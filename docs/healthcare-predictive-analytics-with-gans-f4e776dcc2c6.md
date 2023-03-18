# 利用 GANs 进行医疗保健预测分析

> 原文：<https://towardsdatascience.com/healthcare-predictive-analytics-with-gans-f4e776dcc2c6>

## 用 GANs 增加不平衡的医疗再入院数据

![](img/a83412946ff05d4cc5529aa8baa0d28f.png)

由[像素](https://www.pexels.com/photo/ambulance-architecture-building-business-263402/)上的[像素](https://www.pexels.com/@pixabay/)生成的图像

生成对抗网络(GANs)是 Ian Goodfellow 及其同事在 2014 年开发的一类深度学习模型。在高层次上，gan 由两个竞争的神经网络组成，这两个神经网络构成了一个零和游戏。这意味着一个神经网络代理的收益对应于另一个代理的损失。具体来说，GAN 算法训练鉴别器来区分真实数据和合成数据，同时训练生成器来产生可以欺骗鉴别器的合成数据实例。

GANs 有各种各样的应用，包括图像生成、图像到图像的转换、表格数据扩充等等。数据扩充用例很有趣，因为它可以用来扩充不平衡数据集，以进行离群点检测，这在行业中有广泛的应用。例如，在医疗保健空间数据中，使用 GANs 进行增强可用于改进预测患者再入院的机器学习模型。

患者再次入院对应于在特定时间间隔后，入院的患者返回同一家或另一家医院的事件。患者再入院率是衡量治疗和护理质量的一个很好的指标。高再入院率意味着较差的患者结果和较高的手术成本。事实上,《平价医疗法案》( ACA)对高再入院率的医疗服务提供者进行了处罚。也就是说，医疗保健提供者通过提供更高质量的护理来降低再入院率。

造成高再入院率的因素有很多。这包括年龄、体重、地理位置、合并症、多种药物等等。例如，老年患者更有可能再次入院，因为他们有更多的慢性病和疾病。体重，尤其是肥胖，也起着很大的作用，因为超重和肥胖的人更有可能患有心脏病、癌症和其他严重的并发症。

目前大多数降低再入院率的尝试包括理解 ACA 政策、识别高风险患者、药物调和、预防保健获得性感染以及良好的移交沟通。例如，ACA 制定了减少再入院计划，激励医疗服务提供者提高医疗质量。此外，能够根据病史和人口统计数据识别高危人群也很重要。医疗协调包括确保患者的药物清单尽可能是最新的。这有助于降低因服用多种药物而导致的药物相关不良事件的风险。

接受多种药物治疗的患者也很有可能再次入院。这很大程度上是由于需要这些药物治疗的合并症。多重用药还会导致药物相互作用，这可能会导致出院后的不良事件，增加再次入院的可能性。采取措施预防这些类型的感染可以降低再次入院的可能性。最后，不干涉交流很重要，因为它包含了对患者病情和治疗计划的清晰记录。如果在不干涉交流过程中遗漏了任何相关因素的信息，如多药或共病，可能会增加再入院的可能性。

除了手动监控这些再入院因素，医疗保健提供商还可以利用机器学习来帮助识别和锁定高危人群。在过去，基于各种风险因素训练的逻辑回归模型被用于预测再入院的概率。这些模型可以与人工检查配合使用，以采取预防措施来降低再入院率。

鉴于医疗保健数据高度敏感和机密，访问用于建模的数据源可能会很困难。尽管存在这些挑战，但仍有许多开源工具可用于创建真实代表预测建模所需因素的合成数据集。合成数据具有匿名、免费使用和公开共享的优势。尽管数据是合成的，但有了足够的领域专业知识，就可以生成一个具有高度代表性的数据集，并应用于各种用例中。

[Faker](https://faker.readthedocs.io/en/master/) 是一款开源 python 工具，可用于生成各种行业垂直领域的合成数据，包括金融、零售和医疗保健。我们将了解如何使用 Faker 生成合成的医疗保健再入院数据，并将其用于预测建模。我们将包括许多已知的导致再入院风险的因素。然后，我们将基于高风险因素，以基于规则的方式为我们的机器学习模型定义再入院目标。

鉴于再入院并不常见，我们将此数据集建模为不平衡数据集，其中大部分数据由在规定时间范围内未再入院的患者组成。我们将构建一个基线 catboost 模型，用于比较数据扩充前后的性能。然后，我们将使用表格生成对抗网络( [tabgans](https://github.com/Diyago/GAN-for-tabular-data) )来扩充我们的不平衡数据。最后，我们将建立一个 catboost 第二分类模型，用于根据我们的扩充数据预测患者再入院。

对于这项工作，我将在 [Deepnote](https://deepnote.com/) 中编写代码，这是一个协作数据科学笔记本，使运行可重复的实验变得非常容易。

## **用 Faker 生成合成数据**

首先，让我们导航到 Deepnote 并创建一个新项目(如果您还没有帐户，可以免费注册)。

让我们创建一个名为“synthetic_data”的项目，并在这个项目中创建一个名为“tabgan_experiment”的笔记本:

![](img/0864f82ea37f03786d547de19ed48822.png)

作者截图

让我们安装将要使用的软件包:

作者创建的嵌入

接下来，让我们导入 Faker，并为将要生成的合成数据的大小定义一个变量。我们将生成一个包含 5000 行的数据集:

作者创建的嵌入

接下来，让我们定义一个 Faker 对象，并将其存储在一个名为“fake”的变量中:

```
fake = Faker()
```

让我们设置一个种子，以便我们的结果是可重复的，并初始化一个名为 names 的列表，我们将使用它来存储我们的合成名称:

```
Faker.seed(42)
names = []
```

现在让我们在 for 循环中用合成名称填充列表。为此，我们调用 faker 对象上的 name()方法来生成合成名称:

```
for i in range(0,DATA_SIZE):
    names.append(fake.name())
```

完整的单元格如下:

作者创建的嵌入

通过在 for 循环中调用 faker 对象上的 state()方法，我们可以为美国状态做一些类似的事情:

作者创建的嵌入

对于我们的示例，我们将考虑患者被重新接纳到急诊部的场景:

作者创建的嵌入

我们还将指定性别:

作者创建的嵌入

接下来，让我们导入 numpy 并使用 random.normal 生成平均值为 50 岁、标准差为 20 年的正态分布年龄:

作者创建的嵌入

让我们也生成体重的正态分布值，平均值为 180 磅，标准偏差为 70 磅:

作者创建的嵌入

让我们对以英寸为单位的高度做同样的事情:

作者创建的嵌入

我们还可以定义一个字段来指定患者是否吸烟:

作者创建的嵌入

另一个详细说明了病人在急诊室呆了多少天:

作者创建的嵌入

接下来，我们将使用动态提供者方法从外部列表或源中随机选择元素。让我们导入动态提供者:

```
from faker.providers import DynamicProvider
```

让我们定义一个带有健康保险列表的动态提供者对象:

```
health_insurance_provider = DynamicProvider(
provider_name="health_insurance",
elements=["UnitedHealth Group", "Anthem", "Aetna", "Cigna", "Humana", "Medicare"],
)
```

现在，我们将为可再现性设置一个随机种子，并将我们的健康保险提供商对象添加到我们的 faker 对象中:

```
Faker.seed(42)
fake.add_provider(health_insurance_provider)
```

我们现在可以将随机选择的保险附加到我们的保险列表中:

```
insurance = []
for i in range(0, DATA_SIZE):
    insurance.append(fake.health_insurance())
```

完整的单元格如下:

作者创建的嵌入

接下来，让我们使用我们的列表创建一个熊猫数据框架:

作者创建的嵌入

让我们也从我们的体重和身高值计算身体质量指数:

作者创建的嵌入

我们的目标是创建一个数据集，用于训练再入院分类模型。接下来我们需要做的是为重新接纳生成目标标签。让我们从生成一些随机分配的标签开始。这将成为我们通常在真实数据中发现的噪声:

```
df['readmission'] = [np.random.randint(0,2) for x in range(0, DATA_SIZE)]
```

faker 对象的 names 方法生成的名称不一定是惟一的，所以让我们去掉重复的名称:

```
df.drop_duplicates('name', inplace=True)
```

接下来，让我们对 20%的结果数据进行采样，并将其存储在一个名为 df_sample1 的新数据帧中。该数据框将构成我们的阴性和阳性再入院结果的噪声值:

```
df_sample1 = df.sample(frac=0.2, replace=True, random_state=1)
```

其余 80%的数据将存储在另一个名为 df_sample2 的数据帧中:

```
df_sample2 = df[~df['name'].isin(list(set(df_sample1['name'])))]
```

我们将使用 df_sample 2 来定义我们的基本事实标签。重新接纳值将为 0 或 1。重新入院值为 0 表示患者在指定的时间段后没有重新入院。值为 1 表示患者已再次入院。这通常是 30 天或 60 天，但出于我们的目的，我们不必担心确切的值，因为这都是合成数据。让我们将 df_sample2 中的所有重新接纳值初始化为 0

```
df_sample2['readmission'] = 0
```

接下来，让我们将所有身体质量指数> 30、吸烟、有医疗保险且在急诊室停留> 5 天的患者标记为再入院值为 1:

```
df_sample2.loc[(df_sample2.bmi >=30) & (df_sample2.smoker == 'Yes') & (df_sample2.insurance == 'Medicare') & (df.length_of_stay >= 5), 'readmission'] = 1
```

最后，让我们将 df_sample1 追加到 df_sample2，并将结果存储在新变量 df 中:

```
df = df_sample2.append(df_sample1)
```

完整的单元格如下:

作者创建的嵌入

接下来，让我们使用计数器方法来查看 0 和 1 再入院结果的数量。如我们所见，数据不平衡，517 个再入院值等于 1，4405 个再入院值等于 0:

作者创建的嵌入

## 构建 Catboost 分类器

现在，我们可以开始为分类模型准备数据了。让我们将分类列转换成机器可读的代码。虽然 catboost 可以直接处理分类变量，但这将使以后使用 tabgan 更加容易:

作者创建的嵌入

我们现在可以为建模定义输入和输出。我们将使用“保险”、“性别”、“吸烟者”、“州”、“身高”、“体重”、“bmi”、“住院时间”来预测“再次入院”:

作者创建的嵌入

接下来，让我们将数据分为训练和测试两部分:

作者创建的嵌入

现在让我们导入 catboost 包:

作者创建的嵌入

我们现在可以定义我们的模型对象，并使它适合我们的训练数据。为简单起见，我们对 catboost 模型使用 10 次迭代(与 n_estimators 相同):

作者创建的嵌入

现在让我们来评估我们模型的性能。由于我们的数据是不平衡的，精度是一个很好的度量标准，用于衡量模型预测代表性不足的类别的效果。精度值为 1.0 意味着模型具有完美的精度:

作者创建的嵌入

我们看到，该模型预测测试集中的所有值都具有 0 的重新接纳值，即使测试集中有 146 个 1 的基本真值。这相当于精度值为 0。在不平衡数据上构建分类模型时，这是一个典型的问题。理想情况下，表格形式的 GANs 可以帮助我们通过数据扩充来提高模型精度。

## 用 Tabgan 扩充数据

让我们从导入 tabgan 开始:

```
from tabgan.sampler import GANGenerator
```

让我们定义列、输入和输出，并重置索引:

```
cols = ['insurance', 'sex', 'smoker', 'state', 'height', 'weight', 'bmi', 'length_of_stay', 'readmission']X = df[cols[:-1]]
y = pd.DataFrame(list(df['readmission']), columns=['readmission'])X.reset_index(inplace=True, drop=True)
y.reset_index(inplace=True, drop=True)
```

接下来，我们将拆分数据用于培训和测试:

```
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3, random_state=42)X_train.reset_index(inplace=True, drop=True)
y_train.reset_index(inplace=True, drop=True)
X_test.reset_index(inplace=True, drop=True)
```

最后用生成器生成我们的合成数据。该代码将生成输入(new_train2)和输出(new_target2)的新数据帧，其中合成输入数据被附加到 X_train 并存储在 new_train2 中，合成目标值被附加到 y_train 并存储在 new_target2 中。如果您对与 GANGenerator 和 generate_data_pipe 相关的参数感兴趣，请参见 [tabgan 文档](https://pypi.org/project/tabgan/)。

```
new_train2, new_target2 = GANGenerator(cat_cols = cols, epochs=2, is_post_process=False).generate_data_pipe(X_train, y_train, X_test,use_adversarial=False, only_generated_data=False)
```

完整的单元格如下:

作者创建的嵌入

我们现在可以使用计数器方法来查看重新接纳的 1 和 0 的分布:

我们看到产生了更多的数据。在我们的原始数据集中，有 4405 个再入院值等于 0，517 个再入院值等于 1。与上面的截图相比，我们现在有 8102 个值等于 0，2921 个值等于 1:

作者创建的嵌入

我们还可以显示新的输入数据 new_train2:

作者创建的嵌入

现在，让我们在扩充数据上训练一个新的 catboost 模型:

作者创建的嵌入

并评估性能:

作者创建的嵌入

我们看到我们在精度上有了一点点提高。这可以通过调节恒发生器的超参数进一步改善。例如，您可以尝试将纪元的数量从 2 增加到更大的数字，如 50 或 100。

这篇文章中使用的代码可以在 [GitHub](https://github.com/spierre91/deepnote) 上找到。

## 结论

在这里，我们看了如何使用开源 python 包来考虑预测患者再入院的真实医疗保健用例。首先，我们使用 faker 软件包生成患者属性，随后我们使用这些属性来训练再入院分类模型。然后，我们看到了如何使用 tabgan 包来扩充我们用由我们的 GANgenerator 生成的合成值生成的训练数据。我们发现，通过这种数据扩充方法，我们能够提高分类模型的精度。这种数据扩充的方法也可以用于这里没有提到的医疗保健预测问题。这包括罕见疾病检测、不良药物相互作用事件、基于价值的护理的患者人群风险分类等等。