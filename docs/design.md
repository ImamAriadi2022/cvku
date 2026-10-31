# Sistem Desain & UI/UX — CVKU

**Produk:** CVKU — Platform SaaS Website Builder & Pembuat CV ATS Gratis  
**Arah Visual:** Modern SaaS, Minimalis, Editorial, Product-First (Inspirasi komposisi visual Thumbsby dengan identitas brand mandiri CVKU)  
**Dukungan Tema:** Light Mode, Dark Mode, & System Mode (Disimpan secara persisten)  
**Bahasa Antarmuka:** 100% Bahasa Indonesia  

---

## 1. Prinsip Utama UI/UX

1. **Product-First & Minimalis:** Menonjolkan pratinjau produk nyata (Website Editor, Template Preview, CV ATS Preview) dengan ruang kosong (*whitespace*) yang proporsional.
2. **Tanpa Dekorasi Berlebihan:** Menghindari gradient pelangi yang berlebihan, efek neon yang menyilaukan, penggunaan emoji sebagai pengganti ikon, atau tampilan template AI generik.
3. **Kematangan Dua Tema (Dark & Light Mode):** Kedua mode dirancang menggunakan variabel CSS semantik (`--background`, `--surface`, `--surface-elevated`, `--border`, `--text-primary`, `--text-secondary`, `--primary`) sehingga memiliki kontras WCAG AA yang nyaman.
4. **Konsistensi Bahasa Indonesia:** Seluruh navigasi (`Beranda`, `Template`, `Fitur`, `Harga`, `Tentang`, `Masuk`, `Mulai Sekarang`), tombol aksi, state kosong (*empty state*), state pemuatan (*loading state*), dan toast notifikasi menggunakan Bahasa Indonesia.

---

## 2. Sistem Warna (Design Tokens)

### 2.1 Aksen Brand Utama
| Token | Nilai Hex | Penggunaan |
|---|---|---|
| `--primary` | `#E84B5B` | Tombol aksi utama (CTA), badge aktif, penanda fokus |
| `--primary-hover` | `#D83D4D` | Kondisi *hover* pada tombol utama |
| `--primary-soft` | `#FCEBED` | Latar highlight lembut pada Light Mode |
| `--primary-dark-soft` | `#351B21` | Latar highlight lembut pada Dark Mode |

### 2.2 Palet Light Mode (`:root`)
| Token | Nilai Hex | Penggunaan |
|---|---|---|
| `--background` | `#FAFAFA` | Latar utama halaman (putih keabu-abuan lembut) |
| `--surface` | `#FFFFFF` | Latar kartu, panel, dialog, dan floating navbar |
| `--surface-elevated` | `#F3F3F3` | Latar sekunder, input hover, dan kartu bertingkat |
| `--border` | `#E8E8E8` | Garis tepi kartu, tabel, dan pemisah bagian |
| `--text-primary` | `#171717` | Judul utama dan teks isi primer |
| `--text-secondary` | `#666666` | Deskripsi dan subjudul |
| `--text-muted` | `#999999` | Keterangan tambahan dan teks petunjuk |

### 2.3 Palet Dark Mode (`[data-theme="dark"]` / `.dark`)
| Token | Nilai Hex | Penggunaan |
|---|---|---|
| `--background` | `#101010` | Latar utama halaman gelap |
| `--surface` | `#171717` | Latar kartu, sidebar, dan floating navbar |
| `--surface-elevated` | `#202020` | Latar elemen bertingkat dan hover state |
| `--border` | `#303030` | Garis tepi tipis dan divider |
| `--text-primary` | `#F5F5F5` | Judul utama dan teks primer |
| `--text-secondary` | `#A1A1AA` | Deskripsi dan teks sekunder |
| `--text-muted` | `#71717A` | Keterangan tambahan |

---

## 3. Tipografi & Tata Letak

### 3.1 Font Utama
- **Sans-Serif Utama:** `Inter` (atau `Geist Sans` sebagai pendamping), dimuat melalui `next/font/google` untuk mencegah *layout shift*.
- **Monospace (Kode/Subdomain/Invoice):** `JetBrains Mono` atau `Geist Mono`.

### 3.2 Skala Tipografi Responsif
| Elemen | Ukuran Desktop | Ukuran Mobile | Ketebalan (Weight) |
|---|---|---|---|
| Judul Hero (H1) | `64px – 76px` | `36px – 44px` | `700 – 800` |
| Judul Bagian (H2) | `36px – 48px` | `28px – 34px` | `700` |
| Judul Kartu (H3) | `20px – 24px` | `18px – 20px` | `600` |
| Teks Isi Besar | `18px` | `16px` | `400` |
| Teks Isi Standar | `16px` | `14px – 15px` | `400` |
| Keterangan (Caption) | `13px – 14px` | `12px – 13px` | `400 – 500` |
| Tombol & Navigasi | `14px – 15px` | `14px` | `600` |

### 3.3 Dimensi Kontainer & Radius
- **Lebar Maksimum Kontainer Publik:** `1240px` (Padding samping: Desktop `40px`, Tablet `28px`, Mobile `20px`).
- **Jarak Antarbagian Landing Page:** `96px – 128px` (Desktop), `64px – 80px` (Mobile).
- **Border Radius:**
  - Kartu (`--radius-card`): `20px`
  - Tombol (`--radius-button`): `12px`
  - Floating Navbar (`--radius-navbar`): `22px`

---

## 4. Struktur Halaman Utama (Landing Page Bahasa Indonesia)

Mengadopsi komposisi modern seperti referensi visual `ui/` dengan copywriting Bahasa Indonesia:
1. **Floating Navbar:** Logo CVKU, menu `Beranda`, `Template`, `Fitur`, `Harga`, `Tentang`, pengalih tema (`Terang` / `Gelap` / `Sistem`), tombol `Masuk`, dan CTA utama `Mulai Sekarang`.
2. **Hero Section:** Badge singkat, judul utama yang tegas, deskripsi manfaat pembuatan website & CV ATS tanpa koding, dua tombol CTA (`Mulai Buat Website`, `Lihat Galeri Template`), dan visual interaktif produk CVKU.
3. **Showcase Produk (Bento Grid):** Menampilkan integrasi pemilihan template, editor visual, pratinjau responsif, dan publikasi subdomain.
4. **Showcase Galeri Template:** Menampilkan kartu template website dari database dengan filter tema & profesi.
5. **Bagian Fitur Utama:** Penjelasan keunggulan editor visual, kustomisasi mudah, desain responsif, subdomain instan, analitik, dan pengelolaan terpusat.
6. **Bagian Pembuat CV ATS Gratis:** Highlight khusus fitur pembuatan CV ramah ATS dengan ekspor PDF gratis tanpa syarat berlangganan.
7. **Cara Kerja (3 Langkah):** `01 Pilih Template` → `02 Sesuaikan Konten` → `03 Publikasikan Website`.
8. **Showcase Editor Visual:** Tampilan dua kolom yang memperlihatkan kemudahan panel bagian, pengaturan komponen, dan kanvas pratinjau.
9. **Bagian Layanan & Harga Dinamis:** Mengambil daftar paket layanan aktif beserta `ServiceEntitlement` langsung dari database.
10. **Bagian Tanya Jawab (FAQ):** Accordion interaktif dalam Bahasa Indonesia.
11. **Ajakan Penutup (Final CTA) & Footer:** Tautan produk, sumber daya, perusahaan, kebijakan privasi, dan syarat layanan.

---

## 5. Katalog Komponen Reusable (`src/components/ui/`)

Seluruh antarmuka dibangun di atas satu set komponen dasar yang konsisten dan mendukung aksesibilitas keyboard:
- `Button` (varian: `primary`, `secondary`, `outline`, `ghost`, `destructive`; ukuran: `sm`, `md`, `lg`, `icon`)
- `Input`, `Textarea`, `Select`, `Checkbox`, `Switch`, `Label`
- `Dialog` / `Modal` & `ConfirmationDialog`
- `DropdownMenu`
- `Tabs` & `Accordion`
- `Sidebar` & `Navbar` (Publik, Dashboard Pengguna, Dashboard Affiliate, Dashboard Admin)
- `Card`, `Badge`, `Tooltip`
- `Table` & `Pagination`
- `Toast` / Sistem Notifikasi Umpan Balik
- `EmptyState`, `LoadingState`, & `Skeleton`
- `ThemeSwitcher` (Mendukung Light, Dark, dan System Mode tanpa *flash of unstyled content*)
