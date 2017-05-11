---
title: 动态网页编程测试题
date: 2017-05-04 09:39:34
tags:
---
<h1 style="text-align: center">动态网页编程阶段测试</h1>
1. 行内元素和块级元素的具体区别是什么？行内元素的 padding 和 margin 可设置吗？
	> 1.  行内元素在一行上显示,块级元素独占一行
	> 2. 行内元素不可以设置宽高,要想设置宽高必须先转换成块级元素或者行内块,块级元素可以设置宽和高
	> 2. 块级元素可以设置margin和padding,行内元素只能设置左右的margin和padding,不可以设置上下的margin和padding

2. 如何垂直居中一个浮动元素?
	```html
	<!DOCTYPE html>
	<html lang="en">
	<head>
	<meta charset="UTF-8">
	<title>垂直水平居中</title>
	<style type="text/css">
		.box{
			width: 200px;
			height: 200px;
			background-color: red;
			float: left;
			position: absolute;
			top: 50%;	/*让div的左上角距离上面50%*/
			left: 50%;	/*让div的左上角距离左面50%*/
			margin-left: -100px;  /* 应为只是左上角到啦,多移动啦自身的一半,所以我们还要让他回去 */
			margin-top: -100px;
		}
	</style>
    </script>
    </head>
    <body>
	<div class="box"></div>
    </body>
	<script type="text/javascript">
		var bod=document.getElementsByTagName("body")[0]

		bod.style.height=window.innerHeight
		bod.style.width=window.innerWidth
	</script>
    </html>

	```
    **[点击查看效果](/anli/0505/divjuzhong.html)**
3. display:none 与 visibility:hidden 的区别是什么？
	>  display:none 与 visibility:hidden 都可以隐藏一个元素,display:none隐藏后元素不占位置, visibility:hidden隐藏后元素占位置
	
4. Ajax 的核心是什么?最大的特点是什么?
	> Ajax 的核心是XMLHttpRequest
	> 最大的特点是实现不刷新页面,可以改变局部页面
	
5. 看下列代码输出为何？解释原因。

	```javascript
	var a;
	alert(typeof a); 
	alert(b); 
	```
	> alert(typeof a)输出undefined,变量被定义,没有赋值,那么变量值就是undefined,数据类型也就是undefined;
	> alert(b) 报错,找不到b;要想使用,必须声明
	
6. 看代码给答案。

	```javascript
	var a = new Object();
	a.value = 1;
	b = a;
	b.value = 2;
	alert(a.value);
	```
	> 输出2;应为b=a;这时候b和a都是指向的相同的对象,b.value发生改变,a.value也发生改变
7. 看代码给答案

	```javascript
	function f1(){
        var tmp = 1;
        this.x = 3;
        console.log(tmp);
        console.log(this.x)}
    var obj = new f1();
    console.log(obj.x) 
    console.log(f1());
    console.log(x);
	```
	> this指向问题: 
	> var obj = new f1()时this指向f1沟照函数的实例,这个时候的this.x其实就是obj.x;
	>   console.log(f1())中,f1()是普通函数调用,这时候的this指向window,this.x也就是window.x,相当于var x
	
8. 	看代码给答案
	
	```javascript
	//第一题
	function fn(){
		console.log(a)
		var a
		a=5;
		console.log(a)
		return a	
	}
	console.log(typeof fn())
    //变量提升问题: 在第一次console.log(a),虽然前面没有出现a,但是在页面上有var a,
     // 把var a提上到啦上面,上面的代码相当于**下面代码:**
	```
	```javascript
	function fn(){
		var a
		console.log(a)
		a=5;
		console.log(a)
		return a	
	}
	console.log(typeof fn())//fn有一个返回值,返回a,也就是5;tyoeof 5,所以应该是number
	```
	```javascript
	//第二题:
	function bar() {
	return foo;
	foo = 10;
	function foo() {}
	var foo = 11;
	}
	alert(typeof bar());
	```
    > 同时存在变量和函数,函数的权重大于变量;所以返回的是function
    
    
8. 已知数组 var stringArray = [ “This” , “is” , “Baidu” , “Campus” ]，Alert 出”This is Baidu Campus”?
	> alert(stringArray.join(" "))
	
9. 截取字符串 abcdefg 的 efg?
	> "abcdefg".slice(4)
	> 字符串方法多多,自己看
10. 写一个三元运算, 并解释如何执行
	> a>b? 语句1:语句2
	> 如果a>b成立,就执行语句1,不成立执行语句2
	
11.  this在函数中的指向问题?
	> 1. 在普通函数调用中this指向window
	```javascript
	function f1(){
			this.a=5
		}
		f1(); //普通函数调用,this指向window,也就是window.a,window.a相当于全局变量var a
	```
	> 2. 函数被当做构造函数使用时,this指向构造函数的实例
	```javascript
	function fn(){
		this.name="张三"
	}
	var obj=new fn();//构造函数中的this指向啦它的实例;这个里面obj就是它的实例;那么this.name就相当于obj.name 
	```
	> 3. 当函数被当做对象方法调用的时候,this指向调用它的对象
		```javascript
		var obj={}
		function f1(){
			this.name="张三";
		}
		obj.seyHi=f1;
		obj.seyHi(); //这时候的this指向啦调用它的对象.this.name="张三"就相当于obj.name="张三";
		console.log(obj.name)
		```
		
12.  ”==”和“===”的不同?
	> == 判断的是值是否相等
	> === 判断的是值和数据类型是否相等
13.   如何创建一个对象?画出在内存中是如何表示的?
14. call 和 applay 的区别是什么？
	> call和applay都可以改变this的指向,第一个参数代表this的指向;不同点是传参的方式不同,call是依次往后传,以逗号分隔,applay传进去的是一个数组,数组中的每一向是代表要传入的参数;
15. 数组方法 pop() push() unshift() shift()分别是什么意思?
16. typeof返回哪写数据类型?返回值得类型是什么? 
17. 把 Script 标签 放在页面的最底部的 body 封闭之前 和封闭之后有什么区别？浏览器会如何解析它们？
	> 没有区别;浏览器解析时都会把他放到body封闭之前

18. 闭包的缺点是什么?如何解决?
	> 应为闭包的特性会照成在闭包中的变量常注内存,所有如果频繁的使用闭包会造成性能问题,在ie中会造成内存泄露;解决方法是当不使用后,让它等于null;
	
19. get提交和post提交有什么区别?
	> 1. get提交提交的内容在地址栏,post是在内部提交,post比get提交更加安全
	> 2.  get提交有大小限制;post提交理论上大小是不限制的;

20. 用正则表达式，写出由字母开头，其余由数字.字母.下划线组成的长度为 6~30 的字符串？
	> /^[a-zA-Z][0-1A-Za-z_]{5,29}/	

----------


# 
* 输出今天的日期，以 YYYY-MM-DD 的方式,比如今天是 2014 年 9 月 26 日，则输出 2014-09-26
	>   
		```html
		<!DOCTYPE html>
		<html lang="en">
		<head>
	    <meta charset="UTF-8">
	    <title>Title</title>
		</head>
		<body>
		<script>
	    var date=new Date();
	    var YY=date.getFullYear();
	    console.log(YY);
	    var MM=date.getMonth();
	    if(MM<10){
        MM="0"+(MM+1);
	    }else {
        MM=MM+1;
	    }
	    var DD=date.getData();
	    if(DD<10){
	        DD="0"+DD;
	    }
		document.write(YY+"-"+MM+"-"+DD);
		</script>
		</body>
		</html>
		```
   **[点击查看效果](/anli/0505/date.html)**
		 
* 生成 5 个不同的随机数,并且输出到页面上；

	> 
	```html
	<!DOCTYPE html>
	<html lang="en">
	<head>
    <meta charset="UTF-8">
    <title>Title</title>
	</head>
	<body>
	<div id="box"></div>
	<script>
	    var  box=document.getElementById("box");
	    for(var i=0;i<5;i++){
        num=Math.random();
        box.innerHTML+=num+"</br>"
	    }
	</script>
	</body>
	</html>
	```
	**[点击查看效果](/anli/0505/MathRANDOM.html)**