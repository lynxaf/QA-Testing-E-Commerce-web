# Regression Test Results

## Project Information
* **Project:** E-Commerce Web Application (Electronic Store)
* **Testing Method:** Manual Functional and Regression Testing
* **Environment:** Windows 11 / Google Chrome (Desktop)
* **Related Defects:** DEF-001, DEF-002, DEF-003, and DEF-004

---

## Purpose
Tujuan dari *Regression Testing* ini adalah untuk memastikan bahwa perbaikan (*corrective actions*) yang diterapkan pada *defect* yang sebelumnya ditemukan (`DEF-001` hingga `DEF-004`) telah berhasil diselesaikan tanpa menimbulkan efek samping negatif atau merusak fitur lain yang sebelumnya sudah berjalan dengan normal.

---

## Corrective Actions Tested
1. **DEF-001 (Sign Up Validation):** Penambahan validasi *regex* email dan pengecekan *required field* pada form pendaftaran.
2. **DEF-002 (Sign In Authentication):** Perbaikan penanganan respons API autentikasi dan manajemen pesan error saat kredensial salah.
3. **DEF-003 (Out of Stock Indicator):** Sinkronisasi data inventaris *real-time* untuk menonaktifkan tombol "Tambah ke Keranjang" saat stok bernilai 0.
4. **DEF-004 (Payment Gateway Simulation):** Perbaikan integrasi *mock payment gateway* dan penanganan *callback response* pada simulasi pembayaran VA/QRIS.

---

## Defect Retest Results
| Test Case ID | Related Defect | Retest Scenario | Expected Result | Retest Result |
| :--- | :--- | :--- | :--- | :--- |
| **TC-CAT-01N** | DEF-001 | Submit Sign Up dengan email tidak valid & password kosong | Sistem menolak pendaftaran dan menampilkan pesan error validasi | Pass |
| **TC-CAT-02N** | DEF-002 | Login dengan email tidak terdaftar atau password salah | Sistem menampilkan pesan error kredensial dan menolak akses | Pass |
| **TC-CAT-04** | DEF-003 | Buka halaman produk dengan sisa stok 0 | Tombol "Tambah ke Keranjang" berubah menjadi *disabled* & berlabel "Stok Habis" | Pass |
| **TC-PAY-01** | DEF-004 | Melakukan simulasi pembayaran via VA / QRIS | Transaksi sukses diproses dan user diarahkan ke halaman *Order Success* | Pass |

---

## Regression Test Execution
Fungsi-fungsi terkait di dalam aplikasi juga diuji kembali untuk memastikan stabilitas sistem secara keseluruhan setelah perbaikan diterapkan.

| Test Case ID | Regression Scenario | Result |
| :--- | :--- | :--- |
| **TC-CAT-01** | Pendaftaran akun baru dengan data valid | Pass |
| **TC-CAT-02** | Login pengguna dengan akun terdaftar | Pass |
| **TC-CRT-01** | Menambahkan produk elektronik ke keranjang | Pass |
| **TC-ADM-01** | Login Admin Panel | Pass |
| **TC-ADM-02** | Menambahkan kategori produk baru | Pass |
| **TC-ADM-05** | Menambahkan katalog produk baru | Pass |
| **TC-ADM-06** | Pembaruan status pesanan (*Orders*) | Pass |

---

## Regression Results Summary
* **Regression Tests Executed:** 11
* **Passed:** 11
* **Failed:** 0

Tidak ada *defect* baru yang ditemukan selama proses *regression testing* berlangsung. Seluruh perbaikan berhasil mengatasi `DEF-001`, `DEF-002`, `DEF-003`, dan `DEF-004`, sementara fitur-fitur pendukung lainnya tetap beroperasi dengan stabil sesuai ekspektasi.

---

## Conclusion
Pengujian regresi mengonfirmasi bahwa seluruh perbaikan kode yang diterapkan berhasil menyelesaikan masalah tanpa mengganggu fungsionalitas inti aplikasi e-commerce. Semua kasus uji yang sebelumnya gagal kini telah berstatus **PASS**, dan sistem siap untuk tahap pengoperasian atau *deployment* lanjutan.
