<h3>Airbnb项目规范

命名规范

文件夹,文件名统一小写,多个单词以连字符连接

js变量小驼峰,常量大写,组件大驼峰

css采用普通css和styled-component(全局普通,局部styled-component)

采用hooks编写

使用memo包裹

组件内部,使用useState,useReducer;业务数据放redux

组件内部编写顺序

组件内部state管理

redux的hooks

其他hooks

其他逻辑代码

返回jsx代码

![1664677154380](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1664677154380.png)

redux采用两种方式

分独立模块,最后合并

redux会存在共享状态,以及从服务器获取状态

用axios进行二次封装,所有请求文件放在一个文件夹

采用AntDesign 和MUI

多部分需要自己封装



**项目**

配置标题,删除无用文件

配置jsconfig 路径提示会变的更好

安装craco,解决路径别名   @craco/craco@alpha -D

创建craco.config.js文件   添加配置,修改脚本命令,改为craco

修改webpack的方式

一 npm run eject弹出webpack配置文件修改,过程不可逆

二 配置craco. 最新的react-script需要安装alpha版本 @craco/craco@alpha

解决配置版本的问题,github上issue上看,Stack Overflow查





样式重置

安装  normalize.css;

自己设置reset.css



路由

安装 react-router-dom, 配置相应文件,懒加载,app处加载.应用



redux

安装 redux/toolkit react-redux





jsx中的style={{}}必须用{{}}包裹,对象类型必须用驼峰写属性



**添加组件库**

引入出错

一可能是引入出错，修改或者添加配置

二版本不匹配的问题。

MUI

Ant Design  集成less需要配置

index里面写导入的配置

文档是说明书，组件是产品