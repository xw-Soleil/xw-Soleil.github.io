# L12：缓存一致性 Cache Coherence

> 多处理器共享内存背景、snoopy/directory 一致性协议、memory consistency 与 fence 指令笔记

> Rnh is my  Snoopy

## L12 Cache Coherence｜缓存一致性笔记

> ## 后面带页数的可以看 都检查过

> 来源：`L12 Cache Coherence(4).pptx`，共 90 页。
> 
> 整理方式：按“直觉 → 机制 → 例子 → tradeoff / 3C / AMAT 连接 → 工程 intuition → 考点”重组，而不是逐字翻译 PPT。
> 
> 本讲主线：**多核共享内存为什么会出错？硬件如何用 snoopy / directory 维护 coherence？coherence miss 为什么是第四个 C？coherence 和 memory consistency 到底有什么区别？**

---

### 0. Lecture Map｜本讲内容地图（Slides 1–3）

这节课在整个计算机系统抽象层次中处在 **architecture implementation / hardware architecture description** 这一层：上层程序看到的是共享变量和 load/store，底层真实硬件里却有多个 core、多个 private cache、共享 interconnect、memory controller。问题是：**多个 cache 里可能同时保存同一个 memory block 的副本，这些副本如何保持一致？**

本讲分成五块：

```text
1. Cache Coherence Issue       多核缓存一致性问题
2. Snoopy Cache                基于广播/总线监听的一致性协议
3. Directory Cache             基于目录的可扩展一致性协议
4. The Fourth Cache Miss       Coherence Miss：第四类 miss
5. Memory Consistency Model    内存一致性模型：跨地址访问顺序
```

一句话总览：

```text
Cache coherence 解决“同一个地址的值应该是谁”的问题；
Memory consistency 解决“不同地址的 load/store 顺序应该如何被其他线程观察到”的问题。
```

---

## 1. Multiprocessor Background｜为什么需要多核与共享内存（Slides 5–13）

### 1.1 为什么 2005 年左右转向多核？｜Power Wall → Multicore

PPT 的练习题问：从单处理器转向多处理器的主要原因是什么？

- I：**power wall** 出现，不能再靠更高 clock rate 和更高功耗换性能。
- II：用多个相对高效的处理器替代一个越来越低效的大处理器。
- III：OpenMP 让并行编程突然变简单。

考试角度答案：**ORANGE：I & II only**。

关键不是 OpenMP 本身，而是硬件 scaling 遇到功耗墙。过去靠频率提升获得性能：

```text
raise clock frequency → more performance
```

但频率和电压提高会让功耗与散热不可承受：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

P

</mi>

<mi>

o

</mi>

<mi>

w

</mi>

<mi>

e

</mi>

<mi>

r

</mi>

<mo>

≈

</mo>

<mi>

C

</mi>

<mo>

×

</mo>

<msup>
<mi>

V

</mi>

<mn>

2

</mn>
</msup>

<mo>

×

</mo>

<mi>

f

</mi>
</mrow>

<annotation encoding="application/x-tex">

Power \approx C \times V^2 \times f

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="mord,mathnormal">

o

</span>

<span className="mord,mathnormal" style="margin-right:0.0269em;">

w

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

er

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

≈

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

×

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.9474em;vertical-align:-0.0833em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.2222em;">

V

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8641em;">
<span style="top:-3.113em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">

2

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

×

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1076em;">

f

</span>
</span>
</span>
</span>
</span>

于是架构设计从“一个 core 越做越快”转向：

```text
many cores + parallelism + memory hierarchy + coherence protocol
```

**工程 intuition：** 多核不是免费加速。它把单核性能问题转化为并行编程、同步、缓存一致性、内存一致性和互连扩展问题。

---

### 1.2 多处理器的三个核心问题｜Share, Coordinate, Scale

PPT 给出三个问题：

```text
Q1: How do they share data?       多个处理器如何共享数据？
Q2: How do they coordinate?       多个处理器如何协调顺序？
Q3: How many processors supported? 系统可以扩展到多少处理器？
```

这三个问题正好对应本讲后续：

<table>
<thead>
  <tr>
    <th>
      问题
    </th>
    
    <th>
      硬件/软件机制
    </th>
    
    <th>
      本讲连接
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      共享数据
    </td>
    
    <td>
      shared memory / message passing
    </td>
    
    <td>
      Slides 7–12
    </td>
  </tr>
  
  <tr>
    <td>
      协调顺序
    </td>
    
    <td>
      locks, synchronization, fences
    </td>
    
    <td>
      Slides 78–90
    </td>
  </tr>
  
  <tr>
    <td>
      扩展规模
    </td>
    
    <td>
      snoopy bus vs directory network
    </td>
    
    <td>
      Slides 27–59
    </td>
  </tr>
</tbody>
</table>

一句话：**共享内存让编程模型更像单机，但硬件必须付出 coherence + consistency 的代价。**

---

### 1.3 UMA vs NUMA｜物理内存组织

#### UMA / SMP｜统一内存访问

UMA（Uniform Memory Access）也叫 SMP（Symmetric Multiprocessor）。所有处理器到主存的访问距离基本相同。

```text
CPU0 ─ Cache ┐
CPU1 ─ Cache ├── Shared Interconnect ── Main Memory
CPU2 ─ Cache ┘
```

特点：

- 所有内存位置访问延迟相近。
- 编程模型简单，适合 shared memory。
- 内存带宽是集中瓶颈。
- 处理器数量增多时，所有 core 都抢同一个内存系统，扩展性差。

**tradeoff：** UMA 简单，但 bandwidth 不随 core 数线性增长。

---

#### NUMA｜非统一内存访问

NUMA（Non-Uniform Memory Access）中，每个 node 有自己的本地 memory。访问本地 memory 快，访问远程 memory 慢。

```text
Node0: CPU + Cache + Local Memory
Node1: CPU + Cache + Local Memory
Node2: CPU + Cache + Local Memory
Nodes connected by interconnect
```

特点：

- 若大多数访问是本地访问，总 memory bandwidth 可随节点数增加。
- 远程访问 latency 更高。
- 软件/OS/编译器要尽量保证 data locality。

**工程 intuition：** NUMA 把“一个内存瓶颈”拆成“多个本地内存 + 远程访问代价”。性能好不好取决于数据放在哪里。

---

### 1.4 Shared Memory vs Message Passing｜通信模型

#### Shared Memory｜共享地址空间

共享内存中，不同处理器可以通过相同地址访问同一个变量。

```c
// Producer
flag = 0;
a = 10;
flag = 1;

// Consumer
while (!flag) {}
x = a * y;
```

优点：

- 编程看起来像普通 load/store。
- 支持细粒度共享。
- 可用 lock / critical section 做同步。
- 单一 OS image 更自然。

缺点：

- 硬件要维护 cache coherence。
- 程序员仍然要理解 synchronization 和 memory consistency。

---

#### Message Passing｜消息传递

消息传递中，每个处理器有自己的地址空间，通信通过 send / receive 显式完成。

```c
// Producer
send(p2, a, label);

// Consumer
receive(p1, b, label);
x = b * y;
```

优点：

- 数据移动显式，coherence 负担小。
- 更适合大规模 cluster。

缺点：

- 编程更复杂。
- 细粒度共享开销很高。

**对比总结**

<table>
<thead>
  <tr>
    <th>
      模型
    </th>
    
    <th>
      通信方式
    </th>
    
    <th>
      同步方式
    </th>
    
    <th>
      优点
    </th>
    
    <th>
      代价
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      Shared Memory
    </td>
    
    <td>
      共享变量
    </td>
    
    <td>
      lock / fence / atomic
    </td>
    
    <td>
      编程直观，细粒度共享
    </td>
    
    <td>
      coherence + consistency 成本
    </td>
  </tr>
  
  <tr>
    <td>
      Message Passing
    </td>
    
    <td>
      send / receive
    </td>
    
    <td>
      消息隐式同步
    </td>
    
    <td>
      可扩展，通信显式
    </td>
    
    <td>
      编程复杂，细粒度共享贵
    </td>
  </tr>
</tbody>
</table>

---

### 1.5 Bus Management｜总线为什么适合 snoopy？

Bus 是共享通信线路。任意时刻通常只有一个 master 发起事务，其他 slave 可以观察地址和控制信号。

```text
Master requests bus → Bus controller grants → Master drives address/data/control
Other caches observe transaction → decide whether to respond / invalidate / write back
```

这就是 snoopy cache 的基础：**所有 cache 都能“听见”总线上发生的读写请求。**

**tradeoff：** 总线天然提供广播和顺序，但带宽有限，无法扩展到很多 core。

---

## 2. Cache Coherence Issue｜缓存一致性问题（Slides 14–26）

### 2.1 并行 sum 代码为什么会出问题？

PPT 给出代码：

```c
sum = 0;
begin parallel
for (i = 1; i <= 2; i++) {
    lock(id, myLock);
    sum = sum + a[i];
    unlock(id, myLock);
}
end parallel
print sum;
```

假设：

```text
a[1] = 3
a[2] = 7
expected sum = 10
```

直觉上，加锁后应该正确。但 PPT 引出两个层次的问题：

```text
1. lock 本身如何正确实现？
2. 即使临界区互斥，多个 cache 中的 sum 副本是否一致？
```

注意：真实程序中 lock 通常会通过 atomic operation + memory ordering 保证同步；PPT 的动画主要想说明：**如果没有 cache coherence，普通 shared variable 会在不同 cache 中产生多个不一致副本。**

---

### 2.2 Cache-Coherence Problem 的本质

缓存一致性问题的根源：

```text
同一个 memory address 的 block
可能同时存在于多个 private cache 中。
如果一个 processor 写了它，其他 processor 的旧副本怎么办？
```

以 `Sum` 为例：

```text
Initial: Memory[Sum] = 0, all caches empty
P1 reads Sum → P1 cache has Sum = 0, valid
P2 reads Sum → P2 cache has Sum = 0, valid
P1 writes Sum = 3 → P1 cache has Sum = 3, dirty
P2 writes Sum = 7 → P2 cache has Sum = 7, dirty
P1 reads Sum → P1 may still read Sum = 3
```

这时系统中可能同时存在：

```text
P1 cache: Sum = 3, dirty
P2 cache: Sum = 7, dirty
Memory:   Sum = 0 or stale value
```

这违反了 shared memory 的直觉：程序员以为 `Sum` 是一个变量，但硬件里它变成了多个 private copies。

---

### 2.3 Write-Through 为什么也不够？

PPT 问：使用 write-through cache 是否能解决？答案：**不能根本解决。**

Write-through 只保证：

```text
processor 写 cache 时，也把新值写到 memory
```

但它不保证：

```text
其他 cache 中已有的旧副本会自动失效或更新
```

例如：

```text
P1 cache has Sum = 3
P2 writes Sum = 7 and write-through to memory
Memory becomes 7
P1 later reads Sum
```

如果 P1 的 cache line 仍然 valid，P1 可能仍然读到旧的 `3`。所以 write-through 只能改善 memory freshness，不能维护 cache-to-cache coherence。

**关键点：** coherence 的核心不是“memory 是否最新”，而是“所有 cache 对同一地址是否遵循一致的读写规则”。

---

### 2.4 如果没有 cache 或 Sum 不可缓存呢？

如果 `Sum` 不可缓存，所有访问都直接去 shared memory，那么 stale cache copy 问题消失。但这不等于并行程序一定正确：

- 仍然需要 lock / atomic 来保证 `sum = sum + a[i]` 的 read-modify-write 不被交错破坏。
- 仍然需要 memory ordering 保证 lock/unlock 对临界区内读写的顺序。
- 性能会很差，因为每次访问都去主存。

**tradeoff：** 不缓存共享变量可以回避 coherence，但牺牲了 memory hierarchy 的核心性能优势。

---

### 2.5 Shared-Memory Multiprocessor 的矛盾

多处理器系统需要 cache，因为主存 bandwidth 是瓶颈：

```text
每个 core 有 private cache → 减少主存访问 → 性能提高
```

但 private cache 也带来 coherence problem：

```text
private copies → possible stale values → shared memory abstraction broken
```

以 `Memory[1000]` 为例：

```text
P1 reads Memory[1000] = 20 → P1 cache has 20
P2 reads Memory[1000] = 20 → P2 cache has 20
P0 writes Memory[1000] = 40
```

问题：P1/P2 cache 里的 20 是否还有效？如果有效，它们之后读到的就是旧值。硬件必须做下面两类事情之一：

```text
Invalidate: 让 P1/P2 的旧副本失效
Update:     把新值广播给 P1/P2
```

现实中更常用的是 **write invalidate**，因为 bandwidth 更省。

---

## 3. Snoopy Cache｜监听式缓存一致性（Slides 27–41）

### 3.1 Snoopy 的核心思想

Snoopy cache 的思想：

```text
所有 cache 监听 shared interconnect / bus 上的 memory transactions。
一旦看到别的 processor 对自己缓存的 line 发起读/写请求，
就根据协议改变本地 line state，必要时提供数据或使副本失效。
```

也就是：

```text
processor 自己访问 cache
cache 同时 snoop 别人的 bus transaction
```

所以 snoopy cache 的 tag 通常需要额外 read port，或者用别的结构避免 CPU 访问与 snoop 访问冲突。

---

### 3.2 Write Invalidate vs Write Update｜写无效 vs 写更新

#### Write Update｜写广播

每次写共享数据时，把新值广播给其他 cache。

优点：

- 其他处理器之后读该数据时 latency 小，因为已经更新。

缺点：

- 写频繁时产生大量 bandwidth 消耗。
- 其他处理器可能根本不会再读这个值，广播浪费。

---

#### Write Invalidate｜写无效

写之前，让其他 cache 中同一 line 的副本 invalid。

```text
writer obtains exclusive ownership
other copies become Invalid
writer can then write locally
```

优点：

- 节省 bandwidth。
- writer 连续多次写同一 line 时，不需要每次广播新值。

缺点：

- 其他 processor 下次读会 miss，需要重新取数据。

**工程 intuition：** bandwidth 比 latency 更珍贵，所以多数 multiprocessor 使用 write invalidate。

---

### 3.3 Snoopy Protocol 的基本动作

PPT 给出两个关键规则：

#### Write Miss

在执行写之前，该地址在所有其他 cache 中必须 invalid。

```text
Write miss / write intent
→ broadcast invalidation
→ collect / assume invalidation done depending bus protocol
→ writer obtains line exclusively
→ perform write
```

#### Read Miss

如果某个 cache 里有 dirty copy，则不能直接从 memory 读，因为 memory 可能 stale。

```text
Read miss
→ snoop other caches
→ if another cache has Modified/dirty copy:
      dirty owner supplies data or writes back
→ requester receives latest data
```

这里产生了 **intervention** 的概念：dirty cache 必须介入，防止 memory 返回旧数据。

---

### 3.4 MOESI States｜五种常见 cache line 状态

MOESI 是一类通用 cache coherence state 的集合：

<table>
<thead>
  <tr>
    <th>
      State
    </th>
    
    <th>
      中文
    </th>
    
    <th>
      含义
    </th>
    
    <th>
      Memory 是否最新
    </th>
    
    <th>
      其他 cache 是否可有副本
    </th>
    
    <th>
      本 processor 写是否需要通知别人
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      M Modified
    </td>
    
    <td>
      已修改
    </td>
    
    <td>
      本 cache 有最新 dirty data
    </td>
    
    <td>
      否
    </td>
    
    <td>
      否
    </td>
    
    <td>
      不需要，已经独占
    </td>
  </tr>
  
  <tr>
    <td>
      O Owned
    </td>
    
    <td>
      所有者
    </td>
    
    <td>
      本 cache 有最新 data，其他 cache 可有 shared 副本
    </td>
    
    <td>
      否
    </td>
    
    <td>
      是，其他为 S
    </td>
    
    <td>
      写仍需先获得独占
    </td>
  </tr>
  
  <tr>
    <td>
      E Exclusive
    </td>
    
    <td>
      独占未改
    </td>
    
    <td>
      本 cache 独占且 clean
    </td>
    
    <td>
      是
    </td>
    
    <td>
      否
    </td>
    
    <td>
      可静默写成 M
    </td>
  </tr>
  
  <tr>
    <td>
      S Shared
    </td>
    
    <td>
      共享
    </td>
    
    <td>
      多个 cache 可有 clean copy
    </td>
    
    <td>
      是
    </td>
    
    <td>
      是
    </td>
    
    <td>
      写前要 invalidate others
    </td>
  </tr>
  
  <tr>
    <td>
      I Invalid
    </td>
    
    <td>
      无效
    </td>
    
    <td>
      本 cache 没有有效副本
    </td>
    
    <td>
      不适用
    </td>
    
    <td>
      不适用
    </td>
    
    <td>
      访问会 miss
    </td>
  </tr>
</tbody>
</table>

一句话记忆：

```text
M: 我改过，只有我有，memory 旧。
E: 只有我有，但没改，memory 新。
S: 大家可能都有，memory 新。
O: 我负责最新数据，别人也有旧? 不，是 shared clean-looking copies，但 memory 旧。
I: 没有。
```

---

### 3.5 MSI Protocol｜最基本的三状态协议

MSI 只有三种状态：

```text
M = Modified
S = Shared
I = Invalid
```

每条 cache line 除了 tag/data，还要有 state bits：

```text
| state bits | address tag | data block |
```

#### MSI 状态转换：以 P1 的某条 line 为视角

<table>
<thead>
  <tr>
    <th>
      当前状态
    </th>
    
    <th>
      事件
    </th>
    
    <th>
      下一个状态
    </th>
    
    <th>
      动作
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      I
    </td>
    
    <td>
      P1 read miss
    </td>
    
    <td>
      S
    </td>
    
    <td>
      从 memory 或其他 cache 获取 line
    </td>
  </tr>
  
  <tr>
    <td>
      I
    </td>
    
    <td>
      P1 write miss
    </td>
    
    <td>
      M
    </td>
    
    <td>
      获取 line，invalidate 其他副本
    </td>
  </tr>
  
  <tr>
    <td>
      S
    </td>
    
    <td>
      P1 read
    </td>
    
    <td>
      S
    </td>
    
    <td>
      hit
    </td>
  </tr>
  
  <tr>
    <td>
      S
    </td>
    
    <td>
      P1 write / intent to write
    </td>
    
    <td>
      M
    </td>
    
    <td>
      发送 invalidation，让其他 shared copies 失效
    </td>
  </tr>
  
  <tr>
    <td>
      S
    </td>
    
    <td>
      other processor intent to write
    </td>
    
    <td>
      I
    </td>
    
    <td>
      P1 副本失效
    </td>
  </tr>
  
  <tr>
    <td>
      M
    </td>
    
    <td>
      P1 read/write
    </td>
    
    <td>
      M
    </td>
    
    <td>
      hit，本地读写
    </td>
  </tr>
  
  <tr>
    <td>
      M
    </td>
    
    <td>
      other processor read
    </td>
    
    <td>
      S
    </td>
    
    <td>
      P1 write back / supply data，自己降级为 S
    </td>
  </tr>
  
  <tr>
    <td>
      M
    </td>
    
    <td>
      other processor intent to write
    </td>
    
    <td>
      I
    </td>
    
    <td>
      P1 write back / supply data，自己失效
    </td>
  </tr>
</tbody>
</table>

状态机直觉：

```text
I --read miss--> S
I --write miss--> M
S --own write intent--> M
S --other write intent--> I
M --own read/write--> M
M --other read--> S + writeback/supply
M --other write intent--> I + writeback/supply
```

---

### 3.6 MSI 的关键 invariant｜M 状态的排他性

PPT 强调：

```text
If one cache has a line in M state,
no other cache can have a valid copy of that line.
```

这条 invariant 非常重要。它保证：

```text
同一个地址不会同时存在两个不同的最新值。
```

如果没有这个 invariant，就会回到前面的 `Sum=3` 和 `Sum=7` 同时存在的问题。

---

### 3.7 MESI｜为什么加入 E 状态？

MESI 在 MSI 上增加 E（Exclusive but unmodified）。

```text
M: Modified exclusive
E: Exclusive but unmodified
S: Shared
I: Invalid
```

#### E 状态的意义

如果一个 processor read miss 某个 line，并且 snoop 发现没有其他 cache 拥有副本，那么这个 line 可以进入 E，而不是 S。

```text
I --read miss, not shared--> E
E --own read--> E
E --own write--> M   // silent upgrade, no bus transaction
```

相比 MSI，MESI 优化了 private data：

```text
private data read into cache 后，第一次写不需要发 invalidation。
```

因为既然没有其他副本，就不需要通知别人。

#### E 状态还能减少 writeback

E 是 clean exclusive。替换时不需要写回 memory，因为 memory 本来就是最新的。

**tradeoff：** MESI 需要判断 read miss 时是否 shared，因此硬件更复杂；但它显著减少 private data 的不必要 bus traffic。

---

### 3.8 Owner State｜O 状态为什么存在？

O 状态可以看作 Shared 的一个变体：

```text
Owner cache has latest data.
Other caches may hold shared copies.
Memory may be stale.
Owner supplies data on read miss.
```

没有 O 状态时，如果 M line 被别人读，通常要 write back 到 memory，然后双方变 S。O 状态允许 owner 不必立刻把 memory 更新到最新，而是由 owner 负责向其他请求者提供数据。

**tradeoff：** 减少 memory traffic，但协议状态更复杂，需要追踪谁是 owner。

### 3.10 两级 Snoop Cache 优化｜Inclusive L2

现代处理器常有

```text
small L1 + larger L2/L3
```

如果 L2 是 inclusive：

```text
L1 中的 line 必须也存在于 L2 中
```

那么 snooper 可以只 snoop L2 tag：

```text
L2 miss → L1 一定没有 → 不必打扰 L1
L2 invalidation hit → 再检查/invalid L1
```

优点：

- snoop traffic 不直接占用 CPU-L1 端口。
- 降低 L1 hit path 干扰。

代价

- inclusive cache 会带来额外容量压力。
- L2 eviction 可能需要反向 invalid L1。
- 同一地址同时被 CPU-L1 和 L2-bus 访问时仍需要 interlock。

---

## 4. Directory Cache｜目录缓存一致性（Slides 42–59）

### 4.1 Snoopy 为什么不可扩展？

Snoopy/broadcast 的问题：

```text
任何 processor cache miss / write intent
都要广播给所有 cache。
```

随着 core 数增加，瓶颈来自：

```text
1. bus / interconnect bandwidth 总线通信带宽
2. snoopy tag bandwidth snoopy 标签带宽——Snooper 要不断访问 cache tag
```

PPT 的 insight：

```text
Most snoops do not find a match.
```

也就是大多数广播其实没有必要，因为大多数其他 cache 并没有这条 line。

**Snoopy 协议靠广播和所有 cache 监听来保持一致性，小规模系统很好用；但处理器数量变多后，会受到总线带宽和 tag 检查带宽限制，因为大多数广播检查其实都查不到匹配项，所以后面要引入 Directory 协议来提高可扩展性。**

### 4.2 Directory 的核心思想

Directory protocol 为每个 memory line 维护 directory information：

```text
line state + sharer vector / owner id
```

当一个 cache miss 发生时，不广播给所有 cache，而是：

```text
requester → home directory
home directory checks who has copies
only contact actual sharers / owner
```

直觉：

```text
Snoopy:  你喊一嗓子，所有人都听。
Directory: 你先查登记表，只找相关的人。
```

**tradeoff：** directory 减少无效广播，适合大规模系统；但需要额外 directory storage、更多消息步骤、复杂 transient states。

---

### 4.3 Directory Protocol 的系统结构

典型结构：

```text
CPU + Cache nodes
Directory Controller + DRAM Bank nodes
Interconnection Network
```

每个 cache line 有：

```text
Cache side: tag + data + cache state
Memory side: data + directory state + sharer vector
```

假设网络：

```text
reliable network
FIFO messages between a given source-destination pair
```

但即使网络可靠，delay 仍然存在，因此协议必须处理并发事务、乱序到达、pending 状态。

---

### 4.4 Cache States in Directory Protocol｜缓存侧状态

PPT 给出每条 cache line 四种状态：

<table>
<thead>
  <tr>
    <th>
      Cache State
    </th>
    
    <th>
      等价理解
    </th>
    
    <th>
      含义
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      C-invalid
    </td>
    
    <td>
      Nothing
    </td>
    
    <td>
      本 cache 没有该数据
    </td>
  </tr>
  
  <tr>
    <td>
      C-shared
    </td>
    
    <td>
      Sh
    </td>
    
    <td>
      数据在本 cache，其他节点也可能有；memory 有效
    </td>
  </tr>
  
  <tr>
    <td>
      C-modified
    </td>
    
    <td>
      Ex
    </td>
    
    <td>
      本 cache 独占且 modified；memory 没有最新数据
    </td>
  </tr>
  
  <tr>
    <td>
      C-transient
    </td>
    
    <td>
      Pending
    </td>
    
    <td>
      请求已发出，回复未收到，处于协议中间态
    </td>
  </tr>
</tbody>
</table>

注意：directory 协议中 transient state 很重要，因为 network delay 让“请求发出”和“状态完成”之间存在时间窗口。

---

### 4.5 Home Directory States｜目录侧状态

PPT 给出 memory line 的 directory states：

<table>
<thead>
  <tr>
    <th>
      Directory State
    </th>
    
    <th>
      含义
    </th>
    
    <th>
      Memory 是否最新
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      R(dir)
    </td>
    
    <td>
      line 被 <code code="dir">
        dir
      </code>
      
       中的节点 shared；若 <code code="dir=ε">
        dir=ε
      </code>
      
      ，表示无人缓存
    </td>
    
    <td>
      是
    </td>
  </tr>
  
  <tr>
    <td>
      W(id)
    </td>
    
    <td>
      line 被节点 <code code="id">
        id
      </code>
      
       独占修改
    </td>
    
    <td>
      否
    </td>
  </tr>
  
  <tr>
    <td>
      TR(dir)
    </td>
    
    <td>
      transient read/shared 状态，等待 invalidation ACK
    </td>
    
    <td>
      取决于事务
    </td>
  </tr>
  
  <tr>
    <td>
      TW(id)
    </td>
    
    <td>
      transient writeback/ownership transfer 状态，等待 modified owner 更新 memory/home
    </td>
    
    <td>
      否或 pending
    </td>
  </tr>
</tbody>
</table>

一句话：

```text
Directory 是每条 memory line 的 summary state。
它不保存所有 cache 的完整状态，但保存足够信息来找 sharers / owner。
```

---

### 4.6 Snoopy vs Directory｜序列化点不同

<table>
<thead>
  <tr>
    <th>
      维度
    </th>
    
    <th>
      Snoopy Coherence
    </th>
    
    <th>
      Directory Coherence
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      全局状态
    </td>
    
    <td>
      分散在所有 cache state 中，没有集中摘要
    </td>
    
    <td>
      directory 保存 summary state
    </td>
  </tr>
  
  <tr>
    <td>
      通信方式
    </td>
    
    <td>
      广播 / snoop 所有事务
    </td>
    
    <td>
      点对点，只联系 sharers / owner
    </td>
  </tr>
  
  <tr>
    <td>
      序列化点
    </td>
    
    <td>
      bus / ring 提供总顺序
    </td>
    
    <td>
      directory controller 提供 per-line ordering
    </td>
  </tr>
  
  <tr>
    <td>
      扩展性
    </td>
    
    <td>
      适合小规模 bus-based SMP
    </td>
    
    <td>
      适合大规模 scalable network
    </td>
  </tr>
  
  <tr>
    <td>
      主要瓶颈
    </td>
    
    <td>
      bus bandwidth + snoop tag bandwidth
    </td>
    
    <td>
      directory storage + message latency + protocol complexity
    </td>
  </tr>
</tbody>
</table>

关键区别：

```text
Snoopy: bus order serializes transactions.
Directory: home directory serializes transactions for a line.
```

注意：directory 对每条 line 能排序，但不自动保证整个系统对所有地址都是 sequential consistency。

---

### 4.7 Read Miss Flow｜读 miss 流程

PPT 的 read miss 场景：directory state 是 R，已有 0 个或多个 sharers。

流程：

```text
1. CPU load request reaches cache.
2. Cache load miss.
3. Cache sends ShReq to directory.
4. Directory receives ShReq.
5. Directory checks line state: R(dir).
6. Directory sets requester bit in sharer vector.
7. Directory sends ShRep with cache line data.
8. ShRep arrives at cache.
9. Cache updates tag/data/state and returns data to CPU.
```

状态变化：

```text
Directory: R(dir) → R(dir ∪ {requester})
Requester cache: I/Pending → S
```

如果 memory 是最新的，directory 直接从 DRAM bank 返回 data。

---

### 4.8 Write Miss to Shared Line｜对 shared line 写 miss

场景：store miss，directory state 为 R(dir)，已有多个 sharers。

目标：写者必须拿到 exclusive ownership。

流程：

```text
1. CPU store reaches cache.
2. Cache store miss.
3. Cache sends ExReq to directory.
4. Directory receives ExReq.
5. Directory sees state R(dir), with sharers.
6. Directory sends InvReq to every sharer.
7. Each sharer receives InvReq.
8. Sharer invalidates local line and sends InvRep.
9. Directory receives InvRep and clears sharer bits.
10. When all sharers invalidated, directory sends ExRep to requester.
11. ExRep reaches requester cache.
12. Requester installs line and performs store.
```

状态变化：

```text
Old sharers: S → I
Requester:   I/Pending → M
Directory:   R(dir) → TR(dir) → W(requester)
```

**为什么要等所有 ACK？**

因为如果某个旧 sharer 还没 invalid，它可能继续读旧值。写者在所有旧副本失效前不能真正认为自己独占。

---

### 4.9 Directory Structure｜目录结构和共享向量

Directory information 对每个 memory line 保存：

```text
line state bits
sharing vector: one bit per processor
```

例如 3 个 processor：

```text
Dir state: 01 = shared
Sharer vector: [1, 0, 1]
```

表示：

```text
P0 and P2 have shared copies.
Memory value is valid.
P1 does not have this line.
```

如果 state 是 modified：

```text
Dir state: 10 = modified
Sharer vector can encode owner id, e.g. [0,1,0]
```

表示：

```text
P1 has the only modified copy.
Memory is stale.
```

---

### 4.10 四个 Directory 操作例子

#### Case A：load with no sharers

```text
Directory: not cached, sharer vector empty
P0 load miss → ShReq
Directory returns value from memory
P0 enters Shared
Directory marks P0 as sharer
```

结果：

```text
Memory valid
P0: S
Directory: R({P0})
```

---

#### Case B：load with sharers

```text
Directory: R({P0})
P1 load miss → ShReq
Directory returns memory value
Directory adds P1 to sharer vector
```

结果：

```text
P0: S
P1: S
Directory: R({P0, P1})
```

多个 processor 可以同时读同一 line。

---

#### Case C：store with sharers

```text
Directory: R({P0, P1})
P2 store miss → ExReq
Directory sends InvReq to P0 and P1
P0/P1 invalidate and ACK
Directory sends ExRep to P2
P2 writes and becomes M
```

结果：

```text
P0: I
P1: I
P2: M
Directory: W(P2)
Memory stale
```

这就是 directory 版 write invalidate。

---

#### Case D：load with owner

```text
Directory: W(P0)
P1 load miss → ShReq
Directory forwards request to owner P0
P0 supplies latest data / ACK
P0 downgrades from M to S or O depending protocol
P1 becomes S
Directory updates sharer/owner state
```

核心原因：memory stale，所以不能直接从 memory 返回数据。

---

下面这几页从 **Directory 协议的工程细节**，转到 **一致性对性能的影响**，最后引出 **第 4 类 cache miss：coherence miss**。

---

## 第 57 页：目录操作注意事项

这一页讲的是：Directory 协议不是“查个表就结束”，还需要处理很多确认消息和异常情况。

### 写共享行时，必须等所有 invalid ACK

如果某条 cache line 现在被多个处理器共享：

```text
P0: A, Shared
P1: A, Shared
P2: A, Shared
```

现在 P3 要写 A。Directory 不能直接允许 P3 写，而是要先通知 P0、P1、P2：

```text
你们的 A 副本都失效
```

然后必须收到它们的确认：

```text
P0 -> Directory: ACK
P1 -> Directory: ACK
P2 -> Directory: ACK
```

只有全部 ACK 收齐，P3 才能获得独占写权限。课件也明确说，对多个 sharers 的写操作，需要在实际写之前收集并计数所有 invalidation ACK。

---

### 复杂状态变化也要确认

不只是 invalidate 需要确认。只要涉及状态变化，比如：

```text
Shared -> Modified
Modified owner 转移
Directory 等待某个 cache 回写数据
```

Directory 都需要确认消息来判断：

```text
这个 load/store 到底完成了吗？
状态能不能更新？
```

否则 Directory 可能误以为某个处理器已经失效或已经拥有数据，导致一致性错误。

---

### 需要临时状态 transient states

Directory 协议中有大量“请求已经发出，但回复还没回来”的中间阶段。

比如：

```text
P3 请求写 A
Directory 已经发出 invalidate
但 P0/P1/P2 还没全部 ACK
```

这时不能简单说 A 是 Shared，也不能说 A 已经 Modified by P3。它处于一个 **pending / transient** 状态。

所以前面讲的 `TR(dir)`、`TW(id)` 就是为这种情况服务的。

---

### 缓冲区满时需要 NACK

`NACK` = Negative Acknowledge，否定确认。

意思是：

```text
我现在处理不了你的请求，请你稍后重试。
```

例如 Directory 或 cache 的请求队列满了，不能继续收消息，就可能发 NACK。课件提到，和总线类似，当缓冲区溢出时需要引入 NACK。

---

### Directory 适合“少数处理器共享同一数据”

Directory 的优势是避免广播。

如果一条数据只被少数处理器共享，Directory 只通知相关处理器，效率高。

但如果一条数据几乎被所有处理器共享：

```text
P0, P1, P2, ... P127 都有副本
```

那 Directory 还是要给很多人发 invalidate，反而不一定比广播好。

所以这一页最后的意思是：

> **Directory 适合共享者较少的情况；如果所有人都在共享同一数据，广播可能更简单。**

---

## 第 58 页：实现困难举例

这一页讲两个很具体的坑：**操作必须按顺序处理**。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L12-CacheCoherence-01.webp)

---

### 例子 1：P0 本地必须按顺序处理事务

课件流程大概是：

```text
1. P0 发送 read request for line A
2. P1 发送 read exclusive request for line A，在 directory 等待
3. Directory 回复 P0 的 read，并设置 sharing vector，但消息延迟
4a/4b. Directory 同时回复 P0 和 P1：
       通知 P0 失效，给 P1 新 owner 权限
5. P0 invalidates line A and sends ACK
```

问题在于：

```text
第 3 步的旧 read reply 可能很晚才到达 P0
```

如果 P0 已经根据第 4 步把 A 失效了，结果第 3 步的旧数据又到达 P0，被放进 cache，那么 P0 又重新拥有了一个过期副本。

这就错了。

**解决方案：P0 必须本地顺序处理事务。**

也就是：

```text
如果 P0 对 A 有一个 read 请求还挂起，
它不能随便处理后面和 A 相关的 invalidate / owner 转移。
```

课件原文也指出，当第 3 步最终到达 P0 时，line A 的过期值可能被放入缓存；解决方法是 P0 必须本地顺序处理事务。

---

### 例子 2：Directory 自己也必须按顺序处理事务

第二个例子大概是：

```text
1. P1 发送 read exclusive request for line A
2. Directory 转发请求给 P0，因为 P0 是 owner
3a. P0 把数据发给 P1
3b. P0 给 Directory 发 ACK，但 ACK 延迟
4. P1 收到数据后认为 read exclusive 完成；
   后来 P1 替换这条 line，把更新值写回内存
```

问题是：

```text
第 4 步写回内存可能先到 Directory
第 3b 步 ACK 反而后到
```

Directory 如果没处理好，就可能：

```text
先接受 P1 写回并覆盖内存
后收到 3b，又认为所有权转移刚刚完成，P1 还是 owner
```

状态就乱了。

**解决方案：Directory 必须顺序处理事务。**

特别是：

```text
当 ownership transfer 还没完成时，
Directory 不能随便响应后来的 replacement/writeback。
```

这页核心就是：

> **Directory 协议的难点不在“状态名字”，而在消息延迟和乱序到达时，如何保证同一条 cache line 的事务顺序不乱。**

---

## 第 59 页：目录的开销

这一页讲 Directory 的缺点：**目录信息本身也要占空间。**

假设系统有：

```text
128 个处理器
256GB 内存
每个处理器 1MB L2 cache
64B cache line
```

### 朴素目录：每条内存行都放一个 sharing vector

128 个处理器意味着每条内存行要一个 128-bit sharing vector：

```text
128 bit = 16 bytes
```

再加 3 bit 状态，约等于 16B。

每条 cache line 是 64B，所以目录开销是：

```text
16 / 64 = 0.25 = 25%
```

256GB 内存对应的目录开销就是：

```text
0.25 × 256GB = 64GB
```

也就是说，光目录就要 64GB，太大了。课件给出的计算正是：128 位共享向量加状态约 16 字节，每行 16/64 = 25%，总计 64GB 内存开销。

---

### 解决方案：Cached Directories

观察：不是所有内存行都会同时被 cache。

整个系统一共有：

```text
128 个处理器 × 每个 1MB cache = 128MB cache
```

如果 cache line 是 64B，那么最多实际被缓存的行数是：

```text
128MB / 64B = 2M lines
```

所以可以只给 **活跃缓存行** 建目录，而不是给所有内存行都建目录。

这就叫 **cached directory**。

但是这样目录项需要额外保存 tag，因为它不是固定跟着每条内存行放了。

每个活跃 cache line 的目录开销大约是：

```text
tag 8B + directory 16B = 24B
24 / 64 = 37.5%
```

但总量只对应 2M 条活跃行：

```text
0.375 × 2M × 64B = 768KB
```

所以总开销从 64GB 降到约 768KB。课件也给出这个结论：只维护 actively cached lines 时，总开销约 768KB。

---

## 第 60 页：过渡页：缓存未命中的第四个 C

这一页基本是章节过渡：

```text
The Fourth Cache Miss
缓存未命中的第四个 C
```

前面你学过传统 3C：

```text
Compulsory miss
Capacity miss
Conflict miss
```

现在多处理器系统中又出现一类新的 miss：

```text
Coherence miss
```

它不是因为 cache 太小，也不是因为映射冲突，而是因为 **别的处理器的一致性操作让你的 cache line 失效了**。

---

## 第 61 页：SMP 性能

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L12-CacheCoherence-02.webp)

SMP = Symmetric Multiprocessor，对称多处理器。

这一页讲：多处理器里的 cache 性能不只取决于单核 cache miss，还取决于处理器之间的通信。

### 单处理器 cache miss 流量

这是传统 cache miss：

```text
第一次访问没有
cache 容量不够
cache 映射冲突
```

这些就是 3C 里面的内容。

---

### 通信造成的流量

多核程序中，处理器之间会通过共享变量通信。

比如：

```text
P0 写 flag = 1
P1 读 flag
```

这种通信会导致：

```text
invalidate
cache miss
数据在不同 cache 之间转移
```

这部分流量是单核程序没有的。

---

### Coherence Miss

课件把它叫：

```text
Coherence miss
```

也叫：

```text
Communication miss
```

它是传统 3C 之外的第四类 cache miss。课件第 61 页明确说，SMP 缓存性能包括单处理器 miss 流量和通信造成的流量，而 coherence miss 是 Compulsory、Capacity、Conflict 之外的第四类 miss。

---

## 第 62 页：按 block 跟踪缓存一致性

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L12-CacheCoherence-03.webp)

这一页是理解 **false sharing** 的基础。

课件设定：

```text
block 大小 = 32B
Processor 0 读写变量 X
Processor 1 读写变量 Y
X 地址 = 4000
Y 地址 = 4012
```

问题是：

```text
4000 和 4012 虽然是不同变量，
但它们落在同一个 32B cache block 里。
```

因为一个 32B block 可能覆盖：

```text
4000, 4004, 4008, 4012, 4016, ..., 4028
```

所以：

```text
X 和 Y 是不同 word
但属于同一个 cache line
```

Cache coherence 是按 **cache line/block** 管理的，不是按单个变量管理。

所以如果 P0 写 X：

```text
P0 获得整个 block 的独占权
```

这会导致 P1 里包含 Y 的那整个 block 被 invalid。

即使 P1 根本没有用 X，只是在用 Y，也会受影响。课件第 62 页正是用 X=4000、Y=4012、block=32B 来说明这个问题。

---

## 第 63 页：干预 Intervention

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L12-CacheCoherence-04.webp)

这一页讲的是：当一个 cache 里有最新数据，而主存是旧的时，另一个处理器来读，**不能让主存直接回答**。

图里有：

```text
CPU-Memory Bus
A 200
A 100
```

可以理解为：

```text
某个 cache 中 A = 200，是最新值
Memory 中 A = 100，是旧值
```

现在另一个处理器请求读 A。

如果让 memory 返回 A=100，就错了。

所以拥有最新值的 cache 要“干预”：

```text
看到总线上有人读 A
发现自己有 A 的 modified copy
于是阻止/覆盖 memory 的旧响应
把 A=200 提供出去
```

这就叫 **intervention**。

它的本质是：

```text
当 cache 有最新脏数据时，
cache 需要介入这次读请求，
把最新数据提供给请求者。
```

它和前面 Directory 的 “load with owner” 是同一个核心思想：如果某个 owner cache 有 modified line，读取者不能直接拿主存旧值，而要通过 owner 获得最新值；课件第 56 页也展示了 load with owner，需要 forward 和 acknowledge+value。

---

## 第 64 页：伪共享 False Sharing

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L12-CacheCoherence-05.webp)

这一页正式定义伪共享。

### Cache line 含多个 word

比如一条 cache line：

```text
state | line addr | data0 | data1 | ... | dataN
```

一个 cache line 里有很多 word。

---

### 一致性是在 line-level 完成的

这句话非常关键：

```text
Cache coherence 是按 cache line 管理，
不是按 word 管理。
```

所以硬件看到的是：

```text
这一整行有没有被别人写？
```

而不是：

```text
这一行里的哪个具体 word 被写？
```

课件也明确说：Cache line 包含多个字，cache coherence 是在 line-level 而不是 word-level 完成的。

---

### 伪共享发生条件

假设：

```text
M1 写 word_i
M2 写 word_k
i ≠ k
但 word_i 和 word_k 在同一个 cache line
```

从程序角度看：

```text
两个处理器写的是不同变量，没有真正共享同一个变量。
```

但从硬件角度看：

```text
它们写的是同一条 cache line。
```

于是它们会不断让对方的 cache line 失效。

这就是 **false sharing**。

---

## 第 65 页：跟踪 Cache Block Coherency

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L12-CacheCoherence-06.webp)

这一页总结第 62～64 页的现象。

### 两个 cache 之间会出现 ping-pong

假设：

```text
P0 反复写 X
P1 反复写 Y
```

X 和 Y 不同，但在同一个 cache line。

那么会出现：

```text
P0 写 X -> P1 的整行失效
P1 写 Y -> P0 的整行失效
P0 再写 X -> P1 又失效
P1 再写 Y -> P0 又失效
```

这条 cache line 就在两个 cache 之间来回“弹来弹去”。

课件称之为：

```text
ping-pong effect
```

即使两个处理器访问的是不相交变量，也会出现。课件第 65 页明确说，两个缓存之间会发生 ping-pong effect，即使处理器访问的是不相交变量，这就是 false sharing。

---

### 如何预防？

核心方法是：

```text
让不同处理器频繁写的数据不要落在同一个 cache line。
```

常见办法：

```text
加 padding
按 cache line 对齐
每个线程的数据分开放到不同 cache line
```

例如：

```c
// 容易 false sharing
double sum[NUM_THREADS];

// 更安全：让每个线程隔开一个 cache line
double sum[NUM_THREADS][CACHE_LINE_SIZE / sizeof(double)];
```

---

## 第 66 页：还记得 3C 吗？

这一页复习传统三类 cache miss。

### Compulsory Miss

也叫 cold-start miss。

意思是：

```text
第一次访问某个 block，cache 里肯定没有。
```

特点：

```text
不可完全避免；
长时间运行程序中占比通常较小。
```

解决办法之一：

```text
增大 block size
```

但代价是：

```text
miss penalty 变大；
block 太大还可能增加 miss rate。
```

课件也这么总结：Compulsory 是第一次访问，解决方法可以是增加 block size，但会增加 miss penalty，过大还会增加 miss rate。

---

### Capacity Miss

意思是：

```text
cache 总容量不够，
即使 fully associative + 完美替换策略，也装不下程序需要的所有 block。
```

解决办法：

```text
增加 cache size
```

代价：

```text
可能增加访问时间。
```

---

### Conflict Miss

意思是：

```text
cache 总容量够，
但多个内存块映射到同一个 cache 位置，
互相挤掉。
```

解决办法：

```text
增加 cache size
增加 associativity
改进替换策略，例如 LRU
```

课件把这些都归纳在第 66 页。

---

## 第 67 页：第四个 C：Coherence Misses

这一页引出重点：多处理器里还有第四种 miss。

### Coherence Miss 是什么？

定义：

```text
由于其他处理器的一致性通信导致的 cache miss。
```

比如：

```text
P0 有 A
P1 写 A
P0 的 A 被 invalid
P0 下次再读 A，miss
```

这个 miss 不是因为 cache 小，也不是因为映射冲突，而是因为一致性协议让它失效。

课件第 67 页明确说，coherence misses 是由于与其他处理器的一致性通信而导致的 miss，也叫 communication misses。

---

### 为什么也叫 Communication Miss？

因为它本质上来自处理器之间的数据移动。

比如：

```text
P0 写完数据
P1 要读这个数据
```

数据必须从 P0 cache / memory 转移给 P1。

这就是并行程序里的通信。

---

### Coherence Miss 可能很严重

在一些并行程序中，如果多个处理器频繁共享或伪共享数据：

```text
不断 invalid
不断 miss
不断重新取数据
```

coherence miss 可能会成为主要性能瓶颈。

课件也说，在一些并行程序中，coherence misses 可能主导总的 miss。

---

> **Coherence 是按 cache line 维护的，不是按变量维护的；所以即使两个处理器访问不同变量，只要它们落在同一个 cache line，也可能互相 invalid，产生 false sharing 和 coherence miss。**

下面这组页的主线是：

**Coherence Miss → True/False Sharing → 伪共享如何影响性能 → 如何避免 → 进入 Memory Consistency Model。**

---

## 第 68 页：一致性缺失 Coherency Misses

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L12-CacheCoherence-07.webp)

这一页把 **coherence miss** 分成两类：

```text
Coherence miss
├── True sharing miss   真共享缺失
└── False sharing miss  伪共享缺失
```

#### 真共享缺失 True sharing miss

真共享的意思是：**两个处理器真的在访问同一个变量 / 同一个 word。**

例如：

```text
P1 写 X = 10
P2 后面读 X
```

P1 写 X 时，会让 P2 cache 里的 X 失效。

P2 之后再读 X，就会 miss。

这个 miss 是“合理的”，因为 P2 确实需要 P1 写过的新值。

所以真共享缺失的本质是：

```text
不同处理器真的通过同一个数据通信。
```

---

#### 伪共享缺失 False sharing miss

伪共享的意思是：**两个处理器访问的是不同变量，但这些变量刚好在同一个 cache line 里。**

例如：

```text
同一个 cache line 里有 X 和 Y

P1 只写 X
P2 只写 Y
```

从程序逻辑看，P1 和 P2 没有共享同一个变量。
但是硬件的一致性协议是按 **cache line** 管理的，不是按单个变量管理的。

所以 P1 写 X 时，会让 P2 包含 Y 的整条 cache line 失效。

P2 之后访问 Y，也会 miss。

这个 miss 就是伪共享缺失。

一句话：

```text
真共享：别人改的正是我要用的数据。
伪共享：别人改的不是我要用的数据，但因为在同一 cache line，我也被误伤。
```

---

### 第 69 页：例子：真伪共享与命中

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L12-CacheCoherence-08.webp)

这一页用一个表格追踪两个处理器 P1、P2 的 cache 状态。

表里的 `(X, Y)` 表示：

```text
X 和 Y 在同一个 cache block / cache line 里。
```

所以 cache 状态不是单独针对 X 或 Y，而是针对整块 `(X, Y)`。

表中反复出现：

```text
P1 Cache State: Modified(X, Y)
P2 Cache State: Invalid(X, Y)
```

意思是：

```text
P1 拿到了整个 cache line (X, Y) 的写权限；
P2 中这一整行都被 invalid。
```

即使 P2 只关心 Y，P1 只关心 X，也会发生整行失效。

---

#### 表中几种典型情况

##### 情况 1：P1 写 X

P1 写 X 时，它必须获得整个 `(X, Y)` block 的独占权限：

```text
P1: Modified(X, Y)
P2: Invalid(X, Y)
```

解释栏写的是：

```text
P1 Invalidates block (X, Y) in P2
```

也就是说，P1 写 X 会让 P2 的整个 `(X,Y)` block 失效。

如果 P2 后面要读 Y，那么 P2 会 miss。
但 P2 读的是 Y，不是 P1 刚写的 X，所以这是 **false sharing miss**。

---

##### 情况 2：P2 读取这个 block

表里有：

```text
P1: Shared(X, Y)
P2: Shared(X, Y)
Explanation: Write-back & Copy block from P1 to P2
```

意思是：

```text
P1 原来有最新的 Modified block；
P2 想读；
P1 必须把最新 block 提供出来；
最后两边都变成 Shared。
```

如果 P2 读取的是 P1 刚写过的 X，那是真共享。

如果 P2 只是读取 Y，那就是伪共享造成的数据搬运。

---

##### 情况 3：P1 和 P2 交替写不同 word

如果 P1 写 X，P2 写 Y，P1 再写 X，P2 再写 Y：

```text
P1 写 X -> P2 的 (X,Y) invalid
P2 写 Y -> P1 的 (X,Y) invalid
P1 写 X -> P2 的 (X,Y) invalid
...
```

这条 cache line 会在 P1 和 P2 之间来回移动，叫 **ping-pong**。

这就是伪共享最典型的性能问题。

---

### 第 70 页：4 核商业处理器工作负载的 miss 分解

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L12-CacheCoherence-09.webp)

这一页的柱状图把 miss 分成几类：

```text
Instruction
Capacity / Conflict
Cold
False Sharing
True Sharing
```

这张图想说明：

> 在多核商业工作负载中，cache miss 不只是传统 3C miss，还包含 true sharing 和 false sharing。

传统单核只关心：

```text
Cold miss
Capacity miss
Conflict miss
```

但多核还要看：

```text
True sharing miss
False sharing miss
```

图里可以看到，**True Sharing** 和 **False Sharing** 确实占了一部分 miss。尤其是商业负载，比如 OLTP、数据库、搜索引擎，会频繁访问共享数据结构，所以 coherence miss 不能忽略。

---

### 第 71 页：2 MiB 缓存商业处理器工作负载

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L12-CacheCoherence-10.webp)

这一页和第 70 页类似，但强调的是在较大 cache 配置下，多核工作负载的 miss 构成。

重点不是记住具体柱子数值，而是理解趋势：

```text
cache 变大后，
capacity/conflict miss 可能下降，
但 true sharing / false sharing 不一定消失。
```

原因是：

```text
coherence miss 不是因为 cache 太小，
而是因为别的处理器写共享数据，导致你的副本失效。
```

所以即使 cache 容量足够大，仍然可能因为多核通信产生 miss。

---

### 第 72 页：OpenMP 中的伪共享

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L12-CacheCoherence-11.webp)

这一页给了一个计算 π 的 OpenMP 例子：

```c
double x, pi, sum[NUM_THREADS];

#pragma omp parallel private(i, x)
{
    int id = omp_get_thread_num();

    for (i = id, sum[id] = 0.0; i < num_steps; i = i + NUM_THREADS) {
        x = (i + 0.5) * step;
        sum[id] += 4.0 / (1.0 + x * x);
    }
}
```

表面上看，每个线程都写自己的位置：

```text
线程 0 写 sum[0]
线程 1 写 sum[1]
线程 2 写 sum[2]
线程 3 写 sum[3]
```

没有数据竞争。

但问题是：

```text
double = 8 bytes
sum[0] 和 sum[1] 在内存中相邻
```

如果 cache line 是 64B，那么一条 cache line 可以放：

```text
64 / 8 = 8 个 double
```

也就是说：

```text
sum[0], sum[1], ..., sum[7]
```

很可能在同一条 cache line 里。

于是线程 0 更新 sum<span>

0

</span>

，会让线程 1、2、3 所在 cache 的整条 line 失效；线程 1 更新 sum<span>

1

</span>

，又让线程 0 的整条 line 失效。课件也指出，`sum[0]` 是 8 字节，`sum[1]` 是相邻的 8 字节，如果块大小大于 8 字节，就会发生 false sharing。

所以这段程序的问题不是结果错，而是：

```text
性能会很差。
```

---

### 第 73 页：练习题：避免伪共享

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L12-CacheCoherence-12.webp)

代码变成：

```c
double x, pi, sum[10000];

#pragma omp parallel private(i, x)
{
    int id = omp_get_thread_num(), fix = ________;

    for (i = id, sum[id] = 0.0; i < num_steps; i = i + NUM_THREADS) {
        x = (i + 0.5) * step;
        sum[id * fix] += 4.0 / (1.0 + x * x);
    }
}
```

问题是：`fix` 取什么值可以避免 false sharing？

答案是：

```text
YELLOW：Constant for size of blocks in doubles
```

也就是：

```text
fix = cache line 中能放多少个 double
```

如果 cache line 是 64B，double 是 8B：

```text
fix = 64 / 8 = 8
```

这样：

```text
线程 0 写 sum[0]
线程 1 写 sum[8]
线程 2 写 sum[16]
线程 3 写 sum[24]
```

它们就落在不同 cache line 里，不会互相 invalid。

为什么不是 ORANGE？

```text
ORANGE = block size in bytes
```

如果直接用 64，间隔太大了。
真正需要的是 **以 double 为单位的 cache line 大小**，所以是 YELLOW。

---

### 第 74 页：过渡页

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L12-CacheCoherence-13.webp)

---

### 第 75 页：加速和缩放的类型

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L12-CacheCoherence-14.webp)

这一页讲 **scalability，可扩展性**。

定义：

```text
如果给机器增加 x 倍资源，
性能也接近提高 x 倍，
就叫可扩展性好。
```

这里的资源通常是：

```text
处理器数量
内存容量
互连带宽
```

课件说，加入 x 倍资源后希望得到接近 x 倍的性能，也就是随着处理器数量增加，效率还能保持。

这一页还说，常见的可扩展性模型有两类：

```text
Problem constrained scaling
Time constrained scaling
```

---

### 第 76 页：Problem Constrained Scaling

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L12-CacheCoherence-15.webp)

这个也可以理解成 **强缩放 strong scaling**。

特点：

```text
问题规模固定；
增加处理器数量；
目标是减少执行时间。
```

例如：

```text
同一个矩阵乘法任务
1 个处理器要 100 秒
10 个处理器希望接近 10 秒
```

加速比定义为：

```text
S = Time(1 processor) / Time(p processors)
```

也就是：

```text
同一个任务，用 p 个处理器比用 1 个处理器快多少。
```

这类缩放更难，因为问题规模固定后，处理器越多，每个处理器分到的工作越少，通信和同步开销占比会变大。

---

### 第 77 页：Time Constrained Scaling

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L12-CacheCoherence-16.webp)

这个接近 **弱缩放 weak scaling**。

特点：

```text
允许执行时间固定；
增加处理器数量；
目标是处理更大的问题。
```

例如：

```text
1 个处理器 1 分钟处理 1GB 数据；
10 个处理器 1 分钟希望处理 10GB 数据。
```

加速比定义为：

```text
S = Work(p processors) / Work(1 processor)
```

也就是：

```text
在相同时间内，多处理器能完成多少倍工作。
```

这类缩放通常比强缩放容易，因为每个处理器仍然有足够多的工作，通信开销相对不那么显眼。

---

### 第 78 页：同步 Synchronization

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L12-CacheCoherence-17.webp)

这一页进入同步问题。

只要系统中存在并发进程，就需要同步，即使是单处理器系统也一样。课件把同步分成两类：生产者-消费者和互斥。

#### 生产者-消费者 Producer-Consumer

意思是：

```text
生产者先产生数据；
消费者必须等数据准备好之后才能使用。
```

例如：

```text
P1 写 data
P1 设置 flag = 1

P2 看到 flag = 1
P2 读取 data
```

关键问题是：

```text
P2 看到 flag = 1 时，data 是否一定已经可见？
```

这会引出后面的 memory consistency model。

---

#### 互斥 Mutual Exclusion

意思是：

```text
同一时间只允许一个处理器使用共享资源。
```

例如：

```text
一次只允许一个线程进入临界区；
一次只允许一个人编辑文件。
```

这通常通过 lock / unlock 实现。

---

### 第 79 页：简单的生产者-消费者例子

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L12-CacheCoherence-18.webp)

图里有：

```text
Producer processor
Consumer processor
Shared Memory: flag, data
```

生产者和消费者都通过共享内存中的 `flag` 和 `data` 通信。

生产者的意图是：

```text
先写 data；
再写 flag = 1；
告诉消费者数据准备好了。
```

消费者的意图是：

```text
不断读取 flag；
如果 flag == 0，就继续等；
如果 flag == 1，就读取 data。
```

直觉上，我们希望：

```text
消费者一旦看到 flag = 1，
就一定能看到生产者写入的新 data。
```

但这个直觉只在足够强的内存一致性模型下成立。

仅有 cache coherence 还不够，因为：

```text
flag 和 data 是两个不同地址。
```

Coherence 只保证单个地址的一致性，不能自动保证不同地址之间的顺序。

---

### 第 80 页：内存一致性模型 Memory Consistency Model

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L12-CacheCoherence-19.webp)

这一页区分两个概念：

```text
Cache coherence
Memory consistency
```

#### Cache coherence 解决什么？

它关注 **单个内存地址**。

例如地址 X：

```text
P1 写 X = 1
P2 读 X
P3 写 X = 2
```

Coherence 规定所有处理器对同一个地址 X 的读写应该看到合法顺序。

---

#### Memory consistency 解决什么？

它关注 **多个地址之间的顺序**。

例如：

```text
Producer 写 data
Producer 写 flag

Consumer 读 flag
Consumer 读 data
```

这里有两个地址：

```text
data
flag
```

问题是：

```text
Consumer 看到 flag = 1 时，
是否一定能看到新的 data？
```

这不是 coherence 单独能回答的问题。课件也说，内存一致性模型描述跨多个硬件线程时，load 指令可以返回哪些值；coherence 主要描述单个地址应该返回的合法值。

---

### 第 81 页：生产者-消费者代码

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L12-CacheCoherence-20.webp)

生产者代码：

```text
sw xdata, (xdatap)
li xflag, 1
sw xflag, (xflagp)
```

意思是：

```text
先写 data；
再把 flag 设为 1。
```

消费者代码：

```text
spin:
    lw xflag, (xflagp)
    beqz xflag, spin
    lw xdata, (xdatap)
```

意思是：

```text
一直读 flag；
如果 flag 是 0，就继续等；
如果 flag 是 1，就读取 data。
```

初始：

```text
flag = 0
```

这页问的问题是：

```text
消费者看到 flag = 1 之前，
生产者写入的 data 是否已经对消费者可见？
```

在 **顺序一致性 SC** 下，答案是：应该可见。

但在弱内存模型下，可能出现：

```text
flag = 1 已经被消费者看到；
data 的新值还没有对消费者可见。
```

所以后面需要讨论 memory consistency 和 fence。

---

### 第 82 页：顺序一致性 SC

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L12-CacheCoherence-21.webp)

这一页给的是 Leslie Lamport 的经典定义。

简单翻译：

> 一个系统是顺序一致的，如果任何执行结果都像是所有处理器的操作按照某个全局顺序依次执行；并且每个处理器自己的操作顺序仍然符合程序规定的顺序。课件原文也强调：每个处理器的操作要按照程序指定的顺序出现。

拆成两点：

#### 存在一个全局顺序

所有处理器的内存操作可以排成一个队列：

```text
P1 的某条 store
P2 的某条 load
P1 的另一条 store
P3 的 load
...
```

系统表现得好像这些操作是一个一个发生的。

---

#### 每个处理器内部顺序不能乱

如果 P1 程序里是：

```text
store data
store flag
```

那么在全局顺序里，也必须是：

```text
store data 在 store flag 前面
```

不能反过来。

所以在生产者-消费者例子中，如果消费者看到 `flag = 1`，那么按 SC 推理：

```text
Producer: store data 发生在 store flag 前
Consumer: load flag 发生在 load data 前
Consumer 读到 flag = 1，说明 store flag 已经发生
因此 store data 也已经发生
```

所以消费者应该读到新 data。

---

### 第 83 页：生产者-消费者中的顺序关系

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L12-CacheCoherence-22.webp)

这一页继续用生产者-消费者说明 SC 的直觉。

图里红、蓝箭头可以理解成不同处理器上的操作顺序。

生产者这边的顺序是：

```text
写 data
写 flag
```

消费者这边的顺序是：

```text
读 flag
读 data
```

SC 要求这两个本地顺序都不能被打乱。

因此正确逻辑应该是：

```text
Producer 写 data
Producer 写 flag = 1
Consumer 读到 flag = 1
Consumer 再读 data
```

这样消费者读 data 时，应该能看到生产者写的数据。

但现实硬件为了性能可能会做优化，例如：

```text
store buffer
load/store 重排序
让不同地址的访存乱序完成
```

这就可能破坏这种直觉顺序。

---

### 第 84 页：大多数真正的机器都不是 SC

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L12-CacheCoherence-23.webp)

这一页非常重要。

它说：

```text
大多数真实机器都不是 Sequential Consistency。
```

课件明确提到，只有少数商业 ISA 要求 SC，x86 和 ARM 都不是 SC；使用 SC 会让简单机器变慢，或者需要复杂硬件来保持性能。

为什么？

因为现代处理器为了性能，会使用：

```text
store buffer
乱序执行
非阻塞 cache
load/store 优化
写合并
```

这些优化会让内存操作对其他处理器可见的顺序和程序顺序不完全一致。

所以现实中需要：

```text
fence
memory barrier
atomic 操作
acquire / release
lock / unlock
```

来明确告诉硬件：

```text
这里的顺序不能乱。
```

对于生产者-消费者例子，通常要保证：

```text
生产者：data 写入必须在 flag 写入之前对外可见；
消费者：看到 flag 后，读取 data 不能被提前。
```

否则就可能出现：

```text
Consumer 看到 flag = 1
但读到旧 data
```

---

下面这几页进入的是 **Memory Consistency Model，内存一致性模型**。它和前面 **cache coherence** 不一样：

```text
Cache coherence：管同一个地址的值是否一致。
Memory consistency：管不同地址的读写顺序是否符合程序员预期。
```

例如生产者-消费者里有两个地址：`data` 和 `flag`。
即使 `data` 自己是 coherent 的、`flag` 自己也是 coherent 的，也不代表消费者看到 `flag = 1` 时一定能看到新的 `data`。这就是 memory consistency 要解决的问题。课件也明确区分了：coherence 描述单个内存地址能返回什么合法值，而 consistency model 描述跨多个硬件线程时 load 可以返回哪些值。

---

## 第 85 页：Store Buffer Optimization，存储缓冲区优化

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L12-CacheCoherence-24.webp)

这页讲的是为什么真实处理器很少严格按照 **SC 顺序一致性** 来执行。

图中每个 CPU 和 shared memory 中间加了一个：

```text
Store Buffer
```

它的作用是：**CPU 执行 store 时，不必等这个写操作真正进入 cache / memory / 对其他处理器可见，而是先把写操作放进 store buffer，CPU 继续往后执行。**

例如：

```text
CPU 执行：store X = 1
```

没有 store buffer 时，CPU 可能要等：

```text
写入 cache
获得 cache line 独占权
完成一致性协议
其他 cache 副本失效
```

这会很慢。

有 store buffer 后：

```text
store X = 1 先进入 store buffer
CPU 继续执行后面的指令
稍后再慢慢把 X=1 写到 cache / memory 系统中
```

所以它的优点是：

```text
减少 store 阻塞 CPU 的时间；
隐藏 cache miss / coherence 操作延迟；
提高流水线性能。
```

但是它带来的问题是：

```text
本处理器以为自己已经写了；
其他处理器暂时还看不到这个写。
```

这正是 TSO 比 SC 更弱的根源。

---

## 第 86 页：TSO 例子

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L12-CacheCoherence-25.webp)

这一页通常对应经典的 **Store Buffering litmus test**。

假设初始：

```text
X = 0
Y = 0
```

两个处理器执行：

```text
P1:
X = 1
r1 = Y

P2:
Y = 1
r2 = X
```

表格中的：

```text
P1.x2 = P1 最后读到的 Y
P2.x2 = P2 最后读到的 X
```

结果表：

<table>
<thead>
  <tr>
    <th>
      P1.x2
    </th>
    
    <th>
      P2.x2
    </th>
    
    <th>
      SC
    </th>
    
    <th>
      TSO
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      0
    </td>
    
    <td>
      0
    </td>
    
    <td>
      N
    </td>
    
    <td>
      Y
    </td>
  </tr>
  
  <tr>
    <td>
      0
    </td>
    
    <td>
      1
    </td>
    
    <td>
      Y
    </td>
    
    <td>
      Y
    </td>
  </tr>
  
  <tr>
    <td>
      1
    </td>
    
    <td>
      0
    </td>
    
    <td>
      Y
    </td>
    
    <td>
      Y
    </td>
  </tr>
  
  <tr>
    <td>
      1
    </td>
    
    <td>
      1
    </td>
    
    <td>
      Y
    </td>
    
    <td>
      Y
    </td>
  </tr>
</tbody>
</table>

最关键的是第一行：

```text
P1.x2 = 0
P2.x2 = 0
```

在 **SC** 下不允许。
因为 SC 要求所有处理器的内存操作能排成一个全局顺序，而且每个处理器自己的程序顺序不能乱。无论怎么排，只要 P1 读到 `Y=0`，说明 P2 的 `Y=1` 还没发生；P2 又读到 `X=0`，说明 P1 的 `X=1` 还没发生。这样会形成矛盾，所以 SC 不允许。

但在 **TSO** 下允许。原因是：

```text
P1 的 X=1 先进入 P1 的 store buffer，还没被 P2 看到；
P2 的 Y=1 先进入 P2 的 store buffer，还没被 P1 看到；
P1 随后读 Y，看到旧值 0；
P2 随后读 X，也看到旧值 0。
```

所以 TSO 的核心是：

```text
每个处理器可以先看到自己的 store；
其他处理器稍后才看到这个 store。
```

课件第 89 页也把 TSO 描述为：处理器可以在其他处理器之前看到自己的写操作，这是由 store buffer 引起的。

---

## 第 87 页：强与弱内存一致性模型

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L12-CacheCoherence-26.webp)

这一页在讲不同 memory model 的强弱。

### 强内存模型 Stronger models

强模型提供更多顺序保证。

典型代表：

```text
SC，Sequential Consistency
```

它对程序员最友好，因为程序看起来像：

```text
所有处理器的内存操作按某个全局顺序一个一个执行；
每个处理器内部仍保持程序顺序。
```

好处：

```text
编程简单；
推理简单；
更接近直觉。
```

坏处：

```text
硬件更难做快；
很多重排序优化不能随便使用；
可能需要复杂硬件检测顺序违规。
```

课件也指出，强模型提供更多 load/store 顺序保证，因此 ISA 级编程模型更简单，但可能需要更多硬件来确保顺序。

---

### 弱内存模型 Weaker models

弱模型提供较少顺序保证。

好处：

```text
硬件更容易做高性能；
允许 store buffer；
允许 load/store 重排序；
允许更激进的乱序执行。
```

坏处：

```text
程序员或编译器必须显式加 fence；
并发程序更难理解；
不小心就会出现“flag 已经变了，但 data 还没看到”的问题。
```

所以弱模型会提供额外指令：

```text
fence
memory barrier
acquire / release
atomic operation
```

让软件告诉硬件：

```text
这里不能乱序。
```

---

## 第 88 页：生产者-消费者中的栅栏 Fence

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L12-CacheCoherence-27.webp)

> ### Fence
> 
> 你可以把 **fence** 理解成 CPU 里的一个“**禁止越线标志 / 栅栏**”。
> 
> 它不是数据，也不是锁，而是一条指令，作用是：
> 
> **告诉 CPU：某些内存操作不能乱序，必须等前面的完成后，后面的才能继续。**
> 
> ---
> 
> #### 为什么需要 fence？
> 
> 先看生产者-消费者问题。
> 
> 生产者想表达的是：
> 
> ```text
> 写 data
> 写 flag = 1
> ```
> 
> 意思是：
> 
> ```text
> 我先把数据准备好，
> 然后再告诉别人：数据好了。
> ```
> 
> 消费者想表达的是：
> 
> ```text
> 读 flag
> 如果 flag == 1，再读 data
> ```
> 
> 意思是：
> 
> ```text
> 我先确认数据好了，
> 然后再去读数据。
> ```
> 
> 按人的直觉，这肯定没问题。
> 
> 但是 CPU 为了性能，可能会做优化：
> 
> ```text
> 写 data 先放进 store buffer，还没真正让别人看到；
> 写 flag = 1 反而先被别人看到了。
> ```
> 
> 于是消费者可能看到：
> 
> ```text
> flag = 1
> ```
> 
> 以为数据好了，结果读 `data` 时读到的还是旧值。
> 
> 这就出错了。
> 
> ---
> 
> #### fence 是干什么的？
> 
> **fence 就是阻止这种乱序或延迟可见。**
> 
> 它像一个栅栏：
> 
> ```text
> 前面的操作没完成，后面的操作不能越过 fence。
> ```
> 
> ---
> 
> ### 生产者这里的 fence w,w
> 
> 生产者代码：
> 
> ```text
> sd xdata, (xdatap)     # 写 data
> li xflag, 1
> fence w,w             # 写-写栅栏
> sd xflag, (xflagp)     # 写 flag = 1
> ```
> 
> `fence w,w` 的意思是：
> 
> ```text
> 前面的写操作，必须在后面的写操作之前完成。
> ```
> 
> 这里就是：
> 
> ```text
> 写 data 必须先对外可见；
> 然后才能写 flag = 1。
> ```
> 
> 所以它防止这种错误：
> 
> ```text
> flag = 1 已经被消费者看到，
> 但 data 还没真正写出去。
> ```
> 
> 你可以把它理解成：
> 
> ```text
> 生产者先把饭做好，再挂出“饭好了”的牌子。
> 不能牌子先挂出去，饭还没做好。
> ```
> 
> ---
> 
> ### 消费者这里的 fence r,r
> 
> 消费者代码：
> 
> ```text
> spin:
>     ld xflag, (xflagp)     # 读 flag
>     beqz xflag, spin       # 如果 flag == 0，继续等
>     fence r,r              # 读-读栅栏
>     ld xdata, (xdatap)     # 读 data
> ```
> 
> `fence r,r` 的意思是：
> 
> ```text
> 前面的读操作，必须在后面的读操作之前完成。
> ```
> 
> 这里就是：
> 
> ```text
> 必须先真的读到 flag = 1；
> 然后才能读 data。
> ```
> 
> 它防止 CPU 提前做这种事：
> 
> ```text
> 还没确认 flag，就提前把 data 读了。
> ```
> 
> 如果 data 被提前读取，可能读到旧值。
> 
> ---
> 
> ### 这页到底在讲什么？
> 
> 这页讲的是：
> 
> **在弱内存模型下，CPU 可能为了性能打乱内存操作的可见顺序。为了让生产者-消费者程序正确，需要用 fence 强制关键顺序。**
> 
> 具体就是两个顺序：
> 
> ```text
> 生产者：
> 写 data  →  写 flag
> 
> 消费者：
> 读 flag  →  读 data
> ```
> 
> fence 的作用就是保护这两个箭头不能被打乱。
> 
> ---
> 
> ### 一句话总结
> 
> **fence 就是内存操作之间的“红绿灯”：前面的读/写没按要求完成，后面的读/写不能先过去。**
> 
> 这页最核心就是：
> 
> ```text
> 生产者用 fence w,w：
> 保证 data 先写出去，flag 后写出去。
> 
> 消费者用 fence r,r：
> 保证先看到 flag，再去读 data。
> ```

这页回到生产者-消费者例子。

生产者想做：

```text
sd xdata, (xdatap)
li xflag, 1
fence w,w
sd xflag, (xflagp)
```

消费者想做：

```text
spin:
    ld xflag, (xflagp)
    beqz xflag, spin
    fence r,r
    ld xdata, (xdatap)
```

这里的关键是两个 fence。

### 生产者端：`fence w,w`

意思是：

```text
前面的写操作，必须在后面的写操作之前完成 / 对外可见。
```

对应这里就是：

```text
写 data 必须早于写 flag。
```

否则可能出现：

```text
flag = 1 已经被消费者看到；
但 data 的新值还没对消费者可见。
```

这就违反生产者-消费者的语义。

---

### 消费者端：`fence r,r`

意思是：

```text
前面的读操作，必须在后面的读操作之前完成。
```

对应这里就是：

```text
先读 flag；
确认 flag = 1；
再读 data。
```

否则硬件可能为了性能提前读取 data，导致：

```text
消费者提前读到了旧 data；
之后才看到 flag = 1。
```

所以这页的核心是：

```text
生产者用 fence 保证 data 写在 flag 写之前；
消费者用 fence 保证 flag 读在 data 读之前。
```

课件第 88 页正是用 `fence w,w` 和 `fence r,r` 修正生产者-消费者顺序问题。

---

## 第 89 页：内存一致性模型分类

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L12-CacheCoherence-28.webp)

这一页把常见 memory consistency model 分成几类。

### SC：Sequential Consistency

最强、最直观。

```text
所有处理器看到一个统一的全局内存操作顺序；
每个处理器自己的操作顺序保持程序顺序。
```

优点是好理解，缺点是硬件实现成本高。

---

### TSO：Total Store Order

比 SC 弱一点，但仍然算比较强。

TSO 允许的关键优化是：

```text
store 进入 store buffer 后，
后面的 load 可以先执行。
```

也就是说，它允许一种重要重排序：

```text
Store -> Load 可以表现得像被重排了。
```

但是 TSO 仍然保持很多顺序，比如：

```text
同一个处理器的 store 顺序通常仍然按程序顺序对外可见；
其他处理器通常以相同顺序看到这些 store。
```

课件列出的例子包括：

```text
IBM-370 TSO
x86 TSO
SPARC TSO
RISC-V RVTSO
```

---

### 弱的、multi-copy atomic 内存模型

multi-copy atomic 可以理解为：

```text
一个处理器的写操作一旦对其他处理器可见，
所有处理器看到这个写的顺序是一致的。
```

也就是说，不同处理器不会对“别人写入的顺序”产生严重分歧。

课件举例：

```text
修改后的 ARMv8 memory model
RISC-V RVWMO
```

---

### 弱的、non-multi-copy atomic 内存模型

这种更弱。

含义是：

```text
不同处理器可能以不同顺序看到另一个处理器的写操作。
```

这会让程序推理非常困难。

课件举例：

```text
ARMv7
原始 ARMv8
IBM POWER
DEC Alpha
```

课件最后也指出，最近的共识认为这种模型可能太弱了。

---

## 第 90 页：Release Consistency，释放一致性

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L12-CacheCoherence-29.webp)

这一页讲一种更实用的弱一致性思想：**不要要求所有普通内存访问都严格有序，只在同步点保证顺序。**

图里有：

```text
Acquire
Critical
Release
Other Code
```

对应锁的逻辑：

```c
lock();      // Acquire
临界区;      // Critical section
unlock();    // Release
```

---

### Acquire 是什么？

Acquire 是“获取锁”或“获得共享数据访问权”。

它要求：

```text
Acquire 之后的临界区读写，不能被提前到 Acquire 之前。
```

直觉是：

```text
你必须先拿到锁，才能读写临界区里的共享数据。
```

如果临界区里的读取被提前到拿锁之前，就可能读到别人还没发布完成的数据。

---

### Release 是什么？

Release 是“释放锁”或“发布更新”。

它要求：

```text
临界区里的写操作，必须在 Release 对其他处理器可见之前完成。
```

直觉是：

```text
你必须先把临界区里的更新做好，再告诉别人“我释放锁了”。
```

否则别人拿到锁之后，可能看不到你刚刚在临界区做的修改。

---

### 图中的 P1 和 P2 怎么理解？

P1 先进入临界区：

```text
P1 Acquire
P1 Critical：修改共享数据
P1 Release
```

P2 后进入临界区：

```text
P2 Acquire
P2 Critical：读取共享数据
P2 Release
```

Release Consistency 保证：

```text
P1 在 Critical 中的更新，
必须在 P1 的 Release 之前对外可见；

P2 的 Critical 读取，
必须发生在 P2 的 Acquire 之后。
```

所以 P2 acquire 成功后，应该能看到 P1 release 之前发布的更新。

课件第 90 页总结得很清楚：consistency 只在进程通信数据时才重要；一个进程向其他进程共享更新时需要 consistent view，其他进程在获得共享数据访问权后需要接收更新。

---

## 总结这几页

这几页的逻辑是：

```text
第 85 页：
Store buffer 提高性能，但让自己的写先被自己看到，别人稍后看到。

第 86 页：
TSO 允许两个处理器都读到旧值 0，这是 SC 不允许的。

第 87 页：
强模型更好理解但难实现高性能；弱模型更快但需要 fence。

第 88 页：
生产者-消费者需要 fence，保证 data 和 flag 的访问顺序。

第 89 页：
内存模型从强到弱可以分为 SC、TSO、弱 MCA、弱 non-MCA。

第 90 页：
Release consistency 只在 acquire/release 这类同步点保证必要顺序。
```

最关键的一句话是：

> **Store buffer 让处理器更快，但会打破“所有人立刻按程序顺序看到写入”的直觉；所以现代处理器需要 memory consistency model 和 fence/acquire/release 来规定什么时候必须保持顺序。**
