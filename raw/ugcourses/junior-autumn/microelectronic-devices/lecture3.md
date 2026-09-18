# Lecture 3：费米能级、载流子散射与迁移率

> 费米能级随掺杂与温度的变化、本征费米能级、简并掺杂与带隙变窄、n 与 p 的一般理论、极端温度下的载流子浓度、有效质量、热运动、三种散射机制、漂移与迁移率、马西森定则与速度饱和

## Dependence of <span className="katex">
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

 on Net Dopant Concentration and Temperature ｜ 费米能级与净掺杂浓度、温度的关系

净掺杂浓度：对于 N 型，为 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

N

</mi>

<mi>

D

</mi>
</msub>

<mo>

−

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

N_D - N_A

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

。

![Ef vs dopant concentration and temperature](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture3-01.webp)

For N-type:

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

n

</mi>

<mo>

=

</mo>

<msub>
<mi>

N

</mi>

<mi>

c

</mi>
</msub>

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

E

</mi>

<mi>

c

</mi>
</msub>

<mo>

−

</mo>

<msub>
<mi>

E

</mi>

<mi>

F

</mi>
</msub>

<mo stretchy="false">

)

</mo>

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

<mtext>



</mtext>

<mo>

⇒

</mo>

<mtext>



</mtext>

<msub>
<mi>

E

</mi>

<mi>

F

</mi>
</msub>

<mo>

=

</mo>

<msub>
<mi>

E

</mi>

<mi>

c

</mi>
</msub>

<mo>

−

</mo>

<mi>

k

</mi>

<mi>

T

</mi>

<mi>

ln

</mi>

<mo>

⁡

</mo>

<mfrac>
<msub>
<mi>

N

</mi>

<mi>

c

</mi>
</msub>

<mi>

n

</mi>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

n = N_c e^{-(E_c - E_F)/kT} \;\Rightarrow\; E_F = E_c - kT \ln\frac{N_c}{n}

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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.088em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.109em;">

N

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
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
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

E

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1645em;">
<span style="top:-2.357em;margin-left:-0.0576em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
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
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

E

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3448em;">
<span style="top:-2.3567em;margin-left:-0.0576em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

⇒

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

−

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:2.0463em;vertical-align:-0.686em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0315em;">

k

</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

T

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mop">

ln

</span>

<span className="mspace" style="margin-right:0.1667em;">



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
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.109em;">

N

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
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

> 非简并模型：掺得越多，<span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msub>
> <mi>
> 
> E
> 
> </mi>
> 
> <mi>
> 
> F
> 
> </mi>
> </msub>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> E_F
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
> <span className="mord,mathnormal" style="margin-right:0.0576em;">
> 
> E
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3283em;">
> <span style="top:-2.55em;margin-left:-0.0576em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mathnormal,mtight" style="margin-right:0.1389em;">
> 
> F
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
>  就越靠近你引入的杂质的那一侧带边（n 型靠 <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msub>
> <mi>
> 
> E
> 
> </mi>
> 
> <mi>
> 
> c
> 
> </mi>
> </msub>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> E_c
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
> <span className="mord,mathnormal" style="margin-right:0.0576em;">
> 
> E
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.1514em;">
> <span style="top:-2.55em;margin-left:-0.0576em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mathnormal,mtight">
> 
> c
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
> ，p 型靠 <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msub>
> <mi>
> 
> E
> 
> </mi>
> 
> <mi>
> 
> v
> 
> </mi>
> </msub>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> E_v
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
> <span className="mord,mathnormal" style="margin-right:0.0576em;">
> 
> E
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.1514em;">
> <span style="top:-2.55em;margin-left:-0.0576em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">
> 
> v
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
> ）；温度越高，<span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msub>
> <mi>
> 
> E
> 
> </mi>
> 
> <mi>
> 
> F
> 
> </mi>
> </msub>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> E_F
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
> <span className="mord,mathnormal" style="margin-right:0.0576em;">
> 
> E
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3283em;">
> <span style="top:-2.55em;margin-left:-0.0576em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mathnormal,mtight" style="margin-right:0.1389em;">
> 
> F
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
>  又会往带隙中部"退"一些；到重掺杂时需用简并模型。

## Intrinsic Fermi Level ｜ 本征费米能级 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

E

</mi>

<mi>

i

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

E_i

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
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0576em;margin-right:0.05em;">
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



To find <span className="katex">
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

 for an intrinsic semiconductor, use the fact that <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

n

</mi>

<mo>

=

</mo>

<mi>

p

</mi>
</mrow>

<annotation encoding="application/x-tex">

n = p

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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



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

:

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<msub>
<mi>

N

</mi>

<mi>

c

</mi>
</msub>

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

E

</mi>

<mi>

c

</mi>
</msub>

<mo>

−

</mo>

<msub>
<mi>

E

</mi>

<mi>

F

</mi>
</msub>

<mo stretchy="false">

)

</mo>

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

=

</mo>

<msub>
<mi>

N

</mi>

<mi>

v

</mi>
</msub>

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

E

</mi>

<mi>

F

</mi>
</msub>

<mo>

−

</mo>

<msub>
<mi>

E

</mi>

<mi>

v

</mi>
</msub>

<mo stretchy="false">

)

</mo>

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

N_c e^{-(E_c - E_F)/kT} = N_v e^{-(E_F - E_v)/kT}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.088em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.109em;">

N

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
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
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

E

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1645em;">
<span style="top:-2.357em;margin-left:-0.0576em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
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
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

E

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3448em;">
<span style="top:-2.3567em;margin-left:-0.0576em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.088em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.109em;">

N

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
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
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

E

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3448em;">
<span style="top:-2.3567em;margin-left:-0.0576em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
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
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

E

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1645em;">
<span style="top:-2.357em;margin-left:-0.0576em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
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
<span className="vlist" style="height:0.143em;">
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

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
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

<mo>

=

</mo>

<mfrac>
<mrow>
<msub>
<mi>

E

</mi>

<mi>

c

</mi>
</msub>

<mo>

+

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

<mn>

2

</mn>
</mfrac>

<mo>

+

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

<mn>

2

</mn>
</mfrac>

<mi>

ln

</mi>

<mo>

⁡

</mo>

<mfrac>
<msub>
<mi>

N

</mi>

<mi>

v

</mi>
</msub>

<msub>
<mi>

N

</mi>

<mi>

c

</mi>
</msub>
</mfrac>

<mo>

≡

</mo>

<msub>
<mi>

E

</mi>

<mi>

i

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

E_F = \frac{E_c + E_v}{2} + \frac{kT}{2} \ln\frac{N_v}{N_c} \equiv E_i

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



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
<span className="mord,mathnormal" style="margin-right:0.0315em;">

k

</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

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

<span className="mop">

ln

</span>

<span className="mspace" style="margin-right:0.1667em;">



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

N

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
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
<span className="mord,mathnormal" style="margin-right:0.109em;">

N

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
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

≡

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

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
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0576em;margin-right:0.05em;">
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

E

</mi>

<mi>

i

</mi>
</msub>

<mo>

=

</mo>

<mfrac>
<mrow>
<msub>
<mi>

E

</mi>

<mi>

c

</mi>
</msub>

<mo>

+

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

3

</mn>

<mi>

k

</mi>

<mi>

T

</mi>
</mrow>

<mn>

4

</mn>
</mfrac>

<mi>

ln

</mi>

<mo>

⁡

</mo>

<mfrac>
<msubsup>
<mi>

m

</mi>

<mi>

p

</mi>

<mo>

∗

</mo>
</msubsup>

<msubsup>
<mi>

m

</mi>

<mi>

n

</mi>

<mo>

∗

</mo>
</msubsup>
</mfrac>

<mo>

≃

</mo>

<mfrac>
<mrow>
<msub>
<mi>

E

</mi>

<mi>

c

</mi>
</msub>

<mo>

+

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

<mn>

2

</mn>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

E_i = \frac{E_c + E_v}{2} + \frac{3kT}{4} \ln\frac{m_p^*}{m_n^*} \simeq \frac{E_c + E_v}{2}

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
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0576em;margin-right:0.05em;">
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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



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
<span className="strut" style="height:2.3948em;vertical-align:-0.933em;">



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

3

</span>

<span className="mord,mathnormal" style="margin-right:0.0315em;">

k

</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

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

<span className="mop">

ln

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord">
<span className="mopen,nulldelimiter">



</span>

<span className="mfrac">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:1.4618em;">
<span style="top:-2.314em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord,mathnormal">

m

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.6147em;">
<span style="top:-2.453em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

n

</span>
</span>
</span>

<span style="top:-2.989em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mbin,mtight">

∗

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

<span style="top:-3.23em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="frac-line" style="border-bottom-width:0.04em;">



</span>
</span>

<span style="top:-3.7731em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord,mathnormal">

m

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.6887em;">
<span style="top:-2.453em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

p

</span>
</span>
</span>

<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mbin,mtight">

∗

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
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.933em;">
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

≃

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



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

这个只要记住 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

E

</mi>

<mi>

i

</mi>
</msub>

<mo>

=

</mo>

<mstyle scriptlevel="0" displaystyle="true">
<mfrac>
<mrow>
<msub>
<mi>

E

</mi>

<mi>

c

</mi>
</msub>

<mo>

+

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

<mn>

2

</mn>
</mfrac>
</mstyle>
</mrow>

<annotation encoding="application/x-tex">

E_i = \dfrac{E_c + E_v}{2}

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
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0576em;margin-right:0.05em;">
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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



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

 应该就 OK 了。

## <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

n

</mi>

<mo stretchy="false">

(

</mo>

<msub>
<mi>

n

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

E

</mi>

<mi>

i

</mi>
</msub>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

n(n_i, E_i)

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord,mathnormal">

n

</span>

<span className="mopen">

(

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
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0576em;margin-right:0.05em;">
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
</span>
</span>
</span>

 and <span className="katex">
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

<msub>
<mi>

n

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

E

</mi>

<mi>

i

</mi>
</msub>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

p(n_i, E_i)

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
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0576em;margin-right:0.05em;">
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
</span>
</span>
</span>

 ｜ 用 <span className="katex">
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

、<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

E

</mi>

<mi>

i

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

E_i

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
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0576em;margin-right:0.05em;">
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

 表示载流子浓度

In an **intrinsic semiconductor**, <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

n

</mi>

<mo>

=

</mo>

<mi>

p

</mi>

<mo>

=

</mo>

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

n = p = n_i

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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



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

 and <span className="katex">
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

<mo>

=

</mo>

<msub>
<mi>

E

</mi>

<mi>

i

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

E_F = E_i

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
<span className="mord,mathnormal" style="margin-right:0.0576em;">

E

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0576em;margin-right:0.05em;">
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

:

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

n

</mi>

<mo>

=

</mo>

<msub>
<mi>

n

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

N

</mi>

<mi>

c

</mi>
</msub>

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

E

</mi>

<mi>

c

</mi>
</msub>

<mo>

−

</mo>

<msub>
<mi>

E

</mi>

<mi>

i

</mi>
</msub>

<mo stretchy="false">

)

</mo>

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

<mtext>



</mtext>

<mo>

⇒

</mo>

<mtext>



</mtext>

<msub>
<mi>

N

</mi>

<mi>

c

</mi>
</msub>

<mo>

=

</mo>

<msub>
<mi>

n

</mi>

<mi>

i

</mi>
</msub>

<msup>
<mi>

e

</mi>

<mrow>
<mo stretchy="false">

(

</mo>

<msub>
<mi>

E

</mi>

<mi>

c

</mi>
</msub>

<mo>

−

</mo>

<msub>
<mi>

E

</mi>

<mi>

i

</mi>
</msub>

<mo stretchy="false">

)

</mo>

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

n = n_i = N_c e^{-(E_c - E_i)/kT} \;\Rightarrow\; N_c = n_i e^{(E_c - E_i)/kT}

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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.088em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.109em;">

N

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
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
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

E

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1645em;">
<span style="top:-2.357em;margin-left:-0.0576em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
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
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

E

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3281em;">
<span style="top:-2.357em;margin-left:-0.0576em;margin-right:0.0714em;">
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

<span className="mclose,mtight">

)

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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

⇒

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
<span className="mord,mathnormal" style="margin-right:0.109em;">

N

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.088em;vertical-align:-0.15em;">



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
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

E

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1645em;">
<span style="top:-2.357em;margin-left:-0.0576em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
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
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

E

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3281em;">
<span style="top:-2.357em;margin-left:-0.0576em;margin-right:0.0714em;">
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

<span className="mclose,mtight">

)

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

<msub>
<mi>

n

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

N

</mi>

<mi>

v

</mi>
</msub>

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

E

</mi>

<mi>

i

</mi>
</msub>

<mo>

−

</mo>

<msub>
<mi>

E

</mi>

<mi>

v

</mi>
</msub>

<mo stretchy="false">

)

</mo>

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

<mtext>



</mtext>

<mo>

⇒

</mo>

<mtext>



</mtext>

<msub>
<mi>

N

</mi>

<mi>

v

</mi>
</msub>

<mo>

=

</mo>

<msub>
<mi>

n

</mi>

<mi>

i

</mi>
</msub>

<msup>
<mi>

e

</mi>

<mrow>
<mo stretchy="false">

(

</mo>

<msub>
<mi>

E

</mi>

<mi>

i

</mi>
</msub>

<mo>

−

</mo>

<msub>
<mi>

E

</mi>

<mi>

v

</mi>
</msub>

<mo stretchy="false">

)

</mo>

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

p = n_i = N_v e^{-(E_i - E_v)/kT} \;\Rightarrow\; N_v = n_i e^{(E_i - E_v)/kT}

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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.088em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.109em;">

N

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
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
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

E

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3281em;">
<span style="top:-2.357em;margin-left:-0.0576em;margin-right:0.0714em;">
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

<span className="mbin,mtight">

−

</span>

<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

E

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1645em;">
<span style="top:-2.357em;margin-left:-0.0576em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
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
<span className="vlist" style="height:0.143em;">
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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

⇒

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
<span className="mord,mathnormal" style="margin-right:0.109em;">

N

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.088em;vertical-align:-0.15em;">



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
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

E

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3281em;">
<span style="top:-2.357em;margin-left:-0.0576em;margin-right:0.0714em;">
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

<span className="mbin,mtight">

−

</span>

<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

E

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1645em;">
<span style="top:-2.357em;margin-left:-0.0576em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
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
<span className="vlist" style="height:0.143em;">
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

把一般情况与本征情况相除：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mfrac>
<mi>

n

</mi>

<msub>
<mi>

n

</mi>

<mi>

i

</mi>
</msub>
</mfrac>

<mo>

=

</mo>

<mfrac>
<mrow>
<msub>
<mi>

N

</mi>

<mi>

c

</mi>
</msub>

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

E

</mi>

<mi>

c

</mi>
</msub>

<mo>

−

</mo>

<msub>
<mi>

E

</mi>

<mi>

F

</mi>
</msub>

<mo stretchy="false">

)

</mo>

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

<mrow>
<msub>
<mi>

N

</mi>

<mi>

c

</mi>
</msub>

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

E

</mi>

<mi>

c

</mi>
</msub>

<mo>

−

</mo>

<msub>
<mi>

E

</mi>

<mi>

i

</mi>
</msub>

<mo stretchy="false">

)

</mo>

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
</mfrac>

<mo>

=

</mo>

<msup>
<mi>

e

</mi>

<mrow>
<mo stretchy="false">

[

</mo>

<mo stretchy="false">

(

</mo>

<msub>
<mi>

E

</mi>

<mi>

c

</mi>
</msub>

<mo>

−

</mo>

<msub>
<mi>

E

</mi>

<mi>

i

</mi>
</msub>

<mo stretchy="false">

)

</mo>

<mo>

−

</mo>

<mo stretchy="false">

(

</mo>

<msub>
<mi>

E

</mi>

<mi>

c

</mi>
</msub>

<mo>

−

</mo>

<msub>
<mi>

E

</mi>

<mi>

F

</mi>
</msub>

<mo stretchy="false">

)

</mo>

<mo stretchy="false">

]

</mo>

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

=

</mo>

<msup>
<mi>

e

</mi>

<mrow>
<mo stretchy="false">

(

</mo>

<msub>
<mi>

E

</mi>

<mi>

F

</mi>
</msub>

<mo>

−

</mo>

<msub>
<mi>

E

</mi>

<mi>

i

</mi>
</msub>

<mo stretchy="false">

)

</mo>

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

\frac{n}{n_i} = \frac{N_c e^{-(E_c - E_F)/kT}}{N_c e^{-(E_c - E_i)/kT}} = e^{[(E_c - E_i) - (E_c - E_F)]/kT} = e^{(E_F - E_i)/kT}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
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
<span className="strut" style="height:2.419em;vertical-align:-0.854em;">



</span>

<span className="mord">
<span className="mopen,nulldelimiter">



</span>

<span className="mfrac">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:1.565em;">
<span style="top:-2.296em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.109em;">

N

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
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

<span className="mord">
<span className="mord,mathnormal">

e

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.814em;">
<span style="top:-2.989em;margin-right:0.05em;">
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
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

E

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1645em;">
<span style="top:-2.357em;margin-left:-0.0576em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
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
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

E

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3281em;">
<span style="top:-2.357em;margin-left:-0.0576em;margin-right:0.0714em;">
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

<span className="mclose,mtight">

)

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
<span className="mord,mathnormal" style="margin-right:0.109em;">

N

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
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

<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

E

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1645em;">
<span style="top:-2.357em;margin-left:-0.0576em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
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
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

E

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3448em;">
<span style="top:-2.3567em;margin-left:-0.0576em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
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

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.854em;">
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
<span className="strut" style="height:0.938em;">



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

[(

</span>

<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

E

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1645em;">
<span style="top:-2.357em;margin-left:-0.0576em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
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
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

E

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3281em;">
<span style="top:-2.357em;margin-left:-0.0576em;margin-right:0.0714em;">
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

<span className="mclose,mtight">

)

</span>

<span className="mbin,mtight">

−

</span>

<span className="mopen,mtight">

(

</span>

<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

E

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1645em;">
<span style="top:-2.357em;margin-left:-0.0576em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
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
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

E

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3448em;">
<span style="top:-2.3567em;margin-left:-0.0576em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
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
<span className="vlist" style="height:0.1433em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>

<span className="mclose,mtight">

)]

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
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

E

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3448em;">
<span style="top:-2.3567em;margin-left:-0.0576em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
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
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

E

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3281em;">
<span style="top:-2.357em;margin-left:-0.0576em;margin-right:0.0714em;">
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

<span className="mclose,mtight">

)

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

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mfrac>
<mi>

p

</mi>

<msub>
<mi>

n

</mi>

<mi>

i

</mi>
</msub>
</mfrac>

<mo>

=

</mo>

<mfrac>
<mrow>
<msub>
<mi>

N

</mi>

<mi>

v

</mi>
</msub>

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

E

</mi>

<mi>

F

</mi>
</msub>

<mo>

−

</mo>

<msub>
<mi>

E

</mi>

<mi>

v

</mi>
</msub>

<mo stretchy="false">

)

</mo>

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

<mrow>
<msub>
<mi>

N

</mi>

<mi>

v

</mi>
</msub>

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

E

</mi>

<mi>

i

</mi>
</msub>

<mo>

−

</mo>

<msub>
<mi>

E

</mi>

<mi>

v

</mi>
</msub>

<mo stretchy="false">

)

</mo>

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
</mfrac>

<mo>

=

</mo>

<msup>
<mi>

e

</mi>

<mrow>
<mo stretchy="false">

[

</mo>

<mo stretchy="false">

(

</mo>

<msub>
<mi>

E

</mi>

<mi>

i

</mi>
</msub>

<mo>

−

</mo>

<msub>
<mi>

E

</mi>

<mi>

v

</mi>
</msub>

<mo stretchy="false">

)

</mo>

<mo>

−

</mo>

<mo stretchy="false">

(

</mo>

<msub>
<mi>

E

</mi>

<mi>

F

</mi>
</msub>

<mo>

−

</mo>

<msub>
<mi>

E

</mi>

<mi>

v

</mi>
</msub>

<mo stretchy="false">

)

</mo>

<mo stretchy="false">

]

</mo>

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

=

</mo>

<msup>
<mi>

e

</mi>

<mrow>
<mo stretchy="false">

(

</mo>

<msub>
<mi>

E

</mi>

<mi>

i

</mi>
</msub>

<mo>

−

</mo>

<msub>
<mi>

E

</mi>

<mi>

F

</mi>
</msub>

<mo stretchy="false">

)

</mo>

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

\frac{p}{n_i} = \frac{N_v e^{-(E_F - E_v)/kT}}{N_v e^{-(E_i - E_v)/kT}} = e^{[(E_i - E_v) - (E_F - E_v)]/kT} = e^{(E_i - E_F)/kT}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
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
<span className="strut" style="height:2.419em;vertical-align:-0.854em;">



</span>

<span className="mord">
<span className="mopen,nulldelimiter">



</span>

<span className="mfrac">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:1.565em;">
<span style="top:-2.296em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.109em;">

N

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
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

<span className="mord">
<span className="mord,mathnormal">

e

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.814em;">
<span style="top:-2.989em;margin-right:0.05em;">
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
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

E

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3281em;">
<span style="top:-2.357em;margin-left:-0.0576em;margin-right:0.0714em;">
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

<span className="mbin,mtight">

−

</span>

<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

E

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1645em;">
<span style="top:-2.357em;margin-left:-0.0576em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
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
<span className="vlist" style="height:0.143em;">
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
<span className="mord,mathnormal" style="margin-right:0.109em;">

N

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
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

<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

E

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3448em;">
<span style="top:-2.3567em;margin-left:-0.0576em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
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
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

E

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1645em;">
<span style="top:-2.357em;margin-left:-0.0576em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
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
<span className="vlist" style="height:0.143em;">
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

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.854em;">
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
<span className="strut" style="height:0.938em;">



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

[(

</span>

<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

E

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3281em;">
<span style="top:-2.357em;margin-left:-0.0576em;margin-right:0.0714em;">
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

<span className="mbin,mtight">

−

</span>

<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

E

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1645em;">
<span style="top:-2.357em;margin-left:-0.0576em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
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
<span className="vlist" style="height:0.143em;">
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

<span className="mopen,mtight">

(

</span>

<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

E

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3448em;">
<span style="top:-2.3567em;margin-left:-0.0576em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
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
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

E

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1645em;">
<span style="top:-2.357em;margin-left:-0.0576em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
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
<span className="vlist" style="height:0.143em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>

<span className="mclose,mtight">

)]

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
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

E

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3281em;">
<span style="top:-2.357em;margin-left:-0.0576em;margin-right:0.0714em;">
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

<span className="mbin,mtight">

−

</span>

<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

E

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3448em;">
<span style="top:-2.3567em;margin-left:-0.0576em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
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

即可得到：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

n

</mi>

<mo>

=

</mo>

<msub>
<mi>

n

</mi>

<mi>

i

</mi>
</msub>

<msup>
<mi>

e

</mi>

<mrow>
<mo stretchy="false">

(

</mo>

<msub>
<mi>

E

</mi>

<mi>

F

</mi>
</msub>

<mo>

−

</mo>

<msub>
<mi>

E

</mi>

<mi>

i

</mi>
</msub>

<mo stretchy="false">

)

</mo>

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

<mo separator="true">

,

</mo>

<mspace width="2em">



</mspace>

<mi>

p

</mi>

<mo>

=

</mo>

<msub>
<mi>

n

</mi>

<mi>

i

</mi>
</msub>

<msup>
<mi>

e

</mi>

<mrow>
<mo stretchy="false">

(

</mo>

<msub>
<mi>

E

</mi>

<mi>

i

</mi>
</msub>

<mo>

−

</mo>

<msub>
<mi>

E

</mi>

<mi>

F

</mi>
</msub>

<mo stretchy="false">

)

</mo>

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

n = n_i e^{(E_F - E_i)/kT}, \qquad p = n_i e^{(E_i - E_F)/kT}

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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.1324em;vertical-align:-0.1944em;">



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
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

E

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3448em;">
<span style="top:-2.3567em;margin-left:-0.0576em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
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
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

E

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3281em;">
<span style="top:-2.357em;margin-left:-0.0576em;margin-right:0.0714em;">
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

<span className="mclose,mtight">

)

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

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:2em;">



</span>

<span className="mspace" style="margin-right:0.1667em;">



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
<span className="strut" style="height:1.088em;vertical-align:-0.15em;">



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
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

E

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3281em;">
<span style="top:-2.357em;margin-left:-0.0576em;margin-right:0.0714em;">
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

<span className="mbin,mtight">

−

</span>

<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

E

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3448em;">
<span style="top:-2.3567em;margin-left:-0.0576em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
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

These two are very important relations.

> **Summary: Important Terminology**
> 
> **donor:** impurity atom that increases <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <mi>
> 
> n
> 
> </mi>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> n
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
> n
> 
> </span>
> </span>
> </span>
> </span>
> 
> , for example Group-V elements
> 
> **acceptor:** impurity atom that increases <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <mi>
> 
> p
> 
> </mi>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> p
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
> p
> 
> </span>
> </span>
> </span>
> </span>
> 
> , for example Group-III elements
> 
> **n-type material:** contains more electrons than holes
> 
> **p-type material:** contains more holes than electrons
> 
> **majority carrier:** the most abundant carrier
> 
> **minority carrier:** the least abundant carrier
> 
> **intrinsic semiconductor:** <span className="katex">
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
> <mo>
> 
> =
> 
> </mo>
> 
> <mi>
> 
> p
> 
> </mi>
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
> n
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
> n = p = n_i
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
> n
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
> <span className="strut" style="height:0.625em;vertical-align:-0.1944em;">
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
> <span className="strut" style="height:0.5806em;vertical-align:-0.15em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> <span className="mord,mathnormal">
> 
> n
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
> 
> 
> **extrinsic semiconductor:** doped semiconductor, <span className="katex">
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
> <mo mathvariant="normal">
> 
> ≠
> 
> </mo>
> 
> <mi>
> 
> p
> 
> </mi>
> 
> <mo mathvariant="normal">
> 
> ≠
> 
> </mo>
> 
> <msub>
> <mi>
> 
> n
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
> n \ne p \ne n_i
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
> n
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
> <span className="mrel">
> <span className="mord,vbox">
> <span className="thinbox">
> <span className="rlap">
> <span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">
> 
> 
> 
> </span>
> 
> <span className="inner">
> <span className="mord">
> <span className="mrel">
> 
> 
> 
> </span>
> </span>
> </span>
> 
> <span className="fix">
> 
> 
> 
> </span>
> </span>
> </span>
> </span>
> </span>
> 
> <span className="mspace,nobreak">
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
> <span className="mord,mathnormal">
> 
> p
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
> <span className="mrel">
> <span className="mord,vbox">
> <span className="thinbox">
> <span className="rlap">
> <span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">
> 
> 
> 
> </span>
> 
> <span className="inner">
> <span className="mord">
> <span className="mrel">
> 
> 
> 
> </span>
> </span>
> </span>
> 
> <span className="fix">
> 
> 
> 
> </span>
> </span>
> </span>
> </span>
> </span>
> 
> <span className="mspace,nobreak">
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
> <span className="strut" style="height:0.5806em;vertical-align:-0.15em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> <span className="mord,mathnormal">
> 
> n
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

## Nondegenerately Doped Semiconductor ｜ 非简并半导体

**Non**degenerately doped: **not very heavily doped**.

**经验判据**：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

E

</mi>

<mi>

v

</mi>
</msub>

<mo>

+

</mo>

<mn>

3

</mn>

<mi>

k

</mi>

<mi>

T

</mi>

<mo>

≤

</mo>

<msub>
<mi>

E

</mi>

<mi>

F

</mi>
</msub>

<mo>

≤

</mo>

<msub>
<mi>

E

</mi>

<mi>

c

</mi>
</msub>

<mo>

−

</mo>

<mn>

3

</mn>

<mi>

k

</mi>

<mi>

T

</mi>
</mrow>

<annotation encoding="application/x-tex">

E_v + 3kT \le E_F \le E_c - 3kT

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8304em;vertical-align:-0.136em;">



</span>

<span className="mord">

3

</span>

<span className="mord,mathnormal" style="margin-right:0.0315em;">

k

</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

T

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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

≤

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

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

<span className="mord">

3

</span>

<span className="mord,mathnormal" style="margin-right:0.0315em;">

k

</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

T

</span>
</span>
</span>
</span>



![Nondegenerately doped](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture3-02.webp)

## Degenerately Doped Semiconductor ｜ 简并半导体

If **a semiconductor is very heavily doped**, the Boltzmann approximation is not valid.

![Degenerately doped](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture3-03.webp)

Terminology:

- "n+" <span className="katex">
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

 **degenerately n-type doped**, <span className="katex">
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

<mo>

≅

</mo>

<msub>
<mi>

E

</mi>

<mi>

c

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

E_F \cong E_c

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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

≅

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

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
</span>
</span>
</span>
- "p+" <span className="katex">
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

 **degenerately p-type doped**, <span className="katex">
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

<mo>

≅

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

E_F \cong E_v

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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

≅

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

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

## Band Gap Narrowing ｜ 带隙变窄

If the dopant concentration is a significant fraction of the silicon atomic density, the energy-band structure is perturbed and the band gap is reduced by <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi mathvariant="normal">

Δ

</mi>

<msub>
<mi>

E

</mi>

<mi>

G

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

\Delta E_G

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

:

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

E

</mi>

<mi>

G

</mi>
</msub>

<mo>

≅

</mo>

<mn>

3.5

</mn>

<mo>

×

</mo>

<msup>
<mn>

10

</mn>

<mrow>
<mo>

−

</mo>

<mn>

8

</mn>
</mrow>
</msup>

<mtext>



</mtext>

<msup>
<mi>

N

</mi>

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

<msqrt>
<mfrac>
<mn>

300

</mn>

<mi>

T

</mi>
</mfrac>
</msqrt>
</mrow>

<annotation encoding="application/x-tex">

\Delta E_G \cong 3.5 \times 10^{-8}\, N^{1/3} \sqrt{\frac{300}{T}}

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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

≅

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.7278em;vertical-align:-0.0833em;">



</span>

<span className="mord">

3.5

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
<span className="strut" style="height:2.44em;vertical-align:-0.7884em;">



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
<span className="mord,mtight">

−

</span>

<span className="mord,mtight">

8

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

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.109em;">

N

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

<span className="mord,sqrt">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:1.6516em;">
<span className="svg-align" style="top:-4.4em;">
<span className="pstrut" style="height:4.4em;">



</span>

<span className="mord" style="padding-left:1em;">
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
<span className="mord,mathnormal" style="margin-right:0.1389em;">

T

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

300

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

<span style="top:-3.6116em;">
<span className="pstrut" style="height:4.4em;">



</span>

<span className="hide-tail" style="min-width:1.02em;height:2.48em;">
<svg xmlns="http://www.w3.org/2000/svg" width="400em" height="2.48em" viewBox="0 0 400000 2592" preserveAspectRatio="xMinYMin slice">
<path d="M424,2478
c-1.3,-0.7,-38.5,-172,-111.5,-514c-73,-342,-109.8,-513.3,-110.5,-514
c0,-2,-10.7,14.3,-32,49c-4.7,7.3,-9.8,15.7,-15.5,25c-5.7,9.3,-9.8,16,-12.5,20
s-5,7,-5,7c-4,-3.3,-8.3,-7.7,-13,-13s-13,-13,-13,-13s76,-122,76,-122s77,-121,77,-121
s209,968,209,968c0,-2,84.7,-361.7,254,-1079c169.3,-717.3,254.7,-1077.7,256,-1081
l0 -0c4,-6.7,10,-10,18,-10 H400000
v40H1014.6
s-87.3,378.7,-272.6,1166c-185.3,787.3,-279.3,1182.3,-282,1185
c-2,6,-10,9,-24,9
c-8,0,-12,-0.7,-12,-2z M1001 80
h400000v40h-400000z">



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
<span className="vlist" style="height:0.7884em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

![Band gap narrowing](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture3-04.webp)

当**掺杂浓度 NNN（施主或受主）高到接近晶体本征原子密度的一小部分**时，杂质带与本征能带发生明显相互作用；同时强电荷屏蔽、交换-相关多体效应会把导带底 <span className="katex">
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
</mrow>

<annotation encoding="application/x-tex">

E_c

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
</span>
</span>
</span>

 **下拉**、价带顶 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
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

E_v

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

 **上推**，于是**有效带隙**变小。

> 掺杂越多、温度越低，收缩越强。这个公式可以抄一下，感觉看公式就可以理解了。

## Dopant Ionization ｜ 杂质电离

不是重点，上课应该没怎么提，看一下就行。

![Dopant ionization](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture3-05.webp)

> 计算过程：
> 
> 先假设完全电离（非简并），求费米能级的位置：由 <span className="katex">
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
> <mo>
> 
> =
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
> d
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
> N
> 
> </mi>
> 
> <mi>
> 
> c
> 
> </mi>
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
> <mo stretchy="false">
> 
> (
> 
> </mo>
> 
> <msub>
> <mi>
> 
> E
> 
> </mi>
> 
> <mi>
> 
> c
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
> <msub>
> <mi>
> 
> E
> 
> </mi>
> 
> <mi>
> 
> F
> 
> </mi>
> </msub>
> 
> <mo stretchy="false">
> 
> )
> 
> </mo>
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
> 
> <mi>
> 
> T
> 
> </mi>
> </mrow>
> </msup>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> n = N_d = N_c e^{-(E_c - E_F)/kT}
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
> n
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
> <span className="vlist" style="height:0.3361em;">
> <span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
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
> <span className="mord,mathnormal" style="margin-right:0.109em;">
> 
> N
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.1514em;">
> <span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mathnormal,mtight">
> 
> c
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
> <span className="mopen,mtight">
> 
> (
> 
> </span>
> 
> <span className="mord,mtight">
> <span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">
> 
> E
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.1645em;">
> <span style="top:-2.357em;margin-left:-0.0576em;margin-right:0.0714em;">
> <span className="pstrut" style="height:2.5em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size3,size1,mtight">
> <span className="mord,mathnormal,mtight">
> 
> c
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
> <span className="mbin,mtight">
> 
> −
> 
> </span>
> 
> <span className="mord,mtight">
> <span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">
> 
> E
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3448em;">
> <span style="top:-2.3567em;margin-left:-0.0576em;margin-right:0.0714em;">
> <span className="pstrut" style="height:2.5em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size3,size1,mtight">
> <span className="mord,mathnormal,mtight" style="margin-right:0.1389em;">
> 
> F
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
> 
> <span className="mord,mtight">
> 
> /
> 
> </span>
> 
> <span className="mord,mathnormal,mtight" style="margin-right:0.0315em;">
> 
> k
> 
> </span>
> 
> <span className="mord,mathnormal,mtight" style="margin-right:0.1389em;">
> 
> T
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
>  可得 <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msub>
> <mi>
> 
> E
> 
> </mi>
> 
> <mi>
> 
> F
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
> E
> 
> </mi>
> 
> <mi>
> 
> c
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
> <mn>
> 
> 146
> 
> </mn>
> 
> <mtext>
> 
> 
> 
> </mtext>
> 
> <mtext>
> 
> meV
> 
> </mtext>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> E_F = E_c - 146\,\text{meV}
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
> <span className="mord,mathnormal" style="margin-right:0.0576em;">
> 
> E
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3283em;">
> <span style="top:-2.55em;margin-left:-0.0576em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mathnormal,mtight" style="margin-right:0.1389em;">
> 
> F
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
> <span className="strut" style="height:0.8333em;vertical-align:-0.15em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> <span className="mord,mathnormal" style="margin-right:0.0576em;">
> 
> E
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.1514em;">
> <span style="top:-2.55em;margin-left:-0.0576em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mathnormal,mtight">
> 
> c
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
> <span className="mord">
> 
> 146
> 
> </span>
> 
> <span className="mspace" style="margin-right:0.1667em;">
> 
> 
> 
> </span>
> 
> <span className="mord,text">
> <span className="mord">
> 
> meV
> 
> </span>
> </span>
> </span>
> </span>
> </span>
> 
> 。
> 
> 对于 Silicon，施主能级一般在导带下方 <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <mn>
> 
> 45
> 
> </mn>
> 
> <mtext>
> 
> 
> 
> </mtext>
> 
> <mtext>
> 
> meV
> 
> </mtext>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> 45\,\text{meV}
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
> <span className="mord">
> 
> 45
> 
> </span>
> 
> <span className="mspace" style="margin-right:0.1667em;">
> 
> 
> 
> </span>
> 
> <span className="mord,text">
> <span className="mord">
> 
> meV
> 
> </span>
> </span>
> </span>
> </span>
> </span>
> 
> ，所以有 <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msub>
> <mi>
> 
> E
> 
> </mi>
> 
> <mi>
> 
> c
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
> <msub>
> <mi>
> 
> E
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
> =
> 
> </mo>
> 
> <mn>
> 
> 45
> 
> </mn>
> 
> <mtext>
> 
> 
> 
> </mtext>
> 
> <mtext>
> 
> meV
> 
> </mtext>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> E_c - E_d = 45\,\text{meV}
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
> <span className="mord,mathnormal" style="margin-right:0.0576em;">
> 
> E
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.1514em;">
> <span style="top:-2.55em;margin-left:-0.0576em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mathnormal,mtight">
> 
> c
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
> <span className="strut" style="height:0.8333em;vertical-align:-0.15em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> <span className="mord,mathnormal" style="margin-right:0.0576em;">
> 
> E
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3361em;">
> <span style="top:-2.55em;margin-left:-0.0576em;margin-right:0.05em;">
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
> <span className="strut" style="height:0.6833em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> 
> 45
> 
> </span>
> 
> <span className="mspace" style="margin-right:0.1667em;">
> 
> 
> 
> </span>
> 
> <span className="mord,text">
> <span className="mord">
> 
> meV
> 
> </span>
> </span>
> </span>
> </span>
> </span>
> 
> 。
> 
> 计算 <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <mi>
> 
> f
> 
> </mi>
> 
> <mo stretchy="false">
> 
> (
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
> 
> <mo>
> 
> =
> 
> </mo>
> 
> <mstyle scriptlevel="0" displaystyle="true">
> <mfrac>
> <mn>
> 
> 1
> 
> </mn>
> 
> <mrow>
> <mn>
> 
> 1
> 
> </mn>
> 
> <mo>
> 
> +
> 
> </mo>
> 
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
> <msup>
> <mi>
> 
> e
> 
> </mi>
> 
> <mrow>
> <mo stretchy="false">
> 
> (
> 
> </mo>
> 
> <msub>
> <mi>
> 
> E
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
> −
> 
> </mo>
> 
> <msub>
> <mi>
> 
> E
> 
> </mi>
> 
> <mi>
> 
> F
> 
> </mi>
> </msub>
> 
> <mo stretchy="false">
> 
> )
> 
> </mo>
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
> 
> <mi>
> 
> T
> 
> </mi>
> </mrow>
> </msup>
> </mrow>
> </mfrac>
> </mstyle>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> f(E) = \dfrac{1}{1 + \frac{1}{2} e^{(E_d - E_F)/kT}}
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
> <span className="mord,mathnormal" style="margin-right:0.1076em;">
> 
> f
> 
> </span>
> 
> <span className="mopen">
> 
> (
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
> <span className="strut" style="height:2.4015em;vertical-align:-1.0801em;">
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
> <span className="vlist" style="height:1.3214em;">
> <span style="top:-2.2649em;">
> <span className="pstrut" style="height:3em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> <span className="mord">
> 
> 1
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
> <span className="vlist" style="height:0.814em;">
> <span style="top:-2.989em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mtight">
> <span className="mopen,mtight">
> 
> (
> 
> </span>
> 
> <span className="mord,mtight">
> <span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">
> 
> E
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3448em;">
> <span style="top:-2.3488em;margin-left:-0.0576em;margin-right:0.0714em;">
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
> 
> <span className="mbin,mtight">
> 
> −
> 
> </span>
> 
> <span className="mord,mtight">
> <span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">
> 
> E
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3448em;">
> <span style="top:-2.3567em;margin-left:-0.0576em;margin-right:0.0714em;">
> <span className="pstrut" style="height:2.5em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size3,size1,mtight">
> <span className="mord,mathnormal,mtight" style="margin-right:0.1389em;">
> 
> F
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
> 
> <span className="mord,mtight">
> 
> /
> 
> </span>
> 
> <span className="mord,mathnormal,mtight" style="margin-right:0.0315em;">
> 
> k
> 
> </span>
> 
> <span className="mord,mathnormal,mtight" style="margin-right:0.1389em;">
> 
> T
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
> <span className="vlist" style="height:1.0801em;">
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
> ，和 Fermi-Dirac 分布相比多了一个 <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <mi>
> 
> g
> 
> </mi>
> 
> <mo>
> 
> =
> 
> </mo>
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
> g = 2
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
> <span className="mord,mathnormal" style="margin-right:0.0359em;">
> 
> g
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
> <span className="strut" style="height:0.6444em;">
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
> </span>
> </span>
> </span>
> 
>  的简并度（这个上课其实没讲）。
> 
> 然后算出来实际上也只有 4% 左右没电离，所以假设完全电离是合理的。
> 
> 这个应该是推出一个结论：掺杂的 dopant 基本都能全电离，可以直接让 <span className="katex">
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
> <mo>
> 
> =
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
> d
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
> <msub>
> <mi>
> 
> N
> 
> </mi>
> 
> <mi>
> 
> a
> 
> </mi>
> </msub>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> n = N_d - N_a
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
> n
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
> <span className="vlist" style="height:0.3361em;">
> <span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
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
> <span className="vlist" style="height:0.1514em;">
> <span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mathnormal,mtight">
> 
> a
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
> （<span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msub>
> <mi>
> 
> N
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
> ≫
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
> a
> 
> </mi>
> </msub>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> N_d \gg N_a
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
> N
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3361em;">
> <span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
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
> ≫
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
> <span className="mord,mathnormal" style="margin-right:0.109em;">
> 
> N
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.1514em;">
> <span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mathnormal,mtight">
> 
> a
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
> ）等等。

## General Theory of <span className="katex">
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

 and <span className="katex">
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

 ｜ 载流子浓度的一般理论

Charge neutrality ｜ 电中性：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

n

</mi>

<mo>

+

</mo>

<msub>
<mi>

N

</mi>

<mi>

a

</mi>
</msub>

<mo>

=

</mo>

<mi>

p

</mi>

<mo>

+

</mo>

<msub>
<mi>

N

</mi>

<mi>

d

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

n + N_a = p + N_d

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6667em;vertical-align:-0.0833em;">



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
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.109em;">

N

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

a

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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

<span className="mord,mathnormal">

p

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
<span className="mord,mathnormal" style="margin-right:0.109em;">

N

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
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
</span>

Thermal equilibrium ｜ 热平衡：

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

p

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
</mrow>

<annotation encoding="application/x-tex">

np = n_i^2

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.625em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal">

n

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
<span className="strut" style="height:1.1111em;vertical-align:-0.247em;">



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
</span>
</span>
</span>
</span>

然后解方程：

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

<mfrac>
<mrow>
<msub>
<mi>

N

</mi>

<mi>

a

</mi>
</msub>

<mo>

−

</mo>

<msub>
<mi>

N

</mi>

<mi>

d

</mi>
</msub>
</mrow>

<mn>

2

</mn>
</mfrac>

<mo>

+

</mo>

<msup>
<mrow>
<mo fence="true">

[

</mo>

<msup>
<mrow>
<mo fence="true">

(

</mo>

<mfrac>
<mrow>
<msub>
<mi>

N

</mi>

<mi>

a

</mi>
</msub>

<mo>

−

</mo>

<msub>
<mi>

N

</mi>

<mi>

d

</mi>
</msub>
</mrow>

<mn>

2

</mn>
</mfrac>

<mo fence="true">

)

</mo>
</mrow>

<mn>

2

</mn>
</msup>

<mo>

+

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

<mo fence="true">

]

</mo>
</mrow>

<mrow>
<mn>

1

</mn>

<mi mathvariant="normal">

/

</mi>

<mn>

2

</mn>
</mrow>
</msup>
</mrow>

<annotation encoding="application/x-tex">

p = \frac{N_a - N_d}{2} + \left[\left(\frac{N_a - N_d}{2}\right)^2 + n_i^2\right]^{1/2}

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
<span className="mord,mathnormal" style="margin-right:0.109em;">

N

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

a

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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
<span className="mord,mathnormal" style="margin-right:0.109em;">

N

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
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
<span className="strut" style="height:3.2779em;vertical-align:-1.25em;">



</span>

<span className="minner">
<span className="minner">
<span className="mopen,delimcenter" style="top:0em;">
<span className="delimsizing,size4">

[

</span>
</span>

<span className="minner">
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
<span className="mord,mathnormal" style="margin-right:0.109em;">

N

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

a

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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
<span className="mord,mathnormal" style="margin-right:0.109em;">

N

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
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

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:1.654em;">
<span style="top:-3.9029em;margin-right:0.05em;">
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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



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

<span className="mclose,delimcenter" style="top:0em;">
<span className="delimsizing,size4">

]

</span>
</span>
</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:2.0279em;">
<span style="top:-4.2029em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">

1/2

</span>
</span>
</span>
</span>
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

n

</mi>

<mo>

=

</mo>

<mfrac>
<mrow>
<msub>
<mi>

N

</mi>

<mi>

d

</mi>
</msub>

<mo>

−

</mo>

<msub>
<mi>

N

</mi>

<mi>

a

</mi>
</msub>
</mrow>

<mn>

2

</mn>
</mfrac>

<mo>

+

</mo>

<msup>
<mrow>
<mo fence="true">

[

</mo>

<msup>
<mrow>
<mo fence="true">

(

</mo>

<mfrac>
<mrow>
<msub>
<mi>

N

</mi>

<mi>

d

</mi>
</msub>

<mo>

−

</mo>

<msub>
<mi>

N

</mi>

<mi>

a

</mi>
</msub>
</mrow>

<mn>

2

</mn>
</mfrac>

<mo fence="true">

)

</mo>
</mrow>

<mn>

2

</mn>
</msup>

<mo>

+

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

<mo fence="true">

]

</mo>
</mrow>

<mrow>
<mn>

1

</mn>

<mi mathvariant="normal">

/

</mi>

<mn>

2

</mn>
</mrow>
</msup>
</mrow>

<annotation encoding="application/x-tex">

n = \frac{N_d - N_a}{2} + \left[\left(\frac{N_d - N_a}{2}\right)^2 + n_i^2\right]^{1/2}

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
<span className="mord,mathnormal" style="margin-right:0.109em;">

N

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

−

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
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

a

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



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
<span className="strut" style="height:3.2779em;vertical-align:-1.25em;">



</span>

<span className="minner">
<span className="minner">
<span className="mopen,delimcenter" style="top:0em;">
<span className="delimsizing,size4">

[

</span>
</span>

<span className="minner">
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
<span className="mord,mathnormal" style="margin-right:0.109em;">

N

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

−

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
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

a

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



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

<span className="mclose,delimcenter" style="top:0em;">
<span className="delimsizing,size3">

)

</span>
</span>
</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:1.654em;">
<span style="top:-3.9029em;margin-right:0.05em;">
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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



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

<span className="mclose,delimcenter" style="top:0em;">
<span className="delimsizing,size4">

]

</span>
</span>
</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:2.0279em;">
<span style="top:-4.2029em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">

1/2

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

> **Important concepts**
> 
> - Dopant compensation ｜ 补偿掺杂：同时有施主和受主。一部分施主产生的电子被受主"中和"，真正决定导电类型的是两者的**差**。
> - Net dopant concentration ｜ 净掺杂浓度：<span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msub>
> <mi>
> 
> N
> 
> </mi>
> 
> <mrow>
> <mi>
> 
> n
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
> <msub>
> <mi>
> 
> N
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
> −
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
> a
> 
> </mi>
> </msub>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> N_{net} = N_d - N_a
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
> N
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.2806em;">
> <span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
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
> n
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
> <span className="vlist" style="height:0.3361em;">
> <span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
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
> <span className="vlist" style="height:0.1514em;">
> <span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mathnormal,mtight">
> 
> a
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
> （if <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msub>
> <mi>
> 
> N
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
> >
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
> a
> 
> </mi>
> </msub>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> N_d > N_a
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
> N
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3361em;">
> <span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
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
> >
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
> <span className="mord,mathnormal" style="margin-right:0.109em;">
> 
> N
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.1514em;">
> <span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mathnormal,mtight">
> 
> a
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
> ）

![General theory of n and p](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture3-06.webp)

可抄公式。

## Carrier Concentration at Extremely High and Low Temperatures ｜ 极端温度下的载流子浓度

![Carrier concentration vs temperature](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture3-07.webp)

就是掺杂半导体载流子浓度如何随温度变化。

1. The temperature is **extremely high**: a large number of valence band electrons are excited to the conduction band, and the effect of doping is relatively small, **approximate intrinsic behavior**. ｜ 当温度很高时，掺杂的半导体就表现为接近本征半导体未掺杂时的情况了。<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

n

</mi>

<mo>

=

</mo>

<mi>

p

</mi>

<mo>

=

</mo>

<msub>
<mi>

n

</mi>

<mi>

i

</mi>
</msub>

<mo>

=

</mo>

<msqrt>
<mrow>
<msub>
<mi>

N

</mi>

<mi>

c

</mi>
</msub>

<msub>
<mi>

N

</mi>

<mi>

v

</mi>
</msub>
</mrow>
</msqrt>

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

<msub>
<mi>

E

</mi>

<mi>

g

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
</mrow>

<annotation encoding="application/x-tex">

n = p = n_i = \sqrt{N_c N_v}\, e^{-E_g / 2kT}

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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.24em;vertical-align:-0.2395em;">



</span>

<span className="mord,sqrt">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:1.0005em;">
<span className="svg-align" style="top:-3.2em;">
<span className="pstrut" style="height:3.2em;">



</span>

<span className="mord" style="padding-left:1em;">
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.109em;">

N

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
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

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.109em;">

N

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
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

<span style="top:-2.9605em;">
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
<span className="vlist" style="height:0.2395em;">
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

<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

E

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1645em;">
<span style="top:-2.357em;margin-left:-0.0576em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
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
<span className="vlist" style="height:0.2819em;">
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
</span>
</span>
</span>
</span>
2. The temperature is **extremely low**: **freeze out**. ｜ 电子基本上不电离，只有少量热激发的电子进入导带，<span className="katex">
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

 随降温快速下降。<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

n

</mi>

<mo>

=

</mo>

<msqrt>
<mfrac>
<mrow>
<msub>
<mi>

N

</mi>

<mi>

c

</mi>
</msub>

<msub>
<mi>

N

</mi>

<mi>

d

</mi>
</msub>
</mrow>

<mn>

2

</mn>
</mfrac>
</msqrt>

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

<mo stretchy="false">

(

</mo>

<msub>
<mi>

E

</mi>

<mi>

c

</mi>
</msub>

<mo>

−

</mo>

<msub>
<mi>

E

</mi>

<mi>

d

</mi>
</msub>

<mo stretchy="false">

)

</mo>

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
</mrow>

<annotation encoding="application/x-tex">

n = \sqrt{\frac{N_c N_d}{2}}\, e^{-(E_c - E_d)/2kT}

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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:2.44em;vertical-align:-0.769em;">



</span>

<span className="mord,sqrt">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:1.671em;">
<span className="svg-align" style="top:-4.4em;">
<span className="pstrut" style="height:4.4em;">



</span>

<span className="mord" style="padding-left:1em;">
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
<span className="mord,mathnormal" style="margin-right:0.109em;">

N

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
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

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.109em;">

N

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
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

<span style="top:-3.631em;">
<span className="pstrut" style="height:4.4em;">



</span>

<span className="hide-tail" style="min-width:1.02em;height:2.48em;">
<svg xmlns="http://www.w3.org/2000/svg" width="400em" height="2.48em" viewBox="0 0 400000 2592" preserveAspectRatio="xMinYMin slice">
<path d="M424,2478
c-1.3,-0.7,-38.5,-172,-111.5,-514c-73,-342,-109.8,-513.3,-110.5,-514
c0,-2,-10.7,14.3,-32,49c-4.7,7.3,-9.8,15.7,-15.5,25c-5.7,9.3,-9.8,16,-12.5,20
s-5,7,-5,7c-4,-3.3,-8.3,-7.7,-13,-13s-13,-13,-13,-13s76,-122,76,-122s77,-121,77,-121
s209,968,209,968c0,-2,84.7,-361.7,254,-1079c169.3,-717.3,254.7,-1077.7,256,-1081
l0 -0c4,-6.7,10,-10,18,-10 H400000
v40H1014.6
s-87.3,378.7,-272.6,1166c-185.3,787.3,-279.3,1182.3,-282,1185
c-2,6,-10,9,-24,9
c-8,0,-12,-0.7,-12,-2z M1001 80
h400000v40h-400000z">



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
<span className="vlist" style="height:0.769em;">
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
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

E

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1645em;">
<span style="top:-2.357em;margin-left:-0.0576em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
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
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

E

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3448em;">
<span style="top:-2.3488em;margin-left:-0.0576em;margin-right:0.0714em;">
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

<span className="mclose,mtight">

)

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
</span>
</span>
</span>
</span>

## Infrared Detector Based on Freeze-out ｜ 基于 Freeze-out 的红外探测器

![Infrared detector](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture3-08.webp)

In doped Si operating in the **freeze-out mode**, conduction electrons are created when the **infrared** photons provide the energy to ionize the donor atoms.

把掺杂 Si 冷到 freeze-out，**让施主几乎都保持中性**，此时几乎没有热生成电子；让红外光子把施主上的电子打到导带，靠这种**光致电离**来产生导电电子并输出信号，就能探测到 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mo>

∼

</mo>

<mn>

0.1

</mn>

<mtext>



</mtext>

<mtext>

eV

</mtext>
</mrow>

<annotation encoding="application/x-tex">

\sim 0.1\,\text{eV}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.3669em;">



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

<span className="mord">

0.1

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord,text">
<span className="mord">

eV

</span>
</span>
</span>
</span>
</span>

 的黑体辐射。了解一下即可。

> **Summary: Important Relations**
> 
> - <span className="katex">
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
> <mo>
> 
> =
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
> c
> 
> </mi>
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
> <mo stretchy="false">
> 
> (
> 
> </mo>
> 
> <msub>
> <mi>
> 
> E
> 
> </mi>
> 
> <mi>
> 
> c
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
> <msub>
> <mi>
> 
> E
> 
> </mi>
> 
> <mi>
> 
> F
> 
> </mi>
> </msub>
> 
> <mo stretchy="false">
> 
> )
> 
> </mo>
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
> 
> <mi>
> 
> T
> 
> </mi>
> </mrow>
> </msup>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> n = N_c e^{-(E_c - E_F)/kT}
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
> n
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
> <span className="mord,mathnormal" style="margin-right:0.109em;">
> 
> N
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.1514em;">
> <span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mathnormal,mtight">
> 
> c
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
> <span className="mopen,mtight">
> 
> (
> 
> </span>
> 
> <span className="mord,mtight">
> <span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">
> 
> E
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.1645em;">
> <span style="top:-2.357em;margin-left:-0.0576em;margin-right:0.0714em;">
> <span className="pstrut" style="height:2.5em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size3,size1,mtight">
> <span className="mord,mathnormal,mtight">
> 
> c
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
> <span className="mbin,mtight">
> 
> −
> 
> </span>
> 
> <span className="mord,mtight">
> <span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">
> 
> E
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3448em;">
> <span style="top:-2.3567em;margin-left:-0.0576em;margin-right:0.0714em;">
> <span className="pstrut" style="height:2.5em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size3,size1,mtight">
> <span className="mord,mathnormal,mtight" style="margin-right:0.1389em;">
> 
> F
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
> 
> <span className="mord,mtight">
> 
> /
> 
> </span>
> 
> <span className="mord,mathnormal,mtight" style="margin-right:0.0315em;">
> 
> k
> 
> </span>
> 
> <span className="mord,mathnormal,mtight" style="margin-right:0.1389em;">
> 
> T
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
> - <span className="katex">
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
> <mo>
> 
> =
> 
> </mo>
> 
> <msub>
> <mi>
> 
> n
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
> <msup>
> <mi>
> 
> e
> 
> </mi>
> 
> <mrow>
> <mo stretchy="false">
> 
> (
> 
> </mo>
> 
> <msub>
> <mi>
> 
> E
> 
> </mi>
> 
> <mi>
> 
> F
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
> <msub>
> <mi>
> 
> E
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
> <mo stretchy="false">
> 
> )
> 
> </mo>
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
> 
> <mi>
> 
> T
> 
> </mi>
> </mrow>
> </msup>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> n = n_i e^{(E_F - E_i)/kT}
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
> n
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
> <span className="mord,mathnormal">
> 
> n
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
> <span className="mopen,mtight">
> 
> (
> 
> </span>
> 
> <span className="mord,mtight">
> <span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">
> 
> E
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3448em;">
> <span style="top:-2.3567em;margin-left:-0.0576em;margin-right:0.0714em;">
> <span className="pstrut" style="height:2.5em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size3,size1,mtight">
> <span className="mord,mathnormal,mtight" style="margin-right:0.1389em;">
> 
> F
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
> <span className="mbin,mtight">
> 
> −
> 
> </span>
> 
> <span className="mord,mtight">
> <span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">
> 
> E
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3281em;">
> <span style="top:-2.357em;margin-left:-0.0576em;margin-right:0.0714em;">
> <span className="pstrut" style="height:2.5em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size3,size1,mtight">
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
> <span className="mclose,mtight">
> 
> )
> 
> </span>
> 
> <span className="mord,mtight">
> 
> /
> 
> </span>
> 
> <span className="mord,mathnormal,mtight" style="margin-right:0.0315em;">
> 
> k
> 
> </span>
> 
> <span className="mord,mathnormal,mtight" style="margin-right:0.1389em;">
> 
> T
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
> - <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <mi>
> 
> p
> 
> </mi>
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
> N
> 
> </mi>
> 
> <mi>
> 
> v
> 
> </mi>
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
> <mo stretchy="false">
> 
> (
> 
> </mo>
> 
> <msub>
> <mi>
> 
> E
> 
> </mi>
> 
> <mi>
> 
> F
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
> <msub>
> <mi>
> 
> E
> 
> </mi>
> 
> <mi>
> 
> v
> 
> </mi>
> </msub>
> 
> <mo stretchy="false">
> 
> )
> 
> </mo>
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
> 
> <mi>
> 
> T
> 
> </mi>
> </mrow>
> </msup>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> p = N_v e^{-(E_F - E_v)/kT}
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
> p
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
> <span className="mord,mathnormal" style="margin-right:0.109em;">
> 
> N
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.1514em;">
> <span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">
> 
> v
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
> <span className="mopen,mtight">
> 
> (
> 
> </span>
> 
> <span className="mord,mtight">
> <span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">
> 
> E
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3448em;">
> <span style="top:-2.3567em;margin-left:-0.0576em;margin-right:0.0714em;">
> <span className="pstrut" style="height:2.5em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size3,size1,mtight">
> <span className="mord,mathnormal,mtight" style="margin-right:0.1389em;">
> 
> F
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
> <span className="mbin,mtight">
> 
> −
> 
> </span>
> 
> <span className="mord,mtight">
> <span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">
> 
> E
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.1645em;">
> <span style="top:-2.357em;margin-left:-0.0576em;margin-right:0.0714em;">
> <span className="pstrut" style="height:2.5em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size3,size1,mtight">
> <span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">
> 
> v
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
> <span className="mclose,mtight">
> 
> )
> 
> </span>
> 
> <span className="mord,mtight">
> 
> /
> 
> </span>
> 
> <span className="mord,mathnormal,mtight" style="margin-right:0.0315em;">
> 
> k
> 
> </span>
> 
> <span className="mord,mathnormal,mtight" style="margin-right:0.1389em;">
> 
> T
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
> - <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <mi>
> 
> p
> 
> </mi>
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
> n
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
> <msup>
> <mi>
> 
> e
> 
> </mi>
> 
> <mrow>
> <mo stretchy="false">
> 
> (
> 
> </mo>
> 
> <msub>
> <mi>
> 
> E
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
> −
> 
> </mo>
> 
> <msub>
> <mi>
> 
> E
> 
> </mi>
> 
> <mi>
> 
> F
> 
> </mi>
> </msub>
> 
> <mo stretchy="false">
> 
> )
> 
> </mo>
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
> 
> <mi>
> 
> T
> 
> </mi>
> </mrow>
> </msup>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> p = n_i e^{(E_i - E_F)/kT}
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
> p
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
> <span className="mord,mathnormal">
> 
> n
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
> <span className="mopen,mtight">
> 
> (
> 
> </span>
> 
> <span className="mord,mtight">
> <span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">
> 
> E
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3281em;">
> <span style="top:-2.357em;margin-left:-0.0576em;margin-right:0.0714em;">
> <span className="pstrut" style="height:2.5em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size3,size1,mtight">
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
> <span className="mbin,mtight">
> 
> −
> 
> </span>
> 
> <span className="mord,mtight">
> <span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">
> 
> E
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3448em;">
> <span style="top:-2.3567em;margin-left:-0.0576em;margin-right:0.0714em;">
> <span className="pstrut" style="height:2.5em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size3,size1,mtight">
> <span className="mord,mathnormal,mtight" style="margin-right:0.1389em;">
> 
> F
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
> 
> <span className="mord,mtight">
> 
> /
> 
> </span>
> 
> <span className="mord,mathnormal,mtight" style="margin-right:0.0315em;">
> 
> k
> 
> </span>
> 
> <span className="mord,mathnormal,mtight" style="margin-right:0.1389em;">
> 
> T
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
> - <span className="katex">
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
> <mo>
> 
> =
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
> d
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
> <msub>
> <mi>
> 
> N
> 
> </mi>
> 
> <mi>
> 
> a
> 
> </mi>
> </msub>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> n = N_d - N_a
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
> n
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
> <span className="vlist" style="height:0.3361em;">
> <span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
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
> <span className="vlist" style="height:0.1514em;">
> <span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mathnormal,mtight">
> 
> a
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
> - <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <mi>
> 
> p
> 
> </mi>
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
> N
> 
> </mi>
> 
> <mi>
> 
> a
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
> <msub>
> <mi>
> 
> N
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
> p = N_a - N_d
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
> p
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
> <span className="vlist" style="height:0.1514em;">
> <span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mathnormal,mtight">
> 
> a
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
> <span className="vlist" style="height:0.3361em;">
> <span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
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
> - <span className="katex">
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
> p
> 
> </mi>
> 
> <mo>
> 
> =
> 
> </mo>
> 
> <msubsup>
> <mi>
> 
> n
> 
> </mi>
> 
> <mi>
> 
> i
> 
> </mi>
> 
> <mn>
> 
> 2
> 
> </mn>
> </msubsup>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> np = n_i^2
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
> p
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
> <span className="strut" style="height:1.0728em;vertical-align:-0.2587em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> <span className="mord,mathnormal">
> 
> n
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.8141em;">
> <span style="top:-2.4413em;margin-left:0em;margin-right:0.05em;">
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
> 
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
> 
> <span className="vlist-s">
> 
> ​
> 
> </span>
> </span>
> 
> <span className="vlist-r">
> <span className="vlist" style="height:0.2587em;">
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

## Carrier Actions in Semiconductor ｜ 半导体中载流子的行为

Three primary types of carrier action occur inside a semiconductor ｜ 三种载流子行为：

1. **Drift** ｜ 漂移：charged particle (带电粒子) motion under the influence of an **electric field**. ｜ **电场**作用产生漂移
2. **Diffusion** ｜ 扩散：particle motion due to **concentration gradient** or **temperature gradient**. ｜ **浓度梯度以及温度梯度**产生扩散
3. **Recombination–Generation** ｜ 复合–产生

### Effective Mass ｜ 有效质量

![Effective mass](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture3-09.webp)

左右两边的电子运动不同：真空中就直接用牛二，但是在半导体中，由于周期性晶格势的影响，电子的质量**需要等效为有效质量来看待**。

### Electron and Hole Effective Masses ｜ 电子、空穴有效质量

![Electron and hole effective masses](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture3-10.webp)

### Carrier Random Thermal Motion ｜ 载流子随机热运动

![Carrier random thermal motion](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture3-11.webp)

Electrons make frequent **collisions (撞击)** under different **scattering mechanisms (散射机制)**. **Frequency** of collision increases with increasing temperature.

电子始终以 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mo>

∼

</mo>

<msup>
<mn>

10

</mn>

<mn>

7

</mn>
</msup>

<mtext>



</mtext>

<mtext>

cm/s

</mtext>
</mrow>

<annotation encoding="application/x-tex">

\sim 10^7\,\text{cm/s}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.3669em;">



</span>

<span className="mrel">

∼

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

7

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

<span className="mord,text">
<span className="mord">

cm/s

</span>
</span>
</span>
</span>
</span>

 量级（at 300 K）做随机热运动，散射越频繁（温度越高）越"乱"；若施加外电场作用，只会产生一个很小的漂移偏置，这个偏置决定了宏观电流。

### Thermal Velocity ｜ 热运动速度

![Thermal velocity](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture3-12.webp)

> 这个速度就是单纯的**电子由于热激发引起的随机运动的速度**，和上面 <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msup>
> <mn>
> 
> 10
> 
> </mn>
> 
> <mn>
> 
> 7
> 
> </mn>
> </msup>
> 
> <mtext>
> 
> 
> 
> </mtext>
> 
> <mtext>
> 
> cm/s
> 
> </mtext>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> 10^7\,\text{cm/s}
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
> <span className="mord">
> 
> 1
> 
> </span>
> 
> <span className="mord">
> <span className="mord">
> 
> 0
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
> 7
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
> <span className="mspace" style="margin-right:0.1667em;">
> 
> 
> 
> </span>
> 
> <span className="mord,text">
> <span className="mord">
> 
> cm/s
> 
> </span>
> </span>
> </span>
> </span>
> </span>
> 
>  的量级对应一下。这个动能公式感觉也可以抄。

## Carrier Scattering ｜ 载流子散射

### Phonon Scattering ｜ 声子散射

![Phonon scattering](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture3-13.webp)

- Collision with vibrating lattice ｜ 与振动的晶格碰撞
- Phonons carry quantized energy of lattice vibration ｜ 声子携带晶格振动的量子化能量
- **Increases** with elevated temperature ｜ 温度升高，声子散射增加

> 温度升高，晶格振动加剧，声子散射应该会更强。

### Impurity Scattering ｜ 杂质散射

![Impurity scattering](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture3-14.webp)

- Deflection by ionized impurity atoms ｜ 电离杂质原子引起的偏转
- **Increases** with **increased impurity concentration** ｜ 杂质浓度增加，杂质散射增加
- **Decreases** with elevated temperature ｜ 温度升高，杂质散射反而减小了

> 这个可以这么理解：因为杂质散射是电离的杂质原子引起的偏转，当温度升高，电子运动速度变快，在相同力作用下更不容易被偏转（当然不一定严谨）。

同时对于杂质散射而言，正负离子作用相同，因此散射强度与掺杂浓度之和相关。

### Charge-charge Scattering ｜ 电荷-电荷散射

- Deflection due to Coulombic force between carriers ｜ 电子–电子、电子–空穴之间的库仑相互作用导致偏转
- Only significant **at high carrier concentrations** ｜ 只在高载流子浓度时显著，毕竟是载流子之间的散射
- Decreases with elevated temperature ｜ 温度升高，载流子散射反而减小了

> **温度升高，电子（或空穴）平均速度变快，与带电中心相互作用的时间更短，同样库仑力造成的偏转角更小**，因此**电离杂质散射**与**载流子–载流子散射**都会减弱。

**The net current in any direction is zero if no electric field is applied.**

> **无外电场**时只有**随机热运动**，各向平均为零，**任意方向的净电流都为 0**。
> 
> 要出现**定向电流**，必须有：
> 
> - **电场**（漂移：<span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msub>
> <mi>
> 
> v
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
> =
> 
> </mo>
> 
> <mi>
> 
> μ
> 
> </mi>
> 
> <mi>
> 
> E
> 
> </mi>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> v_d = \mu E
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:0.5806em;vertical-align:-0.15em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> <span className="mord,mathnormal" style="margin-right:0.0359em;">
> 
> v
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3361em;">
> <span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
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
> <span className="strut" style="height:0.8778em;vertical-align:-0.1944em;">
> 
> 
> 
> </span>
> 
> <span className="mord,mathnormal">
> 
> μ
> 
> </span>
> 
> <span className="mord,mathnormal" style="margin-right:0.0576em;">
> 
> E
> 
> </span>
> </span>
> </span>
> </span>
> 
> ）；或
> - **浓度/温度梯度**（扩散）。
> 
> 散射决定的是这种定向运动**能建立到多大**（即迁移率、扩散系数）。

## Carrier Drift ｜ 载流子漂移

![Carrier drift](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture3-15.webp)

![Carrier drift](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture3-16.webp)

当一个电场（例如，由于外部施加的电压）施加到半导体上时，可移动的载流子将被静电力加速。这个力**叠加**在电子的随机运动之上。

由于散射（scattering）的存在，半导体中的电子并不会获得恒定的加速度。然而，它们可以被视为以一个**恒定的平均漂移速度** <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

v

</mi>

<mi>

d

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

v_d

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.5806em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

v

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
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

 运动的准经典粒子。

- 电子在外加电场的**反方向**上漂移，从而形成电流。

> 电场与散射让随机热运动**产生了有偏置的"平均流动"**，这就是漂移电流。

## Mobility ｜ 迁移率

衡量在单位电场下，载流子（电子或空穴）运动的快慢 ｜ It quantifies the velocity of charge carriers (electrons or holes) under a unit electric field.

### Electron Mobility ｜ 电子迁移率

![Electron mobility](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture3-17.webp)

在每次碰撞之后，电子都会直接损失掉由于电场带来的动量，即 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msubsup>
<mi>

m

</mi>

<mi>

n

</mi>

<mo>

∗

</mo>
</msubsup>

<msub>
<mi>

v

</mi>

<mi>

d

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

m_n^* v_d

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9357em;vertical-align:-0.247em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

m

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.6887em;">
<span style="top:-2.453em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

n

</span>
</span>
</span>

<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mbin,mtight">

∗

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
<span className="mord,mathnormal" style="margin-right:0.0359em;">

v

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
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

；然后在两次碰撞之间，电子会从电场又得到动量，即 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mo stretchy="false">

(

</mo>

<mo>

−

</mo>

<mi>

q

</mi>

<mo stretchy="false">

)

</mo>

<mi>

E

</mi>

<msub>
<mi>

τ

</mi>

<mrow>
<mi>

m

</mi>

<mi>

n

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

(-q) E \tau_{mn}

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

−

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

q

</span>

<span className="mclose">

)

</span>

<span className="mord,mathnormal" style="margin-right:0.0576em;">

E

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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

mn

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

，这里的 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

τ

</mi>

<mrow>
<mi>

m

</mi>

<mi>

n

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

\tau_{mn}

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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

mn

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

 就是 mean free time（平均自由时间）。

我们让损失的动量和在电场中得到的动量相等，即 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msubsup>
<mi>

m

</mi>

<mi>

n

</mi>

<mo>

∗

</mo>
</msubsup>

<msub>
<mi>

v

</mi>

<mi>

d

</mi>
</msub>

<mo>

=

</mo>

<mo stretchy="false">

(

</mo>

<mo>

−

</mo>

<mi>

q

</mi>

<mo stretchy="false">

)

</mo>

<mi>

E

</mi>

<msub>
<mi>

τ

</mi>

<mrow>
<mi>

m

</mi>

<mi>

n

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

m_n^* v_d = (-q) E \tau_{mn}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9357em;vertical-align:-0.247em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

m

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.6887em;">
<span style="top:-2.453em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

n

</span>
</span>
</span>

<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mbin,mtight">

∗

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
<span className="mord,mathnormal" style="margin-right:0.0359em;">

v

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
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

<span className="mord">

−

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

q

</span>

<span className="mclose">

)

</span>

<span className="mord,mathnormal" style="margin-right:0.0576em;">

E

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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

mn

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

，解出

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi mathvariant="normal">

∣

</mi>

<msub>
<mi>

v

</mi>

<mi>

d

</mi>
</msub>

<mi mathvariant="normal">

∣

</mi>

<mo>

=

</mo>

<mfrac>
<mrow>
<mi>

q

</mi>

<mi>

E

</mi>

<msub>
<mi>

τ

</mi>

<mrow>
<mi>

m

</mi>

<mi>

n

</mi>
</mrow>
</msub>
</mrow>

<msubsup>
<mi>

m

</mi>

<mi>

n

</mi>

<mo>

∗

</mo>
</msubsup>
</mfrac>

<mo>

=

</mo>

<msub>
<mi>

μ

</mi>

<mi>

n

</mi>
</msub>

<mi>

E

</mi>
</mrow>

<annotation encoding="application/x-tex">

|v_d| = \frac{q E \tau_{mn}}{m_n^*} = \mu_n E

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
<span className="mord,mathnormal" style="margin-right:0.0359em;">

v

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
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
<span className="strut" style="height:2.2933em;vertical-align:-0.933em;">



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

m

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.6147em;">
<span style="top:-2.453em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

n

</span>
</span>
</span>

<span style="top:-2.989em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mbin,mtight">

∗

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

<span className="mord,mathnormal" style="margin-right:0.0576em;">

E

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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

mn

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



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
<span className="vlist" style="height:0.933em;">
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
<span className="strut" style="height:0.8778em;vertical-align:-0.1944em;">



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

<span className="mord,mathnormal" style="margin-right:0.0576em;">

E

</span>
</span>
</span>
</span>
</span>

于是，electron mobility 就定义为

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<msub>
<mi>

μ

</mi>

<mi>

n

</mi>
</msub>

<mo>

=

</mo>

<mfrac>
<mrow>
<mi>

q

</mi>

<msub>
<mi>

τ

</mi>

<mrow>
<mi>

m

</mi>

<mi>

n

</mi>
</mrow>
</msub>
</mrow>

<msubsup>
<mi>

m

</mi>

<mi>

n

</mi>

<mo>

∗

</mo>
</msubsup>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

\mu_n = \frac{q \tau_{mn}}{m_n^*}

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
<span className="strut" style="height:2.0406em;vertical-align:-0.933em;">



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

m

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.6147em;">
<span style="top:-2.453em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

n

</span>
</span>
</span>

<span style="top:-2.989em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mbin,mtight">

∗

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
<span className="mord,mathnormal,mtight">

mn

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



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
<span className="vlist" style="height:0.933em;">
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

![Electron mobility](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture3-18.webp)

### Hole Mobility ｜ 空穴迁移率

It's the same.

![Hole mobility](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture3-19.webp)

#### Summary

- Mean free time: <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

τ

</mi>
</mrow>

<annotation encoding="application/x-tex">

\tau

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.4306em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1132em;">

τ

</span>
</span>
</span>
</span>
- Mean free path: <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

λ

</mi>

<mo>

=

</mo>

<msub>
<mi>

v

</mi>

<mi>

t

</mi>
</msub>

<mo>

×

</mo>

<mi>

τ

</mi>
</mrow>

<annotation encoding="application/x-tex">

\lambda = v_t \times \tau

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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.7333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

v

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
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

<span className="mord,mathnormal" style="margin-right:0.1132em;">

τ

</span>
</span>
</span>
</span>

> 注意这里的速度是 thermal velocity。

![Mobility summary](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture3-20.webp)

![Mobility summary](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture3-21.webp)

## Matthiessen's Rule ｜ 马西森定则

该定则指出，材料的迁移率 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

μ

</mi>
</mrow>

<annotation encoding="application/x-tex">

\mu

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.625em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal">

μ

</span>
</span>
</span>
</span>

 的倒数等于由各种**独立**散射机制（如晶格振动和杂质）所引起的迁移率的倒数之和：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mfrac>
<mn>

1

</mn>

<msub>
<mi>

μ

</mi>

<mtext>

total

</mtext>
</msub>
</mfrac>

<mo>

=

</mo>

<mfrac>
<mn>

1

</mn>

<msub>
<mi>

μ

</mi>

<mtext>

lattice

</mtext>
</msub>
</mfrac>

<mo>

+

</mo>

<mfrac>
<mn>

1

</mn>

<msub>
<mi>

μ

</mi>

<mtext>

impurities

</mtext>
</msub>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

\frac{1}{\mu_{\text{total}}} = \frac{1}{\mu_{\text{lattice}}} + \frac{1}{\mu_{\text{impurities}}}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:2.2019em;vertical-align:-0.8804em;">



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

μ

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
<span className="mord,text,mtight">
<span className="mord,mtight">

total

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
<span className="strut" style="height:2.2019em;vertical-align:-0.8804em;">



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

μ

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
<span className="mord,text,mtight">
<span className="mord,mtight">

lattice

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
<span className="strut" style="height:2.2935em;vertical-align:-0.9721em;">



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

μ

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3175em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,text,mtight">
<span className="mord,mtight">

impurities

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
</span>
</span>
</span>
</span>

![Matthiessen's rule](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture3-22.webp)

Mechanism <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

i

</mi>
</mrow>

<annotation encoding="application/x-tex">

i

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6595em;">



</span>

<span className="mord,mathnormal">

i

</span>
</span>
</span>
</span>

：第 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

i

</mi>
</mrow>

<annotation encoding="application/x-tex">

i

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6595em;">



</span>

<span className="mord,mathnormal">

i

</span>
</span>
</span>
</span>

 种散射机制，也就是 phonon scattering、impurity scattering、charge-charge scattering 三者中的其中之一。

设第 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

i

</mi>
</mrow>

<annotation encoding="application/x-tex">

i

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6595em;">



</span>

<span className="mord,mathnormal">

i

</span>
</span>
</span>
</span>

 种散射机制的**平均时间间隔**为 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

τ

</mi>

<mi>

i

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

\tau_i

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
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.1132em;margin-right:0.05em;">
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

。在一个**很小**的时间片 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

d

</mi>

<mi>

t

</mi>
</mrow>

<annotation encoding="application/x-tex">

dt

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

<span className="mord,mathnormal">

t

</span>
</span>
</span>
</span>

 内，被这种机制散射的**概率** <span className="katex">
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

<mstyle scriptlevel="0" displaystyle="true">
<mfrac>
<mrow>
<mi>

d

</mi>

<mi>

t

</mi>
</mrow>

<msub>
<mi>

τ

</mi>

<mi>

i

</mi>
</msub>
</mfrac>
</mstyle>
</mrow>

<annotation encoding="application/x-tex">

P = \dfrac{dt}{\tau_i}

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
<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.1132em;">

τ

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.1132em;margin-right:0.05em;">
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

，<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mstyle scriptlevel="0" displaystyle="true">
<mfrac>
<mn>

1

</mn>

<msub>
<mi>

τ

</mi>

<mi>

i

</mi>
</msub>
</mfrac>
</mstyle>
</mrow>

<annotation encoding="application/x-tex">

\dfrac{1}{\tau_i}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:2.1574em;vertical-align:-0.836em;">



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
<span className="mord,mathnormal" style="margin-right:0.1132em;">

τ

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.1132em;margin-right:0.05em;">
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
</span>
</span>
</span>

 就是该机制的**散射率**（每秒发生的平均次数）。

如果散射机制之间彼此是独立的，那么 the probability that a carrier will be scattered within a time period <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

d

</mi>

<mi>

t

</mi>
</mrow>

<annotation encoding="application/x-tex">

dt

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

<span className="mord,mathnormal">

t

</span>
</span>
</span>
</span>

 is <span className="katex">
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

<mstyle scriptlevel="0" displaystyle="true">
<mfrac>
<mrow>
<mi>

d

</mi>

<mi>

t

</mi>
</mrow>

<msub>
<mi>

τ

</mi>

<mi>

i

</mi>
</msub>
</mfrac>
</mstyle>
</mrow>

<annotation encoding="application/x-tex">

\sum_i \dfrac{dt}{\tau_i}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:2.2074em;vertical-align:-0.836em;">



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
<span className="mord,mathnormal" style="margin-right:0.1132em;">

τ

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.1132em;margin-right:0.05em;">
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

，也就是把各种散射机制 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

i

</mi>
</mrow>

<annotation encoding="application/x-tex">

i

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6595em;">



</span>

<span className="mord,mathnormal">

i

</span>
</span>
</span>
</span>

 都加到一起。

### Superposition Law ｜ 叠加定律

![Superposition law](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture3-23.webp)

其实就是上面推导的等价：直接加起来 phonon scattering 和 impurity scattering。猜测不加 charge-charge scattering 的原因就是它本身的性质（only significant **at high carrier concentrations**）；还有就是 Matthiessen 只把"真正在体系外耗散动量"的散射相加，C-C 散射应该是动量在载流子之间相互传递。

![Mobility vs doping](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture3-24.webp)

> 掺杂浓度 <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msub>
> <mi>
> 
> N
> 
> </mi>
> 
> <mi>
> 
> a
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
> N
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
> N_a + N_d
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
> N
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.1514em;">
> <span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mathnormal,mtight">
> 
> a
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
> <span className="mord,mathnormal" style="margin-right:0.109em;">
> 
> N
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3361em;">
> <span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
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
>  升高，mobility 下降。

![Mobility vs temperature](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture3-25.webp)

直接就是散射的应用了。回顾一下，对于 **impurity scattering，温度低反而更强了**，所以当重掺杂时，低温下杂质散射明显，曲线就在低温时弯下去了；轻掺杂时，主导的还是 phonon scattering，温度升高，mobility 降低。

## Velocity Saturation ｜ 速度饱和

![Velocity saturation](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture3-26.webp)

当载流子的动能超过一个临界值时，它会产生一个**光学声子 (optical phonon)** 并失去**动能 (kinetic energy)**。

因此，动能在较大的 <span className="katex">
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

 时达到上限，速度不会超过饱和速度 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

v

</mi>

<mtext>

sat

</mtext>
</msub>
</mrow>

<annotation encoding="application/x-tex">

v_{\text{sat}}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.5806em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

v

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
<span className="mord,text,mtight">
<span className="mord,mtight">

sat

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

。

**Velocity saturation** has a **deleterious (不利的)** effect on device speed as in **nanoscale (纳米级)** transistors.

## Summary ｜ 小结

> **Carrier mobility varies with doping**
> 
> Decreases with increasing total concentration of ionized dopants.
> 
> **Carrier mobility varies with temperature**
> 
> Decreases with increasing <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <mi>
> 
> T
> 
> </mi>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> T
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
> T
> 
> </span>
> </span>
> </span>
> </span>
> 
>  if lattice scattering is dominant.
> 
> Decreases with decreasing <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <mi>
> 
> T
> 
> </mi>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> T
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
> T
> 
> </span>
> </span>
> </span>
> </span>
> 
>  if impurity scattering is dominant.

总结一下，其实就是上面一样的内容。
