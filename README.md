# Sistem Rekomendasi Makanan di Kantin Filkom UB Menggunakan Algoritma Naive Bayes 🍽️

Proyek ini adalah aplikasi berbasis Python sederhana yang bertujuan untuk memberikan rekomendasi menu makanan di Kantin Fakultas Ilmu Komputer (FILKOM) Universitas Brawijaya. Sistem ini menggunakan algoritma **Naive Bayes** untuk memprediksi makanan yang paling sesuai dengan preferensi pengguna.

## 📝 Deskripsi

Sistem ini bekerja dengan mempelajari pola dari **Data Latih** yang berisi riwayat karakteristik makanan (harga, rasa, tekstur, popularitas) dan nama makanannya. Ketika pengguna memasukkan preferensi mereka, sistem akan menghitung probabilitas untuk setiap menu dan menampilkan 3 rekomendasi teratas dengan skor tertinggi.

## 🚀 Fitur

* **Input Preferensi Pengguna**: Memungkinkan pengguna memilih kriteria makanan yang diinginkan.
* **Rekomendasi Cerdas**: Menggunakan probabilitas statistik, bukan sekadar pencocokan kata kunci (keyword matching).
* **Top 3 Ranking**: Menampilkan tiga opsi terbaik agar pengguna memiliki alternatif.
* **Skor Probabilitas**: Menampilkan skor kalkulasi untuk transparansi hasil prediksi.

## 🧠 Algoritma & Metode

Program ini menerapkan **Naive Bayes Classifier** dengan teknik **Laplace Smoothing**.

1.  **Prior Probability**: Menghitung peluang kemunculan setiap jenis makanan berdasarkan data latih.
2.  **Likelihood**: Menghitung peluang setiap fitur (budget, selera, dll) muncul pada makanan tertentu.
3.  **Laplace Smoothing**: Kode ini menggunakan penambahan nilai konstanta (+1 pada pembilang dan +4 pada penyebut) untuk menghindari *zero probability* (peluang nol) jika ada kombinasi fitur yang belum pernah muncul di data latih.

### Atribut Data (Fitur)
Sistem memproses rekomendasi berdasarkan 4 parameter utama:
* **Budget**: `murah`, `menengah`, `mahal`
* **Selera**: `pedas`, `sedang`, `tidak pedas`
* **Karakteristik**: `crispy`, `gurih`, `berkuah`, `kering`
* **Popularitas**: `populer`, `biasa`

## 📂 Struktur Data Latih

Data latih disimpan secara *hardcoded* di dalam program (list `data_latih`). Contoh data:
```python
['murah', 'tidak pedas', 'gurih', 'biasa', 'Indomie Goreng']
['murah', 'pedas', 'berkuah', 'populer', 'Mie Ayam']
```

## 💻 Cara Menjalankan Program

### Prasyarat
* **Python 3.x** terinstal di komputer Anda.
* **Tidak memerlukan library eksternal** (hanya menggunakan library bawaan python yaitu `collections`).

### Langkah-langkah
1.  Clone atau download repository ini.
2.  Buka terminal atau command prompt (CMD/PowerShell).
3.  Arahkan direktori ke tempat file disimpan.
4.  Jalankan perintah berikut:

```bash
python nama_file.py
```

### Berikut adalah simulasi interaksi program ketika dijalankan di terminal:

Nama kamu siapa? Alif
Masukkan budget kamu (murah/menengah/mahal): murah
Kamu suka pedas atau tidak pedas? (pedas/sedang/tidak pedas): pedas
Karakteristik makanan yang kamu suka? (crispy/gurih/berkuah/kering): berkuah
Apakah kamu ingin makanan populer? (ya/tidak): ya

Halo Alif, berikut rekomendasi makanan untukmu:
- Mie Ayam (skor probabilitas: 0.004210)
- Mie yamin (skor probabilitas: 0.001050)
- Indomie Ayam Geprek (skor probabilitas: 0.000850)

👉 Rekomendasi utama untuk kamu adalah: Mie Ayam 🍽

👤 Author
1. Alif Eriksandi Agustino
2. Alif Aryasatya Rofiq
3. Balada Raja Baskara
4. Andi Muhammad Fadli

Teknik Komputer - Universitas Brawijaya
