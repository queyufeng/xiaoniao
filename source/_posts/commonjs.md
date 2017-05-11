---
title: 模块化规范
date: 2017-04-11 11:44:46
tags: 
    - JavaScript
    - 模块化规范
    - 面向对象
categories: 
    - 前端模块化加载框架

---
### 服务器端规范
* [CommonJS](http://www.commonjs.org/)
 - [Node.js](https://nodejs.org/)
 > CommonJS 定义JavaScript语言后端规范 
    + 后端语言应该具备什么能力？ 接收请求、处理底层数据、 模块化定义（Module)

### 浏览器端规范
* [AMD](https://github.com/amdjs/amdjs-api) 
   - [RequireJS](http://requirejs.org/)
 > AMD 也是一种规范的名称，推崇异步加载，遵循依赖前置(加载前置)(提前加载) 

* [CMD](https://github.com/amdjs/amdjs-api)
    - [Seajs](http://seajs.org/) 
      > CMD是一种规范 推崇同步加载 遵循加载滞后，按需加载,懒加载(需要的时候加载)