---
title: Java进阶之泛型
date: 2020/4/27 20:08:11
layout: java8
permalink: java8.html
cover: http://5b0988e595225.cdn.sohucs.com/images/20190418/47658e88f01a43d5b520242152262ddb.jpeg
---
普通的类和方法只能使用特定的类型，基本数据类型或类类型。如果编写的代码需要应用于多种类型，这种严苛的限制对代码的束缚就会很大。Java 泛型（generics）是 JDK 5 中引入的一个新特性, 泛型提供了编译时类型安全检测机制，该机制允许程序员在编译时检测到非法的类型。泛型的本质是参数化类型，也就是说所操作的数据类型被指定为一个参数。 <!--more-->

---

#### 一、泛型的认识
Java 泛型（generics）是 JDK 5 中引入的一个新特性, 泛型提供了编译时类型安全检测机制，该机制允许程序员在编译时检测到非法的类型。

参数化类型：
* 把类型当做参数一样传递
* <数据类型>只是引用类型

相关术语：
* ArrayList<I>中的I称为类型参数变量
* ArrayList<Integer> 中的Integer称为实际类型参数
* 整个称为ArrayList<I>泛型类型
* 整个ArrayList<Integer>称为参数化的类型ParameterizedType


> 泛型：把类型明确的工作推迟到创建对象或调用方法的时候才去明确的特殊类型

> 使用泛型机制编写大程序代码要比那些杂乱无章地使用Object变量，然后再进行强制类型转换的代码具有更好的安全性和可读性。

> 泛型的本质是参数化类型，也就是说所操作的数据类型被指定为一个参数

> 对于泛型，只是允许程序员在编译时检测到非法的类型而已。
但是在运行期时，其中的泛型标志会变化为 Object 类型。

---

##### 二、泛型的作用
Java语言引入泛型的好处是安全简单，它可以使代码更直接更优雅的同时可以将运行时的错误提前到编译时的错误。
> 泛型设计原则：只要在编译期间没有出现警告，那么运行期间就不会出现ClassCastException异常

与JavaSE 1.5引入泛型前做对比：
>1. 在没有泛型的情况下，往往是通过对Object的引用类似实现参数的“任意化”，“任意化”带来的缺点便是需要进行显示地强制类型转换。针对类型转换错误情况，编译器不会报错，在运行时才会抛出异常：ClassCastException，因此使用Object实现参数的”任意化”是存在安全隐患的。
>2. 有了泛型后：泛型提供了编译时的类型安全检测机制，允许开发者在编译时检测到非法类型转换，提高了代码的健壮性，同时泛型会进行自动和隐式的强制类型转换，提高了代码的复用性。

假定我们有这样一个需求：写一个排序方法，能够对整型数组、字符串数组甚至其他任何类型的数组进行排序，该如何实现？

> 使用 Java 泛型便能很好的解决，使用 Java 泛型的概念，我们可以写一个泛型方法来对一个对象数组排序。然后，调用该泛型方法来对整型数组、浮点数数组、字符串数组等进行排序。

---

##### 三、泛型的使用

###### (一)、泛型类
泛型类就是将泛型定义在类上，用户在使用该类时，才会把类型明确下来，用户明确了什么类型，该类就代表着什么类型，当用户在使用的时候就不用担心强转类型的问题，运行时转换异常的问题了。

* 注：在类上定义的泛型，在类的方法中也可以使用。

      //1. 把泛型定义在类上
      //2. 类型变量定义在类上，方法中也可以使用
      public class ObjectTool<T> {
       private T obj;

       public T getObj(){
         retuen obj;
       }
       public void setObj(T Obj){
         this.obj = obj;
       }
      }

让我们来测试一下：

     public static void main (String[] ags) {
       //创建对象并指定元素类型
       ObjectTool<String> tool = new ObjectTool<>();

       tool.setObj(new String("罗小刀"));
       String s = tool.getObj();
       System.out.println(s);

       //创建对象并指定元素类型
       ObjectTool<Integer> ObjectTool = new ObjectTool<>();
       /**
        * 如果我在这个对象里传入的是String类型的，它在编译时期就通过不了了。
        */
        ObjectTool.setObj(10);
        int i = ObjectTool.getObj();
        System.out.out.println(i);
     }

可以看出，用户想要使用哪种类型，就在创建的时候指定类型，使用时，该类就会自动转换成用户想要使用的类型。

---

###### (二)、泛型方法
在上面提到了在类上定义的泛型，在方法中也可以使用，
现在，我们只想在某个方法上使用泛型，外界仅仅是关心该方法，不关心其他属性，这样的话我们在整个类上定义泛型，就未免有些小题大做了。

     //定义泛型方法，泛型是先定义后使用
     public <T> void show(T t) {
       System.out.println(t);
     }

再让我们来测试一下：

    public static void main (String[] ags) {
    //创建对象
    ObjectTooltool = new ObjectTool<>();

    //调用方法，传入的参数是什么类型，返回值就是什么类型
    tool.show("hello!boy!");
    tool.show(100);
    tool.show(3.14159);
    }  

可以看出，调用方法时，传入的参数是什么类型，返回值就是什么类型。

---

###### (三)、泛型类派生出的子类

前面我们已经定义了泛型类，泛型类是拥有泛型这个特征的类，所以它本质上的Java类就可以被继承。

当它被继承时，会有两种情况：
    1. 子类明确泛型类的类型参数变量
    2. 子类不明确泛型类的类型参数变量

###### 子类明确泛型类的类型参数变量

* 泛型接口

      //把泛型定义在接口上
      public interface Inter<T> {
        public abstrat void show(T t);
      }    

* 实现泛型接口的类

     //子类明确泛型类的类型参数变量
     public class InterImpl implements Inter<String> {
       @Override
       public void show(String s) {
         System.out.println(s);
       }
     }

###### 子类不明确泛型类的类型参数变量   

---

当子类不明确泛型接口的类型参数变量时，外界使用子类的1时候，也需要传递类型参数变量进来，在实现类上需要定义出类型参数变量。

    //子类不明确泛型类的类型参数变量，子类也要定义出<T>类型
    public class InterImpl<T> implements Inter<T> {

      @Override
      public void show(T t) {
        System.out.println(t);
      }
    }

第n次测试：

      public static void main(String[] args) {
           //开始第一种情况测试
           //Inter<String> i = new InterImpl();
           //i.show("hello");


           //开始第二种情况测试
           Inter<String> ii = new InterImpl<>();
           ii.show("100");
      }

---

##### （四)、类型通配符
