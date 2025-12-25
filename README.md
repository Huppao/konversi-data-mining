# 🎮 Analisis Sentimen Ulasan Game *Stella Sora*

Project Konversi Mata Kuliah **Data Mining** (Periode Gasal 2025/2026)

---

## 📖 Deskripsi Umum

Repositori ini berisi dokumentasi dan kode program untuk **Project Akhir Konversi Mata Kuliah Data Mining**. Proyek ini berfokus pada **analisis sentimen ulasan pengguna** terhadap aplikasi game **Stella Sora** menggunakan pendekatan **Machine Learning**.

Analisis sentimen dilakukan untuk mengklasifikasikan opini pengguna ke dalam tiga kategori, yaitu **Positif**, **Netral**, dan **Negatif**, sehingga dapat membantu pengembang dalam memahami persepsi dan kepuasan pemain secara otomatis.

---

## 👨‍🎓 Identitas Mahasiswa

* **Nama**            : Augie Bryan Athalla
* **NPM**             : 23082010184
* **Program Studi**   : Sistem Informasi
* **Perguruan Tinggi**: UPN "Veteran" Jawa Timur
* **Mata Kuliah**     : Data Mining (Konversi PLK)

---

## 📌 Deskripsi Proyek

Studi kasus pada proyek ini mengangkat **ulasan pemain terhadap game RPG Stella Sora**. Dengan jumlah ulasan yang sangat besar dan terus bertambah setiap hari, dibutuhkan sistem otomatis untuk memahami kecenderungan opini pengguna.

Tujuan utama proyek ini adalah:

* Membangun **model klasifikasi sentimen** (Positif, Netral, Negatif)
* Mengetahui tingkat kepuasan pemain berdasarkan ulasan di Google Play Store

Proyek ini mencakup proses **end-to-end data mining**, meliputi:

1. **Data Acquisition** – Pengambilan data ulasan dari Google Play Store
2. **Preprocessing** – Pembersihan dan normalisasi data teks
3. **Modeling** – Pelatihan model Machine Learning
4. **Evaluation** – Evaluasi performa model

---

## 📂 Struktur Direktori

Berikut adalah struktur file dalam repositori ini:

```bash
├── Notebook
  ├── scrapping_playstore.ipynb
  ├── modeling.ipynb 
├── Dataset
  ├── dataset_stella_sora_original.csv                   
├── requirements.txt                  
└── README.md                         
```

---

## 🛠️ Metodologi & Alur Pengerjaan

### 1️⃣ Pengumpulan Data (*Data Acquisition*)

* Data diperoleh melalui teknik **web scraping** menggunakan library `google-play-scraper`
* **Target aplikasi** : Stella Sora (`com.YoStarEN.StellaSora`)
* **Jumlah data**     : 15.000 ulasan
* **Cakupan negara**  : ID, US, JP, KR, SG, IN, PH
* **Translasi data**  : Menggunakan `deep-translator` untuk menerjemahkan ulasan non-Bahasa Indonesia agar data seragam

---

### 2️⃣ Pra-pemrosesan Data (*Preprocessing*)

Tahapan preprocessing yang dilakukan meliputi:

* **Text Cleaning**  : Menghapus tanda baca, URL, dan angka menggunakan *Regex*
* **Case Folding**  : Mengubah seluruh teks menjadi huruf kecil
* **Stopword Removal** : Menghapus kata umum yang tidak memiliki makna sentimen (library **Sastrawi**)
* **Stemming**      : Mengubah kata berimbuhan menjadi kata dasar (library **Sastrawi**)
* **Labeling**      : Pemberian label otomatis berdasarkan rating:

  * Rating 1–2 → **Negatif**
  * Rating 3   → **Netral**
  * Rating 4–5 → **Positif**

---

### 3️⃣ Pemodelan (*Modeling*)

* **Feature Extraction** : TF-IDF (*Term Frequency – Inverse Document Frequency*)

  * `ngram_range = (1,2)` (Unigram & Bigram)
  * Maksimum 10.000 fitur kata
* **Algoritma** : Random Forest Classifier
* **Parameter utama** :

  * `n_estimators = 200`
  * `max_depth = 50`
  * `class_weight = 'balanced'`

---

## 📊 Hasil dan Evaluasi

Berdasarkan eksperimen pada notebook `modeling.ipynb`, diperoleh hasil sebagai berikut:

* **Distribusi Sentimen**:

  * Negatif  : 64%
  * Positif  : 31%
  * Netral   : 4%

* **Akurasi Training** : 91.98%

* **Akurasi Testing**  : 86.56%

Hasil evaluasi menunjukkan bahwa **Random Forest** mampu mengklasifikasikan sentimen dengan cukup baik dan tidak mengalami *overfitting* yang berlebihan. Tantangan utama berasal dari **ketidakseimbangan kelas data (imbalanced dataset)**.

---

## 🚀 Cara Menjalankan Proyek (*Reproducibility*)

Ikuti langkah berikut untuk menjalankan proyek ini di komputer lokal:

### 1️⃣ Clone Repositori

```bash
git clone 
cd konversi-data-mining
```

### 2️⃣ Install Dependencies

Pastikan **Python** sudah terinstal, kemudian jalankan:

```bash
pip install -r requirements.txt
```

Library utama yang digunakan:

* `pandas`
* `numpy`
* `scikit-learn`
* `nltk`
* `sastrawi`
* `google-play-scraper`
* `deep-translator`

### 3️⃣ Jalankan Notebook

* Jalankan `scrapping_playstore.ipynb` untuk mengambil data ulasan terbaru
* Jalankan `modeling.ipynb` untuk melihat proses preprocessing, dan pemodelan

---

## 📌 Catatan

Repositori ini dibuat untuk **keperluan akademik** dan diharapkan dapat menjadi referensi pembelajaran dalam penerapan **Text Mining dan Analisis Sentimen** menggunakan Machine Learning.

---

✨ *Feel free to fork, explore, and learn!*
