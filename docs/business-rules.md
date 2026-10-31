# Aturan Bisnis & Matriks Hak Akses — CVKU

Dokumen ini merangkum seluruh aturan bisnis (*business rules*) dan kebijakan keamanan yang wajib ditegakkan di sisi server pada platform CVKU.

---

## 1. Prinsip Dasar Platform

1. **Bahasa Antarmuka Wajib Bahasa Indonesia:** Seluruh teks yang dilihat pengguna (navigasi, tombol, formulir, placeholder, pesan error/sukses, status badge, halaman publik, dasbor pengguna, dasbor affiliate, dan dasbor admin) wajib menggunakan Bahasa Indonesia yang baku, jelas, dan natural.
2. **Data Dinamis Berbasis Database:** Tidak boleh menanam (*hardcode*) daftar profesi, daftar tema, paket layanan/harga, template website, maupun template CV ATS sebagai array statis yang menggantikan database. Gunakan `prisma/seed.js` untuk menyediakan data awal pengembangan.
3. **Pembuat CV ATS 100% Gratis:** Pengguna yang terdaftar dapat membuat, menyimpan, memilih template CV ATS yang telah dipublikasikan admin, dan mengunduh PDF CV ATS secara gratis tanpa diwajibkan membeli paket langganan Website Builder.

---

## 2. Matriks Aktor & Hak Akses (RBAC + Ownership)

| Modul / Operasi | Pengunjung (Anonim) | Pengguna (`USER`) | Affiliate (`USER` + `AffiliateProfile` Aktif) | Admin (`ADMIN`) |
|---|---|---|---|---|
| Melihat Beranda, Harga, FAQ, Galeri Template | Diizinkan | Diizinkan | Diizinkan | Diizinkan |
| Mengakses Website Publik Tenant (`*.cvku.giize.com`) | Diizinkan (hanya `PUBLISHED`) | Diizinkan | Diizinkan | Diizinkan |
| Mengisi Orientasi & Mengelola Profil Sendiri | Ditolak | Diizinkan (Milik Sendiri) | Diizinkan (Milik Sendiri) | Diizinkan |
| Membuat & Mengedit Website | Ditolak | Sesuai Entitlement & Milik Sendiri | Sesuai Entitlement & Milik Sendiri | Moderasi & Pratinjau |
| Membuat CV ATS & Ekspor PDF Gratis | Melihat Info & Template | Diizinkan (Milik Sendiri) | Diizinkan (Milik Sendiri) | Diizinkan |
| Checkout Layanan & Simulasi Pembayaran | Ditolak | Diizinkan (Transaksi Sendiri) | Diizinkan (Transaksi Sendiri) | Pemantauan & Refund |
| Membagikan Referral, Melihat Komisi, & Tarik Saldo | Ditolak | Hanya jika memenuhi syarat Affiliate | Diizinkan (Data Affiliate Sendiri) | Persetujuan & Pembayaran |
| Mengelola Profesi, Tema, Template, Layanan, Promo | Ditolak | Ditolak | Ditolak | Diizinkan (Tercatat di AuditLog) |

---

## 3. Aturan Bisnis Spesifik per Domain

### 3.1 Autentikasi & Orientasi Pengguna
- **Pencegahan Duplikasi Akun Google OAuth:** Login menggunakan Google memeriksa kecocokan akun secara terverifikasi; tidak boleh membuat dua akun dengan email yang sama.
- **Popup Orientasi Sekali Saja:** Popup orientasi hanya ditampilkan apabila `onboardingStatus` bernilai `NOT_STARTED` atau `IN_PROGRESS`. Jika pengguna telah menyelesaikan (`COMPLETED`) atau melewati (`SKIPPED`), popup tidak boleh muncul berulang kali.
- **Fleksibilitas Profil:** Seluruh jawaban orientasi (sumber informasi, minat jamak, dan profesi) dapat diperbarui kapan saja melalui menu Profil Saya.

### 3.2 Template Versioning (Website & CV ATS)
- **Penguncian Versi (*Version Pinning*):** Setiap `Website` mengikat ke `templateVersionId` dan setiap `CVDocument` mengikat ke `cvTemplateVersionId`.
- **Isolasi Perubahan Admin:** Ketika Admin mempublikasikan versi baru dari sebuah template, website atau CV milik pengguna lama **tidak berubah secara otomatis**. Pengguna diberikan pilihan untuk memperbarui versi secara eksplisit.
- **Keamanan Komponen:** Admin maupun pengguna tidak dapat menyisipkan script JavaScript mentah atau kode React arbitrer ke dalam konfigurasi template. Seluruh blok dirender melalui `componentRegistry` resmi.

### 3.3 Sistem Entitlement Layanan
- Pengecekan hak akses pengguna wajib dilakukan di server sebelum mengeksekusi aksi:
  - **Batas Jumlah Website (`maxWebsites`):** Pengguna tidak dapat membuat website baru jika jumlah website aktif/draf miliknya telah mencapai batas entitlement.
  - **Akses Template (`templateAccess`):** Template berlabel premium hanya dapat digunakan oleh pengguna dengan entitlement yang mendukung akses template penuh (`ALL`).
  - **Custom Domain & Analitik:** Diperiksa berdasarkan `allowCustomDomain` dan `allowAnalytics` pada entitlement aktif pengguna.
- Pengguna tanpa langganan berbayar aktif mengikuti kebijakan kuota dasar default platform (atau paket Dasar/Gratis sesuai konfigurasi `PlatformSetting`), namun **fitur Pembuat CV ATS tetap terbuka gratis**.

### 3.4 Transaksi, Kode Promo, & Simulasi Pembayaran
- **Perhitungan Server-Side:** Harga layanan, potongan kode promo, pajak, dan total akhir wajib dihitung ulang di server. Nilai harga atau diskon dari request client diabaikan sepenuhnya.
- **Snapshot Transaksi:** Saat transaksi dibuat, rincian layanan, entitlement, promo, dan referral disimpan ke dalam `transactionSnapshot` agar perubahan harga di masa depan tidak mengubah catatan historis transaksi.
- **Diskon 100% (Harga Nol):** Jika kode promo menghasilkan harga akhir `Rp0`, transaksi langsung diselesaikan (`PAID`) melalui `ZeroPricePaymentFlow` tanpa melewati simulasi gateway eksternal, tetap mencatat `Transaction` dan `PromoUsage`, serta langsung mengaktifkan `Subscription`.
- **Keamanan Simulasi Pembayaran:**
  - Hanya aktif jika diizinkan oleh konfigurasi environment (`NODE_ENV !== "production"` atau `ENABLE_PAYMENT_SIMULATION === "true"`).
  - Hanya pemilik transaksi (`transaction.userId === session.user.id`) atau Admin yang dapat memicu aksi simulasi pada transaksi yang masih berstatus `AWAITING_PAYMENT`.
  - Menggunakan validasi idempotensi agar klik ganda tidak membuat langganan atau komisi ganda.

### 3.5 Program Affiliate, Komisi, & Penarikan
- **Larangan Self-Referral:** Pengguna tidak dapat menggunakan kode referral miliknya sendiri untuk mendapatkan komisi atas pembelian pribadinya.
- **Pemisahan Promo Code & Referral:** Kode promo memberikan diskon kepada pembeli; kode referral mencatat atribusi affiliate untuk perhitungan komisi. Keduanya adalah entitas terpisah yang dapat bekerja berdampingan dalam satu transaksi.
- **Basis Perhitungan Komisi:** Komisi dihitung dari nilai transaksi bersih setelah dikurangi diskon promo (`totalAmount`). Jika transaksi bernilai `Rp0` (diskon 100%), maka komisi persentase bernilai `Rp0`.
- **Siklus Hidup Komisi & Reversal:**
  - Saat transaksi berstatus `PAID`, komisi dicatat sebagai `PENDING`.
  - Setelah disetujui / melewati masa tunggu, status menjadi `APPROVED` dan masuk ke `CommissionLedger` (menambah `availableBalance`).
  - Jika transaksi dibatalkan atau di-*refund*, komisi terkait wajib diubah menjadi `REVERSED` dan saldo disesuaikan di `CommissionLedger`.
- **Validasi Penarikan (*Withdrawal*):** Pengajuan penarikan hanya boleh dilakukan jika `amount >= minimumWithdrawal` dan `amount <= availableBalance`, diproses di dalam transaksi database atomik.
