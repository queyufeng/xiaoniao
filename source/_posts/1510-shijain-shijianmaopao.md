---
title: BOM
date: 2017-04-25 22:16:51
tags: 
    - JavaScript
    - 前端基础
    - 动态网页编程
categories: 
    - 学习
    - 动态网页编程
---
# Window 对象
##概念：
> Window 对象表示浏览器中打开的窗口。如果文档包含框架（frame 或 iframe 标签），浏览器会为 HTML 文档创建一个 window 对象，并为每个框架创建一个额外的 window 对象
## 属性
* innerHeight 返回窗口的文档显示区的高度
* innerWidth 返回窗口的文档显示区的宽度
* outerHeight 返回窗口的外部高度 包括滚动条、地址栏、收藏栏等
* outerwidth 返回窗口的外部宽度 
* length 设置或返回窗口中的框架数量
* name 设置或返回窗口的名称。
	* window.open() 打开的新网页，第二个参数就是此网页的name。
	* iframe里面，name属性就是window的name

## 方法
* close() 关闭浏览器窗口
* alert() 显示带有一段消息和一个确认按钮的警告框
* confirm() 显示带有一段消息以及确认按钮和取消按钮的对话框
* prompt()显示可提示用户输入的对话框
* open() 打开一个新的浏览器窗口或查找一个已命名的窗口
* resizeBy() 按照指定的像素调整窗口的大小
* resizeTo() 把窗口的大小调整到指定的宽度和高度
* scrollBy() 按照指定的像素值来滚动内容
* scrollTo() 把内容滚动到指定的坐标

# navigator对象
> navigator对象通常用于检测浏览器不操作系统的版本
##属性：
* appCodeName返回浏览器的代码名
* appVersion返回浏览器的次级版本
* appName返回浏览器的名称
* language返回当前浏览器的语言
* platform 返回运行浏览器的操作系统平台

# document对象

> document 对象是 Window 对象的一部分，包含整个htmlDOM,可通过 window.document 属性对其进行访问,也可以用document直接访问

##属性:

* document.cookie 获取或设置cookie
* document.title 获取或设置title
* document.URL 获取或设置URL

## window下的其他对象
> screen 对象包含有关客户端显示屏幕的信息

###  属性
* height 返回显示屏幕的高度； width返回显示器屏幕的宽度
* availHeight 返回显示屏幕的高度 (除 Windows 任务栏之外)
*  availWidth 返回显示屏幕的宽度 (除 Windows 任务栏之外)
*   colorDepth 返回目标设备或缓冲器上的调色板的比特深度
*   pixelDepth 返回显示屏幕的颜色分辨率（比特每像素）

## Body对象

### 属性
* clientWidth网页可见区域宽
* clientHeight网页可见区域高
* scrollWidth网页正文全文宽
* scrollHeight网页正文全文高
* scrollTop网页被卷去的高
* scrollLeft网页被卷去的左

##Location 对象
> Location 对象对象包含有关当前 URL 的信息
### 属性
* hash设置或返回从井号 (#) 开始的 URL（锚）
* host设置或返回主机名和当前 URL 的端口号
* hostname设置或返回当前 URL 的主机名
* href设置或返回完整的 URL
* pathname设置或返回当前 URL 的路径部分
* port设置或返回当前 URL 的端口号
* protocol设置或返回当前 URL 的协议
* search设置或返回从问号 (?) 开始的 URL（查询部分）

###方法
* assign() 加载新的文档
* reload() 重新加载当前文档
* replace() 用新的文档替换当前文档
