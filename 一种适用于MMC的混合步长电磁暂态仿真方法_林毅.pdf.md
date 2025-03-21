## 一种适用于MMC的混合步长电磁 暂态仿真方法

林毅,林威,刘鑫²,刘崇茹2

（1.国网福建省电力有限公司经济技术研究院，福建福州350000；2.新能源电力系统国家重点实验室（华北电力大学），北京102206）

摘要：随着"双碳"目标的提出，大量新能源接人电网，以模块化多电平换流器（modularmultilevelconvertershigh voltagedc,MMC）为代表的柔性直流输电系统获得广泛的工程应用。而电磁暂态仿真在MMC系统规划与运行过 程中均发挥重要作用，但是大步长机电暂态仿真精度不足，小步长电磁暂态仿真耗时过长，无法适应MMC的发展 需求。因此基于混合仿真的基本思想，将MMC详细等效模型拆分为交流和直流两部分，建立了接口等值模型，提 出数据交互算法，从而实现交流系统使用大步长仿真、直流系统采用小步长仿真。基于PSCAD/EMTDC的MMC 系统仿真验证表明，混合仿真方法相较于大步长机电暂态仿真的仿真精度明显提高，相较于小步长电磁暂态仿真 的仿真时间大幅缩短。

关键词：模块化多电平换流器；混合步长仿真；接口模型；仿真精度 DOI:10.19781/j.issn.1673-9140.2023.02.007中图分类号：TM744文章编号：1673-9140(2023)02-0058-09

## A hybrid step-size electromagnetic transient simulation method suitable for MMC

LIN Yi', LIN Wei', LIU Xin², LIU Chongru²

(1.State Grid Fujian Economic Research Institute,Fuzhou 350000,China;2.State Key Laboratory of Alternate Electrical Power System with Renewable Energy Sources(North China ElectricPower University）,Beijing 102206,China)

Abstract: With the proposal of "double carbon" goal, many new energy sources are connected to the power grid,and the flexible DC transmission system represented by modular multilevel converters （MMC） has been widely used in engineering. Electromagnetic transient simulation plays an essential role in the planning and operation of the MMC system , but the accuracy of the large-step electromechanical transient simulation needs to be improved, and the small-step electromagnetic transient simulation takes too long to meet the development needs of MMC. Therefore,based on the basic idea of the hybrid simulation,the MMC detailed equivalent model is divided into AC and DC parts，the interface equivalent model is established, and the data interaction algorithm is proposed，so as to realize the long-step simulation of AC system and small-step simulation of DC system.The simulation verification of the MMC system based on PSCAD/ EMTDC shows that the simulation accuracy of the hybrid simulation method is obviously improved compared with the large-step electromechanical transient simulation， and the simulation time is greatly shortened compared with the small-step electromagnetic transient simulation.

Keywords:modularmultilevel converter;hybrid step simulation;interface model;simulationprecision

收稿日期：2022-03-14；修回日期：2022-08-29

基金项目：国网福建省电力有限公司科技项目（52130N20000C）

通信作者：刘崇茹（1977一）,女，博士，教授，主要从事交直流输电系统分析、稳定和控制研究；E-mail：chongru.liu@ncepu.edu.cn

分之一，它能准确地模拟系统的动态过程，对物理 现象刻画深刻，数值收敛性好，这种仿真可以应用 于电力系统的规划、设计、运行及科学研究等领域， 是学习和探究电力系统暂态复杂行为机理的必要 工具1]。

典型的对交直流混联大系统的仿真分析通常 采用机电暂态模型，积分步长一般为毫秒级，其仿 真过程忽略了复杂的电磁过程，结果更接近于稳 态"。电磁暂态仿真更关注系统的动态行为和暂态 过程，积分步长为微秒级²。

针对VSC-HVDC系统，需要根据仿真需求选 择机电暂态仿真、电磁暂态仿真或机电一电磁混合 仿真方法中的一种。文献[3]总结了VSC-HVDC 的机电暂态数学方程，并基于机电仿真程序PSS/E 的用户自定义模型实现了VSC-HVDC系统的机电 暂态仿真。文献[4]为了解决VSC-HVDC交流侧 数学模型不能精确解耦的问题，建立了基于αB静止 坐标系的VSC-HVDC机电暂态模型，并利用 PSASP\_UPI编写VSC-HVDC系统子程序实现机 电暂态仿真，为了更好地体现VSC控制器动态响 应，其机电仿真过程采用了双时步的仿真方法。文 献[5-6]分别提出了电磁暂态仿真程序（PSCAD/ 电磁暂态仿真模型，并作了仿真分析，后者还详细 介绍了MMC的子模块戴维南等效模型。文献 [7-8]介绍了VSC-HVDC系统的小时步仿真在实 时仿真器RTDS中的应用。文献[9」提出了一种混 合仿真方法，可用PSCAD程序调用嵌人的机电暂 态仿真程序（transient simulationprogram，TSP）对 外部系统进行功角仿真，而PSCAD自带的元件图 库方便地搭建柔性交流输电系统（FACTS)元件及 其控制器电路，对其进行精确的电磁暂态仿真，从 而实现全系统的混合仿真。文献[10]提出了一种 电力系统电磁一机电暂态联合模拟的通用接口，在 对暂态网络计算时，机电暂态网络进行戴维南等 值；在对机电暂态网络计算时，电磁暂态网络进行 诺顿等值。当柔性直流输电接人交流系统时，交流 系统的运行控制需要考虑更多的细节。当所连接 的直流线路增加与电压等级提升时，模拟数据的计

VSC-HVDC的混合仿真技术，在一定程度上提高 了VSC仿真模型的仿真速度并能很好地反映 VSC-HVDC的动态特性。

目前针对模块化多电平换流器开关器件的精 确仿真，一般都是在电磁暂态仿真程序下采用微秒 级的步长进行仿真计算。但是，当系统规模较大 时，仿真耗时过长，严重降低仿真效率。工程实际 中，MMC-HVDC的控制系统的控制周期是固定 的，一般为50μs或100μs。

为了兼顾仿真时长与仿真精度，本文针对 PSCAD/EMTDC本身不具备实现混合仿真的条 件，提出在PSCAD/EMTDC环境下实现MMC桥 臂器件在小步长下仿真、控制系统以及交流系统 在大步长下仿真的MMC-HVDC系统多种步长结 合的电磁暂态仿真算法。在PSCAD/EMTDC环 境下搭建单端MMC-HVDC系统，运用混合步长 电磁暂态仿真算法，通过比较MMC桥臂仿真小 步长下，控制系统以及交流系统在不同步长下的 仿真时间和MMC桥臂电压的仿真精度，证实在仿 真准确度和仿真花费时间方面，本文提出的多种步 长仿真算法具有更好的优越性。另外搭建双端 MMC-HVDC系统，将其中一端采用混合步长仿真 算法的换流站代替，从系统动态响应特性方面验证 该算法的可靠性和实用性。

## 1MMC桥臂详细模型等效方法

MMC桥臂详细等效模型基于Dommel等值 原理建立的戴维南等值模型，模块化多电平换流 器的六桥臂上级联的N个子模块等值为N个戴维 南等值电路串联的形式，每个戴维南等值电路中 包含一个戴维南电压源和串联的等效电阻[15-16], 等效后整个MMC换流器的结构如图1所示，Lo为 桥臂电感。

实际运行中，当MMC直流侧发生故障时，子模 块会闭锁隔离故障。闭锁状态的桥臂等值模型如 图2所示。其中，EN表示上IGBT触发信号，取值 0、1分别代表闭锁和正常状态；D、D2表示桥臂等值 后的二极管元件；Uarm表示桥臂电压；Iarm表示流过

桥臂的电流；≥Req≥Uceg分别表示单个桥臂上串联 的所有子模块电容的戴维南等值电阻之和以及戴 维南等效电压源之和。

图1MMC换流器等效结构

<!-- image -->

在关断状态下，子模块中只仅存二极管元件， 所有IGBT闭锁。在静态电磁转换模拟程序中，应 对二极管进行插值，以正确模拟二极管的单向导电 性[17]。由于PSCAD/EMTDC不提供插补算法的 外部接口，用户很难适应插补算法的应用。因此， 使用集成在PSCAD/EMTDC中的二极管元件来 模拟桥架的锁定距离。整体闭锁时,IGBT的触发 信号EN为O,桥臂各子模块的控制信号强制为1， 每个子模块投人电路部分相当于电容；正常状态 下，IGBT的触发信号EN为1,由于电容电压的恒 定正特性，所有子模块的控制信号由外部控制器决 定。具体电路通路如图2的加粗黑线所示，因为子 模块成串联结构，所有子模块流过的电流相等，从 而在整个桥臂等值模型中加人二极管能正确模拟 闭锁状态。

图2闭锁状态下桥臂等值模型

<!-- image -->

## 2PSCAD下的混合步长电磁暂态仿 真原理

## 2.1混合步长仿真的整体实现

多仿真接口实现方法逻辑如图3所示。

图3接口实现方法逻辑

<!-- image -->

图3的3个主框图依次是交流一次系统、MMC 电容电压计算、换流站系统，它们负责的逻辑计算 内容如下。

1）交流一次系统单元：负责交流一次系统的模 拟验证，它的功能是求解整体等值网络矩阵。

- 2）MMC桥臂计算单元：计算桥臂的戴维南等 值电路，包括所有桥臂中子电容的电压。
- 3）换流站的控制单元：担任电容电压均衡控 制、功率平衡和MMC桥臂中环流控制任务。

图3中关于数据交互模块的结构功能如下。

Ai:将大步长网络求解得到的桥臂电流Iar传输 给MMC桥臂模拟电容电压。

A2:将MMC桥臂计算单元得到的等效电路参 数传输给交流系统。

Bi:将MMC桥臂计算单元求解的电容电压传 输给换流站控制系统。

B2:分析前一步长的系统状态,把控制信号送给 MMC桥臂的分析模块。

C:把MMC桥臂计算单元得到的电气信号送 给换流站控制系统。

△T表示电磁暂态仿真大步长，△t表示电磁暂 态仿真小步长。

## 2.2接口位置的选取

混合步长电磁暂态混合仿真接口问题，其主要 思路是：将仿真的系统根据用户自身的需求拆分成 需要精确仿真的网络和不需要精确仿真的网络，并 选择合适的接口位置，建立起两部分的电气联系； 精确仿真的网络在用户定义的小步长下仿真，不需 要精确仿真的网络在电磁暂态仿真程序定义的大 步长下仿真。

上述混合步长仿真接口的模拟，应从以下4个 方面进行：①接口位置的选择；②大小步长网络接 口等值模型的建立；③接口模型的整体实现；④接 口仿真时序的给定。

对于MMC-HVDC系统，在系统换流器的出口 母线设置接口。大小步长电磁暂态网络对彼此的 等值比较简单，同时网络复杂程度不会限制这种 等值[18]。

## 2.3大小步长网络接口等值模型

如图4所示，点为大小步长网络分割点，分割 点左侧为交流系统大步长网络，分割点为需要更精 确仿真的小步长网络。大步长网络对小步长网络 的接口模型等效为注人网络分割点的受控电流源 I,它的大小是流经MMC桥臂电流Iarm；反之可等效 成和MMC桥臂并联的电压源V,电压源V的大小 等于桥臂电感的压降总和。

图4大小步长接口等值模型设计 Figure 4Interface model for different time step

<!-- image -->

## 2.4电磁暂态大步长网络和小步长网络时序接口 设计规则

基于MMC的电磁暂态混合步长仿真的基本原 理为：拆分的大小步长网络分别利用对侧网络上一 步长的计算结果，结合本侧网络参数进行计算，两 侧网络由于选择的计算步长不同，其数据交互在特 定的时间点进行，一般选择在大步长网络的各时间

点进行数据交互。大步长网络和小步长网络时序 接口流程如图5所示。

<!-- image -->

2)

具体交换过程如下。

- 1）仿真初始时刻，小步长网络的MMC桥臂接 收大步长网络传来的桥臂电流及控制信号。
- 2）小步长网络计算中，MMC桥臂计算单元依 据戴维南等值原理得到等值网络的Ueg、Req以及电 容电压Ue,并计算总的桥臂电压Uameq，这个时候大 步长交流系统的仿真处于暂停状态。

3）由于前一阶段的计算中每一个小步长都需 要重新得到一次总的桥臂电压Uameq,最后传递给大 步长交流系统的桥臂等效电压源Uameg（Tbig）如下：

<!-- formula-not-decoded -->

式中，Uarmi（tsmall)为交流网络小步长模拟时每次等效 计算的桥臂电压；ULo为桥臂电感上的电压；k为交 流网络小步长模拟时重复次数。

除此之外，柔性直流的触发信号需要步骤2)中 仿真得到的电容电压Uc经过控制回路，利用均压控 制策略产生。电容电压Uc如下：

<!-- formula-not-decoded -->

式中，t和t为2个相邻计算时间，且有t=t十△t；C 为电容值；Ic（t）、Ic（t)为不同时间流过MMC桥臂 子电容的电流；Uc(t)为t时刻的MMC桥臂的电容 电压。

由于小步长网络计算的电容电压要利用当前 时刻以及前一时刻的值，因此传回大步长网络控制 系统的电容电压应是在大步长△T时间内最后一个 小步长计算得到的Uc，因为在时序上二者最接近。

4）接收步骤3)得到的控制系统和交流一次系 统的网络参数，将控制系统再产生T时刻的触发脉 冲信号,交流系统再计算T时刻的Iarm,大步长网络 计算得到的桥臂电流和触发信号作为下次数据交 互小步长网络计算的初值。

## 2.5大小步长交互仿真流程图

由文2.4中提出的电磁暂态过程仿真混合仿真 步长接口设计规则，得出基于PSCAD/EMTDC的 混合仿真接口逻辑程序流程如图6所示。

图6接口逻辑程序实现流程

<!-- image -->

## 3仿真分析

## 3.1仿真耗时分析

本文选择表1所示的3种方案来验证所提出的 混合步长仿真算法的性能。

表13种方案的仿真步长分配 Table 1Simulation time stepfor different cases

| 方案   | 仿真步长/us   | 仿真步长/us   | 仿真步长/us   |
|------|-----------|-----------|-----------|
| 方案   | 交流系统      | MMC等效桥臂模型 | 控制系统      |
| 1    | 2.5       | 2.5       | 2.5       |
| 2    | 50        | 2.5       | 50        |
| 3    | 50        | 50        | 50        |

采用Intel（R）Core（TM）i5-3330CPU处理器， 8GB内存，主频为3.00GHz配置的电脑进行仿真， 测试系统为单端101电平MMC-HVDC系统，系统

参数如表2所示。

表2测试参数 Table 2Introduction of the test system

| 交流系统   | 交流系统    | 交流系统   | 交流系统   | 交流系统   |
|--------|---------|--------|--------|--------|
| Uac/kV | R/Q     | Ls/H   | P/MW   | Q/MVar |
| 110    | 0.314 2 | 0.001  | 100    | 50     |
| MMC    | MMC     | MMC    | MMC    | MMC    |
| Csm/F  | Lam/H   | Uac/kV | Rdc/Q  | Ldc/H  |
| 0.025  | 0.007 5 | 200    | 0.14   | 0.023  |

设置仿真时间为1s,换流器A相上桥臂的等效 建模、单端101电平模块化多电平换流器型高压直 流输电系统开始执行仿真程序以及仿真程序运行 完成的CPU工作时间如表3所示。

Table3 Statistics for the equivalent arm progress time-consuming of differentcases

|   方案 | 桥臂耗时tcpu/s   | 系统耗时TcPu/s   |
|------|--------------|--------------|
|    1 | 4.875 0      | 74.875 0     |
|    2 | 3.968 8      | 26.921 9     |
|    3 | 0.265 6      | 6.250 0      |

由表3可以看出，方案2无论桥臂仿真耗时还 是系统耗时都介于方案1和方案3之间，且在减少 系统仿真耗时上效果较为明显。

## 3.2 稳态仿真精度验证

对图7所示101电平单端MMC-HVDC系统进 行仿真，系统参数见表2，使用P-Q的控制方式，底 层阀控方法采取基于NLM调制的分层排序电压均 衡控制。桥臂的电压波形如图8所示，由图8分析 可得，3种方案下的桥臂电压仿真精度很高。考虑 到方案1的交流系统计算步长为2.5μs,方案2、3的 交流系统计算步长均为为50μs,为了进一步分析3 种方案对于桥臂电压仿真精度的误差，认为小步长 仿真的仿真精度最高,因此本文选取50μs计算步 长下方案1中20次桥臂电压计算均值分别与50μs 计算步长下方案2和方案3的桥臂电压计算值作 对比。

在Matlab中编制程序计算三者之间的绝对误 差，绝对误差的计算式如下：

<!-- formula-not-decoded -->

图7 101电平单端MMC-HVDC系统

<!-- image -->

Figure7S Structure ofthe101-levelMMC-HVDC system

<!-- image -->

(a）桥臂电压波形1

图8桥臂电压对比

<!-- image -->

<!-- formula-not-decoded -->

式中,Uermi为方案2相对方案1的绝对误差，Uem2为 方案3相对方案1的绝对误差；Uams为方案1的桥臂 电压；Uarmb为方案2的桥臂电压；Uamd为方案3的桥 臂电压。

为了进一步分析方案2、3相对方案1的误差， 计算esuml、esum2\serl、ser2,其具体计算式为

<!-- formula-not-decoded -->

<!-- formula-not-decoded -->

式（5）、（6)中,esuml、esum2分别为绝对误差Uerl、Uer2在 2.5～3s仿真时间时1×10次计算之和;Uer（i） Uer2（i)分别为Uer、Uer2在 2.5～3 s仿真时间时1× 104次计算的平均值；seml、sem2分别为Uerl、Uerr2在 2.5～3s仿真时间时1×10*次计算的方差。

具体计算结果如表4所示。

表4误差对比情况 Table 4Comparison of the absolute error

| 绝对误差   | esum/(103 kV)   | 方差ser   |
|--------|-----------------|---------|
| Uerrl  | 3.754 9         | 0.066 4 |
| Uer2   | 3.8089          | 0.068 6 |

经比较，方案2绝对误差的方差以及绝对误差之 和比方案3的更小，因此方案2比方案1的精度更高。

## 3.3暂态仿真精度分析及双端系统的应用

1）暂态仿真精度分析。

图7的单端柔直系统设置在t=1s时刻发生双 极短路故障，故障持续时间为5ms,t=1.005s时子 模块闭锁，图9对比了3种方案在发生直流侧双极 短路故障下的暂态特性。

以方案1(小步长)仿真图形为基准，由图9可得， 第2种方案的仿真精度介于第1种方案和第3种方案 之间。比较第2种方案和第3种方案，可以得到大步 长模型和混合步长交互模型对模块化多电平变流器 高压直流输电系统动态响应特性基本一致的结论。

## 2）双端系统的应用。

将本算法应用在双端系统中，系统参数见表5,并 对比混合步长模型（整流侧采用大小步长交互详细桥 臂模型，逆变侧采用大步长详细桥臂等效模型)和同为 大步长模型（整流、逆变侧均为大步长详细桥臂等效模 型)在功率阶跃时的系统稳定性特性如图10所示。

表5双端系统参数 Table 5Two terminal system parameters

| 参数          | 整流侧MMC               | 逆变侧MMC2              |
|-------------|----------------------|----------------------|
| 交流侧电阻       | Rs=0.01Ω             | Rs2=0.01Ω            |
| 交流侧电感       | Ls=0.001 H           | Ls2=0.001 H          |
| 换流变压器阀侧等值电阻 | R=0.01Ω              | R2=0.01Ω             |
| 换流变压器阀侧等值电感 | L=0.001 H            | L2=0.001 H           |
| 直流侧电阻       | Rac=0.15Ω            | Rac=0.15Ω            |
| 直流侧电感       | Ldc=0.125 H          | Ldc=0.125 H          |
| 桥臂电感        | Larm1=40 mH          | Larm2=7mH            |
| 传输功率        | Ps=300MW Qs1=-30Mvar | Ps2=-300MW Qs2=0Mvar |
| 直流电压        | Uac=200 kV           | Uac=200kV            |
| 子模块电容       | C=30mF               | C=30mF               |

图10中，Qaa代表混合步长模型中的无功功率， Padr、Uac\_ddt分别为其中的有功功率和直流电压;P、Q、Uac 代表大步长模型下的有功功率、无功功率和直流电压， 由图10可以看出，两种模型的控制响应并无明显区别， 它们的响应时间为10～20ms,并最后达到了参考指令。

3.50

<!-- image -->

(a)A相上桥臂电容电压

<!-- image -->

(c）A相上桥臂电流

<!-- image -->

(e）直流侧电压

<!-- image -->

（g）直流电流

<!-- image -->

由上述分析可得，当系统运行状况改变时，采 用混合仿真系统能够保证系统的稳定运行。混合 仿真系统与大步长仿真系统相比,在二者对模块化 多电平变流器高压直流输电系统的动态特性的反 应几乎相同，说明大小步长系统的稳定性较好。

0.475

<!-- image -->

(b）A相上桥臂电容电压放大对比

<!-- image -->

(d）A相上桥臂电流放大对比

<!-- image -->

(f)直流侧电压放大对比

<!-- image -->

(h）直流电流放大对比

<!-- image -->

(i)故障点交流侧电流波形

(j）故障点交流侧电流波形放大对比

图10功率阶跃时系统稳定性特性

<!-- image -->

## 3.4机电暂态仿真对比

前述方案3的仿真步长为50us,本质上仍属于 大步长的电磁暂态仿真。于是对比基于动态相量 模型的机电暂态仿真方法[19]，以研究混合步长仿真 方法同机电暂态仿真的差异。其中机电暂态仿真 步长设置为1ms。

图11为仿真结果对比，可以看出采用不同仿真 算法时，混合步长电磁暂态仿真算法与电磁暂态仿

桥臂电流/kA

图11 1仿真结果对比

<!-- image -->

真算法的曲线高度重合，说明混合步长仿真精度高 于机电暂态仿真。同时机电暂态仿真耗时1.364S， 混合步长电磁暂态仿真算法耗时9.647s，电磁暂态 仿真耗时18.515s。因此混合步长仿真算法相较于 电磁暂态仿真能显著减少系统仿真耗时，相较于机 电暂态仿真在用时稍多的前提下有效提高仿真 精度。

## 4  结语

本文在现有机电一电磁暂态混合仿真接口原 理的基础上，提出了一种基于电磁暂态仿真软件 PSCAD/EMTDC实现MMC型柔性直流输电系统 混合步长仿真的算法。在PSCAD下就系统稳态、 暂态以及动态响应进行了仿真验证，所提出的混合 步长仿真算法可以很好地适应系统稳定运行、故障 情况，还可扩展应用于多端MMC-HVDC系统的动 态响应研究。与小步长电磁暂态仿真相比，减少了 仿真算法耗时；与大步长电磁暂态仿真相比，有效 地提高了仿真的仿真精度。本文的分析还存在不 足，没有实现在PSCAD下交流系统、控制系统、桥 臂器件三部分均在不同步长下的仿真，以后的工作 将针对这方面展开。

## 参考文献：

- [1] 何海林，史华勃，王顺亮，等.用于大规模机电-电磁暂态 仿真模型自动转化的分层布局方法[J].中国电力，2022， 55(9): 111-120.

HE Hailin,SHI Huabo,WANG Shunliang, et al. Hierarchical layout method for automatic transformation oflarge-scaleelectromechanical-electromagnetictransient simulation model[J].Electric Power,2022,55(9):111-120.

- [2] 王路，李兴源，罗凯明，等.交直流混联系统的多速率混 合仿真技术研究[J].电网技术，2005,29(15)：23-27.
- WANG Lu,LI Xingyuan,LUO Kaiming,et al. Study on multirate hybrid simulation technology for AC/DC power system[J].Power System Technology,2005,29(15):23-27.

[3]

- 刘昇，徐政，唐庚，等.VSC-HVDC机电暂态仿真建模及仿 真[J].电网技术,2013,37(6):1672-1677.

LIU Sheng, XU Zheng, TANG Geng, et al. Electromechanicaltransientmodelingandsimulationfor voltage source converterbased HVDCpower transmission [J].Power System Technology,2013,37(6):1672-1677.

- [4]张芳，李静远，李传栋.含VSC-HVDC交直流混合系统机 电暂态仿真研究[J].电力自动化设备，2016,36(2)：17-24. ZHANG  Fang,  LI  Jingyuan， LI 　 Chuandong. Electromechanical transient simulation of AC/DC hybrid systems containing VSC-HVDC[J]. Electric Power AutomationEquipment,2016,36(2):17-24.
- [5] QAHRAMAN B，RAHIMI E,GOLE A M.An electromagnetic transient simulation model for voltage sourcedconverterbasedHVDCtransmission[C]// Electrical and Computer Engineering ,Niagara Falls,Ont, Canada,2004.
- [6] GNANARATHNA U N,GOLE A M,JAYASINGHE R P. EfficientmodelingofmodularmultilevelHVDC converters(MMC）on electromagnetic transient simulation programs[J]. IEEE Transactions on Power Delivery,2010, 26(1):316-324.
- [7] OU K,MAGUIRE T,WARKENTIN B,et al.Research and application of small time-step simulation for MMC VSC-HVDC in RTDS[C]// International Conference on Power System Technology.Chengdu,China,2014.
- [8] MAGUIRE T,GIESBRECHT J.Small time-step ($&lt;$2 us) VSCmodelfortherealtimedigitalsimulator[C]// International Conference on Power Systems Transients, 2005.
- 鄂志君，房大中，王立伟，等.基于EMTDC的混合仿真算
- E Zhijun,FANG Dazhong, WANG Liwei,et al.Research of hybrid simulation algorithm based on EMTDC[J]. Relay,
- [9] 法研究[J].继电器，2005,33(8):47-51. 2005,33(8):47-51.
- [10]和萍，李钊，李从善，等.基于虚拟同步机技术的储能机电暂 态特性建模[J].电力系统保护与控制，2022,50(7):11-22. HE Ping, LI Zhao,LI Congshan,et al. Electromechanical transient modeling of energy storage based on virtual synchronous machinetechnology[J]. Power System Protection and Control,2022,50(7):11-22.
- [11]李占凯，李炬，张福民，等.基于交流信号注人的混合微 电网功率均衡策略[J].电网与清洁能源，2022,38(2)： 18-26+34.
- LI Zhankai,LI Ju,ZHANG Fumin,et al.Power balance control strategy of hybridmicrogridbasedonAC signal injection[J].Power System and CleanEnergy,2022,38(2): 18-26+34.
- [12]刘栋，汤广福，贺之渊，等.模块化多电平柔性直流输电 数字一模拟混合实时仿真技术[J].电力自动化设备， 2013,33(2):68-73+80.
- LIU Dong, TANG Guangfu,HE Zhiyuan, et al. Hybrid real-time simulation technology for MMC-HVDC[J].Electric PowerAutomationEquipment,2013,33(2):68-73+80.
- [13]刘栋,汤广福,郑健超,等.模块化多电平换流器小信号 模型及开环响应时间常数分析[川].中国电机工程学报， 2012,32(24):1-7.
- LIU Dong,TANG Guangfu,ZHENG Jianchao,et al.Small signal modeling and analysis of open-loop response time constant of MMC[J].Proceedings of the CSEE,2012,32(24): 1-7.
- [14]杨景刚，赵科，高山，等.多端口混合直流断路器特性分 析及其仿真研究[J].高压电器，2021,57(12):50-56. YANGJinggang,ZHAOKe,GAOShan,et al.Characteristic analysis andsimulationstudy of multi-port hybridDC circuit breaker[J]. High Voltage Apparatus, 2021,57(12): 50-56+66.
- [15]许建中，赵成勇，刘文静.超大规模MMC电磁暂态仿真 提速模型[J].中国电机工程学报,2013,33(10):114-120. XU Jianzhong, ZHAO Chengyong, LIU Wenjing. Acceleratedmodelof ultra-largescale MMCin electromagnetictransient simulations[J].Proceedings of the CSEE,2013,33(10):114-120.
- [16]郭高朋,胡学浩，温家良，等.基于大规模子模块群的MMC 建模与快速仿真算法[J].电网技术,2015,39(5)：1226-1232. GUO Gaopeng, HU Xuehao, WEN Jialiang, et al. A large-scalesubmodule groupbased algorithm for modeling andhigh-speedsimulation[J].Power System Technology,2015,39(5):1226-1232.
- [17]唐庚，徐政，刘昇.改进式模块化多电平换流器快速仿真 方法[J].电力系统自动化，2014,38(24):56-61+85. TANG Geng,XU Zheng,LIU Sheng.Improved fast model of themodular multilevel converter[J].Automation of Electric Power Systems,2014,38(24):56-61+85.
- [18]何昊，崔成，贾希浩，等.基于暂态响应轨迹的光伏逆变 器参数辨识方法[J].智慧电力,2022,50(4):51-58. HE Hao,CUI Cheng,JIA Xihao,et al.Photovoltaic inverter parameter identification method based on transient response trajectory[J].Smart Power,2022,50(4):51-58.
- [19]马钰，韦钢，李扬，等.考虑孤岛源一荷不确定性的直流 配电网可靠性评估[J].电工技术学报，2021,36(22)：47264738. MA Yu, WEI Gang,LI Yang,et al.Reliability evaluation of DCdistributionnetwork consideringislanding sourceload uncertainty[J]. Transactions  of   China ElectrotechnicalSociety,2021,36(22):4726-4738.