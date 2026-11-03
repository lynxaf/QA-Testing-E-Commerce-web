# SOFTWARE TEST PLAN
**Proyek:** Website E-Commerce Penjualan Produk Elektronik  
**Dokumen Versi:** 2.1  
**Tanggal:** November 2026  
**Penulis:** Quality Assurance Team  

---

## 1. Pendahuluan (Introduction)
Dokumen Test Plan ini dirancang untuk memvalidasi fungsionalitas, akurasi data inventaris, sistem perhitungan logistik, keandalan transaksi pada storefront pelanggan, serta manajemen operasional pada Halaman Admin (Admin Dashboard) e-commerce produk elektronik.

## 2. Ruang Lingkup Pengujian (Scope of Testing)

### Yang Diuji (In-Scope):

#### A. Halaman Pelanggan (Storefront & Customer Side):
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

## 3. Strategi Pengujian (Test Strategy)
1. **Functional & UI Testing:** Memastikan informasi spesifikasi teknis produk elektronik tampil akurat serta seluruh tombol aksi di storefront dan admin dashboard berfungsi normal.
2. **Inventory & Concurrency Testing:** Menguji sinkronisasi stok antara perubahan di Admin Dashboard dengan ketersediaan barang di storefront untuk mencegah overselling.
3. **Integration Testing:** Memastikan integrasi dengan payment gateway, API ongkos kirim, dan sistem pembaruan resi kurir berjalan valid.

## 4. Kriteria Kelayakan (Entry & Exit Criteria)

### Kriteria Masuk (Entry Criteria):
* Katalog produk elektronik beserta varian dan stok awal telah dimasukkan ke database.
* Akun kredensial Admin (Super Admin & Staf Role) dan lingkungan uji (staging environment) siap diakses.
* API kurir logistik dan payment gateway (mode sandbox) sudah terhubung.

### Kriteria Keluar (Exit Criteria):
* Alur dari pemilihan varian produk oleh pelanggan hingga pemrosesan pesanan di Halaman Admin berhasil (End-to-End Test Passed 100%).
* Sinkronisasi data antara Admin Dashboard dan Storefront berjalan akurat tanpa penundaan (delay) data stok.
* Tidak ada bug kritis pada sistem pengurangan stok otomatis, manajemen pesanan, dan status transaksi.

## 5. Sumber Daya & Perangkat Uji (Resources & Environment)
* **Perangkat:** Laptop (Windows/Mac) & Smartphone (Responsive Mobile View).
* **Browser:** Google Chrome, Mozilla Firefox, Microsoft Edge.
* **Tools Pendukung:** Postman (API Testing), GitHub Issues (Bug Tracking), Browser DevTools.
