# CVKU — Landing Page Design System

**Product:** CVKU  
**Product Category:** SaaS Website Builder  
**Design Reference:** Thumbsby (visual direction and landing page composition)  
**Platform:** Web Application  
**Primary Framework:** Next.js + React  
**Design Approach:** Modern SaaS, Product-focused, Minimal, Editorial  
**Theme Support:** Dark Mode & Light Mode

---

# 1. Design Overview

## 1.1 Product Identity

CVKU merupakan platform SaaS yang memungkinkan pengguna membuat website profesional tanpa harus menulis kode.

Landing page harus memperkenalkan CVKU sebagai platform website builder yang mudah digunakan, fleksibel, dan memiliki berbagai pilihan template.

Pengunjung harus dapat memahami tiga hal dalam beberapa detik pertama:

1. CVKU dapat digunakan untuk membuat website.
2. Pengguna dapat memulai dari template yang sudah tersedia.
3. Website dapat diedit dan dipublikasikan tanpa harus memiliki kemampuan programming.

## 1.2 Design Direction

Gunakan referensi visual Thumbsby yang ada di direktori ui/*![alt text](image.png) sebagai inspirasi dalam hal:

- Floating navigation.
- Hero section dengan tipografi besar.
- Visual showcase yang mendominasi layar.
- Komposisi gambar berbentuk card dengan sudut membulat.
- Layout yang memiliki ruang kosong cukup luas.
- Feature section dengan ikon dan deskripsi singkat.
- CTA yang kontras dan mudah ditemukan.
- Animasi ringan untuk memberikan kesan interaktif.

Jangan menyalin identitas visual, logo, konten, atau aset Thumbsby.

CVKU harus tetap memiliki identitas visual sendiri.

## 1.3 Design Personality

CVKU harus terlihat:

- Modern.
- Profesional.
- Premium.
- Minimalis.
- Kreatif.
- Technology-oriented.
- User-friendly.

Hindari tampilan yang terlalu ramai, terlalu banyak gradient, penggunaan emoji sebagai ikon, dan dekorasi yang tidak memiliki fungsi.

---

# 2. Color System

CVKU wajib mendukung dua tema: Dark Mode dan Light Mode.

Tema harus dirancang sebagai dua pengalaman visual yang sama-sama matang, bukan sekadar mengubah background dari hitam menjadi putih.

## 2.1 Brand Accent

Gunakan warna aksen utama yang konsisten pada kedua tema.

| Token | Color | Usage |
|---|---|---|
| Primary | `#E84B5B` | Primary button dan CTA |
| Primary Hover | `#D83D4D` | Hover state |
| Primary Soft | `#FCEBED` | Highlight pada light mode |
| Primary Dark Soft | `#351B21` | Highlight pada dark mode |

Warna aksen digunakan secara terukur agar tidak mendominasi keseluruhan halaman.

## 2.2 Dark Mode

<caption>Konsep visual dark mode</caption>

| Token | Color | Usage |
|---|---|---|
| Background | `#101010` | Main background |
| Surface | `#171717` | Card background |
| Surface Elevated | `#202020` | Elevated card |
| Navbar | `#171717` | Floating navigation |
| Border | `#303030` | Border dan divider |
| Text Primary | `#F5F5F5` | Heading dan teks utama |
| Text Secondary | `#A1A1AA` | Deskripsi |
| Text Muted | `#71717A` | Informasi sekunder |
| Accent | `#E84B5B` | CTA dan highlight |

Karakteristik:

- Background gelap dengan kontras yang nyaman.
- Card menggunakan warna surface yang sedikit lebih terang.
- Border tipis dan tidak terlalu mencolok.
- Gunakan shadow secara minimal.
- Hindari efek neon berlebihan.
- Teks utama harus memiliki kontras tinggi.

## 2.3 Light Mode

<caption>Konsep visual light mode</caption>

| Token | Color | Usage |
|---|---|---|
| Background | `#FAFAFA` | Main background |
| Surface | `#FFFFFF` | Card background |
| Surface Elevated | `#F3F3F3` | Elevated card |
| Navbar | `#FFFFFF` | Floating navigation |
| Border | `#E8E8E8` | Border dan divider |
| Text Primary | `#171717` | Heading dan teks utama |
| Text Secondary | `#666666` | Deskripsi |
| Text Muted | `#999999` | Informasi sekunder |
| Accent | `#E84B5B` | CTA dan highlight |

Karakteristik:

- Background putih keabu-abuan, bukan putih yang terlalu menyilaukan.
- Card menggunakan warna putih.
- Border tipis.
- Shadow sangat halus.
- Heading berwarna gelap.
- Aksen tetap menggunakan warna brand.

## 2.4 Theme Switching

Sediakan theme switcher dengan tiga pilihan:

- Light.
- Dark.
- System.

Ketentuan:

1. Pengguna dapat mengganti tema kapan saja.
2. Tema mengikuti preferensi perangkat jika memilih System.
3. Preferensi tema disimpan agar tidak kembali ke default ketika halaman dimuat ulang.
4. Perubahan tema tidak boleh menyebabkan flash warna yang mengganggu.
5. Seluruh komponen harus mendukung kedua tema.
6. Theme transition berlangsung halus, tetapi tidak berlebihan.

Gunakan CSS variables atau design tokens sebagai sumber warna utama.

---

# 3. Typography System

Gunakan typography yang modern dan mudah dibaca.

Rekomendasi font:

**Primary Font:** Inter

Alternatif: Geist Sans.

## 3.1 Typography Scale

| Element | Desktop | Mobile | Weight |
|---|---:|---:|---|
| Hero Heading | 64–80px | 38–48px | 700–800 |
| Section Heading | 40–48px | 30–36px | 700 |
| Card Heading | 20–24px | 18–20px | 600 |
| Body Large | 18px | 16px | 400 |
| Body | 16px | 14–15px | 400 |
| Caption | 13–14px | 12–13px | 400 |
| Button | 14–16px | 14px | 600 |

## 3.2 Typography Guidelines

- Heading harus tegas dan mudah dipindai.
- Gunakan line-height yang nyaman.
- Hindari paragraf terlalu panjang.
- Batasi lebar teks pada hero dan deskripsi section.
- Gunakan font weight untuk membangun hierarki.
- Hindari terlalu banyak variasi ukuran font.

---

# 4. Layout System

Gunakan layout dengan whitespace yang cukup.

## 4.1 Container

| Property | Value |
|---|---|
| Maximum Width | 1240px |
| Desktop Side Padding | 40px |
| Tablet Side Padding | 28px |
| Mobile Side Padding | 20px |
| Section Spacing | 100–140px |
| Card Radius | 16–24px |
| Button Radius | 12–14px |
| Navbar Radius | 20–24px |

Gunakan grid yang fleksibel agar tampilan tetap konsisten pada berbagai resolusi.

## 4.2 Visual Hierarchy

Prioritas visual landing page:

1. Hero headline.
2. CTA utama.
3. Product showcase.
4. Template showcase.
5. Feature explanation.
6. Cara kerja platform.
7. Pricing atau paket layanan.
8. FAQ.
9. Final CTA.

---

# 5. Landing Page Structure

Landing page menggunakan satu halaman utama dengan beberapa section yang saling terhubung.

Urutan section:

```text
Landing Page
│
├── Floating Navbar
│
├── Hero Section
│
├── Product Showcase
│
├── Social Proof / Platform Statistics
│
├── Template Showcase
│
├── Features Section
│
├── How It Works
│
├── Product Editor Showcase
│
├── Pricing / Services
│
├── FAQ
│
├── Final CTA
│
└── Footer
```

---

# 6. Floating Navbar

## 6.1 Visual Direction

Navbar menjadi elemen navigasi yang mengambang di bagian atas halaman.

Karakteristik:

- Floating container.
- Rounded corners.
- Background menggunakan surface theme.
- Border tipis.
- Shadow halus.
- Posisi sticky atau fixed.
- Lebar mengikuti container utama.
- Tidak memenuhi seluruh lebar layar.

Contoh struktur:

```text
┌──────────────────────────────────────────────────────────────┐
│ [CVKU Logo]    Product  Templates  Features  Pricing  FAQ    │
│                                            [Theme] [Login]   │
│                                            [Get Started]     │
└──────────────────────────────────────────────────────────────┘
```

## 6.2 Navigation Items

- Product.
- Templates.
- Features.
- Pricing.
- FAQ.

Action:

- Sign In.
- Get Started.

Sediakan theme switcher di navbar.

## 6.3 Interaction

- Navbar tetap terlihat saat pengguna melakukan scroll.
- Menu dapat melakukan smooth scroll ke section.
- Navbar menggunakan mobile menu pada layar kecil.
- Theme switcher harus mudah dijangkau.
- CTA utama memiliki visual paling menonjol.

---

# 7. Hero Section

## 7.1 Objective

Hero section harus langsung menjelaskan manfaat utama CVKU.

Gunakan headline yang singkat, kuat, dan berorientasi pada hasil.

Rekomendasi copywriting:

**Headline:**

"Your Website, Your Way."

**Supporting Text:**

"Create a professional website in minutes. Choose a template, customize your content, and publish your website without writing a single line of code."

**Primary CTA:**

"Start Building"

**Secondary CTA:**

"Explore Templates"

Tambahkan label kecil di atas headline:

"THE WEBSITE BUILDER FOR EVERYONE"

Copywriting dapat disesuaikan kembali dengan positioning dan target pasar CVKU.

## 7.2 Layout

Hero menggunakan komposisi terpusat atau sedikit asimetris.

```text
                 [ SMALL BADGE ]

             Your Website,
               Your Way.

      Build and publish a professional
        website without writing code.

      [Start Building] [Explore Templates]


               PRODUCT VISUAL
```

## 7.3 Product Visual

Visual utama merupakan elemen paling penting setelah headline.

Gunakan mockup aplikasi CVKU yang menampilkan:

- Website preview.
- Template website.
- Website editor.
- Panel pengaturan.
- Komponen section.
- Preview desktop dan mobile.

Komposisi visual dapat dibuat sedikit perspektif, tetapi jangan sampai menyulitkan pengguna memahami produk.

Gunakan screenshot produk asli setelah UI aplikasi tersedia. Sebelum itu, gunakan mockup yang merepresentasikan antarmuka CVKU, bukan gambar dekoratif yang tidak relevan.

## 7.4 Visual Treatment

- Rounded corner 20–28px.
- Border tipis.
- Shadow halus.
- Background visual mengikuti tema.
- Elemen utama memiliki depth yang cukup.
- Hindari glow berlebihan.

---

# 8. Product Showcase

Section ini berfungsi menunjukkan bahwa CVKU benar-benar memiliki produk yang dapat digunakan.

Judul:

"Everything You Need to Build Your Website"

Deskripsi:

"From choosing a template to publishing your website, everything happens in one place."

## 8.1 Showcase Composition

Gunakan kumpulan visual berupa kartu dengan ukuran berbeda.

Contoh:

```text
┌─────────────────────┐  ┌──────────────────────────┐
│                     │  │                          │
│  Template Preview   │  │    Website Editor        │
│                     │  │                          │
└─────────────────────┘  └──────────────────────────┘

┌──────────────────────────┐  ┌──────────────────────┐
│                          │  │                      │
│    Website Preview       │  │   Responsive View    │
│                          │  │                      │
└──────────────────────────┘  └──────────────────────┘
```

Gunakan bento-style composition.

Visual harus berasal dari produk CVKU atau representasi yang konsisten dengan produk.

---

# 9. Template Showcase

Section ini menampilkan berbagai template website yang tersedia di CVKU.

Judul:

"Start With a Template You Love"

Deskripsi:

"Explore professionally designed templates and make them your own."

## 9.1 Template Categories

Contoh kategori:

- Portfolio.
- Personal Website.
- Business.
- Agency.
- Creative.
- Landing Page.

Kategori harus mengikuti template yang benar-benar tersedia di platform.

## 9.2 Template Cards

Setiap kartu berisi:

- Preview gambar website.
- Nama template.
- Kategori.
- Deskripsi singkat.
- Tombol Preview.

Desain:

- Image-first card.
- Aspect ratio 16:10 atau 4:3.
- Rounded corners.
- Border tipis.
- Hover effect ringan.
- Tidak menggunakan dekorasi yang berlebihan.

Tambahkan CTA:

"Explore All Templates"

Jika template belum tersedia, gunakan data demo yang representatif dan jangan menampilkan jumlah template yang belum benar-benar ada.

---

# 10. Features Section

Judul:

"Everything to Bring Your Website to Life"

Deskripsi:

"Powerful tools to help you create, customize, and manage your website."

Gunakan layout dua kolom atau bento grid.

## 10.1 Feature List

### Visual Website Builder

Create and customize your website with an intuitive visual editor.

### Professional Templates

Start with professionally designed templates that fit your needs.

### Easy Customization

Change content, images, colors, and sections without coding.

### Responsive Design

Your website automatically adapts to desktop, tablet, and mobile screens.

### Custom Domain

Connect your own domain when your selected plan supports it.

### Website Analytics

Understand how visitors interact with your website.

### Simple Management

Manage multiple websites from one dashboard, according to your plan.

### Fast Publishing

Publish your website and make it accessible through your CVKU subdomain.

## 10.2 Visual Guidelines

Setiap feature dapat menggunakan:

- Lucide icon.
- Short heading.
- Description.
- Small interface preview jika relevan.

Jangan membuat semua kartu memiliki ukuran dan isi visual yang sama jika bento layout dapat memperjelas hierarki.

---

# 11. How It Works

Section ini menjelaskan cara menggunakan CVKU secara sederhana.

Judul:

"From Idea to Website in Three Simple Steps"

## Step 1 — Choose Your Template

Explore available templates and select one that fits your purpose.

## Step 2 — Customize Your Website

Edit text, images, sections, and other supported settings through the visual editor.

## Step 3 — Publish Your Website

Publish your website and share it through your CVKU subdomain or supported custom domain.

## 11.1 Layout

Gunakan tiga card atau tiga langkah horizontal.

Desktop:

```text
[01 Choose Template] → [02 Customize] → [03 Publish]
```

Mobile:

```text
01 Choose Template
       ↓
02 Customize
       ↓
03 Publish
```

Setiap langkah dapat memiliki preview visual sederhana.

---

# 12. Website Editor Showcase

Section ini menjelaskan keunggulan editor CVKU.

Judul:

"Design Your Website Without the Complexity"

Deskripsi:

"Customize your website using a visual editor designed to keep things simple."

Tampilkan mockup editor yang memiliki:

- Sidebar section.
- Component settings.
- Website canvas.
- Desktop/mobile preview.
- Publish button.

Gunakan layout dua kolom:

- Satu sisi untuk penjelasan fitur.
- Satu sisi untuk visual editor.

Section ini harus memperlihatkan bagaimana pengguna bekerja di CVKU, bukan hanya menampilkan hasil website.

---

# 13. Pricing / Services Section

Judul:

"Choose the Plan That Fits Your Needs"

Deskripsi:

"Start simple and unlock more possibilities as your website grows."

Pricing harus mengambil data dari sistem layanan CVKU, bukan hardcoded di frontend.

Setiap pricing card menampilkan:

- Nama paket.
- Deskripsi.
- Harga.
- Periode pembayaran.
- Daftar fitur.
- Batas jumlah website.
- Kapasitas penyimpanan jika berlaku.
- Akses template.
- Custom domain jika tersedia.
- CTA untuk berlangganan.

## 13.1 Pricing Card Design

Gunakan tiga kolom pada desktop jika jumlah paket sesuai.

Paket unggulan dapat diberi penekanan visual, tetapi jangan membuat seluruh card terlihat sama menonjol.

## 13.2 Dynamic Pricing

Ketentuan:

- Harga berasal dari database.
- Status paket berasal dari database.
- Fitur berasal dari entitlement.
- Harga promo dihitung di server.
- Promo code tidak boleh diterapkan hanya melalui manipulasi frontend.

Jika belum ada paket yang dipublikasikan, tampilkan CTA untuk menghubungi atau melihat layanan, bukan harga palsu.

---

# 14. FAQ Section

Judul:

"Frequently Asked Questions"

Contoh pertanyaan:

1. What is CVKU?
2. Do I need coding skills to use CVKU?
3. Can I create multiple websites?
4. Can I customize my website?
5. Can I use my own domain?
6. Are the templates responsive?
7. Can I change my template later?
8. What happens when my subscription expires?

Gunakan accordion.

Ketentuan:

- Hanya satu atau beberapa item dapat dibuka sesuai desain.
- Animasi accordion ringan.
- Pertanyaan mudah dipindai.
- Jawaban singkat dan jelas.

Jawaban harus mengikuti kebijakan produk yang sebenarnya.

---

# 15. Final CTA

Section terakhir sebelum footer harus mengajak pengunjung mencoba CVKU.

Headline:

"Ready to Build Your Website?"

Description:

"Start with a template, make it yours, and publish your website with CVKU."

Primary CTA:

"Get Started"

Secondary CTA:

"Explore Templates"

Visual dapat menggunakan preview website dengan komposisi yang sederhana.

---

# 16. Footer

Footer menggunakan layout beberapa kolom.

```text
┌───────────────────────────────────────────────────────────────┐
│ CVKU                                                          │
│ Build your website with simplicity.                           │
│                                                               │
│ Product          Resources          Company         Legal     │
│ Features         Templates          About           Privacy   │
│ Pricing          FAQ                Contact         Terms     │
│                                                               │
│ © 2026 CVKU. All rights reserved.                             │
└───────────────────────────────────────────────────────────────┘
```

Tambahkan:

- Logo.
- Deskripsi singkat.
- Navigasi produk.
- Navigasi resource.
- Informasi perusahaan.
- Privacy Policy.
- Terms of Service.
- Copyright.

Footer harus menyesuaikan kedua tema.

---

# 17. Interaction & Animation

Animasi harus memberikan feedback, bukan sekadar dekorasi.

## 17.1 Scroll Animation

- Section muncul dengan fade-in ringan.
- Product showcase dapat menggunakan staggered entrance.
- Hindari animasi yang menghambat pengguna membaca konten.

## 17.2 Hover Animation

- Button berubah warna secara halus.
- Card sedikit terangkat.
- Preview image dapat melakukan subtle scale.
- Navbar menu memiliki hover state.

## 17.3 Transition

Gunakan durasi sekitar 150–300ms untuk interaksi UI standar.

Hindari:

- Parallax berlebihan.
- Infinite animation pada semua elemen.
- Animasi yang terlalu lambat.
- Gerakan yang menyebabkan layout bergeser.
- Efek yang mengganggu navigasi.

Hormati preferensi `prefers-reduced-motion`.

---

# 18. Responsive Design

Landing page harus optimal pada desktop, tablet, dan mobile.

## 18.1 Desktop

- Floating navbar horizontal.
- Hero headline besar.
- Showcase visual lebar.
- Bento grid.
- Pricing tiga kolom jika sesuai.
- Section memiliki whitespace luas.

## 18.2 Tablet

- Navbar menyesuaikan ruang.
- Grid dapat berubah menjadi dua kolom.
- Hero heading mengecil.
- Showcase tetap mempertahankan hierarki.
- Padding section dikurangi.

## 18.3 Mobile

- Navbar menggunakan hamburger menu.
- Hero headline sekitar 38–48px.
- CTA dapat disusun vertikal atau horizontal jika cukup.
- Showcase menggunakan single-column atau horizontal carousel.
- Bento grid berubah menjadi satu kolom.
- Pricing card disusun vertikal.
- Footer menjadi beberapa grup accordion jika diperlukan.
- Theme switcher tetap mudah ditemukan.

Jangan sekadar mengecilkan ukuran desktop. Susun ulang komposisi sesuai kebutuhan layar mobile.

---

# 19. Component Architecture

Komponen landing page dipisahkan agar mudah dikembangkan.

```text
components/
└── landing/
    ├── Navbar.jsx
    ├── MobileNavigation.jsx
    ├── ThemeSwitcher.jsx
    ├── HeroSection.jsx
    ├── ProductShowcase.jsx
    ├── TemplateShowcase.jsx
    ├── FeaturesSection.jsx
    ├── HowItWorks.jsx
    ├── EditorShowcase.jsx
    ├── PricingSection.jsx
    ├── FAQSection.jsx
    ├── FinalCTA.jsx
    └── Footer.jsx
```

Shared UI:

```text
components/
└── ui/
    ├── Button.jsx
    ├── Container.jsx
    ├── Badge.jsx
    ├── Card.jsx
    ├── Accordion.jsx
    └── SectionHeading.jsx
```

## 19.1 Component Guidelines

- Gunakan reusable component.
- Pisahkan data dan tampilan.
- Gunakan design tokens.
- Jangan menulis seluruh landing page dalam satu file.
- Gunakan semantic HTML.
- Pastikan semua interaksi dapat diakses menggunakan keyboard.
- Hindari duplikasi komponen khusus dark mode dan light mode.

---

# 20. Design Tokens

Gunakan CSS variables sebagai sumber utama design system.

Contoh:

```css
:root {
  color-scheme: light;

  --background: #fafafa;
  --surface: #ffffff;
  --surface-elevated: #f3f3f3;

  --border: #e8e8e8;

  --text-primary: #171717;
  --text-secondary: #666666;
  --text-muted: #999999;

  --primary: #e84b5b;
  --primary-hover: #d83d4d;

  --radius-card: 20px;
  --radius-button: 12px;
  --radius-navbar: 22px;
}

[data-theme="dark"] {
  color-scheme: dark;

  --background: #101010;
  --surface: #171717;
  --surface-elevated: #202020;

  --border: #303030;

  --text-primary: #f5f5f5;
  --text-secondary: #a1a1aa;
  --text-muted: #71717a;

  --primary: #e84b5b;
  --primary-hover: #d83d4d;
}
```

Seluruh komponen harus menggunakan token tersebut.

Jangan menuliskan warna langsung berulang kali pada masing-masing komponen jika warna tersebut merupakan bagian dari design system.

---

# 21. Accessibility & SEO

## Accessibility

- Kontras teks harus memenuhi standar WCAG AA untuk teks normal.
- Semua tombol memiliki accessible label.
- Semua gambar informatif memiliki alt text.
- Navigasi dapat digunakan dengan keyboard.
- Focus state harus terlihat.
- Theme switcher memiliki label yang jelas.
- Hindari penggunaan warna sebagai satu-satunya penanda informasi.
- Hormati reduced motion.

## SEO

- Gunakan satu H1 utama.
- Gunakan struktur heading yang konsisten.
- Setiap section memiliki heading yang relevan.
- Optimalkan metadata.
- Gunakan Open Graph metadata.
- Optimalkan ukuran gambar.
- Gunakan semantic HTML.
- Tambahkan structured data jika sesuai.
- Pastikan konten utama dapat diindeks oleh search engine.

---

# 22. Implementation Guidelines

Urutan implementasi yang disarankan:

**Phase 1 — Design Foundation**

- Brand color.
- Typography.
- Spacing.
- Border radius.
- Dark mode.
- Light mode.
- Theme switcher.

**Phase 2 — Main Layout**

- Floating navbar.
- Hero section.
- Product showcase.
- Responsive container.

**Phase 3 — Product Sections**

- Template showcase.
- Features.
- How it works.
- Editor showcase.

**Phase 4 — Conversion Sections**

- Dynamic pricing.
- FAQ.
- Final CTA.
- Footer.

**Phase 5 — Polish**

- Responsive refinement.
- Animation.
- Accessibility.
- SEO.
- Performance optimization.

---

# 23. Final Design Principles

Seluruh implementasi landing page CVKU harus mengikuti prinsip berikut:

1. Product-first: visual produk harus menjadi fokus utama.
2. Clear hierarchy: pengguna harus mudah memahami informasi.
3. Minimal but expressive: sederhana, tetapi tidak terlihat kosong atau generik.
4. Consistent theming: dark mode dan light mode sama-sama matang.
5. Responsive by design: setiap section harus dirancang untuk berbagai ukuran layar.
6. Reusable components: komponen dapat digunakan kembali.
7. Real product representation: visual harus mencerminkan fitur CVKU yang benar-benar tersedia.
8. Performance-conscious: animasi dan visual tidak boleh mengorbankan kecepatan halaman.
9. Conversion-focused: CTA harus jelas dan mudah ditemukan.
10. Accessible: desain dapat digunakan oleh sebanyak mungkin pengguna.

**Hasil akhir yang diharapkan:** landing page CVKU dengan nuansa visual SaaS modern seperti referensi Thumbsby, tetapi memiliki identitas brand sendiri, menampilkan produk website builder secara dominan, dan menyediakan pengalaman Dark Mode maupun Light Mode yang konsisten.