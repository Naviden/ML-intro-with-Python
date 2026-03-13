## RobustScaler

`RobustScaler` scales features using statistics that are robust to outliers. Instead of using mean and standard deviation (like `StandardScaler`), it uses the median and interquartile range (IQR).

### Formula

$$X_{scaled} = \frac{X - \text{median}(X)}{IQR(X)}$$

Where $IQR = Q_{75} - Q_{25}$ (the interquartile range, i.e., the range between the 25th and 75th percentiles).

### Example

Given values: `[1, 2, 3, 4, 100]`

- Median = 3
- Q25 = 2, Q75 = 4, IQR = 2

| Original | Scaled |
|----------|--------|
| 1        | (1-3)/2 = -1.0 |
| 2        | (2-3)/2 = -0.5 |
| 3        | (3-3)/2 = 0.0 |
| 4        | (4-3)/2 = 0.5 |
| 100      | (100-3)/2 = 48.5 |

Notice the outlier (100) is still far from the others, but it doesn't distort the scaling of the non-outlier values (compare with StandardScaler where mean=22 and std=39.2 would compress the normal values).

### When to Use

- When your data **contains outliers** that you don't want to remove but shouldn't influence scaling
- Before algorithms sensitive to feature scales (SVM, KNN, neural networks, regularized linear models)
- When StandardScaler produces poor results due to outliers skewing the mean and std

### RobustScaler vs. StandardScaler vs. MinMaxScaler

| Scaler | Method | Outlier Robust? | Output Range |
|--------|--------|-----------------|-------------|
| StandardScaler | Mean and std | No | Unbounded (centered at 0) |
| MinMaxScaler | Min and max | No | [0, 1] by default |
| RobustScaler | Median and IQR | Yes | Unbounded (centered at 0) |

### sklearn Example

```python
from sklearn.preprocessing import RobustScaler

scaler = RobustScaler()
X_train_scaled = scaler.fit_transform(X_train)
X_test_scaled = scaler.transform(X_test)  # Always fit on train only!
```

### Parameters

- `with_centering` (default=True): Center data by subtracting the median
- `with_scaling` (default=True): Scale data by dividing by the IQR
- `quantile_range` (default=(25.0, 75.0)): The percentile range used to calculate the IQR
