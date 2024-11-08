# 📊 Studi Kasus: Prediksi Emisi CO₂ dengan Interpolasi Lagrange

Dalam studi kasus ini, kita menerapkan **Interpolasi Lagrange** untuk memprediksi emisi CO₂ berdasarkan konsumsi listrik dari bahan bakar fosil. Metode ini memungkinkan kita memperkirakan nilai di antara titik-titik data yang sudah ada menggunakan interpolasi polinomial.

## 📌 Langkah-Langkah Implementasi

### 1️⃣ Data Input
Dataset yang digunakan adalah:
- **`electricity_data`**: Data konsumsi listrik dari bahan bakar fosil dalam satuan TWh.
- **`co2_emission_data`**: Data emisi CO₂ terkait dalam satuan kiloton (kt).

### 2️⃣ Fungsi Pembentukan Polinomial Lagrange
Fungsi `lagrange_polynomial` membentuk polinomial Lagrange secara simbolik menggunakan **SymPy** berdasarkan titik data terdekat yang dipilih. Fungsi ini membantu membentuk polinomial interpolasi yang digunakan untuk memprediksi emisi CO₂ pada titik target.

### 3️⃣ Interpolasi Lagrange
Fungsi `lagrange_interpolation` menghitung nilai interpolasi pada titik target tertentu (`x_target`) untuk berbagai orde:
- Memilih titik-titik terdekat sesuai dengan orde interpolasi untuk mencapai hasil prediksi yang lebih akurat.
  
### 4️⃣ Batas Error Lagrange Manual
Fungsi `lagrange_error_bound_manual` menghitung batas error Lagrange secara manual. Batas error ini didasarkan pada turunan ke-(n+1) dari polinomial interpolasi dan produk jarak dari titik target ke setiap titik data terdekat. Batas error ini memberikan perkiraan maksimum galat untuk setiap orde interpolasi.

### 5️⃣ Evaluasi Prediksi dan Galat
Untuk setiap orde interpolasi, kita menghitung nilai prediksi pada setiap titik data asli dan mengukur galatnya (selisih dengan nilai aktual).
- Hasil prediksi dan galat ditampilkan dalam tabel untuk setiap orde interpolasi.

### 6️⃣ Metrik Evaluasi Error
Untuk setiap orde interpolasi, kita menghitung metrik evaluasi berikut:
- **Error Relatif (%)**: Rata-rata persentase dari galat relatif.
- **Korelasi Pearson (R)**: Mengukur korelasi antara nilai aktual dan prediksi.
- **R-Squared**: Koefisien determinasi yang menunjukkan seberapa baik model menjelaskan variabilitas data.
- **MAPE (%)**: Mean Absolute Percentage Error, menunjukkan kesalahan absolut dalam bentuk persentase.

### 7️⃣ Visualisasi Hasil Interpolasi
Grafik interpolasi dibuat untuk setiap orde hingga batas maksimum yang diatur (`max_order`), beserta titik prediksi pada `x_target` untuk memberikan visualisasi yang komprehensif.

## 🔧 Parameter yang Dapat Diatur
- **`x_target`**: Titik prediksi (contoh: 213).
- **`max_order`**: Batas maksimum orde interpolasi yang ingin dihitung (contoh: hingga orde 3).
  
Pengaturan `max_order` dan `x_target` memungkinkan fleksibilitas dalam menentukan orde interpolasi dan titik prediksi.

## 📈 Hasil dan Output

### 📊 Hasil Prediksi dan Galat untuk Setiap Orde
Untuk setiap orde dari 1 hingga `max_order`, hasil prediksi, galat, dan evaluasi error ditampilkan dalam tabel per orde. Hal ini memudahkan untuk membandingkan akurasi antar orde dan memahami seberapa baik interpolasi pada setiap orde dalam mendekati data asli.

### 📉 Grafik Interpolasi
Grafik interpolasi menampilkan:
- **Kurva interpolasi untuk setiap orde** dari 1 hingga `max_order`.
- **Titik prediksi pada `x_target`** untuk setiap orde, dengan label hasil prediksi.
- **Titik data asli** sebagai acuan untuk visualisasi.

---

## 📂 Referensi Fungsi Utama
- **`lagrange_polynomial(x_values, y_values)`**: Membentuk polinomial Lagrange secara simbolis.
- **`lagrange_interpolation(x_values, y_values, x_target, order)`**: Menghitung nilai interpolasi untuk titik target dengan orde tertentu.
- **`lagrange_error_bound_manual(x_values, y_values, x_target, order)`**: Menghitung batas error Lagrange secara manual menggunakan finite differences untuk estimasi turunan.
- **`calculate_error_metrics(y_actual, y_pred)`**: Menghitung metrik error seperti Error Relatif, Korelasi Pearson (R), R-Squared, dan MAPE.

---

## 📌 Kesimpulan Studi Kasus
Studi ini menunjukkan bahwa **Interpolasi Lagrange dapat memberikan estimasi yang baik pada rentang data yang tersedia**. Beberapa kesimpulan utama adalah:
- **Interpolasi Orde Tinggi**: Memberikan hasil yang lebih baik pada data asli tetapi mungkin lebih rentan terhadap osilasi pada interval di luar rentang data.
- **Evaluasi Metrik Error**: Memberikan gambaran praktis mengenai akurasi model dalam pendekatan interpolasi.
- **Pemilihan Orde yang Optimal**: Interpolasi orde rendah sering kali cukup stabil dan dapat memberikan hasil yang baik dalam rentang data terbatas, sementara orde yang lebih tinggi memberikan ketelitian lebih baik pada data yang ada namun dapat rentan terhadap overfitting.

---

**Author:** Arezyhs
