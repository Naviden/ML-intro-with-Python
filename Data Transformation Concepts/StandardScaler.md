Suppose we have a dataset with two features: `Feature 1` and `Feature 2`. Here's a hypothetical dataset:

| Example | Feature 1 | Feature 2 |
|---------|-----------|-----------|
| 1       | 10        | 20        |
| 2       | 15        | 25        |
| 3       | 8         | 30        |
| 4       | 12        | 18        |

StandardScaler works by transforming each feature such that it has a mean of 0 and a standard deviation of 1. Here's how it works:

1. **Calculate the mean**: For each feature, calculate the mean value.

   Mean of `Feature 1` = (10 + 15 + 8 + 12) / 4 = 11.25
   
   Mean of `Feature 2` = (20 + 25 + 30 + 18) / 4 = 23.25

2. **Calculate the standard deviation**: For each feature, calculate the standard deviation.

   Standard deviation of `Feature 1` = sqrt(((10-11.25)^2 + (15-11.25)^2 + (8-11.25)^2 + (12-11.25)^2) / 4)
   
   Standard deviation of `Feature 2` = sqrt(((20-23.25)^2 + (25-23.25)^2 + (30-23.25)^2 + (18-23.25)^2) / 4)

3. **Scale the features**: Subtract the mean from each feature value and divide by the standard deviation.

   Standardized value of `Feature 1` = (10 - 11.25) / standard deviation of `Feature 1`
   
   Standardized value of `Feature 2` = (20 - 23.25) / standard deviation of `Feature 2`

Let's say the standard deviations are calculated to be 2.5 for `Feature 1` and 4.0 for `Feature 2`. Then the standardized values would be:

| Example | Standardized Feature 1 | Standardized Feature 2 |
|---------|------------------------|------------------------|
| 1       | (10 - 11.25) / 2.5 = -0.50 | (20 - 23.25) / 4.0 = -0.81 |
| 2       | (15 - 11.25) / 2.5 =  1.50 | (25 - 23.25) / 4.0 =  0.44 |
| 3       | (8 - 11.25) / 2.5 = -1.30  | (30 - 23.25) / 4.0 =  1.69 |
| 4       | (12 - 11.25) / 2.5 =  0.30 | (18 - 23.25) / 4.0 = -1.31 |

As you can see, after standard scaling, each feature has a mean of 0 and a standard deviation of 1. This scaling process ensures that each feature contributes equally to the analysis, preventing features with larger scales from dominating the others.