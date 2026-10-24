# 矩阵论25-26回忆卷

> 

## 25-26 回忆卷 by Soleil

#### 一、证明题

(1) 已知矩阵 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi mathvariant="bold-italic">

B

</mi>
</mrow>

<annotation encoding="application/x-tex">

\boldsymbol{B}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6861em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord,boldsymbol" style="margin-right:0.0483em;">

B

</span>
</span>
</span>
</span>
</span>
</span>

 满足 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi mathvariant="normal">

∣

</mi>

<mi mathvariant="bold-italic">

B

</mi>

<mi mathvariant="normal">

∣

</mi>

<mo mathvariant="normal">

≠

</mo>

<mn>

0

</mn>
</mrow>

<annotation encoding="application/x-tex">

|\boldsymbol{B}| \neq 0

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
<span className="mord">
<span className="mord,boldsymbol" style="margin-right:0.0483em;">

B

</span>
</span>
</span>

<span className="mord">

∣

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
<span className="strut" style="height:0.6444em;">



</span>

<span className="mord">

0

</span>
</span>
</span>
</span>

，证明矩阵 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi mathvariant="bold-italic">

A

</mi>

<mo>

=

</mo>

<mi mathvariant="bold-italic">

B

</mi>

<msup>
<mi mathvariant="bold-italic">

B

</mi>

<mi mathvariant="normal">

H

</mi>
</msup>
</mrow>

<annotation encoding="application/x-tex">

\boldsymbol{A} = \boldsymbol{B}\boldsymbol{B}^{\mathrm{H}}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6861em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord,boldsymbol">

A

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
<span className="strut" style="height:0.9173em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord,boldsymbol" style="margin-right:0.0483em;">

B

</span>
</span>
</span>

<span className="mord">
<span className="mord">
<span className="mord">
<span className="mord,boldsymbol" style="margin-right:0.0483em;">

B

</span>
</span>
</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.9173em;">
<span style="top:-3.139em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathrm,mtight">

H

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

 是正定矩阵；

(2) 已知 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msup>
<mi mathvariant="bold-italic">

A

</mi>

<mi mathvariant="normal">

T

</mi>
</msup>

<mo>

=

</mo>

<mo>

−

</mo>

<mi mathvariant="bold-italic">

A

</mi>
</mrow>

<annotation encoding="application/x-tex">

\boldsymbol{A}^{\mathrm{T}} = -\boldsymbol{A}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9173em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord">
<span className="mord,boldsymbol">

A

</span>
</span>
</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.9173em;">
<span style="top:-3.139em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathrm,mtight">

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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.7694em;vertical-align:-0.0833em;">



</span>

<span className="mord">

−

</span>

<span className="mord">
<span className="mord">
<span className="mord,boldsymbol">

A

</span>
</span>
</span>
</span>
</span>
</span>

，证明 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi mathvariant="bold-italic">

A

</mi>
</mrow>

<annotation encoding="application/x-tex">

\boldsymbol{A}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6861em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord,boldsymbol">

A

</span>
</span>
</span>
</span>
</span>
</span>

 的特征值一定为0或纯虚数。

#### 二、线性方程组的解

已知线性方程组

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mo fence="true">

{

</mo>

<mtable rowspacing="0.36em" columnalign="left left" columnspacing="1em">
<mtr>
<mtd>
<mstyle scriptlevel="0" displaystyle="false">
<mrow>
<mi>

α

</mi>

<msub>
<mi>

x

</mi>

<mn>

1

</mn>
</msub>

<mo>

+

</mo>

<mi>

α

</mi>

<msub>
<mi>

x

</mi>

<mn>

3

</mn>
</msub>

<mo>

=

</mo>

<mn>

3

</mn>

<mo>

−

</mo>

<mn>

2

</mn>

<mi>

α

</mi>
</mrow>
</mstyle>
</mtd>
</mtr>

<mtr>
<mtd>
<mstyle scriptlevel="0" displaystyle="false">
<mrow>
<mn>

2

</mn>

<msub>
<mi>

x

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

x

</mi>

<mn>

2

</mn>
</msub>

<mo>

+

</mo>

<mo stretchy="false">

(

</mo>

<mi>

α

</mi>

<mo>

+

</mo>

<mn>

3

</mn>

<mo stretchy="false">

)

</mo>

<msub>
<mi>

x

</mi>

<mn>

3

</mn>
</msub>

<mo>

=

</mo>

<mi>

α

</mi>
</mrow>
</mstyle>
</mtd>
</mtr>

<mtr>
<mtd>
<mstyle scriptlevel="0" displaystyle="false">
<mrow>
<mn>

3

</mn>

<msub>
<mi>

x

</mi>

<mn>

1

</mn>
</msub>

<mo>

+

</mo>

<mi>

α

</mi>

<msub>
<mi>

x

</mi>

<mn>

2

</mn>
</msub>

<mo>

+

</mo>

<mo stretchy="false">

(

</mo>

<mn>

2

</mn>

<mi>

α

</mi>

<mo>

+

</mo>

<mn>

3

</mn>

<mo stretchy="false">

)

</mo>

<msub>
<mi>

x

</mi>

<mn>

3

</mn>
</msub>

<mo>

=

</mo>

<mn>

2

</mn>

<mi>

α

</mi>
</mrow>
</mstyle>
</mtd>
</mtr>
</mtable>
</mrow>

<annotation encoding="application/x-tex">

\begin{cases} \alpha x_1 + \alpha x_3 = 3 - 2\alpha \\ 2x_1 + x_2 + (\alpha + 3)x_3 = \alpha \\ 3x_1 + \alpha x_2 + (2\alpha + 3)x_3 = 2\alpha \end{cases}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:4.32em;vertical-align:-1.91em;">



</span>

<span className="minner">
<span className="mopen">
<span className="delimsizing,mult">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:2.35em;">
<span style="top:-2.2em;">
<span className="pstrut" style="height:3.15em;">



</span>

<span className="delimsizinginner,delim-size4">
<span>

⎩

</span>
</span>
</span>

<span style="top:-2.192em;">
<span className="pstrut" style="height:3.15em;">



</span>

<span style="height:0.316em;width:0.8889em;">
<svg xmlns="http://www.w3.org/2000/svg" width="0.8889em" height="0.316em" style="width:0.8889em" viewBox="0 0 888.89 316" preserveAspectRatio="xMinYMin">
<path d="M384 0 H504 V316 H384z M384 0 H504 V316 H384z">



</path>
</svg>
</span>
</span>

<span style="top:-3.15em;">
<span className="pstrut" style="height:3.15em;">



</span>

<span className="delimsizinginner,delim-size4">
<span>

⎨

</span>
</span>
</span>

<span style="top:-4.292em;">
<span className="pstrut" style="height:3.15em;">



</span>

<span style="height:0.316em;width:0.8889em;">
<svg xmlns="http://www.w3.org/2000/svg" width="0.8889em" height="0.316em" style="width:0.8889em" viewBox="0 0 888.89 316" preserveAspectRatio="xMinYMin">
<path d="M384 0 H504 V316 H384z M384 0 H504 V316 H384z">



</path>
</svg>
</span>
</span>

<span style="top:-4.6em;">
<span className="pstrut" style="height:3.15em;">



</span>

<span className="delimsizinginner,delim-size4">
<span>

⎧

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:1.85em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>

<span className="mord">
<span className="mtable">
<span className="col-align-l">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:2.41em;">
<span style="top:-4.41em;">
<span className="pstrut" style="height:3.008em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0037em;">

α

</span>

<span className="mord">
<span className="mord,mathnormal">

x

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

<span className="mord,mathnormal" style="margin-right:0.0037em;">

α

</span>

<span className="mord">
<span className="mord,mathnormal">

x

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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mord">

3

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

<span className="mord,mathnormal" style="margin-right:0.0037em;">

α

</span>
</span>
</span>

<span style="top:-2.97em;">
<span className="pstrut" style="height:3.008em;">



</span>

<span className="mord">
<span className="mord">

2

</span>

<span className="mord">
<span className="mord,mathnormal">

x

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

<span className="mord">
<span className="mord,mathnormal">

x

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

<span className="mopen">

(

</span>

<span className="mord,mathnormal" style="margin-right:0.0037em;">

α

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mord">

3

</span>

<span className="mclose">

)

</span>

<span className="mord">
<span className="mord,mathnormal">

x

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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0037em;">

α

</span>
</span>
</span>

<span style="top:-1.53em;">
<span className="pstrut" style="height:3.008em;">



</span>

<span className="mord">
<span className="mord">

3

</span>

<span className="mord">
<span className="mord,mathnormal">

x

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

<span className="mord,mathnormal" style="margin-right:0.0037em;">

α

</span>

<span className="mord">
<span className="mord,mathnormal">

x

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

<span className="mopen">

(

</span>

<span className="mord">

2

</span>

<span className="mord,mathnormal" style="margin-right:0.0037em;">

α

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mord">

3

</span>

<span className="mclose">

)

</span>

<span className="mord">
<span className="mord,mathnormal">

x

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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mord">

2

</span>

<span className="mord,mathnormal" style="margin-right:0.0037em;">

α

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:1.91em;">
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

(1) 是否存在 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

α

</mi>
</mrow>

<annotation encoding="application/x-tex">

\alpha

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.4306em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0037em;">

α

</span>
</span>
</span>
</span>

 方程组只有唯一解的情况，若存在，求出 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

α

</mi>
</mrow>

<annotation encoding="application/x-tex">

\alpha

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.4306em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0037em;">

α

</span>
</span>
</span>
</span>

 的值；

(2) 是否存在 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

α

</mi>
</mrow>

<annotation encoding="application/x-tex">

\alpha

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.4306em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0037em;">

α

</span>
</span>
</span>
</span>

 方程组无解的情况，若存在，求出 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

α

</mi>
</mrow>

<annotation encoding="application/x-tex">

\alpha

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.4306em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0037em;">

α

</span>
</span>
</span>
</span>

 的值；

(3) 是否存在 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

α

</mi>
</mrow>

<annotation encoding="application/x-tex">

\alpha

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.4306em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0037em;">

α

</span>
</span>
</span>
</span>

 方程组有无穷多解的情况，若存在，求出 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

α

</mi>
</mrow>

<annotation encoding="application/x-tex">

\alpha

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.4306em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0037em;">

α

</span>
</span>
</span>
</span>

 的值。

#### 三、矩阵奇异值分解

已知矩阵为

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi mathvariant="bold-italic">

A

</mi>

<mo>

=

</mo>

<msub>
<mrow>
<mo fence="true">

[

</mo>

<mtable rowspacing="0.16em" columnalign="center center" columnspacing="1em">
<mtr>
<mtd>
<mstyle scriptlevel="0" displaystyle="false">
<mn>

2

</mn>
</mstyle>
</mtd>

<mtd>
<mstyle scriptlevel="0" displaystyle="false">
<mn>

0

</mn>
</mstyle>
</mtd>
</mtr>

<mtr>
<mtd>
<mstyle scriptlevel="0" displaystyle="false">
<mn>

0

</mn>
</mstyle>
</mtd>

<mtd>
<mstyle scriptlevel="0" displaystyle="false">
<mn>

1

</mn>
</mstyle>
</mtd>
</mtr>

<mtr>
<mtd>
<mstyle scriptlevel="0" displaystyle="false">
<mn>

1

</mn>
</mstyle>
</mtd>

<mtd>
<mstyle scriptlevel="0" displaystyle="false">
<mn>

0

</mn>
</mstyle>
</mtd>
</mtr>

<mtr>
<mtd>
<mstyle scriptlevel="0" displaystyle="false">
<mn>

0

</mn>
</mstyle>
</mtd>

<mtd>
<mstyle scriptlevel="0" displaystyle="false">
<mrow>
<mo>

−

</mo>

<mn>

1

</mn>
</mrow>
</mstyle>
</mtd>
</mtr>
</mtable>

<mo fence="true">

]

</mo>
</mrow>

<mrow>
<mn>

4

</mn>

<mo>

×

</mo>

<mn>

2

</mn>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

\boldsymbol{A} = \begin{bmatrix} 2 & 0 \\ 0 & 1 \\ 1 & 0 \\ 0 & -1 \end{bmatrix}_{4 \times 2}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6861em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord,boldsymbol">

A

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
<span className="strut" style="height:4.9081em;vertical-align:-2.2581em;">



</span>

<span className="minner">
<span className="minner">
<span className="mopen">
<span className="delimsizing,mult">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:2.65em;">
<span style="top:-4.65em;">
<span className="pstrut" style="height:6.8em;">



</span>

<span style="width:0.667em;height:4.8em;">
<svg xmlns="http://www.w3.org/2000/svg" width="0.667em" height="4.8em" viewBox="0 0 667 4800">
<path d="M403 1759 V84 H666 V0 H319 V1759 v1200 v1759 v84 h347 v-84
H403z M403 1759 V0 H319 V1759 v1200 v1759 v84 h84z">



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
<span className="vlist" style="height:2.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>

<span className="mord">
<span className="mtable">
<span className="col-align-c">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:2.65em;">
<span style="top:-4.81em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord">

2

</span>
</span>
</span>

<span style="top:-3.61em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord">

0

</span>
</span>
</span>

<span style="top:-2.41em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord">

1

</span>
</span>
</span>

<span style="top:-1.21em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord">

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
<span className="vlist" style="height:2.15em;">
<span>



</span>
</span>
</span>
</span>
</span>

<span className="arraycolsep" style="width:0.5em;">



</span>

<span className="arraycolsep" style="width:0.5em;">



</span>

<span className="col-align-c">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:2.65em;">
<span style="top:-4.81em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord">

0

</span>
</span>
</span>

<span style="top:-3.61em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord">

1

</span>
</span>
</span>

<span style="top:-2.41em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord">

0

</span>
</span>
</span>

<span style="top:-1.21em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord">

−

</span>

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
<span className="vlist" style="height:2.15em;">
<span>



</span>
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
<span className="vlist" style="height:2.65em;">
<span style="top:-4.65em;">
<span className="pstrut" style="height:6.8em;">



</span>

<span style="width:0.667em;height:4.8em;">
<svg xmlns="http://www.w3.org/2000/svg" width="0.667em" height="4.8em" viewBox="0 0 667 4800">
<path d="M347 1759 V0 H0 V84 H263 V1759 v1200 v1759 H0 v84 H347z
M347 1759 V0 H263 V1759 v1200 v1759 h84z">



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
<span className="vlist" style="height:2.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:-1.7486em;">
<span style="top:-0.5003em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



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
<span className="vlist" style="height:2.2581em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

(1) 求矩阵 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi mathvariant="bold-italic">

A

</mi>
</mrow>

<annotation encoding="application/x-tex">

\boldsymbol{A}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6861em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord,boldsymbol">

A

</span>
</span>
</span>
</span>
</span>
</span>

 的右奇异向量；

(2) 求矩阵 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi mathvariant="bold-italic">

A

</mi>
</mrow>

<annotation encoding="application/x-tex">

\boldsymbol{A}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6861em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord,boldsymbol">

A

</span>
</span>
</span>
</span>
</span>
</span>

 的非零左奇异向量；

(3) 考虑截断 SVD 方法，求 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi mathvariant="bold-italic">

A

</mi>

<mi>

k

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

\boldsymbol{A}_k

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8361em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord">
<span className="mord,boldsymbol">

A

</span>
</span>
</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-right:0.05em;">
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

，其中 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

k

</mi>

<mo>

=

</mo>

<mn>

1

</mn>
</mrow>

<annotation encoding="application/x-tex">

k=1

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
<span className="strut" style="height:0.6444em;">



</span>

<span className="mord">

1

</span>
</span>
</span>
</span>

, 并解释截断 SVD 的几何意义或者物理含义。

#### 四、矩阵微分

(1) 已知 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi mathvariant="bold-italic">

A

</mi>
</mrow>

<annotation encoding="application/x-tex">

\boldsymbol{A}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6861em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord,boldsymbol">

A

</span>
</span>
</span>
</span>
</span>
</span>

 为矩阵变量， <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi mathvariant="bold-italic">

B

</mi>
</mrow>

<annotation encoding="application/x-tex">

\boldsymbol{B}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6861em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord,boldsymbol" style="margin-right:0.0483em;">

B

</span>
</span>
</span>
</span>
</span>
</span>

 为常数矩阵，求 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

t

</mi>

<mi>

r

</mi>

<mo stretchy="false">

(

</mo>

<msup>
<mi mathvariant="bold-italic">

A

</mi>

<mi>

T

</mi>
</msup>

<mi mathvariant="bold-italic">

B

</mi>

<mi mathvariant="bold-italic">

A

</mi>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

tr(\boldsymbol{A}^T\boldsymbol{B}\boldsymbol{A})

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.1673em;vertical-align:-0.25em;">



</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>

<span className="mopen">

(

</span>

<span className="mord">
<span className="mord">
<span className="mord">
<span className="mord,boldsymbol">

A

</span>
</span>
</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.9173em;">
<span style="top:-3.139em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
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

<span className="mord">
<span className="mord">
<span className="mord,boldsymbol" style="margin-right:0.0483em;">

B

</span>
</span>
</span>

<span className="mord">
<span className="mord">
<span className="mord,boldsymbol">

A

</span>
</span>
</span>

<span className="mclose">

)

</span>
</span>
</span>
</span>

 的梯度矩阵
(2) 已知 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>
<mrow>
<mi mathvariant="bold-italic">

F

</mi>

<mo stretchy="false">

(

</mo>

<mi mathvariant="bold-italic">

x

</mi>

<mo stretchy="false">

)

</mo>
</mrow>
</mi>

<mo>

=

</mo>

<mrow>
<mo fence="true">

[

</mo>

<mtable rowspacing="0.16em" columnalign="center" columnspacing="1em">
<mtr>
<mtd>
<mstyle scriptlevel="0" displaystyle="false">
<mrow>
<msubsup>
<mi>

x

</mi>

<mn>

1

</mn>

<mn>

2

</mn>
</msubsup>

<msub>
<mi>

x

</mi>

<mn>

2

</mn>
</msub>
</mrow>
</mstyle>
</mtd>
</mtr>

<mtr>
<mtd>
<mstyle scriptlevel="0" displaystyle="false">
<mrow>
<mi>

s

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

<msub>
<mi>

x

</mi>

<mn>

1

</mn>
</msub>

<msub>
<mi>

x

</mi>

<mn>

2

</mn>
</msub>

<mo stretchy="false">

)

</mo>
</mrow>
</mstyle>
</mtd>
</mtr>

<mtr>
<mtd>
<mstyle scriptlevel="0" displaystyle="false">
<msup>
<mi>

e

</mi>

<mrow>
<msub>
<mi>

x

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

x

</mi>

<mn>

2

</mn>
</msub>
</mrow>
</msup>
</mstyle>
</mtd>
</mtr>
</mtable>

<mo fence="true">

]

</mo>
</mrow>
</mrow>

<annotation encoding="application/x-tex">

\boldsymbol{F(x)} = \begin{bmatrix} x_1^2x_2 \\ sin(x_1 x_2) \\ e^{x_1 + x_2} \end{bmatrix}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord,boldsymbol" style="margin-right:0.1597em;">

F

</span>

<span className="mopen,mathbf">

(

</span>

<span className="mord,boldsymbol">

x

</span>

<span className="mclose,mathbf">

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
<span className="strut" style="height:3.6em;vertical-align:-1.55em;">



</span>

<span className="minner">
<span className="mopen">
<span className="delimsizing,mult">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:2.05em;">
<span style="top:-4.05em;">
<span className="pstrut" style="height:5.6em;">



</span>

<span style="width:0.667em;height:3.6em;">
<svg xmlns="http://www.w3.org/2000/svg" width="0.667em" height="3.6em" viewBox="0 0 667 3600">
<path d="M403 1759 V84 H666 V0 H319 V1759 v0 v1759 v84 h347 v-84
H403z M403 1759 V0 H319 V1759 v0 v1759 v84 h84z">



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
<span className="vlist" style="height:1.55em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>

<span className="mord">
<span className="mtable">
<span className="col-align-c">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:2.05em;">
<span style="top:-4.21em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord,mathnormal">

x

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.8141em;">
<span style="top:-2.4519em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">

1

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
<span className="vlist" style="height:0.2481em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>

<span className="mord">
<span className="mord,mathnormal">

x

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

<span style="top:-3.01em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

s

</span>

<span className="mord,mathnormal">

in

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

x

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

<span className="mclose">

)

</span>
</span>
</span>

<span style="top:-1.81em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord,mathnormal">

e

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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

x

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

<span className="mbin,mtight">

+

</span>

<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

x

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
<span className="vlist" style="height:1.55em;">
<span>



</span>
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
<span className="vlist" style="height:2.05em;">
<span style="top:-4.05em;">
<span className="pstrut" style="height:5.6em;">



</span>

<span style="width:0.667em;height:3.6em;">
<svg xmlns="http://www.w3.org/2000/svg" width="0.667em" height="3.6em" viewBox="0 0 667 3600">
<path d="M347 1759 V0 H0 V84 H263 V1759 v0 v1759 H0 v84 H347z
M347 1759 V0 H263 V1759 v0 v1759 h84z">



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
<span className="vlist" style="height:1.55em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

, 求 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>
<mrow>
<mi mathvariant="bold-italic">

F

</mi>

<mo stretchy="false">

(

</mo>

<mi mathvariant="bold-italic">

x

</mi>

<mo stretchy="false">

)

</mo>
</mrow>
</mi>
</mrow>

<annotation encoding="application/x-tex">

\boldsymbol{F (x)}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord,boldsymbol" style="margin-right:0.1597em;">

F

</span>

<span className="mopen,mathbf">

(

</span>

<span className="mord,boldsymbol">

x

</span>

<span className="mclose,mathbf">

)

</span>
</span>
</span>
</span>
</span>
</span>

 的雅可比矩阵 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>
<mrow>
<mi mathvariant="bold-italic">

J

</mi>

<mo stretchy="false">

(

</mo>

<mi mathvariant="bold-italic">

x

</mi>

<mo stretchy="false">

)

</mo>
</mrow>
</mi>
</mrow>

<annotation encoding="application/x-tex">

\boldsymbol{J(x)}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord,boldsymbol" style="margin-right:0.1007em;">

J

</span>

<span className="mopen,mathbf">

(

</span>

<span className="mord,boldsymbol">

x

</span>

<span className="mclose,mathbf">

)

</span>
</span>
</span>
</span>
</span>
</span>

, 并求 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

x

</mi>

<mn>

1

</mn>
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

<msub>
<mi>

x

</mi>

<mn>

2

</mn>
</msub>

<mo>

=

</mo>

<mn>

0

</mn>
</mrow>

<annotation encoding="application/x-tex">

x_1 = 1, x_2=0

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

x

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

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

x

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

 时的雅可比矩阵 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>
<mrow>
<mi mathvariant="bold-italic">

J

</mi>

<mo stretchy="false">

(

</mo>

<mi mathvariant="bold-italic">

x

</mi>

<mo stretchy="false">

)

</mo>
</mrow>
</mi>
</mrow>

<annotation encoding="application/x-tex">

\boldsymbol{J(x)}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord,boldsymbol" style="margin-right:0.1007em;">

J

</span>

<span className="mopen,mathbf">

(

</span>

<span className="mord,boldsymbol">

x

</span>

<span className="mclose,mathbf">

)

</span>
</span>
</span>
</span>
</span>
</span>



#### 五、Rayleigh 商问题

下列 Rayleigh 商问题，其中 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

x

</mi>

<mo mathvariant="normal">

≠

</mo>

<mi mathvariant="bold">

0

</mi>
</mrow>

<annotation encoding="application/x-tex">

x \neq \boldsymbol{0}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal">

x

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
<span className="strut" style="height:0.6444em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord,mathbf">

0

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
<mi mathvariant="bold-italic">

A

</mi>
</mrow>

<annotation encoding="application/x-tex">

\boldsymbol{A}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6861em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord,boldsymbol">

A

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
<mi mathvariant="bold-italic">

B

</mi>
</mrow>

<annotation encoding="application/x-tex">

\boldsymbol{B}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6861em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord,boldsymbol" style="margin-right:0.0483em;">

B

</span>
</span>
</span>
</span>
</span>
</span>

 为 Hermitian 正定矩阵。

(1) 已知 Rayleigh 商 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

R

</mi>

<mo stretchy="false">

(

</mo>

<mi mathvariant="bold-italic">

x

</mi>

<mo stretchy="false">

)

</mo>

<mo>

=

</mo>

<mfrac>
<mrow>
<msup>
<mi mathvariant="bold-italic">

x

</mi>

<mi mathvariant="normal">

H

</mi>
</msup>

<mi mathvariant="bold-italic">

A

</mi>

<mi mathvariant="bold-italic">

x

</mi>
</mrow>

<mrow>
<msup>
<mi mathvariant="bold-italic">

x

</mi>

<mi mathvariant="normal">

H

</mi>
</msup>

<mi mathvariant="bold-italic">

x

</mi>
</mrow>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

R(\boldsymbol{x}) = \frac{\boldsymbol{x}^{\mathrm{H}}\boldsymbol{A}\boldsymbol{x}}{\boldsymbol{x}^{\mathrm{H}}\boldsymbol{x}}

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

<span className="mopen">

(

</span>

<span className="mord">
<span className="mord">
<span className="mord,boldsymbol">

x

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
<span className="strut" style="height:1.3892em;vertical-align:-0.3519em;">



</span>

<span className="mord">
<span className="mopen,nulldelimiter">



</span>

<span className="mfrac">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:1.0374em;">
<span style="top:-2.6481em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">
<span className="mord,mtight">
<span className="mord,mtight">
<span className="mord,boldsymbol,mtight">

x

</span>
</span>
</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.7741em;">
<span style="top:-2.786em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
<span className="mord,mtight">
<span className="mord,mathrm,mtight">

H

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

<span className="mord,mtight">
<span className="mord,mtight">
<span className="mord,boldsymbol,mtight">

x

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
<span className="mord,mtight">
<span className="mord,mtight">
<span className="mord,boldsymbol,mtight">

x

</span>
</span>
</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.9191em;">
<span style="top:-2.931em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
<span className="mord,mtight">
<span className="mord,mathrm,mtight">

H

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

<span className="mord,mtight">
<span className="mord,mtight">
<span className="mord,boldsymbol,mtight">

A

</span>
</span>
</span>

<span className="mord,mtight">
<span className="mord,mtight">
<span className="mord,boldsymbol,mtight">

x

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
<span className="vlist" style="height:0.3519em;">
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

，写出 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

R

</mi>

<mo stretchy="false">

(

</mo>

<mi mathvariant="bold-italic">

x

</mi>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

R(\boldsymbol{x})

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

<span className="mopen">

(

</span>

<span className="mord">
<span className="mord">
<span className="mord,boldsymbol">

x

</span>
</span>
</span>

<span className="mclose">

)

</span>
</span>
</span>
</span>

 的极大值及相应的 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi mathvariant="bold-italic">

x

</mi>
</mrow>

<annotation encoding="application/x-tex">

\boldsymbol{x}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.4444em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord,boldsymbol">

x

</span>
</span>
</span>
</span>
</span>
</span>

 向量。

(2) 举例说明 Rayleigh 商在最小二乘法中的应用，要求简要描述问题模型和物理意义。

注：可用矩阵的特征值及特征向量表示求解量。

#### 六、神经网络训练调参

在深度学习中,线性代数和优化算法(如最小二乘法)广泛应用于参数估计和模型训练。假设我们有一个简单的线性神经网络(无激活函数),其输出为:

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi mathvariant="bold-italic">

y

</mi>

<mo>

=

</mo>

<mi mathvariant="bold-italic">

W

</mi>

<mi mathvariant="bold-italic">

x

</mi>

<mo>

+

</mo>

<mi mathvariant="bold-italic">

b

</mi>
</mrow>

<annotation encoding="application/x-tex">

\boldsymbol{y} = \boldsymbol{W}\boldsymbol{x} + \boldsymbol{b}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6389em;vertical-align:-0.1944em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord,boldsymbol" style="margin-right:0.037em;">

y

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
<span className="strut" style="height:0.7694em;vertical-align:-0.0833em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord,boldsymbol" style="margin-right:0.1597em;">

W

</span>
</span>
</span>

<span className="mord">
<span className="mord">
<span className="mord,boldsymbol">

x

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
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord,boldsymbol">

b

</span>
</span>
</span>
</span>
</span>
</span>
</span>

其中,<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi mathvariant="bold-italic">

x

</mi>

<mo>

∈

</mo>

<msup>
<mi mathvariant="double-struck">

R

</mi>

<mi>

n

</mi>
</msup>
</mrow>

<annotation encoding="application/x-tex">

\boldsymbol{x} \in \mathbb{R}^n

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.5782em;vertical-align:-0.0391em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord,boldsymbol">

x

</span>
</span>
</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

∈

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.6889em;">



</span>

<span className="mord">
<span className="mord,mathbb">

R

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

 是输入向量,<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi mathvariant="bold-italic">

W

</mi>

<mo>

∈

</mo>

<msup>
<mi mathvariant="double-struck">

R

</mi>

<mrow>
<mi>

m

</mi>

<mo>

×

</mo>

<mi>

n

</mi>
</mrow>
</msup>
</mrow>

<annotation encoding="application/x-tex">

\boldsymbol{W} \in \mathbb{R}^{m \times n}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.7252em;vertical-align:-0.0391em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord,boldsymbol" style="margin-right:0.1597em;">

W

</span>
</span>
</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

∈

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.7713em;">



</span>

<span className="mord">
<span className="mord,mathbb">

R

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

m

</span>

<span className="mbin,mtight">

×

</span>

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
</span>

 是权重矩阵,<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi mathvariant="bold-italic">

b

</mi>

<mo>

∈

</mo>

<msup>
<mi mathvariant="double-struck">

R

</mi>

<mi>

m

</mi>
</msup>
</mrow>

<annotation encoding="application/x-tex">

\boldsymbol{b} \in \mathbb{R}^m

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.7335em;vertical-align:-0.0391em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord,boldsymbol">

b

</span>
</span>
</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

∈

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.6889em;">



</span>

<span className="mord">
<span className="mord,mathbb">

R

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

m

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

 是偏置向量,<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi mathvariant="bold-italic">

y

</mi>

<mo>

∈

</mo>

<msup>
<mi mathvariant="double-struck">

R

</mi>

<mi>

m

</mi>
</msup>
</mrow>

<annotation encoding="application/x-tex">

\boldsymbol{y} \in \mathbb{R}^m

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.7335em;vertical-align:-0.1944em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord,boldsymbol" style="margin-right:0.037em;">

y

</span>
</span>
</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

∈

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.6889em;">



</span>

<span className="mord">
<span className="mord,mathbb">

R

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

m

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

 是输出向量。现在,假设我们有一组训练数据 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msubsup>
<mrow>
<mo stretchy="false">

(

</mo>

<msub>
<mi mathvariant="bold-italic">

x

</mi>

<mi>

i

</mi>
</msub>

<mo separator="true">

,

</mo>

<msub>
<mi mathvariant="bold-italic">

y

</mi>

<mi>

i

</mi>
</msub>

<mo stretchy="false">

)

</mo>
</mrow>

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

<mi>

N

</mi>
</msubsup>
</mrow>

<annotation encoding="application/x-tex">

{(\boldsymbol{x}_i, \boldsymbol{y}_i)}_{i=1}^N

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.2809em;vertical-align:-0.2997em;">



</span>

<span className="mord">
<span className="mord">
<span className="mopen">

(

</span>

<span className="mord">
<span className="mord">
<span className="mord">
<span className="mord,boldsymbol">

x

</span>
</span>
</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-right:0.05em;">
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
<span className="mord">
<span className="mord">
<span className="mord,boldsymbol" style="margin-right:0.037em;">

y

</span>
</span>
</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.2175em;">
<span style="top:-2.4559em;margin-right:0.05em;">
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
<span className="vlist" style="height:0.2441em;">
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

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.9812em;">
<span style="top:-2.4003em;margin-right:0.05em;">
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

1

</span>
</span>
</span>
</span>

<span style="top:-3.2029em;margin-right:0.05em;">
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
<span className="vlist" style="height:0.2997em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

,并希望通过最小二乘法来估计权重矩阵 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi mathvariant="bold-italic">

W

</mi>
</mrow>

<annotation encoding="application/x-tex">

\boldsymbol{W}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6861em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord,boldsymbol" style="margin-right:0.1597em;">

W

</span>
</span>
</span>
</span>
</span>
</span>

 和偏置向量 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi mathvariant="bold-italic">

b

</mi>
</mrow>

<annotation encoding="application/x-tex">

\boldsymbol{b}

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
<span className="mord,boldsymbol">

b

</span>
</span>
</span>
</span>
</span>
</span>

。
已知最小二乘优化问题为:

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<munder>
<mrow>
<mi>

min

</mi>

<mo>

⁡

</mo>
</mrow>

<mi mathvariant="bold-italic">

W

</mi>
</munder>

<mi>

L

</mi>

<mo stretchy="false">

(

</mo>

<mi mathvariant="bold-italic">

W

</mi>

<mo stretchy="false">

)

</mo>

<mo>

=

</mo>

<munder>
<mrow>
<mi>

min

</mi>

<mo>

⁡

</mo>
</mrow>

<mi mathvariant="bold-italic">

W

</mi>
</munder>

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

<mi>

N

</mi>
</munderover>

<mi mathvariant="normal">

∣

</mi>

<mi mathvariant="normal">

∣

</mi>

<msub>
<mi mathvariant="bold-italic">

y

</mi>

<mi>

i

</mi>
</msub>

<mo>

−

</mo>

<mi mathvariant="bold-italic">

W

</mi>

<msub>
<mi mathvariant="bold-italic">

x

</mi>

<mi>

i

</mi>
</msub>

<mi mathvariant="normal">

∣

</mi>

<msubsup>
<mi mathvariant="normal">

∣

</mi>

<mn>

2

</mn>

<mn>

2

</mn>
</msubsup>
</mrow>

<annotation encoding="application/x-tex">

\min_{\boldsymbol{W}} L(\boldsymbol{W}) = \min_{\boldsymbol{W}} \sum_{i=1}^{N} ||\boldsymbol{y}_i - \boldsymbol{W}\boldsymbol{x}_i||_2^2

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.4963em;vertical-align:-0.7463em;">



</span>

<span className="mop,op-limits">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.6679em;">
<span style="top:-2.3537em;margin-left:0em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">
<span className="mord,mtight">
<span className="mord,boldsymbol,mtight" style="margin-right:0.1597em;">

W

</span>
</span>
</span>
</span>
</span>
</span>

<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span>
<span className="mop">

min

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.7463em;">
<span>



</span>
</span>
</span>
</span>
</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord,mathnormal">

L

</span>

<span className="mopen">

(

</span>

<span className="mord">
<span className="mord">
<span className="mord,boldsymbol" style="margin-right:0.1597em;">

W

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
<span className="strut" style="height:3.106em;vertical-align:-1.2777em;">



</span>

<span className="mop,op-limits">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.6679em;">
<span style="top:-2.3537em;margin-left:0em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">
<span className="mord,mtight">
<span className="mord,boldsymbol,mtight" style="margin-right:0.1597em;">

W

</span>
</span>
</span>
</span>
</span>
</span>

<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span>
<span className="mop">

min

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.7463em;">
<span>



</span>
</span>
</span>
</span>
</span>

<span className="mspace" style="margin-right:0.1667em;">



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

∣∣

</span>

<span className="mord">
<span className="mord">
<span className="mord">
<span className="mord,boldsymbol" style="margin-right:0.037em;">

y

</span>
</span>
</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.2175em;">
<span style="top:-2.4559em;margin-right:0.05em;">
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
<span className="vlist" style="height:0.2441em;">
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
<span className="strut" style="height:1.1141em;vertical-align:-0.25em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord,boldsymbol" style="margin-right:0.1597em;">

W

</span>
</span>
</span>

<span className="mord">
<span className="mord">
<span className="mord">
<span className="mord,boldsymbol">

x

</span>
</span>
</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-right:0.05em;">
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

∣

</span>

<span className="mord">
<span className="mord">

∣

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.8641em;">
<span style="top:-2.453em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">

2

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
</span>
</span>
</span>
</span>

在实际应用中,为了减少模型参数量和计算复杂度,可以采用低秩分解的方法来更新权重矩阵。考虑 LoRA(Low-Rank Adaptation)算法,该算法将权重更新表示为:<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi mathvariant="bold-italic">

W

</mi>

<mo>

=

</mo>

<msub>
<mi mathvariant="bold-italic">

W

</mi>

<mn>

0

</mn>
</msub>

<mo>

+

</mo>

<mi mathvariant="normal">

Δ

</mi>

<mi mathvariant="bold-italic">

W

</mi>
</mrow>

<annotation encoding="application/x-tex">

\boldsymbol{W} = \boldsymbol{W}_0 + \Delta \boldsymbol{W}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6861em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord,boldsymbol" style="margin-right:0.1597em;">

W

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
<span className="strut" style="height:0.8361em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord">
<span className="mord,boldsymbol" style="margin-right:0.1597em;">

W

</span>
</span>
</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-right:0.05em;">
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
<span className="strut" style="height:0.6861em;">



</span>

<span className="mord">

Δ

</span>

<span className="mord">
<span className="mord">
<span className="mord,boldsymbol" style="margin-right:0.1597em;">

W

</span>
</span>
</span>
</span>
</span>
</span>


其中 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi mathvariant="bold-italic">

W

</mi>

<mn>

0

</mn>
</msub>

<mo>

∈

</mo>

<msup>
<mi mathvariant="double-struck">

R

</mi>

<mrow>
<mi>

m

</mi>

<mo>

×

</mo>

<mi>

n

</mi>
</mrow>
</msup>
</mrow>

<annotation encoding="application/x-tex">

\boldsymbol{W}_0 \in \mathbb{R}^{m \times n}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8361em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord">
<span className="mord,boldsymbol" style="margin-right:0.1597em;">

W

</span>
</span>
</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-right:0.05em;">
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

∈

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.7713em;">



</span>

<span className="mord">
<span className="mord,mathbb">

R

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

m

</span>

<span className="mbin,mtight">

×

</span>

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
</span>

 是预训练的初始权重矩阵,<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi mathvariant="normal">

Δ

</mi>

<mi mathvariant="bold-italic">

W

</mi>

<mo>

∈

</mo>

<msup>
<mi mathvariant="double-struck">

R

</mi>

<mrow>
<mi>

m

</mi>

<mo>

×

</mo>

<mi>

n

</mi>
</mrow>
</msup>
</mrow>

<annotation encoding="application/x-tex">

\Delta \boldsymbol{W} \in \mathbb{R}^{m \times n}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.7252em;vertical-align:-0.0391em;">



</span>

<span className="mord">

Δ

</span>

<span className="mord">
<span className="mord">
<span className="mord,boldsymbol" style="margin-right:0.1597em;">

W

</span>
</span>
</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

∈

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.7713em;">



</span>

<span className="mord">
<span className="mord,mathbb">

R

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

m

</span>

<span className="mbin,mtight">

×

</span>

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
</span>

 是权重更新量。为了降低参数量,将 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi mathvariant="normal">

Δ

</mi>

<mi mathvariant="bold-italic">

W

</mi>
</mrow>

<annotation encoding="application/x-tex">

\Delta \boldsymbol{W}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6861em;">



</span>

<span className="mord">

Δ

</span>

<span className="mord">
<span className="mord">
<span className="mord,boldsymbol" style="margin-right:0.1597em;">

W

</span>
</span>
</span>
</span>
</span>
</span>

 分解为两个低秩矩阵的乘积:

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi mathvariant="normal">

Δ

</mi>

<mi mathvariant="bold-italic">

W

</mi>

<mo>

=

</mo>

<mi mathvariant="bold-italic">

B

</mi>

<mi mathvariant="bold-italic">

A

</mi>
</mrow>

<annotation encoding="application/x-tex">

\Delta \boldsymbol{W} = \boldsymbol{B} \boldsymbol{A}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6861em;">



</span>

<span className="mord">

Δ

</span>

<span className="mord">
<span className="mord">
<span className="mord,boldsymbol" style="margin-right:0.1597em;">

W

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
<span className="strut" style="height:0.6861em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord,boldsymbol" style="margin-right:0.0483em;">

B

</span>
</span>
</span>

<span className="mord">
<span className="mord">
<span className="mord,boldsymbol">

A

</span>
</span>
</span>
</span>
</span>
</span>
</span>

其中 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi mathvariant="bold-italic">

B

</mi>

<mo>

∈

</mo>

<msup>
<mi mathvariant="double-struck">

R

</mi>

<mrow>
<mi>

m

</mi>

<mo>

×

</mo>

<mi>

r

</mi>
</mrow>
</msup>
</mrow>

<annotation encoding="application/x-tex">

\boldsymbol{B} \in \mathbb{R}^{m \times r}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.7252em;vertical-align:-0.0391em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord,boldsymbol" style="margin-right:0.0483em;">

B

</span>
</span>
</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

∈

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.7713em;">



</span>

<span className="mord">
<span className="mord,mathbb">

R

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

m

</span>

<span className="mbin,mtight">

×

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

r

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

,<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi mathvariant="bold-italic">

A

</mi>

<mo>

∈

</mo>

<msup>
<mi mathvariant="double-struck">

R

</mi>

<mrow>
<mi>

r

</mi>

<mo>

×

</mo>

<mi>

n

</mi>
</mrow>
</msup>
</mrow>

<annotation encoding="application/x-tex">

\boldsymbol{A} \in \mathbb{R}^{r \times n}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.7252em;vertical-align:-0.0391em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord,boldsymbol">

A

</span>
</span>
</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

∈

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.7713em;">



</span>

<span className="mord">
<span className="mord,mathbb">

R

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
<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

r

</span>

<span className="mbin,mtight">

×

</span>

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
</span>

,且 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

r

</mi>

<mo>

≪

</mo>

<mi>

min

</mi>

<mo>

⁡

</mo>

<mo stretchy="false">

(

</mo>

<mi>

m

</mi>

<mo separator="true">

,

</mo>

<mi>

n

</mi>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

r \ll \min(m, n)

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.5782em;vertical-align:-0.0391em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mop">

min

</span>

<span className="mopen">

(

</span>

<span className="mord,mathnormal">

m

</span>

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord,mathnormal">

n

</span>

<span className="mclose">

)

</span>
</span>
</span>
</span>

 是低秩参数。

1. 采用 LoRA 算法进行权重更新:写出基于 LoRA 算法的优化问题,明确指出优化目标函数和优化变量
2. 相比于直接优化 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi mathvariant="bold-italic">

W

</mi>
</mrow>

<annotation encoding="application/x-tex">

\boldsymbol{W}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6861em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord,boldsymbol" style="margin-right:0.1597em;">

W

</span>
</span>
</span>
</span>
</span>
</span>

,采用 LoRA 算法后模型的可训练参数量减少了多少?给出具体的参数量对比分析。
3. 对模型加入正则化:
(a) 给出加入正则化后的优化目标函数,明确指出优化目标和优化变量;
(b) 解释正则化项在 LoRA 算法中的作用。

#### 七、滤波器

令代价函数为 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

f

</mi>

<mo stretchy="false">

(

</mo>

<mi mathvariant="bold-italic">

w

</mi>

<mo stretchy="false">

)

</mo>

<mo>

=

</mo>

<msup>
<mi mathvariant="bold-italic">

w

</mi>

<mi mathvariant="normal">

H

</mi>
</msup>

<msub>
<mi mathvariant="bold-italic">

R

</mi>

<mi>

e

</mi>
</msub>

<mi mathvariant="bold-italic">

w

</mi>
</mrow>

<annotation encoding="application/x-tex">

f(\boldsymbol{w}) = \boldsymbol{w}^{\mathrm{H}}\boldsymbol{R}_e\boldsymbol{w}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1076em;">

f

</span>

<span className="mopen">

(

</span>

<span className="mord">
<span className="mord">
<span className="mord,boldsymbol" style="margin-right:0.0278em;">

w

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
<span className="strut" style="height:0.9913em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord">
<span className="mord,boldsymbol" style="margin-right:0.0278em;">

w

</span>
</span>
</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8413em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathrm,mtight">

H

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

<span className="mord">
<span className="mord">
<span className="mord">
<span className="mord,boldsymbol" style="margin-right:0.0042em;">

R

</span>
</span>
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
<span className="mord,boldsymbol" style="margin-right:0.0278em;">

w

</span>
</span>
</span>
</span>
</span>
</span>

，并且给滤波器加约束条件 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mrow>
<mi mathvariant="normal">

R

</mi>

<mi mathvariant="normal">

e

</mi>
</mrow>

<mo stretchy="false">

(

</mo>

<mrow>
<msup>
<mi mathvariant="bold-italic">

w

</mi>

<mi mathvariant="normal">

H

</mi>
</msup>

<mi mathvariant="bold-italic">

x

</mi>
</mrow>

<mo stretchy="false">

)

</mo>

<mo>

=

</mo>

<mi>

b

</mi>
</mrow>

<annotation encoding="application/x-tex">

\mathrm{Re}({\boldsymbol{w}^{\mathrm{H}}\boldsymbol{x}}) = b

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.0913em;vertical-align:-0.25em;">



</span>

<span className="mord">
<span className="mord,mathrm">

Re

</span>
</span>

<span className="mopen">

(

</span>

<span className="mord">
<span className="mord">
<span className="mord">
<span className="mord">
<span className="mord,boldsymbol" style="margin-right:0.0278em;">

w

</span>
</span>
</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8413em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathrm,mtight">

H

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

<span className="mord">
<span className="mord">
<span className="mord,boldsymbol">

x

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
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,mathnormal">

b

</span>
</span>
</span>
</span>

，其中 <span className="katex">
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

 为一常数，<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi mathvariant="bold-italic">

R

</mi>

<mi>

e

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

\boldsymbol{R}_e

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8361em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord">
<span className="mord,boldsymbol" style="margin-right:0.0042em;">

R

</span>
</span>
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
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

 为一噪声向量 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi mathvariant="bold-italic">

e

</mi>
</mrow>

<annotation encoding="application/x-tex">

\boldsymbol{e}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.4444em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord,boldsymbol">

e

</span>
</span>
</span>
</span>
</span>
</span>

 的协方差矩阵。
(1) 假定 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi mathvariant="bold-italic">

R

</mi>

<mi>

e

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

\boldsymbol{R}_e

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8361em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord">
<span className="mord,boldsymbol" style="margin-right:0.0042em;">

R

</span>
</span>
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
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

 可逆，求最优滤波器 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi mathvariant="bold-italic">

w

</mi>
</mrow>

<annotation encoding="application/x-tex">

\boldsymbol{w}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.4444em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord,boldsymbol" style="margin-right:0.0278em;">

w

</span>
</span>
</span>
</span>
</span>
</span>

。
(2) 考虑 Tikhonov 正则化，正则化超参数取 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

λ

</mi>
</mrow>

<annotation encoding="application/x-tex">

\lambda

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,mathnormal">

λ

</span>
</span>
</span>
</span>

 ，求最优滤波器 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi mathvariant="bold-italic">

w

</mi>
</mrow>

<annotation encoding="application/x-tex">

\boldsymbol{w}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.4444em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord,boldsymbol" style="margin-right:0.0278em;">

w

</span>
</span>
</span>
</span>
</span>
</span>

，并解释正则化参数的作用
(3) 说明当 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi mathvariant="bold-italic">

R

</mi>

<mi>

e

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

\boldsymbol{R}_e

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8361em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord">
<span className="mord,boldsymbol" style="margin-right:0.0042em;">

R

</span>
</span>
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
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

 奇异性很强或奇异时的两种解决方法

#### 八、简答题

(1) 请解释矩阵条件数在**矩阵方程里的**意义，并给出条件数和矩阵奇异值之间的关系

(2) 解释 PCA 主成分分析的实施流程，并且距一个实际应用例子

(3) 考虑约束优化问题 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

min

</mi>

<mo>

⁡

</mo>

<mi>

f

</mi>

<mo stretchy="false">

(

</mo>

<mi mathvariant="bold-italic">

x

</mi>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

\min f(\boldsymbol{x})

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mop">

min

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1076em;">

f

</span>

<span className="mopen">

(

</span>

<span className="mord">
<span className="mord">
<span className="mord,boldsymbol">

x

</span>
</span>
</span>

<span className="mclose">

)

</span>
</span>
</span>
</span>

 subject to <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

g

</mi>

<mi>

i

</mi>
</msub>

<mo stretchy="false">

(

</mo>

<mi mathvariant="bold-italic">

x

</mi>

<mo stretchy="false">

)

</mo>

<mo>

≥

</mo>

<mn>

0

</mn>

<mo separator="true">

,

</mo>

<mi>

i

</mi>

<mo>

=

</mo>

<mn>

1

</mn>

<mo separator="true">

,

</mo>

<mo>

⋯

</mo>

<mtext>



</mtext>

<mo separator="true">

,

</mo>

<mi>

m

</mi>
</mrow>

<annotation encoding="application/x-tex">

g_i(\boldsymbol{x}) \geq 0, i = 1, \cdots, m

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



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

<span className="mopen">

(

</span>

<span className="mord">
<span className="mord">
<span className="mord,boldsymbol">

x

</span>
</span>
</span>

<span className="mclose">

)

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

≥

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.854em;vertical-align:-0.1944em;">



</span>

<span className="mord">

0

</span>

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord,mathnormal">

i

</span>

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

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="minner">

⋯

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord,mathnormal">

m

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

h

</mi>

<mi>

j

</mi>
</msub>

<mo stretchy="false">

(

</mo>

<mi mathvariant="bold-italic">

x

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

<mo separator="true">

,

</mo>

<mi>

j

</mi>

<mo>

=

</mo>

<mn>

1

</mn>

<mo separator="true">

,

</mo>

<mo>

⋯

</mo>

<mtext>



</mtext>

<mo separator="true">

,

</mo>

<mi>

q

</mi>
</mrow>

<annotation encoding="application/x-tex">

h_j(\boldsymbol{x}) = 0, j = 1, \cdots, q

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

<span className="mopen">

(

</span>

<span className="mord">
<span className="mord">
<span className="mord,boldsymbol">

x

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
<span className="strut" style="height:0.854em;vertical-align:-0.1944em;">



</span>

<span className="mord">

0

</span>

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0572em;">

j

</span>

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

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="minner">

⋯

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

q

</span>
</span>
</span>
</span>

，分别给出使用混合外罚函数和混合内罚函数对应的**目标优化函数表达式**；

---

下面是 PDF 版本

<embed src="/pdf/posts/ugcourses/junior-autumn/matrix/matrix/回忆卷.pdf" width="100%" height="600" type="application/pdf">



</embed>
