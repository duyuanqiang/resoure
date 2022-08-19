<h3>弹性盒flex

display:flex 一维布局

默认主轴方向'

flex-container的css属性

flex-direction: row-reverse(改变主轴方向,主轴翻转); column(列为主轴) column-reverse(列为主轴翻转)

flex-wrap:no-wrap(单行) wrap(多行) wrap-reverse(换行翻转)

flex-flow属性是flex-direction和flex-wrap的简写.顺序任意,可以省略    

flex-flow:row wrap

(对齐方式)justify-content: flex-start center flex-end space-between space-around(左右两端间隙,等于其他item间隙的一半) space-evenly(左右两端间隙和其他item之间间隙相等)

align-item决定item在交叉轴上的对其方式

align-item:normal stretch(会将交叉轴的长度为auto的拉伸填充flex-container,高度默认为auto,有高度此属性无效)

flex-start(cross start对齐) flex-end(与cross end对齐) center(居中对齐) baseline(与基线对齐 x的底线)

flex-wrap:wrap;

大多在不知道高度情况下,设置多行的对齐方式

align-content: stretch flex-start flex-end center space-between space-around space-evenly



flex-item的属性

order:0(数字越小,越排在前面.默认0)

align-self: auto,stretch,flex-start,flex-end,center,baseline(独立的对某一个item设置,可以覆盖flex-container设置的align-items)

flex-grow:1决定了flex-items如何扩展)

可以设置任意非负数,默认值是0

当flex container在main axis方向上有剩余size时,flex-grow才会生效

当flex-grow总数大于1,则每个item的size为size*flex-grow/sum

不能大于max-width

flex-shrink决定了flex items如何收缩

可以设置任何非负数,默认值为1

flex items 在main axis方向上超过flex container的size,才会生效

如果flex shrink的总和超过1,每个flex item瘦多的size

flex items 超出flex container的size*收缩比例/所有felx items的收缩比例之和

不能小于min-width

flex-basic 基础尺寸为了将内容完全显示,会拉伸宽度 auto

决定flex-basic 最终生效的优先级,从高到低

max-width/max-height/min-width/min-height

flex-basis

width height

内容本身的size

flex是felx-grow||flex-shrink ||flex-basis的简写,flex属性可以指定1个,2个或3个值

none|[<flex-grow><flex-shrink>?||<flex-basis>] | auto

样式布局和游戏一样有许多假象的东西

为了让多行布局整齐,需要填充列数-2个i元素 