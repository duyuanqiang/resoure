TS

安装 npm i typescript -g

ts代码需要编译才可以运行

tsc 文件名

在webpack配置编译

安装ts-node插件

npm i tslib @types、node -g

![1665425668791](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1665425668791.png)

**ts在编译过程就会报错**

变量声明需要类型注解，

后面还会学到函数签名

**类型推断**

字面量类型

let推导的通用类型，const推导出来字面量类型





有那些类型

number Boolean string Array Array<number>泛型 type类型

object是空对象类型{}

null和undefined类型

函数的参数和返回值设置类型





![1665426368349](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1665426368349.png)

**类型别名**

type name={}

![1665637879763](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1665637879763.png)

**interface**接口的声明

interface name{}



两者区别

type可以声明联合类型，不允许同名别名存在



interface 

命名一般加I，一般用来声明对象类型

同名声明是合并属性，支持继承，可以实现

![1665638541515](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1665638541515.png)

**交叉类型**，多种类型都要满足，一般在对象中使用 类型用“&”链接

![1665638775736](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1665638775736.png)

**as**

有时候无法获取具体的类型信息，可以用类型断言。**as 类型** 

获得确认类型

**非空类型断言 "!"**

断言的语法，默认开发者比ts语言更确认类型

![1665639561514](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1665639561514.png)

**字面量类型**

method：“post”|“get” 规定了method的值

直接定义属性为确定的值，可以直接在对象后面加上 “as const”，

那么用此类型的值是确定的。

**类型缩小**

![1665640598508](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1665640598508.png)

![1665640710570](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1665640710570.png)

![1665640949883](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1665640949883.png)

**instanceof 判断参数是否是类的实例**

![1665641093391](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1665641093391.png)

**in运算符判断某一个对象是否有某一个属性**

![1665641303972](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1665641303972.png)

**函数的类型**

函数类型表达式，

(参数类型)=>返回值类型

![1665646936794](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1665646936794.png)

函数类型参数个数的问题。

TS不对传入参数个数进行检测,因为有些匿名函数参数是不确定的.

TS的检测是根据规则来推断！

**函数类型表达式**

type barType = （num1：number）=>number

**函数的调用签名**（call signatures）

interface Ibar{

​	name:string,

​	age:number,

​	(num1:number):number

}

开发中如何选择

1.如果只是描述函数类型本身（函数可以被调用），使用函数类型表达式（Function Type Expressions）

2.如果在描述函数作为对象可以被调用，同时也有其他属性时，使用函数调用签名

![1665650968711](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1665650968711.png)

传入的多余的参数会被忽略

**构造签名**

先写类，再写接口类型

![1665652830333](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1665652830333.png)

**可选参数**

**可选类型**是写的类型|undefined   联合类型

**默认参数**

有默认参数可以省略类型注解。可以接受undefined

![1665653561163](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1665653561163.png)

**剩余参数**

![1665653603750](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1665653603750.png)

**函数的重载**

先编写重载签名

再编写函数的实现

![1665654163158](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1665654163158.png)

**能用联合类型实现的，不用重载类型**

在TS中使用this，默认any类型。

明确指出this的类型

tsc --init  生成配置文件。查找this，修改“noImpLicitThis”：true，需要明确指出this的类型，会通过上下文推导this的类型，如果无法推导出来this类型就会报错，需要明确指出this类型。this必须在第一个参数位置,并且为this

![1665657791552](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1665657791552.png)

this的内置工具使用.

typeof 可以获取函数类型

获取函数类型中this的类型

type FooType =typeof foo

type FooThisType = ThisParameterType<FooType>

![1665658732284](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1665658732284.png)

![1665658806083](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1665658806083.png)

3 通过ThisType<IState>绑定this,指定this的类型

![1665658670591](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1665658670591.png)

