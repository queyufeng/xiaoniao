---
title: jQuery2
date: 2017-05-10 17:42:35
tags: 
    - JavaScript
    - 前端基础
    - 动态网页编程
categories: 
    - 学习
    - 动态网页编程
---
# JQuery 基础二

## 鼠标键盘事件
* 鼠标事件

| 事件名称      |     描述|   举例说明|
| :-------- | --------:| :------: |
| mousedown|   当鼠标指针移动到元素上方，并按下鼠标按键时，会发生 mousedown事件|$("button").mousedown(function(){$("p").slideToggle()|
|mouseup |当在元素上放松鼠标按钮时，会发生mouseup 事件|$("button").mouseup(function(){$("p").slideToggle();})|
|mouseenter | 当鼠标指针穿过元素时，会发生mouseenter 事件|$("p").mouseenter(function(){$("p").css("backgroundcolor","yellow"); });|
|mousemove| 当鼠标指针在指定的元素中移动时，就会发生 mousemove 事件|$("button").mousemove(function(){})|
|event.pageX| pageX() 属性是鼠标指针的位置，相对于文档的左边缘|$(document).mousemove(function(e){$("span").text("X: " +e.pageX});|
|event.pageY pageY()|属性是鼠标指针的位置，相对于文档的上边缘|$(document).mousemove(function(e){ $("span").text(“Y: " +e.pageY});|
|mouseover| 当鼠标指针位于元素上方时，会发生mouseover 事件|$("button").mouseover(function(){})|
|event.preventDefault();|阻止元素发生默认的行为 |$("a").click(function(event){event.preventDefault(); });|

* 键盘事件

| 事件名称| 描述  |   举例说明   |
| :-------- | --------:| :------: |
| keydown |当按钮被按下时，发生 keydown 事件| $("input").keydown(function(){$("input").css("color","#FFFFCC"); });|
|keypress| 当按钮被按下时，会发生该事件。它发生在当前获得焦点的元素上|$("input").keypress(function(){$("span").text(i+=1);});|
|keyup| 当按钮被松开时，发生 keyup 事件。它发生在当前获得焦点的元素上。|$("input").keyup(function(){$("input").css("color","#D6D6FF");});|

## 标签的添加删除
* 添加元素：
	*  append() - 在被选元素的尾部插入内容
	*  appendTo() – 在被选元素的结尾（仍然在内部）插入指定内容
	
	```javascript
	$(“p”).append(“ World.”);
	//如p标签的原文本为:“Hello”
	//则现文本为： Hello World.等同于
	$("<b>World.</b>").appendTo("p"
	```
* 添加元素
	* prepend() - 在被选元素的开头插入内容
	* prependTo() - 在被选元素的开头（仍位于内部）插入指定内容
	
	```javascript
	$(“p”).prepend(“ 你好，”);
	//如p标签的原文本为:“ 李明”
	//则现文本为： 你好，李明等同于
	//$("你好").prependTo("p");
	```
* 添加元素
	*	append()和prepend()方法添加若干新元素

	```javascript
	function appendText() {
	var txt1=“<p>Text.</p>”; // 以 HTML 创建新元素
	var txt2=$(“<p></p>”).text(“Text.”); // 以 jQuery 创建新元素
	var txt3=document.createElement(“p”); // 以DOM 创建新元素
	txt3.innerHTML="Text.";
	$("p").append(txt1,txt2,txt3); // 追加新元素 
	}
	```
* 添加元素 
	* after() – 在被选元素之后插入内容
	* before – 在被选元素之前插入内容

* after()和before() 方法添加若干新元素
	```javascript
	function afterText() {
	var txt1=“<b>I </b>”; // 以 HTML 创建新元素
	var txt2=$(“<i></i>”).text(“love ”); // 通过 jQuery 创建新元素
	var txt3=document.createElement(“big”); // 通过 DOM 创建新元素
	txt3.innerHTML="jQuery!";
	$("img").after(txt1,txt2,txt3); // 在 img 之后插入新元素
	 }
	```
#### 思考问题：
> append()和preappend()与after()和before()区别：
	 append() & prepend()是在元素内插入内容（该内容变成该元素的子元素或节点）
	after() & before()是在元素的外面插入内容（其内容变成元素的兄弟节点）

* 删除元素
	* remove() - 删除被选元素（及其子元素）
	
		> 例：$(“#div1”).remove(); //删除的是div1的

	*  remove() – 过滤被删除的元素
		> remove() 方法也可接受一个参数，允许被删元素进行过滤。该参数可以是任何 jQuery 选择器的语法。
		`$(“p”).remove(“.italic”);//删除 class="italic" 的所有 <p> 元素`
		
* 删除元素
	* removeAttr()从被选元素中移除属性
	例：$("p").removeAttr("id");		

## 属性的获取设置
* 设置内容 – text() 、 html()、以及val()
	* 获取内容语法：$(selector).text()
	* 设置内容语法：$(selector).text(“设置内容” )  
		
		> 其它两个方法语法一样
		
* text()、 html() 以及 val()的回调函数
回调函数由两个参数：被选元素列表中当前元素的下标，以及原始（旧的）值。然后以函数新值返回您希望使用的字符串。

```javascript
$("#btn1").click(function(){
$("#test1").text(function(i,origText){
return "Old text: " + origText + " New text: Hello " +
" world! (index: " + i + ")";
});
});
```

* 获取属性或设置属性 – attr()
	* 获取属性语法：$(selector).attr(“ 属性名” )
	* 设置属性语法：$(selector).attr(“属性名”，“属性值” )
* attr()的回调函数
	* 回调函数有两个参数：被选元素列表中当前元素的下标，以及原始（旧的）值。然后以函数新值返回您希望使用的字符串
```javascript
$("button").click(function(){
$("#taobao").attr("href", function(i,origValue){
return origValue + "/market/nvzhuang";
});
});
```
* css()方法设置或返回被选元素的一个或多个样式属性。
	* 返回CSS属性：
		语法：css(“ 属性名” )
		例：$(“p”).css(“color”)
	* 设置CSS属性：
		语法：css(“ 属性名”，“属性值” )
		例：$(“p”).css(“color” ，”#f00”)
	* 设置多个CSS属性：
		语法：css({“ 属性名”:“ 属性值” ,属性名”:“ 属性值” ,…})
		例   $(“p”).css({“color”:”#f00”,”background”:”#00f”)	
	
## Class的添加删除
* addClass() – 向被选元素中添加一个或多个class类
* removeClass() – 从被选元素删除一个或多个class类与addClass()用法相同
* toggleClass() – 对被选元素进行添加/删除class类的切换操作
	 
	> 该方法是对addClass()和removeClass()方法的切换

## jQuery编写图片轮播