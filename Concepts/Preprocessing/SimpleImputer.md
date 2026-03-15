Suppose we have a dataset with a few missing values:

| Example | Feature 1 | Feature 2 | Feature 3 |
|---------|-----------|-----------|-----------|
| 1       | 10        | 20        | NaN       |
| 2       | NaN       | 25        | 30        |
| 3       | 8         | NaN       | 35        |
| 4       | 12        | 18        | NaN       |

Here, `NaN` represents missing values.

SimpleImputer works by replacing missing values with a specified strategy. The strategy could be mean, median, most frequent value, or a constant value. Let's use the mean strategy for this example.

1. **Calculate the mean**: Calculate the mean for each feature with missing values.

   Mean of `Feature 1` = (10 + 8 + 12) / 3 = 10
   
   Mean of `Feature 2` = (20 + 25 + 18) / 3 = 21
   
   Mean of `Feature 3` = (30 + 35) / 2 = 32.5

2. **Replace missing values**: Replace the missing values in each feature with its corresponding mean.

   Missing value in `Feature 1` replaced with 10
   
   Missing value in `Feature 2` replaced with 21
   
   Missing value in `Feature 3` replaced with 32.5

After applying SimpleImputer with the mean strategy, the dataset becomes:

| Example | Feature 1 | Feature 2 | Feature 3 |
|---------|-----------|-----------|-----------|
| 1       | 10        | 20        | 32.5      |
| 2       | 10        | 25        | 30        |
| 3       | 8         | 21        | 35        |
| 4       | 12        | 18        | 32.5      |

As you can see, the missing values have been replaced with the mean value of each respective feature. This ensures that the dataset is complete and ready for further analysis or modeling.

## Python Example

Below is a simple Python example showing how to use `SimpleImputer` from `scikit-learn` to replace missing values with the mean of each feature.

```python
import numpy as np
import pandas as pd
from sklearn.impute import SimpleImputer

# Create the dataset
data = {
    "Feature 1": [10, np.nan, 8, 12],
    "Feature 2": [20, 25, np.nan, 18],
    "Feature 3": [np.nan, 30, 35, np.nan]
}

df = pd.DataFrame(data)

print("Original dataset:")
print(df)

# Create the imputer
imputer = SimpleImputer(strategy="mean")

# Apply the imputer
imputed_data = imputer.fit_transform(df)

# Convert back to DataFrame for readability
df_imputed = pd.DataFrame(imputed_data, columns=df.columns)

print("\nDataset after applying SimpleImputer:")
print(df_imputed)
```