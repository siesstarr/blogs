---
title: Hello World！
date: 2017-12-18 15:44:00
categories:
- PHP
- 正文
---

# Hello World！

在前面我们已经搭建好了PHP的执行环境，现在开始写第一个程序“Hello World”。
首先，启动Apache服务器。
然后，在Apache服务器的*htdocs*目录下新建*helloworld.php*，内容为：
```
<?php
	echo "hello world!";
```
打开web浏览器，输入`http://localhost/helloworld.php`，可以看到*hello world!*的字样已经打印在屏幕上。
至此，PHP已经解析完成。
然后我们来详细了解下整个过程：
1. 启动Apache服务器。
2. 通过URL访问文件名为*helloworld.php*的服务器资源。
3. Apache服务器返回解析结果。
然后我们再仔细分析。

## SAPI

