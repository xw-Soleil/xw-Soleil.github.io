# Chapter 12：算术运算电路 Arithmetic

> 加法器、比较器与计数器等基本算术电路的结构与延迟分析。

## 基本的计算机组成 ｜ Major Components of a Computer

### 本节概述

1. 处理器的核心结构可以概括为：
**Processor = Control + Datapath + Memory + Interconnect**
2. 后续 Arithmetic 章节主要关注：
**Datapath 中的执行单元**
3. 重点对象包括：
  - 加法器
  - 乘法器
  - 除法器
  - 移位器
  - ALU

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter12-Arithmetic-01.webp)

### 计算机与数字处理器基本结构

1. **计算机系统组成****Computer = Processor + Memory + Devices**
  - **Processor 处理器**
    - 负责执行程序，是计算机系统的核心。
    - 主要包括：
    
      - **Control 控制单元**：产生控制信号，决定指令如何执行、数据如何流动。
      - **Datapath 数据通路**：负责数据运算、暂存和传输，是算术逻辑单元所在位置。
  - **Memory 存储器**
    - 保存程序和数据。
    - 供处理器读取指令、读取数据、写回结果。
  - **Devices 输入输出设备**
    - **Input 输入设备**：键盘、传感器、摄像头等。
    - **Output 输出设备**：显示器、通信接口等。

### 通用数字处理器抽象

1. **基本数据流 Input / Output ↔ Datapath ↔ Memory**
  - **Input / Output**：负责与外部设备交换数据。
  - **Datapath**：执行运算、暂存数据、传输数据。
  - **Memory**：存放指令和数据。
  - **Control**：根据指令控制 Datapath 和 Memory 的工作。

### Basic Building Blocks

1. **Datapath 数据通路**
  - **Execution units 执行单元**
    - Adder 加法器
    - Multiplier 乘法器
    - Divider 除法器
    - Shifter 移位器
    - ALU 算术逻辑单元
  - **Register file 寄存器堆**
    - 存放处理器内部临时数据。
  - **Pipeline registers 流水线寄存器**
    - 在流水线各阶段之间暂存数据。
  - **Multiplexers 多路选择器**
    - 在多个输入数据中选择一个输出。
  - **Decoders 译码器**
    - 将编码信息转换为控制信号或选择信号。
2. **Control 控制单元**
  - 负责产生控制信号。
  - 常见实现方式：
  
    - FSM 有限状态机
    - PLA 可编程逻辑阵列
    - ROM
    - Random logic 随机逻辑
3. **Interconnect 互连结构**
  - 负责模块之间的数据连接与传输。
  - 包括：
  
    - Switches 开关
    - Arbiters 仲裁器
    - Buses 总线
4. **Memory 存储结构**
  - 包括：
  
    - Cache 高速缓存
    - TLB 地址转换缓存
    - DRAM 主存
    - Buffers 缓冲器

### 现代处理器结构风格

1. **Pipelined, single issue**
  - 流水线单发射。
  - 每个周期通常发射一条指令。
2. **Superscalar**
  - 超标量结构。
  - 由硬件控制多发射，每周期可发射多条指令。
3. **VLIW**
  - Very Long Instruction Word，超长指令字。
  - 由软件 / 编译器安排多发射。
4. **Multithreaded**
  - 多线程结构。
  - 从多个线程中取指令执行，提高硬件利用率。

### Datapath Bit-Sliced Organization

多位数据通路 = 重复的一位处理单元 + 统一控制信号。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter12-Arithmetic-02.webp)

## Adder ｜ 加法器设计

### Single-Bit Addition

#### Half adder & Full Adder

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter12-Arithmetic-03.webp)

#### Brute force implementation from eqns  ｜ 直接按照公式硬搭majority gate电路

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter12-Arithmetic-04.webp)

#### 经过优化关键路径后的加法器

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter12-Arithmetic-05.webp)

- 先计算进位,然后再利用公式<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

S

</mi>

<mo>

=

</mo>

<mi>

A

</mi>

<mi>

B

</mi>

<mi>

C

</mi>

<mo>

+

</mo>

<mo stretchy="false">

(

</mo>

<mi>

A

</mi>

<mo>

+

</mo>

<mi>

B

</mi>

<mo>

+

</mo>

<msub>
<mi>

C

</mi>

<mi>

i

</mi>
</msub>

<mo stretchy="false">

)

</mo>

<mover accent="true">
<msub>
<mi>

C

</mi>

<mi>

o

</mi>
</msub>

<mo stretchy="true">

‾

</mo>
</mover>
</mrow>

<annotation encoding="application/x-tex">

S = ABC + (A+B+C_i)\overline{C_o}

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

A

</span>

<span className="mord,mathnormal" style="margin-right:0.0502em;">

B

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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mopen">

(

</span>

<span className="mord,mathnormal">

A

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

<span className="mord,mathnormal" style="margin-right:0.0502em;">

B

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
<span className="strut" style="height:1.1333em;vertical-align:-0.25em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

i

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

<span className="mord,overline">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.8833em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

o

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

<span style="top:-3.8033em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="overline-line" style="border-bottom-width:0.04em;">



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

计算出求和
- 此种方法会比串行进位加法器速度快，因为串行操作需要三次异或操作

#### 进位加法器设计

##### 进位行为分析

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 50.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter12-Arithmetic-06.webp" />
      </p>
    </td>
    
    
      <td style="width: 49.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter12-Arithmetic-07.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

- **Carry status—— 进位状态**
只看当前位的 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

A

</mi>

<mo separator="true">

,

</mo>

<mi>

B

</mi>
</mrow>

<annotation encoding="application/x-tex">

A,B

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8778em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal">

A

</span>

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0502em;">

B

</span>
</span>
</span>
</span>

，判断它对输入进位 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

C

</mi>

<mi>

i

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

C_i

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
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

i

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

 做什么：
  1. **Generate 产生进位**
    - (A=1,B=1)
    - 不管 (C_i) 是多少，(C_o=1)
    - <span className="katex">
    <span className="katex-mathml">
    <math xmlns="http://www.w3.org/1998/Math/MathML">
    <semantics>
    <mrow>
    <mi>
    
    G
    
    </mi>
    
    <mo>
    
    =
    
    </mo>
    
    <mi>
    
    A
    
    </mi>
    
    <mo>
    
    ⋅
    
    </mo>
    
    <mi>
    
    B
    
    </mi>
    </mrow>
    
    <annotation encoding="application/x-tex">
    
    G=A\cdot B
    
    </annotation>
    </semantics>
    </math>
    </span>
    
    <span className="katex-html" ariaHidden="true">
    <span className="base">
    <span className="strut" style="height:0.6833em;">
    
    
    
    </span>
    
    <span className="mord,mathnormal">
    
    G
    
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
    
    <span className="mord,mathnormal">
    
    A
    
    </span>
    
    <span className="mspace" style="margin-right:0.2222em;">
    
    
    
    </span>
    
    <span className="mbin">
    
    ⋅
    
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
  2. **Propagate 传播进位**
    - (<span className="katex">
    <span className="katex-mathml">
    <math xmlns="http://www.w3.org/1998/Math/MathML">
    <semantics>
    <mrow>
    <mi>
    
    A
    
    </mi>
    
    <mo mathvariant="normal">
    
    ≠
    
    </mo>
    
    <mi>
    
    B
    
    </mi>
    </mrow>
    
    <annotation encoding="application/x-tex">
    
    A\neq B
    
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
    
    <span className="mspace" style="margin-right:0.2778em;">
    
    
    
    </span>
    
    <span className="mrel">
    <span className="mrel">
    <span className="mord,vbox">
    <span className="thinbox">
    <span className="rlap">
    <span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">
    
    
    
    </span>
    
    <span className="inner">
    <span className="mord">
    <span className="mrel">
    
    
    
    </span>
    </span>
    </span>
    
    <span className="fix">
    
    
    
    </span>
    </span>
    </span>
    </span>
    </span>
    
    <span className="mspace,nobreak">
    
    
    
    </span>
    
    <span className="mrel">
    
    =
    
    </span>
    </span>
    
    <span className="mspace" style="margin-right:0.2778em;">
    
    
    
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
    
    )
    - 输出进位等于输入进位
    - <span className="katex">
    <span className="katex-mathml">
    <math xmlns="http://www.w3.org/1998/Math/MathML">
    <semantics>
    <mrow>
    <mi>
    
    P
    
    </mi>
    
    <mo>
    
    =
    
    </mo>
    
    <mi>
    
    A
    
    </mi>
    
    <mo>
    
    ⊕
    
    </mo>
    
    <mi>
    
    B
    
    </mi>
    </mrow>
    
    <annotation encoding="application/x-tex">
    
    P=A\oplus B
    
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
    
    A
    
    </span>
    
    <span className="mspace" style="margin-right:0.2222em;">
    
    
    
    </span>
    
    <span className="mbin">
    
    ⊕
    
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
  3. **Kill / Delete 删除进位**
    - (A=0,B=0)
    - 不管 (C_i) 是多少，(C_o=0)
    - <span className="katex">
    <span className="katex-mathml">
    <math xmlns="http://www.w3.org/1998/Math/MathML">
    <semantics>
    <mrow>
    <mi>
    
    K
    
    </mi>
    
    <mo>
    
    =
    
    </mo>
    
    <mover accent="true">
    <mi>
    
    A
    
    </mi>
    
    <mo stretchy="true">
    
    ‾
    
    </mo>
    </mover>
    
    <mo>
    
    ⋅
    
    </mo>
    
    <mover accent="true">
    <mi>
    
    B
    
    </mi>
    
    <mo stretchy="true">
    
    ‾
    
    </mo>
    </mover>
    </mrow>
    
    <annotation encoding="application/x-tex">
    
    K=\overline A\cdot \overline B
    
    </annotation>
    </semantics>
    </math>
    </span>
    
    <span className="katex-html" ariaHidden="true">
    <span className="base">
    <span className="strut" style="height:0.6833em;">
    
    
    
    </span>
    
    <span className="mord,mathnormal" style="margin-right:0.0715em;">
    
    K
    
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
    <span className="strut" style="height:0.8833em;">
    
    
    
    </span>
    
    <span className="mord,overline">
    <span className="vlist-t">
    <span className="vlist-r">
    <span className="vlist" style="height:0.8833em;">
    <span style="top:-3em;">
    <span className="pstrut" style="height:3em;">
    
    
    
    </span>
    
    <span className="mord">
    <span className="mord,mathnormal">
    
    A
    
    </span>
    </span>
    </span>
    
    <span style="top:-3.8033em;">
    <span className="pstrut" style="height:3em;">
    
    
    
    </span>
    
    <span className="overline-line" style="border-bottom-width:0.04em;">
    
    
    
    </span>
    </span>
    </span>
    </span>
    </span>
    </span>
    
    <span className="mspace" style="margin-right:0.2222em;">
    
    
    
    </span>
    
    <span className="mbin">
    
    ⋅
    
    </span>
    
    <span className="mspace" style="margin-right:0.2222em;">
    
    
    
    </span>
    </span>
    
    <span className="base">
    <span className="strut" style="height:0.8833em;">
    
    
    
    </span>
    
    <span className="mord,overline">
    <span className="vlist-t">
    <span className="vlist-r">
    <span className="vlist" style="height:0.8833em;">
    <span style="top:-3em;">
    <span className="pstrut" style="height:3em;">
    
    
    
    </span>
    
    <span className="mord">
    <span className="mord,mathnormal" style="margin-right:0.0502em;">
    
    B
    
    </span>
    </span>
    </span>
    
    <span style="top:-3.8033em;">
    <span className="pstrut" style="height:3em;">
    
    
    
    </span>
    
    <span className="overline-line" style="border-bottom-width:0.04em;">
    
    
    
    </span>
    </span>
    </span>
    </span>
    </span>
    </span>
    </span>
    </span>
    </span>
- **用 P、G、K 表达加法器:**
  - <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <msub>
  <mi>
  
  C
  
  </mi>
  
  <mi>
  
  o
  
  </mi>
  </msub>
  
  <mo>
  
  =
  
  </mo>
  
  <mi>
  
  G
  
  </mi>
  
  <mo>
  
  +
  
  </mo>
  
  <mi>
  
  P
  
  </mi>
  
  <msub>
  <mi>
  
  C
  
  </mi>
  
  <mi>
  
  i
  
  </mi>
  </msub>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  C_o = G + P C_i
  
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
  <span className="vlist" style="height:0.1514em;">
  <span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
  <span className="pstrut" style="height:2.7em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size6,size3,mtight">
  <span className="mord,mathnormal,mtight">
  
  o
  
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
  <span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">
  
  
  
  </span>
  
  <span className="mord,mathnormal">
  
  G
  
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
  <span className="vlist" style="height:0.3117em;">
  <span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
  <span className="pstrut" style="height:2.7em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size6,size3,mtight">
  <span className="mord,mathnormal,mtight">
  
  i
  
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

如果我们知道每一位是 **Generate / Propagate / Kill**，就可以提前推导高位进位，形成后面的：

- Carry Lookahead Adder
- Carry Skip Adder
- Carry Select Adder
- Prefix Adder

#### Mirror Adder

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter12-Arithmetic-08.webp)

核心公式<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

C

</mi>

<mi>

o

</mi>
</msub>

<mo>

=

</mo>

<mi>

A

</mi>

<mi>

B

</mi>

<mo>

+

</mo>

<msub>
<mi>

C

</mi>

<mi>

i

</mi>
</msub>

<mo stretchy="false">

(

</mo>

<mi>

A

</mi>

<mo>

+

</mo>

<mi>

B

</mi>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

C_o = AB + C_i(A+B)

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
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

o

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
<span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">



</span>

<span className="mord,mathnormal">

A

</span>

<span className="mord,mathnormal" style="margin-right:0.0502em;">

B

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
<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

i

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

A

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

<span className="mord,mathnormal" style="margin-right:0.0502em;">

B

</span>

<span className="mclose">

)

</span>
</span>
</span>
</span>



##### 电路实现

红色网络实际先生成：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mover accent="true">
<msub>
<mi>

C

</mi>

<mi>

o

</mi>
</msub>

<mo stretchy="true">

‾

</mo>
</mover>
</mrow>

<annotation encoding="application/x-tex">

\overline{C_o}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.0333em;vertical-align:-0.15em;">



</span>

<span className="mord,overline">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.8833em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

o

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

<span style="top:-3.8033em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="overline-line" style="border-bottom-width:0.04em;">



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

- 上拉网络：负责让 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mover accent="true">
<msub>
<mi>

C

</mi>

<mi>

o

</mi>
</msub>

<mo stretchy="true">

‾

</mo>
</mover>

<mo>

=

</mo>

<mn>

1

</mn>
</mrow>

<annotation encoding="application/x-tex">

\overline{C_o}=1

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.0333em;vertical-align:-0.15em;">



</span>

<span className="mord,overline">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.8833em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

o

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

<span style="top:-3.8033em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="overline-line" style="border-bottom-width:0.04em;">



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


  - 对应 Kill 和 “0”-Propagate
- 下拉网络：负责让 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mover accent="true">
<msub>
<mi>

C

</mi>

<mi>

o

</mi>
</msub>

<mo stretchy="true">

‾

</mo>
</mover>

<mo>

=

</mo>

<mn>

0

</mn>
</mrow>

<annotation encoding="application/x-tex">

\overline{C_o}=0

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.0333em;vertical-align:-0.15em;">



</span>

<span className="mord,overline">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.8833em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

o

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

<span style="top:-3.8033em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="overline-line" style="border-bottom-width:0.04em;">



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


  - 对应 Generate 和 “1”-Propagate

##### 优点

- 不显式生成 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

P

</mi>

<mo>

=

</mo>

<mi>

A

</mi>

<mo>

⊕

</mo>

<mi>

B

</mi>
</mrow>

<annotation encoding="application/x-tex">

P=A\oplus B

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

A

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

⊕

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
- 直接把 Kill / Propagate / Generate 写进晶体管导通路径
- 晶体管数少：24T
- Carry 路径更直接，适合 ripple-carry adder

<mark>

**Mirror Adder 是按进位行为设计晶体管网络：消进位、传进位、产生进位。**

</mark>



#### Transmission Gate Full Adder

采用传输门的方式来进行全加器的设计

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter12-Arithmetic-09.webp)

#### Complementary Pass Transistor Logic ｜ 互补传输晶体管逻辑

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter12-Arithmetic-10.webp)

速度更快是因为级连数目比较少 但是会占用比较大的面积

### Multi-bit Addition

#### Ripple-Carry Adder 串行进位加法器

把多个 **Full Adder，全加器** 串起来：

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter12-Arithmetic-11.webp)

关键路径<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

C

</mi>

<mi>

i

</mi>
</msub>

<mo>

→

</mo>

<msub>
<mi>

C

</mi>

<mi>

o

</mi>
</msub>

<mo>

→

</mo>

<msub>
<mi>

C

</mi>

<mi>

o

</mi>
</msub>

<mo>

→

</mo>

<mo>

⋯

</mo>
</mrow>

<annotation encoding="application/x-tex">

C_i \rightarrow C_o \rightarrow C_o \rightarrow \cdots

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
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

i

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

→

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

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
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

o

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

→

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

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
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

o

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

→

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.313em;">



</span>

<span className="minner">

⋯

</span>
</span>
</span>
</span>

,延迟随位数线性增加.

具体延迟计算

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<msub>
<mi>

t

</mi>

<mrow>
<mi>

a

</mi>

<mi>

d

</mi>

<mi>

d

</mi>

<mi>

e

</mi>

<mi>

r

</mi>
</mrow>
</msub>

<mo>

=

</mo>

<mo stretchy="false">

(

</mo>

<mi>

N

</mi>

<mo>

−

</mo>

<mn>

1

</mn>

<mo stretchy="false">

)

</mo>

<msub>
<mi>

t

</mi>

<mrow>
<mi>

c

</mi>

<mi>

a

</mi>

<mi>

r

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

+

</mo>

<msub>
<mi>

t

</mi>

<mrow>
<mi>

s

</mi>

<mi>

u

</mi>

<mi>

m

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

t_{adder}=(N-1)t_{carry}+t_{sum}

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
<span className="mord,mathnormal,mtight">

a

</span>

<span className="mord,mathnormal,mtight">

dd

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

er

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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mopen">

(

</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

N

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
<span className="strut" style="height:1.0361em;vertical-align:-0.2861em;">



</span>

<span className="mord">

1

</span>

<span className="mclose">

)

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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

c

</span>

<span className="mord,mathnormal,mtight">

a

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

r

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



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
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

s

</span>

<span className="mord,mathnormal,mtight">

u

</span>

<span className="mord,mathnormal,mtight">

m

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
</span>

其中<span className="katex">
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

c

</mi>

<mi>

a

</mi>

<mi>

r

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

t_{carry}

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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

c

</span>

<span className="mord,mathnormal,mtight">

a

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

r

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

是单个 full adder 中，**进位从输入传到输出**的延迟，即Ci→Co的延迟,<span className="katex">
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

s

</mi>

<mi>

u

</mi>

<mi>

m

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

t_{sum}

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
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

s

</span>

<span className="mord,mathnormal,mtight">

u

</span>

<span className="mord,mathnormal,mtight">

m

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

则是最后一级 full adder 中，进位到达后产生 Sum 的延迟。

#### Inversion Property ｜ 全加器的反向特性

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter12-Arithmetic-12.webp)

全加器有这样的反相特性——如果把全加器的所有输入都取反，那么输出也会整体取反

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mover accent="true">
<mi>

S

</mi>

<mo stretchy="true">

‾

</mo>
</mover>

<mo stretchy="false">

(

</mo>

<mi>

A

</mi>

<mo separator="true">

,

</mo>

<mi>

B

</mi>

<mo separator="true">

,

</mo>

<msub>
<mi>

C

</mi>

<mi>

i

</mi>
</msub>

<mo stretchy="false">

)

</mo>

<mo>

=

</mo>

<mi>

S

</mi>

<mo stretchy="false">

(

</mo>

<mover accent="true">
<mi>

A

</mi>

<mo stretchy="true">

‾

</mo>
</mover>

<mo separator="true">

,

</mo>

<mover accent="true">
<mi>

B

</mi>

<mo stretchy="true">

‾

</mo>
</mover>

<mo separator="true">

,

</mo>

<mover accent="true">
<msub>
<mi>

C

</mi>

<mi>

i

</mi>
</msub>

<mo stretchy="true">

‾

</mo>
</mover>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

\overline{S}(A,B,C_i)=S(\overline A,\overline B,\overline {C_i})

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.1333em;vertical-align:-0.25em;">



</span>

<span className="mord,overline">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8833em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0576em;">

S

</span>
</span>
</span>

<span style="top:-3.8033em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="overline-line" style="border-bottom-width:0.04em;">



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

A

</span>

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0502em;">

B

</span>

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

i

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
<span className="strut" style="height:1.1333em;vertical-align:-0.25em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0576em;">

S

</span>

<span className="mopen">

(

</span>

<span className="mord,overline">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8833em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

A

</span>
</span>
</span>

<span style="top:-3.8033em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="overline-line" style="border-bottom-width:0.04em;">



</span>
</span>
</span>
</span>
</span>
</span>

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord,overline">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8833em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0502em;">

B

</span>
</span>
</span>

<span style="top:-3.8033em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="overline-line" style="border-bottom-width:0.04em;">



</span>
</span>
</span>
</span>
</span>
</span>

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord,overline">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.8833em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

i

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

<span style="top:-3.8033em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="overline-line" style="border-bottom-width:0.04em;">



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

<span className="mclose">

)

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
<mover accent="true">
<msub>
<mi>

C

</mi>

<mi>

o

</mi>
</msub>

<mo stretchy="true">

‾

</mo>
</mover>

<mo stretchy="false">

(

</mo>

<mi>

A

</mi>

<mo separator="true">

,

</mo>

<mi>

B

</mi>

<mo separator="true">

,

</mo>

<msub>
<mi>

C

</mi>

<mi>

i

</mi>
</msub>

<mo stretchy="false">

)

</mo>

<mo>

=

</mo>

<msub>
<mi>

C

</mi>

<mi>

o

</mi>
</msub>

<mo stretchy="false">

(

</mo>

<mover accent="true">
<mi>

A

</mi>

<mo stretchy="true">

‾

</mo>
</mover>

<mo separator="true">

,

</mo>

<mover accent="true">
<mi>

B

</mi>

<mo stretchy="true">

‾

</mo>
</mover>

<mo separator="true">

,

</mo>

<mover accent="true">
<msub>
<mi>

C

</mi>

<mi>

i

</mi>
</msub>

<mo stretchy="true">

‾

</mo>
</mover>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

\overline{C_o}(A,B,C_i)=C_o(\overline A,\overline B,\overline {C_i})

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.1333em;vertical-align:-0.25em;">



</span>

<span className="mord,overline">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.8833em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

o

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

<span style="top:-3.8033em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="overline-line" style="border-bottom-width:0.04em;">



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

<span className="mopen">

(

</span>

<span className="mord,mathnormal">

A

</span>

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0502em;">

B

</span>

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

i

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
<span className="strut" style="height:1.1333em;vertical-align:-0.25em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

o

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

<span className="mord,overline">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8833em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

A

</span>
</span>
</span>

<span style="top:-3.8033em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="overline-line" style="border-bottom-width:0.04em;">



</span>
</span>
</span>
</span>
</span>
</span>

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord,overline">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8833em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0502em;">

B

</span>
</span>
</span>

<span style="top:-3.8033em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="overline-line" style="border-bottom-width:0.04em;">



</span>
</span>
</span>
</span>
</span>
</span>

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord,overline">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.8833em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

i

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

<span style="top:-3.8033em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="overline-line" style="border-bottom-width:0.04em;">



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

<span className="mclose">

)

</span>
</span>
</span>
</span>
</span>

真实 CMOS 全加器的 carry 输出往往**天然是反相**的，如果每一级都加反相器恢复极性，会拖慢 carry critical path；所以**让 even / odd 全加器交替使用反相 carry**，省掉 carry 路径上的反相器

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter12-Arithmetic-13.webp)

具体实施操作如下图所示<mark>

（从右往左看）

</mark>

：

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter12-Arithmetic-14.webp)

A2,B2 需要以反相信号形式进入 odd cell，这样输出的S2才是正值

<mark>

注意：

</mark>

<mark>

**在**

</mark>

<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mo>

⊕

</mo>
</mrow>

<annotation encoding="application/x-tex">

\oplus

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6667em;vertical-align:-0.0833em;">



</span>

<span className="mord">

⊕

</span>
</span>
</span>
</span>

<mark>

**符号上的圆圈表示反相输入，并不代表有反相器存在！！**

</mark>



#### Manchester Carry Chain | 曼彻斯特加法链

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter12-Arithmetic-15.webp)

此页左边电路就是在实现这个逻辑：

- <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

P

</mi>

<mi>

i

</mi>
</msub>

<mo>

=

</mo>

<mn>

1

</mn>
</mrow>

<annotation encoding="application/x-tex">

P_i=1

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

P

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.1389em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

i

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

1

</span>
</span>
</span>
</span>

：传输门打开，直接把 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

C

</mi>

<mi>

i

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

C_i

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
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

i

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

 传到 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

C

</mi>

<mi>

o

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

C_o

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
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

o

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

；
- <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

G

</mi>

<mi>

i

</mi>
</msub>

<mo>

=

</mo>

<mn>

1

</mn>
</mrow>

<annotation encoding="application/x-tex">

G_i=1

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

G

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

i

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

1

</span>
</span>
</span>
</span>

：上拉到 <span className="katex">
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

，强制 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

C

</mi>

<mi>

o

</mi>
</msub>

<mo>

=

</mo>

<mn>

1

</mn>
</mrow>

<annotation encoding="application/x-tex">

C_o=1

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
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

o

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

1

</span>
</span>
</span>
</span>

；
- <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

D

</mi>

<mi>

i

</mi>
</msub>

<mo>

=

</mo>

<mn>

1

</mn>
</mrow>

<annotation encoding="application/x-tex">

D_i=1

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

D

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0278em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

i

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

1

</span>
</span>
</span>
</span>

：下拉到 GND，强制 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

C

</mi>

<mi>

o

</mi>
</msub>

<mo>

=

</mo>

<mn>

0

</mn>
</mrow>

<annotation encoding="application/x-tex">

C_o=0

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
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

o

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

0

</span>
</span>
</span>
</span>

。

右边本质上是在动态逻辑里实现：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mover accent="true">
<msub>
<mi>

C

</mi>

<mi>

o

</mi>
</msub>

<mo stretchy="true">

‾

</mo>
</mover>

<mo>

=

</mo>

<msub>
<mi>

D

</mi>

<mi>

i

</mi>
</msub>

<mo>

+

</mo>

<msub>
<mi>

P

</mi>

<mi>

i

</mi>
</msub>

<mover accent="true">
<msub>
<mi>

C

</mi>

<mi>

i

</mi>
</msub>

<mo stretchy="true">

‾

</mo>
</mover>
</mrow>

<annotation encoding="application/x-tex">

\overline{C_o}=D_i+P_i\overline{C_i}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.0333em;vertical-align:-0.15em;">



</span>

<span className="mord,overline">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.8833em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

o

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

<span style="top:-3.8033em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="overline-line" style="border-bottom-width:0.04em;">



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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

D

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0278em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

i

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
<span className="strut" style="height:1.0333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.1389em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

i

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

<span className="mord,overline">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.8833em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

i

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

<span style="top:-3.8033em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="overline-line" style="border-bottom-width:0.04em;">



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



![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter12-Arithmetic-16.webp)

对于第二页，把前面一位 cell 复制 4 次，形成 4-bit carry chain

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mover accent="true">
<msub>
<mi>

C

</mi>

<mrow>
<mi>

i

</mi>

<mo separator="true">

,

</mo>

<mn>

0

</mn>
</mrow>
</msub>

<mo stretchy="true">

‾

</mo>
</mover>

<mo>

→

</mo>

<mover accent="true">
<msub>
<mi>

C

</mi>

<mn>

0

</mn>
</msub>

<mo stretchy="true">

‾

</mo>
</mover>

<mo>

→

</mo>

<mover accent="true">
<msub>
<mi>

C

</mi>

<mn>

1

</mn>
</msub>

<mo stretchy="true">

‾

</mo>
</mover>

<mo>

→

</mo>

<mover accent="true">
<msub>
<mi>

C

</mi>

<mn>

2

</mn>
</msub>

<mo stretchy="true">

‾

</mo>
</mover>

<mo>

→

</mo>

<mover accent="true">
<msub>
<mi>

C

</mi>

<mn>

3

</mn>
</msub>

<mo stretchy="true">

‾

</mo>
</mover>
</mrow>

<annotation encoding="application/x-tex">

\overline{C_{i,0}} \rightarrow \overline{C_0} \rightarrow \overline{C_1} \rightarrow \overline{C_2} \rightarrow \overline{C_3}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.1694em;vertical-align:-0.2861em;">



</span>

<span className="mord,overline">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.8833em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

i

</span>

<span className="mpunct,mtight">

,

</span>

<span className="mord,mtight">

0

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

<span style="top:-3.8033em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="overline-line" style="border-bottom-width:0.04em;">



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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

→

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.0333em;vertical-align:-0.15em;">



</span>

<span className="mord,overline">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.8833em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">

0

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

<span style="top:-3.8033em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="overline-line" style="border-bottom-width:0.04em;">



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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

→

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.0333em;vertical-align:-0.15em;">



</span>

<span className="mord,overline">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.8833em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">

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

<span style="top:-3.8033em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="overline-line" style="border-bottom-width:0.04em;">



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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

→

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.0333em;vertical-align:-0.15em;">



</span>

<span className="mord,overline">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.8833em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
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

<span style="top:-3.8033em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="overline-line" style="border-bottom-width:0.04em;">



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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

→

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.0333em;vertical-align:-0.15em;">



</span>

<span className="mord,overline">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.8833em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">

3

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

<span style="top:-3.8033em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="overline-line" style="border-bottom-width:0.04em;">



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

普通 ripple-carry adder 每一位都要经过一个完整 FA 的 carry 逻辑：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<msub>
<mi>

C

</mi>

<mi>

i

</mi>
</msub>

<mo>

→

</mo>

<mi>

F

</mi>

<mi>

A

</mi>

<mo>

→

</mo>

<msub>
<mi>

C

</mi>

<mrow>
<mi>

i

</mi>

<mo>

+

</mo>

<mn>

1

</mn>
</mrow>
</msub>

<mspace linebreak="newline">



</mspace>

<msub>
<mi>

C

</mi>

<mi>

i

</mi>
</msub>

<mo>

→

</mo>

<mi>

F

</mi>

<mi>

A

</mi>

<mo>

→

</mo>

<msub>
<mi>

C

</mi>

<mrow>
<mi>

i

</mi>

<mo>

+

</mo>

<mn>

1

</mn>
</mrow>
</msub>

<msub>
<mi>

C

</mi>

<mi>

i

</mi>
</msub>

<mspace linebreak="newline">



</mspace>

<mo>

→

</mo>

<mi>

F

</mi>

<mi>

A

</mi>

<mo>

→

</mo>

<mi>

C

</mi>

<mi>

i

</mi>

<mo>

+

</mo>

<mn>

1

</mn>
</mrow>

<annotation encoding="application/x-tex">

C_i→FA→C_{i+1} \\    C_i \rightarrow FA \rightarrow C_{i+1}C_i \\ →FA→Ci+1

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
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

i

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

→

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

F

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
<span className="strut" style="height:0.8917em;vertical-align:-0.2083em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

i

</span>

<span className="mbin,mtight">

+

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
<span className="vlist" style="height:0.2083em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>

<span className="mspace,newline">



</span>

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
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

i

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

→

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

F

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
<span className="strut" style="height:0.8917em;vertical-align:-0.2083em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

i

</span>

<span className="mbin,mtight">

+

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
<span className="vlist" style="height:0.2083em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

i

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

<span className="mspace,newline">



</span>

<span className="base">
<span className="strut" style="height:0.3669em;">



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

F

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
<span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="mord,mathnormal">

i

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

1

</span>
</span>
</span>
</span>
</span>

而Manchester Carry Chain 的思路是：先把 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

A

</mi>

<mi>

i

</mi>
</msub>

<mo separator="true">

,

</mo>

<msub>
<mi>

B

</mi>

<mi>

i

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

A_i,B_i

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8778em;vertical-align:-0.1944em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

A

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

i

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

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0502em;">

B

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0502em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

i

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

 提前变成控制信号

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<msub>
<mi>

G

</mi>

<mi>

i

</mi>
</msub>

<mo>

=

</mo>

<msub>
<mi>

A

</mi>

<mi>

i

</mi>
</msub>

<msub>
<mi>

B

</mi>

<mi>

i

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

G_i=A_iB_i

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

G

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

i

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
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

A

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

i

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
<span className="mord,mathnormal" style="margin-right:0.0502em;">

B

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0502em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

i

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
</span>

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<msub>
<mi>

P

</mi>

<mi>

i

</mi>
</msub>

<mo>

=

</mo>

<msub>
<mi>

A

</mi>

<mi>

i

</mi>
</msub>

<mo>

⊕

</mo>

<msub>
<mi>

B

</mi>

<mi>

i

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

P_i=A_i\oplus B_i

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

P

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.1389em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

i

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
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

A

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

i

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

⊕

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0502em;">

B

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0502em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

i

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
</span>

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<msub>
<mi>

D

</mi>

<mi>

i

</mi>
</msub>

<mo>

=

</mo>

<mover accent="true">
<msub>
<mi>

A

</mi>

<mi>

i

</mi>
</msub>

<mo stretchy="true">

‾

</mo>
</mover>

<mover accent="true">
<msub>
<mi>

B

</mi>

<mi>

i

</mi>
</msub>

<mo stretchy="true">

‾

</mo>
</mover>
</mrow>

<annotation encoding="application/x-tex">

D_i=\overline{A_i}\overline{B_i}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

D

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0278em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

i

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
<span className="strut" style="height:1.0333em;vertical-align:-0.15em;">



</span>

<span className="mord,overline">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.8833em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord,mathnormal">

A

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

i

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

<span style="top:-3.8033em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="overline-line" style="border-bottom-width:0.04em;">



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

<span className="mord,overline">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.8833em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0502em;">

B

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0502em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

i

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

<span style="top:-3.8033em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="overline-line" style="border-bottom-width:0.04em;">



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

这些都先预计算好（**在 carry 到来之前就可以算好**），然后再来计算carry链

<mark>

但是如果所有位都是 propagate，那 carry 还是要穿过很多 pass transistor。链太长时，RC 延迟会变大，信号也可能变弱，

</mark>

<mark>

**所以 Manchester carry chain 通常适合做一小段高速 carry 链。**

</mark>

  长位宽还要配合分段、buffer、carry-bypass、carry-lookahead 等结构。

#### Carry-Bypass Adder ｜ 进位旁路/跳过加法器

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter12-Arithmetic-17.webp)

这个核心思想就是，如果P=1,那进位的输入就等于输出，如果有连续的一个block都是P=1的话，那么实际上就可以直接旁路一开始的<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

C

</mi>

<mi>

i

</mi>

<msub>
<mi>

n

</mi>

<mn>

0

</mn>
</msub>
</mrow>

<annotation encoding="application/x-tex">

Cin_0

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord">
<span className="mord,mathnormal">

n

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

0

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

，直接传输过来，节省了四个FA的运算时间（以上图作为例子）

**如果整个 block（比如选取四个FA作为一个Block） 都是 propagate，就直接跳过；否则说明 block 内部某一位会产生或杀死进位，就走普通 ripple 结果。**

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter12-Arithmetic-18.webp)

那么这个延迟时间计算：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<msub>
<mi>

t

</mi>

<mrow>
<mi>

a

</mi>

<mi>

d

</mi>

<mi>

d

</mi>

<mi>

e

</mi>

<mi>

r

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

s

</mi>

<mi>

e

</mi>

<mi>

t

</mi>

<mi>

u

</mi>

<mi>

p

</mi>
</mrow>
</msub>

<mo>

+

</mo>

<mi>

M

</mi>

<msub>
<mi>

t

</mi>

<mrow>
<mi>

c

</mi>

<mi>

a

</mi>

<mi>

r

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

+

</mo>

<mrow>
<mo fence="true">

(

</mo>

<mfrac>
<mi>

N

</mi>

<mi>

M

</mi>
</mfrac>

<mo>

−

</mo>

<mn>

2

</mn>

<mo fence="true">

)

</mo>
</mrow>

<msub>
<mi>

t

</mi>

<mrow>
<mi>

b

</mi>

<mi>

y

</mi>

<mi>

p

</mi>

<mi>

a

</mi>

<mi>

s

</mi>

<mi>

s

</mi>
</mrow>
</msub>

<mo>

+

</mo>

<mo stretchy="false">

(

</mo>

<mi>

M

</mi>

<mo>

−

</mo>

<mn>

1

</mn>

<mo stretchy="false">

)

</mo>

<msub>
<mi>

t

</mi>

<mrow>
<mi>

c

</mi>

<mi>

a

</mi>

<mi>

r

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

+

</mo>

<msub>
<mi>

t

</mi>

<mrow>
<mi>

s

</mi>

<mi>

u

</mi>

<mi>

m

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

t_{adder}=t_{setup}+Mt_{carry}+\left(\frac{N}{M}-2\right)t_{bypass}+(M-1)t_{carry}+t_{sum}

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
<span className="mord,mathnormal,mtight">

a

</span>

<span className="mord,mathnormal,mtight">

dd

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

er

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
<span className="strut" style="height:0.9012em;vertical-align:-0.2861em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

t

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

se

</span>

<span className="mord,mathnormal,mtight">

t

</span>

<span className="mord,mathnormal,mtight">

u

</span>

<span className="mord,mathnormal,mtight">

p

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

+

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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

c

</span>

<span className="mord,mathnormal,mtight">

a

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

r

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:2.4em;vertical-align:-0.95em;">



</span>

<span className="minner">
<span className="mopen,delimcenter" style="top:0em;">
<span className="delimsizing,size3">

(

</span>
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
<span className="mord,mathnormal" style="margin-right:0.109em;">

M

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
<span className="mord,mathnormal" style="margin-right:0.109em;">

N

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

−

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mord">

2

</span>

<span className="mclose,delimcenter" style="top:0em;">
<span className="delimsizing,size3">

)

</span>
</span>
</span>

<span className="mspace" style="margin-right:0.1667em;">



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
<span className="mord,mathnormal,mtight">

b

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

y

</span>

<span className="mord,mathnormal,mtight">

p

</span>

<span className="mord,mathnormal,mtight">

a

</span>

<span className="mord,mathnormal,mtight">

ss

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

<span className="mopen">

(

</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

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
<span className="strut" style="height:1.0361em;vertical-align:-0.2861em;">



</span>

<span className="mord">

1

</span>

<span className="mclose">

)

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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

c

</span>

<span className="mord,mathnormal,mtight">

a

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

r

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



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
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

s

</span>

<span className="mord,mathnormal,mtight">

u

</span>

<span className="mord,mathnormal,mtight">

m

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
</span>

这里：

- <span className="katex">
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

：总位数，比如 16 bit；
- <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

M

</mi>
</mrow>

<annotation encoding="application/x-tex">

M

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
</span>
</span>
</span>

：每个 block 的位数，比如 4 bit；
- <span className="katex">
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

s

</mi>

<mi>

e

</mi>

<mi>

t

</mi>

<mi>

u

</mi>

<mi>

p

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

t_{setup}

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
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

se

</span>

<span className="mord,mathnormal,mtight">

t

</span>

<span className="mord,mathnormal,mtight">

u

</span>

<span className="mord,mathnormal,mtight">

p

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

：提前算 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

P

</mi>

<mi>

i

</mi>
</msub>

<mo separator="true">

,

</mo>

<msub>
<mi>

G

</mi>

<mi>

i

</mi>
</msub>

<mo separator="true">

,

</mo>

<mi>

B

</mi>

<mi>

P

</mi>
</mrow>

<annotation encoding="application/x-tex">

P_i,G_i,BP

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8778em;vertical-align:-0.1944em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.1389em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

i

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

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

G

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

i

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

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0502em;">

B

</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>
</span>
</span>
</span>

 的时间；
- <span className="katex">
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

c

</mi>

<mi>

a

</mi>

<mi>

r

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

t_{carry}

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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

c

</span>

<span className="mord,mathnormal,mtight">

a

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

r

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

：carry 经过一位 FA 的时间；
- <span className="katex">
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

b

</mi>

<mi>

y

</mi>

<mi>

p

</mi>

<mi>

a

</mi>

<mi>

s

</mi>

<mi>

s

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

t_{bypass}

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
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

b

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

y

</span>

<span className="mord,mathnormal,mtight">

p

</span>

<span className="mord,mathnormal,mtight">

a

</span>

<span className="mord,mathnormal,mtight">

ss

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

：carry 经过一个 bypass MUX 的时间；
- <span className="katex">
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

s

</mi>

<mi>

u

</mi>

<mi>

m

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

t_{sum}

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
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

s

</span>

<span className="mord,mathnormal,mtight">

u

</span>

<span className="mord,mathnormal,mtight">

m

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

：最后生成 sum 的时间。

<alert type="tip">

这个公式怎么得出来的（为什么上面的这个式子是最坏情况）：

<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

P

</mi>

<mo>

=

</mo>

<mi>

A

</mi>

<mo>

⊕

</mo>

<mi>

B

</mi>
</mrow>

<annotation encoding="application/x-tex">

P=A\oplus B

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

A

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

⊕

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

, <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

G

</mi>

<mo>

=

</mo>

<mi>

A

</mi>

<mo>

⋅

</mo>

<mi>

B

</mi>
</mrow>

<annotation encoding="application/x-tex">

G=A\cdot B

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal">

G

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

<span className="mord,mathnormal">

A

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

⋅

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

，<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

C

</mi>

<mi>

o

</mi>
</msub>

<mo>

=

</mo>

<mi>

G

</mi>

<mo>

+

</mo>

<mi>

P

</mi>

<msub>
<mi>

C

</mi>

<mi>

i

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

C_o = G + P C_i

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
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

o

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
<span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">



</span>

<span className="mord,mathnormal">

G

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
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

i

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



如果P=1，那么G=0一定成立，所以这个时候Cin =  Cout，<mark>

但如果P=0，那么Co=G,此时就和这一级之前的加法器电路完全无关了，前面的延时不会被加进来

</mark>



所以说，<mark>

如果考虑Carry Bypass最坏情况下，应该是，第一个FA电路是P=0，无跳过的；剩下中间N/M-2个FA加法器都走Bypass路径（最后一个加法器不用管进位输出了）

</mark>

，那么这样时间就好算了：
<span className="katex">
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

s

</mi>

<mi>

e

</mi>

<mi>

t

</mi>

<mi>

u

</mi>

<mi>

p

</mi>
</mrow>
</msub>

<mo>

+

</mo>

<mi>

M

</mi>

<msub>
<mi>

t

</mi>

<mrow>
<mi>

c

</mi>

<mi>

a

</mi>

<mi>

r

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

t_{setup}+Mt_{carry}

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
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

se

</span>

<span className="mord,mathnormal,mtight">

t

</span>

<span className="mord,mathnormal,mtight">

u

</span>

<span className="mord,mathnormal,mtight">

p

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

+

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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

c

</span>

<span className="mord,mathnormal,mtight">

a

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

r

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

 是第一个FA的时间，<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mrow>
<mo fence="true">

(

</mo>

<mfrac>
<mi>

N

</mi>

<mi>

M

</mi>
</mfrac>

<mo>

−

</mo>

<mn>

2

</mn>

<mo fence="true">

)

</mo>
</mrow>

<msub>
<mi>

t

</mi>

<mrow>
<mi>

b

</mi>

<mi>

y

</mi>

<mi>

p

</mi>

<mi>

a

</mi>

<mi>

s

</mi>

<mi>

s

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

\left(\frac{N}{M}-2\right)t_{bypass}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.2223em;vertical-align:-0.35em;">



</span>

<span className="minner">
<span className="mopen,delimcenter" style="top:0em;">
<span className="delimsizing,size1">

(

</span>
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
<span className="mord,mathnormal,mtight" style="margin-right:0.109em;">

M

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

−

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mord">

2

</span>

<span className="mclose,delimcenter" style="top:0em;">
<span className="delimsizing,size1">

)

</span>
</span>
</span>

<span className="mspace" style="margin-right:0.1667em;">



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
<span className="mord,mathnormal,mtight">

b

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

y

</span>

<span className="mord,mathnormal,mtight">

p

</span>

<span className="mord,mathnormal,mtight">

a

</span>

<span className="mord,mathnormal,mtight">

ss

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

是中间N/M-2个FA加法器 的时间，<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mo stretchy="false">

(

</mo>

<mi>

M

</mi>

<mo>

−

</mo>

<mn>

1

</mn>

<mo stretchy="false">

)

</mo>

<msub>
<mi>

t

</mi>

<mrow>
<mi>

c

</mi>

<mi>

a

</mi>

<mi>

r

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

(M-1)t_{carry}

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

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

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
<span className="strut" style="height:1.0361em;vertical-align:-0.2861em;">



</span>

<span className="mord">

1

</span>

<span className="mclose">

)

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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

c

</span>

<span className="mord,mathnormal,mtight">

a

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

r

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

是对于最后一个加法器，实际上只需要计算剩余的M-1 个位就可以了，第M位是用来计算输出的进位的，但这个不在我们考虑范围内（我们只考虑sum的结果，不考虑sum的进位），所以是<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mo stretchy="false">

(

</mo>

<mi>

M

</mi>

<mo>

−

</mo>

<mn>

1

</mn>

<mo stretchy="false">

)

</mo>

<msub>
<mi>

t

</mi>

<mrow>
<mi>

c

</mi>

<mi>

a

</mi>

<mi>

r

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

(M-1)t_{carry}

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

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

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
<span className="strut" style="height:1.0361em;vertical-align:-0.2861em;">



</span>

<span className="mord">

1

</span>

<span className="mclose">

)

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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

c

</span>

<span className="mord,mathnormal,mtight">

a

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

r

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

,最后再加上sum的计算时间<span className="katex">
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

s

</mi>

<mi>

u

</mi>

<mi>

m

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

t_{sum}

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
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

s

</span>

<span className="mord,mathnormal,mtight">

u

</span>

<span className="mord,mathnormal,mtight">

m

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

,结果就是

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<msub>
<mi>

t

</mi>

<mrow>
<mi>

a

</mi>

<mi>

d

</mi>

<mi>

d

</mi>

<mi>

e

</mi>

<mi>

r

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

s

</mi>

<mi>

e

</mi>

<mi>

t

</mi>

<mi>

u

</mi>

<mi>

p

</mi>
</mrow>
</msub>

<mo>

+

</mo>

<mi>

M

</mi>

<msub>
<mi>

t

</mi>

<mrow>
<mi>

c

</mi>

<mi>

a

</mi>

<mi>

r

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

+

</mo>

<mrow>
<mo fence="true">

(

</mo>

<mfrac>
<mi>

N

</mi>

<mi>

M

</mi>
</mfrac>

<mo>

−

</mo>

<mn>

2

</mn>

<mo fence="true">

)

</mo>
</mrow>

<msub>
<mi>

t

</mi>

<mrow>
<mi>

b

</mi>

<mi>

y

</mi>

<mi>

p

</mi>

<mi>

a

</mi>

<mi>

s

</mi>

<mi>

s

</mi>
</mrow>
</msub>

<mo>

+

</mo>

<mo stretchy="false">

(

</mo>

<mi>

M

</mi>

<mo>

−

</mo>

<mn>

1

</mn>

<mo stretchy="false">

)

</mo>

<msub>
<mi>

t

</mi>

<mrow>
<mi>

c

</mi>

<mi>

a

</mi>

<mi>

r

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

+

</mo>

<msub>
<mi>

t

</mi>

<mrow>
<mi>

s

</mi>

<mi>

u

</mi>

<mi>

m

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

t_{adder}=t_{setup}+Mt_{carry}+\left(\frac{N}{M}-2\right)t_{bypass}+(M-1)t_{carry}+t_{sum}

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
<span className="mord,mathnormal,mtight">

a

</span>

<span className="mord,mathnormal,mtight">

dd

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

er

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
<span className="strut" style="height:0.9012em;vertical-align:-0.2861em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

t

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

se

</span>

<span className="mord,mathnormal,mtight">

t

</span>

<span className="mord,mathnormal,mtight">

u

</span>

<span className="mord,mathnormal,mtight">

p

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

+

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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

c

</span>

<span className="mord,mathnormal,mtight">

a

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

r

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:2.4em;vertical-align:-0.95em;">



</span>

<span className="minner">
<span className="mopen,delimcenter" style="top:0em;">
<span className="delimsizing,size3">

(

</span>
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
<span className="mord,mathnormal" style="margin-right:0.109em;">

M

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
<span className="mord,mathnormal" style="margin-right:0.109em;">

N

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

−

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mord">

2

</span>

<span className="mclose,delimcenter" style="top:0em;">
<span className="delimsizing,size3">

)

</span>
</span>
</span>

<span className="mspace" style="margin-right:0.1667em;">



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
<span className="mord,mathnormal,mtight">

b

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

y

</span>

<span className="mord,mathnormal,mtight">

p

</span>

<span className="mord,mathnormal,mtight">

a

</span>

<span className="mord,mathnormal,mtight">

ss

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

<span className="mopen">

(

</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

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
<span className="strut" style="height:1.0361em;vertical-align:-0.2861em;">



</span>

<span className="mord">

1

</span>

<span className="mclose">

)

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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

c

</span>

<span className="mord,mathnormal,mtight">

a

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

r

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



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
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

s

</span>

<span className="mord,mathnormal,mtight">

u

</span>

<span className="mord,mathnormal,mtight">

m

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
</span>
</alert>

##### Carry Ripple vs Carry Bypass 对比图

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter12-Arithmetic-19.webp)

Carry-bypass adder 也会随 (N) 增长，但斜率小一些，因为中间有些 block 可以 bypass；但是 carry-bypass 有额外开销：<span className="katex">
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

s

</mi>

<mi>

e

</mi>

<mi>

t

</mi>

<mi>

u

</mi>

<mi>

p

</mi>
</mrow>
</msub>

<mo separator="true">

,

</mo>

<mtext>



</mtext>

<mi>

B

</mi>

<mi>

P

</mi>

<mtext>

逻辑

</mtext>

<mo separator="true">

,

</mo>

<mtext>



</mtext>

<mi>

M

</mi>

<mi>

U

</mi>

<mi>

X

</mi>
</mrow>

<annotation encoding="application/x-tex">

t_{setup},\ BP\text{ 逻辑},\ MUX

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9694em;vertical-align:-0.2861em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

t

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

se

</span>

<span className="mord,mathnormal,mtight">

t

</span>

<span className="mord,mathnormal,mtight">

u

</span>

<span className="mord,mathnormal,mtight">

p

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

<span className="mpunct">

,

</span>

<span className="mspace">



</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0502em;">

B

</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="mord,text">
<span className="mord">



</span>

<span className="mord,cjk_fallback">

逻辑

</span>
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

<span className="mord,mathnormal" style="margin-right:0.109em;">

U

</span>

<span className="mord,mathnormal" style="margin-right:0.0785em;">

X

</span>
</span>
</span>
</span>



所以在位数很小时，它不一定比 ripple 快。图上标的 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mn>

4

</mn>

<mo>

∼

</mo>

<mn>

8

</mn>
</mrow>

<annotation encoding="application/x-tex">

4\sim8

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6444em;">



</span>

<span className="mord">

4

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

∼

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
</span>
</span>
</span>

：**通常位数大到一定程度后，carry-bypass 才开始明显优于 ripple。**

#### Carry-Select Adder ｜ 进位选择加法器

核心思想：<mark>

不等 carry 到了以后再算；先假设 carry-in=0 和 carry-in=1，把两种结果都提前算好。等真实 carry 到达时，用 MUX 选正确的结果——用面积换时间。

</mark>



<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 45.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter12-Arithmetic-20.webp" />
      </p>
    </td>
    
    
      <td style="width: 54.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter12-Arithmetic-21.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

##### Critical Path 分析  ｜ 关键路径分析

图里把 16-bit 分成 4 个 4-bit block，<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mtext>

Bit 0–3

</mtext>

<mo separator="true">

,

</mo>

<mspace width="1em">



</mspace>

<mtext>

Bit 4–7

</mtext>

<mo separator="true">

,

</mo>

<mspace width="1em">



</mspace>

<mtext>

Bit 8–11

</mtext>

<mo separator="true">

,

</mo>

<mspace width="1em">



</mspace>

<mtext>

Bit 12–15

</mtext>
</mrow>

<annotation encoding="application/x-tex">

\text{Bit 0–3},\quad \text{Bit 4–7},\quad \text{Bit 8–11},\quad \text{Bit 12–15}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8778em;vertical-align:-0.1944em;">



</span>

<span className="mord,text">
<span className="mord">

Bit 0–3

</span>
</span>

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:1em;">



</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord,text">
<span className="mord">

Bit 4–7

</span>
</span>

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:1em;">



</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord,text">
<span className="mord">

Bit 8–11

</span>
</span>

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:1em;">



</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord,text">
<span className="mord">

Bit 12–15

</span>
</span>
</span>
</span>
</span>

,每个 block 都提前算两套结果, 所以除了第一个 block 以外，后面 block 的内部 carry 结果其实都已经准备好了，关键路径实际上转换为：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mtext>

第一个 block 内部 carry 传播

</mtext>

<mo>

→

</mo>

<mtext>

MUX

</mtext>

<mo>

→

</mo>

<mtext>

MUX

</mtext>

<mo>

→

</mo>

<mtext>

MUX

</mtext>

<mo>

→

</mo>

<mtext>

MUX

</mtext>

<mo>

→

</mo>

<mtext>

最高位 sum

</mtext>
</mrow>

<annotation encoding="application/x-tex">

\text{第一个 block 内部 carry 传播} \rightarrow \text{MUX} \rightarrow \text{MUX} \rightarrow \text{MUX} \rightarrow \text{MUX} \rightarrow \text{最高位 sum}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,text">
<span className="mord,cjk_fallback">

第一个

</span>

<span className="mord">

block

</span>

<span className="mord,cjk_fallback">

内部

</span>

<span className="mord">

carry

</span>

<span className="mord,cjk_fallback">

传播

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
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,text">
<span className="mord">

MUX

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
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,text">
<span className="mord">

MUX

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
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,text">
<span className="mord">

MUX

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
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,text">
<span className="mord">

MUX

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
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,text">
<span className="mord,cjk_fallback">

最高位

</span>

<span className="mord">

sum

</span>
</span>
</span>
</span>
</span>
</span>

从而有

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<msub>
<mi>

T

</mi>

<mrow>
<mi>

a

</mi>

<mi>

d

</mi>

<mi>

d

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

s

</mi>

<mi>

e

</mi>

<mi>

t

</mi>

<mi>

u

</mi>

<mi>

p

</mi>
</mrow>
</msub>

<mo>

+

</mo>

<mi>

M

</mi>

<msub>
<mi>

t

</mi>

<mrow>
<mi>

c

</mi>

<mi>

a

</mi>

<mi>

r

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

+

</mo>

<mfrac>
<mi>

N

</mi>

<mi>

M

</mi>
</mfrac>

<msub>
<mi>

t

</mi>

<mrow>
<mi>

m

</mi>

<mi>

u

</mi>

<mi>

x

</mi>
</mrow>
</msub>

<mo>

+

</mo>

<msub>
<mi>

t

</mi>

<mrow>
<mi>

s

</mi>

<mi>

u

</mi>

<mi>

m

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

T_{add}=t_{setup}+Mt_{carry}+\frac{N}{M}t_{mux}+t_{sum}

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

a

</span>

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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

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
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

se

</span>

<span className="mord,mathnormal,mtight">

t

</span>

<span className="mord,mathnormal,mtight">

u

</span>

<span className="mord,mathnormal,mtight">

p

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

+

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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

c

</span>

<span className="mord,mathnormal,mtight">

a

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

r

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



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
<span className="mord,mathnormal" style="margin-right:0.109em;">

M

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
<span className="mord,mathnormal" style="margin-right:0.109em;">

N

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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

m

</span>

<span className="mord,mathnormal,mtight">

ux

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
<span className="strut" style="height:0.7651em;vertical-align:-0.15em;">



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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

s

</span>

<span className="mord,mathnormal,mtight">

u

</span>

<span className="mord,mathnormal,mtight">

m

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
</span>

其中：

- <span className="katex">
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

：总位数；
- <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

M

</mi>
</mrow>

<annotation encoding="application/x-tex">

M

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
</span>
</span>
</span>

：每个 block 的位数；
- <span className="katex">
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

s

</mi>

<mi>

e

</mi>

<mi>

t

</mi>

<mi>

u

</mi>

<mi>

p

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

t_{setup}

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
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

se

</span>

<span className="mord,mathnormal,mtight">

t

</span>

<span className="mord,mathnormal,mtight">

u

</span>

<span className="mord,mathnormal,mtight">

p

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

：计算 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

P

</mi>

<mo separator="true">

,

</mo>

<mi>

G

</mi>
</mrow>

<annotation encoding="application/x-tex">

P,G

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8778em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord,mathnormal">

G

</span>
</span>
</span>
</span>

 的时间；
- <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

M

</mi>

<msub>
<mi>

t

</mi>

<mrow>
<mi>

c

</mi>

<mi>

a

</mi>

<mi>

r

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

Mt_{carry}

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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

c

</span>

<span className="mord,mathnormal,mtight">

a

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

r

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

：第一个 block 内部产生 carry 的时间；
- <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mfrac>
<mi>

N

</mi>

<mi>

M

</mi>
</mfrac>

<msub>
<mi>

t

</mi>

<mrow>
<mi>

m

</mi>

<mi>

u

</mi>

<mi>

x

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

\frac{N}{M}t_{mux}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
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
<span className="mord,mathnormal,mtight" style="margin-right:0.109em;">

M

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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

m

</span>

<span className="mord,mathnormal,mtight">

ux

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

：一共有 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mfrac>
<mi>

N

</mi>

<mi>

M

</mi>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

\frac{N}{M}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
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
<span className="mord,mathnormal,mtight" style="margin-right:0.109em;">

M

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

 个 block，所以真实 carry 要经过这么多个 MUX；
- <span className="katex">
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

s

</mi>

<mi>

u

</mi>

<mi>

m

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

t_{sum}

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
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

s

</span>

<span className="mord,mathnormal,mtight">

u

</span>

<span className="mord,mathnormal,mtight">

m

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

：最后生成 sum 的时间。

> 这次注意，实际上会经过N/M个mux

细节查看下图蓝线

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter12-Arithmetic-22.webp)

##### Square Root Carry Select Adder ｜ 平方根进位选择加法器

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter12-Arithmetic-23.webp)

前面提到的是等分的block，如果block不等分，而是呈等差数列 逐级递增+1的话，最终计算式子如下：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

N

</mi>

<mo>

=

</mo>

<mi>

M

</mi>

<mo>

+

</mo>

<mo stretchy="false">

(

</mo>

<mi>

M

</mi>

<mo>

+

</mo>

<mn>

1

</mn>

<mo stretchy="false">

)

</mo>

<mo>

+

</mo>

<mo stretchy="false">

(

</mo>

<mi>

M

</mi>

<mo>

+

</mo>

<mn>

2

</mn>

<mo stretchy="false">

)

</mo>

<mo>

+

</mo>

<mo>

⋯

</mo>

<mo>

+

</mo>

<mo stretchy="false">

(

</mo>

<mi>

M

</mi>

<mo>

+

</mo>

<mi>

P

</mi>

<mo>

−

</mo>

<mn>

1

</mn>

<mo stretchy="false">

)

</mo>

<mo>

=

</mo>

<mfrac>
<msup>
<mi>

P

</mi>

<mn>

2

</mn>
</msup>

<mn>

2

</mn>
</mfrac>

<mo>

+

</mo>

<mi>

P

</mi>

<mrow>
<mo fence="true">

(

</mo>

<mi>

M

</mi>

<mo>

−

</mo>

<mfrac>
<mn>

1

</mn>

<mn>

2

</mn>
</mfrac>

<mo fence="true">

)

</mo>
</mrow>
</mrow>

<annotation encoding="application/x-tex">

N=M+(M+1)+(M+2)+\cdots+(M+P-1) = \frac{P^2}{2}+P\left(M-\frac{1}{2}\right)

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

M

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

<span className="mopen">

(

</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

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

<span className="mopen">

(

</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

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
<span className="strut" style="height:0.6667em;vertical-align:-0.0833em;">



</span>

<span className="minner">

⋯

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

<span className="mopen">

(

</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

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

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

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

<span className="mord">

1

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
<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:2.4em;vertical-align:-0.95em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="minner">
<span className="mopen,delimcenter" style="top:0em;">
<span className="delimsizing,size3">

(

</span>
</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

−

</span>

<span className="mspace" style="margin-right:0.2222em;">



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

<span className="mclose,delimcenter" style="top:0em;">
<span className="delimsizing,size3">

)

</span>
</span>
</span>
</span>
</span>
</span>
</span>

后面一项在N很大的时候可以忽略

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

N

</mi>

<mo>

=

</mo>

<mfrac>
<msup>
<mi>

P

</mi>

<mn>

2

</mn>
</msup>

<mn>

2

</mn>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

N= \frac{P^2}{2}

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
<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

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

延迟就变成了

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<msub>
<mi>

T

</mi>

<mrow>
<mi>

a

</mi>

<mi>

d

</mi>

<mi>

d

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

s

</mi>

<mi>

e

</mi>

<mi>

t

</mi>

<mi>

u

</mi>

<mi>

p

</mi>
</mrow>
</msub>

<mo>

+

</mo>

<mi>

M

</mi>

<msub>
<mi>

t

</mi>

<mrow>
<mi>

c

</mi>

<mi>

a

</mi>

<mi>

r

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

+

</mo>

<mi>

P

</mi>

<msub>
<mi>

t

</mi>

<mrow>
<mi>

m

</mi>

<mi>

u

</mi>

<mi>

x

</mi>
</mrow>
</msub>

<mo>

+

</mo>

<msub>
<mi>

t

</mi>

<mrow>
<mi>

s

</mi>

<mi>

u

</mi>

<mi>

m

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

T_{add}=t_{setup}+Mt_{carry}+Pt_{mux}+t_{sum}

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

a

</span>

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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

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
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

se

</span>

<span className="mord,mathnormal,mtight">

t

</span>

<span className="mord,mathnormal,mtight">

u

</span>

<span className="mord,mathnormal,mtight">

p

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

+

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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

c

</span>

<span className="mord,mathnormal,mtight">

a

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

r

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

m

</span>

<span className="mord,mathnormal,mtight">

ux

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
<span className="strut" style="height:0.7651em;vertical-align:-0.15em;">



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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

s

</span>

<span className="mord,mathnormal,mtight">

u

</span>

<span className="mord,mathnormal,mtight">

m

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
</span>

当 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

P

</mi>
</mrow>

<annotation encoding="application/x-tex">

P

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
</span>
</span>
</span>

 近似为 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msqrt>
<mrow>
<mn>

2

</mn>

<mi>

N

</mi>
</mrow>
</msqrt>
</mrow>

<annotation encoding="application/x-tex">

\sqrt{2N}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.04em;vertical-align:-0.1133em;">



</span>

<span className="mord,sqrt">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.9267em;">
<span className="svg-align" style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord" style="padding-left:0.833em;">
<span className="mord">

2

</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

N

</span>
</span>
</span>

<span style="top:-2.8867em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="hide-tail" style="min-width:0.853em;height:1.08em;">
<svg xmlns="http://www.w3.org/2000/svg" width="400em" height="1.08em" viewBox="0 0 400000 1080" preserveAspectRatio="xMinYMin slice">
<path d="M95,702
c-2.7,0,-7.17,-2.7,-13.5,-8c-5.8,-5.3,-9.5,-10,-9.5,-14
c0,-2,0.3,-3.3,1,-4c1.3,-2.7,23.83,-20.7,67.5,-54
c44.2,-33.3,65.8,-50.3,66.5,-51c1.3,-1.3,3,-2,5,-2c4.7,0,8.7,3.3,12,10
s173,378,173,378c0.7,0,35.3,-71,104,-213c68.7,-142,137.5,-285,206.5,-429
c69,-144,104.5,-217.7,106.5,-221
l0 -0
c5.3,-9.3,12,-14,20,-14
H400000v40H845.2724
s-225.272,467,-225.272,467s-235,486,-235,486c-2.7,4.7,-9,7,-19,7
c-6,0,-10,-1,-12,-3s-194,-422,-194,-422s-65,47,-65,47z
M834 80h400000v40h-400000z">



</path>
</svg>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.1133em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

 时，延迟写成：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<msub>
<mi>

T

</mi>

<mrow>
<mi>

a

</mi>

<mi>

d

</mi>

<mi>

d

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

s

</mi>

<mi>

e

</mi>

<mi>

t

</mi>

<mi>

u

</mi>

<mi>

p

</mi>
</mrow>
</msub>

<mo>

+

</mo>

<mi>

M

</mi>

<msub>
<mi>

t

</mi>

<mrow>
<mi>

c

</mi>

<mi>

a

</mi>

<mi>

r

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

+

</mo>

<msqrt>
<mrow>
<mn>

2

</mn>

<mi>

N

</mi>
</mrow>
</msqrt>

<msub>
<mi>

t

</mi>

<mrow>
<mi>

m

</mi>

<mi>

u

</mi>

<mi>

x

</mi>
</mrow>
</msub>

<mo>

+

</mo>

<msub>
<mi>

t

</mi>

<mrow>
<mi>

s

</mi>

<mi>

u

</mi>

<mi>

m

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

T_{add}=t_{setup}+Mt_{carry}+\sqrt{2N} t_{mux}+t_{sum}

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

a

</span>

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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

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
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

se

</span>

<span className="mord,mathnormal,mtight">

t

</span>

<span className="mord,mathnormal,mtight">

u

</span>

<span className="mord,mathnormal,mtight">

p

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

+

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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

c

</span>

<span className="mord,mathnormal,mtight">

a

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

r

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.1255em;vertical-align:-0.15em;">



</span>

<span className="mord,sqrt">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.9755em;">
<span className="svg-align" style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord" style="padding-left:0.833em;">
<span className="mord">

2

</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

N

</span>
</span>
</span>

<span style="top:-2.9355em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="hide-tail" style="min-width:0.853em;height:1.08em;">
<svg xmlns="http://www.w3.org/2000/svg" width="400em" height="1.08em" viewBox="0 0 400000 1080" preserveAspectRatio="xMinYMin slice">
<path d="M95,702
c-2.7,0,-7.17,-2.7,-13.5,-8c-5.8,-5.3,-9.5,-10,-9.5,-14
c0,-2,0.3,-3.3,1,-4c1.3,-2.7,23.83,-20.7,67.5,-54
c44.2,-33.3,65.8,-50.3,66.5,-51c1.3,-1.3,3,-2,5,-2c4.7,0,8.7,3.3,12,10
s173,378,173,378c0.7,0,35.3,-71,104,-213c68.7,-142,137.5,-285,206.5,-429
c69,-144,104.5,-217.7,106.5,-221
l0 -0
c5.3,-9.3,12,-14,20,-14
H400000v40H845.2724
s-225.272,467,-225.272,467s-235,486,-235,486c-2.7,4.7,-9,7,-19,7
c-6,0,-10,-1,-12,-3s-194,-422,-194,-422s-65,47,-65,47z
M834 80h400000v40h-400000z">



</path>
</svg>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.0645em;">
<span>



</span>
</span>
</span>
</span>
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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

m

</span>

<span className="mord,mathnormal,mtight">

ux

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
<span className="strut" style="height:0.7651em;vertical-align:-0.15em;">



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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

s

</span>

<span className="mord,mathnormal,mtight">

u

</span>

<span className="mord,mathnormal,mtight">

m

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
</span>

因此叫做平方根进位选择加法器

##### 对比关键路径

这个就是把时间和N的关系画了一个图来对比一下，没啥好说的 后面这俩性能比较好

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter12-Arithmetic-24.webp)

## 1’s & 0’s Detectors ｜ 全 1 / 全 0 检测器

**功能**：判断一个多 bit 信号是不是全 1 或全 0

比如 8-bit 输入：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

A

</mi>

<mn>

7

</mn>
</msub>

<msub>
<mi>

A

</mi>

<mn>

6

</mn>
</msub>

<msub>
<mi>

A

</mi>

<mn>

5

</mn>
</msub>

<msub>
<mi>

A

</mi>

<mn>

4

</mn>
</msub>

<msub>
<mi>

A

</mi>

<mn>

3

</mn>
</msub>

<msub>
<mi>

A

</mi>

<mn>

2

</mn>
</msub>

<msub>
<mi>

A

</mi>

<mn>

1

</mn>
</msub>

<msub>
<mi>

A

</mi>

<mn>

0

</mn>
</msub>
</mrow>

<annotation encoding="application/x-tex">

A_7A_6A_5A_4A_3A_2A_1A_0

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

A

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

7

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

A

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

6

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

A

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

5

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

A

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

4

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

A

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

3

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

A

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

<span className="mord">
<span className="mord,mathnormal">

A

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

A

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

0

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

,只有当所有位都是 1 时，全 1 检测器输出才是 1：

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter12-Arithmetic-25.webp)

<mark>

大 fan-in 门不好做，直接做一个 8 输入 AND，晶体管串并联会很复杂，延迟和面积都不好。

</mark>



所以课件给了几种实现方式：

1. balanced tree：平衡树结构，层数少，比较规整；
2. skewed chain：偏斜链式结构，适合某些输入更关键的情况；
3. transistor-level detector：直接用晶体管拉高/拉低节点，比如全 0 检测常可以做成 NOR 型结构。

## Equality Comparator ｜ 相等比较器

顾名思义。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter12-Arithmetic-26.webp)

有意思的一个点是——**equality comparator 本质是bitwise XNOR +allones detector**，即先采用**异或非/同或**逻辑，然后去判断这几个位是否全是1，如果不全是1，就说明不相等，那实际上就是全 1 检测器

## Magnitude Comparator ｜ 大小比较器

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter12-Arithmetic-27.webp)

实际上是计算B-A 然后再看符号位和sum值来判断

## Counters ｜ 计数器

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter12-Arithmetic-28.webp)

### binary counter｜二进制计数器

N-bit binary counter 会按二进制顺序计数：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mn>

0000

</mn>

<mo>

→

</mo>

<mn>

0001

</mn>

<mo>

→

</mo>

<mn>

0010

</mn>

<mo>

→

</mo>

<mn>

0011

</mn>

<mo>

→

</mo>

<mo>

⋯

</mo>
</mrow>

<annotation encoding="application/x-tex">

0000 \rightarrow 0001 \rightarrow 0010 \rightarrow 0011 \rightarrow \cdots

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6444em;">



</span>

<span className="mord">

0000

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
<span className="strut" style="height:0.6444em;">



</span>

<span className="mord">

0001

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
<span className="strut" style="height:0.6444em;">



</span>

<span className="mord">

0010

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
<span className="strut" style="height:0.6444em;">



</span>

<span className="mord">

0011

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
<span className="strut" style="height:0.313em;">



</span>

<span className="minner">

⋯

</span>
</span>
</span>
</span>



一个 N-bit counter 有<span className="katex">
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
</mrow>

<annotation encoding="application/x-tex">

2^N

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
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

N

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

个状态（使用有限状态机来实现——数电内容，时序逻辑电路）

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter12-Arithmetic-29.webp)

图里的 synchronous counter 是同步计数器，所有寄存器都由同一个 clock 触发，不是一位一位异步翻转。

TC 是 terminal count，终端计数信号；<mark>

比如向上计数时：Q=1111，再加 1 就溢出回到 0000，这时可以产生 TC。

</mark>



![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter12-Arithmetic-30.webp)

这张图是一个带功能选择的同步计数器：

- up/down：控制加 1 还是减 1；
- load：允许直接装载外部数据 (D)；
- reset：复位；
- enable：允许计数；
- TC：终端计数输出。

### **LFSR linear-feedback shift register ｜ 线性反馈移位寄存器**

**LFSR，linear-feedback shift register，线性反馈移位寄存器** 也是一个 N-bit 寄存器，但它不是简单加 1，而是：每个时钟把寄存器整体移位，然后把某几位 XOR 的结果反馈到最高位或最低位。

N 位 LFSR 最多可以遍历除全 0 外的所有 <span className="katex">
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

<mo>

−

</mo>

<mn>

1

</mn>
</mrow>

<annotation encoding="application/x-tex">

2^N-1

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
</span>
</span>
</span>

 个状态，但顺序不是正常二进制递增，而是看起来像<mark>

**随机的伪随机顺序**

</mark>

。

## Multiplier ｜ 乘法器设计

### The Binary Multiplication ｜ 二进制乘法

1. 二进制数的按位展开
设 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

X

</mi>
</mrow>

<annotation encoding="application/x-tex">

X

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0785em;">

X

</span>
</span>
</span>
</span>

 是 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

M

</mi>
</mrow>

<annotation encoding="application/x-tex">

M

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
</span>
</span>
</span>

 位二进制数，<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

Y

</mi>
</mrow>

<annotation encoding="application/x-tex">

Y

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.2222em;">

Y

</span>
</span>
</span>
</span>

 是 <span className="katex">
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

 位二进制数，则：<br />

<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

X

</mi>

<mo>

=

</mo>

<msubsup>
<mo>

∑

</mo>

<mrow>
<mi>

i

</mi>

<mo>

=

</mo>

<mn>

0

</mn>
</mrow>

<mrow>
<mi>

M

</mi>

<mo>

−

</mo>

<mn>

1

</mn>
</mrow>
</msubsup>

<msub>
<mi>

X

</mi>

<mi>

i

</mi>
</msub>

<msup>
<mn>

2

</mn>

<mi>

i

</mi>
</msup>
</mrow>

<annotation encoding="application/x-tex">

X=\sum_{i=0}^{M-1}X_i2^i

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0785em;">

X

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
<span className="strut" style="height:1.2809em;vertical-align:-0.2997em;">



</span>

<span className="mop">
<span className="mop,op-symbol,small-op" style="position:relative;top:0em;">

∑

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.9812em;">
<span style="top:-2.4003em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

i

</span>

<span className="mrel,mtight">

=

</span>

<span className="mord,mtight">

0

</span>
</span>
</span>
</span>

<span style="top:-3.2029em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.109em;">

M

</span>

<span className="mbin,mtight">

−

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
<span className="vlist" style="height:0.2997em;">
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
<span className="mord,mathnormal" style="margin-right:0.0785em;">

X

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0785em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

i

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
<span className="mord">

2

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8247em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

i

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

，<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

Y

</mi>

<mo>

=

</mo>

<msubsup>
<mo>

∑

</mo>

<mrow>
<mi>

j

</mi>

<mo>

=

</mo>

<mn>

0

</mn>
</mrow>

<mrow>
<mi>

N

</mi>

<mo>

−

</mo>

<mn>

1

</mn>
</mrow>
</msubsup>

<msub>
<mi>

Y

</mi>

<mi>

j

</mi>
</msub>

<msup>
<mn>

2

</mn>

<mi>

j

</mi>
</msup>
</mrow>

<annotation encoding="application/x-tex">

Y=\sum_{j=0}^{N-1}Y_j2^j

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.2222em;">

Y

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
<span className="strut" style="height:1.417em;vertical-align:-0.4358em;">



</span>

<span className="mop">
<span className="mop,op-symbol,small-op" style="position:relative;top:0em;">

∑

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.9812em;">
<span style="top:-2.4003em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0572em;">

j

</span>

<span className="mrel,mtight">

=

</span>

<span className="mord,mtight">

0

</span>
</span>
</span>
</span>

<span style="top:-3.2029em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.109em;">

N

</span>

<span className="mbin,mtight">

−

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
<span className="vlist" style="height:0.4358em;">
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
<span className="mord,mathnormal" style="margin-right:0.2222em;">

Y

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0572em;">

j

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

<span className="mord">
<span className="mord">

2

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8247em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0572em;">

j

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

。<br />

其中，<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

X

</mi>

<mi>

i

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

X_i

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

X

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0785em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

i

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

 和 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

Y

</mi>

<mi>

j

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

Y_j

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9694em;vertical-align:-0.2861em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.2222em;">

Y

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0572em;">

j

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

 都是单个 bit，只能取 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mn>

0

</mn>
</mrow>

<annotation encoding="application/x-tex">

0

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
</span>
</span>
</span>

 或 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mn>

1

</mn>
</mrow>

<annotation encoding="application/x-tex">

1

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
</span>
</span>
</span>

。
2. 乘法的数学展开
乘积为 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

Z

</mi>

<mo>

=

</mo>

<mi>

X

</mi>

<mo>

×

</mo>

<mi>

Y

</mi>
</mrow>

<annotation encoding="application/x-tex">

Z=X\times Y

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

Z

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

X

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

<span className="mord,mathnormal" style="margin-right:0.2222em;">

Y

</span>
</span>
</span>
</span>

。<br />

把 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

X

</mi>
</mrow>

<annotation encoding="application/x-tex">

X

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0785em;">

X

</span>
</span>
</span>
</span>

 和 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

Y

</mi>
</mrow>

<annotation encoding="application/x-tex">

Y

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.2222em;">

Y

</span>
</span>
</span>
</span>

 的按位展开代入：<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

Z

</mi>

<mo>

=

</mo>

<mrow>
<mo fence="true">

(

</mo>

<munderover>
<mo>

∑

</mo>

<mrow>
<mi>

i

</mi>

<mo>

=

</mo>

<mn>

0

</mn>
</mrow>

<mrow>
<mi>

M

</mi>

<mo>

−

</mo>

<mn>

1

</mn>
</mrow>
</munderover>

<msub>
<mi>

X

</mi>

<mi>

i

</mi>
</msub>

<msup>
<mn>

2

</mn>

<mi>

i

</mi>
</msup>

<mo fence="true">

)

</mo>
</mrow>

<mrow>
<mo fence="true">

(

</mo>

<munderover>
<mo>

∑

</mo>

<mrow>
<mi>

j

</mi>

<mo>

=

</mo>

<mn>

0

</mn>
</mrow>

<mrow>
<mi>

N

</mi>

<mo>

−

</mo>

<mn>

1

</mn>
</mrow>
</munderover>

<msub>
<mi>

Y

</mi>

<mi>

j

</mi>
</msub>

<msup>
<mn>

2

</mn>

<mi>

j

</mi>
</msup>

<mo fence="true">

)

</mo>
</mrow>
</mrow>

<annotation encoding="application/x-tex">

Z=\left(\sum_{i=0}^{M-1}X_i2^i\right)\left(\sum_{j=0}^{N-1}Y_j2^j\right)

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

Z

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
<span className="strut" style="height:3.2421em;vertical-align:-1.4138em;">



</span>

<span className="minner">
<span className="mopen,delimcenter" style="top:0em;">
<span className="delimsizing,size4">

(

</span>
</span>

<span className="mop,op-limits">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:1.8283em;">
<span style="top:-1.8723em;margin-left:0em;">
<span className="pstrut" style="height:3.05em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

i

</span>

<span className="mrel,mtight">

=

</span>

<span className="mord,mtight">

0

</span>
</span>
</span>
</span>

<span style="top:-3.05em;">
<span className="pstrut" style="height:3.05em;">



</span>

<span>
<span className="mop,op-symbol,large-op">

∑

</span>
</span>
</span>

<span style="top:-4.3em;margin-left:0em;">
<span className="pstrut" style="height:3.05em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.109em;">

M

</span>

<span className="mbin,mtight">

−

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
<span className="vlist" style="height:1.2777em;">
<span>



</span>
</span>
</span>
</span>
</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0785em;">

X

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0785em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

i

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
<span className="mord">

2

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8747em;">
<span style="top:-3.113em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

i

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

<span className="mclose,delimcenter" style="top:0em;">
<span className="delimsizing,size4">

)

</span>
</span>
</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="minner">
<span className="mopen,delimcenter" style="top:0em;">
<span className="delimsizing,size4">

(

</span>
</span>

<span className="mop,op-limits">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:1.8283em;">
<span style="top:-1.8723em;margin-left:0em;">
<span className="pstrut" style="height:3.05em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0572em;">

j

</span>

<span className="mrel,mtight">

=

</span>

<span className="mord,mtight">

0

</span>
</span>
</span>
</span>

<span style="top:-3.05em;">
<span className="pstrut" style="height:3.05em;">



</span>

<span>
<span className="mop,op-symbol,large-op">

∑

</span>
</span>
</span>

<span style="top:-4.3em;margin-left:0em;">
<span className="pstrut" style="height:3.05em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.109em;">

N

</span>

<span className="mbin,mtight">

−

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
<span className="vlist" style="height:1.4138em;">
<span>



</span>
</span>
</span>
</span>
</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.2222em;">

Y

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0572em;">

j

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

<span className="mord">
<span className="mord">

2

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8747em;">
<span style="top:-3.113em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0572em;">

j

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

<span className="mclose,delimcenter" style="top:0em;">
<span className="delimsizing,size4">

)

</span>
</span>
</span>
</span>
</span>
</span>
</span>

根据乘法分配律展开：

<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

Z

</mi>

<mo>

=

</mo>

<msubsup>
<mo>

∑

</mo>

<mrow>
<mi>

i

</mi>

<mo>

=

</mo>

<mn>

0

</mn>
</mrow>

<mrow>
<mi>

M

</mi>

<mo>

−

</mo>

<mn>

1

</mn>
</mrow>
</msubsup>

<msubsup>
<mo>

∑

</mo>

<mrow>
<mi>

j

</mi>

<mo>

=

</mo>

<mn>

0

</mn>
</mrow>

<mrow>
<mi>

N

</mi>

<mo>

−

</mo>

<mn>

1

</mn>
</mrow>
</msubsup>

<msub>
<mi>

X

</mi>

<mi>

i

</mi>
</msub>

<msub>
<mi>

Y

</mi>

<mi>

j

</mi>
</msub>

<msup>
<mn>

2

</mn>

<mrow>
<mi>

i

</mi>

<mo>

+

</mo>

<mi>

j

</mi>
</mrow>
</msup>
</mrow>

<annotation encoding="application/x-tex">

Z=\sum_{i=0}^{M-1}\sum_{j=0}^{N-1}X_iY_j2^{i+j}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

Z

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
<span className="strut" style="height:1.417em;vertical-align:-0.4358em;">



</span>

<span className="mop">
<span className="mop,op-symbol,small-op" style="position:relative;top:0em;">

∑

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.9812em;">
<span style="top:-2.4003em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

i

</span>

<span className="mrel,mtight">

=

</span>

<span className="mord,mtight">

0

</span>
</span>
</span>
</span>

<span style="top:-3.2029em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.109em;">

M

</span>

<span className="mbin,mtight">

−

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
<span className="vlist" style="height:0.2997em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mop">
<span className="mop,op-symbol,small-op" style="position:relative;top:0em;">

∑

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.9812em;">
<span style="top:-2.4003em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0572em;">

j

</span>

<span className="mrel,mtight">

=

</span>

<span className="mord,mtight">

0

</span>
</span>
</span>
</span>

<span style="top:-3.2029em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.109em;">

N

</span>

<span className="mbin,mtight">

−

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
<span className="vlist" style="height:0.4358em;">
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
<span className="mord,mathnormal" style="margin-right:0.0785em;">

X

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0785em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

i

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
<span className="mord,mathnormal" style="margin-right:0.2222em;">

Y

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0572em;">

j

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

<span className="mord">
<span className="mord">

2

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8247em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

i

</span>

<span className="mbin,mtight">

+

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0572em;">

j

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

。

这个式子说明：**二进制乘法可以分解成很多个** <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

X

</mi>

<mi>

i

</mi>
</msub>

<msub>
<mi>

Y

</mi>

<mi>

j

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

X_iY_j

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9694em;vertical-align:-0.2861em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0785em;">

X

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0785em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

i

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
<span className="mord,mathnormal" style="margin-right:0.2222em;">

Y

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0572em;">

j

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

 **的部分积相加。**

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter12-Arithmetic-31.webp)

1. Partial Product：部分积
每一个 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

X

</mi>

<mi>

i

</mi>
</msub>

<msub>
<mi>

Y

</mi>

<mi>

j

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

X_iY_j

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9694em;vertical-align:-0.2861em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0785em;">

X

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0785em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

i

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
<span className="mord,mathnormal" style="margin-right:0.2222em;">

Y

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0572em;">

j

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

 叫做一个 **partial product，部分积**。<br />

因为 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

X

</mi>

<mi>

i

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

X_i

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

X

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0785em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

i

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

 和 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

Y

</mi>

<mi>

j

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

Y_j

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9694em;vertical-align:-0.2861em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.2222em;">

Y

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0572em;">

j

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

 都是二进制位，所以 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

X

</mi>

<mi>

i

</mi>
</msub>

<msub>
<mi>

Y

</mi>

<mi>

j

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

X_iY_j

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9694em;vertical-align:-0.2861em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0785em;">

X

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0785em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

i

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
<span className="mord,mathnormal" style="margin-right:0.2222em;">

Y

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0572em;">

j

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

 在硬件中可以直接用 **AND 门** 生成。<br />

也就是：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

P

</mi>

<mrow>
<mi>

i

</mi>

<mi>

j

</mi>
</mrow>
</msub>

<mo>

=

</mo>

<msub>
<mi>

X

</mi>

<mi>

i

</mi>
</msub>

<msub>
<mi>

Y

</mi>

<mi>

j

</mi>
</msub>

<mo>

=

</mo>

<msub>
<mi>

X

</mi>

<mi>

i

</mi>
</msub>

<mo>

∧

</mo>

<msub>
<mi>

Y

</mi>

<mi>

j

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

P_{ij}=X_iY_j=X_i\land Y_j

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9694em;vertical-align:-0.2861em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.1389em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0572em;">

ij

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
<span className="strut" style="height:0.9694em;vertical-align:-0.2861em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0785em;">

X

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0785em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

i

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
<span className="mord,mathnormal" style="margin-right:0.2222em;">

Y

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0572em;">

j

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
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0785em;">

X

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0785em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

i

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

∧

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.9694em;vertical-align:-0.2861em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.2222em;">

Y

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0572em;">

j

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

<br />

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter12-Arithmetic-32.webp)

由于 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msup>
<mn>

2

</mn>

<mi>

i

</mi>
</msup>

<mo>

⋅

</mo>

<msup>
<mn>

2

</mn>

<mi>

j

</mi>
</msup>

<mo>

=

</mo>

<msup>
<mn>

2

</mn>

<mrow>
<mi>

i

</mi>

<mo>

+

</mo>

<mi>

j

</mi>
</mrow>
</msup>
</mrow>

<annotation encoding="application/x-tex">

2^i\cdot2^j=2^{i+j}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8247em;">



</span>

<span className="mord">
<span className="mord">

2

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8247em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

i

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

⋅

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8247em;">



</span>

<span className="mord">
<span className="mord">

2

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8247em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0572em;">

j

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
<span className="strut" style="height:0.8247em;">



</span>

<span className="mord">
<span className="mord">

2

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8247em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

i

</span>

<span className="mbin,mtight">

+

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0572em;">

j

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

，所以部分积 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

X

</mi>

<mi>

i

</mi>
</msub>

<msub>
<mi>

Y

</mi>

<mi>

j

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

X_iY_j

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9694em;vertical-align:-0.2861em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0785em;">

X

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0785em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

i

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
<span className="mord,mathnormal" style="margin-right:0.2222em;">

Y

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0572em;">

j

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

 的权重是 <span className="katex">
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

i

</mi>

<mo>

+

</mo>

<mi>

j

</mi>
</mrow>
</msup>
</mrow>

<annotation encoding="application/x-tex">

2^{i+j}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8247em;">



</span>

<span className="mord">
<span className="mord">

2

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8247em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

i

</span>

<span className="mbin,mtight">

+

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0572em;">

j

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

。因此，<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

X

</mi>

<mi>

i

</mi>
</msub>

<msub>
<mi>

Y

</mi>

<mi>

j

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

X_iY_j

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9694em;vertical-align:-0.2861em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0785em;">

X

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0785em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

i

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
<span className="mord,mathnormal" style="margin-right:0.2222em;">

Y

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0572em;">

j

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

 应该放在第 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

i

</mi>

<mo>

+

</mo>

<mi>

j

</mi>
</mrow>

<annotation encoding="application/x-tex">

i+j

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.7429em;vertical-align:-0.0833em;">



</span>

<span className="mord,mathnormal">

i

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
<span className="strut" style="height:0.854em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0572em;">

j

</span>
</span>
</span>
</span>

 列

二进制乘法本质上就是：<mark>

**根据乘数的每一位，决定是否加入一行被乘数，并把这一行左移对应位数。**

</mark>



如果某一位 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

Y

</mi>

<mi>

j

</mi>
</msub>

<mo>

=

</mo>

<mn>

1

</mn>
</mrow>

<annotation encoding="application/x-tex">

Y_j=1

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9694em;vertical-align:-0.2861em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.2222em;">

Y

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0572em;">

j

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
<span className="strut" style="height:0.6444em;">



</span>

<span className="mord">

1

</span>
</span>
</span>
</span>

，就加入一行左移 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

j

</mi>
</mrow>

<annotation encoding="application/x-tex">

j

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.854em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0572em;">

j

</span>
</span>
</span>
</span>

 位的 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

X

</mi>
</mrow>

<annotation encoding="application/x-tex">

X

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0785em;">

X

</span>
</span>
</span>
</span>

；如果 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

Y

</mi>

<mi>

j

</mi>
</msub>

<mo>

=

</mo>

<mn>

0

</mn>
</mrow>

<annotation encoding="application/x-tex">

Y_j=0

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9694em;vertical-align:-0.2861em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.2222em;">

Y

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0572em;">

j

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
<span className="strut" style="height:0.6444em;">



</span>

<span className="mord">

0

</span>
</span>
</span>
</span>

，这一行就是全 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mn>

0

</mn>
</mrow>

<annotation encoding="application/x-tex">

0

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
</span>
</span>
</span>



所以乘法可以看成很多行 partial product 的加法

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter12-Arithmetic-33.webp)

<mark>

实际上部分积的生成也是很简单——只需要做与运算就可以了

</mark>



### The Array Multiplier ｜ 乘法器阵列

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter12-Arithmetic-34.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter12-Arithmetic-35.webp)

#### 全加器与半加器的应用

实际上每一行的第一个都会用半加器HA，因为不需要进位；

#### Critical Path ｜ 关键路径

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter12-Arithmetic-36.webp)

对于一个<mark>

MxN

</mark>

的阵列乘法器，关键路径（上图是4*4）

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<msub>
<mi>

t

</mi>

<mrow>
<mi>

m

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
</mrow>
</msub>

<mo>

=

</mo>

<mrow>
<mo fence="true">

[

</mo>

<mo stretchy="false">

(

</mo>

<mi>

M

</mi>

<mo>

−

</mo>

<mn>

1

</mn>

<mo stretchy="false">

)

</mo>

<mo>

+

</mo>

<mo stretchy="false">

(

</mo>

<mi>

N

</mi>

<mo>

−

</mo>

<mn>

2

</mn>

<mo stretchy="false">

)

</mo>

<mo fence="true">

]

</mo>
</mrow>

<msub>
<mi>

t

</mi>

<mrow>
<mi>

c

</mi>

<mi>

a

</mi>

<mi>

r

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

+

</mo>

<mo stretchy="false">

(

</mo>

<mi>

N

</mi>

<mo>

−

</mo>

<mn>

1

</mn>

<mo stretchy="false">

)

</mo>

<msub>
<mi>

t

</mi>

<mrow>
<mi>

s

</mi>

<mi>

u

</mi>

<mi>

m

</mi>
</mrow>
</msub>

<mo>

+

</mo>

<msub>
<mi>

t

</mi>

<mrow>
<mi>

a

</mi>

<mi>

n

</mi>

<mi>

d

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

t_{mult}=\left[(M-1)+(N-2)\right]t_{carry}+(N-1)t_{sum}+t_{and}

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
<span className="mord,mathnormal,mtight">

m

</span>

<span className="mord,mathnormal,mtight">

u

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0197em;">

l

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
<span className="strut" style="height:1.0361em;vertical-align:-0.2861em;">



</span>

<span className="minner">
<span className="mopen,delimcenter" style="top:0em;">

[

</span>

<span className="mopen">

(

</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

−

</span>

<span className="mspace" style="margin-right:0.2222em;">



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

<span className="mopen">

(

</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

N

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

−

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mord">

2

</span>

<span className="mclose">

)

</span>

<span className="mclose,delimcenter" style="top:0em;">

]

</span>
</span>

<span className="mspace" style="margin-right:0.1667em;">



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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

c

</span>

<span className="mord,mathnormal,mtight">

a

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

r

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

<span className="mopen">

(

</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

N

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

<span className="mord">

1

</span>

<span className="mclose">

)

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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

s

</span>

<span className="mord,mathnormal,mtight">

u

</span>

<span className="mord,mathnormal,mtight">

m

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
<span className="mord,mathnormal,mtight">

an

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
</span>

其中：

- <span className="katex">
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

a

</mi>

<mi>

n

</mi>

<mi>

d

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

t_{and}

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
<span className="mord,mathnormal,mtight">

an

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

：生成部分积 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

X

</mi>

<mi>

i

</mi>
</msub>

<msub>
<mi>

Y

</mi>

<mi>

j

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

X_iY_j

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9694em;vertical-align:-0.2861em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0785em;">

X

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0785em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

i

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
<span className="mord,mathnormal" style="margin-right:0.2222em;">

Y

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0572em;">

j

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

 的 AND 门延迟；
- <span className="katex">
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

c

</mi>

<mi>

a

</mi>

<mi>

r

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

t_{carry}

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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

c

</span>

<span className="mord,mathnormal,mtight">

a

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

r

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

：FA / HA 的 carry 输出延迟

  - 关键路径信号进入某个 HA / FA 之后，从该输入传播到这个 HA / FA 的 carry 输出的延迟；
- <span className="katex">
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

s

</mi>

<mi>

u

</mi>

<mi>

m

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

t_{sum}

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
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

s

</span>

<span className="mord,mathnormal,mtight">

u

</span>

<span className="mord,mathnormal,mtight">

m

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

：FA / HA 的 sum 输出延迟；

  - 关键路径信号进入某个 HA / FA 之后，从该输入传播到这个 HA / FA 的 sum 输出的延迟；
- <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

M

</mi>
</mrow>

<annotation encoding="application/x-tex">

M

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
</span>
</span>
</span>

：被乘数位数；
- <span className="katex">
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

：乘数位数。

<alert type="tip">

关键路径分析

关键路径从某个 partial product 开始，先经过一个 AND 门<span className="katex">
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

a

</mi>

<mi>

n

</mi>

<mi>

d

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

t_{and}

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
<span className="mord,mathnormal,mtight">

an

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

， 然后信号在阵列里传播，信号会经过很多 FA / HA，"横向"走 是<span className="katex">
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

c

</mi>

<mi>

a

</mi>

<mi>

r

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

t_{carry}

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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

c

</span>

<span className="mord,mathnormal,mtight">

a

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

r

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

, "竖向"走是<span className="katex">
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

s

</mi>

<mi>

u

</mi>

<mi>

m

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

t_{sum}

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
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

s

</span>

<span className="mord,mathnormal,mtight">

u

</span>

<span className="mord,mathnormal,mtight">

m

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

;

其实无论走哪一条路径，都是竖向走N-1个加法器，即<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mo stretchy="false">

(

</mo>

<mi>

N

</mi>

<mo>

−

</mo>

<mn>

1

</mn>

<mo stretchy="false">

)

</mo>

<msub>
<mi>

t

</mi>

<mrow>
<mi>

s

</mi>

<mi>

u

</mi>

<mi>

m

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

(N-1)t_{sum}

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

<span className="mord,mathnormal" style="margin-right:0.109em;">

N

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

<span className="mord">

1

</span>

<span className="mclose">

)

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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

s

</span>

<span className="mord,mathnormal,mtight">

u

</span>

<span className="mord,mathnormal,mtight">

m

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

； <mark>

同时对于横向方向，都是走(M+N-1) -1 -1 = (M+N-3)个carry

</mark>

，即<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mrow>
<mo fence="true">

[

</mo>

<mo stretchy="false">

(

</mo>

<mi>

M

</mi>

<mo>

−

</mo>

<mn>

1

</mn>

<mo stretchy="false">

)

</mo>

<mo>

+

</mo>

<mo stretchy="false">

(

</mo>

<mi>

N

</mi>

<mo>

−

</mo>

<mn>

2

</mn>

<mo stretchy="false">

)

</mo>

<mo fence="true">

]

</mo>
</mrow>

<msub>
<mi>

t

</mi>

<mrow>
<mi>

c

</mi>

<mi>

a

</mi>

<mi>

r

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

\left[(M-1)+(N-2)\right]t_{carry}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.0361em;vertical-align:-0.2861em;">



</span>

<span className="minner">
<span className="mopen,delimcenter" style="top:0em;">

[

</span>

<span className="mopen">

(

</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

−

</span>

<span className="mspace" style="margin-right:0.2222em;">



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

<span className="mopen">

(

</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

N

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

−

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mord">

2

</span>

<span className="mclose">

)

</span>

<span className="mclose,delimcenter" style="top:0em;">

]

</span>
</span>

<span className="mspace" style="margin-right:0.1667em;">



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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

c

</span>

<span className="mord,mathnormal,mtight">

a

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

r

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



> 这里的解释是这样的：
> 
> 对于横向方向，总长度实际上就是M+N-1，即输出位宽是M+N-1，那么横向之间的间隔就有(输出位宽-1)=N+M-2个宽度，然后实际上我们只关系最后一位的sum结果，因此最后一个加法器它的carry时间就不计算在内了，所以再减一，结果就是<span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <mo stretchy="false">
> 
> (
> 
> </mo>
> 
> <mi>
> 
> M
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
> N
> 
> </mi>
> 
> <mo>
> 
> −
> 
> </mo>
> 
> <mn>
> 
> 3
> 
> </mn>
> 
> <mo stretchy="false">
> 
> )
> 
> </mo>
> 
> <msub>
> <mi>
> 
> t
> 
> </mi>
> 
> <mrow>
> <mi>
> 
> c
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
> r
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
> </mrow>
> </msub>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> (M + N - 3)t_{carry}
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
> <span className="mopen">
> 
> (
> 
> </span>
> 
> <span className="mord,mathnormal" style="margin-right:0.109em;">
> 
> M
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
> N
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
> −
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
> <span className="strut" style="height:1.0361em;vertical-align:-0.2861em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> 
> 3
> 
> </span>
> 
> <span className="mclose">
> 
> )
> 
> </span>
> 
> <span className="mord">
> <span className="mord,mathnormal">
> 
> t
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.1514em;">
> <span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
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
> c
> 
> </span>
> 
> <span className="mord,mathnormal,mtight">
> 
> a
> 
> </span>
> 
> <span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">
> 
> r
> 
> </span>
> 
> <span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">
> 
> r
> 
> </span>
> 
> <span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">
> 
> y
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
> </span>
> </span>
> </span>

因此最终计算得出<span className="katex">
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

m

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
</mrow>
</msub>

<mo>

=

</mo>

<mrow>
<mo fence="true">

[

</mo>

<mo stretchy="false">

(

</mo>

<mi>

M

</mi>

<mo>

−

</mo>

<mn>

1

</mn>

<mo stretchy="false">

)

</mo>

<mo>

+

</mo>

<mo stretchy="false">

(

</mo>

<mi>

N

</mi>

<mo>

−

</mo>

<mn>

2

</mn>

<mo stretchy="false">

)

</mo>

<mo fence="true">

]

</mo>
</mrow>

<msub>
<mi>

t

</mi>

<mrow>
<mi>

c

</mi>

<mi>

a

</mi>

<mi>

r

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

+

</mo>

<mo stretchy="false">

(

</mo>

<mi>

N

</mi>

<mo>

−

</mo>

<mn>

1

</mn>

<mo stretchy="false">

)

</mo>

<msub>
<mi>

t

</mi>

<mrow>
<mi>

s

</mi>

<mi>

u

</mi>

<mi>

m

</mi>
</mrow>
</msub>

<mo>

+

</mo>

<msub>
<mi>

t

</mi>

<mrow>
<mi>

a

</mi>

<mi>

n

</mi>

<mi>

d

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

t_{mult}=\left[(M-1)+(N-2)\right]t_{carry}+(N-1)t_{sum}+t_{and}

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
<span className="mord,mathnormal,mtight">

m

</span>

<span className="mord,mathnormal,mtight">

u

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0197em;">

l

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
<span className="strut" style="height:1.0361em;vertical-align:-0.2861em;">



</span>

<span className="minner">
<span className="mopen,delimcenter" style="top:0em;">

[

</span>

<span className="mopen">

(

</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

−

</span>

<span className="mspace" style="margin-right:0.2222em;">



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

<span className="mopen">

(

</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

N

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

−

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mord">

2

</span>

<span className="mclose">

)

</span>

<span className="mclose,delimcenter" style="top:0em;">

]

</span>
</span>

<span className="mspace" style="margin-right:0.1667em;">



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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

c

</span>

<span className="mord,mathnormal,mtight">

a

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

r

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

<span className="mopen">

(

</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

N

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

<span className="mord">

1

</span>

<span className="mclose">

)

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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

s

</span>

<span className="mord,mathnormal,mtight">

u

</span>

<span className="mord,mathnormal,mtight">

m

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
<span className="mord,mathnormal,mtight">

an

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
</alert>

### Carry-Save Multiplier ｜ 进位保存乘法器

普通 array multiplier 里，每一行加法器内部 carry 会横向 ripple：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

c

</mi>

<mi>

a

</mi>

<mi>

r

</mi>

<mi>

r

</mi>

<mi>

y

</mi>

<mo>

→

</mo>

<mi>

c

</mi>

<mi>

a

</mi>

<mi>

r

</mi>

<mi>

r

</mi>

<mi>

y

</mi>

<mo>

→

</mo>

<mi mathvariant="normal">

.

</mi>

<mi mathvariant="normal">

.

</mi>

<mi mathvariant="normal">

.

</mi>
</mrow>

<annotation encoding="application/x-tex">

carry→carry→...

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.625em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal">

c

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

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
<span className="strut" style="height:0.625em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal">

c

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

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
<span className="strut" style="height:0.1056em;">



</span>

<span className="mord">

...

</span>
</span>
</span>
</span>

,所以延迟里会出现很多横向 carry delay 和竖向 sum delay;

Carry-save multiplier 的核心思想是中间累加 partial products 时，不把 carry 立刻横向传播完，每个 FA 做好sum和carry的输出之后，作为一个“carry vector”的一部分保存下来，送到下一层/下一列去处理进位

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 42.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter12-Arithmetic-37.webp" />
      </p>
    </td>
    
    
      <td style="width: 57.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter12-Arithmetic-38.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

（左右对比）

#### CSA-based Array Multiplier ｜ 基于保留进位加法器的乘法器

> 这个小节是讲一种具体的实现方案，上面那个Carry-Save Multiplier是一个大类的乘法器结构
> 
> CPA指的是进位传播加法器，实际上就是前面的串行加法器的大类
> 
> ![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter12-Arithmetic-39.webp)
> 
> CSA指的是Carry-Save Adder，注意不是前面的进位选择加法器
> 
> 下图左就是CPA计算过程，每一次计算都会把进位考虑上；右就是CSA计算过程，每次先算出sum和进位 然后再把进位和sum加起来 <mark>
> 
> rnh is my
> 
> </mark>
> 
> <mark>
> 
> (scy)
> 
> </mark>
> 
>  <mark>
> 
> good son
> 
> </mark>
> 
> 
> 
> 
> 
> 
>   
> > <table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
> <tbody>
>   <tr style="border: none;">
>     <td style="width: 55.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
>       <p>
>         <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter12-Arithmetic-40.webp" />
>       </p>
>     </td>
>     
>     
>       <td style="width: 44.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
>       <p>
>         <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter12-Arithmetic-41.webp" />
>       </p>
>     </td>
>   </tr>
> </tbody>
> </table>
> 
> ![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter12-Arithmetic-42.webp)
> 
> ##### Critical Path
> 
> 关键路径这里就是 最多累加的地方 当然是x0y3 + x1y2 + x2y1 + x3y0这个累加是最长的路径
> 然后再加上CPA计算的时间，就是关键路径延迟了
> 
> > 这里假设<span className="katex">
> > <span className="katex-mathml">
> > <math xmlns="http://www.w3.org/1998/Math/MathML">
> > <semantics>
> > <mrow>
> > <msub>
> > <mi>
> > 
> > t
> > 
> > </mi>
> > 
> > <mrow>
> > <mi>
> > 
> > s
> > 
> > </mi>
> > 
> > <mi>
> > 
> > u
> > 
> > </mi>
> > 
> > <mi>
> > 
> > m
> > 
> > </mi>
> > </mrow>
> > </msub>
> > 
> > <mo>
> > 
> > >
> > </mo>
> > 
> > <msub>
> > <mi>
> > 
> > t
> > 
> > </mi>
> > 
> > <mrow>
> > <mi>
> > 
> > c
> > 
> > </mi>
> > 
> > <mi>
> > 
> > a
> > 
> > </mi>
> > 
> > <mi>
> > 
> > r
> > 
> > </mi>
> > 
> > <mi>
> > 
> > r
> > 
> > </mi>
> > 
> > <mi>
> > 
> > y
> > 
> > </mi>
> > </mrow>
> > </msub>
> > </mrow>
> > 
> > <annotation encoding="application/x-tex">
> > 
> > t_{sum}>t_{carry}
> > 
> > </annotation>
> > </semantics>
> > </math>
> > </span>
> > 
> > <span className="katex-html" ariaHidden="true">
> > <span className="base">
> > <span className="strut" style="height:0.7651em;vertical-align:-0.15em;">
> > 
> > 
> > 
> > </span>
> > 
> > <span className="mord">
> > <span className="mord,mathnormal">
> > 
> > t
> > 
> > </span>
> > 
> > <span className="msupsub">
> > <span className="vlist-t,vlist-t2">
> > <span className="vlist-r">
> > <span className="vlist" style="height:0.1514em;">
> > <span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
> > <span className="pstrut" style="height:2.7em;">
> > 
> > 
> > 
> > </span>
> > 
> > <span className="sizing,reset-size6,size3,mtight">
> > <span className="mord,mtight">
> > <span className="mord,mathnormal,mtight">
> > 
> > s
> > 
> > </span>
> > 
> > <span className="mord,mathnormal,mtight">
> > 
> > u
> > 
> > </span>
> > 
> > <span className="mord,mathnormal,mtight">
> > 
> > m
> > 
> > </span>
> > </span>
> > </span>
> > </span>
> > </span>
> > 
> > <span className="vlist-s">
> > 
> > ​
> > 
> > </span>
> > </span>
> > 
> > <span className="vlist-r">
> > <span className="vlist" style="height:0.15em;">
> > <span>
> > 
> > 
> > 
> > </span>
> > </span>
> > </span>
> > </span>
> > </span>
> > </span>
> > 
> > <span className="mspace" style="margin-right:0.2778em;">
> > 
> > 
> > 
> > </span>
> > 
> > <span className="mrel">
> > 
> > >
> > </span>
> > 
> > <span className="mspace" style="margin-right:0.2778em;">
> > 
> > 
> > 
> > </span>
> > </span>
> > 
> > <span className="base">
> > <span className="strut" style="height:0.9012em;vertical-align:-0.2861em;">
> > 
> > 
> > 
> > </span>
> > 
> > <span className="mord">
> > <span className="mord,mathnormal">
> > 
> > t
> > 
> > </span>
> > 
> > <span className="msupsub">
> > <span className="vlist-t,vlist-t2">
> > <span className="vlist-r">
> > <span className="vlist" style="height:0.1514em;">
> > <span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
> > <span className="pstrut" style="height:2.7em;">
> > 
> > 
> > 
> > </span>
> > 
> > <span className="sizing,reset-size6,size3,mtight">
> > <span className="mord,mtight">
> > <span className="mord,mathnormal,mtight">
> > 
> > c
> > 
> > </span>
> > 
> > <span className="mord,mathnormal,mtight">
> > 
> > a
> > 
> > </span>
> > 
> > <span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">
> > 
> > r
> > 
> > </span>
> > 
> > <span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">
> > 
> > r
> > 
> > </span>
> > 
> > <span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">
> > 
> > y
> > 
> > </span>
> > </span>
> > </span>
> > </span>
> > </span>
> > 
> > <span className="vlist-s">
> > 
> > ​
> > 
> > </span>
> > </span>
> > 
> > <span className="vlist-r">
> > <span className="vlist" style="height:0.2861em;">
> > <span>
> > 
> > 
> > 
> > </span>
> > </span>
> > </span>
> > </span>
> > </span>
> > </span>
> > </span>
> > </span>
> > </span>
> 
> ##### Rectangular Array
> 
> 把斜着的CSA-based Array Multiplier阵列“压扁 / 拉正”，排成一个规整的矩形，方便芯片版图实现
> 
> ![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter12-Arithmetic-43.webp)
> 
> #### Wallace-Tree Multiplier
> 
> 这个其实就是作业的那个题，对于4x4的乘法阵列，定制一个Wallace-Tree Multiplier ，如右图所示
> 
> <table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
> <tbody>
>   <tr style="border: none;">
>     <td style="width: 46.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
>       <p>
>         <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter12-Arithmetic-44.webp" />
>       </p>
>     </td>
>     
>     
>       <td style="width: 53.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
>       <p>
>         <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter12-Arithmetic-45.webp" />
>       </p>
>     </td>
>   </tr>
> </tbody>
> </table>
> 
> ##### Build From CSA-Based Multipler
> 
> 事实上Wallace-Tree Multiplier  就是一种CSA based 的阵列乘法器，因为全加器就是一种CSA加法器
> 
> ![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter12-Arithmetic-46.webp)
> 
> ##### CSA vs conventional Adder
> 
> ![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter12-Arithmetic-47.webp)
> 
> 实际上也没什么区别 只是说全加器的进位在CSA这里也是作为输出，而不是作为<mark>
> 
> 下一级全加器的输入
> 
> </mark>
> 
> 
> 
> ##### Wallace-Tree Multiplier 的优势与劣势
> 
> ![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter12-Arithmetic-48.webp)
> 
> 这张图说明了Wallace-Tree乘法器的速度为什么比普通的CSA链快，是因为普通CSA链也还是有很多的串行逻辑，但是Wallace-Tree节省了一些不必要的串行等待——能把串行CSA的O(N)复杂度压缩到O(logN)的复杂度。<mark>
> 
> 在乘法器中使用 Wallace Tree 的目的，是减少加法操作的数量，或者更准确地说，是减少 CSA 链的深度。
> 
> </mark>
> 
> 
> 
> 但是也有缺点，缺点是连线更复杂，但是也也可以构造 <mark>
> 
> Booth 编码的 Wallace Tree 乘法器。
> 
> </mark>
> 
> 
> 
> <table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
> <tbody>
>   <tr style="border: none;">
>     <td style="width: 55.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
>       <p>
>         <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter12-Arithmetic-49.webp" />
>       </p>
>     </td>
>     
>     
>       <td style="width: 44.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
>       <p>
>         <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter12-Arithmetic-50.webp" />
>       </p>
>     </td>
>   </tr>
> </tbody>
> </table>
> 
> ## Shifter ｜ 移位器
> 
> 移位器 shifter 的几种硬件实现方式
> 
> ### The Binary Shifter
> 
> ![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter12-Arithmetic-51.webp)
> 
> 有三个控制信号：
> 
> - **Right**：右移 1 位
> - **nop**：no operation，不移位
> - **Left**：左移 1 位
> 
> 可以把它理解成一个由传输门/传输晶体管组成的 **3 选 1 mux**。
> 
> #### A programmable Binary Shifter
> 
> 表中 <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <mi>
> 
> r
> 
> </mi>
> 
> <mi>
> 
> g
> 
> </mi>
> 
> <mi>
> 
> t
> 
> </mi>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> rgt
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:0.8095em;vertical-align:-0.1944em;">
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
> <span className="mord,mathnormal" style="margin-right:0.0359em;">
> 
> g
> 
> </span>
> 
> <span className="mord,mathnormal">
> 
> t
> 
> </span>
> </span>
> </span>
> </span>
> 
> 、<span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <mi>
> 
> n
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
> p
> 
> </mi>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> nop
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:0.625em;vertical-align:-0.1944em;">
> 
> 
> 
> </span>
> 
> <span className="mord,mathnormal">
> 
> n
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
> p
> 
> </span>
> </span>
> </span>
> </span>
> 
> 、<span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <mi>
> 
> l
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
> f
> 
> </mi>
> 
> <mi>
> 
> t
> 
> </mi>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> left
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">
> 
> 
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
> e
> 
> </span>
> 
> <span className="mord,mathnormal" style="margin-right:0.1076em;">
> 
> f
> 
> </span>
> 
> <span className="mord,mathnormal">
> 
> t
> 
> </span>
> </span>
> </span>
> </span>
> 
>  是控制信号，通常是 one-hot，也就是三者只能有一个为 1。
> 
> ![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter12-Arithmetic-52.webp)
> 
> 注意这里**右移的时候高位补0**
> 
> ### The Barrel Shifter
> 
> Barrel shifter 的思想是：<mark>
> 
> 每个输出
> 
> </mark>
> 
>  <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msub>
> <mi>
> 
> B
> 
> </mi>
> 
> <mi>
> 
> j
> 
> </mi>
> </msub>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> B_j
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
> <span className="mord,mathnormal" style="margin-right:0.0502em;">
> 
> B
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3117em;">
> <span style="top:-2.55em;margin-left:-0.0502em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mathnormal,mtight" style="margin-right:0.0572em;">
> 
> j
> 
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
> </span>
> </span>
> </span>
> 
>  <mark>
> 
> 都可以从多个输入
> 
> </mark>
> 
>  <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msub>
> <mi>
> 
> A
> 
> </mi>
> 
> <mi>
> 
> k
> 
> </mi>
> </msub>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> A_k
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:0.8333em;vertical-align:-0.15em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> <span className="mord,mathnormal">
> 
> A
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3361em;">
> <span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mathnormal,mtight" style="margin-right:0.0315em;">
> 
> k
> 
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
> <span className="vlist" style="height:0.15em;">
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
> </span>
> 
>  <mark>
> 
> 中直接选择一个
> 
> </mark>
> 
> 。（任意移动多少个位置，算术移动）
> 
> <table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
> <tbody>
>   <tr style="border: none;">
>     <td style="width: 47.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
>       <p>
>         <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter12-Arithmetic-53.webp" />
>       </p>
>     </td>
>     
>     
>       <td style="width: 52.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
>       <p>
>         <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter12-Arithmetic-54.webp" />
>       </p>
>     </td>
>   </tr>
> </tbody>
> </table>
> 
> 本质上是一个很大的交叉开关阵列。
> 
> 例如 4-bit barrel shifter 中，每个输出都可能从 <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msub>
> <mi>
> 
> A
> 
> </mi>
> 
> <mn>
> 
> 3
> 
> </mn>
> </msub>
> 
> <mo separator="true">
> 
> ,
> 
> </mo>
> 
> <msub>
> <mi>
> 
> A
> 
> </mi>
> 
> <mn>
> 
> 2
> 
> </mn>
> </msub>
> 
> <mo separator="true">
> 
> ,
> 
> </mo>
> 
> <msub>
> <mi>
> 
> A
> 
> </mi>
> 
> <mn>
> 
> 1
> 
> </mn>
> </msub>
> 
> <mo separator="true">
> 
> ,
> 
> </mo>
> 
> <msub>
> <mi>
> 
> A
> 
> </mi>
> 
> <mn>
> 
> 0
> 
> </mn>
> </msub>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> A_3,A_2,A_1,A_0
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:0.8778em;vertical-align:-0.1944em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> <span className="mord,mathnormal">
> 
> A
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3011em;">
> <span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mtight">
> 
> 3
> 
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
> <span className="vlist" style="height:0.15em;">
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
> <span className="mord">
> <span className="mord,mathnormal">
> 
> A
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3011em;">
> <span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
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
> 
> <span className="vlist-s">
> 
> ​
> 
> </span>
> </span>
> 
> <span className="vlist-r">
> <span className="vlist" style="height:0.15em;">
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
> <span className="mord">
> <span className="mord,mathnormal">
> 
> A
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3011em;">
> <span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mtight">
> 
> 1
> 
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
> <span className="vlist" style="height:0.15em;">
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
> <span className="mord">
> <span className="mord,mathnormal">
> 
> A
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3011em;">
> <span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mtight">
> 
> 0
> 
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
> <span className="vlist" style="height:0.15em;">
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
> </span>
> 
>  中选择，因此会有很多横向数据线、纵向控制线、交叉点开关。
> 
> 这个结构的面积主要不是被晶体管占掉的，而是被大量连线占掉的。对于 <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <mi>
> 
> N
> 
> </mi>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> N
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
> <span className="mord,mathnormal" style="margin-right:0.109em;">
> 
> N
> 
> </span>
> </span>
> </span>
> </span>
> 
>  位 barrel shifter，交叉连接规模大约是 <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <mi>
> 
> O
> 
> </mi>
> 
> <mo stretchy="false">
> 
> (
> 
> </mo>
> 
> <msup>
> <mi>
> 
> N
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
> <mo stretchy="false">
> 
> )
> 
> </mo>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> O(N^2)
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:1.0641em;vertical-align:-0.25em;">
> 
> 
> 
> </span>
> 
> <span className="mord,mathnormal" style="margin-right:0.0278em;">
> 
> O
> 
> </span>
> 
> <span className="mopen">
> 
> (
> 
> </span>
> 
> <span className="mord">
> <span className="mord,mathnormal" style="margin-right:0.109em;">
> 
> N
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
> <span className="mclose">
> 
> )
> 
> </span>
> </span>
> </span>
> </span>
> 
> ，所以位宽变大以后，布线压力很明显。
> 
> ### Logarithmic Shifter
> 
> 用多级小移位实现任意移位，不再用一个巨大的全交叉阵列，而是分成若干级，每一级只负责移 <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <mn>
> 
> 1
> 
> </mn>
> 
> <mo separator="true">
> 
> ,
> 
> </mo>
> 
> <mn>
> 
> 2
> 
> </mn>
> 
> <mo separator="true">
> 
> ,
> 
> </mo>
> 
> <mn>
> 
> 4
> 
> </mn>
> 
> <mo separator="true">
> 
> ,
> 
> </mo>
> 
> <mn>
> 
> 8
> 
> </mn>
> 
> <mo separator="true">
> 
> ,
> 
> </mo>
> 
> <mo>
> 
> …
> 
> </mo>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> 1,2,4,8,\dots
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
> 1
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
> <span className="mord">
> 
> 2
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
> <span className="mord">
> 
> 4
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
> <span className="mord">
> 
> 8
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
> <span className="minner">
> 
> …
> 
> </span>
> </span>
> </span>
> </span>
> 
>  位。
> 
> <table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
> <tbody>
>   <tr style="border: none;">
>     <td style="width: 48.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
>       <p>
>         <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter12-Arithmetic-55.webp" />
>       </p>
>     </td>
>     
>     
>       <td style="width: 51.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
>       <p>
>         <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter12-Arithmetic-56.webp" />
>       </p>
>     </td>
>   </tr>
> </tbody>
> </table>
> 
> ## ALU ｜ Arithmetic Logic Unit 运算器
> 
> ALU 需要根据 **opcode** 执行不同功能，比如：<span className="katex">
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
> <mo>
> 
> +
> 
> </mo>
> 
> <mi>
> 
> B
> 
> </mi>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> A+B
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">
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
> <span className="strut" style="height:0.6833em;">
> 
> 
> 
> </span>
> 
> <span className="mord,mathnormal" style="margin-right:0.0502em;">
> 
> B
> 
> </span>
> </span>
> </span>
> </span>
> 
> 、<span className="katex">
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
> <mo>
> 
> +
> 
> </mo>
> 
> <mi>
> 
> B
> 
> </mi>
> 
> <mo>
> 
> +
> 
> </mo>
> 
> <mn>
> 
> 1
> 
> </mn>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> A+B+1
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">
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
> <span className="mord,mathnormal" style="margin-right:0.0502em;">
> 
> B
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
> 、<span className="katex">
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
> <mo>
> 
> −
> 
> </mo>
> 
> <mi>
> 
> B
> 
> </mi>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> A-B
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">
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
> <span className="mspace" style="margin-right:0.2222em;">
> 
> 
> 
> </span>
> 
> <span className="mbin">
> 
> −
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
> <span className="strut" style="height:0.6833em;">
> 
> 
> 
> </span>
> 
> <span className="mord,mathnormal" style="margin-right:0.0502em;">
> 
> B
> 
> </span>
> </span>
> </span>
> </span>
> 
> 、<span className="katex">
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
> <mi mathvariant="normal">
> 
> &
> 
> </mi>
> 
> <mi>
> 
> B
> 
> </mi>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> A\&B
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
> <span className="mord,mathnormal">
> 
> A
> 
> </span>
> 
> <span className="mord">
> 
> &
> 
> </span>
> 
> <span className="mord,mathnormal" style="margin-right:0.0502em;">
> 
> B
> 
> </span>
> </span>
> </span>
> </span>
> 
> 、<span className="katex">
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
> <mi mathvariant="normal">
> 
> ∣
> 
> </mi>
> 
> <mi>
> 
> B
> 
> </mi>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> A|B
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
> <span className="mord,mathnormal">
> 
> A
> 
> </span>
> 
> <span className="mord">
> 
> ∣
> 
> </span>
> 
> <span className="mord,mathnormal" style="margin-right:0.0502em;">
> 
> B
> 
> </span>
> </span>
> </span>
> </span>
> 
> 、<span className="katex">
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
> <mo>
> 
> ⊕
> 
> </mo>
> 
> <mi>
> 
> B
> 
> </mi>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> A\oplus B
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">
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
> <span className="mspace" style="margin-right:0.2222em;">
> 
> 
> 
> </span>
> 
> <span className="mbin">
> 
> ⊕
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
> <span className="strut" style="height:0.6833em;">
> 
> 
> 
> </span>
> 
> <span className="mord,mathnormal" style="margin-right:0.0502em;">
> 
> B
> 
> </span>
> </span>
> </span>
> </span>
> 
> 
> 
> 其中 **opcode** 决定当前做什么操作，**carry-in** 也会参与决定具体算术功能
> 
> ![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter12-Arithmetic-57.webp)
> 
> ### Function blocks and ALUs
> 
> ALU
> 
> - 可以提供两个变量的**完整逻辑函数集合**，也可以只提供其中一个子集。
> - ALU 通常围绕加法器构建，因为加法是典型的算术运算，而且**进位链 carry chain** 往往决定整体延迟。
> - Function block 可以用来计算全功能 ALU 所需的中间信号。
> - 所需面积较小。
> - 可以使用传输门实现，但传输门可能会引入额外延迟。
> 
> ![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter12-Arithmetic-58.webp)
> 
> <span className="katex-display">
> <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
> <semantics>
> <mrow>
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
> t
> 
> </mi>
> 
> <mi>
> 
> p
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
> <mo>
> 
> =
> 
> </mo>
> 
> <mover accent="true">
> <mi>
> 
> a
> 
> </mi>
> 
> <mo stretchy="true">
> 
> ‾
> 
> </mo>
> </mover>
> 
> <mover accent="true">
> <mi>
> 
> b
> 
> </mi>
> 
> <mo stretchy="true">
> 
> ‾
> 
> </mo>
> </mover>
> 
> <mi>
> 
> o
> 
> </mi>
> 
> <msub>
> <mi>
> 
> p
> 
> </mi>
> 
> <mn>
> 
> 0
> 
> </mn>
> </msub>
> 
> <mo>
> 
> +
> 
> </mo>
> 
> <mi>
> 
> a
> 
> </mi>
> 
> <mover accent="true">
> <mi>
> 
> b
> 
> </mi>
> 
> <mo stretchy="true">
> 
> ‾
> 
> </mo>
> </mover>
> 
> <mi>
> 
> o
> 
> </mi>
> 
> <msub>
> <mi>
> 
> p
> 
> </mi>
> 
> <mn>
> 
> 1
> 
> </mn>
> </msub>
> 
> <mo>
> 
> +
> 
> </mo>
> 
> <mover accent="true">
> <mi>
> 
> a
> 
> </mi>
> 
> <mo stretchy="true">
> 
> ‾
> 
> </mo>
> </mover>
> 
> <mi>
> 
> b
> 
> </mi>
> 
> <mi>
> 
> o
> 
> </mi>
> 
> <msub>
> <mi>
> 
> p
> 
> </mi>
> 
> <mn>
> 
> 2
> 
> </mn>
> </msub>
> 
> <mo>
> 
> +
> 
> </mo>
> 
> <mi>
> 
> a
> 
> </mi>
> 
> <mi>
> 
> b
> 
> </mi>
> 
> <mi>
> 
> o
> 
> </mi>
> 
> <msub>
> <mi>
> 
> p
> 
> </mi>
> 
> <mn>
> 
> 3
> 
> </mn>
> </msub>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> output=\overline{a}\overline{b}op_0+a\overline{b}op_1+\overline{a}bop_2+abop_3
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:0.8095em;vertical-align:-0.1944em;">
> 
> 
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
> u
> 
> </span>
> 
> <span className="mord,mathnormal">
> 
> tp
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
> <span className="strut" style="height:1.0889em;vertical-align:-0.1944em;">
> 
> 
> 
> </span>
> 
> <span className="mord,overline">
> <span className="vlist-t">
> <span className="vlist-r">
> <span className="vlist" style="height:0.6306em;">
> <span style="top:-3em;">
> <span className="pstrut" style="height:3em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> <span className="mord,mathnormal">
> 
> a
> 
> </span>
> </span>
> </span>
> 
> <span style="top:-3.5506em;">
> <span className="pstrut" style="height:3em;">
> 
> 
> 
> </span>
> 
> <span className="overline-line" style="border-bottom-width:0.04em;">
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
> <span className="mord,overline">
> <span className="vlist-t">
> <span className="vlist-r">
> <span className="vlist" style="height:0.8944em;">
> <span style="top:-3em;">
> <span className="pstrut" style="height:3em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> <span className="mord,mathnormal">
> 
> b
> 
> </span>
> </span>
> </span>
> 
> <span style="top:-3.8144em;">
> <span className="pstrut" style="height:3em;">
> 
> 
> 
> </span>
> 
> <span className="overline-line" style="border-bottom-width:0.04em;">
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
> <span className="mord,mathnormal">
> 
> o
> 
> </span>
> 
> <span className="mord">
> <span className="mord,mathnormal">
> 
> p
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3011em;">
> <span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mtight">
> 
> 0
> 
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
> <span className="vlist" style="height:0.15em;">
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
> <span className="strut" style="height:1.0889em;vertical-align:-0.1944em;">
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
> <span className="mord,overline">
> <span className="vlist-t">
> <span className="vlist-r">
> <span className="vlist" style="height:0.8944em;">
> <span style="top:-3em;">
> <span className="pstrut" style="height:3em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> <span className="mord,mathnormal">
> 
> b
> 
> </span>
> </span>
> </span>
> 
> <span style="top:-3.8144em;">
> <span className="pstrut" style="height:3em;">
> 
> 
> 
> </span>
> 
> <span className="overline-line" style="border-bottom-width:0.04em;">
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
> <span className="mord,mathnormal">
> 
> o
> 
> </span>
> 
> <span className="mord">
> <span className="mord,mathnormal">
> 
> p
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3011em;">
> <span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mtight">
> 
> 1
> 
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
> <span className="vlist" style="height:0.15em;">
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
> <span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">
> 
> 
> 
> </span>
> 
> <span className="mord,overline">
> <span className="vlist-t">
> <span className="vlist-r">
> <span className="vlist" style="height:0.6306em;">
> <span style="top:-3em;">
> <span className="pstrut" style="height:3em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> <span className="mord,mathnormal">
> 
> a
> 
> </span>
> </span>
> </span>
> 
> <span style="top:-3.5506em;">
> <span className="pstrut" style="height:3em;">
> 
> 
> 
> </span>
> 
> <span className="overline-line" style="border-bottom-width:0.04em;">
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
> <span className="mord,mathnormal">
> 
> b
> 
> </span>
> 
> <span className="mord,mathnormal">
> 
> o
> 
> </span>
> 
> <span className="mord">
> <span className="mord,mathnormal">
> 
> p
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3011em;">
> <span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
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
> 
> <span className="vlist-s">
> 
> ​
> 
> </span>
> </span>
> 
> <span className="vlist-r">
> <span className="vlist" style="height:0.15em;">
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
> <span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">
> 
> 
> 
> </span>
> 
> <span className="mord,mathnormal">
> 
> ab
> 
> </span>
> 
> <span className="mord,mathnormal">
> 
> o
> 
> </span>
> 
> <span className="mord">
> <span className="mord,mathnormal">
> 
> p
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3011em;">
> <span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mtight">
> 
> 3
> 
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
> <span className="vlist" style="height:0.15em;">
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
> </span>
> </span>
> 
> 这个公式的意思是：<span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <mi>
> 
> o
> 
> </mi>
> 
> <msub>
> <mi>
> 
> p
> 
> </mi>
> 
> <mn>
> 
> 0
> 
> </mn>
> </msub>
> 
> <mo separator="true">
> 
> ,
> 
> </mo>
> 
> <mi>
> 
> o
> 
> </mi>
> 
> <msub>
> <mi>
> 
> p
> 
> </mi>
> 
> <mn>
> 
> 1
> 
> </mn>
> </msub>
> 
> <mo separator="true">
> 
> ,
> 
> </mo>
> 
> <mi>
> 
> o
> 
> </mi>
> 
> <msub>
> <mi>
> 
> p
> 
> </mi>
> 
> <mn>
> 
> 2
> 
> </mn>
> </msub>
> 
> <mo separator="true">
> 
> ,
> 
> </mo>
> 
> <mi>
> 
> o
> 
> </mi>
> 
> <msub>
> <mi>
> 
> p
> 
> </mi>
> 
> <mn>
> 
> 3
> 
> </mn>
> </msub>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> op_0,op_1,op_2,op_3
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:0.625em;vertical-align:-0.1944em;">
> 
> 
> 
> </span>
> 
> <span className="mord,mathnormal">
> 
> o
> 
> </span>
> 
> <span className="mord">
> <span className="mord,mathnormal">
> 
> p
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3011em;">
> <span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mtight">
> 
> 0
> 
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
> <span className="vlist" style="height:0.15em;">
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
> <span className="mord,mathnormal">
> 
> o
> 
> </span>
> 
> <span className="mord">
> <span className="mord,mathnormal">
> 
> p
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3011em;">
> <span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mtight">
> 
> 1
> 
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
> <span className="vlist" style="height:0.15em;">
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
> <span className="mord,mathnormal">
> 
> o
> 
> </span>
> 
> <span className="mord">
> <span className="mord,mathnormal">
> 
> p
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3011em;">
> <span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
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
> 
> <span className="vlist-s">
> 
> ​
> 
> </span>
> </span>
> 
> <span className="vlist-r">
> <span className="vlist" style="height:0.15em;">
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
> <span className="mord,mathnormal">
> 
> o
> 
> </span>
> 
> <span className="mord">
> <span className="mord,mathnormal">
> 
> p
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3011em;">
> <span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mtight">
> 
> 3
> 
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
> <span className="vlist" style="height:0.15em;">
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
> </span>
> 
>  分别对应 <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <mi>
> 
> a
> 
> </mi>
> 
> <mo separator="true">
> 
> ,
> 
> </mo>
> 
> <mi>
> 
> b
> 
> </mi>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> a,b
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">
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
> <span className="mord,mathnormal">
> 
> b
> 
> </span>
> </span>
> </span>
> </span>
> 
>  的四种输入情况。
> 
> <table>
> <thead>
>   <tr>
>     <th>
>       输入
>     </th>
>     
>     <th>
>       输出由谁决定
>     </th>
>   </tr>
> </thead>
> 
> <tbody>
>   <tr>
>     <td>
>       <span className="katex">
>         <span className="katex-mathml">
>           <math xmlns="http://www.w3.org/1998/Math/MathML">
>             <semantics>
>               <mrow>
>                 <mi>
>                   a
>                 </mi>
>                 
>                 <mo>
>                   =
>                 </mo>
>                 
>                 <mn>
>                   0
>                 </mn>
>                 
>                 <mo separator="true">
>                   ,
>                 </mo>
>                 
>                 <mi>
>                   b
>                 </mi>
>                 
>                 <mo>
>                   =
>                 </mo>
>                 
>                 <mn>
>                   0
>                 </mn>
>               </mrow>
>               
>               <annotation encoding="application/x-tex">
>                 a=0,b=0
>               </annotation>
>             </semantics>
>           </math>
>         </span>
>         
>         <span className="katex-html" ariaHidden="true">
>           <span className="base">
>             <span className="strut" style="height:0.4306em;">
>               
>             </span>
>             
>             <span className="mord,mathnormal">
>               a
>             </span>
>             
>             <span className="mspace" style="margin-right:0.2778em;">
>               
>             </span>
>             
>             <span className="mrel">
>               =
>             </span>
>             
>             <span className="mspace" style="margin-right:0.2778em;">
>               
>             </span>
>           </span>
>           
>           <span className="base">
>             <span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">
>               
>             </span>
>             
>             <span className="mord">
>               0
>             </span>
>             
>             <span className="mpunct">
>               ,
>             </span>
>             
>             <span className="mspace" style="margin-right:0.1667em;">
>               
>             </span>
>             
>             <span className="mord,mathnormal">
>               b
>             </span>
>             
>             <span className="mspace" style="margin-right:0.2778em;">
>               
>             </span>
>             
>             <span className="mrel">
>               =
>             </span>
>             
>             <span className="mspace" style="margin-right:0.2778em;">
>               
>             </span>
>           </span>
>           
>           <span className="base">
>             <span className="strut" style="height:0.6444em;">
>               
>             </span>
>             
>             <span className="mord">
>               0
>             </span>
>           </span>
>         </span>
>       </span>
>     </td>
>     
>     <td>
>       <span className="katex">
>         <span className="katex-mathml">
>           <math xmlns="http://www.w3.org/1998/Math/MathML">
>             <semantics>
>               <mrow>
>                 <mi>
>                   o
>                 </mi>
>                 
>                 <msub>
>                   <mi>
>                     p
>                   </mi>
>                   
>                   <mn>
>                     0
>                   </mn>
>                 </msub>
>               </mrow>
>               
>               <annotation encoding="application/x-tex">
>                 op_0
>               </annotation>
>             </semantics>
>           </math>
>         </span>
>         
>         <span className="katex-html" ariaHidden="true">
>           <span className="base">
>             <span className="strut" style="height:0.625em;vertical-align:-0.1944em;">
>               
>             </span>
>             
>             <span className="mord,mathnormal">
>               o
>             </span>
>             
>             <span className="mord">
>               <span className="mord,mathnormal">
>                 p
>               </span>
>               
>               <span className="msupsub">
>                 <span className="vlist-t,vlist-t2">
>                   <span className="vlist-r">
>                     <span className="vlist" style="height:0.3011em;">
>                       <span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
>                         <span className="pstrut" style="height:2.7em;">
>                           
>                         </span>
>                         
>                         <span className="sizing,reset-size6,size3,mtight">
>                           <span className="mord,mtight">
>                             0
>                           </span>
>                         </span>
>                       </span>
>                     </span>
>                     
>                     <span className="vlist-s">
>                       ​
>                     </span>
>                   </span>
>                   
>                   <span className="vlist-r">
>                     <span className="vlist" style="height:0.15em;">
>                       <span>
>                         
>                       </span>
>                     </span>
>                   </span>
>                 </span>
>               </span>
>             </span>
>           </span>
>         </span>
>       </span>
>     </td>
>   </tr>
>   
>   <tr>
>     <td>
>       <span className="katex">
>         <span className="katex-mathml">
>           <math xmlns="http://www.w3.org/1998/Math/MathML">
>             <semantics>
>               <mrow>
>                 <mi>
>                   a
>                 </mi>
>                 
>                 <mo>
>                   =
>                 </mo>
>                 
>                 <mn>
>                   1
>                 </mn>
>                 
>                 <mo separator="true">
>                   ,
>                 </mo>
>                 
>                 <mi>
>                   b
>                 </mi>
>                 
>                 <mo>
>                   =
>                 </mo>
>                 
>                 <mn>
>                   0
>                 </mn>
>               </mrow>
>               
>               <annotation encoding="application/x-tex">
>                 a=1,b=0
>               </annotation>
>             </semantics>
>           </math>
>         </span>
>         
>         <span className="katex-html" ariaHidden="true">
>           <span className="base">
>             <span className="strut" style="height:0.4306em;">
>               
>             </span>
>             
>             <span className="mord,mathnormal">
>               a
>             </span>
>             
>             <span className="mspace" style="margin-right:0.2778em;">
>               
>             </span>
>             
>             <span className="mrel">
>               =
>             </span>
>             
>             <span className="mspace" style="margin-right:0.2778em;">
>               
>             </span>
>           </span>
>           
>           <span className="base">
>             <span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">
>               
>             </span>
>             
>             <span className="mord">
>               1
>             </span>
>             
>             <span className="mpunct">
>               ,
>             </span>
>             
>             <span className="mspace" style="margin-right:0.1667em;">
>               
>             </span>
>             
>             <span className="mord,mathnormal">
>               b
>             </span>
>             
>             <span className="mspace" style="margin-right:0.2778em;">
>               
>             </span>
>             
>             <span className="mrel">
>               =
>             </span>
>             
>             <span className="mspace" style="margin-right:0.2778em;">
>               
>             </span>
>           </span>
>           
>           <span className="base">
>             <span className="strut" style="height:0.6444em;">
>               
>             </span>
>             
>             <span className="mord">
>               0
>             </span>
>           </span>
>         </span>
>       </span>
>     </td>
>     
>     <td>
>       <span className="katex">
>         <span className="katex-mathml">
>           <math xmlns="http://www.w3.org/1998/Math/MathML">
>             <semantics>
>               <mrow>
>                 <mi>
>                   o
>                 </mi>
>                 
>                 <msub>
>                   <mi>
>                     p
>                   </mi>
>                   
>                   <mn>
>                     1
>                   </mn>
>                 </msub>
>               </mrow>
>               
>               <annotation encoding="application/x-tex">
>                 op_1
>               </annotation>
>             </semantics>
>           </math>
>         </span>
>         
>         <span className="katex-html" ariaHidden="true">
>           <span className="base">
>             <span className="strut" style="height:0.625em;vertical-align:-0.1944em;">
>               
>             </span>
>             
>             <span className="mord,mathnormal">
>               o
>             </span>
>             
>             <span className="mord">
>               <span className="mord,mathnormal">
>                 p
>               </span>
>               
>               <span className="msupsub">
>                 <span className="vlist-t,vlist-t2">
>                   <span className="vlist-r">
>                     <span className="vlist" style="height:0.3011em;">
>                       <span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
>                         <span className="pstrut" style="height:2.7em;">
>                           
>                         </span>
>                         
>                         <span className="sizing,reset-size6,size3,mtight">
>                           <span className="mord,mtight">
>                             1
>                           </span>
>                         </span>
>                       </span>
>                     </span>
>                     
>                     <span className="vlist-s">
>                       ​
>                     </span>
>                   </span>
>                   
>                   <span className="vlist-r">
>                     <span className="vlist" style="height:0.15em;">
>                       <span>
>                         
>                       </span>
>                     </span>
>                   </span>
>                 </span>
>               </span>
>             </span>
>           </span>
>         </span>
>       </span>
>     </td>
>   </tr>
>   
>   <tr>
>     <td>
>       <span className="katex">
>         <span className="katex-mathml">
>           <math xmlns="http://www.w3.org/1998/Math/MathML">
>             <semantics>
>               <mrow>
>                 <mi>
>                   a
>                 </mi>
>                 
>                 <mo>
>                   =
>                 </mo>
>                 
>                 <mn>
>                   0
>                 </mn>
>                 
>                 <mo separator="true">
>                   ,
>                 </mo>
>                 
>                 <mi>
>                   b
>                 </mi>
>                 
>                 <mo>
>                   =
>                 </mo>
>                 
>                 <mn>
>                   1
>                 </mn>
>               </mrow>
>               
>               <annotation encoding="application/x-tex">
>                 a=0,b=1
>               </annotation>
>             </semantics>
>           </math>
>         </span>
>         
>         <span className="katex-html" ariaHidden="true">
>           <span className="base">
>             <span className="strut" style="height:0.4306em;">
>               
>             </span>
>             
>             <span className="mord,mathnormal">
>               a
>             </span>
>             
>             <span className="mspace" style="margin-right:0.2778em;">
>               
>             </span>
>             
>             <span className="mrel">
>               =
>             </span>
>             
>             <span className="mspace" style="margin-right:0.2778em;">
>               
>             </span>
>           </span>
>           
>           <span className="base">
>             <span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">
>               
>             </span>
>             
>             <span className="mord">
>               0
>             </span>
>             
>             <span className="mpunct">
>               ,
>             </span>
>             
>             <span className="mspace" style="margin-right:0.1667em;">
>               
>             </span>
>             
>             <span className="mord,mathnormal">
>               b
>             </span>
>             
>             <span className="mspace" style="margin-right:0.2778em;">
>               
>             </span>
>             
>             <span className="mrel">
>               =
>             </span>
>             
>             <span className="mspace" style="margin-right:0.2778em;">
>               
>             </span>
>           </span>
>           
>           <span className="base">
>             <span className="strut" style="height:0.6444em;">
>               
>             </span>
>             
>             <span className="mord">
>               1
>             </span>
>           </span>
>         </span>
>       </span>
>     </td>
>     
>     <td>
>       <span className="katex">
>         <span className="katex-mathml">
>           <math xmlns="http://www.w3.org/1998/Math/MathML">
>             <semantics>
>               <mrow>
>                 <mi>
>                   o
>                 </mi>
>                 
>                 <msub>
>                   <mi>
>                     p
>                   </mi>
>                   
>                   <mn>
>                     2
>                   </mn>
>                 </msub>
>               </mrow>
>               
>               <annotation encoding="application/x-tex">
>                 op_2
>               </annotation>
>             </semantics>
>           </math>
>         </span>
>         
>         <span className="katex-html" ariaHidden="true">
>           <span className="base">
>             <span className="strut" style="height:0.625em;vertical-align:-0.1944em;">
>               
>             </span>
>             
>             <span className="mord,mathnormal">
>               o
>             </span>
>             
>             <span className="mord">
>               <span className="mord,mathnormal">
>                 p
>               </span>
>               
>               <span className="msupsub">
>                 <span className="vlist-t,vlist-t2">
>                   <span className="vlist-r">
>                     <span className="vlist" style="height:0.3011em;">
>                       <span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
>                         <span className="pstrut" style="height:2.7em;">
>                           
>                         </span>
>                         
>                         <span className="sizing,reset-size6,size3,mtight">
>                           <span className="mord,mtight">
>                             2
>                           </span>
>                         </span>
>                       </span>
>                     </span>
>                     
>                     <span className="vlist-s">
>                       ​
>                     </span>
>                   </span>
>                   
>                   <span className="vlist-r">
>                     <span className="vlist" style="height:0.15em;">
>                       <span>
>                         
>                       </span>
>                     </span>
>                   </span>
>                 </span>
>               </span>
>             </span>
>           </span>
>         </span>
>       </span>
>     </td>
>   </tr>
>   
>   <tr>
>     <td>
>       <span className="katex">
>         <span className="katex-mathml">
>           <math xmlns="http://www.w3.org/1998/Math/MathML">
>             <semantics>
>               <mrow>
>                 <mi>
>                   a
>                 </mi>
>                 
>                 <mo>
>                   =
>                 </mo>
>                 
>                 <mn>
>                   1
>                 </mn>
>                 
>                 <mo separator="true">
>                   ,
>                 </mo>
>                 
>                 <mi>
>                   b
>                 </mi>
>                 
>                 <mo>
>                   =
>                 </mo>
>                 
>                 <mn>
>                   1
>                 </mn>
>               </mrow>
>               
>               <annotation encoding="application/x-tex">
>                 a=1,b=1
>               </annotation>
>             </semantics>
>           </math>
>         </span>
>         
>         <span className="katex-html" ariaHidden="true">
>           <span className="base">
>             <span className="strut" style="height:0.4306em;">
>               
>             </span>
>             
>             <span className="mord,mathnormal">
>               a
>             </span>
>             
>             <span className="mspace" style="margin-right:0.2778em;">
>               
>             </span>
>             
>             <span className="mrel">
>               =
>             </span>
>             
>             <span className="mspace" style="margin-right:0.2778em;">
>               
>             </span>
>           </span>
>           
>           <span className="base">
>             <span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">
>               
>             </span>
>             
>             <span className="mord">
>               1
>             </span>
>             
>             <span className="mpunct">
>               ,
>             </span>
>             
>             <span className="mspace" style="margin-right:0.1667em;">
>               
>             </span>
>             
>             <span className="mord,mathnormal">
>               b
>             </span>
>             
>             <span className="mspace" style="margin-right:0.2778em;">
>               
>             </span>
>             
>             <span className="mrel">
>               =
>             </span>
>             
>             <span className="mspace" style="margin-right:0.2778em;">
>               
>             </span>
>           </span>
>           
>           <span className="base">
>             <span className="strut" style="height:0.6444em;">
>               
>             </span>
>             
>             <span className="mord">
>               1
>             </span>
>           </span>
>         </span>
>       </span>
>     </td>
>     
>     <td>
>       <span className="katex">
>         <span className="katex-mathml">
>           <math xmlns="http://www.w3.org/1998/Math/MathML">
>             <semantics>
>               <mrow>
>                 <mi>
>                   o
>                 </mi>
>                 
>                 <msub>
>                   <mi>
>                     p
>                   </mi>
>                   
>                   <mn>
>                     3
>                   </mn>
>                 </msub>
>               </mrow>
>               
>               <annotation encoding="application/x-tex">
>                 op_3
>               </annotation>
>             </semantics>
>           </math>
>         </span>
>         
>         <span className="katex-html" ariaHidden="true">
>           <span className="base">
>             <span className="strut" style="height:0.625em;vertical-align:-0.1944em;">
>               
>             </span>
>             
>             <span className="mord,mathnormal">
>               o
>             </span>
>             
>             <span className="mord">
>               <span className="mord,mathnormal">
>                 p
>               </span>
>               
>               <span className="msupsub">
>                 <span className="vlist-t,vlist-t2">
>                   <span className="vlist-r">
>                     <span className="vlist" style="height:0.3011em;">
>                       <span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
>                         <span className="pstrut" style="height:2.7em;">
>                           
>                         </span>
>                         
>                         <span className="sizing,reset-size6,size3,mtight">
>                           <span className="mord,mtight">
>                             3
>                           </span>
>                         </span>
>                       </span>
>                     </span>
>                     
>                     <span className="vlist-s">
>                       ​
>                     </span>
>                   </span>
>                   
>                   <span className="vlist-r">
>                     <span className="vlist" style="height:0.15em;">
>                       <span>
>                         
>                       </span>
>                     </span>
>                   </span>
>                 </span>
>               </span>
>             </span>
>           </span>
>         </span>
>       </span>
>     </td>
>   </tr>
> </tbody>
> </table>
> 
> 用 opcode 控制 function block，就可以灵活生成不同逻辑函数
> 
> ### ALU Structure
> 
> ![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter12-Arithmetic-59.webp)
> 
> 把 ALU 分成几个功能块：<span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <mi>
> 
> G
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
> b
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
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> G\ block
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
> <span className="mord,mathnormal">
> 
> G
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
> b
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
> oc
> 
> </span>
> 
> <span className="mord,mathnormal" style="margin-right:0.0315em;">
> 
> k
> 
> </span>
> </span>
> </span>
> </span>
> 
> 、<span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <mi>
> 
> P
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
> b
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
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> P\ block
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
> <span className="mord,mathnormal" style="margin-right:0.1389em;">
> 
> P
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
> b
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
> oc
> 
> </span>
> 
> <span className="mord,mathnormal" style="margin-right:0.0315em;">
> 
> k
> 
> </span>
> </span>
> </span>
> </span>
> 
> 、<span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <mi>
> 
> C
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
> r
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
> <mtext>
> 
> 
> 
> </mtext>
> 
> <mi>
> 
> b
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
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> Carry\ block
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">
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
> <span className="mord,mathnormal">
> 
> a
> 
> </span>
> 
> <span className="mord,mathnormal" style="margin-right:0.0278em;">
> 
> r
> 
> </span>
> 
> <span className="mord,mathnormal" style="margin-right:0.0278em;">
> 
> r
> 
> </span>
> 
> <span className="mord,mathnormal" style="margin-right:0.0359em;">
> 
> y
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
> b
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
> oc
> 
> </span>
> 
> <span className="mord,mathnormal" style="margin-right:0.0315em;">
> 
> k
> 
> </span>
> </span>
> </span>
> </span>
> 
> 、<span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <mi>
> 
> S
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
> m
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
> b
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
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> Sum\ block
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
> <span className="mord,mathnormal" style="margin-right:0.0576em;">
> 
> S
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
> m
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
> b
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
> oc
> 
> </span>
> 
> <span className="mord,mathnormal" style="margin-right:0.0315em;">
> 
> k
> 
> </span>
> </span>
> </span>
> </span>
> 
> 
> 
> 在普通加法器中，常见定义是：<span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msub>
> <mi>
> 
> G
> 
> </mi>
> 
> <mi>
> 
> i
> 
> </mi>
> </msub>
> 
> <mo>
> 
> =
> 
> </mo>
> 
> <msub>
> <mi>
> 
> a
> 
> </mi>
> 
> <mi>
> 
> i
> 
> </mi>
> </msub>
> 
> <msub>
> <mi>
> 
> b
> 
> </mi>
> 
> <mi>
> 
> i
> 
> </mi>
> </msub>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> G_i=a_ib_i
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:0.8333em;vertical-align:-0.15em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> <span className="mord,mathnormal">
> 
> G
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3117em;">
> <span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mathnormal,mtight">
> 
> i
> 
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
> <span className="vlist" style="height:0.15em;">
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
> <span className="strut" style="height:0.8444em;vertical-align:-0.15em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> <span className="mord,mathnormal">
> 
> a
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3117em;">
> <span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mathnormal,mtight">
> 
> i
> 
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
> <span className="vlist" style="height:0.15em;">
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
> <span className="mord">
> <span className="mord,mathnormal">
> 
> b
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3117em;">
> <span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mathnormal,mtight">
> 
> i
> 
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
> <span className="vlist" style="height:0.15em;">
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
> </span>
> 
>  <span className="katex">
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
> <mi>
> 
> i
> 
> </mi>
> </msub>
> 
> <mo>
> 
> =
> 
> </mo>
> 
> <msub>
> <mi>
> 
> a
> 
> </mi>
> 
> <mi>
> 
> i
> 
> </mi>
> </msub>
> 
> <mo>
> 
> ⊕
> 
> </mo>
> 
> <msub>
> <mi>
> 
> b
> 
> </mi>
> 
> <mi>
> 
> i
> 
> </mi>
> </msub>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> P_i=a_i\oplus b_i
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:0.8333em;vertical-align:-0.15em;">
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
> <span className="vlist" style="height:0.3117em;">
> <span style="top:-2.55em;margin-left:-0.1389em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mathnormal,mtight">
> 
> i
> 
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
> <span className="vlist" style="height:0.15em;">
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
> <span className="strut" style="height:0.7333em;vertical-align:-0.15em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> <span className="mord,mathnormal">
> 
> a
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3117em;">
> <span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mathnormal,mtight">
> 
> i
> 
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
> <span className="vlist" style="height:0.15em;">
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
> <span className="mspace" style="margin-right:0.2222em;">
> 
> 
> 
> </span>
> 
> <span className="mbin">
> 
> ⊕
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
> <span className="strut" style="height:0.8444em;vertical-align:-0.15em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> <span className="mord,mathnormal">
> 
> b
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3117em;">
> <span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mathnormal,mtight">
> 
> i
> 
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
> <span className="vlist" style="height:0.15em;">
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
> </span>
> 
> 进位关系为：<span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msub>
> <mi>
> 
> C
> 
> </mi>
> 
> <mrow>
> <mi>
> 
> i
> 
> </mi>
> 
> <mo>
> 
> +
> 
> </mo>
> 
> <mn>
> 
> 1
> 
> </mn>
> </mrow>
> </msub>
> 
> <mo>
> 
> =
> 
> </mo>
> 
> <msub>
> <mi>
> 
> G
> 
> </mi>
> 
> <mi>
> 
> i
> 
> </mi>
> </msub>
> 
> <mo>
> 
> +
> 
> </mo>
> 
> <msub>
> <mi>
> 
> P
> 
> </mi>
> 
> <mi>
> 
> i
> 
> </mi>
> </msub>
> 
> <msub>
> <mi>
> 
> C
> 
> </mi>
> 
> <mi>
> 
> i
> 
> </mi>
> </msub>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> C_{i+1}=G_i+P_iC_i
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:0.8917em;vertical-align:-0.2083em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> <span className="mord,mathnormal" style="margin-right:0.0715em;">
> 
> C
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3117em;">
> <span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
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
> i
> 
> </span>
> 
> <span className="mbin,mtight">
> 
> +
> 
> </span>
> 
> <span className="mord,mtight">
> 
> 1
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
> <span className="vlist" style="height:0.2083em;">
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
> <span className="strut" style="height:0.8333em;vertical-align:-0.15em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> <span className="mord,mathnormal">
> 
> G
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3117em;">
> <span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mathnormal,mtight">
> 
> i
> 
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
> <span className="vlist" style="height:0.15em;">
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
> <span className="strut" style="height:0.8333em;vertical-align:-0.15em;">
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
> <span className="vlist" style="height:0.3117em;">
> <span style="top:-2.55em;margin-left:-0.1389em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mathnormal,mtight">
> 
> i
> 
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
> <span className="vlist" style="height:0.15em;">
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
> <span className="mord">
> <span className="mord,mathnormal" style="margin-right:0.0715em;">
> 
> C
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3117em;">
> <span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mathnormal,mtight">
> 
> i
> 
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
> <span className="vlist" style="height:0.15em;">
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
> </span>
> 
> 
> 
> 其中 <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msub>
> <mi>
> 
> G
> 
> </mi>
> 
> <mi>
> 
> i
> 
> </mi>
> </msub>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> G_i
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:0.8333em;vertical-align:-0.15em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> <span className="mord,mathnormal">
> 
> G
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3117em;">
> <span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mathnormal,mtight">
> 
> i
> 
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
> <span className="vlist" style="height:0.15em;">
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
> </span>
> 
>  表示 generate，产生进位；<span className="katex">
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
> <mi>
> 
> i
> 
> </mi>
> </msub>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> P_i
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:0.8333em;vertical-align:-0.15em;">
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
> <span className="vlist" style="height:0.3117em;">
> <span style="top:-2.55em;margin-left:-0.1389em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mathnormal,mtight">
> 
> i
> 
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
> <span className="vlist" style="height:0.15em;">
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
> </span>
> 
>  表示 propagate，传播进位。
> 
> <mark>
> 
> 但是在 ALU 中，对于非加法操作，
> 
> </mark>
> 
> <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <mi>
> 
> P
> 
> </mi>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> P
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
> <span className="mord,mathnormal" style="margin-right:0.1389em;">
> 
> P
> 
> </span>
> </span>
> </span>
> </span>
> 
>  <mark>
> 
> 和
> 
> </mark>
> 
>  <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <mi>
> 
> G
> 
> </mi>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> G
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
> G
> 
> </span>
> </span>
> </span>
> </span>
> 
>  <mark>
> 
> 不一定是真正的 carry-lookahead 中的 propagate 和 generate。它们可能只是由 opcode 控制生成的中间信号。
> 
> </mark>
> 
> 
> 
> **Carry unit 只负责进位逻辑，Sum unit 负责产生最终 result。这样可以复用加法器结构，同时支持多种逻辑和算术功能**
> 
> ## Summary
> 
> ![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter12-Arithmetic-60.webp)
