---
title: laravel安装
date: 2018-01-17 15:43:20
categories:
- laravel
- 正文
---

# laravel安装

在官网上安装教程为使用`Homestead`虚拟机作为开发环境。因为电脑配置原因，在这里使用本地环境作为开发环境。
在本地环境中开发laravel，需要满足以下几点要求：
* PHP >= 7.0.0
* PHP OpenSSL 扩展
* PHP PDO 扩展
* PHP Mbstring 扩展
* PHP Tokenizer 扩展
* PHP XML 扩展

## 安装composer

laravel使用composer来进行管理,所以安装laravel需要先安装composer。

首先，新建文件夹composer，路径为`C:\composer`。将路径加入到环境变量中。
然后启动`cmd`或者使用`git bash`在C:\composer目录下执行以下内容：
```
php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
php -r "if (hash_file('SHA384', 'composer-setup.php') === '544e09ee996cdf60ece3804abc52599c22b1f40f4323403c44d44fdfdd586475ca9813a858088ffbc1f233e9b180f061') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
php composer-setup.php
php -r "unlink('composer-setup.php');"
```
上面的操作分别是：
* 下载安装程序到当前目录
* 验证安装程序`SHA384`
* 运行安装程序
* 删除安装程序

执行`composer -version`查看版本号验证安装是否成功。

## 启用中国镜像

修改composer的全局配置文件启动镜像服务。
```
composer config -g repo.packagist composer https://packagist.phpcomposer.com
```

## 安装laravel

输入`composer require laravel/laravel`下载laravel。
打开命令行工具进入c盘根目录，执行`composer create-project laravel/laravel --prefer-dist`安装laravel。
安装完成后进入laravel目录，输入`php artisan serve`启动laravel，也可以输入`php artisan serve --port=80`在80端口启动（需要确保端口未被占用）。
在浏览器中输入地址，网页页面中出现`laravel`表示安装成功。