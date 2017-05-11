---
title: JS赋值 运算比较 流程控制
date: 2017-04-10 22:48:08
tags: 
    - JavaScript
    - 前端基础
    - 动态网页编程
categories: 
    - 学习
    - 动态网页编程

---
<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width=330 height=86 src="//music.163.com/outchain/player?type=2&id=31445554&auto=1&height=66"></iframe>
# JS赋值 运算比较 流程控制
## 变量的声明与赋值
* 先声明变量再赋值

	> `var width`      `width=5`
	> `var` － 用于声明变量的关键字
	> `width` － 变量名
* 同时声明和赋值变量
	
	> `var catName= “ 皮皮”; var x, y, z = 10;` 

* 不声明直接赋值

	> `width=5`

## JS运算
### 运算符号
* 算数运算符(+,-,*,/,%,++,--)
* 赋值运算符(=,+=,-=,*=,/=,%=)
* 字符串连接符(+)
* 优先级:
> 优先级：（）>算术运算符（先乘除后加减）>赋值运算符
## JS比较
### 比较符号
* 比较运算符(>,<,>=,<=,==,===,!=,!==)
* 逻辑运算符(&&,||,!)
* 三目运算符:

	>  条件?语句1:语句2

## JS 流程控制
### 简介:
> 所谓的“流程”就是程序代码执行的顺序。在任何一种语言中，程序控制是必需的。它能使整个程序减少混乱，使之顺利按照其一定的方式执行。 JavaScript常用的控制流程有3种基本结构：**顺序结构**、**选择结构**、**循环结构顺序结构**,正常情况下，程序中的语句是按照书写顺序执行的，这种结构成为顺序结构。前面所例丼的程序都是顺序结构的程序。

### 选择结构
> 选择结构主要用判断语句来实现根据一定的条件决定进一步执行那些语句。 JavaScript提供了两种类型的选择结果语句，也成为判断语句：`if语句`和`switch语句`。一般来讲if语句用于从两条执行路线中选择其一执行,而switch语句用于从多条执行路线中选择其一执行。

* if语句
```javascript
if(条件){
//JavaScript代码;
}
```
* If条件语句
```javascript
if(条件){
//JavaScript代码;
}else{
//JavaScript代码;
}
```
* If…else if…else语句
```javascript
if (条件 1)
{
当条件 1 为 true 时执行的代码
}
else if (条件 2)
{
当条件 2 为 true 时执行的代码
}
else
{
当条件 1 和 条件 2 都不为 true 时执行的代码
}
```
* switch语句
```javascript
switch(n)
{ case 1:
执行代码块 1
break;
case 2:
执行代码块 2
break;
default:
n 与 case 1 和 case 2 不同时执行的代码
}
```

### 循环结构
> 前面介绍的if语句和switch语句，都属于条件判断语句。即在条件为真的情况下每行脚本只有一次执行的机会。对于实际情况中，需要根据条件或计数器来重复执行多行程序代码的能力，利用循环语句来实现。
在JavaScript中有两种主要类型的循环语句，`for循`
环和`while循环`

* for 循环

	```javascript
	for (语句 1; 语句 2; 语句 3)
	{
	被执行的代码块
	}
	```

	* 语句 1 在循环（代码块）开始前执行
	* 语句 2 定义运行循环（代码块）的条件
    * 语句 3 在循环（代码块）已被执行之后执行

* While 语句
```javascript
while (条件)
{
需要执行的代码
}
```

* Do…While语句
```javascript
do
{
需要执行的代码
}
while (条件);
```
> 在循环语句中，只有当循环条件表达式值为false时，循环语句才能结束，为了给for和while循环加入更多的使用程序，JavaScript包含有`break`和`continue语句`。这两个语句可用于改变循环的流程。
* Break语句 中断循环
* Continue语句 开始下一次循环

