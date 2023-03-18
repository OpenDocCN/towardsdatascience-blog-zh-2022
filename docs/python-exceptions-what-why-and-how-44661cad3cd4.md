# Python 异常——什么、为什么和如何？

> 原文：<https://towardsdatascience.com/python-exceptions-what-why-and-how-44661cad3cd4>

## 理解 Python 中异常的工作方式以及如何正确使用它们

![](img/2b81636e59144346101b829bd1b93a42.png)

在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上由 [Erwan Hesry](https://unsplash.com/@erwanhesry?utm_source=medium&utm_medium=referral) 拍摄的照片

# 什么是例外？

异常就像一些恼人的朋友，在您的 Python 之旅中，您会以这样或那样的方式遇到它们。任何时候你试图做一些不守规矩的事情或者让 Python 做一些 Python 不喜欢的事情，你很可能会被移交给一些*异常*，它们会根据“冒犯”的程度停止或者只是警告你

> Python 用自己的方式告诉你，你所要求的要么无法实现，要么需要做些事情来避免将来执行失败。

在这篇文章中，我们将深入 Python *异常*的细节。我们将学习如何处理它们，将它们理解为 Python *类*，如何基于异常类型定制我们的响应，还将知道如何创建自己的异常。

由于异常本身就是类，我们将使用大量对 Python 类的引用。因此，如果你需要快速复习，你可以阅读我的关于 Python 中面向对象编程的系列文章。

# 处理异常

异常是 Python 告诉你事情没有按计划或预期进行的方式。在交互式和特别的编码场景中，比如数据分析，我们通常不需要处理异常，因为我们在面对异常并继续前进时会修复它们。但是如果你想把你的脚本用于任何类型的自动化任务，比如一个 [ETL](https://en.wikipedia.org/wiki/Extract,_transform,_load) 任务，不处理异常就像把一把上膛的枪放在无人看管的地方，对准你的脚。你永远不知道什么时候会有人给它一个晃动，无意中拍摄它！

> *我们所说的*处理异常*基本上是指设置一组命令，这样如果发生*异常*，Python 就知道下一步该做什么，而不仅仅是抛出一个 fit。*

## 最简单的方法

为了捕获异常，我们使用了一个名为`try-except`的代码块。我们将被怀疑是错误来源的那段代码放在`try`块中，然后在`except`块中捕获并设计响应。查看以下示例，其中函数`calcArea`被定义为从用户处接收圆的`radius`值，并返回圆的计算面积。

```
Area for radius 5 = 78.53999999999999Something is wrong with aArea for radius 4 = 50.2656Area for radius 8 = 201.0624Something is wrong with bArea for radius 0 = 0.0
```

在`for`循环中，

Python 首先执行`try`块内的`calcArea()`。

*   它试图计算面积并将其保存到名为`area`的变量中。
*   如果没有遇到任何异常，它打印出新创建的变量`area`。
*   但是如果它遇到了问题，它就转移到`except`代码块。

在`except`代码块内，

*   `Exception`类被捕获或存储，并被命名为`e`，或者给它你想要的任何名字。这个命名对象随后用于访问*异常*类*对象*的元素。

但是异常处理有什么好处呢？

请注意，一旦`for`循环获得意外值，即`strings`，它不会中断。如果我们不处理从`calcArea()`抛出的异常，那么`for`循环就会在执行完第一个元素后中断。

🛑看你自己试试看！尝试在不使用`try-except`的情况下在循环中运行`calcArea()`。

## 让我们稍微投入一点

`try-except`代码块有两个附加分支:`else`和`finally`。

*   `else`代码块只有在没有异常发生的情况下才会执行。我们可以用它以一种更简洁的方式打印出一个成功操作的定制消息——而不是把它塞在`try`块中。
*   `finally`无论有无异常，代码块**总是**被执行。通常用于留下一个脚印以标志操作的结束。

```
calcArea() ran successfully for 5
Area for input 5 = 78.53999999999999 
calcArea() run completed on 2022-03-24 10:36:49.778314

Something is wrong for a.
Area for input a = None 
calcArea() run completed on 2022-03-24 10:36:49.778314

calcArea() ran successfully for 4
Area for input 4 = 50.2656 
calcArea() run completed on 2022-03-24 10:36:49.779315

calcArea() ran successfully for 8
Area for input 8 = 201.0624 
calcArea() run completed on 2022-03-24 10:36:49.779315

Something is wrong for b.
Area for input b = None 
calcArea() run completed on 2022-03-24 10:36:49.779315

calcArea() ran successfully for 0
Area for input 0 = 0.0 
calcArea() run completed on 2022-03-24 10:36:49.779315
```

## 更有表现力怎么样！

我们的`try-except`模块告诉我们有问题，但没有告诉我们到底哪里出了问题。在本节中，我们将对此进行研究。

正如我们已经知道的，Python 中的异常基本上是类本身，它们还带有一些 Python 类的内置变量。在下面的例子中，我们将使用这些类属性中的一些来使错误消息更有表现力。

让我们先看看例子，然后我们会回来讨论例子中使用的类属性。

```
calcArea() ran successfully for 5
Area for input 5 = 78.53999999999999 
calcArea() run completed on 2022-03-24 10:36:52.476687

Area couldn't be calculated for a.
Error type: ValueError 
Error msg: could not convert string to float: 'a'.
Area for input a = None 
calcArea() run completed on 2022-03-24 10:36:52.476687

calcArea() ran successfully for 4
Area for input 4 = 50.2656 
calcArea() run completed on 2022-03-24 10:36:52.476687

calcArea() ran successfully for 8
Area for input 8 = 201.0624 
calcArea() run completed on 2022-03-24 10:36:52.476687

Area couldn't be calculated for b.
Error type: ValueError 
Error msg: could not convert string to float: 'b'.
Area for input b = None 
calcArea() run completed on 2022-03-24 10:36:52.477706

calcArea() ran successfully for 0
Area for input 0 = 0.0 
calcArea() run completed on 2022-03-24 10:36:52.477706
```

*   `type(e).__name__`:打印出*异常*的*子类*名称。`except`块在遇到`string`作为输入时打印出`TypeError`。
*   `print(e)`:打印出整个错误信息。

**但是如果** `**e**` **是一个异常类的*对象*，我们不应该用类似** `**e.print_something()**` **的东西吗？**

这是可能的，因为 Python *异常*类带有一个名为`__str__()`的内置方法。在一个类中定义这个方法可以直接打印出一个类。

🛑试试看！不要调用`e`，而是调用`e.__str__()`来打印错误信息。

## 如果我们需要一些定制呢？

从我们的`calcArea()`函数中，我们可以看到`ValueError`是一个重复的错误类型——用户输入的是`string`而不是数值，因此 Python 无法执行数值运算。如果我们定制`try-except`块来适应这种常见的错误类型，并在完全忽略用户的输入之前给用户另一个机会，怎么样？

为此，我们可以专门为`ValueError`异常调用一个单独的代码块。在这里我们将检查或验证输入`type`以确保它只是`int`或`float`类型。否则，我们将继续提示用户输入一个数值作为输入。

为了简化验证过程，让我们定义一个名为`validate_input()`的函数——它将进行检查，如果输入变量是`float`类型，则返回`True`，否则返回`False`状态。

```
def validate_input(value):
    try: 
        value = float(value)
        return True
    except: return False
```

```
calcArea() ran successfully for 5
Area for input 5 = 78.53999999999999 
calcArea() run completed on 2022-03-24 10:36:57.001287

Input data is not numeric type.
Please input a numeric value: 8
Area for input 8 = 201.0624 
calcArea() run completed on 2022-03-24 10:37:00.426775

calcArea() ran successfully for 4
Area for input 4 = 50.2656 
calcArea() run completed on 2022-03-24 10:37:00.426775

calcArea() ran successfully for 8
Area for input 8 = 201.0624 
calcArea() run completed on 2022-03-24 10:37:00.426775

Input data is not numeric type.
Please input a numeric value: k
Please input a numeric value: 999
Area for input 999 = 3135319.9416 
calcArea() run completed on 2022-03-24 10:37:04.927187

calcArea() ran successfully for 0
Area for input 0 = 0.0 
calcArea() run completed on 2022-03-24 10:37:04.927187
```

为了定制对`ValueError`的响应，我们添加了一个专门的代码块来只捕获`ValueError`异常。在代码异常块内部，

*   我们正在给用户打印一条消息。
*   然后我们在一个循环中请求一个数字输入，直到输入类型是数字。
*   最后，在收到数字类型输入时，我们再次调用`calcArea()`。

注意一些事情，

📌我们将`ValueError`代码块放在了`Exception`代码块的上面。否则，我们的代码永远不会到达`ValueError`部分。因为它是 Exception 类的子类，所以它会被`Exception`代码块捕获。

📌我们没有在`ValueError`代码块中使用`ValueError as e`，但是**可以有**。因为我们不需要任何*类*属性来打印或用于其他用途，所以我们没有捕获 *TypeError* 类作为对象。

🛑考虑这样一个场景，你可能想要合并其他特定的*异常*类型。你将如何整合它们？

# 将异常理解为一个类

我在这篇文章中多次提到过*异常*是类，但是除了展示一些应用之外，并没有太多的细节。让我们在本节中尝试这样做。

> *在 Python 中，所有的*异常*都是从被称为* `*BaseException*` *的*类*中派生出来的。*

在`BaseException`下面，所有的内置异常被安排成一个层次结构。`BaseException`下的四个主要子类是:

*   系统退出
*   键盘中断
*   发电机出口
*   例外

我们通常关心或想要采取行动的异常是*异常*子类下的异常。*异常*子类又包含几组*子类*。下面是 Python 类的部分树层次结构。详情请参考来自 python.org 的官方文件。

```
BaseException
 +-- SystemExit
 +-- KeyboardInterrupt
 +-- GeneratorExit
 +-- Exception
      +-- StopIteration
      +-- StopAsyncIteration
      +-- ArithmeticError
      |    +-- FloatingPointError
      |    +-- OverflowError
      |    +-- ZeroDivisionError
      +-- AssertionError
      +-- AttributeError
      +-- BufferError
      +-- EOFError
      +-- ImportError
      |    +-- ModuleNotFoundError
      +-- LookupError
```

🛑你可以在这些类上运行用于检查公共类层次关系的方法来自己检查上面的层次结构。试试跑步，

*   `print(BaseException.__subclasses__())`:你应该看到`BaseException`类下的主要子类。
*   `print(issubclass(ValueError, Exception))`:你应该看到`True`作为返回值，因为`ValueError`是`Exception`的子类。

# 实现我们自己的异常

到目前为止，我们只使用了 Python 已经定义的异常。如果我们想要一个进一步定制的异常怎么办？为此，我们可以定义自己的异常类。

> *由于*异常*是*类*，我们可以像编写常规 Python* 类*一样编写自己的自定义*异常*类。*

在我们的例子中，假设我们希望将用户输入限制在一个可管理的范围内，这样用户就不能要求程序计算任意大半径的面积。出于演示的目的，假设我们想将其限制在`50`英寸以内。

我们可以通过在`calcArea()`函数中添加一个`if`条件来轻松做到这一点。但是使用`exceptions`有一种更好的方法。

# 编写自定义异常

对于我们的解决方案，我们将首先定义我们自己的异常类`Above50Error`。

```
class Above50Error(Exception):
    def __init__(self, value):            
        Exception.__init__(self)
        self.value = value

    def __str__(self):
        return "Input {} is larger than 50 inches".format(self.value)
```

`Above50Error`异常类被创建为内置*异常*异常*类*的子类，这样它就继承了所有的属性。

*   我们用一个参数初始化它:`value`，然后将它存储为一个名为`value`的类变量。
*   然后我们重写从异常类继承的`__str__()` *方法*来打印出一条定制消息。

注意，要打印出自定义消息，我们可以在初始化`Above50Error`时添加一条消息作为参数，并将其传递给`Exception`初始化。`Exception` *类*会将参数作为消息传递并自定义`__str__()`方法。但是我们用更长的方式实现它只是为了演示。

🛑试试看！修改`Above50Error`，使其不需要`__str__()`方法来打印消息。

🛑:还有，你能想出一个方法来确认`Above50Error`是否真的是`Exception`的子类吗？

要了解更多关于 Python 类和子类关系的知识，你可以查看我的帖子[Python 中的面向对象编程——继承和子类](https://curious-joe.net/post/2022-03-13-oop-python-inheritance-and-subclass/oop-python-inheritance-subclass/)

## 实现自定义异常

由于`Above50Error`是一个自定义异常，所以当我们想要将它注册为异常时，我们需要推动 Python 将其提升为异常。因此，当我们将代码放在一个`try-except`代码块中时，它可以将行为捕获为异常。为此，我们使用了`raise`关键字。

所以我们修改了`calcArea()`函数，添加了一个条件来检查输入值是否高于 50。如果是，它抛出`Above50Error`异常，否则继续计算面积。

```
def calcArea(radius):
    pi = 3.1416
    radius = float(radius)
    if radius > 50:
        raise Above50Error(radius)
    else: 
        area = pi * radius ** 2
    return area
```

```
calcArea() ran successfully for 5
Area for input 5 = 78.53999999999999 
calcArea() run completed on 2022-03-24 10:37:15.619721

calcArea() ran successfully for 5
Area for input 5 = 78.53999999999999 
calcArea() run completed on 2022-03-24 10:37:15.619721

Area couldn't be calculated for 55.
Error type: Above50Error 
Error msg: Input 55.0 is larger than 50 inches.
Area for input 55 = None 
calcArea() run completed on 2022-03-24 10:37:15.619721

calcArea() ran successfully for 4
Area for input 4 = 50.2656 
calcArea() run completed on 2022-03-24 10:37:15.619721

calcArea() ran successfully for 8
Area for input 8 = 201.0624 
calcArea() run completed on 2022-03-24 10:37:15.619721

Input data is not numeric type.
Please input a numeric value: k
Please input a numeric value: 7
Area for input 7 = 153.9384 
calcArea() run completed on 2022-03-24 10:37:20.308639

calcArea() ran successfully for 0
Area for input 0 = 0.0 
calcArea() run completed on 2022-03-24 10:37:20.308639
```

注意`Exception`的 except 代码块是如何捕获我们定制的*异常*的。在总结之前，让我们强调一下自定义异常类的一些特性:

*   自定义异常类类似于常规的内置异常类。例如，我们可以为`Above50Error`创建一个单独的 except 代码块，就像我们为`ValueError`所做的那样。试试看！
*   此外，由于这些是类，我们可以创建它们自己的子类，以便对错误和异常进行更多的定制。

# 下一步是什么？

这将是我的 Python 系列中面向对象编程的总结。在这个系列中，我试图解释:

*   [什么是 OOP，为什么要关注它？](https://curious-joe.net/post/2022-03-09-oop-in-python-what-why/oop-python-what-why/)
*   [了解一个类。](https://curious-joe.net/post/2022-03-11-oop-in-python-elements-of-class/oop-python-understanding-class/)
*   [理解这个概念在子类中的继承和应用。](https://curious-joe.net/post/2022-03-13-oop-python-inheritance-and-subclass/oop-python-inheritance-subclass/)
*   [在类上下文中理解 Python 变量。](https://curious-joe.net/post/2202-03-16-oop-python-variables-in-class/oop-python-inheritance-subclass/)
*   理解 Python 方法。

最后，在这篇博客中，我们深入探讨了 Python 异常，作为 Python 类的一个例子。

感谢您阅读这篇文章，希望这个博客系列能让您对 Python 中的面向对象编程有一个初步的了解。在未来的系列文章中，我们将踏上另一段旅程，进入 Python *类*的世界，并有更深入的理解。