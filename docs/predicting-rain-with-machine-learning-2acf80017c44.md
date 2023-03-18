# 用机器学习预测降雨

> 原文：<https://towardsdatascience.com/predicting-rain-with-machine-learning-2acf80017c44>

## 机器学习

## 明天会下雨吗？让我们建立一个人工智能模型来回答这个问题。

![](img/bdf39886d837c0ac43ec08ab939ad98c.png)

照片由[Atilla bingl](https://unsplash.com/@abingol?utm_source=medium&utm_medium=referral)在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄

寻找有趣的挑战来提高您的数据科学技能？

这是一个现实世界的问题。

## 问题陈述

> 天气对农业有着重要的影响，因此，预测天气有助于农民的日常决策，例如如何有效地计划、最小化成本和最大化产量。
> 
> 一家大型农业公司需要您帮助他们最大限度地提高增长效率、节约资源和优化生产。
> 
> 为了实现这些目标，该公司需要有一个准确的天气预测算法，这将改善他们对典型农业活动(如种植和灌溉)的决策。
> 
> 利用他们所在地区的历史天气信息，**你能预测未来几天的天气吗**？
> 
> [来源](https://bitgrit.net/competition/15)

你现在有了一个明确的目标。

## 目标🥅

根据三个标签预测第二天的天气。

*   `N` —无雨
*   `L` —小雨
*   `H` —暴雨

现在让我们来看看数据

## 数据[💾](https://emojipedia.org/floppy-disk/)

```
📂 **train**
 ├── region_A_train.csv
 ├── region_B_train.csv
 ├── region_C_train.csv
 ├── region_D_train.csv
 ├── region_E_train.csv
 ├── solution_format.csv
 └── solution_train.csv📂 **test**
 ├── region_A_test.csv
 ├── region_B_test.csv
 ├── region_C_test.csv
 ├── region_D_test.csv
 └── region_E_test.csv
```

数据被方便地分成训练和测试数据集。

在每一次训练和测试中，您都将获得天气数据，这些数据由命名为区域 A 到区域 E 的匿名位置组成，它们都是相邻的区域。

下面来看看`region_A_train.csv`的前五排

您应该注意到的第一件事是`date`列不是日期，而是被匿名化为某个随机值。

共有 10 个特征，由温度、降水、风速、风速方向和大气压力组成

然后，看着`solution_format.csv`

我们可以利用日期列将它与训练数据连接起来，并构建一个模型。

现在你对目标有了一个想法，对给你的数据有了一些了解，是时候动手了。

通过[注册](https://bitgrit.net/register)获得数据，参加[数据科学竞赛](https://bitgrit.net/competition/15)并跟随本文！

**本文代码→**[**Google collab**](https://colab.research.google.com/drive/1Bj5abt3p4o1tTDzJ0YunN7fLOriANNGT?usp=sharing)**或**[**deep note**](https://deepnote.com/project/weather-forecast-ffE1wpHBRaOpjtaoHzPYaw/%2Fweather-forecast-20220322-035931.ipynb)。

## 安装库和模型

首先，安装我们选择的武器:`[lightgbm](https://lightgbm.readthedocs.io/en/latest/)`

## 加载库

接下来，我们加载一些用于可视化和机器学习的基本库。

## 加载数据

让我们读入所有的数据。

# 探索性数据分析

有趣的部分到了，可视化数据。

## 将所有区域连接在一起

由于所有的区域数据共享一个主键`date`，我们可以将它们与 pandas 中的`[concat()](https://pandas.pydata.org/docs/reference/api/pandas.concat.html)`连接起来，并将这些键设置为区域名。

我不希望区域作为索引，所以我们可以重置索引，然后重命名一些列，以获得正确形状的数据。

## 目标阶层分布

让我们首先想象一下我们的目标类。

看起来我们手里有一个不平衡的职业，因为`N`标签统治了其余的职业。

为什么这是一个问题？

模型会偏向于样本量较大的类。

发生这种情况是因为分类器具有关于具有更多样本的类的更多信息，因此它学习如何更好地预测这些类，而它在较小的类上保持较弱。

在我们的例子中，标签`N`会比其他职业更容易被预测到。

让我们记住这一点，并向更多的可视化前进。

## 绘制特征

我们在每个地区都有十个特色。

是时候编造一些情节了。

因为所有区域都用于预测第二天的天气，所以让我们看看是否所有区域都具有相似的特征模式，以及是否存在任何异常值或异常值。

从图中，我们看到数据中的模式非常相似，除了区域 C、D、E 的`min.wind.speed`和`avg.wind.speed`在较低的比例上。

现在我们已经对数据进行了一些探索，我们检查数据中缺失的值。

# 缺少值

使用我的自定义助手函数，似乎有大量数据丢失给了`min.atmos.pressure`变量

我们还可以使用热图来可视化该列中缺失的数据。

我们有多种方法可以[处理丢失的数据](https://medium.com/bitgrit-data-science-publication/data-cleaning-with-python-f6bc3da64e45)。

让我们先来看看缺少值的列的分布。

由于列的分布非常正态，让我们用平均值来估算缺失的数据。

然后，我们对测试数据做同样的事情(笔记本中的全部代码)

# 特征预处理和工程

## 转换数据类型

让我们首先将标签添加到数据中。

然后我们看一下数据集的分类列。

我们必须将分类特征(包括目标变量)转换成数字格式。

让我们使用 [scikit-learn 的标签编码器](https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.LabelEncoder.html)来完成这项工作。

这里有一个在标签列上使用`LabelEncoder()`的例子

## 创建新的天气特征

既然我们已经有了一些天气特征，我们还可以设计一些有趣的新特征。

一个例子是[蒲福风级](https://www.spc.noaa.gov/faq/tornado/beaufort.html)，这是“一种将[风速](https://en.wikipedia.org/wiki/Wind_speed)与观察到的海上或陆地条件联系起来的经验测量方法。”

下面是一个功能，做我们的特征工程。

我们可以轻松地在训练和测试数据集上应用特征工程步骤。

# 准备列车数据

让我们看看目前为止的训练数据。

是时候[将我们的数据转换成更长的](https://pandas.pydata.org/pandas-docs/stable/user_guide/reshaping.html)格式了，这意味着区域不再是一列，每个特性都有自己的区域，比如`avg.temp_A`、`avg.temp_B`，直到`avg.temp_E`剩余的特性。

这样，数据将处于构建模型的正确状态。

我们可以使用熊猫的`[pivot_table](https://pandas.pydata.org/docs/reference/api/pandas.pivot_table.html)`功能来实现这一点。

列名不理想，所以我写了一个函数来解决这个问题。

这是目前为止的训练数据。

在我们对测试数据做了同样的操作后，就该拆分训练数据了。

LightGBM 喜欢给分类特征指定分类数据类型，所以我们就这么做吧。

我们可以使用`[train_test_split](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.train_test_split.html)`将我们的数据分成训练集和评估集。

是时候构建 LightGBM 模型了！

# LightGBM

让我们为一个简单的预测创建一个基础`[lgb.LGBMClassifier](https://lightgbm.readthedocs.io/en/latest/pythonapi/lightgbm.LGBMClassifier.html)`

然后我们可以`fit`训练数据。

然后我们对评估数据调用`predict`函数

# 模型性能

让我们看看一个基本的 LightGBM 分类器是如何工作的。

对于不平衡的数据集，99%的准确率可能毫无意义，因此我们需要更合适的指标，如精度、召回率和混淆矩阵。

## 混淆矩阵

让我们为我们的模型预测创建一个混淆矩阵。

首先，我们需要获得标签编码器给出的类名和标签，这样我们的图就可以显示标签名。

然后我们绘制一个非标准化和标准化的混淆矩阵。

正如你从图的阴影中看到的，我们的模型比其他模型更能预测标签`N`。

有了你在上图中看到的值，我们可以计算出一些指标，告诉我们我们的模型做得有多好。

## 分类报告

分类报告衡量分类算法的预测质量。

它回答了多少预测是真的，多少是假的问题。

更具体地说，它使用真阳性、假阳性、真阴性和假阴性来计算精确度、召回率和 f1 值

让我们来分解输出。

> 你的预测有百分之多少是正确的？
> `Recall` — *你们抓到的阳性病例占百分之多少？*
> `F1-score`—*—*—
> `support`—*每个给定类别的出现次数*

如果你仍然很难理解精确和回忆，[阅读这个伟大的解释](https://www.reddit.com/r/datascience/comments/qdai89/i_just_explained_recallprecision_to_a_nonds_and/)。

## 计算指标

以标签为`H`的类 0 为例，让我们根据混淆矩阵中的值来计算精确度、召回率和 f1 值

```
TP - True Positive | FP - False Positive
FN - False Negative | TN - True NegativePrecision = TP/(FP+TP) = 3/(3+4+2) = 3/9 = 0.33
Recall = TP/(TP+FN) = 3/(3+1+0) = 3/4 = 0.75F1-score = 2 * (Recall * Precision) / (Recall + Precision) 
         = 2 * 0.33 * 0.75 / (0.33 + 0.75)
         = 0.495 / 1.08
         = 0.458
```

## 宏观还是加权？

您可能会注意到，F1 总分有三个值`0.64`、`0.53`、`0.65`。你应该关注哪个价值？

在所有类都同等重要的不平衡数据集中，`macro average`是一个很好的选择，因为它平等地对待所有类。

但是，如果您希望将较大的权重分配给数据中样本较多的类，则首选加权平均值。

您可以使用的另一个度量标准是 [Precision-Recall](https://scikit-learn.org/stable/auto_examples/model_selection/plot_precision_recall.html) ，这是在类非常不平衡时预测成功的一个有用的度量。

# 特征重要性

让我们也画出特性的重要性，看看哪些特性更重要。

从上图中可以看出，风速特征和降水量是很好的预测因子。

我们创建的 Beaufort 比例特征似乎不太重要，因此最好将其移除。

有趣的是，A 地区的`min.atmos.pressure`最重要，而其他地区的`min.atmos.pressure`重要性最低。

# 保存模型

当你对你的模型满意时，你可以用`joblib`把它保存为一个 pickle 文件

# 根据测试数据进行预测

我们做了一个简单的模型。是时候在测试数据上预测一下了。

让我们看一下最终的提交文件。

标签仍被编码为数值；让我们把实际的标签名称带回来。

因为我们已经有了标签名称到数值的映射字典，即`‘H’ : 0`，我们可以颠倒上面的字典来将数字映射到名称

# 保存预测文件。

# 后续步骤

基础模型不足以做出好的预测；下面是改进给定方法的一些后续步骤。

1.  更多特征预处理和工程
2.  使用交叉验证来更好地衡量性能。
3.  使用[远视](https://hyperopt.github.io/hyperopt/)或 [Optuna](https://optuna.org/) 来调节 LightGBM 的参数
4.  直接调整 LightGBM 的`**class_weight**`参数以处理不平衡等级
5.  [通过利用欠采样(从多数样本中选取较小的样本以匹配较小的样本)或重采样(使用 SMOTE 等算法用虚假数据扩充数据集)来平衡数据集](/5-techniques-to-work-with-imbalanced-data-in-machine-learning-80836d45d30c#:~:text=Upsampling%20or%20Oversampling%20refers%20to,to%20create%20artificial%20data%20points.)
6.  测试其他算法，如 KNN，SVM，XGBoost，Catboost 等。
7.  [**加入 bitgrit discord 服务器**](https://discord.com/invite/H5UTQs32Bn) 与其他数据科学家讨论挑战

# 资源

## 一般

*   [应对机器学习数据集中不平衡类别的 8 种策略](https://machinelearningmastery.com/tactics-to-combat-imbalanced-classes-in-your-machine-learning-dataset/)
*   [多类分类的提示和技巧](https://medium.com/@b.terryjack/tips-and-tricks-for-multi-class-classification-c184ae1c8ffc)
*   [如何减轻处理不平衡数据的痛苦](/https-medium-com-abrown004-how-to-ease-the-pain-of-working-with-imbalanced-data-a7f7601f18ba)

## 超参数调谐

*   [使用 Optuna 调整 LGBM 超参数🏄🏻‍♂️](https://www.kaggle.com/code/hamzaghanmi/lgbm-hyperparameter-tuning-using-optuna)
*   [使用 Hyperopt 对 XGBoost、LightGBM 和 CatBoost 进行超参数优化的示例](/an-example-of-hyperparameter-optimization-on-xgboost-lightgbm-and-catboost-using-hyperopt-12bc41a271e)

## 多类度量

*   [简化多类指标，第一部分:精度和召回率](/multi-class-metrics-made-simple-part-i-precision-and-recall-9250280bddc2)
*   [简化多类别指标，第二部分:F1-得分](/multi-class-metrics-made-simple-part-ii-the-f1-score-ebe8b2c2ca1)
*   [简化的多类别指标，第三部分:Kappa 得分(又名 Cohen 的 Kappa 系数)](/multi-class-metrics-made-simple-the-kappa-score-aka-cohens-kappa-coefficient-bdea137af09c)
*   [微观，宏观&F1 得分的加权平均值，清楚地解释了](/micro-macro-weighted-averages-of-f1-score-clearly-explained-b603420b292f)

祝你在比赛中玩得开心！

# 感谢阅读！

## 喜欢这篇文章吗？这里有三篇文章你可能会喜欢:

*   NCATS 发起的 LitCoin NLP 挑战
*   [利用数据科学预测病毒性推文](/using-data-science-to-predict-viral-tweets-615b0acc2e1e)
*   [建立 XGBoost 模型预测视频流行度](https://medium.com/bitgrit-data-science-publication/building-an-xgboost-model-to-predict-video-popularity-ce4a39a356d7)

喜欢我的写作吗？通过我的推荐链接加入 Medium，你将直接支持我🤗

[](https://benedictxneo.medium.com/membership) [## 通过我的推荐链接加入 Medium-Benedict Neo

### 作为一个媒体会员，你的会员费的一部分会给你阅读的作家，你可以完全接触到每一个故事…

benedictxneo.medium.com](https://benedictxneo.medium.com/membership)