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