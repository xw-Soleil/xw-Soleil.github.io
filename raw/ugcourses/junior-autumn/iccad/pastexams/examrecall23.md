# 不知名回忆卷 2/3

> 历年考卷回忆整理 2、3

<alert title="阅读说明" type="info">

- 这套是缓考卷，没有选择题；回忆卷 2（docx）和回忆卷 3（PDF）是同一张卷子，所以合在一页
- 正文按原卷顺序排列，题号与原卷一致；题干照抄原卷，缩写题原卷回忆时直接写了全称，这里只留缩写，全称放进答案
- 绿色的「答案」块里是答案和补充讲解，默认遮住，点一下查看单个答案；也可以 <answer-toggle>



</answer-toggle>
</alert>

**原卷**（回忆版）
<embed src="/pdf/ICCAD-Recall-23.pdf" width="100%" height="600" type="application/pdf">



</embed>



## 一、缩写注释

<alert title="题目" type="question">

缩写注释（英语全称，中文解释，10 个 20 分）

</alert>

IC　CAD　GNU　GUI　LAN　NFS　HTTP　DNS　HTML　IP

<answer>

1. IC <mark>

(Integrated Circuit)

</mark>

 集成电路，把晶体管、电阻等大量元件集成在一块芯片上，实现计算/存储/控制等功能。
2. CAD <mark>

(Computer Auxiliary Design)

</mark>

 计算机辅助设计，用软件辅助完成设计与制图/建模/验证，提高设计效率与准确性（电子、机械都用）。
3. GNU <mark>

(GNU is Not Unix!)

</mark>

 自由软件项目与工具链集合（如 gcc、bash 等），目标是提供“类 Unix 但自由”的完整系统。
4. GUI <mark>

(Graphical User Interface)

</mark>

 用户图形界面，用窗口、图标、菜单等图形方式与系统交互。
5. LAN <mark>

(Local Area Network)

</mark>

 局域网，在小范围（宿舍/实验室/公司）内连接设备的网络，速度高、延迟低，常见以太网/Wi-Fi
6. NFS <mark>

(Network File System)

</mark>

 网络文件系统，让你像访问本地目录一样访问远程服务器共享的目录，常用于 Linux/Unix 环境的共享存储。
7. HTTP <mark>

(Hyper Text Transfer Protocol)

</mark>

 超文本传输协议，浏览器与网站服务器通信的基础协议，采用请求/响应模式
8. DNS <mark>

(Domain Name ~~Server~~ System)

</mark>

 域名系统/解析服务，把域名（如 `www.xxx.com`）解析成 IP 地址
9. HTML <mark>

(Hyper Text Markup Language)

</mark>

 超文本标记语言，网页的结构描述语言（标题、段落、链接、表格等），常与 CSS/JS 配合。
10. IP <mark>

(Internet Protocol)

</mark>

 互联网协议，网络层的基础协议，负责寻址与路由，把数据包从一台主机送到另一台（IPv4/IPv6）。

</answer>

## 二、单词解释

<alert title="题目" type="question">

单词解释（中文加英文，10 个 20 分）。原卷只回忆出下面 9 个。

</alert>

**apropos**

<answer>

**Main function:** Search the **man/whatis database** for manual page names and descriptions matching a keyword

在 man/whatis 数据库中按照关键字搜索相关手册描述，命令名字和简短描述

**Syntax:** `apropos [keyword]` <=> `man -k [keyword]`

</answer>

**sudo**

<answer>

**Main function:** Run commands as another user, (default is root), typically for temporary privilege elevation. The most common use is to run command with administrator/superuser privileges

以其他用户身份（默认为 root 超级用户）执行命令，通常用于临时提权，最常用的情况就是以超级用户权限运行命令

**Syntax:** `sudo [command]` or `sudo -u username [command]`

</answer>

**df**

<answer>

**Main function:** Shows disk space usage of mounted file systems

显示挂载的文件系统的磁盘使用情况

**Syntax:** `df [option] [filesystem]`

- `df -i` Displays inode usage instead of disk block usage
- `df -k` Displays disk usage in kilobytes (KB)

</answer>

**xterm**

<answer>

**Main function:** Opens a terminal window under the X Window System ｜ 打开一个X Window系统的终端窗口

**语法 Syntax:**

```bash
xterm [options]

#举例子
xterm -e top
xterm -e "bash"
```

`xterm -e [command]` 表示打开xterm终端并且执行command ｜ Open an xterm terminal and execute the command.

</answer>

**gdb**

<answer>

**Main function:** GNU debugger for debugging programs ｜ GNU调试工具,用于调试程序

`gdb` is used to locate and debug program errors，Breakpoints, step execution, and variable inspection are core features。

**Syntax:**

```bash
gdb [program] [core]
```

- `program`：Executable file to be debugged ｜ 要调试的可执行文件
- `core`：Core dump file (optional) ｜ core dump 文件（可选）

**常用命令 Common commands:**

```text
- gdb
  - list            # 列出源代码
                    # List source code
  - br n            # 在第 n 行设置断点（br = break）
                    # Set a breakpoint at line n
  - run             # 运行程序
                    # Run the program
  - print x         # 打印变量 x 的值
                    # Print the value of variable x
  - next            # 执行下一行（不进入函数）
                    # Execute next line without stepping into functions
  - where           # 显示当前调用的函数和行号
                    # Show call stack and current line number
  - help            # 显示可用命令
                    # Show available commands
  - quit            # 退出 gdb
                    # Exit gdb
```

**编译要求 Compile requirement:** To enable debugging, compile the program with `-g`

```bash
gcc -g main.c -o main
```

</answer>

**ln**

<answer>

**Main function:** Creates hard links or symbolic links to files ｜ 创建文件或目录的硬链接/软链接

**Syntax:** `ln [option] source target`

- `-s` create symbolic link ｜ 创建符号链接(软链接)
- `-f` force creation ｜ 强制创建,覆盖已存在文件

</answer>

**chmod**

<answer>

**Main function:** Changes file or directory access permissions ｜ 改变文件或目录的访问权限

**Syntax:** `chmod [option] mode file`

- `-R` recursively change directories and their contents ｜ 递归修改目录及其内容
- mode:

  - numeric mode (e.g., 755)
  - symbolic (e.g., u+x)

</answer>

**top**

<answer>

**Main function:** Displays running processes and system resource usage in real-time ｜ 实时显示系统进程和资源使用情况

**Syntax:** `top [options]`

- `-d` 设置刷新间隔 set delay time interval
- `-u` 显示指定用户的进程 display specific user's processes

</answer>

**cat**

<answer>

**Main function:** Displays file contents or concatenates files ｜ 显示文件内容或连接多个文件

**Syntax:** `cat [option] [files]`

- `-n` 显示行号 number all output lines

</answer>

## 三、句子解释

<alert title="题目" type="question">

句子解释（每一个细节全部写出来，包括标点符号，后给总体翻译，8 题 23 分）。原卷只回忆出下面 6 题。

</alert>

**1.** `alias rm ="rm -i"; alias`

<answer>

- **逐字解释:**
  - `alias` - alias命令,用于创建命令别名
  - `rm` - 要创建别名的命令名称
  - `=` - 赋值符号
  - `"rm -i"` - 双引号包围的实际命令
  
    - `rm` - remove命令,删除文件
    - `-i` - interactive选项,交互模式,删除前确认
  - `;` - 分号,命令分隔符
  - `alias` - 再次调用alias命令(无参数时列出所有别名)
- **整体翻译:**
  - 将rm命令设置别名为"rm -i"(删除前需确认),然后列出所有当前的别名。
  - Sets an alias for rm command to "rm -i" (requires confirmation before deletion), then lists all current aliases.

</answer>

**2.** `find /usr -name XErrdb -print 2> /dev/null`

<answer>

- **逐字解释:**
  - `find` - 查找文件命令
  - `/usr` - 搜索的起始目录路径
  - `-name` - 按名称查找选项
  - `XErrdb` - 要查找的文件名
  - `-print` - 打印找到的文件路径
  - `2>` - 重定向标准错误输出(stderr)
  - `/dev/null` - 空设备,丢弃所有写入的数据
- **整体翻译:**
  - 在/usr目录下查找名为XErrdb的文件并打印路径,错误信息丢弃到/dev/null(不显示错误)。
  - Searches for files named XErrdb in /usr directory and prints their paths, while discarding error messages to /dev/null.

</answer>

**3.** `sudo mount /dev/sdb2 ./disk ; du -sk`

<answer>

- **逐字解释:**
  - `sudo` - 以超级用户权限执行
  - `mount` - 挂载文件系统命令
  - `/dev/sdb2` - 第二块硬盘的第二个分区
  - `./disk` - 当前目录下的disk目录(挂载点)
  - `;` - 分号,命令分隔符
  - `du` - disk usage,磁盘使用统计命令
  - `-s` - summary,只显示总计
  - `-k` - 以KB为单位显示
- **整体翻译:**
  - 以管理员权限将/dev/sdb2分区挂载到当前目录的disk文件夹,然后显示磁盘使用总量(以KB为单位)。
  - Mounts /dev/sdb2 partition to ./disk directory with admin privileges, then displays total disk usage in KB.

</answer>

**4.** `cd ~/src;chmod 764 * ; chmod o+r *.[Pp]ng`

<answer>

- **逐字解释:**
  - `cd` - change directory,切换目录命令
  - `~/src` - 用户家目录下的src文件夹
  
    - `~` - 家目录符号
    - `/src` - src子目录
  - `;` - 分号,命令分隔符
  - `chmod` - change mode,修改权限命令
  - `764` - 权限数字:所有者(7=rwx),组(6=rw-),其他(4=r--)
  - `*` - 通配符,匹配所有文件
  - `o+r` - 其他用户(others)添加(+)读权限(r)
  - `*.[Pp]ng` - 通配符,匹配.png或.Png结尾的文件
  
    - `*` - 任意文件名
    - `.` - 点号
    - `[Pp]` - P或p字符
    - `ng` - ng字符
- **整体翻译:**
  - 切换到家目录的src文件夹,将所有文件权限改为764(所有者读写执行,组读写,其他只读),然后给所有.png或.Png文件的其他用户添加读权限。
  - Changes to ~/src directory, sets all files to 764 permissions (owner: rwx, group: rw-, others: r--), then adds read permission for others to all .png or .Png files.

</answer>

**5.** `gcc -o tri triangle.c -lm`

<answer>

- **逐字解释:**
  - `gcc` - GNU C Compiler,GNU C编译器
  - `-o` - output,指定输出文件名选项
  - `tri` - 输出的可执行文件名
  - `triangle.c` - 源代码文件名
  - `-lm` - 链接数学库选项
  
    - `-l` - link library,链接库
    - `m` - math,数学库
- **整体翻译:**
  - 使用gcc编译器将triangle.c源文件编译为名为tri的可执行文件,并链接数学库。
  - Compiles triangle.c source file into an executable named tri using gcc compiler, linking the math library.

</answer>

**6.** `gzip -d cube.tar.gz | tar -tvf cube.tar | tar -xvf cube.tar /home`（这条的名称忘了，大概长这样）

<answer>

原卷这条是回忆者凭印象写的，下面按通顺的写法 `gzip -dc cube.tar.gz | tar -xvf - -C /home` 来解释。

- **逐字解释:**
  - `gzip` - GNU zip 压缩/解压工具 ｜ GNU zip compression/decompression tool
  - `-d` - decompress，解压 ｜ Decompress
  - `-c` - write to stdout，将结果输出到标准输出 ｜ Write output to standard output
  - `cube.tar.gz` - gzip 压缩的 tar 归档文件 ｜ gzip-compressed tar archive
  - `|` - 管道符，将前一个命令的输出传给下一个命令 ｜ Pipe, passes output of previous command to the next
  - `tar` - tape archive，用于处理 tar 归档文件 ｜ Tool for handling tar archives
  
    - `-x` - extract，解压文件 ｜ Extract files
    - `-v` - verbose，显示详细过程 ｜ Verbose output
    - `-f -` - file，指定归档文件，`-` 表示从标准输入读取归档内容 ｜ Read archive from standard input
  - `-C /home` - 指定解压目录为 /home ｜ Change extraction directory to /home
- **整体翻译:**
  - 将 cube.tar.gz 解压，通过管道传递给 tar，并把其中的内容解压到 /home 目录下。
  - Decompress cube.tar.gz and pipe it to tar, extracting its contents into the /home directory.

</answer>

## 四、问答

<alert title="题目" type="question">

问答（可以使用中文，如果你的英语不行的话，8 题 27 分）

</alert>

**1.** EDA meaning？Big-3 of EDA company and these product？

<answer>

- EDA means **Electronic Design Automation,** software tools used to design, simulate, verify, and manufacture integrated circuits (ICs) and electronic systems.
- Big-3 of EDA

  1. Synopsys
  
    - **VCS** – RTL simulation
    - **Design Compiler** – logic synthesis
  2. Cadence
  
    - **Virtuoso** – analog IC design
  3. Siemens EDA (Mentor Graphics)
  
    - **Questa** – simulation

</answer>

**2.** Ubuntu，what is it？What mean in Africa？

<answer>
<mark>

Ubuntu is a Linux operating system based on desktop applications.

</mark>



Ubuntu is named after the Nguni philosophy of ubuntu, which Canonical indicates means "humanity to others" with a connotation of "I am what I am because of who we all are".

<mark>

Ubuntu (African meaning) is "I am because where we are"，

</mark>

Meaning: Humanity、Community、Sharing、Mutual respect

</answer>

**3.** How to use manul？How to read it in vim？Write other two way to open manul？

<answer>

- Basic usage: `man ls`
- Read `man` page in Vim: `man ls | vim -` or `MANPAGER=vim man ls`
- Two other ways to open manuals

  1. `info`: `info ls`
  2. `--help`: `ls --help` (Short and fast reference)

</answer>

**4.** Three disk？What change when use them？

<answer>

- HDD (Hard Disk Drive)：Mechanical、cheap、slow、large capacity
- SSD (Solid State Drive)：Flash memory、Fast、No moving parts、Expensive per GB
- NVMe SSD：Uses PCIe bus、Much faster than SATA SSD、Low latency

</answer>

**5.** Meta characters： /　\　&　*

<answer>

Slash、backslash、ampersand、asterisk

</answer>

**6.** Write a makefile and explain it

<answer>

NULL，原整理没有写答案（等下记得复习 makefile 和 touch），可以参考 20-21 卷简答题第 2 题。

</answer>

**7.** grep ->r,e,p meaning? How to use grep?

<answer>

- meaning：

  - **g**: global
  - **re**: regular expression
  - **p**: print
- Use

  - Basic usage: `grep "main" file.c`
  - Common options

```bash
grep -i "error" log.txt     # ignore case
grep -r "TODO" src/         # recursive
grep -n "printf" main.c     # show line number
```

</answer>

**8.** In ftp，pwd and !pwd meaning? Use an example

<answer>

- `pwd`: Shows **remote server directory**
- `!pwd`: Runs command on **local machine**

```bash
ftp> pwd
257 "/home/ftpuser"

ftp> !pwd
/home/soleil
```

</answer>

## 五、写代码

<alert title="题目" type="question">

写一个代码，并解释（10 分）。要求：输入 dir_name，列这个地址中的所有文件，包括文件夹里面所有文件，并统计数目

</alert>

<answer>

```bash
#!/bin/bash

read -p "输入目录: " dir_name

if [ ! -d "$dir_name" ]; then
    echo "目录不存在"
    exit 1
fi

echo "所有文件:"
find "$dir_name" -type f

echo ""
echo "文件总数: $(find "$dir_name" -type f | wc -l)"
```

</answer>

## 六、附加题

<alert title="题目" type="question">

附加题（8 分，only English）

</alert>

**1.** How to use vi read？Write more , point more.

**2.** You have two computer : one windows computer, one linux computer. If you have linux-like software in windows computer. What thing you should do?

这两道暂无答案。
