## QuantileTransformer

The `QuantileTransformer` transforms features to follow a uniform or normal distribution by mapping the original values through their empirical cumulative distribution function (CDF). This is useful when algorithms assume normally distributed features, or when you need to reduce the impact of outliers.

### How It Works

1. **Compute empirical quantiles** from the training data
2. **Map each value** to its corresponding quantile position (a value between 0 and 1)
3. **Optionally transform** to a normal distribution using the inverse CDF of the standard normal

### Example

Dataset with 5 test scores:

| Student | Score |
|---------|-------|
| A       | 20    |
| B       | 40    |
| C       | 60    |
| D       | 80    |
| E       | 100   |

With `output_distribution='uniform'`, sklearn computes quantile positions based on the empirical CDF. For 5 equally spaced samples, the transformed values are:

| Student | Score | Transformed (uniform) |
|---------|-------|-----------------------|
| A       | 20    | 0.0                   |
| B       | 40    | 0.25                  |
| C       | 60    | 0.5                   |
| D       | 80    | 0.75                  |
| E       | 100   | 1.0                   |

> **Note:** The actual sklearn output uses `(rank - 0.5) / n` interpolation by default, so values may differ slightly. The key idea is that the transformed data is uniformly distributed.

### Parameters

- `n_quantiles` (default=1000): Number of quantiles to compute. Should not exceed the number of samples.
- `output_distribution`: `'uniform'` (default) maps to [0, 1]; `'normal'` maps to a standard Gaussian.
- `subsample` (default=100000): For large datasets, compute quantiles on a subsample for efficiency.

### When to Use

- When your data has a skewed distribution and you want to make it more Gaussian-like
- To reduce the impact of outliers (extreme values get clipped to the quantile range)
- Before algorithms that assume normal distributions (e.g., LDA, Gaussian Naive Bayes)

### vs. StandardScaler

| Aspect | QuantileTransformer | StandardScaler |
|--------|---------------------|----------------|
| Handles outliers | Yes (clips to quantile range) | No (outliers remain extreme) |
| Output shape | Uniform or Gaussian | Gaussian (only if input is Gaussian) |
| Non-linear | Yes | No (linear transform) |
| Information loss | Can distort relative distances | Preserves relative distances |

### sklearn Example

```python
from sklearn.preprocessing import QuantileTransformer

qt = QuantileTransformer(output_distribution='normal', random_state=42)
X_train_transformed = qt.fit_transform(X_train)
X_test_transformed = qt.transform(X_test)  # Always fit on train only!
```

**Important:** Always `fit` on training data only, then `transform` both train and test. Fitting on the full dataset causes data leakage.
