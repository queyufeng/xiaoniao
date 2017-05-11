---
title: 五分钟学会Seajs
date: 2017-04-11 11:49:17
tags: 
    - JavaScript
    - 模块化规范
    - 面向对象
    - Seajs
categories: 
    - 前端模块化加载框架
---
* 1：引入包文件 sea.js
* 2: 启动seajs.use('./main') 设置启动入口模块 参数可以不需要.js后缀

```html
<html>
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>06_seajs基本使用</title>
</head>
<body>
  <!-- 1：引包 -->
  <script src="../seajs-3.0.0/dist/sea.js" charset="utf-8"></script>
  <!-- <script src="./one.js" charset="utf-8"></script>
  <script src="./two.js" charset="utf-8"></script> 不适用seajs加载的方式，需要注意文件顺序-->
  <!-- 2: 启动seajs 并且指定入口模块 -->
  <script type="text/javascript">
    seajs.use('./one');
  </script>
</body>
</html>

```

* 3: 声明一个模块：模块在define();内部包裹
* 4: 需要向外暴露值，通过module.exports来返回

```javascript
define(function(require,exports,module){
      // 如果这个模块需要别的模块的返回值
      var aaa =require('模块路径ID');//返回对方模块内部的module.exports
      module.exports = 返回值;
});

```
* 在模块内部，声明的变量，都是模块的作用域
	  + 在CMD中，一个模块就是一个文件，外部无法访问
	  + 如果需要访问，通过module.exports 向外暴露

#### define参数的三种方式
* 字符串 define('123')
> define('我是字符串');

* 对象define({name:'aaa'})
> define({name:'gaga',age:19});

* 函数define(function(require,exports,module){})
```javascript
define(function(require,exports,module){
  // module.exports = {nane:'jack'}
  return 'abcl';
})
```
#### exports和module.exports的小问题
* 模块被加载的时期，这两个对象都指向一块内存，该内存初始值是一个空对象
* 不管任意改变哪个对象的内存指向 （对象=值），最终仍然返回module.exports对象
* 如果module.exports 和exports让你头晕脑胀，建议使用module.exports

* **框架的使用尽量遵守其规则,基于define内部解析对象，根据参数的数据来，顺序不要改变**
* module.exports 用来赋值并暴露，exports用来给暴露的对象挂载属性，就是一个简写
#### Use的2种方法
* use函数是一个异步函数
  + 异步：不阻塞后续代码执行
  + 同步：当前函数不执行完毕，下一行代码无法执行
```javascript
seajs.use('./a',function(a){
    code....
  })
  // 着重掌握
  seajs.use(['./a','./b'],function(a,b){
    code..
  })
```
* seajs.use 第二个参数是一个函数，内部参数与传入的加载模块的返回值的顺序一致

#### 总结

![图像 1.png](http://upload-images.jianshu.io/upload_images/4071931-90c555599427ed14.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


![图像 2.png](http://upload-images.jianshu.io/upload_images/4071931-3bd1fce1865f145a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


![图像 3.png](http://upload-images.jianshu.io/upload_images/4071931-40750964b2359ec9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


![图像 4.png](http://upload-images.jianshu.io/upload_images/4071931-f9c28a3f102986b5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)



![图像 5.png](http://upload-images.jianshu.io/upload_images/4071931-055972a5dc5c0511.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


![图像 6.png](http://upload-images.jianshu.io/upload_images/4071931-a6655f4b716eadc6.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


![图像 7.png](http://upload-images.jianshu.io/upload_images/4071931-979612060f8ddeff.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)



![图像 8.png](http://upload-images.jianshu.io/upload_images/4071931-322dc147f8820040.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


![图像 9.png](http://upload-images.jianshu.io/upload_images/4071931-278a02434091f7fe.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)