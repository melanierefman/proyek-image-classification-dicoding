# Proyek Image Classification Dicoding

Proyek ini bertujuan untuk membangun model klasifikasi gambar menggunakan dataset bunga dari Kaggle. Model ini dirancang untuk mengklasifikasikan gambar bunga ke dalam lima kategori: daisy, dandelion, roses, sunflowers, dan tulips. Model dibangun dengan memanfaatkan transfer learning menggunakan arsitektur pre-trained VGG16.

## **Pendahuluan**

Klasifikasi gambar merupakan salah satu tugas penting dalam bidang computer vision. Proyek ini mengimplementasikan solusi berbasis deep learning untuk memproses gambar bunga dan mengelompokkan gambar tersebut berdasarkan jenis bunganya. Dataset yang digunakan diambil dari Kaggle dan mencakup lima jenis bunga.

## **Tahapan Proyek**

### **1. Import Dataset**
Dataset diunduh menggunakan Kaggle API dan diekstrak ke dalam lingkungan Colab untuk proses lebih lanjut. Dataset ini terdiri dari gambar-gambar bunga yang disusun dalam folder berdasarkan labelnya.

### **2. Eksplorasi Dataset**
Dataset dianalisis untuk:
- Melihat distribusi gambar pada setiap kelas.
- Memeriksa kelengkapan dataset (missing values).
- Visualisasi contoh gambar dari setiap kelas untuk memahami karakteristik visual dataset.

### **3. Persiapan Data**
Dataset dibagi menjadi dua subset:
- **Train set (80%)**
- **Test set (20%)**

Pembagian dilakukan secara terpisah untuk setiap kelas, sehingga data setiap kelas memiliki proporsi yang seimbang.

Augmentasi gambar juga diterapkan pada data training menggunakan `ImageDataGenerator` untuk meningkatkan keragaman dataset dan membantu model dalam proses generalisasi.

### **4. Modeling**
Model dikembangkan menggunakan arsitektur VGG16 yang telah di-pretrain pada dataset ImageNet:
- **Layer Pre-trained**: Bagian awal VGG16 digunakan sebagai ekstraktor fitur.
- **Fine-tuning**: Layer akhir dari model di-train ulang agar lebih sesuai dengan dataset bunga.
- **Custom Layers**: Layer tambahan seperti Convolutional, Batch Normalization, Dropout, dan Dense ditambahkan untuk meningkatkan performa klasifikasi.

### **5. Training Model**
Model dilatih menggunakan dataset training dengan parameter berikut:
- **Optimizer**: Adam optimizer dengan learning rate rendah untuk stabilitas training.
- **Loss Function**: Categorical crossentropy untuk multi-class classification.
- **Metrics**: Akurasi.

### **6. Evaluasi Model**
Hasil training dievaluasi dengan:
- **Grafik Akurasi**: Membandingkan akurasi training dan validasi.
- **Grafik Loss**: Membandingkan loss training dan validasi.

### **7. Menyimpan Model**
Model yang dilatih disimpan dalam beberapa format:
- **SavedModel**: Format default TensorFlow.
- **TF-Lite**: Untuk deployment pada perangkat mobile.
- **TFJS**: Untuk deployment berbasis web.

## **Hasil Akhir**
Model berhasil mencapai akurasi yang baik pada dataset validasi. Dengan menyimpan model dalam berbagai format, solusi ini dapat digunakan pada berbagai platform, termasuk web dan mobile.

## **Cara Menjalankan Proyek**

1. **Unduh Dataset**:
   Pastikan Anda memiliki file `kaggle.json` untuk mengakses dataset dari Kaggle.
   ```python
   from google.colab import files
   files.upload()

   !mkdir -p ~/.kaggle
   !cp kaggle.json ~/.kaggle/
   !chmod 600 ~/.kaggle/kaggle.json
   !kaggle datasets download -d rahmasleam/flowers-dataset/
   ```
2. **Ekstrak Dataset**:
   ```python
   from zipfile import ZipFile
   with ZipFile("flowers-dataset.zip", 'r') as zip:
       zip.extractall()
   ```
3. **Jalankan Notebook**:
   Ikuti alur kode dalam notebook untuk eksplorasi data, preprocessing, dan training model.

## **Teknologi yang Digunakan**

- **Python**: Bahasa pemrograman utama.
- **TensorFlow & Keras**: Framework untuk membangun dan melatih model deep learning.
- **OpenCV**: Untuk memproses gambar.
- **Matplotlib & Seaborn**: Untuk visualisasi data.
- **Scikit-learn**: Untuk pembagian data dan menghitung class weights.

## **Dataset**
Dataset yang digunakan dapat diakses melalui tautan berikut: [Flowers Dataset](https://www.kaggle.com/datasets/rahmasleam/flowers-dataset).

## **Kontributor**
- Nama: Melanie Sayyidina Sabrina Refman
