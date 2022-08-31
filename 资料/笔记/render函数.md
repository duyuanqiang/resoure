render函数

可以返回的react元素,可以返回组件,可以返回数组或者fragment

,返回字符串

函数式组件

没有生命周期,也会被挂载

this关键字不能指向组件实例



react的前端工程化

安装 npm i create-react-app -g 脚手架

create-react-app  name(不能有大写字母)

pwa 渐进式web应用,一般针对手机端

logo图片可以添加成桌面图标,做离线缓存

robots.txt用于告知是否可以爬虫



更新完成调用 componentDidMount

依赖dom操作,发送网络请求,添加一些订阅componentDidUpdate 

取消一些订阅 componentWillUnmount



不常用的

shouldComponentUpdate(){

​	return false   (不重新执行render函数)

}