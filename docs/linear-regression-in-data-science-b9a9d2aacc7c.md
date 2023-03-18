# 数据科学中的线性回归

> 原文：<https://towardsdatascience.com/linear-regression-in-data-science-b9a9d2aacc7c>

## 机器学习的数学技术

![](img/9a8b6cd8c8c58839f539667d6ffdc588.png)

艾萨克·史密斯在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄的照片

随着毕业季即将来临，我有几个家庭成员问他们多久会使用他们多年来学到的信息。尤其是他的一个表亲，并不热衷于数学。然而，他制造了自己的游戏 PC，并喜欢学习计算机硬件。曾经有人提到，计算机会做所有必要的数学运算，那么为什么要记忆公式呢？虽然我在一定程度上看到了他的观点，但数学是学习更多计算机知识的基石，而且作为一名程序员，能够验证结果不会有什么坏处。这种思路把我带回了代数 1，我记得在那里学习了图形和建模方法，如线性回归。那时我从未想过我会在大学毕业后很好地使用它。但是，我对数据科学的兴趣让我在预测分析和相关数据方面完全融入了数学。所以今天，我决定回顾一下线性回归及其在数据科学中的应用。

# 线性回归概述

如果你还记得数学课，回归在统计学中被用来描述模型。它也用于描述和估计变量之间的关系。线性回归的要点是找到并画出代表两个或多个感兴趣的变量之间关系的最佳拟合线。这条线可以帮助您找到数据之间的相关性并做出预测。

从数据中找到相似的趋势，并对未来的数据做出预测，这是数据科学用于机器学习和统计建模的内容。稍微回顾一下，让我们回到数据科学的话题。

# 机器学习方法

当我们谈论线性回归时，是时候提一下它使用的机器学习技术了。主要的两种机器学习方法是监督学习和非监督学习。

有了监督学习，就可以使用带标签的输出数据来训练模型。这有助于模型按照您想要的方式将其映射导向匹配输出标签的输入变量。回归或分类就是一个例子。

在无监督学习中，模型没有任何标记数据，因此它必须找到数据中的模式和结构，以决定如何映射它。一个例子是聚类或关联。

当我们想到线性回归时，我们想到的是监督学习技术。这有助于快速训练模型，并且易于理解。既然我们简要地讨论了学习类型，让我们回到线性回归在数据科学中的应用。

# 为什么是线性回归

当考虑回归类型时，有几种不同的方法可以采用。您可以使用简单回归或多元回归。在这两种情况下，您都可以选择使用线性或非线性回归。通常，线性回归更容易使用，也更容易解释。因为有了清晰的线性线，不仅模型更容易理解，也更容易预测。

线性回归确实试图将数据“拟合”到模型中。那个模型是线性的。这也把数据控制在一定的误差范围内，也就是不遵循线性模型的数据点。由于这种对误差的控制，你可能并不总是拥有在一定程度上完美地保持在线内的数据。如果是这种情况，这时你应该选择使用非线性回归。您的数据需要满足一些假设才能很好地使用线性回归。

线性回归假设

*   最佳拟合线性线的误差(或残差)遵循正态分布
*   数据没有明显的异常值
*   观察应该是相互独立的，也就是说没有依赖性
*   变量应该在一个连续的水平上被测量
*   检查同方差性，同方差性是一个统计概念，即最佳拟合线的方差在整个直线上应该保持相似
*   查看数据时，使用散点图可以快速查看变量之间是否存在线性关系

# 线性回归程序

简单介绍一下可以用来执行线性回归的不同程序和环境:

*   MATLAB 线性回归
*   线性回归 Python
*   r 线性回归
*   Sklearn 线性回归
*   Excel 线性回归

# 线性回归用例

为了涵盖所有基础，并且因为有时我认为这样学习更容易，我们也来看几个用例。

一个例子是保险公司的风险分析。在这种情况下，线性回归可以用来帮助预测或估计索赔的成本。这可能有助于企业就承担何种风险做出重要决策。

显而易见的例子是教育、金钱和其他途径，如经验或年龄。然而，我认为一个有趣的例子是关于体育分析的。你可以比较的数据点是赢得的比赛数，以及你的团队得分的平均数。你也可以反过来，根据对手得分的多少来决定赢了多少局。这样，一旦你发现了这种相关性，你就可以预测游戏的结果，或者一个赛季可能会赢多少。

# 结论

今天我们讨论了线性回归以及它在数据科学中的应用。首先，我们概述了什么是线性回归。接下来，我们讨论了线性回归使用的机器学习方法，以及为什么使用线性回归。之后，我们研究了如何确定线性回归是否适合建模，包括数据必须匹配的假设。简单地说，我们还检查了一些可以用来执行线性回归的程序和环境。最后，我们看了几个用例。

尽管学习线性回归是许多年前的数学概念，但机器学习将该技术带回帮助机器预测趋势和未来数据。希望数据科学中使用的线性回归更有意义，你会发现读起来很有趣。下次见，干杯！

***用我的*** [***每周简讯***](https://crafty-leader-2062.ck.page/8f8bcfb181) ***免费阅读我的所有文章，谢谢！***

***想阅读介质上的所有文章？成为中等*** [***成员***](https://miketechgame.medium.com/membership) ***今天！***

查看我最近的一些文章

[](https://miketechgame.medium.com/getting-started-with-seq-in-python-4f5fde688364) [## Python 中的 Seq 入门

### 向脚本中快速添加日志记录的简单方法。

miketechgame.medium.com](https://miketechgame.medium.com/getting-started-with-seq-in-python-4f5fde688364) [](https://medium.com/codex/javascript-cdns-and-how-to-use-them-offline-e6e6333491a3) [## Javascript CDNs 以及如何离线使用它们

### 它们是什么？它们如何帮助我们？

medium.com](https://medium.com/codex/javascript-cdns-and-how-to-use-them-offline-e6e6333491a3) [](https://medium.com/codex/something-i-learned-this-week-vue-js-in-asp-net-core-mvc-7b7540a38343) [## 这周学到的东西:ASP.NET 核心 MVC 中的 Vue.js

### 这听起来有点奇怪，但实际上真的很酷…

medium.com](https://medium.com/codex/something-i-learned-this-week-vue-js-in-asp-net-core-mvc-7b7540a38343) [](https://python.plainenglish.io/5-python-libraries-to-use-everyday-d32a9de13269) [## 你可以每天使用的 5 个 Python 库

### 网站、机器学习、自动化——Python 可以做很多事情。

python .平原英语. io](https://python.plainenglish.io/5-python-libraries-to-use-everyday-d32a9de13269) [](https://blog.devgenius.io/automate-kubernetes-with-python-2150c290afe7) [## 用 Python 自动化 Kubernetes

### 摆脱手动运行命令的简单方法…

blog.devgenius.io](https://blog.devgenius.io/automate-kubernetes-with-python-2150c290afe7) 

参考资料:

[](https://brilliant.org/wiki/linear-regression/) [## 线性回归|精彩的数学和科学维基

### 线性回归是一种用于模拟观察变量之间关系的技术。简单背后的理念…

brilliant.org](https://brilliant.org/wiki/linear-regression/) [](https://www.analyticsvidhya.com/blog/2021/05/all-you-need-to-know-about-your-first-machine-learning-model-linear-regression/) [## 线性回归|数据科学线性回归简介

### 如果您正在阅读这篇文章，我假设您已经进入了数据科学世界，并且对…

www.analyticsvidhya.com](https://www.analyticsvidhya.com/blog/2021/05/all-you-need-to-know-about-your-first-machine-learning-model-linear-regression/) [](https://www.ibm.com/topics/linear-regression) [## 关于线性回归| IBM

### 什么是线性回归？了解此分析程序如何生成预测，使用一个易于解释的…

www.ibm.com](https://www.ibm.com/topics/linear-regression)  [## 线性还是非线性回归？这是个问题。

### 你可能已经注意到，统计领域是一个奇怪的领域。需要更多证据吗？线性回归可以产生…

blog.minitab.com](https://blog.minitab.com/en/adventures-in-statistics-2/linear-or-nonlinear-regression-that-is-the-question)