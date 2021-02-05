**第1章 开始** 

1.1 编写一个简单的C++程序  

1.1.1 编译、运行程序  

1.2 初识输入输出 

1.3 注释简介  

1.4 控制流 

1.4.1 while语句  

1.4.2 for语句 

1.4.3 读取数量不定的输入数据 

1.4.4 if语句  

1.5 类简介  

1.5.1 Sales_item类  

1.5.2 初识成员函数  

1.6 书店程序  

小结  

术语表  

**第Ⅰ部分 C++基础**  

**第2章 变量和基本类型**  

2.1 基本内置类型  

2.1.1 算术类型  

2.1.2 类型转换  

2.1.3 字面值常量  

2.2 变量  

2.2.1 变量定义  

2.2.2 变量声明和定义的关系  

2.2.3 标识符  

2.2.4 名字的作用域  

2.3 复合类型  

2.3.1 引用  

2.3.2 指针  

2.3.3 理解复合类型的声明  

2.4 const限定符  

2.4.1 const的引用  

2.4.2 指针和const  

2.4.3 顶层const  

2.4.4 constexpr和常量表达式  

2.5 处理类型  

2.5.1 类型别名  

2.5.2 auto类型说明符  

2.5.3 decltype类型指示符  

2.6 自定义数据结构  

2.6.1 定义Sales_data类型  

2.6.2 使用Sales_data类  

2.6.3 编写自己的头文件  

小结  

术语表  

**第3章 字符串、向量和数组**  

3.1 命名空间的using声明  

3.2 标准库类型string  

3.2.1 定义和初始化string对象  

3.2.2 string对象上的操作  

3.2.3 处理string对象中的字符  

3.3 标准库类型vector  

3.3.1 定义和初始化vector对象  

3.3.2 向vector对象中添加元素  

3.3.3 其他vector操作  

3.4 迭代器介绍  

3.4.1 使用迭代器  

3.4.2 迭代器运算  

3.5 数组 

3.5.1 定义和初始化内置数组 

3.5.2 访问数组元素 

3.5.3 指针和数组 

3.5.4 C风格字符串 

3.5.5 与旧代码的接口 

3.6 多维数组 

小结 

术语表 

**第4章 表达式** 

4.1 基础 

4.1.1 基本概念 

4.1.2 优先级与结合律 

4.1.3 求值顺序 

4.2 算术运算符 

4.3 逻辑和关系运算符 

4.4 赋值运算符 

4.5 递增和递减运算符 

4.6 成员访问运算符 

4.7 条件运算符 

4.8 位运算符 

4.9 sizeof运算符 

4.10 逗号运算符 

4.11 类型转换 

4.11.1 算术转换 

4.11.2 其他隐式类型转换 

4.11.3 显式转换 

4.12 运算符优先级表 

小结 

术语表 

**第5章 语句** 

5.1 简单语句 

5.2 语句作用域 

5.3 条件语句 

5.3.1 if语句 

5.3.2 switch语句 

5.4 迭代语句 

5.4.1 while语句 

5.4.2 传统的for语句 

5.4.3 范围for语句 

5.4.4 do while语句 

5.5 跳转语句 

5.5.1 break语句 

5.5.2 continue语句 

5.5.3 goto语句 

5.6 TRY语句块和异常处理 

5.6.1 throw表达式 

5.6.2 try语句块 

5.6.3 标准异常 

小结 

术语表 

**第6章 函数** 

6.1 函数基础 

6.1.1 局部对象 

6.1.2 函数声明 

6.1.3 分离式编译 

6.2 参数传递 

6.2.1 传值参数 

6.2.2 传引用参数 

6.2.3 const形参和实参 

6.2.4 数组形参 

6.2.5 main：处理命令行选项 

6.2.6 含有可变形参的函数 

6.3 返回类型和return语句 

6.3.1 无返回值函数 

6.3.2 有返回值函数 

6.3.3 返回数组指针 

6.4 函数重载 

6.4.1 重载与作用域 

6.5 特殊用途语言特性 

6.5.1 默认实参 

6.5.2 内联函数和constexpr函数 

6.5.3 调试帮助 

6.6 函数匹配 

6.6.1 实参类型转换 

6.7 函数指针 

小结 

术语表 

**第7章 类** 

7.1 定义抽象数据类型 

7.1.1 设计Sales_data类 

7.1.2 定义改进的Sales_data类 

7.1.3 定义类相关的非成员函数 

7.1.4 构造函数 

7.1.5 拷贝、赋值和析构 

7.2 访问控制与封装 

7.2.1 友元 

7.3 类的其他特性 

7.3.1 类成员再探 

7.3.2 返回*this的成员函数 

7.3.3 类类型 

7.3.4 友元再探 

7.4 类的作用域 

7.4.1 名字查找与类的作用域 

7.5 构造函数再探 

7.5.1 构造函数初始值列表 

7.5.2 委托构造函数 

7.5.3 默认构造函数的作用 

7.5.4 隐式的类类型转换 

7.5.5 聚合类 

7.5.6 字面值常量类 

7.6 类的静态成员 

小结 

术语表 

**第Ⅱ部 C++标准库** 

**第8章 IO库** 

8.1 IO类 

8.1.1 IO对象无拷贝或赋值 

8.1.2 条件状态 

8.1.3 管理输出缓冲 

8.2 文件输入输出 

8.2.1 使用文件流对象 

8.2.2 文件模式 

8.3 string流 

8.3.1 使用istringstream 

8.3.2 使用ostringstream 

小结 

术语表 

**第9章 顺序容器** 

9.1 顺序容器概述 

9.2 容器库概览 

9.2.1 迭代器 

9.2.2 容器类型成员 

9.2.3 begin和end成员 

9.2.4 容器定义和初始化 

9.2.5 赋值和swap 

9.2.6 容器大小操作 

9.2.7 关系运算符 

9.3 顺序容器操作 

9.3.1 向顺序容器添加元素 

9.3.2 访问元素 

9.3.3 删除元素 

9.3.4 特殊的forward_list操作 

9.3.5 改变容器大小 

9.3.6 容器操作可能使迭代器失效 

9.4 vector对象是如何增长的 

9.5 额外的string操作 

9.5.1 构造string的其他方法 

9.5.2 改变string的其他方法 

9.5.3 string搜索操作 

9.5.4 compare函数 

9.5.5 数值转换 

9.6 容器适配器 

小结 

术语表 

**第10章 泛型算法** 

10.1 概述 

10.2 初识泛型算法 

10.2.1 只读算法 

10.2.2 写容器元素的算法 

10.2.3 重排容器元素的算法 

10.3 定制操作 

10.3.1 向算法传递函数 

10.3.2 lambda表达式 

10.3.3 lambda捕获和返回 

10.3.4 参数绑定 

10.4 再探迭代器 

10.4.1 插入迭代器 

10.4.2 iostream迭代器 

10.4.3 反向迭代器 

10.5 泛型算法结构 

10.5.1 5类迭代器 

10.5.2 算法形参模式 

10.5.3 算法命名规范 

10.6 特定容器算法 

小结 

术语表 

**第11章 关联容器** 

11.1 使用关联容器 

11.2 关联容器概述 

11.2.1 定义关联容器 

11.2.2 关键字类型的要求 

11.2.3 pair类型 

11.3 关联容器操作 

11.3.1 关联容器迭代器 

11.3.2 添加元素 

11.3.3 删除元素 

11.3.4 map的下标操作 

11.3.5 访问元素 

11.3.6 一个单词转换的map 

11.4 无序容器 

小结 

术语表 

**第12章 动态内存** 

12.1 动态内存与智能指针 

12.1.1 shared_ptr类 

12.1.2 直接管理内存 

12.1.3 shared_ptr和new结合使用 

12.1.4 智能指针和异常 

12.1.5 unique_ptr 

12.1.6 weak_ptr 

12.2 动态数组 

12.2.1 new和数组 

12.2.2 allocator类 

12.3 使用标准库：文本查询程序 

12.3.1 文本查询程序设计 

12.3.2 文本查询程序类的定义 

小结 

术语表 

**第Ⅲ部分 类设计者的工具** 

**第13章 拷贝控制** 

13.1 拷贝、赋值与销毁 

13.1.1 拷贝构造函数 

13.1.2 拷贝赋值运算符 

13.1.3 析构函数 

13.1.4 三/五法则 

13.1.5 使用=default 

13.1.6 阻止拷贝 

13.2 拷贝控制和资源管理 

13.2.1 行为像值的类 

13.2.2 定义行为像指针的类 

13.3 交换操作 

13.4 拷贝控制示例 

13.5 动态内存管理类 

13.6 对象移动 

13.6.1 右值引用 

13.6.2 移动构造函数和移动赋值运算符 

13.6.3 右值引用和成员函数 

小结 

术语表 

**第14章 操作重载与类型转换** 

14.1 基本概念 

14.2 输入和输出运算符 

14.2.1 重载输出运算符<< 

14.2.2 重载输入运算符>> 

14.3 算术和关系运算符 

14.3.1 相等运算符 

14.3.2 关系运算符 

14.4 赋值运算符 

14.5 下标运算符 

14.6 递增和递减运算符 

14.7 成员访问运算符 

14.8 函数调用运算符 

14.8.1 lambda是函数对象 

14.8.2 标准库定义的函数对象 

14.8.3 可调用对象与function 

14.9 重载、类型转换与运算符 

14.9.1 类型转换运算符 

14.9.2 避免有二义性的类型转换 

14.9.3 函数匹配与重载运算符 

小结 

术语表 

**第15章 面向对象程序设计** 

15.1 OOP：概述 

15.2 定义基类和派生类 

15.2.1 定义基类 

15.2.2 定义派生类 

15.2.3 类型转换与继承 

15.3 虚函数 

15.4 抽象基类 

15.5 访问控制与继承 

15.6 继承中的类作用域 

15.7 构造函数与拷贝控制 

15.7.1 虚析构函数 

15.7.2 合成拷贝控制与继承 

15.7.3 派生类的拷贝控制成员 

15.7.4 继承的构造函数 

15.8 容器与继承 

15.8.1 编写Basket类 

15.9 文本查询程序再探 

15.9.1 面向对象的解决方案 

15.9.2 Query_base类和Query类 

15.9.3 派生类 

15.9.4 eval函数 

小结 

术语表 

**第16章 模板与泛型编程** 

16.1 定义模板 

16.1.1 函数模板 

16.1.2 类模板 

16.1.3 模板参数 

16.1.4 成员模板 

16.1.5 控制实例化 

16.1.6 效率与灵活性 

16.2 模板实参推断 

16.2.1 类型转换与模板类型参数 

16.2.2 函数模板显式实参 

16.2.3 尾置返回类型与类型转换 

16.2.4 函数指针和实参推断 

16.2.5 模板实参推断和引用 

16.2.6 理解std::move 

16.2.7 转发 

16.3 重载与模板 

16.4 可变参数模板 

16.4.1 编写可变参数函数模板 

16.4.2 包扩展 

16.4.3 转发参数包 

16.5 模板特例化 

小结 

术语表 

**第Ⅳ部分 高级主题** 

**第17章 标准库特殊设施** 

17.1 tuple类型 

17.1.1 定义和初始化tuple 

17.1.2 使用tuple返回多个值 

17.2 BITSET类型 

17.2.1 定义和初始化bitset 

17.2.2 bitset操作 

17.3 正则表达式 

17.3.1 使用正则表达式库 

17.3.2 匹配与Regex迭代器类型 

17.3.3 使用子表达式 

17.3.4 使用regex_replace 

17.4 随机数 

17.4.2 其他随机数分布 

bernoulli_distribution类 

17.5 IO库再探 

17.5.1 格式化输入与输出 

17.5.2 未格式化的输入/输出操作 

17.5.3 流随机访问 

小结 

术语表 

**第18章 用于大型程序的工具** 

18.1 异常处理 

18.1.1 抛出异常 

18.1.2 捕获异常 

18.1.3 函数try语句块与构造函数 

18.1.4 noexcept异常说明 

18.1.5 异常类层次 

18.2 命名空间 

18.2.1 命名空间定义 

18.2.2 使用命名空间成员 

18.2.3 类、命名空间与作用域 

18.2.4 重载与命名空间 

18.3 多重继承与虚继承 

18.3.1 多重继承 

18.3.2 类型转换与多个基类 

18.3.3 多重继承下的类作用域 

18.3.4 虚继承 

18.3.5 构造函数与虚继承 

小结 

术语表 

**第19章 特殊工具与技术** 

19.1 控制内存分配 

19.1.1 重载new和delete 

19.1.2 定位new表达式 

19.2 运行时类型识别 

19.2.1 dynamic_cast运算符 

19.2.2 typeid运算符 

19.2.3 使用RTTI 

19.2.4 type_info类 

19.3 枚举类型 

19.4 类成员指针 

19.4.1 数据成员指针 

19.4.2 成员函数指针 

19.4.3 将成员函数用作可调用对象 

19.5 嵌套类 

19.6 union：一种节省空间的类 

19.7 局部类 

19.8 固有的不可移植的特性 

19.8.1 位域 

19.8.2 volatile限定符 

19.8.3 链接指示：extern "C" 

小结

