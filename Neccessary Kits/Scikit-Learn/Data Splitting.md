# Overview
**A. Train_test_split()**<br>
**B. KFold()**<br>
**C. StratifiedKFold()**<br>
**D. TimeSeriesSplit()**<br>
**E. ShuffleSplit()**

# *A Trian_test_split()*

``` Things Could Be Optimized
from sklearn.model_selection import train_test_split

X_train, X_test, y_train, y_test = train_test_split(
    X, y,                    # 特征和标签
    test_size=0.2,          # 测试集比例
    random_state=42,        # 随机种子
    stratify=None,          # 分层抽样
    shuffle=True            # 是否打乱
)
```

## train_test_split() 所有参数详解

| 参数 | 类型 | 默认值 | 说明 |
|-------------|-------------|-------------|---------------------|
| `arrays` | array-like | 必需 | 要分割的数据 (X, y) |
| `test_size` | float/int | 0.25 | 测试集大小 |
| `train_size` | float/int | None | 训练集大小 |
| `random_state` | int | None | 随机种子 |
| `shuffle` | bool | True | 分割前是否打乱 |
| `stratify` | array-like | None | 分层抽样的标签 ，保证测试级苹果香蕉的比列一样|

---
## Details for the splitting

**使用Numpy的方式导入**
```
from sklearn.model_selection import train_test_split
from sklearn.datasets import load_iris
import pandas as pd

# 数据导入 - NumPy方式
iris = load_iris()
X, y = iris.data, iris.target

# 可选：创建DataFrame查看数据
df = pd.DataFrame(X, columns=iris.feature_names)
df['target'] = y
print("数据预览:")
print(df.head())

# 数据分割 (修正语法错误)
X_train, X_test, y_train, y_test = train_test_split(
    X, y,                    # 添加逗号
    train_size=0.7, 
    test_size=0.3,
    random_state=42,         # 添加逗号
    stratify=y,              # 添加逗号
    shuffle=True
)

print(f"训练集形状: X_train={X_train.shape}, y_train={y_train.shape}")
print(f"测试集形状: X_test={X_test.shape}, y_test={y_test.shape}")
```

**使用 DataFrame 方式**
```
from sklearn.model_selection import train_test_split
from sklearn.datasets import load_iris
import pandas as pd

# 数据导入 - DataFrame方式
iris = load_iris()
X, y = iris.data, iris.target

# 创建完整DataFrame
df = pd.DataFrame(X, columns=iris.feature_names)
df['target'] = y

# 分割DataFrame
train_df, test_df = train_test_split(
    df,                      # 分割整个DataFrame
    train_size=0.7,
    test_size=0.3,
    random_state=42,
    stratify=df['target'],   # 注意这里是df['target']
    shuffle=True
)

# 从分割后的DataFrame中提取特征和标签
X_train = train_df.drop('target', axis=1)
y_train = train_df['target']
X_test = test_df.drop('target', axis=1)
y_test = test_df['target']

print(f"训练集形状: X_train={X_train.shape}, y_train={y_train.shape}")
print(f"测试集形状: X_test={X_test.shape}, y_test={y_test.shape}")
```


