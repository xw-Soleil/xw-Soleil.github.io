# L5：数字系统设计 Digital System Design

> CMOS 逻辑门与 RISC-V 数据通路的同步时序设计，触发器与建立/保持时间的计算

> 怎么数集阴魂不散，这一章我怎么记得他连讲都没讲（doge）

## CMOS

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L5-DSD-01.webp)

### MOS 网络

#### 反向网络

电路中的x和y呈现反向关系。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L5-DSD-02.webp)

#### 多输入网络

利用真值表可以列出输出和所有输入的关系

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 34.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L5-DSD-03.webp" />
      </p>
    </td>
    
    
      <td style="width: 65.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L5-DSD-04.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

### 逻辑门设计实例

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L5-DSD-05.webp)

> **AOI21** 中数字 **2 和 1** 表示：一个 **2 输入 AND 项**：A⋅B； 一个 **1 输入项**：C； 然后两项**OR，**最后整体取反。

## RISC-V数据路径设计 | Data Path

整个的部分主要围绕RISC-V数据路径各个部分的设计展开，包括同步电路设计，多路选择器，ALU等等。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L5-DSD-06.webp)

### 同步数字系统电路设计

同步数字系统主要由两类电路组成：组合逻辑电路和时序逻辑电路。

#### 程序计数器 | Program Counter

程序计数器用来保存**当前指令地址**。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L5-DSD-07.webp)

如果没有寄存器隔离，**当前 PC 和 PC+4 会同时出现在同一条反馈线上**，电路会不断变化<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

P

</mi>

<mi>

C

</mi>

<mo>

→

</mo>

<mi>

P

</mi>

<mi>

C

</mi>

<mo>

+

</mo>

<mn>

4

</mn>

<mo>

→

</mo>

<mi>

P

</mi>

<mi>

C

</mi>

<mo>

+

</mo>

<mn>

8

</mn>

<mo>

→

</mo>

<mi>

P

</mi>

<mi>

C

</mi>

<mo>

+

</mo>

<mn>

12

</mn>

<mo>

→

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
</mrow>

<annotation encoding="application/x-tex">

PC→PC+4→PC+8→PC+12→...

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

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

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
<span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

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

4

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
<span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

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

8

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
<span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

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

12

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
<span className="strut" style="height:0.1056em;">



</span>

<span className="mord">

...

</span>
</span>
</span>
</span>



所以要加一个**状态元件**，也就是寄存器/触发器，用来在某个时钟边沿才更新 PC。

<mark>

添加正边沿触发器

</mark>

以后，程序计数器的时序逻辑图如下。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L5-DSD-08.webp)

##### 边缘触发器 | DFF

D Flip-Flop 是时序电路中最基本的存储单元，DFF是在**时钟边沿**采样输入。

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 50.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L5-DSD-09.webp" />
      </p>
    </td>
    
    
      <td style="width: 50.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <table>
        <thead>
          <tr>
            <th>
              元件
            </th>
            
            <th>
              工作方式
            </th>
          </tr>
        </thead>
        
        <tbody>
          <tr>
            <td>
              RS latch
            </td>
            
            <td>
              对电平敏感，时钟为有效电平时可能一直变化
            </td>
          </tr>
          
          <tr>
            <td>
              DFF
            </td>
            
            <td>
              对边沿敏感，只在时钟边沿更新
            </td>
          </tr>
        </tbody>
      </table>
    </td>
  </tr>
</tbody>
</table>

###### Flip-Flop Timing

- **建立时间**（<span className="katex">
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

e

</mi>

<mi>

t

</mi>

<mi>

u

</mi>

<mi>

p

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

t_{setup}

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
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

se

</span>

<span className="mord,mathnormal,mtight">

t

</span>

<span className="mord,mathnormal,mtight">

u

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

）表示在时钟上升沿到来之前，D 输入必须提前稳定一段时间。下图中电路的建立时间为：<span className="katex">
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

s

</mi>

<mi>

e

</mi>

<mi>

t

</mi>

<mi>

u

</mi>

<mi>

p

</mi>
</mrow>
</msub>

<mo>

=

</mo>

<mn>

2

</mn>

<msub>
<mi>

T

</mi>

<mrow>
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

T

</mi>

<mrow>
<mi>

p

</mi>

<mi>

g

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

T_{setup}=2T_{inv}+T_{pg}

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

T

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:-0.1389em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

se

</span>

<span className="mord,mathnormal,mtight">

t

</span>

<span className="mord,mathnormal,mtight">

u

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
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">

2

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.1389em;">

T

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
<span className="strut" style="height:0.9694em;vertical-align:-0.2861em;">



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

p

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
- **保持时间**（<span className="katex">
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

）表示在时钟上升沿之后，D 输入还需要继续保持稳定一小段时间，在理想化 DFF 结构中，时钟边沿之后不需要额外保持时间。
- **传输延迟**（<span className="katex">
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

l

</mi>

<mi>

k

</mi>

<mo>

−

</mo>

<mi>

t

</mi>

<mi>

o

</mi>

<mo>

−

</mo>

<mi>

Q

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

t_{clk−to−Q}

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

<span className="mord,mathnormal,mtight" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0315em;">

k

</span>

<span className="mbin,mtight">

−

</span>

<span className="mord,mathnormal,mtight">

t

</span>

<span className="mord,mathnormal,mtight">

o

</span>

<span className="mbin,mtight">

−

</span>

<span className="mord,mathnormal,mtight">

Q

</span>
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

）表示时钟上升沿来了以后，Q 不会立刻变化，而是过一段时间才更新。

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 43.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L5-DSD-10.webp" />
      </p>
    </td>
    
    
      <td style="width: 56.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L5-DSD-11.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

#### 最大时钟运行速度

时钟周期必须满足：<span className="katex">
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

y

</mi>

<mi>

c

</mi>

<mi>

l

</mi>

<mi>

e

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

<mi>

l

</mi>

<mi>

k

</mi>

<mo>

−

</mo>

<mi>

t

</mi>

<mi>

o

</mi>

<mo>

−

</mo>

<mi>

Q

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

C

</mi>

<mi>

L

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

e

</mi>

<mi>

t

</mi>

<mi>

u

</mi>

<mi>

p

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

t_{cycle}≥t_{clk−to−Q}+t_{CL}+t_{setup}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
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
<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

cy

</span>

<span className="mord,mathnormal,mtight">

c

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0197em;">

l

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
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

c

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0315em;">

k

</span>

<span className="mbin,mtight">

−

</span>

<span className="mord,mathnormal,mtight">

t

</span>

<span className="mord,mathnormal,mtight">

o

</span>

<span className="mbin,mtight">

−

</span>

<span className="mord,mathnormal,mtight">

Q

</span>
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
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
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
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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
<span className="strut" style="height:0.9012em;vertical-align:-0.2861em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

t

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

se

</span>

<span className="mord,mathnormal,mtight">

t

</span>

<span className="mord,mathnormal,mtight">

u

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



![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L5-DSD-12.webp)

##### 例1 PC电路

计算最大时钟频率，最小时钟周期为：<span className="katex">
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

m

</mi>

<mi>

i

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
<mi>

t

</mi>

<mrow>
<mi>

s

</mi>

<mi>

e

</mi>

<mi>

t

</mi>

<mi>

u

</mi>

<mi>

p

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

a

</mi>

<mi>

d

</mi>

<mi>

d

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

l

</mi>

<mi>

k

</mi>

<mo>

−

</mo>

<mi>

t

</mi>

<mi>

o

</mi>

<mo>

−

</mo>

<mi>

Q

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

t_{min} = t_{setup} + t_{add} + t_{clk-to-Q}

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
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

min

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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
<span className="strut" style="height:0.9012em;vertical-align:-0.2861em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

t

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

se

</span>

<span className="mord,mathnormal,mtight">

t

</span>

<span className="mord,mathnormal,mtight">

u

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
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

a

</span>

<span className="mord,mathnormal,mtight">

dd

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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

<span className="mord,mathnormal,mtight" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0315em;">

k

</span>

<span className="mbin,mtight">

−

</span>

<span className="mord,mathnormal,mtight">

t

</span>

<span className="mord,mathnormal,mtight">

o

</span>

<span className="mbin,mtight">

−

</span>

<span className="mord,mathnormal,mtight">

Q

</span>
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



![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L5-DSD-13.webp)

例子中给出：<span className="katex">
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

e

</mi>

<mi>

t

</mi>

<mi>

u

</mi>

<mi>

p

</mi>
</mrow>
</msub>

<mo>

≥

</mo>

<mn>

15

</mn>

<mi>

p

</mi>

<mi>

s

</mi>
</mrow>

<annotation encoding="application/x-tex">

t_{setup} \geq 15ps

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
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
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

se

</span>

<span className="mord,mathnormal,mtight">

t

</span>

<span className="mord,mathnormal,mtight">

u

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

≥

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8389em;vertical-align:-0.1944em;">



</span>

<span className="mord">

15

</span>

<span className="mord,mathnormal">

p

</span>

<span className="mord,mathnormal">

s

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
<mi>

t

</mi>

<mrow>
<mi>

a

</mi>

<mi>

d

</mi>

<mi>

d

</mi>
</mrow>
</msub>

<mo>

=

</mo>

<mn>

75

</mn>

<mi>

p

</mi>

<mi>

s

</mi>
</mrow>

<annotation encoding="application/x-tex">

t_{add} = 75ps

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

a

</span>

<span className="mord,mathnormal,mtight">

dd

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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
<span className="strut" style="height:0.8389em;vertical-align:-0.1944em;">



</span>

<span className="mord">

75

</span>

<span className="mord,mathnormal">

p

</span>

<span className="mord,mathnormal">

s

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
<mi>

t

</mi>

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

−

</mo>

<mi>

t

</mi>

<mi>

o

</mi>

<mo>

−

</mo>

<mi>

Q

</mi>
</mrow>
</msub>

<mo>

≥

</mo>

<mn>

10

</mn>

<mi>

p

</mi>

<mi>

s

</mi>
</mrow>

<annotation encoding="application/x-tex">

t_{clk-to-Q} \geq 10ps

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
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

<span className="mord,mathnormal,mtight" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0315em;">

k

</span>

<span className="mbin,mtight">

−

</span>

<span className="mord,mathnormal,mtight">

t

</span>

<span className="mord,mathnormal,mtight">

o

</span>

<span className="mbin,mtight">

−

</span>

<span className="mord,mathnormal,mtight">

Q

</span>
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
<span className="strut" style="height:0.8389em;vertical-align:-0.1944em;">



</span>

<span className="mord">

10

</span>

<span className="mord,mathnormal">

p

</span>

<span className="mord,mathnormal">

s

</span>
</span>
</span>
</span>



所以：<span className="katex">
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

m

</mi>

<mi>

i

</mi>

<mi>

n

</mi>
</mrow>
</msub>

<mo>

≥

</mo>

<mn>

15

</mn>

<mi>

p

</mi>

<mi>

s

</mi>

<mo>

+

</mo>

<mn>

75

</mn>

<mi>

p

</mi>

<mi>

s

</mi>

<mo>

+

</mo>

<mn>

10

</mn>

<mi>

p

</mi>

<mi>

s

</mi>

<mo>

=

</mo>

<mn>

100

</mn>

<mi>

p

</mi>

<mi>

s

</mi>
</mrow>

<annotation encoding="application/x-tex">

t_{min} \geq 15ps + 75ps + 10ps = 100ps

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
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

min

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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
<span className="strut" style="height:0.8389em;vertical-align:-0.1944em;">



</span>

<span className="mord">

15

</span>

<span className="mord,mathnormal">

p

</span>

<span className="mord,mathnormal">

s

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
<span className="strut" style="height:0.8389em;vertical-align:-0.1944em;">



</span>

<span className="mord">

75

</span>

<span className="mord,mathnormal">

p

</span>

<span className="mord,mathnormal">

s

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
<span className="strut" style="height:0.8389em;vertical-align:-0.1944em;">



</span>

<span className="mord">

10

</span>

<span className="mord,mathnormal">

p

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
<span className="strut" style="height:0.8389em;vertical-align:-0.1944em;">



</span>

<span className="mord">

100

</span>

<span className="mord,mathnormal">

p

</span>

<span className="mord,mathnormal">

s

</span>
</span>
</span>
</span>



因此：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

f

</mi>

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

−

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
</mrow>
</msub>

<mo>

≤

</mo>

<mfrac>
<mn>

1

</mn>

<mrow>
<mn>

100

</mn>

<mi>

p

</mi>

<mi>

s

</mi>
</mrow>
</mfrac>

<mo>

=

</mo>

<mn>

10

</mn>

<mi>

G

</mi>

<mi>

H

</mi>

<mi>

z

</mi>
</mrow>

<annotation encoding="application/x-tex">

f_{clk-max} \leq \frac{1}{100ps} = 10GHz

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.9028em;vertical-align:-0.2083em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.1076em;">

f

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.1076em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

c

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0315em;">

k

</span>

<span className="mbin,mtight">

−

</span>

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

≤

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.3262em;vertical-align:-0.4811em;">



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

100

</span>

<span className="mord,mathnormal,mtight">

p

</span>

<span className="mord,mathnormal,mtight">

s

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

10

</span>

<span className="mord,mathnormal">

G

</span>

<span className="mord,mathnormal" style="margin-right:0.0813em;">

H

</span>

<span className="mord,mathnormal" style="margin-right:0.044em;">

z

</span>
</span>
</span>
</span>



##### 例2

参考图中的波形图很好理解公式的推导。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L5-DSD-14.webp)

<alert type="tip">

#### 对于图中**setup time**计算的理解

当launch path把数据传到UFF1的D输入口时，此时距离UFF1的下一个周期的上边沿的时间要大于setup time，留有足够多的裕量。

</alert>

<alert type="question">

#### 对图中 hold time 计算的理解

在 UFF1 刚刚采样完旧数据之后，新数据会不会太快到达，把旧数据破坏掉？要求新数据到达UFF1的D输入口的时间要满足 hold time 的所允许最短时间。

</alert>

#### 有限状态机 | FSM

通过逻辑和寄存器的组合，任何FSM都能在硬件中实现。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L5-DSD-15.webp)

##### 案例 | 串行通信

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L5-DSD-16.webp)

针对图中所述的要求，设计一个检测“连续3个1”的FSM，状态转换如下图：

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L5-DSD-17.webp)

<alert type="tip">

#### 对于状态机主要工作流解释：

从 **S0** 开始，说明还没检测到连续 1。
如果输入 `1`，说明看到第一个 1，所以进入 **S1**。
如果在 **S1** 又输入 `1`，说明已经看到 `11`，进入 **S2**。
如果在 **S2** 再输入 `1`，说明出现了 `111`，所以输出 `1`，表示检测成功，可开始读取wifi发送的数据了。

</alert>

### 多路选择器

#### 2 to 1 选择器

根据真值表写出逻辑表达式，化简后画出右图的具体结构。

> 好多手画，难评。。。还有就是应该用不到用真值表，直接写不更简单（doge）

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 44.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L5-DSD-18.webp" />
      </p>
    </td>
    
    
      <td style="width: 55.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L5-DSD-19.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

#### 4 to 1 多路选择器

选择项增加后可以复用前面的 2to1 选择器进行层次化设计，如右下图。

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 63.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L5-DSD-20.webp" />
      </p>
    </td>
    
    
      <td style="width: 36.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L5-DSD-21.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

> 4 to 1 多路选择器的真值表有64行。

### 算术逻辑单元 | ALU

大多数处理器都包含一个特殊的逻辑块，称为“算术和逻辑单元”(Arithmetic and Logic Unit)。

下面主要是展示一个简单的ALU，包括ADD, SUB, bitwise AND,  bitwise OR运算。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L5-DSD-22.webp)

下图是ALU整体框图：

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L5-DSD-23.webp)

#### 加法器设计

##### 1位全加器设计

半加器和全加器的真值表及逻辑表达式

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 53.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L5-DSD-24.webp" />
      </p>
    </td>
    
    
      <td style="width: 46.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L5-DSD-25.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

全加器逻辑表达式：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

s

</mi>

<mi>

i

</mi>

<mo>

=

</mo>

<mi>

X

</mi>

<mi>

O

</mi>

<mi>

R

</mi>

<mo stretchy="false">

(

</mo>

<mi>

a

</mi>

<mi>

i

</mi>

<mo separator="true">

,

</mo>

<mi>

b

</mi>

<mi>

i

</mi>

<mo separator="true">

,

</mo>

<mi>

c

</mi>

<mi>

i

</mi>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

si = XOR(ai, bi, ci)

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6595em;">



</span>

<span className="mord,mathnormal">

s

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

<span className="mord,mathnormal" style="margin-right:0.0785em;">

X

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

O

</span>

<span className="mord,mathnormal" style="margin-right:0.0077em;">

R

</span>

<span className="mopen">

(

</span>

<span className="mord,mathnormal">

ai

</span>

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord,mathnormal">

bi

</span>

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord,mathnormal">

c

</span>

<span className="mord,mathnormal">

i

</span>

<span className="mclose">

)

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
<mi>

c

</mi>

<mrow>
<mi>

i

</mi>

<mo>

+

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

M

</mi>

<mi>

A

</mi>

<mi>

J

</mi>

<mo stretchy="false">

(

</mo>

<mi>

a

</mi>

<mi>

i

</mi>

<mo separator="true">

,

</mo>

<mi>

b

</mi>

<mi>

i

</mi>

<mo separator="true">

,

</mo>

<mi>

c

</mi>

<mi>

i

</mi>

<mo stretchy="false">

)

</mo>

<mo>

=

</mo>

<msub>
<mi>

a

</mi>

<mi>

i

</mi>
</msub>

<msub>
<mi>

b

</mi>

<mi>

i

</mi>
</msub>

<mo>

+

</mo>

<msub>
<mi>

a

</mi>

<mi>

i

</mi>
</msub>

<msub>
<mi>

c

</mi>

<mi>

i

</mi>
</msub>

<mo>

+

</mo>

<msub>
<mi>

b

</mi>

<mi>

i

</mi>
</msub>

<msub>
<mi>

c

</mi>

<mi>

i

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

c_{i+1} = MAJ(ai, bi, ci) = a_i b_i + a_i c_i + b_i c_i

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

c

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
<span className="mord,mathnormal,mtight">

i

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

<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal">

A

</span>

<span className="mord,mathnormal" style="margin-right:0.0962em;">

J

</span>

<span className="mopen">

(

</span>

<span className="mord,mathnormal">

ai

</span>

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord,mathnormal">

bi

</span>

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord,mathnormal">

c

</span>

<span className="mord,mathnormal">

i

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
<span className="strut" style="height:0.8444em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

a

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

<span className="mord">
<span className="mord,mathnormal">

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.7333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

a

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

<span className="mord">
<span className="mord,mathnormal">

c

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8444em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

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

<span className="mord">
<span className="mord,mathnormal">

c

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



![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L5-DSD-26.webp)

##### N bit 加法器链

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L5-DSD-27.webp)

##### 二进制补码加法器/减法器

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L5-DSD-28.webp)

### 关键路径

在同步系统中设置时钟周期时，必须考虑到最坏的情况。

最糟糕情况的组合逻辑路径称为“关键路径(critical path)"，它可以通过“门延迟(gate delays)”的数量来估计：在最坏的情况下必须通过的门的数量。

> **ALU 的关键路径**通常是：
> 
> 最低位进位输入 → 一路穿过所有全加器 → 最高位结果 / overflow

## 处理器设计流程

1. **分析指令集**：先看处理器要支持哪些指令。
2. **确定数据通路需求**：根据指令判断需要哪些硬件，比如寄存器、ALU、内存、PC 等。
3. **选择数据通路组件并确定时钟方法**：决定用哪些组合逻辑和状态元件。
4. **组装数据通路**：把寄存器、ALU、内存、MUX 等连接起来。
5. **设计控制逻辑**：根据不同指令产生不同控制信号。

### 设计步骤1：分析指令集

#### RISC-V精简子集

> 详细可见 L4b-machinecode 这一章的讲述。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L5-DSD-29.webp)

#### 寄存器转换语言 | RTL

所有指令都先从内存中取指令，然后根据指令定义和类型执行不同操作。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L5-DSD-30.webp)

### 设计步骤2：指令集(Instruction Set)对硬件的要求

- **指令内存和数据内存**：取指令、读写数据。
- **寄存器文件**：读取 `rs1`、`rs2`，写回 `rd`。
- **PC**：保存当前指令地址。
- **符号扩展器**：把 `imm12` 扩展成 32 位。
- **ALU**：执行加、减、OR 等操作。
- **PC + 4 加法器**：顺序执行下一条指令。
- **分支比较逻辑**：判断两个寄存器是否相等。

#### 数据通路的通用结构

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L5-DSD-31.webp)

### 设计步骤3：**设计数据通路组件并确定时钟方法**

主要设计组合元素，状态元素+时钟方法以及构建块。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L5-DSD-32.webp)

#### ALU的需求

ALU需要设计加法，减法，逻辑或等算术功能。

`ADD`：加法。

`SUB`：减法。

`ORI`：按位 OR。

`BEQ`：判断两个寄存器是否相等。

也需要给定测试向量，测试ALU操作的输出是否正确。

#### 存储需求

##### 理想化内存

内存需要一个输入总线和一个输出总线。下图的内存模块的接口有：

`Address`：地址输入。

`Data In`：写入内存的数据。

`Data Out`：从内存读出的数据。

`Write Enable`：写使能。

`Clk`：时钟。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L5-DSD-33.webp)

**工作方式**：

- `Write Enable = 0`：读内存。地址有效后，经过访问时间，`Data Out` 有效。
- `Write Enable = 1`：写内存。在时钟作用下，把 `Data In` 写入指定地址。

**时钟输入**

在写操作期间，CLK输入只是一个因素；在读取操作期间，表现为一个**组合逻辑块**：地址有效后，数据会在“内存访问时间(access time)”后才有效。

##### 寄存器文件 | Register File

Register File 类似 D 触发器，但输入输出位更宽，有 N 位输入和 N 位输出，并且有 `Write Enable`。

> **Write Enable****的作用是：**
> 
> - `Write Enable = 0`：不写入，输出保持不变。
> - `Write Enable = 1`：在时钟上升沿，数据输出将变成数据输入

寄存器文件是由32个寄存器组成，包括2个32位输出总线: busA 和 busB和一个32位输入总线: busW。

**寄存器工作方式**

- RA选择要放入busA(数据)的寄存器
- RB选择要放入busB(数据)的寄存器
- 当Write Enable为1时，RW (数字)选择通过busW (数据)写入的寄存器

**时钟输入**

在写操作期间，CLK输入只是一个因素；在读操作期间，表现为一个组合逻辑块: RA或RB有效后，busA或busB在“访问时间(access time)”后才有效。

### 设计步骤4：组装数据通路

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L5-DSD-34.webp)

### 设计步骤5：**设计控制逻辑**

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L5-DSD-35.webp)
