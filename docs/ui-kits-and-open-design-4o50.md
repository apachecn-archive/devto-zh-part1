# UI 套件和开放式设计

> 原文：<https://dev.to/trek/ui-kits-and-open-design-4o50>

## UI 套件和开放式设计。

在过去的几年里，我们见证了用于网络的 [UI 套件](http://topcoat.io/)的[精彩](http://foundation.zurb.com/) [激增](http://twbs.github.io/bootstrap/)。这些库为非设计人员提供了一种创建设计界面的方法，而不需要专门的设计人员。它们的功能很像库，为每个开发人员节省了掌握各种技术(文件 IO、网络、应用程序结构等)的时间，这些技术用于制作技术产品。

像开源软件一样，这些项目也有开放共享的目标，因此任何人都可以获得项目并对其进行扩充，免费使用它，更改并重新发布它，或者提交更改供每个人共享。

UI 工具包意味着一个训练有素的专业人员已经完成了复杂而耗时的任务，即精心制作一组可重用的元素，这些元素可以以多种方式组合，并且仍然保留来自良好设计的凝聚力和统一性。一些工具包还附带了 HTML 和 CSS，节省了您将设计从像素转换为强大但古怪的 DSL 的时间。

从表面上看，这就像是开源软件的等价物:如果你愿意的话，可以称之为“开放设计”。但是这些项目并不像我猜想的作者所希望的那样开放。这是一个大胆的声明，所以请原谅我:发布图像和/或 HTML 和 CSS，即使附有管理其免费使用的许可，也不构成“开放”。它们当然像啤酒一样免费，但我认为它们没有达到更高的免费标准。

PSDs，运球投篮，甚至 HTML 和 CSS 的问题是，无论我们有多大的使用自由，这些东西*都不是设计*。它们是设计的*神器*。它们是设计的一种编码，在视觉上和 DSL (HTML/CSS)中，但它们本身不是*的*设计。

实际的设计——我希望这些框架的作者公开的信息——是他们为尺寸、比例、颜色、线条、纹理和所有其他设计元素选择的*值*背后的决策过程。

让我们以[面漆](http://topcoat.io/)为例。这是他们工具箱里的一个按钮:

[![](img/c9c251ccd2bd2e8aa454ea919075bb7d.png)T2】](https://res.cloudinary.com/practicaldev/image/fetch/s--H33TiXLh--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dl.dropboxusercontent.com/u/1931034/Topcoat.png)

我可以从 CSS 中知道按钮的颜色是浅灰色(`#e5e9e8`)，里面的文本大小是`1.167em`，它有填充的`1.16em`，填充的左右两边是`padding`，顶部和底部是`line-height`。它具有带`3px`半径的`solid #a5a8a8`的`1px`边界。文字是`Source Sans`深色的`200`粗细但不是纯黑色的`#454545`带有轻微的`#fff`阴影。

即使 Topcoat 像其他 UI 工具包一样只提供图像，我也可以使用像 [xScope](http://iconfactory.com/software/xscope) 和 [ColorSchemer Studio](http://www.colorschemer.com/) 这样的工具来导出值。拥有 CSS 很棒，因为它省去了这一步，并且封装了将这些值转换成浏览器可解析格式的最佳实践解决方案。尽管如此，这些特定的值是设计的“是什么”,但它们不是最重要的部分，也不是使设计真正开放和可重用的部分:“为什么”。

为什么是`3px`半径而不是`5px`或`1px`？`3px`和按钮整体的大小或者文字的大小和粗细有什么关系？为什么按钮`#e5e9e8`和边框`#a5a8a8`？这些颜色是怎么选出来的？

从按钮向外扩展，我们可以继续我们的问题。在按钮和它附近的其他元素之间创建空间的值是如何相互关联的？面漆中的颜色是如何选择的，它们之间的关系如何？彩色按钮有各种蓝色来表示状态。这些蓝色是如何从所有可能的色调、饱和度和亮度组合中挑选出来的？蓝色、灰色和接近黑色的颜色如何相互比较？

这些问题(以及更多问题)的答案是设计的实际“来源”。如果你认为“为什么”不是一个设计中最重要的方面，那么打开这些 UI 套件中的一个(或者甚至是一个最喜欢的网络应用！)并开始更改值。你不需要改变很多值，也不需要在设计对你来说看起来“不合适”或“坏了”之前改变太多。通过重新加载将它们改回来，设计看起来会像是将 T1 扣到位，富有其原始的内聚力。

去，试一试。是不是很神奇？更神奇的是，即使你不是设计师，你也会看到它。你生活在一个设计好的世界里。你已经通过不断的接触被训练去看设计。而且，虽然你可能没有受过从头开始做新设计的训练，但你完全有能力区分好的和差的设计。如果你不相信我，[去玩 method.ac](http://method.ac/) 的游戏。

每一个设计都像一种小语言，有自己正确的语法和句法，几乎和编程语言一样具体。它包含图元，但不是像地图、数组、整数和函数这样的概念，而是包含大小、重量、颜色、比例和纹理的图元。

不首先理解这种语言，就不可能正确地表达任何新的东西。对于大多数使用这些库的人来说，这就是问题的开始。如果他们安全地呆在提供的组件中，他们可以制作一个看起来设计好的应用程序(因为它是)，但是没有 UI 工具包提供每一个可能的组件，甚至没有关于现有组件可以组合的所有方式的指导。

不可避免的是，这些工具包将无法提供帮助。你需要一些新的东西——可能大到一个新的组件，也可能小到一种新的高亮颜色——但它看起来会有点不对劲。这是你在这里遇到的第一个来自尝试设计的开发者的抱怨。不是他们不知道什么是好的设计，而是当他们尝试的时候，结果都是错的。

很容易认为 HTML 和 CSS 是设计的来源，通读它们会解释你需要的一切。让我们通过返回到上面的按钮示例并添加另一个按钮来稍微检查一下这个想法:

大按钮
[![](img/c9c251ccd2bd2e8aa454ea919075bb7d.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--H33TiXLh--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dl.dropboxusercontent.com/u/1931034/Topcoat.png)

小按钮
[![](img/71a75f6efa0f097ec6d9659bc7799b69.png)](https://res.cloudinary.com/practicaldev/image/fetch/s--OxbbVWps--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dl.dropboxusercontent.com/u/1931034/Topcoat2.png)

假设我们的应用程序需要三个层次的按钮来吸引注意力。大按钮用于对当前正在交互的数据进行操作，小按钮用于其他地方的操作，small_er_ buttons 用于全局但不常用的操作。

较小的按钮应该使用多少垂直空间？

[平头](http://designmodo.github.io/Flat-UI/)、[自举](http://twbs.github.io/bootstrap/)、[粉底](http://foundation.zurb.com/)、[面漆](http://topcoat.io/)露出的设计神器中隐含的就是实际的设计。一个熟练的设计者可以用同样的方式提取它，一个熟练的程序员可以以惊人的准确性查看一个应用程序并进行逆向工程。

一旦设计师发现了底层的基本元素，创建适合整体设计的新元素就变得轻而易举。

大多数程序员缺乏这种技能。很多设计师新手也是如此。对于一个专业的设计者，尤其是那些制作 UI 套件的人来说，设计是如此的明显，以至于他们不能理解为什么我们会举手说“这些都是漂亮的例子，但是我怎么才能真正的把 T1 变成一个该死的东西呢？”

好消息是程序员在一组约束和规则下工作时训练有素。你只需要告诉他们这些规则是什么，以及如何使用它们。设计不是随机的。设计是对尺寸、比例、颜色、质地、线条等有意选择的积累。选择这些值是出于特定的原因，这些值之间的关系就是设计的语言。

对于所有流行的 UI 套件*来说，有人*知道这些值背后的原因，但是这种知识是不公开的。有了足够的技巧，你可以很好地猜测答案，但这并不比逆向工程中的任何练习更开放。

我非常感谢人们为制作这些框架所做的工作。我只希望他们能分享正确的部分。

#### 脚注

1.  我也和一些设计朋友尝试过这个练习。当单个值发生少量变化时，他们通常能够注意到中断。令人印象深刻。

*这篇文章最初是作为[要点](https://gist.github.com/trek/fff970bf2eb1192d852a)T3 出现的*

#### 通知我思考的一些资源

*   [安卓的风格指南](http://developer.android.com/design/style/index.html)
*   [Windows Phone UI 设计语言](http://channel9.msdn.com/events/MIX/MIX10/CL14)
*   [BBCs 风格指南](http://www.bbc.co.uk/blogs/bbcinternet/2010/02/a_new_global_visual_language_f.html)
*   [苹果人机界面指南(HIG)](https://developer.apple.com/library/mac/#documentation/UserExperience/Conceptual/AppleHIGuidelines/Intro/Intro.html)
*   [蒂姆·布朗——更完美的排版](http://vimeo.com/17079380)和伟大的[模块比例](http://modularscale.com/)工具，用于选择内聚尺寸值
*   [内容输出设计](http://www.markboulton.co.uk/journal/a-richer-canvas)
*   [无限网格](http://alistapart.com/article/the-infinite-grid)