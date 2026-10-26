# Analisis Deskriptif Dataset Film Global Menggunakan Apache Spark

Dokumen ini berisi gambaran umum proyek analisis data besar (*Big Data*) yang melakukan analisis deskriptif terhadap data perfilman global dari platform **The Movie Database (TMDB)** (`mymoviedb.csv`). Proyek ini memanfaatkan kerangka kerja **Apache Spark (PySpark)** untuk memproses, memanipulasi, dan menganalisis dataset berskala besar yang memiliki struktur kompleks secara efisien.

---

## 📌 Isi dan Struktur Proyek

Notebook analisis terbagi menjadi beberapa tahapan utama dalam alur proses data (*Data Pipeline/ETL*):

### 1. Latar Belakang & Pertanyaan Bisnis
Menjelaskan tantangan dalam menganalisis data perfilman (seperti struktur *multi-genre*) serta merumuskan 5 pertanyaan bisnis utama yang mencakup:
* Analisis kualitas & kuantitas genre film.
* Tren perkembangan jumlah rilis film tahunan.
* Pola musiman (perbandingan rilis bulanan vs. tingkat popularitas).
* Korelasi antara popularitas dan *rating* film.
* Performa pasar film berbasis bahasa non-Inggris.

### 2. Deskripsi & Eksplorasi Dataset (`mymoviedb.csv`)
* Mengulas dataset yang mencakup **9.827 baris data** dan **9 kolom utama** (rentang waktu rilis tahun 1902–2024).
* Memuat data ke dalam `SparkSession` dengan menangani format teks khusus (seperti sinopsis/overview) menggunakan opsi `multiLine` dan `escape`.

### 3. Pembersihan Data (*Data Cleansing*)
* Menghapus data duplikat menggunakan fungsi `dropDuplicates`.
* Mengubah tipe data (*casting*) pada kolom tanggal (`Release_Date`) dan kolom numerik (`Popularity`, `Vote_Count`, `Vote_Average`).
* Menghapus kolom yang tidak relevan (`Overview`, `Poster_Url`) serta membuang baris dengan nilai kosong (*null values*).

### 4. Transformasi & Pengayaan Data (*Enrichment*)
* Ekstraksi tanggal rilis menjadi fitur temporal baru: tahun (`Year`) dan bulan (`Month`).
* Memisahkan struktur *multi-genre* menjadi baris genre tunggal (`Single_Genre`) menggunakan kombinasi fungsi `split` dan `explode`.
* Optimasi efisiensi pemrosesan dengan teknik **Caching** pada RAM Spark serta menyimpan data bersih ke format **CSV** dan **Parquet**.

### 5. Analisis Deskriptif & Visualisasi Data
* Menggabungkan hasil agregasi PySpark dengan pustaka visualisasi Python (**Matplotlib** dan **Seaborn**) untuk menjawab seluruh pertanyaan bisnis.

---

## 💻 Teknologi yang Digunakan

| Komponen | Teknologi / Pustaka |
| :--- | :--- |
| **Bahasa Pemrograman** | Python 3 |
| **Framework Big Data** | Apache Spark (`PySpark`) |
| **Pengolahan & Visualisasi** | Pandas, Matplotlib, Seaborn |
| **Format Storage Output** | CSV & Apache Parquet |