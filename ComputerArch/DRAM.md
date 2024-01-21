DRAM的地址分俩次送，可以减少地址线的数目，先送行地址锁存进去，再送列地址锁存进去。

DRAM要定时刷新，以行为单位刷新

刷新是将数据从DRAM中读出，再写入，因为有的存储单元长时间没有被读取，电容会漏电导致数据丢失。

刷新一行的时间==存取周期

![image-20230530183905464](C:\Users\papa\AppData\Roaming\Typora\typora-user-images\image-20230530183905464.png)

#### 集中式刷新

在刷新周期的间隔内，有一个集中的时间专门来进行刷新，此时就会形成一个~~==死区==~~，不能进行存取，在这个刷新的时间里会把存储体中所有的存储单元按照行的方式全部刷新。

![image-20230530195000169](C:\Users\papa\AppData\Roaming\Typora\typora-user-images\image-20230530195000169.png)

分散式的想法是把集中刷新的时间打散分成好几个部分，这样**不会让CPU等待太久**就可以进行下一次的存取操作。

分散式是一个存取周期前半部分来存取，后半部分来刷新。

完成一次存取，就刷新一行，这里需要256微秒

![image-20230530195158553](C:\Users\papa\AppData\Roaming\Typora\typora-user-images\image-20230530195158553.png)

但是分散的话，刷新的过于频繁了，刷新时间增多。而且增长了存储周期，降低系统速度。

异步式：

每隔15.625微秒刷新一行

![image-20230530195913295](C:\Users\papa\AppData\Roaming\Typora\typora-user-images\image-20230530195913295.png)

![image-20230530201332333](C:\Users\papa\AppData\Roaming\Typora\typora-user-images\image-20230530201332333.png)