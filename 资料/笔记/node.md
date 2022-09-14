<h3>node

node的模块化

commonJs和ES Module

<h3>npm包管理工具

共享代码  官网 github  registry

安装需要提前在官网查询是否已经发布至registry

或者在npm官网查看

package.json的配置相对固定



npm install -y 所有的都是yes

packjson字段的含义

name version

private：true 防止误发布

main：“入口文件”，指定入口文件

“script“：{

​	start：“”，执行项目的脚本命令 （npm run start，start，test，stop，restart可以省略run）

}

dependencies 生产环境需要

devDependencies 开发环境 --save-dev  缩写 -D

peerDependencies 依赖别的库



<H3>依赖的版本管理

x.y.z 版本号

x主版本  可能不兼容之前版本

y次版本  新增功能,兼容之前版本

z修订号  修复之前版本的bug

^表示永远安装 y和z的最新版本,

~表示安装z的最新版本

engines 用于指定Node和NPM的版本号

也可以指定操作系统"os":["linux",]

browserlist 属性浏览器兼容

webpack -g 全局安装

yarn,webpack工具包需要安装到全局

axios等库文件需要局部安装

registry有缓存,标识符保存在 package-lock.json中

resolved:"仓库地址"

integrity:"缓存标识"



npm 的原理

![1663042741582](D:\Project\resoure\资料\笔记\images\1663042741582.png)

卸载包   uninstall

强制重新build   npm rebuild

清除缓存 npm cache clean

<H4>yarn</h4>
yarn init -y

yarn add 包名

yarn remove 包名

![1663047985087](D:\Project\resoure\资料\笔记\images\1663047985087.png)

<h4>cnpm</h4>
淘宝镜像

修改registry库地址

cnpm config set registry=https://registry.npm.taobao.org

<h4>
    npx
</h4>

为了调用不同的模块命令

webpack只在开发阶段使用

全局局部都安装webpack，用的是全局

优先使用局部的方式 1 ./node_modules/.bin/webpack --version

2 修改package中 "script".{"webpack":"webpack --version"}

3使用npx webpack --version 

npx优先在node_modules下的.bin文件下查找

打包输出在dist文件



发布npm包

npm install -y

![1663053632165](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1663053632165.png)

注册账号

https://www.npmjs.com

npm login 登录

npm publish 发布

npm unpublish 删除

npm deprecate 让包过期



用排除法,对比排出错误的情况.辩证逻辑

<h4>pnpm

performant npm 缩写

硬链接：

打开文件名就是硬链接，文件名链接存储单元

软连接：保存某个文件的绝对路径，例如快捷方式



文件的copy是占用新的磁盘，硬链接，是文件名指向同一个磁盘地址。软连接，快捷方式。存有绝对路径，指向文件名



命令行

copy

copy A B

hard link

mklink:  /H A B

mac: ln A B

软连接

mklink



pnpm就是为了减少重复的依赖包占用磁盘，非扁平化node_modules，所有的包都是一级目录，二级三级目录都是软连接

pnpm add name 不跟包 pnpm install 卸载 pnpm remove

安装在pnpm里面，硬链接到.pnpm store 文件名

store

pnpm store path 查看pnpm存储地址

会造成pnpm 的文件夹越来越大

pnpm store prune  释放从未引用的的包

