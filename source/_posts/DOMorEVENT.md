---
title: DOM节点查找，事件
date: 2017-04-22 00:33:08
tags: 
    - JavaScript
    - 前端基础
    - 动态网页编程
categories: 
    - 学习
    - 动态网页编程
---

# DOM节点查找

| 属性名称|     作用 |
| :-------- | --------:|
| children   |   子节点，不包含空节点| 
| childNodes    |   子节点，包含空节点| 
| firstChild|   第一个子节点，包含空节点| 
| firstElementChild|   第一个子节点，不包含空节点| 
| lastChild|   最后一个子节点，包含空节点| 
| lastElementChild|   最后一个子节点，不包含空节点| 
| nextSibling|   下一个兄弟节点，包含空节点| 
| nextElementSibling   |   下一个兄弟节点，不包含空节点| 
| previousSibling|   前一个兄弟节点，包含空节点| 
| previousElementSibling|   前一个兄弟节点，不包含空节点| 
| parentNode    |   父节点| 
| offsetParent|   第一个有定位属性的父节点，如果没有，则返回body|



# 事件
* onload 图片或页面加载完成
* 焦点事件:onfocus/onblur 获得焦点/失去焦点
* onchange 表单内容发送改变
* onclick 点击
* ondblclick 点击两次 
* onkeydown 键盘按下
* onkeyup 键盘抬起
* 
*  获取对象 、 兼容处理
	
	```javascript
	 document.onkeydown = function(ev){
	var ev = ev || window.event;
	//获取事件对象兼容处理，一般浏览器直接在function参
	//数ev获取,ie浏览器通过window.event获取
	document.write(ev.keyCode);}
	```
*  键盘event对象属性 keyCode
*  onmousedown 鼠标按下
*  onmouseup 鼠标抬起
*  onmousemove 鼠标移动
*  onmouseover 移到对象上
*  onmouseout 鼠标离开
* 鼠标event对象属性 clientX clientY
* onselect 在文本框中的文本被选中时发生,支持`<input type="text">`, `<textarea>`
* onsubmit 在表单中的提交按钮被点击时触发
*  onreset 在表单中的重置按钮被点击时触发
*   onerror 在文档或图像加载过程中发生错误时被触发
*   阻止默认事件`preventDefault() 或者 return false；`


# 事件的触发机制
事件的触发机制
> 上一级标签开始往下查找，直到捕获到事件目标(target)。

事件冒泡阶段：
> 事件从事件目标(target)开始，往上冒泡直到页面的最上一级标签。

# 事件冒泡

冒泡详解：
>如果此对象定义了此事件的处理程序，那么此事件就会调用这个处理程序，如果没有定义此事件处理程序或者事件返回true，那么这个事件会向这个对象的父级对象传播,不是所有的事件都能冒泡。 blur、 focus、 load和unload不能像其它事件一样冒泡。

阻止冒泡 
> IE中使用cancelBubble=true，Firefox中使用stopPropagation()

  ![冒泡事件](/images/20131028160201571.jpg)
