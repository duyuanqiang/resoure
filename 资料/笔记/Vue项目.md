**Vue+ts项目**

npm init vue@latest

安装 vue-tsc -D

强制清除本地缓存

npm cache clean --force

![1667197555939](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667197555939.png)

配置.editorcopnfig文件

vite区分环境

import.meta.env.DEV 是否开发环境

import.meta.env.PROD 是否生产环境

import.meta.env.SSR 是否服务端渲染

配置环境文件

.env  生产环境和开发环境都在用

.env.development   开发环境用

.env.production 生产环境用

.env.local 会被git忽略

.env.[mode].local 会被git 忽略 

![1667277089394](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667277089394.png)

全局注册

```
// main.ts
import ElementPlus from 'element-plus'
import 'element-plus/dist/index.css'
app.use(ElementPlus)
```

响应式数据，一般要解构传递出去

**登录流程**

**权限管理**

rbac基于角色的访问控制

![1668341490336](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1668341490336.png)

后端返回的数据，要么写成any，要么JSON转类型的工具



字符串转换成动态组件，动态显示图标



后端如果返回的数据比较复杂，比较乱就自己写函数处理成自己想要的数据格式 



根元素中修改子组件的样式，不需要加:deep().因为scoped生成的

data-v-xxx的值是一样的，子组件则是不同的.

scoped实际样式名字后缀添加xxx，比如 跟样式test[data-v-xxx]

如果组件不在app下，要想修改样式，需要:global(样式名) 包裹

动态路由

前端定义role的路由表

在组件传值的时候的变量名和事件名称需要写成横杠形式。

父子组件之间不能有同名的css名字，否则会相互影响



通过computed 和watch函数获取响应式数据



请求不到数据，要校验传入的参数，是否符合后端要求



项目报错需要刷新浏览器，避免vite 的热更新不及时，导致bug还在





defineProps不支持使用别的文件导入类型





{...}解构proxy对象

nexttick  再一次dom更新晚,再执行

vue的响应式改变不是同步的,而是vue将他们缓存在一个队列,直到下一个tick才一起执行,这样确保每个组件无论发生多少次,都仅执行一次更新

nexttick(),可以在状态改变后立即使用,以等待dom更新完成,可以传递一个参数,或者等待await返回的promise