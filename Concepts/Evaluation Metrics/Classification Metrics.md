## Classification Metrics

### Confusion Matrix

A confusion matrix is a table that summarizes the performance of a classification model by showing the counts of correct and incorrect predictions broken down by class. For binary classification:

|                    | Predicted Positive | Predicted Negative |
|--------------------|--------------------|--------------------|
| **Actual Positive** | True Positive (TP)  | False Negative (FN) |
| **Actual Negative** | False Positive (FP) | True Negative (TN)  |

Understanding the confusion matrix is essential before interpreting any of the metrics below.

---

## Accuracy

Accuracy is the ratio of correctly predicted observations to the total observations:

$$\text{Accuracy} = \frac{TP + TN}{TP + TN + FP + FN}$$

High accuracy means the model correctly predicts both positives and negatives at a high rate. However, accuracy can be misleading on **imbalanced datasets** — a model that always predicts the majority class can still achieve high accuracy.

## Precision

Precision (Positive Predictive Value) is the ratio of correctly predicted positive observations to all predicted positives:

$$\text{Precision} = \frac{TP}{TP + FP}$$

High precision means few false positives. Use precision when the **cost of false positives is high** (e.g., spam detection — you don't want to mark a legitimate email as spam).

## Recall (Sensitivity)

Recall (also called Sensitivity or True Positive Rate) is the ratio of correctly predicted positive observations to all actual positives:

$$\text{Recall} = \frac{TP}{TP + FN}$$

High recall means few false negatives. Use recall when the **cost of false negatives is high** (e.g., disease detection — you don't want to miss a sick patient).

## Specificity

Specificity (True Negative Rate) is the ratio of correctly predicted negative observations to all actual negatives:

$$\text{Specificity} = \frac{TN}{TN + FP}$$

Specificity is the recall equivalent for the negative class.

## F1 Score

The F1 Score is the harmonic mean of Precision and Recall, providing a single metric that balances both:

$$F1 = 2 \times \frac{\text{Precision} \times \text{Recall}}{\text{Precision} + \text{Recall}}$$

The F1 score is especially useful when you need a balance between precision and recall and the class distribution is uneven.

## AUC-ROC

The ROC (Receiver Operating Characteristic) curve plots the True Positive Rate (Recall) against the False Positive Rate (1 - Specificity) at various classification thresholds.

The AUC (Area Under the Curve) summarizes the ROC curve as a single number between 0 and 1:
- **AUC = 1.0**: Perfect classifier
- **AUC = 0.5**: No better than random guessing
- **AUC < 0.5**: Worse than random (predictions are inverted)

AUC-ROC is particularly useful for **imbalanced datasets** because it evaluates performance across all thresholds rather than at a single decision point. Most sklearn classifiers provide `predict_proba()` which can be used with `roc_auc_score()`.

---

## Multiclass Averaging

For multiclass problems, precision, recall, and F1 can be computed in different ways:
- **Macro**: Calculate the metric for each class independently, then average. Treats all classes equally.
- **Micro**: Aggregate TP, FP, FN across all classes, then compute the metric. Gives more weight to frequent classes.
- **Weighted**: Like macro, but weighted by the number of samples in each class.

In sklearn: `f1_score(y_true, y_pred, average='macro')` (or `'micro'`, `'weighted'`).

---

### When to Use Each Metric

| Metric    | Best For |
|-----------|----------|
| Accuracy  | Balanced datasets where all errors are equally costly |
| Precision | When false positives are expensive (spam, fraud alerts) |
| Recall    | When false negatives are expensive (disease screening, safety) |
| F1 Score  | When you need a balance between precision and recall |
| AUC-ROC   | Comparing models on imbalanced data, threshold-independent evaluation |
