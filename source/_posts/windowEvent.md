---
title: window中的方法
date: 2017-04-28 09:21:50
tags: 
    - JavaScript
    - 前端基础
    - 动态网页编程
categories: 
    - 学习
    - 动态网页编程
---
# window对象的事件
* onscroll 当浏览器滚动的时候触发
* onresize  当浏览器窗口改变大小时触发
* 鼠标的滚轮事件：
	* 注册滚轮事件的兼容写法
	```javascript

	if(document.addEventListener){//firefox
		"DOMMousescro","fn",false
		}
	 window.onmousewheel = document.onmousewheel = scrollFunc; //ie和谷歌
    ```

	* 判断滚轮方向
		* e.wheelDelta    //ie和谷歌
		* e.delta    //火狐


# cookie
* 概念：
		
	> “Cookie” 是小量信息，某些 Web 站点在您的硬盘上用很小的文本文件存储的信息，下次访问该站点时，可从浏览器读回此信息。

* 作用：保存数据到客户端浏览器 。可用于：保存用户登录状态、跟踪用户行为（如保存地区）、定制页面样式、创建购物车 
* 限制：每个域最多保存50个cookie，单个cookie大小不能超
过4k 

* 储存方式：document.cookie = ‘ 名字＝值; expires=过期时间';
	* 在cookie的名或值中不能使用分号（;）、逗号（,）、等号（=）以及空格，所以存储时需用escape()函数进行编码，它能将一些特殊符号使用十六进制表示，取用时再用unescape反编码 
	* 过期时间是以GMT格式表示的时间字符串，超过这个时间，cookie将消失，过期时间设置为：当前时间+过期天数*24*3600*1000


# 历史记录
> 当浏览器的URL发送改变时，浏览器会记录相应的地址记录以生成历史记录，让浏览器可以前进后退，同时 window 的history对象提供了相应的操作方法。

* back() 退一步，类似在浏览器的工具栏上点击返回按钮
* forward() 前进一步，类似在浏览器中点击前进按钮

* go() 跳转到相应页，当前页面位置索引值为0，上一页就是-1，下一页为1

# iframe操作
 * 操作子页面
	document.getElementById('iframe的ID').contentWindow.document.getElementById(‘ 元素的ID')

* 操作父页面
	window.parent.document.getElementById(‘ 元素的ID')
* 操作顶级页面
	window.top.document.getElementById(‘ 元素的ID')