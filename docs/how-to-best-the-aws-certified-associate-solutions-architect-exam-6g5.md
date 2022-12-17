# 如何通过 AWS 认证助理解决方案架构师考试

> 原文：<https://dev.to/kylegalbraith/how-to-best-the-aws-certified-associate-solutions-architect-exam-6g5>

Amazon Web Services 的发展势头与日俱增。许多公司都在寻求迁移到 AWS，他们正在寻找经验丰富的开发人员来帮助他们。AWS 认证变得非常受欢迎并不奇怪。

您可以参加不同学科的不同认证:

*   认证解决方案架构师(助理和专业人员)
*   认证开发人员(助理)
*   注册系统运行管理员(助理)
*   注册 DevOps 工程师(专业)

我将重点介绍解决方案架构师助理，并分享我以前学习的笔记。在以后的文章中，我将介绍专业解决方案架构师证书。

### 关联解决方案架构师域

考试包括四个领域:

*   设计(60%)
*   实施/部署(10%)
*   安全性(20%)
*   故障排除(10%)

百分比让你知道考试覆盖该领域的百分比。直到你参加考试，你才会知道考试有多少题。也没有公布“及格分数”。您的分数基于您在不同领域的表现。

### 熟悉亚马逊网络服务

每个领域都包含了足以让你头晕目眩的信息。我专注于实际的东西，并对每个领域内的每个服务有所了解。在参加考试之前，我花了大约三年的时间全职开发 AWS。这无疑对我有帮助，但是没有那么多经验也有可能通过考试。

你不应该在没有尝试各种服务之前就参加考试。您至少应该尝试以下核心服务:

*   弹性计算云(EC2)
*   简单存储服务(S3)
*   关系数据库服务
*   弹性块存储
*   虚拟专用云(VPC)
*   云锋
*   云的形成
*   DynamoDB
*   身份访问管理(IAM)

对于这些服务中的每一个，都有足够的特性、问题和用例。你不会了解每一个人的一切。这不是目标。目标是了解每个服务旨在解决什么问题，以及使用它来解决该问题的基础知识。

### 领域 1:设计

该领域侧重于识别和认识云中的架构考虑事项。成本、网络和安全性都是您需要注意的事项。对于这个领域，重点关注 AWS 环境中的那些考虑事项。

有必要了解与 AWS 系统设计相关的两个重要术语。

> 高可用性:系统必须继续运行，但可以在降级状态下继续运行。
> 
> 容错:即使组件完全失效，系统也必须正常运行。

您需要知道如何区分这两种设计考虑。几乎可以保证，在你必须知道区别的地方会有问题。准备好对这些进行推理。关于这一点的白皮书可以在[这里](https://media.amazonwebservices.com/AWS_Building_Fault_Tolerant_Applications.pdf)找到。

考试提示:如果问题以任何方式提到容错，那么为 FT 设计。

设计领域的另一个你应该知道的方面是成本。AWS 成本的一大驱动因素是它提供的弹性。关于如何使事情更具成本效益的问题通常归结为需求弹性。还要知道，大多数在服务中花费更多钱的东西在默认情况下是关闭的。

### 领域 2:实施/部署

这里的重点是了解如何利用一组 AWS 服务来构建云解决方案。有一些重量级的服务可能会出现问题。了解这些服务在实施和部署概念中的作用。根据我的经验，您需要了解的这部分服务有:

##### EC2

*   了解按需、预留和现场实例。
*   弹性块存储(EBS)支持的实例与实例存储。
*   你需要知道 t2 是什么。实例类用于说明 CPU 信用如何影响您。
*   您需要知道如何在实例启动时利用实例用户数据来配置实例。

##### VPC

*   了解 EC2 IP 寻址的工作原理很重要(即默认情况下没有公共 IP 地址)。
*   熟悉 VPC 中子网的工作方式，以及拥有公有或私有子网的含义。
*   安全组和 ACL 在 VPC 环境中非常重要。了解不同之处和每个人试图解决的问题。
*   可能会有一个关于如何从一个 VPC 窥视另一个的问题。理解这样做的用例。

##### S3

*   当利用 S3 时，您**必须**知道它使用的最终一致性模型。在新文件上写后读。
*   了解标准、不经常访问(IA)和冰川存储类别之间的区别。关于每种技术，需要了解的关键是耐用性、可用性和首字节时间。
*   **在热门话题中，知道如何控制对桶的访问。**
*   在 S3 自动移动数据时，生命周期策略非常重要。

##### 云锋

*   了解 CloudFront 的使用案例和优势，以及与其他 CDN 产品相比的局限性。
*   了解它可以支持的源的类型(静态和动态内容)。
*   能够思考如何通过使用 CloudFront 来保护存储在 S3 的私有内容。

##### DynamoDB

*   您需要了解 NoSQL 键值存储背后的基本概念以及如何查询它们。
*   了解最常见的用例。存储会话数据、存储 S3 对象元数据和大规模数据库。
*   了解与迪纳摩相关的好处。任意规模的单位数毫秒读写延迟。
*   了解定价结构以及什么是读写单元。

##### RDS

*   了解如何配置多 AZ 部署非常重要。一个 AZ 中的主节点与另一个 AZ 中的同步辅助节点。
*   了解故障转移流程在多 AZ RDS 部署中的工作方式。
*   总是通过 IP 地址使用 DNS 端点。这也适用于 EC2。
*   熟悉自动备份和您创建的数据库快照之间的区别。
*   了解 RDS 数据库的恢复过程。

这不是一个全面的列表。这些是我学习的服务。还有更多值得阅读和了解的服务。一些是，OpsWorks，CloudFormation 和 Elastic Beanstalk。其中每一项都有一个部署和实施部分，值得在考试中了解。

### 域 3:安全

这是目前 AWS 领域非常热门的一个领域。有足够多的 S3 漏桶使得人们变得有点不安。这个领域着重于了解 AWS 处理什么，你负责什么。

##### AWS 共享责任模式

> AWS 负责云的安全性。你在云中定义你的控制**。[白皮书](https://d1.awsstatic.com/whitepapers/Security/Intro_to_AWS_Security.pdf)**

鉴于 AWS 的复杂性，这是一个相当简单的陈述。然而，这是你能记住的最重要的陈述之一。归结起来就是**你**负责保护你的系统。AWS 将保护数据中心、网络、虚拟化和存储设备。但是像静态加密、全程 SSL，以及哪些 IP 地址可以访问一组服务器，这些都取决于您。

了解分担责任模式对考试有帮助。思考这个领域的问题通常需要回头参考这个。相对于我需要做的事情，亚马逊会为我照顾什么。

你应该知道的与这个领域相关的其他事情。

*   身份访问管理(IAM):知道如何创建用户、角色，以及最重要的控制访问的策略。
*   安全令牌服务(STS):授予某人或进程对您的 AWS 资源的临时权限。
*   联合身份:使用这些身份可以避免创建 IAM 用户帐户并利用您自己的用户目录。
*   安全组与 ACL 的对比:了解每一个解决的问题以及不同之处。
*   VPC:我们之前接触过这个话题，但是真正了解这个话题也将有益于安全领域。
*   静态加密:您需要知道哪些服务提供这种功能，哪些不提供。

了解核心服务的安全原则是有好处的。了解 S3 访问策略和 IAM 实例配置文件也将派上用场。不要害怕过度学习。

### 域 4:故障排除

最后一个领域是为什么通过实际使用这些服务来为这次考试学习是如此重要。如果您从未使用过上述服务，如何对某个场景进行故障排除？你不能。这个领域是关于如何调试 AWS 中出现的常见场景。一些值得了解如何进行故障诊断的事情包括:

*   无法连接到 EC2 实例。
*   如何从已停止的 EC2 实例中恢复数据。如果有 EBS 支持，该如何做？
*   由于服务限制，无法在给定区域创建更多 EC2 实例。
*   通过 CloudWatch 日志调试 Lambda 函数中发生的错误。

这只是四个例子，但我可以向你保证，有数百个这样的例子。学习这一领域的唯一方法就是尝试，犯错误，然后从中吸取教训。

### 结论

对于知道如何利用云提供商的开发者来说，这是一个有利可图的机会。这个提供商是 AWS、Azure 还是 Google Cloud 都无关紧要。其中任何一项认证都表明了承诺。这表明您对该平台的理解超过了文档级别。阅读文档是不够的。您必须通过使用这些服务来了解可供您使用的服务。只有到那时，你才能在云端设计出充分利用它的系统。

解决方案架构师考试是众多考试之一。它涵盖了广泛的主题，会教你很多。阅读书籍、观看视频和浏览文档是很好的学习策略。也就是说，你也应该使用你正在学习的服务。没有什么会积累疤痕组织，考试答案很像经验。

### 饿着肚子学亚马逊 Web 服务？

有很多人渴望学习亚马逊网络服务。受到这个事实的启发，我创建了一个课程，专注于通过使用它来学习 Amazon Web Services。关注静态网站的托管、保护和交付问题。通过构建问题的解决方案，您可以学习 S3、API Gateway、CloudFront、Lambda 和 WAF 等服务。

AWS 周围有大量的信息。很容易迷失方向，在学习上没有任何进步。通过解决这个问题，我们可以简化信息，加快你的学习。我用这本书和视频课程的目的是与你分享我所学到的。

听起来有趣吗？查看登录页面了解更多信息，并选择适合您的套餐，[此处](https://www.kylegalbraith.com/learn-aws/)。