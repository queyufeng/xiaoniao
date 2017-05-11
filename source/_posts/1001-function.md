---
title: JS函数,对象/类,定时器
date: 2017-04-14 16:51:14
tags: 
    - JavaScript
    - 前端基础
    - 动态网页编程
categories: 
    - 学习
    - 动态网页编程
---

#    JS函数,对象/类,定时器
## JS函数
* JavaScript函数定义：

	> 不带参数的函数 
	
	```javascript
	function functionname()
	{
	//这里是要执行的代码
	}
	```
	
	> 带参数的函数
	
	```javascript
		function myFunction(var1,var2)
		{
		//这里是要执行的代码
		}
	```
	> 调用不带参数的函数
	`myFunction()`
	> 调用带参数的函数
	`myFunction(argument1,argument2)`
	
	**在调用函数时，您可以向其传递值，这些值被称为参数。您可以发送任意多的参数，由逗号 (,) 分隔**

* 带有返回值的函数

	```javascript
	function myFunction()
	{
	var x=5;
	return x;
	}
	var myVar=myFunction();
	```
	> myVar 变量的值是 5也就是上面的函数返回值5


* 匿名函数**(匿名函数就是没有实际名字的函数)**
	
	```javascript
	//匿名函数
	(function() {
	alert('water');
	})();
	```
	* 匿名函数的调用

	> 要调用一个函数，我们必须要有方法定位它，引用它。所以，我们会需要帮它找一个名字。
	```javascript
	var abc=function(x,y){
	return x+y;
	}
	alert(abc(2,3));
	```
## JS对象/类
* 对象:
	*  面向对象编程的核心
	*  表示现实世界中的实体
	*  为计算机应用程序提供实用基础
	*  完成特定任务
> 对象是存在的具体实体，具有明确定义的状态和行为。
> 对象：用来描述客观事物的一个实体，由一组属性和方法构成

* 类
	> 具有相同属性和方法的一组对象的集合类是对象的类型
	>类是模子，确定对象将会拥有的特征（属性）和行为（方法）
	
	*  类的创建

		```javascript
		function class1(){
		//类成员的定义及构造函数
		}
		```
		* 创建一个学生类
		* 每个学生都有年龄、姓名、班级和爱好。用类的思想编写学生类

		```javascript
		function Students (name,age,grade,hobby){
		this.name=name; //姓名
		this. age=age; //年龄
		this. grade=grade; //班级
		this. Hobby=hobby; //爱好
		}
		```
		* 为Students引用类型创建几个属性getName和setName方法：
		```javascript
		Students.prototype.getName=function(){
		return this.name;
		}
		Students.prototype.setName=function(name){
		this.name=name;
		}
		```
		* 创建和使用引用类型的实例
		
		> 创建对象语法：var 对象名 = new 类名();

		```javascript
		// 使用对象示例：
		var Student01=new Students("张三","20","2","唱歌");
		var Student02=new Students("李四","30","3","跳舞")
		```
		* 引用对象成员：使用“ .” 进行以下操作 类的创建不引用
		> 属性：对象名.属性
		> 方法：对象名.方法名()
		
		* 调用getName ()方法及age属性等，并将结果输出到页面上：
		```javascript
		document.write("我叫："+Student01.getName()+"年龄:"+Student01.age+",所在班级："+Student01.getGrade()+"，我的爱好是："+Student01.getHobby()+"。 ");
		```

## JS定时器
> JavaScript中有两类计时器，即一次性计时器和定期
触发计时器。

> 一次性计时器仅在指定的时间后触发一次(`setTimeout()`)
> 定期触发计时器是每隔一定时间就触发一次(`setInterval()`)

* 一次性计时器：
	* 使用window对象的setTimeout()方法

		```javascript
				Window.setTimeout(“function(){}”,delay)
		```
	* setTimeout()方法接收两参数，第一个是要执行的JavaScript代码，可以是一个函数，也可以是几个函数，函数间用“；”隔开即可。
	```javascript
	//页面加载3秒后触发的计时器
	function hello(){
	alert("hello");
	}
	window.setTimeout(hello,3000);
	```
	* 清除定时器
		* `clearTimeout(定时器id)`
 
 * 定期触发计时器
 > setInterval()方法的参数不setTimeout()方法相同，但第二
个参数丌是计时器触发前的时间，而是计时器的触发间隔，
该间隔以毫秒为单位。
`Var myTimerID=setInterval(“ myFunction(){}”,5000);`

	* 清除定时器
	`window.clearInterval(timer2)`

> 两者的区别在:  一个只执行一次,另一个没过一段时间就 执行一次;


## 总结
* 函数

	> 不带参数的函数,带参数的函数,匿名函数,函数返回值 

* 对象, 类

   > 概念,创建,使用

* 定时器

   >  概念,创建,使用`setTimeout(), clearTimeout(),setInterval(),clearIearval()`
