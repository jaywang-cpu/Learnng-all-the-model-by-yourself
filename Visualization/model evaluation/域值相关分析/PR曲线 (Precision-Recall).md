# PR (Precision-Recall)

## Definition
Precision-Recall curve is a metric used to measure the performance of classification models, especially for **imbalanced datasets**. PR curve shows the relationship between the model's Precision and Recall at different thresholds. It focuses on the performance of **positive class prediction**.

## Key Metrics
* **Precision**: Precision=TP/(TP+FP): Actual positive rate among predicted positives (same as PPV).
* **Recall**: Recall=TP/(TP+FN): True positive rate among actual positives (same as Sensitivity).
* **Average Precision (AP)**: Area under the PR curve, representing overall model performance.
* **F1-Score**: F1=2×(Precision×Recall)/(Precision+Recall): Harmonic mean of Precision and Recall.

![](https://github.com/jaywang-cpu/Learnng-all-the-model-by-yourself/blob/main/figure/Algorithms/TP%20FP%20TN%20FN.png)

**Conclusion**: PR curve focuses on **positive class performance** - how well we identify and correctly predict positive cases.

## How to draw it
1. Set different thresholds (typically from 0.0 to 1.0) and collect Precision and Recall values.
   *Example: If >30% is considered cancer, if >50% is considered cancer, etc., collect TP, FP, FN under these conditions*
2. Plot the PR curve using (Recall, Precision) coordinates.
3. Calculate the area under the PR curve as Average Precision (AP). The closer AP is to 1.0, the better the model performance.
4. Add baseline: Random classifier baseline = proportion of positive samples in dataset.

![](https://github.com/jaywang-cpu/Learnng-all-the-model-by-yourself/blob/main/figure/Algorithms/PR%20Curve.png)
![](https://github.com/jaywang-cpu/Learnng-all-the-model-by-yourself/blob/main/figure/Algorithms/PR.png)

## How to use it
| AP Score Range     | Test Quality Assessment         | Model Performance Description                    |
|:------------------:|:------------------------------:|:------------------------------------------------:|
| 0.9 - 1.0          | Excellent                      | Outstanding positive class discrimination        |
| 0.8 - 0.9          | Very good                      | Good positive class discrimination               |
| 0.7 - 0.8          | Good                          | Fair positive class discrimination               |
| 0.6 - 0.7          | Satisfactory                  | Poor positive class discrimination               |
| < Baseline         | Unsatisfactory                | Worse than random guessing                       |

*Note: Baseline = positive class proportion (e.g., if 10% samples are positive, baseline AP ≈ 0.1)*

## Advantage
* **Imbalanced Data Focus**: PR curve is more informative than ROC curve when dealing with highly imbalanced datasets (e.g., rare disease detection, fraud detection).
* **Positive Class Emphasis**: Directly shows how well the model performs on the minority class (positive class), which is often more important.
* **Intuitive Interpretation**: Precision and Recall are more intuitive for business stakeholders than TPR and FPR.
* **Threshold Selection**: Helps choose optimal threshold based on business requirements (high precision vs high recall trade-off).

## When to use PR vs ROC
* **Use PR curve when**: 
  - Dataset is highly imbalanced
  - Positive class is more important
  - Care more about precision of positive predictions
* **Use ROC curve when**:
  - Dataset is relatively balanced  
  - Both classes are equally important
  - Need overall classification performance
