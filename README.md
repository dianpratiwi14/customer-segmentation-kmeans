# Optimalisasi Strategi Pemasaran Melalui Segmentasi Pelanggan Menggunakan Metode K-Means Clustering

Laporan Ujian Akhir Semester — Pembelajaran Mesin (Praktikum) I3
Kelompok 13

**Disusun oleh:**

- Dian Pratiwi
- Nova Siska Puspitasari
- Naufaldo Rafi Brahmana

## Deskripsi Project

Project ini bertujuan mengelompokkan (segmentasi) pelanggan sebuah retail online yang berbasis di Inggris, menggunakan metode **K-Means Clustering**. Segmentasi ini dilakukan untuk memahami pola pembelian pelanggan berdasarkan variabel `Quantity` (jumlah barang yang dibeli) dan `UnitPrice` (harga satuan barang), sehingga hasilnya dapat dimanfaatkan untuk mengoptimalkan strategi pemasaran.

### Rumusan Masalah

1. Bagaimana klasifikasi tipe pembelian dan jumlah kunjungan tahunan seorang konsumen berdasarkan data pembelian pertamanya?
2. Bagaimana evaluasi kinerja klasifikasi tersebut berdasarkan data yang digunakan?

### Tujuan

1. Mengembangkan klasifikasi untuk memprediksi tipe pembelian dan jumlah kunjungan tahunan seorang konsumen di platform e-commerce.
2. Mengevaluasi kinerja klasifikasi tersebut berdasarkan data yang digunakan.

## Dataset

Dataset yang digunakan adalah **"E-Commerce Data"**, yang tersedia di [Kaggle](https://www.kaggle.com/datasets/carrie1/ecommerce-data). Dataset ini berisi transaksi yang dilakukan oleh sekitar 4.000 pelanggan pada sebuah ritel online _non-toko_ yang terdaftar dan berbasis di Inggris.

- **Sumber**: [Kaggle — E-Commerce Data](https://www.kaggle.com/datasets/carrie1/ecommerce-data)
- **Jumlah data**: 541.910 baris, 8 kolom fitur
- **Jumlah pelanggan**: ± 4.000 pelanggan
- **Rentang transaksi**: 1 Desember 2010 – 9 Desember 2011

## Metodologi

Alur pengerjaan project ini terdiri dari beberapa tahap:

1. **Load Data**
2. **Pre-Processing**: Pengecekan dan penanganan _missing value_ menggunakan `dropna()`
3. **Cleaning Data**: Penanganan outlier pada fitur `Quantity` dan `UnitPrice` dengan menggantikan nilai ekstrem menggunakan mean (metode IQR). Kolom `CustomerID` tidak diberi perlakuan outlier karena berfungsi sebagai identitas, bukan nilai numerik.
4. **Analisa Data**: Eksplorasi data melalui:
   - Density plot per fitur
   - Plot relasi antar fitur (`Quantity`, `UnitPrice`, `CustomerID`)
   - Visualisasi sebaran `Quantity` dan `UnitPrice` berdasarkan negara
5. **Penentuan Jumlah Cluster**: Menggunakan _Elbow Method_
6. **K-Means Clustering**
7. **Evaluasi Model**: Menggunakan **Silhouette Score**.

## Hasil

- **Jumlah cluster optimal**: 4 (berdasarkan titik elbow pada Elbow Method)
- **Silhouette Score**: 0.543, menunjukkan hasil clustering dengan separasi yang cukup baik antar cluster
- Cluster dengan `Quantity` dan `UnitPrice` tinggi mengindikasikan pelanggan dengan tipe pembelian besar dan kemungkinan frekuensi kunjungan lebih sering.
- Cluster dengan `Quantity` dan `UnitPrice` rendah mengindikasikan pelanggan dengan tipe pembelian kecil dan kemungkinan frekuensi kunjungan lebih jarang.

## Struktur Project

```
.
├── CustomerSegmentation.ipynb   # Notebook utama: load data, preprocessing, clustering, evaluasi
├── data_customer.xlsx           # Dataset transaksi pelanggan
└── README.md
```

## Cara Menjalankan

1. Clone repository ini
2. Install dependency yang dibutuhkan:
   ```bash
   pip install numpy pandas matplotlib seaborn scikit-learn openpyxl
   ```
3. Buka `CustomerSegmentation.ipynb` di Jupyter Notebook / JupyterLab / VS Code
4. Jalankan seluruh cell secara berurutan (Run All)

## Tools & Library

- Python 3.11
- pandas, numpy — manipulasi data
- matplotlib, seaborn — visualisasi data
- scikit-learn (`KMeans`, `silhouette_score`) — clustering & evaluasi model
