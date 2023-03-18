# 机器学习在乳腺癌研究中的应用

> 原文：<https://towardsdatascience.com/machine-learning-in-breast-cancer-research-d1dd99f7819a>

## 可解释的机器学习如何应用于乳腺癌研究中的模式识别

![](img/95e57b33ac949c5d4a418fae189228ce.png)

照片由来自 [Pexels](https://www.pexels.com/photo/ribbon-representing-breast-cancer-amidst-test-tubes-7723582/) 的 [Tara Winstead](https://www.pexels.com/@tara-winstead/) 拍摄

在过去的几年里，围绕机器学习将如何改变许多行业有很多炒作。经常提到的一个行业是医疗保健。在下面的博客文章中，我们将探索一种可以产生的影响。我们将通过检查 2021 年发表在《自然》杂志上的一篇文章来做到这一点。这篇文章的名字是[通过可解释的机器学习进行形态学和分子乳腺癌剖析](https://www.nature.com/articles/s42256-021-00303-4)。

这篇文章将有三个部分:**研究的目的**、研究的**方法** **/结果**以及**为什么**这对肿瘤学和卫生保健很重要。

**目的**

从历史上看，肿瘤学研究中的各种分析技术之间缺乏整合。这使得癌症特性的分子数据和形态学数据有些脱节。这项研究中的研究人员着手通过机器学习建立一种联系，在这两种类型的分析技术之间架起一座桥梁。如果成功，这种方法可以帮助产生细胞类型和分子特性之间联系的假设。

**方法/结果**

*机器学习算法*

这项研究使用的机器学习方法基于一种称为分层相关性传播(LRP)的技术。逐层相关性传播是一种可解释的机器学习算法。该方法可以突出用于给定输出的最重要的输入特征，而不是只给出特定输入的输出。对于使用图像的情况，突出显示的特征是像素。结果是输入图像上的热图，显示哪些像素对输出的波动影响最大。在给定分类的情况下，具有高颜色强度的像素与像素的高相关性分数相关。这个过程的基本等式可以表示为:

![](img/f9b916d0a0472e63119caa349f75afb7.png)

> *j* 和 *k* 代表神经网络中连续两层的神经元。Zjk 表示神经元 *j* 对使神经元 *k* 相关有多少贡献。 *R* 是 *j* 和*k*的关联分数

LRP 计算的属性解释了输入要素的总贡献，而不是您在注意力热图中获得的对输入变化的敏感度。对于逐层相关性传播如何工作的更多技术解释，请参考以下论文:[逐层相关性传播概述](https://www.researchgate.net/publication/335708351_Layer-Wise_Relevance_Propagation_An_Overview)。

*算法的应用*

既然我们讨论了逐层相关性传播如何工作的概述，我们将探索研究团队如何能够将其用于癌症形态学和分子乳腺癌数据。

该团队首先创建了一个图像数据库(柏林癌症图像库，B-CIB ),其中包含显微镜图像数据的注释补丁。使用 LRP，研究小组能够区分癌细胞和肿瘤浸润淋巴细胞(til)。til 是淋巴细胞，可以渗透到肿瘤组织中，识别并杀死癌细胞。它们存在的密度可以用作预测患者存活的特征。LRP 允许他们的密度的视觉表现。

然后，研究人员使用形态学图像数据作为算法的输入来预测分子特征。本质上，试图通过扫描图像来获得对患者分子特性的洞察。用于训练的数据由组合的图像和分子谱数据组成。考虑到这部分研究的目的以及通过数据集获得的用于训练的信息，不需要手动空间注记。他们可以让算法在训练期间通过输入分子数据和形态学数据来识别图像中的模式。为了减少分类任务的维度，他们对不同的分子特征使用了高低分类方法。该算法基于对分子特征的表达是高还是低的预测给出分类，给定形态学图像作为输入。表达水平得分较高的两个基因是 CDH1 和 TP53。

> ***CD h1 和 TP53 基因的重要性***
> 
> 基于它们对乳腺癌的影响的先验知识，为这些分子特征产生高表达分数的算法是有意义的。
> 
> TP53 基因被认为是一种肿瘤抑制基因。它调节细胞有丝分裂的水平。当这种基因突变时，就会发生过度的细胞分裂，形成肿瘤。
> 
> CDH1 突变通过增加增殖(即细胞数量增加)和转移(即癌症生长远离原发地)与癌症进展相关。CDH1 产生的蛋白质是 E-钙粘蛋白，它对细胞粘附至关重要，使细胞保持在一起，人们认为这种基因的遗传变化可以导致癌细胞更容易从肿瘤的原发部位分离，从而导致转移。

该团队还尝试预测分子特征的空间定位。该预测显示了与某些分子特征表达统计相关的空间区域。这些信息可用于创建关于肿瘤微环境的特定成分与分子肿瘤概况特征的相关性的假设，从而推动发现图像中显示的肿瘤组织学特征和可能表达的分子特征之间可能存在的潜在联系。这些链接可以导致候选人名单可用于分子特征。这些列表将包括与乳腺癌相关的分子特征。

最终，机器学习方法揭示了与各种分子特征的表达统计相关的空间和形态学特征。这些信息通过热图显示，热图显示了在大多数情况下，分子特征如何与测试的形态组(癌细胞、til 和间质(支持细胞))有特定的关联。

为了测试结果的有效性，该团队使用了一种称为免疫组织化学(IHC)染色的技术，将结果与机器学习算法生成的热图进行比较。他们利用样方测试来显示两者之间的联系。样方检验可用于测量点格局的空间随机性。象限检验通过卡方检验来测量空间随机性。总的来说，IHC 模式反映了从验证机器学习方法的机器学习算法预测的模式。

**为什么**

我们今天看到的研究是机器学习如何用于癌症研究目的的一个很好的例子。它不一定会取代已经存在的工具，但它可以作为这些工具的补充。肿瘤学研究的一些用例涉及通过基于机器学习的方法可能出现的新模式生成假设。从本文探索的研究中可能产生的假设的例子大多与在非空间分子特征和空间信息之间发现的新关系有关。这些关系有助于更精确的肿瘤分级和潜在靶向治疗的新候选列表。

在模式识别至关重要的行业，机器学习可以充当进一步推动发现的指路明灯。

> 分层相关性传播:概述 ResearchGate 上的科学数字。可从:[https://www . researchgate . net/figure/Illustration-of-the-LRP-procedure-Each-neuron-re distributes-to-the-lower-layer-as-much _ fig 2 _ 335708351](https://www.researchgate.net/figure/Illustration-of-the-LRP-procedure-Each-neuron-redistributes-to-the-lower-layer-as-much_fig2_335708351)【2022 年 8 月 17 日获取】
> 
> Binder，a .，Bockmayr，m .，Hä gele，m .等,《通过可解释的机器学习进行形态学和分子乳腺癌剖析》。自然机器智能 3，355–366(2021)。【https://doi.org/10.1038/s42256-021-00303-4 号
> 
> MEDLINE plus[互联网]。贝塞斯达(MD):美国国家医学图书馆(US)；[更新于 2020 年 6 月 24 日]。CDH1 基因；【更新于 2017 年 8 月 1 日；已审核 2018 年 7 月 1 日；引用 2022 年 8 月 17 日]；供货地:【https://medlineplus.gov/genetics/gene/cdh1/#conditions 