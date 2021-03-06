
[JavaCore](https://github.com/dunwu/javacore)

[Java核心 卷一笔记](https://blog.csdn.net/qq_39326472/category_8572091.html)

### 1  @Override 

是伪代码,表示重写(当然不写也可以)，不过写上有如下好处:

1、可以当注释用,方便阅读；

2、编译器可以给你验证@Override下面的方法名是否是你父类中所有的，如果没有则报错

### 2  equals 和 == 的区别 

equals 是方法，而 == 是操作符；

对于基本类型的变量来说（如 short、 int、 long、 float、 double），只能使用 == ，因为这些基本类型的变量没有 equals 方法。对于基本类型变量的比较，使用 == 比较， 一般比较的是它们的值。

对于引用类型的变量来说（例如 String 类）才有 equals 方法，因为 String 继承了 Object 类， equals 是 Object 类的通用方法。对于该类型对象的比较，默认情况下，也就是没有复写 Object 类的 equals 方法，使用 == 和 equals 比较是一样效果的，都是比较的是它们在内存中的存放地址。但是对于某些类来说，为了满足自身业务需求，可能存在equals 方法被复写的情况，这时使用 equals 方法比较需要看具体的情况，例如 String 类，使用 equals 方法会比较它们的值；

https://www.jianshu.com/p/9cbed9f33a4d

### 3 对象传递 

在Java中，当对象作为参数传递时，实际上传递的是一份“引用的拷贝”。

### 4 实现反射 

java 获取反射机制三种方式

1. new对象 

2. 路径

3. 类名

public class Main {

	public static void main(String[] args) throws ClassNotFoundException {
		// 方式一、new对象
		Student student = new Student();
		Class classObj1 = student.getClass();
		System.out.println(classObj1.getName());

		// 方式二、路径-相对路径
		Class classObj2 = Class.forName("com.aop8.reflect.Student");
		System.out.println(classObj2.getName());

		// 方式三、类名
		Class classObj3 = Student.class;
		System.out.println(classObj3.getName());
	}
}


### 5 extend implement 区别 

[抽象类和接口的区别已经变了](https://zhuanlan.zhihu.com/p/75513356)

子类继承抽象类通过 extends , 单继承

	public abstract class A {}
	public class B extends A {}


抽象类实现接口通过 implements , 多实现，接口继承接口通过 extends

	public interface A {}
	public interface B {}

	public interface C extends A {}

	public class D implements B,C {}

**实例化**

抽象类和接口均不能实例化

抽象类可以有构造方法，接口不能有构造方法

	public abstract class A {
	 public A () {}
	}


**属性**

接口中定义属性只能是 (public)静态常量

	public interface A {
	 //默认(public static final) String A="ABC";
	 String A = "ABC";
	}
	
抽象类中可以定义有任意变量常量

//任意访问修饰符的变量及常量

	public abstract class A {
		 private String a = "a";
		 boolean b = true;
		 public char c = 'a';
		 protected int d = 2;
		 public static final int e = 1;
	}

**设计**

1. 抽象类是对一组类的共同特征进行抽象 ，是子类的模板（is-a）

2. 接口是对行为的抽象，是一种行为的规范和约束 (like-a)

**类优先**

同时extend implement 时，类优先


### 6  Cloneable clone

copy:  浅拷贝

clone: 浅克隆和深克隆之分。

浅克隆: 如果对象包含子对象的引用，拷贝域就包括相同子对象的引用。

深克隆： 深克隆将原型对象的所有引用对象也复制一份给克隆对象。

浅克隆：覆盖Object类的clone()方法可以实现浅克隆。

深克隆：

先对对象进行序列化，紧接着马上反序列化出；

先调用super.clone()方法克隆出一个新对象来，然后在子类的clone()方法中手动给克隆出来的非基本数据类型（引用类型）赋值，比如ArrayList的clone()方法。


***Cloneable接口***

（1）此类实现了Cloneable接口，以指示Object的clone()方法可以合法地对该类实例进行按字段复制

（2）如果在没有实现Cloneable接口的实例上调用Object的clone()方法，则会导致抛出CloneNotSupporteddException

（3）按照惯例，实现此接口的类应该使用公共方法重写Object的clone()方法，Object的clone()方法是一个受保护的方法

***Object的clone()方法***

创建并返回此对象的一个副本。对于任何对象x，表达式：

（1）x.clone() != x为true

（2）x.clone().getClass() == x.getClass()为true

（3）x.clone().equals(x)一般情况下为true，但这并不是必须要满足的要求


### 7 lambda 表达式

**带参变量的表达式**

	(parameters) -> expression

	或

	(parameters) ->{ statements; }

	eg：
	
	// 3. 接受2个参数(数字),并返回他们的差值  
	(x, y) -> x – y  

	// 4. 接收2个int型整数,返回他们的和  
	(int x, int y) -> x + y  

	// 5. 接受一个 string 对象,并在控制台打印,不返回任何值(看起来像是返回void)  
	(String s) -> System.out.print(s)

lambda 表达式中捕获的变量必须实际上是最终变量( effectivelyfinal）。最终变量是指，这个变量初始化之后就不会再为它赋新值。

lambda 表达式的体与嵌套块有相同的作用域。

对于只有一个抽象方法的接口， 需要这种接口的对象时， 就可以提供一个 lambda 表达式。这种接口称为函数式接口。

使用lambda 表达式的重点是延迟执行 deferred execution

**java常用函数式接口：**

Consumer< T>:消费型接口

接口方法 void accept(T t)：参数类型是T，无返回值

Supplier< T>供给型接口

接口方法 T get()：参数类型是T，返回T类型参数

Function<T,R>函数型接口</T,R>

接口方法R apply(T)：对类型T参数操作，返回R类型参数

Predicate< T>段言型接口

接口方法 boolean test（T t）：对类型T进行条件筛选操作，返回boolean

### 8 闭包

在JAVA中，闭包是通过“接口+内部类”实现，JAVA的内部类也可以有匿名内部类。

Lambda表达式也是闭包。

### 9 内部类

[内部类详解](https://www.cnblogs.com/dolphin0520/p/3811445.html)

Java的内部类可分为Inner Class（成员内部类、局部内部类）、Anonymous Class和Static Nested Class三种：

Inner Class和Anonymous Class本质上是相同的，都必须依附于Outer Class的实例，即隐含地持有Outer.this实例，并拥有Outer Class的private访问权限；

Static Nested Class是独立类，但拥有Outer Class的private访问权限。

**特殊语法：** 

	OwterC/ass.this    表示外围类引用

	if (TalkingClock.this,beep) Toolkit.getDefaultToolkitO.beep();

编写内部对象的构造器

	outerObject.n&H InnerClass{construction parameters)

	ActionListener listener = this.new TimePrinterO;
	
	TalkingClock jabberer = new Ta1kingClock(1000, true);
	
	TalkingOock.TiiePrinter listener = jabberer.new TimePrinterO；
	
在外围类的作用域之外，可以这样引用内部类：OuterClass.InnerClass	
	
**成员内部类**

成员内部类是最普通的内部类，它的定义为位于另一个类的内部

外部访问：

外部类.this.成员变量

外部类.this.成员方法

	class Circle {
	    double radius = 0;

	    public Circle(double radius) {
		this.radius = radius;
	    }

	    class Draw {     //内部类
		public void drawSahpe() {
		    System.out.println("drawshape");
		}
	    }
	}

成员内部类是依附外部类而存在的，也就是说，如果要创建成员内部类的对象，前提是必须存在一个外部类的对象

        //第一种方式：
        Outter outter = new Outter();
        Outter.Inner inner = outter.new Inner();  //必须通过Outter对象来创建
         
        //第二种方式：
        Outter.Inner inner1 = outter.getInnerInstance();

**局部内部类**

局部内部类是定义在一个方法或者一个作用域里面的类，它和成员内部类的区别在于局部内部类的访问仅限于方法内或者该作用域内。

```java
	class People{
	    public People() {

	    }
	}

	class Man{
	    public Man(){

	    }

	    public People getWoman(){
		class Woman extends People{   //局部内部类
		    int age =0;
		}
		return new Woman();
	    }
	}
```	


**匿名内部类**

匿名内部类应该是平时我们编写代码时用得最多的，在编写事件监听的代码时使用匿名内部类不但方便，而且使代码更加容易维护

```java
scan_bt.setOnClickListener(new OnClickListener() {
             
            @Override
            public void onClick(View v) {
                // TODO Auto-generated method stub
            }
        });
         
        history_bt.setOnClickListener(new OnClickListener() {
             
            @Override
            public void onClick(View v) {
                // TODO Auto-generated method stub  
            }
        });
```
	
**静态内部类**

```java
	public class Main {
	    public static void main(String[] args) {
		Outer.StaticNested sn = new Outer.StaticNested();
		sn.hello();
	    }
	}

	class Outer {
	    private static String NAME = "OUTER";

	    private String name;

	    Outer(String name) {
		this.name = name;
	    }

	    static class StaticNested {
		void hello() {
		    System.out.println("Hello, " + Outer.NAME);
		}
	    }
	}
```

### 10 反编译

	java reflection.ReflectionTest irmerClass.lilkingClock\STimePrinter

	javap -private innerClass.W kingClock\STimePrinte


### 11 动态代理

动态代理（以下称代理），利用Java的反射技术(Java Reflection)，在运行时创建一个实现某些给定接口的新类（也称“动态代理类”）及其实例（对象）

可以在运行期动态创建某个interface的实例。

```java
	import java.lang.reflect.InvocationHandler;
	import java.lang.reflect.Method;
	import java.lang.reflect.Proxy;

	public class Main {
	    public static void main(String[] args) {
		InvocationHandler handler = new InvocationHandler() {
		    @Override
		    public Object invoke(Object proxy, Method method, Object[] args) throws Throwable {
			System.out.println(method);
			if (method.getName().equals("morning")) {
			    System.out.println("Good morning, " + args[0]);
			}
			return null;
		    }
		};
		Hello hello = (Hello) Proxy.newProxyInstance(
		    Hello.class.getClassLoader(), // 传入ClassLoader
		    new Class[] { Hello.class }, // 传入要实现的接口
		    handler); // 传入处理调用方法的InvocationHandler
		hello.morning("Bob");
	    }
	}

	interface Hello {
	    void morning(String name);
	}
```



在运行期动态创建一个interface实例的方法如下：

1 定义一个InvocationHandler实例，它负责实现接口的方法调用；

2 通过Proxy.newProxyInstance()创建interface实例，它需要3个参数：

	使用的ClassLoader，通常就是接口类的ClassLoader；
	
	需要实现的接口数组，至少需要传入一个接口进去；
	
	用来处理接口方法调用的InvocationHandler实例。
	
3 将返回的Object强制转型为接口。

动态代理实际上是JVM在运行期动态创建class字节码并加载的过程，它并没有什么黑魔法

解决特定问题：一个接口的实现在编译时无法知道，需要在运行时才能实现

实现某些设计模式：适配器(Adapter)或修饰器(Decorator)

面向切面编程：如AOP in Spring


### 12 异常 断言 日志

应该捕获那些知道如何处理的异常，而将那些不知道怎样处理的异常继续进行传递

不管是否有异常被捕获，finally 子句中的代码都被执行。

try 语句可以只有finally 子句，而没有catch 子句

强烈建议解搞合try/catch 和try/finally 语句块

```java
	InputStrean in = . . .;
	try
	{
		try
		{
			code that might throw exceptions
		}
		finally
		{
			in.doseO;
		}
	}
	catch (IOException e)
	{
		show error message
	}
```

带资源的try 语句（try-with-resources) 的最简形式为：

```java
	try (Resource res = . . .)
	{
		work with res
	}
	
	try (Scanner in = new Scanner(new FileInputStream(7usr/share/dict/words")), "UTF-8")
	{
		while (in.hasNextO)
		System.out.pri ntl n(in.next()) ;
	}
```

try 块退出时，会自动调用res.doseO。

这个块正常退出时，或者存在一个异常时，都会调用inxloseO 方法，就好像使用了finally 块一样。

还可以指定多个资源: 例如：

```java
	try (Scanner in = new Scanne「(new FileInputStream('7usr/share/dict/words"). "UTF-8"):
	PrintWriter out = new Pri ntWriter("out.txt"))
	{
		while (in.hasNextO)
		out.pri ntl n(i n.next().toUpperCaseO);
	}
```

堆栈轨迹： 调用 Throwable 类的 printStackTrace 方法访问堆栈轨迹的文本描述信息。

使用 getStackTrace 方法， 它会得到 StackTraceElement 对象的一个数组， 可以在你的程序中分析这个对象数组。

静态的 Thread.getAllStackTrace 方法， 它可以产生所有线程的堆栈轨迹。

在出错的地方抛出一个EmptyStackException异常要比在后面抛出一个NullPointerException 异常更好


	assert 条件：表达式；

断言检查只用于开发和测阶段。

断言是一种测试和调试阶段所使用的战术性工具; 而日志记录是一种在程序的整个生命周期都可以使用的策略性工具。

**日志**

使用全局日志记录器（global logger) 并调用其info 方法：

Logger.getClobal 0,info("File->Open menu item selected");

如果在适当的地方（如main 开始）调用  

Logger.getClobal ().setLevel (Level .OFF);

将会取消所有的日志。

处理器  ----> 过滤器  ---->格式化器

**调试技巧**

每一个类中放置一个单独的main 方法。这样就可以对每一个类进行单元测试。

JUnit是一个非常常见的单元测试框架。

利用Throwable 类提供的printStackTmce 方法，可以从任何一个异常对象中获得堆栈情况。

-Xlint 选项告诉编译器对一些普遍容易出现的代码问题进行检査。

使用jmap实用工具获得一个堆的转储，其中显示了堆中的每个对象。

使用-Xprof 标志运行Java 虚拟机，就会运行一个基本的剖析器来跟踪那些代码中经常被调用的方法。

jconsole 的图形工具，可以用于显示虚拟机性能的统计结果

### 13  泛型

[Java中的泛型方法](https://www.cnblogs.com/iyangyuan/archive/2013/04/09/3011274.html)

[java 泛型详解](https://blog.csdn.net/s10461/article/details/53941091)

从表面上看，Java 的泛型类类似于C++ 的模板类。唯一明显的不同是Java 没有专用的template 关键字。

泛型只在编译阶段有效。

在编译之后程序会采取去泛型化的措施。也就是说Java中的泛型，只在编译阶段有效。在编译过程中，正确检验泛型结果后，会将泛型的相关信息擦出，并且在对象进入和离开方法的边界处添加类型检查和类型转换的方法。也就是说，泛型信息不会进入到运行时阶段。


泛型类：

	public class Pair<T, U> { . . . }

在Java 库中，使用变量E 表示集合的元素类型，K 和V 分别表示表的关键字与值的类型。T ( 需要时还可以用临近的字母U 和S) 表示“ 任意类型”

泛型方法：

	class ArrayAlg
	{
		public static <T> T getMiddle(T... a)
		{
		    return a[a.length / 2];
		}
	}

泛型接口： 

	//定义一个泛型接口
	public interface Generator<T> {
	    public T next();
	}
	
泛型类，是在实例化类的时候指明泛型的具体类型；泛型方法，是在调用方法的时候指明泛型的具体类型 。

类型限制：  public static <T extends Coiparab1e> T a) . . .

多个通配符限制：     T extends Comparable & Serializable

	 public static <T extends Comparable〉Pair<T> minmax(T[] a)

通配符： 类型通配符一般是使用?代替具体的类型参数。例如 List<?> 在逻辑上是List<String>,List<Integer> 等所有List<具体类型实参>的父类。

	public class GenericTest {

	    public static void main(String[] args) {
		List<String> name = new ArrayList<String>();
		name.add("icon");
		getData(name);
	   }

	   public static void getData(List<?> data) {
	      System.out.println("data :" + data.get(0));
	   }

子类型限定： ? extends Employee

超类型限定： ? super Manager



java 类型擦除, C++ 中每个模板的实例化产生不同的类型，这一现象称为“ 模板代码膨账”


### 14  集合

让类库规模小且易于学习，而不希望像C++ 的“ 标准模版库” （S卩STL) 那样复杂，但却又希望能够得到STL 率先推出的“ 泛型算法” 所具有的优点。

将接口（interface) 与实现(implementation) 分离。

#### 队列

队列通常有两种实现方式：一种是使用循环数组；另一种是使用链表。

集合类的基本接口是Collection 接口

	public interface Collection<b
	{
		boolean add(E element);
		Iterator<E> iteratorQ；
	}

Iterator 接口包含4 个方法：

	public interface Iterator<E>
	{
		E next();
		boolean hasNext();
		void remove();
		default void forEachRemaining(Consumer<? super E> action);
	}


	for (String element : c)
	{
		do something with element
	}


删除两个相邻元素： 调用remove之前必须调用next

	it.remove(); 
	it.next()；
	it.remove(); 

#### List

所有链表实际上都是双向链接的(doubly linked) ——即每个结点还存放着指向前驱结点的引用

Add 方法在迭代器位置之前添加一个新对象。

可以根据需要给容器附加许多的迭代器，但是这些迭代器只能读取列表。另外，再单独附加一个既能读又能写的迭代器

contains：检测某个元素是否出现在链表

get ：访问某个特定元素，get 方法做了微小的优化：如果索引大于 size() / 2 就从列表尾端开始搜索元素。

add 方法只依赖于迭代器的位置， 而 remove 方法依赖于迭代器的状态。

set 方法用一个新元素取代调用 next 或 previous 方法返回的上一个元素。

列表迭代器接口：nextlndex 方法返回下一次调用 next 方法时返回元素的整数索引；previouslndex 方法返回下一次调用 previous 方法时 返回元素的整数索引。

有两种访问元素的协议：一种是用迭代器， 另一种是用get和 set 方法随机地访问每个元素。后者不适用于链表， 但对数组却很有用。

**Vector与 ArrayList 区别**

Vector类的所有方法都是同步的。可以由两个线程安全地访问一个Vector对象。但是，如果由一个线程访问Vector, 代码要在同步操作上耗费大量的时间。这种情况还是很常见的。而ArrayList方法不是同步的，

因此，建议在不需要同步时使用ArrayList, 而不要使用Vector。

#### 散列集 HashSet

如果a_equals(b) 为true, a 与b 必须具有相同的散列码。

在Java中，散列表用链表数组实现。每个列表被称为桶（bucket) 。要想査找表中对象的位置， 就要先计算它的散列码， 然后与桶的总数取余，所得到的结果就是保存这个元素的桶的索引。

将桶数设置为一个素数，以防键的集聚。标准类库使用的桶数是2的幂，默认值为16。

装填因子（load factor) 决定何时对散列表进行再散列。例如，如果装填因子为0.75。

HashSet 类，它实现了基于散列表的集。可以用add 方法添加元素。

**树集 Tree Set**

树集(Tree Set)是一个有序集合 (sorted collection)可以以任意顺序将元素插入到集合中。在对集合进行遍历时，每个值将自动地按照排序后的顺序呈现.排序是用树结构完成的（当前实现使用的

是红黑树). 每次将一个元素添加到树中时，都被放置在正确的排序位置上。

将一个元素添加到树中要比添加到散列表中慢。

队列：有两个端头的队列，即双端队列，可以让人们有效地在头部和尾部同时添加或删除元素。Deque接口，并由 ArrayDeque 和 LinkedList 类实现。

**优先级队列（priority queue) **

优先级队列（priority queue) 中的元素可以按照任意的顺序插人，却总是按照排序的顺序进行检索

优先级队列使用了一个优雅且高效的数据结构，称为堆（heap)。堆是一个可以自我调整的二叉树，对树执行添加（add) 和删除（remore) 操作，可以让最小的元素移动到根，而不必花费时间对元素进行排序。

典型示例是任务调度。每一个任务有一个优先级，任务以随机顺序添加到队列中。

	PriorityQueue<LocalDate> pq = new PriorityQueueoO;

#### 映射map

HashMap和TreeMap

	Map<String, Employee> staff = new HashMap<>();//HashMap implements Map
	Employee harry = new Employee ('Harry Hacker");
	staff.put(”987-98-9996",harry);

散列映射对键进行散列，树映射用键的整体顺序对元素进行排序， 并将其组织成搜索树

remove方法用于从映射中删除给定键对应的元素。size 方法用于返回映射中的元素数。 要迭代处理映射的键和值， 最容易的方法是使用forEach 方法。可以提供一个接收键和值的lambda 表达式。映射中的每一项会依序调用这个表达式。 

	map.forEach((k,v)->{
		    System.out.println("k="+k);
		});

更新映射项:  

getOrDefault方法

	counts.put(word,getOrDefault(word,0)+1);

首先调用 putlfAbsent 方法。只有当键原先不存在时才会放入一个值。

	counts.putIfAbsent(word,0);
	counts.put(word,counts.get(word）+1）；

merge方法，将把word与1关联

	counts.merge(word, 1, Integer::sum);

映射视图：

可以得到映射的视图（View)————这是实现了 Collection 接口或某个子接口的对象，键集、值集合（不是一个集）以及键 / 值对集
 
        Map<String,String> map=new HashMap<>();
        map.put("a","b");
        Set<String> set=map.keySet();
        Collection<String> collection=map.values();
        Set<Map.Entry<String, String>> set2=map.entrySet();
        Iterator itr=set2.iterator();
        while(itr.hasNext()) {
        	System.out.println(itr.next());
        }
        for(Map.Entry<String, String> entry:set2) {
        	String a=entry.getValue();
        	String b=entry.getKey();
        }

**弱散列映射：**

负责从长期存活的映射表中删除那些无用的值。 或者使用WeakHashMap完成这件事情。当对键的唯一引用来自散列条目时。

WeakHashMap 使用弱引用（weak references) 保存键，WeakReference对象将引用保存到另外一个对象中，在这里，就是散列键。对于这种类型的对象，垃圾回收器用一种特有的方式进行处理。通常，如果垃圾回收

器发现某个特定的对象已经没有他人引用了，就将其回收。然而，如果某个对象只能由WeakReference引用，垃圾回收器仍然回收它，但要将引用这个对象的弱引用放人队列中。WeakHashMap将周期性地检查队

列， 以便找出新添加的弱引用。一个弱引用进人队列意味着这个键不再被他人使用， 并且已经被收集起来。于是， WeakHashMap将删除对应的条目。
 
**链接散列集与映射**

LinkedHashSet 和 LinkedHashMap类用来记住插人元素项的顺序，这样就可以避免在散列表中的项从表面上看是随机排列的。

链接散列映射将用访问顺序（谁访问的多）， 而不是插入顺序， 对映射条目进行迭代。每次调用 get 或 put, 受到影响的条目将从当前的位置删除，并放到条目链表的尾部

LinkedHashMap<K, V>(initialCapacity, loadFactor, true)

**枚举集与映射**

EnumSet 是一个枚举类型元素集的高效实现。

EnumMap是一个键类型为枚举类型的映射。

EnumMap<Weekday, Employee〉personlnCharge = new EnumMap<>(Weekday.class); 

**表示散列映射**

类 IdentityHashMap 有特殊的作用，在这个类中， 键的散列值不是用hashCode函数计算的， 而是用 System.identityHashCode 方法计算的。 这是 Object.hashCode 方法根据对象的内 存地址来计算散列码时所使用的方式。

#### 视图与包装器

通过使用视图 (views) 可以获得其他的实现了 Collection接口和 Map 接口的对象。

keySet方法返回一个实现 Set 接口的类对象， 这个类的方法对原映射进行操作。这种集合称为视图。

轻量级集合包装器

	List<Card> cardList = Arrays.asList(cardDeck):

返回的对象不是 ArrayList。它是一个视图对象， 带有访问底层数组的 get 和 set方法。

**子范围视图**

不可修改的视图

subList 方法来获得一个列表的子范围视图

	List group2 = staff.subList(10, 20);

类似的：

	SortedSet< E> subSet(E from, E to)
	SortedSet< E> headSet(E to)
	SortedSet< E> tail Set(E from)


**不可修改的视图**

Collections.unmodifiableList

Collections 还有几个方法， 用于产生集合的不可修改视图 

	List<String> staff = new LinkedListoO ;
	
	1ookAt (Coll ecti ons.unmodi fiabl eLi st(staff));

同步视图

synchronizedMap 方法可以将任何一个映射表转换成具有同步访问方法的Map:

	Map<String, Employee>map = Collections.synchronizedMap(new HashMap<String, Employee>())； 


#### 算法

交集： 

	Set<String> result = new HashSeto(a);
	result.retainAll(b);

视图删除： staffMap.keySet().removeAll (terminatedIDs);

toArray： 从集合得到数组

	Object values = staff.toArray（）;
	
批操作

很多操作会“ 成批” 复制或删除元素。通过使用一个子范围视图，可以把批操作限制在子列表和子集上。这个子范围还可以完成更改操作。 staff.subList（0，10）.clear()； 

**集合与数组的转换**

如果需要把一个数组转换为集合，Arrays.asList 包装器可以达到这个目的。例如：

数组---->集合

List<String> list=new ArrayList<>();
    	String[] a=new String[10];
    	HashSet<String> set=new HashSet<>(Arrays.asList(a));
	
集合-->数组

    	String[] b=set.toArray(new String[0]);
    	String[] b=set.toArray(new String[10]);
	
 
#### 遗留集合

Hashtable ：与HashMap 类的作用一样，实际上，它们拥有相同的接口。与Vector 类的方法一样。Hashtable 的方法也是同步的。

枚举： Enumeration 接口有两个方法，即hasMoreElements 和nextElement

Collections.enumeration 将产生一个枚举对象，枚举集合中的元素

属性映射（property map) :

• 键与值都是字符串。

• 表可以保存到一个文件中，也可以从文件中加载。

• 使用一个默认的辅助表。

实现属性映射的 Java 平台类称为 Properties

栈（stack）

位集

由于位集将位包装在字节里，所以，使用位集要比使用 Boolean对象的 ArrayList 更加高效

BitSet 类提供了一个便于读取、设置或清除各个位的接口。使用这个接口可以避免屏蔽和其他麻烦的位操作。


### 15  并发

**一个单独的线程中执行一个任务的简单过程**

```java     
	package com;
	import java.util.*;
	import java.lang.*;
	import java.io.*;
	public class Welcome{
	    class a implements Runnable{
		public void run() {
			System.out.println("a");
		}
	    }
	    public void x() {
		 Runnable i=new a();
			Thread thread=new Thread(new a());
			thread.start();
	    }
	    public static void main(String []args){
		 new Welcome().x();

	    }
	}
```

1 ) 将任务代码移到实现了 Runnable 接口的类的 run方法中。这个接口非常简单，只有 一个方法：

public interface Runnable { void run（）； } 由于 Runnable 是一个函数式接口，可以用 lambda 表达式建立一个实例： Runnable r = () -> { taskcode};

2 ) 由 Runnable 创建一个 Thread 对象： Thread t = new Thread(r);

3 ) 启动线程： t.start（）；
 

#### 中断线程

interrupt 方法可以用来请求终止线程。当对一个线程调用 interrupt 方法时，线程的中断状态将被置位。这是每一个线程都具有的 boolean 标志。

每个线程都应该不时地检査这个标志，以判断线程是否被中断。 要想弄清中断状态是否被置位，首先调用静态的 Thread.currentThread方法获得当前线 程，然后调用 islnterrupted方法
 
	while(!Thread.currentThread().isInterrupted()) {

	}
	
当在一个被阻塞的线程（调用sleep或wait) 上调用 interrupt方法时，阻塞调用将会被 Interrupted Exception 异常中断。	
	
被中断的线程可以决定如何响应中断。某些线程是如此重要以至于应该处理完异常

```java
	Runnable r = () -> {
	 try { 
		while (!Thread.currentThread().islnterrupted0 && more work todo) 
		{ 
		    do morework 
		}
	     } 
	catch(InterruptedException e) 
	{ 
	     // thread was interr叩ted during sleep or wait } 
	    finally
	
	    { cleanup,if required } // exiting the run method terminates the thread 
	} 
```

interrupted和islnterrupted。Interrupted方法是一个静态方法，它检测当前的线程是否被中断。 调用interrupted方法会清除该线程的中断状态。

islnterrupted方法是一个实例方法，可用来检验是否有线程被中断。调用这个方法不会改变中断状态。

InterruptedException 异常被抑制在很低的层次上，

有两种合理 的选择：

•在catch子句中调用 Thread.currentThread().interrupt() 来设置中断状态。于是，调用者可以对其进行检测。

```java
	void mySubTask() {
	try { 
	    sleep(delay); 
	} 
	catch (InterruptedException e) 
	{
	    Thread.currentThread()-interrupt(); 
	}
```

•或者，更好的选择是，用 throws InterruptedException标记你的方法， 不采用 try语句块捕获异常。于是，调用者（或者，最终的 run 方法）可以捕获这一异常。 

#### 线程状态

线程可以有如下 6 种状态：

•New (新创建）

•Runnable (可运行）

•Blocked (被阻塞）

•Waiting (等待）

•Timed waiting (计时等待）

•Terminated (被终止） 


当用new操作符创建一个新线程时，如 new Thread(r)，该线程还没有开始运行。

可运行线程, 一旦调用start方法，线程处于runnable状态。

抢占式调度系统给每一个可运行线程一个时间片来执行任务。当时间片用完，操作系统剥夺该线程的运行权，并给另一个线程运行机会（见图 14-4 )。当选择下一个线程时， 操作系统考虑线程的优先级。

**被阻塞线程和等待线程**

当线程处于被阻塞或等待状态时，它暂时不活动。它不运行任何代码且消耗最少的资源。直到线程调度器重新激活它。

*当一个线程试图获取一个内部的对象锁（而不是java.util.concurrent 库中的锁)，而该锁被其他线程持有，则该线程进人阻塞状态。当所有其他线程释放该锁，并且线程调度器允许本线程持有它的时候，该线程将变成非阻塞状态。

*当线程等待另一个线程通知调度器一个条件时，它自己进入等待状态。在调用Object.wait方法或 Thread.join方法，或者是等待 java, util.concurrent 库中的 Lock 或 Condition 时， 就会出现这种情况。

*有几个方法有一个超时参数。调用它们导致线程进人计时等待（timed waiting)状态。这一状态将一直保持到超时期满或者接收到适当的通知。带有超时参数的方法有 Thread.sleep 和 Object.wait、Thread.join、Lock.tryLock 以及 Condition.await 的计时版。

**被终止的线程**

线程因如下两个原因之一而被终止:  因为run方法正常退出而自然死亡。因为一个没有捕获的异常终止了run方法而意外死亡。

#### 线程属性

**线程优先级**

线程的各种属性：线程优先级、守护线程、线程组以及处理未捕获异常的处理器。

在 Java 程序设计语言中，每一个线程有一个优先级。默认情况下，一个线程继承它的父线程的优先级。可以用setPriority方法提高或降低任何一个线程的优先级。可以将优先级设置为在 MIN_PRIORITY (在 Thread类中定义为 1) 与 MAX_PRIORITY (定义为 10) 之间的任何值。NORM_PRIORITY 被定义为 5。

**守护线程**

t.setDaemon(true); 将线程转换为守护线程（daemon thread)。守护线程的唯一用途是为其他线程提供服务。

计时线程就是一个例子，它定时地发送“ 计时器嘀嗒” 信号给其他线程或清空过时的高速缓存项的线程。当只剩下守护线程时， 虚拟机就退出了，由于如果只 剩下守护线程， 就没必要继续运行程序了。 

守护线程应该永远不去访问固有资源，如文件、 数据库，因为它会在任何时候甚至在一个操作的中间发生中断。

**未捕获异常处理器**

在线程死亡之前，异常被传递到一个用于未捕获异常的处理器。 该处理器必须属于一个实现 Thread.UncaughtExceptionHandler 接口的类

就在线程死亡之前， 异常被传递到一个用于未捕获异常的处理器。 该处理器必须属于一个实现 Thread.UncaughtExceptionHandler 接口的类。这个接口只有— 个方法。

	void uncaughtException(Thread t, Throwable e)

可以用 setUncaughtExceptionHandler方法为任何线程安装一个处理器。也可以用 Thread 类的静态方法 setDefaultUncaughtExceptionHandler 为所有线程安装一个默认的处理器。

线程组是一个可以统一管理的线程集合。默认情况下，创建的所有线程属于相同的线程组， 但是， 也可能会建立其他的组。现在引入了更好的特性用于线程集合的操作， 所以建议不要在自己的程序中使用线程组。

**ThreadGroup 类**

ThreadGroup类实现Thread.UncaughtExceptionHandler接口。它的uncaughtException方法做如下操作：

1 ) 如果该线程组有父线程组，那么父线程组的uncaughtException方法被调用。

2 ) 否则，如果 Thread.getDefaultExceptionHandler方法返回一个非空的处理器， 则调用该处理器。

3 ) 否则，如果 Throwable是ThreadDeath的一个实例， 什么都不做。

4 ) 否则，线程的名字以及Throwable的栈轨迹被输出到System.err 上。 这是你在程序中肯定看到过许多次的栈轨迹


#### 同步

两个或两个以上的线程需要共享对同一数据的存取。如果两个线程存取相同的对象，并且每一个线程都调用了一个修改该对象状态的方法，这样一个情况通常称为竞争条件（race condition)。

**锁对象**

有两种机制防止代码块受并发访问的干扰。synchronized 关键字自动提供一个锁

用 ReentrantLock 保护代码块的基本结构如下：

```java
	myLock.lock（）; // a ReentrantLock object 
	try { critical section } 
	finally 
	{ myLock.unlock（）；// make sure the lock is unlocked even if an exception isthrown } 
```

这一结构确保任何时刻只有一个线程进人临界区。一旦一个线程封锁了锁对象， 其他任 何线程都无法通过 lock语句。当其他线程调用 lock 时，它们被阻塞，直到第一个线程释放 锁对象。

警告：把解锁操作括在 finally 子句之内是至关重要的。如果在临界区的代码抛出异常， 锁必须被释放。否则， 其他线程将永远阻塞。

如果使用锁，就不能使用带资源的try语句。首先， 解锁方法名不是 close。不过， 即使将它重命名，带资源的 try语句也无法正常工作。它的首部希望声明一个新变量。但 是如果使用一个锁， 你可能想使用多个线程共享的那个变量。

同步，简单地理解，就是协同步调，一个完成了，另一个才能开始。

异步，就是你说的不同步，就是互不干扰，各干各的，多个线程可能同时进行。

锁是可重入的，因为线程可以重复地获得已经持有的锁。锁保持一个持有计数（hold count) 来跟踪对 lock 方法的嵌套调用。线程在每一次调用 lock 都要调用 unlock 来释放锁。 由于这一特性， 被一个锁保护的代码可以调用另一个使用相同的锁的方法  

通常， 可能想要保护需若干个操作来更新或检查共享对象的代码块。要确保这些操作完 成后， 另一个线程才能使用相同对象。 

**条件对象**

要使用一个条件对象来管理那些已经获得了一个锁但是却不能做有用工作的线程。

一个锁对象可以有一个或多个相关的条件对象 。习惯上给每一个条件对象命名为可以反映它所表达的条件的名字。

等待获得锁的线程和调用await 方法的线程存在本质上的不同。一旦一个线程调用await方法，它进人该条件的等待集。当锁可用时，该线程不能马上解除阻塞。相反，它处于阻塞状态，直到另一个线程调用同一条件上的signalAll 方法时为止。

这一调用重新激活因为这一条件而等待的所有线程。当这些线程从等待集当中移出时， 它们再次成为可运行的，调度器将再次激活它们。

同时，它们将试图重新进人该对象。一旦锁成为可用的，它们中的某个将从 await 调用返回， 获得该锁并从被阻塞的地方继续执行。

此时， 线程应该再次测试该条件。由于无法确保该条件被满足

signalAll 方法仅仅是通知正在等待的线程 ：此时有可能已经满足条件， 值得再次去检测该条件。 在对象的状态有利于等待线程的方向改变时调用signalAll。

另一个方法 signal, 则是随机解除等待集中某个线程的阻塞状态。这比解除所有线程的阻塞更加有效。当一个线程拥有某个条件的锁时， 它仅仅可以在该条件上调用 await、signalAll 或 signal 方法。

**synchronized关键字**

• 锁用来保护代码片段， 任何时刻只能有一个线程执行被保护的代码。

• 锁可以管理试图进入被保护代码段的线程。

• 锁可以拥有一个或多个相关的条件对象。

• 每个条件对象管理那些已经进入被保护的代码段但还不能运行的线程。

Java 中的每一个对象都有一个内部锁。如果一个方法用 synchronized关键字声明，那么对象的锁 将保护整个方法。也就是说，要调用该方法，线程必须获得内部的对象锁

```java
public synchronized void method（） { method body }
 
public void method(){
 
this.intrinsicLock.lock();
 
try{
 
}finally{
    this.intrinsicLock.unlock();
}
 
}

```

内部对象锁只有一个相关条件。wait方法添加一个线程到等待集中，notifyAll /notify方法解除等待线程的阻塞状态。换句话说，调用wait 或notityAll 等价于

	intrinsicCondition.await（）;
	intrinsicCondition.signalAll（）; 


内部锁和条件存在一些局限。包括：

• 不能中断一个正在试图获得锁的线程。

• 试图获得锁时不能设定超时。

• 每个锁仅有单一的条件，可能是不够的。

 Lock 和 Condition 对象还是同步方法？下面是一些建议:
 
•  最好既不使用 Lock/Condition 也不使用 synchronized 关键字。在许多情况下你可以使用java.util.concurrent 包中的一种机制，它会为你处理所有的加锁。

• 如果synchronized关键字适合你的程序，那么请尽量使用它，这样可以减少编写的代码数量，减少出错的几率。

• 如果特别需要Lock/Condition结构提供的独有特性时，才使用Lock/Condition.

synchronized锁住对象的时候锁住的是堆中的对象，而不是栈中对象的引用。

```java
	Object o=new Object();
	synchronized(o){
	}

	o=new Object();
	synchronized(o){
	}
	//这两个锁住的是不同的对象。
```

不要锁字符串常量，因为相同的字符串常量在一个地址，都在常量池里。不要去锁字符串常量。







