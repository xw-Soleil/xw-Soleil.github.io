# 不知名回忆卷 1

> 历年考卷回忆整理 1

<alert title="阅读说明" type="info">

- 这套是非缓考的回忆卷，回忆者说明「不是本人亲自考试，内容相差较大」；题目不全，和前面几套重复度也高
- 正文按原卷顺序排列，题号与原卷一致（原卷选择题记了 1–15 和 26–30，第 28 题是空的）
- 原卷只记了题干的大意，没有选项；题干照抄原卷，`?` 就是要填的地方
- 绿色的「答案」块里是答案和补充讲解，默认遮住，点一下查看单个答案；也可以 <answer-toggle>



</answer-toggle>
</alert>

**原卷**（回忆版）
<embed src="/pdf/ICCAD-Recall-1.pdf" width="100%" height="600" type="application/pdf">



</embed>



## 一、选择题

<alert title="题目" type="question">

本次试卷大部分选择题。

</alert>

**1.** lazy dog in ? practices

<answer>

lazy dog appears in <mark>

typing

</mark>

 practice.

</answer>

**2.** l in lcd means

<answer>

local

> lcd: local change directory 切换本地目录

</answer>

**3.** ! in !pwd means

<answer>
<mark>

execute the command in the **local shell**

</mark>



> `!pwd` shows the **local** working directory

</answer>

**4.** kill -9 3721 means sending #9 signal to a ? with PID of 3721

<answer>

process

> signal 9 = **SIGKILL**, force terminate

</answer>

**5.** @ages indicates this variable is of ? type

<answer>
<mark>

array

</mark>



> in Perl, `@` = array（数组）; `$` = scalar（标量）; `%` = hash.（哈希）
> 
> 哈希（hash）在 Perl 里指的是一种**键值对（key-value pairs）数据结构，也叫关联数组**或**字典/map**。

</answer>

**6.** .o is for ? file

<answer>
<mark>

object

</mark>

 file

</answer>

**7.** ? is Perl suffix

<answer>

`.pl`

</answer>

**8.** ? is Python suffix

<answer>

`.py`

> **Suffix Naming Convention**
> 
> - `.sh/.bash/.csh` #Shell Script
> - `.c/.cpp/` /`.h/.hpp` #C/C++ Source/Header File
> - `.py` #Python Script
> - `.java` #Java Source File
> - `.o` #Object File，gcc -c之后生成的目标文件
> - `.s` #Assembly Source File，汇编文件
> - `.a` #Library (static)，静态库
> - `.so` #Dynamic-linking Library (shared object)，动态库
> - `.f` #Fortran Source File
> - `.pl` #Perl Script perl 脚本
> - `.tcl` #TCL/TK Script

</answer>

**9.** ? is assembly source code file

<answer>
<mark>

`.s`

</mark>

 is the suffix for an assembly source code file

</answer>

**10.** demo_inout.c prints out 'stdout' and ?

<answer>
<mark>

`stderr`

</mark>
</answer>

**11.** -lX11 means the needed library should be a file called?

<answer>
<mark>

`libX11.a` or `libX11.so`

</mark>
</answer>

**12.** vimtutor is a program running tutorial for vim

<answer>
<mark>

`vimtutor`

</mark>

（原卷记下的就是答案）

</answer>

**13.** -r meaning

<answer>
<mark>

**recursive**

</mark>



> 这个题目没给全，-r 大概有 reverse recusive read 等几种

</answer>

**14.** $@ means this rule's current ?

<answer>
<mark>

`target`

</mark>



> `$@` 目标文件，即 `$(TARGET)`
> 
> `$^` 表示所有的依赖文件，即 `file1.o file2.o file3.o`
> 
> `$<` 表示第一个依赖文件，即 `file1.o`
> 
> `$?` 表示比目标还要新的依赖文件列表
> 
> `$*` 当前任务的基名，即不包括后缀

</answer>

**15.** press ? key to return command mode

<answer>
<mark>

`ESC`

</mark>
</answer>

**26.** s/../../ s?substitution

<answer>

`s` means <mark>

substitution

</mark>



> 和前面几个卷子的一样，分析结果
> 
> 将改行的第一个 `Oct.` 换成 `Nov.`。注意，这里将 `.` 视为普通的点，所以文本匹配的是 `Oct.` 而不是 `Oct`

</answer>

**27.** more exit=q

<answer>

use `more` to display the content of some files, one key to exit = <mark>

`q`

</mark>



> 空格（space）下翻一页，`b`（back）返回一页，`q`（quit）退出(类似man)

</answer>

**28.** 原卷空着，没有记下题目。

**29.** interpreter program of perl (perl)

<answer>
<mark>

`perl`

</mark>



> Tcl/TK interpreter is wish.

</answer>

**30.** class-B IP address: 135.0.1.1

<answer>
<mark>

`135.0.1.1`

</mark>



> 注意最开始的数字大小
> 
> - **Class A**：以 `0` 开头 1–126
> - **Class B**：以 `10` 开头 128–191
> - **Class C**：以 `110` 开头 192–223
> - **Class D**：以 `1110` 开头 224–239
> - **Class E**：以 `1111` 开头 240–255

</answer>

## 二、填空题

**1.** 最大的EDA公司？

<answer>

Synopsys (第一)

Cadence (第二)

Mentor Graphics (第三) (Siemens 收购)

</answer>

**2.** 如何熟练使用perl,shell,tcl,c/c++,几个角度

<answer>

**Core syntax**: variables, if/loop, functions, arrays/maps, I/O

**Typical tasks**:

- Shell = automation
- Perl = text/regex
- Tcl = tool/EDA scripting
- C/C++ = performance/core logic

**Toolchain**: run/env, compile/link, debug, errors

**Engineering habits**: args check, help, logs, clean structure

**Mini project**: use them together (Shell control + Tcl run tool + Perl parse + C/C++ compute)

> **常用语法**：变量、条件循环、函数、数组/哈希、读写文件
> 
> **典型用途**：
> 
> - <mark>
> 
> Shell=自动化
> 
> </mark>
> - Perl=文本/正则
> - Tcl=工具/EDA脚本
> - C/C++=性能/核心模块
> 
> **工具链**：运行环境、编译链接、调试、排错
> 
> **工程习惯**：参数检查、help、日志、结构清晰
> 
> **小项目整合**：Shell控流程 + Tcl跑工具 + Perl解析 + C/C++计算

</answer>

**3.** meta character？

<answer>

Meta chararcter 背吧，没招了

</answer>

## 三、执行基本脚本

<alert title="题目" type="question">

原卷只列了下面这些命令和缩写，按其他几套卷子的题型，应该是写出主要功能和语法。

</alert>

**chmod**

<answer>

Main function: change file/directory permissions (r/w/x for u/g/o).

Syntax: `chmod [OPTION] MODE FILE...` / `chmod [OPTION] OCTAL FILE...`

- `u+x`: add execute permission to the **user(owner)**. e.g., `chmod u+x a.sh`
- `755`: set perms to **rwxr-xr-x**. e.g., `chmod 755 a.sh`

</answer>

**cat**

<answer>

Main function: print/concatenate file contents.

Syntax: `cat [OPTION] [FILE]...`

- `-n`: number all output lines. e.g., `cat -n a.txt`

</answer>

**cp**

<answer>

Main function: copy files/directories.

Syntax: `cp [OPTION] source_file target_file`

- `-r`: copy directories **recursively**. e.g., `cp -r DIR DEST`
- `-f`: Overwrite an existing destination file without prompting (without requiring `--force`).
- `-i`: interactive, prompt before overwrite

</answer>

**which**

<answer>

Main function: locate command path in `PATH`.

Syntax: `which COMMAND...`

</answer>

**paste**

<answer>

Main function: merge lines of files side-by-side.

Syntax: `paste [OPTION] FILE...`

</answer>

**expand**

<answer>

Main function: convert tabs to spaces.

Syntax: `expand [OPTION] [FILE]...`

`-t`: have tabs N characters apart, not 8, e.g. `expand -t 4 a.txt`

</answer>

**env var**

<answer>

Main function: environment variables control program behavior

Syntax: `env [OPTION] [NAME=VALUE]... [COMMAND [ARG]...]`

`-i`, `--ignore-environment`: Starts with an **empty environment**

`-u NAME`, `--unset=NAME`: **Removes** (unsets) the environment variable `NAME` for the command being run.

</answer>

**eda**

<answer>

EDA = Electronic Design Automation，电子设计自动化（原整理没有写这一项，按 22-23 卷第 20–22 空补上）

</answer>

**cad**

<answer>

CAD = Computer Aided Design，计算机辅助设计（原整理没有写这一项，按 22-23 卷第 23–25 空补上）

</answer>

**ping**

<answer>

Main function: test connectivity and latency.

Syntax: `ping [OPTION] DESTINATION`

`-c 4`: send **4** packets then stop (count).

</answer>

**lcd**

<answer>

Main function: change the **local** directory to an FTP client.

Syntax: `lcd [LOCAL_DIR]`

</answer>

**!pwd**

<answer>

Main function: in FTP, `!` runs a **local shell command**; `!pwd` shows the local directory.

Syntax: `!COMMAND`

- `!pwd`: local `pwd`
- `!ls`: local `ls`

</answer>

**pwd**

<answer>

Main function: print current directory path.

Syntax: `pwd [OPTION]`

</answer>

**du**

<answer>

Main function: estimate file space usage.

Syntax: `du [OPTION]... [FILE]...`

`-s`: summary only (total).

`-h`: human-readable units.

`du -sh DIR`: total size of DIR in human-readable form.

`--max-depth=1`: show only 1 level of subdirectories.

`du -h --max-depth=1 DIR`: sizes of first-level entries in DIR.

</answer>

**umount**

<answer>

Main function: unmount a filesystem.

Syntax: `umount [OPTION] MOUNTPOINT|DEVICE`

`umount /mnt/usb`: unmount the filesystem mounted on `/mnt/usb`.

</answer>

**tar**

<answer>

Main function: archive files (create/list/extract), optionally gzip.

Syntax: `tar [options] {directory | file}…`

Key options:

- `-c`: create archive
- `-t`: list archive contents
- `-x`: extract archive
- `-f ARCHIVE`: archive file name to read/write
- `-z`: gzip compress/decompress (`.tar.gz`)

> Examples:
> 
> - `tar -cf a.tar FILE...`: create a tar archive.
> - `tar -tf a.tar`: list contents.
> - `tar -xf a.tar`: extract.
> - `tar -czf a.tar.gz FILE...`: create gzip-compressed archive.
> - `tar -xzf a.tar.gz`: extract gzip-compressed archive.

</answer>
