<H3>pinia</h3>

pinia和vuex的区别

mutations不再存在,解决冗余,精简了api

更好的支持TypeScript

不再有modules的嵌套结构,可以灵活使用每一个store,通过扁平化方式来相互使用

也不再有命名空间的概念,不需要记住它们复杂关系

安装 npm install pinia

创建pinia

import {createPinia} from "pinia"

const pinia = createPinia();

export default pinia





在main里导入,并且挂载

import {createApp} from "vue"

import App from "./App.vue"

import pinia from "./stores"

createApp(App).use(pinia).mount('#app')



定义store

import {defineStore} from  "pinia"

export default const useCounter = defineStore("counter",{

​	state:()=>({

​		count:99

​	})

})

使用pinia

import  useCounter from '@/stores/counter'

const counterStore = useCounter()



html中

{{counterStore.count}}



解构出来的值会失去响应式

storeToRefs(counterStore) 解构出来的变量具有响应式

<h4>store的其他方法</h4>

const {name,age,level} = storeToRefs(userStore)

修改方式可以直接通过赋值的方式  userStore.name = "kobe";

userStore.$reset() 恢复到初始状态

userStore.$patch({counter:100,name:"kobe"})一次修改多个值的状态

替换state成为新的对象  const oldState= userStore.$store;

userStore.$state = {

​	name:"curry",

​	level:200

}

oldState === userStore.$state 结果为true，应该还是同一个对象。

<H4>getters

getters：{ 相当于原先的computed函数

​	doubleCount(state){

​		return state.count*2;

​	}

​	doubleCountAddOne(){

​		return this.doubleCount +1;

​	}

​	getById(state){

​		return function(id) {

​		}

​	}

​	showMessage(state){

​		return `name:${userStore.name}`

​	}

}

js中

import useCounter from "@/stores/counter";

const counterStore = useCounter()

html中

{{counterStore.DoubleCount}}

{{counterStore.getById(111)}}

{{counter.showMessage}}

当前store访问其他getters，用this

<h4>Action

actions:{

​	increment(state) {

​		state用来传递参数

​		store通过this访问

​		this.counter++

​	}

​	async fetchHomedata(){

​		const res = await fetch("http://");

​		const data = await res.json()

​		this.banners = data.data.banner.list (修改state中的banner数据)

​	}

}

js中使用

counterStore.increment(10)

counterStore.fetchHomedata().then(res=>{

​	console.log("fetchHomedata的action完成了")

})