## Definition
简单来说就是我预测有病的中，真正有病的有多少。 精确率 (Precision) = TP / (TP + FP)

## 重要性
相当于在测试你有没有谎报，会影响到满意度

## 代码实现

```
from sklearn.metrics import precision_score, classification_report, confusion_matrix
import matplotlib.pyplot as plt
import seaborn as sns
import numpy as np

def sklearn_precision_analysis():
   
    """使用sklearn分析Precision"""
    
    # 示例数据：推荐系统
    y_true = [1, 1, 0, 1, 0, 1, 1, 0, 0, 1, 0, 0, 1, 0, 1]  # 用户真实喜好
    y_pred = [1, 0, 1, 1, 0, 1, 1, 1, 0, 1, 1, 0, 0, 0, 1]  # 推荐结果
    
    # 计算precision
    precision = precision_score(y_true, y_pred)
    
    print("=== sklearn Precision分析 ===")
    print(f"Precision: {precision:.3f} = {precision*100:.1f}%")
    
    # 详细分类报告
    print("\n=== 详细分类报告 ===")
    report = classification_report(y_true, y_pred, 
                                 target_names=['不喜欢', '喜欢'])
    print(report)
 ```

