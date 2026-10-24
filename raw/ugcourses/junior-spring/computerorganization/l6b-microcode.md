# L6b：微码处理器架构

> 微码 ROM 大小计算与单总线数据通路设计，取指-译码-执行的微指令流程举例

> 这部分的ppt和 L6a singlecycle 中的内容有很大的重合度，相同的地方就不再讲述，主要针对额外的微码设计部分进行讲解。

## 微码处理器架构

**微码处理器的核心架构**可以理解为：处理器内部不是直接用硬连线控制逻辑执行一条机器指令，而是用一段**固定存在 ROM 里的“微程序”**逐步控制数据通路完成这条指令。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L6b-Microcode-01.webp)

1. **Main Memory：主存储器**
保存的是用户程序，也就是普通机器指令，课件中称为“宏指令”，例如 x86、RISC-V 指令。
比如一条 `lw`、`add`、`jal` 都是宏指令。
2. **Datapath：数据通路**
真正执行数据操作的部分，包括 PC、寄存器堆、ALU、内存接口等。
它负责完成寄存器读写、ALU计算、访存、更新PC等实际动作。
3. **Microcode ROM：微码ROM**
保存固定的微码指令，也就是更底层的控制步骤。
一条宏指令不会一次完成，而是被拆成多条微指令执行。

### **Microcode ROM** 大小计算

ROM 地址位数：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi mathvariant="normal">

∣

</mi>

<mi>

μ

</mi>

<mi>

a

</mi>

<mi>

d

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

s

</mi>

<mi>

s

</mi>

<mi mathvariant="normal">

∣

</mi>

<mo>

=

</mo>

<mi mathvariant="normal">

∣

</mi>

<mi>

μ

</mi>

<mi>

P

</mi>

<mi>

C

</mi>

<mi mathvariant="normal">

∣

</mi>

<mo>

+

</mo>

<mi mathvariant="normal">

∣

</mi>

<mi>

o

</mi>

<mi>

p

</mi>

<mi>

c

</mi>

<mi>

o

</mi>

<mi>

d

</mi>

<mi>

e

</mi>

<mi mathvariant="normal">

∣

</mi>

<mo>

+

</mo>

<mn>

1

</mn>

<mo>

+

</mo>

<mn>

1

</mn>
</mrow>

<annotation encoding="application/x-tex">

|\mu address| = |\mu PC| + |opcode| + 1 + 1

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

<span className="mord,mathnormal">

μ

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal">

dd

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal">

ess

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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord">

∣

</span>

<span className="mord,mathnormal">

μ

</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="mord">

∣

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

∣

</span>

<span className="mord,mathnormal">

o

</span>

<span className="mord,mathnormal">

p

</span>

<span className="mord,mathnormal">

co

</span>

<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord">

∣

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
<span className="strut" style="height:0.7278em;vertical-align:-0.0833em;">



</span>

<span className="mord">

1

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

，后面两个“1”是指分支预测结果和存储器是否忙。

ROM 每行数据位数：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi mathvariant="normal">

∣

</mi>

<mi>

d

</mi>

<mi>

a

</mi>

<mi>

t

</mi>

<mi>

a

</mi>

<mi mathvariant="normal">

∣

</mi>

<mo>

=

</mo>

<mi mathvariant="normal">

∣

</mi>

<mi>

μ

</mi>

<mi>

P

</mi>

<mi>

C

</mi>

<mi mathvariant="normal">

∣

</mi>

<mo>

+

</mo>

<mi mathvariant="normal">

∣

</mi>

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

r

</mi>

<mi>

o

</mi>

<mi>

l

</mi>

<mi>

s

</mi>

<mi>

i

</mi>

<mi>

g

</mi>

<mi>

n

</mi>

<mi>

a

</mi>

<mi>

l

</mi>

<mi>

s

</mi>

<mi mathvariant="normal">

∣

</mi>
</mrow>

<annotation encoding="application/x-tex">

|data| = |\mu PC| + |control signals|

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

<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal">

a

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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord">

∣

</span>

<span className="mord,mathnormal">

μ

</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="mord">

∣

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

∣

</span>

<span className="mord,mathnormal">

co

</span>

<span className="mord,mathnormal">

n

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal">

o

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

s

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

g

</span>

<span className="mord,mathnormal">

na

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

s

</span>

<span className="mord">

∣

</span>
</span>
</span>
</span>



![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L6b-Microcode-02.webp)

#### **单总线Microcoded RISC-V ROM大小**

指令获取序列包含3个常用步骤，大约12个指令组，每组约5步(1步调度)，一共是 3+12*5 = 63 步，因此<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

μ

</mi>

<mi>

P

</mi>

<mi>

C

</mi>
</mrow>

<annotation encoding="application/x-tex">

\mu PC

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8778em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal">

μ

</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>
</span>
</span>
</span>



需要用6位来表示，操作码(opcode)有5位，大约18个控制信号(control signal)。

因此<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi mathvariant="normal">

∣

</mi>

<mi>

d

</mi>

<mi>

a

</mi>

<mi>

t

</mi>

<mi>

a

</mi>

<mi mathvariant="normal">

∣

</mi>

<mo>

=

</mo>

<mi mathvariant="normal">

∣

</mi>

<mi>

μ

</mi>

<mi>

P

</mi>

<mi>

C

</mi>

<mi mathvariant="normal">

∣

</mi>

<mo>

+

</mo>

<mi mathvariant="normal">

∣

</mi>

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

r

</mi>

<mi>

o

</mi>

<mi>

l

</mi>

<mi>

s

</mi>

<mi>

i

</mi>

<mi>

g

</mi>

<mi>

n

</mi>

<mi>

a

</mi>

<mi>

l

</mi>

<mi>

s

</mi>

<mi mathvariant="normal">

∣

</mi>

<mo>

=

</mo>

<mn>

6

</mn>

<mo>

+

</mo>

<mn>

18

</mn>

<mo>

=

</mo>

<mn>

24

</mn>
</mrow>

<annotation encoding="application/x-tex">

|data| = |\mu PC| + |control signals| = 6 + 18 = 24

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

<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal">

a

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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord">

∣

</span>

<span className="mord,mathnormal">

μ

</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="mord">

∣

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

∣

</span>

<span className="mord,mathnormal">

co

</span>

<span className="mord,mathnormal">

n

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal">

o

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

s

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

g

</span>

<span className="mord,mathnormal">

na

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

s

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
<span className="strut" style="height:0.7278em;vertical-align:-0.0833em;">



</span>

<span className="mord">

6

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

18

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

24

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
<mi mathvariant="normal">

∣

</mi>

<mi>

μ

</mi>

<mi>

a

</mi>

<mi>

d

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

s

</mi>

<mi>

s

</mi>

<mi mathvariant="normal">

∣

</mi>

<mo>

=

</mo>

<mi mathvariant="normal">

∣

</mi>

<mi>

μ

</mi>

<mi>

P

</mi>

<mi>

C

</mi>

<mi mathvariant="normal">

∣

</mi>

<mo>

+

</mo>

<mi mathvariant="normal">

∣

</mi>

<mi>

o

</mi>

<mi>

p

</mi>

<mi>

c

</mi>

<mi>

o

</mi>

<mi>

d

</mi>

<mi>

e

</mi>

<mi mathvariant="normal">

∣

</mi>

<mo>

+

</mo>

<mn>

1

</mn>

<mo>

+

</mo>

<mn>

1

</mn>

<mo>

=

</mo>

<mn>

6

</mn>

<mo>

+

</mo>

<mn>

5

</mn>

<mo>

+

</mo>

<mn>

2

</mn>

<mo>

=

</mo>

<mn>

13

</mn>
</mrow>

<annotation encoding="application/x-tex">

|\mu address| = |\mu PC| + |opcode| + 1 + 1 = 6 + 5 + 2 = 13

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

<span className="mord,mathnormal">

μ

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal">

dd

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal">

ess

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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord">

∣

</span>

<span className="mord,mathnormal">

μ

</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="mord">

∣

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

∣

</span>

<span className="mord,mathnormal">

o

</span>

<span className="mord,mathnormal">

p

</span>

<span className="mord,mathnormal">

co

</span>

<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord">

∣

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
<span className="strut" style="height:0.7278em;vertical-align:-0.0833em;">



</span>

<span className="mord">

1

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

6

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
<span className="strut" style="height:0.7278em;vertical-align:-0.0833em;">



</span>

<span className="mord">

5

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

2

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

13

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

R

</mi>

<mi>

O

</mi>

<mi>

M

</mi>

<mo>

=

</mo>

<msup>
<mn>

2

</mn>

<mrow>
<mi mathvariant="normal">

∣

</mi>

<mi>

μ

</mi>

<mi>

a

</mi>

<mi>

d

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

s

</mi>

<mi>

s

</mi>

<mi mathvariant="normal">

∣

</mi>
</mrow>
</msup>

<mo>

×

</mo>

<mi mathvariant="normal">

∣

</mi>

<mi>

d

</mi>

<mi>

a

</mi>

<mi>

t

</mi>

<mi>

a

</mi>

<mi mathvariant="normal">

∣

</mi>

<mo>

=

</mo>

<msup>
<mn>

2

</mn>

<mn>

13

</mn>
</msup>

<mo>

×

</mo>

<mn>

24

</mn>

<mo>

=

</mo>

<mn>

196608

</mn>

<mi>

b

</mi>

<mi>

i

</mi>

<mi>

t

</mi>

<mi>

s

</mi>

<mo>

=

</mo>

<mn>

24

</mn>

<mi>

K

</mi>

<mi>

i

</mi>

<mi>

B

</mi>
</mrow>

<annotation encoding="application/x-tex">

ROM = 2^{|\mu address|} × |data| = 2^{13} × 24 = 196608 bits = 24 KiB

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

<span className="mord,mathnormal" style="margin-right:0.0278em;">

O

</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

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
<span className="strut" style="height:1.0213em;vertical-align:-0.0833em;">



</span>

<span className="mord">
<span className="mord">

2

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

∣

</span>

<span className="mord,mathnormal,mtight">

μ

</span>

<span className="mord,mathnormal,mtight">

a

</span>

<span className="mord,mathnormal,mtight">

dd

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal,mtight">

ess

</span>

<span className="mord,mtight">

∣

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

×

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord">

∣

</span>

<span className="mord,mathnormal">

d

</span>

<span className="mord,mathnormal">

a

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal">

a

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
<span className="strut" style="height:0.9474em;vertical-align:-0.0833em;">



</span>

<span className="mord">
<span className="mord">

2

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

13

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

×

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.6444em;">



</span>

<span className="mord">

24

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
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord">

196608

</span>

<span className="mord,mathnormal">

bi

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal">

s

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

<span className="mord">

24

</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

K

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mord,mathnormal" style="margin-right:0.0502em;">

B

</span>
</span>
</span>
</span>
</span>

## 微码RISC-V单总线数据通路

整个数据通路内部主要靠**一条总线**传数据，所以一次只能完成比较简单的寄存器传输操作，比如下面这三种操作：

```text
//写入寄存器传输的微指令:
MA := PC             
B := Reg[rs2]
Reg[rd] := A + B
```

`MA := PC` 意思是把 PC 的值送到总线上，再加载到 Memory Address Register，也就是**内存地址寄存器 MA** 中。

`B := Reg[rs2]`意思是从寄存器堆中读出 `rs2`，送到总线上，再加载到 B 寄存器。

`Reg[rd] := A + B`意思是 ALU 对 A 和 B 做加法，然后把结果写回 `rd` 寄存器。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L6b-Microcode-03.webp)

<alert type="tip">

在单总线数据通路中，**PC**被当作 Register RAM 中的**特殊寄存器**来存放，上图设计中PC寄存器是作为 Register RAM 额外的第**32号寄存器**。

**32(PC)**输入信号表示存放PC的寄存器编号32，这个信号一般会固定为100000，表示选择第32号寄存器，可以进行后续的**读/写操作**。

</alert>

## 纯ROM的内容

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L6b-Microcode-04.webp)

### 案例解释

#### **对于****fetch0: MA, A := PC -> fetch1****微指令的数据通路解释**：

该指令表示把 PC 的值同时送入 MA 和 A，然后进入 fetch1。

1. **RegSel 选择 PC**

图中 Register RAM 里面既有普通寄存器，也有 PC。PC 通常被看成一个特殊寄存器，比如地址编号为 32。

所以控制信号设置为：`RegSel = PC`，表示从寄存器堆中选中 PC。

1. **RegEn 打开寄存器输出**

让 PC 的值从 Register RAM 输出到单总线：`Bus := PC`

1. **MALd = 1**

允许 Memory Address Register (MA) 从总线加载 PC：`MA := PC`。这一步是为了告诉主存“我要访问 **PC 指向的地址**”。

1. **ALd = 1**

ALU 前面的 A 寄存器也从总线加载 PC 的值：`A := PC`

这一步的目的：先把旧 PC 保存到 ALU 的 A 输入端，后面用来计算`PC + 4`或 `PC+offset`

> 注意，**A := PC**和**MA:= PC**这两个动作可以在同一个周期完成，因为它们都是从总线上读PC，不冲突。

#### **对于****fetch1: Busy=1 -> fetch1****的理解**

如果 Main Memory 还没有准备好数据，即输入`busy=1`，就不要进入下一步，继续等待。

#### 对于`fetch0:IR := Mem -> fetch2`的理解

Main Memory 准备好数据，先`Bus := Mem[PC]`，然后`IR := Bus`，把PC地址的指令传给了指令寄存器**IR**，然后进入fetch2。

#### 后续微指令

后续就根据opcode等指令格式和操作要求，依次完成相应寄存器操作，比如图中给出的ADD指令的取指后续微指令执行流程：`fetch2->ALU0->ALU1->ALU2`

## 微码程序草图

> 微码就像处理器内部执行机器指令的小程序，每条机器指令对应一段微码流程。

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 47.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L6b-Microcode-05.webp" />
      </p>
    </td>
    
    
      <td style="width: 52.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L6b-Microcode-06.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

### 公共的取指令流程

`MA, A := PC`

`PC := A + 4`

`wait for memory`

`IR := Mem`

`dispatch on opcode`

**含义**：先用 PC 作为地址去主存取指令，同时把 PC 保存到 A 中。然后 PC 加 4，准备指向下一条指令。等内存返回指令后，把指令放入 IR，也就是指令寄存器。最后根据 opcode 分发到不同指令的微码入口。

### ALU 类微指令

`A := Reg[rs1]`

`B := Reg[rs2]`

`Reg[rd] := ALUOp(A,B)`

`goto instruction fetch`

上述是普通 R 型指令的流程，实现一些运算操作，例如 `add`、`sub`、`and`、`or`。

### ALUI 类微指令

`A := Reg[rs1]`

`B := ImmI`

`Reg[rd] := ALUOp(A,B)`

`goto instruction fetch`

**ALUI** 类指令和 **ALU** 类指令类似，只是第二个操作数不是 `rs2`，而是立即数。

### LW 微指令

`A := Reg[rs1]`

`B := ImmI`

`MA := A + B`

`wait for memory`

`Reg[rd] := Mem`

`goto instruction fetch`

**含义**：先读出基地址寄存器 `rs1`，再取立即数偏移 `ImmI`，然后用 ALU 计算访存地址

### JAL 指令

<mark>

`A := PC`

</mark>

           <mark>

这一条是我添加的，不然

</mark>

<mark>

`A := A - 4`

</mark>

<mark>

有点莫名其妙，大家也可以查一下。

</mark>



`Reg[rd] := A`

`A := A - 4`

`B := ImmJ`

`PC := A + B`

`goto instruction fetch`

**含义**：在取指阶段，PC 已经被加了 4，所以 A 里面保存的是返回地址，也就是 `PC + 4`。

因此，`Reg[rd] := A`，就是把返回地址写入 `rd`。然后`A := A - 4`是恢复原来的 PC。

最后`PC := A + B`，也就是`PC = 原PC + JAL立即数`

### Branch 指令

`A := Reg[rs1]`

`B := Reg[rs2]`

`if (!ALUOp(A,B)) goto instruction fetch`

`A := PC`

`A := A - 4`

`B := ImmB`

`PC := A + B`

`goto instruction fetch`

**含义**：先比较两个寄存器。如果分支条件不成立，就直接去取下一条指令。如果条件成立，就计算分支目标地址。

这里同样要 `A := A - 4`，因为 PC 已经在取指阶段加过 4，所以要先恢复原 PC，再加上分支偏移量。

## 减少控制代码存储空间

**减少ROM高度(地址位宽)**：使用外部逻辑来**合并输入**信号；通过**分组操作码**来减少状态数量

**减少ROM宽度(数据位宽)**：限制**μPC编码**(下一步，调度，等待内存，…)；**编码控制**信号(垂直微编码、纳型编码)

## 单总线RISC-V微码引擎

> 单总线控制逻辑设计

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L6b-Microcode-07.webp)

### µPC跳跃类型

`next,下一步`：表示执行下一条微指令，也就是`µPC := µPC + 1`

`spin,自旋`：表示等待内存。如果内存还忙，就停在当前微指令；如果内存准备好，再继续。

`fetch,读取`：表示跳回取指令流程，开始下一条宏指令。

`dispatch,指令分发`：表示根据 opcode 跳转到对应指令组的入口，例如 ALU、LW、Branch。

`ftrue / ffalse`：表示根据条件判断结果跳转，主要用于分支指令。

### 已编码的ROM内容

与前面纯ROM的内容相比，下面已编码的ROM内容用更紧凑的编码方式存储微码，减少 ROM 的浪费。

此时的ROM的Address只剩下`µPC`，Data中包括`Control Lines`和`Next µPC`

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L6b-Microcode-08.webp)

其中 `Branch2` 的 `ffalse` 表示：如果分支条件为假，就直接回到取指阶段；如果条件为真，就继续执行后面的分支目标地址计算。

### 复杂指令的实现

下面是以存储器-存储器加法为例，演示微码执行流程。

先读第一个内存操作数到 A，再读第二个内存操作数到 B，然后 ALU 相加，最后把结果写回内存。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L6b-Microcode-09.webp)

通过上述流程可以显示出微码的一个重要优势：**实现复杂指令很方便。**通常**不需要修改数据通路**，只需要增加一段微码即可实现**。**

### 水平vs垂直µ码

#### 水平微码

水平微码的**特点**是：

- 微指令很**宽**
- 每条微指令可以同时控制**多个硬件动作**
- 执行步骤**少**，但是编码稀疏，占用 **ROM 位数多**

例如一条水平微指令可能同时控制寄存器选择、ALU操作、写回、地址加载等多个信号。

> **优点**是速度较快，因为一步能做很多事。**缺点**是每条微指令很长，ROM 宽度大。

#### 垂直微码

垂直微码的特点是：

- 微指令**较窄**
- 控制信号经过**编码**
- 通常一条微指令只做**一个较简单**的数据通路操作
- 执行步骤**更多**，但是**更节省** ROM 空间

> **优点**是 ROM 更小。**缺点**是执行同一条宏指令可能需要更多微步骤。

### 纳码

纳码可以理解为一种**两级微码结构**。

普通微码中有很多重复的控制信号模式，比如：`ALU0:  A ← Reg[rs1]`和`ALUI0: A ← Reg[rs1]`，虽然属于不同指令，但**控制信号模式可能完全一样**。如果每次都在微码 ROM 里存完整控制信号，就会浪费空间。

#### 纳码工作构成

<mark>

µcode ROM 负责流程控制和给出 nanoaddress；nanoinstruction ROM 负责输出真正的控制信号。

</mark>



![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L6b-Microcode-10.webp)

微码 ROM：决定下一步去哪、使用哪种控制模式
纳指令 ROM：保存具体控制信号模板

这样重复的控制信号模式只需要在纳指令 ROM 中存一份，不用在每条微码里重复存。

> #### 案例
> 
> Motorola 68000 的例子：
> 
> 17位 µcode，其中可以包含10位µ跳转或者9位纳指令指针
> 纳指令宽 68位，解码后可产生 196个控制信号

## 可写控制存储 | Writable Control Store

六七十年代半导体 ROM/RAM 变得可用，控制存储不一定非要用老式只读结构，于是出现了基于RAM的**可写控制存储(WCS)** (应用案例：B1700, QMachine, Intel i432，…)

**可写控制存储(WCS)**可以理解为把原来存在 ROM 里的微码，改成存在**高速 RAM** 里。这样微码不再是出厂后完全固定的，而是可以被加载、修改、更新。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L6b-Microcode-11.webp)

<mark>

**其他剩余部分和L6a singlecycle章节的内容完全重合，不再赘述。**

</mark>
