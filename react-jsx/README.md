# learn-react
###重温react.js，并将二次学习成果整理成demo分享给大家
由于之前忙于赶项目进度，匆匆忙忙没来得及将自己的学习心得分享给大家，趁着过年时间宽松，重温react.js，并将二次学习成果整理成demo分享给大家。
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
JSX 是一个看起来很像 XML 的 JavaScript 语法扩展。React 可以用来做简单的 JSX 句法转换。

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

JSX 里添加注释很容易；它们只是 JS 表达式而已。你只需要在一个标签的子节点内(非最外层)小心地用 {} 包围要注释的部分。
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

###五、疑惑

####1.jsx语法还能用吗?

0.14分离了react 和 react-dom，很多小伙伴错误的以为JSXTransformer.js 就可以不用了?其实并不是不用了。举个例子 一般都使用Webpack打包项目，里面可能会用到一些loader 这其中就有React-loader ，它就替代了JSXTransform的工作。要理解JSX这种语法最终还是要转变为浏览器识别的JS代码。
