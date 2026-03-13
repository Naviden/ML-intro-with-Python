## Grid Search

Grid Search is a hyperparameter tuning technique that exhaustively evaluates all possible combinations of hyperparameter values from a predefined grid.

### How It Works

1. **Define a parameter grid**: Specify a set of values for each hyperparameter
2. **Generate all combinations**: Create every possible combination of parameters
3. **Evaluate each combination**: Train and evaluate the model using cross-validation
4. **Select the best**: Choose the combination with the best cross-validation score

### sklearn Example

```python
from sklearn.model_selection import GridSearchCV
from sklearn.ensemble import GradientBoostingRegressor

param_grid = {
    'n_estimators': [100, 200, 300],
    'learning_rate': [0.01, 0.1, 0.2],
    'max_depth': [3, 4, 5]
}

grid_search = GridSearchCV(
    estimator=GradientBoostingRegressor(random_state=42),
    param_grid=param_grid,
    scoring='neg_mean_squared_error',
    cv=5,
    n_jobs=-1
)

grid_search.fit(X_train, y_train)
print(f"Best params: {grid_search.best_params_}")
print(f"Best score: {grid_search.best_score_}")
```

### Grid Search vs. Randomized Search

| Aspect | Grid Search | Randomized Search |
|--------|-------------|-------------------|
| Coverage | Exhaustive (all combinations) | Random subset |
| Speed | Slow for large grids | Faster, controllable via `n_iter` |
| Guarantee | Finds the best in the grid | May miss the optimal combination |
| Scalability | $O(n^k)$ grows exponentially | $O(n_{iter})$ fixed cost |
| When to use | Small parameter space, few hyperparameters | Large parameter space, many hyperparameters |

### Why Negative Scoring?

Sklearn's search methods **maximize** the scoring metric. Since error metrics (MSE, MAE) should be minimized, sklearn uses negative versions (`neg_mean_squared_error`, `neg_mean_absolute_error`) to convert minimization into maximization. Higher (less negative) scores are better.

### Advanced Alternatives

- **HalvingGridSearchCV** (sklearn >= 0.24): Starts by evaluating all candidates with a small subset of data, then progressively eliminates poor performers. Much faster for large grids.
- **Bayesian Optimization** (e.g., Optuna, scikit-optimize): Uses a probabilistic model to intelligently choose the next set of hyperparameters to evaluate. Often finds better results with fewer iterations.

### Tips

- Start with `RandomizedSearchCV` to narrow down promising ranges, then use `GridSearchCV` to fine-tune within those ranges
- Use `n_jobs=-1` to parallelize across all CPU cores
- Monitor with `verbose=2` or higher for progress updates
- Access all results via `grid_search.cv_results_` for detailed analysis
