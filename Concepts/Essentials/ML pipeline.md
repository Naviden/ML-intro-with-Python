# Machine Learning Pipeline

## 1. Problem Definition

Before applying machine learning, we must clearly define the problem.

Typical questions: - What do we want to predict? - What data do we have
available? - Is the task regression or classification?

Examples: - Predict house prices → regression - Predict if an email is
spam → classification

------------------------------------------------------------------------

## 2. Dataset: Features and Target

A machine learning dataset is usually divided into:

**Features (X)**\
The input variables used by the model.

**Target (y)**\
The variable we want to predict.

Example:

  Age   Salary   Buys Product
  ----- -------- --------------
  23    25k      0

Features → Age, Salary\
Target → Buys Product

------------------------------------------------------------------------

## 3. Train / Test Split

To evaluate a model correctly, the dataset is divided into two parts.

-   **Training set** → used to train the model
-   **Test set** → used to evaluate the model

Typical split: - 80% training - 20% testing

Why? If we evaluate the model on the same data used for training, the
results may be overly optimistic.

------------------------------------------------------------------------

## 4. Preprocessing

Real-world data is rarely clean and must often be transformed before
training.

Common preprocessing steps:

**Imputation** Handling missing values.

Example: - Replace missing values with the mean or median.

**Scaling** Standardising numeric features so they have comparable
ranges.

Example: - StandardScaler

**Encoding** Transforming categorical variables into numbers.

Example: - One-hot encoding

------------------------------------------------------------------------

## 5. Model Training

During training, the model learns patterns from the training data.

The algorithm estimates parameters that minimise prediction errors.

Examples of models:

Regression: - Linear Regression - Ridge - Lasso

Classification: - Logistic Regression - Decision Trees

------------------------------------------------------------------------

## 6. Prediction

Once trained, the model can be used to make predictions on unseen data.

Example:

Input: - Age - Salary

Output: - Probability of buying a product

------------------------------------------------------------------------

## 7. Evaluation

To measure model performance, we apply evaluation metrics on the **test
set**.

Regression metrics: - Mean Squared Error (MSE) - Root Mean Squared Error
(RMSE) - R²

Classification metrics: - Accuracy - Precision - Recall - F1-score

------------------------------------------------------------------------

## Summary of the ML Pipeline

1.  Define the problem
2.  Prepare the dataset (features and target)
3.  Split data into training and test sets
4.  Preprocess the data
5.  Train the model
6.  Make predictions
7.  Evaluate performance
