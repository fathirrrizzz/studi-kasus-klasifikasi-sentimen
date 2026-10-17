# Studi Kasus Klasifikasi Sentimen Ulasan Produk E-Commerce Indonesia

Proyek pembelajaran *machine learning* untuk mengklasifikasikan ulasan produk berbahasa Indonesia menjadi sentimen **Positive** atau **Negative** menggunakan dataset PRDECT-ID.

## Tujuan

1. Memeriksa struktur dan kualitas dataset.
2. Melakukan eksplorasi data (*exploratory data analysis*/EDA).
3. Mengubah teks ulasan menjadi fitur numerik menggunakan TF-IDF.
4. Membandingkan Logistic Regression, Multinomial Naive Bayes, dan Linear Support Vector Machine (Linear SVM).
5. Mengevaluasi model menggunakan accuracy, macro-precision, macro-recall, macro-F1, classification report, dan confusion matrix.
6. Menentukan model terbaik berdasarkan hasil evaluasi yang benar-benar diperoleh dari data uji.

## Dataset dan sumber data

- **Nama:** Product Reviews Dataset for Emotions Classification Tasks - Indonesian (PRDECT-ID) Dataset.
- **Asal data:** ulasan produk dari Tokopedia.
- **Ukuran:** 5.400 ulasan dari 29 kategori produk.
- **Bahasa:** Indonesia.
- **Fitur teks:** `Customer Review`.
- **Target klasifikasi:** `Sentiment` (`Positive` atau `Negative`).
- **Halaman dataset asli:** https://data.mendeley.com/datasets/574v66hf2v/1
- **DOI dataset:** https://doi.org/10.17632/574v66hf2v.1
- **Mirror alternatif:** https://huggingface.co/datasets/ZakyF/PRDECT-ID

Dataset tidak disertakan di repository ini. Unduh dari sumber resmi di atas jika diperlukan dan periksa ketentuan lisensinya sebelum mendistribusikan ulang. Notebook dirancang untuk memuat data dari sumber daring atau menggunakan file CSV lokal jika pengambilan daring gagal.

## Metode

1. Memeriksa nama kolom, tipe data, nilai kosong, dan duplikasi.
2. Menyiapkan teks ulasan dan label sentimen.
3. Membagi data menjadi data latih dan data uji dengan rasio 80:20 serta stratifikasi.
4. Mengubah teks menjadi fitur TF-IDF (unigram dan bigram).
5. Melatih dan membandingkan:
   - Logistic Regression
   - Multinomial Naive Bayes
   - Linear SVM
   - Majority-class baseline sebagai pembanding sederhana
6. Mengevaluasi hasil dengan metrik klasifikasi dan confusion matrix.

**Pencegahan data leakage:** model menggunakan `Customer Review` sebagai fitur dan `Sentiment` sebagai target. Kolom `Customer Rating`, `Overall Rating`, dan `Emotion` tidak digunakan sebagai fitur, karena dapat membocorkan informasi yang berkaitan dengan label atau mengubah pertanyaan penelitian dari klasifikasi berbasis teks.

TF-IDF digunakan untuk merepresentasikan teks menjadi bobot numerik. `StandardScaler` tidak diperlukan dalam pipeline TF-IDF ini.

## Struktur repository

```text
studi-kasus-klasifikasi-sentimen/
├── notebooks/
│   └── studi_kasus_klasifikasi_sentimen.ipynb
├── reports/
│   └── laporan.md
├── outputs/                 # hasil eksperimen; ditambahkan setelah notebook dijalankan
├── README.md
├── requirements.txt
├── .gitignore
└── GITHUB_GUIDE.md
```

## Cara menjalankan

### Opsi A — Google Colab (disarankan untuk tugas ini)

1. Unduh atau buka file `notebooks/studi_kasus_klasifikasi_sentimen.ipynb`.
2. Buka https://colab.research.google.com/.
3. Pilih **File → Upload notebook** dan unggah notebook tersebut, atau buka notebook yang telah tersimpan di GitHub.
4. Jalankan sel secara berurutan dari atas ke bawah.
5. Pastikan internet aktif jika notebook mengambil CSV dari Hugging Face. Jika gagal, unduh CSV dari halaman Mendeley Data dan unggah ke Colab, lalu sesuaikan variabel path pada sel pemuatan data.
6. Setelah selesai, simpan notebook beserta output hasil eksperimen jika diperlukan untuk penilaian.

### Opsi B — Komputer lokal

Disarankan menggunakan Python 3.10 atau versi kompatibel yang didukung oleh paket di `requirements.txt`.

```bash
python -m venv .venv
```

Aktifkan lingkungan virtual:

- **Windows:** `.venv\Scripts\activate`
- **macOS/Linux:** `source .venv/bin/activate`

Kemudian jalankan:

```bash
pip install -r requirements.txt
jupyter notebook
```

Buka notebook dari folder `notebooks/` dan jalankan sel secara berurutan. Jika dataset belum tersedia secara lokal, ikuti petunjuk pemuatan data di notebook.

## Hasil eksperimen

Isi tabel berikut **setelah notebook dijalankan**. Jangan mengisi nilai perkiraan atau mengklaim model terbaik sebelum melihat hasil evaluasi aktual.

| Model | Accuracy | Macro Precision | Macro Recall | Macro-F1 |
|---|---:|---:|---:|---:|
| Logistic Regression | — | — | — | — |
| Multinomial Naive Bayes | — | — | — | — |
| Linear SVM | — | — | — | — |
| Majority-class baseline | — | — | — | — |

Jika notebook menghasilkan file evaluasi, simpan hasil ringkas seperti tabel perbandingan model ke `outputs/`. Tidak wajib mengunggah file model `.joblib` kecuali memang diperlukan untuk demonstrasi atau penggunaan ulang.

## Referensi (APA 7th edition)

### Dataset

Sutoyo, R., Chowanda, A., Achmad, S., Andangsari, E., Isa, S. M., Soetandar, J. P., Andres, J. R., Richard, R., Hadiwijaya, M. A., Andrews, D., & Pirdaus, F. P. (2022). *Product Reviews Dataset for Emotions Classification Tasks - Indonesian (PRDECT-ID) Dataset* (Version 1) [Data set]. Mendeley Data. https://doi.org/10.17632/574v66hf2v.1

### Artikel jurnal yang mendeskripsikan dataset

Sutoyo, R., Achmad, S., Chowanda, A., Andangsari, E. W., & Isa, S. M. (2022). PRDECT-ID: Indonesian product reviews dataset for emotions classification tasks. *Data in Brief, 44*, Article 108554. https://doi.org/10.1016/j.dib.2022.108554

## Keterbatasan

- Hasil pengujian berlaku untuk pembagian data dan dataset yang digunakan; hasil dapat berbeda pada marketplace, kategori, atau periode lain.
- Sarkasme, singkatan, bahasa informal, salah ketik, dan sentimen campuran dapat menimbulkan kesalahan klasifikasi.
- Evaluasi pada test set internal bukan bukti bahwa model akan memiliki kinerja yang sama pada seluruh ulasan e-commerce Indonesia.

## Catatan atribusi

Proyek ini menggunakan dataset PRDECT-ID yang dipublikasikan oleh para penulis dataset. Cantumkan sumber dataset dan artikel jurnal dalam laporan maupun presentasi. Proyek ini merupakan implementasi pembelajaran dan bukan publikasi resmi dari pembuat dataset.
