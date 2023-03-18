# 我在亚马逊 SDE 实习时学到的三课

> 原文：<https://towardsdatascience.com/three-lessons-i-learnt-as-an-sde-intern-at-amazon-19e78c8cc608>

## 以及它们如何让你成为更好的开发人员和数据科学家…

![](img/da7e0039ca5f45f6736e1a9115ecb42d.png)

照片由 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上的 [Fotis Fotopoulos](https://unsplash.com/@ffstop?utm_source=medium&utm_medium=referral) 拍摄

上个月，我作为一名软件开发工程师结束了在伦敦亚马逊为期 3 个月的[实习。在实习期间，我学到了很多东西，成功地参与了一些令人惊叹的项目，并与一些才华横溢的人一起工作。我知道在编程方面我还有很多要学，但实习也教会了我，编码并不是成为软件工程师或数据科学家的全部。为此，以下是我在亚马逊工作期间学到的三条主要经验，以及它们为什么/如何让我在未来成为更好的软件工程师或数据科学家。](/how-i-landed-an-amazon-sde-internship-without-a-computer-science-degree-85596c480d4d)

## 反馈很重要

如果你想成为一名优秀的软件开发人员/工程师，反馈非常重要。这不仅包括通过代码评审等过程对代码的反馈，还包括一对一、团队会议和文档评审。为了提高你作为一名软件工程师的能力，你必须能够接受这些反馈，从中学习，然后确保你在前进中使用这些反馈。

在编写任何代码之前，我收到反馈的第一个地方是与我的经理、导师、入职伙伴和其他团队成员的一对一会议。这些反馈包括我的进展如何，我应该注意什么，以及我如何适应团队的其他成员。这意味着我可以快速适应，提出问题，并确保我一直朝着正确的方向前进，也意味着我可以更快地加入团队并成为有用的成员。加入一个新团队通常是一个很大的问题，需要吸收大量的信息；在关注什么的指导下，我能够确保尽可能快地做出贡献。这种情况在整个实习期间都在持续，之后的反馈是关于我的进步，或者关于我如何解决问题，我是否有什么可以改进的地方。

我能够通过文档审查过程在团队环境中获得反馈。由于亚马逊是一家以客户为导向和关注焦点的公司，我必须确保我的任何想法或想法对客户都是有用的。在我的例子中，由于我正在构建一个内部工具，这意味着我必须构建一些我的团队能够使用的东西。在这一阶段，所有团队都根据我整理的文档对项目的特性、外观和实现进行了评论，这一阶段的反馈有助于确保最终项目与他们相关。如果没有这个反馈，这个项目就不会满足客户的需求，而且在我离开后，它很可能会被丢弃！不过现在，我被放在了正确的轨道上，以确保团队可以在未来使用。

最后，在代码评审的过程中，我也收到了对我的代码的反馈。这是第一次有人对我的代码、结构、实现以及我是如何写的给出直接反馈。这当然是一个非常伤脑筋的过程，但它设法极大地改善了最终的实现。我挑选了一些东西，并尽我所能在下一个版本和将来的提交中实现，同时也为将来提供了一些有用的提示。这直接有助于提高我的代码质量，虽然我还有很多需要改进的地方，但我希望这将为我未来的成功做好准备。

我将继续寻找反馈，只要它是可用的和合适的。虽然我可以自己学到很多东西，并构建一些伟大的项目，但最终其他人可能会有不同的观点或经验，最终为客户带来更好的代码、更好的过程和更好的产品。

## 干净的代码

这一课是上一课的继续，因为代码和文档审查的过程表明，干净的代码对于为客户创建持久和健壮的产品是非常重要的。这意味着代码应该简单实现，高效，可读/可理解。干净的代码应该以一种合乎逻辑的方式流动，以至于不熟悉基础知识的人应该能够相对容易地理解一段代码的内容和目的，而不需要太多的预先理解或文档。

我不是说文档或注释不重要，但是代码应该能够自己说话。在这方面，我还有很多要学的，但我从这一课中学到的要点包括:

*   变量和函数的名字应该说明它们在做什么或者有什么用。它们应该清晰易懂。如果不是这样，那么你的代码可能很难阅读和调试，当你有一个大的代码库时，这可能会使生活困难 10 倍。这包括确保命名约定在整个代码中保持一致，否则事情会变得混乱和不清楚。
*   一个函数应该只做一件事。如果它做的不止一件事，它应该被分解，以便更容易理解和测试，最终确保更健壮的代码。同样，当您有一个非常大的代码库时，这也很有用，因为这意味着您可以很容易地隔离错误出现的地方并修复它，而不必深入代码本身。
*   文件结构和命名很重要。这与变量和函数的命名点密切相关，但是确保很容易找到代码并且类似的代码被捆绑在一起对于调试和理解代码库的功能是很重要的。对于一个大的代码库来说，这可能会变得更加复杂，但这使得它在浏览各种文件时变得更加重要。
*   最后，虽然不是代码本身，但是提交应该是为了特定的目的并且很小。一个涵盖对代码库的多个更改的大提交将很难看到哪里引入了 bug，以及如果需要，如何回滚更改。分离提交，并清楚地说明它们的目的，可以帮助代码的长期可维护性。

所有这些都应该符合你写作的语言或目的的公认惯例。这包括在整个代码库中保持一致性，这样就不会出现混乱，尤其是当您在一个有多人参与的项目中工作时。所有这些最终将有助于代码的可维护性和可改进性，不仅对您自己，而且对您的整个团队都是如此。

虽然在实习前我就知道很多，因为没有人检查我的代码，我不知道我是否遗漏了什么，或者我所做的是否正确。在漫长的一天编码之后，通常很难对自己进行管理，并且您也不完全确定自己在寻找什么。虽然这并不意味着你不应该坚持高标准，或者你应该依赖他人来解决你的代码，但这意味着一个好的团队可以确保高标准得到保持，并且你们可以不断地互相学习。代码审查过程帮助我学到了很多东西，希望能提高我的代码可读性和目的性，希望能为我自己和团队改进未来的编码承诺。

## 知道去哪里寻找答案

我学到的最后一课是知道去哪里寻找答案。就其本身而言，这可能意味着许多不同的事情。这可能意味着知道如何搜索您需要的代码片段，在哪里可以找到关于已知框架或库的文档，在特定任务中向谁寻求帮助，或者在哪里和什么时候花时间自己解决项目，而不是依赖他人。这对于确保您以高效的方式工作很重要，这样您就可以解决为您设定的任务，同时也意味着您作为一名软件工程师正在发展和学习。

任何软件工程师的工具箱的一个重要部分是能够有效地谷歌找到我们需要的相关代码。无论是修复一个 bug 还是引入一个新特性，技巧通常是相同的。其中一部分还包括知道什么时候简单地复制和粘贴一段代码，以及什么时候深入了解解决方案的工作原理。在某些情况下，谷歌代码仅仅是为了提醒你如何用给定的语言做一些简单的事情，比如循环，或者因为你忘记了一个函数或模块的名字。在这种情况下，从互联网上获取代码应该不成问题，因为这只是复习。然而，在后一种情况下，当查看新代码时，理解它在做什么以及如何做通常是很重要的。这不仅是出于安全原因(您不希望代码库中有不稳定的代码)，也是为了确保下次遇到类似的问题或错误时，您可以更快地修复它，并有更好的理解。否则，我们将花费所有的时间在谷歌上搜索，而不是自己编写代码。

第二部分是知道什么时候尝试自己解决问题，什么时候寻求帮助。第一部分的意思是，在某些情况下，为你做一点点工作可以让你相当快地、不费吹灰之力地找到解决方案。这意味着你不必阻止其他人做他们自己的生产性工作，同时也确保你作为一个软件工程师在成长和学习。这可以确保你将来能够解决类似的问题，成为团队中更有价值的一员。即使你没有找到解决方案，当你需要向别人寻求帮助时，拥有一些潜在的代码会有所帮助，因为你可以向别人展示你至少尝试过解决问题。这可以帮助他们快速上手，并确保他们不必浪费时间想出和你一样的解决方案。当你在与一项新技术互动时，你也可以找一个更有经验的人，确保他们可以为你提供资源，帮助你快速入门并走上正确的方向。

最后一部分是知道去找谁来有效地解决问题。在某些情况下，这可能是团队成员，甚至是团队之外的人，他们以前使用过类似的技术。在其他情况下，它包括知道你可以问谁可能认识某人来帮助，无论是你的经理，你的入职伙伴还是你的导师。这意味着你需要有一个强大而良好的人际网络，你可以依靠他们，但这也意味着你不需要认识每个人。否则，如果你不知道该去找谁，你可能会被困很长时间，这对你的进步没有帮助。你也不应该害怕寻求这种帮助，因为大多数软件工程师都应该理解被困在一个问题上而不知道去哪里是什么感觉。

因此，知道去哪里寻找答案可能意味着不同的事情，无论是知道如何正确地谷歌，知道什么时候花时间自己解决问题，或者什么时候该举手说你卡住了。通常团队会有一个机制来促进这类事情，无论是日常站立或定期团队会议，这将有助于你发展这种技能。这也是一项需要很长时间才能掌握的技能，当我完成更多的任务并理解不同的界限时，我当然还在学习。

## 结论

我了解到反馈对于成为一名软件工程师的各个方面都很重要，干净的代码对于创建和生产健壮且可持续的产品很重要，知道去哪里寻找答案可以极大地加快你的开发过程。在大多数情况下，我仍然有很多东西要学习和掌握，但它们肯定是我未来将继续学习的课程，并且肯定会帮助我成为一名更好的软件工程师或数据科学家。我希望这些也是其他人可以学习的经验，并且这些方面中的每一个对于继续成为更好的开发人员都是重要的。我希望这对我的职业生涯和我最终加入的任何团队都有好处。

如果你喜欢你所读的，并且还不是 medium 会员，请使用下面我的推荐链接注册 Medium，来支持我和这个平台上其他了不起的作家！提前感谢。

[](https://philip-wilkinson.medium.com/membership) [## 通过我的推荐链接加入 Medium—Philip Wilkinson

### 作为一个媒体会员，你的会员费的一部分会给你阅读的作家，你可以完全接触到每一个故事…

philip-wilkinson.medium.com](https://philip-wilkinson.medium.com/membership) 

或者随意查看我在 Medium 上的其他文章:

[](/how-i-landed-an-amazon-sde-internship-without-a-computer-science-degree-85596c480d4d) [## 我是如何在没有计算机科学学位的情况下获得亚马逊 SDE 实习机会的

### 或者解决数百个黑客排名问题…

towardsdatascience.com](/how-i-landed-an-amazon-sde-internship-without-a-computer-science-degree-85596c480d4d) [](/eight-data-structures-every-data-scientist-should-know-d178159df252) [## 每个数据科学家都应该知道的八种数据结构

### 从 Python 中的基本数据结构到抽象数据类型

towardsdatascience.com](/eight-data-structures-every-data-scientist-should-know-d178159df252) [](/a-complete-data-science-curriculum-for-beginners-825a39915b54) [## 面向初学者的完整数据科学课程

### UCL 数据科学协会:Python 介绍，数据科学家工具包，使用 Python 的数据科学

towardsdatascience.com](/a-complete-data-science-curriculum-for-beginners-825a39915b54)