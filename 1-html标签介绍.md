```js
<style>
 p {
	 color: #666666;
 }
 .list {
	 width: 400px;
 }
</style>

<div class="list">标签内容</div>
<br/>
<img src="http://xx.com"/>
```

HTML标签是由`<>`包围的关键词，例如`<html>`

HTML标签通常成对出现，分为标签开头和标签结尾，例如`<html></html>`

有部分标签是没有结束标签，成为单标签，单标签内必须用`/`结尾。例如`<br/>`

页面中所有的内容，都要放在HTML标签中

HTML标签主题分为三个部分：

- 标签名称
- 标签内容
- 标签属性

HTML标签具有语义化

- 语义化，就是仅通过标签名就能判断出该标签的内容

语义化的作用

- 网页结构层次更清晰
- 更容易被搜索引擎收录
- 更容易让屏幕阅读器读出网页内容

标签的内容就是一对标签内部的内容

标签的内容可以是其他标签

## 标签全局标准属性

规定了8个全局标准属性

class属性

- 用于定义元素的类名

id属性

- 用于指定元素的唯一id
- 注意该属性的值在整个HTML文档中具有唯一性

style属性

- 用于指定元素的行为样式
- 使用该属性后将会覆盖任何全局的样式设定

title属性

- 用于指定元素的额外信息

accesskey属性

- 用于指定激活元素的快捷键

tabindex属性

- 用于指定元素在tab键下的次序

dir属性

- 用于指定元素中内容的文本方向
- 属性值只有`ltr`或`rtl`两种，分别是 `left to right`和`right to left`

lang属性

- 用于指定元素内容的语言

## HTML的全局事件属性

`window`窗口事件

`onload`在页面加载结束之后触发

`onunload`在用户从页面离开时发生

`form`表单事件

`onblur`当元素失去焦点时触发

`onchange`在元素的元素值被改变时触发

`onfocus`当元素获得焦点时触发

`onreset`当表单中的重置按钮被点击时触发

`onselect`在元素中文本被选中后触发

`onsubmit`在提交表单时触发

`keyboard`键盘事件

`onkeydown`在用户按下按键时触发

`onkeypress`在用户按下按键后，按着按键时触发。该属性不会对所有按键生效，不生效的有，alt,ctrl,shift,esc

`onkeyup`当用户释放按键时触发

`mouse`鼠标事件

`onclick`当元素上发生鼠标点击时触发

`onblclick`当元素上发生鼠标双击时触发

`onmousedown`当元素上按下鼠标按钮时触发

`onmousemove`当鼠标指针移动到元素上时触发

`onmouseout`当鼠标指针移出元素时触发

`onmouseover`当鼠标指针移动到元素上时触发

`onmouseup`当在元素上释放鼠标按钮时触发

`media`媒体事件

`onabort`当退出时触发

`onwaiting`当媒体已停止播放但打算继续播放时触发。




