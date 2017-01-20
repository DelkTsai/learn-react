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




