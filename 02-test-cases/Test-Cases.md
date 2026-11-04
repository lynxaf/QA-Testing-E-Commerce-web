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
  
#### Test Type: Positive   
* **Pre-Condition:** Pengguna berhasil melakukan pendaftaran kemudian ke halaman login.
*  **Test Steps:**
*  1. Buka halaman Sign Up
*  2. Isi data full name, email, dan password
*  3. Klik Tombol Create New Account
*  **Expected Result:**
*  User diarahkan ke halaman login
*  User berhasil melakukan login berarti data user sudah terdaftar
*  **Status:** Lulus
  
#### Test Type: Negative
*  **Pre-Condition:** Pengguna berhasil melakukan pendaftaran kemudian diarahkan ke halaman login.
*  **Test Steps:**
*  1. Buka halaman sign-up
   2. Isi data full name, email (dengan sintaks email yang salah), dan password kosong
   3. Klik Tombol Create New Account
*  **Expected Result:**
*  User diberikan pesan bahwa email salah dan password wajib diisi
*  User tidak diarahkan ke halaman login dan data tidak terdaftar di database
*  **Status:** Gagal
*  **Related Defect:** DEF-001

### TC-CAT-02: Halaman Sign In (Login Pengguna)

#### Test Type: Positive
* **Test Scenario:** Memastikan pengguna yang sudah terdaftar dapat masuk (sign in) ke akun mereka menggunakan kredensial yang valid.
* **Pre-Condition:** Pengguna sudah memiliki akun terdaftar di database dan berada di halaman Sign In.
* **Test Steps:**
  * 1. Buka halaman Login / Sign In
  * 2. Masukkan email dan password yang valid sesuai data terdaftar
  * 3. Klik Tombol Sign In
* **Expected Result:**
  * User berhasil melakukan autentikasi dan diarahkan ke halaman dashboard / beranda
  * Informasi profil atau nama akun pengguna muncul di bagian header/profil
* **Status:** Lulus
  
#### Test Type: Negative
* **Pre-Condition:** Pengguna sudah terdaftar di database, namun belum melakukan login.
* **Test Steps:**
  * 1. Buka halaman Sign In
  * 2. Masukkan email yang belum terdaftar atau salah format, serta password yang salah/kosong
  * 3. Klik Tombol Sign In
* **Expected Result:**
  * Sistem menampilkan pesan error bahwa email tidak ditemukan atau kombinasi email dan password salah.
  * User gagal masuk ke halaman dashboard dan tetap berada di halaman login.
* **Status:** Lulus

  
#### TC-CAT-03: Memilih Varian Produk (Warna & Kapasitas Memori)
 ### Test Type: Positive
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
  *  **Status:** Gagal
*  **Related Defect:** DEF-002
  
### TC-CAT-04: Validasi Produk Habis (Out of Stock)
#### Test Type: Negative
* **Test Scenario:** Memastikan tombol "Tambah ke Keranjang" terkunci atau berubah menjadi "Stok Habis" ketika sisa inventaris bernilai 0.
* **Pre-condition:** Pengguna membuka halaman detail produk elektronik yang stoknya sudah habis (0 unit).
* **Test Steps:**
  * 1. Buka halaman detail produk elektronik dengan stok 0.
  * 2. Perhatikan tombol aksi utama dan label informasi ketersediaan.
* **Expected Result:**
  * Tombol "Tambah ke Keranjang" menjadi tidak aktif (disabled).
  * Sistem menampilkan label/notifikasi teks "Stok Habis".
* **Status:** Gagal
*  **Related Defect:** DEF-003

---

## 2. Modul Keranjang & Manajemen Stok (Inventory & Cart)

### TC-CRT-01: Penambahan Produk ke Keranjang
#### Test Type: Positive
* **Test Scenario:** Memastikan produk elektronik dengan varian yang dipilih berhasil masuk ke dalam keranjang belanja.
* **Pre-condition:** Pengguna telah memilih varian produk dan menentukan jumlah pembelian (misal: 1 unit).
* **Test Steps:**
  * 1. Klik tombol "Tambah ke Keranjang".
  * 2. Klik ikon Keranjang Belanja di sudut kanan atas.
* **Expected Result:**
  * Produk berhasil ditambahkan ke dalam keranjang tanpa error.
  * Halaman/modal keranjang menampilkan item produk beserta varian dan jumlah yang benar.
* **Status:** Lulus

---

## 3. Modul Pembayaran & Checkout (Payment)

### TC-PAY-01: Simulasi Pembayaran Sukses (Virtual Account / QRIS)
#### Test Type: Positive
* **Test Scenario:** Memastikan sistem berhasil memproses transaksi pembayaran menggunakan metode Virtual Account atau QRIS dan mengarahkan pengguna ke halaman konfirmasi sukses.
* **Pre-condition:** Pengguna sudah berada di halaman checkout dan memilih metode pembayaran (Virtual Account atau QRIS).
* **Test Steps:**
  * 1. Pilih metode pembayaran (misal: VA Bank Mandiri atau QRIS).
  * 2. Klik tombol "Bayar Sekarang" atau selesaikan simulasi pembayaran.
  * 3. Amati perubahan halaman setelah pembayaran dikonfirmasi oleh sistem.
* **Expected Result:**
  * Sistem menampilkan instruksi pembayaran atau QR code dengan benar.
  * Setelah simulasi pembayaran berhasil, pengguna diarahkan ke halaman *Order Success* (Konfirmasi Pesanan).
  * Status pesanan tercatat sebagai "Paid" atau "Menunggu Diproses" di dalam sistem.
* **Status:** Gagal
* **Related Defect:** DEF-004
  
  
