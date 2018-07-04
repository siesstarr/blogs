---
title: PHP websocket应用
date: 2018-04-23 10:42:00
categories:
---

>能在Linux环境下开发就别用Windows。		——鲁迅

坑爹啊，我只想用PHP写一个socket实例啊(╯‵□′)╯︵┻━┻
只想可以在框架中实现啊(╯‵□′)╯︵┻━┻
只想使用下Swoole啊(╯‵□′)╯︵┻━┻
为什么安装那么麻烦_(:з」∠)_


# 简介

懒的编。自己去了解`socket`和`websocket`。


# 安装

再次强调，有条件使用Linux环境开发就别使用Windows!!!!

简单说下Windows环境下的安装坑爹之路。
首先在[Swoole中文文档](https://wiki.swoole.com/)->入门指南->编译安装中，了解到Swoole有两种安装方式，一种是使用`make`编译后安装，一种是使用`pcre`直接安装。
方法一：
```
1. 下载源码包。地址：https://github.com/swoole/swoole-src/releases
2. cd swoole
3. phpize
4. ./configure
5. make
6. make install
```
这个方法要有C++运行环境、make命令、autoconf(并不知道是什么)这些环境准备，如果我没理解错的话，`gcc-4.4 或更高版本`这个环境就是那个需要下载最少上G的安装包，面对公司下载速度只有几十KB的小水管果断放弃。所以只能看方法二了。
方法二：
```
1. pecl install swoole
```
这个方法就很简单了有没有!我们只需要有pecl这个命令就好了。而且，在文档里也明确说了，这是PHP官方提供的命令，瞬间开心！然后就去试验了下`pecl`命令，呵呵，没有这个命令。_(:з」∠)_
然后发现在官方文档中写到：
>目前 PHP 项目没有为 Windows 下 PECL 扩展编译二进制文件。要在 Windows 下编译 PHP，请阅读[有关章节](http://php.net/manual/zh/install.windows.legacy.index.php#install.windows.building)。

可以的。_(:з」∠)_
好吧，我们开始安装pecl。首先，需要到[go-pear.phar](http://pear.php.net/go-pear.phar) 获取到go-pear.phar文件，将他放置在php的根目录。执行`./php.exe go-pear.pear`，安装位置为local，然后就卡死了o(╥﹏╥)o
换用cmd试试。这次使用管理员身份。
换了后成功出来了安装过程，emmmm，反正也看不懂，按enter就对了_(:з」∠)_
然后！重点来了！然后执行`pecl install swoole`：
```
WARNING: channel "pecl.php.net" has updated its protocols, use "pecl channel-update pecl.php.net" to update
downloading swoole-2.1.3.tgz ...
Starting to download swoole-2.1.3.tgz (830,565 bytes)
..................................................................................................................done: 830,565 bytes
247 source files, building
WARNING: php_bin C:\wamp64\bin\php\php7.1.9\php.exe appears to have a suffix .exe, but config variable php_suffix does not match
ERROR: The DSP swoole.dsp does not exist.
```
查了下，**Windows is not supported**(╯‵□′)╯︵┻━┻
心平气和安装了homestead，over。


