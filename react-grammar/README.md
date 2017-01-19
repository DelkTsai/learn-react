# learn-react
###重温react.js，并将二次学习成果整理成demo分享给大家
由于之前忙于赶项目进度，匆匆忙忙没来得及将自己的学习心得分享给大家，趁着过年时间宽松，重温react.js，并将二次学习成果整理成demo分享给大家。
##React基本语法
###React属性和状态详解
React 中的属性和状态初看之下可以互相替代，但是在 React 的设计哲学中两者有着截然不同的使用方式和使用场景。接下来简单介绍下什么是属性的状态、两者的区别和联系以及如何正确使用属性和状态。

####1.React属性的含义和用法

#####(1)属性的含义

关键字：props(properties的缩写)

使用方法：this.props.?

属性是指一个事物的性质与关系。往往属性是与生俱来的，无法改变的(广义解释)。在react中，属性不可由组件自己直接修改的。

#####(2)属性的用法

```js
# 用法一：键值对。值可为字符串，数组，javascript表达式，变量等
<HelloWorld name=? /> 

# 用法二：延展方式(...)
var props = {
  one: "123",
  two: 321
};
<HelloWorld {...props} /> 

# 用法三：使用setProps,强烈不建议
var instance = React.render(<HelloWorld></HelloWorld>, document.body);
instance.setProps({name: "Time"});
```
