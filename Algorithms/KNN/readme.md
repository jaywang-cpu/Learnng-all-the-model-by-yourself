# Overview
**1.definition** <br>
**2.Coding**<br>


# Definition

## what is KNN
k-Nearest Neighbors 是一种基于实例的监督学习算法，通过寻找K个最相思的邻居来对新数据点进行分类或者回归预测（核心细想：物以类聚），最核心的四个步骤便是，找距离，选择邻居个数，选出邻居，决定规则

## 算法特点
- lazy learning: 无需训练，直接存储所有训练数据
- Non-parametric: 不对数据分布作任何假设
- Instance-learning：基于具体实例进行预测

## 四个核心要素

### 距离（Distance)
- 欧几里得距离：直线距离，最常用 90%：  sqrt((x1-y1)² + (x2-y2)² + ... + (xn-yn)²)
- 曼哈顿距离：网格距离，适合高位数据：  |x1-y1| + |x2-y2| + ... + |xn-yn|
- 闵可夫斯基距离：通用万能距离公式：    (|x1-y1|^p + |x2-y2|^p + ... + |xn-yn|^p)^(1/p)  

### 邻居个数（K值）
- 决定多少个最近邻居进行决策
- 通常选择奇数，避免后面投票是平票
- 常用值：3，5，7，9
- 大小容易过拟合（只听一个），太大容易欠拟合（谁的都听）

### 确定邻居
- 计算新点到训练点的数据
- 按距离从小到大排序
- 选前K个做为邻居

### 最后判决（Final Decision)
- 分类任务：多数投票（Majority Voting）：5个里面3个垃圾邮件-预测为垃圾邮件
- 回归任务：取平均值（Average）：3个邻居，1-300w，2-320w，3-280w，那么这个新数据取平均值就行

# Coding
## distance
```
import numpy as np
from collections import Counter
import matplotlib.pyplot as plt
from sklearn.datasets import make_classification, make_regression
from sklearn.model_selection import train_test_split

# 距离计算函数
def euclidean_distance(point1, point2):
    """计算欧几里得距离"""
    return np.sqrt(np.sum((np.array(point1) - np.array(point2))**2))

def manhattan_distance(point1, point2):
    """计算曼哈顿距离"""
    return np.sum(np.abs(np.array(point1) - np.array(point2)))

def minkowski_distance(point1, point2, p=2):
    """计算闵可夫斯基距离"""
    return np.sum(np.abs(np.array(point1) - np.array(point2))**p)**(1/p)
```

## Function achieved
### 分类任务实现
```
import numpy as np
from collections import Counter #自动记票机器

def euclidean_distance(point1, point2):
    """计算欧几里得距离"""
    return np.sqrt(np.sum((np.array(point1) - np.array(point2))**2))

class KNNClassifier:
    def __init__(self, k=3): #就像对一个手机的初始设置，这个是python语法规定，类的第一个参数必须是self
        """
        初始化KNN分类器
        参数: k - 邻居个数
        """
        self.k = k   #把外面传进来的k存储到self k中
        
    def fit(self, X_train, y_train):       #fit就是教学过程，学习规律，存储数据
        """训练KNN（实际上只是存储数据）"""
        self.X_train = np.array(X_train) #这里的X-train 存储的是坐标
        self.y_train = np.array(y_train) #这里的Y-train 存储的是类别
        
    def _get_neighbors(self, test_point):
        """获取K个最近邻居"""
        distances = []
        
        # 计算到所有训练点的距离
        for i in range(len(self.X_train)):
            dist = euclidean_distance(test_point, self.X_train[i])
            distances.append((dist, self.y_train[i]))
        
        # 按距离排序，取前K个
        distances.sort(key=lambda x: x[0]) #key 就是按照什么排序，lambda就是一个一次性函数，x[0]就是按照第一个元素排序
        neighbors = [label for _, label in distances[:self.k]] 
        
        return neighbors
    
    def predict_single(self, test_point):
        """预测单个数据点"""
        neighbors = self._get_neighbors(test_point) #就相当于是已经定义了上面的test点了，就输出三个邻居的建议
        
        # 多数投票
        prediction = Counter(neighbors).most_common(1)[0][0] #选取获胜者
        return prediction
    
    def predict(self, X_test):
        """预测多个数据点"""
        predictions = []
        for test_point in X_test:
            pred = self.predict_single(test_point)
            predictions.append(pred)
        return np.array(predictions)
    
    def score(self, X_test, y_test):
        """计算准确率"""
        predictions = self.predict(X_test)
        accuracy = np.mean(predictions == y_test)
        return accuracy
```
### 回归任务
```
import numpy as np

def euclidean_distance(point1, point2):
    """计算欧几里得距离"""
    return np.sqrt(np.sum((np.array(point1) - np.array(point2))**2))

class KNNRegressor:
    def __init__(self, k=3):
        """
        初始化KNN回归器
        参数: k - 邻居个数
        """
        self.k = k
        
    def fit(self, X_train, y_train):
        """训练KNN（实际上只是存储数据）"""
        self.X_train = np.array(X_train)  # 存储特征（如房屋面积、位置等）
        self.y_train = np.array(y_train)  # 存储数值（如房价、温度等）
        
    def _get_neighbors_values(self, test_point):
        """获取K个最近邻居的数值"""
        distances = []
        
        # 计算到所有训练点的距离
        for i in range(len(self.X_train)):
            dist = euclidean_distance(test_point, self.X_train[i])
            distances.append((dist, self.y_train[i]))
        
        # 按距离排序，取前K个
        distances.sort(key=lambda x: x[0])
        neighbor_values = [value for _, value in distances[:self.k]]
        
        return neighbor_values
    
    def predict_single(self, test_point):
        """预测单个数据点"""
        neighbor_values = self._get_neighbors_values(test_point)
        
        # 取平均值（而不是投票）
        prediction = np.mean(neighbor_values)
        return prediction
    
    def predict(self, X_test):
        """预测多个数据点"""
        predictions = []
        for test_point in X_test:
            pred = self.predict_single(test_point)
            predictions.append(pred)
        return np.array(predictions)
```
