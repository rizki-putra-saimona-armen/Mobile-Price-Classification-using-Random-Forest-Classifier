#  Mobile Price Classification using Random Forest Classifier

Repository ini berisi proyek implementasi algoritma **Random Forest Classifier** untuk memprediksi kelas atau rentang harga perangkat seluler (*mobile phone*) berdasarkan spesifikasi teknisnya (seperti kapasitas RAM, daya baterai, dimensi piksel layar, berat perangkat, dan lainnya). Proyek ini juga mendemonstrasikan teknik optimasi model menggunakan *Feature Engineering* (Polinomial) dan *Hyperparameter Tuning*.

##  Fitur Utama Proyek
* **Data Preprocessing & Feature Engineering:** Implementasi transformasi data numerik menggunakan skema pipa (*pipeline*) serta penambahan fitur kuadratik/interaksi melalui fitur polinomial (`poly=2`).
* **Random Forest Classification:** Pemodelan menggunakan *Random Forest Classifier* untuk menangani klasifikasi multikelas secara efisien.
* **Hyperparameter Tuning:** Optimasi parameter model secara efisien menggunakan `RandomizedSearchCV` dengan validasi silang (`cv=3`) sebanyak 50 iterasi eksperimen (`n_iter=50`).
* **Model Evaluation & Evaluation Metric:** Menggunakan **Accuracy Score** secara bawaan sebagai metrik evaluasi utama untuk mengukur persentase tebakan klasifikasi yang tepat pada data latihan dan data uji.

---

##  Workflow & Arsitektur Model

### 1. Robust Pipeline & Feature Engineering
Proyek ini menggunakan arsitektur `Pipeline` dan `ColumnTransformer` dari Scikit-Learn untuk memastikan kebersihan alur data:
* Fitur numerik penting seperti `battery_power`, `mobile_wt`, `px_height`, `px_width`, dan `ram` diekstrak pola hubungan non-linearnya menggunakan fitur polinomial derajat 2.
* Seluruh proses *preprocessor* digabungkan langsung dengan algoritma `RandomForestClassifier` untuk menghindari **Data Leakage** (Kebocoran Data) selama proses validasi silang.

### 2. Efisiensi Tuning dengan RandomizedSearchCV
Dibandingkan menggunakan *GridSearchCV* yang memakan waktu lama karena mengecek seluruh kombinasi parameter, proyek ini menerapkan **RandomizedSearchCV**. Teknik ini memilih kombinasi parameter secara acak dari ruang pencarian yang ditentukan (`rsp.rf_poly_params`), sehingga memangkas waktu komputasi pemrosesan *training* namun tetap mampu menemukan konfigurasi model yang optimal.

---

##  Tech Stack & Library
* **Python** (Bahasa Pemrograman Utama)
* **Jupyter Notebook** (`.ipynb`)
* **Pandas & NumPy** (Manipulasi Data dan Komputasi Numerik)
* **Scikit-Learn** (`RandomForestClassifier`, `RandomizedSearchCV`, `Pipeline`, dan `ColumnTransformer`)
* **jcopml** (Ekstensi *helper pipeline*, visualisasi, dan modul penyimpanan model otomatis)

---

##  Cara Menjalankan Proyek

1. **Clone Repositori Ini:**
   ```bash
   git clone [https://github.com/username-kamu/nama-repositori.git](https://github.com/username-kamu/nama-repositori.git)
   cd nama-repositori
