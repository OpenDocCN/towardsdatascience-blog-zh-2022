# Python 并发性——多重处理

> 原文：<https://towardsdatascience.com/python-concurrency-multiprocessing-327c02544a5a>

## Python 并发系列的第 2 部分。多重处理模块使我们能够执行真正的并行任务。然而，有许多事情需要注意。

![](img/cd93b4c10d86dc2a0e63e1d92d705c0d.png)

照片由 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上的[尼克·费因斯](https://unsplash.com/@jannerboy62?utm_source=medium&utm_medium=referral)拍摄

## 浏览 Python 并发系列:

*上一篇:*

[](/python-concurrency-threading-and-the-gil-db940596e325) [## Python 并发性——线程和 GIL

### Python 并发系列的第 1 部分。线程是全局解释器锁(GIL)

towardsdatascience.com](/python-concurrency-threading-and-the-gil-db940596e325) 

*接下来的故事:*

[](/python-concurrency-concurrent-futures-15b56dc9a14d) [## Python 并发性——concurrent . futures

### Python 并发系列的第 3 部分。多线程和多处理带来的界面简单性。

towardsdatascience.com](/python-concurrency-concurrent-futures-15b56dc9a14d) 

多处理宣传多核心使用。是不是很多 Python 用户祈祷的答案？是最终绕过 [GIL](/python-concurrency-threading-and-the-gil-db940596e325) 的方法吗？

首先，这并不新鲜。现在其实已经挺老了。早在 2008 年，Python 2.6 就引入了*多处理*模块。

事实上，我们可以将不同的任务提交给在不同内核中同时执行的不同操作系统进程。然而，这可能不是我们期望的解决方案。有两个主要原因:

*   我们首先需要编写并行代码，在多个内核中运行计算。也就是说，将一个较大的任务分成许多可以并行执行的较小的作业。这样的努力并不总是可能的。
*   设计多进程应用程序时，许多细节需要微调。实现流程之间的协调、通信和同步不是一件容易的事情。

在这个故事中，我们将介绍流程创建和流程间数据共享的基础知识，同时指出哪里可能出错、如何出错以及如何避免出错。故事的最后一部分致力于一个激动人心的话题:多进程和[多线程](/python-concurrency-threading-and-the-gil-db940596e325)。

## 故事结构

*   加速一个过程
*   子进程和守护进程
*   上下文
*   跨流程共享变量
*   竞争条件和锁
*   队列和管道
*   进程池
*   进程间数据交换的性能
*   多处理+多线程？？？
*   这个故事的寓意

## 加速一个过程

如果你熟悉*线程*模块，当你使用*多重处理*模块时，你会有宾至如归的感觉。相似概念的接口几乎相同。一个恰当的例子是加速一个新过程的方法:

> 做事…
> 事情做完了

*进程*对象的初始化参数与*线程*对象中的基本相同。主要区别在于，我们需要使用习语来启动新流程:

`if __name__ == ‘__main__’:`

否则，我们会得到一个 RuntimeError，除非是在使用`fork`上下文时(我们将在下一节讨论更多关于上下文的内容)。

与线程不同，我们可以创建许多真正并行的进程:

> 1 做事…
> 0 做事…
> 2 做事…
> 4 做事…
> 3 做事…
> 1 做事
> 0 做事
> 2 做事
> 4 做事
> 3 做事

这是正确的； [GIL](/python-concurrency-threading-and-the-gil-db940596e325) 不干涉进程；它们是同时发生的。

## 子进程和守护进程

任何进程都可以启动新的进程；即，它可以有“子”进程，除非“父”进程是一个*守护进程*进程。例如:

> 父母睡眠 5 秒…
> 孩子睡眠 5 秒…
> 父母完成
> 孩子完成

在这个例子中，`foo`进程从主进程开始；是的，您可能创建的所有流程都是主 Python 流程的子流程。然后，`foo`进程启动它自己的子进程(`foo_child`)。所以这个孩子实际上是 Python 主进程的“孙子”。

像守护线程一样，程序不会等待守护进程完成；即，当所有非守护进程完成时，程序将退出:

> 父进程休眠 5 秒…
> 守护进程子进程休眠 10 秒…
> 父进程完成

在这个例子中，子进程，一个守护进程，比父进程睡眠时间更长；因此，程序不等子进程完成就退出。我们从来没有看到“儿童完成”打印。

总而言之，守护进程与普通进程有两个不同之处:

*   它们不能有子进程。
*   程序在退出前不会等待它们完成。

## 上下文

多处理环境允许我们选择子进程如何开始，也就是说，它从父进程继承了什么。有三种选择:

*   产卵:启动一个全新的 Python 进程。新进程不会从父进程继承不必要的对象。特别是，它不复制线程锁。**这是 macOS 和 Windows 的默认方法。**
*   *fork* :是父进程的副本。虽然它不复制线程，但它复制线程锁。**在 Unix 中是默认的。这种方法被认为是线程不安全的，尤其可能导致 macOS 上的子进程崩溃。**
*   *forkserver* :第一次启动时，它创建一个新的 Python 进程和一个服务器。每当我们想要启动一个新流程时，我们就连接到服务器并请求最初创建的新 Python 流程的一个分支。

查看[官方文档](https://docs.python.org/3/library/multiprocessing.html)了解每种方法的更多信息。

三种方法中，“fork”最快最不安全，“spawn”最慢最安全。

我们所说的过程安全是指什么？

除了使用“fork”方法时报告的 macOS 崩溃之外，安全意味着线程安全，特别是关于线程锁。在故事的最后一部分，我们将探讨多线程多进程程序是如何陷入死锁的。

原则上，使用“fork”创建流程应该比使用“spawn”方法更快。我们来测试一下。

下面的脚本用给定的上下文创建了`n_procs`。它测量创建每个进程所花费的时间，并将它们保存到一个 JSON 文件中:

要运行脚本:

`$ python [script name].py [number or processes] [context (spawn, fork or forkserver)`

结果如下:

> 最小最大值=(1.795373，9.288665)，平均值= 3。18666.866676666867
> 
> *fork:* minmax=(1.151489，8.550412)，mean = 1 . 155041967365
> 
> *forkserver:*minmax =(1.133119，87.569707)，mean = 3.8111726700000004

*时间以毫秒表示。*

正如我们所看到的，的确,“spawn”方法是最慢的。

“forkserver”方法很有趣；最小创建时间比“fork”方法要短，但是它的平均值要大。这种方法的文献不多；我以前没有在生产中使用过它，但是用它做更多的实验可能是值得的。

## 跨流程共享变量

所以“spawn”上下文是避免问题的首选方式。你能猜到如果两个子进程试图修改主进程中定义的一个全局变量会发生什么吗？什么都没有，变量什么都不会发生。因为子流程是一个新的 Python 流程，所以全局变量在实际应用中表现为不同的变量。看看这个例子:

> 进程号初始化 0
> 进程号完成 100
> 进程号初始化 0
> 进程号完成 100
> 主进程完成，编号 0

我们错误地期望看到在主流程中定义的数字变成 200。期望的行为是在两个过程中各加 100。进程的行为不是这样的；在“spawn”上下文中，它们不共享内存。问题来了，我们如何在进程间共享变量？

*多处理*模块实现了两个对象在进程间共享数据，`*Value*`和`*Array*`。

`Value`对象用于共享单值变量，如数字或字符串。例如:

> 进程号初始化 0
> 进程号初始化 0
> 进程号完成 100
> 进程号完成 101
> 主完成，号 101

正确结果:

> 进程号初始化 0
> 进程号完成 100
> 进程号初始化 100
> 进程号完成 200
> 主进程完成，数量 200

我们通过从*数组*模块中声明它的 typecode 来实例化`Value`(用“l”表示有符号长整型)并使用`*value*`属性访问它的值。

出了问题；我们没有得到预期的 200 英镑。现在怎么办？比赛条件。我们成功地在进程间共享变量；现在，我们需要实现同步机制。

## 竞争条件和锁

即使有 [GIL](/python-concurrency-threading-and-the-gil-db940596e325) 的帮助，在执行多线程时避免竞争情况也是至关重要的。现在我们有了真正的并行执行，事情变得更糟了。当使用线程时，我们可以避免使用锁，通常情况下，我们会没事的。当在执行写操作的进程之间使用共享变量时，锁是必须的。

幸运的是，*多处理*模块有一个锁，它实现了与*线程*模块中的锁相同的简单接口。通过向上一节示例中的示例添加锁，我们可以获得正确的行为:

> 进程号初始化 0
> 进程号完成 100
> 进程号初始化 100
> 进程号完成 200
> 主完成，号 200

最后我们在主流程中定义的`number`得了 200。

在[模块](https://docs.python.org/3/library/multiprocessing.html)中还有其他有用的同步原语，请务必查看。它们非常相似，但也有一些不同，这可能使其中一个更适合您的特定用例。

## 队列和管道

共享变量很好，但是队列呢？它们对于[多线程](/python-concurrency-threading-and-the-gil-db940596e325)非常有用。我们能在多个过程中使用它们吗？让我们试试:

> 睡眠 5 秒……
> 睡完了，q 放
> 
> …死锁

结果是行不通的。程序陷入了僵局。我们不能天真地在多处理代码中使用线程安全对象；否则，我们可能会陷入困境。幸运的是，在*多重处理*模块中有一个多重处理安全队列:

> 睡眠 5 秒…
> 完成睡眠后，q 放
> foo 4 秒。54630.64636646666

一切都像预期的那样工作。

队列非常适合于进程间的单向通信；一个进程将东西放入队列，另一个进程获取它们。没有比这更简单的了。但是如果我们需要双向沟通呢？有一个奇妙的对象实现了这一点，即*管道:*

> proc 1 休眠 5 秒…
> proc 1 完成休眠，连接发送
> proc 2 foo 5.0035919869551435 秒
> proc 2 休眠 5 秒…
> proc 2 完成休眠，发送 ack 并关闭连接 2
> proc 1 接收 ack 并关闭连接

从例子中可以看出，当我们实例化`*Pipe*`时，我们得到了连接的两端。然后我们给每个进程传递一个，并使用`send`和`recv`进行通信。太棒了，不是吗？提醒一句，`recv`方法会阻塞。

## 进程池

正如我们已经知道的，产生一个过程是缓慢的。通常，我们只在相对较短的时间内需要其他进程。大多数情况下，它们用于减轻主进程的 CPU 密集型负担(可能是并行计算)。任务被卸载到另一个进程，一旦完成，我们就把结果返回给主进程。每次都创建新的流程是无效的。进入进程池。`*Pool*`为我们负责流程创建和沟通。此外，池界面是为提交任务而设计的。相比之下，香草`*Process*` 界面就通用多了。

在流程池中的方法中，我们将讨论三种最常用的方法:

*   `map`:模拟 Python 的普通地图
*   `apply`:发送一个函数到池中进行计算，等待(阻塞)直到结果准备好
*   `apply_async`:将一个函数发送到池中进行计算，然后以异步方式检索结果

下面的脚本使用阶乘函数(`get_factorial`)的一个简单(计算上很糟糕)的实现作为计算的目标。

每种方法都有一个函数。这些函数接受一个`Pool` 实例和一个整数列表来计算阶乘。此外，函数测量执行时间并返回它。

main 函数创建一个包含 8 个进程的处理池，并从这三种方法中的每一种方法中获取前 20 个整数(包括零)的列表的解决方案。它为`n_trials`重复计算。

毕竟，计算完成后，结果保存在 JSON 文件中供进一步分析:

结果是:

> map: minmax=(0.801848，47.466579)，mean = 1.4865362500000003
> 
> 应用:最小最大值=(3.544991，6.260502)，平均值=4.26371475
> 
> apply_async: minmax=(0.792829，2.11585)，mean=1.12916867

`apply`是 iterable 最慢的方法。这是有意义的，因为我们在提交对应于 iterable 的下一个元素的另一个任务之前等待结果。`apply`不太适合 iterables。我们使用`apply_async`来避免等待每个任务。然而，我震惊地意识到`apply_async`比`map`方法更快(或者至少是可比的)。

处理 iterables 时，给`apply_async`一个机会；不会让人失望的。

## 进程间数据交换的性能

使用多处理作为并行计算手段的主要注意事项是移动数据。也就是说，使数据对需要它的过程可用。这一部分将测试在所有三个*多处理*环境中移动数据所花费的时间。

测试的计算是添加一个矩阵列。整个矩阵以及列的索引被提交给许多过程。每列一个过程。当然，这是一种相对低效的求和方式。尽管如此，它在测试中达到了两个目的:

*   即使我们只需要一列，也必须将整个矩阵移动到每个过程中。
*   单独遍历列(我们有意避免 NumPy 的向量化)相当于一个有许多类似试验的测试。因此，使测试在统计意义上更加稳健。

在下面的代码中，函数`sum_matrix_columns`定义了要提交给流程的任务。main 函数遍历矩阵列，为每一列创建一个过程。请注意，这些过程不是并行的；它们是连续的。测量每个进程的时间，然后保存到 JSON 文件中:

要运行该脚本，我们需要提供上下文、矩阵行数和矩阵列数作为参数，即，

`$ python [script name].py [context(spawn, fork or forkserver) ] [matrix rows] [matrix columns]`

结果是:

> *spawn:*minmax =(284.932112，464.454816)，mean = 297.296767676767
> 
> *叉:* minmax=(0.963039，316.494265)，mean=15.52602248
> 
> *forkserver:*minmax =(176.789977，319.979666)，mean = 188.88676658675

*时间以毫秒表示。*

我们可以清楚地看到，“fork”上下文更快，因为它没有从头开始一个过程；太糟糕了，有时不是很安全。相反，“产卵”是最慢的。然而，这种差异是惊人的，“fork”和“spawn”之间的性能差异约为 20 倍。

## 多处理+多线程？？？

我们把最好的留到了最后。一个非常有趣的话题:当我们在一个多进程程序中使用多线程时会发生什么？在上下文部分，我们讨论了“fork”不会将线程复制到子进程中的事实。但这意味着什么，为什么会不安全？

它在线程的意义上变得不安全，因为多线程程序中使用的锁可能会突然失去所有所有权，导致死锁。锁的所有者是最后锁定它的线程；只有那个线程可以打开它。

考虑下面的例子:

main 函数启动一个线程(在主进程中)，然后启动一个子进程。反过来，子进程启动另一个线程。因此，这是一个多进程、多线程的程序。目标函数请求锁定`max_iter`的迭代。如果它得到锁，它就睡觉。

如果我们使用“spawn”的“forkserver”运行代码，程序将花费几秒钟(等待所有迭代)然后退出。这是预期的行为。然而，如果我们使用“fork”上下文运行程序，它将会一直处于死锁状态。这是为什么呢？

“fork”上下文的问题是它不从父线程复制线程。但是，它确实从父对象复制了锁。
因此，就子进程而言，锁没有所有者；所有者是子子进程中不再存在的线程。

最后一个例子非常清楚地说明了这一点；如果一定要做一个多线程+多进程的应用，明智的做法是不要使用“fork”上下文。

## 这个故事的寓意

我们已经证实，在某些情况下,“分叉”上下文是最快的，快了一个数量级。虽然官方文档说使用 macOS 可能会崩溃，但我还没有亲眼目睹过。事实上，这种方法的速度有时值得冒险。

我会说，如果子进程对程序至关重要，就要避免“fork”。然而，如果子进程只执行 CPU 密集型任务，速度是最重要的，并且不涉及线程，那么您可能会陷入危险的境地，并使用“fork”。

*我希望这个故事对你有用。* [*订阅*](https://medium.com/subscribe/@diego-barba) *到我的邮件列表如果你想知道更多这样的故事。*

*喜欢这个故事？通过我下面的推荐链接成为一个媒体成员来支持我的写作。无限制地访问我的故事和许多其他内容。*

[](https://medium.com/@diego-barba/membership) [## 通过我的推荐链接加入 Medium-Diego Barba

### 阅读迭戈·巴尔巴(以及媒体上成千上万的其他作家)的每一个故事。您的会员费直接支持…

medium.com](https://medium.com/@diego-barba/membership)