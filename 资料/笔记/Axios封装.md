**Axios封装**

分层结构

server {modules（分模块请求数据），config（配置基础数据），request（真正的请求），index（导出接口）}

**添加拦截器**

**所有实例进行拦截**

this.instance.interceptors.request.use(config=>{},err=>{})

this.instance.interceptors.response.use(config=>{},err=>{})

**单个实例进行拦截**

根据不同的request实例，自定义拦截器，将拦截器作为参数传入

需要对原先的接口进行扩展，就需要继承原先的类型，然后在自己的类型写扩展

在拦截器函数传入自定义的函数

**单次请求的拦截器**

