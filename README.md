# Lampiran Penelitian: Analisis Sentimen Berbasis Aspek pada Ulasan Wisata Jatim Park Group Menggunakan Random Forest

Repositori ini berisi seluruh data lampiran, standar operasional, dataset hasil pelabelan, serta kode program untuk penelitian **"Analisis Sentimen Berbasis Aspek pada Ulasan Wisata Jatim Park Group Menggunakan Random Forest"**.

## 📌 Latar Belakang Data & Metodologi Pelabelan

Data penelitian ini diperoleh melalui proses *scraping* ulasan wisatawan dari dua platform digital utama, yaitu **Google Maps** dan **TripAdvisor**. Fokus objek penelitian mencakup 4 destinasi utama di bawah naungan Jatim Park Group, yaitu:
1. **Jawa Timur Park 1 (JTP 1)**
2. **Jawa Timur Park 2 (JTP 2 / Batu Secret Zoo & Museum Satwa)**
3. **Jawa Timur Park 3 (JTP 3)**
4. **Museum Angkut**

Karena data ulasan yang ditarik tidak memiliki label (*unlabeled data*), proses anotasi aspek dan sentimen dilakukan secara otomatis menggunakan Large Language Model (**Claude**) yang dipandu oleh aturan konteks tertulis (**SOP Anotasi**). 

Untuk menjamin akuntabilitas ilmiah dan membuktikan bahwa hasil pelabelan Claude bersifat reliabel sebelum digunakan untuk melatih model Random Forest, dilakukan uji validasi menggunakan metode *Expert Agreement* pada 249 sampel ulasan acak yang mewakili destinasi tersebut.

---

## 📊 Rangkuman Hasil Validasi (Reliability Test)

Berdasarkan hasil penyandingan antara label otomatis dari Claude dan label manual dari *Expert Person* terhadap 249 sampel ulasan acak, diperoleh tingkat kesepakatan yang sangat tinggi:

* **Total Sampel Validasi:** 249 data ulasan
* **Tingkat Kesepakatan (Percentage of Agreement):** **82%**

Dengan tingkat kesepakatan sebesar **82%**, hasil anotasi otomatis menggunakan Claude dinyatakan **sangat reliabel dan valid** untuk digunakan sebagai keseluruhan data latih (*training data*) pada model *Machine Learning* Random Forest.

---

## 📁 Struktur dan Penjelasan Berkas

Kamu dapat menemukan seluruh komponen riset pada berkas-berkas berikut:

### 1. Dokumen Panduan & Kamus Preprocessing
* **`SOP_Anotasi.pdf`**: Dokumen Standar Operasional Prosedur yang berisi panduan, definisi aspek, sentimen, dan aturan konteks yang diberikan kepada Claude sebagai instruksi (*prompt*) pelabelan.
* **`colloquial-indonesian-lexicon.csv`**: *Dictionary* / kamus kata gaul (bahasa Indonesia informal) yang digunakan pada tahap *Text Normalization* di dalam proses *preprocessing* untuk mengubah kata tidak baku menjadi kata baku.

### 2. Dataset Penelitian (`Dataset_Penelitian.xlsx` / `.csv`)
Berisi beberapa lembar kerja (*sheets*) utama:
* **`Final_Data`**: Keseluruhan dataset ulasan dari 4 destinasi (JTP 1, JTP 2, JTP 3, dan Museum Angkut) hasil pelabelan Claude yang telah dinyatakan reliabel dan digunakan dalam pemodelan Random Forest.
* **`Expert Person`**: Data 249 sampel ulasan acak dari Google Maps & TripAdvisor yang telah dilabeli secara mandiri oleh *Expert Person* (Pakar/Ahli).
* **`LLM_Test`**: Data 249 sampel ulasan yang sama yang dilabeli oleh Claude untuk kebutuhan uji reliabilitas.
* **`Comparasion Expert and LLM_Test`**: Tabel sanding (*matrix agreement*) komparasi antara sheet `Expert Person` dan `LLM_Test` yang menghasilkan nilai kesepakatan 82%.

### 3. Kode Program
* **`Kode_Program_Random_Forest.md`**: Seluruh kode pemrograman Python yang diunduh dari Google Colab. Berisi proses prapemrosesan data (*preprocessing* termasuk pemanfaatan *colloquial lexicon*), ekstraksi fitur, penanganan data imbalanced, hingga tahap pelatihan dan evaluasi model Random Forest.

---

## 🔒 Etika Penelitian & Privasi
Seluruh ulasan pengunjung dari Google Maps dan TripAdvisor dalam repositori ini telah melewati proses anonimisasi dengan menghapus Informasi Identitas Pribadi (seperti nama akun asli pengulas dan foto) untuk mematuhi etika penggunaan data publik dan menjaga privasi platform.
