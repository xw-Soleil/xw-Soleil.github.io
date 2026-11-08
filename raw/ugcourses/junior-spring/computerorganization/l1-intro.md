# L1：计算机发展史与体系结构导论

> 计算机发展简史、处理器产业链、ISA 与体系结构的定义，以及执行时间/CPI 性能公式

> 感觉这一章不知道能考啥，但是历年卷好像考过计算机发展史。。。所以很难评，应该对这一章内容要有印象

## 计算机发展史

**第一代计算机：真空管时代，1946–1957**
主要使用真空管作为基本电子器件。特点是体积大、功耗高、发热严重、可靠性较差，但实现了早期电子计算机。

**第二代计算机：晶体管时代，1958–1964**
晶体管取代真空管。相比第一代，计算机体积变小、功耗降低、速度提高、可靠性增强。

**第三代计算机：小/中规模集成电路时代，1965–1970**
开始把多个晶体管集成到一块芯片上，使用小规模集成电路和中规模集成电路。计算机进一步小型化，性能和稳定性继续提升。

**第四代计算机：大规模/超大规模集成电路时代，1971 至今**
使用大规模、超大规模甚至极大规模集成电路，单芯片上可集成大量器件。现代 CPU、内存和 SoC 都属于这一发展阶段，特点是性能高、成本低、集成度极高。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L1-Intro-01.webp)

## 处理器产业链

### 中国基础IT产业链

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L1-Intro-02.webp)

### 国产操作系统

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L1-Intro-03.webp)

### CPU供给概述

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L1-Intro-04.webp)

### 半导体产业链

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L1-Intro-05.webp)

## 处理器介绍

### 处理器类型

分为传统处理器和新一代处理器

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L1-Intro-06.webp)

### 计算机架构的定义

**计算机架构不只是 ISA**。旧观点认为架构主要是指令集架构 ISA，包括寄存器、寻址方式、指令格式、操作类型等；但**真实的计算机架构**还包括**微架构**和**硬件实现**，即如何用功能单元、数据通路、控制逻辑和缓存等部件，把 ISA 具体实现出来，并在成本、功耗和可用性约束下尽量提高性能。

### CPU结构

CPU，即中央处理器，是计算机中负责执行指令和处理数据的核心部件。它主要由功能单元、数据通路、控制器和缓存组成。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L1-Intro-07.webp)

**控制器**负责取指令、译码，并发出控制信号，决定 CPU 下一步做什么。

**数据通路**负责数据的传输和运算，包括寄存器、运算单元 ALU 等。

**功能单元**负责具体操作，比如加减运算、逻辑运算、地址计算等。

**缓存 Cache**用于临时保存常用的指令和数据，减少 CPU 访问主存的时间。

### 指令集架构 ISA

CPU内核的基础就是指令集(ISA)和微架构。ISA 是**软件和硬件之间的接口**，规定了编译器能使用哪些指令，以及 CPU 应该如何识别和执行这些指令，ISA包括以下几个部分：

1. **数据类型**
CPU 能识别什么类型的数据，例如 byte、word、integer、floating point、string 等。
2. **操作类型**
CPU 能对数据做什么操作，例如 add、sub、mul、div、xor、move 等。
3. **可编程存储器**
程序可以直接使用或控制的存储资源，例如寄存器 regs、PC、memory。
4. **寻址方式**
CPU 如何找到操作数，例如立即数、寄存器、绝对地址、相对地址、寄存器加偏移等。
5. **指令编码**
一条机器指令如何用二进制表示，包括 opcode 和 operand fields 等。

#### ISA 对比

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L1-Intro-08.webp)

## 芯片设计与制造流程

### 芯片设计流程

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L1-Intro-09.webp)

### 制造流程

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L1-Intro-10.webp)

## 重要思想1： 摩尔定律与制造工艺

### Moore’s Law

Moore 定律指芯片上的晶体管数量会随时间快速增长，早期约每年翻倍，后来约每 18 个月翻倍。它使得芯片在成本基本不变的情况下，集成度提高、性能增强、功耗降低，是推动计算机硬件性能发展的重要规律。

### 工艺缩放系数

缩放系数 α 表示工艺尺寸缩小的倍数，<mark>

α = 原尺寸 / 新尺寸

</mark>

。若尺寸按 1/α 缩小，则单位面积可集成更多晶体管，芯片性能提高，是摩尔定律背后的重要技术基础。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L1-Intro-11.webp)

### 集成电路工艺的发展史

1962年，SSI（小规模集成）12个晶体管

1966年，MSI（中型集成），100-1k晶体管

1967-1973，大规模集成电路，1k~100k晶体管

1977年，超大规模集成电路（VLSI），30m²，150k晶体管

1993年，ULSI（超大规模集成）16M闪存和256M DRAM集成了10M晶体管

1994年，GSI（千兆级集成）1G DRAM集成了100亿个晶体管

2007年，2T的80核CPU失败

### 处理器技术的发展史

1. **晶体管尺寸不断缩小**
从 **250nm → 130nm → 65nm → 32nm → 14nm → 7nm**，说明工艺节点越来越先进，单个晶体管变得更小。晶体管越小，同样面积芯片上能放更多晶体管。
2. **晶体管密度不断增加**
晶体管密度每年增加约 **35%**，芯片尺寸每年增加 **10%–20%**。这意味着处理器里可以集成更多功能，比如更多缓存、更多核心、更复杂的执行单元等。
3. **晶体管速度随尺寸缩小而提高**
晶体管变小后，沟道更短，电容更小，开关速度理论上会提高。所以早期处理器性能提升很大程度来自工艺缩小。
4. **但电线延迟成为新问题**
晶体管变快，不代表芯片内部连线也等比例变快。随着芯片更复杂、连线更多更长，**电线延迟逐渐成为限制处理器性能的重要瓶颈**。

### 登纳德系数 Dennard Factor

登纳德系数 α 表示**工艺尺寸缩小的倍数**，<mark>

α = 原尺寸 / 新尺寸

</mark>

。它用于描述理想工艺缩放下，尺寸、电压、电流、电容、延迟和功耗如何同步缩小。早期工艺缩放符合登纳德定律，因此晶体管更多、速度更快且功耗可控；但后来电压难以下降，导致功耗问题严重，Dennard Scaling 失效，并引出黑硅问题。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L1-Intro-12.webp)

> **500nm → 350nm：**尺寸、电压、电流、电容基本都能按 0.7 缩小，比较符合登纳德缩放。
> 
> **90nm → 65nm：**尺寸还能缩小到 0.7，但**电压和电流基本不再下降，仍然约等于 1**。这样功耗就降不下来了，说明 **Dennard Scaling 开始失效**。

当电压缩放和频率缩放都受限制时，会出现 **Dark Silicon（黑硅）** 问题，也就是芯片上虽然可以集成越来越多晶体管，但由于功耗和散热限制，不能让所有晶体管同时工作，其中一部分区域必须关闭或低功耗运行，就像“变黑”了一样。

### 功耗墙

**动态功率 ≈ 活性 × 电容 × 电压² × 频率**

其中，**活性**表示有多少晶体管在工作，**电容**和电路规模有关，**电压**影响最大，因为是平方关系，**频率**越高，开关次数越多，功耗也越大。

**功率密度在变大**。电压和频率是恒定的，每个晶体管的面积在减小，晶体管数量（活性）正在增加，漏电功耗也在上升。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L1-Intro-13.webp)

工艺缩小后，晶体管越来越多，但电压和频率不能继续有效下降，漏电也增加，导致单位面积功耗越来越高。这限制了 CPU 继续靠提高主频来提升性能，因此出现“功耗墙”。

## 重要思想2： 抽象表示

### 软硬件接口

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L1-Intro-14.webp)

### 存储器抽象表示

- 表示方式（C语言中以指针来表示）。通常以字节地址命名，通常值以大小的倍数排列
- 读写序列
- 通过写入操作将值写到对应地址
- 读取地址返回该地址的最近写入值

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L1-Intro-15.webp)

## 重要思想3： 层次化

### 计算机体系结构

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L1-Intro-16.webp)

### 存储器技术的发展

存储器的发展经历了从早期物理介质到现代半导体存储的过程。

最早使用穿孔卡片、打孔纸带和机械轮子保存数据或指令，速度慢、容量小；

后来出现水银延迟线和磁芯存储器，使存储器逐渐进入电子化和随机访问阶段；

再后来 Robert Dennard 发明 DRAM，利用电容和晶体管存储信息，具有高密度、低成本的特点，成为现代主存的核心技术。

总体趋势是存储容量和密度快速提高，但访问延迟提升较慢，因此产生了“内存墙”问题，成为现代计算机系统性能的重要瓶颈。

### 存储墙

存储墙是指 CPU 性能提升速度远快于 DRAM 主存性能提升速度，导致处理器和内存之间的性能差距不断扩大，因此 CPU 经常因为等待内存数据而停顿，内存访问成为系统性能瓶颈。

为了解决这个问题，处理器逐渐加入片上 Cache，并发展到 L2 Cache，用更快的缓存减少访问主存的次数。但随着缓存越来越大，其性能收益逐渐下降，所以存储墙仍然是现代计算机设计中的重要问题。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L1-Intro-17.webp)

### 局部性原则(Locality)

局部性原则: 程序在任何时刻都**只能访问地址空间中相对较小**的部分。

#### 两种不同类型的局部性

- 时间局部性：如果一个项被引用，它将倾向于很快被再次引用(例如，循环，重用)
- 空间局部性：如果一个项被引用，其地址靠近的项倾向于很快被引用(例如，直线代码，数组访问)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L1-Intro-18.webp)

> 过去30年，硬件速度的提升主要依靠局部性。

## 重要思想4： 并行

### ILP 墙 | Instruction-Level Parallelism

**ILP 墙**表示在单个程序/单个线程的指令流内部，能够找到的可并行执行的指令越来越少，单核处理器很难再靠“同时执行更多指令”来持续提升性能。

> 简单理解就是单个线程内部的并行性被挖得差不多了，再增加复杂硬件，收益也越来越小。

### 新学派机器结构

现代“新学派机器结构”不再主要依赖单核变快，而是通过不同层次的并行性来提高性能。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L1-Intro-19.webp)

### 并行的分类

#### 应用程序中的并行

- **数据并行 DLP：Data-Level Parallelism，数据级并行**
意思是：对很多数据做相同或类似的操作。
例如：同时计算很多个数组元素、图像像素、矩阵元素。
- **任务并行 / 线程并行 TLP：Thread-Level Parallelism，线程级并行**
任务并行的意思是把不同任务或线程分配到不同计算环境中执行。
例如：一个程序中，一个线程负责搜索，一个线程负责排序，一个线程负责显示结果。

#### 架构中的并行

- **位级并行**：增加处理器字长。
例如从 8 位到 16 位、32 位、64 位，一次能处理更多位的数据。
- **ILP：Instruction-Level Parallelism，指令级并行**
意思是一个处理器核心内部同时处理多条指令，例如流水线、超标量、乱序执行。
- **线程级并行**：多个核心或多个硬件线程同时运行多个线程。
例如多核 CPU 同时跑多个线程。
- **向量架构 / GPU**：适合大量数据并行。
例如 GPU 同时处理大量像素、矩阵运算、AI 张量计算。
- **异构**：不同类型处理器协同工作。
例如 CPU + GPU + NPU，CPU 负责通用控制，GPU/NPU 负责专门计算。

### 并行加速案例

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L1-Intro-20.webp)

## 重要思想5： 流水线

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 50.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L1-Intro-21.webp" />
      </p>
    </td>
    
    
      <td style="width: 49.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L1-Intro-22.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

## 重要思想6： 冗余

通过冗余实现可靠性

适用于从数据中心到存储到内存到指令的所有部分。

- 采用冗余数据中心，即使失去一个数据中心，互联网服务仍然在线
- 采用冗余磁盘阵列(RAID)，即使丢失1个磁盘但不丢失数据
- 冗余内存位(错误纠正码/ECC内存) ，即使丢失1位数据，也不会丢 失整个数据

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L1-Intro-23.webp)

## 重要思想7：性能评估

处理器性能评估的核心是执行时间。执行时间由指令数、CPI 和时钟周期共同决定，不能只看频率或 MIPS。比较性能要用同一工作负载下的执行时间，加速比等于旧时间除以新时间。局部优化不一定带来等比例整体提升，还要考虑功耗、CPI 和系统瓶颈。

### 性能指标

性能主要看两个指标：

**响应时间 response time**：一个程序从开始到结束的时间。
**吞吐率 throughput**：单位时间内完成的任务数量。

> 注意：更快的处理器通常能改善两者；更多处理器主要提升吞吐率，不一定改善单个任务响应时间。

### CPU 时间

PU 时间分为：

**User time**：用户程序运行时间。
**System time**：操作系统执行系统调用等操作的时间。

真正比较性能时，常用：

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

e

</mi>

<mi>

r

</mi>

<mi>

f

</mi>

<mi>

o

</mi>

<mi>

r

</mi>

<mi>

m

</mi>

<mi>

a

</mi>

<mi>

n

</mi>

<mi>

c

</mi>

<mi>

e

</mi>

<mo>

=

</mo>

<mfrac>
<mn>

1

</mn>

<mrow>
<mi>

E

</mi>

<mi>

x

</mi>

<mi>

e

</mi>

<mi>

c

</mi>

<mi>

u

</mi>

<mi>

t

</mi>

<mi>

i

</mi>

<mi>

o

</mi>

<mi>

n

</mi>

<mtext>



</mtext>

<mi>

T

</mi>

<mi>

i

</mi>

<mi>

m

</mi>

<mi>

e

</mi>
</mrow>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

Performance = \frac{1}{Execution\ Time}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

er

</span>

<span className="mord,mathnormal" style="margin-right:0.1076em;">

f

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

or

</span>

<span className="mord,mathnormal">

man

</span>

<span className="mord,mathnormal">

ce

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:2.0074em;vertical-align:-0.686em;">



</span>

<span className="mord">
<span className="mopen,nulldelimiter">



</span>

<span className="mfrac">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:1.3214em;">
<span style="top:-2.314em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0576em;">

E

</span>

<span className="mord,mathnormal">

x

</span>

<span className="mord,mathnormal">

ec

</span>

<span className="mord,mathnormal">

u

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

o

</span>

<span className="mord,mathnormal">

n

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

T

</span>

<span className="mord,mathnormal">

im

</span>

<span className="mord,mathnormal">

e

</span>
</span>
</span>

<span style="top:-3.23em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="frac-line" style="border-bottom-width:0.04em;">



</span>
</span>

<span style="top:-3.677em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord">

1

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.686em;">
<span>



</span>
</span>
</span>
</span>
</span>

<span className="mclose,nulldelimiter">



</span>
</span>
</span>
</span>
</span>
</span>

也就是：**执行时间越短，性能越高**。

### 核心公式：Iron Law

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

C

</mi>

<mi>

P

</mi>

<mi>

U

</mi>

<mi>

T

</mi>

<mi>

i

</mi>

<mi>

m

</mi>

<mi>

e

</mi>

<mo>

=

</mo>

<mi>

I

</mi>

<mi>

n

</mi>

<mi>

s

</mi>

<mi>

t

</mi>

<mi>

r

</mi>

<mi>

u

</mi>

<mi>

c

</mi>

<mi>

t

</mi>

<mi>

i

</mi>

<mi>

o

</mi>

<mi>

n

</mi>

<mi>

s

</mi>

<mo>

×

</mo>

<mi>

C

</mi>

<mi>

P

</mi>

<mi>

I

</mi>

<mo>

×

</mo>

<mi>

C

</mi>

<mi>

l

</mi>

<mi>

o

</mi>

<mi>

c

</mi>

<mi>

k

</mi>

<mi>

C

</mi>

<mi>

y

</mi>

<mi>

c

</mi>

<mi>

l

</mi>

<mi>

e

</mi>

<mi>

T

</mi>

<mi>

i

</mi>

<mi>

m

</mi>

<mi>

e

</mi>
</mrow>

<annotation encoding="application/x-tex">

CPU Time=Instructions×CPI×Clock Cycle Time

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

U

</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

T

</span>

<span className="mord,mathnormal">

im

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0785em;">

I

</span>

<span className="mord,mathnormal">

n

</span>

<span className="mord,mathnormal">

s

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal">

u

</span>

<span className="mord,mathnormal">

c

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

o

</span>

<span className="mord,mathnormal">

n

</span>

<span className="mord,mathnormal">

s

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
<span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="mord,mathnormal" style="margin-right:0.0785em;">

I

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

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

oc

</span>

<span className="mord,mathnormal" style="margin-right:0.0315em;">

k

</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

</span>

<span className="mord,mathnormal">

c

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

T

</span>

<span className="mord,mathnormal">

im

</span>

<span className="mord,mathnormal">

e

</span>
</span>
</span>
</span>
</span>

也可以写成：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

C

</mi>

<mi>

P

</mi>

<mi>

U

</mi>

<mtext>



</mtext>

<mi>

T

</mi>

<mi>

i

</mi>

<mi>

m

</mi>

<mi>

e

</mi>

<mo>

=

</mo>

<mfrac>
<mrow>
<mi>

I

</mi>

<mi>

n

</mi>

<mi>

s

</mi>

<mi>

t

</mi>

<mi>

r

</mi>

<mi>

u

</mi>

<mi>

c

</mi>

<mi>

t

</mi>

<mi>

i

</mi>

<mi>

o

</mi>

<mi>

n

</mi>

<mi>

s

</mi>

<mo>

×

</mo>

<mi>

C

</mi>

<mi>

P

</mi>

<mi>

I

</mi>
</mrow>

<mrow>
<mi>

C

</mi>

<mi>

l

</mi>

<mi>

o

</mi>

<mi>

c

</mi>

<mi>

k

</mi>

<mtext>



</mtext>

<mi>

R

</mi>

<mi>

a

</mi>

<mi>

t

</mi>

<mi>

e

</mi>
</mrow>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

CPU\ Time = \frac{Instructions \times CPI}{Clock\ Rate}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

U

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

T

</span>

<span className="mord,mathnormal">

im

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:2.0463em;vertical-align:-0.686em;">



</span>

<span className="mord">
<span className="mopen,nulldelimiter">



</span>

<span className="mfrac">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:1.3603em;">
<span style="top:-2.314em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

oc

</span>

<span className="mord,mathnormal" style="margin-right:0.0315em;">

k

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.0077em;">

R

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal">

e

</span>
</span>
</span>

<span style="top:-3.23em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="frac-line" style="border-bottom-width:0.04em;">



</span>
</span>

<span style="top:-3.677em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0785em;">

I

</span>

<span className="mord,mathnormal">

n

</span>

<span className="mord,mathnormal">

s

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal">

u

</span>

<span className="mord,mathnormal">

c

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

o

</span>

<span className="mord,mathnormal">

n

</span>

<span className="mord,mathnormal">

s

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

×

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="mord,mathnormal" style="margin-right:0.0785em;">

I

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.686em;">
<span>



</span>
</span>
</span>
</span>
</span>

<span className="mclose,nulldelimiter">



</span>
</span>
</span>
</span>
</span>
</span>

**指令数越少、CPI 越低、时钟周期越短，程序执行越快。**

其中：

**IC / Instructions**：指令数
**CPI**：每条指令平均需要多少个时钟周期
**Clock Cycle Time**：时钟周期时间
**Clock Rate**：时钟频率

算法、编程语言、编译器会影响指令数和 CPI；指令集、微架构、芯片实现会影响 CPI 和时钟周期。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L1-Intro-24.webp)

### 性能比较与加速比

比较两个系统时，不要只看频率，要看执行同一任务的时间。

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

S

</mi>

<mi>

p

</mi>

<mi>

e

</mi>

<mi>

e

</mi>

<mi>

d

</mi>

<mi>

u

</mi>

<mi>

p

</mi>

<mo>

=

</mo>

<mfrac>
<mrow>
<mi>

T

</mi>

<mi>

i

</mi>

<mi>

m

</mi>

<msub>
<mi>

e

</mi>

<mrow>
<mi>

o

</mi>

<mi>

l

</mi>

<mi>

d

</mi>
</mrow>
</msub>
</mrow>

<mrow>
<mi>

T

</mi>

<mi>

i

</mi>

<mi>

m

</mi>

<msub>
<mi>

e

</mi>

<mrow>
<mi>

n

</mi>

<mi>

e

</mi>

<mi>

w

</mi>
</mrow>
</msub>
</mrow>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

Speedup = \frac{Time_{old}}{Time_{new}}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0576em;">

S

</span>

<span className="mord,mathnormal">

p

</span>

<span className="mord,mathnormal">

ee

</span>

<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal">

u

</span>

<span className="mord,mathnormal">

p

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:2.1963em;vertical-align:-0.836em;">



</span>

<span className="mord">
<span className="mopen,nulldelimiter">



</span>

<span className="mfrac">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:1.3603em;">
<span style="top:-2.314em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.1389em;">

T

</span>

<span className="mord,mathnormal">

im

</span>

<span className="mord">
<span className="mord,mathnormal">

e

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

n

</span>

<span className="mord,mathnormal,mtight">

e

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0269em;">

w

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

<span style="top:-3.23em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="frac-line" style="border-bottom-width:0.04em;">



</span>
</span>

<span style="top:-3.677em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.1389em;">

T

</span>

<span className="mord,mathnormal">

im

</span>

<span className="mord">
<span className="mord,mathnormal">

e

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

o

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal,mtight">

d

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.836em;">
<span>



</span>
</span>
</span>
</span>
</span>

<span className="mclose,nulldelimiter">



</span>
</span>
</span>
</span>
</span>
</span>

例如 X 用 10s，Y 用 15s：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

S

</mi>

<mi>

p

</mi>

<mi>

e

</mi>

<mi>

e

</mi>

<mi>

d

</mi>

<mi>

u

</mi>

<mi>

p

</mi>

<mo>

=

</mo>

<mfrac>
<mn>

15

</mn>

<mn>

10

</mn>
</mfrac>

<mo>

=

</mo>

<mn>

1.5

</mn>
</mrow>

<annotation encoding="application/x-tex">

Speedup = \frac{15}{10}=1.5

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0576em;">

S

</span>

<span className="mord,mathnormal">

p

</span>

<span className="mord,mathnormal">

ee

</span>

<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal">

u

</span>

<span className="mord,mathnormal">

p

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:2.0074em;vertical-align:-0.686em;">



</span>

<span className="mord">
<span className="mopen,nulldelimiter">



</span>

<span className="mfrac">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:1.3214em;">
<span style="top:-2.314em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord">

10

</span>
</span>
</span>

<span style="top:-3.23em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="frac-line" style="border-bottom-width:0.04em;">



</span>
</span>

<span style="top:-3.677em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord">

15

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.686em;">
<span>



</span>
</span>
</span>
</span>
</span>

<span className="mclose,nulldelimiter">



</span>
</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.6444em;">



</span>

<span className="mord">

1.5

</span>
</span>
</span>
</span>
</span>

所以 X 比 Y 快 1.5 倍，性能提升是：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mn>

1.5

</mn>

<mo>

−

</mo>

<mn>

1

</mn>

<mo>

=

</mo>

<mn>

50

</mn>

<mi mathvariant="normal">

%

</mi>
</mrow>

<annotation encoding="application/x-tex">

1.5-1=50\%

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.7278em;vertical-align:-0.0833em;">



</span>

<span className="mord">

1.5

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

−

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.6444em;">



</span>

<span className="mord">

1

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8056em;vertical-align:-0.0556em;">



</span>

<span className="mord">

50%

</span>
</span>
</span>
</span>
</span>

注意：**性能提升 50%** 不等于 **执行时间减少 50%**。这个例子中**执行时间只是从 15s 减到 10s，减少了 33%**。

### MIPS 陷阱

MIPS 全称是 **Millions of Instructions Per Second**，即每秒执行几百万条指令：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

M

</mi>

<mi>

I

</mi>

<mi>

P

</mi>

<mi>

S

</mi>

<mo>

=

</mo>

<mfrac>
<mrow>
<mi>

I

</mi>

<mi>

n

</mi>

<mi>

s

</mi>

<mi>

t

</mi>

<mi>

r

</mi>

<mi>

u

</mi>

<mi>

c

</mi>

<mi>

t

</mi>

<mi>

i

</mi>

<mi>

o

</mi>

<mi>

n

</mi>

<mtext>



</mtext>

<mi>

C

</mi>

<mi>

o

</mi>

<mi>

u

</mi>

<mi>

n

</mi>

<mi>

t

</mi>
</mrow>

<mrow>
<mi>

E

</mi>

<mi>

x

</mi>

<mi>

e

</mi>

<mi>

c

</mi>

<mi>

u

</mi>

<mi>

t

</mi>

<mi>

i

</mi>

<mi>

o

</mi>

<mi>

n

</mi>

<mtext>



</mtext>

<mi>

T

</mi>

<mi>

i

</mi>

<mi>

m

</mi>

<mi>

e

</mi>

<mo>

×

</mo>

<msup>
<mn>

10

</mn>

<mn>

6

</mn>
</msup>
</mrow>
</mfrac>

<mo>

=

</mo>

<mfrac>
<mrow>
<mi>

c

</mi>

<mi>

l

</mi>

<mi>

o

</mi>

<mi>

c

</mi>

<mi>

k

</mi>

<mtext>



</mtext>

<mi>

r

</mi>

<mi>

a

</mi>

<mi>

t

</mi>

<mi>

e

</mi>
</mrow>

<mrow>
<mi>

C

</mi>

<mi>

P

</mi>

<mi>

I

</mi>

<mo>

×

</mo>

<msup>
<mn>

10

</mn>

<mn>

6

</mn>
</msup>
</mrow>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

MIPS = \frac{Instruction\ Count}{Execution\ Time \times 10^6} = \frac{clock\ rate}{CPI \times 10^6}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal" style="margin-right:0.0785em;">

I

</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="mord,mathnormal" style="margin-right:0.0576em;">

S

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:2.1297em;vertical-align:-0.7693em;">



</span>

<span className="mord">
<span className="mopen,nulldelimiter">



</span>

<span className="mfrac">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:1.3603em;">
<span style="top:-2.314em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0576em;">

E

</span>

<span className="mord,mathnormal">

x

</span>

<span className="mord,mathnormal">

ec

</span>

<span className="mord,mathnormal">

u

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

o

</span>

<span className="mord,mathnormal">

n

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

T

</span>

<span className="mord,mathnormal">

im

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

×

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mord">

1

</span>

<span className="mord">
<span className="mord">

0

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.7401em;">
<span style="top:-2.989em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">

6

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

<span style="top:-3.23em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="frac-line" style="border-bottom-width:0.04em;">



</span>
</span>

<span style="top:-3.677em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0785em;">

I

</span>

<span className="mord,mathnormal">

n

</span>

<span className="mord,mathnormal">

s

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal">

u

</span>

<span className="mord,mathnormal">

c

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

o

</span>

<span className="mord,mathnormal">

n

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="mord,mathnormal">

o

</span>

<span className="mord,mathnormal">

u

</span>

<span className="mord,mathnormal">

n

</span>

<span className="mord,mathnormal">

t

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.7693em;">
<span>



</span>
</span>
</span>
</span>
</span>

<span className="mclose,nulldelimiter">



</span>
</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:2.1408em;vertical-align:-0.7693em;">



</span>

<span className="mord">
<span className="mopen,nulldelimiter">



</span>

<span className="mfrac">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:1.3714em;">
<span style="top:-2.314em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="mord,mathnormal" style="margin-right:0.0785em;">

I

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

×

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mord">

1

</span>

<span className="mord">
<span className="mord">

0

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.7401em;">
<span style="top:-2.989em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">

6

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

<span style="top:-3.23em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="frac-line" style="border-bottom-width:0.04em;">



</span>
</span>

<span style="top:-3.677em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

c

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

oc

</span>

<span className="mord,mathnormal" style="margin-right:0.0315em;">

k

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal">

e

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.7693em;">
<span>



</span>
</span>
</span>
</span>
</span>

<span className="mclose,nulldelimiter">



</span>
</span>
</span>
</span>
</span>
</span>

但不同 ISA 的“指令”复杂度不同，所以不能直接说 MIPS 高就一定快。比如 MIPS 指令多但 CPI 低，x86 指令少但 CPI 高，最后还是要回到执行时间公式判断。

#### 案例

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L1-Intro-25.webp)

MIPS 处理器：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mfrac>
<mrow>
<mn>

4

</mn>

<mo>

×

</mo>

<msup>
<mn>

10

</mn>

<mn>

9

</mn>
</msup>

<mo>

×

</mo>

<mn>

1.5

</mn>
</mrow>

<mrow>
<mn>

1

</mn>

<mo>

×

</mo>

<msup>
<mn>

10

</mn>

<mn>

9

</mn>
</msup>
</mrow>
</mfrac>

<mo>

=

</mo>

<mn>

6

</mn>

<mi>

s

</mi>
</mrow>

<annotation encoding="application/x-tex">

\frac{4\times10^9 \times 1.5}{1\times10^9}=6s

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.4213em;vertical-align:-0.4033em;">



</span>

<span className="mord">
<span className="mopen,nulldelimiter">



</span>

<span className="mfrac">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:1.0179em;">
<span style="top:-2.655em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">

1

</span>

<span className="mbin,mtight">

×

</span>

<span className="mord,mtight">

1

</span>

<span className="mord,mtight">
<span className="mord,mtight">

0

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.7463em;">
<span style="top:-2.786em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
<span className="mord,mtight">

9

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

<span style="top:-3.23em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="frac-line" style="border-bottom-width:0.04em;">



</span>
</span>

<span style="top:-3.394em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">

4

</span>

<span className="mbin,mtight">

×

</span>

<span className="mord,mtight">

1

</span>

<span className="mord,mtight">
<span className="mord,mtight">

0

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8913em;">
<span style="top:-2.931em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
<span className="mord,mtight">

9

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

<span className="mbin,mtight">

×

</span>

<span className="mord,mtight">

1.5

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.4033em;">
<span>



</span>
</span>
</span>
</span>
</span>

<span className="mclose,nulldelimiter">



</span>
</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.6444em;">



</span>

<span className="mord">

6

</span>

<span className="mord,mathnormal">

s

</span>
</span>
</span>
</span>



x86 处理器：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mfrac>
<mrow>
<mn>

2

</mn>

<mo>

×

</mo>

<msup>
<mn>

10

</mn>

<mn>

9

</mn>
</msup>

<mo>

×

</mo>

<mn>

6

</mn>
</mrow>

<mrow>
<mn>

1.5

</mn>

<mo>

×

</mo>

<msup>
<mn>

10

</mn>

<mn>

9

</mn>
</msup>
</mrow>
</mfrac>

<mo>

=

</mo>

<mn>

8

</mn>

<mi>

s

</mi>
</mrow>

<annotation encoding="application/x-tex">

\frac{2\times10^9 \times 6}{1.5\times10^9}=8s

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.4213em;vertical-align:-0.4033em;">



</span>

<span className="mord">
<span className="mopen,nulldelimiter">



</span>

<span className="mfrac">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:1.0179em;">
<span style="top:-2.655em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">

1.5

</span>

<span className="mbin,mtight">

×

</span>

<span className="mord,mtight">

1

</span>

<span className="mord,mtight">
<span className="mord,mtight">

0

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.7463em;">
<span style="top:-2.786em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
<span className="mord,mtight">

9

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

<span style="top:-3.23em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="frac-line" style="border-bottom-width:0.04em;">



</span>
</span>

<span style="top:-3.394em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">

2

</span>

<span className="mbin,mtight">

×

</span>

<span className="mord,mtight">

1

</span>

<span className="mord,mtight">
<span className="mord,mtight">

0

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8913em;">
<span style="top:-2.931em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
<span className="mord,mtight">

9

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

<span className="mbin,mtight">

×

</span>

<span className="mord,mtight">

6

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.4033em;">
<span>



</span>
</span>
</span>
</span>
</span>

<span className="mclose,nulldelimiter">



</span>
</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.6444em;">



</span>

<span className="mord">

8

</span>

<span className="mord,mathnormal">

s

</span>
</span>
</span>
</span>



所以这个例子中 **MIPS 处理器更快**。

### 性能改善不一定等于整体改善

**只改进系统某一部分，不能期待整体性能按同样比例提升**。系统性能要看整体瓶颈。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L1-Intro-26.webp)

下面的Turbo Boost 例子说明：提高频率可能减少执行时间，但也会改变动态功耗。

#### 案例

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L1-Intro-27.webp)

> 依据动态功耗公式：<span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msub>
> <mi>
> 
> P
> 
> </mi>
> 
> <mrow>
> <mi>
> 
> d
> 
> </mi>
> 
> <mi>
> 
> y
> 
> </mi>
> 
> <mi>
> 
> n
> 
> </mi>
> 
> <mi>
> 
> a
> 
> </mi>
> 
> <mi>
> 
> m
> 
> </mi>
> 
> <mi>
> 
> i
> 
> </mi>
> 
> <mi>
> 
> c
> 
> </mi>
> </mrow>
> </msub>
> 
> <mo>
> 
> =
> 
> </mo>
> 
> <mi>
> 
> A
> 
> </mi>
> 
> <mi>
> 
> c
> 
> </mi>
> 
> <mi>
> 
> t
> 
> </mi>
> 
> <mi>
> 
> i
> 
> </mi>
> 
> <mi>
> 
> v
> 
> </mi>
> 
> <mi>
> 
> i
> 
> </mi>
> 
> <mi>
> 
> t
> 
> </mi>
> 
> <mi>
> 
> y
> 
> </mi>
> 
> <mo>
> 
> ×
> 
> </mo>
> 
> <mi>
> 
> C
> 
> </mi>
> 
> <mo>
> 
> ×
> 
> </mo>
> 
> <msup>
> <mi>
> 
> V
> 
> </mi>
> 
> <mn>
> 
> 2
> 
> </mn>
> </msup>
> 
> <mo>
> 
> ×
> 
> </mo>
> 
> <mi>
> 
> f
> 
> </mi>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> P_{dynamic}=Activity×C×V^2×f
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:0.9694em;vertical-align:-0.2861em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> <span className="mord,mathnormal" style="margin-right:0.1389em;">
> 
> P
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3361em;">
> <span style="top:-2.55em;margin-left:-0.1389em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mtight">
> <span className="mord,mathnormal,mtight">
> 
> d
> 
> </span>
> 
> <span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">
> 
> y
> 
> </span>
> 
> <span className="mord,mathnormal,mtight">
> 
> nami
> 
> </span>
> 
> <span className="mord,mathnormal,mtight">
> 
> c
> 
> </span>
> </span>
> </span>
> </span>
> </span>
> 
> <span className="vlist-s">
> 
> ​
> 
> </span>
> </span>
> 
> <span className="vlist-r">
> <span className="vlist" style="height:0.2861em;">
> <span>
> 
> 
> 
> </span>
> </span>
> </span>
> </span>
> </span>
> </span>
> 
> <span className="mspace" style="margin-right:0.2778em;">
> 
> 
> 
> </span>
> 
> <span className="mrel">
> 
> =
> 
> </span>
> 
> <span className="mspace" style="margin-right:0.2778em;">
> 
> 
> 
> </span>
> </span>
> 
> <span className="base">
> <span className="strut" style="height:0.8778em;vertical-align:-0.1944em;">
> 
> 
> 
> </span>
> 
> <span className="mord,mathnormal">
> 
> A
> 
> </span>
> 
> <span className="mord,mathnormal">
> 
> c
> 
> </span>
> 
> <span className="mord,mathnormal">
> 
> t
> 
> </span>
> 
> <span className="mord,mathnormal">
> 
> i
> 
> </span>
> 
> <span className="mord,mathnormal" style="margin-right:0.0359em;">
> 
> v
> 
> </span>
> 
> <span className="mord,mathnormal">
> 
> i
> 
> </span>
> 
> <span className="mord,mathnormal">
> 
> t
> 
> </span>
> 
> <span className="mord,mathnormal" style="margin-right:0.0359em;">
> 
> y
> 
> </span>
> 
> <span className="mspace" style="margin-right:0.2222em;">
> 
> 
> 
> </span>
> 
> <span className="mbin">
> 
> ×
> 
> </span>
> 
> <span className="mspace" style="margin-right:0.2222em;">
> 
> 
> 
> </span>
> </span>
> 
> <span className="base">
> <span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">
> 
> 
> 
> </span>
> 
> <span className="mord,mathnormal" style="margin-right:0.0715em;">
> 
> C
> 
> </span>
> 
> <span className="mspace" style="margin-right:0.2222em;">
> 
> 
> 
> </span>
> 
> <span className="mbin">
> 
> ×
> 
> </span>
> 
> <span className="mspace" style="margin-right:0.2222em;">
> 
> 
> 
> </span>
> </span>
> 
> <span className="base">
> <span className="strut" style="height:0.8974em;vertical-align:-0.0833em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> <span className="mord,mathnormal" style="margin-right:0.2222em;">
> 
> V
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t">
> <span className="vlist-r">
> <span className="vlist" style="height:0.8141em;">
> <span style="top:-3.063em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mtight">
> 
> 2
> 
> </span>
> </span>
> </span>
> </span>
> </span>
> </span>
> </span>
> </span>
> 
> <span className="mspace" style="margin-right:0.2222em;">
> 
> 
> 
> </span>
> 
> <span className="mbin">
> 
> ×
> 
> </span>
> 
> <span className="mspace" style="margin-right:0.2222em;">
> 
> 
> 
> </span>
> </span>
> 
> <span className="base">
> <span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">
> 
> 
> 
> </span>
> 
> <span className="mord,mathnormal" style="margin-right:0.1076em;">
> 
> f
> 
> </span>
> </span>
> </span>
> </span>
> 
> 
> 
> 依据执行时间公式是：<span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <mi>
> 
> E
> 
> </mi>
> 
> <mi>
> 
> x
> 
> </mi>
> 
> <mi>
> 
> e
> 
> </mi>
> 
> <mi>
> 
> c
> 
> </mi>
> 
> <mi>
> 
> u
> 
> </mi>
> 
> <mi>
> 
> t
> 
> </mi>
> 
> <mi>
> 
> i
> 
> </mi>
> 
> <mi>
> 
> o
> 
> </mi>
> 
> <mi>
> 
> n
> 
> </mi>
> 
> <mtext>
> 
> 
> 
> </mtext>
> 
> <mi>
> 
> T
> 
> </mi>
> 
> <mi>
> 
> i
> 
> </mi>
> 
> <mi>
> 
> m
> 
> </mi>
> 
> <mi>
> 
> e
> 
> </mi>
> 
> <mo>
> 
> =
> 
> </mo>
> 
> <mfrac>
> <mrow>
> <mi>
> 
> I
> 
> </mi>
> 
> <mi>
> 
> n
> 
> </mi>
> 
> <mi>
> 
> s
> 
> </mi>
> 
> <mi>
> 
> t
> 
> </mi>
> 
> <mi>
> 
> r
> 
> </mi>
> 
> <mi>
> 
> u
> 
> </mi>
> 
> <mi>
> 
> c
> 
> </mi>
> 
> <mi>
> 
> t
> 
> </mi>
> 
> <mi>
> 
> i
> 
> </mi>
> 
> <mi>
> 
> o
> 
> </mi>
> 
> <mi>
> 
> n
> 
> </mi>
> 
> <mtext>
> 
> 
> 
> </mtext>
> 
> <mi>
> 
> C
> 
> </mi>
> 
> <mi>
> 
> o
> 
> </mi>
> 
> <mi>
> 
> u
> 
> </mi>
> 
> <mi>
> 
> n
> 
> </mi>
> 
> <mi>
> 
> t
> 
> </mi>
> 
> <mo>
> 
> ×
> 
> </mo>
> 
> <mi>
> 
> C
> 
> </mi>
> 
> <mi>
> 
> P
> 
> </mi>
> 
> <mi>
> 
> I
> 
> </mi>
> </mrow>
> 
> <mrow>
> <mi>
> 
> C
> 
> </mi>
> 
> <mi>
> 
> l
> 
> </mi>
> 
> <mi>
> 
> o
> 
> </mi>
> 
> <mi>
> 
> c
> 
> </mi>
> 
> <mi>
> 
> k
> 
> </mi>
> 
> <mtext>
> 
> 
> 
> </mtext>
> 
> <mi>
> 
> R
> 
> </mi>
> 
> <mi>
> 
> a
> 
> </mi>
> 
> <mi>
> 
> t
> 
> </mi>
> 
> <mi>
> 
> e
> 
> </mi>
> </mrow>
> </mfrac>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> Execution\ Time = \frac{Instruction\ Count \times CPI}{Clock\ Rate}
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:0.6833em;">
> 
> 
> 
> </span>
> 
> <span className="mord,mathnormal" style="margin-right:0.0576em;">
> 
> E
> 
> </span>
> 
> <span className="mord,mathnormal">
> 
> x
> 
> </span>
> 
> <span className="mord,mathnormal">
> 
> ec
> 
> </span>
> 
> <span className="mord,mathnormal">
> 
> u
> 
> </span>
> 
> <span className="mord,mathnormal">
> 
> t
> 
> </span>
> 
> <span className="mord,mathnormal">
> 
> i
> 
> </span>
> 
> <span className="mord,mathnormal">
> 
> o
> 
> </span>
> 
> <span className="mord,mathnormal">
> 
> n
> 
> </span>
> 
> <span className="mspace">
> 
> 
> 
> </span>
> 
> <span className="mord,mathnormal" style="margin-right:0.1389em;">
> 
> T
> 
> </span>
> 
> <span className="mord,mathnormal">
> 
> im
> 
> </span>
> 
> <span className="mord,mathnormal">
> 
> e
> 
> </span>
> 
> <span className="mspace" style="margin-right:0.2778em;">
> 
> 
> 
> </span>
> 
> <span className="mrel">
> 
> =
> 
> </span>
> 
> <span className="mspace" style="margin-right:0.2778em;">
> 
> 
> 
> </span>
> </span>
> 
> <span className="base">
> <span className="strut" style="height:1.2173em;vertical-align:-0.345em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> <span className="mopen,nulldelimiter">
> 
> 
> 
> </span>
> 
> <span className="mfrac">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.8723em;">
> <span style="top:-2.655em;">
> <span className="pstrut" style="height:3em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mtight">
> <span className="mord,mathnormal,mtight" style="margin-right:0.0715em;">
> 
> C
> 
> </span>
> 
> <span className="mord,mathnormal,mtight" style="margin-right:0.0197em;">
> 
> l
> 
> </span>
> 
> <span className="mord,mathnormal,mtight">
> 
> oc
> 
> </span>
> 
> <span className="mord,mathnormal,mtight" style="margin-right:0.0315em;">
> 
> k
> 
> </span>
> 
> <span className="mspace,mtight">
> <span className="mtight">
> 
> 
> 
> </span>
> </span>
> 
> <span className="mord,mathnormal,mtight" style="margin-right:0.0077em;">
> 
> R
> 
> </span>
> 
> <span className="mord,mathnormal,mtight">
> 
> a
> 
> </span>
> 
> <span className="mord,mathnormal,mtight">
> 
> t
> 
> </span>
> 
> <span className="mord,mathnormal,mtight">
> 
> e
> 
> </span>
> </span>
> </span>
> </span>
> 
> <span style="top:-3.23em;">
> <span className="pstrut" style="height:3em;">
> 
> 
> 
> </span>
> 
> <span className="frac-line" style="border-bottom-width:0.04em;">
> 
> 
> 
> </span>
> </span>
> 
> <span style="top:-3.394em;">
> <span className="pstrut" style="height:3em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mtight">
> <span className="mord,mathnormal,mtight" style="margin-right:0.0785em;">
> 
> I
> 
> </span>
> 
> <span className="mord,mathnormal,mtight">
> 
> n
> 
> </span>
> 
> <span className="mord,mathnormal,mtight">
> 
> s
> 
> </span>
> 
> <span className="mord,mathnormal,mtight">
> 
> t
> 
> </span>
> 
> <span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">
> 
> r
> 
> </span>
> 
> <span className="mord,mathnormal,mtight">
> 
> u
> 
> </span>
> 
> <span className="mord,mathnormal,mtight">
> 
> c
> 
> </span>
> 
> <span className="mord,mathnormal,mtight">
> 
> t
> 
> </span>
> 
> <span className="mord,mathnormal,mtight">
> 
> i
> 
> </span>
> 
> <span className="mord,mathnormal,mtight">
> 
> o
> 
> </span>
> 
> <span className="mord,mathnormal,mtight">
> 
> n
> 
> </span>
> 
> <span className="mspace,mtight">
> <span className="mtight">
> 
> 
> 
> </span>
> </span>
> 
> <span className="mord,mathnormal,mtight" style="margin-right:0.0715em;">
> 
> C
> 
> </span>
> 
> <span className="mord,mathnormal,mtight">
> 
> o
> 
> </span>
> 
> <span className="mord,mathnormal,mtight">
> 
> u
> 
> </span>
> 
> <span className="mord,mathnormal,mtight">
> 
> n
> 
> </span>
> 
> <span className="mord,mathnormal,mtight">
> 
> t
> 
> </span>
> 
> <span className="mbin,mtight">
> 
> ×
> 
> </span>
> 
> <span className="mord,mathnormal,mtight" style="margin-right:0.0715em;">
> 
> C
> 
> </span>
> 
> <span className="mord,mathnormal,mtight" style="margin-right:0.1389em;">
> 
> P
> 
> </span>
> 
> <span className="mord,mathnormal,mtight" style="margin-right:0.0785em;">
> 
> I
> 
> </span>
> </span>
> </span>
> </span>
> </span>
> 
> <span className="vlist-s">
> 
> ​
> 
> </span>
> </span>
> 
> <span className="vlist-r">
> <span className="vlist" style="height:0.345em;">
> <span>
> 
> 
> 
> </span>
> </span>
> </span>
> </span>
> </span>
> 
> <span className="mclose,nulldelimiter">
> 
> 
> 
> </span>
> </span>
> </span>
> </span>
> </span>

正常模式能量是：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mn>

100

</mn>

<mi>

W

</mi>

<mo>

×

</mo>

<mn>

100

</mn>

<mi>

s

</mi>

<mo>

=

</mo>

<mn>

10000

</mn>

<mi>

J

</mi>
</mrow>

<annotation encoding="application/x-tex">

100W \times 100s = 10000J

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">



</span>

<span className="mord">

100

</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

W

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
<span className="strut" style="height:0.6444em;">



</span>

<span className="mord">

100

</span>

<span className="mord,mathnormal">

s

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord">

10000

</span>

<span className="mord,mathnormal" style="margin-right:0.0962em;">

J

</span>
</span>
</span>
</span>
</span>

Turbo 模式：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mo stretchy="false">

(

</mo>

<mn>

70

</mn>

<mo>

×

</mo>

<mn>

1.2

</mn>

<mo>

+

</mo>

<mn>

30

</mn>

<mo stretchy="false">

)

</mo>

<mo>

×

</mo>

<mfrac>
<mn>

100

</mn>

<mn>

1.2

</mn>
</mfrac>

<mo>

=

</mo>

<mn>

9500

</mn>

<mi>

J

</mi>
</mrow>

<annotation encoding="application/x-tex">

(70\times1.2+30)\times\frac{100}{1.2}=9500J

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mopen">

(

</span>

<span className="mord">

70

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
<span className="strut" style="height:0.7278em;vertical-align:-0.0833em;">



</span>

<span className="mord">

1.2

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord">

30

</span>

<span className="mclose">

)

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
<span className="strut" style="height:2.0074em;vertical-align:-0.686em;">



</span>

<span className="mord">
<span className="mopen,nulldelimiter">



</span>

<span className="mfrac">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:1.3214em;">
<span style="top:-2.314em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord">

1.2

</span>
</span>
</span>

<span style="top:-3.23em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="frac-line" style="border-bottom-width:0.04em;">



</span>
</span>

<span style="top:-3.677em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord">

100

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.686em;">
<span>



</span>
</span>
</span>
</span>
</span>

<span className="mclose,nulldelimiter">



</span>
</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord">

9500

</span>

<span className="mord,mathnormal" style="margin-right:0.0962em;">

J

</span>
</span>
</span>
</span>
</span>

所以在该假设下 Turbo 模式能量更少。注意前提是：**频率只影响动态功耗，不影响漏电功耗，并假设 CPI 不变**。
