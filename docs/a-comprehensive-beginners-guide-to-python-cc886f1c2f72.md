# Python 初学者综合指南

> 原文：<https://towardsdatascience.com/a-comprehensive-beginners-guide-to-python-cc886f1c2f72>

## 学习 Python 的基础知识，包括数据类型、流控制语句、函数和模块

![](img/a203fe25bace9bef09bbd5bd8cb15a75.png)

杰佛森·桑多斯在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 拍摄的照片

Python 是一种流行的高级编程语言，以其简单性、可读性和灵活性而闻名。它是一种通用语言，可用于广泛的应用，从 web 开发和科学计算到数据分析和人工智能。

# 入门指南

要开始使用 Python，您需要在您的计算机上安装它。Python 的最新版本可以从 Python 官方网站([](https://www.python.org/)**)下载。一旦您下载并安装了 Python，您就可以通过打开 Python 解释器来开始使用它。**

**在 Windows 上，你可以通过*开始>程序> Python 3 打开解释器。X* (其中 *X* 是你安装的版本号)，然后点击***“Python 3。X"*** 图标。**

**在 Mac 上，你可以打开解释器，方法是进入*应用>实用程序>终端*，然后输入***【python 3】***，按*回车*。**

**一旦解释器打开，您就可以通过输入命令并立即看到结果来开始使用 Python。**

**例如，您可以键入`print("Hello, World!")`并按 Enter 键来查看输出*“Hello，World！”*。**

# **Python 基础**

**Python 是一种解释型高级通用编程语言。这意味着它在运行时由**解释器**执行，而不是被**编译**成机器码，这样便于编写和调试。它也是一种高级语言，这意味着它抽象掉了计算机的许多低级细节，如内存管理和垃圾收集，并为程序员提供了更高级、更直观的界面。**

**Python 是一种 ***面向对象的语言*** ，这意味着它将数据和对该数据进行操作的功能组织成称为**对象**的可重用单元。**

> ****对象可以被认为是保存数据和对数据进行操作的函数的容器。这允许你编写模块化的、可重用的、易于维护和扩展的代码。****

**Python 是**动态类型的**，这意味着在声明变量时不需要指定变量的数据类型。解释器将根据您分配给变量 的值自动 ***推断数据类型。例如，下面的代码将整数值 10 赋给变量`a`和字符串值“Hello，World！”变量`b`，而不指定它们的数据类型:*****

```
a = 10
b = "Hello, World!"
```

> **它是 ***动态*** 因为你可以给同一个变量赋另一个不同数据类型的值；因此，它是动态地 键入的 ***。这与**静态类型的**语言相反，在静态类型的语言中，变量只能保存特定于*数据类型的值。这种动态类型允许更大的灵活性，并使编写和维护代码更容易。******

# ***数据类型***

***在 Python 中，有几种内置的数据类型可以用来存储和操作数据。这些数据类型包括:***

*   *****数字** : Python 支持整数和浮点数。整数是可以是正数、负数或零的整数，而浮点数是带小数点的数字。比如`10`、`-5`、`0`都是整数，而`3.14`、`1.23e2`、`-2.5`都是浮点数。***
*   *****字符串**:字符串是一个字符序列，比如一个单词、一个句子或者一个段落。在 Python 中，字符串用单引号或双引号括起来。比如`"Hello, World!"`、`'Python is fun'`、`"123"`都是字符串。字符串是*不可变的*，这意味着它们一旦被创建就不能被修改。***
*   *****布尔值**:布尔值是二进制值，可以是`True`也可以是`False`。布尔通常用在条件语句中来控制程序的流程。例如，以下代码使用布尔值来控制是否执行循环:***

```
*flag = True

if flag:
    # code to be executed
else:
    # code to be executed if the flag is False*
```

*   *****列表**:列表是一个 ***有序的*** 值集合。在 Python 中，列表用方括号(`[]`)括起来，列表中的值用逗号分隔。列表可以包含不同数据类型的值，包括其他列表。例如，下面的代码创建一个字符串列表:***

```
*fruits = ["apple", "banana", "cherry"]*
```

*   *****元组**:元组类似于列表，但是和字符串一样，它是*不可变的*，这意味着一旦创建就不能修改它的值。在 Python 中，元组用括号(`()`)括起来，元组中的值用逗号分隔。像列表一样，元组可以包含不同数据类型的值，包括其他元组。例如，下面的代码创建一个数字元组:***

```
*coordinates = (10, 20, 30)*
```

*   *****字典**:字典是*键值对*的集合。在 Python 中，字典用花括号(`{}`)括起来，键值对用逗号分隔。字典中的关键字必须是唯一的，它们用于查找相应的值。例如，下面的代码创建了一个颜色及其十六进制值的字典:***

```
*colors = {
    "red": "#ff0000",
    "green": "#00ff00",
    "blue": "#0000ff"
}*
```

# ***流控制***

***流控制语句用于控制程序中的执行流。在 Python 中，您可以使用几个流控制语句，包括:***

*   *****if-elif-else**:`if-elif-else`语句用于根据指定的条件执行不同的代码块。`if`条款指定了被测试的条件，而`elif`(“else if”的缩写)和`else`条款指定了条件不满足时采取的替代行动。例如，下面的代码使用一个`if-elif-else`语句根据变量值打印一条消息:***

```
*score = 75

if score >= 90:
    print("Excellent!")
elif score >= 80:
    print("Good job!")
else:
    print("Keep trying.")*
```

*   *****for** :循环`for`用于迭代一系列值。在 Python 中，`for`循环具有以下语法:***

```
*for variable in sequence:
    # code to be executed*
```

> *****`**variable**`**是** `**sequence**` **中当前值的占位符，循环中的代码针对** `**sequence**` **中的每个值执行。*******

*****例如，下面的代码使用了一个`for`循环来打印列表中的元素:*****

```
***fruits = ["apple", "banana", "cherry"]

for fruit in fruits:
    print(fruit)***
```

*   *******while** :当指定条件为`True`时，`while`循环用于重复一段代码。在 Python 中，`while`循环具有以下语法:*****

```
***while condition:
    # code to be executed***
```

*****执行循环中的代码，直到`condition`变为`False`。例如，下面的代码使用了一个`while`循环来打印从 1 到 10 的数字:*****

```
***n = 1

while n <= 10:
    print(n)
    n += 1***
```

> *****当 **n** 达到 10 时，条件 **n ≤ 10** 评估为**假**，while 循环内的代码**不**执行。*****

# *****功能*****

*****函数是执行特定任务的可重用代码块。在 Python 中，函数是用`def`关键字定义的，后面是函数名和函数的 ***参数*** 用括号(`()`)括起来。函数中的代码是缩进的，函数以一个指定返回值的`return`语句结束。例如，下面的代码定义了一个计算矩形面积的函数:*****

```
***def rectangle_area(width, height):
    area = width * height
    return area***
```

*****要调用一个函数，你只需要使用它的名字，后面跟着用括号括起来的必需参数。例如，下面的代码调用`rectangle_area`函数并打印结果:*****

```
***result = rectangle_area(10, 20)
print(result)  # Output: 200***
```

# *****模块*****

*****一个模块就是一个 ***Python 文件*** ，里面包含了相关函数和变量的集合。您可以使用模块来组织您的代码，使其更具可重用性和可维护性。在 Python 中，可以使用`import`关键字导入一个模块并访问它的函数和变量。例如，以下代码导入了`math`模块，并使用其`sqrt`函数来计算一个数字的平方根:*****

```
***import math

result = math.sqrt(9)
print(result)  # Output: 3.0***
```

*****您还可以使用`from`关键字从模块中导入特定的函数或变量。例如，以下代码从`math`模块导入`pi`变量，并使用它来计算圆的面积:*****

```
***from math import pi

def circle_area(radius):
    area = pi * radius ** 2
    return area

result = circle_area(5)
print(result)  # Output: 78.53981633974483***
```

# *****结论*****

*****本指南简要介绍了 Python，包括其基础知识、数据类型、流控制语句、函数和模块。Python 是一种功能强大的通用语言，可用于多种应用。无论您是想学习一门新的编程语言的初学者，还是想拓展技能的有经验的开发人员，Python 都是一个很好的选择。*****

*****如果你喜欢阅读这样的故事，并想支持我成为一名作家，考虑注册成为一名媒体会员。一个月 5 美元， ***让你无限制地访问媒体上的故事*** *。如果你用我的* [***链接***](https://lmatalka90.medium.com/membership) *注册，我会赚一小笔佣金。******

*****[](https://lmatalka90.medium.com/membership) [## 通过我的推荐链接加入媒体——卢艾·马塔尔卡

### 阅读卢艾·马塔尔卡的每一个故事(以及媒体上成千上万的其他作家)。您的会员费直接支持…

lmatalka90.medium.com](https://lmatalka90.medium.com/membership)*****