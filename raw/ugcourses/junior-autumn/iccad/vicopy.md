# Vi（详细版）

> Vi 编辑器的扩展笔记，比基础版更详细

## Editors

- Programs that let you interactively edit text files，即交互式编辑文本文件的程序有：

  - DOS: `edlin`, `edit`
  - Windows: `notepad`, `wordpad`
  - Unix: `ed`, `vi`, `vim`
  - GNU: `emacs`
  - `xedit`, `gedit`, `nano`, `pico`
- 文字处理器，**带排版、字体、图片、分页**等能力，保存的通常不是纯文本（如 `.doc/.docx/.odt/.pdf` 等）

  - WordStar, MSWord, Framemaker, Acrobat…
  - StarOffice, OpenOffice, LibreOffice

## vi Modes

- **Command Mode** 命令模式

  - `vi` 启动后为命令模式
  - 每一个按键执行一个编辑命令
  - <mark>
  
  **输入**
  
  </mark>
  
   <mark>
  
  **:**
  
  </mark>
  
   <mark>
  
  **进入命令行模式**
  
  </mark>
  
  <mark>
  
  （command line mode）
  
  </mark>
- **Insert Mode**
  - 只有在 Insert mode 下，才可以做文字输入，**按** **[ESC]** **键可回到命令行模式**
  - 通过输入几个插入命令之一来进入

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ICCAD/ViCopy-01.webp)

- 简单 `vi` 示例

  - `vi tmp.txt` #在命令模式启动
  - `a` #进入输入模式，在光标后追加**a**ppend内容
  - `ESC` #退出输入模式，回到命令模式
  - `:wq` #保存write并退出quit

### Easier Ways for Practicing

- `vim`：vi 的升级版
- `vimtutor`：参考教材，这是 Vim 自带的**交互式教程，它不是编辑器，而是教你用编辑器的课本**
- `gvim`：带 GUI 的 vi

### Cursor Movement（命令模式）

- 可以用方向箭头键进行光标移动
- 可以用 `hjkl` 代替箭头

  - `[n] h` #左移 n 位
  - `[n] j` #下移 n 位
  - `[n] k` #上移 n 位
  - `[n] l` #右移 n 位
- 还有许多更高级的光标移动命令

#### 屏幕间移动（命令模式）

- `^F` #**F**orward <u>

one screen

</u>
- `^B` #**B**ack <u>

one screen

</u>
- `^D` #**D**own <u>

half screen

</u>
- `^U` #**U**p <u>

half screen

</u>

#### 行内移动（命令模式）

- `$` #end of current line，到行**末**
- `^` #beginning of text on current line，到本行**第一个非空字符**，主要是跳过Tab或者空格等
- `0` #beginning of current line，到行**首**

#### 单词间移动（命令模式）

- `[n] w` #forward `[n]` **w**ord(s)，按词往前走
- `[n] b` #**b**ack `[n]` word(s)，按词往后走
- `e` #**e**nd of word，走到词最后

#### 搜索跳转

##### 行内字符搜索（命令模式）

- `f character` #forward to next this character，移动到下一个这个字母

##### 全文搜索（命令模式）

- `/ pattern string` #go to matched pattern downward，向下搜索pattern string
- `? pattern string` #go to matched pattern upward，向上搜索pattern string
- 上面这两个和man里面的查找操作是一样的

下面这两个是在`/`  `？`时使用的

- `n`：跳到**下一个**匹配（next）
- `N`：跳到**上一个**匹配（反方向的 next）
- 一般来说，如果小写是对后面进行操作，大写就是反向

#### 行间跳转（命令模式）

- `G` **Go** to last line of file
- `[n] G` go to line `[n]`，Go 到第n行

### Inserting Text

这些命令都是**在命令模式下**按的，只是进入插入模式的位置不同而已

- `i` #**i**nsert text **before the cursor**，在当前的**光标前**插入东西
- `a` #**a**ppend text **after the cursor**，在当前的**光标后**插入东西
- `I` #**I**nsert text **at beginning of line**，在**行首**加入东西
- `A` #**A**ppend text **at end of line**，在**行末**加入东西
- `o` #**o**pen new line **after current line**，在**当前行后面加一行**，插入东西
- `O` #**O**pen new line **before current line**，在**当前行前面加一行**，插入东西

大写一般都是对**行**的操作

### Deleting Text

这些命令是如何**在命令模式下**删东西

- <mark>

`dd`

</mark>

 <mark>

#

</mark>

<mark>

**d**

</mark>

<mark>

elete current line，会删到缓存区buffer，可以用

</mark>

 <mark>

`p`

</mark>

 <mark>

粘贴

</mark>

<mark>

（复制到光标后面）

</mark>

<mark>

，所以删除其实也等于剪切

</mark>
- `[n] dd` or `d [n] d` #delete `[n]` line(s)，`3dd`或者`d3d`从当前行开始删3行
- `[n] dw` #**d**elete `[n]` **w**ord(s)
- `D` #**D**elete from cursor to end of line，从光标删到行尾，一般大写都是对行的操作
- `x` #delete current character，删除**当前**的字符
- `[n] x` #delete `[n]` characters
- `[n] X` #delete previous `[n]` character，删除光标之前的字符，相当于`backspace`

#### Changing Commands

这些命令也都还是**在命令模式下**执行

- `s`/`S` #**S**ubstitute，将该处 character 删除，**并进入插入模式**，等待你输入新的字符，`S`是删除一整行
- `r`，把光标下的字符**直接替换replace成你接下来输入的那一个字符**，但**仍然是命令模式**
- `R`，进入**替换模式**：你打字会持续覆盖后面的字符，直到按`ESC`键退出
- `cw` #**c**hange **w**ord，从光标位置开始，**把“到单词结束”的内容删掉**，然后**进入插入模式**让你输入新词
- `[n]cw` #**c**hange next `[n]` **w**ord(s)，删除n个单词，然后**进入插入模式**让你输入新词
- `c$` #**c**hange from cursor to end of line，从光标位置开始，到**行尾**`$`全部清掉，然后**进入插入模式**
- `~` #change case of character，把光标下字母大小写翻转
- `J` #**J**oin current line and next line，把下一行移到该行后面
- <mark>

`u`

</mark>

 <mark>

#

</mark>

<mark>

**u**

</mark>

<mark>

ndo the last command just done，即撤回

</mark>
- `.` #repeat last change, **redo**，重复上一次动作
- <mark>

`[n]yy`

</mark>

 <mark>

or

</mark>

 <mark>

`y[n]y`

</mark>

 <mark>

#

</mark>

<mark>

**y**

</mark>

<mark>

ank

</mark>

 <mark>

`[n]`

</mark>

 <mark>

**line(s)**

</mark>

 <mark>

to buffer，yank复制

</mark>
- `[n]yw` #**y**ank `[n]` **word(s)** to buffer，复制单词
- <mark>

`p`

</mark>

 <mark>

#

</mark>

<mark>

**p**

</mark>

<mark>

ut yanked or deleted text after cursor，复制到

</mark>

<mark>

光标

</mark>

<mark>

后面

</mark>

<mark>

（如果是一整行，就复制到光标所在行的后面一行）

</mark>
- `P` #**P**ut yanked or deleted text before cursor，复制到前面
- <mark>

`4dd10jp`

</mark>


  - <mark>
  
  #1
  
  </mark>
  
   <mark>
  
  `4dd`
  
  </mark>
  
   <mark>
  
  删除 4 行
  
  </mark>
  - <mark>
  
  #2
  
  </mark>
  
   <mark>
  
  `10j`
  
  </mark>
  
   <mark>
  
  **光标下移 10 行**
  
  </mark>
  - <mark>
  
  #3
  
  </mark>
  
   <mark>
  
  `p`
  
  </mark>
  
   <mark>
  
  将删除的 4 行复制到光标后
  
  </mark>

### Command Line Mode命令行模式

- <mark>

Enter command line mode by typing a

</mark>

 <mark>

`:`

</mark>

<mark>

，输入

</mark>

<mark>

`:`

</mark>

<mark>

可以到命令

</mark>

<mark>

**行**

</mark>

<mark>

模式

</mark>
- **Line indicators** 行定位符

  - `:``20`：移动到第 20 行，如 `:20`
  - `:``.` **current line**：将光标移至本行首
  - `:``$` **last line**：将光标移至**整文**的行末
  - `:``+`, `-`, `.+5`, `-10`：光标向上向下移动几行；`$-3` 意思为光标先移动到最后一行，然后再向上移动 3 行

#### File Manipulation

- <mark>

`:wq`

</mark>

 <mark>

#

</mark>

<mark>

**w**

</mark>

<mark>

rite changes and

</mark>

 <mark>

**q**

</mark>

<mark>

uit

</mark>
- `:w!` # ! **f**orce overwrite of file，即强制保存
- `:q` #**q**uit if no changes made
- <mark>

`:q!`

</mark>

 <mark>

#

</mark>

<mark>

**q**

</mark>

<mark>

uit without saving changes ! ，即强制退出，不保存退出

</mark>
- `:![cmd]` #shell escape，即暂时跳到外面的 shell 里 ! 执行`[cmd]`例如 `:!ls`、`:!pwd`
- `:r [file]` # `r=read` insert file at cursor position，即把其它文件的内容插入到后面，默认会换行

#### Configuring vi Session

- <mark>

`:set all`

</mark>

 <mark>

#display

</mark>

 <mark>

**all**

</mark>

 <mark>

option settings，显示所有的选项设置

</mark>

<mark>

（q退出）

</mark>
- `:set ignorecase` #ignore the case of a character in a search，先设置再搜索，忽略大小写查找，使用 `set noignorecase` 进行关闭
- <mark>

`:set number`

</mark>

 <mark>

#display line numbers，显示行号

</mark>
- <mark>

`:set nonumber`

</mark>

 <mark>

#turn off line numbers，关闭行号显示

</mark>

#### Line Manipulation

- `:number` #locate，移动到对应行
- `:n1,n2 m n3` #**m**ove，将 n1 到 n2 行，移动到 n3 行后的位置，会自动换行
- `:n1,n2 d` #**d**elete

  - `:.,$-2 d` #删除当前行到倒数第 3 行，`.`当前行，`$`最后一行
  - `:1,. d` #删除第 1 行到当前行

#### Substitution

- `:[Addr]s/old-expr/new-string/[g]`
  - `[Addr]`表示“在哪些行做替换”，不写只对**当前行**做
  - `s`：表示替换**s**ubstitude操作，`g` 表示全局**g**lobal替换，省略 option 时**仅对每行第一个匹配串进行替换**
  - `:s/hte/the/g` #当前行所有 hte 换为 the
  - `:2,30s/use/used` #将 2-30 行每行第一个 use 换位 used
  - `:1,$s/Oct\./Nov.` #将 1 到最后一行每行第一个 `Oct.` 换成 `Nov.`。注意，这里将 `.` 视为普通的点，所以文本匹配的是 `Oct.` 而不是 `Oct`
  - `:1,$-3s/Oct\./Nov./g` #将 1 到倒数第 4 行所有 `Oct.` 换成`Nov.`
- ###

##### 1. `:%s/old_exp/new_exp/g`

这是一个最经典的全局替换命令。

- **:**：进入底行模式（Command-line mode）。
- **%**：范围修饰符，表示**全文**（从第一行到最后一行）。
- **s**：代表 `substitute`（替换）。
- **/old_exp/**：查找目标，即你想被换掉的旧字符串或正则表达式。
- **/new_exp/**：替换内容，即你想换成的词。
- **/g**：标志位 `global`（全局）。意味着**替换每一行中出现的所有匹配项**。如果没有这个 `g`，每行只会替换第一个匹配到的词。

**总结：** 在整篇文章中，把所有的 `old_exp` 替换为 `new_exp`。

---

##### 2. `:1,$-3s/Oct\./Nov./g`

这是一个带有限定范围和特殊字符转义的替换命令。

- **1,$-3**：这是指定的**行范围**。

  - `1`：从第 1 行开始。
  - `$`：代表最后一行。
  - `$-3`：代表倒数第 4 行（最后一行往上数 3 行）。
  - 所以这个范围是：**从第 1 行到倒数第 4 行**。
- **s**：替换操作。
- **/Oct\. /**：查找目标。

  - 这里的 `\.` 是关键，因为在正则表达式中 `.` 代表任意字符，所以需要用反斜杠 `\` 进行**转义**，表示匹配真实的“句点”。
  - 即：查找字符串 `Oct.`。
- **/Nov./**：替换为 `Nov.`。
- **/g**：行内全局替换。

**总结：** 在第 1 行到倒数第 4 行的范围内，将所有的 `Oct.` 替换为 `Nov.`。

#### <mark>正则表达式</mark>

Regular Expression** - the basics and examples (meta-characters in REP)

不要将正则表达式与用于匹配文件名的“通配符”（Wildcards）混淆

## 正则表达式 (Regular Expression) 基础笔记

> 整理自 ICCAD_V49_3.pdf (第 18-23 页)

### 简介 (Page 18)

正则表达式（Regular Expressions，简称 RE 或 Regex）是一种强大的文本处理工具。

- **功能**：允许对文本内容进行模式匹配（pattern matching）。
- **构成**：由普通字符（normal characters）和特殊字符（即元字符，meta-characters）组合而成。
- **⚠️ 核心警告**：**切勿将其与 Unix Shell 中用于匹配文件名的“通配符”（Wildcards）混淆！** 两者虽然符号相似，但含义不同。

### 易混淆概念：Shell 通配符 (Wild Cards) (Page 19)

在进入正则之前，必须先明确 Unix Shell 中用于**文件名匹配**的通配符。这些**不是**正则表达式。

<table>
<thead>
  <tr>
    <th>
      符号
    </th>
    
    <th>
      含义
    </th>
    
    <th>
      适用 Shell
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      ?
    </td>
    
    <td>
      匹配指定位置的任意单个字符
    </td>
    
    <td>
      所有
    </td>
  </tr>
  
  <tr>
    <td>
      *
    </td>
    
    <td>
      匹配任意长度的字符串（包括零个字符）
    </td>
    
    <td>
      所有
    </td>
  </tr>
  
  <tr>
    <td>
      <span>
        abc...
      </span>
    </td>
    
    <td>
      匹配括号内的任意一个字符
    </td>
    
    <td>
      所有
    </td>
  </tr>
  
  <tr>
    <td>
      <span>
        a-e
      </span>
    </td>
    
    <td>
      匹配指定范围内的任意一个字符（如 a 到 e）
    </td>
    
    <td>
      所有
    </td>
  </tr>
  
  <tr>
    <td>
      <span>
        !def
      </span>
    </td>
    
    <td>
      匹配除括号内字符以外的任意字符
    </td>
    
    <td>
      sh/bash
    </td>
  </tr>
  
  <tr>
    <td>
      {abc,bcd}
    </td>
    
    <td>
      匹配逗号分隔的字符序列集合（不能有空格）
    </td>
    
    <td>
      bash/csh
    </td>
  </tr>
  
  <tr>
    <td>
      ~
    </td>
    
    <td>
      当前用户的主目录 (Home directory)
    </td>
    
    <td>
      bash/csh
    </td>
  </tr>
  
  <tr>
    <td>
      ~user
    </td>
    
    <td>
      指定用户的主目录
    </td>
    
    <td>
      bash/csh
    </td>
  </tr>
</tbody>
</table>

### 应用场景对比 (Page 20)

<table>
<thead>
  <tr>
    <th>
      特性
    </th>
    
    <th>
      通配符 (Wild Card)
    </th>
    
    <th>
      正则表达式 (Regular Expression)
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      处理对象
    </td>
    
    <td>
      文件名 (File names)
    </td>
    
    <td>
      文本内容 (Text patterns)
    </td>
  </tr>
  
  <tr>
    <td>
      典型命令
    </td>
    
    <td>
      ls, cp, rm (如 ls *.c)
    </td>
    
    <td>
      grep, sed, awk, vi
    </td>
  </tr>
  
  <tr>
    <td>
      编程语言
    </td>
    
    <td>
      Shell 脚本
    </td>
    
    <td>
      Tcl, Perl, Python, C++ 等
    </td>
  </tr>
  
  <tr>
    <td>
      Vi 编辑器
    </td>
    
    <td>
      无
    </td>
    
    <td>
      / (查找), ? (反向查找), <s>
        
      </s>
      
       (替换)
    </td>
  </tr>
</tbody>
</table>

### 正则表达式语法详解 (Page 21-22)

正则表达式主要由三种形式构成：

1. **锚点 (Anchors)**：将模式绑定到行的特定位置（如行首、行尾）。
2. **字符集 (Character sets)**：匹配特定位置的单个字符。
3. **修饰符 (Modifiers)**：指定前一个表达式重复的次数。

#### 核心元字符表

<table>
<thead>
  <tr>
    <th>
      符号
    </th>
    
    <th>
      描述
    </th>
    
    <th>
      示例
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      .
    </td>
    
    <td>
      匹配除换行符以外的任意单个字符
    </td>
    
    <td>
      b.t 匹配 bat, bet, bit
    </td>
  </tr>
  
  <tr>
    <td>
      *
    </td>
    
    <td>
      匹配其前面的元素零次或多次 <br />
      
       (注意：不同于通配符中的“任意字符串”)（+是一次或多次；？是零次或一次）
    </td>
    
    <td>
      ab*c 匹配 ac, abc, abbc...
    </td>
  </tr>
  
  <tr>
    <td>
      <span>
        abc
      </span>
    </td>
    
    <td>
      匹配括号内的任意一个字符
    </td>
    
    <td>
      <span>
        cb
      </span>
      
      at 匹配 cat, bat
    </td>
  </tr>
  
  <tr>
    <td>
      <span>
        a-d
      </span>
    </td>
    
    <td>
      匹配指定范围内的任意一个字符
    </td>
    
    <td>
      <span>
        0-9
      </span>
      
       匹配任意数字
    </td>
  </tr>
  
  <tr>
    <td>
      <span>
        ^abc
      </span>
    </td>
    
    <td>
      取反：匹配不在括号内的任意字符
    </td>
    
    <td>
      <span>
        ^0-9
      </span>
      
       匹配非数字字符
    </td>
  </tr>
  
  <tr>
    <td>
      ^
    </td>
    
    <td>
      行首锚点：表达式必须出现在行开头
    </td>
    
    <td>
      ^Start 匹配以 Start 开头的行
    </td>
  </tr>
  
  <tr>
    <td>
      $
    </td>
    
    <td>
      行尾锚点：表达式必须出现在行末尾
    </td>
    
    <td>
      End$ 匹配以 End 结尾的行
    </td>
  </tr>
  
  <tr>
    <td>
      \
    </td>
    
    <td>
      转义字符：将下一个特殊字符视为普通字符
    </td>
    
    <td>
      . 匹配实际的点号
    </td>
  </tr>
</tbody>
</table>

### 实例分析 (Page 23)

以下是一些常见的正则表达式及其匹配含义：

<table>
<thead>
  <tr>
    <th>
      正则表达式
    </th>
    
    <th>
      匹配含义
    </th>
    
    <th>
      匹配示例
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      cat
    </td>
    
    <td>
      字符串 "cat"
    </td>
    
    <td>
      "cat"
    </td>
  </tr>
  
  <tr>
    <td>
      .at
    </td>
    
    <td>
      任意字符后跟 "at"
    </td>
    
    <td>
      "cat", "rat", "mat", "bat"
    </td>
  </tr>
  
  <tr>
    <td>
      xy*z
    </td>
    
    <td>
      一个 x，后跟零个或多个 y，再跟一个 z
    </td>
    
    <td>
      "xz", "xyz", "xyyz", "xyyyz"
    </td>
  </tr>
  
  <tr>
    <td>
      ^cat
    </td>
    
    <td>
      出现在行首的 cat
    </td>
    
    <td>
      "category..." (位于行首)
    </td>
  </tr>
  
  <tr>
    <td>
      cat$
    </td>
    
    <td>
      出现在行尾的 cat
    </td>
    
    <td>
      "...tomcat" (位于行尾)
    </td>
  </tr>
  
  <tr>
    <td>
      *
    </td>
    
    <td>
      字符星号本身 (Literal asterisk)
    </td>
    
    <td>
      "*"
    </td>
  </tr>
  
  <tr>
    <td>
      <span>
        cC
      </span>
      
      at
    </td>
    
    <td>
      "cat" 或者 "Cat"
    </td>
    
    <td>
      "cat", "Cat"
    </td>
  </tr>
  
  <tr>
    <td>
      <span>
        ^a-zA-Z
      </span>
    </td>
    
    <td>
      任意非字母字符
    </td>
    
    <td>
      "1", "@", " " (空格)
    </td>
  </tr>
  
  <tr>
    <td>
      <span>
        0-9
      </span>
      
      $
    </td>
    
    <td>
      以数字结尾的行
    </td>
    
    <td>
      "Item 5", "Year 2023"
    </td>
  </tr>
  
  <tr>
    <td>
      [A-Z]<span>
        A-Z
      </span>
      
      *
    </td>
    
    <td>
      一个或多个大写字母
    </td>
    
    <td>
      "A", "US", "UNIX"
    </td>
  </tr>
  
  <tr>
    <td>
      <span>
        A-Z
      </span>
      
      *
    </td>
    
    <td>
      零个或多个大写字母 (匹配任何内容，即使为空)
    </td>
    
    <td>
      "" (空串), "ABC"
    </td>
  </tr>
</tbody>
</table>

*注：此文档基于 ICCAD_V49_3.pdf 生成，旨在辅助理解 Unix 环境下的文本处理基础。*
