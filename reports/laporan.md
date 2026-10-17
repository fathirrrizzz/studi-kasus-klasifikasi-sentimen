# LAPORAN STUDI KASUS KLASIFIKASI

## Judul
**Klasifikasi Sentimen Ulasan Produk E-Commerce Berbahasa Indonesia Menggunakan TF-IDF dan Perbandingan Algoritma Machine Learning**

## 1. Pendahuluan

### 1.1 Latar Belakang
Ulasan pelanggan pada platform e-commerce memuat informasi mengenai pengalaman konsumen terhadap produk, layanan, dan proses pengiriman. Jumlah ulasan yang besar membuat pemeriksaan manual memerlukan waktu. Klasifikasi sentimen dapat membantu mengelompokkan ulasan ke dalam sentimen positif dan negatif secara otomatis, sehingga ulasan dapat ditinjau secara lebih terstruktur.

Penelitian ini menggunakan PRDECT-ID, dataset berisi 5.400 ulasan produk berbahasa Indonesia yang dikumpulkan dari Tokopedia dan mencakup 29 kategori produk. Dataset menyediakan label sentimen dan emosi sehingga dapat digunakan untuk eksperimen klasifikasi teks (Sutoyo et al., 2022).

### 1.2 Rumusan Masalah
1. Bagaimana membangun model klasifikasi sentimen berdasarkan teks ulasan produk berbahasa Indonesia?
2. Bagaimana membandingkan Logistic Regression, Multinomial Naive Bayes, dan Linear SVM?
3. Model mana yang memperoleh nilai macro-F1 terbaik pada test set?

### 1.3 Tujuan
1. Melakukan eksplorasi dan pemeriksaan kualitas dataset.
2. Membangun pipeline klasifikasi teks dengan TF-IDF.
3. Membandingkan tiga algoritma klasifikasi.
4. Mengevaluasi kinerja model menggunakan metrik klasifikasi yang sesuai.

### 1.4 Manfaat
Proyek ini menjadi contoh penerapan tahapan machine learning pada data teks berbahasa Indonesia dan menunjukkan cara mengevaluasi beberapa algoritma secara terukur.

## 2. Tinjauan Pustaka

### 2.1 Klasifikasi
Klasifikasi merupakan pendekatan supervised learning untuk mempelajari hubungan antara fitur dan label dari data berlabel, kemudian memprediksi label bagi data baru.

### 2.2 Analisis Sentimen
Analisis sentimen adalah tugas pemrosesan bahasa alami (Natural Language Processing/NLP) untuk mengidentifikasi polaritas atau kecenderungan opini dalam teks. Pada penelitian ini, label terdiri atas Positive dan Negative.

### 2.3 TF-IDF
Term Frequency–Inverse Document Frequency (TF-IDF) merepresentasikan teks sebagai vektor numerik. Bobot suatu kata dipengaruhi oleh frekuensi kata dalam dokumen dan tingkat kelangkaannya di seluruh korpus. Pengaturan unigram dan bigram memungkinkan model menggunakan kata tunggal serta pasangan kata sebagai fitur.

### 2.4 Algoritma
- **Logistic Regression:** model klasifikasi linear yang memodelkan probabilitas kelas.
- **Multinomial Naive Bayes:** model probabilistik yang sering digunakan pada representasi fitur teks.
- **Linear SVM:** mencari batas keputusan dengan margin yang memisahkan kelas.
- **Majority-class baseline:** pembanding sederhana yang selalu memprediksi kelas mayoritas.

### 2.5 Metrik Evaluasi
Accuracy menghitung proporsi prediksi yang benar. Precision menunjukkan ketepatan prediksi positif untuk suatu kelas; recall menunjukkan proporsi anggota kelas yang berhasil ditemukan; F1 merupakan rata-rata harmonik precision dan recall. Macro-average menghitung skor setiap kelas dengan bobot sama, sehingga berguna ketika distribusi kelas tidak persis seimbang.

## 3. Metodologi

### 3.1 Dataset
Dataset yang digunakan adalah PRDECT-ID dengan 5.400 ulasan Tokopedia berbahasa Indonesia pada 29 kategori produk. Atribut target adalah `Sentiment`, sedangkan fitur utama adalah `Customer Review`. Sumber akademik dataset: https://doi.org/10.1016/j.dib.2022.108554.

### 3.2 Pra-pemrosesan
1. Memuat CSV dan memeriksa nama kolom.
2. Memeriksa nilai kosong dan distribusi label.
3. Menormalisasi label menjadi `Positive` dan `Negative`.
4. Menghapus baris tanpa teks atau label valid.
5. Menghapus duplikasi pasangan teks-label.
6. Membagi data menjadi 80% data training dan 20% data testing dengan stratifikasi.
7. Mengubah teks menjadi fitur TF-IDF menggunakan unigram dan bigram.

Kolom `Customer Rating`, `Overall Rating`, dan `Emotion` tidak dimasukkan ke fitur model agar prediksi sentimen didasarkan pada teks ulasan dan mengurangi risiko kebocoran target. Karena data utama berupa teks dan TF-IDF menghasilkan matriks sparse, StandardScaler tidak diterapkan.

### 3.3 Pemodelan
Tiga model dilatih dengan pipeline yang menggabungkan TF-IDF dan classifier. `random_state=42` digunakan untuk membuat pembagian data dapat direproduksi. Logistic Regression dan Linear SVM menggunakan penyeimbang kelas melalui `class_weight='balanced'`.

### 3.4 Evaluasi
Setiap model diuji pada test set yang sama. Kinerja dibandingkan menggunakan accuracy, macro-precision, macro-recall, dan macro-F1. Classification report dan confusion matrix digunakan untuk menganalisis prediksi pada masing-masing kelas.

## 4. Hasil dan Pembahasan

> **Petunjuk:** Bagian ini harus dilengkapi setelah notebook dijalankan. Jangan memasukkan angka perkiraan atau mengklaim satu algoritma terbaik sebelum melihat hasil aktual.

### 4.1 Hasil Eksplorasi Data
Tuliskan jumlah data setelah validasi, distribusi kelas aktual, jumlah data training/testing, serta temuan dari grafik distribusi sentimen dan panjang ulasan.

### 4.2 Perbandingan Model
Masukkan tabel dari notebook:

| Model | Accuracy | Macro Precision | Macro Recall | Macro-F1 |
|---|---:|---:|---:|---:|
| Logistic Regression | — | — | — | — |
| Multinomial Naive Bayes | — | — | — | — |
| Linear SVM | — | — | — | — |
| Majority-class baseline | — | — | — | — |

Bahas model dengan macro-F1 tertinggi dan apakah model tersebut melampaui baseline. Perhatikan juga precision dan recall untuk kedua kelas, bukan hanya accuracy.

### 4.3 Confusion Matrix
Jelaskan jumlah prediksi benar dan salah pada setiap kelas berdasarkan confusion matrix model terbaik. Ulasan negatif yang diprediksi positif dan ulasan positif yang diprediksi negatif merupakan dua jenis kesalahan yang perlu dibahas secara terpisah.

### 4.4 Keterbatasan
Hasil dibatasi oleh karakteristik dan cakupan dataset. Model dapat kesulitan memahami sarkasme, bahasa tidak baku, typo, konteks, dan ulasan yang mengandung opini campuran. Pengujian pada dataset ini belum membuktikan bahwa model akan memiliki kinerja sama pada marketplace atau periode lain.

## 5. Kesimpulan dan Saran

### 5.1 Kesimpulan
Lengkapi setelah eksperimen selesai dengan menjawab rumusan masalah: apakah pipeline berhasil dijalankan, algoritma mana yang memperoleh macro-F1 tertinggi, berapa metrik evaluasinya, dan bagaimana hasilnya dibandingkan baseline.

### 5.2 Saran
1. Uji model pada data ulasan baru dari sumber berbeda jika tersedia dan diizinkan.
2. Evaluasi kesalahan klasifikasi dengan membaca sampel false positive dan false negative.
3. Lakukan tuning hyperparameter dengan validasi silang hanya pada data training.
4. Untuk pengembangan lanjutan, bandingkan pendekatan TF-IDF dengan model bahasa Indonesia berbasis transformer.

## Daftar Pustaka

Sutoyo, R., Achmad, S., Chowanda, A., Andangsari, E. W., & Isa, S. M. (2022). PRDECT-ID: Indonesian product reviews dataset for emotions classification tasks. *Data in Brief, 44*, 108554. https://doi.org/10.1016/j.dib.2022.108554
