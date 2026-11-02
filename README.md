# Evaluasi Praktikum Computer Vision (Pertemuan 1 - 4)
**Studi Kasus SIMUTEH:** Sistem Pemeriksaan Mutu Daun Teh Berbasis Citra (Deteksi Bercak Cacar Daun Teh *Exobasidium vexans*)

## Identitas Mahasiswa
- **Nama:** Mochammad Bimo Ibrahim
- **NIM:** 2330511039
- **Kelas:** 7A
- **SEED Dataset Sintetis:** 1039
- **Program Studi:** Teknik Informatika, Universitas Muhammadiyah Sukabumi

---

## Penjelasan Tugas
Tugas ini merupakan Evaluasi Pertemuan 1–4 pada mata kuliah Computer Vision untuk membangun tahap awal *pipeline* praproses citra pada sistem **SIMUTEH** (Sistem Pemeriksaan Mutu Daun Teh Berbasis Citra). Sistem ini dirancang untuk membantu kelompok tani teh rakyat di Kabupaten Sukabumi dalam memisahkan daun sehat dari daun yang terserang penyakit cacar daun teh (*Exobasidium vexans*) secara lebih konsisten, cepat, dan objektif.

Praktikum ini mencakup 5 sub-tugas utama:
1. **Bagian 1 (Formulasi Masalah & Etika):** Memetakan masalah fisik penyortiran daun teh ke dalam domain Computer Vision, merancang *pipeline* 6 tahap, serta mengidentifikasi risiko *Responsible Computer Vision* dan AIK (kejujuran data & kerahasiaan lokasi/metadata petani).
2. **Bagian 2 (Pembentukan Citra & Kanal Warna):** Menghitung proyeksi kamera, resolusi, dan kebutuhan memori, serta menguji 8 kanal warna (RGB, keabuan, HSV) di 5 kondisi pencahayaan untuk menemukan kanal paling informatif dalam memisahkan bercak penyakit dari daun sehat.
3. **Bagian 3 (Histogram & Perbaikan Citra):** Mendiagnosis mutu citra melalui histogram statistik, serta menguji berbagai teknik perbaikan kontras (Gamma, Peregangan Persentil, CLAHE) untuk mengatasi gangguan pencahayaan ekstrem seperti bayangan dan silau.
4. **Bagian 4 (Konvolusi & Penapisan Spasial):** Mengimplementasikan operasi konvolusi/korelasi spasial, membandingkan penapis (Rerata, Gaussian, Median) terhadap derau sensor/garam-merica, serta menganalisis *trade-off* antara kualitas citra (PSNR), pengawetan detail bercak kecil ($\text{dI}$), dan efisiensi waktu komputasi.
5. **Bagian 5 (Integrasi Rangkaian Praproses):** Menyusun dan menguji modul praproses terintegrasi (`src/praproses.py`) dengan parameter final yang efisien untuk digunakan pada tahap segmentasi dan klasifikasi selanjutnya.

---

## Struktur Repositori
- `notebook/` : Notebook pengerjaan per bagian (B1 sampai B5).
- `src/` : Kode sumber (`buat_dataset_sintetis.py`, `utils_cv.py`, `praproses.py`).
- `hasil/` : Tabel, grafik, panel visual, dan parameter `param_praproses.json`.
- `requirements.txt` : Catatan versi pustaka yang digunakan.

---

## Ringkasan Hasil Eksperimen

- **Kanal Warna Terbaik (Bagian 2):** Kanal **R (Red)** secara konsisten memberikan nilai Kontras Bercak (KB) tertinggi (rerata KB kelas berat = 10,14) karena klorofil daun sehat menyerap cahaya merah secara kuat, sedangkan area bercak memantulkannya.
- **Perbaikan Citra per Kondisi (Bagian 3):** 
  - **Gelap:** Gamma $\gamma = 0,5$
  - **Terang:** Gamma $\gamma = 1,8$ (KB naik $3,29 \to 3,61$)
  - **Kontras Rendah:** Peregangan persentil 2–98 (KB naik $1,97 \to 2,11$)
  - **Bayangan:** CLAHE pada kanal V dengan `clipLimit=2.0`, `tileGridSize=4x4` (KB naik $1,62 \to 2,08$)
- **Penapisan Spasial & Pengawetan Detail (Bagian 4):**
  - Penapis **Median $3 \times 3$** terpilih sebagai *trade-off* terbaik untuk meredam derau garam-merica 4% (PSNR $48,18\text{ dB}$, waktu $0,10\text{ ms}$, KB $51,42$) serta menaikkan PSNR citra kondisi normal.
  - Penggunaan kernel median besar (kernel 15) menghapus detail bercak penyakit berukuran kecil (*over-smoothing*).
- **Integrasi Praproses Final (Bagian 5):**
  - Rangkaian praproses final berhasil menaikkan nilai KB pada seluruh kondisi pencahayaan: **Gelap (+72,16%)**, **Normal (+69,83%)**, **Terang (+65,57%)**, **Kontras Rendah (+14,86%)**, dan **Bayangan (+3,51%)**.
  - Mampu menurunkan simpangan baku ($\sigma$) area daun sehat di semua kondisi tanpa menimbulkan bercak palsu (*false positive*).

---

## Parameter Praproses Final
Parameter final tersimpan di `hasil/param_praproses.json`:
```json
{
  "lebar": 640,
  "gamma": 1.0,
  "clahe_clip": 2.0,
  "clahe_tile": 4,
  "penapis": "median",
  "kernel": 3,
  "sigma": 1.0,
  "tajam_k": 0.0
}
