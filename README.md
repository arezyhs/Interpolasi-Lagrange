# 📊 Studi Kasus: Prediksi Emisi CO₂ dengan Interpolasi Lagrange

Studi kasus ini mengeksplorasi penggunaan **Interpolasi Lagrange** untuk memprediksi emisi CO₂ berdasarkan konsumsi listrik dari bahan bakar fosil. Kita akan menggunakan pendekatan interpolasi hingga orde tertentu, yang dapat diatur sesuai keinginan, untuk memprediksi dan mengevaluasi akurasi model pada berbagai orde.

## 📌 Langkah-Langkah Implementasi

### 1️⃣ Data Input
Dataset yang digunakan adalah:
- `electricity_data`: Data konsumsi listrik dari bahan bakar fosil dalam satuan TWh.
- `co2_emission_data`: Data emisi CO₂ terkait dalam satuan kiloton (kt).

### 2️⃣ Fungsi Pembentukan Polinomial Lagrange
Fungsi `lagrange_polynomial` membentuk polinomial Lagrange **simbolik** menggunakan **SymPy** berdasarkan data yang diberikan. Polinomial ini membantu menghitung turunan untuk memperkirakan batas error Lagrange.

### 3️⃣ Interpolasi Lagrange
Fungsi `lagrange_interpolation` digunakan untuk menghitung nilai interpolasi pada titik target tertentu (`x_target`) untuk berbagai orde. Polinomial interpolasi dihitung dari data yang paling mendekati titik target untuk mencapai akurasi yang lebih baik.

### 4️⃣ Batas Error Lagrange Teoritis
- Batas error Lagrange dihitung dengan **turunan ke-(n+1)** dari polinomial interpolasi.
- Turunan ini dievaluasi untuk menemukan **nilai maksimum** dalam rentang data yang tersedia. Nilai maksimum ini digunakan untuk memperkirakan error maksimum dalam setiap orde interpolasi.
- Fungsi `lagrange_error_bound` menerapkan formula Lagrange error bound untuk menghitung batas error teoretis.

### 5️⃣ Evaluasi Error Numerik
Error dievaluasi pada titik tambahan (titik yang tidak termasuk dalam data asli). Untuk setiap orde, kita menghitung error numerik berikut:
- **Mean Absolute Error (MAE)**: Rata-rata selisih absolut antara nilai prediksi dan nilai aktual.
- **Mean Absolute Percentage Error (MAPE)**: Rata-rata persentase error antara nilai prediksi dan nilai aktual.
- **Mean Squared Error (MSE)**: Rata-rata kuadrat selisih antara nilai prediksi dan nilai aktual.
- **Root Mean Squared Error (RMSE)**: Akar kuadrat dari MSE, menunjukkan error rata-rata dalam satuan asli data.

### 6️⃣ Plotting
Grafik interpolasi dihasilkan untuk setiap orde hingga `max_order` yang diatur, beserta titik prediksi pada `x_target`. Grafik ini memvisualisasikan bagaimana model interpolasi mendekati data asli untuk setiap orde.

## 🔧 Parameter yang Dapat Diatur
- **`x_target`**: Titik prediksi (misal: 238.91).
- **`max_order`**: Batas maksimum orde interpolasi yang ingin dihitung (misal: hingga orde 4).
  
Anda dapat mengatur `max_order` untuk menentukan hingga orde berapa interpolasi akan dilakukan dan dievaluasi.

## 📈 Hasil dan Output

### 📊 Hasil Prediksi, Batas Error Lagrange, dan Evaluasi Error
Untuk setiap orde dari 1 hingga `max_order`, hasil prediksi, batas error teoritis, dan evaluasi error pada titik tambahan ditampilkan. Ini membantu dalam membandingkan akurasi antar orde dan memahami seberapa baik setiap orde interpolasi dalam mendekati data asli.

### 📉 Grafik Interpolasi
Grafik interpolasi menunjukkan:
- **Kurva interpolasi untuk setiap orde** dari 1 hingga `max_order`.
- **Titik prediksi pada `x_target`** untuk setiap orde, dengan label hasil prediksi.
- **Titik data asli** dan **titik tambahan untuk evaluasi error** untuk visualisasi yang lebih lengkap.

---

## 📂 Referensi Fungsi Utama
- **`lagrange_polynomial(x_values, y_values)`**: Membentuk polinomial Lagrange secara simbolis.
- **`lagrange_interpolation(x_values, y_values, x_target, order)`**: Menghitung nilai interpolasi untuk titik target dengan orde tertentu.
- **`lagrange_error_bound(x_values, x_target, order)`**: Menghitung batas error Lagrange teoritis berdasarkan turunan ke-(n+1) dan produk dari perbedaan titik data.

---

## 📌 Kesimpulan Studi Kasus
Studi ini menunjukkan bahwa **Interpolasi Lagrange dapat memberikan prediksi yang akurat pada rentang data** yang ada. Namun, perlu diperhatikan:
- **Interpolasi Orde Tinggi**: Memberikan akurasi yang lebih baik pada data asli namun cenderung menghasilkan batas error teoritis yang sangat tinggi. Hal ini terjadi karena hasil kali dari perbedaan titik data serta nilai maksimum turunan ke-(n+1) yang besar.
- **Evaluasi Error Numerik**: Menunjukkan error aktual yang biasanya lebih kecil dibandingkan batas error teoritis. Evaluasi ini memberikan gambaran yang lebih praktis mengenai akurasi model.
- **Pemilihan Orde**: Interpolasi orde lebih rendah sering kali lebih stabil dan cukup akurat untuk data dalam rentang terbatas.
---

**Author:** Arezyhs
