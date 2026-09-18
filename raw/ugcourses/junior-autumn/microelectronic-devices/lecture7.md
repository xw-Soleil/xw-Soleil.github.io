# Lecture 7：金半接触

> 功函数与能带对齐、肖特基接触与整流特性、欧姆接触，以及两者的对比总结

## 金半接触（PN结变体）

![image.png](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture7-23.webp)

## Work Function以及相关概念图示

![image.png](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture7-26.webp)

---

### Work Function | 功函数

---

### <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi mathvariant="bold">

E

</mi>

<mn mathvariant="bold">

0

</mn>
</msub>
</mrow>

<annotation encoding="application/x-tex">

\mathbf{E_0}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8361em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathbf">

E

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathbf,mtight">

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

: Vacuum energy level  | 真空能级 / 真空能量参考

- **中文**：(<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

E

</mi>

<mn>

0

</mn>
</msub>
</mrow>

<annotation encoding="application/x-tex">

E_0

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

) 表示材料表面外“真空中自由电子”的能量基准。电子若达到该能级，可视为脱离材料束缚。
- **English**: (<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

E

</mi>

<mn>

0

</mn>
</msub>
</mrow>

<annotation encoding="application/x-tex">

E_0

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

) is the energy reference for a free electron just outside the surface in vacuum . Reaching (<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

E

</mi>

<mn>

0

</mn>
</msub>
</mrow>

<annotation encoding="application/x-tex">

E_0

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

) means the electron is effectively emitted from the material.

---

### <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

χ

</mi>
</mrow>

<annotation encoding="application/x-tex">

\chi

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.625em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal">

χ

</span>
</span>
</span>
</span>

: Electron affinity | 电子亲和能

- **中文**：电子亲和能 (<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

χ

</mi>
</mrow>

<annotation encoding="application/x-tex">

\chi

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.625em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal">

χ

</span>
</span>
</span>
</span>

) 是从导带底 (<span className="katex">
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

) 到真空能级 (<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

E

</mi>

<mn>

0

</mn>
</msub>
</mrow>

<annotation encoding="application/x-tex">

E_0

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

) 的能量差：<span>
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

χ

</mi>

<mo>

=

</mo>

<msub>
<mi>

E

</mi>

<mn>

0

</mn>
</msub>

<mo>

−

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

\chi = E_0 - E_c

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.625em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal">

χ

</span>

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
</span>


  - 硅的典型值：(<span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mi>
  
  χ
  
  </mi>
  
  <mo stretchy="false">
  
  (
  
  </mo>
  
  <mtext>
  
  Si
  
  </mtext>
  
  <mo stretchy="false">
  
  )
  
  </mo>
  
  <mo>
  
  ≈
  
  </mo>
  
  <mn>
  
  4.05
  
  </mn>
  
  <mo separator="true">
  
  ,
  
  </mo>
  
  <mtext>
  
  eV
  
  </mtext>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  \chi(\text{Si}) \approx 4.05,\text{eV}
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:1em;vertical-align:-0.25em;">
  
  
  
  </span>
  
  <span className="mord,mathnormal">
  
  χ
  
  </span>
  
  <span className="mopen">
  
  (
  
  </span>
  
  <span className="mord,text">
  <span className="mord">
  
  Si
  
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
  <span className="strut" style="height:0.8778em;vertical-align:-0.1944em;">
  
  
  
  </span>
  
  <span className="mord">
  
  4.05
  
  </span>
  
  <span className="mpunct">
  
  ,
  
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
  
  )。锗的典型值：(<span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mi>
  
  χ
  
  </mi>
  
  <mo stretchy="false">
  
  (
  
  </mo>
  
  <mtext>
  
  Ge
  
  </mtext>
  
  <mo stretchy="false">
  
  )
  
  </mo>
  
  <mo>
  
  ≈
  
  </mo>
  
  <mn>
  
  4.00
  
  </mn>
  
  <mo separator="true">
  
  ,
  
  </mo>
  
  <mtext>
  
  eV
  
  </mtext>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  \chi(\text{Ge}) \approx 4.00,\text{eV}
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:1em;vertical-align:-0.25em;">
  
  
  
  </span>
  
  <span className="mord,mathnormal">
  
  χ
  
  </span>
  
  <span className="mopen">
  
  (
  
  </span>
  
  <span className="mord,text">
  <span className="mord">
  
  Ge
  
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
  <span className="strut" style="height:0.8778em;vertical-align:-0.1944em;">
  
  
  
  </span>
  
  <span className="mord">
  
  4.00
  
  </span>
  
  <span className="mpunct">
  
  ,
  
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
  
  )
- **English**: Electron affinity (<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

χ

</mi>
</mrow>

<annotation encoding="application/x-tex">

\chi

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.625em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal">

χ

</span>
</span>
</span>
</span>

) is the energy difference between the vacuum level and the conduction band minimum:<span>
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

χ

</mi>

<mo>

=

</mo>

<msub>
<mi>

E

</mi>

<mn>

0

</mn>
</msub>

<mo>

−

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

\chi = E_0 - E_c

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.625em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal">

χ

</span>

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
</span>

### High/Low Work Function的界定、常见金属的Work Function数值

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 50.1%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="image.png" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture7-21.webp" />
      </p>
    </td>
    
    
      <td style="width: 49.9%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="image.png" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture7-17.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

## 两种**M/S Contacts**

![image.png](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture7-20.webp)

### 整流型接触：**肖特基接触 / 肖特基二极管（Schottky contact/diode）**

#### Metal - N-type Si contact

![image.png](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture7-33.webp)

对 **n 型半导体的肖特基接触**来说，<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi mathvariant="normal">

Φ

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

\Phi_{Bn}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord">

Φ

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

（electron Schottky barrier height）通常定义为：<mark>

**在热平衡时**

</mark>

<mark>

，金属/半导体界面处，

</mark>

<mark>

**半导体导带底**

</mark>

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

 <mark>

到

</mark>

 <mark>

**共同费米能级**

</mark>

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

 <mark>

的能量差

</mark>

<mark>

（和MOS电容里面的

</mark>

<span className="katex">
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

<mark>

完全不一样，这里B是barrier的意思，单位也是能量。

</mark>



<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi mathvariant="normal">

Φ

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

Φ_{Bn}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord">

Φ

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

≡<span className="katex">
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

<mo stretchy="false">

(

</mo>

<mtext>

界面

</mtext>

<mo stretchy="false">

)

</mo>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

E_{c(界面)}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.0385em;vertical-align:-0.3552em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0576em;">

E

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3448em;">
<span style="top:-2.5198em;margin-left:-0.0576em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

c

</span>

<span className="mopen,mtight">

(

</span>

<span className="mord,cjk_fallback,mtight">

界面

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
</span>
</span>
</span>

−<span className="katex">
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

<mo stretchy="false">

(

</mo>

<mtext>

界面

</mtext>

<mo stretchy="false">

)

</mo>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

E_{F(界面)}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.0385em;vertical-align:-0.3552em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0576em;">

E

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3448em;">
<span style="top:-2.5198em;margin-left:-0.0576em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.1389em;">

F

</span>

<span className="mopen,mtight">

(

</span>

<span className="mord,cjk_fallback,mtight">

界面

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
</span>
</span>
</span>



这表示：电子想从金属（在 <span className="katex">
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

 附近）“爬”到半导体的导带里，需要跨过多高的能量“山”

从而可以得出：

<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi mathvariant="normal">

Φ

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

Φ_{Bn}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord">

Φ

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

=<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi mathvariant="normal">

Φ

</mi>

<mi>

M

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

Φ_M

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord">

Φ

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

M

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

−<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

χ

</mi>
</mrow>

<annotation encoding="application/x-tex">

χ

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.625em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal">

χ

</span>
</span>
</span>
</span>



> <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msub>
> <mi mathvariant="normal">
> 
> Φ
> 
> </mi>
> 
> <mi>
> 
> M
> 
> </mi>
> </msub>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> \Phi_M
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
> <span className="mord">
> 
> Φ
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
> <span className="mord,mathnormal,mtight" style="margin-right:0.109em;">
> 
> M
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
> 告诉你：金属的 <span className="katex">
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
>  距离<span className="katex">
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
> E_0
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
> 有多远
> 
> <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <mi>
> 
> χ
> 
> </mi>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> \chi
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
> χ
> 
> </span>
> </span>
> </span>
> </span>
> 
>  告诉你：半导体导带底 <span className="katex">
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
>  距离<span className="katex">
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
> E_0
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
> 有多远
> 
> 界面处<span className="katex">
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
> E_0
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
> 为同一高度的参考点。两者一减，就是<span className="katex">
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
>  和 <span className="katex">
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
>  之间差多少——也就是势垒高度。

#### Metal - P-type Si contact

![image.png](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture7-29.webp)

**对于****空穴****而言****的肖特基势垒高度**

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<msub>
<mi mathvariant="normal">

Φ

</mi>

<mrow>
<mi>

B

</mi>

<mi>

p

</mi>
</mrow>
</msub>

<mo>

=

</mo>

<mi>

χ

</mi>

<mo>

+

</mo>

<msub>
<mi>

E

</mi>

<mi>

G

</mi>
</msub>

<mo>

−

</mo>

<msub>
<mi mathvariant="normal">

Φ

</mi>

<mi>

M

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

\Phi_{Bp}=\chi+E_G-\Phi_M

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9694em;vertical-align:-0.2861em;">



</span>

<span className="mord">
<span className="mord">

Φ

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

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.7778em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal">

χ

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
<span className="mord">

Φ

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

M

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
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
<mi mathvariant="normal">

Φ

</mi>

<mrow>
<mi>

B

</mi>

<mi>

p

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

\Phi_{Bp}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9694em;vertical-align:-0.2861em;">



</span>

<span className="mord">
<span className="mord">

Φ

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

：**对空穴（holes）的势垒高度**。常用能带图上用**在界面处，从共同费米能级**<span className="katex">
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

**到价带顶** <span className="katex">
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

 **的能量差**表示：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<msub>
<mi mathvariant="normal">

Φ

</mi>

<mrow>
<mi>

B

</mi>

<mi>

p

</mi>
</mrow>
</msub>

<mo>

≡

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

<mrow>
<mi>

V

</mi>

<mo stretchy="false">

(

</mo>

<mtext>

界面处

</mtext>

<mo stretchy="false">

)

</mo>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

\Phi_{Bp}\equiv E_F - E_{V(界面处)}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9694em;vertical-align:-0.2861em;">



</span>

<span className="mord">
<span className="mord">

Φ

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

−

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.0385em;vertical-align:-0.3552em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0576em;">

E

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3448em;">
<span style="top:-2.5198em;margin-left:-0.0576em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.2222em;">

V

</span>

<span className="mopen,mtight">

(

</span>

<span className="mord,cjk_fallback,mtight">

界面处

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
</span>
</span>
</span>
</span>

考虑**内建电压，**可得：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

q

</mi>

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

<msub>
<mi mathvariant="normal">

Φ

</mi>

<mrow>
<mi>

B

</mi>

<mi>

p

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

V

</mi>
</msub>

<msub>
<mo stretchy="false">

)

</mo>

<mrow>
<mi>

F

</mi>

<mi>

B

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

qV_{bi}=\Phi_{Bp}-(E_F-E_V)_{FB}

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
<span className="strut" style="height:0.9694em;vertical-align:-0.2861em;">



</span>

<span className="mord">
<span className="mord">

Φ

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
<span className="mord,mathnormal,mtight" style="margin-right:0.1389em;">

F

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0502em;">

B

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
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

：**内建电压**（built-in voltage），也就是半导体从“远离界面处（平带/本体）”到“界面处”产生的**静电势差**，对应能带的**弯曲量**。
- <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
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

V

</mi>
</msub>

<msub>
<mo stretchy="false">

)

</mo>

<mrow>
<mi>

F

</mi>

<mi>

B

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

(E_F-E_V)_{FB}

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
<span className="mord,mathnormal,mtight" style="margin-right:0.1389em;">

F

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0502em;">

B

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

：**平带（Flat-Band）/本体区域**里，费米能级到价带顶的能量差。

> 远离界面处没有弯曲的那一段

### 非整流型接触：**欧姆接触（Ohmic contact）**

![image.png](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture7-13.webp)

对 **n 型半导体**的欧姆接触来说，界面处对**多数载流子电子**的势垒**很低**，因此接触呈现**非整流**特性、接触电阻小。

**同样可以定义电子势垒高度：**在热平衡时，金属/半导体界面处，半导体导带底 <span className="katex">
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

)到共同费米能级 <span className="katex">
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

)的能量差

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<msub>
<mi mathvariant="normal">

Φ

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

<mo>

≡

</mo>

<mfrac>
<mn>

1

</mn>

<mi>

q

</mi>
</mfrac>

<mo stretchy="false">

(

</mo>

<msub>
<mi>

E

</mi>

<mrow>
<mi>

c

</mi>

<mo stretchy="false">

(

</mo>

<mtext>

界面

</mtext>

<mo stretchy="false">

)

</mo>
</mrow>
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
</mrow>

<annotation encoding="application/x-tex">

\Phi_{Bn}\equiv \frac{1}{q} (E_{c(\text{界面})}-E_F)

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord">

Φ

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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

≡

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

<span className="mopen">

(

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0576em;">

E

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3448em;">
<span style="top:-2.5198em;margin-left:-0.0576em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

c

</span>

<span className="mopen,mtight">

(

</span>

<span className="mord,text,mtight">
<span className="mord,cjk_fallback,mtight">

界面

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

<span className="mclose">

)

</span>
</span>
</span>
</span>
</span>

<mark>

**欧姆接触的关键特征：**

</mark>

<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>
<msub>
<mi mathvariant="bold">

Φ

</mi>

<mrow>
<mi mathvariant="bold-italic">

B

</mi>

<mi mathvariant="bold-italic">

n

</mi>
</mrow>
</msub>
</mi>
</mrow>

<annotation encoding="application/x-tex">

\bm{\Phi_{Bn}}

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
<span className="mord,mathbf">

Φ

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3303em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,boldsymbol,mtight">

Bn

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
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

**很小（Low Barrier for electrons）**

</mark>



- 理想 Schottky-Mott 模型下仍有

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<msub>
<mi mathvariant="normal">

Φ

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

<mo>

=

</mo>

<msub>
<mi mathvariant="normal">

Φ

</mi>

<mi>

M

</mi>
</msub>

<mo>

−

</mo>

<mi>

χ

</mi>
</mrow>

<annotation encoding="application/x-tex">

\Phi_{Bn}=\Phi_M-\chi

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord">

Φ

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
<span className="mord">

Φ

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

M

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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
<span className="strut" style="height:0.625em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal">

χ

</span>
</span>
</span>
</span>
</span>

- 当 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi mathvariant="normal">

Φ

</mi>

<mi>

M

</mi>
</msub>

<mo>
<

</mo>

<msub>
<mi mathvariant="normal">

Φ

</mi>

<mi>

S

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

\Phi_M<\Phi_S

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord">

Φ

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

M

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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
<span className="mord">

Φ

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

（且常配合接触区重掺杂 n+）时，界面更容易形成**电子积累/势垒变薄**，使得

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<msub>
<mi mathvariant="normal">

Φ

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

<mo>

≈

</mo>

<mn>

0

</mn>

<mspace width="1em">



</mspace>

<mtext>

或势垒宽度极薄（隧穿容易）

</mtext>
</mrow>

<annotation encoding="application/x-tex">

\Phi_{Bn}\approx 0 \quad \text{或势垒宽度极薄（隧穿容易）}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord">

Φ

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

<span className="mord">

0

</span>

<span className="mspace" style="margin-right:1em;">



</span>

<span className="mord,text">
<span className="mord,cjk_fallback">

或势垒宽度极薄（隧穿容易）

</span>
</span>
</span>
</span>
</span>
</span>

**这表示：** 电子从金属（在 (<span className="katex">
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

) 附近）进入半导体导带几乎不需要跨越“能量山”（<mark>

或可直接隧穿通过

</mark>

），因此 **正反向都容易导通**，I–V 近似线性对称：

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

≈

</mo>

<mfrac>
<mi>

V

</mi>

<msub>
<mi>

R

</mi>

<mi>

c

</mi>
</msub>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

I \approx \frac{V}{R_c}

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
<span className="mord,mathnormal" style="margin-right:0.2222em;">

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

其中 (<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

R

</mi>

<mi>

c

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

R_c

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

) 为接触电阻

#### <span className="katex">
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

与<span className="katex">
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

p

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

\phi_{Bp}

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

与<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

ϕ

</mi>

<mi>

M

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

\phi_M

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
<span className="mord,mathnormal,mtight" style="margin-right:0.109em;">

M

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

之间的趋势关系

![image.png](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture7-30.webp)

### 非理想效应：Contacts-Fermi level pinning Effect | **费米能级钉扎**

![image.png](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture7-11.webp)

<alert type="tip">

**费米能级钉扎 | Fermi level pinning**

A high density of allowed energy states in the band gap at the MS interface pins <span className="katex">
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

 to the range 0.4 eV to 0.9 eV below <span className="katex">
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

 (“Fermi level pinning”). 在金属-半导体界面处的禁带中，存在高密度的允许能态（界面态），这使得费米能级 <span className="katex">
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

 被钉扎在导带底 <span className="katex">
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

 以下 0.4 eV 到 0.9 eV 的范围内（即**“费米能级钉扎”** 现象）。

</alert>

![image.png](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture7-22.webp)

<mark>

费米钉扎效应对应的能带图如下图b所示：

</mark>



<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 64.4%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="image.png" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture7-36.webp" />
      </p>
    </td>
    
    
      <td style="width: 35.6%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="image.png" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture7-25.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

## **Schottky contact 整流接触**

### Electrical Characteristics ｜ 电学特性

#### M/S Junction的电荷分布

电荷储存在接触面的两边

![image.png](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture7-32.webp)

考虑泊松方程（实际就是静电场的高斯定理），其中<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

ρ

</mi>
</mrow>

<annotation encoding="application/x-tex">

ρ

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

为净电荷密度

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 29.7%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="image.png" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture7-06.webp" />
      </p>
    </td>
    
    
      <td style="width: 70.3%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="image.png" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture7-08.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

#### **Depletion Layer Approximation** **｜ 耗尽区近似**

The **depletion-layer approximation** assumes that near a junction the mobile carriers are almost completely swept out, leaving a region of fixed ionized dopants (roughly constant charge density), while the material outside this region remains electrically neutral.

**Depletion Layer Approximation（耗尽层近似）**：在结/接触附近假设某一宽度内移动载流子几乎被“清空”、只剩离化杂质形成近似恒定的空间电荷密度，而该区域外材料电中性、空间电荷近似为零。

![image.png](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture7-18.webp)

上面两个联立可以解出（注意一下右边三幅图）：

> 实际上这里就是由于<span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <mi>
> 
> ρ
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
> q
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
> N
> 
> </mi>
> 
> <mi>
> 
> D
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
> A
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
> 
> <annotation encoding="application/x-tex">
> 
> \rho=q(N_D - N_A)
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
> ρ
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
> <span className="strut" style="height:1em;vertical-align:-0.25em;">
> 
> 
> 
> </span>
> 
> <span className="mord,mathnormal" style="margin-right:0.0359em;">
> 
> q
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
> <span className="mord,mathnormal" style="margin-right:0.109em;">
> 
> N
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3283em;">
> <span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
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
> <span className="mord,mathnormal" style="margin-right:0.109em;">
> 
> N
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3283em;">
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
> A
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
> 是恒定的，那么从这个方程<span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <mfrac>
> <mrow>
> <mi>
> 
> d
> 
> </mi>
> 
> <mi mathvariant="script">
> 
> E
> 
> </mi>
> </mrow>
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
> x
> 
> </mi>
> </mrow>
> </mfrac>
> 
> <mo>
> 
> =
> 
> </mo>
> 
> <mfrac>
> <mi>
> 
> ρ
> 
> </mi>
> 
> <msub>
> <mi>
> 
> ε
> 
> </mi>
> 
> <mi>
> 
> s
> 
> </mi>
> </msub>
> </mfrac>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> \frac{d \mathcal{E}}{dx} = \frac{\rho}{\varepsilon_s}
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
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
> d
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
> d
> 
> </span>
> 
> <span className="mord,mathcal,mtight" style="margin-right:0.0894em;">
> 
> E
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
> <span className="strut" style="height:1.1926em;vertical-align:-0.4451em;">
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
> <span className="vlist" style="height:0.7475em;">
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
> ε
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.1645em;">
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
> s
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
> <span style="top:-3.4461em;">
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
> ρ
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
> </span>
> </span>
> </span>
> 
> 就能计算出电场 电场再积分就能算出电势，于是就有了下图右边三幅图
> 
> 同时图里应该是只考虑了单种掺杂，即只掺了Nd

![image.png](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture7-04.webp)

#### Summary:<span className="katex">
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

<mtext>



</mtext>

<mtext>



</mtext>

<mi mathvariant="normal">

∣

</mi>

<mtext>



</mtext>

<mtext>



</mtext>

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

<mtext>



</mtext>

<mtext>



</mtext>

<mi mathvariant="normal">

∣

</mi>

<mi>

W

</mi>
</mrow>

<annotation encoding="application/x-tex">

\phi_B\,\, |\,\,V_{bi} \,\,| W

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

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord">

∣

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mspace" style="margin-right:0.1667em;">



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

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord">

∣

</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

W

</span>
</span>
</span>
</span>

for n-type and p-type

> 对于耗尽区宽度来说没有本质区别 都是用对应侧的掺杂浓度

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 50.4%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="image.png" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture7-24.webp" />
      </p>
    </td>
    
    
      <td style="width: 49.6%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="image.png" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture7-31.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

### **Current Flow in Schottky Junction**   **N****-type**

#### **Schottky结分析**

![image.png](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture7-10.webp)

<mark>

**Schottky 结电流由多数载流子主导（majority-carrier flow across the MS junction）**

</mark>



1. **热平衡状态（Thermal Equilibrium）：**
在此种状态下，<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

E

</mi>

<mo>

−

</mo>

<msub>
<mi>

E

</mi>

<mi>

f

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

ϕ

</mi>

<mi>

B

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

E - E_f = q\phi_B = qV_{bi}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0576em;">

E

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

q

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

,这就定义了我们的**内建电场Built-in Electric Field，**同时也可以得到具体表达式：

> 借助<span className="katex">
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
> C
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
> n= N_d = N_c e^{-\frac{E_C-E_F}{kT}}
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
> <span className="strut" style="height:1.2504em;vertical-align:-0.15em;">
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
> <span className="vlist" style="height:1.1004em;">
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
> <span className="vlist" style="height:1.0534em;">
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
> <span className="mord,mathnormal,mtight" style="margin-right:0.0715em;">
> 
> C
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
> </span>
> </span>
> </span>
> 
> 可以计算<span className="katex">
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
> C
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
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> E_C - E_F
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
> <span className="mord,mathnormal,mtight" style="margin-right:0.0715em;">
> 
> C
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
> , 可得

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

q

</mi>

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

<mi>

q

</mi>

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

C

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

<mo>

=

</mo>

<mi>

q

</mi>

<mo stretchy="false">

(

</mo>

<msub>
<mi mathvariant="normal">

Φ

</mi>

<mi>

M

</mi>
</msub>

<mo>

−

</mo>

<mi>

χ

</mi>

<mo stretchy="false">

)

</mo>

<mo>

−

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

l

</mi>

<mi>

n

</mi>

<mo fence="false" stretchy="true" minsize="2.4em" maxsize="2.4em">

(

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

<msub>
<mi>

N

</mi>

<mi>

d

</mi>
</msub>
</mfrac>

<mo fence="false" stretchy="true" minsize="2.4em" maxsize="2.4em">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

qV_{bi} = q\phi_{Bn} - (E_C - E_F) = q(\Phi_M-\chi) - \frac{kT}{q}ln\bigg( \frac{N_c}{N_d} \bigg)

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
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

q

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

<span className="mord,mathnormal" style="margin-right:0.0359em;">

q

</span>

<span className="mopen">

(

</span>

<span className="mord">
<span className="mord">

Φ

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

M

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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

<span className="mord,mathnormal">

χ

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
<span className="strut" style="height:2.4em;vertical-align:-0.95em;">



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

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

n

</span>

<span className="mord">
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
<span className="delimsizing,size3">

)

</span>
</span>
</span>
</span>
</span>
</span>

1. **正向偏置（Forward Bias）**
  - 正偏电子需要跨越的势垒为：<span className="katex">
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
  
  , 势垒降低，电子更容易跨越界面
  - **主导过程**：电子从**半导体 → 金属**的扩散/发射（diffusion from semiconductor into metal dominates）
  - 结果：电流明显增大
2. **反向偏置（Reverse Bias）**
  - 反偏电子需要跨越的势垒为<span className="katex">
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
  
  +
  
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
  
  V_{bi} + V_A
  
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
  
  +
  
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
  
  ，势垒升高/耗尽区加宽
  - **主导过程**：电子从**金属 → 半导体**的扩散/发射（diffusion from metal into semiconductor dominates）
  - 结果：电流较小（接近饱和的反向电流）

- **对比**
  - 正向：S → M 的电子流占主导
  - 反向：M → S 的电子流占主导

![image.png](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture7-15.webp)

- **平衡状态** <span className="katex">
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

=

</mo>

<mn>

0

</mn>
</mrow>

<annotation encoding="application/x-tex">

V_A= 0

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


  - 半导体**耗尽区**上的电压降 = **内建电压** <span className="katex">
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
- **加外加****栅极****电压** <span className="katex">
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

<mo mathvariant="normal">

≠

</mo>

<mn>

0

</mn>
</mrow>

<annotation encoding="application/x-tex">

V_A \neq 0

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



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


  - 半导体**耗尽区**上的电压降 = (<span className="katex">
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
  
   - <span className="katex">
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
  
  )

##### 有外加反向电压的W计算公式

![image.png](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture7-34.webp)

#### 热电子发射理论

![image.png](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture7-02.webp)

半导体里的电子有热运动，只要它在垂直于界面的方向上速度够大，就能够越过金属/半导体势垒进入金属，从而形成电流。最后能够推导出电流公式：

![image.png](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture7-09.webp)

### 肖特基结小信号电容

![image.png](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture7-19.webp)

肖特基结中储存的电荷会随外加电压的变化而变化，因此外加交流电时候，会有一些位移电流流过。

我们把W展开带入上面的电容公式，会有：

![image.png](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture7-03.webp)

知道<span className="katex">
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

和<span className="katex">
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
</mrow>

<annotation encoding="application/x-tex">

N_D

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
</span>
</span>
</span>

可以知道<span className="katex">
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

，再知道一个接触面积A可以知道电容。

### 应用

Schottky 二极管（热发射主导）的形式：

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

<mrow>
<mo fence="true">

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

<mo fence="true">

)

</mo>
</mrow>
</mrow>

<annotation encoding="application/x-tex">

I = I_0\left(e^{qV/kT}-1\right)

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
<span className="strut" style="height:1.8em;vertical-align:-0.65em;">



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

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="minner">
<span className="mopen,delimcenter" style="top:0em;">
<span className="delimsizing,size2">

(

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
</span>

以及反向饱和电流（尺度因子）：

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

K

</mi>

<msup>
<mi>

T

</mi>

<mn>

2

</mn>
</msup>

<msup>
<mi>

e

</mi>

<mrow>
<mo>

−

</mo>

<mi>

q

</mi>

<msub>
<mi mathvariant="normal">

Φ

</mi>

<mi>

B

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

I_0 = AKT^2 e^{-q\Phi_B/kT}

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
<span className="strut" style="height:0.938em;">



</span>

<span className="mord,mathnormal">

A

</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

K

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.1389em;">

T

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

<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

q

</span>

<span className="mord,mtight">
<span className="mord,mtight">

Φ

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3448em;">
<span style="top:-2.3567em;margin-left:0em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
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

- <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi mathvariant="normal">

Φ

</mi>

<mi>

B

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

\Phi_B

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord">

Φ

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

 是 Schottky 势垒高度
- <span className="katex">
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

 是面积相关项（或含 Richardson 常数的等效系数）
- 关键点:  <span className="katex">
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

 对 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi mathvariant="normal">

Φ

</mi>

<mi>

B

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

\Phi_B

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord">

Φ

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

 指数敏感，<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi mathvariant="normal">

Φ

</mi>

<mi>

B

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

\Phi_B

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord">

Φ

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

 越小，<span className="katex">
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

 越大。

![image.png](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture7-35.webp)

![image.png](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture7-28.webp)

图里虚线/点线是 Schottky diode，实线是 PN junction diode。可以看到：

在同样电流下，Schottky 的曲线更靠左 → 需要的 <span className="katex">
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

 更小， 也就是 <mark>

**正向压降更小**

</mark>

<mark>

（forward drop 更低)

</mark>

原因就是上面说的：Schottky 的 <span className="katex">
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

 通常更大，所以要达到同样的 <span className="katex">
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

，所需的 <span className="katex">
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

 更小。

<mark>

**因此 Schottky 二极管低压、大电流整流首选**

</mark>



### 肖特基结和PN结的对比

#### 不同之处 ｜ The Difference

![image.png](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture7-05.webp)

主要的不同之处在于：

1. 在M/S Junction中，对**电流起主导作用的是**<mark>

**多数载流子**

</mark>
2. 在PN  Junction中， 对**电流起主导作用的是**<mark>

**少数载流子**

</mark>

##### 其他器件表现上的不同

1. 开关速度与反向恢复（Switching / Reverse recovery）

  - **M/S（肖特基）**：多数载流子器件，基本**不存储少数载流子电荷**
  → **开关更快**、**几乎没有反向恢复时间**（reverse recovery 很小）。
  - **PN 结**：正向导通时会有少数载流子注入并在两侧“存储”（stored charge）
  → 关断时要先清掉存储电荷
  → **反向恢复明显**、高速下损耗更大。
2. 正向压降与导通损耗（Forward drop / Conduction loss）

  - **肖特基**：势垒导通，通常**正向压降低**（常见 0.2–0.4 V 量级，取决于材料与电流）
  → 低压大电流场景导通损耗更小。
  - **PN 结**：需要少数载流子注入，典型硅二极管 **约 0.6–0.8 V**
  → 在低压系统里损耗更明显。
3. 反向漏电与温度敏感性（Reverse leakage / Temperature dependence）

  - **肖特基**：反向电流主要来自热发射等机制，通常**反向漏电更大**，且**随温度上升更快**
  → 高温下漏电与热稳定性更需要关注。
  - **PN 结**：反向漏电通常更小（同等级工艺与器件下）
  → 高温也会上升，但一般**比肖特基更“耐漏”**。
4. 耐压能力（Breakdown voltage）

  - **肖特基**：受界面电场与势垒限制，通常**耐压较低**（同体积/工艺下）
  → 高耐压要靠结构优化或换材料（SiC 肖特基可显著提高耐压）。
  - **PN 结**：通过漂移区设计更容易实现**高耐压**（功率二极管常见）。
5. 反向击穿电压

  - **PN 结**：反向阻断靠“耗尽区电场”支撑，击穿点主要由半导体达到<span className="katex">
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
  
  （雪崩/齐纳）决定；漏电多为耗尽区产生电流，通常较小，所以耐压能做到更接近理论值。
  - **肖特基结：虽然雪崩也发生在半导体里，但反偏时界面强电场会让势垒降低+变薄**，多数载流子通过**热发射/隧穿**形成较大反向电流，往往在到达雪崩条件之前就已受限（漏电、发热、边缘提前失效），所以“可用反向耐压”常比 PN 结低。

## **Ohmic Contacts**欧姆接触

### 应用

MOSFET 栅极电极、MOSFET 源/漏接触、互连：通孔/塞（via/plug）都会用到欧姆接触

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 52.8%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="image.png" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture7-12.webp" />
      </p>
    </td>
    
    
      <td style="width: 47.2%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="image.png" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture7-07.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

实际情况中，**大多数 M–S 接触是整流的（rectifying）**也就是说它更像一个肖特基二极管：一个方向电流大，反方向电流小。**如果希望接触在两个方向都容易导电**<mark>

**（非整流/欧姆接触）**

</mark>

常用的方法是把半导体在接触区<mark>

**非常重掺杂（very heavily dope**

</mark>

<mark>

**d**

</mark>

<mark>

**）**

</mark>

。

- **重掺杂为什么有效？**
因为重掺杂会让半导体一侧的**耗尽层宽度 (W)** 变得非常窄（(W) 变小）。
- **(W) 很窄会带来什么结果？**
即使界面仍然存在势垒，高度可能没完全消失，但由于势垒“很薄”，载流子可以通过**量子隧穿（tunnel）直接穿过势垒→ 于是接触电阻降低，表现为双向都更容易导通**（更像欧姆接触）。

### **Quantum Tunneling Phenomenon** **｜** **量子隧穿效应**

![image.png](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture7-27.webp)

电子有概率穿过势垒，那么这个概率，我们用量子力学的势阱模型可以计算得出，对于宽度为T的能垒，隧穿概率为：

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

≈

</mo>

<mi>

exp

</mi>

<mo>

⁡

</mo>

<mrow>
<mo fence="true">

(

</mo>

<mo>

−

</mo>

<mn>

2

</mn>

<mi>

T

</mi>

<msqrt>
<mrow>
<mfrac>
<mrow>
<mn>

8

</mn>

<msup>
<mi>

π

</mi>

<mn>

2

</mn>
</msup>

<mi>

m

</mi>
</mrow>

<msup>
<mi>

h

</mi>

<mn>

2

</mn>
</msup>
</mfrac>

<mo stretchy="false">

(

</mo>

<msub>
<mi>

V

</mi>

<mi>

H

</mi>
</msub>

<mo>

−

</mo>

<mi>

E

</mi>

<mo stretchy="false">

)

</mo>
</mrow>
</msqrt>

<mo fence="true">

)

</mo>
</mrow>
</mrow>

<annotation encoding="application/x-tex">

P \approx \exp\left(-2T\sqrt{\frac{8\pi^2 m}{h^2}(V_H - E)}\right)

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

≈

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:3em;vertical-align:-1.25em;">



</span>

<span className="mop">

exp

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="minner">
<span className="mopen,delimcenter" style="top:0em;">
<span className="delimsizing,size4">

(

</span>
</span>

<span className="mord">

−

</span>

<span className="mord">

2

</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

T

</span>

<span className="mord,sqrt">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:1.6994em;">
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
<span className="vlist" style="height:1.4171em;">
<span style="top:-2.314em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord,mathnormal">

h

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

8

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

π

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

<span className="mord,mathnormal">

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
<span className="mord,mathnormal,mtight" style="margin-right:0.0813em;">

H

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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

<span className="mord,mathnormal" style="margin-right:0.0576em;">

E

</span>

<span className="mclose">

)

</span>
</span>
</span>

<span style="top:-3.6594em;">
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
<span className="vlist" style="height:0.7406em;">
<span>



</span>
</span>
</span>
</span>
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

其中<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

V

</mi>

<mi>

H

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

V_H

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
<span className="mord,mathnormal,mtight" style="margin-right:0.0813em;">

H

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

为势垒高度， <span className="katex">
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

为当前电子的能量

![image.png](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture7-16.webp)

应用到电子能带里面：首先等效的势垒厚度近似为<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

T

</mi>

<mo>

≈

</mo>

<mfrac>
<mn>

1

</mn>

<mn>

2

</mn>
</mfrac>

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

<mo>

=

</mo>

<msqrt>
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

<mi>

D

</mi>
</msub>
</mrow>
</mfrac>
</msqrt>
</mrow>

<annotation encoding="application/x-tex">

T \approx \frac{1}{2} W_{dep} = \sqrt{\frac{\varepsilon_s\phi_{Bn}}{2qN_D}}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

T

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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.84em;vertical-align:-0.6294em;">



</span>

<span className="mord,sqrt">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:1.2106em;">
<span className="svg-align" style="top:-3.8em;">
<span className="pstrut" style="height:3.8em;">



</span>

<span className="mord" style="padding-left:1em;">
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
<span style="top:-2.3567em;margin-left:-0.109em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
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

<span style="top:-3.4461em;">
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
<span className="mord,mathnormal,mtight">

ϕ

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

<span style="top:-3.1706em;">
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
<span className="vlist" style="height:0.6294em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

, 那么带入上式，可得

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

<msup>
<mi>

e

</mi>

<mrow>
<mo>

−

</mo>

<mi>

H

</mi>

<mo stretchy="false">

(

</mo>

<msub>
<mi mathvariant="normal">

Φ

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

<mi mathvariant="normal">

/

</mi>

<msqrt>
<msub>
<mi>

N

</mi>

<mi>

D

</mi>
</msub>
</msqrt>
</mrow>
</msup>
</mrow>

<annotation encoding="application/x-tex">

P = e^{-H(\Phi_{Bn}-V_A)/\sqrt{N_D}}

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
<span className="strut" style="height:1.0155em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

e

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:1.0155em;">
<span style="top:-3.113em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">

−

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0813em;">

H

</span>

<span className="mopen,mtight">

(

</span>

<span className="mord,mtight">
<span className="mord,mtight">

Φ

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

<span className="mclose,mtight">

)

</span>

<span className="mord,mtight">

/

</span>

<span className="mord,sqrt,mtight">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.8606em;">
<span className="svg-align" style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mtight" style="padding-left:0.833em;">
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

<span style="top:-2.8206em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="hide-tail,mtight" style="min-width:0.853em;height:1.08em;">
<svg xmlns="http://www.w3.org/2000/svg" width="400em" height="1.08em" viewBox="0 0 400000 1080" preserveAspectRatio="xMinYMin slice">
<path d="M95,702
c-2.7,0,-7.17,-2.7,-13.5,-8c-5.8,-5.3,-9.5,-10,-9.5,-14
c0,-2,0.3,-3.3,1,-4c1.3,-2.7,23.83,-20.7,67.5,-54
c44.2,-33.3,65.8,-50.3,66.5,-51c1.3,-1.3,3,-2,5,-2c4.7,0,8.7,3.3,12,10
s173,378,173,378c0.7,0,35.3,-71,104,-213c68.7,-142,137.5,-285,206.5,-429
c69,-144,104.5,-217.7,106.5,-221
l0 -0
c5.3,-9.3,12,-14,20,-14
H400000v40H845.2724
s-225.272,467,-225.272,467s-235,486,-235,486c-2.7,4.7,-9,7,-19,7
c-6,0,-10,-1,-12,-3s-194,-422,-194,-422s-65,47,-65,47z
M834 80h400000v40h-400000z">



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
<span className="vlist" style="height:0.1794em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

对于隧穿概率而言：

1. <mark>

**隧穿概率**

</mark>

**是指数规律**——势垒降低，概率显著变大；
2. **掺杂越重**→ <span className="katex">
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
</mrow>

<annotation encoding="application/x-tex">

N_D

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
</span>
</span>
</span>

越大 →<span className="katex">
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

越大； 这就是“<mark>

重掺杂能做成欧姆接触

</mark>

”的根本。
3. **正向偏置** <span className="katex">
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

**增大** → <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mo stretchy="false">

(

</mo>

<msub>
<mi mathvariant="normal">

Φ

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

<annotation encoding="application/x-tex">

(\Phi_{Bn}-V_A)

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
<span className="mord">

Φ

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

<span className="mclose">

)

</span>
</span>
</span>
</span>

)变小 → <span className="katex">
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

变大 <mark>

正向更容易隧穿

</mark>

从隧穿概率我们可以得到<mark>

**隧穿电流**

</mark>



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

<mrow>
<mi>

S

</mi>

<mo>

→

</mo>

<mi>

M

</mi>
</mrow>
</msub>

<mo>

≈

</mo>

<mi>

q

</mi>

<mi>

P

</mi>

<msub>
<mi>

N

</mi>

<mi>

D

</mi>
</msub>

<msub>
<mi>

v

</mi>

<mrow>
<mi>

t

</mi>

<mi>

h

</mi>

<mi>

x

</mi>
</mrow>
</msub>

<mo>

=

</mo>

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

<msqrt>
<mfrac>
<mrow>
<mi>

k

</mi>

<mi>

T

</mi>
</mrow>

<mrow>
<mn>

2

</mn>

<mi>

π

</mi>

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
</mrow>
</mfrac>
</msqrt>

<msup>
<mi>

e

</mi>

<mrow>
<mo>

−

</mo>

<mi>

H

</mi>

<mo stretchy="false">

(

</mo>

<msub>
<mi mathvariant="normal">

Φ

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

<mi mathvariant="normal">

/

</mi>

<msqrt>
<msub>
<mi>

N

</mi>

<mi>

D

</mi>
</msub>
</msqrt>
</mrow>
</msup>
</mrow>

<annotation encoding="application/x-tex">

J_{S\to M} \approx qPN_D v_{thx} = qN_D \sqrt{\frac{kT}{2\pi m_n^*}}e^{-H(\Phi_{Bn}-V_A)/\sqrt{N_D}}

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
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.0962em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

S

</span>

<span className="mrel,mtight">

→

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.109em;">

M

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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
<span className="strut" style="height:0.8778em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

q

</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

t

</span>

<span className="mord,mathnormal,mtight">

h

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
<span className="strut" style="height:3.04em;vertical-align:-1.1869em;">



</span>

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

<span className="mord,sqrt">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:1.8531em;">
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
<span className="vlist" style="height:1.3714em;">
<span style="top:-2.314em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord">

2

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

π

</span>

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

<span style="top:-3.8131em;">
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
<span className="vlist" style="height:1.1869em;">
<span>



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
<span className="vlist" style="height:1.0155em;">
<span style="top:-3.113em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">

−

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0813em;">

H

</span>

<span className="mopen,mtight">

(

</span>

<span className="mord,mtight">
<span className="mord,mtight">

Φ

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

<span className="mclose,mtight">

)

</span>

<span className="mord,mtight">

/

</span>

<span className="mord,sqrt,mtight">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.8606em;">
<span className="svg-align" style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mtight" style="padding-left:0.833em;">
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

<span style="top:-2.8206em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="hide-tail,mtight" style="min-width:0.853em;height:1.08em;">
<svg xmlns="http://www.w3.org/2000/svg" width="400em" height="1.08em" viewBox="0 0 400000 1080" preserveAspectRatio="xMinYMin slice">
<path d="M95,702
c-2.7,0,-7.17,-2.7,-13.5,-8c-5.8,-5.3,-9.5,-10,-9.5,-14
c0,-2,0.3,-3.3,1,-4c1.3,-2.7,23.83,-20.7,67.5,-54
c44.2,-33.3,65.8,-50.3,66.5,-51c1.3,-1.3,3,-2,5,-2c4.7,0,8.7,3.3,12,10
s173,378,173,378c0.7,0,35.3,-71,104,-213c68.7,-142,137.5,-285,206.5,-429
c69,-144,104.5,-217.7,106.5,-221
l0 -0
c5.3,-9.3,12,-14,20,-14
H400000v40H845.2724
s-225.272,467,-225.272,467s-235,486,-235,486c-2.7,4.7,-9,7,-19,7
c-6,0,-10,-1,-12,-3s-194,-422,-194,-422s-65,47,-65,47z
M834 80h400000v40h-400000z">



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
<span className="vlist" style="height:0.1794em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

1. **重掺杂会极其显著地降低接触电阻**
2. 正向电压<span className="katex">
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

越大 →指数项显著增大 → 更易导通
3. <span className="katex">
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
</mrow>

<annotation encoding="application/x-tex">

m_n^*

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
</span>
</span>
</span>

越大→热速度变小且 <span className="katex">
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

 变大 → 隧穿更难
4. <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

T

</mi>
</mrow>

<annotation encoding="application/x-tex">

T

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

T

</span>
</span>
</span>
</span>

升高→热速度 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mo>

∝

</mo>

<msqrt>
<mi>

T

</mi>
</msqrt>
</mrow>

<annotation encoding="application/x-tex">

\propto\sqrt{T}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.4306em;">



</span>

<span className="mrel">

∝

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.04em;vertical-align:-0.1133em;">



</span>

<span className="mord,sqrt">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.9267em;">
<span className="svg-align" style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord" style="padding-left:0.833em;">
<span className="mord,mathnormal" style="margin-right:0.1389em;">

T

</span>
</span>
</span>

<span style="top:-2.8867em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="hide-tail" style="min-width:0.853em;height:1.08em;">
<svg xmlns="http://www.w3.org/2000/svg" width="400em" height="1.08em" viewBox="0 0 400000 1080" preserveAspectRatio="xMinYMin slice">
<path d="M95,702
c-2.7,0,-7.17,-2.7,-13.5,-8c-5.8,-5.3,-9.5,-10,-9.5,-14
c0,-2,0.3,-3.3,1,-4c1.3,-2.7,23.83,-20.7,67.5,-54
c44.2,-33.3,65.8,-50.3,66.5,-51c1.3,-1.3,3,-2,5,-2c4.7,0,8.7,3.3,12,10
s173,378,173,378c0.7,0,35.3,-71,104,-213c68.7,-142,137.5,-285,206.5,-429
c69,-144,104.5,-217.7,106.5,-221
l0 -0
c5.3,-9.3,12,-14,20,-14
H400000v40H845.2724
s-225.272,467,-225.272,467s-235,486,-235,486c-2.7,4.7,-9,7,-19,7
c-6,0,-10,-1,-12,-3s-194,-422,-194,-422s-65,47,-65,47z
M834 80h400000v40h-400000z">



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
<span className="vlist" style="height:0.1133em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

 上升（这里强调隧穿主导下的温度趋势；若热发射主导则会出现更强的温度指数项）

> 实现欧姆接触的关键不是一定把势垒高度降到 0，而是把势垒做得“足够薄”
> 
> 重掺杂 (<span className="katex">
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
> D
> 
> </mi>
> </msub>
> 
> <mo>
> 
> ↑
> 
> </mo>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> N_D\uparrow
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
> <span className="vlist" style="height:0.3283em;">
> <span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
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
> 
> <span className="mspace" style="margin-right:0.2778em;">
> 
> 
> 
> </span>
> 
> <span className="mrel">
> 
> ↑
> 
> </span>
> </span>
> </span>
> </span>
> 
> ) → 耗尽层 (<span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <mi>
> 
> W
> 
> </mi>
> 
> <mo>
> 
> ↓
> 
> </mo>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> W\downarrow
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
> <span className="mord,mathnormal" style="margin-right:0.1389em;">
> 
> W
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
> ↓
> 
> </span>
> </span>
> </span>
> </span>
> 
> ) → 隧穿概率 (<span className="katex">
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
> ↑
> 
> </mo>
> 
> <mo>
> 
> ↑
> 
> </mo>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> P\uparrow\uparrow
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
> ↑↑
> 
> </span>
> </span>
> </span>
> </span>
> 
> ) → 接触电阻很小 → I–V 近线性（欧姆）

### Specific contact resistivity

![image.png](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture7-01.webp)

接触电阻的定义是单位面积的电阻，于是公式为：

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

<mrow>
<mi>

c

</mi>

<mi>

o

</mi>

<mi>

n

</mi>

<mi>

t

</mi>

<mi>

a

</mi>

<mi>

c

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

ρ

</mi>

<mi>

c

</mi>
</msub>

<msub>
<mi>

A

</mi>

<mrow>
<mi>

c

</mi>

<mi>

o

</mi>

<mi>

n

</mi>

<mi>

t

</mi>

<mi>

a

</mi>

<mi>

c

</mi>

<mi>

t

</mi>
</mrow>
</msub>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

R_{contact} = \frac{\rho_c}{A_{contact}}

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
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:-0.0077em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

co

</span>

<span className="mord,mathnormal,mtight">

n

</span>

<span className="mord,mathnormal,mtight">

t

</span>

<span className="mord,mathnormal,mtight">

a

</span>

<span className="mord,mathnormal,mtight">

c

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
<span className="mord,mathnormal,mtight">

co

</span>

<span className="mord,mathnormal,mtight">

n

</span>

<span className="mord,mathnormal,mtight">

t

</span>

<span className="mord,mathnormal,mtight">

a

</span>

<span className="mord,mathnormal,mtight">

c

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

ρ

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

其中<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

A

</mi>

<mrow>
<mi>

c

</mi>

<mi>

o

</mi>

<mi>

n

</mi>

<mi>

t

</mi>

<mi>

a

</mi>

<mi>

c

</mi>

<mi>

t

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

A_{contact}

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
<span className="mord,mathnormal,mtight">

co

</span>

<span className="mord,mathnormal,mtight">

n

</span>

<span className="mord,mathnormal,mtight">

t

</span>

<span className="mord,mathnormal,mtight">

a

</span>

<span className="mord,mathnormal,mtight">

c

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

为接触面积

但对于实际的欧姆接触的电阻而言， 欧姆接触的电阻率还受到上述提到的量子效应的影响，这样会使得：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<msub>
<mi>

ρ

</mi>

<mi>

c

</mi>
</msub>

<mo>

∝

</mo>

<msup>
<mi>

e

</mi>

<mrow>
<mi>

H

</mi>

<msub>
<mi mathvariant="normal">

Φ

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

<mi mathvariant="normal">

/

</mi>

<msqrt>
<msub>
<mi>

N

</mi>

<mi>

D

</mi>
</msub>
</msqrt>
</mrow>
</msup>
</mrow>

<annotation encoding="application/x-tex">

\rho_c \propto e^{H\Phi_{Bn}/\sqrt{N_D}}

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

ρ

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

∝

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.0155em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

e

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:1.0155em;">
<span style="top:-3.113em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0813em;">

H

</span>

<span className="mord,mtight">
<span className="mord,mtight">

Φ

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

<span className="mord,sqrt,mtight">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.8606em;">
<span className="svg-align" style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mtight" style="padding-left:0.833em;">
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

<span style="top:-2.8206em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="hide-tail,mtight" style="min-width:0.853em;height:1.08em;">
<svg xmlns="http://www.w3.org/2000/svg" width="400em" height="1.08em" viewBox="0 0 400000 1080" preserveAspectRatio="xMinYMin slice">
<path d="M95,702
c-2.7,0,-7.17,-2.7,-13.5,-8c-5.8,-5.3,-9.5,-10,-9.5,-14
c0,-2,0.3,-3.3,1,-4c1.3,-2.7,23.83,-20.7,67.5,-54
c44.2,-33.3,65.8,-50.3,66.5,-51c1.3,-1.3,3,-2,5,-2c4.7,0,8.7,3.3,12,10
s173,378,173,378c0.7,0,35.3,-71,104,-213c68.7,-142,137.5,-285,206.5,-429
c69,-144,104.5,-217.7,106.5,-221
l0 -0
c5.3,-9.3,12,-14,20,-14
H400000v40H845.2724
s-225.272,467,-225.272,467s-235,486,-235,486c-2.7,4.7,-9,7,-19,7
c-6,0,-10,-1,-12,-3s-194,-422,-194,-422s-65,47,-65,47z
M834 80h400000v40h-400000z">



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
<span className="vlist" style="height:0.1794em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

> 想要小的接触电阻：**选小**<span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msub>
> <mi mathvariant="bold">
> 
> Φ
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
> \mathbf{\Phi_B}
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
> Φ
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3303em;">
> <span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
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
> ，并且 **做大** <span className="katex">
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
> <mi mathvariant="bold">
> 
> D
> 
> </mi>
> </msub>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> \mathbf{N_D}
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
> N
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3303em;">
> <span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mathbf,mtight">
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
> 。

## 总结Schittky Contact 与 Ohmic contact

![image.png](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/MicroelectronicDevices/Lecture7-14.webp)
