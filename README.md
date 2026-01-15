# 🩺 Heart Disease Risk Prediction (Supervised Learning)

Proyek ini bertujuan untuk membangun model klasifikasi Machine Learning yang dapat memprediksi risiko penyakit jantung pada pasien berdasarkan parameter klinis seperti usia, tekanan darah, kadar kolesterol, dan detak jantung maksimal.

---

## 🚀 Fitur Utama

- **End-to-End ML Pipeline**: Mulai dari pembersihan data hingga ekspor model siap pakai
- **Feature Importance Analysis**: Mengidentifikasi faktor medis mana yang paling berkontribusi terhadap risiko penyakit jantung
- **Model Persistence**: Model disimpan menggunakan joblib agar dapat langsung digunakan di lingkungan produksi atau aplikasi web

---

## 📦 Instalasi & Dependensi

Proyek ini menggunakan pustaka standar data science di Python. Instalasi dapat dilakukan dengan:

```bash
pip install pandas numpy scikit-learn matplotlib seaborn joblib
```

### Dependensi yang Diperlukan:
- **pandas**: Manipulasi dan analisis data
- **numpy**: Komputasi numerik
- **scikit-learn**: Machine Learning dan preprocessing
- **matplotlib & seaborn**: Visualisasi data
- **joblib**: Penyimpanan dan loading model

---

## 🛠️ Alur Kerja & Penjelasan Kode

Berdasarkan implementasi di `Heart Disease Risk Prediction.ipynb`, berikut adalah tahapan pengolahan datanya:

### 1. Exploratory Data Analysis (EDA)

Tahap awal mencakup pemeriksaan distribusi data dan korelasi antar variabel. Kita menggunakan seaborn untuk melihat hubungan antara fitur medis (seperti RestingBP atau Cholesterol) dengan label target (sakit/sehat).

**Tujuan:**
- Memahami karakteristik data
- Mengidentifikasi outlier dan missing values
- Melihat korelasi antar variabel

### 2. Data Preprocessing

Agar model bekerja maksimal, data melalui proses:

#### Scaling
Menggunakan MinMaxScaler untuk menyamakan skala fitur numerik agar tidak ada variabel yang mendominasi hanya karena angka nominalnya besar (misal: Kolesterol vs Gender).

#### Train-Test Split
Membagi dataset menjadi data latih dan data uji (biasanya rasio 80:20) untuk memvalidasi performa model pada data baru.

### 3. Pemodelan (Random Forest Classifier)

Proyek ini menggunakan algoritma **Random Forest**, yang merupakan kumpulan dari banyak Decision Trees. 

**Alasan pemilihan:**
- Ketahanan terhadap overfitting
- Kemampuan menangani data tabular dengan sangat baik
- Mampu menangani hubungan non-linear
- Memberikan feature importance yang interpretable

### 4. Evaluasi Model

Model dievaluasi menggunakan:

#### Accuracy Score
Melihat persentase prediksi yang benar secara keseluruhan.

#### Confusion Matrix
Menganalisis kesalahan model (False Positives vs False Negatives), yang sangat krusial dalam domain medis.

#### Feature Importance
Menampilkan grafik variabel yang paling berpengaruh (misal: MaxHeartRate seringkali menjadi indikator utama).

---

## 📊 Contoh Penggunaan (Inference)

Setelah model dilatih dan disimpan sebagai `heart_disease_model.pkl`, model dapat dipanggil kembali untuk memprediksi data pasien baru:

```python
import joblib

# Load model
model = joblib.load('heart_disease_model.pkl')

# Data pasien: [Usia, Gender, RestingBP, Cholesterol, MaxHR, FastingBS]
new_patient = [[45, 1, 120, 250, 160, 0]]
prediction = model.predict(new_patient)

print(f"Hasil Prediksi: {'Berisiko' if prediction[0] == 1 else 'Aman'}")
```

### Interpretasi Output:
- **0 (Aman)**: Pasien tidak menunjukkan risiko penyakit jantung yang signifikan
- **1 (Berisiko)**: Pasien menunjukkan risiko penyakit jantung yang perlu perhatian medis

---

## 📂 Struktur Proyek

```
Heart Disease Risk Prediction/
├── Heart Disease Risk Prediction.ipynb    # Notebook eksperimen dan training
├── Cardiovascular_Disease_Dataset.csv     # Dataset utama
├── heart_disease_model.pkl                # Model yang sudah dilatih (Output)
└── README.md                              # Dokumentasi ini
```

### Deskripsi File:

| File | Deskripsi |
|------|-----------|
| `Heart Disease Risk Prediction.ipynb` | Notebook Jupyter yang berisi seluruh pipeline ML dari EDA hingga evaluasi model |
| `Cardiovascular_Disease_Dataset.csv` | Dataset mentah yang berisi informasi klinis pasien |
| `heart_disease_model.pkl` | Model Random Forest yang telah dilatih dan disimpan dalam format joblib |
| `README.md` | File dokumentasi ini |

---

## 🔧 Cara Menjalankan Proyek

1. **Clone/Download repository**
   ```bash
   cd "Heart Disease Risk Prediction"
   ```

2. **Install dependensi**
   ```bash
   pip install -r requirements.txt
   ```

3. **Jalankan notebook**
   - Buka file `Heart Disease Risk Prediction.ipynb` di Jupyter Notebook atau JupyterLab
   - Jalankan semua cell secara berurutan
   - Model akan otomatis disimpan sebagai `heart_disease_model.pkl`

4. **Gunakan model untuk prediksi**
   - Gunakan contoh kode di bagian "Contoh Penggunaan" untuk melakukan prediksi

---

## 📋 Parameter Input Model

Ketika memberikan input ke model, pastikan urutan fitur sesuai dengan:

| Urutan | Fitur | Tipe | Keterangan |
|--------|-------|------|-----------|
| 1 | Age | Numerik | Usia pasien (tahun) |
| 2 | Gender | Kategorik | 0 = Wanita, 1 = Pria |
| 3 | RestingBP | Numerik | Tekanan darah istirahat (mmHg) |
| 4 | Cholesterol | Numerik | Kadar kolesterol (mg/dL) |
| 5 | MaxHR | Numerik | Detak jantung maksimal yang dicapai |
| 6 | FastingBS | Numerik | Gula darah puasa (0/1) |

---

## 📈 Hasil Model

Setelah training, model akan menghasilkan:
- **Accuracy Score**: Tingkat akurasi model pada data test
- **Confusion Matrix**: Perbandingan prediksi vs aktual
- **Feature Importance Chart**: Visualisasi kontribusi setiap fitur
- **Trained Model File**: `heart_disease_model.pkl` untuk penggunaan di masa depan

---

## 💡 Tips Penggunaan

- Pastikan fitur input sudah dinormalisasi (scaled) sesuai dengan preprocessing yang dilakukan saat training
- Gunakan model ini sebagai alat bantu diagnostik, bukan pengganti konsultasi medis profesional
- Secara berkala perbarui model dengan data terbaru untuk meningkatkan akurasi
- Monitor performance model pada data baru untuk mendeteksi data drift

---

## 📞 Support & Kontribusi

Jika ada pertanyaan atau saran untuk peningkatan proyek ini, silakan buat issue atau pull request.

---

**Last Updated**: January 2026
