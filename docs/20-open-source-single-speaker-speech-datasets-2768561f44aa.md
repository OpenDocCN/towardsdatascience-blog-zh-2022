# 20 个开源单说话人语音数据集

> 原文：<https://towardsdatascience.com/20-open-source-single-speaker-speech-datasets-2768561f44aa>

## 全面的开源多语言语音数据

![](img/91560c7eea5a1ea4e53bb9d0af88ed67.png)

杰森·罗斯韦尔在 [Unsplash](https://unsplash.com/s/photos/speaker?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) 上的照片

语音合成(text-to-speech，TTS)是人工智能领域的一项新的关键技术。它提供了从文本输入动态生成类似人类声音的能力。TTS 可用于多种目的，并与自动化服务紧密相关。

然而，训练文本到语音模型需要大量的音频数据及其相应的转写/音素。因此，对于大多数开发人员来说，这并不容易实现，因为收集和标记数据集需要付出巨大的努力。

我整合了 20 个公开的开源单说话人多语言语音数据集。免费为你的项目使用它们。

> **注**:并非所有都可以用于商业目的。我已经在每个数据集下面列出了他们的许可证、采样率和文件大小，供您参考。

# 英语

## LJSpeech

LJSpeech 是最常用的文本到语音转换数据集之一。大约有 13，100 个基于 7 本非小说类书籍的音频剪辑。每个片段由 1 到 10 秒组成，产生超过 23 小时的音频数据。

```
╔═══════════════╦═══════════╦═══════════╦═══════════════════════╗
║  **Sample rate**  ║   **Format**  ║ **File size** ║        **License**        ║
╠═══════════════╬═══════════╬═══════════╣═══════════════════════╣
║ 22050         ║ wav       ║ 2.6 GB    ║ [Public domain ](https://librivox.org/pages/public-domain)        ║
╚═══════════════╩═══════════╩═══════════╩═══════════════════════╝
```

## 世界英语圣经

[世界英语圣经](https://www.kaggle.com/datasets/bryanpark/the-world-english-bible-speech-dataset)是由[音频宝库](https://www.audiotreasure.com/)提供的音频圣经录音的修订版。在最初的版本中，每个音频文件作为文本到语音转换训练的输入数据都太长了。因此，一名研究人员主动将录音拆分，并重新排列转录。

```
╔═══════════════╦═══════════╦═══════════╦═══════════════════════╗
║  **Sample rate**  ║   **Format**  ║ **File size** ║        **License**        ║
╠═══════════════╬═══════════╬═══════════╣═══════════════════════╣
║ 12000         ║ wav       ║ 6.66 GB   ║ [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/)       ║
╚═══════════════╩═══════════╩═══════════╩═══════════════════════╝
```

# 韩国的

## 朝鲜语单一使用者(KSS)

[KSS](https://www.kaggle.com/datasets/bryanpark/korean-single-speaker-speech-dataset) 是首批公开的韩语数据集之一。录音是由一名专业女声演员朗读精选的书籍录制的。大约有 12，853 个音频剪辑，产生超过 12 小时的音频数据。

```
╔═══════════════╦═══════════╦═══════════╦═══════════════════════╗
║  **Sample rate**  ║   **Format**  ║ **File size** ║        **License**        ║
╠═══════════════╬═══════════╬═══════════╣═══════════════════════╣
║ 44100         ║ wav       ║ 4.32 GB   ║ [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/)       ║
╚═══════════════╩═══════════╩═══════════╩═══════════════════════╝
```

## Jejueo 单说话人语音数据集

Jejueo，也叫济州语，是济州岛上使用的韩语。Jejueo 单说话人语音数据集是济州研究中心发起的项目的一部分。它包含大约 10k 音频文件。每个音频片段的长度约为 2 至 18 秒。

```
╔═══════════════╦═══════════╦═══════════╦═══════════════════════╗
║  **Sample rate**  ║   **Format**  ║ **File size** ║        **License**        ║
╠═══════════════╬═══════════╬═══════════╣═══════════════════════╣
║ 44100         ║ wav       ║ 4.38 GB   ║ [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/)       ║
╚═══════════════╩═══════════╩═══════════╩═══════════════════════╝
```

# 日本人

## CSS10 日语

[CSS10](https://github.com/kyubyong/css10) is a collection of single speaker speech datasets for 10 languages created by Kyubyong. All audio recordings is based on the audio books from LibriVox. [CSS10 Japanese](https://www.kaggle.com/datasets/bryanpark/japanese-single-speaker-speech-dataset) is a subset of CSS10 and contains about 14 hours of audio files for [明暗 (Meian)](https://librivox.org/meian-by-soseki-natsume/).

```
╔═══════════════╦═══════════╦═══════════╦═══════════════════════╗
║  **Sample rate**  ║   **Format**  ║ **File size** ║        **License**        ║
╠═══════════════╬═══════════╬═══════════╣═══════════════════════╣
║ 22050         ║ wav       ║ 4.74 GB   ║ [CC0: Public Domain](https://creativecommons.org/publicdomain/zero/1.0/)    ║
╚═══════════════╩═══════════╩═══════════╩═══════════════════════╝
```

## Kokoro 语音数据集

[Kokoro 语音数据集](https://github.com/kaiidams/Kokoro-Speech-Dataset)包含了取自[青空文子](https://www.aozora.gr.jp/)的 14 本小说的大约 43253 段录音。

它有不同的尺寸，即:

*   微小的
*   小的
*   大的
*   xlarge

```
Tiny:
Total clips: 285
Min duration: 3.019 secs
Max duration: 9.462 secs
Mean duration: 4.871 secs
Total duration: 00:23:08Small:
Total clips: 8812
Min duration: 3.007 secs
Max duration: 14.431 secs
Mean duration: 4.951 secs
Total duration: 12:07:12Large:
Total clips: 22910
Min duration: 3.007 secs
Max duration: 14.988 secs
Mean duration: 4.984 secs
Total duration: 31:42:54X Large:
Total clips: 43253
Min duration: 3.007 secs
Max duration: 14.988 secs
Mean duration: 4.993 secs
Total duration: 59:59:40
```

转录元数据是在 LJSpeech 之后建模的，这使得它与大多数语音合成项目兼容。

```
╔═══════════════╦═══════════╦═══════════╦═══════════════════════╗
║  **Sample rate**  ║   **Format**  ║ **File size** ║        **License**        ║
╠═══════════════╬═══════════╬═══════════╣═══════════════════════╣
║ 22050         ║ wav       ║ Varies    ║ [Public Domain](https://librivox.org/pages/public-domain)         ║
╚═══════════════╩═══════════╩═══════════╩═══════════════════════╝
```

## JSUT

[JSUT 单个说话者语料库](https://sites.google.com/site/shinnosuketakamichi/publication/jsut)是 JSUT 集合的一部分，用于连接语音、歌曲和音频事件的日语语音语料库。它有大约 10 小时的音频数据

```
╔═══════════════╦═══════════╦═══════════╦═══════════════════════╗
║  **Sample rate**  ║   **Format**  ║ **File size** ║        **License**        ║
╠═══════════════╬═══════════╬═══════════╣═══════════════════════╣
║ 48000         ║ wav       ║ 2.7 GB    ║ [CC-BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/)          ║
╚═══════════════╩═══════════╩═══════════╩═══════════════════════╝
```

# 西班牙语

## CSS10 西班牙语

[CSS10 西班牙语](https://www.kaggle.com/datasets/bryanpark/spanish-single-speaker-speech-dataset)是 CSS10 集合中最大的数据集之一。它包含超过 23 小时的录音。内容基于以下有声读物:

1.  [百伦](https://librivox.org/bailen-by-benito-perez-galdos/)
2.  [3 月 19 日至 5 月 2 日](https://librivox.org/el-19-de-marzo-y-el-2-de-mayo-by-benito-perez-galdos/)
3.  [拉巴塔拉-德洛斯阿拉皮斯](https://librivox.org/la-batalla-de-los-arapiles-by-benito-perez-galdos/)

```
╔═══════════════╦═══════════╦═══════════╦═══════════════════════╗
║  **Sample rate**  ║   **Format**  ║ **File size** ║        **License**        ║
╠═══════════════╬═══════════╬═══════════╣═══════════════════════╣
║ 22050         ║ wav       ║ 7.57 GB   ║ [CC0: Public Domain](https://creativecommons.org/publicdomain/zero/1.0/)    ║
╚═══════════════╩═══════════╩═══════════╩═══════════════════════╝
```

# 荷兰人

## CSS10 荷兰语

[CSS10 荷兰语](https://www.kaggle.com/datasets/bryanpark/dutch-single-speaker-speech-dataset)是 CSS10 集合的另一个子集。它包含大约 14 小时的录音，基于 [20.000 Mijlen onder Zee](https://librivox.org/20-000-mijlen-onder-zee-by-jules-verne/) 有声读物。每个片段大约 5 到 10 秒。

```
╔═══════════════╦═══════════╦═══════════╦═══════════════════════╗
║  **Sample rate**  ║   **Format**  ║ **File size** ║        **License**        ║
╠═══════════════╬═══════════╬═══════════╣═══════════════════════╣
║ 22050         ║ wav       ║ 4.48 GB   ║ [CC0: Public Domain](https://creativecommons.org/publicdomain/zero/1.0/)    ║
╚═══════════════╩═══════════╩═══════════╩═══════════════════════╝
```

# 法语

## CSS10 法语

[CSS10 法语](https://www.kaggle.com/datasets/bryanpark/french-single-speaker-speech-dataset)自带 19 小时音频数据。每个音频剪辑的长度大约为 2 到 12 秒，这使得它成为大多数文本到语音转换训练的输入数据的良好选择。内容基于以下有声读物:

1.  《悲惨世界》——第 5 卷。
2.  [亚森·罗宾控制她洛克·肖尔斯](https://librivox.org/arsene-lupin-contre-herlock-sholmes-by-maurice-leblanc/)

```
╔═══════════════╦═══════════╦═══════════╦═══════════════════════╗
║  **Sample rate**  ║   **Format**  ║ **File size** ║        **License**        ║
╠═══════════════╬═══════════╬═══════════╣═══════════════════════╣
║ 22050         ║ wav       ║ 6.08 GB   ║ [CC0: Public Domain](https://creativecommons.org/publicdomain/zero/1.0/)    ║
╚═══════════════╩═══════════╩═══════════╩═══════════════════════╝
```

## SynPaFlex

[SynPaFlex](https://www.ortolang.fr/market/corpora/synpaflex-corpus) 语料库拥有大约 87 小时的法语表达音频数据。不像其他数据集。这个数据集是基于一个人阅读不同文学类型的有声读物。它旨在从不同的角度探索表现力。例如:

*   话语风格
*   韵律学
*   发音

```
╔═══════════════╦═══════════╦═══════════╦═══════════════════════╗
║  **Sample rate**  ║   **Format**  ║ **File size** ║        **License**        ║
╠═══════════════╬═══════════╬═══════════╣═══════════════════════╣
║ 44100         ║ wav       ║ 22 GB     ║ [CC BY-NC-SA 2.0](https://creativecommons.org/licenses/by-nc-sa/2.0/)       ║
╚═══════════════╩═══════════╩═══════════╩═══════════════════════╝
```

# 匈牙利的

## CSS10 匈牙利语

与 CSS10 中的另一个子集相比， [CSS10 匈牙利语](https://www.kaggle.com/datasets/bryanpark/hungarian-single-speaker-speech-dataset)数据集的大小和音频长度大约是前者的一半。总共有大约 10 小时的基于 [Egri csillagok](https://librivox.org/egri-csillagok-by-geza-gardonyi/) 有声读物的简短录音。

```
╔═══════════════╦═══════════╦═══════════╦═══════════════════════╗
║  **Sample rate**  ║   **Format**  ║ **File size** ║        **License**        ║
╠═══════════════╬═══════════╬═══════════╣═══════════════════════╣
║ 22050         ║ wav       ║ 3.18 GB   ║ [CC0: Public Domain](https://creativecommons.org/publicdomain/zero/1.0/)    ║
╚═══════════════╩═══════════╩═══════════╩═══════════════════════╝
```

# 中国人

## CSS10 中文

[CSS10 中文](https://www.kaggle.com/datasets/bryanpark/chinese-single-speaker-speech-dataset)是 CSS10 集合中的低资源数据集之一。它只有来自两本有声读物的大约 6 个小时的数据集:

1.  [朝花夕拾 (Chao Hua Si She)](https://librivox.org/chao-hua-si-she-by-lu-xun/)
2.  [呐喊 (Call to Arms)](https://librivox.org/call-to-arms-by-xun-lu/)

它带有中文转录文本以及相应的拼音形式与语调。

```
╔═══════════════╦═══════════╦═══════════╦═══════════════════════╗
║  **Sample rate**  ║   **Format**  ║ **File size** ║        **License**        ║
╠═══════════════╬═══════════╬═══════════╣═══════════════════════╣
║ 22050         ║ wav       ║ 2.05 GB   ║ [CC0: Public Domain](https://creativecommons.org/publicdomain/zero/1.0/)    ║
╚═══════════════╩═══════════╩═══════════╩═══════════════════════╝
```

## 面包师

[Baker](https://www.data-baker.com/en/#/data/index/source) 数据集是汉语文语转换研究中常用的数据集之一。它包含大约 12 小时的音频数据，超过 10，000 个句子。

```
╔═══════════════╦═══════════╦═══════════╦═══════════════════════╗
║  **Sample rate**  ║   **Format**  ║ **File size** ║        **License**        ║
╠═══════════════╬═══════════╬═══════════╣═══════════════════════╣
║ 22050         ║ wav       ║ 2.05 GB   ║ Non-commercial        ║
╚═══════════════╩═══════════╩═══════════╩═══════════════════════╝
```

# 德国人

## CSS10 德语

[CSS10 德语](https://www.kaggle.com/datasets/bryanpark/german-single-speaker-speech-dataset)子集根据以下有声读物录制了约 16 小时的音频数据:

1.  梅斯特·弗洛
2.  [见](https://librivox.org/die-acht-gesichter-am-biwasee-by-max-dauthendey/)

```
╔═══════════════╦═══════════╦═══════════╦═══════════════════════╗
║  **Sample rate**  ║   **Format**  ║ **File size** ║        **License**        ║
╠═══════════════╬═══════════╬═══════════╣═══════════════════════╣
║ 22050         ║ wav       ║ 5.13 GB   ║ [CC0: Public Domain](https://creativecommons.org/publicdomain/zero/1.0/)    ║
╚═══════════════╩═══════════╩═══════════╩═══════════════════════╝
```

## 托尔斯滕之声

Thorsten-Voice 项目是一个针对德语的中立的单个说话者的语音数据(T2)。它模仿 LJSpeech 的元数据和文件结构。作者贡献了超过 23 小时的音频数据，使其成为最大的德语公开数据集之一。

```
╔═══════════════╦═══════════╦═══════════╦═══════════════════════╗
║  **Sample rate**  ║   **Format**  ║ **File size** ║        **License**        ║
╠═══════════════╬═══════════╬═══════════╣═══════════════════════╣
║ 22050         ║ wav       ║ 2.7 GB    ║ [CC Attribution 4.0](https://creativecommons.org/licenses/by/4.0/legalcode)    ║
╚═══════════════╩═══════════╩═══════════╩═══════════════════════╝
```

此外，该项目还提供了另一组[语音数据，带有以下情绪](https://zenodo.org/record/5525023):

*   🙂中立(19 分钟)
*   🤢厌恶(23 分钟)
*   😠愤怒(20 分钟)
*   😀开心(18 分钟)
*   😲惊讶(18 分钟)
*   😔困倦(30 分钟)
*   😵喝醉(25 分钟)
*   🤫窃窃私语(22 分钟)

```
╔═══════════════╦═══════════╦═══════════╦═══════════════════════╗
║  **Sample rate**  ║   **Format**  ║ **File size** ║        **License**        ║
╠═══════════════╬═══════════╬═══════════╣═══════════════════════╣
║ 22050         ║ wav       ║ 399.3 MB  ║ [CC Attribution 4.0](https://creativecommons.org/licenses/by/4.0/legalcode)    ║
╚═══════════════╩═══════════╩═══════════╩═══════════════════════╝
```

# 俄语

## CSS10 俄语

[CSS10 Russian](https://www.kaggle.com/datasets/bryanpark/russian-single-speaker-speech-dataset) 是 CSS10 集合中的高资源数据集之一。总之，这相当于长达 21 小时的录音。每个音频片段平均长度约为 5 至 10 秒。内容基于以下有声读物:

1.  [冰雪三月——ледянойпоход](https://librivox.org/ice-march-by-roman-gul/)
2.  [早期短篇小说](https://librivox.org/early-short-stories-by-zeev-jabotinsky/)
3.  [儿童和成人短篇小说](https://librivox.org/p-short-stories-for-children-and-adults-by-vsevolod-garshin/)

```
╔═══════════════╦═══════════╦═══════════╦═══════════════════════╗
║  **Sample rate**  ║   **Format**  ║ **File size** ║        **License**        ║
╠═══════════════╬═══════════╬═══════════╣═══════════════════════╣
║ 22050         ║ wav       ║ 6.79 GB   ║ [CC0: Public Domain](https://creativecommons.org/publicdomain/zero/1.0/)    ║
╚═══════════════╩═══════════╩═══════════╩═══════════════════════╝
```

# 希腊的

## CSS10 希腊语

[CSS10 希腊语](https://www.kaggle.com/datasets/bryanpark/greek-single-speaker-speech-dataset)包含 CSS10 集合中最少的音频录音。总长度仅相当于 4 小时的数据，这可能不足以训练适当的文本到语音模型。录音基于[παραμύθιχωρίςόνομα(没有名字的故事)](https://librivox.org/paramythi-horis-onoma-by-penelope-delta/)有声读物。

然而，这些数据提供了一个良好的开端，因为你几乎找不到公开可用的希腊语单个说话者的语音数据集。

```
╔═══════════════╦═══════════╦═══════════╦═══════════════════════╗
║  **Sample rate**  ║   **Format**  ║ **File size** ║        **License**        ║
╠═══════════════╬═══════════╬═══════════╣═══════════════════════╣
║ 22050         ║ wav       ║ 1.31 GB   ║ [CC0: Public Domain](https://creativecommons.org/publicdomain/zero/1.0/)    ║
╚═══════════════╩═══════════╩═══════════╩═══════════════════════╝
```

# 芬兰人的

## CSS10 芬兰语

在芬兰数据集中有大约 10 个小时的音频数据。每个音频片段的长度约为 5 到 10 秒。内容基于以下有声读物:

1.  [gulli verin matkat kaukaisilla mailla](https://librivox.org/gulliverin-matkat-kaukaisilla-mailla-by-jonathan-swift/)
2.  [ensimmiset 中篇小说](https://librivox.org/ensimmaeiset-novellit-by-juhani-aho/)
3.  [卡莱利-奥尔佳](https://librivox.org/kaleri-orja-by-heinrich-zschokke/)
4.  [萨尔梅兰·海因塔尔库特](https://librivox.org/salmelan-heinaetalkoot-by-olli-wuorinen/)

```
╔═══════════════╦═══════════╦═══════════╦═══════════════════════╗
║  **Sample rate**  ║   **Format**  ║ **File size** ║        **License**        ║
╠═══════════════╬═══════════╬═══════════╣═══════════════════════╣
║ 22050         ║ wav       ║ 3.35 GB   ║ [CC0: Public Domain](https://creativecommons.org/publicdomain/zero/1.0/)    ║
╚═══════════════╩═══════════╩═══════════╩═══════════════════════╝
```

# 阿拉伯语

## 阿拉伯语语音语料库

[阿拉伯语语音语料库](http://en.arabicspeechcorpus.com/)为阿拉伯语(大马士革口音)提供高质量的自然语音数据集。使用专业工作室记录数据集。

```
╔═══════════════╦═══════════╦═══════════╦═══════════════════════╗
║  **Sample rate**  ║   **Format**  ║ **File size** ║        **License**        ║
╠═══════════════╬═══════════╬═══════════╣═══════════════════════╣
║ 22050         ║ wav       ║ 1.11 GB   ║ [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)             ║
╚═══════════════╩═══════════╩═══════════╩═══════════════════════╝
```

# 结论

随着人工智能的快速发展，语音合成将成为建设智能国家的一个重要因素。希望上面的数据集将有助于你的人工智能项目和研究。

请让我知道你是否在其他单个说话者的语音数据集上有新的发现。我很乐意将它们包含在这篇文章中，以帮助那些有需要的人。

感谢你阅读这篇文章。祝你有美好的一天！

# 参考

1.  [CSS10 — Github](https://github.com/kyubyong/css10)
2.  [OpenSLR —资源](https://www.openslr.org/resources.php)