# Chapter 1：Introduction

> 课程导论：详细版笔记

## 课程安排

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ICCAD/DetailCh1-01.webp)

1. 周一课程时间段结束之后有可能有抽查 lab
2. 要建一个微信群——可能会有互动要求

### 课程章节

- Introduction to IC EDA
- Unix

  - Start
  - File sys
  - Vi
  - Shells
  - Network applications
  - System administration
  - X Window
  - C compilers, make and other development tools
- Scripting language related to ICCAD

  - Tcl/Tk
  - Perl
  - Python
  - Scala
- Design flow (extended and optional)

  - General IC/SoC design flow
- Summary or Review

### 考核要求

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ICCAD/DetailCh1-02.webp)

## 课程目标

1. Learn the principles of using unix commands, utilities and scripts. (命令、工具（或应用）、脚本)
2. To understand basic software concepts and conventions (惯例、规范) seen in main-stream IC design flow.
3. Hence to become confident while facing to complex ICCAD software in the future

## 碎碎念

- C/C++, Linux, bash, even Perl are always the underlying stuffs
- Chisel  和 Verilog、Sys Verilog 区别

## Form transistor to IC

### Brief History of Transistor

这里还有一页 ppt

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ICCAD/DetailCh1-03.webp)

- 1951: Shockley develops junction transistor for production
- 1954: First transistor radios ($30~50; Regency, Totsuko（东京通信工程索尼收音机）)
- 1955: Texas Instruments makes first silicon transistor ($2.50)

> - TI 公司，用 Si 做的，以前都用锗做的

- 1956: Shockley Semiconductor Laboratory is founded in Silicon Valley, Robert Noyce and Gordon Moore join

> - Shockley 半导体公司在硅谷成立 —— 硅谷得名（不确定？）

- 1956: Shockley, Bardeen and Brattain share a Nobel Prize in Physics
- 1957: Noyce leaves Shockley Semiconductor Labs to form Fairchild Semiconductor with Jean Hoerni and Gordon Moore

> - Shockley 管理公司有问题——另外两人去仙童公司

- 1958, 1959: Jack Kilby, working at Texas Instruments, dreams up the idea of a monolithic integrated circuit（集成电路）; Hoerni and Noyce invent diffusing, isolation and connection techniques for first true planar IC

> - jean hoerni 设想五个晶体管合在一起，飞线
> Hoerni and Noyce 的发明导致可以平面飞线——第一款平面集成电路的诞生、

---

- 1961: TI and Fairchild introduce the first logic ICs ($50 in quantity)

> - 逻辑 IC 的出现——TI 和仙童公司推出

- 1968: Fairchild’s first MOS integrated circuit product —— a dual J-K flip-flop

> - 使用 MOS 做出双 JK 触发器

- 1968: Noyce and Moore leave Fairchild and form ==**Intel** ==

> - 创建英特尔

- 1970: Intel starts selling 1K-bit RAM, the 1103 ($21)

> - 英特尔做存储器 RAM。传统方法是磁芯做的，1 kbit 要一个柜子，电流还很大

---

- 1971: Intel introduces the first 4-bit microprocessor, the 4004, originally designed as a special circuit for Busicom (2300 transistors)

> - 做了一个4bit的微处理器

- 1976/81: Apple / IBM PC

> - Apple 第一个 PC， IBM 反击（IBM 原来是不商用的，最后intel授权给amd 8008）

- 1985: Intel begins focusing on microprocessor products

> - 英特尔转型（要倒闭了），专注于微处理器产品

- 1987: TSMC is founded (supports fabless model)

> - 台积电成立

- 1991: ARM introduces its first embeddable RISC IP core (supports chipless model)
- 1996: Samsung introduces prototype 1G DRAM
- 1998: IBM Austin Res. Lab announces 1GHz experimental microprocessor
- Intel’s current flagship desktop microprocessors (Core i9) - Tens of billions of transistors, 10 nm(Intel 7) technology, 24 cores, working at >3G (~6G turbo) Hz,~150 W. Competitors are surpassing very quickly onMobile, Desktop and Server products

#### Try To find info of Apple M3 and A17?

### Today's IC Products

#### Processors

- CPU GPU DSP Controllers xPU

#### Memory chips

- RAM (SRAM/DRAM), ROM
- EPROM, EEPROM,FlashROM

#### Programmable

- PLD, FPGA,FPSoC

#### ASICs (专用集成电路) and SoCs（系统级）

- Consumer electronics vs. infrastructural & industrial
- Telecommunication, network,multimedia, power, automobile,aerospace/military, and etc.

#### Apple Phone

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ICCAD/DetailCh1-04.webp)

##### 🔧 主要模块 / Main Modules

###### 📡 无线接口 / Wireless Interface

- **功能**: GSM/EDGE收发器, RF PA, 蓝牙, 802.11, 基带
- **成本**: A(2.35) + B(2.55) + C(1.90) + D(6.00) + E(11.50) + F(1.40) = **$25.70**

###### 💻 应用处理器 / Application Processor

- **功能**: AP, 运动传感器, 显示驱动, 音频编解码, 电源管理
- **成本**: A(2.25) + B(1.50) + C(1.30) + D(28.25) = **$33.30**

###### 💾 存储 / Memory

- **FlashROM**: 4G/8G容量
- **成本**: **$2.35**

###### 📷 摄像头 / Camera

- **CIS模块**: 图像传感器
- **成本**: **$9.50**

##### 🏭 主要供应商 / Key Suppliers

**通信芯片**: Infineon, Qualcomm
**存储**: Samsung
**模拟**: Marvell, National Semi, Wolfson, Linear Tech
**RF**: Skyworks
**蓝牙**: CSR
**摄像头**: OmniVision

## IC manufacturing, Moore’s Law and ITRS roadmap

### Photolithographic Process | 光刻工艺

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ICCAD/DetailCh1-05.webp)

### Transistor and Interconnect Structures ｜ 晶体管与互联结构

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ICCAD/DetailCh1-06.webp)

### Manufactured Wafer and Die ｜ 晶圆和晶粒

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ICCAD/DetailCh1-07.webp)

> 一英寸等于 25.4 mm

### Chip Sawing and Packaging ｜ 芯片切割与封装

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ICCAD/DetailCh1-08.webp)

这张图展示的是一个非常经典和重要的高性能芯片封装结构，叫做 **倒装芯片球栅格阵列（Flip-Chip Ball Grid Array, 简称 FCBGA）**。

它的核心作用是**将功能强大、结构精密的芯片（Die）安全、高效地连接到我们常见的电路板（PCB）上**。

各部分结构详解：

1. **Die (晶粒 / 芯片裸片)**
  - 这就是整个封装的“大脑”，是实际的硅芯片，上面集成了数以亿计的晶体管电路。
  - **关键点**：在这张图中，芯片是“倒装”（Flip-Chip）的，也就是说，它有电路和连接点的那一面是朝下安装的，而不是朝上。
2. **Bumps (凸点)**
  - 这些是在芯片（Die）有电路那一面上制作的微小焊点，通常是焊锡或铜柱。
  - **作用**：它们是连接芯片和下方基板（Laminate）的桥梁，负责传输电信号和电力。相比传统的引线键合（Wire Bonding），这种直接连接路径更短，电学性能更好（延迟低、速度快）。
3. **Laminate (层压基板 / 封装基板)**
  - 你可以把它理解为一个微型的、高密度的印刷电路板（PCB）。
  - **作用**：它扮演着一个“转接器”的角色。芯片上的连接点（Bumps）非常密集，而主电路板上的焊盘间距则大得多。这个基板的作用就是将来自芯片的密集信号“扇出”（Fan-out），重新布局到下方间距更宽的BGA焊球阵列上。
4. **Underfill (底部填充胶)**
  - 这是一种环氧树脂类的胶水，在芯片贴装到基板后，被注入到芯片和基板之间的缝隙里，将所有的Bumps都包裹起来。
  - **作用**（至关重要）：
  
    - **分散应力**：芯片（硅材料）和基板（有机材料）的热膨胀系数不同，在温度变化时会发生不同程度的伸缩。如果没有Underfill，微小的Bumps连接点会因为这种应力而很快断裂。填充胶能将应力分散开，极大地提高了封装的可靠性和寿命。
    - **物理保护**：保护Bumps免受湿气、灰尘等环境因素的侵蚀。
5. **BGA balls (BGA 焊球)**
  - 这些是位于封装基板（Laminate）底部的、尺寸较大的焊球，它们以阵列（Grid Array）的形式排列。
  - **作用**：它们是整个芯片封装与最终产品的主电路板（比如电脑主板、手机主板）进行连接的接口。在装配时，通过加热将这些焊球熔化，从而将整个芯片封装焊接到主板上。
6. **Mold (模塑 / 塑封体)**
  - 这是覆盖在芯片和基板周围的保护性材料，通常是黑色的环氧树脂模塑料。
  - **作用**：为整个结构提供物理保护，防止其受到撞击、划伤和环境侵蚀。

简单来说，这个结构的连接路径是：

**芯片内部电路 → Bumps (凸点) → Laminate (封装基板) → BGA balls (BGA焊球) → 最终产品的电路板 (PCB)**

### Process and Technology Nodes  ｜ 工艺与制造节点

#### What is the Roadmap?

- International Technology Roadmap for Semiconductors **（ITRS）**
- 2017年以后更名为 International Roadmap for Devices and Systems **(IRDS)**

#### Next “node” = 0.7x minimum feature size

- 180->130->90->65->45->32/28->22/20->16/14->10->7->5->3.5(3)->2.5(2)
- 2x transistors on the same size die
- But node definitions gradually lost accurate physical meanings after 90nm node

> 慢慢的后续的节点定义逐渐失去其物理意义

#### Moore 's law

> 用了三个点来预测发展趋势

每十八个月 same size die 上的晶体管数量乘2

#### Psychology: everyone must beat the Roadmap

- Psychology: everyone must beat the Roadmap

好的，这是为您精简后的Markdown格式版本：

#### 报告概述：摩尔定律与ITRS路线图

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ICCAD/DetailCh1-09.webp)

内容为 **ITRS (国际半导体技术路线图)** 在2007年发布的对未来技术趋势的预测，旨在量化摩尔定律的进程。

##### 图表信息解析

- **图表标题**: 2007年ITRS产品技术趋势 - 半间距与栅长
- **核心指标**:

  - **半间距 (Half-Pitch)**: 衡量芯片**密度**。
  - **栅长 (Gate-Length)**: 决定晶体管**性能**。
- **坐标轴**:

  - **X轴**: 生产年份 (1995-2025)。
  - **Y轴**: 关键尺寸 (nm)，为**对数坐标**，直观展示指数级缩小。

---

##### 关键尺寸趋势 (数据曲线)

- **DRAM M1 1/2 Pitch**: DRAM的集成密度趋势。
- **MPU M1 1/2 Pitch**: 微处理器（MPU）的互连线密度趋势，遵循**2.5年周期**。
- **Flash Poly 1/2 Pitch**: 闪存的存储单元密度趋势。
- **MPU Gate Length - Printed**: 光刻工艺中“印刷”的栅极尺寸。
- **MPU Gate Length - Physical**: 最终形成的**实际**栅极长度，通常更小。

##### 技术演进速度 (黄色框注释)

- `.71X/NYR` **含义**: 尺寸在`N`年内缩小为0.71倍，使芯片面积减半，晶体管数量翻倍。
- **周期变化**:

  - **1998年前**: 3年周期。
  - **1998年后**: 加速为2年周期（经典摩尔定律）。
- **不同产品的周期**:

  - **闪存 (Flash)**: 2年 (最激进)。
  - **微处理器互连线 (MPU M1)**: 2.5年。
  - **微处理器栅长 (Gate Length)**: 3年。
- **重要里程碑**:

  - **1999年**: 小于100nm的**纳米技术时代**开始。
- **尺寸关系**:

  - `GLpr IS = 1.6818 x GLph`: 预测了印刷栅长(pr)与物理栅长(ph)的定量关系。
- **预测范围**:

  - 此图表的预测时间段为 **2007 - 2022年**。
- 2007年的规划**: 展示了当时行业对技术协同发展的清晰规划，摩尔定律依然有效。
- **发展速度差异**: 不同产品（闪存、MPU等）的演进速度存在差异。
- **历史视角**: 这是一个基于当时认知的预测。如今，行业已通过FinFET、GAA、3D堆叠等新技术延续摩尔定律精神。

## Model of IC industry

### Challenges and Demands Facing IC Production

1. Increasing device and chip complexity ｜ 设备和芯片更复杂

  - **Moore’s Law on chip scale**
  - Processors, software, memory, analog blocks and more
  - Implementation and verification more difficult ｜ 实施和验证过程更加困难
2. Nanometer effects ｜ 纳米效应

  - **Moore’s Law on device shrinking**
  - Cross-coupling, signal integrity, device variation, manufacturability, leakage & power ｜ 交叉耦合、信号完整性、器件差异、可制造性、泄漏与功率
3. Stronger market pressures

  - Moore’s Law on generation time
  - Quick development; price competition
  - Performance, area, and power demands ｜ 性能、面积和功耗要求

### Business Models

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ICCAD/DetailCh1-10.webp)

这张图展示了半导体产业从“垂直整合”到“水平分工”的演变。

- 1970年以前：IDM模式

> - 一家公司包揽所有环节，典型代表是英特尔（Intel）。

- 
- 1970-1990年：设计与制造分离

> - 产业开始分工，出现了只负责设计的Fabless（如英伟达NVIDIA、高通Qualcomm）和只负责制造的Foundry（如台积电TSMC）。

- 
- 1990年以后：专业化分工深化

> - 分工更加细化，诞生了提供核心设计方案的IP厂商，最成功的代表是ARM。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ICCAD/DetailCh1-11.webp)

2024年 第一是nvidia 第二是samsung 第三是intel

2017年 第一是qualcomm 高通 第二是broadcom 第三是nvidia

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ICCAD/DetailCh1-12.webp)

#### 倒金字塔结构

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ICCAD/DetailCh1-13.webp)

电子系统占了2万亿（trillion）美元，半导体占了527Billion，eda占了13B，其中半导体占据了20%到30%以上，逐渐也在上升

## EDA and EDA industry | EDA与EDA行业

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ICCAD/DetailCh1-14.webp)

- 劳动生产力or产出率（单位是Trans./staff -Mo.  每个人、月设计的晶体管数目）
- 红色曲线（**每年58%增长——摩尔定律**  (1 + 0.58)^{1.5} = ?）--每个芯片上逻辑晶体管的数量 从10k个到很多很多个晶体管
- 绿色和红色之间有非常大的gap 每个人每个月能完成的晶体管数目只以21%的速率在增长——要增加工程师数目，提出的新的要求——劳动生产率提上去，趋势如同蓝色的线所示

> 怎样提升劳动生产力呢？——使用计算机辅助设计工具 ——EDA

**EDA stands for Electronic Design Automation**

Subtle differences between EDA and ICCAD | EDA 和 ICCAD 的细微区别？

EDA是只要是辅助做电子系统都是EDA，而ICCAD一定是和IC相关的辅助设计工具

> ICCAD占据了EDA的90%左右

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ICCAD/DetailCh1-15.webp)

该图展示了**EDA (电子设计自动化)** 的四个层次，而**ICCAD**是其中的核心子集。

- **ICCAD (集成电路设计)**
  - **主要环节**: **第3部分 - 半导体产业**
  - **核心任务**: 逻辑综合、布局布线、电路仿真。
- **EDA的其他范畴 (非ICCAD)**
  - **系统级设计 (ESL)**: **第1、2部分**，负责更高层的算法（现实世界）和架构（电子系统）。

> - 第二部分也有部分是ICCAD

- 
- **工艺级设计 (TCAD)**: **第4部分**，负责底层的器件和制造工艺（硅晶圆代工厂）。

### 设计生产力跃升趋势

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ICCAD/DetailCh1-16.webp)

这幅图使用**麦肯锡S曲线**模型，展示了集成电路（IC）设计生产力随着技术范式的变迁而不断跃升的过程。核心是**设计抽象层次的不断提高**。

##### 演进的三个主要阶段

1. **晶体管级输入 (Transistor entry)**
  - **方式**: 工程师手动绘制独立的晶体管物理版图。
  - **代表公司**: Calma, Computervision。
2. **原理图输入 (Schematic Entry)**
  - **方式**: 设计抽象到用逻辑门（AND, OR等）连接电路，生产力大幅提升。
  - **代表公司**: Daisy, Mentor, Valid。
3. **综合 (Synthesis)**
  - **方式**: 设计再次抽象到用硬件描述语言（如Verilog）写代码，由EDA工具自动生成电路。这是现代数字设计的基石，生产力实现巨大飞跃。
  - **代表公司**: Cadence, Synopsys。

##### 未来趋势 (What's next?)

图表最后提出疑问：继“综合”之后，下一个能带来生产力巨大飞跃的技术范式是什么？（这通常指向更高层次的抽象，如**高级综合HLS**、**系统级设计ESL**等）。

<table>
<thead>
  <tr>
    <th>
      特性
    </th>
    
    <th>
      C语言 (HLS)
    </th>
    
    <th>
      Chisel
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      目标
    </td>
    
    <td>
      从算法到RTL
    </td>
    
    <td>
      更好地生成RTL
    </td>
  </tr>
  
  <tr>
    <td>
      抽象层次
    </td>
    
    <td>
      更高 (行为级/算法级)
    </td>
    
    <td>
      与RTL同级 (但表达能力更强)
    </td>
  </tr>
  
  <tr>
    <td>
      输出
    </td>
    
    <td>
      Verilog/VHDL 代码
    </td>
    
    <td>
      Verilog 代码
    </td>
  </tr>
  
  <tr>
    <td>
      解决的问题
    </td>
    
    <td>
      复杂算法的硬件实现效率
    </td>
    
    <td>
      RTL设计的复用性、参数化和工程化
    </td>
  </tr>
</tbody>
</table>

### 自上而下的设计流程

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ICCAD/DetailCh1-17.webp)

### 世界EDA公司

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ICCAD/DetailCh1-18.webp)

### Industry’s IC Design Flow in Evolution ｜ IC设计工作流

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ICCAD/DetailCh1-19.webp)

### Mainstream ICCAD Tools on Different Levels  ｜ 主流ICCAD工具

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ICCAD/DetailCh1-20.webp)

> 蓝色的是开源的

#### example ｜ 举例

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ICCAD/DetailCh1-21.webp)

### EDA计算平台演进历史详解

<table>
<thead>
  <tr>
    <th>
      年代
    </th>
    
    <th>
      时代主题
    </th>
    
    <th>
      关键架构
    </th>
    
    <th>
      操作系统家族
    </th>
    
    <th>
      代表厂商/产品线
    </th>
    
    <th>
      硬件/软件平台组合
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      1980s
    </td>
    
    <td>
      专用工作站时代
    </td>
    
    <td>
      私有/定制化, Motorola 68k
    </td>
    
    <td>
      专有 OS
    </td>
    
    <td>
      Daisy/Logician
    </td>
    
    <td>
      SUN 2/3 + SunOS
    </td>
  </tr>
  
  <tr>
    <td>
      
    </td>
    
    <td>
      
    </td>
    
    <td>
      
    </td>
    
    <td>
      
    </td>
    
    <td>
      Mentor/Apollo
    </td>
    
    <td>
      Apollo DN300 + Aegis
    </td>
  </tr>
  
  <tr>
    <td>
      
    </td>
    
    <td>
      
    </td>
    
    <td>
      
    </td>
    
    <td>
      
    </td>
    
    <td>
      Valid/Scald
    </td>
    
    <td>
      DEC MicroVAX + VMS
    </td>
  </tr>
  
  <tr>
    <td>
      1990s
    </td>
    
    <td>
      UNIX工作站黄金时代
    </td>
    
    <td>
      RISC (SPARC, PA-RISC, PowerPC)
    </td>
    
    <td>
      商业 UNIX
    </td>
    
    <td>
      Sun Microsystems
    </td>
    
    <td>
      SPARCstation (Sun4/5/10/20) + Solaris
    </td>
  </tr>
  
  <tr>
    <td>
      
    </td>
    
    <td>
      
    </td>
    
    <td>
      
    </td>
    
    <td>
      
    </td>
    
    <td>
      Mentor Graphics
    </td>
    
    <td>
      HP PA-RISC + HP-UX
    </td>
  </tr>
  
  <tr>
    <td>
      
    </td>
    
    <td>
      
    </td>
    
    <td>
      
    </td>
    
    <td>
      
    </td>
    
    <td>
      (其他主流)
    </td>
    
    <td>
      IBM RS/6000 + AIX, DECstation + Ultrix
    </td>
  </tr>
  
  <tr>
    <td>
      2000s
    </td>
    
    <td>
      X86架构崛起
    </td>
    
    <td>
      RISC, x86
    </td>
    
    <td>
      商业 UNIX, Windows, Linux
    </td>
    
    <td>
      Sun Microsystems
    </td>
    
    <td>
      Sun Ultra + Solaris
    </td>
  </tr>
  
  <tr>
    <td>
      
    </td>
    
    <td>
      
    </td>
    
    <td>
      
    </td>
    
    <td>
      
    </td>
    
    <td>
      Mentor Graphics
    </td>
    
    <td>
      HP PA-RISC + HP-UX (仍在用)
    </td>
  </tr>
  
  <tr>
    <td>
      
    </td>
    
    <td>
      
    </td>
    
    <td>
      
    </td>
    
    <td>
      
    </td>
    
    <td>
      Cadence/Valid
    </td>
    
    <td>
      x86 PC/Server + Windows NT/2000
    </td>
  </tr>
  
  <tr>
    <td>
      2010s
    </td>
    
    <td>
      X86/Linux云与数据中心
    </td>
    
    <td>
      x86-64
    </td>
    
    <td>
      Linux (主流), Windows
    </td>
    
    <td>
      所有EDA厂商
    </td>
    
    <td>
      Intel/AMD x86-64 Servers + Linux (RHEL/CentOS)
    </td>
  </tr>
  
  <tr>
    <td>
      
    </td>
    
    <td>
      
    </td>
    
    <td>
      
    </td>
    
    <td>
      
    </td>
    
    <td>
      (传统平台)
    </td>
    
    <td>
      Oracle Sun Server + Solaris (逐渐边缘化)
    </td>
  </tr>
  
  <tr>
    <td>
      未来?
    </td>
    
    <td>
      异构与云原生时代
    </td>
    
    <td>
      x86-64, ARM, GPU/FPGA
    </td>
    
    <td>
      Linux, 云原生OS
    </td>
    
    <td>
      云计算平台
    </td>
    
    <td>
      AWS Graviton (ARM), NVIDIA DGX (GPU) + Cloud Services
    </td>
  </tr>
  
  <tr>
    <td>
      
    </td>
    
    <td>
      
    </td>
    
    <td>
      
    </td>
    
    <td>
      
    </td>
    
    <td>
      (趋势)
    </td>
    
    <td>
      硬件加速、EDA上云 (SaaS)、架构多元化
    </td>
  </tr>
</tbody>
</table>

### Unix-based Platforms

- Software platforms ｜ **软件平台 - 环境的演进**
  - Various versions of Unix./Unix-like ｜ **Unix/类Unix系统**: 传统核心，以其强大的性能和稳定性著称 (如 Linux)。
  - Windows ：作为补充，提供图形化界面和更广泛的桌面应用支持。
  - Cloud-based computing ｜ 未来的方向，提供按需分配的、可扩展的计算资源。
- Needs and supports ｜ **平台需求与支撑工具 - 保证生产力**
  - Computing power, stability, ease of use, security and low cost
  - Operating system, window system, C compiler, file sharing,software distribution, remote monitoring, shell scripting,batch scheduling, supporting languages (Perl, Tcl/Tk,Python) and etc.
