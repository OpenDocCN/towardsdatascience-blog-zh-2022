# 过度使用“统计显著”这个词会让你看起来很无知

> 原文：<https://towardsdatascience.com/overusing-the-term-statistically-significant-makes-you-look-clueless-f96e1ad1a78e>

## 解读他人假设检验的初级读本

如果你想学一种新的绕口令，试试这句经典的意译:

> “统计显著和统计不显著的区别不一定是显著的。”

![](img/b5d8498621f46f90482a853854d409df.png)

照片由[你好我是尼克](https://unsplash.com/@helloimnik?utm_source=medium&utm_medium=referral)在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

作为一名[恢复中的统计学家](https://www.linkedin.com/in/kozyrkov/)，我有幸认识了许多[数据专家](http://bit.ly/quaesita_universe)，也不快地遇到了许多[装腔作势者](http://bit.ly/quaesita_charlatan)。尽管我遇到的人很难算是随机样本，但我注意到在使用术语“有统计学意义”和不知道它的意思之间有一种关联。数据专家很少在非正式谈话中使用它。这是为什么呢？

> 真正的数据专家很少在随意的谈话中使用“统计显著”这个词。

简而言之，因为从*其他人*的角度来看，术语*统计显著*并不特别显著。重要的是 ***谁*** 设置了计算…如果不是你，结果可能也不适合你。专家明白这一点，所以他们不会把统计意义强加给无辜的旁观者。

这个术语的真正含义和骗子们如何用它来欺骗你是有差距的。我在之前的一篇文章中详细解决了这个问题，我也在本页底部添加了一个快速总结。*在这篇文章中，我将通过一个例子来说明统计决策的过程，并通过给你一个关于**解释其他人的假设检验结果**的入门知识来帮助你抵御骗子。

![](img/cc86f78fe28a50d39a25c20dd01a6186.png)

罗迪·洛佩兹在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上的照片

# 无关紧要的例子

想象你有一个制作蓝丝带的朋友。你的朋友碰巧也是一位熟练的[决策者](http://bit.ly/quaesita_di)，他知道如何使用经典假设检验框架，我已经在这里[为需要复习的人](http://bit.ly/quaesita_damnedlies)解释了这个框架。我假设您知道什么是*默认操作*以及该流程如何工作。如果你不知道，我建议你在继续之前绕一个小弯:

[](/hypothesis-testing-decoded-for-movers-and-shakers-bfc2bc34da41) [## 永远不要从假设开始

### 谎言，该死的谎言，还有 STAT101

towardsdatascience.com](/hypothesis-testing-decoded-for-movers-and-shakers-bfc2bc34da41) 

现在，让我们应用这个框架，让您体验一下推理的过程。

## 默认操作

通过[默认](http://bit.ly/quaesita_damnedlies)，你的朋友将会转向更便宜的蓝色染料供应商，只要他们已经制作的蓝带没有人类可察觉的视觉差异([操作化](http://bit.ly/quaesita_opera)以包括对人类感官易错性的容忍)。

## 设置选择

之前—之前，不是之后(！！)—做一个假设测试，你的朋友必须通过调整一些设置，包括[显著性水平、功效/样本大小和假设](http://bit.ly/quaesita_statistics)，来选择做出决定的质量。我希望更多的人了解统计有多少旋钮和刻度盘。

## 假设检验

然后你的朋友收集[数据](https://bit.ly/quaesita_srstrees1)，[神奇的事情发生了](http://bit.ly/quaesita_stc013) **，他们以一个 [p 值](http://bit.ly/quaesita_pesky)结束，总结他们是应该便宜点(*默认动作*还是坚持使用昂贵的蓝色染料(*替代动作*)。

## 结论

在统计奥德赛的最后，你的朋友拒绝了[零假设](http://bit.ly/quaesita_fisher)，并坚持使用更贵的蓝色染料。这在统计学上是显著的！这是你朋友的结论…但是你应该得出什么结论呢？

# 解释——从他们的结论到你的结论

## 差别大吗？

你应该断定染料之间有*的巨大差异吗？*

*不一定。如果不知道你的朋友[是如何操作](https://bit.ly/quaesita_metricdesign) *“人类可察觉的视觉差异”*的，你就不会知道他们现在相信的差异是不是你所说的大差异。*

*在愤怒的统计学家咆哮的这一点上，我们经常会对“效果大小”产生错位的大惊小怪(我将在另一篇文章中涉及)。现在，我要说的是，这些讨论经常没有抓住要点，因为每当我们处理适当的统计决策时，效应大小应该已经被纳入假设。*

## *这是一个重要的发现吗？*

*这是一个重要的发现吗？不一定。只有那些关心蓝色染料**和**的人，你的朋友选择做什么*才是重要的(剧中人的列表，当然包括你的朋友，他采取了[统计](http://bit.ly/quaesita_statvocab)方法，因为蓝色染料问题对他们个人或专业都很重要)。**

*为什么这对其他人来说很重要？为什么真的。可能不是。*

> *统计摘要本质上可以归结为一个关于惊奇的陈述。比如"这让我很惊讶"*

*不过，有时候，特定的个人惊讶到足以改变他们对某些事情的想法，这一事实对我们其他人来说可能是重要的消息。例如，你可能会认为发表在医学杂志上的一项结果*很重要*，因为撰写该结果的科学家改变了他们对药物如何起作用的看法。当然，你不知道他们在他们的实验室里到底做了什么(即使他们在论文中为你做了总结，你仍然缺乏一些背景知识...如果你不是专家，你不会探究他们做出的[假设](http://bit.ly/quaesita_saddest)的细微差别，但是如果[选择信任他们](http://bit.ly/quaesita_scientists)，你可能会对他们*认为重要和令人惊讶的事情感兴趣。然而，发现 ***真的是*** 吗？不幸的是，如果你只有一个总结，你唯一能做的结论就是:*“我信任的人被说服了，所以我被说服了。”如果你不打算自己做研究，你所能做的就是相信你选择的专家，鹦鹉学舌他们的结论，或者在生活中随波逐流，尽力避免对任何事情形成看法。但是我跑题了——如果你想了解更多这方面的推理，你可以在这里找到:***

*[](https://kozyrkov.medium.com/why-do-we-trust-scientists-98c24e3b9f0e) [## 我们为什么信任科学家？

### 现在是时候重新思考我们对事实和虚构的假设了

kozyrkov.medium.com](https://kozyrkov.medium.com/why-do-we-trust-scientists-98c24e3b9f0e) 

让我们回到蓝丝带上，好吗？

## 有意义吗？

除了你的朋友，每个人都可能认为得到完美的蓝色缎带染料是微不足道的。那么，你朋友的发现有意义吗？

除非你知道(并接受)整套[假设](http://bit.ly/quaesita_saddest)、[风险设定](http://bit.ly/quaesita_statistics)和[决策框架](http://bit.ly/quaesita_damnedlies)，否则这里唯一的*意义*就是你知道你的朋友下周会用哪种染料。

这是否意味着来自廉价供应商的另一种染料质量较低？当然不是。

你朋友的决策设置与染色质量问题无关，所以他们的结论不涉及这个话题。即使质量是问题的一部分，检查[操作化](https://bit.ly/quaesita_metricdesign)也很重要。你对染色质量的看法可能与你朋友的不同。

不幸的是，从你朋友的问题(*)“我是否应该放弃向供应商 B 的更便宜的蓝色染料转移的计划？”*)对一位八卦博主的热捧(*“根据科学，供应商 B 制造劣质染料！！!"*)正是那种弱智的数据盲，让我们统计学家想要敲打一些东西。

> 正是这种弱智的数据盲让我们这些统计学家想要敲打一些东西。

## 你应该避免更便宜的染料吗？

如果你也从事蓝带行业，你会相信便宜的染料不好吗？不一定。

你可能不会[相信你的朋友对染料总量](http://bit.ly/quaesita_saddest)[所做的假设](http://bit.ly/quaesita_popwrong)(也许他们假设[所有瓶染料的方差](http://bit.ly/quaesita_gistlist)为零，并且只测试了一瓶，这可能是一个坏批次)和/或你可能对统计风险有不同的容忍度和/或你不会以同样的方式框定你自己对染料供应商的决定，所以他们的发现可能与你无关。

> 好问题来自于让你对概率好奇的可能性。

然而，欢迎你从[分析](http://bit.ly/quaesita_battle)的角度来消费你朋友的发现……只要你不把它们看得太重。你可以从其他人的工作中获得大量的灵感，帮助你提出更好的问题，构建你自己的决策方法。毕竟，好问题不会凭空出现。它们来自于让你对概率感到好奇的可能性。你需要对什么可能 ***可能*** 有一些接触，以便开始问那些好问题。如果你朋友的发现让你好奇，并且蓝色染料在你的生活中是一件大事，你可能会受到启发去做你自己的测试。如果不是，那么，这不就是降噪耳机的作用吗？

![](img/084294b1d6314ad3629b9c8ee2db7827.png)

Fiona Murray 在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄的照片

# 感谢阅读！YouTube 课程怎么样？

如果你在这里很开心，并且你正在寻找一个为初学者和专家设计的有趣的完整的应用人工智能课程，这里有一个我为你制作的娱乐课程:

# 寻找动手 ML/AI 教程？

以下是我最喜欢的 10 分钟演练:

*   [AutoML](https://console.cloud.google.com/?walkthrough_id=automl_quickstart)
*   [顶点艾](https://bit.ly/kozvertex)
*   [AI 笔记本](https://bit.ly/kozvertexnotebooks)
*   [ML 为表格数据](https://bit.ly/kozvertextables)
*   [文本分类](https://bit.ly/kozvertextext)
*   [图像分类](https://bit.ly/kozverteximage)
*   [视频分类](https://bit.ly/kozvertexvideo)

# *解读提醒:“有人被某事惊到了”

虽然*“统计显著”*听起来像是“*重要*”或“*有意义*”……但事实并非如此。不幸的是，这个术语经常被这样滥用。这是个陷阱。

*   统计上显著的 =某人对某事感到惊讶。
*   重大的；重要的；值得注意的；值得注意。

请不要把一段枯燥的统计术语和一个意思完全不同的词的诗意混淆起来。

> 欢迎来到统计学，答案是 p = 0.042，但是你不知道问题是什么。

更多信息请点击此处:

[](/fooled-by-statistical-significance-7fed1bc2caf9) [## 被统计意义所迷惑

### 不要让诗人欺骗你

towardsdatascience.com](/fooled-by-statistical-significance-7fed1bc2caf9)*