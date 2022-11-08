**CompositionAPI**

setup的两个参数props,context

setup(props,context){}   context包含emit属性

setup的返回值可以在模板template中使用,可以通过setup中的返回值代替data选项

setup（）{

​	

return	{



​	}

}



**reactive**

定义复杂类型数据,传入基本类型会报警告

reactive({name:"",account:""})

![1667791226328](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667791226328.png)

**ref**定义简单数据类型数据

默认情况在template中使用ref时,vue会自动对其进行解包.

在setup中使用还是要用.value来获取

![1667791640682](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667791640682.png)

浅层解包

ref的值,作为对象属性的值,在template中的方法中使用需要obj.key.value 这样获到的值才是响应式

使用时候不需要.value获取.修改的时候需要写.value



reactive的应用场景

应用于本地数据

多个数据之间是有关系/联系(聚合的数据,组织在一起会有特定的作用)

其他场景使用 ref,例如简单数据,从网络中获取的数据,将服务器数据直接赋值给经过ref包装过的变量



**安装devtool插件,github下载文件打包生成的文件放在浏览器的扩展程序中或者直接在谷歌商店直接下载**



单项数据流,不允许子组件修改父组件的值.需要修改,通过事件让父组件修改,组件应该像纯函数一样,不能修改传入的props

**readonly**

被readonly包裹的函数没办法修改,但数据还是响应式的,遵循单向数据流

![1667805914574](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667805914574.png)

![1667805939665](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667805939665.png)

![1667806348935](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667806348935.png)

**isproxy**检查对象是否有reactive或readonly创建的proxy

**isReactive** 检查对象是否有有reactive创建,

该代理是readonly建的,但是包裹由reactive包裹创建的另一个代理.也会返回true

**isReadonly** 检查对象是否是由readonly创建的只读代理

**toRow**返回reactive或readonly代理的原始对象(不建议长久引用)

**shallowReactive**

创建一个响应式代理,它跟踪其自身property的响应性,但不执行嵌套对象的深层响应式转换(深层还是原生对象)

**shallowreadonly**(浅层响应式)

创建proxy, 使其自身的property为只读,但不执行嵌套对象的深度只读转换(深层还是可读,可写的)

**toRefs**

响应式被解构会失去响应式,通过toRefs包裹解构的对象不会失去响应式

![1667818695969](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667818695969.png)

**toRef**

如果我们只是转换一个reactive对象的属性为ref,那么可以使用toRef方法

![1667818821147](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667818821147.png)

unref相当于ref的值取value

![1667819101289](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667819101289.png)

为什么不能在setup中不能使用this,是因为内部函数没有绑定this

**computed**

只是获取值 const value =  computed(()=>value); 返回的value只是**ref**类型.

想要设置值 **value.value = newValue**

![1667824549431](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667824549431.png)

**ref**获取组件元素

在组件中 设置 ref="name",在js中 const name = ref(null) 

return {name}

![1667867289989](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667867289989.png)

**注册生命周期函数**

一开始就会执行setup函数,相当于setup函数

导入以onxxx的相应的周期函数名

![1667867611353](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667867611353.png)

**provide inject**

父组件provide提供响应式数据,其他组件 inject 接收数据

optionAPI获取的值需要解包,setup不需要解包

![1667868160954](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667868160954.png)

**watch**

watch(属性名,(newvalue,oldvalue)=>{

​	

}，{

​	immediate：true（初次侦听）

})

如果监听的是一个对象，那么实际上新值和旧值是同一个对象，只是不同的引用。如果想要监听非一个值，需要进行深拷贝。默认进行深度侦听

监听reactive数据变化后，获取普通对象

watch(()=>({...info}),(newValue,oldValue)=>{},{immediate:true,deep:true})

![1667869700455](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667869700455.png)

![1667869731086](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667869731086.png)

![1667869798004](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667869798004.png)

**watchEffect**(()=>{})

自动搜集依赖，有变化就会进行侦听

![1667870304489](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667870304489.png)

**stopWatch**()  停止监听

**hooks**封装

封装的功能函数,需要引用不同的功能函数,然后导出封装好的功能函数

![1667873389012](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667873389012.png)

useTitle

document.title 修改浏览器文件标题名字

![1667875557589](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667875557589.png)

![1667875804688](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667875804688.png)

**\<script setup>**

语法糖,直接在script中使用setup API

![1667876242662](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667876242662.png)

在顶层写的代码都会默认暴露给template模板,只在setup中第一层使用

![1667876600688](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667876600688.png)

定义props

const props = dafineProps({

​	name:{

​		type:"",

​		default:""

​	}

})

const emit = defineEmits(["changeAge"])

function changeAge() {

​	emit("changeAge",200)

}

![1667877129832](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667877129832.png)

**defineExpose**()

用来暴露组件中的property

![1667877508195](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667877508195.png)

