# Lecture 5：PN 结与耗尽区

> PN 结的制备与理想模型、电荷密度与泊松方程、耗尽近似、内建电势、电容电压特性、反向偏置与击穿（隧穿击穿、雪崩击穿）

## PN Junction

### PN Junction Fabricate

将P型杂质扩散到均匀掺杂的N型衬底

![Mz7XbnsOzoRr72xJ1TxcWgHznQh.png](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture5-21.webp)

### Ideal PN Junction | 理想PN结

#### Step (Abrupt) Junctions | 陡变结

分布近似于虚线所示

![Yw5eb1qo7oMYa6xDNwTcGpqvnfI.png](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture5-22.webp)

#### Graded (Linear) Junction | 线性结

![J0jtbJEAno9OXpxjojZceIRenXc.png](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture5-23.webp)

### Electrical Characteristics ｜ 电学特性

#### Charge Density in a Semiconductor ｜ 电荷密度

Assuming the dopants are completely ionized,then the **net charge density is:**

> 事实上静电荷数密度是 (p+ND)−(n+NA)

#### Gauss's Law & Poission's Equation

![BGBwbdw78ozEoTxfOiVcVXvQnBZ.png](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture5-25.webp)

> 这里注意 <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msub>
> <mi>
> 
> ϵ
> 
> </mi>
> 
> <mrow>
> <mi>
> 
> S
> 
> </mi>
> 
> <mi>
> 
> i
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
> <mn>
> 
> 12
> 
> </mn>
> 
> <msub>
> <mi>
> 
> ϵ
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
> ϵ_{Si}=12ϵ_0
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
> <span className="mord,mathnormal">
> 
> ϵ
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3283em;">
> <span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mtight">
> <span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">
> 
> S
> 
> </span>
> 
> <span className="mord,mathnormal,mtight">
> 
> i
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
> <span className="strut" style="height:0.7944em;vertical-align:-0.15em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> 
> 12
> 
> </span>
> 
> <span className="mord">
> <span className="mord,mathnormal">
> 
> ϵ
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
> ,以及高斯定理和泊松方程

#### Energy Band Diagram ｜ 能带图

![RY3sbUaWhoVIo3xLPqycfvYMnzh.png](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture5-06.webp)

1. Ef is constant at equilibrium and Ec,Ev are known relative to Ef

> 热平衡时费米能级 <span className="katex">
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
>  必须是常数
> 
> <span className="katex">
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
> <mo stretchy="false">
> 
> (
> 
> </mo>
> 
> <mi>
> 
> x
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
> <mfrac>
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
> <mo stretchy="false">
> 
> (
> 
> </mo>
> 
> <mi>
> 
> x
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
> </mrow>
> 
> <mrow>
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
> </mfrac>
> </mrow>
> </msup>
> 
> <mo separator="true">
> 
> ,
> 
> </mo>
> 
> <mspace width="1em">
> 
> 
> 
> </mspace>
> 
> <mi>
> 
> p
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
> x
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
> <mfrac>
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
> (
> 
> </mo>
> 
> <mi>
> 
> x
> 
> </mi>
> 
> <mo stretchy="false">
> 
> )
> 
> </mo>
> </mrow>
> 
> <mrow>
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
> </mfrac>
> </mrow>
> </msup>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> n(x) = N_c e^{-\frac{E_c(x) - E_F}{kT}}, \quad p(x) = N_v e^{-\frac{E_F - E_v(x)}{kT}}
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
> n
> 
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
> x
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
> <span className="strut" style="height:1.3837em;vertical-align:-0.25em;">
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
> <span className="vlist" style="height:1.1337em;">
> <span style="top:-3.363em;margin-right:0.05em;">
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
> −
> 
> </span>
> 
> <span className="mord,mtight">
> <span className="mopen,nulldelimiter,sizing,reset-size3,size6">
> 
> 
> 
> </span>
> 
> <span className="mfrac">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:1.101em;">
> <span style="top:-2.656em;">
> <span className="pstrut" style="height:3em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size3,size1,mtight">
> <span className="mord,mtight">
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
> 
> <span style="top:-3.2255em;">
> <span className="pstrut" style="height:3em;">
> 
> 
> 
> </span>
> 
> <span className="frac-line,mtight" style="border-bottom-width:0.049em;">
> 
> 
> 
> </span>
> </span>
> 
> <span style="top:-3.5653em;">
> <span className="pstrut" style="height:3em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size3,size1,mtight">
> <span className="mord,mtight">
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
> <span className="vlist" style="height:0.2306em;">
> <span style="top:-2.3em;margin-left:-0.0576em;margin-right:0.1em;">
> <span className="pstrut" style="height:2.5em;">
> 
> 
> 
> </span>
> 
> <span className="mord,mathnormal,mtight">
> 
> c
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
> <span className="vlist" style="height:0.2em;">
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
> <span className="mopen,mtight">
> 
> (
> 
> </span>
> 
> <span className="mord,mathnormal,mtight">
> 
> x
> 
> </span>
> 
> <span className="mclose,mtight">
> 
> )
> 
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
> <span style="top:-2.3448em;margin-left:-0.0576em;margin-right:0.1em;">
> <span className="pstrut" style="height:2.6833em;">
> 
> 
> 
> </span>
> 
> <span className="mord,mathnormal,mtight" style="margin-right:0.1389em;">
> 
> F
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
> <span className="vlist" style="height:0.3385em;">
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
> <span className="vlist" style="height:0.344em;">
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
> <span className="mclose,nulldelimiter,sizing,reset-size3,size6">
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
> <span className="mpunct">
> 
> ,
> 
> </span>
> 
> <span className="mspace" style="margin-right:1em;">
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
> <span className="mord,mathnormal">
> 
> p
> 
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
> x
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
> <span className="strut" style="height:1.2837em;vertical-align:-0.15em;">
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
> <span className="vlist" style="height:1.1337em;">
> <span style="top:-3.363em;margin-right:0.05em;">
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
> −
> 
> </span>
> 
> <span className="mord,mtight">
> <span className="mopen,nulldelimiter,sizing,reset-size3,size6">
> 
> 
> 
> </span>
> 
> <span className="mfrac">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:1.101em;">
> <span style="top:-2.656em;">
> <span className="pstrut" style="height:3em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size3,size1,mtight">
> <span className="mord,mtight">
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
> 
> <span style="top:-3.2255em;">
> <span className="pstrut" style="height:3em;">
> 
> 
> 
> </span>
> 
> <span className="frac-line,mtight" style="border-bottom-width:0.049em;">
> 
> 
> 
> </span>
> </span>
> 
> <span style="top:-3.5653em;">
> <span className="pstrut" style="height:3em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size3,size1,mtight">
> <span className="mord,mtight">
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
> <span style="top:-2.3448em;margin-left:-0.0576em;margin-right:0.1em;">
> <span className="pstrut" style="height:2.6833em;">
> 
> 
> 
> </span>
> 
> <span className="mord,mathnormal,mtight" style="margin-right:0.1389em;">
> 
> F
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
> <span className="vlist" style="height:0.3385em;">
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
> <span className="vlist" style="height:0.2306em;">
> <span style="top:-2.3em;margin-left:-0.0576em;margin-right:0.1em;">
> <span className="pstrut" style="height:2.5em;">
> 
> 
> 
> </span>
> 
> <span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">
> 
> v
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
> <span className="vlist" style="height:0.2em;">
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
> <span className="mopen,mtight">
> 
> (
> 
> </span>
> 
> <span className="mord,mathnormal,mtight">
> 
> x
> 
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
> 
> <span className="vlist-s">
> 
> ​
> 
> </span>
> </span>
> 
> <span className="vlist-r">
> <span className="vlist" style="height:0.344em;">
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
> <span className="mclose,nulldelimiter,sizing,reset-size3,size6">
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
> 
> ，由玻尔兹曼近似就可以算出不同位置x的电子or空穴浓度
> 
> 所以**哪边** <span className="katex">
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
>  **更低（更靠近** <span className="katex">
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
> **）哪边就更 n 型；哪边** <span className="katex">
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
>  **更高哪边就更 p 型**

1. Ec and Ev are smooth , the exact shape to be determined
2. A depletion lay exists at the PN junction where n≈0 and p≈0

The built-in potential is generated due to **band bending**.

![OWJCb5THpoSR0ex1Uq9c5vDUn0M.png](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture5-03.webp)

<alert type="question">

**Question: Can** the built-in potential be measured with a voltmeter?

**不可以。**使用一个标准的电压表直接测量PN结的内建电势 (Vbi)，读数将为0伏特。

1. 产生新的接触电势
当电压表的金属探针接触P型区和N型区时，会在“金属-P型”和“金属-N型”的界面上形成两个新的接触电势 (Contact Potentials)。
2. 热平衡抵消
电压表、探针和PN结形成一个完整的闭合回路。在热平衡状态下（无电流流过），此回路中所有电势差的总和必须为零。
  - <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <msub>
  <mi>
  
  V
  
  </mi>
  
  <mtext>
  
  测量值
  
  </mtext>
  </msub>
  
  <mo>
  
  +
  
  </mo>
  
  <msub>
  <mi>
  
  V
  
  </mi>
  
  <mrow>
  <mtext>
  
  金属
  
  </mtext>
  
  <mo>
  
  −
  
  </mo>
  
  <mi>
  
  P
  
  </mi>
  </mrow>
  </msub>
  
  <mo>
  
  +
  
  </mo>
  
  <msub>
  <mi>
  
  V
  
  </mi>
  
  <mrow>
  <mi>
  
  P
  
  </mi>
  
  <mo>
  
  −
  
  </mo>
  
  <mi>
  
  N
  
  </mi>
  </mrow>
  </msub>
  
  <mo>
  
  +
  
  </mo>
  
  <msub>
  <mi>
  
  V
  
  </mi>
  
  <mrow>
  <mi>
  
  N
  
  </mi>
  
  <mo>
  
  −
  
  </mo>
  
  <mtext>
  
  金属
  
  </mtext>
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
  
  V_{测量值}+V_{金属-P}+V_{P-N}+V_{N-金属}=0
  
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
  <span className="mord,cjk_fallback,mtight">
  
  测量值
  
  </span>
  </span>
  </span>
  </span>
  </span>
  
  <span className="vlist-s">
  
  ​
  
  </span>
  </span>
  
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
  <span className="strut" style="height:0.8917em;vertical-align:-0.2083em;">
  
  
  
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
  <span className="mord,cjk_fallback,mtight">
  
  金属
  
  </span>
  
  <span className="mbin,mtight">
  
  −
  
  </span>
  
  <span className="mord,mathnormal,mtight" style="margin-right:0.1389em;">
  
  P
  
  </span>
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
  
  <span className="mspace" style="margin-right:0.2222em;">
  
  
  
  </span>
  
  <span className="mbin">
  
  +
  
  </span>
  
  <span className="mspace" style="margin-right:0.2222em;">
  
  
  
  </span>
  </span>
  
  <span className="base">
  <span className="strut" style="height:0.8917em;vertical-align:-0.2083em;">
  
  
  
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
  <span className="mord,mathnormal,mtight" style="margin-right:0.1389em;">
  
  P
  
  </span>
  
  <span className="mbin,mtight">
  
  −
  
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
  <span className="vlist" style="height:0.2083em;">
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
  <span className="strut" style="height:0.8917em;vertical-align:-0.2083em;">
  
  
  
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
  <span className="mord,mathnormal,mtight" style="margin-right:0.109em;">
  
  N
  
  </span>
  
  <span className="mbin,mtight">
  
  −
  
  </span>
  
  <span className="mord,cjk_fallback,mtight">
  
  金属
  
  </span>
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
  - 其中 <span className="katex">
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
  
  P
  
  </mi>
  
  <mo>
  
  −
  
  </mo>
  
  <mi>
  
  N
  
  </mi>
  </mrow>
  </msub>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  V_{P-N}
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:0.8917em;vertical-align:-0.2083em;">
  
  
  
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
  <span className="mord,mathnormal,mtight" style="margin-right:0.1389em;">
  
  P
  
  </span>
  
  <span className="mbin,mtight">
  
  −
  
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
  <span className="vlist" style="height:0.2083em;">
  <span>
  
  
  
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  
   就是内建电势 <span className="katex">
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
  
  。
3. 物理规律决定了新产生的两个接触电势（V金属-P 和 VN-金属）与内建电势 Vbi **恰好完全相互抵消**。

- 费米能级解释
电压表测量的是其两探针之间的费米能级 (EF) 之差。在热平衡状态下，整个闭合回路的费米能级处处相等（为一条平线）。因此，两探针间的费米能级之差为零，电压表读数即为零。

只能通过**间接方法**（如C-V电容-电压特性测量法）来推算得出。

</alert>

#### Quantitative Analysis ｜ 定量分析

##### Depletion Approximation

<alert type="tip">

**Depletion approximation | 耗尽区近似**

a. 耗尽区内没有可移动的电子和空穴；b. 耗尽区外假设为中性，净电荷浓度为0；

1. **Inside the Depletion Region:** It assumes there are **no** mobile electrons or holes (n=0, p=0). The charge consists **only** of fixed donor (<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msubsup>
<mi>

N

</mi>

<mi>

D

</mi>

<mo>

+

</mo>
</msubsup>
</mrow>

<annotation encoding="application/x-tex">

N_D^+

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.105em;vertical-align:-0.2935em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.109em;">

N

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.8115em;">
<span style="top:-2.4065em;margin-left:-0.109em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

D

</span>
</span>
</span>

<span style="top:-3.1031em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mbin,mtight">

+

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.2935em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

) and acceptor (<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msubsup>
<mi>

N

</mi>

<mi>

A

</mi>

<mo>

−

</mo>
</msubsup>
</mrow>

<annotation encoding="application/x-tex">

N_A^-

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.105em;vertical-align:-0.2935em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.109em;">

N

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.8115em;">
<span style="top:-2.4065em;margin-left:-0.109em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

A

</span>
</span>
</span>

<span style="top:-3.1031em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mbin,mtight">

−

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.2935em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

) ions.
2. **Outside the Depletion Region (Neutral Region):** It assumes the region is **perfectly neutral**, meaning the net charge density is zero (<span className="katex">
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

0

</mn>
</mrow>

<annotation encoding="application/x-tex">

\rho=0

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

0

</span>
</span>
</span>
</span>

).

</alert>

##### Built-in Potential <span className="katex">
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



**Non-degenerately doped | 非简并掺杂**

指半导体中**中等或轻度**的掺杂水平，掺杂浓度不足以使费米能级 (<span className="katex">
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

) 进入导带 (<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

E

</mi>

<mi>

C

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

E_C

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

) 或价带 (<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

E

</mi>

<mi>

V

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

E_V

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
<span className="mord,mathnormal,mtight" style="margin-right:0.2222em;">

V

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

)。费米能级**始终位于禁带之内**。

Refers to a **moderate or light** doping level in semiconductors, where the doping concentration is not sufficient to shift the Fermi level (<span className="katex">
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

) into the conduction band (<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

E

</mi>

<mi>

C

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

E_C

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

) or the valence band (<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

E

</mi>

<mi>

V

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

E_V

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
<span className="mord,mathnormal,mtight" style="margin-right:0.2222em;">

V

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

). The Fermi level remains within the band gap at all times.

![FisAbXuX0ooF3vxFjIhcYm3Znmd.png](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture5-13.webp)

Then we can get the value of <span className="katex">
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

**(前提是非简并材料 non-degenerately doped):**

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

=

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

e

</mi>
</mfrac>

<mi>

ln

</mi>

<mo>

⁡

</mo>

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

A

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
</mfrac>

<mo fence="true">

)

</mo>
</mrow>
</mrow>

<annotation encoding="application/x-tex">

V_{bi} = \frac{kT}{e}\ln\left(\frac{N_A N_D}{n_i^2}\right)

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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:2.4129em;vertical-align:-0.9629em;">



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

n

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.7959em;">
<span style="top:-2.4231em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

i

</span>
</span>
</span>

<span style="top:-3.0448em;margin-right:0.05em;">
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
<span className="vlist" style="height:0.2769em;">
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

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.9629em;">
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

##### <span className="katex">
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

 for Abrupt PN Junctions

<mark>

**The heavy doping side pretty much determine the**

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

 <mark>

**| 重掺杂这一边决定了**

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

<mark>

**和电场的大小**

</mark>



![LdKlbEtk4oVJdVxVhwDci1plnhe.png](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture5-02.webp)

##### Calculation of E(x) V(x)

![AlAmbzqq5oqIuPxLnHOczG0dnCe.png](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture5-17.webp)

**The electric field is continuous at x= 0**

电场是连续不光滑函数，电势是连续且光滑的函数

对电场进行积分可以得到(此处令 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

V

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

=

</mo>

<mn>

0

</mn>
</mrow>

<annotation encoding="application/x-tex">

V(-x_p) = 0

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.0361em;vertical-align:-0.2861em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.2222em;">

V

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
<span className="strut" style="height:0.6444em;">



</span>

<span className="mord">

0

</span>
</span>
</span>
</span>

 作为0电势参考点)

1. On the P side:

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

V

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

−

</mo>

<mn>

0

</mn>

<mo>

=

</mo>

<mo>

−

</mo>

<msubsup>
<mo>

∫

</mo>

<mrow>
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

<mn>

0

</mn>
</msubsup>

<mi>

E

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

<mi>

d

</mi>

<mi>

x

</mi>

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

N

</mi>

<mi>

A

</mi>
</msub>
</mrow>

<mrow>
<mn>

2

</mn>

<msub>
<mi>

ε

</mi>

<mi>

s

</mi>
</msub>
</mrow>
</mfrac>

<mo stretchy="false">

(

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

+

</mo>

<mi>

x

</mi>

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

V(x) - 0 = -\int_{-x_p}^{0} E(x)dx = \frac{qN_A}{2\varepsilon_s}(x_p + x)^2

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.2222em;">

V

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
</span>

<span className="base">
<span className="strut" style="height:0.6444em;">



</span>

<span className="mord">

0

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:2.6733em;vertical-align:-1.1093em;">



</span>

<span className="mord">

−

</span>

<span className="mspace" style="margin-right:0.1667em;">



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

<span style="top:-3.8129em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
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
<span className="vlist" style="height:1.1093em;">
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

E

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

<span className="mord,mathnormal">

d

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

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.1141em;vertical-align:-0.25em;">



</span>

<span className="mord,mathnormal">

x

</span>

<span className="mclose">
<span className="mclose">

)

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

1. On the N side :

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

<mi>

V

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

<mo>

−

</mo>

<msubsup>
<mo>

∫

</mo>

<msub>
<mi>

x

</mi>

<mi>

n

</mi>
</msub>

<mn>

0

</mn>
</msubsup>

<mi>

E

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

<mi>

d

</mi>

<mi>

x

</mi>

<mspace linebreak="newline">



</mspace>

<mi>

V

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

D

</mi>
</msub>
</mrow>

<mrow>
<mn>

2

</mn>

<msub>
<mi>

ε

</mi>

<mi>

s

</mi>
</msub>
</mrow>
</mfrac>

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

<mi>

x

</mi>

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

V_{bi} - V(x) = -\int_{x_n}^{0}E(x)dx \\ V(x) =V_{bi} - \frac{qN_D}{2\varepsilon_s}(x_n - x)^2

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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.2222em;">

V

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
<span className="strut" style="height:2.5761em;vertical-align:-1.012em;">



</span>

<span className="mord">

−

</span>

<span className="mspace" style="margin-right:0.1667em;">



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

<span style="top:-3.8129em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
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
<span className="vlist" style="height:1.012em;">
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

E

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

<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal">

x

</span>
</span>

<span className="mspace,newline">



</span>

<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.2222em;">

V

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

<span className="mord,mathnormal">

x

</span>

<span className="mclose">
<span className="mclose">

)

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

也可以得到<span className="katex">
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

=

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
</mrow>

<mrow>
<mn>

2

</mn>

<msub>
<mi>

ε

</mi>

<mi>

s

</mi>
</msub>
</mrow>
</mfrac>

<mo stretchy="false">

(

</mo>

<msubsup>
<mi>

x

</mi>

<mi>

p

</mi>

<mn>

2

</mn>
</msubsup>

<mo>

+

</mo>

<msubsup>
<mi>

x

</mi>

<mi>

n

</mi>

<mn>

2

</mn>
</msubsup>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

V_{bi} =\frac{qN_A}{2\varepsilon_s}(x_p^2 + x_n^2)

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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.3695em;vertical-align:-0.4451em;">



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

2

</span>

<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

ε

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

<span style="top:-3.4461em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

q

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
<span className="vlist" style="height:0.8141em;">
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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.0641em;vertical-align:-0.25em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

x

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.8141em;">
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

<span className="mclose">

)

</span>
</span>
</span>
</span>

同时有<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

W

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

<mo>

+

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

<annotation encoding="application/x-tex">

W = x_n + x_p

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

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



得到如下一系列公式

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

W

</mi>

<mo>

=

</mo>

<msqrt>
<mrow>
<mfrac>
<mrow>
<mn>

2

</mn>

<msub>
<mi>

ε

</mi>

<mi>

s

</mi>
</msub>

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

<mi>

q

</mi>
</mfrac>

<mrow>
<mo fence="true">

(

</mo>

<mfrac>
<mn>

1

</mn>

<msub>
<mi>

N

</mi>

<mi>

A

</mi>
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

N

</mi>

<mi>

D

</mi>
</msub>
</mfrac>

<mo fence="true">

)

</mo>
</mrow>
</mrow>
</msqrt>
</mrow>

<annotation encoding="application/x-tex">

W = \sqrt{\frac{2\varepsilon_sV_{bi}}{q}\left(\frac{1}{N_A} + \frac{1}{N_D} \right)}

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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:3.04em;vertical-align:-1.1561em;">



</span>

<span className="mord,sqrt">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:1.8839em;">
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
<span className="vlist" style="height:1.3603em;">
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

2

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
<span className="vlist" style="height:1.3214em;">
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

<span className="mclose,delimcenter" style="top:0em;">
<span className="delimsizing,size3">

)

</span>
</span>
</span>
</span>
</span>

<span style="top:-3.8439em;">
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
<span className="vlist" style="height:1.1561em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

![H1DUbVMEsosHNrxYaZncDIvfndh.png](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture5-19.webp)

> **Question: 如果想要制造一个耐高压的器件（high voltage device），应该如何设计？**
> 
> **Answer:**
> 
> To design a high-voltage **abrupt PN junction,** the key is to have **one side heavily doped** (e.g., P+) and the other side **very lightly doped** (e.g., an N- drift region).
> 
> This way, under reverse bias, the depletion layer (W) extends almost entirely into this lightly doped side.
> 
> A very low doping concentration (N_) allows the depletion region to become very wide, supporting a large voltage (V_) before the internal electric field reaches the critical breakdown field (E_).

> 要设计一个耐高压的突变PN结器件，关键是使其一侧重掺杂（例如P+），而另一侧极轻掺杂（例如N-漂移区），而不是使用“本征掺杂”。
> 
> 这样，在反向偏压下，耗尽层（W）会几乎完全延伸到这个轻掺杂区。
> 
> 极低的掺杂浓度 (N_) 会使耗尽层变得非常宽，从而在内部电场达到临界击穿场强（E_）之前，器件可以承受非常高的电压（V_）。

![RnIAbcIvToWfXwxo6rLcNKB5nie.png](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture5-08.webp)

> 不过我觉得除非题目条件没给，不然最好不要用<span className="katex">
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
> b
> 
> </mi>
> 
> <mi>
> 
> i
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
> <mrow>
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
> 
> <mi>
> 
> q
> 
> </mi>
> </mfrac>
> 
> <mi>
> 
> l
> 
> </mi>
> 
> <mi>
> 
> n
> 
> </mi>
> 
> <mrow>
> <mo fence="true">
> 
> (
> 
> </mo>
> 
> <mfrac>
> <msup>
> <mi>
> 
> N
> 
> </mi>
> 
> <msup>
> <mrow>
> 
> 
> 
> </mrow>
> 
> <mo mathvariant="normal" lspace="0em" rspace="0em">
> 
> ′
> 
> </mo>
> </msup>
> </msup>
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
> </mfrac>
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
> V_{bi} = \frac{kT}{q}ln\left( \frac{N^{'}}{n_i}\right)
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
> bi
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
> <span className="strut" style="height:1.8255em;vertical-align:-0.65em;">
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
> <span className="vlist" style="height:0.8801em;">
> <span style="top:-2.655em;">
> <span className="pstrut" style="height:3em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mtight">
> <span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">
> 
> q
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
> 
> <span className="vlist-s">
> 
> ​
> 
> </span>
> </span>
> 
> <span className="vlist-r">
> <span className="vlist" style="height:0.4811em;">
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
> <span className="mord,mathnormal" style="margin-right:0.0197em;">
> 
> l
> 
> </span>
> 
> <span className="mord,mathnormal">
> 
> n
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
> <span className="delimsizing,size2">
> 
> (
> 
> </span>
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
> <span className="vlist" style="height:1.1755em;">
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
> n
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3281em;">
> <span style="top:-2.357em;margin-left:0em;margin-right:0.0714em;">
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
> <span className="mord,mathnormal,mtight" style="margin-right:0.109em;">
> 
> N
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t">
> <span className="vlist-r">
> <span className="vlist" style="height:1.1164em;">
> <span style="top:-3.1164em;margin-right:0.0714em;">
> <span className="pstrut" style="height:2.6854em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size3,size1,mtight">
> <span className="mord,mtight">
> <span className="mord,mtight">
> <span>
> 
> 
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t">
> <span className="vlist-r">
> <span className="vlist" style="height:0.9596em;">
> <span style="top:-2.9596em;margin-right:0.1em;">
> <span className="pstrut" style="height:2.5556em;">
> 
> 
> 
> </span>
> 
> <span className="mord,mtight">
> <span className="mord,mtight">
> 
> ′
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
> <span className="vlist" style="height:0.4451em;">
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
> <span className="mclose,delimcenter" style="top:0em;">
> <span className="delimsizing,size2">
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
> , 因为近似感觉不太合理

<mark>

对于

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

 <mark>

而言，对于它影响的主要因素是

</mark>

<mark>

**高掺杂杂质浓度**

</mark>

<mark>

；而对于耗尽区宽度 W而言，它的主导因素是

</mark>

<mark>

**低掺杂杂质浓度**

</mark>



##### Examples ｜ 例题

![Da9VbeJZfoZ1nAxiVkSctEsNnQf.png](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture5-20.webp)

##### Net doping Concentration

通常，集成电路（IC）器件中的P-N结是通过**补偿掺杂（counter-doping）**形成的

![GrTUbzleHoQEw1xiNSacdcSinqU.png](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture5-01.webp)

##### Reverse -Biased PN Junction

> **Question:**为什么光电传感器（photo detector）一般工作在反向偏置状态?
> 
> ![FLJkbwYM6oGXIWxeGghc8dA6nsg.png](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture5-09.webp)
> 
> 1. 反向偏置使**耗尽层更宽**，这增大了有效的光吸收区域，从而能**产生并收集更多的光生载流子**。
> 2. 器件本身的反向偏置电流（即**暗电流**）非常小，因此，由光生电子-空穴对引起的**额外电流变化会非常显著**，易于检测。
> 3. Reverse bias creates a **wider depletion layer**, which increases the effective light absorption region, thus **generating and collecting more photogenerated carriers**.
> 4. The device's own reverse bias current (i.e., **dark current**) is very small, so the **additional current change** caused by photogenerated electron-hole pairs becomes **very significant** and easy to detect.

![UKtTbhAUmoeTVNx3JTfcpEK7n7b.png](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture5-12.webp)

随着反向偏置电压增加，耗尽区宽度**增加(widen)**-> 这就导致了电容效应

#### Capacitance -Voltage Characteristics | 电容电压特性

##### Depletion Capacitance ｜ 耗尽电容

反偏PN结（Reverse-biased Junction）的电容主要是由**耗尽****电容**主导的

![Fo7nb3PB3ovlKHx5amccKwoFnvc.png](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture5-11.webp)

##### 利用图像测量参数

![RSPTbpCyXoXqHJxmXvwcOHOJndo.png](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture5-10.webp)

> **Light doping concentration approximately  less than** <span className="katex">
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
> 16
> 
> </mn>
> </msup>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> 10^{16}
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
> <span className="mord,mtight">
> 
> 16
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
> 
> 
> **Heavy doping concentration approximately  larger than** <span className="katex">
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
> <mrow>
> <mn>
> 
> 17
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
> <mn>
> 
> 18
> 
> </mn>
> </mrow>
> </msup>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> 10^{17 \space or  \space 18}
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
> <span className="mord,mtight">
> 
> 17
> 
> </span>
> 
> <span className="mspace,mtight">
> <span className="mtight">
> 
> 
> 
> </span>
> </span>
> 
> <span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">
> 
> or
> 
> </span>
> 
> <span className="mspace,mtight">
> <span className="mtight">
> 
> 
> 
> </span>
> </span>
> 
> <span className="mord,mtight">
> 
> 18
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
> 
> 
> ![A5DA94BB-9657-4BA1-ADC0-AB74C6D52AD1.png](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture5-16.webp)

##### Example ｜ 例题

![C4esbmMmtotKIoxdwRPc6hatnAc.png](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture5-07.webp)

> **Answer:**
> 
> **Chinese Version**
> 
> 1. 测量 N_l (轻掺杂): 非常准确。N_l 是根据 1/C^2 曲线的斜率 (Slope) 算出的。C-V法对轻掺杂一侧的浓度非常敏感，这是业界用于测量 N_l 的标准方法。
> 2. 测量 N_h (重掺杂): 非常不准确。N_h 是根据截距 (V_) 反推的。由于 V_ 与 N_h 呈对数 (\ln) 关系（V_ \propto \ln(N_h)），V_ 对 N_h 的巨大变化并不敏感。反之，测量 V_ 时的微小误差，在通过指数 (e^x) 运算反推 N_h 时会被指数级放大，导致结果严重失准。
> 
> **English Version**
> 
> 1. Determining N_l (lighter doping): Very Accurate.N_l is calculated from the slope of the 1/C^2 plot. The C-V method is very sensitive to the lighter doping concentration and is the standard way to measure it.
> 2. Determining N_h (heavier doping): Very Inaccurate. N_h is extracted from the intercept (V_). Because V_ has only a logarithmic (\ln) dependence on N_h (V_ \propto \ln(N_h)), V_ is very insensitive to large changes in N_h. Conversely, small measurement errors in V_ are exponentially (e^x) amplified when solving for N_h, leading to highly inaccurate results.

### PN Junction Break Down

当给PN结施加的反向电压（V为负）大到一定程度，超过一个阈值 V_B（击穿电压）时，反向电流会**突然急剧增大**。这种现象就是“击穿”。

![UxW3bPtZPoPMLaxAiG6czo0En2e.png](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture5-24.webp)

**Zener Diode is designed to operate in the breakdown mode**

> PN结的**击穿特性本身是可逆的**（如果控制电流），但它导致的**发热**往往是**不可逆的破坏**。普通二极管应避免击穿；而齐纳二极管则巧妙地利用了“击穿时电压恒定”这一特性，通过特殊设计（并配合限流电阻R）使其能安全地工作在击穿区，实现了稳压功能

1. **好处 (Good Thing):** 击穿时，二极管两端的电压几乎恒定不变（钳位在 V_B）——**Zener Diode**。
2. **坏处 (Bad Thing):** 击穿时的大电流会**产生大量的热**（焦耳热），如果这个电流不加限制，高温会**不可逆地 (irreversible)** 烧毁器件

#### Breakdown Voltage

当反向电压 V_R 增大，使**峰值电场** <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi mathvariant="bold">

E

</mi>

<mrow>
<mi mathvariant="bold">

p

</mi>

<mi mathvariant="bold">

e

</mi>

<mi mathvariant="bold">

a

</mi>

<mi mathvariant="bold">

k

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

\mathbf{E_{peak}}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9722em;vertical-align:-0.2861em;">



</span>

<span className="mord">
<span className="mord,mathbf">

E

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

peak

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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

 达到了材料所能承受的**临界电场 E_** 时，击穿发生

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 37.9%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="P9HybAHduo4CZMxrY3pckFICncg.png" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture5-05.webp" />
      </p>
      
      <p>
        <img alt="XTOAbGsNKoDMklxWeXJc1lEUnXc.png" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture5-14.webp" />
      </p>
    </td>
    
    
      <td style="width: 62.1%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="XnL4bdeKuoM339x9kc7c4mYEn4c.png" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture5-15.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

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

c

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
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

E_{crit}

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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

cr

</span>

<span className="mord,mathnormal,mtight">

i

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

是一个材料参数（如<span className="katex">
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

c

</mi>

<mi>

r

</mi>

<mi>

i

</mi>

<msub>
<mi>

t

</mi>

<mrow>
<mi>

S

</mi>

<mi>

i

</mi>
</mrow>
</msub>
</mrow>
</msub>

<mo>

≈

</mo>

<mn>

3

</mn>

<mo>

×

</mo>

<msup>
<mn>

10

</mn>

<mn>

5

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

E_{crit_{Si}} \approx 3 \times 10^5 V/cm

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9336em;vertical-align:-0.2503em;">



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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

cr

</span>

<span className="mord,mathnormal,mtight">

i

</span>

<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

t

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3448em;">
<span style="top:-2.3567em;margin-left:0em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

S

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
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.2503em;">
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

5

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

）。

这里给出了一个重要的公式——击穿电压<span className="katex">
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

B

</mi>

<mi>

D

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

ε

</mi>

<mi>

s

</mi>
</msub>

<msubsup>
<mi>

E

</mi>

<mrow>
<mi>

c

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
</mrow>

<mn>

2

</mn>
</msubsup>
</mrow>

<mrow>
<mn>

2

</mn>

<mi>

q

</mi>

<msub>
<mi>

N

</mi>

<mrow>
<mi>

e

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
</mfrac>

<mo>

−

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

≈

</mo>

<mfrac>
<mrow>
<msub>
<mi>

ε

</mi>

<mi>

s

</mi>
</msub>

<msubsup>
<mi>

E

</mi>

<mrow>
<mi>

c

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
</mrow>

<mn>

2

</mn>
</msubsup>
</mrow>

<mrow>
<mn>

2

</mn>

<mi>

q

</mi>

<msub>
<mi>

N

</mi>

<mrow>
<mi>

l

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

<mi>

t

</mi>
</mrow>
</msub>
</mrow>
</mfrac>

<mo>

−

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

V_{BD} = \frac{\varepsilon_s E_{crit}^2}{2qN_{eff}} - V_{bi} \approx  \frac{\varepsilon_s E_{crit}^2}{2qN_{light}} - V_{bi}

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
<span className="mord,mathnormal,mtight" style="margin-right:0.0502em;">

B

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

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.6822em;vertical-align:-0.5481em;">



</span>

<span className="mord">
<span className="mopen,nulldelimiter">



</span>

<span className="mfrac">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:1.1341em;">
<span style="top:-2.655em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">

2

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

q

</span>

<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.109em;">

N

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3448em;">
<span style="top:-2.3488em;margin-left:-0.109em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

e

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

<span style="top:-3.5102em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

ε

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
<span className="vlist" style="height:0.143em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>

<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

E

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.8913em;">
<span style="top:-2.214em;margin-left:-0.0576em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

cr

</span>

<span className="mord,mathnormal,mtight">

i

</span>

<span className="mord,mathnormal,mtight">

t

</span>
</span>
</span>
</span>

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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

≈

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.6822em;vertical-align:-0.5481em;">



</span>

<span className="mord">
<span className="mopen,nulldelimiter">



</span>

<span className="mfrac">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:1.1341em;">
<span style="top:-2.655em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">

2

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

q

</span>

<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.109em;">

N

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3448em;">
<span style="top:-2.3488em;margin-left:-0.109em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal,mtight">

i

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

g

</span>

<span className="mord,mathnormal,mtight">

h

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

<span style="top:-3.5102em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

ε

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
<span className="vlist" style="height:0.143em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>

<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

E

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.8913em;">
<span style="top:-2.214em;margin-left:-0.0576em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

cr

</span>

<span className="mord,mathnormal,mtight">

i

</span>

<span className="mord,mathnormal,mtight">

t

</span>
</span>
</span>
</span>

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



> **如何提高击穿电压** <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msub>
> <mi mathvariant="bold">
> 
> V
> 
> </mi>
> 
> <mi mathvariant="bold">
> 
> B
> 
> </mi>
> </msub>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> \mathbf{V_B}
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:0.8361em;vertical-align:-0.15em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> <span className="mord,mathbf" style="margin-right:0.016em;">
> 
> V
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3303em;">
> <span style="top:-2.55em;margin-left:-0.016em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mathbf,mtight">
> 
> B
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
> **？** （耐高压器件的设计）
> 
> 1. **降低掺杂浓度 (**<span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msub>
> <mi mathvariant="bold">
> 
> N
> 
> </mi>
> 
> <mrow>
> <mi mathvariant="bold">
> 
> l
> 
> </mi>
> 
> <mi mathvariant="bold">
> 
> i
> 
> </mi>
> 
> <mi mathvariant="bold">
> 
> g
> 
> </mi>
> 
> <mi mathvariant="bold">
> 
> h
> 
> </mi>
> 
> <mi mathvariant="bold">
> 
> t
> 
> </mi>
> </mrow>
> </msub>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> \mathbf{N_{light}}
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:0.9722em;vertical-align:-0.2861em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> <span className="mord,mathbf">
> 
> N
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
> <span className="mord,mtight">
> <span className="mord,mathbf,mtight">
> 
> light
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
> **)：**
>   - 从公式 <span className="katex">
>   <span className="katex-mathml">
>   <math xmlns="http://www.w3.org/1998/Math/MathML">
>   <semantics>
>   <mrow>
>   <msub>
>   <mi>
>   
>   V
>   
>   </mi>
>   
>   <mi>
>   
>   B
>   
>   </mi>
>   </msub>
>   
>   <mo>
>   
>   ∝
>   
>   </mo>
>   
>   <mn>
>   
>   1
>   
>   </mn>
>   
>   <mi mathvariant="normal">
>   
>   /
>   
>   </mi>
>   
>   <msub>
>   <mi>
>   
>   N
>   
>   </mi>
>   
>   <mrow>
>   <mi>
>   
>   l
>   
>   </mi>
>   
>   <mi>
>   
>   i
>   
>   </mi>
>   
>   <mi>
>   
>   g
>   
>   </mi>
>   
>   <mi>
>   
>   h
>   
>   </mi>
>   
>   <mi>
>   
>   t
>   
>   </mi>
>   </mrow>
>   </msub>
>   </mrow>
>   
>   <annotation encoding="application/x-tex">
>   
>   V_B \propto 1/N_{light}
>   
>   </annotation>
>   </semantics>
>   </math>
>   </span>
>   
>   <span className="katex-html" ariaHidden="true">
>   <span className="base">
>   <span className="strut" style="height:0.8333em;vertical-align:-0.15em;">
>   
>   
>   
>   </span>
>   
>   <span className="mord">
>   <span className="mord,mathnormal" style="margin-right:0.2222em;">
>   
>   V
>   
>   </span>
>   
>   <span className="msupsub">
>   <span className="vlist-t,vlist-t2">
>   <span className="vlist-r">
>   <span className="vlist" style="height:0.3283em;">
>   <span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
>   <span className="pstrut" style="height:2.7em;">
>   
>   
>   
>   </span>
>   
>   <span className="sizing,reset-size6,size3,mtight">
>   <span className="mord,mathnormal,mtight" style="margin-right:0.0502em;">
>   
>   B
>   
>   </span>
>   </span>
>   </span>
>   </span>
>   
>   <span className="vlist-s">
>   
>   ​
>   
>   </span>
>   </span>
>   
>   <span className="vlist-r">
>   <span className="vlist" style="height:0.15em;">
>   <span>
>   
>   
>   
>   </span>
>   </span>
>   </span>
>   </span>
>   </span>
>   </span>
>   
>   <span className="mspace" style="margin-right:0.2778em;">
>   
>   
>   
>   </span>
>   
>   <span className="mrel">
>   
>   ∝
>   
>   </span>
>   
>   <span className="mspace" style="margin-right:0.2778em;">
>   
>   
>   
>   </span>
>   </span>
>   
>   <span className="base">
>   <span className="strut" style="height:1.0361em;vertical-align:-0.2861em;">
>   
>   
>   
>   </span>
>   
>   <span className="mord">
>   
>   1/
>   
>   </span>
>   
>   <span className="mord">
>   <span className="mord,mathnormal" style="margin-right:0.109em;">
>   
>   N
>   
>   </span>
>   
>   <span className="msupsub">
>   <span className="vlist-t,vlist-t2">
>   <span className="vlist-r">
>   <span className="vlist" style="height:0.3361em;">
>   <span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
>   <span className="pstrut" style="height:2.7em;">
>   
>   
>   
>   </span>
>   
>   <span className="sizing,reset-size6,size3,mtight">
>   <span className="mord,mtight">
>   <span className="mord,mathnormal,mtight" style="margin-right:0.0197em;">
>   
>   l
>   
>   </span>
>   
>   <span className="mord,mathnormal,mtight">
>   
>   i
>   
>   </span>
>   
>   <span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">
>   
>   g
>   
>   </span>
>   
>   <span className="mord,mathnormal,mtight">
>   
>   h
>   
>   </span>
>   
>   <span className="mord,mathnormal,mtight">
>   
>   t
>   
>   </span>
>   </span>
>   </span>
>   </span>
>   </span>
>   
>   <span className="vlist-s">
>   
>   ​
>   
>   </span>
>   </span>
>   
>   <span className="vlist-r">
>   <span className="vlist" style="height:0.2861em;">
>   <span>
>   
>   
>   
>   </span>
>   </span>
>   </span>
>   </span>
>   </span>
>   </span>
>   </span>
>   </span>
>   </span>
>   
>    可知，掺杂越轻， V_B 越高。
>   - 这就是为什么高压器件需要一个宽的、极轻掺杂的“漂移区”。
> 2. **提高临界电场 (**<span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msub>
> <mi mathvariant="bold">
> 
> E
> 
> </mi>
> 
> <mrow>
> <mi mathvariant="bold">
> 
> c
> 
> </mi>
> 
> <mi mathvariant="bold">
> 
> r
> 
> </mi>
> 
> <mi mathvariant="bold">
> 
> i
> 
> </mi>
> 
> <mi mathvariant="bold">
> 
> t
> 
> </mi>
> </mrow>
> </msub>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> \mathbf{E_{crit}}
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:0.8361em;vertical-align:-0.15em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> <span className="mord,mathbf">
> 
> E
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
> <span className="mord,mtight">
> <span className="mord,mathbf,mtight">
> 
> crit
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
> **)：**
>   - 从公式 <span className="katex">
>   <span className="katex-mathml">
>   <math xmlns="http://www.w3.org/1998/Math/MathML">
>   <semantics>
>   <mrow>
>   <msub>
>   <mi>
>   
>   V
>   
>   </mi>
>   
>   <mi>
>   
>   B
>   
>   </mi>
>   </msub>
>   
>   <mo>
>   
>   ∝
>   
>   </mo>
>   
>   <msubsup>
>   <mi>
>   
>   E
>   
>   </mi>
>   
>   <mrow>
>   <mi>
>   
>   c
>   
>   </mi>
>   
>   <mi>
>   
>   r
>   
>   </mi>
>   
>   <mi>
>   
>   i
>   
>   </mi>
>   
>   <mi>
>   
>   t
>   
>   </mi>
>   </mrow>
>   
>   <mn>
>   
>   2
>   
>   </mn>
>   </msubsup>
>   </mrow>
>   
>   <annotation encoding="application/x-tex">
>   
>   V_B \propto E_{crit}^2
>   
>   </annotation>
>   </semantics>
>   </math>
>   </span>
>   
>   <span className="katex-html" ariaHidden="true">
>   <span className="base">
>   <span className="strut" style="height:0.8333em;vertical-align:-0.15em;">
>   
>   
>   
>   </span>
>   
>   <span className="mord">
>   <span className="mord,mathnormal" style="margin-right:0.2222em;">
>   
>   V
>   
>   </span>
>   
>   <span className="msupsub">
>   <span className="vlist-t,vlist-t2">
>   <span className="vlist-r">
>   <span className="vlist" style="height:0.3283em;">
>   <span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
>   <span className="pstrut" style="height:2.7em;">
>   
>   
>   
>   </span>
>   
>   <span className="sizing,reset-size6,size3,mtight">
>   <span className="mord,mathnormal,mtight" style="margin-right:0.0502em;">
>   
>   B
>   
>   </span>
>   </span>
>   </span>
>   </span>
>   
>   <span className="vlist-s">
>   
>   ​
>   
>   </span>
>   </span>
>   
>   <span className="vlist-r">
>   <span className="vlist" style="height:0.15em;">
>   <span>
>   
>   
>   
>   </span>
>   </span>
>   </span>
>   </span>
>   </span>
>   </span>
>   
>   <span className="mspace" style="margin-right:0.2778em;">
>   
>   
>   
>   </span>
>   
>   <span className="mrel">
>   
>   ∝
>   
>   </span>
>   
>   <span className="mspace" style="margin-right:0.2778em;">
>   
>   
>   
>   </span>
>   </span>
>   
>   <span className="base">
>   <span className="strut" style="height:1.0728em;vertical-align:-0.2587em;">
>   
>   
>   
>   </span>
>   
>   <span className="mord">
>   <span className="mord,mathnormal" style="margin-right:0.0576em;">
>   
>   E
>   
>   </span>
>   
>   <span className="msupsub">
>   <span className="vlist-t,vlist-t2">
>   <span className="vlist-r">
>   <span className="vlist" style="height:0.8141em;">
>   <span style="top:-2.4413em;margin-left:-0.0576em;margin-right:0.05em;">
>   <span className="pstrut" style="height:2.7em;">
>   
>   
>   
>   </span>
>   
>   <span className="sizing,reset-size6,size3,mtight">
>   <span className="mord,mtight">
>   <span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">
>   
>   cr
>   
>   </span>
>   
>   <span className="mord,mathnormal,mtight">
>   
>   i
>   
>   </span>
>   
>   <span className="mord,mathnormal,mtight">
>   
>   t
>   
>   </span>
>   </span>
>   </span>
>   </span>
>   
>   <span style="top:-3.063em;margin-right:0.05em;">
>   <span className="pstrut" style="height:2.7em;">
>   
>   
>   
>   </span>
>   
>   <span className="sizing,reset-size6,size3,mtight">
>   <span className="mord,mtight">
>   
>   2
>   
>   </span>
>   </span>
>   </span>
>   </span>
>   
>   <span className="vlist-s">
>   
>   ​
>   
>   </span>
>   </span>
>   
>   <span className="vlist-r">
>   <span className="vlist" style="height:0.2587em;">
>   <span>
>   
>   
>   
>   </span>
>   </span>
>   </span>
>   </span>
>   </span>
>   </span>
>   </span>
>   </span>
>   </span>
>   
>    可知，<span className="katex">
>   <span className="katex-mathml">
>   <math xmlns="http://www.w3.org/1998/Math/MathML">
>   <semantics>
>   <mrow>
>   <msub>
>   <mi>
>   
>   E
>   
>   </mi>
>   
>   <mrow>
>   <mi>
>   
>   c
>   
>   </mi>
>   
>   <mi>
>   
>   r
>   
>   </mi>
>   
>   <mi>
>   
>   i
>   
>   </mi>
>   
>   <mi>
>   
>   t
>   
>   </mi>
>   </mrow>
>   </msub>
>   </mrow>
>   
>   <annotation encoding="application/x-tex">
>   
>   E_{crit}
>   
>   </annotation>
>   </semantics>
>   </math>
>   </span>
>   
>   <span className="katex-html" ariaHidden="true">
>   <span className="base">
>   <span className="strut" style="height:0.8333em;vertical-align:-0.15em;">
>   
>   
>   
>   </span>
>   
>   <span className="mord">
>   <span className="mord,mathnormal" style="margin-right:0.0576em;">
>   
>   E
>   
>   </span>
>   
>   <span className="msupsub">
>   <span className="vlist-t,vlist-t2">
>   <span className="vlist-r">
>   <span className="vlist" style="height:0.3117em;">
>   <span style="top:-2.55em;margin-left:-0.0576em;margin-right:0.05em;">
>   <span className="pstrut" style="height:2.7em;">
>   
>   
>   
>   </span>
>   
>   <span className="sizing,reset-size6,size3,mtight">
>   <span className="mord,mtight">
>   <span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">
>   
>   cr
>   
>   </span>
>   
>   <span className="mord,mathnormal,mtight">
>   
>   i
>   
>   </span>
>   
>   <span className="mord,mathnormal,mtight">
>   
>   t
>   
>   </span>
>   </span>
>   </span>
>   </span>
>   </span>
>   
>   <span className="vlist-s">
>   
>   ​
>   
>   </span>
>   </span>
>   
>   <span className="vlist-r">
>   <span className="vlist" style="height:0.15em;">
>   <span>
>   
>   
>   
>   </span>
>   </span>
>   </span>
>   </span>
>   </span>
>   </span>
>   </span>
>   </span>
>   </span>
>   
>    影响巨大。
>   - 使用**宽禁带半导体**（如 SiC, GaN），它们的 <span className="katex">
>   <span className="katex-mathml">
>   <math xmlns="http://www.w3.org/1998/Math/MathML">
>   <semantics>
>   <mrow>
>   <msub>
>   <mi>
>   
>   E
>   
>   </mi>
>   
>   <mrow>
>   <mi>
>   
>   c
>   
>   </mi>
>   
>   <mi>
>   
>   r
>   
>   </mi>
>   
>   <mi>
>   
>   i
>   
>   </mi>
>   
>   <mi>
>   
>   t
>   
>   </mi>
>   </mrow>
>   </msub>
>   </mrow>
>   
>   <annotation encoding="application/x-tex">
>   
>   E_{crit}
>   
>   </annotation>
>   </semantics>
>   </math>
>   </span>
>   
>   <span className="katex-html" ariaHidden="true">
>   <span className="base">
>   <span className="strut" style="height:0.8333em;vertical-align:-0.15em;">
>   
>   
>   
>   </span>
>   
>   <span className="mord">
>   <span className="mord,mathnormal" style="margin-right:0.0576em;">
>   
>   E
>   
>   </span>
>   
>   <span className="msupsub">
>   <span className="vlist-t,vlist-t2">
>   <span className="vlist-r">
>   <span className="vlist" style="height:0.3117em;">
>   <span style="top:-2.55em;margin-left:-0.0576em;margin-right:0.05em;">
>   <span className="pstrut" style="height:2.7em;">
>   
>   
>   
>   </span>
>   
>   <span className="sizing,reset-size6,size3,mtight">
>   <span className="mord,mtight">
>   <span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">
>   
>   cr
>   
>   </span>
>   
>   <span className="mord,mathnormal,mtight">
>   
>   i
>   
>   </span>
>   
>   <span className="mord,mathnormal,mtight">
>   
>   t
>   
>   </span>
>   </span>
>   </span>
>   </span>
>   </span>
>   
>   <span className="vlist-s">
>   
>   ​
>   
>   </span>
>   </span>
>   
>   <span className="vlist-r">
>   <span className="vlist" style="height:0.15em;">
>   <span>
>   
>   
>   
>   </span>
>   </span>
>   </span>
>   </span>
>   </span>
>   </span>
>   </span>
>   </span>
>   </span>
>   
>    远高于Si，因此是制作高压器件的理想材料。

<alert type="question">

**为什么宽禁带半导体击穿场强大？**

高压器件的击穿主要是**雪崩击穿**。这个过程依赖于**碰撞电离 (Impact Ionization)**，碰撞电离所需要的最小动能（即“门槛能量” <span className="katex">
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

t

</mi>

<mi>

h

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

E_{th}

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
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.0576em;margin-right:0.05em;">
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

）**正比于禁带宽度** <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

E

</mi>

<mi>

g

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

E_g

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
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0576em;margin-right:0.05em;">
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

。（一个近似值是 <span className="katex">
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

t

</mi>

<mi>

h

</mi>
</mrow>
</msub>

<mo>

≈

</mo>

<mn>

1.5

</mn>

<mo>

×

</mo>

<msub>
<mi>

E

</mi>

<mi>

g

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

E_{th} \approx 1.5 \times E_g

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
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.0576em;margin-right:0.05em;">
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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

≈

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.7278em;vertical-align:-0.0833em;">



</span>

<span className="mord">

1.5

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

）

因此，逻辑链是：

**宽禁带 (**<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

E

</mi>

<mi>

g

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

E_g

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
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0576em;margin-right:0.05em;">
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

 **大)** <span className="katex">
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

**碰撞电离的能量高** <span className="katex">
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

**载流子需要被更强的电场加速，才能获得这份能量**  <span className="katex">
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

**能够触发雪崩的“临界电场” (**<span className="katex">
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

c

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
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

E_{crit}

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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

cr

</span>

<span className="mord,mathnormal,mtight">

i

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

**) 非常强。**

</alert>

#### Tunneling Breakdown

![MuJHblb8ZoOItvx9fDfc1ISrnzc.png](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture5-18.webp)

1. **发生条件：**
  - 在**两边都重掺杂 (N_A, N_D 都很高)** 的PN结中占主导。
2. **物理过程：** **量子隧道效应 (Quantum Tunneling)**
  - 两边都重掺杂 <span className="katex">
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
  
   **耗尽区宽度非常窄**（<span className="katex">
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
  
  e
  
  </mi>
  
  <mi>
  
  p
  
  </mi>
  </mrow>
  </msub>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  W_{dep}
  
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
  </span>
  </span>
  </span>
  
   极窄）
  - 势垒虽然高，但非常薄，P区的电子（在价带）可以直接**“隧穿”**通过这个薄势垒，到达N区的导带，形成大电流。
3. **特性：**
  - 通常发生在较低的电压下（例如 V_B < 5\text{V}）。
4. **应用：**  **Zener Diode | 齐纳二极管**
  - **设计：** 专门**被设计用来安全工作在击穿模式**的二极管。（通常 V_B < 5\text{V} 是齐纳击穿为主， V_B > 6\text{V} 是雪崩击穿为主）。
  - **功能：** **稳压 (Voltage Regulator)** 或 **电压钳位 (Clamping)**。
  - **电路：**
    1. 齐纳二极管**反向偏置**。
    2. 与被保护的负载（如 IC）**并联**。
    3. 必须**串联**一个**限流电阻 (R)**，以防止过热烧毁。
  - **工作原理：** 当输入电压(A-B)超过<span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <msub>
  <mi>
  
  V
  
  </mi>
  
  <mi>
  
  B
  
  </mi>
  </msub>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  V_B
  
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
  
  （例如3.7V）时，二极管击穿，将C-D两点的电压“钳位”在 <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <msub>
  <mi>
  
  V
  
  </mi>
  
  <mi>
  
  B
  
  </mi>
  </msub>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  V_B
  
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
  
   (3.7V)，从而保护IC。

#### Avalanche Breakdown  | 雪崩击穿

![PixPin_2025-11-12_20-35-39.png](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture5-04.webp)

1. **发生条件  |  Condition：**
  - 在**轻掺杂**（或中等掺杂）的PN结中占主导。
  - 此时 V_B 较高，耗尽层较宽。
2. **物理过程：** **碰撞电离 (Impact Ionization)**
  - 耗尽区电场强，电子被加速获得很高能量
  <span className="katex">
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
  
  高能电子**撞击**晶格，将价带电子“撞”出，产生一个新的**电子-空穴对**<br />
  
  <span className="katex">
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
  
  新产生的载流子也被加速，再去撞击，产生更多的载流子<br />
  
  <span className="katex">
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
  
    这个过程像雪崩一样，是一个**正反馈 (Positive Feedback)**，导致载流子数量和电流剧增。
  - In the strong electric field of the depletion region, electrons are accelerated and gain high kinetic energy.
  <span className="katex">
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
  
   These energetic electrons **impact** the crystal lattice, "knocking out" a valence electron and **generating a new electron-hole pair**.<br />
  
  <span className="katex">
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
  
   The newly generated carriers are also accelerated, impacting the lattice again to generate even more carriers.<br />
  
  <span className="katex">
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
  
  This process, like an avalanche, is a **positive feedback** loop, leading to a dramatic, exponential increase in carrier concentration and current.
3. **应用：**
  - 雪崩光电探测器 (APD, Avalanche Photodetector) 利用此效应来放大微弱的光信号。
  - 雪崩过程本身**不会**损坏器件，是**过热**导致损坏。
