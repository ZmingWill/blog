---
title: Java面试突击一百道
date: 2021/1/3 1:01:37
layout: Markdown
permalink: Interview100.html
cover: /images/java1/b1.jpg
---

<!--more-->

#### 01.谈谈你对面向对象思想的理解

- 首先，谈谈“面向过程”和”面向对象“

我觉得这两者主要是思考角度的差异，面向过程更多是以“执行者”的角度来思考问题，而面向对象更多是以”组织者“的的角度来思考问题，举个例子，比如我要产生一个0-10之间的随机数，如果以"面向过程"的思维，我更多的关注如何设计一个算法，然后保证比较均衡的产生0-10的随机数，而面向对象的思维下我更多的会关注，我应该找谁来帮我们做这件事，比如Random类，调用其中提供的方法就行了。

所以面向对象的思维更多的是考虑如何去选择合适的工具，然后组织到一起干一件事。

就好比一个导演，要拍一部电影，那么首先要有男主角和女主角，然后其他等等，最后把这些资源组织起来，拍成一部电影。

再回到我们的程序世界，这种组织者的思维无处不在，比如我们要开发项目，以三层架构的模式来开发，那么这个时候，我们不需要造轮子，只需要选择市面上主流的框架即可，比如SpringMVC，Spring，MyBatis等等，这些都是各层的主流框架。


#### 1.JDK,JRE,JVM有什么区别？

- JDK(Java DeveLopment Kit) Java开发工具包，提供了Java开发环境和运行环境。包含了编译Java源文件的编辑器Javac，还有调试和分析工具。

- JRE(Java Runtime Environment) Java运行环境，包含Java虚拟机及一些基础类库。

- JVM(Java Virtual Machine) Java虚拟机，提供执行字节码文件的能力。

所以，如果只是运行Java程序,只需要安装JRE即可。

另外注意，JVM是实现Java跨平台的核心，但JVM本身是不能跨平台的，不同的平台需要安装相应的JVM。

![](https://pic3.zhimg.com/80/v2-199da3b71771a2ac8a6abca871d2bca2_720w.jpg)

#### 2. Java的基本数据类型有哪些？

boolean，char，byte，short，int，long，float，double
而String是引用类型

它们的存储位置：

![](https://img-blog.csdn.net/20170729110914749?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvcXFfMzY1OTYxNDU=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)


#### 3. ==和equals的区别

- == 比较的是值

 > 比较基本数据类型，比较的是数值

 > 比较引用数据类型，比较的是引用所指的值（地址）

- equals 默认比较也是地址，这个方法最初是定义在Object上，默认的实现就是比较地址
自定义的类，如何需要比较的是内容，那么就要学String，重写equals

案例：

    String s1 = new String("zs");
    String s2 = new String("zs");
    System.out.println(s1 == s2);

    false
    双方均new了对象



    String s3 = "zs";
    String s4 = "zs";
    System.out.println(s3 == s4);

    true
    双方均指向常量池的地址

    System.out.println(s3 == s1);

    false
    s3指向常量池的地址
    s1指向的是对象引用的地址


    String s5 = "zszs";
    String s6 = s3+s4;
    System.out.println(s5 == s6);

    false
    s5指向常量池的地址
    s6拼接变量，new了新对象


    final String s7 = "zs";
    final String s8 = "zs";
    String s9 = s7+s8;
    System.out.println(s5 == s9);

    true
    由于s7和s8都是常量，s9在运算时结果也会转变成常量
    s9和s5均指向常量池的值（”zszs”）


    final String s10 = s3+s4;
    System.out.println(s5 == s10);

    false
    s10拼接变量指向引用的对象地址
    s5指向常量池

#### 4. final的作用

 - final修饰类：表示类不可变，不可继承

 比如，String，不可变性

 - final修饰方法：表示方法不可被重写

 比如模板方法，可以固定我们的算法

 - final修饰变量：这个变量就是常量

 注意：

 - 修饰的是基本数据类型，这个值本身不能修改
 - 修饰的是引用类型，引用的指向不能修改

 比如下面的代码是可以的

   fianl Student student = new Student(1,"Andy");
   student.setAge(18);//注意这个是可以的！
   //Student s2 = new Student(1,"Tom");
   //student = s2;        //注意这样是不可以的！

final修饰的对象内容是可以改变的，但是引用时不能内改变的，如果执行注释到的内容，将新生成的s2对象赋值给student的话就会报错。
