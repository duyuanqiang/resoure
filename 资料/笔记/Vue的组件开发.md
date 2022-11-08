Vue的组件开发

全局组件和局部组件

组件命名,一般大驼峰或者横杠分隔,html不区分大小写,大驼峰形式在js中,在html用横杠形式

注册全局组件

1.注册App跟组件

const App={}

2.创建 app

const app=Vue.createApp（App）

3注册一个全局组件

app.component（“product-item”，{

​	template:"#item"	

}）

全局组件一般就是组件库,路由组件,状态库

子组件主要通过关键字components:{子组件名:子组件}

![1667636662096](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667636662096.png)

**脚手架**

npm install @vue/cli -g

npm update @vue/cli -g

vue create project-name

**vue.config.js**

1.在**vue.config.js** 中配置项目配置.例如别名

**js.config.json**

在**js.config.json**里面路径配置提示,

引入vue的版本

.vue文件有自己的作用域

vue模板编译过程

template - createVNode()-VNode-虚拟DOM-真实DOM

在非.vue文件中需要源码中的compile完成

.vue文件中通过vue-loader完成

插件volar

子组件需要在js中先导入,注册 components:{},在html使用大驼峰或者横杠



在style中设置 scoped

vue create  基于webpack  npm install vue@latest 基于vite

组件的嵌套

**组件的通信**

**父传子** props  一般用对象类型 props:{name:{type:"",required:true,default:"kobe"}}

传入的对象类型必须是函数返回一个对象

obj:{type:Object,default(){return message:"hello"}}或者()=>({})

arr:{type:Array,default(){return message:[]}}或者()=>[]

如果当前传递一个非props的attribute的元素，会添加到子组件的根元素的attribute上，通过:class="$attrs.class"拿到相应的属性

props:{inheritAttrs:false} 禁止继承,

多个根组件,通过 v-bind=“$attrs”指定绑定的根元素

**子传父**  $emit

![1667703902624](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667703902624.png)

在子组件里面定义

emits:[放入自定义事件方法名]

对传入的参数进行验证,v3新特性

![1667704214932](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667704214932.png)

**插槽**

在子组件中使用slot元素进行占位,在父组件中用子组件,就可以传入自己需要的元素,会在子组件中显示.slot中元素包裹的是默认内容

**具名插槽**,解决多个slot的问题

父组件\<template v-slot:name>内容\<template/>

子组件 \<div class="name">\<slot>\</slot>\</div>

动态修改插槽名字

在data中定义变量name, v-slot:[name],动态修改name

**语法糖写法 #代替v-slot:**

**渲染作用域**

父级模板都是在父级作用域中编写

子组件的内容都是在子组件作用域编写

**插槽中的子组件数据动态获取**.将子组件的值通过插槽传入到父组件中

子组件\<slot :item="item" abc="abc">\</slot>

父组件 <template #default="props">{{props.item}}\</template>

![1667707367717](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667707367717.png)

简写

![1667707554380](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667707554380.png)

![1667707591464](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667707591464.png)

非父子传值

provide和Inject

![1667723113752](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667723113752.png)

获取data数据provide必须写成函数形式

![1667723265577](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667723265577.png)

想要响应式数据导出computed包裹数据函数

![1667723834848](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667723834848.png)

**eventBus**

安装hy-event-bus,

在utils文件中解构出来 eventbus类,生成实例

const eventBus = new eventBus()

导入eventBus

eventBus.emit("eventname",...arg)

导出eventBus

eventBus.on("eventname",(...arg)=>{})

移除事件监听

在unmounted（）{

​	eventBus.off("eventname",funcname)

}

