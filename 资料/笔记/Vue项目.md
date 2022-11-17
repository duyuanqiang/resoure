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