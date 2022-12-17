# 我们怎么连 JS？(Nylas 的 Javascript 堆栈的组件)

> 原文：<https://dev.to/nylas/how-do-we-even-js-the-components-of-nylass-javascript-stack-6h>

[![How Do We Even JS? (The Components of Nylas's Javascript Stack)](img/377a31d2e9c2ecb124cd1d628da197cb.png)T2】](https://www.nylas.com/blog/how-do-we-even-javascript)

在过去的几年里，Javascript 疲劳已经变得非常普遍，这使得在没有高度焦虑的情况下从大量工具和框架选项中进行选择变得非常困难。

[![how do we even?](img/5e615e3e2d57aadcc96a61fbb8d564a0.png)T2】](https://res.cloudinary.com/practicaldev/image/fetch/s--ClcgpbLB--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_66%2Cw_880/https://www.nylas.com/hs-fs/hubfs/giphy%2520%282%29.gif%3Ft%3D1513026317424%26width%3D600%26height%3D340%26name%3Dgiphy%2520%282%29.gif)

幸运的是，现在已经是 2017 年了，比我聪明的人已经做出了很多这样的选择。

虽然 [Nylas](https://www.nylas.com/) 的主要代码库是用 Python 编写的，但我们已经用 Javascript 构建了一段时间，并与它一起成长；我们有一个很大的代码库，你可以在那里找到 Coffeescript、普通的 ES5、ES6、React、JSX、 *CJSX* (我知道，WTF？)，以及许多风格的 Flux、Redux 和基于可观察的架构。

不用说，我们很高兴开始一个新的绿地项目——[我们为我们的 API 客户新的 Nylas 仪表板](https://www.nylas.com/blog/announcing-the-nylas-dashboard-2.0)——并尝试 React 社区转向的所有最新工具和实践。

在本帖中，我们将回顾我们为在 2017 年开始一个新的网络项目所做的选择。

*TL；博士:*我们咬紧牙关，用了一堆脸书制造的工具。(为他们的[新的麻省理工学院 React 许可证欢呼！](https://code.facebook.com/posts/300798627056246/relicensing-react-jest-flow-and-immutable-js/))

## 节点

使用最新的节点，为什么不呢？

```
install nvm
nvm install 8
nvm use 8 
```

Enter fullscreen mode Exit fullscreen mode

✌️

## 纱线

在开始之前，我们必须选择一个依赖管理器。我们一直使用效果很好的 npm，但出于以下几个原因，我们决定使用 yarn:

*   [锁文件](https://yarnpkg.com/lang/en/docs/yarn-lock/)用于跨机器的一致安装
*   [似乎更快了](https://yarnpkg.com/lang/en/compare/)
*   输出有表情符号✨
*   我们可以只运行纱线，而不是 npm 安装
*   默认情况下，依赖项保存在 package.json 中，无需添加`--save`标志

IMO 的杀手锏是运行自定义脚本，而不必在脚本前面加上 run。假设您的 package.json 中有以下脚本:

```
// Your package.json
"scripts": {
  "win": "node ./scripts/win.js",
}, 
```

Enter fullscreen mode Exit fullscreen mode

要使用 npm 运行该脚本，您必须键入:`npm run win`。但是有了纱，你只需要打字:`yarn win`。感觉真好。

(请记住，npm v5 是最近[发布的](http://blog.npmjs.org/post/161081169345/v500)，带有 yarn 提供的许多好东西，比如锁文件、更好的性能和更好的 CLI。你可能也想用它！)

## 创建-反应-应用

我们写《反应》已经有一段时间了，所以我们想在我们的项目中继续使用它。然而，从头开始一个使用现代 Javascript 的反应项目并不容易，因为它需要大量的配置:

*   webpack(或 browserify，或 rollup，或 brunch，或…)来生成发布到浏览器的构建。这本身就需要大量的配置。
*   巴别塔传输你的代码。它*也*需要大量的配置。此外，了解您在代码中使用的哪些 Javascript 特性需要被编译，以便它们可以在您想要支持的浏览器中运行，确保您根据您的目标浏览器填充正确的内容(例如，Promise、fetch)，以及更多我们可能还没有意识到的内容。
*   对你的代码进行 lint
*   比我可能已经忘记的更多
*   然后把它们绑在一起！

但是，正如我提到的，现在已经是 2017 年了，感谢上帝 [create-react-app](https://github.com/facebookincubator/create-react-app) 的存在。只需一个命令，您就可以搭建一个 React 应用程序，该应用程序预配置了 webpack、babel、eslint、一个可以自动重新加载的开发环境、生成优化生产构建的脚本等。

```
yarn global add create-react-app
create-react-app dope-af
# ✨~magic~✨
cd dope-af
yarn
yarn start  # Start development server
yarn build  # Create optimized production build 
```

Enter fullscreen mode Exit fullscreen mode

此外，它还配有一份出色的[用户指南](https://github.com/facebookincubator/create-react-app/blob/master/packages/react-scripts/template/README.md)，里面有你想做的几乎所有事情的信息。

您可以只使用 create-react-app 来完成，但是如果您需要修改开箱即用的配置，您可以运行 [eject](https://github.com/facebookincubator/create-react-app/blob/master/packages/react-scripts/template/README.md) 命令来手动管理配置。

我发现默认配置中缺少了一些东西，比如 [#2310](https://github.com/facebookincubator/create-react-app/pull/2310) ，但幸运的是这个社区非常活跃，我相信这些东西会被包含进来，而不必退出。

## 是

create-react-app 开箱即用，jest 被配置为其测试运行程序。在本帖中，我们不会讨论如何使用 jest 编写测试，但可以说，这是 dope AF。这次谈话说服了我。

## eslint

通过 create-react-app，eslint 预配置了合理的[默认值](https://github.com/facebookincubator/create-react-app/blob/master/packages/eslint-config-react-app/index.js)。如果想扩展，只需要写一个自定义就可以了。eslintrc 文件:

```
// .eslintrc
{
  "extends": "react-app",
  "rules": [
    "prefer-const": "warn"  // custom rules
  ]
} 
```

Enter fullscreen mode Exit fullscreen mode

当您运行 yarn start 或 yarn build 时，您的代码将默认被 linted，但是您也可以添加一个自定义脚本:

```
yarn add --dev eslint@3.19.0  # Same version that create-react-app uses

// Your package.json
"scripts": {
  "lint": "eslint ./src ./scripts",
}, 
```

Enter fullscreen mode Exit fullscreen mode

## 流量

[flow](https://flow.org/) 是 Javascript 的静态类型检查器。有许多支持和反对静态类型检查器的论点，但是在我们在 Nylas 这里发展了一个巨大的 Javascript 代码库之后，类型的价值变得越来越明显，特别是对于代码库中的核心抽象和高度使用的模块。

一个好的方面是 flow 支持逐步类型化，这意味着类型注释不是到处都需要的。这意味着如果你正在原型化或者编写你知道可能会改变的东西，你不需要使用类型，但是如果你正在你的代码库中编写一个核心模块，你可以用类型来锁定它。

类型可能是有益的，因为:

*   当进行变更或重构时，它们给了我们更多的信心
*   它们作为文档(不会变得陈旧，不像评论)
*   它们防止了许多不必要的单元测试，我们通常只是为了检查类型而编写这些测试

create-react-app 默认不启用 flow，但是，当然，用户指南指定了[如何做](https://github.com/facebookincubator/create-react-app/blob/master/packages/react-scripts/template/README.md#adding-flow)。

在配置 flow 时，我们做了一件额外的事情，就是将它改为将类型错误报告为 eslint 错误:

```
yarn add --dev eslint-plugin-flowtype-errors

// Your .eslintrc
{
  "extends": [
    "react-app"
  ],
  "plugins": [
    "flowtype-errors"
  ],
  "rules": {
    "flowtype-errors/show-errors": 2,
    "prefer-const": "warn"
  }
} 
```

Enter fullscreen mode Exit fullscreen mode

这很有用，因为如果您已经在编辑器中配置了 eslint，就不需要额外的编辑器集成来支持 flow。它也适用于您已经用 eslint 配置的其他工具。例如，我们在 Nylas 使用 Phabricator 进行代码审查，并且我们已经将其与 eslint 集成，因此我们不必为 flow 编写新的集成。

## 漂亮些

[appetter](https://github.com/prettier/prettier)是一个 Javascript 代码格式化程序。这意味着它是一个程序，将您的 javascript 代码作为输入，然后输出相同的代码，但经过格式化。代码将以标准的方式进行格式化，因此看起来都是一样的——例如，使用相同的间距规则、放置换行符的位置等等。

这很棒，因为:

*   您不必在编写代码时花费时间手动格式化代码。你可以写你能想到的最丑的代码，只要它是有效的代码，漂亮就会自动地让它变得更漂亮。
*   你有一个快速和自动化的格式化代码的方法，所以你的 repo 中的所有代码看起来都是一样的，这使得它更容易阅读和理解。
*   你不会为代码应该如何格式化而争论不休，因为不管人们想怎么写，代码都被卸载到工具中了。

create-react-app 没有关于更漂亮的部分，但这就是我们在这里的原因！我们是这样配置的:

```
yarn add --dev prettier eslint-config-prettier eslint-plugin-prettier

// Your package.json
"scripts": {
  "prettier": "prettier --single-quote --trailing-comma es5 --write \"!(build)/**/*.js\"",
},

// Your .eslintrc
{
  "extends": [
    "react-app",
    "prettier",
    "prettier/flowtype",
    "prettier/react"
  ],
  "plugins": [
    "flowtype-errors",
    "prettier"
  ],
  "rules": {
    "flowtype-errors/show-errors": 2,
    "prettier/prettier": ["error", {
      "singleQuote": true,
      "trailingComma": "es5"
    }],
    "prefer-const": "warn"
  }
} 
```

Enter fullscreen mode Exit fullscreen mode

这里发生了一些事情，所以让我们把它们具体化:

*   我们定义了一个自定义的更漂亮的脚本:纱更漂亮。运行时，它将读取不在 build/目录中的任何代码，并以正确的格式写回。还包括一些基本的配置[选项](https://github.com/prettier/prettier#options)给更漂亮的。
*   我们希望 eslint 报告 prettier 检测到的任何格式错误。为此，我们添加了 eslint-plugin-appearlier，并在插件和规则部分启用了它:

```
 "plugins": [
    "flowtype-errors",
    "prettier"
  ],
  "rules": {
    "flowtype-errors/show-errors": 2,
    "prettier/prettier": ["error", {
      "singleQuote": true,
      "trailingComma": "es5"
    }],
    "prefer-const": "warn"
  } 
```

Enter fullscreen mode Exit fullscreen mode

需要注意的一点是，我们必须在这个文件中复制我们更漂亮的配置(😢)和我们的 package.json 中，因为 prettier 目前不支持配置文件。

最后，eslint 本身包含了几个格式规则，但是考虑到我们使用的是 prettle，我们不希望 eslint 抱怨 prettle 将处理的格式规则。为了实现这一点，我们添加了 eslint-config-appellister，它将禁用任何影响格式的 eslint 规则。为了启用它，我们添加了这些额外的扩展:

```
 "extends": [
    "react-app",
    "prettier",
    "prettier/flowtype",
    "prettier/react"
  ], 
```

Enter fullscreen mode Exit fullscreen mode

就是这样！我们的基本漂亮工作流程以如下方式工作:

*   写代码
*   尝试提交差异
*   我们的 diff 工具通过 eslint 报告更漂亮的错误
*   运行纱线更漂亮
*   提交差异！🎉

你也可以通过在你的编辑器中添加更漂亮的来进行更紧密的集成，这样它可以在你输入或者保存文件的时候格式化你的代码，这样你就不需要显式的运行 yarn prettier 了。然而，编辑器集成是另一篇文章的主题。

这就是我们在 Nylas 的工作方式！(或者至少我们是如何努力的。)

最后，我想感谢每一个花时间构建和贡献这些令人敬畏的工具的人，在我看来，这些工具让 2017 年的 Javascript 开发变得更加有趣。

你们公司是怎么做 JS 的？请在下方留言评论。

这篇文章最初发表在 Nylas 工程博客上。

[![](img/7c2b8f1b249d8765a6eba5f0970d99ad.png)T2】](https://res.cloudinary.com/practicaldev/image/fetch/s--NLup0_8a--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_66%2Cw_880/http://track.hubspot.com/__ptq.gif%3Fa%3D3314308%26k%3D14%26r%3Dhttps%253A%252F%252Fwww.nylas.com%252Fblog%252Fhow-do-we-even-javascript%26bu%3Dhttps%25253A%25252F%25252Fwww.nylas.com%25252Fblog%26bvt%3Drss)