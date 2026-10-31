# Spesifikasi Fitur Terpadu — CVKU

**Nama Produk:** CVKU  
**Domain:** `cvku.giize.com` & `*.cvku.giize.com`  
**Bahasa Antarmuka:** Bahasa Indonesia (100% seluruh copywriting, menu, tombol, validasi, dan notifikasi)

---

## 1. Ringkasan Modul Platform

| No. | Modul | Aktor | Deskripsi Fungsional |
|---:|---|---|---|
| 1 | Landing Page & Halaman Publik | Pengunjung, Pengguna | Beranda bergaya SaaS modern (inspirasi visual Thumbsby), Galeri Template, Layanan & Harga dinamis, Info CV ATS Gratis, FAQ, Tentang. |
| 2 | Autentikasi & Keamanan Akun | Pengguna, Admin | Registrasi email, Login email/sandi, Google OAuth ("Lanjutkan dengan Google"), lupa sandi, verifikasi sesi, RBAC (`USER`, `ADMIN`). |
| 3 | Orientasi Pengguna (Onboarding) | Pengguna Baru | Popup 3 langkah saat pertama login: Sumber informasi CVKU, Minat pembuatan (pilihan jamak), dan Profesi dinamis dari database. |
| 4 | Profil & Rekomendasi Template | Pengguna | Pengelolaan profil pribadi, minat, profesi, serta rekomendasi template berbasis aturan (*rule-based tag matching*). |
| 5 | Katalog Template, Profesi, & Tema | Pengunjung, Pengguna, Admin | Filter galeri berdasarkan tema, profesi, popularitas, dan terbaru; dikelola secara dinamis oleh Admin. |
| 6 | Admin Visual Template Builder | Admin | Penyusunan komponen website terdaftar, konfigurasi warna & tipografi, pratinjau langsung, dan penerbitan `TemplateVersion`. |
| 7 | User Visual Website Builder | Pengguna | Pembuatan website dari template, pengeditan teks/gambar/warna/bagian, urutan bagian, pratinjau Desktop/Tablet/Mobile, *autosave*, publikasi ke subdomain `*.cvku.giize.com`. |
| 8 | Pembuat CV ATS Gratis | Pengguna | Pembuatan dan pengelolaan beberapa CV, pengisian 9 bagian data terstruktur, pemilihan/penggantian template CV, indikator kelengkapan, dan ekspor PDF gratis dengan teks yang dapat dipilih (*selectable text*). |
| 9 | Admin Template CV ATS | Admin | Editor khusus template CV ATS (kertas, margin, font, warna, urutan bagian, heading), uji ekstraksi teks PDF, dan penerbitan `CVTemplateVersion`. |
| 10 | Layanan, Harga, & Entitlement | Pengguna, Admin | Pengelolaan paket layanan dinamis beserta hak akses (`maxWebsites`, `maxStorageMB`, `templateAccess`, `allowCustomDomain`, `allowAnalytics`). |
| 11 | Transaksi, Kode Promo, & Simulasi Pembayaran | Pengguna, Admin | Checkout server-side, validasi kode promo (persentase, nominal tetap, diskon 100%), dan simulasi pembayaran terkontrol (`SimulatedPaymentProvider`) sebelum integrasi gateway di Fase 11. |
| 12 | Ekosistem Affiliate & Komisi | Affiliate (`USER`), Admin | Pendaftaran/kelayakan affiliate, tautan & kode referral, pelacakan atribusi, buku besar komisi (`CommissionLedger`), dan pengajuan/persetujuan penarikan saldo. |
| 13 | Admin Dashboard (17 Menu) | Admin | Pusat kendali seluruh entitas database dengan pencarian, filter, pagination, dialog konfirmasi, dan pencatatan `AuditLog`. |
| 14 | Analitik & Notifikasi | Pengguna, Admin | Statistik kunjungan website pengguna, metrik pertumbuhan/pendapatan platform, notifikasi dalam aplikasi, dan riwayat aktivitas. |

---

## 2. Spesifikasi Detail per Modul

### 2.1 Sistem Orientasi Pengguna (Onboarding Popup)
Ditampilkan satu kali setelah pengguna pertama kali masuk dan `onboardingStatus` belum selesai:
1. **Pertanyaan 1 — "Dari mana Anda mengetahui CVKU?"**
   - Pilihan: Instagram, TikTok, YouTube, Facebook, Google, Teman, Komunitas, Website atau blog, Lainnya (input teks opsional).
2. **Pertanyaan 2 — "Apa yang ingin Anda buat?"** *(Pilihan Jamak / Multi-select)*
   - Pilihan: Website portfolio, Website pribadi, Website bisnis, Website perusahaan, Landing page, CV atau resume, Website profesional, Lainnya.
3. **Pertanyaan 3 — "Apa profesi Anda?"**
   - Diambil secara dinamis dari tabel `Profession` yang aktif di database + opsi "Lainnya" (input manual).
- **Ketentuan:** Dapat dilewati ("Lewati untuk sekarang"), tidak muncul berulang setelah disimpan/dilewati, menyimpan versi formulir (`formVersion`), dan dapat diubah kembali di halaman Profil Saya.

### 2.2 Sistem Rekomendasi Template Website
Menggunakan algoritma pencocokan berbasis aturan (*rule-based scoring*) dengan urutan bobot prioritas:
1. Kecocokan dengan **Profesi** pengguna (`TemplateProfession`).
2. Kecocokan dengan **Minat** pembuatan pengguna (`UserInterest`).
3. Kecocokan dengan **Tema** pilihan (`TemplateTheme`).
4. Tingkat **Popularitas** (`usageCount`).
5. Status **Template Unggulan** (`isFeatured`) dan terbaru (`publishedAt`).

### 2.3 Website Builder & Publikasi Subdomain
- **Alur Pengguna:** Pilih Template → Isi Nama Website & Subdomain → Buat Website → Editor Visual → Edit Konten & Urutan Bagian → Pratinjau (Desktop/Tablet/Mobile) → Simpan Otomatis → Publikasikan.
- **Isolasi Versi:** Website menyimpan `templateVersionId`. Pembaruan template oleh Admin tidak mengubah website yang sudah ada secara paksa.
- **Subdomain & Tenant Routing:** Website yang berstatus `PUBLISHED` dapat diakses melalui `{subdomain}.cvku.giize.com` (atau `/sites/{subdomain}` pada lingkungan pengembangan lokal).

### 2.4 Pembuat CV ATS Gratis & Ekspor PDF
- **Gratis Sepenuhnya:** Tidak membutuhkan langganan berbayar.
- **9 Bagian Data CV:**
  1. Informasi Pribadi (Nama, Email, Telepon, Domisili, LinkedIn, Portfolio, GitHub).
  2. Ringkasan Profesional.
  3. Pengalaman Kerja (Multi-item: Perusahaan, Posisi, Lokasi, Periode, Deskripsi & Pencapaian).
  4. Pendidikan (Multi-item: Institusi, Jenjang, Studi, Tahun, Deskripsi).
  5. Keterampilan (Teknis, Nonteknis, Bahasa, Tools).
  6. Proyek (Multi-item: Nama, Peran, Teknologi, Tautan, Deskripsi).
  7. Sertifikasi dan Penghargaan.
  8. Organisasi dan Pengalaman Tambahan.
  9. Informasi Tambahan.
- **Standar PDF Ramah ATS:**
  - Teks dapat dipilih dan disalin (*selectable text*), bukan gambar bitmap.
  - Struktur heading jelas (`H1` Nama, `H2` Bagian, `H3` Posisi/Institusi).
  - Urutan baca linear dari atas ke bawah.
  - Nama file unduhan: `CV_NamaPengguna.pdf`.
  - Dilengkapi indikator kelengkapan CV tanpa mengklaim garansi pasti lolos seluruh sistem ATS perusahaan.

### 2.5 Sistem Transaksi & Simulasi Pembayaran (Fase 8)
- Menampilkan banner jelas: **"Mode Simulasi — Tidak ada pembayaran uang sungguhan."**
- Menyediakan aksi tervalidasi di server:
  - **Simulasikan Pembayaran Berhasil** → Memvalidasi transaksi, mengubah status ke `PAID`, mencatat `PromoUsage`, mengaktifkan `Subscription` beserta snapshot entitlement, dan mencatat `Commission` affiliate jika ada referral.
  - **Batalkan Transaksi** → Mengubah status ke `CANCELLED`.
- Mendukung skenario kedaluwarsa (`EXPIRED`), gagal (`FAILED`), dan checkout bernilai `Rp0` untuk kode promo diskon 100%.

### 2.6 Menu Lengkap Admin Dashboard (17 Modul)
1. **Ringkasan** — Metrik utama pengguna, website, CV, transaksi, pendapatan bersih, dan aktivitas terbaru.
2. **Pengguna** — Daftar pengguna, detail profil, perubahan status akun, dan role.
3. **Profesi** — Tambah, ubah, urutkan, aktifkan/nonaktifkan profesi.
4. **Tema Template** — Tambah, ubah, urutkan, aktifkan/nonaktifkan tema desain.
5. **Template Website** — Katalog template website, Visual Template Builder, manajemen versi, dan publikasi.
6. **Template CV ATS** — Katalog template CV ATS, editor tipografi/margin/urutan bagian, uji ekstraksi PDF, dan publikasi versi.
7. **Website Pengguna** — Daftar seluruh website tenant, pratinjau, dan moderasi status (`SUSPENDED`/`PUBLISHED`).
8. **Layanan dan Harga** — Pengelolaan paket harga, periode tagihan, dan konfigurasi `ServiceEntitlement`.
9. **Langganan** — Daftar langganan pengguna, masa aktif, dan status entitlement.
10. **Transaksi** — Daftar seluruh transaksi, detail snapshot, dan aksi refund/pembatalan.
11. **Kode Promo** — Pembuatan promo (`PERCENTAGE`, `FIXED_AMOUNT`, `FULL` 100%), kuota, batasan layanan/pengguna, dan histori pemakaian.
12. **Affiliate** — Daftar affiliate, persetujuan aplikasi affiliate, riwayat referral, dan pengaturan syarat kelayakan.
13. **Komisi** — Riwayat komisi referral, persetujuan komisi (`PENDING` → `APPROVED`), dan pengaturan aturan komisi.
14. **Penarikan** — Daftar pengajuan penarikan saldo komisi, persetujuan/penolakan, dan pencatatan bukti bayar.
15. **Analitik** — Grafik dan laporan pertumbuhan pengguna, website, populeritas template, pendapatan, dan performa affiliate.
16. **Pengaturan Platform** — Konfigurasi umum aplikasi, domain cadangan, dan kebijakan sistem.
17. **Riwayat Aktivitas** — Log audit (`AuditLog`) seluruh tindakan sensitif di platform.
