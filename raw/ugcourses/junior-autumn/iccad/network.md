# Network

> 计算机网络基础

## Unix Network

### Server/Client Based Architecture

- <mark>

A server is the one who provides requested services

</mark>


  - <mark>
  
  Server（服务器）：
  
  </mark>
  
  <mark>
  
  **提供服务**
  
  </mark>
  
  <mark>
  
  的一方（网页服务器、文件服务器、邮件服务器）
  
  </mark>
- <mark>

Clients are the ones who request services

</mark>


  - <mark>
  
  Client（客户端）：
  
  </mark>
  
  <mark>
  
  **发起请求**
  
  </mark>
  
  <mark>
  
  的一方（浏览器、手机 App、你的电脑）
  
  </mark>

### Daemon

<mark>

daemon 就是后台常驻服务程序（Linux/Unix 里一般以 d 结尾）：

</mark>



- 它一直在后台跑，监听某个端口/资源
- 一旦有客户端请求，它就处理（或派生工作进程处理）
- 常见的一些例子
- `sshd`：监听 22 端口，处理 SSH 登录
- `httpd` / `nginx`：监听 80/443，处理网页请求
- `cron`：定时执行任务
- 协议是一种规范，daemon 会遵守协议

  - 比如 `sshd` 必须遵守 SSH 协议
- 每个人有很多 daemon

### The OSI Reference Model

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ICCAD/Network-01.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ICCAD/Network-02.webp)

**Layer 1: Physical layer** 物理层

- 物理层负责**在设备与物理传输介质之间传输和接收原始数据**，将信号转换为 0 和 1
- 物理链接可以是光缆、电缆、双绞线、无线电波，中间传的可以是声光电等信号
- 物理层的连接器（connector）有：

  - Repeater（中继器），接收信号并重新传输（比如放大信号，拓展传输）信号衰减了就放大，延长距离
  - Hub（集线器），属于纯硬件网络底层设备，它把所有节点集中在以它为中心的节点上，进行**集中收发**。发送数据时采用广播方式发送，所有人都会收到。
- 包含的协议：

  - USB（Universal Serial Bus）通用串行总线，是一个外部总线标准，用于规范电脑与外部设备的连接和通讯。接口可连接多种外设，如鼠标和键盘等

**Layer 2: Data link layer** 链路层

- 链路层对 0、1 底层信号进行分组和处理，后来形成的分组统一协议（或者说标准），就是以太网协议 Ethernet
- 链路层负责在节点和节点之间传输数据
- 链路层与以太网相关，有 MAC 地址的概念
- 以太网可以简单理解为局域网，所以链路层就是负责局域网内的通信
- 链路层的连接器有：

  - **Switch（交换机）**：可以为接入交换机的任意两个网络节点提供独享的电信号通路。最常见的交换机是以太网交换机。
  - **Bridge（网桥）**：根据物理地址过滤和转发数据包的连接设备，类似于聪明的中继器。
- 包括的协议：

  - **PPP（Point to Point Protocol）**：点对点协议。其为点对点连接上传输多协议数据包提供了一个标准方法。
  - **ARP（Address Resolution Protocol）**：地址解析协议。在**知道对方 IP 的前提下，ARP 协议可以获取对方的 MAC 地址**。
  - **CAN（Controller Area Network）**：控制局域网，是德国 BOSCH（博世）公司研发的一种串行通讯协议总线，它可以使用双绞线来传输信号，也是世界上应用最广泛的现场总线之一。
  - **MAC（Media Access Control）**：介质访问控制地址，或称物理地址，也叫硬件地址，用来定义网络设备的位置。

**Layer 3: Network layer** 网络层

- 网络层负责局域网和局域网之间的通信，进行跨网络数据传输。
- 它提供了将数据包从一个节点传输到连接在网络中不同网络的功能和方法。
- 网络本质上就是一种可以连接许多节点的媒介，每个节点都有一个地址。IP 地址用于标识哪个局域网，MAC 地址用于标识设备在局域网中的位置。
- 网络层的连接器有：

  - **Router（路由器）**：控制和协调网络之间的流量。
- 包括的协议：

  - <mark>
  
  **IP（Internet Protocol）**
  
  </mark>
  
  ：网络互联协议，是 TCP/IP 体系（包含了不同层的很多协议，只是 TCP 和 IP 最具代表性）中的网络层协议。IP 规定网络上所有的设备都必须有一个独一无二的 IP 地址。
  - **IPsec（Internet Protocol Security）**：互联网安全协议，是一个协议包，通过对 IP 协议的分组进行加密和认证来保护 IP 协议的网络传输协议簇（一些相互关联的协议集合）。
  - **IPX（Internetwork Packet Exchange Protocol）**：互联网分组交换协议，提供分组寻址和选择路由的功能，保证可靠到达。

**Layer 4: Transport layer** 传输层

- 网络层的 IP 帮我们划分子网，以太网层的 MAC 帮我们找到主机，但大家使用的都是应用程序。
- 我们通过 IP 和 MAC 找到了一台特定的主机，如何标识这台主机上的应用程序？答案就是端口，端口即应用程序与网卡（网络适配器）关联的编号。
- 传输层即建立到端口的通信，负责将一个应用程序的数据跨网络传输到另一个应用程序。
- 传输层的连接器有：

  - **Gateway（网关）**：又称网间连接器、协议转换器。网关要对收到的信息重新打包，以适应当前系统的需求，并进行协议翻译和重新传输。
- 包括的协议：

  - <mark>
  
  **TCP（Transmission Control Protocol）**
  
  </mark>
  
  ：传输控制协议。可靠传输，传输层基本靠此协议完成。
  - **UDP（User Datagram Protocol）**：用户数据报协议，也发送数据包，但不可靠。

**Layer 5(67): Application layer** 应用层

- 最接近用户的层，用户使用的是应用程序。应用层负责规定好数据的组织形式，有各种各样的协议。否则各种各样的应用和功能，乱起八糟的没法处理。
- 合并了 **Session Layer（5）** 和 **Presentation Layer（6）**。会话层用于建立、管理、中止会话。会话层的主要功能是负责维护两个节点之间的传输联接，确保点到点传输不中断。
- 以及管理数据交换等功能。表示层为在应用过程中之间传送的信息提供表示方法的服务，包括加密、解密等。
- 包括的协议：

  - **NFS（Network File System）**：网络文件系统，是由 SUN 公司研制的 UNIX 表示层协议（Presentation Layer protocol），能使使用者访问网络上别处的文件就像在使用自己的计算机一样。
  - <mark>
  
  **HTTP（Hyper Text Transfer Protocol）**
  
  </mark>
  
  ：超文本传输协议，是用于从万维网（WWW: World Wide Web）服务器传输超文本到本地浏览器的传送协议。
  - <mark>
  
  **FTP（File Transfer Protocol）**
  
  </mark>
  
  ：文件传输协议，是用于在网络上进行文件传输的一套标准协议。
  - **SMTP（Simple Mail Transfer Protocol）**：简单邮件传输协议，建立在 FTP 上的一种邮件服务，主要提供系统间的邮件信息传递。
  - <mark>
  
  **DNS（Domain Name Server）**
  
  </mark>
  
  ：域名解析系统，作为将域名和 IP 地址相互映射的一个分布式数据库，能使人更方便地访问互联网，因为 IP 太难记了。
  - **Telnet**：远程终端协议，是 Internet 远程登录服务的标准协议和主要方式。它为用户提供了在本地计算机上完成远程主机工作的能力。
  - **DHCP（Dynamic Host Configuration Protocol）**：动态主机配置协议，该协议允许服务器向客户端动态分配 IP 地址和配置信息。

### Some Useful Technical Terms

- <mark>

**LAN(**

</mark>

<mark>
<u>

**Local**

</u>
</mark>

 <mark>

**Area Network)**

</mark>

 局域网，覆盖范围方圆几十米之内（比如家里、教室、公司一层楼/一栋楼）
- **WAN(**<u>

**Wide**

</u>

 **Area Network)** 广域网，是**连接不同局域网**的远程网，跨接很大物理范围
- **WLAN(**<u>

**Wireless**

</u>

 **Local Area Network)** 无线局域网，使用了无线通信技术
- **Wi-Fi** 中文名为移动热点，是一种基于 IEEE 802.11 标准的无线网络协议，它经常被用于附近设备用无线电波传输数据

  - Wi-Fi 是 WLAN 最常见的实现方式；WLAN 是一种网络形态。
- **Internet** 英特网/互联网，指网络与网络间所串联成的庞大网络，这些网络以一组通用的协议相连
- **Intranet** 内联网，同样使用因特网技术，但建立在企业或组织内部
- **Ethernet** 以太网，一种计算机局域网技术
- **TCP/IP(Transmission Control Protocol/Internet Protocol)** 传输控制协议/网际协议，指能够在多个不同网络间实现信息传输的协议簇。<u>

不只包括 TCP/IP，但两者最具代表性

</u>
- **Packet** 数据包，有一定格式
- **IPv6(Internet Protocol Version 6)** 互联网协议第 6 版，代替 IPv4 成为下一代协议，其地址数量号称可以为全世界的每一粒沙子铺上一个地址，地址长度 **128位**（地址几乎“用不完”）。
- **IPv4(Internet Protocol Version 4)** 互联网协议第 4 版，地址长度 **32位**（大约 43 亿个地址）
- **UDP(User Datagram Protocol)** 用户数据包协议，**不保证可靠**，但更快、更简单
- **NFS(Network File System)** 网络文件系统，是由 SUN 公司研制的 UNIX 表示层协议（Presentation Layer protocol），能使使用者访问网络上别处的文件就像在使用自己的计算机一样
- **URL(Uniform Resource Locator)** 统一资源定位器，用于定位互联网上的资源，URL 即为 HTTP 后面跟的网址
- **HTTP** 超文本传输协议（超文本意思为比一般文本多一点信息，比如可能有链接、图片等）；
- **HTML(HyperText Markup Language)** 超文本标示语言，HTML 允许格式化文本，添加图片，创建链接、输入表单、框架和表格等等，并可将之存为文本文件，浏览器即可读取和显示。但其不是编程语言
- **FTP(File Transfer Protocol)** 文件传输协议
- **SMTP(Simple** <u>

**Mail**

</u>

 **Transfer Protocol)** 简单邮件传输协议
- **IMAP(Internet Message Access Protocol)** 英特网消息访问协议
- **DNS(Domain Name Server)** 域名解析系统，作为将域名和 IP 地址相互映射的一个分布式数据库，能够使人更方便地访问互联网。因为 IP 太难记了
- **ISP(Internet Service Provider)** 互联网服务提供商
- **PPP(Point to Point Protocol)** 点对点协议，为点对点连接上传输数据包提供标准方法
- **PPPoE(Point-to-Point Protocol Over Ethernet)** 以太网上的点对点协议，点对点协议封装在以太网中形成
- **VPN(Virtual Private Network)** 虚拟专用网络。通过在公用网络上建立专用网络，进行加密通讯
- **Web(World Wide Web)** 即全球广域网，也称为万维网，它是一种基于超文本和 HTTP、全球性的分布式图形信息系统。是建立在 Internet 上的一种网络服务，为浏览者在 Internet 上查找和浏览信息提供了图形化的、易于访问的直观界面。可以说 WWW 是覆盖全球的客户机/服务器网络

### TCP/IP Addressing

- **Address Schema:** `xxx.xxx.xxx.xxx (0-255)`
  - 这个是IPv4的地址形式：xxx.xxx.xxx.xxx（例如 192.168.1.10）
  - 每个 xxx 叫一个 八位组（octet），因为它占 8 bit。
  - 8 bit 能表示的范围是：从 00000000 到 11111111，也就是十进制 0 到 255。
  - 4 个 octet = 32 bit，所以 IPv4 一共 32 位。
- **5 Classes of IP Addresses:** A / B / C / D / E，早期的 IPv4 地址“默认划分方法”

<table>
<thead>
  <tr>
    <th>
      类别
    </th>
    
    <th>
      开头范围（第一段）
    </th>
    
    <th>
      默认网络/主机划分
    </th>
    
    <th>
      常见用途
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      A
    </td>
    
    <td>
      1–126
    </td>
    
    <td>
      8 bit 网络 + 24 bit 主机
    </td>
    
    <td>
      超大型网络
    </td>
  </tr>
  
  <tr>
    <td>
      B
    </td>
    
    <td>
      128–191
    </td>
    
    <td>
      16 bit 网络 + 16 bit 主机
    </td>
    
    <td>
      大型网络
    </td>
  </tr>
  
  <tr>
    <td>
      C
    </td>
    
    <td>
      192–223
    </td>
    
    <td>
      24 bit 网络 + 8 bit 主机
    </td>
    
    <td>
      小型网络
    </td>
  </tr>
  
  <tr>
    <td>
      D
    </td>
    
    <td>
      224–239
    </td>
    
    <td>
      不是单播地址
    </td>
    
    <td>
      组播 multicast
    </td>
  </tr>
  
  <tr>
    <td>
      E
    </td>
    
    <td>
      240–255
    </td>
    
    <td>
      保留/实验
    </td>
    
    <td>
      很少用
    </td>
  </tr>
</tbody>
</table>

> 第一段为0.x.x.x 的含义表示本网络，不能作为ip
> 
> 第一段为127.x.x.x的含义是回环地址，也不能作为A类网络

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ICCAD/Network-03.webp)

- **The prefix** identifies a network, while **the suffix** is unique to a host on that network

  - 第一个 bit 为 0 是 A 类，以此类推

> - 把 IPv4 地址看成二进制，**最高位**（最左边的 bit）有规律：
> - **Class A**：以 `0` 开头
> - **Class B**：以 `10` 开头
> - **Class C**：以 `110` 开头
> - **Class D**：以 `1110` 开头
> - **Class E**：以 `1111` 开头

- 不同的 Sample 可找出对应的 Class

  - 比如 192 开头，则分解为 128+64+……，则为 **Class C**，因为是110开头
  - 比如 210 开头，则分解为 128+64+16+……，为 **Class C**，前三位还是110

### Questions

- **How many hosts can be in one class B network?**
查看 suffix 部分长度即可，为 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msup>
<mn>

2

</mn>

<mn>

16

</mn>
</msup>

<mo>

=

</mo>

<mn>

65536

</mn>
</mrow>

<annotation encoding="application/x-tex">

2^{16}=65536

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8141em;">



</span>

<span className="mord">
<span className="mord">

2

</span>

<span className="msupsub">
<span className="vlist-t">
<span className="vlist-r">
<span className="vlist" style="height:0.8141em;">
<span style="top:-3.063em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">

16

</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.6444em;">



</span>

<span className="mord">

65536

</span>
</span>
</span>
</span>

> Class B 默认是 **/16**：
> 
> - 总共 32 位
> - 网络部分 16 位
> - 主机部分 16 位
> 
> 但是全0和全1一般不能分给主机，所以一般是65536-2=65534个hosts

- **How many computers each with a unique IP address can work together on the IP network?**
大致可以说 2 乘以 32 个方，精确的话要去除 special 的地址

> 同样存在大量“不能给普通主机用”的地址：
> 
> - 私有地址段（10.0.0.0/8，192.168.0.0/16 等是内部用）
> - 保留地址、组播地址（D 类）、实验地址（E 类）
> - 网络地址/广播地址等
> - 还有很多被分配但未实际使用的情况

### TCP/IP Commands

- **ping host** 判断目的地是否有效，determine if destination is alive

  - `ping 10.10.0.21`
  - `ping vlsi.zju.edu.cn`
  - `ping www.wikipedia.org`
  - ping 有个小鬼在听，听到就会回答，该命令在 Application 层
- **domainname** #显示/设置域名

  - 默认显示当前域名
- **hostname** #显示/设置主机名

  - 默认当前主机
- **host + 域名**，显示指定域名的 IP

#### Showing/Setting IP Addresses of Computers

- **cat /etc/hosts** #查看 IP 地址和主机名

  - IP 地址和域名保存在 `/etc/hosts` 文件中
  - 如果有一台机器叫 **viola**，如果我想和远程的这台机器访问，则每次都输入 IP 地址就很麻烦，于是我们就可以把 IP 和机器名字存入 `/etc/hosts` 文件中
  - 然后我 `ping viola`，那么机器就知道会去查这个表，由此方便的进行联络和访问IP地址

#### Useful Remote Connection Utilities

- **ftp options host** #使用文件传输协议传输文件

  - `ftp [host]`（这会直接连接并登录服务器）
  - `ftp` #进入 FTP 模式
  
    - `open host/close` #登录/登出 FTP 服务器```bash
    ftp>open ftp.gnu.org
    Name: anonymous
    ftp> close
    221 Goodbye.
    ```
    - `ascii/binary` #设定传输方式，选择文本或二进制传输```bash
    ftp> binary
    200 Switching to Binary mode.
    ftp> ascii
    200 Switching to ASCII mode.
    ftp>
    ```

> - **ascii（文本模式）**：用于纯文本文件（.txt/.c/.py 等）
> 
>   - 它可能会处理换行符差异（Windows `CRLF` vs Unix `LF`）
> - **binary（二进制模式）**：用于图片、压缩包、可执行文件等
> 
>   - **原样传输**，不会改内容

- `cd/lcd` #进入指定目录，`cd` 为改变远程目录（右），`lcd` 为 local（左）
  - <mark>
  
  注意这里只能使用
  
  </mark>
  
  <mark>
  
  `lcd`
  
  </mark>
  
  <mark>
  
  , 部分系统不支持使用
  
  </mark>
  
  <mark>
  
  `!cd`
  
  </mark>
- `pwd` #显示当前**远程的目录**
- `ls/!ls` #列出文件`ls`为远程的文件，`!ls`为local的文件
- `get/mget` #获得文件/批量获得文件
  - `mget + 文件名列表`，支持通配符，如 `*.zip````bash
ftp> get README README.txt
ftp> mget *.zip
```
- `put/mput` #上传文件/批量上传文件
  - `mput + 文件名列表`，支持通配符，如 `*.c````bash
ftp> mget *.zip
ftp> mput *.c
```
- `verbose` #显示更详细的传输过程
- `bye/quit` #中断连接（与 `close` 不同，这会彻底退出 ftp，`close`会断开连接，但仍在ftp里）
- `!` #退回到 shell```shell
ftp> !
$ ls
$ pwd
$ exit   # 返回 ftp
```
- **telnet** <u>

**host**

</u>

 #使用远程登录协议与主机通信
  - 用法：`telnet ip port`，如：`telnet 114.80.67.193 8080`
- **rlogin/rsh** #在另一台机器上远程登录/shell 执行
  - `rlogin + 远程主机`，如：`rlogin 192.168.1.88`
  - `rsh + 远程主机或 IP 地址 + 执行指令`

### 软件许可证管理 (License Management)

#### 识别特定机器 (Identifying a specific machine)

为了防止软件被非法复制，软件供应商需要将许可证与特定的硬件“绑定”。常见的方法包括：

- <mark>

**hostid**

</mark>

：系统生成的唯一标识符。在 Unix/Linux 系统中，这是一个基于硬件生成的 ID。
- <mark>

**MAC address of Ethernet card**

</mark>

：网卡的物理地址。由于全球唯一，它是最常用的绑定手段之一。
- <mark>

**Special hardware such as 'watchdog'**

</mark>

<mark>

：

</mark>

特殊的硬件加密狗（Dongle）。这是一种插在 USB 或并口上的小硬件，只有检测到它存在时，软件才能运行。

---

#### <mark>授权模式 (Node-lock and floating license pool)</mark>

这是两种最主流的授权方式：

- <mark>

**Node-lock**

</mark>

**（节点锁定）**：许可证绑定到特定的某一台电脑上。只有这台电脑能用，不能分给别人。
- <mark>

**Floating license pool**

</mark>

**（浮动许可池）**：许可证存在服务器上。比如公司买了 10 个授权，全公司 50 个人都可以装软件，但**同一时间**只能有 10 个人在线使用。这对于大型企业来说更节省成本。

---

#### 许可的借出与归还 (License check-out and check-in)

这是浮动许可<mark>

**Floating license pool**

</mark>

的具体运行机制：

- **Check-out（借出）**：当你打开软件时，它会向服务器申请一个授权。如果池子里还有剩余，你就“借”走了一个。
- **Check-in（归还）**：当你关闭软件时，授权会自动释放并“还”给服务器，供下一个同事使用。

---

#### <mark>FLEXlm</mark>

- **地位**：这是 Unix/Linux 环境下最著名、市场占有率最高的许可证管理软件（现在通常叫 FlexNet）。
- **用途**：很多昂贵的工程软件（如 CAD、EDA 芯片设计工具、仿真软件）都使用 FLEXlm 来管理全球范围内的授权分配。
