

![image-20240308140153765](/Users/ola/Library/Application Support/typora-user-images/image-20240308140153765.png)



# 1.顺序结构flow

> 按照顺序从上往下执行
>

# 2.分支结构flow

> switch包含break的情况下和if都是多选1，区别:debug
>
> 1.switch:会直接跳到相匹配的case
>
> 2.if:从上到下挨个判断 -> 实际开发主要用if做判断,灵活  
>
> 3.if后跟boolean值，switch后跟的不是boolean

## 2.1.if-else条件判断

### 1.if的第一种格式

```java
1.格式:
  if(boolean表达式){
      执行语句;
  }

2.执行流程:
  先走if后面的boolean表达式,如果是true,就走if后面大括号中的执行语句,否则就不走
      
3.注意:
  if后面跟的是boolean表达式,只要是结果为boolean型的,都可以放在小括号中,哪怕直接写一个true或者false
```

```java
public class Demo01If {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int data1 = sc.nextInt();
        int data2 = sc.nextInt();
        if (data1==data2){
            System.out.println("两个整数相等");
        }
    }
}
```

### 2.if的第二种格式

```java
1.格式:
  if(boolean表达式){
      执行语句1;
  }else{
      执行语句2;
  }
2.执行流程:
  a.先走if后面的boolean表达式,如果是true,就走if后面的执行语句1
  b.否则就走else后面的执行语句2    
```

```java
public class Demo02IfElse {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int data1 = sc.nextInt();
        int data2 = sc.nextInt();
        if (data1==data2){
            System.out.println("两个整数相等");
        }else{
            System.out.println("两个整数不相等");
        }
    }
}
```

#### 2.1 练习

```java
任意给出一个整数，请用程序实现判断该整数是奇数还是偶数，并在控制台输出该整数是奇数还是偶数
```

```java
public class Demo03IfElse {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int data = sc.nextInt();
        if (data%2==0){
            System.out.println("偶数");
        }else{
            System.out.println("奇数");
        }
    }
}
```

#### 2.2练习

```java
需求.利用if  else 求出两个数的较大值
```

```java
public class Demo04IfElse {
    public static void main(String[] args) {
        int i = 10;
        int j = 20;
        if (i>j){
            System.out.println(i);
        }else{
            System.out.println(j);
        }
    }
}

```

```java
public class Demo05IfElse {
    public static void main(String[] args) {
        int i = 10;
        int j = 20;
        int k = 30;

        //定义临时变量,接收前两个数的较大值
        int temp = 0;

        if (i>j){
            temp = i;
        }else{
            temp = j;
        }

        if (temp>k){
            System.out.println(temp);
        }else{
            System.out.println(k);
        }
    }
}
```

#### 2.3练习

```java
案例：从键盘输入年份，请输出该年的2月份的总天数。闰年2月份29天，平年28天。
闰年:
 a.能被4整除,但是不能被100整除  year%4==0 && year%100!=0
 b.或者能直接被400整除  year%400==0

步骤:
  1.创建Scanner对象,调用nextInt键盘录入一个年份 year
  2.判断(year%4==0 && year%100!=0) || (year%400==0)
  3.如果条件成立,就输出闰年2月29天,否则输出平年2月28天    
```

```java
public class Demo06IfElse {
    public static void main(String[] args) {
        //1.创建Scanner对象,调用nextInt键盘录入一个年份 year
        Scanner scanner = new Scanner(System.in);
        int year = scanner.nextInt();
        //2.判断(year%4==0 && year%100!=0) || (year%400==0)
        if ((year%4==0 && year%100!=0) || (year%400==0)){
        //3.如果条件成立,就输出闰年2月29天,否则输出平年2月28天
            System.out.println("闰年2月29天");
        }else{
            System.out.println("平年2月28天");
        }
    }
}
```

#### 2.4练习

```java
public class Demo07IfElse {
    public static void main(String[] args) {
        boolean num1 = false;
        boolean num2 = true;

        int i = 1;

        /*
           num1 = false
           num2 = true
           num1 = num2 -> 相当于将num2的true赋值给了num1
         */
        if (num1=num2){
            i++;
            System.out.println(i);//2
        }

        if (false){
            --i;
            System.out.println(i);
        }
    }
}

```

### 3.if的第三种格式

```java
1.格式:
  if(boolean表达式){
      执行语句1
  }else if(boolean表达式){
      执行语句2
  }else if(boolean表达式){
      执行语句3
  }...else{
      执行语句n
  }

2.执行流程:
  从if开始往下挨个判断,哪个if判断结果为true,就走哪个if对应的执行语句,如果以上所有的判断都是false,就走else对应的执行语句n
      
3.使用场景:2种情况以上的判断      
```

```java
public class Demo08ElseIf {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int data1 = sc.nextInt();
        int data2 = sc.nextInt();
       /* if (data1>data2){
            System.out.println("data1大于data2");
        }else if(data1<data2){
            System.out.println("data1小于data2");
        }else{
            System.out.println("data1等于data2");
        }*/

        if (data1>data2){
            System.out.println("data1大于data2");
        }else if(data1<data2){
            System.out.println("data1小于data2");
        }else if (data1==data2){
            System.out.println("data1等于data2");
        }
    }
}

```

```java
注意:最后一种情况,不一定非得用else,但是必须要保证所有的情况都判断了
```

#### 3.1.练习

```java
需求:
 键盘录入一个星期数(1,2,...7)，输出对应的星期一，星期二，...星期日

输入  1      输出	星期一
输入  2      输出	星期二
输入  3      输出	星期三
输入  4      输出	星期四
输入  5      输出	星期五
输入  6      输出	星期六
输入  7      输出	星期日
输入  其它数字   输出      数字有误

```

```java
public class Demo09ElseIf {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int week = sc.nextInt();
        /*if (week==1){
            System.out.println("周一");
        }else if (week==2){
            System.out.println("周二");
        }else if (week==3){
            System.out.println("周三");
        }else if (week==4){
            System.out.println("周四");
        }else if (week==5){
            System.out.println("周五");
        }else if (week==6){
            System.out.println("周六");
        }else if (week==7){
            System.out.println("周日");
        }else{
            System.out.println("是不是有点大病,没有这个星期!");
        }*/

        if (week<1 || week>7){
            System.out.println("是不是有点大病,没有这个星期!");
        }else{
            if (week==1){
                System.out.println("周一");
            }else if (week==2){
                System.out.println("周二");
            }else if (week==3){
                System.out.println("周三");
            }else if (week==4){
                System.out.println("周四");
            }else if (week==5){
                System.out.println("周五");
            }else if (week==6){
                System.out.println("周六");
            }else if (week==7){
                System.out.println("周日");
            }
        }
    }
}
```

#### 3.2练习

```java
根据最新的年龄段划分标准:
  0-6岁为婴幼儿
  7-12岁为少儿
  13-17岁为青少年
  18-45岁为青年
  46-69岁为中年
  69岁以上为老年
请键盘录入一个年龄,判断属于什么年龄段  
```

```java
public class Demo10ElseIf {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int age = sc.nextInt();
       /* if (age>=0 && age<=6){
            System.out.println("婴幼儿");
        }else if (age>=7 && age<=12){
            System.out.println("少儿");
        }else if (age>=13 && age<=17){
            System.out.println("青少年");
        }else if(age>=18 && age<=45){
            System.out.println("青年");
        }else if(age>=46 && age<=69){
            System.out.println("中年");
        }else if (age>69 && age<=130){
            System.out.println("老年");
        }else {
            System.out.println("年龄不太符合实际");
        }*/

        if (age<0 || age>130){
            System.out.println("年龄不太符合实际");
        }else{
            if (age>=0 && age<=6){
                System.out.println("婴幼儿");
            }else if (age>=7 && age<=12){
                System.out.println("少儿");
            }else if (age>=13 && age<=17){
                System.out.println("青少年");
            }else if(age>=18 && age<=45){
                System.out.println("青年");
            }else if(age>=46 && age<=69){
                System.out.println("中年");
            }else if (age>69 && age<=130){
                System.out.println("老年");
            }
        }
    }
}

```

* 条件判断结构

  * If-else: 2选1
  * if--else if---else if---else：多选1

* 说明：
  * else 结构是可选的

  * 针对于条件表达式：
    * 如果多个条件表达式之间是“互斥”关系(或没有交集的关系),哪个判断和执行语句声明在上面还是下面，无所谓。
    * 如果多个条件表达式之间有交集的关系，需要根据实际情况，考虑清楚应该将哪个结构声明在上面。
    * 如果多个条件表达式之间有包含的关系，通常情况下，需要将范围小的声明在范围大的上面。否则，范围小的就没机会执行了

```java
/*
岳小鹏参加Java考试，他和父亲岳不群达成承诺：
如果：
成绩为100分时，奖励一辆BMW；
成绩为(80，99]时，奖励一台iphone xs max；
当成绩为[60,80]时，奖励一个 iPad；
其它时，什么奖励也没有。
请从键盘输入岳小鹏的期末成绩，并加以判断
*/
import java.util.Scanner;
class IfTest {
	public static void main(String[] args) {
		Scanner scan = new Scanner(System.in);
		
		System.out.println("请输入岳小鹏期末成绩：(0-100)");
		int score = scan.nextInt();

		if(score == 100){
			System.out.println("奖励一辆BMW");//be my wife!  BMW <---> MSN
		}else if(score > 80 &&  score <= 99){
			System.out.println("奖励一台iphone xs max");
		}else if(score >= 60 && score <= 80){
			System.out.println("奖励一个 iPad");
		}else{
			System.out.println("什么奖励也没有");
		}
	}
}
```

* If--else嵌套

  ```java
  /*
  编写程序：由键盘输入三个整数分别存入变量num1、num2、num3，
  对它们进行排序(使用 if-else if-else),并且从小到大输出。
  
  说明：
  1. if-else结构是可以相互嵌套的。
  2. 如果if-else结构中的执行语句只有一行时，对应的一对{}可以省略的。但是，不建议大家省略。
  */
  import java.util.Scanner;
  class IfTest2 {
  	public static void main(String[] args) {
  		
  		Scanner scanner = new Scanner(System.in);
  
  		System.out.println("请输入第一个整数：");
  		int num1 = scanner.nextInt();
  		System.out.println("请输入第二个整数：");
  		int num2 = scanner.nextInt();
  		System.out.println("请输入第三个整数：");
  		int num3 = scanner.nextInt();
  
  		if(num1 >= num2){
  			if(num3 >= num1)
  				System.out.println(num2 + "," + num1 + "," + num3);
  			else if(num3 <= num2)
  				System.out.println(num3 + "," + num2 + "," + num1);
  			else
  				System.out.println(num2 + "," + num3 + "," + num1);
  			
  		
  		}else{
  			if(num3 >= num2)
  				System.out.println(num1 + "," + num2 + "," + num3);
  			else if(num3 <= num1)
  				System.out.println(num3 + "," + num1 + "," + num2);
  			else
  				System.out.println(num1 + "," + num3 + "," + num2);
  			
  		}
  
  	}
  }
  
  ```

  ![image-20240308145108204](/Users/ola/Library/Application Support/typora-user-images/image-20240308145108204.png)

![image-20240308145126353](/Users/ola/Library/Application Support/typora-user-images/image-20240308145126353.png)

![image-20240308145145652](/Users/ola/Library/Application Support/typora-user-images/image-20240308145145652.png)

![image-20240308145204468](/Users/ola/Library/Application Support/typora-user-images/image-20240308145204468.png)

## 2.2.switch-case选择

```java
格式:
  switch(变量){
      case 常量值1:
          执行语句1;
          break;
          
      case 常量值2:
          执行语句2;
          break;
          
      case 常量值3:
          执行语句3;
          break;
          
      case 常量值4:
          执行语句4;
          break;
          ...
      default:
          执行语句n;
          break;
  }
```

* 执行流程:
    用变量接收的值和下面case后面的常量值匹配,匹配上哪个case就执行哪个case对应的执行语句
    如果以上所有case都没有匹配上,就走default对应的执行语句n
* break关键字:代表的是结束switch语句，如果没有break，会发生`穿透`，那么下面的语句会执行，直到遇到break或执行到最后
* 注意:switch能匹配什么类型的数据:
    byte、 short 、char、int、 枚举类型（JDK5.0新增）、 String类型（JDK7.0新增）

![image-20240308155834782](/Users/ola/Library/Application Support/typora-user-images/image-20240308155834782.png)

# 3.循环flow

![image-20240308194654970](/Users/ola/Library/Application Support/typora-user-images/image-20240308194654970.png)

for和while执行顺序一样

do-while和他俩不一样，先执行后判断

![image-20240308162428446](/Users/ola/Library/Application Support/typora-user-images/image-20240308162428446.png)

## for

可以在循环体中使用break，一旦触发，则跳出for

```java
1.格式:
  for(初始化变量;比较;步进表达式){
      循环语句 -> 哪段代码循环执行,就将哪段代码放到此处
  }

2.执行流程:
  a.先走初始化变量
  b.比较,如果是true,走循环语句,走步进表达式(初始化的变量的值进行变化) 
  c.再比较,如果还是true,继续走循环语句,走步进表达式
  d.再比较,直到比较为false,循环结束了
  
public class Demo01For {
    public static void main(String[] args) {
        for(int i = 0;i<3;i++){
            System.out.println("我爱java");
        }
    }
}
```

### 1.1练习

```java
for循环:求1-3之间的数据和,并把求和结果输出到控制台上
1+2+3
    
步骤:
  1.定义一个变量,用来接受两个数的和  sum
  2.利用for循环将1-3表示出来
  3.在循环的过程中,两两相加,将结果赋值给sum
  4.输出sum    
```

```java
public class Demo02For {
    public static void main(String[] args) {
        //1.定义一个变量,用来接受两个数的和  sum
        int sum = 0;
        //2.利用for循环将1-3表示出来
        for (int i = 1; i <= 3; i++) {
        //3.在循环的过程中,两两相加,将结果赋值给sum
            sum+=i;//sum = sum+i;
        }
        //4.输出sum
        System.out.println("sum = " + sum);
    }
}

```

<img src="/Users/ola/java30/课件/04_control_flow/img/1698925007924.png" alt="1698925007924" style="zoom:80%;" />

### 1.2练习

```java
需求:求出1-100的偶数和

步骤:
  1.定义一个变量sum,接受两个偶数的和
  2.利用for循环将1-100表示出来
  3.判断,如果是偶数,相加,将加的结果赋值给sum
  4.输出sum    
```

```java
public class Demo03For {
    public static void main(String[] args) {
        //1.定义一个变量sum,接受两个偶数的和
        int sum = 0;
        //2.利用for循环将1-100表示出来
        for (int i = 1; i <= 100; i++) {
            //3.判断,如果是偶数,相加,将加的结果赋值给sum
            if (i % 2 == 0) {
                sum += i;
            }
        }
        //4.输出sum
        System.out.println("sum = " + sum);
    }
}

```

### 1.3练习

```java
统计一下1-100之间的偶数个数

步骤:
  1.定义一个变量count,用来计数
  2.利用for循环将1-100表示出来
  3.判断,如果是偶数,count++
  4.输出count    
```

```java
public class Demo04For {
    public static void main(String[] args) {
        //1.定义一个变量count,用来计数
        int count = 0;
        //2.利用for循环将1-100表示出来
        for (int i = 1; i <= 100; i++) {
            //3.判断,如果是偶数,count++
            if (i % 2 == 0) {
                count++;
            }
        }
        //4.输出count
        System.out.println("count = " + count);
    }
}
```

![image-20240308170609078](/Users/ola/Library/Application Support/typora-user-images/image-20240308170609078.png)

  ![image-20240308171626172](/Users/ola/Library/Application Support/typora-user-images/image-20240308171626172.png)

![image-20240308171834805](/Users/ola/Library/Application Support/typora-user-images/image-20240308171834805.png)

![image-20240308172719136](/Users/ola/Library/Application Support/typora-user-images/image-20240308172719136.png)

12:1,24,36,48,60,72

20:1,20,60,80



## while

```java
1.格式:
  初始化变量;
  while(比较){
      循环语句;
      步进表达式
  }

2.执行流程:
  a.初始化变量
  b.比较,如果是true,就走循环语句,走步进表达式
  c.再比较,如果还是true,继续走循环语句,继续走步进表达式
  d.再比较,直到比较为false,循环结束
public class Demo01While {
    public static void main(String[] args) {
        int i = 0;
        while(i<5){
            System.out.println("我爱java,我更爱钱");
            i++;
        }
    }
}
```



![image-20240308191310951](/Users/ola/Library/Application Support/typora-user-images/image-20240308191310951.png)

生成一个100以内的数，输入一个数，和这个数判断大小

![image-20240308193014412](/Users/ola/Library/Application Support/typora-user-images/image-20240308193014412.png)

![image-20240308193045875](/Users/ola/Library/Application Support/typora-user-images/image-20240308193045875.png)

### 1.1while练习

```java
需求：世界最高山峰是珠穆朗玛峰(8844.43米=8844430毫米)，假如我有一张足够大的纸，它的厚度是0.1毫米。请问，我折叠多少次，可以折成珠穆朗玛峰的高度? 27

步骤:
  1.定义一个变量表示山峰的高度  mountain
  2.定义一个变量表示纸的厚度    paper
  3.定义一个变量表示折纸的次数  count
  4.利用while循环循环比较,如果paper<mountain 就循环对折
    paper = paper*2;
    count++;
  5.输出count
```

```java
public class Demo05While {
    public static void main(String[] args) {
        //1.定义一个变量表示山峰的高度  mountain
        int mountain = 8844430;
        //2.定义一个变量表示纸的厚度    paper
        double paper = 0.1;
        //3.定义一个变量表示折纸的次数  count
        int count = 0;
        /*4.利用while循环循环比较,如果paper<mountain 就循环对折
          paper = paper*2;
          count++;*/
        while(paper<mountain){
            paper*=2;
            count++;
        }
        //5.输出count
        System.out.println("count = " + count);
    }
}
```



## do-while



![image-20240308193746180](/Users/ola/Library/Application Support/typora-user-images/image-20240308193746180.png)



## 死循环

_[课程视频](https://www.bilibili.com/video/BV1PY411e7J6?p=51&vd_source=6f12b8c78467086fc666a02ab409ef20)_

```java
1.概述:
  一直循环
2.什么条件下一直循环:
  比较条件一直是true
  while(true);for(;;)
  
```

```java
public class Demo01Endless {
    public static void main(String[] args) {
        int count = 0;
        for (int i = 0; i < 10;) {
            count++;
            System.out.println("我爱java"+count);
        }


       /* while(true){
            count++;
            System.out.println("我爱java"+count);
        }*/


    }
}
```

## 嵌套循环

```java
1.概述:循环中还有循环
2.执行流程:
  先执行外层循环,再进入内层循环,内层循环就一直循环,直到内层循环结束,外层循环进入下一次循环,直到外层循环都结束了,整体结束
```

```java
public class Demo02Nest {
    public static void main(String[] args) {
        for (int fen = 0; fen < 60; fen++) {
            for (int miao = 0; miao < 60; miao++) {
                System.out.println(fen+"分"+miao+"秒");
            }
        }
    }
}
```

```java
练习:打印矩形
```

```java
public class Demo03Nest {
    public static void main(String[] args) {
        //外层循环控制行
        for (int i = 0; i < 5; i++) {
            //内层循环控制列
            for (int j = 0; j < 5; j++) {
                System.out.print("* ");
            }
            System.out.println();
        }
    }
}
```

```java
练习:打印直角三角形
```

```java
* 
* * 
* * * 
* * * *   
```

```java
public class Demo04Nest {
    public static void main(String[] args) {
        for (int i = 1; i < 5; i++) {
            for (int j = 0;j<i;j++){
                System.out.print("* ");
            }
            System.out.println();
        }
    }
}

```

## 练习.猜数字小游戏

```java
1.创建Scanner和Random对象
2.调用Random中的nextInt(100)+1在1-100之间随机一个数  rdNumber
3.调用Scanner中的nextInt()方法 键盘录入一个要猜的数   scNumber
4.如果scNumber大于rdNumber,证明猜大了
5.如果scNumber小于rdNumber,证明猜小了
6.如果scNumber等于rdNumber,证明猜中了
```

```java
public class Demo01Exam {
    public static void main(String[] args) {
        //1.创建Scanner和Random对象
        Scanner sc = new Scanner(System.in);
        Random rd = new Random();
        //2.调用Random中的nextInt(100)+1在1-100之间随机一个数  rdNumber
        int rdNumber = rd.nextInt(100) + 1;
        while(true){
            //3.调用Scanner中的nextInt()方法 键盘录入一个要猜的数   scNumber
            System.out.println("请您猜一个数:");
            int scNumber = sc.nextInt();
            //4.如果scNumber大于rdNumber,证明猜大了
            if (scNumber>rdNumber){
                System.out.println("对不起,您猜大了!");
            }else if (scNumber<rdNumber){
                //5.如果scNumber小于rdNumber,证明猜小了
                System.out.println("对不起,您猜小了!");
            }else{
                //6.如果scNumber等于rdNumber,证明猜中了
                System.out.println("恭喜您,猜中了!");
                break;
            }
        }

    }
}
```

# 4.循环控制关键字

```java
1.break:
  a.在switch中代表结束switch语句
  b.在循环中代表结束循环 
      
2.continue:
  结束当前本次循环,直接进入下一次循环,直到条件为false为止
```

```java
public class Demo01BreakAndContinue {
    public static void main(String[] args) {
        for (int i = 1; i <= 5; i++) {
            if (i==3){
                //结束循环
                //break;
                //结束本次循环,进入下一次循环
                continue;
            }
            System.out.println("我爱java"+i);
        }
    }
}
```

# 5.Scanner 类

键盘录入

```
1.概述:是java定义好的一个类
2.作用:将数据通过键盘录入的形式放到代码中参与运行 
3.位置:java.util
4.使用:
  a.导包:通过导包找到要使用的类 -> 导包位置:类上
    import java.util.Scanner -> 导入的是哪个包下的哪个类
      
  b.创建Scanner的类实例，对象，固定格式
    Scanner 变量名 = new Scanner(System.in);

  c.调用方法,实现键盘录入
    变量名.nextInt() 输入整数int型的
    变量名.next() 输入字符串  String型的  
```

```java
/*
如何从键盘获取不同类型的变量：需要使用Scanner类

具体实现步骤：
1.导包：import java.util.Scanner;
2.Scanner的实例化:Scanner scan = new Scanner(System.in);
3.调用Scanner类的相关方法（next() / nextXxx()），来获取指定类型的变量

注意：
需要根据相应的方法，来输入指定类型的值。如果输入的数据类型与要求的类型不匹配时，会报异常：InputMisMatchException
导致程序终止。
*/
//1.导包：import java.util.Scanner;
import java.util.Scanner;

class ScannerTest{
	
	public static void main(String[] args){
		//2.Scanner的实例化
		Scanner scan = new Scanner(System.in);
		
		//3.调用Scanner类的相关方法
		System.out.println("请输入你的姓名：");
		String name = scan.next();
		System.out.pr intln(name);

		System.out.println("请输入你的芳龄：");
		int age = scan.nextInt();
		System.out.println(age);

		System.out.println("请输入你的体重：");
		double weight = scan.nextDouble();
		System.out.println(weight);

		System.out.println("你是否相中我了呢？(true/false)");
		boolean isLove = scan.nextBoolean();
		System.out.println(isLove);

		//对于char型的获取，Scanner没有提供相关的方法。只能获取一个字符串
		System.out.println("请输入你的性别：(男/女)");
		String gender = scan.next();//"男"
		char genderChar = gender.charAt(0);//获取索引为0位置上的字符
		System.out.println(genderChar);
		
    scan.close();//关闭对象，释放资源，防止内存泄漏

	}

}
```



![image-20240308151108124](/Users/ola/Library/Application Support/typora-user-images/image-20240308151108124.png)

![image-20240308151335020](/Users/ola/Library/Application Support/typora-user-images/image-20240308151335020.png)

# 6.Random随机数

> 学习Random和学习Scanner方式方法一样

```java
1.概述:java自带的一个类
2.作用:可以在指定的范围内随机一个整数
3.位置:java.util
4.使用:
  a.导包:import java.util.Random
  b.创建对象:
    Random 变量名 = new Random()
  c.调用方法,生成随机数:
    变量名.nextInt() -> 在int的取值范围内随机一个整数
```

```java
public class Demo01Random {
    public static void main(String[] args) {
        //创建对象
        Random rd = new Random();
        int data = rd.nextInt();
        System.out.println("data = " + data);
    }
}
```

```java
在指定范围内随机一个数:
nextInt(int bound) -> 生成0-(bound-1)
    
a.nextInt(10) -> 生成0-9
b.在1-10之间随机一个数: nextInt(10)+1 -> (0-9)+1 -> 1-10
c.在1-100之间随机一个数:nextInt(100)+1 -> (0-99)+1 -> 1-100
d.在100-999之间随机一个数: nextInt(900)+100 -> (0-899)+100 -> 100-999
```

```java
public class Demo02Random {
    public static void main(String[] args) {
        //创建对象
        Random rd = new Random();
        //在1-100之间随机
        int data1 = rd.nextInt(100)+1;
        System.out.println("data1 = " + data1);

        System.out.println("=====================");

        //在100-999之间随机一个数
        int data2 = rd.nextInt(900)+100;
        System.out.println("data2 = " + data2);
    }
}

```



# Practice

> ```
> 从键盘分别输入年、月、日，判断这一天是当年的第几天
> 注：判断一年是否是闰年的标准：
> 可以被4整除，但不可被100整除 或 可以被400整除
> 例如：1900，2200等能被4整除，但同时能被100整除，但不能被400整除，不是闰年
> ```

```java
public class SwitchCase1 {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        //input information
        System.out.println("Please inter the year");
        int year = input.nextInt();
        System.out.println("Please inter the month");
        int month = input.nextInt();
        System.out.println("Please inter the day");
        int day = input.nextInt();

        //tell year is leap year or not
        boolean yearState;
        if((year % 4 == 0 && year % 100 != 0)||year % 400 == 0){
            yearState=true;
        }else{
            yearState=false;
        }

        //save days
        int sumDays = getDays(month, yearState, day);

        System.out.println(year + "年" + month + "月" + day + "日是当年的第" + sumDays + "天");
    }

    private static int getDays(int month, boolean yearState, int day) {
        int sumDays=0;

        switch(month){
            case 12:
                sumDays += 30;
            case 11:
                sumDays += 31;
            case 10:
                sumDays += 30;
            case 9:
                sumDays += 31;
            case 8:
                sumDays += 31;
            case 7:
                sumDays += 30;
            case 6:
                sumDays += 31;
            case 5:
                sumDays += 30;
            case 4:
                sumDays += 31;
            case 3:
                //sumDays += 28;
                //判断year是否是闰年
                if(yearState){
                    sumDays += 29;
                }else{
                    sumDays += 28;
                }

            case 2:
                sumDays += 31;
            case 1:
                sumDays += day;
        }
        return sumDays;
    }
}
```

