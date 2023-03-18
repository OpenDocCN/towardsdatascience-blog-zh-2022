# 精益机器学习:以精益创业的方式运行概念验证(第 1 部分)

> 原文：<https://towardsdatascience.com/lean-machine-learning-running-your-proof-of-concept-the-lean-startup-way-part-1-f9dbebb74d63>

## 如何转变构建机器学习产品的方式

![](img/f9edcc0675017c2a259741e7e0ad6081.png)

图 Eric Reis 的《精益创业中的构建度量学习周期》。图片作者。

在他的书 *The Lean Startup，*中，Eric Ries 描述了他使用图 1 中描述的构建度量学习周期来构建一个成功的创业公司的方法。虽然我没有自己的创业公司，但作为一名数据科学家，我已经能够在我的生活中应用 Ries 的许多想法。

在整个系列中，我将描述如何通过应用精益启动方法来制作更好的机器学习产品。在第一部分，我将介绍精益创业方式，创新甜蜜点的四个关键领域，以及如何确定您的机器学习产品是否可取。

# 精益启动方式介绍

我经常看到数据科学家花几个月的时间在竖井中以令人难以置信的高精度构建机器学习模型。他们对自己的工作非常自豪，但在展示他们的成果时，他们经常发现企业客户并不真正理解或关心他们花了几个月时间研究的模型。在开始构建机器学习模型之前，我建议数据科学家遵循构建测量学习周期，并首先确定他们想从他们的模型中学习什么。

Ries 在书中描述的最关键的一点是执行和计划之间的区别。当创造一个产品时，首先*制造*这个产品，然后*衡量*它的成功，最后在产品上市后分析你*学到的*东西，这是很有诱惑力的。然而，Ries 认为创造一个成功产品的步骤应该反过来。

![](img/598867760bddde718fe4a7e27de8c8f3.png)

图 2:如何以精益启动的方式规划你的产品。图片作者。

你应该先确定你想*学什么。*你最终会努力了解什么是顾客的理想产品，以及你试图解决的问题。一旦你知道你想学什么，你的下一步就是找出如何*衡量*正确的事情，这样你就可以抓住你想学的东西。只有在你知道要度量什么之后，你才能计划如何构建它。在我的职业生涯中，我看到团队立即开始构建，但等到产品完全构建并发布后才获取度量。他们发现，他们构建产品的方式不允许他们收集我们需要的数据来捕捉我们想要学习的东西。

因此，重要的是要确保你构建产品的方式能够实际获取构建指标所需的数据，而不是一些最后一刻匆忙拼凑的“虚荣”指标。

# 创新的最佳时机

为了将精益创业应用于机器学习，你应该从规划你的概念证明(POC)开始。你已经知道你在努力学习，但是你在努力学什么呢？要回答这个问题，您可以参考创新最佳点(ISS)，这是产品管理中的一个流行概念，如图 3 所示。

![](img/2908bdb9065ba3997adffc22a581572e.png)

图 3:创新最佳点。图片作者。

传统上，基础设施服务由三个关键领域组成:理想的、可行的和可行的。一个好的产品创意是令人满意的、可行的、有生命力的。我发现 ISS 缺少一个关键领域——伦理。一个伟大的产品，尤其是涉及机器学习的产品，也应该是道德的。在机器学习社区中，伦理常常被忽视，所以我在图 3 所示的 ISS 中添加了伦理。

但是，你如何将 ISS 应用于机器学习产品呢？让我们来看看国际空间站的每个区域。

## 创新最佳点——令人向往

从合意开始，你需要确保你的用户*想要*你的产品。例如，网飞用户是希望平台向他们推荐电视节目和电影，还是他们真的喜欢自己搜索内容？这可能不是一个很好的利用你的时间来建立你的客户不想要的东西。在你建立了某种合意感之前，你不应该写一行代码。

## 创新最佳点——可行

技术可行性通常是人们在 POC 过程中最关注的问题。我的机器学习模型能达到 90%的准确率吗？数据质量是否足以训练我的模型？在这个领域，我们想确定用机器学习来解决我们的问题在技术上是否可行。虽然许多数据科学家用准确度、精确度和召回率等指标评估技术可行性，但我将在[第二部分](/lean-machine-learning-running-your-proof-of-concept-the-lean-startup-way-part-2-cf13b6b5154a)中介绍评估其他指标的重要性，如不正确预测的风险。如果你选择了错误的指标来确定可行性，你将会把自己带入一个痛苦的境地。

## 创新最佳点——可行

对于许多数据科学家来说，确定可行性通常是留给产品经理的事情，他们会说，一个可行的产品产生的价值大于构建和维护的成本。然而，由于数据科学家做出的决策，他们在维护解决方案的成本方面扮演着重要角色。例如，通过 GPU 训练的深度学习模型可能比简单的逻辑回归模型维护起来更昂贵。如果你不小心，你可能很容易以一个不可行的产品告终。

![](img/8a3b5112f699cb25e5ff91e0d1767dae.png)

乔治·特罗瓦托在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上的照片

## 创新最佳点——道德

最后，我们触及其中最重要的一点——数据伦理是一个严肃的问题。令人欣慰的是，近年来许多人一直在关注这一领域。此外，许多机构现在都有机器学习中的数据伦理课程。虽然我将在第 3 部分尝试做这个主题体面的正义(即将推出！)，我真的无法强调在您的组织中建立数据道德政策和创建机器学习顾问委员会有多重要。

许多人认为，如果产品没有实施，POC 就失败了。然而，POC 是一个实验，实验的目标是学习。当你开始的时候，你不知道你的产品是否会起作用。如果你发现它行不通，你只是学到了一个不值得花费进一步资源去实现的产品理念。恭喜，你成功了。说真的！只要确保你做好准备去学习正确的东西。最终，如果我们没有从 ISS 的每个领域中获得一些经验——理想的、可行的、可行的和道德的——我们的 POC 就失败了。

## **深入探讨确定合意性**

在与其他数据科学家的交谈中，我经常被问到，“如果你的客户想要你的机器学习产品，你什么时候开始学习？”。我总是建议，这实际上是你与客户沟通时要做的第一件事。

确定一个机器学习产品是否令人满意不是我在学校学到的东西(查看[这篇文章](/why-i-wasnt-prepared-for-my-first-data-science-job-b727d5c8230b)了解更多)，但是这些年来，我从其他部门的同事那里学到了一些技巧。如果你有衡量受欢迎程度的策略，请在评论中给我们大家留言！

![](img/d4153fbc2203e4aa09d3aaa9a2afc2e9.png)

图 4:维生素 vs 止痛药。图片作者。

一位产品经理曾经告诉我，当你评估潜在的产品时，你应该确定产品是维生素还是止痛药。维生素有助于我们的身体正常运作，但它们往往不是正确的饮食和锻炼所必需的。相比之下，如果你经历过严重受伤或手术，你可能会发现止痛药在你的恢复过程中是必不可少的。

我见过很多顾客很痛苦，不管他们是否意识到了。许多人对可以改进的流程变得麻木，因为“这就是我们做事的方式”。如果你提出一个“生活可能是怎样的”的愿景，你会马上看到你是否找到了止痛药。

那么，展现“生活可能是什么样子”的愿景是什么样子的呢？以我的经验来看，它可以有很多种形式。最简单的形式是向你的客户做演示。在进行演示时，我将提供一份调查，从中我可以收集指标。是的。你刚刚经历了一个精益创业。我决定我想学什么——这是可取的吗？然后我决定我可以建立什么样的标准来学习这个。最后，我构建一个包含调查的演示文稿(产品),这样我就可以获取指标。

![](img/7cc959419447c2b471f09939e89d0056.png)

图 5:用一个演示来捕捉需求的例子。图片作者。

但是陈述是确定合意性的唯一方式吗？不——我们可以通过创建实体模型或线框，从用户体验(UX)等其他领域获取信息。这个模型是产品*可能成为*的一个可视化的、理想的交互式表示。UX 的设计师通常使用像 [Balsamiq](https://balsamiq.com/) 和 [Axure](https://www.axure.com/) 这样的工具，但是我见过软件开发人员使用像 Microsoft Visio、Excel、PowerPoint 和 Keynote 这样的工具。事实上，如果安装了正确的软件包，Keynote 允许您模拟真实的网站或移动设备。

这些工具都有不同的复杂程度，但关键是你可以在一个下午做一个像样的模型来弄清楚你的客户对你的产品想法的感觉。

你可能想知道，“你到底是怎么为机器学习创建一个模型的？”。有趣的是，你的模型通常甚至不需要任何机器学习！在您的模型中，您可以从构建一个非常简单快速的基于规则的模型开始。你的客户可能并不指望你在初次会面时就能完全解决问题，而建立一个快速的、基于规则的模型会给他们一种“生活本该如此”的感觉。

我甚至制作了机器学习模型，使用几个关键词的字典对文档进行分类——不需要机器学习！当客户能够将他们的文件拖到一个文件夹中，并且文档被神奇地移动到合适的文件夹中时，他们立刻就被推销了这个产品。不要介意，如果他们试图涵盖每一个边缘情况，它会失败得很惨！关键是他们很容易就能看到幻象，我也能很容易地分辨出这是止痛药还是维生素。

![](img/589a8e04ac1c1d3cc3888a6837035c0f.png)

图 6:一个简单的模型，用于测量机器学习分类器的可取性，该分类器通过将文档移动到文件夹中来自动分类文档。图片作者。

一个更复杂的模型版本可能包括为你的产品建立一个网站，并通过谷歌、脸书或其他高流量网站进行在线广告。在创建你的网站和广告后，你可以采取两种方法来决定是否受欢迎。

一种方法是获取个人的联系信息，通常以电子邮件地址的形式。这可以捕捉到一个人是否对你的产品有普遍兴趣，但它不会告诉你他们是否足够渴望该产品以*支付*购买。决定消费者是否会花他们辛苦赚来的钱购买你的产品是至关重要的。

第二种确定需求的方法是允许个人预购你的产品。当客户登陆您的网站时，您可以允许他们预购并提前全额支付产品费用，或者允许他们在预购时支付少量定金。但是，如果押金太少，一些个人可能会在产品完成之前取消。最终，拥有大量预购清单可以激发投资者的兴趣。

## **结论**

当创建一个机器学习产品时，首先确定你的产品是否令人满意是非常重要的。你应该尝试用一种能产生清晰而强烈信号的方式来衡量可取性，但你的收获会因你的客户和他们的居住地而异。例如，如果你正在建立一个公司内部的机器学习产品，你可能无法通过建立一个要求员工存款的网站来衡量合意性。

别忘了——你是从一个实验开始的。你不会马上寻找一个高保真的产品。尽可能快地捕捉你的学习。请记住，首先要确定你想学什么，然后决定如何衡量它，最后，决定你需要建立什么，以捕捉这些指标。

## 参考

1.  埃里克·里斯，《精益创业》(2011)，《http://theleanstartup.com/book T4》