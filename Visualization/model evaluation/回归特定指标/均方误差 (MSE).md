## definition
MSE是均方误差，它把每个预测值与真实值的差异平方后求平均。误差被平方，大误差会被严厉放大。误差2变成4，误差5变成25。

## 应用场景
需要严厉惩罚大误差的场景，模型训练优化（神经网络、线性回归），解释性不用很强，方便下面计算的场景, **注意单位**
![](https://github.com/jaywang-cpu/Learnng-all-the-model-by-yourself/blob/main/figure/Algorithms/MSE.png)

## 代码实现
```
from sklearn.metrics import mean_squared_error
mse = mean_squared_error(y_true, y_pred)
```
