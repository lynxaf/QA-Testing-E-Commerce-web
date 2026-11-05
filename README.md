# QA-Testing-E-Commerce-web
---

## Project Overview
* **Application Type:** E-Commerce Web (Customer Frontend & Admin Dashboard)
* **Testing Methodology:** Manual Functional Testing, Negative Testing, API Testing, & Regression Testing
* **Environment:** Windows 11, Google Chrome (Desktop)
* **Core Deliverable:** 100% Pass Rate with zero unresolved high-severity bugs before deployment readiness.

---

##  Testing Scope & Key Modules
1. **Customer / Frontend Module:**
   - **Authentication:** Sign Up (`TC-CAT-01`) & Sign In (`TC-CAT-02`) with robust input validation.
   - **Product Catalog & Inventory:** Varian produk dan pengecekan batas stok kosong (*Out of Stock*).
   - **Shopping Cart:** Penambahan dan pengelolaan item keranjang belanja.
   - **Checkout & Payment:** Simulasi pembayaran digital melalui Virtual Account (VA) dan QRIS.
2. **Admin Panel / Backend Management Module:**
   - Autentikasi Admin, Manajemen Kategori, Lokasi/Gudang, Brand, Katalog Produk, Pesanan, dan Pelanggan.

---

## Summary of Testing & Defect Metrics
* **Total Test Cases Executed:** 18 Test Cases
* **Initial Defect Found:** 4 Major Defects (`DEF-001` s.d. `DEF-004`)
* **Defect Resolution Status:** 100% Resolved (Closed)
* **Regression Test Pass Rate:** 100% (11 regression test scenarios passed successfully with no side effects)

---

## 📂 Repository Structure
Struktur direktori dirancang secara modular dan profesional:
- [`01-test-plan/`](https://github.com/lynxaf/QA-Testing-E-Commerce-web/tree/main/01-test-plan) — Dokumen Rencana Uji, ruang lingkup, dan strategi pengujian.
- [`02-test-cases/`](https://github.com/lynxaf/QA-Testing-E-Commerce-web/tree/main/02-test-cases) — Rincian skenario uji positif dan negatif untuk setiap modul.
- [`03-Defect-Reports/`](https://github.com/lynxaf/QA-Testing-E-Commerce-web/tree/main/03-Defect-Reports) — Dokumentasi laporan bug, tingkat keparahan (*severity*), dan prioritas (*priority*).
- [`04-regresion-testing/`](https://github.com/lynxaf/QA-Testing-E-Commerce-web/tree/main/04-regresion-testing) — Hasil pengujian regresi untuk memastikan stabilitas sistem setelah perbaikan kode.
- [`05-root-cause-analysis/`](https://github.com/lynxaf/QA-Testing-E-Commerce-web/tree/main/05-root%20-couse-analysis) — Analisis akar permasalahan (*Root Cause Analysis*) dari setiap *defect* yang ditemukan.
- [`06-test-summary/`](https://github.com/lynxaf/QA-Testing-E-Commerce-web/tree/main/06-test-summary) — Laporan ringkasan eksekutif akhir (*Final Test Summary Report*).

---

## API Testing & Postman Integration
Selain pengujian antarmuka, portofolio ini juga mencakup pengujian API menggunakan **Postman**:
- Memvalidasi endpoint REST API (autentikasi, katalog produk, dan transaksi).
- Menguji *positive & negative cases* untuk memastikan ketepatan kode status HTTP (`200 OK`, `400 Bad Request`, `401 Unauthorized`, dll).
- Memverifikasi konsistensi payload data antara *frontend request* dan penyimpanan basis data.

---

## Key Takeaways & Skills Demonstrated
* Penguasaan penuh terhadap siklus hidup pengujian perangkat lunak (**STLC**).
* Ketelitian dalam menyusun kasus uji fungsional dan pengujian batas (*boundary value analysis*).
* Kemampuan analitis dalam menyusun *Root Cause Analysis* bersama pengembang (*developer*).
* Pelacakan isu yang terstruktur menggunakan standar manajemen *bug tracking*.
