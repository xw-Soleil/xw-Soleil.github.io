# L7：流水线处理器

> 流水线基本概念与结构/数据/控制冒险，以及静态调度、多发射与乱序执行入门

## 前面部分补充

## 第 20 页：处理器性能的 “Iron Law”

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L7-Pipeline-01.webp)

这一页讲的是处理器性能最核心的公式，也叫 **Iron Law**。

公式写成飞书适配格式就是：

```text
程序执行时间
= 程序指令数 × 每条指令平均周期数 × 每个周期的时间
```

英文形式是：

```text
Time / Program
= Instructions / Program × Cycles / Instruction × Time / Cycle
```

也就是：

```text
程序跑得快不快
取决于三件事：

1. 一共要执行多少条指令
2. 每条指令平均要花多少个周期，也就是 CPI
3. 每个时钟周期有多长
```

---

### Instructions / Program：程序指令数

它表示：

```text
一个程序最终被编译成了多少条机器指令
```

这个主要受三个东西影响：

```text
源代码
编译器
ISA 指令集
```

例如，同样一个 C 程序，编译器优化得更好，可能用更少的机器指令完成。

所以：

```text
指令数越少，程序可能越快
```

---

### Cycles / Instruction：CPI

CPI 的意思是：

```text
Cycles Per Instruction
= 每条指令平均需要多少个时钟周期
```

注意是**平均**。

不同处理器结构的 CPI 不一样：

<table>
<thead>
  <tr>
    <th>
      微架构
    </th>
    
    <th>
      CPI
    </th>
    
    <th>
      周期时间
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      微码机器 Microcoded
    </td>
    
    <td>
      大于 1
    </td>
    
    <td>
      短
    </td>
  </tr>
  
  <tr>
    <td>
      单周期机器 Single-cycle
    </td>
    
    <td>
      1
    </td>
    
    <td>
      长
    </td>
  </tr>
  
  <tr>
    <td>
      流水线机器 Pipelined
    </td>
    
    <td>
      理想情况下约等于 1
    </td>
    
    <td>
      短
    </td>
  </tr>
</tbody>
</table>

这里最容易误解的是流水线。

流水线不是说一条指令只需要一个阶段，而是说：

```text
一条指令仍然要经过多个阶段，
但是多条指令可以重叠执行。
```

所以理想情况下，流水线稳定之后：

```text
每个周期完成一条指令
```

因此：

```text
理想 CPI = 1
```

但是如果有冒险、停顿、cache miss，那么：

```text
实际 CPI > 1
```

---

### Time / Cycle：时钟周期时间

它表示：

```text
一个时钟周期有多长
```

单周期处理器的问题是：

```text
一个周期必须足够长，
要能容纳最慢的那条指令。
```

比如 `lw` 需要经过：

```text
取指令 → 译码 → ALU算地址 → 访问内存 → 写回寄存器
```

所以单周期处理器的周期很长。

流水线的优势是把一条指令拆成多个阶段：

```text
IF → ID → EX → MEM → WB
```

每个阶段更短，因此时钟周期可以缩短。

所以流水线提升性能的关键不是：

```text
让单条指令的延迟变短
```

而是：

```text
提高吞吐量，让处理器几乎每个周期都完成一条指令
```

---

## 第 22 页：CPI 例子

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L7-Pipeline-02.webp)

这一页是在纠正一个非常常见的误解：

```text
5级流水线，CPI ≠ 5
```

这是错的。

因为：

```text
5级流水线表示单条指令的延迟大约是5个阶段，
但不表示平均每条指令占用5个完整周期。
```

---

### 微码机器 Microcoded machine

图中说：

```text
3 条指令一共用了 22 个周期
```

所以：

```text
CPI = 总周期数 / 指令数
CPI = 22 / 3
CPI = 7.33
```

意思是：

```text
微码机器执行一条指令通常要拆成很多小步骤，
所以平均每条指令需要多个周期。
```

因此它的 CPI 比较大。

---

### 单周期机器 Unpipelined machine

图中说：

```text
3 条指令用了 3 个周期
```

所以：

```text
CPI = 总周期数 / 指令数
CPI = 3 / 3
CPI = 1
```

单周期机器确实是：

```text
一条指令一个周期完成
```

但是问题是：

```text
这个周期非常长
```

因为它必须保证最慢的指令也能在一个周期内完成。

所以单周期机器虽然：

```text
CPI = 1
```

但它不一定快，因为：

```text
Time / Cycle 很大
```

也就是时钟频率低。

---

### 流水线机器 Pipelined machine

图中说的是理想流水线的情况。

5级流水线包括：

```text
IF：取指令
ID：译码 / 读寄存器
EX：执行
MEM：访存
WB：写回
```

单条指令确实要经过 5 个阶段。

但是多条指令可以重叠执行，例如：

<table>
<thead>
  <tr>
    <th>
      周期
    </th>
    
    <th>
      Inst 1
    </th>
    
    <th>
      Inst 2
    </th>
    
    <th>
      Inst 3
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      1
    </td>
    
    <td>
      IF
    </td>
    
    <td>
      
    </td>
    
    <td>
      
    </td>
  </tr>
  
  <tr>
    <td>
      2
    </td>
    
    <td>
      ID
    </td>
    
    <td>
      IF
    </td>
    
    <td>
      
    </td>
  </tr>
  
  <tr>
    <td>
      3
    </td>
    
    <td>
      EX
    </td>
    
    <td>
      ID
    </td>
    
    <td>
      IF
    </td>
  </tr>
  
  <tr>
    <td>
      4
    </td>
    
    <td>
      MEM
    </td>
    
    <td>
      EX
    </td>
    
    <td>
      ID
    </td>
  </tr>
  
  <tr>
    <td>
      5
    </td>
    
    <td>
      WB
    </td>
    
    <td>
      MEM
    </td>
    
    <td>
      EX
    </td>
  </tr>
  
  <tr>
    <td>
      6
    </td>
    
    <td>
      
    </td>
    
    <td>
      WB
    </td>
    
    <td>
      MEM
    </td>
  </tr>
  
  <tr>
    <td>
      7
    </td>
    
    <td>
      
    </td>
    
    <td>
      
    </td>
    
    <td>
      WB
    </td>
  </tr>
</tbody>
</table>

如果严格从第一条指令开始取指，到第三条指令完全写回，这里会有填充和排空开销。

但是课件这里强调的是**稳态吞吐率**：

```text
流水线装满之后，
每个周期都可以完成一条指令。
```

所以理想情况下：

```text
CPI ≈ 1
```

而不是：

```text
CPI = 5
```

---

## 🐟流水线基本概念（Basic Concept）

流水线通过让多条指令重叠执行，提高整体执行效率；虽然单条指令延迟可能变长，但连续执行多条指令时速度更快。

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 47.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L7-Pipeline-03.webp" />
      </p>
    </td>
    
    
      <td style="width: 52.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L7-Pipeline-04.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

<table>
<thead>
  <tr>
    <th>
      对比项
    </th>
    
    <th>
      单周期数据通路
    </th>
    
    <th>
      流水线数据通路
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      指令执行方式
    </td>
    
    <td>
      一条指令一个周期完成
    </td>
    
    <td>
      一条指令分多个阶段完成
    </td>
  </tr>
  
  <tr>
    <td>
      指令是否重叠
    </td>
    
    <td>
      不重叠
    </td>
    
    <td>
      多条指令重叠执行
    </td>
  </tr>
  
  <tr>
    <td>
      数据通路结构
    </td>
    
    <td>
      一整条长路径
    </td>
    
    <td>
      被切成 F/D/X/M/W 多段
    </td>
  </tr>
  
  <tr>
    <td>
      中间寄存器
    </td>
    
    <td>
      不需要流水线寄存器
    </td>
    
    <td>
      需要阶段间流水线寄存器
    </td>
  </tr>
  
  <tr>
    <td>
      控制信号
    </td>
    
    <td>
      当前周期直接使用
    </td>
    
    <td>
      要随指令向后传递
    </td>
  </tr>
  
  <tr>
    <td>
      时钟周期
    </td>
    
    <td>
      很长，取决于完整指令路径
    </td>
    
    <td>
      较短，取决于最慢流水级
    </td>
  </tr>
  
  <tr>
    <td>
      主要问题
    </td>
    
    <td>
      时钟周期长
    </td>
    
    <td>
      数据冒险、控制冒险、结构冒险
    </td>
  </tr>
</tbody>
</table>

### 🐡流水线的数据通路

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L7-Pipeline-05.webp)

- 在单周期的基础上，在阶段之间加入寄存器。
- 控制信号区别：单周期中，控制信号只需要在当前周期控制当前指令。但流水线中，控制信号也要跟着指令一起向后传递。例如一条 `lw` 指令：

```text
D 阶段产生控制信号
X 阶段需要 ALU 加法
M 阶段需要读内存
W 阶段需要写回寄存器
```

所以像 `MemRW`、`WBSel`、`RegWEn` 这些信号，不能只在 D 阶段用完，而要一路跟着这条指令传到后面的阶段。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L7-Pipeline-06.webp)

## 🐟流水线冒险（Hazard）

### 🐡结构冒险(structural hazard)

**流水线中的一条指令可能需要流水线中的另一条指令正在使用的资源 。**

<alert type="info">

**定义：**流水线中，两条或多条指令在同一周期竞争同一个硬件资源，而该资源无法同时服务多个请求。

**产生原因：**流水线让多条指令并行重叠执行，因此不同阶段可能同时需要同一资源。

**典型例子：**若指令存储器和数据存储器共用一个单端口内存，则 IF 阶段取指和 MEM 阶段访存可能同时访问内存，产生冲突。

**解决方法：**

1. 暂停流水线，让指令轮流使用资源
2. 增加硬件资源，如分离 IMEM/DMEM，或增加内存端口

**经典 RISC 五级流水线****（在设计上没有结构冒险）****：**

通常通过硬件资源分离避免结构冒险，

例如 IMEM 和 DMEM 分开，寄存器堆提供多读一写端口。

</alert>

#### 🐠寄存器文件的结构冒险

- **例 1：寄存器文件端口冲突**

每条 RISC-V 指令最多可能需要：

```text
ID 阶段：同时读两个源寄存器 rs1、rs2
WB 阶段：写回一个目标寄存器 rd
```

因此寄存器堆通常设计为两个读端口 + 一个写端口，这样一个周期内可以同时完成：

```text
读 Reg[rs1]
读 Reg[rs2]
写 Reg[rd]
```

如果端口不够，就会发生结构冒险，必须暂停流水线。

- **例 2：取指和访存冲突**

五级流水线中：

```text
IF 阶段：需要访问指令存储器 IMEM
MEM 阶段：lw / sw 需要访问数据存储器 DMEM
```

如果只有一个统一的单端口内存，那么可能出现：一条指令在 IF 阶段取指，另一条指令在 MEM 阶段读/写数据

两者同时访问内存，就会冲突。

解决方式：

```text
方案 1：暂停取指，让 MEM 阶段先访问内存
方案 2：分离指令存储器和数据存储器
方案 3：使用独立的 I-Cache 和 D-Cache（指令缓存和数据缓存两套分开）
```

### 🐡数据冒险(data hazard)

*一条指令可能依赖于前一条指令产生的结果。***（依赖可能是为了一个数据值，数据化的危险）**

#### 🐠访问寄存器

##### 读写同周期：

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L7-Pipeline-07.webp)

寄存器访问文件的时间大约为100ps，这个速度可以做到**在前半周期完成WB 写寄存器，在后半周其完成ID 读寄存器。** ID 应该读到 WB 刚写进去的新值**。**

##### 🌟读的数据还要几个周期后才写回

也叫RAW 冒险：Read After Write，后面的指令想读一个寄存器，但前面的指令还没来得及把新值写进去。（上面是读写同时进行，这个是还没进行到写阶段下一条就要读了）

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L7-Pipeline-08.webp)

对于后面的xor和sw，指令能够正常读到前面“add s0,t1,t2”的s0写回结果。但是中间的sub和or和add指令相距太近无法读到写回结果

###### **解决方法：**

1. **🌟停顿 Stalling，也叫互锁 Interlock。**

当后一条指令依赖前一条指令尚未写回的结果时，可以通过硬件互锁让流水线停顿，插入 bubble，等前一条指令写回后再继续执行，从而避免数据冒险。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L7-Pipeline-09.webp)

<alert type="tip">

**Interlock 是硬件机制**，它负责检测指令之间有没有依赖冲突。

**Stalling 是动作**，意思是让流水线某些阶段暂停，不让后面的指令继续推进。

**Bubble：气泡**，负责填补空出来的流水线位置

</alert>

停顿可以保证结果正确，但会降低流水线性能；**编译器有时可以通过重新安排指令顺序，减少停顿。**

比如原来是：

```text
add s0, t0, t1
sub t2, s0, t3
```

这两条靠得太近，`sub` 必须等 `add`。

如果中间有一条无关指令：

```text
add s0, t0, t1
or  t4, t5, t6
sub t2, s0, t3
```

那么 `or` 可以填补等待时间。

这样 `add` 有更多时间产生结果，`sub` 可能就不需要停顿，或者少停顿。

附：有bubble的CPI计算例

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L7-Pipeline-10.webp)

1. **数据前递(Forwarding)/旁通(Bypass)**

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 50.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L7-Pipeline-11.webp" />
      </p>
    </td>
    
    
      <td style="width: 49.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L7-Pipeline-12.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

前一条指令的结果一旦在 ALU 算出来，就**直接送给后一条指令使用，不必等它写回寄存器。**

好处是：**减少停顿，提高流水线性能。**

代价是：**数据通路中需要额外连线和选择器。**

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 65.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L7-Pipeline-13.webp" />
      </p>
    </td>
    
    
      <td style="width: 34.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L7-Pipeline-14.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

##### lw data hazard（1 和3广义上来说也属于第二种）

`lw` 从内存读出的数据出来得比较晚，即使有 forwarding，下一条紧跟着用它的指令也可能来不及拿到数据，所以通常要停顿一个周期。如图所示，可以综合利用停顿、数据前递来解决。若不想要停顿，也可综合代码调度。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L7-Pipeline-15.webp)

普通 ALU 指令，例如：

```text
add s0, t0, t1
sub t2, s0, t3
```

`add` 的结果在 **EX 阶段结束** 就已经由 ALU 算出来了，可以通过 forwarding 直接把 ALU 结果送给下一条指令。

但是 `lw` 不一样：

```text
lw  s0, 0(t1)
sub t2, s0, t3
```

`lw` 的结果是从内存 DMEM 读出来的。

`lw` 的过程是：

```text
EX：计算地址 Reg[t1] + offset
MEM：访问内存，读出数据
WB：写回寄存器 s0
```

也就是说，`lw` 真正的数据要到 **MEM 阶段结束** 才出现。

而下一条 `sub` 在它的 **EX 阶段** 就需要 `s0` 参与运算。

问题就是：

```text
sub 需要数据的时候，
lw 的数据还没从内存读出来。
```

所以即使有 forwarding，也可能晚一个阶段。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L7-Pipeline-16.webp)

**停顿会浪费周期，但编译器可以通过指令重排，把与当前依赖无关的指令放到 load delay slot 中，从而避免插入空泡，减少执行周期。**

左边原始顺序因为 `lw` 后马上使用加载结果，需要停顿，所以是 **13 周期**。
右边通过提前执行无关的 `lw t4, 8(t0)`，填掉一个等待槽，因此减少到 **11 周期**。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L7-Pipeline-17.webp)

### 🐡控制冒险 (分支, 异常) (control hazard (branches, exceptions))

*一条指令可能依赖于前一条指令产生的结果。***（可能依赖于下一条指令的地址）**

**控制冒险 Control Hazard** 指的是：

> 流水线在取下一条指令时，还不知道下一条指令到底应该从哪里取。

正常情况下，CPU 默认执行顺序是：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

P

</mi>

<msub>
<mi>

C

</mi>

<mrow>
<mi>

n

</mi>

<mi>

e

</mi>

<mi>

x

</mi>

<mi>

t

</mi>
</mrow>
</msub>

<mo>

=

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
</mrow>

<annotation encoding="application/x-tex">

PC_{next}=PC+4

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

n

</span>

<span className="mord,mathnormal,mtight">

e

</span>

<span className="mord,mathnormal,mtight">

x

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
</span>
</span>
</span>

，也就是取下一条顺序指令。

但是一旦遇到 **跳转、分支、函数返回** 这类会改变程序执行路径的指令，下一条 PC 就不一定是 `PC+4`，可能是某个跳转目标地址。因此就会产生控制冒险。

##### 回顾：各类指令如何决定下一个 PC？

1. 情况一：普通指令

例如：

```text
add r1, r2, r3
lw r1, 0(r2)
sub r4, r5, r6
```

这些指令不改变程序流程。

所以：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

P

</mi>

<msub>
<mi>

C

</mi>

<mrow>
<mi>

n

</mi>

<mi>

e

</mi>

<mi>

x

</mi>

<mi>

t

</mi>
</mrow>
</msub>

<mo>

=

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
</mrow>

<annotation encoding="application/x-tex">

PC_{next}=PC+4

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

n

</span>

<span className="mord,mathnormal,mtight">

e

</span>

<span className="mord,mathnormal,mtight">

x

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
</span>
</span>
</span>
</span>

需要知道的信息很少，只要知道它不是跳转或分支指令即可。

---

1. 情况二：无条件跳转 Unconditional Jump

例如：

```text
j label
```

它一定会跳转，不需要判断条件。

下一条 PC 是：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

P

</mi>

<msub>
<mi>

C

</mi>

<mrow>
<mi>

n

</mi>

<mi>

e

</mi>

<mi>

x

</mi>

<mi>

t

</mi>
</mrow>
</msub>

<mo>

=

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

<mtext>

offset

</mtext>
</mrow>

<annotation encoding="application/x-tex">

PC_{next}=PC+\text{offset}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

n

</span>

<span className="mord,mathnormal,mtight">

e

</span>

<span className="mord,mathnormal,mtight">

x

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
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,text">
<span className="mord">

offset

</span>
</span>
</span>
</span>
</span>
</span>

或者某种由指令字段拼接出来的目标地址。

所以它需要：

<table>
<thead>
  <tr>
    <th>
      需要的信息
    </th>
    
    <th>
      作用
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      Opcode
    </td>
    
    <td>
      判断这是跳转指令
    </td>
  </tr>
  
  <tr>
    <td>
      PC
    </td>
    
    <td>
      作为跳转目标计算的基准
    </td>
  </tr>
  
  <tr>
    <td>
      offset
    </td>
    
    <td>
      计算跳转目标地址
    </td>
  </tr>
</tbody>
</table>

无条件跳转比条件分支简单，因为它**一定跳**，不需要比较寄存器条件。

---

1. 情况三：跳转寄存器 Jump Register

例如：

```text
jr r31
```

常见于函数返回，比如从 `r31` 或 `ra` 中取返回地址。

它的下一条 PC 不是由 offset 决定的，而是来自某个寄存器：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

P

</mi>

<msub>
<mi>

C

</mi>

<mrow>
<mi>

n

</mi>

<mi>

e

</mi>

<mi>

x

</mi>

<mi>

t

</mi>
</mrow>
</msub>

<mo>

=

</mo>

<mi>

R

</mi>

<mo stretchy="false">

[

</mo>

<mi>

r

</mi>

<mi>

s

</mi>

<mo stretchy="false">

]

</mo>
</mrow>

<annotation encoding="application/x-tex">

PC_{next}=R[rs]

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

n

</span>

<span className="mord,mathnormal,mtight">

e

</span>

<span className="mord,mathnormal,mtight">

x

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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0077em;">

R

</span>

<span className="mopen">

[

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal">

s

</span>

<span className="mclose">

]

</span>
</span>
</span>
</span>
</span>

所以它需要：

<table>
<thead>
  <tr>
    <th>
      需要的信息
    </th>
    
    <th>
      作用
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      Opcode
    </td>
    
    <td>
      判断这是 jump register
    </td>
  </tr>
  
  <tr>
    <td>
      Register value
    </td>
    
    <td>
      给出真正的跳转目标
    </td>
  </tr>
  
  <tr>
    <td>
      offset
    </td>
    
    <td>
      某些架构可能还会加偏移量
    </td>
  </tr>
</tbody>
</table>

这种情况更麻烦，因为目标地址存在寄存器中，必须等寄存器值读出来，CPU 才知道下一条指令地址。

---

1. 情况四：条件分支 Conditional Branch

例如：

```text
beq r1, r2, label
```

意思是：

如果 `r1 == r2`，就跳到 `label`；否则继续执行下一条指令。

所以它有两个可能的下一 PC：

不跳转：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

P

</mi>

<msub>
<mi>

C

</mi>

<mrow>
<mi>

n

</mi>

<mi>

e

</mi>

<mi>

x

</mi>

<mi>

t

</mi>
</mrow>
</msub>

<mo>

=

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
</mrow>

<annotation encoding="application/x-tex">

PC_{next}=PC+4

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

n

</span>

<span className="mord,mathnormal,mtight">

e

</span>

<span className="mord,mathnormal,mtight">

x

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
</span>
</span>
</span>
</span>

跳转：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mi>

P

</mi>

<msub>
<mi>

C

</mi>

<mrow>
<mi>

n

</mi>

<mi>

e

</mi>

<mi>

x

</mi>

<mi>

t

</mi>
</mrow>
</msub>

<mo>

=

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

<mtext>

offset

</mtext>
</mrow>

<annotation encoding="application/x-tex">

PC_{next}=PC+\text{offset}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

n

</span>

<span className="mord,mathnormal,mtight">

e

</span>

<span className="mord,mathnormal,mtight">

x

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
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,text">
<span className="mord">

offset

</span>
</span>
</span>
</span>
</span>
</span>

因此条件分支需要的信息最多：

<table>
<thead>
  <tr>
    <th>
      需要的信息
    </th>
    
    <th>
      作用
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      Opcode
    </td>
    
    <td>
      判断这是分支指令
    </td>
  </tr>
  
  <tr>
    <td>
      Register
    </td>
    
    <td>
      判断条件是否成立
    </td>
  </tr>
  
  <tr>
    <td>
      PC
    </td>
    
    <td>
      计算分支目标地址
    </td>
  </tr>
  
  <tr>
    <td>
      offset
    </td>
    
    <td>
      给出跳转距离
    </td>
  </tr>
</tbody>
</table>

这就是控制冒险最典型的来源：
**CPU 不知道分支到底跳不跳，但流水线又不能停下来不取指。**

<table>
<thead>
  <tr>
    <th>
      流水线阶段
    </th>
    
    <th>
      已知信息
    </th>
    
    <th>
      对控制冒险的意义
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      Fetch
    </td>
    
    <td>
      当前 PC 已知
    </td>
    
    <td>
      可以默认取 PC + 4
    </td>
  </tr>
  
  <tr>
    <td>
      Decode
    </td>
    
    <td>
      Opcode 和 offset 已知
    </td>
    
    <td>
      才知道当前指令是不是 jump / branch，以及跳转偏移量是多少
    </td>
  </tr>
  
  <tr>
    <td>
      Execute
    </td>
    
    <td>
      Branch condition、Jump register value 已知
    </td>
    
    <td>
      才知道条件分支是否成立，或者寄存器跳转目标是多少
    </td>
  </tr>
  
  <tr>
    <td>
      Memory
    </td>
    
    <td>
      与 PC 选择关系较弱
    </td>
    
    <td>
      主要用于访存
    </td>
  </tr>
  
  <tr>
    <td>
      Writeback
    </td>
    
    <td>
      与 PC 选择关系较弱
    </td>
    
    <td>
      主要用于写回寄存器
    </td>
  </tr>
</tbody>
</table>

##### 无条件PC相对跳转

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 31.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L7-Pipeline-18.webp" />
      </p>
    </td>
    
    
      <td style="width: 68.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L7-Pipeline-19.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

###### kill

kill的作用是：把错误取进流水线的指令变成 bubble，也就是让它不产生实际效果。

例如：

```text
j target
add x1, x2, x3    # 这条被错误取入
target:
or x7, x8, x9
```

当 CPU 确认 `j target` 要跳转之后，`add x1, x2, x3` 就会被 Kill。
被 Kill 后，它相当于变成：

```text
nop
```

也就是“什么都不做”。

###### 分支延迟槽

指的是：分支或跳转指令后面的那一个指令位置，即使程序已经决定跳转，这条指令也会先执行。

也就是说，早期某些 RISC ISA 规定：

```text
j target
add x1, x2, x3
target:
xori x1, x1, 7
```

执行顺序不是：

```text
j target -> xori
```

而是：

```text
j target -> add -> xori
```

也就是说，虽然 `j target` 表示跳到 `target`，但紧跟在它后面的 `add x1, x2, x3` 仍然会执行。

这个 `add x1, x2, x3` 所在的位置，就是 **delay slot，延迟槽**。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L7-Pipeline-20.webp)

<alert type="tip">

分支延迟槽和“没有 Kill 的原始硬件行为”在流水线现象上很像，都是跳转后一条指令继续执行；但前者是 ISA 规定的正确行为，编译器会专门安排这条指令，后者是1在普通 ISA 下没有清除错误指令导致的错误执行。

</alert>

###### 1990 年后的 RISC ISA 不再把 delay slot 写进指令集语义里

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L7-Pipeline-21.webp)

1. **Delay slot 会把微架构细节写进 ISA**
早期 RISC 的 delay slot 本质上是把“跳转后一条指令已经进入流水线、来不及清除”这个硬件现象，规定成 ISA 语义：跳转后一条指令必须执行。这样会让软件必须感知具体流水线结构。
2. **Delay slot 不一定提升性能**
如果编译器能在 delay slot 中放入有用指令，确实可以减少浪费；但如果找不到合适指令，只能填 `NOP`。这些 `NOP` 会增加代码长度，占用 I-cache，甚至可能因为取 `NOP` 发生 I-cache miss 而让处理器等待。
3. **Delay slot 不适合复杂微架构**
对简单五级流水线来说，一个 delay slot 还比较自然；但如果是深流水线、多发射、乱序执行的处理器，固定一个 delay slot 会限制硬件设计，使高级微架构更加复杂。
4. **现代处理器更依赖分支预测**
1990 年后的 RISC ISA 通常取消 delay slot，不再规定跳转后一条指令必须执行。跳转后错误取入的指令由硬件 `Kill / Flush` 清除，并通过分支预测尽量减少控制冒险带来的性能损失

##### 条件分支跳转

###### fkill&dkill

如果分支(branch)没有被采用，那么在分支之后依次获取的指令是正确的

如果采用分支(branch)或跳转(jump)，则需要通过转换为NOP从流水线中清除不正确的指令

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 45.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L7-Pipeline-22.webp" />
      </p>
    </td>
    
    
      <td style="width: 54.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L7-Pipeline-23.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

<alert type="question">

Fetch 阶段：

先默认取 PC + 4

Decode 阶段：

通过 opcode 知道这是 Branch

同时生成 offset，准备计算目标地址

Execute 阶段：

比较寄存器，得到 Cond?

如果 Branch? && Cond? 成立：

PCSel 选择分支目标地址

FKill 清除 Fetch 阶段错误指令

DKill 清除 Decode 阶段错误指令

如果条件不成立：

继续执行顺序路径

**在分支条件尚未确定时先默认顺序取指；等 Execute 阶段判断出条件后，如果分支不成立就继续执行，如果分支成立就用** **PCSel** **改写 PC，并用** **FKill****、****DKill** **清除已经错误取入流水线的顺序指令。**

</alert>

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L7-Pipeline-24.webp)

###### 分支预测(Branch Prediction)

在简单的流水线中，每个分支花费2个无效周期

为了提高性能，使用“分支预测(branch prediction)”来猜测分支将在流水线中更早地走向哪条路

只有在分支预测(branch prediction)不正确的时候，重新冲洗流水线

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L7-Pipeline-25.webp)

- 如何进行：CPU 看到 `beq t0, t1, label` 后，还不知道条件是否成立。
但是它可以先猜：

```text
这次分支会被采用 taken
```

于是它提前把下一条 PC 设为：

```text
PC_next = label
```

然后开始从 `label` 处取指令。

等到 `beq` 进入 Execute 阶段，CPU 真正算出：

```text
t0 == t1 是否成立
```

再检查刚才的预测是否正确。

---

- 如果预测正确，会怎样？

假设 CPU 猜：

```text
分支会跳转 taken
```

而实际结果也确实跳转，那么预测正确。

这时流水线已经提前从 `label` 取了正确的指令，所以可以继续执行。

也就是说：

```text
预测正确：流水线基本不用清空，分支惩罚很小
```

这就是分支预测能提高性能的原因。

---

- 如果预测错误，会怎样？

假设 CPU 猜：

```text
分支会跳转 taken
```

但实际结果是不跳转。

那么 CPU 前面从 `label` 取进来的指令就是错的。

这时必须：

```text
Kill / Flush 错误路径上的指令
重新从正确 PC 取指
```

也就是：

```text
预测错误：清空错误指令，产生 bubble，付出分支惩罚
```

所以分支预测不是保证一定对，而是：

> 先猜，猜对就省时间；猜错再纠正。

---

- 分支预测到底预测什么？

分支预测主要预测两个东西：

<table>
<thead>
  <tr>
    <th>
      预测内容
    </th>
    
    <th>
      含义
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      分支方向
    </td>
    
    <td>
      这条分支是 taken 还是 not taken
    </td>
  </tr>
  
  <tr>
    <td>
      分支目标
    </td>
    
    <td>
      如果 taken，下一条 PC 应该跳到哪里
    </td>
  </tr>
</tbody>
</table>

对于这条指令：

```text
beq t0, t1, label
```

CPU 可能猜：

```text
预测 taken：PC_next = label
预测 not taken：PC_next = PC + 4
```

---

- 和前面 Kill 的关系

没有分支预测时，简单流水线通常默认继续取顺序指令：

```text
默认 PC_next = PC + 4
```

如果后来发现分支 taken，就 Kill 错误取入的顺序指令。

而分支预测是更主动的做法：

```text
不只是默认顺序执行，而是根据预测选择下一条 PC
```

所以：

<table>
<thead>
  <tr>
    <th>
      方法
    </th>
    
    <th>
      做法
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      不预测 / 默认不跳
    </td>
    
    <td>
      先取 PC + 4，如果实际跳转再 Kill
    </td>
  </tr>
  
  <tr>
    <td>
      分支预测
    </td>
    
    <td>
      先猜 taken 或 not taken，提前取预测路径
    </td>
  </tr>
  
  <tr>
    <td>
      预测正确
    </td>
    
    <td>
      少浪费周期
    </td>
  </tr>
  
  <tr>
    <td>
      预测错误
    </td>
    
    <td>
      Kill 错误路径，重新取正确指令
    </td>
  </tr>
</tbody>
</table>

<alert type="question">

预测正确的概率？如果是50%的话还有意义吗

真实程序中的分支通常不是随机的，而是有一定规律可以利用。比如，**循环末尾的分支**大多数时候会跳回循环开头，只有循环结束时才不跳；**if 判断**中的某些条件可能经常成立，也可能经常不成立，因此可以根据历史行为进行预测；**函数返回**的目标地址通常具有较强规律，一般可以通过返回地址进行预测；**错误处理分支**大多数情况下不会跳转到错误处理路径，因为正常执行才是常见情况；而 **switch 或间接跳转**虽然目标不固定，但也可能表现出一定的历史规律。

</alert>

#### 🐡冒险应对的例子

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 50.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L7-Pipeline-26.webp" />
      </p>
    </td>
    
    
      <td style="width: 50.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <table>
        <thead>
          <tr>
            <th>
              寄存器
            </th>
            
            <th>
              含义
            </th>
          </tr>
        </thead>
        
        <tbody>
          <tr>
            <td>
              x1
            </td>
            
            <td>
              指向数组 A
            </td>
          </tr>
          
          <tr>
            <td>
              x2
            </td>
            
            <td>
              指向数组 B
            </td>
          </tr>
          
          <tr>
            <td>
              x3
            </td>
            
            <td>
              指向数组 C
            </td>
          </tr>
          
          <tr>
            <td>
              x4
            </td>
            
            <td>
              保存循环结束地址
            </td>
          </tr>
          
          <tr>
            <td>
              f0
            </td>
            
            <td>
              保存 B<span>
                i
              </span>
            </td>
          </tr>
          
          <tr>
            <td>
              f1
            </td>
            
            <td>
              保存 C<span>
                i
              </span>
            </td>
          </tr>
          
          <tr>
            <td>
              f2
            </td>
            
            <td>
              保存 B<span>
                i
              </span>
              
               + C<span>
                i
              </span>
            </td>
          </tr>
        </tbody>
      </table>
    </td>
  </tr>
</tbody>
</table>

#### 原始 vector-vector add 循环：

这段代码的主要问题是：
`fadd.d` 依赖前面的两个 `fld`，`fsd` 又依赖 `fadd.d` 的结果。

也就是：

```text
fld f0 / fld f1 -> fadd.d -> fsd
```

如果加载延迟很长，或者浮点加法延迟很长，流水线中间就容易出现等待。

---

#### 方法一：简单流水线调度

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L7-Pipeline-27.webp)

> 通过重新安排代码顺序，减少流水线冒险。

这里的关键是：

> 把和 `fadd.d` 无关的指针更新指令提前，插到加载和浮点加法之间。

原来是：

```text
load -> load -> 马上用数据做 fadd
```

现在变成：

```text
load -> load -> 做一些无关的 addi -> 再做 fadd
```

这样可以给 `fld` 留出更多时间，让数据更可能在 `fadd.d` 需要时已经准备好。

注意这里：

```text
fsd f2, -8(x1)
```

为什么是 `-8(x1)`？

因为前面已经提前执行了：

```text
addi x1, x1, 8
```

所以 `x1` 已经指向下一个 A 元素。
为了把当前结果写回原来的 `A[i]`，地址要写成：

```text
x1 - 8
```

所以 `fsd f2, -8(x1)` 语义仍然等价于原来的：

```text
fsd f2, 0(x1)
```

只是因为指针更新提前了，存储偏移量要相应调整。

> 简单调度可以减少部分流水线等待，但单个循环迭代内部可挪动的指令有限，所以优化能力有限。

---

#### 方法二：循环展开 Loop Unrolling

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L7-Pipeline-28.webp)

> 把多次循环合并成一次循环，从而暴露更多并行性，减少动态指令数。

原来一次循环只处理一个元素：

```text
A[i] = B[i] + C[i]
```

循环展开后，一次循环处理两个元素：

```text
A[i]     = B[i]     + C[i]
A[i + 1] = B[i + 1] + C[i + 1]
```

这里的优化点有两个。

第一，增加并行性。

两组加载和两组浮点加法之间相对独立：

```text
第1组：fld f0, fld f1 -> fadd.d f2
第2组：fld f10, fld f11 -> fadd.d f12
```

处理器可以更容易找到不互相依赖的指令来填补流水线空隙。

第二，减少循环控制开销。

原来每处理一个元素就要执行一次：

```text
bne x1, x4, loop
```

展开后，每处理两个元素才执行一次分支。

所以动态执行的分支指令数量减少了。

但是循环展开也有代价：

<table>
<thead>
  <tr>
    <th>
      代价
    </th>
    
    <th>
      说明
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      寄存器需求增加
    </td>
    
    <td>
      需要更多寄存器保存多组数据，例如 f10、f11、f12
    </td>
  </tr>
  
  <tr>
    <td>
      代码体积增加
    </td>
    
    <td>
      展开后循环体更长，占用更多 I-cache 空间
    </td>
  </tr>
  
  <tr>
    <td>
      编译器更复杂
    </td>
    
    <td>
      编译器要判断指针、数据依赖、循环次数边界
    </td>
  </tr>
  
  <tr>
    <td>
      可能受架构限制
    </td>
    
    <td>
      如果寄存器数量不够，展开太多反而会变差
    </td>
  </tr>
</tbody>
</table>

所以循环展开的本质是：

> 用更大的代码体积和更多寄存器占用，换取更高的指令并行度和更少的分支开销。

---

#### 方法三：解耦 Decoupling

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 49.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L7-Pipeline-29.webp" />
      </p>
    </td>
    
    
      <td style="width: 50.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L7-Pipeline-30.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

> 把控制和地址计算，与真正的数据计算分开。

原始循环中其实有两类操作。

第一类是控制和地址相关操作：

```text
fld    f0, 0(x2)
fld    f1, 0(x3)
fsd    f2, 0(x1)
addi   x1, x1, 8
addi   x2, x2, 8
addi   x3, x3, 8
bne    x1, x4, loop
```

这些操作主要和地址、指针、循环控制有关。

第二类是真正的数据计算：

```text
fadd.d f2, f0, f1
```

PPT 的意思是：

> 地址和控制操作不一定要等浮点数据计算完成后才做。

例如，即使当前的 `fadd.d` 还没算完，处理器也可以提前算下一轮循环的地址：

```text
下一次 B[i+1] 的地址
下一次 C[i+1] 的地址
下一次 A[i+1] 的地址
下一次是否继续循环
```

所以解耦的核心思想是：

> 控制流和地址生成可以先往前跑，数据计算可以在后面慢慢完成。

这也叫：

```text
lookahead / runahead
```

也就是让控制和地址部分提前“向前看”。

---

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L7-Pipeline-31.webp)

具体解释解耦后每条指令怎么处理。

例如：

```text
fld f0
```

不是立刻等数据回来，而是：

```text
发送加载请求到内存
把“将来写入 f0”的操作排队
```

`fld f1` 同理：

```text
发送加载请求到内存
把“将来写入 f1”的操作排队
```

`fadd.d` 也可以先进入队列：

```text
排队 fadd.d
等 f0、f1 的数据真正回来后再执行
```

`fsd f2` 可以先排队存储地址：

```text
先把存储地址排队
等 f2 数据算出来后再真正写内存
```

而下面这些整数指令：

```text
addi x1
addi x2
addi x3
bne
```

可以继续向前执行，更新指针并判断循环是否继续。

所以执行方式变成：

```text
地址/控制部分继续向前跑
内存访问请求排队
浮点计算排队
数据准备好以后再真正计算或写回
```

还有一个细节：

> 可以同时在队列中对 `f0` 进行多次写操作。

这是因为循环不断前进时，下一轮、下下一轮的 `fld f0` 可能都已经被发出。
虽然它们都写 `f0`，但在队列里可以按顺序管理，保证语义正确。

---

#### 简单解耦机 Simple Decoupled Machine

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L7-Pipeline-32.webp)

机器大致分成两条流水线：

<table>
<thead>
  <tr>
    <th>
      部分
    </th>
    
    <th>
      作用
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      整数型流水线 Integer Pipeline
    </td>
    
    <td>
      负责取指、译码、地址计算、指针更新、分支判断
    </td>
  </tr>
  
  <tr>
    <td>
      浮点流水线 Floating-Point Pipeline
    </td>
    
    <td>
      负责浮点计算和浮点数据写回
    </td>
  </tr>
</tbody>
</table>

中间用几个队列连接：

<table>
<thead>
  <tr>
    <th>
      队列
    </th>
    
    <th>
      作用
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      μOp 队列
    </td>
    
    <td>
      存放要交给浮点流水线执行的微操作
    </td>
  </tr>
  
  <tr>
    <td>
      Load Data Queue
    </td>
    
    <td>
      保存加载回来的数据
    </td>
  </tr>
  
  <tr>
    <td>
      Store Address Queue
    </td>
    
    <td>
      保存已经算好的存储地址
    </td>
  </tr>
  
  <tr>
    <td>
      Store Data Queue
    </td>
    
    <td>
      保存等待写入内存的存储数据
    </td>
  </tr>
</tbody>
</table>

这里最重要的是：

> 整数流水线可以先计算地址和控制流，浮点流水线可以等数据准备好后再执行。

例如整数流水线先做：

```text
算 load 地址
发出 load 请求
算 store 地址
更新指针
判断 bne
继续下一轮
```

浮点流水线后做：

```text
等 load 数据回来
执行 fadd.d
产生 store 数据
写入 Store Data Queue
```

这样两部分不必完全同步等待。

图中还有一个 `Check`，表示：

> 加载地址需要和之前排队的存储地址进行检查。

这是为了保证内存访问顺序正确。

比如如果前面有一个 store 还没真正写入内存，后面又来了一个 load，就要检查它们地址是否冲突，避免读到错误数据。

#### 三种优化方法对比

<table>
<thead>
  <tr>
    <th>
      方法
    </th>
    
    <th>
      核心思想
    </th>
    
    <th>
      优点
    </th>
    
    <th>
      局限
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      简单流水线调度
    </td>
    
    <td>
      重排指令，填补等待空隙
    </td>
    
    <td>
      不改变循环结构，比较简单
    </td>
    
    <td>
      单个循环内可调度空间有限
    </td>
  </tr>
  
  <tr>
    <td>
      循环展开
    </td>
    
    <td>
      一次处理多个元素
    </td>
    
    <td>
      提高并行度，减少分支次数
    </td>
    
    <td>
      增加寄存器压力和代码体积
    </td>
  </tr>
  
  <tr>
    <td>
      解耦执行
    </td>
    
    <td>
      分离地址/控制和数据计算
    </td>
    
    <td>
      可以让控制地址部分提前运行，隐藏长延迟
    </td>
    
    <td>
      需要额外硬件队列和复杂的依赖检查
    </td>
  </tr>
</tbody>
</table>

### 🐡处理冒险小结

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L7-Pipeline-33.webp)

#### **经典 5 级流水线实际 CPI 往往大于 1：**

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L7-Pipeline-34.webp)

##### 1. 完全前递代价太大

理论上，如果所有数据冒险都靠前递解决，流水线可以少停顿。

但现实中，**所有可能的 bypass paths 都做出来代价太高**：

- 硬件连接复杂；
- 多路选择器和比较逻辑增加；
- 可能拉长时钟周期。

所以处理器通常只实现常用前递路径。

一些少见的数据依赖仍然可能需要停顿。

---

##### 2. 加载指令有天然延迟

加载指令 `lw / fld` 的数据要等访存之后才可用。

所以如果下一条指令立刻使用加载结果，例如：

```text
lw  x1, 0(x2)
add x3, x1, x4
```

即使有前递，`add` 也可能太早需要 `x1`，因此必须插入一个 bubble。

这就是 **load-use hazard**。

早期 MIPS-I 把这个问题暴露给软件，定义了 **load delay slot**；编译器需要插入无关指令或 `NOP`。
后来 MIPS-II 改为硬件互锁，由硬件自动停顿。

---

##### 3. 跳转和分支会带来 bubble

跳转和条件分支会改变 PC。

如果跳转结果出来前，后面的指令已经被取入流水线，那么错误路径上的指令就要被 Kill，变成 bubble。

没有 delay slot 的机器中，跳转后错误取入的指令会被终止。
有软件可见 delay slot 的机器中，编译器可能插入大量 `NOP` 来保证正确性。

---

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L7-Pipeline-35.webp)

## 🐟超标量处理器（SuperScalar）

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L7-Pipeline-36.webp)

### 🐡为什么要引入超标量处理器？

前面已经讲过，经典 5 级流水线的理想状态是：

```text
CPI = 1
```

也就是平均每个周期完成一条指令。

但这已经是单发射流水线的理想上限。

即使没有冒险，它通常也只是：

```text
每周期启动 1 条指令
```

所以如果还想继续提高性能，就不能只让一条流水线工作，而要让处理器在一个周期内同时启动多条指令。

这就是超标量的核心思想：

> 不只是把指令执行过程重叠起来，而是让多个执行单元在同一个周期内并行处理多条指令。

---

### 🐡什么是超标量 Superscalar？

**超标量处理器**就是：

> 一个周期可以取多条、译码多条、发射多条指令的处理器。

普通流水线：

```text
每周期发射 1 条指令
```

超标量流水线：

```text
每周期发射多条指令
```

例如 PPT 中提到：

```text
4 GHz 4 路多发射
```

意思是处理器频率为 4 GHz，每个周期最多可以发射 4 条指令。

理想情况下：

```text
IPC = 4
CPI = 0.25
```

这里要注意：

到了超标量这里，常用指标从 CPI 转向 IPC。

<table>
<thead>
  <tr>
    <th>
      指标
    </th>
    
    <th>
      含义
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      CPI
    </td>
    
    <td>
      Cycles Per Instruction，每条指令平均需要多少周期
    </td>
  </tr>
  
  <tr>
    <td>
      IPC
    </td>
    
    <td>
      Instructions Per Cycle，每周期平均完成多少条指令
    </td>
  </tr>
</tbody>
</table>

单发射流水线理想情况：

```text
CPI = 1
IPC = 1
```

4 路超标量理想情况：

```text
CPI = 0.25
IPC = 4
```

---

### 🐡超标量依赖“指令级并行”

超标量能不能发挥作用，取决于程序中是否存在足够多的独立指令。

例如：

```text
add x1, x2, x3
sub x4, x5, x6
```

这两条指令互不依赖，可以同时执行。

但如果是：

```text
add x1, x2, x3
sub x4, x1, x6
```

第二条 `sub` 依赖第一条 `add` 的结果，就不能随便同时执行。

所以 PPT 中说：

```text
依赖在实践中减少了 IPC
```

意思是：
虽然理论上 4 路超标量可以达到 `IPC = 4`，但真实程序里存在数据依赖、控制冒险、资源冲突，所以实际 IPC 往往低于峰值。

---

### 🐡乱序执行 Out-of-order 的作用

PPT 接着提到：

```text
乱序 out-of-order 执行
```

它的含义是：

> 硬件动态重新安排指令执行顺序，让不依赖当前阻塞结果的指令先执行。

例如：

```text
lw  x1, 0(x2)
add x3, x1, x4
sub x5, x6, x7
```

这里 `add` 依赖 `lw` 的结果，可能要等内存数据回来。
但是 `sub` 和前两条无关，可以先执行。

顺序执行会卡住：

```text
lw 等待 -> add 等待 -> sub 也被迫等待
```

乱序执行可以变成：

```text
lw 等待时，先执行 sub
```

所以乱序执行的目的不是改变程序最终结果，而是：

> 在保证结果正确的前提下，尽量利用空闲执行单元，减少冒险造成的等待。

---

### 🐡顺序超标量流水线 In-order Superscalar

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L7-Pipeline-37.webp)

也就是**顺序超标量流水线**。

它的特点是：

> 每周期可以取多条、发射多条，但仍然按照程序顺序发射。

PPT 举的例子是：

```text
每周期获取两条指令；
如果一条是整数/内存指令，另一条是浮点指令，则可以同时发射。
```

也就是说，它不是任意两条都能一起发射，而是要看它们能不能分别进入不同的执行单元。

例如：

```text
addi x1, x1, 8
fadd.d f2, f0, f1
```

一条走整数流水线，一条走浮点流水线，就有机会同时执行。

但如果两条都要用同一个整数 ALU，就可能不能同时发射。

所以顺序超标量是一种比较便宜的提高吞吐量的方法，但能力有限。

---

### 🐡为什么超标量会增加硬件复杂度？

超标量不是简单复制几个 ALU 就行。

因为每周期处理多条指令后，很多硬件都要变宽、变复杂：

<table>
<thead>
  <tr>
    <th>
      部分
    </th>
    
    <th>
      复杂点
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      取指
    </td>
    
    <td>
      每周期要取多条指令
    </td>
  </tr>
  
  <tr>
    <td>
      译码
    </td>
    
    <td>
      每周期要同时译码多条指令
    </td>
  </tr>
  
  <tr>
    <td>
      寄存器堆
    </td>
    
    <td>
      需要更多读端口和写端口
    </td>
  </tr>
  
  <tr>
    <td>
      前递/旁路
    </td>
    
    <td>
      多条指令之间可能互相依赖，旁路网络复杂度上升
    </td>
  </tr>
  
  <tr>
    <td>
      发射逻辑
    </td>
    
    <td>
      要判断哪些指令可以一起执行
    </td>
  </tr>
  
  <tr>
    <td>
      提交/异常处理
    </td>
    
    <td>
      要保证程序结果看起来仍然按顺序发生
    </td>
  </tr>
</tbody>
</table>

PPT 中特别提到：

```text
regfile 端口和 bypass 成本增长很快
```

这是超标量设计中的核心难点之一。

比如 1 条指令最多读 2 个寄存器、写 1 个寄存器。

如果每周期发射 4 条指令，理论上可能需要：

```text
8 个读端口 + 4 个写端口
```

寄存器堆会变得很大、很慢、很耗能。

---

### 🐡增加处理器性能的方法

#### 方法一：提高时钟频率

```text
受限于工艺和功耗
```

频率不能无限提高，因为功耗、发热、时序都会成为瓶颈。

#### 方法二：加深流水线

```text
5 级 -> 10 级 -> 15 级
```

把每一级做得更短，可以提高频率。

但问题是：

```text
流水线越深，冒险代价越大
```

尤其是分支预测错误时，要清空更多级流水线，损失更大。

#### 方法三：超标量

```text
多个执行单元，同时执行多条指令
```

理想情况下可以让：

```text
CPI < 1
```

但实际效果高度依赖程序中是否有足够的指令级并行。
