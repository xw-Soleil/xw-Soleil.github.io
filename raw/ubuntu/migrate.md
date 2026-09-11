# 硬盘迁移系统

> 用 LiveUbuntu + GParted + dd 把 Ubuntu 完整搬到另一块硬盘

换硬盘不想重装的话，可以从 Ubuntu 启动盘进 Live 系统，用 GParted 在新盘上按原来的分区布局分好区，再用 `dd` 逐个分区按位拷贝过去。单系统到这里就完事了；双系统还要给新分区重新生成 UUID 并更新 grub，否则启动时会挂错盘。整个流程照这篇做就行：

<link-preview cover="https://pica.zhimg.com/v2-345a81459c0ca08a14db6458df17b130_1440w.jpg" description="目标：将单系统或双系统 Ubuntu 完整迁移至另一块硬盘。工具：Rufus、GParted、dd；双系统需额外更新 UUID 与 grub。" link="https://zhuanlan.zhihu.com/p/731828327" mirror="weserv" title="Ubuntu 无损迁移、克隆系统">



</link-preview>

<alert title="dd 会覆盖目标分区" type="warning">

`dd` 是按位复制，会把目标分区里原有的数据全部覆盖。执行前一定确认 `if=` 和 `of=` 没写反。

</alert>
