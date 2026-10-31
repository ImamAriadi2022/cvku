# Riwayat Perubahan (Changelog) — CVKU

Seluruh perubahan arsitektur, skema database, fitur, dan keputusan teknis proyek CVKU dicatat secara kronologis dalam dokumen ini.

---

## [Fase 0] — Audit dan Perencanaan (2026-10-31)

### Ditambahkan
- **`docs/arsitektur.md`**: Dokumen arsitektur final yang menyelaraskan spesifikasi Website Builder, Pembuat CV ATS Gratis, sistem katalog dinamis, multi-tenant routing, serta arsitektur pembayaran simulasi (`PaymentProvider` -> `SimulatedPaymentProvider`).
- **`docs/database.md`**: Rancangan lengkap skema database PostgreSQL & Prisma ORM yang mencakup 30+ model lintas 8 domain bisnis beserta aturan snapshot dan buku besar komisi (`CommissionLedger`).
- **`docs/api.md`**: Standar kontrak API Route Handlers & Server Actions, struktur respons JSON Bahasa Indonesia, validasi Zod, dan matriks endpoint.
- **`docs/feature.md`**: Spesifikasi fitur terpadu untuk Pengguna, Affiliate, dan Admin (17 modul dashboard admin).
- **`docs/design.md`**: Spesifikasi sistem desain Dark Mode, Light Mode, dan System Mode, token CSS variabel, skala tipografi, komposisi Landing Page Bahasa Indonesia (referensi visual Thumbsby), dan daftar komponen UI reusable.
- **`docs/business-rules.md`**: Aturan bisnis terpusat, RBAC, kepemilikan data tenant, versi template, entitlement layanan, keamanan simulasi pembayaran, dan aturan komisi affiliate.
- **`docs/development-roadmap.md`**: Rencana implementasi bertahap dari Fase 0 hingga Fase 11 beserta kriteria pengujian.
- **`README.md`**: Pembaruan dokumentasi utama repository.

### Keputusan Teknis
- Mengunci penggunaan **JavaScript** (bukan TypeScript) pada Next.js App Router dengan validasi runtime menggunakan **Zod**.
- Menetapkan bahwa **Payment Gateway sungguhan baru akan diintegrasikan pada Fase 11**, sedangkan Fase 8 menggunakan `SimulatedPaymentProvider` yang aman dan divalidasi di sisi server.
- Mencatat kendala kebijakan eksekusi PowerShell lokal pada Windows (`npm.ps1` diblokir) dan menetapkan penggunaan `npm.cmd` serta `npx.cmd` untuk seluruh eksekusi CLI.
