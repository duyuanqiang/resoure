<H3>
    Less Scss Sass
</h3>



less的的基本使用

1可以用webpack转化,

2可以用vscode插件easyless转化

3引cdn  \<script src="https://cdn.jsdelivr.net/npm/less@4" ></script>

4本地引入less转换源码



less.org在线转换网站

less兼容css

@mainColor:#000

定义变量 @变量名:变量值

嵌套语法,

与html标签嵌套结构一致

&表示当前选择器的父级

hover状态是在内部加

{

​	&:hover{}

}

less的运算

正常的加减乘除,颜色值也可以计算

mixins 混合

会将一组属性集,混入到另一个规则集的方法

调用的混入的类名 .classname();

也可以传入参数

在定义的类函数

.border(@borderwidth){

​	border:@borderwidth solid  red;

}

.b{

​	.border(5px)

}

映射和混入结合使用 函数名[属性名] 取得值

![1663318942627](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1663318942627.png)

![1663319079578](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1663319079578.png)

继承用法

![1663319320681](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1663319320681.png)

max min mod等等内置函数

![1663319401518](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1663319401518.png)

作用域

一个大括号是一个作用域,全局和局部作用域,取最近的值