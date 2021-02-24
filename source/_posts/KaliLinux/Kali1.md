---
title: 黑客日记之SQL注入原理
date: 2020/9/4 21:10:37
ayout: kali1
permalink: kali1.html
cover:
---
SQL注入是比较常见的网络攻击方式，它不是利用操作系统的漏洞，而是针对程序员编写时的疏忽，不注意规范书写 sql 语句和对特殊字符进行过滤...
<!--more-->

### SQL注入是什么
SQL注入是比较常见的网络攻击方式，它不是利用操作系统的漏洞，而是针对程序员编写时的疏忽，不注意规范书写 sql 语句和对特殊字符进行过滤，导致客户端可以通过全局变量POST 和 GET 提交一些 sql 语句正常执行。产生 Sql 注入，通过SQL语句，实现无账号登录，甚至篡改数据库。
### SQL注入的原因
语言的分类：
1. 解释型语言：解释型语言是一种在运行时由运行时一个运行时组件解释语言代码并执行其中包含的指令的语言（比如：Java、C#、PHP、JavaScript、VBScript、Perl、Python、Ruby、Shell等等，源代码不是直接翻译成机器语言，而是先翻译成中间代码，再由解释器对中间代码进行解释运行，例如Java中的JVM就是一个解释器及编译器）

2. 编译型语言：代码在生成时直接转换为机器指令，然后在运行时直接由使用该语言的计算机执行这些指令，机器语言是用二进制代码表示的计算机能够直接识别并执行的一种机器指令的集合。（编译型语言：C、C++等等）

**在解释型语言中，如果程序与用户进行交互，用户可以构造特殊的输入来拼接到程序中执行，从而使得程序依据用户输入执行有可能存在恶意行为的代码。**

**举个栗子：**在与用户交互的程序中，用户的输入拼接到SQL语句中，执行了与原定计划不同的行为，从而产生了SQL注入漏洞。

---

### SQL注入攻击思路
1. 寻找SQL注入的位置（例如：用户登录注册，用户搜索等等）
2. 判断服务器类型和后台数据库类型
3. 针对不同的服务器和数据库特点进行SQL注入攻击

---

### SQL注入案例


    String sql = "select * from user_table where username=
    ' "+userName+" ' and password=' "+password+" '";

- 当输入了上面的用户名和密码，上面的SQL语句变成：


    SELECT * FROM user_table WHERE username=
    '’or 1 = 1 -- and password='’


##### 分析SQL语句：

- 条件后面username=”or 1=1 用户名等于 ” 或1=1 那么这个条件一定会成功；

-  然后后面加两个-，这意味着注释，它将后面的语句注释，让他们不起作用，这样语句永远都能正确执行，用户轻易骗过系统，获取合法身份。
- 这还是比较温柔的，如果是执行
SELECT * FROM user_table WHERE
username='' ;DROP DATABASE (DB Name) --' and password=''篡改删除数据库，后果不堪设想。

### 如何防御SQL注入
我们知道程序凡是存在SQL注入漏洞，其程序都要接收来自客户端用户输入的变量或者URL传递的参数，并且这个变量或参数是组成SQL语句的一部分，而且这个变量或参数并没有通过合理的效验，便可以直接插入SQL语句中，这是十分可怕的。

对于用户输入的内容或参数的传递，我们都要时刻保持警惕，并对它进行合理的效验，确保它的合法性，我们应该遵循安全领域的【外部数据不可信任】的原则，纵观Web安全领域的各种攻击方式，大多数都是因为开发者违反了这个原则而导致的，开发者应该自然的从变量的检测、过滤、验证下手，从而通过限制特殊字符，类型，长度，格式等等方式，避免SQL注入的发生。

###### **检测变量，对变量的数据类型和格式加以限制**
> 例如，编写的SQL语句是类似where id = {$id}这种形式，且数据库中的id字段都为数据，就应该在该SQL执行前,确保用户输入或传递的变量id是int类型（加以判断，检测id的合法性）;如果接受邮箱，则一定要严格确保变量符合邮箱格式，而时间，日期等等也是同一个道理

这样我们就可以知道：当变量具有固定格式时，在SQL语句执行前，应该严格的进行格式检查，确保变量符合我们预想的格式，从而很多程度上避免SQL注入攻击。

######  **过滤特殊符号**

对于无法确定固定格式的变量，一定要进行特殊符号过滤或转义处理。

######  **绑定变量，使用预编译语句**

MySQL提供了预编译语句的支持，不同的程序语言，都分别有使用预编译语句的方法

实际上，绑定变量使用预编译语句是预防SQL注入的最佳方式，使用预编译的SQL语句语义不会发生改变，在SQL语句中，变量用问号?表示，黑客即使本事再大，也无法改变SQL语句的结构


### 预编译语句是如何防止SQL注入的
首先，我们要清楚一条sql的执行过程：

　　1. 词法和语义解析
　　2. 优化sql语句，制定执行计划
　　3. 执行并返回结果

> 我们把这种普通语句称作Immediate Statements。

 - 但是很多情况，我们的一条sql语句可能会反复执行，或者每次执行的时候只有个别的值不同（比如query的where子句值不同，update的set子句值不同,insert的values值不同）。

- 如果每次都需要经过上面的词法语义解析、语句优化、制定执行计划等，则效率就明显不行了。

- 所谓预编译语句就是将这类语句中的值用占位符替代，可以视为将sql语句模板化或者说参数化，一般称这类语句叫Prepared Statements或者Parameterized Statements


* 预编译语句的优势在于归纳为：一次编译、多次运行，省去了解析优化等过程；此外预编译语句能防止sql注入。


在我看来预编译最大的作用便是防止SQl注入

举个栗子

    @Before
    public void init() {
    //获取数据库连接
    final String DRIVER = "com.mysql.jdbc.Driver";
    final String URL = "jdbc:mysql://127.0.0.1:3306/employees?characterEncoding=utf-8&useSSL=true&verifyServerCertificate=false&useServerPrepStmts=true&cachePrepStmts=true";
    final String USER = "root";
    final String PWD = "";
    try {

        Class.forName(DRIVER);
        con = DriverManager.getConnection(URL, USER, PWD);
    } catch (ClassNotFoundException e) {
        e.printStackTrace();
    } catch (SQLException e) {
        e.printStackTrace();
    }
    }
    @After
    public void end() {
    try {
        con.close();
    } catch (SQLException e) {
        e.printStackTrace();
      }
    }

测试一下：

    @Test
    public void test1() throws SQLException {
    //非预编译
    String testSql = "select * from departments where dept_no = ";
    String args = "1 or 1=1";
    Statement statement=con.createStatement();
    statement.execute(testSql+args);
    }

    @Test
    public void test2() throws SQLException {
    //预编译
    String testSql = "select * from departments where dept_no = ?";
    String args = "1 or 1=1";
    PreparedStatement ps = con.prepareStatement(sql);
    ps.setString(1,args);
    ps.execute();
    }

然后打开mysql的全日志，方法如下：
![](/images/kali1/1.png)

执行test，可以在log中看到：
![](/images/kali1/2.png)

#### 为什么PrepareStatement可以防止sql注入

　　原理是采用了预编译的方法，先将SQL语句中可被客户端控制的参数集进行编译，生成对应的临时变量集，再使用对应的设置方法，为临时变量集里面的元素进行赋值，赋值函数setString()，会对传入的参数进行强制类型检查和安全检查，所以就避免了SQL注入的产生。下面具体分析

#####（1）：为什么Statement会被sql注入

　　因为Statement之所以会被sql注入是因为SQL语句结构发生了变化。比如：

    "select*from tablename where username='"+uesrname+  
    "'and password='"+password+"'"
　　在用户输入'or true or'之后sql语句结构改变。

    select*from tablename where username=''or true or'' and password=''

这样本来是判断用户名和密码都匹配时才会计数，但是经过改变后变成了或的逻辑关系，不管用户名和密码是否匹配该式的返回值永远为true;

#####　（2）为什么Preparement可以防止SQL注入。

　　因为Preparement样式为

    select*from tablename where username=? and password=?

该SQL语句会在得到用户的输入之前先用数据库进行预编译，这样的话不管用户输入什么用户名和密码的判断始终都是并的逻辑关系，防止了SQL注入

　　简单总结，参数化能防注入的原因在于，语句是语句，参数是参数，参数的值并不是语句的一部分，数据库只按语句的语义跑，至于跑的时候是带一个普通背包还是一个怪物，不会影响行进路线，无非跑的快点与慢点的区别。

### mybatis是如何防止SQL注入的

    <select id="selectByNameAndPassword" parameterType="java.util.Map" resultMap="BaseResultMap">
    select id, username, password, role
    from user
    where username = #{username,jdbcType=VARCHAR}
    and password = #{password,jdbcType=VARCHAR}
    </select>

    <select id="selectByNameAndPassword" parameterType="java.util.Map" resultMap="BaseResultMap">
    select id, username, password, role
    from user
    where username = ${username,jdbcType=VARCHAR}
    and password = ${password,jdbcType=VARCHAR}
    </select>


mybatis中的#和$的区别：

1. #将传入的数据都当成一个字符串，会对自动传入的数据加一个双引号。

如：where username=#{username}，如果传入的值是111,那么解析成sql时的值为where username="111", 如果传入的值是id，则解析成的sql为where username="id".　

2. $将传入的数据直接显示生成在sql中。
如：where username=${username}，如果传入的值是111,那么解析成sql时的值为where username=111；
如果传入的值是;drop table user;，则解析成的sql为：select id, username, password, role from user where username=;drop table user;

3. #方式能够很大程度防止sql注入，$方式无法防止Sql注入。

4. $方式一般用于传入数据库对象，例如传入表名.

5. 一般能用#的就别用$，若不得不使用“${xxx}”这样的参数，要手工地做好过滤工作，来防止sql注入攻击。

6. 在MyBatis中，“${xxx}”这样格式的参数会直接参与SQL编译，从而不能避免注入攻击。但涉及到动态表名和列名时，只能使用“${xxx}”这样的参数格式。所以，这样的参数需要我们在代码中手工进行处理来防止注入。
【结论】在编写MyBatis的映射语句时，尽量采用“#{xxx}”这样的格式。若不得不使用“${xxx}”这样的参数，要手工地做好过滤工作，来防止SQL注入攻击。

mybatis是如何做到防止sql注入的

　　MyBatis框架作为一款半自动化的持久层框架，其SQL语句都要我们自己手动编写，这个时候当然需要防止SQL注入。其实，MyBatis的SQL是一个具有“输入+输出”的功能，类似于函数的结构，参考上面的两个例子。其中，parameterType表示了输入的参数类型，resultType表示了输出的参数类型。回应上文，如果我们想防止SQL注入，理所当然地要在输入参数上下功夫。上面代码中使用#的即输入参数在SQL中拼接的部分，传入参数后，打印出执行的SQL语句，会看到SQL是这样的：

select id, username, password, role from user where username=? and password=?
　　不管输入什么参数，打印出的SQL都是这样的。这是因为MyBatis启用了预编译功能，在SQL执行前，会先将上面的SQL发送给数据库进行编译；执行时，直接使用编译好的SQL，替换占位符“?”就可以了。因为SQL注入只能对编译过程起作用，所以这样的方式就很好地避免了SQL注入的问题。

　　【底层实现原理】MyBatis是如何做到SQL预编译的呢？其实在框架底层，是JDBC中的PreparedStatement类在起作用，PreparedStatement是我们很熟悉的Statement的子类，它的对象包含了编译好的SQL语句。这种“准备好”的方式不仅能提高安全性，而且在多次执行同一个SQL时，能够提高效率。原因是SQL已编译好，再次执行时无需再编译


本文参考：https://www.jianshu.com/p/6f6195da1063

        https://www.cnblogs.com/myseries/p/10821372.html
