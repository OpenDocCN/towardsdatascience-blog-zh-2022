# Python 中每一个令人敬畏的内置函数

> 原文：<https://towardsdatascience.com/every-single-awesome-built-in-function-in-python-f36a23842954>

# Python 中每一个令人敬畏的内置函数

## 看看这种语言已经提供的一些最好的 Python 方法，以及如何使用它

![](img/49d0a9574ecf002f06a411caf996a6e1.png)

(图片由 [Pixabay](http://pixabay.com) 上的 [Viki_B](https://pixabay.com/images/id-5811382/) 提供)

# 介绍

ython 以其 C 解释的和类似英语的语法荣耀，已经在机器学习领域运行了几年。令人惊讶的是，一种可以用世界上最有影响力和最强大的编程语言之一轻松编写的高级解释脚本语言在机器学习方面表现出色。就语言和科学计算而言，Python 的成功是当之无愧的，也是不言自明的。

虽然 Python 是一种相对容易掌握的语言，读起来像英语，语法简单，但它可能很难掌握。Python 编程语言在某些领域有很大的深度，不断接触新的模块和工具以了解更多他们碰巧正在学习的东西是很棒的——这就是计算的乐趣。外面有这么多东西，没有一个人不能探索新的东西。总是有更多的东西要学，所以热爱学习的人应该考虑数据科学或某种软件工程的职业生涯，这很有趣，而且很多人没有意识到这是非常有创造性的。

有了这种艺术，总有办法提高你的技术。为了说明这一点，我想介绍一个场景。:在我们所有的开发者故事和数据科学旅程中，有一段时间我们遇到了另一个比我们优秀得多的程序员。最棒的是我们有一个极好的机会去学习，不好的是当我们觉得我们不知道我们在做什么，因为

> 他/她/他们只是把我的 20 行互相嵌套的循环变成了一行方法调用。

好吧，不管怎样，也许这只是我早期和我的一个老师经历过的一个场景——但是情况表明，在你的武器库中拥有一堆方法和这些方法的小技巧是很重要的。对于 Python 来说尤其如此，我将这种语言描述为在对象旁边有一个非常有条理的生态系统。我最近写了一篇关于我最喜欢的 Python 装饰者的文章。这让我开始思考，我最喜欢的东西是什么…只是 Python..？我认为它的包装让它变得很棒。我首先想到的是标准库中令人惊奇的选择方法，这些方法总是很有用。如果你想阅读我关于装饰者的文章，这里有一个链接:

[](/10-of-my-favorite-python-decorators-9f05c72d9e33) [## 我最喜欢的 10 个 Python 装饰者

### Python 编程语言中更多优秀装饰者的概述。

towardsdatascience.com](/10-of-my-favorite-python-decorators-9f05c72d9e33) 

不断接触新的做事方法是很棒的，今天我们将回顾一些我一直以来最喜欢的方法，

> 你可能没有注意到他们。

我们将讨论 Python 编程语言中的所有内置函数。这不包括用 Python 打包的标准库中的那些。这些功能的伟大之处在于它们总是在那里帮助你。另外，对于那些想自己尝试这段代码的人来说，这里是这篇文章的笔记本:

[](https://github.com/emmettgb/Emmetts-DS-NoteBooks/blob/master/Python3/essential%20and%20builtin%20python%20funcs.ipynb) [## Emmetts-DS-NoteBooks/essential 和内置 python funcs.ipynb at master …

### 各种项目的随机笔记本。通过创建帐户，为 emmettgb/Emmetts-DS 笔记本电脑的开发做出贡献…

github.com](https://github.com/emmettgb/Emmetts-DS-NoteBooks/blob/master/Python3/essential%20and%20builtin%20python%20funcs.ipynb) 

# №1: abs()

abs()方法是一种内置于 Python 核心的方法。我记得在我早期的编程经历中，当我还是一个小孩子的时候，看到各种语言中一直在使用 abs()，但不知道它是什么意思。因此，假设我们中的许多人都使用过这种方法，或者至少以前在某人的代码中见过它，这可能是明智的。这个方法到底是做什么的，这个方法的一些常规用法是什么？

abs()中的 abs()是 absolute 的简称。该函数返回两个数值之间的绝对距离。这些术语中的距离是数字上远离零的索引，例如，你离零有多少个数字，你们之间有什么。假设列表中有两个项目:

```
list = [5, -32]
```

如果我们想计算 5 是否在-32 的 3 以内，您首先需要将-32 转换为它的正等效值，然后将这两个值相减。要做到这一点，我们需要找出这个数字是否是负数，如果是，那么我们将不得不看看我们的数字是小于它还是大于它，等等。最后变成了一堆条件句。然而，有了 abs，

```
abs(5 - 32)27
```

> 那就简单多了。

# №2:任何()

我们今天要看的第二个方法是 any()方法。any()方法可以用于许多不同的事情，通常用于列表，尽管它意味着接受任何 iterable。any 方法只是简单地检查列表的所有索引是真还是假。如果任何元素为真，它将返回 true。如果所有的元素都是假的，它将返回假。如果没有元素，它将返回 false。

```
any([True, False, True]) any([False, False])False any([])False
```

让我们把这纳入一个使用概念，我们将首先考虑以下功能:

```
def check_list(lst : list):
    if any(lst):
        print("there is now a value")
```

这个函数检查一个列表，看看里面是否有任何东西。这是一个更干净的选择，如果有的话，只调用(list)而不是

```
if len(lst) > 0:
    print("There is now a value")
```

但是，在这种情况下，any()方法有一些重要的问题需要考虑，

> 性能。

第二个例子可能没有那么漂亮，但是由于 any 方法的迭代性质，它可能会更快。也就是说，这个模块有很多很酷的应用程序，所以我肯定会在库中保留一个标签，以防这种用例在您的工作中发生。

# ascii()

ascii 方法提供了 Python 字符的可打印版本。也就是说，扩展的 ascii 是一种全球计算标准，例如，要让打印机正确地读取整数，而不是作为字符读取，它们需要加上 48 才能正确地驻留在 ascii 表上。基本上，这个函数可以用来将标准的 Python 字符转换成 ascii 标准。

```
ascii("hello")
"'hello'"
```

# bin()

bin 方法只是将一个值(由于某种原因不能是 char)返回到一个字节的数据中。

```
bin(50)
'0b110010'
```

如果您正在从 Python 中控制汇编代码，这可能是有用的，但是该事件的可能性在统计上可能并不显著。很有可能这在 Python 中完全没用。

# 可调用()

如果对象是可调用的，callable()方法返回 true，否则返回 false。我认为这个函数的真正用途最初来自于产生“_ 不可调用！”错误。然而，它可能对一些在你自己的软件中相似的应用程序有用，所以这是一个值得注意的功能。

```
callable(5)
False
```

# 编译()

compile()方法只是编译一个添加的参数 python 文件。我们可以编译一串 Python。然后将这个编译后的 Python 放入一个可以执行的对象中。

```
code = 'sum([5, 10, 15])'
codeObeject = compile(code, 'sumstring', 'exec')exec(codeObeject)
```

对象的类型是我们的变量名:

```
type(codeObject)
code
```

# 枚举()

enumerate 方法将接受一个 iterable，并返回对应于每个索引的索引位置的键。每当我们需要循环计数，或者需要我们处理的每个值的索引时，这通常在 for 循环中使用。

```
for index, val in enumerate([5, 10, 15]):
    print(index, "\n", val)0 
 5
1 
 10
2 
 15
```

在这里，我只是打印了每个值，每个值之间有一个\n，它开始一个新行。非常简单，但是很容易看出这种方法的应用领域。也就是说，enumerate 有很多不同的用例，它肯定是 Python 的一个功能。也就是说，我强烈建议选择这个来提高自己的 Python 技能。这可能是这个列表中为数不多的方法之一，实际上我可以自信地说我每天都在使用它，所以有了这种用处，就很容易明白为什么我推荐使用它了。

# 静态方法()

staticmethod 函数实际上是一个非常酷的函数，可以用来从 Python 中移除一些范例。我们可以调用面向对象类的函数来创建一个公共的全局版本。实际上，这意味着我们可以有条不紊地上课。

```
class Adder:def add_numbers(num1, num2):
    return num1 + num2Adder.add_numbers = staticmethod(Adder.add_numbers)tot = Adder.add_numbers(5, 7)
print(tot)
```

最棒的是，我们不再需要用我们的类创建一个新的类型，我们可以直接调用这个方法。当你有一个私有方法时，这是很方便的，但是你更希望它是全局的，特别是当你不是写这样一个类的人的时候。

# 过滤器()

filter()方法与几乎所有其他编程语言中的 filter()方法非常相似。该方法可用于根据“掩码”过滤 iterable 掩码只是位数组的高级名称。位数组只是一个位的数组，意味着一个带索引的位的集合。一个位只是一个真/假值，通常是 1 或 0。换句话说，一个位数组只是一个布尔数组，或者一个二进制数组，例如…

```
[0, 1, 0, 1, 1, 0, 1, 0]
```

为了使用 filter()方法进行过滤，我们只需创建一个过滤函数——或表达式。我们也可以像上面一样用一个位数组来实现，但是我将使用一个函数，因为这在 Python 约定中似乎更典型:

```
def filter_func(x):
    if x < 5:
        return(False)
    else:
        return(True)
```

现在让我们制作一个数组来使用:

```
d = [1, 3, 5, 7, 9, 11]
```

最后，我们可以通过 filter()方法传递它。然而，这个函数的输出可能不是您所期望的:

```
z = filter(filter_func, d)<filter at 0x7fb7851834f0>
```

我们得到的不是过滤后的数组的返回，而是一个过滤器对象。filter 对象是预过滤元素的迭代器。为了演示如何使用一个简单的 for 循环，我将把它们拿出来:

```
vals = [w for w in z]
print(vals)[5, 7, 9, 11]
```

# 格式()

Python 中的一个对数据科学应用程序非常有用的函数是 format()方法。这个方法可以用一个简单的 char 将任何值转换成给定的格式。例如，我们可以使用以下语法将值. 5 转换成百分比:

```
x = .5
fifty_percent = format(x, '%')
```

我对这个函数的唯一看法，更具体地说，它在数据科学中的应用，是这个新格式化值的数据类型是**而不是**。我觉得这多少破坏了这个功能的价值。例如，如果有一个百分比类型，我们的值随后被转换为百分比类型，这也很好，但是看看我们得到的类型:

```
print(type(fifty_percent))
print(fifty_percent)<class 'str'>
50.000000%
```

虽然有点不足，但是，在很多情况下，这个函数都可以派上用场——而且在基本 Python 中，它肯定是值得了解的。

# getattr()

getattr()是一个相当简单的方法，但是它可以用于许多不同的事情。一般来说，它并不完全用于标准的 Python 操作，但是，在某些情况下，它肯定会派上用场。考虑我们以前的加法器类，但是现在有了更多的数据:

```
class Adder:
    numbers_added = 0
    def add_numbers(num1, num2):
        self.numbers_added += 1
        return num1 + num2
```

我们现在可以使用 getattr()方法获得 numbers_added 属性:

```
ouradder = Adder()added = getattr(ouradder, "numbers_added")print(added)0
```

我认为这可以派上用场的地方是第三个位置参数，默认。该参数允许设置默认值。举一个更奇怪的例子，假设我们已经编写了一个完整的游戏，这两个类是我们的元素:

```
class Player:
    hp = 1class Bush:
    def __init__(self, size):
        self.size = size
```

玩家职业有属性 hp，但是灌木没有生命值，所以它没有。现在让我们假设我们有一个方法来检查游戏中所有对象的健康状况，就像这样:

```
def check_hp(x):
    print(x.hp)
```

如果我们让一个玩家通过这个新方法，一切都很好:

```
check_hp(Player())1
```

然而，由于 Bush 类型没有属性 hp，一旦我们在 Bush 上尝试，我们将得到一个恰当命名的**属性错误**:

```
check_hp(Bush(5))AttributeError: 'Bush' object has no attribute 'hp'
```

我们可以通过使用 getattr()方法减轻这种情况，并提供一个默认值零。

```
def check_hp(x):
    hp = getattr(x, "hp", 0)
    print(hp)check_hp(Bush(5))0
```

现在，一个完整的玩家和灌木丛列表可以毫无问题地调用这个方法，而且它会忽略那些没有这个属性的类。

# 全局()

globals()方法只是返回当前全局范围内所有全局定义的别名的字典。

```
x = globals()
print(x){'__name__': '__main__', '__doc__': 'Automatically created module for IPython interactive environment', '__package__': None, '__loader__': None, '__spec__': None, '__builtin__': <module 'builtins' (built-in)>, '__builtins__': <module 'buil...............
```

这在某些情况下非常有用，尤其是在跟踪给定全局范围的状态非常重要的情况下。

# 哈希()

正如所料，hash()方法返回给定 Python 对象的散列值。这有许多应用，并被广泛用于根据本质上并不完全唯一的 UUID 来跟踪代码中的对象。除了唯一性之外，唯一的区别是 UUID 的 hash()版本也是…

> 数据。精彩，漂亮，数据。

也就是说，UUID 的值通常是任意的并且完全唯一，而散列的值遵循特定的散列算法(散列函数)。)这通常应用于密码术中，因为散列经常被用作存储或传输信息的私有方式。把它想象成一把锁，哈希是数据上的锁，哈希函数是打开锁的钥匙。

# iter()

iter()方法非常有用。它可以用来从任何类型的 iterable 中快速创建一个迭代器，如果一个特定的类型在其定义中没有绑定 __iter__ default 函数，这将非常方便。

```
mylist = iter(["spaghetti", "onions", "celery"])
```

此外，它还可以和其他方法一起使用，比如下面的例子:

# 下一个()

next()方法可用于返回迭代器的下一个值。这可以用在任何类型的迭代器上。它可以用来构建你自己的全局类型的循环，这非常棒。在迭代时，您可以有效地定义全局值，而不必受限于 for 循环的边界。

```
mylist = iter(["spaghetti", "onions", "celery"])
x = next(mylist)
print(x)
x = next(mylist)
print(x)
x = next(mylist)
print(x)spaghetti
onions
celery
```

# 反转()

这个方法真的很简单，但是很有用。这个函数的结果在 Python 语言中随处可见。如果你熟悉 reverse 或 rev 是你正在使用的方法中的一个关键词参数，那就太惊讶了！一直以来，您都在使用依赖于 Python 基础上的这个方法的函数调用！

```
mylist = reversed(["spaghetti", "onions", "celery"])
x = next(mylist)
print(x)
x = next(mylist)
print(x)
x = next(mylist)
print(x)celery
onions
spaghetti
```

# 切片()

slice()方法也是处理集合的一个非常棒和有用的方法。该方法可用于选择给定 iterable 的特定索引。我们可以使用 start 参数选择单个，或者使用 start 和 stop 参数选择一个范围:

```
a = [5, 10, 15]
x = slice(1, 2)
print(a[x])
[5, 10]
```

我们还可以使用 step 参数更进一步。这个参数将从开始到结束取那个间隔，并且只返回那些值。在这里，我使用精确的方法得到字母表中的每三个字母:

```
# Every third letter
a = ("a", "b", "c", "d", "e", "f", "g", "h")
x = slice(1, len(a), 3)
print(a[x])
```

# 结论

Python 编程语言是一种因其高级本质而广受尊崇的语言，这肯定是有道理的。这些方法中有很多展示了高级 Python 如何获得一些开箱即用的相当激进的能力。所有这些都很容易使用，这是一个优势。在这种情况下，知道就已经成功了一半！感谢您阅读我的文章，我很高兴能够为您的 Python 技能做出贡献！