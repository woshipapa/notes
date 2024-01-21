# Cache

![image-20230506202111533](C:\Users\papa\AppData\Roaming\Typora\typora-user-images\image-20230506202111533.png)

将主存分块后，某个地址就可以看成先是块号，然后加上块内偏移

主存和Cache是按照**块为单位**进行传输的，并且块的大小保持一致。

CPU发出的是主存地址，这里需要将主存地址转化成Cache地址。

相联的映射关键在于不是放到了指定的位置，需要查表进行比对。

主存地址分成了几块，也就是块的数量决定了主存地址**前面的位**，这些位利用分成几组，分成几个区，来对2的几次幂进行除或者取模的运算，来得到组号，区号等。

主存地址明确了区号之后，就可以看成某个具体区内的几块，几组，然后再明确组号，最后确定组内块号。

Cache地址如果分组了的话，可以看成组号（与主存地址的组号相同）+组内块号（全相联的随机映射）+块内偏移。



## 直接映射

已经规定好了映射规则，所以不需要在表中额外加一列

组相联映射的组间直接，就说明主存地址中显示第几组的那几位只要给了就是Cache中第几组的那几位，不需要与表对应。

全相联映射由于是随机的映射，需要有主存地址的块号-------->Cache中的块号

全相联映射：Cache空间的利用率很高，可以自由放置块，但是在比较地址时比较内容过多，成本高

直接映射的块冲突率会很大，替换操作频繁

组相联：组间直接，组内全相联，利用率提高



平均读写时间=访问Cache的时间+（1-hit_rate）*访问主存的时间



## 替换策略

先入先出只考虑到了历史情况

LRU考虑到了最近的使用情况

LFU是在相邻的俩次替换间隔内，使用次数最少的，每命中一次次数+1，当需要替换时把当前计数最小的替换出去，**其他置零**。计数器位数多

LRU的计数，替换时是替换计数器最大的。

这个计数的含义是距离上次访问过了几回合了，除了比命中到的计数器大的那个不用+1

最佳替换算法用于评价其他算法，他是按照未来，将不再使用或者未来最久才访问的调出。

![image-20230531213620301](C:\Users\papa\AppData\Roaming\Typora\typora-user-images\image-20230531213620301.png)

## 读写一致性问题

写回法：

效率更高，但是存在有的时刻Cache和主存中内容不一致的情况

优先Cache，只有当Cache中的块被调出时，根据脏位是否为1再修改主存。

Cache命中时直接写Cache，Cache不命中时，先将主存中的块调入，再修改Cache。

全写法：

Cache命中，Cache和主存都修改

Cache不命中，改主存，然后有俩种方式，一种是改完之后接着调入Cache，一种是不调入

当采用写回法时，如果IO设备通过DMA的方式读写主存，Cache中的数据和主存中存在不一致的情况，一种解决办法是将外设缓冲区设置为不可缓冲，但是如果频繁访问的话开销会大，另一种就是通过操作系统内核干预，有一些Cache的指令，比如读的时候，会检查Cache中这一块是否更改过，如果更改过就写回主存再读取，如果向主存中写，**Cache这一块就作废，有效位为0**

![image-20230601124915497](C:\Users\papa\AppData\Roaming\Typora\typora-user-images\image-20230601124915497.png)

### 性能评估

第一种是CPU直接访问主存

第二种是CPU要通过Cache拿，Tb也可以认为是Tm

![image-20230601131351154](C:\Users\papa\AppData\Roaming\Typora\typora-user-images\image-20230601131351154.png)

### 影响性能的因素

#### 块大小

刚开始随着块的增大，时空局部性原理的效果很明显，相邻俩次访问的数据可能都在这个块里，但随着块越来越大，Cache中块的数目减少，替换频繁，俩种因素都在起作用，只是看谁起主导

![image-20230601131254744](C:\Users\papa\AppData\Roaming\Typora\typora-user-images\image-20230601131254744.png)

## 多级Cache：

![image-20240104110137496](C:\Users\papa\AppData\Roaming\Typora\typora-user-images\image-20240104110137496.png)

![image-20240104110847847](C:\Users\papa\AppData\Roaming\Typora\typora-user-images\image-20240104110847847.png)

当第一级Cache miss时，去第二级Cache访问，依次直到主存，或者在某级Cache访问到了就返回。

总失效率=各级Cache失效率的乘积

缺页处理时，要去外存中调入，相比Cache去访问主存，访问外存去IO更慢。

所以一般页表采用Write Back写回法，不适用全写法，否则还要来回去磁盘中读写速度太慢了

有效位表示Cache当前行的信息是否有效

成本高，容量小

Cache除了标志位，有效位，脏位，用于替换的位，还有本身存储的**主存的数据副本**

Cache每一行的数据容量就是主存中一块的大小

# 虚拟存储器

虚拟存储是利用进程的虚拟地址空间的概念，扩大了寻址范围，可以从外存中调入，最后翻译为物理地址，再去Cache和主存中找，此时主存或者Cache中一定存在，因为如果主存中没有前面再翻译成物理地址的时候会缺页中断从外存调入主存。

虚拟存储解决了主存储器容量与价格的矛盾，速度接近于主存但是容量和价格接近于外存

![image-20230603142643614](C:\Users\papa\AppData\Roaming\Typora\typora-user-images\image-20230603142643614.png)

![image-20230603142708450](C:\Users\papa\AppData\Roaming\Typora\typora-user-images\image-20230603142708450.png)

## 页式存储

![image-20230603142806686](C:\Users\papa\AppData\Roaming\Typora\typora-user-images\image-20230603142806686.png)

![image-20230603142948732](C:\Users\papa\AppData\Roaming\Typora\typora-user-images\image-20230603142948732.png)

## 段页式

段页式的段表中存放了这个段的页表地址和长度

![image-20230603143134237](C:\Users\papa\AppData\Roaming\Typora\typora-user-images\image-20230603143134237.png)

查页表/段表去进行地址翻译，**地址翻译**需要耗费时间，页表/段表占据空间，并且页表会占用Cache的小空间

压缩页表大小，采用**多级页表**。

采用页表Cache---TLB，跟Cache一样，不过他存放的是**页表项的副本**，一样存在满了需要替换策略（替换位），数据一致性（脏位，一般是写回法，外存IO太慢）

![image-20230603143944326](C:\Users\papa\AppData\Roaming\Typora\typora-user-images\image-20230603143944326.png)

如果访问某个虚拟地址，TLB中没有页表项，页表中也没有（装入位为0），就会启动操作系统的缺页中断处理程序，从外存中调入该页，然后切换回进程

![image-20230603144121690](C:\Users\papa\AppData\Roaming\Typora\typora-user-images\image-20230603144121690.png)

# 做题总结

全相联映射时，主存地址划分为块号+块内地址，Cache地址也是块号+块内地址，所以相联映射表中就是主存块号+Cache的块号+有效位等位

![image-20240106152816819](C:\Users\papa\AppData\Roaming\Typora\typora-user-images\image-20240106152816819.png)

**地址变换表**可能隐式的包含了Cache的块号，就是通过顺序存储的方式，类似于数组的索引，所以可以省去Cache块号这一列

相联存储器容量是Cache中的块数*一条记录也就是一行需要占用的bit

在组相联中，**参与进行比较的存储单元**的个数就是一个组内的块数