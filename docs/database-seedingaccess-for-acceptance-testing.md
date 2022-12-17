# 验收测试的数据库播种/访问

> 原文：<https://dev.to/grahamcox82/database-seedingaccess-for-acceptance-testing>

如果你正在用某种数据库编写一个应用程序——现在大多数人都这样做了——并且你正在为这个应用程序编写验收测试，在某些时候你会遇到测试数据的难题。

这个问题有两种不同的出现方式，两者都很重要。

首先，是填充数据库以便测试工作的情况。假设您遵循了正确的测试原则，那么在测试任何只读操作时，您都会遇到问题。您需要能够在系统中实际检索一些数据——或者能够保证没有这些数据。

在我看来，有 4 种方法可以解决这个问题，但可行性不同:

1.  使用现有的 API 来填充数据。例如，如果您正在测试通过 ID 检索用户，那么首先使用删除用户和创建用户的 API 来确保数据库处于正确的状态。这确实假设这样的 API 存在，并且确实使测试有点混乱，因为您正在使用可能没有通过测试的东西来设置这个测试。
2.  创建一个纯粹用于植入数据库的新 API。您可以拥有一个端点，向其传递 XML 或 JSON 文档来描述数据库状态，并让后端正确设置数据。这意味着创建这个端点需要更多的工作，但是从长远来看，它比上面的方法灵活得多。但是，如果您不小心的话，它确实会带来潜在的安全风险
3.  从测试中直接访问数据库。这是我经常看到的一种情况，它工作得足够好，但是它确实意味着代码和测试之间的知识重复，并且它确实意味着测试只能从可以访问数据库的环境中运行。
4.  用所有需要的测试数据预先播种数据库。从某些方面来说，这是最简单的选择，因为您只有一个安装脚本，这样就完成了。然而，维护是一个真正的痛苦。

我的个人偏好是#2 或#3，这取决于测试中的应用程序的大小。

您遇到的另一个问题是相反的——从数据库中读取数据以确保测试正确运行。同样，我在这里可以想到 4 个选项，具有不同的可行性。

1.  使用现有的 API。如果您刚刚创建了一个用户，请使用检索用户 API 来检查数据。这只会显示您可以从 API 中检索到的数据，因此并不完美。
2.  创建一个纯粹用于检索数据库的新 API。本质上是围绕数据库访问的无操作包装器。不过，这最终会导致您的真实端点出现大量重复
3.  从测试中直接访问数据库。
4.  别为此费心了。

从技术上讲，对于验收测试来说，#4 是更正确的答案。毕竟，只要系统从外部做正确的事情，内部如何工作就没什么关系。这就是单元测试和集成测试的目的。然而，当有些变化没有明显的外部效果，但仍然需要测试时，4 号确实会失败。这种情况非常罕见，以至于我很想回到之前的选择。

* * *

1)通过“适当的测试原则”，我的意思是每个测试应该精确地执行一个动作，并且测试的顺序应该完全独立。在一个测试中执行多个动作意味着你不清楚什么是工作的，什么是不工作的，测试之间的相互依赖使它们变得脆弱，并且再次意味着一个失败的测试会导致其他测试的级联。