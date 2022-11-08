**Vue生命周期**

init-beforeCreate-created-beforeMount-mounted-beforeUpdate-updated-beforeUnmount-unmounted

![1667731464420](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667731464420.png)

**$refs的使用**

拿到原生Dom绑定ref属性

在元素上绑定ref="name",在js中获取实例this.$refs.name

组件每调用一次就是生成一个组件实例，获取到的实例，包含属性和方法

![1667733171709](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667733171709.png)

![1667733256250](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667733256250.png)

**动态组件**

方法一，同过if判断来完成

方法二 is匹配到不同的组件名,显示相应的组件,组件必须是注册的.全局或者局部

\<component :is="动态修改组件名称">\</component>

![1667742336042](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667742336042.png)

**动态组件传值,**将参数放在组件上

![1667742574181](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667742574181.png)

**keep-alive**

内置组件,类似component

指定缓存组件名字,name名字必须是创建组件时候的名字

\<keep-alive include="name1,name2">需要缓存的组件名\<keep-alive>

![1667743023391](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667743023391.png)

**keep-alive 的生命周期**

在子组件中添加生命周期

activated(){组件进入活跃状态}

deactivated(){组件进入不活跃状态}

![1667743234622](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667743234622.png)

**webpack代码分包**

import(分包文件路径).then(res=>{

​	res调用分包文件的方法

})

import {defineAsyncComponent} from "vue"

const componentname = defineAsyncComponent(()=>import(组件路径))

经过异步函数处理即可打包生成分包文件

![1667743969969](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667743969969.png)

![1667744076898](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667744076898.png)

![1667744104801](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667744104801.png)

**组件的v-model**

子组件上使用 v-model="value"

相当于做了给子组件传值:modelValue和绑定@update:modelValue="

appCounter=$event"

![1667745212497](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667745212497.png)

![1667745284875](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667745284875.png)

自定义事件名  v-model:name,在子组件事件名update:name.可以设置多个值

![1667745681069](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667745681069.png)

**mixin**

需要单独文件中定义公共部分,在需要混入的文件中通过mixins:[引入mixin的name] 引入公共部分.data中不同的值会合并,相同值会保留本身值

钩子函数都会被调用,其他的对象属性methods都会生效,如果key相同会取组件中的对象的键值对

在全局混入app.mixin({})  

局部 mixins:[name]

![1667781312016](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667781312016.png)

