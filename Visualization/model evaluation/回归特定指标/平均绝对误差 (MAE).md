
## definition
本质上是和均方根作用是一致的，都是描述平均误差的大小，但是RMSE的惩罚力度是更大的，因为RMSE有平方

## 计算方式
MAE = Σ|实际值 - 预测值| / n


## 代码实现方式

```
from sklearn.metrics import mean_absolute_error
mae = mean_absolute_error(y_true, y_pred)
```
