# CVKU — Platform SaaS Website Builder & Pembuat CV ATS Gratis

CVKU (`cvku.giize.com`) adalah platform SaaS multi-tenant yang memungkinkan pengguna membuat website profesional tanpa menulis kode menggunakan sistem template dan editor visual, serta membuat Curriculum Vitae (CV) ramah ATS secara gratis dengan ekspor PDF berteks yang dapat dipilih (*selectable text*).

---

## Dokumentasi Proyek

Seluruh spesifikasi teknis, arsitektur, desain, dan aturan bisnis proyek didokumentasikan secara terpusat di dalam direktori [`docs/`](./docs):

- [Arsitektur Sistem Final (`docs/arsitektur.md`)](./docs/arsitektur.md)
- [Spesifikasi Fitur Terpadu (`docs/feature.md`)](./docs/feature.md)
- [Sistem Desain & UI/UX (`docs/design.md`)](./docs/design.md)
- [Rancangan Database Prisma & PostgreSQL (`docs/database.md`)](./docs/database.md)
- [Spesifikasi API & Kontrak Server (`docs/api.md`)](./docs/api.md)
- [Aturan Bisnis & Matriks Hak Akses (`docs/business-rules.md`)](./docs/business-rules.md)
- [Peta Jalan Pengembangan (`docs/development-roadmap.md`)](./docs/development-roadmap.md)
- [Riwayat Perubahan (`docs/changelog.md`)](./docs/changelog.md)

---

## Tech Stack Utama

- **Framework:** Next.js (App Router) + React (JavaScript)
- **Styling & UI:** Tailwind CSS + shadcn/ui + Lucide Icons (Mendukung Dark Mode, Light Mode, & System Mode)
- **Database & ORM:** PostgreSQL + Prisma ORM
- **Autentikasi:** Auth.js (Credentials Email/Kata Sandi & Google OAuth)
- **Validasi:** Zod (Server-side & Client-side)
- **Penyimpanan File:** Vercel Blob (dengan fallback penyimpanan lokal pada mode pengembangan)
- **Pembayaran:** Arsitektur Adapter `PaymentProvider` (`SimulatedPaymentProvider` untuk pengembangan & pengujian sebelum integrasi gateway produksi di Fase 11)
