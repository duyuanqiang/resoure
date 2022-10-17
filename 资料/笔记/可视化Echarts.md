**可视化Echarts**

![1665986282525](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1665986282525.png)

显示地图

拿到GeoJSON数据

注册对应的地图数据

配置Geo选项



练习中国地图

首先导入webpack打包过的地图js文件。

然后使用map series的方式进行绘制地图

因为内部map series 会自己生成内部专用的geo地理坐标组件

主要用于地理区域数据的可视化

serise：[

​	{

​		type: "map",

​		map:"中国"	，

​		roam：true

​	}

]

另外一种geo地理坐标系组件

geo：{

​	map：“中国”

}

支持在地里坐标系上绘制散点图，线集

该坐标系可以和其他系列复用

注意：其他系列复用该地里坐标时，series的itemStyle样式将不起作用

用在创建全局的地理坐标系

着色属性

let option={

​	tooltip：{}，

​	serise：[

​	type:"map"

​	map:"中国"

​	data：[

​		{name：“广东”，value：123}

​	]

​	roam:"true" 可拖拽

​	itemStyle:{区域颜色，边界颜色

​		areaColor:"",

​		BorderColor:"",

​	},

​	emphasis:{高亮颜色

​		itemStyle:{

​			areaColor

​		},

​		label:{

​			color:

​		}

​	}

]

}

visualmap视觉映射

在地图坐标绘制散点图

let myChart = echarts.init(document.getElementById("main")) 传入节点

let option ={

series：[

​	name：”散点图“

​	type：“effectScatter”

​	geoIndex：0，

​	coordinateSystem：“geo”

​	data：[

​		{

​			name:"广东"

​			value：[113,39,199] 坐标 经纬度,还有散点图大小

​		}

​	],

​	symbolSize:function(val){

​		return val[2]/10     散点图大小

​	},

​	itemStyle:{ 散点图的配置

​		color:"green",

​		shadowBlur:10,

​		shadowColor:"yelow"

​	}

]

}

myChart.setOption(option) 传入配置

![1665977065003](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1665977065003.png)

响应式图表

window.addEventlistener("resize",()=>{

​	mychart.resize()

})

自动轮播提示框

![1665986116798](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1665986116798.png)

**地图的点击事件**

mychart.on("click",e=>{

​	myChart.registermap(event.name,{geoJSON:guangdong_geojson})

option.series[0].map= event.name

myChart.setOption(option)

})

![1665986626675](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1665986626675.png)

