
## 第2章 命名

### 1.避免误导

"一组账号"别用accountList表示，List对程序员有特殊含义，可以用accountGroup、bunchOfAccounts、甚至是accounts

不使用区别较小的名称，ZYXControllerForEfficientHandlingOfStrings和ZYXControllerForEfficientStorageOfStrings难以辨别

不使用小写l、大写O作变量名，看起来像常量1、0

### 2.做有意义的区分

不以数字系列命名(a1、a2、a3)，按照真实含义命名

Product/ProductInfo/ProductData 意思无区别，只统一用一个

别写冗余的名字，变量名别带variable、表名别带table

### 3.使用可搜索的名称

单字母名称和数字常量很难在上下文中找出。名称长短应与其作用域大小相对应，越是频繁出现的变量名称得越容易搜索(越长)

### 4.命名时避免使用编码

把类型和作用域编码进名称里增加了解码负担。意味着新人除了了解代码逻辑之外，还需要学习这种编码语言。

别使用匈牙利语标记法(格式：[Prefix]-BaseTag-Name 其中BaseTag是数据类型的缩写，Name是变量名字)，纯属多余

不必用"m_"前缀来表明成员变量

接口和实现别在名称中编码。接口名IShapeFactory的前导"I"是废话。如果接口和实现必须选一个编码，宁可选实现，ShapeFactoryImp都比对接口名称编码来的好

### 5.类名、方法名

类名应当是名词或名词短语，方法名应当是动词或动词短语

### 6.每个概念用一个词

fetch、retrieve、get约定一个一直用即可

### 7.别用双关语

add方法一般语义是：根据两个值获得一个新的值。如果要把单个值加入到某个集合，用insert或append命名更好，这里用add就是双关语了。

### 8.添加有意义的语境

很少有名称能自我说明，需要用良好命名的类、函数、或者命名空间来放置名称，给读者提供语境，如果做不到的话，给名称添加前缀就是最后一招了。

## 第3章 函数

### 1.越短小越好

if/else/while语句的代码块应该只有一行，该行应该是一个函数调用语句。

函数的缩进层级不应该多于一层或两层。

### 2.只做一件事

如果函数只是做了该函数名下同一抽象层上的步骤，则函数只做了一件事。

要判断函数是否不止做了一件事，就是要看是否能再拆出一个函数。

### 3.每个函数一个抽象层级

### 4.switch语句

把switch埋在较低的抽象层级，一般可以放在抽象工厂底下，用于创建多态对象。

### 5.使用描述性的名称

函数越短小、功能越集中，就越便于取个好名字。

别害怕长名称，长而具有描述性的名称，要比短而令人费解的名称好，要比描述性的长注释好。

别害怕花时间取名字。

### 6.函数参数

参数越少越好，0参数最好，尽量避免用三个以上参数

参数越多，编写组合参数的测试用例就越困难

别用标识参数，向函数传入bool值是不好的，这意味着函数不止做一件事。可以将此函数拆成两个。

如果函数需要两个、三个或者三个以上参数，就说明其中一些参数应该封装成类了。

将参数的顺序编码进函数名，减轻记忆参数顺序的负担，例如,assertExpectedEqualsActual(expected, actual)

### 7.副作用(函数在正常工作任务之外对外部环境所施加的影响)

检查密码并且初始化session的方法 命名为checkPasswordAndInitializeSession而非checkPassword，即使违反单一职责原则也不要有副作用

避免使用"输出参数"，如果函数必须修改某种状态，就修改所属对象的状态吧

### 8.设置(写)和查询(读)分离

if(set("username", "unclebob")) { ... } 的含义模糊不清。应该改为:

	if (attributeExists("username")) { 
		setAttribute("username", "unclebob");
		...
	}

### 9.使用异常代替返回错误码

返回错误码会要求调用者立刻处理错误，从而引起深层次的嵌套结构:

	if (deletePate(page) == E_OK) {
		if (xxx() == E_OK) {
			if (yyy() == E_OK) {
				log();
			} else {
				log();
			}
		} else {
			log();
		}
	} else {
		log();
	}

使用异常机制:

	try {
		deletePage();
		xxx();
		yyy();
	} catch (Exception e) {
		log(e->getMessage());
	}

try/catch代码块丑陋不堪，所以最好把try和catch代码块的主体抽离出来，单独形成函数

	try {
		do();
	} catch (Exception e) {
		handle();
	}

函数只做一件事，错误处理就是一件事。如果关键字try在某个函数中存在，它就该是函数的第一个单词，而且catch代码块后面也不该有其他内容。

定义错误码的class需要添加新的错误码时，所有用到错误码class的其他class都得重新编译和部署。但如果使用异常而非错误码，新异常可以从异常class派生出来，无需重新编译或部署。这也是开放闭合原则(对扩展开放，对修改封闭)的范例。


### 10.不要写重复代码

重复是软件中一切邪恶的根源。当算法改变时需要修改多处地方

### 11.结构化编程

只要函数保持短小，偶尔出现的return、break、continue语句没有坏处，甚至还比单入单出原则更具有表达力。goto只有在大函数里才有道理，应该尽量避免使用。

### 12.如何写出这样的函数

并不需要一开始就按照这些规则写函数，没人做得到。想些什么就写什么，然后再打磨这些代码，按照这些规则组装函数。


## 第4章 注释

若编程语言足够有表现力，我们就不需要注释。 

注释总是一种失败。

代码在演化，注释却不总是随之变动。

不准确的注释比没注释坏的多。


### 1.用代码来阐述

创建一个与注释所言同一事物的函数即可

	// check to see if the employee is eligible for full benefits
	if ((employee.falgs & HOURLY_FLAG) && (employee.age > 65))

应替换为

	if (employee.isEligibleForFullBenefits())

### 2.好注释

法律信息

提供基本信息，如解释某个抽象方法的返回值

对意图的解释，反应了作者某个决定后面的意图

阐释。把某些晦涩的参数或者返回值的意义翻译成可读的形式(更好的方法是让它们自身变得足够清晰，但是类似标准库的代码我们无法修改):

	if (b.compareTo(a) == 1) //b > a

警示。// don't run unless you have some time to kill

TODO注释

放大 一些看似不合理之物 的重要性	


### 3.坏注释

自言自语

多余的注释。把逻辑在注释里写一遍不能比代码提供更多信息，读它不比读代码简单。一目了然的成员变量别加注释，显得很多余。

误导性注释

遵循规矩的注释。每个函数都加注释、每个变量都加注释是愚蠢的。

日志式注释。有了代码版本控制工具，不必在文件开头维护修改时间、修改人这类日志式的注释

能用函数或者变量表示就别用注释:

	// does the module from the global list <mod> 
	// depend on the subsystem we are part of?
	if (smodule.getDependSubsystems().contains(subSysMod.getSubSystem())

可以改为

	ArrayList moduleDependees = smodule.getDependSubsystems();
	String ourSubSystem = subSysMod.getSubSystem();
	if (moduleDependees.contains(ourSubSystem))
	
位置标记。标记多了会被我们忽略掉:

///////////////////// Actions //////////////////////////

右括号注释

	try {
		while () {
			if () {
				...
			} // if
			...
		} // while
		...
	} // try
	
如果你想标记右括号，其实应该做的是缩短函数

署名 /* add by rick */ 源代码控制工具会记住你，署名注释跟不上代码的演变。

注释掉的代码。会导致看到这段代码其他人不敢删除

信息过多。别在注释中添加有趣的历史话题或者无关的细节

没解释清楚的注释。注释的作用是解释未能自行解释的代码，如果注释本身还需要解释就太遗憾了。

短函数的函数头注释。为短函数选个好名字比函数头注释要好。

非公共API函数的javadoc/phpdoc注释。


## 第5章  代码格式

### 1.垂直格式

短文件比长文件更易于理解。平均200行，最多不超过500行的单个文件可以构造出色的系统

区隔: 封包声明、导入声明、每个函数之间，都用空白行分隔开，空白行下面标识着新的独立概念

靠近: 紧密相关的代码应该互相靠近，例如一个类里的属性之间别用空白行隔开

变量声明应尽可能靠近其使用位置：循环中的控制变量应该总是在循环语句中声明。

成员变量应该放在类的顶部声明，不要四处放置

如果某个函数调用了另外一个，就应该把它们放在一起。我们希望底层细节最后展现出来，不用沉溺于细节，所以调用者尽可能放在被调用者之上。

执行同一基础任务的几个函数应该放在一起。

### 2.水平格式

一行代码不必死守80字符的上限，偶尔到达100字符不超过120字符即可。

区隔与靠近: 空格强调左右两边的分割。赋值运算符两边加空格，函数名与左圆括号之间不加空格，乘法运算符在与加减法运算符组合时不用加空格(a*b - c)

不必水平对齐。例如声明一堆成员变量时，各行不用每一个单词都对齐。

短小的if、while、函数里最好也不要违反缩进规则，不要这样:

	if (xx == yy) z = 1;


 ## 第6章  对象和数据结构

对象:暴露行为(接口),隐藏数据(私有变量)

数据结构:没有明显的行为(接口),暴露数据。如DTO(Data Transfer Objects)、Entity

### 1.对象与数据结构的反对称性(参考书中代码清单6-5)

使用数据结构便于在不改动现在数据结构的前提下添加新函数；使用对象便于在不改动既有函数的前提下添加新类。

使用数据结构难以添加新数据结构，因为必须修改所有函数；使用对象难以添加新函数，因为必须修改所有类。

万物皆对象只是个传说，有时候我们也会在简单数据结构上做一些过程式的操作。

### 2.Demeter定律(最少知识原则)

模块不应该了解它所操作对象的内部情形

class C的方法f只应该调用以下对象的方法:
	C
	在方法f里创建的对象
	作为参数传递给方法f的对象
	C持有的对象
	
方法不应调用由任何函数返回的对象的方法。下面的代码违反了demeter定律:

	final String outputDir = ctxt.getOptions().getScratchDir().getAbsolutePath();

一个简单例子是，人可以命令一条狗行走（walk），但是不应该直接指挥狗的腿行走，应该由狗去指挥控制它的腿如何行走。

## 第7章  异常处理

异常处理很重要，但如果异常处理四处分散在代码中 导致逻辑模糊不清，它就是错的。

### 1.使用异常而不是返回错误码

如果使用错误码，调用者必须在函数返回时立刻处理错误，但这很容易被我们忘记。

错误码通常会导致嵌套if else

### 2.先写try-catch语句

当编写可能会抛异常的代码时，先写好try-catch再往里堆逻辑

### 3.使用unchecked exception(java独有)

### 4.在catch里尽可能的记录错误信息，记录失败的操作以及失败的类型。

### 5.根据调用者的需要 定义不同的异常处理类

同一个try里catch多个不同exception，但是catch处理的事(打日志等)是一致的，可以考虑用函数打包一下这个异常处理，针对不同异常仅需throw成同一个异常而不做任何处理，
在外层catch时统一处理(打日志等)。如果仅想捕获一部分异常而放过其他异常，就使用不同的函数打包这个异常处理。

### 6.特例模式: 创建一个类来处理特例。

	try {
		MealExpendses expenses = expenseRepotDAO.getMeals(employee.getID());
		m_total += expenses.getTotal();// 如果消耗了餐食，计入总额
	} catch (MealExpensesNotFound e) {
		m_total += getMealPeDiem();// 如果没消耗，将员工补贴计入总额
	}
	
异常打断了业务逻辑。可以在getMeals()里不抛异常，而是在没消耗餐食的时候返回一个特殊的MealExpense对象(PerdiemMealExpense)，复写getTotal()方法。

	MealExpendses expenses = expenseRepotDAO.getMeals(employee.getID());
	m_total += expenses.getTotal();

	publc class PerDiemMealExpenses implements MealExpenses {
		public int getTotal() {
			//return xxx; //返回员工补贴
		}
	}
	
### 7.别返回null值

返回null值只要一处没检查null，应用程序就会失败

当想返回null值的时候，可以试试抛出异常，或者返回特例模式的对象。

### 8.别传递null值

在方法中传递null值是一种糟糕的做法，应该尽量避免。

在方法里用if或assert过滤null值参数，但是还是会出现运行时错误，没有良好的办法对付调动者意外传入的null值，恰当的做法就是禁止传入null值。

##  第8章 边界

将第三方代码干净利落地整合进自己的代码中

1.避免公共API返回边界接口，或者将边界接口作为参数传递给API。将边界保留在近亲类中。

2.不要在生产代码中试验新东西，而是编写测试来理解第三方代码。

3.避免我们的代码过多地了解第三方代码中的特定信息。

## 第9章 单元测试

### 1.TDD(Test-driven development)三定律

First Law: You may not write production code until you have written a failing unit test.

Second Law: You may not write more of a unit test than is sufficient to fail, and not compiling is failing.

Third Law: You may not write more production code than is sufficient to pass the currently failing test.

### 2.保持测试整洁

脏测试等同于没测试，测试代码越脏 生产代码越难修改。

测试代码和生产代码一样重要。

整洁的测试代码最应具有的要素是：整洁性。测试代码中不要有大量重复代码的调用。

### 3.每个测试一个断言

每个测试函数有且仅有一个断言语句。

每个测试函数中只测试一个概念。

### 4.整洁的测试依赖于FIRST规则

fast: 测试代码应该能够快速运行，因为我们需要频繁运行它。

independent: 测试应该相互独立，某个测试不应该依赖上一个测试的结果，测试可以以任何顺序进行。

repeatable: 测试应可以在任何环境中通过

self-validating: 测试应该有bool值输出，不应通过查看日志来确认测试结果，不应手工对比两个文本文件确认测试结果。

timely: 及时编写测试代码。单元测试应该在生产代码之前编写，否则生产代码会变得难以测试。

## 第10章  类

### 1.类的结构组织(顺序):

	公共静态常量

	私有静态变量

	私有实体变量

	公共函数

	私有工具函数

### 2.类应该短小

对于函数我们计算代码行数衡量大小，对于类我们使用权责来衡量。

类的名称应当描述其权责。类的命名是判断类长度的第一个手段，如果无法为某个类命以准确的名称，这个类就太长了。类名包含模糊的词汇，如Processor、Manager、Super，这种现象就说明有不恰当的*权责聚集情况。

单一权责原则: 类或者模块应该有一个权责——只有一条修改的理由(A class should have only one reason to change.)。

系统应该由许多短小的类而不是少量巨大的类组成。

类应该只有少量的实体变量，如果一个类中每个实体变量都被每个方法所使用，则说明该类具有最大的内聚性。创建最大化的内聚类不太现实，但是应该以高内聚为目标，内聚性越高说明类中的方法和变量互相依赖、互相结合形成一个逻辑整体。

保持内聚性就会得到许多短小的类。如果你想把一个大函数的某一小部分拆解成单独的函数，拆解出的函数使用了大函数中的4个变量，不必将4个变量作为参数传递到新函数里，仅需将这4个变量提升为大函数所在类的实体变量，但是这么做却因为实体变量的增多而丧失了类的内聚性，更好多做法是让这4个变量拆出来，拥有自己的类。将大函数拆解成小函数往往是将类拆分为小类的时机。

### 3.为修改而组织(参考书中代码清单10-9、10-10)



类应当对扩展开放，对修改封闭(开放闭合原则)

在理想系统中，我们通过扩展系统而非修改现有代码来添加新特性。


## 第11章 系统

### 1.将系统的构造与使用分开

将全部构造过程搬迁到main或者被称之为main的模块中，涉及系统其余部分时，假设所有对象都已经正确构造。

有时应用程序也需要负责确定何时创建对象，我们可以使用抽象工厂模式让应用自行控制何时创建对象，但构造能力在工厂实现类里，与使用部分分开。

依赖注入(DI)，控制反转(IoC)是分离构造与使用的强大机制。


## 第12章  emergent design

四条规矩帮助你创建优良的设计

**1.运行所有测试**

紧耦合的代码难以编写测试，测试写的越多，就越会遵循依赖注入之类的规则，使代码加减少耦合。

测试消除了对清理代码就会破坏代码的恐惧。

**2.消除重复**

两个方法提取共性到新方法中，新方法分解到另外的类里，从而提升其可见性。

模板方法模式是消除重复的通用技巧

	// 原始逻辑
	public class VacationPolicy() {
		public void accrueUSDivisionVacation() {
			//do x;
			//do US y;
			//do z;
		}
		public void accrueEUDivisionVacation() {
			//do x;
			//do EU y;
			//do z;
		}
	}

	// 模板方法模式重构之后
	abstract public class VacationPolicy {
		public void accrueVacation() {
			x();
			y();
			z();
		}
		private void x() {
			//do x;
		}
		abstract protected void y() {
		
		}
		private void z() {
			//do z;
		}
	}
	public class USVacationPolicy extends VacationPolicy {
		protected void y() {
			//do US y;
		}
	}
	public class EUVacationPolicy extends VacationPolicy {
		protected void y() {
			//do EU y;
		}
	}


**3.表达意图**

作者把代码写的越清晰，其他人理解代码就越快。

太多时候我们深入于要解决的问题中，写出能工作的代码之后，就转移到下一个问题上，没有下足功夫调整代码让后来者易于阅读。多少尊重一下我们的手艺，花一点点时间在每个函数和类上。

**4.尽可能少的类和方法**

为了保持类和函数的短小，我们可能会早出太多细小的类和方法。

类和方法数量太多，有时是由毫无意义的教条主义导致的。

5.以上4条规则优先级依次递减。重要的是测试、消除重复、表达意图。


## 第13章  并发编程

1.防御并发代码问题的原则与技巧

遵循单一职责原则。分离并发代码与非并发代码

限制临界区数量、限制对共享数据的访问。

避免使用共享数据，使用对象的副本。

线程尽可能地独立，不与其他线程共享数据。










