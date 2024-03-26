The Gini index, or Gini impurity, is a measure of the disorder or impurity in a set of elements. It is used in decision trees, specifically in the CART (Classification and Regression Trees) algorithm, to evaluate splits in the dataset. The Gini index quantifies how often a randomly chosen element from the set would be incorrectly labeled if it was randomly labeled according to the distribution of labels in the subset.

The Gini index ranges from 0 to 0.5 (or 0 to 1, depending on the formula), where 0 signifies perfect purity (all elements are of the same class), and higher values indicate higher impurity. The formula for the Gini index is:

$$ \text{Gini}(D) = 1 - \sum_{i=1}^{m} p_i^2 $$

where:
- $D$ is the dataset for a node,
- $m$ is the number of classes,
- $p_i$ is the ratio of class $i$ instances among the training instances in the dataset $D$.

### Numerical Example:

Let's say we have a dataset $D$ of 10 instances with two classes: Yes (Y) and No (N). Suppose 6 instances belong to class Yes and 4 to class No.

First, we calculate the proportions of each class in the dataset:
- Proportion of Yes, $p_{\text{Y}} = \frac{6}{10} = 0.6$
- Proportion of No, $p_{\text{N}} = \frac{4}{10} = 0.4$

Next, we apply the formula for the Gini index:
$$ \text{Gini}(D) = 1 - (p_{\text{Y}}^2 + p_{\text{N}}^2) $$
$$ \text{Gini}(D) = 1 - (0.6^2 + 0.4^2) $$
$$ \text{Gini}(D) = 1 - (0.36 + 0.16) $$
$$ \text{Gini}(D) = 1 - 0.52 $$
$$ \text{Gini}(D) = 0.48 $$

Therefore, the Gini index for this dataset is 0.48, indicating a moderate level of impurity. In the context of decision trees, a split that results in the lowest Gini index for the resulting partitions is preferred, as it indicates the most significant increase in purity.