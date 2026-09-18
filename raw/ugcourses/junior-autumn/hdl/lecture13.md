# Lecture 13：浮点数标准

> IEEE 浮点数标准的表示与运算

## 浮点数标准

### 浮点数格式

#### IEEE 754标准

<alert type="info">

1. 对于上溢、下溢、舍入规范定义比较好
2. 但是难以较快执行

  1. 说明在当时定义标准上数值计算人员的话语权>硬件设计人员

</alert>

##### 小数的二进制表示法则

![image.png](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/Lecture13-01.webp)

**特殊例子——左移表示乘2、右移表示除2**

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 36.9%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="image.png" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/Lecture13-02.webp" />
      </p>
    </td>
    
    
      <td style="width: 63.1%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="image.png" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/Lecture13-03.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

**局限性：只能精确表示形式为**<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mfrac>
<mi>

x

</mi>

<msup>
<mn>

2

</mn>

<mi>

k

</mi>
</msup>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

\frac{x}{2^k}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.0528em;vertical-align:-0.3574em;">



</span>

<span className="mord">
<span className="mopen,nulldelimiter">



</span>

<span className="mfrac">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.6954em;">
<span style="top:-2.6426em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">
<span className="mord,mtight">

2

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.782em;">
<span style="top:-2.786em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0315em;">

k

</span>
</span>
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
<span className="vlist" style="height:0.3574em;">
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

**的数，其他形式的数都会被表示成无限小数**

![image.png](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/Lecture13-04.webp)

#### 浮点表示法

![image.png](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/Lecture13-05.webp)

对于这个浮点数的结构而言，同时也引入了约定俗成的<mark>

**规范**

</mark>



![image.png](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/Lecture13-06.webp)

1. **指数编码需要偏置值以便于把负指数映射到正数域中，以便于比较大小**
  1. 通常这个偏置的值取指数的位宽所能表示的数的最大值除以2附近的值

<alert type="tip">

例如对于单精度 exp8位，最大指数位为<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msup>
<mn>

2

</mn>

<mn>

8

</mn>
</msup>

<mo>

−

</mo>

<mn>

1

</mn>

<mo>

=

</mo>

<mn>

256

</mn>

<mo>

−

</mo>

<mn>

1

</mn>

<mo>

=

</mo>

<mn>

255

</mn>
</mrow>

<annotation encoding="application/x-tex">

2^8 - 1 = 256-1 = 255

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8974em;vertical-align:-0.0833em;">



</span>

<span className="mord">
<span className="mord">

2

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

8

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
<span className="strut" style="height:0.7278em;vertical-align:-0.0833em;">



</span>

<span className="mord">

256

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

255

</span>
</span>
</span>
</span>

,指数位的数值取值范围是<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mo stretchy="false">

[

</mo>

<mn>

0

</mn>

<mo separator="true">

,

</mo>

<mn>

255

</mn>

<mo stretchy="false">

]

</mo>
</mrow>

<annotation encoding="application/x-tex">

[0, 255]

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mopen">

[

</span>

<span className="mord">

0

</span>

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord">

255

</span>

<span className="mclose">

]

</span>
</span>
</span>
</span>



需要映射到<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mo stretchy="false">

[

</mo>

<mo>

−

</mo>

<mn>

126

</mn>

<mo separator="true">

,

</mo>

<mn>

127

</mn>

<mo stretchy="false">

]

</mo>
</mrow>

<annotation encoding="application/x-tex">

[-126,127]

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mopen">

[

</span>

<span className="mord">

−

</span>

<span className="mord">

126

</span>

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord">

127

</span>

<span className="mclose">

]

</span>
</span>
</span>
</span>

这个范围之内，因此需要加偏置bias = 127

</alert>

1. 这个值对于一个位宽为e的数来说<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msup>
<mn>

2

</mn>

<mrow>
<mi>

e

</mi>

<mo>

−

</mo>

<mn>

1

</mn>
</mrow>
</msup>

<mo>

−

</mo>

<mn>

1

</mn>
</mrow>

<annotation encoding="application/x-tex">

{2^{e-1} - 1}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8974em;vertical-align:-0.0833em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord">

2

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
<span className="mord,mathnormal,mtight">

e

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
</span>
</span>
</span>
</span>

<alert type="tip">

例如对于 exp e位，最大指数位为<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msup>
<mn>

2

</mn>

<mi>

e

</mi>
</msup>

<mo>

−

</mo>

<mn>

1

</mn>
</mrow>

<annotation encoding="application/x-tex">

2^e - 1

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.7477em;vertical-align:-0.0833em;">



</span>

<span className="mord">
<span className="mord">

2

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

e

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
<span className="strut" style="height:0.6444em;">



</span>

<span className="mord">

1

</span>
</span>
</span>
</span>

,指数位的数值取值范围是<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mo stretchy="false">

[

</mo>

<mn>

0

</mn>

<mo separator="true">

,

</mo>

<msup>
<mn>

2

</mn>

<mi>

e

</mi>
</msup>

<mo>

−

</mo>

<mn>

1

</mn>

<mo stretchy="false">

]

</mo>
</mrow>

<annotation encoding="application/x-tex">

[0, 2^e - 1]

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mopen">

[

</span>

<span className="mord">

0

</span>

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord">
<span className="mord">

2

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

e

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

]

</span>
</span>
</span>
</span>

,去除头和尾（000...0 111...1）之后就是<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mo stretchy="false">

[

</mo>

<mn>

1

</mn>

<mo separator="true">

,

</mo>

<msup>
<mn>

2

</mn>

<mi>

e

</mi>
</msup>

<mo>

−

</mo>

<mn>

2

</mn>

<mo stretchy="false">

]

</mo>
</mrow>

<annotation encoding="application/x-tex">

[1, 2^e - 2]

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mopen">

[

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
<span className="mord">

2

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

e

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

2

</span>

<span className="mclose">

]

</span>
</span>
</span>
</span>

，左右两边同时减去<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mrow>
<msup>
<mn>

2

</mn>

<mrow>
<mi>

e

</mi>

<mo>

−

</mo>

<mn>

1

</mn>
</mrow>
</msup>

<mo>

−

</mo>

<mn>

1

</mn>
</mrow>

<mo stretchy="false">

(

</mo>

<mo>

=

</mo>

<mfrac>
<mrow>
<msup>
<mn>

2

</mn>

<mi>

e

</mi>
</msup>

<mo>

−

</mo>

<mn>

2

</mn>
</mrow>

<mn>

2

</mn>
</mfrac>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

{2^{e-1} - 1}(= \frac{2^e - 2}{2})

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.0641em;vertical-align:-0.25em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord">

2

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
<span className="mord,mathnormal,mtight">

e

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
</span>

<span className="mopen">

(

</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.256em;vertical-align:-0.345em;">



</span>

<span className="mord">
<span className="mopen,nulldelimiter">



</span>

<span className="mfrac">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.911em;">
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
<span className="mord,mtight">

2

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.7385em;">
<span style="top:-2.931em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
<span className="mord,mathnormal,mtight">

e

</span>
</span>
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

<span className="mclose">

)

</span>
</span>
</span>
</span>

即可得到原来的指数位<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mo stretchy="false">

[

</mo>

<mo>

−

</mo>

<mo stretchy="false">

(

</mo>

<msup>
<mn>

2

</mn>

<mi>

e

</mi>
</msup>

<mo>

−

</mo>

<mn>

2

</mn>

<mo stretchy="false">

)

</mo>

<mo separator="true">

,

</mo>

<msup>
<mn>

2

</mn>

<mi>

e

</mi>
</msup>

<mo>

−

</mo>

<mn>

1

</mn>

<mo stretchy="false">

]

</mo>
</mrow>

<annotation encoding="application/x-tex">

[-(2^e - 2), 2^e - 1]

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mopen">

[

</span>

<span className="mord">

−

</span>

<span className="mopen">

(

</span>

<span className="mord">
<span className="mord">

2

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

e

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

2

</span>

<span className="mclose">

)

</span>

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord">
<span className="mord">

2

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

e

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

]

</span>
</span>
</span>
</span>

,所以偏置值就是<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msup>
<mn>

2

</mn>

<mrow>
<mi>

e

</mi>

<mo>

−

</mo>

<mn>

1

</mn>
</mrow>
</msup>

<mo>

−

</mo>

<mn>

1

</mn>
</mrow>

<annotation encoding="application/x-tex">

{2^{e-1} - 1}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8974em;vertical-align:-0.0833em;">



</span>

<span className="mord">
<span className="mord">
<span className="mord">

2

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
<span className="mord,mathnormal,mtight">

e

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
</span>
</span>
</span>
</span>
</alert>

1. 尾数（小数点）编码忽略了前导位1，即尾数编码只考虑小数点之后的部分

##### 举例说明

![image.png](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/Lecture13-07.webp)

##### 非规范数

![image.png](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/Lecture13-08.webp)

1. 非规范数就是指数位全部是0，即<mark>

**当指数位全部是0的时候，进入非规范表示法**

</mark>
2. 此时代表指数位数为1-Bias ,小数将表示为0.xxxx 注意此时是<mark>

**0.x  是以0开头的0.x**

</mark>
3. 精度丧失问题
![image.png](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/Lecture13-09.webp)

###### **举例说明**

![image.png](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/Lecture13-10.webp)

##### 特殊值

![image.png](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/Lecture13-11.webp)

1. 当指数位全是1时，若小数位全是0，那么则代表无穷，正负无穷由符号位决定
2. 当指数位全是1，但小数位不为0时，代表无法确定的数值NAN

#### 总结

##### 编码范围

![image.png](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/Lecture13-12.webp)

##### 数值分布

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 57.4%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="image.png" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/Lecture13-13.webp" />
      </p>
    </td>
    
    
      <td style="width: 42.6%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="image.png" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/Lecture13-14.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>
