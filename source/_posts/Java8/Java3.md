---
title: Java之基本语法
date: 2020/2/5 21:30:26
layout: java3
permalink: java3.html
cover: http://5b0988e595225.cdn.sohucs.com/images/20190418/47658e88f01a43d5b520242152262ddb.jpeg
---
主要介绍Java基本语法篇2，涉及循环结构，流程控制语句及Java中数组的使用，供回顾使用。
<!--more-->
## 学习思维导图
![](/images/java1/java11.jpg)
![](/images/java1/java12.jpg)

## 循环结构
### 循环语句功能
##### 在某些条件满足的情况下，反复执行特定代码的功能
#### 循环语句的四个组成部分
* 初始化部分（init_statement）
* 循环条件部分（test_exp）
* 循环体部分（body_statement）
* 迭代部分（alter_statement）

#### 循环语句分类

* for 循环
* while 循环
* do/while 循环

---

### for循环语句
#### 语法格式
          for (初始化表达式①; 布尔值测试表达式②; 更改表达式)｛
         	         语句或语句块③；
                    ｝
![](/images/java3/java31.PNG)

#### 应用举例
         	public class ForLoop {
		             public static void main(String args[]){
		                 int result = 0;
		                 for(int i=1; i<=100; i++) {
			                   result += i;
		                      }
  	                 System.out.println("1到100之间整数之和为：" + result);
                      	}
                   	}

#### for语句例题
* 编写程序FooBizBaz.java，从1循环到150并在每行打印一个值，另外在每个3的倍数行上打印出“foo”,在每个5的倍数行上打印“biz”,在每个7的倍数行上打印输出“baz”。
1
2
3 foo
4
5 biz
6 foo
7 baz
…
15 foo biz
….
105 foo biz baz
…
          public class FooBizBaz {
            public static void main(String[]args) {

            	for (int i = 0; i <=150; i++) {
            		String str="";
            		str+=i;
					if (i%3==0) {
						    str+="foo";
					}
					if (i%5==0) {
						    str+="biz";
					}
					if (i%7==0) {
						    str+="baz";
					}
					System.out.println(str);
				}
			}
      }

#### for语句练习
1.打印1~100之间所有奇数的和

2.打印1~100之间所有是7的倍数的整数的个数及总和（体会设置计数器的思想）

3.输出所有的水仙花数，所谓水仙花数是指一个3位数，其各个位上数字立方和等于其本身。
    例如： 153 = 1*1*1 + 3*3*3 + 5*5*5

---

### while 循环语句
#### 语法格式
 	     	[初始化语句]
	      	while( 布尔值测试表达式)｛
	           		语句或语句块;
		   	[更改语句;]
	    	}
#### 应用举例
		public class WhileLoop {
		        public static void main(String args[]){
        		int result = 0;
			int i=1;
			while(i<=100) {
			        result += i;
            	       	        i++;
			}
			        System.out.println("result=" + result);
		         }
		}

---

### do-while 循环语句
#### 语法格式
		[初始化语句]
		do｛
	        	语句或语句块;
		        [更改语句;]
		｝while(布尔值测试表达式);
#### 应用举例
		public class WhileLoop {
		        public static void main(String args[]){
        		  int result = 0,  i=1;
			        do{
			        	   result += i;
           		       	   i++;
				 }while(i<=100);
			 System.out.println("result=" + result);
		       }
		}  

#### 循环语句练习
编写程序一：求1到100之间所有偶数的和。用for和while语句分别完成。


#### 补充：
**最简单无限循环格式：while(true) , for(;;),无限循环存在的原因是并不知道循环多少次，需要根据某些条件，来控制循环。**


---

### 嵌套循环

* 将一个循环放在另一个循环体内，就形成了嵌套循环。其中，for ,while ,do…while均可以作为外层循环和内层循环。

* 实质上，嵌套循环就是把内层循环当成外层循环的循环体。当只有内层循环的循环条件为false时，才会完全跳出内层循环，才可结束外层的当次循环，开始下一次的循环。

* 设外层循环次数为m次，内层为n次，则内层循环体实际上需要执行m*n=mn次。

#### 例题：1）九九乘法表
              2）1—100之间的所有质数

---

### 特殊流程控制语句1
#### break 语句
* break语句用于终止某个语句块的执行

        {    … …	 
         break;
          ……
         }

* **break终止当前所在的循环**

#### break 语句用法举例
	 public class TestBreak{
		public static void main(String args[]){
	    for(int i = 0; i<10; i++){
	     	if(i==3)
		      break;	  
	    	System.out.println(" i =" + i);
	    }
	    System.out.println("Game Over!");
		}
}

---

### 特殊流程控制语句2
#### continue 语句
* **continue语句用于跳过某个循环语句块的一次执行**
* **continue语句出现在多层嵌套的循环语句体中时，可以通过标签指明要跳过的是哪一层循环**

#### continue语句用法举例
	public class ContinueTest {
		        public static void main(String args[]){
	     	   for (int i = 0; i < 100; i++) {
	      	         	  if (i%10==0)
			        		continue;
		         	                System.out.println(i);
		         	               }  }  }


---

### 特殊流程控制语句3
#### return：并非专门用于结束循环的，它的功能是结束一个方法。当一个方法执行到一个return语句时，这个方法将被结束。

#### 与break和continue不同的是，return直接结束整个方法，不管这个return处于多少层循环之内

#### 特殊流程控制语句说明

* **break只能用于switch语句和循环语句中。**
* **continue 只能用于循环语句中。**
* **二者功能类似，但continue是终止本次循环，break是终止本层循环。**
* **break、continue之后不能有其他的语句，因为程序永远不会执行其* **后的语句。**

---

### 一维数组声明
#### 一维数组的声明方式：
* **type  var[] 或 type[]  var；**
#### 例如：
		   int a[];
	   	   int[] a1;
		   double  b[];
		   Mydate[] c;  //对象数组

### 一维数组初始化
* **动态初始化：数组声明且为数组元素分配空间与赋值的操作分开进行**
      int[] arr = new int[3];
      arr[0] = 3;
      arr[1] = 9;
      arr[2] = 8;
* **静态初始化：在定义数组的同时就为数组元素分配空间并赋值。**
      int a[] = new int[]{ 3, 9, 8};
      int[] a = {3,9,8};

### 数组元素的引用
* **定义并用运算符new为之分配空间后，才可以引用数组中的每个元素；**
* **数组元素的引用方式：数组名[数组元素下标]**
* 数组元素下标可以是整型常量或整型表达式。如a[3] , b[i] , c[6*i];
* 数组元素下标从0开始；长度为n的数组合法下标取值范围: 0 —>n-1；如int a[]=new int[3];  可引用的数组元素为a[0]、a[1]、a[2]
* **每个数组都有一个属性length指明它的长度，例如：a.length 指明数组a的长度(元素个数)**
* 数组一旦初始化，其长度是不可变的

### 数组元素的默认初始化
* **数组是引用类型，它的元素相当于类的成员变量，因此数组一经分配空间，其中的每个元素也被按照成员变量同样的方式被隐式初始化。例如：**

      public class Test {
      public static void main(String argv[]){
      int a[]= new int[5]; 
      System.out.println(a[3]);	//a[3]的默认值为0
      }
      }

---

### 多维数组
![](/images/java3/java33.PNG)
![](/images/java3/java34.PNG)


#### 练习2：获取arr数组中所有元素的和。使用for的嵌套循环即可。
![](/images/java3/java32.PNG)
#### 练习3
声明：int[] x,y[];  以下选项允许通过编译的是：
a )   x[0] = y;  //no, x[0]是一个数，y是一个二维数组

b)    y[0] = x; //yes， y[0]就是一维数组，x是一维数组

c)    y[0][0] = x;//no， y[0][0] 是一个数字，x是一维数组

d)    x[0][0] = y;//no， x[0][0] 不存在，x是一维数组，没有第二维

e)    y[0][0] = x[0];//yes， y[0][0] 是一个数字， x[0]是一个数

f)    x = y; //no， x是一维数组，y是一个二维数组
一维数组：int[] x  或者int x[]   
二维数组：int[][] y 或者  int[] y[]  或者 int  y[][]

#### 数组中涉及的常见算法
* 1.求数组元素的最大值、最小值、总和、平均数

* 2.数组的复制、反转

* 3.数组元素的排序

### 数组排序
* **插入排序**
直接插入排序、折半插入排序、Shell排序

* **交换排序**
冒泡排序、快速排序（或分区交换排序）

* **选择排序**
简单选择排序、堆排序

* **归并排序**

基数排序

#### 冒泡排序
##### 排序思想：
* **相邻两元素进行比较，如有需要则进行交换，每完成一次循环就将最大元素排在最后（如从小到大排序），下一次循环是将其它的数进行类似操作。**

---

### 数组操作常见问题
* 编译时，不报错！！
![](/images/java3/java35.PNG)

##### 作业
使用简单数组
(1)创建一个名为TestArray的类，在main()方法中声明array1和array2两个变量，他们是int[]类型的数组。
(2)使用大括号{}，把array1初始化为8个素数：2,3,5,7,11,13,17,19。
(3)显示array1的内容。
(4)赋值array2变量等于array1，修改array2中的偶索引元素，使其等于索引值(如array[0]=0,array[2]=2)。打印出array1。

##### 思考：array1和array2是什么关系？
#####  拓展：修改题目，实现array2对array1数组的复制

### 相关代码
    public class Test3 {
	     public static void main(String[] args){
		//连续输出5次hello world
		System.out.println("hello world");
		System.out.println("hello world");
		System.out.println("hello world");
		System.out.println("hello world");
		System.out.println("hello world");

		for(int i = 0;i < 5;i++){//初始化表达式①; 布尔值测试表达式②; 更改表达式
			System.out.println(i);
			System.out.println("hello world");
		}
		//初始化变量，咱们这里的变量是i，判断i < 5，如果是，执行代码块{},执行更改表达式i++给i重新赋值，值就变为1
		//判断变量i < 5，当前的i是1，如果是，执行代码块{},执行更改表达式i++给i重新赋值，i值就变为2
		//判断变量i < 5，当前的i是2，如果是，执行代码块{},执行更改表达式i++给i重新赋值，i值就变为3
		//判断变量i < 5，当前的i是3，如果是，执行代码块{},执行更改表达式i++给i重新赋值，i值就变为4
		//判断变量i < 5，当前的i是4，如果是，执行代码块{},执行更改表达式i++给i重新赋值，i值就变为5
		//判断变量i < 5，当前的i是5，判断结果是false，不再往下执行，结束循环
		        int result = 0;
       for(int i=1; i<=100; i++) {
        	result += i;
       }
        System.out.println("result=" + result);

		for(int i = 1; i <= 150; i++){
			String str = "";
			str += i;
			if(i % 3 == 0){
				str += " foo";
			}
			if(i % 5 == 0){
				str += " biz";
			}
			if(i % 7 == 0){
				str += " baz";
			}
			System.out.println(str);
		}

        for(int i = 100; i <= 999; i++){
       	//145,145/100=1,(145-1*100)/10=4,145 - 1*100 - 4-10 = 5
        	int m = i/100;//得到百位数
        	int n = (i - m*100)/10;//得到十位数
       	int k = i - m*100 - n*10;//得到各位数字
        	System.out.println(i);
        	System.out.println(m + " " + n + " " + k);
        	int res = m*m*m + n*n*n + k*k*k;//各个位上数字立方和
       	if(res == i){//判断是不是水仙花数
        		System.out.println(i);
       	}
        }

		//循环输出1到100的数字
		int i = 1;
		while(i <= 100){
			//获取变量i <= 100的技术结果，是true还是false，如果是true就执行while的大括号里面的代码，如果是false不执行

			System.out.println(i);
			i++;//不断的改变变量i的值
			i = 101;
		}

		//与上面的while是等同的
		for(int k = 1; k <= 100; k++){

		}

		int m = 1;
		do{
			System.out.println(m);
			m++;
		}while(m <= 100);

		//求1到100之间所有偶数的和。用for和while语句分别完成
		int res = 0;
		for(int i = 1; i < 101; i++){
			if(i % 2 == 0){
				res += i;
			}
		}
		System.out.println(res);//要在for循环之外输出最后的结果，因为只有全部循环技术完毕才有1到100之间所有偶数的和

		int res0 = 0;
		int k = 1;
		while(k <= 100){
			if(k % 2 == 0){
				res0 += k;
			}
			k++;
		}

		System.out.println(res0);

		for(;;){//for循环的无限循环

		}

		while(true){//while的无限循环

		}

		for(int i = 0; i < 4; i++){//每一次循环都会执行大括号里面所有代码
			System.out.println("大循环---" + i);
			for(int j = 0; j < 2; j++){//大循环的次数乘以小循环的次数就是小循环的大括号里面执行代码的次数
				System.out.println("大循环---" + i + "小循环---" + j);
				for(){}
			}
		}
		//注意：在写嵌套循环的时候，要尽量保证外层循环的循环次小于内层的循环次数

		for(int i = 1; i < 900; i++){//不建议这样写
			for(int j = 0; j < 20; j++){

			}
		}

		//建议这样写
		for(int j = 0; j < 20; j++){//在编写代码的时候，如果上面的for循环与底下的for可以达到同样的逻辑效果时，要尽量使用下面这种
			for(int i = 1; i < 900; i++){

			}
		}

		1 * 1 = 1
		1 * 2 = 2 2 * 2 = 4
		1 * 3 = 3 2 * 3 = 6 3 * 3 = 9

		//九九乘法表
		for(int i = 1; i <= 9; i++){
			for(int j = 1; j <= i; j++){
				System.out.print(i + " * " + j + " = " + (i * j) + "  ");//print不换行
			}
			System.out.println();//println换行
		}
		//7,循环1到7，用7与循环1到7之间的数分别取模，看能整除的次数，如果整除的次数只有2次，那可以判断是一个质数
		//4,1、2、4，整除3次，不是质数
		//1—100之间的所有质数(质数是一个大于1的自然数并且只能被1和本身整除)
		for(int i = 1; i <= 100; i++){
			int k = 0;//整除的次数,变量是在它所在的大括号范围之内生效
			for(int j = 1; j <= i; j++){//循环1到i，用i与循环1到i之间的数分别取模

				if(i % j == 0){
					k++;
				}
			}

			if(k == 2){//如果循环次数为2次，当前大循环的i值就是1个质数
				System.out.println(i);
			}
		}
		int i = 9;
		switch(i){
		case 1:
			break;//终止case的
		case 2:
			break;//终止case的
		case 3:
			break;//终止case的
		}

		for(int i = 0; i < 9; i++){
			if(i > 6){
				break;//当i>6终止循环
			}
			System.out.println(i);

		}

		for(int j = 0; j < 3; j++){
			for(int i = 0; i < 9; i++){
				if(i > 2){
					break;//当i>6终止循环
				}
				System.out.println(i);

			}
			break;
		}

		for(int i = 0; i < 9; i++){
			if(i % 2 == 0){
				continue;//结束当前这次循环，直接进入下一次循环
			}
			System.out.println(i);
		}

		for(int i = 0 ; i < 9; i++){
			if(i == 7){
				return;//这块看起来和使用break感觉一样，但是实际上，return是把整个方法结束了，break只是终止当前的循环
			}
			System.out.println(i);
		}

		for(int i = 0; i < 2; i++){
			for(int j = 0; j < 2; j++){
				if(j == 1){
					return;//这块看起来和使用break感觉一样，但是实际上，return是把整个方法结束了，break只是终止当前的循环
					break;
				}
			}
			System.out.println(i);
		}

		int i = 0;
		int k = 1;
		int m = 2;
		//想把多个的数据放到一个变量里？使用数组，就存放多个数据的集合
		//例如，存放多个int的类型数据
		int[] ii;//声明一个int的数组
		int iii[];
		int[] ii = new int[4];//声明一个能放4个int类型数据的数组

		int[] ii0 = new int[]{1,2,3,4};//声明了一个存放了1、2、3、4这4个数的数组

		String[] strs = new String[]{"c","a","b"};//数组内的元素都有1个引用的元素下标，这个的下标是个数字，数字是从左到右从0开始

		System.out.println(strs[1]);

		System.out.println("strs的数组长度是：" + strs.length);

		int[] ii = new int[2];//使用动态初始化的时候，数组的元素会有默认值，数字类型的默认值是0，对象的默认类型是null
		System.out.println(ii[0]);

		int[] ii = new int[4];

		System.out.println(ii[0]);

		ii[0] = 2;
		System.out.println(ii[0]);

		//一维数组中每一个元素都是一个数组，这样数组就是二维数组
		int[][] ii = new int[][]{
				{1,2},//第0个元素
				{4,2}//第1个元素
		};

		int[][] ii0 = new int[2][3];//第一维部分的长度是2，第二维也就第一维的每个元素的长度是3
		//{
		// {1,23,4},
		// {2,4,6}
		//}
		int[][] ii1 = new int[2][];//只定义第一维的长度，第二维不定义
				System.out.println(ii[1][0]);		
		int[] x,y[]; //特殊写法，x是一维数组，y是二维数组

		int[][] arr = new int[][]{
				{3,8,2},
				{2,7},
				{9,0,1,6}
				};

		int len = arr.length;//数组的一维的长度
		int res = 0;
   	for(int i = 0; i < len; i++){
			int[] arr0 = arr[i];			int llen = arr0.length;//二维数组的长度
		for(int j = 0; j < llen; j++){
				res += arr0[j];
			}
		}
		System.out.println(res);


		for(int i = 0; i < arr.length; i++){
			for(int j = 0; j < arr[i].length; j++){
				res += arr[i][j];
			}
		}

		int[] arr = new int[]{4,2,7,1,3,5};
		//最大值
		int max = arr[0];//假设arr[0]是目前最大值
		for(int i = 0; i < arr.length; i++){
			if(max < arr[i]){
				max = arr[i];//存放目前最大值
			}
		}
		System.out.println("max:" + max);

		//最小值
		int min = arr[0];//假设arr[0]是目前的最小值
		for(int i = 0; i < arr.length; i++){
			if(min > arr[i]){
				min = arr[i];//把目前最小的值赋值给min
			}
		}
		System.out.println("min:" + min);

		//总和，平均数
		int res = 0;
		for(int i = 0; i < arr.length; i++){			res += arr[i];
		}
		System.out.println("总和：" + res);
		System.out.println("平均数：" + (res / arr.length));

  	//注意：复制不是赋值
		int[] aa = arr;//赋值
		int[] copy = new int[arr.length];//声明一个与arr长度一致的数组
		for(int i = 0; i < arr.length; i++){//复制
			copy[i] = arr[i];//遍历arr，把arr的每一个元素安装顺序拿出来，给copy的每一个元素赋值，在这里的i就是copy和arr的元素下标
		}

		//int[] arr = new int[]{4,2,7,1,3,5};
		//考虑声明一个数组temp，数组temp的长度与arr的长度一致，我们倒着循环arr，正着给temp的元素赋值
		// temp[0] = arr[5],temp[1] = arr[4],temp[2] = arr[3],temp[3] = arr[2],temp[4] = arr[1],temp[5] = arr[0]
		//temp就是arr的倒序的数组，然后再把temp赋值给arr（arr = temp）
		//一个数组的最后一个元素，它的下标等于数组的长度-1，因为元素的下标是从0开始
		int[] temp = new int[arr.length];
		int k = 0;//这个就是temp的元素下标
		for(int i = arr.length - 1; i >= 0; i--){
			System.out.println(arr[i]);
			temp[k] = arr[i];//第一次循环，k=0,i=5,相当于temp[0] = arr[5]
			k++;
		}
		arr = temp;
		for(int i = 0; i < arr.length; i++){
			System.out.println(arr[i]);
		}

		//正序，从大到小
		//4,7,3,1
		//4,3,1,7第一轮得到一个最大的数字，放在倒数第一位
		//3,1,4,7第二轮得到除最后一个数字之外的最大数字，放在倒数第二位
		//1,3,4,7第三轮得到除最后两个个数字之外的最大数字，放在倒数第三位

		int[] arr = new int[]{4,7,3,1};
		int[] arr = new int[]{2,56,33,1,8,5,64,34};
		int temp = 0;
		for(int i = 0; i < arr.length - 1; i++){//外层循环是循环轮次，轮次循环的次数是数字长度-1
			for(int j = 0; j < arr.length - 1 - i; j++){//每一轮次的数字对比排序,每轮次的循环依次4,3,2，轮次长度-1-i
				if(arr[j] > arr[j + 1]){//如果要是两个相邻的元素，前面的大于后面的，前后两个值交换
					temp = arr[j];
					arr[j] = arr[j + 1];
					arr[j + 1] = temp;
				}
			}
		}

		for(int i = 0; i < arr.length; i++){
			System.out.println(arr[i]);
		}

		for(int i = 0; i < arr.length - 1; i++){//外层循环是循环轮次，轮次循环的次数是数字长度-1
			for(int j = 0; j < arr.length - 1 - i; j++){//每一轮次的数字对比排序,每轮次的循环依次4,3,2，轮次长度-1-i
				if(arr[j] < arr[j + 1]){//如果要是两个相邻的元素，前面的大于后面的，前后两个值交换
					//正序与倒序排序，其他的都是一致的，在判断两个相邻的元素在声明情况下做交换不一样
					//如果是正序，前面的大于后面，交换
					//如果是倒序，前面的小于后面，交换
					temp = arr[j];
					arr[j] = arr[j + 1];
					arr[j + 1] = temp;
				}
			}
		}

		for(int i = 0; i < arr.length; i++){
			System.out.println(arr[i]);
		}

		int[] arr = new int[3];
		System.out.println(arr[4]);

		int[] arr = null;
		System.out.println(arr[0]);
	}
}
