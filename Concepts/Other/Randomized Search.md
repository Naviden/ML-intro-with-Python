`RandomizedSearchCV` from `sklearn` is a method used for hyperparameter optimization, a step in building and fine-tuning machine learning models. Unlike grid search that exhaustively tries all combinations of hyperparameters, `RandomizedSearchCV` samples a fixed number of parameter settings from specified distributions. This approach can lead to better results, especially when dealing with a high-dimensional space, and is usually more efficient, saving valuable time and computational resources.

### Methodology

The core idea behind `RandomizedSearchCV` is quite straightforward:

1. **Define the Parameter Space:** Specify a range or distribution for each hyperparameter from which values can be randomly sampled. For instance, if you're tuning a decision tree, you might define a range for the maximum depth of the tree.

2. **Sampling:** Randomly select a fixed number of parameter combinations from the defined space.

3. **Evaluation:** For each combination of parameters, evaluate the model's performance using cross-validation. Cross-validation involves dividing the dataset into a certain number of "folds" or parts, training the model on some of these folds, and validating it on the remaining folds. This process is repeated until each fold has been used for validation once, ensuring that the model's performance is robust and not dependent on a particular train-test split.

4. **Select the Best:** Choose the parameter setting that results in the best performance according to a predefined metric, like accuracy for classification tasks.

###  Numerical Example

Let's consider a simple example with a hypothetical machine learning model where we aim to tune two hyperparameters: `learning_rate` and `max_depth`. For simplicity, we'll say `learning_rate` can range from 0.01 to 0.1, and `max_depth` can be 1, 2, or 3.

1. **Define the Parameter Space:**
   - `learning_rate`: Uniform distribution between [0.01, 0.1]
   - `max_depth`: Discrete values in the set {1, 2, 3}

2. **Sampling:**
   Suppose we decide to sample 3 combinations randomly:
   - Combination 1: `learning_rate` = 0.02, `max_depth` = 2
   - Combination 2: `learning_rate` = 0.05, `max_depth` = 3
   - Combination 3: `learning_rate` = 0.08, `max_depth` = 1

3. **Evaluation:**
   We evaluate each combination using 3-fold cross-validation and suppose we get the following accuracies:
   - Combination 1: 70%
   - Combination 2: 75%
   - Combination 3: 65%

4. **Select the Best:**
   The best performance comes from Combination 2 (`learning_rate` = 0.05, `max_depth` = 3) with an accuracy of 75%.