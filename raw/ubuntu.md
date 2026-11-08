# Ubuntu装进移动硬盘

> 此系列主要是 lz 折腾 ubuntu 系统安装、迁移以及 IC Design 软件在 Ubuntu 上的安装

## Ubuntu装进移动硬盘

## 安装流程

### 写在前面

> 本文记录本人使用移动硬盘安装Ubuntu系统的全过程，实现一个硬盘随插随用，任意电脑都可以使用（windows机器），但过程中也有踩坑，也不保证完全按照流程下来不会出错，仅供参考，下面罗列我的参考文章

[(72 封私信 / 80 条消息) Ubuntu系统安装在移动固态硬盘，实现在不同电脑即插即用 - 知乎](https://zhuanlan.zhihu.com/p/618018275?s_r=0)

[Windows系统下，Ubuntu安装至移动硬盘（简单分析与详细安装教程）_移动硬盘安装ubuntu-CSDN博客](https://blog.csdn.net/qq_42699580/article/details/104312383)

[新手安装 Ubuntu 操作系统步骤教程_ubuntu安装教程-CSDN博客](https://blog.csdn.net/weixin_42776111/article/details/84961031)

[Ubuntu安装详细教程_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1CG4y1h7bx/?spm_id_from=333.337.search-card.all.click)

### Ubuntu 系统镜像下载

选择的是清华镜像源

[Index of /ubuntu-releases/22.04/ | 清华大学开源软件镜像站 | Tsinghua Open Source Mirror](https://mirrors.tuna.tsinghua.edu.cn/ubuntu-releases/22.04/)

版本选择

![image-20250825121711349](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/image-20250825121711349.png)

### U盘启动盘制作

插入U盘，打开UltraISO软件，不需要注册、不需要订购，点击“继续试用”即可

![image-20250825121725885](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/image-20250825121725885.png)

在软件界面找到Ubuntu 的iso文件

![image-20250825121745458](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/image-20250825121745458.png)在菜里栏中 **启动一>写入硬盘映像**

![image-20250825121801134](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/image-20250825121801134.png)格式化之后进行写入，写入成功的界面如下：

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/asynccode)### 移动硬盘分区

打开DiskGenius软件，在其左侧导航栏中点击选中需要分区的移动硬盘，在**基本GPT**处右键，点击创建新分区

> 如果你这里不是基本GPT 是基本MBR 那么你需要点击磁盘盘符 （我这里是HD1:Sandiskextreme55AE）,右键，选择“转换分区表类型为GUID格式”

![image-20250825121953328](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/image-20250825121953328.png)建立新分区的详细操作可以参考下面这个文章，但是**注意不要学习他的分区命名**

[Windows系统下，Ubuntu安装至移动硬盘（简单分析与详细安装教程）_移动硬盘安装ubuntu-CSDN博客](https://blog.csdn.net/qq_42699580/article/details/104312383)

我们一共分四个区域：

1. **ESP(0)分区** ：文件系统类型为FAT32，大小我分配为1.0GB。该分区用于Linux系统的 /boot引导分区，后续启动 Ubuntu 系统的引导文件将会放在这个分区下的EFI目录，所以这个分区很重要

  - 注意这个分区的建立请直接在右键之后的“建立ESP/MSR分区”这里建立ESP分区就好了，我这里建立的是1024MB（软件显示1G）大小
2. **分区(1)**：文件系统类型为Linux swap partition，大小我分配为16.0GB。该分区用于Linux系统的**swap**交换空间
3. **分区(2)**：文件系统类型为EXT4，大小我分配为80GB。该分区用于Linux系统的 **“/”** 目录。
4. **分区(3)** ：文件系统类型为EXT4大小我分配为200 GB。该分区用于Linux系统的 **"/home"** 目录。

注意，这四个分区对于EXT4类型文件系统是可以按照下面方法设置的（这个图来自上面的csdn），其他分区最好先不要设置卷标，也可以都不设置卷标

![image-20250825161745305](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/image-20250825161745305.png)四个分区建立后，点击上方图标栏的“保存更改”按钮，完成分区。

### 安装Ubuntu系统

> 在Ubuntu系统安装之前，**需要记住自己的移动硬盘容量大小及其命名、电脑硬盘大小以及自定义的Ubuntu系统4个分区的大小**

接下来就是对Ubunut系统的安装了，重启电脑，在开机界面**按住F2进入BIOS界面**（不同电脑可能不一样，自行善用搜索即可），在BIOS界面找到 Secure Boot(或安全启动)，将其关闭，而后找到Boot Option(或启动选项)，将USB启动项设置为第一启动，然后保存并退出BIOS界面，这个时候就会从U盘进行启动Ubuntu安装界面（原谅我只找到了这个高糊画质，参考[Ubuntu安装详细教程_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1CG4y1h7bx/?spm_id_from=333.337.search-card.all.click&vd_source=a18b4e2a531bfb64d1c42547f9fe1ad7)）

![image-20250825184058316](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/image-20250825184058316.png)我点击了第一个`Try or Install Ubuntu` 但是点击之后就是黑屏，有一个光标，但是按键盘没任何反应；所以我选了第二个`Ubuntu(safe graphics)`才成功进入启动界面，神奇。

进入安装界面之后，首先是一些常规选项，参考上面B站视频或者是csdn链接都可以，一路设置之后，到了这里

![image-20250825185136885](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/image-20250825185136885.png)**这里要注意一定要选择其他选项，不然你电脑原本的windows硬盘有可能也被格式化了！！！**

继续之后会是下面的界面

![image-20250825185349917](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/image-20250825185349917.png)你的这个界面可能会有很多选项，但是请你仔细识别，这里面包含了windows分区的磁盘和你插入的移动硬盘的分区，一般来说你首先看有一个Windows Boot Manager ，那么这个盘就是Windows的硬盘，同一个名字下面的都不要动，那显然还有另外一个设备，那么你可以根据内存大致推断他是不是你的硬盘，然后按照分区来，**"安装启动引导器的设备"一定要选择 /boot 对应的分区---ESP分区**，然后可能上面这个图也不是很准确，你的界面的挂载点应该是空的，没有任何选项，然后只有两个ext4类型的分区设备，分别双击他们进行更改，你发现可以更改他们的挂载点，对应我前面提到的：

1. **分区(2)**：文件系统类型为EXT4，大小我分配为80GB。该分区用于Linux系统的 **“/”** 目录。
2. **分区(3)** ：文件系统类型为EXT4，大小我分配为200 GB。该分区用于Linux系统的 **"/home"** 目录。

这两部分更改好了之后就选好启动盘("安装启动引导器的设备"选择 /boot 对应的分区---ESP分区)，直接安装就行了。

然后系统会提示你进行重启，注意重启的时候要拔掉启动U盘，我在这一步进入了grub界面，这是因为系统找不到ubuntu的启动文件了，这个时候可以参考网上资料找一找，但是我当时只是输入exit，然后启动的时候把启动引导选择了windows，进了一次windows之后再次返回启动Ububtu界面，发现就好了，正常进入系统。神奇。。。。

到这个阶段为止，Ubuntu在你的电脑上就可以顺畅使用了，但是在别人电脑上还不行。

当把移动固态硬盘插到其他电脑时，是不能正常使用的，原因是移动硬盘的ESP分区中没有引导文件，解决过程如下：

重新插上U盘和移动固态硬盘，进入Ubuntu系统后，连上网络，安装 **boot-repair** 软件：

```powershell
sudo apt-add-repository ppa:yannubuntu/boot-repair
sudo apt update
sudo apt install boot-repair
```

安装完成后，打开终端执行该软件

```bash
boot-repair
```

点击**Recommended repair（或推荐修复）**按钮，等待修复完成即可

之后就可以随便任意电脑都可以打开你的移动硬盘上的Ubuntu系统啦！

## 后续调整

对于磁盘大小调整,参考

1. [如何在 Ubuntu 24.04 中缩小、移动或扩展系统分区](https://cn.linux-terminal.com/?p=7992#:~:text=%E4%BD%BF%E7%94%A8%E7%B3%BB%E7%BB%9F%E5%86%85%E7%BD%AE%E7%9A%84%E2%80%9C%E7%A3%81%E7%9B%98%E2%80%9D%E5%B7%A5%E5%85%B7%E5%8F%AF%E4%BB%A5%E5%BE%88%E5%AE%B9%E6%98%93%E5%9C%B0%E7%BC%A9%E5%B0%8F%E5%88%86%E5%8C%BA%E4%BB%A5%E5%87%8F%E5%B0%8F%E5%85%B6%E5%A4%A7%E5%B0%8F%E3%80%82%20%E9%A6%96%E5%85%88%EF%BC%8C%E6%90%9C%E7%B4%A2%E5%B9%B6%E5%90%AF%E5%8A%A8%E2%80%9C%20%E7%A3%81%E7%9B%98%20%E2%80%9D%E5%B7%A5%E5%85%B7%E3%80%82%20%E8%AF%A5%E5%B7%A5%E5%85%B7%E6%89%93%E5%BC%80%E5%90%8E%EF%BC%8C%E9%80%89%E6%8B%A9%E5%B7%A6%E4%BE%A7%E7%9A%84%E7%A3%81%E7%9B%98%E9%A9%B1%E5%8A%A8%E5%99%A8%EF%BC%8C%E7%84%B6%E5%90%8E%E9%80%89%E6%8B%A9%E8%A6%81%E7%BC%A9%E5%B0%8F%E7%9A%84%E5%88%86%E5%8C%BA%E3%80%82%20%E6%9C%80%E5%90%8E%EF%BC%8C%E5%8D%95%E5%87%BB%E4%B8%8B%E9%9D%A2%E7%9A%84%E9%BD%BF%E8%BD%AE%E5%9B%BE%E6%A0%87%E4%BB%A5%E8%8E%B7%E5%8F%96%E2%80%9C,%E8%B0%83%E6%95%B4%E5%A4%A7%E5%B0%8F...%E2%80%9D%20%E6%B3%A8%E6%84%8F%EF%BC%9A%E5%B9%B6%E9%9D%9E%E6%89%80%E6%9C%89%E6%96%87%E4%BB%B6%E7%B3%BB%E7%BB%9F%E9%83%BD%E5%8F%AF%E4%BB%A5%E8%B0%83%E6%95%B4%E5%A4%A7%E5%B0%8F%E3%80%82%20%E5%9C%A8%E6%88%91%E7%9A%84%E6%B5%8B%E8%AF%95%E4%B8%AD%EF%BC%8C%E5%AE%83%E8%83%BD%E5%A4%9F%E8%B0%83%E6%95%B4%2F%E7%BC%A9%E5%B0%8F%20Ext4%E3%80%81NTFS%20%E5%88%86%E5%8C%BA%E7%9A%84%E5%A4%A7%E5%B0%8F%E3%80%82%20%E5%9C%A8%E4%B8%8B%E4%B8%80%E4%B8%AA%E5%AF%B9%E8%AF%9D%E6%A1%86%E4%B8%AD%EF%BC%8C%E6%82%A8%E7%8E%B0%E5%9C%A8%E5%8F%AF%E4%BB%A5%E7%A7%BB%E5%8A%A8%E6%BB%91%E5%9D%97%E6%9D%A5%E8%AE%BE%E7%BD%AE%E7%BC%A9%E5%B0%8F%E7%9A%84%E7%A9%BA%E9%97%B4%E9%87%8F%E3%80%82)
2. [Ubuntu 24.04 LTS磁盘空间不足解决](https://blog.csdn.net/m0_48160420/article/details/146489694)

以及在gparted里面最好不要动exfat 这种非linux file 格式的磁盘空间，很容易卡住。。。 当时动了我的本来作为U盘的分区 还好只是分区表之类的损坏了 吓死个人
