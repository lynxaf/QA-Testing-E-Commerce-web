# SOFTWARE TEST PLAN
**Proyek:** Website E-Commerce Penjualan Produk Elektronik (Belanja)  
**Tanggal:** November 2026  
**Penulis:** Quality Assurance Team  

---

## 1. Pendahuluan (Introduction)
Dokumen Test Plan ini dirancang untuk memvalidasi fungsionalitas, akurasi data inventaris, sistem perhitungan logistik, keandalan transaksi pada storefront pelanggan, serta manajemen operasional pada Halaman Admin (Admin Dashboard) e-commerce produk elektronik.

## 2. Tujuan
Tujuan pengujian ini adalah mendefinisikan pendekatan pengujian untuk website E-Commerce penjualan produk elektronik. Pengujian berfokus pada fungsi utama aplikasi agar aplikasi dapat beroperasi seperti yang diharapkan.Pengujian memastikan bahwa pengguna dapat bertransaksi tanpa mengalami kesalahan kegunaan sistem.  

## 3. Gambaran Umum Aplikasi
Website Belanja ini adalah website penjualan produk elektronik yang dirancang untuk penjualan berbagai produk elektronik dan brand yang memberikan kualitas unggul. Aplikasi ini menggunakan 2 user, yakni yang pertama adalah user superadmin dan yang kedua adalah user pelanggan.

### Fungsi utama aplikasi meliputi sebagai berikut :
#### Sisi Pengguna / Pelanggan (Customer Journey)
a. Autentikasi Pengguna (Sign Up & Sign In)
- Pendaftaran Akun (Sign Up): Memungkinkan pengguna baru membuat akun dengan memasukkan data kredensial.
- Masuk (Sign In): Memungkinkan pengguna yang sudah terdaftar untuk masuk ke dalam sistem menggunakan akun mereka.
- Navigasi & Pencarian Katalog Produk (Shop & Categories)
- Katalog Beranda: Menampilkan produk populer, rekomendasi produk pilihan (Most Picked Quality Products), dan rilis terbaru (New Releases).
- Filter Kategori: Memungkinkan pengguna menyaring produk berdasarkan kategori spesifik seperti Phones, Headsets, Desktops, Games, Essentials, Lights, Watches, dan Awards.
- Detail Produk: Melihat informasi lengkap barang (seperti nama produk, harga, deskripsi garansi, dan spesifikasi pendukung).

b. Manajemen Keranjang Belanja & Transaksi (Add to Cart)
- Tambah ke Keranjang: Memasukkan produk yang dipilih (seperti Mac PC, AirPods, atau Samsung A15) ke dalam keranjang belanja.
- Proses Pembelian (Checkout): Melanjutkan produk di keranjang menuju tahap pembayaran hingga transaksi selesai.

c. Fitur Tambahan Pengguna
- Testimoni & Ulasan (Testimonials): Melihat ulasan dan penilaian dari pembeli lain (Jemmie Pemilia, Angga Risky, dll.) untuk referensi produk.
- Reward & Diskon (Rewards): Menampilkan informasi promo, bonus, atau potongan harga (seperti diskon 25% atau bonus paket tertentu).

#### Sisi Pengelola / Admin (Admin Portal)
a. Autentikasi Admin: Masuk ke dashboard khusus pengelola dengan hak akses (privileges) tata ruang sistem.

b. Manajemen Produk (CRUD Produk):
- Menambah produk baru ke dalam katalog (lengkap dengan nama, kategori, harga, dan gambar/thumbnail).
- Mengubah atau memperbarui informasi produk dan stok.
- Menghapus produk yang sudah tidak dijual.
- Manajemen Kategori & Brand: Mengatur daftar kategori produk (Phones, Desktops, dll.) serta mengelola daftar brand mitra yang muncul di halaman utama.
- Manajemen Pesanan & Transaksi: Memantau status pesanan yang masuk dari pelanggan, mulai dari status pembayaran hingga proses pengiriman selesai.

  
## 4. Ruang Lingkup Pengujian (Scope of Testing)

### Yang Diuji (In-Scope):

#### A. Halaman Pelanggan (Storefront & Customer Side):

* **Halaman Sign Up (Pendaftaran Pengguna):**
  * Pengujian pendaftaran menggunakan data dummy dengan Positive Case
  * Pengujian pendaftaran menggunakan data dummy dengan Negative Case
* **Halaman Sign In (Pengguna Login):**
  * Pengujian pendaftaran menggunakan data dummy dengan Positive Case
  * Pengujian pendaftaran menggunakan data dummy dengan Negative Case
* **Katalog & Varian Produk Elektronik:** 
  * Pengujian filter spesifikasi (merek, rentang harga, kapasitas RAM/penyimpanan, jenis garansi).
  * Pemilihan varian produk (seperti warna dan spesifikasi) yang memengaruhi perubahan harga dan ketersediaan stok secara dinamis.
* **Manajemen Stok & Keranjang Belanja (Inventory & Cart):** 
  * Validasi pengurangan stok secara otomatis saat produk dibeli.
  * Sistem pembatasan pembelian jika stok habis (Out of Stock).
* **Alur Checkout, Logistik & Ongkir:** 
  * Integrasi API kurir pihak ketiga untuk perhitungan ongkos kirim berdasarkan berat dan dimensi produk elektronik.
  * Pemilihan metode pengiriman (reguler, same-day, asuransi pengiriman).
* **Payment Gateway & Proteksi Transaksi:** 
  * Pengujian berbagai metode pembayaran (Virtual Account, E-Wallet, PayLater).
  * Validasi penambahan biaya asuransi pengiriman atau biaya layanan.

#### B. Halaman Admin (Admin Dashboard & Operational Side):
* **Manajemen Produk & Varian (Product Management):**
  * Fitur CRUD (Create, Read, Update, Delete) produk elektronik, penetapan harga varian, brand, kategori, dan unggah foto produk.
* **Manajemen Pesanan & Transaksi (Order Management):**
  * Pembaruan status pesanan (Menunggu Pembayaran ➔ Diproses ➔ Dikirim ➔ Selesai / Dibatalkan).
  * Penginputan nomor resi pengiriman logistik dan integrasi status pelacakan resi.
* **Manajemen Stok & Gudang (Inventory Control):**
  * Penyesuaian stok manual (Stock Opname) dan notifikasi peringatan stok menipis (*Low Stock Alert*).
* **Hak Akses & Keamanan Admin (Role-Based Access Control):**
  * Pembatasan hak akses sesuai peran (misal: Super Admin, Staf Gudang, Finance, Customer Service).
* **Laporan Transaksi & Analitik (Sales & Reports):**
  * Validasi akurasi laporan penjualan harian/bulanan dan ekspor data transaksi.

### Yang Tidak Diuji (Out-of-Scope):
* Pengujian fisik perangkat keras secara langsung (pengujian murni berfokus pada sistem software e-commerce).
* Pengujian beban berat (Stress Testing) skala jutaan pengguna secara bersamaan.

## 5. Strategi Pengujian (Test Strategy)
1. **Functional & UI Testing:** Memastikan informasi spesifikasi teknis produk elektronik tampil akurat serta seluruh tombol aksi di storefront dan admin dashboard berfungsi normal.
2. **Inventory & Concurrency Testing:** Menguji sinkronisasi stok antara perubahan di Admin Dashboard dengan ketersediaan barang di storefront untuk mencegah overselling.
3. **Integration Testing:** Memastikan integrasi dengan payment gateway, API ongkos kirim, dan sistem pembaruan resi kurir berjalan valid.

## 6. Kriteria Kelayakan (Entry & Exit Criteria)

### Kriteria Masuk (Entry Criteria):
* Katalog produk elektronik beserta varian dan stok awal telah dimasukkan ke database.
* Akun kredensial Admin (Super Admin & Staf Role) dan lingkungan uji (staging environment) siap diakses.
* API kurir logistik dan payment gateway (mode sandbox) sudah terhubung.

### Kriteria Keluar (Exit Criteria):
* Alur dari pemilihan varian produk oleh pelanggan hingga pemrosesan pesanan di Halaman Admin berhasil (End-to-End Test Passed 100%).
* Sinkronisasi data antara Admin Dashboard dan Storefront berjalan akurat tanpa penundaan (delay) data stok.
* Tidak ada bug kritis pada sistem pengurangan stok otomatis, manajemen pesanan, dan status transaksi.

## 7. Sumber Daya & Perangkat Uji (Resources & Environment)
* **Perangkat:** Laptop (Windows/Mac) & Smartphone (Responsive Mobile View).
* **Browser:** Google Chrome, Mozilla Firefox, Microsoft Edge.
* **Tools Pendukung:** Postman (API Testing), GitHub Issues (Bug Tracking), Browser DevTools.
