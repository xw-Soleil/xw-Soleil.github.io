# L6a：单周期处理器设计

> RV32I 单周期数据通路的搭建，从 ADD/ADDI 到 Load/Store 与分支指令的电路实现

## 单周期处理器总体特点

- 每一时钟周期执行一条指令
- 寄存器输出当前状态作为组合逻辑的输入
- 组合逻辑的输出状态值在下一个时钟边缘之前稳定
- 在时钟上升边缘，所有的状态元素都用组合逻辑输出进行更新

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L6a-SingleCycle-01.webp)

### RV32I ISA 需要的状态

处理器执行指令时，必须保存和更新哪些东西，主要有三类状态，包括寄存器文件，程序计数器和存储器状态。

每条指令在执行过程中读取并更新这个状态。

#### Registers（x0..x31）

寄存器文件（regfile）中有 32 个 Registers：Reg<span>

0

</span>

..Reg<span>

31

</span>

，每个register有32bit。

- 根据指令中的 rs1 字段读取第一个寄存器
- 根据指令中的 rs2 字段读取第二个寄存器
- 根据指令中 rd 字段写入目标寄存器
- x0 始终为 0（对 Reg<span>

0

</span>

 的写入将被忽略）

#### 程序计数器（Program Counter, PC）

保存当前指令的地址

#### 存储器（MEM）

- 在一个 32 位字节寻址的内存空间中保存指令和数据
- 我们将为指令和数据使用单独的内存，稍后我们将用指令缓存（ICache）和数据缓存（DCache）来替换
- 从指令内存中读取指令（假设 IMEM 是只读的）
- 加载/存储指令访问数据内存

### 指令执行的基本阶段

单周期处理器中，取指，译码，执行，访存和写回在一个周期内完成。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L6a-SingleCycle-02.webp)

## 单周期 RISC-V 数据通路设计

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L6a-SingleCycle-03.webp)

### 实现 ADD 指令

指令中`inst[6:0]`表示ADD属于R-Type指令，`inst[14:12]`和`inst[30]`表示要进行加法运算。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L6a-SingleCycle-04.webp)

#### ADD 数据通路

PC 先给出当前指令地址，送到 IMEM <mark>

取出指令

</mark>

 `inst[31:0]`。之后进行<mark>

译码操作

</mark>

，`inst[19:15]` 是 `rs1`，用来指定第一个源寄存器；`inst[24:20]` 是 `rs2`，指定第二个源寄存器；`inst[11:7]` 是 `rd`，指定最终写回的目标寄存器。这对应于ADD的指令格式。

寄存器文件根据 `rs1` 和 `rs2` 读出两个数据，分别从 `DataA` 和 `DataB` 输出，送入 ALU。ALU <mark>

执行

</mark>

加法，结果送回到寄存器文件的 `DataD` 输入端。此时控制逻辑会让 `RegWEn` 有效，将结果<mark>

写入

</mark>

指定的`rd`。

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 52.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L6a-SingleCycle-05.webp" />
      </p>
    </td>
    
    
      <td style="width: 47.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L6a-SingleCycle-06.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

#### SUB 的指令格式

减法和加法的指令格式几乎一样，只有`inst[30]`不同，决定了执行减法。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L6a-SingleCycle-07.webp)

#### SUB 数据通路

减法的数据通路和加法基本相同，主要是控制逻辑给ALU的控制信号不同：此时要控制ALU进行减法运算。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L6a-SingleCycle-08.webp)

#### 其他R型指令

数据通路主要区别在于：通过解码**funct3和funct7字段**并选择相应的**ALU函数**实现。

> funct3=`inst[14:12]`, funct7=`inst[31:25]`

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L6a-SingleCycle-09.webp)

### 实现 ADDI 指令

ADDI指令的格式和ADD指令格式的区别在于：`inst[31:20]`在ADDI指令中表示立即数。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L6a-SingleCycle-10.webp)

#### ADDI 数据通路

ADDI的数据通路（左图）和ADD的数据通路（右图）进行比较可以发现：

ADDI的数据路径多了一个**立即数生成器**以及一个加在寄存器文件输出的**多路选择器**。

**立即数生成器**的作用是从指令 `inst[31:20]` 中取出 12 位立即数，并把它符号扩展成 32 位。

ALU 的第一个输入仍然来自 `Reg[rs1]`。ALU 的**第二个输入**：通过一个 MUX 选择。如果是 R 型的指令，ALU 第二个输入选择 `Reg[rs2]`；如果是 I 型指令，ALU 第二个输入选择立即数`imm[31:0]`。

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 50.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L6a-SingleCycle-11.webp" />
      </p>
    </td>
    
    
      <td style="width: 49.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L6a-SingleCycle-12.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

上述数据通路也适用于所有其他I格式的算术指令(slti,sltiu,andi,ori,xori,slli,srli,srai) 只需要通过改变ALUSel

### 实现 Load Word 指令

指令中 opcode`inst[6:0]`表示Load Word属于I-Type指令，`inst[14:12]`表示要进行load操作。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L6a-SingleCycle-13.webp)

#### Load Word 数据通路

处理器先用 **PC** 到 **IMEM** 取出指令，同时 PC 通过 `+4` 计算下一条指令地址；指令译码后，`rs1` 作为基址寄存器被读出，`imm` 经过 **ImmGen** 符号扩展。接着 ALU 不再做普通寄存器加法，而是把 `Reg[rs1] + imm` 相加，得到数据内存 **DMEM** 的访问地址。DMEM 根据这个地址读出内存中的 word，最后通过右侧写回选择器选择 **mem 数据**，写回到 `rd` 寄存器中。

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 56.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L6a-SingleCycle-14.webp" />
      </p>
    </td>
    
    
      <td style="width: 43.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L6a-SingleCycle-15.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

#### 其他读指令

其他读指令的主要区别在于 funct3 字段，其中funct3字段表示不同的加载数据的**大小和符号。**

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L6a-SingleCycle-16.webp)

> 支持**更窄的数据加载**需要**额外的电路**，从内存加载的值中提取正确的字节/半字，并在写入寄存器文件之前将结果**扩展到32位**。

### 实现 Store Word 指令

**rs1**：基址寄存器，用来提供**内存基地址**。

**rs2**：要被存入内存的**数据来源**。

**imm**：偏移量，要和 `x2` 的值相加得到最终内存地址。

**funct3**：表示这是 **SW，存一个 word，也就是 32 位**。

**opcode = 0100011**：表示这是 STORE 类型指令。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L6a-SingleCycle-17.webp)

#### SW 数据通路

**SW 数据通路**表示执行 `sw rs2, imm(rs1)` 时，数据不是写回寄存器，而是写入 **数据内存 DMEM**。

处理器先用 **PC** 从 IMEM 取出指令，同时计算 `PC + 4` 作为下一条指令地址；然后从寄存器堆中读出 **rs1** 和 **rs2**，其中 `rs1` 是基址寄存器，`rs2` 是要存入内存的数据。立即数生成器 **ImmGen** 把 S 格式中分散的立即数字段拼接并符号扩展，ALU 计算 `Reg[rs1] + imm` 得到内存地址。最后，DMEM 以 ALU 输出作为地址，把 `Reg[rs2]` 的值写入该地址；因为 SW 只写内存，所以 **不会写回 rd，RegWEn 不开启**。

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 50.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L6a-SingleCycle-18.webp" />
      </p>
    </td>
    
    
      <td style="width: 49.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L6a-SingleCycle-19.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

#### S型和I型立即数比较

**I型**指令的 12 位立即数是连续放在指令的高 12 位：`inst[31:20] → imm[11:0]`，然后根据最高位 `inst[31]` 做符号扩展，变成 32 位立即数。

**S型**立即数被拆成两段：`inst[31:25] → imm[11:5]；inst[11:7] → imm[4:0]`，执行时要把这两段重新拼起来，再符号扩展成 32 位立即数。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L6a-SingleCycle-20.webp)

硬件实现上，只需要一个**5位的多路选择器**来在两个位置之间进行选择，其中低5位 的立即数可以驻留在指令中。立即数中的其他位被连接到指令中的固定位置

### 实现分支指令

**B格式**与**S格式**指令基本相同，有两个源寄存器 (rs1/rs2)和一个12 位立即数。

但是现在立即数以**2字节**的增量表示**-4096到+4094**之间的值，12位立即数可以编码**13位有符号字节**偏移量(偏移量的最低位总是零，所以不需要存储它)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L6a-SingleCycle-21.webp)

#### 分支数据通路

处理器先用 **PC** 从 IMEM 取出分支指令，同时仍然计算 `PC + 4`。然后寄存器堆读出 `rs1` 和 `rs2`，送入 **Branch Comparator** 比较，判断两者是否相等、大小关系等。同时，**ImmGen** 生成分支偏移量，ALU 选择 `PC + imm` 计算出分支目标地址。最后控制逻辑根据比较结果决定是否跳转：如果分支成立，`PCSel` 选择 `PC + imm`；如果不成立，选择 `PC + 4` 继续执行下一条指令。

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 51.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L6a-SingleCycle-22.webp" />
      </p>
    </td>
    
    
      <td style="width: 48.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L6a-SingleCycle-23.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

#### 分支比较器

分支比较器就是判断 rs1 和 rs2 的关系，输出结果给控制器，让控制器决定分支是否成立。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L6a-SingleCycle-24.webp)

#### 分支立即数表示

分支指令的立即数表示的是 **PC 相对偏移量**，而且偏移量一定是 **2 字节的倍数**，所以最低位永远是 `0`。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L6a-SingleCycle-25.webp)

**12位立即数**以2字节的倍数编码PC相关的偏移：从-4096到 +4094字节

> 12 位有符号数本来范围是：`-2048 ~ +2047`，但分支偏移量单位是 **2 字节**，所以实际字节偏移要乘以 2，所以范围就是 **-4096 到 +4094 字节**

##### 标准硬件实现方法

立即处理为范围`-2048..+2047`，然后左移1位。

但是这样存在弊端：同一套 **ImmGen** 要同时支持 S 型和 B 型立即数。这样会导致很多输出位都可能来自两个不同位置，所以几乎每一位都要加一个 **2 路选择器 mux** 来选择，硬件更复杂、面积更大、延迟也更高。

##### RISC-V 的实现方法

RISC-V的方法不是在硬件里把立即数整体左移 1 位，而是在指令格式设计时，就把大部分分支立即数的 bit 放到左移后应该在的位置。

其中只有`inst[7]`对应在立即数中的位置在S和B之间发生改变，在B格式中`inst[0]`可以直接固定为1，因此基本只需要一个单bit位的选择器针对`inst[7]`bit位进行选择即可。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L6a-SingleCycle-26.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L6a-SingleCycle-27.webp)

### 实现 JALR 指令

**JALR** 指令格式属于**I 型**指令，其作用是：**跳转到一个由寄存器计算出来的地址，同时保存返回地址。**

注意 JALR 的立即数和普通 I 型、load 指令一样，**不需要乘以 2**；它**直接**作为字节偏移量使用。

- **imm11:0**：12 位立即数，也就是偏移量 offset。
- **rs1**：基址寄存器，提供跳转的基础地址，需要计算**Regrs1 + immediate**作为**PC跳转地址**。
- **funct3 = 000**：表示这是 JALR 类型中的固定功能编码。
- **rd**：目标寄存器，用来保存返回地址 `PC + 4`。
- **opcode**：表示这是 JALR 指令。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L6a-SingleCycle-28.webp)

#### JALR 数据通路

执行 `jalr rd, imm(rs1)` 时，处理器先用 **PC** 从 IMEM 取指，同时算出 **PC + 4**。然后从寄存器堆读出 `rs1`，ImmGen 生成 I 型立即数 `imm`，ALU 计算：**Reg[rs1] + imm**。这个结果送回 PC，作为新的跳转地址。与此同时，刚才算出的 **PC + 4** 会通过写回选择器写入 `rd`，作为返回地址。

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 49.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L6a-SingleCycle-29.webp" />
      </p>
    </td>
    
    
      <td style="width: 50.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L6a-SingleCycle-30.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

### 实现J格式的跳跃指令

**JAL（Jump and link）**表示跳转并保存返回地址。JAL的作用是把 `PC + 4` 写入 `rd`，作为返回地址。把 PC 改成 `PC + offset`，跳到目标位置。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L6a-SingleCycle-31.webp)

<alert type="tip">

##### **JAL 和 JALR 的****跳转****区别：**

**JAL 是 PC 相对跳转**，目标地址由 `PC + offset` 得到，不需要读寄存器。
**JALR 是寄存器间接跳转**，目标地址由 `Reg[rs1] + imm` 得到，需要读 `rs1`，JALR 跳转更**灵活**。

</alert>

<alert type="tip">

##### **JAL 和 JALR 的****立即数****区别：**

**JALR 的立即数**是普通 **I 型立即数**：直接取 `inst[31:20]` 这连续 12 位，符号扩展后使用。它表示的是 `Reg[rs1] + imm` 里的偏移量，**不乘 2**，和 `ADDI`、`LW` 的立即数类似。

**JAL 的立即数**是 **J 型立即数**：不是连续放置的，而是分散在指令不同位置，取出后重新拼接，并且最低位默认是 `0`，所以偏移量按 **2 字节对齐**。它用于计算 `PC + offset`，属于 PC 相对跳转。

</alert>

#### JAL 数据通路

执行 `jal rd, offset` 时，处理器先用 **PC** 从 IMEM 取指，同时计算 **PC + 4**。然后 ImmGen 按 **J 型立即数**生成 `offset`，ALU 选择 **PC** 和 **offset** 相加，得到跳转目标地址：**PC + offset**。这个 ALU 结果送回 PC，作为下一条要执行的指令地址；同时 **PC + 4** 通过写回选择器写入 `rd`，作为返回地址。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L6a-SingleCycle-32.webp)

**JAL** 和 **JALR** 的数据通路主要区别是：**JAL 的跳转地址 = PC + offset，不需要读 rs1；JALR 的跳转地址 = Regrs1 + imm，需要读寄存器 rs1。**

### 实现高立即数(Upper Immediate)指令

主要包含两条指令**LUI 和 AUIPC**，**LUI** 是用来加载高位立即数，**AUIPC** 是将高位立即数加到PC。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L6a-SingleCycle-33.webp)

#### LUI 数据通路

执行时，处理器先从 IMEM 取出指令，ImmGen 根据指令生成 U 型立即数；这个立即数经过 ALU 通路送到写回选择器，最后写入 `rd`。LUI 不需要读 `rs1/rs2`，也不访问 DMEM，同时 PC 正常更新为 `PC + 4`。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L6a-SingleCycle-34.webp)

#### AUIPC 数据通路

执行时，PC 一条路径用于取指并计算 `PC + 4`，另一条路径被送入 ALU；ImmGen 生成 U 型立即数，也送入 ALU。ALU 计算 `PC + imm`，结果通过写回选择器写入 `rd`，PC 仍然正常更新为 `PC + 4`。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L6a-SingleCycle-35.webp)

**LUI 和 AUIPC 数据通路的区别**：LUI 写入的是**高立即数本身**；AUIPC 写入的是 **PC + 立即数**。

## 单周期 RISC-V 控制器设计

处理器设计可以分为**数据路径(datapath)**和**控制路径(control)**， 前者用于**存储数字和计算算术操作**，后者用于对数据路径上的操作进行**排序**。本节要设计的就是下图中的**控制逻辑**部分。

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 42.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L6a-SingleCycle-36.webp" />
      </p>
    </td>
    
    
      <td style="width: 57.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L6a-SingleCycle-37.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

<mark>

**控制逻辑实现**

</mark>

<mark>

有两种方法：

</mark>

<mark>

**ROM**

</mark>

 <mark>

和

</mark>

 <mark>

**组合逻辑。**

</mark>



**ROM / 微程序控制方式：**把“某条指令应该产生哪些控制信号”提前存进 ROM。执行时用指令编码去查表，ROM 输出对应的控制信号。优点是结构规则、容易修改错误或增加指令；早期手工设计控制逻辑时很常见。

**组合逻辑 / 硬布线控制方式：**直接把指令字段经过译码，生成各种控制信号，比如 `RegWEn`、`ImmSel`、`ALUSel`、`MemRW`、`WBSel` 等。现代芯片设计通常用逻辑综合工具，把真值表转换成门级电路。

### 控制逻辑真值表（不完整）

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L6a-SingleCycle-38.webp)

### 基于ROM的控制器设计

控制器的输入输出端口如右下图，根据用输入的 11 位地址进入 **Address Decoder**，译码器选中 ROM 里的某一行。每一行提前存好一条“控制字”，例如：`add` 对应 add 的控制信号，`sub` 对应 sub 的控制信号等等。选中ROM中的某一行，就输出提前存好的所有控制信号给数据通路。

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 49.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L6a-SingleCycle-39.webp" />
      </p>
    </td>
    
    
      <td style="width: 50.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L6a-SingleCycle-40.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

#### 微码控制器 | Microcoded CPU

主存 **Main Memory** 里存的是用户程序，也就是普通机器指令，比如 x86、RISC-V 指令，这些叫 **宏指令 macroinstructions**。

CPU 取出一条指令后，不是直接用一个组合逻辑一次性产生所有控制信号，而是把这条指令交给 **Microcode ROM**。Microcode ROM 里存着很多更底层的小步骤，也就是 **微指令 microinstructions**。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L6a-SingleCycle-41.webp)

> **执行过程**：主存中的机器指令 → 取出 opcode → 微码ROM查对应微指令 → 输出控制线控制 datapath → 根据 condition / busy 决定下一条微指令

<alert type="tip">

#### 微码设计的详细讲解内容在 L6b microcode 这一章节可以结合起来看。

</alert>

##### 控制器使用 **Microcode ROM** 大小

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



![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L6a-SingleCycle-42.webp)

**单总线Microcoded RISC-V ROM大小**

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

#### IBM 360中的微编程例子

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 50.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L6a-SingleCycle-43.webp" />
      </p>
    </td>
    
    
      <td style="width: 49.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L6a-SingleCycle-44.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

#### 六七十年代微编程发展

当时微编程流行，是因为 ROM 比 DRAM 快，而且复杂指令集用微码实现更便宜、更容易。比如增加浮点指令，可以通过改微码支持，不一定要大改数据通路。微码还方便修复控制器 bug，也容易保持不同机器之间的 ISA 兼容。

但后来问题出现了：指令集越来越复杂，微码里甚至需要子程序和调用栈；同时 ROM 是只读的，不方便修改，所以出现了 **WCS，可写控制存储**。WCS 允许修改微码，但又带来工具支持差、空间小、上下文切换贵、保护困难等问题。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L6a-SingleCycle-45.webp)

##### 微码机器的CPI

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L6a-SingleCycle-46.webp)

##### 微编程的改进

随着 IC 技术演变，逻辑、RAM、ROM 都逐渐用 MOS 晶体管实现，RAM 和 ROM 的速度差距变小。这样一来，早期“ROM 很快，所以适合做控制器”的优势就减弱了。

**纳型编码 nanocode**的思想是：微码中很多控制信号组合会重复出现，所以不要每条微指令都完整存一大串控制信号，而是把常见控制信号组合放到另一个 ROM 里，再由微码去索引它。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L6a-SingleCycle-47.webp)

##### 从CISC到RISC

因为快速 RAM 可以做指令缓存，简单 ISA 更适合硬连线流水线实现。编译器也变好了，很多复杂 CISC 指令其实很少被用到，所以不如设计简单、规则、容易流水线化的指令集，因此简单硬连线的 RISC 设计逐渐更有优势。

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 43.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L6a-SingleCycle-48.webp" />
      </p>
    </td>
    
    
      <td style="width: 56.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L6a-SingleCycle-49.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

## 处理器性能

以ADD指令执行过程为例进行分析

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 50.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L6a-SingleCycle-50.webp" />
      </p>
    </td>
    
    
      <td style="width: 49.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L6a-SingleCycle-51.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

### 关键路径

ADD指令执行的关键路径时间：<span className="katex">
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

q

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

I

</mi>

<mi>

M

</mi>

<mi>

E

</mi>

<mi>

M

</mi>
</mrow>
</msub>

<mo>

+

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

<mrow>
<msub>
<mi>

t

</mi>

<mrow>
<mi>

R

</mi>

<mi>

e

</mi>

<mi>

g

</mi>
</mrow>
</msub>

<mo separator="true">

,

</mo>

<msub>
<mi>

t

</mi>

<mrow>
<mi>

I

</mi>

<mi>

m

</mi>

<mi>

m

</mi>
</mrow>
</msub>
</mrow>

<mo>

+

</mo>

<msub>
<mi>

t

</mi>

<mrow>
<mi>

A

</mi>

<mi>

L

</mi>

<mi>

U

</mi>
</mrow>
</msub>

<mo>

+

</mo>

<mn>

2

</mn>

<msub>
<mi>

t

</mi>

<mrow>
<mi>

m

</mi>

<mi>

u

</mi>

<mi>

x

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

S

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

t_{clk−q}+t_{IMEM}+max{t_{Reg},t_{Imm}}+t_{ALU}+2t_{mux}+t_{Setup}

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

<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

q

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
<span className="mord,mathnormal,mtight" style="margin-right:0.0785em;">

I

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.109em;">

M

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

E

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.109em;">

M

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

<span className="mord,mathnormal">

ma

</span>

<span className="mord,mathnormal">

x

</span>

<span className="mord">
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
<span className="mord,mathnormal,mtight" style="margin-right:0.0077em;">

R

</span>

<span className="mord,mathnormal,mtight">

e

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

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



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
<span className="mord,mathnormal,mtight" style="margin-right:0.0785em;">

I

</span>

<span className="mord,mathnormal,mtight">

mm

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
<span className="mord,mathnormal,mtight">

A

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.109em;">

LU

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
<span className="strut" style="height:0.7944em;vertical-align:-0.15em;">



</span>

<span className="mord">

2

</span>

<span className="mord">
<span className="mord,mathnormal">

t

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

m

</span>

<span className="mord,mathnormal,mtight">

ux

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
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

S

</span>

<span className="mord,mathnormal,mtight">

e

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



![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L6a-SingleCycle-52.webp)

### 指令执行时间

单周期CPU虽然CPI=1，但时钟周期被最慢指令 lw 限制，导致很多较短指令也必须等完整的 800 ps，硬件模块大部分时间会空闲。

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 46.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L6a-SingleCycle-53.webp" />
      </p>
    </td>
    
    
      <td style="width: 53.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L6a-SingleCycle-54.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

### 处理器性能的“Iron Law”

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mtext>

程序运行时间

</mtext>

<mo>

=

</mo>

<mtext>

指令数

</mtext>

<mo>

×

</mo>

<mi>

C

</mi>

<mi>

P

</mi>

<mi>

I

</mi>

<mo>

×

</mo>

<mtext>

时钟周期时间

</mtext>
</mrow>

<annotation encoding="application/x-tex">

程序运行时间=指令数×CPI×时钟周期时间

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6833em;">



</span>

<span className="mord,cjk_fallback">

程序运行时间

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

<span className="mord,cjk_fallback">

指令数

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
<span className="strut" style="height:0.7667em;vertical-align:-0.0833em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

P

</span>

<span className="mord,mathnormal" style="margin-right:0.0785em;">

I

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

<span className="mord,cjk_fallback">

时钟周期时间

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
<mtext>

即

</mtext>

<mfrac>
<mrow>
<mi>

T

</mi>

<mi>

i

</mi>

<mi>

m

</mi>

<mi>

e

</mi>
</mrow>

<mrow>
<mi>

P

</mi>

<mi>

r

</mi>

<mi>

o

</mi>

<mi>

g

</mi>

<mi>

r

</mi>

<mi>

a

</mi>

<mi>

m

</mi>
</mrow>
</mfrac>

<mo>

=

</mo>

<mfrac>
<mrow>
<mi>

I

</mi>

<mi>

n

</mi>

<mi>

s

</mi>

<mi>

t

</mi>

<mi>

r

</mi>

<mi>

u

</mi>

<mi>

c

</mi>

<mi>

t

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

<mi>

s

</mi>
</mrow>

<mrow>
<mi>

P

</mi>

<mi>

r

</mi>

<mi>

o

</mi>

<mi>

g

</mi>

<mi>

r

</mi>

<mi>

a

</mi>

<mi>

m

</mi>
</mrow>
</mfrac>

<mo>

×

</mo>

<mfrac>
<mrow>
<mi>

C

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

<mi>

s

</mi>
</mrow>

<mrow>
<mi>

I

</mi>

<mi>

n

</mi>

<mi>

s

</mi>

<mi>

t

</mi>

<mi>

r

</mi>

<mi>

u

</mi>

<mi>

c

</mi>

<mi>

t

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
</mrow>
</mfrac>

<mo>

×

</mo>

<mfrac>
<mrow>
<mi>

T

</mi>

<mi>

i

</mi>

<mi>

m

</mi>

<mi>

e

</mi>
</mrow>

<mrow>
<mi>

C

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
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

即 \frac{Time}{Program}=\frac{Instructions}{Program}×\frac{Cycles}{Instruction}×\frac{Time}{Cycle}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:2.2408em;vertical-align:-0.8804em;">



</span>

<span className="mord,cjk_fallback">

即

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

<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal">

o

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

g

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal">

am

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

<span className="mord,mathnormal">

im

</span>

<span className="mord,mathnormal">

e

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.8804em;">
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
<span className="strut" style="height:2.2408em;vertical-align:-0.8804em;">



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

<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal">

o

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

g

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal">

am

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
<span className="mord,mathnormal" style="margin-right:0.0785em;">

I

</span>

<span className="mord,mathnormal">

n

</span>

<span className="mord,mathnormal">

s

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal">

u

</span>

<span className="mord,mathnormal">

c

</span>

<span className="mord,mathnormal">

t

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

<span className="mord,mathnormal">

s

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.8804em;">
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

×

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:2.0574em;vertical-align:-0.686em;">



</span>

<span className="mord">
<span className="mopen,nulldelimiter">



</span>

<span className="mfrac">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:1.3714em;">
<span style="top:-2.314em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0785em;">

I

</span>

<span className="mord,mathnormal">

n

</span>

<span className="mord,mathnormal">

s

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal">

u

</span>

<span className="mord,mathnormal">

c

</span>

<span className="mord,mathnormal">

t

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
<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

</span>

<span className="mord,mathnormal">

c

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

es

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

×

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:2.2408em;vertical-align:-0.8804em;">



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
<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

y

</span>

<span className="mord,mathnormal">

c

</span>

<span className="mord,mathnormal" style="margin-right:0.0197em;">

l

</span>

<span className="mord,mathnormal">

e

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

<span className="mord,mathnormal">

im

</span>

<span className="mord,mathnormal">

e

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.8804em;">
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

- 每个程序的**指令数**取决于：任务、算法、源代码、编程语言、编译器和指令集架构 ISA。
- 每指令周期数 **CPI** 取决于 ISA 和微架构，如：单周期 RISC-V 设计的**CPI = 1**；复杂指令，例如 `strcpy`的**CPI >> 1；**超标量处理器的**CPI < 1。**
- 每个**周期的时间**取决于微架构和工艺技术。

#### 速度权衡示例

尽管处理器B执行了更多的指令，并且具有较低的时钟速率，但 对于这个任务，处理器B更快!

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L6a-SingleCycle-55.webp)

### 处理器能耗的“Iron Law”

简单来说，一个程序/任务消耗的总能量 = 指令数 × 每条指令消耗的能量，即下面式子：

<span className="katex-display">
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<semantics>
<mrow>
<mfrac>
<mtext>

Energy

</mtext>

<mtext>

Program

</mtext>
</mfrac>

<mo>

=

</mo>

<mfrac>
<mtext>

Instructions

</mtext>

<mtext>

Program

</mtext>
</mfrac>

<mo>

×

</mo>

<mfrac>
<mtext>

Energy

</mtext>

<mtext>

Instruction

</mtext>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

\frac{\text{Energy}}{\text{Program}} = \frac{\text{Instructions}}{\text{Program}} \times \frac{\text{Energy}}{\text{Instruction}}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:2.2408em;vertical-align:-0.8804em;">



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
<span className="mord,text">
<span className="mord">

Program

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

<span style="top:-3.677em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord,text">
<span className="mord">

Energy

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
<span className="vlist" style="height:0.8804em;">
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
<span className="strut" style="height:2.2408em;vertical-align:-0.8804em;">



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
<span className="mord,text">
<span className="mord">

Program

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

<span style="top:-3.677em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord,text">
<span className="mord">

Instructions

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
<span className="vlist" style="height:0.8804em;">
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

×

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:2.0463em;vertical-align:-0.686em;">



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
<span className="mord,text">
<span className="mord">

Instruction

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

<span style="top:-3.677em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="mord">
<span className="mord,text">
<span className="mord">

Energy

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
</span>
</span>
</span>
</span>

一个程序消耗的总能量正比于**指令数，电容和电压**：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mfrac>
<mtext>

Energy

</mtext>

<mtext>

Program

</mtext>
</mfrac>

<mo>

∝

</mo>

<mfrac>
<mtext>

Instructions

</mtext>

<mtext>

Program

</mtext>
</mfrac>

<mo>

×

</mo>

<mi>

C

</mi>

<msup>
<mi>

V

</mi>

<mn>

2

</mn>
</msup>
</mrow>

<annotation encoding="application/x-tex">

\frac{\text{Energy}}{\text{Program}} \propto \frac{\text{Instructions}}{\text{Program}} \times C V^2

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.4055em;vertical-align:-0.4811em;">



</span>

<span className="mord">
<span className="mopen,nulldelimiter">



</span>

<span className="mfrac">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.9244em;">
<span style="top:-2.655em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,text,mtight">
<span className="mord,mtight">

Program

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
<span className="mord,text,mtight">
<span className="mord,mtight">

Energy

</span>
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

∝

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1.3534em;vertical-align:-0.4811em;">



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
<span className="mord,text,mtight">
<span className="mord,mtight">

Program

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

<span style="top:-3.394em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,text,mtight">
<span className="mord,mtight">

Instructions

</span>
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

×

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8141em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.2222em;">

V

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

2

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



#### 能耗权衡的例子

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L6a-SingleCycle-56.webp)

电容C降低15%，即0.85C；电压V降低15%，即0.85C。

又<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mfrac>
<mtext>

Energy

</mtext>

<mtext>

Program

</mtext>
</mfrac>

<mo>

∝

</mo>

<mi>

C

</mi>

<msup>
<mi>

V

</mi>

<mn>

2

</mn>
</msup>
</mrow>

<annotation encoding="application/x-tex">

\frac{\text{Energy}}{\text{Program}} \propto C V^2

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.4055em;vertical-align:-0.4811em;">



</span>

<span className="mord">
<span className="mopen,nulldelimiter">



</span>

<span className="mfrac">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.9244em;">
<span style="top:-2.655em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,text,mtight">
<span className="mord,mtight">

Program

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
<span className="mord,text,mtight">
<span className="mord,mtight">

Energy

</span>
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

∝

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8141em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.2222em;">

V

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

2

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

，所以新能耗大约是：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mn>

0.85

</mn>

<mo>

×

</mo>

<msup>
<mn>

0.85

</mn>

<mn>

2

</mn>
</msup>

<mo>

=

</mo>

<msup>
<mn>

0.85

</mn>

<mn>

3

</mn>
</msup>

<mo>

≈

</mo>

<mn>

0.614

</mn>
</mrow>

<annotation encoding="application/x-tex">

0.85 \times 0.85^2 = 0.85^3 \approx 0.614

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.7278em;vertical-align:-0.0833em;">



</span>

<span className="mord">

0.85

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
<span className="strut" style="height:0.8141em;">



</span>

<span className="mord">

0.8

</span>

<span className="mord">
<span className="mord">

5

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

2

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
<span className="strut" style="height:0.8141em;">



</span>

<span className="mord">

0.8

</span>

<span className="mord">
<span className="mord">

5

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

3

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

≈

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.6444em;">



</span>

<span className="mord">

0.614

</span>
</span>
</span>
</span>



也就是原来的 **61.4%**，能耗降低约**39%。**

#### 能耗关键性

能耗效率 Energy efficiency，例如 instructions/Joule，是所有计算设备的关键指标。

对于功率有限的系统，例如 20MW 数据中心，需要更好的能耗效率，以在相同功率下获得更好的性能。

对于能耗有限的系统，例如 1W 的手机，需要更好的能耗效率来延长电池寿命。
