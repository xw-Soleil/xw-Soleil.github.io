# Chapter 13：存储器 Memory

> 存储器的层次结构与访问时序，以及 SRAM 单元的读写电路设计。

## Memory 结构

### 1维存储结构

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter13-Memory-01.webp)

### 2维存储结构

大容量存储器不能再做成一个巨大的单一阵列，而是要分成多个小 block，通过层次化寻址来访问。

**优势**：**每个 block 内部连线更短**，速度更快、延迟更小； **一次只激活一个 block**，不用让整个大存储阵列工作，所以可以降低功耗。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter13-Memory-02.webp)

### 阵列结构

阵列布局方面，减少行数、增加列数，从而让存储阵列更接近方形、更容易布局。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter13-Memory-03.webp)

## Memory 时序定义

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter13-Memory-04.webp)

**Read cycle** 表示两次读操作之间所需要的最短时间间隔。

**Read access** 表示从发出读命令开始，到数据变得有效所需要的时间。

**Write cycle** 表示两次写操作之间所需要的最短时间间隔。

**Write access** 表示写操作从开始到真正写入完成所需的时间。

### 内存访问时序

DRAM 使用**地址复用，**地址总线不是一次性给出完整地址，而是分两步给。

**RAS：Row Access Strobe，行访问选通信号**

**CAS：Column Access Strobe，列访问选通信号**

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter13-Memory-05.webp)

SRAM 通常不需要像 DRAM 那样分行地址和列地址两次送入。地址发生变化，就触发 SRAM 开始读写操作。

**即self-timed，自定时**，即 SRAM 内部电路根据地址变化自动完成访问控制。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter13-Memory-06.webp)

## RAM | Random Access Memory

### 分类

> 了解

#### Static RAM | 静态随机存储器

**数据保持方式**：只要电源存在，数据就一直保存在电路中；

**存储单元较大**：通常一个 bit 需要 **6 个晶体管**，也就是 6T SRAM；

**单位芯片容量较小**：因为每个 bit 占面积大，所以同样面积下能存的 bit 数较少；

**速度快**：读写速度很高；

**常用于 Cache**：比如 CPU 的 L1/L2/L3 缓存；

**差分输出**：通常有两根位线，**BL 和 !BL**，分别表示数据和反相信号；

**需要 sense amplifier**：感应放大器用于快速判断 BL 和 !BL 的电压差，提高读取速度；

**兼容 CMOS 工艺**：容易和普通逻辑电路一起集成。

#### Dynamic RAM | 动态随机存储器

**需要周期性刷新**：否则电容中的电荷逐渐泄漏，数据会丢失；

**存储单元较小**：一个 bit 通常只需要 **1 个晶体管 + 1 个电容**，有时也可说 1 到 3 个晶体管；

**单位芯片容量大**：因为单元面积小，所以同样面积可以存更多 bit；

**速度比 SRAM 慢**；

**常用于主存**：比如电脑内存条中的 DDR DRAM；

**单端输出**：通常只通过一根位线 **BL** 输出；

**必须使用 sense amplifier**：因为电容存储的电压变化很小，需要感应放大器才能正确读出；

**不太适合普通 CMOS 工艺**：因为 DRAM 通常需要特殊的电容结构和制造工艺。

## SRAM

SRAM cell 是 SRAM 的最基本存储单元，每个 cell 必须具备**存储 1 bit 信息、支持读操作和写操作**的功能。

### 12T SRAM 单元

由 **12 个晶体管 transistor** 构成的 SRAM 单元。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter13-Memory-07.webp)

一个简单的 **latch**，用于保存 0/1； 与 **bitline 位线** 相连，用于读写数据； 具备独立的读写控制信号

> `write_b` 一般表示是 `write` 的反相控制。

### 6T SRAM 单元

6T SRAM 是最常见的静态存储单元，由 **6 个晶体管**组成，核心是两个**交叉耦合反相器**，用来稳定保存 0 或 1。

**word line（字线）**：控制该存储单元是否被选中。

**bit / bit_b（位线及反位线）**：用于读出或写入数据，是一对互补信号线。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter13-Memory-08.webp)

### SRAM 读

**读的过程**：先把两条位线 **bit 和 bit_b 都预充到高电平**。然后拉高 **word line（字线）**，打开两侧访问晶体管，使存储节点和位线连接。

#### **举例**：

单元内部存的是 **A = 0，A_b = 1**

字线打开后，左侧位线 **bit** 会通过存储单元被下拉放电

右侧位线 **bit_b** 仍保持高电平

之后通过比较 bit 和 bit_b 的**电压差**，就能读出数据

<alert type="tip">

**真实 SRAM 读操作基本就是利用 bit 和 bit_b 的电压差来读出数据**，但不是让 CPU 或普通逻辑门直接去比较，而是用专门的 **sense amplifier（灵敏放大器/读出放大器）**把这个很小的差值快速放大成完整的数字 0 或 1，**不需要等 bit 完全放电到 0**。

</alert>

#### 读稳定性

读的时候不能把原来存的 0 误翻转成 1，所以要求下拉管 **N1 要比访问管 N2 强**，即 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mo stretchy="false">

(

</mo>

<mi>

W

</mi>

<mi mathvariant="normal">

/

</mi>

<mi>

L

</mi>

<msub>
<mo stretchy="false">

)

</mo>

<mrow>
<mi>

N

</mi>

<mn>

1

</mn>
</mrow>
</msub>

<mo>

>
</mo>

<mo>

>
</mo>

<mo stretchy="false">

(

</mo>

<mi>

W

</mi>

<mi mathvariant="normal">

/

</mi>

<mi>

L

</mi>

<msub>
<mo stretchy="false">

)

</mo>

<mrow>
<mi>

N

</mi>

<mn>

2

</mn>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

(W/L)_{N1}>>(W/L)_{N2}

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

<span className="mord,mathnormal" style="margin-right:0.1389em;">

W

</span>

<span className="mord">

/

</span>

<span className="mord,mathnormal">

L

</span>

<span className="mclose">
<span className="mclose">

)

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.109em;">

N

</span>

<span className="mord,mtight">

1

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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

>>
</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mopen">

(

</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

W

</span>

<span className="mord">

/

</span>

<span className="mord,mathnormal">

L

</span>

<span className="mclose">
<span className="mclose">

)

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.109em;">

N

</span>

<span className="mord,mtight">

2

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

这样即使 bit 是高电平，也不会把节点 A 拉得太高。

在下图中看到，字线导通后，A处的电压稍微抬升后依然被下拉到地，说明下拉管在起作用。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter13-Memory-09.webp)

### SRAM 写

**写的过程**：先在位线上放入要写入的数据，然后拉高字线，N2和N4打开，位线强行改变内部节点的电位。

#### 写的能力

位线和访问管（如N2，N4）必须能压过原来 SRAM 单元内部的反馈保持能力。

<alert type="tip">

ppt中给出的案例：A_b原本存1，现在bit_b要把A_b强制写为0。此时 **P2** 想继续把内部节点拉高，保持旧数据； **N4** 想通过低电平 bit_b 线把内部节点拉低，写入新数据。就需要**访问管 N4 的导通能力要强于上拉管 P2**，这样才能把内部高电平节点拉低。（原ppt的图有些不对应）

</alert>

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter13-Memory-10.webp)

### SRAM 单元尺寸设计

读操作时：高电平位线不能破坏单元

写操作时：低电平位线必须能写入新值

**下拉 NMOS 强>访问 NMOS 中等>上拉 PMOS 弱**

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter13-Memory-11.webp)

### 4*4 SRAM memory

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter13-Memory-12.webp)

### 电阻负载的 SRAM 单元

存在静态功耗：只要电阻某一侧 NMOS 导通，就会有直流电流。

使用大电阻减少静态功耗，是上拉电阻太大，会影响传播延时<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

t

</mi>

<mi>

p

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

t_p

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9012em;vertical-align:-0.2861em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

t

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

p

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.2861em;">
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

，所以位线通常要预充到<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

V

</mi>

<mrow>
<mi>

D

</mi>

<mi>

D

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

V_{DD}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.2222em;">

V

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

D

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

D

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

来提高读写速度。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter13-Memory-13.webp)

### 经典 SRAM 单元对比

> **TFT Cell** 指的是 **薄膜晶体管负载 SRAM 单元**。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter13-Memory-14.webp)

### SRAM ATD | 地址跳变检测电路

ATD | Address Transition Detection

**原理**：输入的地址信号，分两路：一路是原始信号，一路延时单元。一旦任意地址发生变化，由异或门识别出来，输出脉冲被ATD电路识别到后，会经过反相器输出一个ATD脉冲。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter13-Memory-15.webp)

> ATD的作用：
> 
> 协助 SRAM 一旦检测到地址变化，就知道用户要访问新的存储单元。
> 
> ATD 脉冲可以用来启动内部操作，例如：预充电 bit line； 关闭旧的 word line； 打开新的 word line； 启动 sense amplifier； 控制读写时序。

## DRAM

### 3T DRAM Cell

#### 电路结构

**M1**是**写入**管，由 **WWL（Write Word Line，写字线）** 控制，把 **BL1** 上的数据写入存储节点 **X**。

**Cs**是**存储**电容，用来保存数据，节点 **X** 上的电压代表存储的 0 或 1。

**M2 + M3**组成**读出**通路，由节点 **X** 控制 M2，RWL 控制 M3，通过 **BL2** 读出数据。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter13-Memory-16.webp)

#### 关键特点

1. 不像 SRAM 那样要求晶体管强弱比例严格匹配，<mark>

尺寸约束较小。

</mark>
2. 读操作是不会破坏节点**X**上存储的电荷的。原因：读出时 X 只是控制 M2 的栅极，没有直接接到位线。
3. 写入 1 时，**X** 节点只能达到 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

V

</mi>

<mrow>
<mi>

W

</mi>

<mi>

W

</mi>

<mi>

L

</mi>
</mrow>
</msub>

<mo>

−

</mo>

<msub>
<mi>

V

</mi>

<mrow>
<mi>

t

</mi>

<mi>

n

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

V_{WWL}-V_{tn}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.2222em;">

V

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.1389em;">

W

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.1389em;">

W

</span>

<span className="mord,mathnormal,mtight">

L

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

−

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.2222em;">

V

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

t

</span>

<span className="mord,mathnormal,mtight">

n

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

。原因：**M1** NMOS管传输高电平会损失一个阈值电压。
4. **读操作**之前，**BL2** 先预充电到**高电平**。

### 1T DRAM Cell

#### 电路结构

**M1**：访问晶体管，由 **WL（字线）** 控制。

**Cs**：存储电容，用来保存数据。

**BL**：位线，用来写入或读出数据。

**X**：存储节点，X 上的电压表示存的是 0 还是 1。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter13-Memory-17.webp)

#### **写操作**

WL 拉高，M1 导通，把 BL 线中存储的数据写入 X。当写入“1”的时候，会损失一个阈值电压，即最高是<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

V

</mi>

<mrow>
<mi>

d

</mi>

<mi>

d

</mi>
</mrow>
</msub>

<mo>

−

</mo>

<msub>
<mi>

V

</mi>

<mi>

t

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

V_{dd}-V_t

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.2222em;">

V

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

dd

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

−

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.2222em;">

V

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

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



#### **读操作**

读之前，**BL 通常预充到** <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

V

</mi>

<mrow>
<mi>

d

</mi>

<mi>

d

</mi>
</mrow>
</msub>

<mi mathvariant="normal">

/

</mi>

<mn>

2

</mn>
</mrow>

<annotation encoding="application/x-tex">

V_{dd}/2

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.2222em;">

V

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

dd

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

<span className="mord">

/2

</span>
</span>
</span>
</span>

。

当 WL 拉高后，M1 导通，存储电容 **Cs** 和位线电容 **CBL** 相连，二者发生 **电荷共享**。

- 如果原来 X 存的是 1，BL 电压会产生一个很小的上升或变化；
- 如果原来 X 存的是 0，BL 电压会产生相反方向的小变化。

然后由 **sense amplifier，灵敏放大器** 判断这个微小电压差。

<alert type="tip">

此时的读操作是具有**破坏性**的，需要在读后进行**刷新**。

DRAM 的**刷新**就是在读出并放大数据后，利用**灵敏放大器**把完整的 0 或 1 重新写回存储电容。

实际 DRAM 中，即使没有外部读操作，也会周期性地逐行打开字线，让灵敏放大器读出并写回，这就是 **周期刷新 refresh**。

</alert>

#### 1T DRAM 存储单元的重要特点

1. 1T DRAM 存储单元是**单端**结构，只有一根**位线**来读出数据。因此读出时，灵敏放大器只能检测位线上的一个很小电压变化，而不是直接比较一对互补信号，所以**灵敏放大器设计会更复杂**。
2. 由于读操作依赖电荷重新分布，也就是BL线上的电压的微小变化，因此1T DRAM 每根位线都需要灵敏放大器。
3. 1T DRAM 的读操作是破坏性的，读完后必须刷新来恢复数据。
4. 1T DRAM 需要额外的存储电容，并且这个电容必须在版图和工艺中**专门设计**出来。
5. 写入 1 时会损失一个阈值电压，可以通过把字线电压自举到高于Vdd来解决。

## ROM | Read-Only Memory

ROM 具有非易失性，断电以后也能保留其中存储的内容。

掩膜编程 ROM 中，每一位数据通常用一个晶体管来表示。某个位置是否存在晶体管，决定该位存储是 1 还是 0。

### ROM Cells

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter13-Memory-18.webp)

#### Diode ROM

**存1**：该位置**有二极管**。WL 选通后，电流通过二极管流到 BL，BL 得到高电平，约为<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

V

</mi>

<mrow>
<mi>

W

</mi>

<mi>

L

</mi>
</mrow>
</msub>

<mo>

−

</mo>

<msub>
<mi>

V

</mi>

<mrow>
<mi>

D

</mi>

<mi>

o

</mi>

<mi>

n

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

V_{WL}-V_{Don}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.2222em;">

V

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.1389em;">

W

</span>

<span className="mord,mathnormal,mtight">

L

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

−

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.2222em;">

V

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

D

</span>

<span className="mord,mathnormal,mtight">

o

</span>

<span className="mord,mathnormal,mtight">

n

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

。损失一个二极管的导通压降。

**存0**：该位置**没有二极管。BL 通过电阻被拉低，所以读出 0。**

#### MOS ROM

分成两种相反的表示方式。

##### 第一种

用MOS管连通到Vdd。

**存1**：该位置**有MOS管**。WL 选通后，MOS 管给 BL 提供**上拉电流**，BL 变高。

**存0**：该位置**没有MOS管**。BL 不能被拉高，读出 0。

##### 第二种

用MOS管连通到GND，BL线默认上拉到Vdd

**存1**：该位置**没有MOS管，**BL 保持高电平。

**存0**：该位置**有MOS管**。WL 选通后 MOS 管导通，把 BL 拉到 GND，读出 0。

### MOS OR ROM

同一条位线 BL 上，可能连接**多个**来自**不同 WL 的 MOS 管**。只要**某一条**被选中的 WL 上对应的 MOS 管存在并导通，这条 BL 就会被拉到高电平，相当于多个可能的上拉路径对位线做“或”操作。所以它叫 **OR ROM**。

- <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

V

</mi>

<mrow>
<mi>

b

</mi>

<mi>

i

</mi>

<mi>

a

</mi>

<mi>

s

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

V_{bias}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.2222em;">

V

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

bia

</span>

<span className="mord,mathnormal,mtight">

s

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

保证每一条位线默认**下拉到GND**。
- OR ROM 阵列中**有MOS管**表示“1”，没有表示“0”。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter13-Memory-19.webp)

### MOS NOR ROM

因为同一条位线上，多个 NMOS 管是**并联下拉**关系，只要有一个被选中的 NMOS 管导通，位线就会被拉低，从逻辑形式上看是 **NOR 结构**

位线默认被上拉为 1，选中字线后，如果该位置有 NMOS 管，就把位线拉到 0。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter13-Memory-20.webp)

#### Precharged NOR ROM

普通MOS NOR ROM中，每条位线 BL 上方有上拉器件，默认把位线拉到 1。但这样存在的问题是：上拉器件一直存在,当某个 NMOS 导通把 BL 拉低时，会形成从 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

V

</mi>

<mrow>
<mi>

D

</mi>

<mi>

D

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

V_{DD}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.2222em;">

V

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

D

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

D

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

 到 GND 的直流通路,会产生**静态功耗**，而且速度也受上拉管影响。 所以这里改成**预充电结构**。

**工作流程：**

1. Precharge 预充电，把所有位线先充到高电平后预充电关闭。
2. Evaluate 读出，选中某一条字线，如果该 WL 和某条 BL 交叉处 **有 NMOS**，NMOS 导通，位线被拉到 GND，读出 **0**。 如果该位置 **没有 NMOS**，位线没有放电路径，保持高电平，读出 **1**。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter13-Memory-21.webp)

### MOS NAND ROM

位线默认被上拉为 1，通过BL线上**串联的NMOS** 是否能导通到 GND 来决定读出 0 或 1。

#### 读出流程

读取某一行时，其他行的 WL = 1，对应 NMOS 导通，被选中行的 WL = 0。**与NOR ROM不同**

- 如果选中位置 **有 NMOS 管**，这个 NMOS 截止，串联通路断开，BL 保持高电平，读出 **1。**
- 如果选中位置 **没有 NMOS 管**，该位置相当于没有断点，整条串联通路可能导通到 GND，BL 被拉低，读出 **0**。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter13-Memory-22.webp)

### 例子

例子中使用伪NMOS电路，使用弱PMOS上拉，下面的NMOS接地，属于是NOR ROM结构。

但是由于输出经过反相器输出，此时的ROM等效为有NMOS的位置表示“1”，因此画为右下的点状图。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter13-Memory-23.webp)

### MOS NOR ROM Layout

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter13-Memory-24.webp)

### 针对 NOR ROM 的瞬态模型

字线 **WL** 是用 **poly 多晶硅** 做的，电阻比较大，而且它要驱动一整行晶体管的**栅极**，所以会有明显的 RC 延迟。

位线 BL 是用 **metal1 金属一层** 做的，所以电阻比字线小很多，但位线连接很多单元的**漏端**，所以电容也很大。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter13-Memory-25.webp)

#### 计算

**针对有M个Cell的NOR ROM计算word line delay**：

使用**分布式传输线**模型计算得<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

t

</mi>

<mrow>
<mi>

w

</mi>

<mi>

o

</mi>

<mi>

r

</mi>

<mi>

d

</mi>
</mrow>
</msub>

<mo>

=

</mo>

<mn>

0.38

</mn>

<mo>

∗

</mo>

<mo stretchy="false">

(

</mo>

<msub>
<mi>

r

</mi>

<mrow>
<mi>

w

</mi>

<mi>

o

</mi>

<mi>

r

</mi>

<mi>

d

</mi>
</mrow>
</msub>

<mi>

M

</mi>

<mo stretchy="false">

)

</mo>

<mo>

∗

</mo>

<mo stretchy="false">

(

</mo>

<msub>
<mi>

c

</mi>

<mrow>
<mi>

w

</mi>

<mi>

o

</mi>

<mi>

r

</mi>

<mi>

d

</mi>
</mrow>
</msub>

<mi>

M

</mi>

<mo stretchy="false">

)

</mo>

<mo>

=

</mo>

<mn>

0.38

</mn>

<mo stretchy="false">

(

</mo>

<msub>
<mi>

r

</mi>

<mrow>
<mi>

w

</mi>

<mi>

o

</mi>

<mi>

r

</mi>

<mi>

d

</mi>
</mrow>
</msub>

<msub>
<mi>

c

</mi>

<mrow>
<mi>

w

</mi>

<mi>

o

</mi>

<mi>

r

</mi>

<mi>

d

</mi>
</mrow>
</msub>

<mo stretchy="false">

)

</mo>

<msup>
<mi>

M

</mi>

<mn>

2

</mn>
</msup>
</mrow>

<annotation encoding="application/x-tex">

t_{word}=0.38*(r_{word}M)*(c_{word}M) = 0.38(r_{word}c_{word})M^2

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.7651em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

t

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
<span className="mord,mathnormal,mtight" style="margin-right:0.0269em;">

w

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

or

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

0.38

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

∗

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mopen">

(

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.0278em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0269em;">

w

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

or

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

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mclose">

)

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

∗

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mopen">

(

</span>

<span className="mord">
<span className="mord,mathnormal">

c

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
<span className="mord,mathnormal,mtight" style="margin-right:0.0269em;">

w

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

or

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

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mclose">

)

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
<span className="strut" style="height:1.0641em;vertical-align:-0.25em;">



</span>

<span className="mord">

0.38

</span>

<span className="mopen">

(

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.0278em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0269em;">

w

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

or

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

<span className="mord">
<span className="mord,mathnormal">

c

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
<span className="mord,mathnormal,mtight" style="margin-right:0.0269em;">

w

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

or

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

<span className="mclose">

)

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8141em;">
<span style="top:-3.063em;margin-right:0.05em;">
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
</span>
</span>
</span>



**针对有M个Cell的NOR ROM计算Bit line delay**：

假设下拉 NMOS 是最小尺寸，上拉 PMOS 是 3 倍最小尺寸，位线电压摆幅只需要变化约 **1.25V，**平均放电电流 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

I

</mi>

<mrow>
<mi>

a

</mi>

<mi>

v

</mi>

<mi>

H

</mi>

<mi>

L

</mi>
</mrow>
</msub>

<mo>

=

</mo>

<mn>

0.36

</mn>

<mi>

m

</mi>

<mi>

A

</mi>
</mrow>

<annotation encoding="application/x-tex">

I_{avHL}=0.36mA

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0785em;">

I

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.0785em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

a

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

v

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0813em;">

H

</span>

<span className="mord,mathnormal,mtight">

L

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

0.36

</span>

<span className="mord,mathnormal">

m

</span>

<span className="mord,mathnormal">

A

</span>
</span>
</span>
</span>

。

位线总电容约为：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

C

</mi>

<mrow>
<mi>

b

</mi>

<mi>

i

</mi>

<mi>

t

</mi>
</mrow>
</msub>

<mo>

=

</mo>

<mi>

M

</mi>

<mo>

∗

</mo>

<mo stretchy="false">

(

</mo>

<msub>
<mi>

c

</mi>

<mrow>
<mi>

w

</mi>

<mi>

i

</mi>

<mi>

r

</mi>

<mi>

e

</mi>
</mrow>
</msub>

<mo>

+

</mo>

<msub>
<mi>

c

</mi>

<mrow>
<mi>

d

</mi>

<mi>

r

</mi>

<mi>

a

</mi>

<mi>

i

</mi>

<mi>

n

</mi>
</mrow>
</msub>

<mo stretchy="false">

)

</mo>

<mo>

=

</mo>

<mn>

512

</mn>

<mo>

∗

</mo>

<mo stretchy="false">

(

</mo>

<mn>

2.6

</mn>

<mo>

+

</mo>

<mn>

0.8

</mn>

<mo stretchy="false">

)

</mo>

<mo>

≈

</mo>

<mn>

1.7

</mn>

<mi>

p

</mi>

<mi>

F

</mi>
</mrow>

<annotation encoding="application/x-tex">

C_{bit}=M*(c_{wire}+c_{drain})=512*(2.6+0.8) \approx 1.7pF

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

bi

</span>

<span className="mord,mathnormal,mtight">

t

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

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

∗

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mopen">

(

</span>

<span className="mord">
<span className="mord,mathnormal">

c

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0269em;">

w

</span>

<span className="mord,mathnormal,mtight">

i

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal,mtight">

e

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
<span className="mord,mathnormal">

c

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

d

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal,mtight">

ain

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

<span className="mclose">

)

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

512

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

∗

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mopen">

(

</span>

<span className="mord">

2.6

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

0.8

</span>

<span className="mclose">

)

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
<span className="strut" style="height:0.8778em;vertical-align:-0.1944em;">



</span>

<span className="mord">

1.7

</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

pF

</span>
</span>
</span>
</span>



位线延迟近似为：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

t

</mi>

<mo>

=

</mo>

<mfrac>
<mrow>
<msub>
<mi>

C

</mi>

<mrow>
<mi>

b

</mi>

<mi>

i

</mi>

<mi>

t

</mi>
</mrow>
</msub>

<mi mathvariant="normal">

Δ

</mi>

<mi>

V

</mi>
</mrow>

<mi>

I

</mi>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

t = \frac{C_{bit}\Delta V}{I}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6151em;">



</span>

<span className="mord,mathnormal">

t

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
<span className="strut" style="height:1.2392em;vertical-align:-0.345em;">



</span>

<span className="mord">
<span className="mopen,nulldelimiter">



</span>

<span className="mfrac">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.8942em;">
<span style="top:-2.655em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0785em;">

I

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

<span style="top:-3.4159em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0715em;">

C

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3448em;">
<span style="top:-2.3488em;margin-left:-0.0715em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

bi

</span>

<span className="mord,mathnormal,mtight">

t

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
<span className="vlist" style="height:0.1512em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>

<span className="mord,mtight">

Δ

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.2222em;">

V

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
<span className="vlist" style="height:0.345em;">
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



代入后：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

t

</mi>

<mo>

=

</mo>

<mfrac>
<mrow>
<mn>

1.7

</mn>

<mi>

p

</mi>

<mi>

F

</mi>

<mo>

×

</mo>

<mn>

1.25

</mn>

<mi>

V

</mi>
</mrow>

<mrow>
<mn>

0.36

</mn>

<mi>

m

</mi>

<mi>

A

</mi>
</mrow>
</mfrac>

<mo>

≈

</mo>

<mn>

5.9

</mn>

<mi>

n

</mi>

<mi>

s

</mi>
</mrow>

<annotation encoding="application/x-tex">

t = \frac{1.7pF \times 1.25V}{0.36mA} \approx 5.9ns

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6151em;">



</span>

<span className="mord,mathnormal">

t

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
<span className="mord">

0.36

</span>

<span className="mord,mathnormal">

m

</span>

<span className="mord,mathnormal">

A

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

1.7

</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

pF

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

×

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mord">

1.25

</span>

<span className="mord,mathnormal" style="margin-right:0.2222em;">

V

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

≈

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.6444em;">



</span>

<span className="mord">

5.9

</span>

<span className="mord,mathnormal">

n

</span>

<span className="mord,mathnormal">

s

</span>
</span>
</span>
</span>
</span>

根据上拉下拉MOS管的假设，说明位线高到低、低到高的延迟近似相等，所以：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

t

</mi>

<mrow>
<mi>

H

</mi>

<mi>

L

</mi>
</mrow>
</msub>

<mo>

=

</mo>

<msub>
<mi>

t

</mi>

<mrow>
<mi>

L

</mi>

<mi>

H

</mi>
</mrow>
</msub>

<mo>

=

</mo>

<mn>

5.9

</mn>

<mi>

n

</mi>

<mi>

s

</mi>
</mrow>

<annotation encoding="application/x-tex">

t_{HL}=t_{LH}=5.9ns

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.7651em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

t

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0813em;">

H

</span>

<span className="mord,mathnormal,mtight">

L

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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.7651em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

t

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

L

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0813em;">

H

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

5.9

</span>

<span className="mord,mathnormal">

n

</span>

<span className="mord,mathnormal">

s

</span>
</span>
</span>
</span>



![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter13-Memory-26.webp)

#### 减小字线延迟的方法

1. 从两端同时驱动字线。左右两端同时驱动，最远点由最右边变成中间位置，相当于信号传播距离减半。
2. 使用金属旁路。可以避免信号沿着高电阻的多晶硅长距离传播。
3. 使用硅化物。可以显著降低多晶硅的电阻。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter13-Memory-27.webp)

### PROM

Programmable ROM，可编程只读存储器。

**特点**：芯片制造时，每个位置都先放好晶体管；用户编程时，通过“烧断熔丝 fuse”的方式，去掉不需要的连接； 烧断后不可恢复，所以 **PROM 通常只能编程一次**。

### EPROM

Erasable Programmable ROMs，可擦除编程只读存储器。

**特点**：不靠烧断熔丝，而是使用 **floating gate 浮栅晶体管**来关闭不想要的管子，编程后可用紫外线擦除。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter13-Memory-28.webp)

#### FAMOS | 浮栅晶体管

全称：Floating-gate Avalanche-injection Metal-Oxide-Semiconductor transistor，浮栅雪崩注入型 MOS 晶体管

##### 工作原理

浮栅中是否存有电子，会改变晶体管的阈值电压。

- **浮栅没有电子**：阈值电压较低，控制栅加电压后容易导通。
- **浮栅有电子**：电子产生负电荷，会抵消控制栅作用，使阈值电压升高，晶体管更难导通。

##### 非易失性

因为浮栅被绝缘氧化层包围，电荷掉不出去，所以即使断电，电荷仍然保留，数据也不会丢失。

##### 编程过程

1. **雪崩注入**。在漏极和栅极加高电压，源极接地，在漏端附近形成很强的电场，电子获得很高能量，被“打入”浮栅中。
2. 外部施加电压去掉，浮栅中仍然保留负电荷，这就是它能**断电保存数据**的原因。
3. 由于浮栅里有**负电荷**，会抵消控制栅的正电压作用，使沟道更难形成。晶体管的**阈值电压** <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

V

</mi>

<mi>

T

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

V_T

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.2222em;">

V

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.1389em;">

T

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

 **升高**。

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 71.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter13-Memory-29.webp" />
      </p>
    </td>
    
    
      <td style="width: 28.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter13-Memory-30.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

#### Flash EEPROM 结构

EEPROM, Electrically Erasable Programmable ROM

与前面EPROM使用的浮栅晶体管相比，它实现了**电可擦除**功能。

利用**薄隧穿氧化层**，让电子可以电注入、电擦除，因此可以重复写入和擦除。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter13-Memory-31.webp)

### Flash Memory

这是EEPROM的一种，具有非易失性。

#### NOR Flash Memory中擦除操作

给**源极加高电压**（如图12V），控制**栅接低电压**（如图0V），在薄氧化层上形成强电场，把浮栅中的电子通过**隧穿**方式拉到**源极**，从而降低阈值电压。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter13-Memory-32.webp)

#### NOR Flash Memory中写操作

选中某个 cell 后，给**栅极（字线）加高压**、**漏极（位线）加中高压**，使源漏沟道中的热电子注入浮栅；浮栅存入电子后阈值电压升高，从而完成数据写入。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter13-Memory-33.webp)

#### NOR Flash Memory中读操作

给选中 WL 加 5 V，给选中 BL 加小电压 1 V，然后检测位线电流，此时的电压比写入和擦除时小很多

- 有电流：晶体管导通，说明阈值电压低；
- 无电流：晶体管关断，说明阈值电压高。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter13-Memory-34.webp)

#### 对比NAND 和 NOR Flash的电路结构和特点

##### **NAND Flash**

多个存储单元像<mark>

“串联”一样接在一起

</mark>

。读某一个单元时，其他单元也要配合导通，才能形成电流通路。

**特点**：写入和<mark>

擦除速度更快

</mark>

；<mark>

存储密度更高

</mark>

<mark>

（串联版图省）

</mark>

；单位 bit 成本更低；容量更容易做大。

##### NOR Flash

<mark>

每个存储单元基本都直接连到 bit line

</mark>

。读某个单元时，可以比较直接地读取该单元状态。

特点：<mark>

随机读取速度快

</mark>

；可以像 ROM 一样直接读取某个地址；适合直接执行程序代码。但缺点是密度较低，单位 bit 成本较高，容量通常不如 NAND 大。

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 41.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter13-Memory-35.webp" />
      </p>
    </td>
    
    
      <td style="width: 58.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter13-Memory-36.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

#### NOR Flash 的典型用途

NOR Flash 适合替代程序 ROM，用来<mark>

存放程序代码

</mark>

。

NOR Flash 有完整的地址总线和数据总线，支持随机访问，适合代码直接执行，但是连续大容量顺序读写效率不如 NAND Flash，因此不适合做大文件存储。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter13-Memory-37.webp)

#### NAND Flash 的典型用途

NAND Flash 更适合替代磁盘，用来做<mark>

大容量数据存储

</mark>

。

- NAND Flash 通常不是按单个地址随机读写，而是按 <mark>

**page（页）**

</mark>

 访问。
- NAND Flash 的连续读写速度较快，适合大量数据顺序存取。
- NAND Flash 的存储单元串联连接，结构更紧凑，所以单位面积能放更多 bit，因此容量更大，单位 bit 成本更低。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter13-Memory-38.webp)

NAND Flash <mark>

**写入/编程时按 page 页进行**

</mark>

**，**NAND Flash <mark>

**擦除时按 block 块**

</mark>

进行，见下图。

**图中例子解释：**每页 4096 bit，也就是 512 Byte，16 页组成一个块，一整块就是16*512Byte，即8KB。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter13-Memory-39.webp)

#### SLC vs MLC

SLC：一个存储单元存 1 bit。一个浮栅晶体管只需要区分 <mark>

**两个阈值电压状态**

</mark>

，判断简单、可靠性高。

MLC：一个存储单元存多个 bit。MLC 通过把浮栅中的电荷量分成**多个等级**，让同一个晶体管表现出**多个不同的阈值电压**，从而存储更多信息。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter13-Memory-40.webp)

#### Flash Memory 常见错误来源

> 了解

1. **Program disturb / Write disturb（写干扰）**

在写入某些存储单元时，虽然只想改变被选中的 cell，但相邻或同一阵列中未被选中的 cell 也会受到较高电压影响，可能产生轻微电荷变化，导致数据出错。

1. **Read disturb（读干扰）**

反复读取某一页时，未被选中的存储单元也会受到读电压压力。次数多了以后，浮栅中的电荷状态可能被轻微改变，造成误读。

1. **Data retention（数据保持问题）**

Flash 断电后靠浮栅中的电荷保存数据，但电荷会随着时间慢慢泄漏。时间太久或温度较高时，数据可能丢失。

1. **Endurance（耐久性）**

Flash 每次写入/擦除都会损伤氧化层。擦写次数太多后，单元可靠性下降，最终不能正常存储数据。

1. **Soft errors（软错误）**

环境因素也可能导致数据出错，例如宇宙射线、α 粒子等高能粒子影响存储电荷。

1. **Bad blocks（坏块）**

Flash 中允许存在坏块：

- **初始坏块**：制造时由于良率不完美产生，SLC 可有约 2% 坏块，MLC 可有约 5% 坏块。
- **累积坏块**：使用过程中多次写入/擦除后逐渐产生。
- 因此需要 **坏块管理**，把坏块记录下来，避免继续使用。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter13-Memory-41.webp)

##### **Flash 的耐久性（Endurance）问题**

> 了解

Flash 每次 **Program/Erase（写入/擦除）** 时，都要用较高电压让电子穿过氧化层。反复操作后，会有一些电荷被困在绝缘介质中，导致存储单元的**电学特性**发生永久变化。

1. **阈值电压会偏移**
原本表示 0 或 1 的电压范围发生变化，读数据时更容易判断错误。
2. **擦除也无法完全恢复**
因为部分损伤是永久性的，不是简单擦除就能修复。
3. **擦写次数有限**
所以 Flash 不能无限次写入和擦除。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter13-Memory-42.webp)

图中给的典型寿命：

**SLC**：最多大约 **100,000 次** Program/Erase cycles

**MLC**：通常低于 **10,000 次**，有些 MLC 甚至只有约 **1,500 次**

#### Wear Leveling | 磨损均衡 / 损耗均衡

与其反复擦写同一个 block，不如把擦写次数分散到多个 block 上，这就是磨损均衡，这个过程由 **Flash 控制器**完成。

对于 **SLC** 器件来说，磨损均衡是一个有益的增强功能，因为 SLC 的 block 通常可以支持最多 **100,000 次 Program/Erase cycles**。

对于 **MLC** 器件来说，磨损均衡是非常必要的，因为 MLC 的 block 通常只能支持少于 **10,000 次擦写循环**。

#### ECC for Flash

这部分记得当时上课就没怎么细讲，感觉不会考吧（doge）

### 使用 ROM 实现逻辑运算

ROM 可以看成一个 **查找表 Lookup Table**。如果一个逻辑电路有n输入，k输出，那么所有输入组合一共有<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msup>
<mn>

2

</mn>

<mi>

n

</mi>
</msup>
</mrow>

<annotation encoding="application/x-tex">

2^n

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6644em;">



</span>

<span className="mord">
<span className="mord">

2

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.6644em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

n

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

种情况，所以 ROM 需要存<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msup>
<mn>

2

</mn>

<mi>

n

</mi>
</msup>

<mi>

k

</mi>
</mrow>

<annotation encoding="application/x-tex">

2^nk

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord">
<span className="mord">

2

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.6644em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

n

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

<span className="mord,mathnormal" style="margin-right:0.0315em;">

k

</span>
</span>
</span>
</span>

bits。

用 ROM 实现**有限状态机 FSM。**有限状态机不仅有输入和输出，还有 状态 state。此时ROM的输入需要两部分——外部输入和当前状态，即 n+s；输出也有两部分——当前输出和下一步状态，即k+s。所以ROM 需要存<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msup>
<mn>

2

</mn>

<mrow>
<mi>

n

</mi>

<mo>

+

</mo>

<mi>

s

</mi>
</mrow>
</msup>

<mo stretchy="false">

(

</mo>

<mi>

k

</mi>

<mo>

+

</mo>

<mi>

s

</mi>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

2^{n+s}(k+s)

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.0213em;vertical-align:-0.25em;">



</span>

<span className="mord">
<span className="mord">

2

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.7713em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

n

</span>

<span className="mbin,mtight">

+

</span>

<span className="mord,mathnormal,mtight">

s

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

<span className="mopen">

(

</span>

<span className="mord,mathnormal" style="margin-right:0.0315em;">

k

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

<span className="mord,mathnormal">

s

</span>

<span className="mclose">

)

</span>
</span>
</span>
</span>

bits。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter13-Memory-43.webp)

## Serial Access Memory | 串行访问存储器

串行访问存储器不使用地址，主要分为以下几类：

- **Shift Registers**：移位寄存器

  - **Serial In Parallel Out, SIPO**：串入并出
  - **Parallel In Serial Out, PISO**：并入串出
- **Tapped Delay Lines**：抽头延迟线
- **Queues, FIFO, LIFO**：队列，包括先进先出 FIFO、后进先出 LIFO

### Shift Registers

每来一个时钟上升沿，数据就向右移动一级。

#### 主要作用

1. **存储数据**
每一级寄存器都能暂存一拍的数据。
2. **延迟数据**
如果有 4 级寄存器，那么输入数据大约会延迟 4 个时钟周期后从输出端出来。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter13-Memory-44.webp)

设计这种级联寄存器时，要特别注意保持时间 **hold time**。

**原因**是所有寄存器共用同一个时钟，如果前一级寄存器输出变化太快，而后一级寄存器还没完成保持时间要求，后一级可能错误地捕获到“新的数据”，导致时序错误。

#### Denser Shift Registers | 高密度移位寄存器

当移位寄存器很长时，不要真的用很多触发器一级一级串起来，而是用 SRAM 来实现更高密度的移位寄存器。

使用RAM存储数据时，不用RAM的内部数据，而是**只移动读****/写指针**

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter13-Memory-45.webp)

若要实现 N 级延迟的移位寄存器：

1. **Din 写入 SRAM 的某个地址**
2. **Dout 从另一个地址读出旧数据**
3. 每个时钟周期，`writeaddr` 和 `readaddr` 都加 1
4. 地址到末尾后再回到开头，形成循环

### Tapped Delay Line | 可抽头延迟线

本质上是一个<mark>

**可以选择延迟多少个时钟周期的移位寄存器**

</mark>

<mark>

**x**

</mark>



普通移位寄存器延迟固定，而 **tapped delay line** 可以通过控制信号选择延迟级数，例如下图可以选择 **0 到 63 个周期的延迟**。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter13-Memory-46.webp)

`SR32` 表示 32 级移位寄存器，可以提供 32 个周期延迟 ；`SR16` 提供 16 个周期延迟，依次类推。

每一级旁边都有一个 **MUX 多路选择器，**`delay5 ~ delay0` 是控制信号，用来决定这一段延迟是否加入。

### Serial In Parallel Out | 串入并出

把一位一位输入的串行数据，转换成多位同时输出的并行数据。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter13-Memory-47.webp)

### Parallel In Serial Out | 并入串出

先一次性并行装入 N 位数据，然后每个时钟周期串行输出 1 位。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter13-Memory-48.webp)

### Queues | 队列存储器

<mark>

队列允许数据的

</mark>

<mark>

**写入速度**

</mark>

<mark>

和

</mark>

<mark>

**读出速度**

</mark>

<mark>

不一样，比如每 1 个周期写一个数据，每 3 个周期读一个数据。队列可以先把来不及读的数据暂时存起来，起到

</mark>

<mark>

**缓冲区 buffer**

</mark>

<mark>

的作用。

</mark>



队列可以自行判断内部数据读满还是全空。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter13-Memory-49.webp)

#### <mark>FIFO 先进先出</mark>

将读指针和写指针都初始化到第一个元素位置，此时队列为空。每写入一次数据，写指针加 1；如果写指针快要追上读指针，说明队列快满或已满；每读出一次数据，读指针加 1。

#### <mark>LIFO 后进先出</mark>

<mark>

LIFO 也叫

</mark>

 <mark>

**stack，栈**

</mark>

<mark>

。

</mark>



它通常只需要一个 **stack pointer，栈指针**。因为读和写都发生在栈顶：

- 写入数据：栈指针向上移动
- 读出数据：从栈顶取出，栈指针向下移动

<alert type="tip">

FIFO：像排队，先来先走

LIFO：像叠盘子，后来先走

</alert>

## CAM

全称：<mark>

Content Addressable Memory

</mark>

，<mark>

内容寻址存储器

</mark>



### CAM 和普通 SRAM 的区别

普通 SRAM 是按照**地址**找数据，而 CAM 是：给一个数据 key，让存储器自己去找哪些位置存了这个 key。也就是**按内容找地址/位置**。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter13-Memory-50.webp)

左图中的 CAM 既可以像普通存储器一样读写，但它还有一个**额外功能**：输入一个 `key`，CAM 内部所有存储单元同时和 key 比较，如果某一行内容等于 key，这一行就产生 `match`。

> 这个比较是所有行并行比较，所以速度比较快。

右图是 CAM 在 **TLB（Translation Lookaside Buffer，地址转换后备缓冲）** 中的典型应用。

TLB 的作用是：

> 把虚拟地址 Virtual Address 快速转换成物理地址 Physical Address。

这里 CAM 负责：**判断虚拟地址有没有命中某个 TLB 表项。**

SRAM 负责：**存放对应的物理地址或页表信息。**

### 匹配原理

1. **wordline 保持低电平**

`wordline low` 表示不进行普通 SRAM 读写操作。

1. **预充 matchline**

每一行的 matchline 先被预充到高电平。

1. **把 key 放到 bitline 上**

输入的搜索关键字 `key` 被放到 bitline 上，每个 CAM cell 会把自己存储的 bit 和输入的 key bit 进行比较。

1. **matchline 进行评估**

如果某一行中 **所有 bit 都和 key 相同**，那么这一行的 matchline 保持高电平，表示匹配。

如果某一行中 **只要有一个 bit 不同**，该行的 matchline 就会被拉低，表示不匹配。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter13-Memory-51.webp)

#### Miss line 的作用

所有 matchline 会经过一个类似 **伪 nMOS NOR 门** 的结构，如果所有的 matchline=0，即每一行都不匹配，输出miss=1，否则miss=0。
