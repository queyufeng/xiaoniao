---
title: Math对象,Date对象,正则表达式
date: 2017-04-21 09:19:19
tags: 
    - JavaScript
    - 前端基础
    - 动态网页编程
categories: 
    - 学习
    - 动态网页编程
---
#  Math 对象

1.  作用：
		
	>  Javascript中，Math 对象是用于执行数学任务的对象(取整、取余。)

2. 访问语法：MAth.属性名
	> 注释：Math 对象并不像 Date 和 String 那样是对象的类，因此没有构造函数 Math()，像 Math.sin() 这样的函数只是函数，不是某个对象的方法。您无需创建它，通过把 Math 作为对象使用就可以调用其所有属性和方法。

3. 属性和方法
	
	*  abs(x)返回数的绝对值
	*  ceil(x)对数进行上取整
	*  floor(x)对数进行下取整
	*  max(x,y)返回 x 和 y 中的最高值
	*  min(x,y)返回 x 和 y 中的最低值
	*  round(x)把数四舍五入为最接近的整数
	*  pow(x,y)返回 x 的 y 次幂
	*  random()返回 0 ~ 1 之间的随机数
	*  sqrt(x)返回数的平方根

# Date 对象

1. 作用 :

	> Javascript中， Date 对象用于处理日期和时间

2. 创建 Date 对象的语法：

   > `var myDate=new Date()`

3. 属性
	*  constructor返回对创建此对象的 Date 函数的引用
	* prototype使您有能力向对象添加属性和方法。

4. 获取时间方法 ：
	* Date()返回当日的日期和时间
	* getDate()从 Date 对象返回一个月中的某一天 (1 ~ 31)
	* getDay()从 Date 对象返回一周中的某一天 (0 ~ 6)
	* getMonth()从 Date 对象返回月份 (0 ~ 11)
	* getFullYear()从 Date 对象以四位数字返回年份
	* getHours()返回 Date 对象的小时 (0 ~ 23)
	* getMinutes()返回 Date 对象的分钟 (0 ~ 59)
	* getSeconds()返回 Date 对象的秒数 (0 ~ 59)
	* getMilliseconds()返回 Date 对象的毫秒(0 ~ 999)
	* getTime()返回 1970 年 1 月 1 日至今的毫秒数
</br>
</br>
 **获取时间的其他方法**  
</br>
</br>
	* getTimezoneOffset()返回本地时间不格林威治标准时间(GMT) 的分钟差
	* getUTCDate()根据世界时从Date 对象返回月中的一天 (1~31)
	* getUTCDay()根据世界时从 Date 对象返回周中的一天 (0 ~ 6)
	* getUTCMonth()根据世界时从 Date 对象返回月份 (0 ~ 11)
	* getUTCFullYear()根据世界时从 Date 对象返回四位数的年份
	* getUTCHours()根据世界时返回 Date 对象的小时 (0 ~ 23)
	* getUTCMinutes()根据世界时返回 Date 对象的分钟 (0 ~ 59)
	* getUTCSeconds()根据世界时返回 Date 对象的秒钟 (0 ~ 59)
	* getUTCMilliseconds()根据世界时返回 Date 对象的毫秒(0~ 999)
	* parse()返回1970年1月1日午夜到指定日期（字符串）的毫秒数

5. 设置时间方法：

	* setHours()设置 Date 对象中的小时 (0 ~ 23)
	* setMinutes()设置 Date 对象中的分钟 (0 ~ 59)
	* setSeconds()设置 Date 对象中的秒钟 (0 ~ 59)
	* setMilliseconds()设置 Date 对象中的毫秒 (0 ~ 999)
	* setTime()以毫秒设置 Date 对象
</br>
</br>
 **设置时间的其他方法**  
</br>
</br>
	* setUTCDate()根据世界时设置 Date 对象中月份的一天 (1 ~ 31)
	* setUTCMonth()根据世界时设置 Date 对象中的月份 (0 ~ 11)
	* setUTCFullYear()根据世界时设置 Date 对象中的年份（四位数字）
	* setUTCHours()根据世界时设置 Date 对象中的小时 (0 ~ 23)
	* setUTCMinutes()根据世界时设置 Date 对象中的分钟 (0 ~ 59)
	* setUTCSeconds()根据世界时设置 Date 对象中的秒钟 (0 ~ 59)
	* setUTCMilliseconds()根据世界时设置 Date 对象中的毫秒 (0 ~ 999)

6. Date的其他方法:
	* toSource()返回该对象的源代码
	* toString()把 Date 对象转换为字符串 
	* toTimeString()把 Date 对象的时间部分转换为字符串
	* toDateString()把 Date 对象的日期部分转换为字符串
	* toUTCString()根据世界时，把 Date 对象转换为字符串。 
	* toLocaleString()根据本地时间格式，把 Date 对象转换为字符串。
	* toLocaleTimeString()根据本地时间格式，把 Date 对象的时间部分转换为字符串 
	* toLocaleDateString()根据本地时间格式，把 Date 对象的日期部分转换为字符串。
	* UTC()根据世界时返回 1970 年 1 月 1 日 到指定日期的毫秒数。
	* valueOf()返回 Date 对象的原始值

# 正则表达式

1. 概念: 
	> 正则表达式 （Regular Expression、 regex），是使用单个字符串来描述、匹配一系列符合某个句法规则的字符串。

2. 作用:
	> 测试字符串 、 替换文本 、 从字符串中匹配提取一个子字符串

3. 声明方式:
	```javascript
	例1：var myRegExp=/内容 /
	例2：var myRegExp= new RegExp(“ 内容” ) 
	```
	
	**注意:**
	> `斜杠（/内容/）表示正则表达式的开始和结束；`
	`声明方式第一种更简短有效，通常我们都用第一种；`

4. 正则表达式方法: 
	* test(),匹配一个字符串是否符合正则规则，成功，则返回true
	* match(),找到一个或多个正则表达式的匹配
	* replace(),替换与正则表达式匹配的子串
	* search(),检索与正则表达式相匹配的值
	* split(),把字符串分割为字符串数组

5 正则表达式修饰符

* 全局匹配,修饰符g /..../g
	* 例如：

		```javascript
			var str04 = "aacbmaa";
			var reg04 = /a/g;
			document.write( str04.replace(reg04, "m") )
			//输出：mmcbmmm;
			//如果去掉g: var reg04 = /a/;
			//输出：macbmaa;

		```

* 不区分大小写,修饰符i /...../I
	> 就是将Paul和paul视为相同的字符模式
	
* 直接量字符
* 任意字符 ： [abc]
* 范围 ： [a-z]、 [0-9]
* 排除 ： [^a]
* 组合 ： [a-z0-9A-Z]	
		