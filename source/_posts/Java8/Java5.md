---
title: Java高级类特性
date: 2020/2/8 20:12:13
layout: java5
permalink: java5.html
cover: http://5b0988e595225.cdn.sohucs.com/images/20190418/47658e88f01a43d5b520242152262ddb.jpeg
---
类（class）是构造对象的模板或蓝图，由类构造（construct)对象的过程称为创建类的实例（instance）
<!--more-->
## 学习思维导图
![](/images/java1/java11.jpg)
![](/images/java1/java12.jpg)

### 4.1  面向对象特征之二：继承

* 为描述和处理个人信息，定义类Person:

Person|*
---|---
name : String|- 
age : int|-
+getInfo() : String|-


      public class Person {
      public String name;
      public int age;
      public String getInfo()   
       {...}
       }

#### 继  承(1) 
*  为描述和处理学生信息，定义类Student:

Student|*
---|---
name : String |-
age : int|-
school : String|-
getInfo() : String|-


      public class Student {
      public String name;
      public int age;
      public String school;

      public String getInfo()  
     {...}
     }


![](/images/java5/java51.PNG)
![](/images/java5/java52.PNG)

#### 继  承(2) 

* 通过继承，简化Student类的定义:

Person|*
---|---
+name : String|- 
age : int|-
birthDate : Date|-
getInfo() : String|-

Student|*
---|---
school : String|-


      public class Person {
      public String name;
      public int age;
      public String getInfo() {...}
       }

      public class Student extends Person{
      public String school;
       }
       
* **Student类继承了父类Person的所有属性和方法，并增加了一个属性school。Person中的属性和方法,Student都可以利用。**

#### 继  承(3) 

* 为什么要有继承？
    - 多个类中存在相同属性和行为时，将这些内容抽取到单独一个类中，那么多个类无需再定义这些属性和行为，只要继承那个类即可。

* 此处的多个类称为子类，单独的这个类称为父类（基类或超类）。可以理解为:“子类 is a 父类”

* 类继承语法规则:
   - class Subclass extends Superclass{ }
   
   
#### 继  承(4) 

![](/images/java5/java53.PNG)

* 作用：
    - 继承的出现提高了代码的复用性。
    - 继承的出现让类与类之间产生了关系，提供了多态的前提。
    - 不要仅为了获取其他类中某个功能而去继承

#### 类的继承 (5)

* 子类继承了父类，就继承了父类的方法和属性。
* 在子类中，可以使用父类中定义的方法和属性，也可以创建新的数据和方法。
* 在Java 中，继承的关键字用的是“extends”，即子类不是父类的子集，而是对父类的“扩展”。
##### 关于继承的规则：

子类不能直接访问父类中私有的(private)的成员变量和方法。
！[](/images/java5/java54.PNG)

#### 类的继承 (6)

* Java只支持单继承，不允许多重继承
   - 一个子类只能有一个父类
   - 一个父类可以派生出多个子类
   

      class SubDemo extends Demo{ }   //ok
      class SubDemo extends Demo1,Demo2...//error

![](/images/java5/java55.PNG)
![](/images/java5/java56.PNG)
##### 单继承举例
![](/images/java5/java57.PNG)



1.(1)定义一个ManKind类，包括
成员变量int sex和int salary；
方法void manOrWorman()：根据sex的值显示“man”(sex==1)或者“women”(sex==0)；
方法void employeed()：根据salary的值显示“no job”(salary==0)或者“ job”(salary!=0)。
   (2)定义类Kids继承ManKind，并包括
成员变量int yearsOld；
方法printAge()打印yearsOld的值。
   (3)在Kids类的main方法中实例化Kids的对象someKid，用该对象访问其父类的成员变量及方法。

      /*
      *这是一个描述成员的类
      */
      public class ManKind {
      int sex;  //性别
      int salary;  //薪酬


    //这是一个打印输出性别的方法
    public void manOrWorman(){
        if (sex==1){
            System.out.println("man");
        }else {
            System.out.println("women");
        }

    }
    //这是一个打印输出是否有工作的方法
    public void employeed(){
        if (salary==0){
            System.out.println("no job");
        }else {
            System.out.println("job");
        }
       }
     }
     
      /**
      * 这是一个继承ManKind的子类
      */
      public class Kids extends ManKind {

      int yearsOld; //年龄
      public static void main(String[] args) {

        Kids somekid = new Kids();//实例化Kids的对象someKid
        somekid.yearsOld= 12;
        somekid.sex=1;
        somekid.salary=0;

        somekid.manOrWorman();  //访问父类manOrWorman方法
        somekid.printAge();  // 访问printAge方法
        somekid.employeed();// 访问父类employeed方法



    }
     ////这是一个打印输出年龄的方法
    public void printAge(){

        System.out.println("年龄为"+yearsOld);//
       }
     }

---

### 4.2  方法的重写(override)
* 定义：在子类中可以根据需要对从父类中继承来的方法进行改造，也称方法的重置、覆盖。在程序执行时，子类的方法将覆盖父类的方法。
* 要求：
    - 重写方法必须和被重写方法具有相同的方法名称、参数列表和返回值类型。
    - 重写方法不能使用比被重写方法更严格的访问权限。
    - 重写和被重写的方法须同时为static的，或同时为非static的
    - 子类方法抛出的异常不能大于父类被重写方法的异常

##### 重写方法举例(1)

     public class Person {
            public String name;
            public int age;
            public String getInfo() {
	        return "Name: "+ name + "\n" +"age: "+ age;
             }
          }
    public class Student extends Person {
            public String school;
            public String getInfo() {       //重写方法
  	      return  "Name: "+ name + "\nage: "+ age 
	          + "\nschool: "+ school;
             }
            public static void main(String args[]){
	       Student s1=new Student();
	       s1.name="Bob";
	       s1.age=20;
	       s1.school="school2";
	       System.out.println(s1.getInfo());   //Name:Bob  age:20  school:school2
            }
         }

* Person p1=new Person();
p1.getInfo();
   - //调用Person类的getInfo()方法
* Student s1=new Student();
s1.getInfo();
   - //调用Student类的getInfo()方法
   -  这是一种“多态性”：同名的方法，用不同的对象来区分调用的是哪一个方法。

##### 重写方法举例(2)

    class Parent {
	public void method1() {}
    }

    class Child extends Parent {
	private void method1() {}  
    //非法，子类中的method1()的访问权限private比被覆盖方法的访问权限public弱
    }

    public class UseBoth {
	public static void main(String[] args) {
		Parent p1 = new Parent();
		Child p2 = new Child();
		p1.method1();
		p2.method1();
     	}
    }

---

### 4.3 四种访问权限修饰符

**Java权限修饰符public、protected、private置于类的成员定义前，用来限定对象对该类对象成员的访问权限。**

修饰符|类内部|同一个包|子类|任何地方
---|---|---|---|---|---
private|Yes
default(缺省)|Yes|Yse
protected|Yes|Yse|Yes
public|Yes|Yse|Yes|Yes

* **对于class的权限修饰只可以用public和default。**
   - **public类可以在任意地方被访问。**
   -  **default类只可以被同一个包内部的类访问。**

#### 访问控制举例

    class Parent{
        private int f1 = 1;
        int f2 = 2;
        protected  int f3 = 3;
        public  int f4 = 4;
        private  void  fm1() {System.out.println("in fm1() f1=" + f1);}
        void fm2() {System.out.println("in fm2() f2=" + f2);}
        protected  void  fm3() {System.out.println("in fm3() f3=" + f3);}
        public void fm4() {System.out.println("in fm4() f4=" + f4);}	
     }
    
    
     class Child extends Parent{               //设父类和子类在同一个包内
    	private int c1 = 21;
    	public  int c2 = 22;	 
	private void cm1(){System.out.println("in cm1() c1=" + c1);}
	public  void cm2(){System.out.println("in cm2() c2=" + c2);}
	public static void main(String args[]){
		int i; 
		Parent  p = new Parent();		
		i = p.f2;	        //	i = p.f3;		i = p.f4;				p.fm2();         //	p.fm3();	p.fm4();		
		Child  c = new Child();
		i = c.f2;	        //	i = c.f3;		i = c.f4;		
		i = c.c1;	        //	i = c.c2;		
		c.cm1();        // c.cm2();    c.fm2();   c.fm3();   c.fm4()
     	}
     }

#### 访问控制分析

父类Parent和子类Child在同一包中定义时：

子类对象可以访问的数据|子类的对象可以调用的方法
---|---
f2_default|fm2()_default
f3_protected|fm3()_ protected
f4_public|fm4()_ public
c1_private|cm1()_private
c2_public|cm2()_public

---

### 4.4  关键字super

* 在Java类中使用super来调用父类中的指定操作：
    - super可用于访问父类中定义的属性
    - super可用于调用父类中定义的成员方法
    - super可用于在子类构造方法中调用父类的构造器
* 注意：
    - 尤其当子父类出现同名成员时，可以用super进行区分
    - super的追溯不仅限于直接父类
    - super和this的用法相像，this代表本类对象的引用，super代表父类的内存空间的标识

#### 关键字super举例

    class Person {
	protected String name="张三";
             protected int age;
	public String getInfo() {
                     return "Name: " + name + "\nage: " + age;
    	} }
    class Student extends Person {
             protected String name = "李四";
	private String school = "New Oriental";
	public String getSchool(){ return school; }
    	public String getInfo() {
        		return super.getInfo() +"\nschool: " +school;
    	} }
    public class TestStudent{
	public static void main(String[] args){
		Student st = new Student();
		System.out.println(st.getInfo());
	} }

#### 调用父类的构造器

* 子类中所有的构造器默认都会访问父类中空参数的构造器
* 当父类中没有空参数的构造器时，子类的构造器必须通过this(参数列表)或者super(参数列表)语句指定调用本类或者父类中相应的构造器，且必须放在构造器的第一行
* 如果子类构造器中既未显式调用父类或本类的构造器，且父类中又没有无参的构造器，则编译出错

#### 调用父类构造器举例 

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
 	}
 	public Person(String name, Date d) {
 	        this(name, 30, d);
	 }
 	 public Person(String name) {
 	        this(name, 30);
    	}
    	// ……
     }

#### 调用父类构造器举例 

   public class Student extends Person {
 	private String school;

             public Student(String name, int age, String s) {
 	          super(name, age);
 	          school = s;
             }
 	public Student(String name, String s) {
 	          super(name);
	          school = s;
 	}
 	public Student(String s) { // 编译出错: no super(),系统将调用父类  
                                                          无参数的构造方法。
 	          school = s;
 	}
  }
  
#### this和super的区别
No.|区别点|this|super
---|---|---|---
1|访问属性|访问本类中的属性，如果本类没有此属性则从父类中继续查找|访问父类中的属性
2|调用方法|访问本类的方法|直接访问父类中的方法
3||调用构造器|调用本类构造器，必须放在构造器首行|调用父类构造器，必须放在子类构造器的首行
4|特殊|表示当前对象|无此概念



#### 4.5简单类对象的实例化过程

！[](/images/java5/java58.PNG)

#### 4.5子类对象的实例化过程

! [](/images/java5/java59.PNG)

#### 4.6  面向对象特征之三：多态性

* 多态性，是面向对象中最重要的概念，在java中有两种体现：
   - 方法的重载(overload)和重写(overwrite)。
   - 对象的多态性   ——可以直接应用在抽象类和接口上。

* Java引用变量有两个类型：编译时类型和运行时类型。编译时类型由声明该变量时使用的类型决定，运行时类型由实际赋给该变量的对象决定。
    - 若编译时类型和运行时类型不一致，就出现多态（Polymorphism）

#### 多态性(2)

* 对象的多态—在Java中,子类的对象可以替代父类的对象使用
    - 一个变量只能有一种确定的数据类型
    - 一个引用类型变量可能指向(引用)多种不同类型的对象
	Person p = new Person();
	Person e = new Student(); // Person类型的变量e，指向Student类型的对象

* **子类可看做是特殊的父类，所以父类类型的引用可以指向子类的对象：向上转型(upcasting)。**

#### 多态性(3)

* 一个引用类型变量如果声明为父类的类型，但实际引用的是子类对象，那么该变量就不能再访问子类中添加的属性和方法

	  Student m = new Student();
	  m.school = “pku”; 	  //合法,Student类有school成员变量
	  Person e = new Student(); 
	  e.school = “pku”;	//非法,Person类没有school成员变量
      属性是在编译时确定的，编译时e为Person类型，没有school成员变量，因而编译错误。

#### 虚拟方法调用(Virtual Method Invocation)

 * 正常的方法调用
 
    	Person p = new Person();
  	    p.getInfo();
    	Student s = new Student();
   	    s.getInfo();

 * 虚拟方法调用(多态情况下)
 
    	Person e = new Student();
    	e.getInfo();	//调用Student类的getInfo()方法

 * 编译时类型和运行时类型
编译时e为Person类型，而方法的调用是在运行时确定的，所以调用的是Student类的getInfo()方法。——动态绑定

#### 多态小结

* 前提：

   - 需要存在继承或者实现关系
   - 要有覆盖操作

* 成员方法：
   - 编译时：要查看引用变量所属的类中是否有所调用的方法。
   - 运行时：调用实际对象所属的类中的重写方法。
   
* 成员变量：
   - 不具备多态性，只看引用变量所属的类。
   
* 子类继承父类
   - 若子类重写了父类方法，就意味着子类里定义的方法彻底覆盖了父类里的同名方法，系统将不可能把父类里的方法转移到子类中
   - 对于实例变量则不存在这样的现象，即使子类里定义了与父类完全相同的实例变量，这个实例变量依然不可能覆盖父类中定义的实例变量

#### 多态性应用举例

* 方法声明的形参类型为父类类型，可以使用子类的对象作为实参调用该方法

      public class Test{ 
	  public void method(Person e) {
	           //……
	           e.getInfo();
	   }
	  public static  void main(Stirng args[]){
	           Test t = new Test();
	            Student m = new Student();
	            t.method(m); //子类的对象m传送给父类类型的参数e
	       }
        }

#### 多态性应用举例

* 方法声明的形参类型为父类类型，可以使用子类的对象作为实参调用该方法

      public class Test{ 
 	  public void method(Person e) {
	           //……
	           e.getInfo();
     	}
	  public static  void main(Stirng args[]){
	           Test t = new Test();
	            Student m = new Student();
	            t.method(m); //子类的对象m传送给父类类型的参数e
       	}
      }


---

### instanceof 操作符

* x instanceof A：检验x是否为类A的对象，返回值为boolean型。

    - 要求x所属的类与类A必须是子类和父类的关系，否则编译错误。
    - 如果x属于类A的子类B，x instanceof  A值也为true。
    
    
     public class Person extends Object {…}
     public class Student extends Person {…}
     public class Graduate extends Person {…}
     -------------------------------------------------------------------
     public void method1(Person e) {
  	if (e instanceof Person) 
		// 处理Person类及其子类对象
	if (e instanceof Student) 
		//处理Student类及其子类对象
	if (e instanceof Graduate)
		//处理Graduate类及其子类对象
      }

---

### 4.7  Object 类

* Object类是所有Java类的根父类
* 如果在类的声明中未使用extends关键字指明其父类，则默认父类为Object类 

	  public class Person {
	  ...
	  }
	  等价于：
      public class Person extends Object {
      ...
      }

* 例：method(Object obj){…}//可以接收任何类作为其参数

       Person o=new Person();  
       method(o);


#### Object类中的主要方法

NO.|方法名称|类型|描述
---|---|---|---
1|public Objext()|构造|构造方法
2|public boolean equals（Object obj）|普通|对象比较
3|public int hashCodes（）|普通|取得Hash码
4|public String toString（）|普通|对象打印时调用

#### 对象类型转换 (Casting )

* 基本数据类型的Casting：

    - 自动类型转换：小的数据类型可以自动转换成大的数据类型
	      如long g=20;           double d=12.0f
    - 强制类型转换：可以把大的数据类型强制转换(casting)成小的数据类型
            如 float f=(float)12.0;   int a=(int)1200L

* **对Java对象的强制类型转换称为造型**

    - **从子类到父类的类型转换可以自动进行**
    - **从父类到子类的类型转换必须通过造型(强制类型转换)实现**
    - **无继承关系的引用类型间的转换是非法的**

#### 对象类型转换举例

     public class ConversionTest{
	 public static void main(String[] args) {
		double d = 13.4;
		long l = (long)d;
		System.out.println(l);
		int in = 5;
		//boolean b = (boolean)in;
		Object obj = "Hello";
		String objStr = (String)obj;
		System.out.println(objStr);
		Object objPri = new Integer(5);
		//所以下面代码运行时引发ClassCastException异常
		String str = (String)objPri;
     	}
     }

#### 对象类型转换举例

     public class Test{ 
	           public void method(Person e) {	 //设Person类中没有getschool()						方法
		 // System.out.pritnln(e.getschool());   //非法,编译时错误
		 
		  if(e  instanceof  Student){
		          Student me = (Student)e;	//将e强制转换为Student类型
		          System.out.pritnln(me.getschool());
		  }	    
	   }
	    public static  void main(Stirng args[]){
	           Test t = new Test();
	            Student m = new Student();
	            t.method(m);
	       }
       }


! [](/images/java5/java510.PNG)

#### ==操作符与equals方法

* = =： 
    - 基本类型比较值:只要两个变量的值相等，即为true.
	int a=5; if(a==6){…}
    - 引用类型比较引用(是否指向同一个对象):只有指向同一个对象时，==才返回true.
    
		 Person p1=new Person();   
	      Person p2=new Person();
	       if (p1==p2){…}

     - 用“==”进行比较时，符号两边的数据类型必须兼容(可自动转换的基本数据类型除外)，否则编译出错；

* equals()：所有类都继承了Object，也就获得了equals()方法。还可以重写。
    - 只能比较引用类型，其作用与“==”相同,比较是否指向同一个对象。	 
    - 格式:obj1.equals(obj2)
* 特例：当用equals()方法进行比较时，对类File、String、Date及包装类（Wrapper Class）来说，是比较类型及内容而不考虑引用的是否是同一个对象；
    - 原因：在这些类中重写了Object类的equals()方法。

#### toString() 方法

* toString()方法在Object类中定义，其返回值是String类型，返回类名和它的引用地址。
* 在进行String与其它类型数据的连接操作时，自动调用toString()方法
	Date now=new Date();
	System.out.println(“now=”+now);  相当于
      System.out.println(“now=”+now.toString());   
* 可以根据需要在用户自定义类型中重写toString()方法
	如String 类重写了toString()方法，返回字符串的值。
	s1=“hello”;
	System.out.println(s1);//相当于System.out.println(s1.toString());
* 基本类型数据转换为String类型时，调用了对应包装类的toString()方法
    - int a=10;   System.out.println(“a=”+a);

#### 4.7  包装类(Wrapper)

* 针对八种基本定义相应的引用类型—包装类（封装类）
* 有了类的特点，就可以调用类中的方法。

基本数据类型|包装类
---|---
boolean|Boolean
byte|Byte
short|Short
int|Integer
long|Long
char|Character
float|Float
double|Double

* 基本数据类型包装成包装类的实例    ---装箱
    - 通过包装类的构造器实现：
	int i = 500;   Integer t = new Integer(i);
    - 还可以通过字符串参数构造包装类对象：
	Float f = new Float(“4.56”);
	Long l = new Long(“asdf”);  //NumberFormatException
* 获得包装类对象中包装的基本类型变量    ---拆箱
调用包装类的.xxxValue()方法：
	boolean b = bObj.booleanValue();
* JDK1.5之后，支持自动装箱，自动拆箱。但类型必须匹配。

* 字符串转换成基本数据类型
    - 通过包装类的构造器实现：
	int i = new Integer(“12”);
    - 通过包装类的parseXxx(String s)静态方法：
	Float f = Float.parseFloat(“12.1”);

* 基本数据类型转换成字符串
    - 调用字符串重载的valueOf()方法：
	String fstr = String.valueOf(2.34f);
    - 更直接的方式：
	String intStr = 5 + “”

#### 包装类用法举例

int i = 500;
Integer t = new Integer(i);

* 装箱：包装类使得一个基本数据类型的数据变成了类。
有了类的特点，可以调用类中的方法。

String s = t.toString(); // s = “500“,t是类，有toString方法
String s1 = Integer.toString(314); // s1= “314“  将数字转换成字符串。
String s2=“4.56”;
double ds=Double.parseDouble(s2);   //将字符串转换成数字

#### 包装类的用法举例

* 拆箱：将数字包装类中内容变为基本数据类型。

int j = t.intValue();	// j = 500，intValue取出包装类中的数据


* 包装类在实际开发中用的最多的在于字符串变为基本数据类型。

String str1 = "30" ;
String str2 = "30.3" ;	
int x = Integer.parseInt(str1) ;	// 将字符串变为int型
float f = Float.parseFloat(str2) ; // 将字符串变为int型

---

### 5.1  关键字static

* 当我们编写一个类时，其实就是在描述其对象的属性和行为，而并没有产生实质上的对象，只有通过new关键字才会产生出对象，这时系统才会分配内存空间给对象，其方法才可以供外部调用。我们有时候希望无论是否产生了对象或无论产生了多少对象的情况下，某些特定的数据在内存空间里只有一份，例如所有的中国人都有个国家名称，每一个中国人都共享这个国家名称，不必在每一个中国人的实例对象中都单独分配一个用于代表国家名称的变量。

！[](/images/java5/java511.PNG)

     class Circle{
		private double radius;
		public Circle(double radius){this.radius=radius;}
		public double findArea(){return Math.PI*radius*radius;}}
		
* 创建两个Circle对象

        Circle c1=new Circle(2.0);	//c1.radius=2.0
        Circle c2=new Circle(3.0);	//c2.radius=3.0
        
* Circle类中的变量radius是一个实例变量(instance variable)，它属于类的每一个对象，不能被同一个类的不同对象所共享。
* 上例中c1的radius独立于c2的radius，存储在不同的空间。c1中的radius变化不会影响c2的radius，反之亦然。
* **如果想让一个类的所有实例共享数据，就用类变量！**

#### 类属性、类方法的设计思想

* 类属性作为该类各个对象之间共享的变量。在设计类时,分析哪些类属性不因对象的不同而改变，将这些属性设置为类属性。相应的方法设置为类方法。

* **如果方法与调用者无关，则这样的方法通常被声明为类方法，由于不需要创建对象就可以调用类方法，从而简化了方法的调用**

#### 关键字static

* 使用范围：
    - 在Java类中，可用static修饰属性、方法、代码块、内部类

* 被修饰后的成员具备以下特点：
    - 随着类的加载而加载
    - 优先于对象存在
    - 修饰的成员，被所有对象所共享
    - 访问权限允许时，可不创建对象，直接被类调用


     class Circle {
     private double radius;
     public static String name = "这是一个圆";
     public static String getName(){
     return name;}
     public Circle(double radius) {
     getName();
     this.radius = radius;}
     public double findArea() {
     return Math.PI * radius * radius;}
     public void display(){
     System.out.println("name:"+name+"radius:"+radius);
     }}
     
     public class TestStatic {
     public static void main(String[] args) {
     Circle c1 = new Circle(2.0);
     Circle c2 = new Circle(3.0);
     c1.display();
     c2.display();
       }
      }

#### 类变量(class Variable)

* 类变量（类属性）由该类的所有实例共享

！[](/images/java5/java512.PNG)

       public class Person {
       private int id;
       public static int total = 0;
       public Person() {
 	   total++;
 	   id = total;
       }
      }
      
#### 类变量应用举例

       class Person {
           private int id;
           public static int total = 0;
           public Person() {
 	         total++;
 	         id = total;
           }
           public static void main(String args[]){
         	Person Tom=new Person();
	   Tom.id=0;
	   total=100; // 不用创建对象就可以访问静态成员
            }
        }

       public class OtherClass {
            public static void main(String args[]) {
 	         Person.total = 100;  // 不用创建对象就可以访问静态成员
                           //访问方式：类名.类属性，类名.类方法
	         System.out.println(Person.total);
	         Person c = new Person(); 
	         System.out.println(c.total);	//输出101
            }}

#### 类方法(class Method) 

* 没有对象的实例时，可以用类名.方法名()的形式访问由static标记的类方法。
* 在static方法内部只能访问类的static属性，不能访问类的非static属性。

       class Person {
       private int id;
       private static int total = 0;
       public static int getTotalPerson() { 
	   id++;	//非法
	   return total;
       }
       public Person() {
         	total++;
 	   id = total;
       }}
       public class TestPerson {
        public static void main(String[] args) {
 	   System.out.println("Number of total is " +Person.getTotalPerson());
     	//没有创建对象也可以访问静态方法
 	   Person p1 = new Person();
     	System.out.println( "Number of total is "+ Person.getTotalPerson());
        }}

---

### 单例 (Singleton)设计模式

* 设计模式是在大量的实践中总结和理论化之后优选的代码结构、编程风格、以及解决问题的思考方式。设计模式就像是经典的棋谱，不同的棋局，我们用不同的棋谱，免去我们自己再思考和摸索。
* 所谓类的单例设计模式，就是采取一定的方法保证在整个的软件系统中，对某个类只能存在一个对象实例，并且该类只提供一个取得其对象实例的方法。如果我们要让类在一个虚拟机中只能产生一个对象，我们首先必须将类的构造方法的访问权限设置为private，这样，就不能用new操作符在类的外部产生类的对象了，但在类内部仍可以产生该类的对象。因为在类的外部开始还无法得到类的对象，只能调用该类的某个静态方法以返回类内部创建的对象，静态方法只能访问类中的静态成员变量，所以，指向类内部产生的该类对象的变量也必须定义成静态的。

#### 单例(Singleton)设计模式-饿汉式

     class Single{
 	//private的构造器，不能在类的外部创建该类的对象
     private Single() {} 
	 //私有的，只能在类的内部访问
     private static Single onlyone = new Single();
 	//getSingle()为static，不用创建对象即可访问
     public static Single getSingle() {
		return onlyone;
 	   }
     }
     public class TestSingle{
	 public static void main(String args[]) {		
		Single  s1 = Single.getSingle();      //访问静态方法
		Single  s2 = Single.getSingle();
		if (s1==s2){
			System.out.println("s1 is equals to s2!");
		}}}

#### 单例(Singleton)设计模式-懒汉式

    class Singleton{
	//1.将构造器私有化，保证在此类的外部，不能调用本类的构造器。
	private Singleton(){
	}
	//2.先声明类的引用
	//4.也需要配合static的方法，用static修饰此类的引用。
	private static Singleton  instance = null;
	//3.设置公共的方法来访问类的实例
	public static Singleton  getInstance(){
	//3.1如果类的实例未创建，那些先要创建，然后返回给调用者：本类。因此，需要static 修饰。
		if(instance == null){
			instance = new Singleton();
		}
	//3.2 若有了类的实例，直接返回给调用者。
		return instance;
	}  }

* 举例：java.lang.Runtime

！[](/images/java5/java513.PNG)

---

###5.2  理解main方法的语法 
* 由于java虚拟机需要调用类的main()方法，所以该方法的访问权限必须是public，又因为java虚拟机在执行main()方法时不必创建对象，所以该方法必须是static的，该方法接收一个String类型的数组参数，该数组中保存执行java命令时传递给所运行的类的参数。 

！[](/images/java5/java514.PNG)

#### 命令行参数用法举例

     public class CommandPara {
       public static void main(String[] args) {
 	 for ( int i = 0; i < args.length; i++ ) {
    	       System.out.println("args[" + i + "] = " + args[i]);
	    }  } }
      //运行程序CommandPara.java
      java CommandPara "lisa"  "bily"  "Mr Brown"

      输出结果：

      args[0] = lisa
      args[1] = bily
      args[2] = Mr Brown

#### 5.3  类的成员之四：初始化块

！[](/images/java5/java515.PNG)

* 初始化块(代码块)作用：
     - 对Java对象进行初始化

* 程序的执行顺序：
声明成员变量的默认值
	

显式初始化、多个初始化块依次被执行（同级别下按先后顺序执行）
	

构造器再对成员进行赋值操作

#### 5.3  类的成员之四：初始化块

* 一个类中初始化块若有修饰符，则只能被static修饰，称为静态代码块(static block )，当类被载入时，类属性的声明和静态代码块先后顺序被执行，且只被执行一次。

* **static块通常用于初始化static (类)属性**

      class Person {
	  public static int total;
	  static {
	        total = 100;//为total赋初值 
     	}
	   …… //其它属性或方法声明
       }

#### 5.3  类的成员之四：初始化块

* 非静态代码块：没有static修饰的代码块

       1.可以有输出语句。
       2.可以对类的属性声明进行初始化操作。
       3.可以调用静态和非静态的变量或方法。
       4.若有多个非静态的代码块，那么按照从上到下的顺序依
           次执行。
       5.每次创建对象的时候，都会执行一次。且先于构造器执行

* 静态代码块：用static 修饰的代码块

       1.可以有输出语句。
       2.可以对类的属性声明进行初始化操作。
       3.不可以对非静态的属性初始化。即：不可以调用非静态的属
         性和方法。
       4.若有多个静态的代码块，那么按照从上到下的顺序依次执行。
       5.静态代码块的执行要先于非静态代码块。
       6.静态代码块只执行一次


#### 初始化块举例

！[](/images/java5/java516.PNG)
！[](/images/java5/java517.PNG)

#### 5.4  关键字：final

* 在Java中声明类、属性和方法时，可使用关键字final来修饰,表示“最终”。
    - final标记的类不能被继承。提高安全性，提高程序的可读性。 
String类、System类、StringBuffer类
    - final标记的方法不能被子类重写。
Object类中的getClass()。
    - final标记的变量(成员变量或局部变量)即称为常量。名称大写，且只能被赋值一次。
    - final标记的成员变量必须在声明的同时或在每个构造方法中或代码块中显式赋值，然后才能使用。
    final double PI=3.14;

#### 1.final修饰类

     final class A{
     }
     class B extends A{     //错误，不能被继承。
     }
     **Final修饰的类不能被继承**

#### 2.final修饰方法

     class A{
       public final void print(){
                System.out.println(“A”);
       }
      }
      class B extends A{     
        public void print(){   //错误，不能被重写。
                  System.out.println(“众软”);
         }
       }

* **Final修饰的方法不能被子类重写**

#### 3.final修饰变量——常量

     class  A{
        private final String INFO = “众软”;  //声明常量
        public void print(){
                  //INFO = “众软”;
         }
      }
      
* **常量名要大写，内容不可修改。**
* static final：全局常量

#### 关键字final应用举例

       public final class Test{
		public static int totalNumber = 5 ;
		public final int ID;
		public Test(){
			ID = ++totalNumber;  //可在构造方法中给final变量赋值
		}
   		public static void main(String[] args) {
			Test t = new Test();
			System.out.println(t.ID);		
			final int I = 10;
			final int J;
			J = 20;
			J = 30;  //非法
    		}}

#### 5.5  抽象类(abstract class)

* 随着继承层次中一个个新子类的定义，类变得越来越具体，而父类则更一般，更通用。类的设计应该保证父类和子类能够共享特征。有时将一个父类设计得非常抽象，以至于它没有具体的实例，这样的类叫做抽象类。

！[](/images/java5/java518.PNG)

* 用abstract关键字来修饰一个类时，这个类叫做抽象类；
* 用abstract来修饰一个方法时，该方法叫做抽象方法。
     - 抽象方法：只有方法的声明，没有方法的实现。以分号结束：abstract int abstractMethod( int a );
* 含有抽象方法的类必须被声明为抽象类。
* 抽象类不能被实例化。抽象类是用来作为父类被继承的，抽象类的子类必须重写父类的抽象方法，并提供方法体。若没有重写全部的抽象方法，仍为抽象类。
* 不能用abstract修饰属性、私有方法、构造器、静态方法、final的方法

#### 抽象类举例
 
       abstract class A{   
       abstract void m1( );
       public void m2( ){
	    System.out.println("A类中定义的m2方法");
       }
       }

      class B extends A{
       void m1( ){
	     System.out.println("B类中定义的m1方法");
       }
       }

       public class Test{
       public static void main( String args[ ] ){
	     A a = new B( );
	     a.m1( );
	     a.m2( );
          }
        }

#### 抽象类应用

抽象类是用来模型化那些父类无法确定全部实现，而是由其子类提供具体实现的对象的类

！[](/images/java5/java519.PNG)

* 在航运公司系统中，Vehicle类需要定义两个方法分别计算运输工具的燃料效率和行驶距离
* 
问题：卡车(Truck)和驳船(RiverBarge)的燃料效率和行驶距离的计算方法完全不同。Vehicle类不能提供计算方法，但子类可以。

#### 抽象类应用

* 解决方案
	Java允许类设计者指定：超类声明一个方法但不提供实现，该方法的实现由子类提供。这样的方法称为抽象方法。有一个或更多抽象方法的类称为抽象类。
* Vehicle是一个抽象类，有两个抽象方法。

      public abstract class Vehicle{
	  public abstract double   calcFuelEfficiency();	    //计算燃料效率的抽象方法
	  public abstract double  calcTripDistance();	 //计算行驶距离的抽象方法
       }
       public class Truck extends Vehicle{
	    public double calcFuelEfficiency( )   { //写出计算卡车的燃料效率的具体方法   }
  	    public double calcTripDistance( )    {  //写出计算卡车行驶距离的具体方法   }
      }

        public class RiverBarge extends Vehicle{
	    public double calcFuelEfficiency( ) { //写出计算驳船的燃料效率的具体方法  }
	     public double calcTripDistance( )  {  //写出计算驳船行驶距离的具体方法}
         }

* **注意：抽象类不能实例化   new Vihicle()是非法的**

问题1：为什么抽象类不可以使用final关键字声明？

  （抽象类不能被实例化。抽象类是用来被继承的，抽象类的子类必须重写父类的抽象方法，并提供方法体）
  
问题2：一个抽象类中可以定义构造器吗？

抽象类可以有构造方法，只是不能直接创建抽象类的实例对象而已。
抽象类不能实例化   new Vihicle()是非法的

#### 模板方法设计模式(TemplateMethod)

* 抽象类体现的就是一种模板模式的设计，抽象类作为多个子类的通用模板，子类在抽象类的基础上进行扩展、改造，但子类总体上会保留抽象类的行为方式。

* **解决的问题：**

     - 当功能内部一部分实现是确定，一部分实现是不确定的。这时可以把不确定的部分暴露出去，让子类去实现。
     - 编写一个抽象父类，父类提供了多个子类的通用方法，并把一个或多个方法留给其子类实现，就是一种模板模式。


       abstract class Template{
	   public final void getTime(){
		long start = System.currentTimeMillis();
		code();
		long end = System.currentTimeMillis();
		System.out.println("执行时间是："+(end - start));
	    }
    	public abstract void code();
       }
       class SubTemplate extends Template{
	  public void code(){
		for(int i = 0;i<10000;i++){
		System.out.println(i);
      } } }

---

### 5.6 接 口

* 有时必须从几个类中派生出一个子类，继承它们所有的属性和方法。但是，Java不支持多重继承。有了接口，就可以得到多重继承的效果。
* 接口(interface)是抽象方法和常量值的定义的集合。
* 从本质上讲，接口是一种特殊的抽象类，这种抽象类中只包含常量和方法的定义，而没有变量和方法的实现。
* 实现接口类：
class SubClass implements InterfaceA{ }
* 一个类可以实现多个接口，接口也可以继承其它接口。

* 接口的特点：

    - 用interface来定义。
    - 接口中的所有成员变量都默认是由public static final修饰的。
    - 接口中的所有方法都默认是由public abstract修饰的。
    - 接口没有构造器。
    - 接口采用多层继承机制。
    
*接口定义举例

       public interface Runner {
	   int ID = 1;
	   void start();
     	public void run();
	  void stop();
       }


* 实现接口的类中必须提供接口中所有方法的具体实现内容，方可实例化。否则，仍为抽象类。

* 接口的主要用途就是被实现类实现。（面向接口编程）

* 与继承关系类似，接口与实现类之间存在多态性

* 定义Java类的语法格式：先写extends，后写implements

   	  < modifier> class < name> [extends < superclass>]
	   [implements < interface> [,< interface>]* ] {
		< declarations>*
	   }

！[](/images/java5/java520.PNG)

！[](/images/java5/java521.PNG)

！[](/images/java5/java522.PNG)

！[](/images/java5/java523.PNG)

#### 接口应用举例(1)

！[](/images/java5/java524.PNG)

#### 接口应用举例(2)

 * 一个类可以实现多个无关的接口

       interface Runner { public void run();}
       interface Swimmer {public double swim();}
       class Creator{public int eat(){…}} 
       class Man extends Creator implements Runner ,Swimmer{
		public void run() {……}
		public double swim()  {……}
		public int eat() {……}
       }
       
* 与继承关系类似，接口与实现类之间存在多态性

       public class Test{
       	public static void main(String args[]){
		Test t = new Test();
		Man m = new Man();
		t.m1(m);
		t.m2(m);
		t.m3(m);
       	}
       	public String m1(Runner f) { f.run(); }
       	public void  m2(Swimmer s) {s.swim();}
       	public void  m3(Creator a) {a.eat();}
       }

#### 接口的其他问题

* 如果实现接口的类中没有实现接口中的全部方法，必须将此类定义为抽象类 
* 接口也可以继承另一个接口，使用extends关键字。

        interface MyInterface{
		String s=“MyInterface”;
		public void absM1();
	    }
	   interface SubInterface extends MyInterface{
		public void absM2();
	    }
  	    public class SubAdapter implements SubInterface{
		public void absM1(){System.out.println(“absM1”);}
		public void absM2(){System.out.println(“absM2”);}
        }
      
* 实现类SubAdapter必须给出接口SubInterface以及父接口MyInterface中所有方法的实现。


---

#### 工厂方法(FactoryMethod)

* **FactoryMethod模式是设计模式中应用最为广泛的模式，在面向对象的编程中，对象的创建工作非常简单，对象的创建时机却很重要。FactoryMethod解决的就是这个问题，它通过面向对象的手法，将所要创建的具体对象的创建工作延迟到了子类，从而提供了一种扩展的策略，较好的解决了这种紧耦合的关系。**

#### 工厂方法举例

！[](/images/java5/java525.PNG)

---

### 5.7  类的成员之五：内部类

* 在Java中，允许一个类的定义位于另一个类的内部，前者称为内部类，后者称为外部类。
* Inner class一般用在定义它的类或语句块之内，在外部引用它时必须给出完整的名称。
    - Inner class的名字不能与包含它的类名相同；
* Inner class可以使用外部类的私有数据，因为它是外部类的成员，同一个类的成员之间可相互访问。而外部类要访问内部类中的成员需要:内部类.成员或者内部类对象.成员。
* 分类：成员内部类（static成员内部类和非static成员内部类）
	     局部内部类（不谈修饰符）、匿名内部类

#### 内部类举例 (1)

      class A {
	 private int s;
	 public class B{
	        public void mb() {
		s = 100;     
		System.out.println("在内部类B中s=" + s);
	        }  }
	  public void ma() {
		B i = new B();
		i.mb();
	   }  }

       public class Test {	
	   public static void main(String args[]){
	        A o = new A();
	        o.ma();
     	}   } 

#### 内部类特性

* Inner class作为类的成员：
    - 可以声明为final的
    - 和外部类不同，Inner class可声明为private或protected；
    - Inner class 可以声明为static的，但此时就不能再使用外层类的非static的成员变量；
* Inner class作为类：
    - 可以声明为abstract类 ，因此可以被其它的内部类继承
    
**【注意】非static的内部类中的成员不能声明为static的，只有在外部类或static的内部类中才可声明static成员。**

#### 匿名内部类

* 匿名内部类不能定义任何静态成员、方法和类，只能创建匿名内部类的一个实例。一个匿名内部类一定是在new的后面，用其隐含实现一个接口或实现一个类。

       new 父类构造器（实参列表）|实现接口(){
        //匿名内部类的类体部分
       }


       interface  A{
	   public  abstract void fun1();
         }
       public class Outer{
	    public static void main(String[] args) {
		new Outer().callInner(new A(){
               //接口是不能new但此处比较特殊是子类对象实现接口，只不过没有为对象取名
			public void fun1() {
				System.out.println(“implement for fun1");
			}
		   });// 两步写成一步了
	       }
	     public void callInner(A a) {
		a.fun1();
	       }
         }  

---

###面向对象内容总结

！[](/images/java5/java526.PNG)