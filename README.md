# Garbage Classification with MobileNetV2

![TensorFlow](https://img.shields.io/badge/TensorFlow-2.16+-orange?style=for-the-badge&logo=tensorflow)
![Python](https://img.shields.io/badge/Python-3.10+-blue?style=for-the-badge&logo=python)
![Keras](https://img.shields.io/badge/Keras-3.0-red?style=for-the-badge&logo=keras)

Proyek *Deep Learning* klasifikasi sampah menggunakan arsitektur **MobileNetV2**, sistem ini mampu mengenali 12 jenis sampah berbeda.

---

## 📂 Sumber Dataset
Proyek ini menggunakan dataset publik yang tersedia di Kaggle:
**[Garbage Classification (12 Classes)](https://www.kaggle.com/datasets/mostafaabla/garbage-classification)** oleh Mostafa Abla.

### Kategori Kelas (12 Jenis)
1.  **Battery** (Baterai bekas)
2.  **Biological** (Sampah organik/makanan)
3.  **Brown-glass** (Kaca cokelat)
4.  **Cardboard** (Kardus)
5.  **Clothes** (Pakaian/Tekstil)
6.  **Green-glass** (Kaca hijau)
7.  **Metal** (Logam/Kaleng)
8.  **Paper** (Kertas)
9.  **Plastic** (Plastik)
10. **Shoes** (Sepatu)
11. **Trash** (Sampah residu umum)
12. **White-glass** (Kaca bening)

---

## ⚙️ Workflow Proyek
Pipeline pengembangan model dilakukan secara sistematis melalui tahapan berikut:

1.  **Data Acquisition & Audit:** Mengunduh dataset dan melakukan audit terhadap resolusi unik (heterogen) serta distribusi kelas untuk mendeteksi ketidakseimbangan data.
2.  **Preprocessing:** Transformasi citra ke ukuran $224 \times 224$ piksel dan penerapan augmentasi data untuk meningkatkan generalisasi model.
3.  **Transfer Learning:** Menggunakan MobileNetV2 sebagai *backbone* dengan bobot ImageNet. Tahap awal dilakukan dengan membekukan (*freeze*) base model dan hanya melatih lapisan *Classifier*.
4.  **Multi-Phase Fine-Tuning:** Membuka kunci lapisan blok konvolusi secara bertahap (5 tahap) dengan *learning rate* yang semakin kecil ($10^{-5}$) untuk mengoptimalkan akurasi tanpa merusak fitur dasar.
5.  **Model Export & Conversion:** Menyimpan model ke format `SavedModel`, lalu mengonversinya ke **TFLite** untuk Android/iOS dan **TensorFlow.js** untuk web browser.
6.  **Inference Testing:** Pengujian akhir menggunakan data testing serta gambar eksternal dari URL dan Google Drive API.

---

## 📈 Hasil Pemodelan (Ultimate Phase)
Setelah melalui proses *fine-tuning* bertahap, model mencapai performa luar biasa pada iterasi final:

| Metrik | Hasil Akurasi | 
|:---|:---:|
| **Training Accuracy** | **~98.0%** | 
| **Validation Accuracy** | **~94.7%** | 
| **Testing Accuracy** | **~95.0%** | 

*Hasil ini dicapai dengan batch size 8 dan optimasi Adam dengan Learning Rate Scheduler.*

---

