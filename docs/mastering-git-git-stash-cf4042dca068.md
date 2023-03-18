# 掌握 Git:“Git stash”

> 原文：<https://towardsdatascience.com/mastering-git-git-stash-cf4042dca068>

## 如何使用 git stash 来存储您不准备提交的更改

![](img/294e8b3875339e5eef95b39e51d9b925.png)

由 [Praveen Thirumurugan](https://unsplash.com/@praveentcom?utm_source=medium&utm_medium=referral) 在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上拍摄

Git 是所有数据科学家和软件工程师都应该知道如何使用的工具。无论您是独自从事一个项目，还是作为一个大型分布式团队的一部分，了解如何使用 Git 从长远来看都可以为您节省大量时间。虽然 git 对于清楚地查看您对存储库所做的更改的历史很有用，但是在某些情况下，您还没有准备好提交您对历史所做的更改。当 git 告诉您需要提交或者您将丢失您的更改时，这可能是一个挑战。当您想要更改分支或者从远程存储库中提取更改时，Git 通常会这样做。那么你能做什么呢？`git stash`来救援了！`stash`命令允许您“隐藏”您还没有准备好提交的更改，这样您就可以保存更改，而不必将它们添加到历史中。这将允许您轻松地更改分支或从远程存储库中提取，而不必担心丢失您的更改。那么它是如何工作的呢？

## **Git Stash**

git 的正常工作流程是编辑文件，准备变更，然后提交。这个工作流将创建一个清晰的提交历史，其中的工作明显地建立在彼此的基础上。它允许你进入你正在开发的特性的流程，做出清晰的改变，并且在一个编码会话中做出你通常的惊人的代码贡献。当然，这是理想的工作流程，但是在现实中，作为团队的一部分在工作环境中进行开发意味着您必须经常在一天中切换任务或职责。当您正在进行代码更改时，这可能会令人沮丧，因为您还没有准备好提交，但同时又不想丢失您的工作。您可能会被要求更改您正在处理的内容，因为出现了一个需要尽快解决的 bug，另一个开发人员要求您查看另一个分支，对您正在处理的分支进行了新的提交，您只想休息一下。此时，在您可以做任何其他事情之前，git 可能会告诉您对您所做的更改做一些事情。

如果您还不想创建新的提交(尽管您可以随时返回并编辑提交或消息)，您可以使用`git stash`保存未提交的更改。这个过程允许您处理存储库中的其他任务，而不会丢失到目前为止所做的更改。然后，当您想要恢复这些更改时，可以简单地重新应用这些更改，而不会影响提交历史。厉害！它是如何工作的？

## 使用 Git Stash

默认情况下，当您调用`git stash`时，您对跟踪文件所做的所有更改都将被转移到一个存储中。此时，您当前的工作目录将阻止返回到上次提交后的阶段。这意味着在那之后你所做的所有更改都将被保存在一个存储库中，你可以在以后访问它。

你藏起来的东西会包含:

*   对暂存文件所做的更改
*   对跟踪文件所做的更改(但未转移)

但是您需要知道，它不会自动包含:

*   工作目录中尚未暂存的新文件
*   有意忽略的文件

这是您需要注意的事情，尤其是当您处理涉及新文件的变更时。为了包括这一点，您可以使用标志`-u`，它将包括未被跟踪的文件，以及`-a`，它也将包括被忽略的文件。

一旦你创建了隐藏，做了你需要在其他地方做的改变，然后回到你工作的最初的分支，你会想知道你如何能把那些隐藏的改变拿回来？有两种方法可以做到:

*   `git stash apply` —将获取您存储在存储库中的变更，将它们应用到当前签出分支的工作目录中，并且将保持存储库的完整性。当您将更改拉至不同于最初开发的分支时，或者您正在编辑更改，但您可能希望保留最初的更改以备不时之需时，这很有用。重要的是，在它被清理之前，这个藏匿点在未来仍然存在，这意味着如果出现问题，你可以转换回原来的藏匿点。
*   `git stash pop` —还会将存储在存储中的更改应用到当前工作目录，但这将在应用更改后删除存储。这可以在你不在乎以后保留存储时使用，或者如果你计划对存储进行更改，并且不想在任何时候恢复到原始存储时使用。

这非常有用，尤其是对于存储您不准备与团队其他成员共享的变更。

然而，必须注意的是，这并不能代替将您的变更提交到存储库中。储藏只能适度进行。这是因为跟踪变更会变得很困难，尤其是在有多个 stashes 的情况下，因为它们的历史和它们包含的内容不像提交那样清楚。这意味着应该谨慎使用它们，只在需要的时候使用，否则更改应该提交！

## 附加功能

除了使用起来相对简单之外，git stash 是一个非常强大的工具，可以通过多种方式进行修改。

*   `git stash --patch`(或使用`-p`标志)将打开一个编辑器，允许你交互地选择你想要保存的变更和你想要保存在你的工作目录中的变更。当您不想隐藏所有的更改时，这很有用，因为您可能想要提交一些更改。
*   `git stash save "message"`将允许你添加一条消息到你的秘密物品中。当您有多个隐藏并且想要清楚地告诉变更包含什么或者它们为什么被隐藏时，这是特别有用的。如果你经常使用 stash，这是一个很好的实践，当你回去应用 stash 的变化时，它会使你的生活变得容易得多。
*   `git stash show`将显示您最近收藏的内容(文件更改的数量、添加的数量和删除的数量)。这有助于大致了解最新的存储内容，但是如果你想了解文件中的所有变化，你可以通过`-p`，它将显示与`git diff`相同的输出
*   如果你已经藏了不止一次,`git stash list`会显示所有已藏物品的列表。这将显示隐藏来自哪个分支和他们的隐藏索引(你如何能在隐藏之间选择)。默认情况下，在分支和创建存储的提交之上，所有存储都被标识为“WIP”(正在进行的工作)。
*   `git stash show stash@<index>`可用于显示特定存储的变化，例如`git stash show stash@{2}`将显示第三个存储的变化。这可以扩展到前面的命令，比如`git stash pop stash@{2}`，它将弹出第三个存储，而不是默认的最后一个存储更改。
*   `git stash drop`可用于从隐藏条目列表中删除单个隐藏条目。当您知道您在将来的任何时候都不会使用这些更改，并且保持您的 git 存储库没有任何未使用的更改时，这是非常有用的。`git stash clear`将其扩展到删除所有隐藏的更改，但要谨慎使用，因为在此之后很难恢复任何隐藏！
*   最后`git stash branch <branch_name>`可以用来从最新的存储中创建一个分支，并删除最新的存储。当您将存储应用到您的分支的最新版本之后出现冲突时，这可能是有用的(这可能发生，并且可能非常混乱！)

## 结论

如果 git 警告你不能做某件事，因为你没有提交修改`git stash`可以帮助你！它的工作原理是将更改存储到您不准备创建提交的文件中，确保当您更改分支、发出拉请求或只想提交您已经完成的部分工作时，工作不会丢失。这有时会很有用，可以存放多份，但要确保不要过度使用！与提交不同，隐藏可能很难跟踪，而且它们会被全面地记录，所以当您准备好发布您的更改时，就提交吧！

## 来源

[1][https://www . atlassian . com/git/tutorials/saving-changes/git-stash](https://www.atlassian.com/git/tutorials/saving-changes/git-stash)

[2][https://git-scm.com/docs/git-stash](https://git-scm.com/docs/git-stash)

如果你喜欢你所读的，并且还不是 medium 会员，请使用下面我的推荐链接注册 Medium，来支持我和这个平台上其他了不起的作家！提前感谢。

[](https://philip-wilkinson.medium.com/membership) [## 通过我的推荐链接加入 Medium—Philip Wilkinson

### 作为一个媒体会员，你的会员费的一部分会给你阅读的作家，你可以完全接触到每一个故事…

philip-wilkinson.medium.com](https://philip-wilkinson.medium.com/membership) 

或者随意查看我在 Medium 上的其他文章:

[](/eight-data-structures-every-data-scientist-should-know-d178159df252) [## 每个数据科学家都应该知道的八种数据结构

### 从 Python 中的基本数据结构到抽象数据类型

towardsdatascience.com](/eight-data-structures-every-data-scientist-should-know-d178159df252) [](/a-complete-data-science-curriculum-for-beginners-825a39915b54) [## 面向初学者的完整数据科学课程

### UCL 数据科学协会:Python 介绍，数据科学家工具包，使用 Python 的数据科学

towardsdatascience.com](/a-complete-data-science-curriculum-for-beginners-825a39915b54) [](https://python.plainenglish.io/a-practical-introduction-to-random-forest-classifiers-from-scikit-learn-536e305d8d87) [## scikit-learn 中随机森林分类器的实用介绍

### UCL 数据科学学会研讨会 14:什么是随机森林分类器、实现、评估和改进

python .平原英语. io](https://python.plainenglish.io/a-practical-introduction-to-random-forest-classifiers-from-scikit-learn-536e305d8d87)