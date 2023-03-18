# 数据孤岛在您组织中的位置

> 原文：<https://towardsdatascience.com/where-data-silos-live-in-your-organization-f51ecdd90809>

## 你听说过影子 IT，但是影子数据呢？

![](img/eb3f1fa82a43778d938177ba6820fe8c.png)

照片由[斯蒂芬·彼得森](https://unsplash.com/@stephencpedersen?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)在 [Unsplash](https://unsplash.com/s/photos/silo?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) 上拍摄

数据孤岛和黑暗数据:每个组织都有——从定义上来说，我们没有人知道完整的范围。有时数据隐藏起来，不受数据团队的审查，类似于 [shadow IT](https://en.wikipedia.org/wiki/Shadow_IT) 。

影子数据(或数据孤岛)在以下情况下出现:

*   自主性和速度优先于技术标准；
*   数据访问或资源有限，迫使团队围绕现有系统和流程工作；或者
*   数据消费者决定部署他们自己的点解决方案，而不是与您合作。

但是消费者不是挥舞白旗，而是经常在数据团队的监视之外找到他们需要的东西——这是有风险的。

![](img/8c255fb3df909c22b6e16eecc26f09e4.png)

如果您的数据平台或产品过于笨重，数据消费者，甚至您的数据团队成员都会找到另一条路——很可能是一条不太可靠和合规的路。[奥利弗·鲁斯](https://unsplash.com/@fairfilter?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)在 [Unsplash](https://unsplash.com/s/photos/two-paths?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) 上拍摄的照片

数据孤岛给数据消费者和数据团队带来了许多风险，例如:

*   **脆弱性**:我敢打赌，金融分析团队的 John 没有为他的数据集准备像依赖管理和异常检测这样的系统。当高管们来问你为什么这个指标是错的时，如果你不知道它是如何产生的，那就很难调试。无论哪种方式，这都会带来有价值的业务数据丢失的风险。
*   **知识流失**:如果一个数据“超级用户”离开了，你不会想知道如何对你现在继承的他们的深奥系统进行逆向工程。这不仅是一种糟糕的资源分配，而且他们的系统可能在被发现成为问题之前就已经造成了数不清的麻烦(一家公司发现，在一名团队成员离开后，他们的一种预测算法被发现自动运行，导致数百万美元的收入受到影响)。
*   **保安**:“我都不知道这件事！”不会阻止监管机构对不当处理个人数据处以罚款。对 GDPR 来说，罚款最高可达公司收入的 4%——哎哟。
*   **不稳定的访问**:当分析师无法访问他们需要的东西时，他们会变得暴躁，这是理所当然的，因为这些东西无法加入到他们的规范用户表中。这些数据孤岛要么造成不透明，要么需要重复流程，这两者都不是积极的结果。
*   **狭隘的决策**:虽然数据消费者可以通过用户友好的点解决方案快速行动，但对于复杂的决策，他们可能需要专家来考虑实验设计、采样偏差和混杂因素。整个部门可能会围着马车，朝着一个不会从根本上增加业务价值的目标前进，或者以任意的方式进行衡量。

那么，数据团队如何识别隐藏在暗处的数据孤岛呢？他们能否以此为契机，发现其数据平台的弱点，并通过鼓励或强迫的方式吸引消费者？

在我看来，答案是肯定的。让我们看看数据孤岛在哪里，以及如何打破它们。

# 数据仓#1:转换和预聚合

但是在我们谈论数据消费者之前，让我们不要让自己作为数据专业人员完全摆脱困境。在我们不切实际的尝试中，我们创建了我们的数据孤岛，以满足不断增长的数据需求，同时在我们团队的能力范围内工作。

我们公司前几天经历了一个事件，这是由于将 DataDog 添加到我们的技术堆栈中，这将一些跟踪信息引入到流入我们应用程序的数据结构中。

当数据被持久化到 S3 中，然后被摄取到数据块中时，它只是被部分加载，所以我们的管道中有丢失的数据。

我们的事后分析得出结论，我们的 Spark 工作过于复杂，有太多的转换。作为最佳实践，我们应该做的是在关键的检查点将作业分解成一系列更小的转换，这些转换写入到可以监控的表中。

在处理老派的 ETL 和商业智能实现时，我见过类似的场景。数据是为性能而预先聚合的，底层对于负责诊断关键指标暗中下降的分析师来说是不可见的。如果分析师知道基础数据是如何转换的，他们就很幸运了，更不用说能够成功找到下降的原因了。

随着从 ETL 到 ELT 的转变，这种行为也有所改变。如今，您更可能看到数据团队围绕将转换分解成清晰的步骤(例如，事件= >会话= >用户= >活动)建立最佳实践，而不是编写只有所有者才能理解的三页 SQL。

虽然商业智能工具会吹捧它们的数据准备能力，但这最终会变成对工具之外的团队不可用的另一个业务逻辑筒仓。很明显，最后一英里操作有一些好处，也许 BI 中的“不超过 SELECT*”这样的规则太苛刻了，但是任何可重用的语义必须对您的团队广泛可用。

***解决方案*** *:将复杂的转换或 SQL 查询分解成不同的检查点，这些检查点将数据写到被监控数据质量的表中。*

*确保您的业务逻辑不会被锁定在只有部分用户可以访问的单一工具中。例如，您可以通过实现一个能够服务于商业智能和分析用例的度量层来消除孤岛；以及可以跨机器学习应用使用的特征存储。*

*编码语言也可能自然形成孤岛，因此应尽可能考虑标准化。这种极端形式目前正在上演，用 Python 编码的 Tesla 工程师正试图集成到主要用 Scala 编码的 Twitter 中。*

# 数据筒仓#2:电子表格

![](img/0a753330c606ca754b1ef6eba0fe227a.png)

[sasi rin pamai](https://www.shutterstock.com/g/sasirin+pamai)via Shutterstock。

在许多组织中，电子表格仍然是使数据民主化的最成功的方式，即使它们可能偶尔会成为数据团队痛苦和嘲笑的来源。

我们在财务部门的合作伙伴可以通过 PC 和 VLOOKUP 做一些了不起的事情，根据我的经验，没有什么比将表格放入 Google Sheets 并与合作伙伴合作手动添加标签更好的方法来民主化新数据的原型，这些标签是他们在分析中可以看到的有意义的属性。

当电子表格从原型进入生产阶段时，它就变成了一个数据仓库。或者换句话说，如果您不止一次看到同一个电子表格在业务运营中发挥作用，那么是时候将逻辑向上游移动，创建更系统的东西了。

***该审查通常会揭示解决您的数据平台中的差距的方法，并可以帮助您进行上游转换，以提高可观察性和可扩展性。您甚至可能会发现新的机会，使诸如终身价值(LTV)等指标标准化，以获得更广泛的应用，并在更精细的层次上产生它们。***

***在消除财务数据孤岛时，数据完整性非常重要。除非您能够向财务合作伙伴展示您的系统精确到每一分钱，是最新的，并且在他们需要提供业务关键报告时可用，否则您将无法将电子表格逻辑向上游移动。***

# **数据孤岛#3:“一体化”解决方案——ESP、CDP、DMP、A/B**

**如果做错了，这些可能是最难控制的筒仓。**

**许多[营销技术栈](https://lumapartners.com/content/lumascapes/martech-lumascape/)，如电子邮件服务提供商和营销自动化平台，在现代数据仓库的进步之前脱颖而出。这意味着提高影响力的最便捷方式是采用一体化解决方案，直接收集、管理和向营销人员提供数据。不可否认，我曾经推销过运行实验的“单行 javascript”梦想，它可以让你避免与“它”进行任何进一步的对话。**

**这种孤岛造成的一些最紧迫的问题是，这些系统很快经历了客户群的无序蔓延(产品页面重复访问者 2020 年 10 月)，并且分割的活动通常缺乏衡量。**

**回想我做咨询的时候，我估计一家大型电信公司正在“微瞄准”**不到 1%的客户群**，因为他们不知不觉地将营销活动过滤到满足其复杂细分中每个**属性的客户。****

**但是几年前我们有了转机——数据团队和技术现在能够足够快速和灵活地以业务的速度运行，同时利用仓库中丰富的数据释放新的机会(“嘿，想为 LTV 优化而不是点击进入？”).营销人员和其他业务合作伙伴看到了数据团队的价值，而不是绕过它。**

**这些营销第一的解决方案正在适应。无论您是选择现代的 CDP 还是反向 ETL 来将数据传输到营销人员手中，必备的特性是在您的企业数据仓库上进行收集、转换和基本的分段操作。**

*****解决方案*** *:我发现让营销团队参与进来的最佳方式是创建尊重和满足他们对速度和自主权的需求的系统，同时合作确保强有力的治理和衡量是解决方案的一部分。***

***你不仅需要给他们一个更好的工具，在某种程度上你还需要让孤立的系统退役，即使会有阻力。在你到达这一点之前，请穿上营销的鞋子走一英里。合作开展营销活动，并利用这一经验展示您可以自动化和优化流程，同时为营销活动带来更高的回报。***

***不幸的是，数据孤岛本身就带有政治色彩。营销自动化工具可以从营销预算中获得资金，而数据仓库将来自数据团队相对较少的预算。构建业务案例，同时与运营商和高管达成共识。***

# **我的推荐？主动消除孤岛**

**让睡觉的狗躺着可能很诱人，但在我看来，数据团队应该积极主动地消除数据孤岛或任何“影子数据”系统。**

**我通常选择梦想领域的方法——“如果你建造了它，它们就会到来。”(这种方法可能更类似于收集需求、确定项目范围、获得批准、构建最小可行产品、获得反馈、迭代，它们就会到来——但这远没有那么简洁)。**

**但是，如果您构建了它，但他们没有来，那么您需要解决这是否是您的技术解决方案的失败，缺乏组织的认同，或者完全是其他原因。然后，您需要找到一个解决方案，让您走上打破孤岛的正确道路。**

**毕竟，数据最终是数据团队的责任，消费者将做他们需要做的事情来访问它。作为数据领导者，我们前进的最佳途径是接受这一现实，并采取措施缓解它。**

**[关注我](https://medium.com/@shane.murray5)，了解更多关于数据领导、数据科学应用和相关主题的故事。[订阅](https://medium.com/subscribe/@shane.murray5)将我的故事发送到你的收件箱。**