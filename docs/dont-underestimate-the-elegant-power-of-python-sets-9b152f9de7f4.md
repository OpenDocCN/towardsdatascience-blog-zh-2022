# 不要低估 Python 集合的优雅力量💣

> 原文：<https://towardsdatascience.com/dont-underestimate-the-elegant-power-of-python-sets-9b152f9de7f4>

## 有用的小技巧！

## 快速学习 Python 集合的基础知识！

![](img/9eba0b922127e415ebda6b24005be1dd.png)

由 [David Clode](https://unsplash.com/@davidclode?utm_source=medium&utm_medium=referral) 在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄的照片

# 您的旅程概述

1.  [为什么要关心 Python 中的集合？](#2399)
2.  [创建器械包](#854e)
3.  [有用的设置方法](#9015)
4.  [速记符语法](#cf4a)
5.  [一套能放什么？](#c2a1)
6.  [收尾](#0b55)

# 1 —为什么要关心 Python 中的集合？

Python 中有四种基本的容器类型:

*   **列表:**Python 中的列表是可变序列，可以包含不同类型的数据。比如`dates = ["19-12-1922", "08-02-2005"]`。
*   **元组:**Python 中的元组类似于列表，只是它们不是可变的。它们的内部状态不会随着时间而改变。比如`seasons = ("Spring", "Summer", "Autumn", "Winter")`。
*   字典:Python 中的字典是键值存储，其中的键指向一个特定的值。一个例子是`age = {"Eirik": 27, "Grandma": 86}`。
*   **集合:**Python 中的集合是无序且可变的集合。最重要的是，集合只包含唯一的值。例如`emails = {"toy_email@gmail.com", "not_a_real_email@hotmail.com"}`。

在 Python 入门课程中，每个人都学习了列表、元组和字典。然而，Python 中的集合经常被忽略。一些初级数据专业人员认为集合更高级*或更深*或*。这不是真的！*

*Python 中的 set 非常实用，也没那么难学。在这篇博文中，我将或多或少地向您展示开始使用 Python 时需要知道的一切。*

*作为一个例子，在我们开始之前，考虑从下面的列表中提取唯一值的问题:*

```
*languages = ["Python", "R", "R", "SQL", "Python", "C", "SQL"]*
```

*你可以看到`Python`和`R`都被列了两次。要手动执行此操作，您可以执行以下操作:*

```
*languages = ["Python", "R", "R", "SQL", "Python", "C", "SQL"]# Manually:
unique_languages = []
for language in languages:
    if language not in unique_languages:
        unique_languages.append(language)*
```

*这工作得很好，但是它比需要的代码多得多。使用集合，您可以在一行可读的代码中轻松实现这一点:*

```
*languages = ["Python", "R", "R", "SQL", "Python", "C", "SQL"]# Manually:
unique_languages = []
for language in languages:
    if language not in unique_languages:
        unique_languages.append(language)

# With Sets
unique_languages = list(set(languages))*
```

*太棒了，对吧？如果你是一个视觉学习者，我制作了一个视频，涵盖了差不多相同的主题🔥*

> ***注意:**除了这里提到的四种类型，还有许多其他类型的容器。我写了一篇关于[数据类](/be-gone-boilerplate-code-master-dataclasses-in-python-d3f302f9a7c4)的博客，如果你想看的话，你可以看一下！*

# *2 —创建集合*

*在 Python 中创建集合的第一种方法是使用花括号，如下所示:*

```
*# Basic Syntax for Creating Sets
favorite_foods = {"Pizza", "Pasta", "Taco", "Ice Cream"}*
```

*现在，您已经创建了一个有四根弦的 set。集合可以包含不同的数据类型，但是在应用程序中，数据类型通常是相同的。在 Python 中创建集合的另一种方法是使用**集合构造函数**:*

```
*# Set Constructor
aweful_foods = set(["Tuna", "Tomatoes", "Beef", "Ice Cream"])*
```

*这里首先创建一个包含四个字符串的列表，然后将该列表传递给 set 构造函数。你可以想象上面两个例子的数据来自一项关于最喜欢和最不喜欢的食物的调查。*

*一般来说，如果你已经有了一个列表(或者另一个 iterable)中的数据，那么使用 set 构造函数可能是最简单的。*

*了解器械包会自动删除重复项是很重要的:*

```
*i_love = {"You", "You", "You", "You"}
print(i_love)**Output:** 
{"You"}*
```

*甜食😍*

> ***注意:**要创建一个空集，你不能给一个变量赋值`{}`。这将创建一个空字典。相反，使用`set()`创建一个空集。*

# *3 —有用的集合方法*

*集合上有一堆有用的方法。我想告诉你四个最重要的:*

## *向集合中添加元素*

*您可以使用`add()`方法向集合中添加元素:*

```
*favorite_foods.add("Chocolate")
print(favorite_foods)**Output:**
{'Ice Cream', 'Pasta', 'Pizza', 'Chocolate', 'Taco'}*
```

*回想一下，对于列表，有一个方法`append()`可以将一个元素追加到列表的末尾。集合没有顺序。因此 Python 的开发者选择使用名字`add()`而不是`append()`来强调这一点。*

## *合并两个集合*

*如果您有两组，那么您可以使用`union()`方法将它们组合起来:*

```
*all_foods = favorite_foods.union(aweful_foods)
print(all_foods)**Output:**
{'Tomatoes', 'Ice Cream', 'Tuna', 'Pasta', 'Pizza', 'Chocolate', 'Beef', 'Taco'}*
```

*这里，两个集合中的所有元素都被合并到一个新的集合中，称为`all_foods`。注意`"Ice Cream"`在`all_foods`中只出现一次，即使它同时出现在`favorite_foods`和`aweful_foods`中。Python 集合删除重复！*

## *寻找共同元素*

*如果你想找到两个集合共有的元素，那么你可以使用`intersection()`方法:*

```
*dividing_foods = favorite_foods.intersection(aweful_foods)
print(dividing_foods)**Output:**
{'Ice Cream'}*
```

*如您所见，`intersection()`方法挑选出两个集合中的元素。如果你有两组投票，想找出两组都投了什么，这个方法真的很有用。*

## *寻找差异*

*给定两个集合，您通常希望找到第一个集合中不在第二个集合中的元素。为此，您可以使用`difference()`方法:*

```
*likable_foods = favorite_foods.difference(aweful_foods)
print(likable_foods)**Output:** {'Pizza', 'Pasta', 'Taco', 'Chocolate'}*
```

*在上面的代码示例中，`aweful_foods`中的每个元素都已从集合`favorite_foods`中移除。*

## *另一个例子*

*让我们再做一个例子，这样你就可以看到集合是多么有用。假设您有以下两个编程学习平台列表:*

```
*platforms = ["Udemy", "Coursea", "YouTube", "DataCamp", "YouTube"]
paid_platforms = ["Udemy", "Coursea", "Skillshare", "DataCamp"]*
```

***现在说想找免费的平台。**你会怎么做？使用集合，您可以简单地编写:*

```
*print("Free: ", set(platforms).difference(set(paid_platforms)))**Output:**
Free:  {'YouTube'}*
```

# *4-速记运算符语法*

*![](img/832bf7ec7e828747f9a527dd226dd7a4.png)*

*[Jippe Joosten](https://unsplash.com/@jippe_joosten?utm_source=medium&utm_medium=referral) 在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄的照片*

*在上一节中，我向您展示了一些很酷的方法。但是你知道还有`union()`、`intersection()`和`difference()`的简写吗？**简写操作符语法**更容易记忆和阅读。这里您可以看到一个同时包含四个运算符的代码示例:*

```
*print("Union: ", favorite_foods | aweful_foods)
**Output:** Union: {'Tomatoes', 'Ice Cream', 'Tuna', 'Pasta', 'Pizza', 'Chocolate', 'Beef', 'Taco'}print("Intersection: ", favorite_foods & aweful_foods)
**Output:** Intersection: {"Ice Cream"}print("Difference: ", favorite_foods - aweful_foods)
**Output:** Difference: {'Pizza', 'Pasta', 'Taco', 'Chocolate'}*
```

*我个人更喜欢简写的操作符语法。也超级直观！例如，在编程语言中，符号`&`通常代表`and`布尔组合器。`and`布尔组合器的工作方式与交集相同。其他两个例子也很容易得出类似的结论。*

# *5 —你能在一套中放些什么？*

*让我问你一个简单的问题。你能在一套中放什么样的物体？你可能认为答案是*任何东西*。然而，事实并非如此。考虑如果您尝试运行以下代码会发生什么:*

```
*invalid_set = {[1, 2, 3], "Good try, though"}**TypeError**: unhashable type: 'list'*
```

*如您所见，如果您试图将一个列表放入一个集合中，Python 会抛出一个`TypeError`。原因是一份名单不是**所能公布的**。解释 hashable 最精确(但最没帮助)的方式是可以在 hashable 对象上调用`hash()`函数。在实践中，你通常需要知道的是不可变对象是可散列的。然而，并不是所有的可散列对象都是不可变的。*

*因此，您可以确定任何不可变的东西(例如整数、字符串和元组)都可以放入集合中。但是，将列表和字典放入集合是不可能的。您也可以不将一个集合放在另一个集合中:*

```
*nested_set = {1, set([2]), 3}**TypeError**: unhashable type: 'set'*
```

# *6—总结*

*![](img/96d9a560ecb3e0a5fc51c9866e494f7a.png)*

*照片由[斯潘塞·伯根](https://unsplash.com/@spencerbergen?utm_source=medium&utm_medium=referral)在 [Unsplash](https://unsplash.com/?utm_source=medium&utm_medium=referral) 上拍摄*

*希望您对 Python 中的集合感觉更舒服。如果你对数据科学、编程或任何介于两者之间的东西感兴趣，那么请随意在 LinkedIn 上添加我，并向✋问好*

***喜欢我写的？查看我的其他帖子，了解更多 Python 内容:***

*   *[用漂亮的类型提示使你罪恶的 Python 代码现代化](/modernize-your-sinful-python-code-with-beautiful-type-hints-4e72e98f6bf1)*
*   *[用 Python 可视化缺失值非常简单](/visualizing-missing-values-in-python-is-shockingly-easy-56ed5bc2e7ea)*
*   *[使用 PyOD 在 Python 中引入异常/离群点检测🔥](/introducing-anomaly-outlier-detection-in-python-with-pyod-40afcccee9ff)*
*   *[5 个能在紧要关头救你的牛逼数字功能](/5-awesome-numpy-functions-that-can-save-you-in-a-pinch-ba349af5ac47)*
*   *[5 个专家提示，让你的 Python 字典技能突飞猛进🚀](/5-expert-tips-to-skyrocket-your-dictionary-skills-in-python-1cf54b7d920d)*