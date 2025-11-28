## definition
我预测错误的平均值是多少，对大误差特别的敏感，越小越精准，实力水准越稳定

## 基本构成要素
RMSE = √(MSE) = √[Σ(实际值 - 预测值)² / n]
这里的次方是为了，无论预测结果正负都变成正数，用开更好将平方抵掉

## 代码实现
```
对你没看错，这个squared=false其实是要开平方的意思，true才是不用
from sklearn.metrics import mean_squared_error
rmse = mean_squared_error(y_true, y_pred, squared=False)
```
