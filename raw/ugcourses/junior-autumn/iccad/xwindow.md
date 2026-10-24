# XWindow

> X Window 图形界面系统

### Unix X Window

#### X Window 基本概念理解

- X 窗口系统分为 **X server** 与 **X client**
- 因为其 **Server/Client（主从架构）**，这就意味着 X 窗口可以跨网络跨平台运行

> - **X Server：执行协议、掌控显示与输入的那一端**
>   - 负责屏幕显示 + 键盘鼠标输入
> - **X Client：真正的应用程序**
>   - 比如 xterm、firefox、你的 GUI 程序，它请求画什么，但它不直接画到屏幕上
> - **为什么它要分 Server / Client？**
> - 因为设计目标不是只在本机画图，而是要做到：
> 
>   - 程序可以在 A 机器运行
>   - 画面可以显示在 B 机器屏幕上
>   - 键盘鼠标从 B 机器输入
>   - 网络传输这些图形/事件
> - 这就是 **“可跨网络跨平台运行”** 的根本原因：
> **把“运行程序”和“管理显示/输入”拆开了**

<table>
<thead>
  <tr>
    <th>
      场景
    </th>
    
    <th>
      谁是 Server （提供服务的一方）
    </th>
    
    <th>
      谁是 Client （接受服务的一方）
    </th>
    
    <th>
      逻辑
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      Web 上网
    </td>
    
    <td>
      网站主机
    </td>
    
    <td>
      你的浏览器
    </td>
    
    <td>
      你想要数据，网站主机提供数据。
    </td>
  </tr>
  
  <tr>
    <td>
      X Window
    </td>
    
    <td>
      你的显示器
    </td>
    
    <td>
      远端的程序
    </td>
    
    <td>
      程序想要有地方显示和操作，你的显示器鼠标提供了显示和操作。
    </td>
  </tr>
</tbody>
</table>

- 而 **X11（X11R6: X Protocol version 11 Release 6）** 本身是一个**协议**而不是一个操作系统，其与硬件无关，利用网络架构来进行图形接口的执行与绘制
- 所以利用 X11 实现的 X Window 本身与计算机结构和操作系统**独立**，因为XClient(应用程序)不需要直接与硬件通信，通过X11协议来和XServer通信即可
- 具体的实现要靠支持该协议的软件，在 Linux 系统下最流行的是实现 **Xorg** (现代)和 **XFree86**(较早的主流)

  - 毕竟X11只是一个协议，具体的实现需要以靠Xorg/XFree86这种具体的软件，就跟HTTP协议需要Chrome一样(bushi)

> - **X Server 的具体实现（软件）**，负责：
> 
>   - 接管显示输出（把图画到屏幕上）
>   - 管理键盘/鼠标输入
>   - 把输入事件分发给应用（X Client）
>   - 接收应用的绘图请求并执行绘制

#### Client Server Model

- 基本模式为：**Server 等待 Client 的请求**，听到后执行
- **XServer** 管理硬件（键鼠输入、屏幕显示），而 **X Client** 则是在跑的应用程序
- 当用户点击鼠标或敲击键盘时，X Server 接受设备的输入信息，并将信息传递给 X Client
- X Client 上有在跑的应用程序。程序根据输入信息把结果再发回 X Server，告诉 Server 在哪里、执行什么操作
- X Client 应用程序会将所想要呈现的画面告知 X Server，最终由 X server 来将结果通过他所管理的硬件绘制出来
- 因此判断两台机器谁是 Client，谁是 Server，**只要看谁在管硬件管屏幕，谁就是 Server**
- 所以远端服务器在你电脑上画图，远端就是 Client，你就是 Server。这就不同于 FTP 远端是 Server，自己是 Client 的情况

#### X Window <=> MS Windows?

- 相同点

  - 都提供图形界面，允许用户交互
- 不同点

  - X Window 灵活性强，可跨网络跨平台运行，采用客户端/服务器模式
  - **MS Windows 是完整的操作系统**

### Using X Commands

- `xset q`：查询 X 显示，询问 X display 的情况，比如颜色、背景、字体等 `xset=X Server Settings` `q=query`

> 它是向 X Server 询问参数，比如：
> 
> - 屏幕保护/节能（DPMS）
> - 键盘重复率
> - 蜂鸣器
> - 鼠标加速度
> - 以及一些显示相关设置（不同系统输出略有差异）

- `xterm [-option]`：打开一个 X 终端，可以根据 option 进行形状、字体等设置  `xterm=X Terminal`

> `xterm` 是最经典的 X 程序之一。
> 
> - 它本质是一个 **X Client（应用程序）**
> - 它会通过 X11 请求 X Server 画出一个终端窗口
> 
> `[-option]` 就是参数，比如：
> 
> - 字体、颜色、窗口大小、标题等

- `xeyes`：产生一个有眼睛的窗口
- `xclock`：产生一个时钟

上面这俩主要的价值还是在于验证 X 能不能正常显示
