# 新视野冥王星飞船

> 原文：<https://dev.to/funkysi1701/new-horizons-pluto-spacecraft-2ohg>

[![](img/5e81deb921b3d2ef25c4b25492ece7b8.png)T2】](https://res.cloudinary.com/practicaldev/image/fetch/s--63ZWUIHy--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://storageaccountblog9f5d.blob.core.windows.net/blazor/wp-content/uploads/2015/07/84270464_p_lorri_fullframe_color.png%3Fw%3D976%26ssl%3D1)

为了探索陌生的新世界，今天美国国家航空航天局的新视野号宇宙飞船正在这样做。这是迄今为止我们探索过的最远的行星冥王星的最详细的照片。

新视野号于 2006 年 1 月 19 日发射升空。它已经旅行了 3463 天(9.5 年)。

2006 年我们还在用 Windows XP 和 Office 2003。2006 年，我甚至还没有在 IT 部门工作。作为一名软件开发人员，很难想象还会有 9.5 年不用的软件。

航天器携带两个计算机系统:指挥和数据处理系统以及制导和控制处理器。这两个系统中的每一个都是冗余的，总共有四台计算机。用于其飞行计算机的处理器是 mongose-V，一种 12 MHz 抗辐射版本的 MIPS R3000 CPU。多个时钟和定时例程在硬件和软件中实现，以帮助防止故障和停机。为了保存热量和质量，航天器和仪器电子设备一起装在 IEMs(集成电子模块)中。有两个冗余 iem。包括仪器和无线电电子设备等其他功能，每个 IEM 包含 9 块电路板。处理器向每个子系统分配操作命令，收集和处理仪器数据，并对发回地球的信息进行排序。它还运行先进的“自治”算法，允许航天器检查每个系统的状态，如果有必要，纠正任何问题，切换到备份系统或联系地球上的操作员寻求帮助。

[![](img/3d73e11f25818de8038cdcff194bc5aa.png)T2】](https://res.cloudinary.com/practicaldev/image/fetch/s--9tPUTkF8--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://storageaccountblog9f5d.blob.core.windows.net/blazor/wp-content/uploads/2015/07/Mission-Spacecraft-structure.jpg%3Fresize%3D300%252C218%26ssl%3D1)

对于数据存储，新视野号携带了两个低功率固态记录器(一个备份)，每个可以存储 8gb。主处理器在记录器上收集、压缩、重新格式化、分类和存储科学和内务管理(遥测)数据——类似于数码相机的闪存卡——以便通过电信子系统传输到地球。

与宇宙飞船的通讯是通过 X 波段。该飞行器在木星上的通信速率为 38 千比特/秒；在冥王星的距离，大约 1000 位/秒的速度。为了将这个速度放在上下文中，本页顶部的图像大小为 649kb，从冥王星到地球需要 86 分钟以上，(我肯定实际图像要大得多，到达我们这里需要更长的时间。)除了带宽低，冥王星的距离也造成了 4.5 小时左右的延迟(单向)。一旦超出木星，70 米(230 英尺)的美国宇航局深空网络(DSN)碟形天线用于中继命令。将全套冥王星遭遇科学数据发送回地球需要 16 个月。

大多数软件时不时会遇到一个问题，但这个航天器上的软件必须保持运行几乎十年。由于涉及的距离，它不可能上传任何代码调整。发送到航天器的任何命令甚至需要 4.5 个小时才能到达那里，因此需要大量的自治和冗余来应对如此巨大的旅程。

我甚至无法想象你将如何开始编写软件来运行这样一个飞行器。我不认为我写过任何和运行在新视野号飞船上的代码一样老的代码，如果我写过，我想质量会很差，肯定不足以让我不间断地工作十年。

有一些非常聪明的人参与了这个项目。祝贺团队，当数据开始慢慢传回地球时，你们完全有理由感到骄傲。