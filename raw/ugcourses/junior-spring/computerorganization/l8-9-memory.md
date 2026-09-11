# L8-9：存储器层次结构

> DRAM 结构与发展历史、存储器阵列与行/列访问，以及存储器层次相关笔记

## **Introduction to DRAM | 存储器/DRAM简介**

我们说，对于计算机的结构而言，存储器的用途是——存储程序和数据，那么这里面使用的存储器是什么类型的呢——

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-01.webp)

### Memory Array ｜ 存储器阵列

这个就是以恶搞简单的存储器分类，和《数字集成电路设计》这门课讲的差不多，简单看一下

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-02.webp)

### 存储器历史

这部分其实没什么要记住的，都是很了解性的知识

#### Early ROM Technologies ｜ 早期只读存储器技术

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-03.webp)

了解，应该不用记

#### Early R/W Memory ｜ 早期读/写主存技术

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-04.webp)

#### Core Memory ｜ 核心存储器

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-05.webp)

依旧了解，这个总不至于考的吧

#### Semiconductor memory ｜ 半导体存储器

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-06.webp)

#### 1T-1C | 单晶体管动态RAM <span>Dennard, IBM</span>

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-07.webp)

采用"1T-1C"的这种DRAM结构来进行存储，这个数集也有讲过

#### Modern DRAM Structure ｜ 现代DRAM的结构

到了现在，DRAM的结构又发生了变化——

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-08.webp)

### DRAM架构

#### DRAM Cell 结构

##### 1T-1C | 单晶体管动态RAM <span>Dennard, IBM</span>

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-09.webp)

采用"1T-1C"的这种DRAM结构来进行存储，这个数集也有讲过

#### DRAM 内部二维阵列

<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msup>
<mn>

2

</mn>

<mi>

N

</mi>
</msup>

<mtext>

rows

</mtext>

<mo>

×

</mo>

<msup>
<mn>

2

</mn>

<mi>

M

</mi>
</msup>

<mtext>

columns

</mtext>
</mrow>

<annotation encoding="application/x-tex">

2^N\text{ rows} \times 2^M\text{ columns}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9247em;vertical-align:-0.0833em;">



</span>

<span className="mord">
<span className="mord">

2

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8413em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.109em;">

N

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

<span className="mord,text">
<span className="mord">

rows

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
<span className="strut" style="height:0.8413em;">



</span>

<span className="mord">
<span className="mord">

2

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8413em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.109em;">

M

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

<span className="mord,text">
<span className="mord">

columns

</span>
</span>
</span>
</span>
</span>

，每个交叉点是一个 memory cell，存 1 bit。

打开某一行时，row decoder 会让对应的 word line 有效。于是这一行上的所有 cell 都连接到对应 bit line 上。

这一整行的数据会被 sense amplifier 检测并锁存。sense amplifier 其实就形成了一个 **row buffer**，也就是“当前已经打开的行”。

<table>
<thead>
  <tr>
    <th>
      名称
    </th>
    
    <th>
      图中方向
    </th>
    
    <th>
      作用
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      word line
    </td>
    
    <td>
      横向红线
    </td>
    
    <td>
      选择某一整行
    </td>
  </tr>
  
  <tr>
    <td>
      bit line
    </td>
    
    <td>
      纵向绿线
    </td>
    
    <td>
      连接一列上的存储单元，把电荷变化送到 sense amplifier
    </td>
  </tr>
</tbody>
</table>

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-10.webp)

- Logical Banks

  - bank 可以理解成：**DRAM 芯片内部相对独立的小阵列，每个 bank 有自己的行缓冲区。**
  - 多个 bank 的意义是提高并行性。比如一个 bank 正在预充电，另一个 bank 可以准备访问；或者不同请求分散到不同 bank，减少等待。

##### DRAM 操作

DRAM 访问是三步：**Row Access → Column Access → Precharge**

###### Row Access：行访问 / RAS

1. Step1： 解码 row address；
2. Step2：打开对应的wordline
3. Step3：该行所有 cell 连接到 bit lines；
4. Step4：cell 中的电荷和 bit line 共享，造成很小的电压变化；
5. Step5：sense amplifier 检测这个微小变化；
6. Step6：sense amplifier 把结果放大到完整的 0 或 1，并锁存整行；
7. Step7：同时把数据重新写回 cell，恢复电荷。

###### Column Access：列访问 / CAS

当一整行已经打开后，column address 决定从 row buffer 中选择哪几列。

- 读操作：从 sense amplifier 选出对应列，把数据送到芯片引脚。
- 写操作：修改 sense amplifier 中对应列的值，再把这个值写回 DRAM cell。

<mark>

**这就是为什么对同一行连续访问会比较快**

</mark>

<mark>

**，后续只做列选择，不再重复行激活、感测和恢复。**

</mark>



#### DRAM 芯片与 DIMM

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-11.webp)

<table>
<thead>
  <tr>
    <th>
      信号
    </th>
    
    <th>
      作用
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      时钟和控制信号
    </td>
    
    <td>
      告诉 DRAM 当前执行什么操作，比如激活行、读、写、预充电
    </td>
  </tr>
  
  <tr>
    <td>
      地址线
    </td>
    
    <td>
      传输 row address 和 column address
    </td>
  </tr>
  
  <tr>
    <td>
      数据总线
    </td>
    
    <td>
      读写真正的数据，比如 x4、x8、x16、x32 位
    </td>
  </tr>
</tbody>
</table>

- **DIMM = Dual Inline Memory Module**，也就是我们常说的内存条。

  - DIMM 的容量来自多个 DRAM chip，DIMM 的数据宽度来自多个芯片的数据引脚并联
  - 多个芯片共享地址/控制线时，负载电容很大，所以有些内存条会加缓冲器或寄存器，把信号更稳定地驱动到所有芯片。

### SX-Aurora High-Bandwidth Memory (HBM)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-12.webp)

传统 DDR 内存总线可能是 64 bit 级别，而 HBM 可以做到每个通道上千 bit 级别

- **DRAM dies 堆叠**
- **硅中介层 silicon interposer（TSV等）**
- HBM 的优势是：

  - 数据总线非常宽；
  - 单 pin 频率不一定特别高；
  - 总带宽极高；
  - 单位 bit 传输能耗较低。

## **Memory Hierarchy ｜ 存储器层级结构**

### Memory Bottleneck ｜ CPU 内存瓶颈

高速计算机的性能通常受到**内存带宽(bandwidth)**和**延迟(latency)**的限制

1. **Latency 延迟**
  1. 指单次内存访问需要的时间。
  2. 主存访问时间通常远大于 CPU 周期时间，所以一次 load/store 可能让 CPU 等很多周期。
2. **Bandwidth 带宽**
  1. 指单位时间内内存能完成多少访问或传输多少数据。
  2. 即使单次访问不算特别慢，如果每周期请求太多，内存也可能处理不过来。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-13.webp)

对于 RISC-V 这类 load-store 架构：

- 每条指令都要取指，因此至少有 1 次 instruction memory access；
- 若比例为 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

m

</mi>
</mrow>

<annotation encoding="application/x-tex">

m

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.4306em;">



</span>

<span className="mord,mathnormal">

m

</span>
</span>
</span>
</span>

 的指令是 load/store，还会额外访问 data memory；
- 所以平均每条指令需要 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mn>

1

</mn>

<mo>

+

</mo>

<mi>

m

</mi>
</mrow>

<annotation encoding="application/x-tex">

1+m

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.7278em;vertical-align:-0.0833em;">



</span>

<span className="mord">

1

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
<span className="strut" style="height:0.4306em;">



</span>

<span className="mord,mathnormal">

m

</span>
</span>
</span>
</span>

 次内存访问。

若希望处理器达到 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
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

=

</mo>

<mn>

1

</mn>
</mrow>

<annotation encoding="application/x-tex">

CPI=1

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

<span className="mord,mathnormal" style="margin-right:0.0785em;">

I

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

1

</span>
</span>
</span>
</span>

，即每周期完成 1 条指令，则内存系统平均也要支持 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mn>

1

</mn>

<mo>

+

</mo>

<mi>

m

</mi>
</mrow>

<annotation encoding="application/x-tex">

1+m

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.7278em;vertical-align:-0.0833em;">



</span>

<span className="mord">

1

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
<span className="strut" style="height:0.4306em;">



</span>

<span className="mord,mathnormal">

m

</span>
</span>
</span>
</span>

 次访问/周期。若内存带宽不足或延迟过高，CPU 就会停等内存，整体性能下降。

### Memory Hierarchy  ｜ 内存层次结构

CPU 访问内存受到 **latency** 和 **bandwidth** 限制。<mark>

大存储器虽然容量大、成本低，但

</mark>

<mark>

**物理尺寸大**

</mark>

<mark>

，信号传播距离远，字线 / 位线负载大，所以访问延迟高。

</mark>



为了兼顾“快”和“大”，系统不能只使用一种存储器。SRAM 很快但面积大、价格高，适合做 cache；DRAM 容量大、成本低，但访问慢，适合做主存；磁盘 / Flash 更大更便宜，但速度更慢。

因此计算机采用 **内存层次结构**：

> **靠近 CPU 的存储器小而快，远离 CPU 的存储器大而慢。**

Cache 就像图书馆里的桌子，把近期可能会用到的书先放在桌上，避免每次都跑到巨大书库里找。这个设计依赖程序的局部性：刚访问过的数据可能很快再次访问，附近的数据也可能很快访问。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-14.webp)

##### 典型存储器层次结构

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 57.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-15.webp" />
      </p>
    </td>
    
    
      <td style="width: 42.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-16.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

从靠近 CPU 到远离 CPU，大致是：

```text
Register File 寄存器
→ L1 I-Cache / D-Cache 一级指令/数据缓存
→ L2 Cache 二级缓存
→ L3 Cache 三级缓存
→ Main Memory / DRAM 主存 DRAM
→ Secondary Memory / Disk or Flash 磁盘或 Flash 等二级存储
```

越靠近 CPU，速度越快但容量越小；越远离 CPU，容量越大但速度越慢。

<table>
<thead>
  <tr>
    <th>
      层级
    </th>
    
    <th>
      典型实现
    </th>
    
    <th>
      速度
    </th>
    
    <th>
      容量
    </th>
    
    <th>
      每 bit 成本
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      Register File
    </td>
    
    <td>
      寄存器堆
    </td>
    
    <td>
      最快，约亚周期 / 1 周期内
    </td>
    
    <td>
      几百字节
    </td>
    
    <td>
      最高
    </td>
  </tr>
  
  <tr>
    <td>
      L1 Cache
    </td>
    
    <td>
      SRAM分 I-Cache / D-Cache
    </td>
    
    <td>
      约 1 cycle
    </td>
    
    <td>
      数十 KB
    </td>
    
    <td>
      很高
    </td>
  </tr>
  
  <tr>
    <td>
      L2 / L3 Cache
    </td>
    
    <td>
      SRAM
    </td>
    
    <td>
      约 10 cycles
    </td>
    
    <td>
      MB 级
    </td>
    
    <td>
      较高
    </td>
  </tr>
  
  <tr>
    <td>
      Main Memory
    </td>
    
    <td>
      DRAM
    </td>
    
    <td>
      数百到上千 cycles
    </td>
    
    <td>
      GB 级
    </td>
    
    <td>
      较低
    </td>
  </tr>
  
  <tr>
    <td>
      Secondary Memory
    </td>
    
    <td>
      SSD / Disk / Flash
    </td>
    
    <td>
      约百万 cycles
    </td>
    
    <td>
      TB 级
    </td>
    
    <td>
      最低
    </td>
  </tr>
</tbody>
</table>

#### Management of Memory Hierarchy ｜ 内存层次管理

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-17.webp)

不同层级的存储器有不同的管理方式。

1. 小而快的存储器：Registers
  1. 寄存器容量小、速度快，通常由指令直接指定。例如：```text
add x3, x1, x2
```


  1. 指令直接说明读 <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mi>
  
  x
  
  </mi>
  
  <mn>
  
  1
  
  </mn>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  x1
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:0.6444em;">
  
  
  
  </span>
  
  <span className="mord,mathnormal">
  
  x
  
  </span>
  
  <span className="mord">
  
  1
  
  </span>
  </span>
  </span>
  </span>
  
  、读 <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mi>
  
  x
  
  </mi>
  
  <mn>
  
  2
  
  </mn>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  x2
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:0.6444em;">
  
  
  
  </span>
  
  <span className="mord,mathnormal">
  
  x
  
  </span>
  
  <span className="mord">
  
  2
  
  </span>
  </span>
  </span>
  </span>
  
  、写 <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mi>
  
  x
  
  </mi>
  
  <mn>
  
  3
  
  </mn>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  x3
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:0.6444em;">
  
  
  
  </span>
  
  <span className="mord,mathnormal">
  
  x
  
  </span>
  
  <span className="mord">
  
  3
  
  </span>
  </span>
  </span>
  </span>
  
  。因此寄存器对程序是显式可见的，硬件中通常实现为 register file。
  2. 编译器可能进行寄存器分配和栈管理；乱序处理器硬件还可能进行 register renaming，把 ISA 中可见的架构寄存器映射到更多物理寄存器上。
2. 较大较慢的存储器：Main Memory
  1. 主存容量大但速度慢，通常通过地址访问。地址一般由寄存器中的值计算得到，例如：`lw x5, 16(x6)`
    1. 实际访问地址为：<span className="katex">
    <span className="katex-mathml">
    <math xmlns="http://www.w3.org/1998/Math/MathML">
    <semantics>
    <mrow>
    <mi>
    
    A
    
    </mi>
    
    <mi>
    
    d
    
    </mi>
    
    <mi>
    
    d
    
    </mi>
    
    <mi>
    
    r
    
    </mi>
    
    <mi>
    
    e
    
    </mi>
    
    <mi>
    
    s
    
    </mi>
    
    <mi>
    
    s
    
    </mi>
    
    <mo>
    
    =
    
    </mo>
    
    <mi>
    
    R
    
    </mi>
    
    <mi>
    
    e
    
    </mi>
    
    <mi>
    
    g
    
    </mi>
    
    <mo stretchy="false">
    
    [
    
    </mo>
    
    <mi>
    
    x
    
    </mi>
    
    <mn>
    
    6
    
    </mn>
    
    <mo stretchy="false">
    
    ]
    
    </mo>
    
    <mo>
    
    +
    
    </mo>
    
    <mn>
    
    16
    
    </mn>
    </mrow>
    
    <annotation encoding="application/x-tex">
    
    Address = Reg[x6] + 16
    
    </annotation>
    </semantics>
    </math>
    </span>
    
    <span className="katex-html" ariaHidden="true">
    <span className="base">
    <span className="strut" style="height:0.6944em;">
    
    
    
    </span>
    
    <span className="mord,mathnormal">
    
    A
    
    </span>
    
    <span className="mord,mathnormal">
    
    dd
    
    </span>
    
    <span className="mord,mathnormal" style="margin-right:0.0278em;">
    
    r
    
    </span>
    
    <span className="mord,mathnormal">
    
    ess
    
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
    <span className="strut" style="height:1em;vertical-align:-0.25em;">
    
    
    
    </span>
    
    <span className="mord,mathnormal" style="margin-right:0.0077em;">
    
    R
    
    </span>
    
    <span className="mord,mathnormal">
    
    e
    
    </span>
    
    <span className="mord,mathnormal" style="margin-right:0.0359em;">
    
    g
    
    </span>
    
    <span className="mopen">
    
    [
    
    </span>
    
    <span className="mord,mathnormal">
    
    x
    
    </span>
    
    <span className="mord">
    
    6
    
    </span>
    
    <span className="mclose">
    
    ]
    
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
    <span className="strut" style="height:0.6444em;">
    
    
    
    </span>
    
    <span className="mord">
    
    16
    
    </span>
    </span>
    </span>
    </span>
  2. <mark>
  
  Main Memory 通常实现为硬件管理的缓存层次结构(硬件决定在快速内存中保留什么)
  
  </mark>
  
  <mark>
  
  **【虽然说我觉得课件上这句话莫名其妙的，姑且把它理解为：Main Memory 是通过加入一级缓存来实现加快多次访问数据的速度吧】**
  
  </mark>
3. Cache 层次
  1. Cache 通常由硬件管理，对程序员不可见。程序只发出普通 load/store，硬件自动判断数据是否在 Cache 中：<span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mi>
  
  H
  
  </mi>
  
  <mi>
  
  i
  
  </mi>
  
  <mi>
  
  t
  
  </mi>
  
  <mo>
  
  ⇒
  
  </mo>
  
  <mtext>
  
  直接从
  
  </mtext>
  
  <mi>
  
  C
  
  </mi>
  
  <mi>
  
  a
  
  </mi>
  
  <mi>
  
  c
  
  </mi>
  
  <mi>
  
  h
  
  </mi>
  
  <mi>
  
  e
  
  </mi>
  
  <mtext>
  
  返回，低延迟
  
  </mtext>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  Hit \Rightarrow 直接从 Cache 返回，低延迟
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:0.6833em;">
  
  
  
  </span>
  
  <span className="mord,mathnormal" style="margin-right:0.0813em;">
  
  H
  
  </span>
  
  <span className="mord,mathnormal">
  
  i
  
  </span>
  
  <span className="mord,mathnormal">
  
  t
  
  </span>
  
  <span className="mspace" style="margin-right:0.2778em;">
  
  
  
  </span>
  
  <span className="mrel">
  
  ⇒
  
  </span>
  
  <span className="mspace" style="margin-right:0.2778em;">
  
  
  
  </span>
  </span>
  
  <span className="base">
  <span className="strut" style="height:0.6944em;">
  
  
  
  </span>
  
  <span className="mord,cjk_fallback">
  
  直接从
  
  </span>
  
  <span className="mord,mathnormal" style="margin-right:0.0715em;">
  
  C
  
  </span>
  
  <span className="mord,mathnormal">
  
  a
  
  </span>
  
  <span className="mord,mathnormal">
  
  c
  
  </span>
  
  <span className="mord,mathnormal">
  
  h
  
  </span>
  
  <span className="mord,mathnormal">
  
  e
  
  </span>
  
  <span className="mord,cjk_fallback">
  
  返回，低延迟
  
  </span>
  </span>
  </span>
  </span>
  
  ； <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mi>
  
  M
  
  </mi>
  
  <mi>
  
  i
  
  </mi>
  
  <mi>
  
  s
  
  </mi>
  
  <mi>
  
  s
  
  </mi>
  
  <mo>
  
  ⇒
  
  </mo>
  
  <mtext>
  
  从下一级存储器取回
  
  </mtext>
  
  <mi>
  
  b
  
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
  
  ，高延迟
  
  </mtext>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  Miss \Rightarrow 从下一级存储器取回 block，高延迟
  
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
  
  <span className="mord,mathnormal">
  
  i
  
  </span>
  
  <span className="mord,mathnormal">
  
  ss
  
  </span>
  
  <span className="mspace" style="margin-right:0.2778em;">
  
  
  
  </span>
  
  <span className="mrel">
  
  ⇒
  
  </span>
  
  <span className="mspace" style="margin-right:0.2778em;">
  
  
  
  </span>
  </span>
  
  <span className="base">
  <span className="strut" style="height:0.6944em;">
  
  
  
  </span>
  
  <span className="mord,cjk_fallback">
  
  从下一级存储器取回
  
  </span>
  
  <span className="mord,mathnormal">
  
  b
  
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
  
  <span className="mord,cjk_fallback">
  
  ，高延迟
  
  </span>
  </span>
  </span>
  </span>
  2. 软件可以提供提示，例如 prefetch 提前取数据，或者 no-cache / non-temporal 避免污染 Cache。

<alert type="tip">

**寄存器由指令显式指定，主存通过寄存器计算地址访问，Cache 则主要由硬件在背后自动管理。**

</alert>

### Locality ｜ 局部性 （重要思想）

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-18.webp)

局部性是 Cache 能工作的根本原因。程序访问内存通常不是完全随机的，而是在一段时间内集中访问某些地址区域。

##### Temporal Locality ｜ 时间局部性

1. **定义：**如果一个内存位置刚刚被访问，那么它很可能很快再次被访问。
2. **典型来源：**
  - 循环中反复执行同一段指令；
  - 标量变量反复使用，如 `sum`、`i`；
  - 当前函数栈帧中的局部变量反复访问。
3. **Cache 利用方式：**把最近访问过的数据留在 Cache 中。

##### Spatial Locality ｜ 空间局部性

1. **定义：**如果一个内存位置被访问，那么它附近地址的数据很可能很快也会被访问。
2. **典型来源：**
  - 指令顺序执行；
  - 数组顺序访问；
  - 栈帧中相邻变量访问。
3. **Cache 利用方式：**访问某个地址时，把附近的一整个 block 一起取入 Cache。

### Memory Reference Patterns ｜ 内存访问模式

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 51.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-19.webp" />
      </p>
    </td>
    
    
      <td style="width: 48.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-20.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

程序访存可以分为三类：

1. Instruction fetches： 顺序执行有空间局部性，循环有时间局部性
2. Stack accesses： 当前栈帧反复访问，空间和时间局部性都较好
3. Data accesses：取决于程序结构，数组顺序访问好，随机访问差

### Principle of Locality ｜ 局部性原则

程序在任何时刻通常只访问地址空间的一小部分，并且会重复访问这部分。也就是：**访问集中在“小范围”，并且这个“小范围”会被反复使用。**

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-21.webp)

1. 什么程序结构导致<mark>

**指令访问**

</mark>

中的局部性？
**Temporal locality：**
  - 循环：同一段循环体指令会被反复取指。
  - 反复调用同一个函数 / 子程序。
  - 小型热点代码段反复执行。
  **Spatial locality：**
  - 顺序执行代码：PC 通常按 PC,PC+4,PC+8,… 连续取指。
  - 基本块内部的连续指令。
  - 循环体指令在内存中连续存放。
2. 什么程序结构导致<mark>

**数据访问**

</mark>

中的局部性？
**Temporal locality：**
  - 循环中反复访问同一个变量，例如 `sum`、`i`、`temp`。
  - 反复访问当前函数的局部变量和栈帧。
  - 嵌套循环中反复使用同一块数据，例如矩阵分块中的小块数据。
  **Spatial locality：**
  - 顺序访问数组：`A[0], A[1], A[2], ...`
  - 按内存布局访问二维数组，例如 C 语言中按行访问 `A[i][j]`。
  - 访问结构体中相邻字段。
  - 访问栈上相邻的局部变量。
3. 什么结构会破坏局部性？
  1. 破坏指令访问局部性的结构
  
    - 频繁跳转到很远的代码位置。
    - 大量不可预测分支。
    - 间接跳转、函数指针、虚函数调用。
    - 代码体积太大，超过 I-Cache 容量。
    - 频繁调用很多分散的小函数。
  2. 破坏数据访问局部性的结构
  
    - 随机访问数组。
    - 链表、树、图等指针追踪结构。
    - 大步长访问数组,或者 C 语言二维数组按列访问，例如：

#### Cache 的核心策略

Cache 利用了两种可预测性：

1. **时间局部性：**<mark>

保留最近访问过的数据。

</mark>
2. **空间局部性：**取数据时，不只取当前地址，而是<mark>

取附近的一整个 cache block

</mark>

。

## Basic Structure of Cache ｜ 缓存的基本结构

### Cache Philosophy ｜ Cache 的基本哲学

1. Cache 的核心思想是：**用硬件在 CPU 和主存之间自动保存常用数据，让程序员感觉自己拥有一个又大又快的内存。**
2. Cache 是位于 CPU 和主存之间的小而快的硬件存储器；它对普通程序员通常不可见，硬件自动判断数据是否在 Cache 中，从而给程序员一种“拥有又大又快的内存”的错觉。
3. 高性能程序员会“反向理解”Cache 的组织方式，设计更适合 Cache 的数据结构和访问顺序。

### Cache 的系统位置与 CPU 交互（向计算机添加缓存）

#### 缓存术语

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-22.webp)

##### 缓存基本存储单元 - SRAM

> **不知道要不要学🙄🙄🙄 这钩式ppt怎么乱七八糟啥都有  了解一下应该就行**

###### SRAM基本结构

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-23.webp)

工艺缩放让 SRAM 更小，但也让漏电变大、<span className="katex">
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

O

</mi>

<mi>

N

</mi>
</mrow>
</msub>

<mi mathvariant="normal">

/

</mi>

<msub>
<mi>

I

</mi>

<mrow>
<mi>

O

</mi>

<mi>

F

</mi>

<mi>

F

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

I_{ON}/I_{OFF}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



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
<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

O

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.109em;">

N

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

/

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
<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

O

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.1389em;">

F

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.1389em;">

F

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

 变差；为了省 standby 功耗又要降低 <span className="katex">
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

，这会削弱数据保持能力，所以 SRAM cell 里的 PMOS 上拉负载必须足够强，能够补偿漏电并维持存储节点电压。

- 为什么会削弱数据保持能力？
- 假设左边节点存的是 1：这个 1 是靠 PMOS 上拉管维持在 VDD 附近的，但是由于漏电，可能会有一些漏电路径把这个高电平节点往下拉，所以 PMOS 上拉管必须提供一点电流，把这些漏掉的电荷补回来，让高电平节点继续保持为 1。

###### DRV Data Retention Voltage | 数据保持电压

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-24.webp)

1. 降低 VDD可以减少功耗和漏电，但不能无限降低。因为 VDD 降低后，反相器的 VTC 会变差。
2. 对于右侧这个图，VTC1和VTC2这两条曲线实际上是输入和输出相互交换了位置——**SRAM cell 里面本质是两个反相器互相连（V1-->反相器-->V2 且 V2-->反相器-->V1）——把这两条曲线画在同一张图上**
  1. 现实中会有噪声，比如存 1 的节点被往下拉一点或者存 0 的节点被往上抬一点
  2. 这个“最大可忍受扰动”就可以用蝴蝶曲线里能放下的**最大正方形边长（保守估算）**来表示，如果扰动超过了这个正方形，就可能发生误翻转

###### SRAM 读/写流程

看懂怎么读写就好了，这个数集也有讲过，感觉真不会考这东西吧

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 50.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-25.webp" />
      </p>
    </td>
    
    
      <td style="width: 49.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-26.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

###### SNM Static Noise Margin ｜ SRAM静态噪声裕度

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 49.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-27.webp" />
      </p>
    </td>
    
    
      <td style="width: 50.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-28.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

1. **左图**<mark>

**蓝色蝴蝶曲线**

</mark>

是在**读操作条件**下画出的 SRAM **两个反相器的 VTC**。
  1. **读操作本身会扰动 cell**。保持状态下 WL=0，cell 和位线隔离；读状态下 WL=1，预充位线会干扰内部存储节点。
  2. 因此会说：**读 SNM 通常是最严格的约束。**
2. 右边红蓝曲线也是在画等效 VTC，但这次是在 **写入条件** 下画的
  1. 写入条件下，位线不是两边都预充到 VDD，而是一边被强制拉低，一边被强制拉高。这样外部 write driver 改变了 cell 的等效电路特性。
  2. WNM (Write Noise Magrin)：看 write driver 能不能打破原来的稳定状态，把 cell 推到新状态<table>
<thead>
  <tr>
    <th>
      目标
    </th>
    
    <th>
      希望的晶体管关系
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      读稳定
    </td>
    
    <td>
      access 管不要太强，pull-down 要强
    </td>
  </tr>
  
  <tr>
    <td>
      写容易
    </td>
    
    <td>
      access 管要强，pull-up / cell 锁存不要太顽固
    </td>
  </tr>
</tbody>
</table>

读希望 cell “抗扰动”，写希望 cell “容易被扰动”, 因此说**同时优化读写稳定性是很困难的。**

#### 整体框架

下图左图为不加缓存的形式，右图在处理器和Memory中间插入缓存，CPU 发出的访存请求不会直接去 DRAM，而是先问 Cache。

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 49.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-29.webp" />
      </p>
    </td>
    
    
      <td style="width: 50.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-30.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

1. Cache 数据读写

  1. 写数据也会先经过 Cache，再根据写策略决定是否立即更新主存。
  2. 读数据时，CPU 发出地址->Cache 检查有没有这个数据->如果有：直接返回给 CPU->如果没有：去主存取，把数据放入 Cache，再返回给 CPU
2. **CPU 按字节 / 字访问，Cache 按块组织**

> Processor organized around words and bytes.Memory including cache organized around blocks.

1. CPU 发请求时，通常是按：
  1. byte；
  2. half word；
  3. word；
  来访问的
2. 但是 Cache 和主存之间搬运数据时，通常不是只搬一个字，而是搬一整个 **block**。
  1. 原因是空间局部性：如果 CPU 访问了某个地址，那么附近地址很可能也会被访问，所以一次把附近一整块都取上来。

#### RISC-V 数据通路中加入 I-Cache 和 D-Cache

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-31.webp)

**上图为不加入缓存的****RV32I 流水线数据通路，下图为加入 I-Cache 和 D-Cache的数据通路**

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-32.webp)

> `$` 在业界约定俗成地代表"缓存"（Cache）

1. 为什么要分 I$ 和 D$？
如果只有一个内存，那么同一个周期里可能会出现冲突：
  - IF 阶段要取指令；
  - MEM 阶段的 lw / sw 也要访问数据内存。
  这两个访问会抢同一个存储器端口，形成**结构冒险**。所以经典 RISC 流水线通常把指令存储和数据存储分开，实际系统里就是分成：
  - I$：Instruction Cache，指令缓存；
  - D$：Data Cache，数据缓存。
2. IF 阶段：PC 如何取指？
左边这一段是 IF 阶段：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

P

</mi>

<msub>
<mi>

C

</mi>

<mi>

F

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

PC_F

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.1389em;">

F

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

 → I$ → <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

i

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

<msub>
<mi>

r

</mi>

<mi>

D

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

instr_D

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8095em;vertical-align:-0.15em;">



</span>

<span className="mord,mathnormal">

in

</span>

<span className="mord,mathnormal">

s

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.0278em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

D

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

<br />

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-33.webp)<br />

流程是：
  1. PC 寄存器输出当前取指地址 <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mi>
  
  P
  
  </mi>
  
  <msub>
  <mi>
  
  C
  
  </mi>
  
  <mi>
  
  F
  
  </mi>
  </msub>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  PC_F
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:0.8333em;vertical-align:-0.15em;">
  
  
  
  </span>
  
  <span className="mord,mathnormal" style="margin-right:0.1389em;">
  
  P
  
  </span>
  
  <span className="mord">
  <span className="mord,mathnormal" style="margin-right:0.0715em;">
  
  C
  
  </span>
  
  <span className="msupsub">
  <span className="vlist-t,vlist-t2">
  <span className="vlist-r">
  <span className="vlist" style="height:0.3283em;">
  <span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
  <span className="pstrut" style="height:2.7em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size6,size3,mtight">
  <span className="mord,mathnormal,mtight" style="margin-right:0.1389em;">
  
  F
  
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
  
  。
  2. 这个地址送到 I$，I$ 检查自己有没有这个地址对应的指令。
  3. 如果 hit，就把指令送入 IF/ID 流水线寄存器，下一拍进入 ID 阶段;  同时 <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mi>
  
  P
  
  </mi>
  
  <mi>
  
  C
  
  </mi>
  
  <mo>
  
  +
  
  </mo>
  
  <mn>
  
  4
  
  </mn>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  PC+4
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">
  
  
  
  </span>
  
  <span className="mord,mathnormal" style="margin-right:0.1389em;">
  
  P
  
  </span>
  
  <span className="mord,mathnormal" style="margin-right:0.0715em;">
  
  C
  
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
  <span className="strut" style="height:0.6444em;">
  
  
  
  </span>
  
  <span className="mord">
  
  4
  
  </span>
  </span>
  </span>
  </span>
  
   也被计算出来，用于默认顺序取下一条指令。
  4. 如果miss，当前 PC 对应的指令不在一级指令缓存，这时 I$ 必须向更低层存储器请求数据块：I$ → Memory Controller → L2 / Main Memory
  
    1. `To Memory Controller`：向下级存储系统发请求；
    2. `Refill $ Data from Lower Levels of Memory Hierarchy`：从低层存储器把整块 cache line 填回来；
    3. `bubble`：在等待期间给流水线送空操作；
    4. `pc_en`：冻结 PC，避免 PC 一直往后跑。

> - `pc_F`：取指地址。
> - `Primary I$`：一级指令缓存。
> - `Hit?`：是否命中。
> - `instr_D`：送入译码阶段的指令。
> - `pc_en`：PC 是否允许更新。
> - `bubble`：如果取不到有效指令，就往后面送一个空操作

1. ID 阶段：译码、读寄存器、生成立即数

  1. 这段就是和其他流水线或者多周期CPU无异，一样的译码、读寄存器、生成立即数操作
2. EX 阶段：ALU 做三类事情

  1. 仍然和其他流水线或者多周期CPU无异
3. MEM 阶段：D$ 负责 load/store——右边 DMEM 那块现在实际对应 D$。

  1. 对于普通 ALU 指令，这一级基本只是把 ALU 结果继续往后传，和D$无关
  2. 对于访存指令：
  ![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-34.webp)
    1. lw / lb 等 load：<span className="katex">
    <span className="katex-mathml">
    <math xmlns="http://www.w3.org/1998/Math/MathML">
    <semantics>
    <mrow>
    <mi>
    
    A
    
    </mi>
    
    <mi>
    
    L
    
    </mi>
    
    <mi>
    
    U
    
    </mi>
    
    <mtext>
    
    
    
    </mtext>
    
    <mi>
    
    r
    
    </mi>
    
    <mi>
    
    e
    
    </mi>
    
    <mi>
    
    s
    
    </mi>
    
    <mi>
    
    u
    
    </mi>
    
    <mi>
    
    l
    
    </mi>
    
    <mi>
    
    t
    
    </mi>
    
    <mo>
    
    =
    
    </mo>
    
    <mi>
    
    A
    
    </mi>
    
    <mi>
    
    d
    
    </mi>
    
    <mi>
    
    d
    
    </mi>
    
    <mi>
    
    r
    
    </mi>
    </mrow>
    
    <annotation encoding="application/x-tex">
    
    ALU\ result = Addr
    
    </annotation>
    </semantics>
    </math>
    </span>
    
    <span className="katex-html" ariaHidden="true">
    <span className="base">
    <span className="strut" style="height:0.6944em;">
    
    
    
    </span>
    
    <span className="mord,mathnormal">
    
    A
    
    </span>
    
    <span className="mord,mathnormal" style="margin-right:0.109em;">
    
    LU
    
    </span>
    
    <span className="mspace">
    
    
    
    </span>
    
    <span className="mord,mathnormal" style="margin-right:0.0278em;">
    
    r
    
    </span>
    
    <span className="mord,mathnormal">
    
    es
    
    </span>
    
    <span className="mord,mathnormal">
    
    u
    
    </span>
    
    <span className="mord,mathnormal" style="margin-right:0.0197em;">
    
    l
    
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
    <span className="strut" style="height:0.6944em;">
    
    
    
    </span>
    
    <span className="mord,mathnormal">
    
    A
    
    </span>
    
    <span className="mord,mathnormal">
    
    dd
    
    </span>
    
    <span className="mord,mathnormal" style="margin-right:0.0278em;">
    
    r
    
    </span>
    </span>
    </span>
    </span>
    
     → D$ → <span className="katex">
    <span className="katex-mathml">
    <math xmlns="http://www.w3.org/1998/Math/MathML">
    <semantics>
    <mrow>
    <mi>
    
    D
    
    </mi>
    
    <mi>
    
    a
    
    </mi>
    
    <mi>
    
    t
    
    </mi>
    
    <mi>
    
    a
    
    </mi>
    
    <mi>
    
    R
    
    </mi>
    </mrow>
    
    <annotation encoding="application/x-tex">
    
    DataR
    
    </annotation>
    </semantics>
    </math>
    </span>
    
    <span className="katex-html" ariaHidden="true">
    <span className="base">
    <span className="strut" style="height:0.6833em;">
    
    
    
    </span>
    
    <span className="mord,mathnormal" style="margin-right:0.0278em;">
    
    D
    
    </span>
    
    <span className="mord,mathnormal">
    
    a
    
    </span>
    
    <span className="mord,mathnormal">
    
    t
    
    </span>
    
    <span className="mord,mathnormal">
    
    a
    
    </span>
    
    <span className="mord,mathnormal" style="margin-right:0.0077em;">
    
    R
    
    </span>
    </span>
    </span>
    </span>
    2. sw / sb 等 store: <span className="katex">
    <span className="katex-mathml">
    <math xmlns="http://www.w3.org/1998/Math/MathML">
    <semantics>
    <mrow>
    <mi>
    
    A
    
    </mi>
    
    <mi>
    
    d
    
    </mi>
    
    <mi>
    
    d
    
    </mi>
    
    <mi>
    
    r
    
    </mi>
    
    <mo>
    
    →
    
    </mo>
    
    <mi>
    
    D
    
    </mi>
    </mrow>
    
    <annotation encoding="application/x-tex">
    
    Addr \rightarrow D
    
    </annotation>
    </semantics>
    </math>
    </span>
    
    <span className="katex-html" ariaHidden="true">
    <span className="base">
    <span className="strut" style="height:0.6944em;">
    
    
    
    </span>
    
    <span className="mord,mathnormal">
    
    A
    
    </span>
    
    <span className="mord,mathnormal">
    
    dd
    
    </span>
    
    <span className="mord,mathnormal" style="margin-right:0.0278em;">
    
    r
    
    </span>
    
    <span className="mspace" style="margin-right:0.2778em;">
    
    
    
    </span>
    
    <span className="mrel">
    
    →
    
    </span>
    
    <span className="mspace" style="margin-right:0.2778em;">
    
    
    
    </span>
    </span>
    
    <span className="base">
    <span className="strut" style="height:0.6833em;">
    
    
    
    </span>
    
    <span className="mord,mathnormal" style="margin-right:0.0278em;">
    
    D
    
    </span>
    </span>
    </span>
    </span>
    
    、<span className="katex">
    <span className="katex-mathml">
    <math xmlns="http://www.w3.org/1998/Math/MathML">
    <semantics>
    <mrow>
    <mi>
    
    D
    
    </mi>
    
    <mi>
    
    a
    
    </mi>
    
    <mi>
    
    t
    
    </mi>
    
    <mi>
    
    a
    
    </mi>
    
    <mi>
    
    W
    
    </mi>
    
    <mo>
    
    →
    
    </mo>
    
    <mi>
    
    D
    
    </mi>
    </mrow>
    
    <annotation encoding="application/x-tex">
    
    DataW \rightarrow D
    
    </annotation>
    </semantics>
    </math>
    </span>
    
    <span className="katex-html" ariaHidden="true">
    <span className="base">
    <span className="strut" style="height:0.6833em;">
    
    
    
    </span>
    
    <span className="mord,mathnormal" style="margin-right:0.0278em;">
    
    D
    
    </span>
    
    <span className="mord,mathnormal">
    
    a
    
    </span>
    
    <span className="mord,mathnormal">
    
    t
    
    </span>
    
    <span className="mord,mathnormal" style="margin-right:0.1389em;">
    
    aW
    
    </span>
    
    <span className="mspace" style="margin-right:0.2778em;">
    
    
    
    </span>
    
    <span className="mrel">
    
    →
    
    </span>
    
    <span className="mspace" style="margin-right:0.2778em;">
    
    
    
    </span>
    </span>
    
    <span className="base">
    <span className="strut" style="height:0.6833em;">
    
    
    
    </span>
    
    <span className="mord,mathnormal" style="margin-right:0.0278em;">
    
    D
    
    </span>
    </span>
    </span>
    </span>
    
    
      - `Addr` 是 ALU 算出来的地址；
      - `DataW` 是要写入内存的数据，也就是原来的 <span className="katex">
      <span className="katex-mathml">
      <math xmlns="http://www.w3.org/1998/Math/MathML">
      <semantics>
      <mrow>
      <mi>
      
      R
      
      </mi>
      
      <mi>
      
      e
      
      </mi>
      
      <mi>
      
      g
      
      </mi>
      
      <mo stretchy="false">
      
      [
      
      </mo>
      
      <mi>
      
      r
      
      </mi>
      
      <mi>
      
      s
      
      </mi>
      
      <mn>
      
      2
      
      </mn>
      
      <mo stretchy="false">
      
      ]
      
      </mo>
      </mrow>
      
      <annotation encoding="application/x-tex">
      
      Reg[rs2]
      
      </annotation>
      </semantics>
      </math>
      </span>
      
      <span className="katex-html" ariaHidden="true">
      <span className="base">
      <span className="strut" style="height:1em;vertical-align:-0.25em;">
      
      
      
      </span>
      
      <span className="mord,mathnormal" style="margin-right:0.0077em;">
      
      R
      
      </span>
      
      <span className="mord,mathnormal">
      
      e
      
      </span>
      
      <span className="mord,mathnormal" style="margin-right:0.0359em;">
      
      g
      
      </span>
      
      <span className="mopen">
      
      [
      
      </span>
      
      <span className="mord,mathnormal" style="margin-right:0.0278em;">
      
      r
      
      </span>
      
      <span className="mord,mathnormal">
      
      s
      
      </span>
      
      <span className="mord">
      
      2
      
      </span>
      
      <span className="mclose">
      
      ]
      
      </span>
      </span>
      </span>
      </span>
      
      。
    3. 对于D Cache的相关操作：
    
      1. MEM 阶段地址访问 D$；
      2. D$ 如果hit，则返回数据 `DataR`；D$ hit ⇒ DataR 直接送往 WB
      3. 如果没有hit，则 stall entire CPU:
      
        1. 当前 MEM 阶段的 load/store 还没有完成，它对应的是一条已经在流水线中间的真实指令。如果让后面的流水线继续推进，就会出现严重问题：
        
          1. load 还没拿到数据，后续指令可能已经要用这个结果
          2. store 还没完成，后续访存可能和它有顺序关系
          3. 如果允许后面的指令越过它执行，就破坏了简单顺序流水线的语义
        2. 所以 D$ miss 时一般要冻结下面的全部流程：
        
          - PC；
          - IF/ID；
          - ID/EX；
          - EX/MEM；
          - MEM/WB 或相关控制
        - <mark>
        
        **直到 D$ 从低层存储器把缺失 block 拿回来，当前 load/store 完成后，流水线再继续。**
        
        </mark>

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 57.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-35.webp" />
      </p>
    </td>
    
    
      <td style="width: 42.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-36.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

<alert type="tip">
<mark>

**当流水线 CPU 接入真实缓存后，访存不再总是固定 1 个周期，cache miss 会让流水线控制变复杂，缓存 hit 让流水线接近**

</mark>

 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
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

=

</mo>

<mn>

1

</mn>
</mrow>

<annotation encoding="application/x-tex">

CPI=1

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

<span className="mord,mathnormal" style="margin-right:0.0785em;">

I

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

1

</span>
</span>
</span>
</span>

<mark>

**，cache miss 会引入额外 stall，使实际 CPI 增大。**

</mark>
</alert>

##### CPU-Cache 缓存交互总结

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-37.webp)

<mark>

**IF 阶段**

</mark>

用 PC 访问主指令缓存。如果 I$ hit，指令进入 IF / ID 阶段；如果 I$ miss，指令取不到，就要从低层存储器 refill，同时**流水线前端会插入 bubble，PC/取指相关部分暂停**。

<mark>

**MEM 阶段**

</mark>

访问 Primary Data Cache。load/store 如果 hit，就正常返回数据或写入数据；<mark>

**如果 D$ miss，数据缓存未命中导致整个 CPU 失速**

</mark>

**,**因为这条访存指令已经在流水线中间，如果它没完成，后面的指令不能乱往前推进，所以通常要冻结整个流水线，等 lower memory hierarchy 把数据块填回来。

### Cache 的内部组织

#### 缓存内部 ｜ Inside a Cache

<mark>

Cache 是按“块 / 行”存主存中一小段连续地址的数据，并且每一行都要带一个地址标签，用来说明这块数据来自主存哪里

</mark>



<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 46.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-38.webp" />
      </p>
    </td>
    
    
      <td style="width: 53.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-39.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

- Cache 内部通常按 **cache line** 组织。
- 一个 cache line 由两部分构成：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mtext>

Cache Line

</mtext>

<mo>

=

</mo>

<mtext>

Address Tag

</mtext>

<mo>

+

</mo>

<mtext>

Data Block

</mtext>
</mrow>

<annotation encoding="application/x-tex">

\text{Cache Line} = \text{Address Tag} + \text{Data Block}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,text">
<span className="mord">

Cache Line

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
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,text">
<span className="mord">

Address Tag

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
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,text">
<span className="mord">

Data Block

</span>
</span>
</span>
</span>
</span>


  1. Address Tag：地址标签，说明这一行数据来自主存哪个区域。
  
    1. Cache 很小，不可能保存整个主存，所以某一个 cache line 里现在放的到底是主存哪一块数据，必须有一个标记。
    2. 这个标记就是：<span className="katex">
    <span className="katex-mathml">
    <math xmlns="http://www.w3.org/1998/Math/MathML">
    <semantics>
    <mrow>
    <mi>
    
    A
    
    </mi>
    
    <mi>
    
    d
    
    </mi>
    
    <mi>
    
    d
    
    </mi>
    
    <mi>
    
    r
    
    </mi>
    
    <mi>
    
    e
    
    </mi>
    
    <mi>
    
    s
    
    </mi>
    
    <mi>
    
    s
    
    </mi>
    
    <mtext>
    
    
    
    </mtext>
    
    <mi>
    
    T
    
    </mi>
    
    <mi>
    
    a
    
    </mi>
    
    <mi>
    
    g
    
    </mi>
    </mrow>
    
    <annotation encoding="application/x-tex">
    
    Address\ Tag
    
    </annotation>
    </semantics>
    </math>
    </span>
    
    <span className="katex-html" ariaHidden="true">
    <span className="base">
    <span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">
    
    
    
    </span>
    
    <span className="mord,mathnormal">
    
    A
    
    </span>
    
    <span className="mord,mathnormal">
    
    dd
    
    </span>
    
    <span className="mord,mathnormal" style="margin-right:0.0278em;">
    
    r
    
    </span>
    
    <span className="mord,mathnormal">
    
    ess
    
    </span>
    
    <span className="mspace">
    
    
    
    </span>
    
    <span className="mord,mathnormal" style="margin-right:0.1389em;">
    
    T
    
    </span>
    
    <span className="mord,mathnormal">
    
    a
    
    </span>
    
    <span className="mord,mathnormal" style="margin-right:0.0359em;">
    
    g
    
    </span>
    </span>
    </span>
    </span>

> 例如某个 cache line 里存的是主存地址 100 开始的一块数据：
> 
> ```text
> Tag = 100
> Data Block = Memory[100], Memory[101], Memory[102], ...
> ```
> 
> 那么当处理器请求地址 100 时，Cache 检查 tag，发现这个 line 确实对应地址 100 附近的数据，于是命中。
> 
> 如果处理器请求地址 6848，但是这个 line 的 tag 是 100，那就说明这行不是你要的数据，发生 miss。

1. Data Block：数据块，保存主存中一段连续数据的副本。

> 例如一个 data block 可能包含：<span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <mi>
> 
> M
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
> m
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
> r
> 
> </mi>
> 
> <mi>
> 
> y
> 
> </mi>
> 
> <mo stretchy="false">
> 
> [
> 
> </mo>
> 
> <mn>
> 
> 100
> 
> </mn>
> 
> <mo stretchy="false">
> 
> ]
> 
> </mo>
> 
> <mo separator="true">
> 
> ,
> 
> </mo>
> 
> <mi>
> 
> M
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
> m
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
> r
> 
> </mi>
> 
> <mi>
> 
> y
> 
> </mi>
> 
> <mo stretchy="false">
> 
> [
> 
> </mo>
> 
> <mn>
> 
> 101
> 
> </mn>
> 
> <mo stretchy="false">
> 
> ]
> 
> </mo>
> 
> <mo separator="true">
> 
> ,
> 
> </mo>
> 
> <mi>
> 
> M
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
> m
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
> r
> 
> </mi>
> 
> <mi>
> 
> y
> 
> </mi>
> 
> <mo stretchy="false">
> 
> [
> 
> </mo>
> 
> <mn>
> 
> 102
> 
> </mn>
> 
> <mo stretchy="false">
> 
> ]
> 
> </mo>
> 
> <mo separator="true">
> 
> ,
> 
> </mo>
> 
> <mi>
> 
> M
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
> m
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
> r
> 
> </mi>
> 
> <mi>
> 
> y
> 
> </mi>
> 
> <mo stretchy="false">
> 
> [
> 
> </mo>
> 
> <mn>
> 
> 103
> 
> </mn>
> 
> <mo stretchy="false">
> 
> ]
> 
> </mo>
> 
> <mo>
> 
> ⋯
> 
> </mo>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> Memory[100], Memory[101], Memory[102], Memory[103] \cdots
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:1em;vertical-align:-0.25em;">
> 
> 
> 
> </span>
> 
> <span className="mord,mathnormal" style="margin-right:0.109em;">
> 
> M
> 
> </span>
> 
> <span className="mord,mathnormal">
> 
> e
> 
> </span>
> 
> <span className="mord,mathnormal">
> 
> m
> 
> </span>
> 
> <span className="mord,mathnormal" style="margin-right:0.0278em;">
> 
> or
> 
> </span>
> 
> <span className="mord,mathnormal" style="margin-right:0.0359em;">
> 
> y
> 
> </span>
> 
> <span className="mopen">
> 
> [
> 
> </span>
> 
> <span className="mord">
> 
> 100
> 
> </span>
> 
> <span className="mclose">
> 
> ]
> 
> </span>
> 
> <span className="mpunct">
> 
> ,
> 
> </span>
> 
> <span className="mspace" style="margin-right:0.1667em;">
> 
> 
> 
> </span>
> 
> <span className="mord,mathnormal" style="margin-right:0.109em;">
> 
> M
> 
> </span>
> 
> <span className="mord,mathnormal">
> 
> e
> 
> </span>
> 
> <span className="mord,mathnormal">
> 
> m
> 
> </span>
> 
> <span className="mord,mathnormal" style="margin-right:0.0278em;">
> 
> or
> 
> </span>
> 
> <span className="mord,mathnormal" style="margin-right:0.0359em;">
> 
> y
> 
> </span>
> 
> <span className="mopen">
> 
> [
> 
> </span>
> 
> <span className="mord">
> 
> 101
> 
> </span>
> 
> <span className="mclose">
> 
> ]
> 
> </span>
> 
> <span className="mpunct">
> 
> ,
> 
> </span>
> 
> <span className="mspace" style="margin-right:0.1667em;">
> 
> 
> 
> </span>
> 
> <span className="mord,mathnormal" style="margin-right:0.109em;">
> 
> M
> 
> </span>
> 
> <span className="mord,mathnormal">
> 
> e
> 
> </span>
> 
> <span className="mord,mathnormal">
> 
> m
> 
> </span>
> 
> <span className="mord,mathnormal" style="margin-right:0.0278em;">
> 
> or
> 
> </span>
> 
> <span className="mord,mathnormal" style="margin-right:0.0359em;">
> 
> y
> 
> </span>
> 
> <span className="mopen">
> 
> [
> 
> </span>
> 
> <span className="mord">
> 
> 102
> 
> </span>
> 
> <span className="mclose">
> 
> ]
> 
> </span>
> 
> <span className="mpunct">
> 
> ,
> 
> </span>
> 
> <span className="mspace" style="margin-right:0.1667em;">
> 
> 
> 
> </span>
> 
> <span className="mord,mathnormal" style="margin-right:0.109em;">
> 
> M
> 
> </span>
> 
> <span className="mord,mathnormal">
> 
> e
> 
> </span>
> 
> <span className="mord,mathnormal">
> 
> m
> 
> </span>
> 
> <span className="mord,mathnormal" style="margin-right:0.0278em;">
> 
> or
> 
> </span>
> 
> <span className="mord,mathnormal" style="margin-right:0.0359em;">
> 
> y
> 
> </span>
> 
> <span className="mopen">
> 
> [
> 
> </span>
> 
> <span className="mord">
> 
> 103
> 
> </span>
> 
> <span className="mclose">
> 
> ]
> 
> </span>
> 
> <span className="mspace" style="margin-right:0.1667em;">
> 
> 
> 
> </span>
> 
> <span className="minner">
> 
> ⋯
> 
> </span>
> </span>
> </span>
> </span>
> 
> 
> 
> 所以 Cache 不是只把地址 100 这一个字节拿进来，而是会把**地址 100 附近的一整块连续数据**一起拿进来。

##### 例1

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-40.webp)

#### Cache Read Algorithm ｜ 缓存读取算法

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-41.webp)

其实没有什么高大上的算法，实际上还是一套东西——Hit了就皆大欢喜了，直接拿来用；如果Miss了，那么就去从主存储器中拿数据，然后给处理器的同时也更新缓存；

PPT中还提到了一个问题：**“我们要替换哪一行？”**凭空出现了这样一句话，实际上想要表达的是：**如果cache满了，我们需要“踢”出去某一行cache line，然后把我们新拿到的数据存进去。**<mark>

**这个下面讲**

</mark>



#### Cache Replacement | 缓存替换

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-42.webp)

如图所示的例子中，处理器现在请求位置 511，其中包含 11，但是511 不匹配任何 tag，所以 miss。**cache 又满了，所以必须选择一个已有 block 作为 victim，把它驱逐掉**：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mtext>

evict old block

</mtext>

<mo>

→

</mo>

<mtext>

refill new block 511

</mtext>
</mrow>

<annotation encoding="application/x-tex">

\text{evict old block} \rightarrow \text{refill new block 511}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,text">
<span className="mord">

evict old block

</span>
</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

→

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,text">
<span className="mord">

refill new block 511

</span>
</span>
</span>
</span>
</span>



<mark>

**替换策略是：**

</mark>

<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi mathvariant="bold">

L

</mi>

<mi mathvariant="bold">

R

</mi>

<mi mathvariant="bold">

U

</mi>

<mo>

=

</mo>

<mi mathvariant="bold">

L

</mi>

<mi mathvariant="bold">

e

</mi>

<mi mathvariant="bold">

a

</mi>

<mi mathvariant="bold">

s

</mi>

<mi mathvariant="bold">

t

</mi>

<mtext>



</mtext>

<mi mathvariant="bold">

R

</mi>

<mi mathvariant="bold">

e

</mi>

<mi mathvariant="bold">

c

</mi>

<mi mathvariant="bold">

e

</mi>

<mi mathvariant="bold">

n

</mi>

<mi mathvariant="bold">

t

</mi>

<mi mathvariant="bold">

l

</mi>

<mi mathvariant="bold">

y

</mi>

<mtext>



</mtext>

<mi mathvariant="bold">

U

</mi>

<mi mathvariant="bold">

s

</mi>

<mi mathvariant="bold">

e

</mi>

<mi mathvariant="bold">

d

</mi>
</mrow>

<annotation encoding="application/x-tex">

\mathbf{LRU = Least\ Recently\ Used}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord">
<span className="mord,mathbf">

LRU

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mord,mathbf">

Least

</span>

<span className="mspace">



</span>

<span className="mord,mathbf" style="margin-right:0.016em;">

Recently

</span>

<span className="mspace">



</span>

<span className="mord,mathbf">

Used

</span>
</span>
</span>
</span>
</span>

<mark>

，也就是替换“最近最久没用过”的那一行

</mark>

。图里红框标出的那行就是被认为最久没用的 victim。

> 最近用过的数据很可能马上还会用；很久没用的数据相对更适合被替换。

#### Block alignment | 内存中block对齐问题

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-43.webp)

如果一个 block 是一个 word，也就是 4Byte ，那么这个Block的起始地址必须是 4 的倍数。所以 byte address 的最低 2 位一定是：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mn>

00

</mn>

<mn>

2

</mn>
</msub>
</mrow>

<annotation encoding="application/x-tex">

00_2

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.7944em;vertical-align:-0.15em;">



</span>

<span className="mord">

0

</span>

<span className="mord">
<span className="mord">

0

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">

2

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

;

> （ 举例，它的block地址只能是：<span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <mi mathvariant="normal">
> 
> .
> 
> </mi>
> 
> <mi mathvariant="normal">
> 
> .
> 
> </mi>
> 
> <mn>
> 
> .0000
> 
> </mn>
> 
> <mo separator="true">
> 
> ,
> 
> </mo>
> 
> <mtext>
> 
> 
> 
> </mtext>
> 
> <mi mathvariant="normal">
> 
> .
> 
> </mi>
> 
> <mi mathvariant="normal">
> 
> .
> 
> </mi>
> 
> <mn>
> 
> .0100
> 
> </mn>
> 
> <mo separator="true">
> 
> ,
> 
> </mo>
> 
> <mtext>
> 
> 
> 
> </mtext>
> 
> <mi mathvariant="normal">
> 
> .
> 
> </mi>
> 
> <mi mathvariant="normal">
> 
> .
> 
> </mi>
> 
> <mn>
> 
> .1000
> 
> </mn>
> 
> <mo separator="true">
> 
> ,
> 
> </mo>
> 
> <mtext>
> 
> 
> 
> </mtext>
> 
> <mi mathvariant="normal">
> 
> .
> 
> </mi>
> 
> <mi mathvariant="normal">
> 
> .
> 
> </mi>
> 
> <mn>
> 
> .1100
> 
> </mn>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> ...0000,\ ...0100,\ ...1000,\ ...1100
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:0.8389em;vertical-align:-0.1944em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> 
> ...0000
> 
> </span>
> 
> <span className="mpunct">
> 
> ,
> 
> </span>
> 
> <span className="mspace">
> 
> 
> 
> </span>
> 
> <span className="mspace" style="margin-right:0.1667em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> 
> ...0100
> 
> </span>
> 
> <span className="mpunct">
> 
> ,
> 
> </span>
> 
> <span className="mspace">
> 
> 
> 
> </span>
> 
> <span className="mspace" style="margin-right:0.1667em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> 
> ...1000
> 
> </span>
> 
> <span className="mpunct">
> 
> ,
> 
> </span>
> 
> <span className="mspace">
> 
> 
> 
> </span>
> 
> <span className="mspace" style="margin-right:0.1667em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> 
> ...1100
> 
> </span>
> </span>
> </span>
> </span>
> 
> ）

这有什么用——

1. 不需要比较最后 2 位地址，因为它们永远是 00，不参与判断 block 是谁。所以 **tag comparator（Cache Tag 的比较器）** 可以更窄。
2. 不需要在 tag 里存最后 2 位，因为它们永远是 00
3. 所以说实际存储的tag实际上是经过拆分过的——<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

A

</mi>

<mi>

d

</mi>

<mi>

d

</mi>

<mi>

r

</mi>

<mi>

e

</mi>

<mi>

s

</mi>

<mi>

s

</mi>

<mo>

=

</mo>

<mi>

T

</mi>

<mi>

a

</mi>

<mi>

g

</mi>

<mo>

+

</mo>

<mi>

O

</mi>

<mi>

f

</mi>

<mi>

f

</mi>

<mi>

s

</mi>

<mi>

e

</mi>

<mi>

t

</mi>
</mrow>

<annotation encoding="application/x-tex">

Address = Tag + Offset

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,mathnormal">

A

</span>

<span className="mord,mathnormal">

dd

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal">

ess

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
<span className="strut" style="height:0.8778em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

T

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

g

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
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

O

</span>

<span className="mord,mathnormal" style="margin-right:0.1076em;">

f

</span>

<span className="mord,mathnormal" style="margin-right:0.1076em;">

f

</span>

<span className="mord,mathnormal">

se

</span>

<span className="mord,mathnormal">

t

</span>
</span>
</span>
</span>

##### 例2

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-44.webp)

这一页把 block 从 4B 扩大到 8B。<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

C

</mi>

<mi>

a

</mi>

<mi>

c

</mi>

<mi>

h

</mi>

<mi>

e

</mi>

<mtext>



</mtext>

<mi>

s

</mi>

<mi>

i

</mi>

<mi>

z

</mi>

<mi>

e

</mi>

<mo>

=

</mo>

<mn>

32

</mn>

<mi>

B

</mi>
</mrow>

<annotation encoding="application/x-tex">

Cache\ size = 32B

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal">

c

</span>

<span className="mord,mathnormal">

h

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal">

s

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal" style="margin-right:0.044em;">

z

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
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord">

32

</span>

<span className="mord,mathnormal" style="margin-right:0.0502em;">

B

</span>
</span>
</span>
</span>

，<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

B

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

s

</mi>

<mi>

i

</mi>

<mi>

z

</mi>

<mi>

e

</mi>

<mo>

=

</mo>

<mn>

8

</mn>

<mi>

B

</mi>
</mrow>

<annotation encoding="application/x-tex">

Block\ size = 8B

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0502em;">

B

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

<span className="mord,mathnormal">

s

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal" style="margin-right:0.044em;">

z

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
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord">

8

</span>

<span className="mord,mathnormal" style="margin-right:0.0502em;">

B

</span>
</span>
</span>
</span>

， 所以 cache 仍然有：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mn>

32

</mn>

<mi>

B

</mi>

<mi mathvariant="normal">

/

</mi>

<mn>

8

</mn>

<mi>

B

</mi>

<mo>

=

</mo>

<mn>

4

</mn>

<mtext>



</mtext>

<mi>

b

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

s

</mi>
</mrow>

<annotation encoding="application/x-tex">

32B / 8B = 4\ blocks

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord">

32

</span>

<span className="mord,mathnormal" style="margin-right:0.0502em;">

B

</span>

<span className="mord">

/8

</span>

<span className="mord,mathnormal" style="margin-right:0.0502em;">

B

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
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord">

4

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal">

b

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

<span className="mord,mathnormal">

s

</span>
</span>
</span>
</span>

但每个 block 现在可以放两个 4Byte word。

这里 tag 只记录 block 的起始地址，也就是对齐后的地址。**因为 8B block 必须按 8B 对齐，所以地址最低 3 位一定是：**<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mn>

000

</mn>

<mn>

2

</mn>
</msub>
</mrow>

<annotation encoding="application/x-tex">

000_2

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.7944em;vertical-align:-0.15em;">



</span>

<span className="mord">

00

</span>

<span className="mord">
<span className="mord">

0

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">

2

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



这 3 位不用存进 tag，也不用参与 tag compare。

##### 总结

- tag 只记录对齐后的 block 地址，所以表里会出现 130、2040 这种 block base；
- tag 和 comparator 可以更窄；
- 只要请求地址落在这个 block 里的任意一个 word，都算 hit。

例如：Block存储如下

<table>
<thead>
  <tr>
    <th>
      Tag
    </th>
    
    <th>
      Word 0
    </th>
    
    <th>
      Word 1
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      252
    </td>
    
    <td>
      12
    </td>
    
    <td>
      -10
    </td>
  </tr>
  
  <tr>
    <td>
      1022
    </td>
    
    <td>
      99
    </td>
    
    <td>
      1000
    </td>
  </tr>
  
  <tr>
    <td>
      130
    </td>
    
    <td>
      42
    </td>
    
    <td>
      7
    </td>
  </tr>
  
  <tr>
    <td>
      2040
    </td>
    
    <td>
      1947
    </td>
    
    <td>
      20
    </td>
  </tr>
</tbody>
</table>

**请求地址对应 word 131 时，cache 比较到 tag 130 命中**，然后用 block 内 offset 选择第二个 word，也就是数据 7。

#### Hardware Cost of Cache ｜ 硬件缓存成本

如果 cache 很小，比如 4 行，那就可以比较所有的Tag；但是实际的Cache是有很多行的，如果每次访问都把处理器地址和所有 tag 比较，需要大量 comparator。

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 49.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-45.webp" />
      </p>
    </td>
    
    
      <td style="width: 50.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-46.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

所以优化方法是：**把 cache 分成多个 set。**图里先分成两组：

- 组 0
- 组 1

然后用地址中的某一位先选择组，<mark>

**相当于我是建立了一个从地址到组号的一个映射（实际上就是数组）**

</mark>

，只在被选中的 set 里面比较 tag，而不是比较整个 cache 的所有 tag。这样比较器数量减少，硬件面积和能耗下降。这个思想可以推广到更多 set。

- **组索引 Set Index**：中间某些位，用来选择进入哪一组；<mark>

（比如说地址0000——对应组1，地址0001 对应组2 这种提前写好的规则）

</mark>
- **比较标签 Tag Compare**：高位地址，用来和 cache 中 tag 比较；
- **字中的字节 Byte in word(block)**：最低位，用来选择 word 内具体字节。

##### Cache的访问流程

<mark>

**Cache的访问流程**

</mark>

变成：

1. 用 set index 选 set；
2. 在这个 set 内比较 tag；
3. tag 匹配则 hit，返回对应 data。
4. 用低位 offset 定位块内字节；

### Cache 地址字段与查找流程

> <mark>
> 
> 地址本身就是一串 bit；Tag、Index、Offset 是 cache 根据位的位置人为定义出来的三个字段。
> 
> </mark>

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-47.webp)

#### 举例

```text
32 位地址
Cache 容量 = 8KB
Block size = 32B
2 路组相联
```

先算 cache 有多少个 block：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mn>

8

</mn>

<mtext>

KB

</mtext>

<mi mathvariant="normal">

/

</mi>

<mn>

32

</mn>

<mtext>

B

</mtext>

<mo>

=

</mo>

<mn>

256

</mn>
</mrow>

<annotation encoding="application/x-tex">

8\text{KB} / 32\text{B} = 256

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord">

8

</span>

<span className="mord,text">
<span className="mord">

KB

</span>
</span>

<span className="mord">

/32

</span>

<span className="mord,text">
<span className="mord">

B

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

256

</span>
</span>
</span>
</span>

,

因为是 2 路组相联，所以 set 数是：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mn>

256

</mn>

<mi mathvariant="normal">

/

</mi>

<mn>

2

</mn>

<mo>

=

</mo>

<mn>

128

</mn>
</mrow>

<annotation encoding="application/x-tex">

256 / 2 = 128

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord">

256/2

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

128

</span>
</span>
</span>
</span>

,

于是：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mtext>

block offset bits

</mtext>

<mo>

=

</mo>

<msub>
<mrow>
<mi>

log

</mi>

<mo>

⁡

</mo>
</mrow>

<mn>

2

</mn>
</msub>

<mn>

32

</mn>

<mo>

=

</mo>

<mn>

5

</mn>
</mrow>

<annotation encoding="application/x-tex">

\text{block offset bits} = \log_2 32 = 5

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,text">
<span className="mord">

block offset bits

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
<span className="strut" style="height:0.9386em;vertical-align:-0.2441em;">



</span>

<span className="mop">
<span className="mop">

lo<span style="margin-right:0.0139em;">

g

</span>
</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.207em;">
<span style="top:-2.4559em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">

2

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.2441em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord">

32

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

5

</span>
</span>
</span>
</span>

， <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mtext>

set index bits

</mtext>

<mo>

=

</mo>

<msub>
<mrow>
<mi>

log

</mi>

<mo>

⁡

</mo>
</mrow>

<mn>

2

</mn>
</msub>

<mn>

128

</mn>

<mo>

=

</mo>

<mn>

7

</mn>
</mrow>

<annotation encoding="application/x-tex">

\text{set index bits} = \log_2 128 = 7

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,text">
<span className="mord">

set index bits

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
<span className="strut" style="height:0.9386em;vertical-align:-0.2441em;">



</span>

<span className="mop">
<span className="mop">

lo<span style="margin-right:0.0139em;">

g

</span>
</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.207em;">
<span style="top:-2.4559em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">

2

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.2441em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord">

128

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

7

</span>
</span>
</span>
</span>

，<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mtext>

tag bits

</mtext>

<mo>

=

</mo>

<mn>

32

</mn>

<mo>

−

</mo>

<mn>

5

</mn>

<mo>

−

</mo>

<mn>

7

</mn>

<mo>

=

</mo>

<mn>

20

</mn>
</mrow>

<annotation encoding="application/x-tex">

\text{tag bits} = 32 - 5 - 7 = 20

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,text">
<span className="mord">

tag bits

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
<span className="strut" style="height:0.7278em;vertical-align:-0.0833em;">



</span>

<span className="mord">

32

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
<span className="strut" style="height:0.7278em;vertical-align:-0.0833em;">



</span>

<span className="mord">

5

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

7

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

20

</span>
</span>
</span>
</span>



所以地址被拆成：`[ tag: 20 bits | set index: 7 bits | block offset: 5 bits ]`

### Cache 块分配方法

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-48.webp)

1. <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mtext>

cache block 总数

</mtext>

<mo>

=

</mo>

<mtext>

set 数

</mtext>

<mo>

×

</mo>

<mtext>

每个 set 里的 block 数

</mtext>
</mrow>

<annotation encoding="application/x-tex">

\text{cache block 总数}=\text{set 数}\times \text{每个 set 里的 block 数}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,text">
<span className="mord">

cache block

</span>

<span className="mord,cjk_fallback">

总数

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
<span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">



</span>

<span className="mord,text">
<span className="mord">

set

</span>

<span className="mord,cjk_fallback">

数

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
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,text">
<span className="mord,cjk_fallback">

每个

</span>

<span className="mord">

set

</span>

<span className="mord,cjk_fallback">

里的

</span>

<span className="mord">

block

</span>

<span className="mord,cjk_fallback">

数

</span>
</span>
</span>
</span>
</span>
2. 每个 set 里的 block 数，也叫 **way 数**，也就是 associativity。
3. 所以：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mtext>

set 数

</mtext>

<mo>

=

</mo>

<mfrac>
<mtext>

cache block 总数

</mtext>

<mtext>

way 数

</mtext>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

\text{set 数}=\frac{\text{cache block 总数}}{\text{way 数}}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,text">
<span className="mord">

set

</span>

<span className="mord,cjk_fallback">

数

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
<span className="strut" style="height:1.3612em;vertical-align:-0.4811em;">



</span>

<span className="mord">
<span className="mopen,nulldelimiter">



</span>

<span className="mfrac">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.8801em;">
<span style="top:-2.655em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,text,mtight">
<span className="mord,mtight">

way

</span>

<span className="mord,cjk_fallback,mtight">

数

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
<span className="mord,text,mtight">
<span className="mord,mtight">

cache block

</span>

<span className="mord,cjk_fallback,mtight">

总数

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
<span className="vlist" style="height:0.4811em;">
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

假设 cache 一共有 8 个 block：

- 1 个 set，每个 set 8 个 block  -> fully associative，即全相联缓存方法
- 2 个 set，每个 set 4 个 block
- 4 个 set，每个 set 2 个 block  -> 2-way set associative，即组相联缓存
- 8 个 set，每个 set 1 个 block  -> direct mapped，即直接映射缓存

> **set 的数量最多只能等于 cache block 的数量。这个极限情况叫 direct-mapped cache。**

#### Valid Bit ｜ 有效位

有一个概念叫做Valid bit，这个是指有效位

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-49.webp)

因为 cache 刚启动的时候，里面的 SRAM 存储单元并不是“空白”的。它可能是随机值：Tag 里可能刚好有某个值，Data 里也可能有一堆随机数据，如果没有 valid bit，CPU 来访问某个地址时，只要 tag 碰巧相等，cache 就可能误以为：Hit！但实际上这一行根本没有从主存加载过正确的数据。所以需要一个额外的标志位：valid bit

#### Direct-Mapped Cache ｜ 直接映射缓存

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 33.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-50.webp" />
      </p>
    </td>
    
    
      <td style="width: 66.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-51.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

<mark>

Direct-mapped cache 的意思是：

</mark>

<mark>

**一个（或多个）主存 block 直接映射到 cache 中的一个 cache line。**

</mark>



> 直接缓存映射表示主存中的每一个 block，只能放到 cache 中唯一固定的位置。（感觉加这一句也行）

地址还是拆成三段：`[ Tag | Index | Block Offset ]`

访问流程是：

```c
CPU 给出地址
        ↓
用 Index 直接选中 cache 中的一行
        ↓
取出这一行里保存的 Tag 和 Valid bit
        ↓
比较 CPU 地址里的 Tag 和 cache line 里的 Tag
        ↓
Tag 相等且 Valid = 1，则 Hit
        ↓
再用 Block Offset 选择 block 内具体 byte / word
```

**Hit条件是**<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mtext>

Hit

</mtext>

<mo>

=

</mo>

<mo stretchy="false">

(

</mo>

<mtext>

Valid

</mtext>

<mo>

=

</mo>

<mn>

1

</mn>

<mo stretchy="false">

)

</mo>

<mo>

∧

</mo>

<mo stretchy="false">

(

</mo>

<mtext>

Address Tag

</mtext>

<mo>

=

</mo>

<mtext>

Cache Tag

</mtext>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

\text{Hit}=(\text{Valid}=1)\land(\text{Address Tag}=\text{Cache Tag})

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,text">
<span className="mord">

Hit

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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mopen">

(

</span>

<span className="mord,text">
<span className="mord">

Valid

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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord">

1

</span>

<span className="mclose">

)

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

∧

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

<span className="mord,text">
<span className="mord">

Address Tag

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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord,text">
<span className="mord">

Cache Tag

</span>
</span>

<span className="mclose">

)

</span>
</span>
</span>
</span>



##### 举例：

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 47.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-52.webp" />
      </p>
    </td>
    
    
      <td style="width: 52.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-53.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

```text
内存地址宽度 = 6 bit
内存大小 = 64 Byte
block size = 4 Byte = 1 word
Cache 有 4 个 cache block
```

1. 地址格式分析：
  - 因为地址是 6 bit，所以一共能表示：<span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <msup>
  <mn>
  
  2
  
  </mn>
  
  <mn>
  
  6
  
  </mn>
  </msup>
  
  <mo>
  
  =
  
  </mo>
  
  <mn>
  
  64
  
  </mn>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  2^6=64
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:0.8141em;">
  
  
  
  </span>
  
  <span className="mord">
  <span className="mord">
  
  2
  
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
  
  6
  
  </span>
  </span>
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
  
  64
  
  </span>
  </span>
  </span>
  </span>
  
  个 byte 地址。
  - 因为 block size 是 4 Byte，所以每个 block 里有 4 个 byte，需要：<span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <msub>
  <mrow>
  <mi>
  
  log
  
  </mi>
  
  <mo>
  
  ⁡
  
  </mo>
  </mrow>
  
  <mn>
  
  2
  
  </mn>
  </msub>
  
  <mn>
  
  4
  
  </mn>
  
  <mo>
  
  =
  
  </mo>
  
  <mn>
  
  2
  
  </mn>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  \log_2 4=2
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:0.9386em;vertical-align:-0.2441em;">
  
  
  
  </span>
  
  <span className="mop">
  <span className="mop">
  
  lo<span style="margin-right:0.0139em;">
  
  g
  
  </span>
  </span>
  
  <span className="msupsub">
  <span className="vlist-t,vlist-t2">
  <span className="vlist-r">
  <span className="vlist" style="height:0.207em;">
  <span style="top:-2.4559em;margin-right:0.05em;">
  <span className="pstrut" style="height:2.7em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size6,size3,mtight">
  <span className="mord,mtight">
  
  2
  
  </span>
  </span>
  </span>
  </span>
  
  <span className="vlist-s">
  
  ​
  
  </span>
  </span>
  
  <span className="vlist-r">
  <span className="vlist" style="height:0.2441em;">
  <span>
  
  
  
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  
  <span className="mspace" style="margin-right:0.1667em;">
  
  
  
  </span>
  
  <span className="mord">
  
  4
  
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
  
  2
  
  </span>
  </span>
  </span>
  </span>
  
  位 byte offset。所以最低 2 位是：`Byte Offset`。它表示 block 内部的第几个 byte。
  - cache 有 4 个 cache block，而且是 direct-mapped，所以：`set 数 = cache block 数 = 4`需要：<span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <msub>
  <mrow>
  <mi>
  
  log
  
  </mi>
  
  <mo>
  
  ⁡
  
  </mo>
  </mrow>
  
  <mn>
  
  2
  
  </mn>
  </msub>
  
  <mn>
  
  4
  
  </mn>
  
  <mo>
  
  =
  
  </mo>
  
  <mn>
  
  2
  
  </mn>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  \log_2 4=2
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:0.9386em;vertical-align:-0.2441em;">
  
  
  
  </span>
  
  <span className="mop">
  <span className="mop">
  
  lo<span style="margin-right:0.0139em;">
  
  g
  
  </span>
  </span>
  
  <span className="msupsub">
  <span className="vlist-t,vlist-t2">
  <span className="vlist-r">
  <span className="vlist" style="height:0.207em;">
  <span style="top:-2.4559em;margin-right:0.05em;">
  <span className="pstrut" style="height:2.7em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size6,size3,mtight">
  <span className="mord,mtight">
  
  2
  
  </span>
  </span>
  </span>
  </span>
  
  <span className="vlist-s">
  
  ​
  
  </span>
  </span>
  
  <span className="vlist-r">
  <span className="vlist" style="height:0.2441em;">
  <span>
  
  
  
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  
  <span className="mspace" style="margin-right:0.1667em;">
  
  
  
  </span>
  
  <span className="mord">
  
  4
  
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
  
  2
  
  </span>
  </span>
  </span>
  </span>
  
  位 index。所以中间 2 位是：`Index`它表示这个内存 block 应该放到 cache 的哪一行。
  - 总地址只有 6 位：`[ Tag | Index | Byte Offset ]`, offset 用 2 位，index 用 2 位，剩下：<span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mn>
  
  6
  
  </mn>
  
  <mo>
  
  −
  
  </mo>
  
  <mn>
  
  2
  
  </mn>
  
  <mo>
  
  −
  
  </mo>
  
  <mn>
  
  2
  
  </mn>
  
  <mo>
  
  =
  
  </mo>
  
  <mn>
  
  2
  
  </mn>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  6-2-2=2
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:0.7278em;vertical-align:-0.0833em;">
  
  
  
  </span>
  
  <span className="mord">
  
  6
  
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
  <span className="strut" style="height:0.7278em;vertical-align:-0.0833em;">
  
  
  
  </span>
  
  <span className="mord">
  
  2
  
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
  
  2
  
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
  
  2
  
  </span>
  </span>
  </span>
  </span>
  
  位就是 tag。
  所以地址格式是：`[ Tag: 2 bits | Index: 2 bits | Byte Offset: 2 bits ]`
2. 内存映射分析
  1. 主存一共有：16个 memory block，cache 只有 4 个 cache block，那么会出现**4 个 memory block 会竞争同一个 cache block的现象**，如下所示的映射关系```c
memory block 0  -> cache block 0
memory block 1  -> cache block 1
memory block 2  -> cache block 2
memory block 3  -> cache block 3

memory block 4  -> cache block 0
memory block 5  -> cache block 1
memory block 6  -> cache block 2
memory block 7  -> cache block 3

memory block 8  -> cache block 0
memory block 9  -> cache block 1
...
```

因此会出现

```c
cache block 0 可能装 memory block 0, 4, 8, 12
cache block 1 可能装 memory block 1, 5, 9, 13
cache block 2 可能装 memory block 2, 6, 10, 14
cache block 3 可能装 memory block 3, 7, 11, 15
```

所以这个时候需要Tag来进行区分，到底是这个cache block存储的是哪个 memory block

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-54.webp)

1. 这一页是在把 **主存 block 怎么映射到 cache line** 画出来。

  1. 主存有很多 block，cache 只有 4 行，每个主存 block 根据 index 映射到 cache 的某一行

---

举个具体地址——地址 `0b010110`：

```text
01 | 01 | 10
Tag | Index | Offset
```

含义是：

```text
去 cache block 1 找
检查 tag 是不是 01
如果是，并且 valid = 1，就是 hit
然后取这个 block 里的第 2 个 byte
```

---

再看地址 `0b000110`：

```text
00 | 01 | 10
Tag | Index | Offset
```

它的 index 也是 `01`，所以它也去 cache block 1。但是 tag 不同

所以它们虽然都映射到 cache block 1，但不是同一个 memory block。

这就是 direct-mapped cache 可能发生 conflict miss 的原因：

```text
两个不同 memory block
映射到同一个 cache block
不能同时存在
会互相替换
```

##### Multiword-Block Direct-Mapped Cache｜多字块直接映射缓存

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-55.webp)

这一页开始引入新的东西：**一个 cache block 里不只放 1 个 word，而是放多个 word。**

比如一个 block 有 4 个 word：

```text
block = word0 | word1 | word2 | word3
```

那么 cache line 就变成：

```text
Valid | Tag | word0 | word1 | word2 | word3
```

这个时候地址拆分要多一部分：

```text
Tag | Index | Block Offset
```

如果从 byte-address 层面看，完整应该是：

```text
Tag | Index | Word Offset | Byte Offset
```

例如 1 个 block 有 4 个 word，每个 word 是 4 Byte，那么一个 block 是：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mn>

4

</mn>

<mo>

×

</mo>

<mn>

4

</mn>

<mi>

B

</mi>

<mo>

=

</mo>

<mn>

16

</mn>

<mi>

B

</mi>
</mrow>

<annotation encoding="application/x-tex">

4\times 4B=16B

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.7278em;vertical-align:-0.0833em;">



</span>

<span className="mord">

4

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
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord">

4

</span>

<span className="mord,mathnormal" style="margin-right:0.0502em;">

B

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

16

</span>

<span className="mord,mathnormal" style="margin-right:0.0502em;">

B

</span>
</span>
</span>
</span>
</span>

则 block offset 总共需要：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mrow>
<mi>

log

</mi>

<mo>

⁡

</mo>
</mrow>

<mn>

2

</mn>
</msub>

<mn>

16

</mn>

<mo>

=

</mo>

<mn>

4

</mn>
</mrow>

<annotation encoding="application/x-tex">

\log_2 16=4

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9386em;vertical-align:-0.2441em;">



</span>

<span className="mop">
<span className="mop">

lo<span style="margin-right:0.0139em;">

g

</span>
</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.207em;">
<span style="top:-2.4559em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">

2

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.2441em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord">

16

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

4

</span>
</span>
</span>
</span>

位。

其中：高 2 位：选 block 里的第几个 word；低 2 位：选 word 里的第几个 byte

##### Ping Pong Cache

<mark>

**Direct-mapped cache 在某些访问模式下会出现“你踢我、我踢你”的反复替换。**

</mark>

<mark>

这叫

</mark>

 <mark>

**ping-pong**

</mark>

 <mark>

或者

</mark>

 <mark>

**thrashing**

</mark>

<mark>

。

</mark>



假设有两个字符串 / 数组：

```text
string A
string B
```

程序交替访问：

```text
A[0], B[0], A[1], B[1], A[2], B[2], ...
```

如果 A 和 B 的地址刚好映射到同一个 cache line，那么：

```text
访问 A：把 A 的 block 装入 cache
访问 B：B 的 block 映射到同一行，把 A 踢掉
访问 A：A 又 miss，把 B 踢掉
访问 B：B 又 miss，把 A 踢掉
```

这就是 ping-pong。

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 49.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-56.webp" />
      </p>
    </td>
    
    
      <td style="width: 50.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-57.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

77页(右图)就是把第 76 页（左图）的最坏情况画出来。

你可以把图里的两排理解成两个字符串 / 两个数组：

```text
上面一排：字符串 A 的连续 block
下面一排：字符串 B 的连续 block
```

红色斜线表示它们映射到 cache 的同一位置。

在 direct-mapped cache 里，一个 index 只有一个位置，所以如果 A 的某个 block 和 B 的某个 block 有相同 index，它们就不能同时待在 cache 里。

于是访问序列如果是：

```text
A block 0
B block 0
A block 0
B block 0
```

就会出现：

```text
A miss，装入 A
B miss，踢掉 A
A miss，踢掉 B
B miss，踢掉 A
```

结果就是：

```text
明明 cache 有空间，但是因为映射位置固定，两个 block 反复冲突
```

<mark>

这类 miss 叫：conflict miss，也就是

</mark>

 <mark>

**冲突缺失**

</mark>

<mark>

。

</mark>



- <mark>

direct-mapped 的缺点：

</mark>

<mark>

**每个主存 block 只有唯一位置可放，所以容易发生冲突。**

</mark>

---

#### 2-Way Set Associative Cache｜2 路组相联缓存

这一页就是为了解决前面的 ping-pong 问题，引入 **2-way set associative cache**。

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 51.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-58.webp" />
      </p>
    </td>
    
    
      <td style="width: 48.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-59.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

Cache 总容量还是 4 个 word / block，但组织方式变了。

原来 direct-mapped 是：`4 sets × 1 way per set`

现在 2-way set associative 是：`2 sets × 2 ways per set`

也就是：

- set 0：有 2 个位置
- set 1：有 2 个位置

地址还是拆成：`Tag | Index | Offset`

但因为现在只有 2 个 set，所以 index 只需要：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mrow>
<mi>

log

</mi>

<mo>

⁡

</mo>
</mrow>

<mn>

2

</mn>
</msub>

<mn>

2

</mn>

<mo>

=

</mo>

<mn>

1

</mn>
</mrow>

<annotation encoding="application/x-tex">

\log_2 2=1

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9386em;vertical-align:-0.2441em;">



</span>

<span className="mop">
<span className="mop">

lo<span style="margin-right:0.0139em;">

g

</span>
</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.207em;">
<span style="top:-2.4559em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">

2

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.2441em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord">

2

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

1

</span>
</span>
</span>
</span>

位。

相比 direct-mapped 的 4 个 set：

```text
direct-mapped：4 sets，需要 2 位 index
2-way set associative：2 sets，需要 1 位 index
```

index 位变少了，tag 位就变多了。

这也是图里 tag 看起来更长的原因。

---

访问流程变成：

```text
CPU 发出地址
       ↓
用 index 选中一个 set
       ↓
这个 set 里面有 2 个 way
       ↓
同时比较两个 way 的 tag
       ↓
任意一个 way valid=1 且 tag 匹配，就是 hit
```

也就是：

```text
Direct-mapped：index 选中唯一一行
2-way set associative：index 选中一个 set，set 里有两个候选位置
```

这样就可以缓解 ping-pong。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-60.webp)

比如 A 和 B 映射到同一个 set：

```text
A block -> set 0
B block -> set 0
```

在 direct-mapped 里，set 0 只有 1 个位置，所以互相踢。

但在 2-way 里，set 0 有 2 个位置：

```text
A block 放 way 0
B block 放 way 1
```

这样它们可以同时存在，后续访问就可能 hit。

#### Four-Way Set-Associative Cache｜四路组相联缓存

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-61.webp)

这一页是在讲 **4-way set associative cache 的硬件结构**。

图中**每个 set 里有 4 个位置（4way）可以放 block。**

```text
2^8 = 256 个 set
每个 set 有 4 个 way
每个 way 里放 1 个 block
```

地址被拆成：

```text
Tag | Index | Byte Offset
```

其中：

```text
Index = 8 bits   用来选择 256 个 set 中的某一个
Tag   = 22 bits  用来和该 set 内 4 个 way 的 tag 比较
Byte Offset = 2 bits  用来选 word 内的 byte
```

访问流程是：

1. 用 Index 选中一个 set
2. 同时读出这个 set 中 4 个 way 的 tag 和 data
3. 用 4 个比较器并行比较 tag
4. 哪个 way 的 tag 匹配且 valid=1，就从哪个 way 取数据
5. 最后通过 4-to-1 mux 选出正确数据

所以 4-way 的核心是：

> **一个内存 block 不是只能放一个位置，而是可以放在对应 set 里的 4 个 way 中任意一个位置。**

<mark>

这样比 direct-mapped 更不容易冲突，但硬件更复杂，因为需要 4 个 tag comparator 和一个 4 选 1 的数据选择器。

</mark>



#### Fully Associative Cache｜完全关联缓存

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-62.webp)

全关联的意思是：**一个主存 block 可以放到 cache 的任何一个位置。**<mark>

所以它没有 index 字段。

</mark>



地址只需要拆成：

```text
Tag | Block Offset
```

访问时：

1. CPU 给出地址
2. 取地址里的 Tag
3. 同时和 cache 中所有 line 的 tag 比较
4. 只要任意一个 line 匹配，并且 valid=1，就是 hit
5. 再用 block offset 选 block 内的 word / byte

所以全关联 cache 的特点是：

```text
优点：最灵活，冲突 miss 最少
缺点：每个 cache block 都要一个比较器，硬件代价很高
```

---

#### Alternative Cache Organizations｜可选缓存结构 （Tag：总结）

这一页是总结三种 cache organization。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-63.webp)

##### Fully Associative

```text
任意 memory block 可以放到 cache 任意位置
没有 index 字段
每个 cache block 都需要一个 comparator
```

极端灵活，但搜索代价大。

##### Direct Mapped

```text
任意 memory block 只能放到唯一一个 cache 位置
只有 1 个 comparator
set 数 = block 数
```

硬件最简单，速度快，但 conflict miss 多。

##### N-way Set Associative

```text
memory block 先由 index 决定进入哪个 set
然后可以放在这个 set 内的任意一个 way
```

公式是：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi mathvariant="normal">

#

</mi>

<mi>

s

</mi>

<mi>

e

</mi>

<mi>

t

</mi>

<mi>

s

</mi>

<mo>

=

</mo>

<mfrac>
<mrow>
<mi mathvariant="normal">

#

</mi>

<mi>

b

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

s

</mi>
</mrow>

<mi>

N

</mi>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

\#sets=\frac{\#blocks}{N}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord">

#

</span>

<span className="mord,mathnormal">

se

</span>

<span className="mord,mathnormal">

t

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
<span className="strut" style="height:1.2772em;vertical-align:-0.345em;">



</span>

<span className="mord">
<span className="mopen,nulldelimiter">



</span>

<span className="mfrac">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.9322em;">
<span style="top:-2.655em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.109em;">

N

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

<span style="top:-3.4461em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">

#

</span>

<span className="mord,mathnormal,mtight">

b

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal,mtight">

oc

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0315em;">

k

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



N-way 需要 N 个 comparator。

它是 direct-mapped 和 fully associative 的折中。课件也写了：全关联没有索引字段，直接映射只有 1 个比较器，N 路组相联有 N 个比较器，并且 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi mathvariant="normal">

#

</mi>

<mi>

s

</mi>

<mi>

e

</mi>

<mi>

t

</mi>

<mi>

s

</mi>

<mo>

=

</mo>

<mfrac>
<mrow>
<mi mathvariant="normal">

#

</mi>

<mi>

b

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

s

</mi>
</mrow>

<mi>

N

</mi>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

\#sets=\frac{\#blocks}{N}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord">

#

</span>

<span className="mord,mathnormal">

se

</span>

<span className="mord,mathnormal">

t

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
<span className="strut" style="height:1.2772em;vertical-align:-0.345em;">



</span>

<span className="mord">
<span className="mopen,nulldelimiter">



</span>

<span className="mfrac">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.9322em;">
<span style="top:-2.655em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.109em;">

N

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

<span style="top:-3.4461em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">

#

</span>

<span className="mord,mathnormal,mtight">

b

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal,mtight">

oc

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0315em;">

k

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

。

#### Range of Set-Associative Caches｜组相联缓存的范围

这一页讲的是：**在 cache 总容量和 block size 固定时，associativity（就是way） 增大，会发生什么。**

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 49.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-64.webp" />
      </p>
    </td>
    
    
      <td style="width: 50.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-65.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

核心关系是：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mtext>

总 block 数

</mtext>

<mo>

=

</mo>

<mtext>

set 数

</mtext>

<mo>

×

</mo>

<mtext>

way 数

</mtext>
</mrow>

<annotation encoding="application/x-tex">

\text{总 block 数}=\text{set 数}\times \text{way 数}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,text">
<span className="mord,cjk_fallback">

总

</span>

<span className="mord">

block

</span>

<span className="mord,cjk_fallback">

数

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
<span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">



</span>

<span className="mord,text">
<span className="mord">

set

</span>

<span className="mord,cjk_fallback">

数

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
<span className="strut" style="height:0.8778em;vertical-align:-0.1944em;">



</span>

<span className="mord,text">
<span className="mord">

way

</span>

<span className="mord,cjk_fallback">

数

</span>
</span>
</span>
</span>
</span>

，如果总 block 数不变，way 数增大，那么 set 数就减少。

例如：

```text
Direct mapped: 8 sets × 1 way
2-way:         4 sets × 2 ways
4-way:         2 sets × 4 ways
Fully assoc:   1 set  × 8 ways
```

所以 associativity 每翻倍：

```text
way 数 ×2
set 数 ÷2
index 位数减少 1 位
tag 位数增加 1 位
comparator 数量增加
```

> 为什么 tag 会增加？
> 
> 因为地址格式是：
> 
> <span className="katex-display">
> <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
> <semantics>
> <mrow>
> <mtext>
> 
> Address
> 
> </mtext>
> 
> <mo>
> 
> =
> 
> </mo>
> 
> <mtext>
> 
> Tag
> 
> </mtext>
> 
> <mi mathvariant="normal">
> 
> ∣
> 
> </mi>
> 
> <mtext>
> 
> Index
> 
> </mtext>
> 
> <mi mathvariant="normal">
> 
> ∣
> 
> </mi>
> 
> <mtext>
> 
> Offset
> 
> </mtext>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> \text{Address}=\text{Tag}\ |\ \text{Index}\ |\ \text{Offset}
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:0.6944em;">
> 
> 
> 
> </span>
> 
> <span className="mord,text">
> <span className="mord">
> 
> Address
> 
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
> <span className="strut" style="height:1em;vertical-align:-0.25em;">
> 
> 
> 
> </span>
> 
> <span className="mord,text">
> <span className="mord">
> 
> Tag
> 
> </span>
> </span>
> 
> <span className="mspace">
> 
> 
> 
> </span>
> 
> <span className="mord">
> 
> ∣
> 
> </span>
> 
> <span className="mspace">
> 
> 
> 
> </span>
> 
> <span className="mord,text">
> <span className="mord">
> 
> Index
> 
> </span>
> </span>
> 
> <span className="mspace">
> 
> 
> 
> </span>
> 
> <span className="mord">
> 
> ∣
> 
> </span>
> 
> <span className="mspace">
> 
> 
> 
> </span>
> 
> <span className="mord,text">
> <span className="mord">
> 
> Offset
> 
> </span>
> </span>
> </span>
> </span>
> </span>
> </span>
> 
> 地址总位数固定，offset 固定。
> 
> 如果 set 数减少，那么 index bits 变少，剩下给 tag 的位数就变多。

---

#### Total Cache Capacity｜总 Cache 容量公式

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-66.webp)

这一页给出最重要的统一公式：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

C

</mi>

<mo>

=

</mo>

<mi>

N

</mi>

<mo>

×

</mo>

<mi>

S

</mi>

<mo>

×

</mo>

<mi>

B

</mi>
</mrow>

<annotation encoding="application/x-tex">

C=N\times S\times B

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

<span className="mord,mathnormal" style="margin-right:0.109em;">

N

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

<span className="mord,mathnormal" style="margin-right:0.0576em;">

S

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
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0502em;">

B

</span>
</span>
</span>
</span>
</span>

其中：

- C = cache data capacity，单位通常是 Byte
- N = associativity，也就是每个 set 有几个 way
- S = number of sets，set 数
- B = block size，每个 block 有多少 Byte

即 **容量 = 每组 block 数 × 组数 × 每个 block 的字节数**

地址位数公式是：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mtext>

address size

</mtext>

<mo>

=

</mo>

<mtext>

tag size

</mtext>

<mo>

+

</mo>

<mtext>

index size

</mtext>

<mo>

+

</mo>

<mtext>

offset size

</mtext>
</mrow>

<annotation encoding="application/x-tex">

\text{address size}=\text{tag size}+\text{index size}+\text{offset size}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,text">
<span className="mord">

address size

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
<span className="strut" style="height:0.8623em;vertical-align:-0.1944em;">



</span>

<span className="mord,text">
<span className="mord">

tag size

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
<span className="strut" style="height:0.7778em;vertical-align:-0.0833em;">



</span>

<span className="mord,text">
<span className="mord">

index size

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
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,text">
<span className="mord">

offset size

</span>
</span>
</span>
</span>
</span>
</span>

又因为：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mtext>

index size

</mtext>

<mo>

=

</mo>

<msub>
<mrow>
<mi>

log

</mi>

<mo>

⁡

</mo>
</mrow>

<mn>

2

</mn>
</msub>

<mi>

S

</mi>
</mrow>

<annotation encoding="application/x-tex">

\text{index size}=\log_2 S

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,text">
<span className="mord">

index size

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
<span className="strut" style="height:0.9386em;vertical-align:-0.2441em;">



</span>

<span className="mop">
<span className="mop">

lo<span style="margin-right:0.0139em;">

g

</span>
</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.207em;">
<span style="top:-2.4559em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">

2

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.2441em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0576em;">

S

</span>
</span>
</span>
</span>
</span>

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mtext>

offset size

</mtext>

<mo>

=

</mo>

<msub>
<mrow>
<mi>

log

</mi>

<mo>

⁡

</mo>
</mrow>

<mn>

2

</mn>
</msub>

<mi>

B

</mi>
</mrow>

<annotation encoding="application/x-tex">

\text{offset size}=\log_2 B

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,text">
<span className="mord">

offset size

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
<span className="strut" style="height:0.9386em;vertical-align:-0.2441em;">



</span>

<span className="mop">
<span className="mop">

lo<span style="margin-right:0.0139em;">

g

</span>
</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.207em;">
<span style="top:-2.4559em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">

2

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.2441em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0502em;">

B

</span>
</span>
</span>
</span>
</span>

所以：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mtext>

tag size

</mtext>

<mo>

=

</mo>

<mtext>

address size

</mtext>

<mo>

−

</mo>

<msub>
<mrow>
<mi>

log

</mi>

<mo>

⁡

</mo>
</mrow>

<mn>

2

</mn>
</msub>

<mi>

S

</mi>

<mo>

−

</mo>

<msub>
<mrow>
<mi>

log

</mi>

<mo>

⁡

</mo>
</mrow>

<mn>

2

</mn>
</msub>

<mi>

B

</mi>
</mrow>

<annotation encoding="application/x-tex">

\text{tag size}=\text{address size}-\log_2 S-\log_2 B

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8623em;vertical-align:-0.1944em;">



</span>

<span className="mord,text">
<span className="mord">

tag size

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
<span className="strut" style="height:0.7778em;vertical-align:-0.0833em;">



</span>

<span className="mord,text">
<span className="mord">

address size

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
<span className="strut" style="height:0.9386em;vertical-align:-0.2441em;">



</span>

<span className="mop">
<span className="mop">

lo<span style="margin-right:0.0139em;">

g

</span>
</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.207em;">
<span style="top:-2.4559em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">

2

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.2441em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0576em;">

S

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
<span className="strut" style="height:0.9386em;vertical-align:-0.2441em;">



</span>

<span className="mop">
<span className="mop">

lo<span style="margin-right:0.0139em;">

g

</span>
</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.207em;">
<span style="top:-2.4559em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">

2

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.2441em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0502em;">

B

</span>
</span>
</span>
</span>
</span>

1. 如果 associativity 翻倍，且总容量和 block size 不变，其他变量应该如何变化？

  1. <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mi>
  
  N
  
  </mi>
  
  <mo>
  
  ×
  
  </mo>
  
  <mn>
  
  2
  
  </mn>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  N\times 2
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">
  
  
  
  </span>
  
  <span className="mord,mathnormal" style="margin-right:0.109em;">
  
  N
  
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
  
  2
  
  </span>
  </span>
  </span>
  </span>
  
  为了让 <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mi>
  
  C
  
  </mi>
  
  <mo>
  
  =
  
  </mo>
  
  <mi>
  
  N
  
  </mi>
  
  <mo>
  
  ×
  
  </mo>
  
  <mi>
  
  S
  
  </mi>
  
  <mo>
  
  ×
  
  </mo>
  
  <mi>
  
  B
  
  </mi>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  C=N\times S\times B
  
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
  
  <span className="mord,mathnormal" style="margin-right:0.109em;">
  
  N
  
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
  
  <span className="mord,mathnormal" style="margin-right:0.0576em;">
  
  S
  
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
  <span className="strut" style="height:0.6833em;">
  
  
  
  </span>
  
  <span className="mord,mathnormal" style="margin-right:0.0502em;">
  
  B
  
  </span>
  </span>
  </span>
  </span>
  
   不变，<span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mi>
  
  S
  
  </mi>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  S
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:0.6833em;">
  
  
  
  </span>
  
  <span className="mord,mathnormal" style="margin-right:0.0576em;">
  
  S
  
  </span>
  </span>
  </span>
  </span>
  
   必须减半。
  2. 所以：
  
    1. set 数减半
    2. index bits 减少 1 位
    3. tag bits 增加 1 位
    4. comparator 数翻倍
2. 如果 set 数翻倍，且总容量和 block size 不变，其他变量应该如何变化？

  1. <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mi>
  
  S
  
  </mi>
  
  <mo>
  
  ×
  
  </mo>
  
  <mn>
  
  2
  
  </mn>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  S\times 2
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">
  
  
  
  </span>
  
  <span className="mord,mathnormal" style="margin-right:0.0576em;">
  
  S
  
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
  
  2
  
  </span>
  </span>
  </span>
  </span>
  
  则 <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mi>
  
  N
  
  </mi>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  N
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:0.6833em;">
  
  
  
  </span>
  
  <span className="mord,mathnormal" style="margin-right:0.109em;">
  
  N
  
  </span>
  </span>
  </span>
  </span>
  
   必须减半。
  2. 所以：
  
    1. associativity 减半
    2. index bits 增加 1 位
    3. tag bits 减少 1 位
    4. comparator 数减少

---

#### 练习1——P87页

固定总容量时，如果 ways 数翻倍，哪个说法是 false？

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-67.webp)

```text
A: The number of sets is halved
正确，set 数减半

B: The tag width decreases
错误，tag 宽度不是减少，而是增加

C: The block size stays the same
正确，block size 没变

D:The block size is halved
错误，block size是不变的

E: The set index decreases
正确，set 数减半，所以 index bits 减少 1 位
```

#### 练习 2——P88 页

对于 S sets, N ways, B blocks，哪些说法成立？

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-68.webp)

全对 这个没啥好解释的，基本慨念了

---

#### Cache 示例，计算 tag size ｜ 习题3 P90

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-69.webp)

题目给：

```text
cache capacity = 2MB
line size = 64B
physical address = 52 bits
```

先算 cache line 数：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mn>

2

</mn>

<mtext>

MB

</mtext>

<mo>

=

</mo>

<msup>
<mn>

2

</mn>

<mn>

21

</mn>
</msup>

<mtext>

B

</mtext>
</mrow>

<annotation encoding="application/x-tex">

2\text{MB}=2^{21}\text{B}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord">

2

</span>

<span className="mord,text">
<span className="mord">

MB

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
<span className="strut" style="height:0.8641em;">



</span>

<span className="mord">
<span className="mord">

2

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
<span className="mord,mtight">

21

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

<span className="mord,text">
<span className="mord">

B

</span>
</span>
</span>
</span>
</span>
</span>

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mn>

64

</mn>

<mtext>

B

</mtext>

<mo>

=

</mo>

<msup>
<mn>

2

</mn>

<mn>

6

</mn>
</msup>

<mtext>

B

</mtext>
</mrow>

<annotation encoding="application/x-tex">

64\text{B}=2^6\text{B}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord">

64

</span>

<span className="mord,text">
<span className="mord">

B

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
<span className="strut" style="height:0.8641em;">



</span>

<span className="mord">
<span className="mord">

2

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

6

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

<span className="mord,text">
<span className="mord">

B

</span>
</span>
</span>
</span>
</span>
</span>

所以：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi mathvariant="normal">

#

</mi>

<mi>

l

</mi>

<mi>

i

</mi>

<mi>

n

</mi>

<mi>

e

</mi>

<mi>

s

</mi>

<mo>

=

</mo>

<mfrac>
<msup>
<mn>

2

</mn>

<mn>

21

</mn>
</msup>

<msup>
<mn>

2

</mn>

<mn>

6

</mn>
</msup>
</mfrac>

<mo>

=

</mo>

<msup>
<mn>

2

</mn>

<mn>

15

</mn>
</msup>

<mo>

=

</mo>

<mn>

32

</mn>

<mi>

K

</mi>
</mrow>

<annotation encoding="application/x-tex">

\#lines=\frac{2^{21}}{2^6}=2^{15}=32K

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord">

#

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

in

</span>

<span className="mord,mathnormal">

es

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
<span className="strut" style="height:2.1771em;vertical-align:-0.686em;">



</span>

<span className="mord">
<span className="mopen,nulldelimiter">



</span>

<span className="mfrac">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:1.4911em;">
<span style="top:-2.314em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord">

2

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
<span className="mord">
<span className="mord">

2

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
<span className="mord,mtight">

21

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
<span className="strut" style="height:0.8641em;">



</span>

<span className="mord">
<span className="mord">

2

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
<span className="mord,mtight">

15

</span>
</span>
</span>
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

32

</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

K

</span>
</span>
</span>
</span>
</span>

---

##### Direct-mapped

direct-mapped 中：

```text
set 数 = line 数 = 2^15
```

所以：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mtext>

index bits

</mtext>

<mo>

=

</mo>

<mn>

15

</mn>
</mrow>

<annotation encoding="application/x-tex">

\text{index bits}=15

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,text">
<span className="mord">

index bits

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

15

</span>
</span>
</span>
</span>
</span>

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mtext>

offset bits

</mtext>

<mo>

=

</mo>

<msub>
<mrow>
<mi>

log

</mi>

<mo>

⁡

</mo>
</mrow>

<mn>

2

</mn>
</msub>

<mn>

64

</mn>

<mo>

=

</mo>

<mn>

6

</mn>
</mrow>

<annotation encoding="application/x-tex">

\text{offset bits}=\log_2 64=6

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,text">
<span className="mord">

offset bits

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
<span className="strut" style="height:0.9386em;vertical-align:-0.2441em;">



</span>

<span className="mop">
<span className="mop">

lo<span style="margin-right:0.0139em;">

g

</span>
</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.207em;">
<span style="top:-2.4559em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">

2

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.2441em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord">

64

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
</span>
</span>
</span>
</span>

于是：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mtext>

tag bits

</mtext>

<mo>

=

</mo>

<mn>

52

</mn>

<mo>

−

</mo>

<mn>

15

</mn>

<mo>

−

</mo>

<mn>

6

</mn>

<mo>

=

</mo>

<mn>

31

</mn>
</mrow>

<annotation encoding="application/x-tex">

\text{tag bits}=52-15-6=31

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,text">
<span className="mord">

tag bits

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
<span className="strut" style="height:0.7278em;vertical-align:-0.0833em;">



</span>

<span className="mord">

52

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
<span className="strut" style="height:0.7278em;vertical-align:-0.0833em;">



</span>

<span className="mord">

15

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

6

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

31

</span>
</span>
</span>
</span>
</span>

答案：

```text
tag size = 31 bits
```

---

##### 16-way set associative

总 line 数还是 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msup>
<mn>

2

</mn>

<mn>

15

</mn>
</msup>
</mrow>

<annotation encoding="application/x-tex">

2^{15}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8141em;">



</span>

<span className="mord">
<span className="mord">

2

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
<span className="mord,mtight">

15

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
</span>

，但每个 set 有 16 ways：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mn>

16

</mn>

<mo>

=

</mo>

<msup>
<mn>

2

</mn>

<mn>

4

</mn>
</msup>
</mrow>

<annotation encoding="application/x-tex">

16=2^4

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6444em;">



</span>

<span className="mord">

16

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
<span className="strut" style="height:0.8641em;">



</span>

<span className="mord">
<span className="mord">

2

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

4

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
</span>

所以：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi mathvariant="normal">

#

</mi>

<mi>

s

</mi>

<mi>

e

</mi>

<mi>

t

</mi>

<mi>

s

</mi>

<mo>

=

</mo>

<mfrac>
<msup>
<mn>

2

</mn>

<mn>

15

</mn>
</msup>

<msup>
<mn>

2

</mn>

<mn>

4

</mn>
</msup>
</mfrac>

<mo>

=

</mo>

<msup>
<mn>

2

</mn>

<mn>

11

</mn>
</msup>

<mo>

=

</mo>

<mn>

2

</mn>

<mi>

K

</mi>
</mrow>

<annotation encoding="application/x-tex">

\#sets=\frac{2^{15}}{2^4}=2^{11}=2K

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord">

#

</span>

<span className="mord,mathnormal">

se

</span>

<span className="mord,mathnormal">

t

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
<span className="strut" style="height:2.1771em;vertical-align:-0.686em;">



</span>

<span className="mord">
<span className="mopen,nulldelimiter">



</span>

<span className="mfrac">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:1.4911em;">
<span style="top:-2.314em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord">

2

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

4

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
<span className="mord">
<span className="mord">

2

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
<span className="mord,mtight">

15

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
<span className="strut" style="height:0.8641em;">



</span>

<span className="mord">
<span className="mord">

2

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
<span className="mord,mtight">

11

</span>
</span>
</span>
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

2

</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

K

</span>
</span>
</span>
</span>
</span>

因此：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mtext>

index bits

</mtext>

<mo>

=

</mo>

<mn>

11

</mn>
</mrow>

<annotation encoding="application/x-tex">

\text{index bits}=11

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,text">
<span className="mord">

index bits

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

11

</span>
</span>
</span>
</span>
</span>

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mtext>

offset bits

</mtext>

<mo>

=

</mo>

<mn>

6

</mn>
</mrow>

<annotation encoding="application/x-tex">

\text{offset bits}=6

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,text">
<span className="mord">

offset bits

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
</span>
</span>
</span>
</span>

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mtext>

tag bits

</mtext>

<mo>

=

</mo>

<mn>

52

</mn>

<mo>

−

</mo>

<mn>

11

</mn>

<mo>

−

</mo>

<mn>

6

</mn>

<mo>

=

</mo>

<mn>

35

</mn>
</mrow>

<annotation encoding="application/x-tex">

\text{tag bits}=52-11-6=35

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,text">
<span className="mord">

tag bits

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
<span className="strut" style="height:0.7278em;vertical-align:-0.0833em;">



</span>

<span className="mord">

52

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
<span className="strut" style="height:0.7278em;vertical-align:-0.0833em;">



</span>

<span className="mord">

11

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

6

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

35

</span>
</span>
</span>
</span>
</span>

答案：

```text
tag size = 35 bits
```

---

##### Fully associative

fully associative 只有 1 个 set，所以没有 index：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mtext>

index bits

</mtext>

<mo>

=

</mo>

<mn>

0

</mn>
</mrow>

<annotation encoding="application/x-tex">

\text{index bits}=0

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,text">
<span className="mord">

index bits

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

0

</span>
</span>
</span>
</span>
</span>

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mtext>

offset bits

</mtext>

<mo>

=

</mo>

<mn>

6

</mn>
</mrow>

<annotation encoding="application/x-tex">

\text{offset bits}=6

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,text">
<span className="mord">

offset bits

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
</span>
</span>
</span>
</span>

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mtext>

tag bits

</mtext>

<mo>

=

</mo>

<mn>

52

</mn>

<mo>

−

</mo>

<mn>

0

</mn>

<mo>

−

</mo>

<mn>

6

</mn>

<mo>

=

</mo>

<mn>

46

</mn>
</mrow>

<annotation encoding="application/x-tex">

\text{tag bits}=52-0-6=46

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,text">
<span className="mord">

tag bits

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
<span className="strut" style="height:0.7278em;vertical-align:-0.0833em;">



</span>

<span className="mord">

52

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
<span className="strut" style="height:0.7278em;vertical-align:-0.0833em;">



</span>

<span className="mord">

0

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

6

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

46

</span>
</span>
</span>
</span>
</span>

答案：

```text
tag size = 46 bits
```

---

#### Block Size and Spatial Locality｜块大小和空间局部性

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-70.webp)

这一页开始进入另一个参数：**block size**。一个 block 里面到底放多少数据？

图里一个 block 包含：`Word0 | Word1 | Word2 | Word3`,  也就是一个 cache line 里有多个 word，一整块共用一个 tag。

所以 cache line 可以看成：`Tag | Word0 | Word1 | Word2 | Word3`

地址会被分成：

```text
block address | offset
```

其中：`block address 就是 Tag 与 Index拼接而成`;

如果 block size 是 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msup>
<mn>

2

</mn>

<mi>

b

</mi>
</msup>
</mrow>

<annotation encoding="application/x-tex">

2^b

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8491em;">



</span>

<span className="mord">
<span className="mord">

2

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8491em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

b

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

 Byte，那么 offset 需要 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

b

</mi>
</mrow>

<annotation encoding="application/x-tex">

b

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,mathnormal">

b

</span>
</span>
</span>
</span>

 位。

如果是 4-word block，并且 1 word = 4 Byte，那么总 block size 是：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mn>

4

</mn>

<mo>

×

</mo>

<mn>

4

</mn>

<mo>

=

</mo>

<mn>

16

</mn>

<mi>

B

</mi>
</mrow>

<annotation encoding="application/x-tex">

4\times 4=16B

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.7278em;vertical-align:-0.0833em;">



</span>

<span className="mord">

4

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

4

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

16

</span>

<span className="mord,mathnormal" style="margin-right:0.0502em;">

B

</span>
</span>
</span>
</span>



如果按 byte address 完整拆分，offset 应该是：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mrow>
<mi>

log

</mi>

<mo>

⁡

</mo>
</mrow>

<mn>

2

</mn>
</msub>

<mn>

16

</mn>

<mo>

=

</mo>

<mn>

4

</mn>
</mrow>

<annotation encoding="application/x-tex">

\log_2 16=4

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9386em;vertical-align:-0.2441em;">



</span>

<span className="mop">
<span className="mop">

lo<span style="margin-right:0.0139em;">

g

</span>
</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.207em;">
<span style="top:-2.4559em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">

2

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.2441em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord">

16

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

4

</span>
</span>
</span>
</span>



这 4 位可以进一步拆成：

```text
word offset：2 bits，用来选 Word0~Word3
byte offset：2 bits，用来选 word 内的 byte
```

<mark>

PPT 图里写

</mark>

 <mark>

`4 字块, b=2`

</mark>

<mark>

，更像是在强调

</mark>

 <mark>

**4 个 word 需要 2 位 word offset**

</mark>

<mark>

。如果严格按 byte address，还要再加 2 位 byte offset。

</mark>



##### 为什么要增大 block size？

因为利用 **spatial locality 空间局部性**。

- 如果一个 block 只装 1 个 word，那么可能每次都要单独取。
- 如果一个 block 装 4 个 word，那么访问 `A[0]` miss 后，会把：`A[0], A[1], A[2], A[3]`一起取进 cache。后面访问 `A[1]~A[3]` 就可能 hit。

**所以大 block 的好处是：**

1. 减少 tag 开销
2. 利用 DRAM 快速突发传输（fast burst transfer）
3. 利用宽总线快速突发传输（fast burst transfer）

##### 增大 block size 的缺点是什么？

总 cache 容量固定时，block 变大意味着 block 数变少。

例如总容量固定为 64B：

```text
block size = 4B   -> 16 个 block
block size = 16B  -> 4 个 block
```

block 数少了，就更容易发生：capacity miss  和  conflict miss

而且如果程序没有空间局部性，大 block 会浪费带宽。

比如你只访问：`A[0]、A[1000]、A[2000]`,   每次都把附近一整块取进来，但后面又不用，这就浪费。

##### 总结

<mark>

**block size 变大可以利用空间局部性，但过大时会减少 cache 中可容纳的 block 数，增加冲突，并浪费带宽。**

</mark>



#### 习题3——P91页

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-71.webp)

1. 64x4=256 Bytes
2. Set = 64/(2way) = 32； each of  2  blocks；2 places;

> **这个 cache 总共有 64 个 cache block。现在把它组织成 2-way set associative，所以它被分成 32 个 set，每个 set 里面有 2 个 cache block。**

1. Set = 64/(4way) = 16； each of  4 blocks；4 places;
2. Set = 64/(8way) = 8； each of  8  blocks；8 places;

这几页的主线是：

**组相联 cache 可以减少 conflict miss，但代价是硬件更复杂；一旦发生 miss，还要决定替换哪一路；最后再引出 cache miss 的 3C 分类。** 这几页对应课件第 92–99 页。

---

#### Costs of Set-Associative Caches ｜ 组关联缓存的开销

这一页在讲：**set-associative cache 虽然能降低冲突，但不是免费的**

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-72.webp)

##### N-way set associative cache 成本问题

Direct-mapped cache 里，一个地址只能去一个 cache line，所以硬件只需要比较一个 tag。

但是 N-way set associative cache 中，一个地址先通过 index 找到某个 set，然后这个 set 里面有 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

N

</mi>
</mrow>

<annotation encoding="application/x-tex">

N

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

N

</span>
</span>
</span>
</span>

 个 way 都可能存放目标 block，所以必须同时比较 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

N

</mi>
</mrow>

<annotation encoding="application/x-tex">

N

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

N

</span>
</span>
</span>
</span>

 个 tag。

因此有几个开销：

1. **需要** <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

N

</mi>
</mrow>

<annotation encoding="application/x-tex">

N

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

N

</span>
</span>
</span>
</span>

 **个比较器**
  1. 每个 way 的 tag 都要和 CPU 地址的 tag 比较，所以硬件面积、功耗、延迟都会增加。
2. **需要 MUX 选择正确的 way**
  1. 即使 tag 比较出了哪个 way 命中，还要用多路选择器从多个 data block 中选出正确数据。这个 MUX 也会增加 hit time。
3. **不能像 direct-mapped 那样简单地“先拿数据”**
  1. Direct-mapped 中，index 唯一确定一行，所以可以先读出这一行的数据，同时比较 tag。
  2. Set-associative 中，一个 set 里有多个候选 block，必须判断哪个 way hit，然后才能确定返回哪个 data。

<mark>

**组相联 cache 降低了 miss rate，尤其是 conflict miss，但会增加 hit time 和硬件成本。**

</mark>



##### Miss 时 Least Recently Used方法的使用

LRU，即 Least Recently Used，表示在**发生 miss 且目标 set 已满时**，替换该 set 中**最久没有被访问的 block**。它利用 temporal locality（时间局限性）：最近访问过的数据短期内更可能再次被访问。

对于 2-way set associative cache，每个 set 只有两个 way，因此<mark>

只需要 1 个 LRU bit

</mark>

 就能记录使用历史。

一种常见实现是让 LRU bit 记录最近使用的 way：

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-73.webp)

- <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

L

</mi>

<mi>

R

</mi>

<mi>

U

</mi>

<mi mathvariant="normal">

_

</mi>

<mi>

b

</mi>

<mi>

i

</mi>

<mi>

t

</mi>

<mo>

=

</mo>

<mn>

0

</mn>
</mrow>

<annotation encoding="application/x-tex">

LRU\_bit = 0

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.0044em;vertical-align:-0.31em;">



</span>

<span className="mord,mathnormal">

L

</span>

<span className="mord,mathnormal" style="margin-right:0.0077em;">

R

</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

U

</span>

<span className="mord" style="margin-right:0.0278em;">

_

</span>

<span className="mord,mathnormal">

bi

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
<span className="strut" style="height:0.6444em;">



</span>

<span className="mord">

0

</span>
</span>
</span>
</span>

：way 0 里面的Block 最近被使用，miss 时替换 way 1 这个block，把way 1踢掉；
- <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

L

</mi>

<mi>

R

</mi>

<mi>

U

</mi>

<mi mathvariant="normal">

_

</mi>

<mi>

b

</mi>

<mi>

i

</mi>

<mi>

t

</mi>

<mo>

=

</mo>

<mn>

1

</mn>
</mrow>

<annotation encoding="application/x-tex">

LRU\_bit = 1

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.0044em;vertical-align:-0.31em;">



</span>

<span className="mord,mathnormal">

L

</span>

<span className="mord,mathnormal" style="margin-right:0.0077em;">

R

</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

U

</span>

<span className="mord" style="margin-right:0.0278em;">

_

</span>

<span className="mord,mathnormal">

bi

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
<span className="strut" style="height:0.6444em;">



</span>

<span className="mord">

1

</span>
</span>
</span>
</span>

：way 1 里面的Block 最近被使用，miss 时替换 way 0这个block，把way 0踢掉。

每次访问某个 way 后，都更新该 set 的 LRU bit，使刚访问过的 way 不会成为下一次优先替换对象。

---

#### Cache Replacement Policies ｜ 缓存替换策略

> **当一个 set 满了，又来了一个新的 block，需要踢掉谁？**

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-74.webp)

> 注意：**替换只发生在 miss 的时候。**如果是 hit，只需要更新访问状态，不会替换 block。

常见替换策略有：

##### Random

随机选一个 cache block 替换。

优点是硬件最简单，不用记录复杂历史。

缺点是不一定聪明，可能刚用过的 block 也被踢掉。

##### FIFO / Round-Robin

FIFO 是 First-In First-Out，也就是先进先出。

谁最早进入 cache，就先被替换。

它不关心这个 block 最近有没有被访问过。

所以可能出现一个 block 虽然刚刚被用过，但因为它最早进入 cache，还是被替换掉。

Round-Robin 可以理解成硬件用一个指针轮流指向下一个 victim。

##### NMRU

NMRU 是 Not Most Recently Used。

意思是：**不要替换最近刚用过的那个，其他都可以考虑。**

它比 LRU 简单，因为它不需要完整记录谁第一老、谁第二老、谁第三老，只需要避免替换 MRU，也就是最近使用过的 block。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-75.webp)

##### LRU 与伪 LRU

LRU 是 Least Recently Used，意思是：替换最久没有被访问的那个 block。

利用 **temporal locality**：如果一个数据最近被访问过，它很可能很快还会被访问；反过来，最久没被访问的数据，将来短期内再次访问的概率较低。

所以 LRU 通常比 Random / FIFO 更符合程序访问规律。<mark>

但是问题是：真正精确的 LRU 在高相联度 cache 中硬件代价很高。

</mark>

比如 2-way set associative cache，LRU 很简单：每个 set 只要 1 bit 就够了——前面P92页PPT有讲过，略。

<mark>

但是如果是 4-way、8-way、16-way，要精确维护完整访问顺序就复杂很多。

</mark>

比如 8-way，你要知道 8 个 way 从最近到最久的完整排序，每次 hit 都要更新排序。

所以实际硬件中常用 <mark>

**Pseudo-LRU**

</mark>

<mark>

，也就是伪 LRU

</mark>

。它不保证完全等价于真正 LRU，但硬件简单很多，效果也通常够好。这页的 replacement pointer 例子，可以理解成一种很简单的近似策略：

- 硬件维护一个替换指针；
- miss 时替换指针指向的 entry；
- 如果某次访问正好访问了指针指向的 entry，说明它刚被用过，不适合替换，于是指针移动到下一个；
- 如果访问的不是指针指向的 entry，指针不动。

这就是一种“不要替换最近用过的东西”的近似思想。

###### 举例：

假设一个 set 里有 4 个 way：`way0   way1   way2   way3`

现在有一个 replacement pointer：`ptr → way2`,意思是：如果下一次这个 set 发生 miss，就**先替换 way2。**

1. 如果来了一个新 block，并且这个 set 满了，当前：`ptr → way2`,那么就：移除 way2 原来的 block,把新 block 放到 way2,  新 block 刚刚被访问，所以 way2 不应该继续作为下次替换对象。于是 ptr 移到下一个位置，即`ptr → way3`（固定移动到下一个条目）
2. 假设当前还是：`ptr → way2`,

  1. 比如这次 hit 了 way0：访问 way0,  ptr 仍然指向 way2
  2. 正好访问了 way2：这时候 way2 刚刚被访问过了，说明它不应该马上被替换。于是 ptr 往后挪：`ptr → way3`

> <mark>
> 
> **replacement pointer 指向“当前最适合被替换的候选 way”。**
> 
> </mark>

##### Tree-PLRU

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-76.webp)

这一页是 Tree-PLRU，也就是 **树形伪 LRU**。它主要用于 4-way 或 8-way set associative cache。<mark>

核心思想是：用一棵二叉树的若干 bit，近似记录哪一边更久没被访问。

</mark>



<mark>

对于 N-way set associative cache，Tree-PLRU 只需要

</mark>

  <mark>

**n-1**

</mark>

  <mark>

个 bit。

</mark>



比如 4-way cache，需要 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mn>

4

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

3

</mn>
</mrow>

<annotation encoding="application/x-tex">

4-1=3

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.7278em;vertical-align:-0.0833em;">



</span>

<span className="mord">

4

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
<span className="strut" style="height:0.6444em;">



</span>

<span className="mord">

3

</span>
</span>
</span>
</span>

 个 bit。

这页图里有 4 条 line：

- line_0
- line_1
- line_2
- line_3

用 3 个 bit 来做一棵树：

```text
bit_0
        /       \
     bit_1     bit_2
    /    \     /    \
 line0 line1 line2 line3
```

这里每个 bit 可以理解成一个“方向指示器”，表示下一次替换时应该往哪边走。**把这三个bit拼成state变量：state=b0b1b2**

1. 读取规则：

  - 如果 state 是 <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mn>
  
  00
  
  </mn>
  
  <mi>
  
  x
  
  </mi>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  00x
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:0.6444em;">
  
  
  
  </span>
  
  <span className="mord">
  
  00
  
  </span>
  
  <span className="mord,mathnormal">
  
  x
  
  </span>
  </span>
  </span>
  </span>
  
  ，替换 line_0；
  - 如果 state 是 <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mn>
  
  01
  
  </mn>
  
  <mi>
  
  x
  
  </mi>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  01x
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:0.6444em;">
  
  
  
  </span>
  
  <span className="mord">
  
  01
  
  </span>
  
  <span className="mord,mathnormal">
  
  x
  
  </span>
  </span>
  </span>
  </span>
  
  ，替换 line_1；
  - 如果 state 是 <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mn>
  
  1
  
  </mn>
  
  <mi>
  
  x
  
  </mi>
  
  <mn>
  
  0
  
  </mn>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  1x0
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:0.6444em;">
  
  
  
  </span>
  
  <span className="mord">
  
  1
  
  </span>
  
  <span className="mord,mathnormal">
  
  x
  
  </span>
  
  <span className="mord">
  
  0
  
  </span>
  </span>
  </span>
  </span>
  
  ，替换 line_2；
  - 如果 state 是 <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mn>
  
  1
  
  </mn>
  
  <mi>
  
  x
  
  </mi>
  
  <mn>
  
  1
  
  </mn>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  1x1
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:0.6444em;">
  
  
  
  </span>
  
  <span className="mord">
  
  1
  
  </span>
  
  <span className="mord,mathnormal">
  
  x
  
  </span>
  
  <span className="mord">
  
  1
  
  </span>
  </span>
  </span>
  </span>
  
  ，替换 line_3。

> 这里的 <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <mi>
> 
> x
> 
> </mi>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> x
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:0.4306em;">
> 
> 
> 
> </span>
> 
> <span className="mord,mathnormal">
> 
> x
> 
> </span>
> </span>
> </span>
> </span>
> 
>  表示 don’t care，也就是这一位不影响当前替换结果。
> 
> 比如状态是 <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <mn>
> 
> 001
> 
> </mn>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> 001
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:0.6444em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> 
> 001
> 
> </span>
> </span>
> </span>
> </span>
> 
> ：
> 
> - bit_0 = 0，所以往左子树走；
> - bit_1 = 0，所以选 line_0；
> - bit_2 不看。
> 
> 所以替换 line_0。

1. 更新规则：

  1. <mark>
  
  **访问某条 line 之后，要更新沿途 bit，让它们指向“另一边”。因为刚访问过的这一边不应该马上被替换。**
  
  </mark>
  2. 图右侧的表就是更新规则：
  ![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-77.webp)
  3. 下划线表示 unchanged，也就是这一位不变。

举个例子：访问 line_0 后，说明左子树刚被用过，所以根节点 bit_0 要指向右边；同时 line_0 刚被用过，所以左子树内部 bit_1 要指向 line_1。于是状态变成 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mn>

11

</mn>

<mi mathvariant="normal">

_

</mi>
</mrow>

<annotation encoding="application/x-tex">

11\_

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9544em;vertical-align:-0.31em;">



</span>

<span className="mord" style="margin-right:0.0278em;">

11_

</span>
</span>
</span>
</span>



---

#### 摆放策略 |  Placement Policy

**一个 memory block 到底可以放在 cache 的哪里。**

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-78.webp)

三种 cache 组织方式答案不同。

#### Fully Associative

全相联 cache 中，一个 block 可以放在 cache 的任何地方。

所以 block 12 可以放在任意 cache line。

这最灵活，conflict miss 最少，但需要比较所有 tag，硬件最贵。

#### 2-way Set Associative

假设 cache 一共有 8 个 line，2-way set associative。

那么：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mtext>

set 数量

</mtext>

<mo>

=

</mo>

<mfrac>
<mn>

8

</mn>

<mn>

2

</mn>
</mfrac>

<mo>

=

</mo>

<mn>

4

</mn>
</mrow>

<annotation encoding="application/x-tex">

\text{set 数量} = \frac{8}{2} = 4

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,text">
<span className="mord">

set

</span>

<span className="mord,cjk_fallback">

数量

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

2

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

8

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

4

</span>
</span>
</span>
</span>
</span>

memory block 12 应该进入哪个 set？

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mn>

12

</mn>

<mtext>



</mtext>

<mo lspace="0.22em" rspace="0.22em">
<mrow>
<mi mathvariant="normal">

m

</mi>

<mi mathvariant="normal">

o

</mi>

<mi mathvariant="normal">

d

</mi>
</mrow>
</mo>

<mtext>



</mtext>

<mn>

4

</mn>

<mo>

=

</mo>

<mn>

0

</mn>
</mrow>

<annotation encoding="application/x-tex">

12 \bmod 4 = 0

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord">

12

</span>

<span className="mspace" style="margin-right:0.0556em;">



</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">
<span className="mord">
<span className="mord,mathrm">

mod

</span>
</span>
</span>

<span className="mspace" style="margin-right:0.0556em;">



</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.6444em;">



</span>

<span className="mord">

4

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

0

</span>
</span>
</span>
</span>
</span>

所以 block 12 必须放在 **set 0** 中。

但是 set 0 里面有 2 个 way，所以它可以放在 set 0 的任意一个 way。

也就是：

> 不能放在整个 cache 的任意位置，只能放在 set 0 里的任意一路。

#### Direct Mapped

直接映射 cache 中，每个 set 只有 1 个 way。

假设 cache 有 8 个 line，也就是 8 个 set。

block 12 的位置是：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mn>

12

</mn>

<mtext>



</mtext>

<mo lspace="0.22em" rspace="0.22em">
<mrow>
<mi mathvariant="normal">

m

</mi>

<mi mathvariant="normal">

o

</mi>

<mi mathvariant="normal">

d

</mi>
</mrow>
</mo>

<mtext>



</mtext>

<mn>

8

</mn>

<mo>

=

</mo>

<mn>

4

</mn>
</mrow>

<annotation encoding="application/x-tex">

12 \bmod 8 = 4

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord">

12

</span>

<span className="mspace" style="margin-right:0.0556em;">



</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">
<span className="mord">
<span className="mord,mathrm">

mod

</span>
</span>
</span>

<span className="mspace" style="margin-right:0.0556em;">



</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.6444em;">



</span>

<span className="mord">

8

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

4

</span>
</span>
</span>
</span>
</span>

所以它只能放在 cache block 4。

没有选择余地。

### 描述缓存的参数

1. **访问时间 access time**：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

T

</mi>

<mrow>
<mi>

h

</mi>

<mi>

i

</mi>

<mi>

t

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

T_{hit}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.1389em;">

T

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.1389em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

hi

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
</span>
</span>
</span>

，即命中时访问 cache 需要多久
2. **容量 capacity**：cache 可以容纳的数据总量：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

C

</mi>

<mi>

a

</mi>

<mi>

p

</mi>

<mi>

a

</mi>

<mi>

c

</mi>

<mi>

i

</mi>

<mi>

t

</mi>

<mi>

y

</mi>

<mo>

=

</mo>

<mi mathvariant="normal">

#

</mi>

<mi>

b

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

s

</mi>

<mo>

×

</mo>

<mi>

b

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

s

</mi>

<mi>

i

</mi>

<mi>

z

</mi>

<mi>

e

</mi>
</mrow>

<annotation encoding="application/x-tex">

Capacity = \#blocks \times block\ size

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8778em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal">

p

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal">

c

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

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
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord">

#

</span>

<span className="mord,mathnormal">

b

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
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,mathnormal">

b

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

<span className="mord,mathnormal">

s

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal" style="margin-right:0.044em;">

z

</span>

<span className="mord,mathnormal">

e

</span>
</span>
</span>
</span>

，注意这里通常只算 data 容量，不一定把 tag、valid、dirty 等额外位算进去。
3. **块 / 行大小 block(line) size**: 一次移入或移出 cache 的数据量。block 大可以利用空间局部性，但也可能增加 miss penalty（**未命中代价**），并减少 cache 中可容纳的 block 数。
4. **替换策略 replacement policy**:  miss 时 cache 满了，要替换哪个 block？
5. **关联性 associativity**:  一个主存 block 被搬进 cache 时，有多少个候选位置可以放。

  - Direct-mapped：只能放一个位置；
  - Set-associative：能放在某个 set 内的多个 way；
  - Fully associative：能放在任意位置。

### 平均内存访问时间(AMAT) ｜ Average Memory Access Time

<mark>

**平均内存访问时间(AMAT, Average Memory Access Time)**

</mark>

<mark>

是考虑

</mark>

<mark>

**缓存命中**

</mark>

<mark>

和

</mark>

<mark>

**未命中**

</mark>

<mark>

的情况下访问内存的平均时间，计算方法如下：

</mark>



![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-79.webp)

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

A

</mi>

<mi>

M

</mi>

<mi>

A

</mi>

<mi>

T

</mi>

<mo>

=

</mo>

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

<mtext>



</mtext>

<mi>

f

</mi>

<mi>

o

</mi>

<mi>

r

</mi>

<mtext>



</mtext>

<mi>

a

</mi>

<mtext>



</mtext>

<mi>

h

</mi>

<mi>

i

</mi>

<mi>

t

</mi>

<mo>

+

</mo>

<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

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

<mo>

×

</mo>

<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

</mi>

<mtext>



</mtext>

<mi>

p

</mi>

<mi>

e

</mi>

<mi>

n

</mi>

<mi>

a

</mi>

<mi>

l

</mi>

<mi>

t

</mi>

<mi>

y

</mi>
</mrow>

<annotation encoding="application/x-tex">

AMAT = Time\ for\ a\ hit + Miss\ rate \times Miss\ penalty

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal">

A

</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

A

</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

T

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
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



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

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.1076em;">

f

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

or

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal">

a

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal">

hi

</span>

<span className="mord,mathnormal">

t

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
<span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

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

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal">

p

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal">

na

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

</span>
</span>
</span>
</span>
</span>

也就是：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mtext>

平均访存时间

</mtext>

<mo>

=

</mo>

<mtext>

命中时间

</mtext>

<mo>

+

</mo>

<mtext>

未命中率

</mtext>

<mo>

×

</mo>

<mtext>

未命中惩罚

</mtext>
</mrow>

<annotation encoding="application/x-tex">

平均访存时间 = 命中时间 + 未命中率 \times 未命中惩罚

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,cjk_fallback">

平均访存时间

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

<span className="mord,cjk_fallback">

命中时间

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
<span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">



</span>

<span className="mord,cjk_fallback">

未命中率

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
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,cjk_fallback">

未命中惩罚

</span>
</span>
</span>
</span>
</span>

cache 的性能主要就看这三个量：

- <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
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

<mi>

e

</mi>

<mtext>



</mtext>

<mi>

f

</mi>

<mi>

o

</mi>

<mi>

r

</mi>

<mtext>



</mtext>

<mi>

a

</mi>

<mtext>



</mtext>

<mi>

h

</mi>

<mi>

i

</mi>

<mi>

t

</mi>
</mrow>

<annotation encoding="application/x-tex">

Time\ for\ a\ hit

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



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

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.1076em;">

f

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

or

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal">

a

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal">

hi

</span>

<span className="mord,mathnormal">

t

</span>
</span>
</span>
</span>

：命中时访问 cache 的时间；
- <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

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

<annotation encoding="application/x-tex">

Miss\ rate

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

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

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

：未命中比例；<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

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

<mo>

=

</mo>

<mfrac>
<mrow>
<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

</mi>

<mi>

e

</mi>

<mi>

s

</mi>
</mrow>

<mrow>
<mi>

T

</mi>

<mi>

o

</mi>

<mi>

t

</mi>

<mi>

a

</mi>

<mi>

l

</mi>

<mtext>



</mtext>

<mi>

a

</mi>

<mi>

c

</mi>

<mi>

c

</mi>

<mi>

e

</mi>

<mi>

s

</mi>

<mi>

s

</mi>

<mi>

e

</mi>

<mi>

s

</mi>
</mrow>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

Miss\ rate = \frac{Misses}{Total\ accesses}

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

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.2173em;vertical-align:-0.345em;">



</span>

<span className="mord">
<span className="mopen,nulldelimiter">



</span>

<span className="mfrac">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.8723em;">
<span style="top:-2.655em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.1389em;">

T

</span>

<span className="mord,mathnormal,mtight">

o

</span>

<span className="mord,mathnormal,mtight">

t

</span>

<span className="mord,mathnormal,mtight">

a

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0197em;">

l

</span>

<span className="mspace,mtight">
<span className="mtight">



</span>
</span>

<span className="mord,mathnormal,mtight">

a

</span>

<span className="mord,mathnormal,mtight">

ccesses

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
<span className="mord,mathnormal,mtight" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal,mtight">

i

</span>

<span className="mord,mathnormal,mtight">

sses

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
- <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

</mi>

<mtext>



</mtext>

<mi>

p

</mi>

<mi>

e

</mi>

<mi>

n

</mi>

<mi>

a

</mi>

<mi>

l

</mi>

<mi>

t

</mi>

<mi>

y

</mi>
</mrow>

<annotation encoding="application/x-tex">

Miss\ penalty

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal">

p

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal">

na

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

</span>
</span>
</span>
</span>

：一次 miss 额外要付出的代价时间——**从较低的内存级别获取块的时间；它通常包括下面**<mark>

**两个部分：**

</mark>


  1. **访问时间(access time)**: 时延函数(function of latency)，即找到第一个数据所需的延迟；
  
    1. 比如访问 DRAM 时，要经过行激活、列访问、等待返回数据，这部分主要和存储器的 latency 有关。
  2. **传输时间 (transfer time): 即把整个 cache block/line 传回来所需的时间**，它是带宽 b/w 级别的函数：
  
    1. 每次传输一条“缓存线/块(cache line/block)”
    2. 以内存总线宽度的大小进行传输，传输速度取决于带宽<span className="katex">
    <span className="katex-mathml">
    <math xmlns="http://www.w3.org/1998/Math/MathML">
    <semantics>
    <mrow>
    <mi>
    
    T
    
    </mi>
    
    <mi>
    
    r
    
    </mi>
    
    <mi>
    
    a
    
    </mi>
    
    <mi>
    
    n
    
    </mi>
    
    <mi>
    
    s
    
    </mi>
    
    <mi>
    
    f
    
    </mi>
    
    <mi>
    
    e
    
    </mi>
    
    <mi>
    
    r
    
    </mi>
    
    <mtext>
    
    
    
    </mtext>
    
    <mi>
    
    t
    
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
    
    ≈
    
    </mo>
    
    <mfrac>
    <mrow>
    <mi>
    
    B
    
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
    
    s
    
    </mi>
    
    <mi>
    
    i
    
    </mi>
    
    <mi>
    
    z
    
    </mi>
    
    <mi>
    
    e
    
    </mi>
    </mrow>
    
    <mrow>
    <mi>
    
    B
    
    </mi>
    
    <mi>
    
    a
    
    </mi>
    
    <mi>
    
    n
    
    </mi>
    
    <mi>
    
    d
    
    </mi>
    
    <mi>
    
    w
    
    </mi>
    
    <mi>
    
    i
    
    </mi>
    
    <mi>
    
    d
    
    </mi>
    
    <mi>
    
    t
    
    </mi>
    
    <mi>
    
    h
    
    </mi>
    </mrow>
    </mfrac>
    </mrow>
    
    <annotation encoding="application/x-tex">
    
    Transfer\ time \approx \frac{Block\ size}{Bandwidth}
    
    </annotation>
    </semantics>
    </math>
    </span>
    
    <span className="katex-html" ariaHidden="true">
    <span className="base">
    <span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">
    
    
    
    </span>
    
    <span className="mord,mathnormal" style="margin-right:0.1389em;">
    
    T
    
    </span>
    
    <span className="mord,mathnormal" style="margin-right:0.0278em;">
    
    r
    
    </span>
    
    <span className="mord,mathnormal">
    
    an
    
    </span>
    
    <span className="mord,mathnormal">
    
    s
    
    </span>
    
    <span className="mord,mathnormal" style="margin-right:0.1076em;">
    
    f
    
    </span>
    
    <span className="mord,mathnormal" style="margin-right:0.0278em;">
    
    er
    
    </span>
    
    <span className="mspace">
    
    
    
    </span>
    
    <span className="mord,mathnormal">
    
    t
    
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
    
    ≈
    
    </span>
    
    <span className="mspace" style="margin-right:0.2778em;">
    
    
    
    </span>
    </span>
    
    <span className="base">
    <span className="strut" style="height:1.2251em;vertical-align:-0.345em;">
    
    
    
    </span>
    
    <span className="mord">
    <span className="mopen,nulldelimiter">
    
    
    
    </span>
    
    <span className="mfrac">
    <span className="vlist-t,vlist-t2">
    <span className="vlist-r">
    <span className="vlist" style="height:0.8801em;">
    <span style="top:-2.655em;">
    <span className="pstrut" style="height:3em;">
    
    
    
    </span>
    
    <span className="sizing,reset-size6,size3,mtight">
    <span className="mord,mtight">
    <span className="mord,mathnormal,mtight" style="margin-right:0.0502em;">
    
    B
    
    </span>
    
    <span className="mord,mathnormal,mtight">
    
    an
    
    </span>
    
    <span className="mord,mathnormal,mtight">
    
    d
    
    </span>
    
    <span className="mord,mathnormal,mtight" style="margin-right:0.0269em;">
    
    w
    
    </span>
    
    <span className="mord,mathnormal,mtight">
    
    i
    
    </span>
    
    <span className="mord,mathnormal,mtight">
    
    d
    
    </span>
    
    <span className="mord,mathnormal,mtight">
    
    t
    
    </span>
    
    <span className="mord,mathnormal,mtight">
    
    h
    
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
    <span className="mord,mathnormal,mtight" style="margin-right:0.0502em;">
    
    B
    
    </span>
    
    <span className="mord,mathnormal,mtight" style="margin-right:0.0197em;">
    
    l
    
    </span>
    
    <span className="mord,mathnormal,mtight">
    
    oc
    
    </span>
    
    <span className="mord,mathnormal,mtight" style="margin-right:0.0315em;">
    
    k
    
    </span>
    
    <span className="mspace,mtight">
    <span className="mtight">
    
    
    
    </span>
    </span>
    
    <span className="mord,mathnormal,mtight">
    
    s
    
    </span>
    
    <span className="mord,mathnormal,mtight">
    
    i
    
    </span>
    
    <span className="mord,mathnormal,mtight" style="margin-right:0.044em;">
    
    z
    
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

> 这里有一个概率上的推导可以了解一下
> 
> 平均访存时间，实际上应该按照概率来加权——
> 
> 平均访存时间=命中时间*命中概率 + 未命中率*（未命中访问时间）
> 
> 但是实际上未命中访问时间=**查看cache时间(实际上是和命中时间一样的)** + **下一级存储器取数据时间（未命中额外付出的代价时间）**
> 
> 因此把前面的式子展开就可以得到
> 
> 平均访存时间=命中时间*命中概率 + 未命中率*（查看cache时间 + 下一级存储器取数据时间）
> 
> =命中时间*命中概率 + 未命中率*（命中时间 + 未命中惩罚时间）
> 
> ```text
> =命中时间 + 未命中率*（未命中惩罚时间）
> ```
> 
> （命中概率+未命中概率=1）
> 
> 所以有式<span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <mi>
> 
> A
> 
> </mi>
> 
> <mi>
> 
> M
> 
> </mi>
> 
> <mi>
> 
> A
> 
> </mi>
> 
> <mi>
> 
> T
> 
> </mi>
> 
> <mo>
> 
> =
> 
> </mo>
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
> <mtext>
> 
> 
> 
> </mtext>
> 
> <mi>
> 
> f
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
> r
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
> a
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
> h
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
> <mo>
> 
> +
> 
> </mo>
> 
> <mi>
> 
> M
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
> s
> 
> </mi>
> 
> <mi>
> 
> s
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
> r
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
> 
> <mo>
> 
> ×
> 
> </mo>
> 
> <mi>
> 
> M
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
> s
> 
> </mi>
> 
> <mi>
> 
> s
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
> p
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
> l
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
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> AMAT = Time\ for\ a\ hit + Miss\ rate \times Miss\ penalty
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
> <span className="mord,mathnormal">
> 
> A
> 
> </span>
> 
> <span className="mord,mathnormal" style="margin-right:0.109em;">
> 
> M
> 
> </span>
> 
> <span className="mord,mathnormal">
> 
> A
> 
> </span>
> 
> <span className="mord,mathnormal" style="margin-right:0.1389em;">
> 
> T
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
> <span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">
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
> <span className="mspace">
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
> 
> <span className="mord,mathnormal" style="margin-right:0.0278em;">
> 
> or
> 
> </span>
> 
> <span className="mspace">
> 
> 
> 
> </span>
> 
> <span className="mord,mathnormal">
> 
> a
> 
> </span>
> 
> <span className="mspace">
> 
> 
> 
> </span>
> 
> <span className="mord,mathnormal">
> 
> hi
> 
> </span>
> 
> <span className="mord,mathnormal">
> 
> t
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
> +
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
> <span className="mord,mathnormal" style="margin-right:0.109em;">
> 
> M
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
> ss
> 
> </span>
> 
> <span className="mspace">
> 
> 
> 
> </span>
> 
> <span className="mord,mathnormal" style="margin-right:0.0278em;">
> 
> r
> 
> </span>
> 
> <span className="mord,mathnormal">
> 
> a
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
> e
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
> <span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">
> 
> 
> 
> </span>
> 
> <span className="mord,mathnormal" style="margin-right:0.109em;">
> 
> M
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
> ss
> 
> </span>
> 
> <span className="mspace">
> 
> 
> 
> </span>
> 
> <span className="mord,mathnormal">
> 
> p
> 
> </span>
> 
> <span className="mord,mathnormal">
> 
> e
> 
> </span>
> 
> <span className="mord,mathnormal">
> 
> na
> 
> </span>
> 
> <span className="mord,mathnormal" style="margin-right:0.0197em;">
> 
> l
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
> </span>
> </span>
> </span>

> #### 例题
> 
> ![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-80.webp)
> 
> 时钟周期 <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <mn>
> 
> 200
> 
> </mn>
> 
> <mi>
> 
> p
> 
> </mi>
> 
> <mi>
> 
> s
> 
> </mi>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> 200ps
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:0.8389em;vertical-align:-0.1944em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> 
> 200
> 
> </span>
> 
> <span className="mord,mathnormal">
> 
> p
> 
> </span>
> 
> <span className="mord,mathnormal">
> 
> s
> 
> </span>
> </span>
> </span>
> </span>
> 
> ，miss penalty 是 <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <mn>
> 
> 50
> 
> </mn>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> 50
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:0.6444em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> 
> 50
> 
> </span>
> </span>
> </span>
> </span>
> 
>  个周期，miss rate 是 <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <mn>
> 
> 0.02
> 
> </mn>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> 0.02
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:0.6444em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> 
> 0.02
> 
> </span>
> </span>
> </span>
> </span>
> 
> ，cache hit time 是 <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <mn>
> 
> 1
> 
> </mn>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> 1
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:0.6444em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> 
> 1
> 
> </span>
> </span>
> </span>
> </span>
> 
>  个周期，计算一下AMAT是多少呢？
> 
> 答案是<span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <menclose notation="box">
> <mstyle scriptlevel="0" displaystyle="false">
> <mstyle scriptlevel="0" displaystyle="false">
> <mstyle scriptlevel="0" displaystyle="true">
> <mrow>
> <mi>
> 
> B
> 
> </mi>
> 
> <mo>
> 
> :
> 
> </mo>
> 
> <mtext>
> 
> 
> 
> </mtext>
> 
> <mn>
> 
> 400
> 
> </mn>
> 
> <mi>
> 
> p
> 
> </mi>
> 
> <mi>
> 
> s
> 
> </mi>
> </mrow>
> </mstyle>
> </mstyle>
> </mstyle>
> </menclose>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> \boxed{B:\ 400ps}
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:1.5578em;vertical-align:-0.5344em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:1.0233em;">
> <span style="top:-3.5578em;">
> <span className="pstrut" style="height:3.5578em;">
> 
> 
> 
> </span>
> 
> <span className="boxpad">
> <span className="mord">
> <span className="mord">
> <span className="mord,mathnormal" style="margin-right:0.0502em;">
> 
> B
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
> :
> 
> </span>
> 
> <span className="mspace">
> 
> 
> 
> </span>
> 
> <span className="mspace" style="margin-right:0.2778em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> 
> 400
> 
> </span>
> 
> <span className="mord,mathnormal">
> 
> p
> 
> </span>
> 
> <span className="mord,mathnormal">
> 
> s
> 
> </span>
> </span>
> </span>
> </span>
> </span>
> 
> <span style="top:-3.0233em;">
> <span className="pstrut" style="height:3.5578em;">
> 
> 
> 
> </span>
> 
> <span className="stretchy,fbox" style="height:1.5578em;border-style:solid;border-width:0.04em;">
> 
> 
> 
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
> <span className="vlist" style="height:0.5344em;">
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
> </span>
> </span>

## Cache Performance Optimization ｜ 缓存性能优化

### Cache Miss 的来源：3C Model

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-81.webp)

#### 1. Compulsory Miss：强制缺失 / 冷启动缺失

这是第一次访问某个 block 时必然发生的 miss。因为这个 block 从来没被加载进 cache，所以第一次访问一定 miss。

比如第一次访问数组 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

A

</mi>

<mo stretchy="false">

[

</mo>

<mn>

0

</mn>

<mo stretchy="false">

]

</mo>
</mrow>

<annotation encoding="application/x-tex">

A[0]

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord,mathnormal">

A

</span>

<span className="mopen">

[

</span>

<span className="mord">

0

</span>

<span className="mclose">

]

</span>
</span>
</span>
</span>

 所在的 cache block，它不可能已经在 cache 里。这种 miss 即使 cache 无限大、fully associative，也还是会发生。因为第一次访问就是第一次访问，cache 之前没有机会保存它。

**所以 compulsory miss 也叫 cold miss。**

#### 2. Capacity Miss：容量缺失

Capacity miss 是因为：**cache 太小，装不下**程序当前需要反复访问的所有 block。

比如一个程序反复扫描一个 10 MB 的工作集，但 cache 只有 32 KB。即使 cache 是 fully associative，而且 replacement policy 非常好，还是装不下。这种 miss 的根本原因是容量不够。

解决方向是：

- 增大 cache；
- 改程序访问方式，例如 blocking / tiling；
- 减小 working set。

#### 3. Conflict Miss：冲突缺失

Conflict miss 是因为：cache 的摆放规则太受限，多个 memory block 映射到同一个 set 或同一个 line，互相挤掉。

比如 direct-mapped cache 中，block 0 和 block 4 可能都只能放到同一个 cache line。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-82.webp)

如果程序反复访问 0、4、0、4，就会 ping-pong，导致连续 miss。注意：这时候 cache 总容量可能够，但因为映射位置冲突，仍然 miss。

<mark>

Fully associative cache 不会有 conflict miss，因为任何 block 都可以放在任意位置。

</mark>



### 如何用缓存模拟器计算 3C

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-83.webp)

给定一段程序的内存访问 trace，怎样区分三类 miss。

**核心方法是做对照实验。**

#### **第一步：算 compulsory miss**

把 cache 设成“无限大 + fully associative”。这样容量无限、没有冲突，所以剩下的 miss 只能是第一次访问 block 的 compulsory miss。

也就是：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<msub>
<mi>

s

</mi>

<mrow>
<mi>

c

</mi>

<mi>

o

</mi>

<mi>

m

</mi>

<mi>

p

</mi>

<mi>

u

</mi>

<mi>

l

</mi>

<mi>

s

</mi>

<mi>

o

</mi>

<mi>

r

</mi>

<mi>

y

</mi>
</mrow>
</msub>

<mo>

=

</mo>

<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

</mi>

<mo stretchy="false">

(

</mo>

<mi mathvariant="normal">

∞

</mi>

<mo separator="true">

,

</mo>

<mi>

F

</mi>

<mi>

A

</mi>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

Miss_{compulsory}=Miss(\infty,FA)

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9694em;vertical-align:-0.2861em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

s

</span>

<span className="mord">
<span className="mord,mathnormal">

s

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

co

</span>

<span className="mord,mathnormal,mtight">

m

</span>

<span className="mord,mathnormal,mtight">

p

</span>

<span className="mord,mathnormal,mtight">

u

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

sor

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

y

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
<span className="vlist" style="height:0.2861em;">
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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

</span>

<span className="mopen">

(

</span>

<span className="mord">

∞

</span>

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

F

</span>

<span className="mord,mathnormal">

A

</span>

<span className="mclose">

)

</span>
</span>
</span>
</span>

。

#### **第二步：算 capacity miss**

继续使用 fully associative cache，但把容量从无限大逐渐减小，比如 16MB、8MB、4MB、……。因为 fully associative 没有 conflict miss，所以多出来的 miss 主要就是容量不够造成的。

可以近似写成：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<msub>
<mi>

s

</mi>

<mrow>
<mi>

c

</mi>

<mi>

a

</mi>

<mi>

p

</mi>

<mi>

a

</mi>

<mi>

c

</mi>

<mi>

i

</mi>

<mi>

t

</mi>

<mi>

y

</mi>
</mrow>
</msub>

<mo>

=

</mo>

<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

</mi>

<mo stretchy="false">

(

</mo>

<mi>

C

</mi>

<mo separator="true">

,

</mo>

<mi>

F

</mi>

<mi>

A

</mi>

<mo stretchy="false">

)

</mo>

<mo>

−

</mo>

<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<msub>
<mi>

s

</mi>

<mrow>
<mi>

c

</mi>

<mi>

o

</mi>

<mi>

m

</mi>

<mi>

p

</mi>

<mi>

u

</mi>

<mi>

l

</mi>

<mi>

s

</mi>

<mi>

o

</mi>

<mi>

r

</mi>

<mi>

y

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

Miss_{capacity}=Miss(C,FA)-Miss_{compulsory}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9694em;vertical-align:-0.2861em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

s

</span>

<span className="mord">
<span className="mord,mathnormal">

s

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
<span className="mord,mathnormal,mtight">

c

</span>

<span className="mord,mathnormal,mtight">

a

</span>

<span className="mord,mathnormal,mtight">

p

</span>

<span className="mord,mathnormal,mtight">

a

</span>

<span className="mord,mathnormal,mtight">

c

</span>

<span className="mord,mathnormal,mtight">

i

</span>

<span className="mord,mathnormal,mtight">

t

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

y

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
<span className="vlist" style="height:0.2861em;">
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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

</span>

<span className="mopen">

(

</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

F

</span>

<span className="mord,mathnormal">

A

</span>

<span className="mclose">

)

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
<span className="strut" style="height:0.9694em;vertical-align:-0.2861em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

s

</span>

<span className="mord">
<span className="mord,mathnormal">

s

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

co

</span>

<span className="mord,mathnormal,mtight">

m

</span>

<span className="mord,mathnormal,mtight">

p

</span>

<span className="mord,mathnormal,mtight">

u

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

sor

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

y

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

。

#### **第三步：算 conflict miss**

保持同样容量，把 fully associative 改成 16-way、8-way、4-way、2-way、1-way。随着相联度降低，冲突会变多。实际 cache 比 fully associative 多出来的 miss，就是 conflict miss。

可以近似写成：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<msub>
<mi>

s

</mi>

<mrow>
<mi>

c

</mi>

<mi>

o

</mi>

<mi>

n

</mi>

<mi>

f

</mi>

<mi>

l

</mi>

<mi>

i

</mi>

<mi>

c

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

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

</mi>

<mo stretchy="false">

(

</mo>

<mi>

C

</mi>

<mo separator="true">

,

</mo>

<mi>

N

</mi>

<mtext>

-way

</mtext>

<mo stretchy="false">

)

</mo>

<mo>

−

</mo>

<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

</mi>

<mo stretchy="false">

(

</mo>

<mi>

C

</mi>

<mo separator="true">

,

</mo>

<mi>

F

</mi>

<mi>

A

</mi>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

Miss_{conflict}=Miss(C,N\text{-way})-Miss(C,FA)

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9694em;vertical-align:-0.2861em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

s

</span>

<span className="mord">
<span className="mord,mathnormal">

s

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

co

</span>

<span className="mord,mathnormal,mtight">

n

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.1076em;">

f

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal,mtight">

i

</span>

<span className="mord,mathnormal,mtight">

c

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
<span className="vlist" style="height:0.2861em;">
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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

</span>

<span className="mopen">

(

</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

N

</span>

<span className="mord,text">
<span className="mord">

-way

</span>
</span>

<span className="mclose">

)

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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

</span>

<span className="mopen">

(

</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

F

</span>

<span className="mord,mathnormal">

A

</span>

<span className="mclose">

)

</span>
</span>
</span>
</span>

。

### 主要的缓存参数（复习）

> 复习一下前面讲的 重复了这里

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-84.webp)

这一页是在总结描述一个 cache 需要哪些核心参数。

**Block size｜块大小**

一个 cache line / block 里有多少字节数据。比如 block size = 64B，表示一次 miss 从下级存储器搬 64B 到 cache。

block size 越大，越能利用空间局部性，但 miss penalty **（未命中代价）**也可能变大。

**Associativity｜相联度**

每个 set 里有多少个 way。

- direct mapped：每个 set 只有 1 个 way，所以 associativity = 1；
- set associative：每个 set 有多个 way，比如 2-way、4-way；
- fully associative：整个 cache 只有一个 set，所有 block 都可以放到任何位置。

**缓存容量：**<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

C

</mi>

<mi>

a

</mi>

<mi>

p

</mi>

<mi>

a

</mi>

<mi>

c

</mi>

<mi>

i

</mi>

<mi>

t

</mi>

<mi>

y

</mi>

<mo>

=

</mo>

<mi mathvariant="normal">

#

</mi>

<mi>

s

</mi>

<mi>

e

</mi>

<mi>

t

</mi>

<mi>

s

</mi>

<mo>

×

</mo>

<mi>

a

</mi>

<mi>

s

</mi>

<mi>

s

</mi>

<mi>

o

</mi>

<mi>

c

</mi>

<mi>

i

</mi>

<mi>

a

</mi>

<mi>

t

</mi>

<mi>

i

</mi>

<mi>

v

</mi>

<mi>

i

</mi>

<mi>

t

</mi>

<mi>

y

</mi>

<mo>

×

</mo>

<mi>

b

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

s

</mi>

<mi>

i

</mi>

<mi>

z

</mi>

<mi>

e

</mi>
</mrow>

<annotation encoding="application/x-tex">

Capacity=\#sets\times associativity\times block\ size

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8778em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal">

p

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal">

c

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

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
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord">

#

</span>

<span className="mord,mathnormal">

se

</span>

<span className="mord,mathnormal">

t

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
<span className="strut" style="height:0.854em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal">

ssoc

</span>

<span className="mord,mathnormal">

ia

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

v

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

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
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,mathnormal">

b

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

<span className="mord,mathnormal">

s

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal" style="margin-right:0.044em;">

z

</span>

<span className="mord,mathnormal">

e

</span>
</span>
</span>
</span>

。

也可以写成：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi mathvariant="normal">

#

</mi>

<mi>

i

</mi>

<mi>

t

</mi>

<mi>

e

</mi>

<mi>

m

</mi>

<mi>

s

</mi>

<mo>

=

</mo>

<mi mathvariant="normal">

#

</mi>

<mi>

s

</mi>

<mi>

e

</mi>

<mi>

t

</mi>

<mi>

s

</mi>

<mo>

×

</mo>

<mi>

a

</mi>

<mi>

s

</mi>

<mi>

s

</mi>

<mi>

o

</mi>

<mi>

c

</mi>

<mi>

i

</mi>

<mi>

a

</mi>

<mi>

t

</mi>

<mi>

i

</mi>

<mi>

v

</mi>

<mi>

i

</mi>

<mi>

t

</mi>

<mi>

y

</mi>
</mrow>

<annotation encoding="application/x-tex">

\#items=\#sets\times associativity

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord">

#

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal">

m

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
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord">

#

</span>

<span className="mord,mathnormal">

se

</span>

<span className="mord,mathnormal">

t

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
<span className="strut" style="height:0.854em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal">

ssoc

</span>

<span className="mord,mathnormal">

ia

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

v

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

</span>
</span>
</span>
</span>

。

这里的 `items` 本质上就是 cache line / cache block 的总数量。

### Cache Design Space ｜ Cache 设计空间

cache 设计不是单参数优化，而是多个参数互相牵制。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-85.webp)

主要设计维度有：

- cache size；
- block size；
- associativity；
- replacement policy；
- **write-through vs write-back；**
- **write allocation。**

重点是：**没有一个参数是越大越好。**

比如：

cache size 变大，可以降低 miss rate，但 hit time、面积、功耗会增加。

block size 变大，可以利用空间局部性，但 block 数量减少，可能增加 conflict miss，并且 miss penalty 变大。

associativity 变大，可以降低 conflict miss，但需要更多比较器和选择器，hit time 可能增加。

### 六种基本缓存优化 ｜ Six Basic Cache Optimizations

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-86.webp)

这一页是后面几页的总览。

六种优化分别对应 AMAT 里的不同部分。

**1. 更大的 block**

主要减少 compulsory miss（冷启动缺失），因为一次搬入更多相邻数据，利用空间局部性。

但代价是：miss penalty （未命中代价）增加；cache 容量固定时 block 数变少，可能增加 capacity miss 和 conflict miss。

**2. 更大的 cache capacity**

主要减少 miss rate，尤其是 capacity miss。

但代价是：hit time 增加，功耗和面积增加。

**3. 更高的 associativity**

主要减少 conflict miss。

但代价是：hit time 增加，因为需要并行比较多个 tag，还要用 MUX 选择正确 way。

**4. 更多的缓存层级**

比如 L1 后面加 L2、L3。这样 L1 miss 不一定直接去 DRAM，而是先去 L2/L3，因此降低 miss penalty。

**5. read miss 优先于 write miss**

读 miss 会直接卡住 CPU，所以应优先处理读请求。写请求可以放到 write buffer 里慢慢写。

**6. 避免缓存索引时等待地址转换**

也就是尽量让 cache indexing 和虚拟地址到物理地址转换并行，减少 hit time。后面会联系 TLB / 虚拟地址缓存。

### 优化策略对比表

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-87.webp)

表里的 `+` 可以理解成“对这个指标有改善”，`-` 可以理解成“对这个指标有副作用”。

例如：

- **Larger block size：**它可以降低 compulsory miss，所以对 miss rate 有改善；但一次 miss 要搬更多字节，所以 miss penalty 变差。
- **Larger cache size：**它降低 miss rate，但 cache 变大之后 tag array / data array 访问更慢，所以 hit time 变差。
- **Higher associativity：**它降低 conflict miss，所以 miss rate 改善；但多路并行比较和选择会增加 hit time。
- **Multilevel caches：**它主要降低 miss penalty，因为 L1 miss 可以先去 L2，而不一定直接去 DRAM。
- **Read priority over writes：**它主要降低读 miss 的等待时间，所以改善 miss penalty。
- **Avoiding address translation during cache indexing：**它主要减少 hit time，因为不用等完整地址转换结束后再开始访问 cache。

#### 优化1：Larger Cache

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-88.webp)

更大 cache 的直接好处是：**减少 miss**。更准确地说，它主要减少：

- capacity miss；
- 一部分 conflict miss。

但它的坏处是：**hit time 会变长**。

因为 cache 越大，SRAM 阵列越大，decoder、bitline、tag 比较等路径都可能更慢。L1 cache 尤其敏感，因为 L1 hit time 常常影响 CPU 时钟周期。

所以更大 cache 不一定更快。判断标准还是看 AMAT：

1. 如果 miss rate 降低带来的收益，大于 hit time 增加带来的损失，那么更大 cache 有利。
2. 如果 hit time 增加太多，可能反而拖慢整体性能。

#### 优化2:增加缓存行数？

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-89.webp)

如果 block size 不变，通过增加 cache line 数量来增大 cache，会发生什么？

**Hit time 会增加。**因为 cache 更大，需要更大的 tag array 和 data array，访问路径更长。

**Miss rate 会下降。**因为总容量变大，可以容纳更多 block，所以 capacity miss 减少。同时，如果组数增加，很多地址不再挤在同一个 set，也可能减少 conflict miss。

**Miss penalty 基本不变。**因为 block size 没变，一次 miss 仍然搬同样大小的 block，下级存储访问代价大体不变。

**一个经验法则**：容量每增加约 4 倍，miss rate 大约下降 2 倍。但这只是粗略规律，不是严格公式。

##### 更大的缓存对 miss rate 的影响

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-90.webp)

图的横轴是 cache size，从 4KB 到 1024KB；纵轴是 miss rate。

主要趋势是：cache 越大，总 miss rate 越低。

但下降不是线性的，而是逐渐变缓。小 cache 增大一点收益很明显；大 cache 再继续增大，收益会变小。

从 3C 角度看：

compulsory miss 基本不会因为 cache 变大而消失，因为第一次访问 block 仍然 miss。

capacity miss 会明显下降，因为 cache 能容纳更多工作集。

conflict miss 也可能下降，因为更大 cache 往往有更多 set，冲突机会变少。

所以这一页的结论是：**更大 cache 确实能降低 miss rate，但收益递减，而且代价是更慢、更贵、更耗电。**

###### SPEC CPU2000 整数程序的 miss rate 与 cache size

> 这个了解即可了

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-91.webp)

这一页是实验数据图。横轴是 cache size，纵轴是 miss rate，而且纵轴是对数坐标。不同曲线代表不同 associativity：

- Direct；
- 2-way；
- 4-way；
- 8-way；
- Full。

#### 优化3: 增加 associativity

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-92.webp)

##### 更高 associativity 对 miss rate 的影响

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-93.webp)

左边图看的是总 miss rate 随 cache size 的变化。提高 associativity 后，总 miss rate 下降，尤其是在 cache 较小时更明显。

右边图看的是 miss 的组成比例。提高 associativity 主要减少的是 conflict miss，而 compulsory miss 和 capacity miss 不会因为 associativity 提高而本质消失。

**associativity 解决的是“映射冲突”，不是“容量不足”。**

##### 更高 associativity 的经验法则

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-94.webp)

也就是说，提高相联度可以在一定程度上弥补容量较小的问题。因为很多 miss 不是容量真的不够，而是 direct-mapped 的映射冲突太严重。

##### set-associative 的好处

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-95.webp)

这一页图的横轴是 associativity：one-way、two-way、four-way、eight-way。

纵轴是 miss rate。

不同曲线代表不同 cache size，比如 1KB、2KB、4KB、……、128KB。

图里最重要的结论是：**从 direct mapped 到 2-way 的收益最大。**

很多情况下，miss rate 能下降 20% 以上。

但从 4-way 到 8-way，收益就变小了。对于较大的 cache，比如 64KB、128KB，本来 miss rate 已经很低，提高 associativity 的收益更不明显。

所以工程选择要权衡：

1. direct-mapped cache 的 hit time 更短，硬件更简单。
2. set-associative cache 的 miss rate 更低，但 hit time、面积、功耗更高。

最终选哪个，要看 miss penalty 有多大，以及实现代价能不能接受。

#### 练习题

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-96.webp)

题目问：在 cache capacity 和 block size 固定时，增加 associativity 对 AMAT 有什么影响？

正确答案是 **A：Increases hit time, decreases miss rate**。

原因是：capacity 固定、block size 固定时，增加 associativity 意味着每个 set 里 way 更多，冲突减少，所以 miss rate 下降。

但同时，每次访问 cache 要比较更多 tag，还要从多个 way 中选择数据，所以 hit time 增加。

因此对 AMAT 的最终影响不一定单调。因为：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

A

</mi>

<mi>

M

</mi>

<mi>

A

</mi>

<mi>

T

</mi>

<mo>

=

</mo>

<mi>

H

</mi>

<mi>

i

</mi>

<mi>

t

</mi>

<mtext>



</mtext>

<mi>

t

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

+

</mo>

<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

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

<mo>

×

</mo>

<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

</mi>

<mtext>



</mtext>

<mi>

p

</mi>

<mi>

e

</mi>

<mi>

n

</mi>

<mi>

a

</mi>

<mi>

l

</mi>

<mi>

t

</mi>

<mi>

y

</mi>
</mrow>

<annotation encoding="application/x-tex">

AMAT=Hit\ time+Miss\ rate\times Miss\ penalty

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal">

A

</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

A

</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

T

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

<span className="mord,mathnormal" style="margin-right:0.0813em;">

H

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal">

t

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

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

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

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal">

p

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal">

na

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

</span>
</span>
</span>
</span>
</span>

hit time 增加是坏事，miss rate 降低是好事。最后 AMAT 是变大还是变小，要看二者哪个影响更强。

下面重新按你给的笔记风格分析 **L8-9 Memory 第 113–122 页**，也就是从 **AMAT、block size、read miss priority、address translation、multi-level cache** 这一段开始。课件来源为你上传的 `L8-9 Memory(2).pptx`。

---

## Page 113｜AMAT 与 Associativity 权衡

这一页继续讲 **associativity 对 AMAT 的影响**。

核心公式还是：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

A

</mi>

<mi>

M

</mi>

<mi>

A

</mi>

<mi>

T

</mi>

<mo>

=

</mo>

<mi>

H

</mi>

<mi>

i

</mi>

<mi>

t

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

+

</mo>

<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

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

<mo>

×

</mo>

<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

</mi>

<mtext>



</mtext>

<mi>

P

</mi>

<mi>

e

</mi>

<mi>

n

</mi>

<mi>

a

</mi>

<mi>

l

</mi>

<mi>

t

</mi>

<mi>

y

</mi>
</mrow>

<annotation encoding="application/x-tex">

AMAT = Hit\ Time + Miss\ Rate \times Miss\ Penalty

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal">

A

</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

A

</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

T

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

<span className="mord,mathnormal" style="margin-right:0.0813em;">

H

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

t

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

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

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

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal">

na

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

</span>
</span>
</span>
</span>
</span>

更高的 associativity 可以降低 cache miss rate，尤其是降低 **conflict miss**。因为同一个 set 里可以放更多 way，原本会互相挤掉的 blocks 现在可以共存。

但重点是：**associativity 不是越高越好。**

原因是 associativity 增大后：

- tag 比较器数量增加；
- 多个 way 要并行查找；
- hit 后还要通过 MUX 选择正确 way；
- replacement policy 也更复杂；
- 所以 **hit time 会增加**。

因此它对 AMAT 的影响是双向的：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

H

</mi>

<mi>

i

</mi>

<mi>

t

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

↑

</mo>

<mo separator="true">

,

</mo>

<mtext>



</mtext>

<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

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

<mo>

↓

</mo>

<mo separator="true">

,

</mo>

<mtext>



</mtext>

<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

</mi>

<mtext>



</mtext>

<mi>

P

</mi>

<mi>

e

</mi>

<mi>

n

</mi>

<mi>

a

</mi>

<mi>

l

</mi>

<mi>

t

</mi>

<mi>

y

</mi>

<mo>

≈

</mo>

<mtext>

不变

</mtext>
</mrow>

<annotation encoding="application/x-tex">

Hit\ Time \uparrow,\ Miss\ Rate \downarrow,\ Miss\ Penalty \approx 不变

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0813em;">

H

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

t

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

↑

</span>
</span>

<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mpunct">

,

</span>

<span className="mspace">



</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

↓

</span>
</span>

<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mpunct">

,

</span>

<span className="mspace">



</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal">

na

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

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
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,cjk_fallback">

不变

</span>
</span>
</span>
</span>
</span>

所以判断 associativity 是否值得提高，不能只看 miss rate 是否下降，而要看：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

H

</mi>

<mi>

i

</mi>

<mi>

t

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

<mtext>

增加的损失

</mtext>

<mo>
<

</mo>

<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

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

<mtext>

降低带来的收益

</mtext>
</mrow>

<annotation encoding="application/x-tex">

Hit\ Time 增加的损失 < Miss\ Rate 降低带来的收益

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.7224em;vertical-align:-0.0391em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0813em;">

H

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

t

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

<span className="mord,cjk_fallback">

增加的损失

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">
<

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

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

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

<span className="mord,cjk_fallback">

降低带来的收益

</span>
</span>
</span>
</span>
</span>

这一页还有一个重要工程经验：
**8-way set associative cache 在很多实际 workload 中，miss rate 已经接近 fully associative cache。**

注意这里不是说硬件结构等于 fully associative，而是说 **性能效果上接近**。Fully associative 需要全局搜索，硬件代价很高；8-way 往往已经足够接近它的 miss rate。

---

## Page 114｜增加 Block Size？

这一页开始讲另一个优化方向：**larger block size**。

block size 也叫 cache line size，是 cache 和下一级 memory 之间搬运数据的单位。

增大 block size 的影响要分别看 AMAT 三项。

### Hit time

hit time 通常 **基本不变**，有时可能略微下降，也可能略微上升。

为什么可能下降？

因为 block 变大后，在总 cache capacity 固定时，cache line 数量减少，tag 数量减少，tag array 可能更小。

为什么也可能上升？

因为 block 内部的数据选择更复杂，MUX、布线、边界选择可能增加开销。

所以考试里通常写：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

H

</mi>

<mi>

i

</mi>

<mi>

t

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

≈

</mo>

<mi>

U

</mi>

<mi>

n

</mi>

<mi>

c

</mi>

<mi>

h

</mi>

<mi>

a

</mi>

<mi>

n

</mi>

<mi>

g

</mi>

<mi>

e

</mi>

<mi>

d

</mi>
</mrow>

<annotation encoding="application/x-tex">

Hit\ Time \approx Unchanged

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0813em;">

H

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

t

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

≈

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

U

</span>

<span className="mord,mathnormal">

n

</span>

<span className="mord,mathnormal">

c

</span>

<span className="mord,mathnormal">

han

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

g

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal">

d

</span>
</span>
</span>
</span>
</span>

但工程上要知道它不是绝对不变。

### Miss rate

block size 增大后，miss rate 通常 **先下降，后可能上升**。

一开始下降，是因为利用了 **spatial locality｜空间局部性**。
访问一个地址后，很可能继续访问附近地址。

比如访问数组：

```text
a[0], a[1], a[2], a[3]
```

如果一个 block 一次把这几个元素都取进来，那么第一次 miss 后，后面可能都是 hit。

但 block 太大时，miss rate 可能上升。因为总 cache capacity 固定时：

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

a

</mi>

<mi>

c

</mi>

<mi>

h

</mi>

<mi>

e

</mi>

<mtext>



</mtext>

<mi>

B

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

N

</mi>

<mi>

u

</mi>

<mi>

m

</mi>

<mi>

b

</mi>

<mi>

e

</mi>

<mi>

r

</mi>

<mo>

=

</mo>

<mfrac>
<mrow>
<mi>

C

</mi>

<mi>

a

</mi>

<mi>

c

</mi>

<mi>

h

</mi>

<mi>

e

</mi>

<mtext>



</mtext>

<mi>

C

</mi>

<mi>

a

</mi>

<mi>

p

</mi>

<mi>

a

</mi>

<mi>

c

</mi>

<mi>

i

</mi>

<mi>

t

</mi>

<mi>

y

</mi>
</mrow>

<mrow>
<mi>

B

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

S

</mi>

<mi>

i

</mi>

<mi>

z

</mi>

<mi>

e

</mi>
</mrow>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

Cache\ Block\ Number = \frac{Cache\ Capacity}{Block\ Size}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal">

c

</span>

<span className="mord,mathnormal">

h

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.0502em;">

B

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

<span className="mord,mathnormal" style="margin-right:0.109em;">

N

</span>

<span className="mord,mathnormal">

u

</span>

<span className="mord,mathnormal">

mb

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

er

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
<span className="strut" style="height:2.0574em;vertical-align:-0.686em;">



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
<span className="mord,mathnormal" style="margin-right:0.0502em;">

B

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

<span className="mord,mathnormal" style="margin-right:0.0576em;">

S

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal" style="margin-right:0.044em;">

z

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
<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal">

c

</span>

<span className="mord,mathnormal">

h

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal">

p

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal">

c

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

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

block size 越大，cache 里能放的 block 数量越少，所以更容易发生：

- capacity miss；
- conflict miss；
- bandwidth waste。

### Miss penalty

block size 增大后，miss penalty 一般增加。

因为一次 miss 要从下一级 memory 搬更多字节。

所以这一页的核心结论是：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

B

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

S

</mi>

<mi>

i

</mi>

<mi>

z

</mi>

<mi>

e

</mi>

<mo>

↑

</mo>

<mo>

⇒

</mo>

<mi>

C

</mi>

<mi>

o

</mi>

<mi>

m

</mi>

<mi>

p

</mi>

<mi>

u

</mi>

<mi>

l

</mi>

<mi>

s

</mi>

<mi>

o

</mi>

<mi>

r

</mi>

<mi>

y

</mi>

<mtext>



</mtext>

<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

</mi>

<mo>

↓

</mo>

<mo separator="true">

,

</mo>

<mtext>



</mtext>

<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

</mi>

<mtext>



</mtext>

<mi>

P

</mi>

<mi>

e

</mi>

<mi>

n

</mi>

<mi>

a

</mi>

<mi>

l

</mi>

<mi>

t

</mi>

<mi>

y

</mi>

<mo>

↑

</mo>

<mo separator="true">

,

</mo>

<mtext>



</mtext>

<mi>

C

</mi>

<mi>

o

</mi>

<mi>

n

</mi>

<mi>

f

</mi>

<mi>

l

</mi>

<mi>

i

</mi>

<mi>

c

</mi>

<mi>

t

</mi>

<mi mathvariant="normal">

/

</mi>

<mi>

C

</mi>

<mi>

a

</mi>

<mi>

p

</mi>

<mi>

a

</mi>

<mi>

c

</mi>

<mi>

i

</mi>

<mi>

t

</mi>

<mi>

y

</mi>

<mtext>



</mtext>

<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

</mi>

<mtext>

可能

</mtext>

<mo>

↑

</mo>
</mrow>

<annotation encoding="application/x-tex">

Block\ Size \uparrow \Rightarrow Compulsory\ Miss \downarrow,\ Miss\ Penalty \uparrow,\ Conflict/Capacity\ Miss\ 可能\uparrow

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0502em;">

B

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

<span className="mord,mathnormal" style="margin-right:0.0576em;">

S

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal" style="margin-right:0.044em;">

z

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

↑⇒

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="mord,mathnormal">

o

</span>

<span className="mord,mathnormal">

m

</span>

<span className="mord,mathnormal">

p

</span>

<span className="mord,mathnormal">

u

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

sor

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

↓

</span>
</span>

<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mpunct">

,

</span>

<span className="mspace">



</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal">

na

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

↑

</span>
</span>

<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mpunct">

,

</span>

<span className="mspace">



</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="mord,mathnormal">

o

</span>

<span className="mord,mathnormal">

n

</span>

<span className="mord,mathnormal" style="margin-right:0.1076em;">

f

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

c

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord">

/

</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal">

p

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal">

c

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

</span>

<span className="mspace">



</span>

<span className="mord,cjk_fallback">

可能

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

↑

</span>
</span>
</span>
</span>
</span>

---

## Page 115｜回顾：Block Size 与 Spatial Locality

这一页重新强调：**block 是 cache 和 memory 之间的传输单位**。

也就是说，cache miss 的时候，不是只搬一个 byte 或一个 word，而是搬一整个 cache block。

例如一个 block 里有 4 个 words：

```text
Word0 | Word1 | Word2 | Word3
```

当 CPU 访问 Word0 时，如果发生 miss，cache 会把整个 block 都从 memory 搬进来。于是后续访问 Word1、Word2、Word3 时就可能直接 hit。

这利用的是：

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

a

</mi>

<mi>

t

</mi>

<mi>

i

</mi>

<mi>

a

</mi>

<mi>

l

</mi>

<mtext>



</mtext>

<mi>

L

</mi>

<mi>

o

</mi>

<mi>

c

</mi>

<mi>

a

</mi>

<mi>

l

</mi>

<mi>

i

</mi>

<mi>

t

</mi>

<mi>

y

</mi>

<mo>

=

</mo>

<mtext>

访问一个地址后，很可能很快访问附近地址

</mtext>
</mrow>

<annotation encoding="application/x-tex">

Spatial\ Locality = 访问一个地址后，很可能很快访问附近地址

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

a

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal">

ia

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal">

L

</span>

<span className="mord,mathnormal">

oc

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

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

<span className="mord,cjk_fallback">

访问一个地址后，很可能很快访问附近地址

</span>
</span>
</span>
</span>
</span>

### Larger block 的好处

更大的 block 有几个硬件与性能优势：

- tag 数量减少；
- tag storage overhead 降低；
- 可以利用 DRAM burst transfer；
- 可以利用 wide bus 一次传更多数据；
- 对顺序数组访问非常友好。

比如连续访问数组时：

```c
for (i = 0; i < N; i++) {
    sum += a[i];
}
```

这种访问模式 spatial locality 很强，大 block 会比较有利。

### Larger block 的坏处

但 block size 过大也有问题：

- cache 中 line 数量减少；
- 不同 memory blocks 更容易争抢同一个 cache set；
- conflict miss 可能增加；
- miss penalty 增加；
- 如果带入的数据用不到，会浪费 memory bandwidth。

所以这一页想表达的不是“大 block 更好”，而是：

**大 block 是用 miss penalty 和 cache 有效容量去换 spatial locality。**

---

## Page 116｜更大的 Block：Miss Rate 下降但代价存在

这一页总结 larger block 的主要效果。

更大的 block 可以减少：

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

o

</mi>

<mi>

m

</mi>

<mi>

p

</mi>

<mi>

u

</mi>

<mi>

l

</mi>

<mi>

s

</mi>

<mi>

o

</mi>

<mi>

r

</mi>

<mi>

y

</mi>

<mtext>



</mtext>

<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

</mi>
</mrow>

<annotation encoding="application/x-tex">

Compulsory\ Miss

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="mord,mathnormal">

o

</span>

<span className="mord,mathnormal">

m

</span>

<span className="mord,mathnormal">

p

</span>

<span className="mord,mathnormal">

u

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

sor

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

</span>
</span>
</span>
</span>
</span>

因为第一次访问某个 block 时，会把附近数据一起带进 cache。

如果后面访问附近地址，本来可能是新的 compulsory miss，现在变成 hit。

例如：

```text
访问序列：0x1000, 0x1004, 0x1008, 0x100C
```

如果 block size = 4B，那么每个 word 可能各自 miss。

如果 block size = 16B，那么访问 0x1000 miss 后，后面三个地址都已经在同一个 block 里。

所以更大的 block 直接利用的是：

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

a

</mi>

<mi>

t

</mi>

<mi>

i

</mi>

<mi>

a

</mi>

<mi>

l

</mi>

<mtext>



</mtext>

<mi>

L

</mi>

<mi>

o

</mi>

<mi>

c

</mi>

<mi>

a

</mi>

<mi>

l

</mi>

<mi>

i

</mi>

<mi>

t

</mi>

<mi>

y

</mi>
</mrow>

<annotation encoding="application/x-tex">

Spatial\ Locality

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

a

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal">

ia

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal">

L

</span>

<span className="mord,mathnormal">

oc

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

</span>
</span>
</span>
</span>
</span>

但同时，它可能增加：

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

i

</mi>

<mi>

s

</mi>

<mi>

s

</mi>

<mtext>



</mtext>

<mi>

P

</mi>

<mi>

e

</mi>

<mi>

n

</mi>

<mi>

a

</mi>

<mi>

l

</mi>

<mi>

t

</mi>

<mi>

y

</mi>
</mrow>

<annotation encoding="application/x-tex">

Miss\ Penalty

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal">

na

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

</span>
</span>
</span>
</span>
</span>

因为一次 miss 要搬更多数据。

也可能增加：

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

o

</mi>

<mi>

n

</mi>

<mi>

f

</mi>

<mi>

l

</mi>

<mi>

i

</mi>

<mi>

c

</mi>

<mi>

t

</mi>

<mtext>



</mtext>

<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

</mi>
</mrow>

<annotation encoding="application/x-tex">

Conflict\ Miss

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="mord,mathnormal">

o

</span>

<span className="mord,mathnormal">

n

</span>

<span className="mord,mathnormal" style="margin-right:0.1076em;">

f

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

c

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

</span>
</span>
</span>
</span>
</span>

因为 cache capacity 固定时，block size 变大，cache line 数量变少，不同 memory blocks 更容易映射冲突。

所以 page 116 的核心是：

**larger block 主要减少 compulsory miss，但它不是免费优化。**

---

## Page 117｜练习：较大的 Block 对 AMAT 的影响

这一页是对 AMAT 三部分的分类判断。

题目问：在 **cache 总容量和 associativity 固定** 的情况下，larger blocks 对 AMAT 各项有什么影响？

AMAT 公式：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

A

</mi>

<mi>

M

</mi>

<mi>

A

</mi>

<mi>

T

</mi>

<mo>

=

</mo>

<mi>

H

</mi>

<mi>

i

</mi>

<mi>

t

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

+

</mo>

<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

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

<mo>

×

</mo>

<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

</mi>

<mtext>



</mtext>

<mi>

P

</mi>

<mi>

e

</mi>

<mi>

n

</mi>

<mi>

a

</mi>

<mi>

l

</mi>

<mi>

t

</mi>

<mi>

y

</mi>
</mrow>

<annotation encoding="application/x-tex">

AMAT = Hit\ Time + Miss\ Rate \times Miss\ Penalty

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal">

A

</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

A

</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

T

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

<span className="mord,mathnormal" style="margin-right:0.0813em;">

H

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

t

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

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

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

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal">

na

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

</span>
</span>
</span>
</span>
</span>

### Hit Time

一般认为：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

H

</mi>

<mi>

i

</mi>

<mi>

t

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

≈

</mo>

<mi>

U

</mi>

<mi>

n

</mi>

<mi>

c

</mi>

<mi>

h

</mi>

<mi>

a

</mi>

<mi>

n

</mi>

<mi>

g

</mi>

<mi>

e

</mi>

<mi>

d

</mi>
</mrow>

<annotation encoding="application/x-tex">

Hit\ Time \approx Unchanged

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0813em;">

H

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

t

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

≈

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

U

</span>

<span className="mord,mathnormal">

n

</span>

<span className="mord,mathnormal">

c

</span>

<span className="mord,mathnormal">

han

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

g

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal">

d

</span>
</span>
</span>
</span>
</span>

理由是 block size 改变主要影响 miss 时搬运的数据量，对 hit path 不一定有决定性影响。

但课件也提示：

- shorter tags 可能让 tag array 更简单；
- edge MUX 或 block 内选择可能带来额外开销。

所以更严谨地说：

**hit time 大体不变，但可能轻微变化。**

### Miss Rate

通常：

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

i

</mi>

<mi>

s

</mi>

<mi>

s

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

<mo>

↓

</mo>
</mrow>

<annotation encoding="application/x-tex">

Miss\ Rate \downarrow

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

↓

</span>
</span>
</span>
</span>
</span>

原因是 larger block 利用 spatial locality，减少 compulsory miss。

但注意，这个下降不是无限持续的。block 太大时，cache line 数变少，capacity/conflict miss 上升，总 miss rate 可能反弹。

所以更完整的说法是：

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

i

</mi>

<mi>

s

</mi>

<mi>

s

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

<mtext>

先下降，过大后可能上升

</mtext>
</mrow>

<annotation encoding="application/x-tex">

Miss\ Rate 先下降，过大后可能上升

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

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

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

<span className="mord,cjk_fallback">

先下降，过大后可能上升

</span>
</span>
</span>
</span>
</span>

### Miss Penalty

一定倾向于：

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

i

</mi>

<mi>

s

</mi>

<mi>

s

</mi>

<mtext>



</mtext>

<mi>

P

</mi>

<mi>

e

</mi>

<mi>

n

</mi>

<mi>

a

</mi>

<mi>

l

</mi>

<mi>

t

</mi>

<mi>

y

</mi>

<mo>

↑

</mo>
</mrow>

<annotation encoding="application/x-tex">

Miss\ Penalty \uparrow

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal">

na

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

↑

</span>
</span>
</span>
</span>
</span>

因为 miss 时要从下一级 memory 取更大的 block。

### 本页总结

<table>
<thead>
  <tr>
    <th>
      AMAT 项
    </th>
    
    <th>
      Larger Block 的影响
    </th>
    
    <th>
      原因
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      Hit Time
    </td>
    
    <td>
      基本不变
    </td>
    
    <td>
      hit 时只访问 cache，不一定受传输块大小强影响
    </td>
  </tr>
  
  <tr>
    <td>
      Miss Rate
    </td>
    
    <td>
      通常下降
    </td>
    
    <td>
      利用 spatial locality
    </td>
  </tr>
  
  <tr>
    <td>
      Miss Penalty
    </td>
    
    <td>
      增加
    </td>
    
    <td>
      miss 时搬运更多字节
    </td>
  </tr>
</tbody>
</table>

这一页的复习重点是：
**block size 主要是在 miss rate 和 miss penalty 之间做权衡。**

---

## Page 118｜练习：较大的 Block 对 3C Miss 的影响

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-97.webp)

这一页把 larger block 放到 3C miss 框架里分析。

3C miss 是：

- compulsory miss；
- capacity miss；
- conflict miss。

### Compulsory Miss

> **强制未命中**，也叫 **冷启动未命中 / 冷未命中**

larger block 通常会让 compulsory miss 下降。

原因是一次 miss 带入更多相邻数据。后续访问附近地址时，不再需要第一次访问那些小块。所以：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

C

</mi>

<mi>

o

</mi>

<mi>

m

</mi>

<mi>

p

</mi>

<mi>

u

</mi>

<mi>

l

</mi>

<mi>

s

</mi>

<mi>

o

</mi>

<mi>

r

</mi>

<mi>

y

</mi>

<mtext>



</mtext>

<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

</mi>

<mo>

↓

</mo>
</mrow>

<annotation encoding="application/x-tex">

Compulsory\ Miss \downarrow

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="mord,mathnormal">

o

</span>

<span className="mord,mathnormal">

m

</span>

<span className="mord,mathnormal">

p

</span>

<span className="mord,mathnormal">

u

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

sor

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

↓

</span>
</span>
</span>
</span>

前提是程序有较好的 spatial locality。如果程序访问完全随机，大 block 不一定有效。

### Capacity Miss

larger block 可能让 capacity miss 增加。

因为总容量固定时：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

B

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

N

</mi>

<mi>

u

</mi>

<mi>

m

</mi>

<mi>

b

</mi>

<mi>

e

</mi>

<mi>

r

</mi>

<mo>

=

</mo>

<mfrac>
<mrow>
<mi>

C

</mi>

<mi>

a

</mi>

<mi>

c

</mi>

<mi>

h

</mi>

<mi>

e

</mi>

<mtext>



</mtext>

<mi>

C

</mi>

<mi>

a

</mi>

<mi>

p

</mi>

<mi>

a

</mi>

<mi>

c

</mi>

<mi>

i

</mi>

<mi>

t

</mi>

<mi>

y

</mi>
</mrow>

<mrow>
<mi>

B

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

S

</mi>

<mi>

i

</mi>

<mi>

z

</mi>

<mi>

e

</mi>
</mrow>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

Block\ Number = \frac{Cache\ Capacity}{Block\ Size}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0502em;">

B

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

<span className="mord,mathnormal" style="margin-right:0.109em;">

N

</span>

<span className="mord,mathnormal">

u

</span>

<span className="mord,mathnormal">

mb

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

er

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
<span className="strut" style="height:2.0574em;vertical-align:-0.686em;">



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
<span className="mord,mathnormal" style="margin-right:0.0502em;">

B

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

<span className="mord,mathnormal" style="margin-right:0.0576em;">

S

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal" style="margin-right:0.044em;">

z

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
<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal">

c

</span>

<span className="mord,mathnormal">

h

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal">

p

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal">

c

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

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

block size 越大，能同时放进 cache 的独立 blocks 越少。

如果工作集本来就比较大，就更容易因为 cache 放不下而被替换。

所以：

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

a

</mi>

<mi>

p

</mi>

<mi>

a

</mi>

<mi>

c

</mi>

<mi>

i

</mi>

<mi>

t

</mi>

<mi>

y

</mi>

<mtext>



</mtext>

<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

</mi>

<mo>

↑

</mo>
</mrow>

<annotation encoding="application/x-tex">

Capacity\ Miss \uparrow

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal">

p

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal">

c

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

↑

</span>
</span>
</span>
</span>
</span>

### Conflict Miss

larger block 也可能让 conflict miss 增加。

因为 block 数量减少后，set 数量通常也减少。

不同 memory blocks 更容易映射到同一个 set，产生冲突。

所以：

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

o

</mi>

<mi>

n

</mi>

<mi>

f

</mi>

<mi>

l

</mi>

<mi>

i

</mi>

<mi>

c

</mi>

<mi>

t

</mi>

<mtext>



</mtext>

<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

</mi>

<mo>

↑

</mo>
</mrow>

<annotation encoding="application/x-tex">

Conflict\ Miss \uparrow

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="mord,mathnormal">

o

</span>

<span className="mord,mathnormal">

n

</span>

<span className="mord,mathnormal" style="margin-right:0.1076em;">

f

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

c

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

↑

</span>
</span>
</span>
</span>
</span>

### 本页总结

<table>
<thead>
  <tr>
    <th>
      Miss 类型
    </th>
    
    <th>
      Larger Block 的影响
    </th>
    
    <th>
      直觉
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      Compulsory Miss
    </td>
    
    <td>
      减少
    </td>
    
    <td>
      一次带入附近数据
    </td>
  </tr>
  
  <tr>
    <td>
      Capacity Miss
    </td>
    
    <td>
      增加
    </td>
    
    <td>
      cache 可容纳的 block 数变少
    </td>
  </tr>
  
  <tr>
    <td>
      Conflict Miss
    </td>
    
    <td>
      增加
    </td>
    
    <td>
      set/line 变少，映射冲突更多
    </td>
  </tr>
</tbody>
</table>

这一页非常适合考试总结：

**larger block 用空间局部性减少 compulsory miss，但会牺牲 cache 的有效容量，并可能增加 conflict/capacity miss。**

---

## Page 119｜练习：Direct-Mapped Cache Miss 分析

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-98.webp)

这一页是具体地址映射练习。

题目条件：

- direct-mapped cache；
- cache 有 4 个 blocks；
- block size = 16 bytes；
- memory address = 12 bits；
- 地址序列：

```text
0x004
0x0D8
0x005
0x0D4
```

### 地址字段划分

block size = 16 bytes，所以 offset 位数是：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

O

</mi>

<mi>

f

</mi>

<mi>

f

</mi>

<mi>

s

</mi>

<mi>

e

</mi>

<mi>

t

</mi>

<mo>

=

</mo>

<msub>
<mrow>
<mi>

log

</mi>

<mo>

⁡

</mo>
</mrow>

<mn>

2

</mn>
</msub>

<mn>

16

</mn>

<mo>

=

</mo>

<mn>

4

</mn>

<mtext>



</mtext>

<mi>

b

</mi>

<mi>

i

</mi>

<mi>

t

</mi>

<mi>

s

</mi>
</mrow>

<annotation encoding="application/x-tex">

Offset = \log_2 16 = 4\ bits

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

O

</span>

<span className="mord,mathnormal" style="margin-right:0.1076em;">

f

</span>

<span className="mord,mathnormal" style="margin-right:0.1076em;">

f

</span>

<span className="mord,mathnormal">

se

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
<span className="strut" style="height:0.9386em;vertical-align:-0.2441em;">



</span>

<span className="mop">
<span className="mop">

lo<span style="margin-right:0.0139em;">

g

</span>
</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.207em;">
<span style="top:-2.4559em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">

2

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.2441em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord">

16

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
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord">

4

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal">

bi

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal">

s

</span>
</span>
</span>
</span>
</span>

cache 有 4 个 blocks，direct-mapped，所以 index 位数是：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

I

</mi>

<mi>

n

</mi>

<mi>

d

</mi>

<mi>

e

</mi>

<mi>

x

</mi>

<mo>

=

</mo>

<msub>
<mrow>
<mi>

log

</mi>

<mo>

⁡

</mo>
</mrow>

<mn>

2

</mn>
</msub>

<mn>

4

</mn>

<mo>

=

</mo>

<mn>

2

</mn>

<mtext>



</mtext>

<mi>

b

</mi>

<mi>

i

</mi>

<mi>

t

</mi>

<mi>

s

</mi>
</mrow>

<annotation encoding="application/x-tex">

Index = \log_2 4 = 2\ bits

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0785em;">

I

</span>

<span className="mord,mathnormal">

n

</span>

<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal">

x

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
<span className="strut" style="height:0.9386em;vertical-align:-0.2441em;">



</span>

<span className="mop">
<span className="mop">

lo<span style="margin-right:0.0139em;">

g

</span>
</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.207em;">
<span style="top:-2.4559em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">

2

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.2441em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord">

4

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
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord">

2

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal">

bi

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal">

s

</span>
</span>
</span>
</span>
</span>

地址总长是 12 bits，所以 tag 位数是：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

T

</mi>

<mi>

a

</mi>

<mi>

g

</mi>

<mo>

=

</mo>

<mn>

12

</mn>

<mo>

−

</mo>

<mn>

4

</mn>

<mo>

−

</mo>

<mn>

2

</mn>

<mo>

=

</mo>

<mn>

6

</mn>

<mtext>



</mtext>

<mi>

b

</mi>

<mi>

i

</mi>

<mi>

t

</mi>

<mi>

s

</mi>
</mrow>

<annotation encoding="application/x-tex">

Tag = 12 - 4 - 2 = 6\ bits

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8778em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

T

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

g

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
<span className="strut" style="height:0.7278em;vertical-align:-0.0833em;">



</span>

<span className="mord">

12

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
<span className="strut" style="height:0.7278em;vertical-align:-0.0833em;">



</span>

<span className="mord">

4

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

2

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
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord">

6

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal">

bi

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal">

s

</span>
</span>
</span>
</span>
</span>

因此地址格式是：

```text
Tag 6 bits | Index 2 bits | Offset 4 bits
```

也可以用 block number 来算：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

B

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

N

</mi>

<mi>

u

</mi>

<mi>

m

</mi>

<mi>

b

</mi>

<mi>

e

</mi>

<mi>

r

</mi>

<mo>

=

</mo>

<mo stretchy="false">

⌊

</mo>

<mi>

A

</mi>

<mi>

d

</mi>

<mi>

d

</mi>

<mi>

r

</mi>

<mi>

e

</mi>

<mi>

s

</mi>

<mi>

s

</mi>

<mi mathvariant="normal">

/

</mi>

<mi>

B

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

S

</mi>

<mi>

i

</mi>

<mi>

z

</mi>

<mi>

e

</mi>

<mo stretchy="false">

⌋

</mo>
</mrow>

<annotation encoding="application/x-tex">

Block\ Number = \lfloor Address / Block\ Size \rfloor

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0502em;">

B

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

<span className="mord,mathnormal" style="margin-right:0.109em;">

N

</span>

<span className="mord,mathnormal">

u

</span>

<span className="mord,mathnormal">

mb

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

er

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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mopen">

⌊

</span>

<span className="mord,mathnormal">

A

</span>

<span className="mord,mathnormal">

dd

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal">

ess

</span>

<span className="mord">

/

</span>

<span className="mord,mathnormal" style="margin-right:0.0502em;">

B

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

<span className="mord,mathnormal" style="margin-right:0.0576em;">

S

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal" style="margin-right:0.044em;">

z

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mclose">

⌋

</span>
</span>
</span>
</span>
</span>

direct-mapped cache 的 index 是：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

I

</mi>

<mi>

n

</mi>

<mi>

d

</mi>

<mi>

e

</mi>

<mi>

x

</mi>

<mo>

=

</mo>

<mi>

B

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

N

</mi>

<mi>

u

</mi>

<mi>

m

</mi>

<mi>

b

</mi>

<mi>

e

</mi>

<mi>

r

</mi>

<mtext>



</mtext>

<mo lspace="0.22em" rspace="0.22em">
<mrow>
<mi mathvariant="normal">

m

</mi>

<mi mathvariant="normal">

o

</mi>

<mi mathvariant="normal">

d

</mi>
</mrow>
</mo>

<mtext>



</mtext>

<mi>

C

</mi>

<mi>

a

</mi>

<mi>

c

</mi>

<mi>

h

</mi>

<mi>

e

</mi>

<mtext>



</mtext>

<mi>

B

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

N

</mi>

<mi>

u

</mi>

<mi>

m

</mi>

<mi>

b

</mi>

<mi>

e

</mi>

<mi>

r

</mi>
</mrow>

<annotation encoding="application/x-tex">

Index = Block\ Number \bmod Cache\ Block\ Number

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0785em;">

I

</span>

<span className="mord,mathnormal">

n

</span>

<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal">

x

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
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0502em;">

B

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

<span className="mord,mathnormal" style="margin-right:0.109em;">

N

</span>

<span className="mord,mathnormal">

u

</span>

<span className="mord,mathnormal">

mb

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

er

</span>

<span className="mspace" style="margin-right:0.0556em;">



</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">
<span className="mord">
<span className="mord,mathrm">

mod

</span>
</span>
</span>

<span className="mspace" style="margin-right:0.0556em;">



</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal">

c

</span>

<span className="mord,mathnormal">

h

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.0502em;">

B

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

<span className="mord,mathnormal" style="margin-right:0.109em;">

N

</span>

<span className="mord,mathnormal">

u

</span>

<span className="mord,mathnormal">

mb

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

er

</span>
</span>
</span>
</span>
</span>

tag 是：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

T

</mi>

<mi>

a

</mi>

<mi>

g

</mi>

<mo>

=

</mo>

<mo stretchy="false">

⌊

</mo>

<mi>

B

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

N

</mi>

<mi>

u

</mi>

<mi>

m

</mi>

<mi>

b

</mi>

<mi>

e

</mi>

<mi>

r

</mi>

<mi mathvariant="normal">

/

</mi>

<mi>

C

</mi>

<mi>

a

</mi>

<mi>

c

</mi>

<mi>

h

</mi>

<mi>

e

</mi>

<mtext>



</mtext>

<mi>

B

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

N

</mi>

<mi>

u

</mi>

<mi>

m

</mi>

<mi>

b

</mi>

<mi>

e

</mi>

<mi>

r

</mi>

<mo stretchy="false">

⌋

</mo>
</mrow>

<annotation encoding="application/x-tex">

Tag = \lfloor Block\ Number / Cache\ Block\ Number \rfloor

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8778em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

T

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

g

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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mopen">

⌊

</span>

<span className="mord,mathnormal" style="margin-right:0.0502em;">

B

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

<span className="mord,mathnormal" style="margin-right:0.109em;">

N

</span>

<span className="mord,mathnormal">

u

</span>

<span className="mord,mathnormal">

mb

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

er

</span>

<span className="mord">

/

</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal">

c

</span>

<span className="mord,mathnormal">

h

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.0502em;">

B

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

<span className="mord,mathnormal" style="margin-right:0.109em;">

N

</span>

<span className="mord,mathnormal">

u

</span>

<span className="mord,mathnormal">

mb

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

er

</span>

<span className="mclose">

⌋

</span>
</span>
</span>
</span>
</span>

---

### 访问 1：0x004

地址：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mn>

0

</mn>

<mi>

x

</mi>

<mn>

004

</mn>

<mo>

=

</mo>

<mn>

4

</mn>
</mrow>

<annotation encoding="application/x-tex">

0x004 = 4

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6444em;">



</span>

<span className="mord">

0

</span>

<span className="mord,mathnormal">

x

</span>

<span className="mord">

004

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

4

</span>
</span>
</span>
</span>
</span>

block number（一个block的大小为16）：

<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

B

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

N

</mi>

<mi>

u

</mi>

<mi>

m

</mi>

<mi>

b

</mi>

<mi>

e

</mi>

<mi>

r

</mi>

<mo>

=

</mo>

<mo stretchy="false">

⌊

</mo>

<mn>

4

</mn>

<mi mathvariant="normal">

/

</mi>

<mn>

16

</mn>

<mo stretchy="false">

⌋

</mo>

<mo>

=

</mo>

<mn>

0

</mn>
</mrow>

<annotation encoding="application/x-tex">

Block\ Number = \lfloor 4 / 16 \rfloor = 0

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0502em;">

B

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

<span className="mord,mathnormal" style="margin-right:0.109em;">

N

</span>

<span className="mord,mathnormal">

u

</span>

<span className="mord,mathnormal">

mb

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

er

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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mopen">

⌊

</span>

<span className="mord">

4/16

</span>

<span className="mclose">

⌋

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

0

</span>
</span>
</span>
</span>

，说明在第0个block

index：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

I

</mi>

<mi>

n

</mi>

<mi>

d

</mi>

<mi>

e

</mi>

<mi>

x

</mi>

<mo>

=

</mo>

<mn>

0

</mn>

<mtext>



</mtext>

<mo lspace="0.22em" rspace="0.22em">
<mrow>
<mi mathvariant="normal">

m

</mi>

<mi mathvariant="normal">

o

</mi>

<mi mathvariant="normal">

d

</mi>
</mrow>
</mo>

<mtext>



</mtext>

<mn>

4

</mn>

<mo>

=

</mo>

<mn>

0

</mn>
</mrow>

<annotation encoding="application/x-tex">

Index = 0 \bmod 4 = 0

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0785em;">

I

</span>

<span className="mord,mathnormal">

n

</span>

<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal">

x

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
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord">

0

</span>

<span className="mspace" style="margin-right:0.0556em;">



</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">
<span className="mord">
<span className="mord,mathrm">

mod

</span>
</span>
</span>

<span className="mspace" style="margin-right:0.0556em;">



</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.6444em;">



</span>

<span className="mord">

4

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

0

</span>
</span>
</span>
</span>
</span>

tag：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

T

</mi>

<mi>

a

</mi>

<mi>

g

</mi>

<mo>

=

</mo>

<mo stretchy="false">

⌊

</mo>

<mn>

0

</mn>

<mi mathvariant="normal">

/

</mi>

<mn>

4

</mn>

<mo stretchy="false">

⌋

</mo>

<mo>

=

</mo>

<mn>

0

</mn>
</mrow>

<annotation encoding="application/x-tex">

Tag = \lfloor 0 / 4 \rfloor = 0

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8778em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

T

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

g

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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mopen">

⌊

</span>

<span className="mord">

0/4

</span>

<span className="mclose">

⌋

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

0

</span>
</span>
</span>
</span>
</span>

cache 初始为空，所以这次是：

```text
Miss，Compulsory Miss
```

因为这是第一次访问 block 0。

---

### 访问 2：0x0D8

地址：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mn>

0

</mn>

<mi>

x

</mi>

<mn>

0

</mn>

<mi>

D

</mi>

<mn>

8

</mn>

<mo>

=

</mo>

<mn>

216

</mn>
</mrow>

<annotation encoding="application/x-tex">

0x0D8 = 216

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord">

0

</span>

<span className="mord,mathnormal">

x

</span>

<span className="mord">

0

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

D

</span>

<span className="mord">

8

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

216

</span>
</span>
</span>
</span>
</span>

block number：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

B

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

N

</mi>

<mi>

u

</mi>

<mi>

m

</mi>

<mi>

b

</mi>

<mi>

e

</mi>

<mi>

r

</mi>

<mo>

=

</mo>

<mo stretchy="false">

⌊

</mo>

<mn>

216

</mn>

<mi mathvariant="normal">

/

</mi>

<mn>

16

</mn>

<mo stretchy="false">

⌋

</mo>

<mo>

=

</mo>

<mn>

13

</mn>
</mrow>

<annotation encoding="application/x-tex">

Block\ Number = \lfloor 216 / 16 \rfloor = 13

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0502em;">

B

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

<span className="mord,mathnormal" style="margin-right:0.109em;">

N

</span>

<span className="mord,mathnormal">

u

</span>

<span className="mord,mathnormal">

mb

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

er

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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mopen">

⌊

</span>

<span className="mord">

216/16

</span>

<span className="mclose">

⌋

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

13

</span>
</span>
</span>
</span>
</span>

index：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

I

</mi>

<mi>

n

</mi>

<mi>

d

</mi>

<mi>

e

</mi>

<mi>

x

</mi>

<mo>

=

</mo>

<mn>

13

</mn>

<mtext>



</mtext>

<mo lspace="0.22em" rspace="0.22em">
<mrow>
<mi mathvariant="normal">

m

</mi>

<mi mathvariant="normal">

o

</mi>

<mi mathvariant="normal">

d

</mi>
</mrow>
</mo>

<mtext>



</mtext>

<mn>

4

</mn>

<mo>

=

</mo>

<mn>

1

</mn>
</mrow>

<annotation encoding="application/x-tex">

Index = 13 \bmod 4 = 1

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0785em;">

I

</span>

<span className="mord,mathnormal">

n

</span>

<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal">

x

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
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord">

13

</span>

<span className="mspace" style="margin-right:0.0556em;">



</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">
<span className="mord">
<span className="mord,mathrm">

mod

</span>
</span>
</span>

<span className="mspace" style="margin-right:0.0556em;">



</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.6444em;">



</span>

<span className="mord">

4

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

1

</span>
</span>
</span>
</span>
</span>

tag：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

T

</mi>

<mi>

a

</mi>

<mi>

g

</mi>

<mo>

=

</mo>

<mo stretchy="false">

⌊

</mo>

<mn>

13

</mn>

<mi mathvariant="normal">

/

</mi>

<mn>

4

</mn>

<mo stretchy="false">

⌋

</mo>

<mo>

=

</mo>

<mn>

3

</mn>
</mrow>

<annotation encoding="application/x-tex">

Tag = \lfloor 13 / 4 \rfloor = 3

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8778em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

T

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

g

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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mopen">

⌊

</span>

<span className="mord">

13/4

</span>

<span className="mclose">

⌋

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

3

</span>
</span>
</span>
</span>
</span>

这是第一次访问 block 13，所以是：

```text
Miss，Compulsory Miss
```

它放入 cache index 1，不会和 block 0 冲突。

---

### 访问 3：0x005

地址：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mn>

0

</mn>

<mi>

x

</mi>

<mn>

005

</mn>

<mo>

=

</mo>

<mn>

5

</mn>
</mrow>

<annotation encoding="application/x-tex">

0x005 = 5

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6444em;">



</span>

<span className="mord">

0

</span>

<span className="mord,mathnormal">

x

</span>

<span className="mord">

005

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

5

</span>
</span>
</span>
</span>
</span>

block number：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

B

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

N

</mi>

<mi>

u

</mi>

<mi>

m

</mi>

<mi>

b

</mi>

<mi>

e

</mi>

<mi>

r

</mi>

<mo>

=

</mo>

<mo stretchy="false">

⌊

</mo>

<mn>

5

</mn>

<mi mathvariant="normal">

/

</mi>

<mn>

16

</mn>

<mo stretchy="false">

⌋

</mo>

<mo>

=

</mo>

<mn>

0

</mn>
</mrow>

<annotation encoding="application/x-tex">

Block\ Number = \lfloor 5 / 16 \rfloor = 0

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0502em;">

B

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

<span className="mord,mathnormal" style="margin-right:0.109em;">

N

</span>

<span className="mord,mathnormal">

u

</span>

<span className="mord,mathnormal">

mb

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

er

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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mopen">

⌊

</span>

<span className="mord">

5/16

</span>

<span className="mclose">

⌋

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

0

</span>
</span>
</span>
</span>
</span>

index：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

I

</mi>

<mi>

n

</mi>

<mi>

d

</mi>

<mi>

e

</mi>

<mi>

x

</mi>

<mo>

=

</mo>

<mn>

0

</mn>
</mrow>

<annotation encoding="application/x-tex">

Index = 0

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0785em;">

I

</span>

<span className="mord,mathnormal">

n

</span>

<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal">

x

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

0

</span>
</span>
</span>
</span>
</span>

tag：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

T

</mi>

<mi>

a

</mi>

<mi>

g

</mi>

<mo>

=

</mo>

<mn>

0

</mn>
</mrow>

<annotation encoding="application/x-tex">

Tag = 0

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8778em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

T

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

g

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

0

</span>
</span>
</span>
</span>
</span>

它和 0x004 属于同一个 block 0。

block 0 已经在 cache index 0 中，所以：

```text
Hit
```

这里体现的是 spatial locality。

---

### 访问 4：0x0D4

地址：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mn>

0

</mn>

<mi>

x

</mi>

<mn>

0

</mn>

<mi>

D

</mi>

<mn>

4

</mn>

<mo>

=

</mo>

<mn>

212

</mn>
</mrow>

<annotation encoding="application/x-tex">

0x0D4 = 212

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord">

0

</span>

<span className="mord,mathnormal">

x

</span>

<span className="mord">

0

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

D

</span>

<span className="mord">

4

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

212

</span>
</span>
</span>
</span>
</span>

block number：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

B

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

N

</mi>

<mi>

u

</mi>

<mi>

m

</mi>

<mi>

b

</mi>

<mi>

e

</mi>

<mi>

r

</mi>

<mo>

=

</mo>

<mo stretchy="false">

⌊

</mo>

<mn>

212

</mn>

<mi mathvariant="normal">

/

</mi>

<mn>

16

</mn>

<mo stretchy="false">

⌋

</mo>

<mo>

=

</mo>

<mn>

13

</mn>
</mrow>

<annotation encoding="application/x-tex">

Block\ Number = \lfloor 212 / 16 \rfloor = 13

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0502em;">

B

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

<span className="mord,mathnormal" style="margin-right:0.109em;">

N

</span>

<span className="mord,mathnormal">

u

</span>

<span className="mord,mathnormal">

mb

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

er

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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mopen">

⌊

</span>

<span className="mord">

212/16

</span>

<span className="mclose">

⌋

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

13

</span>
</span>
</span>
</span>
</span>

index：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

I

</mi>

<mi>

n

</mi>

<mi>

d

</mi>

<mi>

e

</mi>

<mi>

x

</mi>

<mo>

=

</mo>

<mn>

13

</mn>

<mtext>



</mtext>

<mo lspace="0.22em" rspace="0.22em">
<mrow>
<mi mathvariant="normal">

m

</mi>

<mi mathvariant="normal">

o

</mi>

<mi mathvariant="normal">

d

</mi>
</mrow>
</mo>

<mtext>



</mtext>

<mn>

4

</mn>

<mo>

=

</mo>

<mn>

1

</mn>
</mrow>

<annotation encoding="application/x-tex">

Index = 13 \bmod 4 = 1

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0785em;">

I

</span>

<span className="mord,mathnormal">

n

</span>

<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal">

x

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
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord">

13

</span>

<span className="mspace" style="margin-right:0.0556em;">



</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">
<span className="mord">
<span className="mord,mathrm">

mod

</span>
</span>
</span>

<span className="mspace" style="margin-right:0.0556em;">



</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.6444em;">



</span>

<span className="mord">

4

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

1

</span>
</span>
</span>
</span>
</span>

tag：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

T

</mi>

<mi>

a

</mi>

<mi>

g

</mi>

<mo>

=

</mo>

<mo stretchy="false">

⌊

</mo>

<mn>

13

</mn>

<mi mathvariant="normal">

/

</mi>

<mn>

4

</mn>

<mo stretchy="false">

⌋

</mo>

<mo>

=

</mo>

<mn>

3

</mn>
</mrow>

<annotation encoding="application/x-tex">

Tag = \lfloor 13 / 4 \rfloor = 3

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8778em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

T

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

g

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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mopen">

⌊

</span>

<span className="mord">

13/4

</span>

<span className="mclose">

⌋

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

3

</span>
</span>
</span>
</span>
</span>

它和 0x0D8 属于同一个 block 13。

block 13 已经在 cache index 1 中，所以：

```text
Hit
```

---

### Page 119 最终表格

<table>
<thead>
  <tr>
    <th>
      访问顺序
    </th>
    
    <th>
      地址
    </th>
    
    <th>
      Block Number
    </th>
    
    <th>
      Index
    </th>
    
    <th>
      Tag
    </th>
    
    <th>
      Hit/Miss
    </th>
    
    <th>
      Miss 类型
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      1
    </td>
    
    <td>
      0x004
    </td>
    
    <td>
      0
    </td>
    
    <td>
      0
    </td>
    
    <td>
      0
    </td>
    
    <td>
      Miss
    </td>
    
    <td>
      Compulsory
    </td>
  </tr>
  
  <tr>
    <td>
      2
    </td>
    
    <td>
      0x0D8
    </td>
    
    <td>
      13
    </td>
    
    <td>
      1
    </td>
    
    <td>
      3
    </td>
    
    <td>
      Miss
    </td>
    
    <td>
      Compulsory
    </td>
  </tr>
  
  <tr>
    <td>
      3
    </td>
    
    <td>
      0x005
    </td>
    
    <td>
      0
    </td>
    
    <td>
      0
    </td>
    
    <td>
      0
    </td>
    
    <td>
      Hit
    </td>
    
    <td>
      —
    </td>
  </tr>
  
  <tr>
    <td>
      4
    </td>
    
    <td>
      0x0D4
    </td>
    
    <td>
      13
    </td>
    
    <td>
      1
    </td>
    
    <td>
      3
    </td>
    
    <td>
      Hit
    </td>
    
    <td>
      —
    </td>
  </tr>
</tbody>
</table>

最终结果：

```text
Miss, Miss, Hit, Hit
```

核心原因是：

0x004 和 0x005 在同一个 16B block 里；0x0D8 和 0x0D4 也在同一个 16B block 里。

---

## Page 120｜Read Miss 优先于 Write Miss

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-99.webp)

这一页讲的是优化 miss penalty 的方法：**read miss priority over writes｜读未命中优先于写操作。**

写操作通常可以先放进：

```text
write buffer
```

CPU 不一定要等写操作真正写入 memory 后才能继续执行。

但 read miss 不一样，read miss 通常会直接阻塞 CPU，因为后续指令可能等待读出的数据。

所以优化策略是：

**在 write buffer 还没完全清空时，如果发生 read miss，可以优先处理 read miss。**

这样可以减少 CPU stall。

### 为什么 read 比 write 更急？

因为 read miss 位于关键路径上。

CPU 需要 read 的返回值继续执行。

而 write 通常只是把数据送出去，可以异步排队完成。

所以：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

R

</mi>

<mi>

e

</mi>

<mi>

a

</mi>

<mi>

d

</mi>

<mtext>



</mtext>

<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

</mi>

<mtext>



</mtext>

<mi>

P

</mi>

<mi>

r

</mi>

<mi>

i

</mi>

<mi>

o

</mi>

<mi>

r

</mi>

<mi>

i

</mi>

<mi>

t

</mi>

<mi>

y

</mi>

<mo>

⇒

</mo>

<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

</mi>

<mtext>



</mtext>

<mi>

P

</mi>

<mi>

e

</mi>

<mi>

n

</mi>

<mi>

a

</mi>

<mi>

l

</mi>

<mi>

t

</mi>

<mi>

y

</mi>

<mo>

↓

</mo>
</mrow>

<annotation encoding="application/x-tex">

Read\ Miss\ Priority \Rightarrow Miss\ Penalty \downarrow

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0077em;">

R

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal">

d

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

or

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

⇒

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal">

na

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

↓

</span>
</span>
</span>
</span>
</span>

更准确地说，是降低 **read miss 的有效等待时间**。

### 但这里有一个危险点

如果 write buffer 里已经有对某个地址的写入，而 read miss 正好要读同一个地址，那么不能直接绕过 write。

否则 read 可能读到旧值。

所以硬件要检查：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

R

</mi>

<mi>

e

</mi>

<mi>

a

</mi>

<mi>

d

</mi>

<mtext>



</mtext>

<mi>

A

</mi>

<mi>

d

</mi>

<mi>

d

</mi>

<mi>

r

</mi>

<mi>

e

</mi>

<mi>

s

</mi>

<mi>

s

</mi>

<mo>

=

</mo>

<mo>

=

</mo>

<mi>

W

</mi>

<mi>

r

</mi>

<mi>

i

</mi>

<mi>

t

</mi>

<mi>

e

</mi>

<mtext>



</mtext>

<mi>

B

</mi>

<mi>

u

</mi>

<mi>

f

</mi>

<mi>

f

</mi>

<mi>

e

</mi>

<mi>

r

</mi>

<mtext>



</mtext>

<mi>

A

</mi>

<mi>

d

</mi>

<mi>

d

</mi>

<mi>

r

</mi>

<mi>

e

</mi>

<mi>

s

</mi>

<mi>

s

</mi>
</mrow>

<annotation encoding="application/x-tex">

Read\ Address == Write\ Buffer\ Address

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0077em;">

R

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal">

d

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal">

A

</span>

<span className="mord,mathnormal">

dd

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal">

ess

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

==

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

W

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.0502em;">

B

</span>

<span className="mord,mathnormal">

u

</span>

<span className="mord,mathnormal" style="margin-right:0.1076em;">

f

</span>

<span className="mord,mathnormal" style="margin-right:0.1076em;">

f

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

er

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal">

A

</span>

<span className="mord,mathnormal">

dd

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal">

ess

</span>
</span>
</span>
</span>
</span>

如果不相等，read miss 可以绕过 write buffer 优先执行。

如果相等，要么等待 write 完成，要么从 write buffer forwarding 最新值。

这一页的工程直觉是：

**写可以排队，读不能乱等；但读写同地址时要保证数据一致性。**

---

## Page 121｜避免地址转换阻塞 Cache Indexing

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-100.webp)

这一页讲的是降低 hit time 的方法：**avoiding address translation during cache indexing｜避免 cache 索引等待地址转换。**

现代程序使用虚拟地址 VA，但 cache tag 或 memory 通常依赖物理地址 PA。

因此访存时通常需要：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

V

</mi>

<mi>

A

</mi>

<mo>

→

</mo>

<mi>

P

</mi>

<mi>

A

</mi>
</mrow>

<annotation encoding="application/x-tex">

VA \rightarrow PA

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.2222em;">

V

</span>

<span className="mord,mathnormal">

A

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

→

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="mord,mathnormal">

A

</span>
</span>
</span>
</span>
</span>

这个转换由 TLB 完成。

Cache 访问本身也需要做两件事：

1. 用 index 找到对应 set；
2. 比较 tag 判断 hit/miss。

如果必须等地址转换完成后再访问 cache，那么 L1 hit time 会变长。

而 L1 hit time 对 CPU 很敏感，因为 load/store 几乎每条指令流中都会频繁出现。

所以优化目标是：

**让 TLB translation 和 cache indexing 尽量并行。**

常见思想是使用：

```text
Virtually Indexed, Physically Tagged Cache
```

即用虚拟地址中不会被地址转换改变的 page offset 部分来做 index，同时用物理地址 tag 来保证正确性。

它改善的是 AMAT 中的：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

H

</mi>

<mi>

i

</mi>

<mi>

t

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

<annotation encoding="application/x-tex">

Hit\ Time

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0813em;">

H

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

t

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
</span>
</span>

也就是：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

A

</mi>

<mi>

v

</mi>

<mi>

o

</mi>

<mi>

i

</mi>

<mi>

d

</mi>

<mi>

i

</mi>

<mi>

n

</mi>

<mi>

g

</mi>

<mtext>



</mtext>

<mi>

T

</mi>

<mi>

r

</mi>

<mi>

a

</mi>

<mi>

n

</mi>

<mi>

s

</mi>

<mi>

l

</mi>

<mi>

a

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

D

</mi>

<mi>

u

</mi>

<mi>

r

</mi>

<mi>

i

</mi>

<mi>

n

</mi>

<mi>

g

</mi>

<mtext>



</mtext>

<mi>

C

</mi>

<mi>

a

</mi>

<mi>

c

</mi>

<mi>

h

</mi>

<mi>

e

</mi>

<mtext>



</mtext>

<mi>

I

</mi>

<mi>

n

</mi>

<mi>

d

</mi>

<mi>

e

</mi>

<mi>

x

</mi>

<mi>

i

</mi>

<mi>

n

</mi>

<mi>

g

</mi>

<mo>

⇒

</mo>

<mi>

H

</mi>

<mi>

i

</mi>

<mi>

t

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

↓

</mo>
</mrow>

<annotation encoding="application/x-tex">

Avoiding\ Translation\ During\ Cache\ Indexing \Rightarrow Hit\ Time \downarrow

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal">

A

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

v

</span>

<span className="mord,mathnormal">

o

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal">

in

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

g

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

T

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal">

an

</span>

<span className="mord,mathnormal">

s

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

a

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

<span className="mord,mathnormal" style="margin-right:0.0278em;">

D

</span>

<span className="mord,mathnormal">

u

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal">

in

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

g

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal">

c

</span>

<span className="mord,mathnormal">

h

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.0785em;">

I

</span>

<span className="mord,mathnormal">

n

</span>

<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal">

x

</span>

<span className="mord,mathnormal">

in

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

g

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

⇒

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0813em;">

H

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

t

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

↓

</span>
</span>
</span>
</span>
</span>

**地址转换如果串在 cache 访问前面，会拉长 L1 hit time；所以硬件要想办法并行化。**

---

## Page 122｜多级 Cache 降低 Miss Penalty

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-101.webp)

问题背景是：L1 cache 很快，但容量小。如果 L1 miss 后直接去 DRAM，代价太大。所以现代处理器一般设计为：

```text
L1 → L2 → L3 → Main Memory
```

当 L1 miss 时，不一定直接访问 DRAM，而是先查 L2。

如果 L2 hit，那么 L1 miss penalty 就大幅降低。

如果 L2 miss，再去 L3。

如果 L3 也 miss，最后才访问 DRAM。

因此多级 cache 主要优化 AMAT 中的：

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

i

</mi>

<mi>

s

</mi>

<mi>

s

</mi>

<mtext>



</mtext>

<mi>

P

</mi>

<mi>

e

</mi>

<mi>

n

</mi>

<mi>

a

</mi>

<mi>

l

</mi>

<mi>

t

</mi>

<mi>

y

</mi>
</mrow>

<annotation encoding="application/x-tex">

Miss\ Penalty

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal">

na

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

</span>
</span>
</span>
</span>
</span>

更准确地说，是降低 **L1 miss penalty**。

原来没有 L2 时：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

L

</mi>

<mn>

1

</mn>

<mtext>



</mtext>

<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

</mi>

<mtext>



</mtext>

<mi>

P

</mi>

<mi>

e

</mi>

<mi>

n

</mi>

<mi>

a

</mi>

<mi>

l

</mi>

<mi>

t

</mi>

<mi>

y

</mi>

<mo>

≈

</mo>

<mi>

D

</mi>

<mi>

R

</mi>

<mi>

A

</mi>

<mi>

M

</mi>

<mtext>



</mtext>

<mi>

A

</mi>

<mi>

c

</mi>

<mi>

c

</mi>

<mi>

e

</mi>

<mi>

s

</mi>

<mi>

s

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

<annotation encoding="application/x-tex">

L1\ Miss\ Penalty \approx DRAM\ Access\ Time

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal">

L

</span>

<span className="mord">

1

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal">

na

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

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
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

D

</span>

<span className="mord,mathnormal" style="margin-right:0.0077em;">

R

</span>

<span className="mord,mathnormal">

A

</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal">

A

</span>

<span className="mord,mathnormal">

ccess

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
</span>
</span>

有 L2 后：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

L

</mi>

<mn>

1

</mn>

<mtext>



</mtext>

<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

</mi>

<mtext>



</mtext>

<mi>

P

</mi>

<mi>

e

</mi>

<mi>

n

</mi>

<mi>

a

</mi>

<mi>

l

</mi>

<mi>

t

</mi>

<mi>

y

</mi>

<mo>

=

</mo>

<mi>

L

</mi>

<mn>

2

</mn>

<mtext>



</mtext>

<mi>

H

</mi>

<mi>

i

</mi>

<mi>

t

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

+

</mo>

<mi>

L

</mi>

<mn>

2

</mn>

<mtext>



</mtext>

<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

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

<mo>

×

</mo>

<mi>

L

</mi>

<mn>

2

</mn>

<mtext>



</mtext>

<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

</mi>

<mtext>



</mtext>

<mi>

P

</mi>

<mi>

e

</mi>

<mi>

n

</mi>

<mi>

a

</mi>

<mi>

l

</mi>

<mi>

t

</mi>

<mi>

y

</mi>
</mrow>

<annotation encoding="application/x-tex">

L1\ Miss\ Penalty = L2\ Hit\ Time + L2\ Miss\ Rate \times L2\ Miss\ Penalty

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal">

L

</span>

<span className="mord">

1

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal">

na

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

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

<span className="mord,mathnormal">

L

</span>

<span className="mord">

2

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.0813em;">

H

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

t

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

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">



</span>

<span className="mord,mathnormal">

L

</span>

<span className="mord">

2

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

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

<span className="mord,mathnormal">

L

</span>

<span className="mord">

2

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal">

na

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

</span>
</span>
</span>
</span>
</span>

所以整体 AMAT 可以写成：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

A

</mi>

<mi>

M

</mi>

<mi>

A

</mi>

<mi>

T

</mi>

<mo>

=

</mo>

<mi>

L

</mi>

<mn>

1

</mn>

<mtext>



</mtext>

<mi>

H

</mi>

<mi>

i

</mi>

<mi>

t

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

+

</mo>

<mi>

L

</mi>

<mn>

1

</mn>

<mtext>



</mtext>

<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

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

<mo>

×

</mo>

<mo stretchy="false">

(

</mo>

<mi>

L

</mi>

<mn>

2

</mn>

<mtext>



</mtext>

<mi>

H

</mi>

<mi>

i

</mi>

<mi>

t

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

+

</mo>

<mi>

L

</mi>

<mn>

2

</mn>

<mtext>



</mtext>

<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

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

<mo>

×

</mo>

<mi>

L

</mi>

<mn>

2

</mn>

<mtext>



</mtext>

<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

</mi>

<mtext>



</mtext>

<mi>

P

</mi>

<mi>

e

</mi>

<mi>

n

</mi>

<mi>

a

</mi>

<mi>

l

</mi>

<mi>

t

</mi>

<mi>

y

</mi>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

AMAT = L1\ Hit\ Time + L1\ Miss\ Rate \times (L2\ Hit\ Time + L2\ Miss\ Rate \times L2\ Miss\ Penalty)

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal">

A

</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

A

</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

T

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

<span className="mord,mathnormal">

L

</span>

<span className="mord">

1

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.0813em;">

H

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

t

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

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">



</span>

<span className="mord,mathnormal">

L

</span>

<span className="mord">

1

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

×

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

<span className="mord,mathnormal">

L

</span>

<span className="mord">

2

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.0813em;">

H

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

t

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

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">



</span>

<span className="mord,mathnormal">

L

</span>

<span className="mord">

2

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

×

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord,mathnormal">

L

</span>

<span className="mord">

2

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal">

na

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

</span>

<span className="mclose">

)

</span>
</span>
</span>
</span>
</span>

如果还有 L3，则继续嵌套：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

A

</mi>

<mi>

M

</mi>

<mi>

A

</mi>

<mi>

T

</mi>

<mo>

=

</mo>

<mi>

L

</mi>

<mn>

1

</mn>

<mtext>



</mtext>

<mi>

H

</mi>

<mi>

i

</mi>

<mi>

t

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

+

</mo>

<mi>

L

</mi>

<mn>

1

</mn>

<mtext>



</mtext>

<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

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

<mo>

×

</mo>

<mo stretchy="false">

(

</mo>

<mi>

L

</mi>

<mn>

2

</mn>

<mtext>



</mtext>

<mi>

H

</mi>

<mi>

i

</mi>

<mi>

t

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

+

</mo>

<mi>

L

</mi>

<mn>

2

</mn>

<mtext>



</mtext>

<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

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

<mo>

×

</mo>

<mo stretchy="false">

(

</mo>

<mi>

L

</mi>

<mn>

3

</mn>

<mtext>



</mtext>

<mi>

H

</mi>

<mi>

i

</mi>

<mi>

t

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

+

</mo>

<mi>

L

</mi>

<mn>

3

</mn>

<mtext>



</mtext>

<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

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

<mo>

×

</mo>

<mi>

M

</mi>

<mi>

e

</mi>

<mi>

m

</mi>

<mi>

o

</mi>

<mi>

r

</mi>

<mi>

y

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

<mo stretchy="false">

)

</mo>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

AMAT = L1\ Hit\ Time + L1\ Miss\ Rate \times (L2\ Hit\ Time + L2\ Miss\ Rate \times (L3\ Hit\ Time + L3\ Miss\ Rate \times Memory\ Time))

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal">

A

</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

A

</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

T

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

<span className="mord,mathnormal">

L

</span>

<span className="mord">

1

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.0813em;">

H

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

t

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

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">



</span>

<span className="mord,mathnormal">

L

</span>

<span className="mord">

1

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

×

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

<span className="mord,mathnormal">

L

</span>

<span className="mord">

2

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.0813em;">

H

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

t

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

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">



</span>

<span className="mord,mathnormal">

L

</span>

<span className="mord">

2

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

×

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

<span className="mord,mathnormal">

L

</span>

<span className="mord">

3

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.0813em;">

H

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

t

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

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">



</span>

<span className="mord,mathnormal">

L

</span>

<span className="mord">

3

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

×

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal">

m

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

or

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

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

<span className="mclose">

))

</span>
</span>
</span>
</span>
</span>

这一页的核心工程思想是：

**L1 负责快，L2/L3 负责兜底，主存负责容量。**

所以不同层级 cache 的设计目标不同：

<table>
<thead>
  <tr>
    <th>
      层级
    </th>
    
    <th>
      主要目标
    </th>
    
    <th>
      常见设计倾向
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      L1
    </td>
    
    <td>
      最小化 hit time
    </td>
    
    <td>
      小容量、低 associativity、快速访问
    </td>
  </tr>
  
  <tr>
    <td>
      L2
    </td>
    
    <td>
      降低 L1 miss penalty
    </td>
    
    <td>
      更大容量、更高 associativity
    </td>
  </tr>
  
  <tr>
    <td>
      L3
    </td>
    
    <td>
      减少 DRAM 访问
    </td>
    
    <td>
      更大、更慢、共享
    </td>
  </tr>
  
  <tr>
    <td>
      DRAM
    </td>
    
    <td>
      提供大容量
    </td>
    
    <td>
      慢但容量大
    </td>
  </tr>
</tbody>
</table>

## Page 123｜Local Miss Rate 与 Global Miss Rate

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-102.webp)

这一页非常重要，因为它解释多级 cache 里 miss rate 的两种定义。

### Local Miss Rate｜局部未命中率

Local miss rate 是针对某一级 cache 自己看的。

例如 L2 local miss rate：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

L

</mi>

<mn>

2

</mn>

<mtext>



</mtext>

<mi>

L

</mi>

<mi>

o

</mi>

<mi>

c

</mi>

<mi>

a

</mi>

<mi>

l

</mi>

<mtext>



</mtext>

<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

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

<mo>

=

</mo>

<mfrac>
<mrow>
<mi>

L

</mi>

<mn>

2

</mn>

<mtext>



</mtext>

<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

</mi>

<mi>

e

</mi>

<mi>

s

</mi>
</mrow>

<mrow>
<mi>

L

</mi>

<mn>

1

</mn>

<mtext>



</mtext>

<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

</mi>

<mi>

e

</mi>

<mi>

s

</mi>
</mrow>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

L2\ Local\ Miss\ Rate = \frac{L2\ Misses}{L1\ Misses}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,mathnormal">

L

</span>

<span className="mord">

2

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal">

L

</span>

<span className="mord,mathnormal">

oc

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.2173em;vertical-align:-0.345em;">



</span>

<span className="mord">
<span className="mopen,nulldelimiter">



</span>

<span className="mfrac">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.8723em;">
<span style="top:-2.655em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

L

</span>

<span className="mord,mtight">

1

</span>

<span className="mspace,mtight">
<span className="mtight">



</span>
</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal,mtight">

i

</span>

<span className="mord,mathnormal,mtight">

sses

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
<span className="mord,mathnormal,mtight">

L

</span>

<span className="mord,mtight">

2

</span>

<span className="mspace,mtight">
<span className="mtight">



</span>
</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal,mtight">

i

</span>

<span className="mord,mathnormal,mtight">

sses

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



因为只有 L1 miss 之后，才会访问 L2，所以 L2 的全部访问次数其实就是 L1 misses。

所以也可以写成：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

L

</mi>

<mn>

2

</mn>

<mtext>



</mtext>

<mi>

L

</mi>

<mi>

o

</mi>

<mi>

c

</mi>

<mi>

a

</mi>

<mi>

l

</mi>

<mtext>



</mtext>

<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

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

<mo>

=

</mo>

<mfrac>
<mrow>
<mi>

L

</mi>

<mn>

2

</mn>

<mtext>



</mtext>

<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

</mi>

<mi>

e

</mi>

<mi>

s

</mi>
</mrow>

<mrow>
<mi>

T

</mi>

<mi>

o

</mi>

<mi>

t

</mi>

<mi>

a

</mi>

<mi>

l

</mi>

<mtext>



</mtext>

<mi>

L

</mi>

<mn>

2

</mn>

<mtext>



</mtext>

<mi>

A

</mi>

<mi>

c

</mi>

<mi>

c

</mi>

<mi>

e

</mi>

<mi>

s

</mi>

<mi>

s

</mi>

<mi>

e

</mi>

<mi>

s

</mi>
</mrow>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

L2\ Local\ Miss\ Rate = \frac{L2\ Misses}{Total\ L2\ Accesses}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,mathnormal">

L

</span>

<span className="mord">

2

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal">

L

</span>

<span className="mord,mathnormal">

oc

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.2173em;vertical-align:-0.345em;">



</span>

<span className="mord">
<span className="mopen,nulldelimiter">



</span>

<span className="mfrac">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.8723em;">
<span style="top:-2.655em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.1389em;">

T

</span>

<span className="mord,mathnormal,mtight">

o

</span>

<span className="mord,mathnormal,mtight">

t

</span>

<span className="mord,mathnormal,mtight">

a

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0197em;">

l

</span>

<span className="mspace,mtight">
<span className="mtight">



</span>
</span>

<span className="mord,mathnormal,mtight">

L

</span>

<span className="mord,mtight">

2

</span>

<span className="mspace,mtight">
<span className="mtight">



</span>
</span>

<span className="mord,mathnormal,mtight">

A

</span>

<span className="mord,mathnormal,mtight">

ccesses

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
<span className="mord,mathnormal,mtight">

L

</span>

<span className="mord,mtight">

2

</span>

<span className="mspace,mtight">
<span className="mtight">



</span>
</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal,mtight">

i

</span>

<span className="mord,mathnormal,mtight">

sses

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



这个指标说明：**来到 L2 的访问中，有多少又 miss 了。**

### Global Miss Rate｜全局未命中率

Global miss rate 是站在 CPU 全部内存访问角度看的。

对于两级 cache：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

G

</mi>

<mi>

l

</mi>

<mi>

o

</mi>

<mi>

b

</mi>

<mi>

a

</mi>

<mi>

l

</mi>

<mtext>



</mtext>

<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

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

<mo>

=

</mo>

<mfrac>
<mrow>
<mi>

L

</mi>

<mn>

2

</mn>

<mtext>



</mtext>

<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

</mi>

<mi>

e

</mi>

<mi>

s

</mi>
</mrow>

<mrow>
<mi>

T

</mi>

<mi>

o

</mi>

<mi>

t

</mi>

<mi>

a

</mi>

<mi>

l

</mi>

<mtext>



</mtext>

<mi>

M

</mi>

<mi>

e

</mi>

<mi>

m

</mi>

<mi>

o

</mi>

<mi>

r

</mi>

<mi>

y

</mi>

<mtext>



</mtext>

<mi>

A

</mi>

<mi>

c

</mi>

<mi>

c

</mi>

<mi>

e

</mi>

<mi>

s

</mi>

<mi>

s

</mi>

<mi>

e

</mi>

<mi>

s

</mi>
</mrow>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

Global\ Miss\ Rate = \frac{L2\ Misses}{Total\ Memory\ Accesses}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

Gl

</span>

<span className="mord,mathnormal">

o

</span>

<span className="mord,mathnormal">

ba

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:2.2408em;vertical-align:-0.8804em;">



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

o

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal">

m

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

or

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal">

A

</span>

<span className="mord,mathnormal">

ccesses

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

L

</span>

<span className="mord">

2

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

sses

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.8804em;">
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

它也可以拆成：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

G

</mi>

<mi>

l

</mi>

<mi>

o

</mi>

<mi>

b

</mi>

<mi>

a

</mi>

<mi>

l

</mi>

<mtext>



</mtext>

<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

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

<mo>

=

</mo>

<mi>

L

</mi>

<mn>

1

</mn>

<mtext>



</mtext>

<mi>

L

</mi>

<mi>

o

</mi>

<mi>

c

</mi>

<mi>

a

</mi>

<mi>

l

</mi>

<mtext>



</mtext>

<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

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

<mo>

×

</mo>

<mi>

L

</mi>

<mn>

2

</mn>

<mtext>



</mtext>

<mi>

L

</mi>

<mi>

o

</mi>

<mi>

c

</mi>

<mi>

a

</mi>

<mi>

l

</mi>

<mtext>



</mtext>

<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

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

<annotation encoding="application/x-tex">

Global\ Miss\ Rate = L1\ Local\ Miss\ Rate \times L2\ Local\ Miss\ Rate

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

Gl

</span>

<span className="mord,mathnormal">

o

</span>

<span className="mord,mathnormal">

ba

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.7778em;vertical-align:-0.0833em;">



</span>

<span className="mord,mathnormal">

L

</span>

<span className="mord">

1

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal">

L

</span>

<span className="mord,mathnormal">

oc

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

×

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,mathnormal">

L

</span>

<span className="mord">

2

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal">

L

</span>

<span className="mord,mathnormal">

oc

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

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
</span>
</span>

因为必须先 L1 miss，然后 L2 也 miss，才会真正访问主存。

这页最容易混淆的是：

```text
L2 local miss rate 通常远大于 L2 global miss rate
```

原因是 L2 local miss rate 的分母是 L1 misses，而不是全部 memory accesses。

---

### 多级 Cache 的 AMAT 公式

两级 cache 的 AMAT 是：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

A

</mi>

<mi>

M

</mi>

<mi>

A

</mi>

<mi>

T

</mi>

<mo>

=

</mo>

<mi>

L

</mi>

<mn>

1

</mn>

<mtext>



</mtext>

<mi>

H

</mi>

<mi>

i

</mi>

<mi>

t

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

+

</mo>

<mi>

L

</mi>

<mn>

1

</mn>

<mtext>



</mtext>

<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

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

<mo>

×

</mo>

<mo stretchy="false">

(

</mo>

<mi>

L

</mi>

<mn>

2

</mn>

<mtext>



</mtext>

<mi>

H

</mi>

<mi>

i

</mi>

<mi>

t

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

+

</mo>

<mi>

L

</mi>

<mn>

2

</mn>

<mtext>



</mtext>

<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

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

<mo>

×

</mo>

<mi>

L

</mi>

<mn>

2

</mn>

<mtext>



</mtext>

<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

</mi>

<mtext>



</mtext>

<mi>

P

</mi>

<mi>

e

</mi>

<mi>

n

</mi>

<mi>

a

</mi>

<mi>

l

</mi>

<mi>

t

</mi>

<mi>

y

</mi>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

AMAT = L1\ Hit\ Time + L1\ Miss\ Rate \times (L2\ Hit\ Time + L2\ Miss\ Rate \times L2\ Miss\ Penalty)

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal">

A

</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

A

</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

T

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

<span className="mord,mathnormal">

L

</span>

<span className="mord">

1

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.0813em;">

H

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

t

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

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">



</span>

<span className="mord,mathnormal">

L

</span>

<span className="mord">

1

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

×

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

<span className="mord,mathnormal">

L

</span>

<span className="mord">

2

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.0813em;">

H

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

t

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

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">



</span>

<span className="mord,mathnormal">

L

</span>

<span className="mord">

2

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

×

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord,mathnormal">

L

</span>

<span className="mord">

2

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal">

na

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

</span>

<span className="mclose">

)

</span>
</span>
</span>
</span>
</span>

这个公式的结构要记住：

- 外层是 L1；
- L1 miss 后进入 L2；
- L2 miss 后才进入更低一级。

所以多级 AMAT 是一个嵌套结构，不是简单相加。

---

## Page 124｜多级 Cache AMAT 例子

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-103.webp)

这一页用具体数字说明多级 cache 为什么有效。

给定条件：

```text
L1 miss rate = 10%
L1 hit time = 1 cycle
L2 miss rate = 5%
L2 hit time = 10 cycles
L3 miss rate = 1%
L3 hit time = 20 cycles
Memory time = 300 cycles
```

多级 AMAT 公式：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

A

</mi>

<mi>

M

</mi>

<mi>

A

</mi>

<mi>

T

</mi>

<mo>

=

</mo>

<msub>
<mi>

T

</mi>

<mrow>
<mi>

h

</mi>

<mi>

i

</mi>

<mi>

t

</mi>
</mrow>
</msub>

<mo stretchy="false">

(

</mo>

<mi>

L

</mi>

<mn>

1

</mn>

<mo stretchy="false">

)

</mo>

<mo>

+

</mo>

<mi>

M

</mi>

<mi>

R

</mi>

<mo stretchy="false">

(

</mo>

<mi>

L

</mi>

<mn>

1

</mn>

<mo stretchy="false">

)

</mo>

<mo>

×

</mo>

<mo stretchy="false">

(

</mo>

<msub>
<mi>

T

</mi>

<mrow>
<mi>

h

</mi>

<mi>

i

</mi>

<mi>

t

</mi>
</mrow>
</msub>

<mo stretchy="false">

(

</mo>

<mi>

L

</mi>

<mn>

2

</mn>

<mo stretchy="false">

)

</mo>

<mo>

+

</mo>

<mi>

M

</mi>

<mi>

R

</mi>

<mo stretchy="false">

(

</mo>

<mi>

L

</mi>

<mn>

2

</mn>

<mo stretchy="false">

)

</mo>

<mo>

×

</mo>

<mo stretchy="false">

(

</mo>

<msub>
<mi>

T

</mi>

<mrow>
<mi>

h

</mi>

<mi>

i

</mi>

<mi>

t

</mi>
</mrow>
</msub>

<mo stretchy="false">

(

</mo>

<mi>

L

</mi>

<mn>

3

</mn>

<mo stretchy="false">

)

</mo>

<mo>

+

</mo>

<mi>

M

</mi>

<mi>

R

</mi>

<mo stretchy="false">

(

</mo>

<mi>

L

</mi>

<mn>

3

</mn>

<mo stretchy="false">

)

</mo>

<mo>

×

</mo>

<msub>
<mi>

T

</mi>

<mrow>
<mi>

m

</mi>

<mi>

e

</mi>

<mi>

m

</mi>

<mi>

o

</mi>

<mi>

r

</mi>

<mi>

y

</mi>
</mrow>
</msub>

<mo stretchy="false">

)

</mo>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

AMAT = T_{hit}(L1) + MR(L1) \times (T_{hit}(L2) + MR(L2) \times (T_{hit}(L3) + MR(L3) \times T_{memory}))

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal">

A

</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

A

</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

T

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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.1389em;">

T

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.1389em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

hi

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

<span className="mopen">

(

</span>

<span className="mord,mathnormal">

L

</span>

<span className="mord">

1

</span>

<span className="mclose">

)

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

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal" style="margin-right:0.0077em;">

R

</span>

<span className="mopen">

(

</span>

<span className="mord,mathnormal">

L

</span>

<span className="mord">

1

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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mopen">

(

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.1389em;">

T

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.1389em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

hi

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

<span className="mopen">

(

</span>

<span className="mord,mathnormal">

L

</span>

<span className="mord">

2

</span>

<span className="mclose">

)

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

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal" style="margin-right:0.0077em;">

R

</span>

<span className="mopen">

(

</span>

<span className="mord,mathnormal">

L

</span>

<span className="mord">

2

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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mopen">

(

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.1389em;">

T

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.1389em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

hi

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

<span className="mopen">

(

</span>

<span className="mord,mathnormal">

L

</span>

<span className="mord">

3

</span>

<span className="mclose">

)

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

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal" style="margin-right:0.0077em;">

R

</span>

<span className="mopen">

(

</span>

<span className="mord,mathnormal">

L

</span>

<span className="mord">

3

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
<span className="strut" style="height:1.0361em;vertical-align:-0.2861em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.1389em;">

T

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.1389em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

m

</span>

<span className="mord,mathnormal,mtight">

e

</span>

<span className="mord,mathnormal,mtight">

m

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

or

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

y

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
<span className="vlist" style="height:0.2861em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>

<span className="mclose">

))

</span>
</span>
</span>
</span>
</span>

代入：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

A

</mi>

<mi>

M

</mi>

<mi>

A

</mi>

<mi>

T

</mi>

<mo>

=

</mo>

<mn>

1

</mn>

<mo>

+

</mo>

<mn>

0.10

</mn>

<mo>

×

</mo>

<mo stretchy="false">

(

</mo>

<mn>

10

</mn>

<mo>

+

</mo>

<mn>

0.05

</mn>

<mo>

×

</mo>

<mo stretchy="false">

(

</mo>

<mn>

20

</mn>

<mo>

+

</mo>

<mn>

0.01

</mn>

<mo>

×

</mo>

<mn>

300

</mn>

<mo stretchy="false">

)

</mo>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

AMAT = 1 + 0.10 \times (10 + 0.05 \times (20 + 0.01 \times 300))

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal">

A

</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

A

</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

T

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
<span className="strut" style="height:0.7278em;vertical-align:-0.0833em;">



</span>

<span className="mord">

1

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
<span className="strut" style="height:0.7278em;vertical-align:-0.0833em;">



</span>

<span className="mord">

0.10

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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mopen">

(

</span>

<span className="mord">

10

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
<span className="strut" style="height:0.7278em;vertical-align:-0.0833em;">



</span>

<span className="mord">

0.05

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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mopen">

(

</span>

<span className="mord">

20

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
<span className="strut" style="height:0.7278em;vertical-align:-0.0833em;">



</span>

<span className="mord">

0.01

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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord">

300

</span>

<span className="mclose">

))

</span>
</span>
</span>
</span>
</span>

先算 L3 部分：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mn>

20

</mn>

<mo>

+

</mo>

<mn>

0.01

</mn>

<mo>

×

</mo>

<mn>

300

</mn>

<mo>

=

</mo>

<mn>

23

</mn>
</mrow>

<annotation encoding="application/x-tex">

20 + 0.01 \times 300 = 23

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.7278em;vertical-align:-0.0833em;">



</span>

<span className="mord">

20

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
<span className="strut" style="height:0.7278em;vertical-align:-0.0833em;">



</span>

<span className="mord">

0.01

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

300

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

23

</span>
</span>
</span>
</span>
</span>

再算 L2 部分：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mn>

10

</mn>

<mo>

+

</mo>

<mn>

0.05

</mn>

<mo>

×

</mo>

<mn>

23

</mn>

<mo>

=

</mo>

<mn>

11.15

</mn>
</mrow>

<annotation encoding="application/x-tex">

10 + 0.05 \times 23 = 11.15

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.7278em;vertical-align:-0.0833em;">



</span>

<span className="mord">

10

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
<span className="strut" style="height:0.7278em;vertical-align:-0.0833em;">



</span>

<span className="mord">

0.05

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

23

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

11.15

</span>
</span>
</span>
</span>
</span>

最后算 L1：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mn>

1

</mn>

<mo>

+

</mo>

<mn>

0.10

</mn>

<mo>

×

</mo>

<mn>

11.15

</mn>

<mo>

=

</mo>

<mn>

2.115

</mn>
</mrow>

<annotation encoding="application/x-tex">

1 + 0.10 \times 11.15 = 2.115

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.7278em;vertical-align:-0.0833em;">



</span>

<span className="mord">

1

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
<span className="strut" style="height:0.7278em;vertical-align:-0.0833em;">



</span>

<span className="mord">

0.10

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

11.15

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

2.115

</span>
</span>
</span>
</span>
</span>

所以：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

A

</mi>

<mi>

M

</mi>

<mi>

A

</mi>

<mi>

T

</mi>

<mo>

=

</mo>

<mn>

2.115

</mn>

<mtext>



</mtext>

<mi>

c

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

s

</mi>
</mrow>

<annotation encoding="application/x-tex">

AMAT = 2.115\ cycles

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal">

A

</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

A

</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

T

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
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord">

2.115

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

cy

</span>

<span className="mord,mathnormal">

c

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

es

</span>
</span>
</span>
</span>
</span>

如果没有多级 cache，L1 miss 后直接去 memory：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

A

</mi>

<mi>

M

</mi>

<mi>

A

</mi>

<mi>

T

</mi>

<mo>

=

</mo>

<mn>

1

</mn>

<mo>

+

</mo>

<mn>

0.10

</mn>

<mo>

×

</mo>

<mn>

300

</mn>

<mo>

=

</mo>

<mn>

31

</mn>

<mtext>



</mtext>

<mi>

c

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

s

</mi>
</mrow>

<annotation encoding="application/x-tex">

AMAT = 1 + 0.10 \times 300 = 31\ cycles

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal">

A

</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

A

</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

T

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
<span className="strut" style="height:0.7278em;vertical-align:-0.0833em;">



</span>

<span className="mord">

1

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
<span className="strut" style="height:0.7278em;vertical-align:-0.0833em;">



</span>

<span className="mord">

0.10

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

300

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
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord">

31

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

cy

</span>

<span className="mord,mathnormal">

c

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

es

</span>
</span>
</span>
</span>
</span>

加速比：

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

31

</mn>

<mn>

2.115

</mn>
</mfrac>

<mo>

≈

</mo>

<mn>

14.7

</mn>
</mrow>

<annotation encoding="application/x-tex">

Speedup = \frac{31}{2.115} \approx 14.7

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

2.115

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

31

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

14.7

</span>
</span>
</span>
</span>
</span>

这一页的重点是：
**多级 cache 对 AMAT 的改善非常大，因为它显著降低了 L1 miss 后的平均代价。**

---

## Page 125｜多级 Cache 的设计考虑

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-104.webp)

这一页讲 L1、L2、L3 的设计目标不同。

### L1 Cache：追求 Hit Time

L1 cache 离 CPU 最近，每次取指、load/store 都可能访问它。

所以 L1 的第一目标是：

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

i

</mi>

<mi>

n

</mi>

<mi>

i

</mi>

<mi>

m

</mi>

<mi>

i

</mi>

<mi>

z

</mi>

<mi>

e

</mi>

<mtext>



</mtext>

<mi>

H

</mi>

<mi>

i

</mi>

<mi>

t

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

<annotation encoding="application/x-tex">

Minimize\ Hit\ Time

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

<span className="mord,mathnormal">

inimi

</span>

<span className="mord,mathnormal" style="margin-right:0.044em;">

z

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.0813em;">

H

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

t

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
</span>
</span>

因此 L1 通常设计得：

- 小；
- 快；
- associativity 不会过高；
- block size 不会过大；
- pipeline 关键路径尽量短。

即使 L1 miss rate 稍微高一点也可以接受，因为后面有 L2 兜底。

---

### L2 / L3 Cache：追求 Miss Rate

L2 和 L3 不在 CPU 最关键 hit path 上，所以它们可以牺牲一些 hit time 来换更低 miss rate。

因此 L2/L3 通常设计得：

- 更大；
- associativity 更高；
- block size 可能更大；
- hit time 比 L1 长；
- 但能显著减少访问 DRAM 的次数。

L2 hit time 会成为 L1 miss penalty 的一部分：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

L

</mi>

<mn>

1

</mn>

<mtext>



</mtext>

<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

</mi>

<mtext>



</mtext>

<mi>

P

</mi>

<mi>

e

</mi>

<mi>

n

</mi>

<mi>

a

</mi>

<mi>

l

</mi>

<mi>

t

</mi>

<mi>

y

</mi>

<mo>

=

</mo>

<mi>

L

</mi>

<mn>

2

</mn>

<mtext>



</mtext>

<mi>

H

</mi>

<mi>

i

</mi>

<mi>

t

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

+

</mo>

<mi>

L

</mi>

<mn>

2

</mn>

<mtext>



</mtext>

<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

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

<mo>

×

</mo>

<mi>

L

</mi>

<mn>

2

</mn>

<mtext>



</mtext>

<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

</mi>

<mtext>



</mtext>

<mi>

P

</mi>

<mi>

e

</mi>

<mi>

n

</mi>

<mi>

a

</mi>

<mi>

l

</mi>

<mi>

t

</mi>

<mi>

y

</mi>
</mrow>

<annotation encoding="application/x-tex">

L1\ Miss\ Penalty = L2\ Hit\ Time + L2\ Miss\ Rate \times L2\ Miss\ Penalty

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal">

L

</span>

<span className="mord">

1

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal">

na

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

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

<span className="mord,mathnormal">

L

</span>

<span className="mord">

2

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.0813em;">

H

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

t

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

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">



</span>

<span className="mord,mathnormal">

L

</span>

<span className="mord">

2

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

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

<span className="mord,mathnormal">

L

</span>

<span className="mord">

2

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal">

na

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

</span>
</span>
</span>
</span>
</span>

所以 L2 也不能太慢，但它不像 L1 那样极端追求 hit time。

---

### 本页核心

L1 和 L2 的设计不是同一个目标。

```text
L1：快最重要
L2/L3：减少主存访问最重要
```

所以不能简单说“cache 越大越好”。

对 L1 来说，太大可能拖慢 hit time；对 L2/L3 来说，更大更高 associativity 往往更有价值。

---

## Page 126｜典型多级 Cache 结构

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-105.webp)

这一页给出一个典型层次：

```text
L1 Cache: 32KB I$, 32KB D$
L2 Cache: 256KB
L3 Cache: 4MB
```

这里的重点不是死记容量，而是看出不同层级的设计趋势。

### L1 分成 I$  和 D$

L1 通常分为：

- Instruction Cache，简称 I$；
- Data Cache，简称 D$。

这样做可以减少取指和访存之间的结构冲突。

在流水线里，IF 阶段要访问 instruction memory，MEM 阶段可能访问 data memory。

如果只有一个统一 L1 cache，就可能出现 structural hazard。

所以 L1 分离 I<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mtext>

和

</mtext>

<mi>

D

</mi>
</mrow>

<annotation encoding="application/x-tex">

和 D

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,cjk_fallback">

和

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

D

</span>
</span>
</span>
</span>

 的好处是：

```text
取指和数据访问可以并行
```

---

### L2 / L3 通常统一

L2、L3 更大，通常不再严格区分 instruction 和 data。

它们主要负责给 L1 miss 兜底。

这一页还出现 “Cache Buster”，可以理解为一种会破坏 cache locality 的访问模式。

例如：

- 工作集远大于 cache；
- stride 访问刚好不断冲突；
- 随机访问；
- 访问数据几乎没有 temporal locality。

这类程序会让 cache 难以发挥作用。

---

## Page 128｜CPI / Miss Rate / DRAM Access 的关系

这一页用 SPECInt2006 的数据展示 cache miss 对性能的影响。

图里有几个指标：

- CPI；
- miss rate；
- DRAM accesses；
- instructions and data；
- data only。

这一页的重点不是记具体数值，而是理解趋势：

```text
Miss rate 越高，DRAM accesses 越多，CPI 越容易升高。
```

因为 DRAM access 会引入长延迟，导致 pipeline stall。

如果一个程序 cache locality 很差，就会产生更多 L1/L2/L3 miss，最终访问 DRAM。

DRAM 访问次数多了之后，CPU 即使计算单元很强，也会因为等待数据而变慢。

所以性能不只取决于 ALU 或主频，也强烈取决于 memory behavior。

可以用下面这种思路理解：

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

<annotation encoding="application/x-tex">

CPU\ Time = Instruction\ Count \times CPI \times Cycle\ Time

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
</span>
</span>

cache miss 会增加 CPI：

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

I

</mi>

<mo>

=

</mo>

<mi>

B

</mi>

<mi>

a

</mi>

<mi>

s

</mi>

<mi>

e

</mi>

<mtext>



</mtext>

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

+

</mo>

<mi>

M

</mi>

<mi>

e

</mi>

<mi>

m

</mi>

<mi>

o

</mi>

<mi>

r

</mi>

<mi>

y

</mi>

<mtext>



</mtext>

<mi>

S

</mi>

<mi>

t

</mi>

<mi>

a

</mi>

<mi>

l

</mi>

<mi>

l

</mi>

<mtext>



</mtext>

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

s

</mi>

<mtext>



</mtext>

<mi>

P

</mi>

<mi>

e

</mi>

<mi>

r

</mi>

<mtext>



</mtext>

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
</mrow>

<annotation encoding="application/x-tex">

CPI = Base\ CPI + Memory\ Stall\ Cycles\ Per\ Instruction

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

<span className="mord,mathnormal" style="margin-right:0.0785em;">

I

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

<span className="mord,mathnormal" style="margin-right:0.0502em;">

B

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal">

se

</span>

<span className="mspace">



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

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal">

m

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

or

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.0576em;">

S

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mspace">



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

es

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

er

</span>

<span className="mspace">



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
</span>
</span>
</span>
</span>

而 memory stall 又和 miss rate、miss penalty 有关：

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

e

</mi>

<mi>

m

</mi>

<mi>

o

</mi>

<mi>

r

</mi>

<mi>

y

</mi>

<mtext>



</mtext>

<mi>

S

</mi>

<mi>

t

</mi>

<mi>

a

</mi>

<mi>

l

</mi>

<mi>

l

</mi>

<mo>

≈

</mo>

<mi>

M

</mi>

<mi>

e

</mi>

<mi>

m

</mi>

<mi>

o

</mi>

<mi>

r

</mi>

<mi>

y

</mi>

<mtext>



</mtext>

<mi>

A

</mi>

<mi>

c

</mi>

<mi>

c

</mi>

<mi>

e

</mi>

<mi>

s

</mi>

<mi>

s

</mi>

<mi>

e

</mi>

<mi>

s

</mi>

<mtext>



</mtext>

<mi>

P

</mi>

<mi>

e

</mi>

<mi>

r

</mi>

<mtext>



</mtext>

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

<mo>

×

</mo>

<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

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

<mo>

×

</mo>

<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

</mi>

<mtext>



</mtext>

<mi>

P

</mi>

<mi>

e

</mi>

<mi>

n

</mi>

<mi>

a

</mi>

<mi>

l

</mi>

<mi>

t

</mi>

<mi>

y

</mi>
</mrow>

<annotation encoding="application/x-tex">

Memory\ Stall \approx Memory\ Accesses\ Per\ Instruction \times Miss\ Rate \times Miss\ Penalty

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal">

m

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

or

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.0576em;">

S

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

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

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal">

m

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

or

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal">

A

</span>

<span className="mord,mathnormal">

ccesses

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

er

</span>

<span className="mspace">



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

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

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

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal">

na

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

</span>
</span>
</span>
</span>
</span>

这页就是在强调：
**cache miss 最终会体现在 CPI 上。**

---

## Page 130｜使用 Write-Through 处理 Store

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-106.webp)

这一页进入 **写策略 Write Policy**。

store 指令会改变 memory value。

问题是：cache 里有一份数据，memory 里也有一份数据，那么写入时应该更新谁？

第一种策略是：

```text
Write-Through Policy｜透写策略
```

也就是：

```text
写 cache 的同时，也写 memory
```

这样 cache 和 memory 总是保持一致。

---

### Write-through 的优点

write-through 最大的优点是简单。

因为每次写入都会最终进入 memory，所以 memory 里总有最新副本。

这对一致性、调试、异常恢复都比较友好。

可以理解为：

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

a

</mi>

<mi>

c

</mi>

<mi>

h

</mi>

<mi>

e

</mi>

<mtext>



</mtext>

<mi>

D

</mi>

<mi>

a

</mi>

<mi>

t

</mi>

<mi>

a

</mi>

<mo>

=

</mo>

<mi>

M

</mi>

<mi>

e

</mi>

<mi>

m

</mi>

<mi>

o

</mi>

<mi>

r

</mi>

<mi>

y

</mi>

<mtext>



</mtext>

<mi>

D

</mi>

<mi>

a

</mi>

<mi>

t

</mi>

<mi>

a

</mi>
</mrow>

<annotation encoding="application/x-tex">

Cache\ Data = Memory\ Data

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal">

c

</span>

<span className="mord,mathnormal">

h

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

D

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal">

a

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
<span className="strut" style="height:0.8778em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal">

m

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

or

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

D

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal">

a

</span>
</span>
</span>
</span>
</span>

至少在写完成后成立。

---

### Write-through 的缺点

缺点是慢。

如果每次 store 都要等 memory 写完，CPU 会频繁 stall。

所以需要：

```text
Write Buffer｜写缓冲区
```

CPU 写 cache 后，把写 memory 的请求放入 write buffer。

CPU 可以继续执行，write buffer 在后台慢慢把数据写到 memory。

所以 write-through 通常和 write buffer 一起使用。

<mark>

**注意：写入 cache 的目的不是让 cache 自己主动写 memory，而是为了让 CPU 后续再读这个地址时，能立刻读到最新值，并且保持 cache 里的副本不变旧。**

</mark>



---

## Page 131｜Write-Through Cache 与 Write Buffer

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-107.webp)

这一页画出了 write-through cache 的结构。

写命中时：

```text
CPU → Cache
CPU → Write Buffer → Memory
```

也就是说，数据既写 cache，也进入 write buffer，最后写到 memory。

write buffer 的作用是吸收写流量，避免 CPU 每次 store 都等待主存。

### Write Buffer 的意义

如果没有 write buffer：

```text
store → 等待 memory 写完 → 继续执行
```

如果有 write buffer：

```text
store → 放入 buffer → CPU 继续执行
```

因此 write buffer 可以降低 store 对流水线的阻塞。

---

### Write Miss 怎么办？

这一页最后问：

```text
If cache write miss 怎么办？
```

这就引出后面的 write allocation。

在 write miss 时有两种选择：

1. **Write Allocate**
先把 block 读入 cache，再写 cache。
2. **No Write Allocate**
不把 block 读入 cache，直接写 memory。

write-through 常见组合是：

```text
Write-through + No-write-allocate
```

因为既然每次写都要去 memory，那么 write miss 时不一定值得把整块读进 cache。

---

## Page 132｜使用 Write-Back 处理 Store

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-108.webp)

这一页讲第二种写策略：

```text
Write-Back Policy｜回写策略
```

write-back 的思想是：

```text
写命中时只写 cache，不立刻写 memory
```

memory 里的数据可能暂时是旧的。

只有当这个 cache block 被 eviction 时，才把它写回 memory。

---

### Dirty Bit｜脏位

为了知道一个 block 是否被修改过，需要给每个 cache block 增加一个：

```text
Dirty Bit
```

dirty bit 的含义是：

```text
dirty = 0：cache block 和 memory 一致
dirty = 1：cache block 被修改过，memory 中是旧值
```

如果 dirty block 被替换，就必须写回 memory。

如果 clean block 被替换，可以直接丢弃，因为 memory 里已经有一样的数据。

---

### Write-back 的优点

write-back 可以减少 memory write traffic。

如果一个 block 被多次写入：

```text
write a[0]
write a[1]
write a[2]
write a[3]
```

write-through 可能产生多次 memory write。

write-back 可以把多次写合并，最后 eviction 时只写回一次 block。

所以：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

W

</mi>

<mi>

r

</mi>

<mi>

i

</mi>

<mi>

t

</mi>

<mi>

e

</mi>

<mtext>



</mtext>

<mi>

T

</mi>

<mi>

r

</mi>

<mi>

a

</mi>

<mi>

f

</mi>

<mi>

f

</mi>

<mi>

i

</mi>

<mi>

c

</mi>

<mo>

↓

</mo>
</mrow>

<annotation encoding="application/x-tex">

Write\ Traffic \downarrow

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

W

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

T

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal" style="margin-right:0.1076em;">

f

</span>

<span className="mord,mathnormal" style="margin-right:0.1076em;">

f

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

c

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

↓

</span>
</span>
</span>
</span>
</span>

---

### Write-back 的代价

代价是控制逻辑复杂。

因为每次 miss 替换时要判断 victim block 是否 dirty：

```text
dirty = 1 → write back old block，再读入 new block
dirty = 0 → 直接替换
```

所以一次 miss 可能触发额外写回。

---

## Page 133｜Write-Back Cache 的行为

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-109.webp)

这一页具体列出 write-back cache 的几种情况。

### Store Hit

store 命中时：

```text
只写 cache
设置 dirty bit
memory 暂时不更新
```

也就是：

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

t

</mi>

<mi>

o

</mi>

<mi>

r

</mi>

<mi>

e

</mi>

<mtext>



</mtext>

<mi>

H

</mi>

<mi>

i

</mi>

<mi>

t

</mi>

<mo>

⇒

</mo>

<mi>

C

</mi>

<mi>

a

</mi>

<mi>

c

</mi>

<mi>

h

</mi>

<mi>

e

</mi>

<mtext>



</mtext>

<mi>

U

</mi>

<mi>

p

</mi>

<mi>

d

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

<mi>

d

</mi>

<mo separator="true">

,

</mo>

<mtext>



</mtext>

<mi>

D

</mi>

<mi>

i

</mi>

<mi>

r

</mi>

<mi>

t

</mi>

<mi>

y

</mi>

<mo>

=

</mo>

<mn>

1

</mn>
</mrow>

<annotation encoding="application/x-tex">

Store\ Hit \Rightarrow Cache\ Updated,\ Dirty = 1

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0576em;">

S

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

or

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.0813em;">

H

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

⇒

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal">

c

</span>

<span className="mord,mathnormal">

h

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

U

</span>

<span className="mord,mathnormal">

p

</span>

<span className="mord,mathnormal">

d

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

<span className="mord,mathnormal">

d

</span>

<span className="mpunct">

,

</span>

<span className="mspace">



</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

D

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

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

1

</span>
</span>
</span>
</span>
</span>

---

### Store Miss

课件这里采用的是：

```text
Write Allocate
```

也就是 store miss 时：

1. 先从 memory 把 block 读入 cache；
2. 再修改 cache 中对应位置；
3. 设置 dirty bit。

所以：

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

t

</mi>

<mi>

o

</mi>

<mi>

r

</mi>

<mi>

e

</mi>

<mtext>



</mtext>

<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

</mi>

<mo>

⇒

</mo>

<mi>

F

</mi>

<mi>

e

</mi>

<mi>

t

</mi>

<mi>

c

</mi>

<mi>

h

</mi>

<mtext>



</mtext>

<mi>

B

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

<mo>

+

</mo>

<mi>

W

</mi>

<mi>

r

</mi>

<mi>

i

</mi>

<mi>

t

</mi>

<mi>

e

</mi>

<mtext>



</mtext>

<mi>

C

</mi>

<mi>

a

</mi>

<mi>

c

</mi>

<mi>

h

</mi>

<mi>

e

</mi>

<mo>

+

</mo>

<mi>

S

</mi>

<mi>

e

</mi>

<mi>

t

</mi>

<mtext>



</mtext>

<mi>

D

</mi>

<mi>

i

</mi>

<mi>

r

</mi>

<mi>

t

</mi>

<mi>

y

</mi>
</mrow>

<annotation encoding="application/x-tex">

Store\ Miss \Rightarrow Fetch\ Block + Write\ Cache + Set\ Dirty

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0576em;">

S

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

or

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

⇒

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.7778em;vertical-align:-0.0833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

F

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal">

c

</span>

<span className="mord,mathnormal">

h

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.0502em;">

B

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.7778em;vertical-align:-0.0833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

W

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal">

c

</span>

<span className="mord,mathnormal">

h

</span>

<span className="mord,mathnormal">

e

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
<span className="strut" style="height:0.8778em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0576em;">

S

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

D

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

</span>
</span>
</span>
</span>
</span>

---

### Load Hit

load 命中时直接从 cache 读。

```text
Load hit → use cache value
```

---

### Any Miss

任何 miss 需要替换 block 时：

- 如果 victim block 是 clean，直接丢弃；
- 如果 victim block 是 dirty，必须先 write back。

所以 write-back 的 miss penalty 不是固定的。

可能是：

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

i

</mi>

<mi>

s

</mi>

<mi>

s

</mi>

<mtext>



</mtext>

<mi>

P

</mi>

<mi>

e

</mi>

<mi>

n

</mi>

<mi>

a

</mi>

<mi>

l

</mi>

<mi>

t

</mi>

<mi>

y

</mi>

<mo>

=

</mo>

<mi>

R

</mi>

<mi>

e

</mi>

<mi>

a

</mi>

<mi>

d

</mi>

<mtext>



</mtext>

<mi>

N

</mi>

<mi>

e

</mi>

<mi>

w

</mi>

<mtext>



</mtext>

<mi>

B

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
</mrow>

<annotation encoding="application/x-tex">

Miss\ Penalty = Read\ New\ Block

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal">

na

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

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
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0077em;">

R

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal">

d

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

N

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal" style="margin-right:0.0269em;">

w

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.0502em;">

B

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
</span>
</span>
</span>
</span>

也可能是：

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

i

</mi>

<mi>

s

</mi>

<mi>

s

</mi>

<mtext>



</mtext>

<mi>

P

</mi>

<mi>

e

</mi>

<mi>

n

</mi>

<mi>

a

</mi>

<mi>

l

</mi>

<mi>

t

</mi>

<mi>

y

</mi>

<mo>

=

</mo>

<mi>

W

</mi>

<mi>

r

</mi>

<mi>

i

</mi>

<mi>

t

</mi>

<mi>

e

</mi>

<mtext>



</mtext>

<mi>

B

</mi>

<mi>

a

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

D

</mi>

<mi>

i

</mi>

<mi>

r

</mi>

<mi>

t

</mi>

<mi>

y

</mi>

<mtext>



</mtext>

<mi>

V

</mi>

<mi>

i

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

m

</mi>

<mo>

+

</mo>

<mi>

R

</mi>

<mi>

e

</mi>

<mi>

a

</mi>

<mi>

d

</mi>

<mtext>



</mtext>

<mi>

N

</mi>

<mi>

e

</mi>

<mi>

w

</mi>

<mtext>



</mtext>

<mi>

B

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
</mrow>

<annotation encoding="application/x-tex">

Miss\ Penalty = Write\ Back\ Dirty\ Victim + Read\ New\ Block

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal">

na

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

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
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

W

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.0502em;">

B

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal">

c

</span>

<span className="mord,mathnormal" style="margin-right:0.0315em;">

k

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

D

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.2222em;">

V

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

c

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal">

im

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
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0077em;">

R

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal">

d

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

N

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal" style="margin-right:0.0269em;">

w

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.0502em;">

B

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
</span>
</span>
</span>
</span>

这就是 write-back 比 write-through 更复杂的地方。

---

## Page 134｜Write-Through vs Write-Back

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-110.webp)

这一页对比两种写策略。

### Write-Through｜透写

优点：

- 控制逻辑简单；
- memory 总是有最新数据；
- 访问行为更可预测；
- 更容易处理异常、调试、一致性。

缺点：

- memory write traffic 高；
- 如果没有 write buffer，会很慢；
- write buffer 满了以后 CPU 仍然会 stall。

可以总结为：

```text
Write-through：简单，但写流量大
```

---

### Write-Back｜回写

优点：

- 减少 memory write traffic；
- 多次写可以合并；
- 对写密集程序更高效。

缺点：

- 控制逻辑复杂；
- 需要 dirty bit；
- miss 时可能要先写回 victim block；
- memory 可能不是最新值；
- 可靠性、一致性处理更麻烦。

可以总结为：

```text
Write-back：高效，但复杂
```

---

### 本页核心权衡

write-through 和 write-back 本质是在权衡：

```text
简单性 vs 写流量
```

如果系统追求简单和确定性，write-through 更容易。

如果系统追求性能和带宽效率，write-back 更常见。

---

## Page 135｜Write Policy Choices

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-111.webp)

这一页把写策略分成两个维度。

### 维度一：Cache Hit 时怎么写？

#### Write-through

写 hit 时：

```text
写 cache + 写 memory
```

特点：

```text
简单，但 memory traffic 高
```

#### Write-back

写 hit 时：

```text
只写 cache，设置 dirty bit
```

特点：

```text
memory traffic 低，但控制复杂
```

---

### 维度二：Cache Miss 时怎么写？

#### No Write Allocate

write miss 时不把 block 调入 cache，直接写 memory。

```text
Write miss → write memory only
```

适合 write-through。

因为 write-through 本来就要写 memory，没有必要为了一个 store miss 再读整块进 cache。

---

#### Write Allocate

write miss 时先把 block 调入 cache，再写 cache。

```text
Write miss → fetch block into cache → write cache
```

适合 write-back。

因为 write-back 的思想是后续写都在 cache 中合并，所以先把 block 拉进 cache 是合理的。

---

### 常见组合

最常见的组合是：

```text
Write-through + No-write-allocate
Write-back + Write-allocate
```

原因是它们逻辑匹配。

<table>
<thead>
  <tr>
    <th>
      写策略组合
    </th>
    
    <th>
      适合原因
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      Write-through + No-write-allocate
    </td>
    
    <td>
      miss 时直接写 memory，简单
    </td>
  </tr>
  
  <tr>
    <td>
      Write-back + Write-allocate
    </td>
    
    <td>
      把 block 拉进 cache，后续写可以合并
    </td>
  </tr>
</tbody>
</table>

这一页的重点是：
**write hit policy 和 write miss policy 是两个独立维度，但实际设计中有常见搭配。**

---

## Page 136｜Inclusion Policy｜多级 Cache 包含策略

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-112.webp)

这一页讲多级 cache 之间的数据包含关系。

### Inclusive Cache｜包含式缓存

Inclusive multilevel cache 的规则是：

```text
如果某个 block 在 L1 中，那么它也必须在 L2/L3 中
```

也就是外层 cache 包含内层 cache 的内容。

可以理解为：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

L

</mi>

<mn>

1

</mn>

<mo>

⊆

</mo>

<mi>

L

</mi>

<mn>

2

</mn>

<mo>

⊆

</mo>

<mi>

L

</mi>

<mn>

3

</mn>
</mrow>

<annotation encoding="application/x-tex">

L1 \subseteq L2 \subseteq L3

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8193em;vertical-align:-0.136em;">



</span>

<span className="mord,mathnormal">

L

</span>

<span className="mord">

1

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

⊆

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8193em;vertical-align:-0.136em;">



</span>

<span className="mord,mathnormal">

L

</span>

<span className="mord">

2

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

⊆

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal">

L

</span>

<span className="mord">

3

</span>
</span>
</span>
</span>
</span>

优点是 coherence 简单。

如果外部设备或其他 core 要检查某个 block 是否被缓存，只需要检查最外层 cache。

例如检查 L3，就能知道 L1/L2 中是否可能存在这条 cache line。

缺点是容量有重复。

同一个 block 同时存在 L1、L2、L3，有效容量被浪费一部分。

---

### Exclusive Cache｜独占式缓存

Exclusive cache 的规则是：

```text
L1 中有的 block，L2 中不一定有
```

甚至设计目标是尽量不重复存储。

优点是有效容量更大。

L1 和 L2 可以存不同数据，总可用 cache 容量更高。

缺点是管理复杂。

L1 miss 时，可能要在 L1 和 L2 之间交换 blocks。

cache coherence 和替换逻辑也更麻烦。

---

### 本页核心权衡

```text
Inclusive：简单，但容量重复
Exclusive：容量利用高，但控制复杂
```

这也是典型 cache 设计风格：

不是单纯追求容量最大，而是在硬件复杂度、一致性、性能之间权衡。

---

## Page 137｜Write Performance｜写性能路径

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-113.webp)

这一页回到 cache 写操作本身。

图里是在 direct-mapped cache 结构上加了：

```text
WE = Write Enable
```

写操作和读操作不同。

读操作只需要判断 hit，然后把 data 返回 CPU。

写操作需要判断 hit 后，再决定是否允许写入 data array。

关键问题是：

```text
写 cache 时，必须先知道是不是 hit。
```

因为如果 miss 时直接写 data array，可能会破坏原来的 cache block。

所以写命中的关键路径一般是：

```text
Tag lookup → Hit decision → Enable write
```

这会影响 write hit time。

如果这个流程需要两个周期，就会影响 store 性能。

这一页为后面的 “Reducing Write Hit Time” 做铺垫。

---

## Page 138｜Reducing Write Hit Time｜减少写命中时间

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-114.webp)

这一页讲写命中的性能问题。

### 问题

写操作可能需要两个周期：

1. 第一个周期：tag check，判断是否 hit；
2. 第二个周期：如果 hit，再写 data array。

原因是不能在不知道 hit/miss 的情况下随便写 cache data。

否则 write miss 时可能误写了错误位置。

所以问题是：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

W

</mi>

<mi>

r

</mi>

<mi>

i

</mi>

<mi>

t

</mi>

<mi>

e

</mi>

<mtext>



</mtext>

<mi>

H

</mi>

<mi>

i

</mi>

<mi>

t

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

↑

</mo>
</mrow>

<annotation encoding="application/x-tex">

Write\ Hit\ Time \uparrow

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

W

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.0813em;">

H

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

t

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

↑

</span>
</span>
</span>
</span>
</span>

---

### 解决方案一：支持单周期读写并能恢复

设计一种 data memory，使它可以在一个周期内写入。

如果之后发现 miss，就恢复旧值。

这需要额外硬件支持，复杂度较高。

---

### 解决方案二：CAM Tag / Fully Associative 思路

如果 tag 用 CAM 方式匹配，可以只在 hit 的 wordline 上启用写入。

这样减少误写风险。

但 CAM 硬件昂贵，不适合大容量普通 cache。

---

### 解决方案三：Pipelined Write｜流水线写

这是更实用的思想。

把 store data 和 address 先放在 buffer 里，延迟到下一个阶段写入 data array。

也就是：

```text
当前周期做 tag check
下个周期真正写 data
```

这样 cache 可以保持流水化，不必让 CPU 完全停住。

---

### 本页核心

减少 write hit time 的难点在于：

```text
写入动作必须等待 hit 判断
```

所以优化方向就是让 tag check 和 data write 尽量重叠或流水化。

---

## Page 139｜Pipelining Cache Writes｜流水线缓存写

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-115.webp)

这一页具体展示流水线写 cache 的结构。

核心思想是：

```text
store 的 tag check 和 data write 分成两个阶段
```

当 cache 正在检查下一条 store 的 tag 时，上一条 store 的 data 可以写入 data array。

也就是说：

```text
Cycle n：检查 store A 是否 hit
Cycle n+1：写 store A 的 data，同时检查 store B 的 tag
```

这样可以提高吞吐率。

---

### 为什么需要 Delayed Write Buffer？

图里有：

```text
Delayed Write Data
Delayed Write Addr
```

这是因为真正写 data array 的时候，需要保存上一条 store 的地址和数据。

它相当于一个小的 pipeline register。

---

### Load/Store 冲突

流水线写还需要处理 load/store hazard。

例如：

```text
store x
load x
```

如果 store 还在 delayed write buffer 里，load 直接读 cache 可能读到旧值。

所以硬件要做 forwarding 或 stall。

这和流水线数据相关类似，本质是 memory system 内部的数据相关。

---

### 本页核心

pipelined write 的目标是：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

W

</mi>

<mi>

r

</mi>

<mi>

i

</mi>

<mi>

t

</mi>

<mi>

e

</mi>

<mtext>



</mtext>

<mi>

T

</mi>

<mi>

h

</mi>

<mi>

r

</mi>

<mi>

o

</mi>

<mi>

u

</mi>

<mi>

g

</mi>

<mi>

h

</mi>

<mi>

p

</mi>

<mi>

u

</mi>

<mi>

t

</mi>

<mo>

↑

</mo>
</mrow>

<annotation encoding="application/x-tex">

Write\ Throughput \uparrow

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

W

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

T

</span>

<span className="mord,mathnormal">

h

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal">

o

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

ug

</span>

<span className="mord,mathnormal">

h

</span>

<span className="mord,mathnormal">

p

</span>

<span className="mord,mathnormal">

u

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

↑

</span>
</span>
</span>
</span>
</span>

但代价是：

```text
控制逻辑更复杂，需要处理 load-store ordering 和 forwarding
```

---

## Page 140｜Write Buffer 减少 Read Miss Penalty

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-116.webp)

这一页把 write buffer 和 read miss 结合起来。

write buffer 的基本作用是：

```text
CPU 写入后不等 memory，先把写请求放入 buffer
```

这样 store 不会立刻阻塞 CPU。

但更重要的是：

如果发生 read miss，read miss 应该可以绕过 write buffer 先去访问下一级 cache/memory。

因为 read miss 通常在 CPU 关键路径上。

CPU 等不到 read data，就不能继续执行依赖指令。

所以优化是：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

R

</mi>

<mi>

e

</mi>

<mi>

a

</mi>

<mi>

d

</mi>

<mtext>



</mtext>

<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

</mi>

<mtext>



</mtext>

<mi>

P

</mi>

<mi>

r

</mi>

<mi>

i

</mi>

<mi>

o

</mi>

<mi>

r

</mi>

<mi>

i

</mi>

<mi>

t

</mi>

<mi>

y

</mi>

<mo>

⇒

</mo>

<mi>

E

</mi>

<mi>

f

</mi>

<mi>

f

</mi>

<mi>

e

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

v

</mi>

<mi>

e

</mi>

<mtext>



</mtext>

<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

</mi>

<mtext>



</mtext>

<mi>

P

</mi>

<mi>

e

</mi>

<mi>

n

</mi>

<mi>

a

</mi>

<mi>

l

</mi>

<mi>

t

</mi>

<mi>

y

</mi>

<mo>

↓

</mo>
</mrow>

<annotation encoding="application/x-tex">

Read\ Miss\ Priority \Rightarrow Effective\ Miss\ Penalty \downarrow

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0077em;">

R

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal">

d

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

or

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

⇒

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0576em;">

E

</span>

<span className="mord,mathnormal" style="margin-right:0.1076em;">

f

</span>

<span className="mord,mathnormal" style="margin-right:0.1076em;">

f

</span>

<span className="mord,mathnormal">

ec

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

v

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal">

na

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

↓

</span>
</span>
</span>
</span>
</span>

---

### 关键危险：地址冲突

如果 write buffer 中有待写地址 A，而 read miss 也要读地址 A，那么不能直接绕过。

否则 read 会读到旧数据。

所以硬件需要比较：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

R

</mi>

<mi>

e

</mi>

<mi>

a

</mi>

<mi>

d

</mi>

<mtext>



</mtext>

<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

</mi>

<mtext>



</mtext>

<mi>

A

</mi>

<mi>

d

</mi>

<mi>

d

</mi>

<mi>

r

</mi>

<mi>

e

</mi>

<mi>

s

</mi>

<mi>

s

</mi>

<mo>

=

</mo>

<mo>

=

</mo>

<mi>

W

</mi>

<mi>

r

</mi>

<mi>

i

</mi>

<mi>

t

</mi>

<mi>

e

</mi>

<mtext>



</mtext>

<mi>

B

</mi>

<mi>

u

</mi>

<mi>

f

</mi>

<mi>

f

</mi>

<mi>

e

</mi>

<mi>

r

</mi>

<mtext>



</mtext>

<mi>

A

</mi>

<mi>

d

</mi>

<mi>

d

</mi>

<mi>

r

</mi>

<mi>

e

</mi>

<mi>

s

</mi>

<mi>

s

</mi>
</mrow>

<annotation encoding="application/x-tex">

Read\ Miss\ Address == Write\ Buffer\ Address

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0077em;">

R

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal">

d

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal">

A

</span>

<span className="mord,mathnormal">

dd

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal">

ess

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

==

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

W

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.0502em;">

B

</span>

<span className="mord,mathnormal">

u

</span>

<span className="mord,mathnormal" style="margin-right:0.1076em;">

f

</span>

<span className="mord,mathnormal" style="margin-right:0.1076em;">

f

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

er

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal">

A

</span>

<span className="mord,mathnormal">

dd

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal">

ess

</span>
</span>
</span>
</span>
</span>

如果不相等：

```text
read miss 可以优先处理
```

如果相等：

```text
等待 write 完成，或者从 write buffer forwarding 最新数据
```

---

### 本页核心

write buffer 不只是优化 store，它还可以让 read miss 不被 write 队列拖慢。

但必须保证 memory ordering 和数据一致性。

一句话总结：

```text
写可以缓冲，读要优先；但同地址读写必须检查。
```

---

## Page 141｜L2 的存在如何影响 L1 设计

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-117.webp)

这一页非常重要，因为它说明 cache 层级之间不是独立设计的。

### 如果有 L2，可以使用更小的 L1

因为 L1 miss 不再直接去 DRAM，而是先去 L2。

所以 L1 miss penalty 降低了。

于是可以接受更高一点的 L1 miss rate，换取更低的 L1 hit time。

这就是：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

L

</mi>

<mn>

1

</mn>

<mtext>



</mtext>

<mi>

H

</mi>

<mi>

i

</mi>

<mi>

t

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

↓

</mo>
</mrow>

<annotation encoding="application/x-tex">

L1\ Hit\ Time \downarrow

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal">

L

</span>

<span className="mord">

1

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.0813em;">

H

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

t

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

↓

</span>
</span>
</span>
</span>
</span>

虽然：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

L

</mi>

<mn>

1

</mn>

<mtext>



</mtext>

<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

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

<mo>

↑

</mo>
</mrow>

<annotation encoding="application/x-tex">

L1\ Miss\ Rate \uparrow

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal">

L

</span>

<span className="mord">

1

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

↑

</span>
</span>
</span>
</span>
</span>

但由于：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

L

</mi>

<mn>

1

</mn>

<mtext>



</mtext>

<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

</mi>

<mtext>



</mtext>

<mi>

P

</mi>

<mi>

e

</mi>

<mi>

n

</mi>

<mi>

a

</mi>

<mi>

l

</mi>

<mi>

t

</mi>

<mi>

y

</mi>

<mo>

↓

</mo>
</mrow>

<annotation encoding="application/x-tex">

L1\ Miss\ Penalty \downarrow

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal">

L

</span>

<span className="mord">

1

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal">

na

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

↓

</span>
</span>
</span>
</span>
</span>

整体 AMAT 可能反而更好。

这正是 AMAT 权衡：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

A

</mi>

<mi>

M

</mi>

<mi>

A

</mi>

<mi>

T

</mi>

<mo>

=

</mo>

<mi>

L

</mi>

<mn>

1

</mn>

<mtext>



</mtext>

<mi>

H

</mi>

<mi>

i

</mi>

<mi>

t

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

+

</mo>

<mi>

L

</mi>

<mn>

1

</mn>

<mtext>



</mtext>

<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

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

<mo>

×

</mo>

<mi>

L

</mi>

<mn>

1

</mn>

<mtext>



</mtext>

<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

</mi>

<mtext>



</mtext>

<mi>

P

</mi>

<mi>

e

</mi>

<mi>

n

</mi>

<mi>

a

</mi>

<mi>

l

</mi>

<mi>

t

</mi>

<mi>

y

</mi>
</mrow>

<annotation encoding="application/x-tex">

AMAT = L1\ Hit\ Time + L1\ Miss\ Rate \times L1\ Miss\ Penalty

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal">

A

</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

A

</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

T

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

<span className="mord,mathnormal">

L

</span>

<span className="mord">

1

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.0813em;">

H

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

t

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

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">



</span>

<span className="mord,mathnormal">

L

</span>

<span className="mord">

1

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

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

<span className="mord,mathnormal">

L

</span>

<span className="mord">

1

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal">

na

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

</span>
</span>
</span>
</span>
</span>

---

### 如果有 L2，可以让 L1 更简单

课件提到可以使用更简单的 L1 write-through。

因为 L2 可以是 write-back，用来吸收写流量。

这样 L1 写入虽然透写到 L2，但不一定继续写到片外 DRAM。

所以：

```text
L1 write-through + L2 write-back
```

是一种合理组合。

---

### 为什么 L1 write-through 有好处？

L1 write-through 可以简化：

- L1 控制逻辑；
- pipeline recovery；
- dirty victim handling；
- coherence；
- error recovery。

因为 L1 中不需要复杂地管理 dirty block。

L1 miss 时也不会出现 “先写回 dirty victim 再取新 block” 的复杂情况。

---

### 本页核心

L2 的存在让 L1 可以更激进地追求快和简单。

```text
没有 L2：L1 miss penalty 太大，L1 不能太小。
有 L2：L1 可以小而快，因为 L2 兜底。
```

---

## Page 142｜多级 Cache 的进一步考虑

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-118.webp)

这一页是对多级 cache 设计的过渡总结。

多级 cache 设计要同时考虑：

- L1 hit time；
- L1 miss rate；
- L2 hit time；
- L2 local miss rate；
- L2 global miss rate；
- L3 和 DRAM 访问代价；
- 写策略；
- inclusion policy；
- coherence；
- power 和 area。

这里的重点是：
**多级 cache 不能只看单一级的性能。**

例如 L2 local miss rate 可能很高，但 global miss rate 可能很低。

因为访问 L2 的本来只是 L1 miss 的一小部分。

所以评价 L2 时不能只说：

```text
L2 local miss rate 高，所以 L2 不好
```

而要看它对整体 AMAT 的影响。

整体公式是：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

A

</mi>

<mi>

M

</mi>

<mi>

A

</mi>

<mi>

T

</mi>

<mo>

=

</mo>

<mi>

L

</mi>

<mn>

1

</mn>

<mtext>



</mtext>

<mi>

H

</mi>

<mi>

i

</mi>

<mi>

t

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

+

</mo>

<mi>

L

</mi>

<mn>

1

</mn>

<mtext>



</mtext>

<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

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

<mo>

×

</mo>

<mo stretchy="false">

(

</mo>

<mi>

L

</mi>

<mn>

2

</mn>

<mtext>



</mtext>

<mi>

H

</mi>

<mi>

i

</mi>

<mi>

t

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

+

</mo>

<mi>

L

</mi>

<mn>

2

</mn>

<mtext>



</mtext>

<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

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

<mo>

×

</mo>

<mi>

L

</mi>

<mn>

2

</mn>

<mtext>



</mtext>

<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

</mi>

<mtext>



</mtext>

<mi>

P

</mi>

<mi>

e

</mi>

<mi>

n

</mi>

<mi>

a

</mi>

<mi>

l

</mi>

<mi>

t

</mi>

<mi>

y

</mi>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

AMAT = L1\ Hit\ Time + L1\ Miss\ Rate \times (L2\ Hit\ Time + L2\ Miss\ Rate \times L2\ Miss\ Penalty)

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal">

A

</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

A

</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

T

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

<span className="mord,mathnormal">

L

</span>

<span className="mord">

1

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.0813em;">

H

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

t

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

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">



</span>

<span className="mord,mathnormal">

L

</span>

<span className="mord">

1

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

×

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

<span className="mord,mathnormal">

L

</span>

<span className="mord">

2

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.0813em;">

H

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

t

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

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">



</span>

<span className="mord,mathnormal">

L

</span>

<span className="mord">

2

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

×

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord,mathnormal">

L

</span>

<span className="mord">

2

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal">

na

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

</span>

<span className="mclose">

)

</span>
</span>
</span>
</span>
</span>

如果 L2 hit time 不太高，并且能挡住大量 DRAM 访问，那么它就是有效的。

本页可以理解为：

从这里开始，cache 优化不再只是容量、块大小、相联度，还包括更细的结构优化。

---

## Page 143｜Sub-Block｜用子块减少 Tag 开销

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-119.webp)

这一页讲：

```text
Sub-blocking / Sector Cache｜子块 / 扇区缓存
```

### 问题：Tag Overhead 太大

如果 cache block 很小，那么 block 数量多，tag 数量也多，tag overhead 大。

一种简单方法是增大 block size。

但 larger block 会导致：

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

i

</mi>

<mi>

s

</mi>

<mi>

s

</mi>

<mtext>



</mtext>

<mi>

P

</mi>

<mi>

e

</mi>

<mi>

n

</mi>

<mi>

a

</mi>

<mi>

l

</mi>

<mi>

t

</mi>

<mi>

y

</mi>

<mo>

↑

</mo>
</mrow>

<annotation encoding="application/x-tex">

Miss\ Penalty \uparrow

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal">

na

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

↑

</span>
</span>
</span>
</span>
</span>

因为 miss 时要搬整块。

---

### Sub-block 的思想

把一个大的 cache line 分成多个 sub-block。

整条 line 共享一个 tag，但每个 sub-block 有自己的 valid bit。

也就是说：

```text
一个 tag 管多个 sub-block
每个 sub-block 单独标记是否有效
```

这样可以减少 tag overhead，又不必每次 miss 都搬整条大 block。

---

### 访问时怎么判断？

访问某个地址时，需要判断两件事：

1. tag 是否匹配；
2. 对应 sub-block 的 valid bit 是否为 1。

只有同时满足才是 hit：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

H

</mi>

<mi>

i

</mi>

<mi>

t

</mi>

<mo>

=

</mo>

<mi>

T

</mi>

<mi>

a

</mi>

<mi>

g

</mi>

<mtext>



</mtext>

<mi>

M

</mi>

<mi>

a

</mi>

<mi>

t

</mi>

<mi>

c

</mi>

<mi>

h

</mi>

<mo>

∧

</mo>

<mi>

S

</mi>

<mi>

u

</mi>

<mi>

b

</mi>

<mi>

b

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

V

</mi>

<mi>

a

</mi>

<mi>

l

</mi>

<mi>

i

</mi>

<mi>

d

</mi>
</mrow>

<annotation encoding="application/x-tex">

Hit = Tag\ Match \land Subblock\ Valid

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0813em;">

H

</span>

<span className="mord,mathnormal">

i

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
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

T

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

g

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal">

c

</span>

<span className="mord,mathnormal">

h

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

∧

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0576em;">

S

</span>

<span className="mord,mathnormal">

u

</span>

<span className="mord,mathnormal">

bb

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

<span className="mord,mathnormal" style="margin-right:0.2222em;">

V

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

d

</span>
</span>
</span>
</span>
</span>

如果 tag match 但 sub-block invalid，说明这一大块区域的 tag 对，但目标小块还没被取进来。

这种情况还是 miss，只需要取对应 sub-block。

---

### 本页核心

sub-blocking 是在 larger block 和 smaller block 之间折中：

```text
大 block 的 tag overhead 低
小 block 的 miss penalty 低
sub-block 想同时拿到两者部分好处
```

代价是 valid bits 更多，控制更复杂。

---

## Page 144｜Victim Cache｜受害者缓存

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-120.webp)

这一页讲一个非常经典的优化：

```text
Victim Cache
```

### 问题：Direct-Mapped Cache 容易 Conflict Miss

direct-mapped cache 的优点是 hit time 快。

但缺点是每个 memory block 只能放在唯一位置。

如果两个常用 blocks 映射到同一个 cache line，就会来回互相驱逐，也就是 ping-pong conflict miss。

---

### Victim Cache 的思想

在 L1 direct-mapped cache 旁边加一个很小的 fully associative cache。

它保存最近从 L1 被 evict 出来的 blocks。

流程是：

1. CPU 先查 L1；
2. 如果 L1 hit，正常返回；
3. 如果 L1 miss，再查 victim cache；
4. 如果 victim cache hit，就把 victim cache 中的 block 和 L1 当前 victim block 交换；
5. 如果 victim cache 也 miss，再访问 L2/memory。

---

### 为什么有效？

很多 conflict miss 是短期冲突。

一个 block 刚被 L1 挤出去，马上又要用。

victim cache 正好保存这些刚被驱逐的数据。

所以它减少的是：

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

o

</mi>

<mi>

n

</mi>

<mi>

f

</mi>

<mi>

l

</mi>

<mi>

i

</mi>

<mi>

c

</mi>

<mi>

t

</mi>

<mtext>



</mtext>

<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

</mi>
</mrow>

<annotation encoding="application/x-tex">

Conflict\ Miss

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="mord,mathnormal">

o

</span>

<span className="mord,mathnormal">

n

</span>

<span className="mord,mathnormal" style="margin-right:0.1076em;">

f

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

c

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

</span>
</span>
</span>
</span>
</span>

同时保留 direct-mapped L1 的优点：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

L

</mi>

<mn>

1

</mn>

<mtext>



</mtext>

<mi>

H

</mi>

<mi>

i

</mi>

<mi>

t

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

<mtext>

仍然较快

</mtext>
</mrow>

<annotation encoding="application/x-tex">

L1\ Hit\ Time\ 仍然较快

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal">

L

</span>

<span className="mord">

1

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.0813em;">

H

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

t

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

<span className="mspace">



</span>

<span className="mord,cjk_fallback">

仍然较快

</span>
</span>
</span>
</span>
</span>

---

### 本页核心

victim cache 是一个典型折中：

```text
L1 保持 direct-mapped 的快速 hit time
小型 fully associative victim cache 负责吸收 conflict miss
```

这比把整个 L1 做成高 associativity 更便宜。

---

## Page 145｜Way-Predicting Cache｜路预测缓存

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-121.webp)

这一页讲：

```text
Way Prediction
```

### 问题：Set-Associative Cache Hit Time 更长

N-way set associative cache 需要同时查多个 way，并用 MUX 选择正确数据。

这会增加：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

H

</mi>

<mi>

i

</mi>

<mi>

t

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

<annotation encoding="application/x-tex">

Hit\ Time

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0813em;">

H

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

t

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
</span>
</span>

但 associativity 又能减少：

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

o

</mi>

<mi>

n

</mi>

<mi>

f

</mi>

<mi>

l

</mi>

<mi>

i

</mi>

<mi>

c

</mi>

<mi>

t

</mi>

<mtext>



</mtext>

<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

</mi>
</mrow>

<annotation encoding="application/x-tex">

Conflict\ Miss

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="mord,mathnormal">

o

</span>

<span className="mord,mathnormal">

n

</span>

<span className="mord,mathnormal" style="margin-right:0.1076em;">

f

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

c

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

</span>
</span>
</span>
</span>
</span>

所以有没有办法既保留 associativity，又让常见 hit 像 direct-mapped 一样快？

---

### Way Prediction 的思想

为每个 index 维护一个预测表：

```text
Way Prediction Table
```

访问 cache 时，根据地址预测这次会 hit 哪个 way。

先只访问预测的 way。

如果预测正确：

```text
Fast Hit
```

速度接近 direct-mapped。

如果预测错误，但数据在其他 way：

```text
Slow Hit
```

需要再查其他 way，并更新 prediction table。

如果其他 way 也没有：

```text
Miss
```

再访问下一级 cache。

---

### 本页核心

way prediction 是在 hit time 和 miss rate 之间做折中：

```text
用 set associativity 降 conflict miss
用 way prediction 降常见 hit time
```

但代价是：

- 需要预测表；
- 预测错误会造成 slow hit；
- 控制逻辑更复杂。

---

## Page 146｜Way-Predicting Instruction Cache

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-122.webp)

这一页把 way prediction 用到 instruction cache 上。

Instruction cache 有很强的规律性：

- 大多数指令是顺序执行；
- 分支跳转虽然会改变 PC，但分支目标也有一定可预测性。

所以可以记录：

```text
Sequential Way
Branch Target Way
```

也就是：

- 顺序执行时预测下一个 PC 对应哪个 way；
- 分支跳转时预测 branch target 对应哪个 way。

---

### 为什么 I-cache 适合 way prediction？

因为 instruction fetch 通常非常频繁，而且处在 pipeline 前端。

I-cache hit time 会直接影响取指带宽和流水线供给。

如果每次取指都查多个 way，会增加前端延迟和能耗。

way prediction 可以让大多数取指只访问一个预测 way，从而降低：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

H

</mi>

<mi>

i

</mi>

<mi>

t

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

<annotation encoding="application/x-tex">

Hit\ Time

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0813em;">

H

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

t

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
</span>
</span>

和：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

E

</mi>

<mi>

n

</mi>

<mi>

e

</mi>

<mi>

r

</mi>

<mi>

g

</mi>

<mi>

y

</mi>

<mtext>



</mtext>

<mi>

P

</mi>

<mi>

e

</mi>

<mi>

r

</mi>

<mtext>



</mtext>

<mi>

A

</mi>

<mi>

c

</mi>

<mi>

c

</mi>

<mi>

e

</mi>

<mi>

s

</mi>

<mi>

s

</mi>
</mrow>

<annotation encoding="application/x-tex">

Energy\ Per\ Access

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8778em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0576em;">

E

</span>

<span className="mord,mathnormal">

n

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

er

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

g

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

er

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal">

A

</span>

<span className="mord,mathnormal">

ccess

</span>
</span>
</span>
</span>
</span>

---

### 本页核心

instruction stream 有较强可预测性，因此适合做 way prediction。

工程直觉：

```text
程序大多数时候顺序走，偶尔跳；所以可以预测下一条指令在哪个 way。
```

---

## Page 147｜Loop Interchange｜循环交换

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-123.webp)

这一页从硬件 cache 优化转向软件优化。

代码一：

```c
for(j = 0; j < N; j++) {
    for(i = 0; i < M; i++) {
        x[i][j] = 2 * x[i][j];
    }
}
```

代码二：

```c
for(i = 0; i < M; i++) {
    for(j = 0; j < N; j++) {
        x[i][j] = 2 * x[i][j];
    }
}
```

问题是：这改善什么 locality？

---

### C 语言数组是 Row-Major

C 语言二维数组按行存储。

也就是说：

```text
x[i][0], x[i][1], x[i][2], ...
```

在内存中连续。

---

### 原始代码的问题

原始代码是 j 在外层，i 在内层。

内层循环访问：

```text
x[0][j], x[1][j], x[2][j], ...
```

这是按列访问。

如果数组按行存储，那么相邻访问之间的地址跨度大约是：

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

t

</mi>

<mi>

r

</mi>

<mi>

i

</mi>

<mi>

d

</mi>

<mi>

e

</mi>

<mo>

=

</mo>

<mi>

N

</mi>

<mo>

×

</mo>

<mi>

E

</mi>

<mi>

l

</mi>

<mi>

e

</mi>

<mi>

m

</mi>

<mi>

e

</mi>

<mi>

n

</mi>

<mi>

t

</mi>

<mtext>



</mtext>

<mi>

S

</mi>

<mi>

i

</mi>

<mi>

z

</mi>

<mi>

e

</mi>
</mrow>

<annotation encoding="application/x-tex">

Stride = N \times Element\ Size

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0576em;">

S

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

d

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

<span className="mord,mathnormal" style="margin-right:0.109em;">

N

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
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0576em;">

E

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal">

m

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal">

n

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.0576em;">

S

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal" style="margin-right:0.044em;">

z

</span>

<span className="mord,mathnormal">

e

</span>
</span>
</span>
</span>
</span>

这种 stride 访问空间局部性差。

每次可能跳到很远的位置，cache block 中带入的相邻数据用不上。

---

### 交换循环后的好处

交换后，i 在外层，j 在内层。

内层循环访问：

```text
x[i][0], x[i][1], x[i][2], ...
```

这是按行连续访问。

所以它改善的是：

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

a

</mi>

<mi>

t

</mi>

<mi>

i

</mi>

<mi>

a

</mi>

<mi>

l

</mi>

<mtext>



</mtext>

<mi>

L

</mi>

<mi>

o

</mi>

<mi>

c

</mi>

<mi>

a

</mi>

<mi>

l

</mi>

<mi>

i

</mi>

<mi>

t

</mi>

<mi>

y

</mi>
</mrow>

<annotation encoding="application/x-tex">

Spatial\ Locality

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

a

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal">

ia

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal">

L

</span>

<span className="mord,mathnormal">

oc

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

</span>
</span>
</span>
</span>
</span>

因为连续访问内存中的相邻元素。

---

### 本页核心

Loop interchange 的目的通常是让内层循环沿着内存连续方向访问。

一句话：

```text
把 stride access 变成 sequential access，提高 spatial locality。
```

---

## Page 148｜Loop Fusion｜循环融合

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-124.webp)

这一页讲第二种软件优化：

```text
Loop Fusion
```

原始代码：

```c
for(i = 0; i < N; i++)
    a[i] = b[i] * c[i];

for(i = 0; i < N; i++)
    d[i] = a[i] * c[i];
```

融合后：

```c
for(i = 0; i < N; i++) {
    a[i] = b[i] * c[i];
    d[i] = a[i] * c[i];
}
```

问题是：这改善什么 locality？

---

### 原始代码的问题

第一段循环生成 a<span>

i

</span>

。

第二段循环再使用 a<span>

i

</span>

。

如果数组很大，那么第一段循环结束后，早期的 a<span>

i

</span>

 可能已经不在 cache 里了。

第二段再访问 a<span>

i

</span>

 时，可能产生 miss。

---

### 融合后的好处

融合后：

```text
刚计算出 a[i]，马上使用 a[i]
```

所以 a<span>

i

</span>

 的 reuse distance 变短。

它更可能还在 register 或 cache 中。

这改善的是：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

T

</mi>

<mi>

e

</mi>

<mi>

m

</mi>

<mi>

p

</mi>

<mi>

o

</mi>

<mi>

r

</mi>

<mi>

a

</mi>

<mi>

l

</mi>

<mtext>



</mtext>

<mi>

L

</mi>

<mi>

o

</mi>

<mi>

c

</mi>

<mi>

a

</mi>

<mi>

l

</mi>

<mi>

i

</mi>

<mi>

t

</mi>

<mi>

y

</mi>
</mrow>

<annotation encoding="application/x-tex">

Temporal\ Locality

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

T

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal">

m

</span>

<span className="mord,mathnormal">

p

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

or

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal">

L

</span>

<span className="mord,mathnormal">

oc

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

</span>
</span>
</span>
</span>
</span>

因为同一个数据 a<span>

i

</span>

 被更快地重复使用。

同时，对 b<span>

i

</span>

、c<span>

i

</span>

、d<span>

i

</span>

 的访问仍然是顺序的，所以 spatial locality 也保持较好。

---

### 本页核心

Loop fusion 的主要作用是：

```text
缩短数据生产和消费之间的时间距离
```

所以它主要改善 temporal locality。

如果能让 a<span>

i

</span>

 直接留在 register 里，甚至可以减少对 a 数组的部分 memory traffic。

---

## Page 149｜Naïve Matrix Multiplication｜朴素矩阵乘法

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-125.webp)

这一页分析矩阵乘法的 cache 行为。

代码：

```c
for(i = 0; i < N; i++)
    for(j = 0; j < N; j++) {
        r = 0;
        for(k = 0; k < N; k++)
            r = r + y[i][k] * z[k][j];
        x[i][j] = r;
    }
```

假设 C 语言 row-major 存储。

---

### x 的访问

x[i]<span>

j

</span>

 在 j 内层变化时，是按行连续写入：

```text
x[i][0], x[i][1], x[i][2], ...
```

所以 x 的 spatial locality 比较好。

但每个 x[i]<span>

j

</span>

 在这个版本里通常是最后写一次，temporal locality 不强。

---

### y 的访问

内层 k 循环访问：

```text
y[i][0], y[i][1], y[i][2], ...
```

这是按行连续访问。

所以 y 在单次 j 计算中 spatial locality 好。

但是注意，对于固定 i，不同 j 会重复使用同一行 y[i]<span>

k

</span>

。

如果 cache 能装下这行，y 也有 temporal locality。

如果装不下，就会重复从 memory 拉取。

---

### z 的访问

内层 k 循环访问：

```text
z[0][j], z[1][j], z[2][j], ...
```

这是按列访问。

在 C 的 row-major 存储下，z[k]<span>

j

</span>

 相邻访问之间 stride 很大：

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

t

</mi>

<mi>

r

</mi>

<mi>

i

</mi>

<mi>

d

</mi>

<mi>

e

</mi>

<mo>

=

</mo>

<mi>

N

</mi>

<mo>

×

</mo>

<mi>

E

</mi>

<mi>

l

</mi>

<mi>

e

</mi>

<mi>

m

</mi>

<mi>

e

</mi>

<mi>

n

</mi>

<mi>

t

</mi>

<mtext>



</mtext>

<mi>

S

</mi>

<mi>

i

</mi>

<mi>

z

</mi>

<mi>

e

</mi>
</mrow>

<annotation encoding="application/x-tex">

Stride = N \times Element\ Size

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0576em;">

S

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

d

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

<span className="mord,mathnormal" style="margin-right:0.109em;">

N

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
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0576em;">

E

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal">

m

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal">

n

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.0576em;">

S

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal" style="margin-right:0.044em;">

z

</span>

<span className="mord,mathnormal">

e

</span>
</span>
</span>
</span>
</span>

所以 z 的 spatial locality 很差。

这通常是朴素矩阵乘法 cache 性能差的主要原因之一。

---

### 本页核心

朴素矩阵乘法的问题是：

```text
y 按行访问，较好；
x 按行写入，较好；
z 按列访问，很差。
```

所以大量 cache miss 来自 z 的 stride access。

而且当 N 很大时，工作集超过 cache，y 和 z 的复用也不充分。

---

## Page 150｜Cache Tiling｜矩阵乘法缓存分块

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L8-9-Memory-126.webp)

这一页讲矩阵乘法优化：

```text
Cache Tiling / Blocking｜缓存分块
```

代码思想是把矩阵分成小块处理：

```c
for(jj = 0; jj < N; jj = jj + B)
    for(kk = 0; kk < N; kk = kk + B)
        for(i = 0; i < N; i++)
            for(j = jj; j < min(jj+B, N); j++) {
                r = 0;
                for(k = kk; k < min(kk+B, N); k++)
                    r = r + y[i][k] * z[k][j];
                x[i][j] = x[i][j] + r;
            }
```

---

### Tiling 的核心思想

不要一次遍历整个大矩阵，而是每次只处理一个小 tile。

这样可以让当前正在使用的数据块尽量留在 cache 中。

目标是让 working set 满足：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

W

</mi>

<mi>

o

</mi>

<mi>

r

</mi>

<mi>

k

</mi>

<mi>

i

</mi>

<mi>

n

</mi>

<mi>

g

</mi>

<mtext>



</mtext>

<mi>

S

</mi>

<mi>

e

</mi>

<mi>

t

</mi>

<mtext>



</mtext>

<mi>

S

</mi>

<mi>

i

</mi>

<mi>

z

</mi>

<mi>

e

</mi>

<mo>

≤

</mo>

<mi>

C

</mi>

<mi>

a

</mi>

<mi>

c

</mi>

<mi>

h

</mi>

<mi>

e

</mi>

<mtext>



</mtext>

<mi>

C

</mi>

<mi>

a

</mi>

<mi>

p

</mi>

<mi>

a

</mi>

<mi>

c

</mi>

<mi>

i

</mi>

<mi>

t

</mi>

<mi>

y

</mi>
</mrow>

<annotation encoding="application/x-tex">

Working\ Set\ Size \le Cache\ Capacity

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

W

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

or

</span>

<span className="mord,mathnormal" style="margin-right:0.0315em;">

k

</span>

<span className="mord,mathnormal">

in

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

g

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.0576em;">

S

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.0576em;">

S

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal" style="margin-right:0.044em;">

z

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

≤

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal">

c

</span>

<span className="mord,mathnormal">

h

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal">

p

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal">

c

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

</span>
</span>
</span>
</span>
</span>

对于矩阵乘法，粗略可以理解为让 x、y、z 的相关小块放进 cache：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

T

</mi>

<mi>

i

</mi>

<mi>

l

</mi>

<mi>

e

</mi>

<mtext>



</mtext>

<mi>

F

</mi>

<mi>

o

</mi>

<mi>

o

</mi>

<mi>

t

</mi>

<mi>

p

</mi>

<mi>

r

</mi>

<mi>

i

</mi>

<mi>

n

</mi>

<mi>

t

</mi>

<mo>

≈

</mo>

<mi>

x

</mi>

<mtext>



</mtext>

<mi>

t

</mi>

<mi>

i

</mi>

<mi>

l

</mi>

<mi>

e

</mi>

<mo>

+

</mo>

<mi>

y

</mi>

<mtext>



</mtext>

<mi>

t

</mi>

<mi>

i

</mi>

<mi>

l

</mi>

<mi>

e

</mi>

<mo>

+

</mo>

<mi>

z

</mi>

<mtext>



</mtext>

<mi>

t

</mi>

<mi>

i

</mi>

<mi>

l

</mi>

<mi>

e

</mi>
</mrow>

<annotation encoding="application/x-tex">

Tile\ Footprint \approx x\ tile + y\ tile + z\ tile

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

T

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

F

</span>

<span className="mord,mathnormal">

oo

</span>

<span className="mord,mathnormal">

tp

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal">

in

</span>

<span className="mord,mathnormal">

t

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
<span className="strut" style="height:0.7778em;vertical-align:-0.0833em;">



</span>

<span className="mord,mathnormal">

x

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

e

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
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

e

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
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.044em;">

z

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

e

</span>
</span>
</span>
</span>
</span>

如果 tile size 选得合适，就能显著减少 cache miss。

---

### 它改善什么 locality？

#### 1. Temporal Locality

tiling 让同一小块数据在短时间内被反复使用。

例如 z 的一个小块被加载进 cache 后，会参与多个乘加操作，而不是用一次就被挤掉。

所以：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

T

</mi>

<mi>

e

</mi>

<mi>

m

</mi>

<mi>

p

</mi>

<mi>

o

</mi>

<mi>

r

</mi>

<mi>

a

</mi>

<mi>

l

</mi>

<mtext>



</mtext>

<mi>

L

</mi>

<mi>

o

</mi>

<mi>

c

</mi>

<mi>

a

</mi>

<mi>

l

</mi>

<mi>

i

</mi>

<mi>

t

</mi>

<mi>

y

</mi>

<mo>

↑

</mo>
</mrow>

<annotation encoding="application/x-tex">

Temporal\ Locality \uparrow

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

T

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal">

m

</span>

<span className="mord,mathnormal">

p

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

or

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal">

L

</span>

<span className="mord,mathnormal">

oc

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

↑

</span>
</span>
</span>
</span>
</span>

---

#### 2. Spatial Locality

tile 内部访问通常更连续。

尤其是 j 和 k 被限制在小范围内，访问更集中。

所以：

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

a

</mi>

<mi>

t

</mi>

<mi>

i

</mi>

<mi>

a

</mi>

<mi>

l

</mi>

<mtext>



</mtext>

<mi>

L

</mi>

<mi>

o

</mi>

<mi>

c

</mi>

<mi>

a

</mi>

<mi>

l

</mi>

<mi>

i

</mi>

<mi>

t

</mi>

<mi>

y

</mi>

<mo>

↑

</mo>
</mrow>

<annotation encoding="application/x-tex">

Spatial\ Locality \uparrow

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

a

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal">

ia

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal">

L

</span>

<span className="mord,mathnormal">

oc

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

↑

</span>
</span>
</span>
</span>
</span>

---

### 为什么比 naïve 好？

朴素矩阵乘法的问题是访问范围太大。

一个数据还没来得及复用，就可能被其他数据挤出 cache。

tiling 把大问题切成小问题，让一小片数据在 cache 中反复使用。

这相当于把 memory access 从：

```text
全矩阵范围内大跨度访问
```

变成：

```text
小块范围内集中访问
```

---

### 本页核心

Cache tiling 是软件层面最经典的 cache optimization。

它的本质是：

```text
通过改变循环顺序和计算粒度，让 working set fit in cache。
```

它同时改善：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

T

</mi>

<mi>

e

</mi>

<mi>

m

</mi>

<mi>

p

</mi>

<mi>

o

</mi>

<mi>

r

</mi>

<mi>

a

</mi>

<mi>

l

</mi>

<mtext>



</mtext>

<mi>

L

</mi>

<mi>

o

</mi>

<mi>

c

</mi>

<mi>

a

</mi>

<mi>

l

</mi>

<mi>

i

</mi>

<mi>

t

</mi>

<mi>

y

</mi>
</mrow>

<annotation encoding="application/x-tex">

Temporal\ Locality

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

T

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal">

m

</span>

<span className="mord,mathnormal">

p

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

or

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal">

L

</span>

<span className="mord,mathnormal">

oc

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

</span>
</span>
</span>
</span>
</span>

和：

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

a

</mi>

<mi>

t

</mi>

<mi>

i

</mi>

<mi>

a

</mi>

<mi>

l

</mi>

<mtext>



</mtext>

<mi>

L

</mi>

<mi>

o

</mi>

<mi>

c

</mi>

<mi>

a

</mi>

<mi>

l

</mi>

<mi>

i

</mi>

<mi>

t

</mi>

<mi>

y

</mi>
</mrow>

<annotation encoding="application/x-tex">

Spatial\ Locality

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

a

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal">

ia

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal">

L

</span>

<span className="mord,mathnormal">

oc

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

</span>
</span>
</span>
</span>
</span>

但 tile size 不能随便选。

B 太小，循环 overhead 大，复用不足；B 太大，tile 放不进 cache，miss 又会上升。

---

## Page 122–150 总结｜这一段整体逻辑

这部分从 **cache 硬件层级优化** 逐渐过渡到 **写策略**，最后进入 **软件 locality 优化**。

---

### 1. 多级缓存降低 Miss Penalty

核心公式：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

A

</mi>

<mi>

M

</mi>

<mi>

A

</mi>

<mi>

T

</mi>

<mo>

=

</mo>

<mi>

L

</mi>

<mn>

1

</mn>

<mtext>



</mtext>

<mi>

H

</mi>

<mi>

i

</mi>

<mi>

t

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

+

</mo>

<mi>

L

</mi>

<mn>

1

</mn>

<mtext>



</mtext>

<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

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

<mo>

×

</mo>

<mo stretchy="false">

(

</mo>

<mi>

L

</mi>

<mn>

2

</mn>

<mtext>



</mtext>

<mi>

H

</mi>

<mi>

i

</mi>

<mi>

t

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

+

</mo>

<mi>

L

</mi>

<mn>

2

</mn>

<mtext>



</mtext>

<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

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

<mo>

×

</mo>

<mi>

L

</mi>

<mn>

2

</mn>

<mtext>



</mtext>

<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

</mi>

<mtext>



</mtext>

<mi>

P

</mi>

<mi>

e

</mi>

<mi>

n

</mi>

<mi>

a

</mi>

<mi>

l

</mi>

<mi>

t

</mi>

<mi>

y

</mi>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

AMAT = L1\ Hit\ Time + L1\ Miss\ Rate \times (L2\ Hit\ Time + L2\ Miss\ Rate \times L2\ Miss\ Penalty)

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal">

A

</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

A

</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

T

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

<span className="mord,mathnormal">

L

</span>

<span className="mord">

1

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.0813em;">

H

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

t

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

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">



</span>

<span className="mord,mathnormal">

L

</span>

<span className="mord">

1

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

×

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

<span className="mord,mathnormal">

L

</span>

<span className="mord">

2

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.0813em;">

H

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

t

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

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">



</span>

<span className="mord,mathnormal">

L

</span>

<span className="mord">

2

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

×

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord,mathnormal">

L

</span>

<span className="mord">

2

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal">

na

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

</span>

<span className="mclose">

)

</span>
</span>
</span>
</span>
</span>

多级 cache 的意义是：

```text
L1 miss 不直接去 DRAM，而是先去 L2/L3。
```

所以它主要优化：

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

i

</mi>

<mi>

s

</mi>

<mi>

s

</mi>

<mtext>



</mtext>

<mi>

P

</mi>

<mi>

e

</mi>

<mi>

n

</mi>

<mi>

a

</mi>

<mi>

l

</mi>

<mi>

t

</mi>

<mi>

y

</mi>
</mrow>

<annotation encoding="application/x-tex">

Miss\ Penalty

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal">

na

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

</span>
</span>
</span>
</span>
</span>

---

### 2. L1 / L2 / L3 的设计目标不同

```text
L1：小而快，追求 hit time
L2/L3：更大，追求低 miss rate
DRAM：最大，但最慢
```

所以 cache 层级越靠近 CPU，越重视速度；越远离 CPU，越重视容量。

---

### 3. 写策略处理 Cache 与 Memory 的一致性

写策略主要有：

```text
Write-through
Write-back
```

write-through：

```text
简单，但写流量大
```

write-back：

```text
写流量小，但需要 dirty bit，控制复杂
```

常见组合：

```text
Write-through + No-write-allocate
Write-back + Write-allocate
```

---

### 4. Write Buffer 优化写入和 Read Miss

write buffer 可以让 store 不阻塞 CPU。

同时 read miss 可以优先于 write buffer 中的写请求，从而降低：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

E

</mi>

<mi>

f

</mi>

<mi>

f

</mi>

<mi>

e

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

v

</mi>

<mi>

e

</mi>

<mtext>



</mtext>

<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

</mi>

<mtext>



</mtext>

<mi>

P

</mi>

<mi>

e

</mi>

<mi>

n

</mi>

<mi>

a

</mi>

<mi>

l

</mi>

<mi>

t

</mi>

<mi>

y

</mi>
</mrow>

<annotation encoding="application/x-tex">

Effective\ Miss\ Penalty

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0576em;">

E

</span>

<span className="mord,mathnormal" style="margin-right:0.1076em;">

f

</span>

<span className="mord,mathnormal" style="margin-right:0.1076em;">

f

</span>

<span className="mord,mathnormal">

ec

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

v

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal">

na

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

</span>
</span>
</span>
</span>
</span>

但必须检查地址冲突：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

R

</mi>

<mi>

e

</mi>

<mi>

a

</mi>

<mi>

d

</mi>

<mtext>



</mtext>

<mi>

A

</mi>

<mi>

d

</mi>

<mi>

d

</mi>

<mi>

r

</mi>

<mi>

e

</mi>

<mi>

s

</mi>

<mi>

s

</mi>

<mo>

=

</mo>

<mo>

=

</mo>

<mi>

W

</mi>

<mi>

r

</mi>

<mi>

i

</mi>

<mi>

t

</mi>

<mi>

e

</mi>

<mtext>



</mtext>

<mi>

B

</mi>

<mi>

u

</mi>

<mi>

f

</mi>

<mi>

f

</mi>

<mi>

e

</mi>

<mi>

r

</mi>

<mtext>



</mtext>

<mi>

A

</mi>

<mi>

d

</mi>

<mi>

d

</mi>

<mi>

r

</mi>

<mi>

e

</mi>

<mi>

s

</mi>

<mi>

s

</mi>
</mrow>

<annotation encoding="application/x-tex">

Read\ Address == Write\ Buffer\ Address

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0077em;">

R

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal">

d

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal">

A

</span>

<span className="mord,mathnormal">

dd

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal">

ess

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

==

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

W

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.0502em;">

B

</span>

<span className="mord,mathnormal">

u

</span>

<span className="mord,mathnormal" style="margin-right:0.1076em;">

f

</span>

<span className="mord,mathnormal" style="margin-right:0.1076em;">

f

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

er

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal">

A

</span>

<span className="mord,mathnormal">

dd

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal">

ess

</span>
</span>
</span>
</span>
</span>

同地址时要等待或 forwarding。

---

### 5. 进一步结构优化

这几页还讲了几种 cache 结构优化：

<table>
<thead>
  <tr>
    <th>
      技术
    </th>
    
    <th>
      主要改善
    </th>
    
    <th>
      代价
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      Sub-block
    </td>
    
    <td>
      降低 tag overhead 和 miss penalty
    </td>
    
    <td>
      valid bits 更多，控制复杂
    </td>
  </tr>
  
  <tr>
    <td>
      Victim cache
    </td>
    
    <td>
      减少 conflict miss
    </td>
    
    <td>
      额外小型 FA cache
    </td>
  </tr>
  
  <tr>
    <td>
      Way prediction
    </td>
    
    <td>
      降低 set-associative hit time
    </td>
    
    <td>
      预测错误会 slow hit
    </td>
  </tr>
  
  <tr>
    <td>
      Pipelined write
    </td>
    
    <td>
      提高写吞吐
    </td>
    
    <td>
      load/store hazard 更复杂
    </td>
  </tr>
</tbody>
</table>

---

### 6. 软件优化 Locality

最后几页强调：cache 性能不只靠硬件，也靠程序访问模式。

<table>
<thead>
  <tr>
    <th>
      软件优化
    </th>
    
    <th>
      主要改善
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      Loop interchange
    </td>
    
    <td>
      spatial locality
    </td>
  </tr>
  
  <tr>
    <td>
      Loop fusion
    </td>
    
    <td>
      temporal locality
    </td>
  </tr>
  
  <tr>
    <td>
      Cache tiling
    </td>
    
    <td>
      temporal locality + spatial locality
    </td>
  </tr>
</tbody>
</table>

核心思想是：

```text
让程序访问更连续，让数据复用更快发生，让 working set 尽量留在 cache 中。
```

---

## 最终复习压缩版

```text
Multi-level cache：降低 miss penalty。
Local miss rate：本级访问中的 miss 比例。
Global miss rate：从 CPU 总访问角度看的 miss 比例。
L1：追求 hit time。
L2/L3：追求 miss rate，减少 DRAM access。
Write-through：简单，但写流量大。
Write-back：高效，但需要 dirty bit，控制复杂。
Write allocate：write miss 时先取入 cache。
No-write-allocate：write miss 时直接写 memory。
Sub-block：一个 tag 管多个小块，减少 tag overhead。
Victim cache：保存刚被驱逐的块，减少 conflict miss。
Way prediction：预测命中的 way，降低常见 hit time。
Loop interchange：把跨行 stride 访问改成连续访问，改善 spatial locality。
Loop fusion：缩短数据复用距离，改善 temporal locality。
Cache tiling：让小块 working set 留在 cache，同时改善 temporal 和 spatial locality。
```

所有内容最终还是回到 AMAT：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

A

</mi>

<mi>

M

</mi>

<mi>

A

</mi>

<mi>

T

</mi>

<mo>

=

</mo>

<mi>

H

</mi>

<mi>

i

</mi>

<mi>

t

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

+

</mo>

<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

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

<mo>

×

</mo>

<mi>

M

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

s

</mi>

<mtext>



</mtext>

<mi>

P

</mi>

<mi>

e

</mi>

<mi>

n

</mi>

<mi>

a

</mi>

<mi>

l

</mi>

<mi>

t

</mi>

<mi>

y

</mi>
</mrow>

<annotation encoding="application/x-tex">

AMAT = Hit\ Time + Miss\ Rate \times Miss\ Penalty

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal">

A

</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

A

</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

T

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

<span className="mord,mathnormal" style="margin-right:0.0813em;">

H

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

t

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

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

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

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

ss

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal">

na

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

</span>
</span>
</span>
</span>
</span>
