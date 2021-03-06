### Chapter09:通用编程

#### 57 将局部变量的作用域最小化 

1.第一次使用前定义。 

2.优先使用增强for循环，而不是while或者Iterator.可减少犯错。 

3.方法内容指责单一，短小。

要使局部变量的作用域最小化，最有力的方法就是在第一次使用它的地方声明。

几乎每个局部变量的声明都应该包含一个初始化的表达式。

for循环优于while循环是因为for循环的变量作用域在循环体中，所以不容易出现“剪切-粘贴”错误。

另一个优势就是for循环更加简短可读。

将局部变量的作用域最小化的方法是使方法小而集中

#### 58  for-each循环优先于传统的for循环

增强for循环易读并且不易出错。

三种情况无法使用for-each循环

- 过滤——遍历集合并删除选定元素
- 转换——遍历列表或数组，并取代它部分或者全部的元素值。
- 平行迭代——如果需要并行的遍历多个集合，就需要显示的控制迭代器或者索引变量

#### 59 了解和使用类库

JDK源码，Guava必备，不多说了。

#### 60 如果需要精确的答案，请避免使用float和double

如对于金额计算，使用BigDecimal进行小数运算，int/long可根据金额大小选择，使用分做单位进行四舍五入运算。

关于浮点数的原理可参考： [程序员必知之浮点数运算原理详解](https://links.jianshu.com/go?to=https%3A%2F%2Fblog.csdn.net%2Ftercel_zhang%2Farticle%2Fdetails%2F52537726) 

#### 61 基本类型优先于装箱基本类型


1.包装类型除了拥有值，还有引用。原始类型更加简单性能高。如下面的代码由于不停的拆箱封箱可导致性能问题：

```java
 public static void main(String[] args) {
        Long sum = 0L;
        for (long i = 0;i<Integer.MAX_VALUE;i++){
//不停的拆箱封箱
            sum += i;
        }
        System.out.println(sum);
    }
```

2.原始类型有默认值，而包装类型初始值为null，进行运算时可能会报NullPointerException。

 3.原始类型可使用==比较，包装类型的==总是false。

- 基本类型和装箱基本类型有三个主要区别
  - 基本类型只有值，装箱基本类型则具有与它们的值不同的同一性。
  - 基本类型只有功能完备的值，而每个装箱基本类型除了它对应基本类型的所有功能值之外，还有个非功能值null
  - 基本类型通常比装箱基本类型更节省时间和空间。
- 对装箱基本类型运用==操作符几乎总是错误的。
- 当在一项操作中，混合使用基本类型和装箱基本类型时，装箱基本类型就会自动拆箱，这种情况无一例外。
- 什么时候使用装箱基本类型呢？
  - 最为集合中的元素、键和值，你无法将基本类型放在集合中。
  - 在参数化类型中，必须使用装箱基本类型作为类型参数。
  - 在进行反射的方法调用时，必须使用装箱基本类型。
- 自动装箱减少了使用装箱基本类型的繁琐性，但是并没有减少它的风险。



#### 62 如果其他类型更适合，则尽量避免使用字符串

1.枚举对象时最好用enum。 

2.聚合对象用聚合的方式展示，如用私有静态类表示元素。而非字符串连接。

3.基本类型如int，不要用String表示。

- 字符串不适合代替其他的值类型。
- 字符串不适合代替枚举类型。
- 字符串不适合代替聚集类型。
- 字符串不适合代替能力表（capabilities）

#### 63 了解字符串连接的性能

慎重使用“+”连接字符串** 

"+"连接字符串复杂度是n^2,因为字符串是不可变的，每次都需要copy。使用`StringBuilder`代替，它的复杂度为线性的。或者使用字符数组，或者只调用一次连接字符串。

#### 64 通过接口引用对象  

对象使用接口类引用，而不是实现类引用

对象使用接口类引用会更加灵活。如果找不到合适的接口类引用，尽量选择可提供功能的父类实现。

如果有合适的接口类型存在，那么对于参数、返回值、变量和域来说，就都应该使用接口类型进行声明。

它会使程序更加灵活。

如果没有合适的接口存在，完全可以用类而不是接口来引用对象。

#### 65 接口优先于反射机制  

对于反射对象，优先使用接口或父类引用，而不是反射类的引用

- 反射机制能够获得Constructor、Method、Field实例，并通过调用实例上的方法狗仔地城类的实例、调用底层类的方法、并访问底层类中的域。当然这样也需要付出代价。
  - 丧失了编译时类型检查的好处。包括异常检查。
  - 执行反射访问所需要的代码非常笨拙和冗长。
  - 性能损失。反射方法调用比普通方法慢了许多。
- 通常，普通应用程序在运行时不应该以反射方式访问对象。
- 如果只是以非常有限的形式使用反射机制，虽然也要付出少许代价，但是可以获得许多好处。
- 如果你编写的程序必须要与编译时未知的类一起工作，如果有可能，就应该仅仅使用反射机制来实例化对象。

#### 66 谨慎地使用本地方法

 native方法相比Java普通方法是不安全的，也更加依赖于平台，不容易使用，bug可能导致整个应用失败。

谨慎地使用本地方法（Java Native Interface）允许Java应用程序可以调用本地方法，也就是调用本地程序设计语言，比如C或者C++来编写的特殊方法。

本地方法的三种用途

- 它们提供了“访问特定于平台的机制”的能力
- 提供了访问遗留代码库的能力，从而访问遗留数据。
- 可以通过本地语言，编写应用程序中注重性能的部分，以提高系统的性能

#### 67 谨慎地进行优化 

 提到设计的时候考虑好架构性能，不要图快。配合性能检测工具，优化算法等。

- 要努力编写好的程序而不是快的程序。
- 努力避免那些限制性能的设计决策。
- 要考虑API设计决策的性能后果。
- 为获得好的性能而对API进行包装，这是一种非常不好的想法。
- 在每次试图做优化之前和之后，要对性能进行测量。
- 再多的底层优化也无法弥补算法的选择不当。

#### 68 遵守普遍接受的命名惯例

Package/module: 全小写（com.junit.jupiter） 

Class/Interface: 驼峰命名（Stream,HashMap） 

Method/Filed: 首字母小写，驼峰命名（remove.getCrc） 

Constant Filed: 全大写，单词用下划线隔开（MIN_VALUE） 

Local Variable: 首字母小写，驼峰命名（i,houseName） 

Type Parameter（类型参数）: 大写单字母（T,E）

- T表示任意的类型
- E表示集合的元素类型
- K和V表示映射的键和值类型
- X表示异常。
- 任何类型的序列可以是T、U、V或者T1、T2、T3
  - 对于返回boolean值的方法，齐明明往往以单词“is”开头。

### Chapter10:异常

#### 69 针对异常的情况才使用异常   


异常会阻止JVM的一些优化，影响性能。异常就是用来处理异常的。

#### 70 对可恢复的情况使用受检异常，对编程错误使用运行时异常

不要使用errors，errors是JVM表明资源缺乏等导致无法运行用的。定义所有未检查的异常应该继承RuntimeException。

错误往往被JVM保留用于表示资源不足、约束失败，或者其他使程序无法执行的条件，由于这已经是个几乎被普遍接受的惯例，因此最好不要在实现任何新的Error子类。所以你事先的所有未受检的跑出结构都应该是RuntimeException的子类，不管是直接的还是间接的。

受检异常往往指明了可恢复的条件，所以，对于这样的异常，提供一些辅助的方法尤其重要，通过这些方法，调用者可以获得一些有助于恢复的信息。

#### 71 避免不必要地使用受检异常  

有些异常需要抛给调用者解决。

#### 72 优先使用标准的异常 

大家都懂的异常，简单明了。如NullPointerException。

#### 73 抛出与抽象对应的异常 

```java
            try {
                ... //调用其他低级方法
                
            }catch (LowerLevelException e){
                throw new HigherLevelException(...);
            }
```

#### 74 每个方法抛出的所有异常都要建立文档 

始终要单独地生命受检的异常，并且利用Javadoc的@throws标记，准确地记录下抛出每个异常的条件。

使用Javadoc的@throws标签记录下一个方法可能抛出的每个未受捡异常，但是不要使用throws关键字将未受检的异常包含在方法的声明中。

如果一个类中的许多方法处于同样的原因而抛出同一个异常，在该类的文档注释中对这个异常建立文档，这是可以接受的，

#### 75 在细节消息中包含失败-捕获信息 

 如所有导致这个异常的参数，但也不能包含敏感信息，如密码等。

#### 76 努力使失败保持原子性

类似回滚机制，当异常发生时，应该保证对象被调用前的状态，或者文档详细说明。

- 失败的方法调用应该使对象保持在被调用之前的状态。
- 四种方式保持失败的原子性
  - 设计一个不可变对象
  - 调整计算处理过程的顺序，是的任何可能会失败的计算部分都在对象状态被修改之前发生。
  - 第三种或的失败原子性的办法就是编写一段恢复代码（recovery code）
  - 最后一种在对象的一份临时拷贝上操作，当操作完成后再用临时拷贝中的结果代替对象的内容。
  - 一般而言，作为方法规范的一部分，产生的任何异常都应该让对象保持在该方法调用之前的状态

#### 77 不要忽略异常 

catch完啥也不干是不允许的，否则就要说明为啥要这么干。

### Chapter11:并发

#### 78 同步访问共享的可变数据  

 Java内存模型（JMM）通过happens-before原则，synchronized等关键字定义了Java线程之间的可见性，原子性，顺序性等问题。同步访问的保证有以下方式：

1. synchronized使用时，保证进入同步的条件也是同步的，也就是说与同步有关的读写操作都是同步的。 

2. 第1点可以优化为进入同步的条件必须保证可见性，如双重检查实现单例懒加载方式时，静态单例对象用volatile修饰。

3. 类似j.u.c包中的同步实现，使用volatile+cas(乐观锁原理-版本控制)操作可实现lock-free且线程安全的同步。

#### 79 避免过度同步 

1. 同步方法中不要调用外来方法，如可重写的方法，观察者方法，因为这些方法可能产生异常，死锁等问题导致同步失败。

2. 如果无法实现高性能的并发同步，将同步交给客户端去做，并写好文档说明。对于静态变量，必须自己实现同步。自实现同步时可考虑`lock splitting,lock stripping,nonblocking（无锁）技术`。

#### 80 executor、task和stream优先于线程

优先使用线程池(ThreadPoolExecutor/ForkJoinPool)，任务（Runnable/Callable,ForkJoinTask)而不是多个单线程

池化技术加任务队列能够提高效率，节省资源，更好的抽象等。可参考： [聊聊并发（八）——Fork/Join 框架介绍](https://links.jianshu.com/go?to=https%3A%2F%2Fwww.infoq.cn%2Farticle%2Ffork-join-introduction) [线程池与ForkJoin比较](https://links.jianshu.com/go?to=https%3A%2F%2Fwww.jdon.com%2Fperformance%2Fthreadpool-forkjoin.html) [Java8的CompletableFuture](https://links.jianshu.com/go?to=https%3A%2F%2Fwww.jdon.com%2Fidea%2Fjava%2Fcompletablefuture.html) 

#### 81 并发工具优先于wait和notify 

既然正确地使用wait和notify比较困难，就应该用更高级的并发工具来代替

java.util.concurrent中更高级的工具分成三类

- Executor Framework
- 并发集合（Concurrent Collection）
  - 并发集合中不可能排除并发活动；将他锁定没有什么作用，只会是程序速度变慢。
- 同步器（Synchronizer）

对于间歇式的定时，始终应该优先使用System.nanoTime而不是System.currentTimeMills，System.nanoTime更加准确也更加精确，他不收系统的实时时钟的调整所影响

一般情况下，你应该有限使用notifyAll，而不是notify。如果使用notify，请一定小心，以确保程序的活性。

#### 82 线程安全性的文档化

文档要说明方法的线程安全级别，如：

`不可变`（String/Long/BigInteger）,

`无条件线程安全`(AtomicLong/ConcurrentHashMap),

`有条件线程安全`（Collections.synchronized包装类需要额外保证自身迭代器的同步，否则可能fail-fast）,

`线程不安全`（ArrayList/HashMap),

`违反线程安全的`（修改静态变量时没有同步）。

 有条件线程安全需要写明什么时候需要额外同步，且应该获取什么锁进行同步。 无条件线程安全的类可以在同步方法上使用不可变私有对象锁代替类锁，可保护子类或客户端的同步方法。同时增加自身后续实现的灵活性。

#### 83 慎用延迟初始化

 懒加载适用于初始化对象开销大，且不一定会初始化该对象的场景。否则使用正常初始化更好。对于静态变量，可使用静态私有holder类来加载。对于成员变量，可使用双重检查+volatile实现。

对于延迟初始化，最好的建议“除非绝对必要，否则就不要这么做”，虽然降低了初始化类或者创建实例的开销，却增加了访问被延迟初始化的域的开销

在大多数情况下，正常初始化要优先于延迟初始化。

如果出于性能的考虑而需要对静态域使用延迟初始化，就使用lazy initialization holder class模式。

如果出于性能的考虑而需要对实例域使用延迟初始化，就是用双重检查模式（double-check idiom）

#### 84 不要依赖于线程调度器 

如果某一个程序不能工作，是因为某些线程无法像其他线程那样获得足够的CPU时间，那么，不要企图通过调用Thread.yield来“修正”该程序。这样的程序是不可移植的，因为不同的JVM对其实现不同。Thread.yield没有可测试的语义。

线程优先级是Java平台上最不可移植的特性了。

Thread.yield的唯一用途是在测试期间人为地增加程序的并发性。

使用Thread.sleep(1)代替Thread.yield来进行并发测试。

### Chapter12:序列化

首先介绍下Java原生序列化的原理：

Java原生序列化使用`ObjectInputStream.readObject`和`ObjectOutputStream.writeObject`来序列化和反序列化对象。对象必须实现`Serializable`接口，同时对象也可以自实现序列化方法`readObject`和反序列化方法`writeObject`定义对象成员变量的序列化和反序列化方式。此外对象还可实现`writeReplace`,`readResolve`,`serialVersionUID`。 

`writeReplace`主要用来定义对象具体序列化的内容，可对原来按照`readObject`方法序列化的内容进行修改替换。

 `readResolve`主要用来定义对象反序列化时的内容，可对原来按照`writeObject`方法反序列化的内容进行修改替换。 

 `serialVersionUID`是类的序列化版本号，保证能将二进制流反序列化为内存中存在的类的对象。如果不主动生成的话，在序列化反序列化过程中根据类信息动态生成，耗时且类结构不灵活。

#### 85 其他方法优先于Java序列化 

优先使用其他序列化方式代替Java自身序列化

#### 86 谨慎地实现Serializable接口

1.因为一旦使用了，以后就不好去掉了。本来就不建议使用原生序列化方式。 

2.增加产生bug和安全漏洞的风险。 

3.增加新版本发布的测试负担。

#### 87 考虑使用自定义序列化的格式

如果使用了原生序列化方式，就考虑自实现序列化对象的`readObject`和`writeObject`方法，因为Java实现的太笨重了，序列化所有东西，并且耗时不可控，可能导致安全和异常等问题。自己实现相对会减少这些风险。

#### 88 保护性地编写readObject方法

其实还是降低安全风险等问题，如变量的完整校验，不要将序列化方法重写，交给子类不可控等问题。

#### 89 对于实例控制，枚举类型优先于readResolve

对于单例对象，优先使用`枚举`而不是`readResolve`方法

 why: 枚举类对象的序列化和反序列化方式是Java语言规范的，不是由用户实现的。枚举类对象是天生的单例对象。 自实现`readResolve`方法实现单例的话，需要做很多额外工作，如将所有成员变量用`transient`修饰等，此外仍然会拥有Java序列化的缺点。

 #### 90 考虑用序列化代理代替序列化实例

也就是自实现`writeReplace`方法，好处是安全。

**服务提供者框架有三个重要的组件**

1. 服务接口——提供者实现

2. 提供者注册API——是系统用来注册实现，让客户端访问他们。

3. 服务访问API——客户端用来获取服务的实例。

4. 可选的第四个组件为服务提供者接口——负责创建其服务实现的实例。
