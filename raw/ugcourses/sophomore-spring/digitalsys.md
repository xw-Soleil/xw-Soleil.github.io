# 数字系统设计

> ISEE:贱狗，折磨自己吧！

Wbx Sxw Wjy

## 数字系统概念题

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalSys/DigitalSys-01.webp)

### 历年题汇总

#### 22-23春夏

1. 多个三态门电路的输出可以直接并联，实现逻辑与（❌）

> 要OC门或者OD门，考察实现线与的方式

1. 如果一个译码器有十六个输出，那么需要三个输入端（❌）

> <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msup>
> <mn>
> 
> 2
> 
> </mn>
> 
> <mn>
> 
> 3
> 
> </mn>
> </msup>
> 
> <mo>
> 
> =
> 
> </mo>
> 
> <mn>
> 
> 8
> 
> </mn>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> 2^3=8
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:0.8141em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> <span className="mord">
> 
> 2
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t">
> <span className="vlist-r">
> <span className="vlist" style="height:0.8141em;">
> <span style="top:-3.063em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mtight">
> 
> 3
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
> 8
> 
> </span>
> </span>
> </span>
> </span>
> 
> 所以要四个输入端

1. TTL门悬空相当于输入高电平，CMOS门悬空相当于输入低电平（❌）

> CMOS门不可以悬空

1. 电路测试时，SA0和SA1故障模型可以覆盖所有的故障（❌）

> **"所有"**显然错误

1. 单稳态触发器暂稳态的时长取决于触发脉冲的宽度（❌）

> <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <mi>
> 
> T
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
> R
> 
> </mi>
> 
> <mi>
> 
> C
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
> n
> 
> </mi>
> 
> <mn>
> 
> 3
> 
> </mn>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> T=RCln3
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
> <span className="mord,mathnormal" style="margin-right:0.1389em;">
> 
> T
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
> <span className="strut" style="height:0.6944em;">
> 
> 
> 
> </span>
> 
> <span className="mord,mathnormal" style="margin-right:0.0077em;">
> 
> R
> 
> </span>
> 
> <span className="mord,mathnormal" style="margin-right:0.0715em;">
> 
> C
> 
> </span>
> 
> <span className="mord,mathnormal" style="margin-right:0.0197em;">
> 
> l
> 
> </span>
> 
> <span className="mord,mathnormal">
> 
> n
> 
> </span>
> 
> <span className="mord">
> 
> 3
> 
> </span>
> </span>
> </span>
> </span>
> 
> ，取决于电路本身的参数

1. <mark>

设计可测试性的重要特性包括高的

</mark>

<mark>

**可靠性**

</mark>

<mark>

和高的观察性（❌）

</mark>

> 是**可控性**不是可靠性
> 
> 可控性：表示只用一个输入向量就可以使一个电路节点进入某一指定状态的难易程度，如果可以，说明容易**控制**
> 
> 可观察性：表示在输出引线上观察一个节点值的难易程度

1. TTL和CMOS的**与非门**的多余输入端均可通过电阻接电源端（✅）

> 注意是与非门，电阻接电源就是相当于高电平，接入“1”对于与非门而言不影响，但是注意如果是或非门等等其他的就有影响了

1. <mark>

双稳态触发器和施密特触发器是常用的脉冲信号整形电路（❌）

</mark>

> 注意，<mark>
> 
> **双稳态触发器（Flip-Flop）**
> 
> </mark>
> 
> **和**<mark>
> 
> **施密特触发器（Trigger）**
> 
> </mark>
> 
> 不一样！这题考的就是对于由于翻译原因都叫触发器的两种不同触发器的区别，只有施密特触发器的这种Trigger才有整形作用

1. 在Verilog中，信号赋值语句按程序列出的顺序依次执行（❌）

> **非阻塞赋值**就不是按顺序，是并行的

1. 流水线操作算法结构一定比并行算法结构所需要的运行时间少（❌）

> 可以理解为CPU（流水线）和GPU（并行）这两者之间的区别，要根据具体处理任务的类型来进行区分

1. PROM的与阵列是全译码不可编程阵列（✅）

> 全译码(<span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msup>
> <mn>
> 
> 2
> 
> </mn>
> 
> <mi>
> 
> n
> 
> </mi>
> </msup>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> 2^n
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:0.6644em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> <span className="mord">
> 
> 2
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t">
> <span className="vlist-r">
> <span className="vlist" style="height:0.6644em;">
> <span style="top:-3.063em;margin-right:0.05em;">
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
> </span>
> </span>
> </span>
> </span>
> </span>
> </span>
> </span>
> 
> )与阵列是可以做到的，但是与阵列不可编程（只能用一次，烧进去了里面结构就不能改了）
> 
> 但是**或阵列可以编程**

1. 目前所有产品数字部件都提供边界扫描（❌）

> **"所有"**显然错误
> 
> 边界扫描：把各部件的输入输出引线连成一条串联的扫描链

1. 一条微指令的有效持续时间为两个系统基本周期（❌）

> **机器周期就是系统周期**，一个系统周期可以有多个时钟周期，所以有效持续时间为**一个**系统基本周期

1. <mark>

异步触发信号在整个时钟周期有效，无论时钟电平是高电平还是低电平（❌助教认为没问题是✅的）

</mark>

> ![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalSys/DigitalSys-02.webp)

1. 内建自测试技术可以实现由电路自己决定所得到的测试结果是否正确（✅）

> ![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalSys/DigitalSys-03.webp)
> 
> (补充讲义p50)

#### 21-22春夏

1、在不影响逻辑功能的情况下，CMOS 与非门的多余输入端可通过电阻接地（❌）

> CMOS接地的话，不管电阻有多大，输入端都看作0，与非门接0输出肯定是1，所以废了，不可以

2、组合逻辑电路中产生竞争冒险的主要原因是输入信号受到尖峰干扰（❌）

> 冒险的定义是<mark>
> 
> 逻辑门因输入端的竞争而导致输出产生不应有的
> 
> </mark>
> 
> <mark>
> 
> **尖峰干扰脉冲**
> 
> </mark>
> 
> <mark>
> 
> 的现象
> 
> </mark>
> 
> ，所以题目的尖峰干扰是结果但不是原因
> 
> - 竞争
> 
> 当信号通过导线和逻辑门电路时，将产生**时间延迟**。在组合逻辑电路中，不同信号经过不同长度的导线和不同级数的逻辑门电路，**到达另一个门的输入端的时刻会有先有后的现象**
> 
> - 冒险
> 
> 逻辑门因输入端的竞争而导致输出产生不应有的**尖峰干扰脉冲**的现象
> 
> 冒险的前提是输入端产生了竞争，但并不是是所有的竞争都会产生冒险（即有竞争不一定有冒险，但有冒险就一定存在竞争）

3、只使用与非门的逻辑电路不是时序逻辑电路（❌）

> 最基本的RS触发器不就是用与非门搭出来的吗？所以这个是错误的，可以是时序电路

4、只有一个变量不同的两个最大项的乘积等于各相同变量之和（✅）

> <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <mo stretchy="false">
> 
> (
> 
> </mo>
> 
> <mi>
> 
> A
> 
> </mi>
> 
> <mo>
> 
> +
> 
> </mo>
> 
> <mi>
> 
> B
> 
> </mi>
> 
> <mo stretchy="false">
> 
> )
> 
> </mo>
> 
> <mo stretchy="false">
> 
> (
> 
> </mo>
> 
> <mi>
> 
> A
> 
> </mi>
> 
> <mo>
> 
> +
> 
> </mo>
> 
> <mover accent="true">
> <mi>
> 
> B
> 
> </mi>
> 
> <mo>
> 
> ˉ
> 
> </mo>
> </mover>
> 
> <mo stretchy="false">
> 
> )
> 
> </mo>
> 
> <mo>
> 
> =
> 
> </mo>
> 
> <mi>
> 
> A
> 
> </mi>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> (A+B)(A+\bar B)=A
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
> <span className="mopen">
> 
> (
> 
> </span>
> 
> <span className="mord,mathnormal">
> 
> A
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
> <span className="mord,mathnormal" style="margin-right:0.0502em;">
> 
> B
> 
> </span>
> 
> <span className="mclose">
> 
> )
> 
> </span>
> 
> <span className="mopen">
> 
> (
> 
> </span>
> 
> <span className="mord,mathnormal">
> 
> A
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
> <span className="strut" style="height:1.0701em;vertical-align:-0.25em;">
> 
> 
> 
> </span>
> 
> <span className="mord,accent">
> <span className="vlist-t">
> <span className="vlist-r">
> <span className="vlist" style="height:0.8201em;">
> <span style="top:-3em;">
> <span className="pstrut" style="height:3em;">
> 
> 
> 
> </span>
> 
> <span className="mord,mathnormal" style="margin-right:0.0502em;">
> 
> B
> 
> </span>
> </span>
> 
> <span style="top:-3.2523em;">
> <span className="pstrut" style="height:3em;">
> 
> 
> 
> </span>
> 
> <span className="accent-body" style="left:-0.1667em;">
> <span className="mord">
> 
> ˉ
> 
> </span>
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
> <span className="strut" style="height:0.6833em;">
> 
> 
> 
> </span>
> 
> <span className="mord,mathnormal">
> 
> A
> 
> </span>
> </span>
> </span>
> </span>
> 
> ，由代入定理，A可以换成别的变量和，所以正确

5、一个三态门可以通过使能电平控制实现输入或输出双向数据传输（❌）

> 一个三态门肯定是不行，这个是和传输门混淆了，传输门的结构是两个CMOS，一个通一个不通
> 
> ![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalSys/DigitalSys-04.webp)
> 
> 真要实现传输门需要两个三态门

6、因为 EPROM 属于只读存储器，所以正常工作时无法对它进行写操作（✅）

> ROM(Read Only Memory)肯定是只读存储器，所以正常工作时无法对它进行写操作

7、单稳态触发器有一个稳定状态，两个暂稳状态（❌）

> 单稳态触发器一个稳态**一个暂稳态**
> 
> 多谐振荡电路是两个暂稳态
> 
> 施密特触发器两个稳态

8、固0和固1故障模型可以覆盖所有开路固定故障和短路固定故障（❌）

> 前面出现过

9、逻辑函数化简中无关项、任意项可以为0或1，约束项一般只能取0值（❌）

> 约束项只能是0，任意项可以是0或1，无关项包括了约束项和任意项，所以当无关项是约束项的时候，就不能是0或1了，所以这题是错的

10、将 JK 触发器的两个输入端连在一起作为 D 端就可以构成 D 触发器（❌）

> K还要加一个非门注意JK触发器，<span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msup>
> <mi>
> 
> Q
> 
> </mi>
> 
> <mo lspace="0em" rspace="0em">
> 
> ∗
> 
> </mo>
> </msup>
> 
> <mo>
> 
> =
> 
> </mo>
> 
> <mi>
> 
> J
> 
> </mi>
> 
> <mover accent="true">
> <mi>
> 
> Q
> 
> </mi>
> 
> <mo>
> 
> ˉ
> 
> </mo>
> </mover>
> 
> <mo>
> 
> +
> 
> </mo>
> 
> <mover accent="true">
> <mi>
> 
> K
> 
> </mi>
> 
> <mo>
> 
> ˉ
> 
> </mo>
> </mover>
> 
> <mi>
> 
> Q
> 
> </mi>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> Q^{*}=J\bar Q+\bar KQ
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:0.8831em;vertical-align:-0.1944em;">
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
> <span className="vlist-t">
> <span className="vlist-r">
> <span className="vlist" style="height:0.6887em;">
> <span style="top:-3.063em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mtight">
> <span className="mord,mtight">
> 
> ∗
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
> <span className="strut" style="height:1.0145em;vertical-align:-0.1944em;">
> 
> 
> 
> </span>
> 
> <span className="mord,mathnormal" style="margin-right:0.0962em;">
> 
> J
> 
> </span>
> 
> <span className="mord,accent">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.8201em;">
> <span style="top:-3em;">
> <span className="pstrut" style="height:3em;">
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
> 
> <span style="top:-3.2523em;">
> <span className="pstrut" style="height:3em;">
> 
> 
> 
> </span>
> 
> <span className="accent-body" style="left:-0.1667em;">
> <span className="mord">
> 
> ˉ
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
> <span className="vlist" style="height:0.1944em;">
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
> <span className="strut" style="height:1.0145em;vertical-align:-0.1944em;">
> 
> 
> 
> </span>
> 
> <span className="mord,accent">
> <span className="vlist-t">
> <span className="vlist-r">
> <span className="vlist" style="height:0.8201em;">
> <span style="top:-3em;">
> <span className="pstrut" style="height:3em;">
> 
> 
> 
> </span>
> 
> <span className="mord,mathnormal" style="margin-right:0.0715em;">
> 
> K
> 
> </span>
> </span>
> 
> <span style="top:-3.2523em;">
> <span className="pstrut" style="height:3em;">
> 
> 
> 
> </span>
> 
> <span className="accent-body" style="left:-0.1944em;">
> <span className="mord">
> 
> ˉ
> 
> </span>
> </span>
> </span>
> </span>
> </span>
> </span>
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
> ，JK俩要是直接接一块了，那直接变成T异或Q了，那就是T触发器了

11、门电路内部三极管作为开关使用时，要提高开关速度，可以增加饱和深度（❌）

> 现代高速数字电路（如TTL电路）会采用一些特殊设计来**避免三极管进入深度饱和**，例如使用**肖特基二极管**钳位（构成肖特基三极管），从而绕开深度饱和带来的电荷存储问题，大幅提高开关速度
> 
> ![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalSys/DigitalSys-05.webp)

12、对于一个由<mark>

与非门

</mark>

组成的 SR 锁存器，要让该锁存器<mark>

保持

</mark>

原态，输入信号应为 <mark>

S=R=1

</mark>

（✅）

> 与非门，输入端两个都是 1 的话，不影响最终输出的Q的取值，所以是保持
> 
> 如果是与非门两个输入都是0，Q和Q'都是1
> 
> 但是如果是<mark>
> 
> 或非门，那么就是两个都是0才保持
> 
> </mark>
> 
> 
> 
> 如果是或非门两个输入都是1，Q和Q'都是0

13、摩尔型时序电路的输出既与外输入也与内部状态有关（❌）

> 这是米粒型

14、64Kx16 位 E'PROM 芯片有 16 条地址线和 16 条数据线（✅）

> K是1024，64K是<span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msup>
> <mn>
> 
> 2
> 
> </mn>
> 
> <mn>
> 
> 6
> 
> </mn>
> </msup>
> 
> <mo>
> 
> ×
> 
> </mo>
> 
> <msup>
> <mn>
> 
> 2
> 
> </mn>
> 
> <mn>
> 
> 10
> 
> </mn>
> </msup>
> 
> <mo>
> 
> =
> 
> </mo>
> 
> <msup>
> <mn>
> 
> 2
> 
> </mn>
> 
> <mn>
> 
> 16
> 
> </mn>
> </msup>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> 2^6 \times 2^{10}=2^{16}
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:0.8974em;vertical-align:-0.0833em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> <span className="mord">
> 
> 2
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t">
> <span className="vlist-r">
> <span className="vlist" style="height:0.8141em;">
> <span style="top:-3.063em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mtight">
> 
> 6
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
> <span className="mspace" style="margin-right:0.2222em;">
> 
> 
> 
> </span>
> 
> <span className="mbin">
> 
> ×
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
> <span className="strut" style="height:0.8141em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> <span className="mord">
> 
> 2
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t">
> <span className="vlist-r">
> <span className="vlist" style="height:0.8141em;">
> <span style="top:-3.063em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mtight">
> <span className="mord,mtight">
> 
> 10
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
> <span className="strut" style="height:0.8141em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> <span className="mord">
> 
> 2
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t">
> <span className="vlist-r">
> <span className="vlist" style="height:0.8141em;">
> <span style="top:-3.063em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mtight">
> <span className="mord,mtight">
> 
> 16
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
> 
> 
> 
> ![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalSys/DigitalSys-06.webp)

15、数字系统的控制部件通过控制线向执行部件发出的各种控制信号称为微操作（❌）

> 数字系统的控制部件通过控制线向执行部件发出的**各种控制信号称为微命令**
> 
> **各种控制信号的和叫做微指令（指令比命令大，指令是一串命令）**
> 
> 执行部件接受微命令所执行的操作叫作**微操作**

#### 20-21春夏

1、三态门输出高阻时，其输出线上电压为高电平（❌）

> 三态门高阻态上下都断开了，可以相当于是接了一个非常大的电阻然后接地，**是不是高电平需要看剩下另一边接的是啥**，若是接TTL门电路，则可以认为是高电平，但是若接了CMOS门电路，则是接啥是啥，和电阻大小无关，还是低电平
> 
> ![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalSys/DigitalSys-07.webp)

2、逻辑式Y=(AB+ CD)'的对偶式为YD=((A+B)(C+D))'（✅）

> 对偶规则的定义： <mark>
> 
> 运算取反演，显式的0 1 反演
> 
> </mark>
> 
> 
> 
> ![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalSys/DigitalSys-08.webp)
> 
> 体现在这里面就是或变与，与变或
> 
> **和反演规则相比就是非保持不变**

3、可以通过接入滤波电容消除竞争-冒险现象且不会影响输出电压波形（❌）

> ![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalSys/DigitalSys-09.webp)
> 
> 滤波肯定波形变化

4、一个1024*4位的SRAM中基本存储单元的数量为1024个（❌）

> 1024*4个，**所以一共是4096个存储单元**
> 
> ![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalSys/DigitalSys-10.webp)

5、单稳态电路暂稳态维持时间的长短只取决于本身的参数，与触发脉冲无关（✅）

> “暂稳态维持时间”，就应该是<span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <mi>
> 
> T
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
> R
> 
> </mi>
> 
> <mi>
> 
> C
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
> n
> 
> </mi>
> 
> <mn>
> 
> 3
> 
> </mn>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> T=RCln3
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
> <span className="mord,mathnormal" style="margin-right:0.1389em;">
> 
> T
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
> <span className="strut" style="height:0.6944em;">
> 
> 
> 
> </span>
> 
> <span className="mord,mathnormal" style="margin-right:0.0077em;">
> 
> R
> 
> </span>
> 
> <span className="mord,mathnormal" style="margin-right:0.0715em;">
> 
> C
> 
> </span>
> 
> <span className="mord,mathnormal" style="margin-right:0.0197em;">
> 
> l
> 
> </span>
> 
> <span className="mord,mathnormal">
> 
> n
> 
> </span>
> 
> <span className="mord">
> 
> 3
> 
> </span>
> </span>
> </span>
> </span>
> 
> （当然这个和具体电路有关，这个只是举个栗子）
> 
> ![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalSys/DigitalSys-11.webp)
> 
> 但是暂稳态能不能到下一个稳态的状态，还是和输入<span className="katex">
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
> <mi>
> 
> I
> 
> </mi>
> </msub>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> V_I
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
> <span className="mord,mathnormal,mtight" style="margin-right:0.0785em;">
> 
> I
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
> 有关的
> 
> ![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalSys/DigitalSys-12.webp)

6、为避免状态机运行中进入未定义的状态，设计时需要对所有可能状态进行完全编码（✅）

> ![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalSys/DigitalSys-13.webp)
> 
> 其实就是为了把每一个状态都编码以确保电路能自启动，而不是“陷入”某一个状态后就没法启动了

7、在微码控制器中,微指令测试判别信息编码为“1”,表示执行这条微指令时要对系统的有关“状态标志”进行测试（✅）

> ![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalSys/DigitalSys-14.webp)

8、sa0-sa1模型可以覆盖集成电路中可能的所有故障，故将其作为一种标准模型（❌）

> 出现了无数遍了，略过了

9、任何时钟触发器状态的改变仅与时钟的动作沿到来有关（❌）

> 触发器有电平触发和边沿触发，**电平触发型触发器就和电平高低有关了**，只不过电平触发很容易产生“空翻”现象，所以一般常见的触发器都是边沿触发

10、冯诺依曼结构将程序和数据存储分别放在不同的物理存储空间,具有更好的灵活性和稳定性（❌）

> 这题有两个错误
> 
> - 冯诺依曼结构是存放到相同的物理空间
> - 具有更好的硬件效率
> - 改成哈佛就对了
> 
> 微处理器主要有两种结构，一种是<mark>
> 
> 冯诺依曼结构
> 
> </mark>
> 
> 也称普林斯顿结构，一种是<mark>
> 
> 哈佛
> 
> </mark>
> 
> 
> 
> <mark>
> 
> 结构
> 
> </mark>
> 
> ，两者的区别是前者<mark>
> 
> 将程序存储和数据存储放在同一物理存储空间
> 
> </mark>
> 
> ，后者<mark>
> 
> 将程序
> 
> </mark>
> 
> 
> 
> <mark>
> 
> 存储和数据存储分别放在不同的物理存储空间
> 
> </mark>
> 
> 。冯诺依曼结构<mark>
> 
> 具有更好的硬件效率
> 
> </mark>
> 
> ，
> 
> 哈佛结构<mark>
> 
> 具有更好的灵活性和稳定性
> 
> </mark>

11、时序电路的扫描测试和自测试都不需要外部的测试向量就可以进行（❌）

> **电路自测试并不需要外部的向量**并且可以以很高的速度进行
> 
> <mark>
> 
> 扫描测试需要外部的测试向量，但是自测试不需要
> 
> </mark>
> 
> 
> 
> ![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalSys/DigitalSys-15.webp)

12、流水线操作算法结构一定比并行算法结构所需要的运算时间少（❌）

> 出现好多遍了，略

13、不同的逻辑函数表达式其逻辑功能也不同（❌）

> 不同逻辑表达式也可以相互转化，式子不同但都是对的
> 
> 非常简单一个例子，Y=A异或B和Y=A'B+AB'就是一样的，我甚至可以加几个冗余项，也是不同式子但是功能一样

14、故障覆盖率定义为由测试序列检测到的故障总数除以电路的节点数（❌）

> 故障覆盖率定义为由测试序列检测到的故障总数<mark>
> 
> 除以电路节点数目的
> 
> </mark>
> 
> <mark>
> 
> **两倍**
> 
> </mark>
> 
> ，因为每一个节点可以发生一个 sa0 和一个 sa1 故障。

15、CMOS与非门的多余脚悬空等效于低电平（❌）

> CMOS多余脚不能悬空，对于与非门的多余脚正确的做法是把它接上电阻然后**接高电平**

#### 19-20春夏

1.十进制数“-29”用8位二进制补码表示为 11100011（✅）

> **负数的补码表示：先写出绝对值的二进制表示，在逐位取反加一**
> 
> <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <mo stretchy="false">
> 
> (
> 
> </mo>
> 
> <mn>
> 
> 29
> 
> </mn>
> 
> <msub>
> <mo stretchy="false">
> 
> )
> 
> </mo>
> 
> <mn>
> 
> 10
> 
> </mn>
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
> <mn>
> 
> 00011101
> 
> </mn>
> 
> <msub>
> <mo stretchy="false">
> 
> )
> 
> </mo>
> 
> <mn>
> 
> 2
> 
> </mn>
> </msub>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> (29)_{10}=(00011101)_2
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
> <span className="mopen">
> 
> (
> 
> </span>
> 
> <span className="mord">
> 
> 29
> 
> </span>
> 
> <span className="mclose">
> <span className="mclose">
> 
> )
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
> <span className="mord,mtight">
> 
> 10
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
> 
> 00011101
> 
> </span>
> 
> <span className="mclose">
> <span className="mclose">
> 
> )
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
> </span>
> </span>
> </span>
> 
> ，逐位取反11100010，加一11100011

2.若取 J=K’,则可仅用 J 触发器构成 D触发器（✅）

> J=k'，那么此时等于JQ'+JQ=J就是D触发器了

3.在控制器的设计中，控制时序不能有多余状态，要达到状态最简（❌）

> ![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalSys/DigitalSys-16.webp)

4.因为逻辑表达式 A+B+AB=A+B 成立，所以 AB=0（❌）

> 你让A=B=1试试？

5.任何布尔函数都可以用与非门实现（✅）

> **与非门是逻辑完全门，可以用与非门构建任何逻辑门电路**

6.静态 RAM 需要周期性刷新以保持数据（❌）

> **RAM（随机存储器）****静态RAM (SRAM** **Static Random-Access Memory****) 不需要周期性刷新来保持数据**。需要周期性刷新的是**动态RAM (DRAM** **Dynamic Random-Access Memory****)**

7.对于任何一个逻辑函数来讲，其逻辑图都是唯一的（❌）

> 一个逻辑函数描述的是输入和输出之间的关系，而逻辑图是实现这种关系的物理或图形表示。由于实现方式的多样性（可以通过代数化简、使用不同的门电路组合如与非门/或非门等），一个逻辑函数可以对应多个不同的、但在功能上等效的逻辑图。

8.拥有8个状态的计数器内部至少要含有8个触发器（❌）

> 八个状态，三个触发器，<span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msup>
> <mn>
> 
> 2
> 
> </mn>
> 
> <mn>
> 
> 3
> 
> </mn>
> </msup>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> 2^3
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:0.8141em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> <span className="mord">
> 
> 2
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t">
> <span className="vlist-r">
> <span className="vlist" style="height:0.8141em;">
> <span style="top:-3.063em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mtight">
> 
> 3
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

9.存储容量为128KX8位的RAM存储器,其地址线为7条、数据线为8条（❌）

> [【传送门】点击跳转前面题目](https://my.feishu.cn/docx/MC7VdOGUhoBBBdxTLpUc1b5cnef#doxcngiuYnxyhGywpVyvpYISZ4c)
> 
> 这题应该是<span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <mn>
> 
> 128
> 
> </mn>
> 
> <mi>
> 
> K
> 
> </mi>
> 
> <mo>
> 
> =
> 
> </mo>
> 
> <msup>
> <mn>
> 
> 2
> 
> </mn>
> 
> <mn>
> 
> 7
> 
> </mn>
> </msup>
> 
> <mo>
> 
> ×
> 
> </mo>
> 
> <msup>
> <mn>
> 
> 2
> 
> </mn>
> 
> <mn>
> 
> 10
> 
> </mn>
> </msup>
> 
> <mo>
> 
> =
> 
> </mo>
> 
> <msup>
> <mn>
> 
> 2
> 
> </mn>
> 
> <mn>
> 
> 17
> 
> </mn>
> </msup>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> 128K=2^7\times 2^{10}=2^{17}
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
> <span className="mord">
> 
> 128
> 
> </span>
> 
> <span className="mord,mathnormal" style="margin-right:0.0715em;">
> 
> K
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
> <span className="strut" style="height:0.8974em;vertical-align:-0.0833em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> <span className="mord">
> 
> 2
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t">
> <span className="vlist-r">
> <span className="vlist" style="height:0.8141em;">
> <span style="top:-3.063em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mtight">
> 
> 7
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
> <span className="mspace" style="margin-right:0.2222em;">
> 
> 
> 
> </span>
> 
> <span className="mbin">
> 
> ×
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
> <span className="strut" style="height:0.8141em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> <span className="mord">
> 
> 2
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t">
> <span className="vlist-r">
> <span className="vlist" style="height:0.8141em;">
> <span style="top:-3.063em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mtight">
> <span className="mord,mtight">
> 
> 10
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
> <span className="strut" style="height:0.8141em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> <span className="mord">
> 
> 2
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t">
> <span className="vlist-r">
> <span className="vlist" style="height:0.8141em;">
> <span style="top:-3.063em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mtight">
> <span className="mord,mtight">
> 
> 17
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
> 
> 于是**有17条地址线**，8条数据线是正确的

10..将OD门的输出端直接相连，就可以实现线与结构（❌）

> 你让输出端直接相连接下一个门电路试试？<mark>
> 
> 必须要有上拉电阻才可以
> 
> </mark>

11.同步时序电路和异步时序电路的主要区别是输出是否只与内部状态有关（❌）

> 这个属于典型的混淆概念，这个是区别摩尔型和米粒型电路的
> 应该修改表述为：同步时序电路和异步时序电路的主要区别在于，电路内部的存储单元（触发器）状态更新是否受同一个全局时钟信号的控制。

12.对于一个n变量的逻辑函数，如果它的最小项表达式由k个最小项组成，则它的最大项将由 2”-k个最大项组成（✅）

> 最小项和最大项是互补的关系
> 
> ![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalSys/DigitalSys-17.webp)
> 
> ![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalSys/DigitalSys-18.webp)

13.冯诺依曼结构相比于哈佛体系结构具有更好的灵活性和稳定性，而哈佛体系结构具有更好的硬件效率（❌）

> 反了，冯诺伊曼架构硬件效率高；哈佛架构更灵活和稳定

14.时序电路的扫描测试和自测试都不需要外部的测试向量就可以进行（❌）

> 前面出现过了

15.微处理器设计除了数据通路及控制器外，还需要设计指令集（✅）

> ![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalSys/DigitalSys-19.webp)

#### 18-19春夏

1.2019个1异或的结果再和42个0同或,得到的结果是1（✅）

> 多个异或：奇数个1则为1
> 
> <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <mi>
> 
> X
> 
> </mi>
> 
> <mo>
> 
> ⊕
> 
> </mo>
> 
> <mn>
> 
> 0
> 
> </mn>
> 
> <mo>
> 
> =
> 
> </mo>
> 
> <mi>
> 
> X
> 
> </mi>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> X \oplus 0 = X
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">
> 
> 
> 
> </span>
> 
> <span className="mord,mathnormal" style="margin-right:0.0785em;">
> 
> X
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
> ⊕
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
> <span className="strut" style="height:0.6833em;">
> 
> 
> 
> </span>
> 
> <span className="mord,mathnormal" style="margin-right:0.0785em;">
> 
> X
> 
> </span>
> </span>
> </span>
> </span>
> 
> ,所以0不影响；
> 
> <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <mi>
> 
> X
> 
> </mi>
> 
> <mo>
> 
> ⊕
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
> ⊕
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
> =
> 
> </mo>
> 
> <mover accent="true">
> <mi>
> 
> X
> 
> </mi>
> 
> <mo>
> 
> ˉ
> 
> </mo>
> </mover>
> 
> <mo>
> 
> ⊕
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
> =
> 
> </mo>
> 
> <mi>
> 
> X
> 
> </mi>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> X \oplus 1 \oplus 1 = \bar X \oplus 1 = X
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">
> 
> 
> 
> </span>
> 
> <span className="mord,mathnormal" style="margin-right:0.0785em;">
> 
> X
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
> ⊕
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
> <span className="strut" style="height:0.7278em;vertical-align:-0.0833em;">
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
> 
> <span className="mspace" style="margin-right:0.2222em;">
> 
> 
> 
> </span>
> 
> <span className="mbin">
> 
> ⊕
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
> <span className="strut" style="height:0.9034em;vertical-align:-0.0833em;">
> 
> 
> 
> </span>
> 
> <span className="mord,accent">
> <span className="vlist-t">
> <span className="vlist-r">
> <span className="vlist" style="height:0.8201em;">
> <span style="top:-3em;">
> <span className="pstrut" style="height:3em;">
> 
> 
> 
> </span>
> 
> <span className="mord,mathnormal" style="margin-right:0.0785em;">
> 
> X
> 
> </span>
> </span>
> 
> <span style="top:-3.2523em;">
> <span className="pstrut" style="height:3em;">
> 
> 
> 
> </span>
> 
> <span className="accent-body" style="left:-0.1667em;">
> <span className="mord">
> 
> ˉ
> 
> </span>
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
> ⊕
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
> <span className="strut" style="height:0.6833em;">
> 
> 
> 
> </span>
> 
> <span className="mord,mathnormal" style="margin-right:0.0785em;">
> 
> X
> 
> </span>
> </span>
> </span>
> </span>
> 
> ,所以可以用交换律消去偶数个1。
> 
> 多个同或：偶数个0则为1
> 
> <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <mi>
> 
> X
> 
> </mi>
> 
> <mo>
> 
> ⊙
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
> =
> 
> </mo>
> 
> <mi>
> 
> X
> 
> </mi>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> X \odot 1 = X
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">
> 
> 
> 
> </span>
> 
> <span className="mord,mathnormal" style="margin-right:0.0785em;">
> 
> X
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
> ⊙
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
> <span className="strut" style="height:0.6833em;">
> 
> 
> 
> </span>
> 
> <span className="mord,mathnormal" style="margin-right:0.0785em;">
> 
> X
> 
> </span>
> </span>
> </span>
> </span>
> 
> ,所以1不影响；
> 
> <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <mi>
> 
> X
> 
> </mi>
> 
> <mo>
> 
> ⊙
> 
> </mo>
> 
> <mn>
> 
> 0
> 
> </mn>
> 
> <mo>
> 
> ⊙
> 
> </mo>
> 
> <mn>
> 
> 0
> 
> </mn>
> 
> <mo>
> 
> =
> 
> </mo>
> 
> <mover accent="true">
> <mi>
> 
> X
> 
> </mi>
> 
> <mo>
> 
> ˉ
> 
> </mo>
> </mover>
> 
> <mo>
> 
> ⊙
> 
> </mo>
> 
> <mn>
> 
> 0
> 
> </mn>
> 
> <mo>
> 
> =
> 
> </mo>
> 
> <mi>
> 
> X
> 
> </mi>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> X \odot 0 \odot 0 = \bar X \odot 0 = X
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">
> 
> 
> 
> </span>
> 
> <span className="mord,mathnormal" style="margin-right:0.0785em;">
> 
> X
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
> ⊙
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
> <span className="strut" style="height:0.7278em;vertical-align:-0.0833em;">
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
> 
> <span className="mspace" style="margin-right:0.2222em;">
> 
> 
> 
> </span>
> 
> <span className="mbin">
> 
> ⊙
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
> <span className="strut" style="height:0.9034em;vertical-align:-0.0833em;">
> 
> 
> 
> </span>
> 
> <span className="mord,accent">
> <span className="vlist-t">
> <span className="vlist-r">
> <span className="vlist" style="height:0.8201em;">
> <span style="top:-3em;">
> <span className="pstrut" style="height:3em;">
> 
> 
> 
> </span>
> 
> <span className="mord,mathnormal" style="margin-right:0.0785em;">
> 
> X
> 
> </span>
> </span>
> 
> <span style="top:-3.2523em;">
> <span className="pstrut" style="height:3em;">
> 
> 
> 
> </span>
> 
> <span className="accent-body" style="left:-0.1667em;">
> <span className="mord">
> 
> ˉ
> 
> </span>
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
> ⊙
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
> <span className="strut" style="height:0.6833em;">
> 
> 
> 
> </span>
> 
> <span className="mord,mathnormal" style="margin-right:0.0785em;">
> 
> X
> 
> </span>
> </span>
> </span>
> </span>
> 
> ,所以可以用交换律消去偶数个0。
> 
> 2019个1异或得1，与42个0同或得1

2.摩尔 (Moore)型时序电路可以转化为米利(Mealy)型时序电路,反之则不行（❌）

> 可以互相转化
> 
> (Tips: Mealy → Moore的大致思路: 将不同的输入拆成不同的状态)

3.产生尖峰脉冲是因为存在竞争现象,有竞争就一定会引起尖峰脉冲（❌）

> 前面做到过类似的，但考察点不同
> 
> **竞争：**两个输入信号同时向相反的逻辑电平跳变(一个从1变为0,另一个从0变为1)的现象
> 
> **冒险：**逻辑门因输入端的竞争而导致输出产生不应有的尖峰干扰脉冲的现象
> 
> <mark>
> 
> 竞争不一定有冒险，但有冒险就一定存在竞争
> 
> </mark>
> 
> <mark>
> 
> ，竞争是因，冒险是果
> 
> </mark>

4.最小项 m3(A'BC)和m⒋(AB’C’ )具有相邻性（❌）

> 若两个最小项只有一个因子不同，则称这两个最小项具有**相邻性**。
> 
> 显然没有相邻性

5.能够实现任何逻辑函数的逻辑门类型的集合,被称为逻辑门的完全集,与非门构成了完全集（✅）

> 做到过了，不赘述

6.一个存储容量为32×4位的存储器,可以实现四输入\五输出的逻辑函数（❌）

> 32个地址，<span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <mn>
> 
> 32
> 
> </mn>
> 
> <mo>
> 
> =
> 
> </mo>
> 
> <msup>
> <mn>
> 
> 2
> 
> </mn>
> 
> <mn>
> 
> 5
> 
> </mn>
> </msup>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> 32 = 2^5
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:0.6444em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> 
> 32
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
> <span className="strut" style="height:0.8141em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> <span className="mord">
> 
> 2
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t">
> <span className="vlist-r">
> <span className="vlist" style="height:0.8141em;">
> <span style="top:-3.063em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mtight">
> 
> 5
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
> 
> ,故最大可以处理**五**输入，四输入满足要求；
> 
> 4位数据宽度，最大可以实现**四**输出，五输出不满足。

7.冯诺依曼结构使用共用的地址和数据总线,而哈佛结构使用分离的地址总线和数据总线（❌）

> <mark>
> 
> 没有很懂这个
> 
> </mark>
> 
> 
> 
> 感觉设错应该是在数据总线和地址总线都应该是独立的，不存在共用一说 √ 我们书上讲的就是冯诺依曼结构，所以两个架构离两者都是独立的
> 
> 两个结构的区别在于<mark>
> 
> **存储**
> 
> </mark>
> 
> **数据与程序在不在同一空间**

8.在不附加其他电路的情况下,JK触发器和T触发器可以相互转换（❌）

> 需要附加门电路
> 
> JK转T，不用
> 
> ![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalSys/DigitalSys-20.webp)
> 
> T转JK，需要
> 
> <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <mi>
> 
> T
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
> J
> 
> </mi>
> 
> <mover accent="true">
> <mi>
> 
> Q
> 
> </mi>
> 
> <mo>
> 
> ˉ
> 
> </mo>
> </mover>
> 
> <mo>
> 
> +
> 
> </mo>
> 
> <mi>
> 
> K
> 
> </mi>
> 
> <mi>
> 
> Q
> 
> </mi>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> T = J \bar Q + KQ
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
> <span className="mord,mathnormal" style="margin-right:0.1389em;">
> 
> T
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
> <span className="strut" style="height:1.0145em;vertical-align:-0.1944em;">
> 
> 
> 
> </span>
> 
> <span className="mord,mathnormal" style="margin-right:0.0962em;">
> 
> J
> 
> </span>
> 
> <span className="mord,accent">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.8201em;">
> <span style="top:-3em;">
> <span className="pstrut" style="height:3em;">
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
> 
> <span style="top:-3.2523em;">
> <span className="pstrut" style="height:3em;">
> 
> 
> 
> </span>
> 
> <span className="accent-body" style="left:-0.1667em;">
> <span className="mord">
> 
> ˉ
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
> <span className="vlist" style="height:0.1944em;">
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
> <span className="strut" style="height:0.8778em;vertical-align:-0.1944em;">
> 
> 
> 
> </span>
> 
> <span className="mord,mathnormal" style="margin-right:0.0715em;">
> 
> K
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
> ，这个要推导不很方便
> 
> ![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalSys/DigitalSys-21.webp)
> 
> 当然，如果是大题可以先改造成D再改其他

9.数字系统中,并行算法结构一定比流水线操作算法结构所需要的运算时间少（❌）

> “一定” + 做过多次，不赘述

10.可以用单稳态电路将不规则的矩形波变换为幅度与宽度都相同的矩形波（❌）

> <mark>
> 
> 应该用施密特触发器来整形
> 
> </mark>

11.CPU的ALU需要时钟信号协助完成运算（❌）

> ALU即算术逻辑单元（Arithmetic Logic Unit）,用于完成 CPU 内的**算术和逻辑运算**，它是一个**组合电路**，无需时钟信号协助就能完成计算(不同于时序电路，需要时钟信号)。

12.时序图、状态转换图和状态转换表都可以用来描述同一个时序逻辑电路的逻辑功能,它们之间可以相互转换 （✅）

> ![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalSys/DigitalSys-22.webp)

13.一种处理器指令架构只有一种硬件实现方式（❌）

> 可以有多种
> 
> ![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalSys/DigitalSys-23.webp)

14.在测试电路中,边界扫描电路用于测试电路板的好坏,而内建自测试电路用于测试芯片内部的好坏（❌）

> 边界扫描可以测电路板，也可以测芯片；内建自测试测芯片

15.多个三态门电路的输出可以直接并接,实现逻辑与（❌）

> 三态门不能直接线与，会烧

#### 17-18春夏

1.十进制数 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mo stretchy="false">

(

</mo>

<mn>

65

</mn>

<msub>
<mo stretchy="false">

)

</mo>

<mn>

10

</mn>
</msub>
</mrow>

<annotation encoding="application/x-tex">

(65)_{10}

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

65

</span>

<span className="mclose">
<span className="mclose">

)

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

10

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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

的余3码编码是0111 0100（❌）

> 6 + 3 = 9，5 + 3 = 8，因此余3码为1001 1000。

2.实现两个一位二进制数相加的电路叫全加器（❌）

> 如果**不考虑有来自低位的进位**将两个1位二进制数相加，称为半加。实现半加运算的电路称为**半加器**。
> 
> 在将两个多位二进制数相加时，除了最低位以外，每一位都应该**考虑来自低位的进位**，即将两个对应位的加数和来自低位的进位3个数相加。这种运算称为全加，所用的电路称为**全加器**。

3.一个标准TTL反向器的输入通过5kΩ电阻接到地，则其输出为高电平（❌）

> ![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalSys/DigitalSys-24.webp)
> 
> <span className="katex-display">
> <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
> <semantics>
> <mrow>
> <msub>
> <mi>
> 
> v
> 
> </mi>
> 
> <mi>
> 
> i
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
> <mo stretchy="false">
> 
> (
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
> c
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
> V
> 
> </mi>
> 
> <mrow>
> <mi>
> 
> b
> 
> </mi>
> 
> <mi>
> 
> e
> 
> </mi>
> </mrow>
> </msub>
> 
> <mo stretchy="false">
> 
> )
> 
> </mo>
> 
> <mo>
> 
> ×
> 
> </mo>
> 
> <mfrac>
> <msub>
> <mi>
> 
> R
> 
> </mi>
> 
> <mi>
> 
> i
> 
> </mi>
> </msub>
> 
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
> i
> 
> </mi>
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
> </mrow>
> </mfrac>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> v_i = (V_{cc} - V_{be}) \times \frac{R_i}{R_i + R_1}
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
> <span className="vlist" style="height:0.3117em;">
> <span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mathnormal,mtight">
> 
> i
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
> <span className="mord,mathnormal" style="margin-right:0.2222em;">
> 
> V
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.1514em;">
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
> cc
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
> b
> 
> </span>
> 
> <span className="mord,mathnormal,mtight">
> 
> e
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
> <span className="mclose">
> 
> )
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
> ×
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
> <span className="strut" style="height:2.1963em;vertical-align:-0.836em;">
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
> <span className="vlist" style="height:1.3603em;">
> <span style="top:-2.314em;">
> <span className="pstrut" style="height:3em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
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
> <span className="vlist" style="height:0.3117em;">
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
> i
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
> <span style="top:-3.677em;">
> <span className="pstrut" style="height:3em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
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
> <span className="vlist" style="height:0.3117em;">
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
> i
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
> <span className="vlist-s">
> 
> ​
> 
> </span>
> </span>
> 
> <span className="vlist-r">
> <span className="vlist" style="height:0.836em;">
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
> </span>
> 
> 5kΩ太大了，输入为1，输出为0
> 
> <mark>
> 
> 一般而言临界值就是2k左右，可以当结论记
> 
> </mark>

4.当时序逻辑电路存在无效循环时，该电路不能自启动（✅）

> 正确，好像也没什么可说的

5.如果要把一宽脉冲信号变换为窄脉冲，应采用施密特触发器（❌）

> 施密特触发器：
> 
> ![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalSys/DigitalSys-25.webp)
> 
> 单稳态：
> 
> ![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalSys/DigitalSys-26.webp)
> 
> 多谐：
> 
> ![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalSys/DigitalSys-27.webp)
> 
> 故此处应使用单稳态

6.莫尔（Moore）状态机的输出与电路的当前状态和输入均相关（❌）

> ![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalSys/DigitalSys-28.webp)
> 
> Mealy有关输入，Moore无关输入

7.6个触发器组成的计数器，最多可以组成128进制的计数器（❌）

> <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msup>
> <mn>
> 
> 2
> 
> </mn>
> 
> <mn>
> 
> 6
> 
> </mn>
> </msup>
> 
> <mo>
> 
> =
> 
> </mo>
> 
> <mn>
> 
> 64
> 
> </mn>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> 2^6 = 64
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:0.8141em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> <span className="mord">
> 
> 2
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t">
> <span className="vlist-r">
> <span className="vlist" style="height:0.8141em;">
> <span style="top:-3.063em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mtight">
> 
> 6
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
> 64
> 
> </span>
> </span>
> </span>
> </span>
> 
> ，最多64进制

8.微程序控制器中，若微指令长度为 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msup>
<mn>

2

</mn>

<mi>

n

</mi>
</msup>
</mrow>

<annotation encoding="application/x-tex">

2^n

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6644em;">



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

n

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

位，则微地址寄存器的长度为n位（✅）

> 微指令包含微命令、判别、下地址，<mark>
> 
> 但感觉这个长度为 2^n 位很奇怪（应该是 2^n 条）
> 
> </mark>
> 
> 
> 
> <mark>
> 
> 指令长度是错的，但是如果是指指令条数那就是对的（这题感觉出题人原本意图是这个）
> 
> </mark>
> 
> 
> 
> ![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalSys/DigitalSys-29.webp)
> 
> ![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalSys/DigitalSys-30.webp)

9.存储容量为256K×4位的RAM存储器，其地址线为8条、数据线为4条（❌）

> <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <mn>
> 
> 256
> 
> </mn>
> 
> <mi>
> 
> K
> 
> </mi>
> 
> <mo>
> 
> =
> 
> </mo>
> 
> <msup>
> <mn>
> 
> 2
> 
> </mn>
> 
> <mn>
> 
> 8
> 
> </mn>
> </msup>
> 
> <mo>
> 
> ×
> 
> </mo>
> 
> <msup>
> <mn>
> 
> 2
> 
> </mn>
> 
> <mn>
> 
> 10
> 
> </mn>
> </msup>
> 
> <mo>
> 
> =
> 
> </mo>
> 
> <msup>
> <mn>
> 
> 2
> 
> </mn>
> 
> <mn>
> 
> 18
> 
> </mn>
> </msup>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> 256K = 2^8 \times 2^{10} = 2^{18}
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
> <span className="mord">
> 
> 256
> 
> </span>
> 
> <span className="mord,mathnormal" style="margin-right:0.0715em;">
> 
> K
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
> <span className="strut" style="height:0.8974em;vertical-align:-0.0833em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> <span className="mord">
> 
> 2
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t">
> <span className="vlist-r">
> <span className="vlist" style="height:0.8141em;">
> <span style="top:-3.063em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mtight">
> 
> 8
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
> <span className="mspace" style="margin-right:0.2222em;">
> 
> 
> 
> </span>
> 
> <span className="mbin">
> 
> ×
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
> <span className="strut" style="height:0.8141em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> <span className="mord">
> 
> 2
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t">
> <span className="vlist-r">
> <span className="vlist" style="height:0.8141em;">
> <span style="top:-3.063em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mtight">
> <span className="mord,mtight">
> 
> 10
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
> <span className="strut" style="height:0.8141em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> <span className="mord">
> 
> 2
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t">
> <span className="vlist-r">
> <span className="vlist" style="height:0.8141em;">
> <span style="top:-3.063em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mtight">
> <span className="mord,mtight">
> 
> 18
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
> 
> ,地址线为18条

10.对于m个待处理数据的数据流，每个数据运算有L段，每段用时t的流水线操作结构，理想情况下共需运算时间T=m*t+(L-1)*t（❌答案错，应该为✅）

> 就是对的
> 
> ![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalSys/DigitalSys-31.webp)
> 
> <mark>
> 
> Gemini认为对
> 
> </mark>
> 
> 
> 
> ![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalSys/DigitalSys-32.webp)

11.在一个时序逻辑电路中，消除了其中的组合逻辑电路因竞争冒险而产生的尖峰脉冲，就不会产生竞争冒险现象（❌）

> ![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalSys/DigitalSys-33.webp)
> 
> 时序部分也存在

12.在测试电路中，边界扫描电路用于测试电路板的好坏，而内建自测试电路用于测试芯片内部的好坏（❌）

> 出现过，不赘述

#### 16-17春夏

1. 两个补码进行相加运算，如果最高位产生进位输出，则肯定发生溢出。 (❌)

> **比较符号位的“进位输入”和“进位输出”是否相同才能判定是否真的溢出了**
> 
> - 设 Cin 为进入符号位的进位。
> - 设 Cout 为符号位产生的进位。
> 
> 如果 Cin!=Cout，则发生溢出。
> 
> 如果 Cin=Cout，则没有溢出。
> 
> ---
> 
> **例1：有进位输出，但没有溢出**
> 
> 计算 `(-10) + 20`
> 
> - -10 的补码是 `1111 0110`
> - 20 的补码是 `0001 0100`
> 
> ```text
> 1111 0110   (-10)
> +   0001 0100   (20)
> -----------------
>   1 0000 1010   (结果为 10，正确)
> ```
> 
> - **符号位的进位输入 Cin**: 1
> - **符号位的进位输出 Cout**: 1 (最左边那个被舍弃的1)
> 
> 因为 **Cin=Cout=1**，所以**没有发生溢出**。尽管最高位产生了进位输出，但运算结果 `0000 1010` (十进制的10) 是完全正确的。
> 
> ---
> 
> **例2：有溢出，但没有进位输出**
> 
> 计算 `80 + 80`
> 
> - 80 的补码是 `0101 0000`
> 
> ```text
> 0¹10 0000   <-- 进位 (carry)
>     0101 0000   (80)
> +   0101 0000   (80)
> -----------------
>   0 1010 0000   (结果为 -96，错误)
> ```
> 
> - **符号位的进位输入 Cin**: 1
> - **符号位的进位输出 Cout**: 0
> 
> 因为 **Cin !=Cout**，所以**发生了溢出**。两个正数相加，结果 `1010 0000` 却成了一个负数（-96），这显然是错误的。在这个例子中，虽然发生了严重的溢出，但最高位并没有产生进位输出。
> 
> ---
> 
> <mark>
> 
> **不能**
> 
> </mark>
> 
> <mark>
> 
> 简单地用“最高位是否有进位输出”来判断是否溢出。必须比较符号位的进位输入和进位输出，只有当两者不相等时，才真正发生了溢出
> 
> </mark>

1. 卡诺图化简得到的最简化结果是唯一的。(❌)

> （可能有多个等价最简式）

1. 单稳态触发器的暂稳态时间与输入触发脉冲宽度成正比。(❌)

> 略

1. 组合逻辑电路中产生竞争冒险的主要原因是输入信号受到尖峰干扰。(❌)

> **信号传输延迟不一致**

1. 石英晶体多谐振荡器的振荡频率与电路中的R、C乘积成正比。 (❌)

> 只由石英晶体特性决定

1. 在数字电路中，逻辑功能相同的TTL门和CMOS门芯片都可以互相替代使用。(❌)

> 电平标准不同且输入前接入电阻阻值不同可能会导致门电路输出完全不同

1. 所有的半导体存储器在运行时都具有读写功能，所以使用时很灵活。 (❌)

> ROM是只读的

1. 逻辑函数 F1=ΣABCD(2,3,5,8,11,13)和 F2=ΠABCD(2,4,7,10,12,13)之间满足对偶关系。(✅)

> 这个是满足的，最小项和对偶操作后的最大项下标之和为`n{1'b1}` ，本题对应为15

1. 在测试电路中，响应分析驱动态压缩的输出也称为边界扫描输出。(❌)

> 电路自测试中使用到响应分析驱动态压缩，是解决芯片内部逻辑测试的挑战
> 
> ![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalSys/DigitalSys-34.webp)
> 
> 边界扫描输出主要用于测试**芯片与芯片之间的互连**（例如电路板上的焊点和引线）以及芯片自身的I/O引脚完整性。它通过在每个I/O引脚旁放置一个“边界扫描单元”来实现这一目标
> 
> ![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalSys/DigitalSys-35.webp)

1. A的原码为011010，则2A对应的8位原码形式为00110100，-A的8位补码为11001011。 (❌)

> 补码应该是11001100，这题他忘记取反后加一了

1. 流水线操作算法结构一定比并行算法结构所需要的运算时间少。 (❌)

> 重复

1. TTL电路的JK触发器，时钟端控5kHz脉冲，J与K悬空，则输出Q的频率为5kHz。(❌)

> <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msup>
> <mi>
> 
> Q
> 
> </mi>
> 
> <mo>
> 
> ∗
> 
> </mo>
> </msup>
> 
> <mo>
> 
> =
> 
> </mo>
> 
> <mover accent="true">
> <mi>
> 
> Q
> 
> </mi>
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
> Q^* = \overline{Q}
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:0.8831em;vertical-align:-0.1944em;">
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
> <span className="vlist-t">
> <span className="vlist-r">
> <span className="vlist" style="height:0.6887em;">
> <span style="top:-3.063em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mbin,mtight">
> 
> ∗
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
> <span className="strut" style="height:1.0778em;vertical-align:-0.1944em;">
> 
> 
> 
> </span>
> 
> <span className="mord,overline">
> <span className="vlist-t,vlist-t2">
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
> <span className="mord,mathnormal">
> 
> Q
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
> 
> <span className="vlist-s">
> 
> ​
> 
> </span>
> </span>
> 
> <span className="vlist-r">
> <span className="vlist" style="height:0.1944em;">
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
>  是分频器，二分频

1. 某电路有A、B、C、D、E、F六个状态，A和C、D和E、E和B、F和C分别等价，则该电路可化简为3个状态。 (❌)

> <mark>
> 
> 啥玩意没看懂，但是按题目的意思，如果真合并的话那也是两种状态，不合并就是六个状态
> 
> </mark>

1. 一个16K×32bit的SRAM芯片，除了电源和接地端外，其引出线至少应该有48条。 (✅)

> <mark>
> 
> 16K对应
> 
> </mark>
> 
> <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msup>
> <mn>
> 
> 2
> 
> </mn>
> 
> <mn>
> 
> 14
> 
> </mn>
> </msup>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> 2^{14}
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:0.8141em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> <span className="mord">
> 
> 2
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t">
> <span className="vlist-r">
> <span className="vlist" style="height:0.8141em;">
> <span style="top:-3.063em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mtight">
> <span className="mord,mtight">
> 
> 14
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
> 
> <mark>
> 
> 个存储单元，使用译码器至少需要14个端口，32bit,意味着有32根数据线，还需要有三位控制线
> 
> </mark>
> 
> 
> 
> ![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalSys/DigitalSys-36.webp)

1. 微码控制器，微指令中的判别字段为0时，下址字段信息就是下条微指令的地址；微指令中的判别字段为1时，下条微指令的地址则是下址字段修改后的新地址。 (❌)

#### 15-16春夏

1. "0" 的补码只有一种形式。  (✅)
2. 原码和反码均可将减法运算转化为加法运算。(❌)
3. 主从 JK 触发器、边缘 JK 触发器和同步 JK 触发器的逻辑功能完全相同。 (✅)

> 对于所有JK触发器都遵循同一个特征表
> 
> ![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalSys/DigitalSys-37.webp)
> 
> 区别在于**对时钟信号（Clock）的响应方式**
> 
> - **主从JK触发器 (Master-Slave JK Flip-flop)**
>   - **工作方式**: 由两个锁存器（一个主、一个从）构成。它在时钟脉冲的**整个有效电平期间**（例如，当CLK=1时）对输入J和K采样，然后在时钟电平**跳变时**（例如，CLK从1变0）才将结果传递到最终输出Q。
>   - **致命缺点**: 存在“**一次追赶**”（1s Catching）问题。如果在时钟有效电平期间（CLK=1时），输入J或K发生多次变化，主锁存器的状态会跟着变化，最终输出结果可能不是设计者想要的。它对时钟脉冲期间的干扰很敏感。
> - **边缘JK触发器 (Edge-Triggered JK Flip-flop)**
>   - **工作方式**: 仅在时钟信号的**上升沿**（或下降沿）的**瞬间**对J和K输入进行采样，并立即改变输出Q。
>   - **巨大优势**: 它只关心时钟边沿那一瞬间的输入状态，完全忽略时钟周期内其他时间的输入变化。这使得它对干扰的**抗扰能力极强**，电路行为更稳定、更可预测。这是现代数字设计的标准。
> - **同步JK触发器 (Synchronous JK Flip-flop)**
>   - 这个术语本身有些笼统，因为所有JK触发器都是**同步**元件（其状态变化与时钟同步）。在现代语境下，它通常就是指**边缘触发式JK触发器**，以区别于已经基本淘汰的主从触发器。

1. 并行加法器采用超前进位，目的是为了简化电路。(❌)

> <mark>
> 
> 超前进位的目的是提高速度，实际上超前进位反而会使电路更复杂
> 
> </mark>

1. 在同步时序电路的设计中，如最简状态表中的状态数为 2^N，而又采用 N 个触发器来实现电路，则不需要检查电路的自启动性。(❌)

> 即便每个状态都被设计了也要看看设计出来的部分有没有自启动

1. 流水线操作算法结构一定比并行算法结构所需要的运算时间少。(❌)

> 重复

1. 摩尔型时序逻辑电路的输出与输入和电路当前状态均有关。 (❌)

> 米利型才是，摩尔型只与当前电路状态有关

1. 所有的半导体存储器在运行时都具有读写功能。 (❌)

> 不可以

1. 在电路测试中 SA0 和 SA1 故障模型可以覆盖集成电路中的所有可能的故障。 (❌)

> 重复

1. 冯诺依曼结构相比于哈佛体系结构具有更好的灵活性和稳定性，而哈佛体系结构具有更好的硬件效率。(❌)

> 重复了

#### 14-15春夏

1. 处理器可以分为两个部分:数据通路和控制电路 (✅)

> 那就记下来吧
> 
> ![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalSys/DigitalSys-38.webp)

1. 一般 TTL 门电路的输出端可以直接相连，实现线与 (❌)

> 前面出现过了

1. CMOS 与非门和 TTL 与非门的逻辑功能不一样 (❌)

> 都是与非还能不一样？

1. JK触发器在时钟脉冲的作用下，如果要使 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msup>
<mi>

Q

</mi>

<mrow>
<mi>

n

</mi>

<mo>

+

</mo>

<mn>

1

</mn>
</mrow>
</msup>

<mo>

=

</mo>

<msup>
<mover accent="true">
<mi>

Q

</mi>

<mo>

ˉ

</mo>
</mover>

<mi>

n

</mi>
</msup>
</mrow>

<annotation encoding="application/x-tex">

Q^{n + 1} = \bar Q^{n}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.0085em;vertical-align:-0.1944em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

Q

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

n

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
<span className="strut" style="height:1.0145em;vertical-align:-0.1944em;">



</span>

<span className="mord">
<span className="mord,accent">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.8201em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal">

Q

</span>
</span>

<span style="top:-3.2523em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.1667em;">
<span className="mord">

ˉ

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.1944em;">
<span>



</span>
</span>
</span>
</span>
</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.6644em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



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
</span>
</span>
</span>
</span>
</span>
</span>
</span>

，则输入信号JK应为 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

J

</mi>

<mo>

=

</mo>

<msup>
<mi>

Q

</mi>

<mi>

n

</mi>
</msup>
</mrow>

<annotation encoding="application/x-tex">

J = Q^n

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0962em;">

J

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
<span className="mord,mathnormal">

Q

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

n

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

， <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

K

</mi>

<mo>

=

</mo>

<msup>
<mover accent="true">
<mi>

Q

</mi>

<mo>

ˉ

</mo>
</mover>

<mi>

n

</mi>
</msup>
</mrow>

<annotation encoding="application/x-tex">

K = \bar Q^n

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

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
<span className="strut" style="height:1.0145em;vertical-align:-0.1944em;">



</span>

<span className="mord">
<span className="mord,accent">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.8201em;">
<span style="top:-3em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord,mathnormal">

Q

</span>
</span>

<span style="top:-3.2523em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="accent-body" style="left:-0.1667em;">
<span className="mord">

ˉ

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.1944em;">
<span>



</span>
</span>
</span>
</span>
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

n

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

 (❌)

> 要是这样做了之后JK触发器就变成D触发器了，显然不对

1. 具有记忆功能的各类触发器是构成时序逻辑电路的基本单元 (✅)

> 记下来吧，纯定义问题

1. 石英晶体多谐振荡器的振荡频率与电路中的R、C乘积成正比 (❌)

> 石英晶振就和石英本身有关了，和RC肯定无关了

1. 状态简化中，若 S1、S2 两状态的输出不同，则S1、S2 两状态肯定不等价。由两个 TTL 或非门构成的基本 RS 触发器，当 R=S=0 时，触发器的状态为不定 (✅)

> 这个就是考状态简化的定义了
> 
> ![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalSys/DigitalSys-39.webp)

1. 由两个 TTL 或非门构成的基本 RS 触发器，当 R=S=0 时，触发器的状态为不定 (❌)

> 应该是保持状态，不是不定状态，对于或非门而言，不定状态是指R=S=1

1. 格雷码具有任何相邻码只有一位码元不同的特性 (✅)

> 定义问题

1. 组合逻辑电路中产生竞争冒险的主要原因是输入信号受到尖峰干扰 (❌)

> 冒险的定义是<mark>
> 
> 逻辑门因输入端的竞争而导致输出产生不应有的
> 
> </mark>
> 
> <mark>
> 
> **尖峰干扰脉冲**
> 
> </mark>
> 
> <mark>
> 
> 的现象
> 
> </mark>
> 
> ，所以题目的尖峰干扰是结果但不是原因
> 
> 前面出现过的

1. 对于一个存储容量位32KX16位的RAM有512K个地址单元 (❌)

> 512K是指存储容量，地址单元就是32K
> 
> 存储容量的表示方法 **“N x M位”** 有着明确的含义：
> 
> - **N**: 表示该存储器有多少个**可独立寻址的存储单元（地址单元）**。
> - **M**: 表示**每个**存储单元包含多少个二进制位（bit），即**字长 (Word Length)**。
> 
> 现在我们来看题目中的“**32K x 16位**”：
> 
> - **32K**: 这部分直接告诉我们，这个RAM有 **32K** 个可独立寻址的存储单元。`K`在这里是 210=1024，所以总共有 32×1024=32,768 个地址单元。
> - **16位**: 这部分说明了**每一个**地址单元存放的数据是16位宽。
> 
> 因此，这个RAM的地址单元数量就是 **32K**，而不是512K。

1. 或非门多余的输入端均可以悬空 (❌)

> CMOS不允许悬空

1. 单稳态触发器的暂稳态时间与输入触发脉冲宽度成正比 (❌)

> 只和本身RC有关

1. 由与、或、非门电路构成的逻辑电路一定是组合逻辑电路 (❌)

> 触发器不就是由与非门或非门搭出来的吗（笑）

1. 冯诺依曼结构和哈佛结构的区别是:前者将程序存储和数据存储放在同一物理存储空间，后者将程序和数据存储分别放在不同的物理存储空间 (✅)

> 补充上定义，前面出现过的

#### 13-14春夏

1. 2014个“1”异或的结果再与 117 个“0”同或，得到的结果是“0”(❌)

> 2014偶数个1，异或完是0，然后就是118个0进行同或，偶数个0同或结果为1
> 
> 关于异或，就是检验多少个1，检奇，1的数量为奇则结果为1
> 
> <mark>
> 
> 而同或就反着来了，检验多少个0，检偶，0的数量为偶数则结果为1
> 
> </mark>

1. 有一 8421BCD 数码 10010011，它相当于十进制数“147”(❌)

> 这种编码要拆成4位和4位来看

1. 三态门输出为高阻时，其输出线上电压为高电平(❌)

> 前面出现过的，要看连的那一端

1. 任意两个最大项之和恒为“1” (✅)

> 最大项是和式，再和，肯定会有A和A’这种出现的，结果为1

1. CMOS 与非门的多余脚悬空等效于低电平(❌)

> 不能悬空

1. 将 JK 触发器的 K端接到触发器反向输出端，把J端接到输入 T，就能把JK触发器改造成 T触发器(❌)

> T触发器是把JK直接连到一起了

1. 超前进位加法器比串行进位加法器速度慢(❌)

> 超前进位更快

1. 组合逻辑电路产生竞争冒险的内因是信号在电路内部的电平不一致而且有尖峰脉冲噪声存在(❌)

> 出现好多遍了

1. 施密特触发器电路具有两个稳态且每个稳态需要相应的输入条件维持 (✅)

> 是的，这个就是定义问题了吧

10.五进制计数器的有效状态为5个 (✅)

> 0-1-2-3-4-0，所以是五个

1. 当时序逻辑电路存在无效循环时该电路不能自启动 (✅)

> 对的，这个就是自启动的定义

1. 米里(Mealy)状态机和莫尔(Moore)状态机可以相互转换(❌，我感觉是✅的)

> <mark>
> 
> 问了刘鹏，他也说可以
> 
> </mark>
> 
> 
> 
> 前面有，可以

1. 最少 64 片容量为 256x4 的 RAM 可组合成容量为 4KX8的 RAM(❌)

> 可以算一下，应该是32片

1. 流水线操作算法结构一定比并行算法结构所需要的运算时间少(❌)

> 重复

1. 大批量定型产品的生产因为是成熟设计所以不需要测试(❌)

> 一眼错

### 别的鸡脚旮旯的概念

1. `a^b` 指的是按位异或运算
2. 555触发器这个RS触发器的封装取出来的值是Q'

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalSys/DigitalSys-40.webp)

1. PAL Programable Array Logic 与门可编程，或门不可编程。但是 PLA 与或门都可编程
