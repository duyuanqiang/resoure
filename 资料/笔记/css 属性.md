css 属性

内容溢出

overflow:scroll/auto/visible/hidden

盒模型

margin+border+padding+content

内容是通过宽高设置的  行内级无法设置宽高

min-width最小 max-width最大 移动端常用

宽度默认值auto  会随着浏览器的大小变化

padding

border : width style(不可省略 常用 solid dashed) color

border-radius:数值,百分比(相对是同方向的长度)

margin 兄弟元素之间多用  padding  父子元素之间多用

正常盒模型只是设置的是内容的大小

怪异盒模型 box-sizing:border-box

margin

margin-top:子元素设置margin-top值会传递给父元素

解决方法

1.最好使用padding  或者给父元素设置border

2.触发bfc

3.父元素设置overflow:auto

margin-bottom也会传递   ,父元素的高度设置成auto

上下margin折叠  margin-bottom和margin-top的间隙是最大值

外轮廓 outline 去除a ,input 的默认效果

不占据空间 默认显示border外面

box-shadow: offset-x(水平偏移量 负数昨天) offset-y(垂直方向偏移量) blur-radius(模糊半径) spread-radius(延伸半径) (四周扩散值)  color(阴影颜色), (可设置多个阴影);

text-shadow:offset-x offset-y blur color

行内替换元素  padding值左右占空间,上下不占空间   border 上下被撑开但是不占空间

margin 上下的margin不生效

![image-20220811172052044](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220811172052044.png)

bg-color是包含在border下面

color 包含前景色,border颜色



设置盒子的宽高行为

box-sizing:border-box/content-box(正常盒子)

padding border  都在width和height之间

块级元素 有宽度margin:0 auto才会生效

ie8以下盒模型是怪异盒模型



显示省略号 ,元素必须固定宽度

whit-space:nowrap

overflow:hidden

text-overflow:ellipsis

访问别的图片出现403 img 添加 referrerpolicy="no-referrer" 可以拿到图片



多行显示省略号

display:-webkit-box;

-webkit-box-clamp:2;

-webkit-box-orient:vertical;



background 元素 元素必须设置宽高才会显示出来背景

bg-image; , ;可以设置多张背景图

bg-repeat: no-repeat,repeat-x;

bg-size: contaon(保证某一边先铺满),cover(最后一边按比例铺满),auto(默认显示) <percentage>(百分比),length(设置具体的尺寸);

bg-position:center(设置位置),px(设置具体); 设置背景居中常用的做法

bg-attachment:local;设置背景跟随内容滚动 scroll不跟随滚动 fixed   背景相对视口也不会滚动

缩写属性

background: color url(../) bg-position /size;

bg-image和img区别

一个是元素,一个是css样式

![image-20220812115109471](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220812115109471.png)