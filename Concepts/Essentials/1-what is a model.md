# What Is a Model?

<img src="box.png" alt="alt text" width="300">

**"All models are wrong, but some are useful"**. George E. P. Box, (1919-2013)
## Intuition

In machine learning, a **model** is a mathematical function that learns
patterns from data in order to make predictions. less formally, a model is a "*simplified*" representation of a *complex* phenomenon.

A ML model takes **input variables** (features) and produces an **output**
(prediction).

Example:

Input: - Age - Salary

Output: - Probability that a person buys a product

The model learns how inputs relate to outputs by analysing examples from
a dataset.

------------------------------------------------------------------------

## Model as a Function

At a conceptual level, a model can be seen as a function:

f(X) → y

Where:

-   **X** = features (input variables)
-   **y** = predicted value

Example:

House price prediction

f(size, location, number_of_rooms) → price

The goal of training is to find the function that best maps inputs to
outputs.

------------------------------------------------------------------------

## Models Learn From Data

A machine learning model is trained using **examples**.

Example dataset:

  Size   Rooms   Price
  ------ ------- -------
  70     2       200k
  120    4       350k

By analysing many examples, the model learns the relationship between:

features → target

This learned relationship is then used to make predictions on **unseen data**.

------------------------------------------------------------------------

## Models Are Not the Data

Important distinction:

-   **Dataset** → examples used to train the model
-   **Model** → the learned mathematical rule

After training, the model stores only the learned parameters, not the
full dataset.

------------------------------------------------------------------------

## Why Models Are Useful

Once trained, models allow us to:

-   predict future values
-   classify objects
-   detect patterns in data

Examples:

-   spam detection
-   credit risk prediction
-   medical diagnosis
-   recommendation systems

------------------------------------------------------------------------

## Summary

A machine learning **model** is:

-   a mathematical representation of patterns in data
-   trained using historical examples
-   used to make predictions on new data

In short:

Data → Training → Model → Prediction
