---
title: 闭包
date: 2017-05-04 09:39:35
tags: 
    - JavaScript
    - 前端基础
    - 动态网页编程
categories: 
    - 学习
    - 动态网页编程
---
# 闭包
## 什么是闭包？
> 从本意上来讲就是封闭包裹的意思，而js中函数正好就是一个封闭包裹的空间，所以从广义上来讲认为任何一个函数都是一个闭包
> 
> 从狭义上来讲：**就是某个函数可以访问它外层的函数中定义的变量，认为这个函数就是一个闭包函数**


在函数外部自然无法读取函数内的局部变量，如何从外部读取局部变量？
> 在函数的内部，再定义一个函数，并把内部函数作为返回值，这样就能从外部访问函数内部变量了
```javascript
function f1(){
n=999;
function f2(){
alert(n);
}
return f2;
}
var result=f1();
result(); // 999
```

>**闭包就是能够读取其他函数内部变量的函数**

## 闭包的用途:
1、读取函数内部的变量
2、让这些变量的值始终保持在内存中(优缺共存)
3、避免全局变量的污染

## 使用闭包时的注意点
1. 由于闭包会使得函数中的变量都被保存在内存中，内存消耗很大，所以不能滥用闭包，否则会造成网页的性能问题，在IE中可能导致内存泄露。解决方法是，在退出函数之前，将不使用的局部变量全部删除。
2. 闭包会在父函数外部，改变父函数内部变量的值。所以，如果你把父函数当作对象（object）使用，把闭包当作它的公用方法（Public Method），把内部变量当作它的私有属性（private value），这时一定要小心，不要随便改变父函数内部变量的值

