# SQL-Secure

授权方必须拥有这个权力才能传承往下授权

grant  权限  on 表/视图 to user

![image-20240112212945410](C:\Users\papa\AppData\Roaming\Typora\typora-user-images\image-20240112212945410.png)

权限有select，insert，update，delete，references是可以声明外键

![image-20240112213122769](C:\Users\papa\AppData\Roaming\Typora\typora-user-images\image-20240112213122769.png)

## with grant option会允许被授权的用户可以传递pass这个权力给其他用户

![image-20240112213415960](C:\Users\papa\AppData\Roaming\Typora\typora-user-images\image-20240112213415960.png)

![image-20240112213443378](C:\Users\papa\AppData\Roaming\Typora\typora-user-images\image-20240112213443378.png)

## 例子

![image-20240112213617386](C:\Users\papa\AppData\Roaming\Typora\typora-user-images\image-20240112213617386.png)

# 授予给角色，再通过角色授予给用户

![image-20240112213803272](C:\Users\papa\AppData\Roaming\Typora\typora-user-images\image-20240112213803272.png)

## 撤销revoke



可选部分restrict表示严格，就是如果撤销时，存在某些比如这个用户的存储过程依赖于这个权限的话就会被禁止。还有就是如果with grant option之后这个用户传递了这个权限给其他人，那么就不能删除，除非从叶子开始先把最下面被传递的用户的权限删除依次上来

![image-20240112214523140](C:\Users\papa\AppData\Roaming\Typora\typora-user-images\image-20240112214523140.png)

![image-20240112214715533](C:\Users\papa\AppData\Roaming\Typora\typora-user-images\image-20240112214715533.png)