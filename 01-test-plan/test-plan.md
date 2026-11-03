# SOFTWARE TEST PLAN
**Proyek:** Website E-Commerce Penjualan Produk Elektronik  
**Dokumen Versi:** 2.0  
**Tanggal:** November 2026  
**Penulis:** Quality Assurance Team  

---

## 1. Pendahuluan (Introduction)
Dokumen Test Plan ini dirancang untuk memvalidasi fungsionalitas, akurasi data inventaris, sistem perhitungan logistik, dan keandalan transaksi pada platform e-commerce penjualan produk elektronik (ponsel, headset, dan desktop dsb).

## 2. Ruang Lingkup Pengujian (Scope of Testing)

### Yang Diuji (In-Scope):
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
* **Manajemen Garansi & Riwayat Pesanan:** 
  * Pencatatan informasi garansi pada halaman pesanan dan status pelacakan pengiriman barang.

### Yang Tidak Diuji (Out-of-Scope):
* Pengujian fisik perangkat keras secara langsung (pengujian murni berfokus pada sistem software e-commerce).
* Pengujian beban berat (Stress Testing) skala jutaan pengguna secara bersamaan.

## 3. Strategi Pengujian (Test Strategy)
1. **Functional & UI Testing:** Memastikan informasi spesifikasi teknis produk elektronik tampil akurat dan tombol navigasi berfungsi normal.
2. **Inventory & Concurrency Testing:** Menguji sistem stok untuk mencegah overselling (pembelian melebihi sisa stok fisik).
3. **Integration Testing:** Memastikan integrasi dengan payment gateway dan API ongkos kirim mengembalikan data yang valid.

## 4. Kriteria Kelayakan (Entry & Exit Criteria)

### Kriteria Masuk (Entry Criteria):
* Katalog produk elektronik beserta varian dan stok awal telah dimasukkan ke database.
* API kurir logistik dan payment gateway (mode sandbox) sudah terhubung.
* Lingkungan uji (staging environment) siap diakses.

### Kriteria Keluar (Exit Criteria):
* Alur dari pemilihan varian produk elektronik hingga pembayaran dan perhitungan ongkos kirim berhasil (End-to-End Test Passed 100%).
* Tidak ada bug kritis pada sistem pengurangan stok otomatis dan status transaksi.

## 5. Sumber Daya & Perangkat Uji (Resources & Environment)
* **Perangkat:** Laptop (Windows/Mac) & Smartphone (Responsive Mobile View).
* **Browser:** Google Chrome, Mozilla Firefox, Microsoft Edge.
* **Tools Pendukung:** Postman (API Testing), GitHub Issues (Bug Tracking), Browser DevTools.
