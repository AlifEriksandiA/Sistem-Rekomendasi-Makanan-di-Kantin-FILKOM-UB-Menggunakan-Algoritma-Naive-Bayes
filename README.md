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
