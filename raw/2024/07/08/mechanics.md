# about力学

> 从高中的时候就一直想总结一下，但苦于没有时间。

## 前言

从高中的时候就一直想总结一下，但苦于没有时间。

现在有时间了，顺便用用markdown，总结一下脑子里的物理知识有哪些(～￣▽￣)～

顺便稍稍复习一下下学期即将开课的大物I

> 二编：寒假的时候略无聊，心血来潮想写写的笔记，幻想着能复习一下大物I，可惜这学期太忙了根本没听课（误）。（放在这里做下测试吧）下学期大物II提前上完了，不过还有固体物理，后面应该会更新笔记的<br />
> 
>                          ————————哎，为数不多的物理课了......(心向物理bushi)

## 力学

### 一、运动的描述（运动学）：

##### Describe objects：

1.位置：位置矢量**r**

2.速度：速度矢量**v**= <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mfrac>
<mrow>
<mi>

d

</mi>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

r

</mi>
</mstyle>
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

\frac{d\pmb{r}}{dt}

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

<span className="mord,mtight" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

r

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



3.加速度：**a**=  <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mfrac>
<mrow>
<mi>

d

</mi>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

v

</mi>
</mstyle>
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

\frac{d\pmb{v}}{dt}

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

<span className="mord,mtight" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

v

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



#### （一）对于同一参考系下不同“视角”的描述

##### 坐标系​下的描述

###### 1.任意曲线坐标系：**u**,**v**,**w**

对于其坐标下物体的小位移，对应**r**矢量小位移<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

d

</mi>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

r

</mi>
</mstyle>
</mrow>

<annotation encoding="application/x-tex">

d\pmb{r}

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>
</span>
</span>
</span>
</span>

，有

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

d

</mi>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

r

</mi>
</mstyle>

<mo>

=

</mo>

<mstyle scriptlevel="0" displaystyle="true">
<mfrac>
<mrow>
<mi mathvariant="normal">

∂

</mi>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

r

</mi>
</mstyle>
</mrow>

<mrow>
<mi mathvariant="normal">

∂

</mi>

<mi>

u

</mi>
</mrow>
</mfrac>
</mstyle>

<mi>

d

</mi>

<mi>

u

</mi>

<mo>

+

</mo>

<mstyle scriptlevel="0" displaystyle="true">
<mfrac>
<mrow>
<mi mathvariant="normal">

∂

</mi>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

r

</mi>
</mstyle>
</mrow>

<mrow>
<mi mathvariant="normal">

∂

</mi>

<mi>

v

</mi>
</mrow>
</mfrac>
</mstyle>

<mi>

d

</mi>

<mi>

v

</mi>

<mo>

+

</mo>

<mstyle scriptlevel="0" displaystyle="true">
<mfrac>
<mrow>
<mi mathvariant="normal">

∂

</mi>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

r

</mi>
</mstyle>
</mrow>

<mrow>
<mi mathvariant="normal">

∂

</mi>

<mi>

w

</mi>
</mrow>
</mfrac>
</mstyle>

<mi>

d

</mi>

<mi>

w

</mi>
</mrow>

<annotation encoding="application/x-tex">

d\pmb{r}=\dfrac{\partial \pmb{r}}{\partial u}du+\dfrac{\partial \pmb{r}}{\partial v}dv+\dfrac{\partial \pmb{r}}{\partial w}dw

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

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
<span className="mord" style="margin-right:0.0556em;">

∂

</span>

<span className="mord,mathnormal">

u

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
<span className="mord" style="margin-right:0.0556em;">

∂

</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

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

<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal">

u

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
<span className="mord" style="margin-right:0.0556em;">

∂

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

v

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
<span className="mord" style="margin-right:0.0556em;">

∂

</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

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

<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

v

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
<span className="mord" style="margin-right:0.0556em;">

∂

</span>

<span className="mord,mathnormal" style="margin-right:0.0269em;">

w

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
<span className="mord" style="margin-right:0.0556em;">

∂

</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

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

<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal" style="margin-right:0.0269em;">

w

</span>
</span>
</span>
</span>
</span>

###### 实例：

1.直角坐标系：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

d

</mi>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

r

</mi>
</mstyle>

<mo>

=

</mo>

<mstyle scriptlevel="0" displaystyle="true">
<mfrac>
<mrow>
<mi mathvariant="normal">

∂

</mi>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

r

</mi>
</mstyle>
</mrow>

<mrow>
<mi mathvariant="normal">

∂

</mi>

<mi>

x

</mi>
</mrow>
</mfrac>
</mstyle>

<mi>

d

</mi>

<mi>

x

</mi>

<mo>

+

</mo>

<mstyle scriptlevel="0" displaystyle="true">
<mfrac>
<mrow>
<mi mathvariant="normal">

∂

</mi>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

r

</mi>
</mstyle>
</mrow>

<mrow>
<mi mathvariant="normal">

∂

</mi>

<mi>

y

</mi>
</mrow>
</mfrac>
</mstyle>

<mi>

d

</mi>

<mi>

y

</mi>

<mo>

+

</mo>

<mstyle scriptlevel="0" displaystyle="true">
<mfrac>
<mrow>
<mi mathvariant="normal">

∂

</mi>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

r

</mi>
</mstyle>
</mrow>

<mrow>
<mi mathvariant="normal">

∂

</mi>

<mi>

z

</mi>
</mrow>
</mfrac>
</mstyle>

<mi>

d

</mi>

<mi>

z

</mi>
</mrow>

<annotation encoding="application/x-tex">

d\pmb{r}=\dfrac{\partial \pmb{r}}{\partial x}dx+\dfrac{\partial \pmb{r}}{\partial y}dy+\dfrac{\partial \pmb{r}}{\partial z}dz

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

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
<span className="mord" style="margin-right:0.0556em;">

∂

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
<span className="mord" style="margin-right:0.0556em;">

∂

</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

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

<span className="mord,mathnormal">

d

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
</span>

<span className="base">
<span className="strut" style="height:2.2519em;vertical-align:-0.8804em;">



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
<span className="mord" style="margin-right:0.0556em;">

∂

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

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
<span className="mord" style="margin-right:0.0556em;">

∂

</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

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

<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

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
<span className="mord" style="margin-right:0.0556em;">

∂

</span>

<span className="mord,mathnormal" style="margin-right:0.044em;">

z

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
<span className="mord" style="margin-right:0.0556em;">

∂

</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

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

<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal" style="margin-right:0.044em;">

z

</span>
</span>
</span>
</span>
</span>

其中由几何运算：

<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mstyle scriptlevel="0" displaystyle="true">
<mfrac>
<mrow>
<mi mathvariant="normal">

∂

</mi>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

r

</mi>
</mstyle>
</mrow>

<mrow>
<mi mathvariant="normal">

∂

</mi>

<mi>

x

</mi>
</mrow>
</mfrac>
</mstyle>
</mrow>

<annotation encoding="application/x-tex">

\dfrac{\partial \pmb{r}}{\partial x}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
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
<span className="mord" style="margin-right:0.0556em;">

∂

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
<span className="mord" style="margin-right:0.0556em;">

∂

</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

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

即为沿x轴方向单位矢量<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mover accent="true">
<mi>

x

</mi>

<mo>

^

</mo>
</mover>
</mstyle>
</mrow>

<annotation encoding="application/x-tex">

\pmb{\hat{x}}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,accent">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.6944em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal">

x

</span>
</span>

<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.2222em;">
<span className="mord">

^

</span>
</span>
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
<mstyle scriptlevel="0" displaystyle="true">
<mfrac>
<mrow>
<mi mathvariant="normal">

∂

</mi>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

r

</mi>
</mstyle>
</mrow>

<mrow>
<mi mathvariant="normal">

∂

</mi>

<mi>

y

</mi>
</mrow>
</mfrac>
</mstyle>
</mrow>

<annotation encoding="application/x-tex">

\dfrac{\partial \pmb{r}}{\partial y}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:2.2519em;vertical-align:-0.8804em;">



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
<span className="mord" style="margin-right:0.0556em;">

∂

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

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
<span className="mord" style="margin-right:0.0556em;">

∂

</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

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

即为沿y轴方向单位矢量<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mover accent="true">
<mi>

y

</mi>

<mo>

^

</mo>
</mover>
</mstyle>
</mrow>

<annotation encoding="application/x-tex">

\pmb{\hat{y}}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,accent">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.6944em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

</span>
</span>

<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.1944em;">
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
</span>

​

<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mstyle scriptlevel="0" displaystyle="true">
<mfrac>
<mrow>
<mi mathvariant="normal">

∂

</mi>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

r

</mi>
</mstyle>
</mrow>

<mrow>
<mi mathvariant="normal">

∂

</mi>

<mi>

z

</mi>
</mrow>
</mfrac>
</mstyle>
</mrow>

<annotation encoding="application/x-tex">

\dfrac{\partial \pmb{r}}{\partial z}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
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
<span className="mord" style="margin-right:0.0556em;">

∂

</span>

<span className="mord,mathnormal" style="margin-right:0.044em;">

z

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
<span className="mord" style="margin-right:0.0556em;">

∂

</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

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

即为沿z轴方向单位矢量<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mover accent="true">
<mi>

z

</mi>

<mo>

^

</mo>
</mover>
</mstyle>
</mrow>

<annotation encoding="application/x-tex">

\pmb{\hat{z}}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,accent">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.6944em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.044em;">

z

</span>
</span>

<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.1944em;">
<span className="mord">

^

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

​

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mtext>

亦即

</mtext>

<mi>

d

</mi>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

r

</mi>
</mstyle>

<mo>

=

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mover accent="true">
<mi>

x

</mi>

<mo>

^

</mo>
</mover>
</mstyle>

<mi>

d

</mi>

<mi>

x

</mi>

<mo>

+

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mover accent="true">
<mi>

y

</mi>

<mo>

^

</mo>
</mover>
</mstyle>

<mi>

d

</mi>

<mi>

y

</mi>

<mo>

+

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mover accent="true">
<mi>

z

</mi>

<mo>

^

</mo>
</mover>
</mstyle>

<mi>

d

</mi>
</mrow>

<annotation encoding="application/x-tex">

\text{亦即}d\pmb{r}=\pmb{\hat{x}}dx+\pmb{\hat{y}}dy+\pmb{\hat{z}}d

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

亦即

</span>
</span>

<span className="mord,mathnormal">

d

</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,accent">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.6944em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal">

x

</span>
</span>

<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.2222em;">
<span className="mord">

^

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

<span className="mord,mathnormal">

d

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
</span>

<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,accent">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.6944em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

</span>
</span>

<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.1944em;">
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

<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,accent">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.6944em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.044em;">

z

</span>
</span>

<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.1944em;">
<span className="mord">

^

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

<span className="mord,mathnormal">

d

</span>
</span>
</span>
</span>
</span>

速度

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

v

</mi>
</mstyle>

<mo>

=

</mo>

<mstyle scriptlevel="0" displaystyle="true">
<mfrac>
<mrow>
<mi>

d

</mi>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

r

</mi>
</mstyle>
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
</mstyle>

<mo>

=

</mo>

<mfrac>
<mrow>
<mi>

d

</mi>

<mi>

x

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

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mover accent="true">
<mi>

x

</mi>

<mo>

^

</mo>
</mover>
</mstyle>

<mo>

+

</mo>

<mfrac>
<mrow>
<mi>

d

</mi>

<mi>

y

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

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mover accent="true">
<mi>

y

</mi>

<mo>

^

</mo>
</mover>
</mstyle>

<mo>

+

</mo>

<mfrac>
<mrow>
<mi>

d

</mi>

<mi>

z

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

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mover accent="true">
<mi>

z

</mi>

<mo>

^

</mo>
</mover>
</mstyle>
</mrow>

<annotation encoding="application/x-tex">

\pmb{v}=\dfrac{d\pmb{r}}{dt}=\frac{dx}{dt}\pmb{\hat{x}}+\frac{dy}{dt}\pmb{\hat{y}}+\frac{dz}{dt}\pmb{\hat{z}}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.4306em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

v

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

t

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

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

<span className="mord,mathnormal">

t

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,accent">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.6944em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal">

x

</span>
</span>

<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.2222em;">
<span className="mord">

^

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

<span className="mord,mathnormal">

t

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,accent">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.6944em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

</span>
</span>

<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.1944em;">
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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



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

<span className="mord,mathnormal">

t

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

<span className="mord,mathnormal" style="margin-right:0.044em;">

z

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,accent">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.6944em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.044em;">

z

</span>
</span>

<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.1944em;">
<span className="mord">

^

</span>
</span>
</span>
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

<mover accent="true">
<mi>

x

</mi>

<mo>

˙

</mo>
</mover>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mover accent="true">
<mi>

x

</mi>

<mo>

^

</mo>
</mover>
</mstyle>

<mo>

+

</mo>

<mover accent="true">
<mi>

y

</mi>

<mo>

˙

</mo>
</mover>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mover accent="true">
<mi>

y

</mi>

<mo>

^

</mo>
</mover>
</mstyle>

<mo>

+

</mo>

<mover accent="true">
<mi>

z

</mi>

<mo>

˙

</mo>
</mover>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mover accent="true">
<mi>

z

</mi>

<mo>

^

</mo>
</mover>
</mstyle>
</mrow>

<annotation encoding="application/x-tex">

=\dot{x}\pmb{\hat{x}}+\dot{y}\pmb{\hat{y}}+\dot{z}\pmb{\hat{z}}

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
<span className="strut" style="height:0.7778em;vertical-align:-0.0833em;">



</span>

<span className="mord,accent">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.6679em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal">

x

</span>
</span>

<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.1111em;">
<span className="mord">

˙

</span>
</span>
</span>
</span>
</span>
</span>
</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,accent">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.6944em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal">

x

</span>
</span>

<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.2222em;">
<span className="mord">

^

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
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,accent">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.6679em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

</span>
</span>

<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.0833em;">
<span className="mord">

˙

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,accent">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.6944em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

</span>
</span>

<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.1944em;">
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

<span className="mord,accent">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.6679em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.044em;">

z

</span>
</span>

<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.0833em;">
<span className="mord">

˙

</span>
</span>
</span>
</span>
</span>
</span>
</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,accent">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.6944em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.044em;">

z

</span>
</span>

<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.1944em;">
<span className="mord">

^

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

加速度

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

a

</mi>
</mstyle>

<mo>

=

</mo>

<mfrac>
<mrow>
<mi>

d

</mi>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

v

</mi>
</mstyle>
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

<mo>

=

</mo>

<mover accent="true">
<mi>

x

</mi>

<mo>

¨

</mo>
</mover>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mover accent="true">
<mi>

x

</mi>

<mo>

^

</mo>
</mover>
</mstyle>

<mo>

+

</mo>

<mover accent="true">
<mi>

y

</mi>

<mo>

¨

</mo>
</mover>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mover accent="true">
<mi>

y

</mi>

<mo>

^

</mo>
</mover>
</mstyle>

<mo>

+

</mo>

<mover accent="true">
<mi>

z

</mi>

<mo>

¨

</mo>
</mover>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mover accent="true">
<mi>

z

</mi>

<mo>

^

</mo>
</mover>
</mstyle>
</mrow>

<annotation encoding="application/x-tex">

\pmb{a}=\frac{d\pmb{v}}{dt}=\ddot{x}\pmb{\hat{x}}+\ddot{y}\pmb{\hat{y}}+\ddot{z}\pmb{\hat{z}}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.4306em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal">

a

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

t

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

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
<span className="strut" style="height:0.7778em;vertical-align:-0.0833em;">



</span>

<span className="mord,accent">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.6679em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal">

x

</span>
</span>

<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.2222em;">
<span className="mord">

¨

</span>
</span>
</span>
</span>
</span>
</span>
</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,accent">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.6944em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal">

x

</span>
</span>

<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.2222em;">
<span className="mord">

^

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
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,accent">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.6679em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

</span>
</span>

<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.1944em;">
<span className="mord">

¨

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,accent">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.6944em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

</span>
</span>

<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.1944em;">
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

<span className="mord,accent">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.6679em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.044em;">

z

</span>
</span>

<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.1944em;">
<span className="mord">

¨

</span>
</span>
</span>
</span>
</span>
</span>
</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,accent">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.6944em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.044em;">

z

</span>
</span>

<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.1944em;">
<span className="mord">

^

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

**PS:**(由于直角坐标的单位正交基不是 位置or时间 的函数，在其坐标下的导数就 等于 对应分量导数的矢量和)

2.柱坐标系：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

d

</mi>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

r

</mi>
</mstyle>

<mo>

=

</mo>

<mstyle scriptlevel="0" displaystyle="true">
<mfrac>
<mrow>
<mi mathvariant="normal">

∂

</mi>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

r

</mi>
</mstyle>
</mrow>

<mrow>
<mi mathvariant="normal">

∂

</mi>

<mi>

ρ

</mi>
</mrow>
</mfrac>
</mstyle>

<mi>

d

</mi>

<mi>

ρ

</mi>

<mo>

+

</mo>

<mstyle scriptlevel="0" displaystyle="true">
<mfrac>
<mrow>
<mi mathvariant="normal">

∂

</mi>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

r

</mi>
</mstyle>
</mrow>

<mrow>
<mi mathvariant="normal">

∂

</mi>

<mi>

θ

</mi>
</mrow>
</mfrac>
</mstyle>

<mi>

d

</mi>

<mi>

θ

</mi>

<mo>

+

</mo>

<mstyle scriptlevel="0" displaystyle="true">
<mfrac>
<mrow>
<mi mathvariant="normal">

∂

</mi>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

r

</mi>
</mstyle>
</mrow>

<mrow>
<mi mathvariant="normal">

∂

</mi>

<mi>

z

</mi>
</mrow>
</mfrac>
</mstyle>

<mi>

d

</mi>

<mi>

z

</mi>
</mrow>

<annotation encoding="application/x-tex">

d\pmb{r}=\dfrac{\partial \pmb{r}}{\partial \rho}d\rho+\dfrac{\partial \pmb{r}}{\partial \theta}d\theta+\dfrac{\partial \pmb{r}}{\partial z}dz

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

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
<span className="strut" style="height:2.2519em;vertical-align:-0.8804em;">



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
<span className="mord" style="margin-right:0.0556em;">

∂

</span>

<span className="mord,mathnormal">

ρ

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
<span className="mord" style="margin-right:0.0556em;">

∂

</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

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

<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal">

ρ

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
<span className="mord" style="margin-right:0.0556em;">

∂

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

θ

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
<span className="mord" style="margin-right:0.0556em;">

∂

</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

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

<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

θ

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
<span className="mord" style="margin-right:0.0556em;">

∂

</span>

<span className="mord,mathnormal" style="margin-right:0.044em;">

z

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
<span className="mord" style="margin-right:0.0556em;">

∂

</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

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

<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal" style="margin-right:0.044em;">

z

</span>
</span>
</span>
</span>
</span>

其中由几何运算：

<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mstyle scriptlevel="0" displaystyle="true">
<mfrac>
<mrow>
<mi mathvariant="normal">

∂

</mi>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

r

</mi>
</mstyle>
</mrow>

<mrow>
<mi mathvariant="normal">

∂

</mi>

<mi>

ρ

</mi>
</mrow>
</mfrac>
</mstyle>
</mrow>

<annotation encoding="application/x-tex">

\dfrac{\partial \pmb{r}}{\partial \rho}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:2.2519em;vertical-align:-0.8804em;">



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
<span className="mord" style="margin-right:0.0556em;">

∂

</span>

<span className="mord,mathnormal">

ρ

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
<span className="mord" style="margin-right:0.0556em;">

∂

</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

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

为沿<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

ρ

</mi>
</mrow>

<annotation encoding="application/x-tex">

\rho

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
</span>
</span>
</span>

方向单位矢量<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mover accent="true">
<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

ρ

</mi>
</mstyle>

<mo>

^

</mo>
</mover>
</mrow>

<annotation encoding="application/x-tex">

\hat{\pmb{\rho}}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,accent">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.6944em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal">

ρ

</span>
</span>
</span>

<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.25em;">
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



<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mstyle scriptlevel="0" displaystyle="true">
<mfrac>
<mrow>
<mi mathvariant="normal">

∂

</mi>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

r

</mi>
</mstyle>
</mrow>

<mrow>
<mi mathvariant="normal">

∂

</mi>

<mi>

θ

</mi>
</mrow>
</mfrac>
</mstyle>
</mrow>

<annotation encoding="application/x-tex">

\dfrac{\partial \pmb{r}}{\partial \theta}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
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
<span className="mord" style="margin-right:0.0556em;">

∂

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

θ

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
<span className="mord" style="margin-right:0.0556em;">

∂

</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

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

为<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

ρ

</mi>

<mover accent="true">
<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

θ

</mi>
</mstyle>

<mo>

^

</mo>
</mover>
</mrow>

<annotation encoding="application/x-tex">

\rho\hat{\pmb{\theta}}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.1523em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal">

ρ

</span>

<span className="mord,accent">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.9579em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

θ

</span>
</span>
</span>

<span style="top:-3.2634em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.25em;">
<span className="mord">

^

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

,其中<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mover accent="true">
<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

θ

</mi>
</mstyle>

<mo>

^

</mo>
</mover>
</mrow>

<annotation encoding="application/x-tex">

\hat{\pmb{\theta}}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9579em;">



</span>

<span className="mord,accent">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.9579em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

θ

</span>
</span>
</span>

<span style="top:-3.2634em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.25em;">
<span className="mord">

^

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

为沿<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

θ

</mi>
</mstyle>
</mrow>

<annotation encoding="application/x-tex">

\pmb{\theta}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

θ

</span>
</span>
</span>
</span>
</span>

方向(切向)单位矢量

<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mstyle scriptlevel="0" displaystyle="true">
<mfrac>
<mrow>
<mi mathvariant="normal">

∂

</mi>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

r

</mi>
</mstyle>
</mrow>

<mrow>
<mi mathvariant="normal">

∂

</mi>

<mi>

z

</mi>
</mrow>
</mfrac>
</mstyle>
</mrow>

<annotation encoding="application/x-tex">

\dfrac{\partial \pmb{r}}{\partial z}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
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
<span className="mord" style="margin-right:0.0556em;">

∂

</span>

<span className="mord,mathnormal" style="margin-right:0.044em;">

z

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
<span className="mord" style="margin-right:0.0556em;">

∂

</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

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

即为沿z轴方向单位矢量<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mover accent="true">
<mi>

x

</mi>

<mo>

^

</mo>
</mover>
</mstyle>
</mrow>

<annotation encoding="application/x-tex">

\pmb{\hat{x}}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,accent">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.6944em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal">

x

</span>
</span>

<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.2222em;">
<span className="mord">

^

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

​

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mtext>

亦即

</mtext>

<mi>

d

</mi>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

r

</mi>
</mstyle>

<mo>

=

</mo>

<mi>

d

</mi>

<mi>

ρ

</mi>

<mover accent="true">
<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

ρ

</mi>
</mstyle>

<mo>

^

</mo>
</mover>

<mo>

+

</mo>

<mi>

ρ

</mi>

<mi>

d

</mi>

<mi>

θ

</mi>

<mover accent="true">
<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

θ

</mi>
</mstyle>

<mo>

^

</mo>
</mover>

<mo>

+

</mo>

<mi>

d

</mi>

<mi>

z

</mi>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mover accent="true">
<mi>

z

</mi>

<mo>

^

</mo>
</mover>
</mstyle>
</mrow>

<annotation encoding="application/x-tex">

亦即d\pmb{r}=d\rho\hat{\pmb{\rho}}+\rho d\theta\hat{\pmb{\theta}}+dz\pmb{\hat{z}}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,cjk_fallback">

亦即

</span>

<span className="mord,mathnormal">

d

</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

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

<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal">

ρ

</span>

<span className="mord,accent">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.6944em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal">

ρ

</span>
</span>
</span>

<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.25em;">
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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.1523em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal">

ρ

</span>

<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

θ

</span>

<span className="mord,accent">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.9579em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

θ

</span>
</span>
</span>

<span style="top:-3.2634em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.25em;">
<span className="mord">

^

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
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal" style="margin-right:0.044em;">

z

</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,accent">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.6944em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.044em;">

z

</span>
</span>

<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.1944em;">
<span className="mord">

^

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

速度

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

v

</mi>
</mstyle>

<mo>

=

</mo>

<mfrac>
<mrow>
<mi>

d

</mi>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

r

</mi>
</mstyle>
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

<mo>

=

</mo>

<mover accent="true">
<mi>

ρ

</mi>

<mo>

˙

</mo>
</mover>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mover accent="true">
<mi>

ρ

</mi>

<mo>

^

</mo>
</mover>
</mstyle>

<mo>

+

</mo>

<mi>

ρ

</mi>

<mover accent="true">
<mi>

θ

</mi>

<mo>

˙

</mo>
</mover>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mover accent="true">
<mi>

θ

</mi>

<mo>

^

</mo>
</mover>
</mstyle>

<mo>

+

</mo>

<mover accent="true">
<mi>

z

</mi>

<mo>

˙

</mo>
</mover>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mover accent="true">
<mi>

z

</mi>

<mo>

^

</mo>
</mover>
</mstyle>
</mrow>

<annotation encoding="application/x-tex">

\pmb{v}=\frac{d\pmb{r}}{dt}=\dot{\rho}\pmb{\hat{\rho}}+\rho\dot{\theta}\pmb{\hat{\theta}}+\dot{z}\pmb{\hat{z}}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.4306em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

v

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

t

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

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
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,accent">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.6679em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal">

ρ

</span>
</span>

<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.0556em;">
<span className="mord">

˙

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,accent">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.6944em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal">

ρ

</span>
</span>

<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.1667em;">
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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.1523em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal">

ρ

</span>

<span className="mord,accent">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.9313em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

θ

</span>
</span>

<span style="top:-3.2634em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.0556em;">
<span className="mord">

˙

</span>
</span>
</span>
</span>
</span>
</span>
</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,accent">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.9579em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

θ

</span>
</span>

<span style="top:-3.2634em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.1667em;">
<span className="mord">

^

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
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,accent">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.6679em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.044em;">

z

</span>
</span>

<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.0833em;">
<span className="mord">

˙

</span>
</span>
</span>
</span>
</span>
</span>
</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,accent">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.6944em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.044em;">

z

</span>
</span>

<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.1944em;">
<span className="mord">

^

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

加速度

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

a

</mi>
</mstyle>

<mo>

=

</mo>

<mfrac>
<mrow>
<mi>

d

</mi>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

v

</mi>
</mstyle>
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

<mo>

=

</mo>

<mover accent="true">
<mi>

ρ

</mi>

<mo>

¨

</mo>
</mover>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mover accent="true">
<mi>

ρ

</mi>

<mo>

^

</mo>
</mover>
</mstyle>

<mo>

+

</mo>

<mover accent="true">
<mi>

ρ

</mi>

<mo>

˙

</mo>
</mover>

<mfrac>
<mrow>
<mi>

d

</mi>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mover accent="true">
<mi>

ρ

</mi>

<mo>

^

</mo>
</mover>
</mstyle>
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

<mo>

+

</mo>

<mover accent="true">
<mi>

ρ

</mi>

<mo>

˙

</mo>
</mover>

<mover accent="true">
<mi>

θ

</mi>

<mo>

˙

</mo>
</mover>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mover accent="true">
<mi>

θ

</mi>

<mo>

^

</mo>
</mover>
</mstyle>

<mo>

+

</mo>

<mover accent="true">
<mi>

ρ

</mi>

<mo>

˙

</mo>
</mover>

<mover accent="true">
<mi>

θ

</mi>

<mo>

¨

</mo>
</mover>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mover accent="true">
<mi>

θ

</mi>

<mo>

^

</mo>
</mover>
</mstyle>

<mo>

+

</mo>

<mi>

ρ

</mi>

<mover accent="true">
<mi>

θ

</mi>

<mo>

˙

</mo>
</mover>

<mfrac>
<mrow>
<mi>

d

</mi>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mover accent="true">
<mi>

θ

</mi>

<mo>

^

</mo>
</mover>
</mstyle>
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

<mo>

+

</mo>

<mover accent="true">
<mi>

z

</mi>

<mo>

¨

</mo>
</mover>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mover accent="true">
<mi>

z

</mi>

<mo>

^

</mo>
</mover>
</mstyle>
</mrow>

<annotation encoding="application/x-tex">

\pmb{a}=\frac{d\pmb{v}}{dt}=\ddot{\rho}\pmb{\hat{\rho}}+\dot{\rho}\frac{d\pmb{\hat{\rho}}}{dt}+\dot{\rho}\dot{\theta}\pmb{\hat{\theta}}+\dot{\rho}\ddot{\theta}\pmb{\hat{\theta}}+\rho\dot{\theta}\frac{d\pmb{\hat{\theta}}}{dt}+\ddot{z}\pmb{\hat{z}}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.4306em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal">

a

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

t

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

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
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,accent">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.6679em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal">

ρ

</span>
</span>

<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.1667em;">
<span className="mord">

¨

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,accent">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.6944em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal">

ρ

</span>
</span>

<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.1667em;">
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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:2.0574em;vertical-align:-0.686em;">



</span>

<span className="mord,accent">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.6679em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal">

ρ

</span>
</span>

<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.0556em;">
<span className="mord">

˙

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

t

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,accent">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.6944em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal">

ρ

</span>
</span>

<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.1667em;">
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
<span className="strut" style="height:1.1523em;vertical-align:-0.1944em;">



</span>

<span className="mord,accent">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.6679em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal">

ρ

</span>
</span>

<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.0556em;">
<span className="mord">

˙

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

<span className="mord,accent">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.9313em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

θ

</span>
</span>

<span style="top:-3.2634em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.0556em;">
<span className="mord">

˙

</span>
</span>
</span>
</span>
</span>
</span>
</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,accent">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.9579em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

θ

</span>
</span>

<span style="top:-3.2634em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.1667em;">
<span className="mord">

^

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
<span className="strut" style="height:1.1523em;vertical-align:-0.1944em;">



</span>

<span className="mord,accent">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.6679em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal">

ρ

</span>
</span>

<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.0556em;">
<span className="mord">

˙

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

<span className="mord,accent">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.9313em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

θ

</span>
</span>

<span style="top:-3.2634em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.1667em;">
<span className="mord">

¨

</span>
</span>
</span>
</span>
</span>
</span>
</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,accent">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.9579em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

θ

</span>
</span>

<span style="top:-3.2634em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.1667em;">
<span className="mord">

^

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
<span className="strut" style="height:2.3209em;vertical-align:-0.686em;">



</span>

<span className="mord,mathnormal">

ρ

</span>

<span className="mord,accent">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.9313em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

θ

</span>
</span>

<span style="top:-3.2634em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.0556em;">
<span className="mord">

˙

</span>
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
<span className="vlist" style="height:1.6349em;">
<span style="top:-2.314em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal">

t

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,accent">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.9579em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

θ

</span>
</span>

<span style="top:-3.2634em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.1667em;">
<span className="mord">

^

</span>
</span>
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
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,accent">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.6679em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.044em;">

z

</span>
</span>

<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.1944em;">
<span className="mord">

¨

</span>
</span>
</span>
</span>
</span>
</span>
</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,accent">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.6944em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.044em;">

z

</span>
</span>

<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.1944em;">
<span className="mord">

^

</span>
</span>
</span>
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
<mfrac>
<mrow>
<mi>

d

</mi>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mover accent="true">
<mi>

ρ

</mi>

<mo>

^

</mo>
</mover>
</mstyle>
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

<mtext>

和

</mtext>

<mfrac>
<mrow>
<mi>

d

</mi>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mover accent="true">
<mi>

θ

</mi>

<mo>

^

</mo>
</mover>
</mstyle>
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

\frac{d\pmb{\hat{\rho}}}{dt}和\frac{d\pmb{\hat{\theta}}}{dt}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.4095em;vertical-align:-0.345em;">



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

<span style="top:-3.4461em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

d

</span>

<span className="mord,mtight" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,accent,mtight">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.6944em;">
<span style="top:-2.7em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="mord,mathnormal,mtight">

ρ

</span>
</span>

<span style="top:-2.7em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="accent-body" style="left:-0.1667em;">
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

<span className="mord,cjk_fallback">

和

</span>

<span className="mord">
<span className="mopen,nulldelimiter">



</span>

<span className="mfrac">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:1.0645em;">
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

<span className="mord,mtight" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,accent,mtight">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.9579em;">
<span style="top:-2.7em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

θ

</span>
</span>

<span style="top:-2.9634em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="accent-body" style="left:-0.1667em;">
<span className="mord,mtight">

^

</span>
</span>
</span>
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

怎么处理<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mo>

⟶

</mo>
</mrow>

<annotation encoding="application/x-tex">

\longrightarrow

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.522em;vertical-align:-0.011em;">



</span>

<span className="mrel">

⟶

</span>
</span>
</span>
</span>

利用全微分处理，<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

d

</mi>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mover accent="true">
<mi>

ρ

</mi>

<mo>

^

</mo>
</mover>
</mstyle>

<mtext>

和

</mtext>

<mi>

d

</mi>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mover accent="true">
<mi>

θ

</mi>

<mo>

^

</mo>
</mover>
</mstyle>
</mrow>

<annotation encoding="application/x-tex">

d\pmb{\hat{\rho}}和d\pmb{\hat{\theta}}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.1523em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal">

d

</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,accent">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.6944em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal">

ρ

</span>
</span>

<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.1667em;">
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

<span className="mord,cjk_fallback">

和

</span>

<span className="mord,mathnormal">

d

</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,accent">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.9579em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

θ

</span>
</span>

<span style="top:-3.2634em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.1667em;">
<span className="mord">

^

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

对坐标的全微分是可以获得的：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

d

</mi>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mover accent="true">
<mi>

ρ

</mi>

<mo>

^

</mo>
</mover>
</mstyle>

<mo>

=

</mo>

<mfrac>
<mrow>
<mi mathvariant="normal">

∂

</mi>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mover accent="true">
<mi>

ρ

</mi>

<mo>

^

</mo>
</mover>
</mstyle>
</mrow>

<mrow>
<mi mathvariant="normal">

∂

</mi>

<mi>

ρ

</mi>
</mrow>
</mfrac>

<mi>

d

</mi>

<mi>

ρ

</mi>

<mo>

+

</mo>

<mfrac>
<mrow>
<mi mathvariant="normal">

∂

</mi>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mover accent="true">
<mi>

ρ

</mi>

<mo>

^

</mo>
</mover>
</mstyle>
</mrow>

<mrow>
<mi mathvariant="normal">

∂

</mi>

<mi>

θ

</mi>
</mrow>
</mfrac>

<mi>

d

</mi>

<mi>

θ

</mi>

<mspace linebreak="newline">



</mspace>

<mo>

=

</mo>

<mn>

0

</mn>

<mo>

+

</mo>

<mi>

d

</mi>

<mi>

θ

</mi>

<mo>

⋅

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mover accent="true">
<mi>

θ

</mi>

<mo>

^

</mo>
</mover>
</mstyle>

<mspace linebreak="newline">



</mspace>

<mi>

d

</mi>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mover accent="true">
<mi>

θ

</mi>

<mo>

^

</mo>
</mover>
</mstyle>

<mo>

=

</mo>

<mfrac>
<mrow>
<mi mathvariant="normal">

∂

</mi>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mover accent="true">
<mi>

θ

</mi>

<mo>

^

</mo>
</mover>
</mstyle>
</mrow>

<mrow>
<mi mathvariant="normal">

∂

</mi>

<mi>

ρ

</mi>
</mrow>
</mfrac>

<mi>

d

</mi>

<mi>

ρ

</mi>

<mo>

+

</mo>

<mfrac>
<mrow>
<mi mathvariant="normal">

∂

</mi>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mover accent="true">
<mi>

θ

</mi>

<mo>

^

</mo>
</mover>
</mstyle>
</mrow>

<mrow>
<mi mathvariant="normal">

∂

</mi>

<mi>

θ

</mi>
</mrow>
</mfrac>

<mi>

d

</mi>

<mi>

θ

</mi>

<mspace linebreak="newline">



</mspace>

<mo>

=

</mo>

<mi>

d

</mi>

<mi>

ρ

</mi>

<mo>

⋅

</mo>

<mo stretchy="false">

(

</mo>

<mo>

−

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mover accent="true">
<mi>

ρ

</mi>

<mo>

^

</mo>
</mover>
</mstyle>

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

d

</mi>

<mi>

ρ

</mi>

<mo>

⋅

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mover accent="true">
<mi>

ρ

</mi>

<mo>

^

</mo>
</mover>
</mstyle>
</mrow>

<annotation encoding="application/x-tex">

d\pmb{\hat{\rho}}=\frac{\partial\pmb{\hat{\rho}}}{\partial\rho}d\rho+\frac{\partial\pmb{\hat{\rho}}}{\partial\theta}d\theta
\\
=0+d\theta\cdot\pmb{\hat{\theta}}
\\
d\pmb{\hat{\theta}}=\frac{\partial\pmb{\hat{\theta}}}{\partial\rho}d\rho+\frac{\partial\pmb{\hat{\theta}}}{\partial\theta}d\theta
\\
=d\rho\cdot(-\pmb{\hat{\rho}})=-d\rho\cdot\pmb{\hat{\rho}}

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,accent">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.6944em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal">

ρ

</span>
</span>

<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.1667em;">
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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:2.2519em;vertical-align:-0.8804em;">



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
<span className="mord" style="margin-right:0.0556em;">

∂

</span>

<span className="mord,mathnormal">

ρ

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
<span className="mord" style="margin-right:0.0556em;">

∂

</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,accent">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.6944em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal">

ρ

</span>
</span>

<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.1667em;">
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

<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal">

ρ

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
<span className="mord" style="margin-right:0.0556em;">

∂

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

θ

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
<span className="mord" style="margin-right:0.0556em;">

∂

</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,accent">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.6944em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal">

ρ

</span>
</span>

<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.1667em;">
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

<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

θ

</span>
</span>

<span className="mspace,newline">



</span>

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
<span className="strut" style="height:0.7278em;vertical-align:-0.0833em;">



</span>

<span className="mord">

0

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

<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

θ

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
<span className="strut" style="height:0.9579em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,accent">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.9579em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

θ

</span>
</span>

<span style="top:-3.2634em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.1667em;">
<span className="mord">

^

</span>
</span>
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
<span className="strut" style="height:0.9579em;">



</span>

<span className="mord,mathnormal">

d

</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,accent">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.9579em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

θ

</span>
</span>

<span style="top:-3.2634em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.1667em;">
<span className="mord">

^

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
<span className="strut" style="height:2.5153em;vertical-align:-0.8804em;">



</span>

<span className="mord">
<span className="mopen,nulldelimiter">



</span>

<span className="mfrac">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:1.6349em;">
<span style="top:-2.314em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord" style="margin-right:0.0556em;">

∂

</span>

<span className="mord,mathnormal">

ρ

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
<span className="mord" style="margin-right:0.0556em;">

∂

</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,accent">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.9579em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

θ

</span>
</span>

<span style="top:-3.2634em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.1667em;">
<span className="mord">

^

</span>
</span>
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

<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal">

ρ

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
<span className="strut" style="height:2.3209em;vertical-align:-0.686em;">



</span>

<span className="mord">
<span className="mopen,nulldelimiter">



</span>

<span className="mfrac">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:1.6349em;">
<span style="top:-2.314em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord" style="margin-right:0.0556em;">

∂

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

θ

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
<span className="mord" style="margin-right:0.0556em;">

∂

</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,accent">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.9579em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

θ

</span>
</span>

<span style="top:-3.2634em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.1667em;">
<span className="mord">

^

</span>
</span>
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

<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

θ

</span>
</span>

<span className="mspace,newline">



</span>

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
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal">

ρ

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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mopen">

(

</span>

<span className="mord">

−

</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,accent">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.6944em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal">

ρ

</span>
</span>

<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.1667em;">
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
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord">

−

</span>

<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal">

ρ

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
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,accent">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.6944em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal">

ρ

</span>
</span>

<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.1667em;">
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
</span>
</span>

因此

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mfrac>
<mrow>
<mi>

d

</mi>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mover accent="true">
<mi>

ρ

</mi>

<mo>

^

</mo>
</mover>
</mstyle>
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

<mo>

=

</mo>

<mover accent="true">
<mi>

θ

</mi>

<mo>

˙

</mo>
</mover>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mover accent="true">
<mi>

θ

</mi>

<mo>

^

</mo>
</mover>
</mstyle>

<mspace width="1em">



</mspace>

<mfrac>
<mrow>
<mi>

d

</mi>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mover accent="true">
<mi>

θ

</mi>

<mo>

^

</mo>
</mover>
</mstyle>
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

<mo>

=

</mo>

<mo>

−

</mo>

<mover accent="true">
<mi>

ρ

</mi>

<mo>

˙

</mo>
</mover>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mover accent="true">
<mi>

ρ

</mi>

<mo>

^

</mo>
</mover>
</mstyle>
</mrow>

<annotation encoding="application/x-tex">

\frac{d\pmb{\hat{\rho}}}{dt}=\dot{\theta}\pmb{\hat{\theta}}\quad\frac{d\pmb{\hat{\theta}}}{dt}=-\dot{\rho}\pmb{\hat{\rho}}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
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

<span className="mord,mathnormal">

t

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,accent">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.6944em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal">

ρ

</span>
</span>

<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.1667em;">
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
<span className="strut" style="height:2.3209em;vertical-align:-0.686em;">



</span>

<span className="mord,accent">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.9313em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

θ

</span>
</span>

<span style="top:-3.2634em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.0556em;">
<span className="mord">

˙

</span>
</span>
</span>
</span>
</span>
</span>
</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,accent">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.9579em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

θ

</span>
</span>

<span style="top:-3.2634em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.1667em;">
<span className="mord">

^

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

<span className="mord">
<span className="mopen,nulldelimiter">



</span>

<span className="mfrac">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:1.6349em;">
<span style="top:-2.314em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal">

t

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,accent">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.9579em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

θ

</span>
</span>

<span style="top:-3.2634em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.1667em;">
<span className="mord">

^

</span>
</span>
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
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord">

−

</span>

<span className="mord,accent">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.6679em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal">

ρ

</span>
</span>

<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.0556em;">
<span className="mord">

˙

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,accent">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.6944em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal">

ρ

</span>
</span>

<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.1667em;">
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
</span>
</span>

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

a

</mi>
</mstyle>

<mo>

=

</mo>

<mfrac>
<mrow>
<mi>

d

</mi>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

v

</mi>
</mstyle>
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

<mo>

=

</mo>

<mo stretchy="false">

(

</mo>

<mover accent="true">
<mi>

ρ

</mi>

<mo>

¨

</mo>
</mover>

<mo>

−

</mo>

<mi>

ρ

</mi>

<msup>
<mover accent="true">
<mi>

θ

</mi>

<mo>

˙

</mo>
</mover>

<mn>

2

</mn>
</msup>

<mo stretchy="false">

)

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mover accent="true">
<mi>

ρ

</mi>

<mo>

^

</mo>
</mover>
</mstyle>

<mo>

+

</mo>

<mo stretchy="false">

(

</mo>

<mn>

2

</mn>

<mover accent="true">
<mi>

ρ

</mi>

<mo>

˙

</mo>
</mover>

<mover accent="true">
<mi>

θ

</mi>

<mo>

˙

</mo>
</mover>

<mo>

+

</mo>

<mi>

ρ

</mi>

<mover accent="true">
<mi>

θ

</mi>

<mo>

¨

</mo>
</mover>

<mo stretchy="false">

)

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mover accent="true">
<mi>

θ

</mi>

<mo>

^

</mo>
</mover>
</mstyle>

<mo>

+

</mo>

<mover accent="true">
<mi>

z

</mi>

<mo>

¨

</mo>
</mover>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mover accent="true">
<mi>

z

</mi>

<mo>

^

</mo>
</mover>
</mstyle>
</mrow>

<annotation encoding="application/x-tex">

\pmb{a}=\frac{d\pmb{v}}{dt}=(\ddot{\rho}-{\rho}\dot{\theta}^2)\pmb{\hat{\rho}}+(2\dot{\rho}\dot{\theta}+\rho\ddot{\theta})\pmb{\hat{\theta}}+\ddot{z}\pmb{\hat{z}}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.4306em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal">

a

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

t

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mopen">

(

</span>

<span className="mord,accent">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.6679em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal">

ρ

</span>
</span>

<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.1667em;">
<span className="mord">

¨

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

−

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.1813em;vertical-align:-0.25em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

ρ

</span>
</span>

<span className="mord">
<span className="mord,accent">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.9313em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

θ

</span>
</span>

<span style="top:-3.2634em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.0556em;">
<span className="mord">

˙

</span>
</span>
</span>
</span>
</span>
</span>
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

<span className="mclose">

)

</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,accent">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.6944em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal">

ρ

</span>
</span>

<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.1667em;">
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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.1813em;vertical-align:-0.25em;">



</span>

<span className="mopen">

(

</span>

<span className="mord">

2

</span>

<span className="mord,accent">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.6679em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal">

ρ

</span>
</span>

<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.0556em;">
<span className="mord">

˙

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

<span className="mord,accent">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.9313em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

θ

</span>
</span>

<span style="top:-3.2634em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.0556em;">
<span className="mord">

˙

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
<span className="strut" style="height:1.2079em;vertical-align:-0.25em;">



</span>

<span className="mord,mathnormal">

ρ

</span>

<span className="mord,accent">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.9313em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

θ

</span>
</span>

<span style="top:-3.2634em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.1667em;">
<span className="mord">

¨

</span>
</span>
</span>
</span>
</span>
</span>
</span>

<span className="mclose">

)

</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,accent">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.9579em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

θ

</span>
</span>

<span style="top:-3.2634em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.1667em;">
<span className="mord">

^

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
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,accent">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.6679em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.044em;">

z

</span>
</span>

<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.1944em;">
<span className="mord">

¨

</span>
</span>
</span>
</span>
</span>
</span>
</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,accent">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.6944em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.044em;">

z

</span>
</span>

<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.1944em;">
<span className="mord">

^

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

3.球坐标系，推导方式类似，这里直接给出结果

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

a

</mi>
</mstyle>

<mo>

=

</mo>

<mi>

b

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

b

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

<mi mathvariant="normal">

.

</mi>

<mi mathvariant="normal">

.

</mi>

<mi mathvariant="normal">

.

</mi>

<mo stretchy="false">

(

</mo>

<mtext>

手动狗头

</mtext>

<mi>

b

</mi>

<mi>

u

</mi>

<mi>

s

</mi>

<mi>

h

</mi>

<mi>

i

</mi>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

\pmb{a}=balabala...(手动狗头bushi)

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.4306em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal">

a

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

<span className="mord,mathnormal">

ba

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

aba

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord">

...

</span>

<span className="mopen">

(

</span>

<span className="mord,cjk_fallback">

手动狗头

</span>

<span className="mord,mathnormal">

b

</span>

<span className="mord,mathnormal">

u

</span>

<span className="mord,mathnormal">

s

</span>

<span className="mord,mathnormal">

hi

</span>

<span className="mclose">

)

</span>
</span>
</span>
</span>
</span>

4.平面极坐标（直接由柱坐标系退化即可）

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

a

</mi>
</mstyle>

<mo>

=

</mo>

<mfrac>
<mrow>
<mi>

d

</mi>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

v

</mi>
</mstyle>
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

<mo>

=

</mo>

<mo stretchy="false">

(

</mo>

<mover accent="true">
<mi>

ρ

</mi>

<mo>

¨

</mo>
</mover>

<mo>

−

</mo>

<mi>

ρ

</mi>

<msup>
<mover accent="true">
<mi>

θ

</mi>

<mo>

˙

</mo>
</mover>

<mn>

2

</mn>
</msup>

<mo stretchy="false">

)

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mover accent="true">
<mi>

ρ

</mi>

<mo>

^

</mo>
</mover>
</mstyle>

<mo>

+

</mo>

<mo stretchy="false">

(

</mo>

<mn>

2

</mn>

<mover accent="true">
<mi>

ρ

</mi>

<mo>

˙

</mo>
</mover>

<mover accent="true">
<mi>

θ

</mi>

<mo>

˙

</mo>
</mover>

<mo>

+

</mo>

<mi>

ρ

</mi>

<mover accent="true">
<mi>

θ

</mi>

<mo>

¨

</mo>
</mover>

<mo stretchy="false">

)

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mover accent="true">
<mi>

θ

</mi>

<mo>

^

</mo>
</mover>
</mstyle>
</mrow>

<annotation encoding="application/x-tex">

\pmb{a}=\frac{d\pmb{v}}{dt}=(\ddot{\rho}-{\rho}\dot{\theta}^2)\pmb{\hat{\rho}}+(2\dot{\rho}\dot{\theta}+\rho\ddot{\theta})\pmb{\hat{\theta}}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.4306em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal">

a

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

t

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mopen">

(

</span>

<span className="mord,accent">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.6679em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal">

ρ

</span>
</span>

<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.1667em;">
<span className="mord">

¨

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

−

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.1813em;vertical-align:-0.25em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

ρ

</span>
</span>

<span className="mord">
<span className="mord,accent">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.9313em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

θ

</span>
</span>

<span style="top:-3.2634em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.0556em;">
<span className="mord">

˙

</span>
</span>
</span>
</span>
</span>
</span>
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

<span className="mclose">

)

</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,accent">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.6944em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal">

ρ

</span>
</span>

<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.1667em;">
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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.1813em;vertical-align:-0.25em;">



</span>

<span className="mopen">

(

</span>

<span className="mord">

2

</span>

<span className="mord,accent">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.6679em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal">

ρ

</span>
</span>

<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.0556em;">
<span className="mord">

˙

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

<span className="mord,accent">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.9313em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

θ

</span>
</span>

<span style="top:-3.2634em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.0556em;">
<span className="mord">

˙

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
<span className="strut" style="height:1.2079em;vertical-align:-0.25em;">



</span>

<span className="mord,mathnormal">

ρ

</span>

<span className="mord,accent">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.9313em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

θ

</span>
</span>

<span style="top:-3.2634em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.1667em;">
<span className="mord">

¨

</span>
</span>
</span>
</span>
</span>
</span>
</span>

<span className="mclose">

)

</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,accent">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.9579em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

θ

</span>
</span>

<span style="top:-3.2634em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.1667em;">
<span className="mord">

^

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

###### 2.自然坐标系

自然坐标系的运动的描述：

<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mo>

⟶

</mo>
</mrow>

<annotation encoding="application/x-tex">

\longrightarrow

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.522em;vertical-align:-0.011em;">



</span>

<span className="mrel">

⟶

</span>
</span>
</span>
</span>

把运动分解为直线运动和圆周运动

> <mark>
> 
> 其*本质*是对于速度矢量的大小和方向进行度量
> 
> </mark>
> 
> 
> 
> [![curve.jpg](https://s11.ax1x.com/2024/02/01/pFMYz0f.jpg)](https://imgse.com/i/pFMYz0f)
> 
> 这里其实用到了一个思想<span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <mo>
> 
> ⟶
> 
> </mo>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> \longrightarrow
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:0.522em;vertical-align:-0.011em;">
> 
> 
> 
> </span>
> 
> <span className="mrel">
> 
> ⟶
> 
> </span>
> </span>
> </span>
> </span>
> 
> 将时间项<span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <mtext>
> 
> 
> 
> </mtext>
> 
> <mtext>
> 
> 
> 
> </mtext>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> \,\,
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:0em;">
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
> <span className="mspace" style="margin-right:0.1667em;">
> 
> 
> 
> </span>
> </span>
> </span>
> </span>
> 
> **dt**<span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <mtext>
> 
> 
> 
> </mtext>
> 
> <mtext>
> 
> 
> 
> </mtext>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> \,\,
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:0em;">
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
> <span className="mspace" style="margin-right:0.1667em;">
> 
> 
> 
> </span>
> </span>
> </span>
> </span>
> 
> 利用其他不显含时间的量<span className="katex-error" title="ParseError: KaTeX parse error: Can't use function '$' in math mode at position 5: \,\,$̲$\pmb{\omega}$$…" style="color:#cc0000">
> 
> \,\,$$\pmb{\omega}$$\,\,
> 
> </span>
> 
> ​来进行表示
> 
> ​						这与有心力场中轨道微分方程 <mark>
> 
> Binet公式
> 
> </mark>
> 
> 的思想相同

> 沿运动方向：切向加速度
> 
> 垂直运动方向：向心加速度
> 
> <span className="katex-display">
> <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
> <semantics>
> <mrow>
> <mtext>
> 
> 合并在一个式子里即
> 
> </mtext>
> 
> <mstyle style="text-shadow: 0.02em 0.01em 0.04px">
> <mi>
> 
> a
> 
> </mi>
> </mstyle>
> 
> <mo>
> 
> =
> 
> </mo>
> 
> <mfrac>
> <msup>
> <mi>
> 
> v
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
> ρ
> 
> </mi>
> </mfrac>
> 
> <mstyle style="text-shadow: 0.02em 0.01em 0.04px">
> <mover accent="true">
> <mi>
> 
> r
> 
> </mi>
> 
> <mo>
> 
> ^
> 
> </mo>
> </mover>
> </mstyle>
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
> s
> 
> </mi>
> 
> <mo>
> 
> ¨
> 
> </mo>
> </mover>
> 
> <mstyle style="text-shadow: 0.02em 0.01em 0.04px">
> <mover accent="true">
> <mi>
> 
> τ
> 
> </mi>
> 
> <mo>
> 
> ^
> 
> </mo>
> </mover>
> </mstyle>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> 合并在一个式子里即\pmb{a}=\frac{v^2}{\rho}\pmb{\hat{r}}+\ddot{s}\pmb{\hat{\tau}}
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
> <span className="mord,cjk_fallback">
> 
> 合并在一个式子里即
> 
> </span>
> 
> <span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
> <span className="mord,mathnormal">
> 
> a
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
> <span className="strut" style="height:2.3715em;vertical-align:-0.8804em;">
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
> <span className="vlist" style="height:1.4911em;">
> <span style="top:-2.314em;">
> <span className="pstrut" style="height:3em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> <span className="mord,mathnormal">
> 
> ρ
> 
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
> <span style="top:-3.677em;">
> <span className="pstrut" style="height:3em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> <span className="mord">
> <span className="mord,mathnormal" style="margin-right:0.0359em;">
> 
> v
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
> <span className="vlist-s">
> 
> ​
> 
> </span>
> </span>
> 
> <span className="vlist-r">
> <span className="vlist" style="height:0.8804em;">
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
> <span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
> <span className="mord,accent">
> <span className="vlist-t">
> <span className="vlist-r">
> <span className="vlist" style="height:0.6944em;">
> <span style="top:-3em;">
> <span className="pstrut" style="height:3em;">
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
> </span>
> 
> <span style="top:-3em;">
> <span className="pstrut" style="height:3em;">
> 
> 
> 
> </span>
> 
> <span className="accent-body" style="left:-0.1944em;">
> <span className="mord">
> 
> ^
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
> <span className="strut" style="height:0.6944em;">
> 
> 
> 
> </span>
> 
> <span className="mord,accent">
> <span className="vlist-t">
> <span className="vlist-r">
> <span className="vlist" style="height:0.6679em;">
> <span style="top:-3em;">
> <span className="pstrut" style="height:3em;">
> 
> 
> 
> </span>
> 
> <span className="mord,mathnormal">
> 
> s
> 
> </span>
> </span>
> 
> <span style="top:-3em;">
> <span className="pstrut" style="height:3em;">
> 
> 
> 
> </span>
> 
> <span className="accent-body" style="left:-0.1944em;">
> <span className="mord">
> 
> ¨
> 
> </span>
> </span>
> </span>
> </span>
> </span>
> </span>
> </span>
> 
> <span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
> <span className="mord,accent">
> <span className="vlist-t">
> <span className="vlist-r">
> <span className="vlist" style="height:0.6944em;">
> <span style="top:-3em;">
> <span className="pstrut" style="height:3em;">
> 
> 
> 
> </span>
> 
> <span className="mord,mathnormal" style="margin-right:0.1132em;">
> 
> τ
> 
> </span>
> </span>
> 
> <span style="top:-3em;">
> <span className="pstrut" style="height:3em;">
> 
> 
> 
> </span>
> 
> <span className="accent-body" style="left:-0.2222em;">
> <span className="mord">
> 
> ^
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

<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mtext>



</mtext>

<mtext>



</mtext>

<mtext>



</mtext>
</mrow>

<annotation encoding="application/x-tex">

\,\,\,

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0em;">



</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>
</span>
</span>
</span>

另外的应用——软绳坐标（在约束中再提）

#### （二）对于不同参照系下同一“视角下的描述”

##### 参考系

相对于任意参考系，空间是非均匀且各向异性的，即某个物体与其他物体没有相互作用，它在空间中的不同位置和不同指向在力学意义上是不等价的.同样，一般情况下任意参考系中的时间也是非均匀的，即不同时刻也是不等价的.显然，时间和空间的这些性质使力学现象的描述变得复杂.

然而，似乎总是存在某种参考系，空间相对它是均匀的、各向同性的，时间相对于它是均匀的——这样的参考系称为惯性参考系。

————上述两段摘自Landau力学

##### 伽利略变换

对于两个惯性参考系之间的变换，

<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<msup>
<mi>

r

</mi>

<mo mathvariant="normal" lspace="0em" rspace="0em">

′

</mo>
</msup>
</mstyle>

<mo>

=

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

r

</mi>
</mstyle>

<mo>

+

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

u

</mi>
</mstyle>

<mi>

t

</mi>
</mrow>

<annotation encoding="application/x-tex">

\pmb{r'}=\pmb{r}+\pmb{u}t

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.7519em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.6667em;vertical-align:-0.0833em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

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
<span className="strut" style="height:0.6151em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal">

u

</span>
</span>

<span className="mord,mathnormal">

t

</span>
</span>
</span>
</span>

<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msup>
<mi>

t

</mi>

<mo mathvariant="normal" lspace="0em" rspace="0em">

′

</mo>
</msup>

<mo>

=

</mo>

<mi>

t

</mi>
</mrow>

<annotation encoding="application/x-tex">

t'=t

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

t

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
<span className="strut" style="height:0.6151em;">



</span>

<span className="mord,mathnormal">

t

</span>
</span>
</span>
</span>



​两个式子即代表了两个惯性参照系的坐标与时间关系，后者为经典力学中的绝对时间假设

对上式进行求导，得到了两个坐标系的速度变换公式

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<msup>
<mi>

v

</mi>

<mo mathvariant="normal" lspace="0em" rspace="0em">

′

</mo>
</msup>
</mstyle>

<mo>

=

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

v

</mi>
</mstyle>

<mo>

+

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

u

</mi>
</mstyle>
</mrow>

<annotation encoding="application/x-tex">

\pmb{v'}=\pmb{v}+\pmb{u}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8019em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

v

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8019em;">
<span style="top:-3.113em;margin-right:0.05em;">
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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.6667em;vertical-align:-0.0833em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

v

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
<span className="strut" style="height:0.4306em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal">

u

</span>
</span>
</span>
</span>
</span>
</span>

伽利略相对性原理也可以表述为：力学运动方程在伽利略变换下具有不变性（形式不变）

##### 在不同坐标系下描述物体的运动

###### 1.两个互作平动的参照系之间的变换

互作平动，但是未必相对运动是匀速运动<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<msup>
<mi>

r

</mi>

<mo mathvariant="normal" lspace="0em" rspace="0em">

′

</mo>
</msup>
</mstyle>

<mo>

=

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

r

</mi>
</mstyle>

<mo>

+

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

u

</mi>
</mstyle>

<mi>

t

</mi>
</mrow>

<annotation encoding="application/x-tex">

\pmb{r'}=\pmb{r}+\pmb{u}t

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.7519em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.6667em;vertical-align:-0.0833em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

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
<span className="strut" style="height:0.6151em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal">

u

</span>
</span>

<span className="mord,mathnormal">

t

</span>
</span>
</span>
</span>

​ ✘

下面给出变换公式及其推导

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<msup>
<mi>

r

</mi>

<mo mathvariant="normal" lspace="0em" rspace="0em">

′

</mo>
</msup>
</mstyle>

<mo>

=

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

r

</mi>
</mstyle>

<mo>

+

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

ρ

</mi>
</mstyle>
</mrow>

<annotation encoding="application/x-tex">

\pmb{r'}=\pmb{r}+\pmb{\rho}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8019em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8019em;">
<span style="top:-3.113em;margin-right:0.05em;">
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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.6667em;vertical-align:-0.0833em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

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
<span className="strut" style="height:0.625em;vertical-align:-0.1944em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal">

ρ

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
<mfrac>
<mrow>
<mi>

d

</mi>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

ρ

</mi>
</mstyle>
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

<mo>

≜

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

u

</mi>
</mstyle>

<mo separator="true">

,

</mo>

<mfrac>
<mrow>
<mi>

d

</mi>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

r

</mi>
</mstyle>
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

<mo>

≜

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

v

</mi>
</mstyle>

<mo separator="true">

,

</mo>

<mfrac>
<mrow>
<mi>

d

</mi>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<msup>
<mi>

r

</mi>

<mo mathvariant="normal" lspace="0em" rspace="0em">

′

</mo>
</msup>
</mstyle>
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

<mo>

≜

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<msup>
<mi>

v

</mi>

<mo mathvariant="normal" lspace="0em" rspace="0em">

′

</mo>
</msup>
</mstyle>

<mo separator="true">

,

</mo>

<mfrac>
<mrow>
<mi>

d

</mi>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

u

</mi>
</mstyle>
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

<mo>

≜

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

A

</mi>
</mstyle>
</mrow>

<annotation encoding="application/x-tex">

\frac{d\pmb{\rho}}{dt}\triangleq \pmb{u},\frac{d\pmb{r}}{dt}\triangleq \pmb{v},\frac{d\pmb{r'}}{dt}\triangleq \pmb{v'},\frac{d\pmb{u}}{dt}\triangleq \pmb{A}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
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

<span className="mord,mathnormal">

t

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal">

ρ

</span>
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

<span className="mrel,amsrm">

≜

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:2.0574em;vertical-align:-0.686em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal">

u

</span>
</span>

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



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

t

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

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

<span className="mrel,amsrm">

≜

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:2.1149em;vertical-align:-0.686em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

v

</span>
</span>

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



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
<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal">

t

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

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

<span className="mrel,amsrm">

≜

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:2.0574em;vertical-align:-0.686em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

v

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8019em;">
<span style="top:-3.113em;margin-right:0.05em;">
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

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



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

t

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal">

u

</span>
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

<span className="mrel,amsrm">

≜

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal">

A

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

s

</mi>

<mi mathvariant="normal">

.

</mi>

<mi>

t

</mi>

<mi mathvariant="normal">

.

</mi>

<mtext>



</mtext>

<mtext>



</mtext>

<mtext>



</mtext>

<mtext>



</mtext>

<mtext>



</mtext>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<msup>
<mi>

v

</mi>

<mo mathvariant="normal" lspace="0em" rspace="0em">

′

</mo>
</msup>
</mstyle>

<mo>

=

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

v

</mi>
</mstyle>

<mo>

+

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

u

</mi>
</mstyle>
</mrow>

<annotation encoding="application/x-tex">

s.t.\,\,\,\,\,\pmb{v'}=\pmb{v}+\pmb{u}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8019em;">



</span>

<span className="mord,mathnormal">

s

</span>

<span className="mord">

.

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord">

.

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

v

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8019em;">
<span style="top:-3.113em;margin-right:0.05em;">
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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.6667em;vertical-align:-0.0833em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

v

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
<span className="strut" style="height:0.4306em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal">

u

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
<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<msup>
<mi>

a

</mi>

<mo mathvariant="normal" lspace="0em" rspace="0em">

′

</mo>
</msup>
</mstyle>

<mo>

=

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

a

</mi>
</mstyle>

<mo>

+

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

A

</mi>
</mstyle>
</mrow>

<annotation encoding="application/x-tex">

\pmb{a'}=\pmb{a}+\pmb{A}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8019em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord">
<span className="mord,mathnormal">

a

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8019em;">
<span style="top:-3.113em;margin-right:0.05em;">
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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.6667em;vertical-align:-0.0833em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal">

a

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal">

A

</span>
</span>
</span>
</span>
</span>
</span>

其中物理量含义不做过多解释；

###### 2.两个互作转动的参照系之间的变换

[![pFMRldg.md.jpg](https://s11.ax1x.com/2024/02/01/pFMRldg.md.jpg)](https://imgse.com/i/pFMRldg)

在参考系(**S**)内，如果<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

R

</mi>
</mstyle>
</mrow>

<annotation encoding="application/x-tex">

\pmb{R}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0077em;">

R

</span>
</span>
</span>
</span>
</span>

矢量绕某个轴以角速度<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

ω

</mi>
</mstyle>
</mrow>

<annotation encoding="application/x-tex">

\pmb{\omega}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.4306em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

ω

</span>
</span>
</span>
</span>
</span>

转动(注意**方向是沿轴向上不是逆时针**)，

则对<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

R

</mi>
</mstyle>
</mrow>

<annotation encoding="application/x-tex">

\pmb{R}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0077em;">

R

</span>
</span>
</span>
</span>
</span>

矢量求导满足（记以角速度<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

ω

</mi>
</mrow>

<annotation encoding="application/x-tex">

\omega

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.4306em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

ω

</span>
</span>
</span>
</span>

转动的参考系为**S'**）

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mo stretchy="false">

(

</mo>

<mfrac>
<mrow>
<mi>

d

</mi>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

R

</mi>
</mstyle>
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

<msub>
<mo stretchy="false">

)

</mo>

<mi>

S

</mi>
</msub>

<mo>

=

</mo>

<mo stretchy="false">

(

</mo>

<mfrac>
<mrow>
<mi>

d

</mi>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

R

</mi>
</mstyle>
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

<msub>
<mo stretchy="false">

)

</mo>

<msup>
<mi>

S

</mi>

<mo mathvariant="normal" lspace="0em" rspace="0em">

′

</mo>
</msup>
</msub>

<mo>

+

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

ω

</mi>
</mstyle>

<mo>

×

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

R

</mi>
</mstyle>
</mrow>

<annotation encoding="application/x-tex">

(\frac{d\pmb{R}}{dt})_S=(\frac{d\pmb{R}}{dt})_{S'}+\pmb{\omega}\times\pmb{R}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:2.0574em;vertical-align:-0.686em;">



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
<span className="vlist" style="height:1.3714em;">
<span style="top:-2.314em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal">

t

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0077em;">

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

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:2.0574em;vertical-align:-0.686em;">



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
<span className="vlist" style="height:1.3714em;">
<span style="top:-2.314em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal">

t

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0077em;">

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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

S

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.6828em;">
<span style="top:-2.786em;margin-right:0.0714em;">
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
<span className="strut" style="height:0.6667em;vertical-align:-0.0833em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

ω

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
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0077em;">

R

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

其中

</mtext>

<mo stretchy="false">

(

</mo>

<mfrac>
<mrow>
<mi>

d

</mi>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

R

</mi>
</mstyle>
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

<msub>
<mo stretchy="false">

)

</mo>

<msup>
<mi>

S

</mi>

<mo mathvariant="normal" lspace="0em" rspace="0em">

′

</mo>
</msup>
</msub>

<mtext>

实际为

</mtext>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

R

</mi>
</mstyle>

<mtext>

矢量在

</mtext>

<mi>

S

</mi>

<mtext>

’系中不旋转，只伸长

</mtext>

<mi>

o

</mi>

<mi>

r

</mi>

<mtext>

缩小

</mtext>
</mrow>

<annotation encoding="application/x-tex">

其中(\frac{d\pmb{R}}{dt})_{S'}实际为\pmb{R}矢量在S’系中不旋转，只伸长or缩小

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:2.0574em;vertical-align:-0.686em;">



</span>

<span className="mord,cjk_fallback">

其中

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
<span className="vlist" style="height:1.3714em;">
<span style="top:-2.314em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal">

t

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0077em;">

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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

S

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.6828em;">
<span style="top:-2.786em;margin-right:0.0714em;">
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
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>

<span className="mord,cjk_fallback">

实际为

</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0077em;">

R

</span>
</span>

<span className="mord,cjk_fallback">

矢量在

</span>

<span className="mord,mathnormal" style="margin-right:0.0576em;">

S

</span>

<span className="mord">

’

</span>

<span className="mord,cjk_fallback">

系中不旋转，只伸长

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

or

</span>

<span className="mord,cjk_fallback">

缩小

</span>
</span>
</span>
</span>
</span>

应用上述结论，则有速度变换

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mo stretchy="false">

(

</mo>

<mfrac>
<mrow>
<mi>

d

</mi>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

r

</mi>
</mstyle>
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

<msub>
<mo stretchy="false">

)

</mo>

<mi>

S

</mi>
</msub>

<mo>

=

</mo>

<mo stretchy="false">

(

</mo>

<mfrac>
<mrow>
<mi>

d

</mi>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

r

</mi>
</mstyle>
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

<msub>
<mo stretchy="false">

)

</mo>

<msup>
<mi>

S

</mi>

<mo mathvariant="normal" lspace="0em" rspace="0em">

′

</mo>
</msup>
</msub>

<mo>

+

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

ω

</mi>
</mstyle>

<mo>

×

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

r

</mi>
</mstyle>
</mrow>

<annotation encoding="application/x-tex">

(\frac{d\pmb{r}}{dt})_S=(\frac{d\pmb{r}}{dt})_{S'}+\pmb{\omega}\times\pmb{r}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:2.0574em;vertical-align:-0.686em;">



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
<span className="vlist" style="height:1.3714em;">
<span style="top:-2.314em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal">

t

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

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

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:2.0574em;vertical-align:-0.686em;">



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
<span className="vlist" style="height:1.3714em;">
<span style="top:-2.314em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal">

t

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

S

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.6828em;">
<span style="top:-2.786em;margin-right:0.0714em;">
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
<span className="strut" style="height:0.6667em;vertical-align:-0.0833em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

ω

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
<span className="strut" style="height:0.4306em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

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

即

</mtext>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<msup>
<mi>

v

</mi>

<mo mathvariant="normal" lspace="0em" rspace="0em">

′

</mo>
</msup>
</mstyle>

<mo>

=

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

v

</mi>
</mstyle>

<mo>

+

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

ω

</mi>
</mstyle>

<mo>

×

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

r

</mi>
</mstyle>
</mrow>

<annotation encoding="application/x-tex">

即\pmb{v'}=\pmb{v}+\pmb{\omega}\times\pmb{r}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8019em;">



</span>

<span className="mord,cjk_fallback">

即

</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

v

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8019em;">
<span style="top:-3.113em;margin-right:0.05em;">
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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.6667em;vertical-align:-0.0833em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

v

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
<span className="strut" style="height:0.6667em;vertical-align:-0.0833em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

ω

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
<span className="strut" style="height:0.4306em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>
</span>
</span>
</span>
</span>
</span>

再求导

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mo stretchy="false">

(

</mo>

<mfrac>
<mrow>
<mi>

d

</mi>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<msup>
<mi>

v

</mi>

<mo mathvariant="normal" lspace="0em" rspace="0em">

′

</mo>
</msup>
</mstyle>
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

<msub>
<mo stretchy="false">

)

</mo>

<mi>

S

</mi>
</msub>

<mo>

=

</mo>

<mo stretchy="false">

(

</mo>

<mfrac>
<mrow>
<mi>

d

</mi>

<mo stretchy="false">

(

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

v

</mi>
</mstyle>

<mo>

+

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

ω

</mi>
</mstyle>

<mo>

×

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

r

</mi>
</mstyle>

<mo stretchy="false">

)

</mo>
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

<msub>
<mo stretchy="false">

)

</mo>

<mi>

S

</mi>
</msub>

<mo>

=

</mo>

<mo stretchy="false">

(

</mo>

<mfrac>
<mrow>
<mi>

d

</mi>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

v

</mi>
</mstyle>
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

<msub>
<mo stretchy="false">

)

</mo>

<mi>

S

</mi>
</msub>

<mo>

+

</mo>

<mo stretchy="false">

(

</mo>

<mfrac>
<mrow>
<mi>

d

</mi>

<mo stretchy="false">

(

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

ω

</mi>
</mstyle>

<mo>

×

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

r

</mi>
</mstyle>

<mo stretchy="false">

)

</mo>
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

<msub>
<mo stretchy="false">

)

</mo>

<mi>

S

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

(\frac{d\pmb{v'}}{dt})_S=(\frac{d(\pmb{v}+\pmb{\omega}\times\pmb{r})}{dt})_S=(\frac{d\pmb{v}}{dt})_S+(\frac{d(\pmb{\omega}\times\pmb{r})}{dt})_S

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:2.1149em;vertical-align:-0.686em;">



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
<span className="vlist" style="height:1.4289em;">
<span style="top:-2.314em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal">

t

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

v

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

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:2.113em;vertical-align:-0.686em;">



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
<span className="vlist" style="height:1.427em;">
<span style="top:-2.314em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal">

t

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

<span className="mopen">

(

</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

v

</span>
</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

ω

</span>
</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

×

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

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

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:2.0574em;vertical-align:-0.686em;">



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
<span className="vlist" style="height:1.3714em;">
<span style="top:-2.314em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal">

t

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:2.113em;vertical-align:-0.686em;">



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
<span className="vlist" style="height:1.427em;">
<span style="top:-2.314em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal">

t

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

<span className="mopen">

(

</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

ω

</span>
</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

×

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

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

<mo stretchy="false">

(

</mo>

<mfrac>
<mrow>
<mi>

d

</mi>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

v

</mi>
</mstyle>
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

<msub>
<mo stretchy="false">

)

</mo>

<mi>

S

</mi>
</msub>

<mo>

+

</mo>

<mo stretchy="false">

(

</mo>

<mfrac>
<mrow>
<mi>

d

</mi>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

ω

</mi>
</mstyle>
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

<msub>
<mo stretchy="false">

)

</mo>

<mi>

S

</mi>
</msub>

<mo>

×

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

r

</mi>
</mstyle>

<mo>

+

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

ω

</mi>
</mstyle>

<mo>

×

</mo>

<mo stretchy="false">

(

</mo>

<mfrac>
<mrow>
<mi>

d

</mi>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

r

</mi>
</mstyle>
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

<msub>
<mo stretchy="false">

)

</mo>

<mi>

S

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

=(\frac{d\pmb{v}}{dt})_S+(\frac{d\pmb{\omega}}{dt})_S\times\pmb{r}+\pmb{\omega}\times(\frac{d\pmb{r}}{dt})_S

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
<span className="strut" style="height:2.0574em;vertical-align:-0.686em;">



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
<span className="vlist" style="height:1.3714em;">
<span style="top:-2.314em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal">

t

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:2.0574em;vertical-align:-0.686em;">



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
<span className="vlist" style="height:1.3714em;">
<span style="top:-2.314em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal">

t

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

ω

</span>
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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

×

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.6667em;vertical-align:-0.0833em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

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
<span className="strut" style="height:0.6667em;vertical-align:-0.0833em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

ω

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
<span className="strut" style="height:2.0574em;vertical-align:-0.686em;">



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
<span className="vlist" style="height:1.3714em;">
<span style="top:-2.314em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal">

t

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

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

<mo stretchy="false">

(

</mo>

<mfrac>
<mrow>
<mi>

d

</mi>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

v

</mi>
</mstyle>
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

<msub>
<mo stretchy="false">

)

</mo>

<mi>

S

</mi>
</msub>

<mo>

+

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

β

</mi>
</mstyle>

<mo>

×

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

r

</mi>
</mstyle>

<mo>

+

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

ω

</mi>
</mstyle>

<mo>

×

</mo>

<mo stretchy="false">

(

</mo>

<mfrac>
<mrow>
<mi>

d

</mi>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

r

</mi>
</mstyle>
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

<msub>
<mo stretchy="false">

)

</mo>

<mi>

S

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

=(\frac{d\pmb{v}}{dt})_S+\pmb{\beta}\times\pmb{r}+\pmb{\omega}\times(\frac{d\pmb{r}}{dt})_S

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
<span className="strut" style="height:2.0574em;vertical-align:-0.686em;">



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
<span className="vlist" style="height:1.3714em;">
<span style="top:-2.314em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal">

t

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0528em;">

β

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
<span className="strut" style="height:0.6667em;vertical-align:-0.0833em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

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
<span className="strut" style="height:0.6667em;vertical-align:-0.0833em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

ω

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
<span className="strut" style="height:2.0574em;vertical-align:-0.686em;">



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
<span className="vlist" style="height:1.3714em;">
<span style="top:-2.314em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal">

t

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

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
</span>

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mtext>

而我们又知道

</mtext>

<mo stretchy="false">

(

</mo>

<mfrac>
<mrow>
<mi>

d

</mi>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

r

</mi>
</mstyle>
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

<msub>
<mo stretchy="false">

)

</mo>

<mi>

S

</mi>
</msub>

<mo>

=

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<msup>
<mi>

v

</mi>

<mo mathvariant="normal" lspace="0em" rspace="0em">

′

</mo>
</msup>
</mstyle>

<mo>

=

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

v

</mi>
</mstyle>

<mo>

+

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

ω

</mi>
</mstyle>

<mo>

×

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

r

</mi>
</mstyle>

<mtext>



</mtext>

<mtext>



</mtext>

<mtext>



</mtext>

<mtext>



</mtext>

<mi>

a

</mi>

<mi>

n

</mi>

<mi>

d

</mi>

<mtext>



</mtext>

<mtext>



</mtext>

<mtext>



</mtext>

<mtext>



</mtext>

<mo stretchy="false">

(

</mo>

<mfrac>
<mrow>
<mi>

d

</mi>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

v

</mi>
</mstyle>
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

<msub>
<mo stretchy="false">

)

</mo>

<mi>

S

</mi>
</msub>

<mo>

=

</mo>

<mo stretchy="false">

(

</mo>

<mfrac>
<mrow>
<mi>

d

</mi>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

r

</mi>
</mstyle>
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

<msub>
<mo stretchy="false">

)

</mo>

<msup>
<mi>

S

</mi>

<mo mathvariant="normal" lspace="0em" rspace="0em">

′

</mo>
</msup>
</msub>

<mo>

+

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

ω

</mi>
</mstyle>

<mo>

×

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

v

</mi>
</mstyle>
</mrow>

<annotation encoding="application/x-tex">

而我们又知道(\frac{d\pmb{r}}{dt})_S=\pmb{v'}=\pmb{v}+\pmb{\omega}\times\pmb{r}\,\,\,\,and\,\,\,\,(\frac{d\pmb{v}}{dt})_S=(\frac{d\pmb{r}}{dt})_{S'}+\pmb{\omega}\times\pmb{v}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:2.0574em;vertical-align:-0.686em;">



</span>

<span className="mord,cjk_fallback">

而我们又知道

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
<span className="vlist" style="height:1.3714em;">
<span style="top:-2.314em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal">

t

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

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

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8019em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

v

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8019em;">
<span style="top:-3.113em;margin-right:0.05em;">
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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.6667em;vertical-align:-0.0833em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

v

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
<span className="strut" style="height:0.6667em;vertical-align:-0.0833em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

ω

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
<span className="strut" style="height:2.0574em;vertical-align:-0.686em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>
</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord,mathnormal">

an

</span>

<span className="mord,mathnormal">

d

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mspace" style="margin-right:0.1667em;">



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
<span className="vlist" style="height:1.3714em;">
<span style="top:-2.314em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal">

t

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

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

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:2.0574em;vertical-align:-0.686em;">



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
<span className="vlist" style="height:1.3714em;">
<span style="top:-2.314em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal">

t

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

S

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.6828em;">
<span style="top:-2.786em;margin-right:0.0714em;">
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
<span className="strut" style="height:0.6667em;vertical-align:-0.0833em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

ω

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
<span className="strut" style="height:0.4306em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

v

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

s

</mi>

<mi mathvariant="normal">

.

</mi>

<mi>

t

</mi>

<mi mathvariant="normal">

.

</mi>

<mo stretchy="false">

(

</mo>

<mfrac>
<mrow>
<mi>

d

</mi>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<msup>
<mi>

v

</mi>

<mo mathvariant="normal" lspace="0em" rspace="0em">

′

</mo>
</msup>
</mstyle>
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

<msub>
<mo stretchy="false">

)

</mo>

<mi>

S

</mi>
</msub>

<mo>

=

</mo>

<mo>

=

</mo>

<mo stretchy="false">

(

</mo>

<mfrac>
<mrow>
<mi>

d

</mi>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

v

</mi>
</mstyle>
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

<msub>
<mo stretchy="false">

)

</mo>

<mi>

S

</mi>
</msub>

<mo>

+

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

β

</mi>
</mstyle>

<mo>

×

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

r

</mi>
</mstyle>

<mo>

+

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

ω

</mi>
</mstyle>

<mo>

×

</mo>

<mo stretchy="false">

(

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

v

</mi>
</mstyle>

<mo>

+

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

ω

</mi>
</mstyle>

<mo>

×

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

r

</mi>
</mstyle>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

s.t. (\frac{d\pmb{v'}}{dt})_S==(\frac{d\pmb{v}}{dt})_S+\pmb{\beta}\times\pmb{r}+\pmb{\omega}\times(\pmb{v}+\pmb{\omega}\times\pmb{r})

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:2.1149em;vertical-align:-0.686em;">



</span>

<span className="mord,mathnormal">

s

</span>

<span className="mord">

.

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord">

.

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
<span className="vlist" style="height:1.4289em;">
<span style="top:-2.314em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal">

t

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

v

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

==

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:2.0574em;vertical-align:-0.686em;">



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
<span className="vlist" style="height:1.3714em;">
<span style="top:-2.314em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal">

t

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0528em;">

β

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
<span className="strut" style="height:0.6667em;vertical-align:-0.0833em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

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
<span className="strut" style="height:0.6667em;vertical-align:-0.0833em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

ω

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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mopen">

(

</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

v

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
<span className="strut" style="height:0.6667em;vertical-align:-0.0833em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

ω

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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

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
<mo>

=

</mo>

<mo stretchy="false">

(

</mo>

<mfrac>
<mrow>
<mi>

d

</mi>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

r

</mi>
</mstyle>
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

<msub>
<mo stretchy="false">

)

</mo>

<msup>
<mi>

S

</mi>

<mo mathvariant="normal" lspace="0em" rspace="0em">

′

</mo>
</msup>
</msub>

<mo>

+

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

ω

</mi>
</mstyle>

<mo>

×

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

v

</mi>
</mstyle>

<mo>

+

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

β

</mi>
</mstyle>

<mo>

×

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

r

</mi>
</mstyle>

<mo>

+

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

ω

</mi>
</mstyle>

<mo>

×

</mo>

<mo stretchy="false">

(

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

v

</mi>
</mstyle>

<mo>

+

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

ω

</mi>
</mstyle>

<mo>

×

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

r

</mi>
</mstyle>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

=(\frac{d\pmb{r}}{dt})_{S'}+\pmb{\omega}\times\pmb{v}+\pmb{\beta}\times\pmb{r}+\pmb{\omega}\times(\pmb{v}+\pmb{\omega}\times\pmb{r})

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
<span className="strut" style="height:2.0574em;vertical-align:-0.686em;">



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
<span className="vlist" style="height:1.3714em;">
<span style="top:-2.314em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal">

t

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

S

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.6828em;">
<span style="top:-2.786em;margin-right:0.0714em;">
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
<span className="strut" style="height:0.6667em;vertical-align:-0.0833em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

ω

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
<span className="strut" style="height:0.6667em;vertical-align:-0.0833em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

v

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0528em;">

β

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
<span className="strut" style="height:0.6667em;vertical-align:-0.0833em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

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
<span className="strut" style="height:0.6667em;vertical-align:-0.0833em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

ω

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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mopen">

(

</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

v

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
<span className="strut" style="height:0.6667em;vertical-align:-0.0833em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

ω

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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

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
<mo>

=

</mo>

<mo stretchy="false">

(

</mo>

<mfrac>
<mrow>
<mi>

d

</mi>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

r

</mi>
</mstyle>
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

<msub>
<mo stretchy="false">

)

</mo>

<msup>
<mi>

S

</mi>

<mo mathvariant="normal" lspace="0em" rspace="0em">

′

</mo>
</msup>
</msub>

<mo>

+

</mo>

<mn>

2

</mn>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

ω

</mi>
</mstyle>

<mo>

×

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

v

</mi>
</mstyle>

<mo>

+

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

β

</mi>
</mstyle>

<mo>

×

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

r

</mi>
</mstyle>

<mo>

+

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

ω

</mi>
</mstyle>

<mo>

×

</mo>

<mo stretchy="false">

(

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

ω

</mi>
</mstyle>

<mo>

×

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

r

</mi>
</mstyle>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

=(\frac{d\pmb{r}}{dt})_{S'}+2\pmb{\omega}\times\pmb{v}+\pmb{\beta}\times\pmb{r}+\pmb{\omega}\times(\pmb{\omega}\times\pmb{r})

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
<span className="strut" style="height:2.0574em;vertical-align:-0.686em;">



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
<span className="vlist" style="height:1.3714em;">
<span style="top:-2.314em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal">

t

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

S

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.6828em;">
<span style="top:-2.786em;margin-right:0.0714em;">
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
<span className="strut" style="height:0.7278em;vertical-align:-0.0833em;">



</span>

<span className="mord">

2

</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

ω

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
<span className="strut" style="height:0.6667em;vertical-align:-0.0833em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

v

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0528em;">

β

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
<span className="strut" style="height:0.6667em;vertical-align:-0.0833em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

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
<span className="strut" style="height:0.6667em;vertical-align:-0.0833em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

ω

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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mopen">

(

</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

ω

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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

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
<mo stretchy="false">

(

</mo>

<mfrac>
<mrow>
<mi>

d

</mi>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<msup>
<mi>

v

</mi>

<mo mathvariant="normal" lspace="0em" rspace="0em">

′

</mo>
</msup>
</mstyle>
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

<msub>
<mo stretchy="false">

)

</mo>

<mi>

S

</mi>
</msub>

<mo>

≜

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<msup>
<mi>

a

</mi>

<mo mathvariant="normal" lspace="0em" rspace="0em">

′

</mo>
</msup>
</mstyle>

<mtext>



</mtext>

<mtext>



</mtext>

<mtext>



</mtext>

<mtext>



</mtext>

<mo stretchy="false">

(

</mo>

<mfrac>
<mrow>
<mi>

d

</mi>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

v

</mi>
</mstyle>
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

<msub>
<mo stretchy="false">

)

</mo>

<msup>
<mi>

S

</mi>

<mo mathvariant="normal" lspace="0em" rspace="0em">

′

</mo>
</msup>
</msub>

<mo>

≜

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<msup>
<mi>

a

</mi>

<mo mathvariant="normal" lspace="0em" rspace="0em">

′

</mo>
</msup>
</mstyle>
</mrow>

<annotation encoding="application/x-tex">

(\frac{d\pmb{v'}}{dt})_S\triangleq \pmb{a'}\,\,\,\,(\frac{d\pmb{v}}{dt})_{S'}\triangleq \pmb{a'}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:2.1149em;vertical-align:-0.686em;">



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
<span className="vlist" style="height:1.4289em;">
<span style="top:-2.314em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal">

t

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

v

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

<span className="mrel,amsrm">

≜

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:2.0574em;vertical-align:-0.686em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord">
<span className="mord,mathnormal">

a

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8019em;">
<span style="top:-3.113em;margin-right:0.05em;">
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

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mspace" style="margin-right:0.1667em;">



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
<span className="vlist" style="height:1.3714em;">
<span style="top:-2.314em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal">

t

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

S

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.6828em;">
<span style="top:-2.786em;margin-right:0.0714em;">
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

<span className="mrel,amsrm">

≜

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8019em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord">
<span className="mord,mathnormal">

a

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8019em;">
<span style="top:-3.113em;margin-right:0.05em;">
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
</span>
</span>

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

s

</mi>

<mi mathvariant="normal">

.

</mi>

<mi>

t

</mi>

<mi mathvariant="normal">

.

</mi>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<msup>
<mi>

a

</mi>

<mo mathvariant="normal" lspace="0em" rspace="0em">

′

</mo>
</msup>
</mstyle>

<mo>

=

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

a

</mi>
</mstyle>

<mo>

+

</mo>

<mn>

2

</mn>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

ω

</mi>
</mstyle>

<mo>

×

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

v

</mi>
</mstyle>

<mo>

+

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

β

</mi>
</mstyle>

<mo>

×

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

r

</mi>
</mstyle>

<mo>

+

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

ω

</mi>
</mstyle>

<mo>

×

</mo>

<mo stretchy="false">

(

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

ω

</mi>
</mstyle>

<mo>

×

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

r

</mi>
</mstyle>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

s.t.\pmb{a'}=\pmb{a}+2\pmb{\omega}\times\pmb{v}+\pmb{\beta}\times\pmb{r}+\pmb{\omega}\times(\pmb{\omega}\times\pmb{r})

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8019em;">



</span>

<span className="mord,mathnormal">

s

</span>

<span className="mord">

.

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord">

.

</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord">
<span className="mord,mathnormal">

a

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8019em;">
<span style="top:-3.113em;margin-right:0.05em;">
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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.6667em;vertical-align:-0.0833em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal">

a

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
<span className="strut" style="height:0.7278em;vertical-align:-0.0833em;">



</span>

<span className="mord">

2

</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

ω

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
<span className="strut" style="height:0.6667em;vertical-align:-0.0833em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

v

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0528em;">

β

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
<span className="strut" style="height:0.6667em;vertical-align:-0.0833em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

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
<span className="strut" style="height:0.6667em;vertical-align:-0.0833em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

ω

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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mopen">

(

</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

ω

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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>
</span>

<span className="mclose">

)

</span>
</span>
</span>
</span>
</span>

此即两个互作转动的参照系之间的加速度变换（累死了(´〜｀*) ）

前情提要：

上面对于运动的描述都是对于单个物体（质点）而言，对于质点系而言，当然可以对每个质点单独进行描述，但是对于质点之间，存在着一定的约束，下面我们讨论有约束关系我们能获得什么：

#### （三）约束

理想约束/非理想约束，这个等到后面分析力学再详细展开（或者再这里再补充）

这里仅举常用的一些例子，但是会从更数学的角度去处理约束关系，和从物理的角度对比一下，更好的理解运动关联的那些事

eg1:杆模型

[![pF1nFKO.md.jpg](https://s11.ax1x.com/2024/02/06/pF1nFKO.md.jpg)](https://imgse.com/i/pF1nFKO)

杆模型这里只关注两个端点的约束关系，杆长为<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

l

</mi>
</mrow>

<annotation encoding="application/x-tex">

l

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>
</span>
</span>
</span>

,选取一个原点为<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

O

</mi>
</mrow>

<annotation encoding="application/x-tex">

O

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

O

</span>
</span>
</span>
</span>

,则此时描述两个质点的运动由<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<msub>
<mi>

r

</mi>

<mn>

1

</mn>
</msub>

<mtext>



</mtext>

<msub>
<mi>

r

</mi>

<mn>

2

</mn>
</msub>
</mstyle>
</mrow>

<annotation encoding="application/x-tex">

\pmb{r_1\,r_2}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.5806em;vertical-align:-0.15em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

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

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

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
</span>

来决定

那这两个质点（两个端点）有什么约束关系——很简单，<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi mathvariant="normal">

∣

</mi>

<mrow>
<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<msub>
<mi>

r

</mi>

<mn>

1

</mn>
</msub>
</mstyle>

<mo>

−

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<msub>
<mi>

r

</mi>

<mn>

2

</mn>
</msub>
</mstyle>
</mrow>

<mi mathvariant="normal">

∣

</mi>

<mo>

=

</mo>

<mi>

l

</mi>
</mrow>

<annotation encoding="application/x-tex">

|{\pmb{r_1}-\pmb{r_2}}| = l

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
<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

−

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

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

<span className="mord">

∣

</span>

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

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>
</span>
</span>
</span>



但是操作起来不是那么方便，于是上式改写为<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mo stretchy="false">

(

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<msub>
<mi>

r

</mi>

<mn>

1

</mn>
</msub>
</mstyle>

<mo>

−

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<msub>
<mi>

r

</mi>

<mn>

2

</mn>
</msub>
</mstyle>

<msup>
<mo stretchy="false">

)

</mo>

<mn>

2

</mn>
</msup>

<mo>

=

</mo>

<msup>
<mi>

l

</mi>

<mn>

2

</mn>
</msup>
</mrow>

<annotation encoding="application/x-tex">

(\pmb{r_1}-\pmb{r_2})^2=l^2

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8141em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

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



这样写有什么好处——可以求导了！式子两边对时间求导

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mfrac>
<mrow>
<mi>

d

</mi>

<mo stretchy="false">

(

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<msub>
<mi>

r

</mi>

<mn>

1

</mn>
</msub>
</mstyle>

<mo>

−

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<msub>
<mi>

r

</mi>

<mn>

2

</mn>
</msub>
</mstyle>

<msup>
<mo stretchy="false">

)

</mo>

<mn>

2

</mn>
</msup>
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

<mo>

=

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

t

</mi>
</mrow>
</mfrac>

<mo stretchy="false">

{

</mo>

<mo stretchy="false">

(

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<msub>
<mi>

r

</mi>

<mn>

1

</mn>
</msub>
</mstyle>

<mo>

−

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<msub>
<mi>

r

</mi>

<mn>

2

</mn>
</msub>
</mstyle>

<mo stretchy="false">

)

</mo>

<mo>

⋅

</mo>

<mo stretchy="false">

(

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<msub>
<mi>

r

</mi>

<mn>

1

</mn>
</msub>
</mstyle>

<mo>

−

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<msub>
<mi>

r

</mi>

<mn>

2

</mn>
</msub>
</mstyle>

<mo stretchy="false">

)

</mo>

<mo stretchy="false">

}

</mo>
</mrow>

<annotation encoding="application/x-tex">

\frac{d(\pmb{r_1}-\pmb{r_2})^2}{dt}=\frac{d}{dt}\lbrace (\pmb{r_1}-\pmb{r_2})\cdot(\pmb{r_1}-\pmb{r_2})\rbrace

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

<span className="mord,mathnormal">

t

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

<span className="mopen">

(

</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

−

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

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

<span className="mord,mathnormal">

t

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

<span className="mopen">

{(

</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mopen">

(

</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

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

<span className="mclose">

)}

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

<mo stretchy="false">

(

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<msub>
<mi>

r

</mi>

<mn>

1

</mn>
</msub>
</mstyle>

<mo>

−

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<msub>
<mi>

r

</mi>

<mn>

2

</mn>
</msub>
</mstyle>

<mo stretchy="false">

)

</mo>

<mo>

⋅

</mo>

<mo stretchy="false">

(

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<msub>
<mi>

v

</mi>

<mn>

1

</mn>
</msub>
</mstyle>

<mo>

−

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<msub>
<mi>

v

</mi>

<mn>

2

</mn>
</msub>
</mstyle>

<mo stretchy="false">

)

</mo>

<mo>

+

</mo>

<mo stretchy="false">

(

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<msub>
<mi>

v

</mi>

<mn>

1

</mn>
</msub>
</mstyle>

<mo>

−

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<msub>
<mi>

v

</mi>

<mn>

2

</mn>
</msub>
</mstyle>

<mo stretchy="false">

)

</mo>

<mo>

⋅

</mo>

<mo stretchy="false">

(

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<msub>
<mi>

r

</mi>

<mn>

1

</mn>
</msub>
</mstyle>

<mo>

−

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<msub>
<mi>

r

</mi>

<mn>

2

</mn>
</msub>
</mstyle>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

=(\pmb{r_1}-\pmb{r_2})\cdot(\pmb{v_1}-\pmb{v_2})+(\pmb{v_1}-\pmb{v_2})\cdot(\pmb{r_1}-\pmb{r_2})

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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mopen">

(

</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mopen">

(

</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

v

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

v

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

v

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

v

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mopen">

(

</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

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
<mo>

=

</mo>

<mn>

2

</mn>

<mo stretchy="false">

(

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<msub>
<mi>

r

</mi>

<mn>

1

</mn>
</msub>
</mstyle>

<mo>

−

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<msub>
<mi>

r

</mi>

<mn>

2

</mn>
</msub>
</mstyle>

<mo stretchy="false">

)

</mo>

<mo>

⋅

</mo>

<mo stretchy="false">

(

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<msub>
<mi>

v

</mi>

<mn>

1

</mn>
</msub>
</mstyle>

<mo>

−

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<msub>
<mi>

v

</mi>

<mn>

2

</mn>
</msub>
</mstyle>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

=2(\pmb{r_1}-\pmb{r_2})\cdot(\pmb{v_1}-\pmb{v_2})

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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord">

2

</span>

<span className="mopen">

(

</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mopen">

(

</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

v

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

v

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
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
<mo>

=

</mo>

<mfrac>
<mrow>
<mi>

d

</mi>

<mo stretchy="false">

(

</mo>

<msup>
<mi>

l

</mi>

<mn>

2

</mn>
</msup>

<mo stretchy="false">

)

</mo>
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

<mo>

=

</mo>

<mn>

0

</mn>
</mrow>

<annotation encoding="application/x-tex">

=\frac{d(l^2)}{dt}=0

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

<span className="mord,mathnormal">

t

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

<span className="mopen">

(

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

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
<span className="strut" style="height:0.6444em;">



</span>

<span className="mord">

0

</span>
</span>
</span>
</span>
</span>

由此我们获得了一个信息——<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mo stretchy="false">

(

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<msub>
<mi>

r

</mi>

<mn>

1

</mn>
</msub>
</mstyle>

<mo>

−

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<msub>
<mi>

r

</mi>

<mn>

2

</mn>
</msub>
</mstyle>

<mo stretchy="false">

)

</mo>

<mo>

⋅

</mo>

<mo stretchy="false">

(

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<msub>
<mi>

v

</mi>

<mn>

1

</mn>
</msub>
</mstyle>

<mo>

−

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<msub>
<mi>

v

</mi>

<mn>

2

</mn>
</msub>
</mstyle>

<mo stretchy="false">

)

</mo>

<mo>

=

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mn>

0

</mn>
</mstyle>
</mrow>

<annotation encoding="application/x-tex">

(\pmb{r_1}-\pmb{r_2})\cdot(\pmb{v_1}-\pmb{v_2})=\pmb{0}

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mopen">

(

</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

v

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

v

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord">

0

</span>
</span>
</span>
</span>
</span>



这句话代表了什么<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mo>

⟶

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<msub>
<mi>

r

</mi>

<mn>

1

</mn>
</msub>
</mstyle>

<mo>

−

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<msub>
<mi>

r

</mi>

<mn>

2

</mn>
</msub>
</mstyle>

<mtext>

记为

</mtext>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

l

</mi>
</mstyle>
</mrow>

<annotation encoding="application/x-tex">

\longrightarrow\pmb{r_1}-\pmb{r_2}记为\pmb{l}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.522em;vertical-align:-0.011em;">



</span>

<span className="mrel">

⟶

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.7333em;vertical-align:-0.15em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

−

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8444em;vertical-align:-0.15em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

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

<span className="mord,cjk_fallback">

记为

</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>
</span>
</span>
</span>
</span>

​

上式化为<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

l

</mi>
</mstyle>

<mo>

⋅

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<msub>
<mi>

v

</mi>

<mn>

1

</mn>
</msub>
</mstyle>

<mo>

=

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

l

</mi>
</mstyle>

<mo>

⋅

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<msub>
<mi>

v

</mi>

<mn>

2

</mn>
</msub>
</mstyle>
</mrow>

<annotation encoding="application/x-tex">

\pmb{l}\cdot\pmb{v_1}=\pmb{l}\cdot\pmb{v_2}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

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
<span className="strut" style="height:0.5806em;vertical-align:-0.15em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

v

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

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
<span className="strut" style="height:0.5806em;vertical-align:-0.15em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

v

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
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
</span>



[![pF1n1sS.md.jpg](https://s11.ax1x.com/2024/02/06/pF1n1sS.md.jpg)](https://imgse.com/i/pF1n1sS)

再图里面看是不是就很明显，<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

l

</mi>
</mstyle>

<mo>

⋅

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<msub>
<mi>

v

</mi>

<mn>

1

</mn>
</msub>
</mstyle>

<mo>

=

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

l

</mi>
</mstyle>

<mo>

⋅

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<msub>
<mi>

v

</mi>

<mn>

2

</mn>
</msub>
</mstyle>
</mrow>

<annotation encoding="application/x-tex">

\pmb{l}\cdot\pmb{v_1}=\pmb{l}\cdot\pmb{v_2}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

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
<span className="strut" style="height:0.5806em;vertical-align:-0.15em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

v

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

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
<span className="strut" style="height:0.5806em;vertical-align:-0.15em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

v

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
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
</span>

意思就是沿杆的方向速度相等（图片中两个速度显然不符合实际情况）

————显然是废话{bushi}

从这里面其实我们就能更加深刻的理解，平时我们所说的沿杆的方向速度相等的更深层次的原理，而不是一些物理直觉（当然直觉也是有理有据的）

我们再看<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<msub>
<mi>

r

</mi>

<mn>

1

</mn>
</msub>
</mstyle>

<mo>

−

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<msub>
<mi>

r

</mi>

<mn>

2

</mn>
</msub>
</mstyle>

<mo>

=

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

l

</mi>
</mstyle>
</mrow>

<annotation encoding="application/x-tex">

\pmb{r_1}-\pmb{r_2}=\pmb{l}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.7333em;vertical-align:-0.15em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

−

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.5806em;vertical-align:-0.15em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>
</span>
</span>
</span>
</span>

这个式子，在平面中，<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

l

</mi>
</mstyle>
</mrow>

<annotation encoding="application/x-tex">

\pmb{l}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>
</span>
</span>
</span>
</span>

往往是以平动加转动的方式在“运动”，那么我们尝试对<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

l

</mi>
</mstyle>
</mrow>

<annotation encoding="application/x-tex">

\pmb{l}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>
</span>
</span>
</span>
</span>

进行求导，

显然，这和上面旋转坐标系那里提及的求导方式是一致的，

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mfrac>
<mrow>
<mi>

d

</mi>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

l

</mi>
</mstyle>
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

<mo>

=

</mo>

<mtext>

对长度的求导

</mtext>

<mo>

+

</mo>

<mtext>

对方向的求导

</mtext>
</mrow>

<annotation encoding="application/x-tex">

\frac{d\pmb{l}}{dt}=对长度的求导+对方向的求导

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
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

<span className="mord,mathnormal">

t

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>
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
<span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">



</span>

<span className="mord,cjk_fallback">

对长度的求导

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

对方向的求导

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

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mn>

0

</mn>
</mstyle>

<mo>

+

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

ω

</mi>
</mstyle>

<mo>

×

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

l

</mi>
</mstyle>
</mrow>

<annotation encoding="application/x-tex">

=\pmb{0}+\pmb{\omega}\times\pmb{l}

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
<span className="strut" style="height:0.7278em;vertical-align:-0.0833em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord">

0

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
<span className="strut" style="height:0.6667em;vertical-align:-0.0833em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

ω

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

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

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

ω

</mi>
</mstyle>

<mo>

×

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

l

</mi>
</mstyle>
</mrow>

<annotation encoding="application/x-tex">

=\pmb{\omega}\times\pmb{l}

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
<span className="strut" style="height:0.6667em;vertical-align:-0.0833em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

ω

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

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

也就是说对

</mtext>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<msub>
<mi>

r

</mi>

<mn>

1

</mn>
</msub>
</mstyle>

<mo>

−

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<msub>
<mi>

r

</mi>

<mn>

2

</mn>
</msub>
</mstyle>

<mo>

=

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

l

</mi>
</mstyle>

<mtext>

两边求导，会得到——

</mtext>
</mrow>

<annotation encoding="application/x-tex">

也就是说对\pmb{r_1}-\pmb{r_2}=\pmb{l}两边求导，会得到——

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord,cjk_fallback">

也就是说对

</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

−

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.5806em;vertical-align:-0.15em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>
</span>

<span className="mord,cjk_fallback">

两边求导，会得到

</span>

<span className="mord">

——

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
<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<msub>
<mi>

v

</mi>

<mn>

1

</mn>
</msub>
</mstyle>

<mo>

−

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<msub>
<mi>

v

</mi>

<mn>

2

</mn>
</msub>
</mstyle>

<mo>

=

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

ω

</mi>
</mstyle>

<mo>

×

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

l

</mi>
</mstyle>
</mrow>

<annotation encoding="application/x-tex">

\pmb{v_1}-\pmb{v_2}=\pmb{\omega}\times\pmb{l}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.7333em;vertical-align:-0.15em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

v

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

−

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.5806em;vertical-align:-0.15em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

v

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.6667em;vertical-align:-0.0833em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

ω

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>
</span>
</span>
</span>
</span>
</span>

这个式子我们再看，它有用了起来

<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<msub>
<mi>

v

</mi>

<mn>

1

</mn>
</msub>
</mstyle>

<mo>

−

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<msub>
<mi>

v

</mi>

<mn>

2

</mn>
</msub>
</mstyle>

<mo>

=

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

ω

</mi>
</mstyle>

<mo>

×

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

l

</mi>
</mstyle>
</mrow>

<annotation encoding="application/x-tex">

\pmb{v_1}-\pmb{v_2}=\pmb{\omega}\times\pmb{l}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.7333em;vertical-align:-0.15em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

v

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

−

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.5806em;vertical-align:-0.15em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

v

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.6667em;vertical-align:-0.0833em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

ω

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>
</span>
</span>
</span>
</span>

  其实就是以一个端点为参考系，另一个端点必然是绕原来的端点（在系中静止的）圆周运动

再求导可以得到

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<msub>
<mi>

a

</mi>

<mn>

1

</mn>
</msub>
</mstyle>

<mo>

−

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<msub>
<mi>

a

</mi>

<mn>

2

</mn>
</msub>
</mstyle>

<mo>

=

</mo>

<mfrac>
<mrow>
<mi>

d

</mi>

<mo stretchy="false">

(

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

ω

</mi>
</mstyle>

<mo>

×

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

l

</mi>
</mstyle>

<mo stretchy="false">

)

</mo>
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

<mspace linebreak="newline">



</mspace>

<mo>

=

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

β

</mi>
</mstyle>

<mo>

×

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

l

</mi>
</mstyle>

<mo>

+

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

ω

</mi>
</mstyle>

<mo>

×

</mo>

<mfrac>
<mrow>
<mi>

d

</mi>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

l

</mi>
</mstyle>
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

<mspace linebreak="newline">



</mspace>

<mo>

=

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

β

</mi>
</mstyle>

<mo>

×

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

l

</mi>
</mstyle>

<mo>

+

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

ω

</mi>
</mstyle>

<mo>

×

</mo>

<mo stretchy="false">

(

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

ω

</mi>
</mstyle>

<mo>

×

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

l

</mi>
</mstyle>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

\pmb{a_1}-\pmb{a_2}=\frac{d(\pmb{\omega}\times\pmb{l})}{dt}\\
=\pmb{\beta}\times\pmb{l}+\pmb{\omega}\times\frac{d\pmb{l}}{dt}\\
=\pmb{\beta}\times\pmb{l}+\pmb{\omega}\times(\pmb{\omega}\times\pmb{l})

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.7333em;vertical-align:-0.15em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
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
<span className="strut" style="height:0.5806em;vertical-align:-0.15em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
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
</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

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
<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal">

t

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

<span className="mopen">

(

</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

ω

</span>
</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

×

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

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

<span className="mspace,newline">



</span>

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
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0528em;">

β

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
<span className="strut" style="height:0.7778em;vertical-align:-0.0833em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

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
<span className="strut" style="height:0.6667em;vertical-align:-0.0833em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

ω

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

<span className="mord,mathnormal">

t

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>
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

<span className="mspace,newline">



</span>

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
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0528em;">

β

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
<span className="strut" style="height:0.7778em;vertical-align:-0.0833em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

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
<span className="strut" style="height:0.6667em;vertical-align:-0.0833em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

ω

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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mopen">

(

</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

ω

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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>
</span>

<span className="mclose">

)

</span>
</span>
</span>
</span>
</span>

即，由一个简单的杆约束方程，我们得到了如下信息

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

l

</mi>
</mstyle>

<mo>

⋅

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<msub>
<mi>

v

</mi>

<mn>

1

</mn>
</msub>
</mstyle>

<mo>

=

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

l

</mi>
</mstyle>

<mo>

⋅

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<msub>
<mi>

v

</mi>

<mn>

2

</mn>
</msub>
</mstyle>
</mrow>

<annotation encoding="application/x-tex">

\pmb{l}\cdot\pmb{v_1}=\pmb{l}\cdot\pmb{v_2}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

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
<span className="strut" style="height:0.5806em;vertical-align:-0.15em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

v

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

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
<span className="strut" style="height:0.5806em;vertical-align:-0.15em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

v

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
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
</span>
</span>

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<msub>
<mi>

v

</mi>

<mn>

1

</mn>
</msub>
</mstyle>

<mo>

−

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<msub>
<mi>

v

</mi>

<mn>

2

</mn>
</msub>
</mstyle>

<mo>

=

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

ω

</mi>
</mstyle>

<mo>

×

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

l

</mi>
</mstyle>
</mrow>

<annotation encoding="application/x-tex">

\pmb{v_1}-\pmb{v_2}=\pmb{\omega}\times\pmb{l}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.7333em;vertical-align:-0.15em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

v

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

−

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.5806em;vertical-align:-0.15em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

v

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.6667em;vertical-align:-0.0833em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

ω

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

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
<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<msub>
<mi>

a

</mi>

<mn>

1

</mn>
</msub>
</mstyle>

<mo>

−

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<msub>
<mi>

a

</mi>

<mn>

2

</mn>
</msub>
</mstyle>

<mo>

=

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

β

</mi>
</mstyle>

<mo>

×

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

l

</mi>
</mstyle>

<mo>

+

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

ω

</mi>
</mstyle>

<mo>

×

</mo>

<mo stretchy="false">

(

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

ω

</mi>
</mstyle>

<mo>

×

</mo>

<mstyle style="text-shadow: 0.02em 0.01em 0.04px">
<mi>

l

</mi>
</mstyle>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

\pmb{a_1}-\pmb{a_2}=
\pmb{\beta}\times\pmb{l}+\pmb{\omega}\times(\pmb{\omega}\times\pmb{l})

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.7333em;vertical-align:-0.15em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
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
<span className="strut" style="height:0.5806em;vertical-align:-0.15em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
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
</span>

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

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0528em;">

β

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
<span className="strut" style="height:0.7778em;vertical-align:-0.0833em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

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
<span className="strut" style="height:0.6667em;vertical-align:-0.0833em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

ω

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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mopen">

(

</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

ω

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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord" style="text-shadow:0.02em 0.01em 0.04px;">
<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>
</span>

<span className="mclose">

)

</span>
</span>
</span>
</span>
</span>

eg2:软绳模型——既然前面的情形很常见，那么接下来讨论一个稍微不常见的软绳模型
