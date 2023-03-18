# 各种定标器及其在数据科学中的应用

> 原文：<https://towardsdatascience.com/every-scaler-and-its-application-in-data-science-1115bec62660>

## 古老的连续定标器及其在机器学习中的应用

![](img/ae2abffe08722c665fc2f5d2d29a85e6.png)

安托万·道特里在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄的照片

## 介绍

你的模型中最重要的因素永远是你的数据。提供给模型的数据将最终决定模型的性能，因此特性是创建一个真正性能良好的模型不可或缺的一部分。有几种方法可以通过调整数据的不同方面来提高模型的有效性。有两种不同类型的特征，其中这些种类的改变通常是有益的，它们是分类特征和连续特征。对于分类特征，我们使用编码器。对于连续特征，我们使用定标器。虽然在某些方面，它们服务于不同的目的，但最终作为预处理技术，它们都有助于提高验证的准确性。我过去已经讨论过编码器，所以今天我们将采取相反的轨迹。如果您想了解更多关于编码器的信息，我也有一篇文章，您可以在这里阅读:

[](/encoders-how-to-write-them-how-to-use-them-d8dd70f45e39) [## 编码器——如何编写，如何使用

### 通过这个“从头开始”的演练，探索编码器在机器学习中的多种用途！

towardsdatascience.com](/encoders-how-to-write-them-how-to-use-them-d8dd70f45e39) 

对于数据科学家来说，定标器是一个非常重要的工具。这些缩放器用于数据，以便使其更容易被机器学习算法解释。这种类型的数学可以帮助我们更果断地从数据中归纳和得出结论。可能最著名的连续定标器在统计和机器学习中都有非常突出的应用，这就是正常或标准定标器。

标准定标器通过确定我们的数据与总体平均值的标准差来标准化我们的数据。为了证明这一点，我们将观察它的公式，并解释这究竟如何提高我们量化连续特征的能力。我们还将触及其他连续定标器的基础，它们对机器学习和科学都有用，但不那么有用。

## 标准定标器

正如我之前提到的，标准定标器很可能是最著名的定标器。更方便的是，这个定标器也是正态分布。正态分布是推断统计和高斯统计的完美介绍和基本原则，因此作为科学家，我们强调这一尺度的重要性和用法是非常重要的。如果你想了解更多关于正态分布的知识，我有一篇文章可以很好地解释它，你可以在这里阅读:

[](https://chifi.dev/the-firtst-thing-to-learn-for-data-science-stats-the-normal-distribution-e28dd353e19c) [## 数据科学统计的第一件事是学习正态分布

### 简单正态分布的概述和编程。

chifi.dev](https://chifi.dev/the-firtst-thing-to-learn-for-data-science-stats-the-normal-distribution-e28dd353e19c) 

让我们简单回顾一下什么是正态分布。该分布的概率密度函数(PDF)表示为:

> x̄- / **σ**

即样本减去总体均值，除以总体标准差。检查数学，我们发现我们的样本和平均值之间的差异，然后看看有多少标准差可以符合它。这就是为什么正态分布是均值标准差的可视化。假设大部分人口位于平均值附近的中心(这就是为什么它是平均值)，这就是为什么我们看到抛物线形状通常与分布和数据相关联。我们的标准差给出了我们的数据如何分布的参数，平均值提供了该参数应用于每个样本的平均数。

这项技术已经被证明在机器学习中非常有效。事实上，像这样利用连续数据的大多数管道很可能包括这种形式的标准化。同样，如果你正在做一个项目，这可能是这类工作的最佳工具。下面是 Julia 中一个标准缩放器的简单编写:

```
function standard_scale(x::Vector{<:Number})
               σ = std(x)
               μ = mean(x)
               [i = (i-μ) / σ for i in x]::Vector{<:Number}
end 
```

## 单位长度定标器

鲜为人知的定标器是单位长度定标器。抱歉，这里有另一个链接，但我为那些想了解更多信息的人写了另一个关于单位长度缩放器和机器学习的资源:

[](/unit-length-scaling-the-ultimate-in-continuous-feature-scaling-c5db0b0dab57) [## 单位长度缩放:连续特征缩放的终极？

### 奇妙的单位长度缩放会超越其他形式的缩放并在机器学习中取代它们吗？

towardsdatascience.com](/unit-length-scaling-the-ultimate-in-continuous-feature-scaling-c5db0b0dab57) 

虽然典型的重新标度器、任意重新标度器和均值规格化器需要向标准化倒退，但单位长度标度器在机器学习世界中独树一帜。这通过将每个元素除以向量的欧几里德长度来实现。

下面是 Julia 中的一个缩放器示例:

```
function unitl_scale(data::AbstractVector)
    zeroes = [i = 0 for i in data]
    euclidlen = euclidian(zeroes, data)
    [i = i / euclidlen for i in data]
end
```

## 均值归一化

均值归一化是另一个有一些有用应用的定标器。然而，一般来说，有更好的选择，这是一个缩放器，我在我的经验中没有看到太多的使用。也就是说，在某些时候，这种标准化可能会派上用场，并且是比一般标准缩放器更合适的选择。

```
function mean_norm(array::Array{<:Number})
        avg = mean(array)
        b = minimum(array)
        a = maximum(array)
        [i = (i-avg) / (a-b) for i in array]
end
```

通过正态分布进行归一化涉及确定平均值的标准偏差数，而平均值归一化涉及通过从最大值中减去数据中的最小值来形成标度。与标准缩放器相比，此公式中所替换的只是用`a — b`替换了标准偏差。

## 改比例

重新调整是更简单的选择之一，在数据科学中并不常见。这并不是说这个定标器没有用途，而是说它在数据科学中的作用肯定非常小。如果这个定标器有一些不可测量的用途，那肯定会很有趣，但目前这肯定不是我使用的定标器。不管怎样，看到这些缩放器背后的数学是很酷的，所以我至少想写一个。下面是一个用 julia 写的重标度的例子:

```
function rescaler(x::Array{<:Any})
    min = minumum(x)
    max = maximum(x)
    [i = (i-min) / (max - min) for i in x]
end
```

这可能是最不可能应用于数据科学的定标器。话虽如此，你永远不知道；这当然仍然是一个有趣的公式。幸运的是，它们在数学上也相当简单，只需要最小和最大值来缩放数据。

## 结束语

缩放数据是统计学原理的基础构件，对于任何想要熟悉数据科学的人来说，这绝对是一件非常重要的事情。很容易陷入这样一个陷阱，即对每个应用程序简单地使用标准定标器，而从不探索其他可用的工具。这当然是明智的，因为标准定标器通常是这项工作的最佳工具。然而，我认为在这方面做一些探索是很有意义的。

掌握这些不同的定标器肯定可以在许多不同的情况下为巨大的预测准确度提供实质性的好处。此外，对不同的定标器有一个多样化的知识和坚定的理解，可以方便地理解当它们出现问题时发生了什么。我希望这篇文章有助于提供这方面的一些背景，感谢您的阅读！