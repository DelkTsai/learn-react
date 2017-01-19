# learn-react
###重温react.js，并将二次学习成果整理成demo分享给大家
由于之前忙于赶项目进度，匆匆忙忙没来得及将自己的学习心得分享给大家，趁着过年时间宽松，重温react.js，并将二次学习成果整理成demo分享给大家。
##React基本语法
###一、React.render()
ReactDOM.render 是 React 的最基本方法，用于将模板转为 HTML 语言，并插入指定的 DOM 节点。
```js
# 将一个 h1 标题，插入 example 节点
React.render(
  <h1>Hello, world!</h1>,
  document.getElementById('example')
);
```
###二、React属性和状态详解
React 中的属性和状态初看之下可以互相替代，但是在 React 的设计哲学中两者有着截然不同的使用方式和使用场景。接下来简单介绍下什么是属性的状态、两者的区别和联系以及如何正确使用属性和状态。

####1.React属性的含义和用法

#####(1)属性的含义

关键字：props(properties的缩写)

使用方法：this.props.?

属性是指一个事物的性质与关系。往往属性是与生俱来的，无法改变的(广义解释)。在react中，属性不可由组件自己直接修改的。

#####(2)属性的用法

```js
# 第一种使用方法：键值对
<ClassName name = "Tom" /> # 字符串

<ClassName name = {Tom} /> # 变量

<ClassName name = {"Tom"} /> # javascript表达式

<ClassName name = {[1,2,3]} /> # 数组

<ClassName name = {FunctionNAme} /> # 定义一个函数

# 第二种方法：三个点的展开对象形式
var props = {
  one: "123",
  two: 321
};
<ClassName {...props} />  #增加三个点可以拿到两个属性了（one和two）
# 第三种方法：setProps形式。通过组件更新属性，不能在组件内部中修改属性的，因为会违背组件设计原则（尽量避免）
var instance = React.render(<HelloWorld></HelloWorld>, document.body);
instance.setProps({name: "Tim"});
```
####2.React的状态的含义和用法

#####(1)状态的含义

React 把组件看成是一个状态机。通过与用户的交互，实现不同状态，然后渲染 UI，让用户界面和数据保持一致。React 里，只需更新组件的 state，然后根据新的 state 重新渲染用户界面（不要操作 DOM）。

#####(2)状态的用法

通过调用setState(data, callback)方法，改变状态，就会触发React更新UI。大部分情况下，我们不需要提供callback函数。React会自动的帮我们更新UI。

#####什么样的组件该有state

大部分的组件应该从props属性中获取数据并渲染。但有的时候组件必须响应用户输入，同服务器交互，这些情况下会用到state。React的官方说法是：尽可能的保持你的组件无状态化。为了实现这个目标，需要保持你的状态同业务逻辑分离，并减少冗余信息，尽可能保持组件的单一职责。

React官方推荐的一种模式就是：构建几个无状态的组件用来渲染数据，在这些之上构建一个有状态的组件同用户和服务交互，数据通过props传递给无状态的组件。我的理解大概就是这样：
```js
<div id="root"></div>
<script type="text/jsx">
    var RenderComponent = React.createClass({
        render: function() {
            return (
                <ul>
                    {
                        this.props['data-list'].map(function(item) {
                            return (<li>{item}</li>)
                        })
                    }
                </ul>
            );
        }
    });

    var StateComponent = React.createClass({
        getInitialState: function() {
            return {list: ['xxx', 'yyy']};
        },
        render: function() {
            return (
                <div>
                    <button onClick={this.handleClick}>click</button>
                    <RenderComponent data-list={this.state.list} />
                </div>
            )
        },
        handleClick: function() {
            this.setState({list: [1, 2, 3]});
        }
    }); 

    React.render(
        <StateComponent />,
        document.getElementById('root')
    );
</script>
```

#####state应该包含什么样的数据

UI交互会导致改变的数据。

#####state不应包含什么样的数据

计算过的数据

组件

从props复制的数据

state应保含最原始的数据，比如说时间，格式化应该交给展现层去做。

组件应在render方法里控制。
