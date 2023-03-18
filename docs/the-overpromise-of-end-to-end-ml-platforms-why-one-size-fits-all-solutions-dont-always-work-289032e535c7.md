# 端到端 ML 平台的过度承诺:为什么一刀切的解决方案并不总是有效

> 原文：<https://towardsdatascience.com/the-overpromise-of-end-to-end-ml-platforms-why-one-size-fits-all-solutions-dont-always-work-289032e535c7>

## 意见

## 机器学习基础设施中定制和灵活性的重要性

![](img/06ec7d8a63c6145f68ea6cdac6fc2288.png)

DALL E -一个供应商锁定成本公司太多钱的例子

最近一年，我的收件箱被试图出售其一刀切基础设施的 MLOps 公司所淹没。但不仅仅是在那里，与 covid 之前的年份相比，会议上的参展商也由 ML(Ops)平台主导。你还可以在 medium 上的每篇相关文章下找到大量垃圾邮件，甚至一个**付费的**研讨会也只是这样一家公司的销售演示。虽然我通常对新产品持开放态度，但有太多的承诺，这篇文章是关于保持独立的重要性。

# MLOps 是 DevOps + ML

MLOps，即机器学习操作，结合了软件工程和机器学习，使组织能够使用 DevOps 原则，以可扩展和可靠的方式部署和管理机器学习模型。MLOps 的一个关键挑战是模型的培训、部署、集成和监控伴随着一系列独特的需求和要求。对一家公司有效的平台不一定最适合另一家公司，即使他们在同一个行业。每个组织都有独特的数据源、业务流程和技术堆栈。

# 缺乏特色

大多数 MLOps 产品都提供 AWS、GCP 或 Azure 的简化版本。虽然学习 AWS(或 GCP/Azure)配置很痛苦，如 AMI 角色、网络、EC2、Lambda 和处理这些的技术(如 terraform)，但可能性很大，所有这些努力给了你一个构建高度定制化系统的机会。此外，您还可以提高工程师的技能，让他们为云做好准备。因此，本文不是针对云，而是针对来自单一提供商的完全集成的解决方案。

这些 ML/MLOps 平台试图通过将细节抽象为日常用例并将所有部分连接起来，使云的使用更加容易。它是关于外包你的 ML 基础设施。只要你只在这些简单的用例中运行，你就没问题，在这种情况下，**你应该看看这些平台**。

不幸的是，生产中的机器学习很少适合这些“玩具”用例。根据我的经验，这非常类似于学术界的数据科学与行业中的数据。它始于一个简单的事实，即一些 ML 平台只支持 Python，这种限制应该已经很惊人了。此外，有些不允许区分批处理和 API 工作负载。有的不支持 GPUs 有些人甚至将您的算法选择限制在预先实现的列表中，或者不允许您根据 GPDR 要求保存数据。列表很长，我想参考[这个存储库](https://github.com/thoughtworks/mlops-platforms)进行比较。

# 锁定风险投资资助的技术

但是总体来说，我并不是很关注特性。您可能会找到一个目前完全符合您需求的解决方案，但是如果在某个时候，您的需求发生了变化，而它不再是了，那该怎么办呢？您会并行构建第二个定制系统吗？你会转移到另一个平台吗？即使你选择了功能丰富、价格最贵的提供商，你认为**的长期锁定**值得吗？

一个付费的、昂贵的机器学习平台可能不是**最具成本效益的**解决方案，尤其是对一家更年轻的公司而言。这些平台可能成本高昂，像大多数风险投资平台一样，它们通过**低廉的初始成本**运作，消耗投资者的大量资金，直到**拥有他们的客户**(供应商锁定)。在某个时候，他们必须盈利，猜猜谁在为此买单？将 MLOps 外包给这些 SaaS 提供商可能会非常昂贵。

# 开源胜出

通过定制的开源方法，组织可以轻松地将其机器学习基础设施与现有系统集成，使他们能够快速轻松地部署和管理模型，而不会中断现有的运营。这是有代价的，你需要人们去做。

当然，有很多工具是你不应该自己开发的。对于标准用例，有些解决方案值得购买；数据摄取、实验跟踪、监控等等。其中大多数甚至是开源的，可以作为托管服务使用。通常，这些工具背后有一个咨询业务，你可以付钱给他们来帮助建立和扩展你的系统。但是这些工具通常是可以互换的，你可以保持被锁定的风险很小，并且你仍然在决定你的 ML 架构。您购买的不是整个堆栈，而是部分。

此外，请记住，通常存在明显的利益冲突。虽然 SaaS 提供商希望您每年花更多的钱，通常是通过基于消费的模式(按计算时间、数据量等付费)，但通过尽可能高效地处理数据来降低您的账单对他们来说并不太有吸引力。

# 结论

总的来说，很明显，MLOps 不是一种一刀切的方法，付费的、昂贵的机器学习平台很少是最好的，也不是最便宜的解决方案。定制的开源方法提供了一定程度的灵活性和适应性，通常更适合公司的需求，可以帮助组织节省资金，同时购买他们真正需要的工具。