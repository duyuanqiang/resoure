<H3>webpack</h3>
开发代码到打包后运行的代码是需要转化的工具,

基于node对文件进行操作

vuecli和reactcli 都是基于webpack的

<H4>
	内置模块path
</h4>

node的额路径"\\",现在也支持"/",命令行操作文件

dirname():获取文件的父文件夹

basename:()获取文件名

extname():获取文件扩展名

join(url1,url2)路径拼接

resolve(url1,url2,url3) 返回一个绝对路径,从左到右拼接,只要组成绝对路径,就返回绝对路径,如果最后没有形成,会拼接返回当前文件夹的绝对路径,并会删除尾部多于的"/"

webpack是静态的模块打包文件

安装webpack webpack-cli

全局安装he局部安装

npm install webpack webpack-cli -D

npx webpack  打包

npx webpack --entry 入口名字 --output-filename 出口名字 --output-path ./path（指定输出路径）

创建webpack的配置文件

webpack.config.js  因为webpack运行在node所以要遵守commonjs规范

![1663141536778](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1663141536778.png)

output:{

​	clean:true,(打包会自动清空上一次文件)

}

npx webpack --config name.config.js webpack的配置名字发生改变

设置脚本script

<H4>loader

css的loader处理.css文件，只进行解析，不会进行插入页面，

需要style-loader

安装cssloader npm i css-loader -D

需要在webpack.config.js 配置

![1663144448126](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1663144448126.png![1663144483029](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1663144483029.png)有条件的简写

module:{

​	rules:[

​		{

​			test:/.\css$/,

​			use:[ //顺序从后往前加载

​				{loader:style-loader},

​				{loader:css-loader},

​				{

​					loader:"postcss-loader",

​					options:{

​						postcssOptions:{

​								plugins:[

​									"autoprefixer"

​								]

​						}

​					}

​				}

​				

​			]

​		},

​		{

​			test:/\.less$/,

​			use:[ //顺序从后往前加载

​				{loader:style-loader},

​				{loader:css-loader},

​				{loader:less-loader}

​				"postcss-loader"

​			]

​		},

​		{

​			test：/\.(png|jpe?g|svg|gif)$/,

​			type:"asset/resource/inline(对图片进行base64编码,行内转码,会造成js文件特别长)",

​			parse:{

​				dataURLCondition:{

​					maxSize:60*100(图片的临界值,保留大值)

​				}

​			},

​			generator:{

​				filename:"[name]_\[hash:8][ext]",图片重命名

​				hash:webpack生成

​			}

​		},

​		{

​			test:/\.m?js$/,

​			use:[

​				{

​					loader:"babel-loader",

​					options:{

​						presets:[

​							["@babel/preset-env"]

​						]

​					}

​				}

​			]

​		},

​		{

​			test:/\.vue$/,

​			use:["vue-loader"]

​		}

​	]	

}

想用postCss ,添加浏览器前缀,还需要安装插件autoprefixer -D

在postcss.config.js

module.exports={

​		plugins:[

​				"autoprefixer"

​		]

}

postcss-preset-env  内置了autofixer，功能更强。自动添加前缀，转换其他一些新特性，例如转换rem

npm install postcss-preset-env -D

Babel和babel-loader

小一点的用base64,大得的单独打包,形成新的二维码

配置文件来区分那个文件需要

<H4>babel

安装

npm install @babel/cli @babel/core -D

babel转换需要配合相应的plugins使用

使用预设babel不需要在安装其他插件,内置有相应插件

npm install @babel/preset-env -D

在babel.config.js中配置

module.exports={

​	presets:[

​			["@babel/preset-env"]

​	]

}

<h4>vue-loader

局部安装

另外需要引入

const {VueLoaderPlugin} = require("vue-loader/dist/index")

module.exports={

​	plugins:[

​		new VueLoaderPlugin()

​	]

}



<h4>webpack的路径解析

因为有些文件名并不在解析的数组里，需要自己加上

路径别名

module.exports={

​	resolve:[

​		extensions：[".js",".ts",".jsx",".tsx"],

​		alias:{

​			utils: path.resolve(__dirname,"./src/utils")

​		}

​	]

}

![1663216225107](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1663216225107.png)

<h4>webpack常见的插件和模式

loader是用于特定的模块类型进行转换

Plugin可以用于执行更加广泛的任务，打包优化，资源管理，环境变量注入等

<H5>clean-webpack-plugin -D

const {CleanWebpackPlugin} = require("clean-webpack-plugin")

module.exports={

​	plugins:[

​		new CleamWebpackPlugin()

​	]

}

<h5>html-webpack-plugin

​    指定入口模板


const HtmlWebpackPlugin = require("html-webpack-plugin")

module.exports={

​	plugins:[

​		new HtmlWebpackPlugin({

​			title:"电商项目"，

​			template：“./index.js”

​		})

​	]

}

配置前端模板需要ejs语法

<H5>DefinePlugin

 定义一些全局变量

const DefinePlugin = require("webpack")

module.exports={

​	plugins:[

​		new DefinePlugin ({

​			BASE_URL:"''./" ("" 双引号下是js代码 ，再加单引号是字符串)

​		})

​	]

}

<h5>Mode

DefinePlugin中的process.env.NODE_ENV的值有development,production,none

根据module.exports={

​	mode:development

} 来确定值

<h5>webpack开发本地服务

为了能及时更新

webpack-dev-serve 

局部安装 -D

"script":{

​	"serve":"webpack serve --config webpack.config.js" 编译不输出任何文件，而是将文件保存在内存中

}

<h5>热更新(hot module replacement HMR)

只更新一部分

if(module.hot){

​	module.hot.accept("./文件名",()=>{})

}

<h5>host配置

module.exports={

​	devServer:{

​		hot:true,

​		host:0.0.0.0,

​		port:8888，

​		compress：true,(压缩)

​	}	

}

localhost:本质是域名127.0.0.1，回环地址，会被自己收到

0.0.0.0 监听当前网段所有的ipv4地址

<H5>如何区分开发环境

可以写两个配置文件,一个开发环境,一个生产环境

将公共的配置抽出来

webpack-merge -D 合并配置插件

const {merge} = require("webpack-merge"),

const commonconfig = require("./webpack.common.config")

moudle.exports=merge(commonconfig ,{新配置})

context是上下文,相当于一个标志