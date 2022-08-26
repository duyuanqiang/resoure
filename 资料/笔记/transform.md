tansform 水平和垂直居中

行内替换元素不能形变

tansform:<function> 

tanslate(x,y)位移 单位 px,%(相对于自己的大小)

translateX() translateY()

设置居中

水平居中

行内 text-align:center

块级元素 magin: 0 auto 

绝对定位:在元素有宽度的情况下

flex justify-content:center

垂直居中

行内 line-height值和高度一致

定位,元素必须有高度

flex布局 align-item:center

transform 移动父元素的50%,然后再移动自身的50%,设置定位position:relative,top:50%,translateY:50%

margin-top:50%相对于包含块的宽度