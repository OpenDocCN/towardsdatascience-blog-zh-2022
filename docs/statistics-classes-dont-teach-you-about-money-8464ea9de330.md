# 统计课不会教你关于金钱的知识

> 原文：<https://towardsdatascience.com/statistics-classes-dont-teach-you-about-money-8464ea9de330>

## 数据科学项目的实际第一步

[统计学](http://bit.ly/quaesita_statistics)和[数据科学](http://bit.ly/quaesita_datascim)课程并没有为学生在工作中制定项目规范做太多准备。这里有几个问题:

*   他们教你将问题陈述视为理所当然，但如果你的老板没有能力提出合理的要求，该怎么办？
*   他们不会教你钱和数据预算，所以你学习如何计算理想的数据需求，而不是在商业环境中寻找实用方法所需的成本效益思维。
*   他们不会教你谈判技巧，尤其是帮助你在谈判可行的预算以执行数据收集的灰色区域中导航的灵活性。
*   他们更可能倾向于[继承数据，而不是原始数据](http://bit.ly/quaesita_provenance)设置，因为这对你的教授来说更容易评分。
*   他们忽略了现实世界的细节。

![](img/588cb359a5b22a5b8d749be8a0eeb4a3.png)

由[安特·哈默斯特](https://unsplash.com/@ante_kante?utm_source=medium&utm_medium=referral)在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上根据照片修改

# 数据科学家的第一天工作

假设你是一名[数据科学家](http://bit.ly/quaesita_datascim)，受雇[估算](http://bit.ly/quaesita_vocab)下图森林中松树的平均高度。

![](img/e51a864ee9655e17e7972b594da96f7d.png)

这片森林里的树有多高？照片由 [Marita Kavelashvili](https://unsplash.com/@maritafox?utm_source=medium&utm_medium=referral) 在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄

*(注意:本文中的链接会带你到我对出现的任何行话术语的轻松解释。)*

# 事实与统计

如果我们完美地测量每一棵树，我们会得到比估计值好得多的东西。我们会得到一个**事实**。关于这片森林中树木高度的真实[真相](http://bit.ly/quaesita_saddest)。有了事实，就不需要[统计](http://bit.ly/quaesita_statistics)。

> 当你有事实时，你不需要统计数据。

然后你应该出去测量每棵树的普朗克长度(物理学中最小的长度单位，一个单位等于 0.00000000000000000000000000000001616255 米)吗？你会使用哪种仪器来获得如此精确的测量结果？我敢打赌，你的车库里肯定没有它，尤其是它还没有被发明出来。

即使我们满足于人类最精确的测量设备(数量级太不精确，如果你一心想要普朗克长度)，用它测量一棵树可能会太昂贵，不管你的老板出于什么目的雇用你。

此外，即使你满足于木板长度而不是普朗克长度，并允许你四舍五入到最近的米，测量每一棵树都是多余的…你的森林太大了。你的老板会同意你收集所有东西的完美主义愿望吗？

> 统计抽样就是从你的问题中获得一个视角，这个视角虽然不如事实完美，但已经足够好了。

如果你像优秀的[统计学家](http://bit.ly/quaesita_statistics)一样思考，你就不会有完美主义的冲动——当你可以通过抽取一个[样本](http://bit.ly/quaesita_vocab)得到一个*足够好的* [估计](http://bit.ly/quaesita_vocab)时，为什么还要测量整个[人口](http://bit.ly/quaesita_vocab)？当然，这引入了不确定性(我们不再处理事实)，但也许我们可以接受。让我们测量足够好的树木样本，这样我们就不必测量所有的树木了！

# 但是等等…什么是“足够好”？

我们甚至还没有走近一棵树，就已经在看似简单的树木测量任务中遇到了两个障碍:

*   如果我们不用普朗克长度来测量，测量应该有多精确？
*   如果我们不测量所有的树，我们应该测量多少棵树？

通过这两个问题的方法是理解 ***为什么*** 你的项目首先存在:任务的目的是什么，*【足够好】*实际上是什么意思？这是一个关于成本收益的问题，如果你不了解项目的现实世界，你就无法回答这个问题。

> 从为什么开始:你为什么要收集数据？你的项目的目的是什么？*“足够好”*实际上是什么意思？

不幸的是，如果你是团队中的新员工，严格来说，设定“足够好”的标准是别人的工作。这个人通常是老板。除非你是老板，否则这不是你能决定的。如果你把现实世界的数据问题当成作业题，这对你来说将是一场斗争。

![](img/e2f01d4bc98cb5680b73017e99819ab2.png)

由[micheile . com](https://unsplash.com/@micheile?utm_source=medium&utm_medium=referral)在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上的照片修改而来

## 统计课不会教你关于金钱的知识

第一个问题是[数据科学专业人员](http://bit.ly/quaesita_universe)的课堂课程很少提及[数据](http://bit.ly/quaesita_hist)预算。大多数家庭作业问题要求你想当然地对待[样本大小](http://bit.ly/quaesita_vocab)，让你的大脑与[继承的数据](http://bit.ly/quaesita_notyours)一起工作，但对你处理现实世界中的数据收集谈判毫无帮助。

> 停止将数据视为无价之宝。数据不是神圣的；和其他资源一样，它也是一种资源。

其他的家庭作业问题教你计算你需要的[样本量](http://bit.ly/quaesita_vocab)，却没有让你为下一点做好准备:如何筹集你实际得到这个理想样本量所需的钱。(更不用说向对数字过敏的老板解释权力分析预算曲线的礼节了。)这种教育疏忽最好斗的表现之一是习惯于将数据视为无价之宝，导致奇怪的行为，在团队中的其他每个成年人看来，这些行为都近乎幼稚。在现实世界中，稀缺是存在的，好东西是要花钱的。这也适用于数据。数据不是神圣的；和其他资源一样，它也是一种资源。

## 老板们明白他们在要求什么吗？

第二个问题是你老板的技术水平。如果你掌控了局面(你领导你！)而没有花时间去完全理解你老板的想法，你就有可能做出不适合问题的解决方案。

另一方面，如果你向老板提出测量和样品尺寸规格的要求，那么，这里也有龙。

假设你的老板回答:“请给我 20 棵树，以英尺为单位。”

将项目愿景转化为[样本量](http://bit.ly/quaesita_gistlist)要求需要技巧，在你了解[你老板的决策技巧水平](http://bit.ly/quaesita_ytjenny)之前，很难判断他们的反应是深思熟虑还是懒惰。这可能正是你前进所需要的，但是除非你的老板有数据和测量的经验，否则他们的即席回答可能会让项目陷入困境。他们很有可能会让你徒劳无功。

除非你和你的老板密切合作，否则你不会知道。

再来说说决策技巧！在 bit.ly/quaesita_ytjenny[的 YouTube 上观看](http://bit.ly/quaesita_ytjenny)

## 假设，假设，假设

一旦你在处理不确定性，你就需要在你拥有的事实(你的几棵树样本)和你希望拥有的事实(你的森林中所有树的总数)之间架起一座桥梁。那座桥就是[假设](http://bit.ly/quaesita_saddest)。假设使一个[统计](http://bit.ly/quaesita_fisher)项目打勾。

> 数据+假设=推断

棘手的是你的老板——而不是你！—负责设定项目的[假设](http://bit.ly/quaesita_jupimoon)的人。如果你不是决策者，那么你的工作就是充当数学和你老板脑子里的东西之间的翻译。这是他们在课堂上很少涉及的另一项技能。

[](/tough-love-for-naïve-data-newbies-5dd376693eea) [## 对天真的数据新手的严厉的爱

### 不懂统计数据的书呆子会犯的 3 个错误

towardsdatascience.com](/tough-love-for-naïve-data-newbies-5dd376693eea) 

## 抛开现实世界

我将在下一篇文章中讨论这一点，但简单来说，学校忽略了大部分真实世界的细节。就像这一段。

# 数据项目中真正的第一步

[决策科学家](http://bit.ly/quaesita_di)和更有经验的[数据科学家](http://bit.ly/quaesita_datascim)在开始每个项目时，都会仔细地与老板面谈，以确保数据收集请求的规格清晰，并且符合老板对项目的愿景，同时平衡数据收集过程的成本效益。唉，这是你不太可能在课堂上学到的技能。没有它，你很可能会篡夺老板的角色，或者惊慌失措，完全按照老板说的去做。两个都不好！

> 如果你是一个没有经验的数据工作者，很有可能你会篡夺老板的角色，或者惊慌失措，完全按照老板说的去做。两个都不好！

只有当负责人清楚地了解“足够好”对项目意味着什么，并有能力(通过自己的技能或同事的帮助)将其转化为数据专业人员可以使用的语言时，从事实领域转向不确定领域才是安全的。一切都应该从目的开始——项目的 ***为什么***——并仔细考虑信息的成本效益现实。

这意味着你在任何数据项目中的第一个真正的任务与数字关系不大，更多的是与心理学和沟通有关。

> 每个数据项目都从一个重要的步骤开始:了解你的老板和你的业务。

每个数据项目都从一个重要的步骤开始:了解你的老板和你的业务。跳过这一步，后果自负！

# 感谢阅读

如果你喜欢这篇文章，继续下一篇: [**简单随机抽样真的简单吗？**](http://bit.ly/quaesita_srstrees1) 即将到来！与此同时，顺道拜访并在 Twitter 上打招呼。

[](https://kozyrkov.medium.com/membership) [## 加入介质

### 阅读 Cassie Kozyrkov(以及媒体上成千上万的其他作家)的每一个故事。您的会员费直接支持…

kozyrkov.medium.com](https://kozyrkov.medium.com/membership) 

*附言:你有没有试过在 Medium 上不止一次点击这里的鼓掌按钮，看看会发生什么？* ❤️

# 喜欢作者？与凯西·科兹尔科夫联系

让我们做朋友吧！你可以在 [Twitter](https://twitter.com/quaesita) 、 [YouTube](https://www.youtube.com/channel/UCbOX--VOebPe-MMRkatFRxw) 、 [Substack](http://decision.substack.com) 和 [LinkedIn](https://www.linkedin.com/in/kozyrkov/) 上找到我。有兴趣让我在你的活动上发言吗？使用[表格](http://bit.ly/makecassietalk)联系。