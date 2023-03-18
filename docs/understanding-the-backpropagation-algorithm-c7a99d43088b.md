# 理解反向传播算法

> 原文：<https://towardsdatascience.com/understanding-the-backpropagation-algorithm-c7a99d43088b>

## 了解人工智能的支柱

![](img/e5b20cf3495250b69c64dc42ff7561e6.png)

弗洛里安·里德在 [Unsplash](https://unsplash.com/s/photos/descent?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) 上拍摄的照片

反向传播算法是在训练过程中改进神经网络的工具。在该算法的帮助下，单个神经元的参数被修改，使得模型的预测和实际值尽可能快地匹配。这使得神经网络即使在相对较短的训练期后也能提供良好的结果。

这篇文章加入了其他关于机器学习基础的文章。如果你没有任何关于[神经网络](https://databasecamp.de/en/ml/artificial-neural-networks)和[梯度下降](https://databasecamp.de/en/ml/gradient-descent)话题的背景，你应该在继续阅读之前看看链接的帖子。我们将只能简要地触及这些概念。一般来说，机器学习是一个非常数学化的话题。对于反向传播的解释，我们将尽可能避免数学推导，只给出对该方法的基本理解。

# 神经网络

神经网络由许多组织在不同层中的神经元组成，这些神经元相互通信并相互链接。在输入层，神经元被给予各种输入用于计算。应对网络进行训练，以便输出层(最后一层)根据输入做出尽可能接近实际结果的预测。

所谓的隐藏层用于此目的。这些层还包含许多与前一层和后一层通信的神经元。在训练期间，改变每个神经元的加权参数，使得预测尽可能接近现实。反向传播算法帮助我们决定改变哪个参数，以使损失函数最小。

# 梯度下降法

梯度法是数学优化问题中的一种算法，它有助于尽可能快地逼近函数的最小值。人们计算函数的导数，即所谓的梯度，并沿着这个向量的相反方向前进，因为函数的下降速度最快。

如果这太数学化了，你可能在山里徒步旅行时熟悉这种方法。你终于爬上了山顶，拍下了必须的照片，充分地欣赏了风景，现在你想尽快回到山谷和家里。所以你寻找从山下到山谷最快的路，也就是函数的最小值。凭直觉，人们会简单地选择最陡的下坡路，因为人们认为这是最快的下坡路。当然，这只是形象地说，因为没有人敢走下山上最陡的悬崖。

梯度法对函数也是如此。我们在函数图中的某处，试图找到函数的最小值。与山的例子相反，在这种情况下，我们只有两种移动的可能性。在正或负的 x 方向上(具有一个以上的变量，即多维空间，当然相应地有更多的方向)。梯度帮助我们知道它的负方向是最陡函数下降。

# 机器学习中的梯度下降

机器学习中让我们感兴趣的函数是损失函数。它测量神经网络的预测和训练数据点的实际结果之间的差异。我们还想最小化这个函数，因为这样我们就会有一个 0 的差值。这意味着我们的模型可以准确地预测数据集的结果。达到目标的调节螺丝是神经元的权重，我们可以改变它来更接近目标。

简而言之:在训练过程中，我们得到了损失函数，我们试图找到它的最小值。为了这个目的，我们在每次重复后计算函数的梯度，并朝着函数最陡下降的方向前进。不幸的是，我们还不知道我们必须改变哪个参数，以及改变多少来最小化损失函数。这里的问题是梯度程序只能对前一层及其参数执行。然而，深度神经网络由许多不同的隐藏层组成，这些隐藏层的参数理论上都可以对整体误差负责。

因此，在大型网络中，我们还需要确定每个参数对最终误差的影响有多大，以及我们需要在多大程度上修改它们。这是反向传播的第二个支柱，这个名字由此而来。

# 反向传播算法

我们会尽量让这个帖子非数学化，但不幸的是，没有它我们完全做不到。我们的网络中的每一层都由来自前一层或来自训练数据集的输入和传递到下一层的输出来定义。输入和输出之间的差异来自神经元的权重和激活函数。

问题是，一个层对最终误差的影响还取决于下面的层如何传递这个误差。即使神经元“计算错误”，如果下一层中的神经元简单地忽略该输入，即将其权重设置为 0，这也不是很重要。这通过一层的梯度也包含下一层的参数的事实在数学上示出。因此，我们必须在最后一层，即输出层开始反向传播，然后使用梯度方法逐层向前优化参数。

这就是反向传播或误差反向传播这一名称的由来，因为我们从后面通过网络传播误差并优化参数。

# 这是你应该带走的东西

*   反向传播是一种训练神经网络的算法。
*   其中，它是梯度法在网络损失函数中的应用。
*   这个名字来源于这样一个事实，即误差从模型的末端一层一层地向后传播。

*如果你喜欢我的作品，请在这里订阅*[](https://medium.com/subscribe/@niklas_lang)**或者查看我的网站* [*数据大本营*](http://www.databasecamp.de/en/homepage) *！还有，medium 允许你每月免费阅读* ***3 篇*** *。如果你希望有****无限制的*** *访问我的文章和数以千计的精彩文章，不要犹豫，点击我的推荐链接:*[【https://medium.com/@niklas_lang/membership】](https://medium.com/@niklas_lang/membership)每月花$***5****获得会员资格**

*[](/beginners-guide-to-gradient-descent-47f8d0f4ce3b) [## 梯度下降初学者指南

### 关于梯度下降法你需要知道的一切

towardsdatascience.com](/beginners-guide-to-gradient-descent-47f8d0f4ce3b) [](/beginners-guide-extract-transform-load-etl-49104a8f9294) [## 初学者指南:提取、转换、加载(ETL)

### 了解数据分析中的大数据原理

towardsdatascience.com](/beginners-guide-extract-transform-load-etl-49104a8f9294) [](/8-machine-learning-algorithms-everyone-new-to-data-science-should-know-772bd0f1eca1) [## 数据科学新手应该知道的 8 种机器学习算法

### 简要解释机器学习背后的算法

towardsdatascience.com](/8-machine-learning-algorithms-everyone-new-to-data-science-should-know-772bd0f1eca1)*