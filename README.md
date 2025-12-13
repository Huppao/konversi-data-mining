Analisis Sentimen Ulasan Game Stella Sora - Project Konversi Data Mining
Repositori ini berisi dokumentasi dan kode program untuk Project Akhir Konversi Mata Kuliah Data Mining (Periode Gasal 2025/2026). Proyek ini berfokus pada analisis sentimen ulasan pengguna terhadap aplikasi game Stella Sora menggunakan metode Machine Learning.

👨‍🎓 Identitas Mahasiswa
Nama: Augie Bryan Athalla

NPM: 23082010184

Program Studi: Sistem Informasi

Kampus: UPN "Veteran" Jawa Timur

Mata Kuliah: Data Mining (Konversi PLK)

📌 Deskripsi Proyek
Studi kasus yang diangkat dalam proyek ini adalah analisis opini pemain terhadap game RPG Stella Sora. Dengan ribuan ulasan yang masuk setiap harinya, pengembang game perlu memahami respon pasar secara otomatis.

Tujuan utama proyek ini adalah membangun model klasifikasi sentimen (Positif, Netral, Negatif) untuk melihat kecenderungan kepuasan pemain. Proyek ini mencakup proses end-to-end data mining:

Data Acquisition: Mengambil data ulasan dari Google Play Store.

Preprocessing: Membersihkan teks, menerjemahkan ulasan asing ke Indonesia, dan normalisasi.

Modeling: Melatih model Random Forest dengan fitur ekstraksi TF-IDF.

Evaluation: Mengukur performa model.

📂 Struktur Direktori
Berikut adalah penjelasan file yang ada dalam repositori ini:

Bash

├── dataset_stella_sora_original.csv  # Dataset mentah hasil scraping (15.000 data)
├── scrapping_playstore.ipynb         # Notebook: Proses crawling data dari Google Play
├── modeling.ipynb                    # Notebook: Preprocessing, EDA, dan Modeling (Random Forest)
├── requirements.txt                  # Daftar library Python yang dibutuhkan
└── README.md                         # Dokumentasi proyek ini
🛠️ Metodologi & Alur Pengerjaan
1. Pengumpulan Data (Data Acquisition)
Data diambil menggunakan teknik scraping dengan library google-play-scraper.

Target: Aplikasi Stella Sora (com.YoStarEN.StellaSora).

Volume: 15.000 data ulasan.

Cakupan: Multi-negara (ID, US, JP, KR, SG, IN, PH).

Translasi: Menggunakan deep-translator untuk mengubah ulasan non-Indonesia menjadi Bahasa Indonesia agar seragam.

2. Pra-pemrosesan Data (Preprocessing)
Tahapan penyiapan data meliputi:

Cleaning: Menghapus emoji, tanda baca, URL, dan angka menggunakan Regex.

Case Folding: Mengubah teks menjadi huruf kecil.

Stopword Removal: Menghapus kata umum yang tidak bermakna (menggunakan library Sastrawi).

Stemming: Mengubah kata berimbuhan menjadi kata dasar (menggunakan library Sastrawi).

Labeling: Pemberian label otomatis berdasarkan rating (1-2: Negatif, 3: Netral, 4-5: Positif).

3. Pemodelan (Modeling)
Feature Extraction: Menggunakan TF-IDF (Term Frequency-Inverse Document Frequency) dengan ngram_range=(1,2) (Unigram & Bigram) dan batas fitur 10.000 kata teratas.

Algoritma: Random Forest Classifier.

Konfigurasi: n_estimators=200, max_depth=50, class_weight='balanced'.

📊 Hasil dan Evaluasi
Berdasarkan eksperimen yang dilakukan pada notebook modeling.ipynb, model berhasil dibangun dengan performa sebagai berikut:

Distribusi Data: Data didominasi oleh sentimen Negatif (~64%), diikuti Positif (~31%), dan Netral (~4%).

Akurasi Training: ~91.98%

Akurasi Testing: ~86.56%

Hasil evaluasi menunjukkan model Random Forest mampu mengklasifikasikan sentimen dengan cukup baik (tidak overfitting berlebihan), meskipun terdapat tantangan pada ketidakseimbangan kelas data (imbalance dataset).

🚀 Cara Menjalankan Project (Reproducibility)
Untuk menjalankan ulang kode ini di lokal komputer Anda, ikuti langkah berikut:

Clone Repositori

Bash

git clone https://github.com/USERNAME_GITHUB_ANDA/NAMA_REPO_ANDA.git
cd NAMA_REPO_ANDA
Install Dependencies Pastikan Python sudah terinstal, lalu jalankan perintah:

Bash

pip install -r requirements.txt
Library utama: pandas, numpy, scikit-learn, nltk, sastrawi, google-play-scraper, deep-translator.

Jalankan Notebook

Buka scrapping_playstore.ipynb jika ingin mengambil data baru.

Buka modeling.ipynb untuk melihat proses analisis dan pemodelan.
