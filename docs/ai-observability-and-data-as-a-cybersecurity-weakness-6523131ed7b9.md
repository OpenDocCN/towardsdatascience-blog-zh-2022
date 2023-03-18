# 人工智能的可观察性和数据是网络安全的弱点

> 原文：<https://towardsdatascience.com/ai-observability-and-data-as-a-cybersecurity-weakness-6523131ed7b9>

## [播客](https://towardsdatascience.com/tagged/tds-podcast)

## 戴夫·希尔科谈监控和理解你的数据的重要性

[苹果](https://podcasts.apple.com/ca/podcast/towards-data-science/id1470952338?mt=2) | [谷歌](https://www.google.com/podcasts?feed=aHR0cHM6Ly9hbmNob3IuZm0vcy8zNmI0ODQ0L3BvZGNhc3QvcnNz) | [SPOTIFY](https://open.spotify.com/show/63diy2DtpHzQfeNVxAPZgU) | [其他](https://anchor.fm/towardsdatascience)

*编者按:TDS 播客由 Jeremie Harris 主持，他是 Gladstone AI 的联合创始人。每周，Jeremie 都会与该领域前沿的研究人员和商业领袖聊天，以解开围绕数据科学、机器学习和人工智能的最紧迫问题。*

假设你是一家大型对冲基金，你想出去给自己买一些数据。数据对你来说非常有价值——它会影响你的投资决策，决定你的结果。

但是当你收到数据的时候，一股寒气顺着你的脊梁袭来:你怎么知道你的数据供应商给了你他们承诺的数据？从您的角度来看，您正盯着电子表格中的 100，000 行，无法判断其中一半是不是虚构的，或者更多。

事后看来，这似乎是一个显而易见的问题，但这是我们大多数人都没有想到的问题。我们倾向于假设数据就是数据，电子表格中的 100，000 行就是 100，000 个合法样本。

确保您正在处理高质量的数据，或者至少您拥有您认为您拥有的数据，这一挑战被称为*数据可观察性*，它在大规模上解决起来令人惊讶地困难。事实上，现在有很多公司专门从事这方面的工作——其中一家是 Zectonal，它的联合创始人戴夫·希尔科将加入我们今天的播客。

Dave 的职业生涯一直致力于了解如何评估和监控大规模数据。在云计算的早期，他首先在 AWS 这样做，现在通过 Zectonal，他正在研究允许公司检测数据问题的策略——无论这些问题是由故意的数据中毒还是无意的数据质量问题引起的。在这一集的 TDS 播客中，Dave 和我一起讨论了数据可观测性、数据作为网络攻击的新载体以及企业数据管理的未来。

以下是我在对话中最喜欢的一些观点:

*   不能总是相信数据供应商会在他们承诺的时候交付他们承诺的数据。戴夫发现，在某些情况下，数据供应商会复制，甚至直接捏造样本添加到合法数据中，以欺骗他们的客户，让他们认为他们收到了承诺的全部数据。总的来说，公司缺乏一个系统的方法来评估这种情况何时发生以及是否会发生。
*   与数据数量和质量同样重要的是数据到达的时间。旧数据可能会过时，如果供应商数据的预期年龄与其实际年龄之间存在重大延迟，您可能会遇到超出分布的采样问题，这会使模型表现不佳。从这个角度来看，数据可观测性可能会成为一个人工智能安全问题。
*   合成数据是我们之前讨论过的一个话题。它允许我们通过利用嵌入了大量世界知识的大型模型(想想:GPT-3)，生成实际上可能比“常规”数据信息更丰富的新样本，这些模型可以用来生成解释原始数据没有捕捉到的上下文的样本。但是，数据供应商也可以利用合成数据来夸大一个小得多的真实数据集，以欺骗客户，让他们相信他们获得了比实际更多的原始数据。Dave 认为，随着合成数据生成的不断改进，这将成为未来的一个主要问题。
*   Dave 讨论了 Zectonal 最近进行的一项实验，该实验显示了如何将数据用作实施新型网络攻击的载体。许多网络攻击涉及向易受攻击的 API 发送命令，这导致这些 API 以某种方式失败，从而产生可被黑客利用的漏洞。因此，一整套网络防御生态系统已经发展到可以防止这种正面攻击得逞，或者至少可以减轻它们的影响。但 Zectonal 的研究显示了恶意有效载荷是如何被插入数据中的，这几乎没有受到太多的网络安全审查。Dave 假设数据在未来将成为网络攻击者的一个重要渠道，特别是考虑到历史上很少注意保护数据。

![](img/f03b32954f4b37c25292ffdc418ef95b.png)

## 章节:

*   0:00 介绍
*   3:00 什么是数据可观测性？
*   10:45 与数据提供商的“有趣交易”
*   12:50 数据供应链
*   16:50 各种网络安全影响
*   20:30 深度数据检查
*   27:20 观察到的变化方向
*   普通人能走的 34 步
*   41:15 GDPR 过渡的挑战
*   48:45 总结