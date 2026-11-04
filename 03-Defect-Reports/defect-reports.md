# BUG REPORT & DEFECT TRACKING TEMPLATE
**Proyek:** Website E-Commerce Penjualan Produk Elektronik  
**Status Dokumen:** Aktif / Digunakan untuk Pelacakan Isu  

---

## 1. Panduan Format Pelaporan Bug (Bug Report Guidelines)
Setiap laporan *bug* yang ditemukan saat pengujian harus mencakup informasi berikut agar mudah dipahami dan direproduksi oleh *developer*:
* **Bug ID:** Kode unik (Contoh: `DEF-001`)
* **Judul Bug:** Ringkasan singkat masalah yang terjadi.
* **Severity (Tingkat Keparahan):** *Critical, High, Medium, Low*.
* **Priority (Prioritas Perbaikan):** *P1 (High), P2 (Medium), P3 (Low)*.
* **Environment:** Perangkat, browser, atau sistem operasi yang digunakan saat bug ditemukan.
* **Steps to Reproduce:** Langkah-langkah kronologis untuk memunculkan kembali *bug* tersebut.
* **Expected Result:** Hasil yang seharusnya terjadi berdasarkan sistem.
* **Actual Result:** Hasil nyata atau error yang terjadi pada aplikasi.

---

## 2. Laporan Bug
🔴 DEF-001: Gagal Validasi Error pada Halaman Sign Up
- **Modul:** Autentikasi / Pendaftaran
- **Severity:** High
- **Priority:** P1
- **Status:** Open
- **Environment:** Google Chrome (Desktop), Windows 11
- **Steps to Reproduce:**
  1. Buka halaman Sign Up.
  2. Isi data *full name*, masukkan email dengan sintaks/format yang salah, dan kosongkan *password*.
  3. Klik tombol "Create New Account".
- **Expected Result:** Sistem memberikan pesan error bahwa format email salah dan *password* wajib diisi, serta pengguna gagal dialihkan ke halaman login.
- **Actual Result:** Sistem tidak memunculkan pesan validasi error yang sesuai dan form tetap terkirim sebagian.
- **Attachment / Catatan:** Perlu pengecekan pada skrip validasi *frontend regex email* dan penanganan *required fields*.

---

🔴 DEF-002: Gagal Autentikasi Login Pengguna (Sign In)
- **Modul:** Autentikasi / Login
- **Severity:** High
- **Priority:** P1
- **Status:** Open
- **Environment:** Google Chrome (Desktop), Windows 11
- **Steps to Reproduce:**
  1. Buka halaman Sign In.
  2. Masukkan email yang belum terdaftar atau salah format, serta *password* yang salah/kosong.
  3. Klik tombol "Sign In".
- **Expected Result:** Sistem menampilkan pesan error bahwa email tidak ditemukan atau kombinasi email/password salah, dan pengguna tetap berada di halaman login.
- **Actual Result:** Sistem memberikan respons waktu muat yang lama atau menampilkan pesan error generik tanpa kejelasan informasi kredensial.
- **Attachment / Catatan:** Periksa penanganan respons API autentikasi di sisi *backend* dan manajemen *state error message*.

---

🔴 DEF-003: Ketidaksesuaian Indikator Stok Produk Habis (Out of Stock)
- **Modul:** Katalog & Inventaris Produk
- **Severity:** Medium
- **Priority:** P2
- **Status:** Open
- **Environment:** Google Chrome (Desktop), Windows 11
- **Steps to Reproduce:**
  1. Buka halaman detail produk elektronik yang stoknya bernilai 0 di database.
  2. Amati tombol aksi utama dan label informasi ketersediaan produk.
- **Expected Result:** Tombol "Tambah ke Keranjang" berubah menjadi tidak aktif (*disabled*) dan sistem menampilkan label teks "Stok Habis".
- **Actual Result:** Tombol "Tambah ke Keranjang" masih bisa diklik meskipun stok produk bernilai 0.
- **Attachment / Catatan:** Perlu validasi sinkronisasi data sisa stok inventaris pada komponen tombol aksi *frontend*.


---

🔴 DEF-004: Gagal Simulasi Pembayaran Sukses (Virtual Account / QRIS)
- **Modul:** Pembayaran & Checkout (Payment)
- **Severity:** High
- **Priority:** P1
- **Status:** Open
- **Environment:** Google Chrome (Desktop), Windows 11
- **Steps to Reproduce:**
  1. Berada di halaman checkout, pilih metode pembayaran (misal: VA Bank Mandiri atau QRIS).
  2. Klik tombol "Bayar Sekarang" atau selesaikan simulasi pembayaran.
  3. Amati perubahan halaman setelah konfirmasi sistem.
- **Expected Result:** Sistem menampilkan instruksi pembayaran atau QR code dengan benar, dan setelah simulasi pembayaran berhasil, pengguna diarahkan ke halaman konfirmasi pesanan (*Order Success*) dengan status "Paid" atau "Menunggu Diproses".
- **Actual Result:** Halaman mengalami *loading* berkepanjangan atau gagal mengonfirmasi status pembayaran, sehingga pengguna tetap tertahan di halaman pembayaran tanpa diarahkan ke halaman sukses.
- **Attachment / Catatan:** Perlu investigasi pada integrasi *gateway* pembayaran tiruan (*mock payment gateway*) dan penanganan *callback response* di sisi *backend*.
