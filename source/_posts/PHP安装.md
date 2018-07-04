---
title: PHP安装
date: 2017-12-18 10:57:46
categories:
- PHP
- 正文
---

# PHP安装

在安装之前，我们首先要了解我们PHP可以用来做什么。在官方文档中写到有三种用途：
* Websites and web applications (server-side scripting)
* Command line scripting
* Desktop (GUI) applications

我们一般是用它来写服务器端脚本。所以我们需要一个web服务器和一个web浏览器。

## 解压

将下载的包解压到`C:\php`（名称随意，但最好不要在路径中出现空格，如“C:\Program Files\PHP”，否则可能导致一些web服务器崩溃），将路径添加到**PATH**。
在命令行界面输入`path`检查是否生效。

## 安装Apache服务器

在[下载页](https://www.apachehaus.com/cgi-bin/download.plx)中选择自己要安装的版本（注意安装对应的VC环境），将下载好的压缩包解压，当前路径为`C:\Apache24`。
以管理员身份打开命令行界面，切到`C:\Apache24\bin`目录下，输入`httpd.exe`启动httpd服务。
可以输入`httpd -k install`将Apache作为服务安装到Windows系统。
*注意端口占用问题*
命令行操作：
```
httpd -k stop			停止Apache
httpd -k restart		重启Apache
httpd -k uninstall		卸载Apache
httpd -t			测试配置语法
httpd -V			查看Apache版本
httpd -h			查看Apache命令行选项
```

打开*httpd.conf*,在*LoadModule* 末尾添加：
```
LoadModule php7_module "C:/php/php7apache2_4.dll"
AddType application/x-httpd-php .php
PHPIniDir "C:/php"
```
告诉Apache Server以后收到的Url用户请求，凡是以php作为后缀，就需要调用php7_module模块（php7apache2_4.dll）进行处理。

## 配置php.ini

修改根目录中的*php.ini-production* 名称为*php.ini* 。
修改*doc_root*参数为当前所用web服务器的文档根目录：
```
doc_root = C:\Apache24\htdocs
```
将`; extension_dir = "ext"`前的`;`去掉。

## 安装MySQLi

在PHP7中，移除了MySQL的拓展，推荐使用mysqli或者pdo_mysql。下面开始安装MySQLi。
首先，将`;extension=mysqli`前的`;`去掉。
将`extension_dir = "ext"`中的`ext`修改为当前安装的PHP版本的ext文件夹路径，如`extension_dir = "C:\php\ext"`。
重启Apache服务器，通过`PHPinfo()`验证MySQLi的安装。