# Chapter 4：Network

> 计算机网络：详细版笔记

## NetWork

### Introduction ｜ 引言

> Standard Distributed 的反义词

#### Development History ｜ 发展历程概览

<mark>

一个网络守护进程（daemon）或服务可以一直运行，并在特定的连接点或端口上等待请求，这些端口就是专门为它设置用来监听的。 ｜ A network daemon or service can run and always wait for requests on specific connection points or ports, for which they are set up to listen

</mark>



1. <mark>

**Client/Server（C/S）模式**

</mark>


  - <mark>
  
  结构：客户端（PC） ↔ 服务器
  
  </mark>
  - <mark>
  
  场景：多在局域网内使用
  
  </mark>
  - <mark>
  
  服务器特点：
  
  </mark>
  
  
    - <mark>
    
    跑守护进程（daemon），一直监听端口等待请求
    
    </mark>
    - <mark>
    
    一台服务器可提供多种服务：
    
    </mark>
    
    
      - <mark>
      
      Web 服务
      
      </mark>
      - <mark>
      
      邮件（POP3/SMTP/IMAP）
      
      </mark>
      - <mark>
      
      许可证管理
      
      </mark>
      - <mark>
      
      文件/打印服务
      
      </mark>
      - <mark>
      
      数据库、大数据等
      
      </mark>
2. **Internet 模式**
  - 在 C/S 基础上扩展到 **互联网**
  - 设备：PC、笔记本、手机、远程桌面、远程服务器等都能连入
  - 特点：
  
    - 不再局限于局域网
    - 通过统一的互联网协议（如 HTTP）访问远程服务器
    - 服务器可以在世界任何地方
3. **Cloud（云计算）模式**
  - 在 Internet 之上进一步抽象出“云”
  - 云内部：大量服务器 + 存储 + 网络，被虚拟化和自动管理
  - 用户看到的只是：
  
    - IaaS：租虚拟机、硬盘等基础设施
    - PaaS：应用运行平台
    - SaaS：直接使用在线软件（邮箱、网盘等）
  - 优点：不关心具体服务器数量和位置，只按需使用资源

> 蓝色虚线箭头表示：计算模式从 **传统 C/S → 基于互联网的 C/S → 云计算** 的演进过程。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ICCAD/DetailCh4-01.webp)

#### Some Useful Technical Terms（术语速记）

<table>
<thead>
  <tr>
    <th>
      简称
    </th>
    
    <th>
      中文名称
    </th>
    
    <th>
      英文全称/英文名称
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      LAN
    </td>
    
    <td>
      局域网
    </td>
    
    <td>
      Local Area Network
    </td>
  </tr>
  
  <tr>
    <td>
      WAN
    </td>
    
    <td>
      广域网
    </td>
    
    <td>
      Wide Area Network
    </td>
  </tr>
  
  <tr>
    <td>
      WLAN
    </td>
    
    <td>
      无线局域网
    </td>
    
    <td>
      Wireless Local Area Network
    </td>
  </tr>
  
  <tr>
    <td>
      Wi-Fi
    </td>
    
    <td>
      最常见的 WLAN 技术
    </td>
    
    <td>
      Wireless Fidelity
    </td>
  </tr>
  
  <tr>
    <td>
      Internet
    </td>
    
    <td>
      全球互联网
    </td>
    
    <td>
      Internet (或 Interconnected Network)
    </td>
  </tr>
  
  <tr>
    <td>
      Intranet
    </td>
    
    <td>
      单位内部专用网
    </td>
    
    <td>
      Intranet (或 Internal Network)
    </td>
  </tr>
  
  <tr>
    <td>
      Ethernet
    </td>
    
    <td>
      常见有线局域网技术
    </td>
    
    <td>
      Ethernet
    </td>
  </tr>
  
  <tr>
    <td>
      Packet
    </td>
    
    <td>
      数据包，网络传输的基本单位
    </td>
    
    <td>
      Packet
    </td>
  </tr>
  
  <tr>
    <td>
      TCP/IP
    </td>
    
    <td>
      互联网核心协议族
    </td>
    
    <td>
      Transmission Control Protocol/Internet Protocol
    </td>
  </tr>
  
  <tr>
    <td>
      IPv6
    </td>
    
    <td>
      新一代 IP 协议，地址更多
    </td>
    
    <td>
      Internet Protocol version 6
    </td>
  </tr>
  
  <tr>
    <td>
      DNS
    </td>
    
    <td>
      域名系统，把域名翻成 IP
    </td>
    
    <td>
      Domain Name System
    </td>
  </tr>
  
  <tr>
    <td>
      ISP
    </td>
    
    <td>
      网络服务提供商（电信、移动等）
    </td>
    
    <td>
      Internet Service Provider
    </td>
  </tr>
  
  <tr>
    <td>
      PPP
    </td>
    
    <td>
      点对点拨号协议，早期拨号上网用
    </td>
    
    <td>
      Point-to-Point Protocol
    </td>
  </tr>
  
  <tr>
    <td>
      PPPoE
    </td>
    
    <td>
      基于以太网的 PPP，宽带拨号、多用户常用
    </td>
    
    <td>
      Point-to-Point Protocol over Ethernet
    </td>
  </tr>
  
  <tr>
    <td>
      VPN
    </td>
    
    <td>
      虚拟专用网，加密“隧道”，远程安全访问内网
    </td>
    
    <td>
      Virtual Private Network
    </td>
  </tr>
</tbody>
</table>

<alert type="tip">

- **WiFi（无线局域网）：** 是一种**短距离**无线技术。它通常由一个**路由器**（接入点）发出信号，覆盖范围只有几十米（一个房间或一栋楼）。它的信号源头通常是物理网线（如光纤宽带）。
- **移动数据（蜂窝网络）：** 是一种**广域网**技术。它由移动运营商ISP（如移动、联通、电信）的**基站**（铁塔）发射信号。信号覆盖范围极广，可以跨越城市和荒野。

</alert>

### Network Layer Model

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ICCAD/DetailCh4-02.webp)

- 核心思想：**分层架构**，每层只管自己的职责。
- 发送端流程：

  1. 应用产生 **Message（消息）**
  2. 运输层把消息拆成多个 **Packets（数据包）**
  3. 数据包变成一串 **Bits（比特）**
  4. 物理层把比特编码成 **Signal（电/光/无线信号）** 发出去
- 接收端：按相反方向处理

  - 信号 → 比特 → 数据包 → 组合成完整消息
- 各层大致作用：

  - **TRANSPORT（运输层）**：端到端传输，可靠性（TCP/UDP）
  - **NETWORK（网络层）**：寻址、路由（IP）
  - **LINK（链路层）**：一跳内传输，帧的收发（以太网、WiFi）
  - **PHYSICAL（物理层）**：0/1 怎么变成真实信号在线路上传输

---

#### The OSI Reference Model

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ICCAD/DetailCh4-03.webp)

**网络通信被划分为 7 个抽象层，每层各司其职，层与层之间通过标准接口协作**。

OSI = Open System Interconnect，开放式系统互联参考模型

1. **Physical 物理层**
  - 传输对象：Bits（比特）
  - 作用：定义电压、线缆、插头、无线信号等“怎么看得见的物理传输”。
  - 例子：Ethernet PHY in IEEE 802.3  、802.11 a/b/g/n PHY（WiFi 物理层）、USB 等
2. **Data Link 数据链路层**
  - 传输对象：Frames（帧）
  - 作用：物理地址（MAC）、差错检测、点到点传输。
  - 例子：Ethernet 802.3 (LLC+MAC), PPP, WLAN, CAN …
3. **Network 网络层**
  - 传输对象：Packets（包）
  - 作用：IP 地址、路由选择，让数据在不同网络之间“找路”。
  - 例子：IPv4/IPv6, IPsec, IPX …
4. **Transport 运输层**
  - 传输对象：Segments（段）
  - 作用：端到端连接、可靠传输（如 TCP）、端口号。
  - 例子：TCP, UDP
5. **Session 会话层**
  - 作用：建立、管理、终止会话（对话），保持通信状态。
  - 例子：RPC, NetBIOS …
6. **Presentation 表示层**
  - 作用：数据格式转换、加解密、压缩（例如字符编码、JPEG、SSL 等）。
  - 例子：XDR, MIME, SSL …
7. **Application 应用层**
  - 作用：直接面向应用程序（NFS, HTTP, FTP, SMTP, DNS, Telnet, DHCP 等协议所在层）。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ICCAD/DetailCh4-04.webp)

#### Network Connectors｜ 网络连接设备

1. **Repeater 中继器**

- 作用：**物理信号放大器**
- 场景：线太长、信号衰减，用它把电/光信号再生、放大，延长传输距离。
- 工作层：物理层（只看电平，不看数据内容）。

1. **Hub 集线器**

- 原理：收到一个信号，**广播**到所有端口。
- 特点：

  - 所有设备共享同一带宽、同一冲突域。
  - 谁说话声音大、先占线，就先发；容易冲突。
- 现在基本被交换机（Switch）淘汰。

1. **Bridge / Switch 网桥 / 交换机**

- 作用：

  - 连接同一网络中的多台设备。
  - 监听数据帧，通过 **MAC 地址** 决定转发到哪个端口。
  - **减少冲突**  (Prevents collision)、提升效率（每个端口是独立冲突域）。
- 工作层：数据链路层（第 2 层）
- 备注：也有工作在第 3 层甚至更高的“多层交换机”。

1. **Router 路由器**

- 作用：在**不同网络之间**转发数据。
- 根据 **IP 地址** 和路由表决定下一跳。
- 典型场景：家里的路由器，把内网 192.168.x.x 连到运营商网络、互联网。
- 工作层：网络层（第 3 层）。

1. **Gateway 网关**

- 作用：**协议翻译 + 转发**
  - 比如：公司内部专用协议 ↔ 运营商/ISP 的协议。
  - 或者不同网络体系之间互通。
- 范围：概念更宽，可以涉及更高层协议的转换（应用层、表示层等），不只第 3 层。

> 小总结：从下到上，功能越来越“聪明”：
> Repeater（放大信号） → Hub（广播） → Switch/Bridge（按 MAC 分发） → Router（按 IP 路由） → Gateway（做协议转换和复杂转发）。

**要回去看微信发的小文章来理解网络层的原理！！！**

#### Common Protocols｜ 常见协议

##### Transport / Network ｜ 运输层 / 网络层

- **TCP/IP**
  - 全称：**Transmission Control Protocol / Internet Protocol**
  - IP：负责“找地址、找路”（给每台主机分配 IP 地址，负责路由转发）
  - TCP：负责“可靠传输”（三次握手、重传、顺序、流量控制等）
  - 作用：互联网中最核心的一套协议组合，几乎所有应用都基于它

##### Data Link |  数据链路层

- <mark>

**Ethernet（以太网）**

</mark>


  - 局域网里最常见的链路层协议（网线 + 交换机 就是以太网）
  - 使用 **CSMA-CD** 机制：
  
    - Carrier Sense：先“听一听”有没有别人“说话”
    - Multiple Access：很多设备共用一条信道
    - Collision Detect：如果发现冲突，就停止发送，随机等待后再发
  - **设备共用信道，不能两个人同时“说话”****（人少、信息密度低时好用）**
- <mark>

**Token Ring（令牌环，含 FDDI）**

</mark>

 <mark>

＊（PPT 中被灰掉，不重点讲）

</mark>


  - <mark>
  
  拿到“令牌”的设备才能发数据 → 轮流说话，避免冲突
  
  </mark>
- <mark>

**PPP（Point-to-Point Protocol）**

</mark>

<mark>

＊（PPT 中被灰掉，不重点讲）

</mark>


  - <mark>
  
  点对点链路协议（常用于拨号、串口、早期宽带接入）
  
  </mark>
  - <mark>
  
  特点：
  
  </mark>
  
  <mark>
  
  **两端一对一**
  
  </mark>
  
   <mark>
  
  传输，而不是一堆设备共用一根线
  
  </mark>

如果是不同局域网之间的沟通呢？

A局域网和B局域网之间通过**Gateway**来实现沟通

#### Simplified 4-Layers Model ｜ TCP/IP 简化四层模型

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ICCAD/DetailCh4-05.webp)

1. **链路层（Link & Physical，OSI 1+2 层）**
  - 职责：比特传输、成帧、本地链路通信
  - 典型协议：Ethernet、WiFi、PPP
  - 典型设备：网卡、交换机、集线器
2. **网际层（Internetwork，OSI 第 3 层）**
  - 职责：IP 编址、路由选择，让数据在不同网络间转发
  - 典型协议：IPv4、IPv6、ICMP、IPsec
  - 典型设备：路由器
3. **传输层（Transport，OSI 第 4 层）**
  - 职责：端到端通信、可靠性、端口号
  - 典型协议：TCP、UDP
4. **应用层（Application，OSI 5+6+7 层）**
  - 职责：直接为应用提供网络服务，数据表示、会话管理
  - 典型协议：HTTP、FTP、SMTP、DNS、SSH、Telnet 等

#### Packets Formatted for Layered  Communications ｜ 分层通信时的数据封装

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ICCAD/DetailCh4-06.webp)

### TCP/IP Address

#### IP Address

##### IPv4 地址基本概念

- **表示方式**：点分十进制，例如 `210.32.156.248`
- 一共 **32 bit** → 被写成 **4 个 0–255 的数字**
- **每个 IP 唯一标识一个主机/接口**

---

##### 五类 IP 地址

IP =  **前缀 prefix（网络号）** + **后缀 suffix（主机号）**

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ICCAD/DetailCh4-07.webp)

<table>
<thead>
  <tr>
    <th>
      类别
    </th>
    
    <th>
      前几位(bit)
    </th>
    
    <th>
      首字节范围
    </th>
    
    <th>
      用途
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      A
    </td>
    
    <td>
      0
    </td>
    
    <td>
      0–127
    </td>
    
    <td>
      大网络，前 8 bit 做网络号
    </td>
  </tr>
  
  <tr>
    <td>
      B
    </td>
    
    <td>
      10
    </td>
    
    <td>
      128–191
    </td>
    
    <td>
      中等网络，前 16 bit 做网络号
    </td>
  </tr>
  
  <tr>
    <td>
      C
    </td>
    
    <td>
      110
    </td>
    
    <td>
      192–223
    </td>
    
    <td>
      小网络，前 24 bit 做网络号
    </td>
  </tr>
  
  <tr>
    <td>
      D
    </td>
    
    <td>
      1110
    </td>
    
    <td>
      224–239
    </td>
    
    <td>
      组播地址（multicast）
    </td>
  </tr>
  
  <tr>
    <td>
      E
    </td>
    
    <td>
      1111
    </td>
    
    <td>
      240–255
    </td>
    
    <td>
      保留，将来使用
    </td>
  </tr>
</tbody>
</table>

> 主机真正用的主要是 **A/B/C 类**；D 组播，E 保留。

---

##### 示例地址

- `1.1.1.1` → Class A 公网地址
- `10.10.0.21` → Class A **私网地址**（10.0.0.0/8）
- `127.0.0.1` → **回环地址**（localhost，自己给自己通信）
- `192.168.0.255` → Class C 私网段 `192.168.0.0/24` 的 **广播地址**
- `210.32.156.248` → Class C 公网地址

---

##### 例题：

1. **一个 Class B 网络里最多有多少主机？**
  - Class B：前 16 bit 网络号，后 16 bit 主机号
  - 主机位：2¹⁶ = 65,536 个地址
  - 去掉全 0（网络地址）和全 1（广播地址）
  - **可用主机数 = 65,534 台**
2. **整个 IPv4 理论上可以有多少个不同 IP？**
  - IPv4 一共 32 bit
  - 可组合的地址数：2³² = **4,294,967,296** 个
  - 实际可用会少一些，因为有保留地址（私网、组播、特殊用途等）。
3. **sz小问：为什么192.168开头的IP这么多**

因为IPv4不够用了，将下面这些地址段设为私有IP，供局域网内使用（不能在公网上使用），由路由器包装至公网。挂梯子本质在改变公网IP，内网IP没变。

<table>
<thead>
  <tr>
    <th>
      IP 地址段 (范围)
    </th>
    
    <th>
      类别
    </th>
    
    <th>
      适用场景
    </th>
    
    <th>
      容纳设备数量
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      10.0.0.0 - 10.255.255.255
    </td>
    
    <td>
      Class A
    </td>
    
    <td>
      大型企业、运营商大内网（浙大）
    </td>
    
    <td>
      约 1600 万
    </td>
  </tr>
  
  <tr>
    <td>
      172.16.0.0 - 172.31.255.255
    </td>
    
    <td>
      Class B
    </td>
    
    <td>
      中型企业、学校、容器网络 (Docker)
    </td>
    
    <td>
      约 100 万
    </td>
  </tr>
  
  <tr>
    <td>
      192.168.0.0 - 192.168.255.255
    </td>
    
    <td>
      Class C
    </td>
    
    <td>
      家庭、小型办公室
    </td>
    
    <td>
      约 6.5 万
    </td>
  </tr>
</tbody>
</table>

#### TCP/IP Commands - ping

- **作用**：测试某个主机（host）在网络上是不是“活着”，网络是否连通。
- **基本格式**：
- ping host

  - `host` 可以是 **IP 地址** 或 **域名**。
- **示例**：

  - `ping 10.10.0.21`  → 测试局域网或某台机器是否可达
  - `ping vlsi.zju.edu.cn`  → 先通过 DNS 解析域名，再测试连通性
  - `ping www.wikipedia.org`  → 测试到维基百科网站的网络状况
- **工作原理**：

  - 发送 ICMP Echo Request（“回声请求”报文）
  - 对方若收到，会回复 ICMP Echo Reply（“回声应答”）
  - 根据是否有回复、往返时间 RTT，判断：
  
    - 目的是否可达
    - 延迟大概多少

#### Showing / Setting Names of Domain and Host ｜ 查看 / 设置「域名」和「主机名」

1. **domainname 命令**
  - 功能：显示当前机器所在的「NIS/域名」
  - 示例：
  - piano% domainname
  vlsi.zju.edu.cn.
  - 含义：这台叫 `piano` 的机器属于域 `vlsi.zju.edu.cn`
2. **hostname 命令**
  - 功能：显示当前机器的「主机名」
  - 示例：
  - piano% hostname
  piano<br />
  
  piccolo$ hostname
  piccolo
  - 含义：同一个域里可以有多台主机：`piano`、`piccolo` 等
3.

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ICCAD/DetailCh4-08.webp)

用户名@主机名(hostname):当前工作目录$

#### Showing / Setting IP Addresses of Computers ｜ 用 `/etc/hosts` 管理 IP 和主机名

- **/etc/hosts 文件**
  - 作用：保存 **IP 地址 ↔ 主机名** 的对应关系
  - 例如：
  - 127.0.0.1      localhost
  10.14.111.204  baton
  10.14.111.205  organ
  10.14.111.206  piano  loghost
  10.14.111.207  violin
  10.14.111.208  viola
  ...
- **查看内容**
  - 命令：`cat /etc/hosts`
  - 就能看到当前机器上配置的所有 IP/主机名映射
- **使用示例**
  - 因为 `/etc/hosts` 里有：
  - 10.14.111.208  viola
  - 所以可以直接：
  - ping viola
  - 系统会先在 `/etc/hosts` 里查到 `viola` 对应 IP，再去 ping 这台机器。

#### DNS 服务器与名字解析

<alert type="tip">

- **DNS**（Domain Name System，**域名系统**）是互联网的一项核心服务。它的作用是将人类容易记忆的**域名**（如 `www.google.com`）转换为计算机能够识别的 **IP 地址**（如 `172.217.161.68`），以便浏览器能够加载网络资源。
- **DHCP**（Dynamic Host Configuration Protocol，**动态主机配置协议**）是一个局域网网络协议，主要用于**自动**为网络中的设备分配 IP 地址及相关的网络配置参数。

</alert>

- **DNS 服务器配置：**`/etc/resolv.conf`
  - 保存要使用的 DNS 服务器 IP：
  - `cat /etc/resolv.conf`
  nameserver 10.10.0.21
  nameserver 10.214.1.201
  - **DNS 可由 DHCP 自动下发**
    - 连接到校园网、公司网、路由器时，DHCP 会自动给你（不用手动配置了）：
    
      - IP 地址
      - 网关
      - DNS 服务器地址
    - 相关配置可在：`/etc/dhcp/dhclient.conf`中查看/修改。
- **查询域名：**`host` **命令**
  - 用 DNS 查询某域名的 IP：
  - host ubuntu.com
  ## ubuntu.com has address 185.125.190.20
  
  ## ubuntu.com has IPv6 address 2620:2d:4000:1::28
- **名字解析顺序：**`/etc/nsswitch.conf`
  - 决定系统先从哪里查主机名（本地文件 / DNS / 其它服务）
  - 示例行：
  - hosts:  files nisplus dns mdns4
  - 含义：解析主机名时，先查 `/etc/hosts`（files），再查 NIS+，再查 DNS，最后查 mDNS。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ICCAD/DetailCh4-09.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ICCAD/DetailCh4-10.webp)

#### Network Configuring Commands | 网络配置命令

#### 1. `ip` 命令

这是 Linux 中最新、功能最强大的网络配置工具，它旨在取代旧的 `ifconfig` 等工具

- **功能**：TCP/IP 接口和路由工具”
- **图示示例**：

  - `$ ip addr show`: 显示所有网络接口的 IP 地址信息。
  - `$ ip route show`: 显示内核的路由表（即数据包该往哪里发）。
  - `$ ip neighbor help`: 显示关于邻居表（ARP 缓存）管理的帮助信息。

#### 2. `ifup` / `ifdown`

这一组命令用于更高级别的网络接口管理。

- **功能**：

  - `ifup`: 激活（启动）指定的网络接口。
  - `ifdown`: 禁用（关闭）指定的网络接口。
- **重要细节**：图中提到它 "`runs ip as per /etc/network/interfaces`"。这意味着这两个命令会读取系统配置文件，并根据文件中的配置自动执行底层的 `ip` 命令来设定网络。

#### 3. `ifconfig`

这是一个经典（较老）的网络接口配置工具。

- **功能**：用于配置、控制和查询 TCP/IP 网络接口参数。

#### 4. `netstat`

这是一个用于监控网络状态的通用工具。

- **功能**：显示网络连接（如哪些端口正在监听，哪些 IP 连接到了本机）、路由表、接口统计数据、伪装连接（Masquerade）和多播成员。
- **图示参数建议**：

  - `-r`: 显示路由表 (Routing table)。
  - `-i`: 显示网络接口统计信息 (Interfaces)。
  - `-s`: 显示每种协议的统计摘要 (Statistics)。

### Useful Remote Connection Utilities | 实用的远程连接工具

1. 早期工具（基本都不安全）

  - `ftp [options] host`  transfer file(s) using file transfer protocol
  - `telnet [host [port]]` communicate with host using telnet protocol

Are they secured? Any user/passwd information on network?

问题：账号和密码明文传输

1. 远程登录 / 远程执行

  - `rlogin / rsh`
    - 早期远程登录、远程执行命令的工具（也不安全）
    - login/shell execution remotely on another machine;
  - `ssh`
    - remote login or remote execution using secure shell
    - 安全的远程登录、远程执行命令、加密传输.
  - `rcp/scp`
    - remotely copy files from this machine to another machine;
    - 功能：从本机复制文件到远程机器，或反向复制; `scp` 基于 SSH，传输加密，常用
  - `rsync`
    - 功能：在检查内容后智能地通过网络复制文件。
2. 通过网络下载 / 访问内容

  - `curl`
    - transfer a URL via HTTP, FTP, IMAP, etc
  - `wget`
    - download files over the Internet via HTTP or FTP
    - 通过 HTTP/FTP 下载文件，可断点续传、递归下载网站
  - `lynx / links`
    - text-mode (mini) web browser
    - 纯文本模式的“小型浏览器”，在终端里浏览网页（无图形界面）

#### ssh Application | ssh 应用

1. 基本用法
2. ssh <span>

-l username

</span>

 hostname <span>

command

</span>


  - `-l username`：指定 **远程登录的用户名**（不写就用本机当前用户）
  - `hostname`：远程主机名或 IP
  - `[command]`：可选；如果写了，只在远程执行这条命令然后退出；不写则进入远程交互式 shell

---

1. 示例1 ：远程登录

banjo% ssh -l shiz viola

shiz@viola's password: ********

Last login: Thu Nov 29 20:25:52 from piano

viola%

- 从主机 **banjo**，以用户 **shiz** 登录到主机 **viola**
- 输入密码后，拿到 `viola%` 提示符 → 已经在远程机 **viola** 上操作

---

1. 示例 2：远程执行一条命令

steve@piccolo:~$ ssh violin who

steve@violin's password: ********

root tty2 Jul 24 07:19

lena tty3 Jul 23 22:24

lena :0  Jul 25 22:03

- 本地用户 **steve** 在机器 **piccolo** 上执行
`ssh violin who`
- 连接到主机 **violin**，在远程运行 `who` 命令
- 打印出远程机上当前登录用户列表，随后自动退出 ssh

#### scp - Copying from Machine to Machine | scp 应用

1. Synopsis ｜ 概要

  - `scp [ -pr ] [other network options] file1 file2`
    - `file1`：源（可以是本地也可以是远程）
    - `file2`：目的地（可以是本地也可以是远程）
  - 常用选项：
  
    - `-p`：保留原文件的时间戳、权限等属性
    - `-r`：递归复制目录（整文件夹拷过去）

`scp` 底层走 **SSH**，所以是加密传输

1. Remote file (directory is file too) name forms ｜ 远程文件的写法

  - hostname:file
  - username@hostname:file
  - [username@host.domain](mailto:username@host.domain):file

> 一般常用：`scp 本地文件  user@远程主机:路径` 或反过来。

#### FTP - File Transfer Protocol

FTP 是一种文件传输协议、**应用层协议**

1. **FTP 是什么？**
  - FTP = *File Transfer Protocol*，一种 **应用层协议**，专门用来在网络上传文件。
2. **FTP 服务端（Server）**
  - 提供 FTP 服务的，是后台的 **网络服务守护进程**（daemon）。
  - 常由 `inetd` / `xinetd` 这类“超级守护进程”负责管理、启动。
3. **FTP 客户端（Client）类型**
  - **图形界面（GUI）客户端**
    - Windows：WinSCP、FileZilla
    - Unix/Linux：gftp、filezilla
    - 像文件管理器一样拖拽上传/下载，适合日常使用。
  - **命令行客户端** `ftp`
    - 在 Unix / Linux 上很常见，需要会基本用法（`ftp host`、`get`、`put` 等）。
4. **补充：主动 / 被动模式**
  - PPT 提到：`active / passive mode` 是另一个话题
  - 指 FTP 建立数据连接的两种方式，会影响穿防火墙/代理的行为。

---

##### 基本用法

- 启动方式
- ftp <span>

host

</span>


  - 例：`ftp vlsi.zju.edu.cn`  直接连到远程 FTP 服务器
  - 例：`ftp`  先进入 ftp 交互模式，再用 `open host` 连接
- 在 `ftp>` 提示符下输入 `help` 可查看所有子命令。

---

##### 常用 ftp 子命令

- `open host` / `close`
连接 / 断开 FTP 服务器
- `ascii` / `binary`
选择传输模式：文本 / 二进制（程序、图片一定要 binary）
- `cd` / `lcd`
  - `cd`：切换 **远程** 目录（Server）
  - `lcd`：切换 **本地** 目录（Client）
- `!`
暂时跳回本地 shell 执行命令，例如 `!ls` 查看本地目录
- `ls`
查看远程当前目录内容
- `get` / `mget`
下载 1 个 / 多个文件（multi-get）
- `put` / `mput`
上传 1 个 / 多个文件
- `verbose`
打开/关闭详细输出
- `bye` / `quit`
退出 ftp 会话

匿名登陆如何拼写！！！

---

##### ftp Sample：一次文件上传示例

ftp ftp.tsmc.com        # 连接服务器

...                     # 输入用户名/密码

passwd: ********

ls                      # 看远程当前目录

cd /upload              # 切换到远程的 /upload 目录

lcd /home/my_home/gds_files  # 切到本地存放文件的目录

!ls                     # 在本地列出要上传的文件

binary                  # 切换为二进制传输模式

mkdir my_upload         # 在远程创建目录 my_upload

cd my_upload            # 进入远程 my_upload 目录

mput *.gds2             # 批量上传所有 .gds2 文件

ls                      # 再次查看远程目录确认上传成功

bye                     # 退出 ftp

> 整体流程：**连接 → 调好本地/远程目录 → 设为 binary → 上传文件 → 检查 → 退出**。

#### HTTP Server and Browser

- **HTTP**：Hyper Text Transfer Protocol

  - 一种网络协议，用来在 Web 上传输网页、图片等超文本内容。
- **URL**：Uniform Resource Locator

  - 统一资源定位符，即我们说的“网址”，用来在 HTTP 中指明**具体资源的位置**。
- **Unix 上常见的 HTTP 服务器**
  - Apache HTTP Server（程序名常叫 `httpd`）
- **Unix 上的浏览器（负责解释 HTML/使用 HTTP）**
  - 早期：Mosaic
  - 后来：Netscape Navigator / Mozilla / Firefox / Chrome / Safari
  - 还有纯文本模式的浏览器：lynx、links 等

---

#### Mail in Unix Environment

- 发送邮件命令：
- mail address_list

  - 地址格式一般：`username@hostname.domainname`
- **邮件服务器软件**：`sendmail`（负责收发、转发邮件）
- **远程收发邮件使用的协议**
  - 发送：**SMTP**（Simple Mail Transfer Protocol）
  - 接收：**POP3** 或 **IMAP**
- **图形界面邮件客户端示例**
  - Netscape Composer
  - Mozilla Thunderbird
  - Evolution 等

### 微信公众号文章
