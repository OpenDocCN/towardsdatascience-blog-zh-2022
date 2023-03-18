# 机器学习概述

> 原文：<https://towardsdatascience.com/a-brief-overview-of-machine-learning-20abc68cbd4e>

## 了解机器学习和人工智能的基础知识，以及它们的潜在挑战和警告。

当我们在互联网上随机搜索术语时，我们经常会遇到**【机器学习】**和**【深度学习】**，以及它们如何彻底改变我们的生活方式。目前，从自动驾驶汽车，垃圾邮件检测，我们在**网飞**和**亚马逊**看到的推荐系统，银行使用的信用卡欺诈检测等等，机器学习几乎无处不在。随着潜在的新应用的出现，这个列表还会继续下去。因此，跟上最新的趋势，理解机器学习实际上是什么，并对一些类型的机器学习有更广泛的理解是非常重要的。在这篇文章中，我将解释机器学习和不同类别的机器学习。此外，我们还将讨论机器学习的一些基本限制。

![](img/500fe4e3fd5f96101f555cee4dbc8e4c.png)

照片由 [Shubham Dhage](https://unsplash.com/es/@theshubhamdhage?utm_source=medium&utm_medium=referral) 在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄

## **什么是机器学习？**

机器学习是教会计算机从**数据**中学习并做出决策的过程，无需在训练后明确编程。一般来说，我们必须首先训练机器学习模型，然后才能让它们自己做出决定。所以机器学习算法需要的最重要的东西之一就是数据。没有数据，就没有机器学习算法的本质。根据我们提供给机器学习模型的数据，它们会在对新数据做出预测之前获取数据并理解它。因此，我们必须提供反映真实世界的数据。这是因为机器学习模型将完全依赖于我们提供给模型的数据来进行未来预测。

机器学习中通常发生的是一堆数学，其中有**乘积**、**特征缩放**和**归一化**等等。因此，我们提供给机器学习算法的数据应该是向量或数字的形式，而不是文本或机器无法理解的其他形式。机器不能理解数据的一些例子是**文本**和**字母**。因此，我们必须将所有文本和字母转换为数字形式，并将其输入到机器学习模型中进行训练和预测。

## **机器学习方法**

最典型的机器学习方法是首先将我们的数据分成两组:**训练**和**测试集**。我们必须首先将整个数据转换成数学向量的形式，并拆分数据。拆分数据后，训练集被输入到机器学习模型中。在足够数量的迭代或时期(一个时期发送一次整个训练数据)之后，我们将使用机器学习算法从测试集中进行预测。然后，我们将看到机器学习模型在测试集上的表现如何(机器学习模型在测试集上表现良好真的很重要)。

## **过拟合**

![](img/97cf65839df8ebc60cbd02dcb781b028.png)

照片由 [Diana Polekhina](https://unsplash.com/@diana_pole?utm_source=medium&utm_medium=referral) 在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 拍摄

机器学习模型有可能在训练集上表现得非常好，而在测试集上表现得不那么好。这是过度拟合的一个例子。在这种情况下，机器学习模型从训练数据中学到了太多东西，而无法**概括**。因此，它们在训练数据上拟合得非常好，并且它们能够在这个集合上给出很好的预测。然而，当我们试图从测试集获得预测时，机器学习模型会失败，因为它们已经在训练集上学习并拟合了它们的参数，而不是能够在测试数据(新数据)上进行归纳。因此，我们不仅要注意训练集的准确性，还要注意测试集的准确性。

## **下拟合**

![](img/e344715962bcb0073027a942451fbae1.png)

由[凯利·西克玛](https://unsplash.com/@kellysikkema?utm_source=medium&utm_medium=referral)在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄的照片

有时，机器学习模型与训练数据本身并不十分吻合。因此，当我们在分类任务的情况下考虑一些指标如**准确度**、**召回**和**精确度**时，它们在训练数据上的表现非常差。在回归任务的情况下，他们可能在诸如**均方根误差(RMSE)** 、**均方误差(MSE)** 和**平均绝对误差(MAE)** 等指标上表现不佳。这也会导致测试集的性能下降。机器学习模型在训练数据上表现不佳可能是由于数据不足、不相关的特征、不太复杂的模型等等。因此，我们必须确保我们最大限度地训练机器学习模型，并确保它们不仅在训练数据上表现良好，而且在测试数据上也表现良好。

## **为什么机器学习在最近几年获得了很大的吸引力？**

![](img/98d1a123d62ebfd2c3bb2f14ba761398.png)

沃洛季米尔·赫里先科在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄的照片

机器学习算法和神经网络一起被提出。然而，在那些日子里，没有足够的数据来利用这些算法。除此之外，运行这些算法所需的计算能力非常有限。然而今天，公司中产生了大量的数据，可用的计算资源也非常惊人。看看谷歌(Google cloud)和亚马逊(Amazon Web Services)提供的一些服务，会让我们对我们目前拥有的计算能力有一个很好的了解。我们可以使用所有这些技术，而无需为它们的运行设置基础设施(硬件),因为这是由上述公司提供的。因此，对机器学习和深度学习有着巨大的需求。许多公司都在机器学习研究上投入了巨额资金，以提高他们的生产力，增加使用机器学习的产品的收入。

在我们拥有大量数据的世界中，为了获得不同用例的预测，理解机器学习和深度学习非常重要。查看我们拥有的数据以及公司如何利用这些数据，我们会明白，我们学习机器学习模型越多，我们就越能为公司创造价值，并确保他们获得利润。

![](img/2ea50fcb2a2f46e8be751657206f4211.png)

列宁·艾斯特拉达在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上的照片

## **机器学习的类型**

1.  **监督学习:**在这种类型的机器学习中，我们知道输出标签，我们会训练机器学习模型，并根据它们生成的输出对它们进行评估，并将其与实际输出进行比较。这将确保我们基于已知的输出值来训练机器学习模型，因此，我们可以评估机器学习模型的性能。例如，如果我们希望根据包含房价输入特征和输出的先前数据来预测房价，我们将能够训练机器学习模型，并使用实际输出房价来评估其输出。这将确保我们训练机器学习模型直到完美，这被称为监督学习。
2.  **无监督学习:**在这种机器学习方法中，我们不知道输出，我们将训练机器学习模型，它们将能够识别模式并理解数据。无监督学习的一个流行例子是客户细分，我们会根据客户在特定场景中的行为对他们进行分组。
3.  **半监督学习:**在这种方法中，对于一些数据点，我们将有一些输出数据，而对于其他剩余数据，没有输出。我们将在有输出的训练数据上训练机器学习模型，然后要求模型对没有输出的数据进行分类并自行获取模式。使用半监督学习的一个例子是文本文档分类。我们将首先使用已知的输出进行训练，并要求手头的机器学习模型对输出未知的剩余数据进行分割和分类。

## **机器学习有哪些局限性？**

1.  一个限制是维数灾难。这意味着，当我们为机器学习模型提供更多功能时，我们会让模型花更多时间来训练和实现。这通常会导致性能低下。因此，培训有所延迟，这将导致生产机器学习模型的开发时间更长。
2.  过度拟合可能是机器学习中的一个问题。在这个过程中，机器学习模型能够很好地预测训练数据的输出，但当涉及到测试数据时，它们通常无法对我们将用作测试集的新数据进行归纳。这就是所谓的过度拟合。

## **结论**

我们已经介绍了机器学习和机器学习的类型。我们已经看到了机器学习在现实生活中实施时的一些局限性。我们也看到了在一个大的类别下不同类型的机器学习。希望这篇文章给机器学习一个好的直觉。谢谢你。