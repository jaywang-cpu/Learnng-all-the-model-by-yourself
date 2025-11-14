# Overview

**理论上的**：
- ***level1***: 集成学习（Bagging，Boosting 区别/ 弱学习器组合原理），梯度提升核心（残差学习概念/梯度下降在树模型中的应用），决策树基础（树的构建过程/树的剪枝机制）
- ***level2***: 牛顿法优化（二阶泰勒展开/牛顿法vs梯度下降），正则化机制（L1/L2正则化/正则化参数含义），系统优化（并行计算/内存优化/缺失值处理）
- ***level3***: 数学原理（目标函数构成/ 分裂增益计算/ 叶子权重计算), 算法细节（近似贪心算法/分块并行）

-------------------------

**代码上的**：
- ***level1***基础使用
```
---环境搭建
# 安装和导入
pip install xgboost
import xgboost as xgb
from xgboost import XGBRegressor, XGBClassifier

---基本训练流程
# 数据准备
[ ] 数据加载和预处理 [ ] 训练集/验证集/测试集划分[ ] 特征工程基础
# 模型训练
[ ] 回归任务: XGBRegressor[ ] 分类任务: XGBClassifier  [ ] 基本fit和predict
# 模型评估
[ ] 回归指标: MSE, MAE, R²[ ] 分类指标: Accuracy, Precision, Recall, F1, AUC

---数据格式处理
[ ] pandas DataFrame → XGBoost[ ] numpy array → XGBoost[ ] DMatrix格式使用 [ ] 稀疏矩阵处理
```
- ***level2***:参数调优
```
--- 核心参数理解
# 树结构参数
[ ] n_estimators: 树的数量 (50-2000)[ ] max_depth: 树的深度 (3-10)[ ] min_child_weight: 叶子节点最小权重 (1-10)[ ] subsample: 样本采样比例 (0.6-1.0)[ ] colsample_bytree: 特征采样比例 (0.6-1.0)
# 学习参数
[ ] learning_rate/eta: 学习率 (0.01-0.3)[ ] objective: 目标函数选择[ ] eval_metric: 评估指标
# 正则化参数
[ ] reg_alpha: L1正则化 (0-10)[ ] reg_lambda: L2正则化 (1-10)[ ] gamma: 分裂惩罚 (0-10)

---调参策略
# 网格搜索
[ ] GridSearchCV使用[ ] RandomizedSearchCV使用[ ] 参数空间设计
# 贝叶斯优化
[ ] Optuna使用[ ] hyperopt使用
# 手动调参
[ ] 粗调 → 精调流程[ ] 参数敏感性分析

---早停和验证
[ ] early_stopping_rounds设置[ ] eval_set验证集使用[ ] 学习曲线绘制[ ] 过拟合检测
```

- ***level3***:高级技巧（专家级别）
```
---模型诊断
# 特征重要性
[ ] feature_importances_属性[ ] plot_importance()可视化[ ] SHAP值计算和解释
# 模型解释
[ ] 部分依赖图[ ] 个体预测解释[ ] 特征交互分析

---性能优化
# 计算优化
[ ] n_jobs并行设置[ ] GPU加速 (tree_method='gpu_hist') ] 内存优化技巧
# 大数据处理
[ ] 增量学习[ ] 数据采样策略[ ] 分布式训练
```
