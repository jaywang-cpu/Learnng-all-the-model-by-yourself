## definition
Log-Likelihood（对数似然）是用来衡量给定观测数据下，某个参数组合有多**合理**的数学工具

## 基本构成要素
- 似然：已知数据，问参数的合理性-就像是观测到10次中7次正面，硬币正面概率是0.7合理吗。  （问的是合理性）
- 概率：已知参数，问数据出现的可能性-如果硬币正面概率是0.5，抛10次得到7次正面的可能性？（问的是可能性）
- 对数：连乘很多小数会变成0，但求和不会，并且乘法变加法，求导更容易。
- 好的参数要让所有数据点都有合理概率，而不是让某个点概率极高其他点概率极低！
e.g.
观测[170,175,180]身高：
参数A(μ=170,σ=0.1)：在170cm概率超高，但在175,180cm概率几乎为0 → 联合概率≈0
参数B(μ=175,σ=5)：每个点概率都合理 → 联合概率更高
结论：要所有点都合理，不是某个点超高！

## 公式使用
- Log-Likelihood = Σ ln[P(观测i | 参数)]
- 最佳参数 = argmax(Log-Likelihood)
- 这个两个公式其实就是尝试了很多组合，返回log-likelihood最高时对应的概率
```
e.g.
观测：抛硬币3次得到[正,正,反]
测试不同的p值：
p=0.5: 
Log-Likelihood = ln(0.5) + ln(0.5) + ln(0.5) = -0.69 + (-0.69) + (-0.69) = -2.07
p=0.6:
Log-Likelihood = ln(0.6) + ln(0.6) + ln(0.4) = -0.51 + (-0.51) + (-0.92) = -1.94
p=0.7:
Log-Likelihood = ln(0.7) + ln(0.7) + ln(0.3) = -0.36 + (-0.36) + (-1.20) = -1.92 ← 最高！
结论：最佳参数 p = 0.7
```

## 啥时候用
只要你有数据，而且你想知道什么参数最能解释这些数据，就用log-likelihood。（一般可以用于置信区间，假设检验比较不同假设哪个更合理，逻辑回归找最佳权重参数，朴素贝叶斯估计各类别概率）

## 代码实现
```
from sklearn.linear_model import LogisticRegression
from sklearn.datasets import make_classification
import numpy as np

# 生成数据
X, y = make_classification(n_samples=100, n_features=2, random_state=42)

# 训练模型
model = LogisticRegression()
model.fit(X, y)

# 计算log-likelihood
y_prob = model.predict_proba(X)  # 获取概率
log_likelihood = np.sum(y * np.log(y_prob[:, 1]) + (1-y) * np.log(y_prob[:, 0]))

print(f"Log-Likelihood = {log_likelihood:.3f}")
```
