# 所以你想尝试测试驱动的开发

> 原文：<https://dev.to/recursivefaults/so-you-want-to-try-test-driven-development-71n>

五年前，我开始使用测试驱动开发(TDD)。没有任何其他实践能比这更能提高我的技术能力。顺便说一句，我现在已经学会做三次 TDD 了。

如果你想这篇文章向你推销 TDD，停止阅读。如果你想尝试 TDD，这是你的文章。

**第一步:忘记一切**
世界上有很多关于 TDD 的讨论。别管那噪音了。带着开放的心态去做这个练习。您可能会发现 TDD 值得您花费更多的时间和精力。你不可以。让你自己达到这样的程度，你可以在还没有下定决心的情况下尝试一下。

**第二步:挑一个问题**
每个开发人员都应该有几个他们用来学习新技术的问题。它提供了一个基线和一个通用的学习线索。如果你有，就用那个。如果没有，读 2a。

**步骤 2a:自动售货机**
建造一台自动售货机。自动售货机接受硬币，并允许您从其库存中进行选择。如果你给它足够的钱，自动售货机将分发你选择的商品。如果你的钱不够，它会把钱还给你。

**第三步:明面**
随便挑你想要的。标准是无论您选择什么，都要有工具或能力来构建和运行一套单元测试。

**第四步:规则**
现在该开始了。以下是你如何构建你的示例问题或我提供的自动售货机的规则。保持这个练习在 30-45 分钟内。

1.  你写的所有代码都是测试的形式
2.  在一个源文件中编写所有代码
3.  每个测试必须至少失败一次
4.  您只能在测试通过后从测试中移动或提取代码

这是四条规则。第一条规则意味着你不能在测试之外编写实现代码。您必须在测试本身中编写实现。第二，没有测试文件和源文件的分离。把它们放在一起。第三，你写的每一个测试第一次都需要失败，以保护红绿重构循环。所以写一个失败的测试！最后，在您修复了一个中断的测试之后，您可以将您的实现移出测试，但是在文件内。

这些规则迫使你遵循对 TDD 至关重要的红色、绿色、重构循环。这些规则似乎每个人都讨厌，但还记得第一步吗？试试这个，即使它看起来很蠢。

**结束**
所以已经花了 45 分钟来遵循一些严格的规则，强迫你用你的测试解决一个众所周知的问题。想想你会如何回答这些问题:

*   你是从写一个失败的测试开始的吗？
*   尝试选择要写的测试是什么感觉？
*   您是否发现自己想要跳过一些测试内容，直接进入实现阶段？
*   你是否写过一个你认为毫无意义，但实际上却向你展示了一些东西的测试？
*   与正常情况相比，你的代码设计如何？
*   与正常情况相比，您对自己生成的代码有多少信心？
*   如果 TDD 是你想学习的一项真正的技能，你下一步会关注什么？

**更新**

写完这个我才意识到，我应该提供一些其他的材料，把功劳归于那些影响过我的人。

1.  加里·伯恩哈特。看着他毁掉所有的软件截屏很了不起。他非常努力地工作，显示出他的优秀。
2.  鲍伯·马丁叔叔。他是《干净代码》的作者，并在世界范围内教授 TDD。
3.  基思·布莱斯维特。他关于 TDD 的研讨会是这篇文章的基础。