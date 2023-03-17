# 作为数据科学家，如何处理令人沮丧的利益相关者情况

> 原文：<https://towardsdatascience.com/how-to-deal-with-frustrating-stakeholder-situations-as-a-data-scientist-92d48e2c32f7>

![](img/1ab7d082838af06f1ec47f14b16d693f.png)

布鲁斯·马斯在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上的照片

# 作为数据科学家，如何处理令人沮丧的利益相关者情况

## 并将它们转化为机遇

如果你熟悉我的文章，你就会知道我是[利益相关者管理技能](/top-qualities-hiring-managers-look-for-in-data-scientist-candidates-2e2cd52444c2)的大力倡导者。我坚信，一名优秀的数据科学家不仅应该是利益相关者数据愿景的有效实施者，还应该是帮助利益相关者为其业务问题找到分析解决方案的思想伙伴。但是就像积累任何技能的过程一样，与利益相关者合作不会总是一帆风顺的。

我肯定遇到过令人沮丧的利益相关者的情况；他们中的一些人真的曾经毁了我的一天。不幸的是，根据我与其他数据科学家的交谈，这些情况相当普遍。所以我希望这篇文章能为利益相关者和数据科学家提供一些建议。如果你是一个数据团队的利益相关者，希望这能给你一些启示，告诉你如何更有效地与你的数据伙伴合作，成为一个更好的利益相关者。如果你是一名数据科学家，希望你能得到一些启发，如何不让下面的陈述毁了你的一天，而是利用它们作为发现利益相关者真正需求的机会。

1.  **“这个(结果)和我想的不一样……”**

这是我从利益相关者那里得到的一个非常普遍的回答。老实说，在我将在本文中提到的所有方法中，它并不是最差的，但它仍然令人沮丧，因为它太抽象了，无法提供任何价值。

然而，涉众的领域知识通常对数据工作非常有价值，因为通常那些嗅探测试是防止任何数据错误或其他错误的第一道防线。因此，当这种说法被提出时，它实际上是数据科学家深入挖掘的一个完美的合作机会。

***作为数据科学家如何化挫折为机遇***

与利益相关者坐下来，问一些问题。找出分析的数据/结果是如何让他们吃惊的。然后在他们的帮助下，挖掘数据，找出差异的根本原因。当然，仅仅因为数据不符合某人的期望，并不意味着它是错的。但是，有时这种根本原因将提供对数据或业务流程的新见解，并可能帮助您发现一个数据问题，如果没有领域专业知识，您可能不会注意到这个问题。

2.**“我们昨天就需要这个(数据，分析，XX)**

老实说，无论是谁发明了这个短语，都应该被打上年度最差合作者的烙印，被流放到社会西伯利亚。因为对于这种消极进取的唯一[解决方案驱动的](/5-lessons-mckinsey-taught-me-that-will-make-you-a-better-data-scientist-66cd9cc16aba)反应将是“哦，那让我拿一个时间机器…”。可以理解的是，许多数据需求是迫切的(或者至少目前看起来是如此)。但大多数分析项目不能像高级幻灯片一样在几个小时内完成，因此关于时间表和需求的有效沟通对数据科学家区分工作优先级非常有帮助。

***作为数据科学家如何化挫折为机遇***

试着找出为什么项目是紧急的，最合理的时间表是什么。要非常清楚为什么不可能立即开发出某样东西并管理期望。

此外，如果某件事非常关键，这很可能不是第一次有人想到要做这件事。因此，很可能已经做了一些工作来帮助回答这个问题的一部分，并将为每个人赢得一点时间来开发更完整的解决方案。作为一名数据科学家，不重新发明轮子可以节省你大量的时间。

最后，为了避免这种情况一次又一次的发生，试着去了解沟通的障碍发生在哪里。如果昨天有人需要这种分析，而今天是数据团队第一次听说，那么很可能有人没有尽早通知你。

3.**“为什么我们找不到临时解决方案”**

我们可以，但代价是什么？开发强大的数据表/数据源所需的时间与企业回答问题所需的速度之间存在永久性的差异。因此，企业经常要求临时的解决方案。不要误会我的意思，我完全支持必要时的黑客解决方案，只要每个人都知道警告，并仍然致力于开发一个长期的解决方案，最终取代权宜之计。

***作为数据科学家如何化挫折为机遇***

在我看来，最好的数据科学家可以帮助利益相关者提出相对稳健的临时解决方案，同时帮助设计长期可持续的解决方案。一个例子是数据库中没有记录用于分析或指标监控的数据。权宜之计可能是，如果条目数量合理，请人在 Excel 表中手动记录数据。在这种情况下，数据科学家通常是设计数据输入表的领域专家，以保证数据完整性(例如，构建下拉列表，而不是使用自由文本输入等。).

然而，重要的是不要止步于此；临时解决方案通常无法扩展，并且经常需要大量时间来维护。获得所需的一致性以开发可扩展的长期解决方案是至关重要的(例如，在上面的示例中，让工程承诺在日期 X 之前开始自动记录所需的数据)；否则，你将永远被低效、卑微的任务所困。

4.“我们能得到实时数据吗？”

在很多情况下，实时数据被高估了。数据延迟只有在延迟决策时才会成为问题。因此，在这种情况下，我问的第一个问题是“根据实时数据将做出什么决定？”确保答案不是“实时看到它会很酷”。事实证明，许多经理对看到几乎没有延迟的数据感兴趣，但往往不清楚他们实际上会用这些数据做什么。

***作为数据科学家如何化挫折为机遇***

在某些情况下，实时数据是绝对必要的。一个很好的例子是优步使用的实时激增定价算法。没有实时数据，该模型无法纠正市场的供需失衡。然而，将实时数据呈现给人类(相对于将它吸收到模型中)通常没有多大价值，因为它很难采取行动，并且通常只会导致信息过载。在大多数情况下，特别是如果是为了度量监控的目的，实时数据最多是一个“好东西”。

优秀的数据科学家应该能够倾听利益相关者的痛点以及他们想要实时数据的理由，并能够在确定用例的正确数据延迟和保留期时充当思想伙伴。

5.**“为什么 XX(分析、数据可视化等。)如果数据已经存在，需要这么长时间？”**

没有数据背景的人，往往会把数据的存在误认为是数据的可用性；仅仅因为一段数据“存在”，并不意味着它是可消化和可用的格式，至少对于没有受过深入数据训练的人来说是这样。每个数据科学家都知道，数据清理和格式化在他们的日常工作中需要花费大量时间。不幸的是，缺乏对数据的理解通常会导致利益相关者和数据科学家之间的不信任。

***作为数据科学家如何化挫折为机遇***

对于数据科学家来说，学会用通俗易懂的语言解释分析概念并让利益相关者参与数据转换之旅非常重要。如果数据以原始日志的形式“存在”在数据库中，那么向风险承担者展示少量的数据样本可能有助于解释为什么在转换数据之前很难生成任何信息性的见解和/或可视化。业务利益相关者对数据分析工作流的理解越好，他们就越能理解您的时间表要求。

**感谢阅读！如果你想了解更多关于数据科学和商业的知识，这里有一些推荐:**

[](/top-qualities-hiring-managers-look-for-in-data-scientist-candidates-2e2cd52444c2) [## 招聘经理对数据科学家候选人的最高要求

### 其中一些可以说比编写高效的代码更重要

towardsdatascience.com](/top-qualities-hiring-managers-look-for-in-data-scientist-candidates-2e2cd52444c2) [](/5-mistakes-i-wish-i-had-avoided-in-my-data-science-career-6c22a44304a1) [## 我希望在我的数据科学职业生涯中避免的 5 个错误

### 我得到了这些教训，所以你不必这样做

towardsdatascience.com](/5-mistakes-i-wish-i-had-avoided-in-my-data-science-career-6c22a44304a1) [](/how-to-pick-the-right-career-in-the-data-world-1cec8a084767) [## 2 如何在数据世界中选择合适的职业

### 数据科学家，数据分析师，还是数据工程师？你怎么知道哪个适合你呢？

towardsdatascience.com](/how-to-pick-the-right-career-in-the-data-world-1cec8a084767)