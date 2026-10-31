# Spesifikasi API & Kontrak Server — CVKU

Dokumen ini mendefinisikan standar desain API Route Handlers dan Server Actions pada platform CVKU.

---

## 1. Standar Arsitektur API

1. **Format Pertukaran Data:** JSON dengan struktur respons seragam.
2. **Bahasa Pesan:** Seluruh pesan `message` dan `errors` yang ditampilkan ke pengguna wajib menggunakan **Bahasa Indonesia** yang jelas dan sopan.
3. **Validasi Input:** Seluruh payload body, query params, dan route params wajib divalidasi di sisi server menggunakan **Zod**.
4. **Otorisasi Berlapis:**
   - **Public API:** Hanya untuk data katalog yang berstatus `PUBLISHED` / `ACTIVE`.
   - **Authenticated User API:** Memeriksa sesi login aktif (`auth()`) dan kepemilikan data (`userId === session.user.id`).
   - **Affiliate API:** Memeriksa sesi login dan status `AffiliateProfile` pengguna.
   - **Admin API:** Memeriksa `session.user.role === "ADMIN"` dan mencatat setiap mutasi ke `AuditLog`.

### Struktur Respons Standar

**Respons Berhasil:**
```json
{
  "success": true,
  "message": "Data berhasil disimpan.",
  "data": {},
  "meta": {
    "page": 1,
    "limit": 10,
    "total": 42,
    "totalPages": 5
  }
}
```

**Respons Gagal / Validasi:**
```json
{
  "success": false,
  "message": "Data yang dimasukkan belum valid.",
  "errorCode": "VALIDATION_ERROR",
  "errors": {
    "subdomain": ["Subdomain ini sudah digunakan atau tidak diizinkan."]
  }
}
```

---

## 2. Daftar Endpoint Utama per Modul

### 2.1 Autentikasi & Orientasi (`/api/auth/*` & `/api/onboarding/*`)
- `POST /api/auth/register` — Registrasi akun baru dengan email & kata sandi (termasuk pencatatan kode referral jika ada di cookie/query).
- `POST /api/auth/[...nextauth]` — Handler Auth.js (Credentials & Google OAuth).
- `POST /api/auth/forgot-password` — Permintaan tautan atur ulang kata sandi.
- `POST /api/auth/reset-password` — Pengaturan kata sandi baru menggunakan token.
- `GET /api/onboarding` — Memeriksa status orientasi pengguna dan memuat daftar profesi aktif.
- `POST /api/onboarding` — Menyimpan jawaban orientasi pengguna (sumber informasi, minat, profesi) atau menandai dilewati (`SKIPPED`).

### 2.2 Profil & Rekomendasi (`/api/profile/*` & `/api/recommendations/*`)
- `GET /api/profile` — Mengambil profil lengkap pengguna, minat, profesi, dan akun Google terhubung.
- `PATCH /api/profile` — Memperbarui profil, minat, dan profesi pengguna.
- `GET /api/recommendations/templates` — Mengambil daftar rekomendasi template website berdasarkan pencocokan aturan (*rule-based matching*: profesi -> minat -> tema -> popularitas -> unggulan).

### 2.3 Katalog Publik (`/api/catalog/*`)
- `GET /api/catalog/professions` — Daftar profesi aktif.
- `GET /api/catalog/themes` — Daftar tema template aktif.
- `GET /api/catalog/templates` — Galeri template website terpublikasi (mendukung filter `theme`, `profession`, `search`, `sort=popular|latest`).
- `GET /api/catalog/templates/[slug]` — Detail template website dan pratinjau konfigurasinya.
- `GET /api/catalog/cv-templates` — Galeri template CV ATS terpublikasi.
- `GET /api/catalog/services` — Daftar layanan & paket harga aktif beserta entitlement-nya.

### 2.4 Website Builder & Pengelolaan Website (`/api/websites/*`)
- `GET /api/websites` — Daftar website milik pengguna yang sedang login.
- `POST /api/websites` — Membuat website baru (validasi batas entitlement `maxWebsites`, akses template, dan ketersediaan subdomain).
- `GET /api/websites/[websiteId]` — Detail konfigurasi website dan halaman untuk editor visual.
- `PATCH /api/websites/[websiteId]` — Simpan perubahan konten/desain/urutan bagian website (mendukung *autosave*).
- `POST /api/websites/[websiteId]/publish` — Mempublikasikan atau memperbarui publikasi website ke subdomain `*.cvku.giize.com`.
- `POST /api/websites/[websiteId]/unpublish` — Mengembalikan status website ke `DRAFT`.
- `POST /api/websites/[websiteId]/upgrade-template` — Migrasi eksplisit ke `TemplateVersion` terbaru jika tersedia.
- `DELETE /api/websites/[websiteId]` — Mengarsipkan atau menghapus website milik pengguna.
- `GET /api/websites/check-subdomain?subdomain=...` — Memeriksa ketersediaan dan validitas subdomain.

### 2.5 Pembuat CV ATS Gratis (`/api/cv/*`)
- `GET /api/cv` — Daftar dokumen CV milik pengguna.
- `POST /api/cv` — Membuat dokumen CV ATS baru menggunakan `CVTemplateVersion` yang dipilih.
- `GET /api/cv/[cvId]` — Mengambil data lengkap dokumen CV dan skema template-nya.
- `PATCH /api/cv/[cvId]` — Menyimpan draf isi CV, mengganti template CV, atau mengubah urutan bagian.
- `DELETE /api/cv/[cvId]` — Menghapus dokumen CV.
- `POST /api/cv/[cvId]/export-pdf` — Menghasilkan dokumen PDF terstruktur dengan teks yang dapat dipilih (*selectable text*) dan mengembalikan stream/file PDF `CV_NamaPengguna.pdf`.

### 2.6 Transaksi, Kode Promo, & Simulasi Pembayaran (`/api/transactions/*` & `/api/promo/*`)
- `POST /api/promo/validate` — Memvalidasi kode promo di server terhadap layanan dan pengguna serta mengembalikan rincian potongan harga.
- `POST /api/transactions/checkout` — Membuat transaksi baru dengan perhitungan harga server-side, mengunci snapshot transaksi, dan:
  - Jika total = Rp0 (diskon 100%): langsung menyelesaikan transaksi (`PAID`) dan mengaktifkan langganan.
  - Jika total > Rp0: membuat `PaymentAttempt` melalui `PaymentProvider` (`SimulatedPaymentProvider` pada Fase 8).
- `GET /api/transactions` — Riwayat transaksi pengguna.
- `GET /api/transactions/[transactionId]` — Detail transaksi, ringkasan snapshot, dan status pembayaran.
- `POST /api/transactions/[transactionId]/simulate` — **(Khusus Development/Staging)** Memproses simulasi pembayaran (`SUCCESS`, `CANCEL`, `FAIL`, `EXPIRE`) dengan validasi kepemilikan transaksi, status `AWAITING_PAYMENT`, dan idempotency.

### 2.7 Affiliate & Komisi (`/api/affiliate/*`)
- `GET /api/affiliate/status` — Memeriksa kelayakan pengguna terhadap syarat affiliate aktif dan mengambil ringkasan dasbor affiliate.
- `POST /api/affiliate/apply` — Mengajukan aktivasi profil affiliate (otomatis aktif atau menunggu persetujuan admin sesuai kebijakan).
- `GET /api/affiliate/referrals` — Daftar pengguna yang direferensikan beserta statusnya.
- `GET /api/affiliate/commissions` — Riwayat komisi dan mutasi buku besar (`CommissionLedger`).
- `POST /api/affiliate/withdrawals` — Mengajukan penarikan saldo komisi yang berstatus `APPROVED` (validasi saldo minimum dan transaksi database atomik).

### 2.8 Admin Dashboard API (`/api/admin/*`)
Seluruh endpoint di bawah `/api/admin/*` wajib melewati middleware otorisasi `requireAdmin()` dan mencatat `AuditLog`:
- `/api/admin/overview` — Ringkasan metrik platform dari database.
- `/api/admin/users` — CRUD status pengguna, role, dan detail akun.
- `/api/admin/professions` — CRUD daftar profesi dinamis & pengurutan.
- `/api/admin/themes` — CRUD daftar tema template dinamis & pengurutan.
- `/api/admin/templates` — CRUD template website, Visual Template Builder configuration, dan penerbitan `TemplateVersion`.
- `/api/admin/cv-templates` — CRUD template CV ATS, pengaturan tipografi/margin/struktur, pengujian ekstraksi teks PDF, dan penerbitan `CVTemplateVersion`.
- `/api/admin/websites` — Pemantauan dan moderasi website pengguna.
- `/api/admin/services` — CRUD layanan, harga, dan konfigurasi `ServiceEntitlement`.
- `/api/admin/subscriptions` — Pemantauan dan pengelolaan langganan pengguna.
- `/api/admin/transactions` — Pemantauan transaksi, pembatalan, dan proses refund (termasuk penyesuaian/reversal komisi).
- `/api/admin/promo-codes` — CRUD kode promo dan histori pemakaian.
- `/api/admin/affiliates` — Persetujuan affiliate, pengaturan syarat program, dan kebijakan atribusi.
- `/api/admin/commissions` — Persetujuan atau pembatalan komisi affiliate.
- `/api/admin/withdrawals` — Persetujuan, penolakan, dan pencatatan bukti pembayaran penarikan komisi.
- `/api/admin/settings` — Pengelolaan konfigurasi platform (`PlatformSetting`).
- `/api/admin/audit-logs` — Penelusuran riwayat aktivitas sensitif dengan filter dan pagination.
