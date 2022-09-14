React

引入 babel  React-dom React.js

\<script type= text/babel>



class app extend React.Component{

constructor(){

​	super()

​	this.state = {

​	}

}

render(){

​	return

}

​	

​	ReactDOM.createRoot(DomId)

}

react的列表渲染,直接用高阶函数map渲染

事件绑定 onClick={this.函数名}

需要注意this

root.render(\<App/>) 将组件添加到dom节点上



jsx all in js

jsx 必须有且仅有一个根元素

retrun(\<div>)

单标签必须以</>结尾

jsx中注释{/**/}

jsx中嵌入内容

number array  string 直接显示

null undefined boolean 显示为空,要想显示必须转换成字符串类型

object 不能插入jsx中,需要将对象的内容分开展示

babel会转化成严格模式

绑定属性

基本属性绑定 title={变量}

src href



class用className替代

className={${变量}}动态绑定属性

或者第三方库classname

this.setState({})修改变量

style={{color:"red",fontSize:14}};传入一个对象



jsx绑定函数

1,绑定是用bind(this) (显示绑定)

2.class filed 将调用函数改为箭头函数

定义一个类字段,定义一个全局变量,赋值函数,(隐式绑定)

3.直接传入箭头函数,进行调用(隐式绑定)

总之函数绑定要传入正确的this,或者显示绑定或者隐式绑定

bing传递参数,event参数在最后



React的条件渲染

jsx中可以直接在html中用js

可以将内容提出来,直接用一个变量替代,注意this的指向

条件渲染

1.通过条件判断,获取真正的html的返回值,主要通过render函数渲染

2.三元运算

3.&&逻辑与运算

列表渲染高阶函数

虚拟dom   ReactElement()

diff算法 更新变化的节点



