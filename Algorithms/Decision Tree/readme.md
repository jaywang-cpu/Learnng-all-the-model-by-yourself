# Decision Tree

## Definition 
Decision Tree is a supervised learning algorithm that creates a tree-like model of decisions to predict target values through recursive（递进的） binary splitting. 
Just like a doctor's diagnosis: step by step narrowing down the possibilities based on symptoms to reach a final diagnosis! 🌳
![](https://github.com/jaywang-cpu/Learnng-all-the-model-by-yourself/blob/main/figure/Algorithms/Structure%20of%20decision%20tree.png)
* leaf node: four pie charts
* parent node: Expression correlation>0.9
* children node：those in the middle
----------------------------
## How to evalute it 
### 1. Entropy
#### *Defintion*
we use entropy to quantify the similarity or difference in the node, stands for the chaosity within the node, more close to 0 more close to purity, 1 means half-half possibility which have the most impurity.

#### *Calculation*
The easiest way to calculate it :https://www.youtube.com/watch?v=YtebGVx-Fxw (very easy to understand)
![](https://github.com/jaywang-cpu/Learnng-all-the-model-by-yourself/blob/main/figure/Algorithms/Entropy.jpg)

### 2. Gini Index

#### *Definition*
We use Gini index to measure the impurity or inequality within a node. It represents the probability of incorrectly classifying a randomly chosen element if it were randomly labeled according to the distribution of labels in the node. Gini = 0 indicates perfect purity (all samples belong to one class), while higher values indicate more impurity.

#### *Calculation*
The Gini index is calculated as:
**Gini = 1 - Σ(pi)²**

Where pi is the probability of class i in the node.

For a binary classification:
- If all samples are the same class: Gini = 0 (pure)
- If samples are evenly split (50-50): Gini = 0.5 (maximum impurity)

#### *Example*
Node with 100 samples: 60 Class A, 40 Class B
- P(A) = 60/100 = 0.6
- P(B) = 40/100 = 0.4
- Gini = 1 - (0.6² + 0.4²) = 1 - (0.36 + 0.16) = 0.48

### 3.Key difference from Entropy
Gini index is computationally faster (no logarithms) and ranges from 0 to 0.5 for binary classification, while entropy ranges from 0 to 1.

-------------------------------------
## Important concept

| 概念 | 简单定义 | 公式/怎么用 | 为什么重要 |
|------|----------|-------------|------------|
| **Information Gain** | 衡量分割后信息的改善程度 | `the entropy of parents substract children's` | 选择最好的分割特征 ，越大越好|
| **Information Gain Ratio** | 修正版的信息增益 | `Gain Ratio = Information Gain / Intrinsic Information` | 让选择更公平 |
| **Pre-pruning (预剪枝)** | 提前停止长树 | `max_depth=5`, `min_samples_split=10` | 防止树长得太复杂 |
| **Post-pruning (后剪枝)** | 砍掉没用的树枝 | 先长完整树，再删除多余部分 | 让树更简洁有效 |
| **连续特征分割Continuous Feature Splitting** | 处理数字数据 | 找个数字当分界线：`age ≤ 30` | 能处理年龄、收入等数据 |
| **类别特征分割Categorical Feature Splitting** | 处理文字数据 | 按类别分组：`color = red/blue/green` | 能处理颜色、性别等数据 |
| **过拟合问题Overfitting Problem** | 树记住了训练数据的细节 | 在新数据上表现差 | 需要控制树的复杂度 |
| **特征偏向Feature Bias** | 偏爱"选项多"的特征 | 比如选择"城市"而不是"性别" | 可能选错重要特征 |
| **缺失值处理Missing Values Handling** | 有些数据空白怎么办 | 用其他方法填补或单独处理 | 让算法更实用 |



