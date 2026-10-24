# 飞起来2.0

> HDL 期末复习：典型代码（全加器、移位器、D 触发器、计数器）与综合问题解析

这一部分主要是针对后两道题

<alert type="tip">

*五：典型代码的编写与注释，共2题，每题9分*

代码示例中的**D触发器、全加器、移位器（这三个是重点）**等，对应题型五为主

**Lecture 10里面最后有代码的**

*六：简述以下代码的潜在问题，共3题，每题4分*

综合编译中讲述的重点，对应题型六为主

就是**之前讲到的十七八个问题里面抽三个来考试（回去看看智云**

</alert>

## 典型代码

**我重写了一遍神的代码，然后加上了注释（感觉可以自己重写一遍，就能记住了**

### 第一部分：组合逻辑电路 (Combinational Logic)

来自`Lecture 10 PPT`，紫色部分是他的重点

#### <mark>全加器</mark>

这里展示了三种实现1位全加器的方法，它们在功能上是等价的。

1. 使用 `assign` 连续赋值

这是最直接的组合逻辑描述方式，适用于简单的逻辑门级描述。

```verilog
module full_adder1(
    input a,
    input b,
    input cin,
    output sum,
    output cout
);

    // 使用assign语句描述

    // 和是三个输入的异或
    assign sum = a ^ b ^ cin;

    // 只要三个输入当中有两个是1，就要产生进位，于是这样写
    assign cout = (a & b) | (a & cin) | (b & cin);

endmodule
```

1. 使用 `always` 块

使用 `always` 块（配合敏感列表 `a or b or cin` 或 `always @(*)`）也可以实现组合逻辑

```verilog
module full_adder2(
    input a,
    input b,
    input cin,
    output reg sum, // always中的被赋值的变量必须为reg
    output reg cout
);

    // 敏感列表包含所有的信号
    always @(a or b or cin) // 当然，更直接的写法就是 always @(*)这里是因为神这么写
    begin
        // 和为异或
        sum = a ^ b ^ cin;
        // 进位为三位中的任意两位与再或
        cout = (a & b) | (a & cin) | (b & cin);
    end

endmodule
```

1. 使用 `always` 块 (带中间变量)

这种方式与方式二相同，只是使用了中间变量，使进位逻辑更清晰

```verilog
module full_adder3(
    input a,
    input b,
    input cin,
    output reg sum, // always中的被赋值的变量必须为reg
    output reg cout
);

    reg m1, m2, m3;

    // 敏感列表包含所有的信号
    always @(a or b or cin)
    begin
        // 和为异或
        sum = a ^ b ^ cin;
        // 进位为三位中的任意两位与再或
        // 加上中间变量
        m1 = a & b;
        m2 = a & cin;
        m3 = b & cin;
        cout = (m1 | m2) | m3;
    end

endmodule
```

1. 参数化的加法器

如何使用 `parameter` 关键字来创建一个**可配置位宽**的加法器

```verilog
module AddWithCarryInCarryOut #(
    parameter NUMBITS = 3 // 定义一个代表位数的参数
)(
    input [NUMBITS : 1] OpdA, // 3、2、1三位（神从1开始记数 | 哈哈哈笑死了
    input [NUMBITS : 1] OpdB,
    input CarryIn,
    output [NUMBITS : 1] Sum,
    output CarryOut
);

    // 直接用拼接操作计算
    assign {CarryOut, Sum} = OpdA + OpdB + CarryIn;

endmodule
```

#### 找最高位的 "1" (Priority Encoder)

这是一个8位输入的**优先编码器**，用于找到最高位（MSB）的 "1" 所在的索引。

```verilog
module find_ones(
    input [7:0] x,
    output [2:0] y
);

    // 神用了二分法
    wire [3:0] data_4;
    wire [1:0] data_2;

    // 检查高4位，用"|"缩减或
    // 等效为assign y[2] = x[7] | x[6] | x[5] | x[4];
    assign y[2] = |x[7:4];
    // 如果高4位有1，则 data_4 选高4位；否则选低4位
    assign data_4 = y[2] ? x[7:4] : x[3:0];
    // 检查data_4的高2位，用"|"缩减或
    assign y[1] = |data_4[3:2];
    // 如果data_4的高2位有1，则 data_2 选高2位；否则选低2位
    assign data_2 = y[1] ? data_4[3:2] : data_4[1:0];
    // 检查data_2的高1位
    assign y[0] = data_2[1];

endmodule
```

#### 找最低位的 "1" (Priority Encoder)

这是一个**优先编码器**，用于找到最低位（LSB）的 "1" 所在的索引。

```verilog
module find_one(
    input [7:0] data,
    output [2:0] index
);

    // 神用了二分法
    wire [3:0] data_4;
    wire [1:0] data_2;

    // 检查低4位 data[3:0]
    // ~|data[3:0] (缩减或非)：当且仅当低4位全部为0时，结果为'1'
    // index[2] = 1 表示'1'在高4位
    assign index[2] = ~|data[3:0]; 
    // 如果 index[2] 为 1 (低4位全0)，则 data_4 选高4位
    assign data_4 = index[2] ? data[7:4] : data[3:0];

    // 检查 data_4 的低2位
    // index[1] = 1 表示 '1' 在 data_4 的高2位
    assign index[1] = ~|data_4[1:0];
    assign data_2 = index[1] ? data_4[3:2] : data_4[1:0];

    // 检查 data_2 的低1位
    // index[0] = 1 表示 '1' 在 data_2 的高1位
    assign index[0] = ~data_2[0];

endmodule
```

#### <mark>组合移位器 (Case 语句)</mark>

这是一个4位的**逻辑左移**移位器，使用 `case` 语句（多路选择器 MUX）实现。

```verilog
module left_shifter_case(
    input [3:0] data,
    input [1:0] ctrl,
    output reg [3:0] out // 在always块中赋值，定义为reg
);

    // always @(*)表明这是一个组合逻辑块
    always @(*)
    begin
        case(ctrl)
            2'b00: out = data; // 不移位
            2'b01: out = {data[2:0], 1'b0}; // 左移1位
            2'b10: out = {data[1:0], 2'b00}; // 左移2位
            default: out = {data[0], 3'b000}; // 左移3位
        endcase
    end

endmodule
```

#### <mark>组合移位器 (中间变量)</mark>

这是一个32位的**桶形移位器 (Barrel Shifter)**，使用多级三目运算符实现，效率很高。

```verilog
module left_shift_middle32(
    input [31:0] data,
    input [4:0] ctrl,
    output reg [31:0] out
);

    reg [31:0] temp;

    // 核心逻辑就是二进制数的分解，5bit刚好可以表达32位
    always@(data or ctrl)
    begin
        // 第0级：由 ctrl[0] 控制是否移1位
        temp = ctrl[0] ? {{data[30:0]}, 1'b0} : data;
        // 第1级：由 ctrl[1] 控制是否移2位
        temp = ctrl[1] ? {{temp[29:0]}, 2'b0} : temp;
        // 第2级：由 ctrl[2] 控制是否移4位
        temp = ctrl[2] ? {{temp[27:0]}, 4'b0} : temp;
        // 第3级：由 ctrl[3] 控制是否移8位
        temp = ctrl[3] ? {{temp[23:0]}, 8'b0} : temp;
        // 第4级：由 ctrl[4] 控制是否移16位
        temp = ctrl[4] ? {{temp[15:0]}, 16'b0} : temp;
        out = temp;
    end

endmodule
```

---

### 第二部分：时序逻辑电路 (Sequential Logic)

#### <mark>D 触发器 (带异步复位)</mark>

这是所有时序逻辑中最基本、最重要的单元。它在时钟上升沿锁存输入 `d` 的值，并具有一个**异步**复位功能。

```verilog
module d_flip_flop(
    input clk,
    input rst,
    input d,
    output reg q
);

    always @(posedge clk or negedge rst)
    begin
        if (!rst) begin
            q <= 0; // 异步复位
        end else begin
            q <= d;
        end
    end

endmodule
```

#### 移位寄存器

包含两个模块：一个4位串行输入、并行输出 (SIPO) 移位寄存器和一个32位并行加载寄存器。

```verilog
module block4(
    input clk,
    input d_in,
    output reg Q0,
    output reg Q1,
    output reg Q2,
    output reg Q3
);

    // 数据在时钟沿从 din -> Q0 -> Q1 -> Q2 -> Q3 移动
    always@(posedge clk)
    begin
        Q0 <= d_in; // 使用非阻塞赋值
        Q1 <= Q0;
        Q2 <= Q1;
        Q3 <= Q2;
    end

endmodule

module shifter32(
    input clk,
    input [32:0] a,
    output reg [32:0] c
);

    // 在每个时钟上升沿
    // 寄存器 c 会锁存 a 左移8位、低位补0的结果
    always @(posedge clk)
    begin
        c <= {a[23:0], 8'b0};
    end

endmodule
```

#### 1位计数器 (可串联)

这是一个1位的计数器单元，包含时序逻辑（DFF）、下一状态逻辑和输出逻辑三部分。

```verilog
module counter1bit(
    input clk,
    input reset,
    input cin,
    output cout,
    output reg bit // 状态寄存器
);

    reg bitnext; // 下一状态

    // 时序逻辑部分 D触发器
    always @(posedge clk or negedge reset)
    begin
        if (!reset)
            bit <= 0;
        else
            bit <= bitnext;
    end

    // 组合逻辑部分，下一状态的逻辑
    always @(bit or cin)
    begin
        // bitnext = bit XOR cin (T触发器逻辑)
        // cin=1 时翻转, cin=0 时保持
        bitnext = bit ^ cin;
    end

    // 组合逻辑部分，进位输出
    always @(bit or cin)
    begin
        // cout = bit AND cin
        // 当本位为1且有进位时，向高位输出进位
        cout = bit & cin;
    end

endmodule
```

#### 定时器 (Timer)

这是一个5位的计数器，带异步复位和同步预置，计数到16时停止并拉高 `done` 信号。

```verilog
module timerTick(
    input clk,
    input reset,
    input preset,
    output reg [4:0] tick,
    output reg done
);

    always @(posedge clk or negedge reset)
    begin
        if (!reset) // 异步复位，最高优先级
        begin
            tick <= 5'b0;
            done <= 0;
        end else
        begin
            if (preset) // 同步预置
            begin
                tick <= 5'b0;
                done <= 0;
            end else
            begin // 正常计数逻辑
                if (tick < 16)
                begin
                    tick <= tick +1'b1;
                    done <= 0;
                end else
                begin
                    tick <= 5'b0;
                    done <= 1;
                end
            end
        end
    end

endmodule
```

#### 寄存器文件 (Register File)

一个简易的**寄存器文件**（RAM），具有一个同步读/写端口。

```verilog
module RegFileWithMemory #(
    parameter N = 2, // N=2, 地址位宽 (2 bits, 可寻址 2^2=4 个)
    parameter M = 2 // M=2, 数据位宽 (2 bits, 2 bits)
)(
    input Clk,
    input wire Readwrite,        // 1=读, 0=写
    input wire [N-1:0] Index,    // 寄存器地址
    input wire [M-1:0] DataIn,   // 写入的数据
    output reg [M-1:0] Dataout   // 读出的数据
);

    // 定义寄存器文件存储体 (内存)
    // 这是一个 M 位宽, 深度为 2^N 的数组
    // (N=2 => 2^2 = 4 个寄存器, 地址 0, 1, 2, 3)
    reg [M-1:0] RegFile [ (2**N)-1 : 0 ];

    always @(posedge Clk)
    begin
        if (Readwrite) // 读
        begin
            // 将 RegFile[Index] 的值锁存到 Dataout 寄存器
            Dataout <= RegFile[Index];
        end else // 写
        begin
            // 将 DataIn 写入指定地址
            RegFile[Index] <= DataIn;
        end
    end

endmodule
```

---

## 综合问题

<alert type="tip">

1 2 3 4 5 6 10 14 15 16 17 18 27 45 47 48 49 50

</alert>

### 第一个

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai2-01.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai2-02.webp)

`cAll = {cPartI[PartIMSB:0], {ExcludePartIBits{0}}};`

- `{ExcludePartIBits{0}}`：这是一个复制(Replication) 操作。它的意思是“把 0 这个值，**复制** `ExcludePartIBits` **次**”。

但是 `Value` 是 `0`，这是一个**“无大小的数字” (unsized literal)** （这里无大小可以理解为没有告诉我是多少“位宽”的0）。意味着：Verilog 编译器不知道你希望这个 `0` 是 1 比特 (`1'b0`)、8 比特 (`8'h00`) 还是 32 比特 (`32'd0`)。所以，编译器做出了一个默认的**假设**：“假设为32比特”。

这意味着，你的代码实际上在这里被解释为： ``cAll = {cPartI<span>

...

</span>

, {ExcludePartIBits{32'd0}}};```

---

### 第二个

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai2-03.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai2-04.webp)

这个 `always @ (...)` 模块是用来描述一个**触发器**（就是能存数据的硬件）的。造这种硬件，综合工具（那个把代码变成硬件的程序）有个**死规定**：

`always` 模块里面**必须**是一个完整的 `if...else...` 结构，分成两半：

1. **复位时干啥**：`if (!iReset) begin ... end`
2. **平时干啥**：`else begin ... end`

你所有的赋值 (`<=`) 代码，**必须**完整地放在这两个“块”的*里面*。

也就是这样

```verilog
always @ (posedge iClock or negedge iReset) begin

    // 情况一：处理复位
    if (!iReset) begin
        // 所有的“复位”赋值必须在这里
        // (例如：reg_A <= 0;)
    end

    // 情况二：处理时钟
    else begin // 注意：这里是 else
        // 所有的“平时”赋值必须在这里
        // (例如：reg_A <= data_in;)
    end

    // *** 在这里不允许有任何赋值语句 ***

end
```

你错在哪里？

我们来看看你的“平时干啥”那部分：

```verilog
// ...else if (iReset) begin   // <-- “平时干啥”的 { 开始if (ciRegMode == `CNormalMode)
        rData <= iData;
    end // <-- 错误！你在这里就把“平时干啥”的 } 给关上了！// 因为上面关早了，这行代码就“裸奔”在外面了
    rRegMode <= ciRegMode;

end // <-- 这个 end 本来想配 always 的 begin
```

**问题就出在这里：**

那行 `rRegMode <= ciRegMode;` 掉在了 `else` 块的**外面**。

它现在既不属于“复位时干啥”，也不属于“平时干啥”，它就这么“漂浮”在 `always` 块里。

综合工具看到这行“漂浮”的代码，直接就懵了，它不知道该拿这行代码怎么办，因为它不符合“必须在 `if` 或 `else` 块里”的规定。

总结：**always块中不允许在** **always** **块的“顶层”(也就是if-else块的外面)进行赋值，因为在综合的时候无法确定这个代码是在哪个阶段执行**

---

### <mark>第三个</mark>

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai2-05.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai2-06.webp)

这个问题非常经典！用一句话说清楚就是：

**你不能用一个“数据位”来当“时钟”用。**

**详细解释（说人话）**

1. **always @ (posedge ...)** **是用来干嘛的？** 这个语句是 Verilog 里用来造**时序逻辑**的，最常见的就是造**D触发器**（Flip-Flop）。D 触发器是硬件里用来存数据的基本单元，它需要一个“节拍器”来告诉它什么时候“存”。
2. **posedge** **后面应该放什么？**`posedge` (上升沿) 后面，综合工具**期望**你放一个**“时钟信号” (Clock Signal)** 。

  - **时钟**是整个电路的“心跳”（比如 `clk`, `iClock`）。它是一个非常干净、稳定、有规律的“滴-答-滴-答”信号。
  - 所有触发器都应该听同一个“心跳”信号，这样才能保证整个电路步调一致。
3. **你放了什么？** 你放了 `iData[pmt+2]`，也就是 `iData[7]`。

  - `iData` 从名字上看就是**“数据” (Data)**。
  - `iData[7]` 只是这个数据总线上的第 7 根线。

主要原因还是，时钟信号走的是专用的、高速的“时钟网络”（Global Clock Network），稳定，无毛刺

但是数据走的是“通用布线网络”（General Routing Fabric），会有毛刺，这样就会多次误触发always块

---

### 第四个

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai2-07.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai2-08.webp)

简单来说，这个错误的意思是：

**在（老的）Verilog 语法里，如果**<mark>

**一个**

</mark>

 <mark>

**task**

</mark>

<mark>

**（任务）没有输入或输出参数，那么在定义它或调用它的时候，你不能加**

</mark>

 <mark>

**()**

</mark>

 <mark>

**括号**

</mark>

**。**

---

### 第五个

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai2-09.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai2-10.webp)

简单来说，这个警告的意思是：

**你把“立即执行”的组合逻辑和“等一等再执行”的时序逻辑给混用了。**

在 Verilog 里，`=` 和 `<=` 是两种完全不同的赋值：

1. **=** **(阻塞赋值 / Blocking Assignment)**
  - **意思是：** “马上办，立刻办！”
  - **用途：** 用于**组合逻辑** (Combinational Logic)，比如 `always @ (*)` 或 `always @ (In)`。
  - **行为：** 这一行代码会*立刻*执行，并且*卡住*后面的代码，直到它执行完。
2. **<=** **(非阻塞赋值 / Non-Blocking Assignment)**
  - **意思是：** “等一等，大家一起办。”
  - **用途：** 用于**时序逻辑** (Sequential Logic)，比如 `always @ (posedge clk)`。
  - **行为：** 这一行代码只是“登记”一个任务，说“我打算在当前时间片结束时更新这个值”。它*不会*卡住后面的代码

带有task块的代码等价过程

```verilog
always@(In)   
    tShift(Out, In); // <-- 这是“调用点”
    task 
        tShift(output Q, input D); // <-- 这是“定义”   
        Q <= D; 
    endtask

// 等价之后

always@(In)   
    Q <= In;  // 冲突点就在这里了
```

**这就是矛盾所在：**

- 你的 `always @ (In)` 模块期望 `Out` 的值在 `In` 变化时**立即**更新。
- 但你调用的 `task` 里面却使用了 `Q <= D;`（也就是 `Out <= In;`），这会告诉仿真器：“别急，我**等会儿**（到这个时间片末尾）再更新 `Out` 的值。”

**为什么这会导致“模拟失败”？**

因为这制造了一个“竞争条件” (Race Condition)。

想象一下，在同一个仿真时间点，有另一块逻辑需要读取 `Out` 的值。它读到的是：

- `In` 变化**之前**的旧值？
- 还是 `In` 变化**之后**的新值？

答案是：**不确定！**

---

### 第六个

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai2-11.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai2-12.webp)

这个警告（Warning）的意思非常直白：

**“你定义了一个名叫** **undriven_out** **的输出口，但是在** **task** **里面你一次都没给它赋过值。”**

task其实非常像C或者Python中的函数，里面的input和output就可以看作他的参数，在这一道题里面，我如果在别的地方，在某个always块中通过maybeUnconnected(my_input_wire, my_output_reg_A, my_output_reg_B);调用这个task时，就会出现my_output_reg_B没有对应的情况（因为只有这个out是明确有输出的）
所以，**如果我不需要这个输出，要么我就不定义，要么我必须在task里面指定为0（也就是接地**

---

### 第十个

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai2-13.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai2-14.webp)

简单来说，这个警告的意思是：

**“你的代码在读取** **in2****，但你忘了告诉** **always** **块去‘监听’****in2** **的变化。”**

因为从`myout = in1 | in2`可以看出，这个是**组合逻辑，但是代码在组合逻辑中，没有把每一个被读取的信号加到敏感表里面**，这样会产生锁存器，所以导致了错误

---

### 第十四个

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai2-15.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai2-16.webp)

这个警告是在提醒你：**你的** **case** **语句写得“不完整”，这可能会让综合工具（Synopsys）造出一个又大又慢的电路。**

过一遍case代码，这个的逻辑是：

- 当 `c` = `2'b00` 时，`out = in1`。
- 当 `c` = `2'b11` 时，`out = in2`。
- 当 `c` = `2'b01` 时，`out = in2` (来自 `default`)。
- 当 `c` = `2'b10` 时，`out = in2` (来自 `default`)。

**2'b11: out = in2;** **这一行是完全多余的**

`default` 分支的 `out = in2;` 已经**完全覆盖**了 `2'b01`, `2'b10`, **和** **2'b11** 这三种情况。

所以对应的最优硬件（一个2选1 MUX）应该是： `assign out = (c == 2'b00) ? in1 : in2;`

**这个算是警告，也就是说可以生成更好的逻辑**

---

### 第十五个

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai2-17.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai2-18.webp)

Verilog **明确允许** `Z`可参与逻辑运算（它会被视为 `X`）。

**这是糟糕的设计 (Bad Design)：** 在数字逻辑中，你**永远不应该**有意地去“与”一个高阻态。`Z` 的唯一正确用途是**描述一个“未驱动”状态**，通常用在三态门（Tri-state Buffer）中，以允许多个设备共享一条总线。

**正确用法 (Correct Use of Z)：**

```verilog
// 这是一个三态驱动器
// 当 enable = 1, out 被 data 驱动
// 当 enable = 0, out 被"断开"，呈现高阻态 Z
assign out = (enable) ? data : 1'bz;
```

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai2-19.webp)

<alert type="tip">

总之就是无法被综合or被优化，具体优化成什么实际上由具体软件决定

<mark>

神的旨意是不能综合

</mark>
</alert>

---

### 第十六个

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai2-20.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai2-21.webp)

这个警告是 Verilog 中一个非常重要且危险的规则：

<mark>

**“在**

</mark>

 <mark>

**if**

</mark>

 <mark>

**语句中，任何包含**

</mark>

 <mark>

**x**

</mark>

<mark>

**（未知）或**

</mark>

 <mark>

**z**

</mark>

<mark>

**（高阻）的条件都会被当作**

</mark>

 <mark>

**false**

</mark>

<mark>

**（假）来处理。”**

</mark>



在 `if` 语句中使用了 `x` 或 `z`。仿真器会把它们当 `false` 处理，而综合器会把它们当 `0` 或 `1` 处理，这会导致仿真和硬件不一致。`x` 的目的是在仿真中**传播“未知”**，以帮助**发现 bug，它的存在是为了****暴露****问题，而不是用来****设计****逻辑的**

---

1. **你的代码：**`if (2'b0x)` 这是一个 2 比特的数，其中一位是 `0`，另一位是 `x`（未知）。
2. **Verilog 的规则：**`if` 语句在判断“真”或“假”时，规则如下：

  - **真 (True)：** 只有当**所有位**都明确是 `0` 时，才为假。只要有**任何一位**是 `1`，就为真。
  - **假 (False)：** 如果**任何一位**是 `x` 或 `z`，那么整个条件**立即被判为** **false**。
3. **代码的行为：**
  - 因为你的条件 `2'b0x` 包含了一个 `x`，`if` 语句立即将其判为 `false`。
  - 所以，`if` 后面的第一个 `begin...end` 块（`out = in1;`）**永远不会**被执行。
  - `else` 后面的 `begin...end` 块（`out = in2;`）**永远都会**被执行。
  - （你代码中的注释 `/* Will never fire */` 和 `/* Will always fire */` 已经完美地指出了这一点。）

你可能会想：“既然我知道它永远是 false，这不就行了吗？”

**不行，这非常危险！** 这就是警告中“**模拟/综合不匹配**”的来源：

1. **模拟 (Simulation) 怎么看：**
  - 你的仿真器（比如 VCS, Modelsim）会**严格遵守**上面的 Verilog 规则。
  - 它看到 `x`，就判为 `false`。
  - 所以在你所有的**仿真测试**中，`out` **永远**等于 `in2`。你的测试结果会显示电路的功能就是 `out = in2;`。
2. **综合 (Synthesis) 怎么看：**
  - 综合工具（比如 Synopsys DC, Vivado）是用来**造硬件**的。
  - 当它看到 `x`，它会把它理解为 **"don't care"（不关心）**。
  - 它会想：“哦，设计师不关心 `x` 这种情况。太好了！我可以利用这个‘不关心’来**优化电路**，让它变得最小、最快！”
  - **灾难来了：** 为了优化，综合工具**可能**会把 `x` 当作 `1` 来处理（如果 `if (2'b01)` 能让电路更简单的话），也可能把它当 `0` 来处理。
  - 如果它把 `x` 当作 `1` 来优化，它造出的硬件就会在某些情况下执行 `out = in1;`。

**最终结果：** 你**测试**的电路（仿真）表现为 `out = in2;`。 你**造出**的芯片（综合）表现为 `out = in1;` (在某些情况下)。

**你的芯片和你的测试完全对不上，这就是“模拟/综合不匹配”，它是硬件开发中最致命的 bug 之一。**

**结论：** 永远不要在 `if` 或 `case` 语句的条件中（即控制逻辑中）使用 `x` 或 `z`。

### 第十七个

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai2-22.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai2-23.webp)

这个警告的意思非常简单：

**你的** **default** **语句是多余的，它永远不会被执行。**

---

### 第十八个

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai2-24.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai2-25.webp)

`b: y = ~a;`

`default: y = b;`

不会被执行

其实主要还是因为这个case语句里面直接放了一个常量`1'b1`

---

### 第二十七个

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai2-26.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai2-27.webp)

简单来说：**你的两个** **always** **块在“抢夺”同一个变量** **i** **的“控制权”。**

主要的原因就是，**这两个always块是同步直接执行的，然后因为这个同步的问题，所以不能同时对一样的 i 进行赋值**

### 第四十五个

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai2-28.webp)

代码45：（错误）使用空参数列表进行非法函数声明。

`function`（函数）在 Verilog 中有严格的用途：它必须是一个**纯粹的组合逻辑**，<mark>

它接受

</mark>

<mark>

**至少一个**

</mark>

 <mark>

`input`

</mark>

，并根据这些 `input` **计算出一个返回值（output只有一个）**。所以不能为空参数

---

### 第四十七个

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai2-29.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai2-30.webp)

我的理解是：`function` 必须在 0 时间内立即执行完毕，而 `task` 可以消耗时间

所以：

- 在function当中不能调用task
- 但是在task中可以调用function

简单来说：

**函数 (****function****) 必须像数学公式一样“立即”算出一个结果，而任务 (****task****) 可能会“花时间等待”。Verilog 不允许一个“立即”的东西去调用一个“可能要等待”的东西。**

---

<table>
<thead>
  <tr>
    <th>
      特性
    </th>
    
    <th>
      函数 (Function)
    </th>
    
    <th>
      任务 (Task)
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      事件控制
    </td>
    
    <td>
      不能包含任何事件控制语句（如 @、#、wait）。
    </td>
    
    <td>
      可以包含事件控制语句。
    </td>
  </tr>
  
  <tr>
    <td>
      执行时间
    </td>
    
    <td>
      必须在 0 模拟时间内执行完毕。
    </td>
    
    <td>
      可以在非 0 模拟时间内执行。
    </td>
  </tr>
  
  <tr>
    <td>
      端口
    </td>
    
    <td>
      必须至少有 1 个 input 端口，且只有 1 个 output 端口。
    </td>
    
    <td>
      可以有 0 个或多个 input、output 或 inout 类型的端口。
    </td>
  </tr>
  
  <tr>
    <td>
      调用
    </td>
    
    <td>
      只能调用其他函数。
    </td>
    
    <td>
      可以调用其他任务或函数。
    </td>
  </tr>
  
  <tr>
    <td>
      主要用途
    </td>
    
    <td>
      相对易于综合。常用于简化组合逻辑的表述或进行编译时常量计算。
    </td>
    
    <td>
      描述更复杂的行为，相对较难综合。
    </td>
  </tr>
  
  <tr>
    <td>
      局部变量
    </td>
    
    <td>
      默认是静态的 (static)，在所有调用中共享。可使用 automatic 关键字使其非共享。
    </td>
    
    <td>
      默认是静态的 (static)，在所有调用中共享。可使用 automatic 关键字使其非共享。
    </td>
  </tr>
  
  <tr>
    <td>
      返回值
    </td>
    
    <td>
      默认输出返回 1 位 reg 类型。可以使用 return 语句返回值。
    </td>
    
    <td>
      可以使用 return 语句返回。
    </td>
  </tr>
</tbody>
</table>

### 第四十八个

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai2-31.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai2-32.webp)

在task里面，**如果内部有一个output，那么在调用该task时，就需要传入某一个变量，这个变量是用来被赋值的**

这个错误非常直观，简单来说就是：

**output** **端口是用来“往外写数据”的（驱动器），你必须给它一个“变量”来接住数据，但你却给了一个“常量”。**

---

### 第四十九个

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai2-33.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai2-34.webp)

这个问题和您刚才问的“代码48”是**一模一样的根本错误**，只是换了一种形式。

具体理解就是，**wire**因为是线网型，不能被当作一个变量，因为**wire是只读的**

简单来说：

**task** **的** **output** **端口（****x****）需要一个“篮子”（****reg** **变量）来存放它要输出的值。但你却给了它一个“只读”的东西。**

---

### 第五十个

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai2-35.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/FeiQilai2-36.webp)

这个错误是说：**你不能在“赋值语句”的中间“等待”一个事件。**

这段代码**描述了一个行为**，而不是一个结构。它告诉**仿真器**：“请**暂停**在这里，**等待** `clk` 的下一个上升沿出现。当它出现后，**读取** `a` 的值，然后**赋值**给 `y`。”

**问题：** **物理硬件无法“暂停”**。一个“与”门不能说“我先不工作了，等个时钟沿再算”。硬件是**永远**在运行的。所以综合上会有问题

**正确的代码：**

Verilog

```text
// 这是一个标准的 D 触发器// 它描述了一个“硬件结构”
always @ (posedge clk) begin
    y <= a;
end
```
