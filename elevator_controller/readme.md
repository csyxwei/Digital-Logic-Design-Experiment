### 电梯控制器设计

#### 实验环境： Windows10

#### 实验软件： Vivado 2017.1

#### 开发板： EGO1

##### 以下是实验的原要求

1. 电梯最少可以往返于0—9层楼。
2.  乘客要去的楼层数A可手动输入并显示，按取消键可清除本次输入。
3. 可自动显示电梯运行的楼层数B 
4. 
 - 当A>B时，电梯上升；
 - 当A<B时，电梯下降；
 - 当A=B时，电梯停止运行并开门；
5.  可以自动显示电梯每一次启停之间的运行时间
6. 任何时候按下复位键，电梯回到1层。

##### 以下是本实验的完成功能

1.  电梯往返于0-9层，其中要上楼时将up开关和当前楼层开关闭合，按下sure按键，待得电梯到达后再在up打开的情况下选取要去的楼层并按下sure按键，电梯即会到达指定楼层，下楼时累似。
2. 按取消（clear）键后电梯停留在当前楼层，等待下次输入后才会继续工作。
3. 电梯采用10个LED灯代表0-9层并用灯亮代表电梯位于该层，采用两个七段管分别显示目标楼层和两次启停间的时间。
4. 按下复位键（reset）键后电梯回到0层。
5. 若将超重开关闭合，则电梯停止工作，同时超重灯亮提示乘客电梯超重。
6. 另有3个LED灯分别代表电梯的上升、下降状态以及电梯门的开关。

##### 相应端口的功能及其管脚分布

| 端口 | 功能 | 管脚 |
|:--:|:--:|:--:|
|  | 输入模块 |  |
| floor[9:0] | 对应各个楼层 | P3\P2\R2\M4\N4\R1\U3\U2\V2\V5 |
| up | 要上楼的状态 | P5 |
| down | 要下楼的状态 | P4 |
| over_weight | 超重信号 | T5 |
| clk | 时钟信号 | P17 |
| reset | 复位键 | R11 |
| sure | 确定键 | R17 |
| clear | 清除本次输入的按键 | V1 |
|  | 显示模块 |  |
| up_or_down | 电梯状态，10为上升，01为下降 | F6\G4 |
| on_or_off | 电梯门的状态，1为开门，0为关门 | G3 |
| aim_floor | 显示目标楼层 | G2\B4\A4\A3\B1\A1\B3\B2 |
| require_time | 显示一次启停间的时间 | G1\D4\E3\D3\F4\F3\E2\D2 |
| over_weight_light | 超重提示灯 | J4 |
| now_floor | 每个灯亮对应电梯在该层 | J2\K2\K1\H6\H5\J5\K6\L1\M1\K3 |

#### 其他说明

<p> 上面的管脚对应的是EGO1的开发板，工程文件中已经写好相应的管脚约束，如果是EGO1开发板可以直接烧到板子上，否则的话需要自行更改相应管脚约束。

<p> 另因为能力有限，可能在一些逻辑处理上存在不足，欢迎提issue


