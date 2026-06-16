# kaggle-house_price_linear_regression
本仓库是《人工智能》课程论文“基于线性回归算法的房价预测模型复现与分析”的配套代码。基于 Kaggle 房价数据集，实现数据清洗、特征选择、多元线性回归建模、模型评估与可视化，最终生成可提交至 Kaggle 的预测结果。
本项目复现了经典的多元线性回归算法，并将其应用于 Kaggle 平台的“House Prices: Advanced Regression Techniques”竞赛数据集。通过该系统性的实验，验证了线性回归算法在房价预测任务上的有效性，并分析了其优势和局限性。

主要特点：
完整的数据预处理流程（缺失值处理、特征筛选）
基于 Pearson 相关系数的特征选择
多元线性回归模型训练与验证
模型评估（MSE、RMSE、R²）
可视化分析（真实值 vs 预测值、残差图）
生成符合 Kaggle 提交格式的预测文件

技术栈
工具	版本
Python	3.10+
Pandas	1.5.0+
NumPy	1.24.0+
Scikit-learn	1.3.0+
Matplotlib	3.7.0+
Seaborn	0.13.0+

项目结构
kaggle-house_price_linear_regression/
│
├── house_price_linear_regression.py   # 主程序：完整建模流程
├── train.csv                          # 训练数据集（需自行从Kaggle下载）
├── test.csv                           # 测试数据集（需自行下载）
├── sample_submission.csv              # Kaggle 提交示例（可选）
├── submission.csv                     # 生成的预测结果
├── linear_regression_eval.png         # 模型评估可视化图表
├── README.md                          # 本文件
└── requirements.txt                   # 项目依赖列表

数据集来源
本实验使用 Kaggle 平台上的 House Prices: Advanced Regression Techniques 竞赛数据集。
竞赛主页：https://www.kaggle.com/competitions/house-prices-advanced-regression-techniques
训练集：train.csv（1460 条样本，79 个特征）
测试集：test.csv（1459 条样本，用于预测）

程序运行完成后，将在控制台输出以下信息：
数据集基本信息（训练集和测试集的大小）
特征相关系数（各特征与 SalePrice 的相关性排序）
选中的 Top K 特征（默认取前 8 个）
模型系数（每个特征的权重）
验证集评估指标（MSE、RMSE、R²）

程序运行后会在当前目录生成以下文件：
linear_regression_eval.png
submission.csv

以下是模型在验证集（20% 的原始训练数据）上的评估结果：
评估指标	数值
均方误差（MSE）	1.87 × 10⁹
均方根误差（RMSE）	43,235.21
决定系数（R²）	0.7563
R² = 0.7563 表明该线性回归模型能够解释约 75.6% 的房价变异，验证了线性回归算法在房价预测任务上的有效性。

选择的特征
通过 Pearson 相关系数分析，以下 8 个特征与房价相关性最高，被选入最终模型：

排名	特征	含义	相关系数
1	GrLivArea	地上居住面积	0.709
2	GarageCars	车库容量	0.640
3	GarageArea	车库面积	0.623
4	TotalBsmtSF	地下室总面积	0.614
5	1stFlrSF	一楼面积	0.606
6	FullBath	完整浴室数量	0.561
7	TotRmsAbvGrd	地上房间总数	0.534
8	YearBuilt	建造年份	0.523

程序会自动生成并保存以下两张图：
左图：真实值 vs 预测值
散点越接近红线（理想预测线），说明模型预测越准确。从图中可以看出，大部分点集中在红线附近，说明模型具有较好的预测能力。
右图：残差图
残差随机分布在零线两侧，无明显规律，说明模型没有系统性偏差，满足线性回归的基本假设。
