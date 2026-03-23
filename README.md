# 🐾 Big Cats Classifier with CNN

Proyek ini merupakan implementasi model Convolutional Neural Network (CNN) untuk klasifikasi gambar tiga jenis kucing besar: **Cheetah**, **Lion**, dan **Tiger**. Proyek mencakup proses pelatihan model, evaluasi performa, serta konversi model ke berbagai format untuk keperluan deployment.

---

## 📁 Struktur Proyek

```
├── checkpoints/              # Model checkpoint (.keras) untuk val_accuracy dan val_loss
├── datasets/                # Dataset terstruktur (train/val/test)
│   ├── train/
│   ├── val/
│   └── test/
├── saved_model/             # Model dalam format TensorFlow SavedModel
├── tfjs_model/              # Model dalam format TensorFlow.js
├── tflite/                  # Model dalam format TensorFlow Lite
│   ├── model_loss.tflite
│   └── labels.txt
├── notebook.ipynb           # Notebook utama proyek
├── requirements.txt         # Daftar dependency Python
└── README.md                # Dokumentasi proyek ini
```

---

## 🚀 Ringkasan Proyek

- Model CNN dilatih menggunakan dataset gambar kucing besar yang dibagi menjadi **train**, **val**, dan **test**.
- Pelatihan menggunakan strategi:
  - `EarlyStopping` untuk mencegah overfitting
  - `ReduceLROnPlateau` untuk menyesuaikan learning rate
  - Checkpointing berdasarkan `val_accuracy` dan `val_loss`

> ⏱️ **Checkpoint terbaik**
>
> - **val_loss** (epoch ke-5): `val_loss = 0.2668` | `val_accuracy = 95.58%`
> - **val_accuracy** (epoch ke-11): `val_accuracy = 95.98%` | `val_loss = 0.3180`

---

## 📊 Evaluasi Model

Diuji menggunakan 126 gambar dari 3 kelas:

| Model                     | Akurasi   | F1-Score Rata-rata |
|---------------------------|-----------|---------------------|
| 🏆 `val_loss` terbaik     | **95.24%** | **0.9524**          |
| 🎯 `val_accuracy` terbaik | 94.44%    | 0.9450              |

Model `val_loss` menunjukkan performa prediksi **lebih stabil dan generalisasi lebih baik**, sehingga digunakan untuk proses konversi dan deployment.

---

## 🔁 Format Model

Model terbaik (`val_loss`) telah dikonversi ke format berikut:

| Format        | Lokasi                              | Keterangan                         |
|---------------|-------------------------------------|------------------------------------|
| `SavedModel`  | `saved_model/bigcats_loss_model/`   | Untuk deploy via TensorFlow        |
| `TFLite`      | `tflite/model_loss.tflite`          | Untuk perangkat mobile/embedded    |
| `TF.js`       | `tfjs_model/`                       | Untuk deployment di browser (web)  |

---

## 💡 Cara Menjalankan

1. **Clone repositori dan install dependensi**  
   ```bash
   pip install -r requirements.txt
   ```

2. **Jalankan Notebook**  
   Buka `notebook.ipynb` untuk melihat keseluruhan proses dari pelatihan, evaluasi, hingga konversi model.

---

## 📦 Dataset

Dataset sudah disusun ke dalam direktori:

```bash
datasets/
├── train/    # Gambar untuk training
├── val/      # Gambar untuk validasi
└── test/     # Gambar untuk testing
```

---

## 📈 Visualisasi Training

Log pelatihan tersimpan dalam folder `logs/` dan dapat divisualisasikan dengan TensorBoard:

```bash
tensorboard --logdir=logs/
```

---

## 📝 Catatan

- Model terbaik (`val_loss`) dipilih karena menunjukkan **kesalahan prediksi paling rendah** dan **generalisasi paling baik** terhadap data uji.
- Evaluasi menunjukkan performa **stabil dan akurat** untuk semua kelas, sehingga siap digunakan dalam berbagai skenario klasifikasi gambar.

