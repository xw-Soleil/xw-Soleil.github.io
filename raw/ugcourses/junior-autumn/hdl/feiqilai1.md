# 飞起来1.0

> HDL 期末复习：Verilog 基础、设计基础、加法器/乘法器、浮点、流水线与协处理器，附练习示例

<alert type="tip">
<mark>

紫色

</mark>

部分是神的重点

</alert>

这一部分主要是来源于Key of the courses，针对前四题

<alert type="tip">

*一：判断题，共5题，每题2分*

*二：选择题，共5题，每题2分*

*三：填空题，共10题，每题3分*

基本的硬件描述语言与设计知识，参考课程核心知识点复习，对应题型一、二、三为主

神：绝大多数人一二三不会有问题

*四：简答题，共5题，每题4分*

课程核心知识点(含作业)中的(紫色)重点，对应题型四为主

神：尽量全面，但是不用写得很长，和作业当中的内容对应（是不是就说明是原题

</alert>

## Verilog 基础

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai1-01.webp)

#### module/endmodule

这是 Verilog 设计的**基本单元**，在硬件上对应一个“黑盒”模块。**综合工具会把它视为一个独立的电路单元**

#### wire/reg

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai1-02.webp)

- `wire` (线网型)：代表物理连线，它**没有存储能力**。它必须被**连续驱动**（例如 `assign` 语句或另一个模块的 `output`）。
![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai1-03.webp)
- `reg` (寄存器型)：代表一个**存储元件**。注意，<mark>

`reg`

</mark>

 <mark>

**不一定**

</mark>

<mark>

会被综合成寄存器（Flip-Flop）。

</mark>


  - 在 `always @(posedge clk)` 块中，它被综合为**时序逻辑**（触发器）。
  - 在 `always @(*)` 块中，它被综合为**组合逻辑**（一堆门电路）。

<table>
<thead>
  <tr>
    <th>
      always 块类型
    </th>
    
    <th>
      敏感列表
    </th>
    
    <th>
      赋值完整性
    </th>
    
    <th>
      综合结果
    </th>
    
    <th>
      硬件实例
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      always @(posedge clk)
    </td>
    
    <td>
      时钟边沿
    </td>
    
    <td>
      (N/A)
    </td>
    
    <td>
      时序逻辑
    </td>
    
    <td>
      触发器 (Flip-Flop)
    </td>
  </tr>
  
  <tr>
    <td>
      always @(*)
    </td>
    
    <td>
      电平（所有输入）
    </td>
    
    <td>
      完整（所有分支/情况都赋值）
    </td>
    
    <td>
      组合逻辑
    </td>
    
    <td>
      门电路 (MUX, Adder...)
    </td>
  </tr>
  
  <tr>
    <td>
      always @(*)
    </td>
    
    <td>
      电平（所有输入）
    </td>
    
    <td>
      不完整（有分支未赋值）
    </td>
    
    <td>
      (意外的) 锁存器 (Latch)
    </td>
    
    <td>
      锁存器 (Latch)
    </td>
  </tr>
</tbody>
</table>

<mark>

**关键**

</mark>

<mark>

：

</mark>

<mark>

`assign`

</mark>

 <mark>

语句的左侧

</mark>

<mark>

**必须**

</mark>

<mark>

是

</mark>

 <mark>

`wire`

</mark>

<mark>

；

</mark>

<mark>

`always`

</mark>

 <mark>

或

</mark>

 <mark>

`initial`

</mark>

 <mark>

块内部被赋值的变量

</mark>

<mark>

**必须**

</mark>

<mark>

是

</mark>

 <mark>

`reg`

</mark>

<mark>

。

</mark>



#### input/output/inout

输入、输出、双向输入输出端口**默认是连线wire类型**

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai1-04.webp)

<table>
<thead>
  <tr>
    <th>
      模块端口方向
    </th>
    
    <th>
      模块内部 (例如 arbiter)
    </th>
    
    <th>
      模块外部 (例如 outer_module)
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      input
    </td>
    
    <td>
      必须是 wire (例如 a)
    </td>
    
    <td>
      可以是 reg 或 wire (例如 A)
    </td>
  </tr>
  
  <tr>
    <td>
      output
    </td>
    
    <td>
      可以是 reg 或 wire (例如 q)
    </td>
    
    <td>
      必须是 wire (例如 Q)
    </td>
  </tr>
  
  <tr>
    <td>
      inout
    </td>
    
    <td>
      必须是 wire (例如 b)
    </td>
    
    <td>
      必须是 wire (例如 B)
    </td>
  </tr>
</tbody>
</table>

模块的端口方向。`inout`（双向端口）在综合中比较特殊，**通常用于实现三态总线**。

#### **逻辑电平----**0/1/z/x

- `0` (逻辑0)、`1` (逻辑1)：对应实际电路的低电平和高电平。
- `z` (高阻态)：**代表没有驱动**。它在硬件上是**真实存在**的（如三态缓冲器），用于实现多路复用的总线。
- `x` (未知态)：代表**逻辑冲突**（如两个驱动源同时驱动一个 `wire` 为 0 和 1）或**未初始化**。`x` 态是**仿真**中的概念，用于调试；在真实硬件中没有 `x`，它会**是一个不确定的 0 或 1**。

初始, 所有变量从X开始

- **X是传播的**，例如：逻辑操作(0 or X) = X
- <mark>

**Z也传播X**

</mark>

，例如：逻辑操作(1 and Z) = X

#### vector

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai1-05.webp)

1. 向量写法，如 `wire [7:0] data;`。这是描述总线的基础。
2. 向量通常左边是高位，上述的例子的`reg [0:20] a;`也可表示为`reg [0:-20] a;`
3. `a[<base_bit> +: <width>]` 代表从一个**基地址 (base bit)** 开始，选择一个**固定宽度 (width)** 的位，如果是减号，就向下去取width位

举例如下，**特别关注****n[3+:2]****取到****Bit4,3****(从3这个基地址含3向上取两位)，****n[3-:2]****取到****Bit3,2****(从3这个基地址含3向下取两位)**

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai1-06.webp)

#### constant

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai1-07.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai1-08.webp)

最高位的扩展

- 最高位是0/1：扩展0，如果是有符号数的负数应该是扩展1
- 最高位x：扩展x
- 最高位z：扩展z

#### parameter

这是实现**可配置、可重用**设计的关键。例如，你可以写一个 `parameter WIDTH = 8` 的 N 位加法器，在实例化时通过修改参数将其配置为 32 位或 64 位。这在综合时是**静态确定的**。

#### initial

<mark>

**仅在仿真开始时执行一次**

</mark>

<mark>

。它

</mark>

<mark>

**几乎不可综合**

</mark>

（唯一的例外是 FPGA 中用于初始化 BRAM/ROM 的内容）。<mark>

`initial`

</mark>

 <mark>

块是

</mark>

 <mark>

**Testbench 的核心**

</mark>

<mark>

，用于

</mark>

<mark>

**产生激励信号**

</mark>

<mark>

。

</mark>



- begin .. end的initial块语句块语句内**串行执行**
- initial块语句是行为构造，**仅在t = 0时执行**

#### always

- <mark>

`always @(posedge clk)`

</mark>

<mark>

：描述

</mark>

<mark>

**时序逻辑**

</mark>

<mark>

（同步电路）。

</mark>
- <mark>

`always @(*)`

</mark>

<mark>

：描述

</mark>

<mark>

**组合逻辑**

</mark>

<mark>

。

</mark>

<mark>

`*`

</mark>

 <mark>

会自动包含所有在块内读取的信号。

</mark>
- always的执行可通过敏感表进行控制

#### `#`延迟写法

**100% 不可综合**。综合工具会**完全忽略**它（例如 `#10`）。它仅用于仿真，在 Testbench 中模拟信号的真实延迟。

##### (1) 延迟类型

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 41.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai1-09.webp" />
      </p>
    </td>
    
    
      <td style="width: 58.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai1-10.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

###### 图例说明

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 60.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai1-11.webp" />
      </p>
    </td>
    
    
      <td style="width: 39.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai1-12.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

##### (2) 最小: 典型: 最大的延迟

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 56.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai1-13.webp" />
      </p>
    </td>
    
    
      <td style="width: 43.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai1-14.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

#### assign

<mark>

连续赋值，描述纯粹的

</mark>

<mark>

**组合逻辑**

</mark>

<mark>

。

</mark>

`assign out = a & b;` 会被综合为一个与门。

实际上assign也是触发逻辑，**assign等号右侧的语句有变化了才会触发整个assign语句驱动**

#### If-else 语句

1. 在硬件上会综合成**优先选择器**（Priority MUX）

<alert type="tip">

但如果条件是明显的互斥逻辑，可能由于综合工具的智能而编码成多路选择器，但if else 给出的大体上的”综合意愿“是优先编码器

</alert>

1. `if` 条件优先级最高。如果 `if/else` 链不完整（缺少 `else`或者覆盖的条件不完整，包括下面这个case语句条件覆盖不完整也是一样），在 `always @(*)` 块中会产生**锁存器 (Latch)** 。
2. If-else在匹配x或z时始终返回假

<alert type="tip">

举例：`if (sel)` 会将`sel`取 `x` 或 `z` 视为 **false**（假）。

</alert>

#### Case 语句（case/casez/casex）

- `case` 会综合成一个**多路选择器 (MUX)**。它通常比 `if/else` 链更优（面积更小，速度更快），因为它暗示了**并行比较**。case语句执行精确相等（相当于全等操作符===） If-else在匹配x或z时始终返回假 。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai1-15.webp)

- `casez`：将 `z` 视为 "don't care"（不关心）。

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 54.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai1-16.webp" />
      </p>
    </td>
    
    
      <td style="width: 45.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai1-17.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

- `casex`：将 `x` 和 `z` 都视为 "don't care"。这在描述某些有无关项的真值表时很有用，可以帮助综合器优化逻辑。
![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai1-18.webp)

#### for

`for` 循环在综合时**不是时间上的循环**，而是**空间上的硬件复制**。一个 `for` 循环会**展开**成一长串的硬件电路。例如，用 `for` 循环写一个 32 位加法器，它会被综合成 32 个全加器。

#### function/task

- <mark>

`function`

</mark>

<mark>

（函数）通常用于描述

</mark>

<mark>

**可重用的组合逻辑**

</mark>

<mark>

，它必须有返回值，且

</mark>

<mark>

**不能包含任何时间控制**

</mark>

<mark>

（如

</mark>

 <mark>

`#`

</mark>

 <mark>

或

</mark>

 <mark>

`@`

</mark>

<mark>

）。

</mark>

<mark>

**至少有一个input端口**

</mark>

<mark>

，并且

</mark>

<mark>

**只有一个output端口**

</mark>
- <mark>

`task`

</mark>

<mark>

（任务）更通用，

</mark>

<mark>

**可以包含时间控制，可以没有返回值**

</mark>

<mark>

。在可综合设计中较少用，但在 Testbench 中非常有用。

</mark>

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai1-19.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai1-20.webp)

#### `$display` / `$finish`

<mark>

系统任务，

</mark>

<mark>

**不可综合**

</mark>

<mark>

，仅用于仿真调试（打印信息、结束仿真）。

</mark>



![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai1-21.webp)

#### 文件相关的系统任务

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 48.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai1-22.webp" />
      </p>
    </td>
    
    
      <td style="width: 51.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai1-23.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 50.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai1-24.webp" />
      </p>
    </td>
    
    
      <td style="width: 49.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai1-25.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

#### FSM (3个always块)

三段式写法：

1. `always @(posedge clk ...)`：**时序逻辑**，只负责状态寄存器（`current_state <= next_state;`）。

```verilog
// Block 1: 状态寄存器 (时序逻辑)
// 负责 state 的存储和更新
always @(posedge clk or negedge rst)
    if (!rst)
        state <= s0; // 复位到初始状态 
    else
        state <= next_state; // 在时钟边沿更新状态
```

1. `always @(*)`：**组合逻辑**，负责根据 `current_state` 和 `inputs` 计算 `next_state`（通常用 `case` 语句）。

```verilog
// Block 2: 下一状态逻辑 (组合逻辑)
// 负责计算 next_state
always @(*)
    case (state)
        s0: if (i == 1'b1)
                next_state = s1;
            else
                next_state = s0;
        s1: ... // s1 的跳转逻辑
        s2: ... // s2 的跳转逻辑
        default:
            next_state = s0; // 原文示例不完整, 但 default 是必需的
    endcase
```

1. `always @(*)` (Mealy型) 或 `always @(posedge clk)` (Moore型)：负责根据 `current_state` (和 `inputs`) 计算**输出**

```verilog
// Block 3: 输出逻辑 
// 负责根据 state 产生输出 q
always @(*) // output encoding 
    case (state)
        s0: q = 1'b0;
        s1: q = 1'b0;
        s2: q = 1'b1;
        default: q = 1'b0;
    endcase
```

#### **数据通路 (2个always块)**

这是指 FSM+Datapath 结构中的 `Datapath`（数据通路）部分。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai1-26.webp)

数据通路所做的事情有两个，一个是直接对传入的数据作**组合逻辑**，通过状态判断直接输出；另外一件事就是把上一件事的输出使用**时序逻辑**存储起来（在实现一个变量反复迭代的时候比较有用）

1. `always @(posedge clk ...)`：**时序逻辑****（非阻塞）**，包含所有的寄存器（如累加器、数据暂存器）。

```verilog
// Block 1: 数据寄存器 (时序逻辑)
// 负责所有数据寄存器的存储
always @(posedge clk or negedge rst) begin
    if (!rst) begin
        r_ld <= 1'b0;
        done <= 1'b0;
        q <= 10'b00_0000_0001;
        // ... r_m, r_n 的复位 (讲义中省略了, 但实际需要)
    end else begin
        done <= n_done;  
        q <= n_q;      
        r_ld <= ld;    
        r_m <= n_m;  
        r_n <= n_n;  
    end
end
```

1. `always @(*)`：**组合逻辑****（阻塞）**，包含所有的运算（如加法器、比较器、MUX）。

```verilog
// Block 2: 数据运算逻辑 (组合逻辑)
// 负责所有的数据计算, 受 FSM 的 state 控制
always @(*) begin
    case (state) // state 来自 FSM 控制器 
        srun: begin
            // 执行运算
            n_m = (r_m > r_n) ? r_m - r_n : r_m;
            n_n = (r_m > r_n) ? r_n : r_n - r_m;
            n_done = (r_m == r_n); 
            n_q = r_m;
        end
        default: begin // 对应 "swait" 状态
            // 加载数据
            n_m = m;
            n_n = n;
            n_done = done;
            n_q = q;
        end
    endcase
end
```

#### <mark>

**阻塞 (**

</mark>

<mark>

**=**

</mark>

<mark>

**) vs 非阻塞 (**

</mark>

<mark>

**<=**

</mark>

<mark>

**)**

</mark>



- **阻塞 (****=****)**：立即求值并赋值。在 `always @(*)` **组合逻辑**中使用。
- **非阻塞 (****<=****)**：在 **always** **块结束时才更新值（调度更新）**。在 `always @(posedge clk)` **时序逻辑**中使用。

<mark>

时序逻辑

</mark>

<mark>

**只用**

</mark>

<mark>

非阻塞；组合逻辑

</mark>

<mark>

**只用**

</mark>

<mark>

阻塞。

</mark>



**为什么？** 如果在时序逻辑中用阻塞，仿真器和综合器（真实硬件）的行为会**不一致**，导致仿真/硬件不匹配。

#### <mark>避免锁存器 (Latch)</mark>

锁存器是电平敏感的存储器，在同步设计中是有害的（会导致时序分析困难、易产生毛刺）。

<mark>

在

</mark>

 <mark>

`always @(*)`

</mark>

 <mark>

块中，如果一个

</mark>

 <mark>

`if`

</mark>

 <mark>

或

</mark>

 <mark>

`case`

</mark>

 <mark>

语句没有覆盖所有分支，并且没有为某个

</mark>

 <mark>

`reg`

</mark>

 <mark>

变量在所有条件下都赋值，综合器为了“记住”上一个值，就会生成一个 Latch。

</mark>



如何避免？

1. 确保 `if/else` 完整。
2. 确保 `case` 有 `default` 分支。
3. 在 `always` 块开头为所有变量赋一个默认值。

#### <mark>代码编写规范与命名法</mark>

## 个人Verilog编码规范

综合上述分析,一套优秀的个人Verilog编码规范应是层次化、多维度的。所以我最终形成的个人规范是以**<span>

规范3

</span>

**的分类法为顶层框架;在词法层面,采纳**<span>

规范2

</span>

**的可读性思想和**<span>

规范1

</span>

**的严谨性;在核心的RTL可综合设计层面,则融合了**<span>

规范4

</span>

**中面向FPGA硬件实现的思想。最终形成的个人Verilog编码规范初版如下:

### 总体原则

1. **可读性**: 代码首先是写给人看的,其次才是给机器编译的。清晰度优先于简洁。
2. **可综合性**: 所有RTL模块必须严格遵循可综合子集。避免使用`#delay`, `initial` (非Testbench中), `force`, `release` 等。
3. **模块化**: 设计应划分为功能明确、接口清晰的模块,以利于复用和维护。
4. **一致性**: 在整个项目中,必须严格遵守同一套命名和格式规范。

### 命名规范

#### 文件

- 每个`module`应存放在一个单独的`.v`文件中。
- 文件名必须与模块名完全一致,采用小写蛇形法(snake_case),例如模块`fp_adder`应在`fp_adder.v`文件中。

#### 模块

- 使用**小写蛇形法 (snake_case)** 命名,例如 `fp_multiplier`, `fpu_pipeline`。

#### 信号 (Signals) 与变量 (Variables)

- 使用**小写蛇形法 (snake_case)** 命名,例如 `operand_a`, `man_product`。
- **时钟 (Clocks)**: 统一命名为 `clk`。
- **复位 (Resets)**: 统一使用**异步、低电平有效**,并命名为 `rst_n`。
- **状态机 (FSM)**: 状态寄存器命名为 `state`, `next_state`。状态名使用全大写加 `S_` 前缀,例如 `S_IDLE`, `S_UNPACK`。

#### 常量与参数 (Constants and Parameters)

- 使用 `localparam` 定义模块内部常量,其命名方式与状态机状态名一致(全大写,`S_`前缀)。
- 在顶层或需要外部配置的模块中使用 `parameter`,其命名应使用全大写蛇形法(UPPER_SNAKE_CASE),例如 `ADDR_WIDTH`。

### 格式与布局规范

#### 模块声明

- 端口声明应进行对齐,以提高可读性。类型、位宽和端口名各列对齐。

```verilog
module fp_adder (
    input  wire        clk,
    input  wire        rst_n,
    input  wire        start,
    input  wire [31:0] operand_a,
    output reg  [31:0] result,
    output reg         busy
);
```

#### 缩进与空格

- **严禁使用** **Tab** **键**。
- 统一使用 **4 个空格** 进行缩进。
- 所有二元运算符(`=`, `+`, `^`, `<=`, `?:`)前后必须有空格。
- `if`, `case`, `always @` 等关键字后留一个空格。

#### 代码块

- `always`, `if`, `case`, `for` 语句块,即使只有一条语句,也**必须**使用 `begin...end` 括起来。
- `begin` 与其关联的语句(如`if`, `else`, `case item`)保持在同一行或遵循对齐规则。`end` 单独占一行,并与 `begin` 的起始位置对齐。

#### 注释

- 在信号声明区,使用 `//` 对逻辑相关的信号组进行注释说明,例如 `// Internal Signals`, `// FSM states`。
- 在端口声明后,可使用对齐的行注释说明端口用途。
- 注释应解释"**为什么 (Why)**",阐明设计意图,而不是简单复述代码"**是什么 (What)**"。

### RTL 可综合设计规范

#### 有限状态机

**结构**: **必须** 采用"两段式"描述:

1. **时序逻辑 (****always @(posedge clk or negedge rst_n****)**: 仅负责状态寄存器 `state` 的更新 (`state <= next_state;`)。
2. **组合逻辑 (****always @(*)****)**: 仅负责根据当前状态 `state` 和输入计算下一状态 `next_state`。

**安全性**: 组合逻辑块中的 `case` 语句**必须** 包含 `default` 分支,并将 `next_state` 指向安全状态(如 `S_IDLE`)。

#### 数据通路

- **结构**: 核心的数据操作逻辑应统一放在一个**独立的时序逻辑块 (****always @(posedge clk or negedge rst_n****)** 中。
- **控制**: 使用状态机生成的 `state` 在该 `always` 块内部通过 `case (state)` 语句来控制多周期操作的流程。
- **复位**: 在该 `always` 块的复位逻辑中,对所有输出端口和关键内部寄存器进行初始化。

#### 赋值规则

- 在**时序逻辑块** (`always @(posedge clk ...)` )中,**必须** 使用**非阻塞赋值 (****<=****)**。
- 在**组合逻辑块** (`always @(*)`)中,**必须** 使用**阻塞赋值 (****=****)**。
- **严禁**在同一个 `always` 块中混合使用阻塞和非阻塞赋值。

#### 时钟与复位

- **严禁门控时钟 (Gated Clocks)**。**必须** 使用时钟使能逻辑替代。
- 设计中所有触发器都应接入统一的全局异步复位信号 `rst_n`。

#### 模块化与实例化

- 大型功能(如加法器、乘法器)应封装为独立的子模块。
- 在顶层模块中实例化子模块时,**必须** 使用**命名端口映射 (Named Port Connections)**,并清晰对齐。

```verilog
// 示例
fp_adder u_adder (
    .clk       (clk),
    .rst_n     (rst_n),
    .start     (adder_start),
    .operand_a (adder_op_a),
    .operand_b (adder_op_b),
    .result    (adder_result),
    .busy      (adder_busy)
);
```

#### <mark>RTL设计(风格)</mark>

RTL (Register-Transfer Level，寄存器传输级) 是设计的**抽象层次**。不描述门，而是描述**数据如何在寄存器之间流动和处理**。

我们写的 `always @(posedge clk)` 就是在定义寄存器，`assign` 和 `always @(*)` 就是在定义寄存器之间的组合逻辑。

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 50.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai1-27.webp" />
      </p>
    </td>
    
    
      <td style="width: 49.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai1-28.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

### 时钟域

#### <mark>单时钟域</mark>

整个设计只有一个时钟，时序分析简单。

<mark>

单时钟域表示只能使用一种时钟，不同边沿的时钟或者是分频的同源时钟，均非单时钟域

</mark>



<alert type="tip">

按照实际元件的复位电路情况，通常使用异步复位。为了减少异步复位的释放问题，通常在系统异步复位信号输入时(或者在测试台Testbench中)<span>

这两种情况取其一就可以

</span>

先做同步化

</alert>

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai1-29.webp)

#### 跨时钟域 (CDC)

设计中有多个**异步**时钟。这是高级主题，数据跨域时必须使用**同步器**（如两级 DFF 同步器）来防止亚稳态。

#### 门控时钟

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai1-30.webp)

用逻辑（如 `clk_gated = clk & enable;`）来关闭部分电路的时钟以省电。**极其危险**，容易产生毛刺。**正确做法**是使用带有时钟使能（CE）的寄存器。

#### 异步复位

<mark>

复位信号

</mark>

<mark>

**独立于时钟**

</mark>

。`always @(posedge clk or negedge rst_n)`。

- 好处是复位立即生效
- 坏处是复位的**释放**（de-assertion）是异步的，可能导致亚稳态，需要“复位同步化”

---

#### Verilog的数据流模型、行为模型、结构(级)模型与一般意义上数字逻辑系统中的行为模型、结构模型是什么关系？ Verilog的结构(级)模型具体指哪种描述方式？

##### 数字逻辑系统

- **行为模型**
  - 关注**功能和算法**，比如布尔方程，状态转移图，真值表
- **结构模型**
  - 关注**底层硬件连接****构成**，比如硬件电路图以及模块框图

##### Verilog

- **行为模型**
  - 主要使用 **always** **和** **initial** **块****，过程赋值**
  - 使用 `if/else`, `case`, `for`等过程化语句来描述电路的行为。
  - **抽象级别**：**高**。是在描述一个**算法**
- **数据流模型**
  - 主要使用 **assign** **连续赋值语句**
  - 使用逻辑运算符（`&`, `|`, `^`）和条件运算符（`?:`）来描述数据在“线网”(`wire`) 上的流动和变换。
  - **抽象级别：中。**是在描述**组合逻辑方程。**
- **结构(级)模型**
  - 主要通过**实例化** (Instantiation) 门或其他模块 (`module`)
  - **抽象级别：低。**是在画电路之间的连线**。**

**总结**： 在Verilog中，**数据流模型（****assign****）和（过程）行为模型（****always****/****initial****）** 都是用来描述系统功能的，可以被泛称为广义的“行为模型” 。而Verilog的**结构模型**则对应广义的“结构模型”，用于描述硬件的连接与构成

##### 关系

- **“一般意义的”行为模型**（如 FSM 图、算法）

  - <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mo>
  
  →
  
  </mo>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  \rightarrow
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:0.3669em;">
  
  
  
  </span>
  
  <span className="mrel">
  
  →
  
  </span>
  </span>
  </span>
  </span>
  
   通常用 Verilog 的**行为模型** (`always` 块) 来实现。
  - <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mo>
  
  →
  
  </mo>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  \rightarrow
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:0.3669em;">
  
  
  
  </span>
  
  <span className="mrel">
  
  →
  
  </span>
  </span>
  </span>
  </span>
  
   简单的组合逻辑（如布尔方程）也可以用 Verilog 的**数据流模型** (`assign`) 来实现。
- **“一般意义的”结构模型**（如门级电路图、模块框图）

  - <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mo>
  
  →
  
  </mo>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  \rightarrow
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:0.3669em;">
  
  
  
  </span>
  
  <span className="mrel">
  
  →
  
  </span>
  </span>
  </span>
  </span>
  
   几乎**一对一**地用 Verilog 的**结构(级)模型**（实例化）来实现。

**RTL (寄存器传输级) 设计**，就是 Verilog **行为模型+数据流模型**

- 用 `always @(posedge clk)` (行为模型) 来描述寄存器（Register）
- 用 `assign` (数据流模型) 或 `always @(*)` (行为模型) 来描述寄存器之间的组合逻辑，即数据“传输”和处理

而**综合 (Synthesis)** 工具的核心工作，就是把 **RTL 代码**（行为/数据流模型）**“翻译”成一个纯粹的、由标准单元（基本门电路）组成的 Verilog 结构(级)模型（即门级网表 Netlist**）

##### **Verilog 的结构(级)模型**

<mark>

具体指的就是：

</mark>

<mark>

**通过“实例化”（Instantiation）已有的、更低级的模块，并定义它们之间端口连接方式来描述电路**

</mark>

<mark>

的编码方式。

</mark>



---

## 设计基础

#### VLSI/FPGA设计流程？自顶向下与自底向上在设计中的作用是什么？<mark>前端设计方法学是怎样的？</mark>

VLSI (ASIC)以及FPGA的设计流程分为“前端”和“后端”，**两者以“逻辑综合”为界**。

##### 前端设计流程

前端设计中，VLSI 和 FPGA 基本相同

1. **需求规格 (Specification)**: 定义芯片的功能、性能（速度）、功耗、面积等指标。
2. **架构设计 (Architecture Design)**: 根据需求，设计系统的高层框图，划分主要功能模块（如 CPU 核、内存控制器、外设接口等），定义模块间的接口和时序。
3. **RTL 描述 (RTL Description)**: 使用硬件描述语言 (HDL，如 Verilog 或 VHDL) 对每个模块的行为和数据流动进行代码实现。
4. **功能验证 (Functional Verification)**: 编写测试平台 (Testbench)，通过仿真 (Simulation) 来验证 RTL 代码的功能是否符合设计规格。
5. **逻辑综合 (Logic Synthesis)**: 使用EDA工具（如 Synopsys Design Compiler）将 HDL 代码“翻译”成由基本逻辑门（与门、或门、触发器等）组成的门级网表 (Gate-level Netlist)。

##### 后端设计流程

后端设计中，VLSI 和 FPGA 有一定的区别

###### VLSI (ASIC) 后端流程：

1. **布局规划 (Floorplanning)**: 规划芯片上各个大模块（宏单元）的摆放位置。
2. **布局布线 (Place & Route, P&R)**:

  - **布局 (Placement)**: 确定标准单元（逻辑门）的具体物理位置。
  - **时钟树综合 (CTS)**: 生成时钟网络，确保时钟信号低延迟、低偏移地到达所有触发器。
  - **布线 (Routing)**: 使用金属层连接所有单元，形成完整的电路。
3. **物理验证 (Physical Verification)**: 确保物理版图 (Layout) 正确。

  - **DRC (Design Rule Check)**: 检查版图是否符合制造厂的工艺规则（如最小线宽、间距）。
  - **LVS (Layout vs. Schematic)**: 检查版图提取出的电路，是否与综合后的门级网表一致。
4. **流片实现 (Tape-out)**: 将最终的GDSII版图文件交给芯片代工厂 (Foundry) 进行制造。
5. **板级验证 (Board-level Verification)**: 芯片制造回来后，焊接到 PCB 板上进行真实环境的测试。

###### FPGA 后端流程：

FPGA 流程相对简单，因为物理结构是固定的

1. **实现 (Implementation)**: 对应 ASIC 的 P&R。

  - **布局 (Place)**: 将综合后的逻辑“映射”并“放置”到 FPGA 内部的逻辑单元 (LUT, FF) 上。
  - **布线 (Route)**: 利用 FPGA 内部的可编程布线资源连接这些逻辑单元。
2. **生成比特流 (Bitstream Generation)**: 将布局布线的结果生成一个 .bit 配置文件。
3. **板级验证 (Board-level Verification)**: 将比特流下载到 FPGA 芯片中，在开发板上验证实际功能。

##### 自顶向下与自底向上

1. **自顶向下 (Top-down)**: 适用于较为大型且复杂的系统设计，具有全局视角和模块化结构，自顶向下可以将一个复杂的系统（如一颗 SoC）分解为CPU、GPU、总线、内存控制器等子模块，并定义好它们之间的接口。
2. **自底向上 (Bottom-up)**: 适用于较为小型的系统或已有模块的可重用项目，能够更快地验证基础功能。比如使用 IP 核就是一种“自底向上”的设计，在实现一些子模块时，会大量使用 IP (Intellectual Property) 核。这些 IP 核（例如一个现成的 USB 控制器或一个 ARM CPU 核）是预先设计和验证好的、可重用的模块。
3. **混合式 (Meet-in-the-middle)**: 但是在现代 IC 设计中，大多时候都是采用“混合式”的方法，架构师“自顶向下”定义框架，工程师“自底向上”用 IP 或标准单元库搭建模块，最终在系统层面集成起来。

##### <mark>前端设计方法学</mark>

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai1-31.webp)

<mark>

前端设计方法学是一种

</mark>

 <mark>

从行为描述，到RTL（寄存器传输级）设计、验证与综合的连贯流程

</mark>

 <mark>

。其核心是如何从“系统功能”转变为“门级网表”

</mark>



**前端设计方法学 (Front-end Design Methodology)** ——将一个抽象的**算法或功能概念**，一步步地转变为一个具高效、正确、可验证和可综合的 RTL 代码。

1. **行为（功能需求）描述 (Behavioral Description)**——确定**算法的功能和逻辑**，而不关心具体的硬件实现；具体使用流图或者可执行代码来实现
2. **架构设计 (Architecture Design)**——将抽象的“行为”**划分 (Partition)** 成可以协同工作的硬件模块。即 FSM + Datapath 架构：

  - **控制器 (Controller / FSM):** 作为“大脑”，是一个有限状态机，负责发出控制命令（如 `wait`, `run`）和决策。
  - **数据通路 (Datapath):** 负责存储数据（用寄存器）并执行所有运算（如加法、减法、比较）。
3. **RTL 代码编写 (RTL Coding)**——使用硬件描述语言 (HDL，如 Verilog 或 VHDL)，将“控制器”和“数据通路”翻译成可综合的寄存器传输级 (RTL) 代码。
4. **验证 (Verification / 测试台)**——编写一个“测试台 (Testbench)”——这是另一段（不可综合的）代码，用于模拟各种输入激励，并自动检查 RTL 模块的输出是否符合预期。
5. **逻辑综合 (Logic Synthesis)**——使用综合器（如 Synopsys Design Compiler 或 Vivado Synthesis）将RTL 代码转换为由逻辑门和触发器构成的门级网表

---

<alert type="tip">

感觉这个有点少

1. **基于 HDL 的抽象**：使用 Verilog/VHDL 在寄存器传输级 (Register Transfer Level, RTL) 对电路进行行为描述。RTL 关注的是数据如何在时钟的驱动下，在寄存器之间流动和处理。
2. **综合 (Synthesis) 自动化**：设计者只需编写功能正确的 RTL 代码，并提供时序、面积等约束 (Constraints)，EDA 综合工具会自动将其转换为门级网表。
3. **验证驱动 (Verification-driven)**：由于设计规模巨大，验证（仿真）的复杂度远超设计本身。现代前端方法学（如 UVM）强调在设计初期就制定完备的验证计划，通过搭建可重用的、高覆盖率的测试平台来确保 RTL 功能的正确性，在流片前尽可能多地发现 Bug。

</alert>

---

#### <mark>关键路径、虚假路径、冗余路径的概念？不可到达状态、沉没状态的概念？设计评价：面积/时钟(性能)/功耗</mark>

##### 关键路径

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai1-32.webp)

<mark>

**关键路径**

</mark>

<mark>

是指：

</mark>



1. <mark>

在同步时序电路中，

</mark>

<mark>

**信号传播延迟时间最长的那条路径**

</mark>

。通常指两个相邻触发器 (FF) 之间的组合逻辑路径。
2. <mark>

关键路径延迟决定了

</mark>

<mark>

**电路的最小时钟周期**

</mark>

<mark>

，

</mark>

从而决定了系统的**最高工作频率**。静态时序分析 (STA) 的核心任务就是找到并优化关键路径。

##### 虚假路径

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 49.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai1-33.webp" />
      </p>
    </td>
    
    
      <td style="width: 50.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai1-34.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

<mark>

**虚假路径**

</mark>

<mark>

是指

</mark>



- <mark>

一条

</mark>

<mark>

**由于逻辑条件的约束，在物理结构上存在，但在逻辑功能上不会被激活的路径**

</mark>

<mark>

。

</mark>

<alert type="tip">

比如一个<mark>

多路选择器 (MUX)

</mark>

，由控制信号S选择输入A。此时从输入B到输出的路径虽然物理存在，但逻辑上永远不通，这就是一条虚假路径。

必须在约束中明确告知 STA 工具这些路径是虚假路径 (如使用 set_false_path 命令)，否则工具会错误地将其（如果延迟很长）当作关键路径来优化，浪费资源并可能导致时序无法收敛。

</alert>

##### 冗余路径

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 50.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai1-35.webp" />
      </p>
    </td>
    
    
      <td style="width: 49.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai1-36.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

<mark>

**冗余路径**

</mark>

<mark>

指电路中

</mark>

<mark>

**那些可以被移除，而不改变其静态逻辑功能的门或连线**

</mark>

<mark>

。

</mark>

<mark>

（

</mark>

<mark>

**可以被激活**

</mark>

<mark>

，但其结果“无关紧要”）。

</mark>



冗余路径带来的问题：

1. **浪费 PPA**： 浪费芯片面积，并产生不必要的静态和动态功耗。
2. **降低可测性**： 冗余逻辑会导致某些“固定型故障” (Stuck-at Faults) 无法被检测（即故障被屏蔽），从而降低芯片的测试覆盖率。

逻辑综合工具的一个主要目标就是识别并消除有害的冗余逻辑。

##### 不可到达状态

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai1-37.webp)

<mark>

在

</mark>

<mark>

**有限状态机 (FSM) 中，从“复位状态” (Reset State) 开始，无论通过怎样的输入序列，都永远无法进入的状态**

</mark>

<mark>

。

</mark>



不可到达状态带来的问题：

1. **资源浪费**： 它们占用了状态编码（需要触发器），但从未被使用。
2. **较差的鲁棒性**： 尽管逻辑上不可达，但噪声或毛刺可能使 FSM 意外跳入这些状态。设计时应确保即使进入了不可达状态，也能有一个明确的路径返回到已知状态，而不是卡死。

##### **沉没状态**

<mark>

这是

</mark>

<mark>

**一个（或一组）状态，FSM 一旦进入，就再也无法通过任何输入序列跳出到该状态（组）之外**

</mark>

<mark>

。

</mark>



绝大多数情况下，这是较为严重的设计缺陷，会导致系统“卡死”或“锁定”。

<alert type="tip">
<mark>

**不可到达状态是只能出不能进，沉没状态是只能进不能出**

</mark>
</alert>

##### 设计评价：面积/时钟(性能)/功耗

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai1-38.webp)

<alert type="tip">

这是评价一个 IC 设计好坏的三个核心且**相互制约**的指标。

</alert>

###### 面积

1. 在 ASIC 中指最终版图的物理面积；在 FPGA 中指占用的逻辑资源；
2. 在设计早期也常用**“等效NAND2门数”**来估算。

<alert type="tip">

NAND 2 ——二输入与非门

</alert>

###### 性能

最核心指标是最高工作频率（由关键路径决定）。其他指标还包括吞吐量（单位时间处理的数据量）和延迟（完成一次操作所需的时间）。

###### 功耗

分为两部分：

1. 动态功耗: 电路翻转时产生的功耗。
2. 静态功耗: 也称泄漏功耗 (Leakage)。晶体管即使在关闭状态下也存在的泄漏电流 ( `I_{leakage}`) 导致的功耗。

<mark>

在先进工艺 (28nm 及以下) 中，静态功耗已成为总功耗的主要部分

</mark>

。

###### 权衡

这三者是相互冲突的。例如：

- 提高性能通常需要增加功耗，也可能增加面积（插入 Buffer）。
- 减少面积可能导致布线拥挤增加延迟降低性能。

设计的目标就是在三者之间找到符合产品需求的最优平衡点。

---

#### <mark>ASM图方法、</mark>    <mark>系统框图概念与形式，</mark>    <mark>如何编写控制器/状态机、数据通路的Verilog代码？</mark>

##### ASM图方法（算法状态机）

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai1-39.webp)

ASM 图是一种用于描述数字系统行为的专用流程图。它与普通流程图的最大区别在于，它<mark>

**将控制逻辑（状态）与数据通路（操作）联系起来，并内置了时钟周期的概念**

</mark>

<mark>

。

</mark>



由<mark>

状态框、判断框、条件输出框

</mark>

组成：

1. **状态框**:
  - 形状：矩形。
  - 含义： 代表一个 FSM 状态。
  框内列出在该状态下（无论条件如何）始终为真的 Moore 型输出和无条件的数据操作（例如：regA <= regB）。
2. **判断框**:
  - 形状： 菱形。
  - 含义： 检查一个或多个输入信号或数据通路的状态（例如 counter == 0）。
  它本身不消耗时间，在一个时钟周期内完成判断，并引出两个分支（True / False）。
3. **条件输出框**:
  - 形状： 椭圆形或圆角矩形。
  - 含义： 代表 Mealy 型输出或有条件的数据操作。
  只有当判断框的路径为 True 时，这些输出或操作才会在当前状态下被激活。

ASM 图的一个“状态路径”（从一个状态框出发，经过若干判断框和条件输出框，最终到达下一个状态框）中的所有操作，都在一个时钟周期内完成。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai1-40.webp)

##### 系统框图

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai1-41.webp)

<mark>

系统框图

</mark>

<mark>

是

</mark>

<mark>

**描述模块组成**

</mark>

<mark>

和他们之间

</mark>

<mark>

**连接关系**

</mark>

<mark>

的框图

</mark>

，包括：

1. **方框**: 代表主要的硬件模块，如 “控制器(FSM)”、“数据通路(Datapath)”、“ALU”、“寄存器堆(Register File)”、“内存接口”等。
2. **连线**: 代表信号和数据总线（标注信号名和位宽、流向等）
3. **标注**: 必须清晰标注信号的名称 (如 data_bus)、流向 (用箭头) 和位宽 (如 <span>

31:0

</span>

)。

它是架构设计的核心产物，用于指导后续的RTL编码。它定义了整个系统的接口 (Interface) 和模块划分 (Modularity)。

<alert type="tip">

下面两个FSM以及DataPath的具体实例细节可以回到前面Verilog基础部分看

</alert>

##### 编写控制器 (FSM - 状态机)

控制器的Verilog代码本质上是在描述一个有限状态机，过程如下：

1. **定义状态**：定义所有状态的名称和编码（如 `IDLE`, `CALC`, `DONE`）。
2. **“三段式”****状态机编写**：

  1. **状态更新** **(时序逻辑)**： 编写一个 `always_ff` 块。在时钟沿更新当前状态 `current_state`。
  2. **次态计算** **(组合逻辑)**： 编写一个 `always_comb` 块，通常使用 case 语句。它的工作是根据 当前状态`current_state` 和外部输入，来决定下一个状态 (`next_state`) 应该是什么。
  3. **组合输出****(组合逻辑)**： 编写另一个 `always_comb` 块或使用 assign。根据当前状态`current_state`（**如果是Mealy型，还包括外部输入**），确定输出的控制信号

##### 编写数据通路

数据通路不关心状态，只负责执行操作。它的Verilog代码是在描述和连接硬件组件：

1. **描述寄存器(存储****单元****)**：

  - 为所有需要存储数据的单元（如寄存器、计数器）编写 `always_ff` 块。
  - 这些块的使能信号（如 `if (reg_write_enable)`）直接由控制器的输出控制信号驱动。
2. **描述运算和选择(操作)**：

  - 使用组合逻辑描述运算器（加法器、ALU）和选择器（MUX）
  - 这通常用 `assign` 语句或 `always_comb` 块来实现。

<alert type="tip">

（例如 `assign sum = a + b;`）

`always_comb` 块用于复杂的MUX或ALU

</alert>

- 这些单元的选择信号（如 `mux_select`）**也由控制器**的输出控制信号**驱动**。

<alert type="tip">

数据通路就是用 `always_ff` 描述所有“存东西”的部件，用 `assign` 或 `always_comb` 描述所有“算东西”和“选东西”的部件，而所有这些部件的“开关”都由控制器来控制。

</alert>

---

#### <mark>什么是综合？可综合的关键：1 基于RTL描述的前提；2 可以通过综合工具将Verilog行为级代码变成基于特定工艺的标准单元的门级表示；3 综合前后的模拟行为未改变</mark>

##### <mark>综合是通过代工厂的标准门级单元库，将RTL代码映射成电路实现的，并且综合前后的模拟行为一致</mark>

**综合 (Synthesis)** 工具的核心工作，就是把 **RTL 代码**（行为/数据流模型）**“翻译”成一个纯粹的、由标准单元（基本门电路）组成的 Verilog 结构(级)模型（即门级网表 Netlist**）

主要是记住这个吧

##### **可综合的关键**：

<mark>

1 基于RTL描述的前提

</mark>



<mark>

2 可以通过综合工具将Verilog行为级代码变成基于特定工艺的标准单元的门级表示

</mark>



<mark>

3 综合前后的模拟行为未改变

</mark>



---

#### <mark>Testbench的主要框架是根据测试向量、检查测试结果来进行设计实例的测试，测试向量(可以通过initial与延迟按时间串行执行)主要是随机生成的或者已知结果的测试。测试结果主要通过测试覆盖率来保证，实际是依赖于工具的代码测试覆盖率。Testbench的主要作用是重用与回归测试</mark>

分成几句话理解：

##### <mark>Testbench的主要框架是根据测试向量、检查测试结果来进行设计实例的测试</mark>

怎么测试？用测试向量和检查测试结果来测试设计的实例

##### <mark>测试向量(可以通过initial与延迟按时间串行执行)主要是随机生成的或者已知结果的测试</mark>

测试向量哪来？随机生成的或已知结果的测试

##### <mark>测试结果主要通过测试覆盖率来保证，实际是依赖于工具的代码测试覆盖率</mark>

怎么知道测试结果好不好？用测试覆盖率

##### <mark>Testbench的主要作用是重用与回归测试</mark>

今天写的**RTL 级** Testbench，等你的设计被**综合**成门级网表后，这个 Testbench 还可以**重用，重新运行（回归）你所有的 1000 个测试用例。这个过程就叫回归测试**

当设计更新后，验证工程师只需重新运行（即“回归”）这一整套自动化的测试用例集。测试台会自动施加所有激励并报告任何因代码修改而导致的功能失效 。这确保了设计的健壮性，是“回归测试”的真正价值所在。

---

#### <mark>全加器、半加器、进位保留加法器、先行进位加法器、进位跳跃加法器、进位选择加法器的概念</mark>

##### **半加器**

- 实现两个 1-bit 二进制数相加。
- 无法处理来自低位的进位, 因此不能单独用作多位加法器的基本单元。

`sum = a ^ b`

`c_out = a & b`

##### **全加器**

- 实现三个 1-bit 二进制数相加。这是构成多位加法器的基本单元。

表达式：

<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

S

</mi>

<mo>

=

</mo>

<mi>

A

</mi>

<mo>

⊕

</mo>

<mi>

B

</mi>

<mo>

⊕

</mo>

<msub>
<mi>

C

</mi>

<mrow>
<mi>

i

</mi>

<mi>

n

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

S = A \oplus B \oplus C_{in}

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

<span className="mord,mathnormal">

A

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

⊕

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0502em;">

B

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

⊕

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

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
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

in

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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

 **和即为三者的异或**

<span className="katex">
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

o

</mi>

<mi>

u

</mi>

<mi>

t

</mi>
</mrow>
</msub>

<mo>

=

</mo>

<mo stretchy="false">

(

</mo>

<mi>

A

</mi>

<mo>

⋅

</mo>

<mi>

B

</mi>

<mo stretchy="false">

)

</mo>

<mo>

+

</mo>

<mo stretchy="false">

(

</mo>

<mi>

A

</mi>

<mo>

⋅

</mo>

<msub>
<mi>

C

</mi>

<mrow>
<mi>

i

</mi>

<mi>

n

</mi>
</mrow>
</msub>

<mo stretchy="false">

)

</mo>

<mo>

+

</mo>

<mo stretchy="false">

(

</mo>

<mi>

B

</mi>

<mo>

⋅

</mo>

<msub>
<mi>

C

</mi>

<mrow>
<mi>

i

</mi>

<mi>

n

</mi>
</mrow>
</msub>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

C_{out} = (A \cdot B) + (A \cdot C_{in}) + (B \cdot C_{in})

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
<span className="vlist" style="height:0.2806em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

o

</span>

<span className="mord,mathnormal,mtight">

u

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

<span className="mopen">

(

</span>

<span className="mord,mathnormal">

A

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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0502em;">

B

</span>

<span className="mclose">

)

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

<span className="mord,mathnormal">

A

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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

in

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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

<span className="mord,mathnormal" style="margin-right:0.0502em;">

B

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
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

in

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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

 **只要有任意两个为1，就得进位**

##### **行波进位加法器(RCA)**

这种加法器就是直接把N个全加器串联在一起，但是这样第N个全加器就必须等到第N-1个执行完才能执行，这样就会很慢，下面这些加法器就是来解决这个问题的

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai1-42.webp)

上面这个行波进位加法器，属于是空间增大

下面这个串联加法器是增大时间，“用时间换空间”

##### **串联加法器**

用触发器“记住”进位，只用一个全加器 (FA) ，但我用 N 个时钟周期来完成 N bit 的加法

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai1-43.webp)

##### **先行进位加法器（CLA）**

并行计算所有位的进位, 打破 RCA 的`O(N)`串行依赖。

延迟为`O(log N)`（对于多级分层 CLA）。

<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

G

</mi>

<mi>

i

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

G_i

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

G

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

 (进位产生位 - Generate): <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

G

</mi>

<mi>

i

</mi>
</msub>

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
</mrow>

<annotation encoding="application/x-tex">

G_i = a_i b_i

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

G

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
</span>
</span>
</span>

 均为1，就会产生进位

<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

P

</mi>

<mi>

i

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

P_i

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
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.1389em;margin-right:0.05em;">
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

 (进位传播位 - Propagate): <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

P

</mi>

<mi>

i

</mi>
</msub>

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
</mrow>

<annotation encoding="application/x-tex">

P_i = a_i + b_i

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
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.1389em;margin-right:0.05em;">
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
</span>
</span>
</span>

 只要有一个为1，如果有一个cin是1，那么就会“传播”进位

于是，可以得到<span className="katex">
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

<msub>
<mi>

G

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

P

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

c_{i+1} = G_i + P_i c_i

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
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

G

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
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.1389em;margin-right:0.05em;">
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

，这样我们就有一个递推公式了

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 47.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai1-44.webp" />
      </p>
    </td>
    
    
      <td style="width: 52.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai1-45.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai1-46.webp)

于是可以得出CLA的工作流程

1. **Stage 1 (并行)：**
  - 在**一瞬间**，所有位的 G_i (用 AND 门) 和 P_i (用 OR 门) 都可以被**同时**计算出来，因为它们只依赖 a_i 和 b_i。
2. **Stage 2 (并行 - 核心)：**
  - 一个专门的、复杂的“**先行进位部件 (Lookahead Carry Unit)**”接收所有的 G_i, P_i 和 c_0。
  - 它使用上面那些“扩展后”的并行公式，**同时**计算出 c_1, c_2, c_3, ... c_n。
  - 这就是 PPT 说的“扩展的公式不依赖于中间的进位” 和“进位链逻辑扁平化”。
3. **Stage 3 (并行)：**
  - 现在我们有了所有的 c_i (来自 Stage 2) 和 P_i, G_i (来自 Stage 1)。
  - 我们可以**同时**计算出所有位的“和” s_i。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai1-47.webp)

##### **进位跳跃加法器**

分块，若都是（01）组合，则进位跳过这一块

<alert type="tip">

如果某一位 i，它的输入 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

a

</mi>

<mi>

i

</mi>
</msub>

<mo mathvariant="normal">

≠

</mo>

<msub>
<mi>

b

</mi>

<mi>

i

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

a_i \neq b_i

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
</span>
</span>
</span>

（即 a_i=1, b_i=0 或 a_i=0, b_i=1），那么这一位的输出进位 c_{i+1} 就**完全等于**它的输入进位 c_i。

<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

a

</mi>

<mi>

i

</mi>
</msub>

<mo>

⊕

</mo>

<msub>
<mi>

b

</mi>

<mi>

i

</mi>
</msub>

<mo>

=

</mo>

<mn>

1

</mn>
</mrow>

<annotation encoding="application/x-tex">

a_i \oplus b_i = 1

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

⊕

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

 (这是一个“传播” Propagate 条件)

</alert>

- 在特定条件下, 让进位 *“跳过” (Skip/Bypass)* 某些加法器块。
- 对 RCA 的一种低成本改进, 性能优于 RCA, 但逊于 CLA。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai1-48.webp)

**检测什么**

- **跳跃条件：** ( <span className="katex">
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

<mo mathvariant="normal">

≠

</mo>

<msub>
<mi>

b

</mi>

<mn>

0

</mn>
</msub>
</mrow>

<annotation encoding="application/x-tex">

a_0 \neq b_0

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
<span className="strut" style="height:0.8444em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

b

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

 ) **AND** ( <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

a

</mi>

<mn>

1

</mn>
</msub>

<mo mathvariant="normal">

≠

</mo>

<msub>
<mi>

b

</mi>

<mn>

1

</mn>
</msub>
</mrow>

<annotation encoding="application/x-tex">

a_1 \neq b_1

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
<span className="strut" style="height:0.8444em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

b

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
</span>
</span>
</span>

 )。
- **不跳跃条件：** ( <span className="katex">
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

<mo>

=

</mo>

<msub>
<mi>

b

</mi>

<mn>

0

</mn>
</msub>
</mrow>

<annotation encoding="application/x-tex">

a_0 = b_0

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

b

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

 ) **OR** ( <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

a

</mi>

<mn>

1

</mn>
</msub>

<mo>

=

</mo>

<msub>
<mi>

b

</mi>

<mn>

1

</mn>
</msub>
</mrow>

<annotation encoding="application/x-tex">

a_1 = b_1

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

b

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
</span>
</span>
</span>

 )。 （即，只要有任何一位不满足传播条件，就必须老老实实地计算内部进位）。

**分析** **sel** **信号（选择信号）：**

- 第一个 XNOR 门计算 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msubsup>
<mi>

P

</mi>

<mn>

0

</mn>

<mo mathvariant="normal" lspace="0em" rspace="0em">

′

</mo>
</msubsup>

<mo>

=

</mo>

<mo stretchy="false">

(

</mo>

<msub>
<mi>

a

</mi>

<mn>

0

</mn>
</msub>

<mtext>

XNOR

</mtext>

<msub>
<mi>

b

</mi>

<mn>

0

</mn>
</msub>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

P_0' = (a_0 \text{ XNOR } b_0)

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.2481em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.7519em;">
<span style="top:-2.4519em;margin-left:-0.1389em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">

0

</span>
</span>
</span>

<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">

′

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.2481em;">
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

<span className="mopen">

(

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

<span className="mord,text">
<span className="mord">

XNOR

</span>
</span>

<span className="mord">
<span className="mord,mathnormal">

b

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

<span className="mclose">

)

</span>
</span>
</span>
</span>

。当 <span className="katex">
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

<mo>

=

</mo>

<msub>
<mi>

b

</mi>

<mn>

0

</mn>
</msub>
</mrow>

<annotation encoding="application/x-tex">

a_0 = b_0

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

b

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

 时，<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msubsup>
<mi>

P

</mi>

<mn>

0

</mn>

<mo mathvariant="normal" lspace="0em" rspace="0em">

′

</mo>
</msubsup>

<mo>

=

</mo>

<mn>

1

</mn>
</mrow>

<annotation encoding="application/x-tex">

P_0' = 1

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.2481em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.7519em;">
<span style="top:-2.4519em;margin-left:-0.1389em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">

0

</span>
</span>
</span>

<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">

′

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.2481em;">
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

1

</span>
</span>
</span>
</span>

。
- 第二个 XNOR 门计算 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msubsup>
<mi>

P

</mi>

<mn>

1

</mn>

<mo mathvariant="normal" lspace="0em" rspace="0em">

′

</mo>
</msubsup>

<mo>

=

</mo>

<mo stretchy="false">

(

</mo>

<msub>
<mi>

a

</mi>

<mn>

1

</mn>
</msub>

<mtext>

XNOR

</mtext>

<msub>
<mi>

b

</mi>

<mn>

1

</mn>
</msub>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

P_1' = (a_1 \text{ XNOR } b_1)

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.2481em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.7519em;">
<span style="top:-2.4519em;margin-left:-0.1389em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">

1

</span>
</span>
</span>

<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">

′

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.2481em;">
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

<span className="mopen">

(

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

<span className="mord,text">
<span className="mord">

XNOR

</span>
</span>

<span className="mord">
<span className="mord,mathnormal">

b

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

<span className="mclose">

)

</span>
</span>
</span>
</span>

。当 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

a

</mi>

<mn>

1

</mn>
</msub>

<mo>

=

</mo>

<msub>
<mi>

b

</mi>

<mn>

1

</mn>
</msub>
</mrow>

<annotation encoding="application/x-tex">

a_1 = b_1

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

b

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
</span>
</span>
</span>

 时，<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msubsup>
<mi>

P

</mi>

<mn>

1

</mn>

<mo mathvariant="normal" lspace="0em" rspace="0em">

′

</mo>
</msubsup>

<mo>

=

</mo>

<mn>

1

</mn>
</mrow>

<annotation encoding="application/x-tex">

P_1' = 1

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.2481em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.7519em;">
<span style="top:-2.4519em;margin-left:-0.1389em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">

1

</span>
</span>
</span>

<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">

′

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.2481em;">
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

1

</span>
</span>
</span>
</span>

。
- 最后的 OR 门计算 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mtext>

sel

</mtext>

<mo>

=

</mo>

<msubsup>
<mi>

P

</mi>

<mn>

0

</mn>

<mo mathvariant="normal" lspace="0em" rspace="0em">

′

</mo>
</msubsup>

<mtext>

OR

</mtext>

<msubsup>
<mi>

P

</mi>

<mn>

1

</mn>

<mo mathvariant="normal" lspace="0em" rspace="0em">

′

</mo>
</msubsup>
</mrow>

<annotation encoding="application/x-tex">

\text{sel} = P_0' \text{ OR } P_1'

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,text">
<span className="mord">

sel

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
<span className="strut" style="height:1em;vertical-align:-0.2481em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.7519em;">
<span style="top:-2.4519em;margin-left:-0.1389em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">

0

</span>
</span>
</span>

<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">

′

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.2481em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>

<span className="mord,text">
<span className="mord">

OR

</span>
</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.7519em;">
<span style="top:-2.4519em;margin-left:-0.1389em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">

1

</span>
</span>
</span>

<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">

′

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.2481em;">
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
- 所以，<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mtext>

sel

</mtext>

<mo>

=

</mo>

<mo stretchy="false">

(

</mo>

<msub>
<mi>

a

</mi>

<mn>

0

</mn>
</msub>

<mo>

=

</mo>

<msub>
<mi>

b

</mi>

<mn>

0

</mn>
</msub>

<mo stretchy="false">

)

</mo>

<mtext>

OR

</mtext>

<mo stretchy="false">

(

</mo>

<msub>
<mi>

a

</mi>

<mn>

1

</mn>
</msub>

<mo>

=

</mo>

<msub>
<mi>

b

</mi>

<mn>

1

</mn>
</msub>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

\text{sel} = (a_0 = b_0) \text{ OR } (a_1 = b_1)

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,text">
<span className="mord">

sel

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

<span className="mopen">

(

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
<span className="mord,mathnormal">

b

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

<span className="mclose">

)

</span>

<span className="mord,text">
<span className="mord">

OR

</span>
</span>

<span className="mopen">

(

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
<span className="mord,mathnormal">

b

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

<span className="mclose">

)

</span>
</span>
</span>
</span>

。
- **sel=1** **意味着 "不跳跃"** （因为至少有一位不满足传播条件）。

**分析 MUX（多路选择器）：**

- **输入 0：** "跳跃的进位 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

c

</mi>

<mn>

0

</mn>
</msub>
</mrow>

<annotation encoding="application/x-tex">

c_0

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

c

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

"
- **输入 1：** "内部的进位 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

c

</mi>

<mn>

2

</mn>
</msub>
</mrow>

<annotation encoding="application/x-tex">

c_2

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

c

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

 或 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

G

</mi>

<mn>

2

</mn>
</msub>
</mrow>

<annotation encoding="application/x-tex">

G_2

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

G

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

" (即在块内部通过RCA正常算出来的 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

c

</mi>

<mn>

2

</mn>
</msub>
</mrow>

<annotation encoding="application/x-tex">

c_2

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

c

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

)
- **选择端：** `sel`

##### **进位选择加法器**

对不同的ci都进行计算，得到两个结果，再用MUX选择器

- 推测计算 (Speculative Execution)。与其等待`C_{in}`, 不如先计算出两种可能的结果。
- 性能*:* 速度快（接近 CLA）, 但代价是面积（几乎两套加法电路 + MUX）。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai1-49.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai1-50.webp)

**并行计算：** "进位0" 电路和 "进位1" 电路**同时**开始工作，它们都不需要等待 <span className="katex">
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

i

</mi>

<mi>

n

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

C_{in}

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
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

in

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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

，而是各自按自己的“假设”进行计算。

**等待** <span className="katex">
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

i

</mi>

<mi>

n

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

C_{in}

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
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

in

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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

**：** "前级" 电路（可能是另一个加法器块）最终会算出一个**真实**的 <span className="katex">
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

i

</mi>

<mi>

n

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

C_{in}

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
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

in

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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

**选择 (Select)：**

- 这个**真实**的 <span className="katex">
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

i

</mi>

<mi>

n

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

C_{in}

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
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

in

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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

 被直接用作一组“多路选择器”(MUX) 的**选择信号 (sel)**。
- 每一个 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

S

</mi>

<mi>

i

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

S_i

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

S

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0576em;margin-right:0.05em;">
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

 输出位都有一个 MUX。
- **如果真实的** <span className="katex">
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

i

</mi>

<mi>

n

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

C_{in}

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
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

in

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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

 **是 0：** 所有的 MUX 都会选择 "进位0" 电路算出的结果。
- **如果真实的** <span className="katex">
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

i

</mi>

<mi>

n

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

C_{in}

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
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

in

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

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

 **是 1：** 所有的 MUX 都会选择 "进位1" 电路算出的结果。

##### **进位保留加法器（CSA）**

在wallace树中运用

- 延迟进位的横向传播, 专用于多操作数加法（如 3 个或更多位数相加）。
- 结构*:* 它不是一个完整的`A+B`加法器。它在结构上是由`N`个并联的全加器组成（实现 3:2 压缩）。
- 应用*:* 主要用于乘法器中的部分积求和。它将 3 个数的加法压缩为 2 个数的加法, 且延迟为`O(1)`（一个全加器延迟）, 最后再用一个快速加法器（如 CLA）计算`S+C`的最终结果。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai1-51.webp)

CSA单元其实和普通的Full Adder单元是一样的，但是它和行波进位加法器不同的是，最大可能地进行并行计算

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai1-52.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai1-53.webp)

左边是普通的CSA链，其实也就是行波进位加法器，但是右边就是wallace树种的结构了，主要就是把比如九个数的计算，拆成3+3+3，这样能够最大限度减小整个计算的“深度”从而加快速度

---

#### <mark>阵列乘法器、Booth乘法器、Wallace乘法器的概念，除法的基础方法</mark>

##### 阵列乘法器

阵列乘法器是一种用于实现无符号数乘法的结构。以一个4位无符号阵列乘法器为例，它通过将被乘数（如0110）与乘数（如1001）相乘，产生一系列的部分积（Partial Products）。这些部分积随后相加，最终得到乘积（如00110110）。在版图布局时，阵列会被扭正以得到矩阵排列。这种结构由全加器单元构成。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai1-54.webp)

**竖式乘法**的过程：

```text
0110  (被乘数 y)
    x 1001  (乘数 x)
    -------
      0110  <-- (y 乘以 x 的第0位 '1')
     0000   <-- (y 乘以 x 的第1位 '0', 向左移1位)
    0000    <-- (y 乘以 x 的第2位 '0', 向左移2位)
+  0110     <-- (y 乘以 x 的第3位 '1', 向左移3位)
----------------
  00110110  (最终的“积”)
```

最长路径<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mn>

2

</mn>

<mo stretchy="false">

(

</mo>

<mi>

N

</mi>

<mo>

−

</mo>

<mn>

1

</mn>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

2(N-1)

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord">

2

</span>

<span className="mopen">

(

</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

N

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

)

</span>
</span>
</span>
</span>

个加法器

整体一共需要<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

N

</mi>

<mo stretchy="false">

(

</mo>

<mi>

N

</mi>

<mo>

−

</mo>

<mn>

1

</mn>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

N(N-1)

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

N

</span>

<span className="mopen">

(

</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

N

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

)

</span>
</span>
</span>
</span>

个加法器

##### Booth乘法器

**2位Booth编码**。它不是一次只看1位乘数，而是**“通过观察y的3位”（**<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

Y

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

<mo separator="true">

,

</mo>

<msub>
<mi>

Y

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

Y

</mi>

<mrow>
<mi>

i

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

Y_{i+1}, Y_i, Y_{i-1}

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

Y

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
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

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.2222em;">

Y

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
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
<span className="mord,mathnormal" style="margin-right:0.2222em;">

Y

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

i

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

**）来决定下一步做什么。**

使用了一个代数技巧 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msup>
<mn>

2

</mn>

<mi>

a

</mi>
</msup>

<mo>

=

</mo>

<msup>
<mn>

2

</mn>

<mrow>
<mi>

a

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

−

</mo>

<msup>
<mn>

2

</mn>

<mi>

a

</mi>
</msup>
</mrow>

<annotation encoding="application/x-tex">

2^a = 2^{a+1} - 2^a

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

a

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
<span className="mord,mathnormal,mtight">

a

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

−

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

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

a

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

 然后把某一个乘数y重写成了<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

y

</mi>

<mo>

=

</mo>

<msubsup>
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

0

</mn>

<mo separator="true">

,

</mo>

<mtext>

even

</mtext>
</mrow>

<mrow>
<mi>

n

</mi>

<mo>

−

</mo>

<mn>

2

</mn>
</mrow>
</msubsup>

<msup>
<mn>

2

</mn>

<mi>

i

</mi>
</msup>

<mo stretchy="false">

(

</mo>

<msub>
<mi>

y

</mi>

<mrow>
<mi>

i

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
<mi>

y

</mi>

<mi>

i

</mi>
</msub>

<mo>

−

</mo>

<mn>

2

</mn>

<msub>
<mi>

y

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

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

y = \sum_{i=0, \text{even}}^{n-2} 2^i (y_{i-1} + y_i - 2y_{i+1})

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.625em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

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
<span className="strut" style="height:1.3898em;vertical-align:-0.4358em;">



</span>

<span className="mop">
<span className="mop,op-symbol,small-op" style="position:relative;top:0em;">

∑

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.954em;">
<span style="top:-2.4003em;margin-left:0em;margin-right:0.05em;">
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

0

</span>

<span className="mpunct,mtight">

,

</span>

<span className="mord,text,mtight">
<span className="mord,mtight">

even

</span>
</span>
</span>
</span>
</span>

<span style="top:-3.2029em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

n

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
<span className="vlist" style="height:0.4358em;">
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
<span className="mord">

2

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8247em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

i

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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

i

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
<span className="strut" style="height:0.7778em;vertical-align:-0.1944em;">



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

<span className="mclose">

)

</span>
</span>
</span>
</span>



![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai1-55.webp)

每次操作要加/减的值，就是被乘数 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

x

</mi>
</mrow>

<annotation encoding="application/x-tex">

x

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.4306em;">



</span>

<span className="mord,mathnormal">

x

</span>
</span>
</span>
</span>

 乘以括号里的那个因子 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mo stretchy="false">

(

</mo>

<msub>
<mi>

y

</mi>

<mrow>
<mi>

i

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
<mi>

y

</mi>

<mi>

i

</mi>
</msub>

<mo>

−

</mo>

<mn>

2

</mn>

<msub>
<mi>

y

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

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

(y_{i-1} + y_i - 2y_{i+1})

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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

i

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
<span className="strut" style="height:0.7778em;vertical-align:-0.1944em;">



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

<span className="mclose">

)

</span>
</span>
</span>
</span>

。而括号里的这个因子 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mo stretchy="false">

(

</mo>

<msub>
<mi>

y

</mi>

<mrow>
<mi>

i

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
<mi>

y

</mi>

<mi>

i

</mi>
</msub>

<mo>

−

</mo>

<mn>

2

</mn>

<msub>
<mi>

y

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

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

(y_{i-1} + y_i - 2y_{i+1})

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
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

i

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
<span className="strut" style="height:0.7778em;vertical-align:-0.1944em;">



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

<span className="mclose">

)

</span>
</span>
</span>
</span>

，**其取值只有 0、1、2 以及它们的负值** (4)。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai1-56.webp)

我们只需要观察乘数的3位，就可以决定这一步是 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mo>

+

</mo>

<mn>

0

</mn>

<mo separator="true">

,

</mo>

<mo>

±

</mo>

<mi>

x

</mi>

<mo separator="true">

,

</mo>

<mtext>

还是

</mtext>

<mo>

±

</mo>

<mn>

2

</mn>

<mi>

x

</mi>
</mrow>

<annotation encoding="application/x-tex">

+0, \pm x, \text{还是 } \pm 2x

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8778em;vertical-align:-0.1944em;">



</span>

<span className="mord">

+

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

±

</span>

<span className="mord,mathnormal">

x

</span>

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord,text">
<span className="mord,cjk_fallback">

还是

</span>

<span className="mord">



</span>
</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

±

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

<span className="mord,mathnormal">

x

</span>
</span>
</span>
</span>

。

然后开始计算：

**"观察乘数的3位" (**<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

Y

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

<mo separator="true">

,

</mo>

<msub>
<mi>

Y

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

Y

</mi>

<mrow>
<mi>

i

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

Y_{i+1}, Y_i, Y_{i-1}

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

Y

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
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

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.2222em;">

Y

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
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
<span className="mord,mathnormal" style="margin-right:0.2222em;">

Y

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

i

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

**)**

- **硬件实现：** 这3位被送入 **"译码"**模块。
- **功能：** “译码”模块就是硬件化（硬连线）的“Booth动作”查找表。它是整个操作的“大脑”。

**"决定是 +0,** <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mo>

±

</mo>

<mi>

x

</mi>

<mo separator="true">

,

</mo>

<mtext>

还是

</mtext>

<mo>

±

</mo>

<mn>

2

</mn>

<mi>

x

</mi>
</mrow>

<annotation encoding="application/x-tex">

\pm x, 还是 \pm 2x

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8778em;vertical-align:-0.1944em;">



</span>

<span className="mord">

±

</span>

<span className="mord,mathnormal">

x

</span>

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord,cjk_fallback">

还是

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

±

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

<span className="mord,mathnormal">

x

</span>
</span>
</span>
</span>

**"**

- **硬件实现：** “译码”模块在“观察”完3位后，会输出**两个控制信号**：

  1. 一个 `sel` 信号 发给 **"多路选择器"** (Mux)。
  2. 一个 `op` 信号 发给 **"加减器"** (Add/Subtractor)。

**执行操作**

- **第 3a 步 (准备数据)：**
  - “多路选择器” (Mux) 已经准备好了三个选项：`0`, `x`, `2x`。
  - `sel` 信号会告诉 Mux：“你应该选择 **2x** 并把它传给加减器。”
- **第 3b 步 (执行计算)：**
  - "加减器" 接收两个输入：一个是来自上一级的**累计结果 (AP)**，另一个是 Mux 刚刚传来的 `2x`。
  - `op` 信号会告诉加减器：“嘿，根据译码结果，你应该执行**加法**（如果是-2x，就执行减法）。”

**累计和移位**

- **"AP 累计"：** 加减器的计算结果，就是新的“部分积” <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

A

</mi>

<msub>
<mi>

P

</mi>

<mrow>
<mo stretchy="false">

(

</mo>

<mi>

i

</mi>

<mo>

+

</mo>

<mn>

2

</mn>

<mo stretchy="false">

)

</mo>

<mi mathvariant="normal">

/

</mi>

<mn>

2

</mn>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

AP_{(i+2)/2}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.0385em;vertical-align:-0.3552em;">



</span>

<span className="mord,mathnormal">

A

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3448em;">
<span style="top:-2.5198em;margin-left:-0.1389em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mopen,mtight">

(

</span>

<span className="mord,mathnormal,mtight">

i

</span>

<span className="mbin,mtight">

+

</span>

<span className="mord,mtight">

2

</span>

<span className="mclose,mtight">

)

</span>

<span className="mord,mtight">

/2

</span>
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

。
- **"左移2位"：** 整个结构会**级联**（串联）起来。如图所示，一个单元的输出会作为下一个单元的输入。这个移位是为了在下一步处理乘数的下2位。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai1-57.webp)

在**硬件面积几乎不变** 的情况下，通过让每一步的逻辑“略微复杂”一点，换来了**计算步数减半**，从而使**乘法的总时间缩短了将近一半**

##### Wallace乘法器

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai1-58.webp)

**这个wallace乘法器其实就是用了阵列乘法类似的方式（部分积），但是用wallace树来优化这个过程中的加法**

##### 除法

流程图

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai1-59.webp)

就是在模拟长除法

---

#### <mark>

浮点编码格式<span>

包括非规范值

</span>

、浮点处理异常、向偶舍入

</mark>



##### 浮点编码格式 (含非规范值)

IEEE 754标准将一个浮点数分为三个部分：符号位 (s)、指数 (exp) 和尾数 (frac)。

`VLecture13_Float_Point_Standard_-_2025.pdf`

基本编码

- **s (符号位):** 1位，决定正负。
- **exp (指数):** 8位 (单精度) 或 11位 (双精度)。
- **frac (尾数):** 23位 (单精度) 或 52位 (双精度)。

根据 `exp` 字段的值，浮点数被分为三类：规范值、非规范值和特殊值。

**A. "规范"数值 (Normalized Values)**

这是最常见的浮点数形式。

- **条件：** `exp` 字段既不是全0 (`000...0`)，也不是全1 (`111...1`)。
- **指数 (E)：**
  - 指数采用**偏置值 (Biased)** 编码。
  - <span className="katex">
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
  
  <mtext>
  
  exp
  
  </mtext>
  
  <mo>
  
  −
  
  </mo>
  
  <mtext>
  
  Bias
  
  </mtext>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  E = \text{exp} - \text{Bias}
  
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
  <span className="strut" style="height:0.7778em;vertical-align:-0.1944em;">
  
  
  
  </span>
  
  <span className="mord,text">
  <span className="mord">
  
  exp
  
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
  <span className="strut" style="height:0.6833em;">
  
  
  
  </span>
  
  <span className="mord,text">
  <span className="mord">
  
  Bias
  
  </span>
  </span>
  </span>
  </span>
  </span>
  
  。
  - 单精度 `Bias = 127`；双精度 `Bias = 1023`。
- **尾数 (M)：**
  - 尾数部分隐含了一个前导的 "1"。
  - <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mi>
  
  M
  
  </mi>
  
  <mo>
  
  =
  
  </mo>
  
  <mn>
  
  1.
  
  </mn>
  
  <mtext>
  
  frac
  
  </mtext>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  M = 1.\text{frac}
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:0.6833em;">
  
  
  
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
  <span className="strut" style="height:0.6944em;">
  
  
  
  </span>
  
  <span className="mord">
  
  1.
  
  </span>
  
  <span className="mord,text">
  <span className="mord">
  
  frac
  
  </span>
  </span>
  </span>
  </span>
  </span>
  
   (例如，如果 `frac` 是 `101...`，则尾数M为 <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mn>
  
  1.101...
  
  </mn>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  1.101...
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:0.6444em;">
  
  
  
  </span>
  
  <span className="mord">
  
  1.101...
  
  </span>
  </span>
  </span>
  </span>
  
  ) 。

**B. "非规范"数值 (Denormalized Values)**

非规范值用于表示非常接近于0的数，以实现“逐渐下溢” (gradual underflow)。

- **条件：** `exp` 字段为全0 (`000...0`)。
- **指数 (E)：**
  - 指数E被固定为 <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mo>
  
  −
  
  </mo>
  
  <mtext>
  
  Bias
  
  </mtext>
  
  <mo>
  
  +
  
  </mo>
  
  <mn>
  
  1
  
  </mn>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  -\text{Bias} + 1
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">
  
  
  
  </span>
  
  <span className="mord">
  
  −
  
  </span>
  
  <span className="mord,text">
  <span className="mord">
  
  Bias
  
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
  - 单精度中，`exp=1` 时 <span className="katex">
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
  
  <mn>
  
  1
  
  </mn>
  
  <mo>
  
  −
  
  </mo>
  
  <mn>
  
  127
  
  </mn>
  
  <mo>
  
  =
  
  </mo>
  
  <mo>
  
  −
  
  </mo>
  
  <mn>
  
  126
  
  </mn>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  E = 1 - 127 = -126
  
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
  <span className="strut" style="height:0.6444em;">
  
  
  
  </span>
  
  <span className="mord">
  
  127
  
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
  
  −
  
  </span>
  
  <span className="mord">
  
  126
  
  </span>
  </span>
  </span>
  </span>
  
   。`exp=0` 时E也等于-126，保持了指数的连续性。
- **尾数 (M)：**
  - 尾数**不再隐含**前导的 "1"，而是隐含 "0"。
  - <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mi>
  
  M
  
  </mi>
  
  <mo>
  
  =
  
  </mo>
  
  <mn>
  
  0.
  
  </mn>
  
  <mtext>
  
  frac
  
  </mtext>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  M = 0.\text{frac}
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:0.6833em;">
  
  
  
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
  <span className="strut" style="height:0.6944em;">
  
  
  
  </span>
  
  <span className="mord">
  
  0.
  
  </span>
  
  <span className="mord,text">
  <span className="mord">
  
  frac
  
  </span>
  </span>
  </span>
  </span>
  </span>
  
  。

**非规范值的两种情况：**

1. **零 (Zero)：** 当 `exp = 000...0` 且 `frac = 000...0` 时。注意，根据符号位 `s`，存在+0和-0。
2. **非零 (Subnormal)：** 当 `exp = 000...0` 且 `frac` <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mo mathvariant="normal">

≠

</mo>

<mn>

000...0

</mn>
</mrow>

<annotation encoding="application/x-tex">

\neq 000...0

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8889em;vertical-align:-0.1944em;">



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

000...0

</span>
</span>
</span>
</span>

 时。

**C. "特殊值" (Special Values)**

- **条件：** `exp` 字段为全1 (`111...1`)。
- **两种情况：**
  1. **无穷大 (Infinity, inf)：** 当 `exp = 111...1` 且 `frac = 000...0` 时。用于表示操作上溢 (overflow) 。根据符号位 `s` 区分 <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mo>
  
  +
  
  </mo>
  
  <mi mathvariant="normal">
  
  ∞
  
  </mi>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  +\infty
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:0.6667em;vertical-align:-0.0833em;">
  
  
  
  </span>
  
  <span className="mord">
  
  +
  
  </span>
  
  <span className="mord">
  
  ∞
  
  </span>
  </span>
  </span>
  </span>
  
   和 <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mo>
  
  −
  
  </mo>
  
  <mi mathvariant="normal">
  
  ∞
  
  </mi>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  -\infty
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:0.6667em;vertical-align:-0.0833em;">
  
  
  
  </span>
  
  <span className="mord">
  
  −
  
  </span>
  
  <span className="mord">
  
  ∞
  
  </span>
  </span>
  </span>
  </span>
  
  。
  2. **NaN (Not-a-Number)：** 当 `exp = 111...1` 且 `frac \neq 000...0` 时。用于表示无法确定的数值，例如 <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <msqrt>
  <mrow>
  <mo>
  
  −
  
  </mo>
  
  <mn>
  
  1
  
  </mn>
  </mrow>
  </msqrt>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  \sqrt{-1}
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:1.04em;vertical-align:-0.1744em;">
  
  
  
  </span>
  
  <span className="mord,sqrt">
  <span className="vlist-t,vlist-t2">
  <span className="vlist-r">
  <span className="vlist" style="height:0.8656em;">
  <span className="svg-align" style="top:-3em;">
  <span className="pstrut" style="height:3em;">
  
  
  
  </span>
  
  <span className="mord" style="padding-left:0.833em;">
  <span className="mord">
  
  −
  
  </span>
  
  <span className="mord">
  
  1
  
  </span>
  </span>
  </span>
  
  <span style="top:-2.8256em;">
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
  <span className="vlist" style="height:0.1744em;">
  <span>
  
  
  
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  
   或 <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mi mathvariant="normal">
  
  ∞
  
  </mi>
  
  <mo>
  
  −
  
  </mo>
  
  <mi mathvariant="normal">
  
  ∞
  
  </mi>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  \infty - \infty
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:0.6667em;vertical-align:-0.0833em;">
  
  
  
  </span>
  
  <span className="mord">
  
  ∞
  
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
  <span className="strut" style="height:0.4306em;">
  
  
  
  </span>
  
  <span className="mord">
  
  ∞
  
  </span>
  </span>
  </span>
  </span>
  
   。

#### 浮点处理异常

浮点操作可能产生五种异常类型：

1. **非法操作 (Invalid Operation)**
  - 当操作本身无意义时触发。
  - **示例：**
    - 对NaN进行操作。
    - `(+inf) + (-inf)`。
    - `0 * inf`
    - `0/0` 或 `inf/inf`。
    - `sqrt(-1)`。
    - 将 `inf` 或 `NaN` 转换为整数时。
2. **被0除 (Divide by Zero)**
  - 当除数为0，且被除数为一个确定的、非0的数时触发。
  - 结果应被置为有符号的无穷大 (`+inf` 或 `-inf`)。
3. **上溢 (Overflow)**
  - 当浮点操作结果（在舍入后）的大小超过了其格式所能表示的**最大规范值**时触发。
  - 结果会根据舍入模式被确定为 `+inf`、`-inf` 或最大规范值。
4. **下溢 (Underflow)**
  - 当浮点操作结果（在舍入后）小于**最小的非规范值**时触发。
  - 结果通常被置为 `+0` 或 `-0`。
5. **不精确 (Inexact)**
  - 当舍入丢失了非0的低位时触发。
  - 或者当发生溢出时也会触发。

#### 向偶舍入 (Round to Even)

"向偶舍入"是IEEE 754的默认舍入模式。它也被称为"向近舍入" (Round to Nearest)。

**基本原则**

"向偶舍入"的目标是将结果舍入到最接近的可表示值。关键在于如何处理**正好在两个可表示值正中间 (half-way)** 的情况。

- **规则：** 如果一个数正好处于中间，它将被舍入到使其**最低有效位 (LSB) 为偶数 (即 0)** 的那个值。
- **目的：** 这种方法可以避免在大量计算中系统性地向上或向下舍入，从而减少累积误差。

**十进制示例**

假设舍入到小数点后两位：

- `1.2349999` -> `1.23` (小于一半，向下舍)
- `1.2350001` -> `1.24` (大于一半，向上舍)
- **1.2350000** -> **1.24** (正好一半，`1.24` 的 LSB (4) 是偶数，故向上舍)
- **1.2450000** -> **1.24** (正好一半，`1.24` 的 LSB (4) 是偶数，故向下舍)

**二进制示例 (G-R-S 位法)**

在硬件实现中，我们使用 **Guard (G)**、**Round (R)** 和 **Sticky (S)** 位来判断。

- **来源：** `VLecture14_Float_Point_Operations_-_2025.pdf`
- 假设一个计算结果为 `1.BB...B G R SSS...`
  - `1.BB...B` 是最终要保留的尾数位。
  - **G (Guard位)：** 要保留的最低有效位 (LSB)。
  - **R (Round位)：** 第一个被丢弃的位。
  - **S (Sticky位)：** 所有其他被丢弃位的逻辑 **或**。
- **舍入决策（是否+1）：**
  1. 如果 `R=0`，则 **不增加** (舍去部分小于一半)。
  2. 如果 `R=1` 且 `S=1`，则 **增加1** (舍去部分大于一半)。
  3. 如果 `R=1` 且 `S=0`，则处于 **"正好一半"** 的情况。此时：
  
    - 如果 `G=1` (LSB为奇)，则 **增加1** (使其变为偶数)。
    - 如果 `G=0` (LSB为偶)，则 **不增加** (保持偶数)。
- **PPT中的表格示例：**
  - 数值 `19` (二进制 `1.0011000`)，`GRS = 110`。
  
    - `R=1` 且 `S=0` (来自`...00`)，`G=1`。
    - 符合上述第3条规则 (`G=1, R=1, S=0`)，因此需要增加1。
    - 结果：`1.001` + `0.001` = `1.010`。
  - 数值 `63` (二进制 `1.1111100`)，`GRS = 111`。
  
    - `R=1` 且 `S=1` (来自`...00`)。
    - 符合上述第2条规则，因此需要增加1。
    - 结果：`1.111` + `0.001` = `10.000`。

---

#### <mark>单周期、多周期、流水线处理器的概念架构，流水线与冲突的关系，协处理器及其与主处理器关系</mark>

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai1-60.webp)

##### 单周期架构

- **概念：** 整个处理器使用一个**非常长**的时钟周期。
- **架构：** 在这**一个**时钟周期内，一条指令必须**从头到尾**全部执行完毕（包括取指、译码、执行、访存、写回）。时钟周期的长度由**最慢**的指令（例如 `load`）来决定。
- **特性：**
  - 设计简单。
  - 性能很差，因为每条指令，即使是快速的指令（如 `add`），也必须等待那个为最慢指令设计的长时钟周期。
  - <mark>
  
  由于一个周期内只有一条指令在执行，所以
  
  </mark>
  
  <mark>
  
  **无需考虑冲突**
  
  </mark>
  
  <mark>
  
  。
  
  </mark>

##### 多周期架构

- **概念：** 这是对单周期架构的改进。它将一条指令的执行过程分解为多个（例如5个）更小的步骤，**每个步骤占用一个较短的时钟周期**。
- **架构：** 一条指令会花费多个时钟周期来完成。不同指令可以花费不同数量的周期（例如 `add` 可能花4个周期，`load` 花5个周期）。
- **特性：**
  - 时钟频率可以提得更高（因为每个周期的工作量变少了）。
  - **关键点：** 在任何时刻，**仍然只有一条指令**在处理器中执行。下一条指令必须**等待**当前指令**完成其所有的步骤**后，才能开始取指。
  - <mark>
  
  由于仍是串行执行，所以也
  
  </mark>
  
  <mark>
  
  **无需考虑冲突**
  
  </mark>
  
  <mark>
  
  。
  
  </mark>

##### 流水线架构

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai1-61.webp)

- **概念：** 这是对多周期架构的**自然增强**。它同样将指令执行分解为多个阶段（称为“流水级”，例如：<mark>

取指F、译码D、执行E、访存M、写回W）。

</mark>
- **架构：**
  - 流水线的核心思想是让这**5个阶段在时间上并行起来**。
  - 当指令1进入“执行E”阶段时，指令2同时进入“译码D”阶段，指令3同时进入“取指F”阶段。
  - 理想情况下，每个时钟周期都有一条新指令进入流水线，同时有一条旧指令执行完毕。
  - 硬件上，<mark>
  
  **流水级之间必须插入寄存器**
  
  </mark>
  
  <mark>
  
  （流水线寄存器）
  
  </mark>
  
  ，用于保存上一阶段的结果，传递给下一阶段。
- **特性：**
  - **吞吐率高**。虽然单条指令的执行总时间（延迟）可能比多周期架构还长一点（因为有寄存器开销），<mark>
  
  但理想CPI（每指令时钟周期数）可以达到 1
  
  </mark>
  
  。
  - **关键点：** 由于多条指令（最多5条）**同时在处理器中**的不同阶段执行，它们之间会产生资源和数据的依赖关系，这就是“冲突”的来源。

##### 流水线与冲突 (Hazard) 的关系

**关系：** 流水线架构通过并行执行指令来提高吞吐率，但这种并行性恰恰是导致冲突的根本原因。

<mark>

冲突是指在流水线中，下一条指令无法在预定的时钟周期内正确执行的情况，它会阻碍流水线达到理想的CPI=1的目标。

</mark>



主要有三类冲突：

1. **结构冲突**
  - **原因：** <mark>
  
  硬件资源不足。当流水线中的两条不同指令在
  
  </mark>
  
  <mark>
  
  **同一时钟周期**
  
  </mark>
  
  <mark>
  
  内尝试使用
  
  </mark>
  
  <mark>
  
  **同一个硬件单元**
  
  </mark>
  
  <mark>
  
  时发生。
  
  </mark>
  - **示例：** 假设指令存储器和数据存储器是同一个（没有分开），那么当指令4进行“访存M”阶段（读/写数据）时，指令1正在“取指F”阶段（读指令），两者会竞争同一个存储器。
  - **解决：** 增加额外硬件（例如，将指令存储器和数据存储器分开）。
2. **数据冲突**
  - **原因：** <mark>
  
  指令之间存在数据依赖。当一条指令需要使用的数据
  
  </mark>
  
  <mark>
  
  **尚未被它前面的某条指令计算或写回**
  
  </mark>
  
  <mark>
  
  时发生。最常见的是
  
  </mark>
  
  <mark>
  
  **写后读 (RAW)**
  
  </mark>
  
  <mark>
  
  。
  
  </mark>
  - **示例：**`ADD $2, $3, $4` (这条指令在W阶段才把结果写入`$2`) `ADD $5, $2, $6` (这条指令在D阶段就要读取`$2`，此时`$2`的值是旧的)
  - **解决：**
    - **数据前推：** 不必等待W阶段，当`ADD`指令在E阶段计算出结果后，立即将此结果从E阶段的输出“前推”到下一条指令的E阶段输入端，绕过寄存器堆。
    - **暂停：** 有些情况（如`LW`指令）数据在M阶段才准备好，此时必须暂停后面的指令，并在流水线中插入**一个“气泡” (Bubble)，即一个****NOP****（空操作）**，等待数据就绪。
3. **控制冲突**
  - **原因：** <mark>
  
  由分支或跳转指令引起。当处理器执行一条分支指令时，它需要时间（例如到E或M阶段）才能确定
  
  </mark>
  
  <mark>
  
  **是否跳转**
  
  </mark>
  
  <mark>
  
  以及
  
  </mark>
  
  <mark>
  
  **跳转到哪里**
  
  </mark>
  
  <mark>
  
  ，
  
  </mark>
  
  但流水线在D阶段就已经开始拉取下一条指令（即分支指令的`PC+4`地址）了。
  - **示例：** `BEQ $1, $2, Target`。当 `BEQ` 在D阶段时，F阶段已经在取 `PC+4` 的指令了。如果 `BEQ` 最终判断需要跳转到 `Target`，那么F阶段取来的指令就是错误的，必须被冲刷掉。
  - **解决：**
    - **分支预测 (Prediction)：** 猜测分支是否会跳转，并投机性地从预测的地址取指。如果猜错，则冲刷流水线。
    - **分支延迟槽 (Branch Delay Slot)：** 规定分支指令后面的那条指令**总是**会被执行，无论分支是否跳转。编译器负责找到一条有用的指令（或`NOP`）来填充这个“延迟槽”。

##### 协处理器及其与主处理器的关系

**什么是协处理器 (Coprocessor)？**

协处理器是主处理器 (CPU) 之外的一个辅助处理单元，专门用于执行特定类型的任务，以分担主处理器的负担。

- **示例：**
  - **CP0 (SCU - 系统控制协处理器)：** 负责异常/中断处理、内存管理等操作系统功能。
  - **CP1 (FPU - 浮点协处理器)：** 专门处理浮点数运算（加、减、乘、除）。
  - **CP2：** MIPS架构中保留给用户自定义的协处理器。

**协处理器与主处理器的关系**

协处理器**不是**一个能独立运行的CPU。它与主处理器（在MIPS中也称主框架 Main Frame 或整数处理器核心 IPC）是一种**紧密协同**的主从关系。

1. **共享指令流：** 协处理器与主处理器**共享同一个指令代码空间**。主处理器负责**取指 (Fetch)** 和**预译码 (Pre-decode)** 所有的指令。
2. **指令分发：** 当主处理器取到一条指令，它会先进行译码。如果发现这是一条协处理器指令（例如，MIPS中`opcode`为`0100xx`），它会根据指令中的协处理器编号（如 `xx=01` 代表CP1/FPU）将这条指令**分发**给对应的协处理器。
3. **协同执行：** 协处理器接管该指令的执行，而主处理器可以继续执行后续指令（如果不存在依赖）。这种架构就像一个**“具有分支的流水线”**。
4. **数据交换：** 协处理器（如FPU）拥有自己的寄存器（如浮点寄存器FPRs）。它们通过**协处理器接口** 与主处理器的通用寄存器 (GPRs) 交换数据。

  - `mtc1` (Move To Coprocessor 1)：将数据从主处理器的 GPR **移动到** FPU 的 FPR。
  - `mfc1` (Move From Coprocessor 1)：将数据从 FPU 的 FPR **移动回** 主处理器的 GPR。

---

#### 请说明实践指南章节中示例的主处理器与协处理器是怎样解决数据冲突的

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 52.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai1-62.webp" />
      </p>
    </td>
    
    
      <td style="width: 47.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai1-63.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

通过两种机制来解决数据冲突：<mark>

**数据前推 (Forwarding)**

</mark>

 <mark>

和

</mark>

 <mark>

**阻塞/暂停 (Blocking/Stalling)**

</mark>

。

这个系统中的数据冲突分为两种：

1. **GPR (通用寄存器) 的冲突：** 发生在主处理器 (MF) 内部，通常与 `mfc1`（从FPU读回数据）有关。
2. **FPR (浮点寄存器) 的冲突：** 发生在协处理器 (FPU) 内部，与 `mtc1`（向FPU写入数据）或FPU运算指令（如 `div.s`）有关。

以下是这两种冲突的具体解决方法：

1. 解决 GPR 的数据冲突 (在主处理器 MF 中)

- **冲突情景：** 一条指令（如 `mtc1`）在**译码D级**需要读取主处理器的**GPR**，但这个GPR的值依赖于一条更早的指令（如 `mfc1`）的写回。`mfc1` 指令要到**写回W级**才会把从FPU取回的数据写入GPR。

```verilog
mfc1 $t0, $f0   // W级才写入 t0
mtc1 $t0, $f2   // D级就需要读取 t0
```

- **解决方案：数据前推 (Operand Forwarding)** 讲义（`VLecture15` 第50页）指出，主处理器 (MF) 的冲突检测逻辑会发现这种RAW（写后读）依赖。
- 解决方案是**不**等待 `mfc1` 到达W级。FPU取回的数据在 `mfc1` 指令的 E1, E2, 或 W 流水级时就已经可用了。主处理器的前推逻辑 (Forwarding Logic) 会捕获这个数据，并将其**直接“前推”**（或称“旁路”）到 `mtc1` 指令的执行阶段所需的操作数输入端，从而避免了流水线暂停。

1. 解决 FPR 的数据冲突 (在FPU协处理器中)

FPU内部的冲突检测更为复杂，它需要处理两种来源的数据。

- **冲突情景 1：数据来自主处理器 (MF)** 一条FPU运算指令（如 `div.s`）在**EX级**需要读取一个**FPR**，但这个FPR的值依赖于刚从主处理器GPR传来的 `mtc1` 指令。

```verilog
mtc1 $t0, $f1   // ID级将数据写入 $f1
div.s $f2, $f1, $f0  // EX级需要读取 $f1
```

- **解决方案 (情景1)：数据前推 (Forwarding)** 讲义（`VLecture15` 第59页）指出，FPU的冲突检测逻辑会发现 `ID.FPRead == EX.MTCWrite`。
- `mtc1` 在FPU的ID级（对应MF的D级）就开始接收来自GPR的数据。FPU的前推逻辑会**直接将这个刚收到的数据**从ID级传递给 `div.s` 指令的EX级，无需等待 `mtc1` 完成写回。
- **冲突情景 2：数据来自上一个FPU运算 (FPU -> FPU)** 一条FPU指令需要读取一个**FPR**，但这个FPR是**上一个FPU运算指令（如** **div.s****）** 的目标寄存器，而那个运算**尚未完成**。

```text
div.s $f2, $f1, $f0   // 这是一个多周期操作，结果在EX/WB级才可用
add.s $f4, $f2, $f3   // EX级需要读取 $f2
```

- **解决方案 (情景2)：前推 或 阻塞 (Forwarding or Blocking)** 这是最关键的冲突，讲义（`VLecture15` 第59页）中描述了两种情况：

  1. **可前推：** 如果 `div.s` 已经完成计算，结果在**WB级**（写回级）。FPU的前推逻辑会像在主处理器中一样，将WB级的结果数据前推给 `add.s` 指令的EX级。
  2. **必须阻塞：** 如果 `div.s` 是一个耗时很长的操作（如多周期除法），当 `add.s` 进入EX级时，`div.s` 的结果**尚未生成**（例如 `div.s` 仍在自己的EX级）。此时数据无法前推。
  3. 在这种情况下，FPU的冲突检测逻辑会：
  
    - **发出“FPU数据冲突信号” (FPU data conflict signal)**。
    - 这个信号被发送回**主处理器 (MF) 的全局阻塞控制器**（`VLecture15` 第52页）。
    - 主处理器 (MF) 收到该信号后，**立刻暂停 (Stall) 其D级流水线**，导致MF的D级和F级都停止取指和译码，从而也阻止了FPU获得新指令。
    - 流水线会一直暂停，直到 `div.s` 计算完成，FPU撤销这个冲突信号，流水线才恢复执行。

---

## 练习示例

#### 一、在设计初期同一工艺下，如何简单评价时钟、面积、功耗？

1. 时钟 (性能)

  - 时钟周期主要由<mark>
  
  **关键路径的逻辑延迟**
  
  </mark>
  
  <mark>
  
  决定
  
  </mark>
  
  。
  - 在简单估算时，可以通过对比不同设计方案<mark>
  
  中，
  
  </mark>
  
  <mark>
  
  **关键路径上级联的二输入与非门 (2-input NAND gates) 的数量**
  
  </mark>
  
  <mark>
  
  来进行评价。
  
  </mark>
2. 面积

  - 设计的总面积可以简单地通过<mark>
  
  **所有部件折算成的二输入与非门的总数量**
  
  </mark>
  
  <mark>
  
  来对比。
  
  </mark>
  - 不仅是逻辑门，像存储单元（如寄存器）等也可以归约（折算）成等效的二输入与非门数量来进行统一评价。
3. 功耗

  - 在同一工艺下，传统CMOS电路的功耗主要是**动态功耗**。
  - 动态功耗通常与**性能（时钟频率）成正相关**。
  - 简单估算公式为：动态功耗 ∝电源电压**2* (时钟周期)⁻¹，即**时钟频率越高，功耗越大**。
  - **静态功耗与面积相关**，但在早期简单估算时可以暂时不考虑。

##### 综合评价

在评估架构时，可以将这三个指标进行复合，例如，使用**（时钟周期 × 面积 × 功耗）的乘积**来进行综合评价。

---

#### 二、请写出复位同步化的Verilog代码，并用注释的方式描述其主要内容与作用

<alert type="tip">

1. 复位同步化是指**将异步复位信号同步到时钟域**，避免亚稳态和复位释放时的时序问题。
2. `async_rst_n` 是一个异步信号，它可能在**任何时间**从低电平（复位状态）变为高电平（非复位状态）。

如果这个“变为高电平”的时刻，恰好发生在 `clk` 时钟上升沿的**附近**（在一个被称为“亚稳态窗口”的极小时间窗内），就会违反触发器的**恢复时间 (Recovery Time)** 要求

</alert>

```verilog
// 模块定义
module ResetSynchronizer (
    output wire o_rst_sync_n, // 同步后的复位信号（低有效）
    input  wire i_clk,         // 目标时钟
    input  wire i_rst_async_n  // 异步复位输入（低有效）
);

    // 定义两级寄存器用于同步
    reg rst_sync_r1;
    reg rst_sync_r2;

    // 异步复位、同步释放的核心逻辑
    // 敏感列表包含时钟上升沿和复位下降沿
    always @(posedge i_clk or negedge i_rst_async_n) begin
        if (!i_rst_async_n) begin
            // 异步复位：立即将两级寄存器都拉低
            rst_sync_r1 <= 1'b0;
            rst_sync_r2 <= 1'b0;
        end else begin
            // 同步释放：在时钟边沿逐级传递高电平（代表复位被释放）
            rst_sync_r1 <= 1'b1;
            rst_sync_r2 <= rst_sync_r1;
        end
    end

    // 将第二级寄存器的输出作为同步后的复位信号
    assign o_rst_sync_n = rst_sync_r2;

endmodule
```

---

#### 三、请写出在8位中找最高位"1"的Verilog代码，并采用注释的方式简述其行为的含义

```verilog
// 模块：在8位中找最高位"1"
// 示例：
//   输入 x = 8'b0010_0000 (索引5是最高'1') -> 输出 y = 3'b101 (5)
//   输入 x = 8'b0000_0100 (索引2是最高'1') -> 输出 y = 3'b010 (2)
module find_ones(
    input [7:0] x,   // 8位输入数据
    output [2:0] y   // 3位输出，表示最高"1"的索引
);

    // 中间信号，用于暂存包含最高"1"的4位数据块
    wire [3:0] data_4;
    // 中间信号，用于暂存包含最高"1"的2位数据块
    wire [1:0] data_2;

    // 1. 确定索引的第2位 (MSB)
    //    检查高4位(x[7:4])是否有1。
    //    `|` 是缩位或操作符，x[7:4]中任一为1，结果即为1。
    assign y[2] = |x[7:4];

    // 2. 选择包含最高"1"的4位块
    //    如果y[2]为1 (最高'1'在[7:4]中)，则data_4 = x[7:4]
    //    否则 (最高'1'在[3:0]中)，data_4 = x[3:0]
    assign data_4 = y[2] ? x[7:4] : x[3:0];

    // 3. 确定索引的第1位
    //    在已选定的4位块(data_4)中，检查其高2位(data_4[3:2])是否有1
    assign y[1] = |data_4[3:2];

    // 4. 选择包含最高"1"的2位块
    //    如果y[1]为1 (最高'1'在data_4[3:2]中)，则data_2 = data_4[3:2]
    //    否则 (最高'1'在data_4[1:0]中)，data_2 = data_4[1:0]
    assign data_2 = y[1] ? data_4[3:2] : data_4[1:0];

    // 5. 确定索引的第0位 (LSB)
    //    在已选定的2位块(data_2)中，检查其高1位(data_2[1])是否为1
    assign y[0] = data_2[1];

endmodule
```

---

#### 请描述如何在Verilog中实现一个简单的异步复位D触发器

```verilog
// 模块：带异步复位（低有效）的D触发器
module d_flip_flop_async_reset (
    output reg q,   // 触发器输出
    input wire d,    // 数据输入
    input wire clk,   // 时钟
    input wire rst_n  // 异步复位（低有效）
);

    // 敏感列表包含时钟上升沿和复位下降沿
    always @(posedge clk or negedge rst_n) begin
        if (!rst_n) begin
            // 异步复位：立即将q置为0
            q <= 1'b0;
        end else begin
            // 正常时钟沿：采样输入d
            q <= d;
        end
    end

endmodule
```

---

#### 采用中间变量方式，写出一个全加器单元的Verilog代码，并用注释的方式描述其行为的含义

```verilog
// 模块：1位全加器（使用中间变量）
module full_add3(
    input  wire a,
    input  wire b,
    input  wire cin,
    output reg  sum,
    output reg  cout
);

    // 定义中间变量，用于存储产生进位的各项
    reg m1, m2, m3;

    // 使用 always @(*) 来描述组合逻辑
    always @(a or b or cin) begin
        // 1. 计算"和" (Sum)
        //    和是三个输入的异或
        sum = (a ^ b) ^ cin;

        // 2. 计算"进位"(Carry)的中间项
        //    m1: a 和 b 均为 1
        m1 = a & b;
        //    m2: b 和 cin 均为 1
        m2 = b & cin;
        //    m3: a 和 cin 均为 1
        m3 = a & cin;

        // 3. 计算最终的"输出进位" (Cout)
        //    只要任意一个中间项为1，就产生进位
        cout = (m1 | m2) | m3;
    end

endmodule
```

---

#### 采用中间变量方式，写出一个32位组合向左移位器的Verilog代码，并简述其行为的含义

```verilog
// 模块：32位组合逻辑左移位器（使用中间变量）
module left_shift_middle32(
    input  wire [31:0] data,  // 32位输入数据
    input  wire [4:0]  ctrl,  // 5位移位量控制信号
    output reg  [31:0] out    // 32位移位后输出
);

    // 中间变量，用于存储每一级移位的结果
    reg [31:0] temp;

    // 组合逻辑块，敏感列表包含所有输入
    always @(data or ctrl)
    begin
        // 行为含义：
        // 这是一个5级级联的桶形移位器。
        // temp 变量在每一级中被重复使用和赋值。

        // 第1级：根据 ctrl[0] (控制1位) 决定是否左移1位
        // {{data[30:0]}, 1'b0} 是 Verilog 的拼合操作，等效于 data << 1
        temp = ctrl[0] ? {{data[30:0]}, 1'b0} : data;

        // 第2级：根据 ctrl[1] (控制2位) 决定是否将上一级结果(temp)再左移2位
        temp = ctrl[1] ? {{temp[29:0]}, 2'b0} : temp;

        // 第3级：根据 ctrl[2] (控制4位) 决定是否将上一级结果(temp)再左移4位
        temp = ctrl[2] ? {{temp[27:0]}, 4'b0} : temp;

        // 第4级：根据 ctrl[3] (控制8位) 决定是否将上一级结果(temp)再左移8位
        temp = ctrl[3] ? {{temp[23:0]}, 8'b0} : temp;

        // 第5级：根据 ctrl[4] (控制16位) 决定是否将上一级结果(temp)再左移16位
        temp = ctrl[4] ? {{temp[15:0]}, 16'b0} : temp;

        // 将最后一级的结果赋给输出
        out = temp;
    end

endmodule
```

---

#### 请谈谈Testbench的大致框架？

Testbench（测试台）是一个用于**实施设计验证**的Verilog模型。它本身不是设计的一部分，而是用来模拟和验证你的设计（称为UUT，Unit Under Test，或DUT，Design Under Test）是否按预期工作的。

其大致框架和核心组成部分包括：

1. **实例化被测模块：**
  - Testbench的顶层模块中会实例化（调用）你所设计的硬件模块（UUT）。
2. **激励生成：**
  - 这一部分负责产生并施加测试激励（也称为测试向量或测试模板）到UUT的输入端口。
  - 这通常在 `initial` 块中完成，使用 `#` 延迟来控制信号在不同时间的变化。
  - **时钟和复位生成：** 对于时序逻辑，Testbench必须生成一个时钟信号（例如使用 `always #5 clk = ~clk;`）和一个初始的复位信号。
3. **结果检查：**
  - 这一部分会监视UUT的输出端口。
  - 它会将UUT的实际输出与一个**预期的（黄金）结果**进行比较。
  - 当发现不一致时，它会报告错误（例如使用 `$display` 打印错误信息），并可能终止仿真（使用 `$finish`）。

<mark>

Testbench的主要框架是根据测试向量、检查测试结果来进行设计实例的测试，测试向量(可以通过initial与延迟按时间串行执行)主要是随机生成的或者已知结果的测试。测试结果主要通过测试覆盖率来保证，实际是依赖于工具的代码测试覆盖率。Testbench的主要作用是重用与回归测试

</mark>



---

#### 单精度规范值与非规范值、特殊值有什么不同？

这三者的核心区别在于**指数 (exp) 字段**的编码方式，这决定了尾数 (frac) 如何被解释。

假设为单精度（exp为8位，frac为23位）：

1. **规范值**
  - **条件：** `exp` 字段**不是全0** (`00...0`) 也**不是全1** (`11...1`)。
  - **指数 (E)：** `E = exp - 127` (Bias)。
  - **尾数 (M)：** 尾数**隐含一个前导“1”**。`M = 1.frac`。
  - **用途：** 表示绝大多数“正常”的浮点数。
2. **非规范值**
  - **条件：** `exp` 字段**是全0** (`00...0`)。
  - **指数 (E)：** 指数被固定为最小值 `E = -126`（即 `1 - 127`）。
  - **尾数 (M)：** 尾数**隐含一个前导“0”**。`M = 0.frac`。
  - **用途：**
    - **0 ：** 当 `frac` 也是全0时，表示 `+0` 或 `-0`（取决于符号位）。
    - **次规范数 ：** 当 `frac` 非0时，它表示那些非常接近于0、比最小规范值还小的数。这用于实现“逐渐下溢”，以保持精度。
3. **特殊值**
  - **条件：** `exp` 字段**是全1** (`11...1`)。
  - **用途：**
    - **无穷大 ：** 当 `frac` 是全0时。用于表示“上溢”（结果大到无法表示）或“被0除”。
    - **NaN (Not-a-Number)：** 当 `frac` 非0时。用于表示一个“非法操作”的结果，例如 `sqrt(-1)`、`0/0` 或 `inf - inf`。

---

#### 请叙述处理器的多周期架构与流水线架构的相同与不同？

这两种架构都是对单周期架构的改进，它们都将一条指令的执行划分为多个（如5个）阶段（取指、译码、执行、访存、写回），并使用更短的时钟周期。

**相同点：**

1. **指令分解：** 都将一条指令的完整执行过程分解为多个更小的步骤。
2. **时钟周期：** 都使用一个较短的时钟周期，每个周期只完成一个步骤，因此时钟频率远高于单周期架构。

**不同点：**

<table>
<thead>
  <tr>
    <th>
      特性
    </th>
    
    <th>
      多周期架构 (Multi-Cycle)
    </th>
    
    <th>
      流水线架构 (Pipelined)
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      执行方式
    </td>
    
    <td>
      串行 (Serial)
    </td>
    
    <td>
      并行 (Parallel)
    </td>
  </tr>
  
  <tr>
    <td>
      指令重叠
    </td>
    
    <td>
      无重叠。在任何时刻，处理器中只有一条指令在执行。下一条指令必须等待当前指令完全结束后才能开始。
    </td>
    
    <td>
      有重叠。在任何时刻，处理器中有多条（最多5条）指令同时在执行，只是它们处于不同的阶段。
    </td>
  </tr>
  
  <tr>
    <td>
      吞吐率 (CPI)
    </td>
    
    <td>
      较差。理想CPI是指令的平均周期数（例如4或5）。
    </td>
    
    <td>
      极高。理想CPI可以达到1（即每个周期完成一条指令）。
    </td>
  </tr>
  
  <tr>
    <td>
      硬件需求
    </td>
    
    <td>
      硬件资源可以被（在不同周期）复用。
    </td>
    
    <td>
      必须在每个阶段之间插入流水线寄存器，以保存中间结果并传递给下一阶段。
    </td>
  </tr>
  
  <tr>
    <td>
      冲突问题
    </td>
    
    <td>
      没有冲突。因为指令是串行执行的，不存在资源或数据的竞争。
    </td>
    
    <td>
      必须处理冲突。由于指令并行执行，会导致结构冲突（抢占硬件）、数据冲突（数据未准备好）和控制冲突（分支跳转）。
    </td>
  </tr>
</tbody>
</table>

---

#### 请叙述主处理器与协处理器是怎样大致衔接的？这样的架构主要反映了什么思路？

**衔接方式：**

主处理器（MF或IPC）和协处理器（如FPU）是一种紧密协同的主从关系，它们通过一个**协处理器接口**来衔接：

1. **共享指令流：** 主处理器和协处理器共享同一个指令流。主处理器负责**取指 (Fetch)** 和**预译码 (Pre-decode)** 所有的指令。
2. **指令分发：** 当主处理器译码时，发现这条指令是“协处理器指令”（例如通过特定的`opcode`识别），它就会将这条指令**分发**给对应的协处理器（例如 `opcode 010001` 分发给CP1，即FPU）。
3. **协同执行：** 协处理器接管该指令的执行（例如FPU执行 `div.s`），而主处理器可以继续执行后续的指令（如果不存在依赖）。
4. **数据交换：** 协处理器（FPU）拥有自己的寄存器堆（FPRs）。当需要与主处理器的通用寄存器堆（GPRs）交换数据时，使用专门的指令：

  - **mtc1** **(Move To Coprocessor 1)：** 主处理器将数据从GPR**写入**FPU的FPR。
  - **mfc1** **(Move From Coprocessor 1)：** 主处理器从FPU的FPR**读回**数据到GPR。

**反映的思路：**

这种架构主要反映了**“功能专业化”**和**“任务委托”**的设计思路。

1. **功能专业化：** 主处理器（整数核心）专注于执行常规的整数运算、逻辑判断和程序流控制。而协处理器（如FPU）则是一个高度优化的“专家”，专门处理复杂且耗时的特定任务（如浮点运算）。
2. **任务委托：** 主处理器充当“总指挥”，它不自己去执行不擅长的浮点计算，而是将这些任务“委托”给FPU。
3. **流水线扩展：** 这种架构可以被视为主流水线的一个“功能分支”。协处理器就像一个并行的、专门的执行流水线，主处理器可以将特定指令“分流”到这个分支流水线去处理，从而提高整体的执行效率。

---

#### 请阐述普通加法器与进位保留加法器的异同？请阐述Wallace乘法器的概念？

##### **普通加法器 (以行波进位加法器为例)**

- **概念：** 这是我们最熟悉的加法器，它模拟了“竖式加法”。它由多个全加器 (Full Adder) 级联而成。
- **工作方式：** 它的核心特点是**进位会立即传播**。

  - 每一个全加器 (FA) 接收三个输入：`a`、`b` 和来自**低一位的进位** **cin**。
  - 它产生两个输出：`sum` (本位和) 和 `cout` (到**高一位的进位**)。
- **异同点 (异)：**
  - **依赖性：** 高位的计算**必须**等待低位全加器计算出 `cout` 信号。
  - **延迟：** 这种依赖性形成了一条很长的**“进位链”** 。在 <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mi>
  
  N
  
  </mi>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  N
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:0.6833em;">
  
  
  
  </span>
  
  <span className="mord,mathnormal" style="margin-right:0.109em;">
  
  N
  
  </span>
  </span>
  </span>
  </span>
  
   位加法器中，最坏情况的延迟与 <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mi>
  
  N
  
  </mi>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  N
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:0.6833em;">
  
  
  
  </span>
  
  <span className="mord,mathnormal" style="margin-right:0.109em;">
  
  N
  
  </span>
  </span>
  </span>
  </span>
  
   成正比。这在 <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mi>
  
  N
  
  </mi>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  N
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:0.6833em;">
  
  
  
  </span>
  
  <span className="mord,mathnormal" style="margin-right:0.109em;">
  
  N
  
  </span>
  </span>
  </span>
  </span>
  
   很大时会非常慢。

##### **进位保留加法器 (Carry-Save Adder, CSA)**

- **概念：** CSA 不是用来计算两个数的最终和，而是用来**同时压缩三个数**。它由一组并行的全加器构成，但这些全加器之间的连接方式与普通加法器完全不同。
- **工作方式：** 它的核心特点是**保留进位，不立即传播**。

  - 它接收三个 <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mi>
  
  N
  
  </mi>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  N
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:0.6833em;">
  
  
  
  </span>
  
  <span className="mord,mathnormal" style="margin-right:0.109em;">
  
  N
  
  </span>
  </span>
  </span>
  </span>
  
   位的输入（例如 `A`, `B`, `C`）。
  - 它产生两个 <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mi>
  
  N
  
  </mi>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  N
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:0.6833em;">
  
  
  
  </span>
  
  <span className="mord,mathnormal" style="margin-right:0.109em;">
  
  N
  
  </span>
  </span>
  </span>
  </span>
  
   位的输出：
  
    1. **SSS (Sum)：** 每一位 <span className="katex">
    <span className="katex-mathml">
    <math xmlns="http://www.w3.org/1998/Math/MathML">
    <semantics>
    <mrow>
    <msub>
    <mi>
    
    S
    
    </mi>
    
    <mi>
    
    i
    
    </mi>
    </msub>
    </mrow>
    
    <annotation encoding="application/x-tex">
    
    S_i
    
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
    
    S
    
    </span>
    
    <span className="msupsub">
    <span className="vlist-t,vlist-t2">
    <span className="vlist-r">
    <span className="vlist" style="height:0.3117em;">
    <span style="top:-2.55em;margin-left:-0.0576em;margin-right:0.05em;">
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
    
     是 `A[i]`, `B[i]`, `C[i]` 的**本位和**（即 `A[i] ^ B[i] ^ C[i]`）。
    2. **CCC (Carry)：** 每一位 <span className="katex">
    <span className="katex-mathml">
    <math xmlns="http://www.w3.org/1998/Math/MathML">
    <semantics>
    <mrow>
    <msub>
    <mi>
    
    C
    
    </mi>
    
    <mi>
    
    i
    
    </mi>
    </msub>
    </mrow>
    
    <annotation encoding="application/x-tex">
    
    C_i
    
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
    <span className="vlist" style="height:0.3117em;">
    <span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
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
    
     是 `A[i]`, `B[i]`, `C[i]` 的**本位进位**（即 `(A[i]&B[i]) | (A[i]&C[i]) | (B[i]&C[i])`）。
- **异同点 (异)：**
  - **依赖性：** 每一位（`S[i]` 和 `C[i]`）的计算都是**完全独立**的，**不依赖**于任何其他位的进位。
  - **延迟：** 延迟是恒定的，仅为一个全加器的延迟，与输入位数 N 无关。

**总结对比：**

<table>
<thead>
  <tr>
    <th>
      特性
    </th>
    
    <th>
      普通加法器 (如：行波进位)
    </th>
    
    <th>
      进位保留加法器 (CSA)
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      功能
    </td>
    
    <td>
      计算 2 个 <span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <mi>
                  N
                </mi>
              </mrow>
              
              <annotation encoding="application/x-tex">
                N
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:0.6833em;">
              
            </span>
            
            <span className="mord,mathnormal" style="margin-right:0.109em;">
              N
            </span>
          </span>
        </span>
      </span>
      
       位数的和
    </td>
    
    <td>
      压缩 3 个 N 位数
    </td>
  </tr>
  
  <tr>
    <td>
      输出
    </td>
    
    <td>
      1 个 <span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <mi>
                  N
                </mi>
                
                <mo>
                  +
                </mo>
                
                <mn>
                  1
                </mn>
              </mrow>
              
              <annotation encoding="application/x-tex">
                N+1
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">
              
            </span>
            
            <span className="mord,mathnormal" style="margin-right:0.109em;">
              N
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
      
       位的结果 (最终的和)
    </td>
    
    <td>
      2 个 <span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <mi>
                  N
                </mi>
                
                <mo>
                  +
                </mo>
                
                <mn>
                  1
                </mn>
              </mrow>
              
              <annotation encoding="application/x-tex">
                N+1
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">
              
            </span>
            
            <span className="mord,mathnormal" style="margin-right:0.109em;">
              N
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
      
       位的结果 (<span className="katex">
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
      
       和 <span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <mi>
                  C
                </mi>
              </mrow>
              
              <annotation encoding="application/x-tex">
                C
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:0.6833em;">
              
            </span>
            
            <span className="mord,mathnormal" style="margin-right:0.0715em;">
              C
            </span>
          </span>
        </span>
      </span>
      
      )
    </td>
  </tr>
  
  <tr>
    <td>
      进位
    </td>
    
    <td>
      进位立即从低位传播到高位
    </td>
    
    <td>
      进位被保留在原位（输出为 <span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <mi>
                  C
                </mi>
              </mrow>
              
              <annotation encoding="application/x-tex">
                C
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:0.6833em;">
              
            </span>
            
            <span className="mord,mathnormal" style="margin-right:0.0715em;">
              C
            </span>
          </span>
        </span>
      </span>
      
      ），不横向传播
    </td>
  </tr>
  
  <tr>
    <td>
      延迟
    </td>
    
    <td>
      慢，延迟与位数 <span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <mi>
                  N
                </mi>
              </mrow>
              
              <annotation encoding="application/x-tex">
                N
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:0.6833em;">
              
            </span>
            
            <span className="mord,mathnormal" style="margin-right:0.109em;">
              N
            </span>
          </span>
        </span>
      </span>
      
       相关 (存在进位链)
    </td>
    
    <td>
      快，延迟恒定（仅1个全加器延迟）
    </td>
  </tr>
  
  <tr>
    <td>
      用途
    </td>
    
    <td>
      用于计算最终结果
    </td>
    
    <td>
      用于乘法器中，快速压缩多个中间数
    </td>
  </tr>
</tbody>
</table>

##### Wallace 乘法器的概念

Wallace 乘法器是一种高性能的**并行乘法器**，它的核心思想是利用我们上面提到的**进位保留加法器 (CSA) 来实现快速的中间产物压缩**。

一个乘法过程可以分为三个步骤，Wallace 树主要优化了第二步：

1. **步骤一：生成部分积**
  - 将乘数的每一位与被乘数的每一位进行“与”(`&`)操作，产生 <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
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
  
  <annotation encoding="application/x-tex">
  
  N \times N
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">
  
  
  
  </span>
  
  <span className="mord,mathnormal" style="margin-right:0.109em;">
  
  N
  
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
  
  <span className="mord,mathnormal" style="margin-right:0.109em;">
  
  N
  
  </span>
  </span>
  </span>
  </span>
  
   个部分积。这一步是完全并行的。
2. **步骤二：压缩部分积 (Wallace 树的核心)**
  - 这是最慢的步骤。我们现在有 N 行部分积需要相加。
  - **普通乘法器：** 会一行一行地相加，每加一次都要经历一次缓慢的进位传播。
  - **Wallace 乘法器：** 它不一行一行加。它使用**多层 CSA** 构成一个“树形”结构。
  
    - 它将 <span className="katex">
    <span className="katex-mathml">
    <math xmlns="http://www.w3.org/1998/Math/MathML">
    <semantics>
    <mrow>
    <mi>
    
    N
    
    </mi>
    </mrow>
    
    <annotation encoding="application/x-tex">
    
    N
    
    </annotation>
    </semantics>
    </math>
    </span>
    
    <span className="katex-html" ariaHidden="true">
    <span className="base">
    <span className="strut" style="height:0.6833em;">
    
    
    
    </span>
    
    <span className="mord,mathnormal" style="margin-right:0.109em;">
    
    N
    
    </span>
    </span>
    </span>
    </span>
    
     行部分积**每 3 行分为一组**，输入到一个 CSA 阵列中。
    - 每一层 CSA 都会将输入的行数 K 减少到 <span className="katex">
    <span className="katex-mathml">
    <math xmlns="http://www.w3.org/1998/Math/MathML">
    <semantics>
    <mrow>
    <mfrac>
    <mn>
    
    2
    
    </mn>
    
    <mn>
    
    3
    
    </mn>
    </mfrac>
    
    <mi>
    
    K
    
    </mi>
    </mrow>
    
    <annotation encoding="application/x-tex">
    
    \frac{2}{3}K
    
    </annotation>
    </semantics>
    </math>
    </span>
    
    <span className="katex-html" ariaHidden="true">
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
    
    3
    
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
    
    <span className="mord,mathnormal" style="margin-right:0.0715em;">
    
    K
    
    </span>
    </span>
    </span>
    </span>
    
    (3行输入 <span className="katex">
    <span className="katex-mathml">
    <math xmlns="http://www.w3.org/1998/Math/MathML">
    <semantics>
    <mrow>
    <mo>
    
    →
    
    </mo>
    </mrow>
    
    <annotation encoding="application/x-tex">
    
    \rightarrow
    
    </annotation>
    </semantics>
    </math>
    </span>
    
    <span className="katex-html" ariaHidden="true">
    <span className="base">
    <span className="strut" style="height:0.3669em;">
    
    
    
    </span>
    
    <span className="mrel">
    
    →
    
    </span>
    </span>
    </span>
    </span>
    
     2行输出)。
    - 它不断重复这个过程，直到最后**只剩下 2 行**需要相加。
    - 这个树形压缩过程非常快，因为每一层 CSA 的延迟都是恒定的。
3. **步骤三：最终加法**
  - 当部分积被压缩到只剩 2 行时（即 CSA 的 S 和 C 向量），Wallace 树会使用一个**普通的、高速的加法器**（例如先行进位加法器）来计算这两行的最终和，从而得到乘法结果。

**总结：** Wallace 树的核心概念是，在计算乘法时，先**不进行任何进位传播**，而是利用 CSA 树形结构，以最快的速度（对数级延迟）将 N 行部分积**并行地**压缩为 2 行，最后才用一个单独的加法器完成一次性的进位传播。

---

#### 以”讲义11 RTL设计-示例：算法状态机的初始流图”中的初始流图、控制器ASM图、数据通路、状态转换图的转换为例，叙述ASM图方法，解释ASM图方法与初始流图、控制器ASM图、有限状态机与数据通路的关系、系统框图。叙述通常采用什么方式来进行有限状态机与数据通路的代码编写

<mark>

ASM图方法概述+关系总结+FSM与数据通路的代码编写方式

</mark>



##### ASM图方法概述

ASM（Algorithmic State Machine，算法状态机）图方法是一种用于RTL（寄存器传输级）设计的结构化方法 。它首先通过类似流程图的形式（即“初始流图”）来描述一个算法或功能，此时并不严格区分数据通路和控制 。然后，通过一个“精化”（Refinement）步骤，将这个功能描述划分为**数据通路（Datapath）和控制器（Controller）** 两部分，并最终推导出控制器的有限状态机（FSM）。

就是前端设计的前三点

##### 关系总结

- **ASM图方法与初始流图**： 初始流图是ASM方法的**起点** 。它从算法层面描述了“做什么”（What），而不关心“谁来做”（How）。
- **ASM图方法与控制器ASM图**： 控制器ASM图是初始流图经过“架构划分”后的**精化结果** 。它描述了**控制器**的逻辑，即如何通过发送控制信号（如 `load x`）和接收结果信号（如 `xcompare`）来复现初始流图的功能。
- **ASM图方法与系统框图及数据通路**： ASM图方法是一种“数据通路-控制器”的架构划分方法 。系统框图是这种划分的**高层视图** 。数据通路是这种划分下的“执行单元”，它根据ASM图方法推导出的控制信号来执行具体的数据操作 。
- **ASM图方法与有限状态机 (FSM)**： FSM是ASM图方法中**控制器的最终实现** 。控制器ASM图 和状态转换图  只是FSM的**两种不同表示形式**，ASM图（流程图形式）更易于从算法转换而来，而STG（状态图形式）更接近最终的硬件实现

##### FSM与数据通路的代码编写方式

3+2个always(见前)

---

#### 以下代码可以综合吗？并根据以下代码解释什么是综合？

```verilog
always @(a or b or c or d)
  begin
    t1 <= a & b;
    t2 <= c | d;
    out <= t1 & t2;
  end
```

不能综合

- *综合前* (仿真行为)： 在仿真器中，非阻塞赋值 (<=) 会导致`out`在计算时使用的是旧的`t1`和`t2`的值。这不符合组合逻辑的定义，仿真行为是错误的。
- *综合后* (硬件行为)： 综合工具很可能会忽略(<=)的错误用法，将其“修正”并综合为它认为你想要的纯组合逻辑，即`out = (a & b) & (c | d)`。

##### 根据可综合的关键：

##### 1 基于RTL设计(风格)的前提；

##### 2 可以通过综合工具将Verilog行为级代码变成基于特定工艺的标准单元的门级表示；

##### 3 综合前后的行为未改变。

##### 请指出以下代码可以综合吗？如果不能综合，请指出与前述的哪些关键存在违背的情况

##### 代码分析

这段代码描述了一个组合逻辑电路。它的意图是根据输入 `a`, `b`, `c`, `d` 的变化来计算输出 `out`。

**这段代码在语法上是有效的，但它不符合标准的、推荐的可综合 RTL 设计风格，因此严格来说不应该被认为是可综合的，或者至少是“不推荐综合”的。**

它主要违背了提出的 **关键1（基于RTL设计风格的前提）** 和 **关键3（综合前后的行为未改变）**。

---

##### 详细解释与违背情况

###### 关键1：基于RTL设计(风格)的前提

这条关键是核心问题所在。在标准的 RTL 设计实践中，对组合逻辑和时序逻辑的编码风格有明确的区分：

- **组合逻辑**: 使用 `always @(*)` 或者 `always @(所有输入信号)`，并且内部必须使用**阻塞赋值 (****=****)**。
- **时序逻辑**: 使用 `always @(posedge clk)` 或 `always @(negedge rst_n)`，并且内部必须使用**非阻塞赋值 (****<=****)**。

**这段代码的违背之处在于：**

它描述的是一个**组合逻辑**（敏感列表包含所有输入信号，没有时钟），但却使用了**非阻塞赋值 (****<=****)**，这通常是为时序逻辑保留的。

###### 关键3：综合前后的行为未改变

这条关键是衡量综合正确性的金标准

- 仿真器会严格遵守非阻塞赋值的定义：在 always 块结束时，才统一更新 <= 左侧的信号值。

  1. 当 `a, b, c, d` 中任何一个变化，`always` 块被触发。
  2. `a & b` 的结果被**调度**给 `t1`。
  3. `c | d` 的结果被**调度**给 `t2`。
  4. `t1 & t2` 的结果被**调度**给 `out`。**请注意**：此时用于计算 `out` 的 `t1` 和 `t2` 仍然是它们在进入这个 `always` 块之前的**旧值**，因为新的值要到块结束才更新。
  5. `always` 块执行结束，`t1`, `t2`, `out` 的值被同时更新。
- 这种行为实际上描述了一个**锁存器 (Latch)** 或者说是一个依赖于旧值的时序行为，而不是一个纯粹的组合逻辑路径。
- **违背之处在于**：代码的**仿真行为**（由于非阻塞赋值，表现出类似时序的特性，依赖于旧值）与**综合后的电路行为**（一个纯粹的、无记忆的组合逻辑电路）存在潜在的不匹配。在更复杂的逻辑中，这种不匹配可能会导致功能错误，即综合前后的行为发生了改变。

---

##### 正确的可综合写法

为了清晰地描述这个组合逻辑，代码应该修改为使用阻塞赋值 (=):

```verilog
// 推荐的写法always @(a or b or c or d) // 或者使用 always @(*)begin
  t1 = a & b;     // 使用阻塞赋值
  t2 = c | d;     // 使用阻塞赋值
  out = t1 & t2;  // 使用阻塞赋值end
```

或者使用 `assign` 语句，这是描述纯组合逻辑最直接、最不容易出错的方式：

```text
// 最佳写法wire t1, t2;
assign t1 = a & b;
assign t2 = c | d;
assign out = t1 & t2;
```

总结一下，此段代码**不推荐用于综合**，因为它违反了标准的RTL设计风格，并带来了仿真与综合结果不一致的巨大风险。

##### 什么是综合

##### <mark>综合是通过代工厂的标准门级单元库，将RTL代码映射成电路实现的，并且综合前后的模拟行为一致</mark>

**基于RTL设计风格**： 综合工具（如 Design Compiler） 的主要工作对象是RTL（Register Transfer Level）风格的代码 。这意味着设计是<mark>

围绕

</mark>

<mark>

**组合逻辑**

</mark>

<mark>

和

</mark>

<mark>

**时序单元**

</mark>

**（如边沿触发器）** 来构建的 。结构化的RTL是保证综合质量的最重要风格 。

**转换为门级表示**： 综合工具读取你的 Verilog 代码 ，并<mark>

使用特定的

</mark>

<mark>

**工艺库（标准单元库）**

</mark>

 <mark>

，将其自动映射为由与门、或门、触发器等基本逻辑单元构成的电路实现（即门级网表）

</mark>

 。

**保持行为一致性**： 这是综合的根本原则。<mark>

综合前（RTL级别）的功能模拟行为必须与综合后（门级网表）的模拟行为保持一致

</mark>

 。综合工具会消除繁琐的布尔逻辑映射和电路实现工作 ，但设计的逻辑功能不会改变。
