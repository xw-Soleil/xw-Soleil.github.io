# L13-14：复杂流水线（衔接 L7）

> 在 L7 基础上展开的乱序执行、指令发射与调度等复杂流水线机制

还没仔细理，主要就理了一下ppt结构，ppt全部截进来了

AI根据作业和历年卷总结的重点为：

<alert type="tip">

重点在：**BHT/BTB、分支预测、RAW/WAR/WAW、寄存器重命名、ROB、乱序发射、精确异常。**

深度要求：**能解释乱序执行为什么需要重命名和 ROB，能比较 BHT/BTB**。

</alert>

## 1. OoO 基本概念（简单回顾，基本都是L7的内容）

**OoO Basic Concepts**

### 1.1 流水线中的指令交互

简单回顾一下：

流水线中，指令之间可能互相影响，形成三类冒险：

结构冒险、数据冒险、控制冒险。

这些冒险会引入 bubble，使 CPI 增大，性能下降。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-01.webp)

### 1.2 数据冒险的基本处理策略

主要有三种方法：

停顿、前递、推测。

停顿保证正确性，但降低性能。

前递减少等待，但硬件更复杂。

推测提高并行度，但错误时需要恢复。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-02.webp)

### 1.3 停顿与前递

停顿是让相关指令等待结果写回。

前递是不等写回，直接把计算结果送给后续指令。

前递可以减少甚至消除部分数据冒险带来的 bubble。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-03.webp)

### 1.4 完全旁通数据通路

Fully Bypass Data Path 允许结果从流水线中间阶段直接传给后续指令。

这样后续指令不必等寄存器写回，就可以使用结果。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-04.webp)

### 1.5 寄存器依赖与内存依赖

寄存器依赖通常在 Decode 阶段即可判断。

内存依赖必须等有效地址计算后才能判断。

因此内存相关性比寄存器相关性更难处理。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-05.webp)

### 1.6 复杂流水线的动机

高性能处理器中会出现：

长延迟 FPU、可变延迟内存、多功能单元。

这些因素使简单五级流水线难以满足性能需求。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-06.webp)

### 1.7 复杂流水线中的新问题

复杂流水线会带来新的冲突：

执行阶段结构冒险、写回阶段结构冒险、乱序写回、异常处理困难。

核心问题是：不同指令的执行时间不再统一。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-07.webp)

### 1.8 数据冒险类型

<table>
<thead>
  <tr>
    <th>
      类型
    </th>
    
    <th>
      含义
    </th>
    
    <th>
      本质
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      RAW
    </td>
    
    <td>
      写后读
    </td>
    
    <td>
      真正数据依赖
    </td>
  </tr>
  
  <tr>
    <td>
      WAR
    </td>
    
    <td>
      读后写
    </td>
    
    <td>
      名称依赖
    </td>
  </tr>
  
  <tr>
    <td>
      WAW
    </td>
    
    <td>
      写后写
    </td>
    
    <td>
      名称依赖
    </td>
  </tr>
</tbody>
</table>

RAW 不能消除。

WAR 和 WAW 可通过寄存器重命名消除。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-08.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-09.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-10.webp)

### 1.9 从复杂顺序流水线到乱序执行

一种保守方法是延迟写回，使所有指令在统一阶段写回。

这样便于控制冒险和异常，但会拖慢短延迟指令。

因此需要更高效的方法：乱序执行。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-11.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-12.webp)

### 1.10 什么是乱序执行

OoO 指：只要操作数准备好、功能单元可用，指令就可以先执行。

程序顺序不一定等于执行顺序。

但最终结果必须保持程序语义正确。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-13.webp)

### 1.11 为什么使用乱序执行

乱序执行的目的不是“打乱顺序”，而是提高性能。

它可以：

- 容忍长延迟；
- 挖掘指令级并行性；
- 提高功能单元利用率；
- 减少流水线空等。

代价是硬件复杂、面积大、功耗高。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-14.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-15.webp)

---

## 2. 顺序发射

**In-Order Issue**

### 2.1 指令调度

指令调度关注的是：**指令以什么顺序进入执行阶段**。

顺序发射要求：

```text
I1 → I2 → I3 → I4 → I5 → I6
```

也就是后一条指令不能越过前一条指令先发射。

即使后面的指令已经准备好，只要前面的指令不能发射，后面的也要等待。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-16.webp)

### 2.2 指令何时可以安全发射

在 Issue 阶段，发射一条指令前需要检查：

<table>
<thead>
  <tr>
    <th>
      检查内容
    </th>
    
    <th>
      目的
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      功能单元是否可用
    </td>
    
    <td>
      避免结构冒险
    </td>
  </tr>
  
  <tr>
    <td>
      源操作数是否可用
    </td>
    
    <td>
      避免 RAW 冒险
    </td>
  </tr>
  
  <tr>
    <td>
      目的寄存器是否安全
    </td>
    
    <td>
      避免 WAR / WAW 冒险
    </td>
  </tr>
  
  <tr>
    <td>
      写回端口是否冲突
    </td>
    
    <td>
      避免 WB 阶段结构冒险
    </td>
  </tr>
</tbody>
</table>

如果这些检查都通过，指令才能进入对应功能单元。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-17.webp)

### 2.3 正确发射所需的数据结构

为了判断能否发射，需要记录功能单元中正在执行的指令状态。

典型表项包括：

<table>
<thead>
  <tr>
    <th>
      字段
    </th>
    
    <th>
      含义
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      Name
    </td>
    
    <td>
      功能单元名称
    </td>
  </tr>
  
  <tr>
    <td>
      Busy
    </td>
    
    <td>
      是否被占用
    </td>
  </tr>
  
  <tr>
    <td>
      Op
    </td>
    
    <td>
      正在执行的操作
    </td>
  </tr>
  
  <tr>
    <td>
      Dest
    </td>
    
    <td>
      目的寄存器
    </td>
  </tr>
  
  <tr>
    <td>
      Src1 / Src2
    </td>
    
    <td>
      源寄存器
    </td>
  </tr>
</tbody>
</table>

发射时通过这个表检查：

- `Busy`：功能单元是否空闲；
- `Dest`：是否有 RAW / WAW；
- `Src`：是否有 WAR。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-18.webp)

### 2.4 顺序发射的数据结构简化

在顺序发射中，指令按程序顺序进入功能单元。

因此：

- 操作数通常在 Issue 阶段就被读取；
- 后面的指令不会先于前面的指令读取操作数；
- 所以 **WAR 冒险不会发生**。

但仍然需要处理：

- RAW；
- WAW；
- 功能单元冲突；
- 写回冲突。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-19.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-20.webp)

### 2.5 Scoreboard 记分板

顺序发射可以用简化的 scoreboard 管理状态。

主要记录两个 bit-vector：

<table>
<thead>
  <tr>
    <th>
      结构
    </th>
    
    <th>
      作用
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      Busy<span>
        FU#
      </span>
    </td>
    
    <td>
      记录功能单元是否忙
    </td>
  </tr>
  
  <tr>
    <td>
      WP<span>
        reg#
      </span>
    </td>
    
    <td>
      记录某个寄存器是否正在等待写回
    </td>
  </tr>
</tbody>
</table>

发射一条指令时：

```text
功能单元可用？ → 看 Busy[FU]
RAW？ → 看 WP[src1] 或 WP[src2]
WAW？ → 看 WP[dest]
WAR？ → 顺序发射中不会发生
```

如果可以发射：

- 设置对应功能单元 Busy；
- 设置 `WP[dest]`；
- 等写回后再清除。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-21.webp)

### 2.6 记分板动态示例

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-22.webp)

核心逻辑是：

- 如果源寄存器还在 `WP` 中，说明数据未准备好，不能发射；
- 如果目的寄存器已在 `WP` 中，说明存在 WAW，不能发射；
- 如果功能单元忙，也不能发射。

所以 scoreboard 的作用是：**在不乱发射的前提下，保证指令按顺序安全进入功能单元**。

### 2.7 乱序完成、顺序发射

顺序发射不代表顺序完成。

原因是不同功能单元延迟不同：

```text
Load 可能 1 周期完成
FAdd 可能 1 周期完成
FMul 可能 3 周期完成
FDiv 可能 4 周期完成
```

所以即使发射顺序是：

```text
I1 → I2 → I3 → I4
```

完成顺序也可能是：

```text
I2 → I1 → I3 → I4
```

这就是：**顺序发射，乱序完成**。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-23.webp)

### 2.8 顺序发射的局限

顺序发射最大的局限是：**前面指令卡住，会阻塞后面所有指令**。

即使后面的指令：

- 不依赖前面的数据；
- 功能单元也空闲；
- 本来可以执行；

也不能越过前面的指令先发射。

因此，顺序发射无法充分挖掘 ILP，会浪费可用的功能单元。

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 49.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-24.webp" />
      </p>
    </td>
    
    
      <td style="width: 50.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-25.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

### 总结：

顺序发射的核心机制是：

```text
按程序顺序检查指令 → 确认无冒险 → 发射到功能单元
```

它的优点是：

- 控制简单；
- 冒险判断相对容易；
- WAR 不会发生；
- 容易保证程序语义。

它的缺点是：

- 前面指令会阻塞后面指令；
- 功能单元利用率不高；
- 无法充分利用指令级并行性；
- 面对长延迟指令时性能损失明显。

---

## 3. 乱序发射

**Out-of-Order Issue**

### 3.1 乱序发射机制

顺序发射中，前面的指令卡住，后面的指令也不能发射。

乱序发射则在 Issue 阶段设置一个缓冲区，保存多条等待发射的指令。

基本规则是：

```text
只要指令的源操作数准备好，功能单元可用，就可以先发射。
```

因此，后面的独立指令可以越过前面被阻塞的指令先执行。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-26.webp)

---

### 3.2 流水线中可容纳多少指令

流水线中可同时存在多少条指令，主要受两个因素限制：

<table>
<thead>
  <tr>
    <th>
      限制来源
    </th>
    
    <th>
      含义
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      ISA 寄存器数量
    </td>
    
    <td>
      寄存器名太少会造成 WAR / WAW 名称冲突
    </td>
  </tr>
  
  <tr>
    <td>
      控制流转移
    </td>
    
    <td>
      分支会限制可连续取到的指令数量
    </td>
  </tr>
</tbody>
</table>

所以，仅有乱序调度还不够，还需要解决寄存器名不足和分支控制流问题。

---

### 3.3 寄存器名称不足问题

ISA 中的寄存器数量有限。

例如浮点寄存器较少时，多条无关指令可能因为用了相同寄存器名而产生冲突。

这些冲突不一定是真正的数据依赖，而是**名称依赖**。

典型包括：

- WAR；
- WAW。

如果不处理这些名称依赖，乱序发射的空间会很小。

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 43.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-27.webp" />
      </p>
    </td>
    
    
      <td style="width: 56.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-28.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-29.webp)

---

### 3.4 寄存器重命名

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-30.webp)

寄存器重命名的作用是：

```text
把架构寄存器名映射到更多的内部物理寄存器或 ROB 标签。
```

这样可以消除 WAR 和 WAW。

例如原本：

```text
DIVD F4, F2, F8
ADDD F10, F6, F4
```

如果后面又要写 `F4`，可能产生名称冲突。
重命名后可以变成：

```text
DIVD F4', F2, F8
ADDD F10, F6, F4'
```

这样新的 `F4'` 和旧的 `F4` 不再混淆。

结论：

```text
RAW 是真实依赖，不能消除；
WAR / WAW 是名称依赖，可以通过重命名消除。
```

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-31.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-32.webp)

---

### 3.5 ROB 重排序缓冲区

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-33.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-34.webp)

ROB，即 Reorder Buffer，用来保存已经解码但还未最终提交的指令。

它的作用包括：

- 保存指令状态；
- 保存操作数或操作数标签；
- 保存执行结果；
- 保存异常信息；
- 支持乱序执行；
- 支持顺序提交。

简单理解：

```text
ROB 让指令可以乱序执行，但最后仍然按程序顺序提交。
```

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-35.webp)

---

### 3.6 数据驱动执行

乱序发射的执行方式接近数据流模型。

一条指令能否发射，主要看两个条件：

```text
源操作数是否都准备好？
功能单元是否可用？
```

只要满足条件，就可以从 Issue Buffer / ROB 中被选中执行。

这叫 **data-driven execution**，也就是由数据是否准备好来驱动执行顺序。

---

### 3.7 Tomasulo 算法思想

Tomasulo 算法是早期乱序执行的重要实现方法。

核心思想包括：

<table>
<thead>
  <tr>
    <th>
      结构
    </th>
    
    <th>
      作用
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      Reservation Station
    </td>
    
    <td>
      保存等待执行的指令
    </td>
  </tr>
  
  <tr>
    <td>
      Tag
    </td>
    
    <td>
      标记数据来源
    </td>
  </tr>
  
  <tr>
    <td>
      Common Data Bus
    </td>
    
    <td>
      广播执行结果
    </td>
  </tr>
  
  <tr>
    <td>
      Register Renaming
    </td>
    
    <td>
      消除名称依赖
    </td>
  </tr>
</tbody>
</table>

当某个功能单元产生结果时，会广播：

```text
<tag, result>
```

等待这个 tag 的指令收到结果后，就可以继续执行。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-36.webp)

---

### 3.8 乱序执行早期受限原因

乱序执行在 1960 年代已经出现，但很长时间没有广泛流行。

主要原因是：

- 精确异常难实现；
- 当时可利用的 ILP 有限；
- 内存延迟问题更突出；
- 控制流分支限制严重；
- 硬件复杂度和成本较高。

所以 OoO 真正普及是在 1990 年代之后。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-37.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-38.webp)

---

### 3.9 精确中断与异常

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-39.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-40.webp)

精确中断要求处理器状态看起来像是：

```text
中断发生在两条指令之间。
```

具体要求：

- 中断前的所有指令都已经完成；
- 中断后的所有指令都没有产生影响；
- 程序可以从正确位置重新开始。

乱序执行的问题是：

后面的指令可能已经先完成，因此异常处理会变复杂。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-41.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-42.webp)

---

### 3.10 顺序提交实现精确异常

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-43.webp)

解决方法是：

```text
执行可以乱序，但提交必须顺序。
```

也就是：

```text
Fetch / Decode：顺序
Execute：乱序
Commit：顺序
```

这样即使指令乱序完成，也不会立刻修改体系结构状态。

只有当它到达 ROB 队头，并且前面指令都已经提交后，才可以正式提交。

这保证了精确异常。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-44.webp)

---

### 3.11 回滚与重命名表恢复

如果发生异常或分支预测错误，需要恢复到正确状态。

需要恢复的内容包括：

- PC；
- ROB；
- Rename Table；
- 推测执行产生的临时结果。

一种方法是在分支预测时保存 Rename Table 的快照。

如果预测错误，就恢复旧快照，并清除错误路径上的指令。

核心目标是：

```text
把处理器状态恢复到错误发生前的正确程序状态。
```

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-45.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-46.webp)

---

## 第三部分总结

乱序发射的核心机制是：

```text
多条指令进入等待区 → 操作数准备好就发射 → 执行乱序 → 提交顺序
```

它相比顺序发射的优势是：

- 后面的独立指令可以越过前面的阻塞指令；
- 更能容忍长延迟；
- 更能挖掘 ILP；
- 功能单元利用率更高。

但它也带来新的复杂性：

- 需要寄存器重命名；
- 需要 ROB；
- 需要恢复机制；
- 需要处理精确异常；
- 需要更复杂的调度逻辑。

---

## 4. 分支预测

**Branch Prediction**

### 4.1 控制流惩罚

分支指令会决定程序接下来执行哪条路径。

但分支结果通常要到后面的执行阶段才知道。

在这之前，处理器有两个选择：

```text
等待分支结果 → 流水线空转
先猜一个方向 → 可能预测错误
```

现代处理器流水线很深，如果预测错误，会浪费大量已经取指、解码甚至执行的指令。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-47.webp)

---

### 4.2 分支之间的平均运行长度

程序中分支指令出现频率很高。

例如整数程序中，大约每几条指令就会遇到一次分支。

这说明：

```text
控制冒险不是偶发问题，而是高性能流水线的常见瓶颈。
```

如果不能有效处理分支，前端取指会频繁中断。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-48.webp)

---

### 4.3 减少控制流惩罚的方法

减少分支惩罚主要有软件和硬件两类方法。

<table>
<thead>
  <tr>
    <th>
      方法
    </th>
    
    <th>
      例子
    </th>
    
    <th>
      作用
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      软件方法
    </td>
    
    <td>
      循环展开、指令调度
    </td>
    
    <td>
      减少分支数量或提前计算分支
    </td>
  </tr>
  
  <tr>
    <td>
      硬件方法
    </td>
    
    <td>
      延迟槽、分支预测、推测执行
    </td>
    
    <td>
      让流水线不停等
    </td>
  </tr>
</tbody>
</table>

其中最重要、最常用的是：

```text
分支预测 + 推测执行
```

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-49.webp)

---

### 4.4 分支预测的动机与硬件支持

分支预测的目标是：

```text
在分支真正解析前，提前猜测下一条取指地址。
```

如果预测正确，流水线几乎不断流。

如果预测错误，则清除错误路径并恢复正确 PC。

需要的硬件包括：

- BHT：预测分支方向；
- BTB：预测分支目标地址；
- Return Stack：预测函数返回地址；
- Mispredict Recovery：错误预测恢复机制。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-50.webp)

---

### 4.5 分支预测的重要性

分支预测准确率越高，浪费的指令越少。

例如从 90% 提升到 95%，看似只提高 5%，但错误预测次数减少了一半。

原因是：

```text
错误率从 10% 降到 5%，mispredict 数量减少 50%。
```

所以高性能处理器非常依赖高准确率分支预测器。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-51.webp)

---

### 4.6 静态分支预测

静态预测不依赖运行时历史，而是使用固定规则。

常见规则：

- 默认预测 taken；
- 默认预测 not taken；
- 向后分支预测 taken；
- 向前分支预测 not taken；
- 由 ISA 或编译器给出提示。

局限是：

它无法根据程序实际运行行为动态调整。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-52.webp)

---

### 4.7 动态分支预测

动态预测根据过去行为预测未来行为。

主要利用两类相关性：

<table>
<thead>
  <tr>
    <th>
      相关性
    </th>
    
    <th>
      含义
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      时间相关性
    </td>
    
    <td>
      同一个分支过去怎么走，下次大概率也类似
    </td>
  </tr>
  
  <tr>
    <td>
      空间相关性
    </td>
    
    <td>
      不同分支之间可能存在相关关系
    </td>
  </tr>
</tbody>
</table>

动态预测比静态预测更准确，是现代处理器的主流方法。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-53.webp)

---

### 4.8 一位与两位分支历史预测器

一位预测器只记录上一次结果。

问题是循环分支容易错两次：

```text
进入循环时可能错一次
退出循环时又错一次
```

两位预测器使用饱和计数器，需要连续两次预测错误才改变方向。

因此它更稳定，能减少循环边界处的错误预测。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-54.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-55.webp)

---

### 4.9 BHT 分支历史表

BHT，即 Branch History Table，用于记录分支历史方向。

基本过程：

```text
用 PC 索引 BHT → 读出预测位 → 判断 taken / not taken
```

BHT 主要预测：

```text
分支是否会跳转
```

但它只给方向，不直接给目标地址。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-56.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-57.webp)

---

### 4.10 两级分支预测器

两级预测器利用更长的历史信息。

基本思想：

```text
先记录最近几个分支的历史
再用历史模式选择对应的预测表项
```

它可以捕捉多个分支之间的相关性。

例如：

```text
if (x[i] < 7)
if (x[i] < 5)
```

第一个条件的结果可能帮助预测第二个条件。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-58.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-59.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-60.webp)

---

### 4.11 BTB 分支目标缓冲区

BTB，即 Branch Target Buffer。

BHT 只能预测方向，BTB 可以预测目标地址。

基本作用是：

```text
如果当前 PC 命中 BTB，就直接给出预测跳转目标。
```

这样处理器不必等到分支解码或执行后才知道跳转地址。

BTB 对 taken branch 尤其重要。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-61.webp)

---

### 4.12 BTB 与 BHT 结合

BTB 和 BHT 功能不同：

<table>
<thead>
  <tr>
    <th>
      结构
    </th>
    
    <th>
      主要作用
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      BHT
    </td>
    
    <td>
      预测分支方向
    </td>
  </tr>
  
  <tr>
    <td>
      BTB
    </td>
    
    <td>
      预测分支目标地址
    </td>
  </tr>
</tbody>
</table>

BTB 更贵，容量通常较小，但能更早重定向取指。

BHT 更便宜，容量可以更大，方向预测更灵活。

现代处理器通常结合使用二者。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-62.webp)

---

### 4.13 跳转寄存器与返回栈

有些跳转目标不是立即数，而是寄存器中的地址。

典型场景：

- switch 语句；
- 动态函数调用；
- 子程序返回。

其中函数返回比较特殊。

同一个函数可能从很多地方被调用，所以返回地址变化频繁。

因此处理器使用 **Return Stack**：

```text
函数调用时 push 返回地址
函数返回时 pop 返回地址
```

它通常比普通 BTB 更适合预测函数返回。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-63.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-64.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-65.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-66.webp)

---

### 4.14 顺序与乱序机器中的分支预测

顺序处理器和乱序处理器都需要分支预测。

两者前端可以使用类似的预测器。

区别在于错误恢复：

<table>
<thead>
  <tr>
    <th>
      类型
    </th>
    
    <th>
      错误预测恢复
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      顺序执行
    </td>
    
    <td>
      清除分支后的流水线指令
    </td>
  </tr>
  
  <tr>
    <td>
      乱序执行
    </td>
    
    <td>
      还要恢复 ROB、Rename Table、推测状态
    </td>
  </tr>
</tbody>
</table>

乱序机器中，分支后的指令可能已经执行完成，所以恢复机制更复杂。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-67.webp)

---

### 4.15 分支预测错误恢复

预测错误时，处理器需要：

- 清除错误路径上的指令；
- 恢复正确 PC；
- 恢复 ROB 状态；
- 恢复 Rename Table；
- 重新从正确地址取指。

简单理解：

```text
预测正确 → 继续执行
预测错误 → Kill 错误路径，恢复正确状态
```

为了快速恢复，处理器可能在每个未解析分支处保存 Rename Table 快照。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-68.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-69.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-70.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-71.webp)

---

## 第四部分总结

分支预测的核心机制是：

```text
提前预测分支方向和目标地址 → 沿预测路径继续取指执行 → 错了再恢复
```

它的作用是：

- 减少控制冒险带来的流水线停顿；
- 提高前端取指连续性；
- 降低深流水线中的分支惩罚；
- 支持 OoO 和超标量处理器持续供给指令。

它的代价是：

- 需要预测表结构；
- 需要错误恢复机制；
- 预测错误会浪费大量执行资源；
- OoO 中恢复逻辑更复杂。

---

## 5. 统一物理寄存器文件

**Unified Physical Register File**

### 5.1 OoO 设计选择

乱序处理器有多个实现选择，主要包括：

<table>
<thead>
  <tr>
    <th>
      问题
    </th>
    
    <th>
      选择
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      保留站放在哪里
    </td>
    
    <td>
      集中式 Issue Window 或分布式 Reservation Station
    </td>
  </tr>
  
  <tr>
    <td>
      ROB 是否保存数据
    </td>
    
    <td>
      ROB 保存结果，或只保存状态信息
    </td>
  </tr>
  
  <tr>
    <td>
      重命名如何实现
    </td>
    
    <td>
      ROB 标签重命名，或物理寄存器重命名
    </td>
  </tr>
</tbody>
</table>

统一物理寄存器文件属于后者：
**数据主要放在物理寄存器文件中，而不是 ROB 中。**

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-72.webp)

---

### 5.2 统一物理寄存器文件思想

UPRF 的核心思想是：

```text
架构寄存器名 → 物理寄存器名
```

例如：

```text
x1 → P8
x3 → P7
x6 → P5
```

执行单元不再直接使用 `x1、x2、x3` 这类架构寄存器，而是使用 `P0、P1、P2` 这类物理寄存器。

这样做的好处是：

- 消除 WAR；
- 消除 WAW；
- 支持更多临时结果；
- 减少 ROB 中的数据移动。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-73.webp)

---

### 5.3 物理寄存器生命周期

物理寄存器文件同时保存两类值：

<table>
<thead>
  <tr>
    <th>
      类型
    </th>
    
    <th>
      含义
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      Committed value
    </td>
    
    <td>
      已经提交的正确体系结构状态
    </td>
  </tr>
  
  <tr>
    <td>
      Speculative value
    </td>
    
    <td>
      乱序执行产生的临时结果
    </td>
  </tr>
</tbody>
</table>

物理寄存器不能在结果刚写完时立即释放。

它必须等到新的映射安全提交后，旧物理寄存器才可以回收。

核心规则：

```text
当同一架构寄存器的新写入提交后，旧物理寄存器才能释放。
```

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-74.webp)

---

### 5.4 物理寄存器管理

物理寄存器管理主要依靠三个结构：

<table>
<thead>
  <tr>
    <th>
      结构
    </th>
    
    <th>
      作用
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      Rename Table
    </td>
    
    <td>
      记录架构寄存器当前对应哪个物理寄存器
    </td>
  </tr>
  
  <tr>
    <td>
      Free List
    </td>
    
    <td>
      记录哪些物理寄存器可分配
    </td>
  </tr>
  
  <tr>
    <td>
      ROB
    </td>
    
    <td>
      记录指令顺序、提交状态和旧映射信息
    </td>
  </tr>
</tbody>
</table>

重命名一条写寄存器指令时：

```text
从 Free List 取一个新物理寄存器
更新 Rename Table
在 ROB 中记录旧物理寄存器
```

ROB 中通常需要保存：

<table>
<thead>
  <tr>
    <th>
      字段
    </th>
    
    <th>
      含义
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      Rd
    </td>
    
    <td>
      架构目的寄存器
    </td>
  </tr>
  
  <tr>
    <td>
      PRd
    </td>
    
    <td>
      新分配的物理寄存器
    </td>
  </tr>
  
  <tr>
    <td>
      LPRd
    </td>
    
    <td>
      旧的物理寄存器
    </td>
  </tr>
</tbody>
</table>

`LPRd` 的作用是：
等新指令提交后，把旧物理寄存器释放。

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 49.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-75.webp" />
      </p>
    </td>
    
    
      <td style="width: 50.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-76.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 49.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-77.webp" />
      </p>
    </td>
    
    
      <td style="width: 50.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-78.webp" />
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
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-79.webp" />
      </p>
    </td>
    
    
      <td style="width: 49.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-80.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-81.webp)

---

### 5.5 提交时释放旧物理寄存器

假设原来：

```text
x3 → P7
```

现在有一条新指令写 `x3`，重命名为：

```text
x3 → P1
```

此时：

- `P1` 是新值；
- `P7` 是旧值；
- `P7` 不能立刻释放。

只有当写 `x3` 的这条指令顺序提交后，说明新映射已经成为正式状态，`P7` 才能回到 Free List。

核心逻辑是：

```text
执行完成 ≠ 可以释放旧寄存器
顺序提交后才可以释放旧寄存器
```

---

### 5.6 异常时修复重命名状态

如果发生异常或分支预测错误，需要恢复 Rename Table。

常见方法有两类：

<table>
<thead>
  <tr>
    <th>
      方法
    </th>
    
    <th>
      思路
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      逆序恢复
    </td>
    
    <td>
      根据 ROB 中的 PRd / LPRd 反向撤销重命名
    </td>
  </tr>
  
  <tr>
    <td>
      快照恢复
    </td>
    
    <td>
      在分支处保存 Rename Table snapshot，错误时直接恢复
    </td>
  </tr>
</tbody>
</table>

例如：

- MIPS R10K 使用旧映射信息修复 Rename Table；
- Alpha 21264 保存大量 Rename Table 快照，恢复更快。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-82.webp)

---

### 5.7 使用物理 Regfile 的流水线设计

使用 UPRF 后，流水线大致分为：

```text
Fetch → Decode/Rename → Issue → Execute → Commit
```

其中：

- Fetch：按预测 PC 取指；
- Decode/Rename：把架构寄存器转换成物理寄存器；
- Issue：选择源操作数已准备好的指令；
- Execute：功能单元读取 / 写入物理寄存器；
- Commit：按顺序更新架构映射并释放旧寄存器。

关键点是：

```text
执行可以乱序，提交仍然顺序。
```

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-83.webp)

---

### 5.8 超标量寄存器重命名

超标量处理器每周期可能同时重命名多条指令。

这会带来一个额外问题：

```text
同一周期内的指令之间也可能存在 RAW 依赖。
```

例如：

```text
add x1, x2, x3
sub x4, x1, x5
```

如果这两条指令同周期重命名，第二条必须看到第一条刚刚产生的新物理寄存器映射。

因此，超标量重命名需要：

- 同时分配多个物理寄存器；
- 检查同周期指令之间的依赖；
- 保证后面指令使用最新映射；
- 多端口读取 Rename Table 和 Free List。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-84.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-85.webp)

---

## 第五部分总结

统一物理寄存器文件的核心机制是：

```text
架构寄存器重命名为物理寄存器
物理寄存器保存提交值和推测值
ROB 负责顺序提交和旧寄存器释放
```

它的作用是：

- 消除 WAR / WAW 名称依赖；
- 支持更多乱序临时结果；
- 减少 ROB 中的数据移动；
- 提高乱序执行效率；
- 适合超标量处理器。

它的代价是：

- 需要 Rename Table；
- 需要 Free List；
- 需要更多物理寄存器；
- 需要复杂的恢复机制；
- 超标量重命名逻辑更复杂。

---

## 6. 其他优化与注意事项

**Additional Optimization Methods**

### 6.1 ROB 与 Issue Window 分离

ROB 主要负责：

- 保存指令顺序；
- 支持顺序提交；
- 保存异常信息。

Issue Window 主要负责：

- 保存已解码、已重命名、但尚未发射的指令；
- 等待操作数准备；
- 选择可执行指令发射。

所以两者分工不同：

<table>
<thead>
  <tr>
    <th>
      结构
    </th>
    
    <th>
      作用
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      ROB
    </td>
    
    <td>
      保证顺序提交和精确异常
    </td>
  </tr>
  
  <tr>
    <td>
      Issue Window
    </td>
    
    <td>
      负责乱序选择和发射
    </td>
  </tr>
</tbody>
</table>

ROB 通常比 Issue Window 大，因为已发射但未提交的指令仍要留在 ROB 中。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-86.webp)

---

### 6.2 Completion 与 Commit 分离

**Completion** 表示指令执行完成，结果已经算出。
**Commit** 表示结果正式更新体系结构状态。

二者不能混淆：

```text
完成 ≠ 提交
```

这样做的原因是：

乱序执行中，后面的指令可能先完成，但不能先提交，否则会破坏程序语义。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-87.webp)

---

### 6.3 ROB 保存活动指令

ROB 保存所有“已经进入流水线但还没有提交”的指令。

它像一个按程序顺序排列的队列：

```text
较老指令 → 较新指令
Commit 端 → Fetch 端
```

ROB 的作用是：

- 跟踪指令是否完成；
- 保存异常状态；
- 保证提交顺序；
- 支持错误恢复。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-88.webp)

---

### 6.4 发射时序与延迟预测

有些指令可以根据已知延迟提前安排后续发射。

例如，如果知道上一条指令 1 个周期后会产生结果，下一条依赖指令可以提前准备。

但风险是：

```text
如果实际延迟不符合预测，调度会失败。
```

所以延迟可分为三类：

<table>
<thead>
  <tr>
    <th>
      类型
    </th>
    
    <th>
      处理方式
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      固定延迟
    </td>
    
    <td>
      可直接预测
    </td>
  </tr>
  
  <tr>
    <td>
      预测延迟
    </td>
    
    <td>
      先推测，错了恢复
    </td>
  </tr>
  
  <tr>
    <td>
      可变延迟
    </td>
    
    <td>
      等完成信号
    </td>
  </tr>
</tbody>
</table>

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-89.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-90.webp)

---

### 6.5 改进指令获取

乱序处理器后端很强，但前端可能供不上指令。

原因是：

- OoO 需要大量指令填满窗口；
- 推测执行会取很多最终不提交的指令；
- 分支预测错误会清空窗口；
- taken branch 会打断连续取指。

所以高性能 OoO 处理器必须优化 instruction fetch。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-91.webp)

---

### 6.6 提高 taken branch 带宽

taken branch 会让 PC 跳到不连续位置，影响取指连续性。

优化目标是：

```text
尽早预测 taken branch，并尽快取到目标地址的指令。
```

例如 Alpha 21264 通过 I-Cache、BTB、预测机制结合，提高 taken branch 的前端带宽。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-92.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-93.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-94.webp)

---

### 6.7 Branch Address Cache

Branch Address Cache 可以看作扩展版 BTB。

普通 BTB 每次通常预测一个目标。

Branch Address Cache 试图每周期返回多个分支预测结果。

目的：

```text
支持每周期获取多个不连续基本块。
```

这对宽发射超标量处理器很重要。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-95.webp)

---

### 6.8 获取多个基本块

如果每周期要取多条指令，只取一个基本块可能不够。

解决思路是同时取多个基本块，但会带来问题：

- 多端口 cache 成本高；
- cache 交错可能产生 bank conflict；
- 合并多个基本块会增加延迟；
- 错误预测代价更大。

所以这是一种性能和复杂度的权衡。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-96.webp)

---

### 6.9 Trace Cache

Trace Cache 的核心思想是：

```text
把多个不连续的基本块打包成连续的 trace。
```

这样一次取指就可以拿到跨越多个分支的指令序列。

优点：

- 提高前端供给能力；
- 减少 taken branch 对取指的影响。

代价：

- 结构复杂；
- 需要根据分支预测路径组织 trace；
- 预测错误时浪费较大。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-97.webp)

---

### 6.10 Load-Store Queue 设计

控制冒险之后，内存依赖是超标量处理器的重要瓶颈。

问题是：

```text
sd x1, (x2)
ld x3, (x4)
```

Load 能否先执行，取决于它和前面的 Store 是否访问同一地址。

因此需要 Load-Store Queue 处理：

- Load / Store 顺序；
- 地址比较；
- Store-to-Load 转发；
- 地址推测；
- 错误恢复。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-98.webp)

---

### 6.11 推测存储缓冲区

Store 指令不能在提交前直接修改内存。

原因是：

如果这条 Store 后来被取消，内存状态就无法恢复。

所以 Store 结果先进入 Speculative Store Buffer。

Store 通常拆成两部分：

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
      Store Address
    </td>
    
    <td>
      计算写入地址
    </td>
  </tr>
  
  <tr>
    <td>
      Store Data
    </td>
    
    <td>
      准备写入数据
    </td>
  </tr>
</tbody>
</table>

只有到提交点，Store 才能真正写入 D-Cache。

、

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-99.webp)

---

### 6.12 Load bypass

如果 Load 要读取的数据已经在 Store Buffer 中，就不必再从 Cache 读取。

规则是：

```text
如果 Store Buffer 和 Cache 都有数据，优先使用 Store Buffer。
```

如果同一地址有多个较早 Store，则应该使用：

```text
距离该 Load 最近的较早 Store。
```

这就是 Store-to-Load forwarding。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-100.webp)

---

### 6.13 内存依赖与地址推测

Load 是否能越过 Store，关键看地址是否冲突。

保守做法：

```text
如果前面 Store 地址未知，Load 不执行。
```

激进做法：

```text
猜测 Load 和 Store 地址不同，先执行 Load。
```

如果猜错，必须清除 Load 及其后续指令，代价很大。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-101.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-102.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-103.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-104.webp)

---

### 6.14 内存依赖预测

内存依赖预测用于判断某个 Load 是否应该等待前面的 Store。

如果某条 Load 曾经和前面的 Store 冲突，就可以给它标记：

```text
store-wait
```

下次执行时，这条 Load 会等待较早 Store 完成后再执行。

这样可以减少地址推测错误带来的代价。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-105.webp)

---

### 6.15 UPRF 流水线中的指令流

使用统一物理寄存器文件后，指令大致经过：

```text
Fetch → Decode/Rename → Issue → Execute → Commit
```

各阶段作用：

<table>
<thead>
  <tr>
    <th>
      阶段
    </th>
    
    <th>
      作用
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      Fetch
    </td>
    
    <td>
      根据 PC 和分支预测取指
    </td>
  </tr>
  
  <tr>
    <td>
      Decode/Rename
    </td>
    
    <td>
      分配 ROB、Issue Window、物理寄存器
    </td>
  </tr>
  
  <tr>
    <td>
      Issue
    </td>
    
    <td>
      选择操作数准备好的指令
    </td>
  </tr>
  
  <tr>
    <td>
      Execute
    </td>
    
    <td>
      执行并写回物理寄存器
    </td>
  </tr>
  
  <tr>
    <td>
      Commit
    </td>
    
    <td>
      按程序顺序提交
    </td>
  </tr>
</tbody>
</table>

核心仍然是：

```text
前端顺序，执行乱序，提交顺序。
```

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-106.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-107.webp)

---

### 6.16 顺序阶段与乱序阶段对比

不同阶段的顺序性不同。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-108.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-109.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-110.webp)

<table>
<thead>
  <tr>
    <th>
      阶段
    </th>
    
    <th>
      顺序性
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      Fetch
    </td>
    
    <td>
      顺序 / 推测顺序
    </td>
  </tr>
  
  <tr>
    <td>
      Decode
    </td>
    
    <td>
      顺序
    </td>
  </tr>
  
  <tr>
    <td>
      Rename
    </td>
    
    <td>
      顺序
    </td>
  </tr>
  
  <tr>
    <td>
      Dispatch
    </td>
    
    <td>
      顺序
    </td>
  </tr>
  
  <tr>
    <td>
      Issue
    </td>
    
    <td>
      可乱序
    </td>
  </tr>
  
  <tr>
    <td>
      Execute
    </td>
    
    <td>
      可乱序
    </td>
  </tr>
  
  <tr>
    <td>
      Completion
    </td>
    
    <td>
      通常乱序
    </td>
  </tr>
  
  <tr>
    <td>
      Commit
    </td>
    
    <td>
      通常顺序
    </td>
  </tr>
</tbody>
</table>

其中最关键的是：

```text
Issue / Execute 可以乱序；
Commit 必须顺序。
```

这样既能提高性能，又能支持精确异常。

---

### 6.17 顺序提交与乱序提交

现代处理器通常使用顺序提交。

原因是顺序提交可以支持：

- 精确异常；
- 正确恢复；
- 程序语义一致。

早期一些 OoO 机器采用乱序提交，但会产生 imprecise traps。

所以现在主流设计是：

```text
乱序执行 + 顺序提交
```

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-111.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-112.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-113.webp)

---

## 第六部分总结

第六部分主要是在讲：
**一个真正高性能的 OoO 处理器，不能只靠寄存器重命名和 ROB，还要优化前端取指、发射队列、访存队列和提交机制。**

核心机制可以概括为：

```text
ROB 保证顺序提交
Issue Window 提供乱序发射
Branch/Trace 结构提高取指带宽
Load-Store Queue 处理内存依赖
物理寄存器文件保存乱序结果
```

---

## 7. 伯克利 BOOM

**Berkeley BOOM**

### 7.1 开源 Berkeley RISC-V 处理器体系

Berkeley 的 RISC-V 处理器包括多个层次：

<table>
<thead>
  <tr>
    <th>
      处理器
    </th>
    
    <th>
      特点
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      Sodor
    </td>
    
    <td>
      教学用，简单，不可综合
    </td>
  </tr>
  
  <tr>
    <td>
      Z-scale
    </td>
    
    <td>
      RV32IM，微控制器
    </td>
  </tr>
  
  <tr>
    <td>
      Rocket
    </td>
    
    <td>
      RV64G，顺序单发射处理器
    </td>
  </tr>
  
  <tr>
    <td>
      BOOM
    </td>
    
    <td>
      RV64G，乱序超标量处理器
    </td>
  </tr>
</tbody>
</table>

BOOM 是其中面向高性能 OoO 研究的平台。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-114.webp)

---

### 7.2 什么是 BOOM

BOOM 是一个：

- RISC-V 处理器；
- 超标量处理器；
- 乱序处理器；
- 可综合处理器；
- 可参数化处理器；
- 开源处理器。

简单理解：

```text
BOOM = 开源的 RISC-V OoO Superscalar Processor
```

它的作用不是只做教学演示，而是作为真实架构研究平台。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-115.webp)

---

### 7.3 Chisel

BOOM 使用 Chisel 编写。

Chisel 是嵌入在 Scala 中的硬件构造语言。

它的特点是：

- 不是传统高级综合；
- 用 Scala 数据结构描述硬件；
- 支持面向对象和函数式编程；
- 可以生成 Verilog；
- 使用 FIRRTL 作为中间表示。

核心意义是：

```text
Chisel 让 BOOM 不只是一个固定处理器，而是一个可生成、可配置的处理器设计。
```

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-116.webp)

---

### 7.4 BOOM Pipeline

BOOM 的流水线可以分成两部分：

```text
前半部分：顺序
后半部分：乱序
```

大致流程是：

```text
Fetch → Decode/Rename → Issue Window → Functional Units → Commit
```

其中关键结构包括：

- Rename Map Table；
- Free List；
- Issue Window；
- ROB；
- Unified Physical Register File；
- Functional Units。

这和前面课程主线一致：

```text
前端顺序取指和重命名
后端乱序发射和执行
最后顺序提交
```

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-117.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-118.webp)

---

### 7.5 参数化超标量处理器

BOOM 可以通过参数改变处理器结构，例如：

- 发射宽度；
- ALU 数量；
- 是否有 FPU；
- 是否有乘除法单元；
- 是否有 Load / Store Unit；
- bypass 网络；
- 寄存器读写端口数量。

所以 BOOM 不是单一固定架构，而是可以生成不同规模的 OoO 处理器。

例如可以配置成：

```text
dual-issue
quad-issue
不同数量的执行单元
不同规模的寄存器文件
```

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-119.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-120.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-121.webp)

---

### 7.6 功能单元设计

BOOM 把功能单元抽象出来。

功能单元可以是：

<table>
<thead>
  <tr>
    <th>
      类型
    </th>
    
    <th>
      例子
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      流水线单元
    </td>
    
    <td>
      ALU、FPU
    </td>
  </tr>
  
  <tr>
    <td>
      非流水线单元
    </td>
    
    <td>
      除法器、部分长延迟单元
    </td>
  </tr>
  
  <tr>
    <td>
      访存单元
    </td>
    
    <td>
      LSU / MemAddrCalc
    </td>
  </tr>
  
  <tr>
    <td>
      分支相关单元
    </td>
    
    <td>
      Branch Unit
    </td>
  </tr>
</tbody>
</table>

抽象功能单元负责统一处理：

- 输入输出接口；
- 流水线 / 非流水线差异；
- 分支解析；
- branch kill；
- 存储元数据。

这样不同功能单元可以更方便地接入 OoO 框架。

---

### 7.7 可综合与面积 / 性能结果

BOOM 是可综合的，可以用于：

- ASIC；
- FPGA；
- 架构研究；
- 性能与面积评估。

课件中展示了 BOOM 与 ARM Cortex-A9 的比较。重点不是记具体数字，而是说明：

```text
BOOM 作为开源 OoO RISC-V 处理器，已经可以进行接近真实芯片级别的面积和性能评估。
```

这说明 BOOM 不只是模拟器，而是有实际硬件实现价值。、

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-122.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-123.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-124.webp)

---

### 7.8 Load / Store Unit

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-125.webp)

BOOM 的 LSU 负责处理内存指令。

它需要解决：

- Load 地址计算；
- Store 地址计算；
- Store 数据保存；
- Store-to-Load forwarding；
- 地址冲突检测；
- TLB miss；
- page fault；
- load retry；
- branch kill。

LSU 的核心问题是：

```text
Load 能不能越过前面的 Store 执行？
```

如果地址不冲突，可以提高性能；

如果判断错误，就需要回滚或重试。

所以 LSU 是 OoO 处理器中最复杂的部分之一。

---

### 7.9 Repositories 与 Quick Start

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-126.webp)

课件给出了 BOOM 和 Rocket-chip 的代码组织：

<table>
<thead>
  <tr>
    <th>
      仓库
    </th>
    
    <th>
      作用
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      riscv-boom
    </td>
    
    <td>
      BOOM core 本身
    </td>
  </tr>
  
  <tr>
    <td>
      rocket-chip
    </td>
    
    <td>
      SoC 生成框架和相关组件
    </td>
  </tr>
  
  <tr>
    <td>
      riscv-tools
    </td>
    
    <td>
      工具链和测试支持
    </td>
  </tr>
</tbody>
</table>

Quick Start 的核心流程是：

```text
下载 rocket-chip
启用 BOOM
初始化子模块
编译并运行 riscv-tests
```

这部分主要告诉我们：

BOOM 是一个可以实际下载、配置、运行和测试的开源项目。

---

### 7.10 验证与调试

BOOM 参数化程度高，因此验证比较困难。

常用测试包括：

- riscv-tests；
- CoreMark；
- SPEC；
- Linux；
- riscv-torture。

其中 riscv-torture 会随机生成测试程序，对处理器进行压力测试。

基本方法是：

```text
同一程序分别在 Spike 和 BOOM 上运行
比较最终体系结构状态
如果不同，说明可能有 bug
```

此外，BOOM 还支持 commit logging，用于比较每条提交指令的行为。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-127.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-128.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-129.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-130.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-131.webp)

---

### 7.11 BOOM 小结

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L13-14-ComplexPipeline-132.webp)

BOOM 的意义在于：

它把本章前面讲的复杂 OoO 结构落到了真实处理器中。

可以把 BOOM 理解为：

```text
RISC-V ISA
+ 超标量取指与发射
+ 寄存器重命名
+ Issue Window
+ ROB
+ 统一物理寄存器文件
+ Load/Store Queue
+ 顺序提交
= BOOM OoO Processor
```

---

## 第七部分总结

第七部分不是继续引入新的抽象理论，而是用 BOOM 做一个工程化例子。

它说明：

```text
前面讲的 OoO 机制不是孤立概念，
而是可以组合成一个真实的开源超标量乱序处理器。
```
