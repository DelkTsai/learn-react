# learn-react
###重温react.js，并将二次学习成果整理成demo分享给大家
由于之前忙于赶项目进度，匆匆忙忙没来得及将自己的学习心得分享给大家，趁着过年时间宽松，重温react.js，并将二次学习成果整理成demo分享给大家。
##React基本语法
###React.render()
ReactDOM.render 是 React 的最基本方法，用于将模板转为 HTML 语言，并插入指定的 DOM 节点。
```js
# 将一个 h1 标题，插入 example 节点
React.render(
  <h1>Hello, world!</h1>,
  document.getElementById('example')
);
```
###React属性和状态详解
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
