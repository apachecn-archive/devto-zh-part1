# 介绍搜索建议下拉菜单的可访问性

> 原文：<https://dev.to/peiche/introducing-accessibility-to-a-search-suggest-dropdown>

我一直在做一个项目的搜索建议框。你知道类型:你开始在搜索框中输入，一个建议列表出现在它的下面。

(免责声明:这是我第一次写关于网页可访问性的文章，所以要温和一点。也就是说，我决不会因为太骄傲而不去学习(因此这篇文章)，所以我欢迎对我的代码的任何评论、修改或更正。)

我要写的部分不是让列表显示出来(我只是假设你知道如何做，因为这不是这篇文章的重点)，而是列表中项目的键盘控制。

用键盘导航搜索建议项目是一种非常常见的 UI 模式，但是我最初编写的解决方案根本不可用。焦点停留在搜索输入上，同时改变“键盘选择的”列表项的类(因此只是视觉方面)。当有一个“选择的”项目时，按下回车键，将转到该项目的 URL，而不是提交搜索表单。

您可以在此处看到该功能的通用版本:

[https://codepen.io/peiche/pen/RgzwaK](https://codepen.io/peiche/pen/RgzwaK)

最初出现的问题不是(我不好意思承认)可访问性，而是打开下拉项目链接的动作。一些(但不是全部)需要在新窗口中打开，使用`window.open()`并不总是有效。

澄清一下，其实与其说是不行，不如说是被堵了。浏览器(无论如何，使用默认的安全设置)将阻止任何非用户发起的弹出窗口。例如，在元素的`click()`事件中打开的弹出窗口被视为用户发起的。从一个按键事件中打开一个弹出窗口，没有那么多。(当然，你可以依靠用户来允许弹出窗口，但这是非常糟糕的 UX。)

我突然想到，在一个有焦点的链接上按下回车键的行为与单击它的行为完全一样。因此，如果带有`target="_blank"`属性的链接有焦点，按回车键将在新窗口中打开它。

有了这个认识，我重写了搜索框如何处理上下箭头键事件。焦点实际上*离开了*输入字段，由于`<a>`元素是可聚焦的(出于可访问性的原因，它们必须是可聚焦的)，焦点沿着条目列表移动。绑定到列表中每一项的`focus()`和`blur()`事件切换用于直观指示哪一项被选中的类，以及`aria-selected`属性。

[https://codepen.io/peiche/pen/weLvEx](https://codepen.io/peiche/pen/weLvEx)

回想起来，易访问性的重点(请原谅我的双关语)应该首先是为我的输入字段的下拉菜单编写键盘功能。不过，与第一个版本相比，我更喜欢它现在的行为。

*本文最初发表于[eichefam.net](https://eichefam.net/2017/07/20/accidental-accessibility/)。*