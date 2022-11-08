Vue的基础

CDN引入

![1667525005621](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667525005621.png)

本地提示

![1667525295603](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667525295603.png)



@click=functionName

data：function（）{return object}

method:{functionname(){}}

小技巧,没有template ,会渲染app内容

框架是声明式编程,原生是命令式编程

![1667526501348](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667526501348.png)

**MVVM**

ViewModel主要是连接视图层和model层的,通过数据绑定,和监听函数的形式

![1667527311161](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667527311161.png)

vue的响应式原理

v2 definedpropty

v3 proxy

data在v3必须为函数,v2为对象会出现作用域的问题,别的页面也会共用data,需要data函数设置作用域



this指向取决于函数被调用的方式

模板语法

{{}}

指令 用在元素属性上

v-once 只渲染一次,包括子元素,值发生变化,view层不会变化

v-text v-text="message"绑定的值的相当于{{message}}设置的值

v-html ="content" content包含html元素, v-html就是富文本解析

v-pre 跳过{{}}解析,原始的显示出来

v-clock 结合css使用, vue底层会处理,先不显示,渲染结束再显示

![1667530052895](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667530052895.png)

v-memo="[]",只有在数组里的变量发生变化才会渲染

v-bind 插入属性，动态绑定  :

:class 动态绑定class,用在active中.对象语法,布尔类型

:class="{active? 'active':''}" 内部只能使用单引号 

![1667532674774](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667532674774.png)

当有多个类型名字的时候,可以用数组绑定形式

![1667532872907](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667532872907.png)

:style的绑定,需要对象类型,必须用引号包裹键值,或者键用驼峰形式

![1667533194862](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667533194862.png)

![1667533212295](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667533212295.png)

绑定属性名

![1667533371898](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667533371898.png)

绑定对象

v-bind="{name:'zhangsan'}"绑定对象

事件绑定

v-on @click @mousemove

绑定的函数会有一个默认event参数，

明确参数 $event用来传递事件参数.

![1667543481116](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667543481116.png)

修饰符

v.on.stop

![1667543717811](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667543717811.png)

![1667543694975](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667543694975.png)

**条件渲染**

v-for="key in value"

v-if v-else v-else-if  v-show

templete元素 只是占位不会渲染,类似小程序的block



v-show 不支持template元素.

不能和v-else使用.

v-show本质在修改display:none,高频操作

v-if是把元素销毁,低频操作



v-for ="(item,key,index)  in values" 

写在谁身上,谁就会出现多个.

可遍历可迭代对象 ，数组，数字，字符串，遍历对象也可以

无意义就用template元素

key的作用

**vNode**

![1667547217117](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667547217117.png)

虚拟dom，渲染到浏览器上是真实dom，渲染到移动端，桌面端，映射成符合不同平台的dom ，实现跨平台

不添加key，插入东西就是从插入位置，往后都需要更新。

patchUnkeyedChildren

加上key，key和value一一对应 

调用pathKeyedChildren

**conputed**

**包含任何响应式数据的复杂逻辑，应该使用计算属性**

优势，

写法简洁

和methods比的区别

都可以进行响应式

computed会基于依赖关系对数据进行缓存，如果数据不发生变化，则就不更新

完整的computed的写法

![1667550045202](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667550045202.png)

**watch**

监听数据变化，执行一些逻辑代码

watch：{

​	name（newvalue，oldvalue）{

​		log（name发生了变化）

​	}

}

如果name是对象，则返回的是代理对象，通过解构，获得新对象{...object},也可以通过Vue.toRaw(newValue)来实现

想要深度监听

info:{

​	handler(newValue,oldValue){

​		此时 newValue ===oldValue

​	},

​	deep:true,

​	immediate:true (第一次渲染进行侦听)

},

"info.name":function(newValue,oldValue) {

​	侦听某个属性

}

在created里面监听

created(){

​	this.$watch('message',(newvalue,oldValue)=>{

​		console.log(newValue,oldValue)

​	},{deep:true,imediate:true})

}

**v-model**

双向绑定原理

:value ="message" @input="inputChange"

data(){

​	return {

​		message:""

​	}

},

methods:{

​	inputChange(event){

​		this.message = event.target.value		

​	}	

}

![1667612115108](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667612115108.png)

多选的绑定

每个input要添加value值

![1667612691921](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667612691921.png)

绑定到单选框

同一个值会互斥，只会得到一个值

![1667612960309](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667612960309.png)

绑定到多选框select

![1667613250934](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667613250934.png)

v-model的修饰符

lazy 将绑定事件从input改为change事件，只有在提交的时候才触发

![1667621989578](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667621989578.png)

number 转换成number类型，默认string类型

![1667622232743](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667622232743.png)

trim 去除输入内容的两边空格

通过链式调用可以添加多个修饰符

