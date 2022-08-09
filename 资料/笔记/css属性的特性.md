css属性的特性

属性的继承性

font  line-height color text-align 文本字体相关的

继承过来的值是计算值不是设置值

子元素强制继承   属性值为inherit,比如border:inherit

层叠样式表

同一个属性,权重最高的会生效,同权重的后设置的会生效

![1660030690352](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1660030690352.png)



!important  >内敛>id选择器>类,属性,伪类选择器> 元素选择器,伪元素 > 通配符

+兄弟选择器   >子代选择器     a[href*="en-US] 属性选择器



元素类型

块级元素(某些重要元素) display:block  独占一行可以设置宽高 高度由内容决定

行内元素 inline 不独占一行 宽高由内容决定 

行内块元素 inline-block 不独占一行 可以设置宽度和高度

隐藏元素:none 不占空间

p元素不能包含其他块级元素

visibility:hidden  隐藏但是还占据空间

alpha:设置为0   其中的颜色透明度为某个值,不会影响子元素的

color:rgba(0,0,0,0)

bg-color:transparent(默认值)

opacity:0  透明度 也会给子元素的透明度