# 📘 Documentation: Polynomial Lagrange Interpolation for CO₂ Emissions Prediction

This code implements **Lagrange Polynomial Interpolation** to approximate the `Y` value (CO₂ Emission) based on given data points of `X` (Electricity in TWh) and `Y` (CO₂ Emission in kt). This method constructs Lagrange polynomials up to a specified order to approximate the value at a particular target point with measurable accuracy using various error metrics.

---

## 📌 Key Features of the Code

1. **Lagrange Polynomial Interpolation**: Constructs Lagrange polynomials based on available data points.
2. **Prediction at Target Point**: Estimates the value of `Y` at a specified `X` target based on the interpolation order.
3. **Accuracy Evaluation**: Measures interpolation accuracy with error metrics like MAPE, MAE, RMSE, and R-Squared.
4. **Result Visualization**: Displays Lagrange polynomial curves and prediction points for various interpolation orders.
5. **Lagrange Error Bound**: Calculates the theoretical error bound of interpolation based on the selected order.

---

## 🔧 Function Descriptions

### `lagrange_polynomial` Function
Creates a symbolic Lagrange polynomial using `x`, `x_values`, and `y_values`. This function multiplies each `Y` value by a factor relative to its distance from other points to form the Lagrange polynomial.

- **Parameters**:
  - `x_values`: Array of `X` data points.
  - `y_values`: Array of `Y` values corresponding to the `X` points.
- **Returns**:
  - Symbolic Lagrange polynomial based on the given `X` and `Y` points.

### `lagrange_interpolation` Function
Calculates the `Y` value at a target `X` using a Lagrange polynomial of a specified order.

- **Parameters**:
  - `x_values`: Array of `X` data points.
  - `y_values`: Array of `Y` values corresponding to the `X` points.
  - `x_target`: The target `X` value where `Y` needs to be predicted.
  - `order`: The desired order of interpolation.
- **Returns**:
  - `interpolated_value`: The interpolated `Y` value at `x_target`.
  - `lagrange_poly`: Symbolic Lagrange polynomial generated for the specified order.

### `lagrange_error_bound_manual` Function
Calculates the error bound for Lagrange interpolation at a target `X` for a given order. The error bound is derived based on the polynomial's derivatives and the distance between the target point and other data points.

- **Parameters**:
  - `x_values`: Array of `X` data points.
  - `y_values`: Array of `Y` values corresponding to the `X` points.
  - `x_target`: Target `X` value where `Y` needs to be predicted.
  - `order`: The desired order of interpolation.
- **Returns**:
  - `error_estimate`: Maximum estimated error bound for the interpolation.

### `calculate_error_metrics` Function
Computes various error metrics between actual `Y` values and predicted `Y` values to evaluate interpolation accuracy. The metrics include:
  - **Relative Error**: Average percentage error.
  - **MAPE** (Mean Absolute Percentage Error): Average absolute percentage error.
  - **MAE** (Mean Absolute Error): Average absolute error.
  - **RMSE** (Root Mean Square Error): Root of the mean squared errors.
  - **R-Squared**: Coefficient of determination, measuring the model's fit to the data.

- **Parameters**:
  - `y_actual`: Array of actual `Y` values.
  - `y_pred`: Array of predicted `Y` values.
- **Returns**:
  - `error_relatif`, `R`, `R_squared`, `MAPE`, `MAE`, `RMSE`.

---

## 🖼️ Visualization of Results

The Lagrange interpolation visualization graph shows:
- **Original data points** as blue dots.
- **Interpolation polynomial** for each specified order as a smooth curve.
- **Prediction points** at the target `X` displayed as distinct symbols.

The graph provides a visual representation of the interpolation's fit to the data and shows the predicted values at the target point.

---

## 📈 Usage Example

To use Lagrange interpolation with this code:
1. Define the arrays `X` and `Y` with data points.
2. Set a target `X` point for prediction.
3. Specify the desired interpolation order via `set_order`.

The code will display prediction tables with `Y` and error values for each order, alongside a visualization of the interpolation and predicted points.

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

- **`data_x`**: Array of `X` data points (Electricity in TWh).
- **`data_y`**: Array of `Y` values (CO₂ Emission in kt).
- **`x_target`**: The target `X` value for prediction.
- **`set_order`**: Sets the interpolation order for prediction (default: 4).

---

This code is suitable for performing numerical interpolation with adjustable accuracy. Users can choose the interpolation order based on the available data and desired precision.
