## PolynomialFeatures

`PolynomialFeatures` generates polynomial and interaction features from existing features. This allows linear models to capture non-linear relationships.

### How It Works

For input features $[a, b]$ with `degree=2`:
- Original features: $a, b$
- Polynomial features: $a^2, b^2$
- Interaction features: $a \times b$
- Bias term: $1$ (optional)

Full output: $[1, a, b, a^2, ab, b^2]$

### Example

| Feature 1 | Feature 2 | → | 1 | F1 | F2 | F1² | F1×F2 | F2² |
|-----------|-----------|---|---|----|----|-----|-------|-----|
| 2         | 3         | → | 1 | 2  | 3  | 4   | 6     | 9   |
| 4         | 5         | → | 1 | 4  | 5  | 16  | 20    | 25  |

### sklearn Example

```python
from sklearn.preprocessing import PolynomialFeatures
from sklearn.linear_model import LinearRegression
from sklearn.pipeline import make_pipeline

# Polynomial regression = PolynomialFeatures + LinearRegression
poly_model = make_pipeline(
    PolynomialFeatures(degree=2, include_bias=False),
    LinearRegression()
)
poly_model.fit(X_train, y_train)
```

### Parameters

- `degree` (default=2): Maximum degree of polynomial features
- `interaction_only` (default=False): If True, only generates interaction features (no $a^2$, $b^2$, etc.)
- `include_bias` (default=True): If True, includes a column of ones

### Caution

- Number of features grows rapidly: with $n$ features and degree $d$, output has $\binom{n+d}{d}$ features
- High-degree polynomials are prone to **overfitting** — combine with regularization (Ridge, Lasso)
- For 100 features at degree 2: 5,151 output features. At degree 3: 176,851 features!
