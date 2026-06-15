# 📊 Data Preprocessing Latihan (Pertemuan 11)

Halo! Repositori ini berisi dokumentasi dan kode latihan saya dalam mempelajari tahapan **Data Preprocessing** (Pra-pemrosesan Data) menggunakan Python. Ini merupakan bagian dari materi kuliah Analisis Data / Rekayasa Sistem Informasi.

Proyek ini mensimulasikan bagaimana seorang Data Analyst membersihkan data mentah yang kotor (`data_penjualan_latihan.csv`) hingga siap untuk digunakan dalam tahap analisis atau pembuatan machine learning.

---

## 🛠️ Library Python yang Digunakan
Di awal proyek, kita memuat beberapa alat (library) penting:
* **Pandas & NumPy**: Untuk membaca, memanipulasi, dan mengolah data tabel.
* **Matplotlib**: Untuk membuat grafik (visualisasi) kualitas data.
* **Scikit-Learn (MinMaxScaler)**: Untuk menyamakan skala angka (Normalisasi).
* **NLTK (Natural Language Toolkit)**: Disiapkan untuk belajar mengolah data teks (NLP) pada kolom deskripsi.

---

## 📈 Alur Kerja & Logika Preprocessing

### 1. Eksplorasi Awal Data (Data Exploration)
Sebelum diapa-apakan, data diintip terlebih dahulu menggunakan fungsi:
* `df.head()` : Melihat 5 baris teratas data.
* `df.info()` : Mengetahui tipe data dan mendeteksi kolom mana saja yang isinya bolong (kosong).
* `df.describe()` : Melihat ringkasan statistik (seperti rata-rata, nilai terkecil, dan terbesar).

### 2. Analisis Nilai yang Hilang (Missing Value Analysis)
Menggunakan perintah `df.isnull().sum()`, ditemukan bahwa data ini memiliki **1 nilai kosong** di hampir setiap kolom penting (`harga`, `jumlah`, `rating`, dan `deskripsi`). Untuk mempermudah pemantauan, jumlah data yang hilang ini juga digambarkan dalam bentuk **Grafik Batang (Bar Chart)**.

### 3. Pembersihan Data (Data Cleaning)
Data yang bolong tidak boleh dibiarkan karena bisa merusak analisis. Strategi yang digunakan di proyek ini adalah **Imputasi (Pengisian Nilai)**:
* **Kolom Angka (`harga`, `jumlah`, `rating`)**: Nilai yang kosong otomatis diisi dengan **nilai rata-rata (mean)** dari masing-masing kolom tersebut.
* **Kolom Teks (`deskripsi`)**: Nilai yang kosong diisi dengan teks pengganti: `"tidak ada deskripsi"`.

Setelah dibersihkan, dipastikan kembali bahwa sudah tidak ada lagi data yang kosong (`0 missing values`).

### 4. Transformasi & Integrasi Data (Feature Engineering)
Agar data lebih kaya informasi, dilakukan beberapa modifikasi:
* **Membuat Kolom `total_harga`**: Hasil perkalian otomatis antara kolom `harga` dan `jumlah`.
* **Ekstrak Waktu (`bulan`)**: Mengubah teks tanggal menjadi format tanggal komputer, lalu diambil angka bulannya saja.
* **Normalisasi Fitur**: Mengubah angka di kolom harga dan jumlah menjadi skala **0 sampai 1** menggunakan *MinMaxScaler* agar rentang datanya seragam.

---

## 📁 Struktur File di Repositori
* `data_penjualan_latihan.csv` : File data mentah yang digunakan sebagai bahan latihan.
* `notebook_preprocessing.ipynb` / `main.py` : File kode Python tempat proses pembersihan data dijalankan.
* `README.md` : Dokumentasi panduan ini.

---

## 🧠 Pembelajaran yang Saya Dapatkan
Melalui latihan Pertemuan 11 ini, saya memahami bahwa data di dunia nyata seringkali tidak sempurna (ada yang kosong atau skalanya berantakan). Proses *Data Preprocessing* adalah kunci paling krusial sebelum kita bisa membuat grafik yang benar atau melatih model AI.

*Catatan: Repositori ini dibuat untuk tujuan belajar dan dokumentasi tugas kuliah.*
