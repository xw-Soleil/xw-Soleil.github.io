# 人工智能前沿

> 人工智能前沿课程笔记，整理自 qsgg、bxgg 手写梳理稿和 B 站课程

- [x] 考试时间6.15

> 前言：这个结合了qsgg的整理和本人和bxgg手写梳理了一遍的原稿，以及一些自己在B站上看过的课程
> 
> 考完了，考试其实感觉考得很简单，基础概念懂了，所有的概念都懂了的话就很好理解了
> 
> 放在这里主要是回看用吧，可能还是自己梳理过的东西捡起来会比较容易一点

## 机器学习与深度学习

### 一、机器学习的概念与分类

1. **概念：**通过对数据的优化学习，建立能够刻画数据中所蕴含语义概念或分布结构等信息的模型
2. **分类：**从数据利用的角度，可分为：

  1. 监督学习
  2. 无监督学习
  3. 半监督学习

#### 监督学习

##### 基本概念

目标是给定带有标签信息数据的训练集 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

D

</mi>

<mo>

=

</mo>

<mo stretchy="false">

{

</mo>

<mo stretchy="false">

(

</mo>

<msub>
<mi>

x

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

y

</mi>

<mi>

i

</mi>
</msub>

<mo stretchy="false">

)

</mo>

<msubsup>
<mo stretchy="false">

}

</mo>

<mrow>
<mi>

i

</mi>

<mo>

=

</mo>

<mn>

1

</mn>
</mrow>

<mi>

n

</mi>
</msubsup>
</mrow>

<annotation encoding="application/x-tex">

D = \{(x_i, y_i)\}_{i = 1}^n

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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.0087em;vertical-align:-0.2587em;">



</span>

<span className="mopen">

{(

</span>

<span className="mord">
<span className="mord,mathnormal">

x

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
<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
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

<span className="mclose">
<span className="mclose">

}

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.6644em;">
<span style="top:-2.4413em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

i

</span>

<span className="mrel,mtight">

=

</span>

<span className="mord,mtight">

1

</span>
</span>
</span>
</span>

<span style="top:-3.063em;margin-right:0.05em;">
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
<span className="vlist" style="height:0.2587em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

,学习一个从输入<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

x

</mi>

<mi>

i

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

x_i

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

x

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

到<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

y

</mi>

<mi>

i

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

y_i

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.625em;vertical-align:-0.1944em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
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

的映射，其中D被称为训练集，n是训练样例的数量。

监督学习算法从假设空间（hypothesisspace）学习得到一个**最优映射函数f（又称决策函数）**，映射函数f将输入数据映射到语义标注空间，实现数据的分类和识别。

##### **有监督学习：训练集、验证集、测试集**

1. 在**训练集**上完成模型参数优化
2. 将训练集中⼀部分数据作为**验证集（validation set）**
3. 最后在**测试集**上进⾏测试，将测试结果作为模型性能最终结果

<mark>

要注意的是，训练集、验证集和测试集所包含数据之间没有任何交叉

</mark>



#### 无监督学习

无监督学习则是直接从无标签数据<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mo stretchy="false">

{

</mo>

<msub>
<mi>

x

</mi>

<mi>

i

</mi>
</msub>

<mo separator="true">

;

</mo>

<mo separator="true">

,

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

<mo separator="true">

,

</mo>

<mi mathvariant="normal">

.

</mi>

<mi mathvariant="normal">

.

</mi>

<mo separator="true">

,

</mo>

<mi>

n

</mi>

<mo stretchy="false">

}

</mo>
</mrow>

<annotation encoding="application/x-tex">

\{x_i;,i=1,..,n\}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mopen">

{

</span>

<span className="mord">
<span className="mord,mathnormal">

x

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

;,

</span>

<span className="mspace" style="margin-right:0.1667em;">



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

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord">

..

</span>

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord,mathnormal">

n

</span>

<span className="mclose">

}

</span>
</span>
</span>
</span>

出发学习映射函数，而半监督学习在学习映射函数过程中使用的一部分数据有标签、一部分数据没有标签。

### 二、**模型评估与参数估计手段：损失函数**

#### **泛化能力（generalization）**

在机器学习中，需要保证模型在训练集上所取得性能与在测试集上所取得性能保持一致，即模型具有泛化能力（generalization）。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AIFrontier/AIFrontier-01.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AIFrontier/AIFrontier-02.webp)

#### **经验风险与期望风险**

##### **经验风险**

映射函数<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

f

</mi>
</mrow>

<annotation encoding="application/x-tex">

f

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1076em;">

f

</span>
</span>
</span>
</span>

在训练集上所产⽣损失⼀般被称为**经验风险** <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi mathvariant="normal">

ℜ

</mi>

<mrow>
<mi>

e

</mi>

<mi>

m

</mi>

<mi>

p

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

ℜ_{emp}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9805em;vertical-align:-0.2861em;">



</span>

<span className="mord">
<span className="mord">

ℜ

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

e

</span>

<span className="mord,mathnormal,mtight">

m

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

(empirical risk)。。

经验风险越小说明模型对训练集数据拟合程度越好。经验风险被定义为：

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

<mi>

n

</mi>
</mfrac>

<munderover>
<mo>

∑

</mo>

<mrow>
<mi>

i

</mi>

<mo>

=

</mo>

<mn>

1

</mn>
</mrow>

<mi>

n

</mi>
</munderover>

<mi>

L

</mi>

<mi>

o

</mi>

<mi>

s

</mi>

<mi>

s

</mi>

<mo stretchy="false">

(

</mo>

<msub>
<mi>

y

</mi>

<mi>

i

</mi>
</msub>

<mo separator="true">

,

</mo>

<mi>

f

</mi>

<mo stretchy="false">

(

</mo>

<msub>
<mi>

x

</mi>

<mi>

i

</mi>
</msub>

<mo stretchy="false">

)

</mo>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

\frac{1}{n}\sum_{i = 1}^n Loss(y_i,f(x_i))

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:2.9291em;vertical-align:-1.2777em;">



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

<span className="mop,op-limits">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:1.6514em;">
<span style="top:-1.8723em;margin-left:0em;">
<span className="pstrut" style="height:3.05em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

i

</span>

<span className="mrel,mtight">

=

</span>

<span className="mord,mtight">

1

</span>
</span>
</span>
</span>

<span style="top:-3.05em;">
<span className="pstrut" style="height:3.05em;">



</span>

<span>
<span className="mop,op-symbol,large-op">

∑

</span>
</span>
</span>

<span style="top:-4.3em;margin-left:0em;">
<span className="pstrut" style="height:3.05em;">



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
<span className="vlist" style="height:1.2777em;">
<span>



</span>
</span>
</span>
</span>
</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord,mathnormal">

L

</span>

<span className="mord,mathnormal">

oss

</span>

<span className="mopen">

(

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
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

<span className="mord,mathnormal" style="margin-right:0.1076em;">

f

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

<span className="mclose">

))

</span>
</span>
</span>
</span>
</span>

##### 期望风险

如果知道某⼀任务包含的所有数据，则可以从所有数据中计算模型产⽣的损失，这⼀误差损失被称为期望风险<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi mathvariant="normal">

ℜ

</mi>
</mrow>

<annotation encoding="application/x-tex">

ℜ

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord">

ℜ

</span>
</span>
</span>
</span>

（expected risk）即真实风险或真实误差。记该任务中所有数据的联合分布为<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

P

</mi>

<mo stretchy="false">

(

</mo>

<mi>

x

</mi>

<mo separator="true">

,

</mo>

<mi>

y

</mi>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

P(x,y)

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="mopen">

(

</span>

<span className="mord,mathnormal">

x

</span>

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

</span>

<span className="mclose">

)

</span>
</span>
</span>
</span>

,期望风险被定义为

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<msub>
<mo>

∫

</mo>

<mrow>
<mi>

x

</mi>

<mo>

×

</mo>

<mi>

y

</mi>
</mrow>
</msub>

<mi>

L

</mi>

<mi>

o

</mi>

<mi>

s

</mi>

<mi>

s

</mi>

<mo stretchy="false">

(

</mo>

<mi>

y

</mi>

<mo separator="true">

,

</mo>

<mi>

f

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

<mo stretchy="false">

)

</mo>

<mi>

P

</mi>

<mo stretchy="false">

(

</mo>

<mi>

x

</mi>

<mo separator="true">

,

</mo>

<mi>

y

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

<mi>

d

</mi>

<mi>

y

</mi>
</mrow>

<annotation encoding="application/x-tex">

\int_{x \times y} Loss(y,f(x))P(x,y)dxdy

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:2.4081em;vertical-align:-1.0481em;">



</span>

<span className="mop">
<span className="mop,op-symbol,large-op" style="margin-right:0.4445em;position:relative;top:-0.0011em;">

∫

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:-0.5036em;">
<span style="top:-1.7881em;margin-left:-0.4445em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

x

</span>

<span className="mbin,mtight">

×

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

y

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:1.0481em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord,mathnormal">

L

</span>

<span className="mord,mathnormal">

oss

</span>

<span className="mopen">

(

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

</span>

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1076em;">

f

</span>

<span className="mopen">

(

</span>

<span className="mord,mathnormal">

x

</span>

<span className="mclose">

))

</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="mopen">

(

</span>

<span className="mord,mathnormal">

x

</span>

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

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

<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

</span>
</span>
</span>
</span>
</span>

> **经验风险** ≈ 训练误差
> 
> **期望风险** ≈ 真实的泛化误差

#### 经验风险最小化

当然，由于无法事先就得到任何任务所对应的所有数据分布（如无法采取世界中所有人脸图像来写信完成人脸识别），使得**计算期望风险这一目标可望不可及**。因此，机器学习中模型优化目标一般为<mark>

**经验风险最小化**

</mark>

（empirical risk minimization），虽然机器学习的目标是追求期望风险最小化，即不断提升模型泛化能力。

#### 期望风险与经验风险的关系

期望风险 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi mathvariant="fraktur">

R

</mi>
</mrow>

<annotation encoding="application/x-tex">

\mathfrak{R}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6914em;">



</span>

<span className="mord,mathfrak">

R

</span>
</span>
</span>
</span>

 与经验风险 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi mathvariant="fraktur">

R

</mi>

<mrow>
<mi>

e

</mi>

<mi>

m

</mi>

<mi>

p

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

\mathfrak{R}_{emp}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9775em;vertical-align:-0.2861em;">



</span>

<span className="mord">
<span className="mord,mathfrak">

R

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

e

</span>

<span className="mord,mathnormal,mtight">

m

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

 之间存在如下关系：

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AIFrontier/AIFrontier-03.webp)

<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

e

</mi>

<mi>

r

</mi>

<mi>

r

</mi>
</mrow>

<annotation encoding="application/x-tex">

err

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.4306em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

er

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>
</span>
</span>
</span>

**为误差项**

其中 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

e

</mi>

<mi>

r

</mi>

<mi>

r

</mi>
</mrow>

<annotation encoding="application/x-tex">

err

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.4306em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

er

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>
</span>
</span>
</span>

 取值与机器学习**模型的复杂程度**和**训练集样本数目**有关。在模型训练过程中，<mark>

如果使用同一批训练数据反复训练，模型会变得越复杂

</mark>

，虽然经验风险 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi mathvariant="fraktur">

R

</mi>

<mrow>
<mi>

e

</mi>

<mi>

m

</mi>

<mi>

p

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

\mathfrak{R}_{emp}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9775em;vertical-align:-0.2861em;">



</span>

<span className="mord">
<span className="mord,mathfrak">

R

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

e

</span>

<span className="mord,mathnormal,mtight">

m

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

 会降低，但是 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

e

</mi>

<mi>

r

</mi>

<mi>

r

</mi>
</mrow>

<annotation encoding="application/x-tex">

err

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.4306em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

er

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>
</span>
</span>
</span>

 取值会越大，导致期望风险 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi mathvariant="fraktur">

R

</mi>
</mrow>

<annotation encoding="application/x-tex">

\mathfrak{R}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6914em;">



</span>

<span className="mord,mathfrak">

R

</span>
</span>
</span>
</span>

 增加。这一现象被称为<mark>

**过学习（过拟合）（overfitting）**

</mark>

。

让我为您详细解释模型泛化能力与经验风险、期望风险之间的关系：

#### 四种典型情况分析

根据表格中的四种情况，我们可以看到：

<table>
<thead>
  <tr>
    <th>
      情况类型
    </th>
    
    <th>
      经验风险
    </th>
    
    <th>
      期望风险
    </th>
    
    <th>
      模型泛化能力
    </th>
    
    <th>
      特点/说明
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      理想状态
    </td>
    
    <td>
      小（训练集上表现好）
    </td>
    
    <td>
      小（所有数据上表现好）
    </td>
    
    <td>
      泛化能力强
    </td>
    
    <td>
      这是我们最希望达到的状态
    </td>
  </tr>
  
  <tr>
    <td>
      过拟合
    </td>
    
    <td>
      小（训练集上表现好）
    </td>
    
    <td>
      大（所有数据上表现不好）
    </td>
    
    <td>
      过学习（模型过于复杂）
    </td>
    
    <td>
      典型的过拟合现象
    </td>
  </tr>
  
  <tr>
    <td>
      欠拟合
    </td>
    
    <td>
      大（训练集上表现不好）
    </td>
    
    <td>
      大（所有数据上表现不好）
    </td>
    
    <td>
      欠学习
    </td>
    
    <td>
      模型过于简单，无法捕捉数据规律
    </td>
  </tr>
  
  <tr>
    <td>
      异常情况
    </td>
    
    <td>
      大（训练集上表现不好）
    </td>
    
    <td>
      小（所有数据上表现好）
    </td>
    
    <td>
      "神仙操作"或"贵族套餐"
    </td>
    
    <td>
      这种情况在实际中很少见，可能表示训练数据有问题
    </td>
  </tr>
</tbody>
</table>

#### 结构风险最小化

为了解决过拟合问题，我们引入**结构风险最小化**：

##### 核心思想

在模型优化中引入恰当先验约束可提升模型性能。通过**正则化**来降低模型复杂度，在最小化经验风险的同时，寻求降低模型复杂度的平衡。

##### 数学表达

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

<mi>

n

</mi>
</mfrac>

<munderover>
<mo>

∑

</mo>

<mrow>
<mi>

i

</mi>

<mo>

=

</mo>

<mn>

1

</mn>
</mrow>

<mi>

n

</mi>
</munderover>

<mi>

L

</mi>

<mi>

o

</mi>

<mi>

s

</mi>

<mi>

s

</mi>

<mo stretchy="false">

(

</mo>

<msub>
<mi>

y

</mi>

<mi>

i

</mi>
</msub>

<mo separator="true">

,

</mo>

<mi>

f

</mi>

<mo stretchy="false">

(

</mo>

<msub>
<mi>

x

</mi>

<mi>

i

</mi>
</msub>

<mo stretchy="false">

)

</mo>

<mo stretchy="false">

)

</mo>

<mo>

+

</mo>

<mi>

λ

</mi>

<mi>

J

</mi>

<mo stretchy="false">

(

</mo>

<mi>

f

</mi>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

\frac{1}{n}\sum_{i=1}^{n} Loss(y_i, f(x_i)) + \lambda J(f)

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:2.9291em;vertical-align:-1.2777em;">



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

<span className="mop,op-limits">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:1.6514em;">
<span style="top:-1.8723em;margin-left:0em;">
<span className="pstrut" style="height:3.05em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

i

</span>

<span className="mrel,mtight">

=

</span>

<span className="mord,mtight">

1

</span>
</span>
</span>
</span>

<span style="top:-3.05em;">
<span className="pstrut" style="height:3.05em;">



</span>

<span>
<span className="mop,op-symbol,large-op">

∑

</span>
</span>
</span>

<span style="top:-4.3em;margin-left:0em;">
<span className="pstrut" style="height:3.05em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
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
<span className="vlist" style="height:1.2777em;">
<span>



</span>
</span>
</span>
</span>
</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord,mathnormal">

L

</span>

<span className="mord,mathnormal">

oss

</span>

<span className="mopen">

(

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
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

<span className="mord,mathnormal" style="margin-right:0.1076em;">

f

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

<span className="mclose">

))

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

<span className="mord,mathnormal">

λ

</span>

<span className="mord,mathnormal" style="margin-right:0.0962em;">

J

</span>

<span className="mopen">

(

</span>

<span className="mord,mathnormal" style="margin-right:0.1076em;">

f

</span>

<span className="mclose">

)

</span>
</span>
</span>
</span>
</span>

其中：

- 第一项：经验风险（拟合训练数据）
- <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

J

</mi>

<mo stretchy="false">

(

</mo>

<mi>

f

</mi>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

J(f)

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0962em;">

J

</span>

<span className="mopen">

(

</span>

<span className="mord,mathnormal" style="margin-right:0.1076em;">

f

</span>

<span className="mclose">

)

</span>
</span>
</span>
</span>

：正则化因子或惩罚项因子（控制模型复杂度）
- <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

λ

</mi>
</mrow>

<annotation encoding="application/x-tex">

\lambda

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
</span>
</span>
</span>

：调整惩罚强度的系数

##### 简单有效原理

**"如无必要，勿增实体"** - 即"简单有效原理"

这个哲学原理在机器学习中的体现就是：

- 在能够解释数据的前提下，选择最简单的模型
- 避免不必要的复杂性
- 通过约束（如约束模型参数稀疏等）使建模过程"能够化繁为简、大巧不工"

##### 实际应用意义——平衡拟合与泛化

结构风险最小化——防止过学习，结构风险最小化，求取二者的平衡

#### **模型度量方法**

以二分类问题（正类、负类）为例：

True、False表示真正结果，Positive、Negative表示预测，因此有TP、FP、FN、TN

<mark>

**但注意TP、FP、FN、TN，不代表TF就是真实类别，而PN确实是代表预测对错**

</mark>



<mark>

**T、F代表的是最后预测的对错**

</mark>



<mark>

**使用TP FN负负得正的出来的才是真实类别**

</mark>



> **”纵坐标“是预测，”横坐标“是真实值**

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AIFrontier/AIFrontier-04.webp)

##### 准确率**(accuracy)**

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

A

</mi>

<mi>

C

</mi>

<mi>

C

</mi>

<mo>

=

</mo>

<mfrac>
<mrow>
<mi>

T

</mi>

<mi>

P

</mi>

<mo>

+

</mo>

<mi>

T

</mi>

<mi>

N

</mi>
</mrow>

<mrow>
<mi>

P

</mi>

<mo>

+

</mo>

<mi>

N

</mi>
</mrow>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

ACC = \frac{TP + TN}{P + N}

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

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

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
<span className="strut" style="height:2.1297em;vertical-align:-0.7693em;">



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
<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

N

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
<span className="mord,mathnormal" style="margin-right:0.1389em;">

T

</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

T

</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

N

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.7693em;">
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

这个事情很显然，判断正确的几率

##### 错误率**（error rate）**

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

e

</mi>

<mi>

r

</mi>

<mi>

r

</mi>

<mi>

o

</mi>

<mi>

r

</mi>

<mi>

R

</mi>

<mi>

a

</mi>

<mi>

t

</mi>

<mi>

e

</mi>

<mo>

=

</mo>

<mfrac>
<mrow>
<mi>

F

</mi>

<mi>

P

</mi>

<mo>

+

</mo>

<mi>

F

</mi>

<mi>

N

</mi>
</mrow>

<mrow>
<mi>

P

</mi>

<mo>

+

</mo>

<mi>

N

</mi>
</mrow>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

errorRate = \frac{FP + FN}{P + N}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

er

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

or

</span>

<span className="mord,mathnormal" style="margin-right:0.0077em;">

R

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal">

e

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
<span className="strut" style="height:2.1297em;vertical-align:-0.7693em;">



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
<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

N

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
<span className="mord,mathnormal" style="margin-right:0.1389em;">

F

</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

F

</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

N

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.7693em;">
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

这个事情也很显然，<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mn>

1

</mn>

<mo>

−

</mo>

<mi>

A

</mi>

<mi>

C

</mi>

<mi>

C

</mi>

<mo>

=

</mo>

<mi>

e

</mi>

<mi>

r

</mi>

<mi>

r

</mi>

<mi>

o

</mi>

<mi>

r

</mi>

<mi>

R

</mi>

<mi>

a

</mi>

<mi>

t

</mi>

<mi>

e

</mi>
</mrow>

<annotation encoding="application/x-tex">

1-ACC = errorRate

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.7278em;vertical-align:-0.0833em;">



</span>

<span className="mord">

1

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
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal">

A

</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

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
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

er

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

or

</span>

<span className="mord,mathnormal" style="margin-right:0.0077em;">

R

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal">

e

</span>
</span>
</span>
</span>



##### **精确率——“真”对了多少（precision）**

> 精确率**也叫查准率，**即<mark>
> 
> 预测结果为正确里面有多少个实际也是正确的
> 
> </mark>
> 
> ，即**真对了多少**

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

p

</mi>

<mi>

r

</mi>

<mi>

e

</mi>

<mi>

c

</mi>

<mi>

i

</mi>

<mi>

s

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

<mo>

=

</mo>

<mfrac>
<mrow>
<mi>

T

</mi>

<mi>

P

</mi>
</mrow>

<mrow>
<mi>

T

</mi>

<mi>

P

</mi>

<mo>

+

</mo>

<mi>

F

</mi>

<mi>

P

</mi>
</mrow>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

precision = \frac{TP}{TP + FP}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.854em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal">

p

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal">

ec

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

s

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal">

o

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
<span className="strut" style="height:2.1297em;vertical-align:-0.7693em;">



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
<span className="mord,mathnormal" style="margin-right:0.1389em;">

T

</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

F

</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

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
<span className="mord,mathnormal" style="margin-right:0.1389em;">

T

</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.7693em;">
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

##### **召回率——“找”对了多少（Recall）**

> 也叫**查全率**，表示**所有正例样本中被模型预测为正例的比例**。

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

c

</mi>

<mi>

a

</mi>

<mi>

l

</mi>

<mi>

l

</mi>

<mo>

=

</mo>

<mfrac>
<mrow>
<mi>

T

</mi>

<mi>

P

</mi>
</mrow>

<mrow>
<mi>

T

</mi>

<mi>

P

</mi>

<mo>

+

</mo>

<mi>

F

</mi>

<mi>

N

</mi>
</mrow>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

Recall = \frac{TP}{TP+FN}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0077em;">

R

</span>

<span className="mord,mathnormal">

ec

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

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
<span className="strut" style="height:2.1297em;vertical-align:-0.7693em;">



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
<span className="mord,mathnormal" style="margin-right:0.1389em;">

T

</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

F

</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

N

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
<span className="mord,mathnormal" style="margin-right:0.1389em;">

T

</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.7693em;">
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

在实际应用中，精确率和召回率之间是相互矛盾的，比如可以将所有样本分类为正例使得召回率为100%而精确率极低。因此为了综合考虑精确率和召回率，可采用`F1-Score` 这一综合分类率：

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AIFrontier/AIFrontier-05.webp)

> **即调和平均数**

### 二、回归分析

#### 线性回归

##### 一维线性回归

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AIFrontier/AIFrontier-06.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AIFrontier/AIFrontier-07.webp)

##### 高维线性回归

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AIFrontier/AIFrontier-08.webp)

###### 矩阵形式

为了方便，我们使用矩阵来表示所有的训练数据和数据标签。

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

X

</mi>

<mo>

=

</mo>

<mo stretchy="false">

[

</mo>

<msub>
<mi>

x

</mi>

<mn>

1

</mn>
</msub>

<mo separator="true">

,

</mo>

<mi mathvariant="normal">

.

</mi>

<mi mathvariant="normal">

.

</mi>

<mi mathvariant="normal">

.

</mi>

<mo separator="true">

,

</mo>

<msub>
<mi>

x

</mi>

<mi>

m

</mi>
</msub>

<mo stretchy="false">

]

</mo>

<mo separator="true">

,

</mo>

<mspace width="1em">



</mspace>

<mi mathvariant="bold">

y

</mi>

<mo>

=

</mo>

<mo stretchy="false">

[

</mo>

<msub>
<mi>

y

</mi>

<mn>

1

</mn>
</msub>

<mo separator="true">

,

</mo>

<mi mathvariant="normal">

.

</mi>

<mi mathvariant="normal">

.

</mi>

<mi mathvariant="normal">

.

</mi>

<mo separator="true">

,

</mo>

<msub>
<mi>

y

</mi>

<mi>

m

</mi>
</msub>

<mo stretchy="false">

]

</mo>
</mrow>

<annotation encoding="application/x-tex">

X = [x_1, ..., x_m], \quad \mathbf{y} = [y_1, ..., y_m]

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

[

</span>

<span className="mord">
<span className="mord,mathnormal">

x

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

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord">

...

</span>

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



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

<span className="mclose">

]

</span>

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:1em;">



</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord,mathbf" style="margin-right:0.016em;">

y

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

[

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

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

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord">

...

</span>

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

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

<span className="mclose">

]

</span>
</span>
</span>
</span>
</span>

其中每一个数据<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

x

</mi>

<mi>

i

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

x_i

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

x

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

会扩展一个维度，其值为1，对应参数<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

a

</mi>

<mn>

0

</mn>
</msub>
</mrow>

<annotation encoding="application/x-tex">

a_0

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

。均方误差函数可以表示为：

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

<mi>

m

</mi>
</msub>

<mo stretchy="false">

(

</mo>

<mi mathvariant="bold">

a

</mi>

<mo stretchy="false">

)

</mo>

<mo>

=

</mo>

<mo stretchy="false">

(

</mo>

<mi mathvariant="bold">

y

</mi>

<mo>

−

</mo>

<msup>
<mi>

X

</mi>

<mi>

T

</mi>
</msup>

<mi mathvariant="bold">

a

</mi>

<msup>
<mo stretchy="false">

)

</mo>

<mi>

T

</mi>
</msup>

<mo stretchy="false">

(

</mo>

<mi mathvariant="bold">

y

</mi>

<mo>

−

</mo>

<msup>
<mi>

X

</mi>

<mi>

T

</mi>
</msup>

<mi mathvariant="bold">

a

</mi>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

J_m(\mathbf{a}) = (\mathbf{y} - X^T\mathbf{a})^T(\mathbf{y} - X^T\mathbf{a})

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0962em;">

J

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0962em;margin-right:0.05em;">
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

<span className="mopen">

(

</span>

<span className="mord,mathbf">

a

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

<span className="mopen">

(

</span>

<span className="mord,mathbf" style="margin-right:0.016em;">

y

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
<span className="strut" style="height:1.1413em;vertical-align:-0.25em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0785em;">

X

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8913em;">
<span style="top:-3.113em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
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

<span className="mord,mathbf">

a

</span>

<span className="mclose">
<span className="mclose">

)

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8913em;">
<span style="top:-3.113em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
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

<span className="mopen">

(

</span>

<span className="mord,mathbf" style="margin-right:0.016em;">

y

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
<span className="strut" style="height:1.1413em;vertical-align:-0.25em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0785em;">

X

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8913em;">
<span style="top:-3.113em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
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

<span className="mord,mathbf">

a

</span>

<span className="mclose">

)

</span>
</span>
</span>
</span>
</span>

均方误差函数<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

J

</mi>

<mi>

n

</mi>
</msub>

<mo stretchy="false">

(

</mo>

<mi mathvariant="bold">

a

</mi>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

J_n(\mathbf{a})

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0962em;">

J

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0962em;margin-right:0.05em;">
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

<span className="mopen">

(

</span>

<span className="mord,mathbf">

a

</span>

<span className="mclose">

)

</span>
</span>
</span>
</span>

对所有参数<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi mathvariant="bold">

a

</mi>
</mrow>

<annotation encoding="application/x-tex">

\mathbf{a}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.4444em;">



</span>

<span className="mord,mathbf">

a

</span>
</span>
</span>
</span>

求导可得：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi mathvariant="normal">

∇

</mi>

<mi>

J

</mi>

<mo stretchy="false">

(

</mo>

<mi mathvariant="bold">

a

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

<mn>

2

</mn>

<mi>

X

</mi>

<mo stretchy="false">

(

</mo>

<mi mathvariant="bold">

y

</mi>

<mo>

−

</mo>

<msup>
<mi>

X

</mi>

<mi>

T

</mi>
</msup>

<mi mathvariant="bold">

a

</mi>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

\nabla J(\mathbf{a}) = -2X(\mathbf{y} - X^T\mathbf{a})

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord">

∇

</span>

<span className="mord,mathnormal" style="margin-right:0.0962em;">

J

</span>

<span className="mopen">

(

</span>

<span className="mord,mathbf">

a

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

<span className="mord">

−

</span>

<span className="mord">

2

</span>

<span className="mord,mathnormal" style="margin-right:0.0785em;">

X

</span>

<span className="mopen">

(

</span>

<span className="mord,mathbf" style="margin-right:0.016em;">

y

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
<span className="strut" style="height:1.1413em;vertical-align:-0.25em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0785em;">

X

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8913em;">
<span style="top:-3.113em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
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

<span className="mord,mathbf">

a

</span>

<span className="mclose">

)

</span>
</span>
</span>
</span>
</span>

因为均方误差函数<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

J

</mi>

<mi>

n

</mi>
</msub>

<mo stretchy="false">

(

</mo>

<mi mathvariant="bold">

a

</mi>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

J_n(\mathbf{a})

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0962em;">

J

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0962em;margin-right:0.05em;">
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

<span className="mopen">

(

</span>

<span className="mord,mathbf">

a

</span>

<span className="mclose">

)

</span>
</span>
</span>
</span>

是一个二次的凸函数，所以函数只存在一个极小值点，也同样是最小值点，

所以令<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi mathvariant="normal">

∇

</mi>

<mi>

J

</mi>

<mo stretchy="false">

(

</mo>

<mi mathvariant="bold">

a

</mi>

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

\nabla J(\mathbf{a}) = 0

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord">

∇

</span>

<span className="mord,mathnormal" style="margin-right:0.0962em;">

J

</span>

<span className="mopen">

(

</span>

<span className="mord,mathbf">

a

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

可得：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

X

</mi>

<msup>
<mi>

X

</mi>

<mi>

T

</mi>
</msup>

<mi mathvariant="bold">

a

</mi>

<mo>

=

</mo>

<mi>

X

</mi>

<mi mathvariant="bold">

y

</mi>
</mrow>

<annotation encoding="application/x-tex">

XX^T\mathbf{a} = X\mathbf{y}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8913em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0785em;">

X

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0785em;">

X

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8913em;">
<span style="top:-3.113em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
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

<span className="mord,mathbf">

a

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

<span className="mord,mathnormal" style="margin-right:0.0785em;">

X

</span>

<span className="mord,mathbf" style="margin-right:0.016em;">

y

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
<mi mathvariant="bold">

a

</mi>

<mo>

=

</mo>

<mo stretchy="false">

(

</mo>

<mi>

X

</mi>

<msup>
<mi>

X

</mi>

<mi>

T

</mi>
</msup>

<msup>
<mo stretchy="false">

)

</mo>

<mrow>
<mo>

−

</mo>

<mn>

1

</mn>
</mrow>
</msup>

<mi>

X

</mi>

<mi mathvariant="bold">

y

</mi>
</mrow>

<annotation encoding="application/x-tex">

\mathbf{a} = (XX^T)^{-1}X\mathbf{y}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.4444em;">



</span>

<span className="mord,mathbf">

a

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
<span className="strut" style="height:1.1413em;vertical-align:-0.25em;">



</span>

<span className="mopen">

(

</span>

<span className="mord,mathnormal" style="margin-right:0.0785em;">

X

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0785em;">

X

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8913em;">
<span style="top:-3.113em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
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

<span className="mord,mathnormal" style="margin-right:0.0785em;">

X

</span>

<span className="mord,mathbf" style="margin-right:0.016em;">

y

</span>
</span>
</span>
</span>
</span>

##### 矩阵求梯度详解

###### 基本概念

矩阵求梯度是指对标量函数相对于向量参数求偏导数，结果是一个与参数向量同维度的梯度向量。

###### 常用矩阵求导公式

在推导前，我们需要掌握几个重要的矩阵求导公式：

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AIFrontier/AIFrontier-09.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AIFrontier/AIFrontier-10.webp)

###### 具体推导过程

让我们详细推导均方误差函数的梯度：

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

<mi>

m

</mi>
</msub>

<mo stretchy="false">

(

</mo>

<mi mathvariant="bold">

a

</mi>

<mo stretchy="false">

)

</mo>

<mo>

=

</mo>

<mo stretchy="false">

(

</mo>

<mi mathvariant="bold">

y

</mi>

<mo>

−

</mo>

<msup>
<mi>

X

</mi>

<mi>

T

</mi>
</msup>

<mi mathvariant="bold">

a

</mi>

<msup>
<mo stretchy="false">

)

</mo>

<mi>

T

</mi>
</msup>

<mo stretchy="false">

(

</mo>

<mi mathvariant="bold">

y

</mi>

<mo>

−

</mo>

<msup>
<mi>

X

</mi>

<mi>

T

</mi>
</msup>

<mi mathvariant="bold">

a

</mi>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

J_m(\mathbf{a}) = (\mathbf{y} - X^T\mathbf{a})^T(\mathbf{y} - X^T\mathbf{a})

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0962em;">

J

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0962em;margin-right:0.05em;">
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

<span className="mopen">

(

</span>

<span className="mord,mathbf">

a

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

<span className="mopen">

(

</span>

<span className="mord,mathbf" style="margin-right:0.016em;">

y

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
<span className="strut" style="height:1.1413em;vertical-align:-0.25em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0785em;">

X

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8913em;">
<span style="top:-3.113em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
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

<span className="mord,mathbf">

a

</span>

<span className="mclose">
<span className="mclose">

)

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8913em;">
<span style="top:-3.113em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
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

<span className="mopen">

(

</span>

<span className="mord,mathbf" style="margin-right:0.016em;">

y

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
<span className="strut" style="height:1.1413em;vertical-align:-0.25em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0785em;">

X

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8913em;">
<span style="top:-3.113em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
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

<span className="mord,mathbf">

a

</span>

<span className="mclose">

)

</span>
</span>
</span>
</span>
</span>

###### 第一步：展开二次型

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

<mi>

m

</mi>
</msub>

<mo stretchy="false">

(

</mo>

<mi mathvariant="bold">

a

</mi>

<mo stretchy="false">

)

</mo>

<mo>

=

</mo>

<mo stretchy="false">

(

</mo>

<mi mathvariant="bold">

y

</mi>

<mo>

−

</mo>

<msup>
<mi>

X

</mi>

<mi>

T

</mi>
</msup>

<mi mathvariant="bold">

a

</mi>

<msup>
<mo stretchy="false">

)

</mo>

<mi>

T

</mi>
</msup>

<mo stretchy="false">

(

</mo>

<mi mathvariant="bold">

y

</mi>

<mo>

−

</mo>

<msup>
<mi>

X

</mi>

<mi>

T

</mi>
</msup>

<mi mathvariant="bold">

a

</mi>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

J_m(\mathbf{a}) = (\mathbf{y} - X^T\mathbf{a})^T(\mathbf{y} - X^T\mathbf{a})

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0962em;">

J

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0962em;margin-right:0.05em;">
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

<span className="mopen">

(

</span>

<span className="mord,mathbf">

a

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

<span className="mopen">

(

</span>

<span className="mord,mathbf" style="margin-right:0.016em;">

y

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
<span className="strut" style="height:1.1413em;vertical-align:-0.25em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0785em;">

X

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8913em;">
<span style="top:-3.113em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
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

<span className="mord,mathbf">

a

</span>

<span className="mclose">
<span className="mclose">

)

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8913em;">
<span style="top:-3.113em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
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

<span className="mopen">

(

</span>

<span className="mord,mathbf" style="margin-right:0.016em;">

y

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
<span className="strut" style="height:1.1413em;vertical-align:-0.25em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0785em;">

X

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8913em;">
<span style="top:-3.113em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
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

<span className="mord,mathbf">

a

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

<msup>
<mi mathvariant="bold">

y

</mi>

<mi>

T

</mi>
</msup>

<mi mathvariant="bold">

y

</mi>

<mo>

−

</mo>

<msup>
<mi mathvariant="bold">

y

</mi>

<mi>

T

</mi>
</msup>

<msup>
<mi>

X

</mi>

<mi>

T

</mi>
</msup>

<mi mathvariant="bold">

a

</mi>

<mo>

−

</mo>

<msup>
<mi mathvariant="bold">

a

</mi>

<mi>

T

</mi>
</msup>

<mi>

X

</mi>

<mi mathvariant="bold">

y

</mi>

<mo>

+

</mo>

<msup>
<mi mathvariant="bold">

a

</mi>

<mi>

T

</mi>
</msup>

<mi>

X

</mi>

<msup>
<mi>

X

</mi>

<mi>

T

</mi>
</msup>

<mi mathvariant="bold">

a

</mi>
</mrow>

<annotation encoding="application/x-tex">

= \mathbf{y}^T\mathbf{y} - \mathbf{y}^T X^T\mathbf{a} - \mathbf{a}^T X \mathbf{y} + \mathbf{a}^T X X^T \mathbf{a}

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
<span className="strut" style="height:1.0858em;vertical-align:-0.1944em;">



</span>

<span className="mord">
<span className="mord,mathbf" style="margin-right:0.016em;">

y

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8913em;">
<span style="top:-3.113em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
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

<span className="mord,mathbf" style="margin-right:0.016em;">

y

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
<span className="strut" style="height:1.0858em;vertical-align:-0.1944em;">



</span>

<span className="mord">
<span className="mord,mathbf" style="margin-right:0.016em;">

y

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8913em;">
<span style="top:-3.113em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
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

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0785em;">

X

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8913em;">
<span style="top:-3.113em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
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

<span className="mord,mathbf">

a

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
<span className="strut" style="height:1.0858em;vertical-align:-0.1944em;">



</span>

<span className="mord">
<span className="mord,mathbf">

a

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8913em;">
<span style="top:-3.113em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
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

<span className="mord,mathnormal" style="margin-right:0.0785em;">

X

</span>

<span className="mord,mathbf" style="margin-right:0.016em;">

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
<span className="strut" style="height:0.8913em;">



</span>

<span className="mord">
<span className="mord,mathbf">

a

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8913em;">
<span style="top:-3.113em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
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

<span className="mord,mathnormal" style="margin-right:0.0785em;">

X

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0785em;">

X

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8913em;">
<span style="top:-3.113em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
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

<span className="mord,mathbf">

a

</span>
</span>
</span>
</span>
</span>

###### 第二步：利用对称性简化

注意到 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msup>
<mi mathvariant="bold">

y

</mi>

<mi>

T

</mi>
</msup>

<msup>
<mi>

X

</mi>

<mi>

T

</mi>
</msup>

<mi mathvariant="bold">

a

</mi>
</mrow>

<annotation encoding="application/x-tex">

\mathbf{y}^T X^T\mathbf{a}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.0358em;vertical-align:-0.1944em;">



</span>

<span className="mord">
<span className="mord,mathbf" style="margin-right:0.016em;">

y

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8413em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
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

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0785em;">

X

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8413em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
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

<span className="mord,mathbf">

a

</span>
</span>
</span>
</span>

 是标量，所以： <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msup>
<mi mathvariant="bold">

y

</mi>

<mi>

T

</mi>
</msup>

<msup>
<mi>

X

</mi>

<mi>

T

</mi>
</msup>

<mi mathvariant="bold">

a

</mi>

<mo>

=

</mo>

<mo stretchy="false">

(

</mo>

<msup>
<mi mathvariant="bold">

y

</mi>

<mi>

T

</mi>
</msup>

<msup>
<mi>

X

</mi>

<mi>

T

</mi>
</msup>

<mi mathvariant="bold">

a

</mi>

<msup>
<mo stretchy="false">

)

</mo>

<mi>

T

</mi>
</msup>

<mo>

=

</mo>

<msup>
<mi mathvariant="bold">

a

</mi>

<mi>

T

</mi>
</msup>

<mi>

X

</mi>

<mi mathvariant="bold">

y

</mi>
</mrow>

<annotation encoding="application/x-tex">

\mathbf{y}^T X^T\mathbf{a} = (\mathbf{y}^T X^T\mathbf{a})^T = \mathbf{a}^T X \mathbf{y}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.0358em;vertical-align:-0.1944em;">



</span>

<span className="mord">
<span className="mord,mathbf" style="margin-right:0.016em;">

y

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8413em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
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

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0785em;">

X

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8413em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
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

<span className="mord,mathbf">

a

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
<span className="strut" style="height:1.0913em;vertical-align:-0.25em;">



</span>

<span className="mopen">

(

</span>

<span className="mord">
<span className="mord,mathbf" style="margin-right:0.016em;">

y

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8413em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
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

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0785em;">

X

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8413em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
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

<span className="mord,mathbf">

a

</span>

<span className="mclose">
<span className="mclose">

)

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8413em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.0358em;vertical-align:-0.1944em;">



</span>

<span className="mord">
<span className="mord,mathbf">

a

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8413em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
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

<span className="mord,mathnormal" style="margin-right:0.0785em;">

X

</span>

<span className="mord,mathbf" style="margin-right:0.016em;">

y

</span>
</span>
</span>
</span>



因此： <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

J

</mi>

<mi>

m

</mi>
</msub>

<mo stretchy="false">

(

</mo>

<mi mathvariant="bold">

a

</mi>

<mo stretchy="false">

)

</mo>

<mo>

=

</mo>

<msup>
<mi mathvariant="bold">

y

</mi>

<mi>

T

</mi>
</msup>

<mi mathvariant="bold">

y

</mi>

<mo>

−

</mo>

<mn>

2

</mn>

<msup>
<mi mathvariant="bold">

a

</mi>

<mi>

T

</mi>
</msup>

<mi>

X

</mi>

<mi mathvariant="bold">

y

</mi>

<mo>

+

</mo>

<msup>
<mi mathvariant="bold">

a

</mi>

<mi>

T

</mi>
</msup>

<mi>

X

</mi>

<msup>
<mi>

X

</mi>

<mi>

T

</mi>
</msup>

<mi mathvariant="bold">

a

</mi>
</mrow>

<annotation encoding="application/x-tex">

J_m(\mathbf{a}) = \mathbf{y}^T\mathbf{y} - 2\mathbf{a}^T X \mathbf{y} + \mathbf{a}^T X X^T \mathbf{a}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0962em;">

J

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0962em;margin-right:0.05em;">
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

<span className="mopen">

(

</span>

<span className="mord,mathbf">

a

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
<span className="strut" style="height:1.0358em;vertical-align:-0.1944em;">



</span>

<span className="mord">
<span className="mord,mathbf" style="margin-right:0.016em;">

y

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8413em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
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

<span className="mord,mathbf" style="margin-right:0.016em;">

y

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
<span className="strut" style="height:1.0358em;vertical-align:-0.1944em;">



</span>

<span className="mord">

2

</span>

<span className="mord">
<span className="mord,mathbf">

a

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8413em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
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

<span className="mord,mathnormal" style="margin-right:0.0785em;">

X

</span>

<span className="mord,mathbf" style="margin-right:0.016em;">

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
<span className="strut" style="height:0.8413em;">



</span>

<span className="mord">
<span className="mord,mathbf">

a

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8413em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
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

<span className="mord,mathnormal" style="margin-right:0.0785em;">

X

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0785em;">

X

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8413em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
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

<span className="mord,mathbf">

a

</span>
</span>
</span>
</span>



###### 第三步：对每一项求梯度

1. **第一项**：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msup>
<mi mathvariant="bold">

y

</mi>

<mi>

T

</mi>
</msup>

<mi mathvariant="bold">

y

</mi>
</mrow>

<annotation encoding="application/x-tex">

\mathbf{y}^T\mathbf{y}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.0358em;vertical-align:-0.1944em;">



</span>

<span className="mord">
<span className="mord,mathbf" style="margin-right:0.016em;">

y

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8413em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
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

<span className="mord,mathbf" style="margin-right:0.016em;">

y

</span>
</span>
</span>
</span>

 是常数 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mfrac>
<mi mathvariant="normal">

∂

</mi>

<mrow>
<mi mathvariant="normal">

∂

</mi>

<mi mathvariant="bold">

a

</mi>
</mrow>
</mfrac>

<mo stretchy="false">

(

</mo>

<msup>
<mi mathvariant="bold">

y

</mi>

<mi>

T

</mi>
</msup>

<mi mathvariant="bold">

y

</mi>

<mo stretchy="false">

)

</mo>

<mo>

=

</mo>

<mn mathvariant="bold">

0

</mn>
</mrow>

<annotation encoding="application/x-tex">

\frac{\partial}{\partial \mathbf{a}}(\mathbf{y}^T\mathbf{y}) = \mathbf{0}

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
<span className="mord,mtight" style="margin-right:0.0556em;">

∂

</span>

<span className="mord,mathbf,mtight">

a

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
<span className="mord,mtight" style="margin-right:0.0556em;">

∂

</span>
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

<span className="mopen">

(

</span>

<span className="mord">
<span className="mord,mathbf" style="margin-right:0.016em;">

y

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8413em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
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

<span className="mord,mathbf" style="margin-right:0.016em;">

y

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

<span className="mord,mathbf">

0

</span>
</span>
</span>
</span>
2. **第二项**：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mo>

−

</mo>

<mn>

2

</mn>

<msup>
<mi mathvariant="bold">

a

</mi>

<mi>

T

</mi>
</msup>

<mi>

X

</mi>

<mi mathvariant="bold">

y

</mi>
</mrow>

<annotation encoding="application/x-tex">

-2\mathbf{a}^T X \mathbf{y}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.0358em;vertical-align:-0.1944em;">



</span>

<span className="mord">

−

</span>

<span className="mord">

2

</span>

<span className="mord">
<span className="mord,mathbf">

a

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8413em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
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

<span className="mord,mathnormal" style="margin-right:0.0785em;">

X

</span>

<span className="mord,mathbf" style="margin-right:0.016em;">

y

</span>
</span>
</span>
</span>

 是线性项 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mfrac>
<mi mathvariant="normal">

∂

</mi>

<mrow>
<mi mathvariant="normal">

∂

</mi>

<mi mathvariant="bold">

a

</mi>
</mrow>
</mfrac>

<mo stretchy="false">

(

</mo>

<mo>

−

</mo>

<mn>

2

</mn>

<msup>
<mi mathvariant="bold">

a

</mi>

<mi>

T

</mi>
</msup>

<mi>

X

</mi>

<mi mathvariant="bold">

y

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

<mn>

2

</mn>

<mi>

X

</mi>

<mi mathvariant="bold">

y

</mi>
</mrow>

<annotation encoding="application/x-tex">

\frac{\partial}{\partial \mathbf{a}}(-2\mathbf{a}^T X \mathbf{y}) = -2X\mathbf{y}

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
<span className="mord,mtight" style="margin-right:0.0556em;">

∂

</span>

<span className="mord,mathbf,mtight">

a

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
<span className="mord,mtight" style="margin-right:0.0556em;">

∂

</span>
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

<span className="mopen">

(

</span>

<span className="mord">

−

</span>

<span className="mord">

2

</span>

<span className="mord">
<span className="mord,mathbf">

a

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8413em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
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

<span className="mord,mathnormal" style="margin-right:0.0785em;">

X

</span>

<span className="mord,mathbf" style="margin-right:0.016em;">

y

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
<span className="strut" style="height:0.8778em;vertical-align:-0.1944em;">



</span>

<span className="mord">

−

</span>

<span className="mord">

2

</span>

<span className="mord,mathnormal" style="margin-right:0.0785em;">

X

</span>

<span className="mord,mathbf" style="margin-right:0.016em;">

y

</span>
</span>
</span>
</span>
3. **第三项**：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msup>
<mi mathvariant="bold">

a

</mi>

<mi>

T

</mi>
</msup>

<mi>

X

</mi>

<msup>
<mi>

X

</mi>

<mi>

T

</mi>
</msup>

<mi mathvariant="bold">

a

</mi>
</mrow>

<annotation encoding="application/x-tex">

\mathbf{a}^T X X^T \mathbf{a}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8413em;">



</span>

<span className="mord">
<span className="mord,mathbf">

a

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8413em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
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

<span className="mord,mathnormal" style="margin-right:0.0785em;">

X

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0785em;">

X

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8413em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
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

<span className="mord,mathbf">

a

</span>
</span>
</span>
</span>

 是二次项
4. 由于 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

X

</mi>

<msup>
<mi>

X

</mi>

<mi>

T

</mi>
</msup>
</mrow>

<annotation encoding="application/x-tex">

XX^T

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8413em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0785em;">

X

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0785em;">

X

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8413em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
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

 是对称矩阵，根据公式： <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mfrac>
<mi mathvariant="normal">

∂

</mi>

<mrow>
<mi mathvariant="normal">

∂

</mi>

<mi mathvariant="bold">

a

</mi>
</mrow>
</mfrac>

<mo stretchy="false">

(

</mo>

<msup>
<mi mathvariant="bold">

a

</mi>

<mi>

T

</mi>
</msup>

<mi>

X

</mi>

<msup>
<mi>

X

</mi>

<mi>

T

</mi>
</msup>

<mi mathvariant="bold">

a

</mi>

<mo stretchy="false">

)

</mo>

<mo>

=

</mo>

<mn>

2

</mn>

<mi>

X

</mi>

<msup>
<mi>

X

</mi>

<mi>

T

</mi>
</msup>

<mi mathvariant="bold">

a

</mi>
</mrow>

<annotation encoding="application/x-tex">

\frac{\partial}{\partial \mathbf{a}}(\mathbf{a}^T X X^T \mathbf{a}) = 2XX^T\mathbf{a}

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
<span className="mord,mtight" style="margin-right:0.0556em;">

∂

</span>

<span className="mord,mathbf,mtight">

a

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
<span className="mord,mtight" style="margin-right:0.0556em;">

∂

</span>
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

<span className="mopen">

(

</span>

<span className="mord">
<span className="mord,mathbf">

a

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8413em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
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

<span className="mord,mathnormal" style="margin-right:0.0785em;">

X

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0785em;">

X

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8413em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
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

<span className="mord,mathbf">

a

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
<span className="strut" style="height:0.8413em;">



</span>

<span className="mord">

2

</span>

<span className="mord,mathnormal" style="margin-right:0.0785em;">

X

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0785em;">

X

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8413em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
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

<span className="mord,mathbf">

a

</span>
</span>
</span>
</span>

###### 第四步：合并结果

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi mathvariant="normal">

∇

</mi>

<msub>
<mi>

J

</mi>

<mi>

m

</mi>
</msub>

<mo stretchy="false">

(

</mo>

<mi mathvariant="bold">

a

</mi>

<mo stretchy="false">

)

</mo>

<mo>

=

</mo>

<mn mathvariant="bold">

0

</mn>

<mo>

−

</mo>

<mn>

2

</mn>

<mi>

X

</mi>

<mi mathvariant="bold">

y

</mi>

<mo>

+

</mo>

<mn>

2

</mn>

<mi>

X

</mi>

<msup>
<mi>

X

</mi>

<mi>

T

</mi>
</msup>

<mi mathvariant="bold">

a

</mi>
</mrow>

<annotation encoding="application/x-tex">

\nabla J_m(\mathbf{a}) = \mathbf{0} - 2X\mathbf{y} + 2XX^T\mathbf{a}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord">

∇

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0962em;">

J

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0962em;margin-right:0.05em;">
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

<span className="mopen">

(

</span>

<span className="mord,mathbf">

a

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
<span className="strut" style="height:0.7278em;vertical-align:-0.0833em;">



</span>

<span className="mord,mathbf">

0

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
<span className="strut" style="height:0.8778em;vertical-align:-0.1944em;">



</span>

<span className="mord">

2

</span>

<span className="mord,mathnormal" style="margin-right:0.0785em;">

X

</span>

<span className="mord,mathbf" style="margin-right:0.016em;">

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
<span className="strut" style="height:0.8913em;">



</span>

<span className="mord">

2

</span>

<span className="mord,mathnormal" style="margin-right:0.0785em;">

X

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0785em;">

X

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8913em;">
<span style="top:-3.113em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
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

<span className="mord,mathbf">

a

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

<mi>

X

</mi>

<msup>
<mi>

X

</mi>

<mi>

T

</mi>
</msup>

<mi mathvariant="bold">

a

</mi>

<mo>

−

</mo>

<mn>

2

</mn>

<mi>

X

</mi>

<mi mathvariant="bold">

y

</mi>
</mrow>

<annotation encoding="application/x-tex">

= 2XX^T\mathbf{a} - 2X\mathbf{y}

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
<span className="strut" style="height:0.9747em;vertical-align:-0.0833em;">



</span>

<span className="mord">

2

</span>

<span className="mord,mathnormal" style="margin-right:0.0785em;">

X

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0785em;">

X

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8913em;">
<span style="top:-3.113em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
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

<span className="mord,mathbf">

a

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
<span className="strut" style="height:0.8778em;vertical-align:-0.1944em;">



</span>

<span className="mord">

2

</span>

<span className="mord,mathnormal" style="margin-right:0.0785em;">

X

</span>

<span className="mord,mathbf" style="margin-right:0.016em;">

y

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

<mi>

X

</mi>

<mo stretchy="false">

(

</mo>

<msup>
<mi>

X

</mi>

<mi>

T

</mi>
</msup>

<mi mathvariant="bold">

a

</mi>

<mo>

−

</mo>

<mi mathvariant="bold">

y

</mi>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

= 2X(X^T\mathbf{a} - \mathbf{y})

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
<span className="strut" style="height:1.1413em;vertical-align:-0.25em;">



</span>

<span className="mord">

2

</span>

<span className="mord,mathnormal" style="margin-right:0.0785em;">

X

</span>

<span className="mopen">

(

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0785em;">

X

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8913em;">
<span style="top:-3.113em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
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

<span className="mord,mathbf">

a

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

<span className="mord,mathbf" style="margin-right:0.016em;">

y

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

<mo>

−

</mo>

<mn>

2

</mn>

<mi>

X

</mi>

<mo stretchy="false">

(

</mo>

<mi mathvariant="bold">

y

</mi>

<mo>

−

</mo>

<msup>
<mi>

X

</mi>

<mi>

T

</mi>
</msup>

<mi mathvariant="bold">

a

</mi>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

= -2X(\mathbf{y} - X^T\mathbf{a})

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

−

</span>

<span className="mord">

2

</span>

<span className="mord,mathnormal" style="margin-right:0.0785em;">

X

</span>

<span className="mopen">

(

</span>

<span className="mord,mathbf" style="margin-right:0.016em;">

y

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
<span className="strut" style="height:1.1413em;vertical-align:-0.25em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0785em;">

X

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8913em;">
<span style="top:-3.113em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
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

<span className="mord,mathbf">

a

</span>

<span className="mclose">

)

</span>
</span>
</span>
</span>
</span>

###### 关键理解点

1. 维度匹配

- <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi mathvariant="bold">

a

</mi>
</mrow>

<annotation encoding="application/x-tex">

\mathbf{a}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.4444em;">



</span>

<span className="mord,mathbf">

a

</span>
</span>
</span>
</span>

 是 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

n

</mi>

<mo>

×

</mo>

<mn>

1

</mn>
</mrow>

<annotation encoding="application/x-tex">

n \times 1

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

×

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

 向量
- <span className="katex">
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

 是 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

n

</mi>

<mo>

×

</mo>

<mi>

m

</mi>
</mrow>

<annotation encoding="application/x-tex">

n \times m

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

×

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.4306em;">



</span>

<span className="mord,mathnormal">

m

</span>
</span>
</span>
</span>

 矩阵
- <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi mathvariant="bold">

y

</mi>
</mrow>

<annotation encoding="application/x-tex">

\mathbf{y}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6389em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathbf" style="margin-right:0.016em;">

y

</span>
</span>
</span>
</span>

 是 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

m

</mi>

<mo>

×

</mo>

<mn>

1

</mn>
</mrow>

<annotation encoding="application/x-tex">

m \times 1

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6667em;vertical-align:-0.0833em;">



</span>

<span className="mord,mathnormal">

m

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
<span className="strut" style="height:0.6444em;">



</span>

<span className="mord">

1

</span>
</span>
</span>
</span>

 向量
- 梯度 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi mathvariant="normal">

∇

</mi>

<msub>
<mi>

J

</mi>

<mi>

m

</mi>
</msub>

<mo stretchy="false">

(

</mo>

<mi mathvariant="bold">

a

</mi>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

\nabla J_m(\mathbf{a})

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord">

∇

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0962em;">

J

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0962em;margin-right:0.05em;">
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

<span className="mopen">

(

</span>

<span className="mord,mathbf">

a

</span>

<span className="mclose">

)

</span>
</span>
</span>
</span>

 也必须是 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

n

</mi>

<mo>

×

</mo>

<mn>

1

</mn>
</mrow>

<annotation encoding="application/x-tex">

n \times 1

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

×

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

 向量

1. 链式法则

对于复合函数 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

f

</mi>

<mo stretchy="false">

(

</mo>

<mi>

g

</mi>

<mo stretchy="false">

(

</mo>

<mi mathvariant="bold">

x

</mi>

<mo stretchy="false">

)

</mo>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

f(g(\mathbf{x}))

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1076em;">

f

</span>

<span className="mopen">

(

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

g

</span>

<span className="mopen">

(

</span>

<span className="mord,mathbf">

x

</span>

<span className="mclose">

))

</span>
</span>
</span>
</span>

，有： <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mfrac>
<mrow>
<mi mathvariant="normal">

∂

</mi>

<mi>

f

</mi>
</mrow>

<mrow>
<mi mathvariant="normal">

∂

</mi>

<mi mathvariant="bold">

x

</mi>
</mrow>
</mfrac>

<mo>

=

</mo>

<mfrac>
<mrow>
<mi mathvariant="normal">

∂

</mi>

<mi>

f

</mi>
</mrow>

<mrow>
<mi mathvariant="normal">

∂

</mi>

<mi>

g

</mi>
</mrow>
</mfrac>

<mo>

⋅

</mo>

<mfrac>
<mrow>
<mi mathvariant="normal">

∂

</mi>

<mi>

g

</mi>
</mrow>

<mrow>
<mi mathvariant="normal">

∂

</mi>

<mi mathvariant="bold">

x

</mi>
</mrow>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

\frac{\partial f}{\partial \mathbf{x}} = \frac{\partial f}{\partial g} \cdot \frac{\partial g}{\partial \mathbf{x}}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.2772em;vertical-align:-0.345em;">



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
<span className="mord,mtight" style="margin-right:0.0556em;">

∂

</span>

<span className="mord,mathbf,mtight">

x

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
<span className="mord,mtight" style="margin-right:0.0556em;">

∂

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

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.4133em;vertical-align:-0.4811em;">



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
<span className="mord,mtight" style="margin-right:0.0556em;">

∂

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

g

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
<span className="mord,mtight" style="margin-right:0.0556em;">

∂

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

⋅

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.2772em;vertical-align:-0.345em;">



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
<span className="mord,mtight" style="margin-right:0.0556em;">

∂

</span>

<span className="mord,mathbf,mtight">

x

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
<span className="mord,mtight" style="margin-right:0.0556em;">

∂

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



1. 矩阵求导的本质

矩阵求导实际上是对每个分量分别求偏导数： <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mfrac>
<mrow>
<mi mathvariant="normal">

∂

</mi>

<mi>

f

</mi>
</mrow>

<mrow>
<mi mathvariant="normal">

∂

</mi>

<mi mathvariant="bold">

x

</mi>
</mrow>
</mfrac>

<mo>

=

</mo>

<mrow>
<mo fence="true">

[

</mo>

<mtable rowspacing="0.16em" columnalign="center" columnspacing="1em">
<mtr>
<mtd>
<mstyle scriptlevel="0" displaystyle="false">
<mrow>
<mfrac>
<mrow>
<mi mathvariant="normal">

∂

</mi>

<mi>

f

</mi>
</mrow>

<mrow>
<mi mathvariant="normal">

∂

</mi>

<msub>
<mi>

x

</mi>

<mn>

1

</mn>
</msub>
</mrow>
</mfrac>

<mtext>



</mtext>

<mfrac>
<mrow>
<mi mathvariant="normal">

∂

</mi>

<mi>

f

</mi>
</mrow>

<mrow>
<mi mathvariant="normal">

∂

</mi>

<msub>
<mi>

x

</mi>

<mn>

2

</mn>
</msub>
</mrow>
</mfrac>

<mtext>



</mtext>

<mo>

…

</mo>

<mtext>



</mtext>

<mfrac>
<mrow>
<mi mathvariant="normal">

∂

</mi>

<mi>

f

</mi>
</mrow>

<mrow>
<mi mathvariant="normal">

∂

</mi>

<msub>
<mi>

x

</mi>

<mi>

n

</mi>
</msub>
</mrow>
</mfrac>
</mrow>
</mstyle>
</mtd>
</mtr>
</mtable>

<mo fence="true">

]

</mo>
</mrow>
</mrow>

<annotation encoding="application/x-tex">

\frac{\partial f}{\partial \mathbf{x}} = \begin{bmatrix} \frac{\partial f}{\partial x_1} \ \frac{\partial f}{\partial x_2} \ \dots \ \frac{\partial f}{\partial x_n} \end{bmatrix}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.2772em;vertical-align:-0.345em;">



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
<span className="mord,mtight" style="margin-right:0.0556em;">

∂

</span>

<span className="mord,mathbf,mtight">

x

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
<span className="mord,mtight" style="margin-right:0.0556em;">

∂

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

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.8em;vertical-align:-0.65em;">



</span>

<span className="minner">
<span className="mopen,delimcenter" style="top:0em;">
<span className="delimsizing,size2">

[

</span>
</span>

<span className="mord">
<span className="mtable">
<span className="col-align-c">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.9387em;">
<span style="top:-3.0064em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
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
<span className="mord,mtight" style="margin-right:0.0556em;">

∂

</span>

<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

x

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3173em;">
<span style="top:-2.357em;margin-left:0em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
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
<span className="mord,mtight" style="margin-right:0.0556em;">

∂

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

<span className="mspace">



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
<span className="mord,mtight" style="margin-right:0.0556em;">

∂

</span>

<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

x

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3173em;">
<span style="top:-2.357em;margin-left:0em;margin-right:0.0714em;">
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
<span className="mord,mtight" style="margin-right:0.0556em;">

∂

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

<span className="mspace">



</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="minner">

…

</span>

<span className="mspace">



</span>

<span className="mspace" style="margin-right:0.1667em;">



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
<span className="mord,mtight" style="margin-right:0.0556em;">

∂

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
<span className="mord,mtight" style="margin-right:0.0556em;">

∂

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
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.4387em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>

<span className="mclose,delimcenter" style="top:0em;">
<span className="delimsizing,size2">

]

</span>
</span>
</span>
</span>
</span>
</span>



###### 实用技巧

1. **先展开再求导**：复杂的矩阵表达式可以先展开成标量形式
2. **利用对称性**：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msup>
<mi mathvariant="bold">

a

</mi>

<mi>

T

</mi>
</msup>

<mi mathvariant="bold">

b

</mi>

<mo>

=

</mo>

<msup>
<mi mathvariant="bold">

b

</mi>

<mi>

T

</mi>
</msup>

<mi mathvariant="bold">

a

</mi>
</mrow>

<annotation encoding="application/x-tex">

\mathbf{a}^T\mathbf{b} = \mathbf{b}^T\mathbf{a}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8413em;">



</span>

<span className="mord">
<span className="mord,mathbf">

a

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8413em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
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

<span className="mord,mathbf">

b

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
<span className="strut" style="height:0.8413em;">



</span>

<span className="mord">
<span className="mord,mathbf">

b

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8413em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
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

<span className="mord,mathbf">

a

</span>
</span>
</span>
</span>

（当结果是标量时）
3. **分项处理**：把复杂函数分解为简单项的和
4. **检查维度**：每一步都要确保维度匹配

这样，通过系统的推导，我们就得到了均方误差函数的梯度表达式！

### 三、前馈神经网络与参数优化

##### 1、人工神经网络概述

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AIFrontier/AIFrontier-11.webp)

###### 感知机

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AIFrontier/AIFrontier-12.webp)

###### 前馈神经网络

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AIFrontier/AIFrontier-13.webp)

##### 2、激活函数

> 激活函数必须是【单调递增的】

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AIFrontier/AIFrontier-14.webp)

### 四、卷积神经网络

> 一个很形象的可视化视频，从2min29s开始看就好了

#### 一些杂项

> 八股的概念

图像卷积操作符合“**视觉系统信息分层处理**”这一机制，即视觉感知是由低层细胞到高层细胞对原始输入信息不断抽象完成，**更高层细胞拥有更高级的感受野**，并且对一些**偏移、旋转**等具有一定的**不变性**

#### 基本概念

##### 感受野

**感受野**是卷积神经网络**每一层输出的特征图**（feature map）上的**像素点**在**输入图像**上**映射的区域大小，**<mark>

**是特征图上一个点对应输入图像上的区域**

</mark>



<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mo stretchy="false">

[

</mo>

<mi>

h

</mi>

<mo separator="true">

,

</mo>

<mi>

w

</mi>

<mo stretchy="false">

]

</mo>
</mrow>

<annotation encoding="application/x-tex">

[h,w]

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

<span className="mord,mathnormal">

h

</span>

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0269em;">

w

</span>

<span className="mclose">

]

</span>
</span>
</span>
</span>

:<mark>

感受野

</mark>

大小/<mark>

卷积核

</mark>

大小->对性能的影响

<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mo stretchy="false">

(

</mo>

<mi>

i

</mi>

<mo separator="true">

,

</mo>

<mi>

j

</mi>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

(i,j)

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

<span className="mord,mathnormal">

i

</span>

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0572em;">

j

</span>

<span className="mclose">

)

</span>
</span>
</span>
</span>

：方向和距离->位移

##### 下采样

图像卷积计算即对图像进行了**下采样 (down sampling)**操作

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AIFrontier/AIFrontier-15.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AIFrontier/AIFrontier-16.webp)

###### 下采样的减抽象

> 感觉现场推就可以了

假设被卷积图像大小为<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

W

</mi>

<mo>

×

</mo>

<mi>

W

</mi>
</mrow>

<annotation encoding="application/x-tex">

W×W

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

W

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

W

</span>
</span>
</span>
</span>

，卷积核大小为<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

F

</mi>

<mo>

×

</mo>

<mi>

F

</mi>
</mrow>

<annotation encoding="application/x-tex">

F×F

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

F

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
</span>
</span>
</span>

，上下左右四个边缘填充像素行列数为<span className="katex">
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

<mo stretchy="false">

⌊

</mo>

<mi>

F

</mi>

<mi mathvariant="normal">

/

</mi>

<mn>

2

</mn>

<mo stretchy="false">

⌋

</mo>
</mrow>

<annotation encoding="application/x-tex">

P = ⌊F/2⌋

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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mopen">

⌊

</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

F

</span>

<span className="mord">

/2

</span>

<span className="mclose">

⌋

</span>
</span>
</span>
</span>

，步长为<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

S

</mi>
</mrow>

<annotation encoding="application/x-tex">

S

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0576em;">

S

</span>
</span>
</span>
</span>

，则被卷积结果的分辨率是 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mfrac>
<mrow>
<mi>

W

</mi>

<mo>

−

</mo>

<mi>

F

</mi>

<mo>

+

</mo>

<mn>

2

</mn>

<mi>

P

</mi>
</mrow>

<mi>

S

</mi>
</mfrac>

<mo>

+

</mo>

<mn>

1

</mn>
</mrow>

<annotation encoding="application/x-tex">

\frac{W-F+2P}{S} + 1

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
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
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

S

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
<span className="mord,mathnormal,mtight" style="margin-right:0.1389em;">

W

</span>

<span className="mbin,mtight">

−

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.1389em;">

F

</span>

<span className="mbin,mtight">

+

</span>

<span className="mord,mtight">

2

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

+

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

。

#### Padding（填充）

> 填充可以补0或者复制

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AIFrontier/AIFrontier-17.webp)

#### Stride（步长）

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AIFrontier/AIFrontier-18.webp)

#### Dilation（膨胀）

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AIFrontier/AIFrontier-19.webp)

#### Pooling（池化）

池化操作是卷积神经网络中常用的**下采样方法**，主要有最大池化（Max Pooling）、平均池化（Average Pooling）、 k-max 池化（K-Max Pooling）等

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AIFrontier/AIFrontier-20.webp)

#### 词嵌入（Word embedding）

**词嵌入要达到的目的——**<mark>

**经过word embedding，词意相近的两个词在特征空间会相隔比较近**

</mark>



![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AIFrontier/AIFrontier-21.webp)

通过将One-Hot编码表示的词与嵌入矩阵相乘就可以将高维稀疏的矩阵嵌入到一个低维稠密的矩阵中

### 五、循环神经网络（Recurrent Neural Network, RNN）

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AIFrontier/AIFrontier-22.webp)

#### 1、基本原理

循环神经网络的结构图如上所示。由"循环"两字可知，循环神经网络在处理数据过程中构成了一个循环体。对于一个序列数据，在每一时刻t，循环神经网络单元会**读取当前输入数据**<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

x

</mi>

<mi>

t

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

x_t

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

x

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
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

和**前一时刻**输入数据<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

x

</mi>

<mrow>
<mi>

t

</mi>

<mo>

−

</mo>

<mn>

1

</mn>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

x_{t-1}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6389em;vertical-align:-0.2083em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

x

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
<span className="mord,mathnormal,mtight">

t

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

所<mark>

对应的隐式编码结果

</mark>

<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

h

</mi>

<mrow>
<mi>

t

</mi>

<mo>

−

</mo>

<mn>

1

</mn>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

h_{t-1}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9028em;vertical-align:-0.2083em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

h

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
<span className="mord,mathnormal,mtight">

t

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

<mark>

一起生成

</mark>

<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

t

</mi>
</mrow>

<annotation encoding="application/x-tex">

t

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6151em;">



</span>

<span className="mord,mathnormal">

t

</span>
</span>
</span>
</span>

<mark>

时刻的隐式编码结果

</mark>

<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

h

</mi>

<mi>

t

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

h_t

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

h

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
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

。接着将<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

h

</mi>

<mi>

t

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

h_t

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

h

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
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

后传，去参与生成<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

t

</mi>

<mo>

+

</mo>

<mn>

1

</mn>
</mrow>

<annotation encoding="application/x-tex">

t+1

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6984em;vertical-align:-0.0833em;">



</span>

<span className="mord,mathnormal">

t

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
<span className="strut" style="height:0.6444em;">



</span>

<span className="mord">

1

</span>
</span>
</span>
</span>

时刻输入数据<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

x

</mi>

<mrow>
<mi>

t

</mi>

<mo>

+

</mo>

<mn>

1

</mn>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

x_{t+1}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6389em;vertical-align:-0.2083em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

x

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
<span className="mord,mathnormal,mtight">

t

</span>

<span className="mbin,mtight">

+

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

的隐式编码<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

h

</mi>

<mrow>
<mi>

t

</mi>

<mo>

+

</mo>

<mn>

1

</mn>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

h_{t+1}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9028em;vertical-align:-0.2083em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

h

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
<span className="mord,mathnormal,mtight">

t

</span>

<span className="mbin,mtight">

+

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

。如此循环处理，直至该序列数据被处理完毕。

<mark>

当输入序列过长时，循环神经网络也容易出现梯度消失(gradient vanishing)或者梯度爆炸（gradient exploding）的问题

</mark>



#### 2、序列误差

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AIFrontier/AIFrontier-23.webp)

#### 3、参数更新的问题

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AIFrontier/AIFrontier-24.webp)

#### 4、长短期记忆网络（LSTM）

> <mark>
> 
> **速记**
> 
> </mark>

长短期记忆网络引入了*记忆元*（memory cell），或简称为*单元*（cell）。当前时间步的输入和前一个时间步的隐状态 作为数据送入长短期记忆网络的门中， 如图所示。 它们由三个具有sigmoid激活函数的全连接层处理， 以计算输入门、遗忘门和输出门的值。 因此，这三个门的值都在(0,1)的范围内。

##### 输入门、遗忘门和输出门

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AIFrontier/AIFrontier-25.webp)

假设有h个隐藏单元，批量大小为n，输入数为d。因此，输入为<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

X

</mi>

<mi>

t

</mi>
</msub>

<mo>

∈

</mo>

<msup>
<mi mathvariant="normal">

R

</mi>

<mrow>
<mi>

n

</mi>

<mo>

×

</mo>

<mi>

d

</mi>
</mrow>
</msup>
</mrow>

<annotation encoding="application/x-tex">

X_t ∈ ℝ^{n×d}

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

X

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:-0.0785em;margin-right:0.05em;">
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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

∈

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8491em;">



</span>

<span className="mord">
<span className="mord,amsrm">

R

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8491em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

n

</span>

<span className="mbin,mtight">

×

</span>

<span className="mord,mathnormal,mtight">

d

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

*，前一时间步的隐状态为*<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

H

</mi>

<mrow>
<mi>

t

</mi>

<mo>

−

</mo>

<mn>

1

</mn>
</mrow>
</msub>

<mo>

∈

</mo>

<msup>
<mi mathvariant="normal">

R

</mi>

<mrow>
<mi>

n

</mi>

<mo>

×

</mo>

<mi>

h

</mi>
</mrow>
</msup>
</mrow>

<annotation encoding="application/x-tex">

H_{t-1} ∈ ℝ^{n×h}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8917em;vertical-align:-0.2083em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0813em;">

H

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0813em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

t

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

∈

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8491em;">



</span>

<span className="mord">
<span className="mord,amsrm">

R

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8491em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

n

</span>

<span className="mbin,mtight">

×

</span>

<span className="mord,mathnormal,mtight">

h

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

。相应地，时间步t的门被定义如下：输入门是<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

I

</mi>

<mi>

t

</mi>
</msub>

<mo>

∈

</mo>

<msup>
<mi mathvariant="normal">

R

</mi>

<mrow>
<mi>

n

</mi>

<mo>

×

</mo>

<mi>

h

</mi>
</mrow>
</msup>
</mrow>

<annotation encoding="application/x-tex">

I_t ∈ ℝ^{n×h}

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
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:-0.0785em;margin-right:0.05em;">
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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

∈

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8491em;">



</span>

<span className="mord">
<span className="mord,amsrm">

R

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8491em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

n

</span>

<span className="mbin,mtight">

×

</span>

<span className="mord,mathnormal,mtight">

h

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

，遗忘门是<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

F

</mi>

<mi>

t

</mi>
</msub>

<mo>

∈

</mo>

<msup>
<mi mathvariant="normal">

R

</mi>

<mrow>
<mi>

n

</mi>

<mo>

×

</mo>

<mi>

h

</mi>
</mrow>
</msup>
</mrow>

<annotation encoding="application/x-tex">

F_t ∈ ℝ^{n×h}

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

F

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:-0.1389em;margin-right:0.05em;">
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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

∈

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8491em;">



</span>

<span className="mord">
<span className="mord,amsrm">

R

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8491em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

n

</span>

<span className="mbin,mtight">

×

</span>

<span className="mord,mathnormal,mtight">

h

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

，输出门是<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

O

</mi>

<mi>

t

</mi>
</msub>

<mo>

∈

</mo>

<msup>
<mi mathvariant="normal">

R

</mi>

<mrow>
<mi>

n

</mi>

<mo>

×

</mo>

<mi>

h

</mi>
</mrow>
</msup>
</mrow>

<annotation encoding="application/x-tex">

O_t ∈ ℝ^{n×h}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

O

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:-0.0278em;margin-right:0.05em;">
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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

∈

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8491em;">



</span>

<span className="mord">
<span className="mord,amsrm">

R

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8491em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

n

</span>

<span className="mbin,mtight">

×

</span>

<span className="mord,mathnormal,mtight">

h

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

。它们的计算方法如下：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<msub>
<mi mathvariant="bold">

I

</mi>

<mi>

t

</mi>
</msub>

<mo>

=

</mo>

<mi>

σ

</mi>

<mo stretchy="false">

(

</mo>

<msub>
<mi mathvariant="bold">

X

</mi>

<mi>

t

</mi>
</msub>

<msub>
<mi mathvariant="bold">

W

</mi>

<mrow>
<mi>

x

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
<mi mathvariant="bold">

H

</mi>

<mrow>
<mi>

t

</mi>

<mo>

−

</mo>

<mn>

1

</mn>
</mrow>
</msub>

<msub>
<mi mathvariant="bold">

W

</mi>

<mrow>
<mi>

h

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
<mi mathvariant="bold">

b

</mi>

<mi>

i

</mi>
</msub>

<mo stretchy="false">

)

</mo>

<mo separator="true">

,

</mo>
</mrow>

<annotation encoding="application/x-tex">

\mathbf{I}_t = \sigma(\mathbf{X}_t \mathbf{W}_{xi} + \mathbf{H}_{t-1} \mathbf{W}_{hi} + \mathbf{b}_i),

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

I

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
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

σ

</span>

<span className="mopen">

(

</span>

<span className="mord">
<span className="mord,mathbf">

X

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
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

<span className="mord">
<span className="mord,mathbf" style="margin-right:0.016em;">

W

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.016em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

x

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
<span className="strut" style="height:0.8944em;vertical-align:-0.2083em;">



</span>

<span className="mord">
<span className="mord,mathbf">

H

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
<span className="mord,mathnormal,mtight">

t

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
<span className="mord,mathbf" style="margin-right:0.016em;">

W

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.016em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

hi

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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
<span className="mord,mathbf">

b

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

<span className="mclose">

)

</span>

<span className="mpunct">

,

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
<mi mathvariant="bold">

F

</mi>

<mi>

t

</mi>
</msub>

<mo>

=

</mo>

<mi>

σ

</mi>

<mo stretchy="false">

(

</mo>

<msub>
<mi mathvariant="bold">

X

</mi>

<mi>

t

</mi>
</msub>

<msub>
<mi mathvariant="bold">

W

</mi>

<mrow>
<mi>

x

</mi>

<mi>

f

</mi>
</mrow>
</msub>

<mo>

+

</mo>

<msub>
<mi mathvariant="bold">

H

</mi>

<mrow>
<mi>

t

</mi>

<mo>

−

</mo>

<mn>

1

</mn>
</mrow>
</msub>

<msub>
<mi mathvariant="bold">

W

</mi>

<mrow>
<mi>

h

</mi>

<mi>

f

</mi>
</mrow>
</msub>

<mo>

+

</mo>

<msub>
<mi mathvariant="bold">

b

</mi>

<mi>

f

</mi>
</msub>

<mo stretchy="false">

)

</mo>

<mo separator="true">

,

</mo>
</mrow>

<annotation encoding="application/x-tex">

\mathbf{F}_t = \sigma(\mathbf{X}_t \mathbf{W}_{xf} + \mathbf{H}_{t-1} \mathbf{W}_{hf} + \mathbf{b}_f),

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

F

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.0361em;vertical-align:-0.2861em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

σ

</span>

<span className="mopen">

(

</span>

<span className="mord">
<span className="mord,mathbf">

X

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
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

<span className="mord">
<span className="mord,mathbf" style="margin-right:0.016em;">

W

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.016em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

x

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.9722em;vertical-align:-0.2861em;">



</span>

<span className="mord">
<span className="mord,mathbf">

H

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
<span className="mord,mathnormal,mtight">

t

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
<span className="mord,mathbf" style="margin-right:0.016em;">

W

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.016em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

h

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.0361em;vertical-align:-0.2861em;">



</span>

<span className="mord">
<span className="mord,mathbf">

b

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
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

<span className="mclose">

)

</span>

<span className="mpunct">

,

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
<mi mathvariant="bold">

O

</mi>

<mi>

t

</mi>
</msub>

<mo>

=

</mo>

<mi>

σ

</mi>

<mo stretchy="false">

(

</mo>

<msub>
<mi mathvariant="bold">

X

</mi>

<mi>

t

</mi>
</msub>

<msub>
<mi mathvariant="bold">

W

</mi>

<mrow>
<mi>

x

</mi>

<mi>

o

</mi>
</mrow>
</msub>

<mo>

+

</mo>

<msub>
<mi mathvariant="bold">

H

</mi>

<mrow>
<mi>

t

</mi>

<mo>

−

</mo>

<mn>

1

</mn>
</mrow>
</msub>

<msub>
<mi mathvariant="bold">

W

</mi>

<mrow>
<mi>

h

</mi>

<mi>

o

</mi>
</mrow>
</msub>

<mo>

+

</mo>

<msub>
<mi mathvariant="bold">

b

</mi>

<mi>

o

</mi>
</msub>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

\mathbf{O}_t = \sigma(\mathbf{X}_t \mathbf{W}_{xo} + \mathbf{H}_{t-1} \mathbf{W}_{ho} + \mathbf{b}_o)

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

O

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
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

σ

</span>

<span className="mopen">

(

</span>

<span className="mord">
<span className="mord,mathbf">

X

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
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

<span className="mord">
<span className="mord,mathbf" style="margin-right:0.016em;">

W

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.016em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

x

</span>

<span className="mord,mathnormal,mtight">

o

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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
<span className="strut" style="height:0.8944em;vertical-align:-0.2083em;">



</span>

<span className="mord">
<span className="mord,mathbf">

H

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
<span className="mord,mathnormal,mtight">

t

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
<span className="mord,mathbf" style="margin-right:0.016em;">

W

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.016em;margin-right:0.05em;">
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
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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
<span className="mord,mathbf">

b

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

o

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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

其中<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi mathvariant="bold">

W

</mi>

<mrow>
<mi>

x

</mi>

<mi>

i

</mi>
</mrow>
</msub>

<mo separator="true">

,

</mo>

<msub>
<mi mathvariant="bold">

W

</mi>

<mrow>
<mi>

x

</mi>

<mi>

f

</mi>
</mrow>
</msub>

<mo separator="true">

,

</mo>

<msub>
<mi mathvariant="bold">

W

</mi>

<mrow>
<mi>

x

</mi>

<mi>

o

</mi>
</mrow>
</msub>

<mo>

∈

</mo>

<msup>
<mi mathvariant="double-struck">

R

</mi>

<mrow>
<mi>

d

</mi>

<mo>

×

</mo>

<mi>

h

</mi>
</mrow>
</msup>

<mtext>

和

</mtext>

<msub>
<mi mathvariant="bold">

W

</mi>

<mrow>
<mi>

h

</mi>

<mi>

i

</mi>
</mrow>
</msub>

<mo separator="true">

,

</mo>

<msub>
<mi mathvariant="bold">

W

</mi>

<mrow>
<mi>

h

</mi>

<mi>

f

</mi>
</mrow>
</msub>

<mo separator="true">

,

</mo>

<msub>
<mi mathvariant="bold">

W

</mi>

<mrow>
<mi>

h

</mi>

<mi>

o

</mi>
</mrow>
</msub>

<mo>

∈

</mo>

<msup>
<mi mathvariant="double-struck">

R

</mi>

<mrow>
<mi>

h

</mi>

<mo>

×

</mo>

<mi>

h

</mi>
</mrow>
</msup>
</mrow>

<annotation encoding="application/x-tex">

\mathbf{W}_{xi}, \mathbf{W}_{xf}, \mathbf{W}_{xo} \in \mathbb{R}^{d \times h} \text{ 和 } \mathbf{W}_{hi}, \mathbf{W}_{hf}, \mathbf{W}_{ho} \in \mathbb{R}^{h \times h}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9722em;vertical-align:-0.2861em;">



</span>

<span className="mord">
<span className="mord,mathbf" style="margin-right:0.016em;">

W

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.016em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

x

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
<span className="mord,mathbf" style="margin-right:0.016em;">

W

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.016em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

x

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

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord">
<span className="mord,mathbf" style="margin-right:0.016em;">

W

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.016em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

x

</span>

<span className="mord,mathnormal,mtight">

o

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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

∈

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.1352em;vertical-align:-0.2861em;">



</span>

<span className="mord">
<span className="mord,mathbb">

R

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8491em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

d

</span>

<span className="mbin,mtight">

×

</span>

<span className="mord,mathnormal,mtight">

h

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

<span className="mord,text">
<span className="mord">



</span>

<span className="mord,cjk_fallback">

和

</span>

<span className="mord">



</span>
</span>

<span className="mord">
<span className="mord,mathbf" style="margin-right:0.016em;">

W

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.016em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

hi

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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
<span className="mord,mathbf" style="margin-right:0.016em;">

W

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.016em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

h

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

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord">
<span className="mord,mathbf" style="margin-right:0.016em;">

W

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.016em;margin-right:0.05em;">
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
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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

∈

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8491em;">



</span>

<span className="mord">
<span className="mord,mathbb">

R

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8491em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

h

</span>

<span className="mbin,mtight">

×

</span>

<span className="mord,mathnormal,mtight">

h

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

是权重参数，<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi mathvariant="bold">

b

</mi>

<mi>

i

</mi>
</msub>

<mo separator="true">

,

</mo>

<msub>
<mi mathvariant="bold">

b

</mi>

<mi>

f

</mi>
</msub>

<mo separator="true">

,

</mo>

<msub>
<mi mathvariant="bold">

b

</mi>

<mi>

o

</mi>
</msub>

<mo>

∈

</mo>

<msup>
<mi mathvariant="double-struck">

R

</mi>

<mrow>
<mn>

1

</mn>

<mo>

×

</mo>

<mi>

h

</mi>
</mrow>
</msup>
</mrow>

<annotation encoding="application/x-tex">

\mathbf{b}_i, \mathbf{b}_f, \mathbf{b}_o \in \mathbb{R}^{1 \times h}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9805em;vertical-align:-0.2861em;">



</span>

<span className="mord">
<span className="mord,mathbf">

b

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
<span className="mord,mathbf">

b

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
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

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord">
<span className="mord,mathbf">

b

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

o

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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

∈

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8491em;">



</span>

<span className="mord">
<span className="mord,mathbb">

R

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8491em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">

1

</span>

<span className="mbin,mtight">

×

</span>

<span className="mord,mathnormal,mtight">

h

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

是偏置参数。

###### 候选记忆元 (candidate memory cell)

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<msub>
<mover accent="true">
<mi mathvariant="bold">

C

</mi>

<mo>

~

</mo>
</mover>

<mi>

t

</mi>
</msub>

<mo>

∈

</mo>

<msup>
<mi mathvariant="double-struck">

R

</mi>

<mrow>
<mi>

n

</mi>

<mo>

×

</mo>

<mi>

h

</mi>
</mrow>
</msup>
</mrow>

<annotation encoding="application/x-tex">

\tilde{\mathbf{C}}_t \in \mathbb{R}^{n \times h}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.073em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,accent">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.923em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathbf">

C

</span>
</span>

<span style="top:-3.6051em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.25em;">
<span className="mord">

~

</span>
</span>
</span>
</span>
</span>
</span>
</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

∈

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8991em;">



</span>

<span className="mord">
<span className="mord,mathbb">

R

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8991em;">
<span style="top:-3.113em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

n

</span>

<span className="mbin,mtight">

×

</span>

<span className="mord,mathnormal,mtight">

h

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

它的计算与上面描述的三个门的计算类似，但是使用tanh函数作为激活函数，函数的值范围为(-1,1)。下面导出在时间步t处的方程：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<msub>
<mover accent="true">
<mi mathvariant="bold">

C

</mi>

<mo>

~

</mo>
</mover>

<mi>

t

</mi>
</msub>

<mo>

=

</mo>

<mi>

tanh

</mi>

<mo>

⁡

</mo>

<mo stretchy="false">

(

</mo>

<msub>
<mi mathvariant="bold">

X

</mi>

<mi>

t

</mi>
</msub>

<msub>
<mi mathvariant="bold">

W

</mi>

<mrow>
<mi>

x

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
<mi mathvariant="bold">

H

</mi>

<mrow>
<mi>

t

</mi>

<mo>

−

</mo>

<mn>

1

</mn>
</mrow>
</msub>

<msub>
<mi mathvariant="bold">

W

</mi>

<mrow>
<mi>

h

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
<mi mathvariant="bold">

b

</mi>

<mi>

c

</mi>
</msub>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

\tilde{\mathbf{C}}_t = \tanh(\mathbf{X}_t \mathbf{W}_{xc} + \mathbf{H}_{t-1} \mathbf{W}_{hc} + \mathbf{b}_c)

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.073em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,accent">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.923em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathbf">

C

</span>
</span>

<span style="top:-3.6051em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.25em;">
<span className="mord">

~

</span>
</span>
</span>
</span>
</span>
</span>
</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
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

<span className="mop">

tanh

</span>

<span className="mopen">

(

</span>

<span className="mord">
<span className="mord,mathbf">

X

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
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

<span className="mord">
<span className="mord,mathbf" style="margin-right:0.016em;">

W

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.016em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

x

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
<span className="strut" style="height:0.8944em;vertical-align:-0.2083em;">



</span>

<span className="mord">
<span className="mord,mathbf">

H

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
<span className="mord,mathnormal,mtight">

t

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
<span className="mord,mathbf" style="margin-right:0.016em;">

W

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.016em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



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
<span className="mord,mathbf">

b

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

<span className="mclose">

)

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
<mi mathvariant="bold">

W

</mi>

<mrow>
<mi>

x

</mi>

<mi>

c

</mi>
</mrow>
</msub>

<mo>

∈

</mo>

<msup>
<mi mathvariant="double-struck">

R

</mi>

<mrow>
<mi>

d

</mi>

<mo>

×

</mo>

<mi>

h

</mi>
</mrow>
</msup>

<mtext>

和

</mtext>

<msub>
<mi mathvariant="bold">

W

</mi>

<mrow>
<mi>

h

</mi>

<mi>

c

</mi>
</mrow>
</msub>

<mo>

∈

</mo>

<msup>
<mi mathvariant="double-struck">

R

</mi>

<mrow>
<mi>

h

</mi>

<mo>

×

</mo>

<mi>

h

</mi>
</mrow>
</msup>
</mrow>

<annotation encoding="application/x-tex">

\mathbf{W}_{xc} \in \mathbb{R}^{d \times h} \text{ 和 } \mathbf{W}_{hc} \in \mathbb{R}^{h \times h}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8361em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathbf" style="margin-right:0.016em;">

W

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.016em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

x

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

∈

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.9991em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathbb">

R

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8491em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

d

</span>

<span className="mbin,mtight">

×

</span>

<span className="mord,mathnormal,mtight">

h

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

<span className="mord,text">
<span className="mord">



</span>

<span className="mord,cjk_fallback">

和

</span>

<span className="mord">



</span>
</span>

<span className="mord">
<span className="mord,mathbf" style="margin-right:0.016em;">

W

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.016em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



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

∈

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8491em;">



</span>

<span className="mord">
<span className="mord,mathbb">

R

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8491em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

h

</span>

<span className="mbin,mtight">

×

</span>

<span className="mord,mathnormal,mtight">

h

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

是权重参数，<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi mathvariant="bold">

b

</mi>

<mi>

c

</mi>
</msub>

<mo>

∈

</mo>

<msup>
<mi mathvariant="double-struck">

R

</mi>

<mrow>
<mn>

1

</mn>

<mo>

×

</mo>

<mi>

h

</mi>
</mrow>
</msup>
</mrow>

<annotation encoding="application/x-tex">

\mathbf{b}_c \in \mathbb{R}^{1 \times h}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8444em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathbf">

b

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

∈

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8491em;">



</span>

<span className="mord">
<span className="mord,mathbb">

R

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8491em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">

1

</span>

<span className="mbin,mtight">

×

</span>

<span className="mord,mathnormal,mtight">

h

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

是偏置参数。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AIFrontier/AIFrontier-26.webp)

##### 记忆控制

在长短期记忆网络中，也有两个门用于这样的目的：输入门控制采用多少来自<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mover accent="true">
<mi mathvariant="bold">

C

</mi>

<mo>

~

</mo>
</mover>

<mi>

t

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

\tilde{\mathbf{C}}_t

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.073em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,accent">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.923em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathbf">

C

</span>
</span>

<span style="top:-3.6051em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.25em;">
<span className="mord">

~

</span>
</span>
</span>
</span>
</span>
</span>
</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
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

的新数据，而遗忘门<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi mathvariant="bold">

F

</mi>

<mi>

t

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

\mathbf{F}_t

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

F

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
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

控制保留多少过去的记忆元<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi mathvariant="bold">

C

</mi>

<mrow>
<mi>

t

</mi>

<mo>

−

</mo>

<mn>

1

</mn>
</mrow>
</msub>

<mo>

∈

</mo>

<msup>
<mi mathvariant="double-struck">

R

</mi>

<mrow>
<mi>

n

</mi>

<mo>

×

</mo>

<mi>

h

</mi>
</mrow>
</msup>
</mrow>

<annotation encoding="application/x-tex">

\mathbf{C}_{t-1} \in \mathbb{R}^{n \times h}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8944em;vertical-align:-0.2083em;">



</span>

<span className="mord">
<span className="mord,mathbf">

C

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
<span className="mord,mathnormal,mtight">

t

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

∈

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8491em;">



</span>

<span className="mord">
<span className="mord,mathbb">

R

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8491em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

n

</span>

<span className="mbin,mtight">

×

</span>

<span className="mord,mathnormal,mtight">

h

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

的内容。使用按元素乘法，得出：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<msub>
<mi mathvariant="bold">

C

</mi>

<mi>

t

</mi>
</msub>

<mo>

=

</mo>

<msub>
<mi mathvariant="bold">

F

</mi>

<mi>

t

</mi>
</msub>

<mo>

⊙

</mo>

<msub>
<mi mathvariant="bold">

C

</mi>

<mrow>
<mi>

t

</mi>

<mo>

−

</mo>

<mn>

1

</mn>
</mrow>
</msub>

<mo>

+

</mo>

<msub>
<mi mathvariant="bold">

I

</mi>

<mi>

t

</mi>
</msub>

<mo>

⊙

</mo>

<msub>
<mover accent="true">
<mi mathvariant="bold">

C

</mi>

<mo>

~

</mo>
</mover>

<mi>

t

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

\mathbf{C}_t = \mathbf{F}_t \odot \mathbf{C}_{t-1} + \mathbf{I}_t \odot \tilde{\mathbf{C}}_t

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

C

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8361em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathbf">

F

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
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

⊙

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8944em;vertical-align:-0.2083em;">



</span>

<span className="mord">
<span className="mord,mathbf">

C

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
<span className="mord,mathnormal,mtight">

t

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
<span className="strut" style="height:0.8361em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathbf">

I

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
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

⊙

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.073em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,accent">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.923em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathbf">

C

</span>
</span>

<span style="top:-3.6051em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.25em;">
<span className="mord">

~

</span>
</span>
</span>
</span>
</span>
</span>
</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
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
</span>

如果遗忘门始终为1且输入门始终为0，则过去的记忆元<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi mathvariant="bold">

C

</mi>

<mrow>
<mi>

t

</mi>

<mo>

−

</mo>

<mn>

1

</mn>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

\mathbf{C}_{t-1}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8944em;vertical-align:-0.2083em;">



</span>

<span className="mord">
<span className="mord,mathbf">

C

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
<span className="mord,mathnormal,mtight">

t

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

将随时间被保存并传递到当前时间步。引入这种设计是为了缓解梯度消失问题，并更好地捕获序列中的长距离依赖关系。

##### 隐状态计算

定义如何计算隐状态<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi mathvariant="bold">

H

</mi>

<mi>

t

</mi>
</msub>

<mo>

∈

</mo>

<msup>
<mi mathvariant="double-struck">

R

</mi>

<mrow>
<mi>

n

</mi>

<mo>

×

</mo>

<mi>

h

</mi>
</mrow>
</msup>
</mrow>

<annotation encoding="application/x-tex">

\mathbf{H}_t \in \mathbb{R}^{n \times h}

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

H

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

∈

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8491em;">



</span>

<span className="mord">
<span className="mord,mathbb">

R

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8491em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

n

</span>

<span className="mbin,mtight">

×

</span>

<span className="mord,mathnormal,mtight">

h

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

这就是输出门发挥作用的地方。在长短期记忆网络中，它仅仅是记忆元的tanh的门控版本。这就确保了<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi mathvariant="bold">

H

</mi>

<mi>

t

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

\mathbf{H}_t

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

H

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
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

的值始终在区间(-1,1)内：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<msub>
<mi mathvariant="bold">

H

</mi>

<mi>

t

</mi>
</msub>

<mo>

=

</mo>

<msub>
<mi mathvariant="bold">

O

</mi>

<mi>

t

</mi>
</msub>

<mo>

⊙

</mo>

<mi>

tanh

</mi>

<mo>

⁡

</mo>

<mo stretchy="false">

(

</mo>

<msub>
<mi mathvariant="bold">

C

</mi>

<mi>

t

</mi>
</msub>

<mo stretchy="false">

)

</mo>

<mi mathvariant="normal">

.

</mi>

<mspace width="1em">



</mspace>

<mo stretchy="false">

(

</mo>

<mn>

9.2.4

</mn>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

\mathbf{H}_t = \mathbf{O}_t \odot \tanh(\mathbf{C}_t). \quad (9.2.4)

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

H

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8361em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathbf">

O

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
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

⊙

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mop">

tanh

</span>

<span className="mopen">

(

</span>

<span className="mord">
<span className="mord,mathbf">

C

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
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

<span className="mclose">

)

</span>

<span className="mord">

.

</span>

<span className="mspace" style="margin-right:1em;">



</span>

<span className="mopen">

(

</span>

<span className="mord">

9.2.4

</span>

<span className="mclose">

)

</span>
</span>
</span>
</span>
</span>

只要输出门接近1，我们就能够有效地将所有记忆信息传递给预测部分，而对于输出门接近0，我们只保留记忆元内的所有信息，而不需要更新隐状态。

#### 5、门控循环单元（GRU）

> 门控循环单元与普通的循环神经网络之间的**关键区别**在于： <mark>
> 
> 前者支持隐状态的门控
> 
> </mark>
> 
> 。 这意味着模型有专门的机制来<mark>
> 
> 确定应该何时更新隐状态， 以及应该
> 
> </mark>
> 
> <mark>
> 
> **何时**
> 
> </mark>
> 
> <mark>
> 
> 重置隐状态
> 
> </mark>
> 
> 。 这些机制是可学习的

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AIFrontier/AIFrontier-27.webp)

##### 重置门和更新门

###### 重置门 (Reset Gate) - 控制"遗忘"        <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi mathvariant="bold">

R

</mi>

<mi>

t

</mi>
</msub>

<mo>

∈

</mo>

<msup>
<mi mathvariant="double-struck">

R

</mi>

<mrow>
<mi>

n

</mi>

<mo>

×

</mo>

<mi>

h

</mi>
</mrow>
</msup>
</mrow>

<annotation encoding="application/x-tex">

\mathbf{R}_t \in \mathbb{R}^{n \times h}

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

R

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

∈

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8491em;">



</span>

<span className="mord">
<span className="mord,mathbb">

R

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8491em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

n

</span>

<span className="mbin,mtight">

×

</span>

<span className="mord,mathnormal,mtight">

h

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>



- **重置门 ≈ 0**：完全忘记过去信息，候选隐状态只依赖当前输入（像全新开始）
- **重置门 ≈ 1**：完全保留过去信息，候选隐状态同时考虑当前输入和历史状态

###### 更新门 (Update Gate) - 控制"更新"      <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi mathvariant="bold">

Z

</mi>

<mi>

t

</mi>
</msub>

<mo>

∈

</mo>

<msup>
<mi mathvariant="double-struck">

R

</mi>

<mrow>
<mi>

n

</mi>

<mo>

×

</mo>

<mi>

h

</mi>
</mrow>
</msup>
</mrow>

<annotation encoding="application/x-tex">

\mathbf{Z}_t \in \mathbb{R}^{n \times h}

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

Z

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

∈

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8491em;">



</span>

<span className="mord">
<span className="mord,mathbb">

R

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8491em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

n

</span>

<span className="mbin,mtight">

×

</span>

<span className="mord,mathnormal,mtight">

h

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>



- **更新门 ≈ 0**：大量采用新信息（候选隐状态），少量保留旧信息
- **更新门 ≈ 1**：大量保留旧信息（前一时刻隐状态），少量采用新信息

门控循环单元的数学表达。对于给定的时间步t，假设输入是一个小批量<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi mathvariant="bold">

X

</mi>

<mi>

t

</mi>
</msub>

<mo>

∈

</mo>

<msup>
<mi mathvariant="double-struck">

R

</mi>

<mrow>
<mi>

n

</mi>

<mo>

×

</mo>

<mi>

d

</mi>
</mrow>
</msup>
</mrow>

<annotation encoding="application/x-tex">

\mathbf{X}_t \in \mathbb{R}^{n \times d}

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

X

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

∈

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8491em;">



</span>

<span className="mord">
<span className="mord,mathbb">

R

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8491em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

n

</span>

<span className="mbin,mtight">

×

</span>

<span className="mord,mathnormal,mtight">

d

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

（样本个数n，输入个数d），上一个时间步的隐状态是<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi mathvariant="bold">

H

</mi>

<mrow>
<mi>

t

</mi>

<mo>

−

</mo>

<mn>

1

</mn>
</mrow>
</msub>

<mo>

∈

</mo>

<msup>
<mi mathvariant="double-struck">

R

</mi>

<mrow>
<mi>

n

</mi>

<mo>

×

</mo>

<mi>

h

</mi>
</mrow>
</msup>
</mrow>

<annotation encoding="application/x-tex">

\mathbf{H}_{t-1} \in \mathbb{R}^{n \times h}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8944em;vertical-align:-0.2083em;">



</span>

<span className="mord">
<span className="mord,mathbf">

H

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
<span className="mord,mathnormal,mtight">

t

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

∈

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8491em;">



</span>

<span className="mord">
<span className="mord,mathbb">

R

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8491em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

n

</span>

<span className="mbin,mtight">

×

</span>

<span className="mord,mathnormal,mtight">

h

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

（隐藏单元个数h）。那么，重置门<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi mathvariant="bold">

R

</mi>

<mi>

t

</mi>
</msub>

<mo>

∈

</mo>

<msup>
<mi mathvariant="double-struck">

R

</mi>

<mrow>
<mi>

n

</mi>

<mo>

×

</mo>

<mi>

h

</mi>
</mrow>
</msup>
</mrow>

<annotation encoding="application/x-tex">

\mathbf{R}_t \in \mathbb{R}^{n \times h}

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

R

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

∈

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8491em;">



</span>

<span className="mord">
<span className="mord,mathbb">

R

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8491em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

n

</span>

<span className="mbin,mtight">

×

</span>

<span className="mord,mathnormal,mtight">

h

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

和更新门<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi mathvariant="bold">

Z

</mi>

<mi>

t

</mi>
</msub>

<mo>

∈

</mo>

<msup>
<mi mathvariant="double-struck">

R

</mi>

<mrow>
<mi>

n

</mi>

<mo>

×

</mo>

<mi>

h

</mi>
</mrow>
</msup>
</mrow>

<annotation encoding="application/x-tex">

\mathbf{Z}_t \in \mathbb{R}^{n \times h}

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

Z

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

∈

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8491em;">



</span>

<span className="mord">
<span className="mord,mathbb">

R

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8491em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

n

</span>

<span className="mbin,mtight">

×

</span>

<span className="mord,mathnormal,mtight">

h

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>



的计算如下所示：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<msub>
<mi mathvariant="bold">

R

</mi>

<mi>

t

</mi>
</msub>

<mo>

=

</mo>

<mi>

σ

</mi>

<mo stretchy="false">

(

</mo>

<msub>
<mi mathvariant="bold">

X

</mi>

<mi>

t

</mi>
</msub>

<msub>
<mi mathvariant="bold">

W

</mi>

<mrow>
<mi>

x

</mi>

<mi>

r

</mi>
</mrow>
</msub>

<mo>

+

</mo>

<msub>
<mi mathvariant="bold">

H

</mi>

<mrow>
<mi>

t

</mi>

<mo>

−

</mo>

<mn>

1

</mn>
</mrow>
</msub>

<msub>
<mi mathvariant="bold">

W

</mi>

<mrow>
<mi>

h

</mi>

<mi>

r

</mi>
</mrow>
</msub>

<mo>

+

</mo>

<msub>
<mi mathvariant="bold">

b

</mi>

<mi>

r

</mi>
</msub>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

\mathbf{R}_t = \sigma(\mathbf{X}_t \mathbf{W}_{xr} + \mathbf{H}_{t-1} \mathbf{W}_{hr} + \mathbf{b}_r)

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

R

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
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

σ

</span>

<span className="mopen">

(

</span>

<span className="mord">
<span className="mord,mathbf">

X

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
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

<span className="mord">
<span className="mord,mathbf" style="margin-right:0.016em;">

W

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.016em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

x

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

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
<span className="strut" style="height:0.8944em;vertical-align:-0.2083em;">



</span>

<span className="mord">
<span className="mord,mathbf">

H

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
<span className="mord,mathnormal,mtight">

t

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
<span className="mord,mathbf" style="margin-right:0.016em;">

W

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.016em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

h

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

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
<span className="mord,mathbf">

b

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

r

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<msub>
<mi mathvariant="bold">

Z

</mi>

<mi>

t

</mi>
</msub>

<mo>

=

</mo>

<mi>

σ

</mi>

<mo stretchy="false">

(

</mo>

<msub>
<mi mathvariant="bold">

X

</mi>

<mi>

t

</mi>
</msub>

<msub>
<mi mathvariant="bold">

W

</mi>

<mrow>
<mi>

x

</mi>

<mi>

z

</mi>
</mrow>
</msub>

<mo>

+

</mo>

<msub>
<mi mathvariant="bold">

H

</mi>

<mrow>
<mi>

t

</mi>

<mo>

−

</mo>

<mn>

1

</mn>
</mrow>
</msub>

<msub>
<mi mathvariant="bold">

W

</mi>

<mrow>
<mi>

h

</mi>

<mi>

z

</mi>
</mrow>
</msub>

<mo>

+

</mo>

<msub>
<mi mathvariant="bold">

b

</mi>

<mi>

z

</mi>
</msub>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

\mathbf{Z}_t = \sigma(\mathbf{X}_t \mathbf{W}_{xz} + \mathbf{H}_{t-1} \mathbf{W}_{hz} + \mathbf{b}_z)

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

Z

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
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

σ

</span>

<span className="mopen">

(

</span>

<span className="mord">
<span className="mord,mathbf">

X

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
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

<span className="mord">
<span className="mord,mathbf" style="margin-right:0.016em;">

W

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.016em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

x

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.044em;">

z

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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
<span className="strut" style="height:0.8944em;vertical-align:-0.2083em;">



</span>

<span className="mord">
<span className="mord,mathbf">

H

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
<span className="mord,mathnormal,mtight">

t

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
<span className="mord,mathbf" style="margin-right:0.016em;">

W

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.016em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

h

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.044em;">

z

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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
<span className="mord,mathbf">

b

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.044em;">

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

接下来，让我们将重置门<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi mathvariant="bold">

R

</mi>

<mi>

t

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

\mathbf{R}_t

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

R

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
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

与**常规隐状态更新机制集成**，得到在时间步t的候选隐状态 (candidate hidden state)<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mover accent="true">
<mi mathvariant="bold">

H

</mi>

<mo>

~

</mo>
</mover>

<mi>

t

</mi>
</msub>

<mo>

∈

</mo>

<msup>
<mi mathvariant="double-struck">

R

</mi>

<mrow>
<mi>

n

</mi>

<mo>

×

</mo>

<mi>

h

</mi>
</mrow>
</msup>
</mrow>

<annotation encoding="application/x-tex">

\tilde{\mathbf{H}}_t \in \mathbb{R}^{n \times h}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.073em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,accent">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.923em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathbf">

H

</span>
</span>

<span style="top:-3.6051em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.25em;">
<span className="mord">

~

</span>
</span>
</span>
</span>
</span>
</span>
</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
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

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

∈

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8491em;">



</span>

<span className="mord">
<span className="mord,mathbb">

R

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8491em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

n

</span>

<span className="mbin,mtight">

×

</span>

<span className="mord,mathnormal,mtight">

h

</span>
</span>
</span>
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
<mover accent="true">
<mi mathvariant="bold">

H

</mi>

<mo>

~

</mo>
</mover>

<mi>

t

</mi>
</msub>

<mo>

=

</mo>

<mi>

tanh

</mi>

<mo>

⁡

</mo>

<mo stretchy="false">

(

</mo>

<msub>
<mi mathvariant="bold">

X

</mi>

<mi>

t

</mi>
</msub>

<msub>
<mi mathvariant="bold">

W

</mi>

<mrow>
<mi>

x

</mi>

<mi>

h

</mi>
</mrow>
</msub>

<mo>

+

</mo>

<mo stretchy="false">

(

</mo>

<msub>
<mi mathvariant="bold">

R

</mi>

<mi>

t

</mi>
</msub>

<mo>

⊙

</mo>

<msub>
<mi mathvariant="bold">

H

</mi>

<mrow>
<mi>

t

</mi>

<mo>

−

</mo>

<mn>

1

</mn>
</mrow>
</msub>

<mo stretchy="false">

)

</mo>

<msub>
<mi mathvariant="bold">

W

</mi>

<mrow>
<mi>

h

</mi>

<mi>

h

</mi>
</mrow>
</msub>

<mo>

+

</mo>

<msub>
<mi mathvariant="bold">

b

</mi>

<mi>

h

</mi>
</msub>

<mo stretchy="false">

)

</mo>

<mo separator="true">

,

</mo>

<mspace width="1em">



</mspace>

<mo stretchy="false">

(

</mo>

<mn>

9.1.2

</mn>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

\tilde{\mathbf{H}}_t = \tanh(\mathbf{X}_t \mathbf{W}_{xh} + (\mathbf{R}_t \odot \mathbf{H}_{t-1}) \mathbf{W}_{hh} + \mathbf{b}_h), \quad (9.1.2)

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.073em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,accent">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.923em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathbf">

H

</span>
</span>

<span style="top:-3.6051em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.25em;">
<span className="mord">

~

</span>
</span>
</span>
</span>
</span>
</span>
</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
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

<span className="mop">

tanh

</span>

<span className="mopen">

(

</span>

<span className="mord">
<span className="mord,mathbf">

X

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
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

<span className="mord">
<span className="mord,mathbf" style="margin-right:0.016em;">

W

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.016em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

x

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

<span className="mord">
<span className="mord,mathbf">

R

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
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

⊙

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord">
<span className="mord,mathbf">

H

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
<span className="mord,mathnormal,mtight">

t

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

<span className="mclose">

)

</span>

<span className="mord">
<span className="mord,mathbf" style="margin-right:0.016em;">

W

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.016em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

hh

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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
<span className="mord,mathbf">

b

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

h

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:1em;">



</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mopen">

(

</span>

<span className="mord">

9.1.2

</span>

<span className="mclose">

)

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
<mi mathvariant="bold">

W

</mi>

<mrow>
<mi>

x

</mi>

<mi>

h

</mi>
</mrow>
</msub>

<mo>

∈

</mo>

<msup>
<mi mathvariant="double-struck">

R

</mi>

<mrow>
<mi>

d

</mi>

<mo>

×

</mo>

<mi>

h

</mi>
</mrow>
</msup>

<mtext>

和

</mtext>

<msub>
<mi mathvariant="bold">

W

</mi>

<mrow>
<mi>

h

</mi>

<mi>

h

</mi>
</mrow>
</msub>

<mo>

∈

</mo>

<msup>
<mi mathvariant="double-struck">

R

</mi>

<mrow>
<mi>

h

</mi>

<mo>

×

</mo>

<mi>

h

</mi>
</mrow>
</msup>
</mrow>

<annotation encoding="application/x-tex">

\mathbf{W}_{xh} \in \mathbb{R}^{d \times h} \text{ 和 } \mathbf{W}_{hh} \in \mathbb{R}^{h \times h}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8361em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathbf" style="margin-right:0.016em;">

W

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.016em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

x

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

∈

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.9991em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathbb">

R

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8491em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

d

</span>

<span className="mbin,mtight">

×

</span>

<span className="mord,mathnormal,mtight">

h

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

<span className="mord,text">
<span className="mord">



</span>

<span className="mord,cjk_fallback">

和

</span>

<span className="mord">



</span>
</span>

<span className="mord">
<span className="mord,mathbf" style="margin-right:0.016em;">

W

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.016em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

hh

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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

∈

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8491em;">



</span>

<span className="mord">
<span className="mord,mathbb">

R

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8491em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

h

</span>

<span className="mbin,mtight">

×

</span>

<span className="mord,mathnormal,mtight">

h

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

是权重参数，<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi mathvariant="bold">

b

</mi>

<mi>

h

</mi>
</msub>

<mo>

∈

</mo>

<msup>
<mi mathvariant="double-struck">

R

</mi>

<mrow>
<mn>

1

</mn>

<mo>

×

</mo>

<mi>

h

</mi>
</mrow>
</msup>
</mrow>

<annotation encoding="application/x-tex">

\mathbf{b}_h \in \mathbb{R}^{1 \times h}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8444em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathbf">

b

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

h

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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

∈

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8491em;">



</span>

<span className="mord">
<span className="mord,mathbb">

R

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8491em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">

1

</span>

<span className="mbin,mtight">

×

</span>

<span className="mord,mathnormal,mtight">

h

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

是偏置项，符号<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mo>

⊙

</mo>
</mrow>

<annotation encoding="application/x-tex">

\odot

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6667em;vertical-align:-0.0833em;">



</span>

<span className="mord">

⊙

</span>
</span>
</span>
</span>

是Hadamard积（按元素乘积）运算符。

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<msub>
<mi mathvariant="bold">

H

</mi>

<mi>

t

</mi>
</msub>

<mo>

=

</mo>

<msub>
<mi mathvariant="bold">

Z

</mi>

<mi>

t

</mi>
</msub>

<mo>

⊙

</mo>

<msub>
<mi mathvariant="bold">

H

</mi>

<mrow>
<mi>

t

</mi>

<mo>

−

</mo>

<mn>

1

</mn>
</mrow>
</msub>

<mo>

+

</mo>

<mrow>
<mo fence="true">

(

</mo>

<mn>

1

</mn>

<mo>

−

</mo>

<msub>
<mi mathvariant="bold">

Z

</mi>

<mi>

t

</mi>
</msub>

<mo fence="true">

)

</mo>
</mrow>

<mo>

⊙

</mo>

<msub>
<mover accent="true">
<mi mathvariant="bold">

H

</mi>

<mo>

~

</mo>
</mover>

<mi>

t

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

\mathbf{H}_{t}=\mathbf{Z}_{t} \odot \mathbf{H}_{t-1}+\left(1-\mathbf{Z}_{t}\right) \odot \tilde{\mathbf{H}}_{t}

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

H

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
<span className="strut" style="height:0.8361em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathbf">

Z

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

⊙

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8944em;vertical-align:-0.2083em;">



</span>

<span className="mord">
<span className="mord,mathbf">

H

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
<span className="mord,mathnormal,mtight">

t

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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="minner">
<span className="mopen,delimcenter" style="top:0em;">

(

</span>

<span className="mord">

1

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

−

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mord">
<span className="mord,mathbf">

Z

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

<span className="mclose,delimcenter" style="top:0em;">

)

</span>
</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

⊙

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.073em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,accent">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.923em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathbf">

H

</span>
</span>

<span style="top:-3.6051em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.25em;">
<span className="mord">

~

</span>
</span>
</span>
</span>
</span>
</span>
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
</span>

##### 6、Padding

在循环神经网络中，输入序列的长度通常是不一致的，因此需要对输入序列进行Padding 操作，将所有输入序列填充到相同长度

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AIFrontier/AIFrontier-28.webp)

> PAD加到后面——不好；加到前面——好，因为语句越往后越重要，由此也引出了双向循环神经网络

##### 7、双向循环神经网络（Bidirectional Recurrent Neural Network, BiRNN）

双向循环神经网络（Bidirectional Recurrent Neural Network, BiRNN）是一种特殊的循环神经网络结构，它通过在**时间序列的正向和反向两个方向**上同时进行信息处理，从而更好地捕捉序列数据中的上下文信息

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AIFrontier/AIFrontier-29.webp)

### 六、Transformer结构

#### 1、注意力机制

##### 基本概念

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AIFrontier/AIFrontier-30.webp)

首先生成每个单词的内嵌向量（包含了单词在句子中位置编码向量信息），记为<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

w

</mi>

<mi>

i

</mi>
</msub>

<mo stretchy="false">

(

</mo>

<mn>

1

</mn>

<mo>

≤

</mo>

<mi>

i

</mi>

<mo>

≤

</mo>

<mn>

4

</mn>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

w_i(1≤i≤4)

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0269em;">

w

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0269em;margin-right:0.05em;">
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

<span className="mopen">

(

</span>

<span className="mord">

1

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
<span className="strut" style="height:0.7955em;vertical-align:-0.136em;">



</span>

<span className="mord,mathnormal">

i

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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord">

4

</span>

<span className="mclose">

)

</span>
</span>
</span>
</span>

,如下计算每个单词<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

w

</mi>

<mi>

i

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

w_i

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.5806em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0269em;">

w

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0269em;margin-right:0.05em;">
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

的<mark>

查询向量（query）、键向量(key)和值向量(value)

</mark>

：

1. 查询向量：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

q

</mi>

<mi>

i

</mi>
</msub>

<mo>

=

</mo>

<msup>
<mi>

W

</mi>

<mi>

q

</mi>
</msup>

<mo>

×

</mo>

<msub>
<mi>

w

</mi>

<mi>

i

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

q_i=W^q×w_i

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.625em;vertical-align:-0.1944em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

q

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
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
<span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.1389em;">

W

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.6644em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

q

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

×

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.5806em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0269em;">

w

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0269em;margin-right:0.05em;">
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
2. 健向量：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

k

</mi>

<mi>

i

</mi>
</msub>

<mo>

=

</mo>

<msup>
<mi>

W

</mi>

<mi>

k

</mi>
</msup>

<mo>

×

</mo>

<msub>
<mi>

w

</mi>

<mi>

i

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

k_i=W^k×w_i

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8444em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0315em;">

k

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0315em;margin-right:0.05em;">
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
<span className="strut" style="height:0.9324em;vertical-align:-0.0833em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.1389em;">

W

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8491em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

×

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.5806em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0269em;">

w

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0269em;margin-right:0.05em;">
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
3. 值向量：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

v

</mi>

<mi>

i

</mi>
</msub>

<mo>

=

</mo>

<msup>
<mi>

W

</mi>

<mi>

v

</mi>
</msup>

<mo>

×

</mo>

<msub>
<mi>

w

</mi>

<mi>

i

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

v_i=W^v×w_i

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
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
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
<span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.1389em;">

W

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.6644em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

v

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

×

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.5806em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0269em;">

w

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0269em;margin-right:0.05em;">
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

> <mark>
> 
> **自注意力模型就是要挖掘单词Wi与其他单词在句子中因为上下文（context）关联而具有的自注意力取值大小**
> 
> </mark>

<span className="katex">
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

<msubsup>
<mi>

a

</mi>

<mrow>
<mn>

3

</mn>

<mi>

i

</mi>
</mrow>

<mtext>

′

</mtext>
</msubsup>

<mo>

×

</mo>

<msub>
<mi>

v

</mi>

<mi>

i

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

∑_ia_{3i}^′×v_i

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.0516em;vertical-align:-0.2997em;">



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
<span className="mord,mathnormal">

a

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.7519em;">
<span style="top:-2.4413em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">

3

</span>

<span className="mord,mathnormal,mtight">

i

</span>
</span>
</span>
</span>

<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
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
<span className="vlist" style="height:0.2587em;">
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
<span className="strut" style="height:0.5806em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

v

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
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

, 这个结果作为在当前句子语境下单词<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

w

</mi>

<mn>

3

</mn>
</msub>
</mrow>

<annotation encoding="application/x-tex">

w_3

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.5806em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0269em;">

w

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.0269em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">

3

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

 **“注意”到**与其他单词的关联程度（self-attention）

##### 多头注意力机制——找多重关系

> 可引入**“多头”注意力（multi-headed attention）**机制从更多角度来挖掘某个单词与其他单词之间概率关联，**每个单词自注意力关联可以并行计算**

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AIFrontier/AIFrontier-31.webp)

多头注意⼒机制是由于两个token之间可能存在【多种不同类型的关系】（如语法关系、语义关系等）

#### 2、正则化与批归一化

##### 正则化

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AIFrontier/AIFrontier-32.webp)

##### 批归一化

通过规范化手段，把神经网络每层中任意神经元<mark>

**的输入值分布改变成均值为0、方差为1的标准正态分布**

</mark>

，把偏移较大的分布强制映射为标准正态分布。经过批归一化处理，激活函数的输入值被映射到非线性函数梯度较大的区域，使得梯度变大从而克服梯度消失问题，进而加快收敛速度

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 53.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AIFrontier/AIFrontier-33.webp" />
      </p>
    </td>
    
    
      <td style="width: 46.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AIFrontier/AIFrontier-34.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

实际上就是**概统里面的正态分布估计——大数定律**

#### 3、Transformer

不同于传统卷积神经网络使用固定的卷积核（感受野），Transformer 模型使用自注意力来**自适应计算感受野**

##### 基本组件

- **Image**: <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

I

</mi>

<mo>

∈

</mo>

<msup>
<mi mathvariant="double-struck">

R

</mi>

<mrow>
<mi>

C

</mi>

<mo>

×

</mo>

<mi>

N

</mi>
</mrow>
</msup>
</mrow>

<annotation encoding="application/x-tex">

I \in \mathbb{R}^{C \times N}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.7224em;vertical-align:-0.0391em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0785em;">

I

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

∈

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8413em;">



</span>

<span className="mord">
<span className="mord,mathbb">

R

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8413em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0715em;">

C

</span>

<span className="mbin,mtight">

×

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.109em;">

N

</span>
</span>
</span>
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
<mo stretchy="false">

(

</mo>

<mi>

N

</mi>

<mo>

=

</mo>

<mi>

H

</mi>

<mo>

×

</mo>

<mi>

W

</mi>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

(N = H \times W)

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

<span className="mord,mathnormal" style="margin-right:0.109em;">

N

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

<span className="mord,mathnormal" style="margin-right:0.0813em;">

H

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

W

</span>

<span className="mclose">

)

</span>
</span>
</span>
</span>


  - 绝对位置编码：<span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <msup>
  <mi>
  
  I
  
  </mi>
  
  <mrow>
  <mo stretchy="false">
  
  (
  
  </mo>
  
  <mi>
  
  x
  
  </mi>
  
  <mo separator="true">
  
  ,
  
  </mo>
  
  <mi>
  
  y
  
  </mi>
  
  <mo stretchy="false">
  
  )
  
  </mo>
  </mrow>
  </msup>
  
  <mo>
  
  =
  
  </mo>
  
  <msup>
  <mi mathvariant="bold">
  
  F
  
  </mi>
  
  <mrow>
  <mo stretchy="false">
  
  (
  
  </mo>
  
  <mi>
  
  x
  
  </mi>
  
  <mo separator="true">
  
  ,
  
  </mo>
  
  <mi>
  
  y
  
  </mi>
  
  <mo stretchy="false">
  
  )
  
  </mo>
  </mrow>
  </msup>
  
  <mo>
  
  +
  
  </mo>
  
  <mtext>
  
  Emb
  
  </mtext>
  
  <mo stretchy="false">
  
  (
  
  </mo>
  
  <mi>
  
  x
  
  </mi>
  
  <mo separator="true">
  
  ,
  
  </mo>
  
  <mi>
  
  y
  
  </mi>
  
  <mo stretchy="false">
  
  )
  
  </mo>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  I^{(x,y)} = \mathbf{F}^{(x,y)} + \text{Emb}(x, y)
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:0.888em;">
  
  
  
  </span>
  
  <span className="mord">
  <span className="mord,mathnormal" style="margin-right:0.0785em;">
  
  I
  
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
  <span className="mopen,mtight">
  
  (
  
  </span>
  
  <span className="mord,mathnormal,mtight">
  
  x
  
  </span>
  
  <span className="mpunct,mtight">
  
  ,
  
  </span>
  
  <span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">
  
  y
  
  </span>
  
  <span className="mclose,mtight">
  
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
  
  <span className="mspace" style="margin-right:0.2778em;">
  
  
  
  </span>
  
  <span className="mrel">
  
  =
  
  </span>
  
  <span className="mspace" style="margin-right:0.2778em;">
  
  
  
  </span>
  </span>
  
  <span className="base">
  <span className="strut" style="height:0.9713em;vertical-align:-0.0833em;">
  
  
  
  </span>
  
  <span className="mord">
  <span className="mord,mathbf">
  
  F
  
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
  <span className="mopen,mtight">
  
  (
  
  </span>
  
  <span className="mord,mathnormal,mtight">
  
  x
  
  </span>
  
  <span className="mpunct,mtight">
  
  ,
  
  </span>
  
  <span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">
  
  y
  
  </span>
  
  <span className="mclose,mtight">
  
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
  
  <span className="mord,text">
  <span className="mord">
  
  Emb
  
  </span>
  </span>
  
  <span className="mopen">
  
  (
  
  </span>
  
  <span className="mord,mathnormal">
  
  x
  
  </span>
  
  <span className="mpunct">
  
  ,
  
  </span>
  
  <span className="mspace" style="margin-right:0.1667em;">
  
  
  
  </span>
  
  <span className="mord,mathnormal" style="margin-right:0.0359em;">
  
  y
  
  </span>
  
  <span className="mclose">
  
  )
  
  </span>
  </span>
  </span>
  </span>
- **Query**: <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi mathvariant="bold">

Q

</mi>

<mo>

=

</mo>

<msub>
<mi mathvariant="bold">

W

</mi>

<mi>

q

</mi>
</msub>

<mo>

⋅

</mo>

<mi mathvariant="bold">

I

</mi>

<mo>

∈

</mo>

<msup>
<mi mathvariant="double-struck">

R

</mi>

<mrow>
<msup>
<mi>

C

</mi>

<mo mathvariant="normal" lspace="0em" rspace="0em">

′

</mo>
</msup>

<mo>

×

</mo>

<mi>

N

</mi>
</mrow>
</msup>
</mrow>

<annotation encoding="application/x-tex">

\mathbf{Q} = \mathbf{W}_q \cdot \mathbf{I} \in \mathbb{R}^{C' \times N}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8805em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathbf">

Q

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
<span className="strut" style="height:0.9722em;vertical-align:-0.2861em;">



</span>

<span className="mord">
<span className="mord,mathbf" style="margin-right:0.016em;">

W

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.016em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

q

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

⋅

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.7252em;vertical-align:-0.0391em;">



</span>

<span className="mord,mathbf">

I

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

∈

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.9425em;">



</span>

<span className="mord">
<span className="mord,mathbb">

R

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.9425em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0715em;">

C

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8278em;">
<span style="top:-2.931em;margin-right:0.0714em;">
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

<span className="mbin,mtight">

×

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.109em;">

N

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

, <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi mathvariant="bold">

W

</mi>

<mi>

q

</mi>
</msub>

<mo>

∈

</mo>

<msup>
<mi mathvariant="double-struck">

R

</mi>

<mrow>
<msup>
<mi>

C

</mi>

<mo mathvariant="normal" lspace="0em" rspace="0em">

′

</mo>
</msup>

<mo>

×

</mo>

<mi>

C

</mi>
</mrow>
</msup>
</mrow>

<annotation encoding="application/x-tex">

\mathbf{W}_q \in \mathbb{R}^{C' \times C}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9722em;vertical-align:-0.2861em;">



</span>

<span className="mord">
<span className="mord,mathbf" style="margin-right:0.016em;">

W

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.016em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

q

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

∈

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.9425em;">



</span>

<span className="mord">
<span className="mord,mathbb">

R

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.9425em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0715em;">

C

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8278em;">
<span style="top:-2.931em;margin-right:0.0714em;">
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

<span className="mbin,mtight">

×

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0715em;">

C

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
- **Key**: <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi mathvariant="bold">

K

</mi>

<mo>

=

</mo>

<msub>
<mi mathvariant="bold">

W

</mi>

<mi>

k

</mi>
</msub>

<mo>

⋅

</mo>

<mi mathvariant="bold">

I

</mi>

<mo>

∈

</mo>

<msup>
<mi mathvariant="double-struck">

R

</mi>

<mrow>
<msup>
<mi>

C

</mi>

<mo mathvariant="normal" lspace="0em" rspace="0em">

′

</mo>
</msup>

<mo>

×

</mo>

<mi>

N

</mi>
</mrow>
</msup>
</mrow>

<annotation encoding="application/x-tex">

\mathbf{K} = \mathbf{W}_k \cdot \mathbf{I} \in \mathbb{R}^{C' \times N}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6861em;">



</span>

<span className="mord,mathbf">

K

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
<span className="strut" style="height:0.8361em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathbf" style="margin-right:0.016em;">

W

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.016em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0315em;">

k

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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

⋅

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.7252em;vertical-align:-0.0391em;">



</span>

<span className="mord,mathbf">

I

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

∈

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.9425em;">



</span>

<span className="mord">
<span className="mord,mathbb">

R

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.9425em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0715em;">

C

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8278em;">
<span style="top:-2.931em;margin-right:0.0714em;">
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

<span className="mbin,mtight">

×

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.109em;">

N

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

, <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi mathvariant="bold">

W

</mi>

<mi>

k

</mi>
</msub>

<mo>

∈

</mo>

<msup>
<mi mathvariant="double-struck">

R

</mi>

<mrow>
<msup>
<mi>

C

</mi>

<mo mathvariant="normal" lspace="0em" rspace="0em">

′

</mo>
</msup>

<mo>

×

</mo>

<mi>

C

</mi>
</mrow>
</msup>
</mrow>

<annotation encoding="application/x-tex">

\mathbf{W}_k \in \mathbb{R}^{C' \times C}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8361em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathbf" style="margin-right:0.016em;">

W

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.016em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0315em;">

k

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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

∈

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.9425em;">



</span>

<span className="mord">
<span className="mord,mathbb">

R

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.9425em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0715em;">

C

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8278em;">
<span style="top:-2.931em;margin-right:0.0714em;">
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

<span className="mbin,mtight">

×

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0715em;">

C

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
- **Scaled Dot Product**: <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi mathvariant="bold">

P

</mi>

<mo>

=

</mo>

<mfrac>
<mrow>
<msup>
<mi mathvariant="bold">

Q

</mi>

<mi>

T

</mi>
</msup>

<mo>

⋅

</mo>

<mi mathvariant="bold">

K

</mi>
</mrow>

<msqrt>
<msup>
<mi>

C

</mi>

<mo mathvariant="normal" lspace="0em" rspace="0em">

′

</mo>
</msup>
</msqrt>
</mfrac>

<mo>

∈

</mo>

<msup>
<mi mathvariant="double-struck">

R

</mi>

<mrow>
<mi>

N

</mi>

<mo>

×

</mo>

<mi>

N

</mi>
</mrow>
</msup>
</mrow>

<annotation encoding="application/x-tex">

\mathbf{P} = \frac{\mathbf{Q}^T \cdot \mathbf{K}}{\sqrt{C'}} \in \mathbb{R}^{N \times N}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6861em;">



</span>

<span className="mord,mathbf">

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
<span className="strut" style="height:1.6275em;vertical-align:-0.538em;">



</span>

<span className="mord">
<span className="mopen,nulldelimiter">



</span>

<span className="mfrac">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:1.0895em;">
<span style="top:-2.5374em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,sqrt,mtight">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.9323em;">
<span className="svg-align" style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mtight" style="padding-left:0.833em;">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0715em;">

C

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

<span style="top:-2.8923em;">
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
<span className="vlist" style="height:0.1077em;">
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

<span style="top:-3.4461em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">
<span className="mord,mathbf,mtight">

Q

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.9191em;">
<span style="top:-2.931em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
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

<span className="mbin,mtight">

⋅

</span>

<span className="mord,mathbf,mtight">

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
<span className="vlist" style="height:0.538em;">
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

∈

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8413em;">



</span>

<span className="mord">
<span className="mord,mathbb">

R

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8413em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.109em;">

N

</span>

<span className="mbin,mtight">

×

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.109em;">

N

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
- **Attention**: <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi mathvariant="bold">

A

</mi>

<mo>

=

</mo>

<mtext>

softmax

</mtext>

<mo stretchy="false">

(

</mo>

<mi mathvariant="bold">

P

</mi>

<mo stretchy="false">

)

</mo>

<mo>

∈

</mo>

<msup>
<mi mathvariant="double-struck">

R

</mi>

<mrow>
<mi>

N

</mi>

<mo>

×

</mo>

<mi>

N

</mi>
</mrow>
</msup>
</mrow>

<annotation encoding="application/x-tex">

\mathbf{A} = \text{softmax}(\mathbf{P}) \in \mathbb{R}^{N \times N}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6861em;">



</span>

<span className="mord,mathbf">

A

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

<span className="mord,text">
<span className="mord">

softmax

</span>
</span>

<span className="mopen">

(

</span>

<span className="mord,mathbf">

P

</span>

<span className="mclose">

)

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

∈

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8413em;">



</span>

<span className="mord">
<span className="mord,mathbb">

R

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8413em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.109em;">

N

</span>

<span className="mbin,mtight">

×

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.109em;">

N

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
- **Value**: <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi mathvariant="bold">

V

</mi>

<mo>

=

</mo>

<msub>
<mi mathvariant="bold">

W

</mi>

<mi>

v

</mi>
</msub>

<mo>

⋅

</mo>

<mi mathvariant="bold">

I

</mi>

<mo>

∈

</mo>

<msup>
<mi mathvariant="double-struck">

R

</mi>

<mrow>
<msup>
<mi>

C

</mi>

<mo mathvariant="normal" lspace="0em" rspace="0em">

′

</mo>
</msup>

<mo>

×

</mo>

<mi>

N

</mi>
</mrow>
</msup>
</mrow>

<annotation encoding="application/x-tex">

\mathbf{V} = \mathbf{W}_v \cdot \mathbf{I} \in \mathbb{R}^{C' \times N}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6861em;">



</span>

<span className="mord,mathbf" style="margin-right:0.016em;">

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
<span className="strut" style="height:0.8361em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathbf" style="margin-right:0.016em;">

W

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.016em;margin-right:0.05em;">
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

⋅

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.7252em;vertical-align:-0.0391em;">



</span>

<span className="mord,mathbf">

I

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

∈

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.9425em;">



</span>

<span className="mord">
<span className="mord,mathbb">

R

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.9425em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0715em;">

C

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8278em;">
<span style="top:-2.931em;margin-right:0.0714em;">
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

<span className="mbin,mtight">

×

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.109em;">

N

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

, <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi mathvariant="bold">

W

</mi>

<mi>

v

</mi>
</msub>

<mo>

∈

</mo>

<msup>
<mi mathvariant="double-struck">

R

</mi>

<mrow>
<msup>
<mi>

C

</mi>

<mo mathvariant="normal" lspace="0em" rspace="0em">

′

</mo>
</msup>

<mo>

×

</mo>

<mi>

C

</mi>
</mrow>
</msup>
</mrow>

<annotation encoding="application/x-tex">

\mathbf{W}_v \in \mathbb{R}^{C' \times C}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8361em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathbf" style="margin-right:0.016em;">

W

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.016em;margin-right:0.05em;">
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

∈

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.9425em;">



</span>

<span className="mord">
<span className="mord,mathbb">

R

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.9425em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0715em;">

C

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8278em;">
<span style="top:-2.931em;margin-right:0.0714em;">
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

<span className="mbin,mtight">

×

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0715em;">

C

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>


  - Value 没有对方向、距离信息编码

##### 自注意力计算

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<msub>
<mi mathvariant="bold">

F

</mi>

<mi>

a

</mi>
</msub>

<mo>

=

</mo>

<munderover>
<mo>

∑

</mo>

<mrow>
<mi>

b

</mi>

<mo>

=

</mo>

<mn>

1

</mn>
</mrow>

<mi>

N

</mi>
</munderover>

<msub>
<mi mathvariant="bold">

A

</mi>

<mrow>
<mi>

a

</mi>

<mi>

b

</mi>
</mrow>
</msub>

<mo>

×

</mo>

<msub>
<mi mathvariant="bold">

V

</mi>

<mi>

b

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

\mathbf{F}_a = \sum_{b=1}^{N} \mathbf{A}_{ab} \times \mathbf{V}_b

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

F

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
<span className="strut" style="height:3.1304em;vertical-align:-1.3021em;">



</span>

<span className="mop,op-limits">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:1.8283em;">
<span style="top:-1.8479em;margin-left:0em;">
<span className="pstrut" style="height:3.05em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

b

</span>

<span className="mrel,mtight">

=

</span>

<span className="mord,mtight">

1

</span>
</span>
</span>
</span>

<span style="top:-3.05em;">
<span className="pstrut" style="height:3.05em;">



</span>

<span>
<span className="mop,op-symbol,large-op">

∑

</span>
</span>
</span>

<span style="top:-4.3em;margin-left:0em;">
<span className="pstrut" style="height:3.05em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
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
<span className="vlist" style="height:1.3021em;">
<span>



</span>
</span>
</span>
</span>
</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord">
<span className="mord,mathbf">

A

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

ab

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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
<span className="strut" style="height:0.8361em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathbf" style="margin-right:0.016em;">

V

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.016em;margin-right:0.05em;">
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
</span>

其中 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi mathvariant="bold">

A

</mi>

<mrow>
<mi>

a

</mi>

<mi>

b

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

\mathbf{A}_{ab}

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

A

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

ab

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

 表示 patch<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

a

</mi>
</mrow>

<annotation encoding="application/x-tex">

a

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.4306em;">



</span>

<span className="mord,mathnormal">

a

</span>
</span>
</span>
</span>

 对 patch<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

b

</mi>
</mrow>

<annotation encoding="application/x-tex">

b

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,mathnormal">

b

</span>
</span>
</span>
</span>

 之间的相关性，<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi mathvariant="bold">

V

</mi>

<mi>

b

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

\mathbf{V}_b

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8361em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathbf" style="margin-right:0.016em;">

V

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.016em;margin-right:0.05em;">
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

 表示 patch <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

b

</mi>
</mrow>

<annotation encoding="application/x-tex">

b

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,mathnormal">

b

</span>
</span>
</span>
</span>

 的表征，最终求和得到以 patch <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

a

</mi>
</mrow>

<annotation encoding="application/x-tex">

a

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.4306em;">



</span>

<span className="mord,mathnormal">

a

</span>
</span>
</span>
</span>

 为中心的相关区域的表征

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AIFrontier/AIFrontier-35.webp)

##### 卷积  vs  Transformer

- **Transformer——使用绝对编码，会污染特征**
- 为什么Transfomer还做得很好呢——**大数据，力大砖飞**

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AIFrontier/AIFrontier-36.webp)

### 七、图神经网络

- 节点表示：在图神经网络中，每个节点都会有一个向量表示，该向量捕获了与节点相关的特征信息（包括固有属性和结构性特征）
- 边表示：在图神经网络中，边的表示通常是一个向量，捕获了连接两个节点之间的关系信息（例如边的权重、类型、方向等）
- 消息传递：图神经网络的核心是消息传递机制，节点通过边向其邻居发送消息（通常是特征信息的某种变换），并基于收到的消息更新自己的状态。这 个过程通常包括
- 聚合（Aggregation）和更新（Update）两个步骤
![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AIFrontier/AIFrontier-37.webp)

## 人工智能基础历年卷
