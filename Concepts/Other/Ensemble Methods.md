## Ensemble Methods

Ensemble methods combine multiple models to produce better predictions than any single model alone. The core idea: a group of "weak learners" can form a "strong learner."

### Bagging (Bootstrap Aggregating)

Creates multiple models by training each on a random subset of the data (sampled with replacement), then averages their predictions.

- **Reduces variance** (combats overfitting)
- Models are trained **independently** (can be parallelized)
- Example: **Random Forest** = Bagging + Decision Trees + random feature subsets

How it works:
1. Create $n$ bootstrap samples from training data
2. Train one model on each sample
3. For regression: average predictions. For classification: majority vote.

### Boosting

Builds models **sequentially**, where each new model focuses on the errors made by previous models.

- **Reduces bias** (combats underfitting)
- Models are trained **sequentially** (cannot be parallelized as easily)
- Examples: **AdaBoost**, **Gradient Boosting**, **XGBoost**, **LightGBM**, **CatBoost**

How it works:
1. Train a weak model on the data
2. Identify misclassified/poorly predicted samples
3. Train the next model with more weight on those samples
4. Combine all models with weighted voting

### Stacking

Trains multiple diverse models, then uses another model (meta-learner) to combine their predictions.

1. Train base models (e.g., Random Forest, SVM, KNN)
2. Use their predictions as input features for a meta-learner (e.g., Logistic Regression)
3. The meta-learner learns the optimal way to combine base model outputs

### Comparison

| Method | Reduces | Training | Key Risk | Example |
|--------|---------|----------|----------|---------|
| Bagging | Variance | Parallel | Underfitting (if base models are too simple) | Random Forest |
| Boosting | Bias | Sequential | Overfitting (if too many iterations) | XGBoost, Gradient Boosting |
| Stacking | Both | Two-stage | Complexity, overfitting | Custom stacked models |

### When to Use

- **Bagging**: When your base model overfits (high variance), e.g., deep decision trees
- **Boosting**: When you need maximum accuracy and can tune carefully to avoid overfitting
- **Stacking**: When you want to combine fundamentally different model types

In practice, Gradient Boosting variants (XGBoost, LightGBM) are often the top performers on tabular data.
