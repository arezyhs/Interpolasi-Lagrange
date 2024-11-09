# 📘 Dokumentasi Kode: Interpolasi Polinomial Lagrange dengan Python

Kode ini mengimplementasikan metode **Interpolasi Polinomial Lagrange** untuk menghitung nilai perkiraan `Y` berdasarkan titik data `X` dan `Y` yang diberikan. Metode ini menghasilkan polinomial Lagrange hingga orde yang ditentukan untuk mendekati nilai pada titik tertentu dengan akurasi yang dapat diukur menggunakan berbagai metrik error.

---

## 📌 Fitur Utama Kode

1. **Interpolasi Polinomial Lagrange**: Menghitung polinomial Lagrange untuk titik data yang tersedia.
2. **Prediksi pada Titik Target**: Memperkirakan nilai `Y` pada titik `X` target berdasarkan orde interpolasi.
3. **Evaluasi Akurasi Prediksi**: Mengukur akurasi interpolasi dengan metrik error seperti MAPE, MAE, RMSE, dan R-Squared.
4. **Visualisasi Hasil**: Menampilkan grafik polinomial Lagrange dan titik prediksi pada titik target untuk berbagai orde interpolasi.
5. **Batas Error Lagrange**: Menghitung batas error teoretis dari interpolasi berdasarkan orde yang dipilih.

---

## 🔧 Deskripsi Fungsi

### Fungsi `lagrange_polynomial`
Membentuk polinomial Lagrange secara simbolik menggunakan variabel `x`, `x_values`, dan `y_values`. Fungsi ini mengalikan nilai `Y` setiap titik dengan faktor yang berhubungan dengan jaraknya terhadap titik lainnya untuk membentuk polinomial Lagrange.

- **Parameter**:
  - `x_values`: Array dari titik data `X`.
  - `y_values`: Array dari nilai `Y` yang sesuai dengan titik data `X`.
- **Mengembalikan**:
  - Polinomial Lagrange dalam bentuk ekspresi simbolik yang diperoleh dari titik-titik `X` dan `Y` yang diberikan.

### Fungsi `lagrange_interpolation`
Menghasilkan nilai `Y` pada titik target `X` menggunakan polinomial Lagrange dengan orde tertentu.

- **Parameter**:
  - `x_values`: Array dari titik data `X`.
  - `y_values`: Array dari nilai `Y` yang sesuai dengan titik data `X`.
  - `x_target`: Nilai `X` tempat prediksi `Y` ingin dihitung.
  - `order`: Orde interpolasi yang diinginkan.
- **Mengembalikan**:
  - `interpolated_value`: Nilai interpolasi `Y` pada `x_target`.
  - `lagrange_poly`: Polinomial Lagrange simbolik yang dihasilkan.

### Fungsi `lagrange_error_bound_manual`
Menghitung batas error untuk interpolasi Lagrange pada titik target `X` untuk suatu orde. Batas error ini berdasarkan turunan dari polinomial dan selisih jarak antara titik target dengan titik data lainnya.

- **Parameter**:
  - `x_values`: Array dari titik data `X`.
  - `y_values`: Array dari nilai `Y` yang sesuai dengan titik data `X`.
  - `x_target`: Titik `X` tempat prediksi `Y` ingin dihitung.
  - `order`: Orde interpolasi.
- **Mengembalikan**:
  - `error_estimate`: Perkiraan batas error maksimum untuk interpolasi Lagrange.

### Fungsi `calculate_error_metrics`
Menghitung berbagai metrik error antara nilai aktual `Y` dan nilai prediksi `Y` untuk mengevaluasi akurasi interpolasi. Metrik yang dihitung meliputi:
  - **Error Relatif**: Rata-rata persentase error.
  - **MAPE** (Mean Absolute Percentage Error): Persentase rata-rata kesalahan absolut.
  - **MAE** (Mean Absolute Error): Rata-rata kesalahan absolut.
  - **RMSE** (Root Mean Square Error): Akar kuadrat dari rata-rata kesalahan kuadrat.
  - **R-Squared**: Koefisien determinasi, mengukur kesesuaian model dengan data.

- **Parameter**:
  - `y_actual`: Array dari nilai `Y` aktual.
  - `y_pred`: Array dari nilai `Y` yang diprediksi.
- **Mengembalikan**:
  - `error_relatif`, `R`, `R_squared`, `MAPE`, `MAE`, `RMSE`.

---

## 🖼️ Visualisasi Hasil

Grafik hasil interpolasi Lagrange menampilkan:
- **Data asli** dalam bentuk titik oranye.
- **Polinomial interpolasi** untuk setiap orde yang dipilih dalam bentuk garis kurva.
- **Titik prediksi** pada `X` target ditampilkan sebagai simbol `x` merah.

Grafik ini memberikan visualisasi mengenai kesesuaian polinomial interpolasi dengan data asli dan titik prediksi.

---

## 📈 Contoh Penggunaan

Untuk menggunakan interpolasi Lagrange dengan kode ini, tentukan:
1. Array titik data `X` dan `Y`.
2. Titik target `X` untuk prediksi.
3. Orde interpolasi yang diinginkan dengan mengubah parameter `set_order`.

Kode akan menampilkan tabel prediksi `Y` dan galat untuk setiap orde, dan grafik visualisasi interpolasi beserta titik prediksi pada titik target.

---

## Contoh Metrik Error untuk Evaluasi Akurasi

| Metrik           | Penjelasan                                                     |
|------------------|-----------------------------------------------------------------|
| **Error Relatif**| Rata-rata kesalahan relatif pada prediksi                       |
| **MAPE**         | Mean Absolute Percentage Error, persentase rata-rata error      |
| **MAE**          | Mean Absolute Error, rata-rata kesalahan absolut                |
| **RMSE**         | Root Mean Square Error, pengukuran kesalahan yang sensitif outlier|
| **R-Squared**    | Mengukur tingkat kesesuaian antara prediksi dan data aktual     |

---

## ⚙️ Konfigurasi Variabel Utama

- **`data_x`**: Array yang berisi data `X`.
- **`data_y`**: Array yang berisi data `Y`.
- **`x_target`**: Titik `X` yang ingin diprediksi.
- **`set_order`**: Mengatur orde interpolasi untuk prediksi (nilai default: 4).

---

Kode ini berguna untuk interpolasi data numerik dengan tingkat akurasi yang dapat disesuaikan. Pengguna dapat memilih orde interpolasi berdasarkan kebutuhan dan jumlah data yang tersedia.
