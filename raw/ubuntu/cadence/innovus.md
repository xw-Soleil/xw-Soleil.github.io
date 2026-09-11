# Innovus安装

> Innovus 的安装流程

> 原文：[https://lsyic.top/article/file-1](https://lsyic.top/article/file-1) 发布时间：2024-11-17

## 0.下载文件

通过网盘分享的文件：Innovus安装 链接: [https://pan.baidu.com/s/1EhfuQhX9MOyYx0OFkf-sMg?pwd=yeb6](https://pan.baidu.com/s/1EhfuQhX9MOyYx0OFkf-sMg?pwd=yeb6) 提取码: yeb6

将下载的文件放入虚拟机共享文件夹

## 1.解压压缩包

将INNOVUS相关的压缩包拷贝出共享文件夹，全选然后解压（在虚拟机内进行）

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/(null)-20260909162540074.(null))

## 2.进入安装路径

进入 /opt/Cadence 路径

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/(null)-20260909162540406.(null))

## 3.切换root账户

打开 Terminal，切换为 root 账户

输入命令 `su root`，然后输入密码：`123123`

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/(null)-20260909162540730.(null))

## 4.打开安装软件

进入 `/opt/Cdence/IScape/iscape.04.23-s012/bin` 路径

输入 `./iscape.sh` 打开安装软件

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/(null)-20260909162541110.(null))

## 5.执行安装

选择 local directory Media install

在下方选择第 1 步中解压出的路径，注意填到 `/CDROM1` 这一级

点击 Continue

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/(null)-20260909162541399.(null))

选中 INNOVUDS……，点击 Next

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/(null)-20260909162541688.(null))

选择安装路径，填 `/opt/Cdence/INNOVUS201`，点击 Start 开始安装

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/(null)-20260909162541966.(null))

等待安装结束，弹出的窗口选输入回车，然后输入 n，窗口会自动退出。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/(null)-20260909162542323.(null))

关闭获取 root 权限的 Terminal。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/(null)-20260909162542588.(null))

## 6.完善安装

将下载的 ocad 文件夹放入 `/opt` 路径下

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/(null)-20260909162542977.(null))

在该路径下打开 Terminal，执行命令：

sudo ./ocad/bin/1patch -ecc ./Cdence/INNOVUS201/

提示输入密码：`123321`

等待程序结束，最后出现 error 可以不用管。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/(null)-20260909162543329.(null))

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/(null)-20260909162543675.(null))

将下载的 cadence.dat 文件放入 `/opt/Cdence/license` 路径下

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/(null)-20260909162543965.(null))

## 7.修改环境变量

重新打开一个 Terminal（自动进入用户账户而非 root 账户）

打开 `~/.bashrc`

将 Cadence 后的相关内容改成如下语句：

```bash
export Cadence_Dir=/opt/Cdence
export CDS_LIC_FILE=$Cadence_Dir/license/cadence.dat
export LM_LICENSE_FILE=$Cadence_Dir/license/cadence.dat
export LD_LIBRARY_PATH=$$LD_LIBRARY_PATH$$INNOVUS_HOME/tools.lnx86/lib
```

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/(null)-20260909162544256.(null))

在 MMSIM 相关内容后添加如下内容：

```bash
export INNOVUS_HOME=$Cadence_Dir/INNOVUS201
export OA_HOME=$INNOVUS_HOME/oa_v22.60.028
export PATH=$$INNOVUS_HOME/bin$$PATH
export PATH=$$INNOVUS_HOME/tools/bin$$PATH
export PATH=$$INNOVUS_HOME/tools/dfII/bin$$PATH
```

保存退出

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/(null)-20260909162544604.(null))

## 8.打开软件

打开 Terminal，输入命令：`innovus` 打开软件

如果弹出如下软件窗口，同时 Terminal 中不报任何 error，则安装成功。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/(null)-20260909162544907.(null))
