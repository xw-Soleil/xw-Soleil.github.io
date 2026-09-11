# Lecture 6：Behavioral Modeling，非阻塞赋值

> 行为级建模中的非阻塞赋值，阻塞与非阻塞赋值的区别

always块和initial块是verilog语言中最主要的成分。

## 赋值语句

<table>
<thead>
  <tr>
    <th>
      
    </th>
    
    <th>
      连续赋值
    </th>
    
    <th>
      过程赋值（全称：过程阻塞赋值）
    </th>
    
    <th>
      过程非阻塞赋值
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      操作
    </td>
    
    <td>
      =
    </td>
    
    <td>
      =
    </td>
    
    <td>
      <=
    </td>
  </tr>
  
  <tr>
    <td>
      何处使用
    </td>
    
    <td>
      assign语句b;
    </td>
    
    <td>
      在always与initial语句内部
    </td>
    
    <td>
      在always与initial语句内部
    </td>
  </tr>
  
  <tr>
    <td>
      示例
    </td>
    
    <td>
      wire  q;<br />
      
      reg    a, b;<br />
      
      assign q = a & b;
    </td>
    
    <td>
      reg a;<br />
      
      reg b;<br />
      
      always @(b)
    </td>
    
    <td>
      reg a;<br />
      
      reg b;<br />
      
      always @(b)
    </td>
  </tr>
  
  <tr>
    <td>
      左边LHS
    </td>
    
    <td>
      wire
    </td>
    
    <td>
      reg
    </td>
    
    <td>
      reg
    </td>
  </tr>
  
  <tr>
    <td>
      右边RHS
    </td>
    
    <td>
      net或reg
    </td>
    
    <td>
      net或reg
    </td>
    
    <td>
      net或reg的表达式
    </td>
  </tr>
  
  <tr>
    <td>
      计算
    </td>
    
    <td>
      当右边的任何地方改变时
    </td>
    
    <td>
      过程化执行
    </td>
    
    <td>
      当前时间步结束时
    </td>
  </tr>
</tbody>
</table>

#### 过程化执行定义

**always块被其敏感表中的事件包括信号变化触发，然后开始执行。**

当always块执行时，它的begin-end以顺序方式遍历所有语句代码，直到它运行到一个时间控制语句(@, wait, #)

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 50.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="image.png" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/Lecture6-01.webp" />
      </p>
    </td>
    
    
      <td style="width: 50.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="image.png" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/Lecture6-02.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

## 过程赋值

### 过程阻塞赋值

如果当前赋值没有完成，则顺序块中的下一步执行无法开始。

```verilog
reg [7:0] a, b, c;
always @(c) begin
    a = c + 2;
    b = c * 3;
end
//阻塞赋值:a的赋值必须在b赋值开始前完成
```

### 过程非阻塞赋值

当前时间步结束时，会对于顺序块进行并行赋值。

#### ‘当前时间表结束时’的含义

模拟器根据事件的特点，处理对于给定时间的所有事件

1. 执行以下操作：

  - 计算所有赋值的右边
  - 赋值所有过程阻塞赋值的左边
  - 赋值所有连续赋值的左边
  - 计算所有原语(如: 门电路)的输入和输出
  - 对于$display语句进行打印
2. 赋值所有过程非阻塞赋值的左边
3. 根据<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mi>

s

</mi>

<mi>

t

</mi>

<mi>

r

</mi>

<mi>

o

</mi>

<mi>

b

</mi>

<mi>

e

</mi>

<mtext>

、

</mtext>
</mrow>

<annotation encoding="application/x-tex">

strobe、

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.6944em;">



</span>

<span className="mord,mathnormal">

s

</span>

<span className="mord,mathnormal">

t

</span>

<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>

<span className="mord,mathnormal">

o

</span>

<span className="mord,mathnormal">

b

</span>

<span className="mord,mathnormal">

e

</span>

<span className="mord,cjk_fallback">

、

</span>
</span>
</span>
</span>

monitor语句的执行进行打印

### 赋值语句的执行

#### 例1

```verilog
reg[7:0]a,b;
initial b = 0;
initial a = 4;
always @(a or b)
    begin
        a = b + 2;
        b = a * 3;
    end
//a = 0 + 2 = 2
//b = 2 * 3 = 6
```

```verilog
reg[7:0] a,b;
initial b = 0;
initial a = 4;
always @(a or b)
    begin
        a <= b + 2;
        b <= a * 3;
    end
//a = 0 + 2 = 2
//b = 4 * 3 = 12
```

#### 例2  对于寄存器的赋值

###### 对于寄存器的阻塞赋值

```verilog
module fsm_mod(q1, q0, in, clk);
    output q1, q0;
    input clk, in;
    reg q1, q0;
    always @(posedge clk) begin
        q1 = in;
        q0 = in | q1;
    end
endmodule
```

上述代码波形图如下：

![image.png](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/Lecture6-03.webp)

对于使用同一个@posedge或者@negedge的时钟的级联信号而言，它相当于组合逻辑

![image.png](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/Lecture6-04.webp)

###### 对于寄存器的非阻塞赋值

```verilog
module fsm_mod(q1, q0, in, clk);
    output q1, q0;
    input clk, in;
    reg q1, q0;
    always @(posedge clk) begin
        q1 <= in;
        q0 <= in | q1;
    end
endmodule
```

> 上述代码波形图

![image.png](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/Lecture6-05.webp)

对于使用同一个@posedge或者@negedge的时钟的级联信号而言，需要加1个寄存器

![image.png](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/HDL/Lecture6-06.webp)

#### 例3  D触发器（flip-flop）的非阻塞赋值

在设计与综合阶段，在always块中的非阻塞赋值以行为一致的方式、被用于D触发器建模

- 1个寄存器reg变量被用于表示D触发器
- 写入变量(见上例，如：q1或者q0, 使用<=)意味着连接到其D触发器输入
- 从变量读取(见上例，如：q1)意味着连接到其D触发器输出

```verilog
always @(posedge iClock) begin : lLoop //Testbench
    if (!rReady) disable lLoop;
    rData = rTData[nDataIndex][`DataMSB:`DataLSB];
end

always @(posedge iClock or negedge iReset) begin //Design
    if (!iReset) rDataUse <= 0;
    else
        if (iReset) begin
        rDataUse <= rData;
    end
end
```

##### 3个寄存器链（常规）

```verilog
module chain(q, i, clk);
    output q;
    input i, clk;
reg q, q1, q2;
always @(posedge clk) begin
    q <= q1;         //并行所以无关次序
    q1 <= q2;
    q2 <= i;
end
endmodule
```

##### 多路复用的数据通路方法(时序存储+组合计算)

```verilog
module chain(q, i, clk); 
    output q; 
    input i, clk; 
    reg q, q1, q2; 
    wire q_next, q1_next, q2_next; 
    always @(posedge clk) begin 
    q <= q_next; 
    q1 <= q1_next; 
    q2 <= q2_next; 
    end 
    assign q_next = q1; 
    assign q1_next = q2; 
    assign q2_next = i; 
endmodule
//q、q1、q2相当于不同的数据通路
```

##### 结构化方法

```verilog
module flipflop(q, i, clk);
    output q;
    input i, clk;
    // implementation of flipflop ..
endmodule

module chain(q, i, clk);
    output q;
    input i, clk;
    wire q1, q2;
    flipflop F1(q, q1, clk);
    flipflop F2(q1, q2, clk);
    flipflop F3(q2, i, clk);
endmodule
```

## 总结

- 通常用于在always块中对D触发器类型建模
- 模拟多个并发表达式的行为
- 可以使用always块中的非阻塞赋值设计诸如: 控制器、数据通路等中的时序逻辑
- 通常，不要在同一块中混合非阻塞和阻塞赋值
