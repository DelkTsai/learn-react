# learn-react
###重温react.js，并将二次学习成果整理成demo分享给大家
由于之前忙于赶项目进度，匆匆忙忙没来得及将自己的学习心得分享给大家，趁着过年时间宽松，重温react.js，并将二次学习成果整理成demo分享给大家。

[旧版本：直接引入v0.13.3](https://github.com/sosout/learn-react/tree/master/react-0.13.3)

[新版本：直接引入v15.4.2](https://github.com/sosout/learn-react/tree/master/react-15.4.2)

[通过 npm 使用 React](https://github.com/sosout/learn-react/tree/master/react-npm)

##React概述
React 是一个用于构建用户界面的 JAVASCRIPT 库。
React主要用于构建UI，很多人认为 React 是 MVC 中的 V（视图）。
React 起源于 Facebook 的内部项目，用来架设 Instagram 的网站，并于 2013 年 5 月开源。
React 拥有较高的性能，代码逻辑非常简单，越来越多的人已开始关注和使用它。
###相关DEMO
[旧版本：Hello World DEMO](https://github.com/sosout/learn-react/tree/master/react-0.13.3/helloworld.html)

[新版本：Hello World DEMO](https://github.com/sosout/learn-react/tree/master/react-15.4.2/helloworld.html)

[npm: Hello World DEMO](https://github.com/sosout/learn-react/tree/master/react-npm/helloworld.html)
###一、React产生的背景(Facebook)
Facebook需要解决的问题：构建数据不断变化的大型应用。数据变化会产生大量DOM操作(解决办法：React自动DOM操作)和逻辑极其复杂(解决办法：状态对应内容)。

1.数据交互繁重的应用编写困难

2.整体DOM渲染性能瓶颈
###二、特点
1.声明式设计 −React采用声明范式，可以轻松描述应用。

2.高效 −React通过对DOM的模拟，最大限度地减少与DOM的交互。

3.灵活 −React可以与已知的库或框架很好地配合。

4.JSX − JSX 是 JavaScript 语法的扩展。React 开发不一定使用 JSX ，但我们建议使用它。

5.组件 − 通过 React 构建组件，使得代码更加容易得到复用，能够很好的应用在大项目的开发中。

6.单向响应的数据流 − React 实现了单向响应的数据流，从而减少了重复代码，这也是它为什么比传统数据绑定更简单。
###三、优势
1.非声明式的单向数据绑定

2.面向HTML5的组件化

3.高性能的密集DOM操作

4.支持后端渲染(SEO)

5.运行时的编码规范辅助

6.可靠的维护者Facebook

7.React Native
###四、不足
1.没有同类库生态成熟(jQuery, Angular)

2.增加了调试复杂度(JSX)

3.源码gzip后有35KB
###五、与之前组件开发的差异
1.Javascript与HTML被整合在一起

传统：选中DOM，通过数据设置和调整DOM

React：根据数据声明DOM
###六、适用场景
1.复杂场景下的高性能

2.重用组件库，组件组合

3.团队多人合作时
###七、非适用场景
1.UI交互极少的应用

2.需要之前IE8以下版本的浏览器

##React 安装
React 可以直接下载使用，下载包中也提供了很多学习的实例。我这边旧版的React的版本为0.13.3，新版的版本为15.4.2。

###一、旧版
旧版中我们引入了三个库： react.js 和 JSXTransformer.js：

1.react.js - React 的核心库

2.JSXTransformer.js - 用于将 JSX 语法转为 JavaScript 语法

如果我们需要使用 JSX，则 &lt;script&gt; 标签的 type 属性需要设置为 text/babel。

###二、新版
新版中我们引入了三个库： react.js 、react-dom.js 和 browser.min.js：

1.react.js - React 的核心库

2.react-dom.js - 提供与 DOM 相关的功能

3.browser.min.js - 用于将 JSX 语法转为 JavaScript 语法

如果我们需要使用 JSX，则 &lt;script&gt; 标签的 type 属性需要设置为 text/babel。

###三、通过 npm 使用 React
建议在 React 中使用 CommonJS 模块系统，比如 browserify 或 webpack，我这边使用的 webpack。

1.创建一个项目目录，比如我这边为react-npm，再使用npm init初始化，生成package.json文件：
```js
# 将一个 h1 标题，插入 example 节点
mkdir react-npm
cd react-npm
npm init
name: (react-npm) react-npm
version: (1.0.0) 
description: 
entry point: (index.js) 
test command: 
git repository: 
keywords: 
author: 
license: (ISC) 
......

Is this ok? (yes)
```

2.添加依赖包及插件

(1)全局包
```js
npm install babel -g
npm install webpack -g
```
(2)依赖包

因为我们要使用 React, 所以我们需要先安装它，--save 命令用于将包添加至 package.json 文件。

```js
npm install react --save
npm install react-dom --save
```

(3)插件

同时我们也要安装一些 babel 插件

```js
npm install babel-core
npm install babel-loader
npm install babel-preset-react
npm install babel-preset-es2015
```

3.创建文件

接下来我们创建一些必要文件：index.html、App.jsx、main.js、webpack.config.js

4、编辑

(1)打开 webpack.config.js 文件添加以下代码:

```js
# entry: 指定打包的入口文件 main.js。
# output：配置打包结果，path定义了输出的文件夹，filename则定义了打包结果文件的名称。
# devServer：设置服务器端口号为 8888，端口后你可以自己设定 。
# module：定义了对模块的处理逻辑，这里可以用loaders定义了一系列的加载器，以及一些正则。当需要加载的文件匹配test的正则时，就会调用后面的loader对文件进行处理，这正是webpack强大的原因。
var config = {
    entry: './main.js',
    output: {
        path: './',
        filename: 'index.js'
    },
    devServer: {
        inline: true,
        port: 8888
    },
    module: {
        loaders: [{
            test: /\.jsx?$/,
            exclude: /node_modules/,
            loader: 'babel',
            query: {
                presets: ['es2015', 'react']
            }
        }]
    }
};

module.exports = config;

```
(2)现在打开 package.json 文件，找到 "scripts" 中的 "test" "echo \"Error: no test specified\" && exit 1" 使用以下代码替换：
```js
"start": "webpack-dev-server --hot"
```

替换后的 package.json 文件 内容如下：
```js
#现在我们可以使用 npm start 命令来启动服务。--hot 命令会在文件变化后重新载入，这样我们就不需要在代码修改后重新刷新浏览器就能看到变化。
{
  "name": "react-npm",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "start": "webpack-dev-server --hot"
  },
  "author": "",
  "license": "ISC",
  "devDependencies": {
    "babel-core": "^6.22.0",
    "babel-loader": "^6.2.10",
    "babel-preset-es2015": "^6.22.0",
    "babel-preset-react": "^6.22.0",
    "webpack": "^1.14.0",
    "webpack-dev-server": "^1.16.2"
  },
  "dependencies": {
    "react": "^15.4.2",
    "react-dom": "^15.4.2"
  }
}
```
(3)编辑index.html

设置 div id = "app" 为我们应用的根元素，并引入 index.js 脚本文件。
```js
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
</head>
<body>
	<div id="app"></div>
	<script src="index.js"></script>
</body>
</html>
```
(4)编辑App.jsx 和 main.js

App.jsx 文件代码(react 组件)
```js
import React from 'react';

class App extends React.Component {
  render() {
    return (
      <h1>Hello World</h1>
    );
  }
}

export default App;
```

我们需要引入组件并将其渲染到根元素 App 上，这样我们才可以在浏览器上看到它。

main.js 文件代码
```js
import React from 'react';
import ReactDOM from 'react-dom';

import App from './App.jsx';

ReactDOM.render(<App />, document.getElementById('app'));
```

注意：如果想要组件可以在任何的应用中使用，需要在创建后使用 export 将其导出，在使用组件的文件使用 import 将其导入。

(5)运行服务

完成以上配置后，我们即可运行该服务：
```js
npm start
```

通过浏览器访问 http://localhost:8888/，查看输出结果。

##React-JSX
###一、JSX 语法
JSX语法，像是在Javascript代码里直接写XML的语法，实质上这只是一个语法糖，每一个XML标签都会被JSX转换工具转换成纯Javascript代码，React官方推荐使用JSX，当然你想直接使用纯Javascript代码写也是可以的，只是使用JSX，组件的结构和组件之间的关系看上去更加清晰。
```js
//使用JSX
React.render(
    <div>
        <div>
            <div>content</div>
        </div>
    </div>,
    document.getElementById('example')
);
 
//不使用JSX
React.render(
    React.createElement('div', null,
        React.createElement('div', null,
            React.createElement('div', null, 'content')
        )
    ),
    document.getElementById('example')
);
```
###二、深入理解 JSX

React 使用 JSX 来替代常规的 JavaScript。JSX 是一个看起来很像 XML 的 JavaScript 语法扩展。我们不需要一定使用 JSX，但它有以下优点：

1.JSX 执行更快，因为它在编译为 JavaScript 代码后进行了优化。

2.它是类型安全的，在编译过程中就能发现错误。

3.使用 JSX 编写模板更加简单快速。

####1.为什么要使用 JSX？

你不需要为了 React 使用 JSX，可以直接使用纯粹的 JS。但我们更建议使用 JSX , 因为它能定义简洁且我们熟知的包含属性的树状结构语法。对于非专职开发者（比如设计师）同样比较熟悉。XML 有固定的标签开启和闭合。这能让复杂的树更易于阅读，优于方法调用和对象字面量的形式。它没有修改 JavaScript 语义。

####2.HTML标签 与 React组件 对比

React 可以渲染 HTML 标签 (strings) 或 React 组件 (classes)。

要渲染 HTML 标签，只需在 JSX 里使用小写字母开头的标签名。
```js
var myDivElement = <div className="foo" />;
React.render(myDivElement, document.body);
```
要渲染 React 组件，只需创建一个大写字母开头的本地变量。
```js
var MyComponent = React.createClass({/*...*/});
var myElement = <MyComponent someProperty={true} />;
React.render(myElement, document.body);
```
React 的 JSX 里约定分别使用首字母大、小写来区分本地组件的类和 HTML 标签。

注意：由于 JSX 就是 JavaScript，一些标识符像 class 和 for 不建议作为 XML 属性名。作为替代，React DOM 使用 className 和 htmlFor 来做对应的属性。

####3.转换

JSX 把类 XML 的语法转成纯粹 JavaScript，XML 元素、属性和子节点被转换成 React.createElement 的参数。
```js
var Nav;
// 输入 (JSX):
var app = <Nav color="blue" />;
// 输出 (JS):
var app = React.createElement(Nav, {color:"blue"});
```

JSX 也支持使用 XML 语法定义子结点：
```js
var Nav, Profile;
// 输入 (JSX):
var app = <Nav color="blue"><Profile>click</Profile></Nav>;
// 输出 (JS):
var app = React.createElement(
  Nav,
  {color:"blue"},
  React.createElement(Profile, null, "click")
);
```

注意:
JSX 表达式总是会当作 ReactElement 执行。具体的实际细节可能不同。一种优化 的模式是把 ReactElement 当作一个行内的对象字面量形式来绕过 React.createElement 里的校验代码。

####4.JavaScript 表达式

####1.属性表达式

要使用 JavaScript 表达式作为属性值，只需把这个表达式用一对大括号 ({}) 包起来，不要用引号 ("")。
```js
// 输入 (JSX):
var person = <Person name={window.isLoggedIn ? window.name : ''} />;
// 输出 (JS):
var person = React.createElement(
  Person,
  {name: window.isLoggedIn ? window.name : ''}
);
```
在 JSX 中不能使用 if else 语句，但可以使用 conditional (三元运算) 表达式来替代。

####2.子节点表达式 

同样地，JavaScript 表达式可用于描述子结点：
```js
// 输入 (JSX):
var content = <Container>{window.isLoggedIn ? <Nav /> : <Login />}</Container>;
// 输出 (JS):
var content = React.createElement(
  Container,
  null,
  window.isLoggedIn ? React.createElement(Nav) : React.createElement(Login)
);
```
####3.注释 

注释需要写在花括号中，JSX 里添加注释很容易；它们只是 JS 表达式而已。你只需要在一个标签的子节点内(非最外层)小心地用 {} 包围要注释的部分。
```js
var content = (
  <Nav>
    {/* 一般注释, 用 {} 包围 */}
    <Person
      /* 多
         行
         注释 */
      name={window.isLoggedIn ? window.name : ''} // 行尾注释
    />
  </Nav>
);
```
###三、JSX的延展属性

如果你事先知道组件需要的全部 Props（属性），JSX 很容易地这样写：
```js
var component = <Component foo={x} bar={y} />;
```
####1.修改 Props 是不好的，明白吗?

如果你不知道要设置哪些 Props，那么现在最好不要设置它：
```js
var component = <Component />;
component.props.foo = x; // 不好
component.props.bar = y; // 同样不好
```
这样是反模式，因为 React 不能帮你检查属性类型（propTypes）。这样即使你的 属性类型有错误也不能得到清晰的错误提示。

Props 应该被当作禁止修改的。修改 props 对象可能会导致预料之外的结果，所以最好不要去修改 props 对象。

####2.延展属性

在你可以使用 JSX 的新特性 - 延展属性：
```js
var props = {};
props.foo = x;
props.bar = y;
var component = <Component {...props} />;
```
传入对象的属性会被复制到组件内。

它能被多次使用，也可以和其它属性一起用。注意顺序很重要，后面的会覆盖掉前面的。
```js
var props = { foo: 'default' };
var component = <Component {...props} foo={'override'} />;
console.log(component.props.foo); // 'override'
```
####3.这个奇怪的 ... 标记是什么？

这个 ... 操作符（也被叫做延展操作符 － spread operator）已经被 ES6 数组 支持。相关的还有 ES7 规范草案中的 Object 剩余和延展属性（Rest and Spread Properties）。我们利用了这些还在制定中标准中已经被支持的特性来使 JSX 拥有更优雅的语法。

###四、JSX 的陷阱

JSX 与 HTML 非常相似，但是有些关键区别要注意。

####1.HTML 实体

HTML 实体可以插入到 JSX 的文本中。
```js
<div>First &middot; Second</div>
```

如果想在 JSX 表达式中显示 HTML 实体，可以会遇到二次转义的问题，因为 React 默认会转义所有字符串，为了防止各种 XSS 攻击。
```js
// 错误: 会显示 “First &middot; Second”
<div>{'First &middot; Second'}</div>
```

有多种绕过的方法。最简单的是直接用 Unicode 字符。这时要确保文件是 UTF-8 编码且网页也指定为 UTF-8 编码。
```js
<div>{'First · Second'}</div>
```

安全的做法是先找到 实体的 Unicode 编号 ，然后在 JavaScript 字符串里使用。
```js
<div>{'First \u00b7 Second'}</div>
<div>{'First ' + String.fromCharCode(183) + ' Second'}</div>
```

可以在数组里混合使用字符串和 JSX 元素。
```js
<div>{['First ', <span>&middot;</span>, ' Second']}</div>
```

万不得已，可以直接使用原始 HTML。
```js
<div dangerouslySetInnerHTML={{__html: 'First &middot; Second'}} />
```
####2.自定义 HTML 属性

如果往原生 HTML 元素里传入 HTML 规范里不存在的属性，React 不会显示它们。如果需要使用自定义属性，要加 data- 前缀。
```js
<div data-custom-attribute="foo" />
```

以 aria- 开头的 [网络无障碍] 属性可以正常使用。
```js
<div aria-hidden={true} />
```

###五、独立文件

你的 React JSX 代码可以放在一个独立文件上，例如我们创建一个 helloworld.js 文件，代码如下：
```js
ReactDOM.render(
  <h1>Hello, world!</h1>,
  document.getElementById('example')
);
```
然后在 HTML 文件中引入该 JS 文件：
```js
<body>
  <div id="example"></div>
<script type="text/babel" src="helloworld_react.js"></script>
</body>
```

###五、疑惑

####1.jsx语法还能用吗?

0.14分离了react 和 react-dom，很多小伙伴错误的以为JSXTransformer.js 就可以不用了?其实并不是不用了。举个例子 一般都使用Webpack打包项目，里面可能会用到一些loader 这其中就有React-loader ，它就替代了JSXTransform的工作。要理解JSX这种语法最终还是要转变为浏览器识别的JS代码。

##React 组件

##在React中使用Redux数据流

###一、问题

####1.数据流是什么？

数据流是我们的行为与响应的抽象。

####2.为什么要用数据流？

使用数据流帮助我们明确了行为对应的响应。

####3.React与数据流的关系

React是纯V层框架，需要数据流进行支撑。

###二、单向数据流

####1.MVC

![](https://github.com/sosout/learn-react/blob/master/2017012301.png)

流程：用户一个Action作用在Controller，Controller分发到各个Model，Model层向view层传递信息，同时view层再返回过来作用在Model上


####2.Flux(单向数据流)

![](https://github.com/sosout/learn-react/blob/master/2017012302.png)

流程：All Action 由同一个Dispatcher分发到若个store(保存着数据和页面的状态)，一个store只能向后向页面传递信息，而不允许view层再返回过来作用在store上

###三、Redux概述

Redux是Flux框架的一种实现方法。

![](https://github.com/sosout/learn-react/blob/master/2017012303.png)

流程：页面渲染完成，UI展现出来了。用户触发(trigger)页面上的Actions,然后Actions被传递到一个Reducer方法中，Reducer更新Store的数据即state


