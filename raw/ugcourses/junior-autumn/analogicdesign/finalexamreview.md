# 期末考试整理

> 模拟集成电路设计：期末考试整理

## 英文翻译

### 21-22

1. CMOS：Complementary Metal-Oxide-Semiconductor
2. CMRR：Common-Mode Rejection Ratio
3. OTA：Operational Transconductance Amplifier
4. IC：Integrated Circuit

### 24-25

1. PVT：Process, Voltage, Temperature
2. FET：Field-Effect Transistor
3. ADC：Analog-to-Digital Converter

### 自己加的

- BJT：Bipolar Junction Transistor
- TC：Temperature Coefficient
- THD：Total Harmonic Distortion
- GBW：Gain-Bandwidth

## 选择

### 24-25

1. 将掩模版上的信息转移到 wafer 上的步骤是

> 光刻

1. 描述沟道长度调制效应的现象，判别效应名称

> 沟道长度调制（Channel Length Modulation, CLM）主要出现在 **MOSFET 进入饱和区** 后：理想情况下饱和区电流<span className="katex">
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
> I_D
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
> <span className="vlist" style="height:0.3283em;">
> <span style="top:-2.55em;margin-left:-0.0785em;margin-right:0.05em;">
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
> 应该几乎不随<span className="katex">
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
> 变化，但实际会发现<span className="katex">
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
> **继续增大时**<span className="katex">
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
> I_D
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
> <span className="vlist" style="height:0.3283em;">
> <span style="top:-2.55em;margin-left:-0.0785em;margin-right:0.05em;">
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
> **仍会缓慢上升**。

1. 对于PMOS而言，<span className="katex">
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

增大，<span className="katex">
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

<mrow>
<mi>

t

</mi>

<mi>

h

</mi>

<mi>

p

</mi>
</mrow>
</msub>

<mi mathvariant="normal">

∣

</mi>
</mrow>

<annotation encoding="application/x-tex">

|V_{thp}|

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.0361em;vertical-align:-0.2861em;">



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

<span className="mord">

∣

</span>
</span>
</span>
</span>

变大。

> 体效应公式：NMOS <span className="katex">
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
> t
> 
> </mi>
> 
> <mi>
> 
> h
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
> <mi>
> 
> h
> 
> </mi>
> 
> <mi>
> 
> n
> 
> </mi>
> 
> <mn>
> 
> 0
> 
> </mn>
> </mrow>
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
> γ
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
> <mrow>
> <mo fence="true">
> 
> (
> 
> </mo>
> 
> <msqrt>
> <mrow>
> <mn>
> 
> 2
> 
> </mn>
> 
> <msub>
> <mi>
> 
> ϕ
> 
> </mi>
> 
> <mrow>
> <mi>
> 
> F
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
> <mo>
> 
> +
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
> S
> 
> </mi>
> 
> <mi>
> 
> B
> 
> </mi>
> </mrow>
> </msub>
> </mrow>
> </msqrt>
> 
> <mo>
> 
> −
> 
> </mo>
> 
> <msqrt>
> <mrow>
> <mn>
> 
> 2
> 
> </mn>
> 
> <msub>
> <mi>
> 
> ϕ
> 
> </mi>
> 
> <mrow>
> <mi>
> 
> F
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
> V_{thn} = V_{thn0} + \gamma_n \left(\sqrt{2\phi_{Fn} + V_{SB}} - \sqrt{2\phi_{Fn}}\right)
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
> t
> 
> </span>
> 
> <span className="mord,mathnormal,mtight">
> 
> hn
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
> <span className="mord,mathnormal,mtight">
> 
> hn
> 
> </span>
> 
> <span className="mord,mtight">
> 
> 0
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
> <span className="strut" style="height:1.2em;vertical-align:-0.35em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> <span className="mord,mathnormal" style="margin-right:0.0556em;">
> 
> γ
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.1514em;">
> <span style="top:-2.55em;margin-left:-0.0556em;margin-right:0.05em;">
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
> <span className="mspace" style="margin-right:0.1667em;">
> 
> 
> 
> </span>
> 
> <span className="minner">
> <span className="mopen,delimcenter" style="top:0em;">
> <span className="delimsizing,size1">
> 
> (
> 
> </span>
> </span>
> 
> <span className="mord,sqrt">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.835em;">
> <span className="svg-align" style="top:-3em;">
> <span className="pstrut" style="height:3em;">
> 
> 
> 
> </span>
> 
> <span className="mord" style="padding-left:0.833em;">
> <span className="mord">
> 
> 2
> 
> </span>
> 
> <span className="mord">
> <span className="mord,mathnormal">
> 
> ϕ
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
> <span className="mord,mathnormal,mtight" style="margin-right:0.1389em;">
> 
> F
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
> <span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">
> 
> S
> 
> </span>
> 
> <span className="mord,mathnormal,mtight" style="margin-right:0.0502em;">
> 
> B
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
> 
> <span style="top:-2.795em;">
> <span className="pstrut" style="height:3em;">
> 
> 
> 
> </span>
> 
> <span className="hide-tail" style="min-width:0.853em;height:1.08em;">
> <svg xmlns="http://www.w3.org/2000/svg" width="400em" height="1.08em" viewBox="0 0 400000 1080" preserveAspectRatio="xMinYMin slice">
> <path d="M95,702
> c-2.7,0,-7.17,-2.7,-13.5,-8c-5.8,-5.3,-9.5,-10,-9.5,-14
> c0,-2,0.3,-3.3,1,-4c1.3,-2.7,23.83,-20.7,67.5,-54
> c44.2,-33.3,65.8,-50.3,66.5,-51c1.3,-1.3,3,-2,5,-2c4.7,0,8.7,3.3,12,10
> s173,378,173,378c0.7,0,35.3,-71,104,-213c68.7,-142,137.5,-285,206.5,-429
> c69,-144,104.5,-217.7,106.5,-221
> l0 -0
> c5.3,-9.3,12,-14,20,-14
> H400000v40H845.2724
> s-225.272,467,-225.272,467s-235,486,-235,486c-2.7,4.7,-9,7,-19,7
> c-6,0,-10,-1,-12,-3s-194,-422,-194,-422s-65,47,-65,47z
> M834 80h400000v40h-400000z">
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
> <span className="vlist" style="height:0.205em;">
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
> <span className="mord,sqrt">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.835em;">
> <span className="svg-align" style="top:-3em;">
> <span className="pstrut" style="height:3em;">
> 
> 
> 
> </span>
> 
> <span className="mord" style="padding-left:0.833em;">
> <span className="mord">
> 
> 2
> 
> </span>
> 
> <span className="mord">
> <span className="mord,mathnormal">
> 
> ϕ
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
> <span className="mord,mathnormal,mtight" style="margin-right:0.1389em;">
> 
> F
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
> 
> <span style="top:-2.795em;">
> <span className="pstrut" style="height:3em;">
> 
> 
> 
> </span>
> 
> <span className="hide-tail" style="min-width:0.853em;height:1.08em;">
> <svg xmlns="http://www.w3.org/2000/svg" width="400em" height="1.08em" viewBox="0 0 400000 1080" preserveAspectRatio="xMinYMin slice">
> <path d="M95,702
> c-2.7,0,-7.17,-2.7,-13.5,-8c-5.8,-5.3,-9.5,-10,-9.5,-14
> c0,-2,0.3,-3.3,1,-4c1.3,-2.7,23.83,-20.7,67.5,-54
> c44.2,-33.3,65.8,-50.3,66.5,-51c1.3,-1.3,3,-2,5,-2c4.7,0,8.7,3.3,12,10
> s173,378,173,378c0.7,0,35.3,-71,104,-213c68.7,-142,137.5,-285,206.5,-429
> c69,-144,104.5,-217.7,106.5,-221
> l0 -0
> c5.3,-9.3,12,-14,20,-14
> H400000v40H845.2724
> s-225.272,467,-225.272,467s-235,486,-235,486c-2.7,4.7,-9,7,-19,7
> c-6,0,-10,-1,-12,-3s-194,-422,-194,-422s-65,47,-65,47z
> M834 80h400000v40h-400000z">
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
> <span className="vlist" style="height:0.205em;">
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
> <span className="delimsizing,size1">
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
> ；
> 
> PMOS <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <mrow>
> <mo fence="true">
> 
> ∣
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
> <mi>
> 
> h
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
> <mo fence="true">
> 
> ∣
> 
> </mo>
> </mrow>
> 
> <mo>
> 
> =
> 
> </mo>
> 
> <mrow>
> <mo fence="true">
> 
> ∣
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
> <mi>
> 
> h
> 
> </mi>
> 
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
> </mrow>
> </msub>
> 
> <mo fence="true">
> 
> ∣
> 
> </mo>
> </mrow>
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
> γ
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
> <mrow>
> <mo fence="true">
> 
> (
> 
> </mo>
> 
> <msqrt>
> <mrow>
> <mn>
> 
> 2
> 
> </mn>
> 
> <mrow>
> <mo fence="true">
> 
> ∣
> 
> </mo>
> 
> <msub>
> <mi>
> 
> ϕ
> 
> </mi>
> 
> <mrow>
> <mi>
> 
> F
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
> <mo fence="true">
> 
> ∣
> 
> </mo>
> </mrow>
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
> V
> 
> </mi>
> 
> <mrow>
> <mi>
> 
> B
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
> </msqrt>
> 
> <mo>
> 
> −
> 
> </mo>
> 
> <msqrt>
> <mrow>
> <mn>
> 
> 2
> 
> </mn>
> 
> <mrow>
> <mo fence="true">
> 
> ∣
> 
> </mo>
> 
> <msub>
> <mi>
> 
> ϕ
> 
> </mi>
> 
> <mrow>
> <mi>
> 
> F
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
> <mo fence="true">
> 
> ∣
> 
> </mo>
> </mrow>
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
> \left|V_{thp}\right| = \left|V_{thp0}\right| + \gamma_p \left(\sqrt{2\left|\phi_{Fp}\right| + V_{BS}} - \sqrt{2\left|\phi_{Fp}\right|}\right)
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:1.0361em;vertical-align:-0.2861em;">
> 
> 
> 
> </span>
> 
> <span className="minner">
> <span className="mopen,delimcenter" style="top:0em;">
> 
> ∣
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
> <span className="mord,mathnormal,mtight">
> 
> h
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
> <span className="mclose,delimcenter" style="top:0em;">
> 
> ∣
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
> <span className="strut" style="height:1.0361em;vertical-align:-0.2861em;">
> 
> 
> 
> </span>
> 
> <span className="minner">
> <span className="mopen,delimcenter" style="top:0em;">
> 
> ∣
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
> <span className="mord,mathnormal,mtight">
> 
> h
> 
> </span>
> 
> <span className="mord,mathnormal,mtight">
> 
> p
> 
> </span>
> 
> <span className="mord,mtight">
> 
> 0
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
> <span className="mclose,delimcenter" style="top:0em;">
> 
> ∣
> 
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
> <span className="strut" style="height:1.8em;vertical-align:-0.65em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> <span className="mord,mathnormal" style="margin-right:0.0556em;">
> 
> γ
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.1514em;">
> <span style="top:-2.55em;margin-left:-0.0556em;margin-right:0.05em;">
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
> <span className="mord,sqrt">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.9169em;">
> <span className="svg-align" style="top:-3.2em;">
> <span className="pstrut" style="height:3.2em;">
> 
> 
> 
> </span>
> 
> <span className="mord" style="padding-left:1em;">
> <span className="mord">
> 
> 2
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
> 
> ∣
> 
> </span>
> 
> <span className="mord">
> <span className="mord,mathnormal">
> 
> ϕ
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
> <span className="mord,mathnormal,mtight" style="margin-right:0.1389em;">
> 
> F
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
> <span className="mclose,delimcenter" style="top:0em;">
> 
> ∣
> 
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
> <span className="mord,mathnormal,mtight" style="margin-right:0.0502em;">
> 
> B
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
> 
> <span style="top:-2.8769em;">
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
> <span className="vlist" style="height:0.3231em;">
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
> <span className="mord,sqrt">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.9169em;">
> <span className="svg-align" style="top:-3.2em;">
> <span className="pstrut" style="height:3.2em;">
> 
> 
> 
> </span>
> 
> <span className="mord" style="padding-left:1em;">
> <span className="mord">
> 
> 2
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
> 
> ∣
> 
> </span>
> 
> <span className="mord">
> <span className="mord,mathnormal">
> 
> ϕ
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
> <span className="mord,mathnormal,mtight" style="margin-right:0.1389em;">
> 
> F
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
> <span className="mclose,delimcenter" style="top:0em;">
> 
> ∣
> 
> </span>
> </span>
> </span>
> </span>
> 
> <span style="top:-2.8769em;">
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
> <span className="vlist" style="height:0.3231em;">
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

1. current buffer 是 common gate；voltage buffer 是 common drain（source follwer）
2. Cascode结构输出特性的增益较大，主要由于它的输出电阻大。
3. 增大下**B图**电路的偏置电流，问增益怎么变?（作业题3.5）

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/FinalExamReview-01.webp)

> **增大偏置电流**：A图增益不变，B图增益减小，C图增益减小。
> 
> **增大M1的W/L，**<span className="katex">
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
> 
> <mo separator="true">
> 
> ,
> 
> </mo>
> 
> <mi>
> 
> m
> 
> </mi>
> 
> <mi>
> 
> i
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
> V_{out,min}
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
> <span className="mord,mathnormal" style="margin-right:0.2222em;">
> 
> V
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3117em;">
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
> 
> <span className="mpunct,mtight">
> 
> ,
> 
> </span>
> 
> <span className="mord,mathnormal,mtight">
> 
> min
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
> **变化**：A和B图减小，C图不变。

1. 图中电路结构中 P 点的电压最小是（2Vov+Vth）见课本P128页

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/FinalExamReview-02.webp)

1. 下图结点 E 的电容是多少？

> 输入E是<span className="katex">
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
> <mn>
> 
> 1
> 
> </mn>
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
> <mo stretchy="false">
> 
> )
> 
> </mo>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> C_c(1-A_2)
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
> <span className="mopen">
> 
> (
> 
> </span>
> 
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
> <span className="mclose">
> 
> )
> 
> </span>
> </span>
> </span>
> </span>
> 
> ；输出节点是<span className="katex">
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
> <mn>
> 
> 1
> 
> </mn>
> 
> <mo>
> 
> −
> 
> </mo>
> 
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
> <mo stretchy="false">
> 
> )
> 
> </mo>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> C_c(1-1/A_2)
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
> <span className="mopen">
> 
> (
> 
> </span>
> 
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
> <span className="mord">
> 
> 1/
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
> <span className="mclose">
> 
> )
> 
> </span>
> </span>
> </span>
> </span>

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/FinalExamReview-03.webp)

1. 两级运放里面密勒补偿的目的

> 增大相位裕度。

**频率补偿方法**：单级运放电路可以增加负载电容降低主极点的频率，但是牺牲带宽；多级采用密勒补偿；多级也可以在右半平面中引入零点。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/FinalExamReview-04.webp)

1. 增益 A=1000 的系统，第一个极点在 1MHz，第二个极点在 5MHz，问相位裕度在多少度

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/FinalExamReview-05.webp)

1. 共模响应特性

> **共模反馈**：一种专门的反馈环路，用电路检测差分输出的共模电压<span className="katex">
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
> <mrow>
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
> m
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
> <mo stretchy="false">
> 
> (
> 
> </mo>
> 
> <msub>
> <mi>
> 
> v
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
> 
> <mo>
> 
> +
> 
> </mo>
> </mrow>
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
> v
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
> 
> <mo>
> 
> −
> 
> </mo>
> </mrow>
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
> <mn>
> 
> 2
> 
> </mn>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> v_{ocm}=(v_{out+}+v_{out-})/2
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
> <span className="vlist" style="height:0.1514em;">
> <span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
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
> oc
> 
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
> <span className="mord,mathnormal" style="margin-right:0.0359em;">
> 
> v
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.2806em;">
> <span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
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
> 
> <span className="mord,mtight">
> 
> +
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
> <span className="mord,mathnormal" style="margin-right:0.0359em;">
> 
> v
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.2806em;">
> <span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
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
> 
> <span className="mord,mtight">
> 
> −
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
> <span className="mclose">
> 
> )
> 
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
> ，并与设定的共模参考电压<span className="katex">
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
> C
> 
> </mi>
> 
> <mi>
> 
> M
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
> r
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
> </mrow>
> </msub>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> V_{CM,ref}
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
> <span className="mord,mathnormal,mtight" style="margin-right:0.0715em;">
> 
> C
> 
> </span>
> 
> <span className="mord,mathnormal,mtight" style="margin-right:0.109em;">
> 
> M
> 
> </span>
> 
> <span className="mpunct,mtight">
> 
> ,
> 
> </span>
> 
> <span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">
> 
> r
> 
> </span>
> 
> <span className="mord,mathnormal,mtight">
> 
> e
> 
> </span>
> 
> <span className="mord,mathnormal,mtight" style="margin-right:0.1076em;">
> 
> f
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
> 比较，将误差信号反馈去调节偏置/尾电流/负载等，使<span className="katex">
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
> <mrow>
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
> m
> 
> </mi>
> </mrow>
> </msub>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> v_{ocm}
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
> <span className="vlist" style="height:0.1514em;">
> <span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
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
> oc
> 
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
> 被稳定在<span className="katex">
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
> C
> 
> </mi>
> 
> <mi>
> 
> M
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
> r
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
> </mrow>
> </msub>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> V_{CM,ref}
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
> <span className="mord,mathnormal,mtight" style="margin-right:0.0715em;">
> 
> C
> 
> </span>
> 
> <span className="mord,mathnormal,mtight" style="margin-right:0.109em;">
> 
> M
> 
> </span>
> 
> <span className="mpunct,mtight">
> 
> ,
> 
> </span>
> 
> <span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">
> 
> r
> 
> </span>
> 
> <span className="mord,mathnormal,mtight">
> 
> e
> 
> </span>
> 
> <span className="mord,mathnormal,mtight" style="margin-right:0.1076em;">
> 
> f
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
> 附近，同时尽量不影响差模增益与差模信号传输。
> 
> **共模响应**：共模响应（common-mode response）是指在差分电路/运放中，当两个输入端**同时施加相同的电压变化**（即共模输入<span className="katex">
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
> <mrow>
> <mi>
> 
> c
> 
> </mi>
> 
> <mi>
> 
> m
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
> <mo stretchy="false">
> 
> (
> 
> </mo>
> 
> <msub>
> <mi>
> 
> v
> 
> </mi>
> 
> <mo>
> 
> +
> 
> </mo>
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
> v
> 
> </mi>
> 
> <mo>
> 
> −
> 
> </mo>
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
> <mn>
> 
> 2
> 
> </mn>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> v_{cm}=(v_++v_-)/2
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
> <span className="vlist" style="height:0.1514em;">
> <span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
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
> <span className="mord,mathnormal" style="margin-right:0.0359em;">
> 
> v
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.2583em;">
> <span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mbin,mtight">
> 
> +
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
> <span className="mord,mathnormal" style="margin-right:0.0359em;">
> 
> v
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.2583em;">
> <span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mbin,mtight">
> 
> −
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
> <span className="mclose">
> 
> )
> 
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
> 时，电路输出仍产生变化的现象。

1. 折叠式 cascode 比套筒式 cascode 的优点是什么（大电压**输入输出**摆幅）

<table>
<thead>
  <tr>
    <th>
      参数
    </th>
    
    <th>
      套筒式 cascode（Telescopic）
    </th>
    
    <th>
      折叠式 cascode（Folded）
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      直流增益 (A_0)
    </td>
    
    <td>
      高
    </td>
    
    <td>
      高（略低于套筒式）
    </td>
  </tr>
  
  <tr>
    <td>
      输入共模范围 ICMR
    </td>
    
    <td>
      窄
    </td>
    
    <td>
      宽
    </td>
  </tr>
  
  <tr>
    <td>
      输出摆幅
    </td>
    
    <td>
      小
    </td>
    
    <td>
      大
    </td>
  </tr>
  
  <tr>
    <td>
      供电电压需求（headroom）
    </td>
    
    <td>
      高（不适合低压）
    </td>
    
    <td>
      低（更适合低压）
    </td>
  </tr>
  
  <tr>
    <td>
      带宽/速度
    </td>
    
    <td>
      快
    </td>
    
    <td>
      较慢
    </td>
  </tr>
  
  <tr>
    <td>
      功耗
    </td>
    
    <td>
      低
    </td>
    
    <td>
      较高
    </td>
  </tr>
</tbody>
</table>

### 22-23

1. 哪个单级放大器输入阻抗最低，哪个电压增益最小
  - **输入阻抗最低：共栅 CG**（因为从源极看进去，约 <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mn>
  
  1
  
  </mn>
  
  <mi mathvariant="normal">
  
  /
  
  </mi>
  
  <mo stretchy="false">
  
  (
  
  </mo>
  
  <msub>
  <mi>
  
  g
  
  </mi>
  
  <mi>
  
  m
  
  </mi>
  </msub>
  
  <mo>
  
  +
  
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
  
  b
  
  </mi>
  </mrow>
  </msub>
  
  <mo stretchy="false">
  
  )
  
  </mo>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  1/(g_m+g_{mb})
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:1em;vertical-align:-0.25em;">
  
  
  
  </span>
  
  <span className="mord">
  
  1/
  
  </span>
  
  <span className="mopen">
  
  (
  
  </span>
  
  <span className="mord">
  <span className="mord,mathnormal" style="margin-right:0.0359em;">
  
  g
  
  </span>
  
  <span className="msupsub">
  <span className="vlist-t,vlist-t2">
  <span className="vlist-r">
  <span className="vlist" style="height:0.1514em;">
  <span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
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
  
  mb
  
  </span>
  </span>
  </span>
  </span>
  </span>
  
  <span className="vlist-s">
  
  ​
  
  </span>
  </span>
  
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
  
  ）
  - **电压增益最小：共漏 CD**（源极跟随，<span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <msub>
  <mi>
  
  A
  
  </mi>
  
  <mi>
  
  v
  
  </mi>
  </msub>
  
  <mo>
  
  ≲
  
  </mo>
  
  <mn>
  
  1
  
  </mn>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  A_v\lesssim 1
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:0.9592em;vertical-align:-0.2296em;">
  
  
  
  </span>
  
  <span className="mord">
  <span className="mord,mathnormal">
  
  A
  
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
  
  <span className="mrel,amsrm">
  
  ≲
  
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
  
  ）
2. 折叠式共源共栅比套筒式的优点<table>
<thead>
  <tr>
    <th>
      项目
    </th>
    
    <th>
      套筒 Telescopic
    </th>
    
    <th>
      折叠 Folded
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      增益 Av
    </td>
    
    <td>
      更高（通常最高）
    </td>
    
    <td>
      稍低一些
    </td>
  </tr>
  
  <tr>
    <td>
      速度/GBW
    </td>
    
    <td>
      更快
    </td>
    
    <td>
      稍慢一些
    </td>
  </tr>
  
  <tr>
    <td>
      输出摆幅
    </td>
    
    <td>
      更小（最受限）
    </td>
    
    <td>
      更大
    </td>
  </tr>
  
  <tr>
    <td>
      最低供电 VDD
    </td>
    
    <td>
      要求更高
    </td>
    
    <td>
      更适合低VDD
    </td>
  </tr>
  
  <tr>
    <td>
      输入共模范围 ICMR
    </td>
    
    <td>
      较窄
    </td>
    
    <td>
      较宽
    </td>
  </tr>
  
  <tr>
    <td>
      功耗（同指标）
    </td>
    
    <td>
      通常更低
    </td>
    
    <td>
      通常更高
    </td>
  </tr>
  
  <tr>
    <td>
      噪声（同电流/同gm）
    </td>
    
    <td>
      通常更低
    </td>
    
    <td>
      通常更高一点
    </td>
  </tr>
  
  <tr>
    <td>
      何时选
    </td>
    
    <td>
      VDD够高、追求高增益/高速/低功耗
    </td>
    
    <td>
      VDD偏低或要大摆幅/宽共模
    </td>
  </tr>
</tbody>
</table>
3. 光刻工艺干嘛的
  - 把掩膜版上的信息转移到wafer上，<mark>
  
  教材P635
  
  </mark>
4. 共模响应的特性(与版图匹配有关)
  - P658 版图与封装--对称性 考虑两件事情
  
    1. 栅阴影导致源、漏不对称，对称性好 共模响应才能好
    ![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/FinalExamReview-06.webp)
    2. 为了减小场氧的影响，加入Dummy管来增强对称性
    ![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/FinalExamReview-07.webp)<br />

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/FinalExamReview-08.webp)
5. 理想运放的输入电阻

> 输入电阻无穷大

1. 尺寸减小，本征增益如何变化——变小

> 课本P618

1. 短沟道效应(SCE):迁移率和温度有关，高压下的速度饱和效应等

> 迁移率和温度没见拉扎维提过 🤔
> 
> 微电子器件还在追我😠

1. 两种电流镜结构的特性（哪个精准跟随电流，哪个最小裕度电压）

> P128页两个电流镜结构，左侧这个最小余度电压，右边这个精准跟随电流
> 
> ![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/FinalExamReview-09.webp)

1. 电流镜的偏置电压多少保证管子刚好饱和
2. 稳定结构的特性（GX与PX哪个超前）、precede是什么意思

> PX > GX  ;     precede处在……之前

1. 电容版图哪个更好(中文书669页例题)

> 考虑对称性与dummy问题
> 
> ![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/FinalExamReview-10.webp)

### 21-22

1. 下列哪一项是共栅级的特征：电流缓冲器/高输入电阻/电压跟随器

> 电流缓冲器

1. 下图中运放的输入电阻为：无穷/R/2R/0
2. 考虑体效应，当衬底电压增加时，阈值电压：增加/减小/不变

> NMOS 变小
> 
> PMOS 变得更负，绝对值变大

1. 下列关于光刻的描述错误的是：

  1. 版图由代表不同类型“层”的多边形组成
  2. 光刻是把电路板图信息从晶片上转移到掩模版上
  3. 光刻胶有两种，正胶和负胶

> **b反了** 把电路板图信息从**掩模版**上转移到**晶片**上

1. 下列关于掺杂的描述错误的是：

  1. 掺杂之后不需要进行退火
  2. 掺杂有扩散和离子注入两种

> 肯定是a  需要退火 教材P638 ，<mark>
> 
> **注意好像教材上没有提到扩散，但扩散是掺杂方法**
> 
> </mark>

1. 关于Cascode特性

  1. Cascode的屏蔽效应， 见教材P126最底下一行字
  2. 其他特性见表格
2. 下列放大器中输入电阻最小的是：CS/CG/CD/Cascode

> CG 共栅

1. 根据按比例缩小理论，随着尺寸的缩小，本征增益：变大/变小/不变

> 变小

1. PMOS的衬底应该接到：浮动电压/最高电压/地

> 最高电压

1. 下列关于载流子迁移率的描述错误的是：
2. 载流子迁移率与温度无关
3. 速度饱和时会发生迁移流程退化

> 选a 味大无需多言，wxtr味真大

1. 下列关于相位裕度描述错误的是
2. 单极点系统无条件稳定
3. 两极点系统稳定的条件为PX比GX小

> 选b   PX > GX  才稳定

### MOSFET 三大基本拓扑对比表

> 默认：中频小信号模型；栅极电流≈0；负载为 <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msub>
> <mi>
> 
> R
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
> R_L
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
> <span className="mord,mathnormal" style="margin-right:0.0077em;">
> 
> R
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3283em;">
> <span style="top:-2.55em;margin-left:-0.0077em;margin-right:0.05em;">
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
> ；晶体管输出电阻 <span className="katex">
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
> o
> 
> </mi>
> </msub>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> r_o
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
> <span className="mord,mathnormal" style="margin-right:0.0278em;">
> 
> r
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.1514em;">
> <span style="top:-2.55em;margin-left:-0.0278em;margin-right:0.05em;">
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
> </span>
> </span>
> </span>
> 
> ；体效应用 <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msub>
> <mi>
> 
> g
> 
> </mi>
> 
> <mrow>
> <mi>
> 
> m
> 
> </mi>
> 
> <mi>
> 
> b
> 
> </mi>
> </mrow>
> </msub>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> g_{mb}
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
> <span className="mord">
> <span className="mord,mathnormal" style="margin-right:0.0359em;">
> 
> g
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
> <span className="mord,mtight">
> <span className="mord,mathnormal,mtight">
> 
> mb
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
>  表示（不考虑时令 <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msub>
> <mi>
> 
> g
> 
> </mi>
> 
> <mrow>
> <mi>
> 
> m
> 
> </mi>
> 
> <mi>
> 
> b
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
> 0
> 
> </mn>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> g_{mb}=0
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
> <span className="mord">
> <span className="mord,mathnormal" style="margin-right:0.0359em;">
> 
> g
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
> <span className="mord,mtight">
> <span className="mord,mathnormal,mtight">
> 
> mb
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
> <span className="strut" style="height:0.6444em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> 
> 0
> 
> </span>
> </span>
> </span>
> </span>
> 
> ）。偏置分压/栅极电阻等统称为 <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msub>
> <mi>
> 
> R
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
> R_G
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
> <span className="mord,mathnormal" style="margin-right:0.0077em;">
> 
> R
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3283em;">
> <span style="top:-2.55em;margin-left:-0.0077em;margin-right:0.05em;">
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

<table>
<thead>
  <tr>
    <th>
      拓扑 Topology
    </th>
    
    <th>
      输入端 Input node
    </th>
    
    <th>
      输出端 Output node
    </th>
    
    <th>
      相位 Phase
    </th>
    
    <th>
      输入阻抗 R_in
    </th>
    
    <th>
      输出阻抗 R_out
    </th>
    
    <th>
      电压增益 A_v (近似)
    </th>
    
    <th>
      典型用途 Typical use
    </th>
    
    <th>
      关键备注 Notes
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      共源 CS (Common Source)
    </td>
    
    <td>
      栅极 Gate
    </td>
    
    <td>
      漏极 Drain
    </td>
    
    <td>
      反相(180°)
    </td>
    
    <td>
      R_in ≈ R_G (理想趋于∞，由偏置电阻主导)
    </td>
    
    <td>
      R_out ≈ R_D // r_o (再与R_L并联)
    </td>
    
    <td>
      A_v ≈ -g_m × (R_D // r_o // R_L)
    </td>
    
    <td>
      电压放大主力级
    </td>
    
    <td>
      有Miller效应：输入电容被放大，带宽可能下降
    </td>
  </tr>
  
  <tr>
    <td>
      共栅 CG (Common Gate)
    </td>
    
    <td>
      源极 Source
    </td>
    
    <td>
      漏极 Drain
    </td>
    
    <td>
      同相(0°)
    </td>
    
    <td>
      R_in ≈ 1/(g_m + g_mb) (常为低阻)
    </td>
    
    <td>
      R_out ≈ R_D // r_o (再与R_L并联)
    </td>
    
    <td>
      A_v ≈ +g_m × (R_D // r_o // R_L)
    </td>
    
    <td>
      低输入阻抗、电流/宽带接口、阻抗匹配
    </td>
    
    <td>
      输入端几乎无Miller，常用于高频前端
    </td>
  </tr>
  
  <tr>
    <td>
      共漏 CD (Common Drain) / 源极跟随器（Source Follower）
    </td>
    
    <td>
      栅极 Gate
    </td>
    
    <td>
      源极 Source
    </td>
    
    <td>
      同相(0°)
    </td>
    
    <td>
      R_in ≈ R_G (很高)
    </td>
    
    <td>
      R_out ≈ (1/(g_m + g_mb)) // r_o (再考虑负载)
    </td>
    
    <td>
      A_v ≈ <span>
        g_m×(R_L // r_o)
      </span>
      
       / <span>
        1+(g_m+g_mb)×(R_L // r_o)
      </span>
      
       < 1 (常接近1)
    </td>
    
    <td>
      缓冲/阻抗变换(高入低出)
    </td>
    
    <td>
      电压增益最小，但驱动能力强、线性好一些
    </td>
  </tr>
</tbody>
</table>

## MOSFET 三大基本拓扑简化对比

<table>
<thead>
  <tr>
    <th>
      拓扑
    </th>
    
    <th>
      输入/输出
    </th>
    
    <th>
      相位
    </th>
    
    <th>
      电压增益
    </th>
    
    <th>
      典型用途
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      共源 CS
    </td>
    
    <td>
      栅极 Gate/漏极 Drain
    </td>
    
    <td>
      反相 180°
    </td>
    
    <td>
      高 (≈ -g_m R_D)
    </td>
    
    <td>
      电压放大主力
    </td>
  </tr>
  
  <tr>
    <td>
      共栅 CG
    </td>
    
    <td>
      源极 Source/漏极 Drain
    </td>
    
    <td>
      同相 0°
    </td>
    
    <td>
      中 (≈ +g_m R_D)
    </td>
    
    <td>
      高频/电流缓冲器
    </td>
  </tr>
  
  <tr>
    <td>
      共漏 CD
    </td>
    
    <td>
      栅极 Gate/源极 Source
    </td>
    
    <td>
      同相 0°
    </td>
    
    <td>
      ≈1 (跟随)
    </td>
    
    <td>
      阻抗变换/驱动/电压跟随器
    </td>
  </tr>
</tbody>
</table>

## 版图

### 24-25

（1）M1 和 M2 各自的宽和长都是多少（卷子上标了一些宽度的数据，这里没有）

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/FinalExamReview-11.webp)

（2）此图用了哪些技术来提高匹配；你有什么方案能进一步改进

> （2）一维交叉耦合对称版图，叉指晶体管；增加虚拟管或者浅槽隔离？

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/FinalExamReview-12.webp)

#### 版图设计的艺术

叉指晶体管

对称 symmetry

虚拟管 Dummy管

共中心版图

一维交叉耦合

浅槽隔离

阱临近效应

参考源的合理分布

## 大题

### 22-23

#### 3 五管OTA，两级运放

- 消除米勒补偿电容带来的零点，**见课本P384-385**
- 参考电流的差分管的宽度分别独立增大，SR和PM怎么变

> Is变大，SR变大，增益变大，GX变大，PM变小

#### 4 带隙基准

电源的启动问题，见课本P461和P469

### 21-22

#### 低压带隙基准

见课本P474-475

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/FinalExamReview-13.webp)

和前面的带隙基准有点区别，这个是两路正负温度系数的**电流**叠加导致的零温度系数。

### 两级运放

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/FinalExamReview-14.webp)

> Cc？不知道是哪个，如果按照输出端的电容的话

<mark>

**非常之重要——大概率是原题 请直接去ppt找 ⬇️**

</mark>



![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/FinalExamReview-15.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/FinalExamReview-16.webp)
