**类**

new实例,



属性加上! 表示断言不需要初始化，非空类型断言后面加！

**继承**

**修饰符**

private,public,protected

默认public

abstract 抽象方法必须写在抽象类里面。子类必须实现抽象方法

抽象类无法实例化

父类引入指向子类对象，即为多态



**泛型**

传入参数类型的操作\<T>

**映射**

[property in keyof Type]?:Type[Property]

映射Type类型

\- 删除修饰符, ?代表可选,+添加 是默认属性

类型体操基于

映射类型,条件类型,(extends,infer,as)分发类型



**ts的模块化**

当作为类型导入的时候{type a} type关键字用来表示是类型

![1666769457943](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1666769457943.png)

**ts的命名空间**

相当于es6的模块化

![1666769808243](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1666769808243.png)

**ts的类型查询**

.d.ts

全局安装ts,内置基本的类型文件

ts的github有源码说明,

编写的库,在ts环境下会自动扫描到,做类型显示

官方的定义文件,可以安装定义包 

自己做声明文件.d.ts

declare module "name"





声明文件,

包本身包含axios

2 官方包含 安装npm i @types/react -D

3 自己没有声明,DefineTypes库也没有,手写自定义声明文件

![1666786977268](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1666786977268.png)

![1666786938587](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1666786938587.png)

第三方库,需要自己编写声明库文件

![1666787769066](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1666787769066.png)

declare 模块的声明

declare module name {

}

导入的使用decla module

cdn引入的需要用 declare namespace ${

}用命名空间的形式, $是命名空间的名字



tsconfig.json文件

ts会自动帮我们配置好项目,自动读取



配置文件解析

babel转换ts

![1666790991922](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1666790991922.png)

![1666791001466](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1666791001466.png)

**泛型编程**

泛型就是给类型传入参数，给类型传值的形式

**条件类型**

**符号 "|" 或者意思 ,有" in" 遍历联合类型 "keyof "将对象改成联合类型" -" 删除 "+"增加 "?" 可选**

extends 是否存在其中 

**运用三元运算符，来确定类型**

作用就是。**对泛型值进行限制**，**泛型对值进行限制**

![1666945546085](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1666945546085.png)

**infer类型推断**

**ReturnType**<表达式> 取到类型的返回值，此方法是内置的方法

对类型进行运算，进行操作，此时类型就相当于值，进行类型计算

将推断出来的结果，显示出来,通过推断继承的类型的同位置的类型值,得到自己该位置的类型值. **在泛型中<> 就相当于正常函数里面的(),里面包裹的就是参数,前面的就是函数名**

![1666946206056](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1666946206056.png)

推断返回值类型和推断参数类型

**分发条件类型**

![1666946538673](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1666946538673.png)

**Partial\<Type>将类型转变成可选类型**

![1666946786688](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1666946786688.png)

![1666946916180](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1666946916180.png)

![1666947037091](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1666947037091.png)

keyof是用来遍历对象的,所有key组合成联合类型

![1666947516783](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1666947516783.png)

**从Type挑出来keys里面的类型,keys为Type里面的key联合**

![1666948046898](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1666948046898.png)

**Omit过滤属性**

![1666948135823](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1666948135823.png)

P继承于K,则就将P赋值为never,从而达到删除的目的

![1666948974902](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1666948974902.png)

提取同名类型

![1666949284710](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1666949284710.png)

![1666949584671](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1666949584671.png)

![1666949654250](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1666949654250.png)

![1666949681582](C:\Users\dyqiang\AppData\Roaming\Typora\typora-user-images\1666949681582.png)