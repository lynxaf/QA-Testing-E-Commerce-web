# Root Cause Analysis (RCA)

## Project Information
* **Project:** E-Commerce Web Application (Electronic Store)
* **Project Type:** Simulated QA Portfolio Project
* **Analysis Method:** 5 Whys & Defect Pattern Analysis
* **Related Defects:** DEF-001, DEF-002, DEF-003, DEF-004

---

## 1. RCA for DEF-001: Sign Up Validation Failure
* **Problem Statement:** Form pendaftaran (*Sign Up*) berhasil mengirimkan data meskipun format email salah dan *password* kosong tanpa memunculkan pesan validasi error.
* **Root Cause:** Kurangnya implementasi validasi ekspresi reguler (*regex*) pada kolom input *frontend* serta tidak adanya *middleware* sanitasi data input wajib (*required fields*) pada *endpoint backend API*.
* **Corrective Action:** 
  * Menambahkan validasi format email berbasis *regex* di sisi komponen *frontend*.
  * Menambahkan pengecekan *payload* kosong pada fungsi pengendali pendaftaran di *backend*.
* **Preventive Action:** Menyusun daftar periksa (*checklist*) validasi form sebelum komponen dirilis untuk pengujian QA.

---

## 2. RCA for DEF-002: Sign In Authentication Failure
* **Problem Statement:** Proses *Sign In* gagal memberikan respons pesan kesalahan yang jelas ketika pengguna memasukkan kredensial yang tidak valid atau belum terdaftar.
* **Root Cause:** Kesalahan penanganan status respons (*error handling/status code*) dari API autentikasi, di mana kode status server (seperti `401 Unauthorized`) tidak ditangkap dengan baik oleh antarmuka pengguna (*frontend state management*).
* **Corrective Action:** 
  * Memperbaiki blok penangkapan *error* (`try-catch`) pada fungsi *login request*.
  * Memastikan *frontend* menampilkan pesan peringatan yang sesuai berdasarkan kode status dari *backend*.
* **Preventive Action:** Melakukan *unit testing* rutin pada modul autentikasi untuk berbagai skenario kredensial (valid vs invalid).

---

## 3. RCA for DEF-003: Out of Stock Indicator Failure
* **Problem Statement:** Tombol "Tambah ke Keranjang" tetap dapat diklik meskipun sisa stok produk di database sudah bernilai 0 (habis).
* **Root Cause:** Komponen tombol aksi pada halaman detail produk menggunakan data *state* statis atau tidak melakukan sinkronisasi waktu nyata (*real-time inventory sync*) dengan jumlah kuantitas stok terbaru di database.
* **Corrective Action:** 
  * Menghubungkan logika properti *disabled* pada tombol dengan kondisi sisa stok (`stock <= 0`).
  * Menambahkan label teks dinamis "Stok Habis" ketika kuantitas mencapai angka nol.
* **Preventive Action:** Memastikan pengujian batas kondisi (*boundary value analysis*) pada manajemen inventaris selalu disertakan dalam perencanaan uji coba.

---

## 4. RCA for DEF-004: Payment Gateway Simulation Failure
* **Problem Statement:** Simulasi pembayaran menggunakan Virtual Account atau QRIS mengalami kegagalan proses konfirmasi dan pengguna gagal diarahkan ke halaman sukses.
* **Root Cause:** Terjadi gangguan atau kesalahan pada konfigurasi *mock API endpoint* dari penyedia pembayaran tiruan, serta tidak adanya penanganan fungsi *callback/webhook* yang mengonfirmasi status sukses transaksi ke sistem utama.
* **Corrective Action:** 
  * Memperbaiki alur simulasi respon balik (*mock response*) pada modul pembayaran agar mengembalikan status `Paid` dengan benar.
  * Memastikan *router* navigasi mengarahkan pengguna ke halaman *Order Success* setelah respons pembayaran diterima.
* **Preventive Action:** Melakukan pengujian integrasi (*integration testing*) secara berkala pada seluruh alur transaksi pembayaran (*checkout flow*).

---

## Summary & Conclusion
Sebagian besar akar masalah dari *defect* yang ditemukan bersumber dari **celah validasi input di sisi antarmuka (*frontend*)**, **kurangnya sinkronisasi status data**, serta **penanganan respons API (*error/status handling*) yang belum optimal**. Dengan diterapkannya tindakan korektif dan preventif di atas, kualitas sistem meningkat dan risiko kemunculan *bug* serupa pada rilis mendatang dapat diminimalkan.
