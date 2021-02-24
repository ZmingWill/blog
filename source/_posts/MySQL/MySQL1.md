---
title: MySQL学习之基础入门
date: 2020/9/15 14:00:13
layout: MySQL
permalink:  MySQL1.html
cover:
---
MySQL是一种关系型数据库管理系统，对于个人开发者和中小型企业都是不错的选择，我将逐步学习mysql的sql基本的使用方法，从MySQL执行引擎再到索引、事务等知识，一步步地学习MySQL相关技术的实现原理，更好地了解如何基于这些知识来优化sql，减少SQL执行时间，通过执行计划对SQL性能进行分析，再到MySQL的主从复制、主备部署等内容，以便让更完整地了解整个MySQL方面的技术体系，从而能够在日常操作中灵活运用。
<!--more-->
## 数据库的好处
    1.持久化数据到本地
    2。可以实现结构化查询，方便管理

## 数据库的概念
##### DB
* **数据库（database):存储数据的“仓库”。它保存了一系列有组织的数据。**
##### DBMS
* **数据库管理系统（Databese Management System）。数据库是通过DBMS创建和操作的容器。**
##### SQL
* **结构化查询语言（Structure Query Language）：专门用来与数据库通信的语言。**

---

### SQL的特点：
    1.不是某种特定的数据库供应商专有的语言，几乎所有DBMS都支持SQL。
    2.简单易学


### MySQL产品的特点
* MySQL数据库隶属于MySQLAB公司，总部位于瑞典，后被oracle收购。
* 优点：
     - 成本低：开放源代码，一般可以免费试用
     - 性能高：执行很快
     - 简单：很容易安装和使用
* DBMS分为两类:
     - 基于共享文件系统的DBMS（Access）
     - 基于客户机——服务器的DB MS（MySQL,Oracle,SqlServer）

---  

### MySQL的简单使用

MySQL 为关系型数据库(Relational Database Management System)，一个关系型数据库由一个或数个表格组成的

![](/images/MySQL/MySQL0915/MySQL1.png)

* 表头(header): 每一列的名称;

* 列(col): 具有相同数据类型的数据的集合;

* 行(row): 每一行用来描述某个人/物的具体信息;

* 值(value): 行的具体信息, 每个值必须与该列的数据类型相同;

* 键(key): 表中用来识别某个特定的人物的方法, 键的值在当前列中具有唯一性。





#### MySQL服务的启动和停止
    方式一：
    计算机-管理工具-服务
    方式二：用DOS命令
    启动服务：net stat mysql
    停止服务：net start mysql

---
### MySQL服务的登录和退出  

#### 登录MySQL
     mysql -h 127.0.0.1 -u 用户名 -pmysql -D 所选择的数据库名 -h 主机名 -u 用户名 -pmysql>

     exit # 退出 使用 “quit;” 或 “\q;” 一样的效果

     mysql> status;  # 显示当前mysql的version的各种信息

     mysql> select version(); # 显示当前mysql的version信息

     mysql> show global variables like 'port'; # 查看MySQL端口号

#### 创建数据库

对于表的操作需要先进入库use 库名;

- 创建一个名为 samp_db 的数据库，数据库字符编码指定为 gbkcreate database samp_db character set gbk;
 * drop database samp_db;——- 删除 库名为samp_db的库
 * show databases;        ——- 显示数据库。
 * use samp_db;     ——- 选择创建的数库
 * samp_dbshow tables;     ——- 显示samp_db下面所有的表名字
 * describe 表名;    ——- 显示数据表的结构
 * delete from 表名; - 清空表中记录

#### 创建数据库表
使用 create table 语句可完成对表的创建, create table 的常见形式:

语法：create table 表名称(列声明);

    CREATE TABLE `user_accounts` (
     `id`   int(100) unsigned NOT NULL AUTO_INCREMENT primary key,
     `password`   varchar(32)   NOT NULL DEFAULT '' COMMENT '用户密码',
     `reset_password` tinyint(32)       NOT NULL DEFAULT 0 COMMENT '用户类型：0－不需要重置密码；1-需要重置密码',
     `mobile`  varchar(20)   NOT NULL DEFAULT '' COMMENT '手机',
     `create_at` timestamp(6)  NOT NULL DEFAULT CURRENT_TIMESTAMP(6),  
     `update_at`      timestamp(6)      NOT NULL DEFAULT CURRENT_TIMESTAMP(6) ON UPDATE CURRENT_TIMESTAMP(6),
       -- 创建唯一索引，不允许重复  UNIQUE INDEX
     idx_user_mobile(`mobile`))ENGINE=InnoDB DEFAULT CHARSET=utf8COMMENT='用户表信息';

#### 数据类型属性

* NULL：数据列可包含NULL值；

* NOT NULL：数据列不允许包含NULL值；

* DEFAULT：默认值；

* PRIMARY：KEY 主键；

* AUTO_INCREMENT：自动递增，适用于整数类型；

* UNSIGNED：是指数值类型只能为正数；

* CHARACTER SET name：指定一个字符集；

* COMMENT：对表或者字段说明；
