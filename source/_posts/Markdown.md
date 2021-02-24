---
title: hexo命令及Markdown语法
date: 2020/2/4 23:00:37
layout: Markdown
permalink:  Markdown.html
cover: /images/java1/b1.jpg
---
hexo是使用Markdown编辑文章的，这些文章也都是用这种标记语言完成的。Markdown 是一种轻量级标记语言，创始人为约翰·格鲁伯和亚伦·斯沃茨。它允许人们“使用易读易写的纯文本格式编写文档，然后转换成有效的XHTML文档”。
<!--more-->
## 一、创建文章
在站点文件夹中打开 git bash，输入如下命令创建文章，其中 title 为文章的标题


     $ hexo new "title"


当输入命令后，就会在 source/_post 文件夹下创建一个文件，命名为：title.md

这个文件就是将要发布到网站上的原始文件，用于记录文章内容

下面，我们将要在这个文件中写下我们的第一篇博客

### 二、编写文章（基于 Markdown）
#### 1、Markdown 简介
但是，在我们正式写下第一个文字前，我们需要了解一下究竟什么是 Markdown？

> Markdown 是一种可以使用普通文本编辑器编写的 标记语言，通过简单的 标记语法，它可以使普通文本内容具有一定的格式

基于 Markdown 语法的简洁性，它已经成为目前世界上最流行的用于书写博客的语言

#### 2、Markdown 语法
在编写 Markdown 时，博主强烈的推荐给大家一款简洁易用的 Markdown 编辑器 —— Typora

按照官方的说法就是 简单而强大，它不仅支持原生的语法，也支持对应的快捷键，更重要的是它还可以 实时预览

这里附上 Typora 的下载地址：https://www.typora.io/，有兴趣的朋友可以下载来试试

好，下面开始进入正题，介绍一些常用的 Markdown 语法

###（1）标题
Markdown 语法：

          # 一级标题
          ## 二级标题
          ### 三级标题
          #### 四级标题
          ##### 五级标题
          ###### 六级标题

Typora 快捷键：

          Ctrl+1：一级标题

          Ctrl+2：二级标题

          Ctrl+3：三级标题

          Ctrl+4：四级标题

          Ctrl+5：五级标题

          Ctrl+6 ：六级标题

          Ctrl+0：段落

### （2）粗体、斜体、删除线和下划线
Markdown 语法：

          *斜体*
          **粗体**
          ***加粗斜体***
          ~~删除线~~

Typora 快捷键：

          Ctrl+I：斜体

          Ctrl+B：粗体

          Ctrl+U：下划线

          Alt+Shift+5：删除线

### （3）引用块
Markdown 语法：

          > 文字引用

          Typora 快捷键： Ctrl+Shift+Q

### （4）代码块
Markdown 语法：

          `行内代码`

​          ```
          多行代码
          多行代码
​          ```

Typora 快捷键：

          行内代码：Ctrl+Shift+`

          多行代码：Ctrl+Shift+K

### （5）公式块
Markdown 语法：

          $$
          数学公式
          $$

Typora 快捷键： Ctrl+Shift+M

### （6）分割线
Markdown 语法：

          方法一：---

          方法二：+++

          方法三：***

### （7）列表
Markdown 语法：

          1. 有序列表项

          * 无序列表项

          + 无序列表项

          - 无序列表项

Typora 快捷键：

          有序列表项：Ctrl+Shift+[

          无序列表项：Ctrl+Shift+]

### （8）表格
Markdown 语法：

          表头1|表头2
          -|-|-
          内容11|内容12
          内容21|内容22

Typora 快捷键： Ctrl+T

### （9）超链接
Markdown语法：

          方法一：[链接文字](链接地址 "链接描述")
例如：[示例链接](https://www.example.com/ "示例链接")

          方法二：<链接地址>
例如：<https://www.example.com/>

Typora快捷键： Ctrl+K

### （10）图片
Markdown语法：

          ![图片文字](图片地址 "图片描述")
例如：![示例图片](https://www.example.com/example.PNG "示例图片")

Typora快捷键： Ctrl+Shift+I

### 说明：在 Hexo中 插入图片时，请按照以下的步骤进行设置

* 将 站点配置文件 中的 post_asset_folder 选项的值设置为 true

* 在站点文件夹中打开 git bash，输入命令 npm install hexo-asset-image --save 安装插件

* 这样，当使用 hexo new title 创建文章时，将同时在 source/_post 文件夹中生成一个与 title 同名的文件夹，我们只需将图片放进此文件夹中，然后在文章中通过 Markdown 语法进行引用即可

例如，在资源文件夹（就是那个与 title 同名的文件夹）中添加图片 example.PNG，则可以在对应的文章中使用语句 ![示例图片](title/example.PNG "示例图片") 添加图片

### 3、高级设置
（1）模板设置
当我们使用命令 hexo new "title" 创建文章时，Hexo 会根据 /scaffolds/post.md 对新文章进行初始化

换言之，/scaffolds/post.md 就是新文章的 模板，所以我们可以修改它来适应自己的写作习惯

一个简单的示例如下：

          title: {{ title }}
          date: {{ date }}
          tags:
          categories:

### （2）头部设置
在每篇利用 Hexo 创建的文章的开头，都会有对文章进行说明的文字，叫做 文章头部

文章的头部除了可以设置文章标题、发布日期等基础信息外，还可以为文章添加标签、分类等

一个简单的示例如下：

          title: Title
          date: YYYY-MM-DD HH:MM:SS
          tags: [tag1, tag2, ...]
          categories: category

注意：属性和属性值之间必须有一个空格，否则会解析错误

###  （3）首页显示
在利用 Hexo 框架搭建的博客网站中，首页会显示文章的内容，且默认显示文章的全部内容

如果当文章太长的时候就会显得十分冗余，所以我们有必要对其进行精简

这时，我们只需在文章中使用 <!--more--> 标志即可，表示只会显示标志前面的内容

## 三、部署发布
在站点文件夹中打开 git bash，输入如下命令部署和发布文章

          $ hexo g -d

文章参考：https://blog.csdn.net/wsmrzx/article/details/81478945
