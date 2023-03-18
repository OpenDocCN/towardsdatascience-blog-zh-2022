# MATLAB 还有相关性吗？

> 原文：<https://towardsdatascience.com/is-matlab-still-relevant-cf5627f171b8>

## 意见

## Jupyter 笔记本现在是数据科学事实上的通用语言。MATLAB 怎么了？

![](img/6ead7304016af83c5fd4ec0b211bc78a.png)

[D 锦鲤](https://unsplash.com/@dkoi?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)在 [Unsplash](https://unsplash.com/s/photos/3d-mesh?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) 上的照片

我最后一次使用 MATLAB 是在 90 年代末。我正在完成我的工程学位，我模拟了一个 sigma delta 模数转换器。我记得在大学里同时使用 MATLAB 和 Simulink。那只是我在大学里无数次使用 MATLAB 中的最后一次。

我把它束之高阁，直到几年前，我在 Coursera 上跟随吴恩达的机器学习课程，再次发现了它。我主要使用 Numpy，最近开始重新探索 MATLAB。

虽然行业和媒体似乎已经将 Python、Pandas、Numpy 和它的伙伴生态系统宣传为*【正确的选择】*并且已经逐渐远离 MATLAB，但我想知道这是否是因为第一个生态系统比 MATLAB 更有用和更有生产力，或者对开源生态系统有一些偏见。

# 两种语言如何处理基本的线性代数

数据科学的一些领域，尤其是当你学习这个领域时，与直接处理矩阵直接相关。

线性代数是 ML 的关键组成部分，但不仅如此，在许多情况下，由于大量的数据，建议使用矩阵方法。因此，能够容易地操作矩阵是数据科学中的一个关键需求。不是每次，不是每个人，但它是一个相关的需要*经常*。

尽管我开始有一定的飞行时间使用 Jupyter 笔记本、Pandas 和 Numpy，但我仍然发现它们的 API 和语法不直观。当我使用 Numpy 试图翻译和可视化矩阵时，尤其会发生这种情况。

Numpy 库非常强大，我怀疑你用 MATLAB 能做的事情，有什么是你用 Numpy 做不到的。Numpy 还可以在幕后用 C 和 Fortran 来丰富那些不能用 Numpy 实现的任务。但是，Numpy 仍然是一个添加到通用高级语言中的库，无论我花多少时间使用 Numpy，我仍然发现它有时不直观。

MATLAB 是一种矩阵操作语言(它自己的名字是 Mat 的缩写),它的语法更加直观，也更接近它所代表的东西:一种设计用于线性代数的语言。

对我来说，这是一个重要的观点，但这一点似乎与市场不太相关，因为我从未读到过任何人做出这一观察，但我确信我不是唯一注意到这一点的人。

# 交互式笔记本的作用

围绕数据科学的研究是一个迭代过程。工作流不同于软件开发中使用的工作流。总是有输入数据、算法或数学方法以及交互式图表和可视化。在数据科学中，任何其他要求要么大大减少，要么可以完全忽略。

一个显著的区别是软件方法也是过程化编程。尽管许多数据科学家在写笔记本时采用了面向对象的技术，但在我看来，这是他们年龄的反映(年轻人不知道什么时候一切都是过程化的),而不是实际的需要(当你有一个相当线性的执行线程时，你为什么想要对象？).

上述场景使笔记本成为完美的工具。这是一个线性的过程执行，您可以在特定的代码块上动态地进行迭代和更改。开发不复杂，整体结构简单。它有局限性，但总的来说，它们是一个简单而有用的工具。

这种交互式环境来自计算机时代的早期。事实上，MATLAB 一直是交互式的，甚至像 1968 年开发的 Macsyma 这样的程序也已经是交互式的了。Mathematica 也在 1988 年引入了 Notebook 的概念，所以如果有人认为交互开发过程是现代 Python 的事情，那就不是了。

然而，这种视觉编码块的方法在 Jupyter 笔记本中不知何故更独特或更好地实现，并且它是有用和多产的。这显然是它成功的原因之一。MATLAB 现在确实有一个类似的环境，名为 *Live Editor* ，但它直到 2016 年才拥有该功能。在此之前，它只是程序和交互式命令行。

我目前正在探索这个笔记本的 MATLAB 版本(正如我提到的，它被称为 Live Editor ),我发现它是一个非常有用的工具。

我认为笔记本的缺乏是 MATLAB 减少和 Python 生态系统采用 Jupyter 笔记本的一个原因。我现在无法想象没有他们在这个领域的任何研究或探索，我想在这个领域工作的许多人也有同感。

# 数据帧抽象

熊猫数据框是 Jupyter 笔记本的另一个“大”东西。如果可能的话，我倾向于不使用它们，因为我要处理大量的数据，而 Pandas 不像 Numpy 那样高效。

有些人将它们用作增广矩阵，但你只能用有限的数据量做到这一点。

熊猫是以表格形式处理异构数据类型的一种非常简化的方式。我特别把它们作为一个编排表来记录定量金融的分析结果，而实际的市场数据总是一个单独的 Numpy ndarrays 数据层。这使您在处理粒度数据时速度更快(在 Numpy 中)，在记录和跟踪汇总结果时也更灵活(在 panasus 中)。我觉得这种两级方法很方便，到目前为止，我还没有找到更好的安排。不过，这可能只适用于某些情况。

MATLAB 可以被认为等同于 Numpy，但缺少等同的熊猫数据框架。现在它有了表格和时间表，这可以被视为熊猫的等效版本。

虽然在 MATLAB 论坛上讨论了很多关于表格和时间表性能的警告，但我认为这对熊猫数据框架也适用。表格和时间表看起来很棒，特别是与时间戳和时区处理相关的功能，现在在 MATLAB 中比在其他任何地方都好得多——我有这种特殊的需要，所以有时我会关注它。

虽然有时熊猫可能是必须的，但是更仔细地使用普通数组也可以得到等同于熊猫数据框架的结构。使用为名称分配特定矩阵列索引的单独变量来命名列并不罕见。你可以在 MATLAB 矩阵和 Numpy 数组中实现。这样你就有了充分的表现。

这似乎很奇怪，也很原始，但在数据科学的背景下，一切都需要有良好的结构，这就构成了一个不那么困难的问题。Numpy 数组也有自定义的数据类型定义，到目前为止我还没有在 MATLAB 中看到过(也许这个特性就在那里，我也不知道)。

# ML 和 AI 生态系统的影响

ML 和 AI 现在处理了大量的注意力，所以每种环境处理得多好或多容易是非常相关的。

可以整合到 Jupyter 笔记本电脑中的最先进的库和框架数量巨大。这可能是一个具有更大灵活性和更多选项的环境，所有这些底层库和框架都是低级编码和高度优化的，甚至对于 GPU 和并行部署也是如此。不过，它与 Python 的集成有点人为，因为 Python 是一种通用编程语言，而不是矩阵语言。我怀疑，随着一个人获得更多的屏幕时间，这将成为一个小问题。

MATLAB 结合了几个工具箱来处理最大似然和人工智能。我仍在探索这些(可能是另一篇文章的素材)，但 MATLAB 已经落后了，无法及时为 Jupyter 笔记本中丰富的生态系统提供支持。

在 MATLAB 中实现简单的算法和数值方法比在 Python 中做同样的事情要容易得多，在 Python 中你通常依赖于现成的库。可能正是这种“生产就绪”的生态系统提供了更大的用户基础。通常情况下，用户会对部署神经网络感兴趣，要么是因为他们已经通过了理解其工作方式的底层机制的阶段，要么是因为他们对其内部的更肤浅的知识感到满意。

# 关于成本的明显问题

Jupyter 笔记本和整个生态系统是开源和免费的，而 MATLAB 是一个商业产品。所以在这里，你是在比较一个相当昂贵的产品(MATLAB 本身并不昂贵，但取决于需要多少许可证和工具箱，其成本可能会显著增加)和一个开源免费的生态系统。

这一点很大程度上取决于目标和场景，值得讨论。

当 MATLAB 被用作学习工具或个人工具时，它相当便宜。

在写这篇文章的时候，一个捆绑的学生版 MATLAB、Simulink 和 10 个最常用的工具箱的价格大约是 75 美元，每个额外的工具箱不到 10 美元。考虑到软件的复杂性和目标受众，这几乎是一笔象征性的费用。如果你注册了任何学位课程，拥有 MATLAB 来学习和探索几乎是免费的。大学也可能会通过他们的学术许可来提供对它的访问。

对于个人非商业使用成本较大，MATLAB 本身并不昂贵，但工具箱会使最终的账单有点贵，但你仍然会发现 300-500 美元左右的价格是可以承受的，这取决于你想要添加的工具箱的数量。如果你需要更多的工具箱，价格就会上涨。它不像学生版，但价格仍然很合理，个人使用也负担得起。

真正的东西——在行业中使用 MATLAB 可以表示相关的成本或不相关的成本，这取决于具体的需求(有多少许可证和多少工具箱)。成本显然要大得多，但与此同时，如果你在商业上使用 MATLAB，是因为你处于高附加值行业(否则你为什么要使用它)，与劳动力相比，成本可能仍然较低——你的工资、合同费率或服务费。这里 MATLAB 本身相当便宜(大约 2000 美元)，但是没有工具箱的 MATLAB 可能不再有用。

# 市场怎么说

很难找到人谈论 MATLAB，它不再是一种趋势，它不酷，而且要花钱(相对于免费开源)。所以它看起来像是死了。甚至在 MATLAB 网站上，有一篇谈论 Python 和 MATLAB 的文章，其中解释了它最好与 Python 合作(这听起来不错，最终它只是另一个要使用的工具)。但是在厂商的网站上发现这样的声明让我很惊讶。

但是，尽管人们可能认为 MATLAB 成为了一种传统工具，Mathworks 的财务报表却讲述了另一段历史。时至今日，MATLAB 是一家健康的公司，在全球范围内雇佣了约 5000 名员工，拥有庞大的客户群，在过去的几年里收入一直超过 1B 元。这种情况随时都可能改变，但是从今天开始，这是一个很好的暗示，表明人们仍然在为 MATLAB 花钱。

# 判决

我怀疑 MATLAB 是另一个商业上成熟的产品，被广泛使用但不再流行，它是有用的，有它的位置，但它没有在媒体上获得太多的关注，并专注于机构和大客户。我个人认为它至少在我的知识阶段是有用的，因为它使我更容易处理我处理的数据类型，并使底层数学与 ML 和 a I 的关系可视化。

一旦我进入更成熟的知识阶段，我可能会重视其他方面，如能够部署模型或拥有更多现成的库，这种情况可能会改变。

我确信，就像任何其他技术一样，它会有支持者和反对者，但是对我来说，*到今天*，它似乎还没有死。Mathworks financials 将讲述一段不同的历史。

对我来说，这是一个值得探索的工具，我还不知道会用到什么程度。

# 我发现对 MATLAB 有用的资源

除了已经提到的评估 MATLAB 的低成本选项(学生许可证和家庭许可证)，还有 30 天的试用期，如果我理解正确的话，当你创建一个帐户时，Mathworks 提供的信息 MATLAB 允许你每月 20 小时访问他们的在线云 MATLAB 版本。

我在 YouTube 上浏览了几个教程，也读了几本书。作为介绍/刷新材料，我强烈推荐官方的 *MATLAB Onramp Course* 。它是交互式的，在内容和互动性上都制作得非常好。浏览一遍需要 2 个小时，还有另外的关于 ML 和 AI 的*课程，我打算接下来完成。*

## *补遗*

除了已经提到的非商业许可，有兴趣在商业上使用 MATLAB 的小企业应该知道，可以以非常有竞争力的大约 1500 美元的启动许可价格获得 MATLAB。该许可证仅对满足以下要求的初创公司有效:在过去 5 年内成立，少于 15 名工程师，收入少于 100 万美元。这些限制似乎相当合理，而且价格使得 MATLAB 对初创公司几乎是免费的。

—

## 放弃

*我的观点是我自己的，不代表我的任何客户或雇主(过去或现在)的任何观点，也不与任何与我相关的特定专业活动(过去或现在)相关联。*

我与这里提到的商业产品背后的任何公司都没有任何直接或间接的关系。

*MATLAB 和 Simulink 是 MathWorks 的注册商标。*

*Mathematica 是 Wolfram 的注册商标。*

*此处提供的信息不代表任何购买建议或产品基准或详细比较。任何商业产品的成本和信息都是近似值，并不意味着准确或完整，有关功能、价格或其他规格的详细信息，读者可向不同产品的供应商咨询。*