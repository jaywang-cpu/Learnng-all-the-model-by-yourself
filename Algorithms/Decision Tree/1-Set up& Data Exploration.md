# Necessary kits
```python with explanation
# Data manipulation and analysis
import pandas as pd  #Excel Pro
import numpy as np   #超级计算器

# Data visualization
import matplotlib.pyplot as plt #精装ps
import seaborn as sns #ins的滤镜

# Machine learning library
import sklearn
from sklearn.model_selection import train_test_split #数据预处理的
from sklearn.tree import DecisionTreeClassifier    #DecisionTreeClassifier 是一个用于分类任务的决策树算法实现
from sklearn.metrics import accuracy_score, classification_report #评估模型的
from sklearn.preprocessing import LabelEncoder #将文本转化为数字的

# Tree visualization
from sklearn.tree import plot_tree, export_text #输出树的图片 输出树的文本框
import graphviz #输出高质量的文档，输出的图片最好
from sklearn.tree import export_graphviz

# Other utilities
import pickle  # 保存/加载训练好的决策树模型
import warnings #保持输出整洁，专注于重要信息
warnings.filterwarnings('ignore') #保持输出整洁，专注于重要信息

# Set random seed for reproducibility
np.random.seed(42) #是为了让不同的人跑你的代码，得出来的准确度都是一样的，里面其实可以是任何数字，选择42其实是程序员的浪漫，"生命、宇宙以及一切的答案是42"
```
## Copy it Directly Into Your Book
```
import pandas as pd 
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
import sklearn
from sklearn.model_selection import train_test_split
from sklearn.tree import DecisionTreeClassifier
from sklearn.metrics import accuracy_score, classification_report
from sklearn.preprocessing import LabelEncoder
from sklearn.tree import plot_tree, export_text
import graphviz
from sklearn.tree import export_graphviz
import pickle
import warnings
warnings.filterwarnings('ignore')
np.random.seed(42)
