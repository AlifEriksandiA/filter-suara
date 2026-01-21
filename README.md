# Audio Noise Reduction using Moving Average Filter 🎧📉

Proyek ini adalah implementasi sederhana dari **Low Pass Filter** menggunakan metode **Moving Average (Running Mean)** dengan Python. Script ini bertujuan untuk membersihkan *noise* frekuensi tinggi dari file audio `.wav`.

## 📝 Deskripsi

Program ini membaca file audio mentah (`.wav`), memproses sinyal digitalnya, dan meredam frekuensi di atas ambang batas tertentu (*cutoff frequency*). Teknik yang digunakan adalah menghitung rata-rata berjalan (*running mean*) dari amplitudo sinyal, yang secara efektif memperhalus gelombang suara dan menghilangkan lonjakan kasar (noise).

**Skenario Penggunaan:**
Anda memiliki rekaman suara (`SuaraDenganNoise.wav`) yang terdengar kresek-kresek atau mendesis (frekuensi tinggi). Program ini akan menghaluskan suara tersebut dan menyimpannya sebagai file baru (`SuaraSetelahFilter.wav`).

## 🛠️ Tech Stack & Library

* **Python 3.x**
* **NumPy**: Untuk operasi array dan perhitungan matematika yang efisien.
* **Wave**: Library bawaan Python untuk membaca/menulis file audio format WAV.
* **Matplotlib**: (Opsional) Digunakan jika ingin memvisualisasikan gelombang suara.

## ⚙️ Cara Kerja Algoritma

1.  **Input**: Membaca file `SuaraDenganNoise.wav`.
2.  **Konversi**: Mengubah byte audio menjadi array NumPy (`interpret_wav`).
3.  **Kalkulasi Window (N)**: Menentukan lebar jendela *moving average* berdasarkan *cutoff frequency* (400.0 Hz) dan *sample rate* audio.
4.  **Filtering**: Menerapkan fungsi `running_mean` pada sinyal audio.
    * *Konsep*: Semakin besar window `N`, semakin halus sinyalnya (semakin rendah frekuensi yang lolos).
5.  **Output**: Menyimpan hasil sinyal yang sudah difilter ke `SuaraSetelahFilter.wav`.

## 🚀 Cara Menjalankan

### 1. Persiapan File
Pastikan Anda memiliki file audio bernama **`SuaraDenganNoise.wav`** di folder yang sama dengan script ini.

### 2. Instalasi Library
Jika belum menginstall NumPy, jalankan perintah:
```bash
pip install numpy matplotlib

```

### 3. Eksekusi Program

Jalankan file notebook atau script Python:

```bash
python filter_suara.py

```

*(Atau "Run All" jika menggunakan Jupyter Notebook/Google Colab)*

### 4. Hasil

Cek folder proyek Anda, akan muncul file baru bernama **`SuaraSetelahFilter.wav`** yang suaranya lebih "tumpul" atau bersih dari desis frekuensi tinggi.

## ⚠️ Catatan Teknis (Deprecation Warning)

Jika Anda melihat peringatan:
`DeprecationWarning: The binary mode of fromstring is deprecated...`

Itu karena fungsi `np.fromstring` pada versi NumPy terbaru disarankan diganti. Kode tetap berjalan normal, namun untuk *best practice* di masa depan, baris kode:

```python
channels = np.fromstring(raw_bytes, dtype=dtype)

```

Dapat diganti menjadi:

```python
channels = np.frombuffer(raw_bytes, dtype=dtype)

```

## 👤 Author

**Alif Eriksandi Agustino**

* Teknik Komputer - Universitas Brawijaya
* Topik: Digital Signal Processing (DSP)

---
