<h3>axios

npm i axios

import {createApp} from "vue"

import App from from "./App.vue"

createApp(App).mount("#app")

axios.request({

​	url:"",

​	method:"get"

}).then(res=>{

​	console.log("res",res.data)

})



axios.get("url?id=111").then(res=>{})

axios.get("url",{

​	params:{

​		id:111

​	}

}).then(res=>{})

axios.post("url",{

​	name:dyq,

password:"123456"

}).then(res=>{

​	res.data

})

<H4>配置参数

请求地址

url：'/user'

请求类型

method:"get"

自定义请求头

headers：{x-Requested-Width':'XMLHttpRequest}

url查询对象

params：{id:12}

请求体

data：{key：’aa‘}

timeout：1000，

<h4>默认配置属性

axios.defaults.baseURL = baseURL

axios.defaults.timeout = 10000

axios.defaults.headers = {}

axios..all([

​	axios.get("/home/"),

​	axios.get("http://127.0.0.1")

]).then(res=>{

​	都有结果才会返回 返回的是数组

})

<H4>提供多个实例</h4>

const instance1  = axios.create({baseURL:url1})

const instance2  = axios.create({baseURL:url2})

instance1.get("/子url"，{

​	parmas：{

​		id：111

​	}

})

<H4>拦截器

请求前拦截

axios.interceptors.request.use((config)=>{

​	进行一些操作

​	添加header,

​	认证登录:token/cookie

​	请求参数进行某些转化

​	return config 请求成功返回参数

​	

},(err)=>{

​	return err 请求失败拦截

})

返回后拦截

axios.interceptors.response.use((res) = >{

​	return res.data 相应成功

},(err)=>{

​	return err 相应失败拦截

})

<H4>axios的二次封装

import axios from "axios"

class HYRequest{

​	constructor(baseURL,timeout=10000){

​		this.instance = axios.create({

​			baseURL,

​			timeout

​		})

​	}	

​	request(config) {

​		return new Promise((resolve,reject) => {

​			this.instance.request(config).then(res>{

​				resolve(res.data)

​			}).catch((err =>{

​				reject(err)

​			})

​		})

​	}

​	get(config){

​		return this.request({...config,method:"get"})

​	}

​	post(config) {

​		return this.request({...config,method:"post"})

​	}

}

export default new HYRequest()