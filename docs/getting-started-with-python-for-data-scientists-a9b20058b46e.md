# 面向数据科学家的 Python 入门

> 原文：<https://towardsdatascience.com/getting-started-with-python-for-data-scientists-a9b20058b46e>

## 开始时你应该学什么

![](img/3c0d86a48efb8131432993c8b2b9e14d.png)

由[乌列尔 SC](https://unsplash.com/@urielsc26?utm_source=medium&utm_medium=referral) 在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄的照片

对于任何数据科学初学者来说，一个关键问题是使用哪种语言。有很多选择，做出选择可能很困难，尤其是当你在 Twitter(或其他知名来源)上看到一种语言比另一种语言更好的争论时。我可以很自信的说，无论你从哪种语言开始，都比浪费时间去挑选一种语言要好！一旦你学会了一种语言，如果有必要的话，学习另一种语言就变得容易多了，现在大多数数据科学语言都有完整的工具包可供使用。

尽管如此，大多数人最终还是从 Python 开始。这是因为 Python 中围绕数据科学发展起来的深层生态系统，包括 sklearn、statsmodels、pandas、matplotlib、tensorflow 等库。这意味着你在数据科学职业生涯中可能遇到的任何工作流，你都可能在 Python 中完成。然而，选择 Python 的另一个好处是，除了数据科学之外，它还有广泛的适用性。这包括通过 Django 和 Flask 等框架在 web 开发中使用，以及即将成为 [Pyscript](https://pyscript.net/) 的框架，它在自动化和测试中的使用，因为它的易用性和简单性以及 Beautiful Soup 等包，以及在构建产品的一般软件工程领域的广泛使用。因此，学习 Python 不仅可以为学习数据科学做准备，还可以为软件工程中更广阔的职业生涯做准备。

## Python 基础

学习任何编码语言的第一步是学习基础知识。作为其中的一部分，你还需要设置你的计算机，这样你就可以真正地编写和运行代码。在数据科学中，这通常是通过使用 Anaconda 和 Jupyter 笔记本来完成的，这是一种用于数据数据科学工作流的常见环境。对于初学者来说，这样做的好处是，您可以清楚地运行单独的小代码片段，并且 Anaconda 可以帮助您处理 Python 中经常出现的混乱的包冲突现实。虽然许多人后来开始使用实际的 Python 脚本并使用虚拟环境，但 Anaconda 和 Jupyter 笔记本是很好的起点。

学习语言本身通常从理解变量和数据类型如何工作开始。就 Python 而言，在大多数语言中，变量被用来存储信息，这些信息允许您稍后在程序中调用和使用这些信息。这可以通过 Python 中的`=`操作符简单地完成，它将信息赋给一个变量。接下来要学习的第二件事是该语言支持什么数据类型。在 Python 的情况下，四个主要的基本数据类型包括`int`、`float`、`str`和`bool`，它们代表一个整数(没有小数位的整数值)、一个浮点数(有小数位的数值)、一个字符串值(键入的单词)和一个布尔值(只能取`True`和`false`)。虽然您可能会遇到其他数据类型，但这些是让您开始旅程的基本构件。

接下来的事情是学习语言中的操作符。这是用于执行数学或比较运算等操作的符号。在前一种情况下，我们使用的符号如`+`表示加法，`-`表示减法，`*`表示乘法，`/`表示除法。然而，我们也可以执行比较操作，然后形成控制流的基础。在 Python 中，这可以包括诸如用于检查值是否相等的`==`、用于不相等的`!=`以及分别用于小于和大于的`<`、`>`的比较。

[](/ucl-data-science-society-python-fundamentals-3fb30ec020fa) [## UCL 数据科学协会:Python 基础

### 研讨会 1: Jupyter 笔记本，变量，数据类型和操作

towardsdatascience.com](/ucl-data-science-society-python-fundamentals-3fb30ec020fa) 

## Python 逻辑

接下来要讨论的是逻辑和流程流在 Python 中是如何工作的。这是为了让您可以创建更复杂的程序，其中内置了一些逻辑，以便在满足给定条件时触发某些操作。在 Python 中，构建这些复杂的程序通常涉及到条件语句、逻辑语句、循环和函数的使用。

在这方面，首先要讨论的是条件语句。虽然您已经讨论了比较运算符，但这涉及到如何使用它们来检查是否满足某个条件，然后触发一些代码来响应。一个例子是检查变量`a`是否等于`b`使得`a == b`或者`a`大于`b`使得`a > b`将响应为真。然后，这些比较运算符可用于使用条件语句`if`、`else`、`elif`触发代码。这些允许你触发代码`if`条件被满足，或者`else`否则会发生什么。这些条件可以通过使用`and`、`or`和`not`构建成更复杂的语句，这允许您一次检查多个条件。

我们还需要知道如何基于条件或者通过创建可重用的代码片段来重复代码片段。前者可以使用循环来触发，只要满足条件，循环实际上就运行同一段代码。这分为`while`和`for`循环，前者在条件仍然为真时执行给定的动作，而 for 循环将在已经定义的组上循环。当我们需要在代码的不同区域反复使用代码时，我们还有一些有用的函数。这可能是当您希望执行相同的操作，但输入不同或处于工作流的不同阶段时，通过定义一个可在代码中稍后调用的函数来完成。

[](/ucl-data-science-society-python-logic-3eb847362a97) [## UCL 数据科学学会:Python 逻辑

### 讲习班 3:条件语句、逻辑语句、循环和函数

towardsdatascience.com](/ucl-data-science-society-python-logic-3eb847362a97) 

## Python 序列

一旦你掌握了这门语言的基础和逻辑，下一步就是理解如何存储不同形式的数据。这在数据科学中非常重要，因为您不太可能一次存储单个信息，而是存储多个数据块，每个数据块都需要特定的格式。为此，我们需要能够选择正确的数据格式，以实现最高效的存储和访问。

在 python 中，有四个主要的内建序列，你可以经常利用它们。这包括列表、元组、集合和字典。了解如何使用这些信息及其关键特征以确保以正确的方式存储数据是非常重要的。在这种情况下:

*   **列表**:可变、有序、可索引，并且可以包含重复记录
*   **元组**:不可变、有序、可索引，并且可以包含重复记录
*   **集合**:可变、无序、不可索引，不允许重复记录
*   字典:可变、有序、可索引，并且不能包含重复值(至少在它们的键中)

了解这些特征将决定您将选择哪种数据结构/序列来存储数据，以便在您想要执行分析时可以轻松访问。

[](/ucl-data-science-society-python-sequences-e3ffa67604a0) [## UCL 数据科学协会:Python 序列

### 工作坊 2:列表、元组、集合和字典！

towardsdatascience.com](/ucl-data-science-society-python-sequences-e3ffa67604a0) 

## 编程范例

除了学习语言，理解不同的编程范例如何工作也很重要。在学习上述大部分内容时，您将会遇到过程式和函数式编程范例。前者是指代码以过程化的方式展开，代码基本上按照编写时的样子“进行”。而后者通常使用过程化编程，但也利用了将可重复的代码片段抽象成函数的优势。这减少了您必须编写的代码总量，也允许某种形式的抽象。

另一种选择是面向对象编程，这也是您在深入研究 Python 中的库时会遇到的。与前两个范例相反，这一个范例构造代码，以便数据的特征和行为可以捆绑在一起成为一个单一的结构。它通过创建被称为类的“蓝图”来做到这一点，这些“蓝图”允许您创建可以呈现代码中早期定义的某些特征和行为的对象。理解这种范式对于能够与将成为任何数据科学工作流一部分的许多库进行交互是很重要的。这种范式的好处是，它有助于编写可重复使用的代码，并将特征和行为捆绑到一个结构中，使得在与库交互时更容易使用和理解。

[](/ucl-data-science-society-object-oriented-programming-d69cb7a7b0be) [## UCL 数据科学学会:面向对象编程介绍

### 工作坊 4:什么是 OOP，在 Python 中定义类、添加属性、添加方法、类继承

towardsdatascience.com](/ucl-data-science-society-object-oriented-programming-d69cb7a7b0be) 

## 结论

学习一门新的编码语言可能会很困难，尤其是对那些学习母语的人来说。Python 在这方面对数据科学家是有益的，因为它相对容易地从简单的语法开始，足够容易阅读和理解。在学习数据科学语言时，建议您涵盖大部分基础知识，包括:变量、数据结构、序列、操作、逻辑、函数和面向对象编程。一旦掌握了这些基础知识，您就可以更加自信地开始您的 Python 数据科学之旅，并转向更复杂的主题和构建您的数据科学工作流。祝你好运！

如果你喜欢你所读的，并且还不是 medium 会员，请使用下面我的推荐链接注册 Medium，来支持我和这个平台上其他了不起的作家！提前感谢。

[](https://philip-wilkinson.medium.com/membership) [## 通过我的推荐链接加入 Medium—Philip Wilkinson

### 作为一个媒体会员，你的会员费的一部分会给你阅读的作家，你可以完全接触到每一个故事…

philip-wilkinson.medium.com](https://philip-wilkinson.medium.com/membership) 

或者随意查看我在 Medium 上的其他文章:

[](/how-i-landed-an-amazon-sde-internship-without-a-computer-science-degree-85596c480d4d) [## 我是如何在没有计算机科学学位的情况下获得亚马逊 SDE 实习机会的

### 或者解决数百个黑客排名问题…

towardsdatascience.com](/how-i-landed-an-amazon-sde-internship-without-a-computer-science-degree-85596c480d4d) [](/eight-data-structures-every-data-scientist-should-know-d178159df252) [## 每个数据科学家都应该知道的八种数据结构

### 从 Python 中的基本数据结构到抽象数据类型

towardsdatascience.com](/eight-data-structures-every-data-scientist-should-know-d178159df252) [](/a-complete-data-science-curriculum-for-beginners-825a39915b54) [## 面向初学者的完整数据科学课程

### UCL 数据科学协会:Python 介绍，数据科学家工具包，使用 Python 的数据科学

towardsdatascience.com](/a-complete-data-science-curriculum-for-beginners-825a39915b54)