# UI/UX Design Specification
## MiniBook — Bootstrap 5

| Informasi | Keterangan |
|---|---|
| Produk | MiniBook |
| Jenis aplikasi | Responsive web application |
| Framework CSS | **Bootstrap 5** |
| Dokumen sumber | `Design.pdf` (7 halaman) |
| Referensi kebutuhan | `SRS.docx` |
| Versi dokumen | 1.0 |
| Bahasa antarmuka | Bahasa Indonesia |

> Dokumen ini menerjemahkan mockup pada `Design.pdf` menjadi spesifikasi antarmuka yang dapat diimplementasikan menggunakan Bootstrap 5. Referensi halaman: Jadwal (hlm. 1), Pemesanan (hlm. 2), Riwayat (hlm. 3–5), Dashboard Admin harian (hlm. 6), dan Dashboard Admin bulanan (hlm. 7). Warna dan ukuran yang dicantumkan adalah nilai pendekatan dari visual mockup dan dapat disesuaikan saat implementasi.

---

## 1. Prinsip Desain

1. **Responsive first:** layar nyaman digunakan pada desktop, tablet, dan smartphone.
2. **Jelas dan ringkas:** jadwal, harga, status, dan tindakan penting mudah dipindai.
3. **Konsisten:** sidebar, header, kartu, tombol, badge, dan pola status digunakan secara konsisten di semua halaman.
4. **Berorientasi tugas:** pelanggan diarahkan dari memilih slot ke pengisian data dan pembayaran; admin diarahkan ke verifikasi dan pengelolaan jadwal.
5. **Status mudah dibedakan:** warna status tersedia, terisi, menunggu verifikasi, disetujui/lunas, dan dibatalkan tidak hanya mengandalkan warna, tetapi juga label teks.

## 2. Design Language

### 2.1 Palet Warna

Nilai berikut merupakan perkiraan berdasarkan mockup pada Design.pdf.

| Token | Hex perkiraan | Penggunaan |
|---|---|---|
| `--mb-primary` | `#07866B` | Brand, tombol utama, navigasi aktif, status positif |
| `--mb-primary-dark` | `#07634F` | Hover/active tombol utama dan teks pada aksen |
| `--mb-primary-soft` | `#EAF6F1` | Background terpilih, panel informasi, highlight |
| `--mb-page-bg` | `#F5F7F8` | Background halaman |
| `--mb-surface` | `#FFFFFF` | Kartu, panel, tabel, form |
| `--mb-text` | `#263633` | Judul dan teks utama |
| `--mb-muted` | `#87938F` | Deskripsi, label sekunder |
| `--mb-border` | `#E5EBE8` | Garis tepi dan pemisah |
| `--mb-danger` | `#D85F76` | Status batal/terisi dan aksi pembatalan |
| `--mb-danger-soft` | `#FFF0F2` | Background slot terisi/pesan pembatalan |
| `--mb-warning` | `#A97718` | Status menunggu verifikasi |
| `--mb-warning-soft` | `#FFF5DD` | Badge menunggu verifikasi |
| `--mb-info-soft` | `#EEF6FA` | Panel kategori harga siang |
| `--mb-purple-soft` | `#F4F0FA` | Panel kategori harga malam |

Warna utama hijau digunakan sebagai identitas MiniBook. Gunakan warna aksen secara hemat dan pastikan teks memiliki kontras yang memadai.

### 2.2 Tipografi

- Gunakan system font stack agar ringan dan konsisten lintas perangkat: `system-ui, -apple-system, "Segoe UI", Roboto, Arial, sans-serif`.
- Judul halaman: sekitar 24–32 px pada desktop; ukuran lebih kecil pada mobile.
- Judul kartu: 16–18 px.
- Isi dan label: 13–16 px; informasi tabel tetap terbaca pada layar kecil.
- Nilai nominal rupiah dan angka statistik menggunakan bobot font medium/semibold.
- Hindari penggunaan terlalu banyak variasi ukuran dan ketebalan font.

### 2.3 Spacing, Border, dan Elevation

- Gunakan skala spacing Bootstrap (`p-2`, `p-3`, `p-4`, `gap-2`, `gap-3`, `mb-3`).
- Kartu utama menggunakan `border` tipis, background putih, dan radius sekitar 12–16 px.
- Hindari shadow berat; gunakan `shadow-sm` bila dibutuhkan.
- Beri jarak yang cukup antara judul halaman, deskripsi, filter, dan konten utama.
- Background area kerja menggunakan warna abu-abu sangat muda, sedangkan konten berada di dalam kartu putih.

### 2.4 Status dan Indikator

| Status | Label UI | Treatment visual |
|---|---|---|
| Slot tersedia | Tersedia | Titik/badge hijau dan latar putih |
| Slot sudah dipesan | Terisi | Badge/titik merah dan latar merah muda |
| Menunggu verifikasi | Menunggu Verifikasi | Badge kuning lembut |
| Pembayaran disetujui | Disetujui/Lunas | Badge hijau lembut |
| Dibatalkan | Batal | Badge merah lembut |
| Slot tidak dapat digunakan | Maintenance | Gunakan badge netral/abu-abu; status ini terlihat pada kontrol slot, tetapi perlu dikonfirmasi sebagai status resmi sistem |

Jangan gunakan warna saja untuk menyampaikan status. Sertakan label teks untuk aksesibilitas.

---

## 3. Arsitektur Layout Aplikasi

### 3.1 App Shell

Tampilan pada seluruh halaman menggunakan kerangka yang sama:

- **Sidebar kiri:** logo MiniBook, menu utama, kelompok menu pengelola, kartu lokasi Minisoccer Ngabang, indikator Live Order, bantuan, dan footer.
- **Topbar:** breadcrumb lokasi/halaman, indikator Live Order, avatar/inisial, dan menu pengguna.
- **Main content:** judul halaman, deskripsi, aksi utama, filter, dan konten.
- **Page background:** abu-abu muda; kartu konten berwarna putih.

### 3.2 Navigasi Sidebar

| Grup | Item | Keterangan |
|---|---|---|
| Menu Utama | Jadwal | Melihat kalender dan slot ketersediaan lapangan |
| Menu Utama | Pemesanan | Mengisi data dan mengirim pemesanan |
| Menu Utama | Riwayat | Melihat daftar dan status pemesanan |
| Pengelola | Dashboard Admin | Operasional, verifikasi, pengendalian slot, dan laporan |

Sidebar menampilkan item aktif dengan latar hijau lembut, teks hijau gelap, dan ikon. Kartu lokasi menampilkan **Minisoccer Ngabang**, **Kalimantan Barat**, serta indikator **Live Order**.

### 3.3 Responsivitas

| Ukuran layar | Perilaku |
|---|---|
| Desktop (`lg` ke atas) | Sidebar tetap terlihat di kiri; konten utama menggunakan sisa lebar layar. |
| Tablet (`md`) | Sidebar dapat dipadatkan atau ditampilkan melalui offcanvas; susunan kartu menyesuaikan lebar. |
| Mobile (di bawah `md`) | Sidebar dibuka melalui tombol menu Bootstrap Offcanvas; konten menjadi satu kolom; grid slot dan kartu statistik menyesuaikan lebar; tabel riwayat dapat digulir horizontal atau diubah menjadi daftar kartu. |

**Rekomendasi implementasi Bootstrap 5:**
- Gunakan `.container-fluid` untuk area aplikasi.
- Gunakan `.row` dan `.col-*` untuk grid.
- Gunakan pola `.offcanvas` dengan tombol toggler untuk navigasi mobile agar kompatibel dengan Bootstrap 5 tanpa bergantung pada kelas responsive offcanvas dari versi minor tertentu.
- Gunakan `.navbar` untuk topbar bila diperlukan.
- Gunakan `.d-none`, `.d-lg-block`, dan utility responsive untuk mengatur visibilitas elemen.

---

## 4. Spesifikasi Halaman

## 4.1 Halaman Jadwal dan Ketersediaan Lapangan

**Referensi:** Design.pdf halaman 1.

### Tujuan

Membantu pelanggan memilih tanggal dan slot bermain yang tersedia berdasarkan harga dan kategori waktu.

### Struktur Konten

1. Page header:
   - Judul: **Waktunya turun ke lapangan.**
   - Deskripsi: **Pilih tanggal dan jam bermain untuk tim kamu.**
   - Tombol/tanggal: **Hari ini, [tanggal]**.
2. Pemilih tanggal:
   - Menampilkan tanggal beberapa hari dalam satu baris.
   - Hari/tanggal aktif menggunakan background hijau.
3. Area ketersediaan:
   - Judul **Ketersediaan lapangan**.
   - Legend **Tersedia** dan **Terisi**.
   - Kartu slot per jam.
4. Panel kategori harga:
   - Kategori Siang, Sore, Malam.
   - Tarif reguler dan tarif pelajar.
   - Keterangan diskon pelajar/mahasiswa sesuai kebijakan final.
5. Panel ringkasan slot:
   - Empty state **Belum ada slot dipilih**.
   - Instruksi untuk memilih jam.
   - Jumlah slot yang dipilih.

### Kartu Slot

Setiap kartu slot menampilkan:

- Rentang jam, misalnya `08:00–09:00`.
- Kategori waktu (Siang/Sore/Malam).
- Harga per slot.
- Status Tersedia/Terisi.
- Keadaan terpilih saat pelanggan memilih slot.

**State komponen:**

| State | Tampilan | Interaksi |
|---|---|---|
| Available | Kartu putih, indikator hijau, label Tersedia | Dapat dipilih |
| Booked | Kartu merah muda, indikator merah, label Terisi | Tidak dapat dipilih |
| Selected | Border/aksen hijau dan penanda pilihan | Dapat dibatalkan pilihannya |
| Maintenance | Tampilan nonaktif/netral bila status ini disepakati | Tidak dapat dipilih |

### Grid dan Breakpoint

- Desktop: area slot menggunakan tiga kolom, panel harga/ringkasan berada di kolom samping.
- Tablet: dua kolom slot bila lebar mencukupi; panel samping turun ke bawah.
- Mobile: satu kolom atau dua kolom sempit sesuai ruang; panel harga dan ringkasan ditempatkan di bawah daftar slot.

**Komponen Bootstrap 5:**
- `.row`, `.col-lg-8`, `.col-lg-4`
- `.card`, `.card-body`, `.border`, `.rounded-3`
- `.badge`, `.btn`, `.btn-outline-*`
- `.nav` atau `.nav-pills` untuk pilihan tanggal bila sesuai
- `.d-flex`, `.justify-content-between`, `.align-items-center`

### Data Harga yang Ditampilkan pada Mockup

| Kategori | Jam pada mockup halaman 1 | Reguler | Pelajar |
|---|---|---:|---:|
| Siang | 08.00–14.00 | Rp100.000 | Rp80.000 |
| Sore | 15.00–17.00 | Rp150.000 | Rp120.000 |
| Malam | 18.00–22.00 | Rp200.000 | Rp160.000 |

Mockup juga menampilkan keterangan **Pelajar/Mahasiswa hemat 20%**. Nominal dan persentase di atas adalah data yang terlihat pada mockup; konfirmasi sebagai tarif final tetap diperlukan.

**Catatan konsistensi waktu:** Dashboard harian/bulanan pada halaman 6–7 menampilkan kategori malam `18:00–23:00`, sementara panel harga pada halaman 1 menampilkan `18:00–22:00`. Daftar slot juga menampilkan slot `22:00–23:00`. Gunakan konfigurasi tarif dan slot yang dapat diubah; jangan menanamkan rentang jam sebagai nilai tetap sebelum Owner mengonfirmasinya.

---

## 4.2 Halaman Pemesanan Lapangan

**Referensi:** Design.pdf halaman 2.

### Tujuan

Mengumpulkan data pemesan, menampilkan ringkasan slot dan biaya, menerima bukti transfer, serta memperoleh persetujuan terhadap aturan pembatalan.

### Struktur Konten

1. Page header:
   - Judul **Pemesanan lapangan**.
   - Deskripsi **Lengkapi data tim dan unggah bukti pembayaran kamu.**
   - Tombol **Kembali ke jadwal**.
2. Stepper:
   - `1 Pilih slot`
   - `2 Data pemesan`
   - `3 Pembayaran`
3. Kolom utama:
   - Kartu **Data pemesan**.
   - Kartu **Metode pembayaran transfer**.
   - Area **Upload bukti transfer**.
4. Kolom ringkasan:
   - Kartu **Slot dipilih**.
   - Kartu **Ringkasan pembayaran**.
   - Checkbox persetujuan denda pembatalan.
   - Tombol **Kirim Pesanan Sekarang**.
   - Catatan pesanan diverifikasi oleh pengelola.

### Field Form

| Field | Jenis kontrol | Ketentuan |
|---|---|---|
| Nama lengkap | Text input | Contoh placeholder: Budi Santoso |
| Nama tim/komunitas | Text input | Contoh placeholder: Ngabang FC |
| Nomor WhatsApp | Tel input/text input | Nomor yang dapat dihubungi |
| Kategori Pelajar/Mahasiswa | Checkbox | Memilih kategori tarif khusus jika memenuhi kebijakan |
| Persetujuan ketentuan pembatalan | Checkbox wajib | Menyetujui informasi denda 50% |
| Bukti transfer | File upload | JPG, PNG, atau screenshot; maksimal 5 MB sebagaimana mockup |

### Informasi Pembayaran

- Metode pembayaran yang diperlihatkan adalah transfer bank.
- Mockup menampilkan rekening Mandiri dan BCA atas nama MiniBook Ngabang.
- Nomor rekening disajikan sebagai informasi konfigurasi pengelola, bukan teks yang ditanam permanen di antarmuka.
- Sediakan tombol **Salin** untuk menyalin nomor rekening.
- Payment gateway online tidak termasuk ruang lingkup tahap awal.

### Ringkasan Pembayaran

Menampilkan:
- Slot yang dipilih.
- Harga lapangan.
- Total pembayaran.
- Informasi potongan kategori pelajar/mahasiswa apabila berlaku.
- Persetujuan denda pembatalan.
- Tombol kirim pesanan.

### Validasi dan State

- Jika belum ada slot, tampilkan empty state **Belum Ada Slot** dan arahan kembali ke Jadwal.
- Field wajib tidak boleh kosong.
- Format nomor WhatsApp perlu divalidasi.
- File harus berada dalam format yang diterima dan ukuran maksimal 5 MB.
- Tombol kirim harus memberi umpan balik proses dan hasil.
- Jika pengiriman gagal karena jaringan, tampilkan pesan galat dan sediakan tindakan kirim ulang.
- Jangan menampilkan status berhasil sebelum server mengonfirmasi bahwa pesanan tersimpan.

**Komponen Bootstrap 5:**
- `.form-label`, `.form-control`, `.form-check`, `.invalid-feedback`
- `.card`, `.row`, `.col-lg-7`, `.col-lg-5`
- `.progress` atau stepper berbasis `.nav`
- `.alert`, `.btn`, `.input-group`
- Area upload dapat menggunakan `<input type="file">` yang ditata sebagai dropzone melalui CSS kustom.

---

## 4.3 Halaman Riwayat Pemesanan

**Referensi:** Design.pdf halaman 3–5.

### Tujuan

Memudahkan pelanggan memantau seluruh booking, status verifikasi, jadwal, jumlah pembayaran, dan rincian tiket digital.

### Struktur Konten

1. Page header:
   - Judul **Riwayat pesanan**.
   - Deskripsi **Pantau status pembayaran dan jadwal bermain tim kamu.**
   - Tombol **Booking baru**.
2. Kartu ringkasan:
   - Semua pesanan.
   - Menunggu verifikasi.
   - Disetujui/Lunas.
3. Filter daftar:
   - Semua.
   - Menunggu.
   - Lunas.
   - Batal.
4. Pencarian:
   - Placeholder **Cari nama atau kode pesanan**.
5. Tabel riwayat:
   - Pemesan.
   - Jadwal.
   - Jam slot.
   - Total bayar.
   - Status.
   - Aksi.
6. Panel informasi:
   - Penjelasan proses verifikasi.
   - Ketentuan pembatalan dan denda 50%.
7. Pagination.

### Kolom Tabel

| Kolom | Isi |
|---|---|
| Pemesan | Nama, nama tim/komunitas, kode booking |
| Jadwal | Tanggal/hari penyewaan |
| Jam slot | Rentang jam dan durasi |
| Total bayar | Nilai transaksi |
| Status | Menunggu Verifikasi / Disetujui-Lunas / Batal |
| Aksi | Tombol Batalkan dan informasi Denda 50% sesuai aturan |

### Kondisi Filter pada Mockup

- **Halaman 3:** Semua pesanan; contoh hitungan 3 total, 2 menunggu, 1 disetujui/lunas.
- **Halaman 4:** Filter Menunggu; daftar hanya menampilkan dua pesanan yang menunggu verifikasi.
- **Halaman 5:** Filter Lunas; daftar hanya menampilkan satu pesanan yang disetujui/lunas.

Ketiga tampilan tersebut adalah state dari halaman Riwayat yang sama, bukan tiga halaman berbeda.

### Perilaku

- Kartu ringkasan menampilkan jumlah tiap status.
- Filter memperbarui data tabel.
- Pencarian dapat digunakan untuk nama atau kode booking.
- Aksi pembatalan perlu menampilkan konfirmasi sebelum mengubah status.
- Status yang sudah diverifikasi menampilkan akses ke detail tiket digital sesuai kebutuhan SRS.
- Pesanan dibatalkan menampilkan informasi status dan dampak denda sesuai kebijakan.

**Komponen Bootstrap 5:**
- `.card`, `.row`, `.col-md-4`
- `.nav-pills` atau `.btn-group` untuk filter
- `.input-group` untuk pencarian
- `.table-responsive`, `.table`, `.align-middle`
- `.badge` untuk status
- `.pagination`, `.alert`, `.btn`

**Mobile:** tabel dapat dibungkus `.table-responsive`; alternatifnya, tampilkan setiap booking sebagai kartu vertikal dengan label field agar tidak memerlukan scrolling horizontal terlalu jauh.

---

## 4.4 Dashboard Admin — Laporan Harian

**Referensi:** Design.pdf halaman 6.

### Tujuan

Memberikan gambaran kondisi operasional dan pendapatan harian sekaligus menyediakan akses cepat untuk mengelola slot dan memverifikasi pembayaran.

### Struktur Konten

1. Page header **Dashboard Admin** dan deskripsi ringkasan penyewaan harian.
2. Tombol **Unduh Laporan**.
3. Tab **Laporan Harian** dan **Laporan Bulanan**.
4. Penanda tanggal laporan.
5. Kartu KPI:
   - Total pendapatan.
   - Tingkat okupansi slot.
   - Jam prime time tersewa.
6. Panel **Pendapatan per kategori**: Siang, Sore, Malam.
7. Panel **Slot tersewa hari ini**.
8. Panel **Kontrol status slot**.
9. Panel **Verifikasi transaksi masuk**.

### Kartu KPI

| KPI | Data yang ditampilkan |
|---|---|
| Total pendapatan | Nilai rupiah dan periode |
| Tingkat okupansi slot | Persentase dan jumlah slot terisi dibanding slot tersedia pada periode tersebut |
| Jam prime time tersewa | Kategori waktu dan rentang waktu yang paling relevan sesuai data |

### Pendapatan per Kategori

Menampilkan kategori Siang, Sore, Malam, total pendapatan per kategori, dan jumlah slot. Gunakan progress bar atau indikator proporsi untuk membantu pembacaan, seperti visual pada mockup.

### Slot Tersewa Hari Ini

Menampilkan ringkasan booking terkonfirmasi:
- Rentang jam.
- Kategori waktu dan durasi.
- Nama pemesan.
- Nama tim/komunitas.
- Total pembayaran.
- Kode booking dan status.

### Kontrol Status Slot

- Daftar slot jam ditampilkan sebagai tombol kecil/kartu ringkas.
- Admin dapat memilih slot untuk menandai **Maintenance** atau membuka kembali slot, sebagaimana mockup.
- Perubahan status harus tercermin pada halaman Jadwal pelanggan.
- Berikan state visual yang berbeda untuk tersedia, terisi, dan maintenance.
- Gunakan dialog konfirmasi bila perubahan status akan memengaruhi slot yang sudah memiliki booking.

### Verifikasi Transaksi Masuk

Setiap kartu transaksi menampilkan:
- Nama pemesan dan nama tim/komunitas.
- Kode booking.
- Tanggal dan jam slot.
- Nilai pembayaran.
- Aksi **Lihat Struk**, **Setujui**, dan **Tolak**.
- Tombol **Refresh** untuk memperbarui daftar.

Aksi **Tolak** tampak pada mockup; alasan penolakan dan status akhir belum dijelaskan di SRS sehingga perlu dikonfirmasi.

**Komponen Bootstrap 5:**
- `.row`, `.col-xl-*`, `.card`
- `.nav-tabs` atau `.nav-pills`
- `.progress`, `.badge`
- `.table-responsive` atau komponen list/card
- `.btn`, `.btn-success`, `.btn-outline-secondary`, `.btn-danger`
- `.modal` untuk konfirmasi approve/reject/perubahan status slot

---

## 4.5 Dashboard Admin — Laporan Bulanan

**Referensi:** Design.pdf halaman 7.

### Tujuan

Menampilkan ringkasan pendapatan dan pemanfaatan lapangan dalam periode bulanan serta rincian pendapatan per minggu.

### Struktur Konten

1. Header dan tombol **Unduh Laporan**.
2. Tab Laporan Harian dan Laporan Bulanan.
3. Pemilih bulan/periode.
4. Kartu KPI:
   - Total pendapatan bulan ini.
   - Total jam tersewa.
   - Utilisasi lapangan bulanan.
5. Panel **Pendapatan per minggu** berupa grafik batang.
6. Panel **Rincian penyewaan per minggu** berupa tabel periode, pendapatan, dan jam.
7. Bagian bawah menggunakan kontrol slot dan antrean verifikasi yang sama dengan dashboard harian.

### Rincian Mingguan

- Minggu I: 1–7.
- Minggu II: 8–14.
- Minggu III: 15–21.
- Minggu IV: 22–akhir periode sesuai kalender/bulan.

Gunakan label minggu dan rentang tanggal secara dinamis. Nilai nominal pada mockup merupakan contoh data, bukan nilai tetap.

### Komponen Bootstrap 5

- `.row`, `.col-lg-*`, `.card`
- `.table-responsive`, `.table`
- `.nav-tabs`
- Area grafik di dalam card; library grafik tidak ditentukan oleh mockup. Jika memakai library eksternal, implementasikan agar responsif dan sediakan ringkasan data untuk aksesibilitas.

---

## 5. Komponen UI yang Dapat Digunakan Ulang

| Komponen | Tanggung jawab | Elemen Bootstrap 5 |
|---|---|---|
| `AppSidebar` | Navigasi dan identitas lokasi | `.nav`, `.nav-link`, `.offcanvas` |
| `AppTopbar` | Breadcrumb, Live Order, user menu | `.navbar`, `.dropdown`, `.badge` |
| `PageHeader` | Judul, deskripsi, aksi halaman | Heading, `.d-flex`, `.btn` |
| `DateSelector` | Pemilihan tanggal | `.nav`, `.btn-group`, `.card` |
| `SlotCard` | Informasi dan status slot | `.card`, `.badge`, `.btn` |
| `PriceCategoryCard` | Tarif berdasarkan waktu dan pelanggan | `.card`, `.list-group` |
| `BookingStepper` | Tahap pilih slot, data, pembayaran | `.nav`, `.progress` atau CSS kustom |
| `BookingSummary` | Ringkasan slot dan biaya | `.card`, `.list-group` |
| `FileUpload` | Upload bukti transfer | `.form-control`, area dropzone kustom |
| `StatusBadge` | Label status booking | `.badge` dengan kelas warna kustom |
| `BookingTable` | Daftar riwayat | `.table-responsive`, `.table` |
| `MetricCard` | Ringkasan KPI dashboard | `.card`, `.card-body` |
| `SlotStatusControl` | Buka/maintenance slot | `.btn`, `.badge`, `.modal` |
| `VerificationCard` | Bukti transfer dan aksi admin | `.card`, `.btn`, `.modal` |
| `ReportChart` | Grafik pendapatan per minggu | `.card`; canvas/library grafik bila dipilih |

### 5.1 Pola Tombol

- **Primary:** tindakan utama seperti Kirim Pesanan, Setujui, dan Booking Baru.
- **Secondary/outline:** Kembali ke Jadwal, Refresh, Salin, dan Unduh Laporan.
- **Danger:** Batalkan dan Tolak.
- Tombol yang menjalankan perubahan status perlu konfirmasi dan menampilkan umpan balik berhasil/gagal.

### 5.2 Pola Form

- Setiap input memiliki label yang terlihat.
- Placeholder hanya menjadi contoh, bukan pengganti label.
- Pesan validasi diletakkan dekat dengan field terkait.
- Field wajib ditandai secara konsisten.
- Gunakan `.is-invalid` dan `.invalid-feedback` untuk kesalahan validasi.
- Tombol submit dinonaktifkan saat proses pengiriman berlangsung untuk mencegah pengiriman berulang.

---

## 6. Penerapan Bootstrap 5

### 6.1 Dependensi Dasar

Gunakan Bootstrap 5 CSS dan JavaScript bundle. Ikon tidak termasuk dalam paket inti Bootstrap; gunakan Bootstrap Icons sebagai dependensi opsional atau gunakan SVG/icon set yang sudah disepakati tim.

### 6.2 Struktur Layout yang Disarankan

```html
<div class="container-fluid">
  <div class="row min-vh-100">
    <aside class="col-lg-2 d-none d-lg-flex flex-column border-end bg-white">
      <!-- Brand, navigasi, kartu lokasi, bantuan -->
    </aside>

    <main class="col-12 col-lg-10">
      <header class="py-3 border-bottom bg-white">
        <!-- Breadcrumb, Live Order, user menu -->
      </header>

      <section class="p-3 p-lg-4">
        <!-- Page header dan konten halaman -->
      </section>
    </main>
  </div>
</div>
```

Untuk mobile, tambahkan tombol navigasi yang membuka sidebar sebagai `.offcanvas`. Contoh di atas adalah kerangka layout; struktur final dapat menyesuaikan kebutuhan integrasi.

### 6.3 Design Tokens Kustom

```css
:root {
  --mb-primary: #07866b;
  --mb-primary-dark: #07634f;
  --mb-primary-soft: #eaf6f1;
  --mb-page-bg: #f5f7f8;
  --mb-surface: #ffffff;
  --mb-text: #263633;
  --mb-muted: #87938f;
  --mb-border: #e5ebe8;
  --mb-danger: #d85f76;
  --mb-danger-soft: #fff0f2;
  --mb-warning: #a97718;
  --mb-warning-soft: #fff5dd;
}

body {
  color: var(--mb-text);
  background: var(--mb-page-bg);
  font-family: system-ui, -apple-system, "Segoe UI", Roboto, Arial, sans-serif;
}

.mb-card {
  background: var(--mb-surface);
  border: 1px solid var(--mb-border);
  border-radius: 0.875rem;
}

.btn-mb-primary {
  --bs-btn-color: #fff;
  --bs-btn-bg: var(--mb-primary);
  --bs-btn-border-color: var(--mb-primary);
  --bs-btn-hover-bg: var(--mb-primary-dark);
  --bs-btn-hover-border-color: var(--mb-primary-dark);
  --bs-btn-hover-color: #fff;
}
```

### 6.4 Kelas State Slot dan Status Kustom

```css
.mb-slot {
  border: 1px solid var(--mb-border);
  border-radius: 0.75rem;
  background: #fff;
  padding: 0.875rem;
}

.mb-slot.is-available {
  cursor: pointer;
}

.mb-slot.is-booked {
  background: var(--mb-danger-soft);
  border-color: #f5d8de;
  cursor: not-allowed;
}

.mb-slot.is-selected {
  background: var(--mb-primary-soft);
  border: 1px solid var(--mb-primary);
}

.mb-status-pending {
  color: var(--mb-warning);
  background: var(--mb-warning-soft);
}

.mb-status-approved {
  color: var(--mb-primary-dark);
  background: var(--mb-primary-soft);
}

.mb-status-cancelled {
  color: var(--mb-danger);
  background: var(--mb-danger-soft);
}
```

---

## 7. Navigasi dan Peta Halaman

```text
MiniBook
├── Jadwal
│   ├── Pemilih tanggal
│   ├── Daftar slot
│   ├── Kategori harga
│   └── Ringkasan slot terpilih
├── Pemesanan
│   ├── Data pemesan
│   ├── Kategori pelanggan
│   ├── Metode pembayaran transfer
│   ├── Upload bukti transfer
│   └── Ringkasan dan persetujuan
├── Riwayat
│   ├── Semua pesanan
│   ├── Menunggu verifikasi
│   ├── Disetujui/Lunas
│   ├── Batal
│   └── Rincian tiket digital
└── Pengelola
    └── Dashboard Admin
        ├── Laporan harian
        ├── Laporan bulanan
        ├── Pendapatan per kategori/per minggu
        ├── Slot tersewa
        ├── Kontrol status slot
        └── Verifikasi transaksi masuk
```

Rincian tiket digital dicantumkan karena disyaratkan SRS, tetapi layar detailnya belum ditampilkan pada Design.pdf. Halaman login juga tidak termasuk tujuh mockup; SRS mensyaratkan login untuk Admin dan Owner.

---

## 8. Perilaku Sistem dan Umpan Balik UI

| Kejadian | Umpan balik yang ditampilkan |
|---|---|
| Pelanggan memilih tanggal | Daftar slot dan harga untuk tanggal tersebut diperbarui |
| Pelanggan memilih slot | Kartu berubah ke state selected dan ringkasan jumlah slot/biaya diperbarui |
| Slot sudah terisi | Slot nonaktif dengan label Terisi |
| Data form tidak valid | Pesan validasi dekat field |
| Bukti transfer melebihi 5 MB atau format tidak sesuai | Pesan kesalahan upload |
| Pemesanan berhasil dikirim | Tampilkan informasi pesanan menunggu verifikasi dan kode booking setelah server mengonfirmasi |
| Pengiriman gagal | Tampilkan pesan galat dan pilihan mengirim ulang |
| Admin menyetujui pesanan | Status booking berubah, slot diperbarui, dan data tampil pada riwayat pelanggan |
| Admin menolak pesanan | Tampilkan status hasil penolakan; aturan status/unggah ulang perlu ditentukan |
| Admin mengubah status slot | Jadwal pelanggan diperbarui |
| Admin/Owner mengganti periode laporan | KPI dan rincian laporan mengikuti periode terpilih |
| Tidak ada data | Tampilkan empty state yang menjelaskan tindakan berikutnya |

---

## 9. Aksesibilitas dan Usability

- Pastikan rasio kontras teks dan background memadai.
- Jangan mengandalkan warna saja untuk status; sertakan teks dan/atau ikon.
- Semua input memiliki label dan dapat dioperasikan dengan keyboard.
- Tombol memiliki teks tindakan yang jelas.
- Berikan focus state yang terlihat pada link, tombol, tab, dan kartu slot yang dapat dipilih.
- Area klik pada tombol dan slot cukup besar untuk penggunaan layar sentuh.
- Grafik laporan perlu dilengkapi label angka atau tabel ringkasan.
- Uji tampilan pada beberapa ukuran layar dan browser yang disebutkan di SRS.
- Target usability pada SRS adalah alur pemesanan maksimal empat klik; tim perlu mendefinisikan secara operasional titik awal/akhir hitungan klik sebelum pengujian.

---

## 10. Catatan Konsistensi dan Hal yang Perlu Dikonfirmasi

1. **Pembayaran 50% atau 100%:** SRS menyebut pembayaran 50%, sedangkan mockup menampilkan total pembayaran. Pastikan apakah yang dimaksud uang muka (DP) atau pembayaran penuh. Ini berbeda dari denda pembatalan 50%.
2. **Rentang jam kategori:** mockup halaman Jadwal menampilkan malam 18.00–22.00, sedangkan Dashboard menampilkan 18.00–23.00. Slot 22.00–23.00 juga tampak pada grid jadwal.
3. **Slot 12.00–13.00:** slot tersebut tidak terlihat pada contoh grid, walaupun slot lain membentuk 14 slot. Pastikan apakah jam tersebut tidak beroperasi atau terlewat pada mockup.
4. **Tarif:** contoh tarif dan diskon pelajar 20% terlihat di mockup, tetapi SRS tidak menetapkan angka nominal maupun persentasenya. Konfirmasi sebelum dijadikan data produksi.
5. **Status booking:** SRS menggunakan Pending/Verified dan istilah disetujui; UI menggunakan Menunggu Verifikasi, Disetujui/Lunas, Batal, dan aksi Tolak. Tetapkan satu daftar status dan transisinya.
6. **Akun pelanggan:** mockup menampilkan menu Pelanggan, tetapi SRS hanya secara eksplisit mensyaratkan login Admin dan Owner. Tentukan apakah pelanggan memerlukan akun.
7. **Penolakan pembayaran:** mockup memiliki tombol Tolak, tetapi alur, alasan penolakan, dan mekanisme unggah ulang belum didefinisikan.
8. **Maintenance:** kontrol status Maintenance/Membuka muncul pada dashboard, namun status ini belum dirinci dalam kebutuhan dan model data SRS.
9. **Email:** SRS meminta pengiriman tiket/konfirmasi melalui email setelah verifikasi, tetapi desain form tidak menampilkan field email dan mockup belum menunjukkan alur email.
10. **Tiket digital:** SRS mewajibkan rincian tiket digital, tetapi tampilan detailnya belum ada pada Design.pdf.
11. **Hak akses Owner:** mockup hanya menggambarkan Dashboard Admin/pengelola. Tentukan bagian yang boleh dilihat Owner dan bagian yang khusus Admin.
12. **Tanggal dan footer mockup:** halaman memperlihatkan contoh tanggal Oktober 2025 dan footer © 2025, sedangkan SRS bertanggal 2026. Jadikan tanggal dan periode laporan sebagai data dinamis; konfirmasi tahun footer yang digunakan.

---

## 11. Checklist Implementasi UI

- [ ] App shell, sidebar, topbar, breadcrumb, dan responsive offcanvas.
- [ ] Jadwal: date selector, slot card, status slot, kategori harga, ringkasan slot.
- [ ] Pemesanan: stepper, form pemesan, checkbox kategori, ringkasan biaya, informasi transfer, salin rekening, upload bukti.
- [ ] Riwayat: KPI status, filter, search, tabel/list responsif, pembatalan, detail tiket.
- [ ] Dashboard: tab harian/bulanan, KPI, pendapatan kategori, slot tersewa, kontrol slot, verifikasi transaksi.
- [ ] State loading, empty, validation, success, error, dan disabled.
- [ ] Hak akses tampilan sesuai peran.
- [ ] Validasi ukuran dan jenis file upload.
- [ ] Kontras, keyboard navigation, focus state, dan label aksesibel.
- [ ] Uji responsive dan cross-browser.
- [ ] Konfirmasi seluruh keputusan terbuka pada bagian 10 sebelum data produksi digunakan.

---

## 12. Referensi

1. **Design.pdf** — Rancangan antarmuka MiniBook, 7 halaman: Jadwal (hlm. 1), Pemesanan (hlm. 2), Riwayat (hlm. 3–5), Dashboard Admin harian (hlm. 6), dan bulanan (hlm. 7).
2. **SRS.docx** — *Software Requirements Specification (SRS) Aplikasi Web MiniBook*, versi 1.0, 10 Oktober 2026. Digunakan untuk validasi kebutuhan, role, aturan bisnis, dan kebutuhan non-fungsional.
3. **Bootstrap 5** — Kerangka CSS yang diminta untuk implementasi antarmuka. Versi minor Bootstrap 5 dan strategi instalasi perlu dipilih pada tahap setup proyek.
