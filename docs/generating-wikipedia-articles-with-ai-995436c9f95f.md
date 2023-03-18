# 用人工智能生成维基百科文章

> 原文：<https://towardsdatascience.com/generating-wikipedia-articles-with-ai-995436c9f95f>

## [播客](https://towardsdatascience.com/tagged/tds-podcast)

## Meta AI 研究员 Angela Fan 谈改进维基百科的挑战和重要性

[苹果](https://podcasts.apple.com/ca/podcast/towards-data-science/id1470952338?mt=2) | [谷歌](https://www.google.com/podcasts?feed=aHR0cHM6Ly9hbmNob3IuZm0vcy8zNmI0ODQ0L3BvZGNhc3QvcnNz) | [SPOTIFY](https://open.spotify.com/show/63diy2DtpHzQfeNVxAPZgU) | [其他](https://anchor.fm/towardsdatascience)

*编者按:TDS 播客由杰雷米·哈里斯主持，他是人工智能安全初创公司墨丘利的联合创始人。每周，Jeremie 都会与该领域前沿的研究人员和商业领袖聊天，以解开围绕数据科学、机器学习和人工智能的最紧迫问题。*

生成引用良好且准确的维基百科文章一直是一个重要的问题:维基百科基本上已经成为互联网的记录百科全书，数亿人通过它了解世界。

但在过去十年中，维基百科也成为了数据饥渴的文本生成模型的重要训练数据来源。因此，维基百科内容中的任何缺点都有被未来的文本生成工具放大的风险。如果一种类型的主题或人物在维基百科的语料库中长期代表性不足，我们可以期待生成文本模型在其输出中反映甚至放大这种代表性不足。

从这个角度来看，维基百科文章生成的项目远比它看起来的要多——它实际上是为未来的语言生成系统设置场景，并授权人类以更强大的方式引导这些系统。

这就是为什么我想和 Meta AI 研究员 Angela Fan 谈谈，她的最新项目专注于生成可靠、准确和结构化的维基百科文章。在这一集的 TDS 播客中，她和我一起谈论了她的工作、高质量长格式文本生成的意义以及人类/人工智能合作的未来。

以下是我在对话中最喜欢的一些观点:

*   为了生成连贯和结构良好的维基百科文章，Angela 和她的合作者能够使用一个相当普通的基于 transformer 的架构，并做了两处有趣的修改。首先，维基百科的文章需要参考文献，而普通的变形金刚无法生成这些参考文献。因此，Angela 的系统转而查询公共抓取数据集，以找到贯穿生成的文章的主张的支持证据。该系统还使用缓存机制来确保在文章的前面部分中生成的信息可以被模型在生成新的部分时调用。这克服了 transformer 上下文窗口的有限大小，并确保模型总是有相关的信息，即使它来自文章的更早部分。
*   评估生成的文本可能是棘手的，公平地说，没有一个单一的指标能够完全捕捉到人类评估的所有细微差别。出于这个原因，虽然 Angela 和她的合作者确实使用传统的度量标准评估了生成的样本的质量，但他们用人工审查补充了这种分析。为了被人类评论者视为“准确”，一个句子需要事实正确，并且在语气和风格上与其他维基百科文章一致。这是一个很高的标准，但据 Angela 估计，50%的生成句子确实达到了这个标准——虽然这可能还不足以让她的系统推广到更广泛的世界，但它可以有意义地加快人类作家的工作，他们的责任可以从最初的研究转向事实检查。
*   人们常说，语言模型可以使它们的训练数据中的偏见永久化，事实的确如此。但是安吉拉指出，他们经常超越复制这些基础，实际上是放大它们。例如，如果文本语料库中 60%的代词是女性“她”，则很典型地会发现“她”在生成的文本中会被*过度表示*，因为语言模型通常喜欢“谨慎行事”，生成的文本片段单独来说更能反映训练集，但总的来说会放大现有趋势。

你可以[在这里查看安吉拉的作品](https://ai.facebook.com/people/angela-fan/)，或者[在推特上关注我](https://twitter.com/jeremiecharris)。

![](img/a7ee2e313d4533adf0ae9ffb4de90523.png)

## 章节:

*   0:00 介绍
*   1:45 进入 Meta AI 的旅程
*   5:45 过渡到维基百科
*   11:30 文章如何生成
*   18:00 文本质量
*   21:30 准确度指标
*   25:30 出现幻觉的风险
*   30:45 跟上变化
*   36:15 用户界面/UX 问题
*   45:00 性别失衡的技术原因
*   51:00 总结