#  Overview
A Conclusion <br>
B Basic Indexing (基本索引)<br>
C Slicing Operations (切片操作)<br>
D 2D Array Indexing (二维数组索引)<br>
E 2D Slicing (二维切片)<br>
F Boolean Indexing (布尔索引)<br>
G Fancy Indexing (花式索引)<br>
H Conditional Selection (条件选择)<br>
I Multiple Condition Selection 多条件选择

## A Conclusion
1.
* [:n] → 取到索引n之前的所有元素（共n个元素），
* [-n:] → 取倒数n个元素

2.
*  正着 第n个到第m个--[n-1,m]
*  反者 倒数第m个到倒数第n个--[-m,-(n-1)]
*  **重点：所以最简单的方式，就是判断第几个到第几个然后带公式，你要可以马上根据公式反映出来这个第几个到第几个**

3. 不管正的还是负的，end-start=元素的个数
4. 多条件要加括号：`(条件1) & (条件2)`
5. 切片是**左闭右开**区间 `[start, end)`
6. - 布尔索引用`&`和`|`，不是`and`和`or`


## B. 基础索引
```python
import numpy as np
arr = np.array([1, 2, 3, 4, 5, 6, 7, 8, 9, 10])

arr[0]      # 第一个元素: 1
arr[-1]     # 最后一个元素: 10
arr[2]      # 第三个元素: 3
```

## C. 切片操作
```python
arr[:5]     # 前5个: [1 2 3 4 5]
arr[2:7]    # 索引2到6: [3 4 5 6 7]
arr[::2]    # 每隔一个: [1 3 5 7 9]
arr[::-1]   # 倒序: [10 9 8 7 6 5 4 3 2 1]
arr[1::3]   # 从索引1开始每隔3个: [2 5 8]
```

## D. 二维数组索引
```python
arr_2d = np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]])

arr_2d[0, 1]    # 第1行第2列: 2
arr_2d[1]       # 第2行: [4 5 6]
arr_2d[:, 0]    # 第1列: [1 4 7]
arr_2d[0, :]    # 第1行: [1 2 3]
```

## E. 二维切片
```python
arr_2d[:2, :2]  # 前2行前2列: [[1 2] [4 5]]
arr_2d[1:, 1:]  # 从第2行第2列开始: [[5 6] [8 9]]
arr_2d[::2, ::2] # 隔行隔列: [[1 3] [7 9]]
```

## F. 布尔索引
```python
arr > 5         # 布尔数组: [False False False False False True True True True True]
arr[arr > 5]    # 大于5的元素: [6 7 8 9 10]
arr[arr % 2 == 0] # 偶数: [2 4 6 8 10]
```

## G. 花式索引
```python
indices = [0, 2, 4]
arr[indices]    # 指定索引的元素: [1 3 5]

arr_2d[[0, 2], [1, 0]]  # 取(0,1)和(2,0)位置: [2 7]
```

## H. 条件选择
```python
np.where(arr > 5, arr, 0)  # 大于5保留，否则为0: [0 0 0 0 0 6 7 8 9 10]
np.where(arr > 5)          # 返回索引: (array([5, 6, 7, 8, 9]),)
```

## I. 多条件
```python
mask = (arr > 3) & (arr < 8)  # 3到8之间
arr[mask]       # [4 5 6 7]

arr[(arr > 2) | (arr < 1)]    # 大于2或小于1
```


