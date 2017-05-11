---
title: React快速开始+Recat主要知识内容
date: 2017-04-11 11:59:49
tags: 
    - JavaScript
    - react
categories: 
    - 前端主流框架
    - react
---
#React快速开始+Recat主要知识内容
##快速开始
###创建项目文件夹
>` npm  init // 初始化npm配置文件`

### 依赖环境
**在项目根目录下打开命令窗口下载react和react-dom依赖**
> `npm install  react  react-dom --save `
### 创建目录结构

![](http://upload-images.jianshu.io/upload_images/4071931-2509804071f79ac0.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### Hello World
看官网英文官网的：http://facebook.github.io/react/index.html
```javascript
Var React=require(‘react’);
Var ReactDOM=require(‘react-dom’);
var HelloMessage = React.createClass({
  render: function() {
    return <div>Hello {this.props.name}</div>;
  }
});

ReactDOM.render(<HelloMessage name="John" />, mountNode);
```
### 代码编译方式（语法转换）
因为现在都是使用jsx和es6，所以我们需要对js代码进行编译。
**编译转换有分为浏览器中转换和离线转换，但是基本上公司不会用在浏览器中引入转换js转换，所以我们只介绍离线转换**
* react-tools转换
这是react自己提供的，而且是老版本的，因为中文官网还是老版本的api，所以介绍的是这种方式。
>`npm install -g react-tools // 首先安装依赖`

-------------
>`jsx  --watch  src/  build/  // 用命令进行转换，有兴趣的大家自己看一下jsx -h`

参考地址：http://reactjs.cn/react/docs/getting-started.html
* babel转换
英文官网的文档比较新，已经推荐使用babel来进行转换
1.下载依赖
```cmake
npm install --global babel-cli   // 安装babel
npm install babel-preset-react  -dev-save// 安装babel转换jsx的包
npm install babel-preset-es2015 -dev-save// 安装babel转化ES6的包
```
**注意:加了-dev之后，运行npm install不会下载开发依赖，你需要运行**
>`npm install –dev  //从github上下载之后运行这句才能下载开发依赖`

2. 运行命令进行编译
```cmake
babel --presets react src --watch --out-dir build  // 更多命令可运行babel –h查看或者官网
```
3. 将编译之后的js文件在index.html文件中引入

--------
* Gulp-react
https://github.com/sindresorhus/gulp-react

* 开发工具

![](http://upload-images.jianshu.io/upload_images/4071931-71d8b08a7d971b06.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![](http://upload-images.jianshu.io/upload_images/4071931-e6287f242a0f6bae.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


![](http://upload-images.jianshu.io/upload_images/4071931-562020cd62f569b3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)





###语法版本说明
从最新的版本上来看，未来都是要用es6语法



##Recat主要知识内容
### 视图相关概念
* Props（属性，就是element上的attrs，换个名字property，变成复数，即props）
* State（写过view组件的基本都会知道，按钮有三态，Normal，Highlight，Selected，包括extjs，jquery里的大部分ui框架都是有状态的。）
* Event（其实还应该算一个就是dom事件，上面的例子就把onChange的handler编译后的handleChange方法，这要感谢jsx）
了解了上面这些，就可以写代码了，因为
* 属性，解决了view的定义问题，即语义描述
* 状态，是view的有穷状态机，根据状态决定组件ui和行为
* 事件，是view里元素的行为
有穷状态机：http://baike.baidu.com/view/115336.htm

### jsx语法详解
* HTML 转义（了解）
	1. React 会将所有要显示到 DOM 的字符串转义，防止 XSS。所以如果 JSX 中含有转义后的实体字符比如 © (©) 最后显示到 DOM 中不会正确显示，因为 React 自动把 © 中的特殊字符转义了。有几种解决办法：
		* 直接使用 UTF-8 字符 ©
		* 使用对应字符的 Unicode 编码
		* 使用数组组装 `<div>{['cc ', <span>©</span>, ' 2015']}</div>`
		* 直接插入原始的 HTML
		`<div dangerouslySetInnerHTML=`{``{`__html: 'cc © 2015'}} />`

		[dangerouslySetInnerHTML参考文档](http://reactjs.cn/react/tips/dangerously-set-inner-html.html)
	2. 自定义 HTML 属性（了解）
		**如果在 JSX 中使用的属性不存在于 HTML 的规范中，这个属性会被忽略。如果要使用自定义属性，可以用 data- 前缀。文档估计有问题**
可访问性属性的前缀 aria- 也是支持的。
与dom的区别文档：http://reactjs.cn/react/docs/dom-differences.html

	3. 支持的标签和属性
		**如果你要使用的某些标签或属性不在这些支持列表里面就可能被 React 忽略**，必须要使用的话可以提 issue，或者用前面提到的 dangerouslySetInnerHTML。
支持列表：http://reactjs.cn/react/docs/tags-and-attributes.html
	  * 并不是所有的html标签和属性都能在jsx语法中使用
	  * 基本上你能用到的标签的属性，jsx语法都支持
	  * 有些特殊的属性需要注意，必须class属性要变为className属性

		**所有的属性都是驼峰命名的，class 属性和 for 属性分别改为 className 和 htmlFor，来符合 DOM API 规范。**
		
    4. 属性扩散
	  有时候你需要给组件设置多个属性，你不想一个个写下这些属性，或者有时候你甚至不知道这些属性的名称，这时候 spread attributes 的功能就很有用了。
```javascript
	  var props = {};
props.foo = x;
props.bar = y;
var component = <Component {...props} />;
```

![](http://upload-images.jianshu.io/upload_images/4071931-7bf3439bcaa0bfa0.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

```javascript
var props = { foo: 'default' };
var component = <Component {...props} foo={'override'} />;
console.log(component.props.foo); // 'override'
```


   5. 自闭合标签
	   **如果只有一个组件，就用单闭合标签形式，如果有多个组件嵌套就用双闭合标签形式**
http://reactjs.cn/react/tips/self-closing-tag.html
   6. 注释
	  在 JSX 里使用注释也很简单，就是沿用 JavaScript，唯一要注意的是在一个组件的子元素位置使用注释要用 {} 包起来
```javascript
var content = (
  <Nav>
      {/* child comment, put {} around */}
      <Person
        /* multi
           line
           comment */
        name={window.isLoggedIn ? window.name : ''} // end of line comment
      />
  </Nav>
);
```
###React的API
* [**顶层API**I](http://facebook.github.io/react/docs/top-level-api.html)
* [**组件API**](http://facebook.github.io/react/docs/component-api.html)
### 组件的生命周期（特别重要）
组件的生命周期，另外的名字是状态回调，和上面讲的状态的唯一差别，上面的状态是它里面的元素，而组件的生命周期是它自己
**https://hulufei.gitbooks.io/react-tutorial/content/component-lifecycle.html**
* 组件的生命周期分成三个状态：
	1. Mounting：已插入真实 DOM
	2. Updating：正在被重新渲染
	3. Unmounting：已移出真实 DOM
* 处理函数:
	React 为每个状态都提供了两种处理函数，will函数在进入状态之前调用，did 函数在进入状态之后调用，三种状态共计五种处理函数。
	1. componentWillMount()
	2. componentDidMount()
	3. componentWillUpdate(object nextProps, object nextState)
	4. componentDidUpdate(object prevProps, object prevState)
	5. componentWillUnmount()
	
	此外，React 还提供两种特殊状态的处理函数。
    1. componentWillReceiveProps(object nextProps)：已加载组件收到新的参数时调用
    2. shouldComponentUpdate(object nextProps, object nextState)：组件判断是否重新渲染时调用
* 函数调用顺序图

![](http://upload-images.jianshu.io/upload_images/4071931-2d288f0335cc8e70.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

**从上图中我们可以看出来，组件再初始化一次之后就不会再运行上图运行中文字以上的方法，反而里面会有事件监听，从而执行shouleComponentUpdate事件。**
		
* 代码使用
	+ ES5:


```javascript
var Hello = React.createClass({
    getInitialState() {
        return { liked: false };
    },
    render: function() {
        console.log(this.state.liked);
        return(
            <div>
                <h1 style={style}>Hello world</h1>
                <br/>
                <image/>
            </div>
        )
    }
});
module.exports=Hello;
```
+ ES6


```javascript
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

* 参考文章
	生命周期详细介绍：
	+ http://www.cnblogs.com/CHONGCHONG2008/p/5099483.html
	+ http://pinggod.com/2015/React-%E7%BB%84%E4%BB%B6%E7%9A%84%E7%94%9F%E5%91%BD%E5%91%A8%E6%9C%9F/
	+ http://reactjs.cn/react/docs/component-specs.html
* 在ES6中用ES5的写法会报错

![](http://upload-images.jianshu.io/upload_images/4071931-043b33953f4173b6.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### ES5/ES6最新写法对照表
React的：
http://www.tuicool.com/articles/equ2my

ReactNative的
http://bbs.reactnative.cn/topic/15/react-react-native-%E7%9A%84es5-es6%E5%86%99%E6%B3%95%E5%AF%B9%E7%85%A7%E8%A1%A8/2

###事件处理
* 使用
onClick这种进行驼峰命名ES5和ES6的写法不一样，在ES6中要用bind方法绑定this(具体可参照ES5和ES6写法对照表)
```javascript
import React, { Component } from 'react';
import { render } from 'react-dom';

export default class LinkButton extends Component {
    constructor(props) {
        super(props);
        this.state = {liked: false};
    }

    handleClick(e) {
        this.setState({ liked: !this.state.liked });
    }

    render() {
        const text = this.state.liked ? 'like' : 'haven\'t liked';
        return (
            <p onClick={this.handleClick.bind(this)}>
                You {text} this. Click to toggle.
            </p>
        );
    }
}
```
* 参数传递
ES6写法：给事件处理函数传递额外参数的方式：`bind(this, arg1, arg2, ...)`
```javascript
render: function() {
    return <p onClick={this.handleClick.bind(this, param1,param2,param3)}>;
},
handleClick: function(param1,param2,param3, event) {
    // handle click
}
```
* React 支持的事件列表
http://reactjs.cn/react/docs/events.html

### Dom操作
* findDOMNode()方法（了解）
	 首先我们要了解 `ReactDOM.render `组件返回的是对组件的引用也就是组件实例（对于无状态状态组件来说返回 null），注意 JSX 返回的不是组件实例，它只是一个 `ReactElement` 对象。
当组件加载到页面上之后（mounted），你都可以通过` react-dom `提供的` findDOMNode() `方法拿到组件对应的 DOM 元素。
```javascript
import { findDOMNode } from 'react-dom';

// Inside Component class
componentDidMound() {
  const el = findDOMNode(this);
}
```
**`findDOMNode() 不能用在无状态组件上。`**

* 方法二：refs属性
另外一种方式就是通过在要引用的 DOM 元素上面设置一个 ref 属性指定一个名称，然后通过 `this.refs.name` 来访问对应的 DOM 元素。
**如果 ref 是设置在原生 HTML 元素上，它拿到的就是 DOM 元素，如果设置在自定义组件上，它拿到的就是组件实例，这时候就需要通过 `findDOMNode` 来拿到组件的 DOM 元素。**
因为无状态组件没有实例，所以 ref 不能设置在无状态组件上，一般来说这没什么问题，因为无状态组件没有实例方法，不需要 ref 去拿实例调用相关的方法，但是如果想要拿无状态组件的 DOM 元素的时候，就需要用一个状态组件封装一层，然后通过` ref 和 findDOMNode `去获取。


```javascript
import React, { Component } from 'react';

export default class MyInputFocus extends Component {
    constructor(props) {
        super(props);
        this.state={ userInput: '' };
    }

    handleChange(e) {
        console.log(this.refs.theInput.value);
        this.setState({ userInput: e.target.value });
    }

    clearAndFocusInput() {
        this.setState({ userInput: '' }, () => {
            this.refs.theInput.focus();
        });
    }

    render() {
        return (
            <div>
                <div onClick={this.clearAndFocusInput.bind(this)}>
                    Click to Focus and Reset
                </div>
                <input
                    ref="theInput"
                    value={this.state.userInput}
                    onChange={this.handleChange.bind(this)}
                />
            </div>
        );
    }
}

MyInputFocus.defaultProps={
    autoPlay:false,
    maxLoops:10,
}
MyInputFocus.propTypes = {
    autoPlay: React.PropTypes.bool.isRequired,
    maxLoops: React.PropTypes.number.isRequired,
}
```
* 注意事项
	* 你可以使用 ref 到的组件定义的任何公共方法，比如 this.refs.myTypeahead.reset()
	* Refs 是访问到组件内部 DOM 节点唯一可靠的方法
	* Refs 会自动销毁对子组件的引用（当子组件删除时）
	* 不要在 render 或者 render 之前访问 refs
	* 不要滥用 refs，比如只是用它来按照传统的方式操作界面 UI：找到 DOM -> 更新 DOM
###组件的 DOM 事件监听
这篇文章是讲如何给 DOM 元素绑定 React 未提供的事件
```javascript
var Box = React.createClass({
  getInitialState: function() {
    return {windowWidth: window.innerWidth};
  },

  handleResize: function(e) {
    this.setState({windowWidth: window.innerWidth});
  },

  componentDidMount: function() {
    window.addEventListener('resize', this.handleResize);
  },

  componentWillUnmount: function() {
    window.removeEventListener('resize', this.handleResize);
  },

  render: function() {
    return <div>Current window width: {this.state.windowWidth}</div>;
  }
});

React.render(<Box />, mountNode);
```
http://reactjs.cn/react/tips/dom-event-listeners.html
1. 注意添加dom事件的位置
2. 在组件退出的时候，取消监听事件

###数据获取
http://facebook.github.io/react/tips/initial-ajax.html
###表单
表单不同于其他 HTML 元素，因为它要响应用户的交互，显示不同的状态，所以在 React 里面会有点特殊。
* 状态属性
	表单元素有这么几种属于状态的属性：
	1. `value`，对应` <input>` 和 `<textarea>` 所有
	2. `checked`，对应类型为` checkbox` 和 radio 的` <input>` 所有
	3. ` selected`，对应 `<option>` 所有

在 HTML 中 `<textarea>` 的值可以由子节点（文本）赋值，但是在 React 中，要用 value 来设置。
表单元素包含以上任意一种状态属性都支持 onChange 事件监听状态值的更改。
针对这些状态属性不同的处理策略，表单元素在 React 里面有两种表现形式。
* 受控组件
对于设置了上面提到的对应“状态属性“值的表单元素就是受控表单组件，比如

```javascript
render: function() {
    return <input type="text" value="hello"/>;
}
```

一个受控的表单组件，**它所有状态属性更改涉及 UI 的变更都由 React 来控制（状态属性绑定 UI）。比如上面代码里的` <input> `输入框，用户输入内容，用户输入的内容不会显示（输入框总是显示状态属性 value 的值 hello）**，这有点颠覆我们的认知了，所以说这是受控组件，不是原来默认的表单元素了。
如果你希望输入的内容反馈到输入框，就要用 onChange 事件改变状态属性 value 的值：
```javascript
getInitialState: function() {
    return {value: 'hello'};
},
handleChange: function(event) {
    this.setState({value: event.target.value});
},
render: function() {
    var value = this.state.value;
    return <input type="text" value={value} onChange={this.handleChange} />;
}
//使用这种模式非常容易实现类似对用户输入的验证，或者对用户交互做额外的处理，比如截断最多输入140个字符：
handleChange: function(event) {
    this.setState({value: event.target.value.substr(0, 140)});
}
```
* 非受控属性
**和受控组件相对，如果表单元素没有设置自己的“状态属性”，或者属性值设置为 null，这时候就是非受控组件。**
它的表现就符合普通的表单元素，正常响应用户的操作。
同样，你也可以绑定 onChange 事件处理交互。
**如果你想要给“状态属性”设置默认值，就要用 React 提供的特殊属性 defaultValue，对于 checked 会有 defaultChecked，`<option>` 也是使用 defaultValue。**
* 为什么要有受控组件
引入受控组件不是说它有什么好处，而是因为 React 的 UI 渲染机制，对于表单元素不得不引入这一特殊的处理方式。
在浏览器 DOM 里面是有区分 `attribute` 和` property` 的。`attribute` 是在 HTML 里指定的属性，而每个 HTML 元素在 JS 对应是一个 DOM 节点对象，这个对象拥有的属性就是 `property`（可以在 `console` 里展开一个 DOM 节点对象看一下，`HTML attributes` 只是对应其中的一部分属性），`attribute` 对应的 `property` 会从 `attribute` 拿到初始值，有些会有相同的名称，但是有些名称会不一样，比如 `attribute class` 对应的 `property` 就是 `className`。（详细解释：`.prop`，`.prop() `vs `.attr()`）
回到 React 里的 `<input>` 输入框，当用户输入内容的时候，输入框的 `value property `会改变，但是 `value attribute` 依然会是 HTML 上指定的值`（attribute 要用 setAttribute 去更改）`。
React 组件必须呈现这个组件的状态视图，这个视图 HTML 是由 render 生成，所以对于
```javascript
render: function() {
    return <input type="text" value="hello"/>;
}
```
在任意时刻，这个视图总是返回一个显示 hello 的输入框。

* `<select>`的处理
在 HTML 中 `<select>` 标签指定选中项都是通过对应 <option> 的 selected 属性来做的，但是在 React 修改成统一使用 value。
**所以没有一个 selected 的状态属性。**


```javascript
<select value="B">
    <option value="A">Apple</option>
    <option value="B">Banana</option>
    <option value="C">Cranberry</option>
</select>
```

你可以通过传递一个数组指定多个选中项：`<select multiple={true} value={['B', 'C']}>`

###参数传递的判断
**[http://facebook.github.io/react/docs/transferring-props.html](http://facebook.github.io/react/docs/transferring-props.html)**

###组合组件
使用组件的目的就是通过构建模块化的组件，相互组合组件最后组装成一个复杂的应用。
在 React 组件中要包含其他组件作为子组件，只需要把组件当作一个 DOM 元素引入就可以了。

[http://reactjs.cn/react/docs/multiple-components.html](http://reactjs.cn/react/docs/multiple-components.html)
* 循环插入子元素
如果组件中包含通过循环插入的子元素，为了保证重新渲染 UI 的时候能够正确显示这些子元素，每个元素都需要通过一个特殊的 key 属性指定一个唯一值。为了内部 diff 的效率。
```javascript
var TodoList = React.createClass({
    render: function() {
        var createItem = function(item) {
            return <li key={item.id}>{item.text}</li>;
        };
        return <ul>{this.props.items.map(createItem)}</ul>;
    }
});
module.export=TodoList
```
1. 当 React 校正带有 key 的子级时，它会确保它们被重新排序（而不是破坏）或者删除（而不是重用）。 **务必 把 key 添加到子级数组里组件本身上**，而不是每个子级内部最外层 HTML 上。
2. 也可以传递 object 来做有 key 的子级。object 的 key 会被当作每个组件的 key。但是一定要牢记 JavaScript 并不总是保证属性的顺序会被保留。实际情况下浏览器一般会保留属性的顺序，除了 使用 32位无符号数字做为 key 的属性。数字型属性会按大小排序并且排在其它属性前面。一旦发生这种情况，React 渲染组件的顺序就是混乱。可能在 key 前面加一个字符串前缀来避免：
```javascript
render: function() {
    var items = {};

    this.props.results.forEach(function(result) {
      // 如果 result.id 看起来是一个数字（比如短哈希），那么
      // 对象字面量的顺序就得不到保证。这种情况下，需要添加前缀
      // 来确保 key 是字符串。
      items['result-' + result.id] = <li>{result.text}</li>;
    });

    return (
      <ol>
        {items}
      </ol>
    );
  }
```
* 子级
组件标签里面包含的子元素会通过父元素的`props.children` 传递进来。
HTML 元素会作为 React 组件对象、JS 表达式结果是一个文字节点，都会存入 Parent 组件的 `props.children`。
`props.children` 通常是一个组件对象的数组，但是当只有一个子元素的时候，`props.children `将是这个唯一的子元素，而不是数组了

```javascript
var NotesList = React.createClass({
  render: function() {
    return (
      <ol>
      {
        React.Children.map(this.props.children, function (child) {
          return <li>{child}</li>;
        })
      }
      </ol>
    );
  }
});

ReactDOM.render(
  <NotesList>
    <span>hello</span>
    <span>world</span>
  </NotesList>,
  document.body
);
```
上面代码的 NoteList 组件有两个 span 子节点，它们都可以通过 this.props.children 读取，运行结果如下。

![](http://upload-images.jianshu.io/upload_images/4071931-2570cb0262e72f61.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

这里需要注意， `this.props.children `的值有三种可能：如果当前组件没有子节点，它就是 undefined ;如果有一个子节点，数据类型是 object ；如果有多个子节点，数据类型就是 array 。所以，处理 `this.props.children` 的时候要小心。
React 提供一个工具方法 `React.Children` 来处理 `this.props.children `。我们可以用 React.Children.map 来遍历子节点，而不用担心` this.props.children` 的数据类型是 undefined 还是 object。更多的 `React.Children `的方法，请参考官方文档。
###propsType
[http://www.reactjs.cn/react/docs/reusable-components.html](http://www.reactjs.cn/react/docs/reusable-components.html)

###Context
[http://facebook.github.io/react/docs/context.html](http://facebook.github.io/react/docs/context.html)
###动画
[http://facebook.github.io/react/docs/animation.html](http://facebook.github.io/react/docs/animation.html)
[http://blog.csdn.net/lihongxun945/article/details/46778723](http://blog.csdn.net/lihongxun945/article/details/46778723)
[https://zhuanlan.zhihu.com/p/20419592](https://zhuanlan.zhihu.com/p/20419592)
###获取react常用插件的网址
[https://js.coach/react/react-infinite](https://js.coach/react/react-infinite)
[https://react.parts/native](https://react.parts/native)

####diff算法
[http://blog.csdn.net/lihongxun945/article/details/46640503](http://blog.csdn.net/lihongxun945/article/details/46640503)
[http://reactjs.cn/react/docs/reconciliation.html](http://reactjs.cn/react/docs/reconciliation.html)
[http://blog.csdn.net/yczz/article/details/49585283](http://blog.csdn.net/yczz/article/details/49585283)
[http://blog.csdn.net/yczz/article/details/49886061](http://blog.csdn.net/yczz/article/details/49886061)
###Web Components 
[http://www.oschina.net/p/polymer](http://www.oschina.net/p/polymer)
[http://facebook.github.io/react/docs/webcomponents.html](http://facebook.github.io/react/docs/webcomponents.html)

####服务器渲染
[http://zhuanlan.zhihu.com/p/20669111?](http://zhuanlan.zhihu.com/p/20669111?)from=groupmessage&isappinstalled=0
###组件间通信
* 非父子组件间的通信
使用全局事件 Pub/Sub 模式，在 componentDidMount 里面订阅事件，在 componentWillUnmount 里面取消订阅，当收到事件触发的时候调用 setState 更新 UI。
这种模式在复杂的系统里面可能会变得难以维护，所以看个人权衡是否将组件封装到大的组件，甚至整个页面或者应用就封装到一个组件。
一般来说，对于比较复杂的应用，推荐使用类似 Flux 这种单项数据流架构，参见Data Flow。Flux和redux
* 数据流Flux
Github地址：[https://github.com/facebook/flux](https://github.com/facebook/flux)

	**React   redux  react-redux   react-router     webpack+gulp  ES6  babel**
	**Mocha+chai  node**
	 **React native  Flex  fetch  原生  找插件**