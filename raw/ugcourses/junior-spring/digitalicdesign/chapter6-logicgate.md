# Chapter 6：逻辑门 Logic Gate

> 静态与动态 CMOS 电路风格的对比，以及各类组合逻辑门设计的取舍。

## **CMOS 电路风格**

**静态 CMOS** —— 输出通过一条低电阻路径连接到 **V_DD** 或 **GND**

**特点：**噪声容限高；输出阻抗低，输入阻抗高；在稳态时，V_DD 和 GND 之间不存在直接导通通路；延迟取决于负载电容和晶体管电阻

**动态 CMOS** —— 依靠高阻抗电路节点上的电容，对信号值进行临时存储

**特点：**门电路更简单、速度更快；对噪声更敏感

## 逻辑门的完备性

若函数集f1、f2 ，...  是**完备**的，则意味着所有布尔函数均可通过这些函数的组合生成。

NAND是完备集；NOR是完备集；{AND，OR}则非完备集。传输门不构成完备集。

> 若逻辑门集非完备，则无法实现任意逻辑设计。

## 静态互补型CMOS | Static Complementary CMOS

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter6-LogicGate-01.webp)

**Pull-up network (PUN) 上拉网络使用PMOS；Pull-down network (PDN) 下拉网络使用NMOS**

原因如下图：见课本P157

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter6-LogicGate-02.webp)

上拉网络和下拉网络属于**对偶网络。**N输入静态逻辑门的晶体管数量：**2N。**

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/DigitalICDesign/Chapter6-LogicGate-03.webp)

---

### CMOS组合逻辑电路总结

这页笔记的核心是**对比各种CMOS组合逻辑的优缺点**，分为**静态**和**动态**两大类。

区分标准：①是否有从V_DD到GND的直流通路；②是否需要CLK。

#### 一、静态逻辑（无CLK）

<table>
<thead>
  <tr>
    <th>
      风格
    </th>
    
    <th>
      门数
    </th>
    
    <th>
      抗噪
    </th>
    
    <th>
      静态功耗
    </th>
    
    <th>
      轨至轨
    </th>
    
    <th>
      有/无比
    </th>
    
    <th>
      备注
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      互补CMOS
    </td>
    
    <td>
      2N
    </td>
    
    <td>
      好
    </td>
    
    <td>
      无
    </td>
    
    <td>
      ✓强
    </td>
    
    <td>
      无比
    </td>
    
    <td>
      最经典，但晶体管多
    </td>
  </tr>
  
  <tr>
    <td>
      伪NMOS
    </td>
    
    <td>
      N+1
    </td>
    
    <td>
      差
    </td>
    
    <td>
      有
    </td>
    
    <td>
      非0→V_DD
    </td>
    
    <td>
      有比
    </td>
    
    <td>
      省管子，但有静态功耗
    </td>
  </tr>
  
  <tr>
    <td>
      DCVSL
    </td>
    
    <td>
      2N+2
    </td>
    
    <td>
      好
    </td>
    
    <td>
      无
    </td>
    
    <td>
      ✓
    </td>
    
    <td>
      有
    </td>
    
    <td>
      管子多，消除时差问题
    </td>
  </tr>
  
  <tr>
    <td>
      PT（传输管）
    </td>
    
    <td>
      N
    </td>
    
    <td>
      差
    </td>
    
    <td>
      有
    </td>
    
    <td>
      衰减(V_DD−V_th)
    </td>
    
    <td>
      无
    </td>
    
    <td>
      阈值损失，不可再生
    </td>
  </tr>
  
  <tr>
    <td>
      CPL
    </td>
    
    <td>
      2N+反
    </td>
    
    <td>
      较差
    </td>
    
    <td>
      有(反相器上)
    </td>
    
    <td>
      ✓反
    </td>
    
    <td>
      无
    </td>
    
    <td>
      互补传输管逻辑
    </td>
  </tr>
  
  <tr>
    <td>
      PT->(电平恢复器)
    </td>
    
    <td>
      N+3
    </td>
    
    <td>
      较好
    </td>
    
    <td>
      无
    </td>
    
    <td>
      ✓反
    </td>
    
    <td>
      有
    </td>
    
    <td>
      解决PT阈值损失
    </td>
  </tr>
  
  <tr>
    <td>
      PT->TG
    </td>
    
    <td>
      t+t
    </td>
    
    <td>
      好
    </td>
    
    <td>
      无
    </td>
    
    <td>
      ✓反
    </td>
    
    <td>
      无
    </td>
    
    <td>
      NMOS+PMOS并联，无阈值损失
    </td>
  </tr>
</tbody>
</table>

**关键取舍**：互补CMOS最优但管子数2N最多；伪NMOS/PT省管子但牺牲摆幅和功耗；TG是传输管的最佳改进。

#### 二、动态逻辑（需CLK）

<table>
<thead>
  <tr>
    <th>
      风格
    </th>
    
    <th>
      门数
    </th>
    
    <th>
      抗噪
    </th>
    
    <th>
      轨至轨
    </th>
    
    <th>
      有/无比
    </th>
    
    <th>
      备注
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      普通动态
    </td>
    
    <td>
      N+2
    </td>
    
    <td>
      弱
    </td>
    
    <td>
      ✓
    </td>
    
    <td>
      无
    </td>
    
    <td>
      管子数最少，频率最低限制
    </td>
  </tr>
  
  <tr>
    <td>
      动态+泄露器
    </td>
    
    <td>
      +
    </td>
    
    <td>
      ↑增强
    </td>
    
    <td>
      ✓
    </td>
    
    <td>
      有(弱有比)
    </td>
    
    <td>
      改善抗噪
    </td>
  </tr>
  
  <tr>
    <td>
      多米诺(多级)
    </td>
    
    <td>
      +2(反)
    </td>
    
    <td>
      ↑
    </td>
    
    <td>
      ✓
    </td>
    
    <td>
      无(加泄露器有)
    </td>
    
    <td>
      非反向逻辑,Domino
    </td>
  </tr>
  
  <tr>
    <td>
      无脚无预充
    </td>
    
    <td>
      --
    </td>
    
    <td>
      弱
    </td>
    
    <td>
      ✓
    </td>
    
    <td>
      无
    </td>
    
    <td>
      预充电时间长，功耗↑↑
    </td>
  </tr>
  
  <tr>
    <td>
      双轨多扇出
    </td>
    
    <td>
      2×
    </td>
    
    <td>
      ↑↑
    </td>
    
    <td>
      ✓(PMOS)
    </td>
    
    <td>
      无
    </td>
    
    <td>
      解决非反向问题，功耗↑↑
    </td>
  </tr>
</tbody>
</table>

**关键取舍**：动态逻辑管子少、速度快，但抗噪差（电荷泄漏、电荷分享）；Domino级联解决了只能实现反向逻辑的问题；双轨进一步解决但面积和功耗翻倍。

---

#### 一句话总结

> **静态逻辑稳但慢（管子多），动态逻辑快但脆（抗噪差）**。各种变体都是在**速度、面积、功耗、摆幅、抗噪**之间做trade-off。

### 一、静态逻辑（无CLK）

<table>
<thead>
  <tr>
    <th>
      风格
    </th>
    
    <th>
      门数
    </th>
    
    <th>
      抗噪
    </th>
    
    <th>
      静态功耗
    </th>
    
    <th>
      轨至轨
    </th>
    
    <th>
      有/无比
    </th>
    
    <th>
      备注
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      互补CMOS
    </td>
    
    <td>
      2N
    </td>
    
    <td>
      很好
    </td>
    
    <td>
      无
    </td>
    
    <td>
      √强
    </td>
    
    <td>
      无比
    </td>
    
    <td>
      最经典、最稳健，但晶体管数最多
    </td>
  </tr>
  
  <tr>
    <td>
      伪NMOS
    </td>
    
    <td>
      N+1
    </td>
    
    <td>
      较差
    </td>
    
    <td>
      有
    </td>
    
    <td>
      非严格满摆幅（低电平抬高）
    </td>
    
    <td>
      有比
    </td>
    
    <td>
      省管子，但有静态功耗，噪声裕量下降
    </td>
  </tr>
  
  <tr>
    <td>
      DCVSL
    </td>
    
    <td>
      2N+2
    </td>
    
    <td>
      较好
    </td>
    
    <td>
      无
    </td>
    
    <td>
      √
    </td>
    
    <td>
      有比
    </td>
    
    <td>
      差分+正反馈，同时输出互补信号；满摆幅，但尺寸关系仍重要
    </td>
  </tr>
  
  <tr>
    <td>
      PT（传输管）
    </td>
    
    <td>
      N
    </td>
    
    <td>
      差
    </td>
    
    <td>
      与后级连接有
    </td>
    
    <td>
      衰减（约 (V_-V_)）
    </td>
    
    <td>
      无比
    </td>
    
    <td>
      阈值损失、不可再生，不适合长链级联
    </td>
  </tr>
  
  <tr>
    <td>
      CPL
    </td>
    
    <td>
      2N+反相器/恢复器
    </td>
    
    <td>
      中等偏好
    </td>
    
    <td>
      与后级连接有
    </td>
    
    <td>
      恢复后可满摆幅
    </td>
    
    <td>
      无比
    </td>
    
    <td>
      互补传输管逻辑
    </td>
  </tr>
  
  <tr>
    <td>
      PT→电平恢复器
    </td>
    
    <td>
      N+3
    </td>
    
    <td>
      较好
    </td>
    
    <td>
      基本无
    </td>
    
    <td>
      √/反
    </td>
    
    <td>
      有比（需尺寸配合）
    </td>
    
    <td>
      解决 PT 阈值损失，但会增加内部电容与设计复杂度
    </td>
  </tr>
  
  <tr>
    <td>
      PT→TG
    </td>
    
    <td>
      2N
    </td>
    
    <td>
      好
    </td>
    
    <td>
      无
    </td>
    
    <td>
      √/反
    </td>
    
    <td>
      无比
    </td>
    
    <td>
      NMOS+PMOS 并联，无阈值损失；是传输逻辑里更稳健的实现
    </td>
  </tr>
</tbody>
</table>

这里的关键修正是：Rabaey 对 **PT** 的表述不是“天然就有静态功耗”，而是**它本体主要问题是阈值损失和不可再生；当退化高电平去驱动后级 CMOS 反相器时，可能出现静态电流**。另外，**CPL 的全名就是 Complementary Pass-Transistor Logic**，并且书里明确说差分结构对噪声鲁棒性有利，所以不宜简单写成“较差”。DCVSL 则确实是**满摆幅、无静态功耗**，但仍属于 **ratioed** 风格，不能和互补 CMOS 的鲁棒性完全画等号。

### 二、动态逻辑（需CLK）

<table>
<thead>
  <tr>
    <th>
      风格
    </th>
    
    <th>
      门数
    </th>
    
    <th>
      抗噪
    </th>
    
    <th>
      轨至轨
    </th>
    
    <th>
      有/无比
    </th>
    
    <th>
      备注
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      普通动态
    </td>
    
    <td>
      N+2
    </td>
    
    <td>
      弱
    </td>
    
    <td>
      √
    </td>
    
    <td>
      无比
    </td>
    
    <td>
      管子数少、速度高，但需最小时钟频率
    </td>
  </tr>
  
  <tr>
    <td>
      动态 + 弱保持器（bleeder / keeper）
    </td>
    
    <td>
      +1
    </td>
    
    <td>
      增强
    </td>
    
    <td>
      √
    </td>
    
    <td>
      视实现而定**
    </td>
    
    <td>
      改善抗泄漏、抗噪；实现不当会引入静态功耗或弱 ratio 问题
    </td>
  </tr>
  
  <tr>
    <td>
      多米诺（多级）
    </td>
    
    <td>
      +2（含静态反相器）
    </td>
    
    <td>
      中等
    </td>
    
    <td>
      √
    </td>
    
    <td>
      无比
    </td>
    
    <td>
      便于级联，但只能实现非反向逻辑
    </td>
  </tr>
  
  <tr>
    <td>
      去 evaluation 管的 Domino（footless）
    </td>
    
    <td>
      N+1
    </td>
    
    <td>
      弱
    </td>
    
    <td>
      √
    </td>
    
    <td>
      无比
    </td>
    
    <td>
      会出现 ripple precharge，还可能带来额外静态/短路功耗，一般不推荐
    </td>
  </tr>
  
  <tr>
    <td>
      双轨 Domino（dual-rail / differential）
    </td>
    
    <td>
      约 2×
    </td>
    
    <td>
      较好
    </td>
    
    <td>
      √
    </td>
    
    <td>
      无比
    </td>
    
    <td>
      解决“只能非反向”问题，但功耗更高，因为每周期总有一轨发生 0→1
    </td>
  </tr>
  
  <tr>
    <td>
      多输出 Domino（multiple-output）
    </td>
    
    <td>
      共享后更少
    </td>
    
    <td>
      中
    </td>
    
    <td>
      √
    </td>
    
    <td>
      无比
    </td>
    
    <td>
      复用 PDN 子函数，减少晶体管数与重复实现
    </td>
  </tr>
</tbody>
</table>

Rabaey 对基本 dynamic gate 的总结很明确：**复杂门通常是 (N+2) 个晶体管，相对静态 CMOS 的 (2N) 更省；它是 non-ratioed；但因为动态节点是高阻存储节点，所以对泄漏、charge sharing、clock feedthrough、耦合噪声更敏感，而且需要最小时钟频率**。Domino 的核心不是“抗噪更强”，而是**通过后接静态反相器实现可级联**；它的硬限制是**只能做非反向逻辑**。双轨 Domino 用来解决这个限制，但代价就是**功耗上升**。而去掉 evaluation transistor 的 footless 变体，书里明确指出会有 **ripple precharge**，并可能带来静态功耗，因此并不是常规推荐写法。

** 这一行之所以写“视实现而定”，是因为书里区分了两类思路：
普通 **static bleeder** 会带来弱 ratio 问题并可能有静态功耗；而带反馈的 **keeper/feedback bleeder** 则更接近“改善保持、尽量避免静态功耗”的实现。

### 一句话版关键取舍

- **静态逻辑**：互补 CMOS 最稳健；pseudo-NMOS 用功耗和噪声裕量换面积；PT/CPL 更适合特定结构，不适合简单粗暴地当通用门替代；TG 比纯 PT 稳健得多。
- **动态逻辑**：优势在**少管子、快**，代价是**更脆弱、更依赖时钟与细节设计**。

要是你愿意，我可以下一条直接把这两张表整理成**更像你截图里那种“考试速记版”**，也就是更短、更适合背诵的版本。
