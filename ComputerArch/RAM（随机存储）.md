# RAM（随机存储）

**存储体**可以看成是存储单元构成的矩阵，每个**存储单元**中又是单独的**存储元**。

以下是DRAM

由一个电容和一个MOS管组成，电容充满电荷的状态为1，没有电荷为0。

当给MOS管一端加高电平时，就可以将电容的信息读出来，有电流就是1，无电流就是0，这里就是**读操作**。

这里在读时，与MOS管一端相连的是**字线**。负责选中某一行的存储单元。

写操作时，就是通过位线，在存储元右端加高电平为1，低电平为0，同时继续给字线加高电平导通，然后将数据写入电容中。

读/写操作的**基本单位都是按照存储字**来的，一个存储元为1bit，一个存储单元的大小为存储字长。

![image-20230428132028809](C:\Users\papa\AppData\Roaming\Typora\typora-user-images\image-20230428132028809.png)

MAR是预先将要从哪里读的地址和向哪里写的地址存起来。

MDR是保存从存储单元读取的数据或者要向某存储单元写的数据。

控制电路三个输出端，其中俩个是控制MAR和MDR保证稳定。

外部输入端口，**片选线**就是来选中该芯片的，**读/写控制线**可能俩根也可能一根。

译码器，地址总线n位地址，然后经过译码有2<sup>n</sup>个存储单元，选中某一个来进行读/写。



![image-20230428134008203](C:\Users\papa\AppData\Roaming\Typora\typora-user-images\image-20230428134008203.png)

![image-20230530161909944](C:\Users\papa\AppData\Roaming\Typora\typora-user-images\image-20230530161909944.png)

SRAM静态随机存储器：稳定，信息会一直保存，但是功耗大，集成度低

DRAM行列译码，刷新