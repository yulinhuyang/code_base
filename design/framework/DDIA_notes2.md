

## 第10章 派生数据

整合不同系统是大型应用中最为关键的任务之一 P363

记录系统 P363

* 一个记录系统被称为真实数据系统，拥有数据的权威版本。

* 如果另一个系统与记录系统之间存在任何差异，那么以记录系统中的数据值（按照定义）为准

派生数据系统 P364

* 派生数据系统中的数据则是从另一个系统中获取已有数据并以某种方式进行转换或处理的结果

* 如果派生数据丢失，用户可以从原始数据源进行重建。

* 一个典型的例子是缓存

在线服务/系统 P367

* 服务等待库户请求或指令的到达，收到请求或指令时，服务试图尽快地处理它，并返回一个相应

* 响应时间和可用性是服务性能的主要衡量指标

批处理系统 P367

* 批处理系统接受大量的输入数据，运行一个作业来处理数据，并产生输出数据。

* 批处理作业的衡量标准通常是吞吐量

流处理系统 P368

* 介于在线与离线/批处理之间（有时称为近实时或近线处理）

著名的批处理算法MapReduce P368

* MapReduce值得深入理解，因为他清晰的解释了批处理为什么有用以及如何有用

nginx默认访问日志格式 P369

简单的日志分析 P369

* 利用nginx日志找出网站中前五个最受欢迎的网页

令人惊讶的是，使用awk、sed、grep、sort、uniq、和xargs的组合，可以在几分钟内完成许多数据分析任务，并且表现令人十分满意 P370

归并排序在磁盘上有良好的顺序访问模式 P371

通过管道将程序连接起来的想法成为如今的UNIX哲学，在开发人员和UNIX用户中逐渐变得流行的一些列设计原则 P372

**UNIX哲学 P372**

* 每个程序做好一件事。如果要做新的工作，则建立一个全新的程序，而不是通过增加新“特征”使旧程序变得更加复杂。

* 期待每个程序的数据成为另个尚未确定的程序的输入。不要将输出与无关信息混淆在一起。避免使用严格的表格状或二进制输入格式。不要使用交互式输入

* 尽早尝试设计和构建软件，甚至是操作系统，最在几周内完成。需要扔掉那些笨拙的部分时不要犹豫，并立即进行重建

* 优先使用工具来减轻编程任务，即使你不得不额外花费时间去构建工具，并缺预期在使用完成后会将其中一些工具扔掉

MapReduce与分布式文件系统 P375

MapReduce有点像分布在数千台机器上UNIX工具。MapReduce作业可以和UNIX进程相媲美：需要一个或多个输入，并产生一个或多个输出。P375

MapReduce作业执行流程 P376

要创建MapReduce作业，需要实现两个回调函数，即mapper和reducer P377

当mapper完成肚脐输入文件并写入经过排序的输出文件，MapReduce调度器就会通知reducer开始从mapper中获取输出文件。 P378

MapReduce工作流 P379

Mapreduce没有索引概念，至少不是通常意义上的索引。 P380

当给定一组文件作为MapReduce输入时，他读取所有文件的全部内容；数据库将其称为全表扫描。 P380

* 读取少量记录代价昂贵

* 分析查询场景下较为合理

各种join P384～P386

对比Hadoop和分布式数据库 P390

Haddop经常被用于实现ETL过程：来自事物处理系统的数据以某种原始形式转储到分布式文件系统中，然后编写MapReduce作业进行数据清理，将其转换为关系表单，并将其导入MPP数据仓库以进行分析。数据建模仍然会发生，打它位于一个单独步骤中，与数据收集是分离的。由于分布式文件系统支持任何格式编码的数据，所以这种解偶是可行的 P391

Hadoop生态系统包括可以随机访问的OLTP数据库，如HBse以及MPP模式的分析数据库，如Impala

HBase和Impala都不使用MapReduce，但都使用HDFS进行存储。尽管它们份温和处理数据的方法差异很大，但是可以共存并被集成到同一个系统中。 P392

与在线系统相比，批处理对故障的敏感度较低，因为如果遇到失败的任务，它们不会立即影响用户，而且总是可以重新运行

MapReduce被设计为容忍意外任务终止的原因：不是因为软件不可靠，而是因为任意种植进程的灵活性能够更好的利用集群资源

通过处理阶段明确的建模数据的系统被称为数据流引擎。 P395

像MapReduce一样，他们通过反复调用用户定义的函数在单个线程上一次处理一条记录。他们通过对数据进行分区来进行并行工作，将一个功能输出复制到网络上，成为另一个功能的输入。 P395

回到UNIX类比，我们看到MapReduce就像是将每个命令的输出写入临时文件，而数据流引擎看起来更像是UNIX管道。尤其Flink是围绕流水线执行的思想建立起来的，也就是将运算符的数据递增地传递给其他运算符，并且在开始处理之前不等待输入完成。 P398

批量同步并行模型 P399

批处理引擎正被用于日益广泛的算法领域的分布式执行。随着批处理系统获得更丰富的内置功能和高级声明式运算符，而MPP数据库也变得更具可编程性和灵活性，两者开始变得更加相似：最终，他们都是用于存储和处理数据的系统。 P402



* 在UNIX世界中，允许多个程序组合在一起的统一接口是文件和管道；

* 在MapReduce中，该接口是分布式文件系统。我们看到数据流引擎添加了自己的管道式数据传输机制，以避免在分布式文件系统中将中间状态实体化，而作业的出书输入和最终输出通常仍然是HDFS

* 分布式批处理框架需要解决的两个主要问题是：

	* 分区

	* 容错


## 第11章  流处理系统

一个可用的复杂系统总是从可用的简单系统演进而来。反过来这句话也是正确的：从零开始设计的复杂系统从来都用不了，也没办法把它变成可用。 P413

批处理的问题：输入的更改只会在一天之后的输出中反映出来，这对于许多没有耐心的用户来说太慢了。

为了减少这种延迟，可以更频繁的运行处理，即在每秒钟结束时（甚至是不间断地）处理每秒的数据，完全放弃固定的时间片，每当有事件就开始处理。这就是流处理背后的思想。 P414

向消费者通知新事件的常见方法是使用消息系统：生产者发送包含事件的消息。 P415

消息代理 P416

不管保留多长时间的消息，因为每个消息都被写入到磁盘，因此日志的吞吐量基本保持不变。这种行为与将消息保存在内存中，仅当队列变得过大时才将他们写入磁盘的穿系统系统相比，差异明显：当队列很短的时候这些系统是很快的，当开始写入磁盘时，会变得很慢，因此吞吐量取决于保留的历史记录数量。 P423

没有一个系统能够满足所有的数据存储、查询和处理请求。在实践中，大多数重要的应用程序都需要结合多种不同的技术来满足需求： P424

* 使用OLTP数据库来为用户请求提供服务

* 使用缓存来加速常见请求

* 使用全文索引处理搜索查询

* 使用数据仓库用于分析

每个技术都有自己的数据副本，以自己的表示方法存储，并且针对自己的设计目标而优化

日志压缩：存储引擎定期查找具有相同key的日志记录，丢弃所有的重复项，并且只保留每个key的最新更新。 P428

事件溯源 P429

事件溯源的哲学史小心的区分事件和命令。 P430

事务日志记录了对数据库所做的所有更改。 P432

* 高速追加是更改日志的唯一方法，从这个角度来看，数据库的内容保存了日志中最新的记录值缓存。

* 日志是事实。数据库是是日志子集的缓存。

* 该缓存子集恰好是来自日志的每个记录和索引值的最新值

不变事件的优势 p432

如果发生错误，通常不会删除或更改错误的数据，而是增加新的数据弥补这些错误

覆盖错误的数据将导致数据恢复变得更加的困难。

通过不可变事件的追加日志，诊断问题和从问题中恢复就要容易的多

出于分析的目的，历史记录也能提供有用的消息

缓慢变化的维度 P446

批处理框架可以比较容易实现容错：如果MapReduce作业中的任务失败，可以简单地在另一台机器上重新启动，并丢弃失败任务的输出。这种透明的重试是可能的，因为输入文件是不可变的。每个人物都将其输出写到HDFS上的单独文件，并且输出仅在任务成功完成时可见 P446

流处理的容错 P446

总结:
* 在某些方面，流处理与批处理非常相似，但是它是对无限（永不停止）的流而不是固定大小输入进行持续处理 P449

* 将数据表示为流为高效集成系统提供了更多的机会 P450



## 第12章  数据系统的未来


派生视图允许逐步演变。如果想重新构建数据集，无需采用高风险的陡然切换。而是可以在同一个基础数据上的两个独立派生视图来同时维护新老两种架构。

* 然后，逐步开始将少量用户迁移到新视图中，以测试其性能是否有错误，而大多数用户将继续路由到旧视图。

* 之后，逐渐增加访问新视图的用户比例，最终放弃旧视图

* 这种逐渐迁移的美妙之处在于，如果出现问题，每个阶段的过程都是可以轻易反转：你总是有一个工作系统可以回退 P 468

分拆数据库 P469

* 从最抽象的层面上理解，数据库，Hadoop和操作系统都提供了相同的功能：他们保存某些数据，并支持处理和查询 。

* 许多文件系统不能好很地处理包含一千万个小文件的目录，而包含一千万条记录的数据库完全是正常的。

创建一个索引

* 想想在关系型数据库中运行CREATED INDEX来创建新索引会发生什么。

* 数据库必须扫描表的一致性快照，挑选出所有被索引的字段值，对他们进行排序，然后得到索引。

* 接下来，必须处理从一致性快照创建以来所累计的写入操作（假设表在创建索引时未被锁定，所以写操作可能会继续）。

* 完成后，只要有事物写入表中，数据库就必须保持索引处于最新状态。

构建你并不需要的扩展规模是在浪费精力，可能会把你限制在一个不灵活的设计当中。实际上，这是在做过早优化 P473

将stream operatoe组合成数据流系统与微服务理念有很多相似的特性。但是，底层的通信机制差异很大 P478

* 前者是单向、异步的消息流

* 后者是同步的请求/响应交互

首先创建派生数据集，很可能是因为想在以后多次查询它即读路径：当有用户访问请求时，从派生数据集中读取数据，做些必要处理，然后返回处理后的结果以响应用户。 P479

许多数据存储支持的读写操作其实都是一个请求对应一个响应，但很少支持订阅更改，即一段时间内会主动返回一系列的响应。 P482

为了将写路径扩展到最终用户，我们需要从根本上重新思考构建这些系统的方式：从请求/响应交互转向发布/订阅数据流。我认为更具响应性的用户界面和更好的离线支持的优势是绝对值得尝试的。如果你正在设计数据系统，我希望你能够记住订阅更改这一方式，而不仅仅是查询当前的状态。 P482

Exactly-onece 执行操作 P485

TCP使用序列号来检测网络上是否有数据包丢失或重复，并最终确保数据包以正确的顺序接受。 P486

唯一性约束需要达成共识：如果有多个具有相同值的并发请求，系统需要决定接受哪一个操作，并根据违法约束拒绝其他操作 P489

达成这一共识的最常见的方式是将单一节点作为主节点，并负责作出所有的决定。 P489

日志机制可以确保所有消费者以相同的顺序查看消息，这种保证在形式上被称为全序关系广播，他等价于共识问题 P490

多分区请求处理 P491

事实证明，使用分区日志是可以实现同等的正确性，并却不需要原子提交 P491

* 账户A向账户B转账的请求由客户端赋予一个唯一的请求ID，基于该请求ID追加到对应的日志分区

* 流处理系统读取请求日志。对于每个请求消息，它发出两条输出消息：到付款人账户A的付款指令（按照A进行分区），以及到收款人账户B（按照B进行分区）的信用指令。原始的请求ID都包含在这两条消息中。

* 后续操作接受上述指令，并通过请求ID急性重复数据消除，将最后的更改应用于账户余额。

数据流系统可以保证派生数据的完整性，无需原子提交，线性化或跨分区的同步协调 P 495

虽然严格的唯一性约束要求时效性和协调性，但是只要整体上保证完整性，几十发生暂时约束破坏，可以时候进行修复，因此许多应用实际上采用宽松式的约束并没有问题 P495

算法囚笼 P501
