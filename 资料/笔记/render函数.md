render函数

可以返回的react元素,

可以返回数组或者fragment：可以使render方法返回多个元素

Portals：可以渲染子节点到不同的DOM子树中

返回字符串或者数值类型

返回的布尔类型和null：什么都不渲染



函数式组件

返回值类型和render函数一致

没有生命周期,也会被挂载

this关键字不能指向组件实例



react的前端工程化

安装 npm i create-react-app -g 脚手架

create-react-app  name(不能有大写字母)



pwa 渐进式web应用,一般针对手机端

logo图片可以添加成桌面图标,做离线缓存

robots.txt用于告知是否可以爬虫



Mounting阶段

初始加载 constructor，可以设置this.state={设置变量}

调用render函数

更新dom和refs

调用componentDidMount

依赖dom操作,发送网络请求,添加一些订阅componentDidUpdate 

Updating阶段

render（通过this.setState({修改变量的值})）

更新dom和refs

调用componentDidUpdate

更新完成调用 componentDidMount

卸载

componentWillUnmount

销毁组件，清除timer

取消一些订阅 componentWillUnmount



不常用的

shouldComponentUpdate(){

​	return false   (不重新执行render函数)

}



组件传值

父组件

 属性名={值}

也可以解构{...object}

子组件

可以省略直接获取值

constructor（props）{

​	super（props）

}

render（）{

​	const {值} = this.props

}

引入propTypes进行类型检查，相当于一个声明库

页面名称.propTypes={

​	定义参数类型：propTypes.array,

}

页面名称.defalultProps={

​	定义参数：[],(填写默认值)

}

子传父,父组件传入一个回调函数,子组件把值放入到回调函数里面



实现slot功能

组件的children子元素

在父组件传入多个react元素,在子组件中通过this.props.children:array来获取相应的react元素,传入一个就是当前元素本身

props属性传递react元素



组件之间共享数据 context

首先定义一个公共的context = React。createContext（{key:value}）,设置默认数据

然后包裹住要传递数据的组件 <\namecontext.Provider value={{key:value}}>\<子组件名称>,

需要用数据的组件,先导入定义的context,

文件name.contextType =  公共的context;

然后this.context.key即可获取值

如果是函数式组件则通过\<nameContext.Consumer>{value=>{return\<标签名>{value.key}\<标签名/>}}</nameContext.Consumer>

如果有多个context数据，父组件通过多层嵌套传数据，子组件则可以通过consumer属性获取



如果没有传递参数还要使用，则会获取默认数据



通过事件总线来实现不同组件之间的事件监听，需要安装事件总线库

添加事件之后记得移除掉