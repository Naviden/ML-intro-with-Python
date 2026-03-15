## Cross-Validation

Cross-validation is a technique for evaluating how well a model generalizes to unseen data. Instead of a single train-test split, it systematically splits the data multiple times and averages the results for a more reliable estimate.

### Why Cross-Validation?

A single train-test split can give optimistic or pessimistic results depending on how the data was split. Cross-validation reduces this variance by averaging over multiple splits.

### K-Fold Cross-Validation

The most common method. The data is divided into $k$ equal-sized folds:

1. Use fold 1 as test set, train on folds 2-k
2. Use fold 2 as test set, train on folds 1, 3-k
3. ... repeat for all k folds
4. Average the k performance scores

Typical values: $k = 5$ or $k = 10$.

$$\text{CV Score} = \frac{1}{k} \sum_{i=1}^{k} \text{Score}_i$$

### Stratified K-Fold

For **classification** problems, `StratifiedKFold` preserves the class distribution in each fold. This is important for imbalanced datasets where random splitting might leave some folds with very few minority class samples.

### Other Variants

- **Leave-One-Out (LOO)**: $k = n$ (each sample is its own test set). Very expensive, but minimum bias.
- **Repeated K-Fold**: Runs K-Fold multiple times with different random splits, then averages.
- **TimeSeriesSplit**: For temporal data where future data shouldn't leak into training. Each split uses only past data for training.
- **GroupKFold**: Ensures that samples from the same group (e.g., same patient) don't appear in both train and test.

### sklearn Example

```python
from sklearn.model_selection import cross_val_score, StratifiedKFold

cv = StratifiedKFold(n_splits=5, shuffle=True, random_state=42)
scores = cross_val_score(model, X, y, cv=cv, scoring='f1')
print(f"Mean F1: {scores.mean():.4f} (+/- {scores.std():.4f})")
```

### Cross-Validation vs. Train-Test Split

| Aspect | Train-Test Split | Cross-Validation |
|--------|------------------|-----------------|
| Speed | Fast (one evaluation) | Slower (k evaluations) |
| Variance | High (depends on split) | Low (averaged over k splits) |
| Data usage | Some data only for testing | All data used for both training and testing |
| Use case | Quick evaluation, large datasets | Reliable evaluation, smaller datasets |

### Important Notes

- Cross-validation is for **evaluation**, not training. The final model is typically trained on all available data.
- **Never** apply preprocessing (e.g., scaling) before cross-validation. Use `Pipeline` to ensure preprocessing happens inside each fold.
- For hyperparameter tuning, combine cross-validation with `GridSearchCV` or `RandomizedSearchCV`.
