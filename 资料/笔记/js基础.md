<h1>js基础</h1>

**作用域(Scope)**

表示一些标识符的作用范围是有效的

函数的作用域表示在函数内部定义的变量,只有在函数内部可以访问到

**全局变量和局部变量**

**作用域链**

**函数**

**函数是一种特殊的值,头等公民**

**函数的声明**

function foo(){}

**函数的表达式**

var foo= function(){}

![1667960230395](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667960230395.png)

函数是一等公民

可以被赋值给变量,让函数在变量之间传递,函数可以作为另一个函数的参数,函数作为返回值

柯里化函数就是传入多个参数,每一个函数执行一个参数,剩余参数在内部函数作为返回值,返回函数,下次继续执行.

作为参数一般用匿名函数,函数嵌套函数,就是高阶函数

**立即执行函数**

;(function (){})()

分号后面跟(),[],{}之类的可执行函数,必须加上分号.不能省略

立即执行函数也是有返回值的,在后面括号可以传递参数

![1667961666433](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667961666433.png)

立即执行函数也是有作用域的.

作用,防止命名冲突,污染全局

**可以封装成模块,将想要暴露的函数,返回出去.es5的封装模块**

形成作用域,保存i的值

![1667962470877](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667962470877.png)

**代码规范**

等号左右加空格, 函数的() {}之间加空格,左大括号和括号一行.

参数之间左面加空格

**debugger 调试**

先打印输出值,在chrom中看source,加断点.或者在代码中想断点的地方加debugger

watch监听查看变量执行过程

有跳过断点,下一步,下一个函数,立即跳出函数

-> 跳过异步函数,下箭头可以进入异步函数

**构造函数的new操作符**

new过程,构造函数名大驼峰

在内存中创建一个空对象

这个对象内部的[[protoperty]]属性会被赋值为该构造函数的prototype属性

构造函数内部的this,会指向创建出来的新对象

执行函数的内部代码

如果构造函数没有返回非空对象,则返回创建出来的新对象

**全局window对象**

查找变量会找到window,

提供一些全局的变量/函数/对象,在window上

定义对象和函数

![1667965067868](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667965067868.png)

window最上层的对象,Object继承window,function继承Object

**js内置类**

包装类

name = new String(name),生成的实例可以用String类的方法

Number,Boolean Symbol BigInt

![1667965859735](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667965859735.png)

**Number**

Number的方法tofixed(位数), toString(进制),parseInt(string,radix) 整数，parseFloat(string) 解析成浮点数

![1667966511095](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667966511095.png)



**Math**

![1667966841866](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667966841866.png)

String

数组和字符串可迭代

![1667976873467](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1667976873467.png)

Array

Date