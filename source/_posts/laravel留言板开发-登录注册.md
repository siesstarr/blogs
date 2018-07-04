---
title: laravel留言板开发-登录注册
date: 2018-01-18 14:03:00
categories:
- laravel
- 正文
---

# laravel留言板开发-登录注册

当用户在查看一个网页时，一个完整的访问过程如下。
1. 打开浏览器在地址栏输入 URL 并访问。
2. 路由将 URL 请求映射到指定控制器上。
3. 控制器收到请求，开始进行处理。如果视图需要动态数据进行渲染，则控制器会开始从模型中读取数据。
4. 数据读取完毕，将数据传送给视图进行渲染。
5. 视图渲染完成，在浏览器上呈现出完整页面。

## 路由

所以我们需要使用路由，将不同的url请求转发给不同的控制器处理。
打开`/resources/views`目录，这个目录是后续放置视图的地方，将里面的welcome视图删除掉。
打开`/routes/web.php`文件，里面默认有个welcome的路由，删除掉。
编辑路由：
```
Route::get('/', 'StaticPagesController@home' );
Route::get('/login', 'StaticPagesController@login' );
Route::get('/registered', 'StaticPagesController@registered' );
```
`StaticPagesController`为控制器的名字，当收到get请求，路径为`/`时，改请求由`home`方法处理。

## 控制器

在上面在路由中写到了一个控制器，通过命令来创建这个控制器：
```
php artisan make:controller StaticPagesController
```
生成的控制器路径为：
```
C:\laravel\app\Http\Controllers
```
编辑内容为：
```
	public function home()
    {
        return 'home';
    }

    public function login()
    {
        return 'login';
    }

    public function registered()
    {
        return 'registered';
    }
```
分别打开`http://127.0.0.1/`、`http://127.0.0.1/login`、`http://127.0.0.1/registered`，可以看到页面上显示对应的字符。
接下来使用视图代替控制器中的返回字符。

## 视图

在`C:\laravel\resources\views`下新建文件夹`static_pages`用来存放静态视图。
新建视图`home.blade.php`、`login.blade.php`、`registered.blade.php`，注意，视图后缀为`.blade.php`。
编辑`home.blade.php`：
```
<!doctype html>
<html lang="zh">
<head>
    <meta charset="UTF-8">
    <title>主页</title>
</head>
<body>
<h1>主页</h1>
</body>
</html>
```
编辑`login.blade.php`：
```
<!doctype html>
<html lang="zh">
<head>
    <meta charset="UTF-8">
    <title>登录</title>
</head>
<body>
<h1>登录</h1>
</body>
</html>
```
编辑`registered.blade.php`：
```
<!doctype html>
<html lang="zh">
<head>
    <meta charset="UTF-8">
    <title>注册</title>
</head>
<body>
<h1>注册</h1>
</body>
</html>
```
修改路由中的返回值为对应的视图：
```
    public function home()
    {
        return view( 'static_pages/home' );
    }

    public function login()
    {
        return view( 'static_pages/login' );
    }

    public function registered()
    {
        return view( 'static_pages/registered' );
    }
```
然后再次访问`http://127.0.0.1/`、`http://127.0.0.1/login`、`http://127.0.0.1/registered`可以看到网页中显示的是对应的内容。

## 优化视图

在视图中我们使用了大量的重复代码，使代码变的很笨重，这样很麻烦，我们可以单独建一个默认视图存放通用代码。
在views下新建文件夹layouts，用来存放默认视图，然后在目录下新建文件`default.blade.php`：
```
<!doctype html>
<html lang="zh">
<head>
    <meta charset="UTF-8">
    <title>@yield( 'title','headline' ) - 留言板 </title>
</head>
<body>
@yield( 'content' )
</body>
</html>
```
修改`home.blade.php`：
```
@extends( 'layouts.default' )
@section( 'title','主页' )
@section( 'content' )
    <h1>主页</h1>
@stop
```
修改`login.blade.php`：
```
@extends( 'layouts.default' )
@section( 'title','登录' )
@section( 'content' )
    <h1>登录</h1>
@stop
```
修改`registered.blade.php`：
```
@extends( 'layouts.default' )
@section( 'title','注册' )
@section( 'content' )
    <h1>注册</h1>
@stop
```