`css`全称为层叠样式表，它主要是用于定义HTML内容在浏览器内的显示样式，如文字大小，颜色，字体加粗等。

`css`代码通常存放在style标签内

`css`样式由选择符和声明组成，而声明又由属性和值组成

选择符{属性：值}，例如：`p{color:red;}`;

选择符：又称选择器，指明网页中要应用样式规则的元素

声明：在英文大括号{}中的就是声明，属性和值之间用英文冒号：分隔。当有多条声明时，中间用英文分号；分隔。

`css`放置位置

行内样式

直接书写标签的style属性中

不建议使用

内联样式表

写在style标签中

外联样式表

将一个独立的`.css`文件引入到HTML文件中，使用`link`标签写在head标签中。

`rel="stylesheet"`定义类型为层叠样式表

`css`的继承

`css`的某些样式是具有继承性的，那么什么是继承呢？继承是一种规则，它允许样式不仅应用于某个特定html标签元素，而且应用于其后代。

不可继承样式：display,margin,border,padding,background,height,
minheight,max-height,width,min-width,max-width,
overflow,position,left,right,top,bottom,z-index,float,clear

可继承的样式：letter-spacing,word-spacing,white-space,line-height
color,font,font-family,font-size,font-style,font-variant,
font-weight,text-decoration,text-transform,direction,visibility,cursor


