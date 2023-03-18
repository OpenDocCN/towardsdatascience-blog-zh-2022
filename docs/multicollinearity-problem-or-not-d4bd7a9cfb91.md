# 多重共线性:有问题吗？

> 原文：<https://towardsdatascience.com/multicollinearity-problem-or-not-d4bd7a9cfb91>

## 多重共线性及其如何影响多元回归模型的简要指南

![](img/1878bb42041106b22c58952dd84ddda3.png)

凯莉·德·阿桂在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上的照片

您可能在大学统计学课程中模糊地记得多重共线性是多重回归模型的一个问题。但是多重共线性到底有多成问题*？嗯，就像统计学中的许多主题一样，答案并不完全简单，这取决于你想用你的模型做什么。*

在这篇文章中，我将逐步介绍多重共线性在多重回归模型中面临的一些挑战，并提供一些直觉来解释为什么它会有问题。

## **共线性和多重共线性**

在继续之前，最好先明确什么是共线性和多重共线性。幸运的是，如果你熟悉回归，这些概念非常简单。

*如果*两个*解释变量之间存在线性关联，则存在共线性*。这意味着，对于所有观察值 *i* ，以下情况成立:

![](img/6139bb7bb11e8f24ce70b3c6fe09cb02.png)

说明共线性的方程(图片由作者提供。)

*多重共线性*是这一思想的延伸，如果*两个以上的*解释变量之间存在线性关联，则存在多重共线性。例如，在您的设计矩阵中，一个变量可能与另外两个变量线性相关，如下所示:

![](img/20202217158ab526e1f2cb3175a05676.png)

说明多重共线性的方程(图片由作者提供)。

严格地说，多重共线性不是相关性:相反，它意味着几个解释变量之间存在线性相关性。这是一个微妙的点——但也是重要的一点——两个例子都说明了预测者之间的确定性关联。这意味着可以对一个变量进行简单的转换来计算另一个变量的精确值。如果这是可能的，那么我们说我们有*完美共线性*或*完美多重共线性*。

在拟合多元回归模型时，我们需要避免的正是这一点。具体来说，多元回归的一个关键假设是不存在完美的多重共线性。所以，我们现在知道什么是完美多重共线性，但是*为什么*是个问题？

## **打破行列**

简而言之，问题在于*冗余*，因为完美的多重共线变量提供了相同的信息。

例如，考虑*虚拟变量陷阱。*假设我们有一个设计矩阵，包括两个虚拟编码的{0，1}列。在第一列中，对应于“是”回答的行被赋予值 1。然而，在第二列中，具有“否”响应的行被赋予值 1。在这个例子中，“否”列是完全多余的，因为它可以从“是”列计算出来(“否”= 1 —“是”)。因此，我们不需要单独的列来编码“否”响应，因为“是”列中的零提供了相同的信息。

让我们通过考虑下面的矩阵来进一步扩展冗余的概念:

![](img/02676a86c5567a3bccda939e9d9522ef.png)

矩阵示例(图片由作者提供)。

这里，前两列是线性独立的；然而，*第三个*实际上是第一列和第二列的线性组合(第三列是前两列的总和)。这意味着，如果第一列和第三列，或者第二列和第三列是已知的，那么剩下的一列总是可以计算出来的。这里的结论是，最多只能有两个栏目做出真正独立的贡献——第三个栏目总是多余的。

冗余的下游效应是它使得模型参数的估计不可能。在解释为什么快速定义*矩矩阵*会有用之前:

![](img/243c5179c31d7c62739059bd4a68f61d.png)

***矩矩阵*** (图片由作者提供)。

关键的是，要导出普通最小二乘(OLS)估计器 ***r*** 必须是*可逆的*，这意味着矩阵必须具有*满秩*。如果矩阵是*秩亏的*，那么 OLS 估计器不存在，因为矩阵不能求逆。

好吧，这意味着什么？

不涉及太多细节，矩阵的[秩](https://en.wikipedia.org/wiki/Rank_(linear_algebra))是其列所跨越的向量空间的维数。解析这个定义最简单的方法如下:如果你的设计矩阵包含 *k* 个独立解释变量，那么*rank(****r****)*应该等于 *k* 。完美多重共线性的效果是将 ***r*** 的秩降低到小于设计矩阵中最大列数的某个值。那么，上面的矩阵 **A** 只有秩 2，并且是秩亏的。

直觉上，如果你将 k 条信息放入模型，你会希望每条信息都做出有用的贡献。每个变量都应该有自己的权重。相反，如果你有一个完全依赖于另一个变量的变量，那么它不会贡献任何有用的东西，这将导致*退化。*

## ***不完美的联想***

*到目前为止，我们一直在讨论变量完全多重共线的最坏情况。然而，在现实世界中，你很少会遇到这个问题。更现实的情况是，你会遇到两个或更多变量之间存在近似线性关联的情况。在这种情况下，线性关联不是确定性的，而是随机的。这可以通过重写上面的等式并引入误差项来描述:*

*![](img/1049a3d8edd7123aaa2f319307ff7c00.png)*

*随机多重共线性(图片由作者提供)。*

*这种情况更易于管理，并且不一定导致 ***r*** 的退化。但是，如果误差项很小，变量之间的关联可能*几乎*完全多重共线。在这种情况下，尽管*rank(****r****)= k，*模型拟合可能会变得计算不稳定，并产生表现相当不稳定的系数。例如，数据中相当小的变化都会对系数估计值产生巨大影响，从而降低其统计可靠性。*

## ***充气模型***

*好的，如果你想对你的解释变量进行统计推断，那么随机多重共线性会带来一些障碍。具体来说，它的作用是*增大*估计系数周围的标准误差，这可能导致在存在真实效应时无法拒绝零假设(第二类误差)。幸运的是，统计学家已经来帮忙了，并且创造了一些非常有用的工具来帮助诊断多重共线性。*

*其中一个工具是*方差膨胀因子* (VIF)，它量化了多重回归模型中多重共线性的严重程度。从功能上来说，当存在共线性时，它测量估计系数方差的增加。所以，对于协变量 *j，*VIF 定义如下:*

*![](img/44c06793b223c8af3f77d4965956649e.png)*

*方差膨胀因子(图片由作者提供)。*

*这里，决定系数是从协变量 *j* 对剩余 *k — 1* 变量的回归中得出的。*

*对 VIF 的解释也相当简单。如果 VIF 接近 1，这意味着协变量 *j* 与所有其他变量线性无关。大于 1 的值表示某种程度的多重共线性，而介于 1 和 5 之间的值被认为表现出轻度到中度的多重共线性。这些变量可以留在模型中，尽管在解释它们的系数时需要小心。我很快就会谈到这一点。如果 VIF 大于 5，这表明存在中度到高度的多重共线性，您可能需要考虑不考虑这些变量。然而，如果 VIF 是 10，你可能有合理的理由抛弃这个变量。*

*VIF 的一个非常好的属性是它的平方根指示了系数标准误差的增加。例如，如果一个变量的 VIF 为 4，那么它的标准误差将是与所有其他预测值零相关时的 2 倍。*

*好了，现在提醒一下:如果你*决定保留 VIF 为 1 的变量，那么估计系数的大小将不再提供完全精确的影响度量。回想一下，变量 *j* 的回归系数反映了在保持所有其他变量不变的情况下，仅 *j* 、*的每单位增加量的预期响应变化。*如果解释变量 *j* 和其他几个变量之间存在关联，这种解释就不成立，因为 *j* 的任何变化都不会独立影响响应变量。当然，这种情况的程度取决于 VIF 有多高，但这肯定是需要注意的。**

## ***设计问题***

*到目前为止，我们已经探讨了多重共线性的两个颇成问题的方面:*

*1) *完美多重共线性:*定义协变量之间的确定性关系，产生退化矩矩阵，从而无法通过 OLS 进行估计；和*

*2) *随机多重共线性:*协变量近似线性相关，但矩矩阵的秩不受影响。在解释模型系数和关于它们的统计推断时，这确实会产生一些令人头痛的问题，尤其是当误差项很小时。*

*不过，你会注意到，这些问题只涉及到对*预测者*的计算——没有提到模型本身。这是因为多重共线性*只影响设计矩阵*而不影响模型的整体拟合。*

*所以…..问题，还是没有？嗯，就像我开头说的，看情况。*

*如果您感兴趣的只是解释变量的*集合*对响应变量的预测程度，那么即使存在多重共线性，模型仍会产生有效的结果。然而，如果你想对*个体预测因子* s 做出具体声明，那么多重共线性就更是个问题；但是，如果你意识到了这一点，你可以采取行动来减轻它的影响，在以后的文章中，我将概述这些行动是什么。*

*同时，我希望你在这篇文章中找到一些有用的东西。如果您有任何问题、想法或反馈，请随时给我留言。*

*如果你喜欢这篇文章，并且想保持更新，那么请考虑在 Medium 上关注我。这将确保你不会错过新的内容。如果你更喜欢的话，你也可以在 LinkedIn 和 Twitter 上关注我😉*