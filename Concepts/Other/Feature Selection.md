## Feature Selection

Feature selection is the process of choosing a subset of relevant features for model building. It reduces overfitting, improves model performance, and decreases training time.

### Why Feature Selection?

- **Reduces overfitting**: Fewer features means less noise for the model to learn
- **Improves accuracy**: Removing irrelevant features can improve generalization
- **Faster training**: Fewer features means faster computation
- **Better interpretability**: Simpler models are easier to understand

### Methods

#### 1. Filter Methods

Evaluate features independently of the model using statistical tests.

- **Correlation**: Remove features highly correlated with each other (redundant)
- **Variance Threshold**: Remove features with near-zero variance
- **Chi-squared / ANOVA**: Statistical tests for feature-target relationships
- **Mutual Information**: Measures non-linear dependency between feature and target

```python
from sklearn.feature_selection import SelectKBest, f_classif
selector = SelectKBest(f_classif, k=10)
X_selected = selector.fit_transform(X, y)
```

#### 2. Wrapper Methods

Use the model's performance to evaluate feature subsets.

- **Recursive Feature Elimination (RFE)**: Iteratively removes the least important feature
- **Forward/Backward Selection**: Adds or removes features one at a time

```python
from sklearn.feature_selection import RFE
from sklearn.ensemble import RandomForestClassifier
rfe = RFE(RandomForestClassifier(), n_features_to_select=10)
X_selected = rfe.fit_transform(X, y)
```

#### 3. Embedded Methods

Feature selection happens as part of the model training.

- **Lasso (L1) Regularization**: Drives irrelevant feature coefficients to zero
- **Tree-based Feature Importance**: Random Forest and Gradient Boosting provide built-in feature importance scores

```python
from sklearn.ensemble import RandomForestClassifier
model = RandomForestClassifier().fit(X, y)
importances = model.feature_importances_
```

### Tips

- Always perform feature selection **inside** cross-validation to avoid data leakage
- Start with filter methods (fast), then try embedded methods (accurate)
- Use domain knowledge — sometimes the best feature selection is manual
- For high-dimensional data (e.g., text, genomics), feature selection is often essential
