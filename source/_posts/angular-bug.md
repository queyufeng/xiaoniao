---
title: angular常见问题解答
date: 2017-04-11 11:55:15
tags: 
    - JavaScript
    - angular
categories: 
    - 前端主流框架
    - angular
---
# angular常见问题解答
**-----------------------------------------------**
1. angularjs 是mvc还是mvvm框架

  * **首先阐述下你对mvc和mvvm的理解**

	>首先为什么我们会需要MVC？因为随着代码规模越来越大，切分职责是大势所趋，还有为了后期维护方便，修改一块功能不影响其他功能。还有为了复用，因为很多逻辑是一样的。而MVC只是手段，终极目标是模块化和复用。


   * **mvvm的优点**

		* 低耦合：View可以独立于Model变化和修改，同一个ViewModel可以被多个View复用；并且可以做到View和Model的变化互不影响；

		* 可重用性：可以把一些视图的逻辑放在ViewModel，让多个View复用；

		* 独立开发：开发人员可以专注与业务逻辑和数据的开发（ViewModemvvmdi计人员可以专注于UI(View)的设计；

		*	可测试性：清晰的View分层，使得针对表现层业务逻辑的测试更容易，更简单。

* **在angular中MVVM模式主要分为四部分：**

		*	View：它专注于界面的显示和渲染，在angular中则是包含一堆声明式Directive的视图模板。
		*	ViewModel：它是View和Model的粘合体，负责View和Model的交互和协作，它负责给View提供显示的数据，以及提供了View中Command事件操作Model的途径；在angular中$scope对象充当了这个ViewModel的角色
		*	Model：它是与应用程序的业务逻辑相关的数据的封装载体，它是业务领域的对象，Model并不关心会被如何显示或操作，所以模型也不会包含任何界面显示相关的逻辑。在web页面中，大部分Model都是来自Ajax的服务端返回数据或者是全局的配置对象；而angular中的service则是封装和处理这些与Model相关的业务逻辑的场所，这类的业务服务是可以被多个Controller或者其他service复用的领域服务。
		*	Controller：这并不是MVVM模式的核心元素，但它负责ViewModel对象的初始化，它将组合一个或者多个service来获取业务领域Model放在ViewModel对象上，使得应用界面在启动加载的时候达到一种可用的状态。


![](http://upload-images.jianshu.io/upload_images/4071931-0316d3f61152f855.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)



mvc的界面和逻辑关联紧密，数据直接从数据库读取。mvvm的界面与viewmode是松耦合，界面数据从viewmodel中获取。所以angularjs更倾向于mvvm

**-----------------------------------------------**
* angularjs中$scope，controller，directive，sevice在mvvm中充当什么角色

如果你不知道，第一题的分析以及很明确，仔细再仔细的看一遍
**-----------------------------------------------**

* 在使用angularjs项目开发中 你使用过那些第三方的插件
AngularUi  ui-router oclazyload等等  附上一篇文章仔细去看看 https://segmentfault.com/a/1190000003858219

**-----------------------------------------------**
* 在angular项目中你如何控制静态资源的合理加载
第三题提到了oclazyload这个插件，很好的一个懒加载静态资源的第三方插件

**-----------------------------------------------**
* 再写controlloer逻辑的时候 你需要注意什么？
   *  简化代码（这个是所有开发人员都要具备的）
   * 坚决不能操作dom节点 这个时候可能会问 为什么不能啊
你的回答是：DOM操作只能出现在指令（directive）中。最不应该出现的位置就是服务（service）中。Angular倡导以测试驱动开发，在service或者controller中出现了DOM操作，那么也就意味着的测试是无法通过的。当然，这只是一点，重要的是使用Angular的其中一个好处是啥，那就是双向数据绑定，这样就能专注于处理业务逻辑，无需关系一堆堆的DOM操作。如果在Angular的代码中还到处充斥着各种DOM操作，那为什么不直接使用jquery去开发呢。

测试驱动开发是什么呢？普及一下：
测试驱动开发，英文全称Test-Driven Development，简称TDD，是一种不同于传统软件开发流程的新型的开发方法。它要求在编写某个功能的代码之前先编写测试代码，然后只编写使测试通过的功能代码，通过测试来推动整个开发的进行。这有助于编写简洁可用和高质量的代码，并加速开发过程。

**-----------------------------------------------**
* AngularJS的数据双向绑定是怎么实现的？
1、每个双向绑定的元素都有一个watcher
2、在某些事件发生的时候，调用digest脏数据检测。
这些事件有：表单元素内容变化、Ajax请求响应、点击按钮执行的函数等。
3、脏数据检测会检测rootscope下所有被watcher的元素。
$digest函数就是脏数据监测
又附上一篇原理性的文章 https://github.com/xufei/Make-Your-Own-AngularJS/blob/master/01.md

**-----------------------------------------------**
* controller之间怎么通讯
  * event
这里可以有两种方式，一种是$scope.$emit，然后通过监听$rootScope的事件获取参数；另一种是$rootScope.$broadcast，通过监听$scope的事件获取参数。
这两种方法在最新版本的Angular中已经没有性能区别了，主要就是事件发送的方向不同，可以按实际情况选择。
  * service
可以创建一个专用的事件Service，也可以按照业务逻辑切分，将数据存储在相应的Service
  * $rootScope
这个方法可能会比较dirty一点，胜在方便，也就是把数据存在$rootScope中，这样各个子$scope都可以调用，不过需要注意一下生命周期
  * 直接使用$scope.$$nextSibling及类似的属性
类似的还有$scope.$parent。这个方法的缺点就更多了，官方不推荐使用任何$$开头的属性，既增加了耦合，又需要处理异步的问题，而且scope的顺序也不是固定的。不推荐
另外就是通过本地存储、全局变量或者现代浏览器的postMessage来传递参数了，除非特殊情况，请避免这类方式。

**-----------------------------------------------**
* 自定义指令的几个参数
说几个常用的如：
restrict:指令在dom中的声明形式 E（元素）A（属性）C（类名）M（注释）
template：两种形式，一种HTML文本；一个可以接受两个参数的函数，tElemetn和tAttrs，并返回一个代表模板的字符串。模板字符串必须存在一个根DOM元素
templateUrl:两种形式，一种代表外部HTML文件路径的字符串；一个可以接受两个参数的函数，参数为tElement和tAttrs，并返回一个外部HTML文件路径的字符串
compile (对象或函数)：compile 选项可以返回一个对象或函数。如果设置了 compile 函数,说明我们希望在指令和实时数据被放到DOM中之前进行DOM操作,在这个函数中进行诸如添加和删除节点等DOM操作是安全的。本质上,当我们设置了 link 选项,实际上是创建了一个 postLink() 链接函数,以便 compile() 函数可以定义链接函数。
然后又是传送门：[http://www.cnblogs.com/mliudong/p/4180680.html](http://www.cnblogs.com/mliudong/p/4180680.html)
 compile和link的区别：
编译的时候，compile转换dom，碰到绑定监听器的地方就先存着，有几个存几个，到最后汇总成一个link函数，一并执行，提升了性能。

**-----------------------------------------------**
* angular中的$http
$http 是 AngularJS 中的一个核心服务，用于读取远程服务器的数据。
我们可以使用内置的$http服务直接同外部进行通信。$http服务只是简单的封装了浏览器原生的XMLHttpRequest对象
1、链式调用
$http服务是只能接受一个参数的函数，这个参数是一个对象，包含了用来生成HTTP请求的
配置内容。这个函数返回一个promise对象，具有success和error两个方法。
2、返回一个promise对象
3、快捷的get请求
4、响应对象
传送门：[https://github.com/facebook/flux](https://github.com/facebook/flux)

**-----------------------------------------------**
* angular和jquery的区别
angular是基于数据驱动，所以angular适合做数据操作比较繁琐的项目（这里可以再提一下单页面应用，如果你不会福利又来了 http://www.zhihu.com/question/20792064）
jquery是基于dom驱动，jquery适合做dom操作多的项目

**-----------------------------------------------**
* 对angular中的form表单了解多少
Angular对input元素的type进行了扩展，一共提供了以下10种类型： 
text
number
url
email
radio
checkbox
hidden
button
submit
reset
Angular为表单内置了4中CSS样式。 
ng-valid 校验合法状态
ng-invalid 校验非法状态
ng-pristine 如果要使用原生的form，需要设置这个值
ng-dirty     表单处于脏数据状态
Angular在对表单进行自动校验的时候会校验Model上的属性，如果不设置ng-model，则Angular无法知道myForm.$invalid这个值是否为真。
校验的一下内容
required 表示是否输入内容
ng-maxlength 最大长度
ng-minlength 最小长度
例子：传送门[https://github.com/18500047564/clutter](https://github.com/18500047564/clutter)

**-----------------------------------------------**
* ng-show/ng-hide 与 ng-if 的区别？
我们都知道ng-show/ng-hide实际上是通过 display 来进行隐藏和显示的。而ng-if实际上控制dom节点的增删除来实现的。因此如果我们是根据不同的条件来进行dom节点的加载确认的话，那么ng-if的性能好过ng-show.

**-----------------------------------------------**
* 解释下什么是 $rootScrope 以及和 $scope 的区别？
$rootScrope是所有$scope的父对象

**-----------------------------------------------**
* 表达式 `{`{yourModel`}`}` 是如何工作的？
它依赖于 $interpolation服务，在初始化页面html后，它会找到这些表达式，并且进行标记，于是每遇见一个 `{`{` `}` `}` ，则会设置一个 $watch 。而 $interpolation 会返回一个带有上下文参数的函数，最后该函数执行，则算是表达式 $parse 到那个作用域上。

**-----------------------------------------------**
* fliter是什么你了解的有多少？实现一个自定义fliter
ng 内置的 filter 有九种：
date（日期）
currency（货币）
limitTo（限制数组或字符串长度）
orderBy（排序）
lowercase（小写）
uppercase（大写）
number（格式化数字，加上千位分隔符，并接收参数限定小数点位数）
filter（处理一个数组，过滤出含有某个子串的元素）
json（格式化 json 对象）
filter 有两种使用方法，
一种是直接在页面里：
**`<p>`{``{``now | date : ‘yyyy-MM-dd’`}`}``</p>`**
另一种是在 js 里面用：
$filter('过滤器名称')(需要过滤的对象, 参数1, 参数2,...)
$filter('date')(now, 'yyyy-MM-dd hh:mm:ss’);
自定义一个去重数组的:
```javascript
app.filter('unique', function(){
    return function(arr){
        var n = [];
        var obj = {};

        for(var i = 0;i<arr.length;i++){
           if(!obj[arr[i]]){
            n.push(arr[i])
            obj[arr[i]] = 1;
           } 
        }

       return n;
    }
})
```
