# Analisis Kinerja Penjualan Online Retail

**Proyek portofolio Data Analyst | Python (Pandas) · Power BI**

Proyek ini mengolah data transaksi ritel daring untuk menyiapkan dataset yang lebih konsisten serta menyajikan hasilnya melalui dashboard Power BI. Fokus utamanya adalah **pemeriksaan kualitas data, pembersihan transaksi, dan visualisasi performa penjualan**.

📊 **[Lihat dashboard (PDF)](Porto-Online-Retail.pdf)** · 💻 **[Notebook Python](online-retail.ipynb)** · 📈 **[File Power BI](Porto%20Online%20Retail.pbix)** · 📝 **[Baca artikel analisis di Medium](https://medium.com/@MuharromGanesha/analisis-online-retail-sales-performance-2010-2011-4ec8da1a3637)**

## 1. Gambaran Proyek

Data transaksi penjualan dapat memuat informasi pelanggan yang tidak lengkap, deskripsi produk yang kosong, transaksi dengan harga tidak valid, serta retur atau pembatalan. Jika tidak ditangani, hal-hal tersebut dapat memengaruhi penghitungan dan interpretasi metrik penjualan.

Pada proyek ini saya:

1. Memeriksa struktur dataset serta nilai kosong (*missing values*).
2. Mendokumentasikan dan menangani nilai kosong menggunakan Python/Pandas.
3. Memfilter transaksi berdasarkan harga, kuantitas, dan penanda invoice retur/pembatalan.
4. Mengekspor data hasil pembersihan untuk proses analisis berikutnya.
5. Membuat dashboard Power BI agar data lebih mudah dieksplorasi.

Untuk uraian pembahasan analisis penjualan yang lebih panjang, lihat **[artikel Medium: Analisis Online Retail Sales Performance 2010–2011](https://medium.com/@MuharromGanesha/analisis-online-retail-sales-performance-2010-2011-4ec8da1a3637)**.

## 2. Dataset

Dataset proyek diperoleh dari **Kaggle**. Notebook membaca berkas `online_retail_II.csv`; arsip dataset disediakan dalam repository sebagai [`Dataset.rar`](Dataset.rar).

Berdasarkan output yang tersimpan di notebook:

| Keterangan | Jumlah |
| --- | ---: |
| Baris data awal | 1.067.371 |
| Kolom | 8 |
| Baris setelah proses filter | 1.061.164 |
| Baris yang terbuang setelah filter | 6.207 |

**Kolom data:** `Invoice`, `StockCode`, `Description`, `Quantity`, `InvoiceDate`, `Price`, `Customer ID`, dan `Country`.

### Pemeriksaan nilai kosong

| Kolom | Nilai kosong sebelum pembersihan | Penanganan di notebook |
| --- | ---: | --- |
| `Customer ID` | 243.007 | Mengisi dengan `Guest` |
| `Description` | 4.382 | Mengisi dengan `Unknown Product` |

Enam kolom lainnya tidak memiliki nilai kosong pada pemeriksaan awal `isna()` di notebook.

## 3. Teknologi

- **Python dan Pandas** — membaca data, melakukan pemeriksaan, pembersihan, filter, dan ekspor CSV.
- **Google Colab / Jupyter Notebook** — lingkungan untuk menjalankan proses pengolahan data.
- **Microsoft Power BI** — menyusun dashboard serta visualisasi hasil analisis.

## 4. Alur Pengolahan Data

Langkah yang terdokumentasi pada [`online-retail.ipynb`](online-retail.ipynb):

1. **Memuat dataset CSV** ke DataFrame Pandas dan memeriksa struktur data menggunakan `df.info()`.
2. **Mengidentifikasi nilai kosong** menggunakan `df.isna().sum()`, lalu menyimpan baris yang memiliki nilai kosong ke `data_null_log.csv`.
3. **Mengisi nilai kosong** pada `Customer ID` dengan `Guest` dan `Description` dengan `Unknown Product`.
4. **Memfilter harga** dengan mempertahankan data yang memiliki `Price > 0`.
5. **Menangani kuantitas dan retur:** mempertahankan transaksi dengan `Quantity > 0`, serta transaksi berkuantitas negatif hanya apabila nilai `Invoice` diawali huruf `C` (aturan yang digunakan pada notebook).
6. **Mengekspor hasil pembersihan** menjadi `online_retail_cleaned.csv`.

Hasil filter pada output notebook menunjukkan **1.061.164 baris data** tersisa.

## 5. Hasil yang Terdokumentasi

Temuan berikut dapat diverifikasi dari **output notebook**, bukan asumsi mengenai isi dashboard:

- Data awal terdiri atas **lebih dari satu juta baris transaksi**.
- Kolom `Customer ID` memiliki **243.007 nilai kosong**.
- Kolom `Description` memiliki **4.382 nilai kosong**.
- Proses filter harga dan kuantitas mengurangi **6.207 baris**.
- Data yang sudah dibersihkan diekspor sebagai CSV untuk proses pelaporan.

Analisis bisnis terkait tren penjualan, produk, atau negara dapat ditinjau melalui [dashboard PDF](Porto-Online-Retail.pdf) dan [artikel Medium](https://medium.com/@MuharromGanesha/analisis-online-retail-sales-performance-2010-2011-4ec8da1a3637). README ini tidak menyatakan peringkat atau angka penjualan yang belum diverifikasi secara langsung.

## 6. Dashboard dan Artikel

| Hasil proyek | Tautan |
| --- | --- |
| Dashboard Power BI yang dapat diedit | [Porto Online Retail.pbix](Porto%20Online%20Retail.pbix) |
| Dashboard versi PDF | [Porto-Online-Retail.pdf](Porto-Online-Retail.pdf) |
| Notebook pengolahan data | [online-retail.ipynb](online-retail.ipynb) |
| Artikel dan penjelasan analisis | [Analisis Online Retail Sales Performance 2010–2011 — Medium](https://medium.com/@MuharromGanesha/analisis-online-retail-sales-performance-2010-2011-4ec8da1a3637) |

## 7. Struktur Repository

```text
Online-Retail-Sales-Analysis/
├── Dataset.rar                  # Arsip dataset
├── online-retail.ipynb          # Notebook pembersihan data
├── Porto Online Retail.pbix     # Dashboard Power BI
├── Porto-Online-Retail.pdf      # Hasil ekspor dashboard
└── README.md                    # Dokumentasi proyek
```

## 8. Cara Menjalankan dan Melihat Proyek

**Notebook Python**

1. Unduh atau *clone* repository ini.
2. Ekstrak `Dataset.rar` dan temukan file `online_retail_II.csv`.
3. Buka `online-retail.ipynb` melalui Google Colab atau Jupyter Notebook.
4. Jika diperlukan, instal Pandas dengan `pip install pandas`.
5. **Sesuaikan path dataset dan output** di notebook. Kode awal menggunakan direktori Google Drive pribadi sehingga tidak langsung cocok di komputer lain.
6. Jalankan sel secara berurutan untuk menghasilkan file log nilai kosong dan CSV hasil pembersihan.

**Dashboard Power BI**

1. Buka `Porto Online Retail.pbix` menggunakan Power BI Desktop.
2. Jika sumber data tidak ditemukan, perbarui pengaturan koneksi file ke CSV lokal yang sesuai.
3. Untuk melihat hasil secara cepat tanpa Power BI, buka `Porto-Online-Retail.pdf`.

## 9. Catatan Interpretasi

- Nilai `Guest` adalah penanda **ID pelanggan yang tidak diketahui**, bukan satu pelanggan nyata.
- Baris kuantitas negatif yang memenuhi aturan invoice dipertahankan; hal ini perlu diperhatikan dalam penghitungan penjualan kotor atau bersih.
- Angka yang berasal dari proses *data cleaning* tidak otomatis sama dengan hasil agregasi yang ditampilkan di dashboard.

## Penulis

**Muharrom Ganesha**  
[GitHub](https://github.com/muharromganesha) · [Portofolio](https://muharromganesha.vercel.app) · [Artikel Medium](https://medium.com/@MuharromGanesha/analisis-online-retail-sales-performance-2010-2011-4ec8da1a3637)
