# Lecture 8：PN 结在光电领域的应用

> 基于 PN 结的光伏电池、太阳能电池 I-V 特性、太阳能光伏电池的四代技术

> 能量用的多->太阳能好啊用不完->利用率低，如何提高

## 基于 P-N 结的光伏 (PV) 电池 | P-N Junction-Based PV Cell

### 太阳能（光能）获取步骤

1. Photons are absorbed in the semiconductor resulting in the creation of electron-hole pairs | 光子在半导体中被吸收，从而产生**电子-空穴对**。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture8-01.webp)

1. The photo-generated electron-hole pairs are physically separated at the p/n junction | 光生电子-空穴对在 **p/n 结**处发生物理分离。（耗尽区的内建电场分离电子空穴）

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture8-02.webp)

1. The photogenerated carriers are collected by the contacts on the front and rear of the cell | 光生载流子被电池正面和背面的**接触电极**收集。
2. The photocurrent can be delivered to an external load at an applied voltage to perform useful work | **光电流**可以在一定的外加电压下输送到外部负载，从而做功。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture8-03.webp)

### 太阳能电池：基本要求 | Solar Cell: Basic Requirement

**转换效率**：包括光吸收、材料带隙、复合/输运以及接触电阻。

**可靠性**：包括环境稳定性以及使用寿命。

**热容**：热量会降低光伏效率（特别是对于单晶硅电池）。

> **Conversion Efficiency**
> 
> - Light absorption
> - Material band-gap
> - Recombination/transportation
> - Contact
> 
> **Reliability**
> 
> - Environmental stability
> - Lifetime
> 
> **Heat Capacity**
> 
> - Heat degrades PV efficiency (especially for single crystalline silicon)

### 效率损失机制 | Efficiency loss mechanism

- thermal loss

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

p

</mi>

<mi>

h

</mi>
</mrow>
</msub>

<mo>

>
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

E_{ph} > E_g

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
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.0576em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

p

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

>
</span>

<span className="mspace" style="margin-right:0.2778em;">



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

时，多余能量以热能散失

- junction loss

电池输出的电压无法达到理论上的最大值

- contact loss

欧姆接触损失的能量

- recombination loss

未收集就复合了

### 太阳光谱 | solar spectrum

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 53.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture8-04.webp" />
      </p>
    </td>
    
    
      <td style="width: 46.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture8-05.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

<alert type="tip">

具有<mark>

固定带隙

</mark>

的半导体光伏（PV）电池仅能转换太阳光谱中一部分的能量 |A semiconductor PV cell with fixed band-gap only convertsenergy in a portion of solar spectrum

</alert>

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mtext>

Photon Energy (eV)

</mtext>

<mo>

=

</mo>

<mfrac>
<mrow>
<mi>

h

</mi>

<mi>

c

</mi>
</mrow>

<mi>

λ

</mi>
</mfrac>

<mo>

=

</mo>

<mfrac>
<mn>

1.24

</mn>

<mrow>
<mi>

λ

</mi>

<mo stretchy="false">

(

</mo>

<mi>

μ

</mi>

<mtext>

m

</mtext>

<mo stretchy="false">

)

</mo>
</mrow>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

\text{Photon Energy (eV)} = \frac{hc}{\lambda} = \frac{1.24}{\lambda (\mu\text{m})}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord,text">
<span className="mord">

Photon Energy (eV)

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

λ

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

h

</span>

<span className="mord,mathnormal">

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
<span className="mord,mathnormal">

λ

</span>

<span className="mopen">

(

</span>

<span className="mord,mathnormal">

μ

</span>

<span className="mord,text">
<span className="mord">

m

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

1.24

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

只有当光子能量大于<span className="katex">
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

时，即<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mfrac>
<mrow>
<mi>

h

</mi>

<mi>

c

</mi>
</mrow>

<mi>

λ

</mi>
</mfrac>

<mo>

>
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

\frac{hc}{\lambda}>E_g

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

λ

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

h

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

>
</span>

<span className="mspace" style="margin-right:0.2778em;">



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

，光子才能被吸收

<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

λ

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
<mrow>
<mi>

h

</mi>

<mi>

c

</mi>
</mrow>

<msub>
<mi>

E

</mi>

<mi>

g

</mi>
</msub>
</mfrac>

<mo>

=

</mo>

<mfrac>
<mn>

1.24

</mn>

<msub>
<mi>

E

</mi>

<mi>

g

</mi>
</msub>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

\lambda_{max}=\frac{hc}{E_g}=\frac{1.24}{E_g}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8444em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

λ

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
<span className="strut" style="height:1.4224em;vertical-align:-0.5423em;">



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

h

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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.3874em;vertical-align:-0.5423em;">



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

1.24

</span>
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

可以求到最大能够吸收的光的波长

### 光吸收 | light absorption

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture8-06.webp)

#### 核心物理概念 <span className="katex">
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



- 光强衰减规律：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mtext>

Light intensity

</mtext>

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

α

</mi>

<mi>

x

</mi>
</mrow>
</msup>
</mrow>

<annotation encoding="application/x-tex">

\text{Light intensity }(x) \propto e^{-\alpha x}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord,text">
<span className="mord">

Light intensity

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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

∝

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8213em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

e

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8213em;">
<span style="top:-3.113em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">

−

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0037em;">

α

</span>

<span className="mord,mathnormal,mtight">

x

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

这表示光进入材料后，强度随深度 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

x

</mi>
</mrow>

<annotation encoding="application/x-tex">

x

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
</span>
</span>
</span>

 呈指数衰减。

- 吸收系数 (<span className="katex">
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

)：

单位是 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msup>
<mtext>

cm

</mtext>

<mrow>
<mo>

−

</mo>

<mn>

1

</mn>
</mrow>
</msup>
</mrow>

<annotation encoding="application/x-tex">

\text{cm}^{-1}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8141em;">



</span>

<span className="mord">
<span className="mord,text">
<span className="mord">

cm

</span>
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

1

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

。<span className="katex">
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

 越大，表示材料吸收光的能力越强，光衰减得越快。

- 光穿透深度 (Light penetration depth)：

定义为 <span className="katex">
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

<mi>

α

</mi>
</mrow>

<annotation encoding="application/x-tex">

1/\alpha

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

<span className="mord,mathnormal" style="margin-right:0.0037em;">

α

</span>
</span>
</span>
</span>

。它表示光强度衰减到入射强度的 <span className="katex">
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

<mi>

e

</mi>
</mrow>

<annotation encoding="application/x-tex">

1/e

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

<span className="mord,mathnormal">

e

</span>
</span>
</span>
</span>

（约 37%）时所穿透的距离。吸收系数越大，穿透深度越浅（光在表面就被吸收了）。

- 光子能量与波长的关系：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mtext>

Photon Energy (eV)

</mtext>

<mo>

=

</mo>

<mfrac>
<mrow>
<mi>

h

</mi>

<mi>

c

</mi>
</mrow>

<mi>

λ

</mi>
</mfrac>

<mo>

=

</mo>

<mfrac>
<mn>

1.24

</mn>

<mrow>
<mi>

λ

</mi>

<mo stretchy="false">

(

</mo>

<mi>

μ

</mi>

<mtext>

m

</mtext>

<mo stretchy="false">

)

</mo>
</mrow>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

\text{Photon Energy (eV)} = \frac{hc}{\lambda} = \frac{1.24}{\lambda (\mu\text{m})}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord,text">
<span className="mord">

Photon Energy (eV)

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

λ

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

h

</span>

<span className="mord,mathnormal">

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
<span className="mord,mathnormal">

λ

</span>

<span className="mopen">

(

</span>

<span className="mord,mathnormal">

μ

</span>

<span className="mord,text">
<span className="mord">

m

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

1.24

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

这是一个非常实用的工程公式。它说明光子能量（eV）与波长（<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

μ

</mi>

<mtext>

m

</mtext>
</mrow>

<annotation encoding="application/x-tex">

\mu\text{m}

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

<span className="mord,text">
<span className="mord">

m

</span>
</span>
</span>
</span>
</span>

）成反比。波长越短，能量越高。

#### 图表分析

**关键观察：**

- **GaAs, InP (直接带隙半导体)：** 我们可以看到 GaAs 的曲线在达到带隙能量（约 1.42 eV）后，吸收系数**急剧上升**（几乎是垂直的）。这意味着一旦光子能量足够，它们能极快地吸收光子。
- **Si (间接带隙半导体)：** 硅的曲线虽然也上升，但显得比较**平缓**。这意味着硅在带隙附近的吸光能力较弱，需要更厚的材料才能充分吸收光。

#### 核心结论

> *"A thinner layer of direct-gap semiconductor can absorb most of solar radiation than indirect-gap semiconductor."*

这句话总结了这张图的实际应用意义：

- **直接带隙半导体 (Direct-gap, 如 GaAs)：** 吸光效率非常高。因此，在制造太阳能电池或光电探测器时，只需要**很薄的一层**材料（几微米甚至更薄）就能吸收大部分太阳光。
- **间接带隙半导体 (Indirect-gap, 如 Si)：** 吸光效率较低（因为电子跃迁需要声子的参与，概率较低）。因此，硅基太阳能电池通常需要**较厚**的硅片（通常为几百微米）才能保证足够的光吸收。

### 直接带隙间接带隙  | direct indirect-gap

- 直接带隙<span className="katex">
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

 大
- 间接带隙<span className="katex">
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

 小

## 太阳能电池的 I-V 特性  |Solar Cell I-V Characteristics

### 机制

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture8-07.webp)

#### 物理机制（左上图）

**Light (光照):** 光从左侧射入。

**Short Circuit (短路):** 电池的两端（N区和P区）被一根导线直接连接。在这种情况下，电压 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

V

</mi>

<mo>

=

</mo>

<mn>

0

</mn>
</mrow>

<annotation encoding="application/x-tex">

V=0

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



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
<span className="strut" style="height:0.6444em;">



</span>

<span className="mord">

0

</span>
</span>
</span>
</span>

，电路中流过的电流被称为**短路电流 (**<span className="katex">
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

s

</mi>

<mi>

c

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

I_{sc}

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

sc

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

**)**。

#### 核心方程:

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

<msub>
<mi>

I

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

<mo>

−

</mo>

<msub>
<mi>

I

</mi>

<mrow>
<mi>

s

</mi>

<mi>

c

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

I = I_0(e^{qV/kT} - 1) - I_{sc}

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
<span className="strut" style="height:1.188em;vertical-align:-0.25em;">



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
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0785em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

sc

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
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

I

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

I_0(e^{qV/kT}-1)

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.138em;vertical-align:-0.25em;">



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

: **二极管电流**（暗电流）。它随电压 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

V

</mi>
</mrow>

<annotation encoding="application/x-tex">

V

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.2222em;">

V

</span>
</span>
</span>
</span>

 指数增加。
- <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mo>

−

</mo>

<msub>
<mi>

I

</mi>

<mrow>
<mi>

s

</mi>

<mi>

c

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

-I_{sc}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">

−

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

sc

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

: **光生电流**。这一项是负值，表示光照产生的电流方向与二极管正向导通电流方向相反。正是这一项让曲线向下平移。

> 可以将暗电流理解为PN结发电的损失

#### 关键定义

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

s

</mi>

<mi>

c

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

I_{sc}

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

sc

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

 **(Short-circuit current): 短路电流**。即当电压 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

V

</mi>

<mo>

=

</mo>

<mn>

0

</mn>
</mrow>

<annotation encoding="application/x-tex">

V=0

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



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
<span className="strut" style="height:0.6444em;">



</span>

<span className="mord">

0

</span>
</span>
</span>
</span>

 时流过的电流（对应图中曲线与 Y 轴的交点，值为 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mo>

−

</mo>

<msub>
<mi>

I

</mi>

<mrow>
<mi>

s

</mi>

<mi>

c

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

-I_{sc}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">

−

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

sc

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

）。它主要取决于光照强度和材料的吸光能力。

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

o

</mi>

<mi>

c

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

V_{oc}

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
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

oc

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

 **(Open-circuit voltage): 开路电压**。即当电流 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

I

</mi>

<mo>

=

</mo>

<mn>

0

</mn>
</mrow>

<annotation encoding="application/x-tex">

I=0

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
<span className="strut" style="height:0.6444em;">



</span>

<span className="mord">

0

</span>
</span>
</span>
</span>

 时电池两端的电压（对应图中曲线与 X 轴的交点）。这是太阳能电池如果不接负载时能产生的最大电压。

**总结：光照产生了一个恒定的光生电流 (**<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mo>

−

</mo>

<msub>
<mi>

I

</mi>

<mrow>
<mi>

s

</mi>

<mi>

c

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

-I_{sc}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">

−

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

sc

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

**)，这个电流叠加在普通的二极管 I-V 曲线上，使其向下平移，从而使器件具备了发电能力（在** <span className="katex">
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

o

</mi>

<mi>

c

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

V_{oc}

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
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

oc

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



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
<mn>

0

</mn>
</mrow>

<annotation encoding="application/x-tex">

0

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
</span>
</span>
</span>

 **之间工作时输出功率）**

### 太阳能电池的效率

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture8-08.webp)

- 填充因子

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

F

</mi>

<mi>

F

</mi>

<mo>

=

</mo>

<mfrac>
<mtext>

实际最大功率

</mtext>

<mtext>

理论极限功率

</mtext>
</mfrac>

<mo>

=

</mo>

<mfrac>
<mrow>
<mo stretchy="false">

(

</mo>

<mi>

I

</mi>

<mo>

×

</mo>

<mi>

V

</mi>

<msub>
<mo stretchy="false">

)

</mo>

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
</mrow>

<mrow>
<msub>
<mi>

I

</mi>

<mrow>
<mi>

s

</mi>

<mi>

c

</mi>
</mrow>
</msub>

<mo>

×

</mo>

<msub>
<mi>

V

</mi>

<mrow>
<mi>

o

</mi>

<mi>

c

</mi>
</mrow>
</msub>
</mrow>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

FF = \frac{\text{实际最大功率}}{\text{理论极限功率}} = \frac{(I \times V)_{max}}{I_{sc} \times V_{oc}}

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
<span className="mord,text">
<span className="mord,cjk_fallback">

理论极限功率

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
<span className="mord,text">
<span className="mord,cjk_fallback">

实际最大功率

</span>
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
<span className="strut" style="height:2.263em;vertical-align:-0.836em;">



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

sc

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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
<span className="mord,mathnormal,mtight">

oc

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
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
<span className="mopen">

(

</span>

<span className="mord,mathnormal" style="margin-right:0.0785em;">

I

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

×

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.2222em;">

V

</span>

<span className="mclose">
<span className="mclose">

)

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

- 输出功率的计算公式

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mtext>

Output Power

</mtext>

<mo>

=

</mo>

<msub>
<mi>

I

</mi>

<mrow>
<mi>

s

</mi>

<mi>

c

</mi>
</mrow>
</msub>

<mo>

×

</mo>

<msub>
<mi>

V

</mi>

<mrow>
<mi>

o

</mi>

<mi>

c

</mi>
</mrow>
</msub>

<mo>

×

</mo>

<mi>

F

</mi>

<mi>

F

</mi>
</mrow>

<annotation encoding="application/x-tex">

\text{Output Power} = I_{sc} \times V_{oc} \times FF

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8778em;vertical-align:-0.1944em;">



</span>

<span className="mord,text">
<span className="mord">

Output Power

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

sc

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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
<span className="mord,mathnormal,mtight">

oc

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

F

</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

F

</span>
</span>
</span>
</span>
</span>

- 太阳能电池效率 (<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

η

</mi>
</mrow>

<annotation encoding="application/x-tex">

\eta

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.625em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

η

</span>
</span>
</span>
</span>

)

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

η

</mi>

<mo>

=

</mo>

<mfrac>
<mrow>
<mo stretchy="false">

(

</mo>

<mi>

I

</mi>

<mo>

×

</mo>

<mi>

V

</mi>

<msub>
<mo stretchy="false">

)

</mo>

<mtext>

max

</mtext>
</msub>
</mrow>

<mtext>

input solar power

</mtext>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

\eta = \frac{(I \times V)_{\text{max}}}{\text{input solar power}}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.625em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

η

</span>

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
<span className="mord,text">
<span className="mord">

input solar power

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
<span className="mopen">

(

</span>

<span className="mord,mathnormal" style="margin-right:0.0785em;">

I

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

×

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.2222em;">

V

</span>

<span className="mclose">
<span className="mclose">

)

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
<span className="mord,text,mtight">
<span className="mord,mtight">

max

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
</span>

### <span className="katex">
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

s

</mi>

<mi>

c

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

I_{sc}

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

sc

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

 和<span className="katex">
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

o

</mi>

<mi>

c

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

V_{oc}

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
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

oc

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

 推导

> 这里的推导和PN结很像，应该不会考，直接给出结论

- <span className="katex">
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

<mi>

A

</mi>

<mi>

q

</mi>

<msub>
<mi>

L

</mi>

<mi>

p

</mi>
</msub>

<mi>

G

</mi>
</mrow>

<annotation encoding="application/x-tex">

I_{sc} = A q L_p G

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

sc

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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

<span className="mord,mathnormal">

A

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

q

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

<span className="mord,mathnormal">

G

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
  
   : 光生载流子产生率
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
  
  : 扩散长度

G是不均匀的，材料的扩散长度 <span className="katex">
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

 必须足够大（大于光的穿透深度），这样光生载流子才能在死掉（复合）之前跑到 PN 结被收集起来。

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

o

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

τ

</mi>

<mi>

p

</mi>
</msub>

<mi>

G

</mi>

<msub>
<mi>

N

</mi>

<mi>

d

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

V_{oc} = \frac{kT}{q} \ln\left(\frac{\tau_p G N_d}{n_i^2}\right)

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
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

oc

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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

<span className="mop">

ln

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
<span style="top:-2.6264em;">
<span className="pstrut" style="height:3em;">



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
<span className="vlist" style="height:0.8051em;">
<span style="top:-2.1777em;margin-left:0em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
<span className="mord,mathnormal,mtight">

i

</span>
</span>
</span>

<span style="top:-2.8448em;margin-right:0.0714em;">
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
<span className="vlist" style="height:0.3223em;">
<span>



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

<span className="mord,mathnormal,mtight">

G

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
<span className="vlist" style="height:0.5992em;">
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


  - <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
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
  
  \tau_p
  
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
  
  : 少子寿命

<alert type="question">

**如何提高** <span className="katex">
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

o

</mi>

<mi>

c

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

V_{oc}

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
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

oc

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

**？**

1. **增加** <span className="katex">
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

：光照越强，电压越高（对数增长）。
2. **增加** <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
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

N_d

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

：提高掺杂浓度。
3. **增加** <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
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

\tau_p

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

：提高少子寿命（即提高材料质量，减少缺陷）。
4. **减小** <span className="katex">
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

：这通常意味着使用禁带宽度 (<span className="katex">
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

) 更大的材料（因为 <span className="katex">
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

 与 <span className="katex">
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

 呈指数反比关系）。

</alert>

### 小结

1. **硅太阳能电池**目前以 15-20% 的效率占据市场主导地位。
2. **理论上**，当禁带宽度在 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mn>

1.2

</mn>

<mtext>

eV

</mtext>
</mrow>

<annotation encoding="application/x-tex">

1.2 \text{ eV}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord">

1.2

</span>

<span className="mord,text">
<span className="mord">

eV

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
<mn>

1.9

</mn>

<mtext>

eV

</mtext>
</mrow>

<annotation encoding="application/x-tex">

1.9 \text{ eV}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord">

1.9

</span>

<span className="mord,text">
<span className="mord">

eV

</span>
</span>
</span>
</span>
</span>

 之间时，可以获得最高效率（约 24%）。

- 禁带宽度 (<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
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

E_G

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

) 过大：会导致光吸收率过低，从而使短路电流 (<span className="katex">
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

s

</mi>

<mi>

c

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

I_{sc}

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

sc

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

) 太小。

原因：只有能量 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

h

</mi>

<mi>

ν

</mi>

<mo>

>
</mo>

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

h\nu > E_G

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.7335em;vertical-align:-0.0391em;">



</span>

<span className="mord,mathnormal">

h

</span>

<span className="mord,mathnormal" style="margin-right:0.0637em;">

ν

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

 的光子才能被吸收。如果<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
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

E_G

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

 太高，大部分太阳光（能量较低的部分）都无法被吸收，直接穿透过去了，导致光生电流很小。

- 禁带宽度 (<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
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

E_G

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

) 过小：会导致开路电压 (<span className="katex">
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

o

</mi>

<mi>

c

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

V_{oc}

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
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

oc

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

) 太低。

原因：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
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

E_G

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

小， <span className="katex">
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

大，根据上述的式子，<span className="katex">
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

o

</mi>

<mi>

c

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

V_{oc}

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
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

oc

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

小 。或者可以理解成，带隙越小，内建电势差就越小，导致输出电压上不去。虽然吸收的光多了，但每个电子携带的能量（电压）很低。

1. **叠层太阳能电池 (Tandem solar cells)** 通过使用针对太阳光中短波长和长波长定制的大带隙和小带隙材料，可以获得 35% 的效率。

## 太阳能光伏（PV）电池的四代技术 | Four Generations of Solar PV Cell

> 感觉这个**发展历程**了解就行吧

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture8-09.webp)

> 翻译上述内容

**早期工作**

- 1839 年：发现阳光照射在固体材料上可以产生电流
- 1921 年：爱因斯坦因解释光伏（PV）效应而获得诺贝尔奖
- 1941 年：第一块太阳能电池被发明

**技术代际：**

- **第一代（自 20 世纪 70 年代起）**
  - 晶体硅（Si）光伏技术
  
    - 单晶硅、多晶硅、（此处写作）多晶/聚晶硅
- **第二代（自 20 世纪 80 年代中期起）**
  - 无机薄膜半导体
  
    - 非晶硅（a-Si）、多晶硅薄膜（poly-Si）、碲化镉（CdTe）、CIS/CIGS（铜铟硒/铜铟镓硒）、III-V 族化合物半导体
- **第三代（开始进入市场）**
  - 有机/聚合物与纳米技术路线
  
    - 染料敏化、纳米晶/量子点、给体-受体异质结
- **第四代（to come）**
  - 从生物学汲取灵感

### **主要光伏（PV）机理 | Major PV Mechanisms**

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture8-10.webp)

> 翻译上面内容

- 旧机理：半导体 **P-N 结**（**第一代与第二代**）

  - 晶体硅 **c-Si**、非晶硅 **a-Si**、多晶硅 **poly-Si**
  - **III-V** 族化合物半导体
  - **CdTe**（碲化镉）
  - **CIS/CIGS**（铜铟硒 / 铜铟镓硒）
- 新机理：**给体-受体（D-A）结**（**第三代——纳米技术**）

  - 塑料、有机聚合物
  - 分子（材料）

### 第一代：晶体硅（Si）光伏电池

#### **块体/晶圆型 vs 薄膜型光伏电池 | Bulk vs. Thin-Film PV Cells**

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture8-11.webp)

**块体晶圆型（Bulk Wafer）光伏电池**以一整片较厚的晶体**硅晶圆**为主体，在晶圆内部形成 P-N 结。光照进入硅体后产生电子-空穴对，由结区内建电场分离载流子，电流通过金属电极与外电路输出。它的典型特征是结构较厚、材料**用量较大**、工艺偏“**晶圆加工**”，整体技术成熟、**稳定性强**。

**薄膜型（Thin-Film）光伏电池**不靠厚晶圆，而是把**功能材料一层层沉积在基底**上（如玻璃等），形成包括盖板、减反层、集电电极、P/N 型半导体层和背电极等“层状堆叠”结构，同样依靠结区/界面完成载流子分离并输出电流。它的典型特征是结构更**薄**、材料**用量更少**、可实现**大面积**与多种基底形态（更灵活），但不同薄膜体系在效率与稳定性上与晶圆硅路线各有取舍。

#### 高效率硅太阳电池 | High-Efficiency Silicon PV Cell

为了把硅电池效率做高，需要同时从**光学吸收、载流子复合损失、以及电极遮挡/电阻损失**三方面进行优化。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture8-12.webp)

1. **表面织构增强“陷光” | Texture surface design to enhance light trapping**
上表面做成类似“倒金字塔（inverted pyramids）”的微结构。**作用**：让入射光在表面多次反射、路径变长，**减少反射、增加吸收**，等于“把光留在电池里更久”。
2. **表面钝化 | Surface passivation**
表面会有缺陷/悬挂键，容易让电子-空穴复合，造成损失。通过在表面覆盖 **氧化层/钝化层**，减少表面复合，提升载流子寿命，从而提高电压与效率。
3. **背接触减少遮挡损失 | Back contacts to prevent shading losses**

传统电池正面有金属栅线，会遮住部分光（shading loss）。因此把电极尽量放到背面（rear contact / back contact），**正面更干净**，能接收更多光。

1. **实验室最佳效率约 25% | Efficiency: best 25% (lab)**

### 第二代：薄膜/柔性光伏（PV）电池 | 2nd Generation: Thin-Film/Flexible PV

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture8-13.webp)

> 翻译如图

**成本、重量与柔性**

用料更少（厚度 **1–10 微米**）；可进行大面积制程；可用柔性/可弯曲基底（玻璃、不锈钢或塑料）。

**材料（无机半导体）**

非晶硅 a-Si、多晶硅 poly-Si、III-V 族（GeAs、InN）、碲化镉 CdTe、CIS/CIGS（铜铟硒 / 铜铟镓硒）

**制造工艺**

物理气相沉积、化学气相沉积、电化学沉积、卷对卷印刷（roll-to-roll）

**市场**

不仅进入传统市场（屋顶光伏），同时也创造新应用：建筑一体化产品，消费电子（手机等），一次性电子产品。

#### 薄膜非晶硅光伏电池 |Thin-Film Amorphous Silicon PV Cell

**非晶硅薄膜电池**用**气体沉积薄膜**的方式减少对硅晶圆的依赖，从而降低成本、支持大面积/柔性形态；代价是单结效率通常较低，但它在温度变化下的发电表现更稳定。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture8-14.webp)

> 翻译

**降低光伏成本的方法**

以 **SiH₄（硅烷）气体**作为硅源，不与半导体行业争夺**硅晶圆**资源。

**特点**

- 缺点：光伏效率较低：单结电池通常只有 **6%～8%**
- 优点：对发热/温度不太敏感：发电更稳定、更一致

#### 硅太阳电池效率 | Silicon Cell Efficiency

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture8-15.webp)

上述表格把硅电池按材料分成三类：**单晶硅、多晶硅、非晶硅。**整体效率大小关系是**单晶硅 > 多晶硅 > 非晶硅**。

**实验室效率**通常来自小面积、工艺精细、材料质量高、测试与封装条件受控的样品，因此能逼近材料/结构的上限。**量产效率**需要考虑：大面积均匀性、成本约束、缺陷与杂质控制难度、电极/封装带来的额外损失、生产良率等，所以通常**低于**实验室记录。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture8-16.webp)

**在太阳光下**：太阳光包含大量近红外能量，而 **c-Si（晶体硅）**的响应范围更宽，能延伸到**更长的近红外波段**，所以更适合做高效率的户外发电。

**在室内光/荧光灯下**：室内光谱更偏可见光、且与人眼亮度敏感区更接近；**a-Si（非晶硅）**的响应也更集中在可见光，因此在一些低照度/室内供电的小功率场景（例如小型电子、计算器等）往往更更适合，但是它在标准太阳光下的**面积效率**不如晶体硅。

#### 其他材料：带隙与效率 | Other Materials: Band-Gap & Efficiency

**约 1.4 eV 的带隙**与太阳光谱强度最强的那部分光子的能量相匹配，而**硅**的带隙是 **1.1 eV**，并非最优；但由于晶体质量高，仍能实现较高效率（**14–17%**），下面介绍其他材料的带隙和效率。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture8-17.webp)

> 纯了解吧，要考的话，scy吃粑粑

**砷化镓（GaAs）**

- 带隙：**1.4 eV**（处在最优范围）
- 效率：**>30%**

**碲化镉（Cadmium Telluride, CdTe）**

- 带隙：**1.5 eV**
- 效率：**8–10%**

**Cu(InGe)Se₂（铜铟锗硒，常见同族为 CIGS/CIS 路线）**

- 带隙：可变 **1.0–1.2 eV**
- 效率：**9–11%**
- 抗辐照能力强

**In₁₋ₓGaₓN（铟镓氮，可调组分合金）**

- 带隙：**0.7–3.4 eV（可调）**
  - 这意味着可以用**多层结构去吸收不同波长**的光，并且晶体结构**不会失配**（不容易出现晶格不匹配问题）

#### 结结构 | Junction Structure

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 70.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture8-18.webp" />
      </p>
    </td>
    
    
      <td style="width: 29.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture8-19.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

1. **同质结（Homo-junction）**
指**同一种半导体材料内部**形成的结（最典型就是同一块硅里做 p 区和 n 区形成 p–n 结）。**应用案例**：晶体硅（c-Si）太阳电池。
2. **异质结（Hetero-junction）**
指由**两种不同半导体材料**接触形成的结（材料不同，带隙/能带结构不同）。**应用案例**：CdS/CdTe、CdS/CIGS 太阳电池
3. **p-i-n 与 n-i-p 结**
在 p 与 n 之间加入一层**本征层 i（intrinsic）**，形成 **p-i-n**；反过来沉积顺序也可以是 **n-i-p**。这种结构在薄膜材料（尤其是 **a-Si 非晶硅**）很常见：因为薄膜里缺陷多、载流子寿命短，用 i 层和较强内建电场来帮助光生载流子的产生，降低复合损失。**应用案例**：非晶硅（a-Si）、多晶硅（poly-Si）太阳电池。
4. **多结（Multi-junction）**
把多个“子电池”**垂直叠层**，每一层用不同带隙材料，分别吸收太阳光谱的不同部分。（见上右图）。**应用案例**：III-V、a-Si、CIS 太阳电池。

单结电池只能用一个带隙：要么吸不到低能光（**透过损失**），要么高能光多余能量变热（**热化损失**）。

多结通过分层吸收（**光谱分割**），能同时减少这两类损失，所以整体效率更高。

#### III-V 族半导体光伏电池 | III-V Semiconductor PV Cells

**III-V 族半导体（如 GaAs、GaInP 等）太阳电池**的两种路线：**单结**与**多结（叠层）**。其中多结能更高效、但也更昂贵且对材料匹配要求更苛刻。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture8-20.webp)

**单结（Single Junction）**

- 最大理论效率约 **30%**；最佳实际水平约 **25%**。

**多结（Multi-Junction）**

- 两层：最大效率约 **50%**，最佳实际水平约 **30%**。
- 多层：若各层带隙差别较小并堆叠起来，可接近 **>70%** 的最大效率。
- 由于晶格/应变失配产生的晶体缺陷会严重降低效率。
- 成本高：适合航天或军事应用。

#### 最高效率光伏电池 | Highest Efficiency PV Cell

> 了解

**最高效率的光伏电池通常来自 III-V 族材料的多结（叠层）设计**，通过“光谱分割”让不同带隙的子电池各自负责吸收最适合的波段，从而显著提高总效率。

2005 年 7 月，Spectrolab 报道了当时效率最高的太阳电池：一款 **39.0% 的 GaInP₂/GaAs/Ge 三结（叠层）太阳电池**。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture8-21.webp)

#### “全光谱”光伏电池 | “Full-Spectrum” PV Cell

> 又双是一种电池

**用同一种材料体系 In₁₋ₓGaₓN（铟镓氮）做多结电池**。因为它的**带隙可通过组分 x 大范围可调（0.7～3.4 eV）**，理论上能覆盖从近红外到远紫外的太阳光子能量范围，从而把太阳光谱更充分地转成电能。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture8-22.webp)

**单一材料体系——铟镓氮（In₁₋ₓGaₓN）合金可覆盖太阳光谱中 0.7～3.4 eV 的能量范围（从近红外**到**远紫外**）。**两层**铟镓氮：一层将带隙调到 **1.7 eV**，另一层调到 **1.1 eV**，理论上可达到 **50%** 的最大效率，但是实际效率取决于载流子“组合/复合”等因素。

### 第三代：纳米技术光伏电池 | 3rd Generation: Nanotechnology

**优势：**可在分子尺度进行设计，重量轻，可柔性/可弯曲，材料与制造成本低，有望提高效率（但是仍需证明），环境影响较小。

**技术路线：**量子点（或纳米晶）光伏，聚合物光伏，染料敏化（或 Graetzel）光伏，纳米线/纳米管光伏，分子光伏。

**关键挑战：**可规模化生产、可控合成、对环境敏感、长期可靠性。

#### 用于太阳电池的量子点 | Quantum Dot for Solar Cell

**纳米尺度颗粒**在吸收光并产生电子方面具有巨大潜力。**原因** ：量子点是纳米级半导体晶体（纳米晶）。当尺寸小到一定程度，会出现**量子限域效应**：电子能级变得离散、带隙会随着尺寸变化而变化。这使得材料不再是**固定带隙**，而是**可设计带隙**，对太阳能吸收非常有吸引力。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture8-23.webp)

**吸收可调（可调带隙）**

带隙与量子点尺寸成反比，通过改变量子点尺寸，可以把光伏器件的吸收范围从红外调到可见光；高效的光-电转换既需要高电流也需要高电压，这其中存在一个对应最高转换效率的“最佳带隙”。

- 带隙大 —— 输出电压高
- 带隙小 —— 输出电流高，但输出电压低

**载流子倍增**

吸收一个光子可能产生 2 个甚至 3 个激发电子，最多可到 7 个（量子效应）。最早在硒化铅（PbSe）中观察到，随后在硒化镉（CdSe）、碲化镉（CdTe）中也观察到。

**陷光（光俘获）**

量子点/纳米材料往往可以做成**多散射、多孔或纳米结构层**，光进入后会在内部多次散射/反射，等效光程变长，从而在材料很薄的情况下也能提高吸收；有利于薄膜、柔性器件设计。（如上右图）

#### 中间能带光伏电池 | Intermediate-Band-gap PV Cell

在传统半导体的价带—导带之间，通过引入**量子点**等纳米结构形成一组“中间能级/中间能带”，从而让电池能吸收更多原本吸收不到的低能光子，提高对太阳光谱的利用率，理论效率上限非常高。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture8-24.webp)

在太阳能电池中使用量子点来形成**中间能带（intermediate bands）**，可以收集/利用太阳光谱中更大比例的能量。理论最高效率：**63.2%**（约为硅的 3 倍），其适用于**薄膜器件**（基于溶液的涂覆/印刷）。

#### 有机异质结太阳能电池 | Organic Hetero-junction Solar Cells

对于有机光伏两种异质结结构进行对比：

**双层结构**界面少，激子难到达界面导致损失。

**本体异质**结把界面“铺满整个体相”，更利于激子分离与电荷收集，因此通常更有潜力提高效率。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture8-25.webp)

当时该类有机异质结电池已达到的一个效率水平（3.5%）。

#### 量子点光伏（QD-PV）技术的挑战 | Challenge of QD-PV Technology

1. **对光的吸收能力差****解决方案：**量子点可以被构造成多种不同的形态，如：导电聚合物、溶胶-凝胶（sol-gel）或多孔薄膜
2. **量子点之间导电性差****解决方案：**提高导电性（使用高导电聚合物）；使用纳米线、纳米棒或碳纳米管来传导载流子。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture8-26.webp)

#### 红外（IR）太阳能电池 | Infrared (IR) Solar Cells

**用红外做太阳能电池的困难**

太阳光能量中有 **48%** 属于红外（波长：**700 nm～1 mm**），红外光子能量较低，因此不太容易在半导体中打出电子（激发产生载流子）。而带隙为 **0.025–0.05 eV** 的半导体在室温下会充满热激发载流子，这些载流子会把光生信号淹没，甚至把光生电流短路掉。为了压低热激发载流子，电池需要冷却到**液氮温度以下**才能工作。因此在室温下用**传统单结半导体**难以实现红外太阳能电池。

**可能实现的技术方向**

- 用量子点从红外光中提取能量（纳米材料）。
- 使用特殊的半导体材料（往往需要很多层）来利用更低能量的光子。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture8-27.webp)

### 第四代：生物光伏电池 | 4th Generation: Biological PV

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture8-28.webp)

PV=Photovoltaic 光伏

总结了以下左边那一大段文字，了解即可

> 1. 光对生命的重要性
> 
> 光合作用是地球生物圈能量的主要来源之一，所以研究“怎么高效用光”非常关键。
> 
> 1. 绿色来自叶绿素（Chlorophyll）
> 
> 植物看起来是绿色，是因为叶绿素参与吸收太阳光（它主要吸收红光/蓝光，反射绿色）。
> 
> 1. “集光装置”的结构：很多叶绿素被蛋白质“密集摆放”
> 
> 在蓝藻（cyanobacteria）里发现了一种**收集阳光的装置结构**（植物里也有类似机制），特点是：
> 
> - **多达 96 个叶绿素**
> - 被一个**蛋白质复合体**固定在**很近的距离**
> 
> 这相当于一个“光天线阵列”：用很多吸光分子把光尽可能抓住，再把能量集中输送。
> 
> 1. 能量传递到“中心叶绿素对”，并产生电荷分离
> 
> - 叶绿素先吸收光子 → 变成“激发态能量”
> - 这份能量会被“递送”到一个**中心的叶绿素对（类似反应中心）**
> - 反应中心把能量用来**驱动电子转移/形成跨膜电荷**
> → 于是产生类似电池的“电势差/电化学梯度”
> - 所以文字说它“像一个极其高效的生物太阳能电池”。
> 
> 1. 量子/理论分析：它很“鲁棒（fault tolerant）”
> 
> - **去掉（pruning）少量甚至多量叶绿素，效率影响不大** → 说明体系有冗余、抗损伤
> - **但如果改变叶绿素的空间排列**，效率会下降 → 说明“几何排布/耦合关系”对高效传能很关键
> - 因为自然环境光照强、损伤持续发生，所以这种鲁棒性对生物很重要。

### Light Emitting Diodes | 发光二极管

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture8-29.webp)

LEDs are made of **compound semiconductors** such as InP and GaN.

> 要高效率发光（把电能变成光，而不是热），材料最好是**“直接带隙”**的，而且带隙大小要能覆盖你想要的颜色/波长。
> 
> #### 直接带隙和间接带隙（<mark>
> 
> **Direct**
> 
> </mark>
> 
>  <mark>
> 
> **vs.**
> 
> </mark>
> 
>  <mark>
> 
> **Indirect Band Gap Materials**
> 
> </mark>
> 
> ）
> 
> ![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture8-30.webp)
> 
> ##### 直接带隙：
> 
> III V Group elements
> 
> <mark>
> 
> **Little change in momentum  is required for recombination-> momentum is conserved by photon emission(原文) Material：GaAs**
> 
> </mark>
> 
> 
> 
> 复合（过程）只需要很小的动量改变<span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <mo>
> 
> →
> 
> </mo>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> \rightarrow
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:0.3669em;">
> 
> 
> 
> </span>
> 
> <span className="mrel">
> 
> →
> 
> </span>
> </span>
> </span>
> </span>
> 
> 动量通过发射光子得以守恒
> 
> ##### 间接带隙：
> 
> Silicon、锗等
> 
> <mark>
> 
> **Large change in momentum is required for recombination ->momentum is conserved by phonon + photon emission（原文）Material：Si**
> 
> </mark>
> 
> 
> 
> 复合（过程）需要很大的动量改变<span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <mo>
> 
> →
> 
> </mo>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> \rightarrow
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:0.3669em;">
> 
> 
> 
> </span>
> 
> <span className="mrel">
> 
> →
> 
> </span>
> </span>
> </span>
> </span>
> 
>  动量通过声子和光子的发射得以守恒

Light is emitted when electron and hole undergo **radiative recombination**.

> 当电子和空穴发生**辐射复合(radiative recombination)**时，会把能量以光子(photon)的形式释放出来

然后注意看一下能带图，左边是**radiative recombination**，所以是可以发光的，但是右边是Non-radiative recombination through traps，是陷阱导致的非辐射复合，不发光

> - **陷阱能级（trap states）**：材料缺陷、杂质、位错等在禁带中引入的能级
> - 电子不是“一步到位”掉到价带，而是**先被陷阱捕获，再一步步往下**
> - 这过程中能量主要变成**晶格振动（声子）** → 通俗说就是**变成热**，而不是光

### LED Diode Structure

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture8-31.webp)

首先明确，基本的LED需要做成一个**PN结**的结构，并且**正向偏置**

<alert type="tip">

如果没有 p-n 结构，你很难在同一块材料里同时得到“高密度电子 + 高密度空穴”，更难把它们稳定地驱动到同一位置。

p-n 结在**正向偏置**时会发生“载流子注入”：

- n 区的电子被注入到 p 区一侧
- p 区的空穴被注入到 n 区一侧

于是，在结附近会形成一个区域：电子和空穴**同时很多** → 复合（包括辐射复合）概率就大。

就像右图中展示的这样：

- 黑点/小圆点可以理解为两类载流子：

  - **电子（electrons）**：主要在 n 区多
  - **空穴（holes）**：主要在 p 区多
- 中间那块区域（靠近结的地方）是关键：**p-n 结附近的复合区（有源区）**。

当 LED **正向偏置**时会发生：

- **电子从 n 区被“推”向 p 区**（跨过势垒注入到结附近）
- **空穴从 p 区被“推”向 n 区**
- 它们在结附近相遇并复合：

  - 如果是**辐射复合**：能量以**光子 photons**形式放出 → 图里“Emitted photons”的波浪箭头
  - 如果是**非辐射复合**：能量变成热（之前提到 traps 就是这类损耗来源）

</alert>

> 一个不是很重要的点：
> 
> 外面那个半圆形标了 **Lens（透镜）**：实际 LED 外面常见的透明“圆头”，通常是环氧/硅胶封装，起到：
> 
> 1. **保护芯片与引线**（机械保护、防潮等）
> 2. **改善出光（光提取效率）**：半球/透镜形状能把更多光从高折射率半导体里“导出来”，减少全反射造成的困光
> 3. **改变光束角**：让光更集中或更均匀（取决于透镜形状）

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

L

</mi>

<mi>

E

</mi>

<mi>

D

</mi>

<mi>

W

</mi>

<mi>

a

</mi>

<mi>

v

</mi>

<mi>

e

</mi>

<mi>

l

</mi>

<mi>

e

</mi>

<mi>

n

</mi>

<mi>

g

</mi>

<mi>

t

</mi>

<mi>

h

</mi>

<mtext>



</mtext>

<mi>

λ

</mi>

<mo stretchy="false">

(

</mo>

<mi>

μ

</mi>

<mi>

m

</mi>

<mo stretchy="false">

)

</mo>

<mo>

=

</mo>

<mfrac>
<mn>

1.24

</mn>

<mrow>
<mi>

p

</mi>

<mi>

h

</mi>

<mi>

o

</mi>

<mi>

t

</mi>

<mi>

o

</mi>

<mi>

n

</mi>

<mi>

e

</mi>

<mi>

n

</mi>

<mi>

e

</mi>

<mi>

r

</mi>

<mi>

g

</mi>

<mi>

y

</mi>
</mrow>
</mfrac>

<mo>

≈

</mo>

<mfrac>
<mn>

1.24

</mn>

<mrow>
<mi>

E

</mi>

<mi>

g

</mi>

<mo stretchy="false">

(

</mo>

<mi>

e

</mi>

<mi>

V

</mi>

<mo stretchy="false">

)

</mo>
</mrow>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

LED Wavelength \ \ λ(μm)=\frac{1.24}{photon energy}≈\frac{1.24}{Eg(eV)}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord,mathnormal">

L

</span>

<span className="mord,mathnormal" style="margin-right:0.0576em;">

E

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

D

</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

W

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

v

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal">

n

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

g

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal">

h

</span>

<span className="mspace">



</span>

<span className="mspace">



</span>

<span className="mord,mathnormal">

λ

</span>

<span className="mopen">

(

</span>

<span className="mord,mathnormal">

μ

</span>

<span className="mord,mathnormal">

m

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
<span className="mord,mathnormal">

p

</span>

<span className="mord,mathnormal">

h

</span>

<span className="mord,mathnormal">

o

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal">

o

</span>

<span className="mord,mathnormal">

n

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal">

n

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

er

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

g

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
<span className="mord">

1.24

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

≈

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
<span className="mord,mathnormal" style="margin-right:0.0576em;">

E

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

g

</span>

<span className="mopen">

(

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal" style="margin-right:0.2222em;">

V

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

1.24

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

> 来源就是最基本的光子能量公式：<span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <mi>
> 
> E
> 
> </mi>
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
> h
> 
> </mi>
> 
> <mi>
> 
> c
> 
> </mi>
> </mrow>
> 
> <mi>
> 
> λ
> 
> </mi>
> </mfrac>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> E=\frac{hc}{\lambda}
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
> <span className="mord,mathnormal" style="margin-right:0.0576em;">
> 
> E
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
> <span className="strut" style="height:1.2251em;vertical-align:-0.345em;">
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
> <span className="mord,mathnormal,mtight">
> 
> λ
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
> <span className="mord,mathnormal,mtight">
> 
> h
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

### LED Materials and Structure

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture8-32.webp)

左边的表格就是一些化合物半导体以及他们对应产生的光波长(总是应该不用记吧)

#### Compound Semiconductors | 化合物半导体的分类

##### Binary Semiconductors | 二元

- 例子：GaAs
- 材料本身性质固定（带隙、晶格常数基本固定），但很多二元材料是**直接带隙**，所以“efficient emitter”（发光效率高）

##### Ternary Semiconductors | 三元

- 例子：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

G

</mi>

<mi>

a

</mi>

<mi>

A

</mi>

<msub>
<mi>

s

</mi>

<mrow>
<mn>

1

</mn>

<mo>

−

</mo>

<mi>

x

</mi>
</mrow>
</msub>

<msub>
<mi>

P

</mi>

<mi>

x

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

GaAs_{1-x}P_x

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8917em;vertical-align:-0.2083em;">



</span>

<span className="mord,mathnormal">

G

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal">

A

</span>

<span className="mord">
<span className="mord,mathnormal">

s

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
<span className="mord,mtight">

1

</span>

<span className="mbin,mtight">

−

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
<span className="vlist" style="height:0.2083em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

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
- 这里的x是成分比例。改变x就能改变材料的：**带隙** <span className="katex">
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

 从而改变发光颜色/波长（很多 LED 的“调色”本质就是调合金成分）

##### Quaternary Semiconductors | 四元

- 例子：AlInGaP
- 优势是可以**同时调**：

  - **带隙** <span className="katex">
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
  
  （决定颜色）
  - **晶格常数**（决定能否与衬底匹配、外延质量）
- 四元材料允许你一边把颜色调到想要的波长，一边把晶格常数调到接近某个“便宜或成熟”的衬底，从而长出高质量外延薄膜（缺陷少 → 非辐射少 → 更亮）。

<alert type="tip">

上课强调过，由于Si是**间接带隙**材料，所以无法做LED

</alert>

### Common LEDs

一个更加系统的表格+一个画出能带里费米能级的图+LED的示意图

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture8-33.webp)

右下角图中的单词及概念：

> **Epoxy dome**：环氧树脂穹顶（就是你看到的透明头）
> 
> **Reflecting cup**：反射杯（把向下/侧向的光反射向外，提高出光）
> 
> **Lead**：引脚（电连接）

### Solid-State Lighting | 固态发光源

**luminosity (lumen, lm)**: a measure of visible light energy normalized to the sensitivity of the human eye at different wavelengths

<alert type="tip">

这里的 **luminosity** 更准确叫 **luminous flux（光通量）**，单位是 **流明 lumen（lm）**。

它的意思是：

- **lm 不是纯粹的“光能量”**（那是物理里的辐射功率 W）
- lm 是把光的能量按**人眼对不同波长的敏感程度**做了加权之后得到的“看起来有多亮”的量

直觉例子：

- 同样 1 W 的光学功率，如果是 **555 nm 绿光**，人眼最敏感 → 看起来特别亮（lm 很大）
- 如果是红外/深蓝，人眼不敏感 → 看起来暗（lm 很小，甚至接近 0）

> 所以：**lm 是“以人眼感觉为准的亮度指标”，不是“真实能量”指标。**

</alert>

Luminous efficacy of lamps in **lumen/watt**

> **luminous efficacy（发光效率/光效）**＝ 每消耗 1 W 电功率，产生多少 **lm**
> 
> **数值越大**代表：用同样的电，更“看起来亮”，也就是更省电、更高效

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture8-34.webp)

表格右侧是两个极限值

1. Theoretical limit at peak of eye sensitivity (λ=555 nm)：683 lm/W

> 如果你能把“1 W 的光学功率”全部变成 **555 nm 的单色绿光**，在“光学功率 → 视觉亮度”这个换算里，最多就是 **683 lm**。

1. Theoretical limit (white light)：~340 lm/W

> **白光必须包含很多波长**（红、绿、蓝等组合），而人眼对很多波长并没有 555 nm 那么敏感。
> 同样 1 W 的光学功率，如果分布在更宽的谱上，按人眼加权后得到的 lm 会更少，所以白光的上限大约只有单色绿光的一半左右。

**OLED（有机发光二极管）的光效通常低于基于氮化物/铝化物的无机化合物 LED**（比如 GaN / InGaN / AlGaN 等体系）

> 这在照明里常见：无机 LED（尤其氮化镓体系）在高亮、高效率上更强；OLED 优势更多在**面光源、柔性、显示效果**，但纯“照明光效”往往不如高性能无机 LED。

Terms(术语): luminosity measured in lumens. luminous efficacy. 两个术语

> **luminosity（这里更准确指“光通量 / luminous flux”）**：用 lumens（流明，lm）来量。
> 
> **luminous efficacy（发光效率/光效）**：用 m/W（流明每瓦）来量。

### Organic LEDs

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture8-35.webp)

**Some organic materials exhibit semiconducting properties**
有些有机材料（共轭分子/聚合物）可以像半导体一样传输电荷（电子/空穴）。

**OLEDs are attractive for low-cost, high-quality flat-panel displays**
OLED 适合做低成本、高质量的平板显示（薄、可大面积、可柔性、对比度高等）。

> 应该不太会考，稍微了解一下OLED也有类似的能带图即可
> 
> 右图是一张 OLED 的示意结构（从左到右）：
> 
> - 左侧电极：**ITO hole injector**（ITO 透明导电电极，常做阳极）
> 作用：**注入空穴**，而且透明，方便出光。
> - 中间有机层被分成三层（图例里也标了）：
> 558. **Hole transporting layer（空穴传输层，HTL）**：负责让空穴更容易移动到中间
> 559. **Emissive layer（发光层，EML）**：电子和空穴在这里相遇并复合 → 发光
> 560. **Electron transport layer（电子传输层，ETL）**：负责让电子更容易移动到中间
> - 右侧电极：**metal（金属阴极）**
> 作用：**注入电子**。
> 
> 能级标注：HOMO / LUMO
> 
> 右图上面写 **LUMO levels**，下面写 **HOMO levels**：
> 
> - **HOMO**（最高占据分子轨道）≈ 有机材料里的“价带顶” → 跟**空穴**相关
> - **LUMO**（最低未占据分子轨道）≈ 有机材料里的“导带底” → 跟**电子**相关
> 
> 它是在用有机材料的“分子轨道能级”来类比无机半导体的 Ev,EcE_v, E_cEv,Ec。

### Tunnel Diodes

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture8-36.webp)

**Degenerate doping（简并掺杂）**＝ 掺得非常重，重到：

- **n 区的费米能级** <span className="katex">
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
</mrow>

<annotation encoding="application/x-tex">

E_{Fn}

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
</span>
</span>
</span>

 被推到 **导带** <span className="katex">
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

 里面（所以写 <span className="katex">
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

<mo>

>
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

E_{Fn} > E_c

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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

>
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

）
→ n 区导带里已经“塞满”很多电子，像金属一样。
- **p 区的费米能级** <span className="katex">
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

p

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

E_{Fp}

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

 被拉到 **价带** <span className="katex">
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

 里面（所以写 <span className="katex">
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

p

</mi>
</mrow>
</msub>

<mo>
<

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

E_{Fp} < E_v

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

）
→ p 区价带里有大量空穴态（或者说价带空态非常多）。

可以到negative differential resistance(负微分电阻)状态，也就是电压继续升高，电流反而下降

> 为什么它“**useful in high-speed circuits and perhaps static memories**”
> 
> 因为负微分电阻意味着：
> 
> - **可以做振荡器/高频放大/快速开关**：器件本身响应极快（隧穿是量子过程，时间尺度很短），常用在微波/高速电路。
> - **可以做双稳态（bistable）电路**：I-V 的峰—谷结构允许在电路中形成两个稳定工作点，用来做简单的存储/触发器（“perhaps static memories”）。

#### 零偏压（V=0）：有隧穿，但净电流为 0

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture8-37.webp)

- 在热平衡下，两侧费米能级对齐（整个器件一个 <span className="katex">
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

）。
- 因为两边都存在“已占据态 ↔ 未占据态”的匹配，**确实会发生隧穿**：

  - n侧导带的电子可以隧穿到 p侧某些可用态；
  - p侧的电子也能反向隧穿到 n侧。
- 但由于平衡态：两个方向的隧穿速率相同 ⇒ **净电流为 0**。

---

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture8-38.webp)

#### 小正向偏压（p 端加正）：隧穿电流迅速上升

当施加**小正向电压**时（p 端更正）：

- 能带相对位置发生错位：通常等效为**p侧能带相对 n侧“下移”**。
- 这会让一个非常关键的事情发生：
**n侧导带里“已占据的电子态”会与 p侧价带里“未占据的空态（空穴对应的空电子态）”在能量上出现重叠。**

于是出现**强的带-带隧穿**：

- 电子从 **n侧导带 → 穿过极薄耗尽层 → p侧价带的空态**
- 这不需要跨越势垒顶，只要满足“能量守恒 + 终态为空”。

为什么电流会随着 V 快速增大？

- 正向偏压越大，**两边“可隧穿的重叠能量窗口”越大**（可用的初态/终态组合更多）
⇒ 隧穿电流迅速上升。

#### 到达峰值 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

I

</mi>

<mi>

p

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

I_p

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
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0785em;margin-right:0.05em;">
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

（对应 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

V

</mi>

<mi>

p

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

V_p

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

）：重叠窗口最大

I–V 曲线的第一个峰（<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

I

</mi>

<mi>

p

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

I_p

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
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0785em;margin-right:0.05em;">
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

 at <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

V

</mi>

<mi>

p

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

V_p

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

）对应能带图里“隧穿最顺畅”的情况：

- 此时 n侧导带中“被填充的一段”与 p侧价带中“空的一段”**重叠面积最大**
- 可发生隧穿的态数最多
⇒ 隧穿电流达到最大 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

I

</mi>

<mi>

p

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

I_p

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
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0785em;margin-right:0.05em;">
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

。

#### 继续增大正向电压：进入**负微分电阻区**（NDR）

这是隧道二极管最“反直觉”也最重要的部分：**电压变大，电流反而变小**，即

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
<

</mo>

<mn>

0

</mn>
</mrow>

<annotation encoding="application/x-tex">

\frac{dI}{dV} < 0

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
</span>

原因不是“势垒变高了”，而是更本质的——**能态重叠在变小**：

- 随着 V 继续增大，两侧能带错位进一步加大。
- 原先对得很好的“n侧导带已占据态”与“p侧价带空态”开始**错开**。
- 结果：满足“初态被占据 + 终态为空 + 能量匹配”的组合变少
⇒ **隧穿电流下降**。

这就形成了图里从 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

I

</mi>

<mi>

p

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

I_p

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
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0785em;margin-right:0.05em;">
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

 往下掉到 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

I

</mi>

<mi>

v

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

I_v

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

 的那段：**负微分电阻区**。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture8-39.webp)

#### 到达谷值 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

I

</mi>

<mi>

v

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

I_v

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

：隧穿通道基本关掉

当错位大到一定程度：

- n侧导带的已占据态与 p侧价带的空态**几乎不再重叠**
- 带-带隧穿大幅减弱
⇒ 电流降到谷值 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

I

</mi>

<mi>

v

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

I_v

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

。

#### 更大正向电压（到 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

V

</mi>

<mi>

f

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

V_f

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
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
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

 附近以后）：回到“正常二极管”导通，电流再次上升

再往右，I–V 曲线又开始上升，并且越来越像普通二极管的指数上升（图里虚线/右侧上扬部分）。

此时主导机制变了：

- 隧穿不再是主角（因为带-带对齐条件没了）
- 正向势垒已经被明显降低
- 开始出现**经典的注入/扩散电流**：

  - 电子从 n 注入到 p 的导带并在 p 区扩散/复合
  - 空穴从 p 注入到 n 的价带扩散/复合
  ⇒ 电流再次快速增大（这对应你标的 <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <msub>
  <mi>
  
  V
  
  </mi>
  
  <mi>
  
  f
  
  </mi>
  </msub>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  V_f
  
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
  <span className="vlist" style="height:0.3361em;">
  <span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
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
  
   之后那段）。

---

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture8-40.webp)

#### 反向偏压：也会有很大的隧穿电流（“反向就很容易通”）

图里也画了反向方向电流不小的特性（隧道二极管的反向特性不像普通二极管那样“几乎不导通直到击穿”）。

反向偏压时：

- 两侧能带错位方向相反
- 会让 **p侧价带已占据态** 与 **n侧导带未占据态** 出现重叠
⇒ 电子可以从 p侧直接隧穿到 n侧导带
⇒ 反向电流在比较小的反向电压下就能变得很大（而且比较“快”、不需要雪崩那种过程）。

### P-i-n Photodiodes

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture8-41.webp)

P+区与N+区重掺杂，几乎没有耗尽区，i区轻掺杂，耗尽区几乎占满了i层，所以W(耗尽层宽度)几乎等于<span className="katex">
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

i

</mi>

<mo>

−

</mo>

<mi>

r

</mi>

<mi>

e

</mi>

<mi>

g

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
</msub>
</mrow>

<annotation encoding="application/x-tex">

W_{i-region}

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
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.1389em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

i

</span>

<span className="mbin,mtight">

−

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal,mtight">

e

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

g

</span>

<span className="mord,mathnormal,mtight">

i

</span>

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

，所有的光生电子也是几乎都在i层产生的。

由于i层电场很强，光生载流子在i层产生后，会被电场快速分离与收集，所以说又非常快的反应时间

工作在快雪崩击穿的状态，可以放大信号

### Photodiode Applications

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture8-42.webp)

普通光电二极管和雪崩光电二极管的对比

#### Photodiodes

一般都是工作在反偏状态下的PN结

<alert type="question">

为什么反偏呢？

1. 耗尽层宽，可以产生更多光生载流子
2. 反偏电流小，光生载流子电流更显著
3. 结电容小，RC延迟小

</alert>

#### Avalanche photodiodes

工作在接近雪崩击穿的状态下，可以通过碰撞电离的方式来放大光生电流

### Light Amplification

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture8-43.webp)

#### Absorption 吸收：光子被“吃掉”，电子上跳

图(a)表示：

- 系统里有一个电子在低能级 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

E

</mi>

<mn>

1

</mn>
</msub>
</mrow>

<annotation encoding="application/x-tex">

E_1

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
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0576em;margin-right:0.05em;">
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

。
- 来了一个光子，能量 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

h

</mi>

<mi>

ν

</mi>

<mo>

=

</mo>

<msub>
<mi>

E

</mi>

<mn>

2

</mn>
</msub>

<mo>

−

</mo>

<msub>
<mi>

E

</mi>

<mn>

1

</mn>
</msub>
</mrow>

<annotation encoding="application/x-tex">

h\nu = E_2 - E_1

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

<span className="mord,mathnormal" style="margin-right:0.0637em;">

ν

</span>

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
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0576em;margin-right:0.05em;">
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

−

</span>

<span className="mspace" style="margin-right:0.2222em;">



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
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0576em;margin-right:0.05em;">
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

。
- 电子吸收这个光子，上跳到高能级 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

E

</mi>

<mn>

2

</mn>
</msub>
</mrow>

<annotation encoding="application/x-tex">

E_2

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
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0576em;margin-right:0.05em;">
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

。
- 结果：**光子消失**，光强减少。

一句话：**吸收把光能变成电子的激发能。**

#### Spontaneous Emission 自发辐射：电子自己掉下来，随机发光子

图(b)表示：

- 电子本来在高能级 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

E

</mi>

<mn>

2

</mn>
</msub>
</mrow>

<annotation encoding="application/x-tex">

E_2

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
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0576em;margin-right:0.05em;">
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

（被激发态）。
- 不需要外来的光子触发，电子也会“自己”掉回低能级 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

E

</mi>

<mn>

1

</mn>
</msub>
</mrow>

<annotation encoding="application/x-tex">

E_1

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
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0576em;margin-right:0.05em;">
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

。
- 同时放出一个光子，能量同样是 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

h

</mi>

<mi>

ν

</mi>

<mo>

=

</mo>

<msub>
<mi>

E

</mi>

<mn>

2

</mn>
</msub>

<mo>

−

</mo>

<msub>
<mi>

E

</mi>

<mn>

1

</mn>
</msub>
</mrow>

<annotation encoding="application/x-tex">

h\nu=E_2-E_1

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

<span className="mord,mathnormal" style="margin-right:0.0637em;">

ν

</span>

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
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0576em;margin-right:0.05em;">
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

−

</span>

<span className="mspace" style="margin-right:0.2222em;">



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
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0576em;margin-right:0.05em;">
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

。

关键点：**自发辐射发出的光子方向、相位、时间都是随机的**。
所以它像“灯泡”那样发散，不会形成整齐一致的光束。

#### Stimulated Emission 受激辐射：来一个光子，诱导再出一个“一模一样”的光子

图(c)是整页最重要的机制（激光的核心）：

- 电子在高能级 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

E

</mi>

<mn>

2

</mn>
</msub>
</mrow>

<annotation encoding="application/x-tex">

E_2

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
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0576em;margin-right:0.05em;">
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

。
- 来了一个光子（能量匹配 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

E

</mi>

<mn>

2

</mn>
</msub>

<mo>

−

</mo>

<msub>
<mi>

E

</mi>

<mn>

1

</mn>
</msub>
</mrow>

<annotation encoding="application/x-tex">

E_2-E_1

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
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0576em;margin-right:0.05em;">
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

−

</span>

<span className="mspace" style="margin-right:0.2222em;">



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
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0576em;margin-right:0.05em;">
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

）。
- 这个光子“刺激”电子从 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

E

</mi>

<mn>

2

</mn>
</msub>
</mrow>

<annotation encoding="application/x-tex">

E_2

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
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0576em;margin-right:0.05em;">
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

 掉到 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

E

</mi>

<mn>

1

</mn>
</msub>
</mrow>

<annotation encoding="application/x-tex">

E_1

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
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0576em;margin-right:0.05em;">
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

，同时放出**第二个光子**。

最关键的性质（图下方黄框写的）：

> 受激辐射产生的光子与刺激光子 **频率相同、方向相同、相位一致（相干）**。

所以结果是：输入 1 个光子 → 输出 2 个“复制光子”。

这就是“光被放大”的微观原因。

#### Net Light Absorption 净吸收：为什么通常情况下还是“吸收占上风”

右侧(d)画的是：**大多数电子在低能级** <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

E

</mi>

<mn>

1

</mn>
</msub>
</mrow>

<annotation encoding="application/x-tex">

E_1

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
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0576em;margin-right:0.05em;">
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

，高能级 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

E

</mi>

<mn>

2

</mn>
</msub>
</mrow>

<annotation encoding="application/x-tex">

E_2

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
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0576em;margin-right:0.05em;">
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

 人很少。

这时如果光通过：

- 吸收发生的前提：需要 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

E

</mi>

<mn>

1

</mn>
</msub>
</mrow>

<annotation encoding="application/x-tex">

E_1

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
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0576em;margin-right:0.05em;">
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

 有电子（通常很多） → **吸收概率大**
- 受激辐射发生的前提：需要 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

E

</mi>

<mn>

2

</mn>
</msub>
</mrow>

<annotation encoding="application/x-tex">

E_2

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
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0576em;margin-right:0.05em;">
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

 有电子（通常很少） → **受激辐射概率小**

所以总体效果：
**被吸收的光子数 > 受激产生的光子数** → 光越走越弱（净吸收）。

这就是为什么普通材料不加“泵浦”的时候不会自动变成光放大器。

#### Net Light Amplification 净放大：必须有“粒子数反转”

右侧(e)画的是：**高能级** <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

E

</mi>

<mn>

2

</mn>
</msub>
</mrow>

<annotation encoding="application/x-tex">

E_2

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
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0576em;margin-right:0.05em;">
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

 **的电子反而比低能级** <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

E

</mi>

<mn>

1

</mn>
</msub>
</mrow>

<annotation encoding="application/x-tex">

E_1

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
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0576em;margin-right:0.05em;">
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

 **多**。

这就是右边黄框强调的 **population inversion（粒子数反转）**：

> 高能级的占据概率 <span className="katex">
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
> <msub>
> <mi>
> 
> E
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
> f(E_2)
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
> <span className="vlist" style="height:0.3011em;">
> <span style="top:-2.55em;margin-left:-0.0576em;margin-right:0.05em;">
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
>  大于低能级 <span className="katex">
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
> <msub>
> <mi>
> 
> E
> 
> </mi>
> 
> <mn>
> 
> 1
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
> f(E_1)
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
> <span className="vlist" style="height:0.3011em;">
> <span style="top:-2.55em;margin-left:-0.0576em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mtight">
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
> 。

在这种情况下：

- 受激辐射所需的 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

E

</mi>

<mn>

2

</mn>
</msub>
</mrow>

<annotation encoding="application/x-tex">

E_2

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
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0576em;margin-right:0.05em;">
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

 电子很多 → **受激辐射概率大**
- 吸收所需的 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

E

</mi>

<mn>

1

</mn>
</msub>
</mrow>

<annotation encoding="application/x-tex">

E_1

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
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0576em;margin-right:0.05em;">
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

 电子反而少 → **吸收概率小**

于是总体效果：
**受激产生的光子数 > 被吸收的光子数** → 光越走越强（净放大）。

#### Light Amplification in P-N Diode

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture8-44.webp)

记一个要产生粒子数反转的条件吧

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

q

</mi>

<mi>

V

</mi>

<mo>

=

</mo>

<msub>
<mi>

E

</mi>

<mrow>
<mi>

f

</mi>

<mi>

n

</mi>
</mrow>
</msub>

<mo>

−

</mo>

<msub>
<mi>

E

</mi>

<mrow>
<mi>

f

</mi>

<mi>

p

</mi>
</mrow>
</msub>

<mo>

>
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

qV=E_{fn}-E_{fp}>E_g

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
<span className="strut" style="height:0.9694em;vertical-align:-0.2861em;">



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
<span className="mord,mathnormal,mtight" style="margin-right:0.1076em;">

f

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
<span className="strut" style="height:0.9694em;vertical-align:-0.2861em;">



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
<span className="mord,mathnormal,mtight" style="margin-right:0.1076em;">

f

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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

>
</span>

<span className="mspace" style="margin-right:0.2778em;">



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
</span>

> **上态（导带相关态）被占据的概率，比下态（价带相关态）还“更容易被占据”**（或者等价地说：下态空位足够多、上态电子足够多），从统计上让受激辐射压过吸收，材料出现**净增益（gain）**。

### Optical Feedback and Laser

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture8-45.webp)

先定义三个量：

- <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

R

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

R

</mi>

<mn>

2

</mn>
</msub>
</mrow>

<annotation encoding="application/x-tex">

R_1, R_2

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8778em;vertical-align:-0.1944em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0077em;">

R

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0077em;margin-right:0.05em;">
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
<span className="mord,mathnormal" style="margin-right:0.0077em;">

R

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0077em;margin-right:0.05em;">
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

：两端镜面的**反射率**（0 到 1 之间）
- **G**：光走完“一圈”之后的**净放大因子**（round-trip gain）

  - 它把“在增益区的受激辐射放大”减去“传播损耗、吸收、散射、自由载流子吸收”等所有损耗后的结果合在一起

用“走一圈”理解它

假设腔内某一时刻有光强 <span className="katex">
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

。

1. 光从左端出发，经过增益介质，被放大 → 变成 <span className="katex">
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

×

</mo>

<msub>
<mi>

G

</mi>

<mtext>

single-pass

</mtext>
</msub>
</mrow>

<annotation encoding="application/x-tex">

I_0 \times G_{\text{single-pass}}

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
<span className="mord,mathnormal">

G

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

single-pass

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
2. 到右端镜面，反射回来 → 乘上 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

R

</mi>

<mn>

2

</mn>
</msub>
</mrow>

<annotation encoding="application/x-tex">

R_2

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
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0077em;margin-right:0.05em;">
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
3. 回来再经过一次增益介质（再放大一次） → 再乘一个 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

G

</mi>

<mtext>

single-pass

</mtext>
</msub>
</mrow>

<annotation encoding="application/x-tex">

G_{\text{single-pass}}

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

G

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

single-pass

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
4. 到左端镜面，再反射 → 乘上 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

R

</mi>

<mn>

1

</mn>
</msub>
</mrow>

<annotation encoding="application/x-tex">

R_1

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
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0077em;margin-right:0.05em;">
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

所以走完一圈大致是：

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

<mtext>

after

</mtext>
</msub>

<mo>

=

</mo>

<msub>
<mi>

I

</mi>

<mn>

0

</mn>
</msub>

<mo>

×

</mo>

<msub>
<mi>

R

</mi>

<mn>

1

</mn>
</msub>

<mo>

×

</mo>

<msub>
<mi>

R

</mi>

<mn>

2

</mn>
</msub>

<mo>

×

</mo>

<mo stretchy="false">

(

</mo>

<msub>
<mi>

G

</mi>

<mtext>

single-pass

</mtext>
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

I_{\text{after}} = I_0 \times R_1 \times R_2 \times (G_{\text{single-pass}})^2

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
<span className="mord,mtight">
<span className="mord,text,mtight">
<span className="mord,mtight">

after

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
<span className="mord,mathnormal" style="margin-right:0.0077em;">

R

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0077em;margin-right:0.05em;">
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

×

</span>

<span className="mspace" style="margin-right:0.2222em;">



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
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0077em;margin-right:0.05em;">
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

×

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.1502em;vertical-align:-0.2861em;">



</span>

<span className="mopen">

(

</span>

<span className="mord">
<span className="mord,mathnormal">

G

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

single-pass

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

课件把“来回两次增益 + 传播损耗”等全部打包成一个 **G**（round trip 的净因子），于是写成：

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

<mtext>

after

</mtext>
</msub>

<mo>

=

</mo>

<msub>
<mi>

I

</mi>

<mn>

0

</mn>
</msub>

<mo>

×

</mo>

<msub>
<mi>

R

</mi>

<mn>

1

</mn>
</msub>

<msub>
<mi>

R

</mi>

<mn>

2

</mn>
</msub>

<mi>

G

</mi>
</mrow>

<annotation encoding="application/x-tex">

I_{\text{after}} = I_0 \times R_1 R_2 G

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
<span className="mord,mtight">
<span className="mord,text,mtight">
<span className="mord,mtight">

after

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
<span className="mord,mathnormal" style="margin-right:0.0077em;">

R

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0077em;margin-right:0.05em;">
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
<span className="mord,mathnormal" style="margin-right:0.0077em;">

R

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0077em;margin-right:0.05em;">
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

<span className="mord,mathnormal">

G

</span>
</span>
</span>
</span>
</span>

**阈值条件**就是“回来不要变小”：

- 如果 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

R

</mi>

<mn>

1

</mn>
</msub>

<msub>
<mi>

R

</mi>

<mn>

2

</mn>
</msub>

<mi>

G

</mi>

<mo>
<

</mo>

<mn>

1

</mn>
</mrow>

<annotation encoding="application/x-tex">

R_1R_2G < 1

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
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0077em;margin-right:0.05em;">
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
<span className="mord,mathnormal" style="margin-right:0.0077em;">

R

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0077em;margin-right:0.05em;">
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

<span className="mord,mathnormal">

G

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

1

</span>
</span>
</span>
</span>

：每走一圈都会衰减 → 光只能是微弱自发辐射，无法形成激光
- 如果 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

R

</mi>

<mn>

1

</mn>
</msub>

<msub>
<mi>

R

</mi>

<mn>

2

</mn>
</msub>

<mi>

G

</mi>

<mo>

>
</mo>

<mn>

1

</mn>
</mrow>

<annotation encoding="application/x-tex">

R_1R_2G > 1

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
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0077em;margin-right:0.05em;">
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
<span className="mord,mathnormal" style="margin-right:0.0077em;">

R

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0077em;margin-right:0.05em;">
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

<span className="mord,mathnormal">

G

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

1

</span>
</span>
</span>
</span>

：每走一圈都会增长 → 光会指数增长（直到增益饱和）
- 阈值点：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<msub>
<mi>

R

</mi>

<mn>

1

</mn>
</msub>

<msub>
<mi>

R

</mi>

<mn>

2

</mn>
</msub>

<mi>

G

</mi>

<mo>

=

</mo>

<mn>

1

</mn>
</mrow>

<annotation encoding="application/x-tex">

R_1R_2G = 1

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
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0077em;margin-right:0.05em;">
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
<span className="mord,mathnormal" style="margin-right:0.0077em;">

R

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0077em;margin-right:0.05em;">
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
<span className="strut" style="height:0.6444em;">



</span>

<span className="mord">

1

</span>
</span>
</span>
</span>
</span>

> Light intensity grows until <span className="katex">
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
> <mn>
> 
> 1
> 
> </mn>
> </msub>
> 
> <msub>
> <mi>
> 
> R
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
> <mi>
> 
> G
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
> 1
> 
> </mn>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> R_1R_2G = 1
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
> <span className="vlist" style="height:0.3011em;">
> <span style="top:-2.55em;margin-left:-0.0077em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mtight">
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
> <span className="mord,mathnormal" style="margin-right:0.0077em;">
> 
> R
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3011em;">
> <span style="top:-2.55em;margin-left:-0.0077em;margin-right:0.05em;">
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
> <span className="mord,mathnormal">
> 
> G
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
> 1
> 
> </span>
> </span>
> </span>
> </span>
> 
> s, when the light intensity  is just large enough to stimulate carrier recombinations at the  same rate the carriers are injected by the diode current.

- 一开始你把电流加大，载流子堆积 → **增益变大**（更容易受激辐射）
- 当腔内光强变大时，受激辐射会更频繁 → **把载流子“消耗”掉**（电子空穴复合成光子）
- 光越强，消耗越快，直到进入一个平衡：
**注入 = 消耗**（载流子不再无限堆积）

这会导致一个非常重要的非线性效果：**增益饱和（gain saturation）**
腔内光强足够大时，材料的可用反转被“拉平”，有效增益会自动下降到“刚好补偿损耗”的水平，于是系统稳定在：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<msub>
<mi>

R

</mi>

<mn>

1

</mn>
</msub>

<msub>
<mi>

R

</mi>

<mn>

2

</mn>
</msub>

<mi>

G

</mi>

<mo>

=

</mo>

<mn>

1

</mn>
</mrow>

<annotation encoding="application/x-tex">

R_1R_2G = 1

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
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0077em;margin-right:0.05em;">
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
<span className="mord,mathnormal" style="margin-right:0.0077em;">

R

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0077em;margin-right:0.05em;">
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
<span className="strut" style="height:0.6444em;">



</span>

<span className="mord">

1

</span>
</span>
</span>
</span>
</span>

### Laser Applications

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture8-46.webp)

#### Red diode lasers（红光二极管激光器）

**应用：CD、DVD 读写器（reader/writer）**

- CD/DVD 的读写是用激光照到盘面，通过反射强弱变化读取信息；写入则用激光加热改变记录层状态。
- 红光（或近红外）激光器技术成熟、成本低、稳定，所以早期光盘系统常用。

#### Blue diode lasers（蓝光二极管激光器）

**应用：Blu-ray DVD（蓝光光盘，存储密度更高）**

- 蓝光的波长比红光**更短**。
- 光学系统能聚焦的最小光斑大小大致与波长成正比（波长越短，光斑越小）。
- 光斑更小 → 可以刻录/读取更小的坑点（pit）和更密的轨道 → **单位面积能存更多数据**，所以写“higher storage density（更高存储密度）”。

这就是蓝光光盘比 DVD 容量更大的根本原因之一。

#### 1.55 µm infrared diode lasers（1.55 微米红外二极管激光器）

**应用：Fiber-optic communication（光纤通信）**

- 1.55 µm（PPT 写“mm”应是笔误，应该是 **µm** 微米）是光纤通信的经典波段之一。
- 在这个波段，标准石英光纤的**衰减最低**（信号传得最远），同时也常用掺铒光纤放大器等技术配合。
- 所以 1.55 µm 红外半导体激光器广泛用于长距离、高速的光纤通信。
