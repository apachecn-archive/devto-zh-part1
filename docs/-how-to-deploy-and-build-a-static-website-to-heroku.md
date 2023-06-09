# 🚀如何在 Heroku 上部署和构建一个静态网站

> 原文：<https://dev.to/edvinsantonovs/-how-to-deploy-and-build-a-static-website-to-heroku>

> 这不是一个无关紧要的教程，而是一个我如何能够在 Heroku 上构建和部署我的静态网站的故事。

* * *

最近我在做一个兼职项目，这是一个名为 [**黑客炒作**](http://www.hackerhype.com/) 的在线黑客马拉松平台的登陆页面。这次我想从**数字海洋**换成 **Heroku** 试试。我之前一直使用 Heroku 来部署我的开源软件，所以我觉得部署一个简单的静态页面应该不难。好吧，也许我说得太早了，但我花了一些时间才完成。

* * *

首先，我将源代码存放在 GitHub 的私有存储库上。如果您没有使用过 Heroku，它有一个非常简单的特性，允许您在每次向存储库推送内容时直接编排部署。

显然，在存储库中我有两个分支`master`和`develop`。我使用`master`分支进行自动部署。所以每当我完成一件事情，我所需要的就是将`develop`合并到`master`。好了，在这个阶段，我已经设置好了让我的开发工作流运行所需的一切。

[![](img/e52f9c2934724c0ebe4f8a3343b0aeb0.png)T2】](https://res.cloudinary.com/practicaldev/image/fetch/s--NGE0-2Vi--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/http://edvinsantonovs.co.uk/conteimg/2017/08/deploy.PNG)

* * *

下一步是使用`Gulp`将`scss`和`js`文件构建到生产就绪项目中。从那里我需要在 Heroku 的`Procfile`中配置 [`http-server`](https://github.com/indexzero/http-server) 来服务我的静态文件。这部分花了我一点时间才弄明白。配置`Procfile`才是真正的挑战。我甚至在 StackOverflow 上发布了一个[问题，因为我对如何在 Heroku 的一个`Procfile`中运行多个命令感到困惑。](https://stackoverflow.com/questions/44733986/how-to-run-procfile-with-multiple-commands-on-heroku/44735878#44735878)

因此，为了构建项目，我要求执行下面的命令

*   `npm install`
*   `gulp build` <small>(将生成`/public`文件夹)</small>
*   `http-server` <small>(默认将`/public`文件夹送达)</small>

我尝试了几种配置`Procfile`的方法，但没有一种对我有效。

*   `web: npm install; gulp build; http-server`
*   `web: npm install & gulp build & http-server`

我花了一些时间研究，找到了答案。默认情况下，Heroku 从`package.json`开始安装所有的包，所以不再需要`npm install`。然后我需要跑`gulp build`和`http-server`。为此，我在`package.json`中添加了`"postinstall" : "gulp build"`，所以我的`Procfile`是一个只有一个命令的单行文件- `web: http-server`。化繁为简解决了问题！现在我能够在 Heroku 上部署和构建我的静态网站了！🎉🎉🎉

[![](img/555fc94b398ff71d4b4bae3c82dc9895.png)T2】](https://res.cloudinary.com/practicaldev/image/fetch/s--0y3Lr9Ug--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/http://edvinsantonovs.co.uk/conteimg/2017/08/hackerhype.PNG)

* * *

让我们总结一下这个过程。我有一个静态网站，它的文件是通过 gulp 编译的。然后 Heroku 的`Procfile`被配置为使用`http-server`来服务静态的`html` / `css` / `js`文件。这导致了非常同步的开发和部署流程。

* * *

最初发布在[我的博客](http://edvinsantonovs.co.uk/how-to-deploy-and-build-a-static-website-to-heroku/)上。