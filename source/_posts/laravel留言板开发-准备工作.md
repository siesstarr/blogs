---
title: laravel留言板开发-准备工作
date: 2018-01-18 13:36:01
categories:
- laravel
- 正文
---

# laravel留言板开发-准备工作

因为我们不是在Homestead上搭建的laravel，所以需要自行启动laravel，启动命令为`php artisan serve --port=80`。
打开`.env`文件对数据库进行简单的配置：
```
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=messageboard
DB_USERNAME=root
DB_PASSWORD=123456
```
这里的messageboard数据库需要自己手动创建。
输入命令`php artisan migrate`（命令在数据库相关部分详解），打开messageboard数据库可以看到其中有三张表`migrations`、`password_resets`、`users`，显然数据库连通没有问题。
准备工作完成。