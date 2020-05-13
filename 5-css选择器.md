标签选择器

通过标签的名字，修改css样式

```js
div{
	width: 200px;
	height: 300xp;
}
```

通配符选择器

`*`选择页面中所有的元素

```js
* {
	margin: 0;
	padding: 0;
}
```

一级子元素选择器

选择某个父元素的直接子元素

后代选择器是选择父元素的所有子孙元素，一级子元素原则只选择第一级子元素，不会再向下查找元素

```js
.box > p {
	background-color: red;
}
```

id选择器

通过id查找页面中唯一的标签，用#表示id

```js
#dada {
	width: 200px;
	height: 200px;
}
```

class选择器

通过特定的`class`来查找页面中对应的标签

```js
.box{
	width: 200px;
	height: 300px;
}
<div class="box"></div>
```

伪类选择器

`:hover`鼠标移入某个元素

```js
.box:hover {
	color: red;
}
```

`:before`在某个元素的前面插入内容

```js
div:before {
	content: '-dadaqianduan';
	background-color: yellow;
	color: red;
}
```

`:afer`在某个元素的后面插入内容

```js
div:after{
	content: '-dadaqianduan';
	color: red;
}
```

群组选择器

- 可以对多个不同的选择器设置相同的样式

```js
.box, .box1, .box2 {
	width: 200px;
	height: 300px;
}
```

选择器的优先级

当有不同的选择器对同一个对象进行样式指定时，并且两个选择器有相同的属性被赋予不同的值时。

通过测算那个选择器的权重值最高，应用哪一个选择器的样式

权重计算方式

- 标签选择器：1
- class选择器：10
- id选择器：100
- 行内样式：1000
- !important最高级别，提高样式权重，拥有最高级别

注意：

如果两个选择器的权重值一样高，应用距离对象最近的`css`样式



