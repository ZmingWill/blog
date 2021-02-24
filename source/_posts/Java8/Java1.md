---
title: 从入门到入土Day1-Java程序设计概述
date: 2020/2/1 21:20:25
layout: java1
permalink: java1.html
cover:  http://5b0988e595225.cdn.sohucs.com/images/20190418/47658e88f01a43d5b520242152262ddb.jpeg
---
就发展前景而言，Java的地位是独一无二的。它是一种完全可信赖的程序设计语言，并被广泛认可。
<!--more-->
### 学习思维导图
![](/images/java1/java11.jpg)
![](/images/java1/java12.jpg)
#### 常用DOS命令
> dir: 列出当前目录下的文件以及文件夹

> md:创建目录

> rd：删除目录

> cd:进入指定目录

> cd..：返回上一1 级目录

> del:删除文件

> exit：退出dos命令行

### 1.1 Java语言概述
##### 计算机语言
> 计算机语言：人与计算机交流交互的方式，如：c,c++,Java,python，PHP等。

##### 第一代语言
>打孔机--纯机器语言

##### 第二代语言
> 汇编语言

#### 第三代语言
> C，Pascal，Fortran：面向过程的语言

> C++:面向过程/面向对象

> Java:跨平台的纯面向对象的语言(面向对象能够更好的在抽象的层面来分析问题，在程序实现可以极大的复用之前的代码)

> NET:跨语言的平台

---

#### 小结
> Java语言确实是从C语言和C++语言继承了许多成分，甚至可以将Java看成是类C语言发展和衍生的产物。比如Java语言的变量声明，操作符形式，参数传递，流程控制等方面和C语言，C++语言完全相同。但同时，Java语言是一个纯粹的面向对象的程序设计语言，它继承了C++语言面向对象技术的核心，Java语言舍弃了C语言中容易引起错误的指针（以接口取代），运算符重载（operator overloading)，多重继承（以接口取代）等特性，增加了垃圾回收器功能用于回收不再被引用的对象所占据的内存空间。JDK1.5有引入了泛型编程(Generic Programming)，类型安全的枚举，不定长参数和自动装/拆箱

---

### Java语言的主要特征

##### Java语言是易学的;
> Java语言的语法与C语言和C++语言很接近，使得大多数程序员很容易学习和使用java。
##### Java语言是强制面向对象的;
> Java语言提供类，接口和继承等原语，为了简单起见，只支持类之间的单继承，但支持接口之间的多继承，并支持类与接口之间的实现机制(关键字为implements)。
##### Java语言是分布式的;
> Java语言支持Internet应用的开发，在基本的Java应用编程接口中有一个网络应用编程接口(java net),它提供了用于网络应用编程的类库，包括URL，URLConnection，Socket，ServerSocket等。java的RMI(远程方法激活)机制也是开发分布式应用的重要手段。
##### java语言是健壮的;
> Java的强类型机制，异常处理，垃圾的自动收集等是Java程序健壮性的重要保证。对指针的丢弃是Java的明智选择。
##### Java语言是安全的;
> Java通常被用在网络环境中，为此，java提供了一个安全机制以防止恶意代码的攻击。如：安全防范机制（类ClassLoader）。如分配不同的名字空间以防替代本地的同名类,字节代码检查。
##### Java语言是体系结构中立的;
> Java程序（后缀为java的文件）在Java平台上被编译为体系结构中立的字节码格式（后缀为class的文件），然后可以在实现这个Java平台的任何系统中运行。
##### Java语言是解释型的;
> 如前所述，Java程序在Java平台上被编译为字节码格式，然后可以在实现这个Java平台的任何系统的解释器中运行。
##### Java语言是可移植的。
> 你可以处理文件，正则表达式，xml，日期和时间，数据库，网络连接，线程等，而不用担心操作底层操作系统。Java API往往也比原生API质量更高。
##### Java是性能略高（高性能）的;
> 与那些解释型的高级脚本语言相比，Java的性能还是较优的。
##### Java语言是原生支持多线程的。
> 在Java语言中，线程是一种特殊的对象，它必须由Thread类或其子（孙）类来创建。

##  1.2 Java语言主要概述
![](/images/java1/java13.jpg)
### Java在各领域中的应用
#### 从Java的应用领域来分，Java语言的应用方向主要表现在以下几个方面：
#### •企业级应用：
主要指复杂的大企业的软件系统、各种类型的网站。Java的安全机制以及它的跨平台的优势，使它在分布式系统领域开发中有广泛应用。应用领域包括金融、电信、交通、电子商务等。
#### •Android平台应用：
Android应用程序使用Java语言编写。Android开发水平的高低很大程度上取决于Java语言核心能力是否扎实。
#### •移动领域应用:
主要表现在消费和嵌入式领域，是指在各种小型设备上的应用，包括手机、PDA、机顶盒、汽车通信设备等。

## 1.3  Java语言运行机制及运行过程
#### 特点一：面向对象   女朋友才叫对象
#### •两个基本概念：类、对象
#### •三大特性：封装、继承、多态
#### 特点二：健壮性 完善性
吸收了C/C++语言的优点，但去掉了其影响程序健壮性的部分（如指针、内存的申请与释放等），提供了一个相对安全的内存管理和访问机制
#### 特点三：跨平台性  jvm
跨平台性：通过Java语言编写的应用程序在不同的系统平台上都可以运行。“Write once , Run Anywhere”，一次编写，处处运行
原理：只要在需要运行 java 应用程序的操作系统上，先安装一个Java虚拟机 (JVM Java Virtual Machine) 即可。由JVM来负责Java程序在该系统中的运行。
#### Java两种核心机制
•Java虚拟机（Java Virtal Machine），JVM
•垃圾收集机制（Garbage Collection），GC

![](/images/java1/java14.jpg)
#### 核心机制—Java虚拟机
•JVM是一个虚拟的计算机，具有指令集并使用不同的存储区域。负责执行指令，管理数据、内存、寄存器。
•对于不同的平台，有不同的虚拟机。
•Java虚拟机机制屏蔽了底层运行平台的差别，实现了“一次编译，到处运行。

![](/images/java1/java15.jpg)
#### 核心机制—垃圾回收
•不再使用的内存空间应回收—— 垃圾回收。
•在C/C++等语言中，由程序员负责回收无用内存。
•Java 语言消除了程序员回收无用内存空间的责任：它提供一种系统级线程跟踪存储空间的分配情况。并在JVM空闲时，检查并释放那些可被释放的存储空间。
•垃圾回收在Java程序运行过程中自动进行，程序员无法精确控制和干预。

## 1.4Java语言的环境搭建
### 下载，安装JDK
官方网址：
https://www.oracle.com/technetwork/java/javase/downloads/index.html

###### 安装JDK
傻瓜式安装，下一步即可。
建议：安装路径不要有中文或者特殊符号如空格等。
当提示安装 JRE 时，可以选择不安装。
![](/images/java1/java16.jpg)
![](/images/java1/java17.jpg)


## 1.5 开发体验 — HelloWorld
#### 步骤：
•1.将 Java 代码编写到扩展名为 .java 的文件中。
•2.通过 javac 命令对该 java 文件进行编译。
•3.通过 java 命令对生成的 class 文件进行运行。
![](/images/java1/java18.jpg)

#### 步骤一：编写
•选择最简单的编辑器：记事本。
•敲入代码    class Test{  }
•将文件保存成Test.java，这个文件是存放java代码的文件，称为源文件。

![](/images/java1/java19.jpg)

#### 步骤二：编译
•有了java源文件，通过编译器将其编译成JVM可以识别的字节码文件。
•在该源文件目录下，通过javac编译工具对Test.java文件进行编译。
•如果程序没有错误，没有任何提示，但在当前目录下会出现一个Test.class文件，该文件称为字节码文件，也是可以执行的java的程序。
![](/images/java1/java110.jpg)

#### 步骤三：运行
•有了可执行的java程序(Test.class字节码文件)
•通过运行工具java.exe对字节码文件进行执行。
•出现提示：缺少一个名称为main的方法。
![](/images/java1/java111.jpg)

•因为一个程序的执行需要一个起始点或者入口，所以在Test类中的加入public static void main(String[] args){  }
•对修改后的Test.java源文件需要重新编译，生成新的class文件后，再进行执行。
•发现没有编译失败，但也没有任何效果，因为并没有告诉JVM要帮我们做什么事情，也就是没有可以具体执行的语句。
•想要和JVM来个互动，只要在main方法中加入一句
System.out.println(“Hello World");因为程序进行改动，所以再重新编译，运行即可。
![](/images/java1/java112.jpg)


## 1.6 小结第一个程序

#### •Java源文件以“java”为扩展名。源文件的基本组成部分是类（class），如本类中的Test类。
#### •Java应用程序的执行入口是main()方法。它有固定的书写格式：public static void main(String[] args)  {...}
#### •Java语言严格区分大小写。
#### •Java方法由一条条语句构成，每个语句以“;”结束。
#### •括号都是成对出现的，缺一不可。

## 1.7 常见问题及解决方法
![](/images/java1/java113.jpg)
•源文件名不存在或者写错，或者当前路径错误。
![](/images/java1/java114.jpg)
•类文件名写错，或者类文件不在当前路径下，或者不在classpath指定路径下。
![](/images/java1/java115.jpg)
•声明为public的主类应与文件名一致，否知编译失败。
![](/images/java1/java116.jpg)
•编译失败，注意错误出现的行数，再到源代码中指定位置改错。


## 1.8 注  释

#### •用于注解说明解释程序的文字就是注释。
#### •提高了代码的阅读性；调试程序的重要方法。

#### Java中的注释类型：
•单行注释   //
•多行注释/* */
•文档注释（java特有）

* 注释是一个程序员必须要具有的良好编程习惯。
* 将自己的思想通过注释先整理出来，再用代码去体现

#### 单行注释
格式： //注释文字
#### 多行注释
格式：   /*  注释文字 */
注：
对于单行和多行注释，被注释的文字，不会被JVM（java虚拟机）解释执行。
多行注释里面不允许有多行注释嵌套。

#### 文档注释（java特有）
格式：/**
       * @author  指定java程序的作者
     *@version  指定源文件的版本
              *@param   方法的参数说明信息
              */
注释内容可以被JDK提供的工具 javadoc 所解析，生成一套以网页文件形式体现的该程序的说明文档。

---

### 总结

 ##### 面向对象，人的对象，人的运动的动作，运动的器械这三个对象，

 ##### 面向对象能够更好的在抽象的层面来分析问题，在程序实现跨越极大的赋予之前的代码,这些是面向过程编程很难实现的

 ##### c，c++，由程序员回收，手动编写代码回收（优点：能够在内存不使用时快速回收，准确高效；缺点：容易失误出现bug，例如忘记编写回收内存的代码？内存一直不回收）

 ##### java，垃圾回收是自动，开了一个收集线程自动去检测哪些内存不用了然后回收掉（优点：自动的，意味着不会出现忘记回收；缺点：回收不及时）

 ##### 一般的观点是，宁可回收不及时但是一定要回收，使用自动的垃圾回收恒合适

 ##### 就是使用压缩版的jdk,可以方便项目的更替

---

#### 程序清单  

* Welcome/welcome.java


     /**
     *这个程序显示问候语
     * 这是一个打印Welcome to Core Java的类
     * @version 1.30 2020-02-1
     * @author yzxh
     */
     public class Welcome
     {
     public static void main(String[] args)
      {
      String greeting = "Welcome to Core Java!";
      System.out.println(greeting);
      for (int i = 0; i < greeting.length(); i++)
         System.out.print("=");
      System.out.println();
       }
     }

* ImageViewer/ImageVuiewer.java

      import java.awt.*;
      import java.io.*;
      import javax.swing.*;
      /**
      *这个程序用于查看图像
      * @version 1.30 2020-02-1
      * @author yzxh
      */
      public class ImageViewer {
	  public static void main(String[] args) {
		EventQueue.invokeLater(()-> {
			var frame = new ImageViewerFrame();
			frame.setTitle("图像浏览器");
			frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		    frame.setVisible(true);
		});

	   }

      }
      /**
      *  带有显示图像的标签的框架
      */
      class ImageViewerFrame extends JFrame{
	  public static final int DEFAULT_WTDTH=300;//默认宽度  
 	  public static final int DEFAULT_HEIGHT=400;//默认高度

	  public ImageViewerFrame() {
		setSize(DEFAULT_WTDTH, DEFAULT_HEIGHT);

	  //使用标签来显示图像
		var label = new JLabel();
		add(label);

      //设置文件选择器
		var chooser = new JFileChooser();
		chooser.setCurrentDirectory(new File("."));

	  //设置菜单栏
		var menuBar = new JMenuBar();
		setJMenuBar(menuBar);

	    var menu = new JMenu("文件");
	    menuBar.add(menu);

	    var openItem = new JMenuItem("打开");
	    menu.add(openItem);
	    openItem.addActionListener(event ->{
	    	//显示文件选择器对话框
	    	int result = chooser.showOpenDialog(null);

	    	//如果文件被选中，将其设置为标签的图标
	    	if (result == JFileChooser.APPROVE_OPTION) {

	    	   String name = chooser.getSelectedFile().getPath();
	    	   label.setIcon(new ImageIcon(name));
	        }
	    });

	    var exitItem = new JMenuItem("退出");
	    menu.add(exitItem);
	    exitItem.addActionListener(event ->System.exit(0));

     	}

      }
