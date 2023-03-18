# 使用 Csvkit 包在终端中控制 CSV 文件

> 原文：<https://towardsdatascience.com/master-csv-files-in-the-terminal-with-the-csvkit-package-70984d394501>

## 使用 Excel 并不总是一个好主意。

![](img/8639a2862ce012b1f8fca51fbcdfe593.png)

照片由[西格蒙德](https://unsplash.com/@sigmund?utm_source=medium&utm_medium=referral)在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 拍摄

# 您的旅程概述

1.  [为什么要在终端处理 CSV 文件？](#c0e1)
2.  [快速设置](#8929)
3.  [Excel 黑仔(in2csv)](#c793)
4.  [数据 Scapel (csvcut)](#85f5)
5.  [好看(csvlook)](#4079)
6.  [牛逼统计(csvstat)](#138e)
7.  [巧妙搜索(csvgrep)](#5243)
8.  [包装](#294e)

# 1 —为什么要在终端中处理 CSV 文件？

很少有事情能像在**命令行终端**中工作一样令人生畏。许多数据科学家没有计算机科学背景，因此不习惯这样。甚至看起来在命令行终端工作已经是过去的事情了😧

我在这里告诉你，这是假的。事实上，随着像 [Azure Cloud Shell](https://docs.microsoft.com/en-us/azure/cloud-shell/overview) 这样的基于云的 Shell 的增加，学习命令行比以往任何时候都更有价值。事实是命令行是一个*效率助推器*。对文件夹使用图形用户界面(GUI)对于简单的事情来说是最容易的，但是对于较难的事情来说就变得越来越复杂了。

对于数据科学家/数据工程师来说，有许多终端工具可以快速处理终端中的数据。在这篇博文中，我将告诉你一个我最喜欢的叫做 [csvkit](https://csvkit.readthedocs.io/en/latest/tutorial.html) 的东西。这是一个在终端中处理 CSV 文件的工具。如果您正在处理 CSV 文件或 Excel 文件形式的月度报告，这将非常有用。使用 csvkit，您可以轻松地:

*   将 excel 文件转换为 CSV 文件
*   打印格式良好的 CSV 文件
*   剪切特定的列
*   获取有关列的统计信息
*   使用正则表达式在列内搜索

还有更多！您也许可以用 Excel 做同样的事情。然而，使用 csvkit 做事情的真正价值在于您可以自动化这个过程(例如使用 cronjobs)。

我将向您介绍如何使用 csvkit，以便您可以在终端中处理 CSV 文件。具体来说，我会教你我认为最重要的五个 csvkit 命令。如果你更喜欢视觉学习，那么我也在 csvkit 上制作了一个免费的 youtube 视频系列[你可以看看😃](https://www.youtube.com/playlist?list=PLSE7WKf_qqo1Dl9C2HuegYp0aK7SbZ3Jx)

> **先决条件:**您应该已经安装了运行 BASH 的命令行终端。如果你使用的是 Linux，那么这应该不成问题，而 Windows 用户可能想看看 [cmder](https://cmder.net/) 或者用 [WSL2](https://cloudbytes.dev/snippets/how-to-install-wsl2-on-windows-1011) 启用 Linux 子系统。

# 2—快速设置

要开始使用 csvkit 包，您需要安装它。csvkit 包是一个 Python 包，所以您需要做的就是运行(假设您已经安装了 Pyhon 的包安装程序 pip ):

```
pip install csvkit
```

如果不想全局安装 csvkit 包，那么可以考虑使用 [virtualenv](#https://virtualenv.pypa.io/en/latest/) 来设置一个虚拟环境。要检查安装是否正常，您可以运行以下命令:

```
in2csv --help
```

如果一切安装正确，您现在应该会看到命令`in2csv`的帮助页面。命令`in2csv`是 csvkit 为我们安装的几个命令之一。

让我们打开一个名为`csvkit_sandbox`的新文件夹，你可以在这里玩你的新玩具:

```
mkdir csvkit_sandbox
cd csvkit_sandbox
```

最后，您需要一些实际使用的数据:让我们下载 csvkit 文档也在使用的数据:

```
curl -L -O https://raw.githubusercontent.com/wireservice/csvkit/master/examples/realdata/ne_1033_data.xlsx
```

运行上面的命令后，您应该在您的文件夹中安装了文件`ne_1033_data.xlsx`。如果你不信任我，你可以运行`ls`来检查你的`csvkit_sandbox`文件夹的内容😉

# Excel 黑仔(in2csv)

我们要看的第一个命令是`in2csv`命令。这个命令将一个 excel 文件转换成一个 CSV 文件(废话！).这非常有用，因为数据科学家经常获得 excel 格式的报告，并且必须将它们转换为 CSV 文件才能有效地使用它们。

要使用`in2csv`命令，您只需编写:

```
in2csv ne_1033_data.xlsx
```

如果您像这样使用该命令，那么您只需将所有输出转储到终端。即使对于中等大小的文件，这也很糟糕。更好的选择是将输出重定向到一个文件，如下所示:

```
in2csv ne_1033_data.xlsx > new_file.csv
```

现在，在您的`csvkit_sandbox`文件夹中应该有一个名为`new_file.csv`的新 CSV 文件。我有时使用的一个技巧是在同一个命令中添加一个`rm`命令来删除原始文件，如下所示:

```
in2csv ne_1033_data.xlsx > new_file.csv && rm ne_1033_data
```

如果您运行上面的命令，那么在您的`csvkit_sandbox`文件夹中应该只有文件`new_file.csv`。如果您想签出文件`new_file.csv`，那么尝试命令:

```
head new_file.csv
```

该命令将文件`new_file.csv`中的第一行输出到终端。

![](img/852644bab8571caffd76997963873797.png)

照片由 [Mohamed Nohassi](https://unsplash.com/@coopery?utm_source=medium&utm_medium=referral) 在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 拍摄

# 4—数据手术刀(csvcut)

在上一节中，您从 excel 文件中检索了所有列，并将其转换为 CSV 文件。但是通常您不需要所有的列来进行进一步的分析。如果是这样的话，那么和我们一起拖无用的列将是一件麻烦事。不要害怕！使用命令`csvcut`可以选择 CSV 文件的某些列:

```
csvcut -c county,total_cost,ship_date new_file.csv**Output:**
county,total_cost,ship_date
ADAMS,138.0,2008-07-11
ADAMS,138.0,2008-07-11
ADAMS,138.0,2008-07-11
ADAMS,138.0,2008-07-11
ADAMS,138.0,2008-07-11
ADAMS,138.0,2008-07-11
BUFFALO,499.0,2008-09-24
BUFFALO,499.0,2008-09-24
BUFFALO,499.0,2008-09-24
BUFFALO,499.0,2008-09-24
BUFFALO,499.0,2008-09-24
BUFFALO,499.0,2008-09-24
BUFFALO,499.0,2008-09-24
BUFFALO,499.0,2008-09-24
BURT,499.0,2013-06-20
...
```

上述命令仅从 CSV 文件`new_file.csv`中选择列`county`、`total_cost`和`ship_date`。

但是如果您不记得列名了呢？然后，一个快速的技巧是运行命令:

```
csvcut -n new_file.csv**Output:** 1: state
2: county
3: fips
4: nsn
5: item_name
6: quantity
7: ui
8: acquisition_cost
9: total_cost
10: ship_date
11: federal_supply_category
12: federal_supply_category_name
13: federal_supply_class
14: federal_supply_class_name
```

可选参数`-n`给出了列的名称。整洁，对不对？命令`csvcut`对于选择想要继续的列非常有用。

# 5-看起来不错(csvlook)

![](img/722444f0ff45c36c34c55769e5b45d26.png)

[梅尔·埃利亚斯](https://unsplash.com/@cuartodeiibra?utm_source=medium&utm_medium=referral)在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄的照片

当您将最后一部分中的 CSV 文件输出到终端时，它看起来不是很好。将原始 CSV 文件打印到终端时，这样读起来通常会很糟糕:

```
csvcut -c county,total_cost,ship_date new_file.csv**Output:**
county,total_cost,ship_date
ADAMS,138.0,2008-07-11
ADAMS,138.0,2008-07-11
ADAMS,138.0,2008-07-11
ADAMS,138.0,2008-07-11
ADAMS,138.0,2008-07-11
ADAMS,138.0,2008-07-11
BUFFALO,499.0,2008-09-24
BUFFALO,499.0,2008-09-24
BUFFALO,499.0,2008-09-24
BUFFALO,499.0,2008-09-24
BUFFALO,499.0,2008-09-24
BUFFALO,499.0,2008-09-24
BUFFALO,499.0,2008-09-24
BUFFALO,499.0,2008-09-24
BURT,499.0,2013-06-20
...
```

命令`csvlook`前来救援。您可以使用**管道操作符** `|`将命令`csvcut`的输出作为命令`csvlook`的输入，如下所示:

```
csvcut -c county,total_cost,ship_date new_file.csv | csvlook**Output:** | county     | total_cost |  ship_date |
| ---------- | ---------- | ---------- |
| ADAMS      |     138.00 | 2008-07-11 |
| ADAMS      |     138.00 | 2008-07-11 |
| ADAMS      |     138.00 | 2008-07-11 |
| ADAMS      |     138.00 | 2008-07-11 |
| ADAMS      |     138.00 | 2008-07-11 |
| ADAMS      |     138.00 | 2008-07-11 |
| BUFFALO    |     499.00 | 2008-09-24 |
| BUFFALO    |     499.00 | 2008-09-24 |
| BUFFALO    |     499.00 | 2008-09-24 |
| BUFFALO    |     499.00 | 2008-09-24 |
| BUFFALO    |     499.00 | 2008-09-24 |
| BUFFALO    |     499.00 | 2008-09-24 |
| BUFFALO    |     499.00 | 2008-09-24 |
| BUFFALO    |     499.00 | 2008-09-24 |
| BURT       |     499.00 | 2013-06-20 |
...
```

那看起来好多了！现在，用肉眼解析输出要容易得多。

还记得你用管道操作符`|`将`csvcut`的输出传递给`csvlook`的输入的技巧吗？这在 csvkit 中非常常见，并且是创建更复杂管道的关键🔥

# 6 —令人敬畏的统计数据(csvstat)

当作为数据分析师或数据科学家处理 CSV 文件时，我们经常希望提取汇总统计数据。有数百种方法可以提取 CSV 文件中各列的中值和平均值。你应该用哪一个？将数据导入 Excel？用熊猫进行快速数据分析？

我想你知道我想说什么。当然，csvkit 对此有一个命令叫做`csvstat`。命令`csvstat`从 CSV 文件中的每一列提取基本统计数据:

```
csvstat new_file.csv**Output:**1\. "state"
Type of data:          Text
Contains null values:  False
Unique values:         1
Longest value:         2 characters
Most common values:    NE (1036x)2\. "county"
Type of data:          Text
Contains null values:  False
Unique values:         35
Longest value:         10 characters
Most common values:    DOUGLAS (760x)
                       DAKOTA (42x)
                       CASS (37x)
                       HALL (23x)
                       LANCASTER (18x)3\. "fips"
Type of data:          Number
Contains null values:  False
Unique values:         35
Smallest value:        31001
Largest value:         31185
Sum:                   32176888
Mean:                  31058.772
Median:                31055
StDev:                 23.881
Most common values:    31055 (760x)
                       31043 (42x)
                       31025 (37x)
                       31079 (23x)
                       31109 (18x)
...
```

如果您仔细阅读上面的输出，那么您会发现`csvstat`根据列类型给出不同的统计信息。如果你的某一列是文本格式，那么谈论那一列的标准差就没什么意义了。

命令`csvstat`执行**类型的推理**。它尝试推断列的类型，然后找到合适的汇总统计信息。根据我的经验，这非常有效。

有时，您不想要所有列的统计数据，而只想要几列。为此，使用命令`csvcut`过滤出必要的列，然后通过管道将其传递给`csvstat`以获得统计数据:

```
csvcut -c total_cost,ship_date new_file.csv | csvstat**Output:**1\. "total_cost"
Type of data:          Number
Contains null values:  False
Unique values:         92
Smallest value:        0
Largest value:         412000
Sum:                   5553135.17
Mean:                  5360.169
Median:                6000
StDev:                 13352.139
Most common values:    6800 (304x)
                       10747 (195x)
                       6000 (105x)
                       499 (98x)
                       0 (81x)2\. "ship_date"
Type of data:          Date
Contains null values:  False
Unique values:         84
Smallest value:        2006-03-07
Largest value:         2014-01-30
Most common values:    2013-04-25 (495x)
                       2013-04-26 (160x)
                       2008-05-20 (28x)
                       2012-04-16 (26x)
                       2006-11-17 (20x)Row count: 1036
```

# 7 —智能搜索(csvgrep)

我极力推荐的最后一个命令是`csvgrep`命令。命令`csvgrep`允许您搜索 CSV 文件以找到特定的记录。如果你习惯了终端命令`grep`，那么`csvgrep`命令也差不多。

要查看它的运行情况，让我们在 CSV 文件中搜索 county **HOLT** :

```
csvgrep -c county -m "HOLT" new_file.csv**Output:** NE,HOLT,31089.0,1005-00-073-9421,"RIFLE,5.56 MILLIMETER",1.0,Each,499.0,499.0,2008-05-19,10.0,WEAPONS,1005.0,"Guns, through 30 mm"NE,HOLT,31089.0,1005-00-589-1271,"RIFLE,7.62 MILLIMETER",1.0,Each,138.0,138.0,2006-03-08,10.0,WEAPONS,1005.0,"Guns, through 30 mm"NE,HOLT,31089.0,1005-00-589-1271,"RIFLE,7.62 MILLIMETER",1.0,Each,138.0,138.0,2006-03-08,10.0,WEAPONS,1005.0,"Guns, through 30 mm"
...
```

成功了！现在你只能得到县**霍尔特**的记录。

*   参数`-c`用于选择*列。*
*   参数`-m`用于查找与匹配的字符串*。*

> **Pro 提示:**`csvgrep`命令也允许使用可选参数`-r`进行正则表达式搜索。查看 [csvgrep 文档](https://csvkit.readthedocs.io/en/latest/scripts/csvgrep.html)了解更多相关信息！

我给你的最后一个建议是，试着组合几个 csvkit 命令来获得很酷的结果。看看这个。

```
csvcut -c county,total_cost new_file.csv | csvgrep -c county -m "HOLT" | csvlook**Output:**
| county | total_cost |
| ------ | ---------- |
| HOLT   |     499.00 |
| HOLT   |     138.00 |
| HOLT   |     138.00 |
| HOLT   |     138.00 |
| HOLT   |     138.00 |
| HOLT   |     138.00 |
| HOLT   |     138.00 |
| HOLT   |      58.71 |
```

首先，我只选择了带有`csvcut`的两列`county`和`total_cost`。然后我用命令`csvgrep`搜索县 **HOLT** 。最后，我用命令`csvlook`很好地显示了结果。现在轮到你和✌️搭档了

# 8 —总结

![](img/6784561c6caed537e147ff1a6283d163.png)

照片由[斯潘塞·伯根](https://unsplash.com/@spencerbergen?utm_source=medium&utm_medium=referral)在 [Unsplash](https://unsplash.com/?utm_source=medium&utm_medium=referral) 上拍摄

希望你开始像我一样喜欢 csvkit。同样，如果你想学习一些更酷的技巧和诀窍，那么查看 csvkit 文档[或 csvkit](https://csvkit.readthedocs.io/en/latest/) 上我的 youtube 视频[。](https://www.youtube.com/playlist?list=PLSE7WKf_qqo1Dl9C2HuegYp0aK7SbZ3Jx)

**喜欢我写的？**查看我的其他帖子，了解更多 Python 内容:

*   [作为数据科学家如何写出高质量的 Python](/how-to-write-high-quality-python-as-a-data-scientist-cde99f582675)
*   [用漂亮的类型提示使你罪恶的 Python 代码现代化](/modernize-your-sinful-python-code-with-beautiful-type-hints-4e72e98f6bf1)
*   [用 Python 可视化缺失值非常简单](/visualizing-missing-values-in-python-is-shockingly-easy-56ed5bc2e7ea)
*   [使用 PyOD 在 Python 中引入异常/离群点检测🔥](/introducing-anomaly-outlier-detection-in-python-with-pyod-40afcccee9ff)
*   5 个专家建议让你的 Python 字典技能突飞猛进🚀

如果你对数据科学、编程或任何介于两者之间的东西感兴趣，那么请随意在 LinkedIn 上加我，并向✋问好