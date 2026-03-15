## Regression Metrics

When evaluating regression models, we rely on several key metrics to understand prediction quality.

### Mean Absolute Error (MAE)

MAE measures the average magnitude of errors without considering direction. It's the most interpretable error metric since it's in the same units as the target variable.

$$MAE = \frac{1}{n} \sum_{i=1}^{n} |y_i - \hat{y}_i|$$

- Robust to outliers (compared to MSE/RMSE)
- A MAE of 0 means perfect predictions

### Mean Squared Error (MSE)

MSE squares the errors before averaging, placing more emphasis on larger errors. This makes it sensitive to outliers but useful when large errors are particularly undesirable.

$$MSE = \frac{1}{n} \sum_{i=1}^{n} (y_i - \hat{y}_i)^2$$

### Root Mean Squared Error (RMSE)

RMSE is the square root of MSE, bringing units back to the target variable's scale while still penalizing large errors more than MAE.

$$RMSE = \sqrt{\frac{1}{n} \sum_{i=1}^{n} (y_i - \hat{y}_i)^2}$$

### R-Squared (R²)

R², the coefficient of determination, measures the proportion of variance in the target explained by the model. It provides a relative measure of fit rather than an absolute error value.

$$R^2 = 1 - \frac{\sum_{i=1}^{n} (y_i - \hat{y}_i)^2}{\sum_{i=1}^{n} (y_i - \bar{y})^2}$$

- **R² = 1**: Perfect predictions
- **R² = 0**: Model predicts no better than always predicting the mean
- **R² < 0**: Model is *worse* than predicting the mean (possible with bad models or on test data)

### Adjusted R-Squared

Adjusted R² penalizes the addition of features that don't improve the model, making it more reliable for comparing models with different numbers of features.

$$R^2_{adj} = 1 - \frac{(1 - R^2)(n - 1)}{n - p - 1}$$

Where $p$ is the number of features and $n$ is the number of observations. Unlike R², Adjusted R² can decrease when adding irrelevant features.

### Mean Absolute Percentage Error (MAPE)

MAPE expresses error as a percentage of actual values, making it scale-independent and easier to interpret in business contexts.

$$MAPE = \frac{1}{n} \sum_{i=1}^{n} \left|\frac{y_i - \hat{y}_i}{y_i}\right| \times 100\%$$

**Caution:** MAPE is undefined when actual values are zero and can be biased when values are close to zero.

---

### When to Use Each Metric

| Metric      | Best For |
|-------------|----------|
| MAE         | When all errors should be weighted equally; robust to outliers |
| MSE/RMSE    | When large errors are especially bad; RMSE is more interpretable than MSE |
| R²          | Comparing model fit; understanding explained variance |
| Adjusted R² | Comparing models with different numbers of features |
| MAPE        | When you need percentage-based error for business communication |

In sklearn: `mean_absolute_error`, `mean_squared_error`, `r2_score` from `sklearn.metrics`. For MAPE: `mean_absolute_percentage_error` (sklearn >= 0.24).
