# System Administration

> 系统管理基础

## System Administration

### Administrator/Superuser

- `su` #成为超级用户

  - `su username` #成为指定用户
- `sudo` #以超级用户的身份**执行一行命令**

### The Model Hard Disk Drive

- **Superblock**: Containing **file system** size, free space, etc.

  - 是文件系统最重要的部分，存储了**文件系统（file system）信息**
  - 包括 inode/block 的总量、使用量、剩余量等
- **Inodes**: records important file information - file size, permissions, data addresses, etc

  - 每一个文件和目录都有对应的 Inode（每一个目录不仅有自己的 Inode，也一定有对应的 Data Block）
  - 里面存储了文件大小、允许级别、数据地址等，即 `ls -l` 的内容
  - Inode 指向一个数据块，即 block
- **block**
  - 实际记录文件内容，若文件太大，则会占用多个 block，哪怕文件很小，也会至少占用一个block

#### **ls -l**  **vs** **cat**

<table>
<thead>
  <tr>
    <th>
      操作
    </th>
    
    <th>
      命令
    </th>
    
    <th>
      底层动作
    </th>
    
    <th>
      读取了什么？
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      查看属性
    </td>
    
    <td>
      ls -l filename
    </td>
    
    <td>
      1. 读取当前目录的block数据块，找到 filename 对应的 Inode 号码。<br />
      
      2. 读取该 Inode，获取文件大小、权限、时间等信息。
    </td>
    
    <td>
      只读取了 Inode<br />
      
      (没有触碰 file.txt的Data Blocks)
    </td>
  </tr>
  
  <tr>
    <td>
      查看内容
    </td>
    
    <td>
      cat filename
    </td>
    
    <td>
      1. 读取目录找到 Inode 号码。<br />
      
      2. 读取 Inode，找到数据块的地址指针。<br />
      
      3. 根据指针，去磁盘读取 Data Blocks 的内容并显示。
    </td>
    
    <td>
      读取了 Inode + Data Blocks
    </td>
  </tr>
</tbody>
</table>

### 为什么 C 盘和文件属性查看大小速度不同

- 本质和硬盘结构有关：C 盘（整个分区）有多大、剩多少空间，这些信息记录在 **superblock** 里；而一个目录下面的很多信息（例如子目录有多少、每个文件多大等）不会放在 superblock 里，文件信息都放在 **Inodes** 里面。
- 所以**查看“整个盘”的大小时，直接读 superblock 就能得到结果，速度快**；而**查看“文件/目录占用大小”需要逐个访问 inode、遍历目录项并统计，会更费时间**。

### Displaying File System Information

#### df（report file system disk space usage）

- `df`：显示<mark>

空间磁盘块和文件的数量

</mark>

<mark>

，是文件系统的整体占用

</mark>


  - 用法：`df [options] [directory]`
    - 若无 `dir`，默认当前目录
  - `-k`：以 **k**ilobyte 为统计单位（k 字节报告）
  - `-i`：显示 **i**nodes 信息

#### du（estimate file space usage）

- `du`：<mark>

指定目录或文件占用的磁盘空间

</mark>


  - `du [option] [directory]`
  - 若不加 `dir`，则默认当前文件夹
  - `-a, --all`：除目录外，还统计文件的大小（因为**默认只统计目录的大小**）
  - `-s`：仅显示统计（**s**ummarize），即只显示总的那个文件（display only a total for each argument）
  - `-d #`：目录最大深度
  
    - `0` 时等于 `-s`
    - `1` 只统计当前文件夹内的
    - `2` 还统计到子文件夹内的
    - `3` 会统计到子文件夹内的文件夹
  - `-k`：以 **k**ilobyte 为统计单位

> ![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ICCAD/SystemAdministration-01.webp)
> 
> 目录也会占用一个数据块

#### 二者的区别

- <mark>

`df`

</mark>

 <mark>

更快：读取的是

</mark>

 <mark>

**superblock**

</mark>

 <mark>

内容

</mark>
- <mark>

`du`

</mark>

 <mark>

慢：通过

</mark>

 <mark>

**inode**

</mark>

 <mark>

逐级进入指定目录的每一个子目录，从而统计并显示占用大小

</mark>

### Managing File Systems

- 将文件系统与目录树产生关联的操作为**挂载mount**
  - 挂载 = 把一个文件系统接入到 Linux 的目录树里，让你能通过某个目录去访问它
  - Linux 只有**一棵目录树**：从 `/` 开始一直往下。<mark>
  
  但硬盘/分区/U盘是独立的存储空间
  
  </mark>
  
  ，它们必须**挂到某个目录上**，才能读写。
- 分区（文件系统）是物理上的区分

  - 真实存在的存储设备或分区：
  
    - /dev/sda1、/dev/sdb2、U盘 /dev/sdc1 等
  - 里面有自己的 superblock/inode/block，也就是一个完整文件系统。
- 目录是逻辑上的区分

  - 比如：`/home`、`/mnt/usb`、`/data` 只是“路径名字”
  - 它本身不等于某块物理硬盘空间，除非你把东西挂上去。
- Linux 分区必须挂载到目录树中的某个具体的目录上才能进行读写操作
- **Adds file system to the directory tree**
  - `mount filesystem mountpoint`
  - 比如：`mount /dev/sdc1 /mnt/usb`是把 `/dev/sdc1` 这个文件系统接到 `/mnt/usb` 这个目录上
  - **挂载点 mountpoint 必须是一个目录**。挂载后，这个目录原本的内容会“被遮住”（卸载后又回来）
- **reports mounted systems on current workstation**
  - `mount`
  - 它会列出当前系统所有挂载点，例如：
  
    - `/dev/sda1 on / type ext4 ...`
    - `/dev/sdc1 on /mnt/usb type vfat ...`
- **Remove a file system from the directory tree**
  - `umount {directory | device}`

> - 两种都行：
> 
>   - `umount /mnt/usb`  （按目录卸载）
>   - `umount /dev/sdc1` （按设备卸载）

- `-v`：**v**erbose，verbose mode，输出更多过程信息
- `-f`：**f**orce，force an umount，强制卸载

### File System Backup（系统备份）

- `tar [options] {directory | file}...`：an archiving utility（打包工具）
- **tar = 打包**    **gzip/ compress = 压缩**，打包不一定会变小

常用选项：

- `-c`：创建新的备份文件（**c**reate a new archive），也就是打一个新的包
- `-t`：列出备份文件的内容（lis**t** the contents of an archive），打开包看看里面有什么，但是不拿出来
- `-x`：从备份文件中还原（e**x**tract），从包里面取出来
- `-v`：显示过程（**v**erbose），输出更多过程信息
- `-z`：通过 gzip 处理文件（g**z**ip compression），打完包之后通过gzip再压缩一遍
- `-Z`：通过 compress 处理文件（compress），打完包之后通过compress再压缩一遍，compress比较老也很少用
- `-f file`：指定备份文件名（specify archive filename），指定包叫什么名字

  - 没它 tar 不知道输出到哪个文件

示例：

- 打包指定目录到 bug.tar：

  - `tar -cvf bug.tar /usr/share/bug`
  - 将目录下的所有文件打包成 `bug.tar`，放在当前目录

注意：

- `tar` 只是**打包**，并不是压缩；压缩可以使用 `gzip` 等压缩工具，使用 `-z` 选项。
- 将当前目录打包并压缩为 data.tgz：

  - `tar -zcvf data.tgz .`
- 解压缩 data.tgz 到指定目录（后面目录下）：

  - `tar -zxvf data.tgz` `-C` `$HOME/new_home`
- 查看压缩包中的文件列表（使用 `-t` 选项）：

  - `tar -tvf bug.tar`11

### Network File System

- 网络文件系统，英文 <mark>

**Network File System (NFS)**

</mark>

，是由 **SUN** 公司研制的 UNIX 表示层协议（presentation layer protocol），能使用户访问网络上别处的文件就像在使用自己的计算机一样。
- **Mount remote NFS file systems**
  - `mount -t nfs cello:/remotedir /project`
  - `mount` 命令以 `nfs` 的形式来进行挂载，`cello`（冒号前）最终会被解释为 IP 地址
