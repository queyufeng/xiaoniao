---
title: javascript基本对象,数据类型,常量,变量
date: 2017-04-10 21:30:16
tags: 
    - JavaScript
    - 前端基础
    - 动态网页编程
categories: 
    - 学习
    - 动态网页编程

---
<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width=330 height=86 src="//music.163.com/outchain/player?type=2&id=33162226&auto=1&height=66"></iframe>
# javascript基本对象,数据类型,常量,变量

## javascript数据类型
* 基本数据类型
	1. Number
	2. String
	3. Boolean
	4. Null
	5. Undefined
* 混合数据类型
	* Object
* js中变量是松散类型的，因此有时我们需要检测变量的数据类型
* typeof操作符可以检测变量的数据类型（输出的是一个关于数据类型的字符串）

### 数字(Number)
* 介绍Number类型包含整数和浮点数（浮点数数值必须包含一个小数点，且小数点后面至少有一位数字）两种值
	> 例如:`var x1=34.00`; //使用小数点来写  
	> `var x2=34`; //不使用小数点来写

* 极大或极小的数字可以通过科学（指数）计数法来书写：
	> 例：`var y=123e5; // 12300000`  
	> `var z=123e-5; // 0.00123`

* NaN:非数字类型
	* 特点：涉及到的 任何关于NaN的操作，都会返回NaN
	* NaN不等于自身。
		> 例：`var ab = "a1";`  
		> `console.log(ab/10);// NaN`  
		> `console.log(NaN == NaN);// false;`





###字符串（string）
> 例：`var carname="Bill Gates";`  
>` var answer="He is called 'Johnny'";`

* 字符串是存储字符（比如 "Bill Gates"）的变量。
* 字符串可以是引号中的任意文本，可以使用单引号或双引号，只要不匹配包围字符串的引号即可
* **注： JavaScript对大小写敏感**





###布尔（boolean）
> 例：`var x=true  `
>` var y=false`
* 布尔（逻辑）只能有两个值：**`true`** 或 **`false`**。





### Undefined
* Undefined 这个值表示变量不含有值。
*　可以通过将变量的值设置为 null 来清空变量




### null
* null类型被看做空对象指针，null类型也是空的对象引用。
只有一个值，即null值，所以，在用typeof 操作符去检测
null类型的值时，结果是object类型。
如果你定义了一个变量，但是想在以后把这个变量当做一
个对象来用，那么最好将该对象初始化为null值

###对象（object）
* 对象由花括号分隔。在括号内部，对象的属性以名称和
值对的形式 (name : value) 来定义。属性由逗号分隔：
	> 例：var person={  
	> firstname : "Bill",  
	> lastname : "Gates“  
	> };

* 数组为混合数据类型中的一种

## 常量Constant：不变的值
* `const constantName = value1；`
	> 常量名首字符为字母或下划线，其后可有数字。 value1为直接量或表达式。

* 1个const关键字可定义1个或多个常量。
* 内置常量：JS中Infinity表无穷大的数值，-indinity表无穷小.NaN表非数值。
	> 例：const a = 10;  
	>  alert(a)

##变量
* 概念:变量是存取数字、提供存放信息的容器。对于变量，必须明确变量的命名、变量的类型、变量的声明及其变量的作用域。命名规范
* 变量命名规范:
	* 变量必须以字母或下划线开头，后可以跟字母、数字、下划线，不能有空格或特殊字符等。
	* 不用使用Javascript中的关键字作为变量，如var,true,double等。
	* 在对变量命名时，最好把变量的意义与其代表的意思对应起来，以免发现错误。

* 变量的类型：
	* 整数变量：x=100;
	* 字符串变量：y=“125”
	* 布尔型变量：xy=True
	* 实型变量：cost=19.5

* 变量的声明
	* JavaScript可以在使用前先声明，并可赋值。变量声明用可用命令`var`;
		> 例：`var mytest;`  
		> 该例子定义了一个mytest变量，但没有赋予其值  
		> 例：var mytest=“This is a book”
		> 该例子定义了变量并为其赋予了值。

* 变量的作用域：
	* 变量分为全局变量和局部变量。
		* 全局变量是定义在所有函数体乊外，其作用范围是整个函数
	* 局部变量是定义在函数体乊内，只对其该函数是可见的，而对其它函数则是不可见的。
	* 函数体内可以访问父级函数的变量，父级函数不能访问子函数的变量。
**注：在声明变量时凡是没有var关键字，而直接赋值的变量均为全局变量**


##　JavaScript 的基本对象
> 对象包括：系统标准类对象 和 自定义对象

* 标准类对象:
	* 字符串对象String、
	* 日期对象Date、
	* 数组对象Array、
	* 数字对象Number 、
	* 数学对象Math、
	* 正则表达式对象RegExp

*自定义类对象:自定义的包含属性和方法的对象

```javascript

例：var person={
firstname : "Bill",
lastname : "Gates",
eat : function(){}
};

```    
    