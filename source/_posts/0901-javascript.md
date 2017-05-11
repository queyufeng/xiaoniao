---
title: javascript 数组
date: 2017-04-10 22:51:38
tags: 
    - JavaScript
    - 前端基础
    - 动态网页编程
categories: 
    - 学习
    - 动态网页编程

---
<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width=330 height=86 src="//music.163.com/outchain/player?type=2&id=2526613&auto=1&height=66"></iframe>
# javascript 数组
## 定义数组
### 一维数组创建语法：
> `var 数组名称 = new Array([size]);`
> [size] 表示数组中可存放的元素总数或值([ 该选项可选可不选])

* 方法1

	```javascript
	var fruit = new Array( );
	fruit[0]=“apple”
	fruit[1]=“orange”
	fruit[2]=“peach”
	fruit[3]="bananer"
	```
* 方法2
> `var fruit= new Array("apple", "orange", " peach","bananer") //指定数组长度，数组元素赋值`

* 方法3
	*  指定长度小于数组元素实际数量
	* 制定长度大于数组元素实际数量
* 方法四：推荐使用
	
	```javascript
	var arr4 = [false,"aaa",123];
	alert(arr4);//false,aaa,123
	```
	1. 数组内可以存放任意类型的数据
	2. 数组元素不赋值，则为undefined
	3. 打印数组时，如果某个元素没有赋值，则为“”
	4. 访问数组范围以外的元素时，不会出现越界异常，为undefined
	5. 定义的数组大小，依然可以添加更多的元素

### 二维数组创建语法：

* 语法1: `var arr = new Array(['a','b','c'],['d','e']);
arr[0]`返回第一个一维数组，arr[0][0]返回第一个一维数组的第一个元素‘ a’
> 二维数组可以理解为一个存放数据内容为一维数组的一维数组

* 二维数组创建语法：
	* 语法二:
	```javascript
	 var arr = new Array();
	arr[0]= new Array();
	arr[0][0]= “a”;
	arr[0][1]= “b”;
	arr[0][2]= “c”;
	arr[1]= new Array();
	arr[1][0]= “c”;
	arr[1][1]= “d”;
	```
	> javascript的数组不需要设定长度，会自己迚行扩展
## 访问数组

### 访问数组代码：
* 一维数组：`document.write(fruit[0]); 输出：apple`
* 二维数组：`document.write(arr[0][0]); 输出：a`

### 修改已有数组中的值
	```javascript
	fruit[0]=“pear”
	document.write(fruit[0])
	输出：pear
	```
### 数组的便利

> 利用for语句访问数组中的元素值
	
```javascript
方法一：
var arr = new
Array(13.5,3,4,5,6);
for(var i=0;i<arr.length;i++){
alert(arr[i])
}
方法二：
方法二：
var x
var mycars = new Array()
mycars[0] = "Saab"
mycars[1] = "Volvo"
mycars[2] = "BMW"
for (x in mycars){
document.write(mycars[x])
}
```

## 数组的常用属性和方法
* 数组常用属性—length属性 数组属性`length`
	* 设置或返回数组中元素的数目，该属性的值始终从数值上大于所属数组的任何一个索引号
* 修改数组的length对数组索引的影响
	* 手动增大length属性不影响索引
	* 手动减少length属性会截掉多余的索引
* 修改索引对length属性的影响
	* 增大数组最大索引号会增大length属性
* 删除索引号最大的索引属性不会影响length属性

###数组常用的方法： 数组方法
* join( ) ：把数组的所有元素放入一个字符串，通过一个的分隔符
迚行分隔
* pop( )：删除并返回数组的最后一个元素
* push( )：向数组的末尾添加一个或更多元素，并返回新的长度
* shift()：删除并返回数组的第一个元素
* unshift()：向数组的开头添加一个或更多元素，并返回新的长度数组的常用属性和方法
* reverse()：颠倒数组中元素的顺序
* sort( )：对数组的元素迚行排序
* concat():连接两个或更多的数组，并返回结果。
* slice():从某个已有的数组返回选定的元素
* splice():删除元素，并向数组添加新元素
## 多维数组
> 数组分为一维数组和多维数组二维数组及以上的都称为多维数组，上面我们讲解了一维数组，下面我们例举一下多维数组，以二维数组为例。

```json
[
["Name0", "Age0", "Address0"],
["Name1", "Age1", "Address1"],
["Name2", "Age2", "Address2"]
]
```
*  二维数组的创建：

	```javascript
	Var personnel = new Array();
	Personnel[0]= new Array();
	Personnel[0][0]= “Name0”;
	Personnel[0][1]= “Age0”;
	Personnel[0][2]= “Address0”;
	Personnel[1]= new Array();
	Personnel[1][0]= “Name1”;
	Personnel[1][1]= “Age1”;
	Personnel[1][2]= “Address1”;
	```

	```javascript
	//方法2
	Var aa=new Array(); //定义一维数组
	for(i=1;i<=10;i++)
	{
		aa[i]=new Array(); //将每一个子元素又定义为数组
	for(n=0;n<=10;n++)
	{
	aa[i][n]=i+n; //此时aa[i][n]可以看作是一个二维数 组
	}
	}
	```
	> 还可创建三维数组，四维五维甚至一百维的，但是维数越多越复杂，超过二维的很少使用，下面演示了一个五维数组的声明和访问：

	```javascript
	var myArray=new Array();
	myArray[0]=new Array();
	myArray[0][0]=new Array();
	myArray[0][0][0]=new Array();
	myArray[0][0][0][0]=new Array();
		myArray[0][0][0][0][0]=“This is getting out of hand”
	Document.write(myArray[0][0][0][0][0]);
	```
## 数组的排序
* sort()方法是按照字符编码的顺序进行排序
	```javascript
	function sortNumber(a,b)
	{
	return a - b
	}
	var arr = new Array(6)
	arr[0] = "10"
	arr[1] = "5"
	arr[2] = "40"
	arr[3] = "25"
	arr[4] = "1000"
	arr[5] = "1"
	document.write(arr + "<br />")
	document.write(arr.sort(sortNumber))
	
	```
	> 输出10,5,40,25,1000,1  
	1,5,10,25,40,1000

* 冒泡排序

	
	```javascript
	//冒泡排序法一:
	function sort(elements){
	for(var i=0;i<elements.length-1;i++){
	for(var j=0;j<elements.length-i-1;j++){
	if(elements[j]>elements[j+1]){
	var swap=elements[j];
	elements[j]=elements[j+1];
	elements[j+1]=swap;
	} }
	}}
	var elements = [3, 1, 5, 7, 2, 10, 8, 9, 4, 6];
	document.write('before: ' +
	elements+"<br/>");
	sort(elements);
	document.write(' after: ' + elements);
	```

	> 输出：before: 3,1,5,7,2,10,8,9,4,  
	    after: 1,2,3,4,5,6,7,8,9,10

	```javascript
	function bubbleSort(arr) {
	var i = arr.length, j;
	var tempExchangVal;
	while (i > 0) {
		for (j = 0; j < i - 1; j++) {
	if (arr[j] > arr[j + 1]) {
	tempExchangVal = arr[j];      
	arr[j] = arr[j + 1];
	arr[j + 1] = tempExchangVal;
	}
	}
	i--;
	}
	return arr;
	}
   	```


# 城市二级联动:


```html
<!doctype html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport"
          content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
</head>
<body>

<select  id="gametype">
    <option value="aa">游戏分类</option>
</select></br> 
</br>
</br>

<select  id="gamelist">
    <option>游戏名称</option>

</select>
<script>

     window.onload=function () {
         var game = new Array( );

         game['纸牌游戏']=['斗地主', '拖拉机', '桥牌', '拱猪', '打百分'];
         game['棋类游戏']=['军棋', '跳棋', '五子棋', '围棋', '中国象棋', '国际象棋', '飞行棋', '黑白棋'];
         game['其他游戏'] = ['连连看', '俄罗斯方块', '麻将', '台球', '挑错'];


         //
         var gametype=document.getElementById("gametype")
         for(var x in game){

             gametype.add(new Option(x,x))
         }
        gametype.onchange=function () {


             var  gamelist=document.getElementById("gamelist")
             gamelist.options.length=0;
             var  gametypevalue=gametype.value;

             for(var j in game){
              if(j==gametypevalue){

                  for(var f=0;f<game[j].length;f++){
                      console.log(game[j]);
                      console.log(game[j][f]);
                      gamelist.add(new Option(game[j][f],game[j][f]))
                  }


              }
          }

         }
}





</script>




</body>
</html>

```
	
	

