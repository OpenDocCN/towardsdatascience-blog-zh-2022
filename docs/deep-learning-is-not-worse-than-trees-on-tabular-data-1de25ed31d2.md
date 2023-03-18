# 深度学习并不比表格数据上的树“差”

> 原文：<https://towardsdatascience.com/deep-learning-is-not-worse-than-trees-on-tabular-data-1de25ed31d2>

![](img/2961dfacdf6cac3fbd00d27d36fbc33d.png)

阿啦 [pixabay](https://pixabay.com/photos/notebook-typing-coffee-computer-1850613/) 。

## 超越表格数据的经典概念

深度学习已经成为人工智能的公共和私人面孔。当一个人在聚会上与朋友、街上的陌生人和工作中的同事随意谈论人工智能时，几乎总是谈论令人兴奋的生成语言、创造艺术、合成音乐等模型。大规模和复杂设计的深度学习模型为这些令人兴奋的机器能力提供了动力。

然而，许多从业者正理直气壮地反对深度学习的技术轰动效应。虽然深度学习“很酷”，但它肯定不是建模的最终目的。

尽管深度学习无疑主导了图像、文本和音频等专业的高维数据形式，但普遍的共识是，它在表格数据中的表现相对较差。

因此，那些对深度学习有些厌恶甚至怨恨的人用表格数据表明了他们的观点。(发表公认的深度学习论文，进行看似琐碎甚至科学上可疑的修改，这在过去和现在都很流行。这是对深度学习研究文化的抱怨之一，我在这个领域的许多思想更为传统的同事都表达了这一点，这是公平的。)

现在，在这个少数群体中，抨击“新晋新一代数据科学家”过于迷恋深度学习也很流行，相反，他们吹捧相对更经典的基于树的方法，认为这是表格数据的“最佳”模型。你会发现这种观点无处不在——在大胆的研究论文、面向人工智能的社交媒体、研究论坛和博客帖子中。的确，反文化往往和主流文化一样时髦，无论是和嬉皮士还是深度学习。

这并不是说没有好的研究表明基于树的方法优于深度学习——当然有。但是，这种细致入微和语境化的研究往往被错误地认为是一种普遍规律，那些厌恶深度学习的人往往会像许多推进深度学习状态的人一样，信奉同样有问题的学说:在一组通常定义良好的限制内获得结果，并故意以不考虑所述语境界限的方式外推它们。

那些提倡基于树的模型而不是深度学习模型的人最明显的短视是在问题域空间。对表格深度学习方法的一个常见批评是，它们看起来像是“技巧”，是零星工作的错综复杂的一次性方法，而不是可靠的高性能树方法。智力问题 Wolpert 和 Macready 的经典的没有免费的午餐定理让我们思考每当我们遇到普遍(或甚至接近普遍)优势的主张，无论这是在性能、一致性或另一个度量上的优势，是:(near) *在问题空间*的哪个子集上是普遍的？

广为人知的研究调查和更非正式的调查使用的数据集显示了深度学习在表格数据上的成功，这些数据集是常见的基准数据集-森林覆盖数据集，希格斯玻色子数据集，加州住房数据集，葡萄酒质量数据集，等等。这些数据集，即使以几十个为单位进行评估，无疑也是有限的。当然，我们必须承认，与这些更同质的基准数据集相比，使用表现不佳的多样化数据集进行评估性调查研究要困难得多。

然而，那些吹捧此类研究结果对神经网络在表格数据上的能力做出广泛判断的人，忽视了机器学习模型应用于表格数据领域的广度。

> 在所有数据形式中，表格数据在结构质量和领域上是最多样化的，这种说法不无道理。从这个意义上说，“表格数据”更多的是一个“大他者”，甚至是“大全部”，而不是一个特定类型或结构的数据。

让我们考虑一些超出这个狭窄基准集的表格数据问题的真实例子。

随着可从生物系统获得的数据信号的增加，生物数据集的特征丰富性从仅仅一二十年前的状态显著增加。这些表格数据集的丰富性揭示了生物现象的巨大复杂性——从局部到全球的多种尺度的复杂模式，以无数种方式相互作用。深度神经网络几乎总是被用于对表示复杂生物现象的现代表格数据集进行建模。

或者，内容推荐，一个需要仔细和高容量建模能力的复杂领域，或多或少普遍采用深度学习解决方案。例如，网飞报告称，在实施深度学习时，“通过线下和线上指标衡量，我们的建议有了很大改善”。类似地，谷歌的一篇论文展示了深度学习作为支持 YouTube 建议的范式的重组，该论文写道，“与谷歌的其他产品领域相结合，YouTube 经历了一个基本的范式转变，即使用深度学习作为几乎所有学习问题的通用解决方案。”

只要我们看一看，我们可以找到更多的例子。许多表格数据集包含文本属性，例如包含文本评论以及以表格形式表示的用户和产品信息的在线产品评论数据集。最近的房屋列表数据集包含与标准表格信息(如平方英尺、浴室数量等)相关联的图像。或者，考虑股票价格数据，该数据除了以表格形式获取公司信息之外，还获取时间序列数据。如果除了表格数据和时间序列数据之外，我们还想添加十大财经头条来预测股票价格，该怎么办？据我所知，基于树的模型不能有效地解决这些多模态问题。而深度学习则可以用来解决所有的问题。

事实是，自 2000 年代和 2010 年代初以来，数据已经发生了变化，当时许多基准数据集用于研究深度学习和基于树的模型之间的性能差异。表格数据比以往任何时候都更加精细和复杂，捕捉了广泛的难以置信的复杂现象。在表格数据的环境中，深度学习作为一种非结构化、稀疏和随机的成功方法显然是不正确的。

此外，原始监督学习不仅仅是对表格数据建模的单一问题。

*   表格数据通常是有噪声的，我们需要一些方法来消除噪声，或者开发一些对噪声具有鲁棒性的方法。
*   表格数据也经常不断变化，因此我们需要能够在结构上轻松适应新数据的模型。
*   我们还经常遇到许多不同的数据集，它们共享一个基本相似的结构，因此我们希望能够将知识从一个模型转移到另一个模型。
*   有时缺少表格数据，我们需要生成现实的新数据。
*   我们也希望能够用非常有限的数据集开发非常健壮和通用的模型。

同样，就我们所知，基于树的模型要么不能做到以上所述，要么很难做到以上所述。另一方面，神经网络在适应来自计算机视觉和自然语言处理领域的表格数据后，可以成功地完成以下所有工作。

当然，对神经网络有一些重要的合理的普遍反对意见。

其中一个反对意见是可解释性——认为深度神经网络比树模型更难解释。可解释性是一个特别有趣的想法，因为它更多的是人类观察者的属性，而不是模型本身的属性。对数百个特征进行操作的梯度推进模型真的比在同一数据集上训练的多层感知器更具内在可解释性吗？树模型确实建立了容易理解的单一特征分割条件，但是这本身并没有什么价值。此外，像梯度增强系统这样的流行树集成中的许多或大多数模型不直接对目标建模，而是对残差建模，这使得直接可解释性更加困难。我们更关心的是特性之间的交互。为了有效地理解这一点，树模型和神经网络都需要外部可解释性方法来将决策的复杂性分解为关键的方向和力量。因此，尚不清楚在复杂数据集上，树模型是否比神经网络模型更具有内在的可解释性。

第二个主要的反对意见是调整神经网络的元参数的麻烦。这是神经网络不可调和的属性。鉴于架构、培训课程、优化过程等的可能配置和方法的纯粹多样性，神经网络基本上更多地作为理想而不是真正的具体算法存在。应当注意，对于计算机视觉和自然语言处理领域，这是一个比表格数据更突出的问题，并且已经提出了减轻这种影响的方法。此外，应该注意，基于树的模型也具有大量元参数，这通常需要系统的元优化。

第三个反对意见是神经网络和树模型之间的训练时间差异(树模型比神经网络快)。任何以表格数据为代表提出这种异议的人都表明，他们对表格数据有一个非常具体的概念——即小而简单的数据集。在大型和复杂的数据集上，基于树的模型在时间和空间方面的训练成本都很高。(无论如何，在小而简单的表格数据集上，树模型往往做得更好。这是无可争议的。这里的问题是表格数据的错误限制空间。)

另一个反对意见是神经网络不能以反映特征的有效含义的方式有效地预处理数据。流行的基于树的模型能够以一种被认为对异构数据更有效的方式解释特征。然而，这并不妨碍深度学习与预处理方案的联合应用，预处理方案可以在访问表达特征方面将神经网络置于与基于树的模型平等的基础上。

所有这些都是为了挑战基于树的模型优于深度学习模型的概念，甚至是基于树的模型一贯或普遍优于深度学习模型的概念。这也不是说深度学习总体上优于基于树的模型。相反，我们的目标是全面和公平。

为了清楚起见，提出了以下主张:

*   深度学习在某个明确定义的问题领域上成功工作，就像基于树的方法在另一个明确定义的问题领域上成功工作一样。
*   深度学习可以解决基于树的方法无法解决的原始表格数据到标签监督学习之外的许多问题，例如对多模态数据(图像、文本和/或音频等)进行建模。表格数据之外的数据)、去噪数据、跨数据集传递知识、在有限的数据集上成功训练以及生成数据。
*   深度学习确实容易出现困难，比如可解释性和元优化。然而，在大多数情况下，基于树的模型在某种程度上遭受相同的问题(在深度学习首先至少会取得一定成功的足够复杂的情况下——我们必须在这里进行比较)。

希望这能引起一些思考，并标志着深度学习至少是大范围表格数据问题的一个有意义的候选。

当然，我知道这可能是一个不受欢迎的立场。我欢迎回复中的任何讨论——让我们开始吧！

以上是从*表格数据的现代深度学习*中修改的摘录，这是我与人合著的一本书，将于今年年底发行。这本书的目的是通过提供理论和工具将深度学习应用于表格数据问题，进一步证实这些说法。在超过 1000 页的好材料中，我们调查了几十篇研究论文和许多有趣的想法。这是其中的一个小例子:

*   使用元优化为大型异构数据集选择最佳经典分类编码策略
*   将表格数据转换成图像，然后应用卷积神经网络
*   理解注意力是处理表格数据中异质性的自然方式
*   构建多模态模型，根据图像、时间序列、文本和表格输入执行监督预测
*   探索使用软模拟来模拟决策树结构的架构
*   在隐私和数据集大小约束下为模型训练生成表格数据
*   使用自动编码器架构在标签稀缺的环境中执行自监督预训练

(拿起这本书后，你会了解所有这些，甚至更多！)

我们也给出了树算法和它们适用的问题类型的一个相当广泛的概述。

再说一遍，这本书的目的不是要“站在”深度学习的“一边”。取而代之的是展示现有的各种各样的技术，以及它们可以成功应用于的表格数据问题的类型。

有兴趣的话，在这里预购[！我们很感激。](https://www.barnesandnoble.com/w/modern-deep-learning-for-tabular-data-andre-ye/1141877884)

而且，如果你对最新的文章感兴趣，可以考虑[订阅](https://andre-ye.medium.com/subscribe)。如果你想支持我的写作，通过我的[推荐链接](https://andre-ye.medium.com/membership)加入 Medium 是一个很好的方式。干杯！