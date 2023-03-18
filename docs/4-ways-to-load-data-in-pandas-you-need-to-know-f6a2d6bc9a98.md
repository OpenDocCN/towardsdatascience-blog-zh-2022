# 你需要知道的在 Pandas 中加载数据的 4 种方法

> 原文：<https://towardsdatascience.com/4-ways-to-load-data-in-pandas-you-need-to-know-f6a2d6bc9a98>

## 熊猫图书馆的隐藏瑰宝

![](img/66999d780cef2559f8bd637bcb8449ee.png)

照片由[斯科特·格雷厄姆](https://unsplash.com/@homajob?utm_source=medium&utm_medium=referral)在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄

熊猫让领先数据变得简单！我们可以使用`pd.read_csv()`和`pd.read_excel()`函数轻松加载 CSV 或 Excel 文件。但是我们可以扩展它们的功能，使加载数据更容易、更直接！

在本指南中，您将学习:

1.  如何从剪贴板加载数据，
2.  如何一次读取一个工作簿中的所有 Excel 表格，
3.  如何在一个目录中加载多个工作簿，以及
4.  如何将多个列合并成一个日期列

我们开始吧！

# 从剪贴板加载数据

如果你正在处理网上或工作中的电子表格中的小数据，你可以使用`pd.read_clipboard()`函数加载数据。让我们看看这个过程是什么样子的。将下面的文本复制到剪贴板上:

```
Name  Age  Score
0  Evan   33     85
1  Kate   34     90
2   Nik   32     85
3  Kyra   35     95
```

然后运行以下命令，这将输出结构化数据帧:

如何从剪贴板中读取数据帧

很酷，对吧？在下一节中，您将学习如何一次读取一个文件中的所有 Excel 表格。

# 一次读取所有 Excel 表格

Pandas 提供了一种非常有用的方法，可以一次加载 Excel 工作簿中包含的所有工作表。这可以通过使用`pd.read_excel()`功能并在`sheet_name=None`中加载来完成。想跟着去吗？你可以在这里下载[数据集。(数据集完全虚构，由作者提供。)](https://github.com/datagy/mediumdata/raw/master/Pandas_read_files_tips.xlsx)

当`None`用作参数时，Pandas 将加载一个数据帧字典，其中键是表名，数据帧是值。

从那里，我们可以使用`pd.concat()`函数来传递字典的值。让我们看看这个是什么样子的:

如何将 Excel 文件中的所有工作表读入单个数据框

当我们访问字典的值时，会返回一个类似列表的结构。我们可以将它传递给`pd.concat()`函数，函数[会一个接一个地追加数据帧](https://datagy.io/pandas-merge-concat/)。

# 一次加载多个工作簿

在这一节中，您将学习如何使用 Pandas 在一个目录中同时加载多个工作簿。你可以[在这里](https://github.com/datagy/mediumdata/raw/master/Files.zip)下载文件，并将它们加载到一个文件夹中。(关于数据集的快速说明:它是作者出于虚构的目的而创建的)。

让我们看看我们在上面的代码中做了什么:

1.  我们导入熊猫和操作系统库
2.  我们将目录加载到一个变量中，`file_path`
3.  然后，我们使用列表理解来创建文件的路径列表
4.  然后，我们使用`pd.concat()`函数追加所有的数据帧

在下面的最后一节中，您将学习如何从多个专栏中提高阅读日期。

# 改进多列的阅读日期

Pandas 使得将某些列解析为日期变得很容易。然而，可能让您感到惊讶的是，您可以解析来自不同列的日期组件。

我们的工作表包含月、日和年，它们分布在不同的列中。我们可以将它们组合在一起，作为单个日期时间列来读取。这可以通过传递一个包含要解析的列的列表来实现，比如`[['Month', 'Day', 'Year']].`

但是，我们可以更进一步，使用下面的代码为列指定一个名称:

通过传入字典，我们可以为结果列指定一个名称。这还会阻止读取单个列，从而使数据帧变得更小。

# 结论

在这篇文章中，你学到了与熊猫一起工作时阅读数据的四个隐藏的宝石！熊猫提供了大量的功能，很难找到你想要的东西。希望你能学到新的东西！