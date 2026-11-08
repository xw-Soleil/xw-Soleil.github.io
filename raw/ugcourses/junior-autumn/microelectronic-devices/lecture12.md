# Lecture 12：MOSFET 尺寸缩微

> 技术微缩与摩尔定律、短沟道效应、减小栅绝缘层电学厚度与隧穿电流

## 技术微缩与摩尔定律 | Technology Scaling & Moore's Law

### 摩尔定律

Godon Moore 在1965年总结了一个规律：

- 芯片中的器件数目每18-24个月左右会翻一倍。
- 每一代技术节点（Node）通常由最小线宽/间距定义，特征尺寸约为上一代的70%。
- 电路面积减少约2倍，有利于降低成本和提高速度。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture12-01.webp)

### 技术路线图 | **Technology Roadmap (Example)**

#### 缩微的变化趋势 | Scaling Trends

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

d

</mi>

<mi>

d

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

V_{dd}

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
</span>
</span>
</span>

 **(电源电压)** 随节点缩小而降低，以控制功耗，与此同时晶体管密度和频率持续提升。
- <span className="katex">
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

o

</mi>

<mi>

x

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

T_{ox}

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
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.1389em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

o

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
</span>
</span>
</span>

 **(氧化层厚度)** 被减小以提高 <span className="katex">
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

o

</mi>

<mi>

n

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

I_{on}

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
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0785em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
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

 并保持良好的晶体管特性。
- **性能**分类：HP (High Performance) 和 LSTP (Low Stand-by Power)。
- **技术演进**：从应变硅 (Strained Silicon) ，High-k/Metal-Gate，到湿法光刻（Wet Lithography）再到新结构（如FinFET/UTB）。

> 英文版
> 
> Vdd is reduced at each node to contain power consumption in spite of rising transistor density and frequency
> 
> Tox is reduced to raise Ion and retain good transistor behaviors
> 
> HP: High performance; LSTP: Low stand-by power

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture12-02.webp)

#### 两种性能的对比

**HP（High Performance）**是指高性能计算处理器工艺，追求极致的**运算速度**和**开关频率**。

**LSTP（Low Stand-by Power）**是指低功率待机的产品，如手机，追求极致的**低漏电流**（Low Leakage），以延长电池寿命。

> 英文版
> 
> **HP (High Performance)** refers to the process technology for high-performance computing processors, which pursues ultimate computing speed and switching frequency.
> 
> **LSTP (Low Stand-by Power)** refers to products designed for low standby power consumption, such as mobile phones, which pursue extreme low leakage current to extend battery life.

<alert type="tip">

**Trade-off**

- **阈值电压 (**<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
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

V_t

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

**) 与 漏电流 (**<span className="katex">
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

o

</mi>

<mi>

f

</mi>

<mi>

f

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

I_{off}

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

I

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.0785em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

o

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.1076em;">

f

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.1076em;">

f

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

**)**：

  - **HP** 通常具有**较低的** <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
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
  
  V_t
  
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
  
  。根据公式 <span className="katex">
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
  
  o
  
  </mi>
  
  <mi>
  
  n
  
  </mi>
  </mrow>
  </msub>
  
  <mo>
  
  ∝
  
  </mo>
  
  <mo stretchy="false">
  
  (
  
  </mo>
  
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
  
  <msup>
  <mo stretchy="false">
  
  )
  
  </mo>
  
  <mn>
  
  2
  
  </mn>
  </msup>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  I_{on} \propto (V_{dd} - V_t)^2
  
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
  <span className="vlist" style="height:0.1514em;">
  <span style="top:-2.55em;margin-left:-0.0785em;margin-right:0.05em;">
  <span className="pstrut" style="height:2.7em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size6,size3,mtight">
  <span className="mord,mtight">
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
  
  <span className="mspace" style="margin-right:0.2778em;">
  
  
  
  </span>
  
  <span className="mrel">
  
  ∝
  
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
  <span className="strut" style="height:1.0641em;vertical-align:-0.25em;">
  
  
  
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
  
  <span className="mclose">
  <span className="mclose">
  
  )
  
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
  
  ，低 <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
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
  
  V_t
  
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
  
   可以提高 <span className="katex">
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
  
  o
  
  </mi>
  
  <mi>
  
  n
  
  </mi>
  </mrow>
  </msub>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  I_{on}
  
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
  <span className="vlist" style="height:0.1514em;">
  <span style="top:-2.55em;margin-left:-0.0785em;margin-right:0.05em;">
  <span className="pstrut" style="height:2.7em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size6,size3,mtight">
  <span className="mord,mtight">
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
  
  （速度），但根据亚阈值漏电公式 <span className="katex">
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
  
  o
  
  </mi>
  
  <mi>
  
  f
  
  </mi>
  
  <mi>
  
  f
  
  </mi>
  </mrow>
  </msub>
  
  <mo>
  
  ∝
  
  </mo>
  
  <msup>
  <mn>
  
  10
  
  </mn>
  
  <mrow>
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
  
  <mi mathvariant="normal">
  
  /
  
  </mi>
  
  <mi>
  
  S
  
  </mi>
  </mrow>
  </msup>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  I_{off} \propto 10^{-V_t/S}
  
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
  
  I
  
  </span>
  
  <span className="msupsub">
  <span className="vlist-t,vlist-t2">
  <span className="vlist-r">
  <span className="vlist" style="height:0.3361em;">
  <span style="top:-2.55em;margin-left:-0.0785em;margin-right:0.05em;">
  <span className="pstrut" style="height:2.7em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size6,size3,mtight">
  <span className="mord,mtight">
  <span className="mord,mathnormal,mtight">
  
  o
  
  </span>
  
  <span className="mord,mathnormal,mtight" style="margin-right:0.1076em;">
  
  f
  
  </span>
  
  <span className="mord,mathnormal,mtight" style="margin-right:0.1076em;">
  
  f
  
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
  
  ∝
  
  </span>
  
  <span className="mspace" style="margin-right:0.2778em;">
  
  
  
  </span>
  </span>
  
  <span className="base">
  <span className="strut" style="height:0.888em;">
  
  
  
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
  <span className="vlist" style="height:0.888em;">
  <span style="top:-3.063em;margin-right:0.05em;">
  <span className="pstrut" style="height:2.7em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size6,size3,mtight">
  <span className="mord,mtight">
  <span className="mord,mtight">
  
  −
  
  </span>
  
  <span className="mord,mtight">
  <span className="mord,mathnormal,mtight" style="margin-right:0.2222em;">
  
  V
  
  </span>
  
  <span className="msupsub">
  <span className="vlist-t,vlist-t2">
  <span className="vlist-r">
  <span className="vlist" style="height:0.2963em;">
  <span style="top:-2.357em;margin-left:-0.2222em;margin-right:0.0714em;">
  <span className="pstrut" style="height:2.5em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size3,size1,mtight">
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
  <span className="vlist" style="height:0.143em;">
  <span>
  
  
  
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  
  <span className="mord,mtight">
  
  /
  
  </span>
  
  <span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">
  
  S
  
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
  
  ，这会导致 <span className="katex">
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
  
  o
  
  </mi>
  
  <mi>
  
  f
  
  </mi>
  
  <mi>
  
  f
  
  </mi>
  </mrow>
  </msub>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  I_{off}
  
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
  
  I
  
  </span>
  
  <span className="msupsub">
  <span className="vlist-t,vlist-t2">
  <span className="vlist-r">
  <span className="vlist" style="height:0.3361em;">
  <span style="top:-2.55em;margin-left:-0.0785em;margin-right:0.05em;">
  <span className="pstrut" style="height:2.7em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size6,size3,mtight">
  <span className="mord,mtight">
  <span className="mord,mathnormal,mtight">
  
  o
  
  </span>
  
  <span className="mord,mathnormal,mtight" style="margin-right:0.1076em;">
  
  f
  
  </span>
  
  <span className="mord,mathnormal,mtight" style="margin-right:0.1076em;">
  
  f
  
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
  
   指数级上升。
  - **LSTP** 采用**较高的** <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
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
  
  V_t
  
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
  
  。这牺牲了部分 <span className="katex">
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
  
  o
  
  </mi>
  
  <mi>
  
  n
  
  </mi>
  </mrow>
  </msub>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  I_{on}
  
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
  <span className="vlist" style="height:0.1514em;">
  <span style="top:-2.55em;margin-left:-0.0785em;margin-right:0.05em;">
  <span className="pstrut" style="height:2.7em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size6,size3,mtight">
  <span className="mord,mtight">
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
  
  （速度），但能将 <span className="katex">
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
  
  o
  
  </mi>
  
  <mi>
  
  f
  
  </mi>
  
  <mi>
  
  f
  
  </mi>
  </mrow>
  </msub>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  I_{off}
  
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
  
  I
  
  </span>
  
  <span className="msupsub">
  <span className="vlist-t,vlist-t2">
  <span className="vlist-r">
  <span className="vlist" style="height:0.3361em;">
  <span style="top:-2.55em;margin-left:-0.0785em;margin-right:0.05em;">
  <span className="pstrut" style="height:2.7em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size6,size3,mtight">
  <span className="mord,mtight">
  <span className="mord,mathnormal,mtight">
  
  o
  
  </span>
  
  <span className="mord,mathnormal,mtight" style="margin-right:0.1076em;">
  
  f
  
  </span>
  
  <span className="mord,mathnormal,mtight" style="margin-right:0.1076em;">
  
  f
  
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
  
   压低几个数量级，确保设备在待机时不耗电。
- **氧化层厚度 (**<span className="katex">
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

o

</mi>

<mi>

x

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

T_{ox}

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
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.1389em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

o

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
</span>
</span>
</span>

**) 与 栅极漏电**：

  - HP 使用极薄的<span className="katex">
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
  
  o
  
  </mi>
  
  <mi>
  
  x
  
  </mi>
  </mrow>
  </msub>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  T_{ox}
  
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
  <span className="vlist" style="height:0.1514em;">
  <span style="top:-2.55em;margin-left:-0.1389em;margin-right:0.05em;">
  <span className="pstrut" style="height:2.7em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size6,size3,mtight">
  <span className="mord,mtight">
  <span className="mord,mathnormal,mtight">
  
  o
  
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
  </span>
  </span>
  </span>
  
  来获得更大的栅电容 <span className="katex">
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
  
  o
  
  </mi>
  
  <mi>
  
  x
  
  </mi>
  </mrow>
  </msub>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  C_{ox}
  
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
  <span className="mord,mtight">
  <span className="mord,mathnormal,mtight">
  
  o
  
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
  </span>
  </span>
  </span>
  
  ，从而提升电流。但这会面临栅极隧穿漏电流（Gate Tunneling Leakage）的问题。
  - LSTP 适当增加 EOT 厚度（例如high K 材料），以物理上阻挡电子隧穿，减少这一部分的功耗。

</alert>

<alert type="info">

#### EOT (Equivalent Oxide Thickness, 等效SiO2氧化层厚度)

EOT 是为了在使用高介电常数（High-k）材料替代二氧化硅（<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

S

</mi>

<mi>

i

</mi>

<msub>
<mi>

O

</mi>

<mn>

2

</mn>
</msub>
</mrow>

<annotation encoding="application/x-tex">

SiO_2

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0576em;">

S

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

O

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0278em;margin-right:0.05em;">
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

）时，能有一个统一的衡量标准。

- **定义**：指产生与 High-k 绝缘层相同单位面积电容所需的 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

S

</mi>

<mi>

i

</mi>

<msub>
<mi>

O

</mi>

<mn>

2

</mn>
</msub>
</mrow>

<annotation encoding="application/x-tex">

SiO_2

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0576em;">

S

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

O

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0278em;margin-right:0.05em;">
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

 层理论物理厚度。
- **计算公式：**

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

O

</mi>

<mi>

T

</mi>

<mo>

=

</mo>

<msub>
<mi>

t

</mi>

<mrow>
<mi>

h

</mi>

<mi>

i

</mi>

<mi>

g

</mi>

<mi>

h

</mi>

<mo>

−

</mo>

<mi>

k

</mi>
</mrow>
</msub>

<mo>

⋅

</mo>

<mrow>
<mo fence="true">

(

</mo>

<mfrac>
<msub>
<mi>

ϵ

</mi>

<mrow>
<mi>

S

</mi>

<mi>

i

</mi>

<msub>
<mi>

O

</mi>

<mn>

2

</mn>
</msub>
</mrow>
</msub>

<msub>
<mi>

ϵ

</mi>

<mrow>
<mi>

h

</mi>

<mi>

i

</mi>

<mi>

g

</mi>

<mi>

h

</mi>

<mo>

−

</mo>

<mi>

k

</mi>
</mrow>
</msub>
</mfrac>

<mo fence="true">

)

</mo>
</mrow>
</mrow>

<annotation encoding="application/x-tex">

EOT = t_{high-k} \cdot \left( \frac{\epsilon_{SiO_2}}{\epsilon_{high-k}} \right)

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0576em;">

E

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

O

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

hi

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

g

</span>

<span className="mord,mathnormal,mtight">

h

</span>

<span className="mbin,mtight">

−

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

⋅

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:2.4221em;vertical-align:-0.9721em;">



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
<span className="vlist" style="height:1.1076em;">
<span style="top:-2.314em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord,mathnormal">

ϵ

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

hi

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

g

</span>

<span className="mord,mathnormal,mtight">

h

</span>

<span className="mbin,mtight">

−

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
<span className="mord,mathnormal">

ϵ

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
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

S

</span>

<span className="mord,mathnormal,mtight">

i

</span>

<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

O

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3173em;">
<span style="top:-2.357em;margin-left:-0.0278em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
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
<span className="vlist" style="height:0.143em;">
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

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.2501em;">
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
<span className="vlist" style="height:0.9721em;">
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
</alert>

#### Tox分类和对比

##### **物理（光学）厚度 | Physical Thickness**

指的是栅介质层实际的几何厚度。

物理厚度决定了**栅极泄漏电流 (Gate Leakage Current)**。物理厚度越薄，电子越容易发生直接隧穿效应，导致漏电流指数级增加。

> 英文版
> 
> It refers to the **actual geometric thickness** of the gate dielectric layer.
> 
> Physical thickness determines the **gate leakage current**.As physical thickness decreases, it becomes easier for electrons to undergo the **direct tunneling effect**, which causes the leakage current to **increase exponentially**.

##### **电学厚度 | Electrical Thickness**

是指从电学特性（主要是栅电容 <span className="katex">
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

o

</mi>

<mi>

x

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

C_{ox}

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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

o

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
</span>
</span>
</span>

）推导出的等效氧化层厚度，包括总的栅介质厚度，多晶硅栅耗尽层以及反型层厚度。

电学厚度直接决定了晶体管的**性能**，如驱动电流 (<span className="katex">
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

o

</mi>

<mi>

n

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

I_{on}

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
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0785em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
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

) 和对沟道的控制能力（抑制短沟道效应）

> 英文版
> 
> It refers to the **equivalent oxide thickness** derived from electrical characteristics, (primarily the **gate capacitance** <span className="katex">
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
> o
> 
> </mi>
> 
> <mi>
> 
> x
> 
> </mi>
> </mrow>
> </msub>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> C_{ox}
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
> <span className="mord,mathnormal" style="margin-right:0.0715em;">
> 
> C
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.1514em;">
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
> o
> 
> </span>
> 
> <span className="mord,mathnormal,mtight">
> 
> x
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
> ) which includes the total gate dielectric thickness, the poly-silicon gate depletion layer thickness, and the inversion layer thickness.
> 
> Electrical thickness directly determines **transistor performance**, such as the **drive current** (<span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msub>
> <mi>
> 
> I
> 
> </mi>
> 
> <mrow>
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
> </mrow>
> </msub>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> I_{on}
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
> <span className="mord,mathnormal" style="margin-right:0.0785em;">
> 
> I
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.1514em;">
> <span style="top:-2.55em;margin-left:-0.0785em;margin-right:0.05em;">
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
> o
> 
> </span>
> 
> <span className="mord,mathnormal,mtight">
> 
> n
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
> ) and the ability to control the channel, specifically for **suppressing short-channel effects** (SCE).

##### 对比

在传统的多晶硅栅 (Poly-Si Gate) <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

S

</mi>

<mi>

i

</mi>

<msub>
<mi>

O

</mi>

<mn>

2

</mn>
</msub>
</mrow>

<annotation encoding="application/x-tex">

SiO_2

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0576em;">

S

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

O

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0278em;margin-right:0.05em;">
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

 工艺中，电学厚度通常**大于**物理厚度，主要原因包括：

- **多晶硅耗尽效应 | Poly-depletion effect**
  - 多晶硅栅在反型时会形成耗尽层，这相当于串联了一个额外的电容，增加了等效的电学厚度。
  - 引入金属栅 (Metal-gate) 可以消除这一效应，从而减小<span className="katex">
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
  
  o
  
  </mi>
  
  <mi>
  
  x
  
  </mi>
  
  <mi>
  
  e
  
  </mi>
  </mrow>
  </msub>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  T_{oxe}
  
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
  <span className="vlist" style="height:0.1514em;">
  <span style="top:-2.55em;margin-left:-0.1389em;margin-right:0.05em;">
  <span className="pstrut" style="height:2.7em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size6,size3,mtight">
  <span className="mord,mtight">
  <span className="mord,mathnormal,mtight">
  
  o
  
  </span>
  
  <span className="mord,mathnormal,mtight">
  
  x
  
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
  </span>
  </span>
  </span>
  
  。
- **量子效应 | Quantum effect**
  - 反型层电荷并非紧贴硅表面，而是有一定的分布深度，这也会增加电学厚度。

#### 应力硅 | Strained silicon

电子和空穴的迁移率可以通过施加的机械应力从而得到提高（降低）。

应力通过改变硅晶体的晶格常数，改变了E-k关系，从而改变了有效质量和迁移率。

> 英文版
> 
> The mobility of electrons and holes can be enhanced (or reduced) through the careful application of mechanical strain.
> 
> Strain modifies the E-k relationship by altering the lattice constant of the silicon crystal, thereby changing the effective mass and carrier mobility.

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture12-03.webp)

上图中PFET提高空穴表面迁移率原理如下：（应该不会考这么深吧，只是放在这了）

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture12-04.webp)

## 短沟道效应 | Short-Channel Effect (SCE)

### 定性解释 | Qualitative Explanation of SCE

在栅极下方形成反型层之前，栅极下方的硅表面必须先被耗尽（耗尽深度为 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

W

</mi>

<mrow>
<mi>

d

</mi>

<mi>

m

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

W_{dm}

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

W

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

d

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

）。

源极和漏极的 PN 结会协助耗尽栅极下方的硅区域。

- 沟道区域内的一部分耗尽电荷是由源/漏 (S/D) 区域的电荷平衡的，而不是由栅极电荷平衡。
- **结论** <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mo>

⇒

</mo>
</mrow>

<annotation encoding="application/x-tex">

\Rightarrow

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.3669em;">



</span>

<span className="mrel">

⇒

</span>
</span>
</span>
</span>

 达到反型状态所需的栅极电荷减少（即阈值电压 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi mathvariant="normal">

∣

</mi>

<msub>
<mi>

V

</mi>

<mi>

T

</mi>
</msub>

<mi mathvariant="normal">

∣

</mi>
</mrow>

<annotation encoding="application/x-tex">

|V_T|

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord">

∣

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

<span className="mord">

∣

</span>
</span>
</span>
</span>

 降低）。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture12-05.webp)

### 阈值电压滚降 | Threshold Voltage Roll-off

<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
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

V_t

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

 随着 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

L

</mi>

<mi>

g

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

L_g

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

L

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

g

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

（栅极长度）的减小而减小。它决定了**最小可接受的** <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

L

</mi>

<mi>

g

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

L_g

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

L

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

g

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

，因为如果 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
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

V_t

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

 变得太小，关断电流 <span className="katex">
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

o

</mi>

<mi>

f

</mi>

<mi>

f

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

I_{off}

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

I

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.0785em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

o

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.1076em;">

f

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.1076em;">

f

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

 会过大。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture12-06.webp)

**为什么上图中数据是针对** <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

L

</mi>

<mi>

g

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

L_g

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

L

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

g

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

 **（栅长）绘制的，而不是** <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

L

</mi>
</mrow>

<annotation encoding="application/x-tex">

L

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
</span>
</span>
</span>

**（沟道长度）？**

<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

L

</mi>
</mrow>

<annotation encoding="application/x-tex">

L

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
</span>
</span>
</span>

 难以直接准确测量，而 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

L

</mi>

<mi>

g

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

L_g

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

L

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

g

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

 容易测量。此外，<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

L

</mi>

<mi>

g

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

L_g

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

L

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

g

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

 是制造工程师可以直接控制的物理量。

> L is difficult to measure. Lg is. Also, Lg is the quantity that manufacturing engineers can control directly.

#### **Why Does Vt Decrease with L？**

> 实际上这里是两种解释方法 你看这样对不对
> 
> 第一个是从势垒层面上看，存在两种效应：
> 
> 1. 当沟道长度 <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <mi>
> 
> L
> 
> </mi>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> L
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
> L
> 
> </span>
> </span>
> </span>
> </span>
> 
>  缩短时，源/漏区的静电场耦合增强，即便是Vds=0，Vt也会有一定程度的下降——Vt roll off产生
> 2. 对于Vds逐渐增大的情况，对于短沟道，产生了DIBL——漏致势垒降低
> 
> 第二个从具体模型去解释
> 
> 1. 耗尽层模型解释的是Vt Roll off现象，由于源漏共享耗尽区电荷 导致栅极电压只能控制矩形区域的电荷
> 2. 简单电容模型解释的就是由于外加的Vds，导致了Vt在Vds比较大的时候意外减小，同时考虑公式：<span className="katex-display">
> <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
> <semantics>
> <mrow>
> <msub>
> <mi>
> 
> V
> 
> </mi>
> 
> <mi>
> 
> t
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
> V
> 
> </mi>
> 
> <mrow>
> <mi>
> 
> t
> 
> </mi>
> 
> <mtext>
> 
> -
> 
> </mtext>
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
> n
> 
> </mi>
> 
> <mi>
> 
> g
> 
> </mi>
> </mrow>
> </msub>
> 
> <mo>
> 
> −
> 
> </mo>
> 
> <mo stretchy="false">
> 
> (
> 
> </mo>
> 
> <msub>
> <mi>
> 
> V
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
> s
> 
> </mi>
> </mrow>
> </msub>
> 
> <mo>
> 
> +
> 
> </mo>
> 
> <mn>
> 
> 0.4
> 
> </mn>
> 
> <mo stretchy="false">
> 
> )
> 
> </mo>
> 
> <mtext>
> 
> 
> 
> </mtext>
> 
> <msup>
> <mi>
> 
> e
> 
> </mi>
> 
> <mrow>
> <mo>
> 
> −
> 
> </mo>
> 
> <mi>
> 
> L
> 
> </mi>
> 
> <mi mathvariant="normal">
> 
> /
> 
> </mi>
> 
> <msub>
> <mi>
> 
> l
> 
> </mi>
> 
> <mi>
> 
> d
> 
> </mi>
> </msub>
> </mrow>
> </msup>
> 
> <mo separator="true">
> 
> ,
> 
> </mo>
> 
> <mspace linebreak="newline">
> 
> 
> 
> </mspace>
> 
> <mtext>
> 
> where
> 
> </mtext>
> 
> <msub>
> <mi>
> 
> l
> 
> </mi>
> 
> <mi>
> 
> d
> 
> </mi>
> </msub>
> 
> <mo>
> 
> ≈
> 
> </mo>
> 
> <mroot>
> <mrow>
> <msub>
> <mi>
> 
> T
> 
> </mi>
> 
> <mrow>
> <mi>
> 
> o
> 
> </mi>
> 
> <mi>
> 
> x
> 
> </mi>
> </mrow>
> </msub>
> 
> <mtext>
> 
> 
> 
> </mtext>
> 
> <msub>
> <mi>
> 
> W
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
> e
> 
> </mi>
> 
> <mi>
> 
> p
> 
> </mi>
> </mrow>
> </msub>
> 
> <mtext>
> 
> 
> 
> </mtext>
> 
> <msub>
> <mi>
> 
> X
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
> <mn>
> 
> 3
> 
> </mn>
> </mroot>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> V_t = V_{t\text{-}long} - (V_{ds} + 0.4)\, e^{-L/l_d}, \\ \text{where}\ l_d \approx \sqrt[3]{T_{ox}\, W_{dep}\, X_j}
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
> <span className="mord,mathnormal" style="margin-right:0.2222em;">
> 
> V
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.2806em;">
> <span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mathnormal,mtight">
> 
> t
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
> <span className="strut" style="height:0.9694em;vertical-align:-0.2861em;">
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
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3361em;">
> <span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
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
> t
> 
> </span>
> 
> <span className="mord,text,mtight">
> <span className="mord,mtight">
> 
> -
> 
> </span>
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
> <span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">
> 
> g
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
> <span className="mord">
> <span className="mord,mathnormal" style="margin-right:0.2222em;">
> 
> V
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3361em;">
> <span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
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
> <span className="mord,mathnormal,mtight">
> 
> s
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
> <span className="strut" style="height:1.188em;vertical-align:-0.25em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> 
> 0.4
> 
> </span>
> 
> <span className="mclose">
> 
> )
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
> e
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t">
> <span className="vlist-r">
> <span className="vlist" style="height:0.938em;">
> <span style="top:-3.113em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mtight">
> <span className="mord,mtight">
> 
> −
> 
> </span>
> 
> <span className="mord,mathnormal,mtight">
> 
> L
> 
> </span>
> 
> <span className="mord,mtight">
> 
> /
> 
> </span>
> 
> <span className="mord,mtight">
> <span className="mord,mathnormal,mtight" style="margin-right:0.0197em;">
> 
> l
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3448em;">
> <span style="top:-2.3488em;margin-left:-0.0197em;margin-right:0.0714em;">
> <span className="pstrut" style="height:2.5em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size3,size1,mtight">
> <span className="mord,mathnormal,mtight">
> 
> d
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
> <span className="vlist" style="height:0.1512em;">
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
> </span>
> 
> <span className="mspace,newline">
> 
> 
> 
> </span>
> 
> <span className="base">
> <span className="strut" style="height:0.8444em;vertical-align:-0.15em;">
> 
> 
> 
> </span>
> 
> <span className="mord,text">
> <span className="mord">
> 
> where
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
> <span className="mord,mathnormal" style="margin-right:0.0197em;">
> 
> l
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3361em;">
> <span style="top:-2.55em;margin-left:-0.0197em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mathnormal,mtight">
> 
> d
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
> ≈
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
> <span className="strut" style="height:1.24em;vertical-align:-0.3075em;">
> 
> 
> 
> </span>
> 
> <span className="mord,sqrt">
> <span className="root">
> <span className="vlist-t">
> <span className="vlist-r">
> <span className="vlist" style="height:0.6972em;">
> <span style="top:-2.875em;">
> <span className="pstrut" style="height:2.5em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size1,mtight">
> <span className="mord,mtight">
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
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.9325em;">
> <span className="svg-align" style="top:-3.2em;">
> <span className="pstrut" style="height:3.2em;">
> 
> 
> 
> </span>
> 
> <span className="mord" style="padding-left:1em;">
> <span className="mord">
> <span className="mord,mathnormal" style="margin-right:0.1389em;">
> 
> T
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.1514em;">
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
> o
> 
> </span>
> 
> <span className="mord,mathnormal,mtight">
> 
> x
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
> <span className="mspace" style="margin-right:0.1667em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> <span className="mord,mathnormal" style="margin-right:0.1389em;">
> 
> W
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
> <span className="mord,mathnormal,mtight">
> 
> e
> 
> </span>
> 
> <span className="mord,mathnormal,mtight">
> 
> p
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
> <span className="mspace" style="margin-right:0.1667em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> <span className="mord,mathnormal" style="margin-right:0.0785em;">
> 
> X
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3117em;">
> <span style="top:-2.55em;margin-left:-0.0785em;margin-right:0.05em;">
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
> 
> <span style="top:-2.8925em;">
> <span className="pstrut" style="height:3.2em;">
> 
> 
> 
> </span>
> 
> <span className="hide-tail" style="min-width:1.02em;height:1.28em;">
> <svg xmlns="http://www.w3.org/2000/svg" width="400em" height="1.28em" viewBox="0 0 400000 1296" preserveAspectRatio="xMinYMin slice">
> <path d="M263,681c0.7,0,18,39.7,52,119
> c34,79.3,68.167,158.7,102.5,238c34.3,79.3,51.8,119.3,52.5,120
> c340,-704.7,510.7,-1060.3,512,-1067
> l0 -0
> c4.7,-7.3,11,-11,19,-11
> H40000v40H1012.3
> s-271.3,567,-271.3,567c-38.7,80.7,-84,175,-136,283c-52,108,-89.167,185.3,-111.5,232
> c-22.3,46.7,-33.8,70.3,-34.5,71c-4.7,4.7,-12.3,7,-23,7s-12,-1,-12,-1
> s-109,-253,-109,-253c-72.7,-168,-109.3,-252,-110,-252c-10.7,8,-22,16.7,-34,26
> c-22,17.3,-33.3,26,-34,26s-26,-26,-26,-26s76,-59,76,-59s76,-60,76,-60z
> M1001 80h400000v40h-400000z">
> 
> 
> 
> </path>
> </svg>
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
> <span className="vlist" style="height:0.3075em;">
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
> <br />
> 
> 对于L减小——Vt roll off效应<br />
> 
> 对于<span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msub>
> <mi>
> 
> V
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
> s
> 
> </mi>
> </mrow>
> </msub>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> V_{ds}
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
> <span className="mord,mathnormal" style="margin-right:0.2222em;">
> 
> V
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3361em;">
> <span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
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
> <span className="mord,mathnormal,mtight">
> 
> s
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
> 变化——DIBL效应

##### **1 势垒理论 | Potential Barrier Concept**

当L较小时，需要更小的Vg即可将势垒降低至0.2V，即Vt更小。

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 54.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture12-07.webp" />
      </p>
    </td>
    
    
      <td style="width: 45.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture12-08.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

1. 一种解释方法是：当沟道长度 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

L

</mi>
</mrow>

<annotation encoding="application/x-tex">

L

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
</span>
</span>
</span>

 缩短时，源/漏区的静电场耦合增强(coupling这个有点抽象，这个其实和下面那个矩形边上被吃掉两个小三角讲的是一个东西，到时候可以边上画个图)，导致即使在 <span className="katex">
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

g

</mi>

<mi>

s

</mi>
</mrow>
</msub>

<mo>

=

</mo>

<mn>

0

</mn>
</mrow>

<annotation encoding="application/x-tex">

V_{gs}=0

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

V

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

g

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

 时，源极与沟道之间的**势垒高度**（Source/Channel Barrier）也已经比长沟道器件要低。

> As the channel length L scales down, the electrostatic coupling between the source and drain regions intensifies. Consequently, even at Vgs=0, the source-to-channel potential barrier is already lower than that of a long-channel device.

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture12-09.webp)

1. 还有一种解释方法：对于短沟道器件，漏极电压 <span className="katex">
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

s

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

V_{ds}

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

d

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

 的增加会进一步向下“拉低”沟道电势，使源极端的势垒进一步降低。这就是**漏致势垒降低**（DIBL, Drain-Induced Barrier Lowering）现象。

> For short-channel devices, an increase in the drain voltage <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msub>
> <mi>
> 
> V
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
> s
> 
> </mi>
> </mrow>
> </msub>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> V_{ds}
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
> <span className="mord,mathnormal" style="margin-right:0.2222em;">
> 
> V
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3361em;">
> <span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
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
> <span className="mord,mathnormal,mtight">
> 
> s
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
>  further 'pulls down' the channel potential, leading to a further reduction in the potential barrier at the source end. This is the phenomenon of Drain-Induced Barrier Lowering (DIBL).

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture12-10.webp)

##### **2 耗尽层模型 | Depletion Layer Model**

沟道越短 L 越小，源/漏 pn 结分担（balance）掉的耗尽电荷比例越大，所以栅需要提供的电荷更少，更小的 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

V

</mi>

<mi>

G

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

V_G

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
<span className="mord,mathnormal,mtight">

G

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

就能达到反型，阈值电压 <span className="katex">
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

 下降（roll-off）。

> As the channel becomes shorter (smaller L), the source/drain pn junctions “share” (balance) a larger fraction of the depletion charge. As a result, the gate needs to supply less charge, so inversion can be reached at a smaller <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msub>
> <mi>
> 
> V
> 
> </mi>
> 
> <mi>
> 
> G
> 
> </mi>
> </msub>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> V_G
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
> <span className="mord,mathnormal" style="margin-right:0.2222em;">
> 
> V
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3283em;">
> <span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mathnormal,mtight">
> 
> G
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
> , leading to a reduced threshold voltage <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msub>
> <mi>
> 
> V
> 
> </mi>
> 
> <mi>
> 
> T
> 
> </mi>
> </msub>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> V_T
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
> <span className="mord,mathnormal" style="margin-right:0.2222em;">
> 
> V
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3283em;">
> <span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mathnormal,mtight" style="margin-right:0.1389em;">
> 
> T
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
>  (i.e., <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msub>
> <mi>
> 
> V
> 
> </mi>
> 
> <mi>
> 
> T
> 
> </mi>
> </msub>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> V_T
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
> <span className="mord,mathnormal" style="margin-right:0.2222em;">
> 
> V
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3283em;">
> <span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mathnormal,mtight" style="margin-right:0.1389em;">
> 
> T
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
>  roll-off).

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture12-11.webp)

###### **一阶几何模型（First-Order Model：梯形耗尽区）**

理想长沟道：栅下耗尽区近似 **矩形**（长度L，深度<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

W

</mi>

<mrow>
<mi>

d

</mi>

<mi>

m

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

W_{dm}

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

W

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

d

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

）。

短沟道：两侧源/漏耗尽边界弯进来，使得“由栅控制的耗尽区”变成 **梯形**，底边变短为 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msup>
<mi>

L

</mi>

<mo mathvariant="normal" lspace="0em" rspace="0em">

′

</mo>
</msup>
</mrow>

<annotation encoding="application/x-tex">

L'

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.7519em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

L

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.7519em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">

′

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

（图中标出）。

矩形耗尽区面积：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

A

</mi>

<mtext>

rect

</mtext>
</msub>

<mo>

=

</mo>

<mi>

L

</mi>

<mo>

⋅

</mo>

<msub>
<mi>

W

</mi>

<mrow>
<mi>

d

</mi>

<mi>

m

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

A_{\text{rect}} = L \cdot W_{dm}

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
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,text,mtight">
<span className="mord,mtight">

rect

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

<span className="mord,mathnormal">

L

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
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.1389em;">

W

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

d

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



梯形耗尽区面积：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

A

</mi>

<mtext>

trap

</mtext>
</msub>

<mo>

=

</mo>

<mfrac>
<mrow>
<mi>

L

</mi>

<mo>

+

</mo>

<msup>
<mi>

L

</mi>

<mo mathvariant="normal" lspace="0em" rspace="0em">

′

</mo>
</msup>
</mrow>

<mn>

2

</mn>
</mfrac>

<mo>

⋅

</mo>

<msub>
<mi>

W

</mi>

<mrow>
<mi>

d

</mi>

<mi>

m

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

A_{\text{trap}} = \frac{L + L'}{2}\cdot W_{dm}

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
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,text,mtight">
<span className="mord,mtight">

trap

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
<span className="strut" style="height:1.3185em;vertical-align:-0.345em;">



</span>

<span className="mord">
<span className="mopen,nulldelimiter">



</span>

<span className="mfrac">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.9735em;">
<span style="top:-2.655em;">
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

<span className="mbin,mtight">

+

</span>

<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

L

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8278em;">
<span style="top:-2.931em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
<span className="mord,mtight">
<span className="mord,mtight">

′

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

⋅

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.1389em;">

W

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

d

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



因此，**栅需要支持的耗尽电荷比例**大致按面积比缩小：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mfrac>
<msub>
<mi>

Q

</mi>

<mrow>
<mi>

d

</mi>

<mi>

e

</mi>

<mi>

p

</mi>

<mo separator="true">

,

</mo>

<mrow>
<mi mathvariant="normal">

e

</mi>

<mi mathvariant="normal">

f

</mi>

<mi mathvariant="normal">

f

</mi>
</mrow>
</mrow>
</msub>

<msub>
<mi>

Q

</mi>

<mrow>
<mi>

d

</mi>

<mi>

e

</mi>

<mi>

p

</mi>

<mo separator="true">

,

</mo>

<mrow>
<mi mathvariant="normal">

i

</mi>

<mi mathvariant="normal">

d

</mi>

<mi mathvariant="normal">

e

</mi>

<mi mathvariant="normal">

a

</mi>

<mi mathvariant="normal">

l

</mi>
</mrow>
</mrow>
</msub>
</mfrac>

<mo>

≈

</mo>

<mfrac>
<msub>
<mi>

A

</mi>

<mtext>

trap

</mtext>
</msub>

<msub>
<mi>

A

</mi>

<mtext>

rect

</mtext>
</msub>
</mfrac>

<mo>

=

</mo>

<mfrac>
<mrow>
<mi>

L

</mi>

<mo>

+

</mo>

<msup>
<mi>

L

</mi>

<mo mathvariant="normal" lspace="0em" rspace="0em">

′

</mo>
</msup>
</mrow>

<mrow>
<mn>

2

</mn>

<mi>

L

</mi>
</mrow>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

\frac{Q_{dep,\mathrm{eff}}}{Q_{dep,\mathrm{ideal}}} \approx \frac{A_{\text{trap}}}{A_{\text{rect}}} = \frac{L + L'}{2L}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:2.3324em;vertical-align:-0.9721em;">



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
<span className="mord,mathnormal">

Q

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

<span className="mord,mathnormal,mtight">

e

</span>

<span className="mord,mathnormal,mtight">

p

</span>

<span className="mpunct,mtight">

,

</span>

<span className="mord,mtight">
<span className="mord,mathrm,mtight">

ideal

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
<span className="mord,mathnormal">

Q

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

<span className="mord,mathnormal,mtight">

e

</span>

<span className="mord,mathnormal,mtight">

p

</span>

<span className="mpunct,mtight">

,

</span>

<span className="mord,mtight">
<span className="mord,mathrm,mtight" style="margin-right:0.0778em;">

eff

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

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.9721em;">
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
<span className="mord,mathnormal">

A

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
<span className="mord,text,mtight">
<span className="mord,mtight">

rect

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
<span className="mord,mathnormal">

A

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
<span className="mord,text,mtight">
<span className="mord,mtight">

trap

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

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:2.1149em;vertical-align:-0.686em;">



</span>

<span className="mord">
<span className="mopen,nulldelimiter">



</span>

<span className="mfrac">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:1.4289em;">
<span style="top:-2.314em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord">

2

</span>

<span className="mord,mathnormal">

L

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

L

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.7519em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">

′

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
</span>
</span>
</span>
</span>

则被源/漏极分担的耗尽电荷的比例为<span className="katex">
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

<mfrac>
<mrow>
<mi>

L

</mi>

<mo>

+

</mo>

<msup>
<mi>

L

</mi>

<mo mathvariant="normal" lspace="0em" rspace="0em">

′

</mo>
</msup>
</mrow>

<mrow>
<mn>

2

</mn>

<mi>

L

</mi>
</mrow>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

1 - \frac{L + L'}{2L}

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
<span className="strut" style="height:1.3185em;vertical-align:-0.345em;">



</span>

<span className="mord">
<span className="mopen,nulldelimiter">



</span>

<span className="mfrac">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.9735em;">
<span style="top:-2.655em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">

2

</span>

<span className="mord,mathnormal,mtight">

L

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

<span className="mbin,mtight">

+

</span>

<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

L

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8278em;">
<span style="top:-2.931em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
<span className="mord,mtight">
<span className="mord,mtight">

′

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

，这就是缩减因子。

由图中的几何关系可以得到：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msup>
<mi>

L

</mi>

<mo mathvariant="normal" lspace="0em" rspace="0em">

′

</mo>
</msup>

<mo>

=

</mo>

<mi>

L

</mi>

<mo>

−

</mo>

<mn>

2

</mn>

<msub>
<mi>

r

</mi>

<mi>

j

</mi>
</msub>

<mrow>
<mo fence="true">

(

</mo>

<msqrt>
<mrow>
<mn>

1

</mn>

<mo>

+

</mo>

<mfrac>
<mrow>
<mn>

2

</mn>

<msub>
<mi>

W

</mi>

<mrow>
<mi>

d

</mi>

<mi>

m

</mi>
</mrow>
</msub>
</mrow>

<msub>
<mi>

r

</mi>

<mi>

j

</mi>
</msub>
</mfrac>
</mrow>
</msqrt>

<mo>

−

</mo>

<mn>

1

</mn>

<mo fence="true">

)

</mo>
</mrow>
</mrow>

<annotation encoding="application/x-tex">

L' = L - 2r_j\left(\sqrt{1 + \frac{2W_{dm}}{r_j}} - 1\right)

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.7519em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

L

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.7519em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">

′

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
<span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">



</span>

<span className="mord,mathnormal">

L

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
<span className="strut" style="height:1.84em;vertical-align:-0.6791em;">



</span>

<span className="mord">

2

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0278em;margin-right:0.05em;">
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

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="minner">
<span className="mopen,delimcenter" style="top:0em;">
<span className="delimsizing,size2">

(

</span>
</span>

<span className="mord,sqrt">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:1.1609em;">
<span className="svg-align" style="top:-3.8em;">
<span className="pstrut" style="height:3.8em;">



</span>

<span className="mord" style="padding-left:1em;">
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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

r

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3281em;">
<span style="top:-2.357em;margin-left:-0.0278em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
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
<span className="vlist" style="height:0.2819em;">
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

2

</span>

<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.1389em;">

W

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3448em;">
<span style="top:-2.3488em;margin-left:-0.1389em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

d

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
<span className="vlist" style="height:0.1512em;">
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

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.5423em;">
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

<span style="top:-3.1209em;">
<span className="pstrut" style="height:3.8em;">



</span>

<span className="hide-tail" style="min-width:1.02em;height:1.88em;">
<svg xmlns="http://www.w3.org/2000/svg" width="400em" height="1.88em" viewBox="0 0 400000 1944" preserveAspectRatio="xMinYMin slice">
<path d="M983 90
l0 -0
c4,-6.7,10,-10,18,-10 H400000v40
H1013.1s-83.4,268,-264.1,840c-180.7,572,-277,876.3,-289,913c-4.7,4.7,-12.7,7,-24,7
s-12,0,-12,0c-1.3,-3.3,-3.7,-11.7,-7,-25c-35.3,-125.3,-106.7,-373.3,-214,-744
c-10,12,-21,25,-33,39s-32,39,-32,39c-6,-5.3,-15,-14,-27,-26s25,-30,25,-30
c26.7,-32.7,52,-63,76,-91s52,-60,52,-60s208,722,208,722
c56,-175.3,126.3,-397.3,211,-666c84.7,-268.7,153.8,-488.2,207.5,-658.5
c53.7,-170.3,84.5,-266.8,92.5,-289.5z
M1001 80h400000v40h-400000z">



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
<span className="vlist" style="height:0.6791em;">
<span>



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

<span className="mord">

1

</span>

<span className="mclose,delimcenter" style="top:0em;">
<span className="delimsizing,size2">

)

</span>
</span>
</span>
</span>
</span>
</span>



![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture12-12.webp)

在一阶几何模型的条件下，计算出阈值电压<span className="katex">
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

的下降量为：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mrow>
<mo fence="true">

∣

</mo>

<msub>
<mi>

V

</mi>

<mi>

T

</mi>
</msub>

<mo fence="true">

∣

</mo>
</mrow>

<mo>

−

</mo>

<mrow>
<mo fence="true">

∣

</mo>

<msub>
<mi>

V

</mi>

<mrow>
<mi>

T

</mi>

<mo stretchy="false">

(

</mo>

<mtext>

long-channel

</mtext>

<mo stretchy="false">

)

</mo>
</mrow>
</msub>

<mo fence="true">

∣

</mo>
</mrow>

<mo>

≡

</mo>

<mi mathvariant="normal">

Δ

</mi>

<msub>
<mi>

V

</mi>

<mi>

T

</mi>
</msub>

<mo>

=

</mo>

<mo>

−

</mo>

<mfrac>
<mrow>
<mi>

q

</mi>

<msub>
<mi>

N

</mi>

<mi>

A

</mi>
</msub>

<msub>
<mi>

W

</mi>

<mrow>
<mi>

d

</mi>

<mi>

m

</mi>
</mrow>
</msub>
</mrow>

<msub>
<mi>

C

</mi>

<mrow>
<mi>

o

</mi>

<mi>

x

</mi>

<mi>

e

</mi>
</mrow>
</msub>
</mfrac>

<mo>

⋅

</mo>

<mfrac>
<msub>
<mi>

r

</mi>

<mi>

j

</mi>
</msub>

<mi>

L

</mi>
</mfrac>

<mrow>
<mo fence="true">

(

</mo>

<msqrt>
<mrow>
<mn>

1

</mn>

<mo>

+

</mo>

<mfrac>
<mrow>
<mn>

2

</mn>

<msub>
<mi>

W

</mi>

<mrow>
<mi>

d

</mi>

<mi>

m

</mi>
</mrow>
</msub>
</mrow>

<msub>
<mi>

r

</mi>

<mi>

j

</mi>
</msub>
</mfrac>
</mrow>
</msqrt>

<mo>

−

</mo>

<mn>

1

</mn>

<mo fence="true">

)

</mo>
</mrow>
</mrow>

<annotation encoding="application/x-tex">

\left|V_T\right| - \left|V_{T(\text{long-channel})}\right| \equiv \Delta V_T = -\frac{q N_A W_{dm}}{C_{oxe}} \cdot \frac{r_j}{L} \left(\sqrt{1 + \frac{2W_{dm}}{r_j}} - 1\right)

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="minner">
<span className="mopen,delimcenter" style="top:0em;">

∣

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

<span className="mclose,delimcenter" style="top:0em;">

∣

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
<span className="strut" style="height:1.2052em;vertical-align:-0.3552em;">



</span>

<span className="minner">
<span className="mopen">
<span className="delimsizing,mult">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.85em;">
<span style="top:-2.85em;">
<span className="pstrut" style="height:3.2em;">



</span>

<span style="width:0.333em;height:1.2em;">
<svg xmlns="http://www.w3.org/2000/svg" width="0.333em" height="1.2em" viewBox="0 0 333 1200">
<path d="M145 15 v585 v0 v585 c2.667,10,9.667,15,21,15
c10,0,16.667,-5,20,-15 v-585 v0 v-585 c-2.667,-10,-9.667,-15,-21,-15
c-10,0,-16.667,5,-20,15z M188 15 H145 v585 v0 v585 h43z">



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
<span className="vlist" style="height:0.35em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.2222em;">

V

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3448em;">
<span style="top:-2.5198em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.1389em;">

T

</span>

<span className="mopen,mtight">

(

</span>

<span className="mord,text,mtight">
<span className="mord,mtight">

long-channel

</span>
</span>

<span className="mclose,mtight">

)

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
<span className="vlist" style="height:0.3552em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>

<span className="mclose">
<span className="delimsizing,mult">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.85em;">
<span style="top:-2.85em;">
<span className="pstrut" style="height:3.2em;">



</span>

<span style="width:0.333em;height:1.2em;">
<svg xmlns="http://www.w3.org/2000/svg" width="0.333em" height="1.2em" viewBox="0 0 333 1200">
<path d="M145 15 v585 v0 v585 c2.667,10,9.667,15,21,15
c10,0,16.667,-5,20,-15 v-585 v0 v-585 c-2.667,-10,-9.667,-15,-21,-15
c-10,0,-16.667,5,-20,15z M188 15 H145 v585 v0 v585 h43z">



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
<span className="vlist" style="height:0.35em;">
<span>



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

≡

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">

Δ

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

−

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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

o

</span>

<span className="mord,mathnormal,mtight">

x

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
<span className="mord,mathnormal" style="margin-right:0.0359em;">

q

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
<span className="mord,mathnormal,mtight">

A

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
<span className="mord,mathnormal" style="margin-right:0.1389em;">

W

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

d

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

⋅

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:3.078em;vertical-align:-1.25em;">



</span>

<span className="mord">
<span className="mopen,nulldelimiter">



</span>

<span className="mfrac">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:1.1076em;">
<span style="top:-2.314em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

L

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
<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0278em;margin-right:0.05em;">
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

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="minner">
<span className="mopen,delimcenter" style="top:0em;">
<span className="delimsizing,size4">

(

</span>
</span>

<span className="mord,sqrt">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:1.828em;">
<span className="svg-align" style="top:-5em;">
<span className="pstrut" style="height:5em;">



</span>

<span className="mord" style="padding-left:1em;">
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
<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0278em;margin-right:0.05em;">
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
<span className="mord,mathnormal" style="margin-right:0.1389em;">

W

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

d

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

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.9721em;">
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

<span style="top:-3.788em;">
<span className="pstrut" style="height:5em;">



</span>

<span className="hide-tail" style="min-width:1.02em;height:3.08em;">
<svg xmlns="http://www.w3.org/2000/svg" width="400em" height="3.08em" viewBox="0 0 400000 3240" preserveAspectRatio="xMinYMin slice">
<path d="M473,2793
c339.3,-1799.3,509.3,-2700,510,-2702 l0 -0
c3.3,-7.3,9.3,-11,18,-11 H400000v40H1017.7
s-90.5,478,-276.2,1466c-185.7,988,-279.5,1483,-281.5,1485c-2,6,-10,9,-24,9
c-8,0,-12,-0.7,-12,-2c0,-1.3,-5.3,-32,-16,-92c-50.7,-293.3,-119.7,-693.3,-207,-1200
c0,-1.3,-5.3,8.7,-16,30c-10.7,21.3,-21.3,42.7,-32,64s-16,33,-16,33s-26,-26,-26,-26
s76,-153,76,-153s77,-151,77,-151c0.7,0.7,35.7,202,105,604c67.3,400.7,102,602.7,104,
606zM1001 80h400000v40H1017.7z">



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
<span className="vlist" style="height:1.212em;">
<span>



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

<span className="mord">

1

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

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture12-13.webp)

<alert type="tip">

减小<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi mathvariant="normal">

Δ

</mi>

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

\Delta V_T

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">

Δ

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

的方法：

1. **减小** <span className="katex">
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

o

</mi>

<mi>

x

</mi>

<mi>

e

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

T_{oxe}

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
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.1389em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

o

</span>

<span className="mord,mathnormal,mtight">

x

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
</span>
</span>
</span>

（更薄栅氧 / 更大 <span className="katex">
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

o

</mi>

<mi>

x

</mi>

<mi>

e

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

C_{oxe}

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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

o

</span>

<span className="mord,mathnormal,mtight">

x

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
</span>
</span>
</span>

），栅对沟道势垒控制增强，弱化源漏的控制。
2. **减小** <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

r

</mi>

<mi>

j

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

r_j

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.7167em;vertical-align:-0.2861em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0278em;margin-right:0.05em;">
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

（做浅结、浅源漏），源漏耗尽区更不容易向栅下延伸，电荷共享减弱。
3. **增大** <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

N

</mi>

<mi>

A

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

N_A

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
<span className="mord,mathnormal,mtight">

A

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

（提高沟道/衬底掺杂），耗尽层更“薄”（<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

W

</mi>

<mrow>
<mi>

d

</mi>

<mi>

m

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

W_{dm}

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

W

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

d

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

 变小），共享空间变小。

但 trade-off：**degraded μ, m**

- m（指体效应/亚阈值因子）变差，亚阈值摆幅变差
- μ（迁移率）因杂质散射降低，驱动电流可能下降

</alert>

###### **漏源延伸区 | Source and Drain extensions****——改进方法**

想减小短沟道效应（SCE）就要浅源漏（<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

r

</mi>

<mi>

j

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

r_j

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.7167em;vertical-align:-0.2861em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0278em;margin-right:0.05em;">
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

小），但浅源漏会导致 **源/漏寄生串联电阻变大。**<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

R

</mi>

<mo>

=

</mo>

<mi>

ρ

</mi>

<mfrac>
<mi>

L

</mi>

<mi>

A

</mi>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

R=\rho \frac{L}{A}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0077em;">

R

</span>

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

<span className="mord,mathnormal">

ρ

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

A

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

，等效截面积小了

所以工程上用 **S/D extensions（浅延伸区）** 进行折中。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture12-14.webp)

**靠近沟道处**做一个较浅的 S/D 延伸区（有效减小“靠近栅边缘”的 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

r

</mi>

<mi>

j

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

r_j

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.7167em;vertical-align:-0.2861em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0278em;margin-right:0.05em;">
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

，抑制 SCE）。

**远离沟道处**仍保持更深/更低电阻的重掺杂源漏，以免整体片电阻/串联电阻过大。

> Create a shallower source/drain (S/D) extension region near the channel (effectively reducing the local <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msub>
> <mi>
> 
> r
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
> r_j
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:0.7167em;vertical-align:-0.2861em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> <span className="mord,mathnormal" style="margin-right:0.0278em;">
> 
> r
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3117em;">
> <span style="top:-2.55em;margin-left:-0.0278em;margin-right:0.05em;">
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
>  near the gate edge, thereby suppressing short-channel effects, SCE).
> 
> Farther away from the channel, keep the source/drain heavily doped and deeper (lower resistance) so that the overall sheet resistance/series resistance does not become too large.

##### 3 简单电容模型 | **Simple Capacitance Model**

<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

C

</mi>

<mi>

d

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

C_d

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
<span className="mord,mathnormal,mtight">

d

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

描述的是沟道到漏的静电耦合，当沟道长度减小时，漏到沟道距离减小，因而<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

C

</mi>

<mi>

d

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

C_d

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
<span className="mord,mathnormal,mtight">

d

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

增加。

> As the channel length is reduced, drain to channel distance is reduced→ Cd increases

从电路图中可以看出，漏极电压对于沟道电势与栅极电压起到类似的作用，Vds 和 Vgs 共同决定沟道势垒的高度。当 Vds 存在时，需要更小的 Vgs 将势垒拉低，因而 Vt 会降低。

Vt下降的公式：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

V

</mi>

<mi>

t

</mi>
</msub>

<mo>

=

</mo>

<msub>
<mi>

V

</mi>

<mrow>
<mi>

t

</mi>

<mtext>

-

</mtext>

<mi>

l

</mi>

<mi>

o

</mi>

<mi>

n

</mi>

<mi>

g

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

d

</mi>

<mi>

s

</mi>
</mrow>
</msub>

<mo>

⋅

</mo>

<mfrac>
<msub>
<mi>

C

</mi>

<mi>

d

</mi>
</msub>

<msub>
<mi>

C

</mi>

<mrow>
<mi>

o

</mi>

<mi>

x

</mi>

<mi>

e

</mi>
</mrow>
</msub>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

V_t = V_{t\text{-}long} - V_{ds}\cdot \frac{C_d}{C_{oxe}}

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

t

</span>

<span className="mord,text,mtight">
<span className="mord,mtight">

-

</span>
</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal,mtight">

o

</span>

<span className="mord,mathnormal,mtight">

n

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

g

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
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

d

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

⋅

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.3393em;vertical-align:-0.4451em;">



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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0715em;">

C

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1645em;">
<span style="top:-2.357em;margin-left:-0.0715em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

o

</span>

<span className="mord,mathnormal,mtight">

x

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
<span className="vlist" style="height:0.143em;">
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
<span className="mord,mathnormal,mtight">

d

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
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.4451em;">
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



由于**N⁻沟道 与 N⁺ 源/漏之间存在内建电势（built-in potential）**，所以帮助实现反型的电压不只是外加的 <span className="katex">
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

S

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

V_{DS}

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

<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

S

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

，还要加上大约 0.4 V 的内建项：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<msub>
<mi>

V

</mi>

<mi>

t

</mi>
</msub>

<mo>

=

</mo>

<msub>
<mi>

V

</mi>

<mrow>
<mi>

t

</mi>

<mtext>

-

</mtext>

<mi>

l

</mi>

<mi>

o

</mi>

<mi>

n

</mi>

<mi>

g

</mi>
</mrow>
</msub>

<mo>

−

</mo>

<mo stretchy="false">

(

</mo>

<msub>
<mi>

V

</mi>

<mrow>
<mi>

d

</mi>

<mi>

s

</mi>
</mrow>
</msub>

<mo>

+

</mo>

<mn>

0.4

</mn>

<mo stretchy="false">

)

</mo>

<mo>

⋅

</mo>

<mfrac>
<msub>
<mi>

C

</mi>

<mi>

d

</mi>
</msub>

<msub>
<mi>

C

</mi>

<mrow>
<mi>

o

</mi>

<mi>

x

</mi>

<mi>

e

</mi>
</mrow>
</msub>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

V_t = V_{t\text{-}long} - (V_{ds} + 0.4)\cdot \frac{C_d}{C_{oxe}}

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

t

</span>

<span className="mord,text,mtight">
<span className="mord,mtight">

-

</span>
</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal,mtight">

o

</span>

<span className="mord,mathnormal,mtight">

n

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

g

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

−

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

d

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

0.4

</span>

<span className="mclose">

)

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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

o

</span>

<span className="mord,mathnormal,mtight">

x

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
<span className="mord,mathnormal,mtight">

d

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

2D Poisson 方程的解显示 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

C

</mi>

<mi>

d

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

C_d

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
<span className="mord,mathnormal,mtight">

d

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

 是 L 的指数函数，因此上式可以改写为：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<msub>
<mi>

V

</mi>

<mi>

t

</mi>
</msub>

<mo>

=

</mo>

<msub>
<mi>

V

</mi>

<mrow>
<mi>

t

</mi>

<mtext>

-

</mtext>

<mi>

l

</mi>

<mi>

o

</mi>

<mi>

n

</mi>

<mi>

g

</mi>
</mrow>
</msub>

<mo>

−

</mo>

<mo stretchy="false">

(

</mo>

<msub>
<mi>

V

</mi>

<mrow>
<mi>

d

</mi>

<mi>

s

</mi>
</mrow>
</msub>

<mo>

+

</mo>

<mn>

0.4

</mn>

<mo stretchy="false">

)

</mo>

<mtext>



</mtext>

<msup>
<mi>

e

</mi>

<mrow>
<mo>

−

</mo>

<mi>

L

</mi>

<mi mathvariant="normal">

/

</mi>

<msub>
<mi>

l

</mi>

<mi>

d

</mi>
</msub>
</mrow>
</msup>

<mo separator="true">

,

</mo>

<mspace linebreak="newline">



</mspace>

<mi>

w

</mi>

<mi>

h

</mi>

<mi>

e

</mi>

<mi>

r

</mi>

<mi>

e

</mi>

<mtext>



</mtext>

<msub>
<mi>

l

</mi>

<mi>

d

</mi>
</msub>

<mo>

≈

</mo>

<mroot>
<mrow>
<msub>
<mi>

T

</mi>

<mrow>
<mi>

o

</mi>

<mi>

x

</mi>
</mrow>
</msub>

<mtext>



</mtext>

<msub>
<mi>

W

</mi>

<mrow>
<mi>

d

</mi>

<mi>

e

</mi>

<mi>

p

</mi>
</mrow>
</msub>

<mtext>



</mtext>

<msub>
<mi>

X

</mi>

<mi>

j

</mi>
</msub>
</mrow>

<mn>

3

</mn>
</mroot>
</mrow>

<annotation encoding="application/x-tex">

V_t = V_{t\text{-}long} - (V_{ds} + 0.4)\, e^{-L/l_d}, \\where\ l_d \approx \sqrt[3]{T_{ox}\, W_{dep}\, X_j}

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

t

</span>

<span className="mord,text,mtight">
<span className="mord,mtight">

-

</span>
</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal,mtight">

o

</span>

<span className="mord,mathnormal,mtight">

n

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

g

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

−

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

d

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.188em;vertical-align:-0.25em;">



</span>

<span className="mord">

0.4

</span>

<span className="mclose">

)

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

e

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.938em;">
<span style="top:-3.113em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">

−

</span>

<span className="mord,mathnormal,mtight">

L

</span>

<span className="mord,mtight">

/

</span>

<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0197em;">

l

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3448em;">
<span style="top:-2.3488em;margin-left:-0.0197em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
<span className="mord,mathnormal,mtight">

d

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
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

<span className="mpunct">

,

</span>
</span>

<span className="mspace,newline">



</span>

<span className="base">
<span className="strut" style="height:0.8444em;vertical-align:-0.15em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0269em;">

w

</span>

<span className="mord,mathnormal">

h

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

er

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mspace">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.0197em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

d

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

≈

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.24em;vertical-align:-0.3075em;">



</span>

<span className="mord,sqrt">
<span className="root">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.6972em;">
<span style="top:-2.875em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size6,size1,mtight">
<span className="mord,mtight">
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

<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.9325em;">
<span className="svg-align" style="top:-3.2em;">
<span className="pstrut" style="height:3.2em;">



</span>

<span className="mord" style="padding-left:1em;">
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

o

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

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.1389em;">

W

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

d

</span>

<span className="mord,mathnormal,mtight">

e

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

<span style="top:-2.8925em;">
<span className="pstrut" style="height:3.2em;">



</span>

<span className="hide-tail" style="min-width:1.02em;height:1.28em;">
<svg xmlns="http://www.w3.org/2000/svg" width="400em" height="1.28em" viewBox="0 0 400000 1296" preserveAspectRatio="xMinYMin slice">
<path d="M263,681c0.7,0,18,39.7,52,119
c34,79.3,68.167,158.7,102.5,238c34.3,79.3,51.8,119.3,52.5,120
c340,-704.7,510.7,-1060.3,512,-1067
l0 -0
c4.7,-7.3,11,-11,19,-11
H40000v40H1012.3
s-271.3,567,-271.3,567c-38.7,80.7,-84,175,-136,283c-52,108,-89.167,185.3,-111.5,232
c-22.3,46.7,-33.8,70.3,-34.5,71c-4.7,4.7,-12.3,7,-23,7s-12,-1,-12,-1
s-109,-253,-109,-253c-72.7,-168,-109.3,-252,-110,-252c-10.7,8,-22,16.7,-34,26
c-22,17.3,-33.3,26,-34,26s-26,-26,-26,-26s76,-59,76,-59s76,-60,76,-60z
M1001 80h400000v40h-400000z">



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
<span className="vlist" style="height:0.3075em;">
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

这里的<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

X

</mi>

<mi>

j

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

X_j

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

指的是漏区的结深

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture12-15.webp)

### 沟道方向电场分布 | Electric Field Along Channel

MOSFET 沟道内的横向电场在漏端最强，并且短沟道/高<span className="katex">
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

S

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

V_{DS}

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

<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

S

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

时会出现非常尖的峰值，甚至可以高达<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi mathvariant="script">

E

</mi>

<mtext>

peak

</mtext>
</msub>

<mo>

=

</mo>

<msup>
<mn>

10

</mn>

<mn>

6

</mn>
</msup>

<mi>

V

</mi>

<mi mathvariant="normal">

/

</mi>

<mi>

c

</mi>

<mi>

m

</mi>
</mrow>

<annotation encoding="application/x-tex">

\mathcal{E}_{\text{peak}} = 10^6 V/cm

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9694em;vertical-align:-0.2861em;">



</span>

<span className="mord">
<span className="mord,mathcal" style="margin-right:0.0894em;">

E

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.0894em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,text,mtight">
<span className="mord,mtight">

peak

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
<span className="strut" style="height:1.0641em;vertical-align:-0.25em;">



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

<span className="mord,mathnormal" style="margin-right:0.2222em;">

V

</span>

<span className="mord">

/

</span>

<span className="mord,mathnormal">

c

</span>

<span className="mord,mathnormal">

m

</span>
</span>
</span>
</span>

。

**在较大** <span className="katex">
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

S

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

V_{DS}

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

<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

S

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

**（接近/进入饱和）时**，漏端附近会出现 **pinch-off（夹断区）/强电势突降区域**：电势在很短距离内掉很多，于是在漏端形成了很高的电场峰值。

> At larger<span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msub>
> <mi>
> 
> V
> 
> </mi>
> 
> <mrow>
> <mi>
> 
> D
> 
> </mi>
> 
> <mi>
> 
> S
> 
> </mi>
> </mrow>
> </msub>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> V_{DS}
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
> <span className="mord,mathnormal" style="margin-right:0.2222em;">
> 
> V
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3283em;">
> <span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mtight">
> <span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">
> 
> D
> 
> </span>
> 
> <span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">
> 
> S
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
> (near or in saturation), a pinch-off region (strong potential drop region) forms near the drain: the potential drops significantly over a very short distance, producing a very high peak electric field at the drain end.

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture12-16.webp)

#### 高电场带来的问题

1. **撞击电离 | impact ionization**

在漏端强电场区，载流子（电子/空穴）会被加速到高能；

高能载流子撞击晶格，产生 e–h 对（电离）：

- 电子多数被漏端收集；
- 空穴可能注入衬底/流向衬底接触，形成 **substrate current（衬底电流）**。

常见后果：额外漏端电流、寄生效应增强、可靠性变差（也常与热载流子效应相关联）。

1. **栅氧/界面/体区损伤 | damage to gate-oxide interface and bulk**

高能“热载流子”可能注入到氧化层或在 Si/SiO2 界面产生陷阱；

长期会导致：阈值漂移、迁移率下降、跨导下降、漏电上升、器件老化等可靠性问题。

### 轻掺杂漏极结构

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture12-17.webp)

1. Lower pn junction doping results in **lower peak E-field**（好处）
把漏端靠近沟道处的结（pn 结）做得更轻掺杂，可以把电势下降拉长，从而降低局部最大电场峰值。
2. **Hot-carrier** effects reduced（好处）
当漏端峰值电场很大时，沟道末端的载流子会被强烈加速，变成“热载流子（hot carriers）”。而LDD 把漏端峰值电场压低，所以热载流子效应会明显减轻。
3. **Series resistance** increased（代价）
n− 延伸区**掺杂更轻，导致电阻率更高**，而且它又位于电流路径上（沟道—漏极之间），所以等效上会多出一段 **源/漏串联电阻。**

### 寄生源漏电阻 | **Parasitic Source-Drain Resistance**

器件越缩小，寄生电阻<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

R

</mi>

<mi>

s

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

R_s

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0077em;">

R

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0077em;margin-right:0.05em;">
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

占比越高，<span className="katex">
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

D

</mi>

<mi>

s

</mi>

<mi>

a

</mi>

<mi>

t

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

I_{Dsat}

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
<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

D

</span>

<span className="mord,mathnormal,mtight">

s

</span>

<span className="mord,mathnormal,mtight">

a

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

越小，0.1 µm MOSFET 里 <span className="katex">
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

D

</mi>

<mi>

s

</mi>

<mi>

a

</mi>

<mi>

t

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

I_{Dsat}

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
<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

D

</span>

<span className="mord,mathnormal,mtight">

s

</span>

<span className="mord,mathnormal,mtight">

a

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

 约降 15%。

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

i

</mi>

<mi>

f

</mi>

<mtext>



</mtext>

<msub>
<mi>

I

</mi>

<mrow>
<mi>

D

</mi>

<mi>

s

</mi>

<mi>

a

</mi>

<mi>

t

</mi>

<mn>

0

</mn>
</mrow>
</msub>

<mo>

∝

</mo>

<mo stretchy="false">

(

</mo>

<msub>
<mi>

V

</mi>

<mrow>
<mi>

G

</mi>

<mi>

S

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

T

</mi>
</msub>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

if \ I_{Dsat0}∝(V_{GS}−V_T)

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal" style="margin-right:0.1076em;">

f

</span>

<span className="mspace">



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

D

</span>

<span className="mord,mathnormal,mtight">

s

</span>

<span className="mord,mathnormal,mtight">

a

</span>

<span className="mord,mathnormal,mtight">

t

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

∝

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
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

GS

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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



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
<msub>
<mi>

I

</mi>

<mrow>
<mi>

D

</mi>

<mi>

s

</mi>

<mi>

a

</mi>

<mi>

t

</mi>
</mrow>
</msub>

<mo>

=

</mo>

<mfrac>
<msub>
<mi>

I

</mi>

<mrow>
<mi>

D

</mi>

<mi>

s

</mi>

<mi>

a

</mi>

<mi>

t

</mi>

<mn>

0

</mn>
</mrow>
</msub>

<mrow>
<mn>

1

</mn>

<mo>

+

</mo>

<mstyle scriptlevel="0" displaystyle="true">
<mfrac>
<mrow>
<msub>
<mi>

I

</mi>

<mrow>
<mi>

D

</mi>

<mi>

s

</mi>

<mi>

a

</mi>

<mi>

t

</mi>

<mn>

0

</mn>
</mrow>
</msub>

<msub>
<mi>

R

</mi>

<mi>

s

</mi>
</msub>
</mrow>

<mrow>
<mo stretchy="false">

(

</mo>

<msub>
<mi>

V

</mi>

<mrow>
<mi>

G

</mi>

<mi>

S

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

T

</mi>
</msub>

<mo stretchy="false">

)

</mo>
</mrow>
</mfrac>
</mstyle>
</mrow>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

I_{Dsat}=\frac{I_{Dsat0}}{1+\dfrac{I_{Dsat0}R_s}{(V_{GS}-V_T)}}

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
<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

D

</span>

<span className="mord,mathnormal,mtight">

s

</span>

<span className="mord,mathnormal,mtight">

a

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
<span className="strut" style="height:3.5467em;vertical-align:-2.1863em;">



</span>

<span className="mord">
<span className="mopen,nulldelimiter">



</span>

<span className="mfrac">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:1.3603em;">
<span style="top:-2.11em;">
<span className="pstrut" style="height:3.3603em;">



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
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

GS

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

<span className="mclose">

)

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

D

</span>

<span className="mord,mathnormal,mtight">

s

</span>

<span className="mord,mathnormal,mtight">

a

</span>

<span className="mord,mathnormal,mtight">

t

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
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0077em;">

R

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0077em;margin-right:0.05em;">
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

<span style="top:-3.5903em;">
<span className="pstrut" style="height:3.3603em;">



</span>

<span className="frac-line" style="border-bottom-width:0.04em;">



</span>
</span>

<span style="top:-4.0373em;">
<span className="pstrut" style="height:3.3603em;">



</span>

<span className="mord">
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

D

</span>

<span className="mord,mathnormal,mtight">

s

</span>

<span className="mord,mathnormal,mtight">

a

</span>

<span className="mord,mathnormal,mtight">

t

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
<span className="vlist" style="height:2.1863em;">
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

上式可以用下面两个式子进行推导得出：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<msub>
<mi>

I

</mi>

<mrow>
<mi>

D

</mi>

<mi>

s

</mi>

<mi>

a

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

k

</mi>

<mtext>



</mtext>

<mo stretchy="false">

(

</mo>

<msub>
<mi>

V

</mi>

<mrow>
<mi>

G

</mi>

<mi>

S

</mi>

<mo separator="true">

,

</mo>

<mrow>
<mi mathvariant="normal">

i

</mi>

<mi mathvariant="normal">

n

</mi>

<mi mathvariant="normal">

t

</mi>
</mrow>
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

T

</mi>
</msub>

<mo stretchy="false">

)

</mo>

<mo>

=

</mo>

<mi>

k

</mi>

<mtext>



</mtext>

<mo stretchy="false">

(

</mo>

<msub>
<mi>

V

</mi>

<mrow>
<mi>

G

</mi>

<mi>

S

</mi>
</mrow>
</msub>

<mo>

−

</mo>

<msub>
<mi>

I

</mi>

<mrow>
<mi>

D

</mi>

<mi>

s

</mi>

<mi>

a

</mi>

<mi>

t

</mi>
</mrow>
</msub>

<msub>
<mi>

R

</mi>

<mi>

s

</mi>
</msub>

<mo>

−

</mo>

<msub>
<mi>

V

</mi>

<mi>

T

</mi>
</msub>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

I_{Dsat}=k\,(V_{GS,\mathrm{int}}-V_T)=k\,(V_{GS}-I_{Dsat}R_s-V_T)

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
<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

D

</span>

<span className="mord,mathnormal,mtight">

s

</span>

<span className="mord,mathnormal,mtight">

a

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

<span className="mord,mathnormal" style="margin-right:0.0315em;">

k

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mopen">

(

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
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

GS

</span>

<span className="mpunct,mtight">

,

</span>

<span className="mord,mtight">
<span className="mord,mathrm,mtight">

int

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

−

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

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

<span className="mord,mathnormal" style="margin-right:0.0315em;">

k

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mopen">

(

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
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

GS

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

D

</span>

<span className="mord,mathnormal,mtight">

s

</span>

<span className="mord,mathnormal,mtight">

a

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

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0077em;">

R

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0077em;margin-right:0.05em;">
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
<msub>
<mi>

I

</mi>

<mrow>
<mi>

D

</mi>

<mi>

s

</mi>

<mi>

a

</mi>

<msub>
<mi>

t

</mi>

<mn>

0

</mn>
</msub>
</mrow>
</msub>

<mo>

=

</mo>

<mi>

k

</mi>

<mtext>



</mtext>

<mo stretchy="false">

(

</mo>

<msub>
<mi>

V

</mi>

<mrow>
<mi>

G

</mi>

<mi>

S

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

T

</mi>
</msub>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

I_{Dsat_0}=k\,(V_{GS}-V_T)

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9334em;vertical-align:-0.2501em;">



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

D

</span>

<span className="mord,mathnormal,mtight">

s

</span>

<span className="mord,mathnormal,mtight">

a

</span>

<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

t

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3173em;">
<span style="top:-2.357em;margin-left:0em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
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
<span className="vlist" style="height:0.143em;">
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

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.2501em;">
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

<span className="mord,mathnormal" style="margin-right:0.0315em;">

k

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mopen">

(

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
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

GS

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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



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

<span className="mclose">

)

</span>
</span>
</span>
</span>
</span>

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture12-18.webp)

> Rs 源端寄生电阻（Source resistance）和 Rd 漏端寄生电阻（Drain resistance）两个电阻中，Rs 对MOSFET的性能影响更明显。

由式 <span className="katex">
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

s

</mi>

<mi>

a

</mi>

<mi>

t

</mi>
</mrow>
</msub>

<mo>

=

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

s

</mi>

<mi>

a

</mi>

<mi>

t

</mi>

<mn>

0

</mn>
</mrow>
</msub>

<mo>

+

</mo>

<msub>
<mi>

I

</mi>

<mrow>
<mi>

D

</mi>

<mi>

s

</mi>

<mi>

a

</mi>

<mi>

t

</mi>
</mrow>
</msub>

<mtext>



</mtext>

<mo stretchy="false">

(

</mo>

<msub>
<mi>

R

</mi>

<mi>

s

</mi>
</msub>

<mo>

+

</mo>

<msub>
<mi>

R

</mi>

<mi>

d

</mi>
</msub>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

V_{Dsat}=V_{Dsat0}+I_{Dsat}\,(R_s+R_d)

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

<span className="mord,mathnormal,mtight">

s

</span>

<span className="mord,mathnormal,mtight">

a

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

s

</span>

<span className="mord,mathnormal,mtight">

a

</span>

<span className="mord,mathnormal,mtight">

t

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

D

</span>

<span className="mord,mathnormal,mtight">

s

</span>

<span className="mord,mathnormal,mtight">

a

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

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mopen">

(

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0077em;">

R

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0077em;margin-right:0.05em;">
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
<span className="mord,mathnormal" style="margin-right:0.0077em;">

R

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.0077em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

d

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

 可以发现，外部看到的 <span className="katex">
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

s

</mi>

<mi>

a

</mi>

<mi>

t

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

V_{Dsat}

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

<span className="mord,mathnormal,mtight">

s

</span>

<span className="mord,mathnormal,mtight">

a

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

 反而变大，这是由于外部施加的 <span className="katex">
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

S

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

V_{DS}

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

<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

S

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

 会被串联电阻占去一部分，致使<span className="katex">
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

s

</mi>

<mi>

a

</mi>

<mi>

t

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

V_{Dsat}

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

<span className="mord,mathnormal,mtight">

s

</span>

<span className="mord,mathnormal,mtight">

a

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

会比**内在晶体管**进入饱和所需的<span className="katex">
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

s

</mi>

<mi>

a

</mi>

<msub>
<mi>

t

</mi>

<mn>

0

</mn>
</msub>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

V_{Dsat_0}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9334em;vertical-align:-0.2501em;">



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

s

</span>

<span className="mord,mathnormal,mtight">

a

</span>

<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

t

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3173em;">
<span style="top:-2.357em;margin-left:0em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
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
<span className="vlist" style="height:0.143em;">
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

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.2501em;">
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

更大。

### **漏致势垒降低 | Drain Induced Barrier Lowering (DIBL)**

当沟道变短、源漏更近时，**漏端电压** <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

V

</mi>

<mi>

D

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

V_D

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

 **会降低源端与沟道的势垒高度**，从而减小<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
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

V_t

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

的现象称为**漏致势垒降低。**这会让载流子更容易从源端注入沟道，于是 **亚阈值电流（subthreshold current）显著上升。**

> When the channel becomes shorter and the source and drain move closer together, the drain voltage <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msub>
> <mi>
> 
> V
> 
> </mi>
> 
> <mi>
> 
> D
> 
> </mi>
> </msub>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> V_D
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
> <span className="mord,mathnormal" style="margin-right:0.2222em;">
> 
> V
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3283em;">
> <span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">
> 
> D
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
>  lowers the potential barrier between the source and the channel, thereby reducing the threshold voltage <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msub>
> <mi>
> 
> V
> 
> </mi>
> 
> <mi>
> 
> t
> 
> </mi>
> </msub>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> V_t
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
> <span className="mord,mathnormal" style="margin-right:0.2222em;">
> 
> V
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.2806em;">
> <span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mathnormal,mtight">
> 
> t
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
> . This effect is called drain-induced barrier lowering (DIBL). It makes it easier for carriers to be injected from the source into the channel, so the subthreshold current increases significantly.

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture12-19.webp)

MOSFET的沟道长度 L 减小以后，亚阈值摆幅（SS）变大，这时的MOSFET会很难被关断。

> 引用自教材
> 
> 该式<span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msub>
> <mi>
> 
> V
> 
> </mi>
> 
> <mi>
> 
> t
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
> V
> 
> </mi>
> 
> <mrow>
> <mi>
> 
> t
> 
> </mi>
> 
> <mtext>
> 
> -
> 
> </mtext>
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
> n
> 
> </mi>
> 
> <mi>
> 
> g
> 
> </mi>
> </mrow>
> </msub>
> 
> <mo>
> 
> −
> 
> </mo>
> 
> <mo stretchy="false">
> 
> (
> 
> </mo>
> 
> <msub>
> <mi>
> 
> V
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
> s
> 
> </mi>
> </mrow>
> </msub>
> 
> <mo>
> 
> +
> 
> </mo>
> 
> <mn>
> 
> 0.4
> 
> </mn>
> 
> <mo stretchy="false">
> 
> )
> 
> </mo>
> 
> <mtext>
> 
> 
> 
> </mtext>
> 
> <msup>
> <mi>
> 
> e
> 
> </mi>
> 
> <mrow>
> <mo>
> 
> −
> 
> </mo>
> 
> <mi>
> 
> L
> 
> </mi>
> 
> <mi mathvariant="normal">
> 
> /
> 
> </mi>
> 
> <msub>
> <mi>
> 
> l
> 
> </mi>
> 
> <mi>
> 
> d
> 
> </mi>
> </msub>
> </mrow>
> </msup>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> V_t = V_{t\text{-}long} - (V_{ds} + 0.4)\, e^{-L/l_d}
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
> <span className="mord,mathnormal" style="margin-right:0.2222em;">
> 
> V
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.2806em;">
> <span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mathnormal,mtight">
> 
> t
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
> <span className="strut" style="height:0.9694em;vertical-align:-0.2861em;">
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
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3361em;">
> <span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
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
> t
> 
> </span>
> 
> <span className="mord,text,mtight">
> <span className="mord,mtight">
> 
> -
> 
> </span>
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
> <span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">
> 
> g
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
> <span className="mord">
> <span className="mord,mathnormal" style="margin-right:0.2222em;">
> 
> V
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3361em;">
> <span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
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
> <span className="mord,mathnormal,mtight">
> 
> s
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
> <span className="strut" style="height:1.138em;vertical-align:-0.25em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> 
> 0.4
> 
> </span>
> 
> <span className="mclose">
> 
> )
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
> e
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t">
> <span className="vlist-r">
> <span className="vlist" style="height:0.888em;">
> <span style="top:-3.063em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mtight">
> <span className="mord,mtight">
> 
> −
> 
> </span>
> 
> <span className="mord,mathnormal,mtight">
> 
> L
> 
> </span>
> 
> <span className="mord,mtight">
> 
> /
> 
> </span>
> 
> <span className="mord,mtight">
> <span className="mord,mathnormal,mtight" style="margin-right:0.0197em;">
> 
> l
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3448em;">
> <span style="top:-2.3488em;margin-left:-0.0197em;margin-right:0.0714em;">
> <span className="pstrut" style="height:2.5em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size3,size1,mtight">
> <span className="mord,mathnormal,mtight">
> 
> d
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
> <span className="vlist" style="height:0.1512em;">
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
> </span>
> </span>
> </span>
> </span>
> </span>
> </span>
> </span>
> 
> 来自于**简单电容模型**，其中的<span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msub>
> <mi>
> 
> l
> 
> </mi>
> 
> <mi>
> 
> d
> 
> </mi>
> </msub>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> l_d
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:0.8444em;vertical-align:-0.15em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> <span className="mord,mathnormal" style="margin-right:0.0197em;">
> 
> l
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3361em;">
> <span style="top:-2.55em;margin-left:-0.0197em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mathnormal,mtight">
> 
> d
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
> 可以被称为DIBL的特征长度。在新的工艺节点为了让 <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <mi>
> 
> L
> 
> </mi>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> L
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
> L
> 
> </span>
> </span>
> </span>
> </span>
> 
>  降低，<span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msub>
> <mi>
> 
> l
> 
> </mi>
> 
> <mi>
> 
> d
> 
> </mi>
> </msub>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> l_d
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:0.8444em;vertical-align:-0.15em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> <span className="mord,mathnormal" style="margin-right:0.0197em;">
> 
> l
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3361em;">
> <span style="top:-2.55em;margin-left:-0.0197em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mathnormal,mtight">
> 
> d
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
>  应该随着 <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <mi>
> 
> L
> 
> </mi>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> L
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
> L
> 
> </span>
> </span>
> </span>
> </span>
> 
>  按比例降低。这意味着我们应该减小 <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msub>
> <mi>
> 
> T
> 
> </mi>
> 
> <mi>
> 
> o
> 
> </mi>
> </msub>
> 
> <mi>
> 
> x
> 
> </mi>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> T_ox
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
> T
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.1514em;">
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
> o
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
> <span className="mord,mathnormal">
> 
> x
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
> <msub>
> <mi>
> 
> W
> 
> </mi>
> 
> <mi>
> 
> d
> 
> </mi>
> </msub>
> 
> <mi>
> 
> e
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
> W_dep
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
> <span className="mord,mathnormal" style="margin-right:0.1389em;">
> 
> W
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
> <span className="mord,mathnormal,mtight">
> 
> d
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
> <span className="mord,mathnormal">
> 
> e
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
>  和/或 <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msub>
> <mi>
> 
> X
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
> X_j
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
> <span className="mord,mathnormal" style="margin-right:0.0785em;">
> 
> X
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3117em;">
> <span style="top:-2.55em;margin-left:-0.0785em;margin-right:0.05em;">
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
> 。实际上，在每个工艺节点这三项都会降低，从而实现 <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msub>
> <mi>
> 
> l
> 
> </mi>
> 
> <mi>
> 
> d
> 
> </mi>
> </msub>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> l_d
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:0.8444em;vertical-align:-0.15em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> <span className="mord,mathnormal" style="margin-right:0.0197em;">
> 
> l
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3361em;">
> <span style="top:-2.55em;margin-left:-0.0197em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mathnormal,mtight">
> 
> d
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
>  的降低。降低 <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msub>
> <mi>
> 
> T
> 
> </mi>
> 
> <mi>
> 
> o
> 
> </mi>
> </msub>
> 
> <mi>
> 
> x
> 
> </mi>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> T_ox
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
> T
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.1514em;">
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
> o
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
> <span className="mord,mathnormal">
> 
> x
> 
> </span>
> </span>
> </span>
> </span>
> 
>  可以增加栅控能力或者增加 <span className="katex">
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
> o
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
> </mrow>
> </msub>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> C_{oxe}
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
> <span className="mord,mathnormal" style="margin-right:0.0715em;">
> 
> C
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.1514em;">
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
> o
> 
> </span>
> 
> <span className="mord,mathnormal,mtight">
> 
> x
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
> 。减小 <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msub>
> <mi>
> 
> X
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
> X_j
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
> <span className="mord,mathnormal" style="margin-right:0.0785em;">
> 
> X
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3117em;">
> <span style="top:-2.55em;margin-left:-0.0785em;margin-right:0.05em;">
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
>  通过减小漏区尺寸而减小 <span className="katex">
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
> <mi>
> 
> d
> 
> </mi>
> </msub>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> C_d
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
> <span className="mord,mathnormal" style="margin-right:0.0715em;">
> 
> C
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3361em;">
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
> d
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
> 。减小 <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msub>
> <mi>
> 
> W
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
> e
> 
> </mi>
> 
> <mi>
> 
> p
> 
> </mi>
> </mrow>
> </msub>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> W_{dep}
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
> W
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
> <span className="mord,mathnormal,mtight">
> 
> e
> 
> </span>
> 
> <span className="mord,mathnormal,mtight">
> 
> p
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
>  可以通过引入地平面（衬底的中性区或耗尽区底部），趋于从电学上屏蔽沟道和漏区之间的耦合，这样也可以减小 <span className="katex">
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
> <mi>
> 
> d
> 
> </mi>
> </msub>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> C_d
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
> <span className="mord,mathnormal" style="margin-right:0.0715em;">
> 
> C
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3361em;">
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
> d
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
> 。

### **MOSFET OFF State vs. ON State**

#### 亚阈值区 | Sub-threshold regime

当 <span className="katex">
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

G

</mi>

<mi>

S

</mi>
</mrow>
</msub>

<mo>
<

</mo>

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

V_{GS}<V_T

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
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

GS

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
<

</span>

<span className="mspace" style="margin-right:0.2778em;">



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

 时，沟道没有形成强反型的低阻通道，源端到沟道之间存在势垒。载流子要从源端进入沟道，主要靠**热运动+浓度梯度**越过势垒（即**扩散电流**）。

##### Subthreshold swing S 与 DIBL

**亚阈值摆幅**：SS 越小，说明栅控越强，关断更彻底。

**DIBL**：漏端电压把源端势垒压低，OFF 漏电上升，等效 <span className="katex">
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

 下降。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture12-20.webp)

#### 导通区 | ON state

导通时沟道形成强反型层，相当于出现一条可导电的通道。载流子在横向电场 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

E

</mi>

<mi>

x

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

E_x

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

E

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0576em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

x

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

 下发生**漂移**，此时的<span className="katex">
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

D

</mi>

<mi>

S

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

I_{DS}

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
<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

D

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

S

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

主要由漂移电流决定。

##### 穿通&寄生 BJT | Punchthrough & parasitic BJT

**Punchthrough（穿通）**：当<span className="katex">
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

S

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

V_{DS}

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

<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

S

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

很大、沟道很短时，源漏耗尽区可能在沟道下方连接，导致源端势垒被严重削弱，即使栅控也压不住，<span className="katex">
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

D

</mi>

<mi>

S

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

I_{DS}

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
<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

D

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

S

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

电流突然变大（类似**失控漏电**）。

**寄生 BJT 效应**：MOSFET 的源/体/漏天然构成一个寄生双极管（例如 nMOS 中：源 n+—体 p—漏 n+）。高场下的碰撞电离产生的空穴会抬高体电位，可能触发寄生 BJT 导通，引发更大电流<span className="katex">
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

D

</mi>

<mi>

S

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

I_{DS}

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
<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

D

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

S

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

。

##### 寄生串联电阻 | Parasitic series resistances

**源端电阻**<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

R

</mi>

<mi>

s

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

R_s

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0077em;">

R

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0077em;margin-right:0.05em;">
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

会减小有效的<span className="katex">
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

G

</mi>

<mi>

S

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

V_{GS}

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
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

GS

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

。

**源端和漏端的电阻（**<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

R

</mi>

<mi>

S

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

R_S

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



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
</span>
</span>
</span>

**和**<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

R

</mi>

<mi>

D

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

R_D

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



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

**）**和会减小有效的<span className="katex">
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

S

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

V_{DS}

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

<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

S

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

。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture12-21.webp)

### 亚微米MOSFET的结构与设计 | **Submicron MOSFET: Structure and Design**

**Vertical (Channel) Engineering：纵向/沟道工程**主要解决栅控与短沟道效应：<span className="katex">
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

 roll-off、DIBL、亚阈值摆幅等。

**Horizontal (Drain) Engineering：横向/漏侧工程**主要解决漏端高电场相关问题：热载流子、穿通、寄生 BJT，同时兼顾串联电阻。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture12-22.webp)

## 减小栅绝缘层的电学厚度和隧穿电流 | **Reducing Gate-Insulator Electrical Thickness and Tunneling Leakage**

减小氧化层厚度目的是

- 增大 <span className="katex">
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

o

</mi>

<mi>

x

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

C_{ox}

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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

o

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
</span>
</span>
</span>

 以提高 <span className="katex">
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

o

</mi>

<mi>

n

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

I_{on}

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
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0785em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
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

（导通电流）
- 降低亚阈值摆幅（subthreshold swing）
- 控制阈值电压 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
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

V_t

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

 的回落（roll-off）

如果氧化层太薄也会产生很多问题

- 会因高电场导致击穿（breakdown）
- 漏电流（leakage current）增大

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture12-23.webp)

### 栅极隧穿漏电流 | **Gate Tunneling Leakage Current**

**当栅氧层（或等效栅氧厚度 EOT）被做得很薄时，栅极会出现“量子隧穿”泄漏电流（Gate Tunneling Leakage）**，并且它会成为继续缩小栅氧厚度的**主要限制因素。**

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture12-24.webp)

对于厚度低于 1.5 nm 的 SiO2 膜，**栅漏电会大到功耗/可靠性都无法接受**，这将成为最严重的限制因素。

> 电子以热运动速度到达栅氧化层势垒处，并以式<span className="katex">
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
> <mo>
> 
> ≈
> 
> </mo>
> 
> <mi>
> 
> exp
> 
> </mi>
> 
> <mo>
> 
> ⁡
> 
> </mo>
> 
> <mtext>
> 
> ⁣
> 
> </mtext>
> 
> <mrow>
> <mo fence="true">
> 
> (
> 
> </mo>
> 
> <mo>
> 
> −
> 
> </mo>
> 
> <mn>
> 
> 2
> 
> </mn>
> 
> <mi>
> 
> T
> 
> </mi>
> 
> <msqrt>
> <mrow>
> <mfrac>
> <mrow>
> <mn>
> 
> 8
> 
> </mn>
> 
> <msup>
> <mi>
> 
> π
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
> <mi>
> 
> m
> 
> </mi>
> </mrow>
> 
> <msup>
> <mi>
> 
> h
> 
> </mi>
> 
> <mn>
> 
> 2
> 
> </mn>
> </msup>
> </mfrac>
> 
> <mtext>
> 
> 
> 
> </mtext>
> 
> <mo stretchy="false">
> 
> (
> 
> </mo>
> 
> <msub>
> <mi>
> 
> V
> 
> </mi>
> 
> <mi>
> 
> H
> 
> </mi>
> </msub>
> 
> <mo>
> 
> −
> 
> </mo>
> 
> <mi>
> 
> E
> 
> </mi>
> 
> <mo stretchy="false">
> 
> )
> 
> </mo>
> </mrow>
> </msqrt>
> 
> <mo fence="true">
> 
> )
> 
> </mo>
> </mrow>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> P \approx \exp\!\left(-2T\sqrt{\frac{8\pi^{2}m}{h^{2}}\,(V_{H}-E)}\right)
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
> 
> <span className="mspace" style="margin-right:0.2778em;">
> 
> 
> 
> </span>
> 
> <span className="mrel">
> 
> ≈
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
> <span className="strut" style="height:2.4em;vertical-align:-0.95em;">
> 
> 
> 
> </span>
> 
> <span className="mop">
> 
> exp
> 
> </span>
> 
> <span className="mspace" style="margin-right:-0.1667em;">
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
> <span className="minner">
> <span className="mopen,delimcenter" style="top:0em;">
> <span className="delimsizing,size3">
> 
> (
> 
> </span>
> </span>
> 
> <span className="mord">
> 
> −
> 
> </span>
> 
> <span className="mord">
> 
> 2
> 
> </span>
> 
> <span className="mord,mathnormal" style="margin-right:0.1389em;">
> 
> T
> 
> </span>
> 
> <span className="mord,sqrt">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:1.2707em;">
> <span className="svg-align" style="top:-3.8em;">
> <span className="pstrut" style="height:3.8em;">
> 
> 
> 
> </span>
> 
> <span className="mord" style="padding-left:1em;">
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
> <span className="vlist" style="height:0.9164em;">
> <span style="top:-2.655em;">
> <span className="pstrut" style="height:3em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mtight">
> <span className="mord,mtight">
> <span className="mord,mathnormal,mtight">
> 
> h
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t">
> <span className="vlist-r">
> <span className="vlist" style="height:0.7463em;">
> <span style="top:-2.786em;margin-right:0.0714em;">
> <span className="pstrut" style="height:2.5em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size3,size1,mtight">
> <span className="mord,mtight">
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
> <span className="mord,mtight">
> 
> 8
> 
> </span>
> 
> <span className="mord,mtight">
> <span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">
> 
> π
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t">
> <span className="vlist-r">
> <span className="vlist" style="height:0.7463em;">
> <span style="top:-2.786em;margin-right:0.0714em;">
> <span className="pstrut" style="height:2.5em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size3,size1,mtight">
> <span className="mord,mtight">
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
> 
> <span className="mord,mathnormal,mtight">
> 
> m
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
> 
> <span className="mspace" style="margin-right:0.1667em;">
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
> <span className="mord">
> <span className="mord,mathnormal" style="margin-right:0.2222em;">
> 
> V
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3283em;">
> <span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mtight">
> <span className="mord,mathnormal,mtight" style="margin-right:0.0813em;">
> 
> H
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
> −
> 
> </span>
> 
> <span className="mspace" style="margin-right:0.2222em;">
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
> <span className="mclose">
> 
> )
> 
> </span>
> </span>
> </span>
> 
> <span style="top:-3.2307em;">
> <span className="pstrut" style="height:3.8em;">
> 
> 
> 
> </span>
> 
> <span className="hide-tail" style="min-width:1.02em;height:1.88em;">
> <svg xmlns="http://www.w3.org/2000/svg" width="400em" height="1.88em" viewBox="0 0 400000 1944" preserveAspectRatio="xMinYMin slice">
> <path d="M983 90
> l0 -0
> c4,-6.7,10,-10,18,-10 H400000v40
> H1013.1s-83.4,268,-264.1,840c-180.7,572,-277,876.3,-289,913c-4.7,4.7,-12.7,7,-24,7
> s-12,0,-12,0c-1.3,-3.3,-3.7,-11.7,-7,-25c-35.3,-125.3,-106.7,-373.3,-214,-744
> c-10,12,-21,25,-33,39s-32,39,-32,39c-6,-5.3,-15,-14,-27,-26s25,-30,25,-30
> c26.7,-32.7,52,-63,76,-91s52,-60,52,-60s208,722,208,722
> c56,-175.3,126.3,-397.3,211,-666c84.7,-268.7,153.8,-488.2,207.5,-658.5
> c53.7,-170.3,84.5,-266.8,92.5,-289.5z
> M1001 80h400000v40h-400000z">
> 
> 
> 
> </path>
> </svg>
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
> <span className="vlist" style="height:0.5693em;">
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
> <span className="mclose,delimcenter" style="top:0em;">
> <span className="delimsizing,size3">
> 
> )
> 
> </span>
> </span>
> </span>
> </span>
> </span>
> </span>
> 
> 给出的几率进入栅极。这是栅极漏电流的产生原因。右图给出了随着 SiO2 厚度的减小，栅极漏电流指数上升，这一趋势与隧穿模型的预测相吻合。漏电流可以通过在 **SiO2 中添加氮元素**而减小 10 倍。

高 k 介质材料在相同的等效氧化层厚度（EOT）的条件下，具有更低的隧穿电流。

### **Replacing SiO2 with High-k Dielectric**

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture12-25.webp)

HfO2 的相对介电常数 k 约为 24，是 SiO2 的 6 倍。

一个 6 nm 厚的 HfO2 薄膜具有 1 nm 的**等效氧化层厚度（Equivalent Oxide Thickness）**，对于电子和空穴具有**更厚（虽然更低）**的隧穿势垒，隧穿概率按指数下降，栅漏电流大幅减小。

其他具有吸引力的高 k 介质包括 ZrO2 和 Al2O3。

> HfO₂ has a relative dielectric constant (k) of ~24, six times larger than that of SiO₂.
> 
> For the same EOT, the HfO₂ film presents a much thicker (albeit a lower) tunneling barrier to the electrons and holes.
> 
> <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msub>
> <mi>
> 
> T
> 
> </mi>
> 
> <mrow>
> <mi>
> 
> o
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
> </mrow>
> </msub>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> T_{oxe}
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
> T
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.1514em;">
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
> o
> 
> </span>
> 
> <span className="mord,mathnormal,mtight">
> 
> x
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
>  can be further reduced by introducing metal-gate technology since the poly-depletion effect is eliminated.

### **Challenges of High-K Technology**

#### 挑战

在 IC 制造工艺中采用高 k 介质的**难点**在于：

高 k 介质与硅衬底和栅极之间的**化学反应；**

比 Si-SiO2 系统**更低的表面迁移率和更多的氧化层电荷；**

high-k 里可能存在一些**等效正电荷**或电荷陷阱效应，使得 pMOS 的阈值看起来偏低（|Vt|变小）。

#### **解决方法：**

这些问题可以通过在硅衬底和高 k 介质之间**插入一层很薄的 SiO2 界面**层得到改善。

### question:

**How can** <span className="katex">
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

i

</mi>

<mi>

n

</mi>

<mi>

v

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

T_{inv}

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
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.1389em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

in

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

v

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

 **be reduced?**

1. **增强栅对沟道的电场控制**：更小 EOT、更强栅电容（在不引起过大泄漏的前提下）
2. <s>

**消除 poly-depletion**

</s>

<s>

：用

</s>

 <s>

**metal gate**

</s>

 <s>

替代 poly-Si 栅，使载流子更“贴近”界面、减少等效厚度贡献

</s>
3. **优化界面层厚度/质量**：界面层太厚会增加等效距离，太薄又会牺牲界面质量，需要折中。这个方法是应对 high-k 材料应用的，high-k 材料往往会在 Si 与 high-k 之间插入一层薄 SiO₂ 来改善界面质量，但它会增加等效厚度。

> **Trade-off**：IL 太薄会带来界面缺陷、迁移率/可靠性问题；太厚又会让 EOT / Tinv 超标。

1. 降低**量子反型层厚度** <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

T

</mi>

<mtext>

qm

</mtext>
</msub>
</mrow>

<annotation encoding="application/x-tex">

T_{\text{qm}}

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
<span className="mord,text,mtight">
<span className="mord,mtight">

qm

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

（让反型电荷更靠近界面）

> 1. **Enhance the gate’s electrostatic control over the channel:** achieve a smaller EOT and a higher gate capacitance, as long as this does not cause excessive leakage.
> 2. <s>
> 
> **Eliminate poly-depletion:**
> 
> </s>
> 
>  <s>
> 
> replace the poly-Si gate with a metal gate so that carriers are “closer” to the interface, reducing the contribution to the effective thickness.
> 
> </s>
> 3. **Optimize the interfacial-layer thickness/quality:** an overly thick interfacial layer increases the effective distance, while an overly thin one degrades interface quality, so a trade-off is required. This approach is specifically used for high-k integration: a thin SiO2 interfacial layer is often inserted between Si and the high-k dielectric to improve the interface, but it increases the effective thickness.
> 4. **Reduce the quantum inversion-layer thickness** <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msub>
> <mi>
> 
> T
> 
> </mi>
> 
> <mtext>
> 
> qm
> 
> </mtext>
> </msub>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> T_{\text{qm}}
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
> T
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.1514em;">
> <span style="top:-2.55em;margin-left:-0.1389em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mtight">
> <span className="mord,text,mtight">
> <span className="mord,mtight">
> 
> qm
> 
> </span>
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
>  (bring the inversion charge centroid closer to the interface).

## 金属源/漏的MOSFET | **MOSFET with Metal Source/Drain**

**金属源/漏MOSFET**或**Schottky源/漏MOSFET**可以有非常浅的结（**有助于减小短沟效应**）和很低的串联电阻，因为硅化物比N+或P+硅电导率高10倍以上。唯一的问题是金属源/漏MOSFET的<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

I

</mi>

<mi>

d

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

I_d

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
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.0785em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

d

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

有可能比普通MOSFET的<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

I

</mi>

<mi>

d

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

I_d

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
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.0785em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

d

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

要**低**，这是因为如果<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

ϕ

</mi>

<mi>

B

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

\phi_B

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

ϕ

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0502em;">

B

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

太大，有可能**阻止载流子**（NFET中的电子）从源注入到沟道区。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture12-26.webp)

### 金属源/漏MOSFET的<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

I

</mi>

<mi>

d

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

I_d

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
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.0785em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

d

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

可能比传统低的原因

图（b）给出了从源到漏的沟道界面的能带图。为了简单起见，Vds设为0。这个能带图与传统MOSFET在Vg=0时的能带图类似，其中势垒阻止了电子从源区到沟道，因而整个晶体管处于**关态**。

在**开态**，如图（c）所示，沟道Ec被栅压拉下来，但源漏边缘的Ec并未受到影响，势垒高度仍固定为<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

ϕ

</mi>

<mi>

B

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

\phi_B

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

ϕ

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0502em;">

B

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

。这个势垒在传统MOSFET中是不存在的，它会降低金属源/漏MOSFET的Id。

### 解决方法

为了充分释放Schottky源/漏MOSFET的潜力，对于NFET应该采用<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

ϕ

</mi>

<mrow>
<mi>

B

</mi>

<mi>

n

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

\phi_{Bn}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

ϕ

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
<span className="mord,mathnormal,mtight" style="margin-right:0.0502em;">

B

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

非常低的Schottky结技术。可以在金属和沟道之间加上一层N+薄层，这将减小势垒对电流的影响。但是需要注意，由于<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

ϕ

</mi>

<mrow>
<mi>

B

</mi>

<mi>

n

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

\phi_{Bn}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

ϕ

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
<span className="mord,mathnormal,mtight" style="margin-right:0.0502em;">

B

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

降低，减小Schottky漏-衬底结会导致反向漏电流过大的问题。

## Ion 和 Ioff 之间的折中及可靠性设计

<span className="katex">
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

o

</mi>

<mi>

f

</mi>

<mi>

f

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

I_{off}

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

I

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.0785em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

o

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.1076em;">

f

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.1076em;">

f

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

 主要组成部分是亚阈值电流

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<msub>
<mi>

I

</mi>

<mrow>
<mi mathvariant="normal">

o

</mi>

<mi mathvariant="normal">

f

</mi>

<mi mathvariant="normal">

f

</mi>
</mrow>
</msub>

<mo stretchy="false">

(

</mo>

<mrow>
<mi mathvariant="normal">

n

</mi>

<mi mathvariant="normal">

A

</mi>
</mrow>

<mo stretchy="false">

)

</mo>

<mo>

=

</mo>

<mn>

100

</mn>

<mo>

⋅

</mo>

<mfrac>
<mi>

W

</mi>

<mi>

L

</mi>
</mfrac>

<mo>

⋅

</mo>

<msup>
<mi>

e

</mi>

<mrow>
<mo>

−

</mo>

<mfrac>
<mrow>
<mi>

q

</mi>

<msub>
<mi>

V

</mi>

<mi>

t

</mi>
</msub>
</mrow>

<mrow>
<mi>

η

</mi>

<mi>

k

</mi>

<mi>

T

</mi>
</mrow>
</mfrac>
</mrow>
</msup>

<mo>

=

</mo>

<mn>

100

</mn>

<mo>

⋅

</mo>

<mfrac>
<mi>

W

</mi>

<mi>

L

</mi>
</mfrac>

<mo>

⋅

</mo>

<msup>
<mn>

10

</mn>

<mrow>
<mo>

−

</mo>

<mfrac>
<msub>
<mi>

V

</mi>

<mi>

t

</mi>
</msub>

<mi>

S

</mi>
</mfrac>
</mrow>
</msup>
</mrow>

<annotation encoding="application/x-tex">

I_{\mathrm{off}}(\mathrm{nA}) = 100 \cdot \frac{W}{L}\cdot e^{-\frac{qV_t}{\eta kT}} = 100 \cdot \frac{W}{L}\cdot 10^{-\frac{V_t}{S}}

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
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.0785em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">
<span className="mord,mathrm,mtight" style="margin-right:0.0778em;">

off

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

<span className="mord">
<span className="mord,mathrm">

nA

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

100

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
<span className="mord,mathnormal">

L

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

W

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

⋅

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.149em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

e

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:1.149em;">
<span style="top:-3.4458em;margin-right:0.05em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">

−

</span>

<span className="mord,mtight">
<span className="mopen,nulldelimiter,sizing,reset-size3,size6">



</span>

<span className="mfrac">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:1.0047em;">
<span style="top:-2.656em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

η

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0315em;">

k

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.1389em;">

T

</span>
</span>
</span>
</span>

<span style="top:-3.2255em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="frac-line,mtight" style="border-bottom-width:0.049em;">



</span>
</span>

<span style="top:-3.5166em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

q

</span>

<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.2222em;">

V

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3448em;">
<span style="top:-2.3448em;margin-left:-0.2222em;margin-right:0.1em;">
<span className="pstrut" style="height:2.6151em;">



</span>

<span className="mord,mathnormal,mtight">

t

</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.2703em;">
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

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.4829em;">
<span>



</span>
</span>
</span>
</span>
</span>

<span className="mclose,nulldelimiter,sizing,reset-size3,size6">



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

100

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
<span className="mord,mathnormal">

L

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

W

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

⋅

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.1163em;">



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
<span className="vlist" style="height:1.1163em;">
<span style="top:-3.413em;margin-right:0.05em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">

−

</span>

<span className="mord,mtight">
<span className="mopen,nulldelimiter,sizing,reset-size3,size6">



</span>

<span className="mfrac">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:1.0047em;">
<span style="top:-2.656em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

S

</span>
</span>
</span>
</span>

<span style="top:-3.2255em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="frac-line,mtight" style="border-bottom-width:0.049em;">



</span>
</span>

<span style="top:-3.5166em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
<span className="mord,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.2222em;">

V

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3448em;">
<span style="top:-2.3448em;margin-left:-0.2222em;margin-right:0.1em;">
<span className="pstrut" style="height:2.6151em;">



</span>

<span className="mord,mathnormal,mtight">

t

</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.2703em;">
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

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.344em;">
<span>



</span>
</span>
</span>
</span>
</span>

<span className="mclose,nulldelimiter,sizing,reset-size3,size6">



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
</span>
</span>

Vt decreases with L, a fact known as Vt roll-off, caused by drain-induced barrier lowering (DIBL).

以下是DIBL的经验公式，结合简单电容模型：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<msub>
<mi>

V

</mi>

<mi>

t

</mi>
</msub>

<mo>

=

</mo>

<msub>
<mi>

V

</mi>

<mrow>
<mi>

t

</mi>

<mtext>

-long

</mtext>
</mrow>
</msub>

<mo>

−

</mo>

<mo stretchy="false">

(

</mo>

<msub>
<mi>

V

</mi>

<mrow>
<mi>

d

</mi>

<mi>

s

</mi>
</mrow>
</msub>

<mo>

+

</mo>

<mn>

0.4

</mn>

<mo stretchy="false">

)

</mo>

<mo>

⋅

</mo>

<msup>
<mi>

e

</mi>

<mrow>
<mo>

−

</mo>

<mfrac>
<mi>

L

</mi>

<msub>
<mi>

l

</mi>

<mi>

d

</mi>
</msub>
</mfrac>
</mrow>
</msup>
</mrow>

<annotation encoding="application/x-tex">

V_t = V_{t\text{-long}} - (V_{ds}+0.4)\cdot e^{-\frac{L}{l_d}}

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

t

</span>

<span className="mord,text,mtight">
<span className="mord,mtight">

-long

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

−

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

d

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

0.4

</span>

<span className="mclose">

)

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
<span className="strut" style="height:1.1338em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

e

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:1.1338em;">
<span style="top:-3.5234em;margin-right:0.05em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">

−

</span>

<span className="mord,mtight">
<span className="mopen,nulldelimiter,sizing,reset-size3,size6">



</span>

<span className="mfrac">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.8721em;">
<span style="top:-2.656em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
<span className="mord,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0197em;">

l

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3448em;">
<span style="top:-2.3448em;margin-left:-0.0197em;margin-right:0.1em;">
<span className="pstrut" style="height:2.6944em;">



</span>

<span className="mord,mathnormal,mtight">

d

</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.3496em;">
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

<span style="top:-3.2255em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="frac-line,mtight" style="border-bottom-width:0.049em;">



</span>
</span>

<span style="top:-3.384em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
<span className="mord,mtight">
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
<span className="vlist" style="height:0.5937em;">
<span>



</span>
</span>
</span>
</span>
</span>

<span className="mclose,nulldelimiter,sizing,reset-size3,size6">



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

l

</mi>

<mi>

d

</mi>
</msub>

<mo>

∝

</mo>

<mroot>
<mrow>
<mtext>



</mtext>

<msub>
<mi>

T

</mi>

<mrow>
<mi mathvariant="normal">

o

</mi>

<mi mathvariant="normal">

x

</mi>

<mi mathvariant="normal">

e

</mi>
</mrow>
</msub>

<mtext>



</mtext>

<msub>
<mi>

W

</mi>

<mrow>
<mi mathvariant="normal">

d

</mi>

<mi mathvariant="normal">

e

</mi>

<mi mathvariant="normal">

p

</mi>
</mrow>
</msub>

<mtext>



</mtext>

<msub>
<mi>

X

</mi>

<mi>

j

</mi>
</msub>

<mtext>



</mtext>
</mrow>

<mn>

3

</mn>
</mroot>
</mrow>

<annotation encoding="application/x-tex">

l_d \propto \sqrt[3]{\,T_{\mathrm{oxe}}\, W_{\mathrm{dep}}\, X_j\,}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8444em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.0197em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

d

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

∝

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.24em;vertical-align:-0.3075em;">



</span>

<span className="mord,sqrt">
<span className="root">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.6972em;">
<span style="top:-2.875em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size6,size1,mtight">
<span className="mord,mtight">
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

<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.9325em;">
<span className="svg-align" style="top:-3.2em;">
<span className="pstrut" style="height:3.2em;">



</span>

<span className="mord" style="padding-left:1em;">
<span className="mspace" style="margin-right:0.1667em;">



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
<span className="mord,mtight">
<span className="mord,mathrm,mtight">

oxe

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
<span className="vlist" style="height:0.15em;">
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
<span className="mord,mathnormal" style="margin-right:0.1389em;">

W

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
<span className="mord,mtight">
<span className="mord,mathrm,mtight">

dep

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
<span className="vlist" style="height:0.2861em;">
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

<span className="mspace" style="margin-right:0.1667em;">



</span>
</span>
</span>

<span style="top:-2.8925em;">
<span className="pstrut" style="height:3.2em;">



</span>

<span className="hide-tail" style="min-width:1.02em;height:1.28em;">
<svg xmlns="http://www.w3.org/2000/svg" width="400em" height="1.28em" viewBox="0 0 400000 1296" preserveAspectRatio="xMinYMin slice">
<path d="M263,681c0.7,0,18,39.7,52,119
c34,79.3,68.167,158.7,102.5,238c34.3,79.3,51.8,119.3,52.5,120
c340,-704.7,510.7,-1060.3,512,-1067
l0 -0
c4.7,-7.3,11,-11,19,-11
H40000v40H1012.3
s-271.3,567,-271.3,567c-38.7,80.7,-84,175,-136,283c-52,108,-89.167,185.3,-111.5,232
c-22.3,46.7,-33.8,70.3,-34.5,71c-4.7,4.7,-12.3,7,-23,7s-12,-1,-12,-1
s-109,-253,-109,-253c-72.7,-168,-109.3,-252,-110,-252c-10.7,8,-22,16.7,-34,26
c-22,17.3,-33.3,26,-34,26s-26,-26,-26,-26s76,-59,76,-59s76,-60,76,-60z
M1001 80h400000v40h-400000z">



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
<span className="vlist" style="height:0.3075em;">
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

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture12-27.webp)

短沟道器件的输出电导<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

g

</mi>

<mrow>
<mi>

d

</mi>

<mi>

s

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

g_{ds}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.625em;vertical-align:-0.1944em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

g

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

d

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



<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

g

</mi>

<mrow>
<mi>

d

</mi>

<mi>

s

</mi>
</mrow>
</msub>

<mo>

=

</mo>

<msub>
<mi>

g

</mi>

<mrow>
<mi>

m

</mi>

<mi>

s

</mi>

<mi>

a

</mi>

<mi>

t

</mi>
</mrow>
</msub>

<mo>

×

</mo>

<msup>
<mi>

e

</mi>

<mrow>
<mo>

−

</mo>

<mi>

L

</mi>

<mi mathvariant="normal">

/

</mi>

<msub>
<mi>

l

</mi>

<mi>

d

</mi>
</msub>
</mrow>
</msup>
</mrow>

<annotation encoding="application/x-tex">

g_{ds} = g_{msat} × e^{−L/l_d}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.625em;vertical-align:-0.1944em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

g

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

d

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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.7778em;vertical-align:-0.1944em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

g

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

m

</span>

<span className="mord,mathnormal,mtight">

s

</span>

<span className="mord,mathnormal,mtight">

a

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

×

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.888em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

e

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.888em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">

−

</span>

<span className="mord,mathnormal,mtight">

L

</span>

<span className="mord,mtight">

/

</span>

<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0197em;">

l

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3448em;">
<span style="top:-2.3488em;margin-left:-0.0197em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
<span className="mord,mathnormal,mtight">

d

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

，其中<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

l

</mi>

<mi>

d

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

l_d

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8444em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.0197em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

d

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

是DIBL的特征长度。

### 制造过程的波动与设计 | **Variations and Design for Manufacturing**

如果Vt设计得很高，亚阈值区Ioff将不成问题。但Vt过高会减小Ion，从而降低电路速度，这是不能接受的。采用一个大的Vdd可以提高Ion，但这也是不能接受的，因为这会提高功耗，而功耗已经太大了。减小L可以提高Ion，但这会降低Vt从而提高Ioff。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture12-28.webp)

上图给出了大量晶体管的 log Ioff 与 Ion 的关系。通过有意改变 Lg 值和无意制造 Lg 参数的波动所导致的 Ion（及Ioff）变化情况。图中的 Ion 和 Ioff 并不严格地在一条直线上，这是由于 Lg 和 Vt 的工艺偏差以及栅长的差异造成的。

<alert type="question">

**问题：以下哪个改变（如果有的话）可以减小亚阈值区漏电流，同时还能提高Ion？更大的Vt，更大的L，更小的Tox，还是更小的Vdd？**

唯一有可能做到的就是更小的Tox。

栅氧层变薄，<span className="katex">
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

o

</mi>

<mi>

x

</mi>
</mrow>
</msub>

<mo>

=

</mo>

<msub>
<mi>

ε

</mi>

<mrow>
<mi>

o

</mi>

<mi>

x

</mi>
</mrow>
</msub>

<mi mathvariant="normal">

/

</mi>

<msub>
<mi>

T

</mi>

<mrow>
<mi>

o

</mi>

<mi>

x

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

C_{ox}=ε_{ox}/T_{ox}

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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

o

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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

ε

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

o

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

<span className="mord">

/

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

o

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
</span>
</span>
</span>

 变大，在相同<span className="katex">
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

G

</mi>

<mi>

S

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

V_{GS}

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
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

GS

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

下更容易形成更强反型，由于<span className="katex">
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

o

</mi>

<mi>

n

</mi>
</mrow>
</msub>

<mo>

∝

</mo>

<mi>

μ

</mi>

<msub>
<mi>

C

</mi>

<mrow>
<mi>

o

</mi>

<mi>

x

</mi>
</mrow>
</msub>

<mo stretchy="false">

(

</mo>

<msub>
<mi>

V

</mi>

<mrow>
<mi>

G

</mi>

<mi>

S

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

T

</mi>
</msub>

<msup>
<mo stretchy="false">

)

</mo>

<mn>

2

</mn>
</msup>
</mrow>

<annotation encoding="application/x-tex">

I_{on}\propto \mu C_{ox}(V_{GS}-V_T)^2

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
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0785em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

∝

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord,mathnormal">

μ

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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

o

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

<span className="mopen">

(

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
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

GS

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
<span className="strut" style="height:1.0641em;vertical-align:-0.25em;">



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

<span className="mclose">
<span className="mclose">

)

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

，驱动电流增大。同时栅控能力更强，亚阈值摆幅<span className="katex">
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

<mo stretchy="false">

(

</mo>

<mi>

ln

</mi>

<mo>

⁡

</mo>

<mn>

10

</mn>

<mo stretchy="false">

)

</mo>

<mfrac>
<mrow>
<mi>

k

</mi>

<mi>

T

</mi>
</mrow>

<mi>

q

</mi>
</mfrac>

<mrow>
<mo fence="true">

(

</mo>

<mn>

1

</mn>

<mo>

+

</mo>

<mfrac>
<msub>
<mi>

C

</mi>

<mrow>
<mi>

d

</mi>

<mi>

e

</mi>

<mi>

p

</mi>
</mrow>
</msub>

<msub>
<mi>

C

</mi>

<mrow>
<mi>

o

</mi>

<mi>

x

</mi>
</mrow>
</msub>
</mfrac>

<mo fence="true">

)

</mo>
</mrow>
</mrow>

<annotation encoding="application/x-tex">

S=(\ln 10)\frac{kT}{q}\left(1+\frac{C_{dep}}{C_{ox}}\right)

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
<span className="strut" style="height:1.8em;vertical-align:-0.65em;">



</span>

<span className="mopen">

(

</span>

<span className="mop">

ln

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord">

10

</span>

<span className="mclose">

)

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
<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

q

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
<span className="mord,mathnormal,mtight" style="margin-right:0.0315em;">

k

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.1389em;">

T

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

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="minner">
<span className="mopen,delimcenter" style="top:0em;">
<span className="delimsizing,size2">

(

</span>
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

<span className="mord">
<span className="mopen,nulldelimiter">



</span>

<span className="mfrac">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.9914em;">
<span style="top:-2.655em;">
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
<span className="vlist" style="height:0.1645em;">
<span style="top:-2.357em;margin-left:-0.0715em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

o

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
<span className="vlist" style="height:0.143em;">
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

<span style="top:-3.23em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="frac-line" style="border-bottom-width:0.04em;">



</span>
</span>

<span style="top:-3.5131em;">
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

d

</span>

<span className="mord,mathnormal,mtight">

e

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
<span className="vlist" style="height:0.2901em;">
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

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.4451em;">
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
<span className="delimsizing,size2">

)

</span>
</span>
</span>
</span>
</span>
</span>

减小，会让<span className="katex">
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

o

</mi>

<mi>

f

</mi>

<mi>

f

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

I_{off}

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

I

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.0785em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

o

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.1076em;">

f

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.1076em;">

f

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

指数级下降。

- **更大**<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
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

V_t

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

：<span className="katex">
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

o

</mi>

<mi>

f

</mi>

<mi>

f

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

I_{off}

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

I

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.0785em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

o

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.1076em;">

f

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.1076em;">

f

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

指数级下降，但<span className="katex">
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

o

</mi>

<mi>

n

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

I_{on}

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
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0785em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
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

也会下降。
- **更大L**：短沟道效应减弱，<span className="katex">
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

o

</mi>

<mi>

f

</mi>

<mi>

f

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

I_{off}

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

I

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.0785em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

o

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.1076em;">

f

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.1076em;">

f

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

会减小，但沟道更长<span className="katex">
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

o

</mi>

<mi>

n

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

I_{on}

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
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0785em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
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

会减小。
- **更小**<span className="katex">
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
</mrow>

<annotation encoding="application/x-tex">

V_{dd}

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
</span>
</span>
</span>

：DIBL 变弱，I_减小，但驱动电压变小<span className="katex">
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

o

</mi>

<mi>

n

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

I_{on}

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
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0785em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
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

还是会降低

</alert>

### 解决方法：抗工艺波动的电路设计 | **Variation Tolerant Circuit Design**

工艺已经发展到可以解决Ion和Ioff之间强烈的折中关系，也就是速度和待机功耗之间的折中。

#### 多阈值电压 | Multiple Vt

一个工艺往往提供2~3个（或者更多）Vt给电路设计者进行选择。一个大的电路可以先采用高Vt的器件来进行设计。电路时序仿真会确定信号路径，以及哪些部分的速度需要调高。这时可以采用中等Vt的器件来替换这部分电路。最后可以采用**低Vt的器件来替换需要更高速的电路，**这部分占的比例往往十分小。

#### 多电源电压 | Multiple Vdd

**高的Vdd可以用于少量的、但需要高速的电路**，而低Vdd可以用于其他电路。更大的Vdd可以提供更高的速度，并且（或者）允许使用更大的Vt来抑制漏电流。最终由于大部分电路在低Vdd下工作，动态功耗可以降低。

> #### 按时间所需调整
> 
> 在类似处理器的大的电路中，**某一时刻**只有某些电路模块需要工作在高速度下，而其他电路工作在低速或者待机状态。需要高速工作的电路可以设置相对较低的 Vt 来产生大的 Ion，使得电路可以工作在高速状态。

#### 阱偏置技术 | Substrate/Well bias

- 只有部分电路模块需要以高速工作，其余部分可以采用**反向阱偏置**来提高 Vt。
- 结合智能控制电路，这些技术还可以减小芯片间（chip-to-chip）和模块间（block-to-block）的**差异**。
- 希望器件具有比传统 MOSFET 更强的体效应（body effect）。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture12-29.webp)

> 引自教材
> 
> 这个阱偏置技术同时提供了**补偿片间和模块间偏差**的方法，这些偏差是由于不可避免地制造设备和制造工艺的偏差导致的。在制造与电路设计之间，可以采用很多技术来减小工艺偏差的问题，这些技术统称为**可制造性设计**(DFM，Design For Manufacturing)。**器件偏差**的一个主要原因是光刻工艺对 Lg 控制的非理想性。有些偏差是随机偏差，有些偏差是或多或少可以预测的，称为**系统偏差**。小尺寸 MOSFET 中掺杂原子数量和位置的统计偏差会导致阈值电压显著波动。为了考虑电路设计中片间和片内的**随机偏差**，需要复杂的设计方法学。

## 超薄体 SOI 及多栅MOSFET | **Ultra-Thin-Body SOI and Multi-gate MOSFETs**

当减小Tox以后，会增大栅极对于硅衬底表面的控制（见左图），但是漏区电压对于 Si 表面以下一定距离的处的漏电路径仍然具有比栅更强的控制作用（见右图）。有两种结构可以来解决这个问题，即超薄体SOI和多栅MOSFET（FinFET，这在下一节PPT中）

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture12-30.webp)

### 超薄体 MOSFET 和 SOI | **Ultra-Thin-Body MOSFET and SOI**

> SOI——Silicon-On-Insulator

超薄体(UTB) MOSFET 制作在位于 SiO₂上的很薄的 Si 薄膜上。由于 Si 薄膜十分薄，也许只有 10 nm，因此远离栅的区域不会出现漏电流路径，从而栅极可以有效地抑制漏电。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture12-31.webp)

下图显示了随着衬底 Si 薄膜厚度降低，亚阈值区漏电流减小的情况。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture12-32.webp)

### **SOI 衬底制备 | Producing Silicon-on-Insulator (SOI) Substrates**

- 准备初始硅晶圆 A 和 B
- 对晶圆 A 进行氧化，生长 SiO₂
- 向晶圆 A 注入氢
- 将晶圆 A 翻转倒扣，放到晶圆 B 上方（原子力键合）
- 低温退火使两片晶圆相互融合
- 再进行一次退火以形成 H₂ 气泡，并使晶圆 A 沿氢注入层剥离/裂开
- 抛光表面后，SOI 晶圆即可使用
- 晶圆 A 可以重复使用

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture12-33.webp)

### SOI 电路的横截面 | **Cross-Section of SOI Circuits**

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture12-34.webp)

由于 SOI 晶圆成本很高，只有一些售价较高、并且以速度竞争为主要卖点的微处理器才采用了这项技术。

为了发挥 UTB（超薄体）的优势，硅薄膜的厚度必须被**大幅**降低到约为 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

L

</mi>

<mi>

g

</mi>
</msub>

<mi mathvariant="normal">

/

</mi>

<mn>

4

</mn>
</mrow>

<annotation encoding="application/x-tex">

L_g/4

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.0361em;vertical-align:-0.2861em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

L

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

g

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

/4

</span>
</span>
</span>
</span>

（其中 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

L

</mi>

<mi>

g

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

L_g

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

L

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

g

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

 为栅长）。
