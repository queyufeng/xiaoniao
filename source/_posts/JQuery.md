---
title: JQuery基础一
date: 2017-05-04 09:39:46
tags: 
    - JavaScript
    - 前端基础
    - 动态网页编程
categories: 
    - 学习
    - 动态网页编程
---
# jQuery基础1
## jQuery简介
* jQuery 是一个 JavaScript 凼数库。
* jQuery 极大地简化了 JavaScript 编程。
* jQuery可在jquery.com中下载。
* 使用jQuery须将jQuery载入到网页中：
> `<script type=“ text/javascript”src=“jquery.js”></script>`

## 文档就绪函数
写法一：
> `$( function () {  /* 执行代码*/   } )`

写法二：
> ` $(document).ready(function(){ /*执行代码 */ });`

### 思考问题：
**`$( function () { } ) ,$(document).ready()与window.onload的区别？`**
答： 
> 1. jq的\$(function(){})是\$(document).ready(function(){})的简写,代表的是DOM结构加载完毕后就会执行。而window.onload必须等到页面内（包括图片的）所有元素加载到浏览器中后才能执行；**window.onload**和$(window).load(function(){})是一样的作用
> 2. 编写个数不同：window.onload不能同时写多个，如果有多个window.onload，则只有最后一个会执行，它会把前面的都覆盖掉。$(document).ready(function(){})则不同，它可以编写多个，并且每一个都会执行。


----------


## JQuery语法:
> `$(selector).action()`
 
* 美元符号定义 jQuery
* 选择符（selector）“查询”和“查找” HTML 元素
* jQuery 的 action() 执行对元素的操作 （方法）

```javascript
例： $(this).hide()// - 隐藏当前元素
$("p").hide() //- 隐藏所有段落
```

## 选择器
* id：根据给定的id匹配一个元素
> 例： `$("#test")`选取`id`为`test`的元素

*  .class：根据给定的类名匹配元素
> 例：`$(".test")` 选取所有`class`属性值为`test`的元素

*  element：根据给定的元素名匹配元素
> 例： `$("div")`选取所有`div`元素

* selector1,selector2,….. :将每一个选择匹配到的元
素合并后一起返回
> 例： `$(“ div,span,p”)` 选取所有div，span，p元素

* ：匹配所有的元素
> 例：`$(“*”)`选取所有元素

 **[点击查看更多选择器](http://www.w3school.com.cn/jquery/jquery_ref_selectors.asp)**


----------


## 事件
> 事件处理程序指的是当 HTML 中发生某些事件时所调用的方法

* 鼠标移入/移出事件(hover)
**语法：**
	```javascript
	$(selector).hover(function(){
	//鼠标移入时执行的代码；
	}，function(){
	//鼠标移出时执行的代码；
	})
	```
	**例如：**
	```javascript
	$(“div”).hover(function(){
	$(“ ul”).slideDown();//鼠标经过div，ul展开
	},function(){
	$(“ ul”).slideUp();//鼠标移开div，ul收起
	})
	```
* 切换元素的可见状态事件(toggle)

	> **toggle 语法格式与hover相同**

* 单击事件(click)
	**语法**
	> `$(selector).click(function( ){/*单击被选元素时执行的代码*/；})`

* 获得/失去焦点事件(focus/blur)
* 鼠标移入/移出mouseover/mouseout
* 滚动事件 scroll()
* 重置resize()
> 以上事件的语法格式均不click事件相同，只需要修改事件名
> **[点击查看更多事件方法](http://www.w3school.com.cn/jquery/jquery_ref_events.asp)**


----------
## 常用方法

* 显示/隐藏（show()/hide()）
语法：
	> `$(selector).hide(speed,callback);`  

1. 可选的 speed 参数规定隐藏/显示的速度，可以取以下值：
"slow"、 "fast" 或 毫秒。
2. 可选的 callback 参数是隐藏或显示完成后所执行的凼数名称。

	**例如**
	```javascript
	//无参数：
	$(“div”). hover(function(){
		$(“p”).show()
	}，function(){
		$(“p”).hide()
	})

	//有参数：
	$("div").hover(function(){
		$("p").show(500,showalert)
	},function(){
		$("p").hide(500,hidealert)
	})
	```


**下边没有写语法的均不显示/隐藏语法相同，只需改方法名**
**下边speed,callback没有注释均不以上解释相同**
* 显示/隐藏（toggle()）
	
	> toggle() 方法可用来切换hide()和show()
	
* 淡入/淡出（fadeIn()/fadeOut()）
* 淡入/淡出切换（fadeToggle()）
	> fadeToggle() 方法可以在fadeIn()不fadeOut()方法之间进行切换

* 有透明度的淡入/淡出（fadeTo()）
**语法：**
> `$(selector).fadeTo(speed,opacity,callback);`
1. speed为必选项 参数规定效果的时长。它可以取以下值："slow"、
"fast" 或毫秒。
2. opacity为必选项 参数将淡入淡出效果设置为给定的不透明度
**（值介于 0 不 1 之间）。**
3. 可选的 callback 参数是该凼数完成后所执行的凼数名称。
例：`$(“div”).fadeTo(“slow”,0.5)`

* 上/下滑动(slideUp()/slideDown())
* 上/下滑动(slideToggle())

	> slideToggle() 方法可以在 slideDown() 不 slideUp()方法之间进行切换

* 动画(animate())
**语法：**
	>` $(selector).animate({params},speed,callback);`
	
1. animate() 方法用于创建自定义动画
2. 必选项 params 参数定义形成动画的 CSS 属性
3. speed，callback 参数用法均与上面相同生成动画的过程中可同时使用多个属性

	**例如**
	```javascript
	$(“div”).click(function(){
		$(this).animate({“width”:”500px”
	,”height”:”300px”,”color”:”#fff”},500)
	})
	```

* 停止动画（stop()）

	**语法：**
	> $(selector).stop(stopAll,goToEnd);

1. 可选的 stopAll 参数规定是否应该清除动画队列。默认是 false，即仅停止活动的动画，允许任何排入队列的动画向后执行。
2. 可选的 goToEnd 参数规定是否立即完成当前动画。默认是 false。
3. jQuery stop() 方法用于停止动画或效果，在它们完成之前。
stop() 方法适用于所有 jQuery 效果函数，包括滑动、淡入淡出和自定义动画。 

* 延迟（delay()）

	**语法：**

	> $(selector).delay(speed,queueName)
	
	delay() 方法对队列中的下一项的执行设置延迟。speed不上相同，queueName可选。规定队列的名称。默认是 “ fx” ，标准效果队列，一般丌用。

	例：
	$(“ div”).show().delay().hide();

* 方法链接(chaining)
	> chaining是一种**链接技术**，允许我们在相同的元素上运行多条 jQuery 命令，一条接着另一条
	
	例：

	```javascript
	//例：
	$("div").css("background","#00f").slideUp(2000).slideDown(2000);
	```

## $(this)

> $(this)：代表的上下文对象是一个jquery的上下文对象，可以调用jquery的方法和属性值。

例：
```javascript
$("#textbox").hover(function(){
$(this).css("width","200px");//等同于$("#textbox").css("width","
},function(){
});
```

