## Gini Index (Gini Impurity)

The Gini index (or Gini impurity) measures the disorder or impurity in a set of elements. It is used in decision trees, specifically in the CART (Classification and Regression Trees) algorithm, to evaluate potential splits.

The Gini index quantifies how often a randomly chosen element would be incorrectly labeled if it was randomly labeled according to the distribution of labels in the subset.

### Formula

$$ \text{Gini}(D) = 1 - \sum_{i=1}^{m} p_i^2 $$

where:
- $D$ is the dataset for a node,
- $m$ is the number of classes,
- $p_i$ is the proportion of class $i$ instances in the dataset $D$.

### Range

- **Gini = 0**: Perfect purity (all elements belong to a single class)
- **Maximum Gini** = $1 - \frac{1}{m}$, where $m$ is the number of classes
  - For **binary classification**: max = 0.5 (when classes are equally split)
  - For **3 classes**: max = 0.667
  - For **10 classes**: max = 0.9

> **Note:** Don't confuse Gini *impurity* (used in ML, range 0 to 1-1/m) with the Gini *coefficient* (used in economics, range 0 to 1). They are different concepts.

### Numerical Example

Dataset $D$ of 10 instances with two classes: Yes (Y) and No (N). 6 belong to Yes, 4 to No.

Proportions:
- $p_Y = \frac{6}{10} = 0.6$
- $p_N = \frac{4}{10} = 0.4$

$$ \text{Gini}(D) = 1 - (0.6^2 + 0.4^2) = 1 - (0.36 + 0.16) = 1 - 0.52 = 0.48 $$

A Gini of 0.48 (close to the max of 0.5 for binary) indicates high impurity — the classes are almost evenly split.

### Gini vs. Entropy

Decision trees can also use **Entropy** (Information Gain) as a split criterion:

$$ \text{Entropy}(D) = -\sum_{i=1}^{m} p_i \log_2(p_i) $$

| Aspect | Gini | Entropy |
|--------|------|---------|
| Range (binary) | 0 to 0.5 | 0 to 1.0 |
| Computation | Faster (no logarithm) | Slower |
| Behavior | Tends to isolate the most frequent class | Tends to produce more balanced trees |
| In practice | Very similar results | Very similar results |

In sklearn's `DecisionTreeClassifier`, set `criterion='gini'` (default) or `criterion='entropy'`.

### Weighted Gini for Splits

When evaluating a split, the Gini index is computed as a weighted sum of the child nodes' Gini values:

$$ \text{Gini}_{split} = \frac{|D_L|}{|D|} \text{Gini}(D_L) + \frac{|D_R|}{|D|} \text{Gini}(D_R) $$

The split that produces the lowest weighted Gini is chosen.
