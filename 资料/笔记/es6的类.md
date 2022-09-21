<h3>es6的类

唯一区别就是没办法作为普通函数调用

<h4>访问器

class Person {

​	constructor(name,age){

​		this._name = name

​	}

​	set name(value) {

​		this._name = value;

​	}

​	get name() {

​		return this._name

​	}

}

var p1 = new Person("why",18)

p1.name = "kobe"

<h4>类的静态方法

static 方法名 类名直接调用

new this = new 类名

<h4>extends

**super(name,age);  调用父类的方法。只能在constructor中使用,一般放在首行**

子类重写父类方法

同名覆盖，就能调用自己的方法

实例方法，静态方法也可以调用 super.父类函数名

<h4>继承内置类

calss HYArray extends Array {

​	get lastItem(){

​		return this[this.length - 1]

​	}

}

var arr = new HYArray(10,20,30)

调用arr.lastItem

直接扩展,挂载到原型上

![1663762604847](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1663762604847.png)

<h4>类的混入mixin

![1663765219909](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1663765219909.png)

![1663765429319](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1663765429319.png)

![1663765485741](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1663765485741.png)

函数返回一个类,,下一个类再继承返回的类方法.

<h4>纯函数

立即执行函数,就是为了让方法是一个纯函数

相同的输入一定有相同的输出,没有副作用

babel转成es5,就是一层层封装



读源码