# 机器学习中如何准备 K 重交叉验证的数据

> 原文：<https://towardsdatascience.com/how-to-prepare-data-for-k-fold-cross-validation-in-machine-learning-924a44ec322c>

![](img/ae7c6f1b051dc15605daadb4190a2ec6.png)

作者图片

交叉验证是第一个用来避免过度拟合和数据泄漏的技术，当我们想要在我们的数据上训练一个预测模型的时候。

它的功能是必不可少的，因为它允许我们**以一种安全的方式**对我们的数据进行功能和逻辑测试——也就是说，避免这些过程污染我们的验证数据。

如果我们想做预处理、特征工程或其他转换，**我们必须首先正确地划分我们的数据。**

这确保了我们的验证数据实际上代表了我们的训练集，并且(可能)也代表了我们还没有的真实世界的数据。

因此，如果我们能够[创建一个数据集](/building-your-own-dataset-benefits-approach-and-tools-6ab096e37f2)并对我们的数据进行适当的划分，那么我们就可以相对确定我们从训练中观察到的结果实际上是可用的并且是无偏差的。

# 如何为交叉验证准备数据

正如我在关于[交叉验证以及如何在 Python](/what-is-cross-validation-in-machine-learning-14d2a509d6a5) 中应用它的文章中所写的，其中一个基本步骤是根据折叠(数据集部分)对**目标变量进行分层。**

这样做是为了防止可能的类不平衡对模型的性能产生负面影响。

例如，在二元分类的情况下，可能 80%的类别是肯定的，而只有 20%是否定的。训练模型而不考虑这种不平衡可能会导致不可靠的结果。

有一些数据平衡技术，但是我们不会在本文中涉及它们。相反，我将解释如何使用 Python、Pandas 和 Sklearn **创建一个带有额外列的数据集，该列将指示数据集中的一行属于哪个文件夹。**

> 对于数据集的每个样本，我们将指出它属于哪个折叠，以便我们可以在每个折叠上测试我们的算法，使我们的评估总体上更加稳健。

让我们看看如何在 Python 中应用这个过程。

让我们从导入基本库开始

```
import pandas as pd
from sklearn import model_selection
```

假设我们的训练数据在路径为`./data/dataset_train.csv`的文件中，让我们用 Pandas 导入它，并创建一个名为 fold 的列，我们用值-1 初始化它。这是因为我们的折叠值将从 0 开始。

```
# import our training dataset
df = pd.read_csv("./data/dataset_train.csv")

# define a new column named 'fold'
df["fold"] = -1
```

通常数据集是混洗的——我们使用`.sample`进行推理。我们将使用参数`frac=1`告诉 Pandas 获取整个数据集并随机采样。事实上，这将以简单有效的方式打乱数据集的每一行。

```
df = df.sample(frac=1).reset_index(drop=True)
```

既然我们已经打乱了数据集，我们可以定义我们的目标变量，将其传递给`sklearn.model_selection.StratifiedKFold`来对数据集进行分层。我们将使用一个任意的数字 5 作为我们的折叠。

一旦创建了对象，我们就遍历数据集的每一行，并将 Sklearn 生成的部分应用于之前具有常数值-1 的列。

完成后，我们保存数据集。

```
y = df["target"].values

# we initialize the kfold object with 5 slices
kf = model_selection.StratifiedKFold(n_splits=5)

# populate the fold column
for fold, (train_idx, valid_idx) in enumerate(kf.split(X=df, y=y)):
    df.loc[valid_idx, "fold"] = fold

# save the dataset
df.to_csv("./data/dataset_train_folds.csv")
```

现在我们有了一个数据集，除了它最初拥有的列之外，现在还有一个额外的列来指示要在其上执行验证的折叠。

让我们看看整个剧本。

```
import pandas as pd
from sklearn import model_selection

if __name__ == "__main__":

    # import our training dataset
    df = pd.read_csv("./data/dataset_train.csv")

    # define a new column named 'fold'
    df["fold"] = -1

    # shuffle the dataset
    df = df.sample(frac=1).reset_index(drop=True)

    # initialize the target variable y
    y = df["target"].values

    # we initialize the kfold object with 5 slices
    kf = model_selection.StratifiedKFold(n_splits=5)

    # populate the fold column
    for fold, (train_idx, valid_idx) in enumerate(kf.split(X=df, y=y)):
        df.loc[valid_idx, "fold"] = fold

    # save the dataset
    df.to_csv("./data/dataset_train_folds.csv")
```

现在我们可以运行这个脚本，只需简单地更改数据集在磁盘上的路径，就可以创建一个带有验证折叠的副本**。**

**这种方法是完全可扩展的，几乎可以用于任何机器学习问题。**

# 结论

在这篇简短的文章中，我与你分享了一段代码，我可能会在每个机器学习项目中使用**。**

事实上，在即将到来的项目中不使用它对我来说会很奇怪。**它适用于传统的机器学习，也适用于深度学习。**

一旦数据被分割成多个折叠，我们就可以遍历每个折叠，一次一个折叠地测试我们的假设。这是强大的。

**如果您想支持我的内容创作活动，请随时关注我下面的推荐链接，并加入 Medium 的会员计划**。我将收到你投资的一部分，你将能够以无缝的方式访问 Medium 的大量数据科学文章。

<https://medium.com/@theDrewDag/membership>  

我希望我对你的教育有所贡献。下次见！👋