# SIMUTEH – Proyek Computer Vision

Repositori ini merupakan dokumentasi pengerjaan praktikum Computer Vision untuk proyek **SIMUTEH (Sistem Identifikasi Bercak Daun Teh)**. Proyek ini berfokus pada pengolahan citra dan analisis bercak pada daun teh yang berkaitan dengan penyakit cacar daun teh (*Exobasidium vexans*).

Pengerjaan mencakup tahapan praktikum P1–P4 serta evaluasi P5–P6, mulai dari pembentukan dataset, prapemrosesan citra, deteksi tepi, hingga segmentasi dan analisis bercak.

## Identitas Mahasiswa

- **Nama:** Mochammad Bimo Ibrahim
- **NIM:** 2330511039
- **Program Studi:** Teknik Informatika
- **Kelas:** 7A
- **SEED:** 1039

## Susunan Direktori

Berikut gambaran susunan berkas yang digunakan dalam proyek:

```text
simuteh-2330511039/
│
├── data/
│   └── sintetis/
│       ├── mask_daun/
│       ├── mask_bercak/
│       └── label.csv
│
├── notebook/
│   ├── B1.ipynb
│   ├── B2.ipynb
│   ├── B3.ipynb
│   ├── B4.ipynb
│   ├── B5.ipynb
│   ├── P5_tepi.ipynb
│   └── P6_morfologi.ipynb
│
├── src/
│   ├── buat_dataset_sintetis.py
│   ├── utils_cv.py
│   ├── praproses.py
│   ├── utils_tepi.py
│   └── bercak.py
│
├── hasil/
│   ├── param_praproses.json
│   └── param_bercak.json
│
├── requirements.txt
└── README.md
```

*Catatan: Struktur di atas merupakan rancangan direktori. Sesuaikan nama dan isi berkas dengan kondisi repositori yang benar-benar tersedia.*

## Lingkup Pengerjaan

### P1–P4: Pengolahan dan Prapemrosesan Citra

Tahapan awal dilakukan untuk mempersiapkan citra daun teh agar dapat digunakan dalam proses analisis selanjutnya. Kegiatan yang dilakukan meliputi:

- Pembuatan dataset sintetis menggunakan SEED berdasarkan NIM.
- Pengamatan kanal warna untuk mengetahui kanal yang dapat memperlihatkan bercak dengan lebih jelas.
- Penerapan metode perbaikan kualitas citra.
- Pengujian beberapa jenis penapis untuk mengurangi gangguan pada citra.
- Penyusunan rangkaian prapemrosesan sebagai dasar tahapan berikutnya.

### P5: Deteksi Tepi

Tahap ini membahas identifikasi batas objek dan perubahan intensitas pada citra daun teh. Metode yang dipelajari meliputi:

- Sobel.
- Prewitt.
- Laplacian of Gaussian (LoG).
- Canny.
- Perbandingan hasil deteksi menggunakan metrik evaluasi.

### P6: Morfologi dan Analisis Bercak

Tahap berikutnya berfokus pada pengolahan citra biner untuk memperoleh area bercak yang lebih sesuai dengan objek sebenarnya. Prosesnya mencakup:

- Erosion dan dilation.
- Opening dan closing.
- Pengujian structuring element.
- Connected component labeling.
- Pengukuran karakteristik komponen bercak.
- Pengelompokan tingkat kondisi daun.
- Evaluasi hasil prediksi terhadap data acuan.

## Lingkungan Pengembangan

Proyek dikerjakan menggunakan beberapa perangkat dan pustaka berikut:

- **Platform:** Google Colab.
- **Bahasa pemrograman:** Python.
- **Pengolahan citra:** OpenCV.
- **Analisis data:** NumPy dan Pandas.
- **Visualisasi:** Matplotlib.
- **Penyimpanan kode:** GitHub.

## Cara Menjalankan Proyek

1. Buka repositori proyek melalui GitHub.
2. Salin alamat repositori.
3. Buka Google Colab.
4. Jalankan perintah berikut untuk mengambil repositori:

```bash
!git clone URL_REPOSITORY_KAMU
```

5. Masuk ke direktori proyek:

```python
%cd /content/simuteh-2330511039
```

6. Pasang pustaka yang diperlukan:

```python
!pip install -r requirements.txt
```

7. Apabila dataset belum tersedia, jalankan program pembentukan dataset sesuai petunjuk pada notebook atau repositori.
8. Buka notebook sesuai tahapan praktikum.
9. Jalankan seluruh sel secara berurutan menggunakan **Runtime → Run all**.

## Dokumentasi Hasil Eksperimen

Hasil pengujian P1–P4 dan P5–P6 akan dicatat berdasarkan eksperimen yang dijalankan. Dokumentasi dapat berupa:

- Gambar hasil pengolahan citra.
- Grafik perbandingan metode.
- Tabel hasil evaluasi.
- Parameter metode yang digunakan.
- Analisis kesalahan dan keterbatasan sistem.

Angka evaluasi dan parameter akhir akan dicantumkan setelah seluruh pengujian selesai dilakukan.

## Tujuan Proyek

Proyek SIMUTEH diharapkan dapat menjadi penerapan teknik Computer Vision dalam membantu proses identifikasi bercak pada daun teh melalui pengolahan citra digital. Hasil pengerjaan juga digunakan untuk memahami tahapan analisis citra, mulai dari prapemrosesan hingga evaluasi hasil deteksi.

---

**Repositori Praktikum Computer Vision – Teknik Informatika**  
**Universitas Muhammadiyah Sukabumi (UMMI)**
