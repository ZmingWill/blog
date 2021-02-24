---
title: Java基础之基本语法
date: 2020/2/3 21:30:26
layout: java2
permalink: java2.html
cover:  http://5b0988e595225.cdn.sohucs.com/images/20190418/47658e88f01a43d5b520242152262ddb.jpeg
---
主要介绍Java基本语法，供回顾使用。
<!--more-->
## 学习思维导图
![](/images/java1/java11.jpg)
![](/images/java1/java12.jpg)
## 2.1  关键字
### 关键字的定义和特点
•定义：被Java语言赋予了特殊含义，用做专门用途的字符串（单词）
•特点：关键字中所有字母都为小写
![](/images/java2/java21.PNG)
![](/images/java2/java22.PNG)

---
### 保留字
•Java保留字：现有Java版本尚未使用，但以后版本可能会作为关键字使用。自己命名标记符时要避免使用这些保留字
•byValue、cast、future、 generic、 inner、 operator、 outer、 rest、 var 、 goto 、const

---

### 文本编辑
![](/images/java2/java23.PNG)

---
### 标识符：
•Java 对各种变量、方法和类等要素命名时使用的字符序列称为标识符
•**凡是自己可以起名字的地方都叫标识符。**
#### 定义合法标识符规则：
由26个英文字母大小写，0-9，$或_组成
•***数字不可以开头。***
•***不可以使用关键字和保留字，但能包含关键字和保留字。***
•***Java中严格区分大小写，长度无限制。***
•***标识符不能包含空格。***
注意：在起名字时，为了提高阅读性，要尽量有意义，“见名知意”。

---

### Java中的名称命名规范
#### Java中的名称命名规范：
•**包名：** 多单词组成时所有字母都小写：xxxyyyzzz
•**类名、接口名：** 多单词组成时，所有单词的首字母大写：XxxYyyZzz
•**变量名、方法名：** 多单词组成时，第一个单词首字母小写，第二个单词开始每个单词首字母大写：xxxYyyZzz
•**常量名：** 所有字母都大写。多单词时每个单词用下划线连接：XXX_YYY_ZZZ

## 2.3  变  量
![](/images/java2/java24.PNG)

---
### 变量的概念：
•内存中的一个存储区域
•该区域有自己的名称（变量名）和类型（数据类型）
•**Java中每个变量必须先声明，后使用**
•该区域的数据可以在同一类型范围内不断变化
### 使用变量注意：
•变量的作用域：一对{ }之间有效
•初始化值
### 定义变量的格式：
•数据类型    变量名  =  初始化值
•**变量是通过使用变量名来访问这块区域的**

---
### 变量的分类-按数据类型
**对于每一种数据都定义了明确的具体数据类型，在内存中分配了不同大小的内存空间。**
![](/images/java2/java25.PNG)
#### 补充：变量的分类-按声明的位置的不同
**•在方法体外，类体内声明的变量称为成员变量。**
**•在方法体内部声明的变量称为局部变量。**
![](/images/java2/java26.PNG)
#### ●注意：二者在初始化值方面的异同:
同：都有生命周期      异：局部变量除形参外，需显式初始化。

---
### 整数类型：byte、short、int、long
•Java各整数类型有固定的表数范围和字段长度，不受具体OS的影响，以保证java程序的可移植性。
**•java的整型常量默认为 int 型，声明long型常量须后加‘l’或‘L’**
![](/images/java2/java27.PNG)
---
### 浮点类型：float、double
•与整数类型类似，Java 浮点类型也有固定的表数范围和字段长度，不受具体OS的影响。
**•Java 的浮点型常量默认为double型，声明float型常量，须后加‘f’或‘F’。**
#### 浮点型常量有两种表示形式：
•十进制数形式：如：5.12       512.0f        .512   (必须有小数点）
•  科学计数法形式:如：5.12e2      512E2     100E-2
![](/images/java2/java28.PNG)
---

### 字符类型：char

 •char 型数据用来表示通常意义上“字符”(2字节)
#### 字符型常量的三种表现形式：
• 字符常量是用单引号(‘ ’)括起来的单个字符，涵盖世界上所有书面语的字符。例如：char c1                   = 'a';   char c2 = '中'; char c3 =  '9';
•Java中还允许使用转义字符‘\’来将其后的字符转变为特殊字符型常量。例如：char c3 = ‘\n’;   // '\n'表示换行符
• 直接使用 Unicode 值来表示字符型常量：‘\uXXXX’。其中，XXXX代表一个十六进制整数。如：\u000a 表示 \n。
•char类型是可以进行运算的。因为它都对应有Unicode码。
![](/images/java2/java29.PNG)
---
### 布尔类型：boolean
#### boolean 类型适于逻辑运算，一般用于程序流程控制：
**if条件控制语句；**                
**while循环控制语句；**
**do-while循环控制语句；**
**for循环控制语句；**
**boolean类型数据只允许取值true和false，无null。
                 不可以0或非 0 的整数替代false和true，这点和C语言不同。**

---
### 字符串： String类
**•值null可以赋值给任何引用类型（类、接口、数组）的变量，用以表示这个引用类型变量中保存的地址为空。
•String类属于引用类型，可用null赋值。
•String类是一个典型的不可变类，String对象创建出来就不可能被改变。创建出的字符串将存放在数据区，保证每个字符串常量只有一个，不会产生多个副本。**

      String s0 = “hello”;
      String s1 = “hello”;
      String s2 = “he” + “ll”+”o”;
        System.out.println(s0 ==s1);   
          System.out.println(s0 ==s2);
#### 输出：
**true
  true**
  ***String s3 = new String(“hello”);又如何理解呢？***


---

### 集成开发环境（IDE）
![](/images/java2/java210.PNG)
#### Eclipse安装（推荐）
官网下载，方法看以下网址
https://jingyan.baidu.com/article/b0b63dbf02e4d24a4830701a.html
网盘下载（推荐）
链接：https://pan.baidu.com/s/1qqiI22OgkW2aw1hTHIjFfQ
提取码：zugz
解压，使用

---

### 基本数据类型转换
**自动类型转换：容量小的类型自动转换为容量大的数据类型。数据类型按容量大小排序为：**
![](/images/java2/java211.PNG)
**•有多种类型的数据混合运算时，系统首先自动将所有数据转换成容量最大的那种数据类型，然后再进行计算。
•byte,short,char之间不会相互转换，他们三者在计算时首先转换为int类型。
•当把任何基本类型的值和字符串值进行连接运算时(+)，基本类型的值将自动转化为字符串类型。**

          String str1 = 4;        //判断对错：错  需要加上双引号
          String str2 = 3.5f + “”;             //判断str2对错：对
           System.out.println(str2);        //输出：3.5
             System.out .println(3+4+“Hello!”);      //输出：7Hello!
              System.out.println(“Hello!”+3+4);      //输出：Hello!34
            System.out.println(‘a’+1+“Hello!”);    //输出：98Hello!
          System.out.println(“Hello!”+‘a’+1);            //输出：Hello!a1

---

### 强制类型转换
**•自动类型转换的逆过程，将容量大的数据类型转换为容量小的数据类型。使用时要加上强制转换符（()），但可能造成精度降低或溢出,格外要注意。
•通常，字符串不能直接转换为基本类型，但通过基本类型对应的包装类则可以实现把字符串转换成基本类型。**
如： String a = “43”; int i = Integer.parseInt(a);
boolean类型不可以转换为其它的数据类型。


#### 判断是否能通过编译
1）

            short  s = 5;
            s = s-2;                       //判断：错
2）

            byte b = 3;
            b = b + 4;                  //判断：错
            b = (byte)(b+4);        //判断：对
3）

            char c = ‘a’;
            int  i = 5;
            double d = .314;
            double result = c+i+d;     //判断：对   102.314
4）

            byte b = 5;
            short s = 3;
            short t = s + b;          //判断：错


## 2.4  运算符
### 运算符是一种特殊的符号，用以表示数据的运算、赋值和比较等。
**算术运算符
赋值运算符
比较运算符（关系运算符）
逻辑运算符
位运算符
三元运算符**

---

### 1.算术运算符
![](/images/java2/java212.PNG)

---

### 算术运算符的注意问题
**•如果对负数取模，可以把模数负号忽略不记，如：5%-2=1。 但被模数是负数则不可忽略。此外，取模运算的结果不一定总是整数。
•对于除号“/”，它的整数除和小数除是有区别的：整数之间做除法时，只保留整数部分而舍弃小数部分。**
例如：int x=3510;x=x/1000*1000;  x的结果是？
“+”除字符串相加功能外，还能把非字符串转换成字符串.
      例如：System.out.println("5+5="+5+5); //打印结果是？5+5=55

#### 以下二者的区别：

                System.out.println('*' + '\t' +'*');
                System.out.println("*" + '\t' +'*');

#### 算术运算符：自加、自减:

      public class TestSign{
        public static void main(String[] args){
                int i1 = 10,i2 = 20;
                int i = i1++;
                System.out.print(“i=”+i);  //i=10
                System.out.println(“i1=”+i1);//i1=11
                i = ++i1;
                System.out.print(“i=”+i);//i=12
                System.out.println(“i1=”+i1);//i1=10 11 12 13
                i = i2--;
                System.out.print(“i=”+i);//i=20
                System.out.println(“i2=”+i2);//i2=19
                i = --i2;
                System.out.print(“i=”+i);//i=18
                System.out.println(“i2=”+i2);//i2=18
         }
}

---

### 2.赋值运算符
#### 符号：=
              **当“=”两侧数据类型不一致时，可以使用自动类型转换或使用强制类型转换原则进行处理。
              支持连续赋值。**

#### 扩展赋值运算符： +=, -=, *=, /=, %= ***分割线**

#### 思考1：
                  short s = 3;
                        s=s+2;  ①
                        s+=2;    ②

①和②有什么区别？

#### 思考2：
                  boolean b1 = false;
                 //区分好==和=的区别。
                 if(b1=true)
                   System.out.println("结果为真");
                     else
                   System.out.println("结果为假");

#### 思考3：
                 int i = 1;
                 i *= 0.1;
                System.out.println(i);//
                   i++;
                 System.out.println(i);//

---

### 3.比较运算符
![](/images/java2/java213.PNG)
**比较运算符的结果都是boolean型，也就是要么是true，要么是false。
比较运算符“==”不能误写成“=” 。**

---

### 4.逻辑运算符
**&—逻辑与         | —逻辑或         ！—逻辑非
&& —短路与      || —短路或        ^ —逻辑异或**
![](/images/java2/java214.PNG)
#### 逻辑运算符用于连接布尔型表达式，在Java中不可以写成3<x<6，应该写成x>3 & x<6 。
#### “&”和“&&”的区别：
单&时，左边无论真假，右边都进行运算；
双&时，如果左边为真，右边参与运算，如果左边为假，那么右边不参与运算。
**“|”和“||”的区别同理，||表示：当左边为真，右边不参与运算。
在不需要逻辑运算两边都参与运算的时候，尽量使用&&和||
异或( ^ )与或( | )的不同之处是：当左右都为true时，结果为false。
      理解：异或，追求的是“异”!**

#### 请写出每题的输出结果

          int x = 1;
           int y=1;

            if(x++==2 & ++y==2){
	               x =7;
                  }
               System.out.println("x="+x+",y="+y);//2 2

---

          int x = 1,y = 1;

            if(x++==2 && ++y==2){
	          x =7;
                }
                System.out.println("x="+x+",y="+y);//2 1

---

              int x = 1,y = 1;

                 if(x++==1 | ++y==1){
                    x=7;
                  }
               System.out.println("x="+x+",y="+y);//7 2

---


                  int x = 1,y = 1;

                   if(x++==1 || ++y==1){
	                x =7;
                 }
                  System.out.println("x="+x+",y="+y);//7 1
---

### 5.位运算符
![](/images/java2/java216.PNG)
#### 注意：无<<<
位运算是直接对二进制进行运算
![](/images/java2/java217.PNG)

---

### 6.三元运算符
#### 格式:
**(条件表达式)? 表达式1：表达式2；

                      为true，运算后的结果是表达式1；
            为false，运算后的结果是表达式2；**

#### 练习： 获取两个数中的较大数
             获取三个数中的较大数

#### 运算符的优先级
![](/images/java2/java218.PNG)

## 2.5  程序流程控制
#### 顺序结构
            ***程序从上到下逐行地执行，中间没有任何判断和跳转。***

#### 分支结构
            ***根据条件，选择性地执行某段代码。
            有if…else和switch两种分支语句。***

#### 循环结构
            ***根据循环条件，重复性的执行某段代码。
            有while、do…while、for三种循环语句。***
       注：JDK1.5之后提供了foreach循环，方便的遍历集合、数组元素。
**上一行运算符总优先于下一行。**

### 顺序结构
#### Java中定义成员变量时采用合法的前向引用。如：
            public class Test{
              int num1 = 12;
              int num2 = num1 + 2;
            }
#### 错误形式：
            public class Test{
             int num2 = num1 + 2；
             int num1 = 12;
            }

### 分支语句1： if-else语句

#### if语句三种格式：
**1.
                 if(true){
                 执行代码块；
                    }
2.
          if(条件表达式){
          执行代码块；
         }
           else{
        执行代码块；
          }
3.  if(条件表达式){
  执行代码块；
      }
      else if (条件表达式){
  执行代码块；
      }
       ……
       else{
  执行代码块；
       }**
#### if-else语句应用举例
                   public class TestAge{
                       public static void main(String args[]){
                     int age = 75;
                     if (age< 0) {
                    System.out.println("不可能！");
                  } else if (age>250) {
                       System.out.println("是个妖怪！");
                     } else {
                 System.out.println(“人家芳龄 " + age +" ,马马乎乎啦！");
                      }
                    }
                 }

### 分支结构2：switch语句
**switch(变量){
  case 常量1:
  语句1;
  break;
  case 常量2:
  语句2;
  break;
  … …
  case 常量N:
  语句N;
  break;
  default:
  语句;
  break;
   }**

#### switch语句应用举例
                          public class Test{
                            public static void main(String args[]){
                               int i = 1;
                               switch (i) {
                             case 0:
                        System.out.println("zero");
                               break;
                                   case 1:
                           System.out.println("one");
                               break;
                                  default:
                               System.out.println("default");
                               break;
                                }
                            }
                         }
#### switch语句应用举例
                      public class Test{
                          public static void main(String args[]){
                             String season = “summer”;
                           switch (season) {
                                case “spring”:
                         System.out.println(“春暖花开");
                              break;
                                case “summer”:
                         System.out.println(“夏日炎炎");
                              break;
                                case “autumn”:
                         System.out.println(“秋高气爽");
                              break;
                                case “winter”:
                        System.out.println(“冬雪皑皑");
                              break;
                                     default:
                         System.out.println(“季节输入有误");
                              break;
                                   }}}


### switch语句有关规则
**switch(表达式)中表达式的返回值必须是下述几种类型之一：byte，short，char，int，枚举，String；
case子句中的值必须是常量，且所有case子句中的值应是不同的；
default子句是可任选的，当没有匹配的case时，执行default
break语句用来在执行完一个case分支后使程序跳出switch语句块；如果没有break，程序会顺序执行到switch结尾**

### switch和if语句的对比
#### if和switch语句很像，具体什么场景下，应用哪个语句呢？

***如果判断的具体数值不多，而且符合byte、 short 、int、 char这四种类型。虽然两个语句都可以使用，建议使用swtich语句。因为效率稍高。
其他情况：对区间判断，对结果为boolean类型判断，使用if，if的使用范围更广。***


## 总结：

##### 关键字：就是在java语言编程的时候，在关键的地方使用的单词，体现关键的地方的含义，这些单词都是特有的事先定义好的

##### 保留字：可能在以后被用来作为关键字的单词，java已经把这些单词预定了，这些单词尽量就不要在编程中去随意使用

                    abc_1$

##### 标识符可以是Test1,不能是1Test

##### 比如，类名不能直接使用class,可以是class1

##### 命名规范，是一套约定俗成的规则


##### 代数，未知数的概念
设x=1，x+1=?

##### java中变量的定义：数据类型 变量名 = 变量的值，例如：int i = 1

                       int i = 1
                       i = 2

##### 注意：声明变量过程中的这个=，不是数学意义上的=，在java编程中代表赋值（赋予变量值）

##### 变量的类型：声明的变量的数据类型就是变量的类型

##### 在java中，数据类型分为基本数据类型和引用数据类型，其中基本数据类型有8中，除了这8中之外其他所有的数据类型都是引用数据类型

##### byte的范围-128到127之间，声明byte类型变量的时候赋值不能超过这个范围，给byte类型变量赋值时不能超过这个范围

                    byte b = 130，这个就是超出范围了是错误的

                    byte b = 126

bit是什么单位？

0100110，这个就7bit


                     byte b = 126
                          int i = 1
                      short s = 1
                      long l = 3l

##### 这个long类型变量赋值时要在值的后面跟上一个字母l

                     double d = 1.22
                    float f = 1.22f

##### float类型变量赋值时值后面跟上字母f

##### 字符：用英文的单引号括起来的单个的字母、数字、符号

比如：

                           char c1 = 'a'
                          char c2 = '1'
                          char c3 = '%'
                           char c4 = '\n'
                            char c5 = '\''
                          boolean b2 = false

##### byte short int long float double char boolean,8种基本数据类型

##### 字符串？就是由0到多个字母数字符号共同组成的一个串，这个串要用英文的双引号括起来

                      String str = "hello world";
                     System.out.println(str);

##### 引用类型，都可以用null作为值，也就是说可以在初始化的时候赋值为null
##### String是引用类型，也就是说可以使用null作为值

                        int i0 = 1
                       int i1 = 1

以上这种会在内存中存储2个1的值

                   String s0 = "hello"
                    String s1 = "hello"

###### 这种的，不会在内存中存在两个"hello"，只存在1一个"hello"
##### 假设"hello"的内存地址xxxxx,声明s0变量时给s0赋值"hello"实际上让s0变量引用"hello"的内存地址xxxxx；当我们再声明变量s1也赋值"hello"的时候实际上也是直接把已经存在的"hello"的内存地址给s1引用

##### ASCII码：上个世纪60年代，美国制定了一套字符编码，对英语字符与二进制位之间的关系，做了统一规定。这被称为ASCII码。ASCII码一共规定了128个字符的编码，比如空格“SPACE”是32（二进制00100000），大写的字母A是65（二进制01000001）。

                     String s3 = "he" + "ll" + "o";

创建一个java文件，用文本编辑器打开，写代码，打开dos界面，javac编译，java运行

##### 集成开发环境就是为了解决刚才咱们所说的问题，里面包含文本编辑工作，自动编译，简化运行，随时进行代码的调试


### 数字类型的运算规则：
##### 1、有多种类型的数据混合运算时，系统首先自动将所有数据转换成容量最大的那种数据类型，然后再进行计算。数字类型的从小到大分别是byte、short、int、long、float、double。
##### 2、数字类型的运算中，多个相同类型变量参与的运算，变量要先转换为相对应的数据类型的默认类型（比如两个byte类型的变量相加，会先把两个byte类型的变量转换成默认的int类型之后再计算，得到的结果是int类型）。这种情况适用于变量的数据类型的容量比默认类型的容量小，（比如byte，short，都比int小）
##### 3、byte,short,char之间不会相互转换，他们三者在计算时首先转换为int类型。



---

### 相关代码：
                    public class Test1{
	                    public static void main(String[] args){
	                	//System.out.print("sss\n");
		                 //System.out.println("sss");

	                    	byte b = 1;
	                      	System.out.println(b);

	                           	short s = 2;
		                              System.out.println(s);

	                           	int i = 4;
	                         	System.out.println(i);

	                          	long l = 79l;
                     		System.out.println(l);

                    		float f = 1.23f;
	                              	System.out.println(f);

	                        	double d = 1.56;
	                    	System.out.println(d);

	                       	char c = 'a';
	                        	System.out.println(c);

	                      	boolean b1 = false;
	                                  	System.out.println(b1);

	                       	String str = "hello" + " world";
		                  System.out.println(str);
                                 	}
                              }



                   public class Test {
	                  public static void main(String[] args){
	                	//System.out.println("hello world!!!!");
        //		int i = 0;//声明并初始化变量
        //		i = 1;
        //		int k = 10;
        //		i = k;

        //		short s = 9;
        //		short s0 = 11;
        //		s0 = s;
        //		
         //		byte b = 1;
        //		int m = b;

         //		int i = 0;
        //		byte b = i;//这种的异常叫做编译期异常，在javac的时候可以发现
        //
        //		int i = 1;
        //		short s = 2;
        //		byte b = 3;
        //		
        //		int res = i + s + b;//问题，最后得到的数字6是一个声明类型的呢？在计算过程中i、s、b这3个变量会做数据类型的转化吗？
        //		//在计算过程中，整数类型是int的范围最大，所以s和b都分别先转换成int类型然后进行加的运算，最终的结果是int的数据
        //		
        //		char c = 'a';//char类型的数据在与数字进行数学运算的时候，它是转换为相对应的ASCII码的值然后再进行的计算
        //		
        //		byte b0 = 2;
        //		
        //		int k = c + b0;
        //		System.out.println(k);

        //		String str = "abc";
        //		
        //		int i = 1;
        //		
        //		String str0 = "" + 1 + 2 + 3;
        //		//当把任何基本类型的值和字符串值进行连接运算时(+)，基本类型的值将自动转化为字符串类型。
        //		System.out.println(str0);
        //		System.out.println(3 + 4 + "hello");
        //		
        //		//注意：当有一些列的+的运算的时候，如果某个部分其中含有字符串，那么这个字符串前边挨着的+开始一直往后都是要按照
        //		//字符串拼接去看
        //		
        //		String str1 = 1 + 3 + 5 + "a" + 2 + 6;//9a26
        //		System.out.println(str1);

        //		byte b = 9;
        //		int i = b;
        //		//以上这两行属于正常隐式转换数据类型，自动的
        //		
        //		
        //		int k = 7;
        //		
        //		byte b0 = (byte)k;//这个就是强制转换数据类型,转换的数据类型要用英文的小括号括起来
        //		
        //		
        //		int i0 = -3;
        //		
        //		System.out.println(-i0);
        //		
        //		System.out.println(1 + 2);
        //		//当整数除以整数的时候，会把结果的小数部分舍弃，只保留整数部分
        //		System.out.println(7.0 / 2);
        //		
        //		System.out.println(7 % 5);

        //		int i = 0;
        //		
        //		i++;
        //		++i;
        //		int k = i++;
        //		int k = ++i;
        //		//++和--分别是加1和减1的运算，++或者--符号在变量之前，先对变量进行运算然后再取变量的值；
        //		//如果++或者--符号在变量之后，就先取变量的值，再对变量进行运算
        //		System.out.println(k);
        //		System.out.println(i);

        //		String str = "h" + "e" + "llo";//字符串的加号是字符串拼接
        //		System.out.println(str);

        //		System.out.println(-5 % 2);
        //		
        //		System.out.println("5+5="+5+5);
        //		
        //		//char类型数据是可以做数学运算的，在做数学运算的时候把字符转化为ASCII码进行计算
        //		System.out.println('*' + '\t' +'*');
        //
        //		//字符串与其他数据类型相加时，实际上是把其他的数据转换为字符串，做字符串的拼接
        //		System.out.println("*" + '\t' +'*');

        //		int i = 1;
        //		short s = 2;
        //		
        //		i = s;//自动类型转换
        //		s = (short)i;//强制类型转换
        //		
        //		int i0 = 0;
        //		int i1 = 0;
                //		int i2 = 0;
        //		
        ////		i0 = 1;
        ////		i1 = 1;
        ////		i2 = 1;
                                //		
                        //		i0 = i1 = i2 = 1;//=可以联系赋值

        //		System.out.println(i0 + "," + i1 + "," + i2);

        //		int i = 1;

        ////		i = i + 2;
        //		
        //		i += 2;
        //		
        //		i -= 2;
        //		
        //		System.out.println(i);
        //		
        //		String str = "he";
        //		
        //		str += "llo";//字符串的+=是字符串的拼接
        //		
        //		System.out.println(str);
        //		
        //		short s = 2;
        //		
        //		s = (short)(s + 3);//变量参与运算时候，java程序不知道具体的这个变量在做完运算后会不会查重当前变量的范围，
        //		          //所有会先把变量转换为一个更大长度,这这个例子中，short是一个短整形数据，会转化为默认的int
        //		
        //		s += 3;//在使用扩展赋值运算符时，变量在参与运算时会把结果自动强制转换为当前变量的类型
        //		
        //		int  i = 1;
        //		
        //		i *= 0.1;
        ////		i = (int) (i * 0.1);
        //		System.out.println(i);
        //		
        //		i++;
        //		System.out.println(i);//

        //		System.out.println(4 == 5);
                        //		System.out.println(4 != 5);
		System.out.println(2 == 2 ? (3 == 3 ? 3 : 4) : "1");

                	}
        }
