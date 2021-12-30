# JavaSE_03【流程控制语句】

## 今日内容

- if else判断语句
- switch选择语句

## 学习目标

- [ ] 掌握键盘输入各种数据类型的值

- [ ] 理解if语句的格式和执行流程

- [ ] 理解if...else语句的格式和执行流程

- [ ] 理解if...else if语句的格式和执行流程

- [ ] 了解if语句和三元运算符互换

- [ ] 理解switch选择语句的格式和执行流程

- [ ] 掌握switch选择语句接收的数据类型

- [ ] 理解case的穿透性

- [ ] 掌握break在switch中的使用

- [ ] 掌握default在switch中的使用

- [ ] 了解Math.random()和Math.sqrt(x)等的使用

  

# 第三章 流程控制

不论哪一种编程语言，都会提供两种基本的流程控制结构：分支结构和循环结构。其中分支结构用于实现根据条件来选择性地执行某段代码，循环结构则用于实现根据循环条件重复执行某段代码。

## 3.1 顺序结构

任何编程语言中最常见的程序结构就是顺序结构。顺序结构就是程序从上到下逐行地执行，中间没有任何判断和跳转。如果main方法的多行代码之间没有任何流程控制，则程序总是从上向下依次执行，排在前面的代码先执行，排在后面的代码后执行。

```java
public static void main(String[] args){
    //顺序执行，根据编写的顺序，从上到下运行
    System.out.println(1);
    System.out.println(2);
    System.out.println(3);
}
```

## 3.2 输入语句

键盘输入代码的三个步骤：

1、准备Scanner类型的变量

2、提示输入xx

3、接收输入内容

示例代码：

```java
//1、准备Scanner类型的变量
//Scanner是一个引用数据类型，它的全名称是java.util.Scanner
//input就是一个引用数据类型的变量了，赋给它的值是一个对象
java.util.Scanner input = new java.util.Scanner(System.in);//System.in默认代表键盘输入

//2、提示输入xx
System.out.print("请输入一个整数：");

//3、接收输入内容
int num = input.nextInt();

//列出各种数据类型的输入
int num = input.nextInt();
long bigNum = input.nextLong();
double d = input.nextDouble();
boolean b = input.nextBoolean();
String s = input.next();
char c = input.next().charAt(0);//先按照字符串接收，然后再取字符串的第一个字符（下标为0）
```

### 语法案例演示1：

从键盘输入个人信息

```java
class Day03_Test02_Input{
	public static void main(String[] args){
		//这里变量取什么名，下面就用什么.
		//例如：这里取名input，下面就用input.
		java.util.Scanner input = new java.util.Scanner(System.in);
		
		System.out.print("请输入姓名：");
		String name = input.next();
		
		System.out.print("请输入年龄：");
		int age = input.nextInt();
		
		System.out.print("请输入性别：");
		//input.next()得到字符串，不管你输入几个字符，
		//.charAt(0)：从字符串中取出一个字符，(0)表示取第一个字符，(1)表示取第二个字符
		//charAt(index)：也是一个方法，从第二个单词开始首字母大写，所以A是大写
		char gender = input.next().charAt(0);
		
		System.out.print("请输入体重：");
		double weight = input.nextDouble();
		
		System.out.print("请输入是否已婚(true/false)：");
		boolean isMarry = input.nextBoolean();
		
		System.out.println("姓名：" + name);
		System.out.println("年龄：" + age);
		System.out.println("性别：" + gender);
		System.out.println("体重：" + weight);
		System.out.println("婚否：" + (isMarry?"是":"否"));
	}
}
```

### 语法案例演示2：next()与nextLine()

```java
/*
next()方法：
	遇到空格等空白符，就认为输入结束
nextLine()方法：
	遇到回车换行，就认为输入结束
	
如果你在键盘输入过程中，遇到java.util.InputMismatchException，
说明你输入的数据类型与接收数据的变量的类型不匹配
*/
class Day03_Test04_Input2{
	public static void main(String[] args){
		java.util.Scanner input = new java.util.Scanner(System.in);
		
		System.out.print("请输入姓名：");
		//String name = input.next();//张 三  只能接收张，后面的空格和三无法接收，被下面的输入接收
		String name = input.nextLine();
		System.out.println("name = " + name);
		
		System.out.print("请输入年龄：");
		int age = input.nextInt();	//23回车换行  这里只接收23，回车换行被下面的输入接收	
		input.nextLine();//读取23后面的回车换行，但是这个不需要接收，只有下面一个输入是nextLine()情况下才需要这样，如果下面的输入是next()或者是nextInt(),nextDouble()等就不需要这么干
		System.out.println("age = " + age);
		
		System.out.print("请输入电话号码：");
		String tel = input.nextLine();
		System.out.println("tel = " + tel);
	}
}
```



## 3.3 分支结构：if语句第一种格式

- **if语句第一种格式：** if

```java
if(条件表达式)｛
  	语句体;
｝
```

- **执行流程**

  - 首先判断条件表达式看其结果是true还是false

  - 如果是true就执行语句体

  - 如果是false就不执行语句体

    ![](img\if.jpg)

### 语法案例演示1：

```java
public static void main(String[] args){
    System.out.println("开始");
    // 定义两个变量
    int a = 10;
    int b = 20;
    //变量使用if判断
    if (a == b){
      	System.out.println("a等于b");
    }
    int c = 10;
    if(a == c){
      	System.out.println("a等于c");
    }
    System.out.println("结束");
｝
```

### 语法案例演示2

案例：从键盘输入年份，请输出该年的2月份的总天数。闰年2月份29天，平年28天。

闰年：
（1）能被4整除，不能被100整除
（2）能被400整除

```java
public class Test {
	public static void main(String[] args) {
		java.util.Scanner input = new java.util.Scanner(System.in);
		System.out.print("请输入年份：");
		int year = input.nextInt();
		int days = 28;
		
		if(year%4==0 && year%100!=0 || year%400==0){
			days++;
		}
		System.out.println(year + "年的2月份共" + days + "天");
		input.close();
	}
}
```

```java
public class Test {
	public static void main(String[] args) {
		java.util.Scanner input = new java.util.Scanner(System.in);
		System.out.print("请输入年份：");
		int year = input.nextInt();
		int days = 28;
		
		if(year%4==0 && year%100!=0 || year%400==0)
			days++;//当语句块只有一句时，可以省略{}，但是建议还是保留比较靠谱
		
		System.out.println(year + "年的2月份共" + days + "天");
		input.close();
	}
}
```



## 3.4 分支结构：if语句第二种格式

- **if语句第二种格式：** if...else

```java
if(关系表达式) { 
  	语句体1;
}else {
  	语句体2;
}
```

- 执行流程

  - 首先判断关系表达式看其结果是true还是false

  - 如果是true就执行语句体1

  - 如果是false就执行语句体2

    ![](img\ifelse.jpg)

### 语法案例演示1：

```java
public static void main(String[] args){
    // 判断给定的数据是奇数还是偶数
    // 定义变量
    int a = 1;
    if(a % 2 == 0) {
      	System.out.println("a是偶数");
    } else{
      	System.out.println("a是奇数");
    }
    System.out.println("结束");
}
```

### 语法案例演示2：if语句和三元运算符的互换

在某些简单的应用中，if语句是可以和三元运算符互换使用的。

```java
public static void main(String[] args) {
    int a = 10;
    int b = 20;
    //定义变量，保存a和b的较大值
    int max;
    if(a > b) {
      	max = a;
    } else {
      	max = b;
    }
    //可以上述功能改写为三元运算符形式
    max = a > b ? a : b;
}
```

```java
public static void main(String[] args) {
    int a = 10;
    int b = 20;
    //定义变量，保存a和b的较大值
    int max;
    if(a > b) 
      	max = a;//当语句块只有一个语句时，可以省略{}，但是不建议省略{}
     else 
      	max = b;
}
```

### 练习：求出最大值

从键盘输入三个数，求出最大值，用单分支if和双分支if..else来计算

```java
class Day03_Test08_MaxValueExer{
	public static void main(String[] args){
		java.util.Scanner input = new java.util.Scanner(System.in);
		
		System.out.print("请输入第1个整数：");
		int a = input.nextInt();
		
		System.out.print("请输入第2个整数：");
		int b = input.nextInt();
		
		System.out.print("请输入第3个整数：");
		int c = input.nextInt();
		
		/*
		int max;//存储三个数中的最大值
		if(a > b){
			max = a;
		}else{
			max = b;
		}
		if(c > max){
			max = c;
		}
		*/
		int max = a>b ? a : b;
		max = max>c ? max : c;
		System.out.println(a+","+b+","+c+"中最大的是："+ max);
	}
}
```



## 3.5 分支结构：if语句第三种格式

- **if语句第三种格式：** if...else if ...else

```java
if (判断条件1) {
  	执行语句1;
} else if (判断条件2) {
  	执行语句2;
}
...
}else if (判断条件n) {
 	执行语句n;
} else {
  	执行语句n+1;
}
```

- **执行流程**
  - 首先判断关系表达式1看其结果是true还是false

  - 如果是true就执行语句体1，然后结束当前多分支

  - 如果是false就继续判断关系表达式2看其结果是true还是false

  - 如果是true就执行语句体2，然后结束当前多分支

  - 如果是false就继续判断关系表达式…看其结果是true还是false

  - …

  - 如果没有任何关系表达式为true，就执行语句体n+1，然后结束当前多分支。

    ![](img\ifelseif.jpg)

### 语法案例演示1：

计算如下函数：x和y的关系满足如下：
（1）x>=3；         y = 2x + 1;
（2）-1<=x<3；   y = 2x;
（3）x<-1；          y = 2x – 1;
从键盘输入x的值，计算出y的值并输出。

```java
public static void main(String[] args) {
    java.util.Scanner input = new java.util.Scanner(System.in);
    System.out.print("请输入x的值：");
    int x = input.nextInt();
    int y;
    if (x>= 3) {
      	y = 2 * x + 1;
    } else if (x >= -1 && x < 3) {
      	y = 2 * x;
    } else  {
      	y = 2 * x - 1;
    }
    System.out.println("y的值是："+y);
}
```

```java
public static void main(String[] args) {
    java.util.Scanner input = new java.util.Scanner(System.in);
    System.out.print("请输入x的值：");
    int x = input.nextInt();
    int y;
    if (x>= 3) {
      	y = 2 * x + 1;
    } else if (x >= -1) {
      	y = 2 * x;
    } else  {
      	y = 2 * x - 1;
    }
    System.out.println("y的值是："+y);
}
```

![1561700798198](img/1561700798198.png)

![1561700825016](img/1561700825016.png)

### 语法案例演示2：

- 通过指定考试成绩，判断学生等级
  - 90-100      优秀
  - 80-89        好
  - 70-79        良
  - 60-69        及格
  - 60以下    不及格

```java
public static void main(String[] args) {	
    int score = 89；
    if(score<0 || score>100){
      	System.out.println("你的成绩是错误的");
    }else if(score>=90 && score<=100){
      	System.out.println("你的成绩属于优秀");
    }else if(score>=80 && score<90){
      	System.out.println("你的成绩属于好");
    }else if(score>=70 && score<80){
      	System.out.println("你的成绩属于良");
    }else if(score>=60 && score<70){
      	System.out.println("你的成绩属于及格");
    }else {
      	System.out.println("你的成绩属于不及格");
    }	
}
```
![1561436569004](img/1561436569004.png)

```java
	public static void main(String[] args) {	
	    int score = 89;
	    if(score<0 || score>100){
	      	System.out.println("你的成绩是错误的");
	    }else if(score>=90){
	      	System.out.println("你的成绩属于优秀");
	    }else if(score>=80){
	      	System.out.println("你的成绩属于好");
	    }else if(score>=70){
	      	System.out.println("你的成绩属于良");
	    }else if(score>=60){
	      	System.out.println("你的成绩属于及格");
	    }else {
	      	System.out.println("你的成绩属于不及格");
	    }	
	}
```

![1561437387616](img/1561437387616.png)

## 3.6  分支结构：if..else嵌套

在if的语句块中，或者是在else语句块中，
又包含了另外一个条件判断（可以是单分支、双分支、多分支）

执行的特点：
（1）如果是嵌套在if语句块中的
只有当外部的if条件满足，才会去判断内部的条件
（2）如果是嵌套在else语句块中的
只有当外部的if条件不满足，进入else后，才会去判断内部的条件

### 语法案例演示1：

```java
	public static void main(String[] args) {	
	    int score = 89;
	    if(score<0 || score>100){
	      	System.out.println("你的成绩是错误的");
	    }else{
	    	if(score>=90){
		      	System.out.println("你的成绩属于优秀");
		    }else if(score>=80){
		      	System.out.println("你的成绩属于好");
		    }else if(score>=70){
		      	System.out.println("你的成绩属于良");
		    }else if(score>=60){
		      	System.out.println("你的成绩属于及格");
		    }else {
		      	System.out.println("你的成绩属于不及格");
		    }	
	    }
	}
```

```java
	//省略{}的情况，else中嵌套了一个完整的多分支结构，也算是一个语句，称为复合语句，所以也可以省略{}
	public static void main(String[] args) {	
	    int score = 89;
	    if(score<0 || score>100)
	      	System.out.println("你的成绩是错误的");
	    else
	    	if(score>=90){
		      	System.out.println("你的成绩属于优秀");
		    }else if(score>=80){
		      	System.out.println("你的成绩属于好");
		    }else if(score>=70){
		      	System.out.println("你的成绩属于良");
		    }else if(score>=60){
		      	System.out.println("你的成绩属于及格");
		    }else {
		      	System.out.println("你的成绩属于不及格");
		    }
	}
```

### 语法案例演示2：

从键盘输入一个年份，和月份，输出该年份该月的总天数

要求：年份为正数，月份1-12

```java
	public static void main(String[] args){
		//从键盘输入一个年份，和月份
		java.util.Scanner input = new java.util.Scanner(System.in);
		
		System.out.print("年份：");
		int year = input.nextInt();
		
		System.out.print("月份：");
		int month = input.nextInt();
		
		if(year>0){
			if(month>=1 && month<=12){
				//合法的情况
				int days;
				if(month==2){
					if(year%4==0 && year%100!=0 || year%400==0){
						days = 29;
					}else{
						days = 28;
					}
				}else if(month==4 || month==6  || month==9 || month==11){
					days = 30;
				}else{
					days = 31;
				}
				System.out.println(year+"年" + month + "月有" + days +"天");
			}else{
				System.out.println("月份输入不合法");
			}
		}else{
			System.out.println("年份输入不合法");
		}
	}
```

## 3.7 分支结构：switch选择结构

语法格式：

```java
switch(表达式){
    case 常量值1:
        语句块1;
        【break;】
    case 常量值2:
        语句块2;
        【break;】   
    。。。
   【default:
        语句块n+1;
        【break;】
     】
}
```

执行过程：

（1）入口

①当switch(表达式)的值与case后面的某个常量值匹配，就从这个case进入；

②当switch(表达式)的值与case后面的所有常量值都不匹配，寻找default分支进入;不管default在哪里

（2）一旦从“入口”进入switch，就会顺序往下执行，直到遇到“出口”，即可能发生贯穿

（3）出口

①自然出口：遇到了switch的结束}

②中断出口：遇到了break等



> 注意：
>
> （1）switch(表达式)的值的类型，只能是：4种基本数据类型（byte,short,int,char），两种引用数据类型（JDK1.5之后枚举、JDK1.7之后String）
>
> （2）case后面必须是常量值，而且不能重复

### 语法案例演示1：

```java
public class SwitchDemo01 {
	public static void main(String[] args) {
		//定义指定的星期
		int weekday = 5;
		
		//switch语句实现选择
		switch(weekday) {
            case 1:
                System.out.println("星期一");
                break;
            case 2:
                System.out.println("星期二");
                break;
            case 3:
                System.out.println("星期三");
                break;
            case 4:
                System.out.println("星期四");
                break;
            case 5:
                System.out.println("星期五");
                break;
            case 6:
                System.out.println("星期六");
                break;
            case 7:
                System.out.println("星期日");
                break;
            default:
                System.out.println("你的数字有误");
                break;
		}
	}
}
```
### 语法案例演示2：case的穿透性

在switch语句中，如果case的后面不写break，将出现穿透现象，也就是一旦匹配成功，不会在判断下一个case的值，直接向后运行，直到遇到break或者整个switch语句结束，switch语句执行终止。

练习：根据指定的月份输出对应季节（if语句）

```java
/*
 * 需求：定义一个月份，输出该月份对应的季节。
 * 		一年有四季
 * 		3,4,5	春季
 * 		6,7,8	夏季
 * 		9,10,11	秋季
 * 		12,1,2	冬季
 * 
 * 分析：
 * 		A:指定一个月份
 * 		B:判断该月份是几月,根据月份输出对应的季节
 * 			if
 * 			switch
 */
public class SwitchTest01 {
	public static void main(String[] args) {
		//指定一个月份
		int month = 5;
		
		/*
		if (month == 1) {
			System.out.println("冬季");
		} else if (month == 2) {
			System.out.println("冬季");
		} else if (month == 3) {
			System.out.println("春季");
		} else if (month == 4) {
			System.out.println("春季");
		} else if (month == 5) {
			System.out.println("春季");
		} else if (month == 6) {
			System.out.println("夏季");
		} else if (month == 7) {
			System.out.println("夏季");
		} else if (month == 8) {
			System.out.println("夏季");
		} else if (month == 9) {
			System.out.println("秋季");
		} else if (month == 10) {
			System.out.println("秋季");
		} else if (month == 11) {
			System.out.println("秋季");
		} else if (mouth == 12) {
			System.out.println("冬季");
        } else {
            System.out.println("你输入的月份有误");
        }
		*/
		
		// 改进版
		if ((month == 1) || (month == 2) || (month == 12)) {
			System.out.println("冬季");
		} else if ((month == 3) || (month == 4) || (month == 5)) {
			System.out.println("春季");
		} else if ((month == 6) || (month == 7) || (month == 8)) {
			System.out.println("夏季");
		} else if ((month == 9) || (month == 10) || (month == 11)) {
			System.out.println("秋季");
		} else {
			System.out.println("你输入的月份有误");
		}
	}
}
```

练习：根据指定的月份输出对应季节（switch语句）

```java
/*
 * 需求：指定一个月份，输出该月份对应的季节。
 * 		一年有四季
 * 		3,4,5	春季
 * 		6,7,8	夏季
 * 		9,10,11	秋季
 * 		12,1,2	冬季
 * 
 * 分析：
 * 		A:指定一个月份
 * 		B:判断该月份是几月,根据月份输出对应的季节
 * 			if
 * 			switch
 */
public class SwitchTest02 {
	public static void main(String[] args) {
		//指定一个月份
		int month = 5;
		
		/*
		switch(month) {
            case 1:
                System.out.println("冬季");
                break;
            case 2:
                System.out.println("冬季");
                break;
            case 3:
                System.out.println("春季");
                break;
            case 4:
                System.out.println("春季");
                break;
            case 5:
                System.out.println("春季");
                break;
            case 6:
                System.out.println("夏季");
                break;
            case 7:
                System.out.println("夏季");
                break;
            case 8:
                System.out.println("夏季");
                break;
            case 9:
                System.out.println("秋季");
                break;
            case 10:
                System.out.println("秋季");
                break;
            case 11:
                System.out.println("秋季");
                break;
            case 12:
                System.out.println("冬季");
                break;
            default:
                System.out.println("你输入的月份有误");
                break;
		}
		*/
	
        // 改进版 
		switch(month) {
            case 1:
            case 2:
            case 12:
                System.out.println("冬季");
                break;
            case 3:
            case 4:
            case 5:
                System.out.println("春季");
                break;
            case 6:
            case 7:
            case 8:
                System.out.println("夏季");
                break;
            case 9:
            case 10:
            case 11:
                System.out.println("秋季");
                break;
            default:
                System.out.println("你输入的月份有误");
                break;
		}
	}
}
```
