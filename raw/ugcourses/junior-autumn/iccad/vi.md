# Vi

> Vi 编辑器基础操作

## Editors

- Programs that let you interactively edit text files，即交互式编辑文本文件的程序有：

  - DOS: `edlin`, `edit`
  - Windows: `notepad`, `wordpad`
  - Unix: `ed`, `vi`, `vim`
  - <mark>
  
  GNU:
  
  </mark>
  
   <mark>
  
  `emacs`
  
  </mark>
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
  - <mark>
  
  只有在 Insert mode 下，才可以做文字输入，
  
  </mark>
  
  <mark>
  
  **按**
  
  </mark>
  
   <mark>
  
  **[ESC]**
  
  </mark>
  
   <mark>
  
  **键可回到命令模式**
  
  </mark>
  - 通过输入几个插入命令之一来进入
- 简单 `vi` 示例

  - `vi tmp.txt` #在命令模式启动
  - `a` #进入输入模式，在光标后追加**a**ppend内容
  - `ESC` #退出输入模式，回到命令模式
  - `:wq` #保存write并退出quit

### Easier Ways for Practicing

- <mark>

`vim`

</mark>

<mark>

：vi 的升级版

</mark>
- `vimtutor`：参考教材，这是 Vim 自带的**交互式教程，它不是编辑器，**<mark>

**而是教你用编辑器的课本**

</mark>
- <mark>

`gvim`

</mark>

<mark>

：带 GUI 的 vi

</mark>

### Cursor Movement（命令模式）

- 可以用方向箭头键进行光标移动
- <mark>

可以用

</mark>

 <mark>

`hjkl`

</mark>

 <mark>

代替箭头

</mark>


  - <mark>
  
  `[n] h`
  
  </mark>
  
   <mark>
  
  #左移 n 位
  
  </mark>
  - <mark>
  
  `[n] j`
  
  </mark>
  
   <mark>
  
  #下移 n 位
  
  </mark>
  - <mark>
  
  `[n] k`
  
  </mark>
  
   <mark>
  
  #上移 n 位
  
  </mark>
  - <mark>
  
  `[n] l`
  
  </mark>
  
   <mark>
  
  #右移 n 位
  
  </mark>
- 还有许多更高级的光标移动命令

#### 屏幕间移动（命令模式）

- <mark>

`^F`

</mark>

 <mark>

#

</mark>

<mark>

**F**

</mark>

<mark>

orward

</mark>

 <mark>
<u>

one screen

</u>
</mark>
- <mark>

`^B`

</mark>

 <mark>

#

</mark>

<mark>

**B**

</mark>

<mark>

ack

</mark>

 <mark>
<u>

one screen

</u>
</mark>
- <mark>

`^D`

</mark>

 <mark>

#

</mark>

<mark>

**D**

</mark>

<mark>

own

</mark>

 <mark>
<u>

half screen

</u>
</mark>
- <mark>

`^U`

</mark>

 <mark>

#

</mark>

<mark>

**U**

</mark>

<mark>

p

</mark>

 <mark>
<u>

half screen

</u>
</mark>

#### 行内移动（命令模式）

- <mark>

`$`

</mark>

 <mark>

#end of current line，到行

</mark>

<mark>

**末**

</mark>
- <mark>

`^`

</mark>

 <mark>

#beginning of text on current line，到本行

</mark>

<mark>

**第一个非空字符**

</mark>

<mark>

，主要是跳过Tab或者空格等

</mark>
- <mark>

`0`

</mark>

 <mark>

#beginning of current line，到行

</mark>

<mark>

**首**

</mark>

#### 单词间移动（命令模式）

- `[n] w` #forward `[n]` **w**ord(s)，跳到下第n个词开头
- `[n] b` #**b**ack `[n]` word(s)，跳到上第n个词开头
- `e` #**e**nd of word，走到当前光标所在的这个词的最后

#### 搜索跳转

##### 行内字符搜索（命令模式）

- `f character` #forward to next this character，移动到下一个这个字母

##### 全文搜索（命令模式）

- <mark>

`/ pattern string`

</mark>

 <mark>

#go to matched pattern

</mark>

 <mark>

**downward**

</mark>

<mark>

，向下搜索pattern string

</mark>
- <mark>

`? pattern string`

</mark>

 <mark>

#go to matched pattern

</mark>

 <mark>

**upward**

</mark>

<mark>

，向上搜索pattern string

</mark>
- 上面这两个和man里面的查找操作是一样的

<mark>

下面这两个是在

</mark>

<mark>

`/`

</mark>

  <mark>

`？`

</mark>

<mark>

时使用的

</mark>



- <mark>

`n`

</mark>

<mark>

：跳到

</mark>

<mark>

**下一个**

</mark>

<mark>

匹配（next）

</mark>
- <mark>

`N`

</mark>

<mark>

：跳到

</mark>

<mark>

**上一个**

</mark>

<mark>

匹配（反方向的 next）

</mark>
- <mark>

一般来说，如果小写是对后面进行操作，大写就是反向

</mark>

#### 行间跳转（命令模式）

- `G` **Go** to last line of file
- `[n] G` go to line `[n]`，Go 到第n行

### Inserting Text

这些命令都是**在命令模式下**按的，只是进入插入模式的位置不同而已

- <mark>

`i`

</mark>

 <mark>

#

</mark>

<mark>

**i**

</mark>

<mark>

nsert text

</mark>

 <mark>

**before the cursor**

</mark>

<mark>

，在当前的

</mark>

<mark>

**光标前**

</mark>

<mark>

插入东西

</mark>
- <mark>

`a`

</mark>

 <mark>

#

</mark>

<mark>

**a**

</mark>

<mark>

ppend text

</mark>

 <mark>

**after the cursor**

</mark>

<mark>

，在当前的

</mark>

<mark>

**光标后**

</mark>

<mark>

插入东西

</mark>
- <mark>

`I`

</mark>

 <mark>

#

</mark>

<mark>

**I**

</mark>

<mark>

nsert text

</mark>

 <mark>

**at beginning of line**

</mark>

<mark>

，在

</mark>

<mark>

**行首**

</mark>

<mark>

加入东西

</mark>

  <mark>

**第一个非空字符**

</mark>
- <mark>

`A`

</mark>

 <mark>

#

</mark>

<mark>

**A**

</mark>

<mark>

ppend text

</mark>

 <mark>

**at end of line**

</mark>

<mark>

，在

</mark>

<mark>

**行末**

</mark>

<mark>

加入东西

</mark>
- <mark>

`o`

</mark>

 <mark>

#

</mark>

<mark>

**o**

</mark>

<mark>

pen new line

</mark>

 <mark>

**after current line**

</mark>

<mark>

，在

</mark>

<mark>

**当前行后面加一行**

</mark>

<mark>

，插入东西

</mark>
- <mark>

`O`

</mark>

 <mark>

#

</mark>

<mark>

**O**

</mark>

<mark>

pen new line

</mark>

 <mark>

**before current line**

</mark>

<mark>

，在

</mark>

<mark>

**当前行前面加一行**

</mark>

<mark>

，插入东西

</mark>

<mark>

大写一般都是对

</mark>

<mark>

**行**

</mark>

<mark>

的操作

</mark>



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
- `P` #**P**ut yanked or deleted text before cursor，复制到前面，小写对后操作，大写一般就是对前面操作
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

  <mark>

或者

</mark>

<mark>

`:set nu`

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

#### <mark>Substitution</mark>

- `:[Addr]s/old-expr/new-string/[g]`
  - `[Addr]`表示“在哪些行做替换”，不写只对**当前行**做
  - `s`：表示替换**s**ubstitude操作，`g` 表示全局**g**lobal替换，省略 option 时**仅对每行第一个匹配串进行替换**
  - `:s/hte/the/g` #当前行所有 hte 换为 the
  - `:2,30s/use/used` #将 2-30 行每行第一个 use 换位 used
  - `:1,$s/``Oct\.``/Nov.` #将 1 到最后一行每行第一个 `Oct.` 换成 `Nov.`。注意，这里将 `.` 视为普通的点，所以文本匹配的是 `Oct.` 而不是 `Oct`
  - `:1,$-3s/Oct\./Nov./g` #将 1 到**倒数第 4 行**所有 `Oct.` 换成`Nov.`
