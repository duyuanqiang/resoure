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

Babel和babel-loader

小一点的用base64,大得的单独打包,形成新的二维码

配置文件来区分那个文件需要