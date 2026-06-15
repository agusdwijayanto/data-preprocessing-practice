# 📊 Sales Data Preprocessing & Analytics

Repositori ini berisi dokumentasi dan implementasi kode Python untuk tahapan **Data Preprocessing** (Pra-pemrosesan Data) pada dataset transaksi penjualan. Proyek ini mensimulasikan alur kerja seorang *Data Analyst* dalam mengolah data mentah yang kotor (*raw data*) hingga bertransformasi menjadi dataset yang bersih, valid, dan siap digunakan untuk kebutuhan visualisasi bisnis (*Business Intelligence*) maupun pemodelan *Machine Learning*.

---

## 🛠️ Ekosistem Teknologi & Library
Proyek ini dibangun menggunakan bahasa pemrograman Python dengan memanfaatkan beberapa library standar industri berikut:
* **Pandas:** Digunakan sebagai core engine untuk manipulasi data tabular dan manajemen DataFrame.
* **NumPy:** Digunakan untuk komputasi numerik array dan kalkulasi statistik data penjualan.
* **Matplotlib:** Digunakan untuk menghasilkan visualisasi grafis, histogram distribusi, dan matriks kualitas data.
* **Scikit-Learn (MinMaxScaler):** Digunakan untuk melakukan normalisasi fitur numerik agar skala data berada dalam rentang yang seimbang.
* **NLTK (Natural Language Toolkit):** Digunakan untuk analisis teks tingkat dasar (*Text Mining / Natural Language Processing*) pada ulasan produk.

---

## 📈 Alur Kerja Proyek (Step-by-Step)

### 1. Eksplorasi Data Awal (Data Exploration)
Sebelum melakukan pembersihan, karakteristik dasar dataset diperiksa terlebih dahulu menggunakan fungsi agregasi Pandas:
* `df.head()`: Mengidentifikasi sampel struktur kolom dan representasi baris awal dataset.
* `df.info()`: Mendeteksi tipe data (fitur numerik dan kategorikal) serta mengukur volume data non-null.
* `df.describe()`: Menghasilkan ringkasan statistik deskriptif (Mean, Median, Standar Deviasi, Nilai Minimum, dan Maksimum).

### 2. Analisis Nilai yang Hilang (Missing Value Analysis)
Melalui fungsi `df.isnull().sum()`, ditemukan anomali berupa nilai kosong (*missing values*) pada kolom-kolom krusial bisnis seperti `harga`, `jumlah`, `rating`, dan `deskripsi`. Untuk mempermudah *data monitoring*, distribusi data yang hilang ini dipetakan secara visual menggunakan grafik batang (*Bar Chart*).

### 3. Pembersihan Data (Data Cleaning)
Untuk mempertahankan integritas volume data tanpa harus menghapus baris transaksi, diterapkan strategi **Imputasi Data**:
* **Atribut Numerik (`harga`, `jumlah`, `rating`):** Nilai kosong diisi secara otomatis menggunakan nilai rata-rata (*mean*) dari masing-masing kolom untuk meminimalkan bias statistik.
* **Atribut Teks (`deskripsi`):** Nilai kosong diisi menggunakan *placeholder* teks konstan `"tidak ada deskripsi"` agar format data tetap konsisten.

### 4. Transformasi & Integrasi Data (Feature Engineering)
Untuk memperkaya informasi yang dapat ditarik dari dataset, dilakukan rekayasa fitur baru:
* **Fitur `total_harga`:** Kolom kalkulasi baru yang didapatkan dari hasil perkalian otomatis antara harga produk dan kuantitas jumlah.
* **Ekstraksi Waktu (`bulan`):** Mengonversi kolom tanggal transaksi menjadi tipe data *datetime* untuk mengekstrak komponen bulan spesifik.
* **Normalisasi Skala:** Menggunakan *MinMaxScaler* untuk mentransformasikan rentang angka pada kolom harga dan jumlah menjadi skala universal **0 sampai 1** agar distribusi data lebih seimbang.
* **Pelabelan Kategori:** Membuat fungsi logika kustom untuk mengubah skor rating angka menjadi label teks kategorikal (*Buruk*, *Cukup*, *Baik*).

### 5. Pemrosesan Teks (Text Processing)
Pada kolom deskripsi, diterapkan teknik NLP dasar berupa *Tokenizing* (memecah kalimat menjadi potongan kata tunggal) dan *Filtering* (menghapus kata hubung/kata umum yang tidak esensial). Proyek ini sukses mengekstrak top 5 kata yang paling sering muncul dari ulasan produk untuk analisis sentimen konsumen.

---

## 📁 Struktur Berkas di Repositori
* `data_penjualan_latihan.csv` : Dataset transaksi penjualan mentah (*raw source data*).
* `Untitled.ipynb` : Jupyter Notebook berisi seluruh arsitektur kode dan output eksekusi program.
* `README.md` : Panduan dokumentasi portofolio proyek ini.

---

## 🧠 Kesimpulan Eksekutif
Melalui proyek ini, data mentah yang semula kotor dan memiliki banyak baris kosong berhasil dibersihkan total menjadi **0 missing values**. Tahapan *Data Preprocessing* terbukti menjadi fondasi paling krusial bagi seorang *Data Professional* untuk menjamin data yang dianalisis memiliki kualitas tinggi, valid, dan mampu menghasilkan keputusan bisnis yang akurat.
