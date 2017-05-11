---
title: requireJS学习
date: 2017-04-11 11:49:09
tags: 
    - JavaScript
    - 模块化规范
    - 面向对象
    - Requirejs
categories: 
    - 前端模块化加载框架
---

#### requireJS
* requireJS也可以用Seajs写法,不建议，因为思想冲突，代码风格不再是加载前置了
* 1: 引包
* 2：开启程序入口模块 requirejs(['./a','./b'],function(a,b){code..})
  + seajs.use(['./a','./b'],function(a,b){code..});
* 3: 定义一个模块 define(依赖项数组,返回值的回调);
  + define(function(require,exports,module){code..});
* 4: 向外暴露 return
  + seajs: module.exports || exports 挂载属性
* 5: 需要拿到别的模块的暴露值，参考第三点中的返回值回调  
  + seajs：require
#### seajs和 requireJS比较
* requireJS加载前置，声明前置 （需要什么提前准备好）
  + 首先加载文件前,检查该文件是否有依赖，如果有依赖，先加载依赖模块，再加载本身模块.
* seajs加载：懒加载，延迟加载，加载滞后（什么时候，什么时候加载）
* 玉伯：seajs:明显没有bug —— requirejs: 没有明显的bug
* 我个人认为requireJS可能用得比较多一点
  + requirejs加载机制,思想更贴合前端开发引入标签的模式
  + 加载的机制，在web端，可能因为网络或者卡顿，不太会出现出来一部分，另一部分白的
  + 懒加载思想就是节省资源
 
 ####图解seajs和 requireJS

![requirejs和seajs.png](http://upload-images.jianshu.io/upload_images/4071931-ee3ab4fe5e6c4285.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
