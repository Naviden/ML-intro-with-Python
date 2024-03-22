Logistic regression is a type of statistical model used for binary classification tasks. In binary classification, the goal is to predict whether an observation belongs to one of two classes, usually represented as 0 or 1.

#### How It Works:

1. **Linear Combination:**
   - Logistic regression starts with a linear combination of the input features. It multiplies each feature by a weight (which the model learns during training) and sums them up.
   - This linear combination is then passed through a function called the logistic function (also known as the sigmoid function).

2. **Logistic (Sigmoid) Function:**
   - The logistic function is an S-shaped curve that maps any real-valued number to the range [0, 1].
   - It is defined as: $$\sigma(z) = \frac{1}{1 + e^{-z}}$$
   - Where $z$ is the linear combination of input features and weights.
   - The output of the logistic function represents the probability that an observation belongs to the positive class (class 1).

3. **Decision Boundary:**
   - The logistic function outputs probabilities between 0 and 1. To make a binary decision, a threshold is applied (commonly 0.5).
   - If the predicted probability is above the threshold, the model predicts class 1; otherwise, it predicts class 0.
   - The decision boundary is the point at which the predicted probability equals the threshold.

4. **Training:**
   - During training, the model adjusts the weights to minimize the difference between predicted probabilities and actual class labels.
   - This is typically done using optimization algorithms such as gradient descent.

#### Key Points:

- Logistic regression is used for binary classification tasks.
- It models the probability that an observation belongs to a particular class.
- The logistic function maps the linear combination of features and weights to a probability between 0 and 1.
- The decision boundary separates the classes based on the threshold probability.