# Chapter 6：Xwindow

> X Window 系统：详细版笔记

## Xwindow

### **Introduction**

- **基本定位**
  - 行业标准的软件系统，用来在**网络工作站**上开发**可移植的图形界面**。
  - 同时是一套**窗口系统的规范与实现**，并提供**简单的编程接口**。
- **历史与普及**
  - 由 **MIT、DEC、IBM** 等机构共同开发。
  - 自 **1986 年首次发布**以来，已在几乎所有类型的**位图图形显示设备**上实现。
- **版本信息**
  - **X11** 于 **1987 年发布**。
  - 最新的大版本为 **X11R7.7**（可在 [https://www.x.org/releases/](https://www.x.org/releases/) 查看）。
- **图形扩展**
  - 早期并不存在针对现代 GPU 和视频加速的复杂 2D/3D 客户端渲染库。
  - 目前这类能力通过 **X 的扩展（X extensions）** 来提供和支持。

### X 的主要特性（X Features）

- **与机器架构和操作系统无关**
  - 图形编程接口在所有平台上保持一致。
  - 同一程序可在网络中任意主机运行，但把图形显示到任意工作站上。
- **支持多应用共享同一屏幕**
  - 多个应用程序可以同时在一个显示屏上绘制。
  - 应用之间可以共享窗口及其他屏幕资源。
- **提供丰富的编程库且源码开放**
  - 有大量 X 库可用，源代码可自由获取和分发。

---

### X 的客户端–服务器模型（Client-Server Model）

- **X Display Server（X 显示服务器）**
  - 单一进程，管理本工作站的图形显示和 I/O 设备。
  - 运行在带图形显示的工作站上。
  - 通过网络与各个 X Client 通信。
- **X Clients（X 客户端）**
  - 请求服务器进行图形显示的应用程序。
  - 使用 **X-Protocol** 通过网络与服务器通信。
  - 上层还可以有更高级的库对 X-Protocol 做封装（如 Xlib 等）。

---

#### X Server 与 X Clients（X Server and X Clients）

- **基本关系**
  - 每个 X 显示都对应一个 X 服务器。
  - 任何想在这个显示上画图的进程都可以是一个 X Client。
- **显示名称（display name）格式**
  - `hostname:displaynumber.screennumber`
  - 例：
  
    - `:0.0`, `:0.1`, `:0.2` 等 → 本地默认 X 服务器的不同屏幕。
    - `:0` → 本地默认 X 服务器的默认屏幕。
- **通信方向**
  - 客户端向服务器发 **请求（requests）**，服务器返回 **应答（replies）**，如图示多个 X Client 连接同一个 X Server。

---

#### 客户端/服务器通信（Client/Server Communication）

- **Requests（客户端 → 服务器，约 100 种类型）**
  - 窗口操作：创建、销毁、移动、缩放等。
  - 2D 图形函数：画线、画圆、绘制文本等。
  - 资源分配：字体、颜色等图形资源。
  - 事件管理：注册/管理感兴趣的事件

> - 键盘移动了 or 鼠标双击or鼠标移动

- 特点：通常是**异步(asynchronous)**的（客户端发出请求后默认认为成功，不必等待立即回复）。
- **Replies（服务器 → 客户端）**
  - 服务器针对客户端请求返回的数据包，例如返回当前鼠标位置。
  - 一般与某个请求**同步**（客户端需要等待这个结果）。
  - **XCB**（X C Binding）库改进了这一机制，允许一次发送多条请求，再在需要时批量或延迟获取回复，提高效率。

---

#### X Events（X 事件）

- **定义**
  - 由服务器发送的消息，是用户操作（通常是输入）直接或间接产生的结果。
  - 用于通知客户端：有“感兴趣”的事情发生，需要客户端处理。
- **事件种类（共约 34 类，示例）**
  - 键盘输入。
  - 定位器（鼠标）移动。
  - 鼠标按键输入。
  - 窗口状态、大小、位置、层叠顺序的变化。
  - 窗口属性变化。
  - 窗口全部或部分区域需要重绘（exposure）。
  - 选择、剪切/粘贴信息的相关事件。
  - 其他客户端发送的消息事件。

---

#### 事件机制（Event Mechanism）

- **事件选择（event mask）**
  - 客户端通过设置 **事件掩码** 来声明自己希望接收的事件类型。
  - 事件掩码是一个位掩码，每一位对应一种事件。
  - 示例调用：

```c
XSelectInput(theDisp, mainW,
             ExposureMask | KeyPressMask |
             StructureNotifyMask | ButtonPressMask);
```

- **队列机制**
  - 请求和事件都通过队列管理。
  - 服务器为每个客户端维护其请求队列和事件队列。
  - 客户端通过 API（如 `XNextEvent(theDisp, &event);`）从队列中依次取出事件并处理。

#### 服务器资源（Server Resources）

- **定义**
  - 由 **X 服务器维护**、可以被所有客户端使用/共享的对象。
- **典型类型**
  - 窗口（Windows，最基础的资源）
  - 图形上下文（Graphics Context，保存绘图属性的一组参数）
  - 字体（Fonts）
  - 光标（Cursors）
  - 颜色映射表（Color Maps）
  - 像素图/位图（Pixmaps）等。
- **生命周期**
  - 资源**存放在服务器端**。
  - 但由客户端通过请求来**创建、使用、销毁**。
- **标识方式**
  - 每个资源都有一个由服务器分配的 **resource ID** 作为唯一标识。
- **共享特性**
  - 同一资源可以被多个客户端**低成本地共享**（如共享字体、颜色表、pixmap 等）。

<mark>

Microsoft Windows 和 X windows 区别在哪里

</mark>



<mark>

前者是Operating System， 后者是GUI

</mark>



#### X Window：最基础的资源（A Window: The Most Fundamental X Resource）

- **窗口的本质**
  - 窗口是屏幕上的一个**简单矩形区域**。
  - 特点：
  
    - **无装饰（No decorations）**：边框、标题栏等不属于窗口本体。
    - **有自己的坐标系**：窗口内部的绘图与事件位置以该坐标系为准。
    - **可组合成更高层界面对象**：多个窗口叠加/嵌套可构成按钮、面板等组件。
    - **一个应用可能有很多窗口**：可能达到数百个（用于不同控件/区域）。
- **窗口的属性与属性集（attributes & properties）**
  - 每个窗口都带有一组属性/属性项。
  - 客户端可以通过向服务器发送请求来**修改**这些属性/属性项（例如大小、背景、事件订阅等）。
- **窗口曝光（window exposure）与重绘责任**
  - 当窗口内容被遮挡后又重新露出（exposure）时：
  
    - **客户端负责维护并重绘窗口内容**（服务器不保证替你保存内容）。
    - **X Composite Extension** 可以对内容进行缓冲（buffer），但是否启用取决于**服务器端设置**，而非客户端单方面决定。
- **窗口树（Window Trees）与窗口管理器（Window Manager）**
  - 窗口按层级结构组织成 **窗口树（Window Trees）**。
  - **窗口管理器**可以对窗口进行操作与装饰：如移动、缩放、加边框/标题栏等。

#### X11 的问题与替代方案（X11 Problems and Its Replacements）

- **窗口管理器（Window Manager）的定位**
  - Window Manager 本质上是一个**特殊的 X Client**。
  - 它维护系统中**所有窗口**的信息：窗口列表、位置、大小、遮挡/重叠关系等，并据此进行管理。
- **现代桌面环境带来的复杂性（合成式窗口管理）**
  - 现代桌面环境（如 **GNOME、KDE**）通常采用**合成式窗口管理器（compositing WM / compositor）**。
  - 合成器的关键做法：
  
    - 为**每个窗口维护一个离屏缓冲区（off-screen buffer）**；
    - 再把这些缓冲区**合成为最终的顶层画面**显示到屏幕上（实现透明、阴影、动画等效果）。
- **X11 架构的核心问题：仍可实现，但过于复杂**
  - X 架构并非不能支持合成，但在现实中会形成较复杂的链路：
  
    - X Clients → X Server → Compositor（合成器）→ 内核显示/输入子系统（如 KMS、evdev）
  - 结果：组件分层多、职责分散，整体架构显得**冗长且复杂**。
- **替代方向：Wayland 的简化思路**
  - Wayland 将“显示服务器 + 合成器”的角色更集中：
  
    - **Wayland Compositor** 直接作为核心组件，统一负责合成与显示，并与内核的 KMS/evdev 交互；
    - Wayland Clients 直接与 Wayland Compositor 通信。
  - 典型链路：
  
    - Wayland Clients → Wayland Compositor → 内核（KMS、evdev）
  - 目标：在满足现代合成需求的同时，减少 X11 式的结构复杂度。
  ![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ICCAD/DetailCh6-01.webp)

Wayland 介绍（幻灯片给出的参考）：

[https://wayland.freedesktop.org/](https://wayland.freedesktop.org/)

> Ctrl Z + bg
> 
> 或者 xterm &

#### 使用 X 的常用命令（Using X Commands）

- `xset q`
  - 用途：查询当前 **X display** 的状态与配置（query your X display）。
- `xterm [-option]`
  - 用途：启动一个 **X 终端窗口**（open an X terminal）。
  - 说明：`xterm` 的可选参数很多，可用于配置终端外观（字体、颜色、大小等）。
- **其他常见 X 工具（utilities）**
  - `xwininfo`：查看窗口信息（如窗口 ID、大小、位置、层级等）。
  - `xeyes`：演示程序（眼睛跟随鼠标移动）。
  - `xclock`：时钟程序。
  - 以及更多同类工具。
- **延伸问题（本页提出）**
  - 如何在一台机器上运行 X 程序，但把 GUI 显示到另一台机器上？
  - 要点通常与 **X 的网络透明性**有关：需要指定目标显示（display）并允许远端连接（后续页一般会讲 `DISPLAY`、`ssh -X/-Y`、`xhost` 等）。

#### 远程运行 X 程序（Remotely Running X Program）

- **场景设定**
  - 程序运行在 **机器 A**，X 显示服务器（X display server）运行在 **机器 B**。
  - 直接传输时属于**不安全数据（unsecured data）**。

---

##### 方法一：直接让 B 接收来自 A 的图形输出（不安全/需授权）

- **在机器 B 上：允许 A 连接到本机 X 服务器**
  - 命令：
  - machine_b$ xhost +machine_a    # 或者使用 xauth
  - 含义：让 B 的 X server 接受来自 A 的图形连接请求。
- **在机器 A 上：指定图形应该显示到哪台机器**
  - 命令：
  - machine_a<span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mi>
  
  e
  
  </mi>
  
  <mi>
  
  x
  
  </mi>
  
  <mi>
  
  p
  
  </mi>
  
  <mi>
  
  o
  
  </mi>
  
  <mi>
  
  r
  
  </mi>
  
  <mi>
  
  t
  
  </mi>
  
  <mi>
  
  D
  
  </mi>
  
  <mi>
  
  I
  
  </mi>
  
  <mi>
  
  S
  
  </mi>
  
  <mi>
  
  P
  
  </mi>
  
  <mi>
  
  L
  
  </mi>
  
  <mi>
  
  A
  
  </mi>
  
  <mi>
  
  Y
  
  </mi>
  
  <mo>
  
  =
  
  </mo>
  
  <mi>
  
  m
  
  </mi>
  
  <mi>
  
  a
  
  </mi>
  
  <mi>
  
  c
  
  </mi>
  
  <mi>
  
  h
  
  </mi>
  
  <mi>
  
  i
  
  </mi>
  
  <mi>
  
  n
  
  </mi>
  
  <msub>
  <mi>
  
  e
  
  </mi>
  
  <mi>
  
  b
  
  </mi>
  </msub>
  
  <mo>
  
  :
  
  </mo>
  
  <mn>
  
  0.0
  
  </mn>
  
  <mi>
  
  m
  
  </mi>
  
  <mi>
  
  a
  
  </mi>
  
  <mi>
  
  c
  
  </mi>
  
  <mi>
  
  h
  
  </mi>
  
  <mi>
  
  i
  
  </mi>
  
  <mi>
  
  n
  
  </mi>
  
  <msub>
  <mi>
  
  e
  
  </mi>
  
  <mi>
  
  a
  
  </mi>
  </msub>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  export DISPLAY=machine_b:0.0
  machine_a
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:0.8778em;vertical-align:-0.1944em;">
  
  
  
  </span>
  
  <span className="mord,mathnormal">
  
  e
  
  </span>
  
  <span className="mord,mathnormal">
  
  x
  
  </span>
  
  <span className="mord,mathnormal">
  
  p
  
  </span>
  
  <span className="mord,mathnormal" style="margin-right:0.0278em;">
  
  or
  
  </span>
  
  <span className="mord,mathnormal">
  
  t
  
  </span>
  
  <span className="mord,mathnormal" style="margin-right:0.0278em;">
  
  D
  
  </span>
  
  <span className="mord,mathnormal" style="margin-right:0.0785em;">
  
  I
  
  </span>
  
  <span className="mord,mathnormal" style="margin-right:0.0576em;">
  
  S
  
  </span>
  
  <span className="mord,mathnormal" style="margin-right:0.1389em;">
  
  P
  
  </span>
  
  <span className="mord,mathnormal">
  
  L
  
  </span>
  
  <span className="mord,mathnormal">
  
  A
  
  </span>
  
  <span className="mord,mathnormal" style="margin-right:0.2222em;">
  
  Y
  
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
  <span className="strut" style="height:0.8444em;vertical-align:-0.15em;">
  
  
  
  </span>
  
  <span className="mord,mathnormal">
  
  ma
  
  </span>
  
  <span className="mord,mathnormal">
  
  c
  
  </span>
  
  <span className="mord,mathnormal">
  
  hin
  
  </span>
  
  <span className="mord">
  <span className="mord,mathnormal">
  
  e
  
  </span>
  
  <span className="msupsub">
  <span className="vlist-t,vlist-t2">
  <span className="vlist-r">
  <span className="vlist" style="height:0.3361em;">
  <span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
  <span className="pstrut" style="height:2.7em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size6,size3,mtight">
  <span className="mord,mathnormal,mtight">
  
  b
  
  </span>
  </span>
  </span>
  </span>
  
  <span className="vlist-s">
  
  ​
  
  </span>
  </span>
  
  <span className="vlist-r">
  <span className="vlist" style="height:0.15em;">
  <span>
  
  
  
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  
  <span className="mspace" style="margin-right:0.2778em;">
  
  
  
  </span>
  
  <span className="mrel">
  
  :
  
  </span>
  
  <span className="mspace" style="margin-right:0.2778em;">
  
  
  
  </span>
  </span>
  
  <span className="base">
  <span className="strut" style="height:0.8444em;vertical-align:-0.15em;">
  
  
  
  </span>
  
  <span className="mord">
  
  0.0
  
  </span>
  
  <span className="mord,mathnormal">
  
  ma
  
  </span>
  
  <span className="mord,mathnormal">
  
  c
  
  </span>
  
  <span className="mord,mathnormal">
  
  hin
  
  </span>
  
  <span className="mord">
  <span className="mord,mathnormal">
  
  e
  
  </span>
  
  <span className="msupsub">
  <span className="vlist-t,vlist-t2">
  <span className="vlist-r">
  <span className="vlist" style="height:0.1514em;">
  <span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
  <span className="pstrut" style="height:2.7em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size6,size3,mtight">
  <span className="mord,mathnormal,mtight">
  
  a
  
  </span>
  </span>
  </span>
  </span>
  
  <span className="vlist-s">
  
  ​
  
  </span>
  </span>
  
  <span className="vlist-r">
  <span className="vlist" style="height:0.15em;">
  <span>
  
  
  
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  
   your_program
  - 含义：把应用的显示目标设置为 B 的 display（`:0.0`）。

---

##### 方法二：通过安全隧道做 X 转发（X forwarding through secured tunnel）

- **开启 SSH 的 X11 转发能力（配置层面）**
  - 在机器 A 的 SSH 配置中打开 `ForwardX11`（文件：`/etc/ssh/ssh_config`）。
  - 作用：在 A 上创建一个**虚拟 X server**，并且会自动设置 `DISPLAY`。
- **在机器 B 上通过 SSH 登录 A，并启用 X forwarding**
  - 命令：
  - machine_b$ ssh -X/-Y machine_a
  - 前提：`xhost` 等访问控制需要设置正确。
  - 登录后：在这个终端里启动图形程序，即可把 GUI 安全地转发回 B 显示。

#### PC 上的 X 模拟器（X Emulator on PC）

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ICCAD/DetailCh6-02.webp)

- **常见实现/软件**
  - 在 PC 上运行 X 相关组件的工具包括：**Exceed、Cygwin、X-Win32、Xshell/Xmanager、VcXsrv** 等。
- **核心结论：PC 充当 X Display（显示端）**
  - PC 上运行 **X server**，因此 PC 相当于“显示服务器/显示端”（幻灯片标注为 machine B）。
  - 远端 Unix 主机运行应用程序，应用作为 **X client**（machine A）。
- **通信路径（与图对应）**
  - 应用的图形输出通过 **X Protocol** 传输，承载在 **TCP/IP / Ethernet** 等网络之上。
  - 常见端口含义（图中标注）：
  
    - **SSH 通道：22 端口**（用于建立安全隧道）。
    - **X11：6000 端口**（传统 X server 监听端口，`6000 + displaynumber`）。
- **两种连接方式的暗示（图中灰字）**
  - **直接 X 连接**：X client 直接连到 PC 的 X server（可能走 6000 端口），安全性较弱。
  - **SSH X forwarding（推荐）**：通过 SSH 隧道转发 X 流量（图中“secured tunnel / possible virtual X server”），由 SSH 负责加密与转发。
- **PC 侧补充**
  - PC 通常还会有一个 **终端模拟器**（用于登录远端并启动 X 程序）。

#### 编写一个 X 应用（Programming an X Application）

- **整体结构**
  - 典型流程分三段：**初始化（Initialization）→ 事件管理（Event management）→ 结束清理（Termination）**。

---

##### A. 初始化（Initialization）

1. **引入头文件**
  - `#include <X11/Xlib.h>`
  - `#include <X11/Xutil.h>`
2. **声明变量**
  - 准备 `Display*`、`Window`、`GC`（图形上下文）等后续要用的数据结构/句柄。
3. **连接到工作站的 display**
  - 与 X server 建立连接，拿到一个 `display` 句柄（本质是通信通道）。
4. **从 display 获取可绘制的 screen**
  - 选择要画在哪个屏幕/屏幕资源上。
5. **创建窗口（Create a window）**
  - 在服务器端创建一个窗口资源（会获得对应的 window id/句柄）。
6. **通知窗口管理器期望的窗口属性**
  - 告诉 Window Manager：窗口应有哪些特性（如标题、大小提示、可否缩放等），便于其装饰与管理。
7. **创建其他资源（如 Graphics Context）**
  - 常见的是创建 **GC**：集中保存绘图属性（颜色、线宽、字体等）。
8. **把窗口映射到屏幕（Map window）**
  - `map` 的意义是：让窗口从“存在但不可见”变成“可见并参与显示”。

---

##### B. 事件管理（Event management）

1. **设置感兴趣事件（event mask）**
  - 告诉服务器：这个窗口/应用需要接收哪些事件（键盘、鼠标、曝光、结构变化等）。
2. **事件循环（Event loop）**

- 逻辑：只要还有事件，就**读取 → 解释 → 处理**下一条事件。
- 图形输出通常也发生在这里（例如收到 `Expose` 事件后重绘）。

---

##### C. 结束（Termination）

1. **销毁资源（Destroy resources）**

- 释放窗口、GC、pixmap 等服务器端/客户端侧资源。

1. **关闭 display 连接（Close display）**

- 断开与 X server 的连接。

1. **退出程序（Exit）**

---

##### 现实开发补充（图右侧要点）

- 现在**直接调用 Xlib / Xt / XCB** 来写完整 GUI 已经比较少见。
- 更常见做法：使用更高层的 GUI 工具包（如 **GTK+、Qt**），由它们封装底层 X（或 Wayland）细节。

#### Demo X 源码示例（逐段说明）

- **用途概览**
  - 这是一个最小化的 **Xlib** 程序：创建一个窗口、设置窗口属性与事件监听，然后进入事件循环；在特定事件（如鼠标点击）发生时做处理并输出信息。

---

##### 依赖与头文件（A Demo X Source File (1)）

- **依赖安装（Ubuntu）**
  - `sudo apt-get install libx11-dev`：安装 X11 开发头文件与库，才能编译 Xlib 程序。
- **头文件含义（关键点）**
  - `X11/Xlib.h` / `X11/Xutil.h`：Xlib 核心 API 与常用工具结构体（如 `XSizeHints`）。
  - `X11/cursorfont.h`：提供光标字体常量（如 `XC_umbrella`）。
  - 其余如 `stdio.h`、`stdlib.h` 为标准 C 库。
- **全局 X 相关变量**
  - `Display *theDisp;`：与 X server 的连接句柄。
  - `int theScreen;`：使用的屏幕编号（一个 display 下可能有多个 screen）。
  - `Window rootW, mainW;`：根窗口与主窗口（X 的窗口在服务器端以 ID 表示）。
  - `HandleEvent(XEvent *)`：事件分发函数声明。

---

##### 建立连接与定位根窗口（A Demo X Source File (2)）

- `XOpenDisplay(NULL)`
  - 打开到 X server 的连接。`NULL` 表示使用环境变量 `DISPLAY` 指定的默认显示。
  - 若返回 `NULL`，说明无法连接到 X server，程序直接报错退出。
- `DefaultScreen(theDisp)`
  - 获取默认 screen 编号，后续创建窗口需要。
- `RootWindow(theDisp, theScreen)`
  - 获取该 screen 的根窗口（root window）。
  - 根窗口是所有顶层窗口的父窗口（通常由窗口管理器/桌面环境管理）。

---

##### 设置窗口约束、创建窗口、选择事件（A Demo X Source File (3)）

- **窗口大小提示（**`XSizeHints hints`**）**
  - `hints.width/height = 100`：初始大小 100×100。
  - `max_width/max_height = 600`、`min_width/min_height = 16`：最大/最小尺寸限制。
  - `width_inc = height_inc = 16`：调整大小的步进（每次缩放以 16 为单位）。
  - `hints.flags |= PMaxSize | PMinSize | PResizeInc;`：启用这些限制，让窗口管理器知道要遵守这些 hint。
- **设置鼠标光标（**`XSetWindowAttributes xswa`**）**
  - `xswa.cursor = XCreateFontCursor(theDisp, XC_umbrella);`：把光标设成“伞”的样式。
  - `xswamask = CWCursor;`：告诉 `XCreateWindow` 本次属性里只有 `cursor` 这一项需要应用。
- **创建窗口（**`XCreateWindow`**）**
  - 以 `rootW` 为父窗口，在坐标 `(0,0)` 创建大小 `100×100` 的窗口，边框宽度为 `2`。
  - `CopyFromParent`：许多视觉/深度/类信息从父窗口继承（简化参数）。
  - 返回的 `mainW` 是窗口句柄（ID）。
- **设置窗口基本属性（**`XSetStandardProperties`**）**
  - 设置窗口名/图标名（这里都为 `"x_try"`），并把前面的 `hints` 作为窗口管理器参考。
- **选择要监听的事件（**`XSelectInput`**）**
  - `ExposureMask`：窗口需要重绘时（Expose）。
  - `StructureNotifyMask`：窗口结构变化，如 resize/move（ConfigureNotify 属于这一类）。
  - `ButtonPressMask`：鼠标按键按下事件。

---

##### 显示窗口与事件主循环（A Demo X Source File (4)）

- `XMapWindow(theDisp, mainW)`
  - “映射”窗口：让窗口从不可见变为可见（交给窗口管理器安排显示）。
- **主循环**
  - `XNextEvent(theDisp, &event);`：阻塞等待下一个事件，读到 `event` 中。
  - `HandleEvent(&event);`：交给事件处理函数分发。

---

#### 事件处理逻辑（A Demo X Source File (4)(5)）

- `switch (event->type)`**：按事件类型分支处理**
- **Expose（窗口需要重绘）**
  - `XExposeEvent *exp_event = (XExposeEvent *) event;`：把通用事件解释为 Expose 事件结构。
  - 注释提示：若 `exp_event->window == mainW`，应该在此处执行重绘（例如重新画图形/文字）。
  - 这里示例没有真正绘制代码，只保留了重绘位置。
- **ButtonPress（鼠标按下）**
  - `XButtonEvent *but_event = (XButtonEvent *) event;`
  - 条件：
  
    - `but_event->window == mainW`：事件发生在主窗口上；
    - `but_event->button == Button1`：按下的是鼠标左键。
  - 动作：打印点击坐标 `but_event->x, but_event->y`（窗口内部坐标）。
- **ConfigureNotify（窗口结构变化，如大小/位置变化）**
  - `XConfigureEvent *conf_event = (XConfigureEvent *) event;`
  - 注释提示：窗口尺寸变化后通常也需要重绘/重新布局。
  - 注意：示例注释里写了 `exp_event`，但此分支里实际变量是 `conf_event`——这更像是教学用代码中的小笔误；语义上应当检查 `conf_event->window == mainW`。
- **default**
  - 忽略未处理的事件类型。

---

##### 读代码时可以抓住的“主线”

- **连上 X server**：`XOpenDisplay`
- **找根窗口**：`RootWindow`
- **准备属性 + 创建窗口**：`XCreateWindow`
- **告诉 WM 你的窗口偏好**：`XSetStandardProperties`（含 `XSizeHints`）
- **订阅事件**：`XSelectInput`
- **显示窗口**：`XMapWindow`
- **事件循环**：`XNextEvent` → `HandleEvent`
- **在 Expose/ConfigureNotify 中重绘，在 ButtonPress 中响应输入**
