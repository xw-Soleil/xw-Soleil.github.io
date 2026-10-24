# Linux & Unix

> Linux 与 Unix 基础

## Unix Overview

### Is Linux a kind of Unix?

> <mark>
> 
> No. Linux is an operating system
> 
> </mark>
> 
>  <mark>
> 
> **similar**
> 
> </mark>
> 
>  <mark>
> 
> to UNIX.
> 
> </mark>
> 
>  Its original intention is to **replace Unix**. It is an **imitation(模仿) and optimization of Unix**. The difference between them is that Unix is commercial software, but Linux is **open source**.
> 
> Linux只是一个为了取代Unix而模仿与优化Unix的操作系统，Unix是商业的，Linux是开源的

### Why say GNU/Linux?

> GNU/Linux means that the **upper program of the operating** <mark>
> 
> **system is GNU**
> 
> </mark>
> 
>  <mark>
> 
> and the
> 
> </mark>
> 
>  <mark>
> 
> **kernel is Linux**
> 
> </mark>
> 
> . Only when combined can a complete operating system be formed. It can be said that **Linux is a component(组件) used in GNU project**. The reason why they don't use a single name is that they have different ideas. The former advocates free software and the latter advocates open source software.
> 
> 操作系统可以粗分为两层：**内核（kernel）**：负责管理硬件、进程等核心功能以及**用户空间工具**：命令、库、桌面环境等，GNU 项目做了很多上层工具：`gcc`、`bash`、`ls` 等，Linus 写了 Linux 内核。<mark>
> 
> 把
> 
> </mark>
> 
>  <mark>
> 
> **GNU 工具 + Linux 内核**
> 
> </mark>
> 
>  组合在一起，就变成我们日常说的“Linux 系统”。出于尊重 GNU 的贡献，有人坚持叫 **GNU/Linux**。

### GNU? GPL? GUI?

> 1. **GNU**：GNU’s Not Unix!(递归的缩写，GNU)
> 
> GNU is a free operating system.
> 
> GNU 是一个**自由操作系统**（Free Operating System）项目
> 
> 1. **GPL**：GNU General Public License
> 
> GPL is an agreement certificate for computer software issued by the free software foundation. The software using this certificate is called free software.
> 
> GPL是由 Free Software Foundation 颁布的一种许可证，使用 GPL 的软件被称为 **自由软件**。
> 
> 1. **GUI**： Graphical User Interface
> 
> GUI is a computer operation user interface displayed graphically.

<alert type="tip">

#### Free Software VS Open Source

- **GPL(Free Software 风格):** 你修改了 Linux 内核 → 必须开源你的修改
- **MIT(Open Source 风格):**  你修改了 Node.js → 可以闭源，可以商用

</alert>

### Ubuntu, what is it?

- <mark>

Ubuntu is a Linux operating system based on desktop applications

</mark>

<mark>

Ubuntu是一个基于桌面应用的Linux操作系统

</mark>
- Ubuntu is named after the Nguni philosophy of ubuntu, which Canonical indicates means "**humanity to others**" with a connotation of "**I am what I am because of who we all are**".
Ubuntu名字的哲学含义

##### What application greatly motivated companies to use Linux instead of Windows?

- Apache
Apache 指 **Apache HTTP Server**，一个非常流行的 **Web 服务器** 软件。由于它在 Linux 上稳定、性能好、免费开放，很多公司为了跑网站，就倾向用 Linux + Apache，而不是 Windows + IIS。

### Unix command -options arguments

- '**Whitespace**' separates parts of the command line
- An **argument** indicates on what the command is to perform its action
- An **option** modifies the command, usually starts with '-'

```bash
command [options] [arguments]
# 命令   选项        参数
# command + options(以 - 开头) + arguments(通常是文件/目录名)，用空格分开
```

### case sensitive

- Use lower case
<mark>

Unix / Linux 命令对大小写敏感

</mark>

## Getting Started

### Login/Logout Commands

- `login` #登录
- `logout` #登出
- `exit` #退出

### Control keys perform special functions

- `^H` or `Backspace` #擦除一个字符 erase a character
H=**H**ide
- `^U` #擦除一行 cancel line
U=**U**ndo line
- `^S` #暂停显示 pause display
S = **S**top
- `^Q` #重新启动显示 restart display
这个我也没想好咋记，硬记
- `^C` #取消操作 cancel operation
- `^D` #注销用户，通常禁用 signal end of file
D=**D**one

> 本质就是<mark>
> 
> **发送一个signal，就是EOF**
> 
> </mark>
> 
> 
> 
> ##### `Ctrl+D` 的三种用法
> 
> 1. **程序输入中** - 结束输入，告诉程序"输入完了"（如 `wc`, `cat` 等待输入时）
> 2. **Shell 提示符下** - 退出当前 shell / 登出（空行时按 `Ctrl+D`）
> 3. **行中编辑** - 删除光标后的一个字符（光标不在行首时）

- `^V` #对待下一个控制字符为普通字符 treat following control character as normal character
V = **V**erbatim（逐字的）

### Find Version of Unix

- `uname [options]` #显示 Unix 版本, print system information
- `uname -a` #显示所有系统信息, **a**ll, print all information

Linux host 5.4... x86_64 GNU/Linux

- `uname -o` #仅显示操作系统名称 **o**perating-system

GNU/Linux

### Change Password

- `passwd` #更改密码，注意是**wd**

### System Date and Time

- `date` #显示或设定日期和时间, print or set the system date and time，注意不是time，time是用来统计耗时的

Sat Jan  3 10:11:57 PM CST 2026

### Commands for Useful Info

- `who` #显示当前登录在系统上的登录用户的信息，show who is logged in
  - `who am i` #显示执行该命令的登录用户的信息
  - `whoami` #显示当前有效用户的名字，即终端的操作用户，print effective userid
  scy or root```bash
# 先用用户 bixing 登录：
$ whoami
bixing
$ who am i
bixing  pts/0  2025-12-10 21:00 (192.168.0.100)
# 然后在这个终端里 su 变成 root
$ su -
Password:
$ whoami
root          # 现在你是 root 了
$ who am i
bixing  pts/0  2025-12-10 21:00 (192.168.0.100)
              # 这里还是显示最初登录的人：bixing
who am i   # 等价于 who -m, 它查的是：当前这个终端最早登录进来的那条记录
```
- `ps` #报告进程状态
**p**rocess **s**tatus → 报告进程状态
- `stty` #打印和改变终端设置，change and print terminal line settings

**s**et **tty** → 设置 / 查看 终端(line) 参数

- `env` #显示当前环境变量值，show current EV values
**env**ironment → 显示当前环境变量值

### Check Command Aliases

- `alias` #检查命令别名

  - `alias`：列出当前所有别名
  - `alias aname='pname'`：给命令起别名
  
    - `aname`：**a**lias **name**（别名）
    - `pname`：**p**rogram **name**（原命令）
    - e.g. `alias rm='rm -i'`

### Online Manual

- `man` #手册查询，find and display reference manual pages

  - `Space` `bar` #显示下一页
  - `b` #显示上一页 `b=back`
  - `q` #退出
- `xman` #**有 GUI** 的手册查询，the man has X Window GUI
- `info` #用**超文本**的形式显示更多更新的命令信息，read info document，usually shows more and newer information of a command, in hyper text format

#### 手册页的内部结构

一份标准的 Man page 通常包含以下固定板块：

1. **NAME**: 命令名称及简短描述。
2. **SYNOPSIS**: **语法大纲**（使用方括号 `[]` 表示可选，省略号 `...` 表示多个）。
3. **DESCRIPTION**: 详细的功能解释。
4. **OPTIONS**: 所有参数（Flags）的解释。
5. **EXAMPLES**: 实际用法示例（最有用的部分）。
6. **ENVIRONMENT VARIABLES**
7. **EXIT STATUS**: 错误代码含义。
8. **SEE ALSO**: 相关命令的引用。
9. **BUGS**

#### 传统手册的章节组织 (Manual Sections)

Man pages 遵循一套严格的组织标准，通常分为 8 个主要章节(PPT上只有5个)。了解这些章节能帮你快速定位信息：

<table>
<thead>
  <tr>
    <th>
      章节编号
    </th>
    
    <th>
      类别名称
    </th>
    
    <th>
      说明
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      -1
    </td>
    
    <td>
      用户命令 (User commands)
    </td>
    
    <td>
      普通用户在终端执行的可执行程序或 shell 命令。
    </td>
  </tr>
  
  <tr>
    <td>
      -2
    </td>
    
    <td>
      系统调用 (System calls)
    </td>
    
    <td>
      由内核提供的服务接口（如硬件访问）。
    </td>
  </tr>
  
  <tr>
    <td>
      -3
    </td>
    
    <td>
      库函数 (Library functions)
    </td>
    
    <td>
      程序库中的函数，如 C 标准库中的 printf。
    </td>
  </tr>
  
  <tr>
    <td>
      -4
    </td>
    
    <td>
      设备 (Devices)
    </td>
    
    <td>
      /dev 目录下的特殊文件及其驱动说明。
    </td>
  </tr>
  
  <tr>
    <td>
      -5
    </td>
    
    <td>
      文件格式 (File formats)
    </td>
    
    <td>
      各种配置文件的格式说明（如 /etc/passwd）。
    </td>
  </tr>
</tbody>
</table>

---

## File System

### Standard Unix Directories

- `/bin` bin=**bin**ary 必须命令的**二进制**文件，可执行
- `/dev` dev=**dev**ice **设备**文件
- `/tmp` tmp=**t**e**mp**orary **临时**文件
- `/lib` lib=**lib**rary 必须的**共享库和内核**模块
- `/etc` etc=<mark>

**etc**

</mark>

<mark>

etera

</mark>

 主机特定的系统配置
- `/src` src=**s**ou**rc**e 源代码
- `/root` root 该目录为系统管理员的主目录
- `/home` home 存放所有普通用户主目录
- `/` 根目录，是最高层的目录，其他所有的目录都是他的分支

### A disk

- Disks mounted to positions in file tree
- A disk is divided into blocks

– 512, 1024, 2048 bytes are common block sizes

- A disk partition divided into three major sections

  - – superblock(超级块)
  - – inodes(索引节点)
  - – data blocks(数据块)

<table>
<thead>
  <tr>
    <th>
      区域名称
    </th>
    
    <th>
      核心角色
    </th>
    
    <th>
      对应 PPT 中的关键点
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      Superblock (超级块)
    </td>
    
    <td>
      系统管理员 (掌控全局)
    </td>
    
    <td>
      记录磁盘分区的整体结构信息，包括块大小（512/1024/2048 字节）等关键参数。
    </td>
  </tr>
  
  <tr>
    <td>
      Inodes (索引节点)
    </td>
    
    <td>
      档案管理员 (管理属性)
    </td>
    
    <td>
      存储文件的元数据（权限、大小、位置指针等），但不包含文件名。
    </td>
  </tr>
  
  <tr>
    <td>
      Data blocks (数据块)
    </td>
    
    <td>
      物理仓库 (存储内容)
    </td>
    
    <td>
      磁盘被划分为多个块，用于存放普通文件的数据或目录的映射表。
    </td>
  </tr>
</tbody>
</table>

### File Tree

#### full path name

<mark>

由根目录

</mark>

 <mark>

`/`

</mark>

 <mark>

写起，例如:

</mark>

 <mark>

`/usr/share/doc`

</mark>

<mark>

,

</mark>

 <mark>

`$HOME/.bashrc`

</mark>

 <mark>

等

</mark>



#### relative path name

相对路径就是指由这个文件所在的路径引起的跟其它文件(或文件夹)的路径关系，即从当前目录开始

Linux 中，`.`**表示当前目录，**`..`**表示上一层目录**。所以`../../include/define.h` 的意思为从当前路径开始，向上两级下的 `include` 内的 `define.h`

### Directory Commands

#### pwd

- `pwd` **p**rint **w**orking **d**irectory 打印当前所在的工作目录

#### cd

- `cd` - **c**hange **d**irectory.

  - 不加参数，**默认返回用户主目录**。`cd` = `cd ~` = `cd $HOME`
  - `cd ..`返回上级目录,`cd ../..`返回上两级目录
  - `cd -`返回之前的目录
  - `cd ~somebody` 进入某个用户的 home，但前提是有这个somebody以及有相应的权限

#### mkdir

- `mkdir` **m**a**k**e **dir**ectories

  - `mkdir [option] [directory]`
  - create the directories, if they do not already exist
  - `-p` **p**arents, no error if existing, make parent directories as needed, 绝对路径/目录名，如果目录不存在，可连带创建多层
  - `-v` **v**erbose(冗长的), print a message for each created directory

#### rmdir

- `rmdir` **r**e**m**ove <mark>
<u>

empty

</u>
</mark>

 **dir**ectories

  - Directory <u>
  
  must be empty
  
  </u>
  
  ，**只可以删除空的目录**
  - `-p` **p**arents, remove directories and its ancestors 递归删除，如果父目录为空则可一同删除

#### tree

- `tree`
  - list contents of directories in a tree-like format

#### ls

- `ls` **l**i**s**t contents of directory

  - `ls [option] [file...]`
  - `-a` **a**ll 所有，**包括隐藏文件**， all, including files begin with '.'（隐藏文件以`.`开头）
  - `-d` **d**irectory name only **只显示目录本身**，而不是其内容 仅`.`
  - `-F` **F**ormat suffix 格式后缀（比如目录加`/`）
  - `-l` **l**ong 显示完整信息（长格式，权限/所有者/时间/大小都显示出来）
  - `-R` **R**ecursive 递归显示，会把目录下面子文件也显示出来
  - `-t` **t**ime 按修改时间排序

##### ls --color=auto

- 根据其**文件类型**或**扩展名**自动显示不同的颜色
- 默认颜色含义

  - **蓝色 (Blue)**：目录 (Directory)。
  - **绿色 (Green)**：可执行文件 (Executable)。
  - **青色/淡蓝色 (Cyan)**：符号链接 (Symbolic link)。
  - **红色 (Red)**：压缩文件 (Compressed/Archive file)。
  - **灰色/白色**：普通的文本或数据文件。
  - **紫色**：图片或视频
  - **黄色**：设备
- alias ls（系统预设）

alias ls='ls --color=auto'

##### ls-F

在列出的文件名后面加上一个特殊的“分类符号”

<table>
<thead>
  <tr>
    <th>
      符号
    </th>
    
    <th>
      文件类型
    </th>
    
    <th>
      含义
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      /
    </td>
    
    <td>
      目录 (Directory)
    </td>
    
    <td>
      这是一个文件夹。
    </td>
  </tr>
  
  <tr>
    <td>
      *
    </td>
    
    <td>
      可执行文件 (Executable)
    </td>
    
    <td>
      这是一个程序或脚本，你可以运行它。
    </td>
  </tr>
  
  <tr>
    <td>
      @
    </td>
    
    <td>
      符号链接 (Link)
    </td>
    
    <td>
      这是一个快捷方式，指向另一个文件。
    </td>
  </tr>
  
  <tr>
    <td>
      **`
    </td>
    
    <td>
      `**
    </td>
    
    <td>
      管道 (FIFO)
    </td>
  </tr>
  
  <tr>
    <td>
      =
    </td>
    
    <td>
      套接字 (Socket)
    </td>
    
    <td>
      用于网络或本地通信的接口。
    </td>
  </tr>
  
  <tr>
    <td>
      (无符号)
    </td>
    
    <td>
      普通文件
    </td>
    
    <td>
      这是一个普通的文本、图片或文档。
    </td>
  </tr>
</tbody>
</table>

##### ls -l

`ls -l` 第一列：类型（显示的<u>

第一个字符

</u>

）

- `d`: **d**irectory 目录
- `l`: symbolic **l**ink 符号**链接/快捷方式**
- `b`: **b**lock special file **块特殊文件（磁盘类）**
- `c`: **c**haracter special file **字符特殊文件（终端/串口类）**
- `-`: **o**rdinary 普通文件
- e.g. `drwxr-xr-x` → 第一个字符 `d`：这是**目录**

`ls -l`权限位（<u>

第 2-10 个字符

</u>

）

九个字符拆成三组`rwx rwx rwx`

- first 3: user/owner（前三个字符代表文件拥有者的权限）
- second 3: assigned Unix group（中间三个代表同组用户的权限）
- last 3: others（最后三个代表其他用户的权限）
- **rwx: read, write, execute**

对目录的 `x` 意味着“可进入/可穿越（traverse）”，不是“执行目录”

**ls -l format**

- Access permissions, **Number of links****(硬链接，包括****.****和****..****)**, Owner, Group, Size (所占磁盘大小，单位字节)or device number, Modified time, File name

```bash
# ls -l 的结果举例：
drwxr-xr-x  2  alice  staff  4096  Dec 14 09:00  mydir
```

### File Maintenance Command

#### chmod

- `chmod` **ch**ange file **mod**e bits, change the file or directory access permissions (mode) 更改文件或目录的访问权限/模式

  - `chmod [options] file`
    - `chmod ugo+/-rwx file`
    - `chmod u+w file`：给拥有者加写权限
    - `chmod g+rw file`：给同组的加读取和写权限
    - `chmod go-x file`：给同组与其他人去掉执行权限
  - `u`：**u**ser who owns it
  - `g`：other users in the file’s **g**roup
  - `o`：**o**ther users not in the file’s group
  - `a`：all users，<u>
  
  什么也没写默认认为 all
  
  </u>
  - `r=4, w=2, x=1, total=7`把每一组(uog)都变成一个数字来表示
  - 7 = 4+2+1 = `rwx`
  - 6 = 4+2 = `rw-`
  - 5 = 4+1 = `r-x`
  - 4 = `r--`
  - 0 = `---`
    - `chmod 777 file` 给所有人全开
    - `chmod 750 file` #rwxr-x---
    - `chmod 640 file` #rw-r-----

#### umask

- `umask` # get or set the file mode creation mask (built-in in bash like alias)

  - <mark>
  
  **umask 不是权限本身，而是“要去掉的权限”**
  
  </mark>
  
  <mark>
  
  。
  
  </mark>
  
  
    - 这个是一开始对于终端的设定值，比如`umask 022`之后，再建立的新目录都是`755`了，有点像是光刻的掩膜
  - 默认规律：
  
    - 新建**目录**的基础权限通常是 `777`
    - 新建**文件**的基础权限通常是 `666`（默认不直接给 x）

> - 实际权限 = 基础权限 **减去** umask
> 
>   - `umask 022` #777-022=755->rwxr-xr-x

##umask 023

`umask 023` #777-023=754->rwxr-xr--

#### chgrp

- `chgrp` #**ch**ange **gr**ou**p** ownership 改变文件的组

  - sudo chgrp finance report.pdf

#### chown

- `chown` #**ch**ange file **own**er 改变文件的拥有者

  - sudo chown john file.txt

### Display Commands

`stdout`: **标准输出**：你在终端里看到的“打印出来的文字”，默认都会显示到屏幕上，即为标准输出。

#### echo

- `echo` #echo the text string to stdout 显示一行文本

  - echo "my home is $HOME"

#### cat

- `cat` #con**cat**enate files and print on the standard output 将文件连接并在`stdout`输出

  - `cat` 可查看文件，如 `cat c.txt`
  - `cat a.txt b.txt` # 连接多个文件一起输出
  - `cat a.txt | grep "error"` # 把内容“交给下一个命令”（管道）

#### head

- `head -n (line)` #display first 10 (or #) lines of file，默认显示10行  直接`head a.txt`就是显示10行

  - `head` 可以查看前面指定行数，如 `head -n 5 a.txt`

#### tail

- `tail -n` #display last 10 (or #) lines of file, 默认显示10行

  - `tail` 可以查看尾部指定行数，如 `tail -n 5 a.txt`

#### more

- `more` #browse or page through a text file

  - `more` 命令和 `cat` 的功能一样都是查看文件里的内容，但有所不同的是 `more` **可以按页来查看文件的内容****，****cat****是全部输出**
  - 空格（space）下翻一页，`b`（back）返回一页，`q`（quit）退出(类似man)

#### less

- `less` 比 `more` 功能更为强大：

  - `less` <mark>
  
  **可以按键盘上下方向键**
  
  </mark>
  
  <mark>
  
  显示上下内容
  
  </mark>
  
  ，`more` 不能通过上下方向键控制显示
  - `less` 不必读整个文件，加载速度会比 `more` **更快**
  - `less` 退出后 shell <mark>
  
  **不会留下刚显示的内容**
  
  </mark>
  
  ，而 `more` 退出后会在 shell 上留下刚显示的内容

### File Manipulation(操作) Commands

#### cp

- `cp` #**c**o**p**y files and directories```bash
# 目标是文件名：复制并改名，将 a.txt 复制一份，起名叫 b.txt。
cp a.txt b.txt   # 复制 a.txt 成 b.txt
# 目标是目录：复制到目录里，文件名不变
cp a.txt /tmp/   # 复制到 /tmp/a.txt
```


  - `cp [-fipRr] source_file target_file`  `cp [选项] 源 目标`
    - `-i`（**i**nteractive 可交互的），如果目标文件已存在，在覆写之前进行提示（prompt before overwrite），如 `cp -i /usr/men/m*.c /usr/zh`，复制所有 m 打头的文件
    - `-f` (**f**orce)覆盖已经存在的目标文件而不提示 force,**强制覆盖**, 不提示
    - `-p` (**p**reserve)除复制文件内容外，还**保留**修改时间和访问权限 preserve（In addition to the contents of the file, the modification time and access permissions are copied）
    - `-R -r`（**r**ecursively）#若源文件是一个目录文件，则复制该目录下的所有子目录和文件，**复制目录必须用递归选项**，否则只会报错或不复制内容

#### paste

- `paste`
  - merge lines of files
  - `paste [options] [files]`
  - `-d` **d**elimiters，reuse characters from LIST instead of TABs，用指定字符替代原本的默认连接符 TAB```bash
# a.txt
A
B
C
# b.txt
1
2
3
paste a.txt b.txt
A    1
B    2
C    3
paste -d, a.txt b.txt
A,1
B,2
C,3
```

#### mv

- `mv` #<mark>

**m**

</mark>

<mark>

o

</mark>

<mark>

**v**

</mark>

<mark>

e(or rename)

</mark>

 files

  - `-i`，你移动文件到目标位置，如果那里**已经存在**一个同名文件，覆盖前进行询问 **i**nteractive
  - `-f`，覆写前不询问，强制执行 **f**orce
  - `mv a.txt b.txt` # 改名（本质也是移动：从旧名字移动到新名字）
  - `mv a.txt /tmp/` # 移动到目录

#### rm

- `rm` #**r**e**m**ove(delete) a file(directory)

  - `-f`，**f**orce 强制删除，即不询问
  - `-i`，**i**nteractive 删除前进行提示
  - `-R -r`，**r**ecursively 递归删除，用于**删除目录**

#### ln

- `ln [option] source target` #链接文件，**L**i**n**k to another file

  - 注意：`ln` 里的 `l` 是 **lower case 的 L**，不是 `I`
  - `-s` #**s**ymbolic link 符号链接，如 `ln -s /lib/lsb /usr/lj`，即：在 `usr` 目录下建立指向 `/lib/lsb` 目录的 `lj` 文件, 这两个的位置不要混掉了
  - <mark>
  
  无参数默认生成硬链接
  
  </mark>

> Linux 文件的本体不是文件名
> 
> - **文件名**只是目录里的一条“记录”（name → inode）
> - **inode** 才是真正指向数据的“身份编号/实体”
> - 所以你可以让<mark>
> 
> 多个文件名指向同一个 inode（这就是
> 
> </mark>
> 
> <mark>
> 
> **硬链接**
> 
> </mark>
> 
> <mark>
> 
> ）
> 
> </mark>
> 
> **硬链接特点**
> 
> 1. **硬链接和原文件地位完全一样**（都是“门牌号”）
> 2. 删除任何一个名字，只是“少了一个门牌号”
> 
>   - 只有当硬链接数降到 0，文件数据才真的释放
> 3. **硬链接一般不能跨文件系统**（不同硬盘/分区通常不行）
> 4. **通常不能给目录做硬链接**（为了防止目录结构出现环)
> 
> 如何<mark>
> 
> 验证硬链接数
> 
> </mark>
> 
> <mark>
> 
> `ls -l file`
> 
> </mark>
> 
> <mark>
> 
> 会看到第二列 “Number of links” 会变大
> 
> </mark>
> 
> <mark>
> 
> (软连接不会)
> 
> </mark>
> 
> ，可以回去看一下ls -l format这一章

#### unlink

- `unlink filename` #移除链接，必须对文件执行(意思是 `unlink` 通常只删**单个文件名**，不处理目录、也没有 `-r` 递归这种能力（所以删目录一般用 `rm -r`）)，Remove the link

#### find

- `find directory-list [options] [actions] [...]`
  - search for files in a directory hierarchy
  - 可以通过权限、用户、组、文件类型、修改日期、大小等多种条件来查找文件<mark>
  
  (find本身含有递归属性)
  
  </mark>
  - `-name` 按文件名查找```bash
  find . -name "*.txt"
  ```
  - `-print` 打印**结果路径**```bash
  find . -name "*.log" -print
  ```
  - `-newer` 后面加一个文件，查找比其时间更新的
  - `-type d` 按文件类型查找，`d` 为目录(directory)`f`为普通文件(file)```bash
  find . -type d
   find . -type f
  ```
  - `-a/-o/-not` 表示**与或非**
  - `-size` 后面跟 `+` 表示大于，`-` 表示小于，没有表示精确匹配```bash
find . -size +10000c   # 大于 10000 字节
 find . -size -10M      # 小于 10MB
```


  - `-exec COMMAND {} \;` 表示在查找到的文件上执行指定命令。`-exec` 为对查找到的文件执行指定动作
    - 下面例子就是，在目录 `.` 下查找拥有者为 Bill 或大于 10000c 的文件，打印结果，并删除。`-user` 为按文件拥有者查找
    ```shell
    find . \( -user Bill -o -size +10000c \) -print -exec rm {} \;
    # find . 从当前目录开始往下搜（递归整个目录树）
    # \( ... \) 把条件分成一组（必须转义）
    # -user Bill -o -size +10000c 条件：拥有者是 Bill (-o表示或者) 大小 > 10000 字节
    # -print 把命中的文件先打印出来
    # -exec rm {} \; 对命中的每个文件执行 rm 文件路径
    ```
  - `-ok` 为执行命令前需要进行确认，如 `-ok COMMAND {} \;`
  - `-atime n` 为过去 `n` 天内被读取过```bash
  find . -atime 7    # 过去 7 天内被读过
  find . -atime +7   # 超过 7 天没被读过
  ```
  - `~` 为用户主目录，<mark>
  
  `~user`
  
  </mark>
  
   <mark>
  
  代表指定用户的主目录
  
  </mark>
  
  
    - 在 `bill` 和 `denis` 的主目录中找到大于 `1000` 且 `30` 天内被读取过的文件并执行删除命令，执行前需确认```bash
  find ~bill ~denis -size +1000 -atime 30 -ok rm {} \;
  ```

#### cut

- `cut` #extract sections from each line of files

  - `cut [options] [filename]`
  - `-d` use **delimiter** instead of TAB for field delimiter，使用指定分隔符切割列，一般与 `-f` 一同使用
  - `-f` select only these **fields**，选择切割**哪一列**
  - `-b` select only these **bytes 字节**
  - `-c` select only these **characters 字符**
- Some example

  - `cut -d ' ' -f1 cut.txt`，按空格把第一部分切出来
  - `cut -c 5-8 cut.txt`，切割第 5-8 个字符
  - `cut -b -6 cut.txt`，切割第六个字节以前内容，注意：英文一个字符即一字节，但是中文会切出乱码，一个中文字符在UTF8下是3个字节，所以按字节切可能会有乱码的问题
  - `cut -b 2,4,6 cut.txt`，切割文件中第 2、4、6 的字节

#### expand

- `expand` #convert tabs to spaces，第一次作业命令

  - 用于**将文件的制表符（Tab）转换为空格符（Space）**，**默认一个 Tab 对应 8 个空格符**，并将结果输出到标准输出stdout
  - `-t, --tabs=NUMBER` 指定一个 tab 替换为多少个空格，而不是默认的 8

#### man & info

- man 和 info 的区别

  - man 即为说明手册
  
    - `h` 寻求帮助help
    - `/ pattern` **向下**搜索pattern
    - `? pattern` **向上**搜索pattern
- info 中，每个命令对应一个 Info 文件，每个 Info 文件都组织成一棵树，由一系列节点组成，每个节点一个主题，节点之间相互链接

  - <u>
  
  man更简洁更快，info更复杂更系统化
  
  </u>

#### compress

- `compress [-cfv] [-b bits] [file]` #压缩，后缀为 `.Z`
  - `-c` #输出结果至标准输出stdout设备，即终端，不改动原始文件
  - `-f` #强行**f**orce压缩文件，覆盖已经存在的目标文件而不提示
  - `-v` #列出版本**v**ersion信息（通常会输出压缩比、处理过程之类的信息）
  - `-b bits` #设定共同字串数的上限，一般取 16，和<压缩效率>有关。压缩效率是一个介于 9~16 的数值，预设值为"16"，指定愈大的数值，压缩效率就愈高

#### uncompress

- `uncompress [-cfv] [file...]` #解压，`-cfv`和compress是一样的，就是compress的反过程

#### <mark>gzip</mark>

- `gzip [-cdfhlLnNrtvV19] [-S suffix] [file...]` #后缀为 `.gz`
  - <mark>
  
  `不加`
  
  </mark>
  
   <mark>
  
  #压缩，后缀
  
  </mark>
  
  <mark>
  
  `.gz`
  
  </mark>
  - <mark>
  
  `-d`
  
  </mark>
  
   <mark>
  
  #
  
  </mark>
  
  <mark>
  
  **解压**
  
  </mark>
  
  <mark>
  
  缩
  
  </mark>
  
   <mark>
  
  `decompress`
  
  </mark>
  
  <mark>
  
  ，和下面的
  
  </mark>
  
  <mark>
  
  `gunzip`
  
  </mark>
  
  <mark>
  
  是一回事
  
  </mark>
  - <mark>
  
  `-h`
  
  </mark>
  
   <mark>
  
  #在线
  
  </mark>
  
  <mark>
  
  **帮助**
  
  </mark>
  
   <mark>
  
  `help`
  
  </mark>
  - `-l` #**列**出压缩文件的**相关信息** `list`
  - `-L` #显示**版本信息与版权信息** `License`，注意是大写L
  - `-n` #不保存原来的文件名和更改时间 `noname`
  - `-N` #保存原来的文件名和更改时间 `Name`，注意是大写N
  - `-v` #显示执行过程 `verbose`
  - `-V` #显示版本信息 `Version`，注意是大写V
  - `-1~9` #压缩效率，介于 1~9 之间，预设值为 6
  - `-S` #文件后缀`suffix`，默认后缀 `.gz`，可以改成别的
  - `-c`: Write output on standard output; keep original files  unchanged.

#### gunzip

- `gunzip [file...]` #解压缩

#### bzip2 & bunzip2

- `bzip2/bunzip2` #压缩/解压缩，选项和 gzip 大致相同，如 `-d`、`-c`、`-f`、`-数字` 等

#### <mark>wc</mark>

- `wc` #显示文件的行数、单词数和字符数`wc=word count`，display a count of lines, words and characters in a file

  - `wc [-clw] [文件...]`
    - <mark>
    
    `-c`
    
    </mark>
    
     <mark>
    
    #byte/字节数
    
    </mark>
    
     <mark>
    
    `count bytes`
    
    </mark>
    - <mark>
    
    `-m, chars`
    
    </mark>
    
     <mark>
    
    #字符数
    
    </mark>
    
      <mark>
    
    `multibyte characters`
    
    </mark>
    - <mark>
    
    `-w`
    
    </mark>
    
     <mark>
    
    #单词数
    
    </mark>
    
     <mark>
    
    `word`
    
    </mark>
    - <mark>
    
    `-l`
    
    </mark>
    
     <mark>
    
    #行数
    
    </mark>
    
     <mark>
    
    `lines`
    
    </mark>
  - `ls | wc -l`，是把 ls 的结果列出，而不是里面的每个文件都进行 wc
  
    - `ls` 输出的是“当前目录的条目列表”，管道 `|` 把这个列表送给 `wc -l`，`wc -l` 数的是 **ls 输出有多少行**

<table>
<thead>
  <tr>
    <th>
      维度
    </th>
    
    <th>
      字节 (Byte)
    </th>
    
    <th>
      字符 (Character)
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      定义
    </td>
    
    <td>
      计算机存储和计量容量的基本单位。
    </td>
    
    <td>
      人类语言中的最小语义符号。
    </td>
  </tr>
  
  <tr>
    <td>
      组成
    </td>
    
    <td>
      1 字节 = 8 位 (bit)。
    </td>
    
    <td>
      一个字符由 1 个或多个字节组成。
    </td>
  </tr>
  
  <tr>
    <td>
      举例
    </td>
    
    <td>
      01000001 (二进制)
    </td>
    
    <td>
      'A', '中', '😊', '9'
    </td>
  </tr>
  
  <tr>
    <td>
      稳定性
    </td>
    
    <td>
      在任何系统里，1 字节永远是 8 位。
    </td>
    
    <td>
      同一个字符在不同编码下，占用的字节数不同。
    </td>
  </tr>
</tbody>
</table>

#### <mark>diff</mark> & tkdiff

- `diff` **diff**erence#compare files line by line，逐行比较差异，常用于比较文本文件的不同版本
  - `diff [``file1``] [file``2``]`
  - `tkdiff file1 file2` #并排查看文件差异的工具，**图形化**的展示形式，a graphic diff utility
  `-q`：没有差异不输出，有差异才输出。<br />

`-cNUM`：输出有差异的附近上下各NUM行（一般默认上下各3行）结尾行数不够不会补行<br />

`-uNUM`：输出有差异的附近上下各NUM行（一般默认上下各3行）结尾行数不够不会补行<br />

上述两个区别主要在于**输出格式**不同：`-c` 是 *context* 格式，`-u` 是 *unified* 格式

#### <mark>grep</mark>

- `grep [options] [``regexp``] file` #命令 参数 匹配模式 文件 grep=**G**lobal **R**egular **E**xpression **P**rint全局正则表达式打印

  - print lines that match patterns
  - <mark>
  
  `-i, --ignore-case`
  
  </mark>
  
   <mark>
  
  #忽略大小写的差别
  
  </mark>
  
   <mark>
  
  `i = ignore case`
  
  </mark>
  - <mark>
  
  `-n, --line-number`
  
  </mark>
  
   <mark>
  
  #标出行号
  
  </mark>
  
   <mark>
  
  `n=number`
  
  </mark>
  - `-o`：只显示匹配的内容 `o = only match`
  - <mark>
  
  `-r, --recursive`
  
  </mark>
  
   <mark>
  
  #递归查找匹配
  
  </mark>
  
   <mark>
  
  `r=recursive`
  
  </mark>
  - <mark>
  
  `-c, --count`
  
  </mark>
  
   <mark>
  
  #计算符合样式的行数
  
  </mark>
  
   <mark>
  
  `c=count`
  
  </mark>
  - `-f file, --file=file` #指定规则文件，如 `grep -f test1 test2`，为找出 2 中与 1 的相同行
- `grep static ./*.c`: 在当前目录下所有的 `.c` 源文件中搜索字符串 "static"。
- `grep ^# *.cpp`: 在所有 `.cpp` 文件中查找以 `#` 开头的行（通常用于找预处理指令）。其中 <mark>

`^`

</mark>

 是正则表达式，表示“行首”。//`$` : 匹配行尾
- `man find | grep -ci perm`: 这是一个组合命令。

  - 通过管道符 `|` 将 `find` 命令的帮助文档传给 `grep`。
  - 搜索包含 "perm"出现过多少次（不区分大小写）
- `piano% grep -ni Event main.c`
  - **-n**: 显示行号。
  - **-i**: 忽略大小写（所以能搜到 "Event"、"event" 或 "EVENT"）。
  - **Event**: 搜索关键词。
  - **main.c**: 目标文件。

##### <mark>find和grep区别</mark>

<mark>

**find**

</mark>

 <mark>

**找的是“东西”（文件/目录），而**

</mark>

 <mark>

**grep**

</mark>

 <mark>

**找的是“内容”（文字/代码）。**

</mark>



#### <mark>which</mark>

- `which` #定位一个命令，**显示路径或别名**。locate a command; display its pathname or alias

  - 使用方法：`which command`

#### <mark>file</mark>

- `file` - determine file type #确定文件类型，比如某个.txt文件可能是.mp4改后缀，打不开了，查看具体是什么

  - `file filename`

#### <mark>whatis</mark>

- `whatis` - search the whatis database for word #显示在线手册说明，在 whatis 数据库中查找单词

  - 用于查询命令用途，会比man更简洁
  - `whatis command` 也即 **what is** command

#### <mark>aprop</mark><mark>o</mark><mark>s</mark>

- `apropos` - search the whatis database for string，就是在whatis数据库里面进行<mark>

模糊搜索

</mark>

，apropos: 关于....的

  - 等于 `man -k`，用法为 `apropos command`

#### <mark>sort</mark>

- **sort** - sort, merge, or sequence check text files. **Sort lines of files**
  - 默认 `sort` 将文件的<mark>
  
  **每一行作为一个单位**
  
  </mark>
  
  ，相互比较，比较原则是从首字符向后，依次按 ASCII 码值进行比较，最后将他们按**升序输出**，注意是字符串排序，所以`10`会在`2`前面
  - `-u`（u = **u**nique）去除重复行，不止去重，排序+去重
  - `-r`（r = **r**everse）降序
  - `-o`（`--output=file`），将结果输出到文件，而不是标准输出stdout```bash
  sort -r number.txt -o number.txt
  ```
  - `-n`（`--numeric-sort`），按数值进行排序。否则会出现 10 排在 2 前面的情况，因为 1 比 2 字符上小
  - <mark>
  
  可以利用
  
  </mark>
  
   <mark>
  
  `-t`
  
  </mark>
  
   <mark>
  
  设定间隔符，
  
  </mark>
  
  <mark>
  
  `-k`
  
  </mark>
  
   <mark>
  
  指定列数
  
  </mark>
  
  ```bash
  sort -k 2 -t : facebook.txt
  apple:10:2.5
  orange:20:3.4
  banana:30:5.5
  pear:90:2.3
  ```
  
  
    - <mark>
    
    `-t :`
    
    </mark>
    
     <mark>
    
    ：用冒号切开
    
    </mark>
    - <mark>
    
    `-k 2`
    
    </mark>
    
     <mark>
    
    ：按第2列排序（默认还是字符串排序）
    
    </mark>
- **apt-get** #软件包处理 APT package handling utility, software package handling for Linux

  - `apt-get` `update` #更新软件包列表
  - `apt-get install/remove` 软件，安装/卸载软件包

## saying source code line (with many meta characters) in English

何意味
