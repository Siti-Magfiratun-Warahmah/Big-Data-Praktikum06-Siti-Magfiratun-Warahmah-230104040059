# PRAKTIKUM 6 – Real-Time Analytics & Visualisasi Data Skala Besar

**Proyek:** BIGDATA-SPARK-230104040059

Program ini dibuat untuk memenuhi instruksi **Praktikum 6 Mata Kuliah Teknologi Big Data**. Praktikum ini berfokus pada pengembangan **visualisasi data real-time dalam skala besar (large-scale visualization)** serta optimasi dashboard menggunakan teknik seperti window aggregation, downsampling, dan incremental visualization.

Pipeline yang dibangun merupakan pengembangan dari praktikum sebelumnya, dengan fokus pada peningkatan performa visualisasi dan kemampuan sistem dalam menangani data streaming dalam jumlah besar.

---

# 👩‍🎓 Identitas Mahasiswa

| Keterangan     | Informasi                                            |
| -------------- | ---------------------------------------------------- |
| Mata Kuliah    | Teknologi Big Data                                   |
| Dosen Pengampu | Muhayat, S.Ag., M.IT                                 |
| Praktikum      | Praktikum 6 – Real-Time Analytics & Visualisasi Data |
| Nama Mahasiswa | Siti Magfiratun Warahmah                             |
| NIM            | 230104040059                                         |
| Kelas          | TI23B                                                |

---

# 🚀 Deskripsi Program

Program ini merupakan implementasi sistem **Real-Time Analytics berbasis Big Data** pada domain Smart Transportation. Sistem ini mampu memproses data perjalanan secara streaming dan menampilkannya dalam bentuk dashboard interaktif secara real-time.

Fokus utama pada praktikum ini adalah bagaimana menangani **data dalam skala besar** agar tetap dapat divisualisasikan dengan cepat dan responsif. Oleh karena itu, diterapkan berbagai teknik optimasi seperti window aggregation, downsampling, dan incremental visualization.

Sistem ini tidak hanya menampilkan data, tetapi juga menghasilkan insight secara langsung sehingga dapat digunakan sebagai **Decision-Oriented System**.

---

# 🏗️ Arsitektur Pipeline

Pipeline Big Data Analytics pada praktikum ini menggunakan arsitektur berikut:

```
Trip Generator (JSON)
        │
        ▼
stream_data/transportation
        │
        ▼
Spark Structured Streaming
        │
        ▼
Parquet Data Lake (Serving Layer)
        │
        ▼
Aggregation Layer (Windowing)
        │
        ▼
Visualization Engine (Streamlit)
        │
        ▼
Interactive Dashboard (Real-Time & Large Scale)
```

Penjelasan alur data:

1. **Trip Generator** menghasilkan data perjalanan secara berkala dalam format JSON.
2. Data dibaca oleh **Spark Structured Streaming** sebagai data streaming.
3. Data diproses secara real-time dan disimpan dalam format **Parquet**.
4. Data kemudian melalui proses **window aggregation** untuk penyederhanaan.
5. Hasil agregasi divisualisasikan menggunakan **Streamlit**.
6. Dashboard menampilkan data secara real-time dan tetap responsif.

---

# 🛠️ Teknologi yang Digunakan

* Python 3.12
* Apache Spark (PySpark)
* Spark Structured Streaming
* Parquet Data Lake
* Streamlit
* Pandas
* Visual Studio Code
* WSL Ubuntu
* Bash CLI

---

# 📊 Dataset Streaming

Dataset dihasilkan secara dinamis oleh **trip generator**.

Contoh data:

```
{
  "trip_id": "TRX123",
  "vehicle_type": "Car",
  "location": "Jakarta",
  "distance": 12.5,
  "fare": 45000,
  "timestamp": "2026-03-31 17:45:20"
}
```

---

# ⚙️ Cara Kerja Program

## 1️⃣ Trip Generator

Menghasilkan data perjalanan secara kontinu dalam format JSON.

---

## 2️⃣ Streaming Processing

Menggunakan Spark Structured Streaming untuk membaca dan memproses data secara real-time.

---

## 3️⃣ Aggregation Layer

Menggunakan teknik **window aggregation** untuk mengelompokkan data berdasarkan waktu agar lebih ringan untuk divisualisasikan.

---

## 4️⃣ Dashboard & Visualisasi

Dashboard dibangun menggunakan Streamlit dan menampilkan:

### Visualisasi

* Real-Time Traffic (Windowed)
* Vehicle Distribution
* Mobility Trend
* Fare per Location

### Data

* Live Trip Data (terbatas)

Dashboard diperbarui secara otomatis secara real-time.

---

# ⚡ Optimasi Sistem

Untuk menjaga performa pada data skala besar, digunakan:

* Window Aggregation
* Downsampling
* Incremental Visualization
* Pembatasan data (tail data)
* Pengaturan refresh interval

Teknik ini membuat dashboard tetap cepat, ringan, dan tidak lag.

---

# 📂 Struktur Folder Project

```
BIGDATA-PROJECT
│
├── scripts/
│   └── transportation/
│
├── analytics/
│
├── alerts/
│
├── dashboard/
│
├── data/
│   └── serving/
│       └── transportation/
│
└── README.md
```

---

# ▶️ Cara Menjalankan Program

Install dependency:

```
pip install pyspark streamlit pandas pyarrow
```

Jalankan 3 terminal:

### Terminal 1 — Spark Streaming

```
spark-submit scripts/transportation/streaming_trip_layer.py
```

### Terminal 2 — Trip Generator

```
python scripts/transportation/trip_generator.py
```

### Terminal 3 — Dashboard

```
streamlit run dashboard/dashboard_transportation.py
```

---

# 🌐 Akses Dashboard

Buka di browser:

```
http://localhost:8501
```

---

# 🎯 Kesimpulan

Praktikum ini berhasil mengimplementasikan sistem **Real-Time Analytics dan Visualisasi Data Skala Besar** menggunakan Spark Structured Streaming dan Streamlit. Dengan penerapan teknik optimasi seperti window aggregation dan downsampling, sistem mampu menampilkan data secara real-time dengan performa yang tetap stabil. Sistem ini juga berperan sebagai decision-oriented system yang dapat mendukung pengambilan keputusan berbasis data.

---

# 📦 Repository

```
https://github.com/Siti-Magfiratun-Warahmah/Big-Data-Praktikum06-Siti-Magfiratun-Warahmah-230104040059
```
