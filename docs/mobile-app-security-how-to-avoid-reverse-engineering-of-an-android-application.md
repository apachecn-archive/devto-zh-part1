# 移动应用安全:如何避免 Android 应用的逆向工程

> 原文：<https://dev.to/dianamaltseva8/mobile-app-security-how-to-avoid-reverse-engineering-of-an-android-application>

移动应用安全是所有工程师最优先考虑的问题，也是产品质量的重要组成部分。然而，尽管移动市场发展迅速，但盗版水平非常高，尤其是在 Android 生态系统中。

可惜现在的 app 很容易破解，从中禁用广告，甚至与验证服务脱钩。花大力气创建一个应用程序，并希望获得成功和利润，最终，你不仅会失败，还会“失去它”。

此外，一些人可能希望破解应用程序(设备、程序、软件)来了解它是如何工作的，以便窃取你的想法来做更好的东西，甚至只是复制它。

这种做法被称为**逆向工程**并被用于许多领域，包括制造业甚至军事。在本帖中，我们将讨论保护你的 Android 应用程序免受逆向工程的方法。

应用于 Android，逆向工程过程代表了从 APK 文件(zip 存档)中提取源代码和资源的方法。目标应用程序的 APK 可以通过使用 ADB 从手机中获得，或者直接从 Google Play Market 下载。

### 问题

对于解码资源，可以使用 [Apktool](https://ibotpeaches.github.io/Apktool/) 。该工具可以将资源解码为原始形式，并在修改后重建 APK。它还可以将 dex 文件转换成 Smali 源文件。Smali 更像是一种基于汇编的语言，它不能用于 Java 代码的完全重构。

要将 dex 文件反编译成 Java 代码，可以使用 dex2jar 工具。它将 dex (Android VM 字节码)转换成 jar (Java 字节码)。然后，要将 jar 反编译成 Java 源代码，您可以使用 Java 反编译程序之一，如 [jd-gui](http://jd.benow.ca/) 或 [JAD](http://www.javadecompilers.com/jad) 。

然而，这种方法有一个缺点——将 dex 转换为 jar 会丢失反编译程序可能会用到的重要元数据。存在两个从 dex 到 Java 源代码的反编译器——andro guard DAD 和 JEB。

### 分享经验

为了防止 Android 应用程序被逆向工程，我们使用了 ProGuard。ProGuard 是一个 Java 类文件收缩器、优化器、混淆器和预检验器。它的工作原理如下:

*   收缩步骤检测并移除未使用的类、字段、方法和属性。

*   优化步骤分析并优化方法的字节码。

*   模糊处理步骤使用无意义的短名称重命名剩余的类、字段和方法。

还有，多了解其他 **[避免逆向工程，保证 app 安全的有效方法和做法。](https://smartym.pro/blog/mobile-app-security-how-to-avoid-reverse-engineering-of-an-android-app/)** T8】