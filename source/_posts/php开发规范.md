---
title: php开发规范
date: 2018-01-18 14:25:40
categories:
- 常用知识
---

# php开发规范

## 规范前言篇

标准化不是特殊的个人风格，它让程序员可以了解任何代码，弄清程序的状况；新人可以很快的适应环境；防止新接触php的人一次次的犯同样的错误；在一致的开发环境下，可以减少人们犯错的机会。本规范的标准在绝对多数应用上为仿照java 技术体系，因为java 技术体系以其众多成功的案例成为大部分计算机应用层的工业标准。

## 命名定义篇

### 局部变量命名

使用英文名词、动词，以大写字母作为单词的分隔，其他的字母均使用小写，单词的首个字母使用小写，不使用下划线，例：
```
$repeatCount = ''; 
$delUserSql  = ''; 
```

### 全局变量命名

使用英文名词、动词，所有字母都使用大写，以下划线分隔每个单词，例：
```
define( 'WEBSITE_NAME', '名称' ); 
define( 'WEBSITE_URL',  '地址' )；
```

### 数组变量命名

使用英文名词、动词，以大写字母作为单词的分隔，其他的字母均使用小写，单词的首个字母使用小写，不使用下划线，以[]为后缀，尽量不要适用array关键字（现在都php7了，这种写法早就过时了）例：
```
$scopeArray  = []; 
$bookIdArray = []; 
```

### 静态变量命名

使用英文名词、动词，以大写字母作为单词的分隔，其他的字母均使用小写，单词的首个字母使用小写，不使用下划线，以字符串 Static为后缀，例：
```
function getDirectoryFile() 
{ 
static $fileArrayStatic  = ''; 
static $fileNumStatic  = ''; 
... 
} 
```

### 对象变量命名

使用类名称为变量前缀，所有字母都使用大写，以字符串_OBJECT为后缀，例：
```
$USERACCOUNT_OBJECT  = new UserAccount(); 
$PAINTINGORDER_OBJECT = new PaintingOrder(); 
```

### 类命名

使用英文名词，以大写字母作为词的分隔，其他的字母均使用小写，名词的首个字母使用大写，不使用下划线，（有多个单词组成采用驼峰命名法）例：
```
class UserAccount 
{ 
... 
} 
 
class PaintingOrder 
{ 
... 
} 
```

### 方法命名

使用英文名词、动词，以大写字母作为词的分隔，其他的字母均使用小写，单词的首个字母使用小写，不使用下划线，例：
```
class UserAccount 
{ 
function isAccountOk() 
{ 
  ... 
} 
 
function addAccount() 
{ 
  ... 
} 
} 
```

### 方法中参数命名

使用英文名词、动词，以大写字母作为词的分隔，其他的字母均使用小写，单词的首个字母使用小写，不使用下划线，三种类型（public、private、protected）以关键字为开头， 例： 
```
class UserAccount 
{ 
public/protected/private function isAccountOk( $accountName ) 
{ 
  $this->accountName = $accountName; 
  ... 
} 
 
public/protected/private static function addAccount( $inputDataArray ) 
{ 
  $this->inputArray = $inputDataArray; 
  ... 
} 
} 
```

### 类属性命名

使用英文名词、动词，以大写字母作为词的分隔，其他的字母均使用小写，单词的首个字母使用大写，不使用下划线，对于类属性为某个对象变量，则以字符串 Object为后缀，例： 
```
class UserAccount 
{ 
public $accuntName = ''; //公共变量 其他私有的、受保护的类似
public static $inputArray  = ''; //公共的静态变量命名规范，其他类似

public/protected/private function IsAccountOk() 
{ 
  ... 
} 
 
public/protected/private static function AddAccount() 
{ 
  ... 
}  
} 
```

## 语法书写篇

### 大括号{}规则

将大括号放置在关键词下方的同列处，例：
```
if ( $condition ) 
{ 
... 
}

```
不使用此种方式：
```
if ( $condition ) { 
... 
} 
```

### 代码缩进规则

使用制表符缩进（TAB 键）或四个空格。如果缩进层数大于四的时候，请重新设计该项务逻辑的算法。

### 小括号规则
不要把小括号和关键词、方法名、方法参数紧贴在一起，要用一个空格分隔，例：
```
if ( $condition ) 
{ 
... 
} 
 
function addAccount( $inputDataArray ) 
{ 
... 
} 
```
由于小括号与关键词等紧贴容易被看成是一体，因此不要使用以下方式，例：
```
if ($condition) { 
... 
} 
```

### if...else... 规则

通常最好有一个else块以用于处理未处理到的或未知的其他情况，即使条件处理语句只有一个也必须使用大括号{}，例：
```
if ( $condition1 ) 
{ 
... 
}  
else if ( $condition2 ) 
{ 
... 
... 
}  
else 
{ 
... 
} 
```
尽可能避免以下使用方式，例：
```
if ( $condition1 ) 
... 
else 
... 
```

### switch 规则

每个case块结束处必须加上break，而default总应该存在处理未知情况，例：
```
switch( $condition ) 
{ 
case $value1: 
  ... 
  break; 
case $value2: 
  ... 
  break; 
default: 
  ... 
  break; 
} 
```

### 声明定位规则

声明代码块需要对齐，且初次使用变量时需要初始化，例： 
```
$tableName   	 = ''; 
$databaseObject	 = ''; 
```
不使用以下方式，例： 
```
var $tableName; 
var $accuntName = ''; 
var $databaseObject = ''; 
```

## 其它说明篇 

所有类方法必须有返回值，除结果简单外返回 true 或者 false 之外，其它方法应返回不同的值以交作流程进一步处理。 
html的form表单统一不设置submit按钮的名称属性（name） 。 
html的form表单各个元素名称与数据库字段保持一致。 
每行一个语句。不要采用缺省方法测试非零值，必须显式测试，例：
```
if ( false != $this->IsAccountOk() ) 
{ 
... 
} 
else 
{ 
... 
}
```
不要使用以下方式，例：
```
if ( $this->IsAccountOk() ) 
{ 
... 
} 
else 
{ 
...  
}
```
不要使用三元逻辑符  ? :，但对变量的赋值除外，例：
```
$_GET['act'] = !empty( $_GET['act'] ) ? $_GET['act'] : 'v_login'; 
```
统一使用<?php ?>，禁止使用<? ?>格式。 
对于get、post、session类型变量，必须使用$_GET、$_POST、$_SESSION 方式定义和调用。  
尽可能使用单引号''而不是双引号""。 
使用完毕后的数组变量、对象变量、查询集合必须马上使用 unset()、free_result()释放资源。  
一个php文件只能包含一个类定义编码，以类名称作为文件名称。 
html文件必须通过w3c的html4 检测认证（http://validator.w3.org/ ） 。 
如果发觉您在程序中的命名只有少量能和其对应事物相匹配的话，请重新设计系统。 
在为类命名前首先要知道它是什么。如果通过类名提供的线索，您还是想不起这个类是什么的话，那么您的设计是做得不够好。 
超过三个单词组成的混合名是容易造成系统各个实体间的混淆，请重新设计类。 
通常每个方法只执行一项逻辑动作事务，所以对它们的命名应该清楚的说明它们是做什么的：用checkForErrors()代替  errorCheck()，用 dumpDataToFile()代替 dataFile()。这么做使功能和数据成为更可区分的物体。

## 程序注释篇

注释采用PHPDocument标准，以备后期生成文档。
```
	/**
　　* 函数add,实现两个数的加法
　　*
　　* 一个简单的加法计算，函数接受两个数a、b，返回他们的和c
　　*
　　* @param int 加数
　　* @param int 被加数
　　* @return integer
　　*/
　　function Add($a, $b)
　　{
　　return $a+$b;
　　}
```
a. 注释的形式必须是：
```
　　/**
　　* XXXXXXX
　　*/
```
b. 对于引用了全局变量的函数，必须使用glboal标记。
c. 对于变量，必须用var标记其类型（int,string,bool...）
d. 函数必须通过param和return标记指明其参数和返回值
e. 对于出现两次或两次以上的关键字，要通过ingore忽略掉多余的，只保留一个即可
f. 调用了其他函数或类的地方，要使用link或其他标记链接到相应的部分，便于文档的阅读。
g. 必要的地方使用非文档性注释，提高代码易读性。
h. 描述性内容尽量简明扼要，尽可能使用短语而非句子。
i. 全局变量，静态变量和常量必须用相应标记说明

## 数据库应用篇

数据库的设计必须符合三个范式（极端要求常用高速时考虑单独设置记录表除外）。 
表的命名应尽量和程序的命名有关联（如：表名（t_account），在设计程序时，程序命名尽量写成以account做为关键字的书写）
设计表的字段时应添加注释，说明字段的作用
数据库名称应该由概述项目内容的小写英文名词组成，以下划线分隔单词， 避免跨平台时可能出现的大小写错误。数据表名称应该由物件对象名称的小写英文名词组成（尽可能对应系统中的业务类名称），以下划线分隔单词，避免跨平台时可能出现的大小写错误。 
数据表的字段应避免使用varchar、 text等不定长的类型，时间信息的字段使用 unix tiemstamp类型存储。 查询数据时禁止使用*通配符避免占用资源加速处理速度，尽量避免使用临时表。 查询数据连接多表时各资源应该使用全名称，即 tableName.fieldName，而不是 fieldName。 SQL语句应尽可能符合ansi92标准，避免使用特定数据库对 SQL语言的扩充特性。 开发结束后，必须针对SQL查询语句的条件语句部分（where）添加索引， 
须匹配多个条件的应该使用聚合索引。 索引的组成应由左至右匹配条件语句的顺序。 
严禁盲目添加索引，避免减慢数据插入的速度、增大占用空间及减慢查询速度。 
每当数据库（表）发生结构性变化时须登记保存；日常须定时（不超过三个工作日）备份数据库结构及其数据。 
1. 给php变量赋值为字符串，尽量用单引号。单引号速度要快很多。 
2. 给php变量赋值时，值中带变量，就的用双引号了，双引号能自动解析变量，方便很多。  
  如$b=blue; $a="php$b"; echo $a;  输出 phpblue （单双引号各有千秋啊） 
3. html内尽量用双引号，无论多长拿到 php中首尾加单引号就行，甭怕错。
