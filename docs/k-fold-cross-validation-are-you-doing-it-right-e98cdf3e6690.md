# k 倍交叉验证:你做得对吗？

> 原文：<https://towardsdatascience.com/k-fold-cross-validation-are-you-doing-it-right-e98cdf3e6690>

## 讨论在数据集上执行 k-fold 交叉验证的适当(和不适当)方法

![](img/b35dd402ee61ca8196fcf538851bda8b.png)

Markus Spiske 拍摄的照片:[https://www . pexels . com/photo/one-black-chess-pieces-separated-from-red-pawn-chess-pieces-1679618/](https://www.pexels.com/photo/one-black-chess-piece-separated-from-red-pawn-chess-pieces-1679618/)

k-fold 交叉验证是机器学习应用中一种流行的统计方法。它减轻了过度拟合，并使模型能够更好地利用训练数据进行概括。

然而，在实践中，与典型的训练-测试分割相比，该技术可能更难执行。如果使用不当，k 重交叉验证会导致数据泄漏。

在这里，我们回顾了 Python 中 k-fold 交叉验证的不当实现可能导致数据泄漏的方式，以及用户可以做些什么来避免这种结果。

## k 倍交叉验证审查

k 倍交叉验证是一种需要将训练数据分成 k 个子集的技术。模型被训练和评估 k 次，每个子集被用作评估模型的验证集一次。

例如，如果训练数据集被分成 3 部分:

*   模型 1 将用折叠 1 和 2 训练，并用折叠 3 评估
*   模型 2 将用折叠 1 和 3 训练，并用折叠 2 评估
*   模型 3 将用折叠 2 和 3 训练，并用折叠 1 评估

为了使这种采样策略成功工作，模型应该只使用它们应该能够访问的数据进行训练。

换句话说，用作验证集的折叠不应影响用作训练集的折叠。不遵守这一原则的数据集将容易出现数据泄漏。

数据泄漏是当用训练数据之外的信息(即，验证和测试数据)训练模型时发生的现象。应该避免数据泄漏，因为它会产生误导性的评估指标，从而导致无法在生产中使用的模型。

对于那些不熟悉这个概念的人，可以看看下面的文章:

[](/an-introduction-to-data-leakage-f1c58f7c1d64) [## 数据泄漏介绍

### 对数据的粗心处理会破坏你的机器学习模型

towardsdatascience.com](/an-introduction-to-data-leakage-f1c58f7c1d64) 

不幸的是，在执行 k 重交叉验证时，很容易导致数据泄漏，下面将对此进行解释。

## K-fold 交叉验证(错误的方式)

k 倍交叉验证仅在模型仅使用它们应该能够访问的数据进行训练时有效。如果数据在采样前处理不当，则可能违反该规则。

为了证明这一点，我们可以使用一个玩具数据集。

假设我们首先将训练数据标准化，然后将其分成 3 份。很简单，对吧？

然而，仅仅这几行代码，我们就犯了一个明显的错误。

像标准化这样的转换在确定如何改变每个值时使用整个数据分布。在训练数据被分成 k 个折叠之前执行这样的技术*将意味着训练集将受到验证集的影响，从而导致数据泄露。*

更糟糕的是，代码仍然会成功运行，不会引发任何错误，因此如果用户不注意，他们将会忘记这个问题。

当执行包含交叉验证分割策略的超参数调整方法时，例如网格搜索或随机搜索，也会犯类似的错误。

再一次，这里的数据在被分成 k 倍用于超参数调整之前被标准化*，因此训练集被来自验证集的数据无意中转换。*

## 解决方案

在进行 k-fold 交叉验证时，有一种避免数据泄漏的简单解决方案，即在将训练数据拆分成 k-fold 的之后进行这样的转换*。*

用户可以通过利用 Scikit-Learn 模块的[管道](https://scikit-learn.org/stable/modules/generated/sklearn.pipeline.Pipeline.html)轻松实现这一点。

通俗地说，管道可以创建将工作流的每一步链接在一起的对象。不熟悉 Scikit-Learn 管道的人可以在此了解更多信息:

[](/why-you-should-use-scikit-learn-pipelines-8754b4d1e375) [## 为什么您应该使用 Scikit-Learn 管道

### 这个工具把你的代码带到了一个新的高度

towardsdatascience.com](/why-you-should-use-scikit-learn-pipelines-8754b4d1e375) 

我是这个工具的主要支持者，只要有机会，我就会反复使用它。用户可以将所有的转换器和估算器输入到一个管道对象中，然后对该对象执行 k-fold 交叉验证。

这将通过确保所有变换将仅在单个折叠上执行而不是在整个训练数据上执行来防止数据泄漏。让我们利用管道来修复之前交叉验证尝试中出现的错误。

当执行网格搜索时，可以实现相同的方法来避免数据泄漏。不要给`estimator`超参数分配机器学习算法，而是分配管道对象。

## 关键要点

![](img/ab48d05407767a6615cc7fc3b4b05ab0.png)

照片由 [Prateek Katyal](https://unsplash.com/@prateekkatyal?utm_source=medium&utm_medium=referral) 在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄

执行 k-fold 交叉验证的用户需要警惕数据泄漏，如果无意中使用验证数据来转换训练数据，就会发生数据泄漏。

如果用户无情地利用受数据分布影响的变换，如特征缩放和维度缩减，则可能会出现数据泄漏。

这个问题可以通过在交叉验证分割之后而不是之前应用转换*来防止。实现这一点最简单的方法是使用 Scikit-Learn 包的管道。*

我祝你在数据科学的努力中好运！