---
title: Java基础之面向对象编程
date: 2020/2/6 21:00:11
layout: java4
permalink: java4.html
cover: http://5b0988e595225.cdn.sohucs.com/images/20190418/47658e88f01a43d5b520242152262ddb.jpeg
---
主要介绍Java面向对象编程相关知识，涉及面向对象与面向过程的区别，详细阐述面向对象编程中类和对象的使用。
<!--more-->
## 学习思维导图
![](/images/java1/java11.jpg)
![](/images/java1/java12.jpg)

### 3.1 面向对象与面向过程
##### 面向对象(OOP)与面向过程(POP)
* 二者都是一种思想，面向对象是相对于面向过程而言的。面向过程，强调的是功能行为。面向对象，将功能封装进对象，强调具备了功能的对象。
* 面向对象更加强调运用人类在日常的思维逻辑中采用的思想方法与原则，如抽象、分类、继承、聚合、多态等。
##### 面向对象的三大特征
* **封装  (Encapsulation)**
* **继承  (Inheritance)**
* **多态  (Polymorphism)**

    OOP: Object Oriented Programming  
    面向过程：procedure oriented programming

---

### java类及类的成员


* 现实世界万事万物是由分子、原子构成的。同理，Java代码世界是由诸多个不同功能的类构成的。

* 现实世界中的分子、原子又是由什么构成的呢？原子核、电子！那么，Java中用类class来描述事物也是如此

     - 属 性：对应类中的成员变量
     - 行 为：对应类中的成员方法

* **Field = 属性 = 成员变量，Method =  (成员)方法 = 函数**


---

### 面向对象的思想概述

![](/images/java4/java41.PNG)
- 可以理解为：类 = 汽车设计图；对象 = 实实在在的汽车
- 面向对象程序设计的重点是类的设计
- 定义类其实是定义类中的成员(成员变量和成员方法)

#### 1.java类及类的成员
![](/images/java4/java42.PNG)

---

### 类的语法格式
```
修饰符 class  类名 {
	属性声明;
	方法声明;
}
```
* 说明：
    - 修饰符public：类可以被任意访问
	- 类的正文要用{  }括起来

举例：

	public class  Person{
    public int age ;	            //声明公有变量 age
    public void showAge() { //声明方法showAge( )
	 System.out.println(age);
      }
    }


#### 创建Java自定义类
步骤：

    1.定义类（考虑修饰符、类名）
    2.编写类的属性（考虑修饰符、属性类型、属性名、初始化值）
    3.编写类的方法（考虑修饰符、返回值类型、方法名、形参等）
练习：

定义Person、Animal等类，加以体会。

---

### 3.5 对象的创建和使用

* java类及类的成员(如何使用Java类)

* java类的实例化，即创建类的对象

    - 使用new +构造器创建一个新的对象；
    - 使用“对象名.对象成员”的方式访问对象成员（包括属性和方法）；


     public class Animal  {
     public int legs;   
     public void  eat(){
     System.out.println(“ Eating.”);
     }
     public viod move(){
      System.out.println(“Move.”);
      }    
    }



举例:

    public class Zoo{
    public static void main(String args[]){
	Animal xb=new Animal();
	xb.legs=4;
	System.out.println(xb.legs);
	xb.eat();
	xb.move();
     }
    }


### 3.3 类的成员之一：属性

* 语法格式：

    修饰符  类型  属性名 =初值 ;

      说明:修饰符private:该属性只能由该类的方法访问。
	        修饰符public:该属性可以被该类以外的方法访问。    
                    类型：任何基本类型，如int、boolean或任何类。
* 举例：

      public class Person{
           private int age;             //声明private变量 age
           public String name = “Lila”;    //声明public变 量 name
        }


#### 补：变量的分类：成员变量与局部变量
* 在方法体外，类体内声明的变量称为成员变量。
* 在方法体内部声明的变量称为局部变量。

![](/images/java4/java44.PNG)

#### 成员变量（属性）和局部变量的区别？
* 成员变量：

       - 成员变量定义在类中，在整个类中都可以被访问。
       - 成员变量分为类成员变量和实例成员变量，实例变量存在于对象所在的堆内存中。
       - 成员变量有默认初始化值。
       - 成员变量的权限修饰符可以根据需要，选择任意一个

局部变量：

       - 局部变量只定义在局部范围内，如：方法内，代码块内等。
       - 局部变量存在于栈内存中。
       - 作用的范围结束，变量空间会自动释放。
       - 局部变量没有默认初始化值，每次必须显式初始化。
       - 局部变量声明时不指定权限修饰符

---

### 3.4  类的成员之二：方  法

语法格式：

 	修饰符  返回值类型  方法名 ( 参数列表) {
  	 方法体语句；
    }

说明：
* 修饰符：public, private, protected等。
* 返回值类型：return语句传递返回值。没有返回值：void。
*
举例：

     	public class Person{
        private int age;
       public int getAge()   { return age; } //声明方法getAge
       public void setAge(int i) {          //声明方法setAge
	  age = i;        //将参数i的值赋给类的成员变量age
         }
       }


#### 对象的创建和使用

* 如果创建了一个类的多个对象，对于类中定义的属性，每个对象都拥有各自的一套副本，且互不干扰。


举例:

    public class Zoo{
    public static void main(String args[]){
	Animal xb=new Animal();
	Animal xh=new Animal();
	xb.legs=4;
	xh.legs=0;
	System.out.println(xb.legs);   //4
	System.out.println(xh.legs);   //0
	xb.legs=2;
	System.out.println(xb.legs);   //2
	System.out.println(xh.legs);   //0
    }  }

练  习 1
编写教师类和学生类，并通过测试类创建对象进行测试

---

### 3.6 方法(method)

* 什么是方法（函数）？

      方法是类或对象行为特征的抽象，也称为函数。
      Java里的方法不能独立存在，所有的方法必须定义在类里。                  

         修饰符 返回值类型 方法名（参数类型 形参1，参数类型 形参2，….）｛
         程序代码
         return 返回值;
         ｝


其中：

    - 形式参数：在方法被调用时用于接收外部传入的数据的变量。
    - 参数类型：就是该形式参数的数据类型。
    - 返回值：方法在执行完毕后返还给调用它的程序的数据。
    - 返回值类型：方法要返回的结果的数据类型。
    - 实参：调用方法时实际传给函数形式参数的数据。

* 如何理解方法返回值类型为void的情况 ?

#### 方法的调用
* 方法只有被调用才会被执行
* 方法调用的过程分析
![](/imagges/java4/java45.PNG)

#### 方法的调用

##### 注  意：

- 没有具体返回值的情况，返回值类型用关键字void表示，那么该函数中的return语句如果在最后一行可以省略不写。

- **定义方法时，方法的结果应该返回给调用者，交由调用者处理。**

- **方法中只能调用方法，不可以在方法内部定义方法。**

#### 对象的产生

* 当一个对象被创建时，会对其中各种类型的成员变量自动进行初始化赋值。除           了基本数据类型之外的变量类型都是引用类型，如上面的Person及前面讲过的数组。

成员变量类型|初始值
---|---
byte|0
short|0
int|0
long|0L
float|0.0F
double|0.0D
char|'\u0000'(表示为空)
boolean|false
引用类型|null

#### 匿名对象
* 我们也可以不定义对象的句柄，而直接调用这个对象的方法。这样的对象叫做匿名对象。

        如：new Person().shout();

* 使用情况

        如果对一个对象只需要进行一次方法调用，那么就可以使用匿名对象。
      我们经常将匿名对象作为实参传递给一个方法调用。

练习2
1.创建一个Person类，其定义如下：

     Person
     name:String
     age:int
     sex:int
     study():void
     showAge():void
     addAge(int i):int

要求：(1)创建Person类的对象，设置该对象的name、age和sex属性，调用study方法，输出字符串“studying”，调用showAge()方法显示age值，调用addAge()方法给对象的age属性值增加2岁。
(2)创建第二个对象，执行上述操作，体会同一个类的不同对象之间的关系。

2.利用面向对象的编程方法，设计类Circle计算圆的面积。

#### 提 示

##### 类的访问机制：

* **在一个类中的访问机制：类中的方法可以直接访问类中的成员变量。（例外：static方法访问非static的成员变量，编译不通过。）**

* **在不同类中的访问机制：先创建要访问类的对象，再用对象访问类中定义的成员。**

#### 面向对象思想“落地”法则(一)
     1.关注于类的设计，即设计类的成员：属性 、方法
    2.类的实例化，即创建类的对象（比如：Person p = new Person()）
    3.通过“对象.属性” 、 “对象.方法” 执行

---

### 方法的重载(overload)
##### 重载的概念
在同一个类中，允许存在一个以上的同名方法，只要它们的参数个数或者参数类型不同即可。
##### 重载的特点：
与返回值类型无关，只看参数列表，且参数列表必须不同。(参数个数或参数类型)。调用时，根据方法参数列表的不同来区别。
##### 重载示例：


    //返回两个整数的和
    int add(int x,int  y){return x+y;}
    //返回三个整数的和
    int add(int x,int y,int z){return x+y+z;}
    //返回两个小数的和
    double add(double x,double y){return x+y;}


#### 函数的重载


    public class PrintStream{
    public static void print(int i) {……}
    public static void print(float f) {……}
    private static void print(String s) {……}
	 public static void main(String[] args){
		print(3)；
		print(1.2f)；
		 print(“hello!”)；  
    	}
     }

##### 练习3
1.判 断：

      与void show(int a,char b,double c){}构成重载的有：
        1.void show(int x,char y,double z){}   //no
        2.int show(int a,double c,char b){}   //yes顺序不同也是重载
      c)  void show(int a,double c,char b){}  //yes顺序不同也是重载
      d)  boolean show(int c,char b){}  //yes
      e)  void show(double c){}  //yes
      f)  double show(int x,char y,double z){}  //no
      g)  void shows(){double c}  //no

2.编写程序，定义三个重载方法并调用。方法名为mOL。
三个方法分别接收一个int参数、两个int参数、一个字符串参数。分别执行平方运算并输出结果，相乘并输出结果，输出字符串信息。
在主类的main ()方法中分别用参数区别调用三个方法。

3.定义三个重载方法max()，第一个方法求两个int值中的最大值，第二个方法求两个double值中的最大值，第三个方法求三个double值中的最大值，并分别调用三个方法。

#### 体会可变个数的形参


    //下面采用数组形参来定义方法
    public static void test(int a ,String[] books);
    //以可变个数形参来定义方法
    public static void test(int a ,String…books);

##### 说明：

    1.可变参数：方法参数部分指定类型的参数个数是可变多个
    2.声明方式：方法名（参数的类型名...参数名）
    3.可变参数方法的使用与方法参数部分使用数组是一致的
    4.方法的参数部分有可变形参，需要放在形参声明的最后

例子：

     public void  test(String[] msg){
  	 System.out.println(“含字符串数组参数的test方法 ");
     }
     public void test1(String book){
	 System.out.println(“****与可变形参方法构成重载的test1方法****");
     }
     public void test1(String ... books){
	 System.out.println("****形参长度可变的test1方法****");
      }
    public static void main(String[] args){
	TestOverload to = new TestOverload();
	//下面两次调用将执行第二个test方法
	to.test1();
	to.test1("aa" , "bb");
	//下面将执行第一个test方法
	to.test(new String[]{"aa"});
     }


---

### 方法的参数传递

* 方法，必须有其所在类或对象调用才有意义。若方法含有参数：
   - 形参：方法声明时的参数
   - 实参：方法调用时实际传给形参的参数值

* Java的实参值如何传入方法呢？
    - Java里方法的参数传递方式只有一种：值传递。  即将实际参数值的副本（复制品）传入方法内，


    public class TestTransfer {
	public static void swap(int a , int b){
		int tmp = a;
		a = b;
		b = tmp;
		System.out.println("swap方法里，a的值是"
			+ a + "；b的值是" + b);
	}
	public static void main(String[] args) {
		int a = 6;
		int b = 9;
		swap(a , b);
		System.out.println("交换结束后，变量a的值是"
			+ a + "；变量b的值是" + b);

	}  }



    class DataSwap{
	public int a;
	public int b;
    }
    public class TestTransfer1 {
	public static void swap(DataSwap ds){
		int tmp = ds.a;
		ds.a = ds.b;
		ds.b = tmp;
		System.out.println("swap方法里，a Field的值是"
			+ ds.a + "；b Field的值是" + ds.b);
	}
	public static void main(String[] args) {
		DataSwap ds = new DataSwap();
		ds.a = 6;
		ds.b = 9;
		swap(ds);
		System.out.println("交换结束后，a Field的值是"
			+ ds.a + "；b Field的值是" + ds.b);
     	}
    }


##### 再体会参数的传递

    class BirthDate{
	private int day;
	private int month;
	private int year;
	public BirthDate(int d,int m,int y){
		day = d; month = m; year = y;}
	public void setDay(int d){day = d;}
	public void setMonth(int m){month = m;}
	public void setYear(int y){year = y;}
	public int getDay(){return day;}
	public int getMonth(){return month;}
	public int getYear(){return year;}
	public void display(){
		System.out.println(day+"-"+month+"-"+year);}
     }




    public class Test {
	public void change1(int i){
		i = 1234;}
	public void change2(BirthDate b){
		b = new BirthDate(22,3,2004);}
	public void change3(BirthDate b){
		b.setDay(22);}
	public static void main(String[] args) {
		Test test = new Test();
		int date = 9;
		BirthDate d1 = new BirthDate(7,7,1970);
		BirthDate d2 = new BirthDate(1,1,2009);
		test.change1(date);
		test.change2(d1);
		test.change3(d2);
		System.out.println("date="+date);
		d1.display();
		d2.display();
	}	}


### 3.7面向对象特征之一：封装和隐藏

* **使用者对类内部定义的属性(对象的成员变量)的直接操作会导致数据的错误、混乱或安全性问题。**

       public class Animal {
	   public int legs;	    
	   public void  eat(){
		System.out.println(“Eating.”);
    	 }
	   public void move(){
		System.out.println(“Moving.”);
        }
       }


      public class Zoo{
	   public static void main(String args[]){
		 Animal xb=new Animal();
		 xb.legs=4;
		 System.out.println(xb.legs);
	           xb.eat();xb.move();
       }  }


* **应该将legs属性保护起来，防止乱用。
保护的方式：信息隐藏**
* 问题：xb.legs = -1000;

#### 信息的封装和隐藏

* Java中通过将数据声明为私有的(private)，再提供公共的（public）方法:getXxx()和setXxx()实现对该属性的操作，以实现下述目的：
     - 隐藏一个类中不需要对外提供的实现细节；
     - 使用者只能通过事先定制好的方法来访问数据，可以方便地加入控制逻辑，限制对属性的不合理操作；
     - 便于修改，增强代码的可维护性；


    public class Animal{
	private int legs;//将属性legs定义为private，只能被Animal类内部访问
	public void setLegs(int i){  //在这里定义方法 eat() 和 move()
		if (i != 0 && i != 2 && i != 4){
		     System.out.println("Wrong number of legs!");
		     return;
		}
		legs=i;
	}
	public int getLegs(){
		return legs;
	}  }


    public class Zoo{
	public static void main(String args[]){
		Animal xb=new Animal();
		xb.setLegs(4);	  //xb.setLegs(-1000);       
        		 xb.legs=-1000;	  //非法
		System.out.println(xb.getLegs());
    }  }


#### 四种访问权限修饰符
* **Java权限修饰符public、protected、private置于类的成员定义前，用来限定对象对该类成员的访问权限。**

修饰符|类内部|同一个包|子类|任何地方
---|---|---|---|---
private|Yes
（缺省）|Yes|Yes
protected|Yes|Yes|Yes
public|Yes|Yes|Yes|Yes

* 对于class的权限修饰只可以用public和default(缺省)。

    - public类可以在任意地方被访问。
    - default类只可以被同一个包内部的类访问。\

![](/images/java4/java43.PNG)

###### 练习4

1.创建程序,在其中定义两个类：Person和TestPerson类。定义如下：
    用setAge()设置人的合法年龄(0~130)，用getAge()返回人的年龄。在TestPerson类中实例化Person类的对象b，调用setAge()和getAge()方法，体会Java的封装性。

Person|*
---|---
age:int|-
setAge(i: int)|-
getAge(): int|-

---

### 3.8  类的成员之三：构造器(构造方法)
* 构造器的特征
    - 它具有与类相同的名称
    - 它不声明返回值类型。（与声明为void不同）
    - 不能被static、final、synchronized、abstract、native修饰，不能有return语句返回值

* 构造器的作用：创建对象；给对象进行初始化
    - 如：Order o = new Order();    Person p = new Person(Peter,15);
    - 如同我们规定每个“人”一出生就必须先洗澡，我们就可以在“人”的构造方法中加入完成“洗澡”的程序代码，于是每个“人”一出生就会自动完成“洗澡”，程序就不必再在每个人刚出生时一个一个地告诉他们要“洗澡”了。

#### 构造器
*语法格式：

     修饰符  类名 (参数列表) {
	    初始化语句；
     }


* 举 例：

      public class Animal {
      private int legs;
      public Animal()  {legs = 4; }	   //构造器
      public void setLegs(int i) { legs = i; }
      public int     getLegs(){return legs;}
      }
       创建Animal类的实例 ：Animal  a=new Animal();    
       /调用构造器，将legs初始化为4。


#### 构造器

* 根据参数不同，构造器可以分为如下两类：
    - 隐式无参构造器（系统默认提供）
    - 显式定义一个或多个构造器（无参、有参）

* 注  意：
    - Java语言中，每个类都至少有一个构造器
    - 默认构造器的修饰符与所属类的修饰符一致
    - 一旦显式定义了构造器，则系统不再提供默认构造器
    - 一个类可以创建多个重载的构造器
    - 父类的构造器不可被子类继承

##### 练习5
1. 在前面定义的Person类中添加构造器，利用构造器设置所有人的age属性初始值都为18。

2. 修改上题中类和构造器，增加name属性,使得每次创建Person对象的同时初始化对象的age属性值和name属性值。

Person|*
---|---
name:String|-
setName(i: String)|-
getName(): String|-

3.定义一个“点”（Point）类用来表示三维空间中的点（有三个坐标）。要求如下：
    1）可以生成具有特定坐标的点对象。
    2）提供可以设置三个坐标的方法。
4.编写两个类，TriAngle和TestTriAngle，其中TriAngle中声明私有的底边长base和高height，同时声明公共方法访问私有变量；另一个类中使用这些公共方法，计算三角形的面积。

#### 构造器重载

* 构造器一般用来创建对象的同时初始化对象。如


     class Person{
    	String name;
    	int age;
    	public Person(String n , int a){  name=n; age=a;}
       }

* 构造器重载使得对象的创建更加灵活，方便创建各种不同的对象。

构造器重载举例：

    public class Person{
    public Person(String name, int age, Date d) {this(name,age);…}
    public Person(String name, int age) {…}
    public Person(String name, Date d) {…}
    public Person(){…}
     }


* 构造器重载，参数列表必须不同
##### 构造器重载举例

      public class Person {
      private String name;
      private int age;
      private Date birthDate;
      public Person(String name, int age, Date d) {
 	  this.name = name;
    	this.age = age;
    	this.birthDate = d;
     }
      public Person(String name, int age) {
    	this(name, age, null);    
	 //this.name=name; this.age=age; this.birthDate=null;
     }
     public Person(String name, Date d) {
 	 this(name, 30, d);	   	
	 //this.name=name; this.age=30; this.birthDate=d;
     }
     public Person(String name) {
	 this(name, 30);	   //this.name=name; this.age=30;
        }
      }


##### 练习6

    (1)定义Person类,有4个属性：String name; int age; String school;  
      String major
    (2)定义Person类的3个构造方法:
第一个构造方法Person(String n, int            a)设置类的name和age属性；
第二个构造方法Person(String n, int a, String s)设置类的name, age 和school属性；
第三个构造方法Person(String n, int a, String s, String m)设置类的name, age ,school和major属性；
(3)在main方法中分别调用不同的构造方法创建的对象，并输出其属性值。

---

### 3.9  关键字—this
##### this是什么？
* 在java中，this关键字比较难理解，它的作用和其词义很接近。
     - 它在方法内部使用，即这个方法所属对象的引用；
     - 它在构造器内部使用，表示该构造器正在初始化的对象。
* this表示当前对象，可以调用类的属性、方法和构造器
* 什么时候使用this关键字呢？
     - 当在方法内需要用到调用该方法的对象时，就用this。

#### 使用this，调用属性、方法

    class Person{		// 定义Person类
	private String name ;
	private int age ;			
	public Person(String name,int age){
		this.name = name ;   
		this.age = age ;  }
	public void getInfo(){
		System.out.println("姓名：" + name) ;
		this.speak();
	}
	public void speak(){
		System.out.println(“年龄：” + this.age);
	}
}


* **1.当形参与成员变量重名时，如果在方法内部需要使用成员变量，必须添加this来表明该变量时类成员**

* **2.在任意方法内，如果使用当前类的成员变量或成员方法可以在其前面添加this，增强程序的阅读性**

##### 使用this调用本类的构造器

    class Person{		// 定义Person类
	private String name ;		
	private int age ;			
	public Person(){	  // 无参构造
		System.out.println("新对象实例化") ;
	}
	public Person(String name){
		this();      // 调用本类中的无参构造方法
		this.name = name ;
	}
	public Person(String name,int age){
		this(name) ;  // 调用有一个参数的构造方法
		this.age = age;
	}
	public String getInfo(){
		return "姓名：" + name + "，年龄：" + age ;
	}  }



* **3.this可以作为一个类中，构造器相互调用的特殊格式**
##### 注意：

* 1.使用this()必须放在构造器的首行！

* 2.使用this调用本类中其他的构造器，保证至少有一个构造器是不用this的。

      class Person{  // 定义Person类
    	String name;
    	Person(String name){
		this.name = name;}
	  public void getInfo(){
		System.out.println("Person类 --> " + this.name) ; }
    	public boolean compare(Person p){
		return this.name==p.name;
    	}  }
       public class TestPerson{
    	public static void main(String args[]){
		Person per1 = new Person("张三") ;
		Person per2 = new Person("李四") ;
		per1.getInfo() ;	// 当前调用getInfo()方法的对象是per1
		per2.getInfo() ;	// 当前调用getInfo()方法的对象是per2
		boolean b = per1.compare(per2);
    	}  }

* 当前正在操作本方法的对象称为当前对象。
*
##### 练习7

添加必要的构造器，综合应用构造器的重载，this关键字。

Girl|*                          
---|---
name:String|-
setName(i: String)|-
getName(): String|-
marry(boy:Boy)|-


Boy|*
---|---
name:String|-
age:int|-
setName(i: String)|-
getName(): String|-
setAge(i: int)|-
getAge(): int|-
marry(girl:Girl)|-
shout():void|-

---

### JavaBean
* **JavaBean是一种Java语言写成的可重用组件。**

* **所谓javaBean，是指符合如下标准的Java类：**

      类是公共的
      有一个无参的公共的构造器
      有属性，且有对应的get、set方法

* **用户可以使用JavaBean将功能、处理、值、数据库访问和其他任何可以用java代码创造的对象进行打包，并且其他的开发者可以通过内部的JSP页面、Servlet、其他JavaBean、applet程序或者应用来使用这些对象。用户可以认为JavaBean提供了一种随时随地的复制和粘贴的功能，而不用关心任何改变。**

##### JavaBean示例

     public class TestJavaBean{
      private String name;  //属性一般定义为private
      private int age;
      public  TestJavaBean(){}
      public int getAge(){
             return age;
      }
      public void setAge(int age){
             this.age = age;
      }
      public String getName(){
            return name;
      }
      public void setName(String name){
            this.name = name;
}


---

### 关键字—package
源文件布局：
![](/images/java4/java46.PNG)
#### 软件包：
* 包帮助管理大型软件系统：将语义近似的类组织到包中；解决类命名冲突的问题。
* 包可以包含类和子包。
* 例：某航运软件系统包括：一组域对象、GUI和reports子系统
![](/images/java4/java47.PNG)

#### 关键字—package
* package语句作为Java源文件的第一条语句，指明该文件中定义的类所在的包。(若缺省该语句，则指定为无名包)。它的格式为：  
**package 顶层包名.子包名 ;**

举例：

	pack\Test.java
		package p1;    //指定类Test属于包p1
		public class Test{
		        public void display(){
			System.out.println("in  method display()");
		        }
		}


* 包对应于文件系统的目录，package语句中，用 “.” 来指明包(目录)的层次；
* 包通常用小写单词，类名首字母通常大写。

#### 关键字—import
* 为使用定义在不同包中的Java类，需用import语句来引入指定包层次下所需要的类或全部类(.*)。import语句告诉编译器到哪里去寻找类。
* 语法格式：

	import  包名[.子包名…]. <类名 |*>

* 应用举例：

    	import  p1.Test;   //import p1.*;表示引入p1包中的所有类
    	public class TestPackage{
		public static void main(String args[]){
		          Test t = new Test();          //Test类在p1包中定义
		          t.display();
		}
      }


#### import语句
* 注意：

    - 若引入的包为：java.lang，则编译器默认可获取此包下的类，不需要再显示声明。
    - import语句出现在package语句之后、类定义之前
    - 一个源文件中可包含多个import语句
    - 可以使用import lee.* ;语句，表明导入lee包下的所有类。而lee包下sub子包内的类则不会被导入。import lee.sub.*;
    - import语句不是必需的，可坚持在类里使用其它类的全名
    - JDK 1.5加入import static语句

#### JDK中主要的包介绍
    1.java.lang----包含一些Java语言的核心类，如String、Math、Integer、
                              System和Thread，提供常用功能。
    2.    java.net----包含执行与网络相关的操作的类和接口。
    3.    java.io   ----包含能提供多种输入/输出功能的类。
    4.  java.util----包含一些实用工具类，如定义系统特性、接口的集合框架类、
                            使用与日期日历相关的函数。
    5.     java.text----包含了一些java格式化相关的类
    6.     java.sql----包含了java进行JDBC数据库编程的相关类/接口
    7.     java.awt----包含了构成抽象窗口工具集（abstract window toolkits）的
                             多个类，这些类被用来构建和管理应用程序的图形用户界  
                             面(GUI)。
    8.     java.applet----包含applet运行所需的一些类。
