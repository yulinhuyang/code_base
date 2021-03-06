# 第六部分：系统考虑

## 第27章 程序规模对构建的影响

随着项目规模的增加，下面这些活动的工作量增长超过线性:
* 交流
* 计划
* 管理
* 需求分析
* 系统功能设计
* 接口设计和规格说明
* 架构
* 集成
* 消除缺陷
* 系统测试
* 文档生成

在社交场合，活动越正式，你所穿的服装就会越不舒服（高跟鞋、领带等等）。在软件幵发领域里，项目越正规，你不得不写的文件的数量也会越多，用于确认你已经完成了自己的工作

要点
* 随着项目规模的扩大，交流需要加以支持◊大多数方法论的关键点都在于减少交流中的问题，而一项方法论的存亡关键也应取决于它能否促进交流。
* 在其他条件都相等的时候，大项目的生产率会低于小项目。
* 在其他条件都相等的时候，大项目的每千行代码错误率会高于小项目。
* 在小项目里的一些看起来“理当如此”的活动在大项目中必须仔细地计划。随着项目规模扩大，构建活动的主导地位逐渐降低。
* 放大轻量级的方法论要好于缩小重量级的方法论。最有效的办法是使用“适量级”方法论。


## 第28章  管理构建

核对表（配置管理）

概要
* 你的软件配S管理计划是否用于帮助程序员，并能将额外负担降至最低？
* 你的软件配S管理方法是否避免了对项目的过度控制？
* 你是否将一些变更请求聚成一组？无论采用非正式的方法（如创建一份未决更改的列表）还是更加系统的方法（如设立变更控制委员会）。
* 你系统地评估了每一项提交的更改对成本、计划和质量的影响吗？
* 你是否把重大的变更看做是需求分析还不够完备的螯报信号？

工具
* 你用版本控制软件来促进配置管理吗？
* 你用版本控制软件来减少团队工作中的协调问题吗？

备份
* 你定期地备份项目中的所有资料吗？
* 你定期地把项目备份数据转移到off-site storage里了吗？
* 所有的资料，包栝源代码、文档、阁表和重要的笔记都得到备份了吗？
* 你测试过备份与恢复的过程吗？

要点
* 好的编码实践可以通过“贯彻标准”或者“使用更为灵活的方法”来达到。
* 配置管理，如果应用得当，会使程序员的工作变得更加轻松。特别包括变更控制。
* 好的软件评估是一项重大挑战。成功的关键包括采用多种方法、随着项目的开展而修缮评估结果，以及很好地利用数据来创建评估等。
* 度量是构建管理成功的关键。你可以采取措施度量项目的任何方面，而这要比根本不度量好得多。准确的度量是制定准确的进度表、质t控制和改进开发过程的关键。
* 程序员和管理人员都是人，在把他们当人看的时候工作得最好。

## 第29章 集成

术语“集成”指的是一种软件开发行为：将一些独立的软件组件组合为一个完整系统。
 
核对表（集成）

集成策略
* 该策略是否指明了集成子系统、类、子程序时应该采用的最优顺序？
* 集成的顺序是否与构建顺序协调，以便在适当的时候准备好供集成的类？
* 该策略是否易于诊断缺陷？
* 该策略是否使脚手架最少？
* 所选的策略是否好于其他方式？
* 组件之间的接冂是否有明确定义？（定义接凵不是集成的任务，但要验证这些接口的定义是否明确。）

Dailybuild与冒烟测试
* 项目是否经常build一一理想情况下，每天build一次一一一以支持增量集成？
* 每次build后是否都运行冒烟测试，让你知道这个build能否工作？
* 你是否已使build和冒烟测试自动进行？
* 开发人员是否频繁地checkin他们的代码一一一一一两次checkin之间最多间隔一两天？
* 冒烟测试是否与代码同步更新，随代码发展而发展？
* 破坏build是罕见事件吗？
* 是否在有压力的情况下，也对软件进行build和冒烟测试？

要点
* 构建的先后次序和集成的步骤会影响设计、编码、测试各类的顺序。一个经过充分思考的集成顺序能减少测试的工作量，并使调试变容易。
* 增量集成有若干变型，而且一一一除非项目是微不足道的一．一任何一种形式的增量集成都比阶段式集成好。
* 针对每个特定的项目，最佳的集成步骤通常是自顶向下、自底向上、风险导向及其他集成方法的某种组合。不型集成和直分块集成通常都能工作得很好。
* dailybuild能减少集成的问题，提升开发人员的士气，并提供非常有用的项目管理信息。


## 第30章  编程工具

你至少能在以下领域找到高质量的程序库
* 容器类
* 信用卡交易服务（电子商务服务）
* 跨平台的开发工具，你可以让编写的代码在Windows、AppleMacintosh、XWindowSystem上都能运行一一一只需为各个环境重新编译一次源代码
* 数据压缩工具
* 数据结构与算法
* 数据库操作工具与数据文件操控工具
* 图解/图示／图表工具
* 图像工具
* 许可证管理器
* 数学运算
* 网络与互联网通信工具
* 报表生成器与报表查询@portque引生成器
* 安全与加密工具
* 电子表格和数据网格工具
* 文本与拼写工具
* 语音、电话与传真工具
下列功能特性和工具有助于你进行有效的测试
* 自动测试框架，如JUnit、NUnit、CppUnit等
* 自动化的测试生成器
* 测试用例的记录和回放工具
* 覆盖率监视器（逻辑分析器和执行剖测器）
* 符号调试器
* 系统扰动器（内存填充工具、内存“抖动”工具、选择性的内存失效的工具、内存访问检查器）
* Diff工具（比较数据文件、截获的输出、屏幕图像等）
* 脚手架
* 缺陷注入工具
* 缺陷跟踪软件

核对表（编程工具）
* 你有一套有效的工具集吗？
* 你的IDE集成了：源代码控制、bul测试／除错工具，以及其他有用的功能吗？
* 你有能自动进行常用的重构操作的工具吗？
* 你是否使用版本控制工具，对源代码、内容、需求、设计、项目计划及其他的项目构件进行管理？
* 如果你正面对超大型的项目，你是否使用了数据字典或者其他“包含系统中使用的各个类的权威描述"的中央知识库。
* 当可以用到代码库时，你是否考虑用它来代替“编写定制代码”？
* 你是否充分利用了交互式除错器？
* 你是否使用make或其他“依赖关系控制软件”，用来高效并可靠地build程序？
* 你的测试环境包含有自动化的测试框架、自动测试生成器、覆盖率监视器、系统扰动器、diff工具，以及缺陷跟踪软件吗？
* 你有没有制造过定制工具一一能满足特定项目的需求的那种，特别是能自动执行重复任务的工具？
* 总而言之，你的工作环境有没有从“充足的工具支援”中获益？

要点
* 程序员有时会在长达数年的时间里忽视某些最强大的工具，之后才发现并使用之。好的工具能让你的日子过得安逸得多。
* 下面这些工具己经可用了：编辑、分析代码质量、重构、版本控制、除错、测试、代码调整。
* 你能打造许多自己用的专用工具。
* 好的工具能减少软件开发中最单调乏味的工作的量，但它不能消除对“编程”的需要，虽然它会持续地重塑“编程”的含义。

# 第七部分：软件工艺 

## 第31章  布局与风格

格式化的基本原理指出，好的布局凸现程序的逻辑结构。

对于C++，请仔细组织源文件中内容的次序为：
1.	文件的描述性注释
2.	#include文件行
3.	在多个类里使用的常量定义（如果文件里有多个类）
4.	在多个类里使用的枚举（如果文件里有多个类）
5.	宏函数定义
6.	在多个类里使用的类型定义（如果文件里有多个类）
7.	导入的全局变量和函数
8.	导出的全局变量和函数
9.	本文件私用的变量和函数
10.	各个类，包括各个类中的常量定义、枚举以及类型定义

核对表（布局）
一般问题
* 格式化主要是为了展现代码的逻辑结构吗？
* 你的布局方案能统一地运用吗？
* 你的布局方案能让代码易于维护吗？
* 你的布局方案是否有利于代码的可读性？

控制结够的布局
* 你的代码中避免begin-end对或{}的双重缩进了吗？
* 相邻的块之间用空行分隔了吗？
* 对复杂表达式格式化时考虑到可读性吗？
* 对只有一条语句的块的布局始终如一吗？
* 语句与其他控制结构的格式化保持一致了吗？
* 对goto语句的格式化是否让其显眼了呢？

单条语司的布局
* 为逻辑表达式、数组下标和子程序参数的可读性而使用空格了吗？
* 不完整的语句在行末是以明显有错的方式结束吗？
* 后续行按照标准数目缩进了吗？
* 每行顶多只有一条语句吗？
* 所写的每个语句都没有副作用吗？
* 每行顶多只声明一个数据吗？

注释的布局
* 注释与其所注释的代码的缩进量相同吗？
* 注释的风格便于维护吗？

子程序的布局
* 你对每个子程序参数的格式化方式便于看懂、修改、注释吗？
* 采用空行分隔子程序的各部分了吗？

类、文件和程席的布局
* 多数类和文件之间是一一对应的关系吗？
* 如果文件内有多个类，各类中的子程序按类分组了吗？各类都清楚标识了
* 文件中的子程序用空行清楚地分开了吗？
* 在没有更好的组织形式的场合，所有子程序都按字母顺序排列了吗？

要点
* 可视化布局的首要任务是指明代码的逻辑组织。评估该任务是否实现的指标包括准确性、一致性、易读性和易维护性。外表悦目比起其他指标是最不重要的。然而，如果其他指标都达到了，代码又质量好，那么布局效果看上去也会不错。
* VisualBasic具有纯代码块风格，而Java的传统做法就是使用纯块风格，所以若用这些语言编程，就请使用纯代码块风格。C++中，模拟纯代码块或者begin-end块边界都行之有效。
* 结构化代码有其自身目的。始终如一地沿用某个习惯而少来创新。不能持久的布局规范只会损害可读性。
* 布局的很多方面涉及信仰问题。应试着将客观需要和主观偏好区分开来。
* 定出明确的指标，在此基础上冉讨论风格参数的选择。

## 第32章 自说明代码

核对表（自说明代码）
* 你的类接口体现出某种一致的抽象吗？
* 你的类名有意义吗，能表明其中心意图吗？
* 你的类接凵对于如何使用该类显而易见吗？
* 你的类接囗能抽象到不需考虑其实现过程吗？能把类看成是黑盒吗？

子程序
* 你的每个子程序名都能准确地指示该子程序确切干些什么吗？
* 你的各子程序的任务明确吗？
* 若各子程序中自成一体后更有用，你都将其各自独立出来了吗？
* 每个子程序的接口都清晰明了吗？

数据名
* 类型名描述有助于说明数据声明吗？
* 你的变量名有意义吗？
* 变量只用在其名字所代表意义的场合吗？
* 你的循环变量名能给出更多信息，而不是i、j、k之类的吗？
* 你用了名字有意义的枚举类型，而非临时拼凑的标识或者布尔变量吗？
* 用具名常量代替神秘数值或者字符串了吗？
* 你的命名规范能区分类型名、枚举类型、具名常量、局部变量、类变量以及全局变量吗？

数据组织
* 你根据编程清晰的需要，使用了额外变量来提高清晰度吗？
* 你对某变量的引用集中吗？
* 数据类型简化到了最低复杂度吗？
* 你是通过抽象访问子程序（抽象数据类型）来访问复杂数据吗？

控制
* 代码中的正常执行路径很清晰吗？
* 相关语句放在一起了吗？
* 相对独立的语句组打包为子程序了吗？
* 正常情况的处理位于“语句之后，而非在else子句中吗？
* 控制结构简单明了，以使复杂度最低吗？
* 每个循环完成且仅完成一个功能，是像定义良好的子程序那么做吗？
* 嵌套层次是最少吗？
* 逻辑表达式通过额外添加布尔变量、布尔函数和功能表简化了吗？

布局
* 程序的布局能表现出其逻辑结构吗？
设计
* 代码直截了当吗？是不是避免了自作聪明或新花样？
* 实现细节尽可能隐藏了吗？
* 程序是尽可能采用问题领域的术语，而非按照计算机科学或者编程语言的术语编写的吗？

核对表（好的注释技术）
一般问题
* 别人拿起你的代码就能立刻明白其意吗？
* 你的注释是在解释代码用意，或概括代码在做什么，而非简单重复代码
* 采用了伪代码编程法来减少注释时间吗？
* 是重写有玄机的代码，而非为其做注释吗？
* 你的注释能否同代码一起更新？
* 注释清楚正确吗？
* 你的注释风格便于修改注释吗？

语旬和段落
* 代码避免用行尾注释了吗？
* 注释是着力说明为什么而非怎么样吗？
* 注释为将要阅读代码的人们做好准备了吗？
* 每个注释都其用处吗？删掉抑或改进了多余的、无关紧要的或随意的注释没有？
* 是否注释了代码的非常规之处？
* 避免使用用缩略语了吗？
* 主次注释区别明显吗？
* 含错代码和未公开的代码特性有注释吗？

数据声明
* 对数据声明的注释说明了数值单位吗？
* 数值数据的取值范围注释出来了吗？
* 注释出了编码含义吗？
* 对输入数据的限制有注释吗？
* 对位标志做注释了吗？
* 在各全局变量声明的地方对其做注释了吗？
* 各全局变量是通过命名规范、注释（或者两者兼用）来标识其意义吗？
* 神秘数值是否以具名常量或变量代替，而非只是标注之？

控制结构
* 控制语句都注释了吗？
* 冗长或者复杂的控制结构结尾处有注释吗？抑或可能的话，简化之从而省去注释了吗？

子程序
* 各子程序的意图都注释出了吗？
* 子程序的其他有关情况（诸如输入输出数据、接口假设、局限性、纠错、全局效果和算法来源）都注释出来了吗？

文件、类和程序
* 程序有简短的文档（就像在“以书本为范例”中说明的那样）给出程序组织的概述吗？
* 每个文件的用途都有说明吗？
* 作者姓名、email及电话号码在代码清单中都有吗？

要点
* 该不该注释是个需要认真对待的问题。差劲的注释只会浪费时间，帮倒忙；好的注释才有价值。
+源代码应当含有程序大部分的关键信息。只要程序依然在用，源代码比其他资料都能保持更新，故而将重要信息融入代码是很有用处的。
* 好代码本身就是最好的说明。如果代码太糟，需要大量注释，应先试着改进代码，直至无须过多注释为止。
* 注释应说出代码无法说出的东西一一一例如概述或用意等信息。
* 有的注释风格需要许多重复性劳动，应舍弃之，改用易于维护的注释风格。


## 第33章 个人性格(personal character)

很多好的编程做法都能减轻你的大脑灰质细胞（指脑力）的负担。
* 将系统“分解”，是为了使之易于理解（“设计的层次”）。
* 进行审查、评审和测试正是为了减少人为失误。如果你从不犯错，就无须复审自己的软件。但要知道，人的智力是有限的，所以应和他人沟通，来提高软件质量。
* 将子程序编写得短小，以减轻大脑负荷。
* 基于问题而不是低层实现细节来编程，从而减少工作量。
* 通过各种各样的规范，将思路从相对繁琐的编程事务中解放出来。

编程生涯成熟的部分标志就是发展出一种不屈不挠的诚实感。通常表现为以下几个方面：
* 不是高手时不假装是高手。
* 乐于承认错误。
* 力图理解编译器的警告，而非弃之不理。
* 透彻理解自己的程序，而不要只是编译看看能否运行。
* 提供实际的状况报告。
* 提供现实的进度方案，在上司面前坚持自己的意见。
如果你还没有对某个程序花费至少一个月的时间一一一天工作16小时，其余8小时也睡得不安稳，老是梦到它，为解决“最后错误”连熬几夜一一尔就算没有编过真正复杂的程序，你也不会感受到编程中激动人心的东西。—EdwardYourdon 。这种对编程的痴迷简直是胡闹，儿乎注定会失败。彻夜编程让你感觉像是世上最好的程序员，却要花几个星期去纠正你在短暂辉煌时埋下的失误。可以热爱编程，但热情不能代替熟练的能力，请想明白什么更重要。

要点
* 人的个性对其编程能力有直接影响
* 最有关系的性格微：谦虚、求知欲、诚实、创造性和纪律、以及高明的偷懒
* 程序员高手的性格与田飞无关而任何事都与个人发展相关
* 出乎意料的是，小聪明、经验、坚持和疯狂既有助，也有害
* 很多程序员不愿意主动吸收新知识和技术，只依靠工作是偶尔接触新的信息。如果你能抽出少量时间阅读和学习编程知识，要不了多久就能鹤立鸡群
* 好性格与培养正确的习惯关系甚大。要成为接触的程序员，先要养成良好的习惯，其它自然输掉渠成。

## 第34章 软件工艺的话题

* 在架构层将系统划分为多个子系统，以便让思绪在某段时间内能专注于系统的一小部分。
* 仔细定义类接口，从而可以忽略类内部的工作机理。
* 保持类接口的抽象性，从而不必记住不必要的细节。
* 避免全局变量，因为它会大大增加总是需要兼顾的代码比例。
* 避免深层次的继承，因为这样会耗费很大精力。
* 避免深度嵌套的循环或条件判断，因为它们都能用简单的控制结构取代，后者占用较少的大脑资源。
* 别用goto，因为它们引入了非顺序执行，多数人都不容易弄懂。
* 小心定义错误处理的方法，不要滥用不同的错误处理技术。
* 以系统的观点对待内置的异常机制，后者会成为非线性的控制结构。异常如果不受约束地使用，会和一样难以理解。
* 不要让类过度膨胀，以致于占据整个程序。
* 子程序应保持短小。
* 使用清楚、不言自明的变量名，从而大脑不必费力记住诸如"x代表账号下标，〕代表顾客下标，还是另有它意？”之类的细节。
* 传递给子程序的参数数目应尽量少。更重要的是，只传递保持子程序接口抽象所必需的参数。
* 用规范和约定来使大脑从记忆不同代码段的随意性、偶然性差异中解脱出来。
* 只要有可能，一般情况下应避免“偶然性困难”

计算机不关心你的代码是否好读。它更善于读二进制指令，而非高级语言的代码。编写可读性好的代码，是为了便于别人看懂。可读性对程序的以下方面都有正面影响：

* 可理解性
* 容易复查
* 错误率
* 调试
* 可修改性
* 开发时间
* 上述因素之综合外在质量

深入一门语言去编程，不浮于表面

要点
* 编程的主要目的之一是管理复杂性
* 编程过程对最终产品有深远影响
* 合作开发要求团队成员之间进行广泛沟通，甚于同计算机的交互：而单人开发则是自我交流，其次才是计算机
* 编程规范一旦滥用，只会雪上加霜：使用得当则能为开发环境带来良好机制，有助于管理复杂性和相互沟通
* 编程应基于问题域而非解决方案，这样便于复杂性管理
* 注意警告信息，将其作为编程的疑点，因为编程几乎是纯粹的智力活动
* 开发时迭代次数越多，产品的质量越好
* 墨守成规的方法有悖于高质量的软件开发。请将编程工具箱中填满各种编程工具，不断提高自己挑选合适工具的能力。




