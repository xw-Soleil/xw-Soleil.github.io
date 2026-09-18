# History & Meta Characters

> Unix/Linux 发展简史与 Shell 元字符

## Meta Characters

> 每年附加题都考，放一开始，多看看

### 括号&线条

- `{}` ： `curly bracket`（curly - 卷曲的）
- `[]` ： `square bracket`（square - 直角的）
- `()` ： `parenthesis` （记忆：parent-hesis ）
- `<` ： `less-than sign`
- `>` ： `gr``e``ater-than sign`
- `|` ： `vertical bar`（vertical - 竖直的）
- `/` ： `slash`（注意是右上往左下）
- `\` ： `backslash`

### 标点

- `,` ： `comma`
- `.` ： `dot / period`
- `:` ： `colon`
- `;` ： `semicolon`（和semiconductor一个道理，半个冒号）
- <mark>

`'`

</mark>

 <mark>

：

</mark>

 <mark>

`apostrophe`

</mark>

<mark>

（/əˈpɒstrəfi/）

</mark>
- `"` ： `double quotation mark`
- `?` ： `question mark`

### 数学符号

- `+` ： `plus sign`
- `-` ： `hyphen-minus`（连接单词时叫hyphen(连字符)，算数为minus）
- `=` ： `equal sign`
- `*` ： `asterisk`（aster希腊语小星星）
- `%` ： `percent sign`
- `^` ： `caret`
- `&` ： `ampersand`（词源：and per se and 念快一点就是ampersand）

### 特殊符号

- `~` ： `tilde`
- ````` ： `backquote`
- `!` ： `exclamation mark` （exclamation - 惊叹）
- `@` ： `at sign`
- `#` ： `number sign` （也叫hash）
- `$` ： `dollar sign`
- `_` ： `under score`

### IC Thread

`Shockley Lab -> Fairchild -> Intel -> TSMC`

人物：`Shockley`、`Robert Noyce`、`Gordon Moore`、`Jean Hoerni`

> Shockley 当老板，
> 
> Noyce 和 Moore 不爽，拉上 Hoerni 出来做 Fairchild，
> 
> 后来Noyce 和 Moore 又再一起跳出来做 Intel，
> 
> 后来产业发展需要晶圆代工，TSMC 出场。

于是就可以这样记：

`Shockley Lab(Shockley + Noyce + Moore) -> Fairchild(Noyce + Moore + Hoerni) -> Intel(Noyce + Moore) -> TSMC`

#### Shockley Lab(Shockley + Noyce + Moore)

- **Late 1940s** : Robert Noyce experiments with transistors while a physics major（40年代的Noyce还在学校玩晶体管）
- **1951** : Shockley develops junction transistor for production（51年Shockley做出可量产的**结型晶体管**）
- <mark>

**1956**

</mark>

 <mark>

:

</mark>

 Shockley Semiconductor Laboratory is founded in Silicon Valley, Robert Noyce and Gordon Moore join（56年<mark>

Shockley Semiconductor Lab

</mark>

 在硅谷成立，Noyce & Moore 加入）

#### Fairchild ｜ 仙童(Noyce + Moore + Hoerni)

- <mark>

**1957**

</mark>

 <mark>

:

</mark>

 Noyce leaves Shockley Semiconductor Labs to form Fairchild Semiconductor with Jean Hoerni and Gordon Moore（57年Noyce 不爽 Shockley 管理，拉 Hoerni & Moore 出来做 <mark>

**Fairchild**

</mark>

）
- **1959** : Hoerni and Noyce invent diffusing, isolation and connection techniques for first true planar IC（59年Hoerni and Noyce发明**真正平面 IC**（扩散、隔离、互连技术））
- **1961** : TI and Fairchild introduce the first logic ICs ($50 in quantity)（61年和 TI 一起做出**第一批逻辑 IC**（量产后每片 50 美元））
- **1968** : Fairchild’s first MOS integrated circuit product – a dual J-K flip-flop（68年Fairchild 出第一款 **MOS IC**（双 JK 触发器））

#### Intel(Noyce + Moore)

- <mark>

**1968**

</mark>

 : Noyce and Moore leave Fairchild and form Intel（68年Noyce、Moore 再次出走，成立 <mark>

**Intel**

</mark>

）
- **1970** : Intel starts selling 1K-bit RAM, the 1103 ($21)（70年卖 **1K-bit RAM 1103**）
- **1971** : Intel introduces the first 4-bit microprocessor, the 4004, originally designed as a special circuit for Busicom (2300 transistors)（70年做出 **4004，首个 4 位微处理器**（给 Busicom，2300 个晶体管））
- **1985** : Intel begins focusing on microprocessor products（85年 Intel 开始**主攻微处理器**，不再分散做别的）

#### TSMC

- <mark>

**1987**

</mark>

 <mark>

:

</mark>

 TSMC is founded (supports fabless model)（TSMC台积电成立，支持 **fabless** 模式（自己只做代工，不做品牌芯片））

### PC/OS Thread

`Apple -> IBM -> Microsoft -> GNU/Linux`

> Apple 先搞个人电脑
> 
> IBM 把 PC 标准化
> 
> 微软靠操作系统称王
> 
> 最后 GNU/Linux 代表自由开源阵营

#### Apple(Steve Jobs, Steve Wozniak, John Sculley(后来 CEO))

- **1976** : Apple I
- **1977** : Apple II
- **1985** : Macintosh麦金塔

#### IBM

- **1981** : IBM PC
- **1998** : IBM Austin Res. Lab announces 1GHz experimental microprocessor（98年IBM Austin 实验室做出 1GHz 实验微处理器）

#### Microsoft

- Bill Gates, Paul Allen

IBM 出 PC，微软卖系统

#### GNU/Linux

- Richard Stallman, Linus Torvalds

Stallman 搞 GNU，Torvalds 写 Linux，合体叫 GNU/Linux（自由开源的 OS 世界）

### Big-3 of EDA(Mentor Graphics)

EDA的三巨头

- **Synopsys** (SNPS)美国，最近这几年都是市场份额最大的EDA公司
- **Cadence** (CDNS)美国
- **Mentor Graphics** (Siemens后来被德国西门子收购)

### ICCAD vs. EDA, subtle differences?

#### **EDA: Electronic Design Automation**

电子设计自动化。是指利用计算机辅助设计(CAD)软件，来完成超大规模集成电路(VLSI)芯片设计。

#### **ICCAD: Integrated Circuit Computer** <mark>

**Aided**

</mark>

 **Design**

集成电路计算机辅助设计。

#### **Subtle differences**

**ICCAD 是 EDA 的子集**，EDA 面向所有电子设计的自动化辅助工具，而 ICCAD 则面向电子设计中的集成电路设计，之所以经常讲两者混为一谈，是因为 ICCAD 在 EDA 中的占比非常高，有时便会弱化二者之间的差别。（电路设计软件AD属于EDA软件，但不属于ICCAD软件）

### Open-source EDA tools and using experience?

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ICCAD/HistoryMetaCharacters-01.webp)

<table>
<thead>
  <tr>
    <th>
      设计阶段 (Design Stage)
    </th>
    
    <th>
      商业工具代表 (Commercial/Proprietary)
    </th>
    
    <th>
      开源工具代表 (Open Source)
    </th>
    
    <th>
      备注
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      逻辑综合 (Logic Synthesis)
    </td>
    
    <td>
      Synopsys Design Compiler
    </td>
    
    <td>
      Yosys, Surelog, ABC, UHDM
    </td>
    
    <td>
      负责将RTL代码（如Verilog）转换为门级网表。
    </td>
  </tr>
  
  <tr>
    <td>
      布局布线 (P&R)
    </td>
    
    <td>
      Cadence Innovus
    </td>
    
    <td>
      OpenROAD
    </td>
    
    <td>
      负责将网表转换为物理版图，这是数字后端的关键步骤。
    </td>
  </tr>
  
  <tr>
    <td>
      物理验证 (DRC, LVS, PEX)
    </td>
    
    <td>
      Calibre (西门子/Mentor)
    </td>
    
    <td>
      Magic, Netgen, KLayout
    </td>
    
    <td>
      负责检查版图是否符合工艺规则(DRC)以及与电路图是否一致(LVS)。
    </td>
  </tr>
  
  <tr>
    <td>
      电路仿真 (Simulation)
    </td>
    
    <td>
      hspice, spectre
    </td>
    
    <td>
      Ngspice, Xyce
    </td>
    
    <td>
      负责对电路进行模拟仿真（主要是SPICE级仿真）。
    </td>
  </tr>
</tbody>
</table>

About using experience: 小任务里面用过KLayout还有Ngspice

还有OpenROAD flow

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/ICCAD/HistoryMetaCharacters-02.webp)

Question like 写出三个开源ICCAD软件

---

### A question in early years

下面这些是和上面有些关联的，记下来就可以顺带都了解了

- Robert Noyce → Fairchild, Intel
- Gordon Moore → Fairchild, Intel
- Steve Jobs → Apple, **Macintosh & NeXT**（后面这个，麦金塔是Steve Jobs在Apple时主推的产品，革命性的图形界面，一代经典了属于是，NeXT是Steve后来被赶出Apple的时候创办的公司，后来Apple收购了它，于是Steve又回到了Apple，NeXT 的操作系统技术变成了之后的 Mac OS X / iOS 的基础）
- **Steve Wozniak → Apple**（Apple的创办者有两个Steve，这是第二个）
- Bill Gates → Microsoft
- **Paul Allen → Microsoft**（相对Bill Gates没这么有名，记一下Paul Allen，微软的另一个创始人，也就是书呆子的胜利最开始介绍的拥有开拓者的人）

后面这些需要额外背一下的

- **Linus Torvalds → Linux & git**（伟大，无需多言）
- **Dennis Ritchie → Unix, C Language**（这个老师群里发的推文介绍过，C语言之父同时还是Unix之父）
- **Ken Thompson → Unix, C Language**（里奇的好基友，推文里也有写，关于Unix和C，他也有很大功劳）
- **Richard Stallman → GNU & FSF, gcc**（自由软件教父 → GNU 系统 + FSF 基金会 + gcc 编译器）
- **Larry Ellison → Oracle**（拉里·埃里森 - 甲骨文，搞数据库的）
- **Bill Joy → vi & CShell**（原来vi和Cshell就是他搞的，Bill 乐）

<table>
<thead>
  <tr>
    <th>
      人物
    </th>
    
    <th>
      核心成就 / 公司 / 技术
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      Steve Jobs
    </td>
    
    <td>
      Apple, Macintosh & NeXT
    </td>
  </tr>
  
  <tr>
    <td>
      Steve Wozniak
    </td>
    
    <td>
      Apple (联合创始人，Apple I & II 的设计者)
    </td>
  </tr>
  
  <tr>
    <td>
      Bill Gates
    </td>
    
    <td>
      Microsoft
    </td>
  </tr>
  
  <tr>
    <td>
      Paul Allen
    </td>
    
    <td>
      Microsoft (联合创始人)
    </td>
  </tr>
  
  <tr>
    <td>
      Larry Ellison
    </td>
    
    <td>
      Oracle
    </td>
  </tr>
  
  <tr>
    <td>
      Gordon Moore
    </td>
    
    <td>
      Intel, Fairchild (摩尔定律提出者)
    </td>
  </tr>
  
  <tr>
    <td>
      Robert Noyce
    </td>
    
    <td>
      Intel, Fairchild (集成电路发明者之一)
    </td>
  </tr>
  
  <tr>
    <td>
      Dennis Ritchie
    </td>
    
    <td>
      C Language, Unix
    </td>
  </tr>
  
  <tr>
    <td>
      Ken Thompson
    </td>
    
    <td>
      C Language Unix, B语言, Go语言
    </td>
  </tr>
  
  <tr>
    <td>
      Linus Torvalds
    </td>
    
    <td>
      Linux & git
    </td>
  </tr>
  
  <tr>
    <td>
      Richard Stallman
    </td>
    
    <td>
      GNU & FSF, gcc
    </td>
  </tr>
  
  <tr>
    <td>
      Bill Joy
    </td>
    
    <td>
      vi & CShell, Sun Microsystems, Java (核心推动者) NFS
    </td>
  </tr>
</tbody>
</table>

### Three questions in homework1

#### Question 1

> Where does Gordon Moore sit and what does he say in the video? (Triumph of Nerds)

Gordon Moore appears **around 14'16 in the episode 1 of 3**. He was sitting in the **Chairman's cubicle** in Intel, which is notable for having no door.

He said:

> In a business like this, people with the power are the ones that have the understanding of what's going on not necessarily the ones on top. It's very important that those people that have the knowledge are the ones that make the decisions. So we set up something where everyone who had the knowledge had an equal say in what was going on.

---

#### Question 2

> What is Xerox PARC? Steve Jobs has mentioned 3 innovations from it, what are the other two besides GUI? (Triumph of Nerds)

Xerox PARC(Palo Alto Research Center) appearing **around 5'18 in the episode 3 of 3**, was a **research center set up by Xerox**, <u>

the copier company

</u>

, in 1971 in Palo Alto, south of San Francisco. The management at Xerox had a "sinking feeling" that if people started reading from computer screens instead of paper, their business would be in trouble. Therefore, they established PARC to **"dominate the paperless Office of the future"**. At PARC, researchers were given "unlimited resources and protected them from commercial pressures", fostering an environment of "total intellectual Freedom" where they were told to "go create the new world".

During his visit to Xerox PARC, Steve Jobs was shown three innovations. He was so **"blinded by the first one"**, the **Graphical User Interface (GUI)**, that he "didn't even really see the other two" at first. The other two innovations he mentioned were:

- **Object-oriented programming**.
- **A networked computer system** where over 100 Alto computers were all networked, using email and other features.

---

#### Question 3

> What is the overall opinion of Steve Jobs towards Bill Gates? (Triumph of Nerds)

This appears around **around 40'01 in the episode 3 of 3**. Steve Jobs' main critique is aimed at Microsoft as a company and the quality of its products, rather than at Bill Gates personally.

Jobs' primary issue is that **Microsoft has "absolutely no taste"**. He elaborates on this by stating, "they don't think of original ideas and they don't bring much culture into their product". He clarifies that his issue is not with the company's achievements, stating, "I am saddened not by Microsoft success I have no problem with their success they've earned their success for the most part I have a problem with the fact that they just make really Third Rate products".

---
