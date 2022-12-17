# 作为园丁的程序员

> 原文：<https://dev.to/raulvillares/programmers-as-gardeners>

前一段时间我读了一篇有趣的文章，作者是音乐家[布赖恩·伊诺](https://en.wikipedia.org/wiki/Brian_Eno)，标题是 [*“作为园丁的作曲家”*](https://www.edge.org/conversation/brian_eno-composers-as-gardeners) 。

â€‹â€‹Eno 的基本想法是重新思考作曲的方式，从作曲家预先设计作品所有细节的过程，到她给予一个小小的初始推动，让音乐自己发展的过程。用 Eno 自己的话说:

> [……]我曾假设音乐是以你想象的交响乐作曲家创作音乐的方式产生或创作的，即在他们的头脑中有一个非常详细的完整想法，然后以某种方式写出其他人可以复制它的方法。就像想象建筑师在工作一样。你知道，设计建筑，所有的细节，然后建造。[……]一种新的作曲范式。改变作曲家的想法，从站在一个过程的顶端，并精确地规定如何执行的人，到站在过程底端，小心翼翼地播下一些精选的种子，满怀希望地，看着它们变成东西的人。

这个想法停留在我的脑海中，现在我正在实践[测试驱动开发](https://en.wikipedia.org/wiki/Test-driven_development)，它已经回到前台向我指出**这种编程技术符合 Eno 的哲学**。

## 建筑师

当我们在主程序之后编写单元测试代码时(如果它们被编写的话，**)我们就像是站在过程顶端的作曲家。这一立场迫使我们对我们想要建设的东西有一个全面而精确的愿景。这种想法(继承自臭名昭著的试图将软件开发类似于[其他工程](http://blog.xebia.com/metaphors-in-software-development/))是**不切实际的，并最终产生[复杂、僵化和脆弱的系统](https://www.excella.com/insights/top-4-symptoms-of-bad-code)** 。**

## 园丁

然而，如果我们遵循 TDD，我们就成了园丁，播种并观察它们的生长，必要时浇水或施肥。

我们只在一些测试要求的时候创建一个类(编译错误)，我们只在需要通过一个之前失败的测试的时候编写一个方法。
生产代码(在我们开始之前我们只有一个大概的概念)**像植物的嫩芽一样一个接一个地出现**。这种设计是最自然、最有机的，因为它产生于系统在任何时候的需求。

其他人发现园艺和软件开发之间的比喻很方便:

*   [编程是园艺，不是工程](http://www.artima.com/intv/garden.html)
*   你不是工程师！
*   [软件园艺宣言](http://softwaregarden.io/manifesto/)

所以我要努力变得越来越像一个园丁，而不是建筑师。正如 Eno 自己所说，他们至少在尊严上是平等的。

页（page 的缩写）s:这篇文章是我连续听着低调的音乐写的。