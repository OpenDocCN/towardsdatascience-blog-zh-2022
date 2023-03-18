# 如何设置成功的 A/B 测试

> 原文：<https://towardsdatascience.com/how-to-set-up-a-b-tests-for-success-9ad9a80541b7>

## 帮助非数据专业人员在没有数据科学家的情况下自信地运行测试

![](img/f7a7b571e8b4654fecd806e9d0bb1270.png)

约翰·施诺布里奇在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上的照片

我们，数据科学家，为了精通假设检验和统计学，进行了大量的研究和长时间的工作。然而，数据科学家无法控制其他团队决定运行的每个 A/B 测试。例如，脸书和 Nextdoor 等社交媒体公司的增长型营销团队在没有数据科学家监督实施的情况下不断进行 A/B 测试。这有好处也有坏处:

*   **利:**营销团队变得独立，而数据科学家可以专注于其他需要技术投入的项目。
*   反对意见:如果没有专家对 A/B 测试的意见，成长型营销团队可能会浪费资源。

## 你该怎么办？

教育你的利益相关者是相对简单的，它会对每个人的工作产生重大影响。教育步骤的想法是通过解释简单的概念和分享最佳实践来提高其他团队的标准。在运行 A/B 测试之前，创建一个演示文稿，介绍每个非数据涉众应该知道的内容。这样做的话，你将会消除几十个简单的问题，这些问题通常会扰乱你作为数据科学家的工作，但是与其他团队的测试相关。这是你为成功建立 A/B 所能做的第一件事——即使这不是你的测试。

## 成功的 A/B 测试设置

这是我见过的非数据专业人士挠头的最常见的概念。因公司而异。

1.  **定义一个强有力的假设:**

假设是对两个或多个变量之间关系的预测。你的工作是证明你的预测是真的还是假的。下面是我创作的两个例子:

*   *60 岁的英国男性每天吃一个苹果，比那些不吃苹果的人去看心脏病医生的次数少。*
*   *在纽约市，通过应用程序加入 Medium 的 25-35 岁用户在第一周做出的贡献比通过网络加入的用户更多。此外，贡献被定义为至少一次鼓掌或一个帖子。*

上面的假设有一些共同点，下面列出了我喜欢称之为**的有效假设清单**:

*   定义成功的单一且可衡量的标准。
*   预测关系和结果。
*   简洁明了，避免啰嗦。
*   清晰，没有模糊或者隐含的意思。
*   与问题相关且具体。
*   一个在测试开始日期之前定义好的。

所以，不管样本大小如何，除非你的假设是明确的，否则结果可能会误导。换句话说，如果假设事先没有很好地定义，数据就不太可能代表你所期望的。

**2。置信区间至少应为 95%**

置信水平是指如果您再次运行测试或以相同方式对总体进行重新采样，您预期看到相同的赢/输结果的时间百分比。还有，科学标准是 95%的置信区间。虽然 95%的区间在学术界引起了争议，但这是任何非数据专业人士都应该在测试中使用的默认设置。

将置信区间增加到 99%并使您的测试结果更加可靠是可能的，但是 95%足以获得统计上显著的结果。在某些情况下，您会发现 90%是标准设置。然而，不推荐 95%以下的置信区间**。**

**如果你的非数据利益相关者使用在线计算器，请小心。一般来说，易于使用的计算器不会指示使用了哪种测试(*即*单尾或双尾)。我很欣赏用户可以假设双尾测试，但我们不能保证这是事实。此外，双尾检验并不总是每个假设的最佳选择——这就是为什么我的第一个主题是关于假设的。**

**![](img/45498b70f08327617158fd7063f39658.png)**

**卢克·切瑟在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄的照片**

****3-我可以提前结束测试吗？****

**直截了当的回答是**不**。有几个原因你应该记住:**

*   **置信区间根据样本大小而变化。置信区间**的宽度随着样本量的增加而减小**。因此，在运行您的测试之前，确认需要多少天才能达到预测的样本量。如果这段时间太长，你不能等待，你可以通过使它更具体来检查你的目标样本。**
*   **季节性和外部事件会影响结果。但是，要看行业，产品或者服务。一些例子包括政治、自然灾害、假期和学校日历。**
*   **它会增加假阳性，也称为 I 型错误。换句话说，成功的案例会比应该的多。**

**那么，你能做什么？请看一下**顺序测试**，它使您能够在 A/B 测试期间通过顺序监控数据的累积来做出决定。顺序测试使用可选的停止规则(错误花费函数)来保证总体 I 型错误率。**

## **结论**

**不是每个团队都有数据科学家监督 A/B 测试。因此，请记住，建立一个明确的假设，确保 95%的置信区间，不要过早结束测试，可以很容易地提高你的结果。如果你需要的话，可以使用顺序测试来代替长时间的测试。但是，请务必通过共享这些和其他默认参数来指导非数据专业人员设置 A/B 测试。**

****想获得 Medium 文章的全部访问权限并支持我的工作？使用以下链接订阅:****

**[](https://boemer.medium.com/membership) [## 加入我的介绍链接-雷纳托 Boemer 媒体

### 阅读雷纳托·博默(以及媒体上成千上万的其他作家)的每一个故事。您的会员费直接支持…

boemer.medium.com](https://boemer.medium.com/membership)** 

****感谢阅读。这里有一些你可能会喜欢的文章:****

**[](/switching-career-to-data-science-in-your-30s-6122e51a18a3) [## 30 多岁转行做数据科学。

### 不要纠结于已经有答案的问题。以下是我希望在开始职业生涯前知道的三件事…

towardsdatascience.com](/switching-career-to-data-science-in-your-30s-6122e51a18a3) [](/5-tips-to-get-your-first-data-scientist-job-d8e5afd5a59b) [## 获得第一份数据科学家工作的 5 个技巧

### 我在臭名昭著的求职阶段学到的关键东西

towardsdatascience.com](/5-tips-to-get-your-first-data-scientist-job-d8e5afd5a59b)**