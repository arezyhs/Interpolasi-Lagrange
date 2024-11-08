# 📊 Studi Kasus: Prediksi Emisi CO₂ dengan Interpolasi Lagrange

Dalam studi kasus ini, kita menerapkan **Interpolasi Lagrange** untuk memprediksi emisi CO₂ berdasarkan konsumsi listrik dari bahan bakar fosil. Metode ini membantu kita memahami bagaimana interpolasi polinomial dapat digunakan untuk memperkirakan data di antara titik-titik yang ada.

## 📌 Langkah-Langkah Implementasi

### 1️⃣ Data Input
Dataset yang digunakan adalah:
- **`electricity_data`**: Data konsumsi listrik dari bahan bakar fosil dalam satuan TWh.
- **`co2_emission_data`**: Data emisi CO₂ terkait dalam satuan kiloton (kt).

### 2️⃣ Fungsi Pembentukan Polinomial Lagrange
Fungsi `lagrange_polynomial` digunakan untuk membentuk polinomial Lagrange secara simbolik menggunakan **SymPy** berdasarkan titik data terdekat yang dipilih. Fungsi ini membantu membentuk polinomial interpolasi yang digunakan untuk memprediksi emisi CO₂ pada titik target.

### 3️⃣ Interpolasi Lagrange
Fungsi `lagrange_interpolation` menghitung nilai interpolasi pada titik target tertentu (`x_target`) untuk berbagai orde. 
- Dengan memilih titik-titik terdekat sesuai dengan orde interpolasi, hasil prediksi bisa menjadi lebih akurat dan relevan dengan data sekitar titik target.
  
### 4️⃣ Evaluasi Prediksi dan Galat
Untuk setiap orde interpolasi, kita menghitung nilai prediksi pada titik data yang ada dan mengukur galatnya (selisih dengan nilai aktual).
- Hasil prediksi dan galatnya ditampilkan dalam tabel per orde interpolasi.
  
### 5️⃣ Metrik Evaluasi Error
Untuk setiap orde interpolasi, kita menghitung metrik evaluasi berikut:
- **Error Relatif**: Persentase rata-rata dari galat relatif.
- **Korelasi Pearson (R)**: Menunjukkan korelasi antara nilai aktual dan prediksi.
- **R-Squared**: Koefisien determinasi, menunjukkan seberapa baik model mendekati data.
- **MAPE**: Mean Absolute Percentage Error, mengukur kesalahan absolut dalam bentuk persentase.

### 6️⃣ Visualisasi Hasil Interpolasi
Kita membuat grafik interpolasi untuk setiap orde hingga batas maksimum yang diatur (`max_order`), beserta titik prediksi pada `x_target` untuk visualisasi yang lebih lengkap.

## 🔧 Parameter yang Dapat Diatur
- **`x_target`**: Titik prediksi (contoh: 213).
- **`max_order`**: Batas maksimum orde interpolasi yang ingin dihitung (contoh: hingga orde 3).
  
Pengaturan `max_order` dan `x_target` memudahkan dalam menentukan orde interpolasi dan titik prediksi yang diinginkan.

## 📈 Hasil dan Output

### 📊 Hasil Prediksi dan Galat untuk Setiap Orde
Untuk setiap orde dari 1 hingga `max_order`, hasil prediksi, galat, dan evaluasi error ditampilkan dalam tabel per orde. Hal ini memudahkan perbandingan antar orde dan memahami seberapa baik interpolasi pada setiap orde dalam mendekati data asli.

### 📉 Grafik Interpolasi
Grafik interpolasi menampilkan:
- **Kurva interpolasi untuk setiap orde** dari 1 hingga `max_order`.
- **Titik prediksi pada `x_target`** untuk setiap orde, dengan label hasil prediksi.
- **Titik data asli** sebagai acuan untuk visualisasi.

---

## 📂 Referensi Fungsi Utama
- **`lagrange_polynomial(x_values, y_values)`**: Membentuk polinomial Lagrange secara simbolis.
- **`lagrange_interpolation(x_values, y_values, x_target, order)`**: Menghitung nilai interpolasi untuk titik target dengan orde tertentu.
- **Tabel Evaluasi Error**: Memberikan evaluasi metrik error seperti Error Relatif, Korelasi Pearson (R), R-Squared, dan MAPE.

---

## 📌 Kesimpulan Studi Kasus
Studi ini menunjukkan bahwa **Interpolasi Lagrange dapat memberikan estimasi yang baik pada rentang data yang tersedia**. Kesimpulan utama adalah:
- **Orde yang Lebih Tinggi**: Memberikan hasil yang lebih baik pada data asli tetapi mungkin lebih rentan terhadap osilasi pada interval di luar rentang data.
- **Evaluasi Metrik Error**: Memberikan gambaran praktis mengenai akurasi model dalam pendekatan interpolasi.
- **Pemilihan Orde yang Optimal**: Orde lebih rendah sering kali cukup stabil dan dapat memberikan hasil yang baik dalam rentang data terbatas, sementara orde lebih tinggi memberikan ketelitian lebih baik pada data yang ada namun dapat rentan terhadap overfitting.

---

**Author:** Arezyhs
