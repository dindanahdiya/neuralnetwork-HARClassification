# **Human Activity Recognition with Backpropagation from Scratch**
## Ringkasan Proyek
Proyek ini mengimplementasikan Backpropagation dari Nol untuk klasifikasi Human Activity Recognition (HAR) dataset (OpenPose). Model dikembangkan dari awal tanpa menggunakan framework deep learning siap pakai. Selain itu, perhitungan backpropagation juga dilakukan secara manual menggunakan Excel, untuk memahami proses pembelajaran jaringan saraf tiruan secara mendalam.

## Deskripsi Dataset
Dataset terdiri dari 2.826 sampel dan 37 fitur, yang terdiri dari 36 kolom numerik yang merepresentasikan koordinat sendi tubuh manusia (x, y) serta 1 kolom kategorikal sebagai label aktivitas. Aktivitas yang diklasifikasikan meliputi:
- Stand (Berdiri) – 26.3%
- Walk (Berjalan) – 25.5%
- Wave (Melambaikan tangan) – 24.5%
- Squat (Jongkok) – 23.6%

## Arsitektur Jaringan Saraf Tiruan
Lapisan Input: 36 neuron (koordinat x, y tubuh manusia)
Lapisan Tersembunyi: 9 neuron, aktivasi Sigmoid
Lapisan Output: 4 neuron (1 untuk setiap kelas), aktivasi Sigmoid
Metode Pelatihan: Algoritma Backpropagation
Optimasi: Gradient Descent
Hiperparameter:
Learning Rate: 0.07
Epochs: 1000

## Perhitungan Manual Backpropagation
Untuk memverifikasi keakuratan implementasi backpropagation, dilakukan perhitungan manual menggunakan Excel. Dataset dinormalisasi menggunakan RobustScaler, lalu parameter utama seperti bobot (W1, W2) dan bias (b1, b2) dioptimalkan dalam 9 epoch pelatihan, dengan hasil loss sebesar 0.1418 dan akurasi 100% pada sampel kecil sebagai validasi perhitungan.

## Evaluasi Performa Model
| **Kelas**                  | **Precision** | **Recall** | **F1-Score** | **Akurasi** |  
|----------------------------|--------------|------------|-------------|------------|  
| **Squat**                  | 1.00         | 0.99       | 1.00        | 1.00       |  
| **Stand**                  | 0.99         | 0.97       | 0.98        | 0.99       |  
| **Walk**                   | 0.99         | 0.97       | 0.98        | 0.99       |  
| **Wave**                   | 1.00         | 1.00       | 1.00        | 1.00       |  
| **Akurasi Multi-label Keseluruhan** | **98.23%** | - | - | - |  			

## Analisis Hasil Model
Berdasarkan hasil evaluasi, model menunjukkan performa sangat baik, dengan akurasi keseluruhan sebesar 98.23%. Berikut beberapa poin analisis:
1. Performa Kelas Individu
   - Model berhasil mengenali kelas "Wave" dengan sempurna (Precision, Recall, dan F1-Score = 1.00).
   - Kelas "Squat" memiliki recall 0.99, menunjukkan ada sedikit kesalahan dalam mengenali beberapa sampel.
   - Kelas "Stand" dan "Walk" memiliki sedikit kesalahan klasifikasi dengan recall 0.97, menandakan beberapa sampel yang seharusnya masuk ke kelas ini diklasifikasikan ke kelas lain.
2. Potensi Penyebab Kesalahan
   - Kesamaan pola koordinat pada pose Stand dan Walk bisa menyebabkan model sulit membedakan keduanya.
   - Data yang kurang seimbang dapat menyebabkan kelas dengan jumlah data lebih sedikit memiliki performa yang sedikit lebih rendah.
   - Variasi dalam dataset mungkin tidak cukup tinggi, sehingga model kesulitan dalam menangkap perbedaan kecil antar kelas.
3. Rekomendasi Perbaikan
   - Augmentasi data untuk meningkatkan variasi dalam pose tubuh.
   - Eksperimen dengan arsitektur yang lebih kompleks, seperti menambah jumlah neuron atau hidden layer.
   - Menerapkan teknik balancing data tambahan seperti SMOTE untuk meningkatkan generalisasi model.
