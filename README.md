# 📘 Documentation: Polynomial Lagrange Interpolation

This code implements **Lagrange Polynomial Interpolation** to approximate the `Y` value (dependent variable) based on given data points of `X` (independent variable) and `Y`. It constructs Lagrange polynomials up to a specified order to estimate the value at a particular target point and includes error estimation to gauge prediction accuracy.

---

## 📌 Key Features of the Code

1. **Lagrange Polynomial Interpolation**: Constructs Lagrange polynomials based on available data points.
2. **Prediction at Target Point**: Estimates the value of `Y` at a specified `X` target based on the selected interpolation order.
3. **Error Bound Estimation**: Calculates both **Finite Difference-Based Error Bound** and **Smooth Curve Approximation Error Bound** to assess the theoretical maximum error.
4. **Accuracy Evaluation**: Measures interpolation accuracy using error metrics such as MAPE, MAE, RMSE, and R-Squared.
5. **Result Visualization**: Displays the Lagrange polynomial curves, prediction points, and error bounds for various interpolation orders.

---

## 🔧 Function Descriptions

### `lagrange_polynomial` Function
Creates a symbolic Lagrange polynomial using `x`, `x_values`, and `y_values`. This function forms the polynomial by multiplying each `Y` value with a term based on its distance from other points.

- **Parameters**:
  - `x_values`: Array of `X` data points.
  - `y_values`: Array of `Y` values corresponding to the `X` points.
- **Returns**:
  - The symbolic Lagrange polynomial based on the provided `X` and `Y` data.

### `lagrange_interpolation` Function
Calculates the `Y` value at a specified target `X` using a Lagrange polynomial of a chosen order.

- **Parameters**:
  - `x_values`: Array of `X` data points.
  - `y_values`: Array of `Y` values corresponding to the `X` points.
  - `x_target`: The target `X` value for which `Y` needs to be predicted.
  - `order`: The desired interpolation order.
- **Returns**:
  - `interpolated_value`: The interpolated `Y` value at `x_target`.
  - `lagrange_poly`: The symbolic Lagrange polynomial generated for the specified order.

### `lagrange_error_bound_manual` (Finite Difference-Based Error Bound)
Calculates an error bound for Lagrange interpolation at a target `X` based on finite differences. This estimate is derived from the polynomial's derivative and the distance between the target point and other data points.

- **Parameters**:
  - `x_values`: Array of `X` data points.
  - `y_values`: Array of `Y` values corresponding to the `X` points.
  - `x_target`: Target `X` value for prediction.
  - `order`: The interpolation order.
- **Returns**:
  - `error_estimate`: Maximum estimated error bound for the interpolation.

### `lagrange_error_bound_alternative` (Smooth Curve Approximation Error Bound)
Provides an alternative error bound estimation using smooth curve approximations, which is effective for continuous or smooth data trends. This method approximates derivatives without relying on finite differences, aiming for stable error estimates on smoother data.

- **Parameters**:
  - `x_values`: Array of `X` data points.
  - `y_values`: Array of `Y` values corresponding to the `X` points.
  - `x_target`: The target `X` value for prediction.
  - `order`: The interpolation order.
- **Returns**:
  - `error_estimate`: Estimated error bound based on smooth curve approximation.

### `calculate_error_metrics` Function
Computes various error metrics to evaluate interpolation accuracy between actual and predicted `Y` values, including:
  - **Relative Error**: Average percentage error.
  - **MAPE** (Mean Absolute Percentage Error): Average absolute percentage error.
  - **MAE** (Mean Absolute Error): Average absolute error.
  - **RMSE** (Root Mean Square Error): Root of mean squared errors.
  - **R-Squared**: Coefficient of determination, measuring the model's fit to the data.

- **Parameters**:
  - `y_actual`: Array of actual `Y` values.
  - `y_pred`: Array of predicted `Y` values.
- **Returns**:
  - `error_relatif`, `R`, `R_squared`, `MAPE`, `MAE`, `RMSE`.

---

## 🖼️ Visualization of Results

The visualization graph for Lagrange interpolation includes:
- **Original data points** marked as blue dots.
- **Interpolation polynomials** for each specified order drawn as smooth curves.
- **Prediction points** at the target `X`, marked distinctly to show predicted values.
- **Error Bound Curves** (for both finite difference and smooth curve methods), showing theoretical error bounds for each polynomial order.

This graph provides a clear illustration of how well each polynomial fits the data and where the predicted values lie in relation to the target.

---

## 📈 Usage Example

To use this code for Lagrange interpolation:
1. Define `X` and `Y` arrays with data points.
2. Set a target `X` point for prediction.
3. Choose the interpolation order by setting `set_order`.

The code will output tables of predictions and error metrics for each order and display a visualization showing interpolation curves and predicted points.

---

## Example Error Metrics for Accuracy Evaluation

| Metric            | Description                                                  |
|-------------------|--------------------------------------------------------------|
| **Relative Error**| Average relative error of predictions                        |
| **MAPE**          | Mean Absolute Percentage Error, average error percentage     |
| **MAE**           | Mean Absolute Error, average absolute error                  |
| **RMSE**          | Root Mean Square Error, sensitive to outliers                |
| **R-Squared**     | Measures the model's fit to the actual data                  |

---

## ⚙️ Key Configuration Variables

- **`data_x`**: Array of `X` data points (independent variables).
- **`data_y`**: Array of `Y` values (dependent variables).
- **`x_target`**: The target `X` value for prediction.
- **`set_order`**: Specifies the interpolation order for prediction (default: 4).

---

This code provides a robust solution for numerical interpolation with customizable accuracy and error estimation. Users can select the appropriate interpolation order and method to meet their accuracy requirements.
