# Chapter 8：延迟与速度 Speed

> 门延迟的估算方法，包括 RC 模型、Elmore delay 与逻辑努力（logical effort）。

> 有很多的图，请对照课件进行复习

### 学习路线总览

建议把这个课件分成 **6 个板块** 学习，比较符合它从“定义 → 模型 → 门级 → 工具 → 逻辑努力 → 优化方法”的展开顺序。

<table>
<thead>
  <tr>
    <th>
      板块
    </th>
    
    <th>
      页码范围
    </th>
    
    <th>
      学习主题
    </th>
    
    <th>
      重点抓什么
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      1
    </td>
    
    <td>
      P2–P9
    </td>
    
    <td>
      <strong>
        延迟的基本概念与获取方法
      </strong>
    </td>
    
    <td>
      gate delay、propagation delay、contamination delay、rise/fall time、arrival time、slack，以及 SPICE / LUT / RC analytical model 的区别。课件前面明确把 propagation delay 作为最核心的 delay 概念，并引出 timing analyzer、arrival time 和 slack。
    </td>
  </tr>
  
  <tr>
    <td>
      2
    </td>
    
    <td>
      P10–P31
    </td>
    
    <td>
      <strong>
        从 CMOS 反相器理解延迟
      </strong>
    </td>
    
    <td>
      反相器 DC / transient response、NMOS/PMOS 等效电阻、寄生电容、RC delay、输入 slew、器件尺寸和 PMOS/NMOS ratio 对 delay 的影响。课件强调 analytical model 用 R 和 C 估算延迟，核心近似是 <code code="tpd ≈ RC">
        tpd ≈ RC
      </code>
      
      。
    </td>
  </tr>
  
  <tr>
    <td>
      3
    </td>
    
    <td>
      P32–P46
    </td>
    
    <td>
      <strong>
        复杂逻辑门的延迟
      </strong>
    </td>
    
    <td>
      NAND 等复杂门的等效电阻、电容、Elmore delay、contamination delay、input pattern 对延迟的影响，以及 sizing、topology、transistor ordering、buffer insertion 等加速技巧。课件总结中指出 fan-in 增大会使 delay 快速恶化，复杂门要关注 worst-case delay。
    </td>
  </tr>
  
  <tr>
    <td>
      4
    </td>
    
    <td>
      P47–P51
    </td>
    
    <td>
      <strong>
        现代标准单元中的 delay 建模
      </strong>
    </td>
    
    <td>
      standard cell、standard cell library、cell delay、input slew 和 output load 的查表关系，以及 interconnect delay。课件在这一段进入 “Standard Cell Delay in Modern Design”，并说明 cell delay/output slew 是 input slew 和 output load 的函数。
    </td>
  </tr>
  
  <tr>
    <td>
      5
    </td>
    
    <td>
      P52–P71
    </td>
    
    <td>
      <mark>
        <strong>
          Logical Effort 基础
        </strong>
      </mark>
    </td>
    
    <td>
      logical effort、electrical effort、parasitic delay、FO4、ring oscillator、多级路径 delay、branching effort。课件定义 logical effort 为“同等输出驱动能力下，某门输入电容与反相器输入电容的比值”，且复杂门 logical effort 更大。
    </td>
  </tr>
  
  <tr>
    <td>
      6
    </td>
    
    <td>
      P72–P86
    </td>
    
    <td>
      <mark>
        <strong>
          用 Logical Effort 做路径优化
        </strong>
      </mark>
    </td>
    
    <td>
      path effort <code code="F = GBH">
        F = GBH
      </code>
      
      、best number of stages、best stage effort、gate sizing、delay minimization，以及最后的公式总复习。课件给出了 logical effort 的完整方法：算 path effort、估最佳级数、加 buffer、估最小 delay、确定 stage effort、反推 gate size。
    </td>
  </tr>
</tbody>
</table>

## **一、延迟的基本概念与获取方法**

> **performance / speed / delay**

### Gate Delay —— 门延迟

从逻辑门**输入变得稳定并且有效**开始，到该逻辑门**输出变得稳定并且有效**为止，中间经历的时间就是 gate delay。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter8-Speed-01.webp)

#### Propagation Delay and Rising/Falling Time | 延时参数<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi mathvariant="bold">

t

</mi>

<mrow>
<mi mathvariant="bold">

p

</mi>

<mi mathvariant="bold">

d

</mi>

<mi mathvariant="bold">

r

</mi>
</mrow>
</msub>

<mtext mathvariant="bold">

、

</mtext>

<msub>
<mi mathvariant="bold">

t

</mi>

<mrow>
<mi mathvariant="bold">

p

</mi>

<mi mathvariant="bold">

d

</mi>

<mi mathvariant="bold">

f

</mi>
</mrow>
</msub>

<mtext mathvariant="bold">

、

</mtext>

<msub>
<mi mathvariant="bold">

t

</mi>

<mi mathvariant="bold">

p

</mi>
</msub>

<mtext mathvariant="bold">

、

</mtext>

<msub>
<mi mathvariant="bold">

t

</mi>

<mi mathvariant="bold">

r

</mi>
</msub>

<mtext mathvariant="bold">

、

</mtext>

<msub>
<mi mathvariant="bold">

t

</mi>

<mi mathvariant="bold">

f

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

\mathbf{t_{pdr}、t_{pdf}、t_p、t_r、t_f}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9722em;vertical-align:-0.2861em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord,mathbf">

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
<span className="mord,mathbf,mtight">

pdr

</span>
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

<span className="mord,mathbf,cjk_fallback">

、

</span>

<span className="mord">
<span className="mord,mathbf">

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
<span className="mord,mathbf,mtight" style="margin-right:0.109em;">

pdf

</span>
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

<span className="mord,mathbf,cjk_fallback">

、

</span>

<span className="mord">
<span className="mord,mathbf">

t

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1611em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathbf,mtight">

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

<span className="mord,mathbf,cjk_fallback">

、

</span>

<span className="mord">
<span className="mord,mathbf">

t

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1611em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathbf,mtight">

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

<span className="mord,mathbf,cjk_fallback">

、

</span>

<span className="mord">
<span className="mord,mathbf">

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
<span className="mord,mathbf,mtight" style="margin-right:0.109em;">

f

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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



![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter8-Speed-02.webp)

1. <span className="katex">
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

p

</mi>

<mi>

d

</mi>

<mi>

r

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

t_{pdr}

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

p

</span>

<span className="mord,mathnormal,mtight">

d

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

r

</span>
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

：rising propagation delay
2. <span className="katex">
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

p

</mi>

<mi>

d

</mi>

<mi>

f

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

t_{pdf}

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

p

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.1076em;">

df

</span>
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

：falling propagation delay

> <mark>
> 
> 这里的 “rising\falling” 指的是
> 
> </mark>
> 
>  <mark>
> 
> **output rising**
> 
> </mark>
> 
>    <span className="katex">
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
> D
> 
> </mi>
> </mrow>
> </msub>
> 
> <mi mathvariant="normal">
> 
> /
> 
> </mi>
> 
> <mn>
> 
> 2
> 
> </mn>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> V_{DD}/2
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
> <span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">
> 
> D
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
> <span className="mord">
> 
> /2
> 
> </span>
> </span>
> </span>
> </span>
> 
> **->**<span className="katex">
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
> D
> 
> </mi>
> </mrow>
> </msub>
> 
> <mi mathvariant="normal">
> 
> /
> 
> </mi>
> 
> <mn>
> 
> 2
> 
> </mn>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> V_{DD}/2
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
> <span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">
> 
> D
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
> <span className="mord">
> 
> /2
> 
> </span>
> </span>
> </span>
> </span>

1. <span className="katex">
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

p

</mi>

<mi>

d

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

t_{pd}

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

p

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

：平均传播延迟   <span className="katex">
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

p

</mi>

<mi>

d

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

t

</mi>

<mrow>
<mi>

p

</mi>

<mi>

d

</mi>

<mi>

r

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

p

</mi>

<mi>

d

</mi>

<mi>

f

</mi>
</mrow>
</msub>
</mrow>

<mn>

2

</mn>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

t_{pd} = \frac{t_{pdr} + t_{pdf}}{2}

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

p

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
<span className="strut" style="height:1.2886em;vertical-align:-0.345em;">



</span>

<span className="mord">
<span className="mopen,nulldelimiter">



</span>

<span className="mfrac">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.9436em;">
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

<span style="top:-3.5131em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

t

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3448em;">
<span style="top:-2.3488em;margin-left:0em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

p

</span>

<span className="mord,mathnormal,mtight">

d

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

r

</span>
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

<span className="mbin,mtight">

+

</span>

<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

t

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3448em;">
<span style="top:-2.3488em;margin-left:0em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

p

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.1076em;">

df

</span>
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

；  一般 <span className="katex">
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

p

</mi>

<mi>

d

</mi>

<mi>

r

</mi>
</mrow>
</msub>

<mo mathvariant="normal">

≠

</mo>

<msub>
<mi>

t

</mi>

<mrow>
<mi>

p

</mi>

<mi>

d

</mi>

<mi>

f

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

t_{pdr} \neq t_{pdf}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9805em;vertical-align:-0.2861em;">



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

p

</span>

<span className="mord,mathnormal,mtight">

d

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

r

</span>
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

p

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.1076em;">

df

</span>
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

p

</mi>

<mi>

d

</mi>
</mrow>
</msub>

<mo>

:

</mo>

<mtext>

输入到输出的延迟

</mtext>
</mrow>

<annotation encoding="application/x-tex">

t_{pd}: \text{输入到输出的延迟}

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

p

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

:

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,text">
<span className="mord,cjk_fallback">

输入到输出的延迟

</span>
</span>
</span>
</span>
</span>

1. <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
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

t_r

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

：rise time   常见 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mn>

0.1

</mn>

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

<mo>

→

</mo>

<mn>

0.9

</mn>

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

0.1V_{DD} \rightarrow 0.9V_{DD}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">

0.1

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

0.9

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
2. <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

t

</mi>

<mi>

f

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

t_f

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
<span className="mord,mathnormal,mtight" style="margin-right:0.1076em;">

f

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

：fall time    常见：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mn>

0.9

</mn>

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

<mo>

→

</mo>

<mn>

0.1

</mn>

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

0.9V_{DD} \rightarrow 0.1V_{DD}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">

0.9

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

0.1

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

> <span className="katex-display">
> <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
> <semantics>
> <mrow>
> <msub>
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
> t
> 
> </mi>
> 
> <mi>
> 
> f
> 
> </mi>
> </msub>
> 
> <mo>
> 
> :
> 
> </mo>
> 
> <mtext>
> 
> 输出边沿自身的陡峭程度
> 
> </mtext>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> t_r, t_f: \text{输出边沿自身的陡峭程度}
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:0.9012em;vertical-align:-0.2861em;">
> 
> 
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
> <span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">
> 
> r
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
> t
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
> <span className="mord,mathnormal,mtight" style="margin-right:0.1076em;">
> 
> f
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
> <span className="mspace" style="margin-right:0.2778em;">
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
> <span className="mord,text">
> <span className="mord,cjk_fallback">
> 
> 输出边沿自身的陡峭程度
> 
> </span>
> </span>
> </span>
> </span>
> </span>
> </span>
> 
> t_pLH 对应的是 tpdr（rise），tpdf 对应的是 t_pHL。
> 
> ![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter8-Speed-03.webp)

#### Contamination delay  |  最小延迟

> propagation delay 通常对应 **最大延迟 / max-time**。
> contamination delay 对应 **最小延迟 / min-time**。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter8-Speed-04.webp)

1. <span className="katex">
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

d

</mi>

<mi>

r

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

t_{cdr}

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

c

</span>

<span className="mord,mathnormal,mtight">

d

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

r

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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

：rising contamination delay

表示输出开始可能上升的最早时间。

1. <span className="katex">
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

d

</mi>

<mi>

f

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

t_{cdf}

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

c

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.1076em;">

df

</span>
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

：falling contamination delay

表示输出开始可能下降的最早时间。

1. <span className="katex">
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

d

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

t_{cd}

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

c

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

：平均 contamination delay

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

c

</mi>

<mi>

d

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

t

</mi>

<mrow>
<mi>

c

</mi>

<mi>

d

</mi>

<mi>

r

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

c

</mi>

<mi>

d

</mi>

<mi>

f

</mi>
</mrow>
</msub>
</mrow>

<mn>

2

</mn>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

t_{cd} = \frac{t_{cdr}+t_{cdf}}{2}

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

c

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
<span className="strut" style="height:1.9781em;vertical-align:-0.686em;">



</span>

<span className="mord">
<span className="mopen,nulldelimiter">



</span>

<span className="mfrac">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:1.2921em;">
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

c

</span>

<span className="mord,mathnormal,mtight">

d

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

r

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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

c

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.1076em;">

df

</span>
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
</span>
</span>
</span>
</span>

<alert type="tip">

**Propagation delay 是最常用的 delay。对于** <span className="katex">
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

p

</mi>

<mi>

d

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

t_{pd}

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

p

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

 **和** <span className="katex">
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

d

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

t_{cd}

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

c

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

 **来说，测量方法都是一样的：从输入跨过** <span className="katex">
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

<mi mathvariant="normal">

/

</mi>

<mn>

2

</mn>
</mrow>

<annotation encoding="application/x-tex">

V_{DD}/2

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

<span className="mord">

/2

</span>
</span>
</span>
</span>

 **开始，到输出跨过** <span className="katex">
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

<mi mathvariant="normal">

/

</mi>

<mn>

2

</mn>
</mrow>

<annotation encoding="application/x-tex">

V_{DD}/2

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

<span className="mord">

/2

</span>
</span>
</span>
</span>

 **结束。区别在于，像 NAND 门这种电路，同样是输出** <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mn>

0

</mn>

<mo>

→

</mo>

<mn>

1

</mn>
</mrow>

<annotation encoding="application/x-tex">

0\to1

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

1

</span>
</span>
</span>
</span>

 **或** <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mn>

1

</mn>

<mo>

→

</mo>

<mn>

0

</mn>
</mrow>

<annotation encoding="application/x-tex">

1\to0

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

**，不同输入端翻转、不同导通路径会导致延迟有快有慢。因此** <span className="katex">
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

p

</mi>

<mi>

d

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

t_{pd}

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

p

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

 **取最慢情况下的延迟，**<span className="katex">
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

d

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

t_{cd}

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

c

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

 **取最快情况下的延迟。**

</alert>

<table>
<thead>
  <tr>
    <th>
      名称
    </th>
    
    <th>
      含义
    </th>
    
    <th>
      用途
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      contamination delay
    </td>
    
    <td>
      输出最早可能被“污染”或开始变化的时间
    </td>
    
    <td>
      检查 hold time / min-time
    </td>
  </tr>
  
  <tr>
    <td>
      propagation delay
    </td>
    
    <td>
      输出最晚保证稳定到正确值的时间
    </td>
    
    <td>
      检查 setup time / max-time
    </td>
  </tr>
</tbody>
</table>

#### Timing analyzer ｜ 时序分析

##### Arrival time ｜ 到达时间

- Arrival time 表示：某个节点最晚什么时候会切换到正确值。

  - 如果一个门有多个输入，要等所有相关输入中最晚的那个，因为输出的正确值通常取决于最慢到达的输入。
- 公式为：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

a

</mi>

<mi>

i

</mi>
</msub>

<mo>

=

</mo>

<msub>
<mrow>
<mi>

max

</mi>

<mo>

⁡

</mo>
</mrow>

<mrow>
<mi>

j

</mi>

<mo>

∈

</mo>

<mi>

f

</mi>

<mi>

a

</mi>

<mi>

n

</mi>

<mi>

i

</mi>

<mi>

n

</mi>

<mo stretchy="false">

(

</mo>

<mi>

i

</mi>

<mo stretchy="false">

)

</mo>
</mrow>
</msub>

<mo stretchy="false">

{

</mo>

<msub>
<mi>

a

</mi>

<mi>

j

</mi>
</msub>

<mo stretchy="false">

}

</mo>

<mo>

+

</mo>

<msub>
<mi>

t

</mi>

<mrow>
<mi>

p

</mi>

<mi>

d

</mi>

<mo separator="true">

,

</mo>

<mi>

i

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

a_i = \max_{j \in fanin(i)} \{a_j\} + t_{pd,i}

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

a

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
<span className="strut" style="height:1.1052em;vertical-align:-0.3552em;">



</span>

<span className="mop">
<span className="mop">

max

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3448em;">
<span style="top:-2.5198em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0572em;">

j

</span>

<span className="mrel,mtight">

∈

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.1076em;">

f

</span>

<span className="mord,mathnormal,mtight">

anin

</span>

<span className="mopen,mtight">

(

</span>

<span className="mord,mathnormal,mtight">

i

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

<span className="mopen">

{

</span>

<span className="mord">
<span className="mord,mathnormal">

a

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

<span className="mclose">

}

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

p

</span>

<span className="mord,mathnormal,mtight">

d

</span>

<span className="mpunct,mtight">

,

</span>

<span className="mord,mathnormal,mtight">

i

</span>
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

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mtext>

所有输入 arrival time 的最大值

</mtext>

<mo>

+

</mo>

<mtext>

当前门的传播延迟

</mtext>
</mrow>

<annotation encoding="application/x-tex">

\text{所有输入 arrival time 的最大值} + \text{当前门的传播延迟}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.7778em;vertical-align:-0.0833em;">



</span>

<span className="mord,text">
<span className="mord,cjk_fallback">

所有输入

</span>

<span className="mord">

arrival time

</span>

<span className="mord,cjk_fallback">

的最大值

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

<span className="mord,text">
<span className="mord,cjk_fallback">

当前门的传播延迟

</span>
</span>
</span>
</span>
</span>
</span>

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter8-Speed-05.webp)

##### Slack ｜ 时序裕量

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter8-Speed-06.webp)

- <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mtext>

slack

</mtext>

<mo>

=

</mo>

<mtext>

required time

</mtext>

<mo>

−

</mo>

<mtext>

arrival time

</mtext>
</mrow>

<annotation encoding="application/x-tex">

\text{slack} = \text{required time} - \text{arrival time}

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

slack

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

required time

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
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,text">
<span className="mord">

arrival time

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
  <mtext>
  
  slack
  
  </mtext>
  
  <mo>
  
  >
  </mo>
  
  <mn>
  
  0
  
  </mn>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  \text{slack} > 0
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:0.7335em;vertical-align:-0.0391em;">
  
  
  
  </span>
  
  <span className="mord,text">
  <span className="mord">
  
  slack
  
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
  
     说明信号来得够早，电路满足时序。
  - <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mtext>
  
  slack
  
  </mtext>
  
  <mo>
  <
  
  </mo>
  
  <mn>
  
  0
  
  </mn>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  \text{slack} < 0
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:0.7335em;vertical-align:-0.0391em;">
  
  
  
  </span>
  
  <span className="mord,text">
  <span className="mord">
  
  slack
  
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
  <span className="strut" style="height:0.6444em;">
  
  
  
  </span>
  
  <span className="mord">
  
  0
  
  </span>
  </span>
  </span>
  </span>
  
     说明信号来得太晚，电路不够快，需要优化。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter8-Speed-07.webp)

### 延时计算

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 53.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter8-Speed-08.webp" />
      </p>
    </td>
    
    
      <td style="width: 46.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter8-Speed-09.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

1. transistor-level simulator，例如 SPICE

  - 准确，但慢
2. LUT-based EDA tool

  - 比 SPICE 快很多，精度也较好
3. analytical model，例如 RC ladder model

  - 最快，但是不够精确

<mark>

虽然 SPICE 准，但我们仍然需要 analytical model，因为analytical model is fast而且更容易回答 “what if?”。

</mark>



## **CMOS Inverter ｜ CMOS反相器**

<alert type="tip">

11-18 电阻（铺垫）

19-21 电容（铺垫）

22-25 delay和RC关系 （24页单位CMOS 重要）

26-30 反向器延迟及其影响因素

31 总结

</alert>

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter8-Speed-10.webp)

- 反相器 delay 来自输出节点电容被 PMOS 充电或被 NMOS 放电所需的时间。
- 这个“中间阶段”就是动态延迟产生的关键，因为输出节点电容不是瞬间放完电的。
- 把 NMOS 看成开关  <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

d

</mi>

<mi>

e

</mi>

<mi>

l

</mi>

<mi>

a

</mi>

<mi>

y

</mi>

<mo>

=

</mo>

<msub>
<mi>

R

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

<mi>

C

</mi>
</mrow>

<annotation encoding="application/x-tex">

delay=R_{on}C

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

a

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

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>
</span>
</span>
</span>


  - 把复杂的 MOS 电流方程变成了简单的 RC 延迟模型。
  - 但是MOS transistor 的导通电阻是动态变化的，**RC 模型里的** <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mi>
  
  R
  
  </mi>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  R
  
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
  </span>
  </span>
  </span>
  
   **是平均等效值。**

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 52.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter8-Speed-11.webp" />
      </p>
    </td>
    
    
      <td style="width: 47.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter8-Speed-12.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

平均电阻取 <span className="katex">
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

 到 <span className="katex">
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

<mi mathvariant="normal">

/

</mi>

<mn>

2

</mn>
</mrow>

<annotation encoding="application/x-tex">

V_{DD}/2

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

<span className="mord">

/2

</span>
</span>
</span>
</span>

， delay 测到 <span className="katex">
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

<mi mathvariant="normal">

/

</mi>

<mn>

2

</mn>
</mrow>

<annotation encoding="application/x-tex">

V_{DD}/2

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

<span className="mord">

/2

</span>
</span>
</span>
</span>

，所以估算 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

R

</mi>

<mrow>
<mi>

e

</mi>

<mi>

q

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

R_{eq}

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
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0077em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

e

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

q

</span>
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

 时也主要平均输出从 <span className="katex">
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

 到 <span className="katex">
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

<mi mathvariant="normal">

/

</mi>

<mn>

2

</mn>
</mrow>

<annotation encoding="application/x-tex">

V_{DD}/2

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

<span className="mord">

/2

</span>
</span>
</span>
</span>

 这段。

### 等效电阻

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter8-Speed-13.webp)

#### Summary on Resistance ｜ 电阻总结

1. <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

R

</mi>

<mo>

∝

</mo>

<mfrac>
<mn>

1

</mn>

<mrow>
<mi>

W

</mi>

<mi mathvariant="normal">

/

</mi>

<mi>

L

</mi>
</mrow>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

R \propto \frac{1}{W/L}

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

∝

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.3651em;vertical-align:-0.52em;">



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
<span className="mord,mathnormal,mtight" style="margin-right:0.1389em;">

W

</span>

<span className="mord,mtight">

/

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
<span className="vlist" style="height:0.52em;">
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

，晶体管越宽，导通电阻越小，delay 越小。
2. 当供电电压接近阈值电压 <span className="katex">
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

t

</mi>

<mi>

h

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

V_{th}

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

t

</span>

<span className="mord,mathnormal,mtight">

h

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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

 时，电阻会急剧增大。这对应 near-threshold 和 sub-threshold 工作区，速度会显著下降。
3. MOS 等效电阻通常是 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

k

</mi>

<mi mathvariant="normal">

Ω

</mi>
</mrow>

<annotation encoding="application/x-tex">

k\Omega

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

<span className="mord">

Ω

</span>
</span>
</span>
</span>

 量级。

### Revisit Parasitics MOS Capacitance ｜ MOS 寄生电容

输出节点不只是接了外部负载电容，还会有 MOS 自身带来的寄生电容。

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 51.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter8-Speed-14.webp" />
      </p>
    </td>
    
    
      <td style="width: 48.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter8-Speed-15.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

- 栅面积大约和 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

W

</mi>

<mo>

⋅

</mo>

<mi>

L

</mi>
</mrow>

<annotation encoding="application/x-tex">

W \cdot L

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

<span className="mord,mathnormal">

L

</span>
</span>
</span>
</span>

 (Gate channel cap沟道电容)或和 <span className="katex">
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

(Gate overlap cap 、Diffusion cap) 有关；所以晶体管做大虽然降低电阻，但也会增加电容。
- <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

C

</mi>

<mo>

∝

</mo>

<mi>

W

</mi>

<mo>

⋅

</mo>

<mi>

L

</mi>
</mrow>

<annotation encoding="application/x-tex">

C \propto W\cdot L

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

∝

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

W

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

<span className="mord,mathnormal">

L

</span>
</span>
</span>
</span>

，  cell 级别的电容通常是 fF，也就是：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msup>
<mn>

10

</mn>

<mrow>
<mo>

−

</mo>

<mn>

15

</mn>
</mrow>
</msup>

<mi>

F

</mi>
</mrow>

<annotation encoding="application/x-tex">

10^{-15}F

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
<span className="mord,mtight">

−

</span>

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

<span className="mord,mathnormal" style="margin-right:0.1389em;">

F

</span>
</span>
</span>
</span>


  - 而整个芯片的总 <span className="katex">
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
  
  d
  
  </mi>
  
  <mi>
  
  i
  
  </mi>
  
  <mi>
  
  e
  
  </mi>
  </mrow>
  </msub>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  C_{die}
  
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
  
  d
  
  </span>
  
  <span className="mord,mathnormal,mtight">
  
  i
  
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
  
   可以达到几百到几千 nF，甚至更多。

### 反相器延时估计

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter8-Speed-16.webp)

<mark>

快速估算时可以先忽略 0.69，直接用：

</mark>

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

p

</mi>

<mi>

d

</mi>
</mrow>
</msub>

<mo>

≈

</mo>

<mi>

R

</mi>

<mi>

C

</mi>
</mrow>

<annotation encoding="application/x-tex">

t_{pd}\approx RC

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

p

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
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0077em;">

R

</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>
</span>
</span>
</span>



> 计算过程：（实际老掉牙了 非常简单）
> 
> 一阶 RC 放电可以写成：<span className="katex">
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
> </mrow>
> </msub>
> 
> <mo stretchy="false">
> 
> (
> 
> </mo>
> 
> <mi>
> 
> t
> 
> </mi>
> 
> <mo stretchy="false">
> 
> )
> 
> </mo>
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
> D
> 
> </mi>
> 
> <mi>
> 
> D
> 
> </mi>
> </mrow>
> </msub>
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
> t
> 
> </mi>
> 
> <mi mathvariant="normal">
> 
> /
> 
> </mi>
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
> R
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
> L
> 
> </mi>
> </msub>
> 
> <mo stretchy="false">
> 
> )
> 
> </mo>
> </mrow>
> </msup>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> V_{out}(t)=V_{DD}e^{-t/(R_{on}C_L)}
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
> <span className="mord,mtight">
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
> t
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
> <span className="mopen">
> 
> (
> 
> </span>
> 
> <span className="mord,mathnormal">
> 
> t
> 
> </span>
> 
> <span className="mclose">
> 
> )
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
> <span className="strut" style="height:1.038em;vertical-align:-0.15em;">
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
> <span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">
> 
> D
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
> t
> 
> </span>
> 
> <span className="mord,mtight">
> 
> /
> 
> </span>
> 
> <span className="mopen,mtight">
> 
> (
> 
> </span>
> 
> <span className="mord,mtight">
> <span className="mord,mathnormal,mtight" style="margin-right:0.0077em;">
> 
> R
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.1645em;">
> <span style="top:-2.357em;margin-left:-0.0077em;margin-right:0.0714em;">
> <span className="pstrut" style="height:2.5em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size3,size1,mtight">
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
> <span className="vlist" style="height:0.143em;">
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
> <span className="mord,mtight">
> <span className="mord,mathnormal,mtight" style="margin-right:0.0715em;">
> 
> C
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3448em;">
> <span style="top:-2.3567em;margin-left:-0.0715em;margin-right:0.0714em;">
> <span className="pstrut" style="height:2.5em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size3,size1,mtight">
> <span className="mord,mathnormal,mtight">
> 
> L
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
> <span className="vlist" style="height:0.1433em;">
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
> <span className="mclose,mtight">
> 
> )
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
> ， 传播延迟通常测到输出过半：<span className="katex">
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
> </mrow>
> </msub>
> 
> <mo>
> 
> =
> 
> </mo>
> 
> <mfrac>
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
> D
> 
> </mi>
> </mrow>
> </msub>
> 
> <mn>
> 
> 2
> 
> </mn>
> </mfrac>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> V_{out}=\frac{V_{DD}}{2}
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
> <span className="mord,mtight">
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
> t
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
> <span className="strut" style="height:1.2336em;vertical-align:-0.345em;">
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
> <span className="vlist" style="height:0.8886em;">
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
> 
> 2
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
> <span style="top:-3.4103em;">
> <span className="pstrut" style="height:3em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mtight">
> <span className="mord,mtight">
> <span className="mord,mathnormal,mtight" style="margin-right:0.2222em;">
> 
> V
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3448em;">
> <span style="top:-2.3567em;margin-left:-0.2222em;margin-right:0.0714em;">
> <span className="pstrut" style="height:2.5em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size3,size1,mtight">
> <span className="mord,mtight">
> <span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">
> 
> D
> 
> </span>
> 
> <span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">
> 
> D
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
> <span className="vlist" style="height:0.1433em;">
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
> 
> ， 代入：<span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <mfrac>
> <mn>
> 
> 1
> 
> </mn>
> 
> <mn>
> 
> 2
> 
> </mn>
> </mfrac>
> 
> <mo>
> 
> =
> 
> </mo>
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
> t
> 
> </mi>
> 
> <mi mathvariant="normal">
> 
> /
> 
> </mi>
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
> R
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
> L
> 
> </mi>
> </msub>
> 
> <mo stretchy="false">
> 
> )
> 
> </mo>
> </mrow>
> </msup>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> \frac{1}{2}=e^{-t/(R_{on}C_L)}
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:1.1901em;vertical-align:-0.345em;">
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
> <span className="vlist" style="height:0.8451em;">
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
> 
> 2
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
> <span className="strut" style="height:0.888em;">
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
> t
> 
> </span>
> 
> <span className="mord,mtight">
> 
> /
> 
> </span>
> 
> <span className="mopen,mtight">
> 
> (
> 
> </span>
> 
> <span className="mord,mtight">
> <span className="mord,mathnormal,mtight" style="margin-right:0.0077em;">
> 
> R
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.1645em;">
> <span style="top:-2.357em;margin-left:-0.0077em;margin-right:0.0714em;">
> <span className="pstrut" style="height:2.5em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size3,size1,mtight">
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
> <span className="vlist" style="height:0.143em;">
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
> <span className="mord,mtight">
> <span className="mord,mathnormal,mtight" style="margin-right:0.0715em;">
> 
> C
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3448em;">
> <span style="top:-2.3567em;margin-left:-0.0715em;margin-right:0.0714em;">
> <span className="pstrut" style="height:2.5em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size3,size1,mtight">
> <span className="mord,mathnormal,mtight">
> 
> L
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
> <span className="vlist" style="height:0.1433em;">
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
> <span className="mclose,mtight">
> 
> )
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
> ，可得<span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
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
> <mi>
> 
> ln
> 
> </mi>
> 
> <mo>
> 
> ⁡
> 
> </mo>
> 
> <mn>
> 
> 2
> 
> </mn>
> 
> <mo>
> 
> ⋅
> 
> </mo>
> 
> <msub>
> <mi>
> 
> R
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
> L
> 
> </mi>
> </msub>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> t=\ln 2 \cdot R_{on}C_L
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:0.6151em;">
> 
> 
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
> <span className="strut" style="height:0.6944em;">
> 
> 
> 
> </span>
> 
> <span className="mop">
> 
> ln
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
> <span className="mspace" style="margin-right:0.2222em;">
> 
> 
> 
> </span>
> 
> <span className="mbin">
> 
> ⋅
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
> <span className="mord,mathnormal" style="margin-right:0.0077em;">
> 
> R
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.1514em;">
> <span style="top:-2.55em;margin-left:-0.0077em;margin-right:0.05em;">
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
> <span className="vlist" style="height:0.3283em;">
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
> L
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
>   因此  <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <mi>
> 
> t
> 
> </mi>
> 
> <mo>
> 
> ≈
> 
> </mo>
> 
> <mn>
> 
> 0.69
> 
> </mn>
> 
> <msub>
> <mi>
> 
> R
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
> L
> 
> </mi>
> </msub>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> t\approx 0.69R_{on}C_L
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:0.6151em;">
> 
> 
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
> <span className="strut" style="height:0.8333em;vertical-align:-0.15em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> 
> 0.69
> 
> </span>
> 
> <span className="mord">
> <span className="mord,mathnormal" style="margin-right:0.0077em;">
> 
> R
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.1514em;">
> <span style="top:-2.55em;margin-left:-0.0077em;margin-right:0.05em;">
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
> <span className="vlist" style="height:0.3283em;">
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
> L
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

#### 更高阶的估计——Transient Response 的长沟道模型推导

对输出下降过程做了更细的长沟道模型分析。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter8-Speed-17.webp)

这页想表达的是：如果精确分析，电流方程是分段的，求解比较麻烦；所以后面才更愿意用平均电阻 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

R

</mi>

<mrow>
<mi>

e

</mi>

<mi>

q

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

R_{eq}

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
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0077em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

e

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

q

</span>
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

 的 RC 模型来估算。

#### RC Delay Model —— PMOS 和 NMOS 不一样<mark>（重要）</mark>

进一步修正 RC 模型：PMOS 和 NMOS 的迁移率不同。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter8-Speed-18.webp)

给出单位PMOS 和 NMOS

> 因为 PMOS 的空穴迁移率低于 NMOS 的电子迁移率，所以同尺寸 PMOS 通常比 NMOS 弱。
> 
> 为了让上升和下降速度接近平衡，常常把 PMOS 尺寸做成 NMOS 的大约 2 倍：
> 
> <span className="katex-display">
> <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
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
> p
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
> <mn>
> 
> 2
> 
> </mn>
> 
> <msub>
> <mi>
> 
> W
> 
> </mi>
> 
> <mi>
> 
> n
> 
> </mi>
> </msub>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> W_p≈2W_n
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
> <span className="strut" style="height:0.8333em;vertical-align:-0.15em;">
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
> <span className="mord,mathnormal" style="margin-right:0.1389em;">
> 
> W
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
> </span>
> </span>
> </span>
> </span>
> 
> 晶体管尺寸放大 <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <mi>
> 
> k
> 
> </mi>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> k
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
> <span className="mord,mathnormal" style="margin-right:0.0315em;">
> 
> k
> 
> </span>
> </span>
> </span>
> </span>
> 
>  倍时，导通电阻约变为原来的 <span className="katex">
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
> <mi mathvariant="normal">
> 
> /
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
> 1/k
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
> <span className="mord">
> 
> 1/
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
> ，但相关电容约增大为 <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <mi>
> 
> k
> 
> </mi>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> k
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
> <span className="mord,mathnormal" style="margin-right:0.0315em;">
> 
> k
> 
> </span>
> </span>
> </span>
> </span>
> 
>  倍，**因此 sizing up 会降低电阻、增加电容。**

#### RC Values  |  R、C  典型值

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter8-Speed-19.webp)

---

##### Example: Inverter Delay Estimate |  反相器延迟估算

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter8-Speed-20.webp)

对于这道题而言 无论是0到1反转还是1-0翻转，延时都是相同的<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

d

</mi>

<mi>

e

</mi>

<mi>

l

</mi>

<mi>

a

</mi>

<mi>

y

</mi>

<mo>

=

</mo>

<mn>

6

</mn>

<mi>

R

</mi>

<mi>

C

</mi>
</mrow>

<annotation encoding="application/x-tex">

delay=6RC

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

a

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

<span className="mord">

6

</span>

<span className="mord,mathnormal" style="margin-right:0.0077em;">

R

</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>
</span>
</span>
</span>



#### Factors Impacting Inverter Delay ｜ 影响反相器 delay 的因素

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter8-Speed-21.webp)

1. Output load：输出负载越大，delay 越大：
2. Device size：增大晶体管尺寸可以降低电阻：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

W

</mi>

<mo>

↑

</mo>

<mo>

⇒

</mo>

<mi>

R

</mi>

<mo>

↓

</mo>
</mrow>

<annotation encoding="application/x-tex">

W\uparrow \Rightarrow R\downarrow

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

<span className="mord,mathnormal" style="margin-right:0.0077em;">

R

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

↓

</span>
</span>
</span>
</span>

，但会增加寄生电容：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

W

</mi>

<mo>

↑

</mo>

<mo>

⇒

</mo>

<msub>
<mi>

C

</mi>

<mrow>
<mi>

p

</mi>

<mi>

a

</mi>

<mi>

r

</mi>

<mi>

a

</mi>

<mi>

s

</mi>

<mi>

i

</mi>

<mi>

t

</mi>

<mi>

i

</mi>

<mi>

c

</mi>
</mrow>
</msub>

<mo>

↑

</mo>
</mrow>

<annotation encoding="application/x-tex">

W\uparrow \Rightarrow C_{parasitic}\uparrow

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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

↑⇒

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.9805em;vertical-align:-0.2861em;">



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

p

</span>

<span className="mord,mathnormal,mtight">

a

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal,mtight">

a

</span>

<span className="mord,mathnormal,mtight">

s

</span>

<span className="mord,mathnormal,mtight">

i

</span>

<span className="mord,mathnormal,mtight">

t

</span>

<span className="mord,mathnormal,mtight">

i

</span>

<span className="mord,mathnormal,mtight">

c

</span>
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

↑

</span>
</span>
</span>
</span>

，所以存在 trade-off。
3. P/N ratio，PMOS 和 NMOS 的尺寸比例会影响上升延迟和下降延迟。PMOS 做大，上升更快，但它的扩散电容也变大，可能拖慢下降。
4. Input slew：输入边沿越慢，输出延迟通常越大。因为输入慢时，PMOS 和 NMOS 同时导通的时间更长，并且还会带来更复杂的耦合效应。

##### Device Size —— 晶体管尺寸对 delay 的影响

随着尺寸因子 <span className="katex">
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

 增大，delay 下降，但不是线性下降，而是逐渐趋于饱和。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter8-Speed-22.webp)

原因是：

- 刚开始增大晶体管时，<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

R

</mi>
</mrow>

<annotation encoding="application/x-tex">

R

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
</span>
</span>
</span>

 明显下降，所以 delay 降得快；
- 后面继续增大时，晶体管自己的 **intrinsic capacitance** **寄生电容**也变大；
- self-loading effect 开始主导，所以 delay 不再明显下降。

可以把总 delay 写成一个直观形式：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

t

</mi>

<mo>

≈

</mo>

<msub>
<mi>

R

</mi>

<mrow>
<mi>

e

</mi>

<mi>

q

</mi>
</mrow>
</msub>

<mo stretchy="false">

(

</mo>

<msub>
<mi>

C

</mi>

<mrow>
<mi>

l

</mi>

<mi>

o

</mi>

<mi>

a

</mi>

<mi>

d

</mi>
</mrow>
</msub>

<mo>

+

</mo>

<msub>
<mi>

C

</mi>

<mrow>
<mi>

p

</mi>

<mi>

a

</mi>

<mi>

r

</mi>

<mi>

a

</mi>

<mi>

s

</mi>

<mi>

i

</mi>

<mi>

t

</mi>

<mi>

i

</mi>

<mi>

c

</mi>
</mrow>
</msub>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

t \approx R_{eq}(C_{load}+C_{parasitic})

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

≈

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.0361em;vertical-align:-0.2861em;">



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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

e

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

q

</span>
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
<span className="mord,mathnormal,mtight" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal,mtight">

o

</span>

<span className="mord,mathnormal,mtight">

a

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

p

</span>

<span className="mord,mathnormal,mtight">

a

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal,mtight">

a

</span>

<span className="mord,mathnormal,mtight">

s

</span>

<span className="mord,mathnormal,mtight">

i

</span>

<span className="mord,mathnormal,mtight">

t

</span>

<span className="mord,mathnormal,mtight">

i

</span>

<span className="mord,mathnormal,mtight">

c

</span>
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

，假设尺寸放大 <span className="katex">
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

 倍：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

R

</mi>

<mrow>
<mi>

e

</mi>

<mi>

q

</mi>
</mrow>
</msub>

<mo>

∼

</mo>

<mfrac>
<mi>

R

</mi>

<mi>

S

</mi>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

R_{eq}\sim \frac{R}{S}

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
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0077em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

e

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

q

</span>
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

∼

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
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

S

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

  <span className="katex">
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

p

</mi>

<mi>

a

</mi>

<mi>

r

</mi>

<mi>

a

</mi>

<mi>

s

</mi>

<mi>

i

</mi>

<mi>

t

</mi>

<mi>

i

</mi>

<mi>

c

</mi>
</mrow>
</msub>

<mo>

∼

</mo>

<mi>

S

</mi>

<mi>

C

</mi>
</mrow>

<annotation encoding="application/x-tex">

C_{parasitic}\sim SC

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

p

</span>

<span className="mord,mathnormal,mtight">

a

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal,mtight">

a

</span>

<span className="mord,mathnormal,mtight">

s

</span>

<span className="mord,mathnormal,mtight">

i

</span>

<span className="mord,mathnormal,mtight">

t

</span>

<span className="mord,mathnormal,mtight">

i

</span>

<span className="mord,mathnormal,mtight">

c

</span>
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

∼

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0576em;">

S

</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>
</span>
</span>
</span>

，所以：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

t

</mi>

<mo>

∼

</mo>

<mfrac>
<mi>

R

</mi>

<mi>

S

</mi>
</mfrac>

<mo stretchy="false">

(

</mo>

<msub>
<mi>

C

</mi>

<mrow>
<mi>

l

</mi>

<mi>

o

</mi>

<mi>

a

</mi>

<mi>

d

</mi>
</mrow>
</msub>

<mo>

+

</mo>

<mi>

S

</mi>

<mi>

C

</mi>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

t\sim \frac{R}{S}(C_{load}+SC)

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

∼

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
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

S

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
<span className="mord,mathnormal,mtight" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal,mtight">

o

</span>

<span className="mord,mathnormal,mtight">

a

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

<span className="mord,mathnormal" style="margin-right:0.0576em;">

S

</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="mclose">

)

</span>
</span>
</span>
</span>

  即 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

t

</mi>

<mo>

∼

</mo>

<mfrac>
<mrow>
<mi>

R

</mi>

<msub>
<mi>

C

</mi>

<mrow>
<mi>

l

</mi>

<mi>

o

</mi>

<mi>

a

</mi>

<mi>

d

</mi>
</mrow>
</msub>
</mrow>

<mi>

S

</mi>
</mfrac>

<mo>

+

</mo>

<mi>

R

</mi>

<mi>

C

</mi>
</mrow>

<annotation encoding="application/x-tex">

t\sim \frac{RC_{load}}{S}+RC

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

∼

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
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

S

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
<span className="mord,mathnormal,mtight" style="margin-right:0.0077em;">

R

</span>

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
<span className="mord,mathnormal,mtight" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal,mtight">

o

</span>

<span className="mord,mathnormal,mtight">

a

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

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0077em;">

R

</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>
</span>
</span>
</span>



第一项会随着 <span className="katex">
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

 增大而下降，但第二项不会消失。这就是为什么尺寸做大后 delay 下降会变慢。

---

##### PMOS/NMOS Ratio —— PMOS/NMOS 比例

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter8-Speed-23.webp)

固定 NMOS、增大 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

β

</mi>

<mo>

=

</mo>

<msub>
<mi>

W

</mi>

<mi>

p

</mi>
</msub>

<mi mathvariant="normal">

/

</mi>

<msub>
<mi>

W

</mi>

<mi>

n

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

\beta=W_p/W_n

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0528em;">

β

</span>

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

<span className="mord">

/

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

 时，PMOS 上拉电阻减小，<span className="katex">
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

p

</mi>

<mi>

L

</mi>

<mi>

H

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

t_{pLH}

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

 下降；但 PMOS 扩散电容增大，输出节点负载变大，NMOS 放电更慢，<span className="katex">
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
</mrow>

<annotation encoding="application/x-tex">

t_{pHL}

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
</span>
</span>
</span>

 上升。因此平均延迟 <span className="katex">
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

 随 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

β

</mi>
</mrow>

<annotation encoding="application/x-tex">

\beta

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0528em;">

β

</span>
</span>
</span>
</span>

 呈 U 形变化，存在最优宽度比。这个最优点不一定等于 <span className="katex">
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

p

</mi>

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
</mrow>

<annotation encoding="application/x-tex">

t_{pLH}=t_{pHL}

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
</span>
</span>
</span>

 的平衡点。

##### Input Slew ｜ 输入边沿对 delay 的影响

讨论输入 slew，也就是输入信号的上升/下降时间。

对旧工艺来说，这种关系几乎线性；对 32 nm 及以下工艺，会表现出非线性。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter8-Speed-24.webp)

Input slew 表示输入边沿的上升/下降时间。输入边沿越慢，NMOS/PMOS 的导通状态变化越慢，输出电容的充放电电流变小，因此门延迟增大。图中 <span className="katex">
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

r

</mi>

<mi>

i

</mi>

<mi>

s

</mi>

<mi>

e

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

t_{rise}

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
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal,mtight">

i

</span>

<span className="mord,mathnormal,mtight">

se

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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

 越大，输出高到低延迟 <span className="katex">
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
</mrow>

<annotation encoding="application/x-tex">

t_{pHL}

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
</span>
</span>
</span>

 越大。实际 STA 中，单元 delay 不是常数，而是 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

d

</mi>

<mi>

e

</mi>

<mi>

l

</mi>

<mi>

a

</mi>

<mi>

y

</mi>

<mo>

=

</mo>

<mi>

f

</mi>

<mo stretchy="false">

(

</mo>

<mi>

i

</mi>

<mi>

n

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

<mtext>



</mtext>

<mi>

s

</mi>

<mi>

l

</mi>

<mi>

e

</mi>

<mi>

w

</mi>

<mo separator="true">

,

</mo>

<mtext>



</mtext>

<mi>

o

</mi>

<mi>

u

</mi>

<mi>

t

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

<mtext>



</mtext>

<mi>

l

</mi>

<mi>

o

</mi>

<mi>

a

</mi>

<mi>

d

</mi>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

delay=f(input\ slew,\ output\ load)

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

a

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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1076em;">

f

</span>

<span className="mopen">

(

</span>

<span className="mord,mathnormal">

in

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

<span className="mspace">



</span>

<span className="mord,mathnormal">

s

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal" style="margin-right:0.0269em;">

w

</span>

<span className="mpunct">

,

</span>

<span className="mspace">



</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord,mathnormal">

o

</span>

<span className="mord,mathnormal">

u

</span>

<span className="mord,mathnormal">

tp

</span>

<span className="mord,mathnormal">

u

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mspace">



</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

o

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal">

d

</span>

<span className="mclose">

)

</span>
</span>
</span>
</span>

，所以高速设计必须控制输入 slew。

---

### Key Take-Aways ｜ 总结

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

p

</mi>

<mi>

d

</mi>
</mrow>
</msub>

<mo>

≈

</mo>

<mi>

R

</mi>

<mi>

C

</mi>
</mrow>

<annotation encoding="application/x-tex">

t_{pd}\approx RC

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

p

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
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0077em;">

R

</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>
</span>
</span>
</span>

， 其中：<span className="katex">
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

<mtext>

MOS 等效导通电阻

</mtext>
</mrow>

<annotation encoding="application/x-tex">

R=\text{MOS 等效导通电阻}

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
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,text">
<span className="mord">

MOS

</span>

<span className="mord,cjk_fallback">

等效导通电阻

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

C

</mi>

<mo>

=

</mo>

<mtext>

输出节点总电容

</mtext>
</mrow>

<annotation encoding="application/x-tex">

C=\text{输出节点总电容}

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
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,text">
<span className="mord,cjk_fallback">

输出节点总电容

</span>
</span>
</span>
</span>
</span>

，并且： <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

W

</mi>

<mo>

↑

</mo>

<mo>

⇒

</mo>

<mi>

R

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

C

</mi>

<mo>

↑

</mo>
</mrow>

<annotation encoding="application/x-tex">

W\uparrow \Rightarrow R\downarrow,\ C\uparrow

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

<span className="mord,mathnormal" style="margin-right:0.0077em;">

R

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

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

↑

</span>
</span>
</span>
</span>

，所以 sizing 是 trade-off。

---

## **复杂逻辑门的延迟**

> 反相器只有一个上拉/下拉路径；复杂门有串联、并联晶体管和内部节点电容，delay 怎么估？

### Example: 3-input NAND —— 三输入 NAND 的晶体管尺寸

> MOS中数字代表晶体管宽度，注意标准反向器PMOS宽度为2，NOMS宽度为1

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 27.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter8-Speed-25.webp" />
      </p>
    </td>
    
    
      <td style="width: 72.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter8-Speed-26.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

1. NMOS

  1. 在反相器中，unit NMOS 的宽度可以看作 1，对应导通电阻：<span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mi>
  
  R
  
  </mi>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  R
  
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
  </span>
  </span>
  </span>
  2. 为了让三个串联 NMOS 的总电阻仍然约为 <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mi>
  
  R
  
  </mi>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  R
  
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
  </span>
  </span>
  </span>
  
  ，把每个 NMOS 宽度放大 3 倍：<span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <msub>
  <mi>
  
  W
  
  </mi>
  
  <mi>
  
  n
  
  </mi>
  </msub>
  
  <mo>
  
  =
  
  </mo>
  
  <mn>
  
  3
  
  </mn>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  W_n=3
  
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
  <span className="vlist" style="height:0.1514em;">
  <span style="top:-2.55em;margin-left:-0.1389em;margin-right:0.05em;">
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
  <span className="strut" style="height:0.6444em;">
  
  
  
  </span>
  
  <span className="mord">
  
  3
  
  </span>
  </span>
  </span>
  </span>
  3. 单个 NMOS 电阻变为：<span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mfrac>
  <mi>
  
  R
  
  </mi>
  
  <mn>
  
  3
  
  </mn>
  </mfrac>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  \frac{R}{3}
  
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
2. PMOS

  1. 上拉网络是三个 PMOS 并联。NAND 输出上升时，最坏情况通常只有一个 PMOS 导通。
  2. 所以每个 PMOS 取：<span className="katex">
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
  
  =
  
  </mo>
  
  <mn>
  
  2
  
  </mn>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  W_p=2
  
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
  3. <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mtext>
  
  3-input NAND:
  
  </mtext>
  
  <msub>
  <mi>
  
  W
  
  </mi>
  
  <mi>
  
  p
  
  </mi>
  </msub>
  
  <mo>
  
  =
  
  </mo>
  
  <mn>
  
  2
  
  </mn>
  
  <mo separator="true">
  
  ,
  
  </mo>
  
  <mspace width="1em">
  
  
  
  </mspace>
  
  <msub>
  <mi>
  
  W
  
  </mi>
  
  <mi>
  
  n
  
  </mi>
  </msub>
  
  <mo>
  
  =
  
  </mo>
  
  <mn>
  
  3
  
  </mn>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  \text{3-input NAND: } W_p=2,\quad W_n=3
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:0.9694em;vertical-align:-0.2861em;">
  
  
  
  </span>
  
  <span className="mord,text">
  <span className="mord">
  
  3-input NAND:
  
  </span>
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
  
  =
  
  </span>
  
  <span className="mspace" style="margin-right:0.2778em;">
  
  
  
  </span>
  </span>
  
  <span className="base">
  <span className="strut" style="height:0.8778em;vertical-align:-0.1944em;">
  
  
  
  </span>
  
  <span className="mord">
  
  2
  
  </span>
  
  <span className="mpunct">
  
  ,
  
  </span>
  
  <span className="mspace" style="margin-right:1em;">
  
  
  
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
  <span className="vlist" style="height:0.1514em;">
  <span style="top:-2.55em;margin-left:-0.1389em;margin-right:0.05em;">
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
  <span className="strut" style="height:0.6444em;">
  
  
  
  </span>
  
  <span className="mord">
  
  3
  
  </span>
  </span>
  </span>
  </span>

---

### 3-input NAND Caps —— 给 NAND3 标寄生电容

> 按24页标准来

---

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter8-Speed-27.webp)

1. 输入端
  1. PMOS 宽度是 2，所以它的 gate capacitance 约为：<span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mn>
  
  2
  
  </mn>
  
  <mi>
  
  C
  
  </mi>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  2C
  
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
  
  <span className="mord,mathnormal" style="margin-right:0.0715em;">
  
  C
  
  </span>
  </span>
  </span>
  </span>
  2. NMOS 宽度是 3，所以它的 gate capacitance 约为：<span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mn>
  
  3
  
  </mn>
  
  <mi>
  
  C
  
  </mi>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  3C
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:0.6833em;">
  
  
  
  </span>
  
  <span className="mord">
  
  3
  
  </span>
  
  <span className="mord,mathnormal" style="margin-right:0.0715em;">
  
  C
  
  </span>
  </span>
  </span>
  </span>
  
  
  所以每个输入端的总输入电容是：<span className="katex">
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
  
  n
  
  </mi>
  </mrow>
  </msub>
  
  <mo>
  
  =
  
  </mo>
  
  <mn>
  
  2
  
  </mn>
  
  <mi>
  
  C
  
  </mi>
  
  <mo>
  
  +
  
  </mo>
  
  <mn>
  
  3
  
  </mn>
  
  <mi>
  
  C
  
  </mi>
  
  <mo>
  
  =
  
  </mo>
  
  <mn>
  
  5
  
  </mn>
  
  <mi>
  
  C
  
  </mi>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  C_{in}=2C+3C=5C
  
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
  <span className="mord,mtight">
  <span className="mord,mathnormal,mtight">
  
  in
  
  </span>
  </span>
  </span>
  </span>
  </span>
  
  <span className="vlist-s">
  
  ​
  
  </span>
  </span>
  
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
  
  <span className="mord">
  
  2
  
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
  <span className="strut" style="height:0.6833em;">
  
  
  
  </span>
  
  <span className="mord">
  
  3
  
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
  <span className="strut" style="height:0.6833em;">
  
  
  
  </span>
  
  <span className="mord">
  
  5
  
  </span>
  
  <span className="mord,mathnormal" style="margin-right:0.0715em;">
  
  C
  
  </span>
  </span>
  </span>
  </span><br />

如果这个 NAND3 驱动 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

h

</mi>
</mrow>

<annotation encoding="application/x-tex">

h

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,mathnormal">

h

</span>
</span>
</span>
</span>

 个相同 NAND3，那么负载 gate capacitance 就是：<span className="katex">
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

l

</mi>

<mi>

o

</mi>

<mi>

a

</mi>

<mi>

d

</mi>
</mrow>
</msub>

<mo>

=

</mo>

<mi>

h

</mi>

<mo>

⋅

</mo>

<mn>

5

</mn>

<mi>

C

</mi>

<mo>

=

</mo>

<mn>

5

</mn>

<mi>

h

</mi>

<mi>

C

</mi>
</mrow>

<annotation encoding="application/x-tex">

C_{load}=h\cdot 5C=5hC

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
<span className="mord,mathnormal,mtight" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal,mtight">

o

</span>

<span className="mord,mathnormal,mtight">

a

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
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,mathnormal">

h

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

5

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
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord">

5

</span>

<span className="mord,mathnormal">

h

</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>
</span>
</span>
</span>
2. 输出端
  1. 三个 PMOS 每个宽度 2，所以贡献：<span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mn>
  
  3
  
  </mn>
  
  <mo>
  
  ×
  
  </mo>
  
  <mn>
  
  2
  
  </mn>
  
  <mi>
  
  C
  
  </mi>
  
  <mo>
  
  =
  
  </mo>
  
  <mn>
  
  6
  
  </mn>
  
  <mi>
  
  C
  
  </mi>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  3 \times 2C=6C
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:0.7278em;vertical-align:-0.0833em;">
  
  
  
  </span>
  
  <span className="mord">
  
  3
  
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
  
  2
  
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
  <span className="strut" style="height:0.6833em;">
  
  
  
  </span>
  
  <span className="mord">
  
  6
  
  </span>
  
  <span className="mord,mathnormal" style="margin-right:0.0715em;">
  
  C
  
  </span>
  </span>
  </span>
  </span>
  2. 最上方 NMOS 宽度 3，贡献：<span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mn>
  
  3
  
  </mn>
  
  <mi>
  
  C
  
  </mi>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  3C
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:0.6833em;">
  
  
  
  </span>
  
  <span className="mord">
  
  3
  
  </span>
  
  <span className="mord,mathnormal" style="margin-right:0.0715em;">
  
  C
  
  </span>
  </span>
  </span>
  </span>
  3. 所以输出节点自身寄生电容为：<span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <msub>
  <mi>
  
  C
  
  </mi>
  
  <mi>
  
  Y
  
  </mi>
  </msub>
  
  <mo>
  
  =
  
  </mo>
  
  <mn>
  
  6
  
  </mn>
  
  <mi>
  
  C
  
  </mi>
  
  <mo>
  
  +
  
  </mo>
  
  <mn>
  
  3
  
  </mn>
  
  <mi>
  
  C
  
  </mi>
  
  <mo>
  
  =
  
  </mo>
  
  <mn>
  
  9
  
  </mn>
  
  <mi>
  
  C
  
  </mi>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  C_Y=6C+3C=9C
  
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
  <span className="vlist" style="height:0.3283em;">
  <span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
  <span className="pstrut" style="height:2.7em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size6,size3,mtight">
  <span className="mord,mathnormal,mtight" style="margin-right:0.2222em;">
  
  Y
  
  </span>
  </span>
  </span>
  </span>
  
  <span className="vlist-s">
  
  ​
  
  </span>
  </span>
  
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
  
  <span className="mord">
  
  6
  
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
  <span className="strut" style="height:0.6833em;">
  
  
  
  </span>
  
  <span className="mord">
  
  3
  
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
  <span className="strut" style="height:0.6833em;">
  
  
  
  </span>
  
  <span className="mord">
  
  9
  
  </span>
  
  <span className="mord,mathnormal" style="margin-right:0.0715em;">
  
  C
  
  </span>
  </span>
  </span>
  </span>

> 如果再加上外部 fanout 负载：
> 
> <span className="katex-display">
> <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
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
> Y
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
> <mo stretchy="false">
> 
> (
> 
> </mo>
> 
> <mn>
> 
> 9
> 
> </mn>
> 
> <mo>
> 
> +
> 
> </mo>
> 
> <mn>
> 
> 5
> 
> </mn>
> 
> <mi>
> 
> h
> 
> </mi>
> 
> <mo stretchy="false">
> 
> )
> 
> </mo>
> 
> <mi>
> 
> C
> 
> </mi>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> C_Y=(9+5h)C
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
> <span className="vlist" style="height:0.3283em;">
> <span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mathnormal,mtight" style="margin-right:0.2222em;">
> 
> Y
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
> 
> 9
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
> <span className="strut" style="height:1em;vertical-align:-0.25em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> 
> 5
> 
> </span>
> 
> <span className="mord,mathnormal">
> 
> h
> 
> </span>
> 
> <span className="mclose">
> 
> )
> 
> </span>
> 
> <span className="mord,mathnormal" style="margin-right:0.0715em;">
> 
> C
> 
> </span>
> </span>
> </span>
> </span>
> </span>

1. 内部节点

  1. 3 个 NMOS 串联时，中间会出现两个内部节点，其电容：<span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mn>
  
  3
  
  </mn>
  
  <mi>
  
  C
  
  </mi>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  3C
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:0.6833em;">
  
  
  
  </span>
  
  <span className="mord">
  
  3
  
  </span>
  
  <span className="mord,mathnormal" style="margin-right:0.0715em;">
  
  C
  
  </span>
  </span>
  </span>
  </span>
  2. <mark>
  
  **是因为源漏共用，只算一个**
  
  </mark>

---

### Elmore Delay —— 用 Elmore delay 分析 RC ladder

则 Elmore delay ：<span className="katex">
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

p

</mi>

<mi>

d

</mi>
</mrow>
</msub>

<mo>

≈

</mo>

<msub>
<mo>

∑

</mo>

<mi>

i

</mi>
</msub>

<msub>
<mi>

R

</mi>

<mrow>
<mi>

i

</mi>

<mo>

→

</mo>

<mi>

s

</mi>

<mi>

o

</mi>

<mi>

u

</mi>

<mi>

r

</mi>

<mi>

c

</mi>

<mi>

e

</mi>
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
</mrow>

<annotation encoding="application/x-tex">

t_{pd}\approx \sum_i R_{i\rightarrow source}C_i

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

p

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
<span className="strut" style="height:1.0497em;vertical-align:-0.2997em;">



</span>

<span className="mop">
<span className="mop,op-symbol,small-op" style="position:relative;top:0em;">

∑

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.162em;">
<span style="top:-2.4003em;margin-left:0em;margin-right:0.05em;">
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
<span className="mord,mathnormal" style="margin-right:0.0077em;">

R

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0077em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

i

</span>

<span className="mrel,mtight">

→

</span>

<span className="mord,mathnormal,mtight">

so

</span>

<span className="mord,mathnormal,mtight">

u

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal,mtight">

ce

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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



---

### NAND3 worst-case rising/falling delay

这一页估算 **3-input NAND 驱动** <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

h

</mi>
</mrow>

<annotation encoding="application/x-tex">

h

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,mathnormal">

h

</span>
</span>
</span>
</span>

 **个相同 NAND3** 时的最坏上升和下降延迟。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter8-Speed-28.webp)

#### rising delay：输出从 0 到 1

VCC -> R -> Y

用 Elmore delay 即得如图

#### falling delay：输出从 1 到 0

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

N

</mi>

<mi>

D

</mi>

<mo>

→

</mo>

<mfrac>
<mi>

R

</mi>

<mn>

3

</mn>
</mfrac>

<mo>

→

</mo>

<msub>
<mi>

n

</mi>

<mn>

1

</mn>
</msub>

<mo>

→

</mo>

<mfrac>
<mi>

R

</mi>

<mn>

3

</mn>
</mfrac>

<mo>

→

</mo>

<msub>
<mi>

n

</mi>

<mn>

2

</mn>
</msub>

<mo>

→

</mo>

<mfrac>
<mi>

R

</mi>

<mn>

3

</mn>
</mfrac>

<mo>

→

</mo>

<mi>

Y

</mi>
</mrow>

<annotation encoding="application/x-tex">

GND \rightarrow \frac{R}{3} \rightarrow n_1 \rightarrow \frac{R}{3} \rightarrow n_2 \rightarrow \frac{R}{3} \rightarrow Y

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

GN

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
<span className="mord,mathnormal" style="margin-right:0.0077em;">

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

→

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

→

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
<span className="mord,mathnormal" style="margin-right:0.0077em;">

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

→

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

→

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
<span className="mord,mathnormal" style="margin-right:0.0077em;">

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

→

</span>

<span className="mspace" style="margin-right:0.2778em;">



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
</span>

用 Elmore delay 即得如图

---

### P37：Delay Components —— 延迟分成两部分

把复杂门 delay 拆成两部分：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mtext>

parasitic delay

</mtext>

<mo>

+

</mo>

<mtext>

effort delay

</mtext>
</mrow>

<annotation encoding="application/x-tex">

\text{parasitic delay}+\text{effort delay}

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

parasitic delay

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
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,text">
<span className="mord">

effort delay

</span>
</span>
</span>
</span>
</span>
</span>

parasitic delay 是 15 或 12 RC，和负载无关；effort delay 是 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mn>

5

</mn>

<mi>

h

</mi>

<mi>

R

</mi>

<mi>

C

</mi>
</mrow>

<annotation encoding="application/x-tex">

5hRC

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord">

5

</span>

<span className="mord,mathnormal">

h

</span>

<span className="mord,mathnormal" style="margin-right:0.0077em;">

R

</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>
</span>
</span>
</span>

，与负载电容成正比。

---

### Contamination Delay —— 最好情况延迟

复杂门里的 **contamination delay**。

三个 PMOS 同时导通，而且它们是并联的。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter8-Speed-29.webp)

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

c

</mi>

<mi>

d

</mi>

<mi>

r

</mi>
</mrow>
</msub>

<mo>

=

</mo>

<mfrac>
<mi>

R

</mi>

<mn>

3

</mn>
</mfrac>

<mo stretchy="false">

(

</mo>

<mn>

9

</mn>

<mo>

+

</mo>

<mn>

5

</mn>

<mi>

h

</mi>

<mo stretchy="false">

)

</mo>

<mi>

C

</mi>
</mrow>

<annotation encoding="application/x-tex">

t_{cdr}=\frac{R}{3}(9+5h)C

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

c

</span>

<span className="mord,mathnormal,mtight">

d

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

r

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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
<span className="mord,mathnormal" style="margin-right:0.0077em;">

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

<span className="mopen">

(

</span>

<span className="mord">

9

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

5

</span>

<span className="mord,mathnormal">

h

</span>

<span className="mclose">

)

</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

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

t

</mi>

<mrow>
<mi>

c

</mi>

<mi>

d

</mi>

<mi>

r

</mi>
</mrow>
</msub>

<mo>

=

</mo>

<mrow>
<mo fence="true">

(

</mo>

<mn>

3

</mn>

<mo>

+

</mo>

<mfrac>
<mrow>
<mn>

5

</mn>

<mi>

h

</mi>
</mrow>

<mn>

3

</mn>
</mfrac>

<mo fence="true">

)

</mo>
</mrow>

<mi>

R

</mi>

<mi>

C

</mi>
</mrow>

<annotation encoding="application/x-tex">

t_{cdr}=\left(3+\frac{5h}{3}\right)RC

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

c

</span>

<span className="mord,mathnormal,mtight">

d

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

r

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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
<span className="strut" style="height:2.4em;vertical-align:-0.95em;">



</span>

<span className="minner">
<span className="mopen,delimcenter" style="top:0em;">
<span className="delimsizing,size3">

(

</span>
</span>

<span className="mord">

3

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
<span className="vlist" style="height:1.3714em;">
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

5

</span>

<span className="mord,mathnormal">

h

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

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0077em;">

R

</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

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

t

</mi>

<mrow>
<mi>

c

</mi>

<mi>

d

</mi>

<mi>

f

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

t_{cdf}

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

c

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.1076em;">

df

</span>
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

不变，因为最好情况与最坏情况一样

</mark>



---

### P39：Diffusion Capacitance —— 版图会影响扩散电容

前面假设每个 source/drain 都有 contacted diffusion capacitance，但真实 layout 可以优化 diffusion area。课件举例说，NAND3 layout 共享一个 diffusion contact，可以把输出电容减少 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mn>

2

</mn>

<mi>

C

</mi>
</mrow>

<annotation encoding="application/x-tex">

2C

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

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>
</span>
</span>
</span>

，merged uncontacted diffusion 也可能有帮助。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter8-Speed-30.webp)

9C->7C

> 好的 layout 可以减少 diffusion capacitance，从而减少 parasitic delay。

---

### Input Pattern Affects Delay —— 输入模式影响延迟

除了前面讲过的输出负载、尺寸、P/N ratio、input slew 之外，复杂门 delay 还依赖 input pattern

由于中间节点的电容是否充上电的缘故导致的

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter8-Speed-31.webp)

<mark>

A=B=1->0 的情况是，上拉的两个PMOS并联，电阻小，delay小

</mark>



<mark>

A=1，B=1->0的情况是，下拉电路中B关断，AB两管之间的电容会被充电，延时增强

</mark>



### Faster Design: Sizing —— 用 progressive sizing 加速

P41 开始讲复杂门怎么设计得更快。

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mtext>

靠近输出NMOS小：减小电容

</mtext>
</mrow>

<annotation encoding="application/x-tex">

\text{靠近输出NMOS小：减小电容}

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

靠近输出

</span>

<span className="mord">

NMOS

</span>

<span className="mord,cjk_fallback">

小：减小电容

</span>
</span>
</span>
</span>
</span>
</span>

<mark>

输出节点电容在 delay 中权重最大，因为输出电容要经过整个下拉路径放电。

</mark>



<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mtext>

靠近地NOMS大：减小电阻

</mtext>
</mrow>

<annotation encoding="application/x-tex">

\text{靠近地NOMS大：减小电阻}

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

靠近地

</span>

<span className="mord">

NOMS

</span>

<span className="mord,cjk_fallback">

大：减小电阻

</span>
</span>
</span>
</span>
</span>
</span>

靠近 GND 的 NMOS 虽然变大会增加内部节点电容，但这些内部节点电容在 Elmore delay 里的权重较小。

<mark>

同时，把底部 NMOS 做大可以减少串联路径电阻。

</mark>



#### Sizing 例子比较 —— 12RC vs 137/12RC

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter8-Speed-32.webp)

---

### P43：Faster Design: Topology —— 拓扑结构也影响速度

P43 讨论 **alternative logic designs**，也就是同一个逻辑功能可以用不同门级结构实现。课件要求比较哪个更快，并提示用 Elmore delay 计算 worst-case delay。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter8-Speed-33.webp)

直接用一个大 fan-in 门虽然逻辑级数少，但串联晶体管太多，等效电阻和内部寄生电容都很大，所以 worst-case delay 可能反而很慢。把大 fan-in 逻辑适当拆成中等 fan-in 的多级结构，通常可以在“单级门太慢”和“级数太多”之间取得折中。因此图中通常<mark>

右下角结构最快

</mark>

：它避免了右上角 <mark>

8-input NAND 的大 fan-in 问题

</mark>

，也避免了<mark>

左边结构逻辑级数过多

</mark>

的问题。

> 同一个布尔函数，不同拓扑的 delay 可能差很多。

---

### P44：Faster Design: Transistor Ordering —— 晶体管排序

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter8-Speed-34.webp)

左图：0->1的时候，它需要将输出以及中间节点的所有电容上的电荷全部放掉

右图：0->1的时候，它只需要放掉输出节点的电荷

> 如果某个输入在 critical path 上，并且它的 <mark>
> 
> 0→1 变化
> 
> </mark>
> 
> 触发输出下降，通常希望把它对应的 <mark>
> 
> NMOS 放在靠近输出的位置。
> 
> </mark>
> 
> 这样可以减少它触发切换时需要一起放电的内部寄生电容。

---

### P45：Faster Design: Buffer Insertion —— 插 buffer 隔离 fanin 和 fanout<mark>（最有效）</mark>

P45 讲 buffer insertion。课件说：用 buffer insertion 隔离 fanin 和 fanout，为什么以及怎么做，后面会在 logical effort 中进一步理解。<mark>

（后面重点讲）

</mark>



![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter8-Speed-35.webp)

---

### P46：Key Take-Aways —— 第三板块总结

P46 总结了第三板块的重点：

复杂门的 delay 会随着 fan-in 增加快速恶化；input pattern 会影响复杂门 delay，尤其当寄生电容较大时更明显；实际设计通常更关心 worst-case delay；加速复杂门的经验方法包括 <mark>

progressive sizing    transistor ordering    topology optimization 和 buffer insertion。

</mark>



---

## **四：现代标准单元中的 delay 建模，P47–P51（说不考）**

---

### P48：Standard Cell —— 什么是标准单元？

P48 说：在数字设计中，大多数时候我们处理的是 **standard cells（预设好的逻辑单元）**

---

### P49：Standard Cell Library —— 标准单元库里有什么？

P49 讲的是 **standard cell library** 的组织方式。

课件说：对于每个 combinational cell family，会有：

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

×

</mo>

<mi>

N

</mi>
</mrow>

<annotation encoding="application/x-tex">

M \times N

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

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

<span className="mord,mathnormal" style="margin-right:0.109em;">

N

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

：不同 threshold voltage，也就是不同 <span className="katex">
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

；
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

：每种 <span className="katex">
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

 下的不同尺寸。

---

### P50：Cell Delay —— cell delay 不是固定值

---

### P51：Interconnect Delay —— 互连延迟让问题更复杂

---

## **五：Logical Effort 基础，P52–P71**<mark>

**（最重要）**

</mark>



<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

d

</mi>

<mo>

=

</mo>

<mi>

g

</mi>

<mi>

h

</mi>

<mo>

+

</mo>

<mi>

p

</mi>
</mrow>

<annotation encoding="application/x-tex">

d = gh + p

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,mathnormal">

d

</span>

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

<span className="mord,mathnormal" style="margin-right:0.0359em;">

g

</span>

<span className="mord,mathnormal">

h

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
<span className="strut" style="height:0.625em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal">

p

</span>
</span>
</span>
</span>
</span>

也就是：

> 一个门的 delay = 逻辑复杂度带来的努力 + 负载带来的努力 + 自身寄生延迟。

---

### P53：History of Logic Effort —— Logical Effort 的背景

---

### P54：Sizing Logic Paths for Speed —— 路径 sizing 的问题

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mtext>

inverter chain （反向器）的思想推广到任意逻辑（复杂逻辑门）

</mtext>
</mrow>

<annotation encoding="application/x-tex">

\text{ inverter chain （反向器）的思想推广到任意逻辑（复杂逻辑门）}

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

inverter chain

</span>

<span className="mord,cjk_fallback">

（反向器）的思想推广到任意逻辑（复杂逻辑门）

</span>
</span>
</span>
</span>
</span>
</span>

---

### P55：More for Speed —— 设计者面对哪些选择？

Logical Effort 是用来在拓扑、级数、尺寸之间快速做速度优化的。

---

### P56：Revisit: Inverter Delay —— 从反相器 delay 重新拆分

P56 回到反相器，把负载电容分成两部分：

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

L

</mi>
</msub>

<mo>

=

</mo>

<msub>
<mi>

C

</mi>

<mrow>
<mi>

i

</mi>

<mi>

n

</mi>

<mi>

t

</mi>
</mrow>
</msub>

<mo>

+

</mo>

<msub>
<mi>

C

</mi>

<mrow>
<mi>

e

</mi>

<mi>

x

</mi>

<mi>

t

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

C_L = C_{int} + C_{ext}

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

in

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

C

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

e

</span>

<span className="mord,mathnormal,mtight">

x

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
</span>

其中：

<span className="katex">
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

n

</mi>

<mi>

t

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

C_{int}

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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

in

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

 是 intrinsic parasitic capacitance，<mark>

主要来自 diffusion 等内部寄生电容。

</mark>



<span className="katex">
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

e

</mi>

<mi>

x

</mi>

<mi>

t

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

C_{ext}

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
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

e

</span>

<span className="mord,mathnormal,mtight">

x

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

 是 extrinsic load capacitance，<mark>

主要来自 wiring 和 fanout。

</mark>



课件给出：<span className="katex">
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

<mo>

=

</mo>

<mn>

0.69

</mn>

<msub>
<mi>

R

</mi>

<mrow>
<mi>

e

</mi>

<mi>

q

</mi>
</mrow>
</msub>

<msub>
<mi>

C

</mi>

<mrow>
<mi>

i

</mi>

<mi>

n

</mi>

<mi>

t

</mi>
</mrow>
</msub>

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

e

</mi>

<mi>

x

</mi>

<mi>

t

</mi>
</mrow>
</msub>

<msub>
<mi>

C

</mi>

<mrow>
<mi>

i

</mi>

<mi>

n

</mi>

<mi>

t

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

t_p = 0.69R_{eq}C_{int}\left(1+\frac{C_{ext}}{C_{int}}\right)

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

<span className="mord">

0.69

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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

e

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

q

</span>
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

in

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
<span className="vlist" style="height:0.8884em;">
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
<span className="vlist" style="height:0.3281em;">
<span style="top:-2.357em;margin-left:-0.0715em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

in

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

<span style="top:-3.4101em;">
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
<span className="vlist" style="height:0.2963em;">
<span style="top:-2.357em;margin-left:-0.0715em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

e

</span>

<span className="mord,mathnormal,mtight">

x

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



也可以写成：<span className="katex">
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

<mo>

=

</mo>

<mn>

0.69

</mn>

<msub>
<mi>

R

</mi>

<mrow>
<mi>

e

</mi>

<mi>

q

</mi>
</mrow>
</msub>

<msub>
<mi>

C

</mi>

<mrow>
<mi>

i

</mi>

<mi>

n

</mi>

<mi>

t

</mi>
</mrow>
</msub>

<mo>

+

</mo>

<mn>

0.69

</mn>

<msub>
<mi>

R

</mi>

<mrow>
<mi>

e

</mi>

<mi>

q

</mi>
</mrow>
</msub>

<msub>
<mi>

C

</mi>

<mrow>
<mi>

e

</mi>

<mi>

x

</mi>

<mi>

t

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

t_p = 0.69R_{eq}C_{int} + 0.69R_{eq}C_{ext}

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

0.69

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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

e

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

q

</span>
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

in

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

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.9694em;vertical-align:-0.2861em;">



</span>

<span className="mord">

0.69

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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

e

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

q

</span>
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
<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

e

</span>

<span className="mord,mathnormal,mtight">

x

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



这两个部分含义不同：

<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mn>

0.69

</mn>

<msub>
<mi>

R

</mi>

<mrow>
<mi>

e

</mi>

<mi>

q

</mi>
</mrow>
</msub>

<msub>
<mi>

C

</mi>

<mrow>
<mi>

i

</mi>

<mi>

n

</mi>

<mi>

t

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

0.69R_{eq}C_{int}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9694em;vertical-align:-0.2861em;">



</span>

<span className="mord">

0.69

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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

e

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

q

</span>
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

in

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

  是门本身的 intrinsic delay，也叫 **parasitic delay**。

<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mn>

0.69

</mn>

<msub>
<mi>

R

</mi>

<mrow>
<mi>

e

</mi>

<mi>

q

</mi>
</mrow>
</msub>

<msub>
<mi>

C

</mi>

<mrow>
<mi>

e

</mi>

<mi>

x

</mi>

<mi>

t

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

0.69R_{eq}C_{ext}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9694em;vertical-align:-0.2861em;">



</span>

<span className="mord">

0.69

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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

e

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

q

</span>
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
<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

e

</span>

<span className="mord,mathnormal,mtight">

x

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

  是外部负载造成的 delay，也叫 **effort delay**。

> delay 可以拆成“自身寄生造成的固定部分”和“驱动外部负载造成的可变部分”。

这就是后面：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

d

</mi>

<mo>

=

</mo>

<mi>

f

</mi>

<mo>

+

</mo>

<mi>

p

</mi>
</mrow>

<annotation encoding="application/x-tex">

d = f + p

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,mathnormal">

d

</span>

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

<span className="mord,mathnormal" style="margin-right:0.1076em;">

f

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
<span className="strut" style="height:0.625em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal">

p

</span>
</span>
</span>
</span>

  的来源。

---

### P57：Buffer Example —— 用 buffer chain 引出 g、p、f

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter8-Speed-36.webp)

P57 用一个 buffer chain 说明后面要用的三个符号：

<span className="katex">
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

 表示 intrinsic delay，也就是 parasitic delay。

<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

g

</mi>
</mrow>

<annotation encoding="application/x-tex">

g

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.625em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

g

</span>
</span>
</span>
</span>

 表示 logical effort

<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

f

</mi>
</mrow>

<annotation encoding="application/x-tex">

f

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1076em;">

f

</span>
</span>
</span>
</span>

 表示 effective fanout，或者 stage effort。

课件右边说：<span className="katex">
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

<mo>

=

</mo>

<mn>

1

</mn>

<mo separator="true">

,

</mo>

<mspace width="1em">



</mspace>

<msub>
<mi>

p

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

<mo>

=

</mo>

<mn>

1

</mn>
</mrow>

<annotation encoding="application/x-tex">

g_{inv}=1,\quad p_{inv}=1

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
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
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

1

</span>

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:1em;">



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
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
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



意思是：所有东西都归一化到反相器。

---

### P58：Delay in a Logic Gate —— 逻辑门 delay 的核心公式

<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

d

</mi>

<mo>

=

</mo>

<mi>

g

</mi>

<mi>

h

</mi>

<mo>

+

</mo>

<mi>

p

</mi>
</mrow>

<annotation encoding="application/x-tex">

d = gh + p

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,mathnormal">

d

</span>

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

<span className="mord,mathnormal" style="margin-right:0.0359em;">

g

</span>

<span className="mord,mathnormal">

h

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
<span className="strut" style="height:0.625em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal">

p

</span>
</span>
</span>
</span>

·

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter8-Speed-37.webp)

1. <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

g

</mi>
</mrow>

<annotation encoding="application/x-tex">

g

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.625em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

g

</span>
</span>
</span>
</span>

：logical effort

  1. 衡量这个门相对于反相器来说，驱动电流的能力有多“吃力”。
  2. 相当于门本身的性质，越复杂，g越大
2. <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

h

</mi>
</mrow>

<annotation encoding="application/x-tex">

h

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,mathnormal">

h

</span>
</span>
</span>
</span>

：electrical effort  <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

h

</mi>

<mo>

=

</mo>

<mfrac>
<msub>
<mi>

C

</mi>

<mrow>
<mi>

o

</mi>

<mi>

u

</mi>

<mi>

t

</mi>
</mrow>
</msub>

<msub>
<mi>

C

</mi>

<mrow>
<mi>

i

</mi>

<mi>

n

</mi>
</mrow>
</msub>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

h = \frac{C_{out}}{C_{in}}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,mathnormal">

h

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.3335em;vertical-align:-0.4451em;">



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
<span className="mord,mathnormal,mtight" style="margin-right:0.0715em;">

C

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3281em;">
<span style="top:-2.357em;margin-left:-0.0715em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

in

</span>
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

<span style="top:-3.4101em;">
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
<span className="vlist" style="height:0.2963em;">
<span style="top:-2.357em;margin-left:-0.0715em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

o

</span>

<span className="mord,mathnormal,mtight">

u

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
3. 它表示输出负载电容和输入电容之比，也常被叫作 fanout。（尝试驱动几倍于自身的吨位，可以当作是fanout）
4. <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

f

</mi>
</mrow>

<annotation encoding="application/x-tex">

f

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1076em;">

f

</span>
</span>
</span>
</span>

：effort delay
5. <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

f

</mi>

<mo>

=

</mo>

<mi>

g

</mi>

<mi>

h

</mi>
</mrow>

<annotation encoding="application/x-tex">

f=gh

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1076em;">

f

</span>

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

<span className="mord,mathnormal" style="margin-right:0.0359em;">

g

</span>

<span className="mord,mathnormal">

h

</span>
</span>
</span>
</span>
6. 它表示这个 stage 真正承担的“努力”。
7. <span className="katex">
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

：parasitic delay
8. 表示无外部负载时，门自身内部寄生造成的 delay。也是门本身的性质

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<menclose notation="box">
<mstyle scriptlevel="0" displaystyle="false">
<mstyle scriptlevel="0" displaystyle="false">
<mstyle scriptlevel="0" displaystyle="true">
<mrow>
<mi>

d

</mi>

<mo>

=

</mo>

<mi>

g

</mi>

<mi>

h

</mi>

<mo>

+

</mo>

<mi>

p

</mi>
</mrow>
</mstyle>
</mstyle>
</mstyle>
</menclose>
</mrow>

<annotation encoding="application/x-tex">

\boxed{d=gh+p}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.5689em;vertical-align:-0.5344em;">



</span>

<span className="mord">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:1.0344em;">
<span style="top:-3.5689em;">
<span className="pstrut" style="height:3.5689em;">



</span>

<span className="boxpad">
<span className="mord">
<span className="mord">
<span className="mord,mathnormal">

d

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

g

</span>

<span className="mord,mathnormal">

h

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mord,mathnormal">

p

</span>
</span>
</span>
</span>
</span>

<span style="top:-3.0344em;">
<span className="pstrut" style="height:3.5689em;">



</span>

<span className="stretchy,fbox" style="height:1.5689em;border-style:solid;border-width:0.04em;">



</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.5344em;">
<span>



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
<menclose notation="box">
<mstyle scriptlevel="0" displaystyle="false">
<mstyle scriptlevel="0" displaystyle="false">
<mstyle scriptlevel="0" displaystyle="true">
<mrow>
<mtext>

总延迟

</mtext>

<mo>

=

</mo>

<mtext>

驱动负载的延迟

</mtext>

<mo>

+

</mo>

<mtext>

门自身寄生延迟

</mtext>
</mrow>
</mstyle>
</mstyle>
</mstyle>
</menclose>
</mrow>

<annotation encoding="application/x-tex">

\boxed{\text{总延迟}=\text{驱动负载的延迟}+\text{门自身寄生延迟}}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.4467em;vertical-align:-0.4233em;">



</span>

<span className="mord">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:1.0233em;">
<span style="top:-3.4467em;">
<span className="pstrut" style="height:3.4467em;">



</span>

<span className="boxpad">
<span className="mord">
<span className="mord">
<span className="mord,text">
<span className="mord,cjk_fallback">

总延迟

</span>
</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mord,text">
<span className="mord,cjk_fallback">

驱动负载的延迟

</span>
</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mord,text">
<span className="mord,cjk_fallback">

门自身寄生延迟

</span>
</span>
</span>
</span>
</span>
</span>

<span style="top:-3.0233em;">
<span className="pstrut" style="height:3.4467em;">



</span>

<span className="stretchy,fbox" style="height:1.4467em;border-style:solid;border-width:0.04em;">



</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.4233em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

### Understand Logical Effort —— 为什么叫 effort？

课件说：对于同样的负载，复杂门比 inverter 更“费力”，才能达到类似速度。Logical effort 定义为：

> 在提供相同输出电流能力的前提下，某个逻辑门的输入电容与反相器输入电容的比值。

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

g

</mi>

<mo>

=

</mo>

<mfrac>
<msub>
<mi>

C

</mi>

<mrow>
<mi>

i

</mi>

<mi>

n

</mi>

<mo separator="true">

,

</mo>

<mtext>



</mtext>

<mi>

g

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
</msub>

<msub>
<mi>

C

</mi>

<mrow>
<mi>

i

</mi>

<mi>

n

</mi>

<mo separator="true">

,

</mo>

<mtext>



</mtext>

<mi>

i

</mi>

<mi>

n

</mi>

<mi>

v

</mi>

<mi>

e

</mi>

<mi>

r

</mi>

<mi>

t

</mi>

<mi>

e

</mi>

<mi>

r

</mi>
</mrow>
</msub>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

g = \frac{C_{in,\ gate}}{C_{in,\ inverter}}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.625em;vertical-align:-0.1944em;">



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
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

in

</span>

<span className="mpunct,mtight">

,

</span>

<span className="mspace,mtight">
<span className="mtight">



</span>
</span>

<span className="mord,mathnormal,mtight">

in

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

v

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

er

</span>

<span className="mord,mathnormal,mtight">

t

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
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

in

</span>

<span className="mpunct,mtight">

,

</span>

<span className="mspace,mtight">
<span className="mtight">



</span>
</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

g

</span>

<span className="mord,mathnormal,mtight">

a

</span>

<span className="mord,mathnormal,mtight">

t

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

逻辑越复杂

</mtext>

<mo>

⇒

</mo>

<msub>
<mi>

C

</mi>

<mrow>
<mi>

i

</mi>

<mi>

n

</mi>
</mrow>
</msub>

<mtext>

越大

</mtext>

<mo>

⇒

</mo>

<mi>

g

</mi>

<mtext>

越大

</mtext>
</mrow>

<annotation encoding="application/x-tex">

\text{逻辑越复杂} \Rightarrow C_{in}\text{ 越大} \Rightarrow g\text{ 越大}

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

逻辑越复杂

</span>
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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

in

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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

越大

</span>
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
<span className="strut" style="height:0.8778em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

g

</span>

<span className="mord,text">
<span className="mord">



</span>

<span className="mord,cjk_fallback">

越大

</span>
</span>
</span>
</span>
</span>
</span>

> logical effort 衡量的是“为了实现某种逻辑功能，相比 inverter 多付出了多少输入电容代价”。

---

### Computing Logical Effort —— 怎么计算 logical effort？（依旧套用P24的基准）

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter8-Speed-38.webp)

1. Inverter：<span className="katex">
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

n

</mi>
</mrow>
</msub>

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

2

</mn>

<mo>

=

</mo>

<mn>

3

</mn>
</mrow>

<annotation encoding="application/x-tex">

C_{in}=1+2=3

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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

in

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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

3

</span>
</span>
</span>
</span>
2. 定义：<span className="katex">
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

<mo>

=

</mo>

<mn>

1

</mn>
</mrow>

<annotation encoding="application/x-tex">

g_{inv}=1

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
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
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

---

1. 2-input NAND
2. <span className="katex">
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

n

</mi>
</mrow>
</msub>

<mo>

=

</mo>

<mn>

2

</mn>

<mo>

+

</mo>

<mn>

2

</mn>

<mo>

=

</mo>

<mn>

4

</mn>
</mrow>

<annotation encoding="application/x-tex">

C_{in}=2+2=4

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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

in

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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
<span className="strut" style="height:0.7278em;vertical-align:-0.0833em;">



</span>

<span className="mord">

2

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

4

</span>
</span>
</span>
</span>
3. <span className="katex">
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

N

</mi>

<mi>

A

</mi>

<mi>

N

</mi>

<mi>

D

</mi>

<mn>

2

</mn>
</mrow>
</msub>

<mo>

=

</mo>

<mfrac>
<mn>

4

</mn>

<mn>

3

</mn>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

g_{NAND2}=\frac{4}{3}

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
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.109em;">

N

</span>

<span className="mord,mathnormal,mtight">

A

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.109em;">

N

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

D

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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

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

4

</span>
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

1. 2-input NOR
2. <span className="katex">
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

n

</mi>
</mrow>
</msub>

<mo>

=

</mo>

<mn>

4

</mn>

<mo>

+

</mo>

<mn>

1

</mn>

<mo>

=

</mo>

<mn>

5

</mn>
</mrow>

<annotation encoding="application/x-tex">

C_{in}=4+1=5

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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

in

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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
<span className="strut" style="height:0.7278em;vertical-align:-0.0833em;">



</span>

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

5

</span>
</span>
</span>
</span>
3. <span className="katex">
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

N

</mi>

<mi>

O

</mi>

<mi>

R

</mi>

<mn>

2

</mn>
</mrow>
</msub>

<mo>

=

</mo>

<mfrac>
<mn>

5

</mn>

<mn>

3

</mn>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

g_{NOR2}=\frac{5}{3}

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
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.109em;">

N

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

O

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0077em;">

R

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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

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

5

</span>
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

<mark>

所以 NOR2 比 NAND2 的 logical effort 更大：NOR 通常比 NAND 更“费力”

</mark>



---

### P61：Delay Plots —— delay 图怎么看？

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter8-Speed-39.webp)

### P62：Catalog of Gates —— 常见门的 logical effort<mark>（g）</mark>

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter8-Speed-40.webp)

**为什么 NOR 比 NAND 差？**

<mark>

因为 NOR 的 PMOS 是串联的，而 PMOS 本身迁移率低、驱动弱。为了匹配驱动能力，需要把 PMOS 做得更宽，导致输入电容明显增加。

</mark>



因此在 CMOS 设计中，大 fan-in NOR 通常比大 fan-in NAND 更慢、更不划算。

---

### P63：Catalog of Gates —— 常见门的 parasitic delay

P63 给出常见门的 parasitic delay 表。课件说，一个门的 parasitic delay 是它驱动零负载时的 delay；手算时可以粗略只数输出节点上的 diffusion capacitance。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter8-Speed-41.webp)

---

### P64：Parasitic Delay —— 高 fan-in 门的寄生延迟增长

P64 用更细的 RC ladder 模型估算高 fan-in NAND 的寄生延迟。

图里有一个 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

n

</mi>
</mrow>

<annotation encoding="application/x-tex">

n

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.4306em;">



</span>

<span className="mord,mathnormal">

n

</span>
</span>
</span>
</span>

-input NAND，下拉网络有 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

n

</mi>
</mrow>

<annotation encoding="application/x-tex">

n

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.4306em;">



</span>

<span className="mord,mathnormal">

n

</span>
</span>
</span>
</span>

 个串联 NMOS。为了保持总电阻不变，每个 NMOS 放大到宽度 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

n

</mi>
</mrow>

<annotation encoding="application/x-tex">

n

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.4306em;">



</span>

<span className="mord,mathnormal">

n

</span>
</span>
</span>
</span>

，所以每个 NMOS 的电阻约为：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mfrac>
<mi>

R

</mi>

<mi>

n

</mi>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

\frac{R}{n}

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
<span className="mord,mathnormal">

n

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
<span className="mord,mathnormal" style="margin-right:0.0077em;">

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

但这样会导致内部节点电容增加为：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

n

</mi>

<mi>

C

</mi>
</mrow>

<annotation encoding="application/x-tex">

nC

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal">

n

</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>
</span>
</span>
</span>
</span>

输出节点还要看到 PMOS 和 NMOS 的扩散电容，大约有：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mn>

3

</mn>

<mi>

n

</mi>

<mi>

C

</mi>
</mrow>

<annotation encoding="application/x-tex">

3nC

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord">

3

</span>

<span className="mord,mathnormal">

n

</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>
</span>
</span>
</span>
</span>

课件给出的估算式是：

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

d

</mi>
</mrow>
</msub>

<mo>

=

</mo>

<mi>

R

</mi>

<mo stretchy="false">

(

</mo>

<mn>

3

</mn>

<mi>

n

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

1

</mn>
</mrow>

<mrow>
<mi>

n

</mi>

<mo>

−

</mo>

<mn>

1

</mn>
</mrow>
</munderover>

<mrow>
<mo fence="true">

(

</mo>

<mfrac>
<mrow>
<mi>

i

</mi>

<mi>

R

</mi>
</mrow>

<mi>

n

</mi>
</mfrac>

<mo fence="true">

)

</mo>
</mrow>

<mo stretchy="false">

(

</mo>

<mi>

n

</mi>

<mi>

C

</mi>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

t_{pd}=R(3nC)+\sum_{i=1}^{n-1}\left(\frac{iR}{n}\right)(nC)

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

p

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

<span className="mord,mathnormal" style="margin-right:0.0077em;">

R

</span>

<span className="mopen">

(

</span>

<span className="mord">

3

</span>

<span className="mord,mathnormal">

n

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
<span className="strut" style="height:3.0788em;vertical-align:-1.2777em;">



</span>

<span className="mop,op-limits">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:1.8011em;">
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

1

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
<span className="mord,mathnormal,mtight">

n

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
<span className="mord,mathnormal">

n

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

i

</span>

<span className="mord,mathnormal" style="margin-right:0.0077em;">

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

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mopen">

(

</span>

<span className="mord,mathnormal">

n

</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="mclose">

)

</span>
</span>
</span>
</span>
</span>

化简为：

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

d

</mi>
</mrow>
</msub>

<mo>

=

</mo>

<mrow>
<mo fence="true">

(

</mo>

<mfrac>
<msup>
<mi>

n

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

<mfrac>
<mrow>
<mn>

5

</mn>

<mi>

n

</mi>
</mrow>

<mn>

2

</mn>
</mfrac>

<mo fence="true">

)

</mo>
</mrow>

<mi>

R

</mi>

<mi>

C

</mi>
</mrow>

<annotation encoding="application/x-tex">

t_{pd}=\left(\frac{n^2}{2}+\frac{5n}{2}\right)RC

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

p

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
<span className="strut" style="height:2.4411em;vertical-align:-0.95em;">



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
<span className="mord,mathnormal">

n

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

5

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

<span className="mclose,delimcenter" style="top:0em;">
<span className="delimsizing,size3">

)

</span>
</span>
</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0077em;">

R

</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>
</span>
</span>
</span>
</span>

这说明 parasitic delay 会随着 fan-in 增加得很快，里面出现了：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mfrac>
<msup>
<mi>

n

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

\frac{n^2}{2}

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
<span className="mord,mathnormal">

n

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

也就是二次增长趋势。

课件还写了：

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

:

</mo>

<mn>

4

</mn>

<mo>

∼

</mo>

<mn>

5

</mn>
</mrow>

<annotation encoding="application/x-tex">

N:4\sim 5

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

:

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

5

</span>
</span>
</span>
</span>
</span>

意思是高 fan-in 门通常不要做得太大。输入数到 4 或 5 以上，delay 代价已经明显变差。

这一页的核心结论是：

> fan-in 很大的单级复杂门通常不是好选择，因为内部寄生 delay 会快速增长。

---

### P65：Example – 8-input AND —— 重新理解 8 输入 AND

仅引入，具体看后面

---

### P66：Example: Ring Oscillator —— 环形振荡器例子

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter8-Speed-42.webp)

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

d

</mi>

<mo>

=

</mo>

<mi>

g

</mi>

<mi>

h

</mi>

<mo>

+

</mo>

<mi>

p

</mi>

<mo>

=

</mo>

<mn>

1

</mn>

<mo>

⋅

</mo>

<mn>

1

</mn>

<mo>

+

</mo>

<mn>

1

</mn>

<mo>

=

</mo>

<mn>

2

</mn>
</mrow>

<annotation encoding="application/x-tex">

d=gh+p=1\cdot 1+1=2

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,mathnormal">

d

</span>

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

<span className="mord,mathnormal" style="margin-right:0.0359em;">

g

</span>

<span className="mord,mathnormal">

h

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
<span className="strut" style="height:0.625em;vertical-align:-0.1944em;">



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

1

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

2

</span>
</span>
</span>
</span>
</span>

环形振荡器的周期需要信号绕环传播两次，因为一次传播只完成半个周期翻转，所以：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

f

</mi>

<mrow>
<mi>

o

</mi>

<mi>

s

</mi>

<mi>

c

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

2

</mn>

<mi>

N

</mi>

<mi>

d

</mi>
</mrow>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

f_{osc}=\frac{1}{2Nd}

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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

osc

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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

2

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.109em;">

N

</span>

<span className="mord,mathnormal,mtight">

d

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



代入：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

d

</mi>

<mo>

=

</mo>

<mn>

2

</mn>
</mrow>

<annotation encoding="application/x-tex">

d=2

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,mathnormal">

d

</span>

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



得到：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

f

</mi>

<mrow>
<mi>

o

</mi>

<mi>

s

</mi>

<mi>

c

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

4

</mn>

<mi>

N

</mi>
</mrow>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

f_{osc}=\frac{1}{4N}

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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

osc

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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

4

</span>

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

### P67：Example: FO4 Inverter —— FO4 反相器延迟

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter8-Speed-43.webp)

FO4 的意思是：

> 一个 inverter 驱动 4 个同样大小 inverter 的输入电容。d=5

所以：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

g

</mi>

<mo>

=

</mo>

<mn>

1

</mn>
</mrow>

<annotation encoding="application/x-tex">

g=1

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.625em;vertical-align:-0.1944em;">



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

1

</span>
</span>
</span>
</span>

h=4<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

p

</mi>

<mo>

=

</mo>

<mn>

1

</mn>
</mrow>

<annotation encoding="application/x-tex">

p=1

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



因此：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

d

</mi>

<mo>

=

</mo>

<mi>

g

</mi>

<mi>

h

</mi>

<mo>

+

</mo>

<mi>

p

</mi>

<mo>

=

</mo>

<mn>

1

</mn>

<mo>

⋅

</mo>

<mn>

4

</mn>

<mo>

+

</mo>

<mn>

1

</mn>

<mo>

=

</mo>

<mn>

5

</mn>
</mrow>

<annotation encoding="application/x-tex">

d=gh+p=1\cdot4+1=5

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,mathnormal">

d

</span>

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

<span className="mord,mathnormal" style="margin-right:0.0359em;">

g

</span>

<span className="mord,mathnormal">

h

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
<span className="strut" style="height:0.625em;vertical-align:-0.1944em;">



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

1

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
<span className="strut" style="height:0.7278em;vertical-align:-0.0833em;">



</span>

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

5

</span>
</span>
</span>
</span>
</span>

d=5 可能要记

---

### P68：Multistage Logic Path Delay —— 多级路径 delay

P68 把单级公式推广到多级逻辑路径。课件给出几个路径级别的量：parasitic delay、path logical effort、path electrical effort、path effort。

1. Path parasitic delay    <span className="katex">
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

<mo>

∑

</mo>

<msub>
<mi>

p

</mi>

<mi>

i

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

P=\sum p_i

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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mop,op-symbol,small-op" style="position:relative;top:0em;">

∑

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
2. 就是路径上每一级门的 parasitic delay 相加。
3. Path logical effort
4. <span className="katex">
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

<mo>

∏

</mo>

<msub>
<mi>

g

</mi>

<mi>

i

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

G=\prod g_i

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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mop,op-symbol,small-op" style="position:relative;top:0em;">

∏

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

g

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
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
5. 就是路径上每一级门的 logical effort 相乘。
6. Path electrical effort     <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

H

</mi>

<mo>

=

</mo>

<mfrac>
<msub>
<mi>

C

</mi>

<mrow>
<mi>

o

</mi>

<mi>

u

</mi>

<mi>

t

</mi>

<mo>

−

</mo>

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

h

</mi>
</mrow>
</msub>

<msub>
<mi>

C

</mi>

<mrow>
<mi>

i

</mi>

<mi>

n

</mi>

<mo>

−

</mo>

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

h

</mi>
</mrow>
</msub>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

H=\frac{C_{out-path}}{C_{in-path}}

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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.5395em;vertical-align:-0.5481em;">



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
<span className="vlist" style="height:0.3448em;">
<span style="top:-2.3488em;margin-left:-0.0715em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

in

</span>

<span className="mbin,mtight">

−

</span>

<span className="mord,mathnormal,mtight">

p

</span>

<span className="mord,mathnormal,mtight">

a

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

o

</span>

<span className="mord,mathnormal,mtight">

u

</span>

<span className="mord,mathnormal,mtight">

t

</span>

<span className="mbin,mtight">

−

</span>

<span className="mord,mathnormal,mtight">

p

</span>

<span className="mord,mathnormal,mtight">

a

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
<span className="vlist" style="height:0.5481em;">
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
7. 也就是路径最终输出负载和路径最初输入电容的比值。（其实相当于每一级的h相乘）
8. Path effort（无分支）
9. <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

F

</mi>

<mo>

=

</mo>

<mo>

∏

</mo>

<msub>
<mi>

f

</mi>

<mi>

i

</mi>
</msub>

<mo>

=

</mo>

<mo>

∏

</mo>

<msub>
<mi>

g

</mi>

<mi>

i

</mi>
</msub>

<msub>
<mi>

h

</mi>

<mi>

i

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

F=\prod f_i=\prod g_i h_i

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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mop,op-symbol,small-op" style="position:relative;top:0em;">

∏

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.1076em;">

f

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.1076em;margin-right:0.05em;">
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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mop,op-symbol,small-op" style="position:relative;top:0em;">

∏

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

g

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
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
<span className="mord,mathnormal">

h

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
10. 总delay

  1. <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mi>
  
  D
  
  </mi>
  
  <mo>
  
  =
  
  </mo>
  
  <mo>
  
  ∑
  
  </mo>
  
  <msub>
  <mi>
  
  f
  
  </mi>
  
  <mi>
  
  i
  
  </mi>
  </msub>
  
  <mo>
  
  +
  
  </mo>
  
  <mi>
  
  P
  
  </mi>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  D=\sum f_i+P
  
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
  
  <span className="mop,op-symbol,small-op" style="position:relative;top:0em;">
  
  ∑
  
  </span>
  
  <span className="mspace" style="margin-right:0.1667em;">
  
  
  
  </span>
  
  <span className="mord">
  <span className="mord,mathnormal" style="margin-right:0.1076em;">
  
  f
  
  </span>
  
  <span className="msupsub">
  <span className="vlist-t,vlist-t2">
  <span className="vlist-r">
  <span className="vlist" style="height:0.3117em;">
  <span style="top:-2.55em;margin-left:-0.1076em;margin-right:0.05em;">
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
  <span className="strut" style="height:0.6833em;">
  
  
  
  </span>
  
  <span className="mord,mathnormal" style="margin-right:0.1389em;">
  
  P
  
  </span>
  </span>
  </span>
  </span>

### P69：Paths that Branch —— 有分支时 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

F

</mi>

<mo>

=

</mo>

<mi>

G

</mi>

<mi>

H

</mi>
</mrow>

<annotation encoding="application/x-tex">

F=GH

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
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal">

G

</span>

<span className="mord,mathnormal" style="margin-right:0.0813em;">

H

</span>
</span>
</span>
</span>

 不一定成立

P69 提醒：路径中如果有分支，不能简单用：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

F

</mi>

<mo>

=

</mo>

<mi>

G

</mi>

<mi>

H

</mi>
</mrow>

<annotation encoding="application/x-tex">

F=GH

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
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal">

G

</span>

<span className="mord,mathnormal" style="margin-right:0.0813em;">

H

</span>
</span>
</span>
</span>



---

### P70：Branching Effort —— 分支努力

P70 正式引入 **branching effort**。

对某一级分支，定义：

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

<mfrac>
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

n

</mi>

<mo>

−

</mo>

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

h

</mi>
</mrow>
</msub>

<mo>

+

</mo>

<msub>
<mi>

C

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

<mo>

−

</mo>

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

h

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

n

</mi>

<mo>

−

</mo>

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

h

</mi>
</mrow>
</msub>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

b=\frac{C_{on-path}+C_{off-path}}{C_{on-path}}

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
<span className="mord,mathnormal,mtight">

o

</span>

<span className="mord,mathnormal,mtight">

n

</span>

<span className="mbin,mtight">

−

</span>

<span className="mord,mathnormal,mtight">

p

</span>

<span className="mord,mathnormal,mtight">

a

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
<span className="mord,mathnormal,mtight">

o

</span>

<span className="mord,mathnormal,mtight">

n

</span>

<span className="mbin,mtight">

−

</span>

<span className="mord,mathnormal,mtight">

p

</span>

<span className="mord,mathnormal,mtight">

a

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
<span className="mord,mathnormal,mtight">

o

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.1076em;">

f

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.1076em;">

f

</span>

<span className="mbin,mtight">

−

</span>

<span className="mord,mathnormal,mtight">

p

</span>

<span className="mord,mathnormal,mtight">

a

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
</span>
</span>
</span>
</span>

其中：

<span className="katex">
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

n

</mi>

<mo>

−

</mo>

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

h

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

C_{on-path}

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
<span className="mord,mathnormal,mtight">

o

</span>

<span className="mord,mathnormal,mtight">

n

</span>

<span className="mbin,mtight">

−

</span>

<span className="mord,mathnormal,mtight">

p

</span>

<span className="mord,mathnormal,mtight">

a

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

 是目标路径上的负载电容。

<span className="katex">
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

f

</mi>

<mi>

f

</mi>

<mo>

−

</mo>

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

h

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

C_{off-path}

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
<span className="mord,mathnormal,mtight">

o

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.1076em;">

f

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.1076em;">

f

</span>

<span className="mbin,mtight">

−

</span>

<span className="mord,mathnormal,mtight">

p

</span>

<span className="mord,mathnormal,mtight">

a

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

 是不在目标路径上、但同样由该门驱动的负载电容。

- 如果没有分支：<span className="katex">
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

f

</mi>

<mi>

f

</mi>

<mo>

−

</mo>

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

h

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

C_{off-path}=0

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
<span className="mord,mathnormal,mtight">

o

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.1076em;">

f

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.1076em;">

f

</span>

<span className="mbin,mtight">

−

</span>

<span className="mord,mathnormal,mtight">

p

</span>

<span className="mord,mathnormal,mtight">

a

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

所以：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

b

</mi>

<mo>

=

</mo>

<mn>

1

</mn>
</mrow>

<annotation encoding="application/x-tex">

b=1

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
<span className="strut" style="height:0.6444em;">



</span>

<span className="mord">

1

</span>
</span>
</span>
</span>



- 如果 off-path 负载和 on-path 负载一样大：

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

<mfrac>
<mrow>
<mi>

C

</mi>

<mo>

+

</mo>

<mi>

C

</mi>
</mrow>

<mi>

C

</mi>
</mfrac>

<mo>

=

</mo>

<mn>

2

</mn>
</mrow>

<annotation encoding="application/x-tex">

b=\frac{C+C}{C}=2

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

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

2

</span>
</span>
</span>
</span>
</span>

整条路径的 branching effort 是：<span className="katex">
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

<mo>

∏

</mo>

<msub>
<mi>

b

</mi>

<mi>

i

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

B=\prod b_i

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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mop,op-symbol,small-op" style="position:relative;top:0em;">

∏

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



<mark>

于是有分支时，path effort 变成：

</mark>

<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

F

</mi>

<mo>

=

</mo>

<mi>

G

</mi>

<mi>

B

</mi>

<mi>

H

</mi>
</mrow>

<annotation encoding="application/x-tex">

F=GBH

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
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0502em;">

GB

</span>

<span className="mord,mathnormal" style="margin-right:0.0813em;">

H

</span>
</span>
</span>
</span>



#### 整道例题

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter8-Speed-44.webp)

<mark>

第二级下面那个反向器改为5

</mark>

，路径不变

- **G（逻辑努力）**：两级都是反相器，<span className="katex">
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

<mn>

1

</mn>

<mo>

×

</mo>

<mn>

1

</mn>

<mo>

=

</mo>

<mn>

1

</mn>
</mrow>

<annotation encoding="application/x-tex">

G = 1×1 = 1

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
<span className="strut" style="height:0.7278em;vertical-align:-0.0833em;">



</span>

<span className="mord">

1

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

1

</span>
</span>
</span>
</span>
- **B（分支努力）**：在分支节点处，上支路输入电容为 15，下支路（修改后）输入电容为 5
<span className="katex">
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

<mfrac>
<mrow>
<mn>

15

</mn>

<mo>

+

</mo>

<mn>

5

</mn>
</mrow>

<mn>

5

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

B=\frac{15+5}{5} =4

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

5

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

15

</span>

<span className="mbin,mtight">

+

</span>

<span className="mord,mtight">

5

</span>
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

4

</span>
</span>
</span>
</span>
- **H（电气努力）**：下支路从第一级输入到最终负载的电容比
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

H

</mi>

<mo>

=

</mo>

<mfrac>
<mn>

90

</mn>

<mn>

5

</mn>
</mfrac>

<mo>

=

</mo>

<mn>

18

</mn>
</mrow>

<annotation encoding="application/x-tex">

H= \frac{90}{5} =18

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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

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

5

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

90

</span>
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

18

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

F

</mi>

<mo>

=

</mo>

<mi>

G

</mi>

<mo>

×

</mo>

<mi>

B

</mi>

<mo>

×

</mo>

<mi>

H

</mi>

<mo>

=

</mo>

<mn>

1

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

18

</mn>

<mo>

=

</mo>

<mn>

72

</mn>
</mrow>

<annotation encoding="application/x-tex">

F=G \times B \times H = 1 \times 4 \times 18 = 72

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
<span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">



</span>

<span className="mord,mathnormal">

G

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

<span className="mord,mathnormal" style="margin-right:0.0502em;">

B

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

<span className="mord,mathnormal" style="margin-right:0.0813em;">

H

</span>

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

×

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

×

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.6444em;">



</span>

<span className="mord">

18

</span>

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

72

</span>
</span>
</span>
</span>
</span>

<alert type="tip">

管子里的数字可以看作管的大小，或者直接当作管子的输入电容

</alert>

---

### Summary on Multistage Delays —— 多级 delay 小结

单级门：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

d

</mi>

<mo>

=

</mo>

<mi>

g

</mi>

<mi>

h

</mi>

<mo>

+

</mo>

<mi>

p

</mi>
</mrow>

<annotation encoding="application/x-tex">

d=gh+p

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,mathnormal">

d

</span>

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

<span className="mord,mathnormal" style="margin-right:0.0359em;">

g

</span>

<span className="mord,mathnormal">

h

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
<span className="strut" style="height:0.625em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal">

p

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

g

</mi>

<mo>

=

</mo>

<mtext>

logical effort

</mtext>
</mrow>

<annotation encoding="application/x-tex">

g=\text{logical effort}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.625em;vertical-align:-0.1944em;">



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
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,text">
<span className="mord">

logical effort

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
<mi>

h

</mi>

<mo>

=

</mo>

<mfrac>
<msub>
<mi>

C

</mi>

<mrow>
<mi>

o

</mi>

<mi>

u

</mi>

<mi>

t

</mi>
</mrow>
</msub>

<msub>
<mi>

C

</mi>

<mrow>
<mi>

i

</mi>

<mi>

n

</mi>
</mrow>
</msub>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

h=\frac{C_{out}}{C_{in}}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,mathnormal">

h

</span>

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

in

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

o

</span>

<span className="mord,mathnormal,mtight">

u

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

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

p

</mi>

<mo>

=

</mo>

<mtext>

parasitic delay

</mtext>
</mrow>

<annotation encoding="application/x-tex">

p=\text{parasitic delay}

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

parasitic delay

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
<mi>

f

</mi>

<mo>

=

</mo>

<mi>

g

</mi>

<mi>

h

</mi>
</mrow>

<annotation encoding="application/x-tex">

f=gh

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1076em;">

f

</span>

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

<span className="mord,mathnormal" style="margin-right:0.0359em;">

g

</span>

<span className="mord,mathnormal">

h

</span>
</span>
</span>
</span>
</span>

多级路径：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

P

</mi>

<mo>

=

</mo>

<mo>

∑

</mo>

<msub>
<mi>

p

</mi>

<mi>

i

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

P=\sum p_i

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
<span className="strut" style="height:1.6em;vertical-align:-0.55em;">



</span>

<span className="mop,op-symbol,large-op" style="position:relative;top:0em;">

∑

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
</span>

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

<mo>

∏

</mo>

<msub>
<mi>

g

</mi>

<mi>

i

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

G=\prod g_i

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
<span className="strut" style="height:1.6em;vertical-align:-0.55em;">



</span>

<span className="mop,op-symbol,large-op" style="position:relative;top:0em;">

∏

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

g

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
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
<mi>

H

</mi>

<mo>

=

</mo>

<mfrac>
<msub>
<mi>

C

</mi>

<mrow>
<mi>

o

</mi>

<mi>

u

</mi>

<mi>

t

</mi>

<mo>

−

</mo>

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

h

</mi>
</mrow>
</msub>

<msub>
<mi>

C

</mi>

<mrow>
<mi>

i

</mi>

<mi>

n

</mi>

<mo>

−

</mo>

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

h

</mi>
</mrow>
</msub>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

H=\frac{C_{out-path}}{C_{in-path}}

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
<span className="mord,mathnormal,mtight">

in

</span>

<span className="mbin,mtight">

−

</span>

<span className="mord,mathnormal,mtight">

p

</span>

<span className="mord,mathnormal,mtight">

a

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
<span className="mord,mathnormal,mtight">

o

</span>

<span className="mord,mathnormal,mtight">

u

</span>

<span className="mord,mathnormal,mtight">

t

</span>

<span className="mbin,mtight">

−

</span>

<span className="mord,mathnormal,mtight">

p

</span>

<span className="mord,mathnormal,mtight">

a

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
</span>
</span>
</span>
</span>

如果有分支：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

B

</mi>

<mo>

=

</mo>

<mo>

∏

</mo>

<msub>
<mi>

b

</mi>

<mi>

i

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

B=\prod b_i

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
<span className="strut" style="height:1.6em;vertical-align:-0.55em;">



</span>

<span className="mop,op-symbol,large-op" style="position:relative;top:0em;">

∏

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
</span>

最终 path effort：

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

<mi>

G

</mi>

<mi>

B

</mi>

<mi>

H

</mi>
</mrow>

<annotation encoding="application/x-tex">

F=GBH

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
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0502em;">

GB

</span>

<span className="mord,mathnormal" style="margin-right:0.0813em;">

H

</span>
</span>
</span>
</span>
</span>

<mark>

这一页实际上是为下一板块做准备：下一板块会讲如何用

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

来确定

</mark>

 <mark>

**最佳级数、最佳 stage effort、最小 delay 和每一级 gate size**

</mark>

<mark>

。

</mark>



## **六：用 Logical Effort 做路径优化，P72–P86**。

> 已知一条路径和负载，怎样选级数、插 buffer、算最小 delay，并反推出每一级门的尺寸？

### P72：Designing Fast Circuits —— 快速电路设计的核心结论（<mark>F已知/级数N已知时</mark>）

这一页给出 Logical Effort 最重要的优化结论：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mtext>

Delay is smallest when each stage bears same effort

</mtext>
</mrow>

<annotation encoding="application/x-tex">

\text{Delay is smallest when each stage bears same effort}

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

Delay is smallest when each stage bears same effort

</span>
</span>
</span>
</span>
</span>

：一条路径最快时，每一级承担的 stage effort 应该相等。

<alert type="tip">

前提是<mark>

F已知

</mark>

的情况下

在总路径 effort <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

F

</mi>

<mo>

=

</mo>

<msub>
<mo>

∏

</mo>

<mi>

i

</mi>
</msub>

<msub>
<mi>

f

</mi>

<mi>

i

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

F=\prod_i f_i

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
<span className="strut" style="height:1.0497em;vertical-align:-0.2997em;">



</span>

<span className="mop">
<span className="mop,op-symbol,small-op" style="position:relative;top:0em;">

∏

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.162em;">
<span style="top:-2.4003em;margin-left:0em;margin-right:0.05em;">
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
<span className="mord,mathnormal" style="margin-right:0.1076em;">

f

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.1076em;margin-right:0.05em;">
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

 已知、级数 <span className="katex">
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

 已知的前提下，路径优化就转化为一个数学问题：在各级 effort 的乘积固定时，怎样分配 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

f

</mi>

<mi>

i

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

f_i

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
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.1076em;margin-right:0.05em;">
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

 才能使 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mo>

∑

</mo>

<mi>

i

</mi>
</msub>

<msub>
<mi>

f

</mi>

<mi>

i

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

\sum_i f_i

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.0497em;vertical-align:-0.2997em;">



</span>

<span className="mop">
<span className="mop,op-symbol,small-op" style="position:relative;top:0em;">

∑

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.162em;">
<span style="top:-2.4003em;margin-left:0em;margin-right:0.05em;">
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
<span className="mord,mathnormal" style="margin-right:0.1076em;">

f

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.1076em;margin-right:0.05em;">
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

 最小。根据算术-几何平均不等式，正数乘积固定时，和在各项相等时取得最小。因此最优情况是每一级承担相同的 stage effort，即 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

f

</mi>

<mn>

1

</mn>
</msub>

<mo>

=

</mo>

<msub>
<mi>

f

</mi>

<mn>

2

</mn>
</msub>

<mo>

=

</mo>

<mo>

⋯

</mo>

<mo>

=

</mo>

<msub>
<mi>

f

</mi>

<mi>

N

</mi>
</msub>

<mo>

=

</mo>

<mover accent="true">
<mi>

f

</mi>

<mo>

^

</mo>
</mover>
</mrow>

<annotation encoding="application/x-tex">

f_1=f_2=\cdots=f_N=\hat f

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
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.1076em;margin-right:0.05em;">
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
<span className="mord,mathnormal" style="margin-right:0.1076em;">

f

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.1076em;margin-right:0.05em;">
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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.3669em;">



</span>

<span className="minner">

⋯

</span>

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
<span className="mord,mathnormal" style="margin-right:0.1076em;">

f

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.1076em;margin-right:0.05em;">
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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.1523em;vertical-align:-0.1944em;">



</span>

<span className="mord,accent">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.9579em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1076em;">

f

</span>
</span>

<span style="top:-3.2634em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.0833em;">
<span className="mord">

^

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.1944em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

，其中 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mover accent="true">
<mi>

f

</mi>

<mo>

^

</mo>
</mover>

<mo>

=

</mo>

<msup>
<mi>

F

</mi>

<mrow>
<mn>

1

</mn>

<mi mathvariant="normal">

/

</mi>

<mi>

N

</mi>
</mrow>
</msup>
</mrow>

<annotation encoding="application/x-tex">

\hat f=F^{1/N}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.1523em;vertical-align:-0.1944em;">



</span>

<span className="mord,accent">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.9579em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1076em;">

f

</span>
</span>

<span style="top:-3.2634em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.0833em;">
<span className="mord">

^

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.1944em;">
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
<span className="strut" style="height:0.888em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.1389em;">

F

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

1/

</span>

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
</span>

。

</alert>

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

D

</mi>

<mo>

=

</mo>

<mo>

∑

</mo>

<msub>
<mi>

f

</mi>

<mi>

i

</mi>
</msub>

<mo>

+

</mo>

<mi>

P

</mi>
</mrow>

<annotation encoding="application/x-tex">

D=\sum f_i+P

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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.6em;vertical-align:-0.55em;">



</span>

<span className="mop,op-symbol,large-op" style="position:relative;top:0em;">

∑

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.1076em;">

f

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.1076em;margin-right:0.05em;">
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
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

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

F

</mi>

<mo>

=

</mo>

<mo>

∏

</mo>

<msub>
<mi>

f

</mi>

<mi>

i

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

F=\prod f_i

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
<span className="strut" style="height:1.6em;vertical-align:-0.55em;">



</span>

<span className="mop,op-symbol,large-op" style="position:relative;top:0em;">

∏

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.1076em;">

f

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.1076em;margin-right:0.05em;">
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

那么当每一级 effort 相等时：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

f

</mi>

<mn>

1

</mn>
</msub>

<mo>

=

</mo>

<msub>
<mi>

f

</mi>

<mn>

2

</mn>
</msub>

<mo>

=

</mo>

<mo>

⋯

</mo>

<mo>

=

</mo>

<msub>
<mi>

f

</mi>

<mi>

N

</mi>
</msub>

<mo>

=

</mo>

<mover accent="true">
<mi>

f

</mi>

<mo>

^

</mo>
</mover>
</mrow>

<annotation encoding="application/x-tex">

f_1=f_2=\cdots=f_N=\hat f

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
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.1076em;margin-right:0.05em;">
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
<span className="mord,mathnormal" style="margin-right:0.1076em;">

f

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.1076em;margin-right:0.05em;">
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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.3669em;">



</span>

<span className="minner">

⋯

</span>

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
<span className="mord,mathnormal" style="margin-right:0.1076em;">

f

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.1076em;margin-right:0.05em;">
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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.1523em;vertical-align:-0.1944em;">



</span>

<span className="mord,accent">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.9579em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1076em;">

f

</span>
</span>

<span style="top:-3.2634em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.0833em;">
<span className="mord">

^

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.1944em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

  D取最小

于是：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mover accent="true">
<mi>

f

</mi>

<mo>

^

</mo>
</mover>

<mo>

=

</mo>

<msup>
<mi>

F

</mi>

<mrow>
<mn>

1

</mn>

<mi mathvariant="normal">

/

</mi>

<mi>

N

</mi>
</mrow>
</msup>
</mrow>

<annotation encoding="application/x-tex">

\hat f=F^{1/N}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.1523em;vertical-align:-0.1944em;">



</span>

<span className="mord,accent">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.9579em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1076em;">

f

</span>
</span>

<span style="top:-3.2634em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.0833em;">
<span className="mord">

^

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.1944em;">
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
<span className="strut" style="height:0.888em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.1389em;">

F

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

1/

</span>

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
</span>

， <mark>

因此多级时最小路径 delay 可以写成：

</mark>

   <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

D

</mi>

<mo>

=

</mo>

<mi>

N

</mi>

<msup>
<mi>

F

</mi>

<mrow>
<mn>

1

</mn>

<mi mathvariant="normal">

/

</mi>

<mi>

N

</mi>
</mrow>
</msup>

<mo>

+

</mo>

<mi>

P

</mi>
</mrow>

<annotation encoding="application/x-tex">

D=NF^{1/N}+P

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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.9713em;vertical-align:-0.0833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

N

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.1389em;">

F

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

1/

</span>

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

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>
</span>
</span>
</span>



---

### P73：Gate Sizes —— 如何反推 gate size？

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter8-Speed-45.webp)

由于<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mover accent="true">
<mi>

f

</mi>

<mo>

^

</mo>
</mover>

<mo>

=

</mo>

<msub>
<mi>

g

</mi>

<mi>

i

</mi>
</msub>

<mfrac>
<msub>
<mi>

C

</mi>

<mrow>
<mi>

o

</mi>

<mi>

u

</mi>

<mi>

t

</mi>

<mo separator="true">

,

</mo>

<mi>

i

</mi>
</mrow>
</msub>

<msub>
<mi>

C

</mi>

<mrow>
<mi>

i

</mi>

<mi>

n

</mi>

<mo separator="true">

,

</mo>

<mi>

i

</mi>
</mrow>
</msub>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

\hat f=g_i\frac{C_{out,i}}{C_{in,i}}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.1523em;vertical-align:-0.1944em;">



</span>

<span className="mord,accent">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.9579em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1076em;">

f

</span>
</span>

<span style="top:-3.2634em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.0833em;">
<span className="mord">

^

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.1944em;">
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
<span className="strut" style="height:1.528em;vertical-align:-0.5423em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

g

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
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
<span className="mord,mathnormal,mtight" style="margin-right:0.0715em;">

C

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3281em;">
<span style="top:-2.357em;margin-left:-0.0715em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

in

</span>

<span className="mpunct,mtight">

,

</span>

<span className="mord,mathnormal,mtight">

i

</span>
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
<span className="mord,mathnormal,mtight" style="margin-right:0.0715em;">

C

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3281em;">
<span style="top:-2.357em;margin-left:-0.0715em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

o

</span>

<span className="mord,mathnormal,mtight">

u

</span>

<span className="mord,mathnormal,mtight">

t

</span>

<span className="mpunct,mtight">

,

</span>

<span className="mord,mathnormal,mtight">

i

</span>
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

，所以可以推出每一级的<span className="katex">
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

n

</mi>

<mo separator="true">

,

</mo>

<mi>

i

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

g

</mi>

<mi>

i

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

u

</mi>

<mi>

t

</mi>

<mo separator="true">

,

</mo>

<mi>

i

</mi>
</mrow>
</msub>
</mrow>

<mover accent="true">
<mi>

f

</mi>

<mo>

^

</mo>
</mover>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

C_{in,i}=\frac{g_iC_{out,i}}{\hat f}

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

in

</span>

<span className="mpunct,mtight">

,

</span>

<span className="mord,mathnormal,mtight">

i

</span>
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
<span className="strut" style="height:1.6023em;vertical-align:-0.6166em;">



</span>

<span className="mord">
<span className="mopen,nulldelimiter">



</span>

<span className="mfrac">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.9857em;">
<span style="top:-2.5195em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,accent,mtight">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.9579em;">
<span style="top:-2.7em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.1076em;">

f

</span>
</span>

<span style="top:-2.9634em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="accent-body" style="left:-0.0833em;">
<span className="mord,mtight">

^

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.1944em;">
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

<span style="top:-3.5073em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

g

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3281em;">
<span style="top:-2.357em;margin-left:-0.0359em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
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
<span className="vlist" style="height:0.143em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>

<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0715em;">

C

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3281em;">
<span style="top:-2.357em;margin-left:-0.0715em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

o

</span>

<span className="mord,mathnormal,mtight">

u

</span>

<span className="mord,mathnormal,mtight">

t

</span>

<span className="mpunct,mtight">

,

</span>

<span className="mord,mathnormal,mtight">

i

</span>
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
<span className="vlist" style="height:0.6166em;">
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



当路径总 effort <span className="katex">
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

 和级数 <span className="katex">
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

 已知时，最优每级 effort 为 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mover accent="true">
<mi>

f

</mi>

<mo>

^

</mo>
</mover>

<mo>

=

</mo>

<msup>
<mi>

F

</mi>

<mrow>
<mn>

1

</mn>

<mi mathvariant="normal">

/

</mi>

<mi>

N

</mi>
</mrow>
</msup>
</mrow>

<annotation encoding="application/x-tex">

\hat f=F^{1/N}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.1523em;vertical-align:-0.1944em;">



</span>

<span className="mord,accent">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.9579em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1076em;">

f

</span>
</span>

<span style="top:-3.2634em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.0833em;">
<span className="mord">

^

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.1944em;">
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
<span className="strut" style="height:0.888em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.1389em;">

F

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

1/

</span>

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
</span>

。为了确定各级门尺寸，利用 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mover accent="true">
<mi>

f

</mi>

<mo>

^

</mo>
</mover>

<mo>

=

</mo>

<msub>
<mi>

g

</mi>

<mi>

i

</mi>
</msub>

<msub>
<mi>

h

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

g

</mi>

<mi>

i

</mi>
</msub>

<mfrac>
<msub>
<mi>

C

</mi>

<mrow>
<mi>

o

</mi>

<mi>

u

</mi>

<msub>
<mi>

t

</mi>

<mi>

i

</mi>
</msub>
</mrow>
</msub>

<msub>
<mi>

C

</mi>

<mrow>
<mi>

i

</mi>

<msub>
<mi>

n

</mi>

<mi>

i

</mi>
</msub>
</mrow>
</msub>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

\hat f=g_i h_i=g_i\frac{C_{out_i}}{C_{in_i}}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.1523em;vertical-align:-0.1944em;">



</span>

<span className="mord,accent">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.9579em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1076em;">

f

</span>
</span>

<span style="top:-3.2634em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.0833em;">
<span className="mord">

^

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.1944em;">
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
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

g

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
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
<span className="mord,mathnormal">

h

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
<span className="strut" style="height:1.6483em;vertical-align:-0.6025em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

g

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
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
<span className="mopen,nulldelimiter">



</span>

<span className="mfrac">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:1.0458em;">
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
<span className="vlist" style="height:0.3281em;">
<span style="top:-2.357em;margin-left:-0.0715em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

i

</span>

<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

n

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3448em;">
<span style="top:-2.3448em;margin-left:0em;margin-right:0.1em;">
<span className="pstrut" style="height:2.6595em;">



</span>

<span className="mord,mathnormal,mtight">

i

</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.3147em;">
<span>



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
<span className="vlist" style="height:0.3678em;">
<span>



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

<span style="top:-3.5675em;">
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
<span className="vlist" style="height:0.2963em;">
<span style="top:-2.357em;margin-left:-0.0715em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

o

</span>

<span className="mord,mathnormal,mtight">

u

</span>

<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

t

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3448em;">
<span style="top:-2.3448em;margin-left:0em;margin-right:0.1em;">
<span className="pstrut" style="height:2.6595em;">



</span>

<span className="mord,mathnormal,mtight">

i

</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.3147em;">
<span>



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
<span className="vlist" style="height:0.3678em;">
<span>



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
<span className="vlist" style="height:0.6025em;">
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

 反推出 <span className="katex">
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

<msub>
<mi>

n

</mi>

<mi>

i

</mi>
</msub>
</mrow>
</msub>

<mo>

=

</mo>

<mfrac>
<mrow>
<msub>
<mi>

g

</mi>

<mi>

i

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

u

</mi>

<msub>
<mi>

t

</mi>

<mi>

i

</mi>
</msub>
</mrow>
</msub>
</mrow>

<mover accent="true">
<mi>

f

</mi>

<mo>

^

</mo>
</mover>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

C_{in_i}=\frac{g_i C_{out_i}}{\hat f}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9334em;vertical-align:-0.2501em;">



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

<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

n

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3281em;">
<span style="top:-2.357em;margin-left:0em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
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
<span className="strut" style="height:1.6624em;vertical-align:-0.6166em;">



</span>

<span className="mord">
<span className="mopen,nulldelimiter">



</span>

<span className="mfrac">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:1.0458em;">
<span style="top:-2.5195em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,accent,mtight">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.9579em;">
<span style="top:-2.7em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.1076em;">

f

</span>
</span>

<span style="top:-2.9634em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="accent-body" style="left:-0.0833em;">
<span className="mord,mtight">

^

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.1944em;">
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

<span style="top:-3.5675em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

g

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3281em;">
<span style="top:-2.357em;margin-left:-0.0359em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
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
<span className="vlist" style="height:0.143em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>

<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0715em;">

C

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.2963em;">
<span style="top:-2.357em;margin-left:-0.0715em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

o

</span>

<span className="mord,mathnormal,mtight">

u

</span>

<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

t

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3448em;">
<span style="top:-2.3448em;margin-left:0em;margin-right:0.1em;">
<span className="pstrut" style="height:2.6595em;">



</span>

<span className="mord,mathnormal,mtight">

i

</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.3147em;">
<span>



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
<span className="vlist" style="height:0.3678em;">
<span>



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
<span className="vlist" style="height:0.6166em;">
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

。因此实际计算时从最终负载 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

C

</mi>

<mi>

L

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

C_L

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
</span>
</span>
</span>

 开始向前倒推，每一级根据它要驱动的负载 <span className="katex">
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

u

</mi>

<msub>
<mi>

t

</mi>

<mi>

i

</mi>
</msub>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

C_{out_i}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9334em;vertical-align:-0.2501em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

o

</span>

<span className="mord,mathnormal,mtight">

u

</span>

<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

t

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3281em;">
<span style="top:-2.357em;margin-left:0em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
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

 求出自身所需输入电容 <span className="katex">
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

<msub>
<mi>

n

</mi>

<mi>

i

</mi>
</msub>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

C_{in_i}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9334em;vertical-align:-0.2501em;">



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

<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

n

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3281em;">
<span style="top:-2.357em;margin-left:0em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
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

，而输入电容大小就对应门的宽度。最后再检查倒推得到的第一级输入电容是否满足题目给定的输入电容约束。

---

### P74：Example: Optimize Path —— 四级路径优化例子

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter8-Speed-46.webp)

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

H

</mi>

<mo>

=

</mo>

<mn>

5

</mn>
</mrow>

<annotation encoding="application/x-tex">

H=5

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
<mn>

25

</mn>

<mn>

9

</mn>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

G=\frac{25}{9}

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

9

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

25

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
<mi>

B

</mi>

<mo>

=

</mo>

<mn>

1

</mn>
</mrow>

<annotation encoding="application/x-tex">

B=1

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
<span className="strut" style="height:0.6444em;">



</span>

<span className="mord">

1

</span>
</span>
</span>
</span>
</span>

所以 path effort：

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

<mi>

G

</mi>

<mi>

B

</mi>

<mi>

H

</mi>

<mo>

=

</mo>

<mfrac>
<mn>

25

</mn>

<mn>

9

</mn>
</mfrac>

<mo>

⋅

</mo>

<mn>

5

</mn>

<mo>

=

</mo>

<mfrac>
<mn>

125

</mn>

<mn>

9

</mn>
</mfrac>

<mo>

=

</mo>

<mn>

13.9

</mn>
</mrow>

<annotation encoding="application/x-tex">

F=GBH=\frac{25}{9}\cdot5=\frac{125}{9}=13.9

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
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0502em;">

GB

</span>

<span className="mord,mathnormal" style="margin-right:0.0813em;">

H

</span>

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

9

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

25

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

9

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

125

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

13.9

</span>
</span>
</span>
</span>
</span>

四级路径的 best stage effort 是：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mover accent="true">
<mi>

f

</mi>

<mo>

^

</mo>
</mover>

<mo>

=

</mo>

<msup>
<mi>

F

</mi>

<mrow>
<mn>

1

</mn>

<mi mathvariant="normal">

/

</mi>

<mn>

4

</mn>
</mrow>
</msup>
</mrow>

<annotation encoding="application/x-tex">

\hat f=F^{1/4}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.1523em;vertical-align:-0.1944em;">



</span>

<span className="mord,accent">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.9579em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1076em;">

f

</span>
</span>

<span style="top:-3.2634em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.0833em;">
<span className="mord">

^

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.1944em;">
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
<span className="strut" style="height:0.938em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.1389em;">

F

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

1/4

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
<mover accent="true">
<mi>

f

</mi>

<mo>

^

</mo>
</mover>

<mo>

=

</mo>

<mo stretchy="false">

(

</mo>

<mn>

13.9

</mn>

<msup>
<mo stretchy="false">

)

</mo>

<mrow>
<mn>

1

</mn>

<mi mathvariant="normal">

/

</mi>

<mn>

4

</mn>
</mrow>
</msup>

<mo>

≈

</mo>

<mn>

1.93

</mn>
</mrow>

<annotation encoding="application/x-tex">

\hat f=(13.9)^{1/4}\approx1.93

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.1523em;vertical-align:-0.1944em;">



</span>

<span className="mord,accent">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.9579em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1076em;">

f

</span>
</span>

<span style="top:-3.2634em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.0833em;">
<span className="mord">

^

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.1944em;">
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
<span className="strut" style="height:1.188em;vertical-align:-0.25em;">



</span>

<span className="mopen">

(

</span>

<span className="mord">

13.9

</span>

<span className="mclose">
<span className="mclose">

)

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

1/4

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

≈

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.6444em;">



</span>

<span className="mord">

1.93

</span>
</span>
</span>
</span>
</span>

<mark>

这页想说明的是：一旦知道了

</mark>

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

H

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

<mi>

N

</mi>
</mrow>

<annotation encoding="application/x-tex">

G,H,B,N

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

<span className="mord,mathnormal" style="margin-right:0.0813em;">

H

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

<span className="mord,mathnormal" style="margin-right:0.109em;">

N

</span>
</span>
</span>
</span>

<mark>

，就能很快得到每一级应该承担的 effort。后面如果要 sizing，就用 P73 的公式从后往前推。

</mark>



---

### P75-77：Example: 3-Stage Path —— 三极路径 sizing 题目<mark>（本章最重要的例子）</mark>

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter8-Speed-47.webp)

#### **先算F**

<span className="katex">
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

<mfrac>
<mn>

100

</mn>

<mn>

27

</mn>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

G=\frac{100}{27}

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

27

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

100

</span>
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

 （三个g相乘，前面表格中有公式）

<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

H

</mi>

<mo>

=

</mo>

<mfrac>
<mn>

45

</mn>

<mn>

8

</mn>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

H=\frac{45}{8}

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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

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

8

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

45

</span>
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

（因为最终 on-path 负载是 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mn>

45

</mn>
</mrow>

<annotation encoding="application/x-tex">

45

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6444em;">



</span>

<span className="mord">

45

</span>
</span>
</span>
</span>

，最初输入电容限制是 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mn>

8

</mn>
</mrow>

<annotation encoding="application/x-tex">

8

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6444em;">



</span>

<span className="mord">

8

</span>
</span>
</span>
</span>

。）

<span className="katex">
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

<mn>

3

</mn>

<mo>

⋅

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
</mrow>

<annotation encoding="application/x-tex">

B=3\cdot2=6

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
<span className="strut" style="height:0.6444em;">



</span>

<span className="mord">

3

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

6

</span>
</span>
</span>
</span>

 （2*3的分叉，且都是均分的）

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

<mi>

G

</mi>

<mi>

B

</mi>

<mi>

H

</mi>

<mo>

=

</mo>

<mfrac>
<mn>

100

</mn>

<mn>

27

</mn>
</mfrac>

<mo>

⋅

</mo>

<mfrac>
<mn>

45

</mn>

<mn>

8

</mn>
</mfrac>

<mo>

⋅

</mo>

<mn>

6

</mn>

<mo>

=

</mo>

<mn>

125

</mn>
</mrow>

<annotation encoding="application/x-tex">

F=GBH=\frac{100}{27}\cdot\frac{45}{8}\cdot6=125

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
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0502em;">

GB

</span>

<span className="mord,mathnormal" style="margin-right:0.0813em;">

H

</span>

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

27

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

⋅

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

8

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

45

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

125

</span>
</span>
</span>
</span>
</span>

这条路径有 3 级，所以 best stage effort（每一级承担一样的）：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mover accent="true">
<mi>

f

</mi>

<mo>

^

</mo>
</mover>

<mo>

=

</mo>

<msup>
<mn>

125

</mn>

<mrow>
<mn>

1

</mn>

<mi mathvariant="normal">

/

</mi>

<mn>

3

</mn>
</mrow>
</msup>

<mo>

=

</mo>

<mn>

5

</mn>
</mrow>

<annotation encoding="application/x-tex">

\hat f=125^{1/3}=5

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.1523em;vertical-align:-0.1944em;">



</span>

<span className="mord,accent">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.9579em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1076em;">

f

</span>
</span>

<span style="top:-3.2634em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.0833em;">
<span className="mord">

^

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.1944em;">
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
<span className="strut" style="height:0.938em;">



</span>

<span className="mord">

12

</span>

<span className="mord">
<span className="mord">

5

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

1/3

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

5

</span>
</span>
</span>
</span>
</span>

parasitic delay：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

P

</mi>

<mo>

=

</mo>

<mn>

2

</mn>

<mo>

+

</mo>

<mn>

3

</mn>

<mo>

+

</mo>

<mn>

2

</mn>

<mo>

=

</mo>

<mn>

7

</mn>
</mrow>

<annotation encoding="application/x-tex">

P=2+3+2=7

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
<span className="strut" style="height:0.7278em;vertical-align:-0.0833em;">



</span>

<span className="mord">

2

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

3

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

7

</span>
</span>
</span>
</span>
</span>

总 delay：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

D

</mi>

<mo>

=

</mo>

<mn>

3

</mn>

<mo>

⋅

</mo>

<mn>

5

</mn>

<mo>

+

</mo>

<mn>

7

</mn>

<mo>

=

</mo>

<mn>

22

</mn>
</mrow>

<annotation encoding="application/x-tex">

D=3\cdot5+7=22

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

⋅

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

+

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

22

</span>
</span>
</span>
</span>
</span>

如果用 FO4 作为单位，前面 FO4 inverter 的归一化 delay 是 5，所以：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mn>

22

</mn>

<mi mathvariant="normal">

/

</mi>

<mn>

5

</mn>

<mo>

=

</mo>

<mn>

4.4

</mn>

<mtext>

FO4

</mtext>
</mrow>

<annotation encoding="application/x-tex">

22/5=4.4\ \text{FO4}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord">

22/5

</span>

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

4.4

</span>

<span className="mspace">



</span>

<span className="mord,text">
<span className="mord">

FO4

</span>
</span>
</span>
</span>
</span>
</span>

<mark>

最关键的一步：先算

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

，再算

</mark>

 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mover accent="true">
<mi>

f

</mi>

<mo>

^

</mo>
</mover>
</mrow>

<annotation encoding="application/x-tex">

\hat f

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.1523em;vertical-align:-0.1944em;">



</span>

<span className="mord,accent">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.9579em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1076em;">

f

</span>
</span>

<span style="top:-3.2634em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.0833em;">
<span className="mord">

^

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.1944em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

<mark>

，再估最小 delay。

</mark>



#### 算y,x

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

y

</mi>

<mo>

=

</mo>

<mfrac>
<mrow>
<mi>

g

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

u

</mi>

<mi>

t

</mi>
</mrow>
</msub>
</mrow>

<mover accent="true">
<mi>

f

</mi>

<mo>

^

</mo>
</mover>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

y=\frac{gC_{out}}{\hat f}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.625em;vertical-align:-0.1944em;">



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
<span className="strut" style="height:2.4026em;vertical-align:-1.0423em;">



</span>

<span className="mord">
<span className="mopen,nulldelimiter">



</span>

<span className="mfrac">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:1.3603em;">
<span style="top:-2.1521em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord,accent">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.9579em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1076em;">

f

</span>
</span>

<span style="top:-3.2634em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.0833em;">
<span className="mord">

^

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.1944em;">
<span>



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

g

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

o

</span>

<span className="mord,mathnormal,mtight">

u

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

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:1.0423em;">
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
<mi>

y

</mi>

<mo>

=

</mo>

<mfrac>
<mrow>
<mfrac>
<mn>

5

</mn>

<mn>

3

</mn>
</mfrac>

<mo>

⋅

</mo>

<mn>

45

</mn>
</mrow>

<mn>

5

</mn>
</mfrac>

<mo>

=

</mo>

<mn>

15

</mn>
</mrow>

<annotation encoding="application/x-tex">

y=\frac{\frac{5}{3}\cdot45}{5}=15

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.625em;vertical-align:-0.1944em;">



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
<span className="strut" style="height:2.2661em;vertical-align:-0.686em;">



</span>

<span className="mord">
<span className="mopen,nulldelimiter">



</span>

<span className="mfrac">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:1.5801em;">
<span style="top:-2.314em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord">

5

</span>
</span>
</span>

<span style="top:-3.23em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="frac-line" style="border-bottom-width:0.04em;">



</span>
</span>

<span style="top:-3.735em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
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

5

</span>
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

<span className="mord">

45

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
<mi>

x

</mi>

<mo>

=

</mo>

<mfrac>
<mrow>
<mfrac>
<mn>

5

</mn>

<mn>

3

</mn>
</mfrac>

<mo>

⋅

</mo>

<mn>

30

</mn>
</mrow>

<mn>

5

</mn>
</mfrac>

<mo>

=

</mo>

<mn>

10

</mn>
</mrow>

<annotation encoding="application/x-tex">

x=\frac{\frac{5}{3}\cdot30}{5}=10

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
<span className="strut" style="height:2.2661em;vertical-align:-0.686em;">



</span>

<span className="mord">
<span className="mopen,nulldelimiter">



</span>

<span className="mfrac">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:1.5801em;">
<span style="top:-2.314em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord">

5

</span>
</span>
</span>

<span style="top:-3.23em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="frac-line" style="border-bottom-width:0.04em;">



</span>
</span>

<span style="top:-3.735em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
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

5

</span>
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

<span className="mord">

30

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

10

</span>
</span>
</span>
</span>
</span>

反推输入电容<mark>

（检查验算）

</mark>

：

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

n

</mi>
</mrow>
</msub>

<mo>

=

</mo>

<mfrac>
<mrow>
<mfrac>
<mn>

4

</mn>

<mn>

3

</mn>
</mfrac>

<mo>

⋅

</mo>

<mn>

30

</mn>
</mrow>

<mn>

5

</mn>
</mfrac>

<mo>

=

</mo>

<mn>

8

</mn>
</mrow>

<annotation encoding="application/x-tex">

C_{in}=\frac{\frac{4}{3}\cdot30}{5}=8

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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

in

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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
<span className="strut" style="height:2.2661em;vertical-align:-0.686em;">



</span>

<span className="mord">
<span className="mopen,nulldelimiter">



</span>

<span className="mfrac">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:1.5801em;">
<span style="top:-2.314em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord">

5

</span>
</span>
</span>

<span style="top:-3.23em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="frac-line" style="border-bottom-width:0.04em;">



</span>
</span>

<span style="top:-3.735em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
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

4

</span>
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

<span className="mord">

30

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

8

</span>
</span>
</span>
</span>
</span>

刚好等于题目给定的输入电容限制：

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

n

</mi>
</mrow>
</msub>

<mo>

=

</mo>

<mn>

8

</mn>
</mrow>

<annotation encoding="application/x-tex">

C_{in}=8

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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

in

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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

8

</span>
</span>
</span>
</span>
</span>

#### 推算复杂门的MOS管宽度（同样根据P24的准则，或者P60）

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter8-Speed-48.webp)

过程如上

---

### P78：Best Number of Stages —— 最佳级数不一定最少

<table>
<thead>
  <tr>
    <th>
      级数 <span className="katex">
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
    </th>
    
    <th>
      每级 effort <span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <mi>
                  f
                </mi>
              </mrow>
              
              <annotation encoding="application/x-tex">
                f
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">
              
            </span>
            
            <span className="mord,mathnormal" style="margin-right:0.1076em;">
              f
            </span>
          </span>
        </span>
      </span>
    </th>
    
    <th>
      总 delay <span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <mi>
                  D
                </mi>
              </mrow>
              
              <annotation encoding="application/x-tex">
                D
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
          </span>
        </span>
      </span>
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      1
    </td>
    
    <td>
      64
    </td>
    
    <td>
      65
    </td>
  </tr>
  
  <tr>
    <td>
      2
    </td>
    
    <td>
      8
    </td>
    
    <td>
      18
    </td>
  </tr>
  
  <tr>
    <td>
      3
    </td>
    
    <td>
      4
    </td>
    
    <td>
      15
    </td>
  </tr>
  
  <tr>
    <td>
      4
    </td>
    
    <td>
      2.8
    </td>
    
    <td>
      15.3
    </td>
  </tr>
</tbody>
</table>

最快的是：

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

<mn>

3

</mn>
</mrow>

<annotation encoding="application/x-tex">

N=3

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
<span className="strut" style="height:0.6444em;">



</span>

<span className="mord">

3

</span>
</span>
</span>
</span>
</span>

虽然 4 级也很接近，但不是最优。

这一页说明：如果负载很大，只用一级门直接驱动会非常慢。加入 buffer chain 虽然增加了 parasitic delay，但显著降低了每一级的 electrical effort，所以总 delay 反而下降。

---

### P79：Derivation —— 最佳级数公式怎么来的？<mark>（看看就行，非重点）</mark>

推导最佳级数

思路是：假设原来的 logic block 有 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

n

</mi>

<mn>

1

</mn>
</msub>
</mrow>

<annotation encoding="application/x-tex">

n_1

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
</span>
</span>
</span>

 级，现在可以在路径末端加 inverter buffer，把总级数变成 <span className="katex">
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

。

总 delay 写成：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

D

</mi>

<mo>

=

</mo>

<mi>

N

</mi>

<msup>
<mi>

F

</mi>

<mrow>
<mn>

1

</mn>

<mi mathvariant="normal">

/

</mi>

<mi>

N

</mi>
</mrow>
</msup>

<mo>

+

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

1

</mn>
</mrow>

<msub>
<mi>

n

</mi>

<mn>

1

</mn>
</msub>
</munderover>

<msub>
<mi>

p

</mi>

<mi>

i

</mi>
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

<msub>
<mi>

n

</mi>

<mn>

1

</mn>
</msub>

<mo stretchy="false">

)

</mo>

<msub>
<mi>

p

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

D=NF^{1/N}+\sum_{i=1}^{n_1}p_i+(N-n_1)p_{inv}

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

<span className="mord,mathnormal" style="margin-right:0.109em;">

N

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.1389em;">

F

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

1/

</span>

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:2.9402em;vertical-align:-1.2777em;">



</span>

<span className="mop,op-limits">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:1.6625em;">
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

1

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

<span style="top:-4.3111em;margin-left:0em;">
<span className="pstrut" style="height:3.05em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

n

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
<span className="mord,mathnormal">

p

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

<span className="mclose">

)

</span>

<span className="mord">
<span className="mord,mathnormal">

p

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

<msup>
<mi>

F

</mi>

<mrow>
<mn>

1

</mn>

<mi mathvariant="normal">

/

</mi>

<mi>

N

</mi>
</mrow>
</msup>
</mrow>

<annotation encoding="application/x-tex">

NF^{1/N}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.888em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

N

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.1389em;">

F

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

1/

</span>

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
</span>

 是所有 stage effort delay 的总和；
- <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mo>

∑

</mo>

<msub>
<mi>

p

</mi>

<mi>

i

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

\sum p_i

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mop,op-symbol,small-op" style="position:relative;top:0em;">

∑

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

 是原始逻辑门的寄生延迟；
- <span className="katex">
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

<msub>
<mi>

n

</mi>

<mn>

1

</mn>
</msub>

<mo stretchy="false">

)

</mo>

<msub>
<mi>

p

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

(N-n_1)p_{inv}

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

<span className="mclose">

)

</span>

<span className="mord">
<span className="mord,mathnormal">

p

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

 是额外插入 inverter 的寄生延迟。

为了找最佳 <span className="katex">
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

，对 <span className="katex">
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

 求导并令导数为 0。

课件定义：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

ρ

</mi>

<mo>

=

</mo>

<msup>
<mi>

F

</mi>

<mrow>
<mn>

1

</mn>

<mi mathvariant="normal">

/

</mi>

<mi>

N

</mi>
</mrow>
</msup>
</mrow>

<annotation encoding="application/x-tex">

\rho=F^{1/N}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.625em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal">

ρ

</span>

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

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.1389em;">

F

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

1/

</span>

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
</span>

也就是最佳 stage effort。

最后得到最佳 stage effort 满足：<span className="katex">
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

<mo>

+

</mo>

<mi>

ρ

</mi>

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

ln

</mi>

<mo>

⁡

</mo>

<mi>

ρ

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

p_{inv}+\rho(1-\ln\rho)=0

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
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
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
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

ρ

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

<span className="mop">

ln

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord,mathnormal">

ρ

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



这个公式的作用是告诉我们：最佳每级 effort 不只是数学上的 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

e

</mi>
</mrow>

<annotation encoding="application/x-tex">

e

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.4306em;">



</span>

<span className="mord,mathnormal">

e

</span>
</span>
</span>
</span>

，还要考虑每加一级 inverter 带来的 parasitic delay。

---

### P80：Best Stage Effort —— 最佳每级 effort 大约是多少？<mark>（看看就行，非重点）</mark>

P80 继续 P79 的公式：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<msub>
<mi>

p

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

<mo>

+

</mo>

<mi>

ρ

</mi>

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

ln

</mi>

<mo>

⁡

</mo>

<mi>

ρ

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

p_{inv}+\rho(1-\ln\rho)=0

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
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
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
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

ρ

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

<span className="mop">

ln

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord,mathnormal">

ρ

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
</span>

这个方程没有简单解析解。

如果忽略 parasitic delay：<span className="katex">
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

<mo>

=

</mo>

<mn>

0

</mn>
</mrow>

<annotation encoding="application/x-tex">

p_{inv}=0

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
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
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



那么：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

ρ

</mi>

<mo>

=

</mo>

<mi>

e

</mi>

<mo>

≈

</mo>

<mn>

2.718

</mn>
</mrow>

<annotation encoding="application/x-tex">

\rho=e\approx2.718

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.625em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal">

ρ

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.4831em;">



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
<span className="strut" style="height:0.6444em;">



</span>

<span className="mord">

2.718

</span>
</span>
</span>
</span>



这说明纯数学上，如果只考虑 effort delay，最佳每级放大倍率是 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

e

</mi>
</mrow>

<annotation encoding="application/x-tex">

e

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.4306em;">



</span>

<span className="mord,mathnormal">

e

</span>
</span>
</span>
</span>

。

但真实 inverter 有寄生延迟。若：<span className="katex">
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

<mo>

=

</mo>

<mn>

1

</mn>
</mrow>

<annotation encoding="application/x-tex">

p_{inv}=1

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
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
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



数值解得到：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

ρ

</mi>

<mo>

=

</mo>

<mn>

3.59

</mn>
</mrow>

<annotation encoding="application/x-tex">

\rho=3.59

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.625em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal">

ρ

</span>

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

3.59

</span>
</span>
</span>
</span>



这就是为什么工程上经常说最优 <mark>

stage effort 接近 4

</mark>

，也就是 FO4 附近。

<mark>

所以实际经验是：

</mark>

<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mover accent="true">
<mi>

f

</mi>

<mo>

^

</mo>
</mover>

<mo>

≈

</mo>

<mn>

4

</mn>
</mrow>

<annotation encoding="application/x-tex">

\hat f \approx 4

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.1523em;vertical-align:-0.1944em;">



</span>

<span className="mord,accent">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.9579em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1076em;">

f

</span>
</span>

<span style="top:-3.2634em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.0833em;">
<span className="mord">

^

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.1944em;">
<span>



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
<span className="strut" style="height:0.6444em;">



</span>

<span className="mord">

4

</span>
</span>
</span>
</span>



这也是 P83 里用：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

N

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

4

</mn>
</msub>

<mi>

F

</mi>
</mrow>

<annotation encoding="application/x-tex">

N=\log_4F

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

<span className="mord,mathnormal" style="margin-right:0.1389em;">

F

</span>
</span>
</span>
</span>

 估算最佳级数的原因。

---

### P81-82：<mark>Sensitivity Analysis</mark> —— 级数不必精确到完美/sizing 方向的误差也相对温和

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 49.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter8-Speed-49.webp" />
      </p>
    </td>
    
    
      <td style="width: 50.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter8-Speed-50.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

---

### <mark>P83：Method of Logical Effort —— 做题总流程（重要，常作为最后一道大题）</mark>

课件把 Logical Effort 方法总结为 6 步

#### 第一步：Compute path effort

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

<mi>

G

</mi>

<mi>

B

</mi>

<mi>

H

</mi>
</mrow>

<annotation encoding="application/x-tex">

F=GBH

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
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0502em;">

GB

</span>

<span className="mord,mathnormal" style="margin-right:0.0813em;">

H

</span>
</span>
</span>
</span>
</span>

- path logical effort <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

G

</mi>
</mrow>

<annotation encoding="application/x-tex">

G

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
</span>
</span>
</span>

；
- branching effort <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

B

</mi>
</mrow>

<annotation encoding="application/x-tex">

B

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
</span>
</span>
</span>

；
- path electrical effort <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

H

</mi>
</mrow>

<annotation encoding="application/x-tex">

H

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
</span>
</span>
</span>

#### 第二步：Estimate best number of stages<mark>（N已知时不需要）</mark>

用经验公式：

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

4

</mn>
</msub>

<mi>

F

</mi>
</mrow>

<annotation encoding="application/x-tex">

N=\log_4F

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

<span className="mord,mathnormal" style="margin-right:0.1389em;">

F

</span>
</span>
</span>
</span>
</span>

这里的 4 来自前面最佳 stage effort 接近 FO4。

<mark>

如果算出来不是整数，就选附近的整数进行比较。

</mark>



---

#### 第三步：Sketch path with <span className="katex">
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

 stages by adding buffers<mark>（N已知时不需要）</mark>

如果原路径级数不够，就加 buffer。

如果原路径级数太多，就考虑改拓扑，减少逻辑级数。

---

#### 第四步：Estimate least delay

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

D

</mi>

<mo>

=

</mo>

<mi>

N

</mi>

<msup>
<mi>

F

</mi>

<mrow>
<mn>

1

</mn>

<mi mathvariant="normal">

/

</mi>

<mi>

N

</mi>
</mrow>
</msup>

<mo>

+

</mo>

<mi>

P

</mi>
</mrow>

<annotation encoding="application/x-tex">

D=NF^{1/N}+P

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

<span className="mord,mathnormal" style="margin-right:0.109em;">

N

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.1389em;">

F

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

1/

</span>

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

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>
</span>
</span>
</span>
</span>

这里：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

P

</mi>

<mo>

=

</mo>

<mo>

∑

</mo>

<msub>
<mi>

p

</mi>

<mi>

i

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

P=\sum p_i

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
<span className="strut" style="height:1.6em;vertical-align:-0.55em;">



</span>

<span className="mop,op-symbol,large-op" style="position:relative;top:0em;">

∑

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
</span>

注意如果你加了 inverter buffer，<span className="katex">
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

 也要包括这些新增 inverter 的 parasitic delay。

---

#### 第五步：Determine best stage effort

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mover accent="true">
<mi>

f

</mi>

<mo>

^

</mo>
</mover>

<mo>

=

</mo>

<msup>
<mi>

F

</mi>

<mrow>
<mn>

1

</mn>

<mi mathvariant="normal">

/

</mi>

<mi>

N

</mi>
</mrow>
</msup>
</mrow>

<annotation encoding="application/x-tex">

\hat f=F^{1/N}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.1523em;vertical-align:-0.1944em;">



</span>

<span className="mord,accent">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.9579em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1076em;">

f

</span>
</span>

<span style="top:-3.2634em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.0833em;">
<span className="mord">

^

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.1944em;">
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
<span className="strut" style="height:0.938em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.1389em;">

F

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

1/

</span>

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
</span>
</span>

这是每一级目标 effort。

---

#### 第六步：Find gate sizes

从最后一级负载开始往前推：

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

n

</mi>

<mo separator="true">

,

</mo>

<mi>

i

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

g

</mi>

<mi>

i

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

u

</mi>

<mi>

t

</mi>

<mo separator="true">

,

</mo>

<mi>

i

</mi>
</mrow>
</msub>
</mrow>

<mover accent="true">
<mi>

f

</mi>

<mo>

^

</mo>
</mover>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

C_{in,i}=\frac{g_iC_{out,i}}{\hat f}

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

in

</span>

<span className="mpunct,mtight">

,

</span>

<span className="mord,mathnormal,mtight">

i

</span>
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
<span className="strut" style="height:2.4026em;vertical-align:-1.0423em;">



</span>

<span className="mord">
<span className="mopen,nulldelimiter">



</span>

<span className="mfrac">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:1.3603em;">
<span style="top:-2.1521em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord,accent">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.9579em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1076em;">

f

</span>
</span>

<span style="top:-3.2634em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.0833em;">
<span className="mord">

^

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.1944em;">
<span>



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
<span className="mord,mathnormal" style="margin-right:0.0359em;">

g

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
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

o

</span>

<span className="mord,mathnormal,mtight">

u

</span>

<span className="mord,mathnormal,mtight">

t

</span>

<span className="mpunct,mtight">

,

</span>

<span className="mord,mathnormal,mtight">

i

</span>
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
<span className="vlist" style="height:1.0423em;">
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

<mark>

如果有分支，

</mark>

<span className="katex">
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

u

</mi>

<mi>

t

</mi>

<mo separator="true">

,

</mo>

<mi>

i

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

C_{out,i}

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

o

</span>

<span className="mord,mathnormal,mtight">

u

</span>

<span className="mord,mathnormal,mtight">

t

</span>

<span className="mpunct,mtight">

,

</span>

<span className="mord,mathnormal,mtight">

i

</span>
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

必须包括 on-path 和 off-path 的总负载。

</mark>



#### 第七步：算MOS管大小

根据P24和P60的标准

具体计算参考P77

---

### P84：Review of Definitions —— 符号总复习

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter8-Speed-51.webp)

---

### P85：Key Take-Aways —— Logical Effort 的优点和限制

第一，logical effort 可以用数字表征不同 gate 的速度代价。

第二，最快路径通常让每一级 effort 接近 4。

第三，路径 delay 对级数和尺寸不是极端敏感。

第四，级数少不一定更快。

第五，在 CMOS 中，NAND 通常比 NOR 快。

<mark>

原因是 NOR 的 PMOS 串联，PMOS 本身弱，为了匹配驱动能力需要更大W，输入电容大，所以 logical effort 更大。

</mark>



第六，inverter 和 NAND2 通常比较适合驱动大电容。

---

### P86：Summary —— 全章总结

1. delay 和 RC delay model；
2. complex gates 的 delay model；
3. modern design 中的 standard cell delay；
4. logical effort
