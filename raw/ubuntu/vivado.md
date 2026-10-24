# Ubuntu 24.04 安装 Vivado 2020.1

> Vivado 2020.1 在新版 Ubuntu 上的安装方法，以及连不上开发板的驱动问题

Vivado 2020.1 的图形安装器在 Ubuntu 24.04 上会直接崩掉，报 `no splash screen available`。绕过办法是先用 `./xsetup -b ConfigGen` 生成配置文件，再用 `--batch` 参数走命令行安装，下面两篇讲得很清楚：

<link-preview cover="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/image-20260909172121848.png" description="安装器报 no splash screen available 时，用 xsetup -b ConfigGen 生成 install_config.txt，再用 --batch 模式安装。" link="https://blog.csdn.net/haoxingheng/article/details/108938279" title="Vivado Vitis 2020.1 无法在 Ubuntu 部分版本上安装的解决办法">



</link-preview>

<link-preview cover="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/illustration-of-a-laptop-running-arch-linux-with-the-arch-linux-logo-beside-it.jpg" description="Arch 并不在 Vivado 官方支持列表里，但稍微折腾一下大部分功能都能用；涵盖安装、驱动和常见故障排查。" link="https://wiki.archlinux.org/title/Xilinx_Vivado" title="Xilinx Vivado - ArchWiki">



</link-preview>

## 找不到开发板

Linux 版安装器不会自动装 JTAG 线缆驱动，所以装完 Vivado 之后板子插上也识别不到。需要手动跑一次安装目录里的 `install_drivers` 脚本：

```Bash
cd <Vivado 安装目录>/data/xicom/cable_drivers/lin64/install_script/install_drivers/
sudo ./install_drivers
```

<link-preview cover="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/image-20260909172229103.png" description="不是 VMware USB 兼容性的问题，而是 Linux 版 Vivado 没装线缆驱动，跑一遍 install_drivers 就好。" link="https://blog.csdn.net/weixin_58789603/article/details/146990388" title="Linux 中 Vivado 无法连接开发板解决办法">



</link-preview>

Xilinx 官方文档 UG973 里对这一步的说明：

![UG973 中关于安装线缆驱动的说明](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/(null)-20260909165129529.(null))
