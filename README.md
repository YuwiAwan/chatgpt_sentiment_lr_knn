# Analisis Sentimen ChatGPT pada Twitter/X Menggunakan Logistic Regression & K-Nearest Neighbors (KNN)

Repositori ini berisi kode dan implementasi untuk analisis sentimen terhadap tweet/postingan mengenai **ChatGPT** di platform X (Twitter). Proyek ini memanfaatkan metode *Natural Language Processing (NLP)* dan *Machine Learning* untuk membandingkan performa algoritma **Logistic Regression** dan **K-Nearest Neighbors (KNN)** dalam melakukan klasifikasi sentimen (Positif dan Negatif).

---

## Sumber Dataset
Dataset yang digunakan dalam proyek ini diambil dari Kaggle:
- **Judul Dataset:** ChatGPT Twitter Dataset
- **Sumber / Link:** [Kaggle - ChatGPT Twitter Dataset by Tariq Says](https://www.kaggle.com/datasets/tariqsays/chatgpt-twitter-dataset)[cite: 1]

---

## 🛠️ Alur Kerja & Metodologi

1. **Pengumpulan & Pembersihan Data (*Data Preprocessing & Cleaning*):**
   - Memfilter tweet berbahasa Inggris.
   - Menghapus URL, *mentions* (`@`), *hashtags* (tanda `#`), emoji, dan karakter khusus yang tidak diperlukan.
   - Tokenisasi teks dan penghitungan jumlah kata.

2. **Pelabelan Otomatis (*Sentiment Labeling*):**
   - Menggunakan **VADER Sentiment Analyzer** (`vaderSentiment`) untuk menghitung *Compound Score* dari setiap tweet.
   - Mengelompokkan skor ke dalam kategori sentimen: **Positive**, **Neutral**, dan **Negative**[cite: 1, 2].
   - Memfokuskan analisis klasifikasi pada dua kelas utama, yaitu **Positive** dan **Negative**.

3. **Ekstraksi Fitur (*Feature Extraction*):**
   - Menggunakan **TF-IDF Vectorizer** (`TfidfVectorizer`) dengan konfigurasi `max_features=10000`, n-grams `(1,2)`, serta memfilter *stop_words* bahasa Inggris[cite: 1].

4. **Pembagian Data (*Train-Test Split*):**
   - Membagi data dengan rasio **80% data latih (Training)** dan **20% data uji (Testing)** menggunakan metode *stratified split*[cite: 1].

---

## Model Machine Learning & Hasil Evaluasi

Dua model *supervised learning* dilatih dan dievaluasi dalam penelitian ini:

1. **Logistic Regression:**
   - Parameter utama: `C=5`, `solver='liblinear'`, `max_iter=3000`[cite: 1].
   - **Akurasi Model:** **~86.77%**[cite: 1]

2. **K-Nearest Neighbors (KNN):**
   - Parameter utama: `n_neighbors=21`, `weights='distance'`[cite: 1].
   - **Akurasi Model:** **~79.88%**[cite: 1]

> **Kesimpulan Perbandingan:** Berdasarkan metrik evaluasi (Akurasi, *Precision*, *Recall*, dan *F1-Score*), **Logistic Regression** menunjukkan performa yang lebih unggul dan stabil dibandingkan KNN dalam menangani ruang fitur berdimensi tinggi dari ekstraksi teks TF-IDF[cite: 1].
