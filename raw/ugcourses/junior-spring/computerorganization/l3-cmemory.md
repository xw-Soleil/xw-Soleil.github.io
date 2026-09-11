# L3：C 语言与内存模型

> C 的编译与解释、寄存器与内存布局、指针与数组、栈与堆内存管理笔记

> 这一章的整体难度不大，但很杂乱，有很多要记的小点，可以放在看其他章节累的时候看。
> 
> 大部分例题的详细推导过程已经放在里面了，如果会做就可以不用看冗杂的推导过程了

## 章节一览

<table>
<thead>
  <tr>
    <th>
      学习块
    </th>
    
    <th>
      页码
    </th>
    
    <th>
      学什么
    </th>
    
    <th>
      学完要能做到
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      1. C 与编译地基
    </td>
    
    <td>
      p3–24
    </td>
    
    <td>
      编译/解释、C 基本类型、<code code="sizeof">
        sizeof
      </code>
      
      、函数、结构体、未初始化变量
    </td>
    
    <td>
      能说清 C 为什么快、为什么和机器相关；能解释未初始化变量为什么危险
    </td>
  </tr>
  
  <tr>
    <td>
      2. 指针入门
    </td>
    
    <td>
      p25–36
    </td>
    
    <td>
      地址和值、<code code="&">
        &
      </code>
      
      、<code code="*">
        *
      </code>
      
      、指针类型、<code code="void *">
        void *
      </code>
      
      、结构体指针、指针作函数参数
    </td>
    
    <td>
      看到一段指针代码，能手推变量最终值
    </td>
  </tr>
  
  <tr>
    <td>
      3. 数组与指针关系
    </td>
    
    <td>
      p37–59
    </td>
    
    <td>
      数组越界、<code code="sizeof(array)">
        sizeof(array)
      </code>
      
       vs <code code="sizeof(pointer)">
        sizeof(pointer)
      </code>
      
      、数组名/指针对偶性、指针运算
    </td>
    
    <td>
      能解释 <code code="a[i] == *(a+i)">
        a[i] == *(a+i)
      </code>
      
      ，知道数组传参会丢失长度
    </td>
  </tr>
  
  <tr>
    <td>
      4. C 内存布局
    </td>
    
    <td>
      p60–84
    </td>
    
    <td>
      code/static/stack/heap，<code code="malloc/free/realloc">
        malloc/free/realloc
      </code>
      
      ，谁申请谁释放
    </td>
    
    <td>
      能画出一个程序中变量分别在栈、堆、静态区哪里
    </td>
  </tr>
  
  <tr>
    <td>
      5. 常见内存错误
    </td>
    
    <td>
      p85–96，p103–118
    </td>
    
    <td>
      越界、野指针、非法 <code code="free">
        free
      </code>
      
      、重复 <code code="free">
        free
      </code>
      
      、内存泄漏、返回栈地址
    </td>
    
    <td>
      能把错误分类：越界 / 泄漏 / 非法释放 / use-after-free / 返回局部地址
    </td>
  </tr>
  
  <tr>
    <td>
      6. 残酷现实与性能
    </td>
    
    <td>
      p97–102
    </td>
    
    <td>
      性能不只看复杂度，内存访问模式影响巨大，局部性
    </td>
    
    <td>
      能解释为什么同样复制二维数组，循环顺序不同性能差很多
    </td>
  </tr>
</tbody>
</table>

---

## 一：编译与解释

### p4：抽象表示 Levels of Representation

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L3-CMemory-01.webp)

课件从上到下给了几个层次：

<table>
<thead>
  <tr>
    <th>
      层次
    </th>
    
    <th>
      例子
    </th>
    
    <th>
      你该怎么理解
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      高级语言
    </td>
    
    <td>
      C 代码：<code code="temp = v[k];">
        temp = v[k];
      </code>
    </td>
    
    <td>
      人比较容易读
    </td>
  </tr>
  
  <tr>
    <td>
      汇编语言
    </td>
    
    <td>
      RISC-V：<code code="lw">
        lw
      </code>
      
      , <code code="sw">
        sw
      </code>
    </td>
    
    <td>
      接近机器，但还能看懂
    </td>
  </tr>
  
  <tr>
    <td>
      机器语言
    </td>
    
    <td>
      一串 0/1
    </td>
    
    <td>
      CPU 真正能执行
    </td>
  </tr>
  
  <tr>
    <td>
      硬件结构
    </td>
    
    <td>
      Register File, ALU
    </td>
    
    <td>
      机器码最终驱动硬件
    </td>
  </tr>
  
  <tr>
    <td>
      逻辑电路
    </td>
    
    <td>
      门电路图
    </td>
    
    <td>
      最底层实现
    </td>
  </tr>
</tbody>
</table>

**任何东西都可以用数字表示，包括数据和指令**

> C 代码为什么不能直接被 CPU 执行？

CPU 只能执行机器码，高级语言必须经过编译、汇编、链接等过程变成机器码。

---

### p5：程序员必须关心硬件吗？

需考虑

性能、功耗、安全；

内存管理和线程管理。

---

### p6：Hello World：C 和 Java 对比

<table>
<thead>
  <tr>
    <th>
      语言
    </th>
    
    <th>
      运行前发生什么
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      C
    </td>
    
    <td>
      编译成机器码可执行文件
    </td>
  </tr>
  
  <tr>
    <td>
      Java
    </td>
    
    <td>
      编译成字节码，再由 JVM 运行
    </td>
  </tr>
  
  <tr>
    <td>
      Python
    </td>
    
    <td>
      通常由解释器运行源码或中间表示
    </td>
  </tr>
</tbody>
</table>

---

### p7：C 编译概述

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L3-CMemory-02.webp)

<table>
<thead>
  <tr>
    <th>
      文件
    </th>
    
    <th>
      含义
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      <code code=".c">
        .c
      </code>
    </td>
    
    <td>
      C 源代码，文本
    </td>
  </tr>
  
  <tr>
    <td>
      <code code=".o">
        .o
      </code>
    </td>
    
    <td>
      object file，已经翻译成机器相关代码、但尚未完成地址解析和库连接的中间产物
    </td>
  </tr>
  
  <tr>
    <td>
      <code code="lib.o">
        lib.o
      </code>
      
       或库文件
    </td>
    
    <td>
      别人提前编译好的机器码
    </td>
  </tr>
  
  <tr>
    <td>
      <code code="a.out">
        a.out
      </code>
    </td>
    
    <td>
      最终可执行文件
    </td>
  </tr>
</tbody>
</table>

所以“编译”严格讲不止一步。常见流程是：

```text
预处理 → 编译 → 汇编 → 链接 → 可执行文件
```

```text
main.c
  │
  ├─ 预处理：展开 #include、#define
  │
  ├─ 编译：C 代码 → 汇编代码
  │
  ├─ 汇编：汇编代码 → main.o
  │
  └─ 链接：main.o + 其他 .o + 库 → 可执行文件
```

多个 `.c` 文件可以分别编译成 `.o`，最后由 linker 和库文件一起链接成可执行文件。

---

### p8：编译 vs 解释

C：

```text
源代码 → 编译器/链接器 → 机器语言 → OS 加载 → 硬件直接执行
```

Python：

```text
解释器本身是由高级语言编写，翻译成机器码程序
解释器读取 Python 源代码
解释器边读边解释执行
```

一个小细节很关键：
Python 不是“CPU 直接看懂 Python”。CPU 执行的是 Python 解释器这个程序，解释器再去处理你的 Python 代码。

<table>
<thead>
  <tr>
    <th>
      项目
    </th>
    
    <th>
      C
    </th>
    
    <th>
      Python
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      翻译时机
    </td>
    
    <td>
      运行前
    </td>
    
    <td>
      运行时
    </td>
  </tr>
  
  <tr>
    <td>
      执行者
    </td>
    
    <td>
      硬件直接执行机器码
    </td>
    
    <td>
      解释器读代码并执行
    </td>
  </tr>
  
  <tr>
    <td>
      性能
    </td>
    
    <td>
      通常更快
    </td>
    
    <td>
      通常有解释开销
    </td>
  </tr>
</tbody>
</table>

<alert type="tip">

C 由编译器和链接器翻译成机器语言，再由操作系统加载、硬件执行

Python 则由解释器读取源代码并“解释”它。

</alert>

---

### p9：Java 字节码

Java 是中间路线。流程大概是：

```text
.java 源代码
   ↓ javac
.class 字节码
   ↓ JVM
解释执行 / JIT 编译成本地机器码
```

Java 字节码是<mark>

平台无关

</mark>

的中间表示，是一种抽象的汇编语言，不是某个真实 CPU 的机器码。实际运行中由 JVM 解释执行，或者用 JIT 把热点代码动态编译成本地机器码。

你可以把 Java 理解成：

> 先编译成 JVM 能看懂的代码，再由 JVM 想办法让真实机器执行。

这也是 Java “一次编写，到处运行”的基础。（与c语言不同，同一套 C 代码在不同指令集架构下会编译出不同的机器码）

---

### p10：编译的优点

核心：**运行时性能好。**

因为 C 代码已经提前变成了机器码，所以运行时 CPU 可以直接执行，不需要解释器一边读源代码一边处理。

计算机只运行机器代码；编译型语言预先形成可执行文件，运行时直接由硬件执行，而解释型语言运行时转换会有额外开销。

---

### p11：编译优化例子——乘以 12

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L3-CMemory-03.webp)

编译器会自动把某些算术改写成更适合机器执行的 shift/add 组合。

> 编译器不是逐字翻译，它会优化。

---

### p12-13：无/有符号除以 8

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 55.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L3-CMemory-04.webp" />
      </p>
    </td>
    
    
      <td style="width: 44.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L3-CMemory-05.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

#### 无符号

```c
unsigned long udiv8(unsigned long x) {
    return x / 8;
}
```

编译后可以变成逻辑右移：

```c
return x >> 3;
```

---

#### 有符号

**负数除法不能简单右移完事。**

```c
long idiv8(long x) {
    return x / 8;
}
```

编译器会做类似逻辑：

```c
if (x < 0)
    x += 7;
return x >> 3;
```

为什么负数要先 `+7`？
因为 C 的整数除法通常是向 0 截断，而算术右移对负数更像向负无穷取整。为了让结果符合 C 语义，编译器要修正一下。

例子：

```text
-9 / 8 = -1   // C 语言向 0 截断
-9 >> 3 可能得到 -2
```

> 编译器优化算术时，必须保持 C 语言语义。无符号和有符号处理方式不同。

课件 p13 也明确区分了有符号除法使用算术移位，并在负数情况下先加偏移再右移。

---

### p14：编译的缺点

编译不是全是优点。缺点主要两个：

第一，**可执行文件依赖体系结构和操作系统**。
比如 RISC-V、ARM、x86 不一样；Windows、Linux 也不一样。

第二，**开发迭代可能慢**。
你改一点代码，可能要重新编译再运行。课件 p14 提到，可执行文件是 architecture-specific 和 operating-system-specific；换新系统时通常要重新生成可执行文件，也就是所谓“移植”。

工具 `make` 的作用就是自动化“哪些文件改了，哪些需要重新编译”。

<alert type="tip">

C特点：运行快，但编译和移植成本更明显。

</alert>

---

### p15：C 预处理器 CPP

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L3-CMemory-06.webp)

C 源文件在真正编译前，会先经过预处理器 CPP。

CPP命令一般以“#”开头

常见预处理命令：

```c
#include <stdio.h>
#include "file.h"
#define M_PI (3.14159)
#if
#endif
```

> 预处理发生在编译之前，它处理的是文本层面的东西。

---

### p16：C 语言中的变量

C 变量特点：

1. 使用前要定义；
2. 类型不能随便变；
3. 和 Java 有点像，是静态类型语言。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L3-CMemory-07.webp)

---

### p17：常量和枚举

#### 常量：

```c
const float pi = 3.1415;
const unsigned long addr = 0xaf460;
```

`const` 表示这个变量初始化后不能再改。

#### 枚举：

```c
typedef enum { red, green, blue } Color;
Color pants = green;
```

枚举的作用是：给一组相关取值起名字。
比如颜色、状态、错误码。

你可以这样理解：

```c
enum { red, green, blue };
```

底层通常对应整数：

```text
red = 0
green = 1
blue = 2
```

但写名字比写 0、1、2 更清楚。

本页记忆点：

> `const` 是“这个值别改”；`enum` 是“给一组整数状态起名字”。

---

### p18：整数：Python、Java、C

这一页讲不同语言里的整数大小。

<table>
<thead>
  <tr>
    <th>
      语言
    </th>
    
    <th>
      <code code="int">
        int
      </code>
      
       大小特点
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      Python
    </td>
    
    <td>
      普通整数至少够用，长整数可近似无限精度
    </td>
  </tr>
  
  <tr>
    <td>
      Java
    </td>
    
    <td>
      <code code="int">
        int
      </code>
      
       固定 32 bits
    </td>
  </tr>
  
  <tr>
    <td>
      C
    </td>
    
    <td>
      由机器和编译器决定，可能 16/32/64 bits
    </td>
  </tr>
</tbody>
</table>

课件还给了 C 的保证关系：

```c
sizeof(long long) >= sizeof(long) >= sizeof(int) >= sizeof(short)
```

int在不同指令集不同微架构的位数不一样

C （int）的工作效率最高但有可移植性问题。

---

### p19：变量长度依赖机器

给了某台机器上的 `sizeof` 输出：

```text
char: 1
short: 2
int: 4
unsigned int: 4
long: 8
long long: 8
float: 4
double: 8
```

---

### p20：布尔 Boolean

1. 老式 C 里没有内置 `boolean` 类型。课件给了一种写法：

```c
typedef int boolean;
const boolean false = 0;
const boolean true = 1;
```

1. C 的真假规则：

<table>
<thead>
  <tr>
    <th>
      值
    </th>
    
    <th>
      在 C 中的真假
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      <code code="0">
        0
      </code>
    </td>
    
    <td>
      false
    </td>
  </tr>
  
  <tr>
    <td>
      <code code="NULL">
        NULL
      </code>
    </td>
    
    <td>
      false
    </td>
  </tr>
  
  <tr>
    <td>
      非 0
    </td>
    
    <td>
      true
    </td>
  </tr>
</tbody>
</table>

C 中 false 是 0 或 NULL，其他“不是假的东西都是真的”。

---

### p21：C 语言中的函数

```c
int number_of_people() {
    return 3;
}

void news() {
    printf("no news");
}

int sum(int x, int y) {
    return x + y;
}
```

C 函数像 Java

- 需要声明返回类型和参数类型
- 无返回值用 `void`
- 函数使用前必须声明。

---

### p22：未初始化变量

```c
void undefined_local() {
    int x;  // undefined
    printf("x = %d\n", x);
}
```

未初始化的变量可能为任意值

<mark>

所以申明变量之后一定要初始化

</mark>



---

### p23：结构体 Struct

Struct 是一组结构化变量

例子：

```c
typedef struct {
    int x, y;
} Point;

Point p1;
p1.x = 0;
p1.y = 123;

Point p2 = {77, -8};
printf("p2 at (%d,%d)\n", p2.x, p2.y);
```

它有点像 Java 类，但没有方法

---

### p24：小结

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L3-CMemory-08.webp)

---

## 第二章：指针和地址

这一段你要抓住一条主线：**变量不只是“值”，变量还住在内存的某个“地址”；指针就是专门存地址的变量。** 课件第 25–36 页围绕“指针和地址”展开，包括内存地址、`&`、`*`、指针类型、`void *`、结构体指针、函数参数传递和两道练习题。

---

### p26：计算机组件

这一页是一张计算机组成图。左边是处理器，右边是存储器，中间有地址、读写使能、写数据、读数据这些信号。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L3-CMemory-09.webp)

处理器里主要有：

<table>
<thead>
  <tr>
    <th>
      部件
    </th>
    
    <th>
      作用
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      Controller 控制单元
    </td>
    
    <td>
      决定当前要执行什么操作
    </td>
  </tr>
  
  <tr>
    <td>
      Data Path 数据通路
    </td>
    
    <td>
      真正搬运和处理数据
    </td>
  </tr>
  
  <tr>
    <td>
      PC 程序计数器
    </td>
    
    <td>
      保存下一条指令的地址
    </td>
  </tr>
  
  <tr>
    <td>
      Registers 寄存器
    </td>
    
    <td>
      CPU 内部很快的小存储
    </td>
  </tr>
  
  <tr>
    <td>
      ALU
    </td>
    
    <td>
      做算术和逻辑运算
    </td>
  </tr>
</tbody>
</table>

存储器里放两类东西：

```text
Program 程序
Data 数据
```

注意，这一页最重要的是 **Address 地址线**。

处理器要访问内存时，不是喊一句“我要变量 a”，而是给内存一个地址：

所以，后面 C 里的指针，其实就是把这种“地址”暴露给程序员。

> 处理器通过地址访问内存；变量名是给人看的，机器真正用的是地址。

---

### p27：计算机内存——地址和值不要混

这里一定要区分两件事：

<table>
<thead>
  <tr>
    <th>
      概念
    </th>
    
    <th>
      对应什么
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      <code code="a">
        a
      </code>
      
       的值
    </td>
    
    <td>
      <code code="-85">
        -85
      </code>
    </td>
  </tr>
  
  <tr>
    <td>
      <code code="a">
        a
      </code>
      
       的地址
    </td>
    
    <td>
      <code code="a">
        a
      </code>
      
       在内存中的位置，比如 <code code="0x7fff...">
        0x7fff...
      </code>
    </td>
  </tr>
  
  <tr>
    <td>
      <code code="&a">
        &a
      </code>
    </td>
    
    <td>
      取出 <code code="a">
        a
      </code>
      
       的地址
    </td>
  </tr>
</tbody>
</table>

```c
printf("%d", a);
```

打印的是 **值**。

而如果写：

```c
printf("%p", &a);
```

打印的是 **地址**。

<mark>

不要混淆内存地址 address 和值 value。

</mark>



---

### p28：指针 Pointers

这页正式定义指针：

> 指针是 C 语言中表示内存地址的东西。

课件给的代码大概是：

```c
int *x;      // x 是一个指向 int 的指针
int y = 9;   // y 是一个 int

x = &y;      // 把 y 的地址赋给 x
int z = *x;  // 把 x 指向的值(9)赋给 z

*x = -7;     // 把 x 指向的东西（y）改成 -7
```

这里有两个核心操作符。

<table>
<thead>
  <tr>
    <th>
      操作符
    </th>
    
    <th>
      名字
    </th>
    
    <th>
      意思
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      <code code="&">
        &
      </code>
    </td>
    
    <td>
      address operator 取地址
    </td>
    
    <td>
      <code code="&y">
        &y
      </code>
      
       表示 y 的地址
    </td>
  </tr>
  
  <tr>
    <td>
      <code code="*">
        *
      </code>
    </td>
    
    <td>
      dereference 解引用
    </td>
    
    <td>
      <code code="*x">
        *x
      </code>
      
       表示 x 指向的那个变量
    </td>
  </tr>
</tbody>
</table>

最终结果：

```text
x = &y      // x 存着 y 的地址
y = -7
z = 9
```

注意这个细节：`z` 不会跟着变成 -7。
因为 `z = *x;` 是把当时的值复制了一份给 `z`，不是让 `z` 也指向 `y`。

---

### p29：指针类型 Pointer Type

这一页说：指针也有类型。

```c
int *pi;      // 指向 int 的指针
double *pd;   // 指向 double 的指针
char *pc;     // 指向 char 的指针
```

原因是：**编译器需要知道你通过这个地址一次要读多少字节，以及怎么解释这些字节。**

---

### p30：通用指针 void *

这一页讲 `void *`。

```c
void *vp;
```

1. `void *` 是“通用指针”，意思是：

> 它可以保存任意类型对象的地址，但它不知道这个地址上到底是什么类型。

比如它可以接收：

```c
int a = 3;
double d = 1.5;

void *vp;

vp = &a;
vp = &d;
```

1. 但是问题来了：
因为 `void *` 不知道自己指向的对象大小和类型，所以你不能直接这样安全地用：

```c
*vp
```

1. `void *` 的典型用途是通用函数，尤其是内存分配相关函数，比如：

```c
malloc
free
```

因为 `malloc` 只是申请一块内存，它不知道你准备用这块内存放 `int`、`double` 还是结构体，所以它返回的是 `void *`。

```text
int *    ：我指向 int
double * ：我指向 double
char *   ：我指向 char
void *   ：我只知道我是地址，但不知道指向什么
```

---

### p31：指向结构体的指针 Pointer to struct

代码大概是：

```c
typedef struct {
    int x, y;
} Point;

Point pt = {0, 5};

Point *pt_ptr = &pt;
```

这里：

```text
pt 是一个 Point 结构体变量
pt_ptr 是一个指向 Point 的指针
pt_ptr = &pt 表示 pt_ptr 存放 pt 的地址
```

如果要通过指针访问结构体成员，有两种写法。

第一种：

```c
(*pt_ptr).x = (*pt_ptr).y;
```

> 为什么要加括号？
> 
> 因为 `.` 的优先级比 `*` 高。
> 如果你写：
> 
> ```c
> *pt_ptr.x
> ```
> 
> 编译器会先理解成：
> 
> ```c
> *(pt_ptr.x)
> ```
> 
> 但 `pt_ptr` 是指针，不是结构体变量，不能直接 `.x`。
> 
> 所以必须写：
> 
> ```c
> (*pt_ptr).x
> ```

第二种，也是更常用的写法：

```c
pt_ptr->x = pt_ptr->y;
```

`->` 的意思就是：通过结构体指针访问成员

所以最终：

```text
pt.x = 5
pt.y = 5
```

---

### p32：练习题 1——手推指针代码

课件代码是：

```c
#include <stdio.h>

int main(void) {
    int a = 3, b = -7;
    int *pa = &a, *pb = &b;

    *pb = 5;

    if (*pb > *pa)
        a = *pa - b;

    printf("a=%d b=%d\n", a, b);
}
```

#### 答案：

```text
a = -2
b = 5
```

#### 推导过程：

```text
a = 3
b = -7
pa = &a
pb = &b
```

也就是：

```text
*pa == a == 3
*pb == b == -7
```

执行：

```c
*pb = 5;
```

`pb` 指向 `b`，所以 `*pb = 5` 等价于：

```c
b = 5;
```

现在：

```text
a = 3
b = 5
*pa = 3
*pb = 5
```

执行判断：

```c
if (*pb > *pa)
```

也就是：

```c
if (5 > 3)
```

成立。

于是执行：

```c
a = *pa - b;
```

此时 `*pa` 是 `a` 的当前值，也就是 3；`b` 是 5。

所以：

```text
a = 3 - 5 = -2
```

最终：

```text
a = -2
b = 5
```

所以答案是课件表格里的：

```text
YELLOW：a = -2, b = 5
```

这题的核心坑是：

```c
*pb = 5;
```

它改的是 `b`，不是 `pb`。

---

### p33：这个代码有什么问题？

代码是：

```c
#include <stdio.h>

int main(void) {
    int a;
    int *p;

    printf("a = %d, p = %p, *p = %d\n", a, p, *p);

    return 0;
}
```

这段代码问题很大，属于 C 语言经典“死亡三件套”。

第一，`a` 没初始化：

第二，`p` 没初始化：

第三，还解引用了这个垃圾指针*p：

输出垃圾

---

### p34：指针作为函数实参

这一页讲 C 的参数传递机制：<mark>

**默认按值传递**

</mark>

。也就是说，函数收到的是实参的副本；在函数内部修改普通参数，不会影响外面的原变量。要想让函数修改外面的变量，就传指针。课件第 34 页明确强调 <mark>

C 函数参数默认是通过值传递，要通过引用传递则使用指针

</mark>

。

代码：

```c
#include <stdio.h>

void f(int x, int *p) {
    x = 5;
    *p = -9;
}

int main(void) {
    int a = 1, b = -3;

    f(a, &b);

    printf("a=%d b=%d\n", a, b);
}
```

#### 答案：

```text
a = 1
b = -9
```

#### 推导过程：

```text
a = 1
b = -3
```

调用：

```c
f(a, &b);
```

对应到函数参数：

```text
x = a 的值 = 1
p = b 的地址 = &b
```

注意：`x` 是 `a` 的副本，不是 `a` 本人。

进入函数：

```c
x = 5;
```

这只改了函数里的局部变量 `x`，不会影响 `a`。

所以：

```text
a 仍然是 1
```

然后：

```c
*p = -9;
```

`p` 指向 `b`，所以 `*p = -9` 等价于：

```c
b = -9;
```

最终：

```text
a = 1
b = -9
```

这页的核心区别：

```c
f(a, b);
```

只能把值传进去。

```c
f(a, &b);
```

把 `b` 的地址传进去，函数就能通过 `*p` 修改 `b`。

口诀：

```text
想让函数改外面的变量，就传它的地址。
```

---

### p35：Java 中的参数传递

这一页拿 Java 和 C 对比。

```text
基本类型 int, char, double：按值传递
对象 Objects：通过引用
```

可以这样对比：

<table>
<thead>
  <tr>
    <th>
      对比项
    </th>
    
    <th>
      C
    </th>
    
    <th>
      Java
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      能否显式取地址
    </td>
    
    <td>
      可以，<code code="&a">
        &a
      </code>
    </td>
    
    <td>
      不可以
    </td>
  </tr>
  
  <tr>
    <td>
      能否显式解引用
    </td>
    
    <td>
      可以，<code code="*p">
        *p
      </code>
    </td>
    
    <td>
      不可以
    </td>
  </tr>
  
  <tr>
    <td>
      指针是否暴露给程序员
    </td>
    
    <td>
      暴露
    </td>
    
    <td>
      隐藏
    </td>
  </tr>
  
  <tr>
    <td>
      对象位置能否由运行时移动
    </td>
    
    <td>
      C 一般不随便移动
    </td>
    
    <td>
      JVM 可以移动对象
    </td>
  </tr>
</tbody>
</table>

这页的核心是：

> C 把地址暴露给你，所以你更自由，也更容易犯错。Java 把地址藏起来，所以更安全，但控制力少一些。

---

### p36：练习题 2——用指针实现交换

代码：

```c
#include <stdio.h>

void foo(int *x, int *y) {
    if (*x < *y) {
        int t = *x;
        *x = *y;
        *y = t;
    }
}

int main(void) {
    int a = 3, b = 1, c = 5;

    foo(&a, &b);
    foo(&b, &c);

    printf("a=%d b=%d\n", a, b);
}
```

#### 答案：

```text
YELLOW：a = 3, b = 5, c = 1
```

#### 推导过程

初始：

```text
a = 3
b = 1
c = 5
```

第一次调用：

```c
foo(&a, &b);
```

所以：

```text
x = &a
y = &b
*x = a = 3
*y = b = 1
```

判断：

```c
if (*x < *y)
```

也就是：

```c
if (3 < 1)
```

不成立，所以不交换。

第一次后：

```text
a = 3
b = 1
c = 5
```

第二次调用：

```c
foo(&b, &c);
```

所以：

```text
x = &b
y = &c
*x = b = 1
*y = c = 5
```

判断：

```c
if (1 < 5)
```

成立，执行交换：

```c
int t = *x;
```

也就是：

```text
t = b = 1
```

然后：

```c
*x = *y;
```

`x` 指向 `b`，`y` 指向 `c`，所以：

```text
b = c = 5
```

最后：

```c
*y = t;
```

也就是：

```text
c = 1
```

最终：

```text
a = 3
b = 5
c = 1
```

所以答案是表格里的：

```text
YELLOW：a = 3, b = 5, c = 1
```

虽然 `printf` 里只打印了 `a` 和 `b`，但如果问三个变量最终值，就是：

```text
a = 3
b = 5
c = 1
```

---

### p25–36 小结

最关键的心法是这句：

```text
p 是地址，*p 是地址里的东西。
```

---

## 第三章：数组、指针与字符串

**p37–59 是“数组和指针绑定在一起”的部分**，主线清楚：

> C 里的数组名很多时候会像指针一样用；数组不记录长度；指针运算按“元素大小”移动；字符串本质上是以 `'\0'` 结尾的 `char` 数组。

课件这一段从 C 数组、越界、`sizeof`、指针运算、数组/指针对偶性，一直讲到字符串、`strlen` 和 `main` 的命令行参数。

---

### p37：C 数组 C Arrays

1. 基本声明

```c
int a[5];
```

也就是说，`a[5]` 只是分配空间，**里面原来是什么值不确定**。如果是局部数组，里面可能是垃圾值。

1. 初始化数组：

```c
int b[] = {3, 2, 1};
```

这里编译器会根据初始化元素数量推断数组长度，所以 `b` 长度是 3。

1. C 数组下标从 0 开始：

```text
b[0] = 3
b[1] = 2
b[2] = 1
```

---

### p38：注意：C 没有数组边界检查

这一页非常重要。

课件例子类似：

```c
int a[] = {1, 2, 3};

for (int i = 0; i < 4; i++)
    printf("a[%d] = %d\n", i, a[i]);
```

数组只有 3 个元素，但循环访问到了第四个

课件给出的输出是：

```text
a[0] = 1
a[1] = 2
a[2] = 3
a[3] = -1870523725
```

这个 `a[3]` 不是数组里的合法元素，而是数组后面某块内存里的“碰巧值”。课件也强调，结果可能更糟：不可预测行为、segmentation fault，而且 C 语言本身不知道数组长度。

C 不会帮你检查数组越界。

Java/Python 越界通常会报错；C 可能不报错，还继续跑，甚至把别的变量改坏。这个是 C 最阴险的地方之一：**错了不一定立刻死，可能以后才炸。**

---

### p39：使用常量，而不是字面量

这页讲写代码习惯。

不好的写法：

```c
int i, ar[10];

for (i = 0; i < 10; i++) {
    ...
}
```

好的写法：

```c
const int ARRAY_SIZE = 10;

int i, a[ARRAY_SIZE];

for (i = 0; i < ARRAY_SIZE; i++) {
    ...
}
```

这样数组长度只有一个来源：

---

### p40：指向不同大小的对象

这一页把 p29 的“指针类型”讲得更底层。

现代机器是 **byte-addressable，字节寻址** 的。意思是：内存里每一个字节都有自己的地址。

但问题是，不同类型占用的字节数不同：

```text
char   通常 1 字节
short  通常 2 字节
int    通常 4 字节
double 通常 8 字节
```

所以：

```c
char *z;
short *y;
int *x;
```

虽然它们本质上都存地址，但编译器通过类型知道：

```text
*z 取 1 个字节
*y 取 2 个字节
*x 取 4 个字节
```

这就是为什么指针类型重要。

> 比如地址 `0x1000`：
> 
> ```c
> char *pc = (char *)0x1000;
> int  *pi = (int  *)0x1000;
> ```
> 
> `pc + 1` 到 `0x1001`，因为 char 一个元素 1 字节。
> `pi + 1` 到 `0x1004`，因为 int 一个元素 4 字节。
> 
> 这一页为 p42、p43 的指针运算做铺垫。

---

### p41：`sizeof()` 操作符

`sizeof` 返回对象或类型占用的字节数。

如果代码里有：

```c
double d;
int array[5];

struct {
    short a;
    char c;
} s;
```

课件例子输出：

```text
double: 8
array: 20
s: 4
```

`sizeof(s)` 是 4，不是 3，这里涉及结构体对齐。`short` 2 字节，`char` 1 字节，但编译器可能为了对齐补 1 字节，所以整个结构体是 4 字节。

<alert type="tip">

struct中的总大小必须是其内部最大对齐要求成员的整数倍

</alert>

C 里定义保证

```text
sizeof(char) == 1
```

其他类型大小取决于硬件和编译器，不要假设，要用 `sizeof`。

你要记住两个常用公式：

```c
sizeof(array)              // 整个数组的字节数，仅在数组还没退化成指针时有效
sizeof(array) / sizeof(array[0])  // 数组元素个数
```

---

### p42：指针运算——字符 char

课件例子是字符数组：

```c
char c[] = {'a', 'b'};
char *pc = c;

pc++;
```

课件输出类似：

```text
*pc = b
c  = 0x...3e
pc = 0x...3f
pc - c = 1
```

注意地址差了 1，因为 `char` 一个元素就是 1 字节。

这里有个很关键的点：

```c
pc - c
```

<mark>

结果是 1，不是单纯地址数值相减的字节数概念，而是“相差几个 char 元素”。对于

</mark>

 <mark>

`char`

</mark>

<mark>

，刚好一个元素就是 1 字节，所以看起来一样。

</mark>



---

### p43：指针运算——整型 int

这一页和 p42 对比。

代码大概是：

```c
int i[] = {10, 20};
int *pi = i;

pi++;
```

课件输出类似：

```text
*pi = 20
i  = 0x...40
pi = 0x...44
pi - i = 1
```

注意地址差了 4，因为 `int` 通常是 4 字节。
但是：

```c
pi - i
```

结果仍然是 1，因为它表示相差 1 个 `int` 元素。

<mark>

所以指针运算的规则是：

</mark>



```text
p + 1 不是地址数值 + 1
而是地址数值 + sizeof(*p)
```

比如：

```text
char *p; p + 1   移动 1 字节
int *p;  p + 1   移动 4 字节，假设 sizeof(int)=4
double *p; p + 1 移动 8 字节，假设 sizeof(double)=8
```

这页非常核心。

---

### p44：数组名 / 指针对偶性

这页是 C 里最经典的一页。

课件说：

> 数组变量是指向第一个，也就是第 0 个元素的指针。

更准确地说：**数组名在大多数表达式中会退化成指向首元素的指针**。

例如：

```c
int a[3] = {10, 20, 30};
```

那么<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

a

</mi>
</mrow>

<annotation encoding="application/x-tex">

a

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.4306em;">



</span>

<span className="mord,mathnormal">

a

</span>
</span>
</span>
</span>

很多时候等价于：

```c
&a[0]
```

所以：

```c
a[0] == *a
a[2] == *(a + 2)
```

但是数组名和真正的指针变量<mark>

还有区别

</mark>

：

```c
char astr[] = "abc";
char *pstr = astr;
```

可以：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

p

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

<mo>

+

</mo>

<mo>

+

</mo>
</mrow>

<annotation encoding="application/x-tex">

pstr++

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8095em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal">

p

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.6667em;vertical-align:-0.0833em;">



</span>

<span className="mord">

+

</span>
</span>
</span>
</span>

;

但不能：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

a

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

<mo>

+

</mo>

<mo>

+

</mo>
</mrow>

<annotation encoding="application/x-tex">

astr++

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6984em;vertical-align:-0.0833em;">



</span>

<span className="mord,mathnormal">

a

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

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.6667em;vertical-align:-0.0833em;">



</span>

<span className="mord">

+

</span>
</span>
</span>
</span>

;

因为 `astr` 是数组名，不是一个可以被修改的指针变量。它像指针用，但不是普通指针变量。

<alert type="tip">

数组名像指针，但是不能随便改

</alert>

---

### p45：数组与指针示例

这一页展示数组表示法和指针表示法可以混用。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L3-CMemory-10.webp)

但课件最后也提醒：**混合指针和数组表示法会让人困惑，避免乱用。**

---

### p46：指针运算 Pointer Arithmetic

课件给出：

```c
int n = 3;
int *p;

p += n;  // adds n * sizeof(int) to p
p -= n;  // subtracts n * sizeof(int) from p
```

> 这个例子隐含的关键前提是：**p** **必须已经指向某个** **int** **数组中的元素**，而且运算结果仍不能越出该数组的合法范围。
> 
> 应当类似这样：
> 
> ```text
> int a[10];
> int *p = &a[2];
> 
> p += 3;   // 现在指向 a[5]
> p -= 3;   // 回到 a[2]
> ```

如果 `sizeof(int) == 4`，那么：

```c
p += 3;
```

实际地址增加：

```text
3 * 4 = 12 字节
```

重点不是“加 3 个字节”，而是“向后移动 3 个 int 元素”。

<mark>

**指针运算仅用于数组。**

</mark>



不要这样：

```c
char *p;
char a, b;

p = &a;
p += 1;
```

你可能以为 `p += 1` 会指向 `b`，但不一定。因为 `a` 和 `b` 不保证在内存里挨着，也不保证顺序。课件也明确说，`p += 1` may point to `b`, or not。

---

### p47：数组和指针：数组传参会丢失大小

数组作为指针传给函数后，<mark>

数组大小丢失

</mark>

，所以要 explicitly pass size

课件说：

```c
a[i] ≡ *(a+i)
```

但是，当数组作为函数参数传递时，会退化成指针。

例如：

```c
int foo(int array[]) {
    ...
}
```

实际上参数里的：

```c
int array[]
```

差不多就是：

```c
int *array
```

所以函数里面不知道数组原本有多长。

因此必须显式传入长度：

```c
int foo(int array[], unsigned int size) {
    return array[size - 1];
}

int main(void) {
    int a[10], b[5];

    foo(a, 10);
    foo(b, 5);
}
```

记住：

```text
C 函数收到数组参数时，收到的是首元素地址，不是整个数组信息。
```

---

### p48：`sizeof(array)` 在函数里为什么变了？

这页是 p47 的实锤例子。

代码结构大概是：

```c
int foo(int array[], unsigned int size) {
    printf("%d\n", sizeof(array));
}

int main(void) {
    int a[10];

    foo(a, 10);
    printf("%d\n", sizeof(a));
}
```

假设：

```text
sizeof(int) == 4
```

在 `main` 里：

```c
sizeof(a)
```

是整个数组大小：

```text
10 * 4 = 40
```

所以输出 40。

但在 `foo` 里：

```c
sizeof(array)
```

这里的 `array` 已经不是原数组了，而是一个指针参数。
在现代 64 位机器上，指针通常是 8 字节，所以输出 8。课件这页也给出 `sizeof(array)` 打印 8，而 `sizeof(a)` 打印 40，并解释函数里的数组实际上是指针。

所以这个坑要背下来：

```c
void foo(int array[]) {
    sizeof(array); // 指针大小，不是数组大小
}
```

不要在函数里用 `sizeof(array)/sizeof(array[0])` 计算数组长度。会错。

---

### p49：用下标遍历数组 vs 用指针遍历数组

课件说这两段代码效果相同。

第一种，下标写法：

```c
int i;
int array[5];

for (i = 0; i < 5; i++) {
    array[i] = ...;
}
```

第二种，指针写法：

```c
int *p;
int array[5];

for (p = array; p < &array[5]; p++) {
    *p = ...;
}
```

```text
array[i] 视角：第 i 个元素
*p 视角：当前指针指向的元素
```

---

### p50：数组末尾之后的指针

这一页讲一个有点反直觉但很常用的规则。

代码：

```c
const int SZ = 10;
int ar[SZ], *p, *q, sum = 0;

p = &ar[0];
q = &ar[SZ];

while (p != q) {
    sum += *p++;
}
```

> ```c
> sum += *p++;
> ```
> 
> 等价于：
> 
> ```c
> sum += *p;
> p = p + 1;
> ```
> 
> 因为后缀 `++` 优先使用当前 `p`，再让 `p` 后移。

问题是：

```c
q = &ar[SZ];
```

合法的吗？

`ar[SZ]` 看起来越界，因为最后一个合法元素是：

```c
ar[SZ - 1]
```

<mark>

但是 C 允许你形成“数组末尾后一个元素”的地址，也就是 one-past-the-end pointer。

</mark>



所以：

```c
&ar[SZ]
```

可以作为边界指针来比较。课件也写明，C 定义数组结束后的一个元素必须是有效地址，不会导致错误。

但千万注意：

```c
q = &ar[SZ];  // 可以
*q           // 不可以
```

也就是：

```text
数组末尾后一个位置可以拿来比较，但不能解引用。
```

<alert type="tip">

优先级
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mo>

∗

</mo>

<mi>

p

</mi>

<mo>

+

</mo>

<mo>

+

</mo>
</mrow>

<annotation encoding="application/x-tex">

*p++

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.7778em;vertical-align:-0.1944em;">



</span>

<span className="mord">

∗

</span>

<span className="mord,mathnormal">

p

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
<span className="strut" style="height:0.6667em;vertical-align:-0.0833em;">



</span>

<span className="mord">

+

</span>
</span>
</span>
</span>

： <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mo>

+

</mo>

<mo>

+

</mo>
</mrow>

<annotation encoding="application/x-tex">

++

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

+

</span>
</span>
</span>
</span>

的优先级更高，所以是指针向后一个单位

<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mo stretchy="false">

(

</mo>

<mo>

∗

</mo>

<mi>

p

</mi>

<mo stretchy="false">

)

</mo>

<mo>

+

</mo>

<mo>

+

</mo>
</mrow>

<annotation encoding="application/x-tex">

(*p)++

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

∗

</span>

<span className="mord,mathnormal">

p

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
<span className="strut" style="height:0.6667em;vertical-align:-0.0833em;">



</span>

<span className="mord">

+

</span>
</span>
</span>
</span>

 ： 是先解引用，然后给p对应的值++

</alert>

---

### p51：有效的指针运算

课件总结哪些指针运算合法。

合法的：

```text
1. 指针 + 整数
2. 指针 - 整数
3. 两个指针相减，但必须指向同一个数组中的元素
4. 比较指针：<, <=, ==, !=, >, >=
5. 指针和 NULL 比较
```

不合法的：

```text
两个指针相加
指针相乘
整数 - 指针
```

---

### p52：指向指针的指针

看一个简单例子：

```c
int x = 10;
int *p = &x;
int **pp = &p;
```

关系是：

```text
x   是 int，值是 10
p   是 int*，存的是 x 的地址
pp  是 int**，存的是 p 的地址
```

> 所以：
> 
> ```c
> *p
> ```
> 
> 是 x。
> 
> ```c
> *pp
> ```
> 
> 是 p。
> 
> ```c
> **pp
> ```
> 
> 是 x。

可以画成：

```text
pp ──> p ──> x ──> 10
```

---

### p53：练习题——`int **pp`

课件代码：

```c
int x[] = {2, 4, 6, 8, 10};

int *p = x;
int **pp = &p;

(*pp)++;
(*(*pp))++;

printf("%d\n", *p);
```

#### 答案：

```text
5
```

#### 推导过程：

初始数组：

```text
x[0] = 2
x[1] = 4
x[2] = 6
x[3] = 8
x[4] = 10
```

执行：

```c
int *p = x;
```

也就是：

```text
p 指向 x[0]
*p = 2
```

执行：

```c
int **pp = &p;
```

也就是：

```text
pp 指向 p
*pp 就是 p
**pp 就是 *p，也就是 x[0]
```

然后：

```c
(*pp)++;
```

这里 `*pp` 就是 `p`，所以这句等价于：

```c
p++;
```

于是：

```text
p 从指向 x[0] 变成指向 x[1]
*p = 4
```

接着：

```c
(*(*pp))++;
```

里面：

```c
*pp
```

是 `p`。

```c
*(*pp)
```

就是 `*p`。

而此时 `p` 指向 `x[1]`，所以：

```c
(*(*pp))++;
```

等价于：

```c
x[1]++;
```

于是：

```text
x[1] 从 4 变成 5
```

最后：

```c
printf("%d\n", *p);
```

此时 `p` 指向 `x[1]`，所以：

```text
*p = 5
```

答案是：

```text
5
```

这一题最容易错在 `(*pp)++`：它不是改数组元素，而是让 `p` 往后移动一个元素。

---

### p54：C 字符串

这一页进入字符串。

<alert type="tip">

课件中可能有错的点
课件中说：

C 字符串是以 NULL 结尾的字符数组。

但实际是：

C 字符串是以 **NUL 字符** **'\0'** 结尾的字符数组

</alert>

> - `'\0'`：**字符常量**，表示数值为 0 的字符，也叫 **NUL 字符**。C 字符串靠它作为结束标记。
> 
> ```text
> char s[] = "abc";   // 实际是 {'a', 'b', 'c', '\0'}
> ```
> 
> - `NULL`：**空指针常量**，表示“不指向任何有效对象”。通常定义为 `0`、`0L` 或 `(void *)0`，具体形式由实现决定。
> 
> ```text
> char *p = NULL;
> ```

例如：

```c
char s[] = "abc";
```

内存里不是只有 3 个字符，而是：

```text
s[0] = 'a'
s[1] = 'b'
s[2] = 'c'
s[3] = '\0'
```

所以：

```c
char s[] = "abc";
```

数组长度其实是 4，不是 3。

这个点超级重要：

```text
字符串长度 strlen(s) 是 3
数组占用字符数是 4，因为还有 '\0'
```

---

### p55：字符串例子

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L3-CMemory-11.webp)

课件输出：

```text
str = abc, length = 3
```

注意：

```text
strlen 不包含 '\0'
sizeof(str) 包含 '\0'
```

那么通常：

```c
strlen(str) == 3
sizeof(str) == 4
```

---

### p56：简洁的 `strlen()`

课件给了一个短小但很 C 的实现：

```c
int strlen(char *s) {
    char *p = s;

    while (*p++)
        ; /* Null body of while */

    return (p - s - 1);
}
```

关键是：

```c
while (*p++)
```

意思是：

```text
先取当前 p 指向的字符作为 while 条件
然后 p 往后移动一格
```

#### 过程详解

假设字符串是：

```text
a b c \0
```

过程：

```text
p 指向 'a'，*p++ 是 'a'，非 0，继续
p 指向 'b'，*p++ 是 'b'，非 0，继续
p 指向 'c'，*p++ 是 'c'，非 0，继续
p 指向 '\0'，*p++ 是 0，循环结束，但 p 已经又往后走了一格（这边涉及one-past-end）
```

所以循环结束时，`p` 指向 `'\0'` 后面的一个位置。

因此：

```c
return (p - s - 1);
```

要减 1，得到真正字符串长度<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mn>

3

</mn>
</mrow>

<annotation encoding="application/x-tex">

3

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6444em;">



</span>

<span className="mord">

3

</span>
</span>
</span>
</span>

。

---

### p57：`main()` 的参数

C 语言里，`main` 函数如何接收**命令行参数**。

```c
int main(int argc, char *argv[])
```

```text
argc 是命令行上的字符串数
argv 是一个指向数组的指针，数组中包含字符串形式的参数
```

更具体一点：

```text
argc = argument count，参数个数
argv = argument vector，参数数组
```

`argv` 是一个数组，里面每个元素都是一个 C 字符串，也就是 `char *`。

所以：

```c
char *argv[]
```

可以理解成：

```text
argv 是一个数组
数组每个元素都是 char *
每个 char * 指向一个字符串
```

---

### p58：命令行参数例子

课件例子：

```bash
gcc -o ex Argc.c
./ex -g a "d e f"
```

输出：

```text
arg[0] = ./ex
arg[1] = -g
arg[2] = a
arg[3] = d e f
```

这里有几个点。

第一，`argv[0]` 通常是程序名或程序路径：

```text
argv[0] = ./ex
```

第二，后面的每个命令行参数都是一个字符串：

```text
argv[1] = "-g"
argv[2] = "a"
argv[3] = "d e f"
```

第三，引号 `"d e f"` 的作用是把带空格的内容作为一个整体参数，而不是拆成三个参数。

所以这个命令里：

```text
argc = 4
```

因为一共有：

```text
./ex
-g
a
d e f
```

四个字符串。

可以用这样的程序打印：

```c
#include <stdio.h>

int main(int argc, char *argv[]) {
    for (int i = 0; i < argc; i++) {
        printf("arg[%d] = %s\n", i, argv[i]);
    }
    return 0;
}
```

---

### p59：小结

这一页总结了 p25–59 的指针部分。

核心有五句话：

```text
1. 指针是 C 语言里的机器内存地址
2. 指针变量保存在内存中，指针值本质上是可被软件操作的数字
3. C 中数组和指针关系非常密切
4. 指针知道它指向对象的类型和大小，void * 除外
5. 指针强大，但如果没有规划，会成为错误的主要来
```

```text
数组与指针
├── 数组
│   ├── 下标从 0 开始
│   ├── 不检查越界
│   └── 不自带长度
├── sizeof
│   ├── 在 main 里 sizeof(a) 是整个数组
│   └── 在函数参数里 sizeof(array) 是指针大小
├── 指针运算
│   ├── p+1 移动 sizeof(*p) 字节
│   ├── 只建议在数组内使用
│   └── one-past-end 可比较，不可解引用
├── 数组/指针对偶
│   ├── a[i] == *(a+i)
│   ├── a 常退化成 &a[0]
│   └── 数组名不能 a++
└── 字符串
    ├── char 数组
    ├── 以 '\0' 结尾
    ├── strlen 不数 '\0'
    └── argv 是字符串数组
```

---

## 第四章：C 内存管理

> **C 程序里的数据放在哪里，决定了它什么时候存在、谁负责释放、能不能安全继续用。**

这部分会讲四块内存：**code、static data、stack、heap**。其中真正危险的是 **heap 堆**，也就是 `malloc/free/realloc` 这一套。

---

### p61：C 内存管理总图

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L3-CMemory-12.webp)

<table>
<thead>
  <tr>
    <th>
      区域
    </th>
    
    <th>
      放什么
    </th>
    
    <th>
      谁管理
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      code
    </td>
    
    <td>
      程序机器指令
    </td>
    
    <td>
      操作系统/编译器
    </td>
  </tr>
  
  <tr>
    <td>
      static data
    </td>
    
    <td>
      全局变量、静态变量
    </td>
    
    <td>
      操作系统/编译器
    </td>
  </tr>
  
  <tr>
    <td>
      stack
    </td>
    
    <td>
      函数参数、局部变量
    </td>
    
    <td>
      自动管理
    </td>
  </tr>
  
  <tr>
    <td>
      heap
    </td>
    
    <td>
      <code code="malloc">
        malloc
      </code>
      
       出来的动态内存
    </td>
    
    <td>
      程序员手动管理
    </td>
  </tr>
</tbody>
</table>

这一页要建立全局地图。后面所有 bug，本质都能归到一句话：

> 你用了已经不属于你的内存，或者忘了释放你申请的内存。

---

### p62：代码区 Code

代码区放的是程序指令。

课件说 code 的特点是：

- 程序启动时加载
- 不会改变

比如你写的：

```c
int main(void) {
    printf("hello\n");
}
```

编译后变成机器指令，运行时这些指令会被加载到 code 区。

这块通常不是你手动操作的。你不会：

```c
free(main);
```

代码区由系统负责，程序员基本不用直接管理。

一句话：

> **code 区放“程序要做什么”，不是放普通运行时数据。**

---

### p63：静态数据区 Static Data

静态数据区放的是程序整个运行期间都存在的数据。

- 程序启动时加载
- 可以修改
- 尺寸是固定的

典型例子：

```c
int global_x = 10;

static int count = 0;
```

这些变量在程序启动时就被安排好空间。课件说 static data 的特点是：

```text
程序启动时加载
可以修改
尺寸固定
```

所以它和 code 区不同：<mark>

code 通常不改，static data 可以改。

</mark>



比如：

```c
int g = 1;

int main(void) {
    g = 2;
}
```

`g` 在静态数据区，程序运行期间一直存在。

但它也不是动态的。你不能运行到一半说“全局变量数组突然变大十倍”，除非你用堆。

一句话：

> **static data 生命周期长，可以修改值，但尺寸固定。**

---

### p64：栈 Stack

- 函数内部的局部变量和参数
- 调用函数时分配
- 栈通常向下增长

例子：

```c
void f(int n) {
    int x = 5;
}
```

这里：

```text
n 是函数参数
x 是局部变量
```

它们都在 `f` 的栈帧里。

<mark>

调用

</mark>

 <mark>

`f`

</mark>

 <mark>

时，栈上开一块空间；

</mark>

<mark>

`f`

</mark>

 <mark>

返回后，这块空间就失效

</mark>

。

这会直接导致 p68 的大坑：**不能返回局部变量的地址。**

---

### p65：栈帧示意图

这一页用代码展示栈帧怎么叠起来：

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L3-CMemory-13.webp)

```c
void a() {
    int a_local = 0;
    b(a_local);
}

int b(int arg) {
    int b_local = 5;
    return 2 * arg + b_local;
}

int main(void) {
    a();
    b(7);
}
```

当 `main` 调用 `a`，`a` 又调用 `b` 时，栈上会有类似：

```text
Frame main
Frame a
Frame b
```

栈指针 Stack Pointer 会随着函数调用和返回移动。

你可以把栈想成一摞盘子：

```text
main 先放上去
a 再压上去
b 再压上去
b 返回，b 的盘子拿掉
a 返回，a 的盘子拿掉
```

<mark>

这就是 LIFO：last in, first out，后进先出。

</mark>



---

### p66：栈帧包含什么

> 栈帧：是一次函数调用在调用栈中占用的一块记录区域

每次调用一个函数(function)，就会分配一个新的帧(frame)

当函数返回时，帧被释放

栈帧包含

- 函数参数(function arguments)
- 局部变量(local variables
- <mark>

返回地址(return address，谁调用我的?)

</mark>

栈使用连续的内存块– 栈指针指示当前堆栈级别

栈管理对C程序员来说是透明的，将在编写汇编语言时看到细节

---

### p67：练习题——递归时有多少份 x 和 y？

代码大概是：

```c
#include <stdio.h>
#include <stdlib.h>

int x = 2;

int foo(int n) {
    int y;
    if (n <= 0) {
        printf("End case!\n");
        return 0;
    } else {
        y = n + foo(n - x);
        return y;
    }
}

int main(void) {
    foo(10);
}
```

问题是：

> 在 `printf` 执行之后，但在返回 0 之前，内存中分配了多少个 `x` 和 `y` 的副本？

#### 答案：

```text
#x = 1
#y = 6
```

#### 推导过程：

先看 `x`：

```c
int x = 2;
```

它是全局变量，在静态数据区。全程序只有一份。

所以：

```text
#x = 1
```

再看 `y`：

```c
int foo(int n) {
    int y;
    ...
}
```

`y` 是 `foo` 的局部变量。每调用一次 `foo`，就有一个新的栈帧，也就有一份新的 `y`。

调用链是：

```text
foo(10)
foo(8)
foo(6)
foo(4)
foo(2)
foo(0)
```

到 `foo(0)` 时满足 `n <= 0`，执行 `printf("End case!\n")`。

问题问的是 **printf 执行之后，但在 return 0 之前**。此时所有递归调用都还没返回，所以栈上还保留着 6 个 `foo` 栈帧。

每个 `foo` 栈帧里都有一个 `y`，即使 `foo(0)` 这一层的 `y` 没真正赋值，它的局部变量空间也已经分配了。

所以：

```text
#x = 1
#y = 6
```

---

### p68：返回局部变量地址——大坑

这一页代码是：

```c
#include <stdio.h>
#include <math.h>

int *f() {
    int x = 5;
    return &x;
}

int main(void) {
    int *a = f();
    double d = cos(1.57);
    printf("a = %d\n", *a);
}
```

问题在这里：

```c
int x = 5;
return &x;
```

`x` 是 `f()` 的局部变量，在 `f` 的栈帧里。

当 `f()` 返回后：

```text
f 的栈帧被释放
x 不再有效
```

但是 `a` 还保存着原来 `x` 的地址。于是：

```c
*a
```

就变成了访问一块已经失效的栈内存。

课件输出是：

```text
a = -1085663214
```

---

### p69：堆 Heap

这一页正式进入堆。

课件说堆是：

- 动态数据空间
- 根据需要由程序分配和释放

这就是 `malloc/free` 的地盘。

和栈相比：

<table>
<thead>
  <tr>
    <th>
      对比
    </th>
    
    <th>
      栈 stack
    </th>
    
    <th>
      堆 heap
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      创建方式
    </td>
    
    <td>
      函数调用自动创建
    </td>
    
    <td>
      <code code="malloc/calloc/realloc">
        malloc/calloc/realloc
      </code>
      
       手动申请
    </td>
  </tr>
  
  <tr>
    <td>
      销毁方式
    </td>
    
    <td>
      函数返回自动销毁
    </td>
    
    <td>
      <code code="free">
        free
      </code>
      
       手动释放
    </td>
  </tr>
  
  <tr>
    <td>
      生命周期
    </td>
    
    <td>
      跟函数调用绑定
    </td>
    
    <td>
      由程序员决定
    </td>
  </tr>
  
  <tr>
    <td>
      常见问题
    </td>
    
    <td>
      返回局部变量地址
    </td>
    
    <td>
      泄漏、重复释放、越界、use-after-free
    </td>
  </tr>
</tbody>
</table>

为什么需要堆？

比如你运行时才知道数组大小：

```c
int n;
scanf("%d", &n);
int *a = malloc(n * sizeof(int));
```

这就是动态对象。

---

### p70：管理堆的 C 函数

课件列了四个核心函数：

```text
malloc()   分配一块未初始化的内存
calloc()   分配一块内存并初始化为 0
free()     释放先前分配的内存块
realloc()  更改先前分配块的大小
```

还特别提醒：

> `realloc()` 之后，以前分配的内容可能会移动。

---

### p71：`malloc()`

原型：

```c
void *malloc(size_t n);
```

- `malloc` 分配一块未初始化的内存，`n` 是请求大小，单位是字节
- `size_t` 是足够大、可以计数字节数的无符号整数类型
- 返回 `void *`
- 如果没有更多内存，返回 `NULL`。

例子：

```c
#include <stdlib.h>

int main(void) {
    int *ip = (int *)malloc(50 * sizeof(int));

    double *dp = malloc(1000 * sizeof(double));
}
```

解释：

```c
malloc(50 * sizeof(int))
```

申请 50 个 `int` 的空间。

如果 `sizeof(int) == 4`，就是：

```text
50 * 4 = 200 字节
```

---

### p72：这段代码有什么问题？

代码是：

```c
#include <stdio.h>
#include <stdlib.h>

int main(void) {
    const int SZ = 10;
    int *p = malloc(SZ * sizeof(int));
    int *end = &p[SZ];

    while (p < end)
        *p++ = 0;

    free(p);
}
```

错误在最后：

```c
free(p);
```

```c
while (p < end)
    *p++ = 0;
```

这里 `p++` 会不断移动 `p`。循环结束时，`p` 已经不再是原来的起始地址了，而是指向数组末尾后一个位置：

```text
p == &原数组[SZ]
```

<mark>

可是

</mark>

 <mark>

`free`

</mark>

 <mark>

要求你传入

</mark>

 <mark>

**malloc 最初返回的地址**

</mark>

<mark>

。

</mark>



现在传的是被改过的 `p`，所以报错：

```text
pointer being freed was not allocated
```

```text
不要把 malloc 返回的“原始句柄”弄丢。
```

---

### p73：`free()`

原型：

```c
void free(void *p);
```

课件强调两点：

- 释放 malloc() 分配的内存
- p 必须包含 malloc() 最初返回的地址

这就是 p72 错误的根源。

合法：

```c
int *p = malloc(10 * sizeof(int));
free(p);
```

非法：

```c
int *p = malloc(10 * sizeof(int));
p++;
free(p);      // 错
```

也非法：

```c
int x;
free(&x);     // 错，x 在栈上，不是 malloc 来的
```

更非法：

```c
int a[5];
free(a);      // 错，a 是栈上数组，不是 malloc 来的
```

这页的金句：

> **free 只认 malloc/calloc/realloc 返回的那块堆内存的起始地址。**

---

### p74：Fix——修复 p72

修复代码是：

```c
#include <stdio.h>
#include <stdlib.h>

int main(void) {
    const int SZ = 10;
    int *array = malloc(SZ * sizeof(int));

    for (int *p = array; p < &array[SZ]; )
        *p++ = 0;

    free(array);
}
```

关键变化是：

```c
int *array = malloc(...);
```

`array` 保存原始地址，不动它。

循环里另开一个指针：

```c
int *p = array;
```

让 `p` 去跑。

最后：

```c
free(array);
```

释放原始地址。

**原始指针用来 free，游标指针用来移动。**

---

### p75：为什么调用 `free()`？

手动回收不再使用的内存，避免内存耗尽

课件对比了两种方式：

<table>
<thead>
  <tr>
    <th>
      方式
    </th>
    
    <th>
      语言
    </th>
    
    <th>
      优点
    </th>
    
    <th>
      缺点
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      <code code="malloc/free">
        malloc/free
      </code>
      
       显式管理
    </td>
    
    <td>
      C/C++
    </td>
    
    <td>
      控制力强
    </td>
    
    <td>
      容易泄漏、访问已释放内存
    </td>
  </tr>
  
  <tr>
    <td>
      垃圾收集 GC
    </td>
    
    <td>
      Java/Python
    </td>
    
    <td>
      自动释放不用的对象
    </td>
    
    <td>
      性能开销、何时释放不可预测
    </td>
  </tr>
</tbody>
</table>

课件也提到，手动管理需要计划：我如何知道内存不再被使用？如果忘记释放怎么办？缺点就是潜在 bug，包括内存泄漏和内存损坏。

你可以这么理解：

```text
C：你负责倒垃圾，忘了就堆满屋子。
Java/Python：有人帮你倒垃圾，但他什么时候进屋不完全由你决定。
```

---

### p76：内存不足

这一页说：

```text
空闲内存不足时，malloc() 返回 NULL
```

```text
malloc 可能失败，失败时返回 NULL。
```

---

### p77：示例——动态分配树

这一页用二叉树说明为什么需要堆。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L3-CMemory-14.webp)

动态数据结构，比如链表、树、图，经常用：

```c
malloc(sizeof(Node))
```

来让节点活在堆上。

---

### p78：`malloc` 和 `free` 是好朋友

- 如果在某个地方调用 malloc，则需要对结果调用 free，或者接受内存泄漏。
- 没有 malloc，就没有 free。

示例：

```c
int *p = malloc(...);

// complicated code

free(p);
```

这叫配对。

但下面这些不能 free：

```c
int x;
int *p = &x;
// do not call free(p)

int a[5];
// do not call free(a)
```

因为 `x` 和 `a` 都不是堆内存，而是在栈上或其他自动/静态区域。课件 p78 明确强调：没调用 `malloc` 就不要调用 `free`，比如不要 `free` 栈变量地址或栈数组。

口诀：

```text
malloc 来的，free 回去。
不是 malloc 来的，别 free。
```

---

### p79：观察——哪块内存最麻烦？

课件总结：

- code 和 static storage 简单：不增长也不缩小，由 OS 负责
- stack 相对简单：栈帧 LIFO 创建和销毁，对程序员透明
- heap 是程序员的任务：可以随时分配/释放，需要规划

```text
code/static：系统管
stack：自动管
heap：你来管
```

---

### p80：`malloc/free` 是如何实现的？

这一页讲底层原理。

课件说：底层操作系统允许 `malloc` 库请求堆中的大块内存，例如 Unix 的 `sbrk()`；

C 标准 `malloc` 库会在堆的未使用部分创建数据结构，用来跟踪空闲空间。写入未分配或已释放的内存，会破坏这些数据结构。

这句话很重要。

你写：

```c
int *p = malloc(4 * sizeof(int));
p[1000] = 1;
```

不只是“写错一个数组元素”。你可能把 `malloc` 内部维护的空闲链表、块大小信息等结构破坏了。

然后程序可能在很久之后才崩，比如下一次 `malloc` 或 `free` 时炸。C 的 bug 就爱搞这种悬疑片叙事。

---

### p81：简单的 `malloc()` 实现

这一页讲简单分配器的问题。

简单想法：

```text
malloc 库维护一个空闲块链表
需要内存时，从空闲块里切一块出来
free 时，再放回空闲链表
```

但多次 `malloc/free` 后会出现：

```text
内存碎片
长链条的块
```

课件说，很多小块空闲内存可能散落各处，没有大的连续空闲块；空闲块链表太长，查找会慢。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L3-CMemory-15.webp)

这就是 **fragmentation 内存碎片**。

---

### p82：更好的 `malloc` 实现

这一页介绍更好的思路：

```text
为不同大小的对象保留单独的内存池
```

比如小对象一池，中等对象一池，大对象一池。这样分配和回收更快，也更容易管理。

课件举了 “Buddy allocator 伙伴分配器”。它会把请求大小向上取整到 2 的幂大小，比如：

```text
34 KB -> 64 KB
66 KB -> 128 KB
```

这样做的好处是：找块、拆块、合并相邻空闲块会更简单。课件 p82 就说，伙伴分配器总是四舍五入到 2 次方大小的块，以简化查找正确大小和合并相邻块。

代价也很明显：可能浪费一些空间。

比如你要 34 KB，给你 64 KB，多出来的 30 KB 暂时用不上。

---

### p83：2 次幂 Buddy Allocator

这一页是图示版。

程序请求：

```text
A 请求 34k
B 请求 66k
C 请求 35k
D 请求 67k
```

如果按 2 的幂分配：

```text
34k -> 64k
66k -> 128k
35k -> 64k
67k -> 128k
```

Buddy Allocator 的基本想法是：

```text
大块可以拆成两个一样大的 buddy
两个相邻空闲 buddy 可以合并回大块
```

比如一个 128k 块可以拆成两个 64k；两个 64k 伙伴都空闲时，又可以合回 128k。

这页你不用深挖算法，只要理解：

> <mark>
> 
> 为了让 malloc/free 更快、更可控，实际分配器会用各种数据结构管理空闲内存，不是随便拿一段就完事。
> 
> </mark>

---

### p84：`realloc(p, size)`

这一页讲 `realloc`，很关键。

课件说：

```c
realloc(p, size)
```

<mark>

作用是：把之前在 p 处分配的块调整为新的大小

</mark>



特殊情况：

```text
如果 p 为 NULL，realloc 行为类似 malloc
如果 size 为 0，realloc 行为类似 free
返回新内存块地址，而且很可能已经移动
```

课件示例：

```c
int *ip;

ip = (int *) malloc(10 * sizeof(int));
/* always check for ip == NULL */

ip = (int *) realloc(ip, 20 * sizeof(int));
/* always check for ip == NULL */
/* contents of first 10 elements retained */

realloc(ip, 0); /* identical to free(ip) */
```

课件特别强调：`realloc` 返回的是新地址，内存块很可能已经移动。

---

### p60–84 总结：这段真正要掌握什么

你现在要能把 C 内存分成四类：

```text
code        程序指令，启动时加载，不变
static data 全局/静态数据，启动时加载，可修改，大小固定
stack       局部变量/参数，函数调用时创建，返回时失效
heap        malloc/calloc/realloc 创建，free 释放，程序员负责
```

最重要的 8 条铁律：

```text
1. 不要返回局部变量地址。
2. malloc 后检查是否为 NULL。
3. malloc 出来的内存未初始化。
4. malloc 返回的原始地址要保存好。
5. free 必须传 malloc/calloc/realloc 返回的起始地址。
6. 没 malloc 就别 free。
7. malloc 和 free 要配对，否则泄漏。
8. realloc 可能移动内存，旧指针可能失效。
```

这一段的主线可以压成一句话：

> **栈上的东西自动生死，堆上的东西你说了算；但你说了算，也意味着出了事你背锅。**

下一段 p85 往后就是把这些坑集中爆破：未初始化、越界、非法 `free`、重复 `free`、内存泄漏、`realloc` 后旧指针失效。

---

## 第五章：常见内存问题与性能现实

好，继续 **p85–101**。这一段前半部分是 **C 内存错误集中爆破**，后半部分进入 **Great Reality 残酷现实**：整数/浮点数不是数学里的数、内存错误很阴、性能不只看算法复杂度。

---

### p85：常见的内存问题

这一页是错误清单。课件列了几类 C 里最常见的内存问题

1. 使用未初始化的值(Using uninitialized values)
2. 使用不属于你的内存(Using memory that you don’t own)

  - 重新分配堆栈或堆变量(De-allocated stack or heap variable)
  - 对数组的越界引用(Out-of-bounds reference to array)
  - 使用NULL或垃圾数据作为指针(Using NULL or garbage data as a pointer)
3. 由于打乱malloc/calloc返回的指针，导致不正确地使用free/realloc
4. 内存泄漏(Memory leaks)

  - 你分配了一些东西，但后来忘记释放它

---

### p86：常见内存问题——use-after-free

这一页代码大概是：

```c
#include <stdlib.h>
#include <stdio.h>

int main(void) {
    int *a = malloc(sizeof(int));
    // ...
    free(a);        // a no longer exists!

    int *b = malloc(sizeof(int));
    *b = 128;

    *a = 55;        // ERROR!

    printf("a=%d, b=%d (==128!)\n", *a, *b);
}
```

输出：

```text
a=55, b=55 (==128!)
```

这很离谱：明明给 `b` 赋了 128，最后 `b` 却变成 55。

原因是：

```c
free(a);
```

<mark>

之后，

</mark>

<mark>

`a`

</mark>

 <mark>

指向的那块堆内存已经被归还给堆管理器了。你不能再通过

</mark>

 <mark>

`a`

</mark>

 <mark>

使用它。

</mark>



然后：

```c
int *b = malloc(sizeof(int));
```

堆管理器可能刚好把同一块内存又分配给 `b`。于是：

```text
a 和 b 可能指向同一块物理内存
```

所以：

```c
*a = 55;
```

实际上把 `b` 指向的值也改了。

这类错误叫：

```text
use-after-free：释放后继续使用
```

这页最可怕的点不是“程序崩了”，而是 <mark>

**程序没崩，但结果悄悄错了**

</mark>

。课件也强调：赋值给 `a` 可能破坏 `b`，错误可能无法检测到。

---

### p87：防御性编程 Defensive Programming

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 49.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L3-CMemory-16.webp" />
      </p>
    </td>
    
    
      <td style="width: 49.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L3-CMemory-17.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

这一页是对 p86 的改进版本。代码里在 `free(a)` 后加了：

```c
a = NULL;
```

然后后面又写：

```c
*a = 55;
```

输出变成：

```text
Segmentation fault: 11
```

这看起来像程序更惨了，其实是 **更好了**。

p86 的错误是隐蔽的：`a` 指向已释放内存，写进去可能破坏别的数据，但程序不一定马上崩。

p87 把 `a` 设成 `NULL`：

```c
a = NULL;
```

之后再写：

```c
*a = 55;
```

就是解引用空指针。这个错误通常会马上触发 segmentation fault。

所以这叫防御性编程：

```text
与其让错误悄悄污染数据，不如让错误尽早暴露。
```

以后你可以养成这个习惯：

```c
free(p);
p = NULL;
```

---

### p88：用 gdb 找崩溃位置

这一页展示调试器 `gdb`。

流程是：

```bash
gcc -g DefensiveB.c
gdb a.out
(gdb) run
```

然后 gdb 输出：

```text
Program received signal SIGSEGV, Segmentation fault.
0x0000000100000f76 in main () at DefensiveB.c:11
11    *a = 55;
```

重点是 `-g`：

```bash
gcc -g DefensiveB.c
```

`-g` 会把调试信息放进可执行文件里。这样 gdb 才能告诉你：

```text
在哪个源文件、哪一行崩了
```

这一页你要掌握的不是 gdb 全套命令，而是：

```text
Segmentation fault 不要瞎猜。
用 gdb 跑，先定位崩在哪一行。
```

p87 通过 `a = NULL` 让 bug 更早爆炸；p88 通过 gdb 告诉你爆炸点在哪里。配合起来，就是 C 语言活命二件套。

---

### p89：`realloc` 之后旧别名指针失效

这一页代码大概是：

```c
#include <stdio.h>
#include <stdlib.h>

int main(void) {
    int *a = malloc(10 * sizeof(int));
    int *b = a;       // b is an "alias" for a

    b[0] = 1;

    // work with a (or b) ... then increase size
    a = realloc(a, 1000 * sizeof(int));

    // yet another array
    int *c = malloc(10 * sizeof(int));

    c[0] = 3;
    b[0] = 2;

    printf("a[0]=%d, b[0]=%d, c[0]=%d\n", a[0], b[0], c[0]);
    printf("a = %p\n", a);
    printf("b = %p\n", b);
    printf("c = %p\n", c);
}
```

关键在这几句：

```c
int *b = a;
a = realloc(a, 1000 * sizeof(int));
```

一开始：

```text
a 和 b 指向同一块堆内存
```

但是 `realloc` 可能会把内存块搬到新位置。调用后：

```text
a 指向新位置
b 还指向旧位置
```

<mark>

问题是：旧位置已经不再属于你。

</mark>

<mark>

`b`

</mark>

 <mark>

已经变成悬空指针。

</mark>



课件给出的某次输出是：

```text
a[0]=1, b[0]=2, c[0]=2
a = 0x7fc53b802600
b = 0x7fc53b403140
c = 0x7fc53b403140
```

这里 `b` 和 `c` 地址一样，说明旧块后来可能又被 `malloc` 分给了 `c`。于是：

```c
b[0] = 2;
```

其实破坏了 `c[0]`。

但课件也警告：这个结果是巧合，不同运行、不同机器可能完全不同。核心结论是：

```text
realloc 之后，旧别名指针 b 不再可靠。
继续使用 b 是 bug。
```

---

### p90：残酷的现实 Great Reality

这一页是新小节标题。

从这里开始，课件从“C 内存错误”切到更广的系统现实：

```text
数学模型很美，但机器不是数学。
高级语言很舒服，但机器执行有底层细节。
算法复杂度很重要，但真实性能还受内存系统影响。
```

后面的 p91–100 就是在讲这些“残酷现实”。

---

### p91：残酷现实 #1：Ints are not Integers, Floats are not Reals

这一页的意思是：

```text
int 不是数学里的整数。
float 不是数学里的实数。
```

#### 例子 1：`x² ≥ 0` 一定成立吗？

数学里当然成立。
浮点数里通常也能成立。

但整数里不一定，因为整数有固定宽度，会溢出。

例如 32 位有符号 `int` 最大大约是：2,147,483,647

所以：40000 * 40000 = 1,600,000,000  还没超

但：50000 * 50000 = 2,500,000,000

超过 32 位有符号 `int` 范围了。结果可能变成负数、奇怪值，或者在 C 标准里属于未定义行为。

<mark>

所以机器里的

</mark>

 <mark>

`int`

</mark>

 <mark>

更像：有限格子里的数，不是无限整数。

</mark>



#### 例子 2：加法结合律一定成立吗？

数学里：

```text
(x + y) + z = x + (y + z)
```

但浮点数里不一定。

课件例子：

```text
(1e20 + -1e20) + 3.14  → 3.14
1e20 + (-1e20 + 3.14) → ??
```

为什么第二个可能不是 3.14？

因为 `3.14` 相对于 `1e20` 太小了，小到浮点表示时可能被“吃掉”。于是：

```text
-1e20 + 3.14 ≈ -1e20
```

再加：

```text
1e20 + -1e20 = 0
```

所以结果可能变成 0。

这一页的核心：

```text
机器数有范围、有精度。
不要把 int 当无限整数，不要把 float 当真实实数。
```

课件这里用整数平方和浮点结合律说明机器数与数学数不同。

---

### p92：残酷现实 #2：你必须知道汇编

理解汇编，是理解机器级执行模型的关键。

课件列了几个场景：

```text
1. 程序出现高级语言模型解释不了的错误
2. 调优程序性能
3. 理解编译器做了什么优化、没做什么优化
4. 操作系统、编译器等系统软件实现
5. 分析或对抗恶意软件
```

---

### p93：残酷现实 #3：内存很重要

这页讲三个事实。

第一，内存不是无限的：

- 它必须被分配和管理。
- 很多应用程序是内存主导的。

第二，内存引用错误特别有害：

- 它可能在时间和空间上造成巨大影响。

> 也就是：你现在写错一个地址，可能污染另一个对象；现在埋雷，十分钟后爆。

第三，内存性能不是均匀的：

- 缓存和虚拟内存效应会极大地影响程序性能
- 使程序适应存储器系统的特点可以大幅度提升速度

这句话非常关键。抽象上我们觉得：

```text
访问 memory[i] 和 memory[j] 都差不多
```

但真实机器不是这样。离 CPU 近的缓存很快，主存慢很多；连续访问通常比跳着访问快很多。

课件这一页把内存容量、内存错误和内存性能三个问题放在一起强调：随机访问内存只是抽象，真实内存系统有层次、有代价。

---

### p94：内存引用错误示例

代码：

```c
typedef struct {
    int a[2];
    double d;
} struct_t;

double fun(int i) {
    volatile struct_t s;
    s.d = 3.14;
    s.a[i] = 1073741824; /* Possibly out of bounds */
    return s.d;
}
```

结构体里有：

```text
a[0]
a[1]
d
```

合法访问只有：

```c
s.a[0]
s.a[1]
```

但是代码写的是：

```c
s.a[i] = 1073741824;
```

当 `i >= 2` 时，就越界了。

课件给的结果：

```text
fun(0) → 3.14
fun(1) → 3.14
fun(2) → 3.1399998664856
fun(3) → 2.00000061035156
fun(4) → 3.14
fun(6) → Segmentation fault
```

为什么这么怪？

因为 `a[2]`、`a[3]` 已经不是数组元素了，它们会写到结构体后面的内存。刚好结构体后面就是 `double d` 的字节，所以越界写可能破坏 `d` 的一部分。

所以：

```text
i = 0,1：写的是 a[0], a[1]，d 没变
i = 2,3：写到了 d 的不同部分，d 被改坏
i = 6：写到更危险的位置，程序崩溃
```

这页要记住：

```text
数组越界不一定立刻崩。
它可能只是悄悄改坏旁边的数据。
```

课件也强调这个结果是系统特定的。

---

### p95：解释 p94 的内存布局

这一页用图解释 `fun(i)` 到底写到了哪里。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L3-CMemory-18.webp)

```c
s.a[2] = 1073741824;
```

看起来像访问数组第 3 个元素，但 `a` 只有两个元素。由于 `int` 是 4 字节，`a[2]` 对应的位置刚好可能落在 `d` 的一部分上。

这就是为什么：

```text
fun(2) → 3.1399998664856
fun(3) → 2.00000061035156
```

`d` 被改了一部分，所以结果变成奇怪的小数。

而：

```text
fun(6) → Segmentation fault
```

可能是因为写到了某个关键区域，比如保存程序控制状态的位置，或者不可访问内存。

```text
越界访问的后果取决于内存布局。
内存布局又取决于系统、编译器、优化方式。
```

所以同一段错代码，在你电脑上“没事”，到别人电脑上炸了，完全正常。它不是没 bug，它只是还没到爆炸时间。

---

### p96：内存引用错误总结

**C 和 C++ 不提供内存保护机制**

- 数组越界访问（Out-of-bounds array references）
- 无效的指针值（Invalid pointer values）
- 错误使用 `malloc/free`（如重复释放、未释放、释放后继续使用等）

**容易导致难以发现的 Bug**

- Bug 是否产生影响取决于系统环境和编译器
- Bug 往往与真正出错的位置相距较远

  - 被破坏的对象可能与当前访问对象在逻辑上毫无关联
  - Bug 的影响可能在产生很长时间后才会显现

**应对方法**

- 使用具有内存安全机制的编程语言

  - 如 Java、Ruby、Python、ML 等
- 深入了解各种可能发生的内存交互和错误
- 使用或开发内存检测工具

  - 例如 **Valgrind** 用于检测内存访问错误和内存泄漏

---

### p97：残酷现实 #4：性能比渐近复杂性更复杂

这一页讲性能。

常熟因素很重要

比如两个程序都是 `O(n)`，一个可能比另一个慢 10 倍。

课件强调：

```text
常数因素也很重要
精确操作计数也不能完全预测性能
代码写法可能造成 10 倍性能差异
优化要在多个层次进行：
算法、数据表示、过程、循环
```

系统层面还要知道：

```text
程序如何编译和执行
如何测量性能、识别瓶颈
如何在不破坏模块化和通用性的情况下优化
```

这页的核心：

```text
真实性能 = 算法 + 编译器 + CPU + 缓存 + 内存访问模式 + 代码写法
```

课件第 97 页明确说，常数因素重要，甚至精确操作计数也不能预测性能，并且要在算法、数据表示、过程和循环多个层次优化。

---

### p98：内存系统性能示例——二维数组复制

这一页是非常经典的缓存局部性例子。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L3-CMemory-19.webp)

有两个函数：

```c
void copyji(int src[2048][2048],
            int dst[2048][2048])
{
    int i, j;
    for (j = 0; j < 2048; j++)
        for (i = 0; i < 2048; i++)
            dst[i][j] = src[i][j];
}
```

和：

```c
void copyij(int src[2048][2048],
            int dst[2048][2048])
{
    int i, j;
    for (i = 0; i < 2048; i++)
        for (j = 0; j < 2048; j++)
            dst[i][j] = src[i][j];
}
```

它们做的事一样，都是复制二维数组。
但课件给出的时间差非常大：

```text
copyji：81.8 ms
copyij：4.3 ms
```

为什么？

C 的二维数组是 <mark>

**行优先 row-major**

</mark>

 <mark>

存储

</mark>

，也就是说，同一行里的元素在内存中连续。

`copyij` 的内层循环是 `j`：

固定 `i`，连续扫 `j`，就是沿着一行走。内存访问连续，缓存友好，所以快。

`copyji` 的内层循环是 `i`：

固定 `j`，变化 `i`，相当于沿着一列走。每次跳到下一行同一列，地址跨度很大，缓存很不友好，所以慢。

这页的结论：同样的算法复杂度，同样的数据量，仅仅循环顺序不同，性能可以差十几倍。

课件 p98 就用 `copyji` 和 `copyij` 展示了访问模式对分层存储结构性能的影响。

---

### p99：性能不同可视化——stride

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ComputerOrganization/L3-CMemory-20.webp)

---

### p100：残酷现实 #5：计算机不只是执行程序

**程序需要进行输入和输出（I/O）**

- 输入输出系统对程序的可靠性至关重要
- 输入输出系统对程序的性能至关重要

**程序需要通过网络进行通信**

- 网络环境带来了许多系统级问题：

  - 自治进程的并发操作
  - 应对不可靠的通信媒体
  - 跨平台兼容性
  - 复杂的性能问题

---

### p101：小结

**C 语言有三个主要的内存段**

- **静态数据（Static Data）**
  - 函数外部的变量
  - 例如全局变量（global variables）
- **堆栈（Stack）**
  - 函数的局部变量（local variables）
- **堆（Heap）**
  - 使用 `malloc/free` 显式分配和释放的内存

**堆数据容易产生 Bug**

- 可能导致内存泄漏（memory leaks）
- 可能导致内存损坏（memory corruption）

**应对策略**

- **规划（Planning）**
  - 明确谁“拥有” `malloc` 分配的数据
  - 通常会有多个“所有者”或指针指向同一块数据
  - 明确谁可以安全地调用 `free`
- **防御性编程（Defensive Programming）**
  - 将已释放的指针赋值为 `NULL`
  - 使用常量表示数组大小
- **使用工具**
  - `gdb`
  - `Valgrind`

---

## 第六章：C 内存错误专项训练

好，最后 **p102–119** 基本就是“C 内存错误专项训练”。我先给你一个“坑位编号”，后面每道题都对应这些坑：

<table>
<thead>
  <tr>
    <th>
      坑编号
    </th>
    
    <th>
      坑名
    </th>
    
    <th>
      典型表现
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      坑 A
    </td>
    
    <td>
      使用未初始化值
    </td>
    
    <td>
      读到垃圾值
    </td>
  </tr>
  
  <tr>
    <td>
      坑 B
    </td>
    
    <td>
      使用不属于你的内存
    </td>
    
    <td>
      越界读写、访问已释放内存、访问栈上已失效内存
    </td>
  </tr>
  
  <tr>
    <td>
      坑 C
    </td>
    
    <td>
      搞乱 <code code="malloc">
        malloc
      </code>
      
       返回的句柄
    </td>
    
    <td>
      指针加减后再 <code code="free">
        free
      </code>
      
      ，或者 <code code="free">
        free
      </code>
      
       中间地址
    </td>
  </tr>
  
  <tr>
    <td>
      坑 D
    </td>
    
    <td>
      内存泄漏
    </td>
    
    <td>
      <code code="malloc">
        malloc
      </code>
      
       了，但丢了地址或忘了 <code code="free">
        free
      </code>
    </td>
  </tr>
  
  <tr>
    <td>
      坑 E
    </td>
    
    <td>
      <code code="realloc">
        realloc
      </code>
      
       后旧指针失效
    </td>
    
    <td>
      <code code="realloc">
        realloc
      </code>
      
       可能移动内存，旧别名不能再用
    </td>
  </tr>
  
  <tr>
    <td>
      坑 F
    </td>
    
    <td>
      返回栈内存地址
    </td>
    
    <td>
      函数返回后局部数组/局部变量失效
    </td>
  </tr>
  
  <tr>
    <td>
      坑 G
    </td>
    
    <td>
      非法 <code code="free">
        free
      </code>
      
       / 重复 <code code="free">
        free
      </code>
    </td>
    
    <td>
      <code code="free(&局部变量)">
        free(&局部变量)
      </code>
      
      、<code code="free(p+1)">
        free(p+1)
      </code>
      
      、double free
    </td>
  </tr>
  
  <tr>
    <td>
      坑 H
    </td>
    
    <td>
      字符串结尾 <code code="'\0'">
        '\0'
      </code>
      
       处理错误
    </td>
    
    <td>
      忘记给字符串多留 1 个字节
    </td>
  </tr>
</tbody>
</table>

课件 p85 已经把这些总结过：未初始化、使用不属于你的内存、越界、用 `NULL` 或垃圾指针、打乱 `malloc/calloc` 返回的指针、内存泄漏，都是常见 C 内存问题。

---

### p103–104：使用你不拥有的内存

#### 题目代码

```c
int *ipr, *ipw;

void ReadMem() {
    int i, j;
    ipr = (int *) malloc(4 * sizeof(int));
    i = *(ipr - 1000);
    j = *(ipr + 1000);
    free(ipr);
}

void WriteMem() {
    ipw = (int *) malloc(5 * sizeof(int));
    *(ipw - 1000) = 0;
    *(ipw + 1000) = 0;
    free(ipw);
}
```

#### 错误 1：越界读

```c
i = *(ipr - 1000);
j = *(ipr + 1000);
```

这两个都严重越界。

`ipr - 1000` 指向申请块前面很远的位置。
`ipr + 1000` 指向申请块后面很远的位置。

它们都不属于这次 `malloc` 返回的 4 个 `int` 范围。

---

#### 错误 2：越界写

```c
*(ipw - 1000) = 0;
*(ipw + 1000) = 0;
```

```text
坑 B：使用不属于你的内存
坑 B2：数组/堆块越界写
```

这个和前面 p80 对应：`malloc` 库在堆里维护空闲块数据结构，写入未分配或已释放的内存可能破坏这些结构。

---

#### 正确写法

如果只申请 4 个元素，就只能访问 4 个：

```c
void ReadMem(void) {
    int *ipr = malloc(4 * sizeof(*ipr));
    if (ipr == NULL) return;

    int i = ipr[0];
    int j = ipr[3];

    free(ipr);
}
```

---

### p105–106：堆管理故障——覆盖全局指针导致泄漏

#### 题目代码

```c
int *pi;

void foo() {
    pi = malloc(8 * sizeof(int));
    ...
    free(pi);
}

void main() {
    pi = malloc(4 * sizeof(int));
    foo();
    ...
}
```

p105 问“这段代码有什么问题”，p106 明确说这是 **内存泄漏：****malloc** **比** **free** **多**。

#### 为什么 `free(pi)` 没救回来？

```c
free(pi);
```

此时 `pi` 指向的是堆块 B，所以释放的是 B。

但堆块 A 已经找不到了，无法释放。

所以整个过程是：

```text
main malloc A
foo malloc B，覆盖 pi，A 泄漏
foo free B
A 仍然泄漏
```

---

#### 这题对应哪个坑？

```text
主坑：坑 D，内存泄漏
副坑：所有权规划不清
```

也对应前面 p78 的原则：

> `malloc` 和 `free` 是好朋友。如果调用了 `malloc`，就需要对结果调用 `free`，否则就接受内存泄漏。

<alert type="tip">

`malloc` 和 `free` 的个数一般一样多

</alert>

---

### p107–108：堆管理故障——改变 malloc 返回的句柄

#### 题目代码

```c
int *plk = NULL;

void genPLK() {
    plk = malloc(2 * sizeof(int));
    ...
    plk++;
}
```

p107 问“这段代码有什么问题”，p108 说这是潜在内存泄漏：句柄，也就是块指针，被改变了。

---

#### “句柄被改变”

`malloc` 返回的地址必须保存好。`free` 只认`malloc` 的首地址

这题和前面 p72–74 是同一个坑：循环里把 `p++` 后，再 `free(p)` 是错的；要保留原始地址，最后 `free(array)`。

---

### p109–110：堆管理故障——非法 free 和 double free

#### 题目代码

```c
void FreeMemX() {
    int fnh = 0;
    free(&fnh);
}

void FreeMemY() {
    int *fum = malloc(4 * sizeof(int));
    free(fum + 1);
    free(fum);
    free(fum);
}
```

p109 问问题，p110 给出答案：不能释放非堆内存，不能释放未分配的内存。

---

#### FreeMemX 的问题

`fnh` 是局部变量，在栈上。

但 `free` 只能释放由 `malloc/calloc/realloc` 返回的堆内存。

非法`free`

---

#### FreeMemY 的第一个问题：free 中间地址

`fum` 是 `malloc` 返回的原始地址。

合法：

```c
free(fum);
```

非法：

```c
free(fum + 1);
```

因为 `fum + 1` 指向堆块中间，不是整块堆内存的起始地址。

```text
坑 C：搞乱 malloc 返回的句柄
坑 G：非法 free
```

---

#### FreeMemY 的第二个问题：double free

```c
free(fum);
free(fum);
```

再次释放同一块已经释放过的内存，非法。

对应：

```text
坑 G：重复 free
坑 B：使用/操作已释放内存
```

double free 很危险，因为它可能破坏堆管理器的数据结构，造成崩溃或安全漏洞。

---

#### 正确写法

```c
void FreeMemY(void) {
    int *fum = malloc(4 * sizeof(*fum));
    if (fum == NULL) return;

    ...

    free(fum);
    fum = NULL;
}
```

注意：

```c
fum = NULL;
```

可以降低重复使用已释放指针的风险。

这题对应前面 p78 的原则：

```text
没有 malloc，就没有 free。
free 必须传 malloc 最初返回的地址。
同一块内存只能 free 一次。
```

---

### p111–112：字符串越界——没有给 `'\0'` 留空间

#### 题目代码

```c
void StringManipulate() {
    const char *name = "Safety Critical";
    char *str = malloc(10);
    strncpy(str, name, 10);
    str[10] = '\0';
    printf("%s\n", str);
}
```

p111 问问题，p112 给出：这是超出数组边界的引用，既有越界写，也有越界读。

---

#### 逐步拆

```c
char *str = malloc(10);
```

申请了 10 个字节。

合法下标是：

```text
str[0] ~ str[9]
```

没有：

```text
str[10]
```

---

#### 错误 1：越界写

```c
str[10] = '\0';
```

这是写第 11 个字节。

但是只申请了 10 字节。

所以：

```text
str[10] 越界
```

对应：

```text
坑 B：使用不属于你的内存
坑 H：字符串结尾 '\0' 没有预留空间
```

---

#### 错误 2：`strncpy` 不一定补 `'\0'`

```c
strncpy(str, name, 10);
```

`name` 是：

```text
"Safety Critical"
```

长度明显超过 10。

`strncpy(str, name, 10)` 会复制前 10 个字符，但如果源字符串长度大于等于 10，它不会自动在目标末尾补 `'\0'`。

所以复制后，`str` 里可能是：

```text
S a f e t y   C r i
```

也就是 10 个字符，没有字符串终止符。

---

#### 错误 3：`printf("%s")` 可能越界读

```c
printf("%s\n", str);
```

`%s` 会从 `str` 开始一直读，直到遇到 `'\0'`。

如果 `str` 的合法范围里没有 `'\0'`，它就会继续往后读堆内存。

这对应：

```text
坑 B：越界读
坑 H：字符串没有正确以 '\0' 结尾
```

---

#### 错误 4：没有 `free(str)`

函数结束前没有：

```c
free(str);
```

所以还有一个附加问题：

```text
坑 D：内存泄漏
```

虽然课件这一页重点讲越界，但你考试/查 bug 时要顺手看到这个泄漏。

---

#### 正确写法 1：申请 11 字节

如果你只想复制最多 10 个字符并加终止符：

```c
void StringManipulate(void) {
    const char *name = "Safety Critical";

    char *str = malloc(11);
    if (str == NULL) return;

    strncpy(str, name, 10);
    str[10] = '\0';

    printf("%s\n", str);

    free(str);
}
```

这里申请 11 字节：

```text
10 个有效字符 + 1 个 '\0'
```

---

#### 正确写法 2：按源字符串长度申请

```c
void StringManipulate(void) {
    const char *name = "Safety Critical";

    char *str = malloc(strlen(name) + 1);
    if (str == NULL) return;

    strcpy(str, name);
    printf("%s\n", str);

    free(str);
}
```

这题的核心句：

```text
C 字符串的内存大小 = 字符数量 + 1 个 '\0'。
```

---

### p113–114：返回局部数组地址

#### 题目代码

```c
char *append(const char* s1, const char *s2) {
    const int MAXSIZE = 128;
    char result[128];
    int i = 0, j = 0;

    for (j = 0; i < MAXSIZE - 1 && j < strlen(s1); i++, j++) {
        result[i] = s1[j];
    }

    for (j = 0; i < MAXSIZE - 1 && j < strlen(s2); i++, j++) {
        result[i] = s2[j];
    }

    result[++i] = '\0';
    return result;
}
```

p113 问问题，p114 明确说：`result` 是本地数组名，分配在栈上；函数返回了指向栈内存的指针，函数返回后无效。

---

### 主错误：返回栈内存地址

```c
char result[128];
```

`result` 是局部数组，存在当前函数 `append` 的栈帧里。

函数运行时：

```text
append 的栈帧存在
result 存在
```

函数返回后：

```text
append 的栈帧销毁
result 失效
```

但代码写：

```c
return result;
```

这等价于返回：

```c
return &result[0];
```

也就是把局部数组的地址交给外面。

外面拿到这个指针后，它指向的是已经失效的栈内存。

这对应：

```text
坑 F：返回栈内存地址
坑 B：使用不属于你的内存
```

这和 p68 的 `return &x;` 是同类错误，只不过这里返回的是局部数组地址。

---

### 额外错误：`result[++i] = '\0'`

这个地方也有问题。

前两个循环结束后，`i` 已经是下一个应该写入的位置。

正确应该是：

```c
result[i] = '\0';
```

但代码写的是：

```c
result[++i] = '\0';
```

这会先让 `i` 加 1，再写终止符。

问题有两个：

#### 情况 1：中间跳过一个位置

假设拼接后长度是 5。
循环结束时：

```text
i = 5
```

正确应该写：

```c
result[5] = '\0';
```

但代码写：

```c
result[++i] = '\0';
```

结果写到：

```text
result[6]
```

`result[5]` 没初始化，字符串中间可能出现垃圾字符。

对应：

```text
坑 A：使用未初始化值
坑 H：字符串终止符位置错误
```

#### 情况 2：可能越界写

如果循环结束时：

```text
i = 127
```

因为条件是：

```c
i < MAXSIZE - 1
```

那么：

```c
result[++i] = '\0';
```

会写：

```text
result[128]
```

但合法下标是：

```text
result[0] ~ result[127]
```

所以越界。

对应：

```text
坑 B：数组越界写
坑 H：字符串结尾处理错误
```

---

### 正确写法 1：让调用者提供缓冲区

这是 C 里很常见、很稳的写法：

```c
void append(char *result, size_t maxsize,
            const char *s1, const char *s2) {
    size_t i = 0, j = 0;

    for (j = 0; i < maxsize - 1 && s1[j] != '\0'; i++, j++) {
        result[i] = s1[j];
    }

    for (j = 0; i < maxsize - 1 && s2[j] != '\0'; i++, j++) {
        result[i] = s2[j];
    }

    result[i] = '\0';
}
```

调用者：

```c
char buf[128];
append(buf, sizeof(buf), "hello", "world");
```

好处是：

```text
谁提供内存，谁管理内存。
append 只负责写，不负责分配。
```

---

### 正确写法 2：在堆上分配，让调用者 free

```c
char *append(const char *s1, const char *s2) {
    size_t len1 = strlen(s1);
    size_t len2 = strlen(s2);

    char *result = malloc(len1 + len2 + 1);
    if (result == NULL) return NULL;

    memcpy(result, s1, len1);
    memcpy(result + len1, s2, len2);
    result[len1 + len2] = '\0';

    return result;
}
```

调用者必须：

```c
char *s = append("hello", "world");
...
free(s);
```

这题对应：

```text
主坑：坑 F，返回栈内存地址
副坑：坑 B，可能越界写
副坑：坑 H，字符串 '\0' 位置错误
副坑：坑 D，如果改成 malloc 版本，调用者必须 free
```

---

## p115–117：`realloc` 返回值被忽略

### 题目代码

```c
int* init_array(int *ptr, int new_size) {
    ptr = realloc(ptr, new_size * sizeof(int));
    memset(ptr, 0, new_size * sizeof(int));
    return ptr;
}

int* fill_fibonacci(int *fib, int size) {
    int i;
    init_array(fib, size);

    /* fib[0] = 0; */
    fib[1] = 1;

    for (i = 2; i < size; i++)
        fib[i] = fib[i-1] + fib[i-2];

    return fib;
}
```

p115 问问题，p116 给出提示：这是 `mem` 句柄使用不当；记住 `realloc` 可能移动整块内存；如果数组被移动到新位置怎么办？p117 的 “我的东西呢？” 就是在吐槽：你重新分配后的地址去哪了？

---

### 先看 `init_array`

```c
ptr = realloc(ptr, new_size * sizeof(int));
```

`realloc` 可能有两种情况：

#### 情况 1：原地扩容

```text
旧地址不变
ptr 还是原来的地址
```

这种情况下代码可能碰巧能跑。

#### 情况 2：搬到新位置

```text
旧块释放
新块分配到另一个地址
ptr 指向新地址
```

这个才是关键。

---

### 问题 1：`fill_fibonacci` 忽略了返回值

```c
init_array(fib, size);
```

这里调用了 `init_array`，但没有接住返回值。

如果 `realloc` 把内存搬家了，那么：

```text
init_array 里的 ptr 指向新地址
fill_fibonacci 里的 fib 仍然是旧地址
```

`ptr` 是参数副本。C 函数参数默认按值传递，所以 `init_array` 改的是自己的局部副本，不会自动改外面的 `fib`。

于是后面：

```c
fib[1] = 1;
```

可能是在旧地址上写。

但旧地址可能已经被 `realloc` 释放。

所以这对应：

```text
坑 E：realloc 后旧指针失效
坑 B：访问已释放/不属于你的内存
```

---

### 问题 2：如果 `fib` 原来是 NULL，会更惨

假设调用时：

```c
int *fib = NULL;
fill_fibonacci(fib, size);
```

在 `init_array` 里：

```c
ptr = realloc(NULL, size * sizeof(int));
```

这相当于 `malloc`，返回一块新内存。

但是 `fill_fibonacci` 没有接返回值，所以外面的 `fib` 还是 `NULL`。

然后：

```c
fib[1] = 1;
```

就相当于：

```c
NULL[1] = 1;
```

直接炸。

对应：

```text
坑 B：使用 NULL 指针
坑 E：没有正确接收 realloc 返回的新地址
```

---

### 问题 3：`realloc` 失败时会出事

```c
ptr = realloc(ptr, new_size * sizeof(int));
memset(ptr, 0, new_size * sizeof(int));
```

如果 `realloc` 失败，会返回 `NULL`。

此时：

```c
memset(ptr, 0, ...)
```

就是：

```c
memset(NULL, 0, ...)
```

可能直接崩溃。

而且这句：

```c
ptr = realloc(ptr, ...)
```

还有一个经典危险：如果直接用原指针接返回值，一旦失败，原来的堆块地址可能丢失，造成泄漏。更稳妥应该用临时指针。

对应：

```text
坑 D：可能泄漏
坑 B：可能使用 NULL
坑 E：realloc 处理不当
```

---

### 问题 4：`size < 2` 时 `fib[1]` 越界

代码写：

```c
fib[1] = 1;
```

如果 `size` 是 0 或 1，`fib[1]` 越界。

对应：

```text
坑 B：数组越界写
```

---

### 正确写法

```c
int* init_array(int *ptr, int new_size) {
    int *tmp = realloc(ptr, new_size * sizeof(*ptr));
    if (tmp == NULL) {
        return NULL;
    }

    memset(tmp, 0, new_size * sizeof(*tmp));
    return tmp;
}

int* fill_fibonacci(int *fib, int size) {
    if (size <= 0) return fib;

    fib = init_array(fib, size);
    if (fib == NULL) return NULL;

    fib[0] = 0;

    if (size > 1) {
        fib[1] = 1;
    }

    for (int i = 2; i < size; i++) {
        fib[i] = fib[i-1] + fib[i-2];
    }

    return fib;
}
```

调用者也要接住返回值：

```c
fib = fill_fibonacci(fib, size);
```

这题是最后几页里最综合的一题，对应：

```text
主坑：坑 E，realloc 可能移动内存
副坑：坑 B，旧指针可能访问已释放内存
副坑：坑 D，realloc 失败可能泄漏
副坑：坑 B，size < 2 时越界
副坑：C 参数按值传递，函数里改 ptr 不会自动改外面的 fib
```

一句话：

```text
realloc 的返回值必须接住，而且要用新地址继续操作。
```

---

## p118：Java 中的内存“泄漏”

这一页不是 C 代码题，而是对比 Java 和 C。

课件说，Java 里也可能有“内存泄漏”：如果你意外保留了对未使用对象的引用，垃圾回收器就不会回收它，最终也可能导致内存不足。

---

### Java 为什么也会 leak？

比如：

```java
static List<Object> list = new ArrayList<>();

void f() {
    Object obj = new Object();
    list.add(obj);
}
```

如果 `list` 一直存在，里面的对象引用也一直存在，那么 GC 会认为：

```text
这些对象还能被访问
不能回收
```

哪怕你逻辑上已经不需要它们了，它们也不会被释放。

这就是 Java 的“内存泄漏”。

对应：

```text
坑 D 的 Java 版本：逻辑上不用了，但引用还在，GC 无法回收
```

---

### Java 消除了哪些 C 的坑？

课件列了几类 Java 基本消除的 C 错误：

```text
1. 使用无效参数调用 free
2. 访问已释放内存
3. 数组越界访问
4. 访问未分配内存，忘记 new
```

Java 没有手动 `free`，所以没有：

```text
free(&局部变量)
free(p + 1)
double free
```

数组越界会抛异常，而不是悄悄改坏旁边的数据。

空引用会抛 `NullPointerException`，虽然也是错误，但至少通常不会静默破坏数据。

所以 p118 的核心不是“Java 没有内存问题”，而是：

```text
Java 仍可能泄漏，但少了很多 C 里会静默损坏内存的坑。
```

对应关系：

```text
Java 仍有：坑 D，内存泄漏
Java 大幅避免：坑 B、坑 C、坑 E、坑 G
```

---

## p119：使用堆的例子——怎么除掉苹果树？

这一页接的是前面堆上创建树的例子。课件问：

```text
我们怎样才能除掉苹果树？
```

意思是：如果你用 `malloc` 一个节点一个节点创建了一棵树，最后怎么释放整棵树？

p119 明确说，需要一种方法释放不再使用的内存，否则最终可能耗尽。

---

### 为什么不能只 `free(root)`？

假设树是：

```text
10
       /  \
      5    16
          /
         11
```

每个节点都是单独 `malloc` 出来的。

如果你只写：

```c
free(root);
```

你只释放了根节点 `10`。

但是：

```text
5、16、11 这些节点还在堆上
```

而且根节点释放后，你再也找不到它们了。

这就是：

```text
坑 D：内存泄漏
```

---

### 为什么不能先 free 根，再 free 子树？

错误写法：

```c
void free_tree(Node *root) {
    free(root);
    free_tree(root->left);
    free_tree(root->right);
}
```

这个错得很典型。

因为：

```c
free(root);
```

之后，`root` 指向的内存已经不属于你。

再访问：

```c
root->left
root->right
```

就是 use-after-free。

对应：

```text
坑 B：访问已释放内存
```

---

### 正确释放树：后序遍历

应该先释放左右子树，再释放自己：

```c
void free_tree(Node *root) {
    if (root == NULL) {
        return;
    }

    free_tree(root->left);
    free_tree(root->right);

    free(root);
}
```

为什么是这个顺序？

```text
先释放 left
再释放 right
最后释放 root
```

因为在释放 `root` 之前，你还需要通过：

```c
root->left
root->right
```

找到左右孩子。

这叫后序遍历。

---

### 释放后最好把 root 设为 NULL

如果你在外面有：

```c
Node *root = NULL;
insert(10, &root);
insert(5, &root);
...
```

释放时可以：

```c
free_tree(root);
root = NULL;
```

这样之后如果误用：

```c
root->key
```

更容易暴露为空指针错误，而不是悄悄访问已释放内存。

---

### 如果想在函数里把 root 也清 NULL

可以传二级指针：

```c
void destroy_tree(Node **rootp) {
    if (rootp == NULL || *rootp == NULL) {
        return;
    }

    Node *root = *rootp;

    destroy_tree(&root->left);
    destroy_tree(&root->right);

    free(root);
    *rootp = NULL;
}
```

调用：

```c
destroy_tree(&root);
```

这和前面 `insert(int key, Node **tree)` 的思路一样：如果函数要修改外面的指针本身，就传指针的地址。

p119 对应的坑：

```text
主坑：坑 D，树节点不释放会泄漏
副坑：坑 B，释放根后再访问孩子是 use-after-free
对应原则：谁 malloc，谁规划 free；复杂结构要递归释放
```

---

## 最后 102–119 页总表

<table>
<thead>
  <tr>
    <th>
      页码
    </th>
    
    <th>
      题目/内容
    </th>
    
    <th>
      主要错误
    </th>
    
    <th>
      对应坑
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      p103–104
    </td>
    
    <td>
      <code code="ipr ± 1000">
        ipr ± 1000
      </code>
      
      , <code code="ipw ± 1000">
        ipw ± 1000
      </code>
    </td>
    
    <td>
      超出 <code code="malloc">
        malloc
      </code>
      
       范围读写
    </td>
    
    <td>
      坑 B
    </td>
  </tr>
  
  <tr>
    <td>
      p105–106
    </td>
    
    <td>
      全局 <code code="pi">
        pi
      </code>
      
       被第二次 <code code="malloc">
        malloc
      </code>
      
       覆盖
    </td>
    
    <td>
      原来的堆块丢失
    </td>
    
    <td>
      坑 D
    </td>
  </tr>
  
  <tr>
    <td>
      p107–108
    </td>
    
    <td>
      <code code="plk++">
        plk++
      </code>
    </td>
    
    <td>
      改掉 <code code="malloc">
        malloc
      </code>
      
       原始句柄
    </td>
    
    <td>
      坑 C、坑 D、坑 G
    </td>
  </tr>
  
  <tr>
    <td>
      p109–110
    </td>
    
    <td>
      <code code="free(&fnh)">
        free(&fnh)
      </code>
      
      , <code code="free(fum+1)">
        free(fum+1)
      </code>
      
      , double free
    </td>
    
    <td>
      非法释放、重复释放
    </td>
    
    <td>
      坑 G、坑 C
    </td>
  </tr>
  
  <tr>
    <td>
      p111–112
    </td>
    
    <td>
      <code code="malloc(10)">
        malloc(10)
      </code>
      
       后 <code code="str[10]='\0'">
        str[10]='\0'
      </code>
    </td>
    
    <td>
      字符串终止符越界
    </td>
    
    <td>
      坑 B、坑 H、坑 D
    </td>
  </tr>
  
  <tr>
    <td>
      p113–114
    </td>
    
    <td>
      <code code="return result">
        return result
      </code>
    </td>
    
    <td>
      返回局部数组地址
    </td>
    
    <td>
      坑 F、坑 B、坑 H
    </td>
  </tr>
  
  <tr>
    <td>
      p115–117
    </td>
    
    <td>
      忽略 <code code="realloc">
        realloc
      </code>
      
       返回值
    </td>
    
    <td>
      新地址丢失，旧指针失效
    </td>
    
    <td>
      坑 E、坑 B、坑 D
    </td>
  </tr>
  
  <tr>
    <td>
      p118
    </td>
    
    <td>
      Java 内存泄漏
    </td>
    
    <td>
      保留无用引用，GC 无法回收
    </td>
    
    <td>
      坑 D 的 Java 版本
    </td>
  </tr>
  
  <tr>
    <td>
      p119
    </td>
    
    <td>
      释放堆上的树
    </td>
    
    <td>
      复杂结构要递归 free
    </td>
    
    <td>
      坑 D、坑 B
    </td>
  </tr>
</tbody>
</table>

你最后可以用这句话收束整章：

```text
C 内存错误的本质不是“不会写 malloc/free”，
而是没搞清楚：这块内存是谁的、现在还活着吗、原始地址还在吗、谁负责释放。
```

---
