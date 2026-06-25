# Flood Probability Prediction

**Flood Probability Prediction** adalah proyek data science yang bertujuan memprediksi probabilitas banjir berdasarkan 20 faktor risiko lingkungan dan infrastruktur. Proyek ini dikembangkan sebagai submission pada babak Preliminary Data Science Competition.

---

## Deskripsi Proyek

Proyek ini mencakup pipeline data science secara lengkap, mulai dari eksplorasi data, rekayasa fitur, pelatihan model regresi, hingga pengelompokan data menggunakan K-Means. Hasil akhir divisualisasikan melalui Visual Risk Intelligence Dashboard.

---

## Struktur Repositori

| File                                          | Keterangan                                  |
| --------------------------------------------- | ------------------------------------------- |
| `Notebook_Preliminary_es_kelapa_lovers.ipynb` | Notebook utama berisi seluruh analisis      |
| `requirements.txt`                            | Daftar dependensi Python                    |
| `.gitignore`                                  | File yang dikecualikan dari version control |
| `README.md`                                   | Dokumentasi proyek                          |

Dataset `flood.csv` tidak disertakan dalam repositori karena merupakan aset milik penyelenggara lomba.

---

## Metodologi

### 1. Pemuatan dan Validasi Data

- Dataset dimuat dari `flood.csv`
- Seluruh 20 fitur dikonfirmasi berada dalam rentang valid `[0, 10]`
- Tidak ditemukan outlier — distribusi bersifat simetris

### 2. Rekayasa Fitur

- **Total Risk Index (TRI)** — Fitur baru hasil penjumlahan seluruh 20 faktor risiko per baris data
- Batas kategori TRI: Rendah (< 70), Sedang (70–110), Tinggi (110–150), Kritis (> 150)

### 3. Eksplorasi Data (EDA)

| Gambar   | Keterangan                                         |
| -------- | -------------------------------------------------- |
| Gambar 1 | Correlation Heatmap — 20 Fitur vs FloodProbability |
| Gambar 2 | Distribusi FloodProbability                        |
| Gambar 3 | Distribusi TRI dengan Band Threshold Risiko        |

### 4. Pelatihan Model

Pembagian data menggunakan stratified split 80/20 berdasarkan kategori risiko (Low, Moderate, High, Critical).

| Model                   | Jenis                |
| ----------------------- | -------------------- |
| Linear Regression (OLS) | Baseline regresi     |
| Random Forest Regressor | Ensemble (100 pohon) |
| XGBoost Regressor       | Gradient boosting    |

### 5. Evaluasi dan Analisis Fitur

| Gambar   | Keterangan                                     |
| -------- | ---------------------------------------------- |
| Gambar 4 | Predicted vs Actual FloodProbability (3 model) |
| Gambar 7 | Analisis Koefisien OLS                         |
| Gambar 8 | 5 Fitur Dominan (XGBoost dan Random Forest)    |
| Gambar 9 | Peringkat Seluruh 20 Fitur                     |

### 6. Clustering Tanpa Supervisi

- K-Means dengan k=3, dipilih menggunakan Elbow Method
- Cluster dilabeli berdasarkan centroid TRI: **Aman**, **Waspada**, **Bahaya**
- PCA digunakan untuk memproyeksikan cluster ke ruang 2D

| Gambar    | Keterangan                                 |
| --------- | ------------------------------------------ |
| Gambar 6  | K-Means Clustering (k=3) — Proyeksi PCA 2D |
| Gambar 10 | Visual Risk Intelligence Dashboard         |

---

## Teknologi yang Digunakan

| Kategori          | Library                 |
| ----------------- | ----------------------- |
| Manipulasi Data   | `pandas`, `numpy`       |
| Visualisasi       | `matplotlib`, `seaborn` |
| Machine Learning  | `scikit-learn`          |
| Gradient Boosting | `xgboost`               |

---

## Cara Menjalankan

1. Clone repository ini:

   ```bash
   git clone https://github.com/<username>/<nama-repo>.git
   cd <nama-repo>
   ```

2. Buat virtual environment dan aktifkan:

   ```bash
   python -m venv venv
   source venv/bin/activate        # Linux/macOS
   venv\Scripts\activate           # Windows
   ```

3. Install dependensi:

   ```bash
   pip install -r requirements.txt
   ```

4. Letakkan file `flood.csv` di direktori utama proyek.

5. Jalankan notebook:
   ```bash
   jupyter notebook Notebook_Preliminary_es_kelapa_lovers.ipynb
   ```

---

## Temuan Utama

- XGBoost menghasilkan nilai R² tertinggi di antara ketiga model.
- Seluruh 20 fitur berkontribusi secara merata terhadap probabilitas banjir, konsisten dengan koefisien OLS yang mendekati 1/200 per fitur.
- K-Means berhasil membagi data ke dalam tiga zona risiko yang interpretatif dan tervalidasi oleh nilai centroid TRI.
- Visual Risk Intelligence Dashboard menunjukkan keselarasan yang kuat antara prediksi XGBoost dan distribusi kategori risiko aktual.

---

## Tim

| Nama             | Institusi                                    |
| ---------------- | -------------------------------------------- |
| es_kelapa_lovers | Universitas Singaperbangsa Karawang (UNSIKA) |

---

## Lisensi

Proyek ini dikembangkan untuk keperluan kompetisi akademik. Hak atas dataset sepenuhnya milik penyelenggara lomba.
