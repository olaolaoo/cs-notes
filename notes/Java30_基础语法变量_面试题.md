> 高效的方式计算2*8的值（文辉、轮**科技）

使用<<



> &和&&的区别？（恒*电子、*度）



> Java中的基本类型有哪些？String是最基本的数据类型吗？（恒*电子）

8种，不是，是引用类型

> Java中的基本数据类型包括哪些？（*米）

8：整型4，浮点2，字符1，boolean1

> Java开发中计算金额时使用什么数据类型？（5*到家）*
>

不能使用float，double，精度不高，要用BigDecimal

> char型变量中能不能存储一个中文汉字，为什么？（*通快递）

可以，虽然在ascii码中找不到中文，可以在unicode字符集中查到中文汉字，包含了世界范围内的所有字符

>
> 代码分析（君*科技、新*陆）

```
short s1=1:
s1=S1+1； //有什么错？因为右边是int类型，需要强转
short s1=1:
s1+=1；//有什么错？没错！
```



> int i=0; i=i++执行这两句化后变量i的值为（*软）
>

0

> 如何将两个变量的值互换（北京*彩、中外*译咨询）

![image-20240308134631320](/Users/ola/Library/Application Support/typora-user-images/image-20240308134631320.png)

> boolean 占几个字节（阿**巴）

編译时不谈占几个字节

但是JVM在运行时，给低于等于一个字节的都分配1个slot，因此给boolean类型分配内存空间时，boolean类型的变量占据一个槽位(slot，等于4个字节)。

拓展：在内存中，byte\short\char \boolean\int\float：占用1个slot
double\ long :占用2个slot





![image-20240308135301517](/Users/ola/Library/Application Support/typora-user-images/image-20240308135301517.png)

![image-20240308135321569](/Users/ola/Library/Application Support/typora-user-images/image-20240308135321569.png)