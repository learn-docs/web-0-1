背景颜色background-color

背景颜色的值可以是英文，可以是十六进制颜色值，可以是rgb

背景图片background-image

背景图片的大小可以和容器大小不一样

背景图片不会占位

如果容器大，背景图片小，背景图片会平铺 铺满整个容器

背景图片位置background-position

背景图片定位的值是两个单位，分别代表坐标x,y轴

背景图片定位的值可以是应为left,right,top,bottom,center

背景图片重复background-repeat

no-repeat数组图像不重复，常用

round自动缩放直到适应并填充整个容器

space以相同的间距平铺且填充整个容器

背景图片定位background-attachment

`background-attachment:fixed`

背景图像是否固定或者随着页面的其余部分滚动

`background-attachment`的值可以是`scroll`，`fixed`

`background`缩写

`background: #ff0000 url(bg01.jpg) no-repeat fixed center`

字体样式

字体族：`font-family`

字体大小：`font-size`

字体粗细：`font-weight`

`font-weight`：400

`normal`默认

`bold`加粗

`bolder`

`lighter`

字体颜色`color`

字体斜体：`font-style`

- `font-style:italic`
- `normal`文本正常显示
- `italic`文本斜体显示
- `oblique`文本倾斜显示

文本属性

行高`line-height`

`line-height:50px`

可以将父元素的高度撑起来

文本水平对齐方式：`text-align`

`left`，`center`，`right`

文本所在行高的垂直对齐方式：`vertical-align`

`baseline`默认

`sub`垂直对齐文本的下标，和`sub`标签一样的效果

`super`垂直对齐文本的上标，和`sup`标签一样的效果

`top`对象的顶端与所在容器的顶端对齐

`text-top`对象的顶端与所在行文字顶端对齐

`middle`元素对象基于基线垂直对齐

`bottom`对象的底端与所在行的文字底部对齐

`text-bottom`对象的底端与所在行文字的底端对齐

文本缩进`text-indent`

`text-indent:2em`

通常用在段落开始位置的首行缩进

字母之间的间距`letter-spacing`

单词之间间距：`word-spacing`

文本的大小写`text-transform`

`capitalize`文本中的每个单词以大写字母开头。

`uppercase`定义仅有大写字母

`lowercase`定义仅有小写字母

文本的装饰`text-decoration`

`none`默认

`underline`下划线

`overline`上化线

`line-through`中线

自动换行`word-wrap`

`word-wrap: break-word`

基本样式

width,height

元素默认没有高度，需要设置高度，让元素的内容将元素撑高

鼠标样式`cursor`

定义鼠标的样式`cursor:pointer`

`default`默认，`pointer`小手形状，`move`移动形状

透明度`opacity`

`opacity:0.3`

透明度的值可以使0到1之间的数字，0代表透明，1代表完全不透明

透明的元素只是看不见，但是还占据文档流。

可见性`visibility`

`visibility:hidden`

`visible`元素可见

`hidden`元素不可见

`collapse`当在表格元素中使用时，此值可删除一行或一列，不会影响表格的布局

溢出隐藏`overflow`

设置当对象的内容超过其指定高度及宽度时如何显示内容

`visible`默认值，内容不会被修剪，会呈现在元素框之外

`hidden`内容会被修剪，并且其余内容是不可见的

`scroll`内容会被修剪，但是浏览器会显示滚动条以便查看其余的内容。

`auto`如果内容被修剪，则浏览器会显示滚动条以便查看其余的内容。

边框颜色outline

`input`文本框自带边框，且样式丑陋

`outline:none`清除边框

样式重置

清除元素的margin和padding

去掉自带的列表符

去掉自带的下划线

盒模型样式

块状元素，内联元素，内联壮元素

元素分类转换display

block,将元素转换为块级元素

inline,将元素转换为行级元素

inline-block,将元素转换为内联块元素

none将元素隐藏

描边border

线条的样式：

`dashed`虚线,`dotted`点线，`solid`实线

`css`样式中允许只为一个方向的边框设置样式

下描边`border-bottom`

上描边`border-top`

右描边`border-right`

左描边`border-left`

间距margin

内填充padding

浮动float

浮动原理：浮动使元素脱离文档普通流，漂浮在普通流之上的

浮动元素依然按照其在普通流的位置上出现，然后尽可能的根据设置的浮动方向向左或向右浮动，
知道浮动元素的外边缘遇到包含框或者另一个浮动元素为止，且允许文本和内联元素环绕它

浮动会产生块级框，而不管该元素本身是什么

清除浮动带来的影响

clear清除浮动

`none`不清除,`left`不允许左边有浮动对象，`right`,`both`

利用伪类实现清除浮动

```js
.clearFix{
	content="";
	display: block;
	width: 0;
	height: 0;
	clear: both;
}
```

定位position

层模型，绝对定位（相对于父类）

如果想为元素设置层模型中的绝对定位，需要设置`position:absolute`绝对定位，这条语句的作用加你个元素
从文档流中拖出来，然后使用left,right,top,bottom属性相对于其最接近的一个
具有定位属性的父包含块进行绝对定位。

如果不存在这样的包含块，则相对于body元素，即相对于浏览器窗口

`position:absolute`

```
div{
	width: 200px;
	height: 200px;
	border: 2px red solid;
	position: absolute;
	left: 100px;
	top: 20px;
}
```

层模型-相对定位（相对于原位置）

`position: relative`

```js
#div{
	width: 200px;
	height: 200px;
	border: 2px red solid;
	position: relative;
	left: 100px;
	top: 20px;
}
```

层模型-固定定位（相对于网页窗口）

`position: fixed`
