# GPU-Initiated On-Demand High-Throughput Storage Access in the BaM System Architecture

## 已有solution
### 什么是CPU-centric方法
由CPU进行控制，可以分为两种：1、对数据集进行编排。 2、用memory-mapped的方式。

### 什么是DRAM-only方法
使用CPU memory来拓展GPU memory。


## 挑战
### 挑战一：GPU应用缺乏快速发起按需存储访问的机制
**问题所在：** 
传统GPU访问存储数据，依赖CPU介入。

如：触发页错误（page fault）→ 由CPU处理 → 再将数据传给GPU。问题如下：

需要切换到内核态处理（OS page fault handler）；

CPU-GPU通信和同步代价高；

CPU软件栈效率不高，限制了I/O速度。

**BaM的解决方案：** 
构建一个软件缓存（software cache），驻留在GPU内存中，具备以下特性:

高度并发、可扩展、高吞吐；

利用现代GPU强大的并行性和原子操作能力；

能自动合并重复的存储访问请求，减少I/O开销；

提供数据重用机制，避免重复从SSD加载；

给应用程序“看起来像本地内存”的访问速度。

### 挑战二：GPU无法自主协调未命中缓存的数据请求（I/O操作），必须依赖CPU
**问题所在：**
如果数据未命中GPU缓存，仍需由CPU负责协调I/O操作；

但CPU的I/O路径存在限制：

线程并发度低；

驱动层和页错误处理效率低；

GPU不能高频发起I/O操作，极大浪费潜在并行能力。

**BaM的解决方案：**
引入一个GPU用户态的存储访问库，实现了以下功能：

在GPU内存中维护提交队列（SQ）和完成队列（CQ）；

GPU线程可直接发起存储请求（无须中断或系统调用）；

采用精细同步机制（fine-grained synchronization），

避免队列写入冲突；

减少“临界区”带来的串行化瓶颈；

支持海量线程同时并发I/O，实现高吞吐的存储访问。

