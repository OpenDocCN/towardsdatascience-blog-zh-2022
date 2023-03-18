# BigQuery 的 SQL 反模式

> 原文：<https://towardsdatascience.com/bigquery-anti-patterns-dacb61f8a3f>

## 在 Google Cloud BigQuery 上运行 SQL 的最佳实践和需要避免的事情

![](img/af7bf0ca5e407698e0b8ac3bee3b2c30.png)

[杰克·卡特](https://unsplash.com/@carterjack?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)在 [Unsplash](https://unsplash.com/s/photos/idea?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) 上拍照

**BigQuery** 是**谷歌云平台上的托管**数据仓库**服务，**像大多数服务和技术一样，它有一套使用时需要牢记的原则。

在接下来的几节中，我们将概述一组**最佳实践**，以避免通常会对 BigQuery 性能产生负面影响的常见反模式。应用最佳实践很重要，主要有两个原因——它们将帮助您**编写更高效的查询**,同时，如果应用正确，将**降低您的成本**。

## 避免选择*

从结果集中选择所有字段是一种非常常见的反模式，应该尽可能避免。`SELECT *`将导致对表中的每一列进行完全扫描，这意味着这将是一个执行开销很大的操作。

> 仅查询您需要的列

还要记住`LIMIT`不会减少读取的字节量，因此，您仍然需要为每一列的完全扫描付费。因此，请确保只查询您实际需要的列。如果您仍然需要运行`SELECT *`,那么考虑对您的表进行分区，这样您将能够查询驻留在一个或一些分区中的数据。

## 避免自连接

在表上执行自连接是另一件应该避免的事情。自然有人会问两个独立表的连接和自连接有什么区别。

答案是否定的——这几乎是一回事，但这里的要点是，无论何时您要执行自连接，都有可能使用窗口函数来实现相同的结果，这是一种更优雅的方式。

> 避免自连接，而使用窗口函数

自联接可能会增加输出行数，这意味着它会降低查询性能，还会导致处理的字节数增加，从而增加运行此类查询的成本。

## 处理数据偏斜

数据偏斜是当您的数据被划分为大小不均匀的分区时出现的现象。在后台，BigQuery 会将这些分区发送到插槽中，这些插槽是用于以分布式方式执行 SQL 查询的虚拟 CPU。

因此，分区不能跨不同的插槽共享。如果您创建了不平衡的分区，这意味着一些插槽最终会比其他插槽有更多的工作负载，而在某些极端情况下，过大的分区甚至会使插槽崩溃。

当您基于包含比其他值更频繁出现的值的键/列对表进行分区时，您很可能会得到大小不等的分区。在这种情况下，尽早应用过滤器将有助于缩小这种不平衡。

> 如果你的数据有偏差，尽早应用**过滤**

此外，您可能还需要重新考虑分区键。例如，您可能希望避免使用具有许多`NULL`值的键对表进行分区，因为这将为此类行创建一个巨大的分区。一个常用的分区键是一个日期字段，它可以确保数据在不同分区上的均匀分布(假设每天/每月/每年的数据量大致相同)。

## 交叉连接

交叉连接用于生成两个表之间的笛卡尔积，即包含相关表记录之间所有可能组合的结果。更简单地说，第一个表中的每一行都将被连接到第二个表中的每一行，这意味着在最坏的情况下，我们将得到由 M×N 行组成的结果，其中 M 和 N 分别是表的大小。

> 避免执行会导致输出多于输入的连接

因此，这意味着交叉连接通常会返回比输入更多的输出行，这是我们通常想要避免的。作为一名总顾问，在这种情况下，您应该考虑两种可能的解决方法:

1.  评估窗口函数(比交叉连接更有效)是否能帮助您获得想要的结果
2.  在加入之前，使用`GROUP BY`执行预聚合

## 比起分片，更喜欢表分区

表分片是一种将数据存储到多个不同表中的方法，使用一个命名前缀，比如`[PREFIX]_YYYYMMDD`。许多用户会认为上述技术与分区相同，但实际上并非如此。

表分片要求 BigQuery 维护每个表的元数据和模式，此外，无论何时执行操作，平台都必须验证所有单个表的权限，这会对性能产生重大影响。

> 表分区比表分片更有效

一般来说，表分区的性能更好，因此您应该首选它们而不是分片表。此外，在过滤和降低成本方面，分区表更容易处理。

## 不要将 BigQuery 视为 OLTP 系统

像大多数数据仓库解决方案一样，BigQuery 也是一个 OLAP(在线分析处理)系统。这意味着在使用表扫描处理海量数据时，它的设计是高效的。因此，BigQuery 上的 [DML 语句](/ddl-dml-e802a25076c6)不应该用于执行**批量** **更新**。

> BigQuery 是一个 OLAP 系统，需要如此对待

使用 DML 语句执行模块化更改意味着您试图将 BigQuery 视为 OLTP(在线事务处理)系统。如果是这样的话，你应该重新考虑你的设计，甚至是你正在使用的工具。有可能 OLTP 系统(比如 Google 云平台上的 CloudSQL)更合适。或者，如果您的设计涉及常规模块化插件，您可以考虑其他技术，如流技术。

关于 OLAP 和 OLTP 系统之间的主要区别的更多细节，您可以阅读我最近的一篇文章。

[](/oltp-vs-olap-9ac334baa370) [## OLTP 与 OLAP:他们的区别是什么

### 在数据处理系统的上下文中理解 OLTP 和 OLAP 之间的区别

towardsdatascience.com](/oltp-vs-olap-9ac334baa370) 

## 最后的想法

在 BigQuery 中应用最佳实践并避免常见的反模式非常重要，因为这些原则将帮助您提高系统的性能并降低成本。

总结一下，

*   避免使用`SELECT *`，取而代之的是，确保你只查询你需要的字段
*   尽可能选择窗口函数而不是自连接(例如，如果您需要计算的是行相关的)
*   明智地选择分区键，以避免数据偏斜。如果不可能，请确保尽早应用过滤器
*   避免产生输出多于输入的连接
*   比起表分片，我更喜欢表分区，因为前者效率更高，成本更低
*   避免模块化的 DML 语句——big query 是一个 OLAP 系统，需要这样对待

[**成为会员**](https://gmyrianthous.medium.com/membership) **阅读介质上的每一个故事。你的会员费直接支持我和你看的其他作家。你也可以在媒体上看到所有的故事。**

[](https://gmyrianthous.medium.com/membership) [## 通过我的推荐链接加入 Medium-Giorgos Myrianthous

### 作为一个媒体会员，你的会员费的一部分会给你阅读的作家，你可以完全接触到每一个故事…

gmyrianthous.medium.com](https://gmyrianthous.medium.com/membership) 

**相关文章您可能也喜欢**

[](/visual-sql-joins-4e3899d9d46c) [## SQL 连接的直观解释

### 用维恩图和实际例子理解 SQL 连接

towardsdatascience.com](/visual-sql-joins-4e3899d9d46c) [](/2-rules-groupby-sql-6ff20b22fd2c) [## 在 SQL 中使用 GROUP BY 时要遵循的 2 条规则

### 了解 GROUP BY 子句中要包含哪些列，以及如何在 WHERE 子句中包含聚合

towardsdatascience.com](/2-rules-groupby-sql-6ff20b22fd2c) [](/sql-select-distinct-277c61012800) [## DISTINCT 不是 SQL 函数

### 在 SQL 中使用 DISTINCT 关键字时，括号的使用如何会导致混淆

towardsdatascience.com](/sql-select-distinct-277c61012800)