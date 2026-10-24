# Chapter 5：Administration

> 系统管理：详细版笔记

## System Administration

#### Administrator / Superuser ｜ 管理员 / 超级用户

- **su** – to become superuser
`su`**：切换为超级用户（root），获得系统最高权限。**
- You could also become another user by,
`su username` **– 切换成其他普通用户的身份。**
- **Be careful of every character you typed when in su mode!****在** `su` **模式下要非常小心你输入的每一个字符，因为任何误操作都可能影响整个系统。**
- Nice to use **sudo** to only execute one command a time
**推荐使用** `sudo` **来“只为一条命令暂时提权”，比长时间待在** `su` **下更安全。**
- **Daily tasks of the administrator**
管理员的日常工作包括：

  - Manage user logins
  **管理用户账户与登录权限**
  - Monitor system activity and security
  **监控系统运行状态与安全情况**
  - Administer file systems, devices, and network services
  **管理文件系统、硬件设备以及各种网络服务（如 HTTP、SSH 等）**

#### The Model Hard Disk Drive｜ Unix 硬盘/文件系统的模型

- **Divided into three major sections****整个磁盘在 Unix 文件系统中可以抽象成三大部分：**
  - **Superblock（超级块）**
    - 存放 **整个文件系统的元数据**：
    
      - 块大小、总块数、空闲块数
      - inode 总数、空闲 inode 数
      - 文件系统标识等
    - 没了它，系统就不知道这个分区里文件系统的结构，是“文件系统的身份证 + 目录表”。
  - **Inodes（inode 区）**
    - 每个 inode 对应一个文件或目录的“说明书”：
    
      - 文件类型、权限、所有者、大小、时间戳
      - 以及指向 **数据块的地址（指针）**
    - 注意：**文件名不在 inode 里**，文件名存放在目录的数据块中，目录条目“文件名 → inode 号”。
  - **Data blocks（数据块区）**
    - 真正用来放数据的一块块空间：
    
      - 普通文件的内容
      - 目录中“文件名 ↔ inode 号”的列表
    - 也是我们平时说“文件很大，占了很多磁盘空间”时占用的区域。
- **Look back to what we discussed in Chapter "File System"****这页是回顾前面“文件系统”章节：Unix 文件系统在磁盘上的逻辑结构 = Superblock + Inodes + Data Blocks。**

##### Superblock ｜ 超级块

1. Superblock 是什么？

  - Superblock
  文件系统中的一块特殊区域，用来保存 **整个文件系统的元数据**。
  - Most important part of the file system
  → 是文件系统中 **最重要的部分**，损坏了就可能导致整个分区都挂掉。
2. Superblock 里存什么信息？

- Tracking important file system information
→ 负责 **跟踪记录文件系统的重要信息**。
- Containing file system size, free space, etc.
→ 典型内容包括：

  - 文件系统总大小（总块数）
  - 空闲块数量、空闲 inode 数量
  - 块大小等参数

1. 内存中的 Superblock 缓存

- **Kept in memory to improve performance**
→ 为了加速访问，系统会把 superblock 的内容 **缓存到内存**，避免每次都读磁盘。
- **Copies in memory and on disk can/will be out of "sync" (synchronize)**
→ 这样一来，**内存里的副本** 和 **磁盘上的真实 superblock** 有时会 **不同步（out of sync）**，比如刚更新还没写回盘。

1. `sync` 命令的作用

- `sync` **command writes contents of memory to disk and updates the superblock**
→ `sync` 会把内存中尚未写入的修改 **强制刷到磁盘**，包括更新 superblock，
确保“内存版本”和“磁盘版本”保持一致。

##### Inode ｜ 索引节点

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ICCAD/DetailCh5-01.webp)

1. **每个文件/目录都有一个 inode**
  - All files and directories have an inode
  - inode 可以理解成“文件的身份证 + 目录索引”，文件名不在 inode 里，而在目录的数据块中。
2. **inode 里记录的重要信息**
  - It records important file information – file size, permissions, data addresses, etc.
  - 典型字段：
  
    - 文件类型（普通文件/目录/符号链接等）
    - 访问权限（rwx）
    - 所有者 UID / 所属组 GID
    - 文件大小、时间戳（创建/修改/访问时间）
    - 指向数据块的地址（data block addresses）
  - 注意：真正的文件内容在“数据块区”，inode 只保存“去哪里找这些数据块”。
3. **直接块 + 间接块：支持大文件**
  - Each inode has data block addresses for indirect indexing, and that is enough for handling huge space
  - 结构大致是：
  
    - 若干个 **direct pointers（直接指针）** → 直接指向数据块
    - 再加上 **single / double / triple indirect blocks（一级/二级/三级间接块）**
      - 间接块里存的不是数据，而是“更多数据块地址”
  - 这样一层一层展开，就能让一个 inode 管理非常大的文件空间（上图就是这种“指针树”示意）。

##### Data Block | 数据块

1. Where the actual data is stored

  - 数据块（Data Blocks）就是**真正文件内容存放的地方**：文本、图片、可执行文件的字节都在这里，而不是在 inode 里。
2. Possibly 1/2, 1, 2, 4, 8K bytes long for each fragment block

  - 每个数据块的大小一般是若干 KB，比如 **0.5K、1K、2K、4K、8K** 等（具体取决于文件系统格式和创建参数）。
  - 磁盘会被划分成一块一块的固定大小的 block，文件占用磁盘时是按 block 来分配的。
3. Accessed by referencing an inode

  - 访问数据块是通过 **inode 中保存的“数据块地址”** 来完成的：
  
    - 先根据文件名在目录里找到 inode 号
    - 再从 inode 里取出数据块指针 → 读对应的数据块
4. Inode (filename & location data) + indirect data blocks + storage blocks => a file

  - 一个完整的文件，可以理解为：
  
    - **inode（记录文件元数据 + 数据块位置）**
    - **（可能存在的）间接索引块 indirect data blocks**
    - **真正存内容的 data blocks（storage blocks）**
  - 三者组合起来，才构成我们看到的“一个文件”。

<mark>

使用df来查看C盘容量 放在superblock里面——盘的信息

</mark>



<mark>

那么C盘中某处的容量 使用du来查看

</mark>



##### Cached Hard Drive I/O ｜ 硬盘缓存式输入输出

1. Differences in performance ⇒ Cache

  - CPU / 内存的速度远远快于磁盘，所以操作系统会在**内存里做缓存（cache）**，减少真正访问硬盘的次数。
2. Changes held in RAM

  - 对文件系统的修改（数据块、inode、superblock 等）**先保存在内存缓存中**，并不会立刻写回磁盘。
3. Writes to disk happen in whole block increments

  - 写盘是以 **“整块（block）”为单位** 进行的，而不是一字节一字节写；系统会把修改凑成块，再一次性写入。
4. Power failure, improper shutdown

  - 如果发生断电或不正常关机，内存缓存还没来得及写回磁盘，就会出问题：
  
    - Superblock in memory out of sync with disk version
    → 内存中的 superblock 与磁盘上的版本**不同步**。
    - Data loss, corrupted files and inodes
    → 可能导致**数据丢失、文件损坏、inode 受损**，启动时就需要 fsck 之类的工具检查修复。

##### Repairing File Systems ｜ 文件系统修复

1. 命令格式
2. fsck <span>

-y / -a | -n

</span>

 FileSystem

  - `fsck`：**File System ChecK**，用于检查并修复文件系统
  - `FileSystem`：要检查的分区或设备（如 `/dev/sda1`）
3. 作用

  - Reports and repairs file systems
  
    - 先 **检查** 文件系统是否有错误，再根据需要尝试 **自动修复**。
4. 运行时机

  - Always performed at system startup (while file systems not mounted)
  
    - 系统启动时，在文件系统 **尚未挂载**（not mounted）或只读挂载时自动运行，避免一边用一边修。
5. 常用选项含义

  - `-y` / `-a`：Answer yes to all questions
  
    - 对检查过程中提出的“是否修复？”问题 **全部回答 yes**，自动修复。
  - `-n`：Answer no to all questions
  
    - 对所有修复问题 **全部回答 no**，只做检查、不改动磁盘（安全查看用）。
6. 类比（Windows 中的对应工具）

  - Similar to **scandisk / chkdsk** in Windows/DOS
  
    - 在 Windows/DOS 里的 `scandisk`、`chkdsk` 就是和 `fsck` 类似的磁盘检查/修复工具。

##### Displaying File System Information ｜ 查看文件系统信息

1. 基本命令：`df`
  - `df`：**displays number of free disk blocks and files**
  - 作用：显示各个文件系统（分区）的 **容量 / 已用 / 可用 / 挂载点**。
  - 常看的是最后一列 `Mounted on`，知道哪个分区挂在哪个目录下。
2. `df -k`（Linux / Solaris）

  - `-k`：以 **1K-blocks（1KB 为单位）** 显示容量，而不是默认的更大单位。
  - 重点列：
  
    - `1k-blocks` / `kbytes`：总大小
    - `Used` / `used`：已用
    - `Available` / `avail`：可用
    - `Use%` / `capacity`：使用百分比
  - Linux、Solaris 输出列名略有不同，但含义一样。
3. `df -i .`（Linux）

  - `-i`：显示 **inode 使用情况**（不是磁盘容量，而是“文件数量名额”）。
  - `.`：只查看“当前目录所在分区”的情况。
  - 重点列：
  
    - `Inodes`：该分区 inode 总数（最多能容纳多少文件/目录）
    - `IUsed` / `IFree` / `IUse%`：已用 / 空闲 inode 数及百分比

<mark>

特殊点：

</mark>

<mark>

**磁盘没满但 inode 用光**

</mark>

 <mark>

时，也会“无法再创建新文件”，

</mark>

<mark>

`df -i`

</mark>

 <mark>

就能看出来。

</mark>



##### Managing File Systems ｜ 文件系统管理

1. Minimum Configuration（最小分区配置）

  - `root`：根文件系统 `/`，系统启动、命令、配置文件等都在这里，是必须有的分区。
  - `swap`：交换分区，用来**存放 RAM 溢出的内容**（内存不够时把一部分内容暂时放到磁盘）。
2. Adding systems（添加新的文件系统 / 硬盘分区的大致步骤）

  - Create a mount point (empty directory)
  → 先在现有目录树里创建一个 **空目录**，作为挂载点，比如 `/home`、`/data1`。
  - `mount` the file system
  → 使用 `mount` 命令，把新分区或设备“接到”这个目录上，之后访问这个目录就是访问那块分区。

##### Mounting on an Empty Directory ｜ 挂载到空目录

1. 基本语法
2. mount filesystem mountpoint

  - `filesystem`：设备或分区名，如 `/dev/sdc1`
  - `mountpoint`：挂载点目录，如 `/home`
3. 作用

  - Adds file system to the directory tree
  → 把一个独立的文件系统 **接入当前的目录树**，就像在树上再长出一个子树。
  - 示例：
  - mount /dev/sdc1 /home
  - 表示把 `/dev/sdc1` 这个分区挂到 `/home`，以后所有 `/home/...` 的访问都落在这块分区上。
4. 图示理解

  - 顶层是 `root`（`/`），下面有 `var`、`usr`、`etc`、`home`、`tmp`、`bin` 等目录。
  - 某些目录（如 `usr`、`home`）的下面，其实是**不同的磁盘分区 / 文件系统**，通过 `mount` 接上去。

##### Reporting Mounted Info ｜ 查看当前挂载情况

1. `mount`（无参数）

  - `mount` - without arguments, reports mounted systems on current workstation
  - 直接敲 `mount`，不加任何参数，会列出 **当前所有已挂载的文件系统**：
  
    - 哪个设备（`/dev/sda1` 等）
    - 挂载到哪个目录（`/`、`/home`、`/usr` 等）
    - 使用的文件系统类型（ext4、xfs…）
    - 读写属性（`rw`/`ro`）
2. 用途

  - 快速确认：
  
    - 某个目录是挂在哪个分区上的
    - U 盘 / 移动硬盘是否挂载成功
    - 当前系统一共挂了哪些特殊文件系统（如 `/proc`、`tmpfs` 等）

##### Un-mounting File System ｜ 卸载文件系统

1. 基本命令
2. umount {directory | device}

  - 可以写 **挂载点目录**（如 `/home`）
  - 也可以写 **设备名**（如 `/dev/sdb1`）
3. 作用

  - Remove a file system from the directory tree
  - 把一个文件系统**从当前目录树里摘掉**，卸载 U 盘、移动硬盘前必须先 `umount`。
4. 重要限制

  - Can not be performed on a "busy" file system
  - 如果文件系统正在被使用（busy），就**无法卸载**，常见原因：
  
    - 有人在该目录下 `cd` 着
    - 有进程正在读写该分区的文件
  - 解决思路：退出相关目录、关闭占用的程序，再 `umount`。

##### Reporting Disk Usage ｜ 查看磁盘占用（du）

1. 命令格式（记住大概就行）
2. du <span>

options

</span>

 <span>

file ...

</span>


  - `du` = **disk usage**：按目录 / 文件统计磁盘占用，而不是看整块分区（那是 `df` 做的事）。
3. 常见用法

  1. `du /home`
    - 递归统计 `/home` 下所有目录和文件的大小（每个子目录都会列出）。
  2. `du -ks file_or_dir`
    - `-k`：以 KB 为单位
    - `-s`：只给**总和**，不展开子目录
    - 常用来看“这个目录一共占多大”：
    - du -ks /home   # /home 一共多少 KB
4. 和 `df` 的区别（易考点）

  - `df`：看的是 **分区级别** 的空间使用情况（整块磁盘还有多少）。
  - `du`：看的是 **目录 / 文件级别** 的大小（谁占得多）。
  - 一般定位“磁盘爆了是谁干的”：先 `df` 看哪个分区满，再 `du` 在该分区里一路往下查。

##### File System Backup (tar) ｜ 使用 tar 做备份

1. 基本语法
2. tar <span>

options

</span>

 {directory | file} ...

  - `tar`：**tape archive**，把很多文件打包成一个归档文件（可选压缩）。
3. 核心选项（记几个组合就够了）

  - `-c`：create，创建新归档
  - `-t`：table of contents，列出归档里有哪些文件
  - `-x`：extract，从归档解出文件
  - `-f file`：指定归档文件名（**几乎必带**）
  - `-v`：verbose，显示详细文件列表
  - `-z` / `-j`：用 gzip / bzip2 压缩或解压
  - 注意：`-` 在很多系统里是可选的，所以 `cvf` 和 `-cvf` 效果一样。
4. 常用命令套路（背这几条就行）

  1. 打包目录（不压缩）：
  2. tar cvf bug.tar /usr/share/bug
  
    - `c`：创建
    - `v`：显示过程
    - `f bug.tar`：输出到 `bug.tar` 文件
  3. 查看包里内容：
  4. tar tvf bug.tar
  5. 打包并 gzip 压缩当前目录：
  6. tar czvf data.tgz .
  7. 解压到指定目录：
  8. tar xzvf data.tgz $HOME/new_home
5. 备份场景提示

  - Using tar for daily and weekly backup → 可用 tar 做**每天 / 每周备份**。
  - Incremental backup（增量备份）通常会结合 `find`、时间戳或其他工具，只打包最近修改过的文件。

##### Network File System

<mark>

NFS 是谁发明的？

</mark>



<mark>

**Bill Joy**

</mark>

<mark>

（比尔·乔伊，全名 William Nelson Joy）。

</mark>



- <mark>

在加州大学伯克利分校读研究生时创建了 BSD（Berkeley Software Distribution）

</mark>
- <mark>

是 vi 文本编辑器和 Unix 系统的 C shell (csh) 的创造者

</mark>
- <mark>

开发了 NFS（网络文件系统）

</mark>
- <mark>

1982年作为联合创始人和首席科学家参与创立了 Sun 公司

</mark>
- <mark>

设计了 Sparc 微处理器，并将之前领导开发的 BSD 继续发展成为 Solaris 操作系统

</mark>
- <mark>

是 Java 和 Jini 的主要作者之一

</mark>

<mark>

他在 BSD Unix、TCP/IP 协议实现、vi 编辑器、C shell、NFS 等多个领域都做出了开创性的贡献。

</mark>



###### Concept | 概念

- **Local File System（本地文件系统）**
  - 指安装在本机磁盘上的文件系统，只能在这台机器上直接访问。
- **Network File System, NFS（网络文件系统）**
  - 通过网络把**远程主机的文件系统挂载到本机**，
  - 让远程目录“看起来就像”本地目录一样使用。
  ![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ICCAD/DetailCh5-02.webp)
  - 图中说明：
    - 上方虚线框是主机 **piano** 的本地目录树：
    
      - 根目录：`root`
      - 子目录：`project`, `usr`, `etc`, `home`, `tmp`, `bin` 等。
    - 下方蓝色条写着 **Network**，表示通过网络连接到另一台主机 **cello**。
    - 右下圆柱是主机 **cello** 上的目录 `/remotedir`。
    - 通过 NFS，把 `cello:/remotedir` 挂载到 piano 这台机器的 `/project` 目录：
    
      - 对 piano 来说，访问 `/project/...` 就是在访问 cello 上的 `/remotedir/...`。
      - 用户不必关心文件实际在远程主机上。

---

###### NFS Manipulating｜ NFS 的操作/管理

1. **挂载远程 NFS 文件系统（Mount remote NFS file systems）**

```sh
# mount -t nfs cello:/remotedir /project
```

- `mount`：挂载文件系统的命令。
- `-t nfs`：指定文件系统类型为 NFS。
- `cello:/remotedir`：

  - 远程主机名：`cello`
  - 远程被共享的目录：`/remotedir`
- `/project`：本机上的挂载点目录。
- 效果：

  - 在本机访问 `/project` 时，实际访问的是 `cello` 上的 `/remotedir`。

1. **导出本地文件系统供别人挂载（Export local file systems for mounting）**
2. （也就是在“服务器端”配置要共享出去的目录）

  - **在 Linux 中：**
  - ## cat /etc/exports
  
  
    - `/etc/exports` 文件中列出了本机要通过 NFS 导出的目录及权限等设置。
    - 例如会写类似 `/space  client1(rw)` 之类的配置。
  - **在 Solaris 中：**
  - ## cat /etc/dfs/dfstab
  
  
  share -F nfs /space
  share -F nfs -o rw -d "opt dirs" /opt
  
    - `/etc/dfs/dfstab`：列出需要共享的目录以及 `share` 命令。
    - `share -F nfs /space`：
    
      - `share`：声明要共享一个文件系统。
      - `-F nfs`：使用 NFS 类型。
      - `/space`：要共享的目录。
    - `share -F nfs -o rw -d "opt dirs" /opt`：
    
      - `-o rw`：以读写方式共享（客户端可以读写）。
      - `-d "opt dirs"`：共享描述信息（可选的说明文字）。
      - `/opt`：被共享的目录。

- NFS 让**远程目录**看起来像**本地目录**，通过网络透明访问。
- **客户端**：用 `mount -t nfs 服务器:/远程目录 本地挂载点` 来挂载。
- **服务器端**：

  - Linux 看 `/etc/exports`；
  - Solaris 看 `/etc/dfs/dfstab` 并使用 `share -F nfs` 配置要共享的目录。

##### Centralized Authentication over Network ｜基于网络的集中式认证

Large organizations need to manage thousands of user accounts and passwords in hierarchical departments, and allow networked computers (maybe different OS’s) to have a common interface regardless of where you log into.

- 大型组织有**成千上万的账号和密码**。
- 这些账号分布在**层级结构的部门**里。
- 需要让不同的联网计算机（**可能是不同操作系统**）

  - 使用**统一的登录接口与账号体系**，
  - 用户从哪台机器登录都一样。
- **目录服务（Directory Service）就像黄页电话本**，
- 需要查账号信息时，只要在目录里“查一查”即可。

---

###### 早期方案：NIS / NIS+

Using NIS and NIS+ from SUN, a lookup lets you have the same passwd, host names, group files (same uid and gid) and home directory on each of your machines.

- **NIS / NIS+** 是 SUN 提出的早期目录服务 / 认证系统。
- 通过查询 NIS 服务器，可以在多台机器上保持：

  - 相同的 **密码文件**（passwd）
  - 相同的 **主机名信息**（host names）
  - 相同的 **组信息文件**（group files：同样的 uid/gid）
  - 相同的 **用户主目录设置**（home directory）
- 效果：用户在任何一台机器登录，用的都是**同一个账号身份**。
- **翻译：**
使用 SUN 提供的 NIS 和 NIS+，通过目录查询，可以让每台机器都使用同一套密码、主机名、用户组信息（相同的 uid 与 gid）以及主目录。也就是说，用户在所有机器上看到的是同一个账号环境。

---

###### 现代主流方案：LDAP 与 Active Directory

LDAP (Lightweight Directory Access Protocol), MS Active Directory (= LDAP service + Windows domain applications) are more advanced and popular today (distributed C/S model).

- **LDAP**：

  - 全称 **Lightweight Directory Access Protocol**，轻量级目录访问协议。
  - 一种标准协议，用来**访问/管理目录服务中的账号、组、权限等信息**。
- **Microsoft Active Directory (AD)**：

  - 实质是 **基于 LDAP 的服务** + Windows 域相关应用。
  - 在 Windows 环境下非常常见，用于集中管理用户、计算机、策略等。
- 它们采用**分布式客户端/服务器（C/S）模型**，

  - 比 NIS 之类方案**更先进、更流行**。
- **翻译：**
目前更先进、也更常见的方案是 LDAP（轻量级目录访问协议）以及微软的 Active Directory。Active Directory 可以理解为“LDAP 服务 + Windows 域应用”的组合。它们采用分布式 C/S 模型，用于在网络中集中管理和认证大量用户账号。

<mark>

**集中认证 = 账号与密码集中存放在目录服务中（NIS/LDAP/AD），各台机器通过网络查询这个“黄页”，实现统一的登录与身份管理。**

</mark>



##### Printing Commands ｜ 打印相关命令

1. `lp/lpr [options] file`
  - **作用：**
    - 向打印机**提交打印任务**。
    - `file`：要打印的文件名。
    - `[options]`：可选参数，比如指定打印机、份数等。
  - `lp` / `lpr`：把文件丢到打印机队列里去打印。
2. `lpstat - print information about the status of the print service`
  - **作用：**
    - 查看**打印服务的状态信息**，例如：
    
      - 打印机是不是在线、
      - 当前队列中有哪些任务等。
  - **翻译：**
    - `lpstat`：输出打印服务状态信息。
3. `lpq - display the content of a print queue`
  - **作用：**
    - 显示**打印队列里的内容**：
    
      - 哪些任务在排队、
      - 每个任务的编号、提交者等。
  - **翻译：**
    - `lpq`：查看当前打印队列。
4. `lprm - remove print requests from the print queue`
  - **作用：**
    - 从打印队列中**移除打印任务**，一般根据任务号或用户名来删除。
  - **翻译：**
    - `lprm`：删除/取消排队中的打印请求。

<mark>

提交打印：

</mark>

<mark>

`lp / lpr`

</mark>

<mark>

查服务状态：

</mark>

<mark>

`lpstat`

</mark>

<mark>

看队列：

</mark>

<mark>

`lpq`

</mark>

<mark>

删任务：

</mark>

<mark>

`lprm`

</mark>



#### Configuring Network | 网络配置

##### `/etc` 下的配置文件

> Change setting files under /etc manually or by utilities

这些配置可以**手动改文本文件**，也可以用图形/命令行工具改。常见内容：

- **Network domain | 网络域 / 域名配置**
  - 网络域名，如 `cs.univ.edu`
  - 决定主机的“全名”（FQDN）
- **IP**
  - 主机的 IP 地址：`192.168.x.x` 之类。
- **Router | 路由器 / 网关设置**
  - 默认网关（default gateway），发往外网的包都从这里走。
- **Host name aliases | 主机名别名**
  - 主机名别名，通常写在 `/etc/hosts`。
  - 例如给一台机器起多个名字。
- **Net masks | 网络掩码 / 子网掩码**
  - 子网掩码，比如 `255.255.255.0`。
  - 决定“同一局域网”的 IP 范围。
- **DNS finding | DNS 查找配置（DNS 服务器设置）**
  - DNS 服务器地址与解析规则，常在 `/etc/resolv.conf`。
- **etc.**
  - 还有如：网卡、静态/动态路由、IPv6 等其他网络参数。

---

##### 网络相关服务

> Install services packages such as NFS, LDAP, Samba, etc. | 安装 NFS、LDAP、Samba 等服务软件包，用来提供各种网络服务。

- **NFS**：网络文件系统，共享目录。
- **LDAP**：目录服务，用于集中账号认证。
- **Samba**：在 Unix / Linux 与 Windows 之间共享文件/打印机。

---

##### 查资料 & 用图形工具

- **Find references on system administration book**
  - 去系统管理类书籍或官方文档里查详细说明。
- **Use GUI based administration tools**
  - 使用图形界面的管理工具（如 `nm-connection-editor`、控制面板等）来配置网络。

---

#### License Management（许可证管理）

1. 标识一台具体的机器

> 1. Identifying a specific machine

1. 软件授权通常需要**锁定到某台机器**，标识方式有：

  - **hostid | 主机 ID**
    - 主机 ID，系统生成的唯一标识。
    - 这个个人PC没有（？有的吧）
  - **MAC address of Ethernet card ｜ 以太网卡的 MAC 地址**
    - 网卡的 MAC 地址（物理地址），全球唯一。
    - 但是可以很容易作弊，提供的mac可以被修改
  - **Special hardware such as 'watchdog'**
    - 插在机器上的专用硬件加密狗（dongle），比如“watchdog”。
    - 没有这个硬件，软件就不能运行。
2. 授权方式

> 1. Node-lock and floating license pool
> 
>   - **Node-lock license ｜ 节点锁授权 / 单机授权**
>     - 许可证**锁在某一台机器**（比如根据 MAC 地址）。
>     - 只有那台机器能用这个软件。
>   - **Floating license pool ｜ 浮动许可池（多人共享的并发授权）**
>     - 许可证存在服务器上，是一个“池子”。
>     - 局域网内多台机器可以按需借用，只要**同时使用的数量不超过许可证数**。

1. License check-out / check-in | 借出/归还 许可证

  - **License check-out**
    - 客户端启动软件时，从许可证服务器**借出**一个 license。
  - **License check-in**
    - 退出软件时，把许可证**归还**给服务器，供别人继续使用。
2. FLEXlm

> 1. FLEXlm, the most popular license manager on Unix
> 
>   - **FLEXlm**（后来叫 FlexNet）
>   
>     - Unix / Linux 上最常见的**商业软件许可证管理器**。
>     - 负责：
>     
>       - 管理 license 文件，
>       - 监听客户端的 check-out / check-in，
>       - 控制并发数量等。

##### FLEXlm

###### 一、主要角色（概念梳理）

- **license.dat（许可证配置文件）**
  - 文本文件，包含以下信息：
  
    - `SERVER`：许可证服务器的主机名 / IP、hostid、端口。
    - `DAEMON`：各厂商 Vendor Daemon 的名称及路径。
    - `FEATURE`：各软件功能（feature）的授权信息：版本、数量、到期时间、加密串等。
- **lmgrd（License Manager Daemon）**
  - FLEXlm 的主控制进程。
  - 功能：读取 `license.dat`，启动并管理各个 Vendor Daemon，记录日志。
- **Vendor Daemon（厂商守护进程）**
  - 每个软件厂商对应一个 Vendor Daemon。
  - 功能：具体执行许可证的借出（check-out）、归还（check-in）、计数和状态维护。
- **lock file（锁文件）**
  - 由 Vendor Daemon 创建和维护。
  - 用途：记录当前已借出的许可证数量以及相关状态，防止并发冲突。
- **Application Program（应用程序）**
  - 需要许可证的客户端软件。
  - 通过网络与许可证服务器通信，完成许可证请求和释放。

###### 二、FLEXlm 启动流程（Starting-Up）

1. **lmgrd 读取配置文件**
  - 启动时，`lmgrd` 打开 `license.dat`，解析 `SERVER`、`DAEMON`、`FEATURE` 等条目，确定监听端口及需要启动的 Vendor Daemon 列表。
2. **lmgrd 启动各 Vendor Daemon**
  - 根据 `DAEMON` 条目，`lmgrd` 在同一台服务器上依次启动相应的 Vendor Daemon 进程。
3. **Vendor Daemon 创建锁文件**
  - 每个 Vendor Daemon 启动后创建自己的 `lock file`，用于记录许可证使用情况。
  - 至此，许可证服务器处于就绪状态，可以接收客户端请求。

###### 三、FLEXlm 工作流程（Working Flow）

##### 客户端定位许可证服务器

1. **应用查找 license.dat**
  - 应用程序根据环境变量（如 `LM_LICENSE_FILE=/etc/license.dat`）或默认路径，找到并读取本地的 `license.dat` 文件。
  - 从中获得服务器主机名和端口信息。
2. **应用连接 lmgrd**
  - 应用程序使用从 `SERVER` 条目中得到的地址和端口，与服务器上的 `lmgrd` 建立网络连接。
3. **lmgrd 返回 Vendor Daemon 连接信息**
  - `lmgrd` 根据应用请求的 Feature 所属厂商，向应用返回对应 Vendor Daemon 的地址和端口。

###### 许可证申请与授予

1. **应用向 Vendor Daemon 请求许可证**
  - 应用与 Vendor Daemon 建立连接，发送对某一 `FEATURE` 的许可证请求（含版本、用户信息等）。
2. **Vendor Daemon 授予许可证**
  - Vendor Daemon 检查：
  
    - 该 Feature 是否有效（未过期）。
    - 当前已借出数量是否小于配置的最大数量。
  - 若满足条件，则从许可证池中扣减一份，向应用返回“授权成功”。
3. **Vendor Daemon 记录日志**
  - Vendor Daemon 将本次借出操作的详细信息记录到日志系统（与 `lmgrd` 协同），并更新锁文件中的计数。

###### 运行期间的状态维护

1. **心跳（heartbeat）机制**
  - 在应用运行期间，应用与 Vendor Daemon 周期性交换心跳消息：
  
    - 若心跳正常，应用持续获得许可证使用权。
    - 若心跳失效（网络中断、服务器故障等），在超时时间后，应用可能被要求停止或进入受限模式。

###### 许可证归还流程

1. **应用归还许可证**
  - 用户关闭应用或主动释放功能时，应用向 Vendor Daemon 发送许可证归还（check-in）请求。
2. **Vendor Daemon 更新状态并记录**
  - Vendor Daemon 将该许可证归还到池中，更新锁文件中的计数，并记录相应日志条目。

##### 四、license.dat 示例说明（Using FLEXlm）

示例片段（简化）：

```text
SERVER my_serv.cam.ac.uk 80507de8 1700
DAEMON abcd /etc/abcd
DAEMON xyzd /usr/lib/xyzd /usr/lib/xyz.opt
# keys for vendor xyz
FEATURE app1 xyzd 1.00 1-jan-2015 20 1EF029003EA7B324C0F7 ""
FEATURE app2 xyzd 6.0  1-aug-2014 3  5B6F00438A213675DC06 "core"
# keys for vendor abc
FEATURE app3 abcd 5.01 01-jun-2015 3 23B1854A00357C7F21EA "" 806082f1
FEATURE app4 abcd 2.6  1-jan-2016 1 A36902DF6E334801FB05 "DEMO" 80507de8
```

- `SERVER my_serv.cam.ac.uk 80507de8 1700`
  - 服务器主机名：`my_serv.cam.ac.uk`
  - hostid：`80507de8`
  - 监听端口：`1700`
- `DAEMON abcd /etc/abcd`、`DAEMON xyzd ...`
  - 定义了两个 Vendor Daemon：`abcd` 和 `xyzd`，后面为可执行程序路径及可选配置文件。
- `FEATURE` 行（以 `FEATURE app1 xyzd ...` 为例）

  - `app1`：功能名（feature name）。
  - `xyzd`：所属 Vendor Daemon 名称。
  - `1.00`：版本号。
  - `1-jan-2015`：到期日期。
  - `20`：最大并发许可证数量。
  - 之后的长串十六进制为加密校验码，可选字段例如 `"core"`、`"DEMO"` 为说明或模式。

通过上述配置，FLEXlm 能够在服务器上统一管理不同厂商的软件许可证，实现集中授权与并发控制。

#### Installing ICCAD Software（ICCAD 软件安装）

1. 软件包特点

  - **ICCAD software packages usually are large and complicated, and with lots of legacies**
    - ICCAD 类的软件包通常体积较大、结构复杂，且包含大量历史遗留代码与脚本。
    - 含义：安装过程容易依赖旧版本库、旧脚本，因此更需要仔细阅读文档和环境要求。
2. 阅读安装文档

  - **Read the documents about installation**
    - 在实际安装前，应完整阅读随软件提供的安装说明（README、INSTALL、用户手册章节等）。
    - 目的：了解支持的平台、依赖的库版本、磁盘空间与权限要求等。
3. 理解安装脚本的工作方式

  - **Understand how the installing script works**
    - 安装过程往往由各种脚本驱动，需要理解其大致逻辑与调用方式。
    - 可能涉及的脚本与构建系统：
    
      - Shell：`bash`、`tcsh`
      - `perl` 脚本
      - `makefile`（GNU make 等）
      - `sbt` 等构建工具
    - 理解程度不必到逐行阅读，但应知道：
    
      - 脚本会写哪些目录
      - 使用哪些环境变量
      - 需要哪些外部命令或工具
4. 准备所需的运行环境

  - **Prepare required environment**
    - 主要包括以下几类：
    1. **Needed third-party software and libraries**
      - 必要的第三方软件与库，例如编译器、仿真器、特定版本的 C/C++/Python 库等。
      - 需要根据文档提前安装并配置路径。
    2. **Environment variables**
      - 配置环境变量，如 `PATH`、`LD_LIBRARY_PATH`、`PYTHONPATH`、`LM_LICENSE_FILE` 等。
      - 这些变量决定可执行文件与库文件的查找位置。
    3. **License manager, etc.**
      - 配置许可证管理器（如 FLEXlm/ FlexNet）。
      - 包括设置 `license.dat` 路径、服务器地址等。

---

#### Open Source EDA Tools and Demos（开源 EDA 工具与示例）

> A few tools for your trial and error
> 适合作为练习对象的开源 EDA 工具

1. **KLayout**
  - 官网：[https://klayout.de/](https://klayout.de/)
  - 主要用途：版图查看与编辑（GDSII、OASIS 等格式：`.gds`, `.oas`）。
  - 典型场景：
  
    - 查看工艺版图
    - 做简单的版图修改与检查
2. **Ngspice**
  - 官网：[https://ngspice.sourceforge.io/](https://ngspice.sourceforge.io/)
  - 主要用途：电路级 SPICE 仿真。
  - 支持的输入文件扩展名：`.cir`, `.net`, `.spi` 等。
  - 可用于模拟电路、混合信号电路的行为仿真。
3. **OpenROAD flow**
  - 项目主页：[https://theopenroadproject.org/](https://theopenroadproject.org/)
  - 教程与流程文档：
  [https://openroad.readthedocs.io/en/latest/tutorials/FlowTutorial.html](https://openroad.readthedocs.io/en/latest/tutorials/FlowTutorial.html)
  - 主要用途：从 RTL 到布局布线的数字 IC 设计全流程（物理综合、布局、布线等）。
  - 相关文件类型示例：`.tcl`, `.v`, `.sdc`, `.odb`, `.lef`, `.lib`, `.def`, `.spef`, `.gds` 等。

- **A Chisel RISC-V demo from graduate course homework**
  - 示例仓库：[https://github.com/stuzs/RCore](https://github.com/stuzs/RCore)
  - 主要特点：
  
    - 使用 **Chisel**（基于 Scala 的硬件描述语言）实现 RISC-V 处理器。
    - 仓库中包含多类文件：`.scala`, `.v`, `.s`, `.vcd` 等，覆盖从高层描述、生成 Verilog，到仿真波形的完整流程。
  - 适合作为：
  
    - 研究生课程作业参考
    - 学习 RISC-V 软硬件协同设计与验证的示例工程。

1. **商业 ICCAD 软件安装：**
  - 软件包大而复杂 → 必须先读安装文档。
  - 搞清安装脚本（shell / perl / makefile / sbt 等）做了什么。
  - 提前准备好依赖软件、环境变量和许可证管理器。
2. **学习路径建议：**
  - 先从开源 EDA 工具（KLayout、Ngspice、OpenROAD）入手，练习安装和基本使用。
  - 通过完整示例工程（如 RCore Chisel RISC-V）体验从设计到仿真的全流程。
