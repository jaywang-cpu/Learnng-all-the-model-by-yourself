**If you add spaces in your print code, those spaces will show up in the output**
![](https://github.com/jaywang-cpu/Learnng-all-the-model-by-yourself/blob/main/figure/Algorithms/space%20in%20coding.png)

--------------------
**基础概念**
- 函数：独立工具，print(),len() 带有功能
- 方法：对象的技能，my_list.append(4)
- 类名：对象的模版，KNNClassifier(k=3), knnclassifier是类名，创建对象

--------------------
**括号选择**
- 圆括号（）： 执行动作。 1.函数名（参数）#调用函数 2.方法名（参数） #调用方法  3.类名（参数） #创建对象
- 方括号[]: 容器或访问。 1.[元素] #创建访问列表  2.容器[索引]  #访问元素
- 花括号{}: 键值对容器。 1.{key:value} #字典  2.{元素}

--------------------
**括号个数**
- 添加类方法：一次只能加一个，多个要打包（（a,b,c）） append,count, index, upper, split....
- 计算类函数：多个参数直接传，只要一个括号就行 max(a,b,c), min, print, format
- 问自己需要的一组数据（（）），还是多个独立的数据（）

--------------------
**bias，varience**
- bias: 预估值与实际值的差别
- varience：简单来说就是数据的离散程度，可以衡量模型的稳定性
- over-fiting: 训练级贴合很好，测试级别下降很多
- under-fitting:训练集贴合不好，测试级别也不好
- bias和模型复杂度成正比，varience与模型的复杂度成反比

![](https://github.com/jaywang-cpu/Learnng-all-the-model-by-yourself/blob/main/figure/Algorithms/Bias%20Vs%20Varience.png)
