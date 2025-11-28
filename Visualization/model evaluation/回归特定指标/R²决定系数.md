## definition
模型的解释度有多少，范围为0-1，越靠近1，模型预测性越强，解释性越好

## 基本要素
- SSres (残差平方和): Σ(实际值 - 预测值)²
- SStot (总平方和): Σ(实际值 - 实际平均值)²
- R²决定系数 = 1 - (SSres / SStot)

## 代码实现
```
from sklearn.metrics import r2_score
r2 = r2_score(y_true, y_pred)
```

