# System Development Tools

> 系统开发工具

### C/C++ Program Developing Flow

- **预编译阶段**：c 文件生成 i 文件。`gcc -E 源文件 -o 要生成的文件名`
  - 如：`gcc -E text.c -o text.i`
  - `.i`仍然是文本文件，里面是展开后的 C 源码（非常长）
  - 预编译进行**宏替换、注释删除以及头文件展开**等工作 `E = Preprocess only`
- **编译阶段**：i 文件生成 s 文件。

  - 如：`gcc -S text.i`，默认输出为 `text.s`，也可以直接`gcc -S text.c`，gcc 会自动先预处理再编译
  - `text.s`：汇编文本文件，人可读（但较难）
  - 编译进行目标代码生成与优化、语法语义分析等，**将源代码翻译成汇编**
- **汇编阶段**：s 文件生成 o 文件

  - 如：`gcc -c text.s`，默认输出为 `text.o`，也可以直接`gcc -c text.c`，gcc 自动预处理+编译+汇编，停在 .o
  - `text.o`：目标文件objective（二进制），不可直接运行（通常还需要“拼装”）
  - 汇编生成各段和符号表，将汇编指令翻译成二进制格式
- **链接阶段**：o 文件生成 out 文件

  - 如：`gcc text.o`编译所有 c 并链接，`gcc **.c -o 可执行文件名`。默认输出为 `a.out`
  - 链接的主要内容就是**把各个模块之间相互引用的部分都处理好**，使得各个模块之间能够正确的衔接
  - 链接可以分为静态链接和动态链接。相应的也有静态库和动态库来供链接使用

> - `.a` 是静态库文件，靠 `.o` 文件生成，本质是把`.o` **打包**在一起（**a**rchive）作为一个库为外部程序提供函数、接口。相当于好多个 `.o` 合在一起，程序更独立但是体积大
> - `.so`是动态库文件，链接时，可执行文件里只记录“要用某个库的某些符号”。运行时，系统的动态链接器把 `.so` 加载到内存再把调用地址对应起来，程序体积变小但是依赖环境

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ICCAD/SystemDevelopmentTools-01.webp)

### Suffix Naming Convention

- `.sh/.bash/.csh` #Shell Script
- `.c/.cpp/` /`.h/.hpp` #C/C++ Source/Header File
- `.py` #Python Script
- `.java` #Java Source File
- `.o` #Object File，gcc -c之后生成的目标文件
- `.s` #Assembly Source File，汇编文件
- `.a` #Library (static)，静态库
- `.so` #Dynamic-linking Library (shared object)，动态库
- `.f` #Fortran Source File
- `.pl` #Perl Script perl 脚本
- `.tcl` #TCL/TK Script

  - **怎么运行：**
    - 常见：`tclsh xxx.tcl`（命令行解释器）
    - 或 GUI：`wish xxx.tcl`（带 Tk 界面）
- `.scala` #Scala Source File
- 后缀在 Linux 中只是标注功能，本质上 Linux 中只有文件的概念，这些都没有区别

### gcc Options

- `gcc` # GNU C Compiler

  - `-c` # 只编译，不 Link，产生 `.o` 文件
  - `-g` # 可调试的编译
  
    - 默认编译生成的可执行文件是无法使用 `gdb` 来跟踪或调试的，因为可执行程序中没有可供 `gdb` 调试使用的特殊信息；为了将必要的调试信息整合到可执行文件中，我们便需要用到 `-g` 选项
  - `-O?` # 进行编译优化，级别越高效果越好，时间越长
  
    - `-O1`, `-O2`, `-O3`, `-Os`, `-Ofast`
    - 可以选择一级、二级、三级、空间优化、速度优化等
  - `-o output_filename` # 指定输出文件名称，默认为 `a.out`
  - `-Ipathname` # 指定额外的头文件搜索路径
  
    - 如：`gcc -I ./inc/ main.c add.c`，就添加了路径
  - `-Dsymbol` # 定义宏 `symbol`，等价于 `#define symbol`
    - `gcc -Dsymbol` 直接跟宏名，相当于定义这个宏，默认这个宏的内容是 `1`
    - `gcc -DNAME=value` 表示定义宏，它的内容是 `value`
  - `-Ldirectory` # 指定额外的函数库搜索路径
  - `-lxyz` # 链接时搜索指定具体的函数库
  
    - 如：`gcc -o hello hello.c -I /home/hello/include -L /home/hello/lib -lworld`
    - `-I /home/hello/include` 表示将 `/home/hello/include` 目录作为第一个寻找文件的目录，寻找的顺序是：`/home/hello/include --> /usr/include --> /usr/local/include`
    - `-L /home/hello/lib` 表示将 `/home/hello/lib` 目录作为第一个寻找库文件的目录，寻找的顺序是：`/home/hello/lib --> /lib --> /usr/lib --> /usr/local/lib`
    - `-lworld` 表示在上面的 lib 的路径中寻找 `libworld.so` 或 `libworld.a` 文件
- 三种生成可执行文件的方法

  - 第一种：compile 和 link 是分开的。`-c` 为 compile only，第二步为链接，生成可执行文件
  
    - `gcc -c hello.c`
    - `gcc -o hello hello.o`
  - 第二种：一下子写出，编译和链接一起进行
  
    - `gcc -o hello hello.c`
  - 第三种：没有用 `-o` 来指示，且输入为 `.c` 文件，就直接生成 `a.out`
    - `gcc hello.c`

### Source Code Debugging

- gdb

  - `list` #列出源代码
  - `br n` #在第 n 行设置断点`br=break`
    - `run` #运行文件
    - `print x` #打印变量 x
    - `next` #运行下一行
    - `where` #显示正在运行的函数和行数
    - `help` #显示可用命令
    - `quit` #退出
    - 如果想要 debug，就要在编译时加上 `-g`

### Building One’s Own Library Archive

- `ar`  **(**archive) #从档案中创建/修改/提取。多个 `.o` 文件打包就是 `.a` 静态库文件

  - `-r` 将文件插入库中
  
    - 如：`ar -r liba.a b.o`，就可以将 `b.o` 插入 `liba.a` 中
  - `-x`：从库文件中取出成员文件
  
    - `ar -x liba.a b.o` 表示从库中解出 `.o` 文件
  - `-d`：删除库文件中的成员文件
- `ranlib` #产生档案的索引

  - ranlib 的意思是生成的打包的索引。有索引的话，一旦有外部链接，就很容易连上，访问很快
  - `ranlib + a` 文件

### Other Tools for Developing Software

- `as` #汇编语言

  - as 的意思为 assembler，集合聚集的意思，为汇编语言的编译器
  - 汇编语言为 `.s` 后缀，可以通过 `as` 命令链接为 `.o` 文件
- `lex` #生成一个与输入流的简单语法分析相匹配的 C 或 C++ 语言程序

  - lex 是词法编译器，生成的代码可以用来解析语言
- `yacc` #通过一组语法规则产生编译器的解析部分

  - 写好语法规则后，输给 yacc 后就会生成一段 c 语言代码，到时候可以调用作为解析语言，比如分析输入 c 语言的语法规则，为语法分析器
  - yacc 作为语法分析器可以调用词法分析器 lex

### make Overview

- make/gmake #一个可以自动判断需要编译或链接的源文件的工具
  - make 开发工具用于自动管理源代码的编译和链接；
  - make 本身并不知道这些源代码之间是什么关系，我们要写描述文件关系的文件 makefile；
- makefile Rules

```text
target: depencies...
  commands...
```

- makefile 规则非常简单，格式为“依赖于” + “命令”。dependencies 里面的东西如果比 target 新的话，那就触发下面的 command 动作

### make Command Line Options

- make <span>

options

</span>


  - `-f filename` #当文件名不为 makefile 时，从该文件中读入 makefile，use filename as makefile
  - `-n` #打印命令，但不执行
  - `-p` #打印完整的宏定义和目标描述

### Using Macros (Variables) in makefile

- Macros 意思为宏，可以理解为 makefile 中的变量
- 在 makefile 中引用变量使用 `$` 符号
- Predefined Macros，预先定义好的宏

  - `AS` – assembler (as) #汇编
  - `CC` – C compiler command (cc) #C 编译命令
  - `FC` – Fortran compiler command (fc) #公式编译命令
  - `CPP` – C++ preprocessing command (`$(CC) -E`) #C++ 预处理命令
  - `CXX` – C++ compiler command (g++) #C++ 编译命令
  - `CFLAGS` – C compiler option flags (e.g. `-g`) #C 编译可选标志
  - `FFLAGS` – Fortran compiler option flags (e.g. `-g`) #公式编译可选标志
  - `LDFLAGS` – Linking option flags (e.g. `-L /usr/share/lib`) #链接可选标志
  - `LDLIBS` – Linking libraries (e.g. `-lm`) #链接目录
- 可以用 `make -p` 来查看哪些变量已经预先定义过了

### Special Internal Macros

- `$(TARGET)`: file1.o file2.o file3.o

  - `$@` 目标文件，即 `$(TARGET)`
  - `$^` 表示所有的依赖文件，即 `file1.o file2.o file3.o`
  - `$<` 表示第一个依赖文件，即 `file1.o`
  - `$?` 表示比目标还要新的依赖文件列表
  - `$*` 当前任务的基名，即不包括后缀

> `$?` **只包含那些比目标更新的依赖**；只有在**目标不存在**时，`$?` 才会变成“整个依赖列表”。

### touch

- `touch filename`
  - 实现 remake，update the access and modification times of each file to the current time
  - touch 文件后会更新时间，就可以重新触发 makefile

### Source Code Version Control - git

- `git init`
  - 初始化 git 目录后，当前目录就会成为本地仓库
  - 可以使用命令将新建文件添加到本地仓库
- `git add` / `git commit`
  - add 将文件添加到缓存区，commit 用于提交到本地仓库
  - 如创建 `test.txt` 后，可以 `git add test.txt` 将文件添加到本地仓库缓存
  - 但是这还不算添加到本地仓库，需使用 `git commit` 才能将其最终提交
  - 关于仓库和缓存区，将马上在后面阐述
- `git log`
  - log 用于查看日志
- git 基本组成框架：Workspace、Index / Stage、Repository、Remote

  - Workspace：开发者工作区，也就是当前写代码的目录
  - Index：暂存区/缓存区。它用来存放临时动作，比如我们做了 `git add` 或者 `git rm`，都是把文件提交到缓存区，这是可以撤销的，然后再通过 `git commit` 将缓存区的内容提交到本地仓库
  - Repository：仓库区（或本地仓库）是仓库代码，所有的提交都在这里，git 会保存好每一个历史版本，存放在仓库区
  - Remote：远程仓库，即服务器仓库
- `git remote add origin` `<remote-url>`
  - 该命令可以把 github 本地仓库关联到远程仓库，`origin` 是 github 上的仓库名称，意思是远程仓库的意思
- git 将远仓库代码拉取到本地：`git clone` / `git pull`
  - 当我们远程有仓库时，想要关联到本地只需要使用 `git clone` 就可以了
  - pull 也是一样的，两个的略微区别在最后会阐述
- github 提交本地代码到远程仓库：`git add`、`git commit`、`git push`
  - 修改了本地代码后，使用 `git add` 提交到缓存区，再使用 `commit` 提交到本地仓库，最后使用 `push` 推送到远程就可以了
- git 各种操作总结

  - add 将文件添加到缓存区
  - commit 用于提交到本地仓库
  - `commit -a`：加了 `-a`，在 commit 的时候，能帮你省一步 `git add`，但也只是对修改和删除文件有效，新文件还是要 `git add`
  - pull **必须连接远程仓库才能用**，有权限时可以下载完整代码
  - push 推送到远程。pull 完后及时 push，才能保证两次 pull 互不干扰
  - clone：**没有权限的仓库**，也可以获得代码

## Perl
