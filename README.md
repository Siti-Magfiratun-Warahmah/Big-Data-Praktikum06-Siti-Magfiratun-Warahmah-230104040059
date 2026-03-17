# PRAKTIKUM 4 – Streaming Processing & Real-Time Dashboard

**Proyek:** BIGDATA-SPARK-230104040059

Program ini dibuat untuk memenuhi instruksi **Praktikum 4 Mata Kuliah Teknologi Big Data**. Praktikum ini berfokus pada implementasi **Streaming Data Processing dan Real-Time Analytics Dashboard** menggunakan **Apache Spark Structured Streaming** dan **Streamlit**.

Pipeline yang dibangun mensimulasikan sistem **streaming analytics seperti yang digunakan pada industri teknologi modern**, dimana data transaksi diproses secara real-time dan divisualisasikan melalui dashboard interaktif.

---

# 👩‍🎓 Identitas Mahasiswa

| Keterangan | Informasi |
|---|---|
| Mata Kuliah | Teknologi Big Data |
| Dosen Pengampu | Muhayat, S.Ag., M.IT |
| Praktikum | Praktikum 4 – Streaming Processing & Real-Time Dashboard |
| Nama Mahasiswa | Siti Magfiratun Warahmah |
| NIM | 230104040059 |
| Kelas | TI23B |

---

# 🚀 Deskripsi Program

Program ini merupakan implementasi **streaming data pipeline** yang digunakan untuk memproses data transaksi secara real-time.

Pada praktikum ini dilakukan simulasi **event streaming** menggunakan generator transaksi yang menghasilkan data transaksi secara berkala. Data tersebut kemudian diproses menggunakan **Spark Structured Streaming** dan disimpan dalam **Parquet Data Lake** sebelum ditampilkan pada dashboard analitik real-time.

Pipeline streaming analytics yang dibangun terdiri dari beberapa komponen utama:

✔ Transaction Generator untuk menghasilkan event transaksi  
✔ Spark Structured Streaming untuk memproses data streaming  
✔ Parquet Data Lake sebagai storage layer  
✔ Streamlit Dashboard untuk visualisasi real-time  

Dataset transaksi akan terus bertambah selama sistem berjalan dan dashboard akan menampilkan analitik secara otomatis setiap beberapa detik.

---

# 🏗️ Arsitektur Pipeline

Pipeline streaming analytics pada praktikum ini menggunakan arsitektur berikut:

```
Transaction Generator
        │
        ▼
stream_data/ (JSON events)
        │
        ▼
Spark Structured Streaming
        │
        ▼
Parquet Data Lake
data/serving/stream
        │
        ▼
Real-Time Dashboard (Streamlit)
```

Penjelasan alur data:

1. **Transaction Generator** menghasilkan file JSON transaksi secara berkala.
2. File transaksi disimpan pada folder **stream_data**.
3. **Spark Structured Streaming** membaca file tersebut sebagai data streaming.
4. Hasil pemrosesan streaming disimpan dalam format **Parquet** pada data lake.
5. **Streamlit Dashboard** membaca data tersebut dan menampilkan analitik secara real-time.

---

# 🛠️ Teknologi yang Digunakan

Beberapa teknologi yang digunakan dalam implementasi pipeline ini antara lain:

- Python 3.12
- Apache Spark (PySpark)
- Spark Structured Streaming
- Parquet Data Lake
- Streamlit
- Pandas
- Visual Studio Code
- WSL Ubuntu
- Bash CLI

Teknologi ini digunakan untuk membangun sistem **real-time analytics pipeline** yang mampu memproses data streaming secara kontinu.

---

# 📊 Dataset Streaming

Dataset pada praktikum ini tidak berasal dari file statis, tetapi dihasilkan secara dinamis oleh **transaction generator**.

Generator akan membuat file transaksi JSON secara berkala dengan struktur data seperti berikut:

```
{
  "user_id": 120,
  "product": "Laptop",
  "price": 1500,
  "city": "Jakarta",
  "timestamp": "2026-03-12 10:22:10"
}
```

File transaksi tersebut akan disimpan pada folder:

```
stream_data/
```

Spark Structured Streaming kemudian membaca file tersebut sebagai **data streaming event**.

---

# ⚙️ Cara Kerja Program

Pipeline streaming analytics pada praktikum ini berjalan melalui beberapa tahapan utama.

---

## 1️⃣ Transaction Generator

Program **transaction_generator.py** digunakan untuk mensimulasikan event streaming dengan menghasilkan file transaksi setiap beberapa detik.

File transaksi akan disimpan pada folder:

```
stream_data/
```

Setiap transaksi berisi informasi:

- user_id
- product
- price
- city
- timestamp

---

## 2️⃣ Streaming Processing (Spark Structured Streaming)

Script **streaming_layer.py** bertugas membaca file JSON dari folder stream_data sebagai data streaming.

Spark Structured Streaming kemudian memproses data tersebut menggunakan konsep **micro-batch processing**.

Konfigurasi streaming yang digunakan antara lain:

```
readStream()
writeStream()
trigger(processingTime="5 seconds")
```

Data streaming yang telah diproses akan disimpan dalam format **Parquet** pada folder:

```
data/serving/stream
```

---

## 3️⃣ Serving Layer (Parquet Data Lake)

Serving layer berfungsi sebagai penyimpanan data hasil pemrosesan streaming yang siap digunakan oleh aplikasi atau dashboard.

Lokasi penyimpanan:

```
data/serving/stream
```

Folder ini akan berisi file Parquet seperti:

```
part-00000.snappy.parquet
part-00001.snappy.parquet
part-00002.snappy.parquet
```

File tersebut akan terus bertambah selama pipeline streaming berjalan.

---

## 4️⃣ Real-Time Dashboard

Dashboard analitik dibangun menggunakan **Streamlit**.

Dashboard akan membaca data Parquet dari serving layer dan menampilkan berbagai metrik analitik secara real-time.

Dashboard menampilkan beberapa komponen utama:

### Key Metrics

- Total Transactions
- Total Revenue
- Average Transaction
- Cities

### Visualisasi Grafik

- Revenue per City
- Top Products
- Revenue Trend

### Live Transactions

Dashboard juga menampilkan tabel transaksi terbaru yang masuk ke dalam sistem.

Data pada dashboard akan diperbarui secara otomatis setiap beberapa detik ketika data streaming baru diproses.

---

# 📂 Struktur Folder Project

Struktur project pada praktikum ini adalah sebagai berikut:

```
BIGDATA-PROJECT
│
├── stream_data
│
├── data
│   └── serving
│       └── stream
│
├── scripts
│   ├── streaming_layer.py
│   └── transaction_generator.py
│
├── dashboard
│   └── dashboard_streamlit.py
│
├── logs
│
└── README.md
```

Penjelasan:

- **stream_data** → folder penyimpanan event transaksi JSON  
- **data/serving/stream** → hasil pemrosesan streaming dalam format Parquet  
- **scripts** → script pipeline streaming  
- **dashboard** → aplikasi dashboard Streamlit  

---

# 📊 Real-Time Analytics

Dashboard real-time menampilkan beberapa analitik penting dari transaksi yang masuk ke dalam sistem.

Analitik yang ditampilkan meliputi:

- Total jumlah transaksi
- Total revenue
- Average transaction value
- Jumlah kota yang melakukan transaksi
- Revenue berdasarkan kota
- Produk yang paling banyak menghasilkan pendapatan
- Tren revenue dari waktu ke waktu
- Tabel transaksi terbaru

Dashboard ini memungkinkan pengguna untuk **memantau aktivitas transaksi secara langsung** dan memperoleh insight bisnis secara cepat.

---

# ▶️ Cara Menjalankan Program

Pastikan semua dependency telah diinstall terlebih dahulu.

Install library yang diperlukan:

```
pip install pyspark streamlit pandas pyarrow
```

Pipeline dijalankan menggunakan **3 terminal berbeda**.

---

### Terminal 1 — Spark Streaming

Menjalankan pipeline streaming Spark.

```
spark-submit scripts/streaming_layer.py
```

---

### Terminal 2 — Transaction Generator

Menjalankan generator transaksi.

```
python scripts/transaction_generator.py
```

---

### Terminal 3 — Streamlit Dashboard

Menjalankan dashboard analitik real-time.

```
python -m streamlit run dashboard/dashboard_streamlit.py
```

---

# 🌐 Akses Dashboard

Setelah dashboard dijalankan, buka browser dan akses alamat berikut:

```
http://localhost:8501
```

Dashboard akan menampilkan **analitik transaksi secara real-time**.

---

# 🎯 Kesimpulan

Praktikum ini memperkenalkan konsep **stream processing dalam sistem Big Data** dengan membangun pipeline streaming analytics sederhana menggunakan Apache Spark Structured Streaming.

Data transaksi dihasilkan secara kontinu oleh transaction generator dan diproses secara real-time oleh Spark sebelum disimpan dalam format Parquet pada data lake. Data tersebut kemudian divisualisasikan menggunakan dashboard Streamlit yang menampilkan berbagai metrik analitik seperti total transaksi, revenue per city, top products, dan revenue trend.

Melalui praktikum ini dapat dipahami bagaimana sistem Big Data modern memproses data streaming dan menyajikan analitik secara real-time untuk mendukung proses pengambilan keputusan berbasis data.

---

# 📦 Repository

Source code praktikum ini tersedia pada repository GitHub berikut:

```
https://github.com/Siti-Magfiratun-Warahmah/Big-Data-Praktikum04-Siti-Magfiratun-Warahmah-230104040059
```

---