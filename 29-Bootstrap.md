Bootstrap概述

Bootstrap是由 Twiter 公司(全球最大的微博)的两名技术工程师研发的
一个基于HTML、CSS、JavScript 的开源框架。

该框架代码简洁、视觉优美，可用于快速、简单地构建基于 PC 及移动端设备的 Web 页面需求。 

2010 年 6 月，Twiter 内部的工程师为了解决前端开发任务中的协作统一问题。
经历各种方案后，Bootstrap 最终被确定下来，并于 2010 年 8 月发布。

经过很长时间的迭代升级，
由最初的 CSS 驱动项目发展成为内置很多 JavScript 插件和图标的多功能 Web 前端的开源框架。

Bootstrap最为重要的部分就是它的响应式布局，
通过这种布局可以兼容 PC 端、PAD以及手机移动端的页面访问。 

Bootstrap 下载及演示： 
```
国内文档翻译官网：htp:/w.botcs.com 瓢城 Web 俱乐部官网：htp:/w.ycku.com
```
Bootstrap特点

Bootstrap非常流行，得益于它非常实用的功能和特点。主要核心功能特点如下：

•跨设备、跨浏览器 可以兼容所有现代浏览器，包括比较诟病的 IE7、8。当然，本课程不再考虑 IE9 以下浏览器。

•响应式布局 不但可以支持 PC 端的各种分辨率的显示，还支持移动端 PAD、手机等屏幕的响应式切换显示。

•提供的全面的组件 Bootstrap 提供了实用性很强的组件，包括：导航、标签、工具条、按钮等一系列组件，方便开发者调用。

•内置 jQuery 插件 Bootstrap 提供了很多实用性的 jquery 插件，这些插件方便开发者实现 Web 中各种常规特效。

•支持 HTML5、CSS3 HTML5 语义化标签和 CSS3 属性，都得到很好的支持。

•支持 LESS 动态样式 LESS 使用变量、嵌套、操作混合编码，编写更快、更灵活的 CS。它和 Bootstrap 能很好的配合开发。

Bootstrap结构

首先，想要了解 Bootstrap的文档结构，需要在官网先把它下载到本地。

Bootstrap下载地址如下： 

Bootstrap下载地址：htp:/v3.botcs.com/ (选择生产环境即可，v3.4) 解压后，
目录呈现这样的结构：
```
Bootstrap/
├─ css/
│ ├─ Bootstrap .css
│ ├─ Bootstrap .cs.map
│ ├─ Bootstrap .min.css
│ ├─ Bootstrap-them.css
│ ├─ Bootstrap-them.cs.map
│ └─ Bootstrap-them.min.css
├─ js/
│ ├─ Bootstrap.js
│ └─ Bootstrap.min.js
└─ fonts/
├─ glyphicons-halfings-regular.eot
├─ glyphicons-halfings-regular.svg
├─ glyphicons-halfings-regular.tf
├─ glyphicons-halfings-regular.wof
└─ glyphicons-halfings-regular.wof2
```


主要分为三大核心目录：cs(样式)、js(脚本)、fonts(字体)。

•css 目录中有四个 css 后缀的文件，其中包含 min 字样的，
是压缩版本，一般使用这个；不包含的属于没有压缩的，可以学习了解 css 代码的文件；而 map 后缀的文件则是css 源码映射表，在一些特定的浏览器工具中使用。

•js 目录包含两个文件，是未压缩和压缩的 js 文件。

•fonts 目录包含了不同后缀的字体文件。

创建第一个页面

我们创建一个 HTML5 的页面，并且将 Bootstrap的核心文件引入，
然后测试是否正常显示。

第一个 Bootstrap
```
<!DOCTYPE html>
<htmlang="zh-cn"><head>
<meta charset="UTF-8">
<tile>Bootstrap 介绍</tile>
<link rel="styleshet" href="cs/Bootstrap.min.cs">
</head>
<body>
<buton class="btn btn-info">Bootstrap</buton>
<script src="js/jquery.min.js"></script>
<script src="js/Bootstrap.min.js"></script>
</body>
</html>
```

```js
输入框组件
文本输入框就是可以在元素前后加上文字或按钮，可以实现对表单控件的扩展。
//在左侧添加文字
<div class="input-group">
<span class="input-group-addon">@</span>
<input type="text" class="form-control">
</div>
//在右侧添加文字
<div class="input-group">
<input type="text" class="form-control">
<span class="input-group-addon">@163.com</span>
</div>
//在两侧添加文字
<div class="input-group">
<span class="input-group-addon">$</span>
<input type="text" class="form-control">
<span class="input-group-addon">.00</span>
</div>
//设置尺寸，另外三种分别是默认、xs、sm
<div class="input-group input-group-lg">
//左侧使用复选框和单选框
<div class="input-group">
<span class="input-group-addon"><input type="checkbox"></span>
<input type="text" class="form-control">
</div>
<div class="input-group">
<span class="input-group-addon"><input type="radio"></span>
<input type="text" class="form-control">
</div>
//左侧使用按钮
<div class="input-group">
<span class="input-group-btn">
<button type="button" class="btn btn-default">按钮</button>
</span>
<input type="text" class="form-control">
</div>
//左侧使用下拉菜单或分列式
<div class="input-group">
<span class="input-group-btn">
<button class="btn btn-default dropdown-toggle"
data-toggle="dropdown">
下拉菜单
<span class="caret"></span>
</button>
<ul class="dropdown-menu">
<li class="dropdown-header">网站导航</li>
<li><a href="#">首页</a></li>
<li><a href="#">资讯</a></li>
<li class="divider"><a href="#">产品</a></li>
<li class="disabled"><a href="#">关于</a></li>
</ul>
</span>
<input type="text" class="form-control">
</div>
导航组件
Bootstrap 提供了一组导航组件，用于实现 Web 页面的栏目操作。
//基本导航标签页
<ul class="nav nav-tabs">
    <li class="active"><a href="#">首页</a></li>
    <li><a href="#">资讯</a></li>
    <li><a href="#">产品</a></a></li>
    <li><a href="#">关于</a></li>
</ul>
//胶囊式导航
<ul class="nav nav-pills">
//垂直胶囊式导航
<ul class="nav nav-pills nav-stacked">
//导航两端对齐
<ul class="nav nav-tabs nav-justified">
//禁用导航中的项目
<li class="disabled"><a href="#">关于</a></li>

//带下拉菜单的导航
<ul class="nav nav-tabs">
    <li class="active"><a href="#">首页</a></li>
    <li><a href="#">资讯</a></li>
    <li class="dropdown">
        <a href="#" class="dropdown-toggle" data-toggle="dropdown">下拉菜单
            <span class="caret"></span>
        </a>
        <ul class="dropdown-menu">
            <li><a href="#">菜单一</a></li>
            <li><a href="#">菜单二</a></li>
        </ul>
    </li>
</ul>
导航条组件
导航条是网站中作为导航页头的响应式基础组件。
//基本格式
<nav class="navbar navbar-default">
...
</nav>
//反色调导航
<nav class="navbar navbar-inverse">
...
</nav>
//基本导航条，包含标题和列表
<nav class="navbar navbar-default">
<div class="container">
<div class="navbar-header">
<a href="#" class="navbar-brand">标题</a>
</div>
<ul class="nav navbar-nav">
<li class="active"><a href="#">首页</a></li>
<li><a href="#">资讯</a></li>
<li class="disabled"><a href="#">产品</a></li>
<li><a href="#">关于</a></li>
</ul>
</div>
</nav>
//导航条中使用表单
<form action="" class="navbar-form navbar-left">
<div class="input-group">
<input type="text" class="form-control">
<span class="input-group-btn">
<button type="submit" class="btn btn-default">提交</button>
</span>
</div>
</form>
//导航中使用按钮
<button class="btn btn-default navbar-btn">按钮</button>
//导航中使用对齐方式，left 和 right
<button class="btn btn-default navbar-btn navbar-right">按钮</button>
//导航中使用一段文本
<p class="navbar-text">我是一段文本</p>
//非导航链接，一般需要置入文本区域内
<a href="#" class="navbar-link">非导航链接</a>
//将导航固定在顶部，下面的内容会自动上移
<nav class="navbar navbar-default navbar-fixed-top">
//将导航补丁在底部
<nav class="navbar navbar-default navbar-fixed-bottom">
//静态导航，和页面等宽的导航条，去掉了圆角
<nav class="navbar navbar-default navbar-static-top">
```

```js
路径组件
路径组件也叫做面包屑导航。
//面包屑导航
<ol class="breadcrumb">
    <li><a href="#">首页</a></li>
    <li><a href="#">产品列表</a></li>
    <li class="active">韩版 2015 年羊绒毛衣</li>
</ol>
分页组件
分页组件可以提供带有展示页面的功能。
//默认分页
<ul class="pagination">
    <li><a href="#">&laquo;</a></li>
    <li><a href="#">1</a></li>
    <li><a href="#">2</a></li>
    <li><a href="#">3</a></li>
    <li><a href="#">4</a></li>
    <li><a href="#">5</a></li>
    <li><a href="#">&raquo;</a></li>
</ul>
//首选项和禁用
<li class="active"><a href="#">1</a></li>
<li class="disabled"><a href="#">2</a></li>

//设置尺寸，四种 lg、默认、sm 和 xs
<ul class="pagination pagination-lg">

//翻页效果
<ul class="pager">
    <li><a href="#">上一页</a></li>
    <li><a href="#">下一页</a></li>
</ul>

//对齐翻页链接
<ul class="pager">
    <li class="previous"><a href="#">上一页</a></li>
    <li class="next"><a href="#">下一页</a></li>
</ul>

//翻页项禁用
<li class="previous disabled"><a href="#">上一页</a></li>
标签
//在文本后面带上标签
<h3>标签 <span class="label label-default">new</span></h3>

//不同色调的标签
<h3>标签 <span class="label label-primary">new</span></h3>
<h3>标签 <span class="label label-success">new</span></h3>
<h3>标签 <span class="label label-info">new</span></h3>
<h3>标签 <span class="label label-warning">new</span></h3>
<h3>标签 <span class="label label-danger">new</span></h3>
徽章
//未读信息数量徽章
<a href="#">信息 <span class="badge">10</span></a>

//按钮中使用徽章
<button class="btn btn-success">提交 <span class="badge">3</span></button>

//激活状态自动适配色调
<ul class="nav nav-pills">
    <li class="active"><a href="#">首页 <span class="badge">2</span></a></li>
    <li><a href="#">资讯</a></li>
</ul>
```

```js
巨幕组件
巨幕组件主要是展示网站的关键性区域。
//在固定的范围内，有圆角
<div class="container">
    <div class="jumbotron">
    	<h2>网站标题</h2>
    	<p>这是一个学习性的网站！</p>
    	<p><a href="#" class="btn btn-default">更多内容</a></p>
    </div>

	<div class="jumbotron">
        <div class="container">
    		<h2>网站标题</h2>
    		<p>这是一个学习性的网站！</p>
    		<p><a href="#" class="btn btn-default">更多内容</a></p>
    	</div>
	</div>
</div>
页头组件
//增加一些空间
<div class="page-header">
	<h1>大标题 <small>小标题</small></h1>
</div>
缩略图组件
//缩略图配合响应式
<div class="container">
    <div class="row">
        <div class="col-xs-6 col-md-3 col-sm-4">
            <div class="thumbnail">
    			<img src="img/pic.png" alt="">
			</div>
		</div>
		<div class="col-xs-6 col-md-3 col-sm-4">
			<div class="thumbnail">
        		<img src="img/pic.png" alt="">
        	</div>
		</div>
		<div class="col-xs-6 col-md-3 col-sm-4">
			<div class="thumbnail">
				<img src="img/pic.png" alt="">
			</div>
		</div>
        <div class="col-xs-6 col-md-3 col-sm-4">
        	<div class="thumbnail">
        	<img src="img/pic.png" alt="">
        	</div>
		</div>
	</div>
</div>


//自定义内容
<div class="container">
    <div class="row">
        <div class="col-xs-6 col-md-3 col-sm-4">
            <div class="thumbnail">
            	<img src="img/pic.png" alt="">
                <div class="caption">
                    <h3>图文并茂</h3>
                    <p>这是一个图片结合文字的缩略图</p>
                    <p><a href="#" class="btn btn-default">进入</a></p>
                </div>
    		</div>
		</div>

		<div class="col-xs-6 col-md-3 col-sm-4">
			<div class="thumbnail">
				<img src="img/pic.png" alt="">
				<div class="caption">
					<h3>图文并茂</h3>
					<p>这是一个图片结合文字的缩略图</p>
					<p><a href="#" class="btn btn-default">进入</a></p>
				</div>
			</div>
		</div>

		<div class="col-xs-6 col-md-3 col-sm-4">
			<div class="thumbnail">
				<img src="img/pic.png" alt="">
				<div class="caption">
					<h3>图文并茂</h3>
					<p>这是一个图片结合文字的缩略图</p>
					<p><a href="#" class="btn btn-default">进入</a></p>
				</div>
			</div>
		</div>

        <div class="col-xs-6 col-md-3 col-sm-4">
			<div class="thumbnail">
				<img src="img/pic.png" alt="">
				<div class="caption">
					<h3>图文并茂</h3>
					<p>这是一个图片结合文字的缩略图</p>
					<p><a href="#" class="btn btn-default">进入</a></p>
				</div>
			</div>
		</div>
	</div>
</div>
警告框组件
警告框组件是一组预定义消息。
//基本警告框
<div class="alert alert-success">Bootstrap</div>
<div class="alert alert-info">Bootstrap</div>
<div class="alert alert-warning">Bootstrap</div>
<div class="alert alert-danger">Bootstrap</div>

//带关闭的警告框
<div class="alert alert-success">
    Bootstrap
    <button type="button" class="close" data-dismiss="alert"><span>&times;</span></button>
</div>
//自动适配的超链接
<div class="alert alert-success">
	Bootstrap，请到官网 <a href="#" class="alert-link">下载</a>
</div>
```

基本使用

使用模态框的弹窗组件需要三层 div 容器元素，
分别为 modal(模态声明层)、dialog(窗口声明层)、content(内容层)。

在内容层里面，还有三层，分别为 header(头部)、body(主体)、footer(注脚)。