# BUG REPORT & DEFECT TRACKING TEMPLATE
**Proyek:** Website E-Commerce Penjualan Produk Elektronik  
**Status Dokumen:** Aktif / Digunakan untuk Pelacakan Isu  

---

## 1. Panduan Format Pelaporan Bug (Bug Report Guidelines)
Setiap laporan *bug* yang ditemukan saat pengujian harus mencakup informasi berikut agar mudah dipahami dan direproduksi oleh *developer*:
* **Bug ID:** Kode unik (Contoh: `BUG-ELEC-01`)
* **Judul Bug:** Ringkasan singkat masalah yang terjadi.
* **Severity (Tingkat Keparahan):** *Critical, High, Medium, Low*.
* **Priority (Prioritas Perbaikan):** *P1 (High), P2 (Medium), P3 (Low)*.
* **Environment:** Perangkat, browser, atau sistem operasi yang digunakan saat bug ditemukan.
* **Steps to Reproduce:** Langkah-langkah kronologis untuk memunculkan kembali *bug* tersebut.
* **Expected Result:** Hasil yang seharusnya terjadi berdasarkan sistem.
* **Actual Result:** Hasil nyata atau error yang terjadi pada aplikasi.

---

## 2. Laporan Bug (Sample Defect Log)

### 🔴 BUG-ELEC-01: Harga Varian Produk Tidak Berubah Saat Dipilih
* **Modul:** Katalog & Varian Produk
* **Severity:** High
* **Priority:** P1
* **Status:** Open
* **Environment:** Google Chrome (Desktop), Windows 11
* **Steps to Reproduce:**
  1. Buka halaman detail produk *Smartphone X*.
  2. Klik pilihan varian warna "Midnight Black" dengan kapasitas "RAM 8GB".
  3. Amati perubahan harga pada halaman.
* **Expected Result:** Harga produk otomatis berubah sesuai dengan harga varian RAM 8GB (misal dari Rp3.000.000 menjadi Rp3.500.000).
* **Actual Result:** Harga produk tetap pada harga dasar awal (*default price*) dan tidak merespons perubahan varian.
* **Attachment / Catatan:** Perlu pengecekan pada logika *state management frontend* atau respons API *variants*.

---

### 🟡 BUG-ELEC-02: Tombol Pembayaran QRIS Tidak Merespons Saat Diklik
* **Modul:** Payment Gateway / Checkout
* **Severity:** Critical
* **Priority:** P1
* **Status:** In Progress
* **Environment:** Safari / Mobile View (iOS)
* **Steps to Reproduce:**
  1. Masuk ke halaman checkout pesanan produk elektronik.
  2. Pilih metode pembayaran "QRIS".
  3. Klik tombol "Lanjutkan Pembayaran".
* **Expected Result:** Sistem memuat kode QR pembayaran atau mengarahkan ke halaman *gateway*.
* **Actual Result:** Tombol tidak memberikan reaksi apa pun dan tidak memuat halaman *gateway*.
* **Attachment / Catatan:** Terdeteksi *Console Error: Uncaught TypeError in payment handler script*.
