# 熊猫的高效数据操作

> 原文：<https://towardsdatascience.com/efficient-data-manipulation-with-pandas-2cbc4e3824f9>

## 停止用传统的方式使用熊猫，用“管道”代替

## 学习在熊猫中使用管道进行数据操作

![](img/095e8c13352a6c0e489816c5ead7209b.png)

资料来源:Unsplash，Lars Kienle

我们都在用熊猫。它是几乎每个使用 python 的分析师的首选工具。我们中的许多人已经掌握了数据处理的艺术。我对我所知道的关于熊猫的知识和我应用知识的方式非常满意，直到我看到了马特·哈里森写的一本书。这本书改变了我熊猫的生活。我觉得我一直以来都被背叛了😅在这篇文章中，我将分享几件我学到并立即爱上它们的事情。让我们开始吧。

## 一些我们喜欢的任务

在操作数据时，我们通常使用以下操作:

1️⃣:列选择
2️⃣:过滤数据
3️⃣:更改列
4️⃣:创建新列
5️⃣:应用自定义函数
6️⃣:聚合数据
7️⃣:连接数据
8️⃣:可视化数据

这绝对不是一个完整的列表，但现在足够了。你一定注意到了上面任务中的等级。通常，我们以有序的方式应用这些任务。到目前为止一切顺利。然而，我们通常倾向于单独执行这些任务，即使您将这些任务放在一个函数中。我们缺少的是“管道”。

“管道”的目的是将这些任务缝合在一起，并以一种内存高效的方式计算它们。这本身就是一个巨大的优势。然而，对我来说，管道最大的好处是代码的“可读性”。那么这个“管道”是什么呢？

> 最后有一个完整的可复制的代码示例。只需浏览流程的虚拟代码片段(灰色的)。

## 管道

要构建管道，您实际上不必去任何其他特定的库。我们可以通过将数据帧包装在一个元组中来开始使用管道，就像这样:

```
import pandas as pd# read the data
df = read_csv("some_data.csv")
# make a pipeline
( 
  df
)
```

如果您执行代码，这将显示`df`数据帧。没什么特别的。然而，这就是乐趣的开始。在圆括号内，在`df`下面，你可以开始调用所有你喜欢的方法，一个接一个，按照你想要的顺序。让我们试一试。

```
(
  df
  # select few columns
  [['column_a','column_b','column_c']]
  # filter the data where column_a's values are green & blue
  .query(" column_a == ['green','blue']")
  # check the first 5 rows of the data
  .head())
```

如果运行此代码，您将看到数据框的前五行，共三列，包含“column_a”值为“绿色”或“蓝色”的记录。这正是你点的。但是，如果我们运行并检查`df`，我们会发现`df`什么都没有发生，我们所做的所有更改都应用到内存中，并与`df`分开保存。太棒了😮。这种方法的一些好处是:

👉:代码可读性很强
👉:代码灵活，更改非常容易实现
👉:我们不需要创建修改数据帧的单独引用
👉:内存效率高
👉:原始数据帧保持不变

## 它是如何工作的

圆括号中的每一行都是管道中的一个“步骤”。流水线的第一步必须是数据帧。每一步都必须从单独的一行开始。你走的每一步都需要一个数据框架方法，比如`.head()` `.query()` `.tail()` `.merge()`等。每一步的输出都成为下一步的输入。在我们的例子中，步骤`[['column_a','coumn_b'm'column_c']]`的输出是包含三列的数据帧。这成为过滤数据的`.query()`步骤的输入。过滤后的数据成为`.head()`步骤的输入，最后的输出显示给用户。

重要的是保持这一势头。我的意思是，我们应该避免在第一步之后使用数据框的名称。例如，您想要对现有的列进行更改。我将使用`.assign()`方法，这是创建或更改现有列的方法。

这是你应该**而不是**做的:

```
(
df 
# apply a filter
.query("column_a == ['green','blue']")
# make a change to column_a
.assign(column_a = df['column_b'])
)
```

通过引用`.assign()`步骤中的`df['column_b]`，我们实际上是在引用回`df`的原始状态(即它在第一步时的状态)，这是我们不想要的。我们想要的是仅在我们将过滤器应用到`column_a`(过滤数据的`.query()`步骤的输出)之后改变`column_a`。为了做到这一点，我们将在`assign()`步骤中使用一个函数(比如 lambda)。这就是我们**应该**做的:

```
(
df 
# apply a filter
.query("column_a == ['green','blue']")
# make a change to column_a
.assign(column_a = lambda x: x['column_b])
)
```

在这种情况下，lambda 函数中的参数`x`引用的是`.query()`步骤的输出，而不是原来的`df`，正如我们所希望的那样。

**最后一部分**

在我们进行最后一个可重复的例子之前，我需要向您介绍一个重要的方法，`.pipe()`方法。如果您想要应用熊猫数据框固有的不可用方法(如自定义函数)，此方法非常有用。`.pipe()`方法接受一个函数和该函数的参数。函数的第一个参数应该是数据框。函数的输出也应该是数据框。让我们看一个例子:

```
# define a custom function, first argument as a df. Function
# returns a df.
def some_function(df:pd.DataFrame,column_name:str)->pd.DataFrame:
  new_df = df[column_name]*4/df[column_name]^3
  return new_df# start the pipeline
(
  df
  .pipe(somefunction,"column_c")
  .head()
)
```

简而言之，`.pipe()`将帮助我们部署任何我们想要应用于我们的数据框架的定制解决方案/功能。

**总结**

Pandas piping 是一种优秀的、节省内存的方式，可以为数据操作编写清晰可读的代码。它简单直观。您还可以将最终输出分配给另一个变量，例如

```
df_1 = (
         df
         .query("column_a == 'blue'")
         )
```

我们也可以把管道包装成一个函数，然后一直使用函数进行重复使用。

最后，这里有一个可重复的代码，您可以使用它来进一步挖掘和实践。

作者代码

➖➖➖➖➖➖➖➖➖➖➖➖➖➖➖➖➖➖➖➖➖➖➖➖➖➖➖➖➖➖➖➖➖
可以在 [**上关注我**](https://fahadakbar-50702.medium.com/subscribe) &在[**LinkedIn**](https://www.linkedin.com/in/fahadakbar/)&上联系我访问我的 [**GitHub**](https://github.com/mfahadakbar/) **。** ➖➖➖➖➖➖➖➖➖➖➖➖➖➖➖➖➖➖➖➖➖➖➖➖➖➖➖➖➖➖➖➖➖

# 您可能还对以下内容感兴趣:

👉[Docker](/make-your-data-science-life-easy-with-docker-c3e1fc0dee59)
让您的数据科学生活变得简单👉[使用 PyCaret 的自定义估算器，第 1 部分](/custome-estimator-with-pycaret-part-1-by-fahad-akbar-839513315965)
👉[使用 PyCaret 的自定义估算器，第 2 部分](/custom-estimator-with-pycaret-part-2-by-fahad-akbar-aee4dbdacbf?sk=3556332049ac839d1d423615dab25bf0)
👉[轻松获得 Windows 内部的 Linux](https://fahadakbar-50702.medium.com/get-linux-in-windows-the-easy-way-three-simple-steps-by-fahad-akbar-aa5b142c943c?sk=a8e20dae33fde0563e69bb00966b5c17)
👉[使用 PyCaret 进行多重处理](/a-data-scientists-dream-python-big-data-multi-processing-pycaret-by-fahad-akbar-7cc213a12db)