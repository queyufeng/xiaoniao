---
title: AJAX
date: 2017-05-03 09:21:17
tags: 
    - html
    - 前端基础
    - 动态网页编程
categories: 
    - 学习
    - 动态网页编程
---
# AJAX概念及form提交

## AJAX概念
* AJAX 是什么？
> **Asynchronous JavaScript and XML（异步JavaScript和XML)**

* 作用
	* **不重新加载整个页面的情况下，可以与服务器交换数据并更新部分网页内容。**
	* 节省用户操作，时间，提高用户体验，减少数据请求传输获取数据

* 过程：
> 初始化 -- >发送请求 --> 服务器收到请求 --> 服务器处理 --> 返回结果



# 表单

* 表单form
	* action 提交到哪里
	* method 提交方式
* Get方式
	* Get通过url地址传输
	* 有数据量限制，每个浏览器都不同
	* 不安全
* Post方式
	* Post通过浏览器内部传输
	* 数据量理论上无限
	* 相对比较安全
*   enctype : 提交的数据格式，默认application/x-www-form-urlencoded 
* 提交方式必须与后台的接收方式一致。


# 异常处理
try {}catch{}用于异常处理，当try语句里的内容执行出现
错误的时候，就会执行catch里的语句。 catch里能使用
```javascript
    //err.message捕获出错的原因。
    try{//此处是可能产生例外的语句
}catch(err){
//此处是负责例外的处理白语句
    }

```
 finally里是始终会执行的语句
 
```javascript

Try{
//此处是可能产生例外的语句
} catch (err) {
//此处是负责例外处理的语句
}finally{
//此处是出口语句，当try，catch的
}

```

# AJAX的方法

* Open方法 open(method,url,async)
	* 三个参数的含义
		1、提交方式 Form-method
		2、提交地址 Form-action
    	3、异步（同步）

* Send方法
	发送数据请求，相当于Form的submit

* AJAX请求状态监控
	* onreadystatechange事件
	* readyState属性：请求状态
		0 （初始化）还没有调用open()方法
		1（载入）已调用send()方法，正在发送请求
		2（载入完成）send()方法完成，已收到全部响应内容
		3（解析）正在解析响应内容
		4（完成）响应内容解析完成，可以在客户端调用了
	* status属性：服务器(请求资源)的状态

# AJAX返回数据的处理
* 返回的内容
	* responseText：返回以文本形式存放的内容
	* responseXML：返回XML形式的内容
* 返回数据的处理
	* 数据类型：XML、 HTML、 JSON
	* Eval解析JSON的时候需要注意的地方
	* JSON.parse() : 字符串解析成对象
	
# Ajax 常问问题

1. 什么是ajax，为什么要使用Ajax（请谈一下你对Ajax的认识）
	1. 什么是ajax：
        > AJAX是“Asynchronous JavaScript and XML”的缩写。他是指一种创建交互式网页应用的网页开发技术。

	2. Ajax包含下列技术：

		> * 基于web标准（standards-based presentation）XHTML+CSS的表示；
		> * 使用 DOM（Document Object Model）进行动态显示及交互；
		> * 使用 XML 和 XSLT 进行数据交换及相关操作；
		> * 使用 XMLHttpRequest 进行异步数据查询、检索；
		> * 使用 JavaScript 将所有的东西绑定在一起。

2. 为什么要用ajax：Ajax应用程序的优势在于：

	1. 通过异步模式，提升了用户体验

	2. 优化了浏览器和服务器之间的传输，减少不必要的数据往返，减少了带宽占用

	3. Ajax引擎在客户端运行，承担了一部分本来由服务器承担的工作，从而减少了大用户量下的服务器负载。

3. **Ajax的最大的特点是什么。**

	> Ajax可以实现动态不刷新（局部刷新）

	就是能在不更新整个页面的前提下维护数据。这使得Web应用程序更为迅捷地回应用户动作，并避免了在网络上发送那些没有改变过的信息。

4. 请介绍一下XMLHTTPREQUEST对象？

	Ajax的核心是JavaScript对象XmlHttpRequest。该对象在Internet Explorer 5中首次引入，它是一种支持异步请求的技术。简而言之，XmlHttpRequest使您可以使用JavaScript向服务器提出请求并处理响应，而不阻塞用户。通过XMLHttpRequest对象，Web开发人员可以在页面加载以后进行页面的局部更新。

4. Ajax技术体系的组成部分有哪些？

	HTML，css，dom，xml，xmlHttpRequest，javascript

5. AJAX应用和传统Web应用有什么不同？

	在传统的Javascript编程中，如果想得到服务器端数据库或文件上的信息，或者发送客户端信息到服务器，需要建立一个HTML form然后GET或者POST数据到服务器端。用户需要点击”Submit”按钮来发送或者接受数据信息，然后等待服务器响应请求，页面重新加载。

	因为服务器每次都会返回一个新的页面， 所以传统的web应用有可能很慢而且用户交互不友好。

	使用AJAX技术， 就可以使Javascript通过XMLHttpRequest对象直接与服务器进行交互。

	通过HTTP Request， 一个web页面可以发送一个请求到web服务器并且接受web服务器返回的信息(不用重新加载页面)，展示给用户的还是通一个页面，用户感觉页面刷新，也看不到到Javascript后台进行的发送请求和接受响应。

7. Ajax和javascript的区别？

	javascript是一种在浏览器端执行的脚本语言，Ajax是一种创建交互式网页应用的开发技术 ，它是利用了一系列相关的技术其中就包括javascript。

	Javascript是由网景公司开发的一种脚本语言，它和sun公司的java语言是没有任何关系的，它们相似的名称只是一种行销策略。

	在一般的web开发中，javascript是在浏览器端执行的，我们可以用javascript控制浏览器的行为和内容。

	在 Ajax应用中信息是如何在浏览器和服务器之间传递的

     通过XML数据或者字符串

8. **在浏览器端如何得到服务器端响应的XML数据**

      XMLHttpRequest对象的responseXMl属性

9.  XMLHttpRequest对象在IE和Firefox中创建方式有没有不同？

	有，IE中通过new ActiveXObject()得到，Firefox中通过new XMLHttpRequest()得到

10. 介绍一下XMLHttpRequest对象的常用方法和属性（回答的越多越好）

      open(“method”,”URL”) 建立对服务器的调用，第一个参数是HTTP请求    方式可以为GET，POST或任何服务器所支持的您想调用的方式。
第二个参数是请求页面的URL。

	send()方法，发送具体请求

	abort()方法，停止当前请求

	readyState属性   请求的状态 有5个可取值 
	**0=未初始化 ，1=正在加载,2=以加载，3=交互中，4=完成**

	**responseText 属性  服务器的响应，表示为一个串**

	**reponseXML 属性 服务器的响应，表示为XML**

    status    服务器的HTTP状态码，200对应ok  400对应not found

11. Ajax的优点和缺点

	使用Ajax的最大优点，就是能在不更新整个页面的前提下维护数据。这使得Web应用程序更为迅捷地回应用户动作，并避免了在网络上发送那些没有改变过的信息。

	对应用Ajax最主要的缺点就是，它可能破坏浏览器后退按钮的正常行为

	因为Ajax中采用了xml技术，所以在Ajax中也可能问到XML的问题



12. 介绍一下XMLHttpRequest对象

	通过XMLHttpRequest对象，Web开发人员可以在页面加载以后进行页面的局部更新。

	AJAX开始流行始于Google在2005年使用的”Google Suggest”。

	“Google Suggest”就是使用XMLHttpRequest对象来创建动态的Web接口：

	当用户开始输入google的搜索框，Javascript发送用户输入的字符到服务器，然后服务器返回一个建议列表。

	XMLHttpRequest对象在IE5.0+, Safari 1.2, Mozilla 1.0/Firefox, Opera 8+ 和NetScapt7 开始被支持。

18. AJAX应用和传统Web应用有什么不同？

	在传统的Javascript编程中，如果想得到服务器端数据库或文件上的信息，或者发送客户端信息到服务器，需要建立一个HTML form然后GET或者POST数据到服务器端。用户需要点击”Submit”按钮来发送或者接受数据信息，然后等待服务器响应请求，页面重新加载。

	因为服务器每次都会返回一个新的页面， 所以传统的web应用有可能很慢而且用户交互不友好。

	使用AJAX技术， 就可以使Javascript通过XMLHttpRequest对象直接与服务器进行交互。

	通过HTTP Request， 一个web页面可以发送一个请求到web服务器并且接受web服务器返回的信息(不用重新加载页面)，展示给用户的还是通一个页面，用户感觉页面刷新，也看不到到Javascript后台进行的发送请求和接受响应。

19. AJAX的全称是什么？介绍一下AJAX？

	AJAX的全称是Asynchronous JavaScript And XML.

	AJAX是2005年由Google发起并流行起来的编程方法， AJAX不是一个新的编程语言，但是它是一个使用已有标准的新的编程技术。

	使用AJAX可以创建更好，更快，更用户界面友好的Web应用。

**AJAX技术基于Javascript和HTTP Request.**

15. 介绍一下XMLHttpRequest对象的常用方法和属性？

	open(“method”,”URL”) 建立对服务器的调用，第一个参数是HTTP请求    方式可以为GET，POST或任何服务器所支持的您想调用的方式。

	第二个参数是请求页面的URL。

	send()方法，发送具体请求
	readyState属性   请求的状态 有5个可取值 0=未初始化 ，1=正在加载  2=以加载，3=交互中，4=完成

	responseText 属性 服务器的响应，表示为一个串

	reponseXML 属性 服务器的响应，表示为XML

	status    服务器的HTTP状态码，200对应ok 400对应not found

21. .Ajax主要包含了哪些技术？

	Ajax（Asynchronous JavaScript + XML）的定义

	基于web标准（standards-based presentation）XHTML+CSS的表示；

	使	用 DOM（Document Object Model）进行动态显示及交互；

	使用 XML 和 XSLT 进行数据交换及相关操作；

	使用 XMLHttpRequest 进行异步数据查询、检索；

	使用 JavaScript 将所有的东西绑定在一起。英文参见Ajax的提出者Jesse James Garrett的原文,原文题目(Ajax: A New Approach to Web Applications)。

	类似于DHTML或LAMP，AJAX不是指一种单一的技术，而是有机地利用了一系列相关的技术。事实上，一些基于AJAX的“派生/合成”式（derivative/composite）的技术正在出现，如“AFLAX”。

	AJAX的应用使用支持以上技术的web浏览器作为运行平台。这些浏览器目前包括：Mozilla、Firefox、Internet Explorer、Opera、Konqueror及Safari。但是Opera不支持XSL格式对象，也不支持XSLT。

17. AJAX都有哪些有点和缺点？

	1、最大的一点是页面无刷新，用户的体验非常好。

	2、使用异步方式与服务器通信，具有更加迅速的响应能力。

	3、可以把以前一些服务器负担的工作转嫁到客户端，利用客户端闲置的能力来处理，减轻服务器和带宽的负担，节约空间和宽带租用成本。并且减轻服务器的负担，ajax的原则是“按需取数据”，可以最大程度的减少冗余请求，和响应对服务器造成的负担。

	4、基于标准化的并被广泛支持的技术，不需要下载插件或者小程序。

	**ajax的缺点**

	1、ajax不支持浏览器back按钮。

	2、安全问题 AJAX暴露了与服务器交互的细节。
	3、不容易调试。