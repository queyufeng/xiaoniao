---
title: jQuery遍历 easing.js 和 animate.css
date: 2017-05-07 20:58:36
tags: 
    - jQuery
    - 前端基础
    - 动态网页编程
    - easing.js
    - animate.css
categories: 
    - 学习
    - 动态网页编程
---
## jQuery 中的遍历
> jQuery 遍历 ：用于根据其相对于其他元素的关系来“查找”（或选取）HTML 元素 。以某项选择开始，并沿着这个选择移动，直到抵达期望的元素为止。
> **jQ遍历分为四种，1. 想上遍历   2. 向下遍历   3. 过滤   4.   水平遍历**   

*   **.eq ** 过滤遍历

	* 用法
	 
		```javascript
		$('li').eq(0).css('background','red');
		```
	* 说明：

		> 查找获取到所有li标签中的**第几个，从零开始**


*   **.first()** 过滤遍历

	* 用法
	 
		```javascript
		$('li').first().css('background','red');
		```
	* 说明：

		> 查找获取到所有li标签中的**第一个**


*   **.last()** 过滤遍历

	* 用法
	 
		```javascript
		$('li').last().css('background','red');
		```
	* 说明：

		> 查找获取到所有li标签中的**最后一个**


*   **.slice()** 过滤遍历

	* 用法
	 
		```javascript
		$('li').slice(2,4).css('background','red');
		```
	* 说明：

		> 查找获取到所有li标签中的**第几个到第几个，下标从零开始，要头不要尾**

*   **.children(选择器)** 向下遍历

	* 用法
	 
		```javascript
		$('ul').children('div').css('background','red');
		```
	* 说明：

		> 查找获取到所有ul标签中的**所有【直接子元素】是选择器的元素**

*   **.find(选择器)** 向下遍历

	* 用法
	 
		```javascript
		$('ul').find('div').css('background','red');
		```
	* 说明：

		> 查找获取到所有ul标签中的**所有后代是选择器的元素**

*   **.parent()** 向上遍历

	* 用法
	 
		```javascript
		$('ul').parent().css('background','red');
		```
	* 说明：

		> 返回ul的**直接父元素**

* 更多遍历方法

	* 向上遍历	（查找元素祖先）

| 遍历方法      |     描述 |   例子|
| :--------: | :--------:| :------: |
| parent() |返回被选元素的直接父元素 (只会向下一级对 DOM 树进行遍历 ) |  $("span").parent();|
|parents() |返回被选元素的所有祖先元素，它一路向上直到文档的根元素 (`<html>`) |$("span").parents();$("span").parents("ul")返回所有 `<span>` 元素的所有祖先，并且它是`<ul>` 元素| 
|parentsUntil()| 返回介于两个给定元素之间的所有祖先元素| $("span").parentsUntil("div");|

	* 向下遍历（查找元素后代）
		
| 遍历方法|     描述 |   例子|
| :--------: | :--------:| :------: |
| children()|   返回被选元素的所有直接子元素(只会向下一级对 DOM 树进行遍历 )| $("div").children()$("div").children("p.1")返回类名为 "1" 的所有 `<p>` 元素，并且它们是`<div>` 的直接子元素|
|find()|返回被选元素的后代元素，一路向下直到最后一个后代| $("div").find("span");$("div").find("*");返回 `<div>` 的所有后代|

	* 水平遍历方法(元素同胞元素)：

| 遍历方法|     描述 |   例子   |
| :--------: | :--------:| :------: |
| siblings()|   返回被选元素的所有同胞元素|  $("h2").siblings();$("h2").siblings("p");返回属于 `<h2>` 的同胞元素的所有 `<p>` 元素|
|next() <br>prev() |返回被选元素的下一个/上一个同胞元素|$("h2").next();|
|nextAll()<br>prevAll()|返回被选元素的所有跟随的同胞（前面同胞）元素|$("h2").nextAll();|
|nextUntil()<br>prevUntil()|返回介于两个给定参数之间的所有跟随的同胞（前面同胞）元素|$("h2").nextUntil("h6");|
	* 过滤：
		
| 遍历方法      |     描述 |   例子   |
| :--------: | :--------:| :------: |
| first()|   返回被选元素的首个元素|  $("div p").first();|
|last()| 返回被选元素的最后一个元素| $("div p").last();|
|eq()| 返回被选元素中带有指定索引号的元素|$("p").eq(1);|
|filter()| 不匹配这个标准的元素会被从集合中删除，匹配的元素会被返回|$("p").filter(".intro");|
|not() not() |方法返回不匹配标准的所有元素not() 方法不 filter() 相反。|$("p").not(".intro");|


	* 遍历所有 **each遍历：**
	
		* each()方法规定为每个匹配元素指定运行的函数

			> 语法：`$(selector).each(function(index,element))`

		* 例如 
			```javascript
			$("button").click(function(){
				$("li").each(function(){
				alert($(this).text())
			   });
			});
			```

## jQuery制作下拉列表

* 下拉列表
	* 三级下拉列表（竖向）：单击一级菜单时展开二级菜单，单击二级菜单时展开三级菜单，当单击另一个一级菜单时同级其它菜单将收起。

* 多级下拉列表（横向）：

	* 鼠标经过一级菜单时展开二级菜单，经过二级菜单
时展开三级菜单，依次类推
			

## easing.js的使用 

> [easing.js](http://gsgd.co.uk/sandbox/jquery/easing/)是个极小的 JavaScript 第三方包，支持 CSS3 的动画效果，非常简单美观。
> move.js中有编写了多种效果

* 老规矩，要使用，先引用
```javascript
<script src="js/jquery-1.8.3.min.js"></script>
// easing是基于jQ的，说要在引用他之前要先引用jQ

<script src="js/easing.js"></script>
```

```javascript
$(this).find("ul").sto
p().slideDown(600,'效果名称');

//我们只需在这更换效果名称即可：如easeIn,easeOut，elasticOut等。
```

## animate.css的使用
> [animate.css](http://www.dowebok.com/demo/2014/98/)animate.css 是一个来自国外的 CSS3 动画库，它预设了抖动（shake）、闪烁（flash）、弹跳（bounce）、翻转（flip）、旋转（rotateIn/rotateOut）、淡入淡出（fadeIn/fadeOut）等多达 60 多种动画效果，几乎包含了所有常见的动画效果。

虽然借助 animate.css 能够很方便、快速的制作 CSS3 动画效果，但还是建议看看 animate.css 的代码，也许你能从中学到一些东西。

* 使用
> 引入文件：`<link href="animate.css" type="text/css" />`
> HTML及使用：`<div class=“animated bounce” ></div>`
刷新页面就可看到动画效果			 
		


