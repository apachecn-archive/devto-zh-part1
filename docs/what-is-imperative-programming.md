# 什么是命令式编程？

> 原文：<https://dev.to/mortoray/what-is-imperative-programming>

命令式编程是一种[范式](https://mortoray.com/topics/paradigms/)，它明确地告诉计算机做什么和如何做。与大多数其他方法不同，它是关于数据和执行的相对具体的视图——没有太多神秘或抽象的运行时行为。命令式编程的基本方面是顺序指令和可变数据。

命令式编程是计算的基石。CPU 主要作为命令执行引擎工作，编译器翻译成这种语言。作为我们编程历史中驱动计算机的主要方式，它在语言领域得到了很好的体现。

> 我不是说所有的计算都是这样工作的。一个显著的区别是 GPU。它的主要功能与 CPU 的顺序性质非常不同。但是这篇文章是关于命令式世界的。GPU 更多地遵循函数范式。

## 为什么？

将一个问题分解成几个步骤是我们都可以自然而然做到的事情。我们理解序列和流程图中的真实世界:事物有一个状态，发生了一些事情，然后它们有一个新的状态。这相对容易映射到命令式编程。

计算机和网络是必不可少的。许多事情必须以一定的顺序发生，记忆必须以特定的方式构建。命令式编程适合于触及这些低级领域的用例。

在实现其他范例时，命令式编程是适应性最强的。这是创建工具和特定领域语言的起点。当没有其他方法适用时，这是一个后备方案。

> 本文主要关注命令式编程的好处和核心品质。所有的范例都有缺点；我将在以后的文章中讨论这些内容。

## 序列

命令式编程最突出的是指令和分支的顺序流。

```
var a = 5;
var b = calculate(a);
if( b > 10 ) {
   print("Too big");
   return;
} 
```

代码行从上到下一次执行一行。变量`a`中存储有`5`的值。然后`a`的值由`calculate`函数获取。结果被分配给`b`，然后检查`if`条件。不管我们的功能有多大，它们总是可以被看作是一组按顺序执行的独立的谨慎的步骤。

> 这里有一个非常大的“假设”规则在起作用。代码“好像”遵循我刚才提到的那些规则执行。编译器可以自由地在我们的代码中寻找目标，并应用各种优化:快捷方式、重写和重新排序。CPU 很少关心我们调试代码以及对代码进行重新排序、缓存和分支预测的需要。“假设”规则表明，只要结果与执行我们编写的指令相同，这是可以的。

## 可变变量

这种排序依赖于可变变量。变量代表存储位置，而不仅仅是一个值。跟我一起通过几个微不足道的例子，有一点可以说明这一点。

```
int a;
a = 5; 
```

变量`a`包含一个整数。首先，它是未定义的，或者有一个默认值，这取决于语言。我们给它赋值`5`。`a`现在包含了这个值的副本，与常量值`5`完全无关。

```
int b = 6;
a = b;
b = 7; 
```

`a`和`b`是不同的值。当我们将`b`赋值给`a`时，我们得到了该值的一个副本；当`7`稍后被分配给`b`时，它不会改变`a`的值。可以使用指针(或者引用，或者你最喜欢的语言为它们发明的任何词)将变量绑定到相同的值。

```
int b = 5;
int* a = &b;
//a == 5
*a = 6;
//b == 6 
```

这些例子可能看起来微不足道，但是它们是这个范例的重要方面。命令式编程有一个直接的内存概念。我们得到一个画布，我们可以在其中随意读写值。这要求我们理解值和指针。许多语言甚至允许我们将内存重新解释为任意类型。

> 并发处理给命令式编程带来了一个问题。一般的范例仍然有效，但是线程之间的“假设”规则明显变得宽松了。只有特殊指令才能保证在并行线程之间有任何顺序。只有当我们尽力使数据一致时，才要求数据一致。未能向并行的神致敬将会招致恶灵在程序中游荡，并以令人愤怒的难以破译的模式粉碎比特。

### 功能

顺序排序和可变数据定义了函数的工作方式。像它的函数式编程表亲一样，一个函数可以简单地接受输入并提供一个计算结果，但是在命令式编程中，它可以做的事情是无限的。一个函数可能有各种各样的副作用，改变全局内存值、填充数据库、加载屏幕纹理、开始打电话等等。

所有函数的共同点是在特定点被调用，并在调用方继续之前完成。函数不会部分执行，也不会多次执行(同样适用“假设”规则)。

```
int calc(int q) {
    int a = one(q);
    int b = two(q);
    return b;
} 
```

`a`不用也没关系，`one`万一有副作用还得评估。它也必须在`two`之前进行评估。这些函数中的所有指令在这个函数中都有一个定义好的全局顺序。当组件之间通信时，命令式范式依赖于此。考虑一个库的安装和拆卸:

```
lib_handle h;
lib_init(h);
lib_call(h, 1, 2, 3);
lib_release(h); 
```

编译器从来不知道我们要做什么，它只知道我们告诉它做什么。有人会说命令式编程包含最少的“魔法”；计算机只是做我们让它做的事情，不管它是否有意义。

> 承诺或分派事件的功能呢？很多“命令式语言”都提供了这些，但它们不再是命令式范式的一部分。语言进化，通常是向更好的方向发展，允许使用新的方法和技术。这是停止称它们为“命令式语言”的一个很好的理由，而是选择“通用语言”。

## 面向对象编程

面向对象编程是命令式编程的扩展。它为许多常用的模式提供了语法和名称。重点是将函数和数据分组到逻辑类中。

```
//non-OOP language
struct my_data {
    int a;
};
void my_data_init( my_data * m ) {
    m->a = 0;
}
void my_data_incr( my_data * m ) {
    m->a++;
}

//OOP language
class my_data {
    public int a;
    public my_data() {
        a = 0;
    }
    public incr() {
        a++;
    }
} 
```

语法扩展肯定是有帮助的，但它并不代表一种根本不同的编程方式。甚至在 C++问世之前，C 程序员就已经在用这种方式构建他们的代码了。这可能是范式的提炼，但没有根本的不同。我们仍然在给计算机相当明确的指令，告诉它如何组织数据和事情应该执行的顺序。

## 积木

命令性组件通过函数和变量相互链接。程序是通过对许多库的顺序调用和改变内存、磁盘或网络中的全局状态来创建的。我们可以在条件上循环，分支，甚至调用等待某件事情发生的函数。在代码中，所有发生的事情都是显式编写和排序的。

尽管可以严格使用这种范式编写完整的程序，但除了最小的脚本之外，这种范式不再常见。当与其他[范例](https://mortoray.com/topics/paradigms/)相结合来创建应用程序时，命令式编程可以很好地服务。事件连接一个 UI 应用程序，其中各个响应者是强制性编写的。声明性语言描述了服务器部署，但是各个规则是强制性的。主要具有功能计算的模拟包可以用一些命令性代码粘合在一起。