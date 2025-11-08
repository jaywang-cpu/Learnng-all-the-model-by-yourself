
# Overview
**1.Simplelmputer--简单插补** <br>
**2.KNNImputer（）--K近邻插补** <br>
**3.LterativeImputer--迭代插补** <br>


## 1.SimpleImputer
```
from sklearn.impute import SimpleImputer
import pandas as pd
import numpy as np

df = pd.DataFrame({
    'A': [1, np.nan, 3, np.nan, 5],
    'B': [2, 4, np.nan, 8, np.nan]
})

# sklearn方式
imputer = SimpleImputer(strategy='mean')  # 均值填充
df_filled = pd.DataFrame(imputer.fit_transform(df), columns=df.columns)
(其实你这个还不懂的）
```

## 2.KNNImputer-- K近临插补
```
from sklearn.impute import KNNImputer

df = pd.DataFrame({
    'age': [25, np.nan, 35, 30, np.nan],
    'income': [50000, 60000, np.nan, 55000, 45000],
    'score': [85, 90, 95, np.nan, 80]
})

# KNN插补：用最相似的K个样本来预测缺失值
knn_imputer = KNNImputer(n_neighbors=2)
df_knn = pd.DataFrame(knn_imputer.fit_transform(df), columns=df.columns)

print("原始数据:")
print(df)
#    age   income  score
# 0 25.0  50000.0   85.0
# 1  NaN  60000.0   90.0  ← age缺失
# 2 35.0      NaN   95.0  ← income缺失
# 3 30.0  55000.0    NaN  ← score缺失
# 4  NaN  45000.0   80.0  ← age缺失

print("KNN插补后:")
print(df_knn)
# 会根据相似样本智能填充，比如年龄25的人收入50000，
# 那么收入60000的人年龄可能在25-35之间
```

## 3.IterativeImputer - 迭代插补

```
from sklearn.experimental import enable_iterative_imputer
from sklearn.impute import IterativeImputer

# 迭代插补：用其他特征预测缺失值
iterative_imputer = IterativeImputer(random_state=42)
df_iterative = pd.DataFrame(iterative_imputer.fit_transform(df), columns=df.columns)

# 原理：
# 1. 用age和score预测income
# 2. 用income和score预测age  
# 3. 用age和income预测score
# 4. 反复迭代直到收敛
```

