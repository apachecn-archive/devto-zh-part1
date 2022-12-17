# 解决常见的分支冲突

> 原文：<https://dev.to/meanin/resolve-common-branch-conflict-8al>

# 对，我用的是 git。是的，我喜欢它。不，我不是一贯正确的。

我使用 git 已经有 3-4 年了——从我的软件开发者之旅开始。起初，我被大量的命令弄得不知所措，我无法理解所有这些分布式分支/存储库是如何协同工作的。随着时间的推移，我越来越深入地了解 git。只是现在，我准备使用它，作为首选的版本控制系统工具。尽管如此——我认为我对 git 的了解还没有达到我想要和需要的程度，但是我每天都在学习新的东西。

在我目前的工作中，我们使用了一个最常见的(我认为)分支约定:

*   **开发**
*   **测试**
*   **阶段**
*   **产品**

对于开发人员来说，分支是一个游乐场/沙箱。一种更高级、更稳定的测试是测试人员的**测试**——试图破坏我们的代码并提出第一个错误/问题。**阶段**是再次测试，但这次是由我们最终客户的质量保证团队进行。最后 **Prod** 是 Prod:)

# 问题

当我们发现*合并*的冲突/问题时，在我们的特性分支上并不是什么大事。一种方法是我们可以*隐藏*我们的工作并将其应用于清晰的新分支，通过*从 **dev** 分支提取*变更来解决这个问题(并解决本地分支上的冲突),或者采取任何其他奇妙的方式/工具将我们的代码放入 **dev** 分支。默认情况下，我们创建一个策略来保护像(**阶段**、**测试**、**产品**)这样的分支免于直接提交。真正的问题是当冲突发生在上级部门时。由于我们的默认政策，我们不能直接推动变革，但不知何故，我们发现自己又一次陷入了冲突。让我更好地概述一下情况。

一个阳光明媚的日子，我们不得不为我们客户的 QA 团队将*的修复程序*推向**阶段**。肩负此重任的开发人员，*将整个**测试**分支合并*到所提到的**阶段**。她/他没有意识到在下一个(测试)分支上已经有了一些不应该被*推到**阶段**的特性。那么不幸的开发者做了什么呢？你知道*回复*是什么命令吗？她/他知道。在一些带有新特性的提交被恢复后，一切都很顺利。客户只得到需要的改变，我们没有公开新的/未准备好的特性。每个人都很开心。Yhmm...不，一点也不。一段时间后，当我们的测试人员说新的新鲜特性已经准备好被*推入**阶段**分支时，我们遇到了一个问题。为什么？因为，上个晴天有些提交是直接在**阶段**分支上做的。没有人知道，除了一个开发者。你说，有什么问题？因为 *revert* -commit，我们已经在 git 提交历史中有了，我们不能将变更(从**测试**分支)交付给我们的客户端。**

# 解

那么这个饭桶表现如何呢？*合并*分支不变？！最后，如何修复这种情况？有一种方法，但是我们需要知道 git 是如何工作的。Git 比较两个分支的历史，并应用尚未被*合并的新提交。当分支有不同的提交时，就会发生冲突。历史开始倾倒。但是我们有一个非常清晰的历史记录，涵盖了从**测试**到**阶段**的所有提交。这让我想到了历史。我回顾了所有提交，发现不幸的回复，然后最后，我们可以开始工作了。我*基于**阶段**签出了*新分支，做了一个*回复*到*回复*-提交，*从下级分支拉*变更，并为此创建了一个*拉请求*。它成功了🙂*

# 最后的想法

在那之后，我试着记住:

*   不要*挤压*提交(第一次尝试时，我已经挤压了它们，但不起作用)，
*   从上级创建固定分支，
*   从冲突下级分支中提取更改，
*   解决本地机器上的冲突，
*   然后合并(创建一个拉取请求)到上级分支，然后…瞧！

你在使用 git 的时候遇到什么困难了吗？请在这里与我分享。

本文是看了[git 是最好的风投吗？在我的上一篇文章](https://dev.to/ben/is-git-the-be-all-and-end-all-of-version-control-4lp)[处理晚上的创意爆发](https://dev.to/meanin/how-to-deal-with-evenings-bursts-of-creativity-pc)之后，我收到的所有提示也很有帮助。