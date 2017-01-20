# learn-react
###重温react.js，并将二次学习成果整理成demo分享给大家
由于之前忙于赶项目进度，匆匆忙忙没来得及将自己的学习心得分享给大家，趁着过年时间宽松，重温react.js，并将二次学习成果整理成demo分享给大家。

[知识点一：React概述](https://github.com/sosout/learn-react/tree/master/react-summary)

[知识点二：React-JSX语法](https://github.com/sosout/learn-react/tree/master/react-jsx)

[知识点二：React基本语法](https://github.com/sosout/learn-react/tree/master/react-grammar)

##React概述
React 是一个用于构建用户界面的 JAVASCRIPT 库。
React主要用于构建UI，很多人认为 React 是 MVC 中的 V（视图）。
React 起源于 Facebook 的内部项目，用来架设 Instagram 的网站，并于 2013 年 5 月开源。
React 拥有较高的性能，代码逻辑非常简单，越来越多的人已开始关注和使用它。
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


