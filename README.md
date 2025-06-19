# Analisis Clustering Provinsi di Indonesia Berdasarkan Tingkat Pengangguran Terbuka (TPT)

Repositori ini berisi notebook analisis untuk mengelompokkan (clustering) provinsi-provinsi di Indonesia berdasarkan pola Tingkat Pengangguran Terbuka (TPT) dari tahun 2021 hingga 2023 menggunakan algoritma K-Means.

## 📝 Deskripsi Proyek

Tujuan dari analisis ini adalah untuk mengidentifikasi kelompok-kelompok provinsi yang memiliki karakteristik serupa dalam hal tingkat pengangguran selama tiga tahun terakhir. Dengan menggunakan K-Means, kita dapat mengungkap struktur tersembunyi dalam data dan memahami polarisasi kondisi pasar tenaga kerja di Indonesia.

### Dataset
* **Nama:** Tingkat Pengangguran Terbuka Berdasarkan Provinsi di Indonesia
* **Sumber:** [Open Data Jabar](https://opendata.jabarprov.go.id/id/dataset/tingkat-pengangguran-terbuka-berdasarkan-provinsi--di-indonesia)
* **Fokus Analisis:** Data TPT tahun **2021, 2022, dan 2023**.

---

## ⚙️ Metodologi Analisis

Analisis ini dilakukan melalui beberapa tahapan standar dalam proyek Data Science:

1.  **Data Loading & Cleaning:** Memuat dataset, membersihkan nama kolom, dan menghapus data yang tidak relevan.
2.  **Data Preprocessing:**
    * Melakukan `pivot_table` untuk mengubah struktur data agar setiap provinsi menjadi satu baris observasi dengan fitur TPT per tahun.
    * Menangani nilai yang hilang (*missing values*) dengan menghapus baris terkait.
    * Melakukan **Feature Scaling** menggunakan `StandardScaler` untuk menormalisasi data, yang merupakan langkah penting untuk algoritma K-Means.
3.  **Modeling (K-Means Clustering):**
    * Menggunakan **Elbow Method** untuk menentukan jumlah cluster (k) yang optimal.
    * Melatih model K-Means dengan nilai `k` yang telah ditentukan (k=2).
4.  **Evaluation & Visualization:**
    * Melakukan **Cluster Profiling** dengan menghitung nilai rata-rata TPT untuk setiap cluster guna memahami karakteristiknya.
    * Memvisualisasikan hasil cluster dalam ruang 2D menggunakan **Principal Component Analysis (PCA)**.

---

## 📊 Hasil Analisis

### 1. Penentuan Jumlah Cluster
Berdasarkan **Elbow Method**, jumlah cluster yang paling optimal adalah **2**. Grafik di bawah menunjukkan "titik siku" yang jelas pada `k=2`, di mana penambahan cluster selanjutnya tidak memberikan penurunan *inertia* yang signifikan.

![Elbow Method Plot](img/elbow_plot.png)
*Catatan: Ganti `img/elbow_plot.png` dengan path gambar plot siku Anda.*

### 2. Profil Cluster
Model berhasil mengidentifikasi dua kelompok provinsi dengan karakteristik yang sangat berbeda:

| Cluster | Nama Cluster  | Karakteristik Utama                                                 | Rata-rata TPT (2021-2023) | Jumlah Provinsi |
| :------ | :------------ | :------------------------------------------------------------------ | :------------------------ | :-------------- |
| **0** | **TPT Tinggi** | Provinsi dengan tingkat pengangguran yang secara konsisten tinggi.    | **~6.0% - 7.2%** | 14 Provinsi     |
| **1** | **TPT Rendah** | Provinsi dengan tingkat pengangguran yang relatif lebih rendah & stabil. | **~3.6% - 4.3%** | 20 Provinsi     |

### 3. Visualisasi Hasil Clustering (PCA)
Visualisasi PCA secara efektif menunjukkan bagaimana kedua cluster ini terpisah dengan baik dalam ruang fitur yang telah direduksi.

![PCA Cluster Visualization](img/pca_visualization.png)
*Catatan: Ganti `img/pca_visualization.png` dengan path gambar visualisasi PCA Anda.*

### 4. Daftar Provinsi per Cluster

**--- Cluster: TPT Tinggi (14 Provinsi) ---**
ACEH, BANTEN, DKI JAKARTA, JAWA BARAT, JAWA TENGAH, JAWA TIMUR, KALIMANTAN BARAT, KALIMANTAN TIMUR, KEPULAUAN RIAU, MALUKU, PAPUA BARAT, SULAWESI UTARA, SUMATERA BARAT, SUMATERA UTARA

**--- Cluster: TPT Rendah (20 Provinsi) ---**
BALI, BENGKULU, DI YOGYAKARTA, GORONTALO, JAMBI, KALIMANTAN SELATAN, KALIMANTAN TENGAH, KALIMANTAN UTARA, KEPULAUAN BANGKA BELITUNG, LAMPUNG, MALUKU UTARA, NUSA TENGGARA BARAT, NUSA TENGGARA TIMUR, PAPUA, RIAU, SULAWESI BARAT, SULAWESI SELATAN, SULAWESI TENGAH, SULAWESI TENGGARA, SUMATERA SELATAN

---

## 🚀 Cara Menjalankan Proyek Ini

Untuk mereproduksi analisis ini, ikuti langkah-langkah berikut:

**1. Prasyarat**
* Python 3.x
* PIP (Package Installer for Python)

**2. Kloning Repositori**
```bash
git clone [https://github.com/Bagusdarmawan11/analisis-clustering-tpt-indonesia.git](https://github.com/Bagusdarmawan11/analisis-clustering-tpt-indonesia.git)
cd analisis-clustering-tpt-indonesia
```

**3. Instalasi Dependensi**
Disarankan untuk menggunakan *virtual environment*.
```bash
pip install -r requirements.txt
```

**4. Menjalankan Notebook**
Jalankan Jupyter Notebook atau Jupyter Lab dan buka file `Analisis Clustering Provinsi di Indonesia Berdasarkan Tingkat Pengangguran Terbuka (TPT) 2021-2023 Menggunakan K-Means.ipynb` untuk melihat seluruh alur analisis.

---

## 🛠️ Teknologi yang Digunakan

* **Python**
* **Pandas:** Untuk manipulasi dan analisis data.
* **NumPy:** Untuk komputasi numerik.
* **Scikit-learn:** Untuk implementasi K-Means, PCA, dan StandardScaler.
* **Matplotlib & Seaborn:** Untuk visualisasi data.
* **Jupyter Notebook:** Sebagai lingkungan kerja interaktif.

---

## 📄 Lisensi

Proyek ini dilisensikan di bawah Lisensi MIT.

---

Dibuat oleh **Bagus Darmawan** - [GitHub](https://github.com/Bagusdarmawan11)
