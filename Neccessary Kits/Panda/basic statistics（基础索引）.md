# Overview
A. **df['column']--Selecting single column <br>**
B. **df[['col1','col2']]--Selecting multi-columns<br>**
C. **df.loc[]--Tag-based index<br>**
D. **df.iloc[]--Location-bases index<br>**
E. **df.at[]--Single value access (tag)<br>**
F. **df.iat[]--Single value access (location)<br>**

## Conclusion
```
# 选择方式对比
df['name']          # 单列 → Series(Series 可以是任何类型，不限于数值。它是一维数据，有索引但没有列名）
df[['name']]        # 单列 → DataFrame  
df[['name', 'age']] # 多列 → DataFrame

# 索引方式对比
df.loc[0, 'name']   # 标签索引 → 单值
df.iloc[0, 1]       # 位置索引 → 单值
df.at[0, 'name']    # 标签索引 → 单值（更快）
df.iat[0, 1]        # 位置索引 → 单值（更快）

# 使用建议
# - 选择列：用df['col']或df[['col1', 'col2']]
# - 切片选择：用df.loc[]或df.iloc[]  
# - 单值访问：用df.at[]或df.iat[]（性能更好）

# ⚠️ 容易犯错的重点：
# - df[0] ❌ DataFrame不支持数字索引行！  正确：df.iloc[0] 或 df.loc[0] 来选择行
# - df['name', 'age'] ❌ 不接受元组，只接受字符串或列表 正确：df[['name', 'age']] 用列表选择多列
```

## A df['column']-Selecting single column 
```
import pandas as pd
df = pd.DataFrame({
    'name': ['Alice', 'Bob', 'Charlie'],
    'age': [25, 30, 35],
    'city': ['NYC', 'LA', 'Chicago']
})

# 选择单列，返回Series
result = df['name']
print(result)
# 0      Alice
# 1        Bob
# 2    Charlie
# Name: name, dtype: object
```

## B. df[['name','age']]-Selecting multi-colunms
```
# 选择多列，返回DataFrame
# 注意：双重方括号！
result = df[['name', 'age']]
print(result)
#      name  age
# 0   Alice   25
# 1     Bob   30
# 2 Charlie   35

# 单方括号会报错
# df['name', 'age']  # ❌ 错误写法
```

## df.loc[]--Tag-based index （名字来找）
```
# 按行标签和列标签选择
df.loc[0, 'name']           # 单个值: 'Alice'--就像美国地址一样先小后大
df.loc[0:1, 'name':'age']   # 行0-1，列name到age 只写一个name or age 也是ok的
df.loc[df['age'] > 25, :]   # 条件选择所有列 df['age'] > 25返回的是布尔值，得益于外面的[],将布尔值只保留True的然后输出 

# 设置有意义的索引
df.set_index('name', inplace=True)
df.loc['Alice', 'age']      # Alice是行，age是列，所以这里我们需要的是Alice的age
```

## df.iloc[]--Location-bases index（数字来找）
```
