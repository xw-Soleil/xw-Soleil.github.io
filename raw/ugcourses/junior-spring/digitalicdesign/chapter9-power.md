# Chapter 9：功耗 Power

> 工艺缩放对功耗的影响，以及动态与静态功耗的来源和优化手段。

🛠️表示还在修缮

‼️🌟表示比较重要 怀疑只有这些会考，其他有印象就行

## 一、🛠️Scaling（只整理了一部分，等整章弄完了再来补充，感觉是科普，不知道能考啥）

### Technology Scaling Models（工艺/技术缩放模型）

#### Full Scaling（Constant Electrical Field）完全缩放（恒定电场缩放）

- 理想模型——尺寸和电压按照相同的缩放因子 **S** 一起缩小。
- 这样做的好处是**电场强度基本不变。**因为电场大致可以理解为<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

E

</mi>

<mo>

=

</mo>

<mfrac>
<mi>

V

</mi>

<mi>

L

</mi>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

E= \frac{V}{L}

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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

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
<span className="mord,mathnormal,mtight" style="margin-right:0.2222em;">

V

</span>
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

,器件可靠性比较好，功耗也会降低。但是它是比较理想化的模型，因为实际中电压不能无限降低，否则晶体管开关速度、噪声容限都会受到影响。

#### Fixed Voltage Scaling  固定电压缩放

- 直到最近都曾是最常见的模型——只有器件尺寸缩小，电压保持不变。这样可以让芯片速度提高，因为尺寸变小、电容减小，晶体管开关更快。但是问题是：尺寸变小了，电压不变，电场会变大。
- 这容易带来：功耗密度升高； 器件发热严重；  可靠性下降；  氧化层击穿、热载流子效应等问题加重。 所以这种模型在早期较常见，但随着工艺越来越小，已经越来越不适合。

#### General Scaling  **通用缩放 / 一般缩放**

- 尺寸会缩小，电压也会降低，但二者不是按照完全相同的比例缩放，是现代芯片设计通常采用的折中方式。

### Tox Scaling Challenge: Gate Leakage氧化层厚度缩放的挑战：栅极漏电

- 随着工艺尺寸不断缩小，晶体管的沟道长度变短，为了保证栅极还能有效控制沟道，栅氧化层厚度 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

T

</mi>

<mrow>
<mi>

o

</mi>

<mi>

x

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

T_{ox}

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

T

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.1389em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

o

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

也必须变薄。
- 当 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

T

</mi>

<mrow>
<mi>

o

</mi>

<mi>

x

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

T_{ox}

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

T

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.1389em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

o

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

 变得非常薄时，电子可以通过 **量子隧穿效应** 穿过原本应该绝缘的氧化层，从栅极流向沟道或衬底，形成 **栅极漏电流** <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

I

</mi>

<mi>

G

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

I_G

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

。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter9-Power-01.webp)

- 这会带来：

  1. **静态功耗增加**
  即使晶体管不工作，也会有漏电流流过，芯片待机功耗变大。
  2. **发热严重**
  漏电流越大，功耗越大，芯片温度也更难控制。
  3. **可靠性下降**
  长期漏电和高电场会影响栅氧化层寿命，增加器件失效风险。
  4. **继续缩放变得困难**
  单纯靠继续减薄 <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mi>
  
  S
  
  </mi>
  
  <mi>
  
  i
  
  </mi>
  
  <msub>
  <mi>
  
  O
  
  </mi>
  
  <mn>
  
  2
  
  </mn>
  </msub>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  SiO_2
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:0.8333em;vertical-align:-0.15em;">
  
  
  
  </span>
  
  <span className="mord,mathnormal" style="margin-right:0.0576em;">
  
  S
  
  </span>
  
  <span className="mord,mathnormal">
  
  i
  
  </span>
  
  <span className="mord">
  <span className="mord,mathnormal" style="margin-right:0.0278em;">
  
  O
  
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
  
   已经不可行。
- 改善这个问题的工艺和材料创新：**High-k 介质 + 金属栅技术.**这样，在电学效果上，让栅极看起来像拥有很薄的氧化层；但在物理厚度上，实际绝缘层可以做得更厚。

### Three Key Enablers for Continued Scaling**支撑工艺继续缩放的三个关键技术**

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter9-Power-02.webp)

#### Strained silicon introduced in 90nm 应变硅技术在 90 nm 节点引入

- 普通硅材料中，电子和空穴的运动速度有限。通过让硅晶格产生适当拉伸或压缩，可以改善载流子迁移率，让电子或空穴运动得更快。结果是：<span className="katex">
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

d

</mi>

<mi>

r

</mi>

<mi>

i

</mi>

<mi>

v

</mi>

<mi>

e

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

I_{drive}

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
<span className="mord,mathnormal,mtight">

d

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal,mtight">

i

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

v

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

增大，也就是晶体管的驱动电流变大，开关速度提高。
- 这样做的好处是即使不继续大幅减薄栅氧化层，也能提升晶体管性能，从而缓解了栅氧化层继续缩薄带来的漏电问题。

#### High-K metal gate introduced in 45nm **High-K 金属栅技术在 45 nm 节点引入**

- 前面讲过，电学上等效为很薄的氧化层，但物理上可以做得更厚。这样既能保持栅极对沟道的控制能力，又能显著降低隧穿漏电流

#### Tri-gate introduced in 22nm **三栅极 / Tri-gate 晶体管在 22 nm 节点引入finFET**

- 传统 MOSFET 是平面结构，栅极主要从上方控制沟道。随着沟道越来越短，栅极对沟道的控制变弱，会出现短沟道效应，例如关不住、电流泄漏增大等问题。
- Tri-gate 把沟道做成立体鳍片形状，栅极从上方和两侧包围沟道，相当于从多个方向控制电流。这样可以增强栅极控制能力；降低短沟道效应；减小漏电；支持晶体管继续缩小。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter9-Power-03.webp)

### Changes in Scaling工艺缩放方式的变化

<table>
<thead>
  <tr>
    <th>
      对比维度
    </th>
    
    <th>
      传统工艺缩放
    </th>
    
    <th>
      现在的工艺缩放
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      成本变化
    </td>
    
    <td>
      缩放降低成本
    </td>
    
    <td>
      缩放仍然可以降低成本
    </td>
  </tr>
  
  <tr>
    <td>
      性能提升来源
    </td>
    
    <td>
      缩放直接推动性能提升
    </td>
    
    <td>
      材料、器件结构和工艺创新推动性能提升
    </td>
  </tr>
  
  <tr>
    <td>
      主要限制因素
    </td>
    
    <td>
      主要受性能限制
    </td>
    
    <td>
      主要受功耗限制
    </td>
  </tr>
  
  <tr>
    <td>
      主导功耗类型
    </td>
    
    <td>
      动态功耗占主导
    </td>
    
    <td>
      待机功耗 / 漏电功耗占主导
    </td>
  </tr>
  
  <tr>
    <td>
      设计与工艺关系
    </td>
    
    <td>
      设计和工艺相对独立
    </td>
    
    <td>
      设计和工艺高度相关、需要协同优化
    </td>
  </tr>
  
  <tr>
    <td>
      核心特点
    </td>
    
    <td>
      晶体管变小通常就能带来更快、更便宜的芯片
    </td>
    
    <td>
      单纯缩小尺寸已经不够，需要材料、结构和设计共同优化
    </td>
  </tr>
  
  <tr>
    <td>
      典型问题
    </td>
    
    <td>
      如何继续提高速度
    </td>
    
    <td>
      如何控制漏电、功耗、发热和工艺复杂度
    </td>
  </tr>
</tbody>
</table>

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter9-Power-04.webp)

<table>
<thead>
  <tr>
    <th>
      颜色 / 符号
    </th>
    
    <th>
      含义
    </th>
    
    <th>
      趋势
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      橙色三角形
    </td>
    
    <td>
      晶体管数量，单位是 thousands
    </td>
    
    <td>
      持续快速上升
    </td>
  </tr>
  
  <tr>
    <td>
      蓝色圆点
    </td>
    
    <td>
      单线程性能
    </td>
    
    <td>
      早期快速提升，后期增速变慢
    </td>
  </tr>
  
  <tr>
    <td>
      绿色方块
    </td>
    
    <td>
      时钟频率，MHz
    </td>
    
    <td>
      2000 年前快速上升，之后趋于平缓
    </td>
  </tr>
  
  <tr>
    <td>
      红色倒三角
    </td>
    
    <td>
      典型功耗，Watts
    </td>
    
    <td>
      逐渐上升，但不能无限增加
    </td>
  </tr>
  
  <tr>
    <td>
      黑色菱形
    </td>
    
    <td>
      逻辑核心数
    </td>
    
    <td>
      2000 年后明显增加
    </td>
  </tr>
</tbody>
</table>

2000 年后的 transition：转向多核黑色菱形表示 **Number of Logical Cores，逻辑核心数**。可以看到，在 2000 年前后，核心数基本很少，接近 1；但之后开始明显增加。

这是因为频率提高受限后，厂商开始把更多晶体管用于增加多个核心，让多个核心并行工作。

### 这一部分的总结

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter9-Power-05.webp)

中文人话：早期工艺缩放能够同时带来面积减小、速度提升和功耗降低，因此晶体管越做越小，芯片自然变得更快、更便宜。但在 130 nm 左右以后，传统缩放遇到了栅氧化层过薄和漏电流增大的问题，单纯缩小尺寸不再足够。因此，后续工艺发展越来越依赖材料和器件结构创新，例如 High-K 金属栅、应变硅和 FinFET。

## 二、Power and energy

### Why Power matters

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter9-Power-06.webp)

- 从 1971 年到 2000 年左右，Intel 处理器从 4004、8008、8086、286、386、486 发展到 Pentium、P6 的过程中，功耗整体呈持续上升趋势，而且纵轴采用对数刻度，说明功耗增长幅度很大：早期处理器功耗不到 1W，而后期逐渐上升到十几瓦甚至更高。它强调的是，随着晶体管数量增加和工作频率提升，处理器性能虽然不断增强，但功耗和发热也迅速变成关键限制因素，因此芯片设计不能只追求速度提升，还必须重视功耗控制、散热能力和可靠性问题。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter9-Power-07.webp)

- 处理器功耗密度随工艺和性能提升而快速上升，当单位面积发热接近电热板甚至更高水平时，芯片已经不能单纯依靠提高频率来提升性能，必须重点考虑低功耗设计、散热和能效优化。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter9-Power-08.webp)

- 功耗影响的：封装成本、电源轨设计、芯片和系统散热成本、抗噪声能力和系统可靠性、便携设备中的电池寿命、环境问题。

### Power and Energy

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter9-Power-09.webp)

平均功率的计算⬆️

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter9-Power-10.webp)

功率表示单位时间消耗能量的快慢，能量表示完成一段时间或一个任务总共消耗了多少；低功率设计如果运行时间变长，最终消耗的能量不一定更少。

### 🌟数字集成电路中的功耗来源（感觉和考试相关性大一点）

#### 铺垫：各个器件的功率计算

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter9-Power-11.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter9-Power-12.webp)

> **Ratioed circuits**,比率逻辑电路输出电平不仅由逻辑决定，还依赖于上拉网络和下拉网络的驱动强弱比例。比如psnudo-nMOS电路。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter9-Power-13.webp)

#### 开关电流

##### 铺垫：电容功耗

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter9-Power-14.webp)

##### 开关波形图

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter9-Power-15.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter9-Power-16.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter9-Power-17.webp)

##### <mark>🌟🌟开关功耗‼️可能有计算</mark>

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter9-Power-18.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter9-Power-19.webp)

<mark>

可能会考计算，例子：

</mark>



![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter9-Power-20.webp)

#### 短路电流

##### 概念：

当晶体管发生切换时，nMOS 网络和 pMOS 网络可能会在瞬间同时导通。

- 这会导致一个短暂的短路电流脉冲。
- 如果输入和输出的上升/下降时间相当，那么这部分功耗通常小于动态功耗的 10%。
- 我们通常会忽略这一部分功耗。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter9-Power-21.webp)

##### 发生过程：

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter9-Power-22.webp)

##### 影响因素

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter9-Power-23.webp)

##### 减小短路电流的方法：

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter9-Power-24.webp)

短路功耗主要来自输入翻转时 PMOS 和 NMOS 的短暂同时导通。输入边沿越慢，同时导通时间越长；输出边沿过慢又会把慢边沿传给下一级。因此在多级逻辑链中，应让输入、输出 rise/fall time 大致匹配，使每一级都不承受过慢的边沿，从而降低整体短路功耗。

#### Leakage漏电

主要有gate leakage , drain junction leakage , sub-threshold current.

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter9-Power-25.webp)

##### Gate Leakage栅极漏电

- 定义：MOS 管在关断或工作时，**栅极通过栅氧化层产生的漏电流，**和栅氧化层厚度 <span className="katex">
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

o

</mi>

<mi>

x

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

t_{ox}

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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

o

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

、栅源电压 <span className="katex">
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

g

</mi>

<mi>

s

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

V_{gs}

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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

g

</span>

<span className="mord,mathnormal,mtight">

s

</span>
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

 有非常强的关系。<mark>

栅氧化层越薄，Vgs 越大

</mark>

，栅氧化层两端的电场越强，电子越容易被拉过氧化层栅极，漏电越大。
- scaling:在较老的工艺中，栅极漏电可以忽略不计。**在某些 65 nm 及以下工艺中，栅极漏电可能已经接近亚阈值漏电的大小。**所以先进工艺面临一个矛盾：氧化层薄，有利于提高晶体管控制能力和速度；但氧化层太薄，会导致严重的栅极漏电。
- p/n的差异：<mark>

**pMOS 的栅极漏电通常比 nMOS 小一个数量级（10倍）。**

</mark>

nMOS 中主要载流子是电子，pMOS 中主要载流子是空穴。电子的有效质量通常比空穴更小，因此电子更容易发生隧穿。nMOS 的栅极漏电往往比 pMOS 更严重。
- 工艺上的改善：在工艺层面，可以通过使用**大于** <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mn>

10.5

</mn>

<mtext>



</mtext>

<mover accent="true">
<mtext>

A

</mtext>

<mo>

˚

</mo>
</mover>
</mrow>

<annotation encoding="application/x-tex">

10.5 \, \text{Å}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9468em;">



</span>

<span className="mord">

10.5

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord,text">
<span className="mord,accent">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.9468em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">

A

</span>
</span>

<span style="top:-3.2523em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.375em;">
<span className="mord">

˚

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

 **的**栅氧化层厚度来控制漏电。传统 MOS 管常用二氧化硅作为栅氧化层。但是二氧化硅的介电常数不够高，**High-k 材料**可以解决这一点：在保持较大栅电容的同时，让物理厚度可以做得更厚。**有些工艺会提供多种不同厚度的栅氧化层。**同一芯片中不同供电电压下的晶体管制作不同的厚度，例如thicker oxide for 3.3 V I/O transistors（核心逻辑电路通常工作在较低电压下，例如 1.0 V 或 1.2 V）
- 电路上的改善：在电路设计层面，可以通过限制电源电压 <span className="katex">
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

 来控制栅极漏电。不过这里也有权衡。降低 <span className="katex">
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

 虽然可以减少动态功耗和部分漏电，但也会降低电路速度。为了保持速度，可能又要降低阈值电压<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

V

</mi>

<mi>

T

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

V_T

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
<span className="mord,mathnormal,mtight" style="margin-right:0.1389em;">

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
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

，这会增加亚阈值漏电。

##### Subthreshold Leakage Component亚阈值漏电流

- 亚阈值：即使 <span className="katex">
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

G

</mi>

<mi>

S

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

V_{GS}

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
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

GS

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

 小于阈值电压 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

V

</mi>

<mi>

T

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

V_T

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
<span className="mord,mathnormal,mtight" style="margin-right:0.1389em;">

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
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

，虽然没有形成强反型沟道，但沟道区域并不是完全没有载流子。仍然会有少量载流子由于浓度差发生扩散，从源极流向漏极。这个电流就叫<span className="katex">
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

u

</mi>

<mi>

b

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

I_{sub}

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
<span className="mord,mathnormal,mtight">

s

</span>

<span className="mord,mathnormal,mtight">

u

</span>

<span className="mord,mathnormal,mtight">

b

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
- 阈值电压越低，漏电越严重：
![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter9-Power-26.webp)

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

s

</mi>

<mi>

u

</mi>

<mi>

b

</mi>
</mrow>
</msub>

<mo>

∝

</mo>

<msup>
<mi>

e

</mi>

<mfrac>
<mrow>
<msub>
<mi>

V

</mi>

<mrow>
<mi>

G

</mi>

<mi>

S

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

T

</mi>
</msub>
</mrow>

<mrow>
<mi>

n

</mi>

<msubsup>
<mi>

V

</mi>

<mi>

T

</mi>

<mo mathvariant="normal" lspace="0em" rspace="0em">

′

</mo>
</msubsup>
</mrow>
</mfrac>
</msup>
</mrow>

<annotation encoding="application/x-tex">

I_{sub} \propto e^{\frac{V_{GS}-V_T}{nV_T'}}

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
<span className="mord,mathnormal,mtight">

s

</span>

<span className="mord,mathnormal,mtight">

u

</span>

<span className="mord,mathnormal,mtight">

b

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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
<span className="strut" style="height:1.439em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

e

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:1.439em;">
<span style="top:-3.7016em;margin-right:0.05em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">
<span className="mopen,nulldelimiter,sizing,reset-size3,size6">



</span>

<span className="mfrac">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:1.0534em;">
<span style="top:-2.5334em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

n

</span>

<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.2222em;">

V

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.9004em;">
<span style="top:-2.1488em;margin-left:-0.2222em;margin-right:0.1em;">
<span className="pstrut" style="height:2.6833em;">



</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.1389em;">

T

</span>
</span>

<span style="top:-3.0281em;margin-right:0.1em;">
<span className="pstrut" style="height:2.6833em;">



</span>

<span className="mord,mtight">
<span className="mord,mtight">

′

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.5345em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

<span style="top:-3.2255em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="frac-line,mtight" style="border-bottom-width:0.049em;">



</span>
</span>

<span style="top:-3.5653em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
<span className="mord,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.2222em;">

V

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3448em;">
<span style="top:-2.3448em;margin-left:-0.2222em;margin-right:0.1em;">
<span className="pstrut" style="height:2.6833em;">



</span>

<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

GS

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.3385em;">
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
<span style="top:-2.3448em;margin-left:-0.2222em;margin-right:0.1em;">
<span className="pstrut" style="height:2.6833em;">



</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.1389em;">

T

</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.3385em;">
<span>



</span>
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
<span className="vlist" style="height:0.8484em;">
<span>



</span>
</span>
</span>
</span>
</span>

<span className="mclose,nulldelimiter,sizing,reset-size3,size6">



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

- 怎么越来越像微电子器件了，公式里面DIBL都出来了，应该不会考这种公式，大概了解一下量级

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter9-Power-27.webp)

##### Junction Leakage

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter9-Power-28.webp)

- 反向偏置 p-n 结产生的隧穿漏电，发生在扩散区与衬底或阱之间
- **带间隧穿（BTBT）可能会很显著，**尤其是在高 <span className="katex">
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

 晶体管中，因为其他漏电较小
当 <span className="katex">
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

d

</mi>

<mi>

b

</mi>
</mrow>
</msub>

<mo>

=

</mo>

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

V_{db}=V_{DD}

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

d

</span>

<span className="mord,mathnormal,mtight">

b

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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

 时最严重。

##### 漏电流的影响因素

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter9-Power-29.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter9-Power-30.webp)

#### 重点总结：

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter9-Power-31.webp)

## 三、Power optimization

### 减少动态功耗——设计阶段

表格从两个角度分类：

第一，按功耗类型分为：

- **Active Energy**：电路工作时产生的动态能量，主要来自节点翻转、电容充放电。
- **Leakage**：电路即使不工作也会存在的漏电功耗。

第二，按优化发生的时间和场景分为：

- **Design Time**：设计阶段就决定好的优化方法。
- **Non-active Modules**：模块暂时不用时采用的节能方法。
- **Run Time**：运行过程中动态调整的方法。

从逻辑电路设计、缩小Vdd、改变尺寸、使用多种Vdd下手

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter9-Power-32.webp)

**减小开关功耗:**

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 72.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter9-Power-33.webp" />
      </p>
    </td>
    
    
      <td style="width: 27.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter9-Power-34.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

##### Activity Factor Estimation活动因子估计

开关功耗主要发生在输出从低电平上升到高电平的过程，我们关注会发生多少个这样的翻转过程

- 在完全随机的情况下，节点为0和1的概率各为50%，**节点发生 0 → 1 翻转的概率，等于“上一时刻为 0 的概率”乘以“下一时刻为 1 的概率”。**也就是：

<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

P

</mi>

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
</msub>

<mo>

=

</mo>

<mi>

P

</mi>

<mi>

r

</mi>

<mi>

o

</mi>

<mi>

b

</mi>

<mo stretchy="false">

(

</mo>

<mi>

i

</mi>

<mo>

=

</mo>

<mn>

0

</mn>

<mo stretchy="false">

)

</mo>

<mo>

×

</mo>

<mi>

P

</mi>

<mi>

r

</mi>

<mi>

o

</mi>

<mi>

b

</mi>

<mo stretchy="false">

(

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

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

P_{0\rightarrow1}=Prob(i=0)\times Prob(i=1)

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

P

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.1389em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">

0

</span>

<span className="mrel,mtight">

→

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

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal">

o

</span>

<span className="mord,mathnormal">

b

</span>

<span className="mopen">

(

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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord">

0

</span>

<span className="mclose">

)

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

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal">

o

</span>

<span className="mord,mathnormal">

b

</span>

<span className="mopen">

(

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

，为0.25。

- 实际数据通常不是完全随机的。比如 64 位数据如果表示银行账户余额，高位 bit 通常是 0。因为普通账户余额不会大到需要用满 64 位，所以高位长期保持 0，很少翻转。这说明真实电路中的活动因子往往小于完全随机情况下的 0.25。
- 数据经过 AND 门和 OR 门之后，活动因子通常会降低。因为 AND 门、OR 门的输出不一定像输入那样随机。例如 AND 门只有所有输入都为 1 时输出才为 1，所以输出更容易偏向 0；OR 门只要有一个输入为 1 输出就为 1，所以输出更容易偏向 1。输出一旦偏向某个固定值，翻转概率就会下降。

##### 🌟复杂逻辑门的活动因子估算‼️会计算

同样的，输出为0的概率乘上输出为1的概率。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter9-Power-35.webp)

##### 信号相关性对活动因子的影响

当信号间有相关性时，如A=B，最后的结果也会完全不同。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter9-Power-36.webp)

##### 改变逻辑电路结构来减小开关功耗：

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter9-Power-37.webp)

##### 改变输入信号顺序来降低翻转频率：

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter9-Power-38.webp)

尽量把容易频繁翻转的信号置于逻辑结构中的后几环

##### 降低Vdd来减小开关功耗

需要在开关速度和功耗的矛盾中选取一个折中的方案。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter9-Power-39.webp)

- **器件尺寸调整与降低电源电压相结合，是减少逻辑网络能量消耗的一种非常有效的方法。**
- **器件尺寸调整会影响动态能量消耗。**
  - 对于整体有效扇出较大的网络，收益最大。<span className="katex">
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
  
  <mfrac>
  <msub>
  <mi>
  
  C
  
  </mi>
  
  <mi>
  
  L
  
  </mi>
  </msub>
  
  <msub>
  <mi>
  
  C
  
  </mi>
  
  <mrow>
  <mi>
  
  g
  
  </mi>
  
  <mo separator="true">
  
  ,
  
  </mo>
  
  <mn>
  
  1
  
  </mn>
  </mrow>
  </msub>
  </mfrac>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  F = \frac{C_L}{C_{g,1}}
  
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
  <span className="strut" style="height:1.431em;vertical-align:-0.5423em;">
  
  
  
  </span>
  
  <span className="mord">
  <span className="mopen,nulldelimiter">
  
  
  
  </span>
  
  <span className="mfrac">
  <span className="vlist-t,vlist-t2">
  <span className="vlist-r">
  <span className="vlist" style="height:0.8886em;">
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
  <span className="vlist" style="height:0.3173em;">
  <span style="top:-2.357em;margin-left:-0.0715em;margin-right:0.0714em;">
  <span className="pstrut" style="height:2.5em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size3,size1,mtight">
  <span className="mord,mtight">
  <span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">
  
  g
  
  </span>
  
  <span className="mpunct,mtight">
  
  ,
  
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
  
  <span style="top:-3.4103em;">
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
  <span style="top:-2.3567em;margin-left:-0.0715em;margin-right:0.0714em;">
  <span className="pstrut" style="height:2.5em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size3,size1,mtight">
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

其中，<span className="katex">
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

表示整体有效扇出，<span className="katex">
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

 是负载电容，<span className="katex">
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

g

</mi>

<mo separator="true">

,

</mo>

<mn>

1

</mn>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

C_{g,1}

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
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

g

</span>

<span className="mpunct,mtight">

,

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

是第一级门的输入栅电容。

##### 🛠️最小能量的晶体管尺寸设计Transistor Sizing for Minimum Energy

这一块lzm还不太会，先跳过，奉上ppt

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter9-Power-40.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter9-Power-41.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter9-Power-42.webp)

##### Multiple VDD

- **降低**<span className="katex">
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

**会以平方关系降低动态能量消耗。**
  - 但会增加门延迟，也就是降低性能。
- **在设计阶段确定关键路径，并为这些关键路径上的晶体管使用较高的**<span className="katex">
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

**，以保证速度。对于其他门，则使用较低的** <span className="katex">
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

**，尤其是那些驱动大电容的门，因为这样可以获得最大的能量收益。**
- **需要多少个** <span className="katex">
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

**？——两个电源电压正在变得越来越常见**
  - 许多芯片已经有两个电源：一个用于核心电路，一个用于 I/O 接口。
- **当结合使用多个电源电压时，如果低电源电压模块要驱动高电源电压的门，就需要电平转换器。**
也就是从低电压到高电压的转换，称为 **升压 step-up**。

  - 如果一个由 <span className="katex">
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
  
  <mi>
  
  L
  
  </mi>
  </mrow>
  </msub>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  V_{DDL}
  
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
  <span className="vlist" style="height:0.15em;">
  <span>
  
  
  
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  
  供电的门去驱动一个由<span className="katex">
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
  
  <mi>
  
  H
  
  </mi>
  </mrow>
  </msub>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  V_{DDH}
  
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
  <span className="vlist" style="height:0.15em;">
  <span>
  
  
  
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  
  供电的门，那么 PMOS 可能永远无法完全关断。
  - 对于从高电压到低电压的变化，也就是 **降压 step-down**，通常不需要电平转换器。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter9-Power-43.webp)

### 减少动态功耗——运行阶段

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter9-Power-44.webp)

- **DFS：Dynamic Frequency Scaling，动态频率调节**
- **DVS：Dynamic Voltage Scaling，动态电压调节**

它们属于 **运行时优化方法**。当系统性能需求不高时，可以降低频率或降低电压，从而减少动态能量；当性能需求提高时，再提高频率或电压。

##### 电压 / 频率动态调节

- **让每个模块在满足性能要求的前提下，以尽可能低的电压和频率运行**
  - 例如，一个片上系统（System-on-Chip, SoC）：
  
    - 对存储器使用较高的电源电压，以保证存储单元稳定性；
    - 对处理器使用中等电压；
    - 对以较低速度运行的 I/O 外设使用较低电压。
- **电压域**
  - 为不同模块提供独立的电源；
  - 当信号从低 <span className="katex">
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
  
  电压域跨越到高 <span className="katex">
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
  
  电压域时，需要使用电平转换器。
  （不知道这里为什么要放这一页PPT，感觉这个属于multi Vdd的范畴）
- 当系统任务少、性能需求低时，就降低电压和频率，让电路慢一点工作，从而降低功耗；当系统任务多、需要快速处理时，就提高电压和频率，让电路进入高速工作状态。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter9-Power-45.webp)

##### 作用机制

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter9-Power-46.webp)

- **DVS Controller**
动态电压调节控制器，负责判断系统现在应该快还是慢。
- **Switching Voltage Regulator**
开关电压调节器，根据控制器的指令输出合适的<span className="katex">
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

。
- **Core Logic**
核心逻辑电路，也就是实际工作的计算模块。

Core Logic 会向 DVS Controller 反馈：

- **Workload**：当前工作负载；
- **Temperature**：当前温度。

DVS Controller 根据这些信息输出：

- **Voltage Control**：控制电压调节器改变 <span className="katex">
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

；
- **Freq Control**：控制核心逻辑的工作频率。

所以这个系统可以根据运行状态自动调节功耗。

<alert type="tip">

DVS总结：
调节电压可以使得功耗可以按平方关系降低

只需要工作得“刚好足够快”，满足截止时间即可。

DVS算法可以通过软件或者硬件来实现

</alert>

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter9-Power-47.webp)

### 减少动态功耗——Non-active Modules

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter9-Power-48.webp)

##### 时钟门控

**降低活动因子的最佳方法，是关闭未使用模块中寄存器的时钟。**

- 节省时钟活动功耗
- <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

α

</mi>

<mo>

=

</mo>

<mn>

1

</mn>
</mrow>

<annotation encoding="application/x-tex">

\alpha = 1

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
- 这里表示时钟信号每个周期都会翻转，活动因子很高。
- 消除该模块中的所有开关活动。
- 需要判断该模块是否会被使用。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter9-Power-49.webp)

### 减少静态功耗——Multiple Vt&Stack Effect

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter9-Power-50.webp)

##### Leakage Control

- **漏电和延迟之间存在权衡**
  - 目标是在睡眠模式下降低漏电，在工作模式下降低延迟。
- **为了降低漏电：**
  - 增大 <span className="katex">
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
  
  ：采用多阈值电压 <span className="katex">
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
  
  
    - 只在关键电路中使用低 <span className="katex">
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
  - 增大 <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <msub>
  <mi>
  
  V
  
  </mi>
  
  <mi>
  
  s
  
  </mi>
  </msub>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  V_s
  
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
  
  ：利用堆叠效应
  
    - 在睡眠模式下进行输入向量控制
  - 降低<span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <msub>
  <mi>
  
  V
  
  </mi>
  
  <mi>
  
  b
  
  </mi>
  </msub>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  V_b
  
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
  <span className="mord,mathnormal,mtight">
  
  b
  
  </span>
  </span>
  </span>
  </span>
  
  <span className="vlist-s">
  
  ​
  
  </span>
  </span>
  
  <span className="vlist-r">
  <span className="vlist" style="height:0.15em;">
  <span>
  
  
  
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  
  
    - 采用体偏置技术

##### Multiple Vt

- **与 multiple**<span className="katex">
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

**类似，核心思想是利用可用的时序余量。**
  - 对关键路径上的门分配低 <span className="katex">
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
  
  
  这些路径通常具有负 slack 或没有 slack。
  - 对非关键路径上的门分配高 <span className="katex">
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
  
  
  这些路径通常具有正 slack。
- **Multiple** <span className="katex">
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

**可以在不同粒度上实现：门级、半门级、晶体管级等。**
  - 由于标准单元库的存在，门级实现比较常见。
  - 粒度越细，漏电控制效果越好，但控制和设计工作量也越大。

##### 🌟🌟🌟‼️‼️例子（承接上面的计算题，感觉可以出成大题的两问）

重新回顾一个 **10 亿晶体管芯片** 的功耗估算

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter9-Power-51.webp)

- **估算静态功耗**
  - **亚阈值漏电**
    - 普通 <span className="katex">
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
    
    ：<span className="katex">
    <span className="katex-mathml">
    <math xmlns="http://www.w3.org/1998/Math/MathML">
    <semantics>
    <mrow>
    <mn>
    
    100
    
    </mn>
    
    <mtext>
    
    nA
    
    </mtext>
    
    <mi mathvariant="normal">
    
    /
    
    </mi>
    
    <mi>
    
    μ
    
    </mi>
    
    <mi>
    
    m
    
    </mi>
    </mrow>
    
    <annotation encoding="application/x-tex">
    
    100 \text{ nA}/\mu m
    
    </annotation>
    </semantics>
    </math>
    </span>
    
    <span className="katex-html" ariaHidden="true">
    <span className="base">
    <span className="strut" style="height:1em;vertical-align:-0.25em;">
    
    
    
    </span>
    
    <span className="mord">
    
    100
    
    </span>
    
    <span className="mord,text">
    <span className="mord">
    
    nA
    
    </span>
    </span>
    
    <span className="mord">
    
    /
    
    </span>
    
    <span className="mord,mathnormal">
    
    μ
    
    </span>
    
    <span className="mord,mathnormal">
    
    m
    
    </span>
    </span>
    </span>
    </span>
    - 高 <span className="katex">
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
    
    ：<span className="katex">
    <span className="katex-mathml">
    <math xmlns="http://www.w3.org/1998/Math/MathML">
    <semantics>
    <mrow>
    <mn>
    
    10
    
    </mn>
    
    <mtext>
    
    nA
    
    </mtext>
    
    <mi mathvariant="normal">
    
    /
    
    </mi>
    
    <mi>
    
    μ
    
    </mi>
    
    <mi>
    
    m
    
    </mi>
    </mrow>
    
    <annotation encoding="application/x-tex">
    
    10 \text{ nA}/\mu m
    
    </annotation>
    </semantics>
    </math>
    </span>
    
    <span className="katex-html" ariaHidden="true">
    <span className="base">
    <span className="strut" style="height:1em;vertical-align:-0.25em;">
    
    
    
    </span>
    
    <span className="mord">
    
    10
    
    </span>
    
    <span className="mord,text">
    <span className="mord">
    
    nA
    
    </span>
    </span>
    
    <span className="mord">
    
    /
    
    </span>
    
    <span className="mord,mathnormal">
    
    μ
    
    </span>
    
    <span className="mord,mathnormal">
    
    m
    
    </span>
    </span>
    </span>
    </span>
    - 高 <span className="katex">
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
    
     用于所有存储器，以及 95% 的逻辑门
  - **栅极漏电**：<span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mn>
  
  5
  
  </mn>
  
  <mtext>
  
  nA
  
  </mtext>
  
  <mi mathvariant="normal">
  
  /
  
  </mi>
  
  <mi>
  
  μ
  
  </mi>
  
  <mi>
  
  m
  
  </mi>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  5 \text{ nA}/\mu m
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:1em;vertical-align:-0.25em;">
  
  
  
  </span>
  
  <span className="mord">
  
  5
  
  </span>
  
  <span className="mord,text">
  <span className="mord">
  
  nA
  
  </span>
  </span>
  
  <span className="mord">
  
  /
  
  </span>
  
  <span className="mord,mathnormal">
  
  μ
  
  </span>
  
  <span className="mord,mathnormal">
  
  m
  
  </span>
  </span>
  </span>
  </span>
  - **结漏电可以忽略不计**![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter9-Power-52.webp)

##### Stack Effect堆叠效应

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 39.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter9-Power-53.webp" />
      </p>
    </td>
    
    
      <td style="width: 60.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter9-Power-54.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

- **串联关断的晶体管具有更小的漏电**
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
  
  x
  
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
  
  V_x > 0
  
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
  
  ，因此 N2 具有负的 <span className="katex">
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
  
  g
  
  </mi>
  
  <mi>
  
  s
  
  </mi>
  </mrow>
  </msub>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  V_{gs}
  
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
  <span className="mord,mtight">
  <span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">
  
  g
  
  </span>
  
  <span className="mord,mathnormal,mtight">
  
  s
  
  </span>
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
    
    V
    
    </mi>
    
    <mi>
    
    x
    
    </mi>
    </msub>
    </mrow>
    
    <annotation encoding="application/x-tex">
    
    V_x
    
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
    
     会减小 N2 的漏源电压，从而提高它的阈值电压 <span className="katex">
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
    
    ，并降低它的漏电。
    - DIBL 效应。

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

s

</mi>

<mi>

u

</mi>

<mi>

b

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

o

</mi>

<mi>

f

</mi>

<mi>

f

</mi>
</mrow>
</msub>

<msup>
<mn>

10

</mn>

<mrow>
<mfrac>
<mrow>
<mo>

−

</mo>

<mi>

η

</mi>

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

<mi>

S

</mi>
</mfrac>

<mrow>
<mo fence="true">

(

</mo>

<mfrac>
<mrow>
<mn>

1

</mn>

<mo>

+

</mo>

<mi>

η

</mi>

<mo>

+

</mo>

<msub>
<mi>

k

</mi>

<mi>

γ

</mi>
</msub>
</mrow>

<mrow>
<mn>

1

</mn>

<mo>

+

</mo>

<mn>

2

</mn>

<mi>

η

</mi>

<mo>

+

</mo>

<msub>
<mi>

k

</mi>

<mi>

γ

</mi>
</msub>
</mrow>
</mfrac>

<mo fence="true">

)

</mo>
</mrow>
</mrow>
</msup>

<mo>

≈

</mo>

<msub>
<mi>

I

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
</mrow>
</msub>

<msup>
<mn>

10

</mn>

<mfrac>
<mrow>
<mo>

−

</mo>

<mi>

η

</mi>

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

<mi>

S

</mi>
</mfrac>
</msup>
</mrow>

<annotation encoding="application/x-tex">

I_{sub}=I_{off}10^{\frac{-\eta V_{DD}}{S}\left(\frac{1+\eta+k_\gamma}{1+2\eta+k_\gamma}\right)} \approx I_{off}10^{\frac{-\eta V_{DD}}{S}}

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
<span className="mord,mathnormal,mtight">

s

</span>

<span className="mord,mathnormal,mtight">

u

</span>

<span className="mord,mathnormal,mtight">

b

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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
<span className="strut" style="height:1.6294em;vertical-align:-0.2861em;">



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
<span className="mord,mathnormal,mtight">

o

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
<span className="vlist" style="height:0.2861em;">
<span>



</span>
</span>
</span>
</span>
</span>
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
<span className="vlist" style="height:1.3433em;">
<span style="top:-3.5458em;margin-right:0.05em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">
<span className="mopen,nulldelimiter,sizing,reset-size3,size6">



</span>

<span className="mfrac">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:1.0534em;">
<span style="top:-2.656em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

S

</span>
</span>
</span>
</span>

<span style="top:-3.2255em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="frac-line,mtight" style="border-bottom-width:0.049em;">



</span>
</span>

<span style="top:-3.5653em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
<span className="mord,mtight">
<span className="mord,mtight">

−

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

η

</span>

<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.2222em;">

V

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3448em;">
<span style="top:-2.3448em;margin-left:-0.2222em;margin-right:0.1em;">
<span className="pstrut" style="height:2.6833em;">



</span>

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

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.3385em;">
<span>



</span>
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
<span className="vlist" style="height:0.344em;">
<span>



</span>
</span>
</span>
</span>
</span>

<span className="mclose,nulldelimiter,sizing,reset-size3,size6">



</span>
</span>

<span className="minner,mtight">
<span className="mopen,sizing,reset-size3,size6,mtight,delimcenter" style="top:0.075em;">
<span className="delimsizing,size1,mtight">
<span className="mtight">

(

</span>
</span>
</span>

<span className="mord,mtight">
<span className="mopen,nulldelimiter,sizing,reset-size3,size6">



</span>

<span className="mfrac">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:1.1013em;">
<span style="top:-2.656em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
<span className="mord,mtight">
<span className="mord,mtight">

1

</span>

<span className="mbin,mtight">

+

</span>

<span className="mord,mtight">

2

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

η

</span>

<span className="mbin,mtight">

+

</span>

<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0315em;">

k

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.2306em;">
<span style="top:-2.3em;margin-left:-0.0315em;margin-right:0.1em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0556em;">

γ

</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.3944em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

<span style="top:-3.2255em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="frac-line,mtight" style="border-bottom-width:0.049em;">



</span>
</span>

<span style="top:-3.6052em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
<span className="mord,mtight">
<span className="mord,mtight">

1

</span>

<span className="mbin,mtight">

+

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

η

</span>

<span className="mbin,mtight">

+

</span>

<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0315em;">

k

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.2306em;">
<span style="top:-2.3em;margin-left:-0.0315em;margin-right:0.1em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0556em;">

γ

</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.3944em;">
<span>



</span>
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
<span className="vlist" style="height:0.6257em;">
<span>



</span>
</span>
</span>
</span>
</span>

<span className="mclose,nulldelimiter,sizing,reset-size3,size6">



</span>
</span>

<span className="mclose,sizing,reset-size3,size6,mtight,delimcenter" style="top:0.075em;">
<span className="delimsizing,size1,mtight">
<span className="mtight">

)

</span>
</span>
</span>
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
<span className="strut" style="height:1.4365em;vertical-align:-0.2861em;">



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
<span className="mord,mathnormal,mtight">

o

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
<span className="vlist" style="height:0.2861em;">
<span>



</span>
</span>
</span>
</span>
</span>
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
<span className="vlist" style="height:1.1504em;">
<span style="top:-3.413em;margin-right:0.05em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">
<span className="mopen,nulldelimiter,sizing,reset-size3,size6">



</span>

<span className="mfrac">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:1.0534em;">
<span style="top:-2.656em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

S

</span>
</span>
</span>
</span>

<span style="top:-3.2255em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="frac-line,mtight" style="border-bottom-width:0.049em;">



</span>
</span>

<span style="top:-3.5653em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
<span className="mord,mtight">
<span className="mord,mtight">

−

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

η

</span>

<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.2222em;">

V

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3448em;">
<span style="top:-2.3448em;margin-left:-0.2222em;margin-right:0.1em;">
<span className="pstrut" style="height:2.6833em;">



</span>

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

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.3385em;">
<span>



</span>
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
<span className="vlist" style="height:0.344em;">
<span>



</span>
</span>
</span>
</span>
</span>

<span className="mclose,nulldelimiter,sizing,reset-size3,size6">



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

- **通过 2-stack 的漏电大约降低 10 倍**
- **通过 3-stack 的漏电会进一步降低**

### 减少静态功耗——**当模块暂时不工作时**

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter9-Power-55.webp)

##### Power Gating

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter9-Power-56.webp)

当模块处于空闲状态时，关闭其电源以节省漏电功耗。

- 使用虚拟电源 <span className="katex">
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

<mi>

V

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

V_{DDV}

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

<span className="mord,mathnormal,mtight" style="margin-right:0.2222em;">

V

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
- 对输出进行门控，防止无效逻辑电平传递到下一级模块

这是降低漏电功耗最常用的方法之一。

- 类似于使用时钟门控来降低动态功耗。

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 50.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter9-Power-57.webp" />
      </p>
    </td>
    
    
      <td style="width: 49.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter9-Power-58.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

##### 这么做的好处和坏处

pros

- 实现简单，并且可以在 **IP 级别** 进行，而不需要接触底层细节。有利于技术迁移。
- **功率门控与 DVFS 结合使用，是移动设备中最常见的节能技术之一。**

but

- 睡眠晶体管上的电压降会在正常工作时降低性能。因此需要把该晶体管尺寸设计得<mark>

足够宽

</mark>

，以尽量减小影响。
- 切换较宽的睡眠晶体管会消耗动态功耗。只有当电路睡眠时间足够长时，这种做法才是值得的。

### 减少静态功耗——运行时的调整

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter9-Power-59.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter9-Power-60.webp)

**通过动态调节 PMOS 和 NMOS 的 body 电压，改变晶体管的阈值电压**<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

V

</mi>

<mi>

T

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

V_T

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
<span className="mord,mathnormal,mtight" style="margin-right:0.1389em;">

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
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

**，从而在性能和漏电之间做切换。**

在 **Active mode 工作模式** 下，电路需要速度，所以采用 **Forward Body Bias（正向体偏置，FBB）**：

- PMOS body 和 NMOS body 分别施加约 450 mV 的正向体偏置；
- 这样可以降低等效阈值电压 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

V

</mi>

<mi>

T

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

V_T

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
<span className="mord,mathnormal,mtight" style="margin-right:0.1389em;">

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
<span className="vlist" style="height:0.15em;">
<span>



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
- 晶体管更容易导通，速度更快，延迟更低；
- 但漏电会增加。

在 **Idle mode 空闲模式** 下，电路不需要高速工作，所以采用 **Reverse Body Bias（反向体偏置，RBB）**：

- PMOS body 和 NMOS body 分别施加约 500 mV 的反向体偏置；
- 这样可以提高等效阈值电压 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

V

</mi>

<mi>

T

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

V_T

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
<span className="mord,mathnormal,mtight" style="margin-right:0.1389em;">

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
<span className="vlist" style="height:0.15em;">
<span>



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
- 晶体管更难导通，漏电降低；
- 但速度会变慢，不过空闲状态下速度不重要。
**Triple well needed**意思是这种方法通常需要三阱工艺支持，因为要分别控制不同晶体管的 body 电压，不能让所有衬底简单地接到同一个固定电位。

**总结：一种有效但实现复杂的低功耗技术。**

### 要点总结：

各种功耗降低技术

- 这是 VLSI 设计中一个长期存在、持续重要的话题。
- 理解 **设计阶段** 和 **运行阶段** 的区别。
- 理解影响动态功耗的因素，以及对应的降低功耗技术。
- 理解影响漏电功耗的因素，以及对应的降低功耗技术。

总览：

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter9-Power-61.webp)

**低功耗设计策略贯穿 VLSI 设计的不同层次**。

#### 操作系统层面：Operation System level

对应策略是：

**Portioning, Power down**

可以理解为：

- 把系统任务划分到不同模块；
- 不用的模块可以关闭电源。

这一层更偏系统管理，例如某些功能暂时不用，就让它进入低功耗状态。

#### 软件层面：Software level

对应策略是：

**Regularity, locality, concurrency**

意思是：

- **Regularity**：规律性，让程序访问和计算更有规律；
- **Locality**：局部性，提高数据复用，减少不必要的数据搬运；
- **Concurrency**：并行性，让任务更有效地执行。

软件层面的低功耗重点是：**通过更合理的程序结构减少无效计算和数据访问。**

#### 体系结构层面：Architecture level

对应策略是：

**Pipelining, Redundancy, data encoding**

意思是：

- **Pipelining**：流水线，提高处理效率；
- **Redundancy**：冗余结构，用额外硬件换取更低电压或更高效率；
- **Data encoding**：数据编码，减少数据传输中的翻转次数。

这一层主要是在处理器、总线、存储结构等系统架构上优化功耗。

#### 电路 / 逻辑层面：Circuit/Logic level

对应策略是：

**Logic styles, transistor sizing and energy recovery**

意思是：

- **Logic styles**：选择合适的逻辑风格；
- **Transistor sizing**：调整晶体管尺寸；
- **Energy recovery**：能量恢复技术。

这一层就是我们前面讲过比较多的内容，比如降低动态功耗、优化延迟、调整晶体管尺寸等。

#### 工艺层面：Technology level

对应策略是：

**Threshold reduction, multi threshold devices**

意思是：

- **Threshold reduction**：降低阈值电压；
- **Multi threshold devices**：多阈值器件。

这一层和晶体管本身有关。比如关键路径使用低 <span className="katex">
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

S保证速度，非关键路径使用高 $$V_t$$降低漏电。

**有效的功耗管理可以通过在 VLSI 设计流程的不同层次使用不同策略来实现。因此，设计者需要采用智能化的方法来优化设计中的功耗。**
