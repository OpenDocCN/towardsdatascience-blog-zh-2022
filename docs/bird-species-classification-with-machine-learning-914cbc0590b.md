# 基于机器学习的鸟类分类

> 原文：<https://towardsdatascience.com/bird-species-classification-with-machine-learning-914cbc0590b>

## 数据科学

## 根据基因和位置预测鸟的种类

![](img/99b33172e238413a7a5b732150755f5b.png)

照片由[香农·波特](https://unsplash.com/@cifilter?utm_source=medium&utm_medium=referral)在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄

像鸟一样？比如数据科学？

你会喜欢这个挑战的！

## 问题陈述

> 科学家们已经确定，一种已知的鸟类应该分为 3 个不同的独立物种。这些物种是该国特定地区特有的，必须尽可能精确地跟踪和估计它们的数量。
> 
> 因此，一个非盈利的保护协会承担了这项任务。他们需要能够根据野外工作人员在野外观察到的特征，记录他们遇到了哪些物种。
> 
> 使用某些遗传特征和位置数据，你能预测已经观察到的鸟的种类吗？
> 
> 这是一个初级水平的练习比赛，你的目标是根据属性或位置预测鸟类的种类。"
> 
> [来源](https://bitgrit.net/competition/16)

你现在有了一个明确的目标。

## 目标🥅

根据属性或位置预测鸟的种类(A、B 或 C)

现在让我们来看看数据

## 数据[💾](https://emojipedia.org/floppy-disk/)

通过[注册](https://bitgrit.net/register)获得本次[数据科学竞赛](https://bitgrit.net/competition/16)的数据。

```
📂 **train**
├── training_target.csv
├── training_set.csv
└── solution_format.csv📂 **test**
└── test_set.csv
```

数据被方便地分成训练和测试数据集。

在每一次训练和测试中，你会得到位置 1 到 3 的鸟的数据。

下面来看看`training_set.csv`的前五行

`training_set`和`training_target`可以与`‘id’`柱连接。

下面是给定列的数据字典

```
**species**     : animal species (A, B, C)
**bill_length** : bill length (mm)
**bill_depth**  : bill depth (mm)
**wing_length** : wing length (mm)
**mass**        : body mass (g)
**location**    : island type (Location 1, 2, 3)
**sex**         : animal sex (0: Male; 1: Female; NA: Unknown)
```

然后，看着`solution_format.csv`

现在你对目标有了一个想法，对给你的数据有了一些了解，是时候动手了。

**本文代码→** [**深注**](https://deepnote.com/workspace/benthecoder-1aa3f71b-c5ea-44d1-ba14-b7fe4c5507d7/project/article-notebooks-a605a3e6-1564-47b2-94e7-842290ba7692/%2Fbird-classification.ipynb)

## 加载库

接下来，我们加载一些用于可视化和机器学习的基本库。

## 缺少数据帮助函数

## 加载数据

首先，我们使用`read_csv`函数加载训练和测试数据。

我们还将`training_set.csv`(包含特征)与` training_target.csv `(包含目标变量)合并，形成训练数据。

在这里，我手动保存了列名，包括数字和分类，还保存了目标列。

这使我可以很容易地引用我以后想要的列

# 探索性数据分析

有趣的部分到了，可视化数据。

从`info`函数中，似乎有丢失的值，我们可以看到位置和性别应该是分类的，所以我们稍后必须进行一些数据类型转换。

## 数字列

绘制数值变量的直方图，我们看到

*   bill_depth 在 15 和 19 左右达到峰值
*   比尔的长度在 39 岁和 47 岁左右达到顶峰
*   翼长峰值在 190°和 216°左右
*   质量是右偏的

## 分类列

让我们首先想象一下我们的目标类。

我们看地点和物种似乎是为了它们各自的地点和物种(loc2 &物种 C，loc3 &物种 A)。

我们也看到雌性鸟比雄性鸟稍微多一点。

根据物种图，我们手里似乎有一个不平衡的职业，因为物种`B`比物种`A`和`C`少得多

*为什么这是一个问题？*

模型会偏向于样本量较大的类。

发生这种情况是因为分类器具有关于具有更多样本的类的更多信息，因此它学习如何更好地预测那些类，而它在较小的类中保持较弱。

在我们的例子中，物种`A`和`C`将比其他职业更容易被预测到。

这里有一篇关于如何处理这个问题的很棒的文章。

# 缺少值

使用助手功能，似乎有大量的`bill_length`和`wing_length`数据丢失

我们还可以使用热图来可视化该列中缺失的数据。

## 估算分类值

先看看我们的分类变量里有多少缺失变量。

让我们使用简单的估算器来处理它们，用最频繁的值替换它们。

如您所见，通过`most_frequent`策略，缺失值被估算为 1.0，这是最常见的。

## 估算数字列

# 特征预处理和工程

我们必须将分类特征转换成数字格式，包括目标变量。

让我们使用 [scikit-learn 的标签编码器](https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.LabelEncoder.html)来完成这项工作。

这里有一个使用`LabelEncoder()`标签列的例子

通过首先拟合它，我们可以看到映射看起来像什么。

使用`fit_transform`直接为我们转换

对于其他包含字符串变量(非数字)的列，我们也进行同样的编码

我们还将分类特征转换成`pd.Categorical`数据类型

这是变量的当前数据类型。

现在，我们通过将一些变量除以另一个变量来形成比率，从而创建一些额外的特征。

我们不知道它们是否有助于提高模型的预测能力，但试试也无妨。

这是目前火车场景的样子

# 构建模型

## 列车测试分离

现在该建立模型了，我们先把它拆分成 X(特征)和 y(目标变量)，再拆分成训练集和评估集。

训练是我们训练模型的地方，评估是我们在使模型适合测试集之前测试模型的地方。

我们使用`[train_test_split](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.train_test_split.html)`将我们的数据分成训练集和评估集。

## 决策树分类器

对于本文，我们选择一个简单的基线模式，即[决策树分类器](https://scikit-learn.org/stable/modules/generated/sklearn.tree.DecisionTreeClassifier.html)

一旦我们适应了训练集，我们就可以根据评估数据进行预测。

# 模型性能

让我们看看简单的决策树分类器是如何工作的。

对于不平衡的数据集，99%的准确率可能毫无意义，因此我们需要更合适的指标，如精度、召回率和混淆矩阵。

## 混淆矩阵

让我们为我们的模型预测创建一个混淆矩阵。

首先，我们需要获得标签编码器给出的类名和标签，这样我们的图就可以显示标签名。

然后我们绘制一个非标准化和标准化的混淆矩阵。

混淆矩阵告诉我们，它预测了更多的 A 类和 C 类，这并不奇怪，因为我们有更多的样本。

它还表明，该模型预测了更多的 A 类，而它应该是 B/C 类。

## 分类报告

[分类报告](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.classification_report.html)测量来自分类算法的预测质量。

它告诉我们有多少预测是对的/错的

更具体地说，它使用真阳性、假阳性、真阴性和假阴性来计算精确度、召回率和 f1 值

有关这些指标的详细计算，请查看[简化的多级指标，第二部分:由](/multi-class-metrics-made-simple-part-ii-the-f1-score-ebe8b2c2ca1) [Boaz Shmueli](https://medium.com/u/57ee515c83c5?source=post_page-----914cbc0590b--------------------------------) 撰写的 F1 分数

直观上，[精度](https://en.wikipedia.org/wiki/Precision_and_recall#Precision)是分类器不将一个阴性(错误)样本标记为阳性(正确)的能力，[召回](https://en.wikipedia.org/wiki/Precision_and_recall#Recall)是分类器找到所有阳性(正确)样本的能力。

从[文档](https://scikit-learn.org/stable/modules/model_evaluation.html#classification-report)中，

*   `"macro"`简单地计算二进制指标的平均值，对每个类别赋予相等的权重。在非频繁类仍然重要的问题中，宏平均可能是突出其性能的一种方法。另一方面，所有类都同等重要的假设通常是不正确的，因此宏平均会过度强调不经常出现的类的典型低性能。
*   `"weighted"`通过计算二进制指标的平均值来说明类别不平衡，在二进制指标中，每个类别的分数根据其在真实数据样本中的存在情况进行加权。

没有单一的最佳指标，这取决于您的应用。应用程序以及与不同类型的错误相关的实际成本将决定使用哪种度量标准。

# 特征重要性

让我们也画出特性的重要性，看看哪些特性更重要。

从特征重要性来看，`mass`似乎最擅长预测物种，其次是`bill_length`。

其他变量在分类器中似乎不重要。

我们看到特征重要性是如何在我们的决策树分类器的可视化中使用的。

在根节点中，如果质量低于大约 4600，那么它检查`bill_length`，否则它检查`bill_depth`，然后在叶子处它预测类。

# 根据测试数据进行预测

首先，我们执行相同的预处理+特征生成

然后，我们可以使用我们的模型进行预测，并连接 ID 列以形成解决方案文件。

请注意，物种值是数值，我们必须将其转换回字符串值。有了 fit 早期的标签编码器，我们可以做到这一点。

# 保存预测文件。

# 后续步骤

基础模型不足以做出好的预测；下面是改进给定方法的一些后续步骤。

1.  更多特征预处理和工程
2.  使用交叉验证来更好地衡量性能。
3.  测试其他算法，如 KNN，SVM，XGBoost，Catboost 等。
4.  [**加入 bitgrit discord 服务器**](https://discord.com/invite/H5UTQs32Bn) 与其他数据科学家讨论挑战

## 超棒的 Kaggle 笔记本

这里有 3 个笔记本作为参考，告诉你如何在这次挑战中提升自己的水平

1.  [表格数据的数据科学:高级技术](https://www.kaggle.com/code/vbmokin/data-science-for-tabular-data-advanced-techniques)
2.  [信用欺诈—处理不平衡的数据集](https://www.kaggle.com/code/janiobachmann/credit-fraud-dealing-with-imbalanced-datasets)
3.  [房价:Lasso，XGBoost，以及详细的 EDA](https://www.kaggle.com/code/erikbruin/house-prices-lasso-xgboost-and-a-detailed-eda)

# 感谢阅读！

## 喜欢这篇文章吗？这里有三篇文章你可能会喜欢:

*   [用机器学习预测降雨](/predicting-rain-with-machine-learning-2acf80017c44)
*   [利用数据科学预测病毒性推文](/using-data-science-to-predict-viral-tweets-615b0acc2e1e)
*   40 个有用的熊猫片段。在数据分析工作中派上用场的熊猫片段

## 数据 L *许可*

> *数据由*[*CC-0*](https://creativecommons.org/share-your-work/public-domain/cc0/)*授权按照* [*帕尔默站【LTER】数据策略*](http://pal.lternet.edu/data/policies) *和* [*LTER 数据访问策略获取 I 类数据*](https://lternet.edu/data-access-policy/) *。*

喜欢我的写作吗？**用我的 [**推荐链接**](https://benedictxneo.medium.com/membership) 加入 Medium** ，你将直接支持我🤗

[](https://benedictxneo.medium.com/membership) [## 立即获取无限的故事

### 作为一个媒体会员，你的会员费的一部分会给你阅读的作家，你可以完全接触到每一个故事…

benedictxneo.medium.com](https://benedictxneo.medium.com/membership)