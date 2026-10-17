# Panduan Mengunggah Proyek ke GitHub

## 1. Berkas yang sebaiknya masuk repository

Unggah berkas berikut:

- `README.md` — deskripsi proyek, cara menjalankan, metode, sumber dataset, dan referensi APA.
- `notebooks/studi_kasus_klasifikasi_sentimen.ipynb` — notebook utama, termasuk kode dan (setelah eksperimen dijalankan) output yang diperlukan.
- `reports/laporan.md` — draf laporan studi kasus.
- `requirements.txt` — daftar dependensi Python.
- `.gitignore` — mencegah file lokal, dataset mentah, cache, dan model besar ikut terunggah.
- `GITHUB_GUIDE.md` — panduan unggah ini (opsional, tetapi berguna untuk dokumentasi proyek).
- `outputs/model_comparison.csv` atau gambar hasil evaluasi — opsional, unggah setelah hasil eksperimen nyata tersedia.

## 2. Berkas yang tidak wajib diunggah

- **Dataset CSV mentah:** tidak perlu dimasukkan ke Git. Cantumkan tautan Mendeley Data/Hugging Face di README dan unduh saat diperlukan. Ini menjaga repository tetap ringan dan memudahkan atribusi sumber.
- **Model `.joblib`/`.pkl`:** tidak wajib untuk tugas klasifikasi berbasis notebook; unggah hanya jika dosen meminta model siap pakai atau demonstrasi prediksi.
- **File sementara, cache, atau environment:** jangan diunggah.

Pastikan notebook dapat memuat dataset dari sumber yang dicantumkan atau berikan instruksi jelas untuk mengunggah CSV secara manual jika tautan unduh gagal.

## 3. Membuat repository

1. Masuk ke GitHub dan pilih **New repository**.
2. Gunakan nama, misalnya `studi-kasus-klasifikasi-sentimen`.
3. Tambahkan deskripsi: `Klasifikasi sentimen ulasan produk berbahasa Indonesia menggunakan TF-IDF dan machine learning`.
4. Pilih **Public** jika repository memang akan dikumpulkan sebagai tautan publik; pilih **Private** jika diminta dosen atau sesuai kebutuhan privasi.
5. Jika mengunggah file lokal yang sudah memiliki README, sebaiknya buat repository kosong agar tidak terjadi konflik awal.

## 4. Unggah melalui browser GitHub

1. Ekstrak ZIP proyek di komputer.
2. Buka repository yang baru dibuat.
3. Pilih **Add file → Upload files**.
4. Seret berkas dan folder yang diperlukan ke halaman upload. Pastikan struktur `notebooks/` dan `reports/` tetap terjaga.
5. Tulis commit message, misalnya `Add sentiment classification study case`.
6. Pilih **Commit changes**.
7. Buka `README.md` di GitHub dan periksa apakah judul, struktur folder, tabel, tautan, dan dua referensi APA tampil dengan benar.

## 5. Simpan notebook Colab ke GitHub

Jika notebook dikerjakan di Google Colab:

1. Buka notebook di Colab.
2. Pilih **File → Save a copy in GitHub** (label menu bisa berbeda sedikit).
3. Hubungkan akun GitHub jika diminta.
4. Pilih repository dan branch yang benar.
5. Gunakan path `notebooks/studi_kasus_klasifikasi_sentimen.ipynb` jika menyimpan notebook final.
6. Gunakan commit message seperti `Update notebook with experiment results`.
7. Setelah tersimpan, buka notebook di GitHub dan pastikan kode serta output penting tersedia.

Jika notebook final disimpan di path yang sama, pastikan tidak ada dua salinan dengan nama berbeda yang membingungkan.

## 6. Setelah eksperimen selesai

- Isi tabel hasil pada README dengan metrik aktual.
- Perbarui kesimpulan laporan sesuai hasil model.
- Jika diperlukan, tambahkan tabel hasil ke `outputs/`.
- Periksa kembali sitasi dataset dan jurnal dalam format APA 7.
- Jangan mencantumkan angka evaluasi yang belum dihasilkan dari notebook.
