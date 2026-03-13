## Bias-Variance Tradeoff

The bias-variance tradeoff is a fundamental concept in machine learning that describes the tension between two sources of prediction error.

### Bias

Bias is the error from overly simplistic assumptions in the model. High bias means the model **underfits** — it fails to capture the underlying pattern in the data.

Examples of high-bias models: Linear regression on non-linear data, very shallow decision trees.

### Variance

Variance is the error from the model being too sensitive to fluctuations in the training data. High variance means the model **overfits** — it captures noise rather than the true pattern.

Examples of high-variance models: Deep decision trees with no pruning, KNN with k=1.

### The Tradeoff

$$\text{Total Error} = \text{Bias}^2 + \text{Variance} + \text{Irreducible Error}$$

- **Irreducible error** is noise inherent in the data that no model can eliminate
- As model complexity increases: bias decreases, variance increases
- As model complexity decreases: bias increases, variance decreases
- The goal is to find the sweet spot that minimizes total error

### Practical Implications

| Symptom | Diagnosis | Solutions |
|---------|-----------|-----------|
| High training error, high test error | High bias (underfitting) | More complex model, more features, less regularization |
| Low training error, high test error | High variance (overfitting) | More training data, regularization, simpler model, dropout, pruning |
| Low training error, low test error | Good fit | You're done! |

### How Common Models Fit

- **Linear Regression**: High bias, low variance
- **Decision Trees (deep)**: Low bias, high variance
- **Random Forest**: Reduces variance through averaging (bagging)
- **Gradient Boosting**: Reduces bias through sequential correction
- **Ridge/Lasso**: Adds regularization to reduce variance of linear models
- **KNN (small k)**: Low bias, high variance; KNN (large k): higher bias, lower variance

### Detecting the Tradeoff

- **Learning curves**: Plot training and validation error vs. training set size. If both are high, increase model complexity. If they diverge, reduce variance.
- **Cross-validation**: Compare train vs. validation scores. A large gap suggests overfitting.
