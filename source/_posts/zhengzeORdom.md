---
title: 正则表达式2,DOM
date: 2017-04-22 00:32:18
tags: 
    - JavaScript
    - 前端基础
    - 动态网页编程
categories: 
    - 学习
    - 动态网页编程
---

# 正则表达式	2

| 转义字符  |     功能 | 
| :-------- | --------:| 
| \n    |   换行符 | 
| \r    |   回车符 |
| \t    |   制表符 |
| \f    |   换页符 |
| \cX    |   与x对应的控制字符 |
| \v    |   垂直制表符 |
| \b    |   退格符 |
| \0    |   空字符"" |      
 | .(点)    |   匹配除换行符之外的任一个字符，IE下[^\n],其他[^\n\r] | 
| \d    |   匹配数字[0-9] |
| \D    |   匹配非数字字符 |
| \w    |   匹配字母数字和下划线[a-zA-Z0-9_] |
| \W    | 匹配除字母数字下划线之外的字符 [^azA-Z0-9_] |
| \s    |   匹配一个空白字符 [ \n\r\t\f\x0B] |
| \S    |   匹配一个非空白字符 [^ \n\r\t\f\x0B] |
| \b    |   独立部分（起始、结束、空格） |
| \B    |   非独立部分 |      
| \1    |   第一个匹配子项的重复匹配 |

| 量词      |     功能 |
| :-------- | --------:|
| {n,m}    |  至少出现n次，最多m次 |
| {n,}    |  至少出现n次，|
| *    |  任意次{0，} |
| ？    | 零次或者一次{0,1} |
| +   |  一次或任意次{1,}|
| {n}    |  正好n次 |
```javascript
//例子
//？ 零次或一次 {0,1}
	var reg09 = /a?/;
	document.write( reg09.test("aabbcc") +"</br>");
```
* 首尾
	* **^**匹配起始位置

		> 例：/^a/－表示须以字母a开始
	*	**$** 匹配结束位置

	> 例：/t$/－表示须以字母t结尾

* 选择分组与引用
	* 分组用()

| 常用正则表达式      |     功能 |
| :-------- | --------:|
| [\u4e00-\u9fa5]  |   匹配中文 |
| ^\s*|\s*$ |  行首行尾空格|
| ^\w+@[a-z0-9]+(\.[a-z]+){1,3}$  |   EMAIL|
| [a-zA-z]+://[^\s]*  |   网址 |
| [1-9][0-9]{4,9}  |   QQ号|
| [1-9]\d{5}  |   邮政编码 |
| [1-9]\d{5}  |   邮政编码 |
| [1-9]\d{14}|[1-9]\d{17}|[1-9]\d{16}x |   身份证号 |

# DOM
* 分析DOM节点
```html 
<html>
<head>
<title>DOM 教程</title>
</head>
<body>
<h1>DOM 第一节</h1> 、
<p>Hello world!</p>
</body>
</html>
```
> 分析父、子和同胞节点：·`<html>` 节点没有父节点，它是根节点
>
>`<head>` 和 `<body>` 的父节点是`<html>` 节点 ；文本节点 “ Hello world!”的父节点是 `<p>` 节点

* 获取节点
	* 由id获取 `getElementById`
		* 语法：`node.getElementById("id");`
		* 例: `document.getElementById("intro");`
	* 由class获取 `getElementsByClassName`
		* 语法：`node. getElementsByClassName("class");`
		* 例：`document. getElementsByClassName(" class ");`
	* 由标签名获取 `getElementsByTagName`
		* 语法：`node. getElementsByTagName(“h1 ");`

* 查看节点类型
	*  语法：
	> `nodeObject.[nodeType][nodeName ][nodeValue ]`
	
	* nodeType 返回以数字值返回指定节点的节点类型。如果节点是元素节点，则返回 1。如果节点是属性节点，则返回 2。
	* nodeName 返回节点名称（大写的标签名）
	* nodeValue 文本节点返回文本内容，其他节点返回null

* DOM属性获取与设置
	* 获取方法：
		* element[attributename]
		* element . attributename
		* getAttribute( attributename )
	* 设置属性：
		* setAttribute( attributename, attri
	* 删除属性：
		* removeAttribute( attributename)

* 常用属性：
	* className 类名
	* offsetWidth 宽
	* offsetHeight 高
	* offsetLeft,offsetTop获取距离第一个定位父节点左上角的距离

* 操作子节点
创建节点 createElement( )
子节点的增删改
	* appendChild 在DOM子集最后添加子节点
	* insertBefore 在指定的已有子节点之前插入新的子节点
	* removeChild 删除一个节点
	*  replaceChild 替换节点