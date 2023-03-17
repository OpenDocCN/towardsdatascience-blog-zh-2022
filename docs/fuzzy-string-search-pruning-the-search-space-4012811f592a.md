# 模糊字符串搜索:修剪搜索空间

> 原文：<https://towardsdatascience.com/fuzzy-string-search-pruning-the-search-space-4012811f592a>

# **模糊字符串搜索:修剪搜索空间**

## 拼音键，区分位置的哈希

![](img/68a0b46e648d7ebfd2f563a1210f18f7.png)

照片由[屋大维丹](https://unsplash.com/@octadan?utm_source=medium&utm_medium=referral)在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)

这是在给定的字符串字典中寻找一个字符串的近似匹配的问题。

让我们看一个例子。我们想在一个干净的人名字典中搜索 *Jonahtan* 。我们真正的意思是，在考虑到拼写错误或其他变化后，我们希望找到近似的匹配。我们所说的“其他变体”是什么意思？在我们的示例中，我们真正想要找到的是字典中的名字，这些名字是隐含在输入字符串中的名字的似乎合理的替代表达式。这不仅包括拼写错误，还包括昵称。也可以包括*先生*、*小姐*、…

搜索可能会在字典中产生与 *Jonahtan* 匹配的 *Jonathan* 。我们知道后者是一个拼写错误，并在这个过程中找到它的正确拼写。

**一般方法**

解决这个问题的常见方法是调用模糊匹配器作为黑盒方法。模糊匹配器输入两个字符串，并计算它们成为同一实体的表达式的可能性。模糊匹配器在[1]中有详细介绍。

一种简单的方法是获取输入字符串，将其与字典中的每个字符串进行模糊匹配，将得分最高的匹配排列在列表的顶部，然后以某种方式决定哪些排名最高的匹配(如果有)是输入字符串的足够好的匹配。

当字典很大时，这种方法会很慢。即使它不是很慢，我们也可能有严格的运行时间要求，比如实时查找匹配。

**修剪搜索空间**

在这篇文章中，我们关注的是修剪搜索空间以减少模糊匹配的问题。当然，修剪取决于输入字符串。

我们讨论一些剪枝方法，特别是那些基于语音键和基于位置敏感散列的方法。我们用一个运行中的例子来说明它们:在名字的(大)字典中查找字符串的模糊匹配。

**有哪些取舍？**

目的是在不丢失任何真实匹配的情况下，尽可能地减少空间。因为这个理想可能无法保证，在实践中，所寻求的是性能(在运行时间的意义上使用)和召回率(修剪后找到的真实匹配的百分比)的适当折衷。虽然精度不会显式地出现在权衡中，但它可以间接出现。这是因为较低的精度潜在地转化为更多的结果需要处理，即修剪不充分。有鉴于此，用一个合适的量化修剪的指标来代替“性能”是有吸引力的。最终影响性能的是结果列表的大小。

**音标键**

从字符串派生的音标试图保留字符串的发音。想想*约瑟夫*和*约瑟夫*。它们听起来一样。所以它们应该有相同的音标。

当我们寻找发音相似的字符串时，拼音键有助于缩减搜索空间。我们不是寻找发音相似的字符串，而是查找所有其语音关键字与查询字符串相同的字符串。

生成语音键的两种流行方法是 Soundex 和 Metaphone。变音被广泛认为更好。所以我们这里就重点说一下。

下面是几对具有相同变音键的名字。这摘自[1]。

```
Steven, Stephen → STFN, John, Jon → JN, Cathy, Kathy → K0
```

这表明，在我们的用例中，通过变音键进行修剪将会工作得很好。寻找发音相似的名字。

当然，会有假阳性。例如， *Jack* 和 *Jake* 有相同的变音键， *JK* 。这在修剪过程中不必担心，因为过滤掉误报是模糊匹配器的责任。如果假阳性率如此之高以至于修剪无效，这将是一个问题。幸运的是，变音键不是这样的。

很好，使用合适的语音键可以有效地在字典中找到听起来像输入字符串的名字。但通常这不是我们想要找到的全部。例如，我们还会发现名字中有拼写错误。考虑*Ri****ch****ard*vs*Ri****HC****ard*。显然，这些应该是匹配的，因为这种差异可以用一种常见的错误来解释:相邻字母的错位。然而，他们不健全的名字。事实上，我们看到它们的变音键是不同的，分别是 RXRT 和 RKRT。这两个关键字的不同之处在于两个名称中粗体区域的发音方式不同。

因此，即使在我们的例子中，使用语音键进行修剪也是不够的。

**哈希键**

从讨论到这一点，我们可以抽象出剪枝问题如下。在给定的论域(在我们的例子中，是人名)上定义一个散列函数，它具有以下属性:

1.  *应该充分修剪搜索空间*。虽然这是一个非正式的描述，但很容易根据经验对其进行评估或将其形式化。
2.  *它应该有接近 100%的召回率*。也就是说，被视为匹配的两个名字字符串几乎肯定应该具有相同的哈希值。

语音键是特殊类型的散列函数。更一般地扩展到散列函数，打开了大门。

好吧，这一切都很好，但我们仍然必须弄清楚，作为一个特殊的情况，如何在名字字符串中出现换位错误的情况下进行修剪。

我们接下来讨论的技术在这方面提供了诱人的可能性。

**区分位置哈希**

考虑我们的特殊要求。

```
Two first-name strings deemed a match should almost certainly have the same hash value.
```

现在考虑以下内容，位置敏感散列的定义性断言

```
Map items to hashes so that similar items have the same hash value with high probability.
```

有匹配的吗？(双关。)是的。如下所述。

```
Two first-name strings deemed a match ⇐⇒ similar items
almost certainly ⇐⇒ high probability
```

太好了。我们仍然没有解决我们问题的具体方案。再坚持一会儿。

**位采样**

考虑长度为 *n* 的二元向量。选择特定尺寸 *i* 。对于一个 *n* 位向量 **x** ，定义 h _*I*(**x**)=*x*_ I，这个 hash 函数只是简单的选出 **x** 的 *i* 位。

这一族哈希函数 *h* _1、…、 *h* _ *n* 有一个有趣的(也是吸引人的)性质，对于任意两个二元向量 **x** 和 **y** ，如果我们选择一个随机哈希函数 *h* _i，越相似的 **x** 和 **y** 越有可能是 *h 【T43*

好吧，那不透明。我们来分解一下。首先，我们在这里如何定义相似性？我们将它定义为两个向量具有相同值的 *n* 位的分数。因此 **110** 1 和 **110** 0 具有相似性，因为两个向量中的 4 位中的 3 位具有相同的值。(这些位用粗体标识。)

接下来，我们用极端的例子来建立直觉。考虑 **x** = **y** =1001。显然对于 1 到 4 中的每一个 *i* 来说 *h* _ *i* ( **x** )等于*h*_*I*(**y**)。这只是说，在两个向量相同的极端情况下，该属性将保持“极端”，这意味着无论选择哪个哈希函数，它在两个向量中的值都必然相同。

类似地，我们可以看到，当 **x** 和 **y** 相距最大时，例如 1001 对 0110，每个散列函数必然具有不同的值。

现在考虑“中间某处”的情况。为了便于说明，以这样的方式排列尺寸，即 **x** 和 **y** 的第一个 *d* 位是相同的，其余的是不同的。下面是一个例子

```
**1011111***01001* **1011111***10110*
```

这里 *n* = 12， *d* = 7，相同的位用粗体表示，不同的用斜体表示。

现在让我们从 1 到 12 中随机选择尺寸 *i* 。 *x* _ *i* 和 *y* _ *i* 具有相同值的概率为 *d* / *n* ，这正好是 **x** 和 **y** 的相似度值(我们已经定义过了)。

**使用比特采样来修剪搜索空间**

有了目前为止我们对比特采样的了解，让我们用它来修剪搜索空间。

首先，我们想要更精确地定义我们的修剪问题。设 *D* 表示一组长度为 *n* 的二元向量， **x** 表示一个同类的单一向量。我们希望使用上一节定义的相似性函数，在 *D* 中高效地找到与 **x** 最相似的向量。

上一节的内容建议使用以下方式使用位采样来定义散列键。这里 **y** 是一个长度为 n 的二元向量。

```
key(**y**)
  Sample i uniformly at random from {1, 2, …, n}
  return (i,y_i)
```

注意`key(.)`是一个随机程序。在每个调用`key(.)`中，随机选取其位要被采样的维度。

使用这种键控机制，我们将 D 中的每个向量 **d** 散列到它的键`key(**d**)`。

现在我们准备在任何新的输入向量 **x** 的 *D* 中寻找邻居。

```
neighbors(**x**)
  key_of_x = key(x)
  Return all vectors in D whose key is key_of_x
```

**这种方法效果如何？让我们来做一个例子。说 *n* = 2 而 *D* 包含 11。考虑调用`neighbors(11)`。它会找到 11 吗？不一定。为什么不呢？因为 D 中的 11 是索引在键( *i* ，1)下的。随后，在调用`neighbors(11)`中，在键( *j* ，1)下查找。鉴于 *i* 和 j 都在{1，2}中，由于密钥(.)功能。**

哦，那可不好。我们能做什么？

**查找期间的多个键**

在查找过程中，我们可以生成多个键，并聚合所有与它们相关的向量。这潜在地增加了期望的向量在返回的结果集中的可能性。我们付出的一个代价是在查找过程中花费更多的时间。我们付出的一个潜在的更大代价是，结果的数量可能会大幅增加。在这种情况下，我们可能需要花更多的时间对它们进行后处理。这两点以后再详细讲。

下面是一个明智的方法。定义一个函数 *multi_key* ( **y** ， *m* )，该函数调用*key*(**y**)*m*次，收集查找每个 key 得到的向量，并将其作为一个集合返回。

使用*键* ( **y** )索引矢量。使用 *multi_key* ( **y** ， *m* )查找其邻居。

我们能期望这种方法有多有效？m*m*应该是什么？让我们从*回忆*的角度来看这个问题，我们将它定义为一个索引向量在后续查找自身的结果集中的概率。凭直觉，回忆应该随着 *m* 的增加而增加。(查找时间也是如此。)

对于任何固定的 *n* ，我们可以很容易地将召回量化为 m 的函数。让 *i* 表示索引向量 **y** 时使用的维度。设 *j* 表示在任意一个后续调用*键* ( **y** )期间采样的尺寸。 *i* 和 *j* 不同的概率是( *n* -1)/ *n* ，因为 *j* 有 *n* 个可能的值，除了其中一个之外，其余的都与 *i* 不同。尝试查找 **y** 时，调用*键* ( **y** )的 *m* 中的每个 *j* 不同的概率为(*n*-1)/*n*)^*m*)。至少有一个 *j* 等于 *i* 的概率，即回忆，是这样的

```
1 — ((*n*-1)/*n*)^*m*                                                 (R1)
```

对于 *n* = 20，让我们计算各种 *m* 使用(R1)的召回。

```
m       1      2      10   20    50     100
recall 0.05  0.0975  0.4  0.64  0.92   0.994
```

这表明，为了实现接近 100%的召回率，m 需要比 n *大得多。这是可信的。带有替换的随机采样本质上有点低效，因为同一个密钥可能被采样多次。好吧，与其用 *multi_key* ( **y** ， *m* )，不如干脆把 20 个键都一一列举出来。*

**查找 *n 个*键**

好了，现在我们知道了查找 n 个*键就足以获得 100%的回忆。*

这样够好了吗？没那么快。我们还需要考虑结果集的大小，因为当查找这么多键时，结果集可能会很大。

让我们来分析下面的场景。假设 *D* 包含 1^ *n* ，我们随后对其进行查找。考虑一个向量 **y** 在 *D* 中，其中有 *d* 个。现在考虑 neighbors(1^ *n* 的结果集。在枚举 1^ *n* 的邻居时，我们将查找，对于 1 中的每个 *i* 到 *n* ，索引在值 1 下的 *D* 中的向量。然后把它们都结合起来。

如果 **y** 被索引到 *i* 上，使得 *y* _ *i* 为 1，则它将位于 neighbors(1^ *n* 。这种情况发生的概率是 *d* / *n* 。这是因为在 *n* 中有 *d* 个值为 1 的位，索引从 *n* 个位中随机选择一个位进行索引。

说 *D* 包含 *m* _ *d* 这样的向量。我们可以期待他们中的*m*_*d***d*/*n*进入*邻居* (1^ *n* )的结果集。

现在假设 *d* 很小，比如说 4，而 *n* 大得多，比如说 20。此外，假设 *D* 包含许多包含 *d* 个向量的向量，即 *m* _ *d* 很大。这似乎是合理的，因为宇宙中有“20 选 4”这样的向量。由于 *d* 很小，相对于 1^ *n* 来说，可以合理地预期大部分(如果不是全部)都是假阳性。因为 m*m*_*d*很大，所以很多这样的误报会出现在结果集中。

我们上面的分析适用于 1^ *n* 。可以概括一下吗？让我们用任何一个 *n* 位向量 **x** 来代替 1^ *n* 。设 D 中的 **y** 与 **x** 有共同的 *d* 位，即相似度 *S* ( **x** ， **y** )等于 *d* / *n* 。和以前一样， **y** 到达 *neigbors* ( **x** )结果集的概率是 *d* / *n* 。所以如果有 *m* _ *d* 这样的向量 **y** ，我们可以像之前一样，期待*m*_*d***d*/*n*能够到达结果集。由于 *d* 小，这些相对于 **x** 很可能是误报。如果 *m* _ *d* 很大，那么结果集中就有很多。

总而言之，当 *D* 包含许多与 **x** 有轻微相似性的向量时，在任意向量 **x** 上查找所有 *n* 维确实可以返回许多结果。这是一个问题，当这些结果大部分是假阳性时，这似乎是合理的。

那么我们还能尝试什么呢？

**无替换样品**

像以前一样，让我们对一个维度进行 m 次采样。与之前不同，让我们在不更换的情况下对*进行采样。这相当于从 *n* 个维度中随机选择一个 *m* 维度的子集。*

这能给我们带来什么？更加灵活。将 *m* 设置为 *n* 给出了“在所有尺寸上查找”的情况。选择小于 n 的 m 让我们在返回结果集的大小上权衡召回。

**回忆作为*m*的函数**

考虑一个 *D* 中的 **y** ，我们在它被索引后的某个时间查找它。查找到的结果集包含 **y** 的概率是多少？这是 *m* / *n* ，在查找过程中随机选择的 *m* 维度包括 **y** 被索引的维度的概率。

这告诉我们什么？召回率随着 *m* 线性下降。当然，你只会想要降低 *m* ，也就是说，付出减少召回的代价，除非你有所收获，特别是搜索结果的数量也大幅下降。接下来我们来分析一下这个。

**结果集的预期大小**

对于这个场景，我们将重复上一节所做的分析。为了保持独立，我们将从头开始拼写所有内容。与先前分析不同的部分用粗体表示。

假设 *D* 包含 1^ *n* ，我们随后对其进行查找。考虑一个向量 **y** 在 *D* 中，其中有 *d* 个 1。现在考虑 neighbors(1^ *n* 的结果集。在枚举 1^ *n* 的邻居时，我们将查找从 *n* 位中随机采样(替换)的 *m* 位中的每一位的**，在采样位的值 1 下索引 *D* 中的向量。然后把它们都结合起来。**

如果 **y** 被索引到位 *i* 上，使得 *y* _ *i* 是 1 **并且 *i* 是在 neighbors(1^ *n* )** 中查找期间采样的 *m* 位之一， **y** 将在*邻居*(t67)中 *y* _ *i* 为 1 的概率为 *d* / *n* 。 ***i* 是在 neighbors(1^ *n* 中查找期间采样的 *m* 位之一的概率是 *m* / *n* 。所以组合概率是(*d*/*n*)*(*m*/*n*)***。*

综上所述，通过在计算*邻居* (1^ *n* )所涉及的查找过程中对 *m* 位进行替换采样，召回 1^ *n* 的概率为 *m* / *n* ，结果集的预期大小为*m*_*d**(*d*/*n*)*(

***多键下的索引***

*到目前为止，我们只在查找过程中使用多个键。如果我们在索引期间也使用这种机制会怎么样？更具体地，对于在 1 和 *n* 之间的整数值参数 *m* I，当索引一个 **x** 时，我们采样 *m* I 比特，替换从 1 到 *n* 并且在每个比特下索引 **x** 。*

*使用与之前相同的查找机制，召回概率将随着 *m* I 的增加而增加。结果集的预期大小也是如此。*

***收紧查找***

*为了试图抵消随着 *m* I 的增加而增加的结果集的预期大小，我们可以引入一个参数，称之为 *k* L，以使查找条件更加严格。*

*至此，如果任何特定于位的查找找到一个向量，它就包含在结果集中。有了参数 *k* L，只有在特定于位的查找中至少有 *k* L 找到它时，我们才能将它包含在结果集中。*

*好吧，这确实使我们的聚合逻辑变得复杂了，现在需要包括一些过滤。我们不能只是累加我们找到的所有向量，一路去重复它们。我们还必须确保找到的向量至少在特定于位的结果集中。*

*撇开聚合和过滤逻辑的复杂性不谈，直觉上，这种机制似乎有可能让我们对权衡进行更多的控制。*

*在这篇文章中，我们就说到这里。现在用 *n* 、 *d* 、 *m* 、 *m* I、 *k* L 来参数化的这种情况，量化分析起来令人望而生畏。*

***从比特采样到多项式采样***

*位采样机制扩展到定义为*D*1 X*D*2 X…X*Dn*的论域。这里，每个“尺寸”i 都有一组有限的相关值。不同的维度可以有不同的值集。统计学家和数据科学家可能会将此视为定义在 n 个分类变量集合上的空间，每个变量都有自己的一组值。*

*我们把这一段放在这篇文章中是因为它的启发价值。它为多项式空间上基于 LSH 的索引和查找提供了第二种机制，一种直接的机制。也可以使用比特采样机制；它首先需要将这个宇宙转变成一个二元宇宙。虽然有一种自然的方法可以使用所谓的一键编码将多项式空间转换为二进制空间，但尚不清楚基于两种不同编码(一种直接编码，一种二进制编码)的 LSH 的精度和召回率如何比较。*

***延伸阅读***

1.  *[模糊字符串匹配算法。Levenshtein，语音学|作者 Arun ja gota | 2021 年 12 月|走向数据科学](/fuzzy-string-matching-algorithms-e0d483c2a9ea)*
2.  *[变音——维基百科](https://en.wikipedia.org/wiki/Metaphone)*
3.  *[Levenshtein distance —维基百科](https://en.wikipedia.org/wiki/Levenshtein_distance)*