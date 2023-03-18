# 什么是 ODBC？

> 原文：<https://towardsdatascience.com/what-is-odbc-c27f95164dec>

## 了解数据库管理系统的 API

![](img/c1dec7189384fda00083c53c16ffb6f3.png)

卡斯帕·卡米尔·鲁宾在 [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral) 上的照片

开放式数据库连接(简称:ODBC)是一个用于 [SQL](https://databasecamp.de/en/data/sql-definition) [数据库](https://databasecamp.de/en/data/database)的标准化接口，允许人们访问不同的数据库管理系统并执行查询。目标是拥有一个独立于所选数据库工作的编程接口，从而可以连接到各种现有的数据库。

# 开放式数据库连接是如何工作的？

ODBC 于 1992 年首次推出。当时很难在数据库和应用程序之间建立通信，因为没有可用的标准化工具。

ODBC 的发展使得编写独立于数据库的应用程序成为可能。为此，使用了因数据库而异的驱动程序。他们将一般的查询翻译成关系数据库的特定语言。因此，还必须为每个数据存储安装单独的驱动程序。

这允许程序员提出一个标准的开放式数据库连接数据请求，然后根据驱动程序为正在使用的数据库进行翻译，例如 [MySQL](https://databasecamp.de/en/data/mysqls) 。此外，对存储器的访问权限也存储在驱动程序中，例如用户名和密码。

# ODBC 在哪个架构中使用？

假设一个应用程序使用来自两个不同关系数据库的数据，比如 MySQL 和 PostgreSQL。两个数据存储都包含只有在合并后才有价值的信息。但是，不可能将两个表存储在同一个数据库中。

ODBC 可以用来直接查询和合并数据，而不是费力地从一个表中复制信息并将其连接到另一个数据库。这是通过在数据库服务器上安装适当的驱动程序来实现的。然后，使用 SQL 查询，可以根据需要读取和合并信息。从该接口，合并的数据可以被进一步处理或转发。

# 用起来有什么好处和坏处？

ODBC 为开发人员提供了编写通用应用程序的可能性，因为它们独立于具体的数据库。只要内存遵循关系概念，接口就是可用的。如果一个人想要编程软件并出售它，这是特别有利的。

同时，人们可以用几个不同的应用程序访问同一个开放式数据库连接接口，因此更加灵活。然而，这种高灵活性的缺点是查询有时加载相对较慢，这会延迟事务的执行。因此，它不太适合加载时间非常重要的高性能应用。

此外，一些准备工作是必要的，以充分利用开放的数据库连接。对于每个数据源，必须安装适当的驱动程序，每个数据源的驱动程序各不相同。在复杂的系统环境中，这有时会很复杂，驱动程序也必须定期更新。

此外，驱动程序基于微软和 Windows。尽管 Linux 和 macOS 平台的驱动程序已经同时添加，但在个别情况下可能会出现问题，因为 ODBC 是为 Windows 开发和优化的。

# OLEDB 是什么？

OLEDB 也是微软开发的，为数据库提供应用编程接口(简称:API)。它提供了与 ODBC 相同的可能性，因此也被认为是开放式数据库连接的继承者。然而，它可以在更高的层次上获取数据，从而也可以查询非关系数据库，这被认为是相对于 ODBC 的一大优势。

一旦应用程序访问多个数据库(不仅仅是关系数据库)，就应该使用 OLEDB。

# 这是你应该带走的东西

*   ODBC 是关系数据库的标准化接口，它允许编程不依赖于特定数据库技术的应用程序。
*   这个接口为程序员提供了以简单和不复杂的方式组合几个数据库及其信息的可能性。
*   但是，使用它会导致比直接访问更长查询时间。此外，系统必须预先为数据库配备适当的驱动程序。

*如果你喜欢我的作品，请在这里订阅*[](https://medium.com/subscribe/@niklas_lang)**或者查看我的网站* [*数据大本营*](http://www.databasecamp.de/en/homepage) *！还有，medium 允许你每月免费阅读* ***3 篇*** *。如果你希望有****无限制的*** *访问我的文章和数以千计的精彩文章，不要犹豫，点击我的推荐链接:*[【https://medium.com/@niklas_lang/membership】](https://medium.com/@niklas_lang/membership)每月花$***5****获得会员资格**

*[](/comprehensive-guide-to-principal-component-analysis-bb4458fff9e2) [## 主成分分析综合指南

### 主成分分析的理论解释

towardsdatascience.com](/comprehensive-guide-to-principal-component-analysis-bb4458fff9e2) [](/why-you-should-know-big-data-3c0c161b9e14) [## 为什么您应该了解大数据

### 定义大数据及其潜在威胁

towardsdatascience.com](/why-you-should-know-big-data-3c0c161b9e14) [](/what-are-deepfakes-and-how-do-you-recognize-them-f9ab1a143456) [## 什么是 Deepfakes？

### 如何应对人工智能制造的误传

towardsdatascience.com](/what-are-deepfakes-and-how-do-you-recognize-them-f9ab1a143456)*