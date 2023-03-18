# Pandas 与 SQL —第 3 部分:Pandas 更灵活

> 原文：<https://towardsdatascience.com/pandas-vs-sql-part-3-pandas-is-more-flexible-cb43167189f5>

## Pandas 灵活的数据模型非常适合数据科学用例

![](img/0a4d1f9c4243e6ee6ba87651f78d4480.png)

美洲虎坦巴克在 [Openverse](https://wordpress.org/openverse/image/149edeab-4fbb-4d62-9110-269f6e0474bb/) 拍摄的照片(CC BY-ND 2.0)

**TL；在这篇文章中，我们在三个坐标轴的第二个坐标轴上比较了 Pandas 和 SQL:灵活性。我们介绍了 Pandas dataframe 数据模型提供额外灵活性的八种方式，这使其非常适合数据科学和机器学习，优于 SQL 的关系模型。**

我们继续寻求理解 Pandas 和 SQL 的相对优势——两种用于数据操作和分析的流行且强大的语言。这是比较熊猫和 SQL 的系列帖子中的第三篇；下面是之前的两个帖子:[熊猫大战 SQL —第一部分:美食广场和米其林风格的餐厅](https://ponder.io/pandas-vs-sql-food-court-michelin-style-restaurant/)和[熊猫大战 SQL —第二部分:熊猫更简洁](https://ponder.io/pandas-vs-sql-part-2-pandas-is-more-concise/)。

正如我们在上一篇关于 Pandas 与 SQL 的文章中所看到的，Pandas 有 600 多个函数，可以让您以各种强大的方式对数据进行操作，这些方式在 SQL 中是不可能或极难做到的，涵盖了一系列关键的机器学习、线性代数、特征化和数据清理操作。在这篇文章中，我们展示了 Pandas dataframe 数据模型(或抽象)如何提供额外的灵活性，使其非常适合数据科学和机器学习，优于 SQL 底层的关系模型。因此，前一篇文章关注的是数据框架**代数**，而这篇文章将关注数据框架**数据模型**。

以下是 Pandas 数据框架比关系/SQL 数据框架更灵活的多种方式的列表:

1.  将数据转移到元数据，然后再转移回来
2.  行和列元数据
3.  混合型色谱柱
4.  灵活的模式
5.  元数据转换
6.  柱状操作
7.  分层元数据
8.  对元数据差异的容忍

我们将从一个简单的数据集开始，类似于从电子表格加载数据后可能得到的数据集。这是一个包含 2020 年夏季奥运会最佳表现国家的奖牌总数的数据集。

# 1.在 Pandas 中，你可以在元数据之间来回移动数据！在 SQL 中，您不能。

关于上面的数据集，您可能注意到的第一件事是，我们有像`A, B, C, ...` 这样的非描述性列名，而实际的列名是数据的一部分(第 0 行)。理想情况下，我们希望用这些列名替换`A, B, C, ...`。我们可以通过以下方式做到这一点:

我们所做的只是将标题行提取到`header`，修整数据帧以保留最后的`n-1`行，并通过`df.columns`设置列名。

类似地，可以将信息从元数据(列标题)反向移动到数据。见下文。

我们在这里所做的是通过`to_frame()`将列名提取为数据帧，通过单个字母`T`将数据帧转置为一行，最后通过`pd.concat`将该行与旧数据帧垂直连接。

在 SQL 中，实际上不可能将数据移动到元数据(列名)中，或者将数据移动回来。

# 2.Pandas 支持行和列元数据；SQL 只有列元数据。

虽然 Pandas 像数据库一样支持列元数据(即列标签)，但 Pandas 也支持行标签形式的逐行元数据。如果我们想以直观的方式组织和引用数据，这是很方便的。这里有一个例子:我们从重新加载数据帧开始。

现在我们需要做的就是使用`set_index`来设置行标签或索引。这里我们将其设置为数据中的`Name`列。

就像列标签一样，我们也可以使用`reset_index`命令将行标签移回到数据中。

数据库没有行标签的概念。您可能声称行标签功能可以用一个`*PRIMARY* KEY / *UNIQUE*`关键字来复制，但这并不完全正确——行标签实际上不需要唯一。这是熊猫灵活的另一种方式！

# 3.熊猫允许混合式栏目；SQL 只支持单一类型的列

由于它在数据科学中的使用，在不同的清理阶段对数据进行操作，Pandas 没有对每列强制严格的类型。再看我们的例子:

这里，`Ranking`列包含字符串和整数。如果我们检查该列的类型，我们将看到以下内容:

我们所做的是在通过`apply`推断出列中每个值的类型之后，通过`value_counts`计算每个类型的值。正如您在输出中看到的，`Ranking`列包含四个整数和一个字符串(—)。如果我们希望将字符串值强制转换为空值，以便该列具有单一类型，我们可以通过以下方式实现:

# 4.在 Pandas 中，输出模式可以根据数据灵活变化；在 SQL 中，模式是固定的

在 SQL 中，输出的模式(即一组列及其类型)基于输入和查询的模式进行约束。Pandas 没有这种限制，允许输出根据数据而变化，从而提供了额外的灵活性。这里有一个例子，也是在我们熟悉的数据集上:

如您所见，`get_dummies`函数为`Continent`列中的每个值创建了一个新的布尔列。这对机器学习非常有帮助，因为大多数机器学习包只接受数字数据，所以所有的字符串列都需要转换成数字列。如果我们从数据集中省略了对应于`ROC`的最后一行，就不会有对应于`Continent_Europe/Asia`的列。通过这种方式，输出列可以依赖于数据——非常简单！

# 5.Pandas 允许您灵活地转换元数据(列/行标签)；在 SQL 中，您不能

Pandas 认识到模式总是不断变化的，并赋予我们灵活清理元数据的超能力，而不仅仅是以简单的编程方式清理数据。这里，如果我们发现`Continent_`前缀很难跨列重复，我们可以使用一个命令在所有列中删除它:

噗，就这样，没了！不幸的是，SQL 不能像 Pandas 那样给你操作列名的能力。您需要手动指定每个列名将如何更改。

# 6.Pandas 允许您像操作行一样操作列；SQL 没有

不同于 SQL 对行和列的不同处理，Pandas 对它们的处理是一样的。从上面使用`Name`列作为行索引/标签的`df_name_index`开始，我们可以简单地转置它，使行成为列，列成为行，如下所示:

最酷的是，Pandas 自动推断新列的类型，而无需用户做任何工作。在这种情况下，所有这些列都是混合型的，因为它们既有整数也有字符串。以这种方式组织数据通常更容易比较。除了转置，我们还可以像对待行一样沿着列应用大多数函数。我们在之前的博客中已经提到了这方面的例子。

# 7.Pandas 让你拥有层次化的元数据；SQL 没有

分层元数据帮助我们以更易于阅读和直观的方式组织和呈现信息。幸运的是，Pandas 支持分层的行标签和列标签。假设我们想要创建分层的行标签:

正如我们在上面看到的，我们通过`set_index`操作符创建了一个由一对大陆和国家名称组成的行标签层次结构。通过使用`T`操作符转置这个结果，我们得到了一个分层列标签的例子:

在上面的结果中，列标签的第一行捕获了大陆，而第二行捕获了国家名称。与 Pandas 不同，SQL 和关系数据库不支持分层元数据。对此最好的代理是使用半结构化数据格式(例如 JSON、XML)，关系数据库通常支持这种格式作为列中的特殊数据类型。但是，在这些列上实施分层模式是很困难的，对这些嵌套数据格式的操作也是如此。

# 8.Pandas 在对具有不同元数据的多个数据帧进行操作时是宽容的；SQL 不是

当在多个数据帧上操作时，Pandas 操作允许模式差异。我们将通过考虑一个常见的二元运算`concat`来说明这一点。假设我们在当前数据框架旁边有另一个数据框架，包含关于另外三个国家(澳大利亚、法国和荷兰)的信息。我们可以使用`concat`操作符来执行具有匹配模式的两个数据帧的有序联合，如下所示:

得到的数据帧有八行。这是一个简单的例子，类似于 SQL `*UNION*`操作符。现在假设两个数据帧的模式不同；具体来说，`df2`没有金牌榜栏目。这是我们从熊猫身上得到的:

正如我们所看到的，Pandas 采用了一种“尽力而为”的方法，继续执行有序的联合(即连接)，为两个数据帧之一中缺少的列填充`NaN`(即 null)值。在这里，SQL 会给出一个错误，因为模式需要匹配一个联合。

# 结论

正如我们在上面的例子中看到的，Pandas 中的 dataframe 抽象比 SQL 下的关系模型灵活得多。从最终用户的角度来看，这种额外的灵活性通常使表示和使用数据更加直观。此外，在执行数据清理时，这种增加的灵活性是必不可少的:数据通常是脏的，具有异构类型和不精确、未指定和/或未对齐的模式。最后，Pandas 数据模型放弃了任意的区分:行和列是等价的，数据和元数据是等价的——这使得表达许多重要的数据科学和机器学习操作变得更加方便。

如果你能想到 Pandas 比 SQL 更灵活的其他例子，或者相反，我们很乐意听到！欢迎在推特上关注我们，了解更多类似的内容，并在这里回复我们的推特[！](https://twitter.com/ponderdata/status/1551977628722085888)

在我们的 Pandas 与 SQL 系列的下一篇文章(第 4 篇，共 4 篇)中，我们认为 Pandas 是更方便的语言。在这里阅读更多！

*原载于 2022 年 7 月 26 日*[*https://pounder . io*](https://ponder.io/pandas-vs-sql-part-3-pandas-is-more-flexible/)*。*