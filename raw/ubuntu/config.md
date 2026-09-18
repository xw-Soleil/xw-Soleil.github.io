# ubuntu 系统配置

> 装好系统之后的各种配置

## 中文字体支持

首先安装东风破（plum）：

```Bash
curl -fsSL https://raw.githubusercontent.com/rime/plum/master/rime-install | bash
```

然后安装 rime：

```Bash
sudo apt-get install ibus-rime
```

### 参考资料

- [ubuntu-24.04 安装配置 rime（中州韵）输入法 - CSDN 博客](https://blog.csdn.net/2301_76167370/article/details/148610342)

## 命令行美化

### 字体安装

```Bash
# linux version
sudo apt update
sudo apt install fonts-cascadia-code
```

### Powerlevel10k 重新运行配置向导

```Bash
p10k configure
```

### Starship：命令提示 + Git 符号显示

```Bash
# 使用 gnu 版本而不是 musl 版本
sudo wget -O /tmp/starship.tar.gz https://github.com/starship/starship/releases/latest/download/starship-x86_64-unknown-linux-gnu.tar.gz

# 解压
cd /tmp
sudo tar -xzf starship.tar.gz

# 移动到系统路径
sudo mv starship /usr/local/bin/

# 设置执行权限
sudo chmod +x /usr/local/bin/starship

# 清理
sudo rm starship.tar.gz

# 验证安装
starship --version

echo 'eval "$(starship init zsh)"' >> ~/.zshrc
source ~/.zshrc
```

### 参考资料

- [sorrycc 的 Mac 配置](https://sorrycc.com/mac)
- [zsh 安装与配置，使用 oh-my-zsh 美化终端](https://www.haoyep.com/posts/zsh-config-oh-my-zsh/)

## Ubuntu/Windows 双启动时间冲突

### 问题原因

- **Windows**：硬件时钟存储本地时间
- **Ubuntu**：硬件时钟存储 UTC 时间
- **结果**：切换系统时出现 8 小时时差

### Ubuntu 22.04 及以下解决方案

1. 安装时间同步工具```Bash
sudo apt install ntpdate
```
2. 同步时间```Bash
sudo ntpdate time.windows.com
```
3. 设置硬件时钟为本地时间```Bash
sudo hwclock --localtime --systohc
```
4. 配置系统使用本地时区 RTC```Bash
sudo timedatectl set-local-rtc 1 --adjust-system-clock
```

### 验证结果

```Bash
timedatectl status
```

确认显示：`RTC in local TZ: yes`

### 注意事项

- 系统会显示警告信息，这是正常的
- 重启后分别检查 Windows 和 Ubuntu 时间是否一致
- 警告不影响功能，可以忽略

## SSH 双系统冲突：修改 Ubuntu SSH 端口号

由于我现在使用网线进行网络连接，Windows 和 Ubuntu 共用一个 IP 地址，导致 SSH fingerprint 变更，在 SSH 连接的时候就会有麻烦出现，所以这里就把 Ubuntu 的端口号进行更改，流程如下。

### Ubuntu 24.04

Ubuntu 24.04 比较特殊，请参见以下文章：

- [Ubuntu 24.04.2 修改 ssh 端口 - 博客园](https://www.cnblogs.com/xiao987334176/p/18806530)

### 其他版本的 Ubuntu

修改 Ubuntu SSH 端口到 2222：

1. **编辑 SSH 配置**```Bash
sudo nano /etc/ssh/sshd_config
```
2. **修改端口行**```Bash
Port 2222
```
3. **重启 SSH 服务**```Bash
sudo systemctl restart sshd
```
4. **更新防火墙**```Bash
sudo ufw allow 2222/tcp
sudo ufw delete allow 22/tcp
```
5. **连接测试**```Bash
ssh -p 2222 username@10.112.100.172
```

### 在 VSCode 中修改配置

```Plain
Host soleilUbuntu
  HostName 10.112.100.172
  User soleil
  Port 2222
```

## 屏幕亮度调节（显示屏）

使用 GNOME Shell 扩展 [Soft Brightness Plus](https://extensions.gnome.org/extension/5943/soft-brightness-plus/) 来调节亮度，安装步骤如下。

### 安装步骤

#### 1. 先安装浏览器扩展

点击页面顶部蓝色提示框中的 **"Click here to install browser extension"** 链接，安装浏览器集成插件。

#### 2. 安装本地连接器（Native Host Connector）

根据你的 Linux 发行版，安装本地主机消息应用：

**Ubuntu/Debian:**

```Bash
sudo apt install chrome-gnome-shell
```

#### 3. 查看你的 GNOME Shell 版本

在终端运行：

```Bash
gnome-shell --version
```

#### 4. 选择对应版本并安装

- 点击页面上的 **"Shell version..."** 下拉菜单
- 选择与你的 GNOME Shell 版本匹配的版本
- 点击蓝色的 **"Install"** 按钮
- 在弹出的对话框中确认安装

#### 5. 管理扩展

安装完成后，你可以通过以下方式管理扩展：

- 访问网站顶部的 **"Installed extensions"** 页面
- 或使用 GNOME Extensions 应用（如果已安装）

完成这些步骤后，Soft Brightness 扩展就应该可以正常工作了！

### 参考资料

- [Soft Brightness Plus - GNOME Shell Extensions](https://extensions.gnome.org/extension/5943/soft-brightness-plus/)
