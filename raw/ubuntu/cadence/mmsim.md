# 在 Ubuntu 24.04 上安装 Cadence MMSIM 15.1 的兼容性问题

> MMSIM 15.1 在新系统上的踩坑记录

## 问题描述

在 Ubuntu 24.04 LTS 上运行 Cadence Spectre (MMSIM 15.1, 2015年发布) 进行电路仿真时，Verilog-A 模型（`prog_delay.va` 和 `bsimcmg_FE.va`）编译失败，仿真无法完成。

### 错误链条

仿真过程中依次出现以下错误，形成连锁反应：

1. **VACOMP-2397**：pipe build 编译方式失败，回退到普通文件编译
2. **VACOMP-1008**：ahdlcmi 模块库编译失败（`prog_delay` 和 `bsimcmg_FE` 均失败）
3. **SFE-91**：模型实例无法 elaborate，仿真应终止
4. **SFE-46**：FeFET 被识别为 0 端口（模型未编译成功的连锁后果，并非网表错误）

### 根本原因

MMSIM 15.1 发布于 2015 年，其内部工具链（GCC 4.8、旧版链接器 `ld`）与 Ubuntu 24.04 的现代 glibc (2.39) 完全不兼容。具体表现为两个层面的不兼容。

## 解决方案：Distrobox + Ubuntu 20.04 容器

使用 Distrobox 创建一个 Ubuntu 20.04 (Focal) 容器来运行 Spectre，既能利用旧系统的兼容性，又能无缝访问宿主机文件。

### 第一步：创建并进入容器

```Bash
distrobox create --name synopsys-focal --image ubuntu:20.04
distrobox enter synopsys-focal
```

Distrobox 会自动挂载宿主机的 home 目录，Cadence 安装路径直接可用。

### 第二步：安装 32 位支持库

Cadence 的部分启动工具（如 `cds_root`）是 32 位 ELF 二进制文件，需要 32 位运行时库：

```Bash
sudo dpkg --add-architecture i386
sudo apt update
sudo apt install -y libc6:i386 libstdc++6:i386
```

**排查过程**：`cds_root` 是 32 位程序，需要 `/lib/ld-linux.so.2`（32 位动态链接器）。在缺少 32 位支持的情况下，`ldd` 会报 "not a dynamic executable"，shell 会报 "not found"（即使文件实际存在）。

### 第三步：修复 glibc 头文件路径

MMSIM 自带的 GCC 4.8 编译 Verilog-A 时报错：

```Plain
fatal error: bits/libc-header-start.h: No such file or directory
```

这是因为 Ubuntu 的 multiarch 布局将头文件放在 `/usr/include/x86_64-linux-gnu/bits/`，而 GCC 4.8 期望在 `/usr/include/bits/`。创建符号链接解决：

```Bash
sudo ln -s /usr/include/x86_64-linux-gnu/bits /usr/include/bits
sudo ln -s /usr/include/x86_64-linux-gnu/gnu /usr/include/gnu
sudo ln -s /usr/include/x86_64-linux-gnu/sys /usr/include/sys
sudo ln -s /usr/include/x86_64-linux-gnu/asm /usr/include/asm
```

### 第四步：替换 Cadence 自带的旧版链接器

头文件问题解决后，C 编译通过，但链接阶段失败：

```Plain
ld: /lib/x86_64-linux-gnu/crti.o: unrecognized relocation (0x2a) in section `.init'
ld: final link failed: Bad value
```

原因是 Cadence 自带的 GCC 4.8 内置了旧版 `ld`，不认识 Ubuntu 20.04 glibc 中的新 relocation 类型。将其替换为系统链接器：

```Bash
cd /home/soleil/cadence/installs/MMSIM151/tools.lnx86/cdsgcc/gcc/4.8/install/bin/
mv ld ld.bak      # 备份原始文件，方便回退
ln -s /usr/bin/ld ld
```

### 第五步：清除缓存并重新仿真

```Bash
rm -rf dummy_64x64.ahdlSimDB
spectremdl dummy_64x64.mdl +aps
```

仿真成功完成。

## 问题总结

## 注意事项

- 替换链接器时原文件已备份为 `ld.bak`，如需回退执行 `mv ld.bak ld` 即可。
- 由于 Cadence 安装在宿主机 home 目录下，链接器的替换对宿主机也生效，但宿主机（Ubuntu 24.04）本身也无法正常运行 MMSIM 15.1，因此没有副作用。
- 如果未来遇到其他 Cadence 工具的类似问题，可用相同思路排查：查看 `ahdlcmi.out` 日志 → 定位编译/链接错误 → 修复对应的兼容性问题。
