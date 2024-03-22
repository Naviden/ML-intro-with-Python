Suppose we have a dataset with a single categorical feature `Color`, which can take on three values: 'Red', 'Green', and 'Blue'. Here's a hypothetical dataset:

| Example | Color |
|---------|-------|
| 1       | Red   |
| 2       | Green |
| 3       | Blue  |
| 4       | Red   |

OneHotEncoder works by creating a binary column for each category and encoding the presence or absence of that category for each example. Here's how it works:

1. **Identify unique categories**: Identify all unique categories in the `Color` feature: 'Red', 'Green', and 'Blue'.

2. **Create binary columns**: Create a binary column for each unique category.

3. **Encode the presence or absence of each category**: For each example, set the corresponding binary column to 1 if the example belongs to that category, and 0 otherwise.

Let's encode the `Color` feature using OneHotEncoder:

| Example | Red | Green | Blue |
|---------|-----|-------|------|
| 1       | 1   | 0     | 0    |
| 2       | 0   | 1     | 0    |
| 3       | 0   | 0     | 1    |
| 4       | 1   | 0     | 0    |

As you can see, each unique category in the original `Color` feature has been transformed into a binary feature. For example, in the first row, the `Red` column is set to 1 to indicate that the color of the first example is 'Red', while the `Green` and `Blue` columns are set to 0 since those colors are not present in that example.

OneHotEncoder is commonly used in machine learning models, especially when dealing with categorical data, as it allows algorithms to work with categorical variables directly without the need for manual label encoding, which could introduce unintended ordinal relationships between categories.