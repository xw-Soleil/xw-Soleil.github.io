# Chapter 2：Introduction to Unix

> Unix 基础导论：详细版笔记

## Early History of Unix | 早期历史

#### Unix 发展历史详解

<table>
<thead>
  <tr>
    <th>
      年代
    </th>
    
    <th>
      主要事件/项目
    </th>
    
    <th>
      关键人物/组织
    </th>
    
    <th>
      主要贡献/意义
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      1960s
    </td>
    
    <td>
      Multics 项目
    </td>
    
    <td>
      MIT, GE, AT&T 贝尔实验室
    </td>
    
    <td>
      - 旨在创建多用户、分时操作系统<br />
      
      - 理念超前但过于复杂，AT&T最终退出<br />
      
      - 为Unix的诞生提供了反思和经验教训
    </td>
  </tr>
  
  <tr>
    <td>
      1970s
    </td>
    
    <td>
      Unix 诞生与发展
    </td>
    
    <td>
      Ken Thompson, Dennis Ritchie (贝尔实验室)
    </td>
    
    <td>
      - 1969年: Thompson开发出Unix的第一个版本<br />
      
      - 1972年: Ritchie发明C语言，并用C语言重写了Unix内核<br />
      
      - 意义: C语言的出现使Unix具备了前所未有的可移植性
    </td>
  </tr>
  
  <tr>
    <td>
      1970s/80s
    </td>
    
    <td>
      BSD Unix
    </td>
    
    <td>
      Bill Joy (加州大学伯克利分校 - UCB)
    </td>
    
    <td>
      - 开发了 Berkeley Software Distribution (BSD)<br />
      
      - 引入了虚拟内存、TCP/IP网络协议栈等重要功能<br />
      
      - 成为学术界和许多商业Unix的重要分支
    </td>
  </tr>
  
  <tr>
    <td>
      1980s
    </td>
    
    <td>
      Unix的商业化与新浪潮
    </td>
    
    <td>
      众多商业公司；<br />
      
      Richard Stallman
    </td>
    
    <td>
      - 商业化与碎片化: AT&T开始商业化Unix，导致出现大量不兼容的商业版本 (如HP-UX, AIX, Solaris等)<br />
      
      - DOS/Windows: 借鉴了Unix的目录结构等设计思想<br />
      
      - GNU项目启动: Stallman为反对软件商业化，发起了GNU项目，旨在创建一套完全自由的类Unix系统
    </td>
  </tr>
</tbody>
</table>

> GNU——GNU Not Unix (实际上是一个递归形式)

### The Inventors

Ken Thompson、Dennis Ritchie

ACM Turing Award winners, 1983

### C Language as Byproduct

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ICCAD/DetailCh2-01.webp)

#### C语言的诞生：一个副产品

- **问题**
  - 需要将 Unix 移植到其他平台
  - Unix 是用汇编语言编写的
- **解决方案**
  - 使用 'B' 语言重写 Unix
  - 为适配 Unix 进行了大量修改
- **更名为 'C'**
  - 同时具备高级和低级编程语言的特性
  - 增强了可移植性
  - 更容易改进和增强 Unix

### 两位 “反叛者”颠覆了软件世界：

- **理查德·斯托曼 (Richard Stallman)** 是思想家，他发起了“自由软件”运动和GNU项目，为开源世界奠定了哲学和法律基石。
- **林纳斯·托瓦兹 (Linus Torvalds)** 是实干家，他创造了Linux内核。这个改变世界的项目，起初只是他发布在网络论坛上的一个“业余爱好”。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ICCAD/DetailCh2-02.webp)

这张“家族树”图片简洁地介绍了主流操作系统的演变史，核心要点如下：

1. 共同的祖先：
2. 图中的绝大多数操作系统，都源自于同一个祖先——诞生于1969年的 Unix 系统。
3. 两大主要分支：
4. 从早期的Unix开始，逐渐分化为两大阵营：

  - **商业闭源分支 (红色部分)**：以 AT&T 的 **System V** 为代表，衍生出了许多商业公司的闭源Unix系统，比如 IBM 的 AIX、惠普的 HP-UX 和 Sun/Oracle 的 Solaris。
  - **学术/开源分支 (绿色部分)**：以伯克利大学的 **BSD** 为代表，它衍生出了 FreeBSD、OpenBSD 等一系列重要的开源系统，并且苹果的 **macOS** 也深受其影响（图中标为橙色混合源码）。
5. 独立的力量 (Linux)：
6. 左侧的 Linux (绿色部分) 是一个非常特殊的存在。它不是Unix的直接代码后代，而是一个从零开始编写的“类Unix”系统。自诞生起就完全开源，并发展成如今最庞大、最成功的开源操作系统家族。

这张图清晰地展示了操作系统从单一的闭源祖先 (Unix)，如何一步步演化和分裂，并最终形成了由 Linux 和 BSD 家族主导的、繁荣的开源生态。

> **linux 是 unix 么？ 法律上不是 但是属于 unix-like**

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ICCAD/DetailCh2-03.webp)

**这张图展示了当今主流的、属于“Unix家族”的操作系统。**

它们主要分为两大类：

1. **商业系统**：

  - 传统的商业版Unix，如 Oracle 的 Solaris、HP的 HP-UX 和 IBM 的 AIX。
  - 苹果的 macOS（其底层基于BSD）。
2. **免费开源系统**：

  - **BSD 家族**：如 NetBSD, FreeBSD, OpenBSD。
  - **Linux 家族**：基于 Linus Torvalds 的 Linux 内核，发展出了众多“发行版”，如 Red Hat、Ubuntu、Debian 等。

右下角的两个吉祥物分别是 **GNU 的牛羚**和 **Linux 的企鹅**，它们共同代表了完整的 GNU/Linux 操作系统。

## Free Software License Types

- **Public Domain：** authors waive all copyright

> 任意做都行

- **MIT/BSD Licenses：**  OK to copy, redistribute and modify（修改、商业化） as long as,

  - you respect the identity and rights of the author
  - you agree not sue（起诉） the author over software quality
- **GNU General Public License (GPL)：** requires in addition that any derived work distributed or published

  - must be licensed under the terms of the GPL
  - must have its source code made publicly available

1. **公共领域 (Public Domain)**
  - **最宽松**：作者完全放弃版权，任何人可以不受任何限制地使用。
2. **MIT / BSD 许可证**
  - **比较宽松**：你可以自由地复制、修改和重新分发代码，甚至用于商业闭源软件。
  - **条件**：只需在你的产品中保留原作者的版权声明即可。
3. **GNU 通用公共许可证 (GPL)**
  - **最严格（具有“传染性”）**：除了拥有修改和分发的自由外，它还有一个关键要求：
  - **条件**：任何修改或使用了GPL代码并公开发布的新软件，**其本身也必须采用GPL许可证并公开源代码**。这个特性保证了软件的自由和开源属性会一直传递下去。

## Unix 的设计哲学：

其精髓是追求 **灵活性、自由和简洁**，主要体现在以下几个关键原则上：

1. 工具箱方法 (Toolbox Approach)：
核心理念是“每个程序只专注于做好一件事”。系统由大量小而专的工具组成，用户可以将这些工具灵活地组合起来，完成复杂的任务。
2. 一切皆文件 (Everything is a file)：
这是一个强大的抽象概念。无论是硬件设备（如打印机、硬盘）、网络连接还是普通数据，在Unix中都被视为文件，可以用统一的方式进行读写操作，极大地简化了编程。
3. 小即是美 (Small is beautiful)：
崇尚简单、清晰的设计，认为“少即是多”。鼓励用小巧、易于理解和维护的程序来解决问题。

## 操作系统结构

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ICCAD/DetailCh2-04.webp)

从内到外的结构层次为：

1. **硬件 (Hardware)**：位于最中心，是计算机的物理实体，如CPU、内存、硬盘等。
2. **内核 (Kernel)**：操作系统的核心部分。它直接包裹并管理硬件，是唯一有权限直接与硬件交互的软件。
3. **系统调用 (System Calls)**：这是内核提供给外层程序的“服务窗口”或接口。它是一套预先定义好的指令，程序通过它来请求内核的服务。
4. **程序 (Programs)**：最外层是我们日常使用的应用程序。它们不能直接访问硬件。

工作原理总结：

当一个程序（比如Word）需要保存文件时，它不能直接操作硬件（硬盘）。它必须通过系统调用向内核发出“请帮我保存文件”的请求，内核接收到请求后，再安全地替程序完成硬件操作。

这种分层结构的核心目的在于**保护和隔离**，确保用户程序不会直接弄乱硬件，从而保障整个系统的稳定和安全。

## 文件树

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ICCAD/DetailCh2-05.webp)

## Unix Programs

- Shell is the command line interpreter
- Shell is just another program
- A program or command interacts with the  kernel may be any of:

  - built-in shell command
  - interpreted script
  - compiled object code file
- 当你在 Shell 中输入一个命令时，它通常是以下三种类型之一：

  - **内建命令 (built-in)**：由 Shell 程序自身直接处理的命令，例如 `cd`。
  - **解释型脚本 (script)**：一个由解释器（如 python 或 bash 自身）逐行读取并执行的文本文件。
  - **编译后的程序文件 (compiled file)**：一个独立的可执行文件，系统中的大部分命令（如 `ls`, `grep`）都属于这一类。

### Command Line Structure

#### 1 . 命令的结构

一个标准的 Unix 命令由三部分构成，并用空格隔开：

command options arguments

- **command (命令)**：你要执行的程序名，例如 `ls`。
- **options (选项)**：调整命令的行为，通常以 `-` 开头，例如 `-l`。
- **arguments (参数)**：命令要操作的对象，例如文件名或目录名。
**示例**：`ls -l /home`

#### 2 . 关键使用技巧

- **大小写敏感 (Case Sensitive)**：在 Unix 中，`File1` 和 `file1` 是两个完全不同的文件。命令和文件名通常都使用小写。
- **查阅帮助手册 (man page)**：并非所有命令都遵循相同的标准。要知道一个命令的具体用法和选项，应使用 `man` 命令来查看它的手册 (例如: `man ls`)。
- **终止命令 (Terminate Command)**：如果一个命令正在运行且你想强制停止它，最常用的方法是按下 `Ctrl+C`。

#### 注意attention

- 并非所有的 Unix 命令都遵循相同的标准。
- 一个命令的选项和语法都列在该命令的“man page”（手册页）中。
- 请注意 Unix 是区分大小写的。
- — 通常使用小写字母。
- 要终止一个命令：
- — ^C 中断 (^C 通常指 Ctrl+C)
- — ^D 可能也有效；可以注销用户；此功能经常被禁用 (^D 通常指 Ctrl+D)

### 具体指令

#### man相关指令

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ICCAD/DetailCh2-06.webp)

#### 其他指令

### 文件系统 ｜ file system

#### 文件系统的思想——Everything is a file

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ICCAD/DetailCh2-07.webp)

#### 文件树

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ICCAD/DetailCh2-08.webp)

##### 根目录与主要目录

<table>
<thead>
  <tr>
    <th>
      目录
    </th>
    
    <th>
      全称
    </th>
    
    <th>
      说明
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      /
    </td>
    
    <td>
      slash/root
    </td>
    
    <td>
      根目录，整个文件系统的起点
    </td>
  </tr>
  
  <tr>
    <td>
      /bin
    </td>
    
    <td>
      binary
    </td>
    
    <td>
      基本命令二进制文件（如 ls, cp, mv）
    </td>
  </tr>
  
  <tr>
    <td>
      /sbin
    </td>
    
    <td>
      system binary
    </td>
    
    <td>
      系统管理命令（需要 root 权限）
    </td>
  </tr>
  
  <tr>
    <td>
      /etc
    </td>
    
    <td>
      etcetera
    </td>
    
    <td>
      系统配置文件目录
    </td>
  </tr>
  
  <tr>
    <td>
      /lib
    </td>
    
    <td>
      library
    </td>
    
    <td>
      系统共享库文件
    </td>
  </tr>
  
  <tr>
    <td>
      /usr
    </td>
    
    <td>
      unix system resources
    </td>
    
    <td>
      用户程序和数据（非 user）
    </td>
  </tr>
  
  <tr>
    <td>
      /var
    </td>
    
    <td>
      variable
    </td>
    
    <td>
      可变数据文件（日志、缓存等）
    </td>
  </tr>
  
  <tr>
    <td>
      /tmp
    </td>
    
    <td>
      temporary
    </td>
    
    <td>
      临时文件目录（非 template）
    </td>
  </tr>
  
  <tr>
    <td>
      /home
    </td>
    
    <td>
      home
    </td>
    
    <td>
      用户主目录
    </td>
  </tr>
  
  <tr>
    <td>
      /root
    </td>
    
    <td>
      root
    </td>
    
    <td>
      root 用户的主目录
    </td>
  </tr>
  
  <tr>
    <td>
      /dev
    </td>
    
    <td>
      device
    </td>
    
    <td>
      设备文件目录
    </td>
  </tr>
  
  <tr>
    <td>
      /proc
    </td>
    
    <td>
      process
    </td>
    
    <td>
      进程和内核信息的虚拟文件系统
    </td>
  </tr>
  
  <tr>
    <td>
      /sys
    </td>
    
    <td>
      system
    </td>
    
    <td>
      系统和硬件信息
    </td>
  </tr>
  
  <tr>
    <td>
      /opt
    </td>
    
    <td>
      optional
    </td>
    
    <td>
      可选的第三方软件包
    </td>
  </tr>
  
  <tr>
    <td>
      /boot
    </td>
    
    <td>
      boot
    </td>
    
    <td>
      启动加载器文件（内核、initrd）
    </td>
  </tr>
  
  <tr>
    <td>
      /mnt
    </td>
    
    <td>
      mount
    </td>
    
    <td>
      临时挂载点
    </td>
  </tr>
  
  <tr>
    <td>
      /media
    </td>
    
    <td>
      media
    </td>
    
    <td>
      可移动设备挂载点
    </td>
  </tr>
  
  <tr>
    <td>
      /srv
    </td>
    
    <td>
      service
    </td>
    
    <td>
      服务数据目录
    </td>
  </tr>
</tbody>
</table>

###### 常见子目录

- `/usr/bin` - 用户命令
- `/usr/lib` - 用户程序库
- `/usr/local` - 本地安装的软件
- `/usr/src` - 源代码（source）
- `/var/log` - 系统日志
- `/var/tmp` - 持久化临时文件

##### 其他系统派生文件树

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ICCAD/DetailCh2-09.webp)

##### Identifying Files in the Tree ｜ 绝对路径与相对路径

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ICCAD/DetailCh2-10.webp)

#### File Structures on Disk

Disk里面是以文件块来进行管理的

##### 基本组织方式

- **挂载**：磁盘挂载到文件树的某个位置
- 块划分：磁盘被划分为固定大小的块

  - 常见块大小：512B、1024B、2048B

##### 磁盘分区的三大组成部分

1. 数据块 (Data Blocks)

- **作用**：存储文件的实际内容
- **特点**：大文件会占用多个连续或分散的数据块
- **类比**：储物柜中存放物品的格子

1. inode (索引节点)

- **作用**：存储文件的元数据（描述信息）
- 包含信息：

  - 文件大小、时间戳（创建/修改时间）
  - 所有者、用户组
  - 权限（rwx）
  - **数据块指针列表**（指向文件内容的位置）
- 特点：

  - 每个文件/目录有唯一的 inode 编号
  - 系统通过 inode 而非文件名识别文件
- **类比**：贴在格子上的信息标签

1. 超级块 (Superblock)

- **作用**：记录整个文件系统的全局信息
- 包含信息：

  - 数据块和 inode 的总数与剩余数
  - 文件系统大小、块大小
  - 文件系统状态（挂载时间、健康检查标志）
- 重要性：

  - 超级块损坏会导致整个分区无法访问
  - 系统会在多处保存备份副本
- **类比**：整个仓库的总账本

###### 文件访问流程

1. **查找文件名** → 从目录获取 inode 编号
2. **读取 inode** → 获取元数据和数据块指针
3. **读取数据块** → 根据指针获取文件内容
4. **读取超级块** → 挂载时了解文件系统布局

> 💡 **核心理解**：文件名只是便于人类识别的标签，系统真正依赖 inode 来管理文件

#### File & Directory Naming Guidelines

##### Don' t use Meta Characters

Slash - 斜杠

Back slash - 反斜杠

Under  -space/ -bar /-line

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ICCAD/DetailCh2-11.webp)

要把这些的中英文都会读

[http://en.wikipedia.org/wiki/Punctuation](http://en.wikipedia.org/wiki/Punctuation)

##### Unix is Case Sensitive(大小写敏感 large case small case)

#### Directory Commands

##### pwd

p w d分别代表什么意思

##### cd

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ICCAD/DetailCh2-12.webp)

##### mkdir

`mkdir directory-list`

##### rmdir

`rmdir directory-list`

##### tree

Tree 命令

##### ls    – List Contents of Directory

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ICCAD/DetailCh2-13.webp)

###### 文件域

field

##### alias ls = ls --color=auto

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ICCAD/DetailCh2-14.webp)

**####** **Permissions**

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ICCAD/DetailCh2-15.webp)

`ls -al` 命令输出的开头10个字符，是文件类型和权限的描述。**第一个字符**代表**文件类型**：`d` 表示这是一个目录（文件夹），`-` 表示这是一个普通文件，而 `l` 则表示一个符号链接（快捷方式）。

**接下来的9个字符**代表**访问权限**，它们被分为三组。第一组（第2-4位）是文件**所有者(user)**的权限，第二组（第5-7位）是**所属组(group)**的权限，第三组（第8-10位）是**其他人(others)**的权限。在每一组中，`r` 代表“读”权限，`w` 代表“写”权限，`x` 代表“执行”权限，而 `-` 则表示没有该项权限。

文件属性存储在inode里面

`<权限> <属性>`

##### File Maintenance Commands  ｜ 文件维护命令

1. `chmod`:  change the file or directory access permissions (mode)
2. `umask`: get or set the file mode creation mask **(built-in in bash like alias)**
3. `chgrp`:change the group of the file
4. `chown`: change the owner of a file

> 哪个先哪个后？（智云）

###### chmod

###### method1 | 用法1

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ICCAD/DetailCh2-16.webp)

###### method2 ｜ 用法2

permission 还可以使用数值来代表

直接使用r + w + x的数值来代表权限

> octal. 月份名字（？回看智云）

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ICCAD/DetailCh2-17.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ICCAD/DetailCh2-18.webp)

###### umask

在 Unix 和 Linux 系统中，`umask` 是一个非常重要的安全设置，它像一个“默认权限过滤器”，用来管理你新创建文件和目录的权限。它的核心作用不是“赋予”权限，而是“**拿掉**”权限。当你设置了一个 `umask` 值（比如 `022`），系统就会在你每次创建新文件时，自动从程序请求的“理想权限”（通常是 `666` 或 `777`）中，减去 `umask` 指定的权限，确保你的文件不会一开始就过度开放。

举个例子，如图所示，如果你的 `umask` 设置为 `022`，这个 `0` 对应所有者（user），第一个 `2` 对应所属组（group），第二个 `2` 对应其他人（others）。数字 `2` 代表“**写权限（w）**”。这意味着，当一个程序（如 `open()`）试图创建一个权限为 `666`（即 `rw-rw-rw-`）的文件时，系统会用 `umask 022` 来过滤：它会拿掉“所属组”的“写权限”和“其他人”的“写权限”。因此，新文件的最终权限就变成了 `644`（即 `rw-r--r--`），只有你自己能修改，其他人只能读取，大大提升了系统安全性。

##### Display Commands

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ICCAD/DetailCh2-19.webp)

##### File Manipulation Commands

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ICCAD/DetailCh2-20.webp)

-f forced 强制的

-i interactive 交互的

-R recursive 递归

##### ln and ulink

symbolic 符号链接 /快捷方式

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ICCAD/DetailCh2-21.webp)

##### find

`find directory-list [options] [actions][...]`

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ICCAD/DetailCh2-22.webp)

- 使用`\`来取消命令行对于`*`的特殊解释，转义通配符
- `-newer`:更`新`的文件
- `type`: 第一列是d的打出来

`find` 是一个在 Unix/Linux 系统中功能极其强大的命令，用于在指定目录中**查找文件**，并可以对找到的文件执行操作。

下面逐一解释这几个命令的含义：

1. `find . -name Net\*.jpeg -print`

- `find .`: 从**当前目录** (`.`) 开始查找。
- `-name Net\*.jpeg`: 查找文件名 (name) 匹配 `Net*.jpeg` 模式的文件。

  - `*` 是一个通配符，代表任意数量的字符。
  - `\` 是转义字符，防止 shell（命令行解释器）自己先去解析 `*`，确保 `*` 是传递给 `find` 命令的。更常见的写法是给模式加上引号，如 `find . -name "Net*.jpeg"`。
- `-print`: 将找到的文件或目录的完整路径名打印到屏幕上。
- **在当前目录及其所有子目录中，查找并列出所有以 "Net" 开头、以 ".jpeg" 结尾的文件。**

1. `find . -newer init.c -print`

- `find .`: 从当前目录开始查找。
- `-newer init.c`: 查找**修改时间比** `init.c` **文件更新 (newer) 的所有文件和目录**。
- `-print`: 打印结果。
- **查找并列出当前目录下所有比** `init.c` **这个文件还要新的文件。**

1. `find /usr/local -type d -print`

- `find /usr/local`: 从 `/usr/local` 目录开始查找。
- `-type d`: 查找类型 (type) 为 `d` 的条目，`d` 代表 **目录 (directory)**。
- `-print`: 打印结果。
- **查找并列出** `/usr/local` **目录下的所有子目录。**

1. `find . \( -user Bill -o -size +10000c \) -print -exec rm {} \;`

这是一个更复杂的组合命令：

- `find .`: 从当前目录开始查找。
- `\( ... \)`: 将括号内的条件作为一个**整体**。
- `-user Bill`: 查找所有者是用户 `Bill` 的文件。
- `-o`: 逻辑运算符 **"或" (OR)**。
- `-size +10000c`: 查找大小 (size) **大于** (`+`) 10000 **字节 (bytes)** (`c`) 的文件。
- `-print`: 打印符合条件的文件名。
- `-exec rm {} \;`: 对找到的每一个文件执行 (`exec`) `rm` (删除) 命令。

  - `{}` 是一个占位符，代表当前找到的文件名。
  - `\;` 表示 `-exec` 命令的结束。
- **在当前目录中，查找所有者是 "Bill" 或者大小超过 10000 字节的文件，先打印出它们的名字，然后将它们全部删除。**

1. `find ~bill ~denis -size +1000 -atime 30 -ok rm {} \;`

- `find ~bill ~denis`: 在用户 `bill` 和用户 `denis` 的**家目录** (`~`) 这两个位置开始查找。
- `-size +1000`: 查找大小**大于** 1000 个文件块 (blocks, 通常是512字节) 的文件。
- `-atime 30`: 查找最后访问时间 (access time) 恰好是 **30天前**的文件。（`+30` 是30天以前，`-30` 是30天以内）。
- `-ok rm {} \;`: 这是 `-exec` 的**安全版本**。它会对每个找到的文件，在执行 `rm` 命令**之前**，先**询问你是否同意** (例如会提示 `< rm ... '文件名' > ?`），只有你输入 `y` 并回车后，才会执行删除操作。
- **在 "bill" 和 "denis" 的家目录中，查找大小超过1000个块并且最后访问时间正好是30天前的那些文件，然后逐个询问你是否要删除它们。**

##### compression

在 Unix/Linux 系统中用于**文件压缩**和**解压缩**的几组常用命令，它们可以帮你减小文件大小，方便存储和传输。

- `compress / uncompress`：这是一组比较**古老**的工具，它会生成 `.Z` 后缀的压缩文件。现在已经不太常用了。
- `gzip / gunzip`：这是目前**最常用、最标准**的压缩工具。`gzip filename` 会将文件压缩成 `filename.gz`。要解压时，你可以使用 `gunzip filename.gz`，或者使用 `gzip -d filename.gz`，两者效果完全一样。
- `bzip2 / bunzip2`：这是另一组**更现代**的工具，它通常能提供比 `gzip` 更高的压缩率（即压缩后文件更小），但可能花费时间稍长。它生成 `.bz2` 文件，并使用 `bunzip2` 来解压。

#### Utility - wc

display a count of lines, words and  characters in a file——**word count**

> `wc` 命令是 "word count" (字数统计) 的缩写，用来统计文件的行数、单词数和字节数。
> 
> - **-c**: **字节数 (count bytes)**
> - **-l**: **行数 (count lines)**
> - **-w**: **单词数 (count words)**
> - **不带选项：** `wc filename`
>   - 它会默认同时显示：`行数 单词数 字节数 文件名`
> - **带选项：** `wc -l filename`
>   - 它就**只**显示行数。

#### Utility - diff

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ICCAD/DetailCh2-23.webp)

`diff` 命令，这是一个在 Unix/Linux 中非常基础且强大的**文件比较工具**。它的核心功能是**逐行比较**两个文本文件（`file1` 和 `file2`），然后告诉你它们之间具体有哪些行**不同**（比如哪些行被添加、删除或修改了）。

这个命令在编程和工程领域特别有用，比如用来比较**不同版本的源代码**、配置文件或数据列表（如图中提到的 `netlist`，即网表），能让你快速定位修改过的地方。而 `tkdiff` 和 `windiff` 则是 `diff` 的**图形界面版本**，它们能更直观地（比如并排）显示两个文件的差异，比纯文本输出更容易阅读。

#### grep 命令

`grep` 是 Unix/Linux 中用于文本搜索的工具，在文件中搜索匹配的行并打印出来。

**名称来源**：Global search for Regular Expression and Print

##### 三种模式

###### 1. `grep` (标准模式)

使用基础正则表达式搜索

###### 2. `fgrep` (固定字符串)

只搜索精确字符串，不使用正则表达式，速度更快

###### 3. `egrep` (扩展模式)

使用扩展正则表达式，支持 `+`, `?`, `|` 等语法

- 等同于 `grep -E`

---

##### 使用示例

###### 搜索特定单词

grep static ./*.c

在当前目录所有 `.c` 文件中搜索包含 "static" 的行

###### 搜索以特定字符开头的行

grep ^# *.cpp

在所有 `.cpp` 文件中搜索以 `#` 开头的行

- `^` 表示行首

###### 管道与选项组合

man find | grep -ci perm

在 `find` 命令手册中统计 "perm" 出现次数（忽略大小写）

- `-c`: 只显示匹配行数
- `-i`: 忽略大小写

---

##### 常用选项

<table>
<thead>
  <tr>
    <th>
      选项
    </th>
    
    <th>
      说明
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      -i
    </td>
    
    <td>
      忽略大小写
    </td>
  </tr>
  
  <tr>
    <td>
      -c
    </td>
    
    <td>
      只显示匹配行数
    </td>
  </tr>
  
  <tr>
    <td>
      -v
    </td>
    
    <td>
      反向匹配
    </td>
  </tr>
  
  <tr>
    <td>
      -n
    </td>
    
    <td>
      显示行号
    </td>
  </tr>
  
  <tr>
    <td>
      -r
    </td>
    
    <td>
      递归搜索
    </td>
  </tr>
  
  <tr>
    <td>
      -E
    </td>
    
    <td>
      扩展正则（egrep）
    </td>
  </tr>
  
  <tr>
    <td>
      -F
    </td>
    
    <td>
      固定字符串（fgrep）
    </td>
  </tr>
</tbody>
</table>

Grep 和 Find 的区别？

Find只和文件名，文件属性有关；Grep则是和文件内容相关
