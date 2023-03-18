# 谷歌足球挑战赛:第二关

> 原文：<https://towardsdatascience.com/google-foobar-challenge-level-2-7a021f625c1>

## 对秘密编码挑战问题的深入探究

![](img/16985f4215235e1aab308cd9e0ccee7c.png)

Pawel Czerwinski 在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上的照片

第二级包括两个问题。就难度而言，我发现这两个问题都类似于 Leetcode 的简单问题。像第 1 级一样，这些问题需要对内置数据类型及其方法有扎实的理解。

如果你不熟悉 Foobar 挑战，我推荐你阅读我以前的文章，这篇文章提供了 1 级问题的概述和分解。

[](/google-foobar-challenge-level-1-3487bb252780) [## 谷歌足球挑战赛:第一关

### 对秘密编码挑战和问题分解的介绍

towardsdatascience.com](/google-foobar-challenge-level-1-3487bb252780) 

# 问题和概念📚

## 警告——⛔️前方剧透

下面，我将问题分解，解释我的思考过程。我也提供解决方案。不过， ***我强烈推荐你先尝试一下问题*** 。挑战最好的部分是解决一个难以捉摸的问题的惊喜和满足感。

我考虑过不发布解决方案，只解释基本概念。然而，编码的一部分是学习如何排除故障，并确定代码失败的地方。因此，我决定发布解决方案，这样如果你陷入困境，你就可以准确地看到你的逻辑分歧在哪里。

## 第二级:问题 1 ⭐️

> 电梯维修
> ====================
> 
> 你被分配了繁重的电梯维护任务——啊！除了所有的电梯文档已经在文件柜的底部杂乱无章的堆了好几年，而且你甚至不知道你将要工作的电梯版本号，这不会太糟糕。电梯版本由一系列数字表示，分为主要、次要和修订整数。电梯的新版本增加了主要编号，例如 1、2、3 等等。当新的特征被添加到电梯中而不是一个完整的新版本时，名为“次要”的第二个数字可以用于表示那些新添加的特征，例如 1.0、1.1、1.2 等。小的修复或维护工作可以用第三个数字“修订”来表示，例如 1.1.1、1.1.2、1.2.0 等等。数字 0 可以用作电梯预发布版本的主要版本，例如 0.1、0.5、0.9、2 等(Lambda 指挥官总是小心翼翼地测试她的新技术，以她的忠实追随者为对象！).给定一个用字符串表示的电梯版本列表，写一个函数解(l ),返回同样的列表，按主版本号、次版本号和修订号升序排序，这样你就可以识别当前的电梯版本。列表 l 中的版本将总是包含主要版本号，但是次要版本号和修订版本号是可选的。如果版本包含修订号，那么它也将有一个次版本号。
> 例如，给定列表 l 为["1.1.2 "，" 1.0 "，" 1.3.3 "，" 1.0.12 "，" 1.0.2"]，函数 solution(l)将返回列表["1.0 "，" 1.0.2 "，" 1.0.12 "，" 1.1.2 "，" 1.3.3"]。如果两个或多个版本相同，但其中一个版本包含的数字比其他版本多，则这些版本必须根据它们包含的数字升序排列，例如["1 "、" 1.0 "、" 1.0.0"]。列表 l 中的元素数量至少为 1，不会超过 100。
> 
> 测试用例
> = = = = = = = = = = =
> 你的代码应该通过下面的测试用例。
> 注意，它也可以针对这里没有显示的隐藏测试用例运行。
> - Python 案例-
> 输入:
> solution.solution(["1.11 "，" 2.0.0 "，" 1.2 "，" 2 "，" 0.1 "，" 1.2.1 "，" 1.1.1 "，" 2.0"])
> 输出:
> 0.1，1.1.1，1.2，1.2.1，1.11，2，2.0，2.0
> 
> 输入:
> solution.solution(["1.1.2 "，" 1.0 "，" 1.3.3 "，" 1.0.12 "，" 1.0.2"])
> 输出:
> 1.0，1.0.2，1.0.12，1.1.2，1.3.3

输入是字符串列表，目标是根据标准对它们进行排序。`list`类型有一个`sort`方法，通过执行`<`比较对列表中的项目进行排序。对于类似于`l`的字符串列表，`sort`将查看每个字符串的第一个数字。如果两个字符串有相同的第一个数字，那么比较将使用下一个数字，依此类推。因此，不同长度的字符串*之间的比较可能*不正确。例如，`sort`会将`“1.12”`放在`“1.2”`之前。字符串具有相同的第一个数字，因此比较将使用下一个数字。由于`“1” < “2”`，即使 2 小于 12，`“1.12”`也在`“1.2”`之前。

如果这些是整数而不是字符串，`sort`将使用整数进行比较，而不是逐位比较。然而，将每个条目转换为`int`对于带有修订号的条目不起作用。`sort`需要将每个组成部分作为一个整数与其对应部分进行比较。将每个项目转换为`int`类型的`list`就可以实现这一点。

如下所示，嵌套列表理解创建了`answer`，一个整数列表的列表。`str` type 有一个内置的方法`split`，它给定一个分隔符，将一个字符串分割成子字符串。这里，`‘.’`是分隔符。`split`输出子字符串列表，`int`函数将它们转换成整数。

对于列表的列表，`sort`将根据每个列表中的第一个元素对项目进行排序。如果元素相等，`sort`检查下一个元素。`answer.sort()`就地排序`answer`。

最后，将列表列表转换为字符串列表，即预期的返回值。`str.join`方法获取一系列字符串并将它们连接起来。`‘.’.join`将连接字符串，以便`‘.’` 分隔输出字符串中的每一项。

这个问题需要字符串方法、`list.sort`和列表构造的知识。

## 级别 2:问题 2 ⭐️

> 途中敬礼
> ===================
> 
> Lambda 指挥官热爱效率，讨厌任何浪费时间的事情。毕竟，她是一只忙碌的羔羊！她慷慨地奖励那些找出效率低下的根源并想出消除它们的方法的追随者。你已经发现了一个这样的源头，你认为解决它将有助于你建立晋升所需的声誉。
> 
> 每当指挥官的员工在大厅里擦肩而过时，他们每个人都必须停下来向对方敬礼——一次一个人——然后再继续他们的道路。一个敬礼有五秒钟长，所以每次交换敬礼用了整整十秒钟(Lambda 司令的敬礼有点，呃，牵扯)。你认为通过取消敬礼要求，你可以每天节省几个小时的员工时间。但是首先，你需要让她知道问题有多严重。
> 
> 写一个程序，计算在一次典型的走廊行走中交换了多少次敬礼。大厅由一根弦代表。比如:“— ->-> -”
> 
> 每个走廊字符串将包含三种不同类型的字符: '>'，向右走的员工；
> 
> Write a function answer(s) which takes a string representing employees walking along a hallway and returns the number of times the employees will salute. s will contain at least 1 and at most 100 characters, each one of -, >或<./>
> 
> Sample output:
> 
> Test cases
> =========
> 
> 输入:
> 
> s = " >—
> 
> Output:
> 
> 2
> 
> Inputs:
> 
> s = “<<>> < "
> 
> 输出:
> 
> 4

在我看来，这是迄今为止最简单的问题！对于每一个右行走者，计算他/她经过的左行走者的数量。由于每个敬礼都涉及到两个人，所以将经过的左边步行者的数量乘以 2，并将该数量加到答案中。

`‘-’`字符与答案无关。删除`‘-’`字符会缩短字符串，从而缩小搜索空间。`enumerate`功能输出`no_dash`中每个字符的索引和字符。如果角色是`‘>’`(一个右行走者)，那么创建子串`people_in_front`。`people_in_front`每一个左行者代表一个敬礼，涉及 2 个人。`answer`是敬礼的总人数。

这个问题测试字符串、子字符串和循环的知识。

# 结论📌

我计划在以后的文章中继续描述我的 Foobar 之旅，并详细说明我是如何解决这些问题的。关注我，阅读更多关于挑战的信息。此外，欢迎所有反馈。我总是渴望学习新的或更好的做事方法。请随时留下您的评论或联系我 katyhagerty19@gmail.com。

[](https://medium.com/@katyhagerty19/membership) [## 加入我的介绍链接媒体-凯蒂哈格蒂

### 阅读凯蒂·哈格蒂(以及媒体上成千上万的其他作家)的每一个故事。您的会员费直接支持…

medium.com](https://medium.com/@katyhagerty19/membership)