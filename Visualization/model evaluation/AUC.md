# TP FP TN FN

* Sensitivity: Sensitivity=TP/(TP+FN)：True positive rate among actual positives.
* Specificity: Specificity=TN/(TN+FP) :True negative rate among actual negatives.
* Predictive Positive Value(PPN): TP/(TP+FP): Actual positive rate among predicted positives.
* Negative Predictive Value(NPV): TN/(TN+FN): Actual negative rate among predicted negatives.

Conclusion:竖实际，横预测；敏感病人，特异健康


# AUC （Area Under the Curve)

## Definition
Area Under the Curve is a metric used to measure the performance of classification models. AUC represents the area under the ROC (Receiver Operating Characteristic) curve of the classification model. The ROC curve shows the relationship between the model’s true positive rate (TPR) and false positive rate (FPR) at different thresholds


## How to draw it 
1. Set different thresholds (typically from 0.0 to 1.0) and collect FPR (1-Specificity) and TPR (Sensitivity).
   *Example: If >30% is considered pneumonia, if >50% is considered pneumonia, etc., collect TP and FP under these conditions*
2. Plot the curve ROC using (FPR, TPR) coordinates.
3. Define this curve as ROC, and define the area under the curve as accuracy. The closer the area is to 1 (the closer to high Sensitivity), the higher the true positive probability.

![](https://github.com/jaywang-cpu/Learnng-all-the-model-by-yourself/blob/main/figure/Algorithms/AUC%20Curve.png)


## How to use it 
| AUC Score Range    | Test Quality Assessment         | Model Performance Description                    |
|:------------------:|:------------------------------:|:------------------------------------------------:|
| 0.9 - 1.0          | Excellent                      | Outstanding discrimination ability               |
| 0.8 - 0.9          | Very good                      | Good discrimination ability                      |
| 0.7 - 0.8          | Good                          | Fair discrimination ability                      |
| 0.6 - 0.7          | Satisfactory                  | Poor discrimination ability                      |
| 0.5 - 0.6          | Unsatisfactory                | Fail/No discrimination ability                   |

## Advantage

* *Using Different Thresholds: Compared to other performance metrics, AUC can evaluate the performance of the model using different threshold values. This is important to see the balance between sensitivity and specificity of the model.*
* *Ease of Use: AUC is widely preferred among users because it is an easy metric to calculate and interpret*
