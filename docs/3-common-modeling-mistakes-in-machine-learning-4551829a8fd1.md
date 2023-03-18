# 机器学习中的 3 个常见建模错误

> 原文：<https://towardsdatascience.com/3-common-modeling-mistakes-in-machine-learning-4551829a8fd1>

## 探索可能妨碍模型性能的简单缺陷

![](img/244a365419cf0a47dc53061d53c6b922.png)

在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上由 [Austin Distel](https://unsplash.com/@austindistel?utm_source=medium&utm_medium=referral) 拍摄的照片

建模可以说是机器学习任务中最有趣的部分。

在这里，您可以使用经过精心处理和转换的数据来构建一个可以生成预测的模型。

尽管与数据预处理和特征工程相比，模型构建所需的时间更少，但很容易做出看似无害的决定，从而导致模型性能不佳。

在这里，我们探讨一些常见的错误，这些错误不利于用户训练和调整一个可靠的模型。

## 典型的例子

与数据预处理和特征工程相比，建模阶段相对容易执行。

例如，让我们使用 Scikit 学习包中的一个玩具数据集。

假设我们正在寻找创建一个梯度推进分类器，可以用这些数据生成预测。用于定型和调整模型的代码可能如下所示:

仅通过这个片段，我们就可以:

*   具有不同超参数值的测试模型
*   实施交叉验证分割策略以避免过度拟合
*   使用性能最佳的模型生成预测

用这么少的代码做了这么多的工作。这就是 Scikit 学习包的强大之处。

从表面上看，这种方法似乎完美无缺，但是存在一些缺陷，可能会影响模型的性能。让我们来看看机器学习任务中常见的几个错误。

## 错误 1:没有使用基线模型

在建模阶段，许多人急于直接使用会带来更多复杂性的算法。毕竟，复杂性通常与有效性联系在一起。

可惜，多不一定好。复杂模型产生与简单算法相同的性能(如果不是更差的话)是很常见的。

有可能感兴趣的算法的基本假设不适合数据。也许用来训练模型的数据集一开始就没有太多的预测能力。

为了说明这种情况，能够将调优模型的结果放在上下文中是很重要的。用户可以通过建立基线模型来恰当地评估他们复杂模型的性能。

基线模型是一个简单的模型，作为一个复杂的模型建立方法是否真正获益的指示器。

总的来说，在准备好数据后立即构建复杂的模型可能很诱人，但是您构建的第一个模型应该始终是基线模型。

> 要快速了解基线模型，请查看以下文章:

[](/baseline-models-your-guide-for-model-building-1ec3aa244b8d) [## 基线模型:您的模型构建指南

### 机器学习项目中的一个必要组成部分

towardsdatascience.com](/baseline-models-your-guide-for-model-building-1ec3aa244b8d) 

## 错误 2:使用小范围的超参数

超参数调优的一个常见缺陷是只探索小范围的超参数值。

超参数调整应使用户能够确定产生最佳结果的超参数值。然而，只有当被测试的值的范围足够大时，这个过程才能达到它的目的。

如果值甚至不在搜索空间中，调优过程如何识别最佳超参数值？

在前面的例子中，`learning_rate`超参数的搜索空间仅包括 0.1 和 10 之间的 3 个值。如果最佳值超出此范围，则在调整过程中不会被检测到。

对于许多机器学习算法，模型性能严重依赖于某些超参数。因此，用小范围的值来调优模型是不可取的。

用户可以选择使用更小范围的超参数值，因为更大数量的值将需要更多的计算，并将导致更长的运行时间。

对于这种情况，最好不要使用较小范围的值，而是切换到需要较少时间和计算量的超参数调优方法。

网格搜索是一种有效的超参数调整方法，但也有其他合适的替代方法。

> 如果您有兴趣探索超参数调整的其他替代方法，请查看以下文章:

[](/grid-search-vs-random-search-vs-bayesian-optimization-2e68f57c3c46) [## 网格搜索 VS 随机搜索 VS 贝叶斯优化

### 哪种超参数调优方法最好？

towardsdatascience.com](/grid-search-vs-random-search-vs-bayesian-optimization-2e68f57c3c46) 

## 错误 3:使用错误的评估标准

看到一个评分很高的模特总是很开心。不幸的是，基于错误的评估度量训练的模型是无用的。

用户在使用默认值`scoring`参数的同时执行网格搜索并不罕见。网格搜索中默认的评分标准是准确性，这在很多情况下并不理想。

例如，对于不平衡的数据集，精度度量是一个很差的评估度量。精确度、召回率或 f1 值可能更合适。

也就是说，即使像 f-1 分数这样的稳健指标也可能不理想。f-1 分数同等地权衡精确度和召回率。然而，在许多应用中，假阴性可能比假阳性更有害，反之亦然。

在这种情况下，用户可以根据业务案例定制自己的评估指标。这样，用户将能够调整他们的模型，以实现所需类型的性能。

## 纠正以前的错误

这里有一个用代码解决这些错误的简单例子。

首先，我们可以创建一个基线模型，它将被用来衡量训练模型的性能。具有默认参数的简单 K-最近邻模型就足够了。

现在我们可以继续使用 GridSearchCV 对象来训练和调整梯度增强分类器。这一次，我们将考虑更大范围的`learning_rate`超参数值。

此外，不使用准确性作为评估度量，让我们假设我们想要考虑精确度和召回率，同时对召回率给予更大的权重(即，更多地惩罚假阴性)。

一个解决方案是在 Scikit Learn 中用`make_scorer`包装器创建一个自定义指标，这使我们能够在网格搜索中使用 f-beta 分数(beta=2)作为评估指标。

利用改进的超参数搜索空间和评估度量，我们现在可以执行网格搜索并调整梯度推进分类器。

## 结论

![](img/4ec3807dbcebd1da13aa3556b10052f6.png)

在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上 [Prateek Katyal](https://unsplash.com/@prateekkatyal?utm_source=medium&utm_medium=referral) 拍摄的照片

机器学习任务的建模阶段比预处理和特征工程阶段耗时少得多，但在此阶段仍然容易出错，这可能会妨碍整体模型性能。

谢天谢地，Python 强大的机器学习框架完成了大部分繁重的工作。只要您将优化模型的结果与基线联系起来，考虑各种超参数值，并使用适合应用的评估指标，您的模型就更有可能产生令人满意的结果。

我祝你在数据科学的努力中好运！