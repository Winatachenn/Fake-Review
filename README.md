# Fake-Review

# 🛡️ 1. Title

**Project Name:** Fake Review Detection using Machine Learning and Pseudo-Labeling  
**Primary Dataset:** `fakedataset.csv` (Labeled Computer Generated vs Original)  
**Augmentation Data:** `datasetindo.csv` (Unlabeled Indonesian/Translated Reviews)

---

# 📝 2. Code / Dataset Description

Proyek ini berfokus pada pengembangan sistem cerdas untuk mengklasifikasikan ulasan produk sebagai asli atau palsu. Keunggulan proyek ini adalah penggunaan teknik **Semi-Supervised Learning** melalui metode **Pseudo-Labeling**, di mana model memanfaatkan data tidak berlabel untuk memperkaya basis pengetahuan dan meningkatkan akurasi akhir.

---

# 📊 3. Dataset Information

* **Gene Expression Dataset (fakedataset.csv):** Berisi data ulasan berlabel dengan kategori 'CG' (ulasan palsu buatan komputer) dan 'OR' (ulasan asli).
* **Phenotype Dataset (datasetindo.csv):** Berisi kumpulan ulasan tambahan yang belum memiliki label (bahasa Indonesia/terjemahan) yang digunakan untuk proses augmentasi model.

---

# 💻 4. Code Description

| File Name | Description |
| :--- | :--- |
| **train_fake_review.ipynb** | Notebook utama yang mencakup seluruh alur kerja: preprocessing teks, ekstraksi fitur TF-IDF, pelatihan model awal, proses *pseudo-labeling*, hingga evaluasi model. |
| **fake_review_model.pkl** | Model Logistic Regression yang telah dioptimasi menggunakan data augmentasi. |
| **fake_review_svm_best.pkl** | Model Linear SVM terbaik yang dihasilkan melalui tuning parameter *Grid Search*. |
| **tfidf_vectorizer.pkl** | Objek yang menyimpan pemetaan kata (TF-IDF) untuk mengubah teks menjadi fitur numerik. |

---

# 🚀 5. Usage Instructions

1.  **Load Datasets:** Gunakan `pandas` untuk memuat `fakedataset.csv` sebagai data latih utama dan `datasetindo.csv` sebagai data tambahan.
2.  **Preprocessing:** Jalankan fungsi `clean_text` untuk membersihkan data dari URL, simbol, dan melakukan *stemming*.
3.  **Initial Training:** Latih model awal menggunakan data berlabel untuk mendapatkan probabilitas prediksi awal.
4.  **Pseudo-Labeling:** Gunakan model awal untuk memprediksi label pada `datasetindo.csv`. Data dengan skor keyakinan $\ge 0.75$ akan digunakan sebagai label tambahan.
5.  **Final Modeling:** Gabungkan dataset asli dengan hasil *pseudo-label* untuk melatih model final agar performa lebih stabil.
6.  **Interpretation:** Gunakan **SHAP** untuk mengidentifikasi kata kunci penting yang menentukan keputusan model.

---

# 🛠️ 6. Requirements

Instalasi pustaka yang diperlukan melalui terminal:
```bash
pip install pandas numpy scikit-learn nltk shap joblib

NLTK: Digunakan untuk pembersihan bahasa (Stopwords & PorterStemmer).

Scikit-learn: Library utama untuk pemodelan (LogisticRegression, LinearSVC, GridSearchCV) dan ekstraksi fitur (TfidfVectorizer).

SHAP: Digunakan untuk transparansi model (melihat fitur yang paling berpengaruh).


#7. Methodology for Code Usage
Lakukan pembersihan teks mentah menggunakan fungsi clean_text di awal proses.

Lakukan pembagian data (Data Split) untuk memastikan evaluasi model yang objektif.

Terapkan TfidfVectorizer dengan parameter ngram_range=(1,2) untuk menangkap konteks kata yang lebih luas.

Gunakan teknik augmentasi data (Pseudo-labeling) untuk memperbanyak data latih secara otomatis.

Evaluasi model menggunakan metrik akurasi, laporan klasifikasi, dan skor ROC-AUC.

📚 8. Citation
Not applicable.

⚖️ 9. License & Contribution Guidelines
Not applicable.

📂 10. Code Repository or DOI
[Masukkan Tautan Repository Anda di Sini]
