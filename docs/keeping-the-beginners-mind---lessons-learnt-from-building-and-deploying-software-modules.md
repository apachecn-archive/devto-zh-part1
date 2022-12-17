# 保持初学者的头脑——从构建和部署软件模块中学到的经验

> 原文：<https://dev.to/kr428/keeping-the-beginners-mind---lessons-learnt-from-building-and-deploying-software-modules>

我从事编写和运行软件已经有一段时间了，当我在这里看到一堆文章和文章提供了关于如何(不)成为一个好的甚至更好的开发人员的鼓舞人心的提示时，我想我应该插话并分享我在这个问题上的一些见解。这些也是我希望在我的团队中有抱负的开发人员身上看到的。我们开始吧:

## 把问题放在第一位

无论你多么擅长掌握框架 X 或语言 Y:学会专注于你想要解决的问题而不是手头的解决方案。否则你将面临[金锤](https://en.wikipedia.org/wiki/Law_of_the_instrument):如果你把你的解决方案想法放在第一位，你迟早会用解决方案来看待你的问题，你总是倾向于通过你的“熟悉的”解决方案在这里的效果来判断你是否能解决问题。所以，在这里:试着经常和“商业”人士(那些希望他们的问题得到解决的人)交谈，试着倾听，试着理解他们需要什么。最终帮助他们明确需求。不要太快提出解决方案。

## 有资格跳出框框思考

“问题优先”和“金锤”的继承者:是的，为了快速、高质量地完成工作，在一堆工具中拥有扎实的技能是很重要的。但是同样的，你应该对不同的架构和技术方法、框架、概念、解决方法有一个模糊的概念。

几年前，当我和一位数据库顾问一起研究我们环境中的性能问题时，我有过一次有趣的经历。这时，他查看了系统上所有开放连接的列表，怀疑它们都来自同一个 IP 地址——直到最后以“啊，好吧，那是某种应用服务器”结束。在接下来的对话中，我既觉得自己完全傻了，又大受启发，这主要是因为在我当时的世界中，将 RDBMS 和其他持久性方法隐藏在应用程序服务器外观之后是如此普遍，以至于“显而易见”的事情(至少对于本地用例(构建一个直接连接到数据库的桌面应用程序)是完全看不见的。它不会是绝对的“更好”或“更差”——我们甚至没有想到对此进行评估。

最近我在过度使用 HTTP(和 JSON)进行通信的服务中看到了类似的事情。这时，有时在应用程序中，如果需要的话，我会看到下载二进制文件的专用路径或查询参数。“显而易见”的 HTTP 式解决方案(使用不同的内容类型和内容协商)很少出现。

不同的解决方案、不同的思维方式、不同的实施方法可能会更容易解决一些问题。尝试从概念的角度寻找好的解决方案。当你开始把“舒适的”解决方案放在第一位时，试着意识到这一点，并在这些情况下试着质疑这一点。

因此，长话短说:在你的学习努力中，你应该花一些时间浏览技术和开发世界正在发生的事情，也许听一些播客，通过五分钟的教程来了解一些事情，即使没有完全掌握它们的奉献精神，或者让*在你的下一个项目中使用它们。想想工具箱:你应该有一套最熟悉的工具，另外你应该知道哪些工具是现成的，它们通常是如何工作的，知道如果需要的话你可以很快学会如何使用它们。*

## 尽可能保持简单的解决方案

你试图解决的问题有其固有的复杂性，而你试图解决这个问题所使用的工具也带来了复杂性。对于第一个问题，你不会有太大的改变——这个问题已经很复杂了。但是你可以通过仔细选择添加多少框架，多少运行时依赖，多少强制配置选项到你的组件来改变第二个。当然，它们可以简化您的开发，使您的解决方案更快地启动和运行，但从长远来看，您每次接触该模块时都必须处理这些事情。

## 了解你的基础知识

尽管简单明了的编码很有趣:对代码背后的东西有一些基本的理解会让生活变得更容易，让你的代码更好。是的，能够用多种语言读写代码固然很好，但更重要的是了解一些基本概念——一些基本的算法，一些关于数据结构、抽象、多态或继承、递归的基本知识，不要忘记一些设计模式...。了解一个 QuickSort 实现或一个 Singleton 将帮助你更快更好地理解编写的代码和整个系统的行为。

这也是一个您可能想要花更多时间学习的领域，因为如果在不同的栈和语言之间移动，这些知识通常更可重用(即使，例如，一些设计模式在一些语言中比在其他语言中更有意义...).

## 了解你的工具

我深深扎根于 Java 世界，在这里，人们习惯于使用成熟的强大 ide(如 Eclipse 或 NetBeans)来完成工作。就我个人而言，我非常喜欢这一点，因为它确实让事情变得更容易。但是，要注意的是，这些工具是为那些知道发生了什么并希望通过不必一次又一次地手动完成所有这些事情而变得更快的人而设计的，以减轻重复、枯燥的例行任务。当您使用 IDE 或类似工具而不理解(或者更糟:不想理解)幕后发生的事情时，您可能会很快陷入麻烦。对于一些包含电池的框架来说也是如此，比如 jhipster T1，它会给你带来一大堆样板代码和设置上的麻烦，但是如果你不了解里面有什么以及这些东西是如何组合在一起的，那么它肯定会让你犯错误。

## 准备发货

我在研究项目和公司开发方面都有相当多的经验，其中原型和模块的早期版本*当然*曾经在本地开发人员笔记本上的 IDE 中运行。在某些情况下，将应用程序移出 IDE 并转移到某个专用的生产服务器上变得很麻烦，因为突然之间，我们的复杂性达到了一个全新的水平。突然之间，应用程序和依赖项的打包成为必要。突然间，我们不得不应对这样一个事实，即应用程序需要比应用服务器提供的版本“更新”的依赖项，因此我们需要质疑这些依赖项的运行时和部署策略。在某些情况下，只有在第一次部署到“外部”服务器之后，我们才体验到对开发机器本地资源的访问，这些资源硬编码在应用程序源代码中的某个地方。现在，在专用的测试系统上(而不是在开发人员的笔记本电脑上)呈现应用程序是团队对完成的定义的一部分。所以一般来说，尽早准备好发布应用程序的工件是一个好主意。它有助于快速收集反馈，并且有助于使依赖关系和运行时需求变得明显。它有助于避免可怕的“在我的设备上工作”的情况，这是一个很好的机会，让您在上线和遇到问题后陷入困境，因为生产环境以未知的方式不同于您的开发系统。这是很容易准备好的事情，所以你应该准备好。

## 保持“初学者心态”

最后:永远不要陷入精通事物、无所不知甚至只是“非常了解”的错误观念。你从来没有。你将永远是一个在各方面都可能的学习者。不管你经历了多少开发工作和项目，不管你见过多少技术堆栈或者解决了多少业务问题，总有更多的方法。绝对没有理由认为你不需要学习其他任何东西。你将永远在学习...在发展中，在科技中，在生活中。

从开发人员的角度来看，随着年龄的增长，这尤其有趣:您可能会在您的团队中看到越来越年轻的人，同时可能会向某种“高级工程师”的角色前进一点。你会看到年轻的同事提出新的和不熟悉的想法。您将会看到新的工具和框架出现(在某些情况下，也会消失)。你会看到新的方法和流程不断涌现。你会看到人们尝试一些事情，并且可能犯同样的错误。挑战这些人，但要对他们所说的持开放态度。让他们激励你。一起成长多一点。

欢迎评论和启发。我也只是个初学者。；)

## 一些读数

*   [esr 的《如何成为一名黑客》](http://www.catb.org/esr/faqs/hacker-howto.html)——有些东西也不应该太认真，但你仍然应该至少读一遍，其中的一些观点非常有效。
*   Neal Stephensons“起初有命令行”——虚构多于事实，这是一本关于技术、技术进步、用户界面、有争议的隐喻和一堆其他东西的非常有趣的读物。
*   谷歌“网站可靠性工程”在线书籍——从传统意义上来说，这与开发者无关，但对于开发者来说，这里仍然可以找到一些有效的见解。
*   [本质复杂性与意外复杂性](http://simplicable.com/new/accidental-complexity-vs-essential-complexity)
*   [它在我的机器上工作](http://www.dylanbeattie.net/2017/04/it-works-on-my-machine.html)——这篇有趣的文章就开发人员和运营人员之间的一个基本“问题”提供了一些简洁的提示