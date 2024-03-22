## Understanding MAE, MSE, RMSE, and R^2

When evaluating the performance of regression models, we often rely on several key metrics to understand how well our model is predicting. Let's refresh on what these metrics mean:

### Mean Absolute Error (MAE)

MAE measures the average magnitude of the errors in a set of predictions, without considering their direction. It's calculated as the average of the absolute differences between the predicted values and the actual values. This metric gives an idea of how wrong the predictions are; a value of 0 indicates no error or perfect predictions. Since it measures the average error magnitude, it's easy to interpret.

**Formula:** $$MAE = \frac{1}{n} \sum_{i=1}^{n} |y_i - \hat{y}_i|$$

Where:
- $y_i$ is the actual value,
- $\hat{y}_i$ is the predicted value,
- $n$ is the number of observations.

### Mean Squared Error (MSE)

MSE is similar to MAE but squares the difference between the predicted and actual values before averaging them. The squaring part places more emphasis on larger errors compared to smaller ones, making MSE sensitive to outliers. MSE is useful when large errors are particularly undesirable.

**Formula:** $$MSE = \frac{1}{n} \sum_{i=1}^{n} (y_i - \hat{y}_i)^2$$

### Root Mean Squared Error (RMSE)

RMSE is the square root of the mean squared error. Taking the square root brings the units back to the original units of the output variable and somewhat reduces the sensitivity to large errors. Like MSE, it gives more weight to larger errors, but its units are easier to understand since they match the target variable's units.

**Formula:** $$RMSE = \sqrt{\frac{1}{n} \sum_{i=1}^{n} (y_i - \hat{y}_i)^2}$$

### R-Squared (R^2)

R^2, also known as the coefficient of determination, is a statistical measure that represents the proportion of the variance for the dependent variable that's explained by the independent variable(s) in a regression model. It provides an indication of the goodness of fit of a model. An R^2 of 1 indicates that the regression predictions perfectly fit the data. Values of R^2 outside the range 0 to 1 are possible in cases of extrapolation and should be interpreted with caution.

**Formula:** 

$$
R^2 = 1 - \frac{\sum_{i=1}^{n} (y_i - \hat{y}_i)^2}{\sum_{i=1}^{n} (y_i - \bar{y})^2}
$$

Where:
- $\bar{y}$ is the mean of the actual values.

In summary, MAE, MSE, and RMSE are metrics that directly measure the average error in the predictions, with MSE and RMSE giving more penalty to larger errors. R^2 provides a measure of how well future samples are likely to be predicted by the model. Understanding these metrics helps in evaluating and comparing regression models effectively.
