# Chapter 10：互连 Interconnect

> 串扰、噪声与互连延迟的成因，以及互连线的设计与优化策略。

## VLSI 互连课件笔记（P2–P48）

建议按**6 个板块**学习，逻辑最顺：从“互连为什么重要”到“问题来源”，再到“优化与系统级方案”。

1. **互连基础与寄生效应**（P2–3）
认识互连层、RC/L 寄生参数，以及它们对速度、功耗、噪声和可靠性的总体影响。
2. **电容串扰与噪声分析**（P4–16）
核心概念：<mark>

aggressor / victim

</mark>

、<mark>

噪声和时延

</mark>

、<mark>

浮空与受驱节点

</mark>

、串扰噪声、Miller 效应、延迟变化、动态逻辑的脆弱性。
这一部分是<mark>

全章重点

</mark>

，公式和波形要能看懂。
3. **布局布线上的串扰抑制**（P17–26）
课件给出 6条策略：
  - <mark>
  
  避免浮空节点
  
  </mark>
  
   Avoid floating nodes
  - <mark>
  
  保护敏感节点
  
  </mark>
  
   Protect sensitive nodes （时钟、动态、SRAM/DRAM）
  - <mark>
  
  让上升沿、下降沿不要过快
  
  </mark>
  
   Make rise and fall times as large as possible （边沿越快，<span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mfrac>
  <mrow>
  <mi>
  
  d
  
  </mi>
  
  <mi>
  
  V
  
  </mi>
  </mrow>
  
  <mrow>
  <mi>
  
  d
  
  </mi>
  
  <mi>
  
  t
  
  </mi>
  </mrow>
  </mfrac>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  \frac{dV}{dt}
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
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
  <span className="mord,mathnormal,mtight">
  
  d
  
  </span>
  
  <span className="mord,mathnormal,mtight">
  
  t
  
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
  
  d
  
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
  
   越大，注入 victim 的电流越强，串扰毛刺越大。）
  - 差分信号 Differential signaling
  - <mark>
  
  不要长距离并行走线
  
  </mark>
  
   Do not run wires together for a long distance
  - <mark>
  
  使用屏蔽线、屏蔽层
  
  </mark>
  
   Use shielding wires Use shielding layers
4. <mark>

**供电完整性，VDD和GND长导线优化**

</mark>

（约 P27–32）
重点是 <mark>

IR drop

</mark>

、电源网络、电流切换引起的电压波动，以及如何通过电源/地层降低电阻和电感。
两侧供电 + 网格→四侧供电 + 粗金属网格→专用 VDD/VSS 平面
5. **长距离互联线的互连工艺、布线层与延迟优化**（P33–48）
<mark>

铜、多层金属、对角布线、repeater、终端匹配、低摆幅传输

</mark>

；重点掌握长导线的 RC 延迟为何随长度平方增长，以及 repeater/buffer 插入如何改善延迟。
6. **系统级互连与未来趋势**（P49–58）<mark>

(不考)

</mark>


从片上 bus 过渡到 Network-on-Chip（NoC）、互连 backplane，以及互连技术的发展趋势。

## 第一板块：互连基础与寄生效应（P2–P3）

### P2｜Interconnect Issues in the Chips：为什么“线”这么重要？

芯片并不只是由晶体管组成；实际上，大量面积和设计复杂度都来自于把晶体管连接起来的金属线，也就是 **interconnect（互连）**。

- 互连会影响：

  - **Speed**：导线有电阻和电容，信号传播会变慢；
  - **Power**：给导线电容充放电要消耗能量；
  - **Noise**：相邻导线之间会发生电容耦合，产生串扰。

---

### P3｜Impact of Interconnect Parasitics：寄生参数带来什么问题？

**1. Reduce Robustness：降低鲁棒性**

**2. Affect Performance：影响性能**

- **Increase delay**
- **Increase power dissipation**

---

## 第二板块：电容串扰、噪声与延迟（P4–P16）

### P4｜Crosstalk：串扰到底是什么？

两根靠得很近、平行走线较长的金属线，本质上像两个电容极板，中间存在耦合电容。

当其中一根线电压快速改变时，另一根线会因为这个耦合电容被“带动”一点，这就是 **crosstalk（串扰）** 或 **capacitive coupling（电容耦合）**。

#### 两种后果

**1. 非翻转导线产生噪声（noise)  “不该动的线动一下”**

**2. 正在翻转的导线延迟变大 （delay） “正在动的线动得更慢”**

---

### P5｜RC Crosstalk：aggressor 与 victim

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter10-Interconnect-01.webp)

这页引入串扰分析中的两个标准角色：

- **Aggressor net（攻击线）**：发生翻转、产生干扰的导线；
- **Victim net（受害线）**：被耦合影响的导线。

若victim本身不动就是噪声（noise）

若victim本身也在翻转就是延时delay

---

### P6-8｜Crosstalk Noise：串扰噪声

#### **victim浮空的情况：**

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter10-Interconnect-02.webp)

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi mathvariant="normal">

Δ

</mi>

<msub>
<mi>

V

</mi>

<mtext>

victim

</mtext>
</msub>

<mo>

=

</mo>

<mfrac>
<msub>
<mi>

C

</mi>

<mtext>

adj

</mtext>
</msub>

<mrow>
<msub>
<mi>

C

</mi>

<mtext>

gnd-v

</mtext>
</msub>

<mo>

+

</mo>

<msub>
<mi>

C

</mi>

<mtext>

adj

</mtext>
</msub>
</mrow>
</mfrac>

<mi mathvariant="normal">

Δ

</mi>

<msub>
<mi>

V

</mi>

<mtext>

aggressor

</mtext>
</msub>
</mrow>

<annotation encoding="application/x-tex">

\Delta V_{\text{victim}} = \frac{C_{\text{adj}}} {C_{\text{gnd-v}}+C_{\text{adj}}} \Delta V_{\text{aggressor}}

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
<span className="vlist" style="height:0.3175em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,text,mtight">
<span className="mord,mtight">

victim

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
<span className="mord,text,mtight">
<span className="mord,mtight">

gnd-v

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

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



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
<span className="mord,text,mtight">
<span className="mord,mtight">

adj

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
<span className="mord,text,mtight">
<span className="mord,mtight">

adj

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
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,text,mtight">
<span className="mord,mtight">

aggressor

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
</span>

- <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

C

</mi>

<mtext>

adj

</mtext>
</msub>
</mrow>

<annotation encoding="application/x-tex">

C_{\text{adj}}

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
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,text,mtight">
<span className="mord,mtight">

adj

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

 越大，耦合越强，victim 被带动得越明显；
- <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

C

</mi>

<mtext>

gnd-v

</mtext>
</msub>
</mrow>

<annotation encoding="application/x-tex">

C_{\text{gnd-v}}

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
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,text,mtight">
<span className="mord,mtight">

gnd-v

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

 越大，victim 越“稳”，噪声越小；
- aggressor 翻转幅度越大，victim 噪声也越大。

若：

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

<mtext>

adj

</mtext>
</msub>

<mo>

=

</mo>

<msub>
<mi>

C

</mi>

<mtext>

gnd-v

</mtext>
</msub>
</mrow>

<annotation encoding="application/x-tex">

C_{\text{adj}}=C_{\text{gnd-v}}

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
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,text,mtight">
<span className="mord,mtight">

adj

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
<span className="strut" style="height:0.9694em;vertical-align:-0.2861em;">



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
<span className="mord,text,mtight">
<span className="mord,mtight">

gnd-v

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
</span>

则：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi mathvariant="normal">

Δ

</mi>

<msub>
<mi>

V

</mi>

<mtext>

victim

</mtext>
</msub>

<mo>

=

</mo>

<mfrac>
<mn>

1

</mn>

<mn>

2

</mn>
</mfrac>

<mi mathvariant="normal">

Δ

</mi>

<msub>
<mi>

V

</mi>

<mtext>

aggressor

</mtext>
</msub>
</mrow>

<annotation encoding="application/x-tex">

\Delta V_{\text{victim}} = \frac{1}{2}\Delta V_{\text{aggressor}}

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
<span className="vlist" style="height:0.3175em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,text,mtight">
<span className="mord,mtight">

victim

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
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,text,mtight">
<span className="mord,mtight">

aggressor

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
</span>

#### **victim 被驱动时：**

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter10-Interconnect-03.webp)

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi mathvariant="normal">

Δ

</mi>

<msub>
<mi>

V

</mi>

<mtext>

victim

</mtext>
</msub>

<mo>

=

</mo>

<mfrac>
<msub>
<mi>

C

</mi>

<mtext>

adj

</mtext>
</msub>

<mrow>
<msub>
<mi>

C

</mi>

<mtext>

gnd-v

</mtext>
</msub>

<mo>

+

</mo>

<msub>
<mi>

C

</mi>

<mtext>

adj

</mtext>
</msub>
</mrow>
</mfrac>

<mo>

⋅

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

+

</mo>

<mi>

k

</mi>
</mrow>
</mfrac>

<mi mathvariant="normal">

Δ

</mi>

<msub>
<mi>

V

</mi>

<mtext>

aggressor

</mtext>
</msub>
</mrow>

<annotation encoding="application/x-tex">

\Delta V_{\text{victim}} = \frac{C_{\text{adj}}} {C_{\text{gnd-v}}+C_{\text{adj}}} \cdot \frac{1}{1+k} \Delta V_{\text{aggressor}}

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
<span className="vlist" style="height:0.3175em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,text,mtight">
<span className="mord,mtight">

victim

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
<span className="mord,text,mtight">
<span className="mord,mtight">

gnd-v

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

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



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
<span className="mord,text,mtight">
<span className="mord,mtight">

adj

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
<span className="mord,text,mtight">
<span className="mord,mtight">

adj

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

⋅

</span>

<span className="mspace" style="margin-right:0.2222em;">



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

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0315em;">

k

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
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,text,mtight">
<span className="mord,mtight">

aggressor

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
</span>

其中：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

k

</mi>

<mo>

=

</mo>

<mfrac>
<msub>
<mi>

τ

</mi>

<mtext>

aggressor

</mtext>
</msub>

<msub>
<mi>

τ

</mi>

<mtext>

victim

</mtext>
</msub>
</mfrac>

<mo>

=

</mo>

<mfrac>
<mrow>
<msub>
<mi>

R

</mi>

<mtext>

aggressor

</mtext>
</msub>

<mo stretchy="false">

(

</mo>

<msub>
<mi>

C

</mi>

<mtext>

gnd-a

</mtext>
</msub>

<mo>

+

</mo>

<msub>
<mi>

C

</mi>

<mtext>

adj

</mtext>
</msub>

<mo stretchy="false">

)

</mo>
</mrow>

<mrow>
<msub>
<mi>

R

</mi>

<mtext>

victim

</mtext>
</msub>

<mo stretchy="false">

(

</mo>

<msub>
<mi>

C

</mi>

<mtext>

gnd-v

</mtext>
</msub>

<mo>

+

</mo>

<msub>
<mi>

C

</mi>

<mtext>

adj

</mtext>
</msub>

<mo stretchy="false">

)

</mo>
</mrow>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

k= \frac{\tau_{\text{aggressor}}} {\tau_{\text{victim}}} = \frac{R_{\text{aggressor}}(C_{\text{gnd-a}}+C_{\text{adj}})} {R_{\text{victim}}(C_{\text{gnd-v}}+C_{\text{adj}})}

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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.9436em;vertical-align:-0.836em;">



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
<span className="mord,mathnormal" style="margin-right:0.1132em;">

τ

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3175em;">
<span style="top:-2.55em;margin-left:-0.1132em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,text,mtight">
<span className="mord,mtight">

victim

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
<span className="mord,mathnormal" style="margin-right:0.1132em;">

τ

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.1132em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,text,mtight">
<span className="mord,mtight">

aggressor

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
<span className="strut" style="height:2.3991em;vertical-align:-0.9721em;">



</span>

<span className="mord">
<span className="mopen,nulldelimiter">



</span>

<span className="mfrac">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:1.427em;">
<span style="top:-2.314em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0077em;">

R

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3175em;">
<span style="top:-2.55em;margin-left:-0.0077em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,text,mtight">
<span className="mord,mtight">

victim

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
<span className="mord,text,mtight">
<span className="mord,mtight">

gnd-v

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

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



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
<span className="mord,text,mtight">
<span className="mord,mtight">

adj

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
<span className="mord,mtight">
<span className="mord,text,mtight">
<span className="mord,mtight">

aggressor

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

<span className="mopen">

(

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
<span className="mord,text,mtight">
<span className="mord,mtight">

gnd-a

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

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



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
<span className="mord,text,mtight">
<span className="mord,mtight">

adj

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

<span className="mclose">

)

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
</span>
</span>

<span className="katex">
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

 为驱动器的相对驱动能力

victim 驱动越强，<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

R

</mi>

<mtext>

victim

</mtext>
</msub>
</mrow>

<annotation encoding="application/x-tex">

R_{\text{victim}}

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
<span className="vlist" style="height:0.3175em;">
<span style="top:-2.55em;margin-left:-0.0077em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,text,mtight">
<span className="mord,mtight">

victim

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
</span>

 越小；<span className="katex">
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

 越大；<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mfrac>
<mn>

1

</mn>

<mrow>
<mn>

1

</mn>

<mo>

+

</mo>

<mi>

k

</mi>
</mrow>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

\frac{1}{1+k}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.2484em;vertical-align:-0.4033em;">



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

1

</span>

<span className="mbin,mtight">

+

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0315em;">

k

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
</span>
</span>
</span>

 越小；最终噪声越低。

> 强驱动的 victim 更容易把被耦合进来的电荷泄掉或补回来。

#### **Coupling Waveforms**

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter10-Interconnect-04.webp)

---

### P9｜Crosstalk Delay：串扰时延

这页讨论的是：victim 本身也在翻转时，邻线的行为如何改变其延迟。

对于待分析导线 A，邻线 B 的状态决定了耦合电容对 A 的“有效负载”。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter10-Interconnect-05.webp)

如果B不动的时候，对于A来说，B就相当于GND

---

### P10-11｜Wire Cross-section：两侧都有攻击线时

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter10-Interconnect-06.webp)

> 两侧邻线同时反向切换，是互连延迟的典型最坏模式。

---

### P12｜Capacitive Crosstalk: Dynamic Node：为什么动态逻辑特别危险？

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter10-Interconnect-07.webp)

#### 为什么动态节点更脆弱？

静态 CMOS 的输出通常一直由上拉或下拉网络驱动，因此有“恢复能力”。

但动态节点在评估期常常是靠电容存储电荷：

Y 实际上就处于一种高阻、近似浮空的状态，很容易受串扰的影响

---

### P13｜Cross Talk and Performance：Miller Effect 的本质

Miller Effect 导致电容等效变大，时延增加

---

### P14｜Impact of Crosstalk on Delay：三线总线的延迟因子

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter10-Interconnect-08.webp)

> 中间线翻转时，两侧邻线都反向翻转，是最坏延迟模式；两侧都同向翻转，是最佳模式。

---

### P15｜Capacitive Crosstalk Driven Node：受驱节点的时间常数

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter10-Interconnect-09.webp)

即希望：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<msub>
<mi>

τ

</mi>

<mrow>
<mi>

X

</mi>

<mi>

Y

</mi>
</mrow>
</msub>

<mo>
<

</mo>

<msub>
<mi>

t

</mi>

<mi>

r

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

\tau_{XY}<t_r

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6891em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.1132em;">

τ

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.1132em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0785em;">

X

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.2222em;">

Y

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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
<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

r

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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

这样 victim 的驱动器有足够快的能力去抵消耦合注入电荷，受害节点不会被拉出很高、很宽的噪声脉冲。

---

### P16｜Noise Implications：有噪声就一定出错吗？

不一定。

#### 情况 1：噪声小于噪声容限

#### 情况 2：静态 CMOS

但仍然可能有两个代价：

- **额外延迟**
- **额外功耗**

#### 情况 3：动态逻辑

动态逻辑很危险。

#### 情况 4：存储器和敏感模拟/时序电路

例如 SRAM、Sense Amplifier、锁存器、时钟路径等，<mark>

对小扰动都可能敏感

</mark>

，进而产生错误读写或错误采样。

---

## P2–P16 最终串联总结

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mtext>

导线靠得近

</mtext>

<mo>

→

</mo>

<msub>
<mi>

C

</mi>

<mtext>

adj

</mtext>
</msub>

<mtext>

增大

</mtext>

<mo>

→

</mo>

<mtext>

邻线翻转时产生耦合电流

</mtext>

<mo>

→

</mo>

<mrow>
<mo fence="true">

{

</mo>

<mtable rowspacing="0.36em" columnalign="left left" columnspacing="1em">
<mtr>
<mtd>
<mstyle scriptlevel="0" displaystyle="false">
<mtext>

静止/浮空 victim：产生噪声

</mtext>
</mstyle>
</mtd>
</mtr>

<mtr>
<mtd>
<mstyle scriptlevel="0" displaystyle="false">
<mtext>

翻转 victim：有效电容增加、延迟增大

</mtext>
</mstyle>
</mtd>
</mtr>
</mtable>
</mrow>
</mrow>

<annotation encoding="application/x-tex">

\text{导线靠得近} \rightarrow C_{\text{adj}}增大 \rightarrow \text{邻线翻转时产生耦合电流} \rightarrow \begin{cases} \text{静止/浮空 victim：产生噪声}\\ \text{翻转 victim：有效电容增加、延迟增大} \end{cases}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,text">
<span className="mord,cjk_fallback">

导线靠得近

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
<span className="strut" style="height:0.9694em;vertical-align:-0.2861em;">



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
<span className="mord,text,mtight">
<span className="mord,mtight">

adj

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

<span className="mord,cjk_fallback">

增大

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

邻线翻转时产生耦合电流

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
<span className="strut" style="height:3em;vertical-align:-1.25em;">



</span>

<span className="minner">
<span className="mopen,delimcenter" style="top:0em;">
<span className="delimsizing,size4">

{

</span>
</span>

<span className="mord">
<span className="mtable">
<span className="col-align-l">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:1.69em;">
<span style="top:-3.69em;">
<span className="pstrut" style="height:3.008em;">



</span>

<span className="mord">
<span className="mord,text">
<span className="mord,cjk_fallback">

静止

</span>

<span className="mord">

/

</span>

<span className="mord,cjk_fallback">

浮空

</span>

<span className="mord">

victim

</span>

<span className="mord,cjk_fallback">

：产生噪声

</span>
</span>
</span>
</span>

<span style="top:-2.25em;">
<span className="pstrut" style="height:3.008em;">



</span>

<span className="mord">
<span className="mord,text">
<span className="mord,cjk_fallback">

翻转

</span>

<span className="mord">

victim

</span>

<span className="mord,cjk_fallback">

：有效电容增加、延迟增大

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:1.19em;">
<span>



</span>
</span>
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

最重要的三个结论是：

1. **浮空节点最怕串扰**：电容分压直接决定噪声幅度。
2. **反向翻转最慢**：Miller 效应使耦合电容的等效负载翻倍。
3. **双侧邻线反向翻转最坏**：中间线的等效耦合负载可达到 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mn>

4

</mn>

<msub>
<mi>

C

</mi>

<mn>

21

</mn>
</msub>
</mrow>

<annotation encoding="application/x-tex">

4C_{21}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">

4

</span>

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
<span className="mord,mtight">

21

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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

---

## 第三板块：串扰抑制、布线优化与输出驱动（P17–P26）

**既然互连会产生串扰、噪声和延迟，那么版图、布线和驱动电路该怎样设计？**

---

### P17｜Dealing with Capacitive Cross Talk：抑制电容串扰的总原则

课件给出 6条策略：

- <mark>

避免浮空节点

</mark>

 Avoid floating nodes
- 保护敏感节点 Protect sensitive nodes （时钟、动态、SRAM/DRAM）
- <mark>

让上升沿、下降沿不要过快

</mark>

 Make rise and fall times as large as possible （边沿越快，<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mfrac>
<mrow>
<mi>

d

</mi>

<mi>

V

</mi>
</mrow>

<mrow>
<mi>

d

</mi>

<mi>

t

</mi>
</mrow>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

\frac{dV}{dt}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
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
<span className="mord,mathnormal,mtight">

d

</span>

<span className="mord,mathnormal,mtight">

t

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

d

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

 越大，注入 victim 的电流越强，串扰毛刺越大。）
- 差分信号 Differential signaling
- <mark>

不要长距离并行走线

</mark>

 Do not run wires together for a long distance
- <mark>

使用屏蔽线、屏蔽层

</mark>

 Use shielding wires Use shielding layers

---

### P18｜Shielding：屏蔽线和屏蔽层的做法

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter10-Interconnect-10.webp)

---

### P19｜Structured Predictable Interconnect：结构化、可预测的互连

这页提出一种更系统的想法：

> 不只是某条危险线临时加屏蔽，而是从布线规则上就让相邻关系可控、可预测。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter10-Interconnect-11.webp)

---

### P20｜Crosstalk Optimization Example：通过改变线序降低串扰（减少重叠并行）

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter10-Interconnect-12.webp)

---

### P21｜Twizzled Wires：交织 / 扭绞式布线  （减少长距离平行）

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter10-Interconnect-13.webp)

---

### P22｜Encoding Data：用编码避免最坏切换模式

核心思想是：

> 不直接把原始数据送到总线上，而是先编码，避免最坏的相邻反向翻转模式。

---

### P23-25｜Using Cascaded Buffers：级联缓冲器驱动大负载

互连带来的大电容负载，怎样被驱动器高效驱动。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter10-Interconnect-14.webp)

---

### P26｜Tristate Buffers：共享总线为什么需要高阻态？（总线不考）

高阻态不是逻辑 0，也不是逻辑 1，而是：

> 输出端基本与总线断开，不主动驱动电压。

共享总线往往长、连接模块多，总电容较大，需要更强的<mark>

输出驱动能力

</mark>

。

未驱动的 Z 总线会接近浮空，容易受到串扰；实际设计中通常会配合 bus keeper、上拉/下拉或严格时序控制，避免它长时间完全悬空。

---

### P17–P26 一条主线总结

- **P17–P19**：屏蔽、敏感节点保护、结构化布线；
- **P20–P22**：线序优化、交织布线、编码避免最坏切换；
- **P23–P25**：用级联 buffer 驱动互联带来的大负载；
- **P26**：共享总线用三态缓冲器避免争用。

---

## 第四板块：电源线和地线的全局interconnect（P27–P32）

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mtext>

电源线有电阻

</mtext>

<mo>

→

</mo>

<mtext>

电流流过时产生

</mtext>

<mi>

I

</mi>

<mi>

R

</mi>

<mtext>

压降

</mtext>

<mo>

→

</mo>

<mtext>

局部

</mtext>

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

<mtext>

降低、局部 GND 抬高

</mtext>

<mo>

→

</mo>

<mtext>

速度、噪声裕量和可靠性变差

</mtext>
</mrow>

<annotation encoding="application/x-tex">

\text{电源线有电阻} \rightarrow \text{电流流过时产生 }IR\text{ 压降} \rightarrow \text{局部 }V_{DD}\text{ 降低、局部 GND 抬高} \rightarrow \text{速度、噪声裕量和可靠性变差}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,text">
<span className="mord,cjk_fallback">

电源线有电阻

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

电流流过时产生

</span>

<span className="mord">



</span>
</span>

<span className="mord,mathnormal" style="margin-right:0.0785em;">

I

</span>

<span className="mord,mathnormal" style="margin-right:0.0077em;">

R

</span>

<span className="mord,text">
<span className="mord">



</span>

<span className="mord,cjk_fallback">

压降

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

<span className="mord,text">
<span className="mord,cjk_fallback">

局部

</span>

<span className="mord">



</span>
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

<span className="mord,text">
<span className="mord">



</span>

<span className="mord,cjk_fallback">

降低、局部

</span>

<span className="mord">

GND

</span>

<span className="mord,cjk_fallback">

抬高

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

速度、噪声裕量和可靠性变差

</span>
</span>
</span>
</span>
</span>
</span>

这里关心的是**整颗芯片怎样把稳定的电源和地送到每一个门电路**。

---

### P27｜Impact of Resistance：电阻最典型的问题发生在电源分配

课件先说：RC 互连的驱动问题前面已经讨论过；现在重点看电阻在 **power supply distribution（供电分配网络）** 中的影响。主要有两类：

- **IR drop**：电流流过电源线电阻时产生压降；
- **Voltage variations**：大量门电路同步翻转时，局部供电电压会波动。

最基本关系是：

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

V

</mi>

<mo>

=

</mo>

<mi>

I

</mi>

<mi>

R

</mi>
</mrow>

<annotation encoding="application/x-tex">

\Delta V=IR

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

<span className="mord,mathnormal" style="margin-right:0.2222em;">

V

</span>

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

<span className="mord,mathnormal" style="margin-right:0.0785em;">

I

</span>

<span className="mord,mathnormal" style="margin-right:0.0077em;">

R

</span>
</span>
</span>
</span>
</span>

因此，课件强调电源网络的目标是同时减小：

1. 静态的 IR drop；
2. 门切换带来的瞬态电流变化。 

---

### P29｜Resistance and the Power Distribution Problem：为什么电源网络必须做分析？

做电源完整性分析时，不能只看版图里某一根电源线，而要把它看成跨越芯片、封装和板级系统的完整网络。 

---

### P30-32｜3 Metal Layer Approach（EV4\5\6）：三层金属下怎样做供电？

<mark>

**随着芯片规模变大，如何不断升级金属层和供电拓扑，以降低电源网络的电阻与电感。**

</mark>


两侧供电 + 网格→四侧供电 + 粗金属网格→专用 VDD/VSS 平面

---

## 第五板块：<mark>全局互连、长线互联优化</mark>与信号完整性（P33–P48）

这一段的主线是：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mtext>

芯片越来越大、全局线越来越长

</mtext>

<mo>

→

</mo>

<mtext>

RC 延迟和反射/噪声成为瓶颈

</mtext>

<mo>

→

</mo>

<mtext>

采用铜、多层金属、对角布线、repeater、终端匹配、低摆幅传输等方法

</mtext>
</mrow>

<annotation encoding="application/x-tex">

\text{芯片越来越大、全局线越来越长} \rightarrow \text{RC 延迟和反射/噪声成为瓶颈} \rightarrow \text{采用铜、多层金属、对角布线、repeater、终端匹配、低摆幅传输等方法}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,text">
<span className="mord,cjk_fallback">

芯片越来越大、全局线越来越长

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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord,text">
<span className="mord">

RC

</span>

<span className="mord,cjk_fallback">

延迟和反射

</span>

<span className="mord">

/

</span>

<span className="mord,cjk_fallback">

噪声成为瓶颈

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
<span className="strut" style="height:0.8778em;vertical-align:-0.1944em;">



</span>

<span className="mord,text">
<span className="mord,cjk_fallback">

采用铜、多层金属、对角布线、

</span>

<span className="mord">

repeater

</span>

<span className="mord,cjk_fallback">

、终端匹配、低摆幅传输等方法

</span>
</span>
</span>
</span>
</span>
</span>

- <mark>

铜

</mark>
- <mark>

多层金属

</mark>
- <mark>

对角布线

</mark>
- <mark>

Repeater

</mark>
- <mark>

终端匹配

</mark>
- <mark>

低摆幅传输

</mark>

**长距离全局互连如何可靠、高速地传递信息**。

---

### P33｜The Global Wire Problem：全局长线为什么最难处理？

根据公式

> **长线自身的 RC 延迟与长度平方** <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msup>
> <mi>
> 
> L
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
> L^2
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
> <span className="mord,mathnormal">
> 
> L
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
>  **成正比。**

这意味着芯片尺寸稍大一些，全局线延迟可能迅速上升。

> 当互连延迟接近甚至超过逻辑门延迟时，系统架构必须为通信延迟服务。

---

### P34｜Interconnect Projections: Copper：为什么金属从铝转向铜？

**1. 降低线电阻**

铜的电阻率更低

**2. 改善 electromigration（电迁移）可靠性**

铜电迁移寿命好

---

### P35｜Interconnect: # of Wiring Layers：为什么金属层数持续增加？

1. 芯片更大、器件更多
2. 需要层次化布线网络

- <mark>

**Local wires**

</mark>

<mark>

：高密度、短距离，用于连接附近标准单元；

</mark>
- <mark>

**Global wires**

</mark>

<mark>

：低 RC、长距离，用于跨模块、时钟、电源和总线

</mark>

。

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mtext>

低层：密度优先

</mtext>

<mspace width="2em">



</mspace>

<mtext>

高层：性能与供电优先

</mtext>
</mrow>

<annotation encoding="application/x-tex">

\text{低层：密度优先} \qquad \text{高层：性能与供电优先}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,text">
<span className="mord,cjk_fallback">

低层：密度优先

</span>
</span>

<span className="mspace" style="margin-right:2em;">



</span>

<span className="mord,text">
<span className="mord,cjk_fallback">

高层：性能与供电优先

</span>
</span>
</span>
</span>
</span>
</span>

---

### P36｜Diagonal Wiring：为什么对角布线能减少长度？

短

---

### P37-39｜Reducing RC-delay：插入 repeater 的基本模型

超长导线中间分段插入 repeater，降低导线 RC 延迟

---

### P40｜Matched Termination：为什么长线要做阻抗匹配？

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter10-Interconnect-15.webp)

当信号边沿很快、导线很长时，导线不能只看成 RC 网络，而可能需要近似为<mark>

传输线。

</mark>



若驱动端或接收端阻抗不匹配，信号到达端点后会发生反射，造成：

- 反射；
- 振铃；
- 过冲 / 欠冲；

**图中的两种方法**

1. Series Source Termination：源端串联

在源端串联电阻，使源端等效阻抗接近：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<msub>
<mi>

Z

</mi>

<mi>

S

</mi>
</msub>

<mo>

≈

</mo>

<msub>
<mi>

Z

</mi>

<mn>

0

</mn>
</msub>
</mrow>

<annotation encoding="application/x-tex">

Z_S\approx Z_0

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

Z

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

≈

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0715em;">

Z

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
</span>
</span>

1. Parallel Destination Termination：终端并联匹配

在接收端接上近似：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<msub>
<mi>

Z

</mi>

<mi>

L

</mi>
</msub>

<mo>

=

</mo>

<msub>
<mi>

Z

</mi>

<mn>

0

</mn>
</msub>
</mrow>

<annotation encoding="application/x-tex">

Z_L=Z_0

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

Z

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

L

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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
<span className="mord,mathnormal" style="margin-right:0.0715em;">

Z

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
</span>
</span>

---

### P41｜Segmented Matched Line Driver：分段匹配驱动器

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter10-Interconnect-16.webp)

把驱动器拆成多个可控部分。这样可以通过控制打开多少个 segment

调节等效输出电阻：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

R

</mi>

<mtext>

driver,eq

</mtext>
</msub>
</mrow>

<annotation encoding="application/x-tex">

R_{\text{driver,eq}}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9694em;vertical-align:-0.2861em;">



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
<span className="mord,mtight">
<span className="mord,text,mtight">
<span className="mord,mtight">

driver,eq

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

使他尽可能接近<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

Z

</mi>

<mn>

0

</mn>
</msub>
</mrow>

<annotation encoding="application/x-tex">

Z_0

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

Z

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
</span>



---

### P42｜Parallel Termination - Transistors as Resistors：MOS 管如何充当终端电阻？

这页展示用 NMOS、PMOS 或 CMOS 结构来实现“可集成的终端电阻”。

> MOS 终端电阻便于片上集成和调节，但它是非线性的，不能完全等同于理想固定电阻。使用 NMOS 与 PMOS 组合，通常可以让电阻变化更平坦一些。

---

### P43｜Reducing the Swing：降低摆幅以改善互连速度和功耗

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

p

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

<mfrac>
<mrow>
<msub>
<mi>

C

</mi>

<mi>

L

</mi>
</msub>

<msub>
<mi>

V

</mi>

<mtext>

swing

</mtext>
</msub>
</mrow>

<mrow>
<mn>

2

</mn>

<msub>
<mi>

I

</mi>

<mtext>

av

</mtext>
</msub>
</mrow>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

t_{pHL} = \frac{C_LV_{\text{swing}}}{2I_{\text{av}}}

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
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

p

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
<span className="mord,text,mtight">
<span className="mord,mtight">

av

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
<span className="mord,mathnormal,mtight">

L

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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

V

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3175em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,text,mtight">
<span className="mord,mtight">

swing

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
</span>
</span>
</span>
</span>

---

### P44｜Single-Ended Static Driver and Receiver：单端低摆幅驱动与恢复

左边是 driver，右边是 receiver。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter10-Interconnect-17.webp)

> 低摆幅可以让“线上传输”更快、更省电；左侧 driver 将信号送到较低摆幅的长线， 右侧接收端则负责把弱信号恢复为标准 CMOS 逻辑电平。

---

### P45｜Technology Scaling Trends: Total Interconnect Length on a Chip

> 未来工艺越先进，互连设计的重要性越高。

---

### P46｜Technology Scaling Trends: Interconnect Performance

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter10-Interconnect-18.webp)

> 随工艺缩放，门延迟会下降，但全局导线延迟不一定下降；不加 repeater 的全局线甚至可能成为性能瓶颈。

---

### P47｜Signal Integrity：“信号完整性”？  （互连好不好，不只看延迟）

---

### P48｜noise：噪声是一个系统级问题

这页把前面学过的各种噪声放在一张图里。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter10-Interconnect-19.webp)

---

## P33–P48 最终复习框架

你可以按下面五条记忆这一板块：

1. **全局线 RC 延迟随长度平方增长。**
2. **铜、更宽高层金属、更多布线层可降低互连阻力。**
3. **长线常用 repeater 分段，但会增加面积与功耗。**
4. **高速长线需要考虑阻抗匹配、反射和低摆幅传输。**
5. **信号完整性是电源、封装、互连、噪声与接收器共同决定的系统问题。**

---

BUS不考
