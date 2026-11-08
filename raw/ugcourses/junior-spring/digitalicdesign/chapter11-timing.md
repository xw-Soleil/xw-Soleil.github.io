# Chapter 11：时序 Timing

> 时钟偏差与抖动、建立/保持时间约束，以及时钟分配网络的设计。

## 学习路线建议

建议按**5个板块**学，逻辑最顺，也便于后面做时序题。

1. **基础模型与术语**（第2–4页）
同步/异步/混合系统；寄存器—组合逻辑—寄存器模型；<mark>

掌握

</mark>

 <span className="katex">
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

<mark>

、

</mark>

<span className="katex">
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

<mark>

、

</mark>

<span className="katex">
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

<mark>

、时钟周期

</mark>

。
2. **时钟非理想性与来源**（第5–13页）
重点区分 skew 和 jitter，理解正/负 skew，以及工艺、互连、电源、温度、耦合等不确定性来源。
3. **核心：Setup / Hold 时序约束**（第14–19页）
<mark>

这是本章最重要的部分。要会推导并使用

</mark>

：

  - setup 看**最长路径**，决定最高工作频率；
  - hold 看**最短路径**，与时钟周期通常无关；
  - skew、jitter 对两类约束的影响与权衡。
4. **时钟分配网络与功耗**（第20–31页）
<mark>

H-tree

</mark>

、matched RC tree、<mark>

clock grid

</mark>

、clock driver、clock gating；理解“降低 skew”和“降低时钟功耗”之间的工程取舍。
5. **工程应对与异步设计**（第32页及后续）
总结怎么减小 skew/jitter：平衡路径、数据与时钟布线方向、屏蔽、dummy fill、控制电源与温度变化等；最后把所有公式放回同一条寄存器到寄存器路径上做题。<mark>

二相四相异步设计

</mark>

**学习优先级：第3板块 > 第2板块 > 第4板块 > 第1、5板块。**
这份课件的主线可以浓缩成一句话：**时钟不完美会压缩可用时序窗口，因此必须同时保证 setup 和 hold。**

---

## 板块一：基础模型与术语（第 2–4 页）

### 第 2 页：Timing Classifications——时序系统的三种分类

1. 同步系统（Synchronous systems）

同步系统使用一棵全局时钟树，把同一个周期性的 `CLK` 分发给所有寄存器。

两类问题：

- **Clock skew（时钟偏斜）**：<mark>

同一个时钟沿到不同位置的寄存器，时间不一致

</mark>

。<mark>

它是“空间上的差异”。

</mark>
- **Clock jitter（时钟抖动）**：<mark>

同一个位置的时钟沿，在不同周期出现的时间会漂移

</mark>

。<mark>

它是“时间上的差异”。

</mark>

1. 异步系统（Asynchronous systems）

<mark>

异步系统没有全局统一时钟。模块之间通常靠握手信号协调

</mark>

，例如“数据准备好”和“我已接收”。

优点是没有<mark>

全局时钟分配

</mark>

与严重的<mark>

时钟 skew

</mark>

 问题

缺点是需要额外的握手逻辑，设计与验证难度更高。

1. 混合系统（Hybrid systems）

现实芯片里很常见：芯片整体可能是同步的，但内部不同模块运行在不同频率，或者部分接口是异步的。

---

### 第 4 页：Register Parameters——触发器必须掌握的四个量

这一页定义了同步时序分析最核心的参数。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter11-Timing-01.webp)

#### 1. 时钟周期 <span className="katex">
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



#### 2. 建立时间 <span className="katex">
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

（setup time）

在有效时钟沿到来**之前**，寄存器<mark>

输入端 D 必须已经稳定的最短时间

</mark>

。

#### 3. 保持时间 <span className="katex">
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

（hold time）

在有效时钟沿到来**之后**，寄存器输入端 D 还必须继续保持稳定的最短时间。

#### 4. 时钟到输出延迟 <span className="katex">
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

（clock-to-Q delay）

时钟沿到达寄存器后，Q 端不会立刻变化，而是经过一段延迟才更新。

这段延迟就是数据从 R1 “发射”出来的起始代价。

---

## 板块二：时钟非理想性与来源（第 5–13 页）

### 第 5 页：Clock Nonidealities——真实时钟并不完美

这一页给出三类关键时钟问题。

1. Clock skew
2. Clock jitter

课件把 jitter 分成：

- **Cycle-to-cycle / short-term jitter，**<span className="katex">
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

J

</mi>

<mi>

S

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

t_{JS}

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
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0962em;">

J

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

S

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

：相邻周期之间的变化，最直接影响单周期时序；
- **Long-term jitter，**<span className="katex">
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

J

</mi>

<mi>

L

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

t_{JL}

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
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0962em;">

J

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

：经过多个周期后相对理想参考时钟的累计漂移。

1. 脉宽变化（pulse width variation）

---

### 第 6 页：Clock Skew and Jitter——两者怎样影响有效周期

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter11-Timing-02.webp)

> **Skew 比较的是节点之间；jitter 比较的是周期之间。**

---

### 第 7-9 页：Clock Uncertainties——时钟不确定性的物理来源

图中列出 7 个来源：

1. **Clock generation**：时钟源本身不完美，例如 PLL / DLL 的相位噪声、频率误差。
2. **Devices**：驱动器、缓冲器的晶体管参数存在工艺偏差。
3. <mark>

**Interconnect**

</mark>

<mark>

：导线长度、宽度、厚度、寄生电阻与电容不同。（dummy filled来缓解）

</mark>
4. **Power supply**：供电波动会改变门延迟。
5. **Temperature**：温度变化会改变晶体管速度和互连电阻。
6. **Capacitive load**：不同分支挂载的负载不同，延迟不同。
7. **Coupling to adjacent lines**：相邻信号翻转通过耦合电容影响时钟边沿。

---

### 第 10 页：Positive and Negative Skew——正偏斜与负偏斜

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter11-Timing-03.webp)

数据和时钟同向   正 skew  <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

δ

</mi>

<mo>

>
</mo>

<mn>

0

</mn>
</mrow>

<annotation encoding="application/x-tex">

\delta>0

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.7335em;vertical-align:-0.0391em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0379em;">

δ

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



数据和时钟反向   负 skew  <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

δ

</mi>

<mo>
<

</mo>

<mn>

0

</mn>
</mrow>

<annotation encoding="application/x-tex">

\delta<0

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.7335em;vertical-align:-0.0391em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0379em;">

δ

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



---

### 第 11-12 页：波形图如何理解

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 47.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter11-Timing-04.webp" />
      </p>
    </td>
    
    
      <td style="width: 52.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter11-Timing-05.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

---

### 这 12 页学完后，你应能回答

1. <span className="katex">
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

、<span className="katex">
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

、<span className="katex">
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

 分别代表什么？
2. skew 和 jitter 的区别是什么？
3. 为什么互连、电源、温度都会造成时钟不确定性？
4. 正 skew 为什么对 setup 有利、对 hold 不利？
5. 为什么数据与时钟同向传播常对应正 skew？

---

## 模块三：Setup / Hold 时序约束（第14–19页）

---

## 第 14 页：Setup Time Constraint

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<msub>
<mi>

T

</mi>

<mrow>
<mi>

C

</mi>

<mi>

L

</mi>

<mi>

K

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

c

</mi>

<mo>

−

</mo>

<mi>

q

</mi>

<mo stretchy="false">

(

</mo>

<mi>

m

</mi>

<mi>

a

</mi>

<mi>

x

</mi>

<mo stretchy="false">

)

</mo>
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

<mo stretchy="false">

(

</mo>

<mi>

m

</mi>

<mi>

a

</mi>

<mi>

x

</mi>

<mo stretchy="false">

)

</mo>
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

T_{CLK}\ge t_{c-q(max)}+t_{logic(max)}+t_{su}

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
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.1389em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0715em;">

C

</span>

<span className="mord,mathnormal,mtight">

L

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0715em;">

K

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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

≥

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.9703em;vertical-align:-0.3552em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

t

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3448em;">
<span style="top:-2.5198em;margin-left:0em;margin-right:0.05em;">
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

<span className="mopen,mtight">

(

</span>

<span className="mord,mathnormal,mtight">

ma

</span>

<span className="mord,mathnormal,mtight">

x

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

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.9703em;vertical-align:-0.3552em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

t

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3448em;">
<span style="top:-2.5198em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
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

<span className="mopen,mtight">

(

</span>

<span className="mord,mathnormal,mtight">

ma

</span>

<span className="mord,mathnormal,mtight">

x

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
</span>

---

## 第 15 页：Hold Time Constraint

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
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

<mo>

≤

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

<mo stretchy="false">

(

</mo>

<mi>

m

</mi>

<mi>

i

</mi>

<mi>

n

</mi>

<mo stretchy="false">

)

</mo>
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

<mo stretchy="false">

(

</mo>

<mi>

m

</mi>

<mi>

i

</mi>

<mi>

n

</mi>

<mo stretchy="false">

)

</mo>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

t_{hold}\le t_{c-q(min)}+t_{cdlogic(min)}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.786em;vertical-align:-0.15em;">



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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

≤

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.9703em;vertical-align:-0.3552em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

t

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3448em;">
<span style="top:-2.5198em;margin-left:0em;margin-right:0.05em;">
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

<span className="mopen,mtight">

(

</span>

<span className="mord,mathnormal,mtight">

min

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

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.9703em;vertical-align:-0.3552em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

t

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3448em;">
<span style="top:-2.5198em;margin-left:0em;margin-right:0.05em;">
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

<span className="mopen,mtight">

(

</span>

<span className="mord,mathnormal,mtight">

min

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

---

## 第 16 页：Positive Clock Skew

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter11-Timing-06.webp)

### 1. 对 setup 的影响：有利

相对周期变为：     <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

T

</mi>

<mo>

+

</mo>

<mi>

δ

</mi>
</mrow>

<annotation encoding="application/x-tex">

T+\delta

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

T

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

<span className="mord,mathnormal" style="margin-right:0.0379em;">

δ

</span>
</span>
</span>
</span>



setup 条件变成：  <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

T

</mi>

<mo>

+

</mo>

<mi>

δ

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

T+\delta\ge t_{c-q}+t_{plogic}+t_{su}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

T

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

<span className="mord,mathnormal" style="margin-right:0.0379em;">

δ

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



整理：                   <span className="katex">
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

<mo>

−

</mo>

<mi>

δ

</mi>
</mrow>

<annotation encoding="application/x-tex">

T\ge t_{c-q}+t_{plogic}+t_{su}-\delta

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

<span className="mord,mathnormal" style="margin-right:0.0379em;">

δ

</span>
</span>
</span>
</span>



所以正 skew 可以放松 setup 约束，理论上允许更短时钟周期、更高频率。

### 2. 对 hold 的影响：不利

R2 当前周期的采样沿也晚了 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

δ

</mi>
</mrow>

<annotation encoding="application/x-tex">

\delta

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0379em;">

δ

</span>
</span>
</span>
</span>

，这意味着它要求旧数据保持得更久。

hold条件变为：              <span className="katex">
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

<mo>

+

</mo>

<mi>

δ

</mi>

<mo>

≤

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
</mrow>

<annotation encoding="application/x-tex">

t_{hold}+\delta\le t_{cdlogic}+t_{cdreg}

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

<span className="mord,mathnormal" style="margin-right:0.0379em;">

δ

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
</span>
</span>
</span>



整理：                            <span className="katex">
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

<mo>

≤

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

−

</mo>

<mi>

δ

</mi>
</mrow>

<annotation encoding="application/x-tex">

t_{hold}\le t_{cdlogic}+t_{cdreg}-\delta

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.786em;vertical-align:-0.15em;">



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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

≤

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

−

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0379em;">

δ

</span>
</span>
</span>
</span>



当 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

δ

</mi>
</mrow>

<annotation encoding="application/x-tex">

\delta

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0379em;">

δ

</span>
</span>
</span>
</span>

 增大，右侧变小，hold 更难满足。

所以不能简单说“正 skew 一定好”。它是在<mark>

**用 hold 裕量换取 setup 裕量**

</mark>

<mark>

。

</mark>



课件特别强调：若 hold 不满足，会产生 race condition，而且即使降低时钟频率也无法消除。

---

## 第 17 页：Negative Clock Skew

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter11-Timing-07.webp)

### 1. 对 setup 的影响：不利

有效可用时间变为：    <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

T

</mi>

<mo>

+

</mo>

<mi>

δ

</mi>
</mrow>

<annotation encoding="application/x-tex">

T+\delta

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

T

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

<span className="mord,mathnormal" style="margin-right:0.0379em;">

δ

</span>
</span>
</span>
</span>



setup 条件仍然是：     <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

T

</mi>

<mo>

+

</mo>

<mi>

δ

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

T+\delta\ge t_{c-q}+t_{plogic}+t_{su}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

T

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

<span className="mord,mathnormal" style="margin-right:0.0379em;">

δ

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



整理后：                      <span className="katex">
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

<mo>

−

</mo>

<mi>

δ

</mi>
</mrow>

<annotation encoding="application/x-tex">

T\ge t_{c-q}+t_{plogic}+t_{su}-\delta

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

<span className="mord,mathnormal" style="margin-right:0.0379em;">

δ

</span>
</span>
</span>
</span>



因为 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mo>

−

</mo>

<mi>

δ

</mi>

<mo>

>
</mo>

<mn>

0

</mn>
</mrow>

<annotation encoding="application/x-tex">

-\delta>0

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.7778em;vertical-align:-0.0833em;">



</span>

<span className="mord">

−

</span>

<span className="mord,mathnormal" style="margin-right:0.0379em;">

δ

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

，所需时钟周期变长，频率必须降低。

### 2. 对 hold 的影响：有利

R2 更早完成采样和保持窗口，新数据即使较早到达，也更不容易破坏旧数据。

因此负 skew 往往能缓解 hold 风险。

---

## 第 18 页：Clock Jitter

这一页讨论 jitter 对 setup 的影响。

假设每一个时钟沿都可能偏移 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mo>

±

</mo>

<msub>
<mi>

t

</mi>

<mrow>
<mi>

j

</mi>

<mi>

i

</mi>

<mi>

t

</mi>

<mi>

t

</mi>

<mi>

e

</mi>

<mi>

r

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

\pm t_{jitter}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9012em;vertical-align:-0.2861em;">



</span>

<span className="mord">

±

</span>

<span className="mord">
<span className="mord,mathnormal">

t

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0572em;">

j

</span>

<span className="mord,mathnormal,mtight">

i

</span>

<span className="mord,mathnormal,mtight">

tt

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

er

</span>
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

对 setup 最坏的情况是：

- 发射边沿晚到 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mo>

+

</mo>

<msub>
<mi>

t

</mi>

<mrow>
<mi>

j

</mi>

<mi>

i

</mi>

<mi>

t

</mi>

<mi>

t

</mi>

<mi>

e

</mi>

<mi>

r

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

+t_{jitter}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9012em;vertical-align:-0.2861em;">



</span>

<span className="mord">

+

</span>

<span className="mord">
<span className="mord,mathnormal">

t

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0572em;">

j

</span>

<span className="mord,mathnormal,mtight">

i

</span>

<span className="mord,mathnormal,mtight">

tt

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

er

</span>
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

；
- 接收边沿早到 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mo>

−

</mo>

<msub>
<mi>

t

</mi>

<mrow>
<mi>

j

</mi>

<mi>

i

</mi>

<mi>

t

</mi>

<mi>

t

</mi>

<mi>

e

</mi>

<mi>

r

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

-t_{jitter}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9012em;vertical-align:-0.2861em;">



</span>

<span className="mord">

−

</span>

<span className="mord">
<span className="mord,mathnormal">

t

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0572em;">

j

</span>

<span className="mord,mathnormal,mtight">

i

</span>

<span className="mord,mathnormal,mtight">

tt

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

er

</span>
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

于是原本周期 <span className="katex">
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

 被压缩成：    <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

T

</mi>

<mo>

−

</mo>

<mn>

2

</mn>

<msub>
<mi>

t

</mi>

<mrow>
<mi>

j

</mi>

<mi>

i

</mi>

<mi>

t

</mi>

<mi>

t

</mi>

<mi>

e

</mi>

<mi>

r

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

T-2t_{jitter}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

T

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
<span className="strut" style="height:0.9305em;vertical-align:-0.2861em;">



</span>

<span className="mord">

2

</span>

<span className="mord">
<span className="mord,mathnormal">

t

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0572em;">

j

</span>

<span className="mord,mathnormal,mtight">

i

</span>

<span className="mord,mathnormal,mtight">

tt

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

er

</span>
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



所以 setup 条件变成：              <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

T

</mi>

<mo>

−

</mo>

<mn>

2

</mn>

<msub>
<mi>

t

</mi>

<mrow>
<mi>

j

</mi>

<mi>

i

</mi>

<mi>

t

</mi>

<mi>

t

</mi>

<mi>

e

</mi>

<mi>

r

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

T-2t_{jitter}\ge t_{c-q}+t_{plogic}+t_{su}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

T

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
<span className="strut" style="height:0.9305em;vertical-align:-0.2861em;">



</span>

<span className="mord">

2

</span>

<span className="mord">
<span className="mord,mathnormal">

t

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0572em;">

j

</span>

<span className="mord,mathnormal,mtight">

i

</span>

<span className="mord,mathnormal,mtight">

tt

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

er

</span>
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



整理：                                       <span className="katex">
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

<mo>

+

</mo>

<mn>

2

</mn>

<msub>
<mi>

t

</mi>

<mrow>
<mi>

j

</mi>

<mi>

i

</mi>

<mi>

t

</mi>

<mi>

t

</mi>

<mi>

e

</mi>

<mi>

r

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

T\ge t_{c-q}+t_{plogic}+t_{su}+2t_{jitter}

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.9305em;vertical-align:-0.2861em;">



</span>

<span className="mord">

2

</span>

<span className="mord">
<span className="mord,mathnormal">

t

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0572em;">

j

</span>

<span className="mord,mathnormal,mtight">

i

</span>

<span className="mord,mathnormal,mtight">

tt

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

er

</span>
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



### 关键理解

jitter 不像正 skew 那样可能带来某种 setup 好处。
它本质上是时间不确定性，会直接吃掉时序裕量。

注意：课件这里写 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mn>

2

</mn>

<msub>
<mi>

t

</mi>

<mrow>
<mi>

j

</mi>

<mi>

i

</mi>

<mi>

t

</mi>

<mi>

t

</mi>

<mi>

e

</mi>

<mi>

r

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

2t_{jitter}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9305em;vertical-align:-0.2861em;">



</span>

<span className="mord">

2

</span>

<span className="mord">
<span className="mord,mathnormal">

t

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0572em;">

j

</span>

<span className="mord,mathnormal,mtight">

i

</span>

<span className="mord,mathnormal,mtight">

tt

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

er

</span>
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

，是因为其模型假设发射和接收边沿都可能分别偏移一个 <span className="katex">
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

j

</mi>

<mi>

i

</mi>

<mi>

t

</mi>

<mi>

t

</mi>

<mi>

e

</mi>

<mi>

r

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

t_{jitter}

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
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0572em;">

j

</span>

<span className="mord,mathnormal,mtight">

i

</span>

<span className="mord,mathnormal,mtight">

tt

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

er

</span>
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

。实际工程中要看库、PLL 或 STA 工具给出的 jitter 定义，不能机械地总是乘 2。

---

## 第 19 页：Skew 与 Jitter 的综合影响

这一页将正 skew 和 jitter 一起考虑。

### 1. Setup 条件

正 skew 给了额外时间 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

δ

</mi>
</mrow>

<annotation encoding="application/x-tex">

\delta

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0379em;">

δ

</span>
</span>
</span>
</span>

，但 jitter 损失了 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mn>

2

</mn>

<msub>
<mi>

t

</mi>

<mrow>
<mi>

j

</mi>

<mi>

i

</mi>

<mi>

t

</mi>

<mi>

t

</mi>

<mi>

e

</mi>

<mi>

r

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

2t_{jitter}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9305em;vertical-align:-0.2861em;">



</span>

<span className="mord">

2

</span>

<span className="mord">
<span className="mord,mathnormal">

t

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0572em;">

j

</span>

<span className="mord,mathnormal,mtight">

i

</span>

<span className="mord,mathnormal,mtight">

tt

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

er

</span>
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

有效可用时间：                           <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

T

</mi>

<mo>

+

</mo>

<mi>

δ

</mi>

<mo>

−

</mo>

<mn>

2

</mn>

<msub>
<mi>

t

</mi>

<mrow>
<mi>

j

</mi>

<mi>

i

</mi>

<mi>

t

</mi>

<mi>

t

</mi>

<mi>

e

</mi>

<mi>

r

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

T+\delta-2t_{jitter}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

T

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
<span className="strut" style="height:0.7778em;vertical-align:-0.0833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0379em;">

δ

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
<span className="strut" style="height:0.9305em;vertical-align:-0.2861em;">



</span>

<span className="mord">

2

</span>

<span className="mord">
<span className="mord,mathnormal">

t

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0572em;">

j

</span>

<span className="mord,mathnormal,mtight">

i

</span>

<span className="mord,mathnormal,mtight">

tt

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

er

</span>
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



因此：                                         <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

T

</mi>

<mo>

+

</mo>

<mi>

δ

</mi>

<mo>

−

</mo>

<mn>

2

</mn>

<msub>
<mi>

t

</mi>

<mrow>
<mi>

j

</mi>

<mi>

i

</mi>

<mi>

t

</mi>

<mi>

t

</mi>

<mi>

e

</mi>

<mi>

r

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

T+\delta-2t_{jitter} \ge t_{c-q}+t_{plogic}+t_{su}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

T

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
<span className="strut" style="height:0.7778em;vertical-align:-0.0833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0379em;">

δ

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
<span className="strut" style="height:0.9305em;vertical-align:-0.2861em;">



</span>

<span className="mord">

2

</span>

<span className="mord">
<span className="mord,mathnormal">

t

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0572em;">

j

</span>

<span className="mord,mathnormal,mtight">

i

</span>

<span className="mord,mathnormal,mtight">

tt

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

er

</span>
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



整理：                                         <span className="katex">
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

<mo>

−

</mo>

<mi>

δ

</mi>

<mo>

+

</mo>

<mn>

2

</mn>

<msub>
<mi>

t

</mi>

<mrow>
<mi>

j

</mi>

<mi>

i

</mi>

<mi>

t

</mi>

<mi>

t

</mi>

<mi>

e

</mi>

<mi>

r

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

T\ge t_{c-q}+t_{plogic}+t_{su} -\delta +2t_{jitter}

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

−

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.7778em;vertical-align:-0.0833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0379em;">

δ

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
<span className="strut" style="height:0.9305em;vertical-align:-0.2861em;">



</span>

<span className="mord">

2

</span>

<span className="mord">
<span className="mord,mathnormal">

t

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0572em;">

j

</span>

<span className="mord,mathnormal,mtight">

i

</span>

<span className="mord,mathnormal,mtight">

tt

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

er

</span>
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



含义是：

- 正 skew 能帮 setup；
- jitter 会抵消甚至超过这部分收益；
- 想利用正 skew 提升频率，必须先留足 jitter 裕量。

### 2. Hold 条件

对于 hold，正 skew 和 jitter 都会使约束更苛刻：    <span className="katex">
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

<mo>

≤

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

−

</mo>

<mi>

δ

</mi>

<mo>

−

</mo>

<mn>

2

</mn>

<msub>
<mi>

t

</mi>

<mrow>
<mi>

j

</mi>

<mi>

i

</mi>

<mi>

t

</mi>

<mi>

t

</mi>

<mi>

e

</mi>

<mi>

r

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

t_{hold}\le t_{cdlogic}+t_{cdreg} -\delta -2t_{jitter}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.786em;vertical-align:-0.15em;">



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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

≤

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

−

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.7778em;vertical-align:-0.0833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0379em;">

δ

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
<span className="strut" style="height:0.9305em;vertical-align:-0.2861em;">



</span>

<span className="mord">

2

</span>

<span className="mord">
<span className="mord,mathnormal">

t

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0572em;">

j

</span>

<span className="mord,mathnormal,mtight">

i

</span>

<span className="mord,mathnormal,mtight">

tt

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

er

</span>
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



也可以理解为：                                                        <span className="katex">
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

<mo>

+

</mo>

<mi>

δ

</mi>

<mo>

+

</mo>

<mn>

2

</mn>

<msub>
<mi>

t

</mi>

<mrow>
<mi>

j

</mi>

<mi>

i

</mi>

<mi>

t

</mi>

<mi>

t

</mi>

<mi>

e

</mi>

<mi>

r

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

t_{cdlogic}+t_{cdreg} \ge t_{hold}+\delta+2t_{jitter}

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.7778em;vertical-align:-0.0833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0379em;">

δ

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
<span className="strut" style="height:0.9305em;vertical-align:-0.2861em;">



</span>

<span className="mord">

2

</span>

<span className="mord">
<span className="mord,mathnormal">

t

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0572em;">

j

</span>

<span className="mord,mathnormal,mtight">

i

</span>

<span className="mord,mathnormal,mtight">

tt

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

er

</span>
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



因此，jitter 不仅影响 setup，也会减少可接受的正 skew。

---

## 这一板块的核心公式表

<table>
<thead>
  <tr>
    <th>
      场景
    </th>
    
    <th>
      Setup 条件
    </th>
    
    <th>
      Hold 条件
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      无 skew、无 jitter
    </td>
    
    <td>
      <span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <mtext>
                  
                </mtext>
                
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
                    
                    <mo stretchy="false">
                      (
                    </mo>
                    
                    <mi>
                      m
                    </mi>
                    
                    <mi>
                      a
                    </mi>
                    
                    <mi>
                      x
                    </mi>
                    
                    <mo stretchy="false">
                      )
                    </mo>
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
                    
                    <mo stretchy="false">
                      (
                    </mo>
                    
                    <mi>
                      m
                    </mi>
                    
                    <mi>
                      a
                    </mi>
                    
                    <mi>
                      x
                    </mi>
                    
                    <mo stretchy="false">
                      )
                    </mo>
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
                \;T\ge t_{c-q(max)}+t_{logic(max)}+t_{su}
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:0.8193em;vertical-align:-0.136em;">
              
            </span>
            
            <span className="mspace" style="margin-right:0.2778em;">
              
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
            <span className="strut" style="height:0.9703em;vertical-align:-0.3552em;">
              
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal">
                t
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.3448em;">
                      <span style="top:-2.5198em;margin-left:0em;margin-right:0.05em;">
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
                            
                            <span className="mopen,mtight">
                              (
                            </span>
                            
                            <span className="mord,mathnormal,mtight">
                              ma
                            </span>
                            
                            <span className="mord,mathnormal,mtight">
                              x
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
              +
            </span>
            
            <span className="mspace" style="margin-right:0.2222em;">
              
            </span>
          </span>
          
          <span className="base">
            <span className="strut" style="height:0.9703em;vertical-align:-0.3552em;">
              
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal">
                t
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.3448em;">
                      <span style="top:-2.5198em;margin-left:0em;margin-right:0.05em;">
                        <span className="pstrut" style="height:2.7em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mtight">
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
                            
                            <span className="mopen,mtight">
                              (
                            </span>
                            
                            <span className="mord,mathnormal,mtight">
                              ma
                            </span>
                            
                            <span className="mord,mathnormal,mtight">
                              x
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
    </td>
    
    <td>
      <span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <mtext>
                  
                </mtext>
                
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
                    
                    <mo stretchy="false">
                      (
                    </mo>
                    
                    <mi>
                      m
                    </mi>
                    
                    <mi>
                      i
                    </mi>
                    
                    <mi>
                      n
                    </mi>
                    
                    <mo stretchy="false">
                      )
                    </mo>
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
                    
                    <mo stretchy="false">
                      (
                    </mo>
                    
                    <mi>
                      m
                    </mi>
                    
                    <mi>
                      i
                    </mi>
                    
                    <mi>
                      n
                    </mi>
                    
                    <mo stretchy="false">
                      )
                    </mo>
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
                \;t_{c-q(min)}+t_{logic(min)}\ge t_{hold}
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:0.9703em;vertical-align:-0.3552em;">
              
            </span>
            
            <span className="mspace" style="margin-right:0.2778em;">
              
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal">
                t
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.3448em;">
                      <span style="top:-2.5198em;margin-left:0em;margin-right:0.05em;">
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
                            
                            <span className="mopen,mtight">
                              (
                            </span>
                            
                            <span className="mord,mathnormal,mtight">
                              min
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
              +
            </span>
            
            <span className="mspace" style="margin-right:0.2222em;">
              
            </span>
          </span>
          
          <span className="base">
            <span className="strut" style="height:0.9912em;vertical-align:-0.3552em;">
              
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal">
                t
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.3448em;">
                      <span style="top:-2.5198em;margin-left:0em;margin-right:0.05em;">
                        <span className="pstrut" style="height:2.7em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mtight">
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
                            
                            <span className="mopen,mtight">
                              (
                            </span>
                            
                            <span className="mord,mathnormal,mtight">
                              min
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
    </td>
  </tr>
  
  <tr>
    <td>
      加 skew <span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <mi>
                  δ
                </mi>
              </mrow>
              
              <annotation encoding="application/x-tex">
                \delta
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:0.6944em;">
              
            </span>
            
            <span className="mord,mathnormal" style="margin-right:0.0379em;">
              δ
            </span>
          </span>
        </span>
      </span>
    </td>
    
    <td>
      <span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <mtext>
                  
                </mtext>
                
                <mi>
                  T
                </mi>
                
                <mo>
                  +
                </mo>
                
                <mi>
                  δ
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
                    
                    <mo stretchy="false">
                      (
                    </mo>
                    
                    <mi>
                      m
                    </mi>
                    
                    <mi>
                      a
                    </mi>
                    
                    <mi>
                      x
                    </mi>
                    
                    <mo stretchy="false">
                      )
                    </mo>
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
                    
                    <mo stretchy="false">
                      (
                    </mo>
                    
                    <mi>
                      m
                    </mi>
                    
                    <mi>
                      a
                    </mi>
                    
                    <mi>
                      x
                    </mi>
                    
                    <mo stretchy="false">
                      )
                    </mo>
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
                \;T+\delta\ge t_{c-q(max)}+t_{logic(max)}+t_{su}
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">
              
            </span>
            
            <span className="mspace" style="margin-right:0.2778em;">
              
            </span>
            
            <span className="mord,mathnormal" style="margin-right:0.1389em;">
              T
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
            
            <span className="mord,mathnormal" style="margin-right:0.0379em;">
              δ
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
            <span className="strut" style="height:0.9703em;vertical-align:-0.3552em;">
              
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal">
                t
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.3448em;">
                      <span style="top:-2.5198em;margin-left:0em;margin-right:0.05em;">
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
                            
                            <span className="mopen,mtight">
                              (
                            </span>
                            
                            <span className="mord,mathnormal,mtight">
                              ma
                            </span>
                            
                            <span className="mord,mathnormal,mtight">
                              x
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
              +
            </span>
            
            <span className="mspace" style="margin-right:0.2222em;">
              
            </span>
          </span>
          
          <span className="base">
            <span className="strut" style="height:0.9703em;vertical-align:-0.3552em;">
              
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal">
                t
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.3448em;">
                      <span style="top:-2.5198em;margin-left:0em;margin-right:0.05em;">
                        <span className="pstrut" style="height:2.7em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mtight">
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
                            
                            <span className="mopen,mtight">
                              (
                            </span>
                            
                            <span className="mord,mathnormal,mtight">
                              ma
                            </span>
                            
                            <span className="mord,mathnormal,mtight">
                              x
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
    </td>
    
    <td>
      <span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <mtext>
                  
                </mtext>
                
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
                    
                    <mo stretchy="false">
                      (
                    </mo>
                    
                    <mi>
                      m
                    </mi>
                    
                    <mi>
                      i
                    </mi>
                    
                    <mi>
                      n
                    </mi>
                    
                    <mo stretchy="false">
                      )
                    </mo>
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
                    
                    <mo stretchy="false">
                      (
                    </mo>
                    
                    <mi>
                      m
                    </mi>
                    
                    <mi>
                      i
                    </mi>
                    
                    <mi>
                      n
                    </mi>
                    
                    <mo stretchy="false">
                      )
                    </mo>
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
                
                <mo>
                  +
                </mo>
                
                <mi>
                  δ
                </mi>
              </mrow>
              
              <annotation encoding="application/x-tex">
                \;t_{c-q(min)}+t_{logic(min)}\ge t_{hold}+\delta
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:0.9703em;vertical-align:-0.3552em;">
              
            </span>
            
            <span className="mspace" style="margin-right:0.2778em;">
              
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal">
                t
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.3448em;">
                      <span style="top:-2.5198em;margin-left:0em;margin-right:0.05em;">
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
                            
                            <span className="mopen,mtight">
                              (
                            </span>
                            
                            <span className="mord,mathnormal,mtight">
                              min
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
              +
            </span>
            
            <span className="mspace" style="margin-right:0.2222em;">
              
            </span>
          </span>
          
          <span className="base">
            <span className="strut" style="height:0.9912em;vertical-align:-0.3552em;">
              
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal">
                t
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.3448em;">
                      <span style="top:-2.5198em;margin-left:0em;margin-right:0.05em;">
                        <span className="pstrut" style="height:2.7em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mtight">
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
                            
                            <span className="mopen,mtight">
                              (
                            </span>
                            
                            <span className="mord,mathnormal,mtight">
                              min
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
            
            <span className="mord,mathnormal" style="margin-right:0.0379em;">
              δ
            </span>
          </span>
        </span>
      </span>
    </td>
  </tr>
  
  <tr>
    <td>
      加 jitter
    </td>
    
    <td>
      <span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <mtext>
                  
                </mtext>
                
                <mi>
                  T
                </mi>
                
                <mo>
                  −
                </mo>
                
                <mn>
                  2
                </mn>
                
                <msub>
                  <mi>
                    t
                  </mi>
                  
                  <mi>
                    j
                  </mi>
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
                      c
                    </mi>
                    
                    <mo>
                      −
                    </mo>
                    
                    <mi>
                      q
                    </mi>
                    
                    <mo stretchy="false">
                      (
                    </mo>
                    
                    <mi>
                      m
                    </mi>
                    
                    <mi>
                      a
                    </mi>
                    
                    <mi>
                      x
                    </mi>
                    
                    <mo stretchy="false">
                      )
                    </mo>
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
                    
                    <mo stretchy="false">
                      (
                    </mo>
                    
                    <mi>
                      m
                    </mi>
                    
                    <mi>
                      a
                    </mi>
                    
                    <mi>
                      x
                    </mi>
                    
                    <mo stretchy="false">
                      )
                    </mo>
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
                \;T-2t_j\ge t_{c-q(max)}+t_{logic(max)}+t_{su}
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">
              
            </span>
            
            <span className="mspace" style="margin-right:0.2778em;">
              
            </span>
            
            <span className="mord,mathnormal" style="margin-right:0.1389em;">
              T
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
            <span className="strut" style="height:0.9305em;vertical-align:-0.2861em;">
              
            </span>
            
            <span className="mord">
              2
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal">
                t
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
            
            <span className="mspace" style="margin-right:0.2778em;">
              
            </span>
            
            <span className="mrel">
              ≥
            </span>
            
            <span className="mspace" style="margin-right:0.2778em;">
              
            </span>
          </span>
          
          <span className="base">
            <span className="strut" style="height:0.9703em;vertical-align:-0.3552em;">
              
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal">
                t
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.3448em;">
                      <span style="top:-2.5198em;margin-left:0em;margin-right:0.05em;">
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
                            
                            <span className="mopen,mtight">
                              (
                            </span>
                            
                            <span className="mord,mathnormal,mtight">
                              ma
                            </span>
                            
                            <span className="mord,mathnormal,mtight">
                              x
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
              +
            </span>
            
            <span className="mspace" style="margin-right:0.2222em;">
              
            </span>
          </span>
          
          <span className="base">
            <span className="strut" style="height:0.9703em;vertical-align:-0.3552em;">
              
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal">
                t
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.3448em;">
                      <span style="top:-2.5198em;margin-left:0em;margin-right:0.05em;">
                        <span className="pstrut" style="height:2.7em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mtight">
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
                            
                            <span className="mopen,mtight">
                              (
                            </span>
                            
                            <span className="mord,mathnormal,mtight">
                              ma
                            </span>
                            
                            <span className="mord,mathnormal,mtight">
                              x
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
    </td>
    
    <td>
      最坏情况下同样会压缩 hold 裕量
    </td>
  </tr>
  
  <tr>
    <td>
      skew + jitter
    </td>
    
    <td>
      <span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <mtext>
                  
                </mtext>
                
                <mi>
                  T
                </mi>
                
                <mo>
                  +
                </mo>
                
                <mi>
                  δ
                </mi>
                
                <mo>
                  −
                </mo>
                
                <mn>
                  2
                </mn>
                
                <msub>
                  <mi>
                    t
                  </mi>
                  
                  <mi>
                    j
                  </mi>
                </msub>
                
                <mo>
                  ≥
                </mo>
                
                <mo>
                  ⋯
                </mo>
              </mrow>
              
              <annotation encoding="application/x-tex">
                \;T+\delta-2t_j\ge \cdots
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">
              
            </span>
            
            <span className="mspace" style="margin-right:0.2778em;">
              
            </span>
            
            <span className="mord,mathnormal" style="margin-right:0.1389em;">
              T
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
            <span className="strut" style="height:0.7778em;vertical-align:-0.0833em;">
              
            </span>
            
            <span className="mord,mathnormal" style="margin-right:0.0379em;">
              δ
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
            <span className="strut" style="height:0.9305em;vertical-align:-0.2861em;">
              
            </span>
            
            <span className="mord">
              2
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal">
                t
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
            
            <span className="mspace" style="margin-right:0.2778em;">
              
            </span>
            
            <span className="mrel">
              ≥
            </span>
            
            <span className="mspace" style="margin-right:0.2778em;">
              
            </span>
          </span>
          
          <span className="base">
            <span className="strut" style="height:0.313em;">
              
            </span>
            
            <span className="minner">
              ⋯
            </span>
          </span>
        </span>
      </span>
    </td>
    
    <td>
      <span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <mtext>
                  
                </mtext>
                
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
                    
                    <mo stretchy="false">
                      (
                    </mo>
                    
                    <mi>
                      m
                    </mi>
                    
                    <mi>
                      i
                    </mi>
                    
                    <mi>
                      n
                    </mi>
                    
                    <mo stretchy="false">
                      )
                    </mo>
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
                    
                    <mo stretchy="false">
                      (
                    </mo>
                    
                    <mi>
                      m
                    </mi>
                    
                    <mi>
                      i
                    </mi>
                    
                    <mi>
                      n
                    </mi>
                    
                    <mo stretchy="false">
                      )
                    </mo>
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
                
                <mo>
                  +
                </mo>
                
                <mi>
                  δ
                </mi>
                
                <mo>
                  +
                </mo>
                
                <mn>
                  2
                </mn>
                
                <msub>
                  <mi>
                    t
                  </mi>
                  
                  <mi>
                    j
                  </mi>
                </msub>
              </mrow>
              
              <annotation encoding="application/x-tex">
                \;t_{c-q(min)}+t_{logic(min)}\ge t_{hold}+\delta+2t_j
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:0.9703em;vertical-align:-0.3552em;">
              
            </span>
            
            <span className="mspace" style="margin-right:0.2778em;">
              
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal">
                t
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.3448em;">
                      <span style="top:-2.5198em;margin-left:0em;margin-right:0.05em;">
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
                            
                            <span className="mopen,mtight">
                              (
                            </span>
                            
                            <span className="mord,mathnormal,mtight">
                              min
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
              +
            </span>
            
            <span className="mspace" style="margin-right:0.2222em;">
              
            </span>
          </span>
          
          <span className="base">
            <span className="strut" style="height:0.9912em;vertical-align:-0.3552em;">
              
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal">
                t
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.3448em;">
                      <span style="top:-2.5198em;margin-left:0em;margin-right:0.05em;">
                        <span className="pstrut" style="height:2.7em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mtight">
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
                            
                            <span className="mopen,mtight">
                              (
                            </span>
                            
                            <span className="mord,mathnormal,mtight">
                              min
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
            
            <span className="mspace" style="margin-right:0.2222em;">
              
            </span>
            
            <span className="mbin">
              +
            </span>
            
            <span className="mspace" style="margin-right:0.2222em;">
              
            </span>
          </span>
          
          <span className="base">
            <span className="strut" style="height:0.7778em;vertical-align:-0.0833em;">
              
            </span>
            
            <span className="mord,mathnormal" style="margin-right:0.0379em;">
              δ
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
            <span className="strut" style="height:0.9305em;vertical-align:-0.2861em;">
              
            </span>
            
            <span className="mord">
              2
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal">
                t
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
          </span>
        </span>
      </span>
    </td>
  </tr>
</tbody>
</table>

---

## 容易混淆的点

1. **Setup 看最长路径；hold 看最短路径。**
2. **Setup 违例可尝试降频；hold 违例通常不能靠降频修复。**
3. **正 skew 改善 setup、恶化 hold。**
4. **负 skew 恶化 setup、改善 hold。**
5. **jitter 通常同时压缩 setup 和 hold 裕量。**

---

## 模块四：时钟分配网络（第20–31页）

下面继续讲第 **4 板块：时钟分配网络（Clock Distribution Networks）**，对应第 **20–31 页**。这一部分的主线是：

> 怎样把一个时钟源，可靠、低 skew、低功耗地送到整颗芯片的所有寄存器。

课件从 H-tree、clock grid，一直讲到 Alpha 处理器的真实工程案例。

---

## 第 20 页：Clock Distribution Networks——为什么时钟网络是关键问题

这页给出时钟网络的两个核心目标：

1. **减小 skew 和 jitter**
2. **控制功耗**

课件列出两类主要分配方法：

### 1. Balanced paths：平衡路径

目标是让<mark>

时钟从源头到每个寄存器的路径长度、缓冲级数、RC 延迟尽量一致

</mark>

。

理想情况下：<mark>

因此 skew 接近零。

</mark>



例如：

- H-tree；
- matched RC tree。

### 2. Clock grid：时钟网格

把时钟<mark>

送入大面积、低阻抗的金属网格，再从网格分发到局部模块

</mark>

。

它更强调降低**绝对延迟**和局部电压/时钟波动，而不单纯保证每条路径完全等长。课件指出，grid 通常用于时钟<mark>

网络最后阶段。

</mark>



---

## 第 21 页：Clock Distribution——理想 H-tree 的概念

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter11-Timing-08.webp)

---

## 第 22 页：H-Tree Clock Network——H-tree 与 clock gating

这页首先强调：

> 若所有路径真正完全平衡，clock skew 可以为零。

随后引入一个非常实际的机制：**clock gating（时钟门控）**。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter11-Timing-09.webp)

---

## 第 23-24 页：More realistic H-tree——真实 H-tree 不会那么规整

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 44.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter11-Timing-10.webp" />
      </p>
    </td>
    
    
      <td style="width: 55.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter11-Timing-11.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

---

## 第 25 页：The Grid System——时钟网格结构

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter11-Timing-12.webp)

- **No RC-matching**：它不依赖严格的 RC 路径匹配；
- **Large power**：功耗很大。

---

## 第 26-31 页：EV5/6

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 53.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter11-Timing-13.webp" />
      </p>
    </td>
    
    
      <td style="width: 46.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter11-Timing-14.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

本板块最重要的结论

1. **H-tree 的目标是路径平衡，主要压低相对 skew。**
2. **Clock grid 的目标是低阻抗、低绝对延迟和更高鲁棒性，但功耗大。**
3. **Clock gating 能明显省电，但会增加时钟设计与验证复杂度。**
4. **真实时钟树一定会受到布局、负载、RC、温度和电源噪声影响。**
5. **时钟网络不是辅助电路，而是高性能芯片中最重要、最耗电的系统之一。**

下一板块是第 32 页的“如何处理 skew 和 jitter”，它会把前面所有内容收束成具体的工程策略。

---

## 模块五：工程应对 + 自定时/异步设计（第32–44页）

下面是第 **5 模块：工程处理方法 + 自定时/异步设计**，对应第 **32–44 页**。这一段从“如何改善 skew/jitter”，过渡到“不依赖全局时钟时，系统怎样保证先后顺序和完成判定”。

---

## 第 32 页：Dealing with Clock Skew and Jitter

这一页是前面同步时序内容的工程总结。

1. 平衡时钟路径
2. 让数据与时钟反向布线

- **hold 更容易满足**，race 风险降低；
- **setup 更难满足**，性能可能下降。

1. Clock gating 的代价
2. 屏蔽时钟线
3. Dummy fill
4. 温度和电源

---

## 第 34 页：Self-timed and Asynchronous Design

这一页说明：同步时钟实际上承担两种任务。

### 时钟的两个作用

1. **Completion signal：完成标志**
全局时钟默认告诉系统：“经过一个周期后，组合逻辑应该算完了。”
2. **Ordering：事件顺序约束**
它规定了谁先更新、谁后更新，所有寄存器按照统一节奏工作。

### 异步设计

异步电路没有统一时钟。

换言之，设计者必须确保：前一级的数据真的稳定后，后一级才会响应。

### 自定时设计

自定时设计进一步通过**握手协议**显式规定顺序：

因此它不靠固定周期判断完成，而是靠真实的“请求—确认”关系推进。

---

## 第 35 页：Self-Timed Pipelined Datapath

这一页是自定时流水线的核心结构。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter11-Timing-15.webp)

数据路径仍然是：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

R

</mi>

<mn>

1

</mn>

<mo>

→

</mo>

<mi>

F

</mi>

<mn>

1

</mn>

<mo>

→

</mo>

<mi>

R

</mi>

<mn>

2

</mn>

<mo>

→

</mo>

<mi>

F

</mi>

<mn>

2

</mn>

<mo>

→

</mo>

<mi>

R

</mi>

<mn>

3

</mn>

<mo>

→

</mo>

<mi>

F

</mi>

<mn>

3

</mn>
</mrow>

<annotation encoding="application/x-tex">

R1 \rightarrow F1 \rightarrow R2 \rightarrow F2 \rightarrow R3 \rightarrow F3

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0077em;">

R

</span>

<span className="mord">

1

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

→

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

F

</span>

<span className="mord">

1

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

→

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0077em;">

R

</span>

<span className="mord">

2

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

→

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

F

</span>

<span className="mord">

2

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

→

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0077em;">

R

</span>

<span className="mord">

3

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

→

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

F

</span>

<span className="mord">

3

</span>
</span>
</span>
</span>
</span>

**关键区别：**
同步流水线每一级都等固定时钟；自定时流水线中每一级按自身真实完成时间推进。慢级会自然拖慢后级，形成自动 back-pressure（反压）。

---

## 第 36 页：Completion Signal Generation

自定时系统最大的难题之一是：

> 怎样知道组合逻辑真的完成了？

图中给出一种简单方法：**延迟模块法**

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter11-Timing-16.webp)

---

## 第 37 页：SR Latch Example（自定时系统例子）

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter11-Timing-17.webp)

---

## 第 38 页：Hand-Shaking Protocol——两相握手

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter11-Timing-18.webp)

两相握手中，**上升沿和下降沿都表示一次事件**；不需要每次都回到 `Req=0, Ack=0` 的初始状态。

优点：一次传输所需控制信号翻转少，速度快。
缺点：它是边沿敏感的，任何错误毛刺、漏检测或初始化状态错误，都可能被误判为一次有效传输。

<mark>

一个数据只需要两次信息传递

</mark>



---

## 第 41 页：4-Phase Handshake Protocol

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter11-Timing-19.webp)

四相握手又称 **return-to-zero handshake**：每一次传输后，`Req` 和 `Ack` 都回到初始低电平。

<mark>

一个数据只需要四次信息传递

</mark>



<table>
<thead>
  <tr>
    <th>
      方式
    </th>
    
    <th>
      每轮控制事件
    </th>
    
    <th>
      速度
    </th>
    
    <th>
      可读性与可靠性
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      两相握手
    </td>
    
    <td>
      少
    </td>
    
    <td>
      较快
    </td>
    
    <td>
      边沿敏感，状态管理难
    </td>
  </tr>
  
  <tr>
    <td>
      四相握手
    </td>
    
    <td>
      多
    </td>
    
    <td>
      较慢
    </td>
    
    <td>
      回零明确，不易歧义
    </td>
  </tr>
</tbody>
</table>

---

## 第 43 页：Asynchronous Bus

异步总线没有统一时钟，而是靠握手协议完成读写传输。

---

## 第 44 页：Summary

本章最终可压缩为四条主线：

1. **同步数字电路**：寄存器—组合逻辑—寄存器，靠时钟统一更新。
2. **Clock skew / jitter**：压缩 setup、hold 时序裕量。
3. **Clock distribution**：通过 H-tree、clock grid、buffer、gating 来控制 skew 与功耗。
4. **异步与自定时设计**：不依赖全局时钟，通过完成信号和握手协议保证顺序与正确性。

---

## 这一模块最该记住的内容

- 同步系统：固定周期决定“什么时候算完”。
- 自定时系统：完成信号决定“什么时候算完”。
- 两相握手：快，但边沿敏感。
- 四相握手：慢，但回零明确、不易歧义。
- Muller C 元件：**输入一致才更新；输入不一致就保持原状态。**
- 异步总线避免全局时钟 skew，但用额外控制线和握手开销交换灵活性。

---

## 重点问答：两相握手 vs 四相握手

本质区别在于：**两相握手用“信号翻转”表示一次事件；四相握手用“信号电平 + 回零”表示一次事件。**

<table>
<thead>
  <tr>
    <th>
      对比点
    </th>
    
    <th>
      两相握手（2-phase）
    </th>
    
    <th>
      四相握手（4-phase）
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      事件编码
    </td>
    
    <td>
      边沿/翻转编码
    </td>
    
    <td>
      电平编码
    </td>
  </tr>
  
  <tr>
    <td>
      一次传输控制动作
    </td>
    
    <td>
      <code code="Req">
        Req
      </code>
      
       翻转一次，<code code="Ack">
        Ack
      </code>
      
       翻转一次
    </td>
    
    <td>
      <code code="Req↑ → Ack↑ → Req↓ → Ack↓">
        Req↑ → Ack↑ → Req↓ → Ack↓
      </code>
    </td>
  </tr>
  
  <tr>
    <td>
      是否回到初始状态
    </td>
    
    <td>
      不需要
    </td>
    
    <td>
      必须回到 <code code="Req=0, Ack=0">
        Req=0, Ack=0
      </code>
    </td>
  </tr>
  
  <tr>
    <td>
      每次传输的控制翻转数
    </td>
    
    <td>
      2 次
    </td>
    
    <td>
      4 次
    </td>
  </tr>
  
  <tr>
    <td>
      速度
    </td>
    
    <td>
      更快
    </td>
    
    <td>
      较慢
    </td>
  </tr>
  
  <tr>
    <td>
      控制难度
    </td>
    
    <td>
      更高，必须检测上升沿和下降沿
    </td>
    
    <td>
      更直观，状态明确
    </td>
  </tr>
  
  <tr>
    <td>
      课件总结
    </td>
    
    <td>
      Fast，但 edge-sensitive
    </td>
    
    <td>
      Slower，但 unambiguous
    </td>
  </tr>
</tbody>
</table>

### 两相握手：看“变化”

假设初始为：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

R

</mi>

<mi>

e

</mi>

<mi>

q

</mi>

<mo>

=

</mo>

<mn>

0

</mn>

<mo separator="true">

,

</mo>

<mspace width="1em">



</mspace>

<mi>

A

</mi>

<mi>

c

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

Req=0,\quad Ack=0

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8778em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0077em;">

R

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

q

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

0

</span>

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:1em;">



</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord,mathnormal">

A

</span>

<span className="mord,mathnormal">

c

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
</span>

一次传输：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mo stretchy="false">

(

</mo>

<mn>

0

</mn>

<mo separator="true">

,

</mo>

<mn>

0

</mn>

<mo stretchy="false">

)

</mo>

<mo>

→

</mo>

<mo stretchy="false">

(

</mo>

<mn>

1

</mn>

<mo separator="true">

,

</mo>

<mn>

0

</mn>

<mo stretchy="false">

)

</mo>

<mo>

→

</mo>

<mo stretchy="false">

(

</mo>

<mn>

1

</mn>

<mo separator="true">

,

</mo>

<mn>

1

</mn>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

(0,0)\rightarrow(1,0)\rightarrow(1,1)

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

0

</span>

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord">

0

</span>

<span className="mclose">

)

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

→

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

1

</span>

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord">

0

</span>

<span className="mclose">

)

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

→

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

1

</span>

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



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
</span>

- 发送端让 `Req` 翻转，表示“有一笔新数据”；
- 接收端发现 `Req` 变了，接收数据，再让 `Ack` 翻转；
- 此时交易完成。

下一笔数据不必把信号拉回 0，而是继续翻转：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mo stretchy="false">

(

</mo>

<mn>

1

</mn>

<mo separator="true">

,

</mo>

<mn>

1

</mn>

<mo stretchy="false">

)

</mo>

<mo>

→

</mo>

<mo stretchy="false">

(

</mo>

<mn>

0

</mn>

<mo separator="true">

,

</mo>

<mn>

1

</mn>

<mo stretchy="false">

)

</mo>

<mo>

→

</mo>

<mo stretchy="false">

(

</mo>

<mn>

0

</mn>

<mo separator="true">

,

</mo>

<mn>

0

</mn>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

(1,1)\rightarrow(0,1)\rightarrow(0,0)

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

1

</span>

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord">

1

</span>

<span className="mclose">

)

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

→

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

0

</span>

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord">

1

</span>

<span className="mclose">

)

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

→

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

0

</span>

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord">

0

</span>

<span className="mclose">

)

</span>
</span>
</span>
</span>
</span>

所以两相协议中，**上升沿和下降沿都代表有效事件**。它少了“复位回零”的两个步骤，因此更快；但必须记住上一状态、正确检测每一次翻转，毛刺或初始化错误更危险。课件将它概括为“信号事件数最少，但 edge-sensitive”。

### 四相握手：看“请求是否被拉高”

一次传输固定是：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mo stretchy="false">

(

</mo>

<mn>

0

</mn>

<mo separator="true">

,

</mo>

<mn>

0

</mn>

<mo stretchy="false">

)

</mo>

<mo>

→

</mo>

<mo stretchy="false">

(

</mo>

<mn>

1

</mn>

<mo separator="true">

,

</mo>

<mn>

0

</mn>

<mo stretchy="false">

)

</mo>

<mo>

→

</mo>

<mo stretchy="false">

(

</mo>

<mn>

1

</mn>

<mo separator="true">

,

</mo>

<mn>

1

</mn>

<mo stretchy="false">

)

</mo>

<mo>

→

</mo>

<mo stretchy="false">

(

</mo>

<mn>

0

</mn>

<mo separator="true">

,

</mo>

<mn>

1

</mn>

<mo stretchy="false">

)

</mo>

<mo>

→

</mo>

<mo stretchy="false">

(

</mo>

<mn>

0

</mn>

<mo separator="true">

,

</mo>

<mn>

0

</mn>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

(0,0) \rightarrow(1,0) \rightarrow(1,1) \rightarrow(0,1) \rightarrow(0,0)

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

0

</span>

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord">

0

</span>

<span className="mclose">

)

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

→

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

1

</span>

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord">

0

</span>

<span className="mclose">

)

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

→

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

1

</span>

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord">

1

</span>

<span className="mclose">

)

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

→

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

0

</span>

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord">

1

</span>

<span className="mclose">

)

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

→

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

0

</span>

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord">

0

</span>

<span className="mclose">

)

</span>
</span>
</span>
</span>
</span>

对应：

1. `Req↑`：发送端声明数据有效；
2. `Ack↑`：接收端确认已接收；
3. `Req↓`：发送端撤销请求；
4. `Ack↓`：接收端撤销确认。

只有双方都回到 0，下一笔传输才开始。

因此四相协议有一个很清晰的“空闲态”：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

R

</mi>

<mi>

e

</mi>

<mi>

q

</mi>

<mo>

=

</mo>

<mn>

0

</mn>

<mo separator="true">

,

</mo>

<mspace width="1em">



</mspace>

<mi>

A

</mi>

<mi>

c

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

Req=0,\quad Ack=0

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8778em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0077em;">

R

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

q

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

0

</span>

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:1em;">



</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord,mathnormal">

A

</span>

<span className="mord,mathnormal">

c

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
</span>

它不需要把下降沿也解释成“新数据到来”，所以控制含义更明确、调试更直观，但多了一个回零阶段，吞吐率较低。课件第 42 页用 Muller C 元件实现这种“请求—确认—撤销请求—撤销确认”的顺序约束。

一句话记忆：

> **两相：翻转一次就算一笔交易；四相：拉高表示交易、回零表示收尾。**
