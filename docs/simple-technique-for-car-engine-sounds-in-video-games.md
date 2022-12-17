# 视频游戏中汽车引擎声音的简单技巧

> 原文：<https://dev.to/buntine/simple-technique-for-car-engine-sounds-in-video-games>

当我在做 Swervin’Mervin 的时候，有一件事一直在我的待办事项列表上。这看起来很简单，但是摆脱它比我最初想的要困难得多。

我想做的只是:

> 根据速度产生发动机声音

我不知道我要怎么做，但是我知道一些事情。比如我就知道效果不需要完美。它只需要让玩家头脑中有一个大概的想法，剩下的就是他们的想象力了。我也知道我不想太深地掉进音频信号处理的兔子洞，因为我知道一旦我爬进去，我就再也出不来了，或者我会像一个失败的烂摊子一样爬出来。

我首先想到的是产生一个锯齿波，并根据玩家的速度设置频率。我知道这在理论上是可行的，因为经典街机游戏《T2》的音效程序员使用了类似的(但更先进的)技术。我设置了一个小原型，它工作正常，但不幸的是，听起来几乎不像汽车发动机。我已经用[网络音频 API](https://developer.mozilla.org/en-US/docs/Web/API/Web_Audio_API) 重新制作了效果。我开始尝试更高级的波形，但很快意识到我正滑入前面提到的厄运之兔洞。

如果我在 1979 年发布 Swervin' Mervin，我在波形生成方面半生不熟的尝试可能已经足够了。唉...

我的下一个想法是找到一个运行引擎的声音片段，我可以无缝地循环，并简单地改变音高和/或回放速度以响应播放器速度的增加。当我意识到 [Pygame](http://www.pygame.org/) 中的声音库根本不支持无缝循环时，这个想法就不攻自破了。每个循环之间有几毫秒的间隔，这完全破坏了效果。但是后来我在文档中注意到[我可以对声音进行排队](https://www.pygame.org/docs/ref/music.html#pygame.mixer.music.queue)。厉害！但是，令我沮丧的是，它根本不起作用。我尝试了我能做的一切，直到我最终发现[它有点不工作](http://stackoverflow.com/questions/25277724/pygame-music-queue-not-functioning)。非常...

我已经[使用(很明显)更强大的 WebAudio API 再次重现了汽车引擎音效](http://bunts.io/experiments/engine2)。至于一个简单的引擎效果，这个对我来说实际上很好...

我还有最后一个想法，就是播放一段汽车引擎从空转到完全加速的音乐片段，并记录我们在水流中的位置。如果玩家停止加速，另一段与第一段相反的音乐将从同一位置开始播放。很简单，是吧？事实证明 Pygame 并没有为我们提供一种简单的方法来跟踪声音文件中的当前位置！当然，WebAudio API 可以...

这些小实验给我上了重要的一课:

在选择依赖关系时要格外小心！

我一直知道汽车发动机的声音是我想添加到 Swervin' Mervin 中的东西，但我对 Pygame 太有信心了，以至于我从来没有真正费心去研究它到底有多“强大”。事实证明，Pygame 几乎已经死亡，上一个稳定版本是在 6 年前！像生活中的所有事情一样——不要轻易做决定...快乐编码。

我在这里提到的 WebAudio API 例子也可以在 Github 上的 [my repository](https://github.com/buntine/CarEngines) 中找到。