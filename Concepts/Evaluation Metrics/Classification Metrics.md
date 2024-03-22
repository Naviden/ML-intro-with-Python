## Accuracy

Accuracy is one of the most intuitive performance measures. It is the ratio of correctly predicted observations to the total observations and is given by the formula:


Accuracy = (True Positives + True Negatives) / (Total Observations)


High accuracy means that a model correctly predicts both the positives and negatives at a high rate.

## Precision

Precision, also known as Positive Predictive Value, is the ratio of correctly predicted positive observations to the total predicted positives. High precision relates to a low false positive rate, and the formula is:


Precision = True Positives / (True Positives + False Positives)


Precision is a good measure to determine when the costs of False Positives are high.

## Recall

Recall, also known as Sensitivity or True Positive Rate, is the ratio of correctly predicted positive observations to the all observations in actual class - yes. The formula is:


Recall = True Positives / (True Positives + False Negatives)


Recall shall be the model metric we use to select our best model when there is a high cost associated with False Negative.

## F1 Score

The F1 Score is the weighted average of Precision and Recall. Therefore, this score takes both false positives and false negatives into account. It is a good way to show that a classifer has a good value for both recall and precision. And the formula for the F1 score is:


F1 Score = 2 * (Precision * Recall) / (Precision + Recall)


The F1 score is a measure of a test’s accuracy and is used when the distribution of data and the cost of false positives and false negatives are not equally important.

---

*True Positives (TP)* - These are the correctly predicted positive values which mean that the value of actual class is yes and the value of predicted class is also yes.

*True Negatives (TN)* - These are the correctly predicted negative values which mean that the value of actual class is no and value of predicted class is also no.

*False Positives (FP)* - When actual class is no and predicted class is yes.

*False Negatives (FN)* - When actual class is yes but predicted class in no.

