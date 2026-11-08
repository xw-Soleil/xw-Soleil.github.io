# Chapter 7：Software Development Tools

> 软件开发工具：详细版笔记

## Software Development Tools

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ICCAD/DetailCh7-01.webp)

#### **C/C++ 程序开发流程（从源码到运行）**

- **1）编辑源码（Editing source program）**
  - 编写/修改源文件，例如 `xxx.c`（C）或 `xxx.cpp`（C++）。
  - 产物：仍是**人类可读**的源代码文件。
- **2）编译（Compiler）**
  - 编译器把 `xxx.c` 翻译成**目标文件** `xxx.o`（object file）。
  - 目标文件特点：
  
    - 已经是机器相关的二进制，但**通常还不能直接运行**；
    - 可能仍有“未解析的符号”（比如调用了别的文件/库里的函数）。
- **3）链接（Linker）**
  - 链接器把多个目标文件和库“拼起来”，生成最终可执行文件。
  - 输入可能包括：
  
    - 当前编译产物：`xxx.o`
    - 其他模块的目标文件：`yyy.o`, `zzz.o`（Object modules）
    - 库：`sss.a`（Library，通常指**静态库** `.a`）
  - 输出：可执行文件，例如默认的 `a.out`，或命名为 `xxx`。
- **4）操作系统执行（OS execution）**
  - 运行可执行文件：OS 负责装载程序到内存、做动态链接（若有）、分配资源并开始执行。
- **5）调试（Debugger，if error）**
  - 如果运行出错（崩溃、逻辑不对、异常行为），使用调试器（如 `gdb`）定位问题：断点、单步、查看调用栈/变量等。

#### 文件后缀命名约定（Suffix Naming Convention）

- `.sh` **/** `.bash` **/** `.csh`：Shell 脚本
- `.c` **/** `.cpp` **/** `.h` **/** `.hpp`：C/C++ 源文件 / 头文件
- `.f`：Fortran 源文件
- `.o`：目标文件（Object file，编译后的中间产物，尚未链接）
- `.s`：汇编源文件（Assembly source）
- `.a`：静态库（Static library，链接时把需要的目标代码打包进可执行文件）
- `.so`：动态库 / 共享库（Shared object，运行时或装载时动态链接）
- `.pl`：Perl 脚本
- `.tcl`：Tcl/Tk 脚本
- `.py`：Python 脚本
- `.java`：Java 源文件
- `.scala`：Scala 源文件

Stuz 老师本来打算下来问大家——要记住

同时强调了一下.a  .so 静态链接库和动态链接库

**gcc 原来叫GNU C compliers  现在叫GNU Compiler Collection**

后来它支持的不止 C（还包括 C++、Fortran 等），所以官方把 **GCC** 的全称扩展为 **GNU Compiler Collection**。

#### C 编译器命名与来源（C Compilers）

- `cc/CC`：历史上常见于 **Sun Microsystems** 的编译器命令名

  - 一般约定：`cc` 偏 C；`CC` 偏 C++（不同系统/厂商实现细节可能不同）
- `gcc/g++`：来自 **GNU** 工具链

  - `gcc`：常用作 C 编译驱动器（也可驱动其他语言，取决于参数/文件后缀）
  - `g++`：常用作 C++ 编译驱动器（默认会链接 C++ 标准库）
- **编译选项很多**：不确定含义时，用 `man gcc` / `man cc` 查手册

---

#### `cc/gcc` 常用选项（编译阶段/输出控制）

- `-c`：只编译（compile only），生成 `.o` **目标文件**，不进行链接
- `-g`：生成调试信息（用于 gdb 等调试器）
- `-O?`：优化级别（例如 `-O1` / `-O2` / `-O3` / `-Os` / `-Ofast`）

  - 数字越大通常优化越激进；`-Os` 侧重减小体积
- `-o output_filename`：指定输出文件名

  - 若不指定，默认可执行文件名通常为 `a.out`

---

#### `cc/gcc` 常用选项（头文件/宏/库链接）

- `-Ipathname`（大写 **I**）：把 `pathname` 加入头文件搜索路径（影响 `#include`）
- `-Dsymbol`：定义预处理宏

  - 等价于在代码里写 `#define symbol`
- `-Ldirectory`：把 `directory` 加入库搜索路径（linker 找库用）
- `-lxyz`（小写 **l**）：链接名为 `xyz` 的库

  - 通常对应 `libxyz.a`（静态库）或 `libxyz.so`（共享库）

#### 编译 hello.c（从源码到可执行文件）

- **源码文件：**`hello.c`（包含 `#include <stdio.h>`，`printf("hello, world!\n");`）
- **两步法（编译→链接）：**
  - 只编译生成目标文件：`gcc -c hello.c` → 得到 `hello.o`
  - 再链接生成可执行文件：`gcc -o hello hello.o` → 得到 `hello`
- **一步到位（编译+链接）：**
  - `gcc -o hello hello.c`
  - 或 `gcc hello.c`（不指定 `-o` 时，默认输出可执行文件名 **a.out**）

#### 链接目标文件（把多个 .o 组合成一个程序）

- **例子结构：**
  - `hello1.c`：`extern void foo();` 声明外部函数，`main()` 里调用 `foo()`
  - `sub_hello1.c`：定义 `void foo()`（例如打印 `"hello, world!\n"`）
- **正确流程：先分别编译，再统一链接**
  - 分别生成目标文件：
  
    - `gcc -c hello1.c` → `hello1.o`
    - `gcc -c sub_hello1.c` → `sub_hello1.o`
  - 链接成最终程序：
  
    - `gcc -o my_hello hello1.o sub_hello1.o`
- **关键点：**`extern` 只负责“声明我会用到 foo”，**真正的定义**在另一个 `.c` 里；链接阶段把符号（如 `foo`）对应起来。

#### 与库链接（以 sin() / libm 为例）

- **现象：**`triangle.c` 即使 `#include <math.h>`，直接 `gcc -o tri triangle.c` 仍可能报
`undefined reference to 'sin'`（头文件只是声明，函数实现还在库里）
- **解决：链接数学库 libm**
  - `gcc -o tri triangle.c -lm`
  - 运行后得到类似输出：`sine 45 = 0.707106`
- **库从哪里找：**
  - 编译器通常在 `/usr/lib`（或如 `/usr/lib/i386-linux-gnu` 等架构相关目录）寻找库文件（如 `libm.a` / `libm.so`）
  - 若库不在默认路径：用 `-Ldirectory` 增加搜索目录
  
    - 例如：`gcc ... -L/some/path -lm`
- **命名规则：**`-lxyz` 会链接 `libxyz.a`（静态）或 `libxyz.so`（动态/共享）

gdb ——GNU debugging

#### Source Code Debugging

- **编译时带调试信息**：`gcc -g ...`（生成可被调试器读懂的符号信息）
- **启动调试器**：`gdb tri`（也可用带 GUI 的 `ddd`）
- **常用调试流程（对应示例）**
  - 看源码：`(gdb) list`
  - 下断点：`(gdb) br 8`（在第 8 行停住）
  - 运行程序：`(gdb) run`
  - 查看变量：`(gdb) print value`
- **单步与定位**
  - 单步执行（不进入函数内部）：`(gdb) next`
  - 再查看变量：`(gdb) print value`
  - 看调用栈位置：`(gdb) where`
- **帮助与退出**
  - 查看帮助分类：`(gdb) help`（也可 `help all` / `help <命令>`）
  - 退出：`(gdb) quit`（若程序仍在跑，会提示是否强制退出）

在查看`history`的时候，重复执行xyz行的命令只需要输入`!xyz`就等价于输入这个命令

`run with arguments` 指的是输入命令(比如`./argoic 1013`)后面的参数

还有其他`gdb`命令 比如`disp angle` `p angle`缩写， 以及对应命令的快捷键（F5之类的？）

yak是什么？14.07

- 带GUI的`gdb`——`ddd`

#### Building One’s Own Library Archive

- **ar**：用来**创建 / 修改 / 解包**归档文件（archive）

  - **archive**：一个“打包文件”，里面装着一组其他文件，并保留结构，之后还能把单个文件取出来
  - 大型软件开发里，常把很多 `.o` **目标文件**打包成一个或多个 archive（便于管理/链接）
- **ranlib**：为 archive **生成索引**（index），让链接器更快找到需要的符号（函数/变量）

#### Other Tools for Developing Software

- **as**：汇编器（assembler），把汇编代码（`.s/.S`）转换成目标文件（`.o`）
- **lex**：生成**词法分析**程序（lexical analyzer）

  - 会生成用于**字符输入词法处理**的 C 代码
  - 常作为 **yacc** 的前端（配合使用）
  - GNU 版本叫 **flex**
- **yacc**：语法分析器生成器（yet another compiler-compiler）

  - 根据一组**文法规则（grammar rules）**生成编译器的**语法解析（parsing）**部分
  - GNU 版本叫 **bison**

**lex/flex - 像切菜**

**你要做什么：** 把一串字符切成有意义的"词"

**怎么做：**

1. 你告诉 lex："看到连续数字就叫它'数字'，看到 + 就叫它'加号'"
2. lex 生成一个程序，像传送带一样从左到右扫描
3. 每次识别出一个词，就贴上标签扔出来

**例子：**

输入: "123 + 456"

lex 工作: 看到 1...2...3(停)空格(跳过)看到+(停)空格(跳过)看到 4...5...6(停)

输出: <span>

数字:123

</span>

 <span>

加号

</span>

 <span>

数字:456

</span>



---

**yacc/bison - 像搭积木**

**你要做什么：** 检查这些"词"的组合是否合理，并理解它的意思

**怎么做：**

1. 你告诉 yacc："数字+数字 = 表达式，可以计算"
2. yacc 拿到 lex 切好的词，像玩拼图一样往上摞
3. 摞的过程中按规则计算结果

**例子：**

输入词: <span>

数字:3

</span>

 <span>

加号

</span>

 <span>

数字:5

</span>



yacc 的脑子:

"看到数字 3" → 放进盒子

"看到加号" → 记住要做加法

"看到数字 5" → 放进盒子

"哦！这是 数字+数字，符合规则" → 计算 3+5=8

输出: 8

---

**更直白的比喻**

**lex** = 超市收银员扫条码

- 哔哔哔地识别每件商品："这是苹果、这是牛奶、这是面包"

**yacc** = 收银系统算账

- "哦，3个苹果每个5块，牛奶打折，总共..."
- 检查你是否按对了组合（比如优惠券能不能和折扣同时用）

#### make Overview

- **make / gmake**：自动判断哪些源文件需要**重新编译**和/或**重新链接**，只做必要的部分（增量构建）。
- **构建规则来源**：从 **makefile / Makefile** 读取“怎么编译、怎么链接”的规则与依赖关系。
- **还能做什么**：除了 build，也常用来执行 **install / uninstall** 等其它命令（写在 makefile 里）。
- **小建议**：从已有的 makefile 模板开始改，会比从零写更快、更不容易出错。

#### makefile Rules

- **规则基本格式**
  - `target: dependencies ...`
  - 下一行（**必须以 Tab 开头**）写要执行的 `commands ...`
  - 含义：要生成/更新 **target**，先保证 **dependencies** 都是最新，然后执行命令。
- **举例**
  - `myapp1: srcfile1.o srcfile2.o srcfile3.o`
    - 目标：生成可执行文件 `myapp1`
    - 依赖：三个 `.o`
    - 命令：`gcc -o myapp1 srcfile1.o srcfile2.o srcfile3.o -lm`
  - `srcfile1.o: srcfile1.c myinclude.h`（2/3 同理）
  
    - 目标：生成 `srcfile1.o`
    - 依赖：源文件 + 头文件
    - 命令：`gcc -c srcfile1.c`（编译成 `.o`，不链接）
  - `clean:`
    - 常见“伪目标”，用来清理产物：`rm -f myapp1 ...`
- **依赖图（dependency graph）可以这样画**
  - `myapp1`
  ↳ `srcfile1.o` ↳ `srcfile1.c`, `myinclude.h`
  ↳ `srcfile2.o` ↳ `srcfile2.c`, `myinclude.h`
  ↳ `srcfile3.o` ↳ `srcfile3.c`, `myinclude.h`
  - `clean`（独立目标，不依赖上面这些）
- **make 的关键效果**
  - 如果只改了 `myinclude.h`：三个 `.o` 都会重编译，然后再重新链接 `myapp1`
  - 如果只改了 `srcfile2.c`：只会重编 `srcfile2.o`，然后重新链接 `myapp1`

#### Makefile 里的宏（变量）与内置符号

- **变量/宏**：用来简化重复书写，例如：

```makefile
OBJS=srcfile1.o srcfile2.o srcfile3.o
myapp1: $(OBJS)
    $(CC) -o myapp1 $(OBJS) -lm
```

- **预定义变量（make -p 可查看）**：

  - `CC`(C 编译器), `CXX`(C++ 编译器), `CFLAGS`(编译选项), `LDFLAGS`(链接选项), `LDLIBS`(库，如 `-lm`) 等。
- **后缀规则（Suffixes）**：make 内置一些“从 `.c` 生成 `.o`”的默认规则；`$<` 常表示触发规则的那个依赖文件（如 `.c`）。
- **特殊内部宏**：

  - `$@`：当前目标名（target）
  - `$*`：当前目标去掉后缀的“基名”
  - `$<`：第一个依赖文件名
  - `$?`：比目标更新的依赖列表

\ back slash 代表换行 取消特殊含义 去行

按照依赖触发深度优先搜索，保证目标是最新的

#### make Command Line Options

- 基本用法：`make [options]`
- `-f filename`：指定使用的规则文件（不用默认的 `makefile/Makefile`）
- `-n`：只打印将要执行的命令，不真正执行（预览/排错）
- `-p`：打印完整的宏定义与目标/规则信息（查看 make 内置/当前环境）

---

#### touch

- 用法：`touch filename`
- 作用：更新文件的“修改时间戳”
- 和 make 的关系：**make 依据时间戳判断是否需要重编译**，所以常用 `touch` 来“强制触发”某些目标重新构建（re-make）

---

#### Real Example of makefile

- 典型结构：**变量定义 + 目标规则 + 模式规则 + clean**
- 变量示例（把编译参数集中管理）：

  - `LIB`：库路径/库（如 `-L... -lX11 -lm`）
  - `INC`：头文件搜索路径（如 `-I...`）
  - `INCFILE`：头文件集合
  - `SOURCE`：源文件集合
  - `OBJ = $(SOURCE:%.c=%.o)`：把 `.c` 映射为 `.o`
- 目标示例：

  - `draw: $(OBJ)`：链接生成可执行文件（`$@` 表示目标名）
- 模式规则示例：

  - `%.o: %.c`：把每个 `.c` 编译成对应 `.o`（`$<` 表示第一个依赖）
- `clean`：删除产物（如 `*.o`、可执行文件）

##### 脚本解释

LIB = -L /usr/lib/x86_64-linux-gnu -lX11 -lm

INC = -I /usr/include/X11 -I ./include

INCFILE = all.h draw.h global.h

SOURCE  = main.c init.c readline.c toview.c translate.c \

cast.c drawline.c draw_guide.c

OBJ = $(SOURCE:%.c=%.o)

draw: <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mo stretchy="false">

(

</mo>

<mi>

O

</mi>

<mi>

B

</mi>

<mi>

J

</mi>

<mo stretchy="false">

)

</mo>

<mi>

g

</mi>

<mi>

c

</mi>

<mi>

c

</mi>

<mo>

−

</mo>

<mi>

g

</mi>
</mrow>

<annotation encoding="application/x-tex">

(OBJ)
gcc -g

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

<span className="mord,mathnormal" style="margin-right:0.0278em;">

O

</span>

<span className="mord,mathnormal" style="margin-right:0.0502em;">

B

</span>

<span className="mord,mathnormal" style="margin-right:0.0962em;">

J

</span>

<span className="mclose">

)

</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

g

</span>

<span className="mord,mathnormal">

cc

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
<span className="strut" style="height:0.625em;vertical-align:-0.1944em;">



</span>

<span className="mord,mathnormal" style="margin-right:0.0359em;">

g

</span>
</span>
</span>
</span>

(OBJ) <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mo stretchy="false">

(

</mo>

<mi>

L

</mi>

<mi>

I

</mi>

<mi>

B

</mi>

<mo stretchy="false">

)

</mo>

<mo>

−

</mo>

<mi>

o

</mi>
</mrow>

<annotation encoding="application/x-tex">

(LIB) -o

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

<span className="mord,mathnormal">

L

</span>

<span className="mord,mathnormal" style="margin-right:0.0785em;">

I

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

−

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.4306em;">



</span>

<span className="mord,mathnormal">

o

</span>
</span>
</span>
</span>

@

%.o: %.c

gcc -g -c <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mo stretchy="false">

(

</mo>

<mi>

I

</mi>

<mi>

N

</mi>

<mi>

C

</mi>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

(INC)

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

<span className="mord,mathnormal" style="margin-right:0.0785em;">

I

</span>

<span className="mord,mathnormal" style="margin-right:0.109em;">

N

</span>

<span className="mord,mathnormal" style="margin-right:0.0715em;">

C

</span>

<span className="mclose">

)

</span>
</span>
</span>
</span>

< -o $@

clean:

rm -f *.o

rm draw

---

`LIB = -L ... -lX11 -lm`

- **作用**：告诉链接器去哪里找库、并链接哪些库。

  - `-L /usr/lib/x86_64-linux-gnu`：把这个目录加入“库搜索路径”
  - `-lX11`：链接 `libX11.so`（或 `libX11.a`）
  - `-lm`：链接数学库 `libm.so`（sin/cos 等函数都在这里）

> 直觉：`LIB` 是“链接阶段”才用的东西。

##### `INC = -I ...`

- **作用**：告诉编译器去哪里找头文件。

  - `-I /usr/include/X11`：让 `#include <X11/...>` 找得到
  - `-I ./include`：让 `#include "xxx.h"` 在项目的 `include/` 下也能找到

> 直觉：`INC` 是“编译阶段（.c -> .o）”才用的东西。

`INCFILE = all.h draw.h global.h`

- **作用**：列出一些头文件名（用于表达依赖关系很常见）。
- **但注意**：这个版本里，`INCFILE` **只是定义了**，并没有在规则里写成依赖（例如没有 `$(OBJ): $(INCFILE)` 这种），所以它**目前不会直接影响 make 是否重编译**。

`SOURCE = main.c ...`

- **作用**：列出所有参与编译的 `.c` 源文件。

`OBJ = $(SOURCE:%.c=%.o)`

- **作用**：把 `SOURCE` 里的每个 `.c` **批量替换**成对应的 `.o`。
- 这是 make 的“模式替换”写法：

  - `main.c` → `main.o`
  - `init.c` → `init.o`
  - …以此类推
- 所以 `OBJ` 最终就是：`main.o init.o readline.o ... draw_guide.o`

---

目标规则 draw：最终把一堆 .o 链接成可执行文件

`draw: $(OBJ)`

- **含义**：目标是 `draw`，它依赖于 `$(OBJ)` 里所有 `.o` 文件。
- **make 的核心规则**：

  - 如果 `draw` 不存在 → 必须生成
  - 如果某个依赖 `.o` 不存在 → 必须先生成那个 `.o`
  - 如果某个依赖 `.o` 比 `draw` 更新（时间戳更“新”）→ 重新链接 `draw`

`gcc -g $(OBJ) $(LIB) -o $@`

- 这一行是“生成 draw 的命令”（**链接阶段**）。
- `gcc -g ...`：带调试信息（方便 gdb）
- `$(OBJ)`：所有目标文件一起参与链接
- `$(LIB)`：把 X11 库、数学库等链接进来
- `-o $@`：输出文件名是 `$@`
  - `$@` 是 make 的自动变量：**当前规则的目标名**
  - 在这里 `$@` 就是 `draw`

> 所以这一条命令大致等价于：
> `gcc -g main.o init.o ... draw_guide.o -L... -lX11 -lm -o draw`

---

模式规则 `%.o: %.c`：教 make “任何 .c 怎么编译成 .o”

##### `%.o: %.c`

- **含义**：任意 `xxx.o` 依赖 `xxx.c`
- 当 make 发现它需要 `main.o`，就会套用这个规则，自动得到：

  - `main.o: main.c`
  同理 `init.o: init.c` …

##### `gcc -g -c $(INC) $< -o $@`

- 这一行是“生成 .o 的命令”（**编译阶段**）。
- `-c`：只编译不链接（输出 `.o`）
- `$(INC)`：加上头文件搜索路径
- `$<`：make 自动变量：**第一个依赖文件**
  - 在 `main.o: main.c` 里，`$<` 就是 `main.c`
- `$@`：目标文件名

  - 在 `main.o: main.c` 里，`$@` 就是 `main.o`

> 所以对 `main.o` 来说，这行等价于：
> `gcc -g -c -I/usr/include/X11 -I./include main.c -o main.o`

##### `clean:`

- 这是一个“伪目标”（一般会额外写 `.PHONY: clean`，但你图里没写也能用）
- 运行 `make clean` 时会执行下面的 rm

##### `rm -f *.o`

- 删除所有 `.o` 文件（中间产物）

##### `rm draw`

- 删除最终可执行文件 `draw`

---

###### make 真正“执行顺序”

假设你执行：

- `make`（默认目标通常是 Makefile 里出现的第一个目标，这里是 `draw`）
- 或 `make draw`

make 会做这样的事（按依赖自动推导）：

1. 目标：`draw`
2. 发现 `draw` 依赖：`main.o init.o ...`
3. 逐个检查这些 `.o`：

  - 若某个 `.o` 不存在 → 用 `%.o: %.c` 编译它
  - 若某个 `.o` 旧了（对应 `.c` 更新了）→ 重新编译它
4. 所有 `.o` 都最新后 → 执行链接命令生成/更新 `draw

---

#### Running and Learning More

- 常见运行方式：

  - `make`（默认目标，通常是第一个目标）
  - `make draw`（指定构建某个目标）
  - `make clean`（清理）
- 核心概念：make 会根据 **dependency graph（依赖图）** 做构建顺序安排（可理解为深度优先地满足依赖）
- 延伸：

  - 进一步阅读：Makefile 相关文档/百科
  - 其他构建工具：bazel、MSBuild、sbt 等

小任务`demo_code.zip`里面的makefile还要再看看

`gcc -I include -M main.c`

#### Source Code Version Control（源代码版本控制）

1. **为什么需要版本控制（Why version-control?）**

- **多人协作开发**（Multi-programmers working together）
- **记录历史版本**（History recording）
- **按不同需求创建代码分支**（Code branches for various demands）

1. **版本控制工具类型（Version control tools）**
  - **本地数据模型（Local data model）**
    - **SCCS**：Source Code Control System
    - **RCS**：Revision Control System
  - **客户端-服务器模型（Client-server model）**
    - **CVS**：Concurrent Versioning System
    - **tkcvs**：CVS 的 GUI 工具（tkcvs with GUI）
  - **分布式模型（Distributed model）**
    - **git**：开发者拥有自己的本地仓库（developer has own local repository），修改可以共享（changes can be shared）

##### Functions of a Version Control Tool | 版本控制工具的功能

1. **基础功能（Basic）**
  - **维护文件版本记录**（Maintain a record of versions of a file）
  - **可恢复旧版本**（Old versions can be recovered）
  - **可同时维护多个不同版本**（Different versions can be maintained simultaneously）
  - **支持文件/分支的签入/签出**（Checkin/checkout files/branches）
2. **高级功能（Advanced）**
  - **为每个用户提供视图/工作区**（Viewport for each user）
  - **分支管理**（Branch management）
  - **项目管理**（Project management），例如：
  
    - **差异比较**（diff）
    - **合并**（merge）
    - **等**（etc.）
3. **学习建议（Tips）**
  - **运行并学习**：`man gittutorial`（'man gittutorial' and follow it?）
  - **去 GitHub 学习入门介绍**（Visit github to learn some introductions）
