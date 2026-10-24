# Ubuntu 24.04 安装 Synopsys

> 用 Distrobox 起一个 Ubuntu 20.04 容器跑 Synopsys 2024 工具链，以及一路踩过的坑

Synopsys 2024 系列工具是用旧版 glibc 编译的，在 Ubuntu 24.04 上直接跑会遇到符号不匹配等一堆问题。本文的思路是：用 Distrobox（底层是 podman）起一个 Ubuntu 20.04 容器，工具装在宿主机和容器共享的 HOME 目录下，在容器里运行；license 服务则留在宿主机上跑。

安装器本身的操作（`SynopsysInstaller`、SCL、生成 license、配置环境变量）和 [Ubuntu 22.04 上安装 VCS + Verdi 的知乎教程](https://zhuanlan.zhihu.com/p/1899035861158454466)是一样的，这里不再重复；缺库、FlexLM 这类通用问题，[Verdvana 的这篇总结](https://verdvana.cn/_posts/2021-11-13-Synopsys-EDA-Tools%E5%AE%89%E8%A3%85%E4%B8%AD%E5%87%BA%E7%8E%B0%E7%9A%84%E9%97%AE%E9%A2%98%E5%8F%8A%E8%A7%A3%E5%86%B3%E6%96%B9%E6%B3%95/)也整理得很全。本文只记录容器化的做法和 24.04 上额外踩到的坑。

## 需要的文件

Design Compiler 依赖 `libpng12.so.0`，而 Ubuntu 16.04 之后的软件源就不再提供 libpng12 了。这里放一份可以直接用的（x86_64，libpng 1.2.54）：

直接点这里下载：[libpng12.so.0](/files/libpng12.so.0)，或者在容器里用 wget 拉下来并校验：

```Bash
wget https://xw-soleil.github.io/files/libpng12.so.0
sha256sum libpng12.so.0
# 3637148c97e858efda3a229f8c2f0e9d91f1b5d26eabe7d52e0e84fa30e3bf06
```

这个文件提取自 Ubuntu 16.04（xenial）的官方软件包 [libpng12-0 1.2.54-1ubuntu1](https://launchpad.net/ubuntu/xenial/amd64/libpng12-0)，和 deb 里的 `libpng12.so.0.54.0` 逐字节一致。不想用博客上的文件的话，也可以自己从 deb 里解出来：

```Bash
wget https://mirrors.tuna.tsinghua.edu.cn/ubuntu/pool/main/libp/libpng/libpng12-0_1.2.54-1ubuntu1.1_amd64.deb
dpkg-deb -x libpng12-0_1.2.54-1ubuntu1.1_amd64.deb libpng12
ls -l libpng12/lib/x86_64-linux-gnu/   # libpng12.so.0 -> libpng12.so.0.54.0
```

安装到系统库路径的步骤见下文[问题 4](#%E9%97%AE%E9%A2%98-4%E7%BC%BA%E5%A4%B1-libpng12so0)。

## 日常使用

license 在宿主机，工具在容器里，所以每次分两步：

```Bash
# 1. 宿主机：加载环境并启动 license 服务
source ~/synopsys/env_synopsys_2024.sh
lmg

# 2. 进入容器，再加载一次环境，然后正常跑 vcs / verdi / dc_shell
distrobox enter synopsys-focal
source ~/synopsys/env_synopsys_2024.sh
```

`lmg` 是环境脚本里定义的别名，脚本全文见[下文](#%E7%8E%AF%E5%A2%83%E8%84%9A%E6%9C%AC-env_synopsys_2024sh)。

## 搭建容器

### 创建容器

```Bash
# 宿主机安装 distrobox + podman
sudo apt update
sudo apt install -y podman distrobox

# 创建并进入 Ubuntu 20.04 容器
distrobox create -n synopsys-focal -i ubuntu:20.04
distrobox enter synopsys-focal
```

distrobox 默认共享 HOME 目录，所以 `~/synopsys/` 下的工具不用复制，容器里直接可用。

### 容器内安装基础依赖

```Bash
sudo apt update
sudo apt install -y \
  tcsh csh ksh bash \
  perl python3 gawk sed grep coreutils \
  make file less procps \
  libstdc++6 zlib1g libgcc-s1 \
  libncurses5 libtinfo5 \
  libx11-6 libxext6 libxrender1 libxt6 libxi6 libxft2 libxmu6 \
  libsm6 libice6 libfontconfig1 libfreetype6 \
  libglib2.0-0 libpng16-16 \
  xauth x11-apps fonts-dejavu-core
```

后文的[一键安装](#%E4%B8%80%E9%94%AE%E5%AE%89%E8%A3%85%E6%89%80%E6%9C%89%E5%AE%B9%E5%99%A8%E5%86%85%E4%BE%9D%E8%B5%96)把所有问题里用到的包合在了一起，嫌麻烦可以直接跳过去。

## 踩坑记录

### 问题 1：design_vision 启动即 Segfault

**现象**：`design_vision` 一启动就 `Segmentation fault (core dumped)`。

**原因**：容器内 hostname（如 `synopsys-focal.soleilUbuntu`）在宿主机 `/etc/hosts` 中没有对应条目。NSS 走 `myhostname` 插件，返回 `fe80::%3` 这种带 scope-id 的 IPv6 link-local 地址，DC 内部调 `gethostid()` → `gethostbyname_r()` 时没有正确处理，直接 segfault。

**修复**：

```Bash
# 在宿主机上添加 hostname 映射（容器内 /etc/hosts 是 bind-mount 只读的）
echo "127.0.1.1 synopsys-focal.soleilUbuntu" | sudo tee -a /etc/hosts

# 在容器内禁用 nss-myhostname（可能也需要先 umount）
sudo umount /etc/nsswitch.conf 2>/dev/null
echo "hosts: files dns" | sudo tee /etc/nsswitch.conf
```

**验证**：`getent ahosts $(hostname)` 应返回干净的 `127.0.1.1`，不再出现 `fe80::...%3`。

### 问题 2：Qt 平台插件初始化失败（Design Vision）

**现象**：`no Qt platform plugin could be initialized`

**修复**：安装 xcb 相关依赖

```Bash
sudo apt install -y libxcb-xinerama0 libxcb-icccm4 libxcb-image0 \
  libxcb-keysyms1 libxcb-randr0 libxcb-render-util0 libxcb-shape0 \
  libxcb-xfixes0 libxcb-xkb1 libxkbcommon-x11-0 libfontconfig1 \
  libxrender1 libxi6 libxext6 libx11-xcb1 libgl1-mesa-glx
```

如不需要 GUI，可用命令行模式 `./dc_shell`，或设置 `export QT_QPA_PLATFORM=offscreen`。

### 问题 3：终端类型警告

**现象**：`Cannot use command line editor for terminal type 'xterm-256color'. (UI-74)`

**修复**：启动前设置 `export TERM=xterm`（已写入 `env_synopsys_2024.sh`）。

### 问题 4：缺失 libpng12.so.0

**现象**：Ubuntu 16.04+ 默认只有 libpng16，DC 需要 libpng12。这个问题 [Verdvana 的文章](https://verdvana.cn/_posts/2021-11-13-Synopsys-EDA-Tools%E5%AE%89%E8%A3%85%E4%B8%AD%E5%87%BA%E7%8E%B0%E7%9A%84%E9%97%AE%E9%A2%98%E5%8F%8A%E8%A7%A3%E5%86%B3%E6%96%B9%E6%B3%95/)里也有记录。

**修复**：按[上文](#%E9%9C%80%E8%A6%81%E7%9A%84%E6%96%87%E4%BB%B6)拿到 `libpng12.so.0`，放到系统库路径：

```Bash
sudo cp libpng12.so.0 /usr/lib/x86_64-linux-gnu/
sudo chmod 755 /usr/lib/x86_64-linux-gnu/libpng12.so.0
sudo ldconfig
ldconfig -p | grep libpng12  # 验证
```

### 问题 5：FlexLM 目录缺失

**现象**：`Can't make directory /usr/tmp/.flexlm, errno: 2`

**修复**：

```Bash
sudo mkdir -p /usr/tmp
sudo touch /usr/tmp/.flexlm
```

### 问题 6：GCC / 编译工具链缺失（VCS）

**现象**：`ld: command not found`、`dc: command not found`、`gcc can't be found`

**修复**：

```Bash
sudo apt install -y \
    gcc-9 g++-9 build-essential binutils make \
    gdb bc csh ksh dc

sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-9 90
sudo update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-9 90
```

### 问题 7：NUMA 库缺失（VCS FGP 模式）

**现象**：`Numa library is not available. Please check if the file /usr/lib64/libnuma.so is accessible`

**修复**：

```Bash
sudo apt install -y libnuma-dev libnuma1
```

### 问题 8：FlexLM 无法绑定 TCP 端口

**现象**：`(lmgrd) Failed to open the TCP port number in the license`

**原因**：distrobox 容器的网络命名空间限制，`lmgrd` 无法在容器内正常绑定端口。

**解决**：在**宿主机**上运行 `lmgrd`，容器内通过环境变量指向宿主机的 license server：

```Bash
export LM_LICENSE_FILE=27000@localhost
```

### 问题 9：Verdi 缺失系统库

**现象**：Verdi 启动时依次报 `libsmime3.so`、`libXtst.so.6`、`libxslt.so.1` 找不到

**修复**：

```Bash
sudo apt install -y libnss3 libxtst6 libxslt1-dev
```

### 问题 10：Verdi 自带的 Qt5 / TBB / RtxStable 库找不到

**现象**：`ldd` 显示大量 `libQt5*.so.5 => not found`、`libtbb.so.12 => not found`、`libRtxStable.so => not found`

**原因**：这些库是 Verdi 自带的，不需要从系统安装，只需设置 `LD_LIBRARY_PATH`。

**相关路径**（均在 Verdi 安装目录下）：

<table>
<thead>
  <tr>
    <th>
      库
    </th>
    
    <th>
      路径
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      Qt5
    </td>
    
    <td>
      verdi/W-2024.09-SP1/platform/linux64/lib/Qt5/lib
    </td>
  </tr>
  
  <tr>
    <td>
      TBB
    </td>
    
    <td>
      verdi/W-2024.09-SP1/platform/linux64/lib/tbb
    </td>
  </tr>
  
  <tr>
    <td>
      RtxStable
    </td>
    
    <td>
      verdi/W-2024.09-SP1/platform/linux64/lib/zebu
    </td>
  </tr>
</tbody>
</table>

**修复**：在环境脚本中添加对应的 `LD_LIBRARY_PATH`（见下方[环境脚本](#%E7%8E%AF%E5%A2%83%E8%84%9A%E6%9C%AC-env_synopsys_2024sh)）。

### 问题 11：容器内 X11 转发认证失败

**现象**：从 Mac 通过 SSH 连到宿主机（soleilUbuntu），再进入容器后，`xeyes`、`design_vision` 等 GUI 程序起不来：

```Plain
X11 connection rejected because of wrong authentication.
Error: Can't open display: localhost:10.0
```

而直接在宿主机上，X11 转发是正常的。

**原因**：

- **hostname 不匹配**：SSH X11 转发生成的 xauth cookie 注册在宿主机 hostname `soleilUbuntu/unix:10` 下，而容器的 hostname 是 `synopsys-focal.soleilUbuntu`。X Server 按 hostname 找 cookie，找不到就拒绝连接。
- **XAUTHORITY 为空**：容器内没有这个环境变量，xauth 定位不到 `~/.Xauthority`，无法正常读写 cookie。
- **cookie 匹配歧义**：`.Xauthority` 里同时有宿主机和容器的记录。脚本匹配不精确时会拿到容器自己的旧 cookie（已失效），而不是宿主机当前会话的有效 cookie。

**手动修复**（容器内依次执行）：

```Bash
# 1. 指定 XAUTHORITY 路径
export XAUTHORITY=/home/soleil/.Xauthority

# 2. 从宿主机 xauth list 中找到当前 DISPLAY 对应的 cookie
xauth -f /home/soleil/.Xauthority list | grep "^soleilUbuntu/unix:"

# 3. 添加 cookie 到当前 DISPLAY
xauth -f /home/soleil/.Xauthority add localhost:10.0 MIT-MAGIC-COOKIE-1 <cookie值>

# 4. 验证
xeyes
```

**自动化修复**：每次 SSH 重连后 cookie 都会变，手动加很麻烦。把下面这段追加到容器的 `~/.bashrc`，每次进入 Distrobox 时就会自动同步 cookie：

```Bash
cat >> ~/.bashrc << 'XEOF'
# --- X11 auto fix for Distrobox ---
export XAUTHORITY=/home/soleil/.Xauthority
if [ -n "$DISPLAY" ]; then
    DISPLAY_NUM=$(echo "$DISPLAY" | sed 's/.*:\([0-9]*\).*/\1/')
    COOKIE=$(xauth -f /home/soleil/.Xauthority list 2>/dev/null | grep "^soleilUbuntu/unix:${DISPLAY_NUM} " | head -1 | awk '{print $3}')
    if [ -n "$COOKIE" ]; then
        xauth -f /home/soleil/.Xauthority add "$DISPLAY" MIT-MAGIC-COOKIE-1 "$COOKIE" 2>/dev/null
    fi
fi
XEOF
```

脚本做了四件事：

1. 设置 `XAUTHORITY` 指向共享 home 目录下的 `.Xauthority` 文件
2. 从 `$DISPLAY`（如 `localhost:10.0`）中提取 display 编号（如 `10`）
3. 用 `^soleilUbuntu/unix:` 精确匹配宿主机的 cookie，避免误取容器自身的旧记录
4. 把宿主机的有效 cookie 添加到容器当前的 `$DISPLAY` 地址上

注意事项：

- 如果宿主机 hostname 不是 `soleilUbuntu`，需要把脚本中的 `soleilUbuntu` 替换为实际 hostname
- 如果使用多个 Distrobox 容器，每个容器都需要添加此脚本
- 若 SSH 配置变更导致 DISPLAY 编号改变，脚本会自动适配，无需修改

## 环境脚本 env_synopsys_2024.sh

```Bash
#!/usr/bin/env bash
# Synopsys 2024 environment setup
# Usage: source ~/synopsys/env_synopsys_2024.sh

########################################
# 1) 安装根目录
########################################
INSTALL_ROOT="/home/soleil/synopsys"

########################################
# 2) License
########################################
export SNPSLMD_LICENSE_FILE="27000@localhost.localdomain"
export LM_LICENSE_FILE="${INSTALL_ROOT}/scl/2024.06/admin/license/Synopsys.dat"

########################################
# 3) SCL
########################################
export SCL_HOME="${INSTALL_ROOT}/scl/2024.06"

########################################
# 4) VCS
########################################
export VCS_HOME="${INSTALL_ROOT}/vcs/W-2024.09-SP1"
export VCS_CC=gcc-9
export VCS_CXX=g++-9
export VCS_MODE_FLAG=64
export VCS_ARCH_OVERRIDE="linux"

########################################
# 5) Verdi
########################################
export VERDI_HOME="${INSTALL_ROOT}/verdi/W-2024.09-SP1"

########################################
# 6) Design Compiler (syn)
########################################
export DC_HOME="${INSTALL_ROOT}/syn/T-2022.03-SP2"

########################################
# 7) PATH
########################################
export PATH="${SCL_HOME}/linux64/bin:${VCS_HOME}/bin:${VERDI_HOME}/bin:${DC_HOME}/bin:${PATH}"

########################################
# 8) LD_LIBRARY_PATH（自动检查目录是否存在）
########################################
_LD_DIRS=(
    "${VERDI_HOME}/share/PLI/VCS/linux64"
    "${VERDI_HOME}/platform/linux64/lib/Qt5/lib"
    "${VERDI_HOME}/platform/linux64/lib/tbb"
    "${VERDI_HOME}/platform/linux64/lib/zebu"
)
for _d in "${_LD_DIRS[@]}"; do
    [ -d "$_d" ] && export LD_LIBRARY_PATH="${_d}:${LD_LIBRARY_PATH:-}"
done
unset _LD_DIRS _d

########################################
# 9) 终端兼容
########################################
export TERM=xterm

########################################
# 10) 快捷命令
########################################
alias lmg="lmgrd -c '${INSTALL_ROOT}/scl/2024.06/admin/license/Synopsys.dat'"
```

## 一键安装所有容器内依赖

上面各个问题里装的包合在一起，新开一个容器时直接跑这一段：

```Bash
sudo apt update && sudo apt install -y \
    gcc-9 g++-9 build-essential binutils make gdb bc csh ksh dc \
    libnuma-dev libnuma1 libnss3 libxtst6 libxslt1-dev libtbb-dev \
    libxcb-xinerama0 libxcb-icccm4 libxcb-image0 libxcb-keysyms1 \
    libxcb-randr0 libxcb-render-util0 libxcb-shape0 libxcb-xfixes0 \
    libxcb-xkb1 libxkbcommon-x11-0 libfontconfig1 libxrender1 \
    libxi6 libxext6 libx11-xcb1 libgl1-mesa-glx \
    tcsh perl python3 gawk libstdc++6 zlib1g libgcc-s1 \
    libncurses5 libtinfo5 libx11-6 libxt6 libxft2 \
    libxmu6 libsm6 libice6 libfreetype6 libglib2.0-0 libpng16-16 \
    xauth x11-apps fonts-dejavu-core

sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-9 90
sudo update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-9 90
sudo mkdir -p /usr/tmp && sudo touch /usr/tmp/.flexlm
```

## 依赖检查

经 `ldd ... | grep "not found"` 验证，以下工具在完成上述配置后**依赖全部满足**：

- `vcs`（VCS W-2024.09-SP1）
- `icc2_shell`（ICC2 W-2024.09）
- `dc_shell` / `design_vision`（Design Compiler T-2022.03-SP2）
- `verdi`（Verdi W-2024.09-SP1）

## 最终效果

最后拿神的大作业来跑了一下，效果还可以 😃

![VCS 仿真：FPU 除法测试全部通过](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/(null)-20260909162653990.(null))

![Design Vision 图形界面正常启动](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/(null)-20260909162654252.(null))
