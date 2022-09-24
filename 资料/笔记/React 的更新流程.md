<h3>React 的更新流程

react的算法优化

同层节点之间相互比较,不会跨节点比较.

不同类型的节点,产生不同的树结构

开发中,可以通过key来指定哪些节点在不同的渲染下保持问题

key需要保持唯一,不要使用随机数

使用index作为key ,对性能没有优化.因为下一次index可能都会改变

<h3>shouldComponentUpdate

shouldComponentUpdate(nextProps,newState) {

​	if(this.state.message !== newState.message) {

​		return true

​	}

​	retuen false

}

继承**PureComponent**组件会自动过滤未改变的组件

在函数式组件 导入memo，由memo包裹函数，然后导出返回的组件

![1664040143470](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1664040143470.png)

<h3>数据不可变的力量

不要把同一个对象,重新设置.因为在PureCopmponent不会更新,所有需要重新拷贝一下,再设置

const books = [...this.state.books]

<h3>获取dom ref

方式一:在点设置 <h2 ref="why">\</h2>

this.refs.why 即可获取当前节点dom

**推荐**方式二:\<h2 ref={this.titleRef}>\</h2>

在state中this.titleRef = createRef();

this.titleRef.current

方式三

\<h2 ref={el=>{this.titleEl = el)}}></h2>

在state中设置 this.titleEl = null;

this.titleEl

<h3>获取组件实例

\<HelloWorld ref={this.titleRef}>

在state中this.titleRef = createRef();(react解构出来的)

this.titleRef.current

函数式组件没有实例

解构出来{forwardRef}

forwardREf(function(props,ref){

​	return(

​		\<div>

​			\<h1 ref={ref}>Hello World\</h1>

​		\</div>

​	)	

})

获取this.titleRef.current

<h3>受控组件

表单元素value有绑定值,则就是受控组件

![1664045233384](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1664045233384.png)

设置onChange={e=>this.inputChange(@)}

inputChange(e) {

​	this.setState({username:event.target.value})	

}

需要绕一圈重新设置，需要调用onChange事件