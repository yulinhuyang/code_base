### 1  tricks

[C++开源矩阵计算工具——Eigen的简单用法（一）](https://blog.csdn.net/houjixin/article/details/8490941)

[动态存储区、静态存储区、堆和栈的区别](https://blog.csdn.net/chen1083376511/article/details/54930191)


#### 秋招总结------C++面试题总结 1-5系列

https://blog.csdn.net/qq_39503189/article/details/104718499

https://blog.csdn.net/qq_39503189/article/details/104880359

https://blog.csdn.net/qq_39503189/article/details/104895023

https://blog.csdn.net/qq_39503189/article/details/104925389


####   面经汇总 C++基础再探

https://wangpengcheng.github.io/2019/11/28/%E9%9D%A2%E7%BB%8F%E6%B1%87%E6%80%BB-C++%E5%9F%BA%E7%A1%80%E5%86%8D%E6%8E%A2/

### 2  notes


引用与指针： 指针是实体，要初始化,间接访问，传参是传递指针的地址， 引用是别名，直接访问。传引用是传递变量的地址。

传值与传引用：传值是传递参数的拷贝，传引用是实参变量的地址。

static:

	全局可见性，分配一次。不能被virtual修饰。修饰的变量要类外初始化，修饰的函数不能访问非static的类成员。

	static变量，初始化一次，多次赋值。主程序之前内存分配。

const:阻止变量被修改，定义的时候就初始化。类型转换const_cast转为非const类型。

深复制：开辟新内存地址存放复制的对象。浅复制：只指向被复制的内存地址。

class与struct: class private ，strcut public,

虚函数与inline: 虚函数，实现运行时多态; inline,小函数，编译期间替换函数代码。

列表初始化：快于赋值初始化


构造函数执行顺序：基类-->成员类-->派生类

析构函数：派生类-->成员类-->基类

类的关系：has-A  包含,use-A 组合,is-A 继承


C语言执行过程： 源代码－－>预处理－－>编译（.s）－－>优化－－>汇编（.o）－－>链接-->可执行文件


堆：程序员管理，申请或释放，向上生长，动态分配。堆大小4G。

栈：系统管理，向下生长。栈1M大小。


#### **static**

static被引入以告知编译器，将变量存储在程序的静态存储区而非栈上空间，静态数据成员按定义出现的先后顺序依次初始化，注意静态成员嵌套时，要保证所嵌套的成员已经初始化了。消除时的顺序是初始化的反顺序。


#### **程序的内存分配**

栈区(stack):由编译器自动分配释放，存放函数的参数值，局部变量等值。

堆区(heap):堆允许程序在运行时动态地申请某个大小的内存。一般由程序员分配释放。

数据段：

只读数据段：一般是const修饰的变量以及程序中使用的文字常量一般会存放在只读数据段中。

已初始化的读写数据段：一般为已经初始化的全局变量，已经初始化的静态局部变量(static修饰的已经初始化的变量)

未初始化段（BSS）：BSS段通常是指用来存放程序中未初始化的全局变量和静态变量的一块内存区域。


常量区（特殊的常量存储区，属于静态存储区）

　　1) 常量占用内存,只读状态,决不可修改
　
　　3) 常量字符串就是放在这里的，程序结束后由系统释放

程序的内存分配：

  一个由C/C++编译的程序占用的内存分为以下几个部分  
  
        1、栈区（stack）：由编译器自动分配释放   ，存放函数的参数值，局部变量的值等。其  操作方式类似于数据结构中的栈。  
        
        2、堆区（heap） ：一般由程序员分配释放，   若程序员不释放，程序结束时可能由OS回收。注意它与数据结构中的堆是两回事，分配方式倒是类似于链表。
        
        3、全局区（静态区）（static）：全局变量和静态变量的存储是放在一块的，初始化的全局变量和静态变量在一块区域，   未初始化的全局变量和未初始化的静态变量在相邻的另一块区域。程序结束后由系统释放。  
        
         4、文字常量区：常量字符串就是放在这里的程序结束后由系统释放  
         
         5、程序代码区：存放函数体的二进制代码。


#### **引用与指针**

引用是别名

构造函数和析构函数不能抛出异常，不要调用虚函数。

use—A：类的依赖关系


#### **C++多态**

C++支持两种多态性：编译时多态性，运行时多态性。

　　a.编译时多态性：通过重载函数实现。
  
　　b.运行时多态性：通过虚函数实现。


1 静态多态（重载，模板）  是在编译的时候，就确定调用函数的类型。

2 动态多态（覆盖，虚函数实现）  在运行的时候，才确定调用的是哪个函数，动态绑定。运行基类指针指向派生类的对象，并调用派生类的函数。

虚函数实现原理：虚函数表和虚函数指针。

纯虚函数： virtual int fun() = 0;

函数的运行版本由实参决定，在运行时选择函数的版本，所以动态绑定又称为运行时绑定。

当编译器遇到一个模板定义时，它并不生成代码。只有当实例化出模板的一个特定版本时，编译器才会生成代码。

#### **类型转换**

继承机制中对象之间如何转换？指针和引用之间如何转换？

向上类型转换：将派生类指针或引用转换为基类的指针或引用被称为向上类型转换，向上类型转换会自动进行，而且向上类型转换是安全的。

向下类型转换：将基类指针或引用转换为派生类指针或引用被称为向下类型转换，向下类型转换不会自动进行，因为一个基类对应几个派生类，所以向下类型转换时不知道对应哪个派生类，所以在向下类型转换时必须加动态类型识别技术。RTTI技术，用dynamic_cast进行向下类型转换。

#### **拷贝与移动**

C++11之前，对象的拷贝控制由三个函数决定：拷贝构造函数（Copy Constructor）、拷贝赋值运算符（Copy Assignment operator）和析构函数（Destructor）。

C++11之后，新增加了两个函数：移动构造函数（Move Constructor）和移动赋值运算符（Move Assignment operator）。

区分构造和赋值：构造函数与赋值运算符的区别是，构造函数在创建或初始化对象的时候调用，而赋值运算符在更新一个对象的值时调用。

区分拷贝与移动：用对象a初始化对象b，拷贝构造函数，实际上就是把a对象的内容复制一份到b中。这样就避免了新的空间的分配，大大降低了构造的成本。这就是移动构造函数设计的初衷

https://www.jianshu.com/p/f5d48a7f5a52

```cpp
class A {
public:
    int x;
    A(int x) : x(x)
    {
        cout << "Constructor" << endl;
    }
    A(A& a) : x(a.x)
    {
        cout << "Copy Constructor" << endl;
    }
    A& operator=(A& a)
    {
        x = a.x;
        cout << "Copy Assignment operator" << endl;
        return *this;
    }
    A(A&& a) : x(a.x)
    {
        cout << "Move Constructor" << endl;
    }
    A& operator=(A&& a)
    {
        x = a.x;
        cout << "Move Assignment operator" << endl;
        return *this;
    }
};
```

#### **C语言的编译链接过程**

源代码－－>预处理－－>编译－－>优化－－>汇编－－>链接-->可执行文件

预编优，汇链执

预处理：读取c源程序，对其中的伪指令（以#开头的指令）和特殊符号进行处理。包括**宏定义替换、条件编译指令、头文件包含指令、特殊符号**。 预编译程序所完成的基本上是对源程序的“替代”工作。经过此种替代，生成一个没有宏定义、没有条件编译指令、没有特殊符号的输出文件。i预处理后的c文件，.ii预处理后的C++文件。

编译阶段：编译程序所要作得工作就是通过**词法分析和语法分析**，在确认所有的指令都符合语法规则之后，将其翻译成等价的中间代码表示或**汇编代码.s文件。**

汇编过程：汇编过程实际上指把汇编语言代码翻译成目标机器指令的过程。对于被翻译系统处理的每一个C语言源程序，都将最终经过这一处理而得到相应的目标文件。目标文件中所存放的也就是与源程序等效的目标的**机器语言代码。.o目标文件**

链接阶段：链接程序的主要工作就是将有关的目标文件彼此相连接，也即将在一个文件中引用的符号同该符号在另外一个文件中的定义连接起来，使得所有的这些目标文件成为一个能够诶操作系统装入执行的统一整体。

#### **函数指针**

函数指针指向的是特殊的数据类型，函数的类型是由其返回的数据类型和其参数列表共同决定的。

int (*pf)(const int&, const int&); (1)

上面的pf就是一个函数指针，指向所有返回类型为int，并带有两个const int&参数的函数。注意*pf两边的括号是必须的。

一个函数名就是一个指针，它指向函数的代码。一个函数地址是该函数的进入点，也就是调用函数的地址。

**野指针**

野指针是什么？如何检测内存泄漏？

野指针：指向内存被释放的内存或者没有访问权限的内存的指针。

1  “野指针”的成因主要有3种：

指针变量没有被初始化。任何指针变量刚被创建时不会自动成为NULL指针，它的缺省值是随机的，它会乱指一气。所以，指针变量在创建的同时应当被初始化，要么将指针设置为NULL，要么让它指向合法的内存。例如

```cpp
char *p = NULL;
char *str = new char(100);
char * p = (char * )malloc(sizeof(char));

```

2  指针p被free或者delete之后，没有置为NULL；

3  指针操作超越了变量的作用范围。

#### **内存泄漏**

内存泄漏：内存泄漏是指由于疏忽或错误造成了程序未能释放掉不再使用的内存的情况。

使用工具软件BoundsChecker，BoundsChecker是一个运行时错误检测工具，它主要定位程序运行时期发生的各种错误；调试运行DEBUG版程序，运用以下技术：CRT(C run-time libraries)、运行时函数调用堆栈、内存泄漏时提示的内存分配序号。

解决办法：智能指针。

检查、定位内存泄漏

检查方法：在main函数最后面一行，加上一句_CrtDumpMemoryLeaks()。调试程序，自然关闭程序让其退出，查看输出：

输出这样的格式{453}normal block at 0x02432CA8,868 bytes long

被{}包围的453就是我们需要的内存泄漏定位值，868 bytes long就是说这个地方有868比特内存没有释放。

定位代码位置

在main函数第一行加上_CrtSetBreakAlloc(453);意思就是在申请453这块内存的位置中断。然后调试程序，程序中断了，查看调用堆栈。加上头文件#include <crtdbg.h>

#### **delete p和delete[] p**

operator new 和 operator delete函数有两个重载版本

```cpp
void* operator new (size_t);        // allocate an object
void* operator new [] (size_t);     // allocate an array
  
void operator delete (void*);       // free an oject
void operator delete [] (void*);    // free an array
```

new的机制是将内存分配和对象构造组合在一起，同样的，delete也是将对象析构和内存释放组合在一起的。

allocator将这两部分分开进行，allocator申请一部分内存，不进行初始化对象，只有当需要的时候才进行初始化操作。

#### **RAII**

使用智能指针管理内存资源，RAII

**RAII全称是“Resource Acquisition is Initialization**，直译过来是“资源获取即初始化”，也就是说在构造函数中申请分配资源，在析构函数中释放资源。因为C++的语言机制保证了，当一个对象创建的时候，自动调用构造函数，当对象超出作用域的时候会自动调用析构函数。所以，在RAII的指导下，我们应该使用类来管理资源，将资源和对象的生命周期绑定。

智能指针（std::shared_ptr和std::unique_ptr）即RAII最具代表的实现，使用智能指针，可以实现自动的内存管理，再也不需要担心忘记delete造成的内存泄漏。毫不夸张的来讲，有了智能指针，代码中几乎不需要再出现delete了。

#### **内存对齐？位域**

  分配内存的顺序是按照声明的顺序。

  每个变量相对于起始位置的偏移量必须是该变量类型大小的整数倍，不是整数倍空出内存，直到偏移量是整数倍为止。

  最后整个结构体的大小必须是里面变量类型最大值的整数倍。
 
添加了#pragma pack(n)后规则就变成了下面这样：

  偏移量要是n和当前变量大小中较小值的整数倍

  整体大小要是n和最大变量大小中较小值的整数倍

  n值必须为1,2,4,8…，为其他值时就按照默认的分配规则

#### typedef、define、const、inline使用方法

[C++ typedef、define、const 和 inline](https://zhuanlan.zhihu.com/p/106576540)

typedef 

可以分别为基本类型重命名、指针类型重命名、结构体类型重命名和函数指针类型重命名

typedef在编译阶段有效，typedef有类型检查的功能

```cpp

// 结构体类型重命名
typedef struct Node {
    int n;
    double d;
}MyNode;            // 将结构体Node(C++ 中定义结构体为 Node node; C 中定义结构体为 struct Node node;) 重命名为MyNode

typedef struct {
    int n;
    char c;
}_Node;              // 给没有名字的结构体重命名为_Node(如果没有typedef给该结构体重命名，它就只能在此处定义一个结构体变量)


```
define

宏的本质是替换, 因为宏定义是预编译指令(前面带#号的)不是语句，所以后面不加 “;” 分号

enum给int型常量起名字，typedef给数据类型起名字，宏定义也可以看做一种重命名

宏指示符:  \ ” 反斜杠 换行,  # ” 字符指示符, “ ## ” 字符串拼接

const 

常量限定符，声明的常量只读，不允许修改

对于全局 const 值，C++ 中默认是内部链接(跟 static 一样只允许在本文件内可见)，而不是 C 中的默认外部链接

inline

inline(内联) 函数在被调用处进行代码替换，编译阶段进行替换

C++ 中使用 inline 定义内联函数(C 语言中一般是使用 #define 定义宏函数)

宏函数是简单的文本替换，不是真正的传参数，如果不注意运算顺序很容易出错，C++ 使用 inline 定义内联函数，比定义宏函数可靠，inline 定义的内联函数是真正的传递参数，C++ 中 inline 可用于常规函数也可用于类方法

C++ 中推荐使用 const 代替 #define 声明常量

C++ 中推荐使用 inline 代替 #define 声明函数

####  模板类

模板类一般都是放在一个h文件中，由template<…>处理的任何东西都意味着编译器在当时不为它分配存储空间，它一直处于等待状态直到被一个模板实例告知。在编译器和连接器的某一处，有一机制能去掉指定模板的多重定义。所以为了容易使用，几乎总是在头文件中放置全部的模板声明和定义。

在分离式编译的环境下，编译器编译某一个.cpp文件时并不知道另一个.cpp文件的存在,遇到模板时就傻眼了，因为模板仅在需要的时候才会实例化出来，所以，当编译器只看到模板的声明时，它不能实例化该模板，只能创建一个具有外部连接的符号并期待连接器能够将符号的地址决议出来。


#### 继承与派生

protected ： 派生类来说，相当于公有成员，在派生类中可以被访问

#### 迭代器++it,it++

迭代器++it,it++哪个好，为什么

前置返回一个引用，后置返回一个对象

// ++i实现代码为：

int& operator++()

{
    *this += 1;
    
    return *this;
}

前置不会产生临时对象，后置必须产生临时对象，临时对象会导致效率降低

//i++实现代码为：                                 

int operator++(int)                                 
{

int temp = *this;                                    

       ++*this;                                            

       return temp;     
}

#### class、union、struct的区别？

C语言中，struct只是一个聚合数据类型，没有权限设置，无法添加成员函数，无法实现面向对象编程，且如果没有typedef结构名，声明结构变量必须添加关键字struct。

C++中，struct功能大大扩展，可以有权限设置（默认权限为public），可以像class一样有成员函数，继承（默认public继承），可以实现面对对象编程，允许在声明结构变量时省略关键字struct。

C与C++中的union:一种数据格式，能够存储不同的数据类型，但只能同时存储其中的一种类型。C++ union结构式一种特殊的类。它能够包含访问权限、成员变量、成员函数（可以包含构造函数和析构函数）。它不能包含虚函数和静态数据变量。它也不能被用作其他类的基类，它本身也不能有从某个基类派生而来。Union中得默认访问权限是public。union类型是共享内存的，以size最大的结构作为自己的大小。每个数据成员在内存中的起始地址是相同的。

#### 动态编译与静态编译

静态编译，编译器在编译可执行文件时，把需要用到的对应动态链接库中的部分提取出来，连接到可执行文件中去，使可执行文件在运行时不需要依赖于动态链接库；生成.a 

动态编译的可执行文件需要附带一个动态链接库，在执行时，需要调用其对应动态链接库的命令。所以其优点一方面是缩小了执行文件本身的体积，另一方面是加快了编译速度，节省了系统资源。缺点是哪怕是很简单的程序，只用到了链接库的一两条命令，也需要附带一个相对庞大的链接库；二是如果其他计算机上没有安装对应的运行库，则用动态编译的可执行文件就不能运行。生成so

####  空类的大小是多少？为什么？

C++空类的大小不为0，不同编译器设置不一样，vs设置为1；

C++标准指出，不允许一个对象（当然包括类对象）的大小为0，不同的对象不能具有相同的地址；

带有虚函数的C++类大小不为1，因为每一个对象会有一个vptr指向虚函数表，具体大小根据指针大小确定；

C++中要求对于类的每个实例都必须有独一无二的地址,那么编译器自动为空类分配一个字节大小，这样便保证了每个实例均有独一无二的内存地址。

#### vptr和vtable

https://yosef-gao.github.io/2016/09/27/cpp-vptr-and-vtable/

编译器在编译的时候使用了延迟绑定技术(late binding)。通过virtual关键字创建虚函数能引发晚捆绑，编译器在幕后完成了实现晚捆绑的必要机制。

它对每个包含虚函数的类创建一个表(称为VTABLE)，用于放置虚函数的地址。在每个包含虚函数的类中，编译器秘密地放置了一个称之为vpointer(缩写为VPTR)的指针，指向这个对象的VTABLE。

在创建一个含有虚函数的类时，系统会自动生成一个虚函数表，存放了当前对象所有的虚函数，而vptr指针就指向这个表的地址。

子类继承父类后，也会生成一个属于自己的虚函数表和vptr指针。对象调用虚函数，则会通过vptr指针在虚函数表中查找函数的地址进行调用。以此来达到多态的效果。

#### 引用与指针

如果数据对象很小，如内置数据类型或者小型结构，则按照值传递；

如果数据对象是数组，则使用指针（唯一的选择），并且指针声明为指向const的指针；

如果数据对象是较大的结构，则使用const指针或者引用，已提高程序的效率。这样可以节省结构所需的时间和空间；

如果数据对象是类对象，则使用const引用（传递类对象参数的标准方式是按照引用传递）；

####  静态函数能定义为虚函数吗？常函数?

1  static成员不属于任何类对象或类实例，所以即使给此函数加上virutal也是没有任何意义的。

2   静态与非静态成员函数之间有一个主要的区别。那就是静态成员函数没有this指针。虚函数依靠vptr和vtable来处理。vptr是一个指针，在类的构造函数中创建生成，并且只能用this指针来访问它，因为它是类的一个成员，并且vptr指向保存虚函数地址的vtable.对于静态成员函数，它没有this指针，所以无法访问vptr. 这就是为何static函数不能为virtual.虚函数的调用关系：this -> vptr -> vtable ->virtual function.

#### 数组与指针区别

1 数组在内存中是连续存放的，开辟一块连续的内存空间；数组所占存储空间：sizeof（数组名）；数组大小：sizeof(数组名)/sizeof(数组元素数据类型)；

2 用运算符sizeof 可以计算出数组的容量（字节数）。sizeof(p),p 为指针得到的是一个指针变量的字节数，而不是p 所指的内存容量。

3 编译器为了简化对数组的支持，实际上是利用指针实现了对数组的支持。具体来说，就是将表达式中的数组元素引用转换为指针加偏移量的引用。

4 在向函数传递参数的时候，如果实参是一个数组，那用于接受的形参为对应的指针。也就是传递过去是数组的首地址而不是整个数组，能够提高效率；

5 在使用下标的时候，两者的用法相同，都是原地址加上下标值，不过数组的原地址就是数组首元素的地址是固定的，指针的原地址就不是固定的。

#### 虚函数与纯虚函数的区别

纯虚函数只有定义没有实现，虚函数既有定义又有实现；

含有纯虚函数的类不能定义对象，含有虚函数的类能定义对象；

纯虚函数是在基类中声明的虚函数，它在基类中没有定义，但要求任何派生类都要定义自己的实现方法。在基类中实现纯虚函数的方法是在函数原型后加 =0:

　 virtual void funtion1()=0


#### 智能指针怎么用？智能指针出现循环引用怎么解决？

**shared_ptr**

调用一个名为make_shared的标准库函数，shared_ptr<int> p = make_shared<int>(42);通常用auto更方便，auto p = shared_ptr<int> p2(new int(2));

每个shared_ptr都有一个关联的计数器，通常称为引用计数，一旦一个shared_ptr的计数器变为0，它就会自动释放自己所管理的对象；shared_ptr的析构函数就会递减它所指的对象的引用计数。如果引用计数变为0，shared_ptr的析构函数就会销毁对象，并释放它占用的内存。

**unique_ptr**

一个unique_ptr拥有它所指向的对象。某个时刻只能有一个unique_ptr指向一个给定对象。当unique_ptr被销毁时，它所指向的对象也被销毁。

**weak_ptr**

weak_ptr是一种不控制所指向对象生存期的智能指针，它指向由一个shared_ptr管理的对象，将一个weak_ptr绑定到一个shared_ptr不会改变引用计数，一旦最后一个指向对象的shared_ptr被销毁，对象就会被释放，即使有weak_ptr指向对象，对象还是会被释放。

弱指针用于专门解决shared_ptr循环引用的问题，weak_ptr不会修改引用计数，即其存在与否并不影响对象的引用计数器。循环引用就是：两个对象互相使用一个shared_ptr成员变量指向对方。弱引用并不对对象的内存进行管理，在功能上类似于普通指针，然而一个比较大的区别是，弱引用能检测到所管理的对象是否已经被释放，从而避免访问非法内存。

#### C++类型转换有四种

static_cast能进行基础类型之间的转换，也是最常看到的类型转换。它主要有如下几种用法：

1 . 用于类层次结构中父类和子类之间指针或引用的转换。进行上行转换（把子类的指针或引用转换成父类表示）是安全的；

2 . 进行下行转换（把父类指针或引用转换成子类指针或引用）时，由于没有动态类型检查，所以是不安全的；

3 . 用于基本数据类型之间的转换，如把int转换成char，把int转换成enum。这种转换的安全性也要开发人员来保证。

4 . 把void指针转换成目标类型的指针（不安全！！）

5 . 把任何类型的表达式转换成void类型。

const_cast： 运算符用来修改类型的const或volatile属性。除了去掉const 或volatile修饰之外， type_id和expression得到的类型是一样的。但需要特别注意的是const_cast不是用于去除变量的常量性，而是去除指向常数对象的指针或引用的常量性，其去除常量性的对象必须为指针或引用。

reinterpret_cast： 它可以把一个指针转换成一个整数，也可以把一个整数转换成一个指针（先把一个指针转换成一个整数，在把该整数转换成原类型的指针，还可以得到原先的指针值）。

dynamic_cast :主要用在继承体系中的安全向下转型。它能安全地将指向基类的指针转型为指向子类的指针或引用，并获知转型动作成功是否。转型失败会返回null（转型对象为指针时）或抛出异常bad_cast（转型对象为引用时）。  

dynamic_cast 会动用运行时信息（RTTI）来进行类型安全检查，因此 dynamic_cast 存在一定的效率损失。当使用dynamic_cast时，该类型必须含有虚函数，这是因为dynamic_cast使用了存储在VTABLE中的信息来判断实际的类型，RTTI运行时类型识别用于判断类型。typeid表达式的形式是typeid(e)，typeid操作的结果是一个常量对象的引用，该对象的类型是type_info或type_info的派生。



 
