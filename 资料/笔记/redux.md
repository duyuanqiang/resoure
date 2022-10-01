<h3>redux

<h4>纯函数

![1664208888769](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1664208888769.png)

<h4>store

存数据

![1664209314689](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1664209314689.png)

<h4>action

改数据

![1664209515791](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1664209515791.png)

<h4>reducer

![1664209671691](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1664209671691.png)

yarn init -y   生成package.json

yarn add redux

![1664212752080](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1664212752080.png)

<h4>三大原则

![1664213075754](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1664213075754.png)

<h4>使用过程

![1664213108488](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1664213108488.png)

<h4>Redux结构划分

![1664213182890](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1664213182890.png)

![1664214666096](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1664214666096.png)

dispatch(action(参数))

reducer

![1664214771773](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1664214771773.png)



在componentDisMount()订阅调用, render渲染

<h4>封装高阶组件

安装 react-redux

导入 {**Provider**} from "react-redux"

**provider给整个应用程序提供store,别的地方不需要再次导入store**

![1664251707642](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1664251707642.png)

**connect**

拦截about组件,返回一个经过connect函数加持的高阶组件,第一个括号中的参数整合到props中,供About组件使用,.connect()返回值是一个高阶函数,再次调用connect()()

![1664251755790](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1664251755790.png)

![1664255014652](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1664255014652.png)

<h3>中间件

![1664266885188](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1664266885188.png)

<h4>组件中的异步操作


安装redux-thunk

ation返回函数的步骤

![1664266837117](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1664266837117.png)

![1664266284441](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1664266284441.png)

![1664266183484](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1664266183484.png)

<h3>react调试工具

**react-devtool**

**redux-devtool**

开启redux的调试

![1664268912263](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1664268912263.png)

<h4>redux 的模块化

拆分模块,然后将不同的state合并起来

通过导入combineReducers,组合成新的reducer

![1664274379321](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1664274379321.png)

再取每个模块数据,就需要跟上模块名.例如state = store.getState().counter

![1664280164094](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1664280164094.png)