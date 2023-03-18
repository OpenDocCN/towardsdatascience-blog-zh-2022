# Python 的 Map()、Filter()和 Reduce()函数解释

> 原文：<https://towardsdatascience.com/pythons-map-filter-and-reduce-functions-explained-2b3817a94639>

## **用代码示例、数学和表情符号展示 Python 中函数式编程的构建模块**

![](img/d78ea7a3bf325e1491c6eac8bf99ab9d.png)

Filter()是 Python 中可以使用的三个高阶函数之一，它允许为您的代码注入函数式编程结构

从根本上说，Python 是一种**面向对象的编程语言**，建立在命令式编程范式之上。当执行一系列语句时，通常使用如下结构(for-loop ):

```
my_list= [17.43, -0.99, 6.81, -12.25, 4.52]
my_list_squared = []for i in my_list:
    i_squared = i**2
    my_list_squared.append(i_squared)
```

通过对感兴趣的对象(原始列表)执行操作，每条语句都使我们离期望的最终结果(在本例中是平方数列表)更近了一步。

或者，我们可以构建一个**列表理解**来用更少的代码行完成同样的任务:

```
my_list_squared = [i**2 for i in my_list]
```

在这两种情况下，*数据*是中心，对`my_list` 执行重复操作以达到结束状态。

在函数式编程中，事情有点不同。与 OOP 不同，它依赖于声明性编程模型，其中*函数*是核心。尽管**不是函数式编程语言**，Python 确实包含了几个强大的函数来迎合这种类型的编程。

在**功能表**中，使用`map()`功能，上述程序如下所示:

```
my_list_squared = list(map(lambda i: i**2, my_list))
```

本文(非常)简要地讨论了函数式编程的概念及其潜在的好处，并描述了在 Python 中应用函数式编程原则的三个关键构建块——`map()`、`filter()`和`reduce()`函数。

# **什么是函数式编程？**

函数式编程的本质属性是它强调我们执行的操作，而不是我们执行操作的对象。对于我们在相对有限数量的对象上执行**许多不同操作**(即许多功能)的问题，这可能是首选的编程范例。

函数式编程的核心是**高阶函数**。这些函数接受另一个函数作为输入，使它们成为强大的通用表达式。用数学术语来说，人们可以认为是一个导数 *d/dx* ，以函数 *f* 作为输入。本文讨论了 Python 中可以使用的三个关键高阶函数:`map()`、`filter()`和`reduce()`。

尽管首选方法严重依赖于问题，但函数式编程比面向对象编程有几个(潜在的)好处。每个函数代表一段独立的代码。它接受输入，转换输入，然后输出。这种简洁的模块化结构通常可以简化调试和维护。此外，其固有的惰性评估(仅在请求时产生输出)可以更加节省内存。最后，函数式编程通常会简化并行化。

当使用**许多数据操作和少量“事物”**(例如，相对少量的变量、集合等)时，函数式编程可能更可取。).相比之下，当“事情”很多但操作相对较少时，OOP 往往会工作得更好。请记住，两者通常都能完成工作，并且许多编程语言都包含了两者的元素。

虽然越来越受欢迎，但与 Python 或 C++等广泛使用的 OOP 语言相比，LISP 或 Haskell 等函数式语言的采用有限。然而，OOP 语言越来越多地**结合了函数式编程**的元素，从而可以应用类似的结构。

既然已经介绍了函数式编程的基础，是时候转向具体的 Python 实现了。

# **地图()**

作为高阶函数，map 函数将另一个**函数和一个可迭代的**(例如，列表、集合、元组)作为输入，将该函数应用于可迭代的，并返回输出。它的语法定义如下:

> 映射(函数，可迭代)

对于那些喜欢数学的人来说，考虑从域 *X* 到域 *Y* 的映射可能更方便:

> f:X →Y

或者:

> f(x)=y，∀x∈X

对于视觉学习者来说，一个 map() — *的表情符号示例归功于*[*global nerdy*](https://www.globalnerdy.com/2016/06/23/map-filter-and-reduce-explained-using-emoji/)*对于灵感*——可能更有帮助:

> *地图(库克，[* 🐷*，🌽，*🥚,🍠 *]) → [* 🥓*，🍿，*🍳,🍟

*输出 *y* 是一个 **map 对象**(一个 iterable)，我们仍然需要将它转换成一个集合或列表。要结合这两个步骤，我们可以简单地将 map 语句包装在里面，例如，`set()`函数:`my_set=set(map(function, iterable))`。*

*让我们举一个具体的例子。假设我们有大量的字符串，我们想用**将**和 *"_2022"* 连接起来。数据科学充满了这种需要在大型数据集上执行的相对简单的操作。对于`map()`，我们可以表达为*

```
*string_map_22 = map(lambda my_string: my_string + '_2022', set_of_strings)*
```

*这种工作方式非常强大——只需一下子，我们就可以更新整个集合！但是不要忘记将贴图对象转换为集合:*

```
*set_of_strings_22 = set(string_map_22)*
```

*再来一杯？假设我们想在一个薪水列表上转换一个**对数转换**。尽管使用 lambda 函数会产生简洁的代码，但为了提高效率，建议**使用`def`来预定义函数**。此外，我们现在直接将`map()`函数包装在一个`list()`函数中:*

```
*def get_log_value(salary: int):
    return np.log(salary)log_salaries = list(map(get_log_value, salaries))*
```

# ***过滤器()***

*与`map()`类似，`filter()`高阶函数将一个函数和一个可迭代函数作为输入。该函数需要具有**布尔性质**，返回与过滤条件相对应的真/假值。作为输出，它返回满足函数规定的条件的输入数据的子集。*

*从数学上讲，过滤操作可以大致指定如下:*

> *f:X →X '，带 X'⊆X*

**(更具体地说，我们可能会定义一个布尔向量来剔除集合中的假值元素，但这里让我们保持简洁)**

*回到食物的例子，假设我们定义了一个过滤函数`non_vegan()`。然后，我们可以应用以下过滤器:*

> *过滤器(非素食者，[🥓,🍿,🍳,🍟]) → [🥓,🍳]*

*我们再来看一个例子。假设我们有一个包含 tweets 的数据帧，并希望**过滤 retwetes**(由 tweets 的前两个字符*‘RT’*表示)。我们可以这样做:*

```
*def check_retweet(tweet: str):
    return tweet[:2]=='RT'list_retweets = list(filter(check_retweet, tweets_df['Tweet text']))*
```

*很漂亮，对吧？*

# ***减少***

*与前两个函数不同，`reduce()`必须从`functools`导入才能正常工作。它返回单个值(即，*减少*单个元素的输入)。通常，这是一个列表中所有元素的总和。*

*事实上，Python 3 中没有内置`reduce()`的原因就是它通常只是用来计算总和。根据 Python 创始人 Van Rossum 的说法:*

> *“我最终讨厌 reduce()，因为它几乎专门用于(a)实现 sum()，或者(b)编写不可读的代码。所以我们添加了 builtin sum()，同时将 reduce()从 builtin 降级为 functools 中的某个东西(这是一个我并不真正关心的东西的垃圾场:-)”*

*数学表示:*

> *外宾:→ℝ*

*表情符号的例子:*

> *减少(混合，[🥬，🥕,🍅,🥒]) →🥗*

*如上所述，reduce 函数通常用于对列表中的所有元素求和或相乘的操作，如**。让我们看看乘法器的实现:***

```
*from functools import reduceproduct = reduce(lambda x, y: x*y, list_integers)*
```

*同样，执行该操作只需要很少的代码。*

*对于所有三个高阶函数，都有更深奥的用例(例如，将多个迭代器作为输入、嵌套结构)，但这些超出了这篇介绍性文章的范围。*

# ***结束语***

*函数式编程将*函数*——而不是*对象*——置于编程实践的核心。尽管 Python 主要是一种面向对象的语言，但是三个**高阶函数** — `map()`、`function()`和`reduce()` —对利用 Python 中的函数式编程概念大有帮助。每个都接受一个函数和一个 iterable 作为输入。让我们再回顾一遍:*

*   ***Map()** :对一个 iterable 中的所有元素执行相同的操作。一个例子是对每个元素执行对数转换。*
*   ***Filter()** :过滤满足特定(一组)条件的元素子集。一个例子是过滤出包含特定字符串的句子。*
*   ***Reduce()** :对可迭代对象执行运算，产生单值结果。一个常见的例子是对列表中的所有元素求和，产生一个数字作为输出。*

*和许多问题一样，没有放之四海而皆准的解决方案。大问题是:**Python 中什么时候使用函数式编程？**如前所述，有些情况下函数式编程是最合适的。然而，如果我们致力于 Python，具体什么时候我们会采用本文中讨论的功能呢？*

*老实说，不经常。列表理解通常(实质上)更快，而且——有点武断——更容易阅读。此外， **NumPy 操作**通常在大型重复数组操作方面更胜一筹。很可能，大多数 Python 程序员永远不会*需要*来使用本文中列出的函数(反高潮，我知道)。*

*最终，Python——尽管提供了一些更高级的函数——只是**不是函数式编程语言**。它不是那样设计的。在赛车上拍打泥土轮胎并不能使它成为拉力赛车。Python 没有能最大限度发挥函数式编程优势的编译器，因此也没有纯函数式语言的优势。*

*最后一次引用范·罗森的话:*

> *“如果我想到函数式编程，我通常会想到拥有强大编译器的语言，比如 Haskell。对于这样一个编译器来说，函数范式是有用的，因为它提供了大量可能的转换，包括并行化。但是 Python 的编译器不知道你的代码意味着什么，这也是有用的。所以，我认为尝试在 Python 中添加“函数式”原语没有多大意义，因为这些原语在函数式语言中工作良好的原因并不适用于 Python，并且它们使得不习惯函数式语言的人(也就是大多数程序员)很难读懂代码。*
> 
> *我也不认为当前的函数式语言已经为主流做好了准备。诚然，除了 Haskell 之外，我对这个领域了解不多，但是任何不如 Haskell 受欢迎的语言肯定都没有什么实用价值，我也没有听说过比 Haskell 受欢迎的函数式语言。至于 Haskell，我认为它是关于编译器技术的各种想法的一个很好的试验场，但我认为它的“纯度”将永远保持在被采用的道路上。对大多数人来说，不得不与单子打交道是不值得的。"*

# ***延伸阅读***

*[](https://www.analyticsvidhya.com/blog/2021/07/python-most-powerful-functions-map-filter-and-reduce-in-5-minutes/) [## Python 最强大的函数:map()，filter()，reduce()5 分钟-

### 这篇文章是作为数据科学博客的一部分发表的。这些功能不仅使…

www.analyticsvidhya.com](https://www.analyticsvidhya.com/blog/2021/07/python-most-powerful-functions-map-filter-and-reduce-in-5-minutes/) [](https://developers.slashdot.org/story/13/08/25/2115204/interviews-guido-van-rossum-answers-your-questions) [## 采访:吉多·范·罗苏姆回答你的问题

### 上周你有机会问吉多·范·罗苏姆，Python 的 BDFL(仁慈的终身独裁者)，关于所有的事情…

developers.slashdot.org](https://developers.slashdot.org/story/13/08/25/2115204/interviews-guido-van-rossum-answers-your-questions) [](https://www.learnpython.org/en/Map%2C_Filter%2C_Reduce#:~:text=Map%2C%20Filter%2C%20and%20Reduce%20are,intricacies%20like%20loops%20and%20branching) [## 地图、过滤、归约-学习 Python -免费的交互式 Python 教程

### 映射、过滤和归约是函数式编程的范例。它们允许程序员(你)写得更简单…

www.learnpython.org](https://www.learnpython.org/en/Map%2C_Filter%2C_Reduce#:~:text=Map%2C%20Filter%2C%20and%20Reduce%20are,intricacies%20like%20loops%20and%20branching) [](https://www.educba.com/functional-programming-vs-oop/) [## 函数式编程与面向对象编程|需要了解的 8 大有用差异

### 函数式编程是一种编程技术，它强调了创建和修改

www.educba.com](https://www.educba.com/functional-programming-vs-oop/) [](https://www.knowledgehut.com/blog/programming/python-map-list-comprehension) [## Python 地图 vs 列表理解哪个更好？

### 有许多内置的方法、数据结构和模块来获得想要的输出。当我们编写一个巨大的代码时…

www.knowledgehut.com](https://www.knowledgehut.com/blog/programming/python-map-list-comprehension)  [## 函数式编程指南- Python 3.10.6 文档

### 在本文档中，我们将浏览 Python 适合以函数式风格实现程序的特性…

docs.python.org](https://docs.python.org/3/howto/functional.html)*