# 期中前

> 模拟集成电路设计：期中前内容整理； btw 这个写的有点过于意识流了，大家随便看看就好了，重点还是 ppt 和书以及历年卷

## Introduction

### why CMOS

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/BeforeMidterm-01.webp)

### Analog vs Digital IC

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/BeforeMidterm-02.webp)

### PVT

Fabrication Process，Supply Voltage，Ambient Temperature。

即制造工艺，供电电压和环境温度。

## 工艺制造

Chips are built in huge factories called Fabs.

### CMOS 工艺流程

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/BeforeMidterm-03.webp)

## Wafer processing

81

## Photolithography

photomask （掩膜）

Photoresist（光刻胶）：分为正胶（不透光）和负胶（透光）

## 工艺角Process Coners

<table>
<thead>
  <tr>
    <th>
      工艺角 (Corner)
    </th>
    
    <th>
      特性 (Characteristic)
    </th>
    
    <th>
      VTH​ (阈值电压)
    </th>
    
    <th>
      ID​ (驱动电流)
    </th>
    
    <th>
      gm​ (跨导)
    </th>
    
    <th>
      功耗 (Power)
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      FF
    </td>
    
    <td>
      Fast-Fast (快速)
    </td>
    
    <td>
      低 (Lower)
    </td>
    
    <td>
      高 (Higher)
    </td>
    
    <td>
      高 (Higher)
    </td>
    
    <td>
      高 (Higher)
    </td>
  </tr>
  
  <tr>
    <td>
      TT
    </td>
    
    <td>
      Typical-Typical (典型)
    </td>
    
    <td>
      典型 (Typical)
    </td>
    
    <td>
      典型 (Typical)
    </td>
    
    <td>
      典型 (Typical)
    </td>
    
    <td>
      典型 (Typical)
    </td>
  </tr>
  
  <tr>
    <td>
      SS
    </td>
    
    <td>
      Slow-Slow (慢速)
    </td>
    
    <td>
      高 (Higher)
    </td>
    
    <td>
      低 (Lower)
    </td>
    
    <td>
      低 (Lower)
    </td>
    
    <td>
      低 (Lower)
    </td>
  </tr>
</tbody>
</table>

## 单端放大器

### Common Source  Stage ｜ 共源级放大器

#### Resistive Load | 阻性负载

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 33.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/BeforeMidterm-04.webp" />
      </p>
    </td>
    
    
      <td style="width: 66.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/BeforeMidterm-05.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

###### 信号特性分析

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/BeforeMidterm-06.webp)

#### Diode-Connect Load

##### 二极管接法的MOS管信号特性

1. 大信号特性——Vth阈值电压（类似二极管的关断和打开）
![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/BeforeMidterm-07.webp)
2. 小信号电阻特性
![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/BeforeMidterm-08.webp)

##### 大信号特性

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/BeforeMidterm-09.webp)

##### 小信号电路分析

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/BeforeMidterm-10.webp)

实际上两个NMOS的话无法避免体效应，那么就把二极管接法MOS管子改成PMOS

###### PMOS接法

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 51.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/BeforeMidterm-11.webp" />
      </p>
    </td>
    
    
      <td style="width: 48.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/BeforeMidterm-12.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

- 但PMOS接法有个缺点，P的mobility通常是N mobility 的1/2或者2/3，所以如果想要高增益---就得<mark>

让M1的W/L大于M2的W/L的好几倍，这会导致寄生电容增加，影响电路速度，但是电路带宽可以做到很大

</mark>

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/BeforeMidterm-13.webp)
- 增益与器件尺寸的函数关系相对较弱——高增益 意味着 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mo stretchy="false">

(

</mo>

<mi>

W

</mi>

<mi mathvariant="normal">

/

</mi>

<mi>

L

</mi>

<msub>
<mo stretchy="false">

)

</mo>

<mn>

1

</mn>
</msub>

<mo>

≫

</mo>

<mo stretchy="false">

(

</mo>

<mi>

W

</mi>

<mi mathvariant="normal">

/

</mi>

<mi>

L

</mi>

<msub>
<mo stretchy="false">

)

</mo>

<mn>

2

</mn>
</msub>
</mrow>

<annotation encoding="application/x-tex">

(W/L)_1 \gg (W/L)_2

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mopen">

(

</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

W

</span>

<span className="mord">

/

</span>

<span className="mord,mathnormal">

L

</span>

<span className="mclose">
<span className="mclose">

)

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">

1

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

≫

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mopen">

(

</span>

<span className="mord,mathnormal" style="margin-right:0.1389em;">

W

</span>

<span className="mord">

/

</span>

<span className="mord,mathnormal">

L

</span>

<span className="mclose">
<span className="mclose">

)

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">

2

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

导致不成比例的宽或长晶体管（带来大的输入或负载电容）

#### Current Source Load

##### 电路拓扑与等效电路

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 52.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/BeforeMidterm-14.webp" />
      </p>
    </td>
    
    
      <td style="width: 47.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/BeforeMidterm-15.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

输入输出特性曲线

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/BeforeMidterm-16.webp)

输出摆幅限制在<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mo stretchy="false">

[

</mo>

<msub>
<mi>

V

</mi>

<mrow>
<mi>

i

</mi>

<mi>

n

</mi>
</mrow>
</msub>

<mo>

−

</mo>

<msub>
<mi>

V

</mi>

<mrow>
<mi>

T

</mi>

<mi>

H

</mi>

<mn>

1

</mn>
</mrow>
</msub>

<mo separator="true">

,

</mo>

<msub>
<mi>

V

</mi>

<mrow>
<mi>

D

</mi>

<mi>

D

</mi>
</mrow>
</msub>

<mo>

−

</mo>

<mi mathvariant="normal">

∣

</mi>

<msub>
<mi>

V

</mi>

<mrow>
<mi>

G

</mi>

<mi>

S

</mi>

<mn>

2

</mn>
</mrow>
</msub>

<mo>

−

</mo>

<msub>
<mi>

V

</mi>

<mrow>
<mi>

T

</mi>

<mi>

H

</mi>

<mn>

2

</mn>
</mrow>
</msub>

<mi mathvariant="normal">

∣

</mi>

<mo stretchy="false">

]

</mo>
</mrow>

<annotation encoding="application/x-tex">

[V_{in}-V_{TH1}, V_{DD} - |V_{GS2} - V_{TH2}| ]

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mopen">

[

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.2222em;">

V

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

in

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

−

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8778em;vertical-align:-0.1944em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.2222em;">

V

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.1389em;">

T

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0813em;">

H

</span>

<span className="mord,mtight">

1

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>

<span className="mpunct">

,

</span>

<span className="mspace" style="margin-right:0.1667em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.2222em;">

V

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

D

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

D

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

−

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord">

∣

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.2222em;">

V

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

GS

</span>

<span className="mord,mtight">

2

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

−

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.2222em;">

V

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.1389em;">

T

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0813em;">

H

</span>

<span className="mord,mtight">

2

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>

<span className="mord">

∣

</span>

<span className="mclose">

]

</span>
</span>
</span>
</span>

区间内（<mark>

注意这里的值都是直流信号量，才能给小信号设计留有余量

</mark>

）

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/BeforeMidterm-17.webp)

<table>
<thead>
  <tr>
    <th>
      特性
    </th>
    
    <th>
      1. 二极管连接负载 (Diode-Connected Load)
    </th>
    
    <th>
      2. 电流源负载 (Current Source Load)
    </th>
    
    <th>
      3. 推挽式反相器 (Push-Pull Inverter)
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      电路示意图
    </td>
    
    <td>
      <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/BeforeMidterm-18.webp" />
    </td>
    
    <td>
      <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/BeforeMidterm-19.webp" />
    </td>
    
    <td>
      <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/BeforeMidterm-20.webp" />
    </td>
  </tr>
  
  <tr>
    <td>
      电压增益 (<span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <msub>
                  <mi>
                    A
                  </mi>
                  
                  <mi>
                    v
                  </mi>
                </msub>
              </mrow>
              
              <annotation encoding="application/x-tex">
                A_v
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:0.8333em;vertical-align:-0.15em;">
              
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal">
                A
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.1514em;">
                      <span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
                        <span className="pstrut" style="height:2.7em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">
                            v
                          </span>
                        </span>
                      </span>
                    </span>
                    
                    <span className="vlist-s">
                      ​
                    </span>
                  </span>
                  
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.15em;">
                      <span>
                        
                      </span>
                    </span>
                  </span>
                </span>
              </span>
            </span>
          </span>
        </span>
      </span>
      
      )
    </td>
    
    <td>
      低 <br />
      
       <span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <mo>
                  ≈
                </mo>
                
                <mo>
                  −
                </mo>
                
                <msub>
                  <mi>
                    g
                  </mi>
                  
                  <mrow>
                    <mi>
                      m
                    </mi>
                    
                    <mn>
                      1
                    </mn>
                  </mrow>
                </msub>
                
                <mi mathvariant="normal">
                  /
                </mi>
                
                <msub>
                  <mi>
                    g
                  </mi>
                  
                  <mrow>
                    <mi>
                      m
                    </mi>
                    
                    <mn>
                      2
                    </mn>
                  </mrow>
                </msub>
              </mrow>
              
              <annotation encoding="application/x-tex">
                \approx -g_{m1} / g_{m2}
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:0.4831em;">
              
            </span>
            
            <span className="mrel">
              ≈
            </span>
            
            <span className="mspace" style="margin-right:0.2778em;">
              
            </span>
          </span>
          
          <span className="base">
            <span className="strut" style="height:1em;vertical-align:-0.25em;">
              
            </span>
            
            <span className="mord">
              −
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal" style="margin-right:0.0359em;">
                g
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.3011em;">
                      <span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
                        <span className="pstrut" style="height:2.7em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mtight">
                            <span className="mord,mathnormal,mtight">
                              m
                            </span>
                            
                            <span className="mord,mtight">
                              1
                            </span>
                          </span>
                        </span>
                      </span>
                    </span>
                    
                    <span className="vlist-s">
                      ​
                    </span>
                  </span>
                  
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.15em;">
                      <span>
                        
                      </span>
                    </span>
                  </span>
                </span>
              </span>
            </span>
            
            <span className="mord">
              /
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal" style="margin-right:0.0359em;">
                g
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.3011em;">
                      <span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
                        <span className="pstrut" style="height:2.7em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mtight">
                            <span className="mord,mathnormal,mtight">
                              m
                            </span>
                            
                            <span className="mord,mtight">
                              2
                            </span>
                          </span>
                        </span>
                      </span>
                    </span>
                    
                    <span className="vlist-s">
                      ​
                    </span>
                  </span>
                  
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.15em;">
                      <span>
                        
                      </span>
                    </span>
                  </span>
                </span>
              </span>
            </span>
          </span>
        </span>
      </span>
    </td>
    
    <td>
      非常高 <br />
      
       <span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <mo>
                  −
                </mo>
                
                <msub>
                  <mi>
                    g
                  </mi>
                  
                  <mrow>
                    <mi>
                      m
                    </mi>
                    
                    <mn>
                      1
                    </mn>
                  </mrow>
                </msub>
                
                <mo stretchy="false">
                  (
                </mo>
                
                <msub>
                  <mi>
                    r
                  </mi>
                  
                  <mrow>
                    <mi>
                      o
                    </mi>
                    
                    <mn>
                      1
                    </mn>
                  </mrow>
                </msub>
                
                <mi mathvariant="normal">
                  /
                </mi>
                
                <mi mathvariant="normal">
                  /
                </mi>
                
                <msub>
                  <mi>
                    r
                  </mi>
                  
                  <mrow>
                    <mi>
                      o
                    </mi>
                    
                    <mn>
                      2
                    </mn>
                  </mrow>
                </msub>
                
                <mo stretchy="false">
                  )
                </mo>
              </mrow>
              
              <annotation encoding="application/x-tex">
                -g_{m1} (r_{o1} // r_{o2})
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:1em;vertical-align:-0.25em;">
              
            </span>
            
            <span className="mord">
              −
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal" style="margin-right:0.0359em;">
                g
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.3011em;">
                      <span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
                        <span className="pstrut" style="height:2.7em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mtight">
                            <span className="mord,mathnormal,mtight">
                              m
                            </span>
                            
                            <span className="mord,mtight">
                              1
                            </span>
                          </span>
                        </span>
                      </span>
                    </span>
                    
                    <span className="vlist-s">
                      ​
                    </span>
                  </span>
                  
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.15em;">
                      <span>
                        
                      </span>
                    </span>
                  </span>
                </span>
              </span>
            </span>
            
            <span className="mopen">
              (
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal" style="margin-right:0.0278em;">
                r
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.3011em;">
                      <span style="top:-2.55em;margin-left:-0.0278em;margin-right:0.05em;">
                        <span className="pstrut" style="height:2.7em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mtight">
                            <span className="mord,mathnormal,mtight">
                              o
                            </span>
                            
                            <span className="mord,mtight">
                              1
                            </span>
                          </span>
                        </span>
                      </span>
                    </span>
                    
                    <span className="vlist-s">
                      ​
                    </span>
                  </span>
                  
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.15em;">
                      <span>
                        
                      </span>
                    </span>
                  </span>
                </span>
              </span>
            </span>
            
            <span className="mord">
              //
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal" style="margin-right:0.0278em;">
                r
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.3011em;">
                      <span style="top:-2.55em;margin-left:-0.0278em;margin-right:0.05em;">
                        <span className="pstrut" style="height:2.7em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mtight">
                            <span className="mord,mathnormal,mtight">
                              o
                            </span>
                            
                            <span className="mord,mtight">
                              2
                            </span>
                          </span>
                        </span>
                      </span>
                    </span>
                    
                    <span className="vlist-s">
                      ​
                    </span>
                  </span>
                  
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.15em;">
                      <span>
                        
                      </span>
                    </span>
                  </span>
                </span>
              </span>
            </span>
            
            <span className="mclose">
              )
            </span>
          </span>
        </span>
      </span>
    </td>
    
    <td>
      最高 <br />
      
       <span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <mo>
                  −
                </mo>
                
                <mo stretchy="false">
                  (
                </mo>
                
                <msub>
                  <mi>
                    g
                  </mi>
                  
                  <mrow>
                    <mi>
                      m
                    </mi>
                    
                    <mn>
                      1
                    </mn>
                  </mrow>
                </msub>
                
                <mo>
                  +
                </mo>
                
                <msub>
                  <mi>
                    g
                  </mi>
                  
                  <mrow>
                    <mi>
                      m
                    </mi>
                    
                    <mn>
                      2
                    </mn>
                  </mrow>
                </msub>
                
                <mo stretchy="false">
                  )
                </mo>
                
                <mo stretchy="false">
                  (
                </mo>
                
                <msub>
                  <mi>
                    r
                  </mi>
                  
                  <mrow>
                    <mi>
                      o
                    </mi>
                    
                    <mn>
                      1
                    </mn>
                  </mrow>
                </msub>
                
                <mi mathvariant="normal">
                  /
                </mi>
                
                <mi mathvariant="normal">
                  /
                </mi>
                
                <msub>
                  <mi>
                    r
                  </mi>
                  
                  <mrow>
                    <mi>
                      o
                    </mi>
                    
                    <mn>
                      2
                    </mn>
                  </mrow>
                </msub>
                
                <mo stretchy="false">
                  )
                </mo>
              </mrow>
              
              <annotation encoding="application/x-tex">
                -(g_{m1} + g_{m2}) (r_{o1} // r_{o2})
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:1em;vertical-align:-0.25em;">
              
            </span>
            
            <span className="mord">
              −
            </span>
            
            <span className="mopen">
              (
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal" style="margin-right:0.0359em;">
                g
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.3011em;">
                      <span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
                        <span className="pstrut" style="height:2.7em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mtight">
                            <span className="mord,mathnormal,mtight">
                              m
                            </span>
                            
                            <span className="mord,mtight">
                              1
                            </span>
                          </span>
                        </span>
                      </span>
                    </span>
                    
                    <span className="vlist-s">
                      ​
                    </span>
                  </span>
                  
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.15em;">
                      <span>
                        
                      </span>
                    </span>
                  </span>
                </span>
              </span>
            </span>
            
            <span className="mspace" style="margin-right:0.2222em;">
              
            </span>
            
            <span className="mbin">
              +
            </span>
            
            <span className="mspace" style="margin-right:0.2222em;">
              
            </span>
          </span>
          
          <span className="base">
            <span className="strut" style="height:1em;vertical-align:-0.25em;">
              
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal" style="margin-right:0.0359em;">
                g
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.3011em;">
                      <span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
                        <span className="pstrut" style="height:2.7em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mtight">
                            <span className="mord,mathnormal,mtight">
                              m
                            </span>
                            
                            <span className="mord,mtight">
                              2
                            </span>
                          </span>
                        </span>
                      </span>
                    </span>
                    
                    <span className="vlist-s">
                      ​
                    </span>
                  </span>
                  
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.15em;">
                      <span>
                        
                      </span>
                    </span>
                  </span>
                </span>
              </span>
            </span>
            
            <span className="mclose">
              )
            </span>
            
            <span className="mopen">
              (
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal" style="margin-right:0.0278em;">
                r
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.3011em;">
                      <span style="top:-2.55em;margin-left:-0.0278em;margin-right:0.05em;">
                        <span className="pstrut" style="height:2.7em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mtight">
                            <span className="mord,mathnormal,mtight">
                              o
                            </span>
                            
                            <span className="mord,mtight">
                              1
                            </span>
                          </span>
                        </span>
                      </span>
                    </span>
                    
                    <span className="vlist-s">
                      ​
                    </span>
                  </span>
                  
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.15em;">
                      <span>
                        
                      </span>
                    </span>
                  </span>
                </span>
              </span>
            </span>
            
            <span className="mord">
              //
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal" style="margin-right:0.0278em;">
                r
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.3011em;">
                      <span style="top:-2.55em;margin-left:-0.0278em;margin-right:0.05em;">
                        <span className="pstrut" style="height:2.7em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mtight">
                            <span className="mord,mathnormal,mtight">
                              o
                            </span>
                            
                            <span className="mord,mtight">
                              2
                            </span>
                          </span>
                        </span>
                      </span>
                    </span>
                    
                    <span className="vlist-s">
                      ​
                    </span>
                  </span>
                  
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.15em;">
                      <span>
                        
                      </span>
                    </span>
                  </span>
                </span>
              </span>
            </span>
            
            <span className="mclose">
              )
            </span>
          </span>
        </span>
      </span>
    </td>
  </tr>
  
  <tr>
    <td>
      输出电阻 (<span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <msub>
                  <mi>
                    R
                  </mi>
                  
                  <mrow>
                    <mi>
                      o
                    </mi>
                    
                    <mi>
                      u
                    </mi>
                    
                    <mi>
                      t
                    </mi>
                  </mrow>
                </msub>
              </mrow>
              
              <annotation encoding="application/x-tex">
                R_{out}
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:0.8333em;vertical-align:-0.15em;">
              
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal" style="margin-right:0.0077em;">
                R
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.2806em;">
                      <span style="top:-2.55em;margin-left:-0.0077em;margin-right:0.05em;">
                        <span className="pstrut" style="height:2.7em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mtight">
                            <span className="mord,mathnormal,mtight">
                              o
                            </span>
                            
                            <span className="mord,mathnormal,mtight">
                              u
                            </span>
                            
                            <span className="mord,mathnormal,mtight">
                              t
                            </span>
                          </span>
                        </span>
                      </span>
                    </span>
                    
                    <span className="vlist-s">
                      ​
                    </span>
                  </span>
                  
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.15em;">
                      <span>
                        
                      </span>
                    </span>
                  </span>
                </span>
              </span>
            </span>
          </span>
        </span>
      </span>
      
      )
    </td>
    
    <td>
      低 <br />
      
       <span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <mo>
                  ≈
                </mo>
                
                <mn>
                  1
                </mn>
                
                <mi mathvariant="normal">
                  /
                </mi>
                
                <msub>
                  <mi>
                    g
                  </mi>
                  
                  <mrow>
                    <mi>
                      m
                    </mi>
                    
                    <mn>
                      2
                    </mn>
                  </mrow>
                </msub>
              </mrow>
              
              <annotation encoding="application/x-tex">
                \approx 1 / g_{m2}
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:0.4831em;">
              
            </span>
            
            <span className="mrel">
              ≈
            </span>
            
            <span className="mspace" style="margin-right:0.2778em;">
              
            </span>
          </span>
          
          <span className="base">
            <span className="strut" style="height:1em;vertical-align:-0.25em;">
              
            </span>
            
            <span className="mord">
              1/
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal" style="margin-right:0.0359em;">
                g
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.3011em;">
                      <span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
                        <span className="pstrut" style="height:2.7em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mtight">
                            <span className="mord,mathnormal,mtight">
                              m
                            </span>
                            
                            <span className="mord,mtight">
                              2
                            </span>
                          </span>
                        </span>
                      </span>
                    </span>
                    
                    <span className="vlist-s">
                      ​
                    </span>
                  </span>
                  
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.15em;">
                      <span>
                        
                      </span>
                    </span>
                  </span>
                </span>
              </span>
            </span>
          </span>
        </span>
      </span>
    </td>
    
    <td>
      非常高 <br />
      
       <span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <msub>
                  <mi>
                    r
                  </mi>
                  
                  <mrow>
                    <mi>
                      o
                    </mi>
                    
                    <mn>
                      1
                    </mn>
                  </mrow>
                </msub>
                
                <mi mathvariant="normal">
                  /
                </mi>
                
                <mi mathvariant="normal">
                  /
                </mi>
                
                <msub>
                  <mi>
                    r
                  </mi>
                  
                  <mrow>
                    <mi>
                      o
                    </mi>
                    
                    <mn>
                      2
                    </mn>
                  </mrow>
                </msub>
              </mrow>
              
              <annotation encoding="application/x-tex">
                r_{o1} // r_{o2}
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:1em;vertical-align:-0.25em;">
              
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal" style="margin-right:0.0278em;">
                r
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.3011em;">
                      <span style="top:-2.55em;margin-left:-0.0278em;margin-right:0.05em;">
                        <span className="pstrut" style="height:2.7em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mtight">
                            <span className="mord,mathnormal,mtight">
                              o
                            </span>
                            
                            <span className="mord,mtight">
                              1
                            </span>
                          </span>
                        </span>
                      </span>
                    </span>
                    
                    <span className="vlist-s">
                      ​
                    </span>
                  </span>
                  
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.15em;">
                      <span>
                        
                      </span>
                    </span>
                  </span>
                </span>
              </span>
            </span>
            
            <span className="mord">
              //
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal" style="margin-right:0.0278em;">
                r
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.3011em;">
                      <span style="top:-2.55em;margin-left:-0.0278em;margin-right:0.05em;">
                        <span className="pstrut" style="height:2.7em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mtight">
                            <span className="mord,mathnormal,mtight">
                              o
                            </span>
                            
                            <span className="mord,mtight">
                              2
                            </span>
                          </span>
                        </span>
                      </span>
                    </span>
                    
                    <span className="vlist-s">
                      ​
                    </span>
                  </span>
                  
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.15em;">
                      <span>
                        
                      </span>
                    </span>
                  </span>
                </span>
              </span>
            </span>
          </span>
        </span>
      </span>
    </td>
    
    <td>
      非常高 <br />
      
       <span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <msub>
                  <mi>
                    r
                  </mi>
                  
                  <mrow>
                    <mi>
                      o
                    </mi>
                    
                    <mn>
                      1
                    </mn>
                  </mrow>
                </msub>
                
                <mi mathvariant="normal">
                  /
                </mi>
                
                <mi mathvariant="normal">
                  /
                </mi>
                
                <msub>
                  <mi>
                    r
                  </mi>
                  
                  <mrow>
                    <mi>
                      o
                    </mi>
                    
                    <mn>
                      2
                    </mn>
                  </mrow>
                </msub>
              </mrow>
              
              <annotation encoding="application/x-tex">
                r_{o1} // r_{o2}
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:1em;vertical-align:-0.25em;">
              
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal" style="margin-right:0.0278em;">
                r
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.3011em;">
                      <span style="top:-2.55em;margin-left:-0.0278em;margin-right:0.05em;">
                        <span className="pstrut" style="height:2.7em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mtight">
                            <span className="mord,mathnormal,mtight">
                              o
                            </span>
                            
                            <span className="mord,mtight">
                              1
                            </span>
                          </span>
                        </span>
                      </span>
                    </span>
                    
                    <span className="vlist-s">
                      ​
                    </span>
                  </span>
                  
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.15em;">
                      <span>
                        
                      </span>
                    </span>
                  </span>
                </span>
              </span>
            </span>
            
            <span className="mord">
              //
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal" style="margin-right:0.0278em;">
                r
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.3011em;">
                      <span style="top:-2.55em;margin-left:-0.0278em;margin-right:0.05em;">
                        <span className="pstrut" style="height:2.7em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mtight">
                            <span className="mord,mathnormal,mtight">
                              o
                            </span>
                            
                            <span className="mord,mtight">
                              2
                            </span>
                          </span>
                        </span>
                      </span>
                    </span>
                    
                    <span className="vlist-s">
                      ​
                    </span>
                  </span>
                  
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.15em;">
                      <span>
                        
                      </span>
                    </span>
                  </span>
                </span>
              </span>
            </span>
          </span>
        </span>
      </span>
    </td>
  </tr>
  
  <tr>
    <td>
      输出摆幅 (Swing)
    </td>
    
    <td>
      中等偏低 <br />
      
       （输出上限会损失一个 <span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <msub>
                  <mi>
                    V
                  </mi>
                  
                  <mrow>
                    <mi>
                      T
                    </mi>
                    
                    <mi>
                      H
                    </mi>
                    
                    <mn>
                      2
                    </mn>
                  </mrow>
                </msub>
                
                <mo>
                  +
                </mo>
                
                <msub>
                  <mi>
                    V
                  </mi>
                  
                  <mrow>
                    <mi>
                      O
                    </mi>
                    
                    <mi>
                      V
                    </mi>
                    
                    <mn>
                      2
                    </mn>
                  </mrow>
                </msub>
              </mrow>
              
              <annotation encoding="application/x-tex">
                V_{TH2} + V_{OV2}
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:0.8333em;vertical-align:-0.15em;">
              
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal" style="margin-right:0.2222em;">
                V
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.3283em;">
                      <span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
                        <span className="pstrut" style="height:2.7em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mtight">
                            <span className="mord,mathnormal,mtight" style="margin-right:0.1389em;">
                              T
                            </span>
                            
                            <span className="mord,mathnormal,mtight" style="margin-right:0.0813em;">
                              H
                            </span>
                            
                            <span className="mord,mtight">
                              2
                            </span>
                          </span>
                        </span>
                      </span>
                    </span>
                    
                    <span className="vlist-s">
                      ​
                    </span>
                  </span>
                  
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.15em;">
                      <span>
                        
                      </span>
                    </span>
                  </span>
                </span>
              </span>
            </span>
            
            <span className="mspace" style="margin-right:0.2222em;">
              
            </span>
            
            <span className="mbin">
              +
            </span>
            
            <span className="mspace" style="margin-right:0.2222em;">
              
            </span>
          </span>
          
          <span className="base">
            <span className="strut" style="height:0.8333em;vertical-align:-0.15em;">
              
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal" style="margin-right:0.2222em;">
                V
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.3283em;">
                      <span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
                        <span className="pstrut" style="height:2.7em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mtight">
                            <span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">
                              O
                            </span>
                            
                            <span className="mord,mathnormal,mtight" style="margin-right:0.2222em;">
                              V
                            </span>
                            
                            <span className="mord,mtight">
                              2
                            </span>
                          </span>
                        </span>
                      </span>
                    </span>
                    
                    <span className="vlist-s">
                      ​
                    </span>
                  </span>
                  
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.15em;">
                      <span>
                        
                      </span>
                    </span>
                  </span>
                </span>
              </span>
            </span>
          </span>
        </span>
      </span>
      
      ）
    </td>
    
    <td>
      高 <br />
      
       （可接近 <span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <msub>
                  <mi>
                    V
                  </mi>
                  
                  <mrow>
                    <mi>
                      D
                    </mi>
                    
                    <mi>
                      D
                    </mi>
                  </mrow>
                </msub>
              </mrow>
              
              <annotation encoding="application/x-tex">
                V_{DD}
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:0.8333em;vertical-align:-0.15em;">
              
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal" style="margin-right:0.2222em;">
                V
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.3283em;">
                      <span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
                        <span className="pstrut" style="height:2.7em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mtight">
                            <span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">
                              D
                            </span>
                            
                            <span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">
                              D
                            </span>
                          </span>
                        </span>
                      </span>
                    </span>
                    
                    <span className="vlist-s">
                      ​
                    </span>
                  </span>
                  
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.15em;">
                      <span>
                        
                      </span>
                    </span>
                  </span>
                </span>
              </span>
            </span>
          </span>
        </span>
      </span>
      
       和 GND，仅受 <span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <msub>
                  <mi>
                    V
                  </mi>
                  
                  <mrow>
                    <mi>
                      O
                    </mi>
                    
                    <mi>
                      V
                    </mi>
                  </mrow>
                </msub>
              </mrow>
              
              <annotation encoding="application/x-tex">
                V_{OV}
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:0.8333em;vertical-align:-0.15em;">
              
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal" style="margin-right:0.2222em;">
                V
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.3283em;">
                      <span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
                        <span className="pstrut" style="height:2.7em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mtight">
                            <span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">
                              O
                            </span>
                            
                            <span className="mord,mathnormal,mtight" style="margin-right:0.2222em;">
                              V
                            </span>
                          </span>
                        </span>
                      </span>
                    </span>
                    
                    <span className="vlist-s">
                      ​
                    </span>
                  </span>
                  
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.15em;">
                      <span>
                        
                      </span>
                    </span>
                  </span>
                </span>
              </span>
            </span>
          </span>
        </span>
      </span>
      
       限制）
    </td>
    
    <td>
      高 <br />
      
       （作为放大器时，摆幅同电流源负载）
    </td>
  </tr>
  
  <tr>
    <td>
      带宽 (速度)
    </td>
    
    <td>
      高 <br />
      
       （<span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <msub>
                  <mi>
                    R
                  </mi>
                  
                  <mrow>
                    <mi>
                      o
                    </mi>
                    
                    <mi>
                      u
                    </mi>
                    
                    <mi>
                      t
                    </mi>
                  </mrow>
                </msub>
              </mrow>
              
              <annotation encoding="application/x-tex">
                R_{out}
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:0.8333em;vertical-align:-0.15em;">
              
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal" style="margin-right:0.0077em;">
                R
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.2806em;">
                      <span style="top:-2.55em;margin-left:-0.0077em;margin-right:0.05em;">
                        <span className="pstrut" style="height:2.7em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mtight">
                            <span className="mord,mathnormal,mtight">
                              o
                            </span>
                            
                            <span className="mord,mathnormal,mtight">
                              u
                            </span>
                            
                            <span className="mord,mathnormal,mtight">
                              t
                            </span>
                          </span>
                        </span>
                      </span>
                    </span>
                    
                    <span className="vlist-s">
                      ​
                    </span>
                  </span>
                  
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.15em;">
                      <span>
                        
                      </span>
                    </span>
                  </span>
                </span>
              </span>
            </span>
          </span>
        </span>
      </span>
      
       很低，输出极点频率高）
    </td>
    
    <td>
      低 <br />
      
       （<span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <msub>
                  <mi>
                    R
                  </mi>
                  
                  <mrow>
                    <mi>
                      o
                    </mi>
                    
                    <mi>
                      u
                    </mi>
                    
                    <mi>
                      t
                    </mi>
                  </mrow>
                </msub>
              </mrow>
              
              <annotation encoding="application/x-tex">
                R_{out}
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:0.8333em;vertical-align:-0.15em;">
              
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal" style="margin-right:0.0077em;">
                R
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.2806em;">
                      <span style="top:-2.55em;margin-left:-0.0077em;margin-right:0.05em;">
                        <span className="pstrut" style="height:2.7em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mtight">
                            <span className="mord,mathnormal,mtight">
                              o
                            </span>
                            
                            <span className="mord,mathnormal,mtight">
                              u
                            </span>
                            
                            <span className="mord,mathnormal,mtight">
                              t
                            </span>
                          </span>
                        </span>
                      </span>
                    </span>
                    
                    <span className="vlist-s">
                      ​
                    </span>
                  </span>
                  
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.15em;">
                      <span>
                        
                      </span>
                    </span>
                  </span>
                </span>
              </span>
            </span>
          </span>
        </span>
      </span>
      
       很高，输出极点频率低）
    </td>
    
    <td>
      低 <br />
      
       （作为放大器时，<span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <msub>
                  <mi>
                    R
                  </mi>
                  
                  <mrow>
                    <mi>
                      o
                    </mi>
                    
                    <mi>
                      u
                    </mi>
                    
                    <mi>
                      t
                    </mi>
                  </mrow>
                </msub>
              </mrow>
              
              <annotation encoding="application/x-tex">
                R_{out}
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:0.8333em;vertical-align:-0.15em;">
              
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal" style="margin-right:0.0077em;">
                R
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.2806em;">
                      <span style="top:-2.55em;margin-left:-0.0077em;margin-right:0.05em;">
                        <span className="pstrut" style="height:2.7em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mtight">
                            <span className="mord,mathnormal,mtight">
                              o
                            </span>
                            
                            <span className="mord,mathnormal,mtight">
                              u
                            </span>
                            
                            <span className="mord,mathnormal,mtight">
                              t
                            </span>
                          </span>
                        </span>
                      </span>
                    </span>
                    
                    <span className="vlist-s">
                      ​
                    </span>
                  </span>
                  
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.15em;">
                      <span>
                        
                      </span>
                    </span>
                  </span>
                </span>
              </span>
            </span>
          </span>
        </span>
      </span>
      
       很高）
    </td>
  </tr>
  
  <tr>
    <td>
      偏置 (Biasing)
    </td>
    
    <td>
      简单 <br />
      
       （自偏置，无需额外电路）
    </td>
    
    <td>
      复杂 <br />
      
       （需要 <span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <msub>
                  <mi>
                    V
                  </mi>
                  
                  <mrow>
                    <mi>
                      G
                    </mi>
                    
                    <mi>
                      G
                    </mi>
                    
                    <mn>
                      2
                    </mn>
                  </mrow>
                </msub>
              </mrow>
              
              <annotation encoding="application/x-tex">
                V_{GG2}
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:0.8333em;vertical-align:-0.15em;">
              
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal" style="margin-right:0.2222em;">
                V
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.3283em;">
                      <span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
                        <span className="pstrut" style="height:2.7em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mtight">
                            <span className="mord,mathnormal,mtight">
                              GG
                            </span>
                            
                            <span className="mord,mtight">
                              2
                            </span>
                          </span>
                        </span>
                      </span>
                    </span>
                    
                    <span className="vlist-s">
                      ​
                    </span>
                  </span>
                  
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.15em;">
                      <span>
                        
                      </span>
                    </span>
                  </span>
                </span>
              </span>
            </span>
          </span>
        </span>
      </span>
      
       偏置，通常来自电流镜）
    </td>
    
    <td>
      非常困难 <br />
      
       （作为模拟放大器时，偏置点极敏感）
    </td>
  </tr>
  
  <tr>
    <td>
      主要特点
    </td>
    
    <td>
      增益低，但速度快，常用于宽带缓冲级或作为电流镜的输出端。
    </td>
    
    <td>
      增益-带宽权衡的经典代表。用极高的增益换取了较低的速度。是运放第一级的首选结构。
    </td>
    
    <td>
      增益最高（<span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <msub>
                  <mi>
                    M
                  </mi>
                  
                  <mn>
                    1
                  </mn>
                </msub>
                
                <mo separator="true">
                  ,
                </mo>
                
                <msub>
                  <mi>
                    M
                  </mi>
                  
                  <mn>
                    2
                  </mn>
                </msub>
              </mrow>
              
              <annotation encoding="application/x-tex">
                M_1, M_2
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:0.8778em;vertical-align:-0.1944em;">
              
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal" style="margin-right:0.109em;">
                M
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.3011em;">
                      <span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
                        <span className="pstrut" style="height:2.7em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mtight">
                            1
                          </span>
                        </span>
                      </span>
                    </span>
                    
                    <span className="vlist-s">
                      ​
                    </span>
                  </span>
                  
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.15em;">
                      <span>
                        
                      </span>
                    </span>
                  </span>
                </span>
              </span>
            </span>
            
            <span className="mpunct">
              ,
            </span>
            
            <span className="mspace" style="margin-right:0.1667em;">
              
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal" style="margin-right:0.109em;">
                M
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.3011em;">
                      <span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
                        <span className="pstrut" style="height:2.7em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mtight">
                            2
                          </span>
                        </span>
                      </span>
                    </span>
                    
                    <span className="vlist-s">
                      ​
                    </span>
                  </span>
                  
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.15em;">
                      <span>
                        
                      </span>
                    </span>
                  </span>
                </span>
              </span>
            </span>
          </span>
        </span>
      </span>
      
       都在贡献 <span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <msub>
                  <mi>
                    g
                  </mi>
                  
                  <mi>
                    m
                  </mi>
                </msub>
              </mrow>
              
              <annotation encoding="application/x-tex">
                g_m
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:0.625em;vertical-align:-0.1944em;">
              
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal" style="margin-right:0.0359em;">
                g
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.1514em;">
                      <span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
                        <span className="pstrut" style="height:2.7em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mathnormal,mtight">
                            m
                          </span>
                        </span>
                      </span>
                    </span>
                    
                    <span className="vlist-s">
                      ​
                    </span>
                  </span>
                  
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.15em;">
                      <span>
                        
                      </span>
                    </span>
                  </span>
                </span>
              </span>
            </span>
          </span>
        </span>
      </span>
      
      ）。但偏置困难，主要用于数字逻辑或AB类输出级。
    </td>
  </tr>
</tbody>
</table>

#### Source Degeneration ｜ 源极负反馈

##### 电路结构

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/BeforeMidterm-21.webp)

由于平方律方程——导致实际上Id和Vov过驱动电压是非线性关系。

<mark>

为了改善这种关系引入源极负反馈

</mark>



##### 大信号分析

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/BeforeMidterm-22.webp)

##### 小信号分析

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/BeforeMidterm-23.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/BeforeMidterm-24.webp)

线性度改善

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/BeforeMidterm-25.webp)

##### 带负载的增益

> 实际上这里直接复用前面最完整的公式就可以了

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/BeforeMidterm-26.webp)

##### 一望而知

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 56.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/BeforeMidterm-27.webp" />
      </p>
    </td>
    
    
      <td style="width: 43.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/BeforeMidterm-28.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

对于Cs放大器的增益来说，分子等于Drian漏端电阻，分母等于从Source源端看进去从源到漏的电阻

> 举例说明——一望而知
> 
> ![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/BeforeMidterm-29.webp)

#### CMOS Inverter ｜ CMOS反相器

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/BeforeMidterm-30.webp)

和电流源负载的输出电阻是一样的，但是跨导更大；但是问题在于偏置电流是PVT的强相关函数

> **P**rocess（工艺偏差）, **V**oltage（电源电压波动）, **T**emperature（温度变化）
> 
> 这里是因为这个偏置电流是从VG栅极电压给的，不好精确控制电压；但是其他结构电路可以精确控制漏电流（电流镜）并有所反馈，所以这个反相器结构的电路不好偏置

### Source Follower ｜ 源级跟随器（共漏）

#### 电阻负载

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/BeforeMidterm-31.webp)

##### 通断情况

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/BeforeMidterm-32.webp)

##### 大信号分析

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/BeforeMidterm-33.webp)

##### 小信号分析

> 在小信号分析这里，由于漏端接地，所以体效应对应的gmb可以视为电阻

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/BeforeMidterm-34.webp)

可以看出，source Follwer的增益是小于1的

###### 戴维南等效——T型电路

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/BeforeMidterm-35.webp)

> 举例：
> 
> ![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/BeforeMidterm-36.webp)
> 
> <mark>
> 
> 注意下半部分这个电路的PMOS的阻抗是(1/(gm + gmb))//ro
> 
> </mark>

##### 输入输出电阻

> 事实上从T形等效电路可以非常清晰的看出来输出负载情况

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/BeforeMidterm-37.webp)

说明体效应会让输出电阻减小decrease

##### 电流源负载

> 电阻负载会导致这个Gain是非线性的，只有当Rs无限大的时候才可以是线性变化的负载——电流源负载，**但是两个NMOS会引入体效应，所以使用两个PMOS来解决问题，PMOS可以不使用同一个Vb（右图）**

<table style="width: 100%; border: 0; border-collapse: collapse; border-spacing: 0;">
<tbody>
  <tr style="border: none;">
    <td style="width: 50.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/BeforeMidterm-38.webp" />
      </p>
    </td>
    
    
      <td style="width: 49.0%; text-align: center; border: none; padding: 0.3em; margin: 0;">
      <p>
        <img alt="img" src="https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/BeforeMidterm-39.webp" />
      </p>
    </td>
  </tr>
</tbody>
</table>

##### 缺点

###### 电压域限制

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/BeforeMidterm-40.webp)

<mark>

对于Vgs2的直流值，要求很大，比如说0.9V，那么这样的话，Vx的电压摆幅被严重限制

</mark>



###### 驱动能力差

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/BeforeMidterm-41.webp)

上图在驱动的时候，负载电阻过小就会导致增益急剧下降——驱动能力很差

### Common Gate Stage ｜ 共栅极放大器

##### 电路结构

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/BeforeMidterm-42.webp)

##### 通断分析

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/BeforeMidterm-43.webp)

##### 大信号分析

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/BeforeMidterm-44.webp)

##### 小信号分析

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/BeforeMidterm-45.webp)

##### 输入电阻分析

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/BeforeMidterm-46.webp)

> 对于这个精确公式，可以理解为Rd 这个漏端电阻被除以<span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <mo stretchy="false">
> 
> [
> 
> </mo>
> 
> <mn>
> 
> 1
> 
> </mn>
> 
> <mo>
> 
> +
> 
> </mo>
> 
> <mo stretchy="false">
> 
> (
> 
> </mo>
> 
> <msub>
> <mi>
> 
> g
> 
> </mi>
> 
> <mi>
> 
> m
> 
> </mi>
> </msub>
> 
> <mo>
> 
> +
> 
> </mo>
> 
> <msub>
> <mi>
> 
> g
> 
> </mi>
> 
> <mrow>
> <mi>
> 
> m
> 
> </mi>
> 
> <mi>
> 
> b
> 
> </mi>
> </mrow>
> </msub>
> 
> <mo stretchy="false">
> 
> )
> 
> </mo>
> 
> <msub>
> <mi>
> 
> r
> 
> </mi>
> 
> <mi>
> 
> o
> 
> </mi>
> </msub>
> 
> <mo stretchy="false">
> 
> ]
> 
> </mo>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> [1 + (g_m +g_{mb})r_o]
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:1em;vertical-align:-0.25em;">
> 
> 
> 
> </span>
> 
> <span className="mopen">
> 
> [
> 
> </span>
> 
> <span className="mord">
> 
> 1
> 
> </span>
> 
> <span className="mspace" style="margin-right:0.2222em;">
> 
> 
> 
> </span>
> 
> <span className="mbin">
> 
> +
> 
> </span>
> 
> <span className="mspace" style="margin-right:0.2222em;">
> 
> 
> 
> </span>
> </span>
> 
> <span className="base">
> <span className="strut" style="height:1em;vertical-align:-0.25em;">
> 
> 
> 
> </span>
> 
> <span className="mopen">
> 
> (
> 
> </span>
> 
> <span className="mord">
> <span className="mord,mathnormal" style="margin-right:0.0359em;">
> 
> g
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.1514em;">
> <span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mathnormal,mtight">
> 
> m
> 
> </span>
> </span>
> </span>
> </span>
> 
> <span className="vlist-s">
> 
> ​
> 
> </span>
> </span>
> 
> <span className="vlist-r">
> <span className="vlist" style="height:0.15em;">
> <span>
> 
> 
> 
> </span>
> </span>
> </span>
> </span>
> </span>
> </span>
> 
> <span className="mspace" style="margin-right:0.2222em;">
> 
> 
> 
> </span>
> 
> <span className="mbin">
> 
> +
> 
> </span>
> 
> <span className="mspace" style="margin-right:0.2222em;">
> 
> 
> 
> </span>
> </span>
> 
> <span className="base">
> <span className="strut" style="height:1em;vertical-align:-0.25em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> <span className="mord,mathnormal" style="margin-right:0.0359em;">
> 
> g
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3361em;">
> <span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mtight">
> <span className="mord,mathnormal,mtight">
> 
> mb
> 
> </span>
> </span>
> </span>
> </span>
> </span>
> 
> <span className="vlist-s">
> 
> ​
> 
> </span>
> </span>
> 
> <span className="vlist-r">
> <span className="vlist" style="height:0.15em;">
> <span>
> 
> 
> 
> </span>
> </span>
> </span>
> </span>
> </span>
> </span>
> 
> <span className="mclose">
> 
> )
> 
> </span>
> 
> <span className="mord">
> <span className="mord,mathnormal" style="margin-right:0.0278em;">
> 
> r
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.1514em;">
> <span style="top:-2.55em;margin-left:-0.0278em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mathnormal,mtight">
> 
> o
> 
> </span>
> </span>
> </span>
> </span>
> 
> <span className="vlist-s">
> 
> ​
> 
> </span>
> </span>
> 
> <span className="vlist-r">
> <span className="vlist" style="height:0.15em;">
> <span>
> 
> 
> 
> </span>
> </span>
> </span>
> </span>
> </span>
> </span>
> 
> <span className="mclose">
> 
> ]
> 
> </span>
> </span>
> </span>
> </span>
> 
> ,剩下的部分是<span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msub>
> <mi>
> 
> r
> 
> </mi>
> 
> <mi>
> 
> o
> 
> </mi>
> </msub>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> r_o
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:0.5806em;vertical-align:-0.15em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> <span className="mord,mathnormal" style="margin-right:0.0278em;">
> 
> r
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.1514em;">
> <span style="top:-2.55em;margin-left:-0.0278em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mathnormal,mtight">
> 
> o
> 
> </span>
> </span>
> </span>
> </span>
> 
> <span className="vlist-s">
> 
> ​
> 
> </span>
> </span>
> 
> <span className="vlist-r">
> <span className="vlist" style="height:0.15em;">
> <span>
> 
> 
> 
> </span>
> </span>
> </span>
> </span>
> </span>
> </span>
> </span>
> </span>
> </span>
> 
> 和<span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML">
> <semantics>
> <mrow>
> <msub>
> <mi>
> 
> g
> 
> </mi>
> 
> <mi>
> 
> m
> 
> </mi>
> </msub>
> 
> <mtext>
> 
> 
> 
> </mtext>
> 
> <msub>
> <mi>
> 
> g
> 
> </mi>
> 
> <mrow>
> <mi>
> 
> m
> 
> </mi>
> 
> <mi>
> 
> b
> 
> </mi>
> </mrow>
> </msub>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> g_m \space \space g_{mb}
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:0.625em;vertical-align:-0.1944em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> <span className="mord,mathnormal" style="margin-right:0.0359em;">
> 
> g
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.1514em;">
> <span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mathnormal,mtight">
> 
> m
> 
> </span>
> </span>
> </span>
> </span>
> 
> <span className="vlist-s">
> 
> ​
> 
> </span>
> </span>
> 
> <span className="vlist-r">
> <span className="vlist" style="height:0.15em;">
> <span>
> 
> 
> 
> </span>
> </span>
> </span>
> </span>
> </span>
> </span>
> 
> <span className="mspace">
> 
> 
> 
> </span>
> 
> <span className="mspace">
> 
> 
> 
> </span>
> 
> <span className="mord">
> <span className="mord,mathnormal" style="margin-right:0.0359em;">
> 
> g
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3361em;">
> <span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mtight">
> <span className="mord,mathnormal,mtight">
> 
> mb
> 
> </span>
> </span>
> </span>
> </span>
> </span>
> 
> <span className="vlist-s">
> 
> ​
> 
> </span>
> </span>
> 
> <span className="vlist-r">
> <span className="vlist" style="height:0.15em;">
> <span>
> 
> 
> 
> </span>
> </span>
> </span>
> </span>
> </span>
> </span>
> </span>
> </span>
> </span>
> 
> 的并联电阻
> 
> <span className="katex-display">
> <span className="katex">
> <span className="katex-mathml">
> <math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
> <semantics>
> <mrow>
> <mfrac>
> <mrow>
> <msub>
> <mi>
> 
> r
> 
> </mi>
> 
> <mi>
> 
> o
> 
> </mi>
> </msub>
> 
> <mo>
> 
> +
> 
> </mo>
> 
> <msub>
> <mi>
> 
> R
> 
> </mi>
> 
> <mi>
> 
> D
> 
> </mi>
> </msub>
> </mrow>
> 
> <mrow>
> <mn>
> 
> 1
> 
> </mn>
> 
> <mo>
> 
> +
> 
> </mo>
> 
> <mo stretchy="false">
> 
> (
> 
> </mo>
> 
> <msub>
> <mi>
> 
> g
> 
> </mi>
> 
> <mi>
> 
> m
> 
> </mi>
> </msub>
> 
> <mo>
> 
> +
> 
> </mo>
> 
> <msub>
> <mi>
> 
> g
> 
> </mi>
> 
> <mrow>
> <mi>
> 
> m
> 
> </mi>
> 
> <mi>
> 
> b
> 
> </mi>
> </mrow>
> </msub>
> 
> <mo stretchy="false">
> 
> )
> 
> </mo>
> 
> <msub>
> <mi>
> 
> r
> 
> </mi>
> 
> <mi>
> 
> o
> 
> </mi>
> </msub>
> </mrow>
> </mfrac>
> 
> <mo>
> 
> =
> 
> </mo>
> 
> <mfrac>
> <mn>
> 
> 1
> 
> </mn>
> 
> <mrow>
> <mfrac>
> <mn>
> 
> 1
> 
> </mn>
> 
> <msub>
> <mi>
> 
> r
> 
> </mi>
> 
> <mn>
> 
> 0
> 
> </mn>
> </msub>
> </mfrac>
> 
> <mo>
> 
> +
> 
> </mo>
> 
> <mo stretchy="false">
> 
> (
> 
> </mo>
> 
> <msub>
> <mi>
> 
> g
> 
> </mi>
> 
> <mi>
> 
> m
> 
> </mi>
> </msub>
> 
> <mo>
> 
> +
> 
> </mo>
> 
> <msub>
> <mi>
> 
> g
> 
> </mi>
> 
> <mrow>
> <mi>
> 
> m
> 
> </mi>
> 
> <mi>
> 
> b
> 
> </mi>
> </mrow>
> </msub>
> 
> <mo stretchy="false">
> 
> )
> 
> </mo>
> </mrow>
> </mfrac>
> 
> <mo>
> 
> +
> 
> </mo>
> 
> <mfrac>
> <msub>
> <mi>
> 
> R
> 
> </mi>
> 
> <mi>
> 
> D
> 
> </mi>
> </msub>
> 
> <mrow>
> <mn>
> 
> 1
> 
> </mn>
> 
> <mo>
> 
> +
> 
> </mo>
> 
> <mo stretchy="false">
> 
> (
> 
> </mo>
> 
> <msub>
> <mi>
> 
> g
> 
> </mi>
> 
> <mi>
> 
> m
> 
> </mi>
> </msub>
> 
> <mo>
> 
> +
> 
> </mo>
> 
> <msub>
> <mi>
> 
> g
> 
> </mi>
> 
> <mrow>
> <mi>
> 
> m
> 
> </mi>
> 
> <mi>
> 
> b
> 
> </mi>
> </mrow>
> </msub>
> 
> <mo stretchy="false">
> 
> )
> 
> </mo>
> 
> <msub>
> <mi>
> 
> r
> 
> </mi>
> 
> <mi>
> 
> o
> 
> </mi>
> </msub>
> </mrow>
> </mfrac>
> </mrow>
> 
> <annotation encoding="application/x-tex">
> 
> \frac{r_o + R_D}{1 + (g_m +g_{mb})r_o} = \frac{1}{\frac{1}{r_0} + (g_m +g_{mb})} + \frac{R_D}{1 + (g_m +g_{mb})r_o}
> 
> </annotation>
> </semantics>
> </math>
> </span>
> 
> <span className="katex-html" ariaHidden="true">
> <span className="base">
> <span className="strut" style="height:2.2963em;vertical-align:-0.936em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> <span className="mopen,nulldelimiter">
> 
> 
> 
> </span>
> 
> <span className="mfrac">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:1.3603em;">
> <span style="top:-2.314em;">
> <span className="pstrut" style="height:3em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> <span className="mord">
> 
> 1
> 
> </span>
> 
> <span className="mspace" style="margin-right:0.2222em;">
> 
> 
> 
> </span>
> 
> <span className="mbin">
> 
> +
> 
> </span>
> 
> <span className="mspace" style="margin-right:0.2222em;">
> 
> 
> 
> </span>
> 
> <span className="mopen">
> 
> (
> 
> </span>
> 
> <span className="mord">
> <span className="mord,mathnormal" style="margin-right:0.0359em;">
> 
> g
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.1514em;">
> <span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mathnormal,mtight">
> 
> m
> 
> </span>
> </span>
> </span>
> </span>
> 
> <span className="vlist-s">
> 
> ​
> 
> </span>
> </span>
> 
> <span className="vlist-r">
> <span className="vlist" style="height:0.15em;">
> <span>
> 
> 
> 
> </span>
> </span>
> </span>
> </span>
> </span>
> </span>
> 
> <span className="mspace" style="margin-right:0.2222em;">
> 
> 
> 
> </span>
> 
> <span className="mbin">
> 
> +
> 
> </span>
> 
> <span className="mspace" style="margin-right:0.2222em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> <span className="mord,mathnormal" style="margin-right:0.0359em;">
> 
> g
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3361em;">
> <span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mtight">
> <span className="mord,mathnormal,mtight">
> 
> mb
> 
> </span>
> </span>
> </span>
> </span>
> </span>
> 
> <span className="vlist-s">
> 
> ​
> 
> </span>
> </span>
> 
> <span className="vlist-r">
> <span className="vlist" style="height:0.15em;">
> <span>
> 
> 
> 
> </span>
> </span>
> </span>
> </span>
> </span>
> </span>
> 
> <span className="mclose">
> 
> )
> 
> </span>
> 
> <span className="mord">
> <span className="mord,mathnormal" style="margin-right:0.0278em;">
> 
> r
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.1514em;">
> <span style="top:-2.55em;margin-left:-0.0278em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mathnormal,mtight">
> 
> o
> 
> </span>
> </span>
> </span>
> </span>
> 
> <span className="vlist-s">
> 
> ​
> 
> </span>
> </span>
> 
> <span className="vlist-r">
> <span className="vlist" style="height:0.15em;">
> <span>
> 
> 
> 
> </span>
> </span>
> </span>
> </span>
> </span>
> </span>
> </span>
> </span>
> 
> <span style="top:-3.23em;">
> <span className="pstrut" style="height:3em;">
> 
> 
> 
> </span>
> 
> <span className="frac-line" style="border-bottom-width:0.04em;">
> 
> 
> 
> </span>
> </span>
> 
> <span style="top:-3.677em;">
> <span className="pstrut" style="height:3em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> <span className="mord">
> <span className="mord,mathnormal" style="margin-right:0.0278em;">
> 
> r
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.1514em;">
> <span style="top:-2.55em;margin-left:-0.0278em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mathnormal,mtight">
> 
> o
> 
> </span>
> </span>
> </span>
> </span>
> 
> <span className="vlist-s">
> 
> ​
> 
> </span>
> </span>
> 
> <span className="vlist-r">
> <span className="vlist" style="height:0.15em;">
> <span>
> 
> 
> 
> </span>
> </span>
> </span>
> </span>
> </span>
> </span>
> 
> <span className="mspace" style="margin-right:0.2222em;">
> 
> 
> 
> </span>
> 
> <span className="mbin">
> 
> +
> 
> </span>
> 
> <span className="mspace" style="margin-right:0.2222em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> <span className="mord,mathnormal" style="margin-right:0.0077em;">
> 
> R
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3283em;">
> <span style="top:-2.55em;margin-left:-0.0077em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">
> 
> D
> 
> </span>
> </span>
> </span>
> </span>
> 
> <span className="vlist-s">
> 
> ​
> 
> </span>
> </span>
> 
> <span className="vlist-r">
> <span className="vlist" style="height:0.15em;">
> <span>
> 
> 
> 
> </span>
> </span>
> </span>
> </span>
> </span>
> </span>
> </span>
> </span>
> </span>
> 
> <span className="vlist-s">
> 
> ​
> 
> </span>
> </span>
> 
> <span className="vlist-r">
> <span className="vlist" style="height:0.936em;">
> <span>
> 
> 
> 
> </span>
> </span>
> </span>
> </span>
> </span>
> 
> <span className="mclose,nulldelimiter">
> 
> 
> 
> </span>
> </span>
> 
> <span className="mspace" style="margin-right:0.2778em;">
> 
> 
> 
> </span>
> 
> <span className="mrel">
> 
> =
> 
> </span>
> 
> <span className="mspace" style="margin-right:0.2778em;">
> 
> 
> 
> </span>
> </span>
> 
> <span className="base">
> <span className="strut" style="height:2.5016em;vertical-align:-1.1802em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> <span className="mopen,nulldelimiter">
> 
> 
> 
> </span>
> 
> <span className="mfrac">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:1.3214em;">
> <span style="top:-2.2649em;">
> <span className="pstrut" style="height:3em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> <span className="mord">
> <span className="mopen,nulldelimiter">
> 
> 
> 
> </span>
> 
> <span className="mfrac">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.8451em;">
> <span style="top:-2.655em;">
> <span className="pstrut" style="height:3em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mtight">
> <span className="mord,mtight">
> <span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">
> 
> r
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3173em;">
> <span style="top:-2.357em;margin-left:-0.0278em;margin-right:0.0714em;">
> <span className="pstrut" style="height:2.5em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size3,size1,mtight">
> <span className="mord,mtight">
> 
> 0
> 
> </span>
> </span>
> </span>
> </span>
> 
> <span className="vlist-s">
> 
> ​
> 
> </span>
> </span>
> 
> <span className="vlist-r">
> <span className="vlist" style="height:0.143em;">
> <span>
> 
> 
> 
> </span>
> </span>
> </span>
> </span>
> </span>
> </span>
> </span>
> </span>
> </span>
> 
> <span style="top:-3.23em;">
> <span className="pstrut" style="height:3em;">
> 
> 
> 
> </span>
> 
> <span className="frac-line" style="border-bottom-width:0.04em;">
> 
> 
> 
> </span>
> </span>
> 
> <span style="top:-3.394em;">
> <span className="pstrut" style="height:3em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mtight">
> <span className="mord,mtight">
> 
> 1
> 
> </span>
> </span>
> </span>
> </span>
> </span>
> 
> <span className="vlist-s">
> 
> ​
> 
> </span>
> </span>
> 
> <span className="vlist-r">
> <span className="vlist" style="height:0.4451em;">
> <span>
> 
> 
> 
> </span>
> </span>
> </span>
> </span>
> </span>
> 
> <span className="mclose,nulldelimiter">
> 
> 
> 
> </span>
> </span>
> 
> <span className="mspace" style="margin-right:0.2222em;">
> 
> 
> 
> </span>
> 
> <span className="mbin">
> 
> +
> 
> </span>
> 
> <span className="mspace" style="margin-right:0.2222em;">
> 
> 
> 
> </span>
> 
> <span className="mopen">
> 
> (
> 
> </span>
> 
> <span className="mord">
> <span className="mord,mathnormal" style="margin-right:0.0359em;">
> 
> g
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.1514em;">
> <span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mathnormal,mtight">
> 
> m
> 
> </span>
> </span>
> </span>
> </span>
> 
> <span className="vlist-s">
> 
> ​
> 
> </span>
> </span>
> 
> <span className="vlist-r">
> <span className="vlist" style="height:0.15em;">
> <span>
> 
> 
> 
> </span>
> </span>
> </span>
> </span>
> </span>
> </span>
> 
> <span className="mspace" style="margin-right:0.2222em;">
> 
> 
> 
> </span>
> 
> <span className="mbin">
> 
> +
> 
> </span>
> 
> <span className="mspace" style="margin-right:0.2222em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> <span className="mord,mathnormal" style="margin-right:0.0359em;">
> 
> g
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3361em;">
> <span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mtight">
> <span className="mord,mathnormal,mtight">
> 
> mb
> 
> </span>
> </span>
> </span>
> </span>
> </span>
> 
> <span className="vlist-s">
> 
> ​
> 
> </span>
> </span>
> 
> <span className="vlist-r">
> <span className="vlist" style="height:0.15em;">
> <span>
> 
> 
> 
> </span>
> </span>
> </span>
> </span>
> </span>
> </span>
> 
> <span className="mclose">
> 
> )
> 
> </span>
> </span>
> </span>
> 
> <span style="top:-3.23em;">
> <span className="pstrut" style="height:3em;">
> 
> 
> 
> </span>
> 
> <span className="frac-line" style="border-bottom-width:0.04em;">
> 
> 
> 
> </span>
> </span>
> 
> <span style="top:-3.677em;">
> <span className="pstrut" style="height:3em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> <span className="mord">
> 
> 1
> 
> </span>
> </span>
> </span>
> </span>
> 
> <span className="vlist-s">
> 
> ​
> 
> </span>
> </span>
> 
> <span className="vlist-r">
> <span className="vlist" style="height:1.1802em;">
> <span>
> 
> 
> 
> </span>
> </span>
> </span>
> </span>
> </span>
> 
> <span className="mclose,nulldelimiter">
> 
> 
> 
> </span>
> </span>
> 
> <span className="mspace" style="margin-right:0.2222em;">
> 
> 
> 
> </span>
> 
> <span className="mbin">
> 
> +
> 
> </span>
> 
> <span className="mspace" style="margin-right:0.2222em;">
> 
> 
> 
> </span>
> </span>
> 
> <span className="base">
> <span className="strut" style="height:2.2963em;vertical-align:-0.936em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> <span className="mopen,nulldelimiter">
> 
> 
> 
> </span>
> 
> <span className="mfrac">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:1.3603em;">
> <span style="top:-2.314em;">
> <span className="pstrut" style="height:3em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> <span className="mord">
> 
> 1
> 
> </span>
> 
> <span className="mspace" style="margin-right:0.2222em;">
> 
> 
> 
> </span>
> 
> <span className="mbin">
> 
> +
> 
> </span>
> 
> <span className="mspace" style="margin-right:0.2222em;">
> 
> 
> 
> </span>
> 
> <span className="mopen">
> 
> (
> 
> </span>
> 
> <span className="mord">
> <span className="mord,mathnormal" style="margin-right:0.0359em;">
> 
> g
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.1514em;">
> <span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mathnormal,mtight">
> 
> m
> 
> </span>
> </span>
> </span>
> </span>
> 
> <span className="vlist-s">
> 
> ​
> 
> </span>
> </span>
> 
> <span className="vlist-r">
> <span className="vlist" style="height:0.15em;">
> <span>
> 
> 
> 
> </span>
> </span>
> </span>
> </span>
> </span>
> </span>
> 
> <span className="mspace" style="margin-right:0.2222em;">
> 
> 
> 
> </span>
> 
> <span className="mbin">
> 
> +
> 
> </span>
> 
> <span className="mspace" style="margin-right:0.2222em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> <span className="mord,mathnormal" style="margin-right:0.0359em;">
> 
> g
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3361em;">
> <span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mtight">
> <span className="mord,mathnormal,mtight">
> 
> mb
> 
> </span>
> </span>
> </span>
> </span>
> </span>
> 
> <span className="vlist-s">
> 
> ​
> 
> </span>
> </span>
> 
> <span className="vlist-r">
> <span className="vlist" style="height:0.15em;">
> <span>
> 
> 
> 
> </span>
> </span>
> </span>
> </span>
> </span>
> </span>
> 
> <span className="mclose">
> 
> )
> 
> </span>
> 
> <span className="mord">
> <span className="mord,mathnormal" style="margin-right:0.0278em;">
> 
> r
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.1514em;">
> <span style="top:-2.55em;margin-left:-0.0278em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mathnormal,mtight">
> 
> o
> 
> </span>
> </span>
> </span>
> </span>
> 
> <span className="vlist-s">
> 
> ​
> 
> </span>
> </span>
> 
> <span className="vlist-r">
> <span className="vlist" style="height:0.15em;">
> <span>
> 
> 
> 
> </span>
> </span>
> </span>
> </span>
> </span>
> </span>
> </span>
> </span>
> 
> <span style="top:-3.23em;">
> <span className="pstrut" style="height:3em;">
> 
> 
> 
> </span>
> 
> <span className="frac-line" style="border-bottom-width:0.04em;">
> 
> 
> 
> </span>
> </span>
> 
> <span style="top:-3.677em;">
> <span className="pstrut" style="height:3em;">
> 
> 
> 
> </span>
> 
> <span className="mord">
> <span className="mord">
> <span className="mord,mathnormal" style="margin-right:0.0077em;">
> 
> R
> 
> </span>
> 
> <span className="msupsub">
> <span className="vlist-t,vlist-t2">
> <span className="vlist-r">
> <span className="vlist" style="height:0.3283em;">
> <span style="top:-2.55em;margin-left:-0.0077em;margin-right:0.05em;">
> <span className="pstrut" style="height:2.7em;">
> 
> 
> 
> </span>
> 
> <span className="sizing,reset-size6,size3,mtight">
> <span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">
> 
> D
> 
> </span>
> </span>
> </span>
> </span>
> 
> <span className="vlist-s">
> 
> ​
> 
> </span>
> </span>
> 
> <span className="vlist-r">
> <span className="vlist" style="height:0.15em;">
> <span>
> 
> 
> 
> </span>
> </span>
> </span>
> </span>
> </span>
> </span>
> </span>
> </span>
> </span>
> 
> <span className="vlist-s">
> 
> ​
> 
> </span>
> </span>
> 
> <span className="vlist-r">
> <span className="vlist" style="height:0.936em;">
> <span>
> 
> 
> 
> </span>
> </span>
> </span>
> </span>
> </span>
> 
> <span className="mclose,nulldelimiter">
> 
> 
> 
> </span>
> </span>
> </span>
> </span>
> </span>
> </span>

1. **传统（长沟道）器件：**
  - <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <msub>
  <mi>
  
  r
  
  </mi>
  
  <mi>
  
  O
  
  </mi>
  </msub>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  r_O
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:0.5806em;vertical-align:-0.15em;">
  
  
  
  </span>
  
  <span className="mord">
  <span className="mord,mathnormal" style="margin-right:0.0278em;">
  
  r
  
  </span>
  
  <span className="msupsub">
  <span className="vlist-t,vlist-t2">
  <span className="vlist-r">
  <span className="vlist" style="height:0.3283em;">
  <span style="top:-2.55em;margin-left:-0.0278em;margin-right:0.05em;">
  <span className="pstrut" style="height:2.7em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size6,size3,mtight">
  <span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">
  
  O
  
  </span>
  </span>
  </span>
  </span>
  
  <span className="vlist-s">
  
  ​
  
  </span>
  </span>
  
  <span className="vlist-r">
  <span className="vlist" style="height:0.15em;">
  <span>
  
  
  
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  
   很大，本征增益 <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mo stretchy="false">
  
  (
  
  </mo>
  
  <msub>
  <mi>
  
  g
  
  </mi>
  
  <mi>
  
  m
  
  </mi>
  </msub>
  
  <mo>
  
  +
  
  </mo>
  
  <msub>
  <mi>
  
  g
  
  </mi>
  
  <mrow>
  <mi>
  
  m
  
  </mi>
  
  <mi>
  
  b
  
  </mi>
  </mrow>
  </msub>
  
  <mo stretchy="false">
  
  )
  
  </mo>
  
  <msub>
  <mi>
  
  r
  
  </mi>
  
  <mi>
  
  O
  
  </mi>
  </msub>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  (g_m + g_{mb}) r_O
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:1em;vertical-align:-0.25em;">
  
  
  
  </span>
  
  <span className="mopen">
  
  (
  
  </span>
  
  <span className="mord">
  <span className="mord,mathnormal" style="margin-right:0.0359em;">
  
  g
  
  </span>
  
  <span className="msupsub">
  <span className="vlist-t,vlist-t2">
  <span className="vlist-r">
  <span className="vlist" style="height:0.1514em;">
  <span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
  <span className="pstrut" style="height:2.7em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size6,size3,mtight">
  <span className="mord,mathnormal,mtight">
  
  m
  
  </span>
  </span>
  </span>
  </span>
  
  <span className="vlist-s">
  
  ​
  
  </span>
  </span>
  
  <span className="vlist-r">
  <span className="vlist" style="height:0.15em;">
  <span>
  
  
  
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  
  <span className="mspace" style="margin-right:0.2222em;">
  
  
  
  </span>
  
  <span className="mbin">
  
  +
  
  </span>
  
  <span className="mspace" style="margin-right:0.2222em;">
  
  
  
  </span>
  </span>
  
  <span className="base">
  <span className="strut" style="height:1em;vertical-align:-0.25em;">
  
  
  
  </span>
  
  <span className="mord">
  <span className="mord,mathnormal" style="margin-right:0.0359em;">
  
  g
  
  </span>
  
  <span className="msupsub">
  <span className="vlist-t,vlist-t2">
  <span className="vlist-r">
  <span className="vlist" style="height:0.3361em;">
  <span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
  <span className="pstrut" style="height:2.7em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size6,size3,mtight">
  <span className="mord,mtight">
  <span className="mord,mathnormal,mtight">
  
  mb
  
  </span>
  </span>
  </span>
  </span>
  </span>
  
  <span className="vlist-s">
  
  ​
  
  </span>
  </span>
  
  <span className="vlist-r">
  <span className="vlist" style="height:0.15em;">
  <span>
  
  
  
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  
  <span className="mclose">
  
  )
  
  </span>
  
  <span className="mord">
  <span className="mord,mathnormal" style="margin-right:0.0278em;">
  
  r
  
  </span>
  
  <span className="msupsub">
  <span className="vlist-t,vlist-t2">
  <span className="vlist-r">
  <span className="vlist" style="height:0.3283em;">
  <span style="top:-2.55em;margin-left:-0.0278em;margin-right:0.05em;">
  <span className="pstrut" style="height:2.7em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size6,size3,mtight">
  <span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">
  
  O
  
  </span>
  </span>
  </span>
  </span>
  
  <span className="vlist-s">
  
  ​
  
  </span>
  </span>
  
  <span className="vlist-r">
  <span className="vlist" style="height:0.15em;">
  <span>
  
  
  
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  
   非常高（比如 > 100）。
  - <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mfrac>
  <msub>
  <mi>
  
  R
  
  </mi>
  
  <mi>
  
  D
  
  </mi>
  </msub>
  
  <mrow>
  <mo stretchy="false">
  
  (
  
  </mo>
  
  <msub>
  <mi>
  
  g
  
  </mi>
  
  <mi>
  
  m
  
  </mi>
  </msub>
  
  <mo>
  
  +
  
  </mo>
  
  <msub>
  <mi>
  
  g
  
  </mi>
  
  <mrow>
  <mi>
  
  m
  
  </mi>
  
  <mi>
  
  b
  
  </mi>
  </mrow>
  </msub>
  
  <mo stretchy="false">
  
  )
  
  </mo>
  
  <msub>
  <mi>
  
  r
  
  </mi>
  
  <mi>
  
  O
  
  </mi>
  </msub>
  </mrow>
  </mfrac>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  \frac{R_D}{(g_m + g_{mb}) r_O}
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:1.4086em;vertical-align:-0.52em;">
  
  
  
  </span>
  
  <span className="mord">
  <span className="mopen,nulldelimiter">
  
  
  
  </span>
  
  <span className="mfrac">
  <span className="vlist-t,vlist-t2">
  <span className="vlist-r">
  <span className="vlist" style="height:0.8886em;">
  <span style="top:-2.655em;">
  <span className="pstrut" style="height:3em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size6,size3,mtight">
  <span className="mord,mtight">
  <span className="mopen,mtight">
  
  (
  
  </span>
  
  <span className="mord,mtight">
  <span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">
  
  g
  
  </span>
  
  <span className="msupsub">
  <span className="vlist-t,vlist-t2">
  <span className="vlist-r">
  <span className="vlist" style="height:0.1645em;">
  <span style="top:-2.357em;margin-left:-0.0359em;margin-right:0.0714em;">
  <span className="pstrut" style="height:2.5em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size3,size1,mtight">
  <span className="mord,mathnormal,mtight">
  
  m
  
  </span>
  </span>
  </span>
  </span>
  
  <span className="vlist-s">
  
  ​
  
  </span>
  </span>
  
  <span className="vlist-r">
  <span className="vlist" style="height:0.143em;">
  <span>
  
  
  
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  
  <span className="mbin,mtight">
  
  +
  
  </span>
  
  <span className="mord,mtight">
  <span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">
  
  g
  
  </span>
  
  <span className="msupsub">
  <span className="vlist-t,vlist-t2">
  <span className="vlist-r">
  <span className="vlist" style="height:0.3448em;">
  <span style="top:-2.3488em;margin-left:-0.0359em;margin-right:0.0714em;">
  <span className="pstrut" style="height:2.5em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size3,size1,mtight">
  <span className="mord,mtight">
  <span className="mord,mathnormal,mtight">
  
  mb
  
  </span>
  </span>
  </span>
  </span>
  </span>
  
  <span className="vlist-s">
  
  ​
  
  </span>
  </span>
  
  <span className="vlist-r">
  <span className="vlist" style="height:0.1512em;">
  <span>
  
  
  
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  
  <span className="mclose,mtight">
  
  )
  
  </span>
  
  <span className="mord,mtight">
  <span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">
  
  r
  
  </span>
  
  <span className="msupsub">
  <span className="vlist-t,vlist-t2">
  <span className="vlist-r">
  <span className="vlist" style="height:0.3448em;">
  <span style="top:-2.3567em;margin-left:-0.0278em;margin-right:0.0714em;">
  <span className="pstrut" style="height:2.5em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size3,size1,mtight">
  <span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">
  
  O
  
  </span>
  </span>
  </span>
  </span>
  
  <span className="vlist-s">
  
  ​
  
  </span>
  </span>
  
  <span className="vlist-r">
  <span className="vlist" style="height:0.1433em;">
  <span>
  
  
  
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  
  <span style="top:-3.23em;">
  <span className="pstrut" style="height:3em;">
  
  
  
  </span>
  
  <span className="frac-line" style="border-bottom-width:0.04em;">
  
  
  
  </span>
  </span>
  
  <span style="top:-3.4103em;">
  <span className="pstrut" style="height:3em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size6,size3,mtight">
  <span className="mord,mtight">
  <span className="mord,mtight">
  <span className="mord,mathnormal,mtight" style="margin-right:0.0077em;">
  
  R
  
  </span>
  
  <span className="msupsub">
  <span className="vlist-t,vlist-t2">
  <span className="vlist-r">
  <span className="vlist" style="height:0.3448em;">
  <span style="top:-2.3567em;margin-left:-0.0077em;margin-right:0.0714em;">
  <span className="pstrut" style="height:2.5em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size3,size1,mtight">
  <span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">
  
  D
  
  </span>
  </span>
  </span>
  </span>
  
  <span className="vlist-s">
  
  ​
  
  </span>
  </span>
  
  <span className="vlist-r">
  <span className="vlist" style="height:0.1433em;">
  <span>
  
  
  
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  
  <span className="vlist-s">
  
  ​
  
  </span>
  </span>
  
  <span className="vlist-r">
  <span className="vlist" style="height:0.52em;">
  <span>
  
  
  
  </span>
  </span>
  </span>
  </span>
  </span>
  
  <span className="mclose,nulldelimiter">
  
  
  
  </span>
  </span>
  </span>
  </span>
  </span>
  
   这一项非常小，**可以忽略**。
  - <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <msub>
  <mi>
  
  R
  
  </mi>
  
  <mrow>
  <mi>
  
  i
  
  </mi>
  
  <mi>
  
  n
  
  </mi>
  </mrow>
  </msub>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  R_{in}
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:0.8333em;vertical-align:-0.15em;">
  
  
  
  </span>
  
  <span className="mord">
  <span className="mord,mathnormal" style="margin-right:0.0077em;">
  
  R
  
  </span>
  
  <span className="msupsub">
  <span className="vlist-t,vlist-t2">
  <span className="vlist-r">
  <span className="vlist" style="height:0.3117em;">
  <span style="top:-2.55em;margin-left:-0.0077em;margin-right:0.05em;">
  <span className="pstrut" style="height:2.7em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size6,size3,mtight">
  <span className="mord,mtight">
  <span className="mord,mathnormal,mtight">
  
  in
  
  </span>
  </span>
  </span>
  </span>
  </span>
  
  <span className="vlist-s">
  
  ​
  
  </span>
  </span>
  
  <span className="vlist-r">
  <span className="vlist" style="height:0.15em;">
  <span>
  
  
  
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  
   **约等于** <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mfrac>
  <mn>
  
  1
  
  </mn>
  
  <mrow>
  <msub>
  <mi>
  
  g
  
  </mi>
  
  <mi>
  
  m
  
  </mi>
  </msub>
  
  <mo>
  
  +
  
  </mo>
  
  <msub>
  <mi>
  
  g
  
  </mi>
  
  <mrow>
  <mi>
  
  m
  
  </mi>
  
  <mi>
  
  b
  
  </mi>
  </mrow>
  </msub>
  </mrow>
  </mfrac>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  \frac{1}{g_m + g_{mb}}
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:1.3262em;vertical-align:-0.4811em;">
  
  
  
  </span>
  
  <span className="mord">
  <span className="mopen,nulldelimiter">
  
  
  
  </span>
  
  <span className="mfrac">
  <span className="vlist-t,vlist-t2">
  <span className="vlist-r">
  <span className="vlist" style="height:0.8451em;">
  <span style="top:-2.655em;">
  <span className="pstrut" style="height:3em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size6,size3,mtight">
  <span className="mord,mtight">
  <span className="mord,mtight">
  <span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">
  
  g
  
  </span>
  
  <span className="msupsub">
  <span className="vlist-t,vlist-t2">
  <span className="vlist-r">
  <span className="vlist" style="height:0.1645em;">
  <span style="top:-2.357em;margin-left:-0.0359em;margin-right:0.0714em;">
  <span className="pstrut" style="height:2.5em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size3,size1,mtight">
  <span className="mord,mathnormal,mtight">
  
  m
  
  </span>
  </span>
  </span>
  </span>
  
  <span className="vlist-s">
  
  ​
  
  </span>
  </span>
  
  <span className="vlist-r">
  <span className="vlist" style="height:0.143em;">
  <span>
  
  
  
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  
  <span className="mbin,mtight">
  
  +
  
  </span>
  
  <span className="mord,mtight">
  <span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">
  
  g
  
  </span>
  
  <span className="msupsub">
  <span className="vlist-t,vlist-t2">
  <span className="vlist-r">
  <span className="vlist" style="height:0.3448em;">
  <span style="top:-2.3488em;margin-left:-0.0359em;margin-right:0.0714em;">
  <span className="pstrut" style="height:2.5em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size3,size1,mtight">
  <span className="mord,mtight">
  <span className="mord,mathnormal,mtight">
  
  mb
  
  </span>
  </span>
  </span>
  </span>
  </span>
  
  <span className="vlist-s">
  
  ​
  
  </span>
  </span>
  
  <span className="vlist-r">
  <span className="vlist" style="height:0.1512em;">
  <span>
  
  
  
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  
  <span style="top:-3.23em;">
  <span className="pstrut" style="height:3em;">
  
  
  
  </span>
  
  <span className="frac-line" style="border-bottom-width:0.04em;">
  
  
  
  </span>
  </span>
  
  <span style="top:-3.394em;">
  <span className="pstrut" style="height:3em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size6,size3,mtight">
  <span className="mord,mtight">
  <span className="mord,mtight">
  
  1
  
  </span>
  </span>
  </span>
  </span>
  </span>
  
  <span className="vlist-s">
  
  ​
  
  </span>
  </span>
  
  <span className="vlist-r">
  <span className="vlist" style="height:0.4811em;">
  <span>
  
  
  
  </span>
  </span>
  </span>
  </span>
  </span>
  
  <span className="mclose,nulldelimiter">
  
  
  
  </span>
  </span>
  </span>
  </span>
  </span>
2. **现代（短沟道）器件：**
  - <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <msub>
  <mi>
  
  r
  
  </mi>
  
  <mi>
  
  O
  
  </mi>
  </msub>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  r_O
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:0.5806em;vertical-align:-0.15em;">
  
  
  
  </span>
  
  <span className="mord">
  <span className="mord,mathnormal" style="margin-right:0.0278em;">
  
  r
  
  </span>
  
  <span className="msupsub">
  <span className="vlist-t,vlist-t2">
  <span className="vlist-r">
  <span className="vlist" style="height:0.3283em;">
  <span style="top:-2.55em;margin-left:-0.0278em;margin-right:0.05em;">
  <span className="pstrut" style="height:2.7em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size6,size3,mtight">
  <span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">
  
  O
  
  </span>
  </span>
  </span>
  </span>
  
  <span className="vlist-s">
  
  ​
  
  </span>
  </span>
  
  <span className="vlist-r">
  <span className="vlist" style="height:0.15em;">
  <span>
  
  
  
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  
   **非常小**（沟道长度调制效应严重）。
  - 导致其**本征增益**<span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mfrac>
  <mn>
  
  1
  
  </mn>
  
  <mrow>
  <msub>
  <mi>
  
  g
  
  </mi>
  
  <mi>
  
  m
  
  </mi>
  </msub>
  
  <mo>
  
  +
  
  </mo>
  
  <msub>
  <mi>
  
  g
  
  </mi>
  
  <mrow>
  <mi>
  
  m
  
  </mi>
  
  <mi>
  
  b
  
  </mi>
  </mrow>
  </msub>
  </mrow>
  </mfrac>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  \frac{1}{g_m + g_{mb}}
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:1.3262em;vertical-align:-0.4811em;">
  
  
  
  </span>
  
  <span className="mord">
  <span className="mopen,nulldelimiter">
  
  
  
  </span>
  
  <span className="mfrac">
  <span className="vlist-t,vlist-t2">
  <span className="vlist-r">
  <span className="vlist" style="height:0.8451em;">
  <span style="top:-2.655em;">
  <span className="pstrut" style="height:3em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size6,size3,mtight">
  <span className="mord,mtight">
  <span className="mord,mtight">
  <span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">
  
  g
  
  </span>
  
  <span className="msupsub">
  <span className="vlist-t,vlist-t2">
  <span className="vlist-r">
  <span className="vlist" style="height:0.1645em;">
  <span style="top:-2.357em;margin-left:-0.0359em;margin-right:0.0714em;">
  <span className="pstrut" style="height:2.5em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size3,size1,mtight">
  <span className="mord,mathnormal,mtight">
  
  m
  
  </span>
  </span>
  </span>
  </span>
  
  <span className="vlist-s">
  
  ​
  
  </span>
  </span>
  
  <span className="vlist-r">
  <span className="vlist" style="height:0.143em;">
  <span>
  
  
  
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  
  <span className="mbin,mtight">
  
  +
  
  </span>
  
  <span className="mord,mtight">
  <span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">
  
  g
  
  </span>
  
  <span className="msupsub">
  <span className="vlist-t,vlist-t2">
  <span className="vlist-r">
  <span className="vlist" style="height:0.3448em;">
  <span style="top:-2.3488em;margin-left:-0.0359em;margin-right:0.0714em;">
  <span className="pstrut" style="height:2.5em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size3,size1,mtight">
  <span className="mord,mtight">
  <span className="mord,mathnormal,mtight">
  
  mb
  
  </span>
  </span>
  </span>
  </span>
  </span>
  
  <span className="vlist-s">
  
  ​
  
  </span>
  </span>
  
  <span className="vlist-r">
  <span className="vlist" style="height:0.1512em;">
  <span>
  
  
  
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  
  <span style="top:-3.23em;">
  <span className="pstrut" style="height:3em;">
  
  
  
  </span>
  
  <span className="frac-line" style="border-bottom-width:0.04em;">
  
  
  
  </span>
  </span>
  
  <span style="top:-3.394em;">
  <span className="pstrut" style="height:3em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size6,size3,mtight">
  <span className="mord,mtight">
  <span className="mord,mtight">
  
  1
  
  </span>
  </span>
  </span>
  </span>
  </span>
  
  <span className="vlist-s">
  
  ​
  
  </span>
  </span>
  
  <span className="vlist-r">
  <span className="vlist" style="height:0.4811em;">
  <span>
  
  
  
  </span>
  </span>
  </span>
  </span>
  </span>
  
  <span className="mclose,nulldelimiter">
  
  
  
  </span>
  </span>
  </span>
  </span>
  </span>
  
  **很低**（比如可能只有 5 或 10）。
  - <span className="katex">
  <span className="katex-mathml">
  <math xmlns="http://www.w3.org/1998/Math/MathML">
  <semantics>
  <mrow>
  <mfrac>
  <msub>
  <mi>
  
  R
  
  </mi>
  
  <mi>
  
  D
  
  </mi>
  </msub>
  
  <mrow>
  <mo stretchy="false">
  
  (
  
  </mo>
  
  <msub>
  <mi>
  
  g
  
  </mi>
  
  <mi>
  
  m
  
  </mi>
  </msub>
  
  <mo>
  
  +
  
  </mo>
  
  <msub>
  <mi>
  
  g
  
  </mi>
  
  <mrow>
  <mi>
  
  m
  
  </mi>
  
  <mi>
  
  b
  
  </mi>
  </mrow>
  </msub>
  
  <mo stretchy="false">
  
  )
  
  </mo>
  
  <msub>
  <mi>
  
  r
  
  </mi>
  
  <mi>
  
  O
  
  </mi>
  </msub>
  </mrow>
  </mfrac>
  </mrow>
  
  <annotation encoding="application/x-tex">
  
  \frac{R_D}{(g_m + g_{mb}) r_O}
  
  </annotation>
  </semantics>
  </math>
  </span>
  
  <span className="katex-html" ariaHidden="true">
  <span className="base">
  <span className="strut" style="height:1.4086em;vertical-align:-0.52em;">
  
  
  
  </span>
  
  <span className="mord">
  <span className="mopen,nulldelimiter">
  
  
  
  </span>
  
  <span className="mfrac">
  <span className="vlist-t,vlist-t2">
  <span className="vlist-r">
  <span className="vlist" style="height:0.8886em;">
  <span style="top:-2.655em;">
  <span className="pstrut" style="height:3em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size6,size3,mtight">
  <span className="mord,mtight">
  <span className="mopen,mtight">
  
  (
  
  </span>
  
  <span className="mord,mtight">
  <span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">
  
  g
  
  </span>
  
  <span className="msupsub">
  <span className="vlist-t,vlist-t2">
  <span className="vlist-r">
  <span className="vlist" style="height:0.1645em;">
  <span style="top:-2.357em;margin-left:-0.0359em;margin-right:0.0714em;">
  <span className="pstrut" style="height:2.5em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size3,size1,mtight">
  <span className="mord,mathnormal,mtight">
  
  m
  
  </span>
  </span>
  </span>
  </span>
  
  <span className="vlist-s">
  
  ​
  
  </span>
  </span>
  
  <span className="vlist-r">
  <span className="vlist" style="height:0.143em;">
  <span>
  
  
  
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  
  <span className="mbin,mtight">
  
  +
  
  </span>
  
  <span className="mord,mtight">
  <span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">
  
  g
  
  </span>
  
  <span className="msupsub">
  <span className="vlist-t,vlist-t2">
  <span className="vlist-r">
  <span className="vlist" style="height:0.3448em;">
  <span style="top:-2.3488em;margin-left:-0.0359em;margin-right:0.0714em;">
  <span className="pstrut" style="height:2.5em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size3,size1,mtight">
  <span className="mord,mtight">
  <span className="mord,mathnormal,mtight">
  
  mb
  
  </span>
  </span>
  </span>
  </span>
  </span>
  
  <span className="vlist-s">
  
  ​
  
  </span>
  </span>
  
  <span className="vlist-r">
  <span className="vlist" style="height:0.1512em;">
  <span>
  
  
  
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  
  <span className="mclose,mtight">
  
  )
  
  </span>
  
  <span className="mord,mtight">
  <span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">
  
  r
  
  </span>
  
  <span className="msupsub">
  <span className="vlist-t,vlist-t2">
  <span className="vlist-r">
  <span className="vlist" style="height:0.3448em;">
  <span style="top:-2.3567em;margin-left:-0.0278em;margin-right:0.0714em;">
  <span className="pstrut" style="height:2.5em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size3,size1,mtight">
  <span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">
  
  O
  
  </span>
  </span>
  </span>
  </span>
  
  <span className="vlist-s">
  
  ​
  
  </span>
  </span>
  
  <span className="vlist-r">
  <span className="vlist" style="height:0.1433em;">
  <span>
  
  
  
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  
  <span style="top:-3.23em;">
  <span className="pstrut" style="height:3em;">
  
  
  
  </span>
  
  <span className="frac-line" style="border-bottom-width:0.04em;">
  
  
  
  </span>
  </span>
  
  <span style="top:-3.4103em;">
  <span className="pstrut" style="height:3em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size6,size3,mtight">
  <span className="mord,mtight">
  <span className="mord,mtight">
  <span className="mord,mathnormal,mtight" style="margin-right:0.0077em;">
  
  R
  
  </span>
  
  <span className="msupsub">
  <span className="vlist-t,vlist-t2">
  <span className="vlist-r">
  <span className="vlist" style="height:0.3448em;">
  <span style="top:-2.3567em;margin-left:-0.0077em;margin-right:0.0714em;">
  <span className="pstrut" style="height:2.5em;">
  
  
  
  </span>
  
  <span className="sizing,reset-size3,size1,mtight">
  <span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">
  
  D
  
  </span>
  </span>
  </span>
  </span>
  
  <span className="vlist-s">
  
  ​
  
  </span>
  </span>
  
  <span className="vlist-r">
  <span className="vlist" style="height:0.1433em;">
  <span>
  
  
  
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  </span>
  
  <span className="vlist-s">
  
  ​
  
  </span>
  </span>
  
  <span className="vlist-r">
  <span className="vlist" style="height:0.52em;">
  <span>
  
  
  
  </span>
  </span>
  </span>
  </span>
  </span>
  
  <span className="mclose,nulldelimiter">
  
  
  
  </span>
  </span>
  </span>
  </span>
  </span>
  
   这一项的分母很小，导致**这一项本身不再可以忽略**！

对于<mark>

现代的短沟道工艺

</mark>

，**不能再简单地**使用 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mfrac>
<mn>

1

</mn>

<mrow>
<msub>
<mi>

g

</mi>

<mi>

m

</mi>
</msub>

<mo>

+

</mo>

<msub>
<mi>

g

</mi>

<mrow>
<mi>

m

</mi>

<mi>

b

</mi>
</mrow>
</msub>
</mrow>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

\frac{1}{g_m + g_{mb}}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.3262em;vertical-align:-0.4811em;">



</span>

<span className="mord">
<span className="mopen,nulldelimiter">



</span>

<span className="mfrac">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.8451em;">
<span style="top:-2.655em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

g

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1645em;">
<span style="top:-2.357em;margin-left:-0.0359em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
<span className="mord,mathnormal,mtight">

m

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.143em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>

<span className="mbin,mtight">

+

</span>

<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

g

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3448em;">
<span style="top:-2.3488em;margin-left:-0.0359em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

mb

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.1512em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

<span style="top:-3.23em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="frac-line" style="border-bottom-width:0.04em;">



</span>
</span>

<span style="top:-3.394em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">

1

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.4811em;">
<span>



</span>
</span>
</span>
</span>
</span>

<span className="mclose,nulldelimiter">



</span>
</span>
</span>
</span>
</span>

 ， <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

R

</mi>

<mrow>
<mi>

i

</mi>

<mi>

n

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

R_{in}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0077em;">

R

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0077em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

in

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

 **会受到** <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

R

</mi>

<mi>

D

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

R_D

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0077em;">

R

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.0077em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

D

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

 **的影响**，因为短沟道器件的“增益”太低，无法有效地将 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

R

</mi>

<mi>

D

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

R_D

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0077em;">

R

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.0077em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

D

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

 的影响从输入端“屏蔽”掉。

1. 体效应越强（<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

g

</mi>

<mrow>
<mi>

m

</mi>

<mi>

b

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

g_{mb}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.625em;vertical-align:-0.1944em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

g

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

mb

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

 越大），<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

R

</mi>

<mrow>
<mi>

i

</mi>

<mi>

n

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

R_{in}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0077em;">

R

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0077em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

in

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

 就会越小
2. **只有当**漏极负载 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

R

</mi>

<mi>

D

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

R_D

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0077em;">

R

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.0077em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

D

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

 非常小（接近短路）时，<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

R

</mi>

<mrow>
<mi>

i

</mi>

<mi>

n

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

R_{in}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0077em;">

R

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0077em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

in

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

 才约等于 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mfrac>
<mn>

1

</mn>

<msub>
<mi>

g

</mi>

<mi>

m

</mi>
</msub>
</mfrac>
</mrow>

<annotation encoding="application/x-tex">

\frac{1}{g_m}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1.3262em;vertical-align:-0.4811em;">



</span>

<span className="mord">
<span className="mopen,nulldelimiter">



</span>

<span className="mfrac">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.8451em;">
<span style="top:-2.655em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

g

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1645em;">
<span style="top:-2.357em;margin-left:-0.0359em;margin-right:0.0714em;">
<span className="pstrut" style="height:2.5em;">



</span>

<span className="sizing,reset-size3,size1,mtight">
<span className="mord,mathnormal,mtight">

m

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.143em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

<span style="top:-3.23em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="frac-line" style="border-bottom-width:0.04em;">



</span>
</span>

<span style="top:-3.394em;">
<span className="pstrut" style="height:3em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mtight">

1

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.4811em;">
<span>



</span>
</span>
</span>
</span>
</span>

<span className="mclose,nulldelimiter">



</span>
</span>
</span>
</span>
</span>

。**在这种情况下，**<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

R

</mi>

<mrow>
<mi>

i

</mi>

<mi>

n

</mi>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

R_{in}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0077em;">

R

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3117em;">
<span style="top:-2.55em;margin-left:-0.0077em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

in

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

 **是一个低阻抗。**
3. 电流源做负载时源端电阻无穷大，电流为0，增益变为<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

A

</mi>

<mi>

v

</mi>
</msub>

<mo>

=

</mo>

<mo stretchy="false">

(

</mo>

<msub>
<mi>

g

</mi>

<mi>

m

</mi>
</msub>

<mo>

+

</mo>

<msub>
<mi>

g

</mi>

<mrow>
<mi>

m

</mi>

<mi>

b

</mi>
</mrow>
</msub>

<mo stretchy="false">

)

</mo>

<msub>
<mi>

r

</mi>

<mi>

o

</mi>
</msub>

<mo>

+

</mo>

<mn>

1

</mn>
</mrow>

<annotation encoding="application/x-tex">

A_v = (g_m + g_{mb})r_o + 1

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal">

A

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">

v

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mopen">

(

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

g

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

m

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0359em;">

g

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3361em;">
<span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight">

mb

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>

<span className="mclose">

)

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.1514em;">
<span style="top:-2.55em;margin-left:-0.0278em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight">

o

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

+

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.6444em;">



</span>

<span className="mord">

1

</span>
</span>
</span>
</span>
4. **现实中**的情况（特别是在短沟道工艺中， <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

r

</mi>

<mi>

O

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

r_O

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.5806em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.0278em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

O

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

 本身就很低）。负载 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

R

</mi>

<mi>

D

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

R_D

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0077em;">

R

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.0077em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

D

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

（比如另一个晶体管的 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

r

</mi>

<mi>

O

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

r_O

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.5806em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.0278em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

O

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

）和 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

M

</mi>

<mn>

1

</mn>
</msub>
</mrow>

<annotation encoding="application/x-tex">

M_1

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">

1

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

 的 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

r

</mi>

<mi>

O

</mi>
</msub>
</mrow>

<annotation encoding="application/x-tex">

r_O

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.5806em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.0278em;">

r

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.0278em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

O

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

 大小差不多

<mark>

只有在漏端电阻小的时候输入电阻才会变小

</mark>



![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/BeforeMidterm-47.webp)

##### 输出电阻分析

> 和CS放大器是一样的

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/BeforeMidterm-48.webp)

### 三者对比

<table>
<thead>
  <tr>
    <th>
      特性
    </th>
    
    <th>
      1. CS (Common-Source / 共源极)
    </th>
    
    <th>
      2. SF (Source-Follower / 源极跟随器)
    </th>
    
    <th>
      3. CG (Common-Gate / 共栅极)
    </th>
  </tr>
</thead>

<tbody>
  <tr>
    <td>
      基本结构
    </td>
    
    <td>
      输入: 栅极 (G) <br />
      
       输出: 漏极 (D)
    </td>
    
    <td>
      输入: 栅极 (G) <br />
      
       输出: 源极 (S)
    </td>
    
    <td>
      输入: 源极 (S) <br />
      
       输出: 漏极 (D)
    </td>
  </tr>
  
  <tr>
    <td>
      ⚡️ 电压增益 (<span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <msub>
                  <mi>
                    A
                  </mi>
                  
                  <mi>
                    v
                  </mi>
                </msub>
              </mrow>
              
              <annotation encoding="application/x-tex">
                A_v
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:0.8333em;vertical-align:-0.15em;">
              
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal">
                A
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.1514em;">
                      <span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
                        <span className="pstrut" style="height:2.7em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">
                            v
                          </span>
                        </span>
                      </span>
                    </span>
                    
                    <span className="vlist-s">
                      ​
                    </span>
                  </span>
                  
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.15em;">
                      <span>
                        
                      </span>
                    </span>
                  </span>
                </span>
              </span>
            </span>
          </span>
        </span>
      </span>
      
      )
    </td>
    
    <td>
      高，反相 <br />
      
       ( <span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <msub>
                  <mi>
                    A
                  </mi>
                  
                  <mi>
                    v
                  </mi>
                </msub>
                
                <mo>
                  =
                </mo>
                
                <mo>
                  −
                </mo>
                
                <msub>
                  <mi>
                    g
                  </mi>
                  
                  <mi>
                    m
                  </mi>
                </msub>
                
                <msub>
                  <mi>
                    R
                  </mi>
                  
                  <mrow>
                    <mi>
                      o
                    </mi>
                    
                    <mi>
                      u
                    </mi>
                    
                    <mi>
                      t
                    </mi>
                  </mrow>
                </msub>
              </mrow>
              
              <annotation encoding="application/x-tex">
                A_v = -g_m R_{out}
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:0.8333em;vertical-align:-0.15em;">
              
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal">
                A
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.1514em;">
                      <span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
                        <span className="pstrut" style="height:2.7em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">
                            v
                          </span>
                        </span>
                      </span>
                    </span>
                    
                    <span className="vlist-s">
                      ​
                    </span>
                  </span>
                  
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.15em;">
                      <span>
                        
                      </span>
                    </span>
                  </span>
                </span>
              </span>
            </span>
            
            <span className="mspace" style="margin-right:0.2778em;">
              
            </span>
            
            <span className="mrel">
              =
            </span>
            
            <span className="mspace" style="margin-right:0.2778em;">
              
            </span>
          </span>
          
          <span className="base">
            <span className="strut" style="height:0.8778em;vertical-align:-0.1944em;">
              
            </span>
            
            <span className="mord">
              −
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal" style="margin-right:0.0359em;">
                g
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.1514em;">
                      <span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
                        <span className="pstrut" style="height:2.7em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mathnormal,mtight">
                            m
                          </span>
                        </span>
                      </span>
                    </span>
                    
                    <span className="vlist-s">
                      ​
                    </span>
                  </span>
                  
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.15em;">
                      <span>
                        
                      </span>
                    </span>
                  </span>
                </span>
              </span>
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal" style="margin-right:0.0077em;">
                R
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.2806em;">
                      <span style="top:-2.55em;margin-left:-0.0077em;margin-right:0.05em;">
                        <span className="pstrut" style="height:2.7em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mtight">
                            <span className="mord,mathnormal,mtight">
                              o
                            </span>
                            
                            <span className="mord,mathnormal,mtight">
                              u
                            </span>
                            
                            <span className="mord,mathnormal,mtight">
                              t
                            </span>
                          </span>
                        </span>
                      </span>
                    </span>
                    
                    <span className="vlist-s">
                      ​
                    </span>
                  </span>
                  
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.15em;">
                      <span>
                        
                      </span>
                    </span>
                  </span>
                </span>
              </span>
            </span>
          </span>
        </span>
      </span>
      
       )
    </td>
    
    <td>
      <span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <mo>
                  ≤
                </mo>
                
                <mn>
                  1
                </mn>
              </mrow>
              
              <annotation encoding="application/x-tex">
                \le 1
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:0.7719em;vertical-align:-0.136em;">
              
            </span>
            
            <span className="mrel">
              ≤
            </span>
            
            <span className="mspace" style="margin-right:0.2778em;">
              
            </span>
          </span>
          
          <span className="base">
            <span className="strut" style="height:0.6444em;">
              
            </span>
            
            <span className="mord">
              1
            </span>
          </span>
        </span>
      </span>
      
      ，同相 <br />
      
       ( <span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <msub>
                  <mi>
                    A
                  </mi>
                  
                  <mi>
                    v
                  </mi>
                </msub>
                
                <mo>
                  ≈
                </mo>
                
                <mfrac>
                  <mrow>
                    <msub>
                      <mi>
                        g
                      </mi>
                      
                      <mi>
                        m
                      </mi>
                    </msub>
                    
                    <msub>
                      <mi>
                        R
                      </mi>
                      
                      <mi>
                        S
                      </mi>
                    </msub>
                  </mrow>
                  
                  <mrow>
                    <mn>
                      1
                    </mn>
                    
                    <mo>
                      +
                    </mo>
                    
                    <msub>
                      <mi>
                        g
                      </mi>
                      
                      <mi>
                        m
                      </mi>
                    </msub>
                    
                    <msub>
                      <mi>
                        R
                      </mi>
                      
                      <mi>
                        S
                      </mi>
                    </msub>
                  </mrow>
                </mfrac>
              </mrow>
              
              <annotation encoding="application/x-tex">
                A_v \approx \frac{g_m R_S}{1 + g_m R_S}
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:0.8333em;vertical-align:-0.15em;">
              
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal">
                A
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.1514em;">
                      <span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
                        <span className="pstrut" style="height:2.7em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">
                            v
                          </span>
                        </span>
                      </span>
                    </span>
                    
                    <span className="vlist-s">
                      ​
                    </span>
                  </span>
                  
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.15em;">
                      <span>
                        
                      </span>
                    </span>
                  </span>
                </span>
              </span>
            </span>
            
            <span className="mspace" style="margin-right:0.2778em;">
              
            </span>
            
            <span className="mrel">
              ≈
            </span>
            
            <span className="mspace" style="margin-right:0.2778em;">
              
            </span>
          </span>
          
          <span className="base">
            <span className="strut" style="height:1.4055em;vertical-align:-0.4811em;">
              
            </span>
            
            <span className="mord">
              <span className="mopen,nulldelimiter">
                
              </span>
              
              <span className="mfrac">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.9244em;">
                      <span style="top:-2.655em;">
                        <span className="pstrut" style="height:3em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mtight">
                            <span className="mord,mtight">
                              1
                            </span>
                            
                            <span className="mbin,mtight">
                              +
                            </span>
                            
                            <span className="mord,mtight">
                              <span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">
                                g
                              </span>
                              
                              <span className="msupsub">
                                <span className="vlist-t,vlist-t2">
                                  <span className="vlist-r">
                                    <span className="vlist" style="height:0.1645em;">
                                      <span style="top:-2.357em;margin-left:-0.0359em;margin-right:0.0714em;">
                                        <span className="pstrut" style="height:2.5em;">
                                          
                                        </span>
                                        
                                        <span className="sizing,reset-size3,size1,mtight">
                                          <span className="mord,mathnormal,mtight">
                                            m
                                          </span>
                                        </span>
                                      </span>
                                    </span>
                                    
                                    <span className="vlist-s">
                                      ​
                                    </span>
                                  </span>
                                  
                                  <span className="vlist-r">
                                    <span className="vlist" style="height:0.143em;">
                                      <span>
                                        
                                      </span>
                                    </span>
                                  </span>
                                </span>
                              </span>
                            </span>
                            
                            <span className="mord,mtight">
                              <span className="mord,mathnormal,mtight" style="margin-right:0.0077em;">
                                R
                              </span>
                              
                              <span className="msupsub">
                                <span className="vlist-t,vlist-t2">
                                  <span className="vlist-r">
                                    <span className="vlist" style="height:0.3448em;">
                                      <span style="top:-2.3567em;margin-left:-0.0077em;margin-right:0.0714em;">
                                        <span className="pstrut" style="height:2.5em;">
                                          
                                        </span>
                                        
                                        <span className="sizing,reset-size3,size1,mtight">
                                          <span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">
                                            S
                                          </span>
                                        </span>
                                      </span>
                                    </span>
                                    
                                    <span className="vlist-s">
                                      ​
                                    </span>
                                  </span>
                                  
                                  <span className="vlist-r">
                                    <span className="vlist" style="height:0.1433em;">
                                      <span>
                                        
                                      </span>
                                    </span>
                                  </span>
                                </span>
                              </span>
                            </span>
                          </span>
                        </span>
                      </span>
                      
                      <span style="top:-3.23em;">
                        <span className="pstrut" style="height:3em;">
                          
                        </span>
                        
                        <span className="frac-line" style="border-bottom-width:0.04em;">
                          
                        </span>
                      </span>
                      
                      <span style="top:-3.4461em;">
                        <span className="pstrut" style="height:3em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mtight">
                            <span className="mord,mtight">
                              <span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">
                                g
                              </span>
                              
                              <span className="msupsub">
                                <span className="vlist-t,vlist-t2">
                                  <span className="vlist-r">
                                    <span className="vlist" style="height:0.1645em;">
                                      <span style="top:-2.357em;margin-left:-0.0359em;margin-right:0.0714em;">
                                        <span className="pstrut" style="height:2.5em;">
                                          
                                        </span>
                                        
                                        <span className="sizing,reset-size3,size1,mtight">
                                          <span className="mord,mathnormal,mtight">
                                            m
                                          </span>
                                        </span>
                                      </span>
                                    </span>
                                    
                                    <span className="vlist-s">
                                      ​
                                    </span>
                                  </span>
                                  
                                  <span className="vlist-r">
                                    <span className="vlist" style="height:0.143em;">
                                      <span>
                                        
                                      </span>
                                    </span>
                                  </span>
                                </span>
                              </span>
                            </span>
                            
                            <span className="mord,mtight">
                              <span className="mord,mathnormal,mtight" style="margin-right:0.0077em;">
                                R
                              </span>
                              
                              <span className="msupsub">
                                <span className="vlist-t,vlist-t2">
                                  <span className="vlist-r">
                                    <span className="vlist" style="height:0.3448em;">
                                      <span style="top:-2.3567em;margin-left:-0.0077em;margin-right:0.0714em;">
                                        <span className="pstrut" style="height:2.5em;">
                                          
                                        </span>
                                        
                                        <span className="sizing,reset-size3,size1,mtight">
                                          <span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">
                                            S
                                          </span>
                                        </span>
                                      </span>
                                    </span>
                                    
                                    <span className="vlist-s">
                                      ​
                                    </span>
                                  </span>
                                  
                                  <span className="vlist-r">
                                    <span className="vlist" style="height:0.1433em;">
                                      <span>
                                        
                                      </span>
                                    </span>
                                  </span>
                                </span>
                              </span>
                            </span>
                          </span>
                        </span>
                      </span>
                    </span>
                    
                    <span className="vlist-s">
                      ​
                    </span>
                  </span>
                  
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.4811em;">
                      <span>
                        
                      </span>
                    </span>
                  </span>
                </span>
              </span>
              
              <span className="mclose,nulldelimiter">
                
              </span>
            </span>
          </span>
        </span>
      </span>
      
       )
    </td>
    
    <td>
      高，同相 <br />
      
       ( <span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <msub>
                  <mi>
                    A
                  </mi>
                  
                  <mi>
                    v
                  </mi>
                </msub>
                
                <mo>
                  ≈
                </mo>
                
                <msub>
                  <mi>
                    g
                  </mi>
                  
                  <mi>
                    m
                  </mi>
                </msub>
                
                <msub>
                  <mi>
                    R
                  </mi>
                  
                  <mi>
                    D
                  </mi>
                </msub>
              </mrow>
              
              <annotation encoding="application/x-tex">
                A_v \approx g_m R_{D}
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:0.8333em;vertical-align:-0.15em;">
              
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal">
                A
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.1514em;">
                      <span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
                        <span className="pstrut" style="height:2.7em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">
                            v
                          </span>
                        </span>
                      </span>
                    </span>
                    
                    <span className="vlist-s">
                      ​
                    </span>
                  </span>
                  
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.15em;">
                      <span>
                        
                      </span>
                    </span>
                  </span>
                </span>
              </span>
            </span>
            
            <span className="mspace" style="margin-right:0.2778em;">
              
            </span>
            
            <span className="mrel">
              ≈
            </span>
            
            <span className="mspace" style="margin-right:0.2778em;">
              
            </span>
          </span>
          
          <span className="base">
            <span className="strut" style="height:0.8778em;vertical-align:-0.1944em;">
              
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal" style="margin-right:0.0359em;">
                g
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.1514em;">
                      <span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
                        <span className="pstrut" style="height:2.7em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mathnormal,mtight">
                            m
                          </span>
                        </span>
                      </span>
                    </span>
                    
                    <span className="vlist-s">
                      ​
                    </span>
                  </span>
                  
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.15em;">
                      <span>
                        
                      </span>
                    </span>
                  </span>
                </span>
              </span>
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal" style="margin-right:0.0077em;">
                R
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.3283em;">
                      <span style="top:-2.55em;margin-left:-0.0077em;margin-right:0.05em;">
                        <span className="pstrut" style="height:2.7em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mtight">
                            <span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">
                              D
                            </span>
                          </span>
                        </span>
                      </span>
                    </span>
                    
                    <span className="vlist-s">
                      ​
                    </span>
                  </span>
                  
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.15em;">
                      <span>
                        
                      </span>
                    </span>
                  </span>
                </span>
              </span>
            </span>
          </span>
        </span>
      </span>
      
       )
    </td>
  </tr>
  
  <tr>
    <td>
      📥 输入阻抗 (<span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <msub>
                  <mi>
                    R
                  </mi>
                  
                  <mrow>
                    <mi>
                      i
                    </mi>
                    
                    <mi>
                      n
                    </mi>
                  </mrow>
                </msub>
              </mrow>
              
              <annotation encoding="application/x-tex">
                R_{in}
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:0.8333em;vertical-align:-0.15em;">
              
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal" style="margin-right:0.0077em;">
                R
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.3117em;">
                      <span style="top:-2.55em;margin-left:-0.0077em;margin-right:0.05em;">
                        <span className="pstrut" style="height:2.7em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mtight">
                            <span className="mord,mathnormal,mtight">
                              in
                            </span>
                          </span>
                        </span>
                      </span>
                    </span>
                    
                    <span className="vlist-s">
                      ​
                    </span>
                  </span>
                  
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.15em;">
                      <span>
                        
                      </span>
                    </span>
                  </span>
                </span>
              </span>
            </span>
          </span>
        </span>
      </span>
      
      )
    </td>
    
    <td>
      非常高 <br />
      
       (理想为 <span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <mi mathvariant="normal">
                  ∞
                </mi>
              </mrow>
              
              <annotation encoding="application/x-tex">
                \infty
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:0.4306em;">
              
            </span>
            
            <span className="mord">
              ∞
            </span>
          </span>
        </span>
      </span>
      
      )
    </td>
    
    <td>
      非常高 <br />
      
       (理想为 <span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <mi mathvariant="normal">
                  ∞
                </mi>
              </mrow>
              
              <annotation encoding="application/x-tex">
                \infty
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:0.4306em;">
              
            </span>
            
            <span className="mord">
              ∞
            </span>
          </span>
        </span>
      </span>
      
      )
    </td>
    
    <td>
      低 <br />
      
       ( <span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <mo>
                  ≈
                </mo>
                
                <mfrac>
                  <mn>
                    1
                  </mn>
                  
                  <msub>
                    <mi>
                      g
                    </mi>
                    
                    <mi>
                      m
                    </mi>
                  </msub>
                </mfrac>
              </mrow>
              
              <annotation encoding="application/x-tex">
                \approx \frac{1}{g_m}
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:0.4831em;">
              
            </span>
            
            <span className="mrel">
              ≈
            </span>
            
            <span className="mspace" style="margin-right:0.2778em;">
              
            </span>
          </span>
          
          <span className="base">
            <span className="strut" style="height:1.3262em;vertical-align:-0.4811em;">
              
            </span>
            
            <span className="mord">
              <span className="mopen,nulldelimiter">
                
              </span>
              
              <span className="mfrac">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.8451em;">
                      <span style="top:-2.655em;">
                        <span className="pstrut" style="height:3em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mtight">
                            <span className="mord,mtight">
                              <span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">
                                g
                              </span>
                              
                              <span className="msupsub">
                                <span className="vlist-t,vlist-t2">
                                  <span className="vlist-r">
                                    <span className="vlist" style="height:0.1645em;">
                                      <span style="top:-2.357em;margin-left:-0.0359em;margin-right:0.0714em;">
                                        <span className="pstrut" style="height:2.5em;">
                                          
                                        </span>
                                        
                                        <span className="sizing,reset-size3,size1,mtight">
                                          <span className="mord,mathnormal,mtight">
                                            m
                                          </span>
                                        </span>
                                      </span>
                                    </span>
                                    
                                    <span className="vlist-s">
                                      ​
                                    </span>
                                  </span>
                                  
                                  <span className="vlist-r">
                                    <span className="vlist" style="height:0.143em;">
                                      <span>
                                        
                                      </span>
                                    </span>
                                  </span>
                                </span>
                              </span>
                            </span>
                          </span>
                        </span>
                      </span>
                      
                      <span style="top:-3.23em;">
                        <span className="pstrut" style="height:3em;">
                          
                        </span>
                        
                        <span className="frac-line" style="border-bottom-width:0.04em;">
                          
                        </span>
                      </span>
                      
                      <span style="top:-3.394em;">
                        <span className="pstrut" style="height:3em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mtight">
                            <span className="mord,mtight">
                              1
                            </span>
                          </span>
                        </span>
                      </span>
                    </span>
                    
                    <span className="vlist-s">
                      ​
                    </span>
                  </span>
                  
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.4811em;">
                      <span>
                        
                      </span>
                    </span>
                  </span>
                </span>
              </span>
              
              <span className="mclose,nulldelimiter">
                
              </span>
            </span>
          </span>
        </span>
      </span>
      
       )<br />
      
       **(注意: <span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <msub>
                  <mi>
                    R
                  </mi>
                  
                  <mrow>
                    <mi>
                      i
                    </mi>
                    
                    <mi>
                      n
                    </mi>
                  </mrow>
                </msub>
              </mrow>
              
              <annotation encoding="application/x-tex">
                R_{in}
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:0.8333em;vertical-align:-0.15em;">
              
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal" style="margin-right:0.0077em;">
                R
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.3117em;">
                      <span style="top:-2.55em;margin-left:-0.0077em;margin-right:0.05em;">
                        <span className="pstrut" style="height:2.7em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mtight">
                            <span className="mord,mathnormal,mtight">
                              in
                            </span>
                          </span>
                        </span>
                      </span>
                    </span>
                    
                    <span className="vlist-s">
                      ​
                    </span>
                  </span>
                  
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.15em;">
                      <span>
                        
                      </span>
                    </span>
                  </span>
                </span>
              </span>
            </span>
          </span>
        </span>
      </span>
      
       依赖于 <span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <msub>
                  <mi>
                    R
                  </mi>
                  
                  <mi>
                    D
                  </mi>
                </msub>
              </mrow>
              
              <annotation encoding="application/x-tex">
                R_D
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:0.8333em;vertical-align:-0.15em;">
              
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal" style="margin-right:0.0077em;">
                R
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.3283em;">
                      <span style="top:-2.55em;margin-left:-0.0077em;margin-right:0.05em;">
                        <span className="pstrut" style="height:2.7em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">
                            D
                          </span>
                        </span>
                      </span>
                    </span>
                    
                    <span className="vlist-s">
                      ​
                    </span>
                  </span>
                  
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.15em;">
                      <span>
                        
                      </span>
                    </span>
                  </span>
                </span>
              </span>
            </span>
          </span>
        </span>
      </span>
      
      )¹
    </td>
  </tr>
  
  <tr>
    <td>
      📤 输出阻抗 (<span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <msub>
                  <mi>
                    R
                  </mi>
                  
                  <mrow>
                    <mi>
                      o
                    </mi>
                    
                    <mi>
                      u
                    </mi>
                    
                    <mi>
                      t
                    </mi>
                  </mrow>
                </msub>
              </mrow>
              
              <annotation encoding="application/x-tex">
                R_{out}
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:0.8333em;vertical-align:-0.15em;">
              
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal" style="margin-right:0.0077em;">
                R
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.2806em;">
                      <span style="top:-2.55em;margin-left:-0.0077em;margin-right:0.05em;">
                        <span className="pstrut" style="height:2.7em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mtight">
                            <span className="mord,mathnormal,mtight">
                              o
                            </span>
                            
                            <span className="mord,mathnormal,mtight">
                              u
                            </span>
                            
                            <span className="mord,mathnormal,mtight">
                              t
                            </span>
                          </span>
                        </span>
                      </span>
                    </span>
                    
                    <span className="vlist-s">
                      ​
                    </span>
                  </span>
                  
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.15em;">
                      <span>
                        
                      </span>
                    </span>
                  </span>
                </span>
              </span>
            </span>
          </span>
        </span>
      </span>
      
      )
    </td>
    
    <td>
      高 <br />
      
       ( <span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <mo>
                  ≈
                </mo>
                
                <msub>
                  <mi>
                    R
                  </mi>
                  
                  <mi>
                    D
                  </mi>
                </msub>
                
                <mo>
                  ∥
                </mo>
                
                <msub>
                  <mi>
                    r
                  </mi>
                  
                  <mi>
                    o
                  </mi>
                </msub>
              </mrow>
              
              <annotation encoding="application/x-tex">
                \approx R_D \parallel r_o
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:0.4831em;">
              
            </span>
            
            <span className="mrel">
              ≈
            </span>
            
            <span className="mspace" style="margin-right:0.2778em;">
              
            </span>
          </span>
          
          <span className="base">
            <span className="strut" style="height:1em;vertical-align:-0.25em;">
              
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal" style="margin-right:0.0077em;">
                R
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.3283em;">
                      <span style="top:-2.55em;margin-left:-0.0077em;margin-right:0.05em;">
                        <span className="pstrut" style="height:2.7em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">
                            D
                          </span>
                        </span>
                      </span>
                    </span>
                    
                    <span className="vlist-s">
                      ​
                    </span>
                  </span>
                  
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.15em;">
                      <span>
                        
                      </span>
                    </span>
                  </span>
                </span>
              </span>
            </span>
            
            <span className="mspace" style="margin-right:0.2778em;">
              
            </span>
            
            <span className="mrel">
              ∥
            </span>
            
            <span className="mspace" style="margin-right:0.2778em;">
              
            </span>
          </span>
          
          <span className="base">
            <span className="strut" style="height:0.5806em;vertical-align:-0.15em;">
              
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal" style="margin-right:0.0278em;">
                r
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.1514em;">
                      <span style="top:-2.55em;margin-left:-0.0278em;margin-right:0.05em;">
                        <span className="pstrut" style="height:2.7em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mathnormal,mtight">
                            o
                          </span>
                        </span>
                      </span>
                    </span>
                    
                    <span className="vlist-s">
                      ​
                    </span>
                  </span>
                  
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.15em;">
                      <span>
                        
                      </span>
                    </span>
                  </span>
                </span>
              </span>
            </span>
          </span>
        </span>
      </span>
      
       )
    </td>
    
    <td>
      低 <br />
      
       ( <span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <mo>
                  ≈
                </mo>
                
                <mfrac>
                  <mn>
                    1
                  </mn>
                  
                  <msub>
                    <mi>
                      g
                    </mi>
                    
                    <mi>
                      m
                    </mi>
                  </msub>
                </mfrac>
              </mrow>
              
              <annotation encoding="application/x-tex">
                \approx \frac{1}{g_m}
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:0.4831em;">
              
            </span>
            
            <span className="mrel">
              ≈
            </span>
            
            <span className="mspace" style="margin-right:0.2778em;">
              
            </span>
          </span>
          
          <span className="base">
            <span className="strut" style="height:1.3262em;vertical-align:-0.4811em;">
              
            </span>
            
            <span className="mord">
              <span className="mopen,nulldelimiter">
                
              </span>
              
              <span className="mfrac">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.8451em;">
                      <span style="top:-2.655em;">
                        <span className="pstrut" style="height:3em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mtight">
                            <span className="mord,mtight">
                              <span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">
                                g
                              </span>
                              
                              <span className="msupsub">
                                <span className="vlist-t,vlist-t2">
                                  <span className="vlist-r">
                                    <span className="vlist" style="height:0.1645em;">
                                      <span style="top:-2.357em;margin-left:-0.0359em;margin-right:0.0714em;">
                                        <span className="pstrut" style="height:2.5em;">
                                          
                                        </span>
                                        
                                        <span className="sizing,reset-size3,size1,mtight">
                                          <span className="mord,mathnormal,mtight">
                                            m
                                          </span>
                                        </span>
                                      </span>
                                    </span>
                                    
                                    <span className="vlist-s">
                                      ​
                                    </span>
                                  </span>
                                  
                                  <span className="vlist-r">
                                    <span className="vlist" style="height:0.143em;">
                                      <span>
                                        
                                      </span>
                                    </span>
                                  </span>
                                </span>
                              </span>
                            </span>
                          </span>
                        </span>
                      </span>
                      
                      <span style="top:-3.23em;">
                        <span className="pstrut" style="height:3em;">
                          
                        </span>
                        
                        <span className="frac-line" style="border-bottom-width:0.04em;">
                          
                        </span>
                      </span>
                      
                      <span style="top:-3.394em;">
                        <span className="pstrut" style="height:3em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mtight">
                            <span className="mord,mtight">
                              1
                            </span>
                          </span>
                        </span>
                      </span>
                    </span>
                    
                    <span className="vlist-s">
                      ​
                    </span>
                  </span>
                  
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.4811em;">
                      <span>
                        
                      </span>
                    </span>
                  </span>
                </span>
              </span>
              
              <span className="mclose,nulldelimiter">
                
              </span>
            </span>
          </span>
        </span>
      </span>
      
       )
    </td>
    
    <td>
      高 <br />
      
       ( <span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <mo>
                  ≈
                </mo>
                
                <msub>
                  <mi>
                    R
                  </mi>
                  
                  <mi>
                    D
                  </mi>
                </msub>
                
                <mo>
                  ∥
                </mo>
                
                <mi mathvariant="normal">
                  .
                </mi>
                
                <mi mathvariant="normal">
                  .
                </mi>
                
                <mi mathvariant="normal">
                  .
                </mi>
              </mrow>
              
              <annotation encoding="application/x-tex">
                \approx R_D \parallel ...
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:0.4831em;">
              
            </span>
            
            <span className="mrel">
              ≈
            </span>
            
            <span className="mspace" style="margin-right:0.2778em;">
              
            </span>
          </span>
          
          <span className="base">
            <span className="strut" style="height:1em;vertical-align:-0.25em;">
              
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal" style="margin-right:0.0077em;">
                R
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.3283em;">
                      <span style="top:-2.55em;margin-left:-0.0077em;margin-right:0.05em;">
                        <span className="pstrut" style="height:2.7em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">
                            D
                          </span>
                        </span>
                      </span>
                    </span>
                    
                    <span className="vlist-s">
                      ​
                    </span>
                  </span>
                  
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.15em;">
                      <span>
                        
                      </span>
                    </span>
                  </span>
                </span>
              </span>
            </span>
            
            <span className="mspace" style="margin-right:0.2778em;">
              
            </span>
            
            <span className="mrel">
              ∥
            </span>
            
            <span className="mspace" style="margin-right:0.2778em;">
              
            </span>
          </span>
          
          <span className="base">
            <span className="strut" style="height:0.1056em;">
              
            </span>
            
            <span className="mord">
              ...
            </span>
          </span>
        </span>
      </span>
      
       )
    </td>
  </tr>
  
  <tr>
    <td>
      🎯 主要应用
    </td>
    
    <td>
      电压放大
    </td>
    
    <td>
      电压缓冲 / 阻抗匹配
    </td>
    
    <td>
      电流缓冲 / 阻抗匹配
    </td>
  </tr>
  
  <tr>
    <td>
      - - - - - - - - - - - -
    </td>
    
    <td>
      - - - - - - - - - - - - - - - - - - - -
    </td>
    
    <td>
      - - - - - - - - - - - - - - - - - - - -
    </td>
    
    <td>
      - - - - - - - - - - - - - - - - - - - -
    </td>
  </tr>
  
  <tr>
    <td>
      🚀 驱动"容性负载" (<span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <msub>
                  <mi>
                    C
                  </mi>
                  
                  <mi>
                    L
                  </mi>
                </msub>
              </mrow>
              
              <annotation encoding="application/x-tex">
                C_L
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:0.8333em;vertical-align:-0.15em;">
              
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal" style="margin-right:0.0715em;">
                C
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.3283em;">
                      <span style="top:-2.55em;margin-left:-0.0715em;margin-right:0.05em;">
                        <span className="pstrut" style="height:2.7em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mathnormal,mtight">
                            L
                          </span>
                        </span>
                      </span>
                    </span>
                    
                    <span className="vlist-s">
                      ​
                    </span>
                  </span>
                  
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.15em;">
                      <span>
                        
                      </span>
                    </span>
                  </span>
                </span>
              </span>
            </span>
          </span>
        </span>
      </span>
      
      )<br />
      
       (考核速度/带宽**)
    </td>
    
    <td>
      差 (Poor) <br />
      
       高 <span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <msub>
                  <mi>
                    R
                  </mi>
                  
                  <mrow>
                    <mi>
                      o
                    </mi>
                    
                    <mi>
                      u
                    </mi>
                    
                    <mi>
                      t
                    </mi>
                  </mrow>
                </msub>
              </mrow>
              
              <annotation encoding="application/x-tex">
                R_{out}
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:0.8333em;vertical-align:-0.15em;">
              
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal" style="margin-right:0.0077em;">
                R
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.2806em;">
                      <span style="top:-2.55em;margin-left:-0.0077em;margin-right:0.05em;">
                        <span className="pstrut" style="height:2.7em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mtight">
                            <span className="mord,mathnormal,mtight">
                              o
                            </span>
                            
                            <span className="mord,mathnormal,mtight">
                              u
                            </span>
                            
                            <span className="mord,mathnormal,mtight">
                              t
                            </span>
                          </span>
                        </span>
                      </span>
                    </span>
                    
                    <span className="vlist-s">
                      ​
                    </span>
                  </span>
                  
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.15em;">
                      <span>
                        
                      </span>
                    </span>
                  </span>
                </span>
              </span>
            </span>
          </span>
        </span>
      </span>
      
       导致极点频率低，速度慢（且有密勒效应）。
    </td>
    
    <td>
      优秀 (Excellent) <br />
      
       低 <span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <msub>
                  <mi>
                    R
                  </mi>
                  
                  <mrow>
                    <mi>
                      o
                    </mi>
                    
                    <mi>
                      u
                    </mi>
                    
                    <mi>
                      t
                    </mi>
                  </mrow>
                </msub>
              </mrow>
              
              <annotation encoding="application/x-tex">
                R_{out}
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:0.8333em;vertical-align:-0.15em;">
              
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal" style="margin-right:0.0077em;">
                R
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.2806em;">
                      <span style="top:-2.55em;margin-left:-0.0077em;margin-right:0.05em;">
                        <span className="pstrut" style="height:2.7em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mtight">
                            <span className="mord,mathnormal,mtight">
                              o
                            </span>
                            
                            <span className="mord,mathnormal,mtight">
                              u
                            </span>
                            
                            <span className="mord,mathnormal,mtight">
                              t
                            </span>
                          </span>
                        </span>
                      </span>
                    </span>
                    
                    <span className="vlist-s">
                      ​
                    </span>
                  </span>
                  
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.15em;">
                      <span>
                        
                      </span>
                    </span>
                  </span>
                </span>
              </span>
            </span>
          </span>
        </span>
      </span>
      
       导致极点频率高，速度快。这是它作为“缓冲器”的核心价值。
    </td>
    
    <td>
      良好 (Good) <br />
      
       无密勒效应，高频特性好。常用于高速电路。
    </td>
  </tr>
  
  <tr>
    <td>
      📉 驱动"低阻性负载" (<span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <msub>
                  <mi>
                    R
                  </mi>
                  
                  <mi>
                    L
                  </mi>
                </msub>
              </mrow>
              
              <annotation encoding="application/x-tex">
                R_L
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:0.8333em;vertical-align:-0.15em;">
              
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal" style="margin-right:0.0077em;">
                R
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.3283em;">
                      <span style="top:-2.55em;margin-left:-0.0077em;margin-right:0.05em;">
                        <span className="pstrut" style="height:2.7em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mathnormal,mtight">
                            L
                          </span>
                        </span>
                      </span>
                    </span>
                    
                    <span className="vlist-s">
                      ​
                    </span>
                  </span>
                  
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.15em;">
                      <span>
                        
                      </span>
                    </span>
                  </span>
                </span>
              </span>
            </span>
          </span>
        </span>
      </span>
      
      )<br />
      
       (考核电压效率/增益)
    </td>
    
    <td>
      尚可 (Fair) <br />
      
       <span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <msub>
                  <mi>
                    A
                  </mi>
                  
                  <mi>
                    v
                  </mi>
                </msub>
                
                <mo>
                  =
                </mo>
                
                <mo>
                  −
                </mo>
                
                <msub>
                  <mi>
                    g
                  </mi>
                  
                  <mi>
                    m
                  </mi>
                </msub>
                
                <msub>
                  <mi>
                    R
                  </mi>
                  
                  <mi>
                    L
                  </mi>
                </msub>
              </mrow>
              
              <annotation encoding="application/x-tex">
                A_v = -g_m R_L
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:0.8333em;vertical-align:-0.15em;">
              
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal">
                A
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.1514em;">
                      <span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
                        <span className="pstrut" style="height:2.7em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">
                            v
                          </span>
                        </span>
                      </span>
                    </span>
                    
                    <span className="vlist-s">
                      ​
                    </span>
                  </span>
                  
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.15em;">
                      <span>
                        
                      </span>
                    </span>
                  </span>
                </span>
              </span>
            </span>
            
            <span className="mspace" style="margin-right:0.2778em;">
              
            </span>
            
            <span className="mrel">
              =
            </span>
            
            <span className="mspace" style="margin-right:0.2778em;">
              
            </span>
          </span>
          
          <span className="base">
            <span className="strut" style="height:0.8778em;vertical-align:-0.1944em;">
              
            </span>
            
            <span className="mord">
              −
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal" style="margin-right:0.0359em;">
                g
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.1514em;">
                      <span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
                        <span className="pstrut" style="height:2.7em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mathnormal,mtight">
                            m
                          </span>
                        </span>
                      </span>
                    </span>
                    
                    <span className="vlist-s">
                      ​
                    </span>
                  </span>
                  
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.15em;">
                      <span>
                        
                      </span>
                    </span>
                  </span>
                </span>
              </span>
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal" style="margin-right:0.0077em;">
                R
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.3283em;">
                      <span style="top:-2.55em;margin-left:-0.0077em;margin-right:0.05em;">
                        <span className="pstrut" style="height:2.7em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mathnormal,mtight">
                            L
                          </span>
                        </span>
                      </span>
                    </span>
                    
                    <span className="vlist-s">
                      ​
                    </span>
                  </span>
                  
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.15em;">
                      <span>
                        
                      </span>
                    </span>
                  </span>
                </span>
              </span>
            </span>
          </span>
        </span>
      </span>
      
      。在 <span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <msub>
                  <mi>
                    R
                  </mi>
                  
                  <mi>
                    L
                  </mi>
                </msub>
              </mrow>
              
              <annotation encoding="application/x-tex">
                R_L
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:0.8333em;vertical-align:-0.15em;">
              
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal" style="margin-right:0.0077em;">
                R
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.3283em;">
                      <span style="top:-2.55em;margin-left:-0.0077em;margin-right:0.05em;">
                        <span className="pstrut" style="height:2.7em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mathnormal,mtight">
                            L
                          </span>
                        </span>
                      </span>
                    </span>
                    
                    <span className="vlist-s">
                      ​
                    </span>
                  </span>
                  
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.15em;">
                      <span>
                        
                      </span>
                    </span>
                  </span>
                </span>
              </span>
            </span>
          </span>
        </span>
      </span>
      
       极低时，增益 <span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <mo stretchy="false">
                  ∣
                </mo>
                
                <msub>
                  <mi>
                    A
                  </mi>
                  
                  <mi>
                    v
                  </mi>
                </msub>
                
                <mo stretchy="false">
                  ∣
                </mo>
              </mrow>
              
              <annotation encoding="application/x-tex">
                \lvert A_v \rvert
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:1em;vertical-align:-0.25em;">
              
            </span>
            
            <span className="mopen">
              ∣
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal">
                A
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.1514em;">
                      <span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
                        <span className="pstrut" style="height:2.7em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">
                            v
                          </span>
                        </span>
                      </span>
                    </span>
                    
                    <span className="vlist-s">
                      ​
                    </span>
                  </span>
                  
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.15em;">
                      <span>
                        
                      </span>
                    </span>
                  </span>
                </span>
              </span>
            </span>
            
            <span className="mclose">
              ∣
            </span>
          </span>
        </span>
      </span>
      
       也会很低，但没有分压损失。
    </td>
    
    <td>
      差 (Poor) <br />
      
       <span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <msub>
                  <mi>
                    A
                  </mi>
                  
                  <mi>
                    v
                  </mi>
                </msub>
                
                <mo>
                  ≈
                </mo>
                
                <mfrac>
                  <msub>
                    <mi>
                      R
                    </mi>
                    
                    <mi>
                      L
                    </mi>
                  </msub>
                  
                  <mrow>
                    <msub>
                      <mi>
                        R
                      </mi>
                      
                      <mi>
                        L
                      </mi>
                    </msub>
                    
                    <mo>
                      +
                    </mo>
                    
                    <mn>
                      1
                    </mn>
                    
                    <mi mathvariant="normal">
                      /
                    </mi>
                    
                    <msub>
                      <mi>
                        g
                      </mi>
                      
                      <mi>
                        m
                      </mi>
                    </msub>
                  </mrow>
                </mfrac>
              </mrow>
              
              <annotation encoding="application/x-tex">
                A_v \approx \frac{R_L}{R_L + 1/g_m}
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:0.8333em;vertical-align:-0.15em;">
              
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal">
                A
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.1514em;">
                      <span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
                        <span className="pstrut" style="height:2.7em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">
                            v
                          </span>
                        </span>
                      </span>
                    </span>
                    
                    <span className="vlist-s">
                      ​
                    </span>
                  </span>
                  
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.15em;">
                      <span>
                        
                      </span>
                    </span>
                  </span>
                </span>
              </span>
            </span>
            
            <span className="mspace" style="margin-right:0.2778em;">
              
            </span>
            
            <span className="mrel">
              ≈
            </span>
            
            <span className="mspace" style="margin-right:0.2778em;">
              
            </span>
          </span>
          
          <span className="base">
            <span className="strut" style="height:1.4086em;vertical-align:-0.52em;">
              
            </span>
            
            <span className="mord">
              <span className="mopen,nulldelimiter">
                
              </span>
              
              <span className="mfrac">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.8886em;">
                      <span style="top:-2.655em;">
                        <span className="pstrut" style="height:3em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mtight">
                            <span className="mord,mtight">
                              <span className="mord,mathnormal,mtight" style="margin-right:0.0077em;">
                                R
                              </span>
                              
                              <span className="msupsub">
                                <span className="vlist-t,vlist-t2">
                                  <span className="vlist-r">
                                    <span className="vlist" style="height:0.3448em;">
                                      <span style="top:-2.3567em;margin-left:-0.0077em;margin-right:0.0714em;">
                                        <span className="pstrut" style="height:2.5em;">
                                          
                                        </span>
                                        
                                        <span className="sizing,reset-size3,size1,mtight">
                                          <span className="mord,mathnormal,mtight">
                                            L
                                          </span>
                                        </span>
                                      </span>
                                    </span>
                                    
                                    <span className="vlist-s">
                                      ​
                                    </span>
                                  </span>
                                  
                                  <span className="vlist-r">
                                    <span className="vlist" style="height:0.1433em;">
                                      <span>
                                        
                                      </span>
                                    </span>
                                  </span>
                                </span>
                              </span>
                            </span>
                            
                            <span className="mbin,mtight">
                              +
                            </span>
                            
                            <span className="mord,mtight">
                              1/
                            </span>
                            
                            <span className="mord,mtight">
                              <span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">
                                g
                              </span>
                              
                              <span className="msupsub">
                                <span className="vlist-t,vlist-t2">
                                  <span className="vlist-r">
                                    <span className="vlist" style="height:0.1645em;">
                                      <span style="top:-2.357em;margin-left:-0.0359em;margin-right:0.0714em;">
                                        <span className="pstrut" style="height:2.5em;">
                                          
                                        </span>
                                        
                                        <span className="sizing,reset-size3,size1,mtight">
                                          <span className="mord,mathnormal,mtight">
                                            m
                                          </span>
                                        </span>
                                      </span>
                                    </span>
                                    
                                    <span className="vlist-s">
                                      ​
                                    </span>
                                  </span>
                                  
                                  <span className="vlist-r">
                                    <span className="vlist" style="height:0.143em;">
                                      <span>
                                        
                                      </span>
                                    </span>
                                  </span>
                                </span>
                              </span>
                            </span>
                          </span>
                        </span>
                      </span>
                      
                      <span style="top:-3.23em;">
                        <span className="pstrut" style="height:3em;">
                          
                        </span>
                        
                        <span className="frac-line" style="border-bottom-width:0.04em;">
                          
                        </span>
                      </span>
                      
                      <span style="top:-3.4103em;">
                        <span className="pstrut" style="height:3em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mtight">
                            <span className="mord,mtight">
                              <span className="mord,mathnormal,mtight" style="margin-right:0.0077em;">
                                R
                              </span>
                              
                              <span className="msupsub">
                                <span className="vlist-t,vlist-t2">
                                  <span className="vlist-r">
                                    <span className="vlist" style="height:0.3448em;">
                                      <span style="top:-2.3567em;margin-left:-0.0077em;margin-right:0.0714em;">
                                        <span className="pstrut" style="height:2.5em;">
                                          
                                        </span>
                                        
                                        <span className="sizing,reset-size3,size1,mtight">
                                          <span className="mord,mathnormal,mtight">
                                            L
                                          </span>
                                        </span>
                                      </span>
                                    </span>
                                    
                                    <span className="vlist-s">
                                      ​
                                    </span>
                                  </span>
                                  
                                  <span className="vlist-r">
                                    <span className="vlist" style="height:0.1433em;">
                                      <span>
                                        
                                      </span>
                                    </span>
                                  </span>
                                </span>
                              </span>
                            </span>
                          </span>
                        </span>
                      </span>
                    </span>
                    
                    <span className="vlist-s">
                      ​
                    </span>
                  </span>
                  
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.52em;">
                      <span>
                        
                      </span>
                    </span>
                  </span>
                </span>
              </span>
              
              <span className="mclose,nulldelimiter">
                
              </span>
            </span>
          </span>
        </span>
      </span>
      
      。这是一个分压器！如果 <span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <msub>
                  <mi>
                    R
                  </mi>
                  
                  <mi>
                    L
                  </mi>
                </msub>
                
                <mo>
                  ≈
                </mo>
                
                <mn>
                  1
                </mn>
                
                <mi mathvariant="normal">
                  /
                </mi>
                
                <msub>
                  <mi>
                    g
                  </mi>
                  
                  <mi>
                    m
                  </mi>
                </msub>
              </mrow>
              
              <annotation encoding="application/x-tex">
                R_L \approx 1/g_m
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:0.8333em;vertical-align:-0.15em;">
              
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal" style="margin-right:0.0077em;">
                R
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.3283em;">
                      <span style="top:-2.55em;margin-left:-0.0077em;margin-right:0.05em;">
                        <span className="pstrut" style="height:2.7em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mathnormal,mtight">
                            L
                          </span>
                        </span>
                      </span>
                    </span>
                    
                    <span className="vlist-s">
                      ​
                    </span>
                  </span>
                  
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.15em;">
                      <span>
                        
                      </span>
                    </span>
                  </span>
                </span>
              </span>
            </span>
            
            <span className="mspace" style="margin-right:0.2778em;">
              
            </span>
            
            <span className="mrel">
              ≈
            </span>
            
            <span className="mspace" style="margin-right:0.2778em;">
              
            </span>
          </span>
          
          <span className="base">
            <span className="strut" style="height:1em;vertical-align:-0.25em;">
              
            </span>
            
            <span className="mord">
              1/
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal" style="margin-right:0.0359em;">
                g
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.1514em;">
                      <span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
                        <span className="pstrut" style="height:2.7em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mathnormal,mtight">
                            m
                          </span>
                        </span>
                      </span>
                    </span>
                    
                    <span className="vlist-s">
                      ​
                    </span>
                  </span>
                  
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.15em;">
                      <span>
                        
                      </span>
                    </span>
                  </span>
                </span>
              </span>
            </span>
          </span>
        </span>
      </span>
      
      ，电压信号损失50%。
    </td>
    
    <td>
      尚可 (Fair) <br />
      
       <span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <msub>
                  <mi>
                    A
                  </mi>
                  
                  <mi>
                    v
                  </mi>
                </msub>
                
                <mo>
                  ≈
                </mo>
                
                <msub>
                  <mi>
                    g
                  </mi>
                  
                  <mi>
                    m
                  </mi>
                </msub>
                
                <msub>
                  <mi>
                    R
                  </mi>
                  
                  <mi>
                    L
                  </mi>
                </msub>
              </mrow>
              
              <annotation encoding="application/x-tex">
                A_v \approx g_m R_L
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:0.8333em;vertical-align:-0.15em;">
              
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal">
                A
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.1514em;">
                      <span style="top:-2.55em;margin-left:0em;margin-right:0.05em;">
                        <span className="pstrut" style="height:2.7em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mathnormal,mtight" style="margin-right:0.0359em;">
                            v
                          </span>
                        </span>
                      </span>
                    </span>
                    
                    <span className="vlist-s">
                      ​
                    </span>
                  </span>
                  
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.15em;">
                      <span>
                        
                      </span>
                    </span>
                  </span>
                </span>
              </span>
            </span>
            
            <span className="mspace" style="margin-right:0.2778em;">
              
            </span>
            
            <span className="mrel">
              ≈
            </span>
            
            <span className="mspace" style="margin-right:0.2778em;">
              
            </span>
          </span>
          
          <span className="base">
            <span className="strut" style="height:0.8778em;vertical-align:-0.1944em;">
              
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal" style="margin-right:0.0359em;">
                g
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.1514em;">
                      <span style="top:-2.55em;margin-left:-0.0359em;margin-right:0.05em;">
                        <span className="pstrut" style="height:2.7em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mathnormal,mtight">
                            m
                          </span>
                        </span>
                      </span>
                    </span>
                    
                    <span className="vlist-s">
                      ​
                    </span>
                  </span>
                  
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.15em;">
                      <span>
                        
                      </span>
                    </span>
                  </span>
                </span>
              </span>
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal" style="margin-right:0.0077em;">
                R
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.3283em;">
                      <span style="top:-2.55em;margin-left:-0.0077em;margin-right:0.05em;">
                        <span className="pstrut" style="height:2.7em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mathnormal,mtight">
                            L
                          </span>
                        </span>
                      </span>
                    </span>
                    
                    <span className="vlist-s">
                      ​
                    </span>
                  </span>
                  
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.15em;">
                      <span>
                        
                      </span>
                    </span>
                  </span>
                </span>
              </span>
            </span>
          </span>
        </span>
      </span>
      
      。与CS情况相同。
    </td>
  </tr>
  
  <tr>
    <td>
      - - - - - - - - - - - -
    </td>
    
    <td>
      - - - - - - - - - - - - - - - - - - - -
    </td>
    
    <td>
      - - - - - - - - - - - - - - - - - - - -
    </td>
    
    <td>
      - - - - - - - - - - - - - - - - - - - -
    </td>
  </tr>
  
  <tr>
    <td>
      👎 主要缺点
    </td>
    
    <td>
      带宽窄 (密勒效应)；<br />
      
       带负载能力差 (高 <span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <msub>
                  <mi>
                    R
                  </mi>
                  
                  <mrow>
                    <mi>
                      o
                    </mi>
                    
                    <mi>
                      u
                    </mi>
                    
                    <mi>
                      t
                    </mi>
                  </mrow>
                </msub>
              </mrow>
              
              <annotation encoding="application/x-tex">
                R_{out}
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:0.8333em;vertical-align:-0.15em;">
              
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal" style="margin-right:0.0077em;">
                R
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.2806em;">
                      <span style="top:-2.55em;margin-left:-0.0077em;margin-right:0.05em;">
                        <span className="pstrut" style="height:2.7em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mtight">
                            <span className="mord,mathnormal,mtight">
                              o
                            </span>
                            
                            <span className="mord,mathnormal,mtight">
                              u
                            </span>
                            
                            <span className="mord,mathnormal,mtight">
                              t
                            </span>
                          </span>
                        </span>
                      </span>
                    </span>
                    
                    <span className="vlist-s">
                      ​
                    </span>
                  </span>
                  
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.15em;">
                      <span>
                        
                      </span>
                    </span>
                  </span>
                </span>
              </span>
            </span>
          </span>
        </span>
      </span>
      
      )。
    </td>
    
    <td>
      1. 消耗电压裕度；<br />
      
       2. 驱动低 <span className="katex">
        <span className="katex-mathml">
          <math xmlns="http://www.w3.org/1998/Math/MathML">
            <semantics>
              <mrow>
                <msub>
                  <mi>
                    R
                  </mi>
                  
                  <mi>
                    L
                  </mi>
                </msub>
              </mrow>
              
              <annotation encoding="application/x-tex">
                R_L
              </annotation>
            </semantics>
          </math>
        </span>
        
        <span className="katex-html" ariaHidden="true">
          <span className="base">
            <span className="strut" style="height:0.8333em;vertical-align:-0.15em;">
              
            </span>
            
            <span className="mord">
              <span className="mord,mathnormal" style="margin-right:0.0077em;">
                R
              </span>
              
              <span className="msupsub">
                <span className="vlist-t,vlist-t2">
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.3283em;">
                      <span style="top:-2.55em;margin-left:-0.0077em;margin-right:0.05em;">
                        <span className="pstrut" style="height:2.7em;">
                          
                        </span>
                        
                        <span className="sizing,reset-size6,size3,mtight">
                          <span className="mord,mathnormal,mtight">
                            L
                          </span>
                        </span>
                      </span>
                    </span>
                    
                    <span className="vlist-s">
                      ​
                    </span>
                  </span>
                  
                  <span className="vlist-r">
                    <span className="vlist" style="height:0.15em;">
                      <span>
                        
                      </span>
                    </span>
                  </span>
                </span>
              </span>
            </span>
          </span>
        </span>
      </span>
      
       时效率差。
    </td>
    
    <td>
      1. 输入阻抗低；<br />
      
       2. 偏置复杂。
    </td>
  </tr>
</tbody>
</table>

### Cascode Stage

#### Common Cascode stage

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/BeforeMidterm-49.webp)

结构的好处——抑制噪声

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/BeforeMidterm-50.webp)

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/BeforeMidterm-51.webp)

> 由于两个管子堆叠，导致吃掉了两倍的过驱动电压**导致输出摆幅**严重受限

##### 大信号分析

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/BeforeMidterm-52.webp)

##### 小信号电路与分析

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/BeforeMidterm-53.webp)

##### 输出电阻与增益

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/BeforeMidterm-54.webp)

##### 特殊结构——Triple Cascode

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/BeforeMidterm-55.webp)

##### gm与Av的trade off

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/BeforeMidterm-56.webp)

##### 电流负载

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/BeforeMidterm-57.webp)

##### Casecode 与 Casecade

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/BeforeMidterm-58.webp)

##### Poorman's Cascode

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/BeforeMidterm-59.webp)

<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

M

</mi>

<mn>

2

</mn>
</msub>
</mrow>

<annotation encoding="application/x-tex">

M_2

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">

2

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

（底部晶体管）工作在三极管区 (Triode Region)，而不是饱和区。

- <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

M

</mi>

<mn>

2

</mn>
</msub>
</mrow>

<annotation encoding="application/x-tex">

M_2

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">

2

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

 保持饱和的条件是 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

V

</mi>

<mrow>
<mi>

D

</mi>

<mi>

S

</mi>

<mn>

2

</mn>
</mrow>
</msub>

<mo>

>
</mo>

<msub>
<mi>

V

</mi>

<mrow>
<mi>

O

</mi>

<mi>

V

</mi>

<mn>

2

</mn>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

V_{DS2} > V_{OV2}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.2222em;">

V

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

D

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

S

</span>

<span className="mord,mtight">

2

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

>
</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.2222em;">

V

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

O

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.2222em;">

V

</span>

<span className="mord,mtight">

2

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

，即 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

V

</mi>

<mrow>
<mi>

D

</mi>

<mi>

S

</mi>

<mn>

2

</mn>
</mrow>
</msub>

<mo>

>
</mo>

<msub>
<mi>

V

</mi>

<mrow>
<mi>

G

</mi>

<mi>

S

</mi>

<mn>

2

</mn>
</mrow>
</msub>

<mo>

−

</mo>

<msub>
<mi>

V

</mi>

<mrow>
<mi>

T

</mi>

<mi>

H

</mi>

<mn>

2

</mn>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

V_{DS2} > V_{GS2} - V_{TH2}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.2222em;">

V

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

D

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

S

</span>

<span className="mord,mtight">

2

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

>
</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.2222em;">

V

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

GS

</span>

<span className="mord,mtight">

2

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

−

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.2222em;">

V

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.1389em;">

T

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0813em;">

H

</span>

<span className="mord,mtight">

2

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

。
- 但在电路中， <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

V

</mi>

<mrow>
<mi>

D

</mi>

<mi>

S

</mi>

<mn>

2

</mn>
</mrow>
</msub>

<mo>

=

</mo>

<msub>
<mi>

V

</mi>

<mrow>
<mi>

G

</mi>

<mi>

S

</mi>

<mn>

2

</mn>
</mrow>
</msub>

<mo>

−

</mo>

<msub>
<mi>

V

</mi>

<mrow>
<mi>

G

</mi>

<mi>

S

</mi>

<mn>

1

</mn>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

V_{DS2} = V_{GS2} - V_{GS1}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.2222em;">

V

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

D

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

S

</span>

<span className="mord,mtight">

2

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

=

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.2222em;">

V

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

GS

</span>

<span className="mord,mtight">

2

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

−

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.2222em;">

V

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

GS

</span>

<span className="mord,mtight">

1

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

。（<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

V

</mi>

<mrow>
<mi>

G

</mi>

<mi>

S

</mi>

<mn>

2

</mn>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

V_{GS2}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.2222em;">

V

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

GS

</span>

<span className="mord,mtight">

2

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

是总电压，<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

V

</mi>

<mrow>
<mi>

G

</mi>

<mi>

S

</mi>

<mn>

1

</mn>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

V_{GS1}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.2222em;">

V

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

GS

</span>

<span className="mord,mtight">

1

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

 是 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

M

</mi>

<mn>

1

</mn>
</msub>
</mrow>

<annotation encoding="application/x-tex">

M_1

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">

1

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

 的电压，<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

V

</mi>

<mrow>
<mi>

D

</mi>

<mi>

S

</mi>

<mn>

2

</mn>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

V_{DS2}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.2222em;">

V

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0278em;">

D

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

S

</span>

<span className="mord,mtight">

2

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

 是 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

M

</mi>

<mn>

2

</mn>
</msub>
</mrow>

<annotation encoding="application/x-tex">

M_2

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">

2

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

 的电压）。
- 所以， <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

M

</mi>

<mn>

2

</mn>
</msub>
</mrow>

<annotation encoding="application/x-tex">

M_2

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">

2

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

 饱和的条件变成了 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<mo stretchy="false">

(

</mo>

<msub>
<mi>

V

</mi>

<mrow>
<mi>

G

</mi>

<mi>

S

</mi>

<mn>

2

</mn>
</mrow>
</msub>

<mo>

−

</mo>

<msub>
<mi>

V

</mi>

<mrow>
<mi>

G

</mi>

<mi>

S

</mi>

<mn>

1

</mn>
</mrow>
</msub>

<mo stretchy="false">

)

</mo>

<mo>

>
</mo>

<mo stretchy="false">

(

</mo>

<msub>
<mi>

V

</mi>

<mrow>
<mi>

G

</mi>

<mi>

S

</mi>

<mn>

2

</mn>
</mrow>
</msub>

<mo>

−

</mo>

<msub>
<mi>

V

</mi>

<mrow>
<mi>

T

</mi>

<mi>

H

</mi>

<mn>

2

</mn>
</mrow>
</msub>

<mo stretchy="false">

)

</mo>
</mrow>

<annotation encoding="application/x-tex">

(V_{GS2} - V_{GS1}) > (V_{GS2} - V_{TH2})

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mopen">

(

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.2222em;">

V

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

GS

</span>

<span className="mord,mtight">

2

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

−

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.2222em;">

V

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

GS

</span>

<span className="mord,mtight">

1

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>

<span className="mclose">

)

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

>
</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mopen">

(

</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.2222em;">

V

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

GS

</span>

<span className="mord,mtight">

2

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>

<span className="mbin">

−

</span>

<span className="mspace" style="margin-right:0.2222em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:1em;vertical-align:-0.25em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.2222em;">

V

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.1389em;">

T

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0813em;">

H

</span>

<span className="mord,mtight">

2

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>

<span className="mclose">

)

</span>
</span>
</span>
</span>

。
- 简化后得到：<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

V

</mi>

<mrow>
<mi>

T

</mi>

<mi>

H

</mi>

<mn>

2

</mn>
</mrow>
</msub>

<mo>

>
</mo>

<msub>
<mi>

V

</mi>

<mrow>
<mi>

G

</mi>

<mi>

S

</mi>

<mn>

1

</mn>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

V_{TH2} > V_{GS1}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.2222em;">

V

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.1389em;">

T

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0813em;">

H

</span>

<span className="mord,mtight">

2

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

>
</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.2222em;">

V

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

GS

</span>

<span className="mord,mtight">

1

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

。
<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

M

</mi>

<mn>

1

</mn>
</msub>
</mrow>

<annotation encoding="application/x-tex">

M_1

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">

1

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

 是**导通**的，所以 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

V

</mi>

<mrow>
<mi>

G

</mi>

<mi>

S

</mi>

<mn>

1

</mn>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

V_{GS1}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.2222em;">

V

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

GS

</span>

<span className="mord,mtight">

1

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

 **必须大于** <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

V

</mi>

<mrow>
<mi>

T

</mi>

<mi>

H

</mi>

<mn>

1

</mn>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

V_{TH1}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.2222em;">

V

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.1389em;">

T

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0813em;">

H

</span>

<span className="mord,mtight">

1

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

。在标准工艺中 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

V

</mi>

<mrow>
<mi>

T

</mi>

<mi>

H

</mi>

<mn>

1

</mn>
</mrow>
</msub>

<mo>

≈

</mo>

<msub>
<mi>

V

</mi>

<mrow>
<mi>

T

</mi>

<mi>

H

</mi>

<mn>

2

</mn>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

V_{TH1} \approx V_{TH2}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.2222em;">

V

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.1389em;">

T

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0813em;">

H

</span>

<span className="mord,mtight">

1

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

≈

</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.2222em;">

V

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.1389em;">

T

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0813em;">

H

</span>

<span className="mord,mtight">

2

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

。这意味着 <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

V

</mi>

<mrow>
<mi>

G

</mi>

<mi>

S

</mi>

<mn>

1

</mn>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

V_{GS1}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.2222em;">

V

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

GS

</span>

<span className="mord,mtight">

1

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

 几乎**总是大于** <span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

V

</mi>

<mrow>
<mi>

T

</mi>

<mi>

H

</mi>

<mn>

2

</mn>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

V_{TH2}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.2222em;">

V

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.1389em;">

T

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0813em;">

H

</span>

<span className="mord,mtight">

2

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

。

<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

M

</mi>

<mn>

2

</mn>
</msub>
</mrow>

<annotation encoding="application/x-tex">

M_2

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">

2

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

 饱和的条件（<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

V

</mi>

<mrow>
<mi>

T

</mi>

<mi>

H

</mi>

<mn>

2

</mn>
</mrow>
</msub>

<mo>

>
</mo>

<msub>
<mi>

V

</mi>

<mrow>
<mi>

G

</mi>

<mi>

S

</mi>

<mn>

1

</mn>
</mrow>
</msub>
</mrow>

<annotation encoding="application/x-tex">

V_{TH2} > V_{GS1}

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.2222em;">

V

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.1389em;">

T

</span>

<span className="mord,mathnormal,mtight" style="margin-right:0.0813em;">

H

</span>

<span className="mord,mtight">

2

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>

<span className="mrel">

>
</span>

<span className="mspace" style="margin-right:0.2778em;">



</span>
</span>

<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.2222em;">

V

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3283em;">
<span style="top:-2.55em;margin-left:-0.2222em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">
<span className="mord,mathnormal,mtight" style="margin-right:0.0576em;">

GS

</span>

<span className="mord,mtight">

1

</span>
</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

）**永远无法满足**。因此，<span className="katex">
<span className="katex-mathml">
<math xmlns="http://www.w3.org/1998/Math/MathML">
<semantics>
<mrow>
<msub>
<mi>

M

</mi>

<mn>

2

</mn>
</msub>
</mrow>

<annotation encoding="application/x-tex">

M_2

</annotation>
</semantics>
</math>
</span>

<span className="katex-html" ariaHidden="true">
<span className="base">
<span className="strut" style="height:0.8333em;vertical-align:-0.15em;">



</span>

<span className="mord">
<span className="mord,mathnormal" style="margin-right:0.109em;">

M

</span>

<span className="msupsub">
<span className="vlist-t,vlist-t2">
<span className="vlist-r">
<span className="vlist" style="height:0.3011em;">
<span style="top:-2.55em;margin-left:-0.109em;margin-right:0.05em;">
<span className="pstrut" style="height:2.7em;">



</span>

<span className="sizing,reset-size6,size3,mtight">
<span className="mord,mtight">

2

</span>
</span>
</span>
</span>

<span className="vlist-s">

​

</span>
</span>

<span className="vlist-r">
<span className="vlist" style="height:0.15em;">
<span>



</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>
</span>

 **总是**被推入**三极管区**。

<mark>

“补救”方法——让Vth不一样

</mark>



##### Folded Cascode Stage

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/BeforeMidterm-60.webp)

解决电压域问题

###### 大信号分析

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/BeforeMidterm-61.webp)

###### 输出电阻分析

![img](https://phenthu-1321233386.cos.ap-nanjing.myqcloud.com/img/AnalogICDesign/BeforeMidterm-62.webp)
