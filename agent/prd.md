# Product Requirements Document (PRD)
## MiniBook — Sistem Penyewaan Lapangan Minisoccer

| Informasi | Keterangan |
|---|---|
| Nama produk | **MiniBook** |
| Jenis produk | Aplikasi web responsif untuk penyewaan lapangan minisoccer |
| Dokumen sumber | `SRS.docx` |
| Versi dokumen sumber | 1.0 |
| Tanggal SRS | 10 Oktober 2026 |
| Disusun oleh (sesuai SRS) | Veronika Ria; Nova Sinta Bela |
| Mata kuliah | Rekayasa Web |
| Program studi | Sistem Informasi |
| Status SRS | Disetujui |
| Versi PRD | 1.0 — turunan dari SRS |

> **Catatan penggunaan dokumen:** PRD ini merangkum dan menyusun ulang kebutuhan yang tercantum dalam SRS. ID kebutuhan `KB`, `KF`, `KNF`, `US`, `UC`, dan `BT` dipertahankan agar mudah ditelusuri kembali. Informasi yang belum tegas atau saling berbeda di dalam SRS dan rancangan antarmuka tidak diputuskan secara sepihak; hal tersebut dicatat pada bagian **Keputusan Terbuka**.

---

## 1. Ringkasan Produk

MiniBook adalah aplikasi web untuk mendukung proses penyewaan lapangan minisoccer di Minisoccer Ngabang, Kalimantan Barat. Sistem membantu pelanggan melihat ketersediaan jadwal dan harga, memilih slot bermain, mengirim pemesanan beserta bukti transfer, serta memantau status pemesanan. Admin menggunakan dashboard untuk mengelola jadwal dan pemesanan serta memverifikasi pembayaran. Owner menggunakan informasi laporan untuk memantau aktivitas dan kinerja penyewaan.

Sebelum MiniBook digunakan, informasi jadwal kosong dan pemesanan disampaikan melalui Instagram dan WhatsApp. Pelanggan harus menghubungi admin untuk memastikan ketersediaan lapangan. Proses tersebut berisiko menimbulkan keterlambatan informasi, kesalahan pencatatan, dan bentrok jadwal. MiniBook memusatkan informasi dan pencatatan pemesanan ke dalam satu aplikasi web.

### 1.1 Tujuan Produk

1. Mempermudah pelanggan melihat jadwal lapangan yang tersedia.
2. Memudahkan pelanggan melakukan pemesanan berdasarkan tanggal dan jam.
3. Membantu admin mengelola data lapangan, jadwal, pelanggan, pemesanan, dan transaksi.
4. Membantu pengelola mengurangi risiko bentrok jadwal.
5. Menyimpan data penyewaan secara terstruktur dan menyediakan laporan bagi owner.

### 1.2 Nilai yang Diharapkan

- Pelanggan dapat memeriksa ketersediaan slot dan harga tanpa harus menghubungi admin untuk setiap permintaan.
- Data pemesanan diteruskan ke dashboard pengelola untuk diverifikasi.
- Perubahan status pemesanan tercermin pada ketersediaan slot.
- Owner dan admin memperoleh ringkasan aktivitas serta laporan penyewaan.

---

## 2. Latar Belakang dan Masalah

### 2.1 Kondisi Saat Ini

Proses penyewaan lapangan masih menggunakan Instagram dan WhatsApp untuk membagikan informasi jadwal kosong dan menerima pemesanan. Pelanggan perlu menghubungi admin untuk memastikan slot yang tersedia. Admin juga perlu mengelola data pelanggan, jadwal, pemesanan, dan transaksi secara teratur.

### 2.2 Masalah yang Ingin Diselesaikan

| Masalah | Dampak | Respons MiniBook |
|---|---|---|
| Jadwal kosong diinformasikan melalui Instagram dan WhatsApp | Pelanggan perlu menghubungi admin untuk memastikan ketersediaan | Menampilkan jadwal dan status slot pada halaman Jadwal |
| Booking dilakukan untuk tanggal dan jam tertentu | Jadwal perlu diperiksa agar tidak terjadi pemesanan ganda | Menyediakan pemilihan tanggal dan slot serta pengelolaan jadwal |
| Pelanggan dapat membatalkan secara sepihak | Owner berisiko kehilangan pendapatan dari slot yang telah dipesan | Menampilkan ketentuan pembatalan dan denda 50% |
| Harga berbeda menurut waktu dan kategori pelanggan | Pelanggan perlu mengetahui harga sebelum memesan | Menampilkan tarif siang, sore, malam, serta kategori pelajar dan reguler |
| Data penyewaan perlu direkap | Owner memerlukan informasi aktivitas dan pendapatan | Menyediakan dashboard serta laporan harian dan bulanan |

### 2.3 Kebutuhan Bisnis

| ID | Kebutuhan bisnis | Indikator keberhasilan |
|---|---|---|
| KB-01 | Mempermudah pelanggan melihat jadwal lapangan yang tersedia | Pelanggan dapat melihat jadwal yang tersedia dengan mudah |
| KB-02 | Memudahkan pelanggan melakukan pemesanan lapangan | Pesanan dicatat dan disimpan oleh sistem |
| KB-03 | Membantu admin mengelola data pelanggan dan pemesanan | Admin dapat menambah, mengubah, dan menghapus data penyewaan |
| KB-04 | Membantu pengelola mengatur jadwal agar tidak terjadi bentrok | Sistem mencegah bentrok jadwal pemesanan |
| KB-05 | Mempermudah pencatatan data penyewaan secara terstruktur | Data pelanggan dan penyewaan tersimpan serta mudah ditemukan |

---

## 3. Stakeholder dan Pengguna

### 3.1 Stakeholder

| Stakeholder | Peran | Kepentingan utama | Pengaruh | Keterlibatan dalam elisitasi |
|---|---|---|---|---|
| Owner | Pemilik bisnis | Memantau aktivitas bisnis, melihat laporan penyewaan, dan meningkatkan efisiensi operasional | Tinggi | Wawancara |
| Admin | Kasir/pengelola operasional | Mengelola data lapangan, jadwal, konfirmasi pemesanan, dan transaksi pembayaran | Tinggi | Wawancara |
| Pelanggan | Penyewa lapangan | Melihat jadwal dan harga serta memesan lapangan tanpa bentrok | Tinggi | Wawancara sebagaimana tercantum pada daftar stakeholder |

### 3.2 Persona Pengguna

**Persona 1 — Owner**

| Atribut | Profil |
|---|---|
| Nama | Stepanus Ade Aswinda |
| Peran | Pemilik usaha |
| Literasi digital | Tinggi |
| Perangkat utama | Smartphone |
| Tujuan | Memantau bisnis penyewaan, melihat data pesanan, dan mengetahui aktivitas penyewaan |
| Kendala | Kesulitan memantau pemesanan bila pencatatan masih manual; membutuhkan laporan yang mudah dipahami |

**Persona 2 — Admin**

| Atribut | Profil |
|---|---|
| Nama | Riska |
| Peran | Admin |
| Literasi digital | Tinggi |
| Perangkat utama | Smartphone |
| Tujuan | Mengelola jadwal lapangan, data pelanggan, dan transaksi penyewaan |
| Kendala | Risiko kesalahan input dan bentroknya jadwal jika pengelolaan tidak teratur |

**Persona 3 — Pelanggan**

SRS menyebut pelanggan sebagai kelas pengguna dan stakeholder, tetapi tidak melengkapi nama, latar belakang, perangkat, atau persona terperinci. Karena itu, detail persona pelanggan tidak diasumsikan dalam PRD ini.

### 3.3 Peran dan Hak Akses

| Peran | Hak akses utama |
|---|---|
| Pelanggan | Melihat jadwal dan harga, melakukan pemesanan, melihat riwayat pemesanan dan rincian tiket digital |
| Admin | Login; mengelola data lapangan, jadwal, harga, pelanggan, dan pemesanan; memeriksa bukti pembayaran; mengonfirmasi atau membatalkan penyewaan |
| Owner | Login; melihat informasi penyewaan dan laporan bisnis |

Hak akses harus dibatasi berdasarkan peran (Role-Based Access Control/RBAC). Rincian halaman yang boleh diakses Owner dibandingkan Admin perlu ditetapkan pada implementasi karena mockup hanya menampilkan satu dashboard pengelola.

---

## 4. Ruang Lingkup Produk

### 4.1 Termasuk dalam Ruang Lingkup

1. Menampilkan informasi lapangan minisoccer.
2. Menampilkan ketersediaan slot berdasarkan tanggal dan jam.
3. Menampilkan harga berdasarkan kategori waktu (siang, sore, malam) dan pelanggan (pelajar, reguler).
4. Menyediakan formulir pemesanan lapangan.
5. Menerima data pemesan dan bukti transfer.
6. Menampilkan informasi ketentuan pembatalan dan denda 50%.
7. Meneruskan pemesanan ke dashboard admin untuk verifikasi.
8. Mengelola dan memperbarui status pemesanan serta ketersediaan slot.
9. Menampilkan riwayat dan status pemesanan pelanggan.
10. Menampilkan rincian tiket digital untuk pemesanan yang telah diverifikasi.
11. Menampilkan ringkasan statistik dan laporan penyewaan harian/bulanan.

### 4.2 Di Luar Ruang Lingkup

- Integrasi pembayaran otomatis melalui payment gateway pihak ketiga, seperti Midtrans atau Xendit.
- Pengembangan aplikasi mobile native Android dan iOS. Tahap awal berfokus pada aplikasi web responsif.
- Integrasi perangkat keras khusus seperti barcode scanner atau printer thermal.
- Fitur lain yang tidak dinyatakan dalam SRS.

### 4.3 Platform dan Lingkungan Operasi

| Aspek | Ketentuan dari SRS |
|---|---|
| Bentuk aplikasi | Aplikasi web responsif |
| Perangkat | Desktop, tablet, smartphone Android dan iPhone |
| Sistem operasi | Windows, macOS, Linux, Android, dan iOS |
| Browser | Google Chrome, Mozilla Firefox, Microsoft Edge, Safari |
| Bahasa pemrograman sisi server | PHP |
| Basis data | MySQL |
| Server pengembangan yang disebutkan | Apache melalui XAMPP |
| Komunikasi | HTTPS |

---

## 5. Alur Pengguna Utama

### 5.1 Alur Pelanggan — Pemesanan Lapangan

1. Pelanggan membuka halaman Jadwal.
2. Pelanggan memilih tanggal bermain.
3. Sistem menampilkan slot jam beserta status ketersediaan dan kategori harga.
4. Pelanggan memilih satu atau beberapa slot yang tersedia.
5. Pelanggan membuka halaman Pemesanan dan mengisi nama lengkap, nama tim/komunitas, nomor WhatsApp, serta kategori pelajar/mahasiswa apabila memenuhi ketentuan.
6. Sistem menampilkan ringkasan biaya sesuai slot dan kategori pelanggan.
7. Pelanggan membaca dan menyetujui ketentuan pembatalan.
8. Pelanggan melakukan transfer ke rekening yang ditampilkan dan mengunggah bukti transfer.
9. Pelanggan mengirim pesanan.
10. Sistem menyimpan data dan meneruskannya ke dashboard admin.
11. Pelanggan memantau status pemesanan melalui halaman Riwayat.
12. Setelah admin memverifikasi pesanan, sistem memperbarui status dan menampilkan rincian tiket digital.

**Kondisi alternatif:** Jika slot telah dipesan pengguna lain, sistem menolak pemesanan slot tersebut dan meminta pelanggan memilih slot lain.

**Kondisi pengecualian:** Jika koneksi jaringan gagal saat formulir dikirim, sistem menampilkan pesan galat dan meminta pelanggan mengirim ulang data.

### 5.2 Alur Admin — Verifikasi dan Operasional

1. Admin login.
2. Admin membuka Dashboard Admin.
3. Sistem menampilkan ringkasan jumlah pesanan yang menunggu verifikasi dan informasi operasional.
4. Admin membuka pesanan masuk dan melihat data pemesan, jadwal, jumlah pembayaran, serta bukti transfer.
5. Admin memeriksa bukti transfer.
6. Admin menyetujui atau menolak pesanan sesuai hasil pemeriksaan.
7. Sistem memperbarui status pemesanan dan ketersediaan slot.
8. Admin dapat mengelola jadwal dan data penyewaan.

Mockup juga menampilkan kontrol untuk mengubah slot menjadi *Maintenance* atau membukanya kembali. Status dan aturan operasional fitur ini perlu dikonfirmasi karena tidak dirinci dalam model data SRS.

### 5.3 Alur Owner — Pemantauan

1. Owner login.
2. Owner membuka informasi dashboard/laporan.
3. Owner melihat ringkasan total pendapatan, jumlah booking, antrean verifikasi, dan informasi okupansi.
4. Owner memilih periode laporan harian atau bulanan.
5. Sistem menampilkan ringkasan dan rincian penyewaan sesuai periode.

---

## 6. Kebutuhan Fungsional

Seluruh kebutuhan fungsional berikut memiliki prioritas **Must Have (M)** dan status **Disetujui** pada SRS.

| ID | Modul | Kebutuhan produk | Prioritas | Status sumber |
|---|---|---|---|---|
| KF-01 | Autentikasi & hak akses | Sistem harus menyediakan login untuk Admin dan Owner agar pengelolaan data dan akses laporan sesuai hak akses peran. | M | Disetujui |
| KF-02 | Informasi lapangan, harga, jadwal, dan pemesanan | Sistem harus menampilkan tarif siang, sore, malam, kategori pelanggan pelajar/reguler, serta slot jadwal. Sistem harus menyediakan formulir pemesanan terintegrasi untuk memilih jadwal, melakukan transfer pembayaran 50% sebagaimana tertulis pada KF-02 SRS, dan mengunggah bukti transfer. Ketentuan pembayaran 50% ini harus dikonfirmasi karena mockup menampilkan total pembayaran. | M | Disetujui |
| KF-03 | Verifikasi & notifikasi otomatis | Sistem harus meneruskan data pemesanan ke Dashboard Admin secara otomatis untuk diverifikasi tanpa konfirmasi manual melalui WhatsApp. | M | Disetujui |
| KF-04 | Aturan pembatalan & denda | Sistem harus menampilkan ketentuan pembatalan booking dan informasi denda sebesar 50% dari harga sewa kepada pelanggan. | M | Disetujui |
| KF-05 | Pengelolaan data penyewaan | Admin harus dapat menambah, mengubah, mengonfirmasi, dan membatalkan data penyewaan lapangan. | M | Disetujui |
| KF-06 | Riwayat pemesanan pelanggan | Pelanggan dapat melihat riwayat, status pemesanan (Pending/Verified sebagaimana istilah SRS), dan rincian tiket digital pada sistem web. | M | Disetujui |
| KF-07 | Laporan & widget statistik | Sistem harus menyajikan laporan penyewaan dan widget statistik berupa total pendapatan, booking harian, serta antrean verifikasi pada Dashboard Owner dan Admin. | M | Disetujui |

### 6.1 Kriteria Penerimaan per User Story

#### US-01 — Melihat Jadwal dan Informasi Harga Lapangan

**Aktor:** Pelanggan  
**Kebutuhan terkait:** KF-02  
**Prioritas:** Must Have

- Ketika pelanggan memilih tanggal di halaman utama, sistem menampilkan slot jam yang tersedia beserta keterangan harga sesuai waktu sewa dan kategori pelanggan.
- Jika slot sudah dipesan pengguna lain, sistem menampilkan status slot sebagai **Terisi / Booked**.

#### US-02 — Pemesanan Lapangan dan Pengiriman Otomatis

**Aktor:** Pelanggan  
**Kebutuhan terkait:** KF-02, KF-03, KF-04  
**Prioritas:** Must Have

- Jika pelanggan telah memilih slot kosong dan mengisi data diri, saat tombol konfirmasi pemesanan ditekan, sistem menyimpan data booking dan meneruskannya ke Dashboard Admin.
- Sistem menampilkan ketentuan pembatalan sepihak dan denda 50% dari harga sewa sebelum pelanggan mengonfirmasi pesanan.

#### US-03 — Verifikasi Pesanan dan Pengelolaan Jadwal oleh Admin

**Aktor:** Admin  
**Kebutuhan terkait:** KF-01, KF-03, KF-05, KF-07  
**Prioritas:** Must Have

- Jika ada pesanan baru, dashboard menampilkan jumlah pesanan yang menunggu verifikasi.
- Ketika admin memverifikasi pembayaran/pesanan, status berubah menjadi disetujui dan slot jadwal terkunci secara otomatis.

#### US-05 — Riwayat Pemesanan dan Tiket Digital Pelanggan

**Aktor:** Pelanggan  
**Kebutuhan terkait:** KF-06  
**Prioritas:** Must Have

- Halaman Riwayat menampilkan daftar transaksi dan status pemesanan.
- Ketika pelanggan membuka rincian transaksi yang telah terverifikasi, sistem menampilkan rincian tiket digital pemesanan lapangan.

#### US-06 — Pemantauan Laporan dan Ringkasan Statistik

**Aktor:** Owner dan Admin  
**Kebutuhan terkait:** KF-07  
**Prioritas:** Must Have

- Dashboard menampilkan data transaksi terbaru dan widget total pendapatan, booking harian, serta antrean verifikasi.
- Ketika Owner memilih periode harian atau bulanan, sistem menampilkan rincian laporan sesuai periode yang dipilih.

> **Catatan sumber:** SRS memuat entri `US-04` yang belum lengkap dan mengulang sebagian isi `US-03`. Entri tersebut tidak diperlakukan sebagai user story tersendiri dalam PRD ini sampai definisinya dikonfirmasi.

---

## 7. Use Case Utama

### UC-01 — Pemesanan dan Verifikasi Lapangan Minisoccer

| Atribut | Deskripsi |
|---|---|
| Aktor | Pelanggan, Admin |
| Tujuan | Pelanggan memesan slot lapangan secara online dan Admin memverifikasi pesanan melalui dashboard |
| Prakondisi | Pelanggan telah membuka web MiniBook dan melihat jadwal kosong |
| Pemicu | Pelanggan memilih slot tanggal dan jam yang diinginkan lalu memulai pemesanan |
| Pascakondisi | Data pemesanan tersimpan; dashboard memperoleh data pesanan; status slot diperbarui sesuai hasil proses |

**Alur utama**

1. Pelanggan memilih tanggal dan slot jam sewa.
2. Sistem menampilkan tarif sesuai kategori waktu dan kategori pelanggan serta informasi denda pembatalan 50%.
3. Pelanggan mengisi data pemesan.
4. Pelanggan melakukan transfer pembayaran 50% sebagaimana tertulis pada KF-02 SRS, lalu mengunggah bukti transfer. Besaran ini perlu dikonfirmasi karena mockup Pemesanan menampilkan label total pembayaran.
5. Pelanggan mengirim formulir pemesanan.
6. Sistem menyimpan transaksi dan meneruskan data pesanan ke Dashboard Admin.
7. Admin memeriksa data pesanan dan bukti pembayaran.
8. Admin memverifikasi status pesanan.
9. Sistem memperbarui status pemesanan dan status ketersediaan slot.

**Alur alternatif**

- Jika slot telah dipesan oleh pengguna lain, sistem menampilkan pesan penolakan dan meminta pelanggan memilih slot lain.

**Alur pengecualian**

- Jika jaringan gagal saat formulir dikirim, sistem menampilkan pesan galat dan meminta pelanggan mengirim ulang data.

**Aturan bisnis**

- Pembatalan sepihak secara mendadak oleh pelanggan dikenakan denda/potongan sebesar 50% dari total harga sewa.

**Kebutuhan terkait:** KF-01 sampai KF-07 dan KNF-02.

---

## 8. Aturan Bisnis

| ID | Aturan | Penjelasan |
|---|---|---|
| BR-01 | Tarif berbasis waktu | Harga sewa dibedakan menurut waktu siang, sore, dan malam. |
| BR-02 | Tarif berbasis kategori pelanggan | Tersedia kategori harga reguler dan pelajar. |
| BR-03 | Ketersediaan slot | Slot yang telah dipesan tidak boleh ditawarkan sebagai slot tersedia untuk pemesanan lain. |
| BR-04 | Pemeriksaan pesanan | Pesanan diteruskan ke Dashboard Admin untuk diverifikasi. |
| BR-05 | Penguncian slot | Setelah pesanan diverifikasi/disetujui, slot jadwal dikunci secara otomatis sesuai acceptance criteria SRS. |
| BR-06 | Pembatalan | Pembatalan sepihak oleh pelanggan dikenakan denda 50% dari harga sewa/total harga sewa sebagaimana dinyatakan dalam SRS. Dasar nominal yang digunakan perlu dikonfirmasi. |
| BR-07 | Pembayaran manual | Pembayaran dilakukan melalui transfer manual dan bukti transfer diunggah ke sistem; payment gateway tidak termasuk ruang lingkup tahap awal. |

---

## 9. Model Data Konseptual

Model data konseptual pada SRS memuat lima entitas utama.

| Entitas | Atribut utama | Tanggung jawab |
|---|---|---|
| Pengguna | `id_pengguna`, `nama`, `email`, `password`, `peran` (Pelanggan/Admin/Owner) | Menyimpan data pengguna dan peran untuk RBAC |
| Lapangan | `id_lapangan`, `nama_lapangan`, `deskripsi_lapangan`, `status_lapangan` | Menyimpan informasi lapangan minisoccer |
| Harga/Tarif | `id_tarif`, `kategori_waktu`, `kategori_pelanggan`, `harga` | Menyimpan tarif berdasarkan waktu dan kategori pelanggan |
| Pemesanan/Booking | `id_booking`, `id_user`, `id_lapangan`, `tanggal_sewa`, `jam_mulai`, `jam_selesai`, `total_harga`, `status_booking` | Menyimpan transaksi pemesanan |
| Pembayaran/Verifikasi | `id_pembayaran`, `id_booking`, `metode_pembayaran`, `bukti_bayar`, `status_verifikasi` | Menyimpan data pembayaran dan hasil verifikasi |

### 9.1 Relasi Konseptual

- Pengguna melakukan pemesanan.
- Pemesanan terkait dengan lapangan yang disewa.
- Pemesanan menggunakan tarif sesuai kategori waktu dan kategori pelanggan.
- Pembayaran terkait dengan satu pemesanan untuk menyimpan bukti dan status verifikasi.

Kardinalitas rinci dan atribut tambahan belum dijelaskan di SRS; perlu ditetapkan saat penyusunan ERD dan desain basis data.

---

## 10. Kebutuhan Antarmuka Eksternal

| ID | Jenis | Persyaratan |
|---|---|---|
| KA-01 | Antarmuka pengguna | Tata letak web responsif untuk mobile dan desktop. Navigasi utama mencakup Jadwal, Pemesanan, Riwayat, dan Dashboard Admin. Jadwal menampilkan tanggal, slot per jam, status tersedia/terisi, kategori harga, dan penanda harga pelajar. Form pemesanan menampilkan data pemesan, slot terpilih, rincian biaya, aturan pembatalan, serta tombol konfirmasi. Dashboard menampilkan kontrol jadwal, verifikasi transaksi, statistik, dan laporan harian/bulanan. |
| KA-02 | Antarmuka perangkat lunak | PHP, MySQL, Apache/XAMPP pada lingkungan pengembangan, dan dukungan browser Chrome, Firefox, Edge, serta Safari. |
| KA-03 | Antarmuka perangkat keras | Tidak memerlukan perangkat keras khusus. Pencatatan dan verifikasi dilakukan melalui aplikasi web. |
| KA-04 | Antarmuka komunikasi | Komunikasi browser dan server menggunakan HTTPS. Data booking memperbarui Dashboard Admin secara otomatis/real-time. Setelah transaksi diverifikasi, sistem mengirimkan konfirmasi berupa kode booking/tiket digital ke riwayat pelanggan dan email pelanggan. |

**Catatan:** Pengiriman email disebutkan pada KA-04 SRS, tetapi tidak terlihat sebagai alur atau komponen pada mockup Design.pdf. Detail layanan email dan kondisi pengirimannya perlu dipastikan saat implementasi.

---

## 11. Kebutuhan Non-Fungsional

| ID | Kategori | Kebutuhan | Metrik/cara uji | Prioritas |
|---|---|---|---|---|
| KNF-01 | Kinerja | Halaman web harus dimuat dalam waktu ≤ 2 detik pada koneksi internet standar 4G/Wi-Fi. | Google Lighthouse | M |
| KNF-02 | Keamanan | Password diamankan dengan Bcrypt, komunikasi menggunakan HTTPS, dan akses dibatasi sesuai peran (RBAC). | SRS belum menetapkan metrik pengujian rinci | M |
| KNF-03 | Kegunaan | Pelanggan dapat menyelesaikan pemesanan maksimal dalam empat kali klik: memilih lapangan; memilih tanggal dan jam; menekan Lanjut ke Pembayaran/Pesan Sekarang; lalu konfirmasi pemesanan/pembayaran. | Usability testing dengan 5 pengguna | S |
| KNF-04 | Aksesibilitas | Teks dan warna memiliki kontras yang jelas dan mudah dibaca. | Audit aksesibilitas browser | S |
| KNF-05 | Kompatibilitas | Aplikasi berfungsi dan tampil responsif pada browser Chrome, Firefox, Safari, dan Edge serta perangkat desktop dan mobile. | Cross-browser testing | S |
| KNF-06 | Ketersediaan | Sistem harus memiliki keandalan/availability yang memadai. SRS belum menetapkan target uptime numerik. | Uptime monitoring | M |
| KNF-07 | Skalabilitas | Sistem tidak mengalami penurunan kinerja yang mengganggu saat digunakan 50 pengguna secara bersamaan. | Load testing menggunakan Apache JMeter atau alat setara | S |
| KNF-08 | Keterpeliharaan | Kode disimpan secara terstruktur di GitHub dan dilengkapi catatan database serta modul. | Code review | S |
| KNF-09 | Privasi & kepatuhan | Sistem menyediakan kebijakan privasi dan persetujuan penggunaan data pribadi dasar saat pendaftaran/pemesanan. | Checklist keberadaan kebijakan dan persetujuan | S |
| KNF-10 | SEO | Setiap halaman utama memiliki judul dan meta description yang unik serta ramah mesin pencari. | SEO checker atau Google Lighthouse | C |

### 11.1 Prioritas MoSCoW

| Prioritas | Kebutuhan |
|---|---|
| Must Have | KF-01 sampai KF-07; KNF-01, KNF-02, KNF-06 |
| Should Have | KNF-03, KNF-04, KNF-05, KNF-07, KNF-08, KNF-09 |
| Could Have | KNF-10 |
| Won't Have pada tahap awal | Payment gateway pihak ketiga dan aplikasi mobile native Android/iOS |

---

## 12. Batasan dan Ketergantungan

| ID | Jenis | Batasan |
|---|---|---|
| BT-01 | Teknologi/ruang lingkup | Fokus pada informasi jadwal, harga, dan pemesanan. Pembayaran manual dan tidak terintegrasi dengan payment gateway online. Aplikasi harus dapat digunakan pada Android dan iOS melalui web responsif. |
| BT-02 | Waktu | Pengembangan dibatasi oleh waktu pengerjaan tugas kuliah. |
| BT-03 | Regulasi/aturan bisnis | Sistem mengikuti ketentuan penyewaan yang ditetapkan Owner, termasuk aturan pembatalan dan denda 50% dari harga sewa. |

Ketergantungan utama adalah ketersediaan informasi tarif, kebijakan pembayaran dan pembatalan, rekening tujuan transfer, serta keputusan Owner mengenai verifikasi dan status booking.

---

## 13. Risiko dan Mitigasi

| Risiko | Dampak | Kemungkinan menurut SRS | Mitigasi |
|---|---|---|---|
| Perubahan kebutuhan saat pengembangan | Tinggi | Sedang | Gunakan prosedur Change Request, analisis dampak, dan persetujuan Owner/ketua tim sebelum perubahan diterapkan |
| Dua pelanggan memesan slot yang sama secara bersamaan | Tinggi | Rendah | Terapkan validasi ketersediaan dan penguncian slot secara konsisten pada proses penyimpanan/persetujuan pemesanan |

---

## 14. Kriteria Keberhasilan Produk

Keberhasilan MiniBook dievaluasi berdasarkan pencapaian kebutuhan bisnis berikut:

| Kriteria | Bukti keberhasilan |
|---|---|
| Jadwal dapat dilihat pelanggan | Halaman Jadwal menampilkan tanggal, slot, harga, dan status ketersediaan |
| Booking tercatat | Pesanan pelanggan tersimpan dan muncul di dashboard admin |
| Pengelolaan pesanan berjalan | Admin dapat mengelola data penyewaan serta memverifikasi pesanan |
| Bentrok slot dicegah | Slot yang sudah dipesan/terverifikasi tidak dapat dipesan ulang |
| Data penyewaan terstruktur | Riwayat dan data penyewaan dapat ditampilkan serta dicari |
| Laporan tersedia | Dashboard menyajikan statistik dan laporan harian/bulanan |
| Kualitas teknis terpenuhi | Pengujian terhadap KNF dilakukan sesuai metrik yang ditetapkan; KNF yang belum memiliki target perlu dilengkapi sebelum pengujian final |

---

## 15. Traceability Kebutuhan ke Modul

| ID | Modul/halaman utama | Artefak rancangan yang terkait | Pengujian utama |
|---|---|---|---|
| KB-01 / KF-02 | Jadwal | Jadwal & Ketersediaan (Design.pdf hlm. 1) | Pilih tanggal; cek status dan harga setiap slot |
| KB-02 / KF-02 | Pemesanan | Form Pemesanan (hlm. 2) | Submit booking; pastikan data tersimpan |
| KF-03 | Dashboard Admin | Verifikasi transaksi (hlm. 6–7) | Booking baru muncul di antrian admin |
| KF-04 | Pemesanan dan Riwayat | Persetujuan aturan pembatalan (hlm. 2–5) | Pastikan aturan dan denda terlihat |
| KF-05 | Dashboard Admin | Kontrol status slot dan aksi verifikasi (hlm. 6–7) | Tambah/ubah/konfirmasi/batalkan data |
| KF-06 | Riwayat | Daftar riwayat dan filter status (hlm. 3–5) | Tampilkan riwayat, status, dan tiket digital |
| KF-07 | Dashboard Admin/Owner | Laporan harian dan bulanan (hlm. 6–7) | Periksa ringkasan dan filter periode |
| KNF-01 | Semua halaman | Semua mockup | Ukur waktu muat dengan Lighthouse |
| KNF-02 | Login dan seluruh modul privat | Tidak ada layar login pada mockup | Uji autentikasi, HTTPS, hashing, dan RBAC |
| KNF-03–KNF-10 | Seluruh aplikasi | Seluruh mockup | Pengujian sesuai metrik masing-masing KNF |

---

## 16. Keputusan Terbuka dan Ambiguitas

Hal-hal berikut perlu dikonfirmasi oleh Owner/tim sebelum implementasi final. PRD ini sengaja tidak memilih salah satu versi ketika sumber berbeda.

| No. | Topik | Isi sumber yang berbeda/tidak lengkap | Keputusan yang diperlukan |
|---|---|---|---|
| 1 | Nama produk | Sampul SRS menyebut `MiniBook`, tabel ruang lingkup menulis `Mini Book`. | Gunakan satu ejaan resmi; PRD memakai `MiniBook` mengikuti identitas dokumen dan mockup. |
| 2 | Nominal pembayaran | KF-02 menyebut transfer pembayaran 50%; mockup menampilkan “total pembayaran” dan transfer sesuai total pembayaran. | Pastikan apakah pelanggan membayar DP 50% atau membayar 100% saat booking. Pisahkan aturan DP dari denda pembatalan. |
| 3 | Denda pembatalan | SRS menyebut 50% dari harga sewa/total harga sewa; mockup menyebut 50% dari total bayar. | Tetapkan dasar perhitungan denda dan apakah berlaku untuk semua status booking. |
| 4 | Rentang tarif | SRS hanya menyebut siang, sore, malam. Mockup menampilkan siang 08.00–14.00, sore 15.00–17.00, malam 18.00–22.00; dashboard menampilkan malam 18.00–23.00. | Tetapkan batas jam setiap kategori dan konsistensinya dengan slot terakhir. |
| 5 | Daftar slot | Mockup menampilkan 14 slot, tetapi rentang 12.00–13.00 tidak tampak. | Konfirmasi jam operasional dan apakah slot yang hilang memang tidak tersedia atau hanya belum ditampilkan. |
| 6 | Harga pelajar | Mockup memperlihatkan diskon 20% dan contoh nominal Rp80.000/Rp120.000/Rp160.000, sedangkan SRS hanya menyebut harga pelajar lebih murah. | Konfirmasi apakah nominal dan diskon pada mockup adalah tarif final. |
| 7 | Status booking | SRS menggunakan Pending/Verified dan menyebut disetujui; mockup menggunakan Menunggu Verifikasi, Disetujui/Lunas, Batal, serta tombol Tolak. | Tetapkan daftar status, transisi status, dan padanan nilai database. |
| 8 | Akun pelanggan | KF-01 secara eksplisit menyebut login Admin dan Owner; model data memasukkan Pelanggan sebagai peran dan mockup menampilkan menu akun Pelanggan. | Putuskan apakah pelanggan harus mendaftar/login atau dapat memesan tanpa akun. |
| 9 | Verifikasi pembayaran | SRS mengharuskan verifikasi Admin; mockup menyediakan Setujui dan Tolak. | Tetapkan alasan penolakan, apakah pelanggan dapat mengunggah ulang bukti, dan status akhir transaksi yang ditolak. |
| 10 | Slot Maintenance | Mockup memperlihatkan kontrol Maintenance/Membuka slot, tetapi atribut status pada SRS hanya status lapangan dan tidak merinci status slot. | Tetapkan status slot, siapa yang dapat mengubahnya, serta apakah perubahan memerlukan alasan. |
| 11 | Email konfirmasi | KA-04 mensyaratkan email setelah transaksi diverifikasi, tetapi mockup tidak memperlihatkan input email atau alur email. | Tentukan sumber alamat email pelanggan dan apakah pengiriman email wajib pada rilis ini. |
| 12 | Tiket digital | KF-06 mensyaratkan rincian tiket digital, tetapi layar rincian tiket tidak tampak di Design.pdf. | Definisikan field tiket dan halaman/modal detail yang akan dibuat. |
| 13 | Owner vs Admin | SRS memberikan hak akses berbeda, sedangkan Design.pdf menampilkan satu Dashboard Admin/pengelola. | Tetapkan apakah Owner menggunakan dashboard yang sama dengan menu baca-saja atau dashboard terpisah. |
| 14 | KNF-06 | Target uptime tidak ditentukan. | Tetapkan persentase uptime dan periode pengukuran yang dapat diuji. |
| 15 | Riwayat dan detail persona | Persona pelanggan belum diisi; US-04 tidak lengkap dan mengulang US-03. | Lengkapi persona pelanggan dan klarifikasi apakah US-04 perlu dihapus atau diganti. |
| 16 | Data contoh pada mockup | Footer menampilkan © 2025 dan data tanggal Oktober 2025, sementara SRS bertanggal 2026. | Gunakan data dinamis dan tetapkan tahun hak cipta/isi contoh untuk rilis. |

---

## 17. Manajemen Perubahan

Setiap perubahan kebutuhan harus mengikuti urutan berikut:

1. Pengaju mengisi Change Request.
2. Tim menganalisis dampak perubahan terhadap kebutuhan, modul, jadwal, dan pekerjaan yang telah selesai.
3. Owner dan ketua tim memutuskan untuk menerima, menolak, atau menunda perubahan.
4. Dokumen PRD/SRS dan artefak terkait diperbarui; versi serta riwayat perubahan dicatat.
5. Seluruh anggota tim diberi tahu mengenai keputusan.

### 17.1 Formulir Change Request

| Kolom | Isi |
|---|---|
| Nomor perubahan |  |
| Tanggal dan pengaju |  |
| ID kebutuhan terdampak |  |
| Deskripsi perubahan |  |
| Alasan |  |
| Analisis dampak |  |
| Keputusan | Terima / Tolak / Tunda |
| Pemberi keputusan dan tanggal |  |

### 17.2 Riwayat Perubahan PRD

| Versi | Tanggal | Deskripsi |
|---|---|---|
| 1.0 | 23 November 2026 | Penyusunan PRD berdasarkan SRS MiniBook versi 1.0 |

---

## 18. Referensi Sumber

1. **SRS.docx** — *Software Requirements Specification (SRS) Aplikasi Web MiniBook*, versi 1.0, tanggal 10 Oktober 2026. Menjadi sumber kebutuhan bisnis, stakeholder, batasan, kebutuhan fungsional/non-fungsional, use case, model data, risiko, dan aturan pengelolaan kebutuhan.
2. **Design.pdf** — *Rancangan Antarmuka MiniBook*, 7 halaman. Digunakan sebagai referensi layar Jadwal (hlm. 1), Pemesanan (hlm. 2), Riwayat dengan beberapa filter (hlm. 3–5), Dashboard harian (hlm. 6), dan Dashboard bulanan (hlm. 7).

