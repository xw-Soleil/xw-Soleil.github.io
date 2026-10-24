# Shells

> Shell 基础与常用命令

## Shell Types

> `echo $SHELL` #查看当前使用的是什么 shell

1. **Bourne Shell (sh)**：良好的输入/输出控制，常用于脚本；不适合交互式用户；<mark>

默认提示为

</mark>

 <mark>

`$`

</mark>
2. **C Shell (csh)**：invented by Bill Joy；语法和 C 语言类似；输入输出不如 sh；对交互式用户更为友好；工作控制、历史记录等新功能；<mark>

默认提示为

</mark>

 <mark>

`%`

</mark>
3. **Bourne-Again Shell (bash)**：GNU 开发的自由软件；提供 csh 的所有交互式特征；编程语言和 sh 兼容；<mark>

默认提示是

</mark>

 <mark>

`$`

</mark>

<mark>

，root是

</mark>

<mark>

`#`

</mark>

## Wild card(通配符)

<table>
<thead>
  <tr>
    <th>
      符号
    </th>
    
    <th>
      名称
    </th>
    
    <th>
      作用
    </th>
    
    <th>
      匹配机制
    </th>
    
    <th>
      示例
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      *
    </td>
    
    <td>
      星号
    </td>
    
    <td>
      匹配 0 到无穷个字符
    </td>
    
    <td>
      文件匹配 (Glob)
    </td>
    
    <td>
      *.log
    </td>
  </tr>
  
  <tr>
    <td>
      ?
    </td>
    
    <td>
      问号
    </td>
    
    <td>
      匹配确切的 1 个字符
    </td>
    
    <td>
      文件匹配 (Glob)
    </td>
    
    <td>
      test?.py
    </td>
  </tr>
  
  <tr>
    <td>
      <span>
        
      </span>
    </td>
    
    <td>
      方括号
    </td>
    
    <td>
      匹配指定范围内的 1 个字符
    </td>
    
    <td>
      文件匹配 (Glob)
    </td>
    
    <td>
      <span>
        a-z
      </span>
      
      *
    </td>
  </tr>
  
  <tr>
    <td>
      {}
    </td>
    
    <td>
      花括号
    </td>
    
    <td>
      生成任意字符串序列
    </td>
    
    <td>
      字符串扩展 (Expansion)
    </td>
    
    <td>
      {a,b}.txt
    </td>
  </tr>
  
  <tr>
    <td>
      ~
    </td>
    
    <td>
      波浪号
    </td>
    
    <td>
      当前用户的主目录
    </td>
    
    <td>
      路径扩展
    </td>
    
    <td>
      ~/Desktop
    </td>
  </tr>
</tbody>
</table>

## Standard File Descriptors

- **(0) stdin**：给程序的**标准输入**，通常来自键盘，也可以重定向来自文件或命令
- **(1) stdout**：来自程序的**标准输出**，通常输出到终端屏幕，也可以重定向到文件或命令
- **(2) stderr**：**标准错误输出**，通常输出到终端屏幕，也可以重定向到文件或命令

## File Redirection | 文件重定向

1. **重定向标准输入**
  - <mark>
  
  `<`
  
  </mark>
  
   <mark>
  
  从
  
  </mark>
  
  <mark>
  
  **文件重定向输入**
  
  </mark>
  
   <mark>
  
  ，从
  
  </mark>
  
  <mark>
  
  `infile`
  
  </mark>
  
  <mark>
  
  读入作为输入
  
  </mark>
  
   <mark>
  
  `command < infile`
  
  </mark>
2. **重定向标准输出**
  1. 重定向覆盖输出
  
    - <mark>
    
    `>`
    
    </mark>
    
      <mark>
    
    重定向
    
    </mark>
    
    <mark>
    
    （
    
    </mark>
    
    <mark>
    
    覆盖）
    
    </mark>
    
    <mark>
    
    **标准输出到文件**
    
    </mark>
    
     <mark>
    
    ，不输出到终端屏幕，输出到
    
    </mark>
    
    <mark>
    
    `outfile`
    
    </mark>
    
     <mark>
    
    `command > outfile`
    
    </mark>
  2. 重定向追加输出
  
    - <mark>
    
    `>>`
    
    </mark>
    
     <mark>
    
    **追加标准输出**
    
    </mark>
    
    <mark>
    
    到文件， 不覆盖，写到文件末尾
    
    </mark>
    
     <mark>
    
    `command >> outfile`
    
    </mark>
3. **重定向标准错误输出**
  1. <mark>
  
  `2> file`
  
  </mark>
  
   <mark>
  
  重定向
  
  </mark>
  
  <mark>
  
  **标准错误**
  
  </mark>
  
  <mark>
  
  到文件，
  
  </mark>
  
  <mark>
  
  `2`
  
  </mark>
  
  <mark>
  
  代表
  
  </mark>
  
  <mark>
  
  `stderr`
  
  </mark>
  - 这一块不同shell各不相同，相见本节下小节
4. **管道符与命令**<mark>

**|**

</mark>

 <mark>

**tee**

</mark>


  - <mark>
  
  `|`
  
  </mark>
  
   <mark>
  
  #
  
  </mark>
  
  <mark>
  
  **命令 1 的标准输出作为命令 2 的标准输入**
  
  </mark>
  
  <mark>
  
  ，也就是把
  
  </mark>
  
  <mark>
  
  `command1`
  
  </mark>
  
  <mark>
  
  的
  
  </mark>
  
  <mark>
  
  `stdout`
  
  </mark>
  
  <mark>
  
  接到
  
  </mark>
  
  <mark>
  
  `command2`
  
  </mark>
  
  <mark>
  
  的
  
  </mark>
  
  <mark>
  
  `stdin`
  
  </mark>
  
   <mark>
  
  `command1 | command2`
  
  </mark>
  - <mark>
  
  `tee`
  
  </mark>
  
   <mark>
  
  #复制标准输出：从
  
  </mark>
  
  <mark>
  
  **标准输入读**
  
  </mark>
  
  <mark>
  
  ，再
  
  </mark>
  
  <mark>
  
  **写入标准输出和文件**
  
  </mark>
  
  <mark>
  
  **（三通）**
  
  </mark>
  
  <mark>
  
  （replicate the standard output）
  
  </mark>
  
  
    - <mark>
    
    举例：
    
    </mark>
    
      <mark>
    
    `ls -l | tee lslist`
    
    </mark>
    
    
      - <mark>
      
      此时
      
      </mark>
      
       <mark>
      
      `tee`
      
      </mark>
      
       <mark>
      
      会在屏幕上打印
      
      </mark>
      
       <mark>
      
      `ls -l`
      
      </mark>
      
       <mark>
      
      的内容，并将结果写入
      
      </mark>
      
       <mark>
      
      `lslist`
      
      </mark>
      - <mark>
      
      `-a`
      
      </mark>
      
       <mark>
      
      选项为
      
      </mark>
      
      <mark>
      
      **追加append**
      
      </mark>
      
      <mark>
      
      ，不覆盖，追加到文件的末尾
      
      </mark>
      - <mark>
      
      可以通过
      
      </mark>
      
       <mark>
      
      `tee test1.txt test2.txt`
      
      </mark>
      
       <mark>
      
      来写入两个文件，这样
      
      </mark>
      
      <mark>
      
      **会在屏幕上打印**
      
      </mark>
      
      <mark>
      
      **一**
      
      </mark>
      
      <mark>
      
      **次**
      
      </mark>
      
      <mark>
      
      **（两次应该是版本问题）**
      
      </mark>
5. <mark>

**丢弃输出 ｜ To discard output**

</mark>


  - <mark>
  
  `> /dev/null`
  
  </mark>
  
  <mark>
  
  ：将输出送到垃圾箱（黑洞）
  
  </mark>

### 标准输出流与标准错误输出流

#### Csh中标准输出流与标准错误输出流

1. <mark>

`>& file`

</mark>

 <mark>

重定向（覆盖）

</mark>

<mark>

**标准输出和标准错误**

</mark>

<mark>

到文件，

</mark>

<mark>

`&`

</mark>

<mark>

**意思可以理解为带上错误**

</mark>
2. `>>& file` <mark>

**追加**

</mark>

标准输出和标准错误到文件，与上一点相同
3. `|& command` 输送标准输出和标准错误到命令，也就是，把`stdout`和`stderr`一起通过管道送给下一个命令
4. `(command > outfile) >& errfile` 重定向标准输出和标准错误到**不同的文件**
  - 第一步：`command > outfile`
    - 把 stdout(1) 写到 `outfile`
    - stderr(2) 仍然默认到屏幕
  - 第二步：外层的 `>& errfile`
    - 它作用的是整个括号里的“命令组”的输出环境
    - 把“剩余的输出”（主要是 stderr）也重定向到 `errfile`

> <mark>
> 
> 这些命令在 bash 中也适用
> 
> </mark>

#### Sh/bash中标准输出流与标准错误输出流

1. <mark>

`2> file`

</mark>

 <mark>

重定向

</mark>

<mark>

**标准错误**

</mark>

<mark>

到文件，

</mark>

<mark>

`2`

</mark>

<mark>

代表

</mark>

<mark>

`stderr`

</mark>
2. `>` `file 2>&1` 重定向<mark>

**标准输出和标准错误**

</mark>

到文件
  - 拆开来理解（**类似于**<mark>
  
  **C语言指针的思想**
  
  </mark>
  
  ）
  
    1. `> file`是指重定向标准输出`>`到文件`file`
    2. `2>`处理标准错误输出
    3. `&1`，不是文件1，而是`stdout`
    4. 所以`2>&1`的意思是：**让 stderr（2）指向 stdout（1）当前指向的地方**
  - <mark>
  
  在
  
  </mark>
  
   <mark>
  
  **bash/zsh**
  
  </mark>
  
   <mark>
  
  里有一个更短的语法糖
  
  </mark>
  
  <mark>
  
  `&> file`
  
  </mark>
  
  <mark>
  
  ，等价于这个，即
  
  </mark>```bash
command &> file
command > file 2>&1
```


  - **语法糖(Syntactic Sugar)**: 就是"更甜的语法",让你写起来更简单、更爽,但底层做的事情是一样的。
3. `>> file 2>&1` **追加**标准输出和标准错误到文件，和上面的区别就是`>>`
4. `2>&1 | command` 输送**标准输出和标准错误**到某个命令command
5. `command > outfile 2> errfile` #重定向标准输出和标准错误到不同的文件
  - `>` 代表正常的输出`stdout`，写到`outfile`
  - `2>`代表错误输出`stderr`，写到`errfile`

<alert type="warning">

#### <mark>

`>&`

</mark>

 <mark>与</mark> <mark>

`&>`

</mark>

 <mark>区别</mark>

- `2>&1` 的含义：**将标准错误输出重定向到标准输出**。注意：符号 `>&` 是一个整体，不可分开，分开后就不是上述含义了。可以比对以下例子进行理解：

  1. `cat test > file 2>&1`
    - `> file` 先执行，stdout 指向 file
    - `2>&1` 后执行，stderr 指向 stdout 的当前位置（即 file）
    - **结果**：stdout 和 stderr 都输出到 file
  2. `cat test 2>&1 > file`
    - `2>&1` 先执行，此时 stdout 还指向终端，所以 stderr 也指向终端
    - `file` 后执行，stdout 改为指向 file，但 stderr 已经固定指向终端
    - **结果**：stderr 输出到终端，stdout 输出到 file（分离了！）
- <mark>

注意与

</mark>

 <mark>

`&>`

</mark>

 <mark>

的区别，

</mark>

<mark>

`&>`

</mark>

<mark>

是在

</mark>

 <mark>

**bash/zsh**

</mark>

 <mark>

里一个更短的语法糖——也就是约定俗成的把

</mark>

<mark>

`stdout stderror`

</mark>

<mark>

一起重定向了，将标准错误和标准输出全部送到一个地方

</mark>
</alert>

<table>
<thead>
  <tr>
    <th>
      语法符号
    </th>
    
    <th>
      作用 (重定向 STDOUT 和 STDERR)
    </th>
    
    <th>
      Csh / Tcsh
    </th>
    
    <th>
      Bash
    </th>
    
    <th>
      Sh (POSIX)
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      >& file
    </td>
    
    <td>
      将标准输出和错误都写入文件
    </td>
    
    <td>
      原生支持 (常用)
    </td>
    
    <td>
      支持 (兼容写法)
    </td>
    
    <td>
      不支持 (通常报错或行为不同)
    </td>
  </tr>
  
  <tr>
    <td>
      &> file
    </td>
    
    <td>
      将标准输出和错误都写入文件
    </td>
    
    <td>
      不支持
    </td>
    
    <td>
      原生支持 (推荐语法糖)
    </td>
    
    <td>
      不支持
    </td>
  </tr>
</tbody>
</table>

## Other Special Command Symbols

- <mark>

`;`

</mark>

 <mark>

# 命令分隔符，就是

</mark>

<mark>

`cmd1 ; cmd2`

</mark>

<mark>

，

</mark>

<mark>

`cmd1`

</mark>

<mark>

执行完之后执行

</mark>

<mark>

`cmd2`

</mark>

<mark>

，哪怕

</mark>

<mark>

`cmd1`

</mark>

<mark>

执行失败

</mark>
- <mark>

`&`

</mark>

 <mark>

# 在后台运行命令

</mark>

<mark>

`cmd &`

</mark>
- <mark>

`&&`

</mark>

 <mark>

#只有上一条命令成功完成才运行下一条命令，逻辑与，

</mark>

<mark>

`make && ./a.out`

</mark>

<mark>

编译成功才运行程序

</mark>
- <mark>

`||`

</mark>

 <mark>

#只有上一条命令没有成功完成才运行下一条命令，比如：

</mark>

<mark>

`cd /some/dir || echo "no such dir"`

</mark>
- <mark>

`()`

</mark>

 <mark>

#圆括号中的分组子命令在子 shell 中执行

</mark>

```bash
(cd /tmp; ls)
pwd   # 你会发现外面还是原来的目录
```

## Quoting

- <mark>

`\`

</mark>

 <mark>

#对待下一个字符为纯文本，比如

</mark>

<mark>

`echo \$HOME`

</mark>

<mark>

，输出的是

</mark>

<mark>

`$HOME`

</mark>

<mark>

而不是实际的HOME

</mark>
- <mark>

`' '`

</mark>

 <mark>

#

</mark>

<mark>

**单引号内不允许变量和命令替代**

</mark>

<mark>

，即

</mark>

 <mark>

`$`

</mark>

 <mark>

失效，就是按字符串对待

</mark>
- <mark>

`" "`

</mark>

 <mark>

#

</mark>

<mark>

**双引号内允许变量和命令替代**

</mark>

<mark>

，不在字符串中禁用

</mark>

 <mark>

`$`

</mark>

 <mark>

和

</mark>

 <mark>

`\`

</mark>

<mark>

，和单引号区分一下

</mark>
- `command` 或 `$(command)` #用命令的输出代替命令输入

```bash
echo "today is $(date)"
```

## Job Control

- `&` #命令在后台执行
- <mark>

`^Z`

</mark>

 <mark>

#当正在运行时

</mark>

<mark>

，

</mark>

<mark>

**停止**

</mark>

<mark>

**该工作**

</mark>

<mark>

，该工作

</mark>

<mark>

**在后台挂起**

</mark>
- `^C` #<mark>

**结束**

</mark>

**当前工作**
- <mark>

`bg`

</mark>

 <mark>

#继续在后台挂起的工作

</mark>

 <mark>

`bg = back-ground`

</mark>

<mark>

，注意是

</mark>

<mark>

**在后台继续**

</mark>


  - <mark>
  
  `bg + 任务号`
  
  </mark>
- <mark>

`fg [%n]`

</mark>

 <mark>

#将工作

</mark>

<mark>

**返回到前台**

</mark>

<mark>

**（sh被堵住了）**

</mark>

<mark>

`fg = fore-ground`

</mark>


  - <mark>
  
  `fg + 任务号`
  
  </mark>
  
  <mark>
  
  ，这里的
  
  </mark>
  
  <mark>
  
  **任务号都是**
  
  </mark>
  
   <mark>
  
  `jobs`
  
  </mark>
  
   <mark>
  
  **中的**
  
  </mark>
  
  <mark>
  
  ，不是
  
  </mark>
  
   <mark>
  
  `ps`
  
  </mark>
  
   <mark>
  
  进程号
  
  </mark>
- <mark>

`jobs`

</mark>

 <mark>

#列出后台工作（list background jobs）

</mark>


  - `-l` 列出 pid `l = list`
  - `-r` 正在后台 run 的工作 `r = run`
  - `-s` 后台中暂停的工作 `s = stop`
- <mark>

`ps`

</mark>

 <mark>

可以查看进程状态，

</mark>

<mark>

`top`

</mark>

 <mark>

进行动态进程监控，而

</mark>

 <mark>

`jobs`

</mark>

 <mark>

可以查看后台任务

</mark>

> <mark>
> 
> `ps/top`
> 
> </mark>
> 
>  <mark>
> 
> 看的是系统层面的进程
> 
> </mark>
> 
> 
> 
> <mark>
> 
> `jobs`
> 
> </mark>
> 
>  <mark>
> 
> 看的是
> 
> </mark>
> 
> <mark>
> 
> **当前这个 shell**
> 
> </mark>
> 
>  <mark>
> 
> 启动并管理的任务
> 
> </mark>
> 
> 
> 
> `[1]+ 27335 Running                 xeyes &`
> 
> - 1是任务号
> - 27335是进程号

## <mark>Process Commands</mark>

### <mark>ps</mark>

- <mark>

`ps [options]`

</mark>

 <mark>

#report a

</mark>

 <mark>

**p**

</mark>

<mark>

hoto

</mark>

 <mark>

**s**

</mark>

<mark>

napshot of the current processes, show status of process，显示进程状态

</mark>


  - <mark>
  
  `-ef`
  
  </mark>
  
   <mark>
  
  #
  
  </mark>
  
   <mark>
  
  `e=every process`
  
  </mark>
  
   <mark>
  
  `f=full format`
  
  </mark>
  
  <mark>
  
  使用标准语法查看系统上的每个进程，即显示进程详细信息并显示进程父子关系
  
  </mark>

> UID          PID    PPID  C STIME TTY          TIME CMD
> 
> root           1       0  0 14:19 ?        00:00:03 /sbin/init splash
> 
> root           2       0  0 14:19 ?        00:00:00 <span>
> 
> kthreadd
> 
> </span>
> 
> 
> 
> root           3       2  0 14:19 ?        00:00:00 <span>
> 
> pool_workqueue_release
> 
> </span>
> 
> 
> 
> root           4       2  0 14:19 ?        00:00:00 <span>
> 
> kworker/R-rcu_gp
> 
> </span>
> 
> 
> 
> root           5       2  0 14:19 ?        00:00:00 <span>
> 
> kworker/R-sync_wq
> 
> </span>

> **PPID**（Parent Process ID） **PID** ( Process ID )

- <mark>

`-l`

</mark>

 <mark>

#

</mark>

 <mark>

**l**

</mark>

<mark>

ong format，显示长信息

</mark>

### <mark>top</mark>

- <mark>

`top`

</mark>

 <mark>

#display Linux processes，显示更新的进程信息和系统使用，间隔为 5s

</mark>

### <mark>pstree</mark>

- <mark>

`pstree`

</mark>

 <mark>

#显示进程之间的

</mark>

<mark>

**层次关系**

</mark>

<mark>

（show the

</mark>

 <mark>

hierarchical

</mark>

 <mark>

relations between processes）

</mark>

### uptime

- `uptime` #显示该系统的**运行时长**（tell how long the system has been running）

### kill

- <mark>

`kill`

</mark>

 <mark>

#terminate or signal processes，终止或示意进程

</mark>


  - `kill [-signal] processID`
  - `kill -l` #列出可用的 kill 信号
  - <mark>
  
  `kill -9 processID`
  
  </mark>
  
   <mark>
  
  强制杀死进程
  
  </mark>

## <mark>Environment</mark> <mark>Variables</mark>

先搞懂两类变量：local vs environment

> 对应sz的 export PATH=$PAT

### <mark>Shell 变量（local shell variable）</mark>

- 只在**当前这个 shell**里有效
- 你开一个新终端或启动一个子进程，**它不一定能看到**

例子（bash）：

```bash
name=Alice
echo $name
```

### 环境变量（environment variable）

- 会被“导出（export）”，变成环境的一部分
- 启动子进程（比如运行 `python`、`grep`、`bash`）时，<mark>

**子进程会继承这些变量**

</mark>
- 这就是为什么它叫 environment：它是程序运行的“环境”

例子（bash）：

```bash
export NAME=Alice
```

> #### 一句话记忆
> 
> - **local：只给自己用**
> - **env：给自己 + 子进程用**

- **Set global environment variable**
  - `setenv NAME value` #csh设置环境变量的方式
  - `NAME=value; export NAME` #sh设置环境变量
  - `export NAME=value` #bash（export 用于将 shell 变量输出为环境变量）
- **Set local shell variable**
  - `set name=value` #csh设置shell变量
  - `name=value` #sh/bash设置shell变量
- **Unset**
  - `unsetenv / unset` #csh取消变量
  - `unset` #sh/bash取消变量
- **Showing/Getting Variables**
  - `env` #csh，bash 也可，只看环境变量
  - `set` #sh/bash，但 set 会显示更多，因为**显示所有变量**，env 只是环境变量
  - `echo $NAME`  `echo + $变量名 = 打印变量值`
- 当给环境变量赋多个值时，需要用 `:` 间隔不同值 #When assigning multiple values to the variable they must be separated by the colon `:` character

典型就是 `PATH`

```bash
echo $PATH
/usr/local/bin:/usr/bin:/bin:...
```

- 用`:`分割多个目录，shell 查找命令时，会按 PATH 列表顺序去这些目录找

## <mark>Shell Controls</mark>

### if 条件

- 最基本的用法，`[ ]` 单括号为判断，也叫**测试**，注意`[ <-左右两边要有空格-> ]`，`if then elif else fi` 的格式，记忆一下格式即可

```bash
if [ $grade -gt 90 ]; then
     echo "good"
 elif [ $grade -gt 70 ]; then
     echo "pass"
 else
     echo "no"
 fi
```

#### options 选项

```bash
#这些 -r/-w/-x/... 都是用来判断 某个文件/路径的属性
[ -r filename ]   # 可读？
[ -d dirname ]    # 是目录？
```

- `-r` #存在且可读
true if it exists and is **r**eadable, otherwise return false (0)
- `-w` #存在且可写
true if it exists and is **w**ritable
- `-x` #存在且可执行
true if it exists and is e**x**ecutable
- `-f` #存在且是常规文件
true if it exists and is **a regular file**
- `-d` #存在且是目录
true if it exists and is a **d**irectory
- `-e` #存在
true if the file **e**xists
- `-o` #使用者拥有该文件
true if the user **o**wns the file
- `-z` #文件大小为 0 / 文件为空
true if the file has **z**ero length (empty)

#### 比较运算

- 只能用于数字：`-gt`（**g**reater **t**han）、`-lt`（**l**ess **t**han）、`-eq`（**eq**ual）、`-ne`（**n**ot **e**qual）、`-le`（**l**ess or **e**qual）、`-ge`（**g**reater or **e**qual）
- `-a`（**a**nd）、`-o`（**o**r）、`!`（not）

  - 在 `[]` 中不能直接使用 `&&` 和 `||`，只能使用 `-a`、`-o`、`!`；但在 `[]` 外面是可以使用的，如：
  ```bash
  if [ -f $line ] && [ -x $line ]; then
      code...
  else
      code...
  fi
  ```

### `[[ ]]` 的使用方法

> Bash
> 
> Zsh
> 
> Ksh (Korn Shell)
> 
> 这三者才兼容这个语法

- 在 `[[ ]]` 中使用 `>`、`<` 等符号不需要转义文字，即`>`不会被当成重定向，但是注意`>`比较的是字符串不是数字，数字比较要用`-gt` `-lt`，如：```bash
if [[ $1 > 5 ]]; then
    echo "$1 的值大于 5"
else
    echo "$1 的值小于 5"
fi
```
- 支持 `&&` 和 `||` 的括号内使用，如：```bash
if [[ $a != 3 && $a != 10 ]]; then
     echo "hello i am linux"
 fi
```
- 如果不使用 `[[ ]]` 的话则需要这样写：```bash
if [ $a != 3 -a $a != 10 ]; then
     echo "hello i am linux"
 fi
```
- 或者```bash
if [ $a != 3 ] && [ $a != 10 ]; then
     echo "hello i am linux"
 fi
```

### for 循环语句

#### 基本用法

`for 变量名 in 取值列表; do ... done`，如下

```bash
for Host in $(seq 1 254); do
     code...
 done
 for i in $(find / -name $filename); do
     code...
 done
 for i in {1..5}; do
     code...
 done
```

#### 进阶用法：

**如果想依次处理传入程序的参数，可以使用** `for` **与** `$*` **的结合**

- `$1/$2/$3...` 是什么？

当你运行：

```bash
./demo a b c d
```

> - `$0` = 脚本名（demo）
> - `$1` = a
> - `$2` = b
> - `$3` = c
> - `$4` = d
> 记忆：**$N = 第 N 个参数****，超过10要加${10}**

- `$1`：脚本中第一个参数，`$2`、`$3`、`$4` 以此类推
- `$*`：以一个字符串显示所有向脚本传递的参数，等于 `"$1 $2 $3 ..."`
- 示例：假设脚本叫 `demo.bash`，终端输入 `./demo a b c d`，则参数依次为 `$1 $2 $3 $4`，脚本内容如下：

```bash
#!/bin/bash

 for i in $*; do
     echo "$i"
 done
```

- 这样会依次遍历 `$1 $2 $3 $4` 并处理（这里是打印到屏幕上）

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ICCAD/Shells-01.webp)

### while 循环语句

#### 基本用法：

`while 表达式; do 内容 done`

- 可以与 `break` 与 `continue` 结合，和C语言类似的

  - `break` 是终止循环
  - `continue` 是跳出当前循环
- 例子如下：在死循环中，满足条件终止循环

```bash
while true; do
     let N++
     if [ $N -eq 5 ]; then
         break
     fi
     echo $N
 done
```

- 又如：利用 `continue` 跳过一次循环

```bash
N=0
 while [ $N -lt 5 ]; do
     let N++
     if [ $N -eq 3 ]; then
         continue
     fi
     echo $N
 done
```

结果输出：`1 2 4`

#### 进阶技巧：

利用 `while` 依次读入文件内容进行处理

```bash
while read line; do
     echo "$line"
 done < temp.txt
```

- `line` 是一个变量名，这里 `while` 将依次读取 `temp.txt` 每行的内容，并打印
- 这个技巧同上面的 `for` 进阶技巧一样，非常好用且重要：可以把要处理的内容保存到文本文件中，再用这个 `while` 逐行处理

### case 选择语句

#### 基本用法：

`case 变量 in 模式1) ... ;; 模式2) ... ;; esac`

```bash
case 模式名 in
 模式1)
     命令
     ;;
 模式2)
     命令
     ;;
esac
```

- 每个**模式必须以右括号** `)` **结束**（可以是数字或英文）
- 每个分支的**命令必须以双分号** `;;` **结束**，`;;`就相当于`break`
- `esac` 表示 case 结束
- 示例：

```bash
case $choice in
 1)
     操作
     ;;
 Start)
     操作
     ;;
esac
```

### 终端命令与 History

- 终端：定义指的是与计算机系统相连的一种**输入输出设备**
  - `tty` #print the file name of the terminal connected to standard input
- `tty = tell terminal type/device`

> 显示当前终端设备的文件名

- `stty` #change and print terminal line settings，改变终端设置
- `stty = set tty`
- **History** #GNU history library

  - `history [nn]` #显示过去 nn 条命令
  - `!!` #重复上一条命令
  - `!nn` #重复`history`中编号为 nn 的命令
  - `!string` #重复最近的以 string 开头的命令

### <mark>Magic Symbol</mark> <mark>

`#!`

</mark>



脚本解释器，告诉系统：这个脚本应该用哪个解释器来运行

- <mark>

**sh/bash**

</mark>


  - <mark>
  
  `#!/bin/sh`
  
  </mark>
  - <mark>
  
  `#!/bin/bash`
  
  </mark>
- <mark>

**csh**

</mark>


  - <mark>
  
  `#!/bin/csh -f`
  
  </mark>
  
  <mark>
  
  （
  
  </mark>
  
  <mark>
  
  `-f`
  
  </mark>
  
   <mark>
  
  option，without parsing
  
  </mark>
  
   <mark>
  
  `.cshrc`
  
  </mark>
  
  <mark>
  
  ）
  
  </mark>
- <mark>

如果没有 Magic Symbol 指示，那么执行脚本命令前必须加上对应的解释器

</mark>


  - <mark>
  
  `sh sh_script`
  
  </mark>
  
   <mark>
  
  /
  
  </mark>
  
   <mark>
  
  `csh csh_script`
  
  </mark>
  
   <mark>
  
  /
  
  </mark>
  
   <mark>
  
  `bash bash_script`
  
  </mark>
  
   <mark>
  
  /
  
  </mark>
  
   <mark>
  
  `app_prog app_script`
  
  </mark>
- <mark>

但在加上 Magic Symbol 并且

</mark>

 <mark>

`chmod +x script`

</mark>

 <mark>

后，我们即可直接运行脚本

</mark>


  - `sh_script` / `csh_script` / `bash_script` / `app_script`

## <mark>Meta-Characters And REP</mark>

### Meta-Characters as Wild Cards

这些是 shell 里的通配符（wildcards / globbing），主要用于 `ls`、`cp`、`mv`、`rm`、`find`（注意：`find` 本身也有通配/正则的用法）等命令里做**文件名/路径匹配**。

#### Meta-Character Rules

- `?` 匹配当前位置任意一个字符，即当前位置**必须**有一个字符（不多不少）

  - `ls m?n` #m4n, man, m!n
- `*` 匹配当前位置任意 0 个或多个字符，即当前位置可以匹配 **0 个或多个字符**
  - `ls *` #不是 . 开头的任意文件
  - `ls [a-z]*` #小写字母开头的任意文件
  - `a*` 匹配：`a`、`ab`、`abc.txt`、`a___`
  - `*.c` 匹配：`main.c`、`test.c`
- `[abc]` #匹配括号内的任意<mark>

一个

</mark>

字符
- `[a-d]` #匹配括号内范围的任意字符
- `[!abc]` #匹配任意字符不在封闭集内

  - `ls chpt[1-4]` #chpt1, chpt2, chpt3, chpt4
- `{abc,bcd,cde}` #匹配任一一组中的任一字符，注意用逗号分隔，花括号展开

  - `echo {a,b,c}` 会展开成：`echo a b c`
  - `ls {src,include}/*.h` 等价于：`ls src/*.h include/*.h`
- `~` #当前用户的 home 目录
- `~user` #指定 user 的 home 目录
- `\` #对待下一个字符为纯文本

## Regular Expression Syntax

这些是正则表达式（Regular Expression, regex）的基础语法，和通配符很像，但含义不一样，主要给“文本内容匹配”用

### REP Rules

- `cat` #字符串 cat
- `.` #匹配除换行以外的任意单个字符

  - `.at` #cat, rat, mat, bat
- `?` #匹配之前单个字符的 **0 个或 1 个**
  - `colou?r`匹配：`color`（u 出现 0 次）、`colour`（u 出现 1 次）
- `*` #匹配之前的单个字符的 **0 或更多实例**
  - `xy*z`匹配：xz（y 0 次）、xyz（1 次）、xyyz（2 次）、xyyyz（3 次）......
  - `[A-Z][A-Z]*` #A, CD, GPIO，第一位必须是大写字母，后面可以跟 0 或更多个大写字母
  - `[A-Z]*` #  , A, CD，0 或更多个大写字母
- `[abc]` #匹配括号内的任意**一个**字符

  - `gr[ae]y`匹配：`gray` 或 `grey`
  - `[cC]at` #cat 或 Cat
- `[a-d]` #匹配括号内范围的任意**一个**字符
- `[^abc]` #匹配任意字符不在封闭集内

  - `[^a-zA-Z]` #任意非字母字符
- `^exp` #以该表达式开头的行

  - `^cat` #cat 在行首
- `exp$` #以该表达式结尾的行

  - `cat$` #cat 在行尾
  - `[0-9]$` #以数字结尾的行
- `\` #对待下一个字符为纯文本

  - `\*` #对待为纯文本星号
  <mark>
  
  **通配符（Wildcards/Globbing）主要用于管理文件，而正则表达式（Regular Expressions）主要用于处理文本内容。**
  
  </mark>

> 特殊字符总结
> 
> 正则中的特殊字符(需要转义来匹配字面意思)
> 
> ```text
> . * + ? ^ $ { } [ ] ( ) | \
> ```
> 
> 转义序列(需要反斜杠来表示特殊含义)
> 
> ```text
> \s  空白字符
> \d  数字
> \w  单词字符
> \n  换行
> \t  制表符
> ```

- `|` #表示或

来个具体例子

> ```bash
> ❯ ls | grep -E '\(Answer format: "[^"]+"\)'                                  
> (Answer format: "edlin, edit")
> ```
> 
> **匹配过程:**
> 
> 1. `"` → 匹配第一个双引号 `"`
> 2. `[^"]+` → 捕获 `edlin, edit` (所有非引号字符)
> 3. `"` → 匹配第二个双引号 `"`
> 4. `\)` → 匹配右括号 `)`

### 条件判断部分

第一行包含三个逻辑判断，通常用于决定是否执行后续的 `diff` 或拷贝操作：

- **(if -d)**:

  - 通常用于检查某个**路径是否存在且是一个目录**（Directory）。
  - 完整写法一般是 `if [ -d $DIR_PATH ]`。
- **(if !-w)**:

  - 检查文件或目录是否**不可写**。`!` 是取反符号，`-w` 代表可写（Writable）。
  - 这通常是为了确认目标位置是否有权限限制，或者是否需要提升权限。
- **if [ \****tty != "console" ]**:

  - 检查当前的终端类型。
  - **tty** 命令会返回当前控制台的设备名。
  - **意思**：<mark>
  
  如果当前用户
  
  </mark>
  
  <mark>
  
  **不是**
  
  </mark>
  
  <mark>
  
  在物理控制台（Console）上直接操作（例如是通过 SSH 远程登录），则条件成立。
  
  </mark>

---

### 命令执行部分

第二行是一个文件对比命令：

`diff $SYNOPSYS/admin/setup/$f $LIBX11 >& /dev/null`

- **diff**: 比较两个文件的差异。

  - 源文件：`$SYNOPSYS/admin/setup/$f`（通常是 Synopsys EDA 软件的安装配置模板）。
  - 目标文件：`$LIBX11`（系统路径下的配置文件）。
- **>& /dev/null**:

  - 这是一个**重定向**操作。
  - 它将“标准输出”和“标准错误”全部丢弃到 `/dev/null`（黑洞）。
  - **目的**：脚本并不想让你看到具体的差异内容，它只是通过 `diff` 的**退出状态码（Exit Status）**来判断两个文件是否一致。
  
    - <mark>
    
    如果状态码为
    
    </mark>
    
     <mark>
    
    `0`
    
    </mark>
    
    <mark>
    
    ：文件完全一致。
    
    </mark>
    - <mark>
    
    如果状态码为
    
    </mark>
    
     <mark>
    
    `1`
    
    </mark>
    
    <mark>
    
    ：文件有差异。
    
    </mark>
