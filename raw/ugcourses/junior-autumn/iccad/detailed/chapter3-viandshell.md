# Chapter 3：Vi and Shell

> Vi 编辑器与 Shell：详细版笔记

## vi

---

### Editors

- 编辑器：允许用户交互地编辑纯文本文件的程序。
- 常见平台与工具：

  - MSDOS：`edlin`, `edit`（仍可在 `C:\Windows\System32` 找到）。
  - MS Windows：`notepad`, `wordpad`。
  - Unix 早期：`ed`, `vi`，之后有增强版 `vim`。
  - 更高级使用：GNU `emacs`。
  - 其他：`xedit`, `gedit`, `nano`, `pico`。
- 文字处理软件（带排版功能）：

  - `WordStar`, `MSWord`, `Framemaker`, `Acrobat` 等。
  - `StarOffice`, `OpenOffice`, `LibreOffice` 等。

---

### vi Modes

- vi 有两大基本模式：

  - **Command Mode（命令模式）**：
  
    - 启动时默认处于命令模式。
    - 每个按键都被当成编辑命令，而不是文本输入。
    - 输入冒号 `:` 进入命令行模式，如 `:help`。
  - **Insert Mode（插入模式）**：
  
    - 用于输入文本。
    - 通过执行各种插入类命令进入（如 `i`, `a`, `o` 等）。

---

### Sample vi Edit Session

- 基本编辑流程示例：

  1. 在命令行输入：`vi tmp.txt` 打开文件。
  2. 启动后处于 Command Mode。
  3. 按下“追加”类命令键（如 `a`，在光标后开始输入）。
  4. 进入 Insert Mode，输入文本内容。
  5. 按 `ESC` 返回 Command Mode。
  6. 输入 `:wq` 回车，保存并退出。
- 示例中展示了在 vi 中输入多行文本、以 `:wq` 结束编辑的流程。

---

### Easier Ways for Practicing

- 推荐使用 **vim 教学工具**：

  - 命令：`vimtutor`。
- 先了解有图形界面的 vi 与纯文本 vi 的差异：

  - GUI 版：`gvim`（GNU 版），可用命令例如：
  - sudo apt-get install vim-gnome
  - 课程建议：优先熟悉 **文本界面 vi/vim**，更通用。

---

### Cursor Movement (1)

- 光标移动方式：

  - 可用方向键（依终端而定）。
  - 使用 `h`, `j`, `k`, `l` 作为替代：
  
    - `[n] h`：向左移动 n 个字符。
    - `[n] j`：向下移动 n 行。
    - `[n] k`：向上移动 n 行。
    - `[n] l`：向右移动 n 个字符。

---

### Cursor Movement (2)

- 以屏为单位的移动：

  - `^F`：前进一屏（Forward）。
  - `^B`：后退一屏（Back）。
  - `^D`：向下移动半屏。
  - `^U`：向上移动半屏。
- 以行号或行内位置移动：

  - `G`：移动到文件最后一行。
  - `[n] G`：移动到第 n 行；若不带 n，则到最后一行。
  - `$`：移到当前行行尾。
  - `^`：移到当前行第一个非空白字符。
  - `0`：移到当前行开头（列 0）。
- 以单词为单位移动：

  - `[n] w`：向前移动 n 个单词开头。
  - `[n] b`：向后移动 n 个单词开头。
  - `e`：移动到当前或下一个单词结尾。

---

### Cursor Movement by Matching

- 按字符/模式匹配移动：

  - `f <char>`：在当前行向前找到下一个 `<char>` 并移动到那里。
  - `/ pattern`：向下搜索 pattern，并把光标移动到匹配位置。
  - `? pattern`：向上搜索 pattern。
  - `n`：重复上一次搜索，继续找下一个匹配。
  - `N`：重复上一次搜索，反向搜索。
  - `%`：在括号、花括号等成对符号间跳转匹配。

---

### Inserting Text

- 文本插入/追加命令：

  - `i`：在光标前开始插入。
  - `a`：在光标后开始追加。
  - `I`：在当前行行首（文本开始位置）插入。
  - `A`：在当前行行尾追加。
  - `o`：在当前行下方新开一行，并进入插入模式。
  - `O`：在当前行上方新开一行，并进入插入模式。

---

### Deleting Text

- 删除行与单词：

  - `dd`：删除当前整行。
  - `[n] dd` 或 `d [n] d`：删除连续 n 行。
  - `[n] dw`：删除 n 个单词。
- 删除到行尾：

  - `D`：从光标处删除到当前行末尾。
- 删除字符：

  - `x`：删除当前字符。
  - `[n] x`：删除光标起始的 n 个字符。
  - `[n] X`：向前删除 n 个字符（类似多次退格）。

---

### Changing Commands (1)

- 修改类命令：

  - `s` / `S`：替换字符或整行（具体行为随实现）。
  - `r` / `R`：替换字符或连续替换。
  - `c`：change（“改写”），配合移动使用：
  
    - `[n] cw`：修改接下来的 n 个单词。
    - `c$`：从光标处修改到行尾。
  - `~`：切换光标处字符大小写。
  - `J`：将当前行和下一行合并为一行。
  - `u`：撤销上一次操作。
- 幻灯片提出问题：如何 redo（重做）？（后续通过 `.` 或其他机制实现）。

---

### Changing Commands (2)

- 重复和拷贝相关：

  - `.`：重复上一次“修改类”操作。
  - `[n] yy` 或 `y [n] y`：将 n 行“yank”（复制）到缓冲区。
  - `[n] yw`：复制 n 个单词到缓冲区。
  - `p`：在光标之后粘贴 yank 或删除的内容。
  - `P`：在光标之前粘贴。
  - `v` / `V`：可视模式，结合 `y` / `x` / `p` 做可视选择复制/删除/粘贴。
  - 文本缓冲区中存在默认缓冲与命名缓冲。
  - 示例组合：`4dd10jp`（删除 4 行并在第 10 行之后粘贴等）。

---

### Command Line Mode

- 通过输入冒号 `:` 进入命令行模式。
- 常用行范围标记：

  - 单个行号：`20`。
  - 行号范围：`1,5`。
  - `.`：当前行。
  - `$`：最后一行。
  - `%`：相当于 `1,$`（整个文件）。
  - `+`、`-`：表示相对行，比如 `+5`、`-10`、`$-3` 等。

---

### File Manipulation

- 写文件相关：

  - `:[n1,n2]w[>>][file]`：将范围内的文本写入文件，可选择追加。
  - `:wq`：写入并退出。
  - `:w!`：强制覆盖原文件。
- 退出相关：

  - `:q`：在无修改时退出。
  - `:q!`：不保存修改直接退出。
- 其他：

  - `:![cmd]`：执行外部 shell 命令。
  - `:r [file]`：在光标处读入另一个文件的内容。

---

### Configuring vi Session

- 使用 `:set` 配置 vi 行为：

  - `:set all`：显示所有当前配置项。
  - `:set ignorecase`：搜索时忽略大小写。
  - `:set number`：显示行号。
  - `:set nonumber`：关闭行号显示。
  - 示例：
  - <set>
  
  
  
  </set>
  
   nu
  <set>
  
  
  
  </set>
  
   nonu
- 其他常用选项包括：`wrap`（是否折行）、`indent`（缩进）等。

---

### Line Manipulation

- 行定位：

  - `:number`：跳转到指定行。
- 行移动与复制：

  - `:n1,n2mn3`：将 n1～n2 的行移动到 n3 行之后。
  - `:n1,n2tn3` 或 `:n1,n2copy n3`：复制行到 n3 之后。
- 删除：

  - `:n1,n2d`：删除范围行。
  - 示例：
  
    - `:.,$-2d`：从当前行到倒数第 2 行删除。
    - `:1,.d`：删除从第 1 行到当前行。

---

### Substitution

- 替换命令基本格式：

  - `:[Addr]s/old-expr/new-string/[g]`
- 示例：

  - `:s/hte/the/g`：当前行将所有 `hte` 换成 `the`。
  - `:2,30s/use/used`：第 2～30 行将 `use` 换成 `used`。
  - `:1,$s/Oct\./Nov.`：整个文件将 `Oct.` 换成 `Nov.`。
  - `:%s/Oct\./Nov./g`：同样是全文件替换、并加 `g` 做每行全局替换。

---

### Regular Expression Syntax (1)

- 正则表达式（Regular Expressions, RE）：

  - 用于在文本中做模式匹配。
  - 由普通字符和特殊字符（元字符）组成。
  - 与 Shell 中匹配文件名的通配符不同（后续专门区分）。

---

### Meta-Characters as Wild Cards

- 通配符元字符用于 **命令行中文件名匹配**：

  - `?`：匹配任意单个字符。
  - `*`：匹配任意长度（0 个或更多）的字符串。
  - `[abc...]`：匹配括号中任一字符。
  - `[a-e]`：匹配 a～e 之间任一字符。
  - `[!def]`：匹配不在 d,e,f 中的字符（`sh/bash`）。
  - `{abc,bcd,cde}`：匹配集合中任一串（`bash/csh`，逗号分隔且无空格）。
  - `~`：当前用户家目录（`bash/csh`）。
  - `~user`：指定用户的家目录（`bash/csh`）。

---

### Where Are They Being Used?

- 通配符元字符主要用于：

  - Shell 命令涉及文件名时的匹配。
- 正则表达式（REPs）中的元字符主要用于：

  - 文本工具：`grep`, `sed`, `awk` 等。
  - vi 中：
  
    - `/` 和 `?` 搜索命令。
    - `:s` 替换命令。
  - 脚本语言：Tcl、Perl、Python 的正则模块等。
- 示例应用：

  - 查找单元名字以 `CLK` 或 `clk` 开头的标准单元名。
- 结论：**通配符与正则表达式不是同一套东西**。

---

### Regular Expression Syntax (2)

- 正则表达式的三种基本形式：

  - **Anchors**（锚定）：绑定到行的特定位置。
  - **Character sets**（字符集）：在某位置匹配一个字符。
  - **Modifiers**（修饰符）：指定前一个表达式重复次数。
- 正则表达式可以组合，构成更长的模式。

---

### Regular Expression Syntax (3)

- 常用元字符：

  - `.`：匹配除换行外任意单个字符。
  - `*`：匹配前一个表达式的 0 次或多次重复。
  - `[abc]`：匹配任一括号内字符。
  - `[a-d]`：匹配 a～d 范围内的任一字符。
  - `[^abc]`：匹配**不在**集合中的任一字符。
  - `^exp`：模式必须从行首开始。
  - `exp$`：模式必须在行尾结束。
  - `\`：将下一个字符“转义”为普通含义。

---

### Sample REPs and Meanings

- `cat`：匹配字符串 “cat”。
- `.at`：匹配 `cat`, `rat`, `mat`, `bat`, `fat`, `hat` 等。
- `xy*z`：匹配一个 `x`，后跟 0 个或多个 `y`，再跟 `z`。
- `^cat`：匹配行首为 “cat” 的行。
- `cat$`：匹配行尾为 “cat” 的行。
- `\*`：匹配字符 `*` 本身。
- `[cC]at`：匹配 `cat` 或 `Cat`。
- `[^a-zA-Z]`：匹配任意非字母字符。
- `[0-9]$`：匹配以数字结尾的行。
- `[A-Z][A-Z]*`：匹配一个或多个大写字母。
- `[A-Z]*`：匹配 0 个或多个大写字母（即理论上可匹配“任何东西”）。

---

### More on vi

- 多文件编辑：

  - `vi file-list`：一次打开多个文件，例如：`vi *.c`。
  - 在 vi 中：
  
    - `:n`：切换到下一个文件。
    - `:rew`：回到第一个文件。
- 显示当前编辑文件信息：

  - `:f` 或 `^G`。
- 特殊打开方式：

  - `vi -R filename`：只读方式打开。
  - `vi -r filename`：恢复模式打开（崩溃后恢复）。

---

## Shells

- Shell 位于用户和操作系统之间：

  - 作为命令解释器。
  - 读取用户输入。
  - 将命令翻译成系统动作。
- 查看当前登录 shell：

  - `echo $SHELL`。
  - `cat /etc/shells`：查看系统支持的所有 shell 列表。

---

### Shell Types

- 主要 shell 类型：

  - Bourne Shell：`sh`。
  - C Shell：`csh`。
- 基于 Bourne Shell 的：

  - `ksh`（Korn shell）。
  - `bash`（Bourne-Again Shell）。
  - `zsh`（Z Shell）。
- 基于 C Shell 的：

  - `tcsh`（T C shell）。

---

### Bourne Shell

- 特点：

  - 拥有较好的 I/O 控制功能，适合写脚本。
  - 交互性较弱，对普通用户交互不够方便。
  - 很多基于 Bourne 的 shell 在交互方面做了改进。
- 默认提示符：`$`。

---

### C Shell

- 由 Bill Joy 编写。
- 语法类似 C 语言，更适合写“类 C 风格”的脚本。
- I/O 控制不如 Bourne shell 方便。
- 交互体验相对更好：

  - 支持作业控制（job control）、命令历史（history）等。
- 默认提示符：`%`。

---

### Bourne-Again Shell

- GNU 项目开发的自由软件。
- 提供：

  - 交互式命令行编辑。
  - 支持作业控制（在支持的体系结构上）。
  - 类 csh 的历史替换、花括号扩展等特性。
- `bash`：

  - 交互特性吸收了 `csh`、`ksh` 的优点。
  - 编程语言上兼容 Bourne shell (`sh`)。
  - Linux 平台上非常常见，默认提示符通常也是 `$`。
  - 支持便捷的命令行编辑（方向键、Tab、`CTRL+L` 等）。

---

### Meta-Characters Again

- Shell 命令行中常见的特殊字符：

  - `/ \ " \` * : ; ' ^ ? ~ { } ( ) <span>
  
  
  
  </span>
  
   ~ ! $ < > | & #@% ,+=`
- 示例：

  - `ls *`：列出当前目录下所有不以 `.` 开头的文件。
  - `ls chpt[1-4]`：等价于 `ls chpt1 chpt2 chpt3 chpt4`。
  - `ls m?n`：匹配形如 `man`、`men` 的三个字符文件名。
  - `ls [a-z]*`：匹配以小写字母开头的文件（与正则不同）。
- 注意：与前面“Wild Card”部分相联系，`*`、`?` 等在 shell 中匹配文件名；`\` 用于转义，与正则中的用法类似。

---

### I/O Redirection and Piping in Unix

- 输出重定向到文件。
- 输入重定向自文件。
- 管道（piping）：

  - 一个命令的输出作为下一个命令的输入。

---

### Standard File Descriptors (1)

- 标准文件描述符：

  - `stdin`：标准输入。
  - `stdout`：标准输出。
  - `stderr`：标准错误输出。
- 在 shell 中一般用编号引用，而不是名字。
- 默认情况下：

  - `stdin` 来自键盘。
  - `stdout` 和 `stderr` 输出到终端屏幕。
- 可以重定向：

  - 把输入、输出、或错误重定向到文件或其他命令。

---

### Standard File Descriptors (2)

- 当前 shell 中常用的描述符号：

  - `stdin`：0。
  - `stdout`：1。
  - `stderr`：2。
- 在 C 语言中的使用（示例）：

```c
#include <stdio.h>
int main(int argc, char\*\* argv) {
    fprintf(stdout, "abcd\n"); // 等价于 printf("abcd\n");
    fprintf(stderr, "efgh\n");
}
```

---

### File Redirection

- 标准输出重定向：

  - `>`、`>!` 或 `>|`：覆盖输出到文件。
  - command > outfile
  - `>>`：追加输出到文件。
  - command >> outfile
- 标准输入重定向：

  - `<`：从文件读入作为标准输入。
  - command < infile
- 管道：

  - `|`：把前一命令输出作为后一命令输入。
  - command1 | command2
- `tee`：复制标准输出，一边显示，一边写文件：
- ls -l | tee lslist
- 丢弃输出：

  - 重定向到 `/dev/null`，作为“黑洞”：
  - > /dev/null

---

### File Redirection (csh)

- C Shell 中的特殊写法：

  - `>& file`：把 `stdout` 和 `stderr` 都重定向到 `file`。
  - `>> & file`：追加写入 `stdout` 和 `stderr` 到文件。
  - `|& command`：把 `stdout` 和 `stderr` 都通过管道给下一个命令。
- 将 `stdout` 和 `stderr` 分开重定向的示例：
- % (command > outfile) >& errfile

---

### File Redirection (sh/bash)

- 仅重定向标准错误：

  - `2> file`。
- 同时重定向标准输出与错误：

  - `> file 2>&1` 或 `&> file`。
- 追加重定向：

  - `>> file 2>&1`。
- 把两者一起通过管道传给命令：

  - `2>&1 | command`。
- 将二者分别重定向：
- $ command > outfile 2> errfile

---

### Other Special Command Symbols

- `;`：命令分隔符（在同一行串联多个命令）。
- `&`：在后台运行命令。
- `&&`：仅在前一个命令成功时才执行下一个命令。
- `||`：仅在前一个命令失败时才执行下一个命令。
- `( )`：将命令组在子 shell 中执行。

---

### Quoting

- `\`：转义下一个字符，使其按字面意义处理。
- 单引号 `' '`：

  - 其中字符全部按字面意义使用（在 csh 中 `!` 是例外）。
- 双引号 `" "`：

  - 允许变量替换与命令替换。
  - 不屏蔽 `$` 和 `\`。
- 反引号或 `$()`：命令替换：

  - `\`command```或``$(command)`：命令输出替换到当前命令行。
  - 示例：
  - echo "Today is $(date)."

---

### Job Control (csh/bash)

- 把任务放入后台：

  - 在命令末尾加 `&`。
  - 使用 `^Z`（Ctrl+Z）中止正在前台运行的任务。
- `^C`：中断前台任务。
- `bg`：在后台继续运行被暂停的任务。
- `fg [%n]`：把某个任务带回前台。
- `jobs` 命令：列出后台任务列表。

---

### Process Commands – ps

- 进程与线程：

  - Process：用 PID（进程 ID）标识。
  - Thread：轻量级进程、位于进程内部（详细见 C 语言部分）。
- `ps [options]`：显示进程状态：

  - 基本：`ps`。
  - 常用：`ps -ef` 或 `ps -aux`。
  - 选项在不同系统中略有差异，可查阅 `man ps`。

---

### Example Outputs of ps

- 示例展示：

  - 使用 `ps -ef | more` 输出进程列表，包括 UID、PID、PPID、CPU、TTY、CMD 等字段。
  - 使用 `ps -l` 输出详细格式，包括优先级、状态等。
- 示例中列出了系统进程（如 `sched`, `init`, `pageout`）和用户进程（如 `csh`, `xterm`）。

---

### Getting Process Information

- `top`：

  - 动态显示进程信息和系统资源使用情况（默认每 5 秒更新）。
- `pstree`：

  - 以树状结构显示进程之间的父子层级关系。
- `uptime`：

  - 显示系统已运行时间、登录用户数、平均负载等。

---

### kill

- `kill`：用于终止或发送信号给进程。

  - 基本格式：`kill [-signal] processID`。
- `kill -l`：列出所有可用信号。
- 示例信号列表：

  - `HUP`, `INT`, `QUIT`, `ILL`, `TRAP`, `ABRT`, `BUS`, `FPE`, `KILL`, `USR1`, `SEGV`, `USR2`, `PIPE`, `ALRM`, `TERM`, 等。
- `kill -9 processID`：

  - 发送 `SIGKILL`，强制终止进程（“最后手段”）。
- 常见键盘中断与信号对应关系：

  - `^C` → `SIGINT(2)`。
  - `^\` → `SIGQUIT(3)`。
  - `^Z` → `SIGSTOP(19)`。
- 可在头文件中查找信号定义：

  - `/usr/include/linux/signal.h`。
  - `/usr/include/asm-generic/signal.h` 等。

---

### Environment Variables

#### Shell Variable

为什么执行命令的时候 `./type.sh`可以，但是`type.sh`就不行呢？（已经给了权限`chmod u+x type.sh`）

> 答：`./`表示当前目录, 而对于`type.sh`直接执行这条命令，系统会从环境变量`$PATH$`中去找是否有这个指令，显然是找不到的，于是返回`command not found` **当然也可以在**`$PATH`**里面加入**`./`**,这样命令行就可以找到**`type.sh`**命令了**

- 环境变量为程序提供运行所需的环境信息。
- **全局环境变量**：

  - 可以被子进程使用。
- **本地 shell 变量**：

  - 仅在当前 shell 内使用，不向父进程回传。
  - 在脚本内，默认变量通常是“全局”的，函数内部可用 `local varName` 定义局部变量（视具体 shell 而定）。
- 常见保留变量：

  - `USER`, `HOME`, `PATH`, `SHELL`, `TZ`, `TERM`, `DISPLAY`, `LD_LIBRARY_PATH`, `LANG`, `PS1`, `PS2`, `EDITOR` 等。

---

### Setting Environment Variables

- 设置全局环境变量：

  - csh：
  - setenv NAME value
  - sh：
  - NAME=value
  export NAME
  - bash：
  - export NAME=value
- 设置本地 shell 变量：

  - csh：
  - set name=value
  - sh/bash：
  - name=value
- 删除变量：

  - csh：`unsetenv`、`unset`。
  - sh/bash：`unset`。

---

### Showing/Getting Variables (1)

- `env`：显示当前环境变量：

  - 示例输出包括：`HOME`, `SHELL`, `USER`, `PWD`, `PATH` 等。
- 使用 `echo` 查看单个变量：

  - `echo $HOME`。
  - 也可使用 `${variable_name}` 形式：
  - echo "::${HOME}_stuffs"

---

### Showing/Getting Variables (2)

- `set`：显示当前 shell 内所有变量（bash 示例）：

  - 输出包括：
  
    - `BASH`, `BASH_VERSINFO`, `BASH_VERSION`。
    - `COLORS`, `COLUMNS`, `CVSROOT`。
    - `PS1`, `PS2`, `PS4`。
    - `PVM_ROOT`, `PVM_RSH`, `PWD` 等。

---

### Shell Controls

- 本部分主要讨论 **C Shell 的控制结构**。
- C Shell 的控制结构与 C 语言相似。
- 学习路线建议：

  - 在教材中学习 sh/bash 的编程。
  - 阅读并理解 ICCAD 软件中真实脚本（包括 csh 和 sh/bash）。
  - 熟悉如何查找和使用参考资料。

---

### if/then/endif

- C Shell 中的条件语句结构：

```csh
if (condition1) then
    command list if condition1 is true
[else if (condition2) then
    command list if condition2 is true]
[else
    command list if condition1 is false]
endif
```

---

### Some if Conditions

- Shell 提供对文件类型和权限的检测操作符：

  - `-r`：文件存在且可读则为真。
  - `-w`：文件存在且可写。
  - `-x`：文件存在且可执行。
  - `-f`：存在且为普通文件（在 csh 中为“存在且不是目录”）。
  - `-d`：存在且为目录。
  - `-e`：文件存在。
  - `-o`：当前用户是文件所有者。
  - `-z`：文件大小为 0（空文件）。
  - `-s`：存在且非空（可在相关文档中查具体含义）。
- 幻灯片提示：可在接下来的示例脚本中看到这些操作符的实际使用。

---

### switch/case

- C Shell 中的分支结构：
- switch (parameter)
case pattern1:
command list1
<span>

breaksw

</span>


case pattern2:
command list2
<span>

breaksw

</span>


default:
command list for default behavior
<span>

breaksw

</span>


endsw

---

### foreach

- C Shell 的循环结构之一：
- foreach variable (list_of_variable_values)
command list
end

---

### while

- C Shell 的 while 循环：
- while (condition)
command list
<span>

break

</span>

<span>

continue

</span>


end

---

### Shell Startup

- 传统 shell 启动文件：

  - `~/.profile`（sh）。
  - `~/.login`（csh），登录时执行一次。
  - `~/.cshrc` 在每次启动 C shell 时执行。
- bash 登录 shell 的执行顺序：

  1. `/etc/profile`
  2. `~/.bash_profile`
  3. `~/.bash_login`
  4. `~/.profile`
- bash 非登录 shell：

  - 执行 `/etc/bashrc` 和 `~/.bashrc`。
- 登出时：

  - `/etc/bash.logout`、`~/.bash_logout` 会被执行。
- 启动脚本中常见任务：

  - 设置 `PATH`。
  - 定义函数。
  - 设置终端参数（`stty`）。
  - 设置终端类型。
  - 设置默认文件权限（`umask`）。
  - 其他初始化操作。

---

### Sample .login on Solaris

```bash
# @(#)local.login 1.4 98/02/06 SMI
stty -istrip #strip to 7 bits
# if possible, start the windows system.
# Give user a chance to bail out
if ( "`tty`" == "/dev/console" ) then
if ( "$TERM" == "sun" || "$TERM" == "AT386" ) then
    if ( ${?OPENWINHOME} == 0 ) then
        setenv OPENWINHOME /usr/openwin
    endif
    echo ""
    echo -n "Starting OpenWindows in 5 seconds (type Control-C to cancel)"
    sleep 5
    echo ""
    $OPENWINHOME/bin/openwin
    clear # get rid of annoying cursor rectangle
    logout # logout after leaving windows system
endif
endif
```

- 核心功能：

  - 设置终端为 7 位模式。
  - 仅在控制台 `/dev/console` 且终端类型为 `sun` 或 `AT386` 时尝试启动 OpenWindows。
  - 若 `OPENWINHOME` 未设置，则设为 `/usr/openwin`。
  - 提示用户可在 5 秒内用 `Ctrl+C` 取消。
  - 启动图形系统后，清屏并在退出图形界面时自动注销。

---

### Sample /etc/profile on Linux (1)

```bash
# /etc/profile: system-wide .profile file for the Bourne shell
# and Bourne compatible shells
if [ "$PS1" ]; then
if [ "$BASH" ] && [ "$BASH" != "/bin/sh" ]; then
    # The file bash.bashrc already sets the default PS1.
    # PS1='\h:\w\$ '
    if [ -f /etc/bash.bashrc ]; then
        . /etc/bash.bashrc # i.e. source /etc/bash.bashrc
        # try command line ‘$ help .’ ?
    fi
else # original bourne shell not bash
    if [ "`id -u`" -eq 0 ]; then
        PS1='# '
    else
        PS1='$ '
    fi
fi
fi
```

- 主要逻辑：

  - 若存在 `PS1`（交互式 shell），继续。
  - 若为真正的 `bash`（而非 `/bin/sh` 兼容模式）：
  
    - 若存在 `/etc/bash.bashrc`，则通过 `.`（source）加载。
  - 否则视为原始 Bourne shell：
  
    - root 用户提示符为 `#`，普通用户为 `$`。

---

### Sample /etc/profile on Linux (2)

```bash
# The default umask is now handled by pam_umask.
# See pam_umask(8) and /etc/login.defs.
if [ -d /etc/profile.d ]; then
for i in /etc/profile.d/*.sh; do
    if [ -r $i ]; then 
        . $i # i.e. source $i for various initializations
    fi
done
unset i
fi
```

- 功能：

  - 默认 `umask` 已由 `pam_umask` 统一管理。
  - 若存在 `/etc/profile.d` 目录：
  
    - 遍历其中可读的 `*.sh` 文件并逐个 `source`。
    - 这些脚本用于各种初始化（由系统和软件包提供）。
  - 最后 `unset i` 清理循环变量。

---

### Sample ~/.profile on Linux

```bash
# ~/.profile: executed by the command interpreter for login shells.
# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login
# exists.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.
# the default umask is set in /etc/profile; for setting the umask
# for ssh logins, install and configure the libpam-umask package.
#umask 022
# if running bash
if [ -n "$BASH_VERSION" ]; then # variable non-empty?
# include .bashrc if it exists
if [ -f "$HOME/.bashrc" ]; then
    . "$HOME/.bashrc" # i.e. source ~/.bashrc
fi
fi
# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
PATH="$HOME/bin:$PATH" # why add ~/bin to $PATH?
fi
```

- 主要内容：

  - `.profile` 只在 login shell 中执行；若有 `.bash_profile` 或 `.bash_login`，bash 不再读 `.profile`。
  - 默认 `umask` 在 `/etc/profile` 设置，SSH 登录可通过 `libpam-umask` 管理。
  - 若 `BASH_VERSION` 非空（表示正在运行 bash）：
  
    - 若存在 `~/.bashrc`，则将其 `source` 进来。
  - 若用户家目录下存在 `~/bin` 目录：
  
    - 将其加入 `PATH`，以便执行用户自定义脚本。

---

### History

- C Shell、bash 等支持命令历史功能：

  - 保存之前执行过的命令。
- 历史记录条数可通过变量设置：

  - 例如在 `.cshrc` 中：
  - set history=200
  set savehist=100
  - 在 `.bashrc` 中：
  - export HISTSIZE=1000
- 历史命令通常保存在用户家目录下：

  - C Shell：`~/.history`。
  - bash：`~/.bash_history`。

---

### History Commands

- 常用历史命令操作：

  - `history [nn]`：显示最近 nn 条命令。
  - `!!`：重复上一条命令。
  - `!nn`：重复编号为 nn 的命令。
  - `!string`：重复最近以 `string` 开头的命令。
- 在 Linux 终端中：

  - 可用方向键（↑ ↓）浏览历史命令并编辑。
  - `CTRL+R` 可在历史中搜索匹配的命令。

---

### Magic Symbol #! (or Shebang / Hashbang)

- Unix 脚本应以 `#!` 开头，告诉内核该脚本可直接执行，并指定解释器：

  - Bourne Shell / Bash：
  - #! /bin/sh
  #! /bin/bash
  - C Shell：
  - #! /bin/csh -f   # -f 表示不读取 .cshrc
- 没有 `#!` 时，可用以下方式运行脚本：

  - `sh sh_script` / `csh csh_script` / `bash bash_script` / `app_prog app_script`。
- 加上 `#!` 并赋予执行权限后（`chmod +x script`），可直接执行：

  - `sh_script` / `csh_script` / `bash_script` / `app_script`。

---

### Target of the Sample csh Script

- 示例 csh 脚本的目标场景：

  - 应用包目录（`$SYNOPSYS_ROOT`）下存在一套 X11 相关文件：
  
    - `admin/setup/rgb.txt`, `XErrorDB` 等。
  - 系统目录 `$LIBDIR/X11` 下也有对应文件：
  
    - `rgb.txt`, `XErrorDB` 等。
- 检查目标：

  1. 系统端是否存在 `rgb.txt`？
  2. 系统端是否存在 `XErrorDB`？
  3. 应用端 `XErrorDB` 中每个 `XRequest` 代码是否都在系统端 `XErrorDB` 中存在？
- 若以上任意检测失败：

  - 将应用端文件复制到系统端，完成安装/修复。

---

### Flow Graph of the Sample Script

- 幻灯片以流程图形式描述脚本逻辑，大致流程：

  - 判断是否 Sun 机器。
  - 输入 Synopsys 根目录，并检查目录合法性。
  - 检查应用端 X11 文件是否存在。
  - 检查系统端 X11 文件是否存在。
  - 检查 `XRequest` 代码是否全部存在。
  - 判断是否需要更新：
  
    - 若无缺失且无不匹配，则无需操作。
    - 否则检查系统目录写权限。
  - 备份旧文件。
  - 把应用端 X11 文件复制到系统端并验证复制结果。

---

#### A Sample csh Script File (1)

> 第一行是 -f fast模式，使用csh解释
> 
> bash中不支持`PATH <space> = <space> XXX` ,等号前后不能有空格，但是csh支持

```bash
#! /bin/csh -f
set path = (/bin /usr/bin /usr/ucb)
set LIBDIR = /usr/lib
set LIBX11 = $LIBDIR/X11 # /usr/share/X11 for Linux?
set XERRDB = $LIBX11/XErrorDB
set XRGB = $LIBX11/rgb.txt
echo " "
echo "Synopsys X11 Installation Script (Version 3.1)"
echo "Modified for Educational Use"
echo " "
# Check for valid platform
if (-x /bin/arch) then
set ARCH = `/bin/arch`
else
echo "Error: /bin/arch does not exist or is not executable."
set ARCH = unknown
endif
```

---

#### A Sample csh Script File (2)

> - `$?SYNOPSYS` 检查 SYNOPSYS 变量是否已定义
> - echo `-n` 参数的作用是:**阻止在输出末尾添加换行符**
> - goto 语句跳转点——readdir:
> - `$<` 从标准输入读取一行，赋值给变量 `a`
> - 如果用户输入了内容（`$a` 不为空）：
> 
>   - `-d $a` 检查路径是否存在且是目录
>   - 如果是有效目录，更新 SYNOPSYS 变量
>   - 如果不是，显示错误并跳回 `readdir` 标签重新询问
> - 如果用户直接按回车（空输入），保持默认值

```bash
if ("$ARCH" != "sun4") then
echo "Error: architecure is invalid or unknown."
echo "This script only runs on SPARC platforms."
exit 1
endif
# 检查 $ARCH 变量是否为 "sun4"（Sun SPARC 架构）
# 如果不是，输出错误信息并退出脚本
# Validate Root Directory
# goto 语句跳转点
readdir:
if (! $?SYNOPSYS) then
set SYNOPSYS = `pwd`
endif
echo -n "Synopsys root directory [" $SYNOPSYS "]: "
set a = $<
if ($a != "") then
if (-d $a) then
    set SYNOPSYS = $a
else
    echo "Error: root directory $a does not exist."
    goto readdir
endif
endif
```

---

#### A Sample csh Script File (3)

> `foreach f ($FILES)` - 遍历 FILES 列表中的每个文件
> 
> `-e` 检查文件是否存在
> 
> `!` 取反，即"如果不存在"
> 
> 完整路径是：`$SYNOPSYS/admin/setup/rgb.txt` 和 `$SYNOPSYS/admin/setup/XErrorDB`
> 
> 如果文件不存在：
> 
> - 输出错误信息
> - 将 `missing` 设为 1（true）

```bash
# Consistency check or Root Directory
set FILES = "rgb.txt XErrorDB"
set missing = 0
foreach f ($FILES)
if (! -e $SYNOPSYS/admin/setup/$f) then
    echo "Error: file $SYNOPSYS/admin/setup/$f does not exist."
    set missing = 1
endif
end
if ($missing) then
goto readdir
endif
```

---

#### A Sample csh Script File (4)

> 遍历三个变量：`$LIBX11`、`$XRGB`、`$XERRDB`
> 
> 如果是 `$LIBX11`：
> 
> - `-d` 检查是否为目录
> - 不存在则报错，`missing` 加 1
> 
> 如果是其他（`$XRGB` 或 `$XERRDB`）：
> 
> - `-f` 检查是否为文件
> - 不存在则报错，`missing` 加 1
> 
> `@ missing = $missing + 1` 是 C Shell 中的**算术运算**语法

```bash
# Analyze current installation
echo ""
echo "Checking existing X11 installation"
echo ""
set missing = 0
set keys = -1
foreach f ($LIBX11 $XRGB $XERRDB)
if ($f == $LIBX11) then
    if (! -d $f) then
        echo "Required directory $f does not exist."
        @ missing = $missing + 1
    endif
else
    if (! -f $f) then
        echo "Required file $f does not exist."
        @ missing = $missing + 1
    endif
endif
end
```

---

#### A Sample csh Script File (5)

> 如果 `$LIBX11` 目录和 `$XERRDB` 文件都存在：
> 
> - 切换到 `$SYNOPSYS/admin/setup` 目录
> - 从 `XErrorDB`（Synopsys 自带）中提取所有以 `XRequest.` 开头的行
> - `awk '{print $1}'` 提取第一列（请求代码名称）
> - 对每个请求代码，检查系统的 `$XERRDB` 文件中是否存在
> - `>& /dev/null` 抑制 grep 输出
> - `$status` 是上一条命令的退出状态（0=成功，非0=失败）
> - 如果找不到，报错并计数

```bash
if (-d $LIBX11 && -f $XERRDB) then
cd $SYNOPSYS/admin/setup
set reqs = 0
foreach xreq (`grep '^XRequest\.' XErrorDB | awk '{print $1}'`)
    grep $xreq $XERRDB >& /dev/null
    if ($status) then
        echo "Required $xreq code does not exist in $XERRDB"
        @ reqs = $reqs + 1
    endif
end
endif
echo ""
echo "Finished checking existing X11 installation"
echo ""
```

---

#### A Sample csh Script File (6)

> - 如果缺少请求代码（`$reqs > 0`），提示需要更新 `$XERRDB`
> - 如果没有缺失文件（`$missing == 0`）且没有缺少请求代码（`$reqs == 0`）
> 
>   - 说明 X11 安装完整，无需修改
>   - 直接退出脚本
> - 确定要检查的目录：
> 
>   - 如果 `$LIBX11` 目录存在，使用它
>   - 否则使用 `$LIBDIR`（父目录）
> - `-w` 检查目录是否可写
> - `\` 表示续行（跨行字符串）
> - 如果没有写权限，报错退出（需要 root 或适当权限）

```bash
if ($reqs > 0) then
echo "$XERRDB needs to be updated."
endif
if ($missing == 0 && $reqs == 0) then
echo "$LIBX11 installation requires no changes."
exit 0
endif
# Check write permissions
if (-d $LIBX11) then
set DIR = "$LIBX11"
else
set DIR = "$LIBDIR"
endif
if (! -w $DIR) then
echo "Error: directory $DIR must be writable to perform \
installation."
exit 1
endif
```

---

#### A Sample csh Script File (7)

> - 定义需要的目录列表：
> 
>   - `$LIBX11`：X11 库的主目录
>   - `$LIBX11/app-defaults`：X11 应用程序默认配置目录
> - 遍历每个目录
> - 如果目录不存在（`! -d $dir`）：
> 
>   - 输出提示信息
>   - 使用 `mkdir` 创建目录
>   - **再次检查**目录是否创建成功
>   - 如果创建失败（可能因权限问题），报错退出
> - 这种**双重检查**确保目录确实创建成功

```bash
# Create missing directories
set DIRS = "$LIBX11 $LIBX11/app-defaults"
foreach dir ($DIRS)
if (! -d $dir) then
    echo "Creating directory $dir"
    mkdir $dir
    if (! -d $dir) then
        echo "Error: could not create directory $dir"
        exit 1
    endif
endif
end
# Determine the file(s) to install
set FILES = ""
if (! -f $XRGB) then
set FILES = rgb.txt
endif
if (! -f $XERRDB || $reqs != 0) then
set FILES = "$FILES XErrorDB"
endif
```

---

#### A Sample csh Script File (8)

> 遍历 `$FILES`（之前定义的 `rgb.txt` 和 `XErrorDB`）
> 
> 如果目标文件已存在：
> 
> - 备份旧文件，重命名为 `.old` 后缀
> - 防止覆盖丢失原有配置

```bash
# Install the required file(s)
foreach f ($FILES)
if (-f $LIBX11/$f) then
    echo "Preserving old $f file in $LIBX11/$f.old"
    mv $LIBX11/$f $LIBX11/$f.old
endif
echo "Copying $f to $LIBX11"
cp $SYNOPSYS/admin/setup/$f $LIBX11
diff $SYNOPSYS/admin/setup/$f $LIBX11/$f >& /dev/null
if ($status) then
    echo "Error: could not copy file $f"
    exit 1
endif
chmod 444 $LIBX11/$f
end
exit 0
```

- 逻辑总结：

  - 检测和创建路径。
  - 校验文件存在性与内容一致性。
  - 备份旧文件。
  - 复制新文件并做 `diff` 校验。
  - 设置权限（只读 444）。

---

### Comparing Shell Features and Learn More

- 建议了解更多 shell 特性：

  - 参考文献：
  
    - 《Introduction to Linux》附录 C。
    - 表 C-1：各 shell 的共同特性。
    - 表 C-2：各 shell 的差异特性。
- 学习重点：`bash` 和 `csh`。
- 建议使用 `man` 查看手册：

  - `man sh`、`man bash`、`man csh`。
- bash 调试模式：

  - 使用 `bash -x` 可以跟踪脚本执行过程。
