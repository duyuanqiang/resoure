<h3>Vue路由

![1663509508439](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1663509508439.png)

1.创建路由对象

*routes:映射关系

*history:修改url的模式(hash/history)

2.让路由对象生效

*app.use(router)

3.router-view的占位

4.router-link进行路由的切换



redirect:"",重定向.可以设置默认路由

router-link的几个属性

to="",跳转路径;

replace替换路径,不会存放历史路径中

.router-link-active{}; 设置激活的时的样式

可以自己定义属性名

active-class="自己想定义的属性名"

<H4>路由懒加载

const Home = ()=>import(/*webpackChunkName:'home'\*/"../View/Home.Vue");指定分包的名字,魔法注释;

![1663520290643](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1663520290643.png)

name属性和meta属性

meta可以附带其他属性

<H4>获取路径上的参数

 获取动态路由

html中获取{{$route.params.id}}

js中拿取 导入{useRoute} from 'vue-router'

useRoute().params.id

<H4>NotFound

![1663521552708](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1663521552708.png)

匹配不到相应的路径

<h4>路由嵌套

children：[

​	{

​		path:"",

​		component:import("")

​	}

]

router-link-exact-active 精准匹配，添加样式

<H4>代码跳转

import {useRouter} from "vue-router"

const router = useRouter()

router.push({path:"",query:{}});添加路由,传递参数

$route.query.name 获取参数

router.replace("")替换路由

router.back()返回上一页

router.forward();向前一步

router.go(num) num前进或者后退数

<H4>动态管理路由的其他方法

删除路由的方法

添加一个同名的路由

1.通过removeRoute，传入路由的名字

2.通过addRoute方法的返回值回调

3.const removeRoute = router.addRoute(routeRecord);

removeRoute();//删除存在的路由

router.hasRoute():检查路由是否存在

route.getRoutes():获取一个包含所有路由记录的数组

<H4>路由导航守卫

判断是否登录 token是否存在，通过localStorage获取Token

router.beforeEach((to,from)=>{  任何页面跳转,都会调用

​	if(!token) return "./login"

})

<H4>完整的导航解析流程

导航被触发

在失活里调用 beforeRouteLeave 守卫.(刚离开的界面调用)

调用全局的beforeEach

在重用组件调用beforeRouteUpdate守卫.  (同一个界面跳转)

![1663556806555](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1663556806555.png)