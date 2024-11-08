# 📊 Studi Kasus: Prediksi Emisi CO₂ dengan Interpolasi Lagrange

Studi kasus ini mengeksplorasi penggunaan **Interpolasi Lagrange** untuk memprediksi emisi CO₂ berdasarkan konsumsi listrik dari bahan bakar fosil. Pada proyek ini, kita akan menggunakan pendekatan interpolasi hingga orde tertentu, yang dapat diatur sesuai keinginan, untuk memprediksi dan mengevaluasi akurasi model pada berbagai orde.

## 📌 Langkah-Langkah Implementasi

### 1️⃣ Data Input
Dataset yang digunakan adalah:
- `electricity_data`: Data konsumsi listrik dari bahan bakar fosil dalam satuan TWh.
- `co2_emission_data`: Data emisi CO₂ terkait dalam satuan kiloton (kt).

### 2️⃣ Fungsi Pembentukan Polinomial Lagrange
Fungsi `lagrange_polynomial` membentuk polinomial Lagrange **simbolik** menggunakan **SymPy** berdasarkan data yang diberikan. Polinomial ini membantu membentuk fungsi interpolasi untuk estimasi nilai emisi CO₂ pada titik prediksi.

### 3️⃣ Interpolasi Lagrange
Fungsi `lagrange_interpolation` digunakan untuk menghitung nilai interpolasi pada titik target tertentu (`x_target`) untuk berbagai orde. Polinomial interpolasi dihitung dari data yang paling mendekati titik target untuk mencapai akurasi yang lebih baik.

### 4️⃣ Batas Error Lagrange Teoritis (Manual)
- Fungsi `lagrange_error_bound_manual` menghitung batas error Lagrange secara manual. Batas error ini didasarkan pada turunan ke-(n+1) dari polinomial interpolasi dan produk jarak dari titik target ke setiap titik data terdekat.
- Turunan dihitung menggunakan metode finite differences (beda hingga) sebagai estimasi dari turunan yang tidak diketahui.
- Nilai error yang dihasilkan memberikan perkiraan maksimum error yang mungkin terjadi pada setiap orde interpolasi.

### 5️⃣ Evaluasi Error Numerik
Error numerik dihitung berdasarkan hasil prediksi untuk setiap orde, menggunakan metrik-metrik berikut:
- **Residual Sum of Squares (RSS)**: Jumlah kuadrat dari selisih antara nilai aktual dan nilai prediksi.
- **Total Sum of Squares (TSS)**: Variabilitas total data dari rata-rata aktual.
- **R-squared**: Nilai koefisien determinasi, menunjukkan seberapa baik model menjelaskan variabilitas data.
- **Mean Absolute Error (MAE)**: Rata-rata selisih absolut antara nilai prediksi dan nilai aktual.
- **Mean Absolute Percentage Error (MAPE)**: Rata-rata persentase error antara nilai prediksi dan nilai aktual dalam bentuk persen.
- **Mean Squared Error (MSE)**: Rata-rata kuadrat selisih antara nilai prediksi dan nilai aktual.
- **Root Mean Squared Error (RMSE)**: Akar kuadrat dari MSE, menunjukkan error rata-rata dalam satuan asli data.

### 6️⃣ Plotting
Menghasilkan grafik interpolasi untuk setiap orde hingga `max_order`, beserta titik prediksi pada `x_target`. Grafik untuk memvisualisasikan bagaimana model interpolasi mendekati data asli untuk setiap orde.

## 🔧 Parameter yang Dapat Diatur
- **`x_target`**: Titik prediksi (misal: 238.91).
- **`max_order`**: Batas maksimum orde interpolasi yang ingin dihitung (misal: hingga orde 6).
  
Mengatur `max_order` untuk menentukan hingga orde berapa interpolasi akan dilakukan dan dievaluasi.

## 📈 Hasil dan Output

### 📊 Hasil Prediksi, Batas Error Lagrange, dan Evaluasi Error
Untuk setiap orde dari 1 hingga `max_order`, hasil prediksi, batas error Lagrange, dan evaluasi error dalam bentuk tabel metrik ditampilkan. Digunakan untuk membandingkan akurasi antar orde dan memahami seberapa baik setiap orde interpolasi dalam mendekati data asli.

### 📉 Grafik Interpolasi
Grafik interpolasi menunjukkan:
- **Kurva interpolasi untuk setiap orde** dari 1 hingga `max_order`.
- **Titik prediksi pada `x_target`** untuk setiap orde, dengan label hasil prediksi.
- **Titik data asli** untuk visualisasi yang lebih lengkap.

---

## 📂 Referensi Fungsi Utama
- **`lagrange_polynomial(x_values, y_values)`**: Membentuk polinomial Lagrange secara simbolis.
- **`lagrange_interpolation(x_values, y_values, x_target, order)`**: Menghitung nilai interpolasi untuk titik target dengan orde tertentu.
- **`lagrange_error_bound_manual(x_values, y_values, x_target, order)`**: Menghitung batas error Lagrange secara manual menggunakan metode finite differences.

---

## 📌 Kesimpulan Studi Kasus
Studi ini menunjukkan bahwa **Interpolasi Lagrange dapat memberikan prediksi yang akurat pada rentang data** yang ada. Namun, perlu diperhatikan:
- **Interpolasi Orde Tinggi**: Memberikan akurasi yang lebih baik pada data asli namun cenderung menghasilkan batas error teoritis yang lebih tinggi. Hal ini terjadi karena produk dari perbedaan titik data dan estimasi turunan yang tinggi.
- **Evaluasi Error Numerik**: Menunjukkan error aktual yang bisa lebih kecil dibandingkan batas error teoritis. Evaluasi ini memberikan gambaran yang lebih praktis mengenai akurasi model.
- **Pemilihan Orde**: Interpolasi orde lebih rendah sering kali lebih stabil dan cukup akurat untuk data dalam rentang terbatas.

--- 

**Author:** Arezyhs
