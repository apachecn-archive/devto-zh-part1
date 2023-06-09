# 📦创建 Guten 块:使用零配置 JavaScript 工具包#0CJS 创建 React WordPress # Guten 块

> 原文：<https://dev.to/ahmadawais/-create-guten-block-create-react-wordpress-gutenblocks-with-zero-config-javascript-toolkit-0cjs-4kf6>

[![create-guten-block](img/8f933fd99cf60ccc6290456502c50201.png)T2】](https://res.cloudinary.com/practicaldev/image/fetch/s--bRWcwjdu--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/http://on.ahmda.ws/p6XB/c)

🙌我真的很兴奋发布我最好的开源软件包之一，叫做`create-guten-block`，用它你可以开始为新的 WordPress 编辑器(计划在 WordPress 5.0 中发布)创建模块。

液体错误:内部

`create-guten-block`是一个固执己见的零配置 JavaScript 工具包，用它你不需要配置任何与 React、webpack、ESLint 等相关的东西。

所以，开始了...

[![CGB Create Guten Block by Ahmad Awais](img/1d76228cb55ceca81ec9aaa6fd6282ca.png)T2】](https://res.cloudinary.com/practicaldev/image/fetch/s--nGCYmrgq--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/http://on.ahmda.ws/osSb/c)

[![Create Guten Block](img/eb4b1e67fd32beff268215efaa1071d9.png)T2】](https://res.cloudinary.com/practicaldev/image/fetch/s--nm2iyoNx--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/http://on.ahmda.ws/orxb/c)

| **`create-guten-block`**
一个用于构建 WordPress Gutenberg block 插件的零配置开发者工具包。 |
| 由[艾哈迈德·阿瓦斯](https://github.com/ahmadawais)开发的一个 FOSS(自由&开源软件)项目。 |
| <sup>关注 Ahmad 在 GitHub 上的#FOSS 作品[@ Ahmad awais](https://github.com/ahmadawais)——说👋在推特上[@ MrAhmadAwais](https://twitter.com/mrahmadawais/)T5】</sup> |

# 📦`create-guten-block`

> `create-guten-block`是*zero configuration dev-toolkit*(# 0CJS)在几分钟内开发 WordPress Gutenberg blocks，无需配置`React`、`Webpack`、`ES6/7/8/Next`、`ESLint`、`Babel`等。

创建 Guten 块不同于其他的[初学者工具包](https://github.com/ahmadawais/wpgulp)或[样板](https://github.com/ahmadawais/Gutenberg-boilerplate)。这是一个不断更新的开发者工具箱。因为它是零配置的，所以您可以随时更新它，而无需对您的代码进行任何更改。

想象一下，你的项目中只有一个依赖项，而不是 50 个。

[![create-guten-block](img/15140d4ed1cf9d1e16fec23393ee5a12.png)T2】](https://res.cloudinary.com/practicaldev/image/fetch/s--08LJx8qF--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/http://on.ahmda.ws/p6h2/c)

`create-guten-block`是:

*   🥞版本化
*   🤠可更新
*   🗃的一套理智-默认
*   🐎一个单一的`cgb-scripts`依赖关系

[![Start](img/209060fb60f39fd95e08326dc3f35e10.png)T2】](https://res.cloudinary.com/practicaldev/image/fetch/s--8XfWN3pQ--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/http://on.ahmda.ws/osd3/c)

## 入门！

用`create-guten-block`真的很容易上手。只需将它作为一个全局模块安装，然后运行它来为 WordPress 创建下一代 Gutenberg block 插件。

让我们开始吧！

**第 0 步**——如果你没有安装`Node.js` + `npm`，那么读一下这个。(点击展开！)

如果你对`Node.js`、JavaScript 和`npm`包的世界完全是初学者，你需要做的就是去节点的网站[下载并在你的系统上安装](https://nodejs.org/en/download/)节点。这将同时安装`Node.js`和`npm`，即节点包管理器——node . js 的命令行界面

您可以通过打开终端应用程序并键入以下内容来验证安装...

```
node -v
# Results into v9.1.0 — make sure you have Node &gt;= 8 installed.

npm -v
# Results into 5.6.0 — make sure you have npm &gt;= 5.2 installed. 
```

Enter fullscreen mode Exit fullscreen mode

### →步骤#1

通过`npx`安装`create-guten-block`，并用它创建你的插件。

您需要在本地开发机器上安装节点> = 8 和 npm >= 5.3(但在服务器上不需要)。你可以使用 [nvm](https://github.com/creationix/nvm#installation) (macOS/Linux)或者 [nvm-windows](https://github.com/coreybutler/nvm-windows#node-version-manager-nvm-for-windows) 在不同项目之间轻松切换节点版本。

现在，你所要做的就是创建一个古腾堡块，并开始建设。这是通过运行`create-guten-block`命令并为将要创建的 WordPress 插件提供一个唯一的名称来完成的。

> ⚠️确保在你本地 WordPress 安装程序的插件文件夹中运行这个命令，即`/local_dev_site.tld/wp-content/plugins/`文件夹——因为这个命令会产生一个 WordPress 插件，你可以去`WP-Admin` ▶︎ `Plugins`激活它。

```
npx create-guten-block my-block 
```

Enter fullscreen mode Exit fullscreen mode

( [npx](https://medium.com/@maybekatz/introducing-npx-an-npm-package-runner-55f7d4bd282b) 附带 npm 5.2+及更高版本，请参见旧版本 npm 的[说明](https://gist.github.com/ahmadawais/99cd74a5593a9295192adf118182b509)

[![cgb block](img/fa41702acc0d979d4567c2dd07d8cf70.png)T2】](https://res.cloudinary.com/practicaldev/image/fetch/s--nPCp7sSb--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/http://on.ahmda.ws/p89T/c)

它将在当前文件夹中创建一个名为`my-block`的目录。在该目录中，它将生成初始的项目结构并安装可传递的依赖项:

```
INSIDE: /local_dev_site.tld/wp-content/plugins/my-block

├── plugin.php
├── package.json
├── README.md
|
├── dist
|  ├── blocks.build.js
|  ├── blocks.editor.build.css
|  └── blocks.style.build.css
|
└── src
   ├── block
   |  ├── block.js
   |  ├── editor.scss
   |  └── style.scss
   |
   ├── blocks.js
   ├── common.scss
   └── init.php 
```

Enter fullscreen mode Exit fullscreen mode

无需配置或复杂的文件夹结构，只需构建应用程序所需的文件。

### →步骤#3

安装完成后，您可以打开项目文件夹并运行启动脚本。

让我们去做吧。

```
cd my-block
npm start 
```

Enter fullscreen mode Exit fullscreen mode

*你也可以用`yarn start`如果那是你的果酱*

[![cgb-npm-start](img/1a9a5c23a34e3483ea49394cdf9ff9cd.png)T2】](https://res.cloudinary.com/practicaldev/image/fetch/s--ehY2c1Vc--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/http://on.ahmda.ws/orrh/c)

这将在开发模式下运行插件。产生生产代码运行`npm run build`。
您将在控制台中看到构建消息、错误和 lint 警告。

> 就这样，你正在用 Gutenberg，React.js，ES 6/7/8/Next 构建你的下一个 WordPress 插件，用 Babel 编译，它也有 ESLint 配置供你的代码编辑器自动选择和使用。

[![More](img/27b7122a57274a69302c157198ac8d46.png)T2】](https://res.cloudinary.com/practicaldev/image/fetch/s--VeTmFOXj--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/http://on.ahmda.ws/orsm/c)

### 工作流程！

在您的`create-guten-block`工作流程中，您可以使用三个脚本。使用这三个脚本，您可以开发、构建和弹出您的插件。

#### 👉`npm start`

*   用于在开发模式下编译和运行该块。
*   监视代码中的任何更改并报告任何错误。

#### 👉`npm run build`

*   用于在`dist`文件夹中为您的块构建生产代码。
*   运行一次并报告生成代码的 gzip 文件大小。

#### 👉`npm run eject`

*   用于将您的插件弹出`create-guten-block`。
*   提供所有配置，以便您可以根据需要自定义项目。
*   这是一条单行道，你必须自己维护一切。
*   你通常不需要`eject`一个项目，因为通过退出，你失去了与`create-guten-block`的联系，从那以后你必须自己更新和维护所有的依赖。

*大概就是这样。*

[![included](img/de779e300fd68143b863f19d0b1a1036.png)T2】](https://res.cloudinary.com/practicaldev/image/fetch/s--SWCxSk6l--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/http://on.ahmda.ws/orOe/c)

## 包含哪些内容？

你的环境将拥有你需要的一切来构建一个现代的下一代 WordPress Gutenberg 插件:

*   反应，JSX 和 ES6 语法支持。
*   幕后的 Webpack 开发/生产构建流程。
*   ES6 之外的额外语言，比如对象扩展操作符。
*   自动加前缀的 CSS，所以不需要`-webkit`或者其他前缀。
*   一个构建脚本，将 JS、CSS 和图像与源地图捆绑在一起用于生产。
*   通过单一依赖关系对上述工具进行无障碍更新`cgb-scripts`。

代价是**这些工具被预先配置为以特定的方式工作**。如果您的项目需要更多的定制，您可以[【弹出】](https://github.com/ahmadawais/create-guten-block#--npm-run-eject)并定制它，但是之后您将需要维护这个配置。

[![Philosophy](img/0cf0fce6d136f80fa1cd9b3bfb40f3a6.png)T2】](https://res.cloudinary.com/practicaldev/image/fetch/s--onSGyRJ0--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/http://on.ahmda.ws/orq5/c)

## 哲学

*   一个依赖关系:只有一个构建依赖关系。它使用了 Webpack、Babel、ESLint 和其他令人惊叹的项目，但在它们之上提供了一种有凝聚力的策划体验。

*   **不需要配置:**不需要配置任何东西。开发和生产版本的合理配置已经为您处理好了，因此您可以专注于编写代码。

*   **无锁定:**你可以`eject`随时进行自定义设置。运行一个命令，所有的配置和构建依赖项将被直接移动到您的项目中，因此您可以从您离开的地方重新开始。

[![Why](img/3c8336ce2e3f207e740a650c835a5981.png)T2】](https://res.cloudinary.com/practicaldev/image/fetch/s--w9rmLR1o--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/http://on.ahmda.ws/orvy/c)

## 为什么是`create-guten-block`？

嗯，像 Webpack，React，ES 6/7/8/Next，ESLint，Babel 等等，真的很难配置。在你开始写 Hello World gutenberg 块之前。事实上，随着 JavaScript 社区中所有新工具的出现和发展，您必须维护并不断更新您的配置。

`create-guten-block`将所有这些配置隐藏在一个我们称之为`cgb-scripts`的优化包中。这个包是项目中唯一的依赖项。当你继续创造下一个最好的 WordPress 主题和插件时，我们让`cgb-scripts`保持最新。

[![tldr](img/88e21dce95b263a24d398f843c3c4d28.png)T2】](https://res.cloudinary.com/practicaldev/image/fetch/s--nU7qxcZE--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/http://on.ahmda.ws/osPO/c)

## TL；速度三角形定位法(dead reckoning)

> 太久了，没看？这里有一个更短的版本。

打开终端应用程序并运行以下命令。

*   ✅ **Install/Update** : `npm install create-guten-block --global`
*   🔰**创建** : `create-guten-block my-block` —在本地 WP 安装目录下运行，例如`/wp.local/wp-content/plugins/`目录。
*   📂**浏览** : `cd my-block` —打开新创建的插件目录。
*   ♻️ **运行** : `npm start` —进行开发。
*   📦**运行** : `npm run build` —用于生产构建。
*   ⏏ **运行**:`npm run eject`——自行定制、更新、维护。

Create-Guten-Block 已经过测试，可以在 macOS 上运行，但也必须在 Windows 和 Linux 上运行。
如果有问题，请提交[问题→](https://github.com/ahmadawais/create-guten-block/issues/new)

[![update](img/edb42600e639069cbf14173922eb4558.png)T2】](https://res.cloudinary.com/practicaldev/image/fetch/s--fsvOthuJ--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/http://on.ahmda.ws/osO7/c)

## 更新到新版本

创建 Guten 块分为两个包:

1.  **`create-guten-block`** 是一个命令行实用程序，你可以用它来创建新的 WP 古腾堡插件——只要运行`npx create-guten-block your-block-name`，你就可以一直使用最新的 create-guten-block 工具包。
2.  **`cgb-scripts`** 是生成插件项目中的一个开发依赖。

你几乎不需要更新`create-guten-block`本身:它将所有的设置委托给`cgb-scripts`。

当你运行`create-guten-block`时，它总是用最新版本的`cgb-scripts`创建项目，所以你会自动获得新创建插件的所有新特性和改进。

要将现有项目更新到新版本的`cgb-scripts`，请打开[变更日志](https://github.com/ahmadawais/create-guten-block#changelog)，找到您当前的版本(如果您不确定，请查看插件文件夹中的 package.json)，并应用新版本的迁移说明。

在大多数情况下，在 package.json 中修改`cgb-scripts`版本并在这个文件夹中运行`npm install`就足够了，但是最好参考一下[的变更日志](https://github.com/ahmadawais/create-guten-block#changelog)以了解潜在的重大变更。

我们致力于保持突破性的改变最小化，这样你就可以轻松地升级`cgb-scripts`。

[![Log](img/5750525f0fcbd3ef161327a532db514a.png)T2】](https://res.cloudinary.com/practicaldev/image/fetch/s--xzy2mpo7--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/http://on.ahmda.ws/osUz/c)

## 变更日志

阅读什么📦新的，👌改进了，🐛固定，如果📖文件更新了。

👉点击此链接阅读整个变更日志— [CGB 变更日志→](https://github.com/ahmadawais/create-guten-block/blob/master/CHANGELOG.md)

没有什么是完整的，所以请容忍我们，让我们不断迭代，走向更美好的未来。

> ```
> 'Coz every night I lie in bed
> The brightest colors fill my head
> A million dreams are keeping me awake
> I think of what the world could be
> A vision of the one I see
> A million dreams is all it's gonna take
> A million dreams for the world we're gonna make ... 
> ```
> 
> ...*听→ [一百万个梦想！](https://www.youtube.com/watch?v=pSQk-4fddDI)T3】*

[![Hello](img/1cbbd570e01a44d47e5ec3b29f8247cc.png)T2】](https://res.cloudinary.com/practicaldev/image/fetch/s--ygAQeunb--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/http://on.ahmda.ws/os6O/c)

#### **你好，我们是 [WordPress 夫妇](https://WPCouple.com)** ！

我( [Ahmad Awais](https://twitter.com/mrahmadawais/) )是一名完整的网络开发人员，也是 WordPress 的定期核心贡献者。我的另一半([梅达哈·巴图尔](https://twitter.com/MaedahBatool/))是一名技术项目经理，她也是 WordPress 的核心贡献者。我们和我们的[团队](https://WPCouple.com/team)一起运营[WPCouple.com](https://WPCouple.com/)。

如果你想深入了解我们对开源软件、专业全栈开发、WordPress 社区、JavaScript 的发展或成家、创业的热爱，那么就订阅我们名为↣ [The WordPress Takeaway](https://WPTakeaway.club) 的优质简讯吧！

#### [**支持我们的开源项目！**](https://pay.paddle.com/checkout/515568) 🎩

如果你希望我们继续生产专业的自由和开源软件(FOSS)。考虑为我一小时的开发时间付费。我们将花两个小时在每个贡献的开源上。是的，没错，你付了一个小时的钱，然后让我们俩花一个小时作为感谢。

[![Partners](img/6907ad554191b101cfa57b34d1b6393f.png)T2】](https://res.cloudinary.com/practicaldev/image/fetch/s--Ld_PQnlS--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/http://on.ahmda.ws/osEJ/c)

### 项目支持方& [WPCouple 合作方](https://WPCouple.com/partners) ⚡️

这个 FOSS(自由和开源软件)项目是在下面列出的优秀企业的帮助下更新和维护的。没有这些了不起的公司/个人的支持，这个项目是不可能的。

——*什么/怎样？[了解详情→](https://WPCouple.com/partners)T3】*

| [![](img/b9cafdeac6a61cde9e42b45eece3b9eb.png)T2】](https://www.gravityforms.com/?utm_source=WPCouple&utm_medium=Partner) | [![](img/17ad73b2eec95e787dda6766939b4aba.png)T2】](https://kinsta.com/?utm_source=WPCouple&utm_medium=Partner) | [![](img/8014e46d93054bb5a02678b8a15530b4.png)T2】](https://wpengine.com/?utm_source=WPCouple&utm_medium=Partner) |
| [![](img/08755f07033549525ecc607769eca5ab.png)T2】](https://www.sitelock.com/?utm_source=WPCouple&utm_medium=Partner) | [![](img/d87423ee9cbf5431cc12b47e4ab5db80.png)T2】](https://wp-rocket.me/?utm_source=WPCouple&utm_medium=Partner) | [![](img/80b5c0f18515df4c19522e0a7ce3287b.png)T2】](https://blogvault.net/?utm_source=WPCouple&utm_medium=Partner) |
| [![](img/7f329be28828399f8b8d62dd23dfe23d.png)T2】](http://cridio.com/?utm_source=WPCouple&utm_medium=Partner) | [![](img/c48d3609845a863cafad1fe786fb745d.png)T2】](http://wecobble.com/?utm_source=WPCouple&utm_medium=Partner) | [![](img/dbcb9c95b7de24efa708f62ce0aca8fc.png)T2】](https://www.cloudways.com/?utm_source=WPCouple&utm_medium=Partner) |
| [![](img/76674c7bf1044b28336782ddf47ddb4a.png)T2】](https://www.cozmoslabs.com/?utm_source=WPCouple&utm_medium=Partner) | [![](img/f6ea86c6ea3f9ce17de562b70b12c5ec.png)T2】](https://wpgeodirectory.com/?utm_source=WPCouple&utm_medium=Partner) | [![](img/fb176a9738ce0cc205e4cefd570797ac.png)T2】](https://www.wpsecurityauditlog.com/?utm_source=WPCouple&utm_medium=Partner) |
| [![](img/b274d2dbc4896a1cd57a1dcac6d574ea.png)T2】](https://mythemeshop.com/?utm_source=WPCouple&utm_medium=Partner) | [![](img/2e0d3e69d4f66ed636efaf7ed9477e0b.png)T2】](https://www.liquidweb.com/?utm_source=WPCouple&utm_medium=Partner) | [![](img/25c39b0c39b7e4e78136a230ae39b706.png)T2】](https://WPCouple.com/contact?utm_source=WPCouple&utm_medium=Partner) |

[![Thanks](img/411ce3934b623ca35b03d7f13768b5d6.png)T2】](https://res.cloudinary.com/practicaldev/image/fetch/s--7OCtTDXU--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/http://on.ahmda.ws/orkW/c)

## 执照&归属

艾哈迈德·阿瓦斯。

这个项目的灵感来自于比我在这里能提到的更多的人的工作。不过，还是要感谢创建 React App 的[丹·阿布拉莫夫](https://twitter.com/dan_abramov)、React.js 团队的[安德鲁·克拉克](https://twitter.com/acdlite)和[克里斯多夫·切多](https://twitter.com/vjeux)、[索菲·阿尔珀特](https://twitter.com/sophiebits)、React[React](https://ReactForBeginners.com/friend/AHMADAWAIS)、 [ES6](https://ES6.io/friend/AHMADAWAIS) 和 [Node](https://LearnNode.com/friend/AHMADAWAIS) 初学者的[韦斯·博斯](https://twitter.com/wesbos)的精彩课程。 [Kent C. Dodds](https://twitter.com/kentcdodds) 为他的开源布道，WordPress 核心贡献者， [Gary](https://twitter.com/GaryPendergast) 为保持每个人的理智， [Gutenberg](http://github.com/wordpress/gutenberg) 开发者 [Matias](https://twitter.com/matias_ventura) ， [Riad](https://github.com/youknowriad) ， [Andrew](https://github.com/aduth) ， [Ella](https://twitter.com/ellaiseulde) ，[黄智中](https://github.com/jasmussen)， [Tammie](https://twitter.com/karmatosed) ， [Greg](https://twitter.com/gziolo) 和贡献者，以及其他

[![Thanks](img/a6fdfb0ccd09288c3a8f92b8a51ae8ce.png)T2】](https://res.cloudinary.com/practicaldev/image/fetch/s--TEuNNLFD--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/http://on.ahmda.ws/oy5y/c)

### 更新

*   🚀 [`create-guten-block`](https://github.com/ahmadawais/create-guten-block) 已经火了~ 500[GitHub 上的观星者](https://github.com/ahmadawais/create-guten-block/stargazers)
*   🙌呜！呜！今天，[项目正在 GitHub JavaScript repos 上成为](http://on.ahmda.ws/oytg)的热门话题
*   😇今天很荣幸被列为 GitHub 上的[趋势开发者——这太疯狂了！](http://on.ahmda.ws/oz9O)
*   🔥Holly Molly — [`create-guten-block`](https://github.com/ahmadawais/create-guten-block) 现在是 GitHub 上所有语言的[趋势！](http://on.ahmda.ws/oy9x)
*   📣create-guten-block 在 ProductHunt 的主页上排名前五，这太棒了
*   😇来自 a8c 的 Gary 通过[写下这条意义重大的推文](https://wptavern.com/gutenberg-boilerplate-demonstrates-how-to-build-custom-blocks),以他的方式来欣赏 create-guten-block 工具包
*   🍩韦斯·博斯是的，就是那个，在推特上说他计划如何[试用 create-guten-block](https://twitter.com/wesbos/status/955426735532724224) 和新的 WordPress Gutenberg 编辑器
*   😲马特·克伦威尔把我和[古腾堡样板](https://ahmadawais.com/gutenberg-boilerplate/)和 [`create-guten-block`](https://github.com/ahmadawais/create-guten-block) 项目一起列入了[他的 2018 年跟进名单](https://www.mattcromwell.com/who-what-ill-follow-in-2018/)
*   ✅我为此写了一篇博文:[介绍 Create Guten Block](https://ahmadawais.com/create-guten-block-toolkit/)

液体错误:内部

> 🔥如果你[在推特上发布关于它的消息](https://twitter.com/home?status=%F0%9F%94%A5%20Configuring%20and%20maintaining%20React,%20Webpack,%20ES6/7/8/Next,%20ESLint,%20Babel,%20etc.%20is%20not%20what%20I%20do%20while%20creating%20%40WordPress%20%23Gutenberg%20blocks.%0A%0AI%20use%20a%20%230CJS%20dev%20%23toolkit%20called%20%60create-guten-block%60%20by%20%40MrAhmadAwais%20%F0%9F%9B%A0%F0%9F%9A%80%0A%0A%F0%9F%91%89%20CHECK%20IT%20OUT%3A%20https%3A//AhmdA.ws/CreateGutenBlock_%20%20%0A)，尝试一下，并做出贡献，那对我来说将意味着整个世界。