# Ubuntu24.04安装Cadence 系列软件

> Cadence Virtuoso 617 的安装流程

## 参考文章

<link-preview cover="https://picx.zhimg.com/v2-e9ff4b11993cc5f0469b2ad0ec8d70f3_1440w.png" description="最完整的一篇，从依赖库到 license 全流程；作者也提醒 Ubuntu 兼容性一般，正式环境建议用 CentOS / RHEL" link="https://zhuanlan.zhihu.com/p/659144314" title="Ubuntu22 安装 IC618、spectre21、innovus211、calibre2022">



</link-preview>

<link-preview cover="https://oscimg.oschina.net/oscnet/up-0e7db6d5b236f050933fc08787034983d20.png" description="早期的 IC617 安装记录，InstallScape 的用法看这篇" link="https://my.oschina.net/propagator/blog/3166272" title="ubuntu18.04 安装 cadence virtuoso">



</link-preview>

<link-preview cover="https://pica.zhimg.com/v2-daaaa1f9b9c35a23f6450efd4efd2214_1440w.jpg" description="和本文一样的 24.04 真机环境，附工艺库导入" link="https://zhuanlan.zhihu.com/p/1889032029292700153" title="Ubuntu24.04 安装 Cadence Virtuoso617 + Tsmc18rf 工艺库实录">



</link-preview>

<link-preview cover="https://i-blog.csdnimg.cn/blog_migrate/c3a36fd6adc6ed16af8900243c15beaf.png" description="安装包解压、InstallScape 找不到 release 等细节" link="https://blog.csdn.net/yilan0926/article/details/134293421" title="Ubuntu22.04 下载 IC617 等细节补充">



</link-preview>

<link-preview cover="https://i-blog.csdnimg.cn/blog_migrate/cover/451bd3cb0200ebe9bda02f699c8b39d1.png" description="CXXABI_1.3.8、libGLU.so.1 缺失和 dlopen libdl.so 失败的解决" link="https://blog.csdn.net/qq_52159533/article/details/130780399" title="cadence ic617 virtuoso 安装时遇见的一些问题">



</link-preview>

## 依赖安装

由于一般来说cadence都是安装在centos系统上，在ubuntu24.04这个过新的版本上支持并不好，所以进行了一系列依赖与兼容库的安装

### 依赖与兼容库

```Bash
# 安装基本依赖
sudo apt-get install ksh csh xterm libncurses-dev

# 安装32位兼容库
sudo apt install \
  libncurses6:i386 libncursesw6:i386 \
  lib32z1 libstdc++6:i386 libxrender1:i386 libxtst6:i386 libxi6:i386
```

### 创建软链接

由于 virtuoso 支持的 redhat enterprice linux 和 ubuntu 还是有些不同，因此还需要做一些修改才能顺利安装。首先创建如下软链接

```Bash
sudo ln -s /usr/bin/mawk /bin/awk
sudo ln -s /usr/bin/basename /bin/basename
sudo ln -s /lib/x86_64-linux-gnu/libncursesw.so.6.4 /lib/libtermcap.so.2
```

然后在 /etc 文件夹中新增文件 redhat-release，其内容为如下一句话

这是为了让软件认为自己运行在 red hat enterprice linux 上。注意在 /etc 中创建文件需要 root 权限，因此完成后最好把权限修改为 644

```Bash
echo "Red Hat Enterprise Linux release 6.12" | sudo tee /etc/redhat-release
sudo chmod 644 /etc/redhat-release
```

接下来就可以开始安装了。首先下载安装文件，所有安装文件可在如下地址下载

[https://pan.baidu.com/s/1Pq_ofvvDoV8u5jz1wZyQIg](https://pan.baidu.com/s/1Pq_ofvvDoV8u5jz1wZyQIg)

提取码为：eern

注意下载后的文件是按安装在虚拟机上准备的，因此有一些文件是没必要的，实际上用得到的只有从 03 到 10。此外，文件的排列顺序也就是实际的安装顺序，在安装前要对所有文件进行解压。因为 04 的两个压缩包是分卷压缩的，因此解压需要使用如下方法

```Bash
cat 04.IC06.17.700_Base.zip* > 04.IC06.17.700_Base.zip
unzip 04.IC06.17.700_Base.zip
```

即先将两个分卷合并，然后再解压，否则可能遇到无法解压的情况。

进入解压后的 03.InstallScape，可看到如下压缩文件，

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/(null)-20260909162321400.(null))

在此目录下执行如下语句即可开始安装。注意网上的帖子均安装在 /opt 目录下，因此需要 root 权限创建文件夹并修改权限。此处我直接装在当前用户目录下，故不需要 root 权限，而且以后的操作也都不再需要 root 权限。

```Bash
iscape/bin/iscape.sh
```

选择 IC617 解压后所在目录，直接点击 continue

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/(null)-20260909162321786.(null))

选择要安装的程序，点击 next

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/(null)-20260909162322172.(null))

在安装过程中，配置环节会跳出窗口进行配置，可以按如下方式处理

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/(null)-20260909162322447.(null))

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/(null)-20260909162322810.(null))

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/(null)-20260909162323141.(null))

安装完成后，点击 done，回到主界面，此时可以点击 cancel，重新选择软件包路径，继续安装 MMSIM

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/(null)-20260909162323445.(null))

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/(null)-20260909162323822.(null))

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/(null)-20260909162324094.(null))

接下来的安装步骤和之前安装 IC617 几乎完全一样。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/(null)-20260909162324705.(null))

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/(null)-20260909162325271.(null))

同样在配置时会跳出窗口进行配置

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/(null)-20260909162325577.(null))

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/(null)-20260909162325863.(null))

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/(null)-20260909162326295.(null))

至此安装完成，可如下查看当前系统安装的软件，然后退出 iscape。此时，IC617 和 MMSIM 都被安装到用户目录 cadence/installs 目录下。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/(null)-20260909162326840.(null))

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/(null)-20260909162327182.(null))

接下来安装 calibre，可以看到，解压后的 calibre 是个单独的 exe 文件

由于运行该文件会直接把 calibre 安装在当前目录下，因此在 cadence 目录下创建一个 calibre2015 目录，将该 exe 文件复制或剪切进去。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/(null)-20260909162327475.(null))

接下来进入该目录下，运行如下指令

```Bash
chmod u+x aoi_cal_2015.2_36.27_mib.exe
./aoi_cal_2015.2_36.27_mib.exe
```

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/(null)-20260909162327902.(null))

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/(null)-20260909162328164.(null))

如果出现下面的错误提示，mgc_install: not found，我也遇到这个错误并困惑了好久，但是我最后的解决办法就是不断反复的运行这个exe指令，最后就成功了

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/(null)-20260909162328508.(null))

至此 IC617, MMSIM 和 Calibre2015 均安装完成，接下来分别为其安装补丁。

## 补丁安装

### IC617 & MMSIM 补丁

先进入 07.cadence_patch 解压后的文件夹，如下所示

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/(null)-20260909162328844.(null))

执行如下指令打补丁

```Bash
chmod u+x cadence.pat cadence_patch.sh sfk
./cadence_patch.sh ~/cadence/installs/IC617
./cadence_patch.sh ~/cadence/installs/MMSIM151
```

第一句为几个文件增加可执行权限，后面两句分别为 IC617 和 MMSIM 打补丁，注意./cadence_patch.sh 后面是 IC617  和 MMSIM  的安装目录，不同的用户安装目录可能不同，要根据自己的情况修改。另外就是执行完后，可能会显示有几个错误（errors），不用理会，这是由于  IC617 目录中有链接到系统文件，打补丁时没权限所致，如果看着别扭，可以用 sudo 执行即可。

### calibre补丁

为 calibre 打补丁的过程类似，解压后的文件如下所示

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/(null)-20260909162329130.(null))

将这几个文件复制到 calibre 安装目录下（此处为  /home/praise/cadence/calibre2015），然后进入该目录执行如下指令对 calibre 打补丁（注意 calibre  的补丁必须复制到安装目录下运行，不能像 IC617 和 MMSIM 那样在解压后的目录下也可以直接运行）

```Bash
chmod u+x patch_calibre sfk
./patch_calibre aoi_cal_2015.2_36.27
```

同样可能出现 errors，但此处是由于无法对二进制文件（sfk 和之前的安装文件 aoi_cal_2015.2_36.27_mib.exe）进行读写所致，同样不用理会。

注意这里会出现不兼容问题

#### 给[Calibre](https://zhida.zhihu.com/search?content_id=255708613&content_type=Article&match_order=1&q=Calibre&zd_token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJ6aGlkYV9zZXJ2ZXIiLCJleHAiOjE3NTkwMzg0MDIsInEiOiJDYWxpYnJlIiwiemhpZGFfc291cmNlIjoiZW50aXR5IiwiY29udGVudF9pZCI6MjU1NzA4NjEzLCJjb250ZW50X3R5cGUiOiJBcnRpY2xlIiwibWF0Y2hfb3JkZXIiOjEsInpkX3Rva2VuIjpudWxsfQ.o408nlNGzWL80luMpdrG_R2H7rikLQDeFlS__pGmxHY&zhida_source=entity)打补丁的时候报错

##### 问题分析

```Bash
(base) wizard@wizard:~/cadence/calibre2015$ ./patch_calibre aoi_cal_2015.2_36.27
./sfk: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
```

`sfk` 这个二进制程序依赖一个非常老的 C++ 运行库 **libstdc++.so.5，**然后我运行

```Bash
sudo apt install libstdc++5
```

然而在注意到输出是

```Bash
Unpacking libstdc++5:amd64 (1:3.3.6-30ubuntu2) ...
Setting up libstdc++5:amd64 (1:3.3.6-30ubuntu2) ...
Processing triggers for libc-bin (2.39-0ubuntu8.4) ...
```

已经安装了 64‑bit 版本的 **libstdc++5**，但 `./sfk` 实际上是一个 **32‑bit** 可执行文件（可以通过file ./sfk确认），所以它在找不到 32‑bit 的 `libstdc++.so.5`

##### 解决办法

解决办法如下

```Bash
sudo dpkg --add-architecture i386
sudo apt update
sudo apt install libstdc++5:i386
```

### 安装license

接下来安装 license 文件，解压后的 cadence_license 文件夹如下

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/(null)-20260909162329468.(null))

直接将其中的 license.dat 文件复制到 IC617 的 license 目录下即可（此处为 /home/praise/cadence/installs/IC617/share/license）

同样的，将解压后的 calibre_license 目录下 license.dat 文件复制到 calibre 的 license  目录下（此处为  /home/praise/cadence/calibre2015/aoi_cal_2015.2_36.7/shared/license），需要注意的是，此时  license 目录不存在，需要自己建一个。

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/(null)-20260909162329806.(null))

打开该 license.dat 文件，将其中的 HOSTID=000c294756b0 替换为自己的 mac 地址。

至此，就算安装完成了，只需要设置一些环境变量即可运行了。但为了不污染系统本来的环境变量，采用脚本的方式来执行。将 09.bashrc 解压后文件夹中的 bashrc 文件复制到合适的位置

由于我使用的是zsh或者bash，cadence的bashrc文件会不兼容，需要把含有`$prompt`的这几行注释

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/(null)-20260909162330169.(null))

然后进行相应改动

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/(null)-20260909162330563.(null))

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/(null)-20260909162330870.(null))

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/(null)-20260909162331293.(null))

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/(null)-20260909162331713.(null))

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/(null)-20260909162332087.(null))

注意上面倒数第二个图中（417,418 行）的 praise-VirtualBox 是主机名，可用 hostname  命令查看。此外可以看出，该脚本实际上为多个软件设置了环境变量，其中有一些用不到，另外一些虽然将来会用到，但现在暂时先不理会，在后续文章中再处理。

## 兼容问题

上述安装好之后启动spectre是正常的，但是viva和virtuoso是不正常的，分别报错

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/(null)-20260909162332407.(null))

### 修复virtuoso

**重命名Cadence自带的libstdc++**

```Bash
cd ~/cadence/installs/IC617/tools/lib/64bit/
mv libstdc++.so.6 libstdc++.so.6.bak
```

此时会报错

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/(null)-20260909162332690.(null))

接着，运行

```Bash
sudo ln -s /usr/lib/x86_64-linux-gnu/libdl.so.2 /usr/lib/libdl.so
```

解决libdl.so问题

#### 报错

实际上对于打开版图还是会有报错：

`libXp.so.6` 属于 **libxp6（X11 Print Extension 库）**，这个库已经从 Ubuntu 官方仓库里移除了；很多旧版 Cadence / Mentor 都会依赖它

在 **24.04** 里：

- `multiarch-support` 已经从系统里删掉，不再提供
- 老的 `libxp6_1.0.2-2_amd64.deb` 会声明 **PreDepends: multiarch-support**，所以直接装会报依赖错误

最终采取了如下解决办法

有人专门给 **24.04 (noble)** 打好了新版的 `libxp` 包（包含 `libXp.so.6`），放在 PPA 里，明确支持 noble。[Launchpad](https://launchpad.net/~zeehio/%2Barchive/ubuntu/libxp/%2Bpackages)

#### 添加 libxp6 的 PPA

```Plain
sudo add-apt-repository ppa:zeehio/libxp
sudo apt update
sudo apt install libxp6
```

这个 PPA 里有 `libxp` 和它的依赖 `x11proto-print` 的 24.04 版本，不再依赖 `multiarch-support`。[Launchpad+1](https://launchpad.net/~zeehio/%2Barchive/ubuntu/libxp/%2Bpackages)

#### 确认 `libXp.so.6` 已存在

```text
ls -l /usr/lib/x86_64-linux-gnu/libXp.so.6
```

看到一个指向 `libXp.so.6.2.0` 之类的链接就 OK 了。

再检查一下 Cadence 的那个可执行文件是否能找到它：

```Plain
ldd /home/soleil/cadence/installs/IC617/tools.lnx86/dfII/bin/64bit/strmin | grep libXp
```

正常应该输出类似：

```text
libXp.so.6 => /usr/lib/x86_64-linux-gnu/libXp.so.6 (0x....)
```

然后重新在 Virtuoso 里做一次 GDS 导入，看 `strmin` 的 error 是否消失。

### 修复viva

viva报错找不到库，就进行安装

```Bash
wget http://ftp.de.debian.org/debian/pool/main/g/glibc/multiarch-support_2.28-10+deb10u1_amd64.deb
sudo dpkg -i multiarch-support_2.28-10+deb10u1_amd64.deb
wget launchpadlibrarian.net/183708483/libxp6_1.0.2-2_amd64.deb
sudo dpkg -i libxp6_1.0.2-2_amd64.deb
```

也会报错说`multiarch-support_2.28-10+deb10u1_amd64.deb`找不到，找不到就强行安装

```Bash
sudo dpkg -i --force-depends libxp6_1.0.2-2_amd64.deb
```

至此，最终安装结束
