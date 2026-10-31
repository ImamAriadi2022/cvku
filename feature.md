# CVKU — Spesifikasi Fitur Platform

**Nama Produk:** CVKU  
**Jenis Produk:** Platform SaaS Website Builder dan CV ATS  
**Domain:** `cvku.giize.com`  
**Dokumen:** Spesifikasi Fitur  
**Versi:** 2.0  
**Bahasa Antarmuka:** Bahasa Indonesia

---

# 1. Gambaran Umum Produk

CVKU merupakan platform SaaS yang menyediakan layanan pembuatan website profesional dan Curriculum Vitae (CV) berbasis ATS (Applicant Tracking System).

Pengguna dapat membuat website tanpa perlu menulis kode melalui sistem pemilihan template dan editor visual. Selain itu, pengguna dapat membuat CV ATS secara gratis menggunakan template yang telah disediakan oleh platform dan mengunduhnya dalam format PDF.

CVKU memiliki tiga aktor utama:

1. **Pengguna:** Pelanggan yang membuat website, mengelola CV, dan menggunakan layanan platform.
2. **Admin:** Pengelola platform yang mengatur pengguna, layanan, template website, template CV ATS, promo, transaksi, dan affiliate.
3. **Affiliate:** Pengguna yang memenuhi persyaratan program affiliate dan memperoleh komisi dari transaksi yang berhasil direferensikan.

Affiliate merupakan kemampuan tambahan pada akun pengguna, bukan jenis akun yang terpisah.

## 1.1 Prinsip Produk

- Mudah digunakan tanpa kemampuan pemrograman.
- Memiliki tampilan Dark Mode dan Light Mode.
- Seluruh antarmuka menggunakan Bahasa Indonesia.
- Rekomendasi template disesuaikan dengan profil pengguna.
- Pengguna dapat membuat website secara mandiri.
- Pengguna dapat membuat CV ATS secara gratis.
- Admin dapat mengelola layanan dan template secara dinamis.
- Sistem mendukung pengembangan fitur tanpa mengubah keseluruhan arsitektur.

# 2. Daftar Modul Utama

| No. | Modul | Fitur Utama |
|---:|---|---|
| 1 | Website Publik | Beranda, galeri template, layanan, harga, FAQ |
| 2 | Autentikasi | Registrasi, login, Google Login, reset kata sandi |
| 3 | Orientasi Pengguna | Informasi pengguna baru, sumber informasi, minat, profesi |
| 4 | Profil Pengguna | Informasi pribadi, profesi, minat, preferensi |
| 5 | Rekomendasi Template | Rekomendasi berdasarkan tema dan profesi |
| 6 | Pengelolaan Website | Membuat, mengedit, dan menghapus website |
| 7 | Pembuat Website | Editor visual, pengaturan konten, pratinjau |
| 8 | Publikasi Website | Subdomain, custom domain, status publikasi |
| 9 | Pembuat CV ATS | Formulir CV, pemilihan template, ekspor PDF |
| 10 | Pengelolaan Langganan | Layanan, paket, masa aktif, hak akses |
| 11 | Transaksi | Checkout, pembayaran, riwayat transaksi |
| 12 | Kode Promo | Diskon persentase, nominal, dan gratis 100% |
| 13 | Affiliate | Tautan referral, pelacakan, statistik |
| 14 | Komisi | Perhitungan komisi dan penarikan |
| 15 | Admin | Pengelolaan seluruh ekosistem CVKU |
| 16 | Notifikasi | Notifikasi dalam aplikasi dan email |
| 17 | Sistem | Keamanan, audit log, penyimpanan, analitik |

# 3. Website Publik

## 3.1 Beranda

Beranda merupakan halaman utama CVKU yang dapat diakses oleh pengunjung tanpa login.

Konten:

- Hero section yang menjelaskan CVKU.
- Informasi keunggulan platform.
- Pratinjau hasil website.
- Galeri template unggulan.
- Informasi pembuat CV ATS gratis.
- Penjelasan fitur utama.
- Daftar layanan dan harga.
- FAQ.
- Tombol ajakan untuk mulai menggunakan CVKU.

Beranda harus mendukung Dark Mode dan Light Mode.

## 3.2 Galeri Template Website

Pengunjung dapat melihat template website yang tersedia sebelum melakukan registrasi.

Fitur:

- Melihat seluruh template.
- Melihat pratinjau template.
- Mencari template berdasarkan nama.
- Memfilter berdasarkan tema.
- Memfilter berdasarkan profesi.
- Melihat detail template.
- Melihat kategori dan deskripsi template.

### 3.2.1 Filter Berdasarkan Tema

Tema digunakan untuk mengelompokkan template berdasarkan tujuan atau karakteristik desain website.

Contoh:

- Minimalis.
- Modern.
- Profesional.
- Kreatif.
- Elegan.
- Personal.
- Korporat.
- Sederhana.

Daftar tema dikelola melalui Admin Dashboard.

### 3.2.2 Filter Berdasarkan Profesi

Profesi digunakan untuk mengelompokkan template berdasarkan pekerjaan atau bidang profesional yang dituju.

Contoh:

- Programmer.
- Web Developer.
- UI/UX Designer.
- Graphic Designer.
- Digital Marketer.
- Fotografer.
- Content Creator.
- Penulis.
- Guru.
- Mahasiswa.
- Konsultan.
- Pengusaha.
- Arsitek.

Daftar profesi tidak ditanam permanen di dalam kode aplikasi. Admin dapat menambahkan, mengubah, mengurutkan, dan menonaktifkan profesi melalui dashboard.

Satu template dapat memiliki lebih dari satu tema dan profesi.

# 4. Autentikasi

CVKU menyediakan beberapa metode autentikasi.

## 4.1 Registrasi dengan Email

Pengguna dapat membuat akun dengan:

- Nama lengkap.
- Alamat email.
- Kata sandi.
- Konfirmasi kata sandi.

## 4.2 Masuk dengan Email

Pengguna dapat masuk menggunakan email dan kata sandi.

Fitur tambahan:

- Ingat sesi.
- Keluar dari akun.
- Pemulihan kata sandi.
- Verifikasi email.
- Pembatasan percobaan login.

## 4.3 Masuk dengan Google

Pengguna dapat mendaftar atau masuk menggunakan akun Google.

Tombol yang ditampilkan:

**Lanjutkan dengan Google**

Alur:

1. Pengguna memilih tombol masuk dengan Google.
2. Sistem mengarahkan pengguna ke halaman autentikasi Google.
3. Pengguna memilih akun Google.
4. Google mengirimkan hasil autentikasi ke CVKU.
5. Sistem memvalidasi identitas.
6. Sistem mencari atau membuat akun pengguna.
7. Sistem membuat sesi login.
8. Pengguna diarahkan ke dashboard atau orientasi pengguna jika belum pernah menyelesaikannya.

## 4.4 Penghubungan Akun

Pengguna dapat menghubungkan akun Google dengan akun CVKU yang telah dimiliki.

Sistem tidak boleh membuat akun ganda atau menggabungkan akun secara otomatis hanya berdasarkan kecocokan alamat email tanpa validasi kepemilikan.

## 4.5 Pemulihan Kata Sandi

Fitur:

- Memasukkan email.
- Mengirim tautan pemulihan.
- Memvalidasi token.
- Mengatur kata sandi baru.

# 5. Orientasi Pengguna Baru

<badge>Fitur baru</badge>

Orientasi pengguna merupakan popup atau rangkaian pertanyaan singkat yang ditampilkan ketika pengguna pertama kali berhasil masuk ke CVKU.

Tujuannya adalah mengumpulkan informasi profil agar sistem dapat memberikan rekomendasi template yang lebih relevan.

Orientasi tidak boleh menjadi proses yang terlalu panjang atau menghalangi pengguna menggunakan platform.

## 5.1 Alur Orientasi

```text
Pengguna berhasil masuk
          ↓
Periksa status orientasi
          ↓
Sudah pernah mengisi?
     ↙           ↘
   Ya             Tidak
   ↓                ↓
Dashboard       Popup Orientasi
                    ↓
             Sumber Informasi
                    ↓
               Minat Pengguna
                    ↓
              Pilihan Profesi
                    ↓
              Simpan Profil
                    ↓
                 Dashboard
```

## 5.2 Pertanyaan Pertama: Mengetahui CVKU dari Mana?

Pertanyaan:

**"Dari mana Anda mengetahui CVKU?"**

Pilihan:

- Instagram.
- TikTok.
- YouTube.
- Facebook.
- Google atau mesin pencari.
- Teman atau rekomendasi orang lain.
- Komunitas atau organisasi.
- Website atau blog.
- Lainnya.

Jika memilih lainnya, pengguna dapat mengisi sumber informasi secara manual.

Data ini digunakan untuk analisis akuisisi pengguna dan efektivitas pemasaran.

## 5.3 Pertanyaan Kedua: Apa yang Anda Minati?

Pertanyaan:

**"Apa yang ingin Anda buat menggunakan CVKU?"**

Pilihan dapat berupa pilihan jamak:

- Website portfolio.
- Website pribadi.
- Website bisnis.
- Website perusahaan.
- Landing page.
- CV atau resume.
- Website untuk kebutuhan profesional.
- Lainnya.

Pengguna dapat memilih lebih dari satu minat.

Data ini digunakan untuk menentukan rekomendasi fitur dan template.

## 5.4 Pertanyaan Ketiga: Apa Profesi Anda?

Pertanyaan:

**"Apa profesi atau bidang pekerjaan Anda saat ini?"**

Pilihan diambil secara dinamis dari database profesi yang dikelola admin.

Contoh:

- Mahasiswa.
- Programmer.
- Web Developer.
- UI/UX Designer.
- Graphic Designer.
- Digital Marketer.
- Content Creator.
- Fotografer.
- Guru.
- Pengusaha.
- Konsultan.
- Lainnya.

Jika memilih lainnya, pengguna dapat memasukkan profesi secara manual.

## 5.5 Pengaturan Orientasi

Ketentuan:

- Hanya ditampilkan ketika pengguna belum menyelesaikan orientasi.
- Dapat dilewati jika pengguna tidak ingin mengisi.
- Dapat dilanjutkan kembali.
- Jawaban dapat diubah melalui pengaturan profil.
- Pengguna dapat memilih beberapa minat.
- Profesi diambil dari daftar yang dikelola admin.
- Sistem menyimpan waktu pengisian dan versi pertanyaan.
- Informasi sumber pemasaran tidak boleh diperlakukan sebagai informasi profil yang wajib.

## 5.6 Penyimpanan Data Orientasi

Data yang disimpan:

| Data | Kegunaan |
|---|---|
| Sumber informasi | Analisis pemasaran |
| Minat pengguna | Personalisasi rekomendasi |
| Profesi | Rekomendasi template |
| Status orientasi | Menentukan apakah popup perlu ditampilkan |
| Waktu pengisian | Riwayat profil |
| Versi pertanyaan | Pengelolaan perubahan formulir |

# 6. Profil dan Personalisasi Pengguna

## 6.1 Pengelolaan Profil

Pengguna dapat mengelola:

- Nama lengkap.
- Foto profil.
- Email.
- Nomor telepon.
- Profesi.
- Deskripsi singkat.
- Minat.
- Sumber informasi awal.
- Akun Google yang terhubung.

## 6.2 Rekomendasi Template

Sistem memberikan rekomendasi template berdasarkan informasi pengguna.

Contoh:

```text
Profil Pengguna

Profesi:
Web Developer

Minat:
Website Portfolio
Website Profesional

Rekomendasi Template:

1. Developer Portfolio
2. Minimalist Portfolio
3. Professional Profile
4. Personal Branding
```

### Aturan Rekomendasi

Prioritas rekomendasi:

1. Kesesuaian profesi.
2. Kesesuaian minat.
3. Kesesuaian tema.
4. Popularitas template.
5. Template terbaru atau unggulan.

Rekomendasi awal dapat menggunakan sistem pencocokan berbasis tag, tanpa perlu AI.

Pengguna tetap dapat melihat semua template dan tidak dibatasi hanya pada rekomendasi.

# 7. Dashboard Pengguna

Dashboard merupakan pusat pengelolaan akun.

Informasi:

- Ringkasan website.
- Jumlah website.
- Website yang telah dipublikasikan.
- Website dalam bentuk draf.
- Layanan aktif.
- Masa berlaku layanan.
- Penggunaan penyimpanan.
- Rekomendasi template.
- Riwayat transaksi.
- Notifikasi.

Menu utama yang disarankan:

1. Ringkasan.
2. Website Saya.
3. Buat Website.
4. Pembuat CV ATS.
5. Layanan Saya.
6. Riwayat Transaksi.
7. Profil Saya.
8. Pengaturan.

# 8. Pembuat Website

## 8.1 Membuat Website

Pengguna dapat membuat website melalui alur:

1. Memilih template.
2. Mengisi nama website.
3. Menentukan alamat subdomain.
4. Membuat website.
5. Masuk ke editor visual.

## 8.2 Editor Visual

Komponen editor:

- Area pratinjau website.
- Daftar bagian website.
- Pengaturan komponen.
- Pengaturan teks.
- Pengaturan gambar.
- Pengaturan warna.
- Pengaturan tata letak.
- Pratinjau desktop.
- Pratinjau tablet.
- Pratinjau mobile.
- Simpan perubahan.
- Publikasikan website.

## 8.3 Pengelolaan Bagian Website

Pengguna dapat:

- Menambahkan bagian.
- Menghapus bagian.
- Mengubah urutan bagian.
- Mengaktifkan dan menonaktifkan bagian.
- Mengedit isi bagian.

## 8.4 Simpan Otomatis

Perubahan dapat disimpan secara otomatis.

Sistem harus menampilkan status penyimpanan dan menangani kegagalan penyimpanan.

## 8.5 Publikasi Website

Fitur:

- Menerbitkan website.
- Memperbarui website.
- Membatalkan publikasi.
- Melihat status publikasi.
- Membuka website publik.

# 9. Pengelolaan Website

## 9.1 Subdomain

Setiap website dapat menggunakan subdomain CVKU.

Contoh:

`imam.cvku.giize.com`

Fitur:

- Menentukan subdomain.
- Memeriksa ketersediaan alamat.
- Mengubah subdomain sesuai kebijakan.
- Melihat status domain.

## 9.2 Domain Pribadi

Pengguna dapat menghubungkan domain sendiri jika layanan yang dimiliki mendukungnya.

Fitur:

- Menambahkan domain.
- Verifikasi DNS.
- Pengaturan domain utama.
- Status SSL.
- Menghapus domain.

## 9.3 Analitik Website

Informasi:

- Jumlah kunjungan.
- Pengunjung unik.
- Halaman populer.
- Sumber pengunjung.
- Jenis perangkat.
- Riwayat kunjungan berdasarkan periode.

# 10. Pembuat CV ATS Gratis

<badge color="success">Fitur utama baru</badge>

CVKU menyediakan fitur pembuatan Curriculum Vitae yang dapat digunakan secara gratis oleh pengguna.

Fitur ini merupakan produk tersendiri di dalam CVKU dan tidak harus bergantung pada langganan website builder.

Pengguna dapat mengisi data diri, pengalaman, pendidikan, keterampilan, dan informasi profesional lainnya. Sistem kemudian menyusun informasi tersebut ke dalam template CV yang dipilih dan menghasilkan dokumen PDF.

## 10.1 Halaman Pembuat CV ATS

Menu:

**Pembuat CV ATS**

Konten halaman:

- Penjelasan mengenai CV ATS.
- Daftar template CV ATS.
- Tombol mulai membuat CV.
- Informasi bahwa fitur pembuatan dan ekspor PDF tersedia gratis.

## 10.2 Pemilihan Template CV ATS

Pengguna dapat memilih template sebelum mulai mengisi CV.

Fitur:

- Galeri template CV.
- Pratinjau template.
- Melihat nama template.
- Melihat deskripsi template.
- Memilih template.
- Mengganti template sebelum atau sesudah pengisian.

Template harus berasal dari template yang telah dipublikasikan admin.

## 10.3 Formulir Data CV

Formulir dibagi menjadi beberapa bagian.

### A. Informasi Pribadi

- Nama lengkap.
- Alamat email.
- Nomor telepon.
- Domisili.
- Tautan LinkedIn.
- Tautan portfolio.
- Tautan GitHub atau platform profesional lainnya.

Foto profil tidak perlu diwajibkan karena format CV ATS sebaiknya mengutamakan struktur teks yang mudah dibaca sistem rekrutmen.

### B. Ringkasan Profesional

Pengguna dapat menuliskan ringkasan mengenai:

- Latar belakang.
- Pengalaman.
- Keahlian utama.
- Tujuan karier.

### C. Pengalaman Kerja

Informasi:

- Nama perusahaan.
- Posisi.
- Lokasi.
- Tanggal mulai.
- Tanggal selesai.
- Deskripsi pekerjaan.
- Pencapaian.

Pengguna dapat menambahkan beberapa pengalaman kerja.

### D. Pendidikan

Informasi:

- Institusi.
- Jenjang pendidikan.
- Program studi.
- Tahun mulai.
- Tahun selesai.
- Deskripsi tambahan.

### E. Keterampilan

Pengguna dapat menambahkan:

- Keterampilan teknis.
- Keterampilan nonteknis.
- Bahasa.
- Tools atau teknologi.

### F. Proyek

Informasi:

- Nama proyek.
- Deskripsi.
- Peran.
- Teknologi yang digunakan.
- Tautan proyek.

### G. Sertifikasi dan Penghargaan

Informasi:

- Nama sertifikat.
- Institusi penerbit.
- Tahun penerbitan.
- Tautan verifikasi jika tersedia.

### H. Organisasi dan Pengalaman Tambahan

Informasi:

- Nama organisasi.
- Jabatan.
- Periode.
- Deskripsi kontribusi.

Bagian tambahan dapat diaktifkan atau dilewati sesuai kebutuhan pengguna.

## 10.4 Pratinjau CV

Pengguna dapat melihat hasil CV sebelum diekspor.

Fitur:

- Pratinjau langsung.
- Perubahan data.
- Penggantian template.
- Pengaturan urutan bagian jika template mendukungnya.
- Pemeriksaan kelengkapan informasi.
- Pratinjau ukuran halaman.

## 10.5 Ekspor PDF

Pengguna dapat mengunduh CV dalam format PDF secara gratis.

Ketentuan:

- PDF harus memiliki teks yang dapat dipilih.
- Dokumen tidak boleh hanya berupa gambar.
- Struktur heading harus jelas.
- Tata letak sederhana dan konsisten.
- Penggunaan tabel kompleks dan elemen dekoratif yang mengganggu pembacaan ATS harus dihindari.
- Teks harus memiliki urutan baca yang logis.
- Font harus terbaca.
- Ukuran halaman mengikuti format dokumen yang dipilih.

Nama file dapat menggunakan format:

`CV_NamaPengguna.pdf`

## 10.6 Penyimpanan CV

Pengguna dapat:

- Menyimpan CV sebagai draf.
- Membuka kembali CV.
- Mengedit CV.
- Mengganti template.
- Mengunduh ulang PDF.
- Membuat beberapa CV dengan tujuan pekerjaan berbeda.

Contoh:

- CV Web Developer.
- CV Frontend Developer.
- CV Digital Marketing.

Jumlah CV yang dapat disimpan dapat ditentukan melalui kebijakan platform. Namun, pembuatan dan ekspor CV dasar tetap gratis.

## 10.7 Pemeriksaan Kualitas CV

Sistem dapat memberikan pemeriksaan sederhana:

- Kelengkapan informasi kontak.
- Kejelasan ringkasan profesional.
- Kelengkapan pengalaman.
- Konsistensi tanggal.
- Kelengkapan keterampilan.
- Penggunaan tautan profesional.

Sistem boleh memberikan indikator kelengkapan, tetapi tidak boleh menjanjikan bahwa CV pasti lolos ATS atau pasti diterima perusahaan.

# 11. Pengelolaan Template CV ATS oleh Admin

<badge color="success">Fitur admin baru</badge>

Admin memiliki modul khusus untuk mengelola template CV ATS.

Modul ini terpisah dari pengelolaan template website karena struktur dan kebutuhan teknisnya berbeda.

## 11.1 Daftar Template CV ATS

Admin dapat:

- Melihat semua template.
- Mencari template.
- Memfilter berdasarkan status.
- Melihat pratinjau.
- Mengedit template.
- Mengarsipkan template.
- Mempublikasikan template.

## 11.2 Membuat Template CV ATS

Admin dapat membuat template CV baru melalui editor khusus.

Informasi template:

- Nama template.
- Deskripsi.
- Kategori.
- Thumbnail.
- Status.
- Versi template.

## 11.3 Editor Template CV ATS

Admin dapat mengatur:

- Ukuran kertas.
- Margin.
- Jenis font.
- Ukuran font.
- Jarak antarbagian.
- Warna teks.
- Warna aksen.
- Urutan bagian.
- Format heading.
- Tata letak informasi.
- Pemisah antarbagian.

Admin dapat mengatur struktur template menggunakan komponen yang telah disediakan developer.

Contoh struktur:

```text
Template CV ATS
│
├── Header
│   ├── Nama Lengkap
│   ├── Email
│   ├── Nomor Telepon
│   └── Tautan Profesional
│
├── Ringkasan Profesional
│
├── Pengalaman Kerja
│
├── Pendidikan
│
├── Keterampilan
│
├── Proyek
│
└── Sertifikasi
```

## 11.4 Pratinjau Template

Admin dapat melihat hasil template menggunakan data contoh.

Pratinjau harus menunjukkan hasil dokumen yang mendekati hasil ekspor PDF.

## 11.5 Publikasi Template

Status template:

- Draf.
- Menunggu pemeriksaan.
- Dipublikasikan.
- Diarsipkan.

Template yang masih berstatus draf tidak dapat digunakan oleh pengguna.

## 11.6 Versi Template

Setiap perubahan template yang dipublikasikan harus menghasilkan versi baru.

CV pengguna yang sudah dibuat tidak boleh berubah secara otomatis ketika admin memperbarui template.

## 11.7 Pengujian ATS

Sebelum template dipublikasikan, sistem sebaiknya melakukan pemeriksaan:

- Apakah teks dapat diekstrak dari PDF?
- Apakah urutan teks benar?
- Apakah heading dapat dikenali?
- Apakah karakter khusus terbaca?
- Apakah struktur dokumen tidak rusak?
- Apakah hasil PDF sesuai dengan pratinjau?

Tujuannya memastikan template memiliki struktur yang ramah pembaca dokumen dan sistem ATS.

# 12. Layanan dan Langganan

Admin dapat membuat layanan secara dinamis.

Contoh:

- Dasar.
- Profesional.
- Bisnis.
- Seumur Hidup.

Setiap layanan dapat memiliki entitlement:

- Batas jumlah website.
- Kapasitas penyimpanan.
- Akses template.
- Custom domain.
- Analitik.
- Fitur premium.

Fitur:

- Membuat layanan.
- Mengedit layanan.
- Mengatur harga.
- Mengatur periode pembayaran.
- Mengatur batas penggunaan.
- Mengaktifkan atau menonaktifkan layanan.

Hak akses harus diperiksa oleh server, bukan hanya disembunyikan pada tampilan frontend.

# 13. Transaksi dan Pembayaran

Fitur:

- Checkout layanan.
- Ringkasan transaksi.
- Kode promo.
- Perhitungan harga akhir.
- Integrasi payment gateway.
- Konfirmasi pembayaran.
- Riwayat transaksi.
- Refund sesuai kebijakan.

Harga dan diskon harus dihitung ulang di server.

Transaksi dengan diskon 100% tetap harus tercatat sebagai transaksi dengan nilai pembayaran nol.

# 14. Pengelolaan Kode Promo

Admin dapat membuat kode promo secara manual atau otomatis.

Jenis diskon:

| Jenis | Keterangan |
|---|---|
| Persentase | Diskon berdasarkan persentase |
| Nominal Tetap | Potongan harga dengan nominal tertentu |
| Gratis 100% | Seluruh harga menjadi nol |

Pengaturan:

- Nama promo.
- Kode promo.
- Nilai diskon.
- Layanan yang berlaku.
- Pengguna yang berhak.
- Minimal pembelian.
- Maksimal penggunaan.
- Batas penggunaan per pengguna.
- Tanggal mulai.
- Tanggal berakhir.
- Status aktif.

Admin dapat melihat riwayat penggunaan dan total diskon yang diberikan.

Kode promo admin berbeda dengan kode referral affiliate.

# 15. Program Affiliate

Pengguna dapat memperoleh akses affiliate setelah memenuhi persyaratan yang ditentukan admin.

Fitur:

- Persyaratan affiliate.
- Persetujuan otomatis atau manual.
- Tautan referral.
- Kode referral.
- Statistik referral.
- Riwayat transaksi referral.
- Riwayat komisi.

## 15.1 Dasbor Affiliate

Informasi:

- Total referral.
- Referral berhasil.
- Referral menunggu.
- Total komisi.
- Komisi tersedia.
- Komisi yang telah dibayarkan.

## 15.2 Pengaturan Affiliate oleh Admin

Admin dapat mengatur:

- Syarat menjadi affiliate.
- Persentase komisi.
- Nominal komisi.
- Masa atribusi referral.
- Minimum penarikan.
- Masa tunggu komisi.
- Kebijakan pembatalan komisi.

Komisi dihitung berdasarkan transaksi bersih yang memenuhi syarat setelah diskon.

# 16. Komisi dan Penarikan

Affiliate dapat:

- Melihat komisi.
- Melihat status komisi.
- Mengajukan penarikan.
- Melihat riwayat penarikan.

Admin dapat:

- Melihat pengajuan.
- Menyetujui penarikan.
- Menolak penarikan.
- Memproses pembayaran.
- Mencatat bukti pembayaran.
- Melihat histori penarikan.

Saldo komisi harus dikelola menggunakan pencatatan transaksi yang konsisten agar tidak terjadi penarikan ganda.

# 17. Admin Dashboard

Menu admin:

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

## 17.1 Pengelolaan Profesi

Admin dapat:

- Menambahkan profesi.
- Mengubah nama profesi.
- Mengatur deskripsi.
- Mengatur ikon.
- Mengatur urutan.
- Mengaktifkan profesi.
- Menonaktifkan profesi.

Profesi digunakan oleh:

- Formulir orientasi pengguna.
- Profil pengguna.
- Filter galeri template.
- Sistem rekomendasi template.
- Pengelompokan template.

## 17.2 Pengelolaan Tema Template

Admin dapat:

- Menambahkan tema.
- Mengedit tema.
- Mengatur deskripsi.
- Mengatur urutan.
- Mengaktifkan atau menonaktifkan tema.

## 17.3 Pengelolaan Template Website

Admin dapat:

- Membuat template.
- Mengatur nama dan deskripsi.
- Memilih tema.
- Menentukan profesi yang relevan.
- Menambahkan komponen.
- Mengatur tata letak.
- Melihat pratinjau.
- Membuat versi.
- Mempublikasikan template.

## 17.4 Pengelolaan Template CV ATS

Admin memiliki editor terpisah untuk membuat dan mengatur template CV ATS.

Admin dapat mengelola struktur, tipografi, margin, urutan bagian, pratinjau, dan publikasi template.

## 17.5 Pengelolaan Orientasi Pengguna

Admin dapat mengelola daftar pilihan orientasi yang memang bersifat dinamis, seperti daftar profesi dan pilihan minat.

Untuk pertanyaan sumber informasi, admin dapat mengelola pilihan sumber yang tersedia dan melihat statistik jawabannya.

# 18. Notifikasi

Notifikasi ditampilkan melalui dashboard dan email.

Contoh:

- Selamat datang di CVKU.
- Website berhasil dipublikasikan.
- Perubahan website berhasil disimpan.
- Pembayaran berhasil.
- Langganan hampir berakhir.
- CV berhasil diekspor.
- Affiliate disetujui.
- Komisi tersedia.
- Penarikan diproses.

# 19. Keamanan dan Sistem

Fitur sistem:

- Autentikasi aman.
- Google OAuth.
- Role-based access control.
- Pemeriksaan kepemilikan website.
- Validasi server.
- Pembatasan percobaan login.
- Validasi unggahan file.
- Verifikasi webhook pembayaran.
- Audit log.
- Background jobs.
- Isolasi data antar pengguna.
- Pengelolaan sesi.

Role utama:

```text
USER
ADMIN
```

Affiliate menggunakan profil tambahan yang terhubung dengan akun USER.

# 20. Prioritas Pengembangan

## Tahap 1 — Fondasi Platform

- [ ] Landing Page.
- [ ] Dark Mode dan Light Mode.
- [ ] Registrasi dan login.
- [ ] Login dengan Google.
- [ ] Pemulihan kata sandi.
- [ ] Dashboard pengguna.
- [ ] Profil pengguna.
- [ ] Orientasi pengguna baru.
- [ ] Pengelolaan profesi.
- [ ] Pengelolaan tema.
- [ ] Galeri template.
- [ ] Rekomendasi template dasar.

## Tahap 2 — Website Builder

- [ ] Pengelolaan layanan.
- [ ] Sistem entitlement.
- [ ] Pengelolaan template website.
- [ ] Editor visual.
- [ ] Pengelolaan konten.
- [ ] Pratinjau.
- [ ] Simpan otomatis.
- [ ] Publikasi website.
- [ ] Subdomain CVKU.

## Tahap 3 — Pembuat CV ATS

- [ ] Halaman pembuat CV ATS.
- [ ] Pengelolaan template CV ATS oleh admin.
- [ ] Editor template CV ATS.
- [ ] Formulir data CV.
- [ ] Pratinjau CV.
- [ ] Penyimpanan CV.
- [ ] Ekspor PDF.
- [ ] Pengujian ekstraksi teks PDF.

Fitur ini tetap gratis dan tidak memerlukan langganan website builder.

## Tahap 4 — Transaksi dan Monetisasi

- [ ] Checkout.
- [ ] Payment gateway.
- [ ] Langganan.
- [ ] Riwayat transaksi.
- [ ] Kode promo.
- [ ] Diskon 100%.
- [ ] Pengelolaan kuota promo.

## Tahap 5 — Affiliate

- [ ] Persyaratan affiliate.
- [ ] Dasbor affiliate.
- [ ] Tautan referral.
- [ ] Pelacakan referral.
- [ ] Perhitungan komisi.
- [ ] Penarikan komisi.
- [ ] Pengelolaan affiliate oleh admin.

## Tahap 6 — Pengembangan Lanjutan

- [ ] Domain pribadi.
- [ ] Analitik lanjutan.
- [ ] Duplikasi website.
- [ ] Pencadangan dan pemulihan website.
- [ ] Pengaturan SEO.
- [ ] Formulir kontak.
- [ ] Asisten AI pembuat konten.
- [ ] Pemeriksaan kualitas CV.
- [ ] Analitik rekomendasi template.

# 21. Aturan Bisnis Penting

| No. | Aturan | Ketentuan |
|---:|---|---|
| 1 | Bahasa | Seluruh antarmuka menggunakan Bahasa Indonesia |
| 2 | Akun | Satu pengguna dapat memiliki beberapa website |
| 3 | Google Login | Google hanya digunakan untuk autentikasi |
| 4 | Orientasi | Popup hanya muncul ketika pengguna belum menyelesaikan orientasi |
| 5 | Profesi | Daftar profesi dikelola admin |
| 6 | Tema | Daftar tema dikelola admin |
| 7 | Rekomendasi | Berdasarkan profesi, minat, tema, dan relevansi |
| 8 | Template Website | Website mengunci versi template yang digunakan |
| 9 | Template CV | Dikelola terpisah dari template website |
| 10 | CV ATS | Pembuatan dan ekspor PDF tersedia gratis |
| 11 | PDF | Dokumen harus memiliki teks yang dapat diekstrak |
| 12 | Layanan | Hak akses mengikuti entitlement |
| 13 | Promo | Diskon dihitung dan divalidasi oleh server |
| 14 | Affiliate | Affiliate merupakan profil tambahan pengguna |
| 15 | Komisi | Komisi dihitung berdasarkan transaksi yang memenuhi syarat |
| 16 | Kepemilikan | Pengguna tidak dapat mengakses data pengguna lain |
| 17 | Versi | Perubahan template tidak mengubah dokumen lama secara otomatis |
| 18 | Keamanan | Operasi sensitif harus divalidasi oleh server |

# 22. Target Akhir Produk

CVKU dikembangkan sebagai platform yang memiliki dua layanan utama:

**A. Website Builder**

Membantu pengguna membuat website profesional melalui pemilihan template dan editor visual tanpa perlu kemampuan pemrograman.

**B. Pembuat CV ATS**

Membantu pengguna menyusun Curriculum Vitae yang terstruktur, ramah terhadap sistem pembaca CV, dan dapat diekspor ke PDF secara gratis.

Kedua layanan didukung oleh sistem pengelolaan terpusat yang memungkinkan admin mengatur template, profesi, tema, layanan, harga, promosi, dan ekosistem affiliate.

**Tujuan akhir:** CVKU menjadi platform terpadu untuk membangun identitas profesional secara digital, baik melalui website portfolio maupun dokumen CV yang siap digunakan untuk melamar pekerjaan.