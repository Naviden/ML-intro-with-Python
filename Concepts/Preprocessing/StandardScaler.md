# StandardScaler

In many machine learning algorithms, features may have very different
ranges. For example, one feature might represent **age (0--100)** while
another represents **salary (0--100000)**.

If we do not scale the data, features with larger values can dominate
the learning process.

`StandardScaler` from `scikit-learn` solves this problem by
**standardizing the features**.

Standardization transforms each feature so that:

-   the **mean becomes 0**
-   the **standard deviation becomes 1**

The transformation applied is:

    z = (x − μ) / σ

where:

-   `x` = original value\
-   `μ` = mean of the feature\
-   `σ` = standard deviation of the feature

------------------------------------------------------------------------

### Example

Suppose we have a dataset with two features: `Feature 1` and
`Feature 2`.

  Example   Feature 1   Feature 2
  --------- ----------- -----------
  1         10          20
  2         15          25
  3         8           30
  4         12          18

------------------------------------------------------------------------

### Step 1 --- Calculate the Mean

Mean of `Feature 1`

    (10 + 15 + 8 + 12) / 4 = 11.25

Mean of `Feature 2`

    (20 + 25 + 30 + 18) / 4 = 23.25

------------------------------------------------------------------------

### Step 2 --- Calculate the Standard Deviation

Standard deviation of `Feature 1`

    √((10−11.25)² + (15−11.25)² + (8−11.25)² + (12−11.25)²) / 4

Standard deviation of `Feature 2`

    √((20−23.25)² + (25−23.25)² + (30−23.25)² + (18−23.25)²) / 4

------------------------------------------------------------------------

### Step 3 --- Scale the Features

Each value is transformed using:

    z = (x − μ) / σ

After scaling, each feature will have:

-   mean = 0\
-   standard deviation = 1

------------------------------------------------------------------------

### Python Example

Below is a simple Python example showing how to apply `StandardScaler`
from `scikit-learn`.

``` python
import pandas as pd
from sklearn.preprocessing import StandardScaler

# Create the dataset
data = {
    "Feature 1": [10, 15, 8, 12],
    "Feature 2": [20, 25, 30, 18]
}

df = pd.DataFrame(data)

print("Original dataset:")
print(df)

# Create the scaler
scaler = StandardScaler()

# Apply the scaler
scaled_data = scaler.fit_transform(df)

# Convert back to DataFrame for readability
df_scaled = pd.DataFrame(scaled_data, columns=df.columns)

print("\nDataset after applying StandardScaler:")
print(df_scaled)
```
