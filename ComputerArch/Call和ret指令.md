# Call和ret指令

call指令调用另一个函数，此时会将IP也就是本应该执行的下一条指令的地址压入当前函数的栈顶中，然后IP跳转到调用的函数位置相当于jmp。

ret会将栈中的之前保存的IP旧值出栈，IP重新指向原位置。

用户栈的栈底在高地址，栈顶在低地址。

ebp指向栈帧的底部也就是高地址，esp指向栈帧的顶部是低地址。

#### 访问栈帧

push时esp会减4，然后将数据压入栈中。pop时esp+4，同时将数据pop到寄存器或者主存的某个位置上。

![image-20230518194056030](C:\Users\papa\AppData\Roaming\Typora\typora-user-images\image-20230518194056030.png)

可以通过add，sub来改变esp栈顶指针的值，也可以通过运算对ebp，esp进行。

每一个函数的栈底也就是高地址位都压入了调用它的原函数的栈底地址就是

都会先 **push ebp**,然后mov ebp，esp让ebp指向当前的函数栈中了。



函数ret之前leave会先把栈顶指针回到栈底，mov esp，ebp 然后出栈，pop ebp并将栈底的值赋给ebp





栈底附近一般是局部变量（ebp-4之类），**最先声明的在最下面，靠近栈顶方向**。

调用过其他函数的函数栈帧中，栈底是保存了上一个调用它的函数的栈帧栈底地址，栈顶是调用了其他函数的时候也就是call的时候存放了IP原来要执行的下一条指令的地址。

函数在返回时，会把返回值写到寄存器里。

![image-20230518234817278](C:\Users\papa\AppData\Roaming\Typora\typora-user-images\image-20230518234817278.png)

