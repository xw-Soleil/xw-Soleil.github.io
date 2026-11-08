# 与PPT的对应

> 课程笔记与 PPT 章节的对应关系

#### 课程学习重点 (Key Points) 与 PPT 讲义对应指

#### Verilog基础

- **module/endmodule****、****wire/reg****、****input/output/inout****、****0/1/z/x****、向量写法、常量写法、****parameter****、****begin/end**
  - **主讲义：** VLecture3_The_Basical_Concept_of_Verilog_-_2025.pdf
  - **对应内容：**
    - module 框架、端口表、端口定义
    - wire vs. reg
    - 0/1/z/x (4值逻辑)
    - 向量 (Vectors)
    - 常量 (Constants)
- **initial****、****always****、****#****延迟写法、连续赋值****assign****写法、与/或/非逻辑及条件运算符写法**
  - **主讲义：** VLecture3、VLecture4、VLecture5
  - **对应内容：**
    - initial 和 always 块 (VLecture3)
    - ## 延迟写法 (Delay Modeling) (VLecture4)
    - assign (连续赋值) (VLecture5)
    - 操作符 (与/或/非/条件 ?:) (VLecture5)
- **if/else****、****case-default****、****casez-default****、****casex-default****、****for**
  - **主讲义：** VLecture7_Behavioral_Modeling：Conditionals_and_Loops_-_2025.pdf
  - **对应内容：**
    - if-else (包括嵌套)
    - case, casez, casex (包括 default 和全等比较)
    - for, repeat, while, forever
- **function****、****task****、****$display****、****$finish****、文件相关系统任务等的作用**
  - **主讲义：** VLecture8_Functions_&*Task*&*System_Call*-_2025.pdf
  - **对应内容：**
    - function vs. task 对比
    - $display (及其%格式)
    - $finish, $stop
    - 文件I/O ($fopen, $fclose, $fdisplay, $readmemb)
- **状态机FSM的3个****always****块写法、数据通路的2个****always****块写法**
  - **主讲义：** VLecture12_Controller_and_Data-Path_Coding_-_2025.pdf
  - **对应内容：**
    - **3-****always** **FSM** (时序+次态+输出)
    - **2-****always** **Datapath** (在GCD示例中)
    - 对比1、2、3个 always 块的优缺点
- **阻塞的组合逻辑、非阻塞的时序逻辑写法, 避免锁存器**
  - **主讲义：** VLecture6 和 VLecture9
  - **对应内容：**
    - **阻塞 (****=****) vs. 非阻塞 (****<=****)** 的核心区别和执行顺序 (VLecture6)
    - **规则1：** 时序逻辑 (带 posedge clk) **必须**使用非阻塞 (<=) (VLecture6)
    - **规则2：** 组合逻辑 (always @(*)) **必须**使用阻塞 (=) (VLecture3, Key_of_The_Course)
    - **避免锁存器 (Latch)：** 组合逻辑 always 块中的 if 必须有 else，case 必须有 default (VLecture9)
- **代码编写规范与命名法、RTL设计(风格)**
  - **主讲义：** VLecture11__Register-Transfer_Design_-_2025.pdf
  - **对应内容：**
    - RTL设计 (寄存器传输级) 概念
    - RTL风格 (匈牙利命名法, 结构化注释等)
    - VLecture9 也通篇在讲“可综合的RTL风格”
- **单时钟域与跨时钟域、门控时钟、异步复位**
  - **主讲义：** VLecture11__Register-Transfer_Design_-_2025.pdf
  - **对应内容：**
    - 单时钟域 vs. 多时钟域
    - 跨时钟域同步 (同步器)
    - 门控时钟 (Clock Gating) 及其风险
    - 异步复位 (及其同步化/同步释放)
- **Verilog的数据流模型、行为模型、结构(级)模型与...的关系?**
  - **主讲义：** VLecture1, VLecture3, VLecture5
  - **对应内容：**
    - **Verilog模型分类：** 结构 (门实例化)，数据流 (assign)，行为 (always/initial) (VLecture1)
    - **数字系统模型：** 行为 (功能)，结构 (输入输出与层次) (VLecture1)
    - **关系：** Verilog的数据流和行为模型都用于描述数字系统的行为。Verilog的结构(级)模型用于描述数字系统的结构。
- **Verilog的结构(级)模型具体指哪种描述方式?**
  - **主讲义：** VLecture5_Dataflow_Modeling_-_2025.pdf
  - **对应内容：**
    - 指使用**门级原语** (如 and, or, not) 或**模块实例化** (orunit G1(...)) 来描述电路连接的方式。

---

#### 设计基础

- **VLSI/FPGA设计流程? ... 前端设计方法学是怎样的?**
  - **主讲义：** VLecture1_Introduction_-*2025.pdf 和 VLecture9_Logic_Synthesis*-_2025.pdf
  - **对应内容：**
    - VLSI设计流程 (RTL -> 综合 -> 布局布线 -> ...) (VLecture1)
    - 前端设计方法学 (行为描述 -> 架构 -> RTL -> 验证) (VLecture1)
    - FPGA vs VLSI 流程对比 (前端/后端) (VLecture9)
- **关键路径、虚假路径、冗余路径的概念? ...**
  - **主讲义：** VLecture11__Register-Transfer_Design_-_2025.pdf
  - **对应内容：**
    - 关键路径 (Critical Path)
    - 虚假路径 (False Path)
    - 冗余逻辑 (Redundant Logic)
- **不可到达状态、沉没状态的概念?**
  - **主讲义：** VLecture12_Controller_and_Data-Path_Coding_-_2025.pdf
  - **对应内容：**
    - 不可到达状态 (Unreachable States)
    - 沉没状态 (Sink States)
- **设计评价: 面积/时钟(性能)/功耗**
  - **主讲义：** VLecture11__Register-Transfer_Design_-_2025.pdf
  - **对应内容：**
    - RTL前评估/架构评估的简单估算方法
    - VLecture9 也有综合后的评估图
- **ASM图方法、系统框图概念...如何编写控制器/状态机、数据通路的Verilog代码?**
  - **主讲义：** VLecture11 和 VLecture12
  - **对应内容：**
    - ASM (算法状态机) 概念 (VLecture11)
    - 从初始流图 -> 系统框图 (划分) -> 控制器ASM图 -> FSM状态转换图 的完整示例 (VLecture11)
    - **编码：** 控制器用 **3-****always** **块**，数据通路用 **2-****always** **块** (VLecture12)
- **什么是综合? 可综合的关键...**
  - **主讲义：** VLecture9_Logic_Synthesis_-_2025.pdf
  - **对应内容：**
    - 综合的定义 (RTL代码 -> 门级网表)
    - 三个关键点 (RTL描述、可转换、行为一致)
- **Testbench的主要框架...**
  - **主讲义：** VLecture11__Register-Transfer_Design_-_2025.pdf
  - **对应内容：**
    - Testbench 框架 (UUT + Tester)
    - 测试激励 (Stimulus) (用 initial 和 # 延迟)
    - 结果检查 (Checking)
    - 覆盖率 (Coverage) 和回归 (Regression)
    - VLecture1 也有Testbench在设计流程中的位置

---

#### 设计基础, 续

- **全加器、半加器、进位保留加法器...**
  - **主讲义：** VLecture10_Hardware_Computing_-_2025.pdf
  - **对应内容：**
    - 半加器 (Half Adder)
    - 全加器 (Full Adder)
    - 进位保留加法器 (Carry-Save Adder, CSA)
    - 先行进位加法器 (Carry-Lookahead)
    - 进位跳跃加法器 (Carry-Skip)
    - 进位选择加法器 (Carry-Select)
- **阵列乘法器、Booth乘法器、Wallace乘法器...除法的基础方法**
  - **主讲义：** VLecture10_Hardware_Computing_-_2025.pdf
  - **对应内容：**
    - 阵列乘法器 (Array Multiplier)
    - Booth乘法器 (Booth Multiplier)
    - Wallace乘法器 (Wallace Tree)
    - 除法 (Division) 算法流图
- **浮点编码格式包括非规范值、浮点处理异常、向偶舍入**
  - **主讲义：** VLecture13_Float_Point_Standard_-_2025.pdf
  - **对应内容：**
    - 编码格式 (规范值, **非规范值**, 特殊值)
    - 异常 (Exceptions) (非法操作, 上溢, 下溢, 被0除, 不精确)
    - 舍入模式 (Rounding) (特别是**向偶舍入**)
    - VLecture14 也有向偶舍入的 GRS 位实现
- **单周期、多周期、流水线处理器的概念架构, 流水线与冲突的关系, 协处理器及其与主处理器关系**
  - **主讲义：** VLecture15_Design_Explore_-_2025.pdf
  - **对应内容：**
    - 架构对比 (单周期/多周期/流水线)
    - 流水线冲突 (Hazard) (结构/数据/控制)
    - 冲突解决 (前推/暂停)
    - 协处理器 (Coprocessor) 概念 (CP0/CP1)
    - 主-协处理器关系 (指令分发, mfc1/mtc1)
- **请说明实践指南章节中示例的主处理器与协处理器是怎样解决数据冲突的**
  - **主讲义：** VLecture15_Design_Explore_-_2025.pdf
  - **对应内容：**
    - 这是对讲义内容的**理解题**。答案在第 49-54, 59, 61 页。
    - 主处理器 (MF) 冲突 (GPR)
    - FPU 冲突 (FPR) (包括来自 MF 的 mtc1 和 FPU 内部的运算)
    - 解决方案：阻塞控制 (Stalling) 和数据前推 (Forwarding)。

---

#### 练习示例

（这部分是**复习指南中的问题**，我来指出每个问题对应的知识点在哪个PPT中）

- **...评价时钟、面积、功耗?**
  - **答案来源：** VLecture11__Register-Transfer_Design_-_2025.pdf
- **...复位同步化的Verilog代码...**
  - **答案来源：** VLecture11__Register-Transfer_Design_-_2025.pdf (概念)。
- **...8位中找最高位"1"的Verilog代码...**
  - **答案来源：** VLecture10_Hardware_Computing_-_2025.pdf (第64页提供了完整代码)。
- **...异步复位D触发器。**
  - **答案来源：** VLecture9_Logic_Synthesis_-_2025.pdf (第36页提供了完整代码) 和 VLecture10 (第61页)。
- **...中间变量方式...全加器单元...**
  - **答案来源：** VLecture10_Hardware_Computing_-_2025.pdf (第63页提供了完整代码)。
- **...中间变量方式...32位组合向左移位器...**
  - **答案来源：** VLecture10_Hardware_Computing_-_2025.pdf (第68页提供了完整代码)。
- **...Testbench的大致框架?**
  - **答案来源：** VLecture11__Register-Transfer_Design_-_2025.pdf
- **...单精度规范值与非规范值、特殊值有什么不同?**
  - **答案来源：** VLecture13_Float_Point_Standard_-_2025.pdf
- **...多周期架构与流水线架构的相同与不同?**
  - **答案来源：** VLecture15_Design_Explore_-_2025.pdf
- **...主处理器与协处理器是怎样大致衔接的?...**
  - **答案来源：** VLecture15_Design_Explore_-_2025.pdf
- **...普通加法器与进位保留加法器的异同?...**
  - **答案来源：** VLecture10_Hardware_Computing_-_2025.pdf
- **...Wallace乘法器的概念?**
  - **答案来源：** VLecture10_Hardware_Computing_-_2025.pdf
- **...叙述ASM图方法...**
  - **答案来源：** VLecture11__Register-Transfer_Design_-*2025.pdf (方法) 和 VLecture12_Controller_and_Data-Path_Coding*-_2025.pdf (编码风格)。
- **...以下代码可以综合吗?并根据以下代码解释什么是综合?**
  - **答案来源：** VLecture9_Logic_Synthesis_-*2025.pdf (综合概念, 锁存器陷阱) 和 VLecture6_Behavioral_Modeling：Non-blocking__Assignment*-_2025.pdf (非阻塞赋值用于时序逻辑)。
  - **解释：** 这段代码**不可综合**（或者说会综合出**锁存器**），因为你在组合逻辑块 (always @(a or b...)) 中错误地使用了**非阻塞赋值 (****<=****)**。
