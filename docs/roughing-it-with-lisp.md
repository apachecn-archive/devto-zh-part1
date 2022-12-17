# 用 Lisp 处理它

> 原文：<https://dev.to/syncsynchalt/roughing-it-with-lisp>

像许多软件开发人员一样，我和 Lisp 有一点点、微弱的、几乎不存在的关系。高中时，我曾涉猎过 emacs，大学时，我有一个热爱 lambda 的朋友，但我基本上忽略了他，一旦我进入职场，我总是把“学习一些 Lisp”放在我的待办事项列表上，通常在底部附近。

直到几周前，在读埃里克·诺曼德的文章[“Lisp 的想法”](https://dev.to/ericnormand/the-idea-of-lisp)时，我才终于心痒痒了。但是我应该怎么做呢？文章将最初的 LISP 描述为构建运行时的一组五个原语，就像基于五个不可约公理的欧几里得几何。我实际上从未编写过语言解释器，我认为阅读[原版麦卡锡论文](https://www.brinckerhoff.org/clements/csc530-sp09/Readings/mccarthy-1960.pdf)会很有趣，看看我是否能实现所描述的语言。手边没有 IBM 704，我打算用 C 语言写，用尽可能少的代码~~合理地~~写，并且尽可能地依赖给定的原语。我不打算作弊并查看其他 Lisp 资源，尽管我确实看了一眼维基百科上关于 S-Expressions 的文章，因为原始论文中的视觉布局对我来说并不清楚。简而言之，我想假装这是 1960 年 4 月，我刚刚得到了最新的 CACM，就像一些现代的徒步旅行者走进树林假装他们手边没有 GPS。

在实现本文中的语言时，您需要解决一些问题。首先，论文中的大部分代码都是 M 表达式，这对于像我这样的算法专家来说并不习惯，而且显然从未在软件中实现过。一旦克服了这个障碍，将 M 表达式转换成您选择的语言，您会注意到论文中的函数定义有时会缺少终止条件，或者某些区域的行为不明确，或者定义中的括号不平衡(这在关于 Lisp 的论文中很讽刺)。在你做了一些修正并指定了 unspecified 之后，你还会发现在`eval`的定义中有一个错误。我花了半天时间解决了后者，后来才发现这个错误和修复是众所周知的(麦卡锡在 1995 年的更新中暗示了它，保罗·格拉厄姆在[Lisp 的根源](http://paulgraham.com/rootsoflisp.html)中详细说明了它)。

结果是，[一个粗糙的 Lisp 实现](https://github.com/syncsynchalt/axiomatic-lisp)，具有论文中描述的特性，包括标记-清除 GC，加上一些 2 函数数学。它的不同寻常之处在于，它可以在几百行 C 语言中解析 S 表达式并执行递归函数，但这并不是你想要使用的语言。你想做的第一件事是做一些明显的添加，使它更有用(我已经通过添加一个`defun`开始，它将必要的`lambda`和`label`引用放在一个全局 args 范围内)。你真的可以看出，最初的论文是试图捕捉一个移动的物体，这是一个及时的快照，大概是在递归函数被证明有效后不久，但在任何人用它们做有用的工作之前。

令人难以置信的是，它存在于 50 年代，整整十年前，我的宇宙通常被认为已经开始。最初的 Lisp 就像一个约翰·哈里森钟，因为你无法想象它是如何构思的，如何制作的，或者一切是如何配合得如此之好。谢谢你的文章，埃里克，你让我看到了一块宝石。

<small>封面图片由[大卫·菲尔丁(aviator Dave @ Flickr)](https://www.flickr.com/photos/aviatordave/)CC BY-NC-ND 2.0</small>