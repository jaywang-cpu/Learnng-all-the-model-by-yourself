# Definition
其实就是sensitive  TP/（TP+FN），简单些来说就是所有真正的病人，预测成功的概率是多少。

# 实际意义
高recall率其实就是典型害怕误诊，宁可错杀，不可放过。

# 代码实现 
```
# 直接调用sklearn中的recall_score功能就行
from sklearn.metrics import recall_score, classification_report, confusion_matrix
import numpy as np

def calculate_recall_sklearn():
    # 示例数据
    y_true = [1, 1, 0, 1, 0, 1, 1, 0, 0, 1]    # 真实标签
    y_pred = [1, 0, 0, 1, 0, 1, 1, 0, 1, 1]    # 预测标签
    
    # 计算recall
    recall = recall_score(y_true, y_pred)
    
    print("=== Recall 分析 ===")
    print(f"Recall: {recall:.3f}")
    print(f"意思: 在所有实际为正类的样本中，{recall*100:.1f}%被正确识别")
    
    # 详细报告
    print("\n=== 详细分类报告 ===")
    print(classification_report(y_true, y_pred, target_names=['负类', '正类']))
    
    # 混淆矩阵
    print("\n=== 混淆矩阵 ===")
    cm = confusion_matrix(y_true, y_pred)
    print(cm)
    print("混淆矩阵解释:")
    print(f"TN (真负例): {cm[0,0]}")
    print(f"FP (假正例): {cm[0,1]}")  
    print(f"FN (假负例): {cm[1,0]}")
    print(f"TP (真正例): {cm[1,1]}")
    
    return recall

# 运行
calculate_recall_sklearn()
```
