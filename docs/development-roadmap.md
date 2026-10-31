# Peta Jalan Pengembangan (Development Roadmap) — CVKU

Dokumen ini menjadi acuan urutan implementasi bertahap CVKU. Setiap fase wajib diselesaikan, diuji (`lint`, `build`, dan pengujian fungsional), serta dilaporkan sebelum melangkah ke fase berikutnya.

---

## Ringkasan Fase Pengembangan

| Fase | Nama Fase | Fokus Utama | Status |
|---:|---|---|---|
| **Fase 0** | Audit dan Perencanaan | Audit repository, rekonsiliasi spesifikasi, struktur proyek final, rancangan database, API, design system, dan mitigasi risiko. | **Selesai** |
| **Fase 1** | Fondasi Aplikasi | Inisialisasi Next.js App Router (JS), Tailwind CSS, shadcn/ui, Lucide, Prisma + PostgreSQL, variabel environment, sistem tema (Dark/Light/System), komponen UI dasar, dan layout utama. | Menunggu Eksekusi |
| **Fase 2** | Autentikasi dan Pengguna | Registrasi, Login email/sandi, Google OAuth, Logout, Reset kata sandi, RBAC (`USER`/`ADMIN`), Dasbor pengguna dasar, Profil pengguna, dan Popup Orientasi Pengguna (Onboarding). | Menunggu Eksekusi |
| **Fase 3** | Landing Page dan Katalog Template | Implementasi penuh Landing Page Bahasa Indonesia (referensi visual Thumbsby), pengelolaan Profesi & Tema dinamis, Galeri & Detail Template, Filter, dan Sistem Rekomendasi berbasis aturan. | Menunggu Eksekusi |
| **Fase 4** | Admin Template Website | Dasbor Admin inti, Component Registry website, Visual Template Builder untuk Admin, manajemen `TemplateVersion`, pratinjau langsung, dan publikasi template. | Menunggu Eksekusi |
| **Fase 5** | Website Builder | Alur pembuatan website pengguna, Editor Visual (teks, gambar, warna, bagian, urutan), pratinjau Desktop/Tablet/Mobile, *autosave*, publikasi subdomain, dan tenant routing (`src/proxy.js`). | Menunggu Eksekusi |
| **Fase 6** | CV ATS Builder | Halaman Pembuat CV ATS gratis, formulir 9 bagian data CV, penyimpanan beberapa draf CV, pemilihan/penggantian template CV, pratinjau halaman, ekspor PDF *selectable text*, dan uji ekstraksi teks. | Menunggu Eksekusi |
| **Fase 7** | Admin Template CV ATS | Modul Admin khusus Template CV ATS, editor ukuran kertas/margin/tipografi/warna/urutan bagian/heading, `CVTemplateVersion`, pratinjau dengan data contoh, pengujian PDF ATS, dan publikasi. | Menunggu Eksekusi |
| **Fase 8** | Layanan dan Transaksi Simulasi | Pengelolaan Layanan & Harga dinamis oleh Admin, sistem `ServiceEntitlement`, Checkout server-side, Kode Promo (persentase, nominal, diskon 100%), `SimulatedPaymentProvider`, aktivasi langganan, dan riwayat transaksi. | Menunggu Eksekusi |
| **Fase 9** | Affiliate dan Komisi | Pengaturan syarat affiliate oleh Admin, pendaftaran & dasbor Affiliate, kode & tautan referral, pelacakan atribusi, perhitungan komisi bersih, `CommissionLedger`, pengajuan penarikan, dan persetujuan Admin. | Menunggu Eksekusi |
| **Fase 10** | Analitik dan Penyempurnaan | Analitik website pengguna, analitik bisnis & template di Admin Dashboard, kelengkapan 17 menu Admin + Audit Log, audit keamanan menyeluruh, optimasi performa, dan pengujian responsivitas end-to-end. | Menunggu Eksekusi |
| **Fase 11** | Integrasi Payment Gateway | **(Tahap Terakhir)** Implementasi adapter payment gateway sungguhan pada `PaymentProvider`, pembuatan pembayaran, verifikasi signature webhook, idempotency, pembatalan, refund, dan sinkronisasi langganan. | Menunggu Eksekusi |

---

## Kriteria Selesai (Definition of Done) Setiap Fase

Sebelum sebuah fase dinyatakan **Selesai**:
1. Seluruh fitur dalam cakupan fase berfungsi nyata dan terhubung ke database PostgreSQL melalui Prisma ORM (bukan sekadar mockup statis).
2. Seluruh teks antarmuka menggunakan Bahasa Indonesia.
3. Mendukung Dark Mode dan Light Mode secara konsisten serta responsif di layar mobile, tablet, dan desktop.
4. Memiliki *loading state*, *empty state*, *error state*, dan *success feedback* yang lengkap.
5. Validasi input dilakukan di sisi server menggunakan Zod dan otorisasi diperiksa di server.
6. Pemeriksaan `npm.cmd run lint` dan `npm.cmd run build` berjalan bersih tanpa error.
7. Dokumentasi terkait di folder `docs/` dan `docs/changelog.md` telah diperbarui.
