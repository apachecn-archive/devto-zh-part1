# 弹性“全球”RSL

> 原文：<https://dev.to/kritner/flex-global-rsls-51ef>

我正在考虑以“全球 RSL 库”的方式在 flex 中部署我们的定制库。我不知道如何确切地描述我们正在努力做的事情，但我打算试一试。

在我到目前为止发现的每个例子中，当使用 RSLs 时，编译时指定的路径要么是:

1)相对于应用程序的部署路径(swf)

2)绝对路径。

由于我们的开发过程和站点布局，以上两种使用 RSL 的方法都不理想。我希望找到一个解决方案，为一个 RSL 指定一个相对于 web 根目录的相对路径。

例如，如果我指定/libs/rsl.swf 作为我的路径，当启动位于[http://192 . 168 . 1 . 50/some directory/some other directory/project . swf](http://192.168.1.50/someDirectory/someOtherDirectory/project.swf)的我的 swf 时，swf 将访问位于[http://192 . 168 . 1 . 50/libs/rsl . swf](http://192.168.1.50/libs/rsl.swf)的 RSL

我们在选项 1 中试图避免的问题是，我们的 swf 文件位于整个站点的不同目录中，并且到处都有库的重复副本是多余的，并且使更新我们的库更加困难，因为我们必须确保在 RSL 存在的每个路径中进行部署。

选项 2(绝对路径)也不是特别好，因为我们的代码在不同的环境中进行测试和 QAd(但在我们的开发环境中只编译一次)，所以在生产之前为每个环境指定我们的绝对生产 RSL URL 和故障转移 URL 有很大的误差，而且据我所知，编译选项不是我们的 QA 流程中可以审查的内容(以确保开发人员[我]输入正确的生产 RSL 路径)

我试图完成的事情明白了吗？我不可能是第一个想这样做的人，难道我只是忽略了互联网上的解决方案吗？

*   克里斯特