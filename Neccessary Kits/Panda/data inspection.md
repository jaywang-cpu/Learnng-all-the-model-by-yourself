# Overview
**1. df.isnull()** <br>
**2. df.isna()** <br>
**3. df.notnull()** <br>
**4. df.duplicated()** <br>
**5. df.value_counts()** <br>
**6. df.unique()** <br>

## Definition of missing data
```
会被认为是missing data的-- isnull() is true:
'np.nan'(numpy NaN),'None'(Python None),'pd.Nat'(pandas时间缺失），‘pd.NA'(pandas 通用缺失）

不会被认成missing data的--isnull() is False:
'NaN'(字符串），""(空字符串），'0'，'False(布尔值）'
```

## 1.2 df.isnull()，df.isna()
```
# 统计缺失值，返回布尔值：True=缺失，False=不缺失
# df.isnull().sum() 每一行的缺失值，输出的是个数
# df.isnull().sum().sum() 所有缺失的值，输出的是个数

df = pd.DataFrame({
    'A': [1, np.nan, 3],
    'B': [4, 5, None]
})

print(df.isnull())  # 或 df.isna()，完全相同
#        A      B
# 0  False  False
# 1   True  False  
# 2  False   True
```

## 3. df.notnull()
```
#与isnull刚好相反，统计有值的框，True=有值，False=缺失
# df.notnull().sum() 每一行的缺失值，输出的是个数
# df.notnull().sum().sum() 所有缺失的值，输出的是个数

print(df.notnull())
#        A      B
# 0   True   True
# 1  False   True
# 2   True  False
```

## 4.df.duplicated()
```
#检测有没有重复行的，输出的是布尔值
#df.duplicated().sum() 检测出总共有多少重复
df2 = pd.DataFrame({
    'A': [1, 2, 1, 3],
    'B': [4, 5, 4, 6]
})

print(df2.duplicated())
# 0    False  # 第一次出现
# 1    False  # 唯一行
# 2     True  # 重复行！
# 3    False  # 唯一行
```

## 5.df.value_counts()
```
# 统计每个值出现的次数，自动排序
# df['叉叉叉'].value_counts()  可以查看这个框框里有哪些值，这些值又有几个
# # df['叉叉叉'].value_counts().head(10) 可以查看前十个
# df.iloc[:, 0].value_counts() 可以查看这个区段里有哪些值，这些值又有几个
# df['hr'].describe()  这个可以列出中位数，平均值，标准差
s = pd.Series(['A', 'B', 'A', 'C', 'A'])
print(s.value_counts())
# A    3
# B    1  
# C    1
```

## 6.df.unique()
```
# 和value有点像 但是比value 费一点，value还多一个统计数值
s = pd.Series(['A', 'B', 'A', 'C', 'A'])
print(s.unique())
# ['A' 'B' 'C']

# 返回去重后的唯一值数组
```
