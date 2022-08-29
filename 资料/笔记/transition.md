transition

在mdn搜索那些属性可以设置动画的。 #可以设置多个属性，空格隔开

transition属性 transition-property，transition-duration，transition-timing-function,transition-delay

transition不能定义中间状态，不能重复执行性，需要在特定状态下才能执行

transform 形变属性

translate（形变函数）

transition：动画属性，主要用来做过渡动画： all 对所有属性生效 ，也可以具体到某个属性



Animation：

通过@keyframes 定义动画状态,序列帧动画

人眼看的小于16帧，会感觉卡顿

@keyframes aniName{

​	0%{

​		transform:

​	}

​	50%{

​		transform:

​	}

​	100%{

​		transform:

​	}

}

animation-name/duration/timing-function(重点)

animation-iteration-count:执行次数 infinite 无限次数

animation-direction:reverse/normal;

animation-fill-mode:forwards ：元素停留在动画哪个位置

animation-play-state：paused 通过js操控动画状态

animation:name dur timing-function dealy  direction fill-mode