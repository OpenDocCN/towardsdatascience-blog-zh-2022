# 4 机器学习模型部署中再现性的挑战

> 原文：<https://towardsdatascience.com/4-challenges-of-reproducibility-in-the-machine-learning-model-deployment-3b4ca7b975c8>

![](img/e9937cab0ac652b468886b4481f1d3c7.png)

照片由[在](https://unsplash.com/@theblowup?utm_source=medium&utm_medium=referral) [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上放大

在机器学习模型的管道中，有几个我们考虑的环境——**研究环境、开发环境和生产环境**。在**研究环境**中，执行模型开发的不同组成部分，例如探索性数据分析(EDA)、模型构建、模型评估和结果分析。在**开发环境**中，在**生产环境**中向客户提供/展示模型之前，检查模型性能的质量，尤其是再现性。

**机器学习(ML)部署中的再现性**表明在给定相同输入数据的情况下，机器学习模型将在研究和生产环境中提供相同的结果。为了确保基于 ML 的模型部署中的再现性，我们不仅要确保模型训练时的再现性，还必须确保 ML 管道的其他组件中的再现性，包括数据收集、特征工程、特征选择和模型部署过程，参见图 1。

![](img/0c082ce926f8bfded9af0feecdcf3e98.png)

机器学习管道中的再现性(图片由作者提供)

再现性对于开发基于 ML 的管道以提供研究的正确性、可信度和基线是至关重要的。我们预期具有相同数据和过程的 ML 模型将提供相同的结果；否则，整个模型的正确性和可信度都会受到质疑。在科学研究中，我们经常报告我们的发现，并将其与基线模型进行比较，以说明我们提出的工作的优越性。如果 ML 模型不可复制，那么进行比较分析是不公平的。

在本文中，我们将讨论任何 ML 管道的主要组件面临的挑战和潜在解决方案，在这些组件中，我们必须确保再现性:

1.  **再现性—数据收集**

数据收集是再现性的主要挑战之一。数据是构建 ML 的关键组成部分，也是实现再现性的最大挑战。如果使用相同的数据来训练 ML 模型，则 ML 模型仅再现完全相同的结果。但是，由于数据库不断更新，训练数据无法再现，而且在许多情况下，数据的顺序并不像 SQL 中那样固定。

**潜在解决方案—** 我们可以将训练数据集保存在另一个存储中，将动态数据转换为静态数据，解决数据加载中的不一致问题。然而，这种方法也有局限性，比如数据伦理。在另一个地方存储数据可能违反欧盟的[一般数据保护规则(GDPR)](https://gdpr.eu/) 。另一方面，存储数据对于大规模数据集来说并不是一个可行的解决方案。因此，我们必须寻找其他解决方案，比如设计带有准确时间戳的数据源。此外，我们可以在数据的顺序上使用一些条件来加载数据。

**2。再现性—特征工程**

在大多数情况下，对数据进行预处理时会发现缺乏再现性。在以下情况下，可能会出现缺乏再现性的情况

*   替换数据集中要素的缺失值
*   根据用于替换缺失值的要素计算统计汇总
*   检测异常值

**潜在解决方案—** 我们应该应用不同的策略来保持再现性，同时进行特征工程:

*   对于训练和测试数据的缺失值插补，我们应该始终考虑训练数据的汇总统计
*   在将数据分成训练集或测试集时，将种子值设置为固定值。此外，还设置了一个固定的种子数量，而工作的随机性
*   我们应该在编码时始终实践标准，比如使用版本控制和时间戳散列版本

我写了一篇关于如何在特征工程中避免缺乏可重复性的实践文章:[避免数据预处理步骤中的数据泄漏](https://medium.com/p/48169c48c347)

**3。再现性—模型训练**

模型训练是 ML 管道中的另一个组成部分，在这里我们遇到了再现性的挑战。许多机器学习模型，包括基于神经网络(NN)和深度学习(DL)的方法，在模型训练的不同部分使用随机性。例如，神经网络模型训练中的初始化权重矩阵是随机的。

**潜在解决方案—**

*   我们可以通过设置种子值来控制模型的随机化
*   应该详细给出关于模型训练的信息，例如特征的顺序、不同的特征变换和模型超参数

**4。再现性—模型部署**

在部署模型时保持可再现性有几个挑战:

*   硬件环境——在某些情况下，ML 模型的再现性取决于开发阶段使用的硬件。因此，遵循相同的硬件设置是对再现性的挑战
*   软件环境—在研究环境中使用不同的编程语言，这些语言在生产环境中可能不可用—这对可重复性是一个挑战
*   真实环境中缺失的要素-在某些情况下，用于模型训练的所有要素可能无法用于生成实时结果

**潜在解决方案—**

*   记录所有软件相关信息，包括不同软件包的版本，并在部署时匹配软件版本
*   使用容器(例如，Docker)
*   在管道的所有环境(研究和生产环境)中使用相同的编程语言
*   使用训练数据的汇总统计来估算缺失的特征

总之，我们可以保证 ML 模型结果的再现性，然而，实践上述标准方法将有助于最小化模型部署中再现性的缺乏。

# 阅读默罕默德·马苏姆博士(以及媒体上成千上万的其他作家)的每一个故事。

你的会员费将直接支持和激励穆罕默德·马苏姆和你所阅读的成千上万的其他作家。你还可以在媒体上看到所有的故事—【https://masum-math8065.medium.com/membership】

**快乐阅读！**

参考

*   UDEMY-机器学习模型的部署
*   奥洛里萨德，B. K .，布雷顿，p .，，安朵斯，P. (2017)。基于机器学习的研究中的再现性:文本挖掘的一个例子。