# 大型语言模型的发展——BERT、GPT3、MUM 和 PaML

> 原文：<https://towardsdatascience.com/self-supervised-transformer-models-bert-gpt3-mum-and-paml-2b5e29ea0c26>

## ChatGPT 和 Google Bard 背后的算法

![](img/d7d85287af1419828ea6218f7f27e561.png)

作者照片

在早期，NLP 系统大多是基于规则的，后来被机器学习模型所取代。从零开始训练深度学习语言模型需要大量的标记数据，生成这些数据是昂贵的，而获得大量的未标记文本数据是非常容易的。同时，迁移学习允许重用在源任务中学到的知识，以便在目标任务中表现良好。近年来，变形金刚比传统的 rnn 更受欢迎。结合变压器和迁移学习的力量，NLP 的研究人员开发了基于变压器的自我监督语言模型。

在本文中，我们将概述基于 Transformer 的自监督语言模型，并解释核心概念，包括预训练和下游适应。我们还将比较几个流行的自我监督模型，包括 **GPT3** 和**BERT**——基于 transformer 的自我监督语言模型的先驱，**MUM**—近年来为许多谷歌功能提供动力的模型，以及 **PaML** —该领域的最新突破。

# **自我监督学习**

## 什么是自我监督学习

传统上，大型语言模型是用监督学习来训练的，即从人类标记的数据中学习。这些模型在特定任务上表现良好，但是它们需要大量的标记数据来实现良好的性能，并且通常缺乏泛化能力。这些问题在自监督学习中得到解决，因为只需要少量甚至 0(在 0 次学习的情况下)人标记的数据，而绝大多数未标记的数据可以被利用。

## 自我监督学习的两个阶段

**预培训**

预训练过程通常无人监督。标签根据数据属性和预训练任务的定义自动生成。对大量未标记的数据进行预训练有助于模型学习通用的语法和语义模式，这些模式可以在以后转移到特定的下游任务。我们可以把这比作一个获得基本常识的人。

**下游适应**

这就是迁移学习发挥作用的地方。预先训练的模型可以通过添加一两个特定层来适应下游任务。下游适应有助于我们避免从头开始训练下游模型，实现小数据集的良好性能，并防止过度拟合。将预先训练的语言表示应用于下游任务有不同的策略，包括:

1.  基于特征的

基于特征的方法预先训练语言表示，并将它们用作下游模型中的输入特征。Word2Vec 就是一个例子。

2.微调

与基于特征的方法不同，在基于特征的方法中，我们需要训练单独的下游模型，微调方法只是用特定任务的标记数据来微调预训练模型中的所有参数。

3.少量学习

少量学习是元学习的一种。与微调方法中使用的标准监督学习不同，少镜头学习不需要大型标记数据集。相反，它只需要少量的样本(它们被称为*支持集*)，在推理时，模型根据与支持集的数据相似性进行预测。少击学习的特例是一击学习和零击学习，其中只提供一个或零个下游例子。

# 变压器

当今前沿语言模型的另一个关键共同特征是它们都是变形金刚。由于梯度消失的问题，传统的 RNN 深度学习模型难以建模长期上下文。为了克服这一点，研究人员开发了一种新型的深度学习模型，称为变形金刚。与顺序处理输入令牌的传统 rnn 相比，Transformers 一次处理所有单词，使它们高度并行化。变形金刚的主要组成部分是自我关注，这是一种关注的变体，它用序列中其余元素的加权平均值来替换序列中的每个元素。变压器有几种不同的架构:

1.  编码器-解码器

这在最初的变压器模型中使用。编码层生成输入的编码，而解码层处理编码以生成输出序列。编码器和解码器层都有一个前馈神经网络，并利用注意机制。

2.仅编码器

仅编码器模型被设计为对每个输入标记或序列产生单个预测，这意味着它们适用于分类任务，但不适用于生成任务，如机器翻译或文本摘要。编码器是双向的，由两个主要部分组成:自关注机制和前馈神经网络。

3.仅解码器

解码器模型是自回归的，这意味着每一步的输出都作为输入馈入下一步。这也意味着解码器是单向的。在没有编码器对输入句子进行编码的情况下，解码器本身会根据输入句子及其迄今为止输出的内容来学习如何集中注意力。

是时候钻研几款小说模式了！下面按时间顺序列出了这些型号。

# 伯特

来自变压器的双向编码器表示(BERT)是最先开发的基于变压器的自监督语言模型之一。BERT 有 340M 个参数，是一个仅支持编码器的双向转换器。

使用来自图书语料库(8 亿单词)和英语维基百科(2500 万单词)的未标记语言序列对 BERT 进行预训练。回想一下，预训练是无人监督的。为了构建预训练目标，每个序列中所有标记的 15%被随机屏蔽，并且模型被训练来预测被屏蔽的单词，而不是重建整个输入。这被称为“蒙面语言模型”(MLM)。除了 MLM，伯特还使用“下一句话预测”任务来联合预训练模型。

微调应用于下游适配，其中特定于任务的输入和输出被插入到 BERT 中，并且所有参数被端到端地微调。

# GPT3

GPT3 是 Open AI 的 GPT 模型系列的一部分。这正是为著名的 ChatGPT 提供动力的模型。这是一个只有解码器的单向自回归模型，有 175 个参数(比 BERT 大得多)。

与 BERT 不同，GPT3 试图用少镜头学习代替下游微调。该模型在推理时被给予任务的少量数据演示作为条件，但是与微调方法不同，没有权重更新。这是受到这样一个事实的启发，即一旦人类有了一般的语言理解，我们就不一定需要大规模的监督数据集来学习大多数语言任务。尽管在大多数情况下，微调仍然优于少量多次学习，但 GPT3 显示，在某些任务中，零次、一次和少量多次设置几乎与最先进的微调系统的性能相当。

Open AI 已经计划很快发布 GPT4，它可能会是另一个顶级的表现者。一旦它出来，我会写专门的文章。敬请期待！

# 最大值(T5)

多任务统一模型(MUM)是今天推动复杂的谷歌搜索的技术。

MUM 使用文本到文本转换转换器(T5)，这是一种编码器-解码器、多任务学习模型，结合了初始的无监督预训练(作为任务)和针对特定任务的微调(每个作为任务)。它在微调之前对无监督和有监督任务的多任务混合进行预训练，因此我们可以对任何 NLP 任务使用相同的模型、损失函数和超参数。

MUM 是多模态的，所以它理解文本和图像之间的信息。它有 11 个参数，同时接受 75 种不同语言和许多不同任务的训练，使它能够比以前的模型更全面地理解信息和世界知识。事实上，它比伯特强大 1000 倍。

# PaML

路径语言模型(PaML)是 Google 的最新突破。它已经扩展到 540B 参数，但使用 Pathways 系统进行了有效训练，这是一种新的 ML 系统，能够在数千个加速器芯片上高效训练非常大的神经网络。

PaML 有一个标准的编码器-解码器转换器模型架构，并做了一些修改。凭借大规模的参数，它展示了出色的少数镜头性能，在 29 个最广泛评估的英语 NLP 任务中的 28 个任务上取得了最先进的结果，包括代码生成、问答、多语言生成、NMT、推理等。

值得一提的是，PaML 在算术和常识推理任务上有突破性的表现。这是通过规模和*思维链*提示的组合来实现的，其中模型在做出预测之前被明确提示生成自然语言逻辑推理链。等等，这不是我们人类天生的行为吗？

# 结论

在本文中，我们讨论了基于 Transformer 的自监督语言模型系统，并探索了几个流行的模型，这些模型要么已经在行业中大量使用，要么优于当前的技术水平

这是一个相对较新的快速发展的领域，不断取得突破。几个月后，我们可能会看到更多高性能的型号问世。请继续关注我的更多更新。:)

我希望你喜欢这篇文章！

# 参考

1.  [用统一的文本到文本转换器探索迁移学习的极限](https://arxiv.org/abs/1910.10683)
2.  [PaLM:用通路扩展语言建模](https://arxiv.org/abs/2204.02311)
3.  [语言模型是一次性学习者](https://arxiv.org/abs/2005.14165)
4.  [BERT:用于语言理解的深度双向转换器的预训练](https://arxiv.org/abs/1810.04805)
5.  [自然语言处理中基于变换器的预训练模型综述](https://arxiv.org/abs/2108.05542)