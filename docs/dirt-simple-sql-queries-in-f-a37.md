# F#中极其简单的 SQL 查询

> 原文：<https://dev.to/kspeakman/dirt-simple-sql-queries-in-f-a37>

SQL 是我们许多人竭尽全力试图抽象出来的东西。存储库模式、ORM 和[类型提供者](https://docs.microsoft.com/en-us/dotnet/fsharp/tutorials/type-providers/accessing-a-sql-database)是 SQL 的抽象例子。但是每一种都有不适合每一种用例的权衡。

今天，我提出了一些不太抽象的东西，更多的是一组帮助函数。这也有利弊，但它非常适合我的需求。看你怎么想。

## 使用起来是什么感觉

它不会试图对你隐藏 SQL，而只是在你使用 SQL 时试图避开你。下面是定义查询的方法。

```
open QueryHelpers

let listCourses offset limit =
    sql
        """
        SELECT CourseId, CourseName
          FROM Course
        OFFSET @Offset ROWS
         FETCH
          NEXT @Limit ROWS ONLY
        ;
        """
        [
            p "Offset" offset
            p "Limit" limit
        ] 
```

Enter fullscreen mode Exit fullscreen mode

上例中的辅助函数是`sql`和`p`。实际上，`p`(参数的简称)只是一个制作元组和装箱<sup>的快捷方式📌</sup>参数值。

> **📌装箱参数值**
> 
> *装箱意味着将某物转换成类型`obj`。对于像`int`这样的原始类型，将其转换为`obj`会有内存/性能损失。(因为它必须包装在引用类型中，并由垃圾收集器 IIRC 分配。)*
> 
> 在撰写本文时，ADO.NET 需要装箱参数值才能使用它们。所以这样做没有坏处，而且可以防止我们的 F#代码中出现类型推断问题。

下面是运行查询的方式。

```
type Course =
    {
        CourseId : int
        CourseName : string
    }

let query = listCourses request.Offset request.Limit
let coursesAsync = Sql.query<Course> connectString query

// coursesAsync is Async<Course array> 
```

Enter fullscreen mode Exit fullscreen mode

这里，`Sql.query<Course>`是一个运行查询并将每个数据行转换成一个`Course`对象的函数。与大多数映射器一样，属性类型和名称必须与返回的列相匹配。

请注意，查询是与执行查询的代码分开创建的。这对于执行更新的查询特别方便。我可以提前设置多次写操作，甚至是从单独的代码片段，然后在同一个事务中稍后执行它们。

```
let deactivateCourse courseId =
    sql "UPDATE ..." [ p "CourseId" courseId ]

let cancelCourseRegistrations courseId =
    sql "DELETE ..." [ p "CourseId" courseId ]

...

let patches =
    [
        deactivateCourse courseId
        cancelCourseRegistrations courseId
    ]

...

Sql.writeBatch connectString patches

// returns Async<unit> 
```

Enter fullscreen mode Exit fullscreen mode

## 实现它

下面是上述用法的完整的 40 行实现。

```
namespace Foo.MsSql

open System
open System.Data.SqlClient

type SqlQuery =
    {
        Query : string
        Parameters : (string * obj) list
    }

module QueryHelpers =

    let p name value =
        (name, box value)

    let sql query parameters =
        {
            Query = query
            Parameters = parameters
        }

module Sql =

    open Dapper  // adds QueryAsync and ExecuteAsync

    let query<'T> connectString q =
        async {
            use connection = new SqlConnection(connectString)
            do! connection.OpenAsync() |> Async.AwaitTask
            let! result =
                connection.QueryAsync<'T>(q.Query, dict q.Parameters)
                    |> Async.AwaitTask
            return Array.ofSeq result
        }

    let writeBatch connectString writes =
        async {
            use connection = new SqlConnection(connectString)
            do! connection.OpenAsync() |> Async.AwaitTask
            use transaction = connection.BeginTransaction()
            for write in writes do
                do!
                    connection.ExecuteAsync
                        (write.Query, dict write.Parameters, transaction)
                        |> Async.AwaitTask
                        |> Async.Ignore
            transaction.Commit()
        } 
```

Enter fullscreen mode Exit fullscreen mode

> Dapper 负责将行映射到对象的艰苦工作。Dapper 太棒了。

这段代码只是一个起点，但它对于添加新功能来说是相当开放的。例如，随着时间的推移，我添加了以下内容，我可能会在以后的帖子中介绍:

*   从查询中返回多个数据集
*   更多设置，如命令超时
*   通过将写入合并到一个查询*中进行批处理，与上面不同的是，只对数据库*进行一次往返
*   大型结果集处理*返回一个序列，该序列在迭代*之前不会读入内存
*   Postgres 版本
*   参数类型*主要为 Postgres jsonb 类型，其中 Npgsql 没有正确推断*

我不得不为`option`类型添加 [Dapper 类型处理程序。但是有了它，我可以将空 DB 字段映射到 F#选项，并避免空处理。](https://stackoverflow.com/questions/42797288/dapper-column-to-f-option-property)

## 那呢...？

### 只获取 1 行

因为数据是以数组的形式返回的，所以如果存在第一行，可以使用 F# Array 函数如`Array.tryHead`来获取第一行。

### 获取标量

Dapper 支持将行转换成类似`int`的原语。所以你可以使用`Sql.query<int>`，这将返回每行第一列的`int`值。然后，您可以使用数组函数只获取第一行。

## 这能让你走多远？

我使用了一些原则，这些原则(加上我提到的附加内容)满足了我所有的 SQL 需求。

首先，我把决定和副作用分开。所以我的代码[返回消息](https://dev.to/kspeakman/message-based-api-part-2-67c),表示作为用户请求的结果发生了什么决策和事件。后来，这些决定变成了副作用，比如保存到数据库或发送电子邮件。

第二，我用多种方法对数据建模。第一个模型是其他模型所基于的权威模型(真理的来源)。这可能是一个事件日志或规范化的关系表。这是大多数人在使用关系数据库时止步的地方。然而，我还创建了一些模型，这些模型是为特定的目的量身定做的。

例如，我将一门课程的数据(有几层嵌套的对象)存储为一个 JSON 对象，因为对于添加/编辑/查看场景，这样加载和保存很方便。我有一个单独的 CourseSearch 模型(表),其中包含一些相同的数据，但作为关系列。这些列用于筛选、排序和填充文本搜索索引，使用户能够执行全文搜索。这两种模型都有其特定的用途。这是在数据级别的**关注点分离。但是，如果我试图将两者都压缩到同一个大型模型中，将会很难工作。因为我总是不得不**同时从两个不同的维度考虑巨型模型，以便做出正确的选择**。我的空间受限的大脑无法持续做到这一点。**

第三，作为一个规则，我没有既改变数据又返回数据的查询。非此即彼。这样我就不会因为意料之外的副作用而引入错误。因此，我不能使用自动生成的 id。但最后证明这是好的。因为它们使重试等其他功能变得复杂。一旦单个服务器无法满足您的需求，无论如何都必须放弃(或[外包](https://www.slideshare.net/davegardnerisme/unique-id-generation-in-distributed-systems))。

由于上述原因，我的查询保持相对简单，并针对特定的目的。所以一个简单的 SQL API 就满足了我的所有需求。

> 对于每个想要的改变，让改变变得容易(警告:这可能很难)，然后让改变变得容易
> 
> *   肯特·贝克