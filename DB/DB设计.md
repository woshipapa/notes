# ER图

概念设计是ER图，逻辑设计是关系

![image-20240114135535335](C:\Users\papa\AppData\Roaming\Typora\typora-user-images\image-20240114135535335.png)



![image-20240114140135131](C:\Users\papa\AppData\Roaming\Typora\typora-user-images\image-20240114140135131.png)



![image-20240114140157937](C:\Users\papa\AppData\Roaming\Typora\typora-user-images\image-20240114140157937.png)

entity实体，relationship实体之间的联系

![image-20240114134450728](C:\Users\papa\AppData\Roaming\Typora\typora-user-images\image-20240114134450728.png)

派生属性是从其他属性计算得出的

![image-20240114134719792](C:\Users\papa\AppData\Roaming\Typora\typora-user-images\image-20240114134719792.png)

下划线在属性下面表示主键，矩形表示实体，椭圆表示属性

![image-20240114134758706](C:\Users\papa\AppData\Roaming\Typora\typora-user-images\image-20240114134758706.png)

![image-20240114134926450](C:\Users\papa\AppData\Roaming\Typora\typora-user-images\image-20240114134926450.png)

联系中也可以有属性

![image-20240114135009725](C:\Users\papa\AppData\Roaming\Typora\typora-user-images\image-20240114135009725.png)![image-20240114135020035](C:\Users\papa\AppData\Roaming\Typora\typora-user-images\image-20240114135020035.png)

### 角色

就是一个联系中联系的实体可以是同一个实体，但是要赋予不同的角色来区分

一个是课程，一个是前置课程



![image-20240114135304728](C:\Users\papa\AppData\Roaming\Typora\typora-user-images\image-20240114135304728.png)

## 联系的度（联系的实体个数）

![image-20240114140450358](C:\Users\papa\AppData\Roaming\Typora\typora-user-images\image-20240114140450358.png)



![image-20240114140740688](C:\Users\papa\AppData\Roaming\Typora\typora-user-images\image-20240114140740688.png)

![image-20240114140859434](C:\Users\papa\AppData\Roaming\Typora\typora-user-images\image-20240114140859434.png)

![image-20240114140906301](C:\Users\papa\AppData\Roaming\Typora\typora-user-images\image-20240114140906301.png)

![image-20240114141514510](C:\Users\papa\AppData\Roaming\Typora\typora-user-images\image-20240114141514510.png)

![image-20240114141543976](C:\Users\papa\AppData\Roaming\Typora\typora-user-images\image-20240114141543976.png)

## 实体参与度

![image-20240114141854473](C:\Users\papa\AppData\Roaming\Typora\typora-user-images\image-20240114141854473.png)

## 设计问题

### 属性与实体的冲突

当属性与其他实体有联系时，他就要作为一个实体

![image-20240114142104326](C:\Users\papa\AppData\Roaming\Typora\typora-user-images\image-20240114142104326.png)

![image-20240114142131315](C:\Users\papa\AppData\Roaming\Typora\typora-user-images\image-20240114142131315.png)

![image-20240114142350113](C:\Users\papa\AppData\Roaming\Typora\typora-user-images\image-20240114142350113.png)

![image-20240114142700776](C:\Users\papa\AppData\Roaming\Typora\typora-user-images\image-20240114142700776.png)

![image-20240114145228342](C:\Users\papa\AppData\Roaming\Typora\typora-user-images\image-20240114145228342.png)

## 根据ER图得到关系模式

多值属性单独拎出一个关系

![image-20240114150129056](C:\Users\papa\AppData\Roaming\Typora\typora-user-images\image-20240114150129056.png)

组合属性全部原子性的展开

![image-20240114150231170](C:\Users\papa\AppData\Roaming\Typora\typora-user-images\image-20240114150231170.png)

![image-20240114150244406](C:\Users\papa\AppData\Roaming\Typora\typora-user-images\image-20240114150244406.png)

多对多的关系要单独写一个新的关系，多对一的在多的那一张关系中，加入外键指向一的那张表

![image-20240114150724149](C:\Users\papa\AppData\Roaming\Typora\typora-user-images\image-20240114150724149.png)

![image-20240114150927963](C:\Users\papa\AppData\Roaming\Typora\typora-user-images\image-20240114150927963.png)

## 弱实体

要依赖于其他的实体才能存在，就是说明他其中的属性不能唯一确定一个元组，所以需要一个强实体的存在

![image-20240114152101874](C:\Users\papa\AppData\Roaming\Typora\typora-user-images\image-20240114152101874.png)

![image-20240114152259030](C:\Users\papa\AppData\Roaming\Typora\typora-user-images\image-20240114152259030.png)

![image-20240114152739260](C:\Users\papa\AppData\Roaming\Typora\typora-user-images\image-20240114152739260.png)

![image-20240114153020116](C:\Users\papa\AppData\Roaming\Typora\typora-user-images\image-20240114153020116.png)

## 聚合

关系可以作为一个实体参与另一个关系

![image-20240114153248559](C:\Users\papa\AppData\Roaming\Typora\typora-user-images\image-20240114153248559.png)

![image-20240114153255514](C:\Users\papa\AppData\Roaming\Typora\typora-user-images\image-20240114153255514.png)

![image-20240114153331140](C:\Users\papa\AppData\Roaming\Typora\typora-user-images\image-20240114153331140.png)

![image-20240114163005977](C:\Users\papa\AppData\Roaming\Typora\typora-user-images\image-20240114163005977.png)

![img](https://img-blog.csdnimg.cn/a7588f393403456f8b8f360c3079be83.png)