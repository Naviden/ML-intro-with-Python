## LabelEncoder

`LabelEncoder` converts categorical text labels into integer values. It assigns a unique integer to each category.

### How It Works

Given categories: `['cat', 'dog', 'bird']`

LabelEncoder assigns integers alphabetically:
- `bird` → 0
- `cat` → 1
- `dog` → 2

### When to Use

- **Target variable encoding**: Converting class labels (e.g., `'spam'`/`'ham'`) to integers for classification
- **Ordinal features** where the integer ordering is meaningful

### When NOT to Use

- **Input features** in most models — LabelEncoder creates an arbitrary ordinal relationship between categories. A model may incorrectly assume that `dog (2) > cat (1) > bird (0)`. Use `OneHotEncoder` or `OrdinalEncoder` instead.

### sklearn Example

```python
from sklearn.preprocessing import LabelEncoder

le = LabelEncoder()
y_encoded = le.fit_transform(['cat', 'dog', 'bird', 'cat', 'dog'])
# Output: [1, 2, 0, 1, 2]

# Inverse transform to get original labels
y_original = le.inverse_transform([1, 2, 0])
# Output: ['cat', 'dog', 'bird']
```

### LabelEncoder vs. OrdinalEncoder vs. OneHotEncoder

| Encoder | Output | Use For |
|---------|--------|---------|
| LabelEncoder | Single column of integers | Target variable (y) |
| OrdinalEncoder | Integer columns (preserves shape) | Ordinal features (e.g., low/medium/high) |
| OneHotEncoder | Binary columns per category | Nominal features (no inherent order) |

### Important Notes

- LabelEncoder only works on a single column (1D array), not a DataFrame
- For encoding the target variable, you can also use `y.map({'class_a': 0, 'class_b': 1})` for explicit control
- If new categories appear at prediction time, LabelEncoder will raise an error
