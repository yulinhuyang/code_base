**第1章 关于本书的对话** 

**第2章 操作系统介绍 **

2.1 虚拟化CPU 

2.2 虚拟化内存 

2.3 并发 

2.4 持久性 

2.5 设计目标 

2.6 简单历史 

2.7 小结 

 

**第1部分 虚拟化**

**第3章 关于虚拟化的对话** 

**第4章 抽象：进程** 

4.1 抽象：进程 

4.2 进程API 

4.3 进程创建：更多细节

4.4 进程状态 

4.5 数据结构

4.6 小结 

 

**第5章 插叙：进程API** 

5.1 fork()系统调用 

5.2 wait()系统调用 

5.3 最后是exec()系统调用 

5.4 为什么这样设计API 

5.5 其他API 

5.6 小结 

 



**第6章 机制：受限直接执行**

6.1 基本技巧：受限直接执行 

6.2 问题1：受限制的操作 

6.3 问题2：在进程之间切换 

6.4 担心并发吗 

6.5 小结 

 

**第7章 进程调度：介绍** 

7.1 工作负载假设 

7.2 调度指标 

7.3 先进先出（FIFO） 

7.4 最短任务优先（SJF） 

7.5 最短完成时间优先（STCF） 

7.6 新度量指标：响应时间 

7.7 轮转 

7.8 结合I/O 

7.9 无法预知 

7.10 小结 

 

**第8章 调度：多级反馈队列** 

8.1 MLFQ：基本规则 

8.2 尝试 #1：如何改变优先级 

8.3 尝试 #2：提升优先级 

8.4 尝试 #3：更好的计时方式 

8.5 MLFQ调优及其他问题 

8.6 MLFQ：小结 

 

**第9章 调度：比例份额** 

9.1 基本概念：彩票数表示份额 

9.2 彩票机制 

9.3 实现 

9.4 一个例子 

9.5 如何分配彩票 

9.6 为什么不是确定的 

9.7 小结

 

**第10章 多处理器调度（高级）** 

10.1 背景：多处理器架构 

10.2 别忘了同步 

10.3 最后一个问题：缓存亲和度 

10.4 单队列调度 

10.5 多队列调度 

10.6 Linux 多处理器调度 

10.7 小结 

 

**第11章 关于CPU虚拟化的总结对话** 

第12章 关于内存虚拟化的对话 

第13章 抽象：地址空间 

13.1 早期系统 

13.2 多道程序和时分共享 

13.3 地址空间 

13.4 目标 

13.5 小结 



**第14章 插叙：内存操作API **

14.1 内存类型 

14.2 malloc()调用 

14.3 free()调用 

14.4 常见错误 

14.5 底层操作系统支持 

14.6 其他调用 

14.7 小结 

 

**第15章 机制：地址转换** 

15.1 假设 

15.2 一个例子 

15.3 动态（基于硬件）重定位 

15.4 硬件支持：总结 

15.5 操作系统的问题 

15.6 小结 

 

 

**第16章 分段** 

16.1 分段：泛化的基址/界限 

16.2 我们引用哪个段 

16.3 栈怎么办 

16.4 支持共享 

16.5 细粒度与粗粒度的分段 

16.6 操作系统支持 

16.7 小结 

 

**第17章 空闲空间管理** 

17.1 假设 

17.2 底层机制 

17.3 基本策略 

17.4 其他方式 

17.5 小结 

 

 

**第18章 分页：介绍** 

18.1 一个简单例子 

18.2 页表存在哪里 

18.3 列表中究竟有什么 

18.4 分页：也很慢 

18.5 内存追踪 

18.6 小结 

 

 

**第19章 分页：快速地址转换（TLB）** 

19.1 TLB的基本算法 

19.2 示例：访问数组 

19.3 谁来处理TLB未命中 

19.4 TLB的内容 

19.5 上下文切换时对TLB的处理 

19.6 TLB替换策略 

19.7 实际系统的TLB表项 

19.8 小结 

 

**第20章 分页：较小的表** 

20.1 简单的解决方案：更大的页 

20.2 混合方法：分页和分段 

20.3 多级页表 

20.4 反向页表 

20.5 将页表交换到磁盘 

20.6 小结 

 

 

**第21章 超越物理内存：机制** 

21.1 交换空间 

21.2 存在位 

21.3 页错误 

21.4 内存满了怎么办 

21.5 页错误处理流程 

21.6 交换何时真正发生 

21.7 小结 

 

**第22章 超越物理内存：策略** 

22.1 缓存管理 

22.2 最优替换策略 

22.3 简单策略：FIFO 

22.4 另一简单策略：随机 

22.5 利用历史数据：LRU 

22.6 工作负载示例 

22.7 实现基于历史信息的算法 

22.8 近似LRU 

22.9 考虑脏页 

22.10 其他虚拟内存策略 

22.11 抖动 

22.12 小结 

 

 

**第23章 VAX/VMS虚拟内存系统** 

23.1 背景 

23.2 内存管理硬件 

23.3 一个真实的地址空间 

23.4 页替换 

23.5 其他漂亮的虚拟内存技巧 

23.6 小结 

 

**第24章 内存虚拟化总结对话** 



**第2部分 并发**

**第25章 关于并发的对话** 

**第26章 并发：介绍** 

26.1 实例：线程创建 

26.2 为什么更糟糕：共享数据 

26.3 核心问题：不可控的调度 

26.4 原子性愿望 

26.5 还有一个问题：等待另一个线程 

26.6 小结：为什么操作系统课要研究并发 

 

 

**第27章 插叙：线程API** 

27.1 线程创建 

27.2 线程完成 

27.3 锁 

27.4 条件变量 

27.5 编译和运行 

27.6 小结 

 

**第28章 锁** 

28.1 锁的基本思想 

28.2 Pthread锁 

28.3 实现一个锁 

28.4 评价锁 

28.5 控制中断 

28.6 测试并设置指令（原子交换） 

28.7 实现可用的自旋锁 

28.8 评价自旋锁 

28.9 比较并交换 

28.10 链接的加载和条件式存储指令 

28.11 获取并增加 

28.12 自旋过多：怎么办 

28.13 简单方法：让出来吧，宝贝 

28.14 使用队列：休眠替代自旋 

28.15 不同操作系统，不同实现 

28.16 两阶段锁 

28.17 小结 

 

**第29章 基于锁的并发数据结构** 

29.1 并发计数器 

29.2 并发链表 

29.3 并发队列 

29.4 并发散列表 

29.5 小结 

 

**第30章 条件变量** 

30.1 定义和程序 

30.2 生产者/消费者（有界缓冲区）问题 

30.3 覆盖条件 

30.4 小结 

 

**第31章 信号量** 

31.1 信号量的定义 

31.2 二值信号量（锁） 

31.3 信号量用作条件变量 

31.4 生产者/消费者（有界缓冲区）问题 

31.5 读者—写者锁 

31.6 哲学家就餐问题 

31.7 如何实现信号量 

31.8 小结 

 

**第32章 常见并发问题** 

32.1 有哪些类型的缺陷 

32.2 非死锁缺陷 

32.3 死锁缺陷 

32.4 小结 

 

**第33章 基于事件的并发（进阶）** 

33.1 基本想法：事件循环 

33.2 重要API：select()（或poll()） 

33.3 使用select() 

33.4 为何更简单？无须锁 

33.5 一个问题：阻塞系统调用 

33.6 解决方案：异步I/O 

33.7 另一个问题：状态管理 

33.8 什么事情仍然很难 

33.9 小结 

 

**第34章 并发的总结对话** 

**第3部分 持久性**

**第35章 关于持久性的对话** 

**第36章 I/O设备** 

36.1 系统架构 

36.2 标准设备 

36.3 标准协议 

36.4 利用中断减少CPU开销 

36.5 利用DMA进行更高效的数据传送 

36.6 设备交互的方法 

36.7 纳入操作系统：设备驱动程序 

36.8 案例研究：简单的IDE磁盘驱动程序 

36.9 历史记录 

36.10 小结 

 

**第37章 磁盘驱动器** 

37.1 接口 

37.2 基本几何形状 

37.3 简单的磁盘驱动器 

37.4 I/O时间：用数学 

37.5 磁盘调度 

37.6 小结 

 

**第38章 廉价冗余磁盘阵列（RAID）** 

38.1 接口和RAID内部 

38.2 故障模型 

38.3 如何评估RAID 

38.4 RAID 0级：条带化 

38.5 RAID 1级：镜像 

38.6 RAID 4级：通过奇偶校验节省空间 

38.7 RAID 5级：旋转奇偶校验 

38.8 RAID比较：总结 

38.9 其他有趣的RAID问题 

38.10 小结 

 

 

**第39章 插叙：文件和目录** 

39.1 文件和目录 

39.2 文件系统接口 

39.3 创建文件 

39.4 读写文件 

39.5 读取和写入，但不按顺序 

39.6 用fsync()立即写入 

39.7 文件重命名 

39.8 获取文件信息 

39.9 删除文件 

39.10 创建目录 

39.11 读取目录 

39.12 删除目录 

39.13 硬链接 

39.14 符号链接 

39.15 创建并挂载文件系统 

39.16 总结 

 

**第40章 文件系统实现** 

40.1 思考方式 

40.2 整体组织 

40.3 文件组织：inode 

40.4 目录组织 

40.5 空闲空间管理 

40.6 访问路径：读取和写入 

40.7 缓存和缓冲 

40.8 小结 

 

 

**第41章 局部性和快速文件系统** 

41.1 问题：性能不佳 

41.2 FFS：磁盘意识是解决方案 

41.3 组织结构：柱面组 

41.4 策略：如何分配文件和目录 

41.5 测量文件的局部性 

41.6 大文件例外 

41.7 关于FFS的其他几件事 

41.8 小结 

 

**第42章 崩溃一致性：FSCK和日志** 

42.1 一个详细的例子 

42.2 解决方案＃1：文件系统检查程序 

42.3 解决方案＃2：日志（或预写日志） 

42.4 解决方案＃3：其他方法 

42.5 小结 

 

**第43章 日志结构文件系统** 

43.1 按顺序写入磁盘 

43.2 顺序而高效地写入 

43.3 要缓冲多少 

43.4 问题：查找inode 

43.5 通过间接解决方案：inode映射 

43.6 检查点区域 

43.7 从磁盘读取文件：回顾 

43.8 目录如何 

43.9 一个新问题：垃圾收集 

43.10 确定块的死活 

43.11 策略问题：要清理哪些块，何时清理 

43.12 崩溃恢复和日志 

43.13 小结 

 

**第44章 数据完整性和保护** 

44.1 磁盘故障模式 

44.2 处理潜在的扇区错误 

44.3 检测讹误：校验和 

44.4 使用校验和 

44.5 一个新问题：错误的写入 

44.6 最后一个问题：丢失的写入 

44.7 擦净 

44.8 校验和的开销 

44.9 小结 

 

**第45章 关于持久的总结对话** 

**第46章 关于分布式的对话** 

**第47章 分布式系统** 

47.1 通信基础 

47.2 不可靠的通信层 

47.3 可靠的通信层 

47.4 通信抽象 

47.5 远程过程调用（RPC） 

47.6 小结 

 

**第48章 Sun的网络文件系统（NFS）** 

48.1 基本分布式文件系统 

48.2 交出NFS 

48.3 关注点：简单快速的服务器崩溃恢复 

48.4 快速崩溃恢复的关键：无状态 

48.5 NFSv2协议 

48.6 从协议到分布式文件系统 

48.7 利用幂等操作处理服务器故障 

48.8 提高性能：客户端缓存 

48.9 缓存一致性问题 

48.10 评估NFS的缓存一致性 

48.11 服务器端写缓冲的隐含意义 

48.12 小结 


**第49章 Andrew文件系统（AFS）** 

49.1 AFS版本1 

49.2 版本1的问题 

49.3 改进协议 

49.4 AFS版本2 

49.5 缓存一致性 

49.6 崩溃恢复 

49.7 AFSv2的扩展性和性能 

49.8 AFS：其他改进 

49.9 小结 




