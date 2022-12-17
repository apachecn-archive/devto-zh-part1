# 你完成一个故事的过程是怎样的？

> 原文：<https://dev.to/willluce/whats-your-process-for-working-through-a-story>

发展是复杂的。不仅仅是因为技术和模式需要知识，还因为将工作投入生产所涉及的无数任务。

作为一个例子，我在本周看到了一个向表单添加新字段的故事。很简单，但事情是这样的。

最重要的是。我需要确保我有合适的工具来完成我的工作。机票有验收标准吗？我是否明白需要做什么样的改变来完成需要做的事情？当我开始写一篇报道时，这些检查是我要做的第一件事。

一旦票到手，我就制定一个完成工作的计划。这是我弄清楚我需要接触代码库的哪些部分来完成新功能的时候了。我通常把它写在我用作鼠标垫的笔记本上。

对于这个故事，我需要更新三件事。

*   数据库ˌ资料库
*   应用程序接口
*   前端

需要指出的是，我们的交付管道和工作流中有四个环境，顺序如下:本地->开发-> UAT ->生产。

我在数据库中添加了一个新列来保存新值。因为所有的开发工作都从本地开始，然后随着它在交付管道中的移动传播到其他环境，所以我编写了一个脚本来添加这个列。

这是我需要跟踪的第一件事。像这样的任务是完成一个故事的过程中所涉及的一种工作。如果我将使用新列的代码推到另一个环境中，而没有首先在那个环境中运行 DB 的脚本，那么事情就会出错。

所以，我把它写在便利贴上或者记在我的笔记本上。

其次，我拉下了两个仓库中的第一个(API ),它需要更改来完成这个故事。这里还有一系列必须按正确顺序发生的事情。我在父分支上运行测试以确保一切正常，然后创建我自己的分支，做出我的更改，运行测试，做出更改，运行测试，修复测试，并在此过程中提交。

一旦回购准备就绪(我知道这一点，因为我已经针对我所做的数据库更改测试了它的运行...本地)，我转移到第二个回购，前端，并重复这个过程。

在这一点上，我有三个独立的工作部分(数据库脚本、API 拉请求、前端拉请求),它们一起工作并且相互依赖，以满足我正在处理的故事的验收标准。

*这是我真正需要开始关注流程*的地方。因为我有多个 pr，所以不可避免的是，它们在不同的时间被评审和接受。有可能一个人今天得到了许可，第二天又得到了许可。当他们得到 ol 的“可以开始了”、“发货了”或“竖起大拇指”时，我需要将他们合并到管道中的下一个环境中。重要的是它们以正确的顺序运行，这样事情就不会中断，而且我必须记住在整个过程中在每个环境上运行那个该死的 DB 脚本。

如果我的工作被 QA 退回，补丁很可能只在我工作过的两个库中的一个中。因此，在这一点上，我必须记住撤回其他工作，这样事情才能保持在一起。

自始至终，因为那个故事的工作已经完成，我只是在等待事情发生，我会用另一个故事重新开始这个过程。

所有这一切的困难之处在于，这看起来像是一个过程，“处理一个故事”，但事实上，它是许多不同的清单、任务列表和时间线，必须正确管理，才能将一个字段放入表单中。不止一次，这个同心圆清单咬了我一口，一些代码片段在它应该在的环境中。

我想知道其他开发者是如何处理这种复杂性的。你用什么工具或方法来管理它？