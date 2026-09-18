# Chapter 7：时序逻辑 Sequential Logic

> 锁存器与触发器的结构、时序约束，以及动态寄存器和流水线设计。

## **第 1–9页：时序逻辑与基本时序约束**

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter7-SequentialLogic-01.webp)

### **主要是一些概念**

#### **时序逻辑与存储元件基础**

- **时序机器的组成：** 时序机器包含组合逻辑（Combinational logic）和存储元件（Memory elements）
- **存储元件的作用：** 它是时序机器中最重要的组件，用于在时钟的控制下存储数值
- **CMOS中的存储实现：** <mark>

主要分为利用电容和刷新机制实现的动态存储（Dynamic），以及利用反馈实现的静态存储（Static）

</mark>

#### **锁存器（Latch）与寄存器（Register/Flip-flop）的区别**

存储元件根据输出与输入的关系主要分为两类

- **锁存器（Latch）：** <mark>

属于

</mark>

<mark>

**电平敏感（level sensitive）**

</mark>

<mark>

器件

</mark>

 。当时钟处于有效电平时，它是“透明的”（即输入的变化会立刻反映到输出上）
- **寄存器/触发器（Register/Flip-flop）：** <mark>

属于

</mark>

<mark>

**边沿触发（edge triggered）**

</mark>

<mark>

器件

</mark>

 。它不是透明的，读取输入数据和改变输出状态是两个独立的事件

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter7-SequentialLogic-02.webp)

#### **时钟相关术语**

- **时钟边沿（Clock edge）：** 指时钟信号的上升沿或下降沿跳变
- **占空比（Duty cycle）：** 指时钟在一个周期内处于激活（Active）状态的时间比例

#### **时序定义与系统约束**

为了保证时序电路的正确运行，信号传输必须满足特定的时间窗口

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter7-SequentialLogic-03.webp)

- **建立时间（**<span className="katex">
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

s

</mi>

<mi>

u

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

t_{su}

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

s

</span>

<span className="mord,mathnormal,mtight">

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
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

**）与保持时间（**<span className="katex">
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

h

</mi>

<mi>

o

</mi>

<mi>

l

</mi>

<mi>

d

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

t_{hold}

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

h

</span>

<span className="mord,mathnormal,mtight">

o

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0197em;">

l

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

**）：** <mark>

在时钟有效边沿到来前后，输入数据（Data）必须保持稳定的时间窗口

</mark>
- **时钟到输出延迟（**<span className="katex">
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

<mo>

−

</mo>

<mi>

q

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

t_{c-q}

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
<span className="vlist" style="height:0.2583em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

c

</span>

<span className="mbin,mtight">

−

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

**）：** 从时钟跳变开始，<mark>

到输出端（Output）数据达到稳定状态所需的时间

</mark>
- **保持时间约束（防止数据穿透）：** 寄存器与组合逻辑的污染延迟（即最小延迟，contamination delay）之和，必须大于或等于保持时间，公式为：<span className="katex">
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

<mi>

e

</mi>

<mi>

g

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

l

</mi>

<mi>

o

</mi>

<mi>

g

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

≥

</mo>

<msub>
<mi>

t

</mi>

<mrow>
<mi>

h

</mi>

<mi>

o

</mi>

<mi>

l

</mi>

<mi>

d

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

t_{cdreg}+t_{cdlogic}\ge t_{hold}

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

<span className="mord,mathnormal,mtight">

d

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
<span className="strut" style="height:0.9221em;vertical-align:-0.2861em;">



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

<span className="mord,mathnormal,mtight" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal,mtight">

o

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

g

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

≥

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

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

h

</span>

<span className="mord,mathnormal,mtight">

o

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0197em;">

l

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

<alert type="tip">

寄存器D端在时钟上升沿之后，至少保持<span className="katex">
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

h

</mi>

<mi>

o

</mi>

<mi>

l

</mi>

<mi>

d

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

t_{hold}

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

h

</span>

<span className="mord,mathnormal,mtight">

o

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0197em;">

l

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

的时间，才能把稳稳把数据锁存进来，所以在<span className="katex">
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

h

</mi>

<mi>

o

</mi>

<mi>

l

</mi>

<mi>

d

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

t_{hold}

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

h

</span>

<span className="mord,mathnormal,mtight">

o

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0197em;">

l

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

的时间内D端数据不能发生变化，污染延迟的时间须要大于等于<span className="katex">
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

h

</mi>

<mi>

o

</mi>

<mi>

l

</mi>

<mi>

d

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

t_{hold}

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

h

</span>

<span className="mord,mathnormal,mtight">

o

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0197em;">

l

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
</alert>

- **建立时间约束（决定最大时钟频率）：** 系统的时钟周期 <span className="katex">
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

 必须足以容纳时钟到输出延迟、组合逻辑传播延迟（<span className="katex">
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

l

</mi>

<mi>

o

</mi>

<mi>

g

</mi>

<mi>

i

</mi>

<mi>

c

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

t_{plogic}

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
<span className="mord,mathnormal,mtight" style="margin-right:0.0197em;">

pl

</span>

<span className="mord,mathnormal,mtight">

o

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

g

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
</span>
</span>
</span>

）以及建立时间，公式为：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

T

</mi>

<mo>

≥

</mo>

<msub>
<mi>

t

</mi>

<mrow>
<mi>

c

</mi>

<mo>

−

</mo>

<mi>

q

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

l

</mi>

<mi>

o

</mi>

<mi>

g

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

+

</mo>

<msub>
<mi>

t

</mi>

<mrow>
<mi>

s

</mi>

<mi>

u

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

T\ge t_{c-q}+t_{plogic}+t_{su}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8193em;vertical-align:-0.136em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

T

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
<span className="strut" style="height:0.9012em;vertical-align:-0.2861em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

t

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.2583em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

c

</span>

<span className="mbin,mtight">

−

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
<span className="mord,mathnormal,mtight" style="margin-right:0.0197em;">

pl

</span>

<span className="mord,mathnormal,mtight">

o

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

g

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

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

s

</span>

<span className="mord,mathnormal,mtight">

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
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

> 1. <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msub>
> <mi>
> 
> t
> 
> </mi>
> 
> <mrow>
> <mi>
> 
> s
> 
> </mi>
> 
> <mi>
> 
> u
> 
> </mi>
> </mrow>
> </msub>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> t_{su}
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:0.7651em;vertical-align:-0.15em;">
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
> <span className="mord,mtight">
> <span className="mord,mathnormal,mtight">
> 
> s
> 
> </span>
> 
> <span className="mord,mathnormal,mtight">
> 
> u
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
> t_<span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msub>
> <mi>
> 
> t
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
> <mo>
> 
> −
> 
> </mo>
> 
> <mi>
> 
> q
> 
> </mi>
> </mrow>
> </msub>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> t_{c-q}
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
> <span className="vlist" style="height:0.2583em;">
> <span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
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
> <span className="mbin,mtight">
> 
> −
> 
> </span>
> 
> <span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">
> 
> q
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
> 是寄存器的“物理固有属性”，是由其内部晶体管、逻辑门和反馈环路组成物理电路导致的延时
> 2. 从时钟跳变开始，到输出端Q的响应（最慢<span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msub>
> <mi>
> 
> t
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
> <mo>
> 
> −
> 
> </mo>
> 
> <mi>
> 
> q
> 
> </mi>
> </mrow>
> </msub>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> t_{c-q}
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
> <span className="vlist" style="height:0.2583em;">
> <span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
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
> <span className="mbin,mtight">
> 
> −
> 
> </span>
> 
> <span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">
> 
> q
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
> ，最快<span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msub>
> <mi>
> 
> t
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
> d
> 
> </mi>
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
> g
> 
> </mi>
> </mrow>
> </msub>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> t_{cdreg}
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
> <span className="mord,mathnormal,mtight">
> 
> c
> 
> </span>
> 
> <span className="mord,mathnormal,mtight">
> 
> d
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
> <span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">
> 
> g
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
> ）
> 3. 组合逻辑传播延迟（最慢<span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msub>
> <mi>
> 
> t
> 
> </mi>
> 
> <mrow>
> <mi>
> 
> p
> 
> </mi>
> 
> <mi>
> 
> l
> 
> </mi>
> 
> <mi>
> 
> o
> 
> </mi>
> 
> <mi>
> 
> g
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
> c
> 
> </mi>
> </mrow>
> </msub>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> t_{plogic}
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
> <span className="mord,mathnormal,mtight" style="margin-right:0.0197em;">
> 
> pl
> 
> </span>
> 
> <span className="mord,mathnormal,mtight">
> 
> o
> 
> </span>
> 
> <span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">
> 
> g
> 
> </span>
> 
> <span className="mord,mathnormal,mtight">
> 
> i
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
> ，最快<span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msub>
> <mi>
> 
> t
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
> d
> 
> </mi>
> 
> <mi>
> 
> l
> 
> </mi>
> 
> <mi>
> 
> o
> 
> </mi>
> 
> <mi>
> 
> g
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
> c
> 
> </mi>
> </mrow>
> </msub>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> t_{cdlogic}
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
> <span className="mord,mathnormal,mtight">
> 
> c
> 
> </span>
> 
> <span className="mord,mathnormal,mtight">
> 
> d
> 
> </span>
> 
> <span className="mord,mathnormal,mtight" style="margin-right:0.0197em;">
> 
> l
> 
> </span>
> 
> <span className="mord,mathnormal,mtight">
> 
> o
> 
> </span>
> 
> <span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">
> 
> g
> 
> </span>
> 
> <span className="mord,mathnormal,mtight">
> 
> i
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
> ）

## 第 10–26 页：基本锁存器和寄存器、非理想时钟

> 避免存储元件混淆，规定如下（P217）
> 
> - 一个边沿触发的存储元件称为寄存器
> - 锁存器是一个电平敏感的器件
> - 由交叉耦合的门构成的任何双稳态元件称为触发器

### 锁存器基础与实现 | Lanch

#### **基本概念：锁存器的“电平敏感”特性**

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter7-SequentialLogic-04.webp)

- 锁存器是一种电平敏感的记忆元件
- 它的运行机制分为两相：<mark>

在时钟有效时处于

</mark>

<mark>

**透明模式（Transparent）**

</mark>

<mark>

，输入直接反映到输出；在时钟无效时处于

</mark>

<mark>

**保持模式（Hold）**

</mark>

<mark>

，无视输入端的变化，死死“锁”住当前数据

</mark>

 （分正负latch，<mark>

正是高电平通，负是低电平通

</mark>

）

#### **底层原理：双稳态与再生反馈**

- 记忆数据的物理本质是**正反馈网络**。通过将两个反相器交叉耦合，可以构建出一个拥有两个稳定状态（0或1）的“双稳态电路（Bistable Circuit）”

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter7-SequentialLogic-05.webp)

> AB为稳态点，点周围环路增益小于1;C为亚稳态点，点周围的环路增益大于1

- 要改写里面存储的数据，就必须施加一个外部脉冲，迫使电路翻转到另一个稳定状态。有两种方式

  - 切断反馈环
  - 用更强输入压过反馈环

#### **工程演进：从逻辑门到晶体管的实现**

- **逻辑门级（SR锁存器）：** 利用两个交叉耦合的或非门（NOR门）实现最基础的置位（Set）和复位（Reset）功能

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 33.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter7-SequentialLogic-06.webp" />
      </p>
    </td>
    
    
      <td style="width: 66.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter7-SequentialLogic-07.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

- **架构级（基于 MUX）：** 利用多路选择器（Multiplexer）作为开关，通过时钟信号在“接收新输入”和“反馈保持原值”之间来回切换
- **晶体管级（TG与PT实现）：** 在实际的 CMOS 制造中，开关通常由**传输门（Transmission Gate, TG）**或**传输管（Pass Transistor, PT）**实现。传输门信号完整性好，而单传输管虽然会带来<mark>

阈值压降损失

</mark>

（第一个反相器输入的高电平下降一个阈值电压），但能有效降低系统的<mark>

时钟负载

</mark>

 （左边TG，右边PT）

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 46.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter7-SequentialLogic-08.webp" />
      </p>
    </td>
    
    
      <td style="width: 53.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter7-SequentialLogic-09.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

### 主从触发器及其时序 | master-slave FF

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 47.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter7-SequentialLogic-10.webp" />
      </p>
    </td>
    
    
      <td style="width: 52.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter7-SequentialLogic-11.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

> 主从结构的主是负锁存器，从是正锁存器

#### 时序特性

<mark>

记得看一下书P221

</mark>



![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter7-SequentialLogic-12.webp)

> 可以这样理解
> 
> - <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msub>
> <mi>
> 
> t
> 
> </mi>
> 
> <mrow>
> <mi>
> 
> s
> 
> </mi>
> 
> <mi>
> 
> u
> 
> </mi>
> </mrow>
> </msub>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> t_{su}
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:0.7651em;vertical-align:-0.15em;">
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
> <span className="mord,mtight">
> <span className="mord,mathnormal,mtight">
> 
> s
> 
> </span>
> 
> <span className="mord,mathnormal,mtight">
> 
> u
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
> : 时钟关门（上升沿）前，数据 <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <mi>
> 
> D
> 
> </mi>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> D
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
> <span className="mord,mathnormal" style="margin-right:0.0278em;">
> 
> D
> 
> </span>
> </span>
> </span>
> </span>
> 
>  必须提前多久到达，才能在**主锁存器（Master）**内部形成稳定的死循环（反馈环路）？
> - <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msub>
> <mi>
> 
> t
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
> <mo>
> 
> −
> 
> </mo>
> 
> <mi>
> 
> q
> 
> </mi>
> </mrow>
> </msub>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> t_{c-q}
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
> <span className="vlist" style="height:0.2583em;">
> <span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
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
> <span className="mbin,mtight">
> 
> −
> 
> </span>
> 
> <span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">
> 
> q
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
> : 时钟上升沿到来时，主锁存器（Master）把数据锁死，**从锁存器（Slave）**的大门打开。数据从中间节点 <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msub>
> <mi>
> 
> Q
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
> Q_M
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:0.8778em;vertical-align:-0.1944em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> <span className="mord,mathnormal">
> 
> Q
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
>  跑到最终输出端 <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <mi>
> 
> Q
> 
> </mi>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> Q
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:0.8778em;vertical-align:-0.1944em;">
> 
> 
> 
> </span>
> 
> <span className="mord,mathnormal">
> 
> Q
> 
> </span>
> </span>
> </span>
> </span>
> 
>  需要多久？
> - <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msub>
> <mi>
> 
> t
> 
> </mi>
> 
> <mrow>
> <mi>
> 
> h
> 
> </mi>
> 
> <mi>
> 
> o
> 
> </mi>
> 
> <mi>
> 
> l
> 
> </mi>
> 
> <mi>
> 
> d
> 
> </mi>
> </mrow>
> </msub>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> t_{hold}
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:0.7651em;vertical-align:-0.15em;">
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
> <span className="mord,mtight">
> <span className="mord,mathnormal,mtight">
> 
> h
> 
> </span>
> 
> <span className="mord,mathnormal,mtight">
> 
> o
> 
> </span>
> 
> <span className="mord,mathnormal,mtight" style="margin-right:0.0197em;">
> 
> l
> 
> </span>
> 
> <span className="mord,mathnormal,mtight">
> 
> d
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
> : 时钟上升沿到来之后，输入端数据 <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <mi>
> 
> D
> 
> </mi>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> D
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
> <span className="mord,mathnormal" style="margin-right:0.0278em;">
> 
> D
> 
> </span>
> </span>
> </span>
> </span>
> 
>  还需要保持多久不能变？

#### 有比逻辑主从结构

> 为了减小时钟负载

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter7-SequentialLogic-13.webp)

满足

- T1>I2；T2>I4  才能输入新的数据
- I1>I4  阻止反向传导

### 非理想时钟

**真实的时钟不完美，可能会有overlap，可能会有0-0重叠或者1-1重叠**

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter7-SequentialLogic-14.webp)

**课本上给了仅用NMOS管的**<mark>

**负主从寄存器**

</mark>

**的例子（如下）**

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter7-SequentialLogic-15.webp)

- 当出现0-0重叠时

  - MOS管全部断开，数据存在输出的电容里，理论时间短不易丢失
- 当出现1-1重叠时

  - MOS管全部导通，数据理论上可以直接从输入D传至输出Q。在本例中，会出现上升沿（1-1重叠）时输出端的数据可能会改变，这是这个负主从寄存器不希望看到的
  - MOS管全部闭合，节点A会同时被节点B,D驱动，造成不确定的状态

> ![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter7-SequentialLogic-16.webp)
> 
> 这边有个小细节。一般来说，<span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <mover accent="true">
> <mtext>
> 
> CLK
> 
> </mtext>
> 
> <mo stretchy="true">
> 
> ‾
> 
> </mo>
> </mover>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> \overline{\text{CLK}}
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:0.8833em;">
> 
> 
> 
> </span>
> 
> <span className="mord,overline">
> <span className="vlist-t">
> <span className="vlist-r">
> <span className="vlist" style="height:0.8833em;">
> <span style="top:-3em;">
> <span className="pstrut" style="height:3em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> <span className="mord,text">
> <span className="mord">
> 
> CLK
> 
> </span>
> </span>
> </span>
> </span>
> 
> <span style="top:-3.8033em;">
> <span className="pstrut" style="height:3em;">
> 
> 
> 
> </span>
> 
> <span className="overline-line" style="border-bottom-width:0.04em;">
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
> 是CLK加一个反相器得到的，所以课本上所有的<span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <mover accent="true">
> <mtext>
> 
> CLK
> 
> </mtext>
> 
> <mo stretchy="true">
> 
> ‾
> 
> </mo>
> </mover>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> \overline{\text{CLK}}
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:0.8833em;">
> 
> 
> 
> </span>
> 
> <span className="mord,overline">
> <span className="vlist-t">
> <span className="vlist-r">
> <span className="vlist" style="height:0.8833em;">
> <span style="top:-3em;">
> <span className="pstrut" style="height:3em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> <span className="mord,text">
> <span className="mord">
> 
> CLK
> 
> </span>
> </span>
> </span>
> </span>
> 
> <span style="top:-3.8033em;">
> <span className="pstrut" style="height:3em;">
> 
> 
> 
> </span>
> 
> <span className="overline-line" style="border-bottom-width:0.04em;">
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
> 都是比CLK延迟一点点的。也就可以得到   1-1重叠->上升沿  0-0重叠->下降沿

**为了避免这些问题，运用两相不重叠的时钟**

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 45.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter7-SequentialLogic-17.webp" />
      </p>
    </td>
    
    
      <td style="width: 54.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter7-SequentialLogic-18.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

- 成功避免了1-1重叠的可能，因为即使<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mover accent="true">
<mtext>

CLK

</mtext>

<mo stretchy="true">

‾

</mo>
</mover>
</mrow>

<annotation encoding="application/x-tex">

\overline{\text{CLK}}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8833em;">



</span>

<span className="mord,overline">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8833em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord,text">
<span className="mord">

CLK

</span>
</span>
</span>
</span>

<span style="top:-3.8033em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="overline-line" style="border-bottom-width:0.04em;">



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

和CLK有一定的延迟，也在1-1非重叠的阈值内
- 伪静态  根据时钟的不同状态，寄存器采取动态或者静态的的存储方式

  - 静态：正常的0-1或者1-0时，利用反馈保持状态
  - 动态：0-0重叠时，利用电荷保存数据（要求保持时间不能太长，会漏电，所以频率要高、non_overlap不能太大）

## 第 27–35 页：动态寄存器、C²MOS 触发器、单相位时钟

> 动态和静态的最大区别是，<mark>
> 
> 静态用的是两个反相器交叉耦合锁住信号，动态用的是存储在电容上的电荷表示信号
> 
> </mark>
> 
> 。所以动态需要不断的刷新数据，频率需要有要求（也是为什么叫动态）
> 
> 上面内容均为静态时序电路，下面开始介绍动态时序电路

### 动态传输门边沿触发寄存器 | Dynamic TG ET FF

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter7-SequentialLogic-19.webp)

##### 工作过程（基于主-从原理）

这种 ET（边沿触发）寄存器通过时钟的两个相位协同工作：

- **第一阶段：Master 透明，Slave 保持 (**<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

c

</mi>

<mi>

l

</mi>

<mi>

k

</mi>

<mo>

=

</mo>

<mn>

0

</mn>
</mrow>

<annotation encoding="application/x-tex">

clk=0

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,mathnormal">

c

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

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

0

</span>
</span>
</span>
</span>

**)**
  - <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <msub>
  <mi>
  
  T
  
  </mi>
  
  <mn>
  
  1
  
  </mn>
  </msub>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  T_1
  
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
  <span className="vlist" style="height:0.3011em;">
  <span style="top:-2.55em;margin-left:-0.1389em;margin-right:0.05em;">
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
  
   导通，输入信号 <span className="katex">
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
  
   进入主级并对电容 <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <msub>
  <mi>
  
  C
  
  </mi>
  
  <mn>
  
  1
  
  </mn>
  </msub>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  C_1
  
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
  <span className="vlist" style="height:0.3011em;">
  <span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
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
  
   充电/放电
  - 此时 <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <msub>
  <mi>
  
  T
  
  </mi>
  
  <mn>
  
  2
  
  </mn>
  </msub>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  T_2
  
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
  <span className="vlist" style="height:0.3011em;">
  <span style="top:-2.55em;margin-left:-0.1389em;margin-right:0.05em;">
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
  
   断开，从级（Slave）处于隔离状态。由于 <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <msub>
  <mi>
  
  C
  
  </mi>
  
  <mn>
  
  2
  
  </mn>
  </msub>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  C_2
  
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
  <span className="vlist" style="height:0.3011em;">
  <span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
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
  
   的电荷保持作用，输出 <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mi>
  
  Q
  
  </mi>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  Q
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:0.8778em;vertical-align:-0.1944em;">
  
  
  
  </span>
  
  <span className="mord,mathnormal">
  
  Q
  
  </span>
  </span>
  </span>
  </span>
  
   维持前一个状态
- **第二阶段：Master 保持，Slave 透明 (**<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

c

</mi>

<mi>

l

</mi>

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

clk=1

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,mathnormal">

c

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

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

**)**
  - 在时钟上升沿，<span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <msub>
  <mi>
  
  T
  
  </mi>
  
  <mn>
  
  1
  
  </mn>
  </msub>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  T_1
  
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
  <span className="vlist" style="height:0.3011em;">
  <span style="top:-2.55em;margin-left:-0.1389em;margin-right:0.05em;">
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
  
   关闭，主级采样瞬间的 <span className="katex">
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
  
   值被锁定在 <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <msub>
  <mi>
  
  C
  
  </mi>
  
  <mn>
  
  1
  
  </mn>
  </msub>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  C_1
  
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
  <span className="vlist" style="height:0.3011em;">
  <span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
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
  
   上
  - 同时 <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <msub>
  <mi>
  
  T
  
  </mi>
  
  <mn>
  
  2
  
  </mn>
  </msub>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  T_2
  
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
  <span className="vlist" style="height:0.3011em;">
  <span style="top:-2.55em;margin-left:-0.1389em;margin-right:0.05em;">
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
  
   导通，主级存储的值 <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <msub>
  <mi>
  
  Q
  
  </mi>
  
  <mi>
  
  M
  
  </mi>
  </msub>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  Q_M
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:0.8778em;vertical-align:-0.1944em;">
  
  
  
  </span>
  
  <span className="mord">
  <span className="mord,mathnormal">
  
  Q
  
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
  
   传递给从级并最终驱动到输出端  <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mi>
  
  Q
  
  </mi>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  Q
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:0.8778em;vertical-align:-0.1944em;">
  
  
  
  </span>
  
  <span className="mord,mathnormal">
  
  Q
  
  </span>
  </span>
  </span>
  </span>

---

##### 关键性能指标

该电路的定时特性如下（<mark>

书本P228

</mark>

，结合上面的小TIPS）：

- **建立时间 (**<span className="katex">
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

s

</mi>

<mi>

u

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

t_{su}

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

s

</span>

<span className="mord,mathnormal,mtight">

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
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

**)**：等于传输门的延迟 <span className="katex">
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

<mi mathvariant="normal">

_

</mi>

<mi>

t

</mi>

<mi>

x

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

t_{pd\_tx}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9821em;vertical-align:-0.367em;">



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

<span className="mord,mtight" style="margin-right:0.0278em;">

_

</span>

<span className="mord,mathnormal,mtight">

t

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
<span className="vlist" style="height:0.367em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
- **保持时间 (**<span className="katex">
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

h

</mi>

<mi>

o

</mi>

<mi>

l

</mi>

<mi>

d

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

t_{hold}

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

h

</span>

<span className="mord,mathnormal,mtight">

o

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0197em;">

l

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

**)**：为零
- **时钟到输出延迟 (**<span className="katex">
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

<mo>

−

</mo>

<mi>

q

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

t_{c-q}

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
<span className="vlist" style="height:0.2583em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

c

</span>

<span className="mbin,mtight">

−

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

**)**：约为两个反相器延迟加上一个传输门延迟 (<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mn>

2

</mn>

<mo>

⋅

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

<mi mathvariant="normal">

_

</mi>

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

<mi mathvariant="normal">

_

</mi>

<mi>

t

</mi>

<mi>

x

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

2 \cdot t_{pd\_inv} + t_{pd\_tx}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6444em;">



</span>

<span className="mord">

2

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
<span className="strut" style="height:0.9821em;vertical-align:-0.367em;">



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

<span className="mord,mtight" style="margin-right:0.0278em;">

_

</span>

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
<span className="vlist" style="height:0.367em;">
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
<span className="strut" style="height:0.9821em;vertical-align:-0.367em;">



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

<span className="mord,mtight" style="margin-right:0.0278em;">

_

</span>

<span className="mord,mathnormal,mtight">

t

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
<span className="vlist" style="height:0.367em;">
<span>



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

---

##### 潜在风险：时钟重叠（Race Conditions）

> 看一下书<mark>
> 
> P228
> 
> </mark>

由于动态电路依赖电荷存储，它对**非理想时钟（时钟重叠/抖动）**非常敏感

- **0-0 重叠**：如果 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

c

</mi>

<mi>

l

</mi>

<mi>

k

</mi>
</mrow>

<annotation encoding="application/x-tex">

clk

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,mathnormal">

c

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal" style="margin-right:0.0315em;">

k

</span>
</span>
</span>
</span>

 和 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mo stretchy="false">

!

</mo>

<mi>

c

</mi>

<mi>

l

</mi>

<mi>

k

</mi>
</mrow>

<annotation encoding="application/x-tex">

!clk

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mclose">

!

</span>

<span className="mord,mathnormal">

c

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal" style="margin-right:0.0315em;">

k

</span>
</span>
</span>
</span>

 同时为低，<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

T

</mi>

<mn>

1

</mn>
</msub>
</mrow>

<annotation encoding="application/x-tex">

T_1

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
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.1389em;margin-right:0.05em;">
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

 和 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

T

</mi>

<mn>

2

</mn>
</msub>
</mrow>

<annotation encoding="application/x-tex">

T_2

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
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.1389em;margin-right:0.05em;">
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

 可能同时导通，导致数据错误地穿透两级
- **1-1 重叠**：可能导致输出状态不确定或电荷流失

### C²MOS 触发器 | Clock CMOS FF

> 对时钟偏差不敏感的动态电路（但也不是完全不敏感。1-1重叠有问题；上升下降时间不能太长）

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter7-SequentialLogic-20.webp)

- 对于0-0重叠：偏差不会造成功能缺陷
- 对于1-1重叠：需满足D在重叠期间保持稳定的条件

> 这边的具体细节，请看<mark>
> 
> P229-230
> 
> </mark>
> 
> ，需注意主要看重叠期下一阶段的状态，判断是否会出现问题

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter7-SequentialLogic-21.webp)

### 真单相钟控寄存器 | TSPCR 结构

> 仅使用一个单相时钟信号（<span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
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
> 
> <mi>
> 
> K
> 
> </mi>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> CLK
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
> <span className="mord,mathnormal" style="margin-right:0.0715em;">
> 
> C
> 
> </span>
> 
> <span className="mord,mathnormal">
> 
> L
> 
> </span>
> 
> <span className="mord,mathnormal" style="margin-right:0.0715em;">
> 
> K
> 
> </span>
> </span>
> </span>
> </span>
> 
> ）来控制所有的锁存器和寄存器，而不像其他动态寄存器那样需要 <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
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
> 
> <mi>
> 
> K
> 
> </mi>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> CLK
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
> <span className="mord,mathnormal" style="margin-right:0.0715em;">
> 
> C
> 
> </span>
> 
> <span className="mord,mathnormal">
> 
> L
> 
> </span>
> 
> <span className="mord,mathnormal" style="margin-right:0.0715em;">
> 
> K
> 
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
> <mover accent="true">
> <mrow>
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
> 
> <mi>
> 
> K
> 
> </mi>
> </mrow>
> 
> <mo stretchy="true">
> 
> ‾
> 
> </mo>
> </mover>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> \overline{CLK}
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:0.8833em;">
> 
> 
> 
> </span>
> 
> <span className="mord,overline">
> <span className="vlist-t">
> <span className="vlist-r">
> <span className="vlist" style="height:0.8833em;">
> <span style="top:-3em;">
> <span className="pstrut" style="height:3em;">
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
> <span className="mord,mathnormal">
> 
> L
> 
> </span>
> 
> <span className="mord,mathnormal" style="margin-right:0.0715em;">
> 
> K
> 
> </span>
> </span>
> </span>
> 
> <span style="top:-3.8033em;">
> <span className="pstrut" style="height:3em;">
> 
> 
> 
> </span>
> 
> <span className="overline-line" style="border-bottom-width:0.04em;">
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
>  两个互补信号

#### 真单相锁存器 | TSPC

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter7-SequentialLogic-22.webp)

> 左边是正锁存器，右边是负锁存器

- 后面最好加反相器隔离，输出节点在某些状态下的浮空可能引发级联的其他信号耦合影响
- 逻辑功能可以嵌入（如下）

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter7-SequentialLogic-23.webp)

#### 简化的TSPC

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter7-SequentialLogic-24.webp)

晶体管节省，但并非全摆幅

- 正锁存器A在in=0时，高电平少Vtn
- 负锁存器A在in=1时，低电平多Vtp

#### 单相钟控寄存器 | TSPCR

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter7-SequentialLogic-25.webp)

> 看书P233

**时序特征：**

- **建立时间 (**<span className="katex">
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

s

</mi>

<mi>

u

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

t_{su}

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

s

</span>

<span className="mord,mathnormal,mtight">

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
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

**)**：等于输入端节点 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

X

</mi>
</mrow>

<annotation encoding="application/x-tex">

X

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0785em;">

X

</span>
</span>
</span>
</span>

 变得有效所需的时间，大约为一个反相器的延迟
- **保持时间 (**<span className="katex">
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

h

</mi>

<mi>

o

</mi>

<mi>

l

</mi>

<mi>

d

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

t_{hold}

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

h

</span>

<span className="mord,mathnormal,mtight">

o

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0197em;">

l

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

**)**：为了保证正确的逻辑求值，输入在时钟上升沿后需要保持极短的时间，通常小于一个反相器延迟
- **传播延迟 (**<span className="katex">
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

<mo>

−

</mo>

<mi>

q

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

t_{c-q}

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
<span className="vlist" style="height:0.2583em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

c

</span>

<span className="mbin,mtight">

−

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

**)**：相当于三个反相器的级联延迟（数据从 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

X

</mi>
</mrow>

<annotation encoding="application/x-tex">

X

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0785em;">

X

</span>
</span>
</span>
</span>

 传播到 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

Q

</mi>
</mrow>

<annotation encoding="application/x-tex">

Q

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8778em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal">

Q

</span>
</span>
</span>
</span>

）

#### **选择时钟策略**

> 选择合适的时钟方案会直接影响电路的功能、速度和功耗

- **两相时钟 (Two-phase designs):** 优点是稳健且概念简单；缺点是需要生成和布线两个时钟信号，并且设计时必须考虑到两个时钟信号之间可能出现的时钟偏移（skew）问题
- **单相时钟 (Single phase designs):** 优点是只需要生成和布线一个信号，大多数自动化设计工具都支持，且无需担心双时钟偏移；缺点是必须保证时钟边缘有足够陡峭的斜率

## 第 36–47 页：流水线、施密特触发器与多谐振荡器

### 流水线 | pipeline

> 流水线是一种通过在组合逻辑块之间插入寄存器或锁存器来提高系统吞吐量的技术。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter7-SequentialLogic-26.webp)

**课件中给出了基于锁存器和C2MOS的流水线**

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 45.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter7-SequentialLogic-27.webp" />
      </p>
    </td>
    
    
      <td style="width: 54.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter7-SequentialLogic-28.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

### 施密特触发器 | schmitt trigger

> 施密特触发器是一种具有迟滞现象的特殊电路，主要用于抗干扰和波形整形。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter7-SequentialLogic-29.webp)

施密特触发器的电压传输特性（VTC）具有迟滞（hysteresis）现象，这意味着它的正向阈值电压（<span className="katex">
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

M

</mi>

<mo>

+

</mo>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

V_{M+}

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
<span className="mord,mathnormal,mtight" style="margin-right:0.109em;">

M

</span>

<span className="mord,mtight">

+

</span>
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

）和反向阈值电压（<span className="katex">
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

M

</mi>

<mo>

−

</mo>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

V_{M-}

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
<span className="mord,mathnormal,mtight" style="margin-right:0.109em;">

M

</span>

<span className="mord,mtight">

−

</span>
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

）是不同的 。下图展示了其噪声抑制能力

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter7-SequentialLogic-30.webp)

左图展示了一个典型的CMOS施密特触发器电路图。它通过反馈机制（输出高电平时，两个PMOS并联和一个NMOS串联；低电平时，两个NMOS并联和一个PMOS串联）来动态改变第一个反相器的开关阈值。（具体见书P242）

右图表显示了如何通过调整晶体管的尺寸来改变迟滞窗口的大小。具体来说，改变PMOS器件 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

M

</mi>

<mn>

4

</mn>
</msub>
</mrow>

<annotation encoding="application/x-tex">

M_4

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

M

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
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
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

 的宽度比（宽度为 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

k

</mi>

<mo>

∗

</mo>

<mn>

0.5

</mn>

<mi>

μ

</mi>

<mi>

m

</mi>
</mrow>

<annotation encoding="application/x-tex">

k*0.5 \mu m

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

∗

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8389em;vertical-align:-0.1944em;">



</span>

<span className="mord">

0.5

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

），可以明显看到电压传输曲线的迟滞范围随之改变（M4越宽，等效电阻越小，VM越大，曲线越往上）

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 55.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter7-SequentialLogic-31.webp" />
      </p>
    </td>
    
    
      <td style="width: 44.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter7-SequentialLogic-32.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

### 多谐振荡器 |  Multivibrator Circuits

#### **多谐振荡器的分类**

- **双稳态 (Bistable):** 具有两个稳定状态（如触发器、施密特触发器）
- **单稳态 (Monostable):** 只有一个稳定状态，受激后会进入暂态，一段时间后自动恢复（如单稳态触发器/one-shot）
- **无稳态 (Astable):** 没有稳定状态，会在两个状态之间不断持续振荡（如振荡器）

#### 单稳态电路

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter7-SequentialLogic-33.webp)

当输入端检测到一个跳变（如上升沿）时，该电路会在输出端产生一个脉冲宽度严格为 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

t

</mi>

<mi>

d

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

t_d

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

 的脉冲信号

#### **无稳态多谐振荡器**

左图展示了环形振荡器（Ring Oscillator）的结构，通常由奇数个反相器首尾相连构成

右图图表显示了一个5级环形振荡器的电压波形随时间（ns）的周期性振荡响应

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 71.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter7-SequentialLogic-34.webp" />
      </p>
    </td>
    
    
      <td style="width: 28.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter7-SequentialLogic-35.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

奇数个反相器首尾相连构成的环形振荡器（Ring Oscillator）的周期计算公式<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

T

</mi>

<mo>

=

</mo>

<mn>

2

</mn>

<mo>

⋅

</mo>

<mi>

N

</mi>

<mo>

⋅

</mo>

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

T = 2 \cdot N \cdot t_p

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

<span className="mord,mathnormal" style="margin-right:0.109em;">

N

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
