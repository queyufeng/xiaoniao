---
title: JavaScript基础引入
date: 2017-04-10 21:26:57
tags: 
    - JavaScript
    - 前端基础
    - 动态网页编程
categories: 
    - 学习
    - 动态网页编程
---
<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width=330 height=86 src="//music.163.com/outchain/player?type=2&id=27583305&auto=1&height=66"></iframe>
# javascript基础
## 简介
* 轻量级、直译式客户端脚本语言。
* 可被所有浏览器执行，实现网页的劢态功能。
* 揑入 HTML 页面后，可由所有的现代浏览器执行
## 应用场景
* 操作页面元素，动态改变页面内容动态改变表格内容
* 编写页面动态效果轮播图层的切换 和 树形菜单等
* 数据的客户端验证－减轻服务器端压力注册表单验证
* 通过ajax和后端语言实现数据交互

## 组成:
1. ECMAScript
2. BOM
3. DOM

## ECMAScript
* 概念：JavaScript的核心，描述了语言的基本语法和数据类
型，ECMAScript是一套标准，定义了一种语言（比如JS）
是什么样子。
* 编码遵循ECMAScript标准

## BOM(浏览器对象模型)
* 概念:BOM是用于描述这种对象不对象乊间层次关系的模型，浏览器对象模型提供了独立于内容的、可以不浏览器窗口进行互劢的对象结构。 BOM由多个对象组成，其中代表浏览器窗口的Window对象是BOM的顶层对象，其他对象都是该对象的子对象。

### DOM(文档对象模型)
* 概念:W3C组织推荐的处理可扩展置标语言的标准编程接口。 DOM是以面向对象方式描述的文档模型。 DOM定义了表示和修改文档所需的对象、这些对象的行为和属性以及这些对象乊间的关系。可以把DOM认为是页面上数据和结构的一个树形表示，不过页面当然可能并不是以这种树的方式具体实现。

##javascript 使用方法
* html内嵌javascript代码
	> `<script type="text/javascript"> //JavaScript 语句</script >`

* 外部JS文件
	> `<script src="hello.js" language="javascript"></script>`

* 行内编写方式
	> `<input name="btn" type="button" value="弹出消息框"onclick="javascript:alert('欢迎你');"/>`

## 事件监听
* onload事件:是在页面或图片加载完成后立即执行的事件获取元素
* getElementById()：获取指定 ID 的第一个对象引用
* getElementsByName()：通过NAME属性获Document中指定名称对象的集合
* getElementsByTagName()：使用指定的标签名返回所有的元
素，这些元素是您在使用此方法时所处的元素的后代

## JavaScript 的调试工具及调试方法
* 调试工具:Firebug工具
* 安装：火狐浏览器 - 选顷 – 附加组件 – 搜索Firebug添加即可。安装完成，按键盘f12即可打开Firebug
* Chrome和ie自带调试工具，不需要安装
* 调试方法
	1. 使用Firebug的HTML 、 CSS、脚本顷查看页面的html标签、 CSS文件、 JS文件。
	2. Firebug控制台:
		1. 如果页面报错，会在控制台显示：包括错误原因和行号
		2. 控制台最下边的输入框可以输入js代码，提交浏览器执行
	3. 利用js的console方法，可以在控制台输出js代码中的值、对象、 DOM等，以方便查看对象的结构
常用方法：console.log() console.dir()


