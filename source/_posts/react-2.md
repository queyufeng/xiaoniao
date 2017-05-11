---
title: React的四个概念简单介绍
date: 2017-04-11 12:01:16
tags: 
    - JavaScript
    - react
categories: 
    - 前端主流框架
    - react
---
# React的四个概念简单介绍
**React主要有四个主要概念构成，下面分别来介绍一下：**
###Virtual DOM
1. 虚拟DOM是React的基石。
* 之所以引入虚拟DOM，一方面是性能的考虑。Web应用和网站不同，一个Web应用 中通常会在单页内有大量的DOM操作，而这些DOM操作很慢。
* 在React中，应用程序在虚拟DOM上操作，这让React有了优化的机会。简单说， React在每次需要渲染时，会先比较当前DOM内容和待渲染内容的差异， 然后再决定如何最优地更新DOM。这个过程被称为reconciliation。
* 除了性能的考虑，React引入虚拟DOM更重要的意义是提供了一种一致的开发方 式来开发服务端应用、Web应用和手机端应用：

![图片2.png](http://upload-images.jianshu.io/upload_images/4071931-f4a4f89fb9057ad6.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

> 因为有了虚拟DOM这一层，所以通过配备不同的渲染器，就可以将虚拟DOM的内容 渲染到不同的平台。而应用开发者，使用JavaScript就可以通吃各个平台了。相当棒的思路！

2. Virtual DOM速度快的说明
> 在Web开发中，我们总需要将变化的数据实时反应到UI上，这时就需要对DOM进行操作。而复杂或频繁的DOM操作通常是性能瓶颈产生的原因（如何 进行高性能的复杂DOM操作通常是衡量一个前端开发人员技能的重要指标）。React为此引入了虚拟DOM（Virtual DOM）的机制：在浏览器端用Javascript实现了一套DOM API。基于React进行开发时所有的DOM构造都是通过虚拟DOM进行，每当数据变化时，React都会重新构建整个DOM树，然后React将当前 整个DOM树和上一次的DOM树进行对比，得到DOM结构的区别，然后仅仅将需要变化的部分进行实际的浏览器DOM更新。而且React能够批处理虚拟 DOM的刷新，在一个事件循环（Event Loop）内的两次数据变化会被合并，例如你连续的先将节点内容从A变成B，然后又从B变成A，React会认为UI不发生任何变化，而如果通过手动控 制，这种逻辑通常是极其复杂的。尽管每一次都需要构造完整的虚拟DOM树，但是因为**虚拟DOM是内存数据，性能是极高的，而对实际DOM进行操作的仅仅是 Diff部分，因而能达到提高性能的目的。**这样，在保证性能的同时，开发者将不再需要关注某个数据的变化如何更新到一个或多个具体的DOM元素，而只需要 关心在任意一个数据状态下，整个界面是如何Render的。[详情查看](http://blog.csdn.net/yczz/article/details/49585313)

### React组件
* 组件化概念
> 1. 虚拟DOM(virtual-dom)不仅带来了简单的UI开发逻辑，同时也带来了组件化开发的思想，所谓组件，即封装起来的具有独立功能的UI部 件。React推荐以组件的方式去重新思考UI构成，将UI上每一个功能相对独立的模块定义成组件，然后将小的组件通过组合或者嵌套的方式构成大的组件， 最终完成整体UI的构建。例如，Facebook的instagram.com整站都采用了React来开发，整个页面就是一个大的组件，其中包含了嵌套 的大量其它组件，大家有兴趣可以看下它背后的代码。
> 2. 如果说MVC的思想让你做到视图-数据-控制器的分离，那么组件化的思考方式则是带来了UI功能模块之间的分离。我们通过一个典型的Blog评论界面来看MVC和组件化开发思路的区别
> 3. 对于MVC开发模式来说，开发者将三者定义成不同的类，实现了表现，数据，控制的分离。开发者更多的是从技术的角度来对UI进行拆分，实现松耦合。

---
对于React而言，则完全是一个新的思路，开发者从功能的角度出发，将**UI分成不同的组件，每个组件都独立封装。**
在React中，你按照界面模块自然划分的方式来组织和编写你的代码，对于评论界面而言，整个UI是一个通过小组件构成的大组件，每个组件只关心自己部分的逻辑，彼此独立。

![](http://upload-images.jianshu.io/upload_images/4071931-2a9c9141d3171550.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


![](http://upload-images.jianshu.io/upload_images/4071931-91e028ba04406cc7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)



* 组件化开发特性
React认为一个组件应该具有如下特征：
1. **可组合（Composeable）**：一个组件易于和其它组件一起使用，或者嵌套在另一个组件内部。如果一个组件内部创建了另一个组件，那么说父组件拥有（own）它创建的子组件，通过这个特性，一个复杂的UI可以拆分成多个简单的UI组件；
2. **可重用（Reusable）**：每个组件都是具有独立功能的，它可以被使用在多个UI场景；
3. **可维护（Maintainable）**：每个小的组件仅仅包含自身的逻辑，更容易被理解和维护；
4. **可测试（Testable）**：因为每个组件都是独立的，那么对于各个组件分别测试显然要比对于整个UI进行测试容易的多。

* 组件定义
在React中定义一个组件也是相当的容易，组件就是一个 实现预定义接口的JavaScript类：
1. 组件渲染
> ReactDOM.render 是 React 的最基本方法，用于将模板转为 HTML 语言，并插入指定的 DOM 节点。
```javascript
ReactDOM.render(
  <h1>Hello, world!</h1>,
  document.getElementById('example')
  );
```
而这个方法， 必须而且只能返回一个有效的React元素。这意味着，如果你的组件是由多个元素构成的，那么你必须在外边包一个顶层 元素，然后返回这个顶层元素。比如我们创建一个布局组件：
```javascript
render:function(){
    return React.createElement(
        "div",null,
        React.createElement("div",null,"header"),
        React.createElement("div",null,"content"),
        React.createElement("div",null,"footer")
    );
}
```
2. ES5方式定义组件
```javascript
"use strict";
var HelloMessage = React.createClass({
  displayName: "HelloMessage",
render: function render() {
    return React.createElement(
      "div",
      null,
      "Hello ",
      this.props.name
    );
  }
  });
ReactDOM.render(React.createElement(HelloMessage, { name: "John" }), mountNode);
```
3. Jsx中定义组件
```javascript
var HelloMessage = React.createClass({
  render: function() {
    return <div>Hello {this.props.name}</div>;
  }
});
ReactDOM.render(<HelloMessage name="John" />, mountNode);
```
4. ES6中定义组件
```javascript
import './Hello.css';
import './Hello.scss';
import React, {Component} from 'react';
// 内联样式
let style={
    backgroundColor:'blue'
}
export default class Hello extends Component {
    constructor(props) {
        super(props);
        this.state = { count: 'es6'};
    }
    render() {
        return (
            <div>
                <h1 style={style}>Hello world{this.state.count}</h1>
                <br/>
                <image/>
            </div>
        )
            }
}
```



5 注意事项

（1）你的React组件名称的首字母应当大写，关于大小写的差异你会在后面发现。
（2）你应该会注意到div元素的样式类是用 className而不是class声明的，这是因为class 是JavaScript的保留字，渲染后，真实的DOM还会是：
> `<div class="ez-led">Hello, React!</div>`




### Jsx语法
* 什么是jsx
> 在用React写组件的时候，通常会用到JSX语法，粗看上去，像是在Javascript代码里直接写起了XML标签，实质上这只是一个语法糖，每一个 XML标签都会被JSX转换工具转换成纯Javascript代码，当然你想直接使用纯Javascript代码写也是可以的，只是**利用JSX，组件的结 构和组件之间的关系看上去更加清晰**

* Jsx语法使用
HTML 语言直接写在 JavaScript 语言之中，不加任何引号，这就是 JSX 的语法，它允许 HTML 与 JavaScript 的混写。

```javascript
var names = ['Alice', 'Emily', 'Kate'];
ReactDOM.render(
  <div>
  {
    names.map(function (name) {
      return <div>Hello, {name}!</div>
    })
  }
  </div>,
  document.getElementById('example')
);
```
**上面代码体现了 JSX 的基本语法规则：遇到 HTML 标签（以 < 开头），就用 HTML 规则解析；遇到代码块（以 { 开头），就用 JavaScript 规则解析。**

-------
JSX 允许直接在模板插入 JavaScript 变量。如果这个变量是一个数组，则会展开这个数组的所有成员
```javascript
var arr = [
  <h1>Hello world!</h1>,
  <h2>React is awesome</h2>,
];
ReactDOM.render(
  <div>{arr}</div>,
  document.getElementById('example')
);
```
上面代码的arr变量是一个数组，结果 JSX 会把它的所有成员，添加到模板，运行结果如下。

![](http://upload-images.jianshu.io/upload_images/4071931-98d4bc48bbd0b369.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


### Data Flow（单向数据流）
* 传统的mvc

![](http://upload-images.jianshu.io/upload_images/4071931-604b4c06682a5d3e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

到了 Flux 当中, 除了名字改变了, 重要的是大量的 Model 归到了 Store, View 也统一了,从而得到了所谓单向的数据流, 就是 Model 和 View 之间关系非常清晰了。这样需要人为管理的状态就一下少了很多, 结果体现在开发应用的效率当中:
* Flux 
1. 详细学习地址：https://hulufei.gitbooks.io/react-tutorial/content/flux.html
2. React 标榜自己是 MVC 里面 V 的部分，那么 Flux 就相当于添加 M 和 C 的部分，Flux 是 Facebook 使用的一套前端应用的架构模式。
3. 一个 Flux 应用主要包含四个部分：
		1. dispatcher 处理动作分发，维护 Store 之间的依赖关系
		2. stores  数据和逻辑部分
		3. views  React 组件，这一层可以看作 controller-views，作为视图同时响应用户交互
		4. actions  提供给 dispatcher 传递数据给 store
4. 单向数据流
先来了解一下 Flux 的核心“单向数据流“怎么运作的：
Action -> Dispatcher -> Store -> View
更多时候 View 会通过用户交互触发 Action，所以一个简单完整的数据流类似这样：

![](http://upload-images.jianshu.io/upload_images/4071931-7d7e819922568908.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


整个流程如下：
1. 首先要有 action，通过定义一些 action creator 方法根据需要创建 Action 提供给 dispatcher
2. View 层通过用户交互（比如 onClick）会触发 Action
3. Dispatcher 会分发触发的 Action 给所有注册的 Store 的回调函数
4. Store 回调函数根据接收的 Action 更新自身数据之后会触发一个 change 事件通知 View 数据更改了
5. View 会监听这个 change 事件，拿到对应的新数据并调用 setState 更新组件 UI
所有的状态都由 Store 来维护，通过 Action 传递数据，构成了如上所述的单向数据流循环，所以应用中的各部分分工就相当明确，高度解耦了。
这种单向数据流使得整个系统都是透明可预测的。
###Redux
Redux官方中文文档：http://camsong.github.io/redux-in-chinese/index.html

Reflux：https://segmentfault.com/a/1190000002793786?utm_source=tuicool