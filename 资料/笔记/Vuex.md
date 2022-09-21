<h3>Vuex

一个状态管理库

安装vuex  npm i vuex

<h4>state

const store = createStore({

​	state:() => ({

​		counter: 100

​	})

})

export default store;

html中使用$store.state.counter

computed中使用 this.$store.state.counter

在setup中使用 toRefs(store.state)获得响应式变量

修改需要提交mutation



导入{mapState} from "vuex"

computed:{

​	...mapState(["name","level"]) 映射一个一个的函数

对象写法

​	...mapState({

​		sName: state =>state.name

​	})

}

{{name}} 获得一个同名函数



在setup中使用

const sName = computed(name.bind({$store:store}))

直接响应式解构

const {name，level} =toRefs(store.state)

<h4>getter

getters:{

​	getFriendById(state,getters){

​		return (id) =>{

​			const friend = state.friends.find(item=>item.id === id)

​			return friend

​		}

​	}

}

调用 {{$store.getters.getFriendsById(111)}}

映射函数{mapGetters},用法类似{mapState}

computed:{

​	...gettters(["myname"]) 映射一个一个的函数

对象写法

​	...gettters({

​		fName: "myname"

​	})

}

在setup中使用

const {message:nessageFn} = mapGetters(["message"])

const message= computed(nessageFn.bind({$store:store}))

直接响应式解构

const {message} =toRefs(store.getters)

针对某一个属性

const message = computed(() =>store.getters.message)

<h4>mutations

mutations:{

​	increment(state,payload){

​		state.counter++

​		state.name = payload

​	}

}

使用

this.$store.commit("increment"," 王小波")

辅助函数

methods:{

​	...mapMutations(["increment"])

}

@click="increment("王小波)"

在setup中使用

![1663641455847](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1663641455847.png)

mutation不能执行异步操作，只能执行同步操作。为了devtools追踪数据

![1663641560857](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1663641560857.png)

<H4>Action

1.可以异步操作,请求数据.

2.action不允许直接拿state,必须提交mutation

重要参数 context

actions:{

​	incrementAction(context){ context包含commit,getters,state

​		context.commit("increment")

​	},

​	changeNameAction(context,payload){

​		context.commit("changeName",payload)		

​	}

}



调用

methods:{

​	actionBtnClick() {

​		this.$store.dispath("incrementAction")

​	}

​	changenameClick(){

​		this.$store.dispath("changeNameAction","wangxiaobo")

​	}

​	...mapActions(["incrementAction","changeNameAction"])

}

@click ="changeNameAction('wangxiaobo')"

<h5>在setup中的this.$store 拿不到,需要手动绑定

![1663644578572](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1663644578572.png)

在dispath之后如果函数返回的promise,就可以通过.then((res)=>{res}) 获取回调通知

![1663646264545](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1663646264545.png)

<H4>module的基本使用

将某一个页面的数据抽到一个单独的对象里面,格式和vuex一致.

然后导入到vuex import {homeModules} from " "

**modules**:{

​	home:homeModules

}

在html中使用 {{$store**.home**.key}},也就是state中的值,原理应该是对象中包含对象

别的使用方法不变,原理应该是模块的getters,mutation,Action进行了合并

<H5>namespace

在子模块设置namespace:true

使用需要加上子模块名字 "子模块名/方法名"

![1663648397969](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1663648397969.png)

![1663648419997](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1663648419997.png)

使用根组件的方法

![1663648520027](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1663648520027.png)

设置root属性