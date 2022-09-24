<h3>keep-alive

<keep-alive include="home，about”>component name</keep-alive>

会被缓存起来，不会被销毁。下次切换到此组件，不会调用created和mounted

include=“需要缓存的名字”

需要包裹的组件内部添加有name属性，表示当前组件名字

数组写法 :include="[a,b]"  正则写法 :include="/a|b/"

exclude 除了 max 最多



![1664009081820](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1664009081820.png)

监听是否进行了切换

activated() {

​	组件进入活跃状态调用

}

deactivated(){

​	离开组件，进入不活跃状态

}

<h3>异步组件

**webpack对代码分包** 

import("url").then(res=>{

​	

})

**Vue中的实现异步组件，一般使用路由懒加载**

import {defineAsyncComponent} from "vue"

const AsyncAbout = defineAsyncComponent(()=>import("url"))