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
2. 分类处理原则-按数据类型分类处理
```
def preprocess_data(df):
    # 1. 先分类 - 把数据按类型分组
    numeric_cols = df.select_dtypes(include=[np.number]).columns
    categorical_cols = df.select_dtypes(include=['object']).columns
    datetime_cols = df.select_dtypes(include=['datetime']).columns
    
    # 2. 分别处理 - 每类用不同方法
    for col in numeric_cols:
        # 数值型处理逻辑
    
    for col in categorical_cols:
        # 分类型处理逻辑
    
    for col in datetime_cols:
        # 时间型处理逻辑
```
3. 循环设计的三步法-循环设计思维：检查-处理-记录
```
# 标准循环模板
for col in columns:
    # 步骤1: 检查条件
    if 需要处理这一列吗?:
        
        # 步骤2: 执行处理
        try:
            处理逻辑
            
        # 步骤3: 记录结果
        except Exception as e:
            记录错误
        else:
            记录成功
实际例子
def handle_missing_values(df):
    processed_df = df.copy()
    processing_log = []
    
    for col in df.columns:
        # 1. 检查：这列有缺失值吗？
        if df[col].isnull().sum() > 0:
            
            # 2. 处理：根据类型选择填充方法
            try:
                if df[col].dtype in ['int64', 'float64']:
                    # 数值型：用均值填充
                    fill_value = df[col].mean()
                    processed_df[col] = processed_df[col].fillna(fill_value)
                else:
                    # 分类型：用众数填充
                    fill_value = df[col].mode()[0]
                    processed_df[col] = processed_df[col].fillna(fill_value)
                
                # 3. 记录：处理成功
                processing_log.append(f"✅ {col}: 填充了 {df[col].isnull().sum()} 个缺失值")
                
            except Exception as e:
                # 3. 记录：处理失败
                processing_log.append(f"❌ {col}: 处理失败 - {str(e)}")
    
    return processed_df, processing_log
```
4. 信息保存原则--处理过程中保存所有重要信息
```
def preprocess_data_complete(df, target_column):
    # 准备信息容器
    preprocessing_info = {
        'original_shape': df.shape,
        'missing_values_before': df.isnull().sum().to_dict(),
        'data_types_before': df.dtypes.to_dict(),
        'encoders': {},
        'scalers': {},
        'processing_steps': [],
        'errors': []
    }
    
    processed_df = df.copy()
    
    # 每个处理步骤都记录信息
    try:
        # 处理缺失值
        processed_df, log = handle_missing_values(processed_df)
        preprocessing_info['processing_steps'].extend(log)
        
        # 编码分类变量
        processed_df, encoders = encode_categorical_features(processed_df)
        preprocessing_info['encoders'] = encoders
        
        # 特征缩放
        processed_df, scaler = scale_features(processed_df)
        preprocessing_info['scalers'] = scaler
        
        # 记录最终信息
        preprocessing_info['final_shape'] = processed_df.shape
        preprocessing_info['missing_values_after'] = processed_df.isnull().sum().to_dict()
        
    except Exception as e:
        preprocessing_info['errors'].append(str(e))
    
    return processed_df, preprocessing_info
```

5.模块化思维（Modular Thinking）-每个功能一个函数，主函数负责协调
```
# 每个小功能独立成函数
def check_data_quality(df):
    """检查数据质量"""
    pass

def handle_missing_values(df):
    """处理缺失值"""
    pass

def encode_categorical_features(df):
    """编码分类特征"""
    pass

def scale_numerical_features(df):
    """缩放数值特征"""
    pass

# 主函数负责协调
def preprocess_data(df, target_column):
    """主预处理函数 - 协调所有步骤"""
    
    # 1. 数据质量检查
    quality_report = check_data_quality(df)
    
    # 2. 处理缺失值
    df_filled, fill_info = handle_missing_values(df)
    
    # 3. 编码分类特征
    df_encoded, encoders = encode_categorical_features(df_filled)
    
    # 4. 缩放数值特征
    df_scaled, scalers = scale_numerical_features(df_encoded)
    
    return df_scaled, {
        'quality_report': quality_report,
        'fill_info': fill_info,
        'encoders': encoders,
        'scalers': scalers
    }
```

   
