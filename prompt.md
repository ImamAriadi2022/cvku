# MASTER PROMPT — PEMBANGUNAN PLATFORM CVKU DARI NOL

Bertindaklah sebagai Senior Full-Stack Engineer, Software Architect, UI/UX Designer, Database Engineer, dan Technical Lead.

Saya ingin membangun sebuah platform SaaS bernama **CVKU** dari awal hingga menjadi aplikasi yang berfungsi secara menyeluruh, bukan sekadar prototype UI.

CVKU adalah platform untuk membuat website profesional menggunakan template dan editor visual, serta menyediakan fitur pembuatan CV ATS secara gratis dengan ekspor PDF.

Bangun aplikasi ini menggunakan pendekatan modular, scalable, maintainable, secure, dan production-oriented.

Jangan langsung membuat seluruh fitur dalam satu implementasi besar. Kerjakan secara bertahap berdasarkan prioritas dan pastikan setiap tahap selesai serta dapat diuji sebelum melanjutkan.

---

# 1. IDENTITAS PRODUK

Nama aplikasi: CVKU

Domain utama:
- `cvku.giize.com`
- `*.cvku.giize.com`

Jenis aplikasi:
- SaaS Website Builder.
- CV ATS Builder.
- Platform pengelolaan template.
- Platform layanan berlangganan.
- Affiliate dan referral management.

Target pengguna:
- Mahasiswa.
- Programmer.
- Web Developer.
- UI/UX Designer.
- Graphic Designer.
- Digital Marketer.
- Content Creator.
- Freelancer.
- Profesional.
- Pengusaha.
- Pengguna umum yang membutuhkan website atau CV.

## 1.1 Prinsip Utama

1. Seluruh copywriting, nama fitur, menu, tombol, notifikasi, pesan validasi, dan teks antarmuka wajib menggunakan Bahasa Indonesia.
2. Istilah teknis dalam kode dan dokumentasi developer boleh menggunakan Bahasa Inggris.
3. Antarmuka harus mendukung Dark Mode dan Light Mode.
4. Desain harus modern, profesional, minimalis, dan konsisten.
5. Hindari penggunaan gradient berlebihan, dekorasi tidak perlu, dan tampilan yang terkesan seperti template AI generik.
6. Prioritaskan pengalaman pengguna, aksesibilitas, performa, dan responsivitas.
7. Seluruh fitur harus benar-benar berfungsi dan terhubung dengan backend.
8. Jangan menggunakan data statis sebagai pengganti data database untuk fitur yang sudah seharusnya dinamis.

---

# 2. DOKUMENTASI PROYEK

Sebelum menulis kode, periksa seluruh file dan struktur repository.

Jika tersedia:
- `arsitektur.md`
- `feature.md`
- `design.md`
- `README.md`

Gunakan dokumen tersebut sebagai sumber utama spesifikasi proyek.

Jika dokumentasi belum tersedia, buat dokumentasi awal berdasarkan spesifikasi dalam prompt ini.

Dokumentasi wajib diperbarui apabila terjadi perubahan:
- Arsitektur aplikasi.
- Struktur database.
- Relasi antarfitur.
- API.
- Hak akses.
- Alur bisnis.
- Komponen desain.
- Keputusan teknis.

Buat file tambahan jika dibutuhkan:

```text
docs/
├── arsitektur.md
├── feature.md
├── design.md
├── database.md
├── api.md
├── development-roadmap.md
├── business-rules.md
└── changelog.md
```

Jangan mengubah keputusan arsitektur secara sepihak tanpa mengevaluasi dampaknya terhadap seluruh aplikasi.

---

# 3. TECH STACK

Gunakan teknologi berikut sebagai stack utama:

## Frontend dan Backend

- Next.js App Router.
- React.
- JavaScript.
- Tailwind CSS.
- shadcn/ui.
- Lucide Icons.

Gunakan JavaScript, bukan TypeScript, kecuali terdapat alasan teknis yang benar-benar kuat dan telah disetujui.

## Database

- PostgreSQL.
- Prisma ORM.

## Autentikasi

- Auth.js atau solusi autentikasi yang kompatibel dengan Next.js.
- Google OAuth.
- Email dan password.
- Session management.
- Role-based access control.

Pilih satu pendekatan autentikasi yang konsisten. Jangan menggabungkan beberapa sistem autentikasi tanpa alasan yang jelas.

## Penyimpanan

- Vercel Blob atau object storage yang kompatibel.
- Penyimpanan gambar profil.
- Penyimpanan aset website.
- Penyimpanan file pendukung jika diperlukan.

## Deployment

- Vercel.
- PostgreSQL eksternal.
- Konfigurasi domain dan wildcard subdomain.

## Validasi

- Zod untuk validasi input.
- Validasi dilakukan di sisi server.
- Gunakan validasi client-side sebagai pelengkap pengalaman pengguna.

Jangan menggunakan Firebase, Docker, Angular, atau Vue.

---

# 4. ARSITEKTUR APLIKASI

Gunakan pendekatan feature-based architecture.

Pisahkan:
- UI components.
- Business logic.
- Data access.
- Validation.
- API.
- Authentication.
- Authorization.
- Template renderer.
- Services.

Contoh struktur:

```text
src/
├── app/
│   ├── (public)/
│   │   ├── page.js
│   │   ├── templates/
│   │   ├── services/
│   │   ├── pricing/
│   │   └── faq/
│   │
│   ├── (auth)/
│   │   ├── login/
│   │   ├── register/
│   │   └── forgot-password/
│   │
│   ├── dashboard/
│   ├── admin/
│   ├── affiliate/
│   ├── sites/
│   └── api/
│
├── components/
│   ├── ui/
│   ├── layouts/
│   ├── forms/
│   ├── navigation/
│   └── feedback/
│
├── features/
│   ├── auth/
│   ├── onboarding/
│   ├── user-profile/
│   ├── recommendations/
│   ├── website-builder/
│   ├── website-renderer/
│   ├── template-management/
│   ├── cv-builder/
│   ├── cv-template-management/
│   ├── service-management/
│   ├── subscription-management/
│   ├── transaction-management/
│   ├── promo-management/
│   ├── affiliate-management/
│   ├── commission-management/
│   └── analytics/
│
├── lib/
│   ├── db.js
│   ├── auth.js
│   ├── permissions.js
│   ├── validation.js
│   ├── storage.js
│   ├── domain.js
│   └── utils.js
│
├── templates/
│   ├── website/
│   │   ├── registry.js
│   │   ├── renderer.js
│   │   └── components/
│   │
│   └── cv/
│       ├── registry.js
│       ├── renderer.js
│       └── components/
│
└── proxy.js
```

Struktur tersebut merupakan referensi awal. Boleh disesuaikan jika ada alasan teknis yang lebih baik, tetapi pemisahan tanggung jawab harus dipertahankan.

---

# 5. AKTOR DAN HAK AKSES

CVKU memiliki tiga aktor utama.

## 5.1 Pengguna

Pengguna dapat:
- Mendaftar.
- Login.
- Login dengan Google.
- Mengisi profil.
- Mengisi orientasi pengguna.
- Melihat rekomendasi template.
- Membuat website.
- Mengedit website.
- Mempublikasikan website.
- Membuat CV ATS.
- Mengekspor CV ke PDF.
- Membeli layanan melalui simulasi pembayaran.
- Menggunakan kode promo.
- Melihat transaksi.
- Mengelola langganan.

## 5.2 Admin

Admin dapat:
- Mengelola pengguna.
- Mengelola profesi.
- Mengelola tema.
- Mengelola template website.
- Mengelola template CV ATS.
- Mengelola layanan dan harga.
- Mengelola transaksi.
- Mengelola kode promo.
- Mengelola affiliate.
- Mengelola komisi.
- Mengelola penarikan.
- Mengelola konfigurasi platform.
- Melihat analitik.

## 5.3 Affiliate

Affiliate merupakan profil tambahan pada akun USER.

Pengguna dapat menjadi affiliate setelah memenuhi persyaratan yang ditentukan admin.

Affiliate dapat:
- Melihat tautan referral.
- Membagikan tautan referral.
- Melihat jumlah referral.
- Melihat transaksi referral.
- Melihat komisi.
- Mengajukan penarikan.

Jangan membuat akun affiliate sebagai entitas autentikasi terpisah.

---

# 6. SISTEM AUTENTIKASI DAN ONBOARDING

Implementasikan:
- Registrasi email.
- Login email dan password.
- Google OAuth.
- Logout.
- Verifikasi email.
- Reset password.
- Session management.

## 6.1 Google Login

Sediakan tombol:

"Lanjutkan dengan Google"

Pastikan:
- OAuth menggunakan callback yang benar.
- Tidak terjadi duplikasi akun.
- Identitas akun diverifikasi.
- Session dibuat secara aman.
- Pengguna diarahkan sesuai status onboarding.

## 6.2 Popup Orientasi Pengguna

Tampilkan popup saat pengguna pertama kali login dan belum mengisi orientasi.

Pertanyaan:

**Pertanyaan 1: Dari mana Anda mengetahui CVKU?**

- Instagram.
- TikTok.
- YouTube.
- Facebook.
- Google.
- Teman.
- Komunitas.
- Website atau blog.
- Lainnya.

**Pertanyaan 2: Apa yang ingin Anda buat?**

- Website portfolio.
- Website pribadi.
- Website bisnis.
- Website perusahaan.
- Landing page.
- CV atau resume.
- Website profesional.
- Lainnya.

Pengguna dapat memilih beberapa jawaban.

**Pertanyaan 3: Apa profesi Anda?**

Ambil daftar profesi dari database yang dikelola admin.

Sediakan pilihan lainnya.

Ketentuan:
- Orientasi dapat dilewati.
- Jawaban dapat diubah di profil.
- Jangan tampilkan popup berulang setelah selesai.
- Simpan versi formulir.
- Gunakan jawaban untuk personalisasi rekomendasi.

---

# 7. LANDING PAGE

Buat landing page profesional dengan referensi visual dari website SaaS modern seperti Thumby.

Karakter desain:
- Dark Mode dan Light Mode.
- Navigasi minimalis.
- Hero section yang kuat.
- Visual produk yang dominan.
- Galeri template.
- Preview website.
- Section fitur.
- Section CV ATS gratis.
- Section layanan.
- FAQ.
- Footer.

Gunakan desain yang konsisten dan responsif.

Navigasi utama:

- Beranda.
- Template.
- Fitur.
- Harga.
- Tentang.
- Masuk.
- Mulai Sekarang.

Jangan meniru website referensi secara identik. Ambil inspirasi dari struktur visual, hierarki informasi, dan pengalaman pengguna.

---

# 8. GALERI DAN REKOMENDASI TEMPLATE WEBSITE

Template website harus menjadi entitas database.

Setiap template memiliki:
- Nama.
- Deskripsi.
- Thumbnail.
- Kategori tema.
- Kategori profesi.
- Status.
- Versi.
- Konfigurasi desain.
- Komponen.
- Tanggal publikasi.

Filter:
- Berdasarkan tema.
- Berdasarkan profesi.
- Berdasarkan popularitas.
- Berdasarkan terbaru.

Daftar profesi dan tema harus dinamis dan dikelola admin.

## 8.1 Sistem Rekomendasi

Gunakan pencocokan berdasarkan:
1. Profesi.
2. Minat.
3. Tema.
4. Popularitas.
5. Template unggulan.

Implementasikan rekomendasi berbasis aturan terlebih dahulu.

Jangan langsung menggunakan AI jika pencocokan berbasis tag sudah mencukupi.

---

# 9. WEBSITE BUILDER

Pengguna harus dapat membuat website tanpa menulis kode.

Alur:

```text
Pilih Template
      ↓
Isi Informasi Website
      ↓
Buat Website
      ↓
Masuk Editor Visual
      ↓
Edit Konten
      ↓
Pratinjau
      ↓
Simpan
      ↓
Publikasikan
```

Editor harus menyediakan:
- Pratinjau langsung.
- Pengaturan teks.
- Pengaturan gambar.
- Pengaturan warna.
- Pengaturan komponen.
- Pengaturan bagian.
- Pengaturan urutan bagian.
- Tampilan desktop.
- Tampilan tablet.
- Tampilan mobile.
- Simpan otomatis.
- Publikasi.

Gunakan komponen yang telah dibuat dan didaftarkan oleh developer.

Admin hanya dapat menyusun dan mengonfigurasi komponen yang tersedia melalui Visual Template Builder.

Jangan mengizinkan admin memasukkan atau menjalankan JavaScript arbitrer dari template.

## 9.1 Template Versioning

Setiap website harus menggunakan versi template tertentu.

Jika admin memperbarui template:
- Website lama tidak berubah otomatis.
- Pengguna dapat memilih untuk memperbarui template jika tersedia.
- Migrasi konten harus ditangani secara eksplisit.

## 9.2 Publikasi

Setiap website memiliki:
- Status draf.
- Status publikasi.
- Subdomain.
- Konten.
- Template version.
- Pemilik.

Gunakan wildcard subdomain CVKU.

Pastikan routing tenant aman dan tidak mengganggu route dashboard, admin, API, serta halaman autentikasi.

---

# 10. PEMBUAT CV ATS GRATIS

Buat modul CV Builder yang terpisah dari Website Builder.

Fitur:
- Membuat CV.
- Mengedit CV.
- Menyimpan draf.
- Memilih template.
- Mengganti template.
- Melihat pratinjau.
- Mengunduh PDF.
- Mengelola beberapa CV.

Data CV:
- Informasi pribadi.
- Ringkasan profesional.
- Pengalaman kerja.
- Pendidikan.
- Keterampilan.
- Proyek.
- Sertifikasi.
- Organisasi.
- Informasi tambahan.

Fitur pembuatan dan ekspor PDF harus gratis.

PDF harus:
- Berisi teks yang dapat dipilih.
- Memiliki struktur heading.
- Memiliki urutan baca yang benar.
- Menggunakan tata letak sederhana.
- Memiliki hasil yang konsisten dengan pratinjau.
- Dapat diekstrak menggunakan PDF text extraction.

Jangan menjanjikan bahwa semua CV pasti lolos ATS.

---

# 11. ADMIN TEMPLATE CV ATS

Admin memiliki modul terpisah untuk mengelola template CV ATS.

Fitur:
- Membuat template.
- Mengedit template.
- Mengatur ukuran halaman.
- Mengatur margin.
- Mengatur font.
- Mengatur ukuran font.
- Mengatur warna.
- Mengatur urutan bagian.
- Mengatur heading.
- Melihat pratinjau.
- Menguji hasil PDF.
- Mempublikasikan template.
- Mengarsipkan template.

Gunakan komponen template yang telah disediakan developer.

Template yang dipublikasikan harus memiliki versi.

Perubahan template tidak boleh merusak CV yang telah dibuat pengguna.

---

# 12. LAYANAN DAN LANGGANAN

Admin dapat membuat dan mengelola layanan secara dinamis.

Setiap layanan dapat memiliki:
- Nama.
- Deskripsi.
- Harga.
- Periode.
- Batas website.
- Kapasitas penyimpanan.
- Akses template.
- Custom domain.
- Fitur premium.
- Status.

Gunakan sistem entitlement.

Jangan melakukan pengecekan hak akses hanya dari frontend.

Backend harus memvalidasi seluruh fitur berdasarkan hak akses pengguna.

---

# 13. SISTEM TRANSAKSI DAN SIMULASI PEMBAYARAN

**PENTING: Payment gateway sungguhan tidak boleh diimplementasikan pada tahap awal.**

Namun, arsitektur transaksi harus disiapkan agar integrasi payment gateway nantinya tidak mengharuskan perubahan besar pada sistem.

## 13.1 Simulasi Pembayaran

Buat payment adapter khusus untuk simulasi.

Alur:

```text
Pengguna memilih layanan
          ↓
Membuat transaksi
          ↓
Menghitung diskon
          ↓
Menampilkan ringkasan
          ↓
Simulasi pembayaran
          ↓
Pengguna klik "Simulasikan Pembayaran Berhasil"
          ↓
Server memvalidasi transaksi
          ↓
Transaksi menjadi PAID
          ↓
Langganan diaktifkan
```

Tampilkan keterangan:

"Mode Simulasi — Tidak ada pembayaran uang sungguhan."

Sediakan tombol:
- Simulasikan Pembayaran Berhasil.
- Batalkan Transaksi.

Sistem harus menangani:
- Transaksi berhasil.
- Transaksi dibatalkan.
- Transaksi kedaluwarsa.
- Transaksi gagal.

## 13.2 Aturan Simulasi

Simulasi hanya boleh aktif di environment development atau staging.

Jangan membuat endpoint publik yang memungkinkan pengguna mengubah transaksi sembarangan menjadi PAID.

Validasi:
- Kepemilikan transaksi.
- Status transaksi.
- Nominal transaksi.
- Status kode promo.
- Kesesuaian layanan.
- Idempotensi.

Pembayaran bernilai nol karena diskon 100% dapat diselesaikan melalui alur transaksi khusus tanpa memanggil payment gateway.

Transaksi tetap dicatat dalam database.

## 13.3 Persiapan Integrasi Gateway

Buat abstraksi:

```text
PaymentProvider
├── createPayment()
├── verifyPayment()
├── cancelPayment()
└── refundPayment()
```

Implementasi awal:

```text
SimulatedPaymentProvider
```

Jangan implementasikan provider pembayaran sungguhan terlebih dahulu.

Jangan meminta atau menyimpan kredensial payment gateway pada tahap ini.

---

# 14. KODE PROMO

Admin dapat membuat kode promo.

Jenis:
- Persentase.
- Nominal tetap.
- Diskon 100%.

Pengaturan:
- Kode.
- Deskripsi.
- Layanan yang berlaku.
- Pengguna yang berhak.
- Minimal pembelian.
- Maksimal penggunaan.
- Maksimal penggunaan per pengguna.
- Tanggal mulai.
- Tanggal berakhir.
- Status.

Sistem harus:
- Memvalidasi kode di server.
- Mencegah penggunaan berulang yang tidak sah.
- Mencegah kuota terlampaui akibat request bersamaan.
- Menghitung harga akhir secara server-side.
- Mencatat histori penggunaan.

Kode promo admin berbeda dengan referral affiliate.

---

# 15. AFFILIATE DAN KOMISI

Affiliate merupakan profil tambahan pengguna.

Fitur:
- Persyaratan affiliate.
- Persetujuan admin.
- Referral code.
- Referral link.
- Pelacakan referral.
- Statistik.
- Komisi.
- Penarikan.

Admin dapat mengatur:
- Minimum transaksi.
- Persyaratan langganan.
- Jenis komisi.
- Persentase.
- Nominal tetap.
- Masa atribusi.
- Minimum penarikan.
- Persetujuan otomatis atau manual.

Komisi dihitung dari nilai transaksi bersih setelah diskon sesuai kebijakan.

Buat sistem pencatatan komisi yang aman dan tidak menghasilkan komisi ganda.

Transaksi yang dibatalkan atau dikembalikan harus dapat membatalkan atau menyesuaikan komisi terkait.

---

# 16. ADMIN DASHBOARD

Menu:

1. Ringkasan.
2. Pengguna.
3. Profesi.
4. Tema Template.
5. Template Website.
6. Template CV ATS.
7. Website Pengguna.
8. Layanan dan Harga.
9. Langganan.
10. Transaksi.
11. Kode Promo.
12. Affiliate.
13. Komisi.
14. Penarikan.
15. Analitik.
16. Pengaturan Platform.
17. Riwayat Aktivitas.

Seluruh data harus berasal dari database.

Admin harus dapat mengelola data melalui antarmuka tanpa mengubah kode atau melakukan deployment ulang.

Gunakan pagination, pencarian, filter, validasi, dan konfirmasi untuk operasi penting.

---

# 17. UI/UX DAN DESIGN SYSTEM

Buat design system yang konsisten.

## 17.1 Mode Tampilan

Sediakan:
- Dark Mode.
- Light Mode.
- System Mode.

Preferensi pengguna disimpan agar tetap konsisten saat berpindah halaman.

## 17.2 Prinsip Desain

- Minimalis.
- Profesional.
- Modern.
- Responsif.
- Mudah digunakan.
- Memiliki hierarki visual yang jelas.
- Tidak berlebihan dalam dekorasi.
- Memiliki kontras yang baik.

## 17.3 Komponen

Buat komponen reusable:
- Button.
- Input.
- Textarea.
- Select.
- Dialog.
- Dropdown.
- Tabs.
- Sidebar.
- Navbar.
- Card.
- Table.
- Badge.
- Tooltip.
- Toast.
- Empty State.
- Loading State.
- Skeleton.
- Pagination.
- Confirmation Dialog.

Jangan membuat komponen duplikat untuk kebutuhan yang sebenarnya sama.

---

# 18. DATABASE

Rancang database PostgreSQL menggunakan Prisma.

Entitas yang perlu dipertimbangkan:

## Autentikasi dan Pengguna
- User.
- Account.
- Session.
- VerificationToken.
- UserProfile.
- UserInterest.
- UserProfession.
- OnboardingResponse.

## Katalog
- Profession.
- Theme.
- Template.
- TemplateVersion.
- TemplateProfession.
- TemplateTheme.

## Website Builder
- Website.
- WebsitePage.
- WebsiteDomain.
- WebsiteAnalytics.

## CV Builder
- CVDocument.
- CVTemplate.
- CVTemplateVersion.

## Layanan
- Service.
- ServiceEntitlement.
- Subscription.

## Transaksi
- Transaction.
- TransactionItem.
- PaymentAttempt.

## Promo
- PromoCode.
- PromoUsage.
- PromoService.
- PromoUser.

## Affiliate
- AffiliateProfile.
- Referral.
- Commission.
- Withdrawal.

## Sistem
- Notification.
- AuditLog.
- PlatformSetting.

Rancang relasi, indeks, unique constraints, foreign keys, dan status enum dengan benar.

Jangan membuat seluruh model secara asal dalam satu file tanpa mengevaluasi kebutuhan relasinya.

Simpan snapshot harga dan ketentuan transaksi agar perubahan harga layanan tidak mengubah histori transaksi lama.

---

# 19. KEAMANAN

Implementasikan:

- Server-side authorization.
- Role-based access control.
- Ownership validation.
- Input validation.
- Secure session.
- Password hashing.
- OAuth validation.
- Rate limiting.
- Upload validation.
- Webhook verification ketika gateway sungguhan ditambahkan.
- Audit log.
- Proteksi akses data tenant.
- Idempotency untuk operasi transaksi.

Jangan mempercayai:
- User ID dari client.
- Harga dari client.
- Status pembayaran dari client.
- Nilai diskon dari client.
- Hak akses dari client.

Semua informasi penting harus dihitung dan diverifikasi oleh server.

---

# 20. TAHAPAN PENGEMBANGAN

Ini merupakan aturan pengerjaan paling penting.

Jangan mengimplementasikan seluruh sistem sekaligus.

Kerjakan dalam fase berikut.

## FASE 0 — Audit dan Perencanaan

- Periksa repository.
- Periksa dokumentasi.
- Tentukan arsitektur final.
- Tentukan struktur folder.
- Rancang database.
- Tentukan design system.
- Buat roadmap.
- Identifikasi risiko teknis.

Output:
- Dokumentasi.
- Struktur proyek.
- Rencana implementasi.

Jangan mulai membuat fitur sebelum fondasi teknis disepakati.

## FASE 1 — Fondasi Aplikasi

- Inisialisasi Next.js.
- Konfigurasi JavaScript.
- Tailwind CSS.
- shadcn/ui.
- Prisma.
- PostgreSQL.
- Environment variables.
- Layout utama.
- Design system.
- Dark Mode.
- Light Mode.
- Responsivitas.

Output:
Aplikasi dapat dijalankan dan memiliki fondasi yang stabil.

## FASE 2 — Autentikasi dan Pengguna

- Registrasi.
- Login.
- Google OAuth.
- Logout.
- Reset password.
- Session.
- Role.
- Dashboard pengguna.
- Profil.
- Orientasi pengguna.

Output:
Pengguna dapat mendaftar, login, dan mengelola profil.

## FASE 3 — Landing Page dan Katalog Template

- Landing page.
- Galeri template.
- Detail template.
- Pengelolaan profesi.
- Pengelolaan tema.
- Filter.
- Rekomendasi.

Output:
Pengguna dapat melihat dan menemukan template yang relevan.

## FASE 4 — Admin Template Website

- Admin dashboard.
- Pengelolaan template.
- Component registry.
- Visual Template Builder.
- Template versioning.
- Pratinjau.
- Publikasi.

Output:
Admin dapat membuat dan mengelola template melalui dashboard.

## FASE 5 — Website Builder

- Membuat website.
- Editor visual.
- Pengelolaan konten.
- Pratinjau.
- Simpan otomatis.
- Publikasi.
- Subdomain.
- Tenant routing.

Output:
Pengguna dapat membuat dan mempublikasikan website.

## FASE 6 — CV ATS Builder

- Halaman CV ATS.
- Formulir CV.
- Penyimpanan dokumen.
- Template CV.
- Pratinjau.
- Ekspor PDF.
- Pengujian ekstraksi teks.

Output:
Pengguna dapat membuat dan mengunduh CV ATS secara gratis.

## FASE 7 — Admin Template CV ATS

- Pengelolaan template CV.
- Editor template.
- Pengaturan tipografi.
- Pengaturan margin.
- Pengaturan struktur.
- Versi template.
- Pratinjau.
- Pengujian PDF.
- Publikasi.

Output:
Admin dapat membuat dan mengelola template CV ATS secara mandiri.

## FASE 8 — Layanan dan Transaksi Simulasi

- Pengelolaan layanan.
- Pengaturan harga.
- Entitlement.
- Checkout.
- Transaksi.
- Simulasi pembayaran.
- Aktivasi langganan.
- Riwayat transaksi.
- Kode promo.
- Diskon 100%.

Output:
Seluruh proses transaksi dapat diuji tanpa payment gateway sungguhan.

## FASE 9 — Affiliate dan Komisi

- Persyaratan affiliate.
- Referral.
- Tracking.
- Perhitungan komisi.
- Dasbor affiliate.
- Pengajuan penarikan.
- Persetujuan admin.

Output:
Ekosistem affiliate berfungsi dengan simulasi proses pembayaran penarikan jika belum tersedia penyedia pembayaran.

## FASE 10 — Analitik dan Penyempurnaan

- Analitik website.
- Analitik pengguna.
- Analitik template.
- Analitik transaksi.
- Audit keamanan.
- Pengujian performa.
- Pengujian responsivitas.
- Pengujian seluruh alur bisnis.

Output:
Aplikasi siap memasuki tahap persiapan produksi.

## FASE 11 — Integrasi Payment Gateway

**Tahap ini harus menjadi tahap terakhir.**

Jangan mulai sebelum seluruh sistem transaksi simulasi stabil.

Implementasikan:
- Integrasi payment gateway.
- Pembuatan pembayaran.
- Verifikasi pembayaran.
- Webhook.
- Idempotency.
- Pembatalan transaksi.
- Refund.
- Sinkronisasi langganan.
- Pengujian pembayaran.

Gunakan payment provider melalui adapter agar sistem transaksi tidak bergantung pada satu penyedia.

---

# 21. ATURAN KERJA AI CODING AGENT

Ikuti aturan berikut selama pengerjaan:

1. Jangan langsung membuat seluruh fitur sekaligus.
2. Kerjakan satu fase dalam satu waktu.
3. Sebelum implementasi, jelaskan rencana teknis singkat.
4. Periksa file yang sudah tersedia sebelum membuat file baru.
5. Jangan menghapus atau menimpa implementasi yang sudah berfungsi tanpa alasan.
6. Jangan membuat mockup yang hanya terlihat bagus tetapi tidak memiliki fungsi.
7. Jangan menggunakan data dummy untuk fitur produksi yang seharusnya terhubung database.
8. Data seed boleh digunakan untuk pengembangan dan pengujian.
9. Gunakan server-side validation.
10. Gunakan reusable components.
11. Hindari duplikasi business logic.
12. Jangan membuat API endpoint yang tidak diperlukan.
13. Jangan menambahkan dependensi tanpa alasan.
14. Pastikan setiap halaman memiliki loading, error, empty, dan success state.
15. Pastikan tampilan mobile dan desktop berfungsi.
16. Jalankan lint, build, dan pengujian yang relevan setelah implementasi.
17. Perbaiki error sebelum menyatakan fase selesai.
18. Perbarui dokumentasi setelah perubahan arsitektur atau business logic.
19. Jangan mengintegrasikan payment gateway sungguhan sebelum Fase 11.
20. Jangan mengklaim fitur selesai jika belum diuji.

## 21.1 Format Laporan Setiap Fase

Setelah menyelesaikan satu fase, berikan laporan:

```text
FASE:
Nama fase

IMPLEMENTASI:
- Fitur yang selesai.
- File penting yang dibuat.
- Perubahan database.
- API yang dibuat.

PENGUJIAN:
- Lint.
- Build.
- Pengujian fungsional.
- Hasil pengujian.

CATATAN:
- Kendala.
- Risiko.
- Keputusan teknis.

STATUS:
- Selesai.
- Perlu perbaikan.
- Terblokir.

FASE BERIKUTNYA:
Nama fase yang akan dikerjakan.
```

Jangan melanjutkan ke fase berikutnya apabila terdapat error kritis atau keputusan arsitektur yang belum diselesaikan.

---

# 22. INSTRUKSI PERTAMA

Mulailah dari **FASE 0 — Audit dan Perencanaan**.

Jangan langsung membuat semua fitur.

Lakukan hal berikut:

1. Periksa seluruh struktur repository.
2. Baca `arsitektur.md`, `feature.md`, dan `design.md` jika tersedia.
3. Identifikasi teknologi yang sudah digunakan.
4. Identifikasi implementasi yang sudah ada.
5. Bandingkan kondisi repository dengan spesifikasi CVKU.
6. Tentukan struktur folder final.
7. Buat rancangan database awal.
8. Buat roadmap implementasi.
9. Identifikasi risiko teknis.
10. Laporkan rencana implementasi.

Setelah Fase 0 selesai, lanjutkan ke Fase 1 secara bertahap.

**Prioritas utama: membangun aplikasi yang benar-benar berfungsi, bukan sekadar menghasilkan banyak file kode.**

Ingat: payment gateway sungguhan adalah pekerjaan terakhir. Seluruh fitur transaksi sebelumnya harus menggunakan simulasi pembayaran yang aman dan terkontrol.