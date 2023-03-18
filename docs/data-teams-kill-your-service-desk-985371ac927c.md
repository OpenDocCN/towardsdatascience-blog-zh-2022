# 数据团队:干掉你的服务台

> 原文：<https://towardsdatascience.com/data-teams-kill-your-service-desk-985371ac927c>

## 我们能否超越服务台陷阱，同时仍然满足业务利益相关者的需求？

![](img/39d1098ac50ffb9a6d39dba69baca575.png)

*照片由* [*海梅丹塔斯*](https://unsplash.com/@jaimedantas?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) *上* [*Unsplash*](https://unsplash.com/?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)

*抓住 Excalibur，杀死你的宿敌:服务台——数据团队永远的敌人。*

在我们花了两年时间构建 Workstream.io 的过程中，我与许多数据领导者谈论过他们最讨厌的工具:用于管理他人请求的“服务台”。

我广义地使用术语“服务台”，因为数据团队有许多不同的方式来完成这项工作。

我们的一个客户有一个叫做“数据吸收”的松弛通道名字本身就能告诉你很多人的感受。其他团队使用谷歌表单，实现了像 JIRA 服务台这样的工具，或者，最糟糕的是，利用一些可怕的组合。

团队首先讨论防止或减少这些请求的方法。我们应该让请求变得更难吗？也许是我们的团队结构加剧了这个问题？我们陷入服务陷阱了吗？我们需要在适当的文档和培训上投入更多吗？我们是否应该采取更多措施来实现自助式分析？

人们提出了这些问题，采取了一些举措，但另一方面却是一个可怕的事实:其他人的问题依然存在。数据团队发自内心的、情绪化的、近乎原始的反应也是如此。

我们的利益相关者呢？他们也仍然讨厌提出要求。

为什么我们都有这种感觉，为什么我们仍然对此无能为力？

# 因为服务体验糟透了

数据团队讨厌他们的服务台，因为我们希望专注于我们认为高价值、战略性的工作。(我们这样做是正确的)。

然而，这种厌恶远不止是工具本身。毕竟，当前一代的“服务台软件”是对之前任何产品的重大改进:锅炉房呼叫中心，那里的代理人努力支持沮丧、愤怒的客户，很少得到他们想要的答案。一个随机的电话号码，你打电话给你的内部 IT 团队，并留下语音邮件说你的电脑坏了。我们今天讨厌的支持系统——比如票务或聊天——天生就是比它们的前辈好得多的体验。

因此，虽然我们可能会抱怨 JIRA 服务台，及其笨重的事务性用户界面，但我们的厌恶是更深层次的:服务体验——除了 Zappos 等少数明显的例外——通常很糟糕。

因此，当我们重新利用那些旨在促进这些体验的工具时，我们向自己和我们的同伴发出了很多关于我们应该如何感受和行为的信号。我们的参考点变得相当字面上，当你被留在等待几个小时，或当辱骂，愤怒的客户尖叫古怪的要求和淫秽的时候。

与我们的服务经历相关的包袱太多了，我们无法打破这个循环。这意味着我们都不幸地以不快乐告终，我们的团队无法充分利用在我们的数据上所做的投资。

# 因为数据团队既不是产品团队，也不是服务团队

在我们的社区中有一场关于数据团队本质上是产品团队还是服务团队的激烈辩论。与传统的客户服务或产品开发这两个截然不同的职能不同，数据团队集支持、产品和工程职能于一身。同一个团队研究和确定产品范围，计划和执行开发工作，对错误进行分类，并管理其他人的大型复杂集合的期望。

现实是，每个数据团队都必须平衡他们的“产品工作”(定义、界定和构建具有长期价值的数据产品)和他们的“服务工作”(响应业务的诊断需求)。虽然后者可能在极少数情况下是令人兴奋的，但当请求是战略性的时，它更经常地令人讨厌，无论是需要拉一个数字，还是对一份报告的行动反馈。

我们都凭直觉知道这一点，这就是为什么即使是关于数据团队作为产品团队的最引人注目的讨论也包括部署令人讨厌的服务台来管理其他人不必要的突发奇想和干扰。

作为推论，也正是这种平衡产品和支持工作的需要，让我们认识到，对于数据团队来说，敏捷是“最糟糕的政府形式——除了我们已经尝试过的所有其他形式。”

为什么敏捷不是数据团队的*完美*的标准论点是，数据工作更具迭代性，没有执行分析或洞察的预定义终点。这是真的。然而，我也认为敏捷并不是一个完美的选择，因为数据工作的工作流程比以前更加相互关联、协作性更强、模块化程度更低。

服务台和敏捷框架都是为了让*可预测系统*——具有可测量的标签输入和可测量的功能(或答案)输出——更加高效。但是处理*不可预测的复杂系统*的出色工作也是如此——例如，同一个团队同时扮演*被动的支持者和主动的建设者*。这是一个复杂的世界，有两个(或更多)竞争的重心。

尽管它们都有不足之处，但我们都实现了它们——认为如果我们能够管理期望，或者设置明确的优先级，这些工具可以互补。如果我们聪明，我们就能打破这个循环。但最终，我们在某些方面失败了，仍然责怪我们的服务台。毕竟，它代表了所有我们讨厌的东西，并使我们远离我们热爱的东西(构建数据产品)。

# 因为服务台关乎权力动态

我们经常认为服务台的外形是我们成功的决定性因素。但事实真的是这样吗？

一种选择是在一个宽松的渠道中管理和交付请求，这可以优化协作和速度。对话发生在人与人之间，并且对跟随的任何人都是公开的。这种模式的论点是，数据对话与您组织中的任何其他对话没有什么不同，它们应该被如此对待。但是消息传递是出了名的饶舌，糟糕的搜索让对话无法追踪，并且期望几乎即时的响应时间是常态。

因此，最成熟的数据团队，那些管理复杂的技术和人员系统的团队，以及那些执行最雄心勃勃的项目的团队，通常会利用一些正式的票务解决方案。这种方法有助于管理对响应时间的期望，并将团队从妨碍深入工作的持续干扰中解放出来。然而，它牺牲了人们接收答案的速度，换取了传递答案者的效率。

这两种形式都忽略了一点，即数据团队不为其他人服务，其他人也不为他们服务。他们都忽略了一点，那就是我们都在互相服务，互相依赖。

我们讨厌服务台，因为它的设计迫使我们决定谁应该行使权力:我们自己，还是其他人？有没有办法走出这个悲惨的循环？

# **杀死服务台的 3 种方法**

最终，团队的成功不在于我们提交请求或发布专题报道的效率，而在于我们对推动组织前进的数据建立共同意识的能力。

正如斯坦利·麦克克里斯特尔将军在他的书《团队的团队》(Portfolio/Penguin，2015 年)中解释的那样，现代世界是“复杂的”，活动的速度和相互依存性使得[“不可能说出哪些事件可能导致什么样的结果。”](https://review.firstround.com/what-startups-can-learn-from-general-mcchrystal-about-combining-strategy-and-execution)简单来说，传统的系统和团队是线性和模块化的。系统被设计成将输入转化为输出，无论是将矿石转化为酒吧，将汽车零件转化为汽车，还是将客户问题转化为解决方案。人员可以被分成执行特定任务的模块化子团队，在这些子团队中，完成一个人的角色只需要相对较少的关于过程中的前一步或下一步的上下文。

相比之下，复杂系统是多维的，相互依赖的。输入同时来自多个维度，输出遵循任意向量。为了应对这个世界，团队成员既需要*的共同意识——*对他人工作的充分理解和同情——也需要*的执行能力——*这意味着他们可以利用自己的知识做出独立的决策。

这就是数据驱动团队所处的世界:一个复杂的世界。它是数据人和其他人之间的空间，在这里每个人都需要访问*共享意识*需要*在任何时候执行*。这是一个传统管理系统无法设计、甚至无法理解的世界。

基于麦克克里斯特尔将军的概念，这里有 3 条建议，可以在满足业务利益相关者需求的同时，超越服务台陷阱:

1.  **主动构建与您的团队同呼吸共命运的文档**。大多数数据团队已经为最终用户维护了一些文档。这种文档通常以传统格式存在——作为 Google doc 的一部分，或者与数据资产本身完全分离的企业内部网。但是，正如 Fishtown Analytics 的联合创始人 Drew Banin 在他在 Coalesce 2020 上发表的开创性演讲“[后现代数据堆栈](https://www.getdbt.com/coalesce-2020/the-post-modern-data-stack/)”中指出的那样，内容和对话需要保持一致，以便每个人都可以轻松访问和消费:“在未来……我们将有专门的媒体来讨论上下文中的数据。这有两种形式。一个是向消费者推送数据……在这个 feed 中，消费者将能够订阅与他们相关的信息。另一个媒介…是您和您的同行将能够就您的数据在上下文中进行对话。”基于他的想法，我相信这将包括:

*   **常见问题。**来自业务用户的重复问题是数据团队的负担，也是对您时间的巨大浪费。有了更好的文档，那些重复的问题可以被推广并公开给任何用户去发现。
*   **培训内容:**这可能包括录制的视频或书面的操作指南，可能是关于如何自助服务、如何最好地利用过滤器等基本功能，或者了解底层数据。
*   **生命周期和认证状态:**让最终用户清楚资产处于其生命周期的哪个阶段，以及它是否得到您的团队的积极支持。
*   **状态页面:**考虑使用数据质量和可观察性解决方案，甚至 dbt，为您最关键的数据资产构建和维护“状态页面”。这让最终用户无需询问您就能了解数据是否可信。

**2。投资了解你的用户。**真正了解您的用户至关重要，否则您如何构建满足他们需求的解决方案？

这从一开始就开始了——在你建造任何东西之前。在你考虑解决方案之前，或者在你努力的方向之前，你需要了解业务经历的问题。一旦你开始做一些事情，一定要和其他人合作，获得他们的反馈并建立信任。

随着时间的推移，投资去理解你的用户——不管是轶事式的还是主动的。进行用户访谈，了解人们最常用的是什么，以及它如何影响他们的决策。他们在与您的数据交互时遇到的常见难题是什么？

然后你想用数字对主观反馈进行三角测量。挖掘任何可用的资源，以了解您的环境中哪些资产是趋势性的，并且经常被使用。

通过所有这些，你可以更好地理解你的工作最有价值，以及你的路线图应该指向哪里。如果你能理解你的产品是如何被使用的，你就能对数据如何适应日常决策有独到的见解。

**3。考虑实施数据管理员解决方案，根据需要随时随地为每个人提供有关其数据的知识**。数据管理员顺利地将一个人的理解传递给另一个人。它将用户准确地定位到他们正在阅读的内容，并验证和联系其来源。这有助于他们理解其他人问了什么问题，不仅仅是答案是什么，还有接下来做了什么。它把每一条数据和每一个输出都当作一个人们需要搭载的产品，并教他们如何正确使用它。

# 结论

在未来 10 年，每个组织都将使用多种工具来消费和分析数据。如果我们继续受到票据、优先积压和权力斗争的约束，数据团队将永远无法发挥其全部潜力。为了以真正数据驱动的方式运营，我们需要超越“我们与他们”的误解，并找到与“其他人”合作的新方式。服务台是我们最常被集体诋毁的工具和活动之一，它将被我们喜爱的东西所取代，这有助于我们更有效地合作。

我们需要在塑造我们的未来中发挥积极作用，以确保每个人(数据从业者和其他人)始终能够从我们最重要的资产——数据——的集体知识中获得力量。