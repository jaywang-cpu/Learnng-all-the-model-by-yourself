# Learnng-all-the-model-by-yourself

## The reason of creating this repo 
I am a beginner in machine learning, deep learning, and other algorithms, but I am confident in mastering them well. I have developed a comprehensive learning plan that consists of two main parts: necessary tools and different algorithms.For the necessary tools, there are many available options, and I plan to learn from their official websites. To maximize my time efficiency, I will follow the **80/20 principle - spending 80% of my time on the 20% most important concepts**, while learning other topics only when needed.For algorithms, I will apply the same approach: maximizing the benefit of my time by focusing on the most vital 20% of content and **learning from open-source coding resources shared by GitHub contributors**.

## Contents we have for kits and algorithms.
* **Kits**：*Pytorch* (Machine learning master), *Scikit-learn* (Machine learning master), *Numpy* (Master in calculating), *Panda* (Exceel Pro), *Matplotlib* (Function like ps), *Seaborn* (The fliter of instagram)， *Simpletk/itk* (master in medical processing)， *Nibabel* (master in neural imaging processing), *OpenCV* ( Multi-functional imaging kits)
* **Algorithms**：**[Top1]** *Logistic Regression*, *Random Forest*, *Convolutional Neural Network(CNN)*, *U-Net*, *XGBoost*.
**[Top2]** *SVM*, *ResNet*, *LSTM*, *GCN*, *Vison Transformer*, *Gradient Boosting*. **[Top3]** *GAT*, *3D CNN*, *Multi-Modal Fusion*, *Attention U-Net*, *EfficientNet*, *BERT for Medical*. **[Top4]** *K-means*, *PCA*, *t-SNE/UMAP*, *Autoencoder*, *VAE*, *GAN*.

![](https://github.com/jaywang-cpu/Learnng-all-the-model-by-yourself/blob/main/figure/Algorithms/Beautiful%20Picture.png)


## 写代码的流程和原则
- 大体框架
问题定义 → 需求分析 → 系统设计 → 算法选择 → 编码实现 → 测试验证 → 优化迭代
    ↑                                                        ↓
    ←←←←←←←←←←←←←←←← 持续改进循环 ←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←

- 内部框架
1. 容器优先 - 先准备盒子，再装东西
``` 
# ❌ 错误思维：边想边装
def preprocess_data(df):
    # 直接开始处理，没有规划容器
    df['age'] = df['age'].fillna(df['age'].mean())
    # 后面发现需要记录处理信息，但没地方放...

# ✅ 正确思维：先准备容器
def preprocess_data(df):
    # 1. 准备结果容器
    processed_df = df.copy()
    processing_log = []
    encoders = {}
    scalers = {}
    
    # 2. 再开始处理
    # 现在有地方放所有东西了
```

