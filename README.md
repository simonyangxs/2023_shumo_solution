# 2023_shumo_solution
Work with ZY and LXF at ShanghaiTech University for [“HUAWEI CUP” THE 20TH CHINA POST-GRADUATE MATHEMATICAL CONTEST IN MODELING](https://cpipc.acge.org.cn/cw/hp/4)


## 问题一

首先根据血肿扩张的定义标记血肿扩张事件；接着进行数据清洗，依据3σ原则对异常值进行分析，并采用最大最小归一化消除特征量纲。依次使用灰色相关度分析、弹性回归网络、SVM递归特征消除进行特征选择，在进行卡方独立性检验后得出最具代表性、独立性的10个特征用于预测血肿扩张概率。全面评估17种不同的机器学习模型（MLP、随机森林等）后，在测试集上的AUC达到了0.91。

## 问题二

使用LOF异常检测算法去除全体患者水肿体积数据中的离群点，并对比多项式回归、ARIMA等7种不同回归模型的拟合效果，为分亚组后的数据拟合提供模型参考；使用LSTM自编码器对患者水肿体积时序数据进行特征学习，再经过t-SNE降维数据后使用K-means对水肿模式进展进行聚类，根据轮廓系数确定最优的3类亚组，将亚组上的$R^2$最高提升到0.294。随后基于已识别出的水肿进展模式分析与治疗方法之间的关联，采用Person相关系数分析单个治疗方法对水肿进展的影响；采用桑基图可视分析不同治疗方案组合对水肿进展的影响。利用LSTM自编码器对血肿体积的模式分组与One-Hot编码的治疗方法特征对水肿进展进行预测，随机森林模型的多分类Acc指标可达50%，验证了治疗方案、血肿体积与水肿体积间存在的关联。

## 问题三

首先利用问题一中的特征工程流程对数据进行处理，然后在文献调研的基础上使用线性、树形和深度学习等15种机器学习模型对患者预后90天mRS评分进行有序分类预测，其中CatBoost模型的Acc达到了73%。接着，参考问题二中对时序数据的提取方法，通过挖掘患者水肿和血肿的时序影像特征，将90天mRS预测任务的Acc提高到81%。最后，使用Person相关系数和训练后的模型（参数权重和SHAP值）分析了90天mRS和各变量之间的关联关系，并为临床决策提出建议。