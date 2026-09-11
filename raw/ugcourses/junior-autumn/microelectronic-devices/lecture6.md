# Lecture 6：正向偏置 PN 结与理想二极管方程

> 正向偏置与低水平注入、结定律、连续性方程与扩散方程、理想晶体管 I-V 方程的推导

> 这一讲的核心是利用L4的输运方程和L5的势垒模型，推导PN结在正向偏置下的I-V特性
> 
> 配合PPT食用更美味

## 一、Review

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 50.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture6-01.webp" />
      </p>
    </td>
    
    
      <td style="width: 49.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture6-02.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

P1  上一节的内容，主要是正向偏置，变成了（<span className="katex">
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

A

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

V_{bi}-V_A

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

bi

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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

）

P2  上一节的内容，展示线性缓变结，依次积分，再积分。从电荷（一次函数）到电场（二次函数）到电势（三次函数）

## 二、Forward Biased PN Junction | 正向偏置

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture6-03.webp)

- **条件：**<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

V

</mi>

<mi>

A

</mi>
</msub>

<mo>
<

</mo>

<mo>
<

</mo>

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
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

V_A<<V_{bi}

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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">
<<

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
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

bi

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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

  <mark>

(否则不满足Low level injection)

</mark>

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture6-04.webp)

- <mark>

加入正向偏置电压，n区fermi-level被抬高，p区Fermi-level被拉低，落差变小，N区的能带相对P区

</mark>

<mark>

**抬高**

</mark>

 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

q

</mi>

<msub>
<mi>

V

</mi>

<mi>

A

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

qV_A

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8778em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

q

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

<mark>

。(Ec或者Ev高的是P区)

</mark>
- 外加电场与内建电场方向相反，总势垒**降低**为 <span className="katex">
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

A

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

V_{bi} - V_A

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

bi

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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

。
- 耗尽层宽度 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

W

</mi>
</mrow>

<annotation encoding="application/x-tex">

W

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

W

</span>
</span>
</span>
</span>

 **变窄** 。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture6-05.webp)

<mark>

少子注入（在准中性区完成和另一边的多数载流子的复合）

</mark>



![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture6-06.webp)

When a forward bias (<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

V

</mi>

<mi>

A

</mi>
</msub>

<mo>

>
</mo>

<mn>

0

</mn>
</mrow>

<annotation encoding="application/x-tex">

V_A > 0

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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

>
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

) is applied, the potential barrier to diffusion across the junction is reduced,  <mark>

Minority carriers are 'injected' into the quasi-neutral regions =>
</mark>

 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi mathvariant="normal">

Δ

</mi>

<msub>
<mi>

n

</mi>

<mi>

p

</mi>
</msub>

<mo>

>
</mo>

<mn>

0

</mn>
</mrow>

<annotation encoding="application/x-tex">

\Delta n_p > 0

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9694em;vertical-align:-0.2861em;">



</span>

<span className="mord">

Δ

</span>

<span className="mord">
<span className="mord,mathnormal">

n

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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

>
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

<mark>

,

</mark>

 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi mathvariant="normal">

Δ

</mi>

<msub>
<mi>

p

</mi>

<mi>

n

</mi>
</msub>

<mo>

>
</mo>

<mn>

0

</mn>
</mrow>

<annotation encoding="application/x-tex">

\Delta p_n > 0

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8778em;vertical-align:-0.1944em;">



</span>

<span className="mord">

Δ

</span>

<span className="mord">
<span className="mord,mathnormal">

p

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

n

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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

>
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

Minority carriers diffuse in the quasi-neutral regions, recombining with majority carriers

**PN结的正向电流 = 少子注入 + 扩散 + 复合**

1. **正向电压** <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mo>

→

</mo>
</mrow>

<annotation encoding="application/x-tex">

\rightarrow

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.3669em;">



</span>

<span className="mrel">

→

</span>
</span>
</span>
</span>

 **势垒降低**。
2. 势垒降低 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mo>

→

</mo>
</mrow>

<annotation encoding="application/x-tex">

\rightarrow

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.3669em;">



</span>

<span className="mrel">

→

</span>
</span>
</span>
</span>

 允许大量多子越过边界，变成“少子注入”。
3. 注入的少子在另一侧（准中性区）进行**扩散**运动。
4. 在扩散的过程中，它们与另一侧的多子相遇并**复合**。

正是这个“注入-扩散-复合”**的连续过程，构成了二极管**正向导通时的主体电流。

## 三、Low-level injection | 低水平注入

**低电平注入**是一个**电流输运假设**，它定义了**正向偏置**时载流子的状态。

- **假设内容：** 注入到中性区的**过剩少数载流子**浓度（例如 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi mathvariant="normal">

Δ

</mi>

<msub>
<mi>

p

</mi>

<mi>

n

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

\Delta p_n

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8778em;vertical-align:-0.1944em;">



</span>

<span className="mord">

Δ

</span>

<span className="mord">
<span className="mord,mathnormal">

p

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

n

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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

）**远小于**该区域原有的**多数载流子**浓度

（The <mark>

excess minority carrier concentration

</mark>

 injected into the neutral region is much smaller than the original majority carrier concentration in this region.）

- **适用条件：** 仅在**正向偏置**（<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

V

</mi>

<mi>

A

</mi>
</msub>

<mo>

>
</mo>

<mn>

0

</mn>
</mrow>

<annotation encoding="application/x-tex">

V_A > 0

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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

>
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

）下使用  且  <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

V

</mi>

<mi>

A

</mi>
</msub>

<mo>
<

</mo>

<mo>
<

</mo>

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
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

V_A<<V_{bi}

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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">
<<

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
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

bi

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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

 （低电平的叫法的由来）。

---

它被用于推导**理想二极管I-V方程**的*每一个关键步骤*：

1. **推导：准费米能级分裂**
LLI 假设中性区（多子浓度很高）的电阻小到可以忽略。因此，我们可以假设**几乎所有的外加电压** <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

V

</mi>

<mi>

A

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

V_A

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

 **都降落在耗尽区**上
2. **推导：“结定律”（边界条件）****LLI 假设**告诉我们：尽管有少子注入，但多子浓度基本不变，即 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

n

</mi>

<mi>

n

</mi>
</msub>

<mo stretchy="false">

(

</mo>

<msub>
<mi>

x

</mi>

<mi>

n

</mi>
</msub>

<mo stretchy="false">

)

</mo>

<mo>

≈

</mo>

<msub>
<mi>

N

</mi>

<mi>

D

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

n_n(x_n) \approx N_D

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

n

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

n

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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
<span className="mord,mathnormal">

x

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

n

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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

≈

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
3. **推导：少数载流子扩散方程**
在中性区，总电流 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

J

</mi>
</mrow>

<annotation encoding="application/x-tex">

J

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0962em;">

J

</span>
</span>
</span>
</span>

 包含漂移和扩散。**LLI 假设**中性区的电场 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi mathvariant="script">

E

</mi>
</mrow>

<annotation encoding="application/x-tex">

\mathcal{E}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathcal" style="margin-right:0.0894em;">

E

</span>
</span>
</span>
</span>

 极小（见应用点1），因此**少数载流子**的漂移电流 (<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

q

</mi>

<msub>
<mi>

μ

</mi>

<mi>

p

</mi>
</msub>

<msub>
<mi>

p

</mi>

<mi>

n

</mi>
</msub>

<mi mathvariant="script">

E

</mi>
</mrow>

<annotation encoding="application/x-tex">

q\mu_p p_n \mathcal{E}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9694em;vertical-align:-0.2861em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

q

</span>

<span className="mord">
<span className="mord,mathnormal">

μ

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

<span className="mord">
<span className="mord,mathnormal">

p

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

n

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>

<span className="mord,mathcal" style="margin-right:0.0894em;">

E

</span>
</span>
</span>
</span>

) 可以忽略不计，这使得少数载流子电流 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

J

</mi>

<mi>

p

</mi>
</msub>

<mo>

≈

</mo>

<mo>

−

</mo>

<mi>

q

</mi>

<msub>
<mi>

D

</mi>

<mi>

p

</mi>
</msub>

<mfrac>
<mrow>
<mi>

d

</mi>

<msub>
<mi>

p

</mi>

<mi>

n

</mi>
</msub>
</mrow>

<mrow>
<mi>

d

</mi>

<mi>

x

</mi>
</mrow>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

J_p \approx -qD_p \frac{dp_n}{dx}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9694em;vertical-align:-0.2861em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0962em;">

J

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0962em;margin-right:0.05em;">
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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

≈

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.2772em;vertical-align:-0.345em;">



</span>

<span className="mord">

−

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

q

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

D

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0278em;margin-right:0.05em;">
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
<span className="mord,mathnormal,mtight">

d

</span>

<span className="mord,mathnormal,mtight">

x

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
<span className="mord,mathnormal,mtight">

d

</span>

<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

p

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1645em;">
<span style="top:-2.357em;margin-left:0em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
<span className="mord,mathnormal,mtight">

n

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

---

**概念：**<mark>

**准中性区**

</mark>

**（quasi-neutral region）和其相关**

- 定义：

  - 耗尽层以外的、**近似**保持电中性的P区和N区。（The P and N regions outside the depletion layer, roughly maintaining electrical neutrality.）
- 特征:

  - 电场 <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mi mathvariant="script">
  
  E
  
  </mi>
  
  <mo>
  
  ≈
  
  </mo>
  
  <mn>
  
  0
  
  </mn>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  \mathcal{E} \approx 0
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:0.6833em;">
  
  
  
  </span>
  
  <span className="mord,mathcal" style="margin-right:0.0894em;">
  
  E
  
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
  
  0
  
  </span>
  </span>
  </span>
  </span>
  
  ，电压降可忽略 。
  - 载流子浓度处于**非平衡态**（<span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mi>
  
  p
  
  </mi>
  
  <mi>
  
  n
  
  </mi>
  
  <mo mathvariant="normal">
  
  ≠
  
  </mo>
  
  <msubsup>
  <mi>
  
  n
  
  </mi>
  
  <mi>
  
  i
  
  </mi>
  
  <mn>
  
  2
  
  </mn>
  </msubsup>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  pn \neq n_i^2
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">
  
  
  
  </span>
  
  <span className="mord,mathnormal">
  
  p
  
  </span>
  
  <span className="mord,mathnormal">
  
  n
  
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
  <span className="strut" style="height:1.0728em;vertical-align:-0.2587em;">
  
  
  
  </span>
  
  <span className="mord">
  <span className="mord,mathnormal">
  
  n
  
  </span>
  
  <span className="msupsub">
  <span className="vlist-t,vlist-t2">
  <span className="vlist-r">
  <span className="vlist" style="height:0.8141em;">
  <span style="top:-2.4413em;margin-left:0em;margin-right:0.05em;">
  <span className="pstrut" style="height:2.7em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size6,size3,mtight">
  <span className="mord,mathnormal,mtight">
  
  i
  
  </span>
  </span>
  </span>
  
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
  
  <span className="vlist-s">
  
  ​
  
  </span>
  </span>
  
  <span className="vlist-r">
  <span className="vlist" style="height:0.2587em;">
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
  - 多数载流子浓度 <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mo>
  
  ≈
  
  </mo>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  \approx
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:0.4831em;">
  
  
  
  </span>
  
  <span className="mrel">
  
  ≈
  
  </span>
  </span>
  </span>
  </span>
  
   掺杂浓度 (<span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <msub>
  <mi>
  
  n
  
  </mi>
  
  <mi>
  
  n
  
  </mi>
  </msub>
  
  <mo>
  
  ≈
  
  </mo>
  
  <msub>
  <mi>
  
  N
  
  </mi>
  
  <mi>
  
  D
  
  </mi>
  </msub>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  n_n \approx N_D
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:0.6331em;vertical-align:-0.15em;">
  
  
  
  </span>
  
  <span className="mord">
  <span className="mord,mathnormal">
  
  n
  
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
  
  n
  
  </span>
  </span>
  </span>
  </span>
  
  <span className="vlist-s">
  
  ​
  
  </span>
  </span>
  
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
  
  , <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <msub>
  <mi>
  
  p
  
  </mi>
  
  <mi>
  
  p
  
  </mi>
  </msub>
  
  <mo>
  
  ≈
  
  </mo>
  
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
  
  p_p \approx N_A
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:0.7692em;vertical-align:-0.2861em;">
  
  
  
  </span>
  
  <span className="mord">
  <span className="mord,mathnormal">
  
  p
  
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
  
  ) 。
  - 过剩的多数载流子浓度 <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mo>
  
  ≈
  
  </mo>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  \approx
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:0.4831em;">
  
  
  
  </span>
  
  <span className="mrel">
  
  ≈
  
  </span>
  </span>
  </span>
  </span>
  
   过剩的少数载流子浓度 (<span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mi mathvariant="normal">
  
  Δ
  
  </mi>
  
  <mi>
  
  n
  
  </mi>
  
  <mo>
  
  ≈
  
  </mo>
  
  <mi mathvariant="normal">
  
  Δ
  
  </mi>
  
  <mi>
  
  p
  
  </mi>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  \Delta n \approx \Delta p
  
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
  
  n
  
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
  
  Δ
  
  </span>
  
  <span className="mord,mathnormal">
  
  p
  
  </span>
  </span>
  </span>
  </span>
  
  )。
- 关系：

  - LLI是“准中性区”假设成立的前提。

## 四、结定律（Law of the junction）（P8-14）

**假设：**

LLI 假设中性区（多子浓度很高）的电阻小到可以忽略。因此，我们可以假设**几乎所有的外加电压** <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

V

</mi>

<mi>

A

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

V_A

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

 **都降落在耗尽区**上

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture6-07.webp)

费米能级分裂，产生了准费米能级（不在热平衡状态了）

#### 过剩载流子

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 49.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture6-08.webp" />
      </p>
    </td>
    
    
      <td style="width: 50.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture6-09.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

左边是平衡状态下的（VA=0），右边是正向偏置下的（VA>0）

<mark>

正向偏压使少子浓度增大，对多子浓度影响不大

</mark>



#### 例题一则

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture6-10.webp)

## 五、连续性方程和扩散方程（P15-22)

> 这一节的推导难度较大，可以知道一个大概，然后抄公式

### 连续性方程的推导 (Page 15)

这张幻灯片的目标是建立一个描述“在任意点，载流子浓度如何随时间变化”的方程。在稳态（Steady-State）下，它描述了电流密度如何随空间变化。

#### 核心思想：粒子数守恒

我们考察一个体积微元 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

A

</mi>

<mo>

⋅

</mo>

<mi mathvariant="normal">

Δ

</mi>

<mi>

x

</mi>
</mrow>

<annotation encoding="application/x-tex">

A \cdot \Delta x

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

<span className="mord">

Δ

</span>

<span className="mord,mathnormal">

x

</span>
</span>
</span>
</span>

 。在稳态（Steady-State）下（即浓度不随时间变化），进入这个微元的空穴（Hole）数量必须等于离开的空穴数量，加上在这个微元内“消失”（即复合）的空穴数量。

#### 方程建立

- **流入率**（单位：个/秒）：进入微元的空穴电流为 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

J

</mi>

<mi>

p

</mi>
</msub>

<mo stretchy="false">

(

</mo>

<mi>

x

</mi>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

J_p(x)

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.0361em;vertical-align:-0.2861em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0962em;">

J

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0962em;margin-right:0.05em;">
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

<span className="mopen">

(

</span>

<span className="mord,mathnormal">

x

</span>

<span className="mclose">

)

</span>
</span>
</span>
</span>

，对应的粒子流（“个/秒”）是 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mfrac>
<mrow>
<mi>

A

</mi>

<mo>

⋅

</mo>

<msub>
<mi>

J

</mi>

<mi>

p

</mi>
</msub>

<mo stretchy="false">

(

</mo>

<mi>

x

</mi>

<mo stretchy="false">

)

</mo>
</mrow>

<mi>

q

</mi>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

\frac{A \cdot J_p(x)}{q}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.5134em;vertical-align:-0.4811em;">



</span>

<span className="mord">
<span className="mopen,nulldelimiter">



</span>

<span className="mfrac">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:1.0323em;">
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

<span style="top:-3.5073em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

A

</span>

<span className="mbin,mtight">

⋅

</span>

<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0962em;">

J

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1645em;">
<span style="top:-2.357em;margin-left:-0.0962em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
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
<span className="vlist" style="height:0.2819em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>

<span className="mopen,mtight">

(

</span>

<span className="mord,mathnormal,mtight">

x

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

。
- **流出率**（单位：个/秒）：流出微元的空穴粒子流是 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mfrac>
<mrow>
<mi>

A

</mi>

<mo>

⋅

</mo>

<msub>
<mi>

J

</mi>

<mi>

p

</mi>
</msub>

<mo stretchy="false">

(

</mo>

<mi>

x

</mi>

<mo>

+

</mo>

<mi mathvariant="normal">

Δ

</mi>

<mi>

x

</mi>

<mo stretchy="false">

)

</mo>
</mrow>

<mi>

q

</mi>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

\frac{A \cdot J_p(x+\Delta x)}{q}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.5134em;vertical-align:-0.4811em;">



</span>

<span className="mord">
<span className="mopen,nulldelimiter">



</span>

<span className="mfrac">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:1.0323em;">
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

<span style="top:-3.5073em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

A

</span>

<span className="mbin,mtight">

⋅

</span>

<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0962em;">

J

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1645em;">
<span style="top:-2.357em;margin-left:-0.0962em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
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
<span className="vlist" style="height:0.2819em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>

<span className="mopen,mtight">

(

</span>

<span className="mord,mathnormal,mtight">

x

</span>

<span className="mbin,mtight">

+

</span>

<span className="mord,mtight">

Δ

</span>

<span className="mord,mathnormal,mtight">

x

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

。
- **复合率**（单位：个/秒）：单位体积内的复合率是 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mfrac>
<mrow>
<mi mathvariant="normal">

Δ

</mi>

<mi>

p

</mi>
</mrow>

<msub>
<mi>

τ

</mi>

<mi>

p

</mi>
</msub>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

\frac{\Delta p}{\tau_p}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.4668em;vertical-align:-0.5423em;">



</span>

<span className="mord">
<span className="mopen,nulldelimiter">



</span>

<span className="mfrac">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.9244em;">
<span style="top:-2.655em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.1132em;">

τ

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1645em;">
<span style="top:-2.357em;margin-left:-0.1132em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
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

<span style="top:-3.4461em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">

Δ

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
</span>

（过剩浓度/寿命），因此整个微元的复合率是<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

A

</mi>

<mo>

⋅

</mo>

<mi mathvariant="normal">

Δ

</mi>

<mi>

x

</mi>

<mo>

⋅

</mo>

<mfrac>
<mrow>
<mi mathvariant="normal">

Δ

</mi>

<mi>

p

</mi>
</mrow>

<msub>
<mi>

τ

</mi>

<mi>

p

</mi>
</msub>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

A \cdot \Delta x \cdot \frac{\Delta p}{\tau_p}

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

<span className="mord">

Δ

</span>

<span className="mord,mathnormal">

x

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
<span className="strut" style="height:1.4668em;vertical-align:-0.5423em;">



</span>

<span className="mord">
<span className="mopen,nulldelimiter">



</span>

<span className="mfrac">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.9244em;">
<span style="top:-2.655em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.1132em;">

τ

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1645em;">
<span style="top:-2.357em;margin-left:-0.1132em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
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

<span style="top:-3.4461em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">

Δ

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
</span>

。

根据守恒定律：

流入 = 流出 + 复合

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mfrac>
<mrow>
<mi>

A

</mi>

<mo>

⋅

</mo>

<msub>
<mi>

J

</mi>

<mi>

p

</mi>
</msub>

<mo stretchy="false">

(

</mo>

<mi>

x

</mi>

<mo stretchy="false">

)

</mo>
</mrow>

<mi>

q

</mi>
</mfrac>

<mo>

=

</mo>

<mfrac>
<mrow>
<mi>

A

</mi>

<mo>

⋅

</mo>

<msub>
<mi>

J

</mi>

<mi>

p

</mi>
</msub>

<mo stretchy="false">

(

</mo>

<mi>

x

</mi>

<mo>

+

</mo>

<mi mathvariant="normal">

Δ

</mi>

<mi>

x

</mi>

<mo stretchy="false">

)

</mo>
</mrow>

<mi>

q

</mi>
</mfrac>

<mo>

+

</mo>

<mi>

A

</mi>

<mo>

⋅

</mo>

<mi mathvariant="normal">

Δ

</mi>

<mi>

x

</mi>

<mo>

⋅

</mo>

<mfrac>
<mrow>
<mi mathvariant="normal">

Δ

</mi>

<mi>

p

</mi>
</mrow>

<msub>
<mi>

τ

</mi>

<mi>

p

</mi>
</msub>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

\frac{A \cdot J_p(x)}{q} = \frac{A \cdot J_p(x+\Delta x)}{q} + A \cdot \Delta x \cdot \frac{\Delta p}{\tau_p}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:2.3074em;vertical-align:-0.8804em;">



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
<span className="mord,mathnormal" style="margin-right:0.0359em;">

q

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

A

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

⋅

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0962em;">

J

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0962em;margin-right:0.05em;">
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

<span className="mopen">

(

</span>

<span className="mord,mathnormal">

x

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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:2.3074em;vertical-align:-0.8804em;">



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
<span className="mord,mathnormal" style="margin-right:0.0359em;">

q

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

A

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

⋅

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0962em;">

J

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0962em;margin-right:0.05em;">
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

<span className="mopen">

(

</span>

<span className="mord,mathnormal">

x

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mord">

Δ

</span>

<span className="mord,mathnormal">

x

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

<span className="mord">

Δ

</span>

<span className="mord,mathnormal">

x

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

Δ

</span>

<span className="mord,mathnormal">

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

#### 数学推导

我们将上述方程两边同除以 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

A

</mi>
</mrow>

<annotation encoding="application/x-tex">

A

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
</span>
</span>
</span>

，并移项：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mfrac>
<mrow>
<msub>
<mi>

J

</mi>

<mi>

p

</mi>
</msub>

<mo stretchy="false">

(

</mo>

<mi>

x

</mi>

<mo stretchy="false">

)

</mo>

<mo>

−

</mo>

<msub>
<mi>

J

</mi>

<mi>

p

</mi>
</msub>

<mo stretchy="false">

(

</mo>

<mi>

x

</mi>

<mo>

+

</mo>

<mi mathvariant="normal">

Δ

</mi>

<mi>

x

</mi>

<mo stretchy="false">

)

</mo>
</mrow>

<mi>

q

</mi>
</mfrac>

<mo>

=

</mo>

<mi mathvariant="normal">

Δ

</mi>

<mi>

x

</mi>

<mo>

⋅

</mo>

<mfrac>
<mrow>
<mi mathvariant="normal">

Δ

</mi>

<mi>

p

</mi>
</mrow>

<msub>
<mi>

τ

</mi>

<mi>

p

</mi>
</msub>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

\frac{J_p(x) - J_p(x+\Delta x)}{q} = \Delta x \cdot \frac{\Delta p}{\tau_p}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:2.3074em;vertical-align:-0.8804em;">



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
<span className="mord,mathnormal" style="margin-right:0.0359em;">

q

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
<span className="mord,mathnormal" style="margin-right:0.0962em;">

J

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0962em;margin-right:0.05em;">
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

<span className="mopen">

(

</span>

<span className="mord,mathnormal">

x

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

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0962em;">

J

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0962em;margin-right:0.05em;">
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

<span className="mopen">

(

</span>

<span className="mord,mathnormal">

x

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mord">

Δ

</span>

<span className="mord,mathnormal">

x

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

Δ

</span>

<span className="mord,mathnormal">

x

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

Δ

</span>

<span className="mord,mathnormal">

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

两边同除以 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi mathvariant="normal">

Δ

</mi>

<mi>

x

</mi>
</mrow>

<annotation encoding="application/x-tex">

\Delta x

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

x

</span>
</span>
</span>
</span>

，并乘以 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

q

</mi>
</mrow>

<annotation encoding="application/x-tex">

q

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
</span>
</span>
</span>

：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mfrac>
<mrow>
<msub>
<mi>

J

</mi>

<mi>

p

</mi>
</msub>

<mo stretchy="false">

(

</mo>

<mi>

x

</mi>

<mo stretchy="false">

)

</mo>

<mo>

−

</mo>

<msub>
<mi>

J

</mi>

<mi>

p

</mi>
</msub>

<mo stretchy="false">

(

</mo>

<mi>

x

</mi>

<mo>

+

</mo>

<mi mathvariant="normal">

Δ

</mi>

<mi>

x

</mi>

<mo stretchy="false">

)

</mo>
</mrow>

<mrow>
<mi mathvariant="normal">

Δ

</mi>

<mi>

x

</mi>
</mrow>
</mfrac>

<mo>

=

</mo>

<mi>

q

</mi>

<mfrac>
<mrow>
<mi mathvariant="normal">

Δ

</mi>

<mi>

p

</mi>
</mrow>

<msub>
<mi>

τ

</mi>

<mi>

p

</mi>
</msub>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

\frac{J_p(x) - J_p(x+\Delta x)}{\Delta x} = q \frac{\Delta p}{\tau_p}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:2.113em;vertical-align:-0.686em;">



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

Δ

</span>

<span className="mord,mathnormal">

x

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
<span className="mord,mathnormal" style="margin-right:0.0962em;">

J

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0962em;margin-right:0.05em;">
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

<span className="mopen">

(

</span>

<span className="mord,mathnormal">

x

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

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0962em;">

J

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0962em;margin-right:0.05em;">
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

<span className="mopen">

(

</span>

<span className="mord,mathnormal">

x

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mord">

Δ

</span>

<span className="mord,mathnormal">

x

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
<span className="strut" style="height:2.3324em;vertical-align:-0.9721em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

q

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

Δ

</span>

<span className="mord,mathnormal">

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

提取负号，得到幻灯片中的第二个方程：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mo>

−

</mo>

<mfrac>
<mrow>
<msub>
<mi>

J

</mi>

<mi>

p

</mi>
</msub>

<mo stretchy="false">

(

</mo>

<mi>

x

</mi>

<mo>

+

</mo>

<mi mathvariant="normal">

Δ

</mi>

<mi>

x

</mi>

<mo stretchy="false">

)

</mo>

<mo>

−

</mo>

<msub>
<mi>

J

</mi>

<mi>

p

</mi>
</msub>

<mo stretchy="false">

(

</mo>

<mi>

x

</mi>

<mo stretchy="false">

)

</mo>
</mrow>

<mrow>
<mi mathvariant="normal">

Δ

</mi>

<mi>

x

</mi>
</mrow>
</mfrac>

<mo>

=

</mo>

<mi>

q

</mi>

<mfrac>
<mrow>
<mi mathvariant="normal">

Δ

</mi>

<mi>

p

</mi>
</mrow>

<msub>
<mi>

τ

</mi>

<mi>

p

</mi>
</msub>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

-\frac{J_p(x+\Delta x) - J_p(x)}{\Delta x} = q \frac{\Delta p}{\tau_p}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:2.113em;vertical-align:-0.686em;">



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
<span className="vlist" style="height:1.427em;">
<span style="top:-2.314em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord">

Δ

</span>

<span className="mord,mathnormal">

x

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
<span className="mord,mathnormal" style="margin-right:0.0962em;">

J

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0962em;margin-right:0.05em;">
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

<span className="mopen">

(

</span>

<span className="mord,mathnormal">

x

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mord">

Δ

</span>

<span className="mord,mathnormal">

x

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

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0962em;">

J

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0962em;margin-right:0.05em;">
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

<span className="mopen">

(

</span>

<span className="mord,mathnormal">

x

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
<span className="strut" style="height:2.3324em;vertical-align:-0.9721em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

q

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

Δ

</span>

<span className="mord,mathnormal">

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

当 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi mathvariant="normal">

Δ

</mi>

<mi>

x

</mi>

<mo>

→

</mo>

<mn>

0

</mn>
</mrow>

<annotation encoding="application/x-tex">

\Delta x \to 0

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

x

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

 时，左侧即是导数的定义，我们得到稳态连续性方程：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mo>

−

</mo>

<mfrac>
<mrow>
<mi>

d

</mi>

<msub>
<mi>

J

</mi>

<mi>

p

</mi>
</msub>
</mrow>

<mrow>
<mi>

d

</mi>

<mi>

x

</mi>
</mrow>
</mfrac>

<mo>

=

</mo>

<mi>

q

</mi>

<mfrac>
<mrow>
<mi mathvariant="normal">

Δ

</mi>

<mi>

p

</mi>
</mrow>

<msub>
<mi>

τ

</mi>

<mi>

p

</mi>
</msub>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

-\frac{dJ_p}{dx} = q \frac{\Delta p}{\tau_p}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:2.0574em;vertical-align:-0.686em;">



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
<span className="vlist" style="height:1.3714em;">
<span style="top:-2.314em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal">

x

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

d

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0962em;">

J

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0962em;margin-right:0.05em;">
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
<span className="strut" style="height:2.3324em;vertical-align:-0.9721em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

q

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

Δ

</span>

<span className="mord,mathnormal">

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

#### 物理意义

空穴电流密度随距离的负变化率（<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mo>

−

</mo>

<mfrac>
<mrow>
<mi>

d

</mi>

<msub>
<mi>

J

</mi>

<mi>

p

</mi>
</msub>
</mrow>

<mrow>
<mi>

d

</mi>

<mi>

x

</mi>
</mrow>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

-\frac{dJ_p}{dx}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.3384em;vertical-align:-0.345em;">



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
<span className="vlist" style="height:0.9934em;">
<span style="top:-2.655em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

d

</span>

<span className="mord,mathnormal,mtight">

x

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

<span style="top:-3.5073em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

d

</span>

<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0962em;">

J

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1645em;">
<span style="top:-2.357em;margin-left:-0.0962em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
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

），等于该点的净复合率。也就是说，如果电流向右流动时逐渐减小，那必定是因为载流子在途中复合消失了。

---

### 少数载流子扩散方程 (Page 16)

上一页的连续性方程是普适的。现在我们将其应用于一个特定但非常重要的情况：准中性区中的少数载流子。

#### 关键假设：低水平注入（Low-Level Injection）

在准中性区（QNR），电场 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

E

</mi>
</mrow>

<annotation encoding="application/x-tex">

E

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
</span>
</span>
</span>

 非常小（大部分电压降在耗尽区）。少数载流子（例如N区的空穴）的电流 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

J

</mi>

<mi>

p

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

J_p

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9694em;vertical-align:-0.2861em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0962em;">

J

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0962em;margin-right:0.05em;">
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

 由漂移和扩散两部分组成：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<msub>
<mi>

J

</mi>

<mi>

p

</mi>
</msub>

<mo>

=

</mo>

<mi>

q

</mi>

<msub>
<mi>

μ

</mi>

<mi>

p

</mi>
</msub>

<mi>

p

</mi>

<mi>

E

</mi>

<mo>

−

</mo>

<mi>

q

</mi>

<msub>
<mi>

D

</mi>

<mi>

p

</mi>
</msub>

<mfrac>
<mrow>
<mi>

d

</mi>

<mi>

p

</mi>
</mrow>

<mrow>
<mi>

d

</mi>

<mi>

x

</mi>
</mrow>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

J_p = q\mu_p p E - qD_p \frac{dp}{dx}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9694em;vertical-align:-0.2861em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0962em;">

J

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0962em;margin-right:0.05em;">
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

<span className="mord,mathnormal" style="margin-right:0.0359em;">

q

</span>

<span className="mord">
<span className="mord,mathnormal">

μ

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

<span className="mord,mathnormal" style="margin-right:0.0576em;">

pE

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
<span className="strut" style="height:2.0574em;vertical-align:-0.686em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

q

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

D

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0278em;margin-right:0.05em;">
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
<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal">

x

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

d

</span>

<span className="mord,mathnormal">

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

因为 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

p

</mi>
</mrow>

<annotation encoding="application/x-tex">

p

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.625em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal">

p

</span>
</span>
</span>
</span>

（少子浓度）和 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

E

</mi>
</mrow>

<annotation encoding="application/x-tex">

E

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
</span>
</span>
</span>

 都很小，所以漂移项 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

q

</mi>

<msub>
<mi>

μ

</mi>

<mi>

p

</mi>
</msub>

<mi>

p

</mi>

<mi>

E

</mi>
</mrow>

<annotation encoding="application/x-tex">

q\mu_p p E

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9694em;vertical-align:-0.2861em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

q

</span>

<span className="mord">
<span className="mord,mathnormal">

μ

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

<span className="mord,mathnormal" style="margin-right:0.0576em;">

pE

</span>
</span>
</span>
</span>

 可以忽略不计。

#### 简化电流方程

因此，少数载流子电流几乎完全是扩散电流：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<msub>
<mi>

J

</mi>

<mi>

p

</mi>
</msub>

<mo>

≈

</mo>

<mo>

−

</mo>

<mi>

q

</mi>

<msub>
<mi>

D

</mi>

<mi>

p

</mi>
</msub>

<mfrac>
<mrow>
<mi>

d

</mi>

<mi>

p

</mi>
</mrow>

<mrow>
<mi>

d

</mi>

<mi>

x

</mi>
</mrow>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

J_p \approx -qD_p \frac{dp}{dx}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9694em;vertical-align:-0.2861em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0962em;">

J

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0962em;margin-right:0.05em;">
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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

≈

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:2.0574em;vertical-align:-0.686em;">



</span>

<span className="mord">

−

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

q

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

D

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0278em;margin-right:0.05em;">
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
<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal">

x

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

d

</span>

<span className="mord,mathnormal">

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

又因为 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

p

</mi>

<mo stretchy="false">

(

</mo>

<mi>

x

</mi>

<mo stretchy="false">

)

</mo>

<mo>

=

</mo>

<msub>
<mi>

p

</mi>

<mrow>
<mi>

n

</mi>

<mn>

0

</mn>
</mrow>
</msub>

<mo>

+

</mo>

<mi mathvariant="normal">

Δ

</mi>

<mi>

p

</mi>

<mo stretchy="false">

(

</mo>

<mi>

x

</mi>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

p(x) = p_{n0} + \Delta p(x)

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord,mathnormal">

p

</span>

<span className="mopen">

(

</span>

<span className="mord,mathnormal">

x

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
<span className="strut" style="height:0.7778em;vertical-align:-0.1944em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

p

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
<span className="mord,mathnormal,mtight">

n

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

Δ

</span>

<span className="mord,mathnormal">

p

</span>

<span className="mopen">

(

</span>

<span className="mord,mathnormal">

x

</span>

<span className="mclose">

)

</span>
</span>
</span>
</span>

，而平衡浓度 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

p

</mi>

<mrow>
<mi>

n

</mi>

<mn>

0

</mn>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

p_{n0}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.625em;vertical-align:-0.1944em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

p

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
<span className="mord,mathnormal,mtight">

n

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

 是一个常数，所以 <span className="katex">
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

p

</mi>
</mrow>

<mrow>
<mi>

d

</mi>

<mi>

x

</mi>
</mrow>
</mfrac>

<mo>

=

</mo>

<mfrac>
<mrow>
<mi>

d

</mi>

<mi mathvariant="normal">

Δ

</mi>

<mi>

p

</mi>
</mrow>

<mrow>
<mi>

d

</mi>

<mi>

x

</mi>
</mrow>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

\frac{dp}{dx} = \frac{d\Delta p}{dx}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
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
<span className="mord,mathnormal,mtight">

d

</span>

<span className="mord,mathnormal,mtight">

x

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
<span className="mord,mathnormal,mtight">

d

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
<span className="mord,mathnormal,mtight">

d

</span>

<span className="mord,mathnormal,mtight">

x

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
<span className="mord,mathnormal,mtight">

d

</span>

<span className="mord,mtight">

Δ

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

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<msub>
<mi>

J

</mi>

<mi>

p

</mi>
</msub>

<mo>

=

</mo>

<mo>

−

</mo>

<mi>

q

</mi>

<msub>
<mi>

D

</mi>

<mi>

p

</mi>
</msub>

<mfrac>
<mrow>
<mi>

d

</mi>

<mi mathvariant="normal">

Δ

</mi>

<mi>

p

</mi>
</mrow>

<mrow>
<mi>

d

</mi>

<mi>

x

</mi>
</mrow>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

J_p = -qD_p \frac{d\Delta p}{dx}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9694em;vertical-align:-0.2861em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0962em;">

J

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0962em;margin-right:0.05em;">
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

−

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

q

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

D

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0278em;margin-right:0.05em;">
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
<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal">

x

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

d

</span>

<span className="mord">

Δ

</span>

<span className="mord,mathnormal">

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

#### 推导扩散方程

将这个简化的 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

J

</mi>

<mi>

p

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

J_p

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9694em;vertical-align:-0.2861em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0962em;">

J

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0962em;margin-right:0.05em;">
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

 代入连续性方程 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mo>

−

</mo>

<mfrac>
<mrow>
<mi>

d

</mi>

<msub>
<mi>

J

</mi>

<mi>

p

</mi>
</msub>
</mrow>

<mrow>
<mi>

d

</mi>

<mi>

x

</mi>
</mrow>
</mfrac>

<mo>

=

</mo>

<mi>

q

</mi>

<mfrac>
<mrow>
<mi mathvariant="normal">

Δ

</mi>

<mi>

p

</mi>
</mrow>

<msub>
<mi>

τ

</mi>

<mi>

p

</mi>
</msub>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

-\frac{dJ_p}{dx} = q \frac{\Delta p}{\tau_p}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.3384em;vertical-align:-0.345em;">



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
<span className="vlist" style="height:0.9934em;">
<span style="top:-2.655em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

d

</span>

<span className="mord,mathnormal,mtight">

x

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

<span style="top:-3.5073em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

d

</span>

<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0962em;">

J

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1645em;">
<span style="top:-2.357em;margin-left:-0.0962em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.4668em;vertical-align:-0.5423em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

q

</span>

<span className="mord">
<span className="mopen,nulldelimiter">



</span>

<span className="mfrac">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.9244em;">
<span style="top:-2.655em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.1132em;">

τ

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1645em;">
<span style="top:-2.357em;margin-left:-0.1132em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
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

<span style="top:-3.4461em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">

Δ

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
</span>

 ：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mo>

−

</mo>

<mfrac>
<mi>

d

</mi>

<mrow>
<mi>

d

</mi>

<mi>

x

</mi>
</mrow>
</mfrac>

<mrow>
<mo fence="true">

(

</mo>

<mo>

−

</mo>

<mi>

q

</mi>

<msub>
<mi>

D

</mi>

<mi>

p

</mi>
</msub>

<mfrac>
<mrow>
<mi>

d

</mi>

<mi mathvariant="normal">

Δ

</mi>

<mi>

p

</mi>
</mrow>

<mrow>
<mi>

d

</mi>

<mi>

x

</mi>
</mrow>
</mfrac>

<mo fence="true">

)

</mo>
</mrow>

<mo>

=

</mo>

<mi>

q

</mi>

<mfrac>
<mrow>
<mi mathvariant="normal">

Δ

</mi>

<mi>

p

</mi>
</mrow>

<msub>
<mi>

τ

</mi>

<mi>

p

</mi>
</msub>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

-\frac{d}{dx}\left(-qD_p \frac{d\Delta p}{dx}\right) = q \frac{\Delta p}{\tau_p}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:2.4em;vertical-align:-0.95em;">



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
<span className="vlist" style="height:1.3714em;">
<span style="top:-2.314em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal">

x

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
<span className="delimsizing,size3">

(

</span>
</span>

<span className="mord">

−

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

q

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

D

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0278em;margin-right:0.05em;">
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
<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal">

x

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

d

</span>

<span className="mord">

Δ

</span>

<span className="mord,mathnormal">

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

<span className="mord,mathnormal" style="margin-right:0.0359em;">

q

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

Δ

</span>

<span className="mord,mathnormal">

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

化简得到：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mfrac>
<mrow>
<msup>
<mi>

d

</mi>

<mn>

2

</mn>
</msup>

<mi mathvariant="normal">

Δ

</mi>

<mi>

p

</mi>
</mrow>

<mrow>
<mi>

d

</mi>

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

<mo>

=

</mo>

<mfrac>
<mrow>
<mi mathvariant="normal">

Δ

</mi>

<mi>

p

</mi>
</mrow>

<mrow>
<msub>
<mi>

D

</mi>

<mi>

p

</mi>
</msub>

<msub>
<mi>

τ

</mi>

<mi>

p

</mi>
</msub>
</mrow>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

\frac{d^2\Delta p}{dx^2} = \frac{\Delta p}{D_p \tau_p}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
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
<span className="mord,mathnormal">

d

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
<span className="mord,mathnormal">

d

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

<span className="mord">

Δ

</span>

<span className="mord,mathnormal">

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
<span className="mord,mathnormal" style="margin-right:0.0278em;">

D

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0278em;margin-right:0.05em;">
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

Δ

</span>

<span className="mord,mathnormal">

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

#### 定义扩散长度 (Diffusion Length)

<mark>

我们定义一个具有长度量纲的常数

</mark>

 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

L

</mi>

<mi>

p

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

L_p

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

<mark>

，称为空穴扩散长度 (Diffusion Length)：

</mark>



<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<msub>
<mi>

L

</mi>

<mi>

p

</mi>
</msub>

<mo>

≡

</mo>

<msqrt>
<mrow>
<msub>
<mi>

D

</mi>

<mi>

p

</mi>
</msub>

<msub>
<mi>

τ

</mi>

<mi>

p

</mi>
</msub>
</mrow>
</msqrt>
</mrow>

<annotation encoding="application/x-tex">

L_p \equiv \sqrt{D_p \tau_p}

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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

≡

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.24em;vertical-align:-0.3075em;">



</span>

<span className="mord,sqrt">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.9325em;">
<span className="svg-align" style="top:-3.2em;">
<span className="pstrut" style="height:3.2em;">



</span>

<span className="mord" style="padding-left:1em;">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

D

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0278em;margin-right:0.05em;">
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

> <mark>
> 
> **物理意义：**
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
> L
> 
> </mi>
> 
> <mi>
> 
> p
> 
> </mi>
> </msub>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> L_p
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
> <span className="mord,mathnormal">
> 
> L
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
> <span className="mord,mathnormal,mtight">
> 
> p
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
> 是少数载流子（空穴）在复合前平均可以扩散的距离。
> 
> </mark>

#### 最终方程

将 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

L

</mi>

<mi>

p

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

L_p

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

 代入，我们就得到了用于描述稳态、低注入、无光照下少数载流子分布的核心方程：

- N区的空穴：
- <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mfrac>
<mrow>
<msup>
<mi>

d

</mi>

<mn>

2

</mn>
</msup>

<mi mathvariant="normal">

Δ

</mi>

<mi>

p

</mi>
</mrow>

<mrow>
<mi>

d

</mi>

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

<mo>

=

</mo>

<mfrac>
<mrow>
<mi mathvariant="normal">

Δ

</mi>

<mi>

p

</mi>
</mrow>

<msubsup>
<mi>

L

</mi>

<mi>

p

</mi>

<mn>

2

</mn>
</msubsup>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

\frac{d^2\Delta p}{dx^2} = \frac{\Delta p}{L_p^2}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.415em;vertical-align:-0.345em;">



</span>

<span className="mord">
<span className="mopen,nulldelimiter">



</span>

<span className="mfrac">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:1.07em;">
<span style="top:-2.655em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

d

</span>

<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

x

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
<span className="mord,mathnormal,mtight">

d

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

2

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

<span className="mord,mtight">

Δ

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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.5669em;vertical-align:-0.6424em;">



</span>

<span className="mord">
<span className="mopen,nulldelimiter">



</span>

<span className="mfrac">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.9244em;">
<span style="top:-2.655em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

L

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.7463em;">
<span style="top:-2.214em;margin-left:0em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
<span className="mord,mathnormal,mtight">

p

</span>
</span>
</span>

<span style="top:-2.786em;margin-right:0.0714em;">
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
<span className="vlist" style="height:0.4249em;">
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

<span style="top:-3.4461em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">

Δ

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
<span className="vlist" style="height:0.6424em;">
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
- P区的电子：
- <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mfrac>
<mrow>
<msup>
<mi>

d

</mi>

<mn>

2

</mn>
</msup>

<mi mathvariant="normal">

Δ

</mi>

<mi>

n

</mi>
</mrow>

<mrow>
<mi>

d

</mi>

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

<mo>

=

</mo>

<mfrac>
<mrow>
<mi mathvariant="normal">

Δ

</mi>

<mi>

n

</mi>
</mrow>

<msubsup>
<mi>

L

</mi>

<mi>

n

</mi>

<mn>

2

</mn>
</msubsup>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

\frac{d^2\Delta n}{dx^2} = \frac{\Delta n}{L_n^2}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.3629em;vertical-align:-0.345em;">



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
<span className="mord,mathnormal,mtight">

d

</span>

<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

x

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
<span className="mord,mathnormal,mtight">

d

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

2

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

<span className="mord,mtight">

Δ

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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.4175em;vertical-align:-0.5452em;">



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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

L

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.7463em;">
<span style="top:-2.214em;margin-left:0em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
<span className="mord,mathnormal,mtight">

n

</span>
</span>
</span>

<span style="top:-2.786em;margin-right:0.0714em;">
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
<span className="vlist" style="height:0.286em;">
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

<span style="top:-3.394em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">

Δ

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
<span className="vlist" style="height:0.5452em;">
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

---

### 求解扩散方程 (Page 17)

现在我们有了方程，需要求解它来找到 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi mathvariant="normal">

Δ

</mi>

<mi>

p

</mi>

<mo stretchy="false">

(

</mo>

<mi>

x

</mi>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

\Delta p(x)

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord">

Δ

</span>

<span className="mord,mathnormal">

p

</span>

<span className="mopen">

(

</span>

<span className="mord,mathnormal">

x

</span>

<span className="mclose">

)

</span>
</span>
</span>
</span>

 的具体函数形式。这张幻灯片以N区（<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

x

</mi>

<mo>

>
</mo>

<msub>
<mi>

x

</mi>

<mi>

N

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

x > x_N

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.5782em;vertical-align:-0.0391em;">



</span>

<span className="mord,mathnormal">

x

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

>
</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.5806em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

x

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.109em;">

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

）为例进行求解。

#### 待解问题

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mfrac>
<mrow>
<msup>
<mi>

d

</mi>

<mn>

2

</mn>
</msup>

<mi mathvariant="normal">

Δ

</mi>

<mi>

p

</mi>
</mrow>

<mrow>
<mi>

d

</mi>

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

<mo>

=

</mo>

<mfrac>
<mrow>
<mi mathvariant="normal">

Δ

</mi>

<mi>

p

</mi>
</mrow>

<msubsup>
<mi>

L

</mi>

<mi>

p

</mi>

<mn>

2

</mn>
</msubsup>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

\frac{d^2\Delta p}{dx^2} = \frac{\Delta p}{L_p^2}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
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
<span className="mord,mathnormal">

d

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
<span className="mord,mathnormal">

d

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

<span className="mord">

Δ

</span>

<span className="mord,mathnormal">

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
<span className="strut" style="height:2.4294em;vertical-align:-1.0691em;">



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

L

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.7401em;">
<span style="top:-2.453em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

p

</span>
</span>
</span>

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

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.3831em;">
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

Δ

</span>

<span className="mord,mathnormal">

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
<span className="vlist" style="height:1.0691em;">
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

#### 通解

这是一个二阶常系数线性齐次微分方程，其通解为：

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

p

</mi>

<mo stretchy="false">

(

</mo>

<mi>

x

</mi>

<mo stretchy="false">

)

</mo>

<mo>

=

</mo>

<mi>

A

</mi>

<msup>
<mi>

e

</mi>

<mrow>
<mi>

x

</mi>

<mi mathvariant="normal">

/

</mi>

<msub>
<mi>

L

</mi>

<mi>

p

</mi>
</msub>
</mrow>
</msup>

<mo>

+

</mo>

<mi>

B

</mi>

<msup>
<mi>

e

</mi>

<mrow>
<mo>

−

</mo>

<mi>

x

</mi>

<mi mathvariant="normal">

/

</mi>

<msub>
<mi>

L

</mi>

<mi>

p

</mi>
</msub>
</mrow>
</msup>
</mrow>

<annotation encoding="application/x-tex">

\Delta p(x) = A e^{x/L_p} + B e^{-x/L_p}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord">

Δ

</span>

<span className="mord,mathnormal">

p

</span>

<span className="mopen">

(

</span>

<span className="mord,mathnormal">

x

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
<span className="strut" style="height:1.0213em;vertical-align:-0.0833em;">



</span>

<span className="mord,mathnormal">

A

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
<span className="mord,mathnormal,mtight">

x

</span>

<span className="mord,mtight">

/

</span>

<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

L

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1645em;">
<span style="top:-2.357em;margin-left:0em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
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
<span className="strut" style="height:0.938em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0502em;">

B

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

x

</span>

<span className="mord,mtight">

/

</span>

<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

L

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1645em;">
<span style="top:-2.357em;margin-left:0em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
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
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

#### 边界条件 (Boundary Conditions)

为了确定常数 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

A

</mi>
</mrow>

<annotation encoding="application/x-tex">

A

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
</span>
</span>
</span>

 和 B，我们需要两个边界条件：

1. 远场 (<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

x

</mi>

<mo>

→

</mo>

<mi mathvariant="normal">

∞

</mi>
</mrow>

<annotation encoding="application/x-tex">

x \to \infty

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.4306em;">



</span>

<span className="mord,mathnormal">

x

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

)：

  - 我们假设这是一个“长二极管”，即准中性区的宽度远大于 <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <msub>
  <mi>
  
  L
  
  </mi>
  
  <mi>
  
  p
  
  </mi>
  </msub>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  L_p
  
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
  
  。在远离结的地方，所有注入的过剩载流子都复合完了，浓度恢复到平衡值。
  - <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mi mathvariant="normal">
  
  Δ
  
  </mi>
  
  <mi>
  
  p
  
  </mi>
  
  <mo stretchy="false">
  
  (
  
  </mo>
  
  <mi mathvariant="normal">
  
  ∞
  
  </mi>
  
  <mo stretchy="false">
  
  )
  
  </mo>
  
  <mo>
  
  =
  
  </mo>
  
  <mn>
  
  0
  
  </mn>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  \Delta p(\infty) = 0
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:1em;vertical-align:-0.25em;">
  
  
  
  </span>
  
  <span className="mord">
  
  Δ
  
  </span>
  
  <span className="mord,mathnormal">
  
  p
  
  </span>
  
  <span className="mopen">
  
  (
  
  </span>
  
  <span className="mord">
  
  ∞
  
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
  
  0
  
  </span>
  </span>
  </span>
  </span>
2. 结的边界 (<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

x

</mi>

<mo>

=

</mo>

<msub>
<mi>

x

</mi>

<mi>

N

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

x = x_N

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.4306em;">



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
<span className="strut" style="height:0.5806em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

x

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.109em;">

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

)：

  - 在耗尽区的N侧边界，过剩空穴浓度由结定律 (Law of the Junction) 决定（这是前一节课的核心内容）：
  - <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mi mathvariant="normal">
  
  Δ
  
  </mi>
  
  <mi>
  
  p
  
  </mi>
  
  <mo stretchy="false">
  
  (
  
  </mo>
  
  <msub>
  <mi>
  
  x
  
  </mi>
  
  <mi>
  
  N
  
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
  
  p
  
  </mi>
  
  <mrow>
  <mi>
  
  n
  
  </mi>
  
  <mn>
  
  0
  
  </mn>
  </mrow>
  </msub>
  
  <mo stretchy="false">
  
  (
  
  </mo>
  
  <msup>
  <mi>
  
  e
  
  </mi>
  
  <mrow>
  <mi>
  
  q
  
  </mi>
  
  <mi>
  
  V
  
  </mi>
  
  <mi mathvariant="normal">
  
  /
  
  </mi>
  
  <mi>
  
  k
  
  </mi>
  
  <mi>
  
  T
  
  </mi>
  </mrow>
  </msup>
  
  <mo>
  
  −
  
  </mo>
  
  <mn>
  
  1
  
  </mn>
  
  <mo stretchy="false">
  
  )
  
  </mo>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  \Delta p(x_N) = p_{n0}(e^{qV/kT} - 1)
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:1em;vertical-align:-0.25em;">
  
  
  
  </span>
  
  <span className="mord">
  
  Δ
  
  </span>
  
  <span className="mord,mathnormal">
  
  p
  
  </span>
  
  <span className="mopen">
  
  (
  
  </span>
  
  <span className="mord">
  <span className="mord,mathnormal">
  
  x
  
  </span>
  
  <span className="msupsub">
  <span className="vlist-t,vlist-t2">
  <span className="vlist-r">
  <span className="vlist" style="height:0.3283em;">
  <span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
  <span className="pstrut" style="height:2.7em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size6,size3,mtight">
  <span className="mord,mathnormal,mtight" style="margin-right:0.109em;">
  
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
  <span className="strut" style="height:1.138em;vertical-align:-0.25em;">
  
  
  
  </span>
  
  <span className="mord">
  <span className="mord,mathnormal">
  
  p
  
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
  <span className="mord,mathnormal,mtight">
  
  n
  
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
  
  <span className="mopen">
  
  (
  
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
  <span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">
  
  q
  
  </span>
  
  <span className="mord,mathnormal,mtight" style="margin-right:0.2222em;">
  
  V
  
  </span>
  
  <span className="mord,mtight">
  
  /
  
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
  
  1
  
  </span>
  
  <span className="mclose">
  
  )
  
  </span>
  </span>
  </span>
  </span>

#### 求解

- 应用边界条件1：

  - 当 <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mi>
  
  x
  
  </mi>
  
  <mo>
  
  →
  
  </mo>
  
  <mi mathvariant="normal">
  
  ∞
  
  </mi>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  x \to \infty
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:0.4306em;">
  
  
  
  </span>
  
  <span className="mord,mathnormal">
  
  x
  
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
  
   时，<span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <msup>
  <mi>
  
  e
  
  </mi>
  
  <mrow>
  <mi>
  
  x
  
  </mi>
  
  <mi mathvariant="normal">
  
  /
  
  </mi>
  
  <msub>
  <mi>
  
  L
  
  </mi>
  
  <mi>
  
  p
  
  </mi>
  </msub>
  </mrow>
  </msup>
  
  <mo>
  
  →
  
  </mo>
  
  <mi mathvariant="normal">
  
  ∞
  
  </mi>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  e^{x/L_p} \to \infty
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
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
  <span className="mord,mathnormal,mtight">
  
  x
  
  </span>
  
  <span className="mord,mtight">
  
  /
  
  </span>
  
  <span className="mord,mtight">
  <span className="mord,mathnormal,mtight">
  
  L
  
  </span>
  
  <span className="msupsub">
  <span className="vlist-t,vlist-t2">
  <span className="vlist-r">
  <span className="vlist" style="height:0.1645em;">
  <span style="top:-2.357em;margin-left:0em;margin-right:0.0714em;">
  <span className="pstrut" style="height:2.5em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size3,size1,mtight">
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
  
  。为了使 <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mi mathvariant="normal">
  
  Δ
  
  </mi>
  
  <mi>
  
  p
  
  </mi>
  
  <mo stretchy="false">
  
  (
  
  </mo>
  
  <mi mathvariant="normal">
  
  ∞
  
  </mi>
  
  <mo stretchy="false">
  
  )
  
  </mo>
  
  <mo>
  
  =
  
  </mo>
  
  <mn>
  
  0
  
  </mn>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  \Delta p(\infty) = 0
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:1em;vertical-align:-0.25em;">
  
  
  
  </span>
  
  <span className="mord">
  
  Δ
  
  </span>
  
  <span className="mord,mathnormal">
  
  p
  
  </span>
  
  <span className="mopen">
  
  (
  
  </span>
  
  <span className="mord">
  
  ∞
  
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
  
  0
  
  </span>
  </span>
  </span>
  </span>
  
  ，系数 <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mi>
  
  A
  
  </mi>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  A
  
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
  </span>
  </span>
  </span>
  
   必须等于 <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mn mathvariant="bold">
  
  0
  
  </mn>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  \mathbf{0}
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:0.6444em;">
  
  
  
  </span>
  
  <span className="mord,mathbf">
  
  0
  
  </span>
  </span>
  </span>
  </span>
  
  。
  - 方程简化为：<span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mi mathvariant="normal">
  
  Δ
  
  </mi>
  
  <mi>
  
  p
  
  </mi>
  
  <mo stretchy="false">
  
  (
  
  </mo>
  
  <mi>
  
  x
  
  </mi>
  
  <mo stretchy="false">
  
  )
  
  </mo>
  
  <mo>
  
  =
  
  </mo>
  
  <mi>
  
  B
  
  </mi>
  
  <msup>
  <mi>
  
  e
  
  </mi>
  
  <mrow>
  <mo>
  
  −
  
  </mo>
  
  <mi>
  
  x
  
  </mi>
  
  <mi mathvariant="normal">
  
  /
  
  </mi>
  
  <msub>
  <mi>
  
  L
  
  </mi>
  
  <mi>
  
  p
  
  </mi>
  </msub>
  </mrow>
  </msup>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  \Delta p(x) = B e^{-x/L_p}
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:1em;vertical-align:-0.25em;">
  
  
  
  </span>
  
  <span className="mord">
  
  Δ
  
  </span>
  
  <span className="mord,mathnormal">
  
  p
  
  </span>
  
  <span className="mopen">
  
  (
  
  </span>
  
  <span className="mord,mathnormal">
  
  x
  
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
  <span className="strut" style="height:0.888em;">
  
  
  
  </span>
  
  <span className="mord,mathnormal" style="margin-right:0.0502em;">
  
  B
  
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
  
  x
  
  </span>
  
  <span className="mord,mtight">
  
  /
  
  </span>
  
  <span className="mord,mtight">
  <span className="mord,mathnormal,mtight">
  
  L
  
  </span>
  
  <span className="msupsub">
  <span className="vlist-t,vlist-t2">
  <span className="vlist-r">
  <span className="vlist" style="height:0.1645em;">
  <span style="top:-2.357em;margin-left:0em;margin-right:0.0714em;">
  <span className="pstrut" style="height:2.5em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size3,size1,mtight">
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
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
- 应用边界条件2：

  - <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mi mathvariant="normal">
  
  Δ
  
  </mi>
  
  <mi>
  
  p
  
  </mi>
  
  <mo stretchy="false">
  
  (
  
  </mo>
  
  <msub>
  <mi>
  
  x
  
  </mi>
  
  <mi>
  
  N
  
  </mi>
  </msub>
  
  <mo stretchy="false">
  
  )
  
  </mo>
  
  <mo>
  
  =
  
  </mo>
  
  <mi>
  
  B
  
  </mi>
  
  <msup>
  <mi>
  
  e
  
  </mi>
  
  <mrow>
  <mo>
  
  −
  
  </mo>
  
  <msub>
  <mi>
  
  x
  
  </mi>
  
  <mi>
  
  N
  
  </mi>
  </msub>
  
  <mi mathvariant="normal">
  
  /
  
  </mi>
  
  <msub>
  <mi>
  
  L
  
  </mi>
  
  <mi>
  
  p
  
  </mi>
  </msub>
  </mrow>
  </msup>
  
  <mo>
  
  =
  
  </mo>
  
  <msub>
  <mi>
  
  p
  
  </mi>
  
  <mrow>
  <mi>
  
  n
  
  </mi>
  
  <mn>
  
  0
  
  </mn>
  </mrow>
  </msub>
  
  <mo stretchy="false">
  
  (
  
  </mo>
  
  <msup>
  <mi>
  
  e
  
  </mi>
  
  <mrow>
  <mi>
  
  q
  
  </mi>
  
  <mi>
  
  V
  
  </mi>
  
  <mi mathvariant="normal">
  
  /
  
  </mi>
  
  <mi>
  
  k
  
  </mi>
  
  <mi>
  
  T
  
  </mi>
  </mrow>
  </msup>
  
  <mo>
  
  −
  
  </mo>
  
  <mn>
  
  1
  
  </mn>
  
  <mo stretchy="false">
  
  )
  
  </mo>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  \Delta p(x_N) = B e^{-x_N / L_p} = p_{n0}(e^{qV/kT} - 1)
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:1em;vertical-align:-0.25em;">
  
  
  
  </span>
  
  <span className="mord">
  
  Δ
  
  </span>
  
  <span className="mord,mathnormal">
  
  p
  
  </span>
  
  <span className="mopen">
  
  (
  
  </span>
  
  <span className="mord">
  <span className="mord,mathnormal">
  
  x
  
  </span>
  
  <span className="msupsub">
  <span className="vlist-t,vlist-t2">
  <span className="vlist-r">
  <span className="vlist" style="height:0.3283em;">
  <span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
  <span className="pstrut" style="height:2.7em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size6,size3,mtight">
  <span className="mord,mathnormal,mtight" style="margin-right:0.109em;">
  
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
  <span className="strut" style="height:0.888em;">
  
  
  
  </span>
  
  <span className="mord,mathnormal" style="margin-right:0.0502em;">
  
  B
  
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
  
  <span className="mord,mtight">
  <span className="mord,mathnormal,mtight">
  
  x
  
  </span>
  
  <span className="msupsub">
  <span className="vlist-t,vlist-t2">
  <span className="vlist-r">
  <span className="vlist" style="height:0.3448em;">
  <span style="top:-2.3567em;margin-left:0em;margin-right:0.0714em;">
  <span className="pstrut" style="height:2.5em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size3,size1,mtight">
  <span className="mord,mathnormal,mtight" style="margin-right:0.109em;">
  
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
  <span className="vlist" style="height:0.1433em;">
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
  
  <span className="mord,mtight">
  <span className="mord,mathnormal,mtight">
  
  L
  
  </span>
  
  <span className="msupsub">
  <span className="vlist-t,vlist-t2">
  <span className="vlist-r">
  <span className="vlist" style="height:0.1645em;">
  <span style="top:-2.357em;margin-left:0em;margin-right:0.0714em;">
  <span className="pstrut" style="height:2.5em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size3,size1,mtight">
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
  <span className="strut" style="height:1.138em;vertical-align:-0.25em;">
  
  
  
  </span>
  
  <span className="mord">
  <span className="mord,mathnormal">
  
  p
  
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
  <span className="mord,mathnormal,mtight">
  
  n
  
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
  
  <span className="mopen">
  
  (
  
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
  <span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">
  
  q
  
  </span>
  
  <span className="mord,mathnormal,mtight" style="margin-right:0.2222em;">
  
  V
  
  </span>
  
  <span className="mord,mtight">
  
  /
  
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
  
  1
  
  </span>
  
  <span className="mclose">
  
  )
  
  </span>
  </span>
  </span>
  </span>
  - 解得 B：<span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mi>
  
  B
  
  </mi>
  
  <mo>
  
  =
  
  </mo>
  
  <msub>
  <mi>
  
  p
  
  </mi>
  
  <mrow>
  <mi>
  
  n
  
  </mi>
  
  <mn>
  
  0
  
  </mn>
  </mrow>
  </msub>
  
  <mo stretchy="false">
  
  (
  
  </mo>
  
  <msup>
  <mi>
  
  e
  
  </mi>
  
  <mrow>
  <mi>
  
  q
  
  </mi>
  
  <mi>
  
  V
  
  </mi>
  
  <mi mathvariant="normal">
  
  /
  
  </mi>
  
  <mi>
  
  k
  
  </mi>
  
  <mi>
  
  T
  
  </mi>
  </mrow>
  </msup>
  
  <mo>
  
  −
  
  </mo>
  
  <mn>
  
  1
  
  </mn>
  
  <mo stretchy="false">
  
  )
  
  </mo>
  
  <msup>
  <mi>
  
  e
  
  </mi>
  
  <mrow>
  <msub>
  <mi>
  
  x
  
  </mi>
  
  <mi>
  
  N
  
  </mi>
  </msub>
  
  <mi mathvariant="normal">
  
  /
  
  </mi>
  
  <msub>
  <mi>
  
  L
  
  </mi>
  
  <mi>
  
  p
  
  </mi>
  </msub>
  </mrow>
  </msup>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  B = p_{n0}(e^{qV/kT} - 1) e^{x_N / L_p}
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:0.6833em;">
  
  
  
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
  <span className="strut" style="height:1.138em;vertical-align:-0.25em;">
  
  
  
  </span>
  
  <span className="mord">
  <span className="mord,mathnormal">
  
  p
  
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
  <span className="mord,mathnormal,mtight">
  
  n
  
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
  
  <span className="mopen">
  
  (
  
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
  <span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">
  
  q
  
  </span>
  
  <span className="mord,mathnormal,mtight" style="margin-right:0.2222em;">
  
  V
  
  </span>
  
  <span className="mord,mtight">
  
  /
  
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
  <span className="strut" style="height:1.138em;vertical-align:-0.25em;">
  
  
  
  </span>
  
  <span className="mord">
  
  1
  
  </span>
  
  <span className="mclose">
  
  )
  
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
  <span className="mord,mathnormal,mtight">
  
  x
  
  </span>
  
  <span className="msupsub">
  <span className="vlist-t,vlist-t2">
  <span className="vlist-r">
  <span className="vlist" style="height:0.3448em;">
  <span style="top:-2.3567em;margin-left:0em;margin-right:0.0714em;">
  <span className="pstrut" style="height:2.5em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size3,size1,mtight">
  <span className="mord,mathnormal,mtight" style="margin-right:0.109em;">
  
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
  <span className="vlist" style="height:0.1433em;">
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
  
  <span className="mord,mtight">
  <span className="mord,mathnormal,mtight">
  
  L
  
  </span>
  
  <span className="msupsub">
  <span className="vlist-t,vlist-t2">
  <span className="vlist-r">
  <span className="vlist" style="height:0.1645em;">
  <span style="top:-2.357em;margin-left:0em;margin-right:0.0714em;">
  <span className="pstrut" style="height:2.5em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size3,size1,mtight">
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
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
- 将 B 代回，得到最终解：

  - <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mi mathvariant="normal">
  
  Δ
  
  </mi>
  
  <mi>
  
  p
  
  </mi>
  
  <mo stretchy="false">
  
  (
  
  </mo>
  
  <mi>
  
  x
  
  </mi>
  
  <mo stretchy="false">
  
  )
  
  </mo>
  
  <mo>
  
  =
  
  </mo>
  
  <msub>
  <mi>
  
  p
  
  </mi>
  
  <mrow>
  <mi>
  
  n
  
  </mi>
  
  <mn>
  
  0
  
  </mn>
  </mrow>
  </msub>
  
  <mo stretchy="false">
  
  (
  
  </mo>
  
  <msup>
  <mi>
  
  e
  
  </mi>
  
  <mrow>
  <mi>
  
  q
  
  </mi>
  
  <mi>
  
  V
  
  </mi>
  
  <mi mathvariant="normal">
  
  /
  
  </mi>
  
  <mi>
  
  k
  
  </mi>
  
  <mi>
  
  T
  
  </mi>
  </mrow>
  </msup>
  
  <mo>
  
  −
  
  </mo>
  
  <mn>
  
  1
  
  </mn>
  
  <mo stretchy="false">
  
  )
  
  </mo>
  
  <msup>
  <mi>
  
  e
  
  </mi>
  
  <mrow>
  <mo>
  
  −
  
  </mo>
  
  <mo stretchy="false">
  
  (
  
  </mo>
  
  <mi>
  
  x
  
  </mi>
  
  <mo>
  
  −
  
  </mo>
  
  <msub>
  <mi>
  
  x
  
  </mi>
  
  <mi>
  
  N
  
  </mi>
  </msub>
  
  <mo stretchy="false">
  
  )
  
  </mo>
  
  <mi mathvariant="normal">
  
  /
  
  </mi>
  
  <msub>
  <mi>
  
  L
  
  </mi>
  
  <mi>
  
  p
  
  </mi>
  </msub>
  </mrow>
  </msup>
  
  <mspace width="1em">
  
  
  
  </mspace>
  
  <mo separator="true">
  
  ,
  
  </mo>
  
  <mtext>
  
  for
  
  </mtext>
  
  <mi>
  
  x
  
  </mi>
  
  <mo>
  
  >
  </mo>
  
  <msub>
  <mi>
  
  x
  
  </mi>
  
  <mi>
  
  N
  
  </mi>
  </msub>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  \Delta p(x) = p_{n0}(e^{qV/kT} - 1) e^{-(x - x_N) / L_p} \quad , \text{for } x > x_N
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:1em;vertical-align:-0.25em;">
  
  
  
  </span>
  
  <span className="mord">
  
  Δ
  
  </span>
  
  <span className="mord,mathnormal">
  
  p
  
  </span>
  
  <span className="mopen">
  
  (
  
  </span>
  
  <span className="mord,mathnormal">
  
  x
  
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
  <span className="strut" style="height:1.138em;vertical-align:-0.25em;">
  
  
  
  </span>
  
  <span className="mord">
  <span className="mord,mathnormal">
  
  p
  
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
  <span className="mord,mathnormal,mtight">
  
  n
  
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
  
  <span className="mopen">
  
  (
  
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
  <span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">
  
  q
  
  </span>
  
  <span className="mord,mathnormal,mtight" style="margin-right:0.2222em;">
  
  V
  
  </span>
  
  <span className="mord,mtight">
  
  /
  
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
  <span className="strut" style="height:1.138em;vertical-align:-0.25em;">
  
  
  
  </span>
  
  <span className="mord">
  
  1
  
  </span>
  
  <span className="mclose">
  
  )
  
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
  
  <span className="mopen,mtight">
  
  (
  
  </span>
  
  <span className="mord,mathnormal,mtight">
  
  x
  
  </span>
  
  <span className="mbin,mtight">
  
  −
  
  </span>
  
  <span className="mord,mtight">
  <span className="mord,mathnormal,mtight">
  
  x
  
  </span>
  
  <span className="msupsub">
  <span className="vlist-t,vlist-t2">
  <span className="vlist-r">
  <span className="vlist" style="height:0.3448em;">
  <span style="top:-2.3567em;margin-left:0em;margin-right:0.0714em;">
  <span className="pstrut" style="height:2.5em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size3,size1,mtight">
  <span className="mord,mathnormal,mtight" style="margin-right:0.109em;">
  
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
  <span className="vlist" style="height:0.1433em;">
  <span>
  
  
  
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  
  <span className="mclose,mtight">
  
  )
  
  </span>
  
  <span className="mord,mtight">
  
  /
  
  </span>
  
  <span className="mord,mtight">
  <span className="mord,mathnormal,mtight">
  
  L
  
  </span>
  
  <span className="msupsub">
  <span className="vlist-t,vlist-t2">
  <span className="vlist-r">
  <span className="vlist" style="height:0.1645em;">
  <span style="top:-2.357em;margin-left:0em;margin-right:0.0714em;">
  <span className="pstrut" style="height:2.5em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size3,size1,mtight">
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
  </span>
  </span>
  </span>
  </span>
  </span>
  
  <span className="mspace" style="margin-right:1em;">
  
  
  
  </span>
  
  <span className="mpunct">
  
  ,
  
  </span>
  
  <span className="mspace" style="margin-right:0.1667em;">
  
  
  
  </span>
  
  <span className="mord,text">
  <span className="mord">
  
  for
  
  </span>
  </span>
  
  <span className="mord,mathnormal">
  
  x
  
  </span>
  
  <span className="mspace" style="margin-right:0.2778em;">
  
  
  
  </span>
  
  <span className="mrel">
  
  >
  </span>
  
  <span className="mspace" style="margin-right:0.2778em;">
  
  
  
  </span>
  </span>
  
  <span className="base">
  <span className="strut" style="height:0.5806em;vertical-align:-0.15em;">
  
  
  
  </span>
  
  <span className="mord">
  <span className="mord,mathnormal">
  
  x
  
  </span>
  
  <span className="msupsub">
  <span className="vlist-t,vlist-t2">
  <span className="vlist-r">
  <span className="vlist" style="height:0.3283em;">
  <span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
  <span className="pstrut" style="height:2.7em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size6,size3,mtight">
  <span className="mord,mathnormal,mtight" style="margin-right:0.109em;">
  
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

### 最终结果（省流版）

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 49.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture6-11.webp" />
      </p>
    </td>
    
    
      <td style="width: 50.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture6-12.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 49.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture6-13.webp" />
      </p>
    </td>
    
    
      <td style="width: 50.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture6-14.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

<mark>

18页是最终在准中性区的载流子分布（载流子越深入中性区，随着不断复合，其生命也在倒计时，浓度慢慢变少）

</mark>



### 例题一则

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture6-15.webp)

### 思考一下

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture6-16.webp)

#### 问题的直接回答：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

L

</mi>

<mi>

n

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

L_n

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
<span className="mord,mathnormal,mtight">

n

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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

 远大于典型器件尺寸

计算结果： <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

L

</mi>

<mi>

n

</mi>
</msub>

<mo>

=

</mo>

<mn>

85

</mn>

<mtext>



</mtext>

<mi>

μ

</mi>

<mtext>

m

</mtext>
</mrow>

<annotation encoding="application/x-tex">

L_n = 85 \text{ }\mu\text{m}

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
<span className="mord,mathnormal,mtight">

n

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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
<span className="strut" style="height:0.8389em;vertical-align:-0.1944em;">



</span>

<span className="mord">

85

</span>

<span className="mord,text">
<span className="mord">



</span>
</span>

<span className="mord,mathnormal">

μ

</span>

<span className="mord,text">
<span className="mord">

m

</span>
</span>
</span>
</span>
</span>

 （85微米）

- <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

L

</mi>

<mi>

n

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

L_n

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
<span className="mord,mathnormal,mtight">

n

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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

 **(扩散长度)的含义：** 它代表在P区中，一个被注入的少数载流子（电子）在与空穴复合之前，平均可以扩散的距离。（The average distance that an injected minority carrier can diffuse before recombination.）
- **“典型器件尺寸”的含义：** 在现代集成电路（IC）中，这个尺寸指的是晶体管的沟道长度（<span className="katex">
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

）或P-N结的结深（<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

x

</mi>

<mi>

j

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

x_j

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.7167em;vertical-align:-0.2861em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

x

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
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

）。在当前的微电子技术中，这个尺寸在纳米 (nm) 到亚微米 (sub-µm) 量级。例如，一个90纳米技术节点的晶体管，其物理栅长（<span className="katex">
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

）仅约37纳米（即 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mn>

0.037

</mn>

<mtext>



</mtext>

<mi>

μ

</mi>

<mtext>

m

</mtext>
</mrow>

<annotation encoding="application/x-tex">

0.037 \text{ }\mu\text{m}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8389em;vertical-align:-0.1944em;">



</span>

<span className="mord">

0.037

</span>

<span className="mord,text">
<span className="mord">



</span>
</span>

<span className="mord,mathnormal">

μ

</span>

<span className="mord,text">
<span className="mord">

m

</span>
</span>
</span>
</span>
</span>

）。

> **结论：** <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msub>
> <mi>
> 
> L
> 
> </mi>
> 
> <mi>
> 
> n
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
> <mn>
> 
> 85
> 
> </mn>
> 
> <mtext>
> 
> 
> 
> </mtext>
> 
> <mi>
> 
> μ
> 
> </mi>
> 
> <mtext>
> 
> m
> 
> </mtext>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> L_n = 85 \text{ }\mu\text{m}
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
> L
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
> <span className="mord,mathnormal,mtight">
> 
> n
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
> <span className="strut" style="height:0.8389em;vertical-align:-0.1944em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> 
> 85
> 
> </span>
> 
> <span className="mord,text">
> <span className="mord">
> 
> 
> 
> </span>
> </span>
> 
> <span className="mord,mathnormal">
> 
> μ
> 
> </span>
> 
> <span className="mord,text">
> <span className="mord">
> 
> m
> 
> </span>
> </span>
> </span>
> </span>
> </span>
> 
>  这个距离，比一个典型器件的尺寸（< 1 µm）要大几个数量级（100倍以上）

#### 知识点榨干：这个对比推翻了我们刚学的模型

这个计算结果的最重要意义在于，它证明了我们在 Lecture 6（幻灯片 17-18, 26）中刚刚用来推导“理想二极管方程”的**“长基区二极管”（Long-base diode）假设，在实际IC器件中是完全不成立的。**

#### A. “长基区”模型（理论推导）

- **假设：** 中性区的物理宽度 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

W

</mi>

<mi>

p

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

W_p

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

W

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.1389em;margin-right:0.05em;">
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

 远大于扩散长度 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

L

</mi>

<mi>

n

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

L_n

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
<span className="mord,mathnormal,mtight">

n

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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

 （即 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

W

</mi>

<mi>

p

</mi>
</msub>

<mo>

≫

</mo>

<msub>
<mi>

L

</mi>

<mi>

n

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

W_p \gg L_n

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

W

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.1389em;margin-right:0.05em;">
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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

≫

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



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
<span className="mord,mathnormal,mtight">

n

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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
- **边界条件：** <mark>

我们假设中性区延伸到无穷远，因此过剩载流子在

</mark>

 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

x

</mi>

<mo>

→

</mo>

<mi mathvariant="normal">

∞

</mi>
</mrow>

<annotation encoding="application/x-tex">

x \to \infty

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.4306em;">



</span>

<span className="mord,mathnormal">

x

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

 <mark>

处完全复合，

</mark>

<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi mathvariant="normal">

Δ

</mi>

<mi>

n

</mi>

<mo stretchy="false">

(

</mo>

<mi mathvariant="normal">

∞

</mi>

<mo stretchy="false">

)

</mo>

<mo>

=

</mo>

<mn>

0

</mn>
</mrow>

<annotation encoding="application/x-tex">

\Delta n(\infty) = 0

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord">

Δ

</span>

<span className="mord,mathnormal">

n

</span>

<span className="mopen">

(

</span>

<span className="mord">

∞

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

0

</span>
</span>
</span>
</span>

<mark>

。

</mark>
- **载流子分布：** 扩散方程 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mfrac>
<mrow>
<msup>
<mi>

d

</mi>

<mn>

2

</mn>
</msup>

<mi mathvariant="normal">

Δ

</mi>

<mi>

n

</mi>
</mrow>

<mrow>
<mi>

d

</mi>

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

<mo>

=

</mo>

<mfrac>
<mrow>
<mi mathvariant="normal">

Δ

</mi>

<mi>

n

</mi>
</mrow>

<msubsup>
<mi>

L

</mi>

<mi>

n

</mi>

<mn>

2

</mn>
</msubsup>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

\frac{d^2\Delta n}{dx^2} = \frac{\Delta n}{L_n^2}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.3629em;vertical-align:-0.345em;">



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
<span className="mord,mathnormal,mtight">

d

</span>

<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

x

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
<span className="mord,mathnormal,mtight">

d

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

2

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

<span className="mord,mtight">

Δ

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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.4175em;vertical-align:-0.5452em;">



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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

L

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.7463em;">
<span style="top:-2.214em;margin-left:0em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
<span className="mord,mathnormal,mtight">

n

</span>
</span>
</span>

<span style="top:-2.786em;margin-right:0.0714em;">
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
<span className="vlist" style="height:0.286em;">
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

<span style="top:-3.394em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">

Δ

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
<span className="vlist" style="height:0.5452em;">
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

 的解是指数衰减：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi mathvariant="normal">

Δ

</mi>

<mi>

n

</mi>

<mo stretchy="false">

(

</mo>

<mi>

x

</mi>

<mo stretchy="false">

)

</mo>

<mo>

∝

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

x

</mi>

<mi mathvariant="normal">

/

</mi>

<msub>
<mi>

L

</mi>

<mi>

n

</mi>
</msub>
</mrow>
</msup>
</mrow>

<annotation encoding="application/x-tex">

\Delta n(x) \propto e^{-x/L_n}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord">

Δ

</span>

<span className="mord,mathnormal">

n

</span>

<span className="mopen">

(

</span>

<span className="mord,mathnormal">

x

</span>

<span className="mclose">

)

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

x

</span>

<span className="mord,mtight">

/

</span>

<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

L

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1645em;">
<span style="top:-2.357em;margin-left:0em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
<span className="mord,mathnormal,mtight">

n

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
</span>
</span>
</span>
</span>
</span>
</span>
</span>

。
- **电流公式：** 电流由扩散长度 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

L

</mi>

<mi>

n

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

L_n

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
<span className="mord,mathnormal,mtight">

n

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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

 决定：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

I

</mi>

<mn>

0

</mn>
</msub>

<mo>

∝

</mo>

<mfrac>
<msub>
<mi>

D

</mi>

<mi>

n

</mi>
</msub>

<mrow>
<msub>
<mi>

L

</mi>

<mi>

n

</mi>
</msub>

<msub>
<mi>

N

</mi>

<mi>

A

</mi>
</msub>
</mrow>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

I_0 \propto \frac{D_n}{L_n N_A}

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
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0785em;margin-right:0.05em;">
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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

∝

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.3337em;vertical-align:-0.4453em;">



</span>

<span className="mord">
<span className="mopen,nulldelimiter">



</span>

<span className="mfrac">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.8884em;">
<span style="top:-2.655em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

L

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1645em;">
<span style="top:-2.357em;margin-left:0em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
<span className="mord,mathnormal,mtight">

n

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
<span className="mord,mathnormal,mtight" style="margin-right:0.109em;">

N

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3448em;">
<span style="top:-2.3567em;margin-left:-0.109em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
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
<span className="vlist" style="height:0.1433em;">
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

<span style="top:-3.4101em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

D

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1645em;">
<span style="top:-2.357em;margin-left:-0.0278em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
<span className="mord,mathnormal,mtight">

n

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
<span className="vlist" style="height:0.4453em;">
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

#### B. “短基区”模型（实际器件）<mark>（非重点，主要看区别）</mark>

- **现实 (来自本例)：** 中性区的物理宽度 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

W

</mi>

<mi>

p

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

W_p

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

W

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.1389em;margin-right:0.05em;">
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

 远小于扩散长度 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

L

</mi>

<mi>

n

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

L_n

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
<span className="mord,mathnormal,mtight">

n

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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

 （即 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

W

</mi>

<mi>

p

</mi>
</msub>

<mo>

≪

</mo>

<msub>
<mi>

L

</mi>

<mi>

n

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

W_p \ll L_n

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

W

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.1389em;margin-right:0.05em;">
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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

≪

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



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
<span className="mord,mathnormal,mtight">

n

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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
- **物理图像：** <mark>

被注入的少数载流子（电子）还没有来得及复合，就已经扩散到了P区另一端的金属接触（Ohmic Contact）处。

</mark>
- **新的边界条件：** <mark>

金属接触是一个理想的复合点（具有无限的复合速率）。因此，边界条件变为

</mark>

 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi mathvariant="normal">

Δ

</mi>

<mi>

n

</mi>

<mo stretchy="false">

(

</mo>

<msub>
<mi>

W

</mi>

<mi>

p

</mi>
</msub>

<mo stretchy="false">

)

</mo>

<mo>

≈

</mo>

<mn>

0

</mn>
</mrow>

<annotation encoding="application/x-tex">

\Delta n(W_p) \approx 0

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.0361em;vertical-align:-0.2861em;">



</span>

<span className="mord">

Δ

</span>

<span className="mord,mathnormal">

n

</span>

<span className="mopen">

(

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.1389em;">

W

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.1389em;margin-right:0.05em;">
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
<span className="strut" style="height:0.6444em;">



</span>

<span className="mord">

0

</span>
</span>
</span>
</span>

<mark>

（在P区末端

</mark>

 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

W

</mi>

<mi>

p

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

W_p

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

W

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.1389em;margin-right:0.05em;">
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

 <mark>

处浓度为0）。

</mark>
- **新的载流子分布：**
  - 由于 <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <msub>
  <mi>
  
  W
  
  </mi>
  
  <mi>
  
  p
  
  </mi>
  </msub>
  
  <mo>
  
  ≪
  
  </mo>
  
  <msub>
  <mi>
  
  L
  
  </mi>
  
  <mi>
  
  n
  
  </mi>
  </msub>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  W_p \ll L_n
  
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
  
  W
  
  </span>
  
  <span className="msupsub">
  <span className="vlist-t,vlist-t2">
  <span className="vlist-r">
  <span className="vlist" style="height:0.1514em;">
  <span style="top:-2.55em;margin-left:-0.1389em;margin-right:0.05em;">
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
  
  <span className="mspace" style="margin-right:0.2778em;">
  
  
  
  </span>
  
  <span className="mrel">
  
  ≪
  
  </span>
  
  <span className="mspace" style="margin-right:0.2778em;">
  
  
  
  </span>
  </span>
  
  <span className="base">
  <span className="strut" style="height:0.8333em;vertical-align:-0.15em;">
  
  
  
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
  <span className="mord,mathnormal,mtight">
  
  n
  
  </span>
  </span>
  </span>
  </span>
  
  <span className="vlist-s">
  
  ​
  
  </span>
  </span>
  
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
  
  ，载流子在扩散通过 <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <msub>
  <mi>
  
  W
  
  </mi>
  
  <mi>
  
  p
  
  </mi>
  </msub>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  W_p
  
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
  
  W
  
  </span>
  
  <span className="msupsub">
  <span className="vlist-t,vlist-t2">
  <span className="vlist-r">
  <span className="vlist" style="height:0.1514em;">
  <span style="top:-2.55em;margin-left:-0.1389em;margin-right:0.05em;">
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
  
   的短暂时间内几乎不发生复合。
  - 扩散方程 <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mfrac>
  <mrow>
  <msup>
  <mi>
  
  d
  
  </mi>
  
  <mn>
  
  2
  
  </mn>
  </msup>
  
  <mi mathvariant="normal">
  
  Δ
  
  </mi>
  
  <mi>
  
  n
  
  </mi>
  </mrow>
  
  <mrow>
  <mi>
  
  d
  
  </mi>
  
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
  
  <mo>
  
  =
  
  </mo>
  
  <mfrac>
  <mrow>
  <mi mathvariant="normal">
  
  Δ
  
  </mi>
  
  <mi>
  
  n
  
  </mi>
  </mrow>
  
  <msubsup>
  <mi>
  
  L
  
  </mi>
  
  <mi>
  
  n
  
  </mi>
  
  <mn>
  
  2
  
  </mn>
  </msubsup>
  </mfrac>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  \frac{d^2\Delta n}{dx^2} = \frac{\Delta n}{L_n^2}
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:1.3629em;vertical-align:-0.345em;">
  
  
  
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
  <span className="mord,mathnormal,mtight">
  
  d
  
  </span>
  
  <span className="mord,mtight">
  <span className="mord,mathnormal,mtight">
  
  x
  
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
  <span className="mord,mathnormal,mtight">
  
  d
  
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
  
  2
  
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  
  <span className="mord,mtight">
  
  Δ
  
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
  
  <span className="mspace" style="margin-right:0.2778em;">
  
  
  
  </span>
  
  <span className="mrel">
  
  =
  
  </span>
  
  <span className="mspace" style="margin-right:0.2778em;">
  
  
  
  </span>
  </span>
  
  <span className="base">
  <span className="strut" style="height:1.4175em;vertical-align:-0.5452em;">
  
  
  
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
  <span className="mord,mtight">
  <span className="mord,mathnormal,mtight">
  
  L
  
  </span>
  
  <span className="msupsub">
  <span className="vlist-t,vlist-t2">
  <span className="vlist-r">
  <span className="vlist" style="height:0.7463em;">
  <span style="top:-2.214em;margin-left:0em;margin-right:0.0714em;">
  <span className="pstrut" style="height:2.5em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size3,size1,mtight">
  <span className="mord,mathnormal,mtight">
  
  n
  
  </span>
  </span>
  </span>
  
  <span style="top:-2.786em;margin-right:0.0714em;">
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
  <span className="vlist" style="height:0.286em;">
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
  
  <span style="top:-3.394em;">
  <span className="pstrut" style="height:3em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size6,size3,mtight">
  <span className="mord,mtight">
  <span className="mord,mtight">
  
  Δ
  
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
  <span className="vlist" style="height:0.5452em;">
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
  
   中的复合项 <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mfrac>
  <mrow>
  <mi mathvariant="normal">
  
  Δ
  
  </mi>
  
  <mi>
  
  n
  
  </mi>
  </mrow>
  
  <msubsup>
  <mi>
  
  L
  
  </mi>
  
  <mi>
  
  n
  
  </mi>
  
  <mn>
  
  2
  
  </mn>
  </msubsup>
  </mfrac>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  \frac{\Delta n}{L_n^2}
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:1.4175em;vertical-align:-0.5452em;">
  
  
  
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
  <span className="mord,mtight">
  <span className="mord,mathnormal,mtight">
  
  L
  
  </span>
  
  <span className="msupsub">
  <span className="vlist-t,vlist-t2">
  <span className="vlist-r">
  <span className="vlist" style="height:0.7463em;">
  <span style="top:-2.214em;margin-left:0em;margin-right:0.0714em;">
  <span className="pstrut" style="height:2.5em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size3,size1,mtight">
  <span className="mord,mathnormal,mtight">
  
  n
  
  </span>
  </span>
  </span>
  
  <span style="top:-2.786em;margin-right:0.0714em;">
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
  <span className="vlist" style="height:0.286em;">
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
  
  <span style="top:-3.394em;">
  <span className="pstrut" style="height:3em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size6,size3,mtight">
  <span className="mord,mtight">
  <span className="mord,mtight">
  
  Δ
  
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
  <span className="vlist" style="height:0.5452em;">
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
  
   几乎为零。
  - 方程简化为 <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mfrac>
  <mrow>
  <msup>
  <mi>
  
  d
  
  </mi>
  
  <mn>
  
  2
  
  </mn>
  </msup>
  
  <mi mathvariant="normal">
  
  Δ
  
  </mi>
  
  <mi>
  
  n
  
  </mi>
  </mrow>
  
  <mrow>
  <mi>
  
  d
  
  </mi>
  
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
  
  <mo>
  
  ≈
  
  </mo>
  
  <mn>
  
  0
  
  </mn>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  \frac{d^2\Delta n}{dx^2} \approx 0
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:1.3629em;vertical-align:-0.345em;">
  
  
  
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
  <span className="mord,mathnormal,mtight">
  
  d
  
  </span>
  
  <span className="mord,mtight">
  <span className="mord,mathnormal,mtight">
  
  x
  
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
  <span className="mord,mathnormal,mtight">
  
  d
  
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
  
  2
  
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  
  <span className="mord,mtight">
  
  Δ
  
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
  
  0
  
  </span>
  </span>
  </span>
  </span>
  
  。
  - 这个方程的解是一个线性分布，不再是指数衰减。
- **新的电流公式：**
  - 扩散电流 <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <msub>
  <mi>
  
  J
  
  </mi>
  
  <mi>
  
  n
  
  </mi>
  </msub>
  
  <mo>
  
  ≈
  
  </mo>
  
  <mi>
  
  q
  
  </mi>
  
  <msub>
  <mi>
  
  D
  
  </mi>
  
  <mi>
  
  n
  
  </mi>
  </msub>
  
  <mfrac>
  <mrow>
  <mi>
  
  d
  
  </mi>
  
  <mi mathvariant="normal">
  
  Δ
  
  </mi>
  
  <mi>
  
  n
  
  </mi>
  </mrow>
  
  <mrow>
  <mi>
  
  d
  
  </mi>
  
  <mi>
  
  x
  
  </mi>
  </mrow>
  </mfrac>
  
  <mo>
  
  ≈
  
  </mo>
  
  <mi>
  
  q
  
  </mi>
  
  <msub>
  <mi>
  
  D
  
  </mi>
  
  <mi>
  
  n
  
  </mi>
  </msub>
  
  <mfrac>
  <mrow>
  <mi mathvariant="normal">
  
  Δ
  
  </mi>
  
  <mi>
  
  n
  
  </mi>
  
  <mo stretchy="false">
  
  (
  
  </mo>
  
  <mo>
  
  −
  
  </mo>
  
  <msub>
  <mi>
  
  x
  
  </mi>
  
  <mi>
  
  p
  
  </mi>
  </msub>
  
  <mo stretchy="false">
  
  )
  
  </mo>
  
  <mo>
  
  −
  
  </mo>
  
  <mn>
  
  0
  
  </mn>
  </mrow>
  
  <msub>
  <mi>
  
  W
  
  </mi>
  
  <mi>
  
  p
  
  </mi>
  </msub>
  </mfrac>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  J_n \approx q D_n \frac{d\Delta n}{dx} \approx q D_n \frac{\Delta n(-x_p) - 0}{W_p}
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:0.8333em;vertical-align:-0.15em;">
  
  
  
  </span>
  
  <span className="mord">
  <span className="mord,mathnormal" style="margin-right:0.0962em;">
  
  J
  
  </span>
  
  <span className="msupsub">
  <span className="vlist-t,vlist-t2">
  <span className="vlist-r">
  <span className="vlist" style="height:0.1514em;">
  <span style="top:-2.55em;margin-left:-0.0962em;margin-right:0.05em;">
  <span className="pstrut" style="height:2.7em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size6,size3,mtight">
  <span className="mord,mathnormal,mtight">
  
  n
  
  </span>
  </span>
  </span>
  </span>
  
  <span className="vlist-s">
  
  ​
  
  </span>
  </span>
  
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
  <span className="strut" style="height:1.2251em;vertical-align:-0.345em;">
  
  
  
  </span>
  
  <span className="mord,mathnormal" style="margin-right:0.0359em;">
  
  q
  
  </span>
  
  <span className="mord">
  <span className="mord,mathnormal" style="margin-right:0.0278em;">
  
  D
  
  </span>
  
  <span className="msupsub">
  <span className="vlist-t,vlist-t2">
  <span className="vlist-r">
  <span className="vlist" style="height:0.1514em;">
  <span style="top:-2.55em;margin-left:-0.0278em;margin-right:0.05em;">
  <span className="pstrut" style="height:2.7em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size6,size3,mtight">
  <span className="mord,mathnormal,mtight">
  
  n
  
  </span>
  </span>
  </span>
  </span>
  
  <span className="vlist-s">
  
  ​
  
  </span>
  </span>
  
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
  
  x
  
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
  
  <span className="mord,mtight">
  
  Δ
  
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
  
  <span className="mspace" style="margin-right:0.2778em;">
  
  
  
  </span>
  
  <span className="mrel">
  
  ≈
  
  </span>
  
  <span className="mspace" style="margin-right:0.2778em;">
  
  
  
  </span>
  </span>
  
  <span className="base">
  <span className="strut" style="height:1.5746em;vertical-align:-0.5423em;">
  
  
  
  </span>
  
  <span className="mord,mathnormal" style="margin-right:0.0359em;">
  
  q
  
  </span>
  
  <span className="mord">
  <span className="mord,mathnormal" style="margin-right:0.0278em;">
  
  D
  
  </span>
  
  <span className="msupsub">
  <span className="vlist-t,vlist-t2">
  <span className="vlist-r">
  <span className="vlist" style="height:0.1514em;">
  <span style="top:-2.55em;margin-left:-0.0278em;margin-right:0.05em;">
  <span className="pstrut" style="height:2.7em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size6,size3,mtight">
  <span className="mord,mathnormal,mtight">
  
  n
  
  </span>
  </span>
  </span>
  </span>
  
  <span className="vlist-s">
  
  ​
  
  </span>
  </span>
  
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
  <span className="mopen,nulldelimiter">
  
  
  
  </span>
  
  <span className="mfrac">
  <span className="vlist-t,vlist-t2">
  <span className="vlist-r">
  <span className="vlist" style="height:1.0323em;">
  <span style="top:-2.655em;">
  <span className="pstrut" style="height:3em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size6,size3,mtight">
  <span className="mord,mtight">
  <span className="mord,mtight">
  <span className="mord,mathnormal,mtight" style="margin-right:0.1389em;">
  
  W
  
  </span>
  
  <span className="msupsub">
  <span className="vlist-t,vlist-t2">
  <span className="vlist-r">
  <span className="vlist" style="height:0.1645em;">
  <span style="top:-2.357em;margin-left:-0.1389em;margin-right:0.0714em;">
  <span className="pstrut" style="height:2.5em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size3,size1,mtight">
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
  
  <span style="top:-3.5073em;">
  <span className="pstrut" style="height:3em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size6,size3,mtight">
  <span className="mord,mtight">
  <span className="mord,mtight">
  
  Δ
  
  </span>
  
  <span className="mord,mathnormal,mtight">
  
  n
  
  </span>
  
  <span className="mopen,mtight">
  
  (
  
  </span>
  
  <span className="mord,mtight">
  
  −
  
  </span>
  
  <span className="mord,mtight">
  <span className="mord,mathnormal,mtight">
  
  x
  
  </span>
  
  <span className="msupsub">
  <span className="vlist-t,vlist-t2">
  <span className="vlist-r">
  <span className="vlist" style="height:0.1645em;">
  <span style="top:-2.357em;margin-left:0em;margin-right:0.0714em;">
  <span className="pstrut" style="height:2.5em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size3,size1,mtight">
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
  <span className="vlist" style="height:0.2819em;">
  <span>
  
  
  
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  
  <span className="mclose,mtight">
  
  )
  
  </span>
  
  <span className="mbin,mtight">
  
  −
  
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
  </span>
  
  。
  - 电流现在由物理宽度 <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <msub>
  <mi>
  
  W
  
  </mi>
  
  <mi>
  
  p
  
  </mi>
  </msub>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  W_p
  
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
  
  W
  
  </span>
  
  <span className="msupsub">
  <span className="vlist-t,vlist-t2">
  <span className="vlist-r">
  <span className="vlist" style="height:0.1514em;">
  <span style="top:-2.55em;margin-left:-0.1389em;margin-right:0.05em;">
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
  
   决定，而不是扩散长度 <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <msub>
  <mi>
  
  L
  
  </mi>
  
  <mi>
  
  n
  
  </mi>
  </msub>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  L_n
  
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
  <span className="mord,mathnormal,mtight">
  
  n
  
  </span>
  </span>
  </span>
  </span>
  
  <span className="vlist-s">
  
  ​
  
  </span>
  </span>
  
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
  - 反向饱和电流变为：<span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <msub>
  <mi>
  
  I
  
  </mi>
  
  <mn>
  
  0
  
  </mn>
  </msub>
  
  <mo>
  
  =
  
  </mo>
  
  <mi>
  
  A
  
  </mi>
  
  <mi>
  
  q
  
  </mi>
  
  <msubsup>
  <mi>
  
  n
  
  </mi>
  
  <mi>
  
  i
  
  </mi>
  
  <mn>
  
  2
  
  </mn>
  </msubsup>
  
  <mrow>
  <mo fence="true">
  
  (
  
  </mo>
  
  <mfrac>
  <msub>
  <mi>
  
  D
  
  </mi>
  
  <mi>
  
  p
  
  </mi>
  </msub>
  
  <msub>
  <mi>
  
  W
  
  </mi>
  
  <mi>
  
  N
  
  </mi>
  </msub>
  </mfrac>
  
  <mo>
  
  +
  
  </mo>
  
  <mfrac>
  <msub>
  <mi>
  
  D
  
  </mi>
  
  <mi>
  
  n
  
  </mi>
  </msub>
  
  <msub>
  <mi>
  
  W
  
  </mi>
  
  <mi>
  
  P
  
  </mi>
  </msub>
  </mfrac>
  
  <mo fence="true">
  
  )
  
  </mo>
  </mrow>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  I_0 = A q n_i^2 \left( \frac{D_p}{W_N} + \frac{D_n}{W_P} \right)
  
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
  <span className="vlist" style="height:0.3011em;">
  <span style="top:-2.55em;margin-left:-0.0785em;margin-right:0.05em;">
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
  
  <span className="mord,mathnormal">
  
  A
  
  </span>
  
  <span className="mord,mathnormal" style="margin-right:0.0359em;">
  
  q
  
  </span>
  
  <span className="mord">
  <span className="mord,mathnormal">
  
  n
  
  </span>
  
  <span className="msupsub">
  <span className="vlist-t,vlist-t2">
  <span className="vlist-r">
  <span className="vlist" style="height:0.8141em;">
  <span style="top:-2.4413em;margin-left:0em;margin-right:0.05em;">
  <span className="pstrut" style="height:2.7em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size6,size3,mtight">
  <span className="mord,mathnormal,mtight">
  
  i
  
  </span>
  </span>
  </span>
  
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
  
  <span className="vlist-s">
  
  ​
  
  </span>
  </span>
  
  <span className="vlist-r">
  <span className="vlist" style="height:0.2587em;">
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
  
  <span className="mord">
  <span className="mopen,nulldelimiter">
  
  
  
  </span>
  
  <span className="mfrac">
  <span className="vlist-t,vlist-t2">
  <span className="vlist-r">
  <span className="vlist" style="height:0.9857em;">
  <span style="top:-2.655em;">
  <span className="pstrut" style="height:3em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size6,size3,mtight">
  <span className="mord,mtight">
  <span className="mord,mtight">
  <span className="mord,mathnormal,mtight" style="margin-right:0.1389em;">
  
  W
  
  </span>
  
  <span className="msupsub">
  <span className="vlist-t,vlist-t2">
  <span className="vlist-r">
  <span className="vlist" style="height:0.3448em;">
  <span style="top:-2.3567em;margin-left:-0.1389em;margin-right:0.0714em;">
  <span className="pstrut" style="height:2.5em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size3,size1,mtight">
  <span className="mord,mathnormal,mtight" style="margin-right:0.109em;">
  
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
  <span className="vlist" style="height:0.1433em;">
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
  
  <span style="top:-3.5073em;">
  <span className="pstrut" style="height:3em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size6,size3,mtight">
  <span className="mord,mtight">
  <span className="mord,mtight">
  <span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">
  
  D
  
  </span>
  
  <span className="msupsub">
  <span className="vlist-t,vlist-t2">
  <span className="vlist-r">
  <span className="vlist" style="height:0.1645em;">
  <span style="top:-2.357em;margin-left:-0.0278em;margin-right:0.0714em;">
  <span className="pstrut" style="height:2.5em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size3,size1,mtight">
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
  </span>
  
  <span className="vlist-s">
  
  ​
  
  </span>
  </span>
  
  <span className="vlist-r">
  <span className="vlist" style="height:0.4453em;">
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
  
  <span className="mord">
  <span className="mopen,nulldelimiter">
  
  
  
  </span>
  
  <span className="mfrac">
  <span className="vlist-t,vlist-t2">
  <span className="vlist-r">
  <span className="vlist" style="height:0.8884em;">
  <span style="top:-2.655em;">
  <span className="pstrut" style="height:3em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size6,size3,mtight">
  <span className="mord,mtight">
  <span className="mord,mtight">
  <span className="mord,mathnormal,mtight" style="margin-right:0.1389em;">
  
  W
  
  </span>
  
  <span className="msupsub">
  <span className="vlist-t,vlist-t2">
  <span className="vlist-r">
  <span className="vlist" style="height:0.3448em;">
  <span style="top:-2.3567em;margin-left:-0.1389em;margin-right:0.0714em;">
  <span className="pstrut" style="height:2.5em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size3,size1,mtight">
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
  <span className="vlist" style="height:0.1433em;">
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
  
  <span style="top:-3.4101em;">
  <span className="pstrut" style="height:3em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size6,size3,mtight">
  <span className="mord,mtight">
  <span className="mord,mtight">
  <span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">
  
  D
  
  </span>
  
  <span className="msupsub">
  <span className="vlist-t,vlist-t2">
  <span className="vlist-r">
  <span className="vlist" style="height:0.1645em;">
  <span style="top:-2.357em;margin-left:-0.0278em;margin-right:0.0714em;">
  <span className="pstrut" style="height:2.5em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size3,size1,mtight">
  <span className="mord,mathnormal,mtight">
  
  n
  
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
  <span className="vlist" style="height:0.4453em;">
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
  
  。

## 六、理想晶体管I-V方程（P23-27）

> 在理想二极管中，正向电流由注入到准中性区的少数载流子扩散并复合所驱动。电流大小随外加电压呈指数增长。

### 理想二极管假设 (Page 24)

1. 突变结，准中性区均匀掺杂
2. 稳态（DC）条件
3. 准中性区满足低水平注入
4. <mark>

**最关键假设：**

</mark>

 <mark>

耗尽层（SCR）中没有载流子的产生或复合 (R-G=0)

</mark>

---

### 推导逻辑 (Page 25-26)

根据假设4，耗尽区内 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mfrac>
<mrow>
<mi>

d

</mi>

<msub>
<mi>

J

</mi>

<mi>

n

</mi>
</msub>
</mrow>

<mrow>
<mi>

d

</mi>

<mi>

x

</mi>
</mrow>
</mfrac>

<mo>

=

</mo>

<mn>

0

</mn>
</mrow>

<annotation encoding="application/x-tex">

\frac{dJ_n}{dx}=0

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.2412em;vertical-align:-0.345em;">



</span>

<span className="mord">
<span className="mopen,nulldelimiter">



</span>

<span className="mfrac">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.8962em;">
<span style="top:-2.655em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

d

</span>

<span className="mord,mathnormal,mtight">

x

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

<span style="top:-3.4101em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

d

</span>

<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0962em;">

J

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1645em;">
<span style="top:-2.357em;margin-left:-0.0962em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
<span className="mord,mathnormal,mtight">

n

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

 且 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mfrac>
<mrow>
<mi>

d

</mi>

<msub>
<mi>

J

</mi>

<mi>

p

</mi>
</msub>
</mrow>

<mrow>
<mi>

d

</mi>

<mi>

x

</mi>
</mrow>
</mfrac>

<mo>

=

</mo>

<mn>

0

</mn>
</mrow>

<annotation encoding="application/x-tex">

\frac{dJ_p}{dx}=0

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.3384em;vertical-align:-0.345em;">



</span>

<span className="mord">
<span className="mopen,nulldelimiter">



</span>

<span className="mfrac">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.9934em;">
<span style="top:-2.655em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

d

</span>

<span className="mord,mathnormal,mtight">

x

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

<span style="top:-3.5073em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

d

</span>

<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0962em;">

J

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1645em;">
<span style="top:-2.357em;margin-left:-0.0962em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
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

 。这意味着 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

J

</mi>

<mi>

n

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

J_n

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0962em;">

J

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0962em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

n

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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

J

</mi>

<mi>

p

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

J_p

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9694em;vertical-align:-0.2861em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0962em;">

J

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0962em;margin-right:0.05em;">
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

 各自恒定地穿过耗尽区。

因此，总电流 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

J

</mi>
</mrow>

<annotation encoding="application/x-tex">

J

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0962em;">

J

</span>
</span>
</span>
</span>

 (在整个器件中都恒定 )，等于耗尽区边界处的少数载流子扩散电流之和：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

J

</mi>

<mo>

=

</mo>

<msub>
<mi>

J

</mi>

<mi>

n

</mi>
</msub>

<mo stretchy="false">

(

</mo>

<mtext>

at

</mtext>

<mi>

x

</mi>

<mo>

=

</mo>

<mo>

−

</mo>

<msub>
<mi>

x

</mi>

<mi>

p

</mi>
</msub>

<mo stretchy="false">

)

</mo>

<mo>

+

</mo>

<msub>
<mi>

J

</mi>

<mi>

p

</mi>
</msub>

<mo stretchy="false">

(

</mo>

<mtext>

at

</mtext>

<mi>

x

</mi>

<mo>

=

</mo>

<msub>
<mi>

x

</mi>

<mi>

n

</mi>
</msub>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

J = J_n(\text{at } x=-x_p) + J_p(\text{at } x=x_n)

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0962em;">

J

</span>

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
<span className="mord,mathnormal" style="margin-right:0.0962em;">

J

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0962em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

n

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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

<span className="mord,text">
<span className="mord">

at

</span>
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
<span className="strut" style="height:1.0361em;vertical-align:-0.2861em;">



</span>

<span className="mord">

−

</span>

<span className="mord">
<span className="mord,mathnormal">

x

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
<span className="strut" style="height:1.0361em;vertical-align:-0.2861em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0962em;">

J

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0962em;margin-right:0.05em;">
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

<span className="mopen">

(

</span>

<span className="mord,text">
<span className="mord">

at

</span>
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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

x

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

n

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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

我们来计算这两个分量：

#### 计算 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

J

</mi>

<mi>

p

</mi>
</msub>

<mo stretchy="false">

(

</mo>

<msub>
<mi>

x

</mi>

<mi>

n

</mi>
</msub>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

J_p(x_n)

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.0361em;vertical-align:-0.2861em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0962em;">

J

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0962em;margin-right:0.05em;">
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

<span className="mopen">

(

</span>

<span className="mord">
<span className="mord,mathnormal">

x

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

n

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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

计算 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

J

</mi>

<mi>

n

</mi>
</msub>

<mo stretchy="false">

(

</mo>

<mo>

−

</mo>

<msub>
<mi>

x

</mi>

<mi>

p

</mi>
</msub>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

J_n(-x_p)

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.0361em;vertical-align:-0.2861em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0962em;">

J

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0962em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

n

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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

−

</span>

<span className="mord">
<span className="mord,mathnormal">

x

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

<span className="mclose">

)

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

J

</mi>

<mi>

p

</mi>
</msub>

<mo stretchy="false">

(

</mo>

<msub>
<mi>

x

</mi>

<mi>

n

</mi>
</msub>

<mo stretchy="false">

)

</mo>

<mo>

=

</mo>

<mo>

−

</mo>

<mi>

q

</mi>

<msub>
<mi>

D

</mi>

<mi>

p

</mi>
</msub>

<mfrac>
<mrow>
<mi>

d

</mi>

<mi mathvariant="normal">

Δ

</mi>

<mi>

p

</mi>
</mrow>

<mrow>
<mi>

d

</mi>

<mi>

x

</mi>
</mrow>
</mfrac>

<msub>
<mi mathvariant="normal">

∣

</mi>

<mrow>
<mi>

x

</mi>

<mo>

=

</mo>

<msub>
<mi>

x

</mi>

<mi>

n

</mi>
</msub>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

J_p(x_n) = -qD_p \frac{d\Delta p}{dx}|_{x=x_n}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.0361em;vertical-align:-0.2861em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0962em;">

J

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0962em;margin-right:0.05em;">
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

<span className="mopen">

(

</span>

<span className="mord">
<span className="mord,mathnormal">

x

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

n

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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
<span className="strut" style="height:2.0574em;vertical-align:-0.686em;">



</span>

<span className="mord">

−

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

q

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

D

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0278em;margin-right:0.05em;">
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
<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal">

x

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

d

</span>

<span className="mord">

Δ

</span>

<span className="mord,mathnormal">

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
<span className="mord">

∣

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

x

</span>

<span className="mrel,mtight">

=

</span>

<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

x

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1645em;">
<span style="top:-2.357em;margin-left:0em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
<span className="mord,mathnormal,mtight">

n

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

<mo>

−

</mo>

<mi>

q

</mi>

<msub>
<mi>

D

</mi>

<mi>

p

</mi>
</msub>

<mo>

⋅

</mo>

<mo stretchy="false">

[

</mo>

<msub>
<mi>

p

</mi>

<mrow>
<mi>

n

</mi>

<mn>

0

</mn>
</mrow>
</msub>

<mo stretchy="false">

(

</mo>

<msup>
<mi>

e

</mi>

<mrow>
<mi>

q

</mi>

<mi>

V

</mi>

<mi mathvariant="normal">

/

</mi>

<mi>

k

</mi>

<mi>

T

</mi>
</mrow>
</msup>

<mo>

−

</mo>

<mn>

1

</mn>

<mo stretchy="false">

)

</mo>

<mo stretchy="false">

]

</mo>

<mo>

⋅

</mo>

<mo stretchy="false">

(

</mo>

<mo>

−

</mo>

<mfrac>
<mn>

1

</mn>

<msub>
<mi>

L

</mi>

<mi>

p

</mi>
</msub>
</mfrac>

<mo stretchy="false">

)

</mo>

<msup>
<mi>

e

</mi>

<mrow>
<mo>

−

</mo>

<mo stretchy="false">

(

</mo>

<msub>
<mi>

x

</mi>

<mi>

n

</mi>
</msub>

<mo>

−

</mo>

<msub>
<mi>

x

</mi>

<mi>

N

</mi>
</msub>

<mo stretchy="false">

)

</mo>

<mi mathvariant="normal">

/

</mi>

<msub>
<mi>

L

</mi>

<mi>

p

</mi>
</msub>
</mrow>
</msup>
</mrow>

<annotation encoding="application/x-tex">

= -qD_p \cdot [p_{n0}(e^{qV/kT}-1)] \cdot (-\frac{1}{L_p}) e^{-(x_n-x_N)/L_p}

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
<span className="strut" style="height:0.9694em;vertical-align:-0.2861em;">



</span>

<span className="mord">

−

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

q

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

D

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0278em;margin-right:0.05em;">
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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

⋅

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.188em;vertical-align:-0.25em;">



</span>

<span className="mopen">

[

</span>

<span className="mord">
<span className="mord,mathnormal">

p

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
<span className="mord,mathnormal,mtight">

n

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

<span className="mopen">

(

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
<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

q

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.2222em;">

V

</span>

<span className="mord,mtight">

/

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

1

</span>

<span className="mclose">

)]

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
<span className="strut" style="height:2.2935em;vertical-align:-0.9721em;">



</span>

<span className="mopen">

(

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
<span className="vlist" style="height:1.3214em;">
<span style="top:-2.314em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
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

<span className="mclose">

)

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

<span className="mopen,mtight">

(

</span>

<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

x

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1645em;">
<span style="top:-2.357em;margin-left:0em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
<span className="mord,mathnormal,mtight">

n

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

<span className="mbin,mtight">

−

</span>

<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

x

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3448em;">
<span style="top:-2.3567em;margin-left:0em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.109em;">

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
<span className="vlist" style="height:0.1433em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>

<span className="mclose,mtight">

)

</span>

<span className="mord,mtight">

/

</span>

<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

L

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1645em;">
<span style="top:-2.357em;margin-left:0em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
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
<mo>

=

</mo>

<mi>

q

</mi>

<mfrac>
<msub>
<mi>

D

</mi>

<mi>

p

</mi>
</msub>

<msub>
<mi>

L

</mi>

<mi>

p

</mi>
</msub>
</mfrac>

<msub>
<mi>

p

</mi>

<mrow>
<mi>

n

</mi>

<mn>

0

</mn>
</mrow>
</msub>

<mo stretchy="false">

(

</mo>

<msup>
<mi>

e

</mi>

<mrow>
<mi>

q

</mi>

<mi>

V

</mi>

<mi mathvariant="normal">

/

</mi>

<mi>

k

</mi>

<mi>

T

</mi>
</mrow>
</msup>

<mo>

−

</mo>

<mn>

1

</mn>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

= q \frac{D_p}{L_p} p_{n0} (e^{qV/kT}-1)

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
<span className="strut" style="height:2.3324em;vertical-align:-0.9721em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

q

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

D

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0278em;margin-right:0.05em;">
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
<span className="mord,mathnormal">

p

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
<span className="mord,mathnormal,mtight">

n

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

<span className="mopen">

(

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
<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

q

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.2222em;">

V

</span>

<span className="mord,mtight">

/

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

1

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

J

</mi>

<mi>

n

</mi>
</msub>

<mo stretchy="false">

(

</mo>

<mo>

−

</mo>

<msub>
<mi>

x

</mi>

<mi>

p

</mi>
</msub>

<mo stretchy="false">

)

</mo>

<mo>

=

</mo>

<mi>

q

</mi>

<msub>
<mi>

D

</mi>

<mi>

n

</mi>
</msub>

<mfrac>
<mrow>
<mi>

d

</mi>

<mi mathvariant="normal">

Δ

</mi>

<mi>

n

</mi>
</mrow>

<mrow>
<mi>

d

</mi>

<mi>

x

</mi>
</mrow>
</mfrac>

<msub>
<mi mathvariant="normal">

∣

</mi>

<mrow>
<mi>

x

</mi>

<mo>

=

</mo>

<mo>

−

</mo>

<msub>
<mi>

x

</mi>

<mi>

p

</mi>
</msub>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

J_n(-x_p) = qD_n \frac{d\Delta n}{dx}|_{x=-x_p}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.0361em;vertical-align:-0.2861em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0962em;">

J

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0962em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

n

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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

−

</span>

<span className="mord">
<span className="mord,mathnormal">

x

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
<span className="strut" style="height:2.0574em;vertical-align:-0.686em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

q

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

D

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0278em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

n

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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
<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal">

x

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

d

</span>

<span className="mord">

Δ

</span>

<span className="mord,mathnormal">

n

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
<span className="mord">

∣

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.2583em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

x

</span>

<span className="mrel,mtight">

=

</span>

<span className="mord,mtight">

−

</span>

<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

x

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1645em;">
<span style="top:-2.357em;margin-left:0em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
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
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.3473em;">
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
<mo>

=

</mo>

<mi>

q

</mi>

<msub>
<mi>

D

</mi>

<mi>

n

</mi>
</msub>

<mo>

⋅

</mo>

<mo stretchy="false">

[

</mo>

<msub>
<mi>

n

</mi>

<mrow>
<mi>

p

</mi>

<mn>

0

</mn>
</mrow>
</msub>

<mo stretchy="false">

(

</mo>

<msup>
<mi>

e

</mi>

<mrow>
<mi>

q

</mi>

<mi>

V

</mi>

<mi mathvariant="normal">

/

</mi>

<mi>

k

</mi>

<mi>

T

</mi>
</mrow>
</msup>

<mo>

−

</mo>

<mn>

1

</mn>

<mo stretchy="false">

)

</mo>

<mo stretchy="false">

]

</mo>

<mo>

⋅

</mo>

<mo stretchy="false">

(

</mo>

<mfrac>
<mn>

1

</mn>

<msub>
<mi>

L

</mi>

<mi>

n

</mi>
</msub>
</mfrac>

<mo stretchy="false">

)

</mo>

<msup>
<mi>

e

</mi>

<mrow>
<mo stretchy="false">

(

</mo>

<mo>

−

</mo>

<msub>
<mi>

x

</mi>

<mi>

p

</mi>
</msub>

<mo>

−

</mo>

<msub>
<mi>

x

</mi>

<mi>

P

</mi>
</msub>

<mo stretchy="false">

)

</mo>

<mi mathvariant="normal">

/

</mi>

<msub>
<mi>

L

</mi>

<mi>

n

</mi>
</msub>
</mrow>
</msup>
</mrow>

<annotation encoding="application/x-tex">

= qD_n \cdot [n_{p0}(e^{qV/kT}-1)] \cdot (\frac{1}{L_n}) e^{(-x_p-x_P)/L_n}

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
<span className="strut" style="height:0.8778em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

q

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

D

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0278em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

n

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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
<span className="strut" style="height:1.2241em;vertical-align:-0.2861em;">



</span>

<span className="mopen">

[

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
<span className="mord,mathnormal,mtight">

p

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

<span className="mopen">

(

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
<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

q

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.2222em;">

V

</span>

<span className="mord,mtight">

/

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

1

</span>

<span className="mclose">

)]

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
<span className="strut" style="height:2.1574em;vertical-align:-0.836em;">



</span>

<span className="mopen">

(

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
<span className="mord,mathnormal,mtight">

n

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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

<span className="mclose">

)

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
<span className="mopen,mtight">

(

</span>

<span className="mord,mtight">

−

</span>

<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

x

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1645em;">
<span style="top:-2.357em;margin-left:0em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
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
<span className="vlist" style="height:0.2819em;">
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
<span className="mord,mathnormal,mtight">

x

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3448em;">
<span style="top:-2.3567em;margin-left:0em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
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
<span className="vlist" style="height:0.1433em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>

<span className="mclose,mtight">

)

</span>

<span className="mord,mtight">

/

</span>

<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

L

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1645em;">
<span style="top:-2.357em;margin-left:0em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
<span className="mord,mathnormal,mtight">

n

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
<mo>

=

</mo>

<mi>

q

</mi>

<mfrac>
<msub>
<mi>

D

</mi>

<mi>

n

</mi>
</msub>

<msub>
<mi>

L

</mi>

<mi>

n

</mi>
</msub>
</mfrac>

<msub>
<mi>

n

</mi>

<mrow>
<mi>

p

</mi>

<mn>

0

</mn>
</mrow>
</msub>

<mo stretchy="false">

(

</mo>

<msup>
<mi>

e

</mi>

<mrow>
<mi>

q

</mi>

<mi>

V

</mi>

<mi mathvariant="normal">

/

</mi>

<mi>

k

</mi>

<mi>

T

</mi>
</mrow>
</msup>

<mo>

−

</mo>

<mn>

1

</mn>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

= q \frac{D_n}{L_n} n_{p0} (e^{qV/kT}-1)

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
<span className="strut" style="height:2.1963em;vertical-align:-0.836em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

q

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
<span className="mord,mathnormal,mtight">

n

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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
<span className="mord,mathnormal" style="margin-right:0.0278em;">

D

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0278em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

n

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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
<span className="mord,mathnormal,mtight">

p

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

<span className="mopen">

(

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
<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

q

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.2222em;">

V

</span>

<span className="mord,mtight">

/

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

1

</span>

<span className="mclose">

)

</span>
</span>
</span>
</span>
</span>

#### 总电流与最终形式

将两者相加，得到理想二极管方程：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

J

</mi>

<mo>

=

</mo>

<mrow>
<mo fence="true">

(

</mo>

<mi>

q

</mi>

<mfrac>
<msub>
<mi>

D

</mi>

<mi>

p

</mi>
</msub>

<msub>
<mi>

L

</mi>

<mi>

p

</mi>
</msub>
</mfrac>

<msub>
<mi>

p

</mi>

<mrow>
<mi>

n

</mi>

<mn>

0

</mn>
</mrow>
</msub>

<mo>

+

</mo>

<mi>

q

</mi>

<mfrac>
<msub>
<mi>

D

</mi>

<mi>

n

</mi>
</msub>

<msub>
<mi>

L

</mi>

<mi>

n

</mi>
</msub>
</mfrac>

<msub>
<mi>

n

</mi>

<mrow>
<mi>

p

</mi>

<mn>

0

</mn>
</mrow>
</msub>

<mo fence="true">

)

</mo>
</mrow>

<mo stretchy="false">

(

</mo>

<msup>
<mi>

e

</mi>

<mrow>
<mi>

q

</mi>

<mi>

V

</mi>

<mi mathvariant="normal">

/

</mi>

<mi>

k

</mi>

<mi>

T

</mi>
</mrow>
</msup>

<mo>

−

</mo>

<mn>

1

</mn>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

J = \left( q \frac{D_p}{L_p} p_{n0} + q \frac{D_n}{L_n} n_{p0} \right) (e^{qV/kT}-1)

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0962em;">

J

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



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

<span className="mord,mathnormal" style="margin-right:0.0359em;">

q

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

D

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0278em;margin-right:0.05em;">
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
<span className="mord,mathnormal">

p

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
<span className="mord,mathnormal,mtight">

n

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

<span className="mord,mathnormal" style="margin-right:0.0359em;">

q

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
<span className="mord,mathnormal,mtight">

n

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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
<span className="mord,mathnormal" style="margin-right:0.0278em;">

D

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0278em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

n

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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
<span className="mord,mathnormal,mtight">

p

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

<span className="mclose,delimcenter" style="top:0em;">
<span className="delimsizing,size3">

)

</span>
</span>
</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mopen">

(

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
<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

q

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.2222em;">

V

</span>

<span className="mord,mtight">

/

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

1

</span>

<span className="mclose">

)

</span>
</span>
</span>
</span>
</span>

定义反向饱和电流密度 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

J

</mi>

<mn>

0

</mn>
</msub>
</mrow>

<annotation encoding="application/x-tex">

J_0

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0962em;">

J

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0962em;margin-right:0.05em;">
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

：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<msub>
<mi>

J

</mi>

<mn>

0

</mn>
</msub>

<mo>

=

</mo>

<mi>

q

</mi>

<msubsup>
<mi>

n

</mi>

<mi>

i

</mi>

<mn>

2

</mn>
</msubsup>

<mrow>
<mo fence="true">

(

</mo>

<mfrac>
<msub>
<mi>

D

</mi>

<mi>

p

</mi>
</msub>

<mrow>
<msub>
<mi>

L

</mi>

<mi>

p

</mi>
</msub>

<msub>
<mi>

N

</mi>

<mi>

D

</mi>
</msub>
</mrow>
</mfrac>

<mo>

+

</mo>

<mfrac>
<msub>
<mi>

D

</mi>

<mi>

n

</mi>
</msub>

<mrow>
<msub>
<mi>

L

</mi>

<mi>

n

</mi>
</msub>

<msub>
<mi>

N

</mi>

<mi>

A

</mi>
</msub>
</mrow>
</mfrac>

<mo fence="true">

)

</mo>
</mrow>
</mrow>

<annotation encoding="application/x-tex">

J_0 = q n_i^2 \left( \frac{D_p}{L_p N_D} + \frac{D_n}{L_n N_A} \right)

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0962em;">

J

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0962em;margin-right:0.05em;">
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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:2.4221em;vertical-align:-0.9721em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

q

</span>

<span className="mord">
<span className="mord,mathnormal">

n

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.8641em;">
<span style="top:-2.453em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

i

</span>
</span>
</span>

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

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.247em;">
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

D

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0278em;margin-right:0.05em;">
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
<span className="mord,mathnormal,mtight">

n

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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

D

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0278em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

n

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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

最终形式：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

J

</mi>

<mo>

=

</mo>

<msub>
<mi>

J

</mi>

<mn>

0

</mn>
</msub>

<mo stretchy="false">

(

</mo>

<msup>
<mi>

e

</mi>

<mrow>
<mi>

q

</mi>

<mi>

V

</mi>

<mi mathvariant="normal">

/

</mi>

<mi>

k

</mi>

<mi>

T

</mi>
</mrow>
</msup>

<mo>

−

</mo>

<mn>

1

</mn>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

J = J_0 (e^{qV/kT}-1)

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0962em;">

J

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.138em;vertical-align:-0.25em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0962em;">

J

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0962em;margin-right:0.05em;">
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

<span className="mopen">

(

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
<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

q

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.2222em;">

V

</span>

<span className="mord,mtight">

/

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

1

</span>

<span className="mclose">

)

</span>
</span>
</span>
</span>

。

---

### 问题一则

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture6-17.webp)

主要原因还是因为<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msubsup>
<mi>

n

</mi>

<mi>

i

</mi>

<mn>

2

</mn>
</msubsup>
</mrow>

<annotation encoding="application/x-tex">

n_i^2

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.0728em;vertical-align:-0.2587em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

n

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.8141em;">
<span style="top:-2.4413em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

i

</span>
</span>
</span>

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

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.2587em;">
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

随温度暴增

<mark>

**简单而言：**

</mark>

 <mark>

温度升高

</mark>

 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mtext>



</mtext>

<mo>

⟹

</mo>

<mtext>



</mtext>

<msubsup>
<mi>

n

</mi>

<mi>

i

</mi>

<mn>

2

</mn>
</msubsup>
</mrow>

<annotation encoding="application/x-tex">

\implies n_i^2

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.549em;vertical-align:-0.024em;">



</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

⟹

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.0728em;vertical-align:-0.2587em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

n

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.8141em;">
<span style="top:-2.4413em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

i

</span>
</span>
</span>

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

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.2587em;">
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

 <mark>

暴增

</mark>

 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mtext>



</mtext>

<mo>

⟹

</mo>

<mtext>



</mtext>

<msub>
<mi>

I

</mi>

<mn>

0

</mn>
</msub>
</mrow>

<annotation encoding="application/x-tex">

\implies I_0

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.549em;vertical-align:-0.024em;">



</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

⟹

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mspace" style="margin-right:0.2778em;">



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
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0785em;margin-right:0.05em;">
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

 <mark>

暴增。

</mark>

    <mark>

为了维持相同的电流

</mark>

 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

I

</mi>
</mrow>

<annotation encoding="application/x-tex">

I

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0785em;">

I

</span>
</span>
</span>
</span>

<mark>

，电压

</mark>

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

A

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

V_A

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

 <mark>

必须降低来抵消

</mark>

 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

I

</mi>

<mn>

0

</mn>
</msub>
</mrow>

<annotation encoding="application/x-tex">

I_0

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
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0785em;margin-right:0.05em;">
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

 <mark>

的暴增。

</mark>



## 七、实际二极管（耗尽区载流子的产生和复合）（P28）

在上述理想晶体管I-V特性中，我们有一个最重要的假设

> <mark>
> 
> **最关键假设：**
> 
> </mark>
> 
>  <mark>
> 
> 耗尽层（SCR）中没有载流子的产生或复合 (R-G=0)
> 
> </mark>

但这个假设仅在正向电压较大时成立。<mark>

因为当正向电压较小或者是在反向偏压时，耗尽区中的载流子的产生和复合产生的电流与中性区中产生的电流数量级相当，不应当忽略。

</mark>



![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture6-18.webp)

**正向**

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture6-19.webp)

注意120mV/dec的斜率小于60mV/dec

**反向**

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture6-20.webp)

## 八、扩散电容（P29-30）

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 50.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture6-21.webp" />
      </p>
    </td>
    
    
      <td style="width: 49.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture6-22.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

**实质：**

当P-N结正向偏置时，电子从N区注入P区（空穴从P区注入N区）。这些被注入的少数载流子（如图中P-side的电子浓度曲线）并不会立即消失，它们会在中性区扩散，并在一段时间 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

τ

</mi>

<mi>

s

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

\tau_s

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.5806em;vertical-align:-0.15em;">



</span>

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

（少数载流子寿命/电荷存储时间）后才与多数载流子复合。

**主要公式：**

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture6-23.webp)

### 问题一则

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture6-24.webp)

- **耗尽电容（结电容）：** 是P-N结耗尽区（空间电荷区）本身形成的物理电容，它在**反向偏置**时占主导地位，并且随着耗尽层增大而**减小**。
- **扩散电容（存储电容）：** 是由电荷存储效应引起的，它**只在正向偏置时**出现，并且随着正向电流 <span className="katex">
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

C

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

I_{DC}

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

<span className="mord,mathnormal,mtight" style="margin-right:0.0715em;">

C

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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

 增大而**增大**。
- **结论：**
  - **正偏：两种电容均存在，且随着正向偏压增大，俩电容均增大，强正向偏置下（例如** <span className="katex">
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
  
  C
  
  </mi>
  </mrow>
  </msub>
  
  <mo>
  
  =
  
  </mo>
  
  <mn>
  
  1
  
  </mn>
  
  <mtext>
  
  mA
  
  </mtext>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  I_{DC} = 1 \text{ mA}
  
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
  
  <span className="mord,mathnormal,mtight" style="margin-right:0.0715em;">
  
  C
  
  </span>
  </span>
  </span>
  </span>
  </span>
  
  <span className="vlist-s">
  
  ​
  
  </span>
  </span>
  
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
  
  1
  
  </span>
  
  <span className="mord,text">
  <span className="mord">
  
  mA
  
  </span>
  </span>
  </span>
  </span>
  </span>
  
  **），扩散电容远远大于耗尽电容。**
  - **反偏：扩散电容为零，只有耗尽电容。并且随着反向偏压增大而减小。**

## 九、附录

### 缩写 (Abbreviations)

<table>
<thead>
  <tr>
    <th>
      缩写
    </th>
    
    <th>
      中文含义
    </th>
    
    <th>
      英文含义
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      <span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <mi mathvariant="script">
                  E
                </mi>
                
                <mo stretchy="false">
                  (
                </mo>
                
                <mn>
                  0
                </mn>
                
                <mo stretchy="false">
                  )
                </mo>
              </mrow>
              
              <annotation encoding="application/x-tex">
                \mathcal{E}(0)
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:1em;vertical-align:-0.25em;">
              
            </span>
            
            <span className="mord,mathcal" style="margin-right:0.0894em;">
              E
            </span>
            
            <span className="mopen">
              (
            </span>
            
            <span className="mord">
              0
            </span>
            
            <span className="mclose">
              )
            </span>
          </span>
        </span>
      </span>
      
      <br />
    </td>
    
    <td>
      峰值电场
    </td>
    
    <td>
      Peak Electric Field
    </td>
  </tr>
  
  <tr>
    <td>
      <span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <mi>
                  W
                </mi>
              </mrow>
              
              <annotation encoding="application/x-tex">
                W
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:0.6833em;">
              
            </span>
            
            <span className="mord,mathnormal" style="margin-right:0.1389em;">
              W
            </span>
          </span>
        </span>
      </span>
      
      <br />
    </td>
    
    <td>
      耗尽层宽度
    </td>
    
    <td>
      Depletion Layer Width
    </td>
  </tr>
  
  <tr>
    <td>
      <span className="katex">
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
                  </mrow>
                </msub>
              </mrow>
              
              <annotation encoding="application/x-tex">
                V_{bi}
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
                              bi
                            </span>
                          </span>
                        </span>
                      </span>
                    </span>
                    
                    <span className="vlist-s">
                      ​
                    </span>
                  </span>
                  
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
    </td>
    
    <td>
      内建电势
    </td>
    
    <td>
      Built-in Potential
    </td>
  </tr>
  
  <tr>
    <td>
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
                    A
                  </mi>
                </msub>
              </mrow>
              
              <annotation encoding="application/x-tex">
                V_A
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
      
      <br />
    </td>
    
    <td>
      外加偏压
    </td>
    
    <td>
      Applied Voltage
    </td>
  </tr>
  
  <tr>
    <td>
      <span className="katex">
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
                
                <mo separator="true">
                  ,
                </mo>
                
                <msub>
                  <mi>
                    N
                  </mi>
                  
                  <mi>
                    D
                  </mi>
                </msub>
              </mrow>
              
              <annotation encoding="application/x-tex">
                N_A, N_D
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:0.8778em;vertical-align:-0.1944em;">
              
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
            
            <span className="mpunct">
              ,
            </span>
            
            <span className="mspace" style="margin-right:0.1667em;">
              
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
    </td>
    
    <td>
      受主、施主浓度
    </td>
    
    <td>
      Acceptor, Donor Concentration
    </td>
  </tr>
  
  <tr>
    <td>
      <span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <msub>
                  <mi>
                    ϵ
                  </mi>
                  
                  <mi>
                    s
                  </mi>
                </msub>
              </mrow>
              
              <annotation encoding="application/x-tex">
                \epsilon_s
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:0.5806em;vertical-align:-0.15em;">
              
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal">
                ϵ
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
      
      <br />
    </td>
    
    <td>
      半导体介电常数
    </td>
    
    <td>
      Semiconductor Permittivity
    </td>
  </tr>
  
  <tr>
    <td>
      <span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <msub>
                  <mi>
                    E
                  </mi>
                  
                  <mi>
                    c
                  </mi>
                </msub>
                
                <mo separator="true">
                  ,
                </mo>
                
                <msub>
                  <mi>
                    E
                  </mi>
                  
                  <mi>
                    v
                  </mi>
                </msub>
              </mrow>
              
              <annotation encoding="application/x-tex">
                E_c, E_v
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:0.8778em;vertical-align:-0.1944em;">
              
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
                            c
                          </span>
                        </span>
                      </span>
                    </span>
                    
                    <span className="vlist-s">
                      ​
                    </span>
                  </span>
                  
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
                          <span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">
                            v
                          </span>
                        </span>
                      </span>
                    </span>
                    
                    <span className="vlist-s">
                      ​
                    </span>
                  </span>
                  
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
    </td>
    
    <td>
      导带底, 价带顶
    </td>
    
    <td>
      Conduction, Valence Band Edge
    </td>
  </tr>
  
  <tr>
    <td>
      <span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <msub>
                  <mi>
                    E
                  </mi>
                  
                  <mi>
                    F
                  </mi>
                </msub>
              </mrow>
              
              <annotation encoding="application/x-tex">
                E_F
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
                    <span className="vlist" style="height:0.3283em;">
                      <span style="top:-2.55em;margin-left:-0.0576em;margin-right:0.05em;">
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
      
      <br />
    </td>
    
    <td>
      费米能级
    </td>
    
    <td>
      Fermi Level
    </td>
  </tr>
  
  <tr>
    <td>
      <span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <msub>
                  <mi>
                    E
                  </mi>
                  
                  <mrow>
                    <mi>
                      F
                    </mi>
                    
                    <mi>
                      n
                    </mi>
                  </mrow>
                </msub>
                
                <mo separator="true">
                  ,
                </mo>
                
                <msub>
                  <mi>
                    E
                  </mi>
                  
                  <mrow>
                    <mi>
                      F
                    </mi>
                    
                    <mi>
                      p
                    </mi>
                  </mrow>
                </msub>
              </mrow>
              
              <annotation encoding="application/x-tex">
                E_{Fn}, E_{Fp}
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:0.9694em;vertical-align:-0.2861em;">
              
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal" style="margin-right:0.0576em;">
                E
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.3283em;">
                      <span style="top:-2.55em;margin-left:-0.0576em;margin-right:0.05em;">
                        <span className="pstrut" style="height:2.7em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mtight">
                            <span className="mord,mathnormal,mtight" style="margin-right:0.1389em;">
                              F
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
            
            <span className="mpunct">
              ,
            </span>
            
            <span className="mspace" style="margin-right:0.1667em;">
              
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal" style="margin-right:0.0576em;">
                E
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.3283em;">
                      <span style="top:-2.55em;margin-left:-0.0576em;margin-right:0.05em;">
                        <span className="pstrut" style="height:2.7em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mtight">
                            <span className="mord,mathnormal,mtight" style="margin-right:0.1389em;">
                              F
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
      
      <br />
    </td>
    
    <td>
      电子、空穴准费米能级
    </td>
    
    <td>
      Electron, Hole Quasi-Fermi Level
    </td>
  </tr>
  
  <tr>
    <td>
      <span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <msub>
                  <mi>
                    n
                  </mi>
                  
                  <mi>
                    i
                  </mi>
                </msub>
              </mrow>
              
              <annotation encoding="application/x-tex">
                n_i
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:0.5806em;vertical-align:-0.15em;">
              
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal">
                n
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
      </span>
      
      <br />
    </td>
    
    <td>
      本征载流子浓度
    </td>
    
    <td>
      Intrinsic Carrier Concentration
    </td>
  </tr>
  
  <tr>
    <td>
      <span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <msub>
                  <mi>
                    n
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
                    p
                  </mi>
                  
                  <mn>
                    0
                  </mn>
                </msub>
              </mrow>
              
              <annotation encoding="application/x-tex">
                n_0, p_0
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:0.625em;vertical-align:-0.1944em;">
              
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
            
            <span className="mpunct">
              ,
            </span>
            
            <span className="mspace" style="margin-right:0.1667em;">
              
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal">
                p
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
      
      <br />
    </td>
    
    <td>
      平衡载流子浓度
    </td>
    
    <td>
      Equilibrium Carrier Concentration
    </td>
  </tr>
  
  <tr>
    <td>
      <span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <mi mathvariant="normal">
                  Δ
                </mi>
                
                <mi>
                  n
                </mi>
                
                <mo separator="true">
                  ,
                </mo>
                
                <mi mathvariant="normal">
                  Δ
                </mi>
                
                <mi>
                  p
                </mi>
              </mrow>
              
              <annotation encoding="application/x-tex">
                \Delta n, \Delta p
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:0.8778em;vertical-align:-0.1944em;">
              
            </span>
            
            <span className="mord">
              Δ
            </span>
            
            <span className="mord,mathnormal">
              n
            </span>
            
            <span className="mpunct">
              ,
            </span>
            
            <span className="mspace" style="margin-right:0.1667em;">
              
            </span>
            
            <span className="mord">
              Δ
            </span>
            
            <span className="mord,mathnormal">
              p
            </span>
          </span>
        </span>
      </span>
      
      <br />
    </td>
    
    <td>
      过剩载流子浓度
    </td>
    
    <td>
      Excess Carrier Concentration
    </td>
  </tr>
  
  <tr>
    <td>
      <span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <msub>
                  <mi>
                    J
                  </mi>
                  
                  <mi>
                    n
                  </mi>
                </msub>
                
                <mo separator="true">
                  ,
                </mo>
                
                <msub>
                  <mi>
                    J
                  </mi>
                  
                  <mi>
                    p
                  </mi>
                </msub>
              </mrow>
              
              <annotation encoding="application/x-tex">
                J_n, J_p
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:0.9694em;vertical-align:-0.2861em;">
              
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal" style="margin-right:0.0962em;">
                J
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.1514em;">
                      <span style="top:-2.55em;margin-left:-0.0962em;margin-right:0.05em;">
                        <span className="pstrut" style="height:2.7em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mathnormal,mtight">
                            n
                          </span>
                        </span>
                      </span>
                    </span>
                    
                    <span className="vlist-s">
                      ​
                    </span>
                  </span>
                  
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
              <span className="mord,mathnormal" style="margin-right:0.0962em;">
                J
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.1514em;">
                      <span style="top:-2.55em;margin-left:-0.0962em;margin-right:0.05em;">
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
      
      <br />
    </td>
    
    <td>
      电子、空穴电流密度
    </td>
    
    <td>
      Electron, Hole Current Density
    </td>
  </tr>
  
  <tr>
    <td>
      <span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <msub>
                  <mi>
                    D
                  </mi>
                  
                  <mi>
                    n
                  </mi>
                </msub>
                
                <mo separator="true">
                  ,
                </mo>
                
                <msub>
                  <mi>
                    D
                  </mi>
                  
                  <mi>
                    p
                  </mi>
                </msub>
              </mrow>
              
              <annotation encoding="application/x-tex">
                D_n, D_p
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:0.9694em;vertical-align:-0.2861em;">
              
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal" style="margin-right:0.0278em;">
                D
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.1514em;">
                      <span style="top:-2.55em;margin-left:-0.0278em;margin-right:0.05em;">
                        <span className="pstrut" style="height:2.7em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mathnormal,mtight">
                            n
                          </span>
                        </span>
                      </span>
                    </span>
                    
                    <span className="vlist-s">
                      ​
                    </span>
                  </span>
                  
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
              <span className="mord,mathnormal" style="margin-right:0.0278em;">
                D
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.1514em;">
                      <span style="top:-2.55em;margin-left:-0.0278em;margin-right:0.05em;">
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
      
      <br />
    </td>
    
    <td>
      电子、空穴扩散系数
    </td>
    
    <td>
      Electron, Hole Diffusion Coefficient
    </td>
  </tr>
  
  <tr>
    <td>
      <span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <msub>
                  <mi>
                    τ
                  </mi>
                  
                  <mi>
                    n
                  </mi>
                </msub>
                
                <mo separator="true">
                  ,
                </mo>
                
                <msub>
                  <mi>
                    τ
                  </mi>
                  
                  <mi>
                    p
                  </mi>
                </msub>
              </mrow>
              
              <annotation encoding="application/x-tex">
                \tau_n, \tau_p
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:0.7167em;vertical-align:-0.2861em;">
              
            </span>
            
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
                          <span className="mord,mathnormal,mtight">
                            n
                          </span>
                        </span>
                      </span>
                    </span>
                    
                    <span className="vlist-s">
                      ​
                    </span>
                  </span>
                  
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
      
      <br />
    </td>
    
    <td>
      电子、空穴（少数载流子）寿命
    </td>
    
    <td>
      Electron, Hole (Minority Carrier) Lifetime
    </td>
  </tr>
  
  <tr>
    <td>
      <span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <msub>
                  <mi>
                    L
                  </mi>
                  
                  <mi>
                    n
                  </mi>
                </msub>
                
                <mo separator="true">
                  ,
                </mo>
                
                <msub>
                  <mi>
                    L
                  </mi>
                  
                  <mi>
                    p
                  </mi>
                </msub>
              </mrow>
              
              <annotation encoding="application/x-tex">
                L_n, L_p
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
                          <span className="mord,mathnormal,mtight">
                            n
                          </span>
                        </span>
                      </span>
                    </span>
                    
                    <span className="vlist-s">
                      ​
                    </span>
                  </span>
                  
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
      
      <br />
    </td>
    
    <td>
      电子、空穴扩散长度
    </td>
    
    <td>
      Electron, Hole Diffusion Length
    </td>
  </tr>
  
  <tr>
    <td>
      SCR
    </td>
    
    <td>
      空间电荷区 (即耗尽区)
    </td>
    
    <td>
      Space-Charge Region
    </td>
  </tr>
  
  <tr>
    <td>
      <span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <mi>
                  Q
                </mi>
              </mrow>
              
              <annotation encoding="application/x-tex">
                Q
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:0.8778em;vertical-align:-0.1944em;">
              
            </span>
            
            <span className="mord,mathnormal">
              Q
            </span>
          </span>
        </span>
      </span>
      
      <br />
    </td>
    
    <td>
      存储电荷
    </td>
    
    <td>
      Stored Charge
    </td>
  </tr>
  
  <tr>
    <td>
      <span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <msub>
                  <mi>
                    τ
                  </mi>
                  
                  <mi>
                    s
                  </mi>
                </msub>
              </mrow>
              
              <annotation encoding="application/x-tex">
                \tau_s
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:0.5806em;vertical-align:-0.15em;">
              
            </span>
            
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
      
      <br />
    </td>
    
    <td>
      电荷存储时间
    </td>
    
    <td>
      Charge-Storage Time
    </td>
  </tr>
  
  <tr>
    <td>
      <span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <mi>
                  G
                </mi>
                
                <mo separator="true">
                  ,
                </mo>
                
                <mi>
                  C
                </mi>
              </mrow>
              
              <annotation encoding="application/x-tex">
                G, C
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:0.8778em;vertical-align:-0.1944em;">
              
            </span>
            
            <span className="mord,mathnormal">
              G
            </span>
            
            <span className="mpunct">
              ,
            </span>
            
            <span className="mspace" style="margin-right:0.1667em;">
              
            </span>
            
            <span className="mord,mathnormal" style="margin-right:0.0715em;">
              C
            </span>
          </span>
        </span>
      </span>
      
      <br />
    </td>
    
    <td>
      （小信号）电导，电容
    </td>
    
    <td>
      (Small-signal) Conductance, Capacitance
    </td>
  </tr>
</tbody>
</table>

### 核心公式 (Formulas)

#### 峰值电场 (单边结)

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi mathvariant="script">

E

</mi>

<mo stretchy="false">

(

</mo>

<mn>

0

</mn>

<mo stretchy="false">

)

</mo>

<mo>

≅

</mo>

<msqrt>
<mfrac>
<mrow>
<mn>

2

</mn>

<mi>

q

</mi>

<mi>

N

</mi>

<mo stretchy="false">

(

</mo>

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

A

</mi>
</msub>

<mo stretchy="false">

)

</mo>
</mrow>

<msub>
<mi>

ϵ

</mi>

<mi>

s

</mi>
</msub>
</mfrac>
</msqrt>
</mrow>

<annotation encoding="application/x-tex">

\mathcal{E}(0) \cong \sqrt{\frac{2qN(V_{bi}-V_{A})}{\epsilon_s}}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord,mathcal" style="margin-right:0.0894em;">

E

</span>

<span className="mopen">

(

</span>

<span className="mord">

0

</span>

<span className="mclose">

)

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

≅

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:3.04em;vertical-align:-1.1106em;">



</span>

<span className="mord,sqrt">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:1.9294em;">
<span className="svg-align" style="top:-5em;">
<span className="pstrut" style="height:5em;">



</span>

<span className="mord" style="padding-left:1em;">
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
<span className="mord,mathnormal">

ϵ

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

<span className="mord,mathnormal" style="margin-right:0.0359em;">

q

</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

N

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

bi

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

A

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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

<span style="top:-3.8894em;">
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
<span className="vlist" style="height:1.1106em;">
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

适用条件： 突变单边结，耗尽层近似。

#### 结定律

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

p

</mi>

<mi>

n

</mi>

<mo>

=

</mo>

<msubsup>
<mi>

n

</mi>

<mi>

i

</mi>

<mn>

2

</mn>
</msubsup>

<msup>
<mi>

e

</mi>

<mrow>
<mi>

q

</mi>

<msub>
<mi>

V

</mi>

<mi>

A

</mi>
</msub>

<mi mathvariant="normal">

/

</mi>

<mi>

k

</mi>

<mi>

T

</mi>
</mrow>
</msup>
</mrow>

<annotation encoding="application/x-tex">

pn = n_i^2 e^{qV_A/kT}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.625em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal">

p

</span>

<span className="mord,mathnormal">

n

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.185em;vertical-align:-0.247em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

n

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.8641em;">
<span style="top:-2.453em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

i

</span>
</span>
</span>

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

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.247em;">
<span>



</span>
</span>
</span>
</span>
</span>
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
<span style="top:-2.3567em;margin-left:-0.2222em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
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
<span className="vlist" style="height:0.1433em;">
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
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

适用条件： 适用于耗尽层边界，准平衡假设。

#### 边界过剩载流子浓度

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

p

</mi>

<mi>

n

</mi>
</msub>

<mo stretchy="false">

(

</mo>

<msub>
<mi>

x

</mi>

<mi>

n

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

p

</mi>

<mrow>
<mi>

n

</mi>

<mn>

0

</mn>
</mrow>
</msub>

<mo stretchy="false">

(

</mo>

<msup>
<mi>

e

</mi>

<mrow>
<mi>

q

</mi>

<msub>
<mi>

V

</mi>

<mi>

A

</mi>
</msub>

<mi mathvariant="normal">

/

</mi>

<mi>

k

</mi>

<mi>

T

</mi>
</mrow>
</msup>

<mo>

−

</mo>

<mn>

1

</mn>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

\Delta p_n(x_n) = p_{n0}(e^{qV_A/kT} - 1)

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord">

Δ

</span>

<span className="mord">
<span className="mord,mathnormal">

p

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

n

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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
<span className="mord,mathnormal">

x

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

n

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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
<span className="strut" style="height:1.188em;vertical-align:-0.25em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

p

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
<span className="mord,mathnormal,mtight">

n

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

<span className="mopen">

(

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
<span style="top:-2.3567em;margin-left:-0.2222em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
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
<span className="vlist" style="height:0.1433em;">
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

1

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
<mi mathvariant="normal">

Δ

</mi>

<msub>
<mi>

n

</mi>

<mi>

p

</mi>
</msub>

<mo stretchy="false">

(

</mo>

<mo>

−

</mo>

<msub>
<mi>

x

</mi>

<mi>

p

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

n

</mi>

<mrow>
<mi>

p

</mi>

<mn>

0

</mn>
</mrow>
</msub>

<mo stretchy="false">

(

</mo>

<msup>
<mi>

e

</mi>

<mrow>
<mi>

q

</mi>

<msub>
<mi>

V

</mi>

<mi>

A

</mi>
</msub>

<mi mathvariant="normal">

/

</mi>

<mi>

k

</mi>

<mi>

T

</mi>
</mrow>
</msup>

<mo>

−

</mo>

<mn>

1

</mn>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

\Delta n_p(-x_p) = n_{p0}(e^{qV_A/kT} - 1)

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.0361em;vertical-align:-0.2861em;">



</span>

<span className="mord">

Δ

</span>

<span className="mord">
<span className="mord,mathnormal">

n

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

<span className="mopen">

(

</span>

<span className="mord">

−

</span>

<span className="mord">
<span className="mord,mathnormal">

x

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
<span className="strut" style="height:1.2241em;vertical-align:-0.2861em;">



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
<span className="mord,mathnormal,mtight">

p

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

<span className="mopen">

(

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
<span style="top:-2.3567em;margin-left:-0.2222em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
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
<span className="vlist" style="height:0.1433em;">
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

1

</span>

<span className="mclose">

)

</span>
</span>
</span>
</span>
</span>

适用条件： 耗尽层边界，低水平注入。

#### 稳态连续性方程

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mo>

−

</mo>

<mfrac>
<mrow>
<mi>

d

</mi>

<msub>
<mi>

J

</mi>

<mi>

p

</mi>
</msub>
</mrow>

<mrow>
<mi>

d

</mi>

<mi>

x

</mi>
</mrow>
</mfrac>

<mo>

=

</mo>

<mi>

q

</mi>

<mfrac>
<mrow>
<mi mathvariant="normal">

Δ

</mi>

<mi>

p

</mi>
</mrow>

<msub>
<mi>

τ

</mi>

<mi>

p

</mi>
</msub>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

-\frac{dJ_p}{dx} = q \frac{\Delta p}{\tau_p}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:2.0574em;vertical-align:-0.686em;">



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
<span className="vlist" style="height:1.3714em;">
<span style="top:-2.314em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal">

x

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

d

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0962em;">

J

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0962em;margin-right:0.05em;">
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
<span className="strut" style="height:2.3324em;vertical-align:-0.9721em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

q

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

Δ

</span>

<span className="mord,mathnormal">

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

适用条件： 仅考虑复合（无光照），稳态。

#### 少数载流子扩散方程

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mfrac>
<mrow>
<msup>
<mi>

d

</mi>

<mn>

2

</mn>
</msup>

<mi mathvariant="normal">

Δ

</mi>

<mi>

p

</mi>
</mrow>

<mrow>
<mi>

d

</mi>

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

<mo>

=

</mo>

<mfrac>
<mrow>
<mi mathvariant="normal">

Δ

</mi>

<mi>

p

</mi>
</mrow>

<msubsup>
<mi>

L

</mi>

<mi>

p

</mi>

<mn>

2

</mn>
</msubsup>
</mfrac>

<mspace width="1em">



</mspace>

<mtext>

其中

</mtext>

<msub>
<mi>

L

</mi>

<mi>

p

</mi>
</msub>

<mo>

=

</mo>

<msqrt>
<mrow>
<msub>
<mi>

D

</mi>

<mi>

p

</mi>
</msub>

<msub>
<mi>

τ

</mi>

<mi>

p

</mi>
</msub>
</mrow>
</msqrt>
</mrow>

<annotation encoding="application/x-tex">

\frac{d^2\Delta p}{dx^2} = \frac{\Delta p}{L_p^2} \quad \text{其中 } L_p = \sqrt{D_p \tau_p}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
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
<span className="mord,mathnormal">

d

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
<span className="mord,mathnormal">

d

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

<span className="mord">

Δ

</span>

<span className="mord,mathnormal">

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
<span className="strut" style="height:2.4294em;vertical-align:-1.0691em;">



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

L

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.7401em;">
<span style="top:-2.453em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

p

</span>
</span>
</span>

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

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.3831em;">
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

Δ

</span>

<span className="mord,mathnormal">

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
<span className="vlist" style="height:1.0691em;">
<span>



</span>
</span>
</span>
</span>
</span>

<span className="mclose,nulldelimiter">



</span>
</span>

<span className="mspace" style="margin-right:1em;">



</span>

<span className="mord,text">
<span className="mord,cjk_fallback">

其中

</span>

<span className="mord">



</span>
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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.24em;vertical-align:-0.3075em;">



</span>

<span className="mord,sqrt">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.9325em;">
<span className="svg-align" style="top:-3.2em;">
<span className="pstrut" style="height:3.2em;">



</span>

<span className="mord" style="padding-left:1em;">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

D

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0278em;margin-right:0.05em;">
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

适用条件： 准中性区，低水平注入，稳态，无光照，均匀掺杂。

#### 理想二极管方程

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

J

</mi>

<mo>

=

</mo>

<msub>
<mi>

J

</mi>

<mn>

0

</mn>
</msub>

<mo stretchy="false">

(

</mo>

<msup>
<mi>

e

</mi>

<mrow>
<mi>

q

</mi>

<msub>
<mi>

V

</mi>

<mi>

A

</mi>
</msub>

<mi mathvariant="normal">

/

</mi>

<mi>

k

</mi>

<mi>

T

</mi>
</mrow>
</msup>

<mo>

−

</mo>

<mn>

1

</mn>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

J = J_0 (e^{qV_A/kT}-1)

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0962em;">

J

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.188em;vertical-align:-0.25em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0962em;">

J

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0962em;margin-right:0.05em;">
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

<span className="mopen">

(

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
<span style="top:-2.3567em;margin-left:-0.2222em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
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
<span className="vlist" style="height:0.1433em;">
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

1

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

J

</mi>

<mn>

0

</mn>
</msub>

<mo>

=

</mo>

<mi>

q

</mi>

<msubsup>
<mi>

n

</mi>

<mi>

i

</mi>

<mn>

2

</mn>
</msubsup>

<mrow>
<mo fence="true">

(

</mo>

<mfrac>
<msub>
<mi>

D

</mi>

<mi>

p

</mi>
</msub>

<mrow>
<msub>
<mi>

L

</mi>

<mi>

p

</mi>
</msub>

<msub>
<mi>

N

</mi>

<mi>

D

</mi>
</msub>
</mrow>
</mfrac>

<mo>

+

</mo>

<mfrac>
<msub>
<mi>

D

</mi>

<mi>

n

</mi>
</msub>

<mrow>
<msub>
<mi>

L

</mi>

<mi>

n

</mi>
</msub>

<msub>
<mi>

N

</mi>

<mi>

A

</mi>
</msub>
</mrow>
</mfrac>

<mo fence="true">

)

</mo>
</mrow>
</mrow>

<annotation encoding="application/x-tex">

J_0 = q n_i^2 \left( \frac{D_p}{L_p N_D} + \frac{D_n}{L_n N_A} \right)

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0962em;">

J

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0962em;margin-right:0.05em;">
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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:2.4221em;vertical-align:-0.9721em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

q

</span>

<span className="mord">
<span className="mord,mathnormal">

n

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.8641em;">
<span style="top:-2.453em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

i

</span>
</span>
</span>

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

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.247em;">
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

D

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0278em;margin-right:0.05em;">
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
<span className="mord,mathnormal,mtight">

n

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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

D

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0278em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

n

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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

适用条件： 理想二极管假设（特别是无 SCR 复合）。

#### SCR（空间电荷区）电流

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

S

</mi>

<mi>

C

</mi>

<mi>

R

</mi>
</mrow>
</msub>

<mo>

=

</mo>

<msub>
<mi>

I

</mi>

<mrow>
<mi>

S

</mi>

<mi>

C

</mi>

<mi>

R

</mi>

<mn>

0

</mn>
</mrow>
</msub>

<mo stretchy="false">

(

</mo>

<msup>
<mi>

e

</mi>

<mrow>
<mi>

q

</mi>

<msub>
<mi>

V

</mi>

<mi>

A

</mi>
</msub>

<mi mathvariant="normal">

/

</mi>

<mn>

2

</mn>

<mi>

k

</mi>

<mi>

T

</mi>
</mrow>
</msup>

<mo>

−

</mo>

<mn>

1

</mn>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

I_{SCR} = I_{SCR0} (e^{qV_A/2kT}-1)

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
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

S

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0715em;">

C

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0077em;">

R

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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
<span className="strut" style="height:1.188em;vertical-align:-0.25em;">



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
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

S

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0715em;">

C

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0077em;">

R

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

<span className="mopen">

(

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
<span style="top:-2.3567em;margin-left:-0.2222em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
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
<span className="vlist" style="height:0.1433em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>

<span className="mord,mtight">

/2

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

1

</span>

<span className="mclose">

)

</span>
</span>
</span>
</span>
</span>

适用条件： 修正理想模型，考虑了耗尽区的复合（正偏）或产生（反偏）。

#### 电荷存储

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

I

</mi>

<mo>

=

</mo>

<mi>

Q

</mi>

<mi mathvariant="normal">

/

</mi>

<msub>
<mi>

τ

</mi>

<mi>

s

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

I = Q / \tau_s

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord,mathnormal">

Q

</span>

<span className="mord">

/

</span>

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
</span>

适用条件： 正向偏置，稳态。

#### 小信号电导

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

G

</mi>

<mo>

=

</mo>

<mfrac>
<mrow>
<mi>

d

</mi>

<mi>

I

</mi>
</mrow>

<mrow>
<mi>

d

</mi>

<mi>

V

</mi>
</mrow>
</mfrac>

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

C

</mi>
</mrow>
</msub>

<mrow>
<mi>

k

</mi>

<mi>

T

</mi>

<mi mathvariant="normal">

/

</mi>

<mi>

q

</mi>
</mrow>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

G = \frac{dI}{dV} = \frac{I_{DC}}{kT/q}

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
<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal" style="margin-right:0.2222em;">

V

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

d

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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

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
<span className="mord,mathnormal" style="margin-right:0.0315em;">

k

</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

T

</span>

<span className="mord">

/

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

q

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

<span className="mord,mathnormal,mtight" style="margin-right:0.0715em;">

C

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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

适用条件： 正向偏置远大于 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

k

</mi>

<mi>

T

</mi>

<mi mathvariant="normal">

/

</mi>

<mi>

q

</mi>
</mrow>

<annotation encoding="application/x-tex">

kT/q

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0315em;">

k

</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

T

</span>

<span className="mord">

/

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

q

</span>
</span>
</span>
</span>

，基于理想二极管模型。

#### 扩散电容

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

<mfrac>
<mrow>
<mi>

d

</mi>

<mi>

Q

</mi>
</mrow>

<mrow>
<mi>

d

</mi>

<mi>

V

</mi>
</mrow>
</mfrac>

<mo>

=

</mo>

<msub>
<mi>

τ

</mi>

<mi>

s

</mi>
</msub>

<mi>

G

</mi>

<mo>

=

</mo>

<msub>
<mi>

τ

</mi>

<mi>

s

</mi>
</msub>

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

C

</mi>
</mrow>
</msub>

<mrow>
<mi>

k

</mi>

<mi>

T

</mi>

<mi mathvariant="normal">

/

</mi>

<mi>

q

</mi>
</mrow>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

C = \frac{dQ}{dV} = \tau_s G = \tau_s \frac{I_{DC}}{kT/q}

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
<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal" style="margin-right:0.2222em;">

V

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

d

</span>

<span className="mord,mathnormal">

Q

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
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

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
<span className="strut" style="height:2.2963em;vertical-align:-0.936em;">



</span>

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
<span className="mord,mathnormal" style="margin-right:0.0315em;">

k

</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

T

</span>

<span className="mord">

/

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

q

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

<span className="mord,mathnormal,mtight" style="margin-right:0.0715em;">

C

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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

适用条件： 正向偏置，小信号。

### 专有名词 (English Terms)

<table>
<thead>
  <tr>
    <th>
      中文
    </th>
    
    <th>
      英文
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      峰值电场
    </td>
    
    <td>
      Peak Electric Field
    </td>
  </tr>
  
  <tr>
    <td>
      线性渐变结
    </td>
    
    <td>
      Linearly Graded Junction
    </td>
  </tr>
  
  <tr>
    <td>
      突变结
    </td>
    
    <td>
      Abrupt Junction (One-sided Junction)
    </td>
  </tr>
  
  <tr>
    <td>
      低水平注入
    </td>
    
    <td>
      Low-Level Injection
    </td>
  </tr>
  
  <tr>
    <td>
      准费米能级
    </td>
    
    <td>
      Quasi-Fermi Level
    </td>
  </tr>
  
  <tr>
    <td>
      结定律
    </td>
    
    <td>
      Law of the Junction
    </td>
  </tr>
  
  <tr>
    <td>
      少数载流子注入
    </td>
    
    <td>
      Minority Carrier Injection
    </td>
  </tr>
  
  <tr>
    <td>
      连续性方程
    </td>
    
    <td>
      Continuity Equation
    </td>
  </tr>
  
  <tr>
    <td>
      扩散长度
    </td>
    
    <td>
      Diffusion Length
    </td>
  </tr>
  
  <tr>
    <td>
      扩散方程
    </td>
    
    <td>
      Diffusion Equation
    </td>
  </tr>
  
  <tr>
    <td>
      理想二极管方程
    </td>
    
    <td>
      Ideal Diode Equation
    </td>
  </tr>
  
  <tr>
    <td>
      反向饱和电流
    </td>
    
    <td>
      Reverse Saturation Current
    </td>
  </tr>
  
  <tr>
    <td>
      空间电荷区 (SCR)
    </td>
    
    <td>
      Space-Charge Region (SCR)
    </td>
  </tr>
  
  <tr>
    <td>
      复合/产生
    </td>
    
    <td>
      Recombination / Generation (R-G)
    </td>
  </tr>
  
  <tr>
    <td>
      电荷存储
    </td>
    
    <td>
      Charge Storage
    </td>
  </tr>
  
  <tr>
    <td>
      小信号模型
    </td>
    
    <td>
      Small-Signal Model
    </td>
  </tr>
  
  <tr>
    <td>
      扩散电容
    </td>
    
    <td>
      Diffusion Capacitance
    </td>
  </tr>
  
  <tr>
    <td>
      耗尽层电容
    </td>
    
    <td>
      Depletion Capacitance (Junction Capacitance)
    </td>
  </tr>
</tbody>
</table>
