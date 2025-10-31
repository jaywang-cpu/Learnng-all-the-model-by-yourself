# Decision Tree

## Definition 
Decision Tree is a supervised learning algorithm that creates a tree-like model of decisions to predict target values through recursive（递进的） binary splitting. 
Just like a doctor's diagnosis: step by step narrowing down the possibilities based on symptoms to reach a final diagnosis! 🌳
![](https://github.com/jaywang-cpu/Learnng-all-the-model-by-yourself/blob/main/figure/Algorithms/Structure%20of%20decision%20tree.png)
* leaf node: four pie charts
* parent node: Expression correlation>0.9
* children node：those in the middle

## How to evalute it 
### 1. Entropy
#### Defintion
we use entropy to quantify the similarity or difference in the node, stands for the chaosity within the node, more close to 0 more close to purity, 1 means half-half possibility which have the most impurity.

The easiest way to calculate it :https://www.youtube.com/watch?v=YtebGVx-Fxw (very easy to understand)
![](https://github.com/jaywang-cpu/Learnng-all-the-model-by-yourself/blob/main/figure/Algorithms/Entropy.jpg)
