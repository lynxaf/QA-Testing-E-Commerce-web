# SOFTWARE TEST CASES & SCENARIOS
**Proyek:** Website E-Commerce Penjualan Produk Elektronik  
**Modul Utama:** Katalog, Varian Produk, Keranjang (Cart), & Perhitungan Ongkir  

---
## Ringkasan Eksekusi Pengujian
Kasus pengujian di website penjualan produk elektronik ini untuk mengevaluasi fungsi website yang sengaja dirancang untuk menunjukkan pengujian yang berhasil dan yang gagal atau diidentifikasi cacat diringkas di tabel berikut :

## Pengujian Halaman Pelanggan
### 1. Modul Katalog & Varian Produk Elektronik

### TC-CAT-01: Halaman Sign Up (Pendaftaran Pengguna)
* **Test Scenario:** Memastikan pengguna dapat melakukan sign-up (pendaftaran) dan menggunakan dua case, yakni case positive dan case negative, agar diketahui masing-masing respons sistem.
* **Test Type:** : Positive   
* **Pre-Condition:** Pengguna berhasil melakukan pendaftaran kemudian ke halaman login.
*  **Test Steps:**
*  1. Buka halaman Sign Up
*  2. Isi data full name, email, dan password
*  3. Klik Tombol Create New Account
*  **Expected Result:**
*  User diarahkan ke halaman login
*  User berhasil melakukan login berarti data user sudah terdaftar
*  **Status:** Lulus
*  
*  **Test Type** : Negative
*  **Pre-Condition:** Pengguna berhasil melakukan pendaftaran kemudian ke halaman login.
*  **Test Steps:**
*  1. Buka halaman sign-up
   2. Isi data full name, email (dengan sintaks email yang salah), dan password kosong
   3. Klik Tombol Create New Account
*  **Expected Result:**
*  User diberikan pesan bahwa email salah dan password wajib diisi
*  User tidak diarahkan ke halaman login dan data tidak terdaftar di database
*  **Status:** Gagal
*  **Related Defect:** DEF-001


#### TC-CAT-02: Memilih Varian Produk (Warna & Kapasitas Memori)
* **Test Scenario:** Memastikan sistem memperbarui harga, ketersediaan stok, dan gambar secara dinamis saat pengguna memilih varian spesifik (Contoh: RAM 8GB/256GB warna Hitam).
* **Pre-condition:** Pengguna berada di halaman detail produk elektronik (misalnya: Smartphone X).
* **Test Steps:**
  1. Buka halaman detail produk elektronik.
  2. Pilih varian Kapasitas "RAM 8GB / 256GB".
  3. Pilih varian Warna "Midnight Black".
* **Expected Result:** 
  * Harga produk berubah sesuai dengan varian yang dipilih.
  * Gambar produk berubah menyesuaikan warna yang dipilih.
  * Status stok memperlihatkan informasi ketersediaan aktual (misal: "Stok Tersedia: 15 unit").
* **Test Type:** Positive / Functional

### TC-CAT-02: Validasi Produk Habis (Out of Stock)
* **Test Scenario:** Memastikan tombol "Tambah ke Keranjang" terkunci atau berubah menjadi "Stok Habis" ketika sisa inventaris bernilai 0.
* **Pre-condition:** Pengguna membuka produk elektronik yang stoknya sudah habis.
* **Test Steps:**
  1. Buka halaman detail produk elektronik dengan stok 0.
  2. Perhatikan tombol aksi utama.
* **Expected Result:** 
  * Tombol "Tambah ke Keranjang" menjadi tidak aktif (disabled).
  * Sistem menampilkan label/notifikasi teks "Stok Habis".
* **Test Type:** Negative / Edge Case

---

## 2. Modul Keranjang & Manajemen Stok (Inventory & Cart)

### TC-CRT-01: Penambahan Produk ke Keranjang
* **Test Scenario:** Memastikan produk elektronik dengan varian yang dipilih berhasil masuk ke dalam keranjang belanja.
* **Pre-condition:** Pengguna telah memilih varian produk dan menentukan jumlah pembelian (misal: 1 unit).
* **Test Steps:**
  1. Klik tombol "Tambah ke Keranjang".
  2. Klik ikon Keranjang Belanja di sudut kanan atas.
* **Expected Result:** 
  * Muncul notifikasi sukses (toast message "Produk berhasil ditambahkan").
  * Badge/angka pada ikon keranjang bertambah.
  * Halaman keranjang menampilkan nama produk, varian yang dipilih, harga satuan, dan total harga yang benar.
* **Test Type:** Positive

### TC-CRT-02: Pencegahan Pembelian Melebihi Stok (Overselling Prevention)
* **Test Scenario:** Memastikan sistem menolak atau membatasi pengguna saat mencoba memasukkan jumlah produk ke keranjang melebihi sisa stok fisik gudang.
* **Pre-condition:** Stok produk yang tersedia di sistem adalah 3 unit.
* **Test Steps:**
  1. Buka halaman keranjang belanja.
  2. Ubah jumlah kuantiti produk menjadi 5 unit, lalu klik perbarui.
* **Expected Result:** 
  * Sistem menampilkan pesan peringatan bahwa jumlah melebihi stok maksimum yang tersedia.
  * Kuantiti di keranjang otomatis dikembalikan ke batas maksimum stok (3 unit) atau ditolak perubahannya.
* **Test Type:** Negative / Concurrency Check

---

## 3. Modul Checkout & Integrasi Logistik (Ongkir)

### TC-CHK-01: Perhitungan Ongkos Kirim Berdasarkan Alamat & Kurir
* **Test Scenario:** Memastikan sistem berhasil mengambil data tarif ongkos kirim secara akurat dari API kurir pihak ketiga berdasarkan kota tujuan dan berat produk elektronik.
* **Pre-condition:** Pengguna berada di halaman Checkout dan telah mengisi alamat pengiriman lengkap.
* **Test Steps:**
  1. Pilih opsi layanan kurir (Contoh: JNE / SiCepat - Layanan Reguler).
  2. Periksa rincian biaya pengiriman pada ringkasan pembayaran.
* **Expected Result:** 
  * Sistem menampilkan pilihan layanan kurir beserta estimasi hari tiba dan tarif biaya kirim yang valid.
  * Total pembayaran akhir (Grand Total) otomatis bertambah secara akurat dengan nominal ongkos kirim yang dipilih.
* **Test Type:** Positive / Integration Testing

### TC-CHK-02: Penambahan Biaya Asuransi Pengiriman Barang Elektronik
* **Test Scenario:** Memastikan sistem menambahkan komponen biaya asuransi pengiriman secara otomatis atau opsional untuk produk bernilai tinggi.
* **Pre-condition:** Produk elektronik kategori bernilai tinggi berada di halaman checkout.
* **Test Steps:**
  1. Centang opsi "Gunakan Asuransi Pengiriman Elektronik".
  2. Amati kalkulasi pada rincian tagihan.
* **Expected Result:** 
  * Biaya asuransi ditambahkan ke dalam rincian tagihan sesuai persentase dari harga barang.
  * Total tagihan akhir diperbarui dengan benar.
* **Test Type:** Functional

---

## 4. Modul Pembayaran (Payment Gateway)

### TC-PAY-01: Simulasi Pembayaran Sukses (Virtual Account / QRIS)
* **Test Scenario:** Memastikan status pesanan berubah menjadi Paid / Processing setelah simulasi pembayaran berhasil dilakukan pada sistem payment gateway.
* **Pre-condition:** Pengguna memilih metode pembayaran (misal: QRIS) dan berada di halaman instruksi pembayaran.
* **Test Steps:**
  1. Lakukan simulasi pembayaran berhasil melalui mode sandbox.
  2. Tunggu beberapa detik atau arahkan kembali ke halaman riwayat pesanan.
* **Expected Result:** 
  * Halaman web otomatis mengarahkan ke halaman Order Success / Thank You.
  * Status transaksi di Dashboard / Riwayat Pesanan berubah dari Pending menjadi Berhasil / Dibayar.
  * Stok produk di database berkurang secara otomatis sesuai jumlah transaksi.
* **Test Type:** Positive / Integration Testing
