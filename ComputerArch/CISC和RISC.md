复杂指令集系统

CISC的指令系统很复杂:寻址方式多，指令数目多，指令的格式也多，导致了硬件很复杂，很多指令执行可能会花费多个时钟周期，**访存指令**也多

![image-20230616085435901](C:\Users\papa\AppData\Roaming\Typora\typora-user-images\image-20230616085435901.png)

精简指令集系统

RISC利用局部性思想，一般很多指令是不使用的，我们是经常用少数的指令

![image-20230616085923470](C:\Users\papa\AppData\Roaming\Typora\typora-user-images\image-20230616085923470.png)

指令长度影响因素：

1.CPU数据总线宽度，指令字长必须是存储子长的整数倍

2.内存大小与组织

3.寄存器数量

4.指令数量，寻址方式



bit3为1表示双字指令，后面一个字可能是立即数，偏移地址disp等