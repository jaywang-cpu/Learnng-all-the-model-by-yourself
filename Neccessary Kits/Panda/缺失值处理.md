# Overview
**1. df.dropna()-删除缺失值** <br>
**2. df.fillna()-填充缺失值** <br>
**3. df.interpolate()-插值填充** <br>
**4. df.bfill()-后向填充** <br>
**5. df.ffill()-前向填充** <br>

## 1.df.dropna()
```
#删除 *任何* 包含缺失值的行 df.dropna()
#删除 *全部* 都是缺失值的行 df.dropna(how='all')
#删除 *任何* 包含缺失值的列 df.drop(axis=1)
```

## 2. df.fillna()
```
# (a).df.fillna(0) 用0去填充
# (b).用不同值填充不同列 自定义指去填充
print("fillna({'A': 999, 'B': -1}):")
print(df.fillna({'A': 999, 'B': -1, 'C': 888}))
        A    B      C
# 0    1.0  5.0    9.0
# 1  999.0  6.0   10.0  ← A列NaN变成999
# 2    3.0 -1.0   11.0  ← B列NaN变成-1
# 3    4.0  8.0  888.0  ← C列NaN变成888
# (c).df.fillna(df.mean()) 用平均值去填充
```

# 3.df.interpolate()
```
# 若空上下都有值，就结合空上下的值来算，保证该空-y=上一空，该空-y=下一空
# 若空上下都没值，那就一直移到上下空都有值的，算好中间有几个缺值，来分配y
# 用就是df.interpolate()
# 注意，我感觉这个用之前要自己先把顺序排好
```

# 4.df.bfill()
```
# 向后取，最近的一个空格中的值
df_fill = pd.DataFrame({
    'A': [1, np.nan, np.nan, 4],
    'B': [np.nan, np.nan, 3, 4]
})

print("原始数据:")
print(df_fill)
#      A    B
# 0  1.0  NaN
# 1  NaN  NaN
# 2  NaN  3.0
# 3  4.0  4.0

print("bfill() - 用后面的值填充:")
print(df_fill.bfill())
#      A    B
# 0  1.0  3.0  ← B列用后面的3填充
# 1  4.0  3.0  ← A列用后面的4填充，B列用后面的3填充
# 2  4.0  3.0  ← A列用后面的4填充
# 3  4.0  4.0
```

# df.ffill()
```
print("ffill() - 用前面的值填充:")
print(df_fill.ffill())
#      A    B
# 0  1.0  NaN  ← B列前面没有值，还是NaN
# 1  1.0  NaN  ← A列用前面的1填充
# 2  1.0  3.0  ← A列用前面的1填充
# 3  4.0  4.0
```
