<h3>React Hooks

![1664444725764](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1664444725764.png)

![1664444969962](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1664444969962.png)

![1664445079504](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1664445079504.png)

![1664446390543](D:\Project\resoure\资料\笔记\React Hooks.png)



**只能在顶层使用hooks**

![1664447132623](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1664447132623.png)

![1664447943883](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1664447943883.png)

**useState相当于取代this.state**

**Effect取代componentDidmount**

![1664512817080](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1664512817080.png)

**清除副作用**![1664513291076](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1664513291076.png)

![1664513405926](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1664513405926.png)

![1664513682141](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1664513682141.png)

![1664514041007](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1664514041007.png)

第二个参数为[],相当于执行componentWillUNmount生命周期.传入哪个参数,就是该参数改变就会重新执行.

![1664514113249](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1664514113249.png)

**次重点**

![1664515304243](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1664515304243.png)

![1664515902902](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1664515902902.png)

了解

![1664516464904](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1664516464904.png)

**useCallBack的优点和用法**

useCallBack的第二个参数里有的变量发生改变,才会更新组件

![1664518703318](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1664518703318.png)

![1664518936119](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1664518936119.png)

**useRef**

解决闭包陷阱,避免不必要的渲染

![1664524375073](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1664524375073.png)

![1664525133040](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1664525133040.png)

![1664525354267](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1664525354267.png)

![1664528731135](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1664528731135.png)

获取DOM

![1664528796590](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1664528796590.png)

![1664529496971](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1664529496971.png)

![1664529547477](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1664529547477.png)

![1664529793748](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1664529793748.png)

![1664530397091](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1664530397091.png)

在 react中 hook 只能以use开头

![1664531253421](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1664531253421.png)

**自定义localStorage 的Hook**

![1664532641455](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1664532641455.png)

![](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1664601923353.png)

useSelector 的第二个参数是shallowEqual

安装

npm i @reduxjs/toolkit react-redux

![1664600406990](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1664600406990.png)

**memo高阶组件只有props发生改变才会重新渲染**

**state监听的所有的变量,有一个发生变化,别的也会刷新,导致其他组件也会重新渲染.所以需要在useSelector函数的第二个参数加上shallowEqual参数,进行浅层比较.**

![](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1664603443201.png)



**SPA存在的问题**

SEO优化问题:主要爬取index文件,spa的index文件并没有多少关键字

首屏渲染速度问题:执行js,bundl.js文件.太消耗时间,ssr不需要在执行js文件,直接渲染

![1664603753419](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1664603753419.png)

![1664603927952](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1664603927952.png)

![1664620163768](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1664620163768.png)

![1664620188214](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1664620188214.png)

安装faker

@faker-js/faker

loading显示可以用,降低任务的优先级,延迟反应

![1664622109155](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1664622109155.png)

![1664622342987](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1664622342987.png)