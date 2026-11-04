# SOFTWARE TEST CASES & SCENARIOS
**Proyek:** Website E-Commerce Penjualan Produk Elektronik  
**Modul Utama:** Katalog, Varian Produk, Keranjang (Cart), & Perhitungan Ongkir  

---
## Ringkasan Eksekusi Pengujian

Kasus pengujian di website penjualan produk elektronik ini untuk mengevaluasi fungsi website yang sengaja dirancang untuk menunjukkan pengujian yang berhasil dan yang gagal atau diidentifikasi cacat diringkas di tabel berikut:

| Test Case ID | Modul / Skenario Pengujian | Test Type | Result | Defect Ref |
| :--- | :--- | :--- | :--- | :--- |
| **TC-CAT-01** | Halaman Sign Up (Pendaftaran Pengguna) | Positive | Lulus | - |
| **TC-CAT-01N** | Halaman Sign Up (Validasi Error Input) | Negative | Gagal | DEF-001 |
| **TC-CAT-02** | Halaman Sign In (Login Pengguna) | Positive | Lulus | - |
| **TC-CAT-02N** | Halaman Sign In (Validasi Gagal Login) | Negative | Gagal | DEF-002 |
| **TC-CAT-04** | Validasi Produk Habis (Out of Stock) | Negative | Gagal | DEF-003 |
| **TC-CRT-01** | Penambahan Produk ke Keranjang | Positive | Lulus | - |
| **TC-PAY-01** | Simulasi Pembayaran Sukses (VA / QRIS) | Positive | Gagal | DEF-004 |
| **TC-ADM-01** | Login Admin Panel | Positive | Lulus | - |
| **TC-ADM-02** | Manajemen Kategori (Add Category) | Positive | Lulus | - |
| **TC-ADM-02N** | Validasi Gagal Tambah Kategori | Negative | Lulus | - |
| **TC-ADM-03** | Manajemen Lokasi / Gudang (Add Location) | Positive | Lulus | - |
| **TC-ADM-03N** | Validasi Gagal Tambah Lokasi | Negative | Lulus | - |
| **TC-ADM-04** | Manajemen Merek (Add Brand) | Positive | Lulus | - |
| **TC-ADM-04N** | Validasi Gagal Tambah Brand | Negative | Lulus | - |
| **TC-ADM-05** | Manajemen Katalog Produk (Add Product) | Positive | Lulus | - |
| **TC-ADM-05N** | Validasi Gagal Tambah Produk | Negative | Lulus | - |
| **TC-ADM-06** | Manajemen Pesanan (Orders Management) | Positive | Lulus | - |
| **TC-ADM-07** | Manajemen Data Pelanggan (Customers Tracking) | Positive | Lulus | - |

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
* **Status:** Gagal
* **Related Defect:** DEF-002
  
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

---

## 4. Modul Panel Admin (Administrator Panel)

### TC-ADM-01: Login Admin Panel
#### Test Type: Positive
* **Test Scenario:** Memastikan admin dapat masuk ke dashboard panel administrasi menggunakan kredensial yang sah dan valid.
* **Pre-condition:** Admin sudah terdaftar di database sistem dengan hak akses (role) administrator dan berada di halaman login admin.
* **Test Steps:**
  * 1. Buka halaman login admin.
  * 2. Masukkan email dan password admin yang valid.
  * 3. Klik tombol "Sign In" atau "Login".
* **Expected Result:**
  * Sistem memvalidasi hak akses admin.
  * Admin berhasil masuk dan diarahkan ke halaman utama Dashboard Admin.
* **Status:** Lulus

---

### TC-ADM-02: Manajemen Kategori (Add Category)
#### Test Type: Positive
* **Test Scenario:** Memastikan admin berhasil menambahkan kategori produk baru ke dalam sistem e-commerce.
* **Pre-condition:** Admin sudah berhasil login dan berada di halaman menu "Categories".
* **Test Steps:**
  * 1. Klik menu "Categories" pada panel navigasi kiri.
  * 2. Klik tombol tambah/buat kategori baru.
  * 3. Masukkan nama kategori baru (misal: "Smartphone & Accessories").
  * 4. Klik tombol simpan (*Save* / *Submit*).
* **Expected Result:**
  * Sistem memproses data dan menampilkan notifikasi sukses.
  * Kategori baru muncul di dalam daftar (tabel) kategori.
* **Status:** Lulus
  
#### Test Type: Negative
* **Test Scenario:** Memastikan sistem menolak penambahan kategori baru jika nama kategori dikosongkan.
* **Pre-condition:** Admin berada di halaman tambah kategori.
* **Test Steps:**
  * 1. Kosongkan kolom input nama kategori.
  * 2. Klik tombol simpan (*Save* / *Submit*).
* **Expected Result:**
  * Sistem menampilkan pesan error validasi (misal: "Category name is required" atau field menyala merah).
  * Data kategori baru gagal disimpan ke dalam database.
* **Status:** Lulus
---

### TC-ADM-03: Manajemen Lokasi Toko / Gudang (Add Location)
#### Test Type: Positive
* **Test Scenario:** Memastikan admin berhasil menambahkan lokasi operasional, toko, atau gudang baru.
* **Pre-condition:** Admin berada di halaman manajemen "Locations".
* **Test Steps:**
  * 1. Klik menu "Locations" pada panel navigasi.
  * 2. Pilih opsi untuk menambah lokasi baru.
  * 3. Isi detail informasi lokasi (nama lokasi, alamat, atau kota).
  * 4. Klik tombol simpan.
* **Expected Result:**
  * Lokasi baru berhasil disimpan oleh sistem.
  * Data lokasi baru muncul pada daftar manajemen lokasi.
* **Status:** Lulus
  
### TC-ADM-03N: Validasi Gagal Tambah Lokasi (Negative Test)
#### Test Type: Negative
* **Test Scenario:** Memastikan sistem menolak penyimpanan data lokasi jika informasi penting seperti nama lokasi atau alamat kosong.
* **Pre-condition:** Admin berada di halaman tambah lokasi.
* **Test Steps:**
  * 1. Biarkan formulir input lokasi dalam keadaan kosong.
  * 2. Klik tombol simpan.
* **Expected Result:**
  * Sistem memunculkan peringatan error terkait data yang wajib diisi.
  * Lokasi baru tidak ditambahkan ke dalam daftar lokasi.
* **Status:** Lulus
---

### TC-ADM-04: Manajemen Merek / Brand (Add Brand)
#### Test Type: Positive
* **Test Scenario:** Memastikan admin berhasil menambahkan merek produk elektronik baru ke dalam sistem.
* **Pre-condition:** Admin berada di halaman manajemen "Brands".
* **Test Steps:**
  * 1. Klik menu "Brands" pada navigasi.
  * 2. Klik tombol tambah brand baru.
  * 3. Masukkan nama brand (misal: "Samsung", "Apple", atau "Sony").
  * 4. Klik tombol simpan.
* **Expected Result:**
  * Brand baru berhasil ditambahkan ke database.
  * Nama brand terdaftar dan tampil pada tabel daftar brand.
* **Status:** Lulus
  
### TC-ADM-04N: Validasi Gagal Tambah Brand (Negative Test)
#### Test Type: Negative
* **Test Scenario:** Memastikan sistem mencegah duplikasi atau pengosongan nama saat menambah brand baru.
* **Pre-condition:** Brand dengan nama tertentu (misal: "Samsung") sudah terdaftar sebelumnya di sistem.
* **Test Steps:**
  * 1. Masukkan kembali nama brand yang sudah ada ("Samsung") atau kosongkan kolom input.
  * 2. Klik tombol simpan.
* **Expected Result:**
  * Sistem mendeteksi duplikasi data atau input kosong.
  * Pesan error ditampilkan dan proses penyimpanan dibatalkan.
* **Status:** Lulus
---

### TC-ADM-05: Manajemen Katalog Produk (Add Product)
#### Test Type: Positive
* **Test Scenario:** Memastikan admin dapat menambahkan produk elektronik baru beserta spesifikasi, harga, stok, kategori, dan brand yang sesuai.
* **Pre-condition:** Admin sudah menambahkan Kategori, Brand, dan Lokasi yang dibutuhkan sebelumnya.
* **Test Steps:**
  * 1. Klik menu "Products" pada navigasi dashboard.
  * 2. Klik tombol tambah produk baru.
  * 3. Lengkapi formulir produk (Nama Produk, Harga, Stok, Kategori, Brand, dan Lokasi).
  * 4. Klik tombol simpan / publikasikan produk.
* **Expected Result:**
  * Produk baru berhasil dibuat dan tersimpan di database sistem.
  * Produk langsung terindeks dan muncul di halaman katalog utama maupun panel manajemen produk admin.
* **Status:** Lulus
#### Test Type: Negative
* **Test Scenario:** Memastikan sistem menolak pembuatan produk baru jika parameter krusial (seperti harga bernilai negatif atau stok kosong) diabaikan.
* **Pre-condition:** Admin mengisi formulir produk dengan nilai harga negatif (misal: `-100000`) atau mengosongkan nama produk.
* **Test Steps:**
  * 1. Masukkan harga produk dengan angka negatif atau kosongkan field wajib.
  * 2. Klik tombol simpan / publikasikan.
* **Expected Result:**
  * Sistem menampilkan pesan validasi error (misal: "Price must be greater than 0").
  * Produk gagal disimpan ke database.
* **Status:** Lulus

---

### TC-ADM-06: Manajemen Pesanan (Orders Management)
#### Test Type: Positive
* **Test Scenario:** Memastikan admin dapat melihat, melacak, dan memperbarui status pesanan yang masuk dari pelanggan.
* **Pre-condition:** Ada transaksi atau pesanan masuk dari pembeli yang tercatat di sistem.
* **Test Steps:**
  * 1. Klik menu "Orders" pada panel navigasi.
  * 2. Pilih salah satu data pesanan dari daftar untuk melihat detail transaksi.
  * 3. Ubah status pesanan (misalnya dari "Pending" menjadi "Processing" atau "Completed").
  * 4. Simpan perubahan status.
* **Expected Result:**
  * Rincian pesanan (detail produk, pelanggan, total harga) tampil dengan akurat.
  * Status pesanan berhasil diperbarui secara *real-time* di dalam sistem.
* **Status:** Lulus

---

### TC-ADM-07: Manajemen Data Pelanggan (Customers Tracking)
#### Test Type: Positive
* **Test Scenario:** Memastikan admin dapat memantau data akun pelanggan yang terdaftar serta melihat riwayat performa transaksinya.
* **Pre-condition:** Admin berada di halaman menu "Customers" dashboard.
* **Test Steps:**
  * 1. Klik menu "Customers" pada navigasi samping.
  * 2. Amati daftar pelanggan yang terdaftar beserta informasi email dan jumlah transaksinya (total transactions).
* **Expected Result:**
  * Daftar pelanggan muncul secara lengkap dan terstruktur.
  * Informasi penting seperti nama akun, email, serta metrik performa transaksi (misalnya 0 atau lebih transaksi) terekam dengan benar sesuai aktivitas user.
* **Status:** Lulus
  
  
