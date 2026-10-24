# L10-11：并行性

> 从 SIMD、GEMM 分块到 ILP/VLIW 静态调度，再到多核与硬件多线程的并行技术梳理

#### 建议拆分

<table>
<thead>
  <tr>
    <th>
      模块
    </th>
    
    <th>
      页码
    </th>
    
    <th>
      学习目标
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      0. 总览
    </td>
    
    <td>
      1–3
    </td>
    
    <td>
      先知道这节课讲什么：并行的几种层次
    </td>
  </tr>
  
  <tr>
    <td>
      1. 并行处理基础
    </td>
    
    <td>
      4–29
    </td>
    
    <td>
      搞懂为什么需要并行、矩阵乘法例子、Amdahl 定律、SISD/SIMD/MIMD/MISD
    </td>
  </tr>
  
  <tr>
    <td>
      2. 数据级并行 DLP / SIMD
    </td>
    
    <td>
      30–60
    </td>
    
    <td>
      重点看 SIMD、AVX、intrinsics、向量化矩阵乘法、loop unrolling、blocking、GEMM
    </td>
  </tr>
  
  <tr>
    <td>
      3. 指令级并行 ILP
    </td>
    
    <td>
      61–89
    </td>
    
    <td>
      看 VLIW、循环展开、软件流水线、trace scheduling、Itanium/IA-64
    </td>
  </tr>
  
  <tr>
    <td>
      4. 线程级并行 TLP
    </td>
    
    <td>
      90–125
    </td>
    
    <td>
      看多核、多线程、SMT/超线程、操作系统线程和硬件线程区别
    </td>
  </tr>
  
  <tr>
    <td>
      5. 并行编程语言 / OpenMP
    </td>
    
    <td>
      126–149
    </td>
    
    <td>
      会读 OpenMP 的 <code code="parallel for">
        parallel for
      </code>
      
      、fork-join、reduction
    </td>
  </tr>
  
  <tr>
    <td>
      6. 并行同步
    </td>
    
    <td>
      150–167
    </td>
    
    <td>
      重点理解 data race、lock、atomic、AMO、critical section、deadlock
    </td>
  </tr>
</tbody>
</table>

## 第 0 模块：总览，1–3 页

### 第 2 页：整门课从“顺序机器”走向“并行机器”

这一页其实是在告诉你：以前学的单周期、多周期、流水线、cache 等，都还偏“单个处理器内部怎么跑得快”；现在要看更复杂的机器结构，也就是<mark>

**利用并行性来实现高性能**

</mark>

。

课件列了几个层次：

<table>
<thead>
  <tr>
    <th>
      并行层次
    </th>
    
    <th>
      例子
    </th>
    
    <th>
      大概对应
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      并行请求
    </td>
    
    <td>
      搜索引擎同时处理很多搜索请求
    </td>
    
    <td>
      数据中心 / 仓库级计算机
    </td>
  </tr>
  
  <tr>
    <td>
      并行线程
    </td>
    
    <td>
      一个程序分成多个线程，分配到多个核心
    </td>
    
    <td>
      多核 CPU
    </td>
  </tr>
  
  <tr>
    <td>
      并行指令
    </td>
    
    <td>
      同一时刻多条指令在流水线中
    </td>
    
    <td>
      ILP，指令级并行
    </td>
  </tr>
  
  <tr>
    <td>
      并行数据
    </td>
    
    <td>
      一条指令同时处理多个数据
    </td>
    
    <td>
      SIMD / 向量指令 / DLP
    </td>
  </tr>
  
  <tr>
    <td>
      硬件描述
    </td>
    
    <td>
      所有门电路同时工作
    </td>
    
    <td>
      数字电路天然并行
    </td>
  </tr>
  
  <tr>
    <td>
      编程语言
    </td>
    
    <td>
      用语言表达并行
    </td>
    
    <td>
      OpenMP 等
    </td>
  </tr>
</tbody>
</table>

这一页的核心不是背图，而是建立一个总框架：**并行不是只有多核，它可以发生在请求、线程、指令、数据、硬件门级等多个层次。**后面模块会依次展开这些层次。

### 第 3 页：目录

目录给出这份课件的主线：

1. 并行处理
2. 数据级并行 DLP
3. 指令级并行 ILP
4. 线程级并行 TLP
5. 并行编程语言
6. 并行同步

---

## 第 1 模块：并行处理，4–29 页

---

### 第 5 页：从单核计算机开始，了解背景即可

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L10-11-Parallelism-01.webp)

第 5 页回顾了一个**单核计算机**：处理器里有控制器、数据通路、PC、寄存器、ALU；外面有 cache、memory、I/O。课件特别强调“无 FPU, SIMD”，也就是这是一个比较朴素的单核处理器模型。

这页的作用是：先让你记住原始状态是**一个处理器按顺序处理字和字节**，内存/cache 按块组织。后面讲 SIMD、多核、线程时，本质上都是在突破这个“一个 ALU 一次算一个东西”的限制。

---

### 第 6–13 页：矩阵乘法作为性能例子

用矩阵乘法说明：同一个算法，用不同语言和不同底层实现，性能可能差很多。

#### 第 6–7 页：为什么选矩阵乘法

矩阵乘法是工程、图像处理、数据处理里的基础操作，比如图像滤波、降噪等。课件还提到深度学习应用，比如图像分类、目标检测、机器翻译、指纹验证、视频生成等。这些应用底层都离不开大量矩阵或向量计算。

这里出现的 **dgemm** 要记一下：
<mark>

**dgemm = double-precision general matrix multiplication**

</mark>

<mark>

，也就是双精度浮点矩阵乘法。

</mark>



#### 第 8–9 页：矩阵乘法公式

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L10-11-Parallelism-02.webp)

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

A

</mi>

<mo>

×

</mo>

<mi>

B

</mi>
</mrow>

<annotation encoding="application/x-tex">

C = A \times B

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

<span className="mord,mathnormal">

A

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

<munder>
<mo>

∑

</mo>

<mi>

k

</mi>
</munder>

<msub>
<mi>

A

</mi>

<mrow>
<mi>

i

</mi>

<mi>

k

</mi>
</mrow>
</msub>

<mo>

×

</mo>

<msub>
<mi>

B

</mi>

<mrow>
<mi>

k

</mi>

<mi>

j

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

C_{ij} = \sum_k A_{ik} \times B_{kj}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9694em;vertical-align:-0.2861em;">



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
<span className="strut" style="height:2.3521em;vertical-align:-1.3021em;">



</span>

<span className="mop,op-limits">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:1.05em;">
<span style="top:-1.8479em;margin-left:0em;">
<span className="pstrut" style="height:3.05em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0315em;">

k

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
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:1.3021em;">
<span>



</span>
</span>
</span>
</span>
</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

A

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
<span className="mord,mathnormal,mtight" style="margin-right:0.0315em;">

ik

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

×

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.9694em;vertical-align:-0.2861em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0502em;">

B

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.0502em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0315em;">

k

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0572em;">

j

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
</span>

这句话要真正理解：
**C 的第 i 行第 j 列元素，是 A 的第 i 行和 B 的第 j 列做点积。**

也就是说，要算一个 (<span className="katex">
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

i

</mi>

<mi>

j

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

C_{ij}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9694em;vertical-align:-0.2861em;">



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
</span>
</span>
</span>

)，需要让 (<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

k

</mi>
</mrow>

<annotation encoding="application/x-tex">

k

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0315em;">

k

</span>
</span>
</span>
</span>

) 从 0 到 (N-1)，每次做一次乘法和一次加法。矩阵里有 (<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msup>
<mi>

N

</mi>

<mn>

2

</mn>
</msup>
</mrow>

<annotation encoding="application/x-tex">

N^2

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8141em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.109em;">

N

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

) 个元素，所以总计算量大约是：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mn>

2

</mn>

<msup>
<mi>

N

</mi>

<mn>

3

</mn>
</msup>
</mrow>

<annotation encoding="application/x-tex">

2N^3

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8641em;">



</span>

<span className="mord">

2

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.109em;">

N

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

3

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

这里的 2 来自：一次乘法 + 一次加法。

> 其实每一个元素(<span className="katex">
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
> <mi>
> 
> j
> 
> </mi>
> </mrow>
> </msub>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> C_{ij}
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
> <span className="mord,mathnormal,mtight" style="margin-right:0.0572em;">
> 
> ij
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
> 
> )应该是需要（N）次乘法加上（N-1）次加法，一共（2N-1）次，(<span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
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
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> N^2
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:0.8141em;">
> 
> 
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
> </span>
> </span>
> </span>
> 
> ) 个元素，就是（<span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <mn>
> 
> 2
> 
> </mn>
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
> 3
> 
> </mn>
> </msup>
> 
> <mo>
> 
> −
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
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> 2N^3-N^2
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:0.8974em;vertical-align:-0.0833em;">
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
> 3
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
> <span className="strut" style="height:0.8141em;">
> 
> 
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
> </span>
> </span>
> </span>
> 
> ）次运算，二次项省略，即得

#### 第 10 页：Python 版本，重要

Python 代码是三层循环：

```python
for i in range(N):
    for j in range(N):
        c[i+j*N] = 0
        for k in range(N):
            c[i+j*N] += a[i+k*N] * b[k+j*N]
```

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L10-11-Parallelism-03.webp)

课件给的数据很有意思：不管 (N=32,160,480,960)，Python 都大概只有 **5.3–5.5 MFLOPS**。这说明 Python 解释执行三重循环时，主要瓶颈不是矩阵大小，而是每次循环、索引、对象处理、解释器执行带来的巨大开销。

要记住单位：

- **1 MFLOP** = 每秒 (<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msup>
<mn>

10

</mn>

<mn>

6

</mn>
</msup>
</mrow>

<annotation encoding="application/x-tex">

10^6

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8141em;">



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
</span>
</span>
</span>

) 次浮点运算；
- **1 GFLOP** = 每秒 (<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msup>
<mn>

10

</mn>

<mn>

9

</mn>
</msup>
</mrow>

<annotation encoding="application/x-tex">

10^9

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8141em;">



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
<span className="vlist" style="height:0.8141em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
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

) 次浮点运算；
- dgemm 的浮点运算数约为 (<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mn>

2

</mn>

<msup>
<mi>

N

</mi>

<mn>

3

</mn>
</msup>
</mrow>

<annotation encoding="application/x-tex">

2N^3

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8141em;">



</span>

<span className="mord">

2

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.109em;">

N

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

3

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

)。

如果考试给你运行时间 (t)，让你算性能：

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

F

</mi>

<mi>

L

</mi>

<mi>

O

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
<mn>

2

</mn>

<msup>
<mi>

N

</mi>

<mn>

3

</mn>
</msup>
</mrow>

<mrow>
<mi>

t

</mi>

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
</mrow>

<annotation encoding="application/x-tex">

GFLOPS = \frac{2N^3}{t \times 10^9}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

GF

</span>

<span className="mord,mathnormal">

L

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

O

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
<span className="strut" style="height:2.2604em;vertical-align:-0.7693em;">



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

2

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.109em;">

N

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

3

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

这个公式非常实用。

#### 第 11–12 页：C 版本和计时

第 11 页给出 C 版本。它也是三重循环，但 C 是编译执行，类型固定、内存布局更直接，所以比 Python 快非常多。

注意代码里有一个局部变量：

```c
double cij = 0;
...
cij += a[i+k*N] * b[k+j*N];
...
c[i+j*N] = cij;
```

这样做的好处是：先把结果累加在寄存器或局部变量里，最后再写回内存，减少频繁访问 `c[i+j*N]` 的成本。

第 12 页讲计时，用 `clock()` 记录开始和结束时间，然后：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi mathvariant="normal">

Δ

</mi>

<mi>

t

</mi>

<mo>

=

</mo>

<mfrac>
<mrow>
<mi>

e

</mi>

<mi>

n

</mi>

<mi>

d

</mi>

<mo>

−

</mo>

<mi>

s

</mi>

<mi>

t

</mi>

<mi>

a

</mi>

<mi>

r

</mi>

<mi>

t

</mi>
</mrow>

<mrow>
<mi>

C

</mi>

<mi>

L

</mi>

<mi>

O

</mi>

<mi>

C

</mi>

<mi>

K

</mi>

<msub>
<mi>

S

</mi>

<mi>

P

</mi>
</msub>

<mi>

E

</mi>

<msub>
<mi>

R

</mi>

<mi>

S

</mi>
</msub>

<mi>

E

</mi>

<mi>

C

</mi>
</mrow>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

\Delta t = \frac{end-start}{CLOCKS_PER_SEC}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord">

Δ

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
<span className="strut" style="height:2.2074em;vertical-align:-0.836em;">



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

<span className="mord,mathnormal">

L

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

O

</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

K

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0576em;">

S

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.0576em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.1389em;">

P

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

<span className="mord,mathnormal" style="margin-right:0.0576em;">

E

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0077em;">

R

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.0077em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

S

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

<span className="mord,mathnormal" style="margin-right:0.0576em;">

E

</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

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

e

</span>

<span className="mord,mathnormal">

n

</span>

<span className="mord,mathnormal">

d

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

−

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mord,mathnormal">

s

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

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

#### 第 13 页：C vs Python

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L10-11-Parallelism-04.webp)

课件给的数据是：C 大概 **0.91–1.32 GFLOPS**，Python 大概 **0.0053–0.0055 GFLOPS**，差了约 **240 倍**。

这一页不要只记“C 比 Python 快”。更重要的是理解差距来源：

1. Python 三重循环解释执行，每次循环开销巨大；
2. C 编译成机器码，循环和浮点操作更直接；
3. C 可以更好利用寄存器、流水线、编译器优化；
4. 但这个 C 版本仍然只是普通 scalar 版本，还没有充分使用 SIMD、多核、cache blocking 等优化。

所以这几页是在铺垫后面的主题：
**即使用 C，**<mark>

**离硬件峰值性能也还差很远；想继续提升，就得靠并行。**

</mark>



---

### 第 14–15 页：为什么需要并行，重要

一个大背景：**CPU 时钟频率不再持续增加**。

以前提升性能有个简单粗暴的方法：提高主频。主频越高，单位时间执行的周期越多。但后来遇到技术和经济问题：散热困难、功耗太高、冷却成本不现实。所以现代处理器不能只靠“把频率拧高”。

课件用了航空公司的类比：飞机最大速度受声速和经济性限制，那要提高运输吞吐量怎么办？不是无限提高单架飞机速度，而是用更多飞机、更大飞机、更多座位。计算机也是类似：单个核心不能无限快，就用更多核心、更多执行单元、更多 SIMD lanes。

第 15 页区分两个概念：

<table>
<thead>
  <tr>
    <th>
      概念
    </th>
    
    <th>
      含义
    </th>
    
    <th>
      难度
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      Multiprogramming，并行程序/多道程序
    </td>
    
    <td>
      同时运行多个独立程序
    </td>
    
    <td>
      相对简单
    </td>
  </tr>
  
  <tr>
    <td>
      Parallel Computing，并行计算
    </td>
    
    <td>
      让一个程序更快运行
    </td>
    
    <td>
      更难
    </td>
  </tr>
</tbody>
</table>

这门课后面关注的是第二个：**如何把一个程序拆开并行执行，让它更快完成。**

这个区别很重要。比如你一边开微信一边开浏览器，这是 multiprogramming；但把一个矩阵乘法拆给 8 个核心一起算，这是 parallel computing。

---

### 第 16–21 页：Amdahl 定律

这是第 1 模块最可能考计算题的地方。

#### 第 16 页：公式本体，必须掌握

Amdahl 定律讨论的是：如果程序中只有一部分能被加速，那么整体能加速多少？

设：

- <mark>

(

</mark>

<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

F

</mi>
</mrow>

<annotation encoding="application/x-tex">

F

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

F

</span>
</span>
</span>
</span>

<mark>

)：程序中可以被加速的部分所占比例

</mark>

；
- (<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mn>

1

</mn>

<mo>

−

</mo>

<mi>

F

</mi>
</mrow>

<annotation encoding="application/x-tex">

1-F

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

−

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

F

</span>
</span>
</span>
</span>

)：不能被加速的部分；
- (<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

S

</mi>

<mi>

E

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

S_E

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0576em;">

S

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.0576em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

E

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

)：可加速部分的加速倍数；
- 总加速比：

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

1

</mn>

<mrow>
<mo stretchy="false">

(

</mo>

<mn>

1

</mn>

<mo>

−

</mo>

<mi>

F

</mi>

<mo stretchy="false">

)

</mo>

<mo>

+

</mo>

<mi>

F

</mi>

<mi mathvariant="normal">

/

</mi>

<msub>
<mi>

S

</mi>

<mi>

E

</mi>
</msub>
</mrow>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

Speedup = \frac{1}{(1-F)+F/S_E}

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
<span className="strut" style="height:2.2574em;vertical-align:-0.936em;">



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
<span className="mopen">

(

</span>

<span className="mord">

1

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

−

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

F

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

<span className="mord,mathnormal" style="margin-right:0.1389em;">

F

</span>

<span className="mord">

/

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0576em;">

S

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.0576em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

E

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
<span className="vlist" style="height:0.936em;">
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

理解方式很简单：
原来程序总时间看作 1。不能加速的部分还是 (<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mn>

1

</mn>

<mo>

−

</mo>

<mi>

F

</mi>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

1-F)

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

−

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

F

</span>

<span className="mclose">

)

</span>
</span>
</span>
</span>

，能加速的部分从 (<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

F

</mi>
</mrow>

<annotation encoding="application/x-tex">

F

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

F

</span>
</span>
</span>
</span>

) 变成 (<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

F

</mi>

<mi mathvariant="normal">

/

</mi>

<msub>
<mi>

S

</mi>

<mi>

E

</mi>
</msub>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

F/S_E)

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

F

</span>

<span className="mord">

/

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0576em;">

S

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.0576em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

E

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
</span>
</span>
</span>

。所以新时间是：

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

1

</mn>

<mo>

−

</mo>

<mi>

F

</mi>

<mo stretchy="false">

)

</mo>

<mo>

+

</mo>

<mi>

F

</mi>

<mi mathvariant="normal">

/

</mi>

<msub>
<mi>

S

</mi>

<mi>

E

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

(1-F)+F/S_E

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

1

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

<span className="mord,mathnormal" style="margin-right:0.1389em;">

F

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

<span className="mord,mathnormal" style="margin-right:0.1389em;">

F

</span>

<span className="mord">

/

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0576em;">

S

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.0576em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

E

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

加速比就是：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mfrac>
<mtext>

原时间

</mtext>

<mtext>

新时间

</mtext>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

\frac{原时间}{新时间}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
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
<span className="mord,cjk_fallback">

新时间

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
<span className="mord,cjk_fallback">

原时间

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

也就是上面的公式。

#### 第 17 页：例题，必须会

题目：程序一半时间可以加快 2 倍，整体加速多少？

这里：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

F

</mi>

<mo>

=

</mo>

<mn>

0.5

</mn>

<mo separator="true">

,

</mo>

<mspace width="1em">



</mspace>

<msub>
<mi>

S

</mi>

<mi>

E

</mi>
</msub>

<mo>

=

</mo>

<mn>

2

</mn>
</mrow>

<annotation encoding="application/x-tex">

F=0.5,\quad S_E=2

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

F

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

<span className="mord">

0.5

</span>

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:1em;">



</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0576em;">

S

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.0576em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

E

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

2

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

1

</mn>

<mrow>
<mo stretchy="false">

(

</mo>

<mn>

1

</mn>

<mo>

−

</mo>

<mn>

0.5

</mn>

<mo stretchy="false">

)

</mo>

<mo>

+

</mo>

<mn>

0.5

</mn>

<mi mathvariant="normal">

/

</mi>

<mn>

2

</mn>
</mrow>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

Speedup = \frac{1}{(1-0.5)+0.5/2}

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
<span className="strut" style="height:2.2574em;vertical-align:-0.936em;">



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
<span className="mopen">

(

</span>

<span className="mord">

1

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

−

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mord">

0.5

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

<span className="mord">

0.5/2

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
<span className="vlist" style="height:0.936em;">
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

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mo>

=

</mo>

<mfrac>
<mn>

1

</mn>

<mrow>
<mn>

0.5

</mn>

<mo>

+

</mo>

<mn>

0.25

</mn>
</mrow>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

= \frac{1}{0.5+0.25}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.3669em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:2.0908em;vertical-align:-0.7693em;">



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

0.5

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mord">

0.25

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

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mo>

=

</mo>

<mfrac>
<mn>

1

</mn>

<mn>

0.75

</mn>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

= \frac{1}{0.75}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.3669em;">



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

0.75

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

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mo>

=

</mo>

<mn>

1.33

</mn>
</mrow>

<annotation encoding="application/x-tex">

= 1.33

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.3669em;">



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

1.33

</span>
</span>
</span>
</span>
</span>

所以整体只加速 **1.33 倍**，不是 2 倍。

这就是 Amdahl 定律最想告诉你的事：
**局部优化很猛，不代表整体加速也很猛。不能加速的部分会拖后腿。**

#### 第 18–19 页：最大可达到加速，超级重要

如果可加速部分的加速倍数趋近无穷大：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<msub>
<mi>

S

</mi>

<mi>

E

</mi>
</msub>

<mo>

→

</mo>

<mi mathvariant="normal">

∞

</mi>
</mrow>

<annotation encoding="application/x-tex">

S_E \to \infty

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0576em;">

S

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.0576em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

E

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
<span className="strut" style="height:0.4306em;">



</span>

<span className="mord">

∞

</span>
</span>
</span>
</span>
</span>

那么：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

F

</mi>

<mi mathvariant="normal">

/

</mi>

<msub>
<mi>

S

</mi>

<mi>

E

</mi>
</msub>

<mo>

→

</mo>

<mn>

0

</mn>
</mrow>

<annotation encoding="application/x-tex">

F/S_E \to 0

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

F

</span>

<span className="mord">

/

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0576em;">

S

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.0576em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

E

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
<span className="strut" style="height:0.6444em;">



</span>

<span className="mord">

0

</span>
</span>
</span>
</span>
</span>

所以最大加速比是：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<msub>
<mi>

S

</mi>

<mrow>
<mi>

m

</mi>

<mi>

a

</mi>

<mi>

x

</mi>
</mrow>
</msub>

<mo>

=

</mo>

<mfrac>
<mn>

1

</mn>

<mrow>
<mn>

1

</mn>

<mo>

−

</mo>

<mi>

F

</mi>
</mrow>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

S_{max} = \frac{1}{1-F}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0576em;">

S

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0576em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

ma

</span>

<span className="mord,mathnormal,mtight">

x

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
<span className="strut" style="height:2.0908em;vertical-align:-0.7693em;">



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

1

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

−

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

F

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

课件例子：如果 (F=0.95)，也就是 95% 的程序可以并行化，那么：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<msub>
<mi>

S

</mi>

<mrow>
<mi>

m

</mi>

<mi>

a

</mi>

<mi>

x

</mi>
</mrow>
</msub>

<mo>

=

</mo>

<mfrac>
<mn>

1

</mn>

<mrow>
<mn>

1

</mn>

<mo>

−

</mo>

<mn>

0.95

</mn>
</mrow>
</mfrac>

<mo>

=

</mo>

<mn>

20

</mn>
</mrow>

<annotation encoding="application/x-tex">

S_{max} = \frac{1}{1-0.95} = 20

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0576em;">

S

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0576em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

ma

</span>

<span className="mord,mathnormal,mtight">

x

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
<span className="strut" style="height:2.0908em;vertical-align:-0.7693em;">



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

1

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

−

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mord">

0.95

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
<span className="strut" style="height:0.6444em;">



</span>

<span className="mord">

20

</span>
</span>
</span>
</span>
</span>

注意：这已经是假设可并行部分无限快了，现实中不可能真的无限快。所以 20 倍是理论上限。

课件还给了一个工程妥协：让顺序部分时间和并行部分时间相等：

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

−

</mo>

<mi>

F

</mi>

<mo>

=

</mo>

<mi>

F

</mi>

<mi mathvariant="normal">

/

</mi>

<msub>
<mi>

S

</mi>

<mi>

E

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

1-F = F/S_E

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

−

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

F

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

<span className="mord,mathnormal" style="margin-right:0.1389em;">

F

</span>

<span className="mord">

/

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0576em;">

S

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.0576em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

E

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

所以：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<msub>
<mi>

S

</mi>

<mi>

E

</mi>
</msub>

<mo>

=

</mo>

<mfrac>
<mi>

F

</mi>

<mrow>
<mn>

1

</mn>

<mo>

−

</mo>

<mi>

F

</mi>
</mrow>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

S_E = \frac{F}{1-F}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0576em;">

S

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.0576em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

E

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
<span className="mord">

1

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

−

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

F

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

当 (F=0.95)：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<msub>
<mi>

S

</mi>

<mi>

E

</mi>
</msub>

<mo>

=

</mo>

<mfrac>
<mn>

0.95

</mn>

<mn>

0.05

</mn>
</mfrac>

<mo>

=

</mo>

<mn>

19

</mn>

<mo>

≈

</mo>

<mn>

20

</mn>
</mrow>

<annotation encoding="application/x-tex">

S_E = \frac{0.95}{0.05} = 19 \approx 20

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0576em;">

S

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.0576em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

E

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

0.05

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

0.95

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

19

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

20

</span>
</span>
</span>
</span>
</span>

此时整体加速：

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

1

</mn>

<mrow>
<mn>

0.05

</mn>

<mo>

+

</mo>

<mn>

0.05

</mn>
</mrow>
</mfrac>

<mo>

=

</mo>

<mn>

10

</mn>
</mrow>

<annotation encoding="application/x-tex">

Speedup = \frac{1}{0.05+0.05} = 10

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
<span className="strut" style="height:2.0908em;vertical-align:-0.7693em;">



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

0.05

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mord">

0.05

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
<span className="strut" style="height:0.6444em;">



</span>

<span className="mord">

10

</span>
</span>
</span>
</span>
</span>

也就是说，**把 95% 的部分加速 20 倍，整体只有 10 倍加速**。这就是并行系统里很经典的“收益递减”。第 19 页图上的曲线也在表达：处理器越来越多，最后会被顺序部分卡住。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L10-11-Parallelism-05.webp)

#### 第 20 页：<mark>强扩展、弱扩展、负载平衡</mark>，重要

这页概念很容易考简答。其实也在讲并行的**评价标准**

**强扩展 Strong Scaling**：
<mark>

问题规模不变，增加处理器数量

</mark>

，看能不能跑得更快。

比如：同一个 (<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mn>

10000

</mn>

<mo>

×

</mo>

<mn>

10000

</mn>
</mrow>

<annotation encoding="application/x-tex">

10000 \times 10000

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.7278em;vertical-align:-0.0833em;">



</span>

<span className="mord">

10000

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

10000

</span>
</span>
</span>
</span>

) 矩阵乘法，用 1 个核、2 个核、4 个核、8 个核分别算，看速度能否对应提升。

**弱扩展 Weak Scaling**：
每个处理器负责的工作量大致不变，<mark>

处理器变多时，问题规模也同比例变大

</mark>

。

比如：1 个核心算 (N) 个数据，8 个核心算 (8N) 个数据。如果总时间差不多，说明弱扩展好。

<mark>

强扩展更难

</mark>

，因为问题总量固定，处理器越多，每个处理器分到的工作越少，但通信、同步、调度开销不会凭空消失。

这页还提到**负载平衡 load balancing**：<mark>

每个处理器最好做差不多的工作

</mark>

。如果一个处理器工作量是其他处理器的两倍，大家都要等它，整体速度会被它拖住。这个点后面 OpenMP、线程同步里也会继续出现。

#### 第 21 页：练习题

题目：程序花费 80% 时间在平方根例程中。要让程序整体快 5 倍，平方根例程必须加速多少？

这里：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

F

</mi>

<mo>

=

</mo>

<mn>

0.8

</mn>

<mo separator="true">

,

</mo>

<mspace width="1em">



</mspace>

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

<mn>

5

</mn>
</mrow>

<annotation encoding="application/x-tex">

F=0.8,\quad Speedup=5

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

F

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

0.8

</span>

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:1em;">



</span>

<span className="mspace" style="margin-right:0.1667em;">



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
<span className="strut" style="height:0.6444em;">



</span>

<span className="mord">

5

</span>
</span>
</span>
</span>
</span>

代入 Amdahl：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mn>

5

</mn>

<mo>

=

</mo>

<mfrac>
<mn>

1

</mn>

<mrow>
<mo stretchy="false">

(

</mo>

<mn>

1

</mn>

<mo>

−

</mo>

<mn>

0.8

</mn>

<mo stretchy="false">

)

</mo>

<mo>

+

</mo>

<mn>

0.8

</mn>

<mi mathvariant="normal">

/

</mi>

<msub>
<mi>

S

</mi>

<mi>

E

</mi>
</msub>
</mrow>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

5 = \frac{1}{(1-0.8)+0.8/S_E}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6444em;">



</span>

<span className="mord">

5

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
<span className="strut" style="height:2.2574em;vertical-align:-0.936em;">



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
<span className="mopen">

(

</span>

<span className="mord">

1

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

−

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mord">

0.8

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

<span className="mord">

0.8/

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0576em;">

S

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.0576em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

E

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
<span className="vlist" style="height:0.936em;">
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

也就是：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mn>

5

</mn>

<mo>

=

</mo>

<mfrac>
<mn>

1

</mn>

<mrow>
<mn>

0.2

</mn>

<mo>

+

</mo>

<mn>

0.8

</mn>

<mi mathvariant="normal">

/

</mi>

<msub>
<mi>

S

</mi>

<mi>

E

</mi>
</msub>
</mrow>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

5 = \frac{1}{0.2+0.8/S_E}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6444em;">



</span>

<span className="mord">

5

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
<span className="strut" style="height:2.2574em;vertical-align:-0.936em;">



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

0.2

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mord">

0.8/

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0576em;">

S

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.0576em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

E

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
<span className="vlist" style="height:0.936em;">
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

两边取倒数：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mn>

0.2

</mn>

<mo>

=

</mo>

<mn>

0.2

</mn>

<mo>

+

</mo>

<mn>

0.8

</mn>

<mi mathvariant="normal">

/

</mi>

<msub>
<mi>

S

</mi>

<mi>

E

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

0.2 = 0.2+0.8/S_E

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6444em;">



</span>

<span className="mord">

0.2

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

0.2

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

0.8/

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0576em;">

S

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.0576em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

E

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

所以：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mn>

0.8

</mn>

<mi mathvariant="normal">

/

</mi>

<msub>
<mi>

S

</mi>

<mi>

E

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

0.8/S_E = 0

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord">

0.8/

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0576em;">

S

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.0576em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

E

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
</span>

这要求：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<msub>
<mi>

S

</mi>

<mi>

E

</mi>
</msub>

<mo>

=

</mo>

<mi mathvariant="normal">

∞

</mi>
</mrow>

<annotation encoding="application/x-tex">

S_E = \infty

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0576em;">

S

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.0576em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

E

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
<span className="strut" style="height:0.4306em;">



</span>

<span className="mord">

∞

</span>
</span>
</span>
</span>
</span>

所以答案不是 5、20、500，而是 **None of above**。因为 80% 可加速时，理论最大加速就是：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<msub>
<mi>

S

</mi>

<mrow>
<mi>

m

</mi>

<mi>

a

</mi>

<mi>

x

</mi>
</mrow>
</msub>

<mo>

=

</mo>

<mfrac>
<mn>

1

</mn>

<mrow>
<mn>

1

</mn>

<mo>

−

</mo>

<mn>

0.8

</mn>
</mrow>
</mfrac>

<mo>

=

</mo>

<mn>

5

</mn>
</mrow>

<annotation encoding="application/x-tex">

S_{max} = \frac{1}{1-0.8} = 5

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0576em;">

S

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0576em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

ma

</span>

<span className="mord,mathnormal,mtight">

x

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
<span className="strut" style="height:2.0908em;vertical-align:-0.7693em;">



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

1

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

−

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mord">

0.8

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
<span className="strut" style="height:0.6444em;">



</span>

<span className="mord">

5

</span>
</span>
</span>
</span>
</span>

要达到这个上限，平方根部分必须无限快，有限倍数都不行。这个题很“阴”，考试很爱出。

---

### 第 22 页：并行的类型，框架重要

这页把并行分成硬件和软件两类。

**硬件的并行性（Parallelism in Hardware）**

- 单处理器中的并行性（Parallelism in a Uniprocessor）

  - 流水线（Pipelining）
  - 超标量（Superscalar）, VLIW 等等
- SIMD 指令，Vector processors，GPUs
- 多处理器（Multiprocessor）

  - Symmetric shared-memory multiprocessors
  - Distributed-memory multiprocessors
  - Chip-multiprocessors a.k.a. Multi-cores
- 多计算机（Multicomputers），又称集群（clusters）

**软件中的并行性（Parallelism in Software）**

- 指令级并行（Instruction level parallelism） ILP
- 任务级并行（Task-level parallelism）
- 数据级并行（Data-level parallelism） DLP
- 事务级并行（Transaction level parallelism）

这页不用死背所有英文，但要能建立映射：

<table>
<thead>
  <tr>
    <th>
      类型
    </th>
    
    <th>
      核心问题
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      DLP
    </td>
    
    <td>
      同一操作作用在很多数据上
    </td>
  </tr>
  
  <tr>
    <td>
      ILP
    </td>
    
    <td>
      多条指令能不能同时执行
    </td>
  </tr>
  
  <tr>
    <td>
      TLP
    </td>
    
    <td>
      多个线程/任务能不能同时执行
    </td>
  </tr>
</tbody>
</table>

后面模块基本就是围绕 DLP、ILP、TLP 展开。

---

### 第 23–27 页：Flynn 分类，重要

Flynn 分类是按照两个维度分机器：

1. 指令流是单个还是多个；
2. 数据流是单个还是多个。

于是得到四类：

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 50.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L10-11-Parallelism-06.webp" />
      </p>
    </td>
    
    
      <td style="width: 49.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L10-11-Parallelism-07.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 50.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L10-11-Parallelism-08.webp" />
      </p>
    </td>
    
    
      <td style="width: 49.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L10-11-Parallelism-09.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

<table>
<thead>
  <tr>
    <th>
      类型
    </th>
    
    <th>
      全称
    </th>
    
    <th>
      含义
    </th>
    
    <th>
      重要度
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      SISD
    </td>
    
    <td>
      Single Instruction Single Data
    </td>
    
    <td>
      单指令流、单数据流
    </td>
    
    <td>
      中
    </td>
  </tr>
  
  <tr>
    <td>
      SIMD
    </td>
    
    <td>
      Single Instruction Multiple Data
    </td>
    
    <td>
      单指令流、多数据流
    </td>
    
    <td>
      高
    </td>
  </tr>
  
  <tr>
    <td>
      MISD
    </td>
    
    <td>
      Multiple Instruction Single Data
    </td>
    
    <td>
      多指令流、单数据流
    </td>
    
    <td>
      低
    </td>
  </tr>
  
  <tr>
    <td>
      MIMD
    </td>
    
    <td>
      Multiple Instruction Multiple Data
    </td>
    
    <td>
      多指令流、多数据流
    </td>
    
    <td>
      高
    </td>
  </tr>
</tbody>
</table>

#### 第 23 页：SISD

SISD 是传统顺序计算机：一个指令流处理一个数据流。课件说传统单处理器机器就是 SISD。

注意一个小细节：流水线机器虽然内部多个阶段同时工作，但从程序员视角看，仍然是单一指令流按顺序推进。所以 Flynn 分类里可以把传统流水线处理器看成 SISD。

#### 第 24 页：SIMD

SIMD 是本课后面很重要的主题：**一条指令，同时处理多个数据。**

典型例子：

- Intel SIMD 指令扩展；
- NVIDIA GPU；
- 向量处理器。

比如你要算：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<msub>
<mi>

A

</mi>

<mn>

0

</mn>
</msub>

<mo>

+

</mo>

<msub>
<mi>

B

</mi>

<mn>

0

</mn>
</msub>

<mo separator="true">

,

</mo>

<mtext>



</mtext>

<msub>
<mi>

A

</mi>

<mn>

1

</mn>
</msub>

<mo>

+

</mo>

<msub>
<mi>

B

</mi>

<mn>

1

</mn>
</msub>

<mo separator="true">

,

</mo>

<mtext>



</mtext>

<msub>
<mi>

A

</mi>

<mn>

2

</mn>
</msub>

<mo>

+

</mo>

<msub>
<mi>

B

</mi>

<mn>

2

</mn>
</msub>

<mo separator="true">

,

</mo>

<mtext>



</mtext>

<msub>
<mi>

A

</mi>

<mn>

3

</mn>
</msub>

<mo>

+

</mo>

<msub>
<mi>

B

</mi>

<mn>

3

</mn>
</msub>
</mrow>

<annotation encoding="application/x-tex">

A_0+B_0,\ A_1+B_1,\ A_2+B_2,\ A_3+B_3

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

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0502em;">

B

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0502em;margin-right:0.05em;">
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

<span className="mpunct">

,

</span>

<span className="mspace">



</span>

<span className="mspace" style="margin-right:0.1667em;">



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

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0502em;">

B

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0502em;margin-right:0.05em;">
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

<span className="mpunct">

,

</span>

<span className="mspace">



</span>

<span className="mspace" style="margin-right:0.1667em;">



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

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0502em;">

B

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0502em;margin-right:0.05em;">
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

<span className="mpunct">

,

</span>

<span className="mspace">



</span>

<span className="mspace" style="margin-right:0.1667em;">



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

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0502em;">

B

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0502em;margin-right:0.05em;">
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
</span>
</span>

普通 scalar 做法可能要四次加法指令；SIMD 可以一条向量加法指令同时完成多个加法。它对应后面的 **数据级并行 DLP**。

#### 第 25 页：MIMD

MIMD 是多个自主处理器同时执行不同指令，处理不同数据。

典型例子：

- 多核 CPU；
- 多处理器系统；
- 数据中心、仓库级计算机。

它对应后面的 <mark>

**线程级并行 TLP**

</mark>

。多个线程可以跑在多个核心上，每个线程有自己的指令序列和状态。

#### 第 26 页：MISD

MISD 是多指令流、单数据流。课件说它没什么应用，本课程不涉及。考试最多让你认一下，不太会深入考。

#### 第 27 页：SIMD + MIMD 最常见，SPMD 要记

课件强调：<mark>

**SIMD 和 MIMD 是现代体系结构中最常见的并行方式，而且通常在同一个系统中同时存在。**

</mark>



比如一台现代电脑：

- 多个 CPU 核心：MIMD；
- 每个核心内部有 AVX/SIMD 指令：SIMD。

所以高性能程序常常是：**多线程 + 每个线程内部 SIMD 向量化**。

这一页还出现了 **SPMD**：

**SPMD = Single Program Multiple Data，单程序多数据。**

意思是：多个处理器/线程运行同一个程序，但处理不同的数据，并通过同步原语协调。

比如 8 个线程都执行同一个矩阵乘法函数，但第 0 个线程算第 0–999 行，第 1 个线程算第 1000–1999 行。这就是 SPMD 风格。

---

### 第 28–29 页：应用程序中的并行分类 DLP / ILP / TLP，重要

这两页是前面所有分类的落地版，很适合考试简答。

#### 第 28 页：DLP 和 ILP

1. **DLP，Data-Level Parallelism，数据级并行**：

- 对应 SIMD；
- 一个指令流同时操作多个数据；
- 适合数组、矩阵、图像、向量计算；
- 限制来自不规则数据访问和内存带宽。

一句话：
**DLP 是“同样的操作，对很多数据一起做”。**

1. **ILP，Instruction-Level Parallelism，指令级并行**：

> 一个 PC，一套架构寄存器

- 同时执行多条指令；
- 例如流水线、超标量、乱序执行、VLIW；
- 可以由硬件管理，也可以由编译器管理（VLIW）；
- 限制来自数据依赖和控制依赖，也就是流水线冒险。

一句话：
**ILP 是“一个线程内部，多条指令能不能重叠执行”。**

#### 第 29 页：TLP

**TLP，Thread-Level Parallelism，线程级/任务级并行**：

- 对应 MIMD；
- 同一个应用程序的多个线程或指令序列并发执行；
- <mark>

每个线程有自己的程序计数器 PC 和处理器状态

</mark>

，比如寄存器；
- 限制来自通信、同步开销和算法特性。

一句话：
**TLP 是“把一个程序拆成多个线程/任务同时跑”。**

第 29 页还区分了几个概念：

<table>
<thead>
  <tr>
    <th>
      概念
    </th>
    
    <th>
      解释
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      Physical CPU / core
    </td>
    
    <td>
      真实物理核心，一般一次运行一个硬件线程
    </td>
  </tr>
  
  <tr>
    <td>
      Logical CPU
    </td>
    
    <td>
      操作系统看到的逻辑处理单元
    </td>
  </tr>
  
  <tr>
    <td>
      SMT ( 超线程)
    </td>
    
    <td>
      一个物理核心同时维护多个线程状态，共享执行资源
    </td>
  </tr>
</tbody>
</table>

最容易混的是：
**多核 ≠ 超线程。**

<mark>

多核是有多个真实核心

</mark>

；<mark>

超线程是一个核心伪装成多个逻辑 CPU

</mark>

，用来提高资源利用率，但不是性能直接翻倍。

---

## 第 2 模块：数据级并行 DLP / SIMD

继续讲**第 2 模块：数据级并行 Data Level Parallelism，约第 30–60 页**。这一块是本课件的核心之一，主线很清楚：

**SIMD 是什么 → AVX 怎么用 → 为什么没达到理论峰值 → 用loop unrolling 和 blocking 继续优化 → GEMM 为什么这么写。**

---

### 第 30–34 页：SIMD 背景，略讲但要知道

#### 第 31 页：SIMD 应用和实现，重要度中等

课件列了 SIMD 的典型应用：

<table>
<thead>
  <tr>
    <th>
      应用领域
    </th>
    
    <th>
      为什么适合 SIMD
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      科学计算：Matlab、NumPy
    </td>
    
    <td>
      大量向量/矩阵操作
    </td>
  </tr>
  
  <tr>
    <td>
      图形和视频处理
    </td>
    
    <td>
      像素处理高度重复
    </td>
  </tr>
  
  <tr>
    <td>
      大数据 / 深度学习
    </td>
    
    <td>
      大量张量、矩阵乘法
    </td>
  </tr>
  
  <tr>
    <td>
      游戏
    </td>
    
    <td>
      图形、物理、动画计算
    </td>
  </tr>
</tbody>
</table>

实现方面包括：

- x86；
- ARM；
- RISC-V vector extensions。

**什么样的程序适合 SIMD？****数据规则、操作相同、循环独立、内存访问连续的程序最适合 SIMD。**

---

#### 第 32–34 页：SIMD 发展和 CPU 特性，略讲

第 32 页说第一个 SIMD 扩展可以追溯到 MIT Lincoln Labs TX-2，1957。这个历史不用背。

第 33 页展示 x86 SIMD 的演进：MMX、SSE、SSE2、SSE3、SSE4、<mark>

AVX

</mark>

。主线是：

> 新指令 + 更宽寄存器 + 更多寄存器 = 更多并行性。

第 34 页用一台 i7-5557U 做例子，列出 CPU 支持的特性，比如 FPU、SSE、SSE2、SSE3、SSE4.1、SSE4.2、AVX、AVX2、FMA 等。重点不是背这些字符串，而是看懂：**现代 CPU 内部已经有很多 SIMD/浮点加速硬件**

---

### 第 35–37 页：SIMD 寄存器、数据类型、向量模式

这三页是 SIMD 概念的基础，建议认真看。

#### 第 35 页：SIMD Registers

课件展示了 x86 SIMD 寄存器：

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L10-11-Parallelism-10.webp)

- **XMM**：128-bit；
- **YMM**：256-bit；
- YMM 的低 128 bit 可以看成对应的 XMM；
- 图里有 YMM0 到 YMM15。

可以这么理解：

普通标量寄存器像一个小盒子，一次放一个 double。
SIMD 寄存器像一个长盒子，一次能放多个 double 或 float。

比如 AVX 的 **256-bit YMM 寄存器**：

- 一个 double 是 64 bit；
- 所以 256 bit 可以放：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mn>

256

</mn>

<mi mathvariant="normal">

/

</mi>

<mn>

64

</mn>

<mo>

=

</mo>

<mn>

4

</mn>
</mrow>

<annotation encoding="application/x-tex">

256 / 64 = 4

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord">

256/64

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

也就是 **4 个 double**。

如果是 float，一个 float 是 32 bit：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mn>

256

</mn>

<mi mathvariant="normal">

/

</mi>

<mn>

32

</mn>

<mo>

=

</mo>

<mn>

8

</mn>
</mrow>

<annotation encoding="application/x-tex">

256 / 32 = 8

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord">

256/32

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
</span>
</span>
</span>
</span>

所以可以放 **8 个 float**。

这就是为什么 AVX 对 double 理论上能有接近 4 倍的数据并行度。

---

#### 第 36 页：SIMD Data Types

这一页说明同样长度的 SIMD 寄存器可以按不同数据类型解释。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L10-11-Parallelism-11.webp)

128-bit SSE/AVX-128 可以装：

- 4 个 float；
- 2 个 double；
- 16 个 byte；
- 8 个 16-bit word；
- 4 个 32-bit doubleword；
- 2 个 64-bit quadword。

256-bit AVX 可以装：

- 8 个 float；
- 4 个 double。

现在还有 AVX-512，可以进一步扩展到 512-bit。对 double 来说：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mn>

512

</mn>

<mi mathvariant="normal">

/

</mi>

<mn>

64

</mn>

<mo>

=

</mo>

<mn>

8

</mn>
</mrow>

<annotation encoding="application/x-tex">

512 / 64 = 8

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord">

512/64

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
</span>
</span>
</span>
</span>

所以 AVX-512 一条向量指令可以处理 8 个 double。

比如：

<table>
<thead>
  <tr>
    <th>
      SIMD 宽度
    </th>
    
    <th>
      double 数量
    </th>
    
    <th>
      float 数量
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      128 bit
    </td>
    
    <td>
      2
    </td>
    
    <td>
      4
    </td>
  </tr>
  
  <tr>
    <td>
      256 bit
    </td>
    
    <td>
      4
    </td>
    
    <td>
      8
    </td>
  </tr>
  
  <tr>
    <td>
      512 bit
    </td>
    
    <td>
      8
    </td>
    
    <td>
      16
    </td>
  </tr>
</tbody>
</table>

---

#### 第 37 页：SIMD Vector Mode，必须理解

这页用图对比了 **SIMD mode** 和 **scalar mode**。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L10-11-Parallelism-12.webp)

标量模式：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

A

</mi>

<mo>

+

</mo>

<mi>

B

</mi>
</mrow>

<annotation encoding="application/x-tex">

A + B

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">



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
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0502em;">

B

</span>
</span>
</span>
</span>
</span>

一次只算一个。

SIMD 模式：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mo stretchy="false">

[

</mo>

<msub>
<mi>

A

</mi>

<mn>

7

</mn>
</msub>

<mo separator="true">

,

</mo>

<msub>
<mi>

A

</mi>

<mn>

6

</mn>
</msub>

<mo separator="true">

,

</mo>

<mo>

…

</mo>

<mo separator="true">

,

</mo>

<msub>
<mi>

A

</mi>

<mn>

0

</mn>
</msub>

<mo stretchy="false">

]

</mo>

<mo>

+

</mo>

<mo stretchy="false">

[

</mo>

<msub>
<mi>

B

</mi>

<mn>

7

</mn>
</msub>

<mo separator="true">

,

</mo>

<msub>
<mi>

B

</mi>

<mn>

6

</mn>
</msub>

<mo separator="true">

,

</mo>

<mo>

…

</mo>

<mo separator="true">

,

</mo>

<msub>
<mi>

B

</mi>

<mn>

0

</mn>
</msub>

<mo stretchy="false">

]

</mo>
</mrow>

<annotation encoding="application/x-tex">

[A_7,A_6,\dots,A_0] + [B_7,B_6,\dots,B_0]

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mopen">

[

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

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



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

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="minner">

…

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mopen">

[

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0502em;">

B

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0502em;margin-right:0.05em;">
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
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0502em;margin-right:0.05em;">
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

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="minner">

…

</span>

<span className="mspace" style="margin-right:0.1667em;">



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
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0502em;margin-right:0.05em;">
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

<span className="mclose">

]

</span>
</span>
</span>
</span>
</span>

结果是：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mo stretchy="false">

[

</mo>

<msub>
<mi>

A

</mi>

<mn>

7

</mn>
</msub>

<mo>

+

</mo>

<msub>
<mi>

B

</mi>

<mn>

7

</mn>
</msub>

<mo separator="true">

,

</mo>

<msub>
<mi>

A

</mi>

<mn>

6

</mn>
</msub>

<mo>

+

</mo>

<msub>
<mi>

B

</mi>

<mn>

6

</mn>
</msub>

<mo separator="true">

,

</mo>

<mo>

…

</mo>

<mo separator="true">

,

</mo>

<msub>
<mi>

A

</mi>

<mn>

0

</mn>
</msub>

<mo>

+

</mo>

<msub>
<mi>

B

</mi>

<mn>

0

</mn>
</msub>

<mo stretchy="false">

]

</mo>
</mrow>

<annotation encoding="application/x-tex">

[A_7+B_7, A_6+B_6, \dots, A_0+B_0]

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mopen">

[

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

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0502em;">

B

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0502em;margin-right:0.05em;">
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

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



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

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0502em;">

B

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0502em;margin-right:0.05em;">
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

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="minner">

…

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



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
<span className="mord,mathnormal" style="margin-right:0.0502em;">

B

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0502em;margin-right:0.05em;">
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

<span className="mclose">

]

</span>
</span>
</span>
</span>
</span>

也就是说，**每个 lane 独立做同一种操作**。

这里有个关键词：**lane**。
一个 SIMD 向量可以看成多条 lane，每条 lane 存一个数据元素。SIMD 指令会对每条 lane 做同样的运算。

> SIMD 的本质是一条指令控制多个数据通道，每个通道执行相同操作，从而利用数据级并行。

---

### 第 38–42 页：为什么用 Intrinsics

#### 第 38 页：问题：编译器不一定能自动生成 SIMD

课件说，大部分编译器不能总是自动生成很好的 SIMD 代码。原因是编译器需要确认很多事情：

- 循环之间有没有数据依赖；
- 指针是否别名 alias；
- 内存是否对齐；
- 分支是否规则；
- 数据访问是否连续。

所以有时需要程序员直接写 SIMD 代码。

直接写汇编太痛苦，x86 指令太多，所以课件引出一个折中方案：

<mark>

用 C 的 intrinsics 直接访问 SIMD 寄存器和指令。

</mark>



> Intrinsics 可以理解成“长得像 C 函数的汇编指令包装器”。
> 它比汇编好写，但仍然非常接近硬件。

---

#### 第 39 页：AVX 数据类型，重要

课件列了一些 AVX intrinsic 类型：

<table>
<thead>
  <tr>
    <th>
      类型
    </th>
    
    <th>
      含义
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      <code code="__m256">
        __m256
      </code>
    </td>
    
    <td>
      256-bit，8 个 single-precision float
    </td>
  </tr>
  
  <tr>
    <td>
      <code code="__m256d">
        __m256d
      </code>
    </td>
    
    <td>
      256-bit，4 个 double
    </td>
  </tr>
  
  <tr>
    <td>
      <code code="__m256i">
        __m256i
      </code>
    </td>
    
    <td>
      256-bit 整数向量
    </td>
  </tr>
  
  <tr>
    <td>
      <code code="__m128">
        __m128
      </code>
    </td>
    
    <td>
      128-bit float 向量
    </td>
  </tr>
  
  <tr>
    <td>
      <code code="__m128d">
        __m128d
      </code>
    </td>
    
    <td>
      128-bit double 向量
    </td>
  </tr>
</tbody>
</table>

这里最重要的是：

```c
__m256d
```

它表示一个 256-bit 的向量寄存器，可以装 **4 个 double**。

后面矩阵乘法里会用它一次计算 4 个 double 的乘加。

---

#### 第 40–41 页：AVX 命名法和 _mm256_mul_pd

第 40 页讲命名法，不用全背，但几个后缀要看懂：

<table>
<thead>
  <tr>
    <th>
      标记
    </th>
    
    <th>
      含义
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      <code code="s">
        s
      </code>
      
       / <code code="d">
        d
      </code>
    </td>
    
    <td>
      single / double
    </td>
  </tr>
  
  <tr>
    <td>
      <code code="ps">
        ps
      </code>
    </td>
    
    <td>
      packed single，即多个 float
    </td>
  </tr>
  
  <tr>
    <td>
      <code code="pd">
        pd
      </code>
    </td>
    
    <td>
      packed double，即多个 double
    </td>
  </tr>
  
  <tr>
    <td>
      <code code="sd">
        sd
      </code>
    </td>
    
    <td>
      scalar double，即单个 double
    </td>
  </tr>
  
  <tr>
    <td>
      <code code="256">
        256
      </code>
    </td>
    
    <td>
      256-bit AVX
    </td>
  </tr>
  
  <tr>
    <td>
      <code code="i">
        i
      </code>
    </td>
    
    <td>
      integer
    </td>
  </tr>
</tbody>
</table>

比如：

```c
_mm256_mul_pd(a, b)
```

可以拆开看：

- `_mm`：Intel intrinsic；
- `256`：操作 256-bit 向量；
- `mul`：乘法；
- `pd`：packed double。

所以它的意思是：
**对两个 256-bit double 向量做逐元素乘法。**

如果 `a` 和 `b` 各有 4 个 double：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

a

</mi>

<mo>

=

</mo>

<mo stretchy="false">

[

</mo>

<msub>
<mi>

a

</mi>

<mn>

0

</mn>
</msub>

<mo separator="true">

,

</mo>

<msub>
<mi>

a

</mi>

<mn>

1

</mn>
</msub>

<mo separator="true">

,

</mo>

<msub>
<mi>

a

</mi>

<mn>

2

</mn>
</msub>

<mo separator="true">

,

</mo>

<msub>
<mi>

a

</mi>

<mn>

3

</mn>
</msub>

<mo stretchy="false">

]

</mo>
</mrow>

<annotation encoding="application/x-tex">

a=[a_0,a_1,a_2,a_3]

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.4306em;">



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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mopen">

[

</span>

<span className="mord">
<span className="mord,mathnormal">

a

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

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

a

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

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

a

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

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

a

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

<span className="mclose">

]

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
<mi>

b

</mi>

<mo>

=

</mo>

<mo stretchy="false">

[

</mo>

<msub>
<mi>

b

</mi>

<mn>

0

</mn>
</msub>

<mo separator="true">

,

</mo>

<msub>
<mi>

b

</mi>

<mn>

1

</mn>
</msub>

<mo separator="true">

,

</mo>

<msub>
<mi>

b

</mi>

<mn>

2

</mn>
</msub>

<mo separator="true">

,

</mo>

<msub>
<mi>

b

</mi>

<mn>

3

</mn>
</msub>

<mo stretchy="false">

]

</mo>
</mrow>

<annotation encoding="application/x-tex">

b=[b_0,b_1,b_2,b_3]

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

[

</span>

<span className="mord">
<span className="mord,mathnormal">

b

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

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

b

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

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

b

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

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

b

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

<span className="mclose">

]

</span>
</span>
</span>
</span>
</span>

那么：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<msub>
<mrow>



</mrow>

<mi>

m

</mi>
</msub>

<mi>

m

</mi>

<msub>
<mn>

256

</mn>

<mi>

m

</mi>
</msub>

<mi>

u

</mi>

<msub>
<mi>

l

</mi>

<mi>

p

</mi>
</msub>

<mi>

d

</mi>

<mo stretchy="false">

(

</mo>

<mi>

a

</mi>

<mo separator="true">

,

</mo>

<mi>

b

</mi>

<mo stretchy="false">

)

</mo>

<mo>

=

</mo>

<mo stretchy="false">

[

</mo>

<msub>
<mi>

a

</mi>

<mn>

0

</mn>
</msub>

<msub>
<mi>

b

</mi>

<mn>

0

</mn>
</msub>

<mo separator="true">

,

</mo>

<msub>
<mi>

a

</mi>

<mn>

1

</mn>
</msub>

<msub>
<mi>

b

</mi>

<mn>

1

</mn>
</msub>

<mo separator="true">

,

</mo>

<msub>
<mi>

a

</mi>

<mn>

2

</mn>
</msub>

<msub>
<mi>

b

</mi>

<mn>

2

</mn>
</msub>

<mo separator="true">

,

</mo>

<msub>
<mi>

a

</mi>

<mn>

3

</mn>
</msub>

<msub>
<mi>

b

</mi>

<mn>

3

</mn>
</msub>

<mo stretchy="false">

]

</mo>
</mrow>

<annotation encoding="application/x-tex">

_mm256_mul_pd(a,b)=[a_0b_0,a_1b_1,a_2b_2,a_3b_3]

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.0361em;vertical-align:-0.2861em;">



</span>

<span className="mord">
<span>



</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

m

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

<span className="mord,mathnormal">

m

</span>

<span className="mord">

25

</span>

<span className="mord">
<span className="mord">

6

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

m

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

<span className="mord,mathnormal">

u

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0197em;margin-right:0.05em;">
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

<span className="mord,mathnormal">

d

</span>

<span className="mopen">

(

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord,mathnormal">

b

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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mopen">

[

</span>

<span className="mord">
<span className="mord,mathnormal">

a

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

<span className="mord">
<span className="mord,mathnormal">

b

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

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

a

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

b

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

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

a

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

b

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

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

a

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

b

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

<span className="mclose">

]

</span>
</span>
</span>
</span>
</span>

第 41 页还给出一个性能信息：`mul_pd` 一条指令可以做 **4 个并行乘法**，并且某些架构上吞吐率可以达到 **每周期 2 条指令，CPI = 0.5**。这个后面会用来算理论峰值。

---

#### 第 42 页：原始双精度吞吐量，重要

课件用 i7-5557U 算峰值：

<table>
<thead>
  <tr>
    <th>
      项
    </th>
    
    <th>
      值
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      时钟
    </td>
    
    <td>
      3.1 GHz
    </td>
  </tr>
  
  <tr>
    <td>
      每周期 <code code="mul_pd">
        mul_pd
      </code>
      
       指令数
    </td>
    
    <td>
      2
    </td>
  </tr>
  
  <tr>
    <td>
      每条指令并行 double 乘法数
    </td>
    
    <td>
      4
    </td>
  </tr>
  
  <tr>
    <td>
      峰值双精度 FLOPS
    </td>
    
    <td>
      24.8 GFLOPS
    </td>
  </tr>
</tbody>
</table>

计算方法是：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mn>

3.1

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

2

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

24.8

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

<annotation encoding="application/x-tex">

3.1 \times 10^9 \times 2 \times 4 = 24.8 \times 10^9

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.7278em;vertical-align:-0.0833em;">



</span>

<span className="mord">

3.1

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

1

</span>

<span className="mord">
<span className="mord">

0

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

9

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
<span className="strut" style="height:0.7278em;vertical-align:-0.0833em;">



</span>

<span className="mord">

2

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
<span className="strut" style="height:0.7278em;vertical-align:-0.0833em;">



</span>

<span className="mord">

24.8

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
<span className="strut" style="height:0.8641em;">



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
<span className="vlist" style="height:0.8641em;">
<span style="top:-3.113em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
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
</span>

所以峰值是：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mn>

24.8

</mn>

<mtext>



</mtext>

<mi>

G

</mi>

<mi>

F

</mi>

<mi>

L

</mi>

<mi>

O

</mi>

<mi>

P

</mi>

<mi>

S

</mi>
</mrow>

<annotation encoding="application/x-tex">

24.8\ GFLOPS

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord">

24.8

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

GF

</span>

<span className="mord,mathnormal">

L

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

O

</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="mord,mathnormal" style="margin-right:0.0576em;">

S

</span>
</span>
</span>
</span>
</span>

注意，<mark>

这只是理想上限

</mark>

。后面实际 dgemm 远低于这个数，说明限制性能的不只是浮点运算单元。

---

### 第 43–45 页：向量化矩阵乘法，重要

这几页开始把 SIMD 用到之前的矩阵乘法 dgemm 上。

#### 第 43–44 页：Vectorized Matrix Multiplication，必须懂

原来的 scalar dgemm 一次算一个 (<span className="katex">
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

i

</mi>

<mi>

j

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

C_{ij}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9694em;vertical-align:-0.2861em;">



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
</span>
</span>
</span>

)。
现在 AVX 一次能放 4 个 double，所以改成一次算 **4 个 C 元素**。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L10-11-Parallelism-13.webp)

课件里的外层循环变成：

```c
for (int i = 0; i < N; i += 4)
```

也就是 (i) 每次加 4。

核心思想是：一次计算：

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

<mrow>
<mi>

i

</mi>

<mo separator="true">

,

</mo>

<mi>

j

</mi>
</mrow>
</msub>

<mo separator="true">

,

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

<mo separator="true">

,

</mo>

<mi>

j

</mi>
</mrow>
</msub>

<mo separator="true">

,

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

2

</mn>

<mo separator="true">

,

</mo>

<mi>

j

</mi>
</mrow>
</msub>

<mo separator="true">

,

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

3

</mn>

<mo separator="true">

,

</mo>

<mi>

j

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

C_{i,j}, C_{i+1,j}, C_{i+2,j}, C_{i+3,j}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9694em;vertical-align:-0.2861em;">



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

<span className="mpunct,mtight">

,

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0572em;">

j

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

<span className="mpunct,mtight">

,

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0572em;">

j

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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

i

</span>

<span className="mbin,mtight">

+

</span>

<span className="mord,mtight">

2

</span>

<span className="mpunct,mtight">

,

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0572em;">

j

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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

i

</span>

<span className="mbin,mtight">

+

</span>

<span className="mord,mtight">

3

</span>

<span className="mpunct,mtight">

,

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0572em;">

j

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
</span>

也就是同一列 (j) 上连续 4 行的结果。

内层大致是：

```c
__m256d c0 = {0,0,0,0};

for (int k = 0; k < N; k++) {
    c0 = _mm256_add_pd(
            c0,
            _mm256_mul_pd(
                _mm256_load_pd(a + i + k*N),
                _mm256_broadcast_sd(b + k + j*N)
            )
         );
}

_mm256_store_pd(c + i + j*N, c0);
```

这里每个 intrinsic 的作用：

<table>
<thead>
  <tr>
    <th>
      代码
    </th>
    
    <th>
      含义
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      <code code="_mm256_load_pd(a+i+k*N)">
        _mm256_load_pd(a+i+k*N)
      </code>
    </td>
    
    <td>
      从 A 中连续加载 4 个 double
    </td>
  </tr>
  
  <tr>
    <td>
      <code code="_mm256_broadcast_sd(b+k+j*N)">
        _mm256_broadcast_sd(b+k+j*N)
      </code>
    </td>
    
    <td>
      把 B 的一个 double 复制成 4 份
    </td>
  </tr>
  
  <tr>
    <td>
      <code code="_mm256_mul_pd(...)">
        _mm256_mul_pd(...)
      </code>
    </td>
    
    <td>
      4 个 double 并行乘法
    </td>
  </tr>
  
  <tr>
    <td>
      <code code="_mm256_add_pd(...)">
        _mm256_add_pd(...)
      </code>
    </td>
    
    <td>
      4 个 double 并行加法
    </td>
  </tr>
  
  <tr>
    <td>
      <code code="_mm256_store_pd(...)">
        _mm256_store_pd(...)
      </code>
    </td>
    
    <td>
      把 4 个结果写回 C
    </td>
  </tr>
</tbody>
</table>

这个写法非常妙：
A 取的是一段连续的 4 个元素：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<msub>
<mi>

A

</mi>

<mrow>
<mi>

i

</mi>

<mo separator="true">

,

</mo>

<mi>

k

</mi>
</mrow>
</msub>

<mo separator="true">

,

</mo>

<msub>
<mi>

A

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

<mo separator="true">

,

</mo>

<mi>

k

</mi>
</mrow>
</msub>

<mo separator="true">

,

</mo>

<msub>
<mi>

A

</mi>

<mrow>
<mi>

i

</mi>

<mo>

+

</mo>

<mn>

2

</mn>

<mo separator="true">

,

</mo>

<mi>

k

</mi>
</mrow>
</msub>

<mo separator="true">

,

</mo>

<msub>
<mi>

A

</mi>

<mrow>
<mi>

i

</mi>

<mo>

+

</mo>

<mn>

3

</mn>

<mo separator="true">

,

</mo>

<mi>

k

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

A_{i,k}, A_{i+1,k}, A_{i+2,k}, A_{i+3,k}

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

A

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

i

</span>

<span className="mpunct,mtight">

,

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0315em;">

k

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

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

A

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

i

</span>

<span className="mbin,mtight">

+

</span>

<span className="mord,mtight">

1

</span>

<span className="mpunct,mtight">

,

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0315em;">

k

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

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

A

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

i

</span>

<span className="mbin,mtight">

+

</span>

<span className="mord,mtight">

2

</span>

<span className="mpunct,mtight">

,

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0315em;">

k

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

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

A

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

i

</span>

<span className="mbin,mtight">

+

</span>

<span className="mord,mtight">

3

</span>

<span className="mpunct,mtight">

,

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0315em;">

k

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
</span>

B 取的是一个标量：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<msub>
<mi>

B

</mi>

<mrow>
<mi>

k

</mi>

<mo separator="true">

,

</mo>

<mi>

j

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

B_{k,j}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9694em;vertical-align:-0.2861em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0502em;">

B

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.0502em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0315em;">

k

</span>

<span className="mpunct,mtight">

,

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0572em;">

j

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
</span>

然后广播成：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mo stretchy="false">

[

</mo>

<msub>
<mi>

B

</mi>

<mrow>
<mi>

k

</mi>

<mo separator="true">

,

</mo>

<mi>

j

</mi>
</mrow>
</msub>

<mo separator="true">

,

</mo>

<msub>
<mi>

B

</mi>

<mrow>
<mi>

k

</mi>

<mo separator="true">

,

</mo>

<mi>

j

</mi>
</mrow>
</msub>

<mo separator="true">

,

</mo>

<msub>
<mi>

B

</mi>

<mrow>
<mi>

k

</mi>

<mo separator="true">

,

</mo>

<mi>

j

</mi>
</mrow>
</msub>

<mo separator="true">

,

</mo>

<msub>
<mi>

B

</mi>

<mrow>
<mi>

k

</mi>

<mo separator="true">

,

</mo>

<mi>

j

</mi>
</mrow>
</msub>

<mo stretchy="false">

]

</mo>
</mrow>

<annotation encoding="application/x-tex">

[B_{k,j},B_{k,j},B_{k,j},B_{k,j}]

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.0361em;vertical-align:-0.2861em;">



</span>

<span className="mopen">

[

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0502em;">

B

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.0502em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0315em;">

k

</span>

<span className="mpunct,mtight">

,

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0572em;">

j

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

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0502em;">

B

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.0502em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0315em;">

k

</span>

<span className="mpunct,mtight">

,

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0572em;">

j

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

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0502em;">

B

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.0502em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0315em;">

k

</span>

<span className="mpunct,mtight">

,

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0572em;">

j

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

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0502em;">

B

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.0502em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0315em;">

k

</span>

<span className="mpunct,mtight">

,

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0572em;">

j

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

]

</span>
</span>
</span>
</span>
</span>

再相乘，相当于一次更新 4 个 C 元素：

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

<mrow>
<mi>

i

</mi>

<mo>

:

</mo>

<mi>

i

</mi>

<mo>

+

</mo>

<mn>

3

</mn>

<mo separator="true">

,

</mo>

<mi>

j

</mi>
</mrow>
</msub>

<mo>

+

</mo>

<mo>

=

</mo>

<msub>
<mi>

A

</mi>

<mrow>
<mi>

i

</mi>

<mo>

:

</mo>

<mi>

i

</mi>

<mo>

+

</mo>

<mn>

3

</mn>

<mo separator="true">

,

</mo>

<mi>

k

</mi>
</mrow>
</msub>

<mo>

×

</mo>

<msub>
<mi>

B

</mi>

<mrow>
<mi>

k

</mi>

<mo separator="true">

,

</mo>

<mi>

j

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

C_{i:i+3,j} += A_{i:i+3,k} \times B_{k,j}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9694em;vertical-align:-0.2861em;">



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

<span className="mrel,mtight">

:

</span>

<span className="mord,mathnormal,mtight">

i

</span>

<span className="mbin,mtight">

+

</span>

<span className="mord,mtight">

3

</span>

<span className="mpunct,mtight">

,

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0572em;">

j

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

<span className="mord">

+

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
<span className="mord,mathnormal">

A

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

i

</span>

<span className="mrel,mtight">

:

</span>

<span className="mord,mathnormal,mtight">

i

</span>

<span className="mbin,mtight">

+

</span>

<span className="mord,mtight">

3

</span>

<span className="mpunct,mtight">

,

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0315em;">

k

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

×

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.9694em;vertical-align:-0.2861em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0502em;">

B

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.0502em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0315em;">

k

</span>

<span className="mpunct,mtight">

,

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0572em;">

j

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
</span>

> 也就是把A的前四行和B的第一列，先一起乘加运算之后得到前四个C

这就是 SIMD 在矩阵乘法里的典型用法。

---

#### 第 45 页：向量化性能，重要

课件给出性能表：

<table>
<thead>
  <tr>
    <th>
      N
    </th>
    
    <th>
      scalar
    </th>
    
    <th>
      AVX
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      32
    </td>
    
    <td>
      1.30
    </td>
    
    <td>
      4.56
    </td>
  </tr>
  
  <tr>
    <td>
      160
    </td>
    
    <td>
      1.30
    </td>
    
    <td>
      5.47
    </td>
  </tr>
  
  <tr>
    <td>
      480
    </td>
    
    <td>
      1.32
    </td>
    
    <td>
      5.27
    </td>
  </tr>
  
  <tr>
    <td>
      960
    </td>
    
    <td>
      0.91
    </td>
    
    <td>
      3.64
    </td>
  </tr>
</tbody>
</table>

单位是 GFLOPS。

可以看到 AVX 大约带来 <mark>

**4 倍左右加速**

</mark>

。这很合理，因为 AVX-256 一次能处理 4 个 double。

但问题来了：理论峰值是 **24.8 GFLOPS**，实际 AVX 只有 3.6–5.5 GFLOPS。
所以第 45 页的结论是：

> SIMD 已经让程序变快了，但还远没榨干硬件。

这就引出后面的两个瓶颈：<mark>

**流水线冒险**

</mark>

<mark>

和

</mark>

<mark>

**内存层次结构**

</mark>

<mark>

。

</mark>



---

### 第 46–49 页：流水线冒险与循环展开，重点

#### 第 46–47 页：为什么没到 25 GFLOPS

第 46 页直接问：为什么没有接近 25 GFLOPS？

可能原因：

- cache；
- hazard，流水线冒险。

第 47 页用 intrinsic guide 里的 `mul_pd` 信息暗示一个点：<mark>

浮点指令有

</mark>

 <mark>

**latency**

</mark>

 <mark>

和

</mark>

 <mark>

**throughput**

</mark>

。

这两个词很关键：

<table>
<thead>
  <tr>
    <th>
      概念
    </th>
    
    <th>
      含义
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      latency
    </td>
    
    <td>
      一条指令从开始到结果可用要等多少周期
    </td>
  </tr>
  
  <tr>
    <td>
      throughput
    </td>
    
    <td>
      流水线稳定后，每周期最多能发射/完成多少条
    </td>
  </tr>
</tbody>
</table>

比如 `mul_pd` latency 是 5，throughput 可以很好。
这意味着：**单条乘法结果要 5 个周期后才能用，但如果有足够多互不依赖的乘法，流水线可以不断塞满。**

问题是 dgemm 里有这种依赖：

```c
c0 = c0 + something;
c0 = c0 + something_else;
c0 = c0 + ...
```

每次都依赖上一次的 `c0`，这叫 **loop-carried dependency**，也就是<mark>

循环携带依赖

</mark>

。
下一次加法要等上一次 `c0` 算完，所以流水线容易空转。

---

#### 第 48 页：<mark>Loop Unrolling</mark>

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L10-11-Parallelism-14.webp)

循环展开的核心目的：

> 制造多个独立的累加器，减少对同一个 `c0` 的连续依赖，让流水线有活干。

课件中 `UNROLL = 4` （4-way 展开通常是一个比较温和的折中），并使用：

```c
__m256d c[4];
```

也就是 <mark>

4 个向量寄存器同时累加

</mark>

。

可以把原来的：

```c
c0 += ...
c0 += ...
c0 += ...
```

变成类似：

```c
c0 += ...
c1 += ...
c2 += ...
c3 += ...
```

<mark>

这样

</mark>

 <mark>

`c0、c1、c2、c3`

</mark>

 <mark>

之间互不依赖，CPU 可以把它们穿插执行，隐藏 latency。（类似流水线思想）

</mark>



这就是循环展开的本质：

> 不是减少总计算量，而是改变指令依赖结构，提高流水线利用率。

第 48 页还问“如何验证生成的代码实际上是展开的？”
答案一般是看编译器生成的汇编代码，检查循环体是否出现多个独立累加寄存器/多组重复指令。

---

#### 第 49 页：循环展开性能，重要

课件性能表：

<table>
<thead>
  <tr>
    <th>
      N
    </th>
    
    <th>
      scalar
    </th>
    
    <th>
      AVX
    </th>
    
    <th>
      unroll
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      32
    </td>
    
    <td>
      1.30
    </td>
    
    <td>
      4.56
    </td>
    
    <td>
      12.95
    </td>
  </tr>
  
  <tr>
    <td>
      160
    </td>
    
    <td>
      1.30
    </td>
    
    <td>
      5.47
    </td>
    
    <td>
      19.70
    </td>
  </tr>
  
  <tr>
    <td>
      480
    </td>
    
    <td>
      1.32
    </td>
    
    <td>
      5.27
    </td>
    
    <td>
      14.50
    </td>
  </tr>
  
  <tr>
    <td>
      960
    </td>
    
    <td>
      0.91
    </td>
    
    <td>
      3.64
    </td>
    
    <td>
      6.91
    </td>
  </tr>
</tbody>
</table>

可以看出 unroll 后性能大幅提升，尤其 (N=160) 时到 **19.70 GFLOPS**，已经接近 24.8 GFLOPS 的理论峰值。

但 (N=960) 时只有 **6.91 GFLOPS**，又掉下来了。

这说明：
<mark>

小/中等矩阵时，主要瓶颈可能是流水线利用率

</mark>

；
<mark>

大矩阵时，主要瓶颈逐渐变成

</mark>

 <mark>

**cache/memory**

</mark>

。

---

### 第 50–55 页：内存访问与 Blocking（缓存分块）

这几页是性能优化的第二个核心：**不是算得不够快，而是数据喂不够快。**

#### 第 50 页：FPU vs Memory Access，重要

课件先做了一个理想分析。

矩阵乘法浮点运算数：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

F

</mi>

<mo>

=

</mo>

<mn>

2

</mn>

<msup>
<mi>

N

</mi>

<mn>

3

</mn>
</msup>
</mrow>

<annotation encoding="application/x-tex">

F = 2N^3

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

F

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

2

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.109em;">

N

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

3

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

因为有 (N^3) 次乘法和 (N^3) 次加法。

如果<mark>

理想情况下

</mark>

 A、B、C 每个元素只从内存访问一次，那么内存访问量大约是：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

M

</mi>

<mo>

=

</mo>

<mn>

3

</mn>

<msup>
<mi>

N

</mi>

<mn>

2

</mn>
</msup>
</mrow>

<annotation encoding="application/x-tex">

M = 3N^2

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

3

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.109em;">

N

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
</span>
</span>
</span>
</span>

于是运算访存比：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

q

</mi>

<mo>

=

</mo>

<mfrac>
<mi>

F

</mi>

<mi>

M

</mi>
</mfrac>

<mo>

=

</mo>

<mfrac>
<mrow>
<mn>

2

</mn>

<msup>
<mi>

N

</mi>

<mn>

3

</mn>
</msup>
</mrow>

<mrow>
<mn>

3

</mn>

<msup>
<mi>

N

</mi>

<mn>

2

</mn>
</msup>
</mrow>
</mfrac>

<mo>

=

</mo>

<mfrac>
<mn>

2

</mn>

<mn>

3

</mn>
</mfrac>

<mi>

N

</mi>
</mrow>

<annotation encoding="application/x-tex">

q = \frac{F}{M} = \frac{2N^3}{3N^2} = \frac{2}{3}N

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.625em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

q

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
<span className="mord,mathnormal" style="margin-right:0.1389em;">

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

3

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.109em;">

N

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

2

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.109em;">

N

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

3

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

3

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

<span className="mord,mathnormal" style="margin-right:0.109em;">

N

</span>
</span>
</span>
</span>
</span>

这个 (q) 越大越好，表示每次内存访问能换来很多计算。

按这个理想模型，矩阵越大，(q) 越大，应该越适合高速计算。
但现实马上打脸。

---

#### 第 51 页：但是内存被反复访问，必须懂

第 51 页指出，在实际内层循环里：

```c
for (int k = 0; k < N; k++) {
    c0 = c0 + load(A) * broadcast(B);
}
```

每次循环大致有：

- 2 个浮点操作：乘法 + 加法；
- 2 个加载：加载 A，加载 B。

所以：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

q

</mi>

<mo>

=

</mo>

<mi>

F

</mi>

<mi mathvariant="normal">

/

</mi>

<mi>

M

</mi>

<mo>

≈

</mo>

<mn>

1

</mn>
</mrow>

<annotation encoding="application/x-tex">

q = F/M \approx 1

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.625em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

q

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

<span className="mord,mathnormal" style="margin-right:0.1389em;">

F

</span>

<span className="mord">

/

</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

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

1

</span>
</span>
</span>
</span>
</span>

也就是说，实际代码没有达到理想的 (<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mfrac>
<mn>

2

</mn>

<mn>

3

</mn>
</mfrac>

<mi>

N

</mi>
</mrow>

<annotation encoding="application/x-tex">

\frac{2}{3}N

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.1901em;vertical-align:-0.345em;">



</span>

<span className="mord">
<span className="mopen,nulldelimiter">



</span>

<span className="mfrac">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.8451em;">
<span style="top:-2.655em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">

3

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

<span className="mord,mathnormal" style="margin-right:0.109em;">

N

</span>
</span>
</span>
</span>

)，因为 A、B 的元素被反复从内存层次中取出来，<mark>

数据复用没有做好

</mark>

。

> 理论上矩阵乘法计算密度很高，但朴素实现会重复访存，导致实际性能受内存层次限制。

---

#### 第 52 页：存储器层次结构，重要

课件展示了典型存储器层次：

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L10-11-Parallelism-15.webp)

<table>
<thead>
  <tr>
    <th>
      层次
    </th>
    
    <th>
      速度
    </th>
    
    <th>
      容量
    </th>
    
    <th>
      单 bit 成本
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      register/cache
    </td>
    
    <td>
      快
    </td>
    
    <td>
      小
    </td>
    
    <td>
      高
    </td>
  </tr>
  
  <tr>
    <td>
      DRAM
    </td>
    
    <td>
      慢
    </td>
    
    <td>
      大
    </td>
    
    <td>
      低
    </td>
  </tr>
  
  <tr>
    <td>
      disk/flash
    </td>
    
    <td>
      极慢
    </td>
    
    <td>
      很大
    </td>
    
    <td>
      更低
    </td>
  </tr>
</tbody>
</table>

优化矩阵乘法的关键就是：

> 让经常重复使用的数据尽量待在 register/cache 里，而不是每次都去 DRAM 拿。

这就是 blocking 的动机。

---

#### 第 53–54 页：Blocking

第 53 页给出 blocking 的定义：

> 重新排列代码，使已经加载到 cache 里的值被多次使用，从而减少慢速 DRAM 访问。

普通矩阵乘法像是：

```c
for i
  for j
    for k
      C[i][j] += A[i][k] * B[k][j];
```

blocking 的思路是不要一次看整个矩阵，而是<mark>

分成小块

</mark>

：

```c
for sj in blocks
  for si in blocks
    for sk in blocks
      do_block(si, sj, sk);
```

每次处理一个小块，<mark>

让 A 的一小块、B 的一小块、C 的一小块尽量留在 cache 里。

</mark>



---

#### 第 55 页：Blocking 性能，重要

课件性能表：

<table>
<thead>
  <tr>
    <th>
      N
    </th>
    
    <th>
      scalar
    </th>
    
    <th>
      AVX
    </th>
    
    <th>
      unroll
    </th>
    
    <th>
      blocking
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      32
    </td>
    
    <td>
      1.30
    </td>
    
    <td>
      4.56
    </td>
    
    <td>
      12.95
    </td>
    
    <td>
      13.80
    </td>
  </tr>
  
  <tr>
    <td>
      160
    </td>
    
    <td>
      1.30
    </td>
    
    <td>
      5.47
    </td>
    
    <td>
      19.70
    </td>
    
    <td>
      21.79
    </td>
  </tr>
  
  <tr>
    <td>
      480
    </td>
    
    <td>
      1.32
    </td>
    
    <td>
      5.27
    </td>
    
    <td>
      14.50
    </td>
    
    <td>
      20.17
    </td>
  </tr>
  
  <tr>
    <td>
      960
    </td>
    
    <td>
      0.91
    </td>
    
    <td>
      3.64
    </td>
    
    <td>
      6.91
    </td>
    
    <td>
      15.82
    </td>
  </tr>
</tbody>
</table>

非常关键的观察：

- <mark>

对小矩阵，blocking 提升不算特别夸张，因为本来就可能放得进 cache

</mark>

；
- <mark>

对大矩阵，blocking 提升明显，(N=960) 从 unroll 的 6.91 提升到 15.82

</mark>

；
- 说明大矩阵的主要瓶颈是内存层次，而不是浮点硬件本身。

所以这个模块的优化路线可以总结成：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

s

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

a

</mi>

<mi>

r

</mi>

<mo>

→

</mo>

<mi>

A

</mi>

<mi>

V

</mi>

<mi>

X

</mi>

<mo>

→

</mo>

<mi>

l

</mi>

<mi>

o

</mi>

<mi>

o

</mi>

<mi>

p

</mi>

<mtext>



</mtext>

<mi>

u

</mi>

<mi>

n

</mi>

<mi>

r

</mi>

<mi>

o

</mi>

<mi>

l

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

g

</mi>

<mo>

→

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

<mi>

i

</mi>

<mi>

n

</mi>

<mi>

g

</mi>
</mrow>

<annotation encoding="application/x-tex">

scalar \rightarrow AVX \rightarrow loop\ unrolling \rightarrow blocking

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,mathnormal">

sc

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

a

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

<span className="mord,mathnormal">

A

</span>

<span className="mord,mathnormal" style="margin-right:0.2222em;">

V

</span>

<span className="mord,mathnormal" style="margin-right:0.0785em;">

X

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
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

oo

</span>

<span className="mord,mathnormal">

p

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal">

u

</span>

<span className="mord,mathnormal">

n

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal">

o

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

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

→

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



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

in

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

g

</span>
</span>
</span>
</span>
</span>

分别解决：

<table>
<thead>
  <tr>
    <th>
      优化
    </th>
    
    <th>
      解决的问题
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      AVX
    </td>
    
    <td>
      一条指令处理多个数据
    </td>
  </tr>
  
  <tr>
    <td>
      loop unrolling（流水线优化）
    </td>
    
    <td>
      缓解流水线依赖，提高指令吞吐
    </td>
  </tr>
  
  <tr>
    <td>
      blocking（缓存分块）
    </td>
    
    <td>
      增强 cache 复用，减少 DRAM 访问
    </td>
  </tr>
</tbody>
</table>

---

### 第 56–59 页：GEMM 的真实高性能实现，略中带重点

最后讲 **GEMM**，想把前面 SIMD、AVX、loop unrolling、blocking 这些零散优化串成一个完整故事

#### 第 56 页：GEMM 和阻塞算法

GEMM 是：

> General Matrix-Matrix Multiplication，一般矩阵-矩阵乘法。

形式通常是：

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

:

</mo>

<mo>

=

</mo>

<mi>

C

</mi>

<mo>

+

</mo>

<mi>

A

</mi>

<mo>

×

</mo>

<mi>

B

</mi>
</mrow>

<annotation encoding="application/x-tex">

C := C + A \times B

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

:=

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

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



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

课件提到阻塞算法变体，最快的通用实现来自类似 GotoBLAS 这样的高性能库。

这里要抓住一句话：

> 真正高性能的 GEMM 不是简单三层循环，而是围绕存储器层次做多级 blocking。

---

#### 第 57–58 页：多级存储器层次 + GEMM 循环

第 57 页的图说明了优化 GEMM 会把数据分层处理：

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L10-11-Parallelism-16.webp)

- 主存里有完整 A、B、C；
- cache / shared memory 里放 packed A、packed B；
- register 里放正在计算的小块；
- 微内核 micro-kernel 负责最核心的小矩阵计算。

第 58 页展示了 GEMM 的多层循环。大概可以理解成：

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L10-11-Parallelism-17.webp)

<table>
<thead>
  <tr>
    <th>
      层次
    </th>
    
    <th>
      目标
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      外层 blocking
    </td>
    
    <td>
      让数据适配 L3 cache
    </td>
  </tr>
  
  <tr>
    <td>
      中层 blocking
    </td>
    
    <td>
      让数据适配 L2 cache
    </td>
  </tr>
  
  <tr>
    <td>
      内层 blocking
    </td>
    
    <td>
      让数据适配 L1 cache
    </td>
  </tr>
  
  <tr>
    <td>
      micro-kernel
    </td>
    
    <td>
      让数据适配 registers
    </td>
  </tr>
</tbody>
</table>

> 高性能 GEMM 会针对 register、L1、L2、L3 分别设计块大小，使数据在每一层都尽可能复用。

“packed A/B”的意思是把矩阵块重新排列成更连续、更适合 SIMD 加载的形式。代价是多一次打包，但收益是后续计算更快、cache 更友好。

---

#### 第 59 页：Micro-Kernel

第 59 页展示 micro-kernel 计算。核心是：
一次不是只算一个 (<span className="katex">
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

i

</mi>

<mi>

j

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

C_{ij}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9694em;vertical-align:-0.2861em;">



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
</span>
</span>
</span>

)，而是算一个小块 (<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

M

</mi>

<mi>

R

</mi>
</msub>

<mo>

×

</mo>

<msub>
<mi>

N

</mi>

<mi>

R

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

M_R \times N_R

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0077em;">

R

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

×

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.109em;">

N

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0077em;">

R

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

) 的 C。

比如一次算 (<span className="katex">
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

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

4 \times 4)

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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord">

4

</span>

<span className="mclose">

)

</span>
</span>
</span>
</span>

 的 C 小块。
A 提供一列/一小块，B 提供一行/一小块，然后做 outer product 更新整个 C 小块。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L10-11-Parallelism-18.webp)

下一页是详细解读

---

### 第 60 页：标量点积 vs 分块外积，重点，非常可能考

这一页很有价值，它回答：

> 为什么 GEMM 微内核要算 (<span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msub>
> <mi>
> 
> M
> 
> </mi>
> 
> <mi>
> 
> R
> 
> </mi>
> </msub>
> 
> <mo>
> 
> ×
> 
> </mo>
> 
> <msub>
> <mi>
> 
> N
> 
> </mi>
> 
> <mi>
> 
> R
> 
> </mi>
> </msub>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> M_R \times N_R
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
> <span className="mord,mathnormal" style="margin-right:0.109em;">
> 
> M
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3283em;">
> <span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mathnormal,mtight" style="margin-right:0.0077em;">
> 
> R
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
> <span className="strut" style="height:0.8333em;vertical-align:-0.15em;">
> 
> 
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
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3283em;">
> <span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mathnormal,mtight" style="margin-right:0.0077em;">
> 
> R
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
> ) 的小块，而不是简单算一个标量点积？

#### 标量点积：一次只算一个 C 元素

比如算：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<msub>
<mi>

γ

</mi>

<mn>

00

</mn>
</msub>

<mo>

=

</mo>

<munderover>
<mo>

∑

</mo>

<mrow>
<mi>

k

</mi>

<mo>

=

</mo>

<mn>

0

</mn>
</mrow>

<mrow>
<msub>
<mi>

K

</mi>

<mi>

C

</mi>
</msub>

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

α

</mi>

<mi>

k

</mi>
</msub>

<msub>
<mi>

β

</mi>

<mi>

k

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

\gamma_{00} = \sum_{k=0}^{K_C-1} \alpha_k \beta_k

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.625em;vertical-align:-0.1944em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0556em;">

γ

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0556em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">

00

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
<span className="strut" style="height:3.1418em;vertical-align:-1.3021em;">



</span>

<span className="mop,op-limits">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:1.8396em;">
<span style="top:-1.8479em;margin-left:0em;">
<span className="pstrut" style="height:3.05em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0315em;">

k

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

<span style="top:-4.3113em;margin-left:0em;">
<span className="pstrut" style="height:3.05em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0715em;">

K

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3448em;">
<span style="top:-2.3567em;margin-left:-0.0715em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0715em;">

C

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.1433em;">
<span>



</span>
</span>
</span>
</span>
</span>
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
<span className="vlist" style="height:1.3021em;">
<span>



</span>
</span>
</span>
</span>
</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0037em;">

α

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.0037em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0315em;">

k

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
<span className="mord,mathnormal" style="margin-right:0.0528em;">

β

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.0528em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0315em;">

k

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

乘加次数：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mn>

2

</mn>

<msub>
<mi>

K

</mi>

<mi>

C

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

2K_C

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">

2

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0715em;">

K

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0715em;">

C

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

读取次数大约：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<msub>
<mi>

K

</mi>

<mi>

C

</mi>
</msub>

<mo>

+

</mo>

<msub>
<mi>

K

</mi>

<mi>

C

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

K_C + K_C

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

K

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0715em;">

C

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
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0715em;">

K

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0715em;">

C

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

再加上 C 的读写 2 次，所以运算访存比大约：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mfrac>
<mrow>
<mn>

2

</mn>

<msub>
<mi>

K

</mi>

<mi>

C

</mi>
</msub>
</mrow>

<mrow>
<mn>

2

</mn>

<msub>
<mi>

K

</mi>

<mi>

C

</mi>
</msub>

<mo>

+

</mo>

<mn>

2

</mn>
</mrow>
</mfrac>

<mo>

≈

</mo>

<mn>

1

</mn>
</mrow>

<annotation encoding="application/x-tex">

\frac{2K_C}{2K_C+2} \approx 1

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
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
<span className="mord">

2

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0715em;">

K

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0715em;">

C

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

2

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0715em;">

K

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0715em;">

C

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

1

</span>
</span>
</span>
</span>
</span>

也就是每次访存换来的计算不多。

---

#### 分块外积：一次算 (<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

M

</mi>

<mi>

R

</mi>
</msub>

<mo>

×

</mo>

<msub>
<mi>

N

</mi>

<mi>

R

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

M_R \times N_R

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0077em;">

R

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

×

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.109em;">

N

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0077em;">

R

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

) 个 C 元素

分块外积一次更新一个 C 小块，比如 (<span className="katex">
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
</mrow>

<annotation encoding="application/x-tex">

4 \times 4

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
</span>
</span>
</span>

)。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L10-11-Parallelism-19.webp)

计算量：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mn>

2

</mn>

<msub>
<mi>

M

</mi>

<mi>

R

</mi>
</msub>

<msub>
<mi>

N

</mi>

<mi>

R

</mi>
</msub>

<msub>
<mi>

K

</mi>

<mi>

C

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

2M_RN_RK_C

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">

2

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0077em;">

R

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
<span className="mord,mathnormal" style="margin-right:0.109em;">

N

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0077em;">

R

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
<span className="mord,mathnormal" style="margin-right:0.0715em;">

K

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0715em;">

C

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

访存量大约：

<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mo stretchy="false">

(

</mo>

<msub>
<mi>

M

</mi>

<mi>

R

</mi>
</msub>

<mo>

+

</mo>

<msub>
<mi>

N

</mi>

<mi>

R

</mi>
</msub>

<mo stretchy="false">

)

</mo>

<msub>
<mi>

K

</mi>

<mi>

C

</mi>
</msub>

<mo>

+

</mo>

<mn>

2

</mn>

<msub>
<mi>

M

</mi>

<mi>

R

</mi>
</msub>

<msub>
<mi>

N

</mi>

<mi>

R

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

(M_R + N_R)K_C + 2M_RN_R

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
<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0077em;">

R

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
<span className="mord,mathnormal" style="margin-right:0.109em;">

N

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0077em;">

R

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
<span className="mord,mathnormal" style="margin-right:0.0715em;">

K

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0715em;">

C

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
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">

2

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0077em;">

R

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
<span className="mord,mathnormal" style="margin-right:0.109em;">

N

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0077em;">

R

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

  （2的原因是读一次写一次）

所以运算访存比：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mfrac>
<mrow>
<mn>

2

</mn>

<msub>
<mi>

M

</mi>

<mi>

R

</mi>
</msub>

<msub>
<mi>

N

</mi>

<mi>

R

</mi>
</msub>

<msub>
<mi>

K

</mi>

<mi>

C

</mi>
</msub>
</mrow>

<mrow>
<mo stretchy="false">

(

</mo>

<msub>
<mi>

M

</mi>

<mi>

R

</mi>
</msub>

<mo>

+

</mo>

<msub>
<mi>

N

</mi>

<mi>

R

</mi>
</msub>

<mo stretchy="false">

)

</mo>

<msub>
<mi>

K

</mi>

<mi>

C

</mi>
</msub>

<mo>

+

</mo>

<mn>

2

</mn>

<msub>
<mi>

M

</mi>

<mi>

R

</mi>
</msub>

<msub>
<mi>

N

</mi>

<mi>

R

</mi>
</msub>
</mrow>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

\frac{2M_RN_RK_C}{(M_R+N_R)K_C + 2M_RN_R}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:2.2963em;vertical-align:-0.936em;">



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
<span className="mopen">

(

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0077em;">

R

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

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.109em;">

N

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0077em;">

R

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
<span className="mord,mathnormal" style="margin-right:0.0715em;">

K

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0715em;">

C

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

<span className="mord">

2

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0077em;">

R

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
<span className="mord,mathnormal" style="margin-right:0.109em;">

N

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0077em;">

R

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
<span className="mord">

2

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0077em;">

R

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
<span className="mord,mathnormal" style="margin-right:0.109em;">

N

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0077em;">

R

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
<span className="mord,mathnormal" style="margin-right:0.0715em;">

K

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0715em;">

C

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
<span className="vlist" style="height:0.936em;">
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

当 (<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

K

</mi>

<mi>

C

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

K_C

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

K

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0715em;">

C

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

) 比较大时，可以近似为：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mfrac>
<mrow>
<mn>

2

</mn>

<msub>
<mi>

M

</mi>

<mi>

R

</mi>
</msub>

<msub>
<mi>

N

</mi>

<mi>

R

</mi>
</msub>
</mrow>

<mrow>
<msub>
<mi>

M

</mi>

<mi>

R

</mi>
</msub>

<mo>

+

</mo>

<msub>
<mi>

N

</mi>

<mi>

R

</mi>
</msub>
</mrow>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

\frac{2M_RN_R}{M_R+N_R}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
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
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0077em;">

R

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

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.109em;">

N

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0077em;">

R

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
<span className="mord">

2

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0077em;">

R

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
<span className="mord,mathnormal" style="margin-right:0.109em;">

N

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0077em;">

R

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

如果 (<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

M

</mi>

<mi>

R

</mi>
</msub>

<mo>

=

</mo>

<msub>
<mi>

N

</mi>

<mi>

R

</mi>
</msub>

<mo>

=

</mo>

<mn>

4

</mn>
</mrow>

<annotation encoding="application/x-tex">

M_R=N_R=4

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0077em;">

R

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
<span className="mord,mathnormal" style="margin-right:0.109em;">

N

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0077em;">

R

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

4

</span>
</span>
</span>
</span>

)，那么：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
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

<mn>

4

</mn>

<mo>

×

</mo>

<mn>

4

</mn>
</mrow>

<mrow>
<mn>

4

</mn>

<mo>

+

</mo>

<mn>

4

</mn>
</mrow>
</mfrac>

<mo>

=

</mo>

<mn>

4

</mn>
</mrow>

<annotation encoding="application/x-tex">

\frac{2 \times 4 \times 4}{4+4} = 4

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:2.0908em;vertical-align:-0.7693em;">



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

4

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mord">

4

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

2

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

×

</span>

<span className="mspace" style="margin-right:0.2222em;">



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

<span className="mord">

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
<span className="strut" style="height:0.6444em;">



</span>

<span className="mord">

4

</span>
</span>
</span>
</span>
</span>

这比标量点积的约 1 好很多。

结论：

> 分块外积通过一次加载 A 和 B 的小块，更新多个 C 元素，提高了计算操作与内存操作的比率，也就是减少访存压力。

**为什么高性能 GEMM 使用 register blocking / outer product micro-kernel，而不是普通 dot product？**

可以答：

> 因为外积形式能复用加载到寄存器/cache 的 A、B 数据，一次更新多个 C 元素，提高 arithmetic intensity，减少慢速内存访问，从而更接近浮点硬件峰值性能。

---

## 第 3 模块：指令级并行 ILP

继续讲**下一板块：第 3 模块——指令级并行 ILP，约第 61–89 页**。

这一块比上一块 SIMD 更“体系结构味”。不用每个 IA-64 细节都死磕，考试重点主要是：

**ILP 是什么 → VLIW 是什么 → 编译器怎么调度 → loop unrolling / software pipelining → trace scheduling → 为什么 VLIW/Itanium 没成功。**

---

### 第 61–63 页：ILP 总览，重要

#### 第 61 页：标题页

进入 **Instruction Level Parallelism，指令级并行**。

> ILP 是在**同一个线程/程序内部**，让多条互不依赖的指令同时执行。

---

#### 第 62 页：ILP 的硬件/软件设计空间，略中带重要

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L10-11-Parallelism-20.webp)

谁来负责发现和利用指令之间的并行性？

大概有两条路线：

<table>
<thead>
  <tr>
    <th>
      路线
    </th>
    
    <th>
      谁负责找并行？
    </th>
    
    <th>
      代表
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      动态调度
    </td>
    
    <td>
      硬件运行时判断哪些指令能并行
    </td>
    
    <td>
      Superscalar，超标量
    </td>
  </tr>
  
  <tr>
    <td>
      静态调度
    </td>
    
    <td>
      编译器提前安排哪些操作并行
    </td>
    
    <td>
      VLIW
    </td>
  </tr>
</tbody>
</table>

这页不用背图，但要抓住一个核心对比：

> **超标量 Superscalar：硬件聪明。VLIW：编译器聪明。**

超标量处理器会在运行时检查依赖、乱序发射、动态调度。VLIW 则把并行性显式写进指令字里，硬件相对简单，但编译器压力巨大。

> 本章主要讲的是编译器角度的静态调度

---

#### 第 63 页：顺序 ISA 瓶颈（从超标量处理器的角度）

传统 ISA 是顺序机器代码：程序看起来是一条条指令排队执行。
但处理器内部其实想问：

> 有没有一些指令其实互不依赖，可以一起做？

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L10-11-Parallelism-21.webp)

第 63 页把流程分成两部分：

1. **Superscalar 编译器**：寻找独立运算、做操作调度；
2. **Superscalar processor**：运行时检查依赖关系、执行调度。

所以顺序 ISA 的问题是：机器码本身没有显式告诉硬件“这几条可以并行”，硬件需要自己猜、自己检查、自己调度，复杂度很高。

<alert type="tip">

超标量和 VLIW在ILP中 通常是 **二选一作为主要设计路线**

</alert>

---

### 第 64–66 页：VLIW，核心概念，必须掌握

#### 第 64 页：VLIW 是什么，最重要

<mark>

**VLIW = Very Long Instruction Word，超长指令字。**

</mark>



它的想法很直接：
把多个操作打包到一条很长的指令里，每个槽位对应一个固定功能单元。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L10-11-Parallelism-22.webp)

也就是说，一条 VLIW 指令里面可能同时包含多个操作。硬件看到这一整条长指令，就把里面的多个操作同时发给不同功能单元执行。课件强调 VLIW 会把多个操作打包到一条指令中，每个槽对应固定功能，并假设操作延迟是恒定的。

这和 superscalar 的区别非常关键：

<table>
<thead>
  <tr>
    <th>
      对比
    </th>
    
    <th>
      Superscalar
    </th>
    
    <th>
      VLIW
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      指令格式
    </td>
    
    <td>
      普通顺序指令
    </td>
    
    <td>
      一条长指令含多个操作
    </td>
  </tr>
  
  <tr>
    <td>
      并行性发现
    </td>
    
    <td>
      硬件运行时发现
    </td>
    
    <td>
      编译器提前安排
    </td>
  </tr>
  
  <tr>
    <td>
      硬件复杂度
    </td>
    
    <td>
      高
    </td>
    
    <td>
      相对低
    </td>
  </tr>
  
  <tr>
    <td>
      编译器压力
    </td>
    
    <td>
      较低
    </td>
    
    <td>
      很高
    </td>
  </tr>
  
  <tr>
    <td>
      依赖检查
    </td>
    
    <td>
      硬件做 RAW 等检查
    </td>
    
    <td>
      编译器保证安全
    </td>
  </tr>
</tbody>
</table>

VLIW编译器的压力大，VLIW 架构希望编译器已经安排好

- 指令内的并行度 → 没有交叉操作的RAW（read after write）检查
- 在数据准备好之前不使用数据 → 无数据联锁

---

#### 第 65 页：早期 VLIW 机器

这一页是历史背景：

- FPS AP120B；
- Multiflow Trace；
- Cydrome Cydra-5。

你只要知道：VLIW 不是 Intel Itanium 才出现的，它之前已经在科学计算、DSP、阵列处理器等场景尝试过。

其中 Cydra-5 的 **rotating register file，旋转寄存器文件** 后面 IA-64 还会讲。

---

#### 第 66 页：VLIW 编译器职责，重要

VLIW 的编译器要做三件事：

1. 调度操作，让并行执行最大化；
2. 保证同一条 VLIW 指令内部的操作确实能并行；
3. 避免数据冒险，必要时插入显式 `nop`。

这里的 `nop` 是 no operation，空操作。

比如一个结果要 4 个周期后才能用，但下一条马上要用它，编译器就得插入空槽或安排别的无关指令填进去。否则硬件不会像复杂超标量那样帮你兜底。

> VLIW 把动态调度压力从硬件转移到编译器，编译器必须静态发现并行性、安排功能单元、避免数据冒险和结构冒险。

---

### 第 67–71 页：循环展开与软件流水线，最重要

这几页是本模块最有价值的部分，建议认真看。

#### 第 67 页：普通循环执行，必须懂

例子：

```c
for (i = 0; i < N; i++)
    B[i] = A[i] + C;
```

编译后大概是：

```text
loop:
    fld  f1, 0(x1)      // load A[i]
    add  x1, 8          // A 指针加 8
    fadd f2, f0, f1     // A[i] + C
    fsd  f2, 0(x2)      // store B[i]
    add  x2, 8          // B 指针加 8
    bne  x1, x3, loop   // 判断循环
```

课件调度后给出的效果是：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mn>

1

</mn>

<mtext>

fadd

</mtext>

<mi mathvariant="normal">

/

</mi>

<mn>

8

</mn>

<mtext>

cycles

</mtext>

<mo>

=

</mo>

<mn>

0.125

</mn>
</mrow>

<annotation encoding="application/x-tex">

1 \text{ fadd} / 8 \text{ cycles} = 0.125

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord">

1

</span>

<span className="mord,text">
<span className="mord">

fadd

</span>
</span>

<span className="mord">

/8

</span>

<span className="mord,text">
<span className="mord">

cycles

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

0.125

</span>
</span>
</span>
</span>
</span>

也就是 8 个周期才完成 1 个浮点加法。
这很浪费，因为功能单元很多时候是空着的。

为什么浪费？因为单次循环里指令太少，load、fadd、store、branch 之间还有延迟和依赖，很难把所有功能单元填满。

---

#### 第 68 页：Loop Unrolling，循环展开

循环展开就是一次处理多个迭代。

原来：

```c
for (i = 0; i < N; i++)
    B[i] = A[i] + C;
```

4 路展开后：

```c
for (i = 0; i < N; i += 4) {
    B[i]   = A[i]   + C;
    B[i+1] = A[i+1] + C;
    B[i+2] = A[i+2] + C;
    B[i+3] = A[i+3] + C;
}
```

这和上一模块的 loop unrolling 是同一个思想：
**一次展开多个迭代，暴露更多互不依赖的指令。**

**它没有凭空创造并行性。它只是把原来分散在 4 次迭代里的独立工作，放进一个更大的基本块里，让编译器/硬件更容易看见。（本质是共用一个分支预测，减少了循环结构的延时）**

注意一个小细节：如果 (N) 不是展开因子，比如不是 4 的倍数，要额外处理尾巴部分。课件也提醒了这一点。

---

#### 第 69 页：调度循环展开后的代码，重要

4 路展开后，循环体里有 4 次 load、4 次 fadd、4 次 store。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L10-11-Parallelism-23.webp)

编译器可以把它们重新排序，比如先连续 load，再连续 fadd，再 store。

课件给出的性能是：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mn>

4

</mn>

<mtext>

fadds

</mtext>

<mi mathvariant="normal">

/

</mi>

<mn>

11

</mn>

<mtext>

cycles

</mtext>

<mo>

=

</mo>

<mn>

0.36

</mn>
</mrow>

<annotation encoding="application/x-tex">

4 \text{ fadds} / 11 \text{ cycles} = 0.36

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord">

4

</span>

<span className="mord,text">
<span className="mord">

fadds

</span>
</span>

<span className="mord">

/11

</span>

<span className="mord,text">
<span className="mord">

cycles

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

0.36

</span>
</span>
</span>
</span>
</span>

相比第 67 页：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mn>

0.125

</mn>

<mo>

→

</mo>

<mn>

0.36

</mn>
</mrow>

<annotation encoding="application/x-tex">

0.125 \rightarrow 0.36

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6444em;">



</span>

<span className="mord">

0.125

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

0.36

</span>
</span>
</span>
</span>
</span>

提升明显。

原因不是计算量少了，而是：

1. 循环控制开销摊薄了；
2. 编译器看到更多独立指令；
3. 不同迭代之间的 load / fadd / store 可以交错；
4. 功能单元更不容易空着。

这一页很适合出问答：

**问：为什么循环展开能提高 ILP？**

答：

> 循环展开把多个迭代放进一个更大的循环体中，暴露跨迭代的独立指令，使编译器/硬件能更好地调度 load、compute、store，并减少循环分支开销。

---

#### 第 70 页：Software Pipelining，软件流水线，最重要

软件流水线比循环展开更进一步。

普通循环像这样：

```text
第 i 次迭代：load → add → store
第 i+1 次迭代：load → add → store
第 i+2 次迭代：load → add → store
```

软件流水线会把不同迭代的不同阶段重叠起来：

```text
普通 loop unrolling：
[第 i 轮完整做完] [第 i+1 轮完整做完] [第 i+2 轮完整做完]

软件流水线：
第 i 轮：        load → add → store
第 i+1 轮：          load → add → store
第 i+2 轮：                load → add → store
第 i+3 轮：                      load → add → store
```

也就是在同一个循环周期里，同时做：

- 当前迭代的 store；
- 前一/后一迭代的 fadd；
- 更后一迭代的 load。

<alert type="tip">

这里的流水线其实和硬件的流水线是一样的

其实本质是硬件流水线是硬件基础，软件流水线尽量跑满整个流程

</alert>

课件第 70 页的结果是：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mn>

4

</mn>

<mtext>

fadds

</mtext>

<mi mathvariant="normal">

/

</mi>

<mn>

4

</mn>

<mtext>

cycles

</mtext>

<mo>

=

</mo>

<mn>

1

</mn>
</mrow>

<annotation encoding="application/x-tex">

4 \text{ fadds} / 4 \text{ cycles} = 1

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord">

4

</span>

<span className="mord,text">
<span className="mord">

fadds

</span>
</span>

<span className="mord">

/4

</span>

<span className="mord,text">
<span className="mord">

cycles

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
</span>

这比循环展开的：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mn>

4

</mn>

<mi mathvariant="normal">

/

</mi>

<mn>

11

</mn>

<mo>

=

</mo>

<mn>

0.36

</mn>
</mrow>

<annotation encoding="application/x-tex">

4 / 11 = 0.36

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord">

4/11

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

0.36

</span>
</span>
</span>
</span>
</span>

又高很多。

---

#### 第 71 页：Software Pipelining vs Loop Unrolling

第 71 页的核心结论：

> 软件流水线只在整个循环中支付一次启动/结束成本，而不是每个迭代都支付一次。

这句话很重要。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L10-11-Parallelism-24.webp)

循环展开虽然也能提高并行度，但每个展开后的大循环体内部<mark>

仍然有启动和收尾的浪费

</mark>

。软件流水线把不同迭代叠起来，让稳定阶段持续运行，吞吐率更高。

考试可以这样比较：

<table>
<thead>
  <tr>
    <th>
      方法
    </th>
    
    <th>
      优点
    </th>
    
    <th>
      缺点
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      Loop Unrolling
    </td>
    
    <td>
      简单，暴露更多独立指令，减少分支
    </td>
    
    <td>
      代码变大，尾部处理麻烦
    </td>
  </tr>
  
  <tr>
    <td>
      Software Pipelining
    </td>
    
    <td>
      稳定阶段吞吐率高，更充分利用功能单元
    </td>
    
    <td>
      调度复杂，需要 prolog/epilog，寄存器压力大
    </td>
  </tr>
</tbody>
</table>

这几页是本模块最核心的“会考”区域。

---

### 第 72–75 页：非循环代码与 Trace Scheduling

#### 第 72 页：如果没有循环呢？

循环好优化，因为模式重复，编译器容易从很多迭代里挖出 ILP。
但如果代码是大量 `if-else`、分支、跳转，就麻烦了。

第 72 页说：分支会限制控制流密集型、不规则代码里的基本块大小，而在单独的基本块中很难找到足够的 ILP。

**Basic block，基本块**：

> 一段只有一个入口、一个出口，中间没有分支跳转的连续指令序列。

基本块太短，就没有多少指令可调度。处理器/编译器再聪明，也没米下锅。

---

#### 第 73 页：Trace Scheduling，跟踪调度

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 57.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L10-11-Parallelism-25.webp" />
      </p>
    </td>
    
    
      <td style="width: 42.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L10-11-Parallelism-26.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

Trace scheduling 的思路是：

> 不只看一个基本块，而是选一串最常走的基本块路径，把它们当成一个大的 trace 一起调度。

它通常需要：

- profiling feedback，运行时统计反馈；
- 或 compiler heuristics，编译器启发式判断。

然后编译器对整个 trace 做统一调度。
如果程序真的沿着这条常见路径走，就很快；如果中途跳出了 trace，就需要补偿代码 compensation code 来修正状态。课件第 73 页明确提到选择最频繁分支路径、一次性调度整个 trace，并添加修复代码处理跳出 trace 的情况。

这块可以这样记：

> Trace scheduling 是为了解决“基本块太小，ILP 不够”的问题；它跨越多个基本块找常见路径，但代价是需要补偿代码，编译器复杂度上升。

#### 第 74–75 页：例子和补偿代码，略

这两页主要是图示。

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 53.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L10-11-Parallelism-27.webp" />
      </p>
    </td>
    
    
      <td style="width: 46.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L10-11-Parallelism-28.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

抓住两个词就行：

- **trace**：常走路径；
- **compensation code**：当执行偏离常走路径时，用来修正语义的补偿代码。

---

### 第 76–77 页：<mark>经典 VLIW 的问题</mark>

第 76 页很重要，因为它解释了为什么 VLIW 听起来很美，但通用计算领域很难成功。

经典问题有五个：

#### 1. 目标代码兼容性差

VLIW 把功能单元数量、延迟、槽位结构等暴露给编译器。
如果换一代机器，功能单元数量或延迟变了，原来的代码调度就不一定合适，甚至需要重新编译。

这就很尴尬：
普通 x86 程序可以跨很多处理器跑，VLIW 程序可能对具体机器太敏感。

#### 2. 目标代码大小变大

VLIW 指令有很多槽位。
如果某些槽没事做，就要填 `nop`，浪费指令空间。

再加上循环展开、软件流水线会复制代码，代码体积更大，可能浪费 instruction cache。

#### 3. 可变延迟内存操作难调度

编译器静态调度时，很希望知道：load 之后几周期数据可用？

但现实里 load 可能命中 L1，也可能 L2/L3，也可能 cache miss 去 DRAM。
延迟不是固定的，编译器很难提前安排好。

#### 4. 分支概率难知道

Trace scheduling 需要知道哪条路径最常走。
这可能需要 profile 反馈，增加构建流程复杂度。

#### 5. 不可预测分支难调度

不同分支路径的最佳调度可能完全不同。
一个静态调度很难同时适配所有路径。

---

#### 第 77 页：VLIW 指令编码

这页讲如何减少 VLIW 未使用字段带来的浪费。

方法包括：

1. 内存中压缩格式，填入 I-cache 时展开；
2. 标记并行组；
3. 提供单操作的 VLIW 指令。

这页不太像重点计算题。记住一个结论：

> VLIW 指令很宽，容易浪费空间，所以需要编码技巧减少空槽和代码膨胀。

---

### 第 78–84 页：Itanium / IA-64 与旋转寄存器，了解为主

这一段比较偏历史和具体架构。考试更可能考概念，不太会考具体参数。

#### 第 78–80 页：Itanium / EPIC / IA-64，了解即可

第 78 页列了 Itanium “Poulson” 的硬件参数，比如 8 核、L1/L2/L3 cache、最多执行 12 指令/周期等。参数不用背。

第 79 页有几个词要分清：

<table>
<thead>
  <tr>
    <th>
      名词
    </th>
    
    <th>
      含义
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      EPIC
    </td>
    
    <td>
      Explicitly Parallel Instruction Computing，显式并行指令计算
    </td>
  </tr>
  
  <tr>
    <td>
      <mark>
        IA-64
      </mark>
    </td>
    
    <td>
      <mark>
        Intel 的 64 位 ISA
      </mark>
    </td>
  </tr>
  
  <tr>
    <td>
      Itanium
    </td>
    
    <td>
      Intel 的处理器产品线
    </td>
  </tr>
  
  <tr>
    <td>
      Merced
    </td>
    
    <td>
      第一代 Itanium 产品
    </td>
  </tr>
</tbody>
</table>

课件说 EPIC 实际上就是一种 VLIW 风格，IA-64 是 Intel 选择的 ISA。

第 80 页讲 IA-64 指令格式：

- 128-bit 指令束；
- 包含 3 条指令 + template；
- template 描述这些指令和相邻 bundle 的分组；
- 每个 group 中的指令可以并行执行。

这和 VLIW 的思想一致：**把可并行关系显式编码进指令格式。**

---

#### 第 81–84 页：旋转寄存器文件，理解概念即可

IA-64 有很多寄存器：

- 128 个通用整数寄存器；
- 128 个浮点寄存器；
- 64 个 1-bit 预测寄存器；
- GPRs（ General Purpose Registers通用寄存器） 可以 rotate，用来减少软件流水线循环的代码大小。

<mark>

**旋转寄存器文件 Rotating Register File**

</mark>

 <mark>

是为软件流水线服务的

</mark>

。

软件流水线会把多个迭代重叠执行，于是不同迭代需要不同寄存器保存中间结果。
如果手工写，会出现大量 prolog/epilog 和寄存器重命名代码。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L10-11-Parallelism-29.webp)

旋转寄存器的思路是：

> 每次循环迭代时，逻辑寄存器名自动映射到不同的物理寄存器组。

这样同一段循环代码可以在不同迭代中使用“看起来一样”的寄存器名，但背后对应不同物理寄存器，减少代码膨胀。

可以这么理解：
你写的是 `f1, f5, f9`，但每次循环硬件把“抽屉编号”自动旋转一下，避免不同迭代互相覆盖。挺像酒店前台把同一个“房型”分配给不同房间，顾客不用知道具体门牌号。

---

### 第 85–87 页：预测执行、推测执行、数据推测，概念重要

这几页是 IA-64 为了帮助静态调度设计的机制。你不用记具体指令名，但要明白它们解决什么问题。

#### 第 85 页：Predicated Execution，预测执行，重要

问题：

> 分支会限制 ILP。

因为 `if-else` 会把代码切成多个基本块，基本块短，调度空间小。

预测执行的做法是：
把分支两边的指令都放到同一个基本块里，但给每条指令加一个谓词条件。

类似：

```text
(p1) Inst 3
(p2) Inst 5
```

如果 `p1` 为真，就执行 `Inst 3`；如果 `p1` 为假，这条指令就变成 NOP。

这样可以减少分支，把多个基本块合成一个更大的调度区域。课件也说 IA-64 中几乎所有指令都可以在预测寄存器下有条件执行，预测寄存器为假时指令变成 NOP。

但代价是：

- 可能执行一些最终无用的指令；
- 前递、依赖、异常处理变复杂。

---

#### 第 86 页：Speculative Execution，推测执行，重要度中等

问题：

> 分支限制了编译器移动代码的自由。

比如某个 load 在分支后面。编译器想把它提前到分支前面，以便早点开始内存访问，隐藏 load latency。

但普通 load 不能乱提前，因为它可能触发异常。
比如本来这条路径不会执行 load，结果你提前执行了，却访问非法地址，产生“虚假异常”。

IA-64 的解决方式是 **speculative load**：

- 推测 load 不立即抛异常；
- 如果有问题，就在目标寄存器上设置 poison 位；
- 后面用 check 指令检查；
- 如果真的出错，再跳到修复代码。

这对提前调度长延迟 load 很有用。

---

#### 第 87 页：Data Speculation，数据推测，了解

问题：

> 可能的内存冒险限制代码调度。

比如：

```text
store [addr]
load  r1, [addr2]
```

编译器不知道 `addr` 和 `addr2` 会不会相同。
如果相同，load 不能提前到 store 前面；如果不同，提前其实没问题。

数据推测的做法是：
允许 load 先提前执行，但硬件用 address check table 检查后面的 store 是否和它冲突。若冲突，则跳转到修复代码。

这页的重点不是细节，而是：

> IA-64 为了支持编译器静态调度，加入了很多硬件机制来处理分支和内存不确定性。

这也反过来说明：VLIW/EPIC 想让硬件简单，但为了应付真实程序，最后硬件又复杂起来了。

---

### 第 88–89 页：静态调度的限制与 Itanium 结局

第 88 页是本模块的总结，非常重要。

静态调度的限制包括：

1. 不可预知的分支；
2. 不可预测的 cache miss；
3. 代码量爆炸；
4. 编译器复杂性。

课件明确说：<mark>

尽管多次尝试，VLIW 在通用计算领域到目前为止都失败了

</mark>

；更复杂的 VLIW 架构在复杂性上接近有序超标量，但在大型复杂应用上没有真正优势。不过 VLIW 在嵌入式 DSP 市场更成功，因为那里的环境更简单、更受约束、代码更友好。

第 89 页讲 Intel 放弃 Itanium。重点不是背日期，而是理解原因：

> Itanium/IA-64 的核心困难在于，它太依赖编译器把并行性提前挖出来，但现实程序有分支、cache miss、指针别名、可变延迟，编译器很难静态预测一切。

这一页可以作为简答题结尾：

> VLIW 的思想是用编译器静态暴露 ILP，降低硬件动态调度复杂度；但通用程序中的动态行为太多，使静态调度难以可靠高效，因此 VLIW/Itanium 在通用计算中失败，而在嵌入式 DSP 等受控环境中较成功。

---

### 一页纸版总结

这模块可以用一条线串起来：

**ILP 想让一个线程里的多条指令并行执行。**

实现 ILP 有两种典型路线：

1. **Superscalar**：硬件动态找并行；
2. **VLIW**：编译器静态安排并行。

VLIW 的优点是<mark>

硬件调度逻辑可以更简单；缺点是编译器压力巨大

</mark>

，而且现实程序有分支、cache miss、指针别名等动态不确定性。

循环里比较容易找 ILP，所以有：

- **Loop unrolling**：<mark>

展开多个迭代，暴露更多独立指令

</mark>

；
- **Software pipelining**：把不同迭代的 load / compute / store 重叠起来，提高稳定阶段吞吐率。

非循环代码由于分支导致基本块短，ILP 不够，所以有：

- **Trace scheduling**：选常见路径跨基本块调度；
- **Compensation code**：偏离 trace 时修正语义。

IA-64/Itanium 为支持 VLIW/EPIC 加入了：

- instruction bundle；
- rotating registers；
- predicated execution；
- speculative execution；
- data speculation。

但最后通用计算领域没成功，因为：

> 静态调度很难预测真实程序的分支、cache miss 和内存依赖，代码量和编译器复杂度都太高。

---

## 第 4 模块：线程级并行 TLP

继续讲**第 4 模块：线程级并行 TLP，Thread Level Parallelism，第 90–125 页**。

这一板块的第一性原理是：

> 一个 CPU 核本质上一次只能沿着一个 PC 指向的指令流往前执行。
> 要同时推进多个任务，<mark>
> 
> 要么
> 
> </mark>
> 
> <mark>
> 
> **复制核心**
> 
> </mark>
> 
> <mark>
> 
> ，要么
> 
> </mark>
> 
> <mark>
> 
> **复制线程状态并共享核心资源**
> 
> </mark>
> 
> ，要么由操作系统把很多软件线程轮流塞进少量硬件线程里。

所以这一章不是单纯讲“多开几个线程”，而是在讲：**线程是什么、核心是什么、硬件线程是什么、操作系统怎么制造“同时运行”的幻觉、超线程到底为什么有时有用有时没用。**

---

### 第 90 页：标题页

进入 **线程级并行 Thread Level Parallelism**。

前面 DLP 是“一条指令处理多个数据”，ILP 是“一个线程内部多条指令并行”。
现在 TLP 是：

> 多个线程 / 多个任务 / 多个指令流同时推进。

它对应 Flynn 分类里的 **MIMD**：多个指令流，多个数据流。

---

### 第 91 页：改进性能的三条路，重要

程序运行时间大概可以写成：

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

Time = \frac{Instruction\ Count \times CPI}{Clock\ Rate}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



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

所以想让程序更快，理论上有三条路：

1. **提高时钟频率 (**<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

f

</mi>

<mi>

s

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

f_s

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.1076em;">

f

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.1076em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

s

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

**)**
也就是 CPU 主频更高。但课件说当今通用计算机已经接近实用极限，一般用途 CPU 很难继续靠主频暴涨。
2. **降低 CPI**
CPI 是每条指令平均需要多少周期。SIMD、流水线、乱序执行、ILP 都在干这件事：让单个核心每周期做更多事。
3. **同时执行多个任务**
这就是本板块：多个 CPU/core 同时跑多个指令流。

这里要注意：TLP 有两种场景。

一种是**相关任务**，例如把一个大矩阵乘法切成几块，每个核心算一部分。另一种是**无关任务**，例如一个核心跑浏览器，一个核心跑 PPT，一个核心处理后台服务。课件最后说真正现代机器是“都要”：高主频、SIMD、多任务并行一起用。

> 这章主要是相关任务

考试问“为什么需要 TLP？”可以答：

> 主频提升遇到功耗和散热限制，单核 CPI 也有极限，所以需要通过多个核心/线程同时推进多个任务来继续提高吞吐量。

---

### 第 92 页：并行计算机体系结构，重要度中等

这页是在把“线程级并行”放到不同规模的机器里看。

从小到大：

<table>
<thead>
  <tr>
    <th>
      结构
    </th>
    
    <th>
      第一性原理理解
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      多核 CPU
    </td>
    
    <td>
      在一个芯片上放多个处理核心，共享部分缓存、内存和外设
    </td>
  </tr>
  
  <tr>
    <td>
      GPU
    </td>
    
    <td>
      大量更简单的计算单元，适合高度并行的数据处理
    </td>
  </tr>
  
  <tr>
    <td>
      计算机阵列 / 集群
    </td>
    
    <td>
      多台独立电脑通过网络通信
    </td>
  </tr>
  
  <tr>
    <td>
      Warehouse-scale computer
    </td>
    
    <td>
      数据中心级别，大量节点一起工作
    </td>
  </tr>
</tbody>
</table>

多核 CPU 的特点是：多个数据路径在单芯片上，通常共享 L3 cache、内存、外设。
这就是在问：

> 我们要复制多少硬件？哪些硬件复制？哪些硬件共享？

如果完全复制一台电脑，那就是集群。
如果复制核心但共享内存，那就是多核 CPU。
如果复制很多小计算单元，强调吞吐，那就是 GPU。

---

### 第 93 页：两核 CPU，重要

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L10-11-Parallelism-30.webp)

这页画了一个两核 CPU：两个处理器核心都有自己的控制器、数据通路和 PC，但访问同一个存储器系统。

> 要独立执行两个指令流，至少要有两个独立的 PC。

因为 PC 决定“下一条指令在哪里”。

这就是 TLP 和 SIMD 的根本区别：

<table>
<thead>
  <tr>
    <th>
      并行类型
    </th>
    
    <th>
      控制流
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      SIMD
    </td>
    
    <td>
      一个指令流控制多个数据
    </td>
  </tr>
  
  <tr>
    <td>
      TLP / MIMD
    </td>
    
    <td>
      多个指令流各自推进
    </td>
  </tr>
</tbody>
</table>

---

### 第 94 页：单核 CPU vs 多核 CPU，重要度中等

这页定义单核和多核。

**单核 CPU**：一个 CPU 核心加相关辅助电路封装在芯片中。
**多核 CPU**：多个 CPU 核心加相关辅助电路封装在同一芯片中。

“核心 core”最关键的是：

- 能取指；
- 能译码；
- 有自己的执行路径；
- 有自己的架构状态，比如 PC 和寄存器；
- 能独立推进一条指令流。

多核的直觉是“复制执行机器”。
但复制不是免费的：面积、功耗、cache 一致性、内存带宽都会成为问题。

---

### 第 95 页：多处理器执行模型，最重要之一

这页明确区分了**独立资源**和**共享资源**。

每个 core 有自己的：

- 数据通路（PC；寄存器；ALU）
- 通常还有较高层级的私有 cache，比如 L1/L2。

多个 core 共享：

- DRAM 主存；
- 通常共享 L3 cache；

所以一个四核 CPU 可以同时执行四个不同的指令流，但它们并不是四台完全独立的机器，因为它们共享内存系统。

这一页是 TLP 的硬件基础。

> 计算需要“算力”和“数据”。多核复制了算力，但数据入口往往仍然共享。

所以多核不一定线性加速。
如果 4 个核心都疯狂访问 DRAM，它们会争同一条内存通路。瓶颈就从“算不动”变成“喂不饱”。

---

### 第 96 页：向多核过渡，理解趋势即可

这页的图表达一个历史趋势：过去单线程程序性能每年大幅提升，后来靠单核继续提升越来越难。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L10-11-Parallelism-31.webp)

1. 主频不能无限增加；
2. 单核乱序、超标量、流水线越做越复杂，边际收益下降；
3. 功耗近似和频率、电压、晶体管活动强相关；
4. 继续把晶体管堆在一个核心上，收益不如分成多个核心。

所以处理器设计从“做一个越来越强的核”，转向“做多个够强的核”。

这页不太会考具体曲线，但可能考概念：**为什么从单核转向多核？**

---

### 第 97 页：多处理器执行模型

这页是多核编程的核心模型。

**共享内存 Shared Memory**：

> 每个 core 都能访问处理器中的整个内存。

优点：

- 程序员可以通过共享变量简化程序中的通信；

缺点：

- 扩展性不好，共享内存会被很多核心同时访问，成为瓶颈；

课件还说使用多处理器有两种方式：

1. **多任务并行**：多个处理器处理无关问题，程序之间没有通信；
2. **单任务划分**：把同一个任务拆给多个核心，比如每个核心算矩阵乘法的一部分。

无关任务并行很简单：大家互不通信，互不等待。
单任务并行难，因为要切分任务、同步结果、避免数据竞争、保证负载平衡。

---

### 第 98 页：并行处理困难但不可避免

这页说并行处理“困难但不可避免”。

为什么不可避免？

- 性能提升需要并行；
- 降低能耗也需要并行；
- 移动设备、数据中心都在用多核和专用处理器。

所以真实系统常常是：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mtext>

数据中心级并行

</mtext>

<mo>

+

</mo>

<mtext>

多节点

</mtext>

<mo>

+

</mo>

<mtext>

多核

</mtext>

<mo>

+

</mo>

<mtext>

每核

</mtext>

<mi>

S

</mi>

<mi>

I

</mi>

<mi>

M

</mi>

<mi>

D

</mi>

<mo>

+

</mo>

<mtext>

每核

</mtext>

<mi>

I

</mi>

<mi>

L

</mi>

<mi>

P

</mi>
</mrow>

<annotation encoding="application/x-tex">

数据中心级并行 + 多节点 + 多核 + 每核SIMD + 每核ILP

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">



</span>

<span className="mord,cjk_fallback">

数据中心级并行

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

多节点

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

多核

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

每核

</span>

<span className="mord,mathnormal" style="margin-right:0.0576em;">

S

</span>

<span className="mord,mathnormal" style="margin-right:0.0785em;">

I

</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

D

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
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,cjk_fallback">

每核

</span>

<span className="mord,mathnormal" style="margin-right:0.0785em;">

I

</span>

<span className="mord,mathnormal">

L

</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>
</span>
</span>
</span>
</span>

---

### 第 99 页：潜在并行性能，重要

这页用表格展示一个趋势：核心数增加，SIMD 位宽增加，总的潜在 FLOPs/cycle 大幅增加。

表里逻辑大概是：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mtext>

总并行能力

</mtext>

<mo>

≈

</mo>

<mtext>

核心数

</mtext>

<mo>

×

</mo>

<mtext>

每核心

</mtext>

<mi>

S

</mi>

<mi>

I

</mi>

<mi>

M

</mi>

<mi>

D

</mi>

<mtext>

宽度

</mtext>
</mrow>

<annotation encoding="application/x-tex">

总并行能力 \approx 核心数 \times 每核心SIMD宽度

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,cjk_fallback">

总并行能力

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

<span className="mord,cjk_fallback">

核心数

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

每核心

</span>

<span className="mord,mathnormal" style="margin-right:0.0576em;">

S

</span>

<span className="mord,mathnormal" style="margin-right:0.0785em;">

I

</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

D

</span>

<span className="mord,cjk_fallback">

宽度

</span>
</span>
</span>
</span>
</span>

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L10-11-Parallelism-32.webp)

- MIMD 提供核心级并行；
- SIMD 提供每核心内部的数据并行；

两者相乘，才有现代处理器的理论吞吐。

但注意：这是**潜在性能**，不是实际性能。
实际能不能达到，要看程序是否有足够并行性、内存能不能喂饱、同步开销大不大。

---

### 第 100 页：电脑上同时运行很多程序，重要度中等

这页列出一堆正在运行的进程，最后问：电脑如何同时做 156 个作业？

<mark>

这是进入“线程/操作系统调度”的引子

</mark>

。

> 如果硬件线程数量远小于软件任务数量，那么所谓“同时运行”很多时候是快速切换造成的幻觉。

比如你电脑只有 4 个硬件线程，但系统里有 156 个进程。它不可能物理上同时跑完所有进程。操作系统会：

- 让一部分线程运行；
- 让其他线程等待；
- 定时切换；
- 遇到 I/O 等待时换别的线程上来。

人的感觉是“都开着”，但硬件每个时刻只能服务有限个线程。

---

### 第 101 页：线程是什么

**线程 Thread**：

> 执行某个任务的一段连续指令流。

每个线程有：

- 专用 PC；
- 独立寄存器；
- 可以访问共享内存。

每个物理核心提供一个或多个 hardware threads。操作系统把 software threads 映射到可用的 hardware threads 上；没有映射到硬件线程的线程只能等待。

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mtext>

线程

</mtext>

<mo>

=

</mo>

<mtext>

当前执行位置

</mtext>

<mo stretchy="false">

(

</mo>

<mi>

P

</mi>

<mi>

C

</mi>

<mo stretchy="false">

)

</mo>

<mo>

+

</mo>

<mtext>

当前变量现场

</mtext>

<mo stretchy="false">

(

</mo>

<mtext>

寄存器

</mtext>

<mi mathvariant="normal">

/

</mi>

<mtext>

栈等

</mtext>

<mo stretchy="false">

)

</mo>

<mo>

+

</mo>

<mtext>

对内存的访问能力

</mtext>
</mrow>

<annotation encoding="application/x-tex">

线程 = 当前执行位置(PC) + 当前变量现场(寄存器/栈等) + 对内存的访问能力

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,cjk_fallback">

线程

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

<span className="mord,cjk_fallback">

当前执行位置

</span>

<span className="mopen">

(

</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

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

<span className="mord,cjk_fallback">

当前变量现场

</span>

<span className="mopen">

(

</span>

<span className="mord,cjk_fallback">

寄存器

</span>

<span className="mord">

/

</span>

<span className="mord,cjk_fallback">

栈等

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
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,cjk_fallback">

对内存的访问能力

</span>
</span>
</span>
</span>
</span>

> 为什么线程需要 PC？
> 因为它要知道下一条指令在哪。
> 
> 为什么需要寄存器？
> 因为它要保存当前计算状态。
> 
> 为什么共享内存？
> 因为多个线程可能协同完成一个任务，需要交换数据。

**问：线程包含哪些状态？****PC、寄存器/处理器状态，以及对共享内存的访问。**

---

### 第 102 页：操作系统线程

这页讲 OS 如何制造“多个线程同时活动”的错觉。

操作系统<mark>

把 software threads 多路复用到 hardware threads 上

</mark>

。切换时要做：

1. 中断当前线程；
2. 保存它的寄存器和 PC 到内存；
3. 选择另一个线程；
4. 恢复那个线程之前保存的寄存器；
5. 跳转到它的 PC 继续执行。

课件提到两种常见切换方式：

- 线程阻塞，比如 cache miss、用户输入、网络访问；
- timer，比如每 1ms 切换一次活动线程。

> 只要你能完整保存一个线程的状态，将来再恢复它，它就会“以为自己只是睡了一下”。

这就是上下文切换 context switch。

但是上下文切换有成本。寄存器越多，状态越大，切换越慢。
现代 CPU 还有 SIMD/AVX 寄存器，状态更大，所以线程切换不是免费的。

---

### 第 103 页：4 核示例，重要度中等

这页展示一个 4 核机器：操作系统维护一个 thread pool，然后把线程映射到 Core 1–4。

核心句子：

> 每个 core 每次主动运行一个指令流。

这句话很关键。
<mark>

如果没有超线程，一个 core 在某个时刻通常只运行一个硬件线程

</mark>

。
如果有 100 个软件线程，它们要排队。

> <mark>
> 
> 核心数量决定了真正同时推进的硬件线程上限；操作系统调度决定哪个软件线程得到运行机会
> 
> </mark>
> 
> 。

这页要和后面超线程区别开：

- 多核：真的有多个执行核心；
- 操作系统线程：软件层面的任务；
- 硬件线程：核心提供的硬件执行单位。

---

### 第 104 页：为什么需要硬件多线程

这页很关键。

典型场景：

- 活动线程遇到 cache miss；
- 需要等待大约 1000 个周期从 DRAM 读取数据；
- 那么可以切换运行别的线程，直到数据回来。

第一性原理：

> CPU 不怕算，怕等。
> 多线程的一个核心价值是：当一个线程在等内存时，让另一个线程占用执行资源。

<mark>

这叫

</mark>

 <mark>

**latency hiding，隐藏延迟**

</mark>

<mark>

。

</mark>



但问题是：
如果靠操作系统保存/恢复 PC 和所有寄存器，切换太慢。
课件说必须在远小于 1000 个周期内完成切换，否则还不如等。

所以硬件能帮忙：在核心内部保留多个线程的 PC 和寄存器状态，切换时不用把大量状态搬进搬出内存。

这就是硬件多线程的动机。

---

### 第 105 页：CDC 6600 外围处理器，了解即可

这是历史例子。

CDC 6600 的外围处理器是早期多线程硬件：

- 10 个虚拟 I/O 处理器；
- fixed interleave，固定交织；
- 简单流水线；
- 每个虚拟处理器每 1000ns 执行一条指令；
- 使用累加器指令集，减少处理器状态。

> 硬件多线程最早的动机之一不是为了提高单线程速度，而是为了在长延迟 I/O 或内存等待中保持硬件忙碌。

---

### 第 106 页：简单多线程流水线，重要

这页画了简单多线程流水线。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L10-11-Parallelism-33.webp)

关键机制是：流水线里要携带 **thread select**，也就是“这条正在流水线中的指令属于哪个线程”。

为什么要携带 thread select？

因为同一条流水线里可能交错着多个线程的指令。
执行到寄存器读写阶段时，必须知道：

- 读哪个线程的寄存器；
- 写哪个线程的寄存器；
- 更新哪个线程的 PC。

课件说，<mark>

对软件和操作系统看起来，它像多个 CPU核心，

</mark>

虽然每个都更慢。

> 如果多个线程共享同一条数据通路，那么必须给每条指令贴上“线程身份标签”。

否则就会出现 Thread A 的指令错误地写 Thread B 的寄存器，直接爆炸。

<alert type="tip">
<mark>

多核心和硬件多线程的区别

</mark>



执行一个线程至少需要两类东西：

1. 线程状态：PC、寄存器、控制状态
2. 执行资源：取指、译码、发射、ALU、FPU、load/store、cache 带宽等

**多核心**的做法是：把执行资源也复制多份。
**硬件多线程**的做法是：主要复制线程状态，但共享大部分执行资源。

</alert>

<alert type="tip">

SMT / Hyperthreading 是硬件多线程的一种

硬件多线程有几种风格：

1. 粗粒度多线程：
一个线程卡住了，比如 cache miss，再切另一个线程
2. 细粒度多线程：
每个 cycle 或几个 cycle 轮换不同线程
3. SMT / Hyperthreading：
同一个 cycle 内，从多个线程同时发射指令

</alert>

---

### 第 107 页：硬件多线程成本，重要

硬件多线程不是白嫖。

每个线程需要自己的用户状态：

- PC；
- GPRs，通用寄存器。

还需要系统状态：

- 虚拟内存页表寄存器；
- 异常处理记录。

其他开销：

- 线程之间竞争 cache；竞争 TLB；
- 需要更大 cache/TLB；
- OS 调度更多线程也有开销。

> 多线程增加吞吐量的前提是“资源空着不用很浪费”。
> 但如果资源本来就紧张，多线程会互相抢资源。

所以超线程可能提升性能，也可能降低某个线程的性能。

---

### 第 108 页：线程调度策略，重要

这页比较三种硬件线程调度策略。

#### 1. Fixed interleave 固定交织

N 个线程轮流执行。
例如有 4 个线程：

```text
周期1：Thread 0
周期2：Thread 1
周期3：Thread 2
周期4：Thread 3
周期5：Thread 0
```

如果某个线程轮到它时没准备好，就插入气泡。

优点：简单。
缺点：不灵活，线程没准备好也浪费槽位。

#### 2. Software-controlled interleave

操作系统给 N 个线程分配 S 个流水线槽，硬件在这些槽上固定交织，执行插槽中的一个线程

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L10-11-Parallelism-34.webp)

优点：比完全固定灵活一点。
缺点：仍然依赖软件安排。

#### 3. Hardware-controlled thread scheduling

硬件跟踪哪些线程 ready，然后按优先级选择下一个线程。

优点：更动态、更有效。
缺点：硬件复杂。

---

### 第 109 页：Denelcor HEP，了解即可

HEP 是第一台在主 CPU 中使用 hardware thread 的商用机器：

- 每个处理器 120 个线程；
- 10 MHz；
- 最多 8 个处理器；
- 是 Tera MTA 多线程架构的前身。

---

### 第 110 页：SMT，同步多线程

这页开始讲 **SMT = Simultaneous Multithreading，同步多线程**，也就是常说的超线程 Hyperthreading 的核心思想。

前面介绍的是 **vertical multithreading，垂直多线程**：

> 每个流水线阶段一次只处理一个线程，只是在不同周期切换线程。

而 SMT 更激进：

> 在同一个时钟周期内，允许多个线程的指令同时进入超标量处理器的多个执行槽位。

课件说 SMT 利用 OoO 超标量已有的细粒度控制，让多个线程的指令在同一周期进入执行，从而更好利用机器资源。

> 超标量 CPU 一周期可能有多个 issue slots，但单个线程经常填不满。SMT 用另一个线程的指令来填空位。

这就是 SMT 的本质：**填空位**。

---

### 第 111 页：超标量机器的浪费，重要

这页图里有两个浪费：

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L10-11-Parallelism-35.webp)

1. **Vertical waste 垂直浪费**
某些周期完全空闲，什么指令都没发射。（整一行都是空的）
2. **Horizontal waste 水平浪费**
某周期有一些指令发射，但 issue width 没填满。
比如 4 发射机器只发射了 1 条或 2 条。（某一行没有填满）

> 超标量机器的硬件宽度是固定成本。空槽越多，硬件利用率越差。

如果单线程因为 cache miss、分支、依赖，无法提供足够指令，硬件就闲着。

---

### 第 112 页：垂直多线程

垂直多线程通过 cycle-by-cycle interleaving 消除一部分垂直浪费。

> 本质就是每个 cycle 换一个 thread 来发射指令。

例如：

```text
周期1：Thread A
周期2：Thread B
周期3：Thread A
周期4：Thread B
```

这样如果 A 在某些周期会卡住，B 可以顶上。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L10-11-Parallelism-36.webp)

但问题是：
每个周期仍然主要来自一个线程，所以如果是 4 发射机器，Thread B 也可能只填 2 个槽。
于是**水平浪费仍然存在**。

所以 vertical multithreading 解决的是“某些周期完全闲着”的问题，但不一定能解决“每周期槽位填不满”的问题。

---

### 第 113 页：Chip Multiprocessing，CMP（其实就是多核心）

CMP 就是把芯片拆成多个处理器核心。

> 需要增加更多的硬件组件，多一份的执行组件

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L10-11-Parallelism-37.webp)

效果：

- 减少水平浪费；
- 留下一些垂直浪费；
- 限制每个线程的峰值吞吐量。

因为如果一个大超标量核心有 4 个 issue slots，一个线程可能填不满。
拆成两个较小核心后，每个核心服务不同线程，单个线程独享一部分资源，资源浪费可能减少。

但代价是：

- 单线程峰值性能下降；
- core 之间共享数据要通信；
- cache coherence 更复杂。

---

### 第 114 页：理想超标量多线程，重要

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L10-11-Parallelism-38.webp)

理想 SMT 是：

> 无约束地把多个线程的指令交叉放进多个 issue slots。

也就是说，在同一周期内：

```text
slot 0: Thread A 的指令
slot 1: Thread B 的指令
slot 2: Thread A 的指令
slot 3: Thread C 的指令
```

只要依赖和资源允许，就尽量填满。

> 如果一个线程不能提供足够独立指令，多个线程合起来可能可以。

这就是 SMT 的理论诱惑：
不复制完整核心，只复制一些线程状态，就提高执行资源利用率。

---

### 第 115 页：Hyperthreading，必须掌握

这页是考试重点。

**Hyperthreading = SMT 的一种商业实现。**

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L10-11-Parallelism-39.webp)

特点：

- 逻辑 CPU 数量大于物理 CPU 数量；
- 每个 core 同时运行多个 threads；
- 每个 thread 有自己的体系结构状态<mark>

，比如 PC、寄存器

</mark>

；
- 共享 <mark>

cache、instruction unit、execution units（执行单元）

</mark>

；
- 可能提高 core 的总体利用率；
- 但也可能降低单个线程性能。

这里课件写“提高核心 CPI，可能降低线程 CPI”，这句话容易让人困惑。直观理解是：

- 从整个 core 看，资源利用率更高，总吞吐更好；
- 从单个 thread 看，它要和别人抢 cache、带宽、执行单元，所以可能变慢。

> 超线程通常提高核心总吞吐，但不保证单线程性能提高；两个逻辑 CPU 共享同一个物理核心的大部分执行资源，因此性能不会等于两个完整核心。

这个非常重要。
**2 个 logical CPU ≠ 2 个 physical core。**

---

### 第 116 页：多线程类别总结，重要

这页图总结了几类多线程方式：

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L10-11-Parallelism-40.webp)

<table>
<thead>
  <tr>
    <th>
      类别
    </th>
    
    <th>
      第一性原理理解
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      Superscalar
    </td>
    
    <td>
      单线程尽量填多个 issue slots
    </td>
  </tr>
  
  <tr>
    <td>
      Coarse-grained MT
    </td>
    
    <td>
      遇到大延迟事件才切换线程
    </td>
  </tr>
  
  <tr>
    <td>
      Fine-grained MT
    </td>
    
    <td>
      每个周期在线程之间切换
    </td>
  </tr>
  
  <tr>
    <td>
      Multiprocessing
    </td>
    
    <td>
      多个核心分别执行线程
    </td>
  </tr>
  
  <tr>
    <td>
      SMT
    </td>
    
    <td>
      同一周期内多个线程共享 issue slots
    </td>
  </tr>
</tbody>
</table>

<alert type="tip">

要清楚：superscalar是ILP范畴的内容。

1. 普通超标量处理器：一个 core 里有多个执行资源（一个较宽的取址前端加上多个ALU……）；同一个周期同时执行/发射的多条指令，通常来自<mark>

同一个线程的同一条指令流

</mark>

。
  - 一份 PC / 一份线程上下文
  - 多条指令同时发射
  - 多个执行单元并行工作
2. 超标量本身只表示一个 core 每周期可发射多条指令；这些指令在普通超标量中来自同一个线程。若再加 SMT，则可以来自多个线程。

</alert>

<alert type="tip">

SMT可以理解为硬件多线程和超标量处理器的结合，（其二者需要的底层硬件结构有所不同）

多核多线程

</alert>

这页图的重点是看“空槽”怎么被减少。

- Superscalar：单线程填不满，容易有空槽；
- Fine-grained：减少完全空闲周期，但仍可能填不满横向槽；
- Coarse-grained：大事件才切换，简单但反应慢；
- Multiprocessing：不同核心跑不同线程；
- SMT：多个线程一起填一个宽发射核心的槽位。

考试如果问“SMT 与 fine-grained multithreading 的区别”，可以答：

> Fine-grained multithreading 通常每个周期只从一个线程取指/发射，只是周期级交织；SMT 可以在同一个周期内从多个线程发射指令到多个 issue slots。

---

### 第 117 页：SMT 初始性能，重要

这页给出实际数据，结论很克制：SMT 不一定暴涨。

例如：

- Pentium 4 Extreme SMT 对 SPECint_rate 加速 1.01；
- 对 SPECfp_rate 加速 1.07；
- 26 个 SPEC 基准中速度变化从 0.90 到 1.58，平均 1.20；
- Power 5 上也有一定提升，但不同应用差异明显；
- 浮点应用 cache 冲突最多，收益较小。

> SMT 的收益取决于“共享资源有没有空闲”和“两个线程会不会抢同一种瓶颈资源”。

如果两个线程瓶颈互补，一个等内存，一个用 ALU，就可能提升明显。
如果两个线程都抢 cache 或内存带宽，就可能互相伤害。

---

### 第 118–120 页：SMT 性能中的应用交互，重要

这三页都在讲同一件事：**SMT 的性能强烈依赖应用组合。**

#### 第 118 页：有些程序不受另一个程序影响

图上标出某些应用“没有受到另外程序的影响”。
这说明它们对共享资源不敏感，或者另一个程序没有抢到它的关键资源。

#### 第 119 页：有些组合表现不好

图里标出“表现不好”。
说明有些程序放在一起会互相拖累。

可能原因：

- 都大量访问 cache；
- 都占用内存带宽；
- 都使用同类执行单元；
- 工作集互相把对方挤出 cache。

#### 第 120 页：有些程序对第二个程序非常敏感

图里标出“对第二个程序非常敏感”。
意思是某个程序单独跑还可以，但和不同程序配对时性能变化很大。

第一性原理：

> SMT 共享的是物理资源，所以两个线程之间不是彼此透明的。它们会通过 cache、TLB、带宽、执行单元发生干扰。

考试可以这样答：

> SMT 性能取决于线程间资源需求是否互补；若线程争用相同瓶颈资源，可能导致 slowdown；若一个线程等待内存而另一个线程可使用执行单元，则吞吐可能提升。

---

### 第 121 页：硬件辅助的软件多线程，重要

这页画了一个 1 core、2 threads 的处理器。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L10-11-Parallelism-41.webp)

硬件内部有两个副本的：

- PC；
- 寄存器。

但共享：

- 控制器/数据通路；
- ALU；
- cache；
- 内存接口。

对软件来说，它像两个处理器：hardware thread 0 和 hardware thread 1。
超线程中两个线程可以同时 active。

> 超线程复制的是“状态”，不是完整“算力”。

如果复制完整核心，那是 multicore。
如果只复制 PC/寄存器等线程状态，共享执行资源，那是 SMT/Hyperthreading。

---

### 第 122 页：逻辑线程 vs 多核，最重要之一

这一页直接对比：

#### 逻辑线程 Logical threads

硬件增加约 1%，性能提升约 10%。
原因：

- 独立寄存器；
- 共享数据通路、ALU、cache。

#### 多核 Multicore

重复处理器（基本是整条流水线）

硬件增加更多，比如 50%，性能可能接近 2 倍，但不保证。

#### 现代机器两者兼备：

**多核，每个核有多个线程。**

第一性原理：

<table>
<thead>
  <tr>
    <th>
      技术
    </th>
    
    <th>
      复制了什么
    </th>
    
    <th>
      共享了什么
    </th>
    
    <th>
      性能特点
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      逻辑线程 / SMT
    </td>
    
    <td>
      PC、寄存器、线程状态
    </td>
    
    <td>
      ALU、cache、取指译码、数据通路
    </td>
    
    <td>
      便宜，提高吞吐有限
    </td>
  </tr>
  
  <tr>
    <td>
      多核
    </td>
    
    <td>
      几乎整个执行核心
    </td>
    
    <td>
      通常共享 L3/DRAM/I/O
    </td>
    
    <td>
      更贵，但并行能力更强
    </td>
  </tr>
</tbody>
</table>

所以看到 `physicalcpu = 4`、`logicalcpu = 8`，不要以为有 8 个完整核心。
它通常是 4 个物理核，每个核 2 个硬件线程。

---

### 第 123 页：Mac Air 例子，重要度中等

这页用命令：

```bash
sysctl -a | grep hw
```

看到机器信息：

- physicalcpu: 2；
- logicalcpu: 4；
- L1 I-cache: 32KB；
- L1 D-cache: 32KB；
- L2: 256KB；
- L3: 4MB；
- cache line size: 64B。

> 操作系统看到的是 logical CPU，用来调度线程；但真实性能上限还要看 physical CPU 和共享资源。

2 个 physical CPU / core，4 个 logical CPU，通常意味着每个物理核有 2 个硬件线程。

性能实验时可以试 1、2、4 个线程，但不要预期 4 个线程一定是 1 个线程的 4 倍。

---

### 第 124 页：Hive 计算机例子

这页机器是：

- physicalcpu: 4；
- logicalcpu: 8；
- L1 I-cache: 32KB；
- L1 D-cache: 32KB；
- L2: 256KB；
- L3: 8MB。

课件说：应该尝试最多 8 个线程，看看即使只有 4 个内核，性能是否有所提高。

这句话很务实。

实验策略：

- 先跑 1 个线程；
- 再跑 2、4 个线程；
- 再跑 8 个线程；
- 看性能曲线。

如果 4 到 8 还有提升，说明 SMT 有帮助。
如果 4 到 8 不升反降，说明超线程带来的资源争用超过了收益。

---

### 第 125 页：6 Core，24 Logical Threads

这页展示 6 个 core，每个 core 有 4 个逻辑线程，所以总共有 24 logical threads。操作系统把软件线程映射到这些核心和硬件线程上。

第一性原理：

> logical thread 是调度入口，不等于完整核心。

如果每个 core 有 4 个 hardware threads，那么这 4 个线程共享同一个 core 的执行资源。
适合的场景是：很多线程经常等待内存或 I/O，可以互相填补空档。

<alert type="tip">

physical CPU 指的是有多少个核心

logical CPU 是看有多少线程（核心*每个核心线程）

</alert>

> TLP 是多个线程或任务的并行执行，对应 MIMD。

> 线程的核心状态包括 PC、寄存器和对共享内存的访问。

> 操作系统通过上下文切换，把多个软件线程多路复用到有限硬件线程上。

> 硬件多线程通过快速切换或同时执行多个线程来隐藏长延迟。

> SMT/超线程复制的是线程状态，不是完整核心；它共享 cache、执行单元和数据通路。

> 逻辑 CPU 数量大于物理 CPU 数量时，通常说明存在超线程，但性能不会按逻辑 CPU 数量线性增长。

---

## 第 5 模块：并行编程语言 / OpenMP（如何用软件利用这些并行性）

> 硬件给了我们多个核心、多个线程、SIMD 单元，但 C 程序默认是**顺序语义**。
> 所以并行编程语言/框架要解决一个根本问题：**程序员怎样告诉机器“哪些工作可以同时做、哪些数据是共享的、哪些结果最后要合并”？**

这块的考试重点非常明确：**OpenMP、parallel for、fork-join、shared/private、barrier、reduction、race condition**。尤其第 135、136、145–149 页，很像会考简答或代码判断。

---

### 第 127 页：为什么需要并行，回顾但重要

这页回顾前面的动机：性能提升的唯一现实路径是并行。原因包括：

1. **时钟频率持平或下降**；
2. **SIMD 位宽变宽**，比如 AVX-512；
3. **MIMD 核心数增加**，例如 10 个物理 CPU、20 个逻辑 CPU；
4. 关键挑战变成：处理器数量增加后，如何写出高性能并行程序。

这页列出的四个挑战要记：

<table>
<thead>
  <tr>
    <th>
      挑战
    </th>
    
    <th>
      第一性原理解释
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      Scheduling 调度
    </td>
    
    <td>
      哪些任务分给哪些线程/核心
    </td>
  </tr>
  
  <tr>
    <td>
      Load balancing 负载平衡
    </td>
    
    <td>
      每个线程工作量尽量差不多
    </td>
  </tr>
  
  <tr>
    <td>
      Synchronization time 同步时间
    </td>
    
    <td>
      线程等待彼此会浪费时间
    </td>
  </tr>
  
  <tr>
    <td>
      Communication overhead 通信开销
    </td>
    
    <td>
      线程交换数据也要成本
    </td>
  </tr>
</tbody>
</table>

---

### 第 128-129 页：并行语言很多，略讲

这一页列了一大堆并行语言/框架：CUDA、Cilk、Go、Erlang、Scala、OpenMP 相关模型等。
这一页不用背名字。

它想说明一件事：

为什么没有万能语言？
因为“并行”的形态差异巨大。

矩阵乘法的并行是：大量规则数据，适合 SIMD、OpenMP、CUDA。
Web 服务器的并行是：很多独立请求，适合线程池/事件驱动。
I/O 的并行是：很多任务在等待磁盘、网络、用户输入。
这些问题的瓶颈完全不同，所以语言设计也不同。

这页还提到 SIMD 特性不断加入编译器，而且把 C 翻译成好的汇编用了 20 多年。意思是：编译器很强，但它不可能总是自动猜出最优并行结构。程序员仍然需要提供并行提示。

---

### 第 130 页：Parallel Loops，并行循环，最重要的直觉

这一页是 OpenMP 的起点。

串行循环：

```c
for (int i = 0; i < 100; i++) {
    ...
}
```

默认语义是：

```text
i=0 做完，再做 i=1，再做 i=2 ...
```

并行循环的想法是把迭代空间切成块：

```text
线程0：i = 0 到 24
线程1：i = 25 到 49
线程2：i = 50 到 74
线程3：i = 75 到 99
```

从第一性原理看，一个循环能不能并行，取决于：

> 第 i 次迭代是否依赖第 i-1 次迭代的结果。

例如这个可以并行：

```c
for (int i = 0; i < N; i++)
    b[i] = a[i] * 2;
```

因为每个 `b[i]` 独立。

这个不容易直接并行：

```c
for (int i = 1; i < N; i++)
    a[i] = a[i-1] + 1;
```

因为第 i 次依赖第 i-1 次。
所以并行循环的第一原则是：**迭代之间最好相互独立。**

---

### 第 131 页：OpenMP 组件：for 循环，重要

这一页具体讲 OpenMP 如何处理 for 循环。

例子：

```c
for (i = 0; i < max; i++)
    zero[i] = 0;
```

OpenMP 的想法是：

> 把循环迭代拆成块，把每个块分给一个线程。

比如 `max = 100`，2 个线程：

- 线程 0：处理 0–49；
- 线程 1：处理 50–99。

这页还说 OpenMP 编译器必须能理解这个循环，并且运行时系统要能决定给每个线程多少迭代。

还有一个限制：<mark>

不能从循环中提前跳出

</mark>

，也就是不要在 pragma 块里用 `break`、`return`、`exit`、`goto` 这类破坏结构化控制流的东西。

> OpenMP 要把循环切开分给多个线程，所以它必须能清楚知道循环的边界、步长、迭代次数和退出条件。

如果你在循环中间 `break`，那就麻烦了：
线程 0 break 了，线程 1、2、3 怎么办？已经执行的迭代算不算？别的线程要不要停？语义会变复杂。

所以 OpenMP 喜欢结构规整的循环。

---

### 第 132 页：OpenMP parallel for 语法，必须掌握

这一页给出最核心语法：

```c
#include <omp.h>

#pragma omp parallel for
for (int i = 0; i < 100; i++) {
    ...
}
```

这也是 OpenMP 的优雅之处：
**它尽量不改变 C 语言本身，而是通过注释式指令添加并行语义。**

---

### 第 133 页：OpenMP 例子输出，重要度中等

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L10-11-Parallelism-42.webp)

注意一个细节：输出顺序不一定按 `i=0,1,2,3...` 排列。
因为线程是并发执行的，谁先打印取决于调度。
所以并行程序里：

> 计算结果可以确定，但输出顺序不一定确定。

这个直觉后面理解 race condition 很重要。

---

### 第 134 页：OpenMP 基本性质，必须掌握

这一页是 OpenMP 的定义页。OpenMP 是：

- C 的扩展，不需要学一门全新语言；
- 多线程；共享内存并行；

  - 使用 compiler directives，比如 `#pragma`；
  - 使用 runtime library，比如 `#include <omp.h>`；
- 同一份源代码可以在 1 核和 16 核机器上运行；
- 只适用于共享内存。

> OpenMP 假设多个线程能看到同一个地址空间。

所以线程之间通信很简单：读写同一个变量。
但这也是危险来源：多个线程如果同时写同一个变量，就可能发生<mark>

数据竞争

</mark>

。

这页非常适合考：

**问：OpenMP 适合什么机器？**

答：
**共享内存多处理器/多核机器。**

它不适合那种每台机器有独立内存、必须通过网络通信的分布式系统。那种更适合 MPI。

---

### 第 135 页：OpenMP parallel for 细节

这一页是考试重点。

代码：

```c
#pragma omp parallel for
for (i = 0; i < max; i++)
    zero[i] = 0;
```

OpenMP 会让主线程创建其他线程，<mark>

每个线程有独立执行上下文

</mark>

。
默认情况下：

- 在 for 循环外声明的变量是 **shared，共享的**；
- 循环索引 `i` 是 **implicitly private，隐式私有的**；
- for 循环结束时有一个隐式 **barrier，同步屏障**；
- 默认按连续区间划分索引区域。

这里每个点都值得理解。

#### 1. 为什么循环索引必须 private？

如果所有线程共享同一个 `i`，那就炸了。
线程 0 改 `i`，线程 1 也改 `i`，循环控制变量会混乱。

所以 OpenMP 自动让每个线程有自己的 `i`。

> 每个线程都需要知道“我现在处理哪一个迭代”，这个状态不能被别的线程乱改。

#### 2. 为什么数组 zero 可以 shared？

因为每个线程写的是不同位置：

```c
zero[i] = 0;
```

线程 0 写 `zero[0..24]`，线程 1 写 `zero[25..49]`。
只要每个元素只被一个线程写，就没问题。

#### 3. 为什么循环结束有 barrier？

因为循环后面的代码可能依赖整个数组都已经处理完。

比如：

```c
#pragma omp parallel for
for (i = 0; i < max; i++)
    zero[i] = 0;

check(zero);
```

如果没有 barrier，某个线程还没写完，主线程就开始 `check`，结果可能错。

> 当后续代码依赖所有并行工作完成时，必须等待最慢的线程。（后面的工作可能是串行的，需要前面全部完成）

这也带来代价：如果负载不均衡，快线程要等慢线程。

---

### 第 136 页：Fork-Join 模型，必须掌握

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L10-11-Parallelism-43.webp)

OpenMP 使用 **Fork-Join Model**。

程序开始时只有一个 **master thread** 顺序执行。
遇到并行区域时：

1. master thread fork 出一组 parallel threads；
2. 多个线程同时执行；
3. 并行区结束时 join；
4. 只留下 master thread 继续顺序执行。

课件还提醒：每个并行区域都重复这个过程，并且要考虑 Amdahl 定律。

> 并行程序不是从头到尾都并行，它通常是在“串行段”和“并行段”之间切换。

这直接对应 Amdahl 定律。

另外，fork/join 本身也有开销。
所以 OpenMP 适合把**足够大的循环**并行化。
如果循环只有 10 次，每次工作量很小，开线程的成本可能比计算还大。

---

### 第 137 页：OpenMP 线程是什么

OpenMP 写出来的是软件层面的并行；最后能不能真的并行，要看操作系统把这些 OpenMP 线程映射到多少个硬件线程上。

---

### 第 138 页：例子 2：计算 π

这一页引入一个经典例子：用数值积分计算 π。

思想是利用：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

π

</mi>

<mo>

=

</mo>

<msubsup>
<mo>

∫

</mo>

<mn>

0

</mn>

<mn>

1

</mn>
</msubsup>

<mfrac>
<mn>

4

</mn>

<mrow>
<mn>

1

</mn>

<mo>

+

</mo>

<msup>
<mi>

x

</mi>

<mn>

2

</mn>
</msup>
</mrow>
</mfrac>

<mi>

d

</mi>

<mi>

x

</mi>
</mrow>

<annotation encoding="application/x-tex">

\pi = \int_0^1 \frac{4}{1+x^2} dx

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.4306em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

π

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
<span className="strut" style="height:2.476em;vertical-align:-0.9119em;">



</span>

<span className="mop">
<span className="mop,op-symbol,large-op" style="margin-right:0.4445em;position:relative;top:-0.0011em;">

∫

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:1.564em;">
<span style="top:-1.7881em;margin-left:-0.4445em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">

0

</span>
</span>
</span>

<span style="top:-3.8129em;margin-right:0.05em;">
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
<span className="vlist" style="height:0.9119em;">
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

1

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

x

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

<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal">

x

</span>
</span>
</span>
</span>
</span>

程序把区间 (<span>

0,1

</span>

) 切成很多小段，每段取一个点算函数值，再把这些值加起来。

这个问题特别适合并行，因为：

> 每个小段的函数值可以独立计算，最后只需要把结果求和。

它的并行结构是：

```text
独立计算很多项  →  最后合并求和
```

这正好引出后面的 **reduction**。

---

### 第 139 页：串行 π

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L10-11-Parallelism-44.webp)

串行版本得到：

```text
pi = 3.142425985001
```

课件说接近 π，但不够准确，所以增加 `num_steps` 并并行化。

> 数值积分的精度取决于把区间切得多细。

`num_steps` 越大，小矩形越窄，近似越准。
但 `num_steps` 越大，循环次数也越多，计算时间越长。
这就是并行化的好机会：每一步相互独立，可以分给多个线程。

---

### 第 140 页：并行化问题：共享 sum

这一页指出最关键的问题：

> 每个线程都需要访问共享变量 `sum`。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L10-11-Parallelism-45.webp)

如果天真的并行化，代码是：

```c
sum += f(i);
```

它至少分成三步：

```text
读 sum
计算 sum + f(i)
写回 sum
```

如果多个线程同时做这三步，就会出问题。

> 高级语言的一条语句，底层可能是多条指令；多个线程的这些指令可能交错执行。

这就是并行编程真正麻烦的地方：
循环里的每一项可以并行算，但共享的 sum 不能被多个线程随便同时更新

---

### 第 141 页：用多个 sum 分开算，重要

这一页给出一个简单思路：

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L10-11-Parallelism-46.webp)

并行计算：

```text
线程0：sum[0]
线程1：sum[1]
```

串行合并：

```text
sum = sum[0] + sum[1]
```

> 如果多个线程同时写同一个变量会冲突，那就让每个线程写自己的私有变量，最后再合并。

---

### 第 142 页：并行 π 试运行

第 142 页打印了类似：

```text
i = 1, id = 1
i = 0, id = 0
i = 2, id = 2
i = 3, id = 3
i = 5, id = 1
i = 4, id = 0
...
```

你会发现 `i` 的输出不是严格 0,1,2,3,4,5 的顺序。

这正是并行程序的正常现象：不同线程谁先跑、谁后跑，由操作系统调度和硬件状态决定。只要每个线程写的是自己的 `sum[id]`，结果就可以是正确的。

第 142 页最后仍然得到：

```text
pi = 3.142425985001
```

说明虽然打印顺序乱，但计算逻辑没错

---

### 第 143 页：增加 num_steps，提高精度，略中带重要

这一页把 `num_steps` 增加到 (10^6)，结果：

```text
pi = 3.141592653590
```

非常接近 π。

> 并行化让我们可以承受更多迭代，从而提高数值精度或处理更大问题。

这是弱扩展思路的影子：硬件更多时，我们不一定只追求更快，也可以追求更大、更准的问题。

---

### 第 144 页：能不能在并行区里直接求总 sum？最重要之一

这一页问：我们可以并行计算 `sum` 吗？

直接写类似：

```c
pi = pi + sum[id];
```

结果：

```text
PI = 3.138450662641
```

而且不同运行之间值会变化。课件问：这是为什么？

答案是：<mark>

**race condition，竞争条件**

</mark>

<mark>

。

</mark>



> 多个线程同时读写同一个共享变量，而最终结果依赖这些读写发生的先后顺序，就会产生不确定性。

这页非常重要，因为它从 OpenMP 编程自然过渡到下一板块“并行同步”。

---

### 第 145 页：用汇编解释 race condition

第 145 页用这个例子：

```text
# *(x1) = 100
lw   x2, 0(x1)
addi x2, x2, 1
sw   x2, 0(x1)
```

两个线程同时执行“把内存里的值加 1”。直觉上应该从 100 变成 102。

但可能发生：

```text
线程 A 读到 100
线程 B 读到 100
线程 A 算 101
线程 B 算 101
线程 A 写 101
线程 B 写 101
```

最后结果是 101，不是 102。

这叫 **lost update**。课件第 145 页就是用这个底层例子说明：高级语言里的 `x++`、`sum += value`、`pi = pi + sum[id]` 都不是天然原子的。

---

### 第 146 页：race condition 是怎么发生的，必须掌握

```text
pi = pi + sum[id]
```

如果多个线程读取同一个 `pi` 的中间值，然后分别计算、分别写回，结果取决于谁先到、谁后到。

所以结果是：

```text
not deterministic
```

也就是非确定性的。

这就是并行程序最讨厌的 bug：

它不是每次都错成同一个值，而是这次对、下次错、换台机器又不一样。

---

### 第 147 页：OpenMP Reduction，最重要

第 147 页引入 OpenMP 的 `reduction`：

```text
#pragma omp for reduction(+ : sum)
for (i = 0; i <= MAX; i++)
    sum += A[i];
```

它的意思是：

```text
每个线程都有一个私有的 sum
每个线程先算自己的部分
并行区域结束后
OpenMP 自动把所有私有 sum 用 + 合并到全局 sum
```

也就是编译器帮你做第 141 页的事情：

```text
sum = sum[0] + sum[1] + sum[2] + ...
```

但它保证不会 race。课件第 147 页明确说，reduction 会指定每个线程私有的变量，并在并行区域末端进行约简操作。

所以 reduction

> **把一个危险的共享更新，改写成“私有局部累计 + 安全合并”。**

---

### 第 148 页：手写的初始并行版本

第 148 页代码大概是：

```text
#define NUM_THREADS 4
static long num_steps = 100000;
double step;

void main() {
    int i;
    double x, pi, sum[NUM_THREADS];

    step = 1.0 / (double) num_steps;

    #pragma omp parallel private(i, x)
    {
        int id = omp_get_thread_num();

        for (i = id, sum[id] = 0.0;
             i < num_steps;
             i = i + NUM_THREADS) {

            x = (i + 0.5) * step;
            sum[id] += 4.0 / (1.0 + x * x);
        }
    }

    for (i = 1; i < NUM_THREADS; i++)
        sum[0] += sum[i];

    pi = sum[0];
}
```

它的核心是这句：

```text
for (i = id; i < num_steps; i = i + NUM_THREADS)
```

假设 4 个线程：

```text
线程 0: i = 0, 4, 8, 12, ...
线程 1: i = 1, 5, 9, 13, ...
线程 2: i = 2, 6, 10, 14, ...
线程 3: i = 3, 7, 11, 15, ...
```

每个线程写自己的：

```text
sum[id]
```

所以不会互相覆盖。最后由主线程串行合并：

```text
sum[0] += sum[1];
sum[0] += sum[2];
sum[0] += sum[3];
```

这就是手写 reduction。课件第 148 页展示的就是这种初始并行版本。

不过这里要注意一个小坑：从数学公式看，最终必须乘上 `step`。第 139 页和第 140 页代码里是：

```text
sum += 4.0 * step / (1.0 + x * x);
```

但第 148、149 页截图里写的是：

```text
sum += 4.0 / (1.0 + x * x);
pi = sum;
```

如果完全照图这样写，结果会大约是 `num_steps * π`，不是 π。正确写法应该二选一：

```text
sum[id] += 4.0 * step / (1.0 + x * x);
pi = sum[0];
```

或者：

```text
sum[id] += 4.0 / (1.0 + x * x);
pi = step * sum[0];
```

所以这里很可能是课件代码漏了 `step`，但它想讲的 OpenMP 并行结构是对的。

---

### 第 149 页：最终版本，用 parallel for + reduction

第 149 页把手写版本简化成 OpenMP 推荐写法：

```text
#pragma omp parallel for private(x) reduction(+:sum)
for (i = 1; i <= num_steps; i++) {
    x = (i - 0.5) * step;
    sum = sum + 4.0 / (1.0 + x * x);
}
pi = sum;
```

这页的重点是：

```text
#pragma omp parallel for private(x) reduction(+:sum)
```

它同时做了三件事：

```text
parallel for:
    把 for 循环的 i 分给多个线程

private(x):
    每个线程有自己的 x，避免互相覆盖

reduction(+:sum):
    每个线程有自己的局部 sum
    最后 OpenMP 自动用 + 合并
```

这就是第 148 页手写版本的自动化。课件第 149 页标题也明确写着：`parallel for, reduction`。

同样，这页数学上也应该乘 `step`：

```text
sum = sum + 4.0 * step / (1.0 + x * x);
```

或者最后：

```text
pi = step * sum;
```

---

### 最值得背的几句话

> OpenMP 是共享内存多线程并行编程模型，通过 `#pragma` 给 C 程序添加并行语义。

> `#pragma omp parallel for` 会把 for 循环迭代分配给多个线程执行。

> OpenMP 使用 fork-join 模型：master thread 遇到并行区 fork 出多个线程，并行区结束后 join。

> 循环外声明的变量默认 shared，循环索引变量默认 private。

> `sum += A[i]` 不是原子操作，多个线程同时执行会产生 race condition。

> `reduction(+:sum)` 的本质是每个线程维护私有局部和，最后自动把它们相加合并。

---

## 第 6 模块：并行同步 Synchronization

继续讲最后一板块：**第 6 模块——并行同步 Synchronization，第 150–167 页**。

> 并行程序里，多个线程会同时读写共享内存。
> 只要两个线程可能同时碰同一个位置，并且至少一个是写，就会出现“不知道谁先发生”的问题。
> 同步的目标就是：**把某些本来可能交错执行的操作，强行变成有秩序、可预测的执行。**

前面 OpenMP 讲的是“怎么把循环拆开并行跑”；这一节讲的是“拆开以后，怎么不互相踩脚”。这块非常容易考：**data race、lock、critical section、atomic/AMO、OpenMP critical、deadlock**。

---

### 第 150 页：标题页

进入 **并行同步 Synchronization**。

上一节我们看到：

```c
pi += sum[id];
```

多个线程同时执行会出错。
为什么？因为它不是一步完成的，而是：

```text
读 pi → 加 sum[id] → 写 pi
```

同步就是为了解决这种“多个线程同时更新共享状态”的问题。

---

### 第 151 页：同步的基本问题

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L10-11-Parallelism-47.webp)

从生活中引入

---

### 第 152 页：数据竞争 Data Race

这一页给出核心定义。

**Data Race，数据竞争**：

> 来自不同线程的两次内存访问访问同一个位置，至少有一次是写，并且它们没有被同步约束顺序，那么就形成数据竞争。

第一性原理：

> 程序正确性不能依赖“刚好某个线程先跑”。
> 如果结果依赖调度运气，这个程序就是不可靠的。

课件也强调：存在 data race 时，程序结果取决于机会；通过同步写入和读取可以获得确定性行为。

---

### 第 153 页：锁 Locks，必须掌握

锁是最基本的同步工具。

通常：

```text
lock = 0 表示 unlocked，没被占用
lock = 1 表示 locked，已经被占用
```

> 锁就是一个共享的标志位，用来表示“某个共享资源现在有没有主人”。

---

### 第 154 页：朴素 lock 写法，看起来对，其实有坑

这一页给出直觉上的锁：

```c
while (lock != 0) ;
lock = 1;

// critical section

lock = 0;
```

即：

```text
如果锁被别人拿着，就等；
看到锁空了，就把锁设为 1；
进入临界区；
结束后把锁设回 0。
```

这看起来非常合理，但问题藏在这两句之间：

```c
while (lock != 0) ;
lock = 1;
```

**检查 lock 是否为 0** 和 **把 lock 设为 1** 是两个动作。
只要是两个动作，中间就可能被别的线程插进来。

也就是说，“看到麦克风在桌上”和“把麦克风拿到手里”不是同一瞬间完成的。你刚看到麦克风空着，别人也看到了，然后你俩同时伸手，尴尬了。

---

### 第 155 页：为什么朴素 lock 失败

这一页用 Thread 1 和 Thread 2 说明：

```c
// Thread 1
while (lock != 0);
lock = 1;
// critical section
lock = 0;

// Thread 2
while (lock != 0);
lock = 1;
// critical section
lock = 0;
```

可能发生这样的时间线：

```text
初始 lock = 0

Thread 1 读 lock，发现是 0
Thread 2 读 lock，发现也是 0

Thread 1 执行 lock = 1
Thread 2 执行 lock = 1

Thread 1 进入 critical section
Thread 2 也进入 critical section
```

两个人都以为自己拿到了锁。
结果锁完全失效。

课件特别强调：这个问题无论怎么尝试，在普通汇编级别也没有解决方案，除非引入新的指令。

这就是本节最关键的洞察：

> 实现锁需要一个不可分割的“读 + 写”操作。
> 普通 load 和 store 分开执行，不足以实现正确的锁。

这也解释了为什么同步不是纯软件问题，<mark>

它需要硬件支持

</mark>

。

---

### 第 156 页：硬件同步 Hardware Synchronization

这一页给出解决方案：**atomic read/write，原子读写**。

原子操作：

> 一个操作在其他线程看来要么完全没发生，要么已经完全发生；中间状态不可见。

具体到锁，我们需要一种指令能做到：

```text
读出旧 lock 值 + 写入新 lock 值
```

并且中间不允许其他线程访问同一个 lock。

课件列了两类常见硬件实现：

1. **atomic swap，原子交换**
把寄存器和内存中的值原子交换。
2. **linked load / conditional store 这一类成对指令**
先“链接读取”，再尝试写入。如果中间内存位置被别人改过，写入失败。

RISC-V 两种都有变体，但课件为了简单重点讲 atomic swap。

为什么必须共享内存？

因为锁本身要被多个处理器/线程共同看到。
如果每个处理器都有自己私有的一份 lock，那就没法协调。
所以同步通常建立在共享内存多处理器之上。

---

### 第 157 页：AMO 原子存储器操作，必须理解

AMO = **Atomic Memory Operations，原子内存操作**。

课件用：

```text
amoadd.w rd, rs2, (rs1)
```

解释 AMO 的通用含义：

```text
t = M[x[rs1]]
x[rd] = t
M[x[rs1]] = t + x[rs2]
```

也就是说，它做三件事：

1. 从内存地址 `x[rs1]` 取出旧值；
2. 把旧值放到目标寄存器 `rd`；
3. 把旧值和 `rs2` 做某种操作后的结果写回内存。

重点是：这三件事是**原子的**。
别人不能插进来看到半成品。

AMO 支持多种操作：

```text
Add, And, Or, Swap, Xor, Max, Min ...
```

课件还提到 `aq` 和 `rl`，它们用来确保顺序执行。

这里稍微展开一下：

<table>
<thead>
  <tr>
    <th>
      标记
    </th>
    
    <th>
      直觉含义
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      <code code="aq">
        aq
      </code>
      
       / acquire
    </td>
    
    <td>
      拿锁之后，后面的内存操作不能乱跑到拿锁之前
    </td>
  </tr>
  
  <tr>
    <td>
      <code code="rl">
        rl
      </code>
      
       / release
    </td>
    
    <td>
      释放锁之前，临界区里的内存操作不能乱跑到释放之后
    </td>
  </tr>
</tbody>
</table>

第一性原理：

> 锁不仅要保证“只有一个线程进去”，还要保证“进去前后内存操作的顺序不要被 CPU/编译器乱重排”。

否则可能出现：你锁是拿了，但临界区里的读写顺序被优化器或硬件重排，另一个线程看到的状态仍然混乱。

---

### 第 158 页：RISC-V Critical Section，最重要

这一页给出正确的 RISC-V 锁实现。

假设：

- `lock` 在 `a0` 指向的内存地址；
- `lock = 0` 表示 free；
- `lock = 1` 表示 set / locked。

代码：

```text
li t0, 1

Try:
    amoswap.w.aq t1, t0, (a0)
    bnez t1, Try

    // critical section

    amoswap.w.rl x0, x0, (a0)
```

逐行理解：

```text
li t0, 1
```

把 1 放入 `t0`，因为我们想把 lock 设置为 1。

```text
amoswap.w.aq t1, t0, (a0)
```

这句是关键。它原子地做：

```text
t1 = 旧的 lock 值
lock = 1
```

也就是说，线程一边读取旧锁值，一边把锁设为 1，整个过程不可分割。

接着：

```text
bnez t1, Try
```

如果旧的 lock 值不是 0，说明别人已经持有锁。那就回去继续试。

如果旧 lock 是 0，说明我成功把它从 0 改成 1，我拿到锁了。

最后释放锁：

```text
amoswap.w.rl x0, x0, (a0)
```

`x0` 永远是 0，所以这相当于把 lock 写回 0，释放锁。课件的 RISC-V critical section 正是用 `amoswap.w.aq` 尝试获得锁，用 `amoswap.w.rl` 释放锁。

第一性原理总结：

> 获得锁的本质不是“看到 lock 是 0”，而是“我成功地把 lock 从 0 改成 1，并且没人能同时完成同样的事”。

这就是 atomic swap 的意义。

---

### 第 159 页：把错误 lock 修正成 AMO lock，重要

这一页把前面的错误写法和修正写法放在一起。

错误写法：

```c
while (lock != 0);
lock = 1;

// critical section

lock = 0;
```

问题是“检查”和“设置”分离。

修正写法：

```text
li t0, 1

Try:
    amoswap.w.aq t1, t0, (a0)
    bnez t1, Try

Locked:
    // critical section

Unlock:
    amoswap.w.rl x0, x0, (a0)
```

这页最值得背的句子是：

> 正确锁的 acquire 必须是原子 test-and-set / swap，而不是普通 load + store。

顺便注意：这里的 `Try` 循环是 **spin lock，自旋锁**。
线程拿不到锁时，不是睡眠，而是一直循环尝试。

自旋锁适合临界区很短的情况。
如果临界区很长，自旋会浪费 CPU：一群线程站在门口疯狂转圈，CPU 粉丝都要破防。

---

### 第 160 页：OpenMP 锁定，重要度中等

这一页从底层 RISC-V 锁回到高级语言 OpenMP。

图里代码大致是：

```c
omp_lock_t lock;
omp_init_lock(&lock);

#pragma omp parallel
{
    int id = omp_get_thread_num();

    // parallel section

    omp_set_lock(&lock);

    // start sequential section
    printf("id = %d\n", id);
    // end sequential section

    omp_unset_lock(&lock);

    // parallel section
}

omp_destroy_lock(&lock);
```

这段代码的第一性原理：

<table>
<thead>
  <tr>
    <th>
      OpenMP 函数
    </th>
    
    <th>
      作用
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      <code code="omp_lock_t lock">
        omp_lock_t lock
      </code>
    </td>
    
    <td>
      声明一个锁变量
    </td>
  </tr>
  
  <tr>
    <td>
      <code code="omp_init_lock(&lock)">
        omp_init_lock(&lock)
      </code>
    </td>
    
    <td>
      初始化锁
    </td>
  </tr>
  
  <tr>
    <td>
      <code code="omp_set_lock(&lock)">
        omp_set_lock(&lock)
      </code>
    </td>
    
    <td>
      获取锁；如果锁被占用，就等待
    </td>
  </tr>
  
  <tr>
    <td>
      <code code="omp_unset_lock(&lock)">
        omp_unset_lock(&lock)
      </code>
    </td>
    
    <td>
      释放锁
    </td>
  </tr>
  
  <tr>
    <td>
      <code code="omp_destroy_lock(&lock)">
        omp_destroy_lock(&lock)
      </code>
    </td>
    
    <td>
      销毁锁
    </td>
  </tr>
</tbody>
</table>

箭头标出的部分也很清楚：

- 锁外面是 parallel section，可以多个线程同时执行；
- `omp_set_lock` 和 `omp_unset_lock` 之间是 sequential section，也就是一次只有一个线程执行；
- 最后要 destroy lock，清理资源。

第一性原理：

> OpenMP 锁把底层硬件原子指令包装成库函数，让程序员不用手写 `amoswap`。

但代价还是存在：临界区本质上是串行的。
如果你的程序大量时间都在锁里面，就会被 Amdahl 定律卡住。

---

### 第 161 页：OpenMP 同步工具，重要

这一页列出 OpenMP 提供的更高级同步构造：

```text
critical
atomic
barrier
ordered
```

它们通常用于高级并行编程。

从第一性原理区分：

<table>
<thead>
  <tr>
    <th>
      构造
    </th>
    
    <th>
      解决什么问题
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      <code code="critical">
        critical
      </code>
    </td>
    
    <td>
      让一段代码一次只被一个线程执行
    </td>
  </tr>
  
  <tr>
    <td>
      <code code="atomic">
        atomic
      </code>
    </td>
    
    <td>
      让一次简单内存更新变成原子操作
    </td>
  </tr>
  
  <tr>
    <td>
      <code code="barrier">
        barrier
      </code>
    </td>
    
    <td>
      所有线程到齐后才能继续
    </td>
  </tr>
  
  <tr>
    <td>
      <code code="ordered">
        ordered
      </code>
    </td>
    
    <td>
      在并行循环中按原始迭代顺序执行某段代码
    </td>
  </tr>
</tbody>
</table>

举例：

```c
#pragma omp critical
{
    pi += sum[id];
}
```

保证这段一次只有一个线程进来。

```c
#pragma omp atomic
sum += x;
```

适合简单的共享变量更新。

```c
#pragma omp barrier
```

所有线程都等到这里，再一起往后走。

考试一般不会深入 `ordered`，但要知道它和顺序有关。

---

### 第 162 页：OpenMP Critical Section，最重要

这一页把上一节 π 的例子修好：

```c
#pragma omp parallel
{
    int id = omp_get_thread_num();

    for (int i = id; i < num_steps; i += NUM_THREADS) {
        double x = (i + 0.5) * step;
        sum[id] += 4.0 * step / (1.0 + x * x);
    }

    #pragma omp critical
    pi += sum[id];
}
```

这里 `sum[id]` 是每个线程自己的局部结果，所以前面的循环可以并行。
最后：

```c
pi += sum[id];
```

会更新共享变量 `pi`，因此必须保护起来。

`#pragma omp critical` 的作用是：

> 让下面这条语句同一时刻只被一个线程执行。

第一性原理：

> 临界区是把“不安全的共享写”包成“串行执行的一小段”。

不过注意一个性能点：

如果 1000 个线程都要进入 critical，最后这 1000 次 `pi += sum[id]` 还是排队执行。
所以 critical 能保证正确性，但可能牺牲并行性能。

在这个求 π 例子中，更好的写法通常是：

```c
#pragma omp parallel for reduction(+:pi)
```

因为 reduction 可以让每个线程局部累加，最后高效合并。
所以考试可以这样比较：

<table>
<thead>
  <tr>
    <th>
      方法
    </th>
    
    <th>
      正确性
    </th>
    
    <th>
      性能
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      不同步直接 <code code="pi += ...">
        pi += ...
      </code>
    </td>
    
    <td>
      错，data race
    </td>
    
    <td>
      看起来快但结果不可靠
    </td>
  </tr>
  
  <tr>
    <td>
      <code code="critical">
        critical
      </code>
    </td>
    
    <td>
      正确
    </td>
    
    <td>
      可能串行瓶颈
    </td>
  </tr>
  
  <tr>
    <td>
      <code code="reduction">
        reduction
      </code>
    </td>
    
    <td>
      正确
    </td>
    
    <td>
      通常更高效
    </td>
  </tr>
</tbody>
</table>

---

### 第 163 页：死锁的麻烦，重要

这一页用两个厨师共用厨房讲死锁。

两个厨师都需要盐和胡椒：

```text
厨师 A 拿了盐，等胡椒
厨师 B 拿了胡椒，等盐
```

结果：

```text
A 等 B 放下胡椒
B 等 A 放下盐
两个人都不动
```

这就是死锁。

第一性原理：

> 每个线程都占有一部分资源，同时等待另一个线程释放资源，导致所有人都无法前进。

课件说死锁在并行程序中是可能的，而且很难调试。

为什么难调试？

因为它依赖时机。
程序可能跑 100 次都没事，第 101 次刚好线程交错顺序变了，就卡死。
调试器一开，时序变了，bug 还可能消失。并行 bug 很会装乖。

---

### 第 164 页：Deadlock 定义与哲学家就餐问题，必须掌握

课件定义：

> Deadlock：一种不可能有任何进展的系统状态。

然后给出经典 **Dining Philosophers，用餐哲学家问题**：

每个哲学家重复：

1. 等左边叉子可用，拿起左叉；
2. 等右边叉子可用，拿起右叉；
3. 拿到两把叉子后吃饭；
4. 放下右叉；
5. 放下左叉；
6. 重复。

如果所有哲学家同时拿起左叉，就会变成：

```text
每个人手里都有左叉
每个人都在等右叉
没有人能吃饭
没有人会放下叉子
```

系统完全停止进展。

第一性原理上，死锁通常需要四个条件同时成立：

<table>
<thead>
  <tr>
    <th>
      条件
    </th>
    
    <th>
      含义
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      互斥 mutual exclusion
    </td>
    
    <td>
      资源一次只能被一个线程占用
    </td>
  </tr>
  
  <tr>
    <td>
      持有并等待 hold and wait
    </td>
    
    <td>
      拿着一个资源，同时等另一个资源
    </td>
  </tr>
  
  <tr>
    <td>
      不可抢占 no preemption
    </td>
    
    <td>
      别人不能强行抢走你持有的资源
    </td>
  </tr>
  
  <tr>
    <td>
      循环等待 circular wait
    </td>
    
    <td>
      A 等 B，B 等 C，C 又等 A
    </td>
  </tr>
</tbody>
</table>

课件没有显式列四条件，但理解这四点很有用。解决死锁，本质上就是破坏其中一个条件。

常见解决方法：

1. **固定加锁顺序**
所有人都先拿编号小的锁，再拿编号大的锁。这样不会形成循环等待。
2. **一次性申请全部资源**
要么全拿到，要么一个都不拿。
3. **try-lock + 失败释放**
拿不到第二个锁，就放下第一个，稍后重试。
4. **限制并发数量**
比如 5 个哲学家只允许 4 个同时尝试拿叉子。

考试问“如何避免哲学家就餐死锁”，答“统一资源获取顺序”最稳。

---

### 第 165 页：用 OpenMP 做矩阵乘法，重要

这一页回到矩阵乘法，用 OpenMP 并行化：

```c
// C[M][N] = A[M][P] × B[P][N]

#pragma omp parallel for private(tmp, j, k)
for (i = 0; i < M; i++) {
    for (j = 0; j < N; j++) {
        tmp = 0.0;
        for (k = 0; k < P; k++) {
            tmp += A[i][k] * B[k][j];
        }
        C[i][j] = tmp;
    }
}
```

第一性原理分析：为什么这里可以并行外层 `i`？

因为每个 `i` 对应 C 的一整行：

```text
线程 0 算 C 的某些行
线程 1 算 C 的另一些行
```

不同线程写的是不同的 `C[i][j]`，没有两个线程同时写同一个 C 元素。
因此不需要给每个 `C[i][j]` 加锁。

这是非常重要的并行编程直觉：

> 最好的同步，是通过任务划分避免同步。

如果每个线程负责不同数据区域，就没有共享写冲突。
锁不是越多越安全，锁多了性能会被串行化。

这里 `private(tmp, j, k)` 也很关键：

- `tmp` 必须 private，因为每个线程都要独立累加自己的 (C_)；
- `j`、`k` 是循环局部控制变量，也应避免线程共享造成混乱；
- `A`、`B` 是只读共享，没问题；
- `C` 是共享数组，但每个线程写不同位置，所以可以。

---

### 第 166 页：矩阵乘法还能怎么优化，重要度中等

这一页说 OpenMP 并行不是终点，还可以继续优化：

1. **编译器优化** **-O2** **/** **-O3**
减少执行指令数量，做循环优化、寄存器分配等。
2. **缓存分块 blocking**
提高 cache 命中，减少 DRAM 访问。
3. **利用 SIMD AVX 指令**
提高浮点运算率，也就是利用 DLP。

第一性原理：

> OpenMP 主要利用 MIMD/TLP，也就是多个核心并行算不同工作。
> 但单个线程内部仍然可以用 SIMD 和 cache blocking 提速。

所以完整高性能矩阵乘法通常是多层优化：

```text
线程级并行：OpenMP 分行/分块给多个核心
数据级并行：每个核心内部用 SIMD/AVX
缓存优化：blocking 提高数据复用
编译器优化：减少指令开销
```

也就是前面几章最后合体：

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

L

</mi>

<mi>

P

</mi>

<mo>

+

</mo>

<mi>

D

</mi>

<mi>

L

</mi>

<mi>

P

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

O

</mi>

<mi>

p

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

<mi>

i

</mi>

<mi>

z

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

<mo>

+

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

i

</mi>

<mi>

l

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

O

</mi>

<mi>

p

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

<mi>

i

</mi>

<mi>

z

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
</mrow>

<annotation encoding="application/x-tex">

TLP + DLP + Memory\ Optimization + Compiler\ Optimization

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

T

</span>

<span className="mord,mathnormal">

L

</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

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

<span className="mord,mathnormal" style="margin-right:0.0278em;">

D

</span>

<span className="mord,mathnormal">

L

</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

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

O

</span>

<span className="mord,mathnormal">

pt

</span>

<span className="mord,mathnormal">

imi

</span>

<span className="mord,mathnormal" style="margin-right:0.044em;">

z

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

i

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

er

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

O

</span>

<span className="mord,mathnormal">

pt

</span>

<span className="mord,mathnormal">

imi

</span>

<span className="mord,mathnormal" style="margin-right:0.044em;">

z

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
</span>
</span>
</span>
</span>

这页非常适合作为整份课件的综合题。

---

### 第 167 页：小结，重要

最后一页总结整份课件：

1. **顺序软件执行速度有限**；
2. **并行处理是获得更高性能的重要途径**；
3. **SIMD 是数据级并行**，现代高性能 CPU 基本都有，编译器部分支持；
4. **MIMD 是线程级并行**，多核处理器和操作系统支持，但单程序利用它通常需要程序员介入，比如 OpenMP；
5. **SIMD + MIMD 才能实现最大性能**；
6. **ILP 是指令级并行**，VLIW 是其中一种，在 DSP 中较常见，通用处理器中已经较少使用；
7. **同步需要硬件支持**，通常通过更高级别工具使用，同时要小心死锁。

这一页的第一性原理总结可以这样说：

> 性能来自并行，但正确性来自同步。
> 没有并行，程序慢；没有同步，程序错；同步太多，程序又会慢。
> 并行编程的艺术就是在“快”和“对”之间找平衡。

---

### 这一板块的考试抓手

<table>
<thead>
  <tr>
    <th>
      重要度
    </th>
    
    <th>
      页码
    </th>
    
    <th>
      内容
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      ★★★★★
    </td>
    
    <td>
      152
    </td>
    
    <td>
      data race 定义：同一位置、不同线程、至少一个写、无同步
    </td>
  </tr>
  
  <tr>
    <td>
      ★★★★★
    </td>
    
    <td>
      153–155
    </td>
    
    <td>
      为什么普通 <code code="while(lock)">
        while(lock)
      </code>
      
       + <code code="lock=1">
        lock=1
      </code>
      
       不能实现锁
    </td>
  </tr>
  
  <tr>
    <td>
      ★★★★★
    </td>
    
    <td>
      156–159
    </td>
    
    <td>
      原子操作、AMO、RISC-V <code code="amoswap">
        amoswap
      </code>
      
       实现锁
    </td>
  </tr>
  
  <tr>
    <td>
      ★★★★★
    </td>
    
    <td>
      162
    </td>
    
    <td>
      OpenMP <code code="critical">
        critical
      </code>
      
       保护共享更新
    </td>
  </tr>
  
  <tr>
    <td>
      ★★★★★
    </td>
    
    <td>
      163–164
    </td>
    
    <td>
      deadlock 定义、哲学家就餐、避免方法
    </td>
  </tr>
  
  <tr>
    <td>
      ★★★★☆
    </td>
    
    <td>
      160–161
    </td>
    
    <td>
      OpenMP lock / critical / atomic / barrier
    </td>
  </tr>
  
  <tr>
    <td>
      ★★★★☆
    </td>
    
    <td>
      165
    </td>
    
    <td>
      OpenMP 矩阵乘法如何避免共享写冲突
    </td>
  </tr>
  
  <tr>
    <td>
      ★★★☆☆
    </td>
    
    <td>
      166–167
    </td>
    
    <td>
      综合优化：OpenMP + blocking + SIMD
    </td>
  </tr>
</tbody>
</table>

---

### 最值得背的几句话

> Data race：不同线程访问同一内存位置，至少一个是写，并且没有同步约束顺序。

> 锁用于实现互斥，保证同一时刻只有一个线程进入临界区。

> 普通 load + store 不能正确实现锁，因为“检查锁”和“设置锁”不是原子操作。

> 正确的锁需要硬件原子指令，例如 atomic swap / AMO / test-and-set。

> `#pragma omp critical` 可以保证一段代码一次只被一个线程执行，但可能降低并行性能。

> 死锁是系统无法继续前进的状态，常见原因是线程持有一个资源并等待另一个资源，形成循环等待。

> 最好的同步往往是通过合理划分数据，避免多个线程写同一个位置。

> 高性能程序通常要同时利用 TLP/OpenMP、DLP/SIMD、cache blocking 和编译器优化。

---

## 全章总逻辑与世界观

可以把这份课件理解成一条非常清晰的主线：

> **顺序执行性能遇到极限 → 寻找程序中的并行性 → 在不同硬件层次利用并行性 → 用编程模型表达并行性 → 用同步保证并行程序正确性。**

也就是说，它不是“并行技术大杂烩”，而是在回答一个核心问题：

> **现代计算机为什么必须并行？并行到底可以从哪些层次来获得？获得之后又会引入什么新问题？**

---

### 1. 全章的第一性原理：性能来自“更多有效工作/单位时间”

最底层的问题是性能：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mtext>

性能

</mtext>

<mo>

≈

</mo>

<mfrac>
<mtext>

完成的有用工作

</mtext>

<mtext>

时间

</mtext>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

性能 \approx \frac{完成的有用工作}{时间}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,cjk_fallback">

性能

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
<span className="mord,cjk_fallback">

时间

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
<span className="mord,cjk_fallback">

完成的有用工作

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

单核时代主要靠三件事提高性能：

1. **提高主频**：一个周期更短；
2. **降低 CPI**：每条指令平均用更少周期；
3. **减少指令数**：编译器优化、算法优化。

但这三条路都有限：

- 主频受功耗和散热限制；
- 单核流水线、乱序、超标量继续加复杂度，收益递减；
- 程序本身有数据依赖、分支、内存访问，不能无限压缩。

所以课件一开始讲 Amdahl 定律，本质是在告诉你：

> **任何优化都只能作用在程序的一部分；不能被加速的部分会成为最终瓶颈。**

这就是全章的地基。后面所有 SIMD、VLIW、多核、OpenMP、同步，都是在问：
**我们还能从哪里挖出可加速的部分？**

课件第 28–29 页已经把应用程序中的并行性分成三大类：DLP 数据级并行、ILP 指令级并行、TLP 线程/任务级并行，并说明它们分别受内存带宽、数据/控制依赖、通信/同步开销限制。

---

### 2. 第 0、1 模块：提出问题，建立地图

第 0、1 模块不是技术细节，而是**全章地图**。

它做了三件事。

第一，说明为什么需要并行。
CPU 主频不能一直涨，单核越来越难靠频率和复杂度继续提升性能，所以并行处理成为继续提高速度的重要路径。

第二，用矩阵乘法建立贯穿全章的例子。
矩阵乘法非常适合当主线，因为它同时包含：

- 大量重复运算；
- 大量独立数据；
- 明显的内存访问问题；
- 可以用 SIMD 优化；
- 可以用 OpenMP 多线程优化；
- 可以用 blocking 优化 cache。

所以它不是随便选的例子，而是一个“并行优化样板间”。

第三，用 Flynn 分类和 DLP/ILP/TLP 把后面的章节排好队：

<table>
<thead>
  <tr>
    <th>
      并行类型
    </th>
    
    <th>
      第一性原理问题
    </th>
    
    <th>
      后续模块
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      DLP
    </td>
    
    <td>
      同一个操作能不能作用在多个数据上？
    </td>
    
    <td>
      数据级并行 / SIMD
    </td>
  </tr>
  
  <tr>
    <td>
      ILP
    </td>
    
    <td>
      同一个线程里的多条指令能不能重叠？
    </td>
    
    <td>
      指令级并行 / VLIW
    </td>
  </tr>
  
  <tr>
    <td>
      TLP
    </td>
    
    <td>
      多个线程/任务能不能同时推进？
    </td>
    
    <td>
      线程级并行 / 多核 / SMT
    </td>
  </tr>
</tbody>
</table>

课件第 27 页强调 SIMD 和 MIMD 是现代体系结构中最常见的并行方式，而且通常存在于同一个系统中；SPMD 则是常见编程风格：多个处理器运行同一程序，处理不同数据，并用同步原语协调。

所以第 0、1 模块的角色是：

> **告诉你为什么要并行，以及并行性大致分几层。**

---

### 3. 第 2 模块 DLP：从“一个操作一个数据”变成“一个操作多个数据”

数据级并行的第一性原理是：

> 如果很多数据要做同一种操作，就不要一条一条算，而应该把它们打包一起算。

比如：

```c
c[i] = a[i] + b[i];
```

每个 `i` 的操作相同，只是数据不同。
这就天然适合 SIMD。

所以 SIMD/AVX 的本质不是“神奇指令”，而是：

> **把多个数据 lane 放进一个宽寄存器，用一条指令同时操作这些 lane。**

这一模块先讲寄存器宽度，比如 256-bit AVX 可以放 4 个 double；然后讲 intrinsics；然后回到矩阵乘法，展示如何一次算多个 (C) 元素。

但课件没有停在“SIMD 很快”这个浅层结论，而是继续追问：

> 为什么用了 AVX 以后还远达不到理论峰值？

于是引出两个更深的瓶颈：

1. **流水线/指令依赖瓶颈**
一个累加器连续依赖自己，CPU 流水线填不满，所以需要 loop unrolling，制造多个独立累加器。
2. **内存层次瓶颈**
大矩阵时，算得快不够，数据要能及时从 cache/DRAM 喂进来，所以需要 blocking，提高数据复用。

因此 DLP 模块的真正逻辑是：

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

I

</mi>

<mi>

M

</mi>

<mi>

D

</mi>

<mo>

→

</mo>

<mtext>

向量化

</mtext>

<mo>

→

</mo>

<mtext>

发现流水线瓶颈

</mtext>

<mo>

→

</mo>

<mi>

l

</mi>

<mi>

o

</mi>

<mi>

o

</mi>

<mi>

p

</mi>

<mtext>



</mtext>

<mi>

u

</mi>

<mi>

n

</mi>

<mi>

r

</mi>

<mi>

o

</mi>

<mi>

l

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

g

</mi>

<mo>

→

</mo>

<mtext>

发现内存瓶颈

</mtext>

<mo>

→

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

<mi>

i

</mi>

<mi>

n

</mi>

<mi>

g

</mi>
</mrow>

<annotation encoding="application/x-tex">

SIMD \rightarrow 向量化 \rightarrow 发现流水线瓶颈 \rightarrow loop\ unrolling \rightarrow 发现内存瓶颈 \rightarrow blocking

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

<span className="mord,mathnormal" style="margin-right:0.0785em;">

I

</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

D

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

<span className="mord,cjk_fallback">

向量化

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

<span className="mord,cjk_fallback">

发现流水线瓶颈

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
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

oo

</span>

<span className="mord,mathnormal">

p

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal">

u

</span>

<span className="mord,mathnormal">

n

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal">

o

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

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

→

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,cjk_fallback">

发现内存瓶颈

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
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



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

in

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

g

</span>
</span>
</span>
</span>
</span>

这一模块在全章中的作用是：

> **证明“并行”不只是多核。单个核心内部也有大量数据级并行，但要受指令依赖和内存层次限制。**

---

### 4. 第 3 模块 ILP：从“数据并行”转向“指令并行”

ILP 的第一性原理是：

> 如果同一个线程中的多条指令互不依赖，就可以重叠执行。

比如：

```c
a = b + c;
d = e + f;
```

这两条没有依赖，可以并行。
但如果是：

```c
a = b + c;
d = a + f;
```

第二条依赖第一条结果，就不能随便并行。

所以 ILP 模块研究的是：

> **在一个线程内部，机器或编译器能挖出多少独立指令？**

这里出现两条路线：

<table>
<thead>
  <tr>
    <th>
      路线
    </th>
    
    <th>
      谁负责找并行？
    </th>
    
    <th>
      代表
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      硬件动态调度
    </td>
    
    <td>
      CPU 运行时找
    </td>
    
    <td>
      Superscalar
    </td>
  </tr>
  
  <tr>
    <td>
      编译器静态调度
    </td>
    
    <td>
      编译器提前安排
    </td>
    
    <td>
      VLIW
    </td>
  </tr>
</tbody>
</table>

VLIW 的第一性原理是：
既然硬件动态找并行很复杂，那就让编译器提前把多个操作打包到一条很长的指令中。

课件第 64–66 页说 VLIW 把多个操作打包到一条指令中，每个操作槽对应固定功能单元，编译器负责调度操作、保证指令内并行性并避免数据冒险。

但是这个模块后半部分又在拆 VLIW 的台：

- 分支不可预测；
- cache miss 不可预测；
- 内存访问延迟不固定；
- 编译器难以静态知道一切；
- 代码量可能爆炸。

所以 ILP 模块的逻辑是：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mtext>

单线程也有并行性

</mtext>

<mo>

→

</mo>

<mtext>

可以由硬件或编译器挖掘

</mtext>

<mo>

→

</mo>

<mi>

V

</mi>

<mi>

L

</mi>

<mi>

I

</mi>

<mi>

W

</mi>

<mtext>

把压力交给编译器

</mtext>

<mo>

→

</mo>

<mtext>

现实程序太动态

</mtext>

<mo>

→

</mo>

<mtext>

静态调度有极限

</mtext>
</mrow>

<annotation encoding="application/x-tex">

单线程也有并行性 \rightarrow 可以由硬件或编译器挖掘 \rightarrow VLIW把压力交给编译器 \rightarrow 现实程序太动态 \rightarrow 静态调度有极限

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,cjk_fallback">

单线程也有并行性

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

<span className="mord,cjk_fallback">

可以由硬件或编译器挖掘

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

<span className="mord,mathnormal" style="margin-right:0.2222em;">

V

</span>

<span className="mord,mathnormal">

L

</span>

<span className="mord,mathnormal" style="margin-right:0.0785em;">

I

</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

W

</span>

<span className="mord,cjk_fallback">

把压力交给编译器

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

<span className="mord,cjk_fallback">

现实程序太动态

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

<span className="mord,cjk_fallback">

静态调度有极限

</span>
</span>
</span>
</span>
</span>

它在全章中的角色是：

> **说明“单线程内部并行”已经被努力挖过了，但受依赖、分支、cache miss 限制，不能单靠 ILP 解决性能问题。**

这也为下一模块 TLP 铺垫：
既然一个线程内部并行性有限，那就同时跑多个线程。

---

### 5. 第 4 模块 TLP：从“一个线程更快”转向“多个线程一起跑”

TLP 的第一性原理是：

> 一个线程被数据依赖、cache miss、分支卡住时，另一个线程可能还能继续执行。
> 与其让硬件闲着，不如让多个线程共享或复制硬件资源。

这一模块从多核讲到硬件线程，再讲 SMT/Hyperthreading。

它有两个核心层次。

#### 第一层：多核

多核的本质是：

> **复制核心，让多个 PC、多个寄存器状态、多个执行路径同时推进多个指令流。**

这对应 MIMD：多个指令流，多个数据流。

#### 第二层：硬件多线程 / SMT

SMT 的本质不是复制完整核心，而是：

> **复制线程状态，复用同一个核心的执行资源。**

为什么有用？
因为超标量核心很宽，单个线程经常填不满 issue slots。SMT 用另一个线程的指令去填空位。

所以这模块的第一性原理可以概括成：

<table>
<thead>
  <tr>
    <th>
      技术
    </th>
    
    <th>
      复制了什么
    </th>
    
    <th>
      解决什么
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      多核
    </td>
    
    <td>
      复制执行核心
    </td>
    
    <td>
      真正同时跑多个线程
    </td>
  </tr>
  
  <tr>
    <td>
      硬件多线程
    </td>
    
    <td>
      复制 PC/寄存器等线程状态
    </td>
    
    <td>
      快速切换，隐藏延迟
    </td>
  </tr>
  
  <tr>
    <td>
      SMT/超线程
    </td>
    
    <td>
      多线程共享超标量资源
    </td>
    
    <td>
      填补执行槽空洞，提高吞吐
    </td>
  </tr>
</tbody>
</table>

课件第 91 页明确把改进性能总结成：提高时钟频率、降低 CPI、同时执行多个任务，并且最终要“高 (f_s)、SIMD、多并行任务”都做。

TLP 模块在全章中的角色是：

> **说明当单线程内部的 DLP/ILP 不够时，可以转向线程级并行，用多个核心或硬件线程提高吞吐。**

但它也埋下了新问题：
多个线程如果共享内存，就会产生同步和数据竞争。

这正好通向后面的 OpenMP 和同步。

---

### 6. 第 5 模块 OpenMP：从“硬件能并行”到“程序员表达并行”

前面几个模块主要是硬件视角：机器有什么能力。
OpenMP 模块切换到软件视角：

> **硬件有多个核心，不代表 C 程序会自动利用多个核心。程序员必须表达哪些部分可以并行。**

OpenMP 的第一性原理是：

> 对共享内存多核机器，用最小语法改动告诉编译器和运行时：这个循环可以拆给多个线程。

比如：

```c
#pragma omp parallel for
for (i = 0; i < N; i++)
    a[i] = 0;
```

这句话背后做的是：

1. fork 出一组线程；
2. 把循环迭代分给线程；
3. 每个线程独立执行一部分；
4. 结束时 join；
5. 必要时 barrier 等待所有线程完成。

课件第 134–136 页说明 OpenMP 是 C 扩展、多线程、共享内存并行，使用 `#pragma` 和运行时库；`parallel for` 中循环外变量默认 shared，循环索引隐式 private，循环结束有隐式 barrier，并采用 fork-join 模型。

这个模块最重要的不是 OpenMP 语法本身，而是它引出的三个软件并行核心问题：

<table>
<thead>
  <tr>
    <th>
      问题
    </th>
    
    <th>
      第一性原理
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      哪些循环能并行？
    </td>
    
    <td>
      迭代之间不能有危险依赖
    </td>
  </tr>
  
  <tr>
    <td>
      哪些变量 shared/private？
    </td>
    
    <td>
      共享变量可能被多个线程同时访问
    </td>
  </tr>
  
  <tr>
    <td>
      如何合并结果？
    </td>
    
    <td>
      局部结果需要 reduction
    </td>
  </tr>
</tbody>
</table>

所以 π 的例子很关键。
它先展示“每个小区间可以独立计算”，再展示“最后求和会产生 race”，最后引出 reduction。

OpenMP 模块在全章中的角色是：

> **把硬件线程级并行变成程序员可用的编程模型。**

但它也自然暴露出：
一旦多个线程共享变量，就需要同步。

---

### 7. 第 6 模块同步：从“并行程序跑起来”到“并行程序跑得对”

同步模块是全章的收口。

前面所有并行技术都在追求“快”。
最后这一章提醒你：

> **并行程序如果没有同步，快也可能是错的。**

同步的第一性原理是：

> 多个线程访问同一内存位置，至少一个写，并且没有确定顺序，结果就依赖调度时机。

这就是 data race。

要解决它，需要：

1. **临界区 critical section**：一次只允许一个线程进入；
2. **锁 lock**：控制进入临界区的资格；
3. **原子操作 atomic/AMO**：保证“检查并设置锁”不可分割；
4. **高级同步工具**：OpenMP `critical`、`atomic`、`barrier`；
5. **避免死锁**：不要让线程形成循环等待。

这一模块和硬件又接上了：
锁看起来是软件概念，但正确实现锁需要硬件原子指令。普通 load/store 不能保证“读锁”和“写锁”之间没人插队。

课件最后总结说：顺序软件执行速度有限，并行处理是获得更高性能的重要途径；SIMD 是数据级并行，MIMD 是线程级并行，SIMD + MIMD 实现最大性能；ILP 中 VLIW 在 DSP 中较常见但通用处理器中较少使用；同步需要硬件支持，通常用高级工具，并且要小心死锁。

所以同步模块在全章中的作用是：

> **给并行性能加上正确性约束。**

没有同步，程序可能错。
同步太多，程序又会慢。
这就是并行编程的核心张力。

---

### 8. 各模块之间的总逻辑

整份课件可以画成这样：

```text
为什么要并行？
    ↓
Amdahl 定律：并行部分越多，理论加速越高，但顺序部分限制上限
    ↓
程序中有哪些并行性？
    ↓
DLP：同一操作，多份数据 → SIMD / AVX / blocking
    ↓
ILP：同一线程，多条指令 → 流水线 / 超标量 / VLIW
    ↓
TLP：多个线程/任务 → 多核 / SMT / Hyperthreading
    ↓
程序员如何使用 TLP？
    ↓
OpenMP：parallel for / fork-join / reduction
    ↓
并行之后如何保证正确？
    ↓
同步：data race / lock / atomic / critical / deadlock
```

这条线特别顺：

- **第 0、1 模块**：提出问题，分类并行；
- **第 2、3、4 模块**：分别讲硬件层面的 DLP、ILP、TLP；
- **第 5 模块**：讲软件如何调用 TLP；
- **第 6 模块**：讲调用 TLP 后如何保证共享内存正确性。

---

### 9. 这章真正想让你形成的世界观

这章不是让你背一堆名词，而是建立一个系统观：

#### 第一，性能瓶颈会迁移

优化前，瓶颈可能是 Python 解释器。
换 C 后，瓶颈变成没有 SIMD。
用 AVX 后，瓶颈变成流水线依赖。
unroll 后，瓶颈变成 cache/memory。
OpenMP 后，瓶颈可能变成同步和内存带宽。

所以高性能优化不是“一招鲜”，而是不断问：

> 当前最稀缺的资源是什么？

是算力？寄存器？cache？内存带宽？线程数？同步时间？

#### 第二，并行有层次，不是只有多线程

同一个程序可以同时利用：

- ILP：流水线/乱序/指令调度；
- DLP：SIMD/AVX；
- TLP：OpenMP 多线程；
- Memory locality：cache blocking；
- Synchronization：保证共享数据正确。

现代高性能程序通常是这些东西叠在一起。

#### 第三，并行越强，正确性越难

串行程序中，顺序很明确：

```text
A 先发生，B 后发生
```

并行程序中，顺序变成：

```text
A 和 B 谁先发生？不知道。
```

所以要用同步人为建立顺序。
但是同步会牺牲并行性，因此真正好的并行程序不是疯狂加锁，而是：

> **尽量通过数据划分避免共享写；只有必要时才同步。**

#### 第四，全章其实围绕矩阵乘法不断升级

矩阵乘法贯穿了整个课件：

<table>
<thead>
  <tr>
    <th>
      阶段
    </th>
    
    <th>
      对矩阵乘法做了什么
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      基础模块
    </td>
    
    <td>
      用它说明性能差距和 flop 计算
    </td>
  </tr>
  
  <tr>
    <td>
      DLP
    </td>
    
    <td>
      用 AVX 一次算多个 double
    </td>
  </tr>
  
  <tr>
    <td>
      DLP 后半
    </td>
    
    <td>
      用 unrolling 和 blocking 提高吞吐和 cache 复用
    </td>
  </tr>
  
  <tr>
    <td>
      TLP/OpenMP
    </td>
    
    <td>
      把矩阵行/块分给多个线程
    </td>
  </tr>
  
  <tr>
    <td>
      同步
    </td>
    
    <td>
      说明如果不同线程写不同 C 元素，就可以避免锁
    </td>
  </tr>
  
  <tr>
    <td>
      总结
    </td>
    
    <td>
      OpenMP + SIMD + blocking 才接近真正高性能 GEMM
    </td>
  </tr>
</tbody>
</table>

所以它是全章的“实验田”。

---

### 10. 最压缩的总总结

这份课件的组织方式可以浓缩成一句话：

> **先说明顺序执行为什么到头了，再按 DLP、ILP、TLP 三个层次寻找并行性能，接着用 OpenMP 把线程级并行暴露给程序员，最后用同步解决共享内存并行带来的正确性问题。**

再更狠一点压缩：

```text
性能问题 → 并行分类 → 硬件利用并行 → 软件表达并行 → 同步保证正确
```

这就是整章的骨架。

---
