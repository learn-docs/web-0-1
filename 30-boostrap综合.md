```js
第一章 Bootstrap介绍
第一节 Bootstrap概述
Bootstrap是由 Twiter 公司(全球最大的微博)的两名技术工程师研发的一个基于HTML、CSS、JavScript 的开源框架。该框架代码简洁、视觉优美，可用于快速、简单地构建基于 PC 及移动端设备的 Web 页面需求。 2010 年 6 月，Twiter 内部的工程师为了解决前端开发任务中的协作统一问题。经历各种方案后，Bootstrap 最终被确定下来，并于 2010 年 8 月发布。经过很长时间的迭代升级，由最初的 CSS 驱动项目发展成为内置很多 JavScript 插件和图标的多功能 Web 前端的开源框架。 Bootstrap最为重要的部分就是它的响应式布局，通过这种布局可以兼容 PC 端、PAD以及手机移动端的页面访问。 Bootstrap 下载及演示： 国内文档翻译官网：htp:/w.botcs.com 瓢城 Web 俱乐部官网：htp:/w.ycku.com


第二节 Bootstrap特点
Bootstrap非常流行，得益于它非常实用的功能和特点。主要核心功能特点如下：
•跨设备、跨浏览器 可以兼容所有现代浏览器，包括比较诟病的 IE7、8。当然，本课程不再考虑 IE9 以下浏览器。
•响应式布局 不但可以支持 PC 端的各种分辨率的显示，还支持移动端 PAD、手机等屏幕的响应式切换显示。
•提供的全面的组件 Bootstrap 提供了实用性很强的组件，包括：导航、标签、工具条、按钮等一系列组件，方便开发者调用。
•内置 jQuery 插件 Bootstrap 提供了很多实用性的 jquery 插件，这些插件方便开发者实现 Web 中各种常规特效。
•支持 HTML5、CSS3 HTML5 语义化标签和 CSS3 属性，都得到很好的支持。
•支持 LESS 动态样式 LESS 使用变量、嵌套、操作混合编码，编写更快、更灵活的 CS。它和 Bootstrap 能很好的配合开发。

第三节 Bootstrap结构
首先，想要了解 Bootstrap的文档结构，需要在官网先把它下载到本地。Bootstrap下载地址如下： Bootstrap下载地址：htp:/v3.botcs.com/ (选择生产环境即可，v3.4) 解压后，目录呈现这样的结构：
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
主要分为三大核心目录：cs(样式)、js(脚本)、fonts(字体)。
•css 目录中有四个 css 后缀的文件，其中包含 min 字样的，是压缩版本，一般使用这个；不包含的属于没有压缩的，可以学习了解 css 代码的文件；而 map 后缀的文件则是css 源码映射表，在一些特定的浏览器工具中使用。
•js 目录包含两个文件，是未压缩和压缩的 js 文件。
•fonts 目录包含了不同后缀的字体文件。

第四节 创建第一个页面
我们创建一个 HTML5 的页面，并且将 Bootstrap的核心文件引入，然后测试是否正常显示。
第一个 Bootstrap
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


第二章 Bootstrap栅格布局
第一节 栅格布局简介
Bootstrap内置了一套响应式、移动设备优先的流式栅格系统，随着屏幕设备或视口（viewport）尺寸的增加，系统会自动分为最多12列。它包含了易于使用的预定义classe，还有强大的mixin用于生成更具语义的布局。
容器：“行（row）”必须包含在 .container （固定宽度）或 .container-fluid （100% 宽度）中，以便为其赋予合适的排列（aligment）和内补（padding）。
rem：实际上是设置列的高度的属性，rem的值是整数，代表的高度是rem值*字体像素大小。
工作原理如下：
•“行（row）”必须包含在 .container （固定宽度）或 .container-fluid （100%宽度）中，以便为其赋予合适的排列（aligment）和内补（padding）。
•通过“行（row）”在水平方向创建一组“列（column）”。
•你的内容应当放置于“列（column）”内，并且，只有“列（column）”可以作为行（row）”的直接子元素。
•类似 .row 和 .col-xs-4 这种预定义的类，可以用来快速创建栅格布局。Bootstrap 源码中定义的 mixin 也可以用来创建语义化的布局。
•通过为“列（column）”设置 padding 属性，从而创建列与列之间的间隔（gutter）。通过为 .row 元素设置负值 margin 从而抵消掉为 .container 元素设置的 padding，也就间接为“行（row）”所包含的“列column）”抵消掉了 padding。
•负值的 margin 就是下面的示例为什么是向外突出的原因。在栅格列中的内容排成一行。
•栅格系统中的列是通过指定 1 到 12 的值来表示其跨越的范围。例如，三个等宽的列可以使用三个 .col-xs-4 来创建。
•如果一“行（row）”中包含了的“列（column）”大于 12，多余的“列（column）”所在的元素将被作为一个整体另起一行排列。
•栅格类适用于与屏幕宽度大于或等于分界点大小的设备 ， 并且针对小屏幕设备覆盖栅格类。 因此，在元素上应用任何 .col-md-* 栅格类适用于与屏幕宽度大于或等于分界点大小的设备 ，并且针对小屏幕设备覆盖栅格类。因此，在元素上应用任何 .col-lg-*不存在， 也影响大屏幕设备。
•在前端开发中，使用框架会带来很舒畅的开发过程，但某些情况下，使用框架可能会导致性能问题，例如，开发一个网页，也用到了BootStrap框架的一些东西，但使用率仅仅有百分之几，这种情况下，浏览器在加载这个网页的时候，会将 BootStrap剩下没有用到的百分之九十多也会加载，存在了一些性能浪费。这种情况下我们就需要对框架进行定制或优化，取出我们用到的代码，或者删除掉无用的代码，这需要对源码有相应的熟悉才能做到。

第二节 Bootstrap相应设备类型
栅格系统最外层区分了四种宽度的浏览器：超小屏(<768px)、小屏(>=768px)、中屏(>=992px)和大屏>=1200px)。而内层.container 容器的自适应宽度为：自动、750px、970px 和 1170px。自动的意思为，如果你是手机屏幕，则全面独占一行显示。
<div class="container">
    <div class="row">
        <div class="col-lg-3 col-md-4 col-sm-6 col-xs-12 a">4</div>
        <div class="col-lg-3 col-md-4 col-sm-6 col-xs-12 a">4</div>
        <div class="col-lg-3 col-md-4 col-sm-6 col-xs-12 a">4</div>
        <div class="col-lg-3 col-md-4 col-sm-6 col-xs-12 a">4</div>
        <div class="col-lg-3 col-md-4 col-sm-6 col-xs-12 a">4</div>
        <div class="col-lg-3 col-md-4 col-sm-6 col-xs-12 a">4</div>
        <div class="col-lg-3 col-md-4 col-sm-6 col-xs-12 a">4</div>
        <div class="col-lg-3 col-md-4 col-sm-6 col-xs-12 a">4</div>
        <div class="col-lg-3 col-md-4 col-sm-6 col-xs-12 a">4</div>
        <div class="col-lg-3 col-md-4 col-sm-6 col-xs-12 a">4</div>
        <div class="col-lg-3 col-md-4 col-sm-6 col-xs-12 a">4</div>
        <div class="col-lg-3 col-md-4 col-sm-6 col-xs-12 a">4</div>
    </div>
</div>
为了显示明显的 CSS
.a {
height: 100px;
background-color: #eee;
border:1px solid #ccc;
}
有时我们可以设置列偏移，让中间保持空隙
<div class="container">
    <div class="row">
        <div class="col-md-8 a">8</div>
        <div class="col-md-3 col-md-offset-1 a">3</div>
    </div>
</div>
也可以嵌套，嵌满也是 12 列
<div class="container">
    <div class="row">
        <div class="col-md-9 a">
            <div class="col-md-8 a">1-8</div>
            <div class="col-md-4 a">9-12</div>
        </div>
        <div class="col-md-3 a">
        	11-12
        </div>
    </div>
</div>
可以把两个列交换位置，push 向左移动，pull 向右移动
<div class="container">
    <div class="row">
        <div class="col-md-9 col-md-push-3 a">9</div>
        <div class="col-md-3 col-md-pull-9 a">3</div>
    </div>
</div>
移动设备优先
<meta name="viewport" content="width=device-width, initial-scale=1,
maximum-scale=1, user-scalable=no">
布局容器
Bootstrap 需要为页面内容和栅格系统包裹一个.container 容器。由于 padding 等属性的原因，这两种容器类不能相互嵌套。
//固定宽度
<div class="container">
...
</div>
//100%宽度
<div class="container-fluid">
...
</div>
第三节 栅格基本布局
Bootstrap中的基本网格布局的代码如下：
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8">
        <link rel="stylesheet" href="css/bootstrap.css" type="text/css">
        <style>
            .row>div {
                background: pink;
                border: 1px solid rgba(86, 61, 124, 0.2);
            }

            .title {
                font-size: 30px;
                color: red;
                text-align: center;
            }
        </style>
    </head>
    <body>
        <p class="title">栅格最基本布局</p>
        <!--基本的方格布局-->
        <div class="row">
            <div class="col-2">col-2</div>
            <div class="col-2">col-2</div>
            <div class="col-2">col-2</div>
        </div>
栅栏布局中有一个特殊的类col-auto，这个类会根据内容的大小自动的扩充列数，而普通的如果内容的长度超过列数就会加行。


第四节 栅格水平和垂直布局
水平布局是通过在行的div标签中利用justify-content-类型来实现的，如下所示：
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8">
        <link rel="stylesheet" href="css/bootstrap.css" type="text/css">
        <style>
            .row>div {
                background: pink;
                border: 1px solid rgba(86, 61, 124, 0.2);
            }

            .title {
                font-size: 30px;
                color: red;
                text-align: center;
            }
        </style>
    </head>
    <body>
        <p class="title">水平布局</p>
        <!--水平的排列方式-->
        <div class="row justify-content-start">
            <div class="col-2">start</div>
            <div class="col-2">start</div>
            <div class="col-2">start</div>
        </div>
        <div class="row justify-content-center">
            <div class="col-2">center</div>
            <div class="col-2">center</div>
            <div class="col-2">center</div>
        </div>
        <div class="row justify-content-end">
            <div class="col-2">end</div>
            <div class="col-2">end</div>
            <div class="col-2">end</div>
        </div>
        <div class="row justify-content-around">
            <div class="col-2">around</div>
            <div class="col-2">around</div>
            <div class="col-2">around</div>
        </div>
        <div class="row justify-content-between">
            <div class="col-2">between</div>
            <div class="col-2">between</div>
            <div class="col-2">between</div>
        </div>
    </body>
</html>
垂直布局和水平布局类似，利用align-items-类型来实现的垂直布局，但是垂直布局中只有start、center、end三种。
第五节 栅格排序和偏移
通过order-数值这个类进行网格的位置排列，代码如下：
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8">
        <link rel="stylesheet" href="css/bootstrap.css" type="text/css">
        <style>
            .row>div {
                background: pink;
                border: 1px solid rgba(86, 61, 124, 0.2);
            }
        </style>
    </head>
    <body>
        <div class="row">
            <div class="col-3 order-0">我是老大</div>
            <div class="col-3 order-2">我是老二</div>
            <div class="col-3 order-1">我是老三</div>
        </div>
    </body>
</html>
列偏移可以通过offset-数字这个类进行网格位置的偏移。
Bootstrap还支持列嵌套，有了列嵌套，栅格布局显得非常的灵活，示例如下：
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8">
        <link rel="stylesheet" href="css/bootstrap.css" type="text/css">
        <style>
            .row>div {
                background: pink;
                border: 1px solid rgba(86, 61, 124, 0.2);
            }
        </style>
    </head>
    <body>
        <div class="row">
            <div class="col-11">外层
                <div class="row">
                    <div class="col-6">内层1</div>
                    <div class="col-6">内层2</div>
                </div>
                <div class="row">
                    <div class="col-3">最内1</div>
                    <div class="col-4">最内2</div>
                </div>
            </div>
        </div>
    </body>
</html>


第三章 排版样式
第一节 页面主体
Bootstrap 将全局 font-size 设置为 14px，line-height 行高设置为 1.428(即20px)；<p>段落元素被设置等于 1/2 行高(即 10px)；颜色被设置为#333。 创建包含段落突出的文本
<p>Bootstrap 框架</p>
<p class="lead">Bootstrap 框架</p>
<p>Bootstrap 框架</p>
<p>Bootstrap 框架</p>
<p>Bootstrap 框架</p>
第二节 标题
从 h1 到 h6
<h1>Bootstrap 框架</h1> /36px
<h2>Bootstrap 框架</h2> /30px
<h3>Bootstrap 框架</h3> /24px
<h4>Bootstrap 框架</h4> /18px
<h5>Bootstrap 框架</h5> /14px
<h6>Bootstrap 框架</h6> /12px
Bootstrap 分别对 h1 ~ h6 进行了 CSS样式的重构，并且还支持普通内联元素定义 class=(.h1 ~ h6)来实现相同的功能。 内联元素使用标题字体：
<span class="h1">Bootstrap</span>
在 h1 ~ h6 元素之间，还可以嵌入一个 smal 元素作为副标题，在标题元素内插入 small元素
<h1>Bootstrap 框架 <small>Bootstrap 小标题</small></h1>
<h2>Bootstrap 框架 <small>Bootstrap 小标题</small></h2>
<h3>Bootstrap 框架 <small>Bootstrap 小标题</small></h3>
<h4>Bootstrap 框架 <small>Bootstrap 小标题</small></h4>
<h5>Bootstrap 框架 <small>Bootstrap 小标题</small></h5>
<h6>Bootstrap 框架 <small>Bootstrap 小标题</small></h6>
h1 ~ h3 下的 smal 为 23.4px、19.5px、15.6px；h4 ~ h6 下 smal 元素的大小只占父元素的 75% ,分别为：13.5px、10.5px、9px。在 h1 ~ h6 下的 smal 样式也进行了改变，颜色变成淡灰色：#7，行高为 1，粗度 为 40。
第三节 内联文本元素
添加标记，<mark>元素或.mark 类
<p>Bootstrap<mark>框架</mark></p>
各种加线条的文本
<del>Bootstrap 框架</del> /删除的文本
<s>Bootstrap 框架</s> /无用的文本
<ins>Bootstrap 框架</ins> /插入的文本
<u>Bootstrap 框架</u> /效果同上，下划线文本
各种强调的文本
<small>Bootstrap 框架</small> /标准字号的 85%
<strong>Bootstrap 框架</strong> /加粗 70
<em>Bootstrap 框架</em> /倾斜
第四节 对齐
设置文本对齐
<p class="text-left">Bootstrap 框架</p> /居左
<p class="text-center">Bootstrap 框架</p> /居中
<p class="text-right">Bootstrap 框架</p> /居右
<p class="text-justify">Bootstrap 框架</p> /两端对齐，支持度不佳
<p class="text-nowrap">Bootstrap 框架</p> /不换行
第五节 大小写
设置英文本大小写
<p class="text-lowercase">Bootstrap 框架</p> /小写
<p class="text-upercase">Bootstrap 框架</p> /大写
<p class="text-capitalize">Bootstrap 框架</p> /首字母大写
第六节 缩略语
缩略语
Bootstrap<abr tile="Bootstrap" class="intialism">框架</abr>
第七节 地址文本
设置地址，去掉了倾斜，设置了行高，底部 20px
<adres>
	<strong>Twiter, Inc.</strong><br>
	795 Folsom Ave, Suite 60<br>
	San Francisco, CA 94107<br>
	<abr tile="Phone">P:</abr>
	(123) 456-7890
</adres>
第八节 引用文本
默认样式引用，增加了做边线，设定了字体大小和内外边距
<blockquote>Bootstrap 框架</blockquote>
反向
<blockquote class="blockquote-revrse ">Bootstrap 框架</blockquote>
第九节 列表排版
移出默认样式
<ul class="list-unstyled">
    <li>Bootstrap 框架</li>
    <li>Bootstrap 框架</li>
    <li>Bootstrap 框架</li>
    <li>Bootstrap 框架</li>
    <li>Bootstrap 框架</li>
</ul>
设置成内联
<ul class="list-inline">
    <li>Bootstrap 框架</li>
    <li>Bootstrap 框架</li>
    <li>Bootstrap 框架</li>
    <li>Bootstrap 框架</li>
    <li>Bootstrap 框架</li>
</ul>
水平排列描述列表
<dl class="dl-horizontal">
	<dt>Bootstrap</dt>
	<dd>Bootstrap 提供了一些常规设计好的页面排版的样式供开发者使用。</dd>
</dl>
第十节 代码
内联代码
<code>&lt;section&gt;</code>
用户输入
pres <kbd>ctrl + ,</kbd>
代码块
<pre>&lt;p&gt;Please input.&lt;/p&gt;</pre>
Bootstrap 还列举了<var>表示标记变量，<samp>表示程序输出，只不过没有重新复写 CSS。


第三章 表格 按钮 表单 图片
第一节 表格
Bootstrap 提供了一些丰富的表格样式供开发者使用。
基本格式
<table class="table">
条纹状表格
让<tbody>里的行产生一行隔一行加单色背景效果
<table class="table table-striped">
带边框的表格
给表格增加边框
<table class="table table-borderd">
悬停鼠标
让<tbody>下的表格悬停鼠标实现背景效果
<table class="table table-hover">
状态类
可以单独设置每一行的背景样式
<tr class="success">
一共五种不同的样式可供选择。
样式	说明
active	鼠标悬停在行或单元格上
success	标识成功或积极的动作
info	标识普通的提示信息或动作
warning	标识警告或需要用户注意
danger	表示危险或潜在的带来负面影响的动作
隐藏某一行
<tr class="sr-only">
响应式表格
表格父元素设置响应式，小于 768px 出现边框
<body class="table-responsive">
第二节 按钮
基本
Bootstrap 提供了很多丰富按钮供开发者使用。可作为按钮使用的标签或元素转化成普通按钮
<a href="###" class="btn btn-default">Link</a>
<button class="btn btn-default">Button</button>
<input type="button" class="btn btn-default" value="input">
预定义样式
样式	说明
btn-default	默认样式
btn-success	成功样式
btn-info	一般信息样式
btn-warning	警告样式
btn-danger	危险样式
btn-primary	首选项样式
btn-link	链接样式
尺寸大小
从大到小的尺寸
<button class="btn btn-lg">Button</button>
<button class="btn">Button</button>
<button class="btn btn-sm">Button</button>
<button class="btn btn-xs">Button</button>
块级按钮
<button class="btn btn-block">Button</button>
<button class="btn btn-block">Button</button>
激活状态
<button class="btn active">Button</button>
禁用状态
<button class="btn active disabled">Button</button>
第三节 表单
基本格式
<form>
    <div class="form-group">
    	<label>电子邮件</label>
    	<input type="email" class="form-control" placeholder="请输入您的电子邮件">
    </div>
    <div class="form-group">
    	<label>密码</label>
    	<input type="password" class="form-control"  placeholder="请输入您的密码">
    </div>
</form>
内联表单
让表单左对齐浮动，并表现为 inline-block 内联块结构
<form class="form-inline">
注：当小于 768px，会恢复独占样式
表单合组
前后增加片段
<div class="input-group">
    <div class="input-group-addon">￥</div>
    <input type="text" class="form-control">
    <div class="input-group-addon">.00</div>
</div>
水平排列
让表单内的元素保持水平排列
<form class="form-horizontal">
    <div class="form-group">
        <label class="col-sm-2 control-label">电子邮件</label>
        <div class="col-sm-10">
            <input type="email" class="form-control" placeholder="请输入您的电子邮件">
        </div>
    </div>
</form>
注：这里用到了 col-sm 栅格系统，后面章节会重点讲解，而 control-label 表示和父元素样式同步。
复选框和单选框
设置复选框，在一行
<div class="checkbox">
	<label><input type="checkbox">体育</label>
</div>
<div class="checkbox">
	<label><input type="checkbox">音乐</label>
</div>

//设置禁用的复选框
<div class="checkbox disabled">
	<label><input type="checkbox" disabled>音乐</label>
</div>
//设置内联一行显示的复选框
<label class="checkbox-inline"><input type="checkbox">体育</label>
<label class="checkbox-inline disabled"><input type="checkbox" disabled>音乐</label>

//设置单选框
<div class="radio disabled">
	<label><input type="radio" name="sex" disabled>男</label>
</div>
下拉列表
设置下拉列表
<select class="form-control">
    <option>1</option>
    <option>2</option>
    <option>3</option>
    <option>4</option>
    <option>5</option>
</select>
校验状态
设置为错误状态
注：还有其他状态如下
样式	说明
has-error	错误状态
has-success	成功状态
has-warning	警告状态
 label 标签同步相应状态
<label class="control-label">Input with success</label>
添加额外的图标
文本框右侧内置文本图标
<div class="form-group has-feedback">
	<label>电子邮件</label><input type="email" class="form-control">
	<span class="glyphicon glyphicon-ok form-control-feedback"></span>
</div>
样式	说明
glyphicon-ok	成功状态
glyphicon-warning-sign	警告状态
glyphicon-remove	错误状态
控制尺寸
从大到小
<input type="password" class="form-control input-lg">
<input type="password" class="form-control">
<input type="password" class="form-control input-sm">
注：也可以设置父元素 form-group-lg、form-group-sm，来调整。
第四节 图片
三种形状
<img src="img/pic.png" alt="图片" class="img-rounded">
<img src="img/pic.png" alt="图片" class="img-circle">
<img src="img/pic.png" alt="图片" class="img-thumbnail">
响应式图片
<img src="img/pic.png" alt="图片" class="img-responsive">


第五章 辅助类和响应式工具
第一节 辅助类
Bootstrap 在布局方面提供了一些细小的辅组样式，用于文字颜色以及背景色的设置、显示关闭图标等等。
情景文本颜色
样式名	描述
text-muted	柔和灰
text-primary	主要蓝
text-success	成功绿
text-info	信息蓝
text-warning	警告黄
text-danger	危险红
 情景背景色
样式名	描述
bg-primary	主要蓝
bg-success	成功绿
bg-info	信息蓝
bg-warning	警告黄
bg-danger	危险红
 关闭按钮
<button type="button" class="close">&times;</button>
三角符号
<span class="caret"></span>
快速浮动
<div class="pull-left">左边</div>
<div class="pull-right">右边</div>
注：这个浮动其实就是 float，只不过使用了!important 加强了优先级。
块级居中
<div class="center-block">居中</div>
注：就是 margin:x auto；并且设置了 display:block;。
清理浮动
<div class="clearfix"></div>
注：这个div可以放在需要清理浮动区块的前面即可。
显示和隐藏
<div class="show">show</div>
<div class="hidden">hidden</div>
第二节 响应式工具
类	超小屏幕 手机(<768px)	小屏幕pad (>=768px)	中等屏幕 桌面（>=992px）	大屏幕 桌面（>=1200px）
.visible-xs-*	可见	隐藏	隐藏	隐藏
.visible-sm-*	隐藏	可见	隐藏	隐藏
.visible-md-*	隐藏	隐藏	可见	隐藏
.visible-lg-*	隐藏	隐藏	隐藏	可见
.hiddden=xs	隐藏	可见	可见	可见
.hidden-sm	可见	隐藏	可见	可见
.hidden-md	可见	可见	隐藏	可见
.hidden-lg	可见	可见	可见	隐藏
超小屏幕激活显示
<div class="visible-xs-block a">Bootstrap</div>
超小屏幕激活隐藏
<div class="hidden-xs a">Bootstrap</div>
 注：对于显示的内容，有三种变体，分别为：block、inline-block、inline。

第六章 组件
第一节 图标菜单和按钮组件
小图标组件
Bootstrap 提供了免费的 263 个小图标，具体可以参考中文官网的组件 链接：http://v3.bootcss.com/components/#glyphicons。可以使用<i>或<span>标签来配合使用，具体如下：
<i class="glyphicon glyphicon-star"></i>
<span class="glyphicon glyphicon-star"></span>

//也可以结合按钮
<button class="btn btn-default btn-lg">
	<span class="glyphicon glyphicon-star"></span>
</button>
<button class="btn btn-default btn">
	<span class="glyphicon glyphicon-star"></span>
</button>
<button class="btn btn-default btn-sm">
	<span class="glyphicon glyphicon-star"></span>
</button>
<button class="btn btn-default btn-xs">
	<span class="glyphicon glyphicon-star"></span>
</button>
下拉菜单组件
下拉菜单，就是点击一个元素或按钮，触发隐藏的列表显示出来
<div class="dropdown">
    <button class="btn btn-default" data-toggle="dropdown">
    	下拉菜单
    	<span class="caret"></span>
    </button>
    <ul class="dropdown-menu">
        <li><a href="#">首页</a></li>
        <li><a href="#">资讯</a></li>
        <li><a href="#">产品</a></li>
        <li><a href="#">关于</a></li>
    </ul>
</div>
按钮和菜单需要包裹在.dropdown 的容器里，而作为被点击的元素按钮需要设置data-toggle="dropdown"才能有效。对于菜单部分，设置 class="dropdown-menu"才能自动隐藏并添加固定样式。设置 class="caret"表示箭头，可上可下。
//设置向上触发
<div class="dropup">

//菜单项居右对齐，默认值是 dropdown-menu-left
<ul class="dropdown-menu dropdown-menu-right">

//设置菜单的标题，不要加超链接
<li class="dropdown-header">网站导航</li>
//设置菜单的分割线

<li class="divider"></li>

//设置菜单的禁用项
<li class="disabled"><a href="#">产品</a></li>

//让菜单默认显示
<div class="dropdown open">
按钮组组件
按钮组就是多个按钮集成在一个容器里形成独有的效果
<div class="btn-group">
    <button type="button" class="btn btn-default">左</button>
    <button type="button" class="btn btn-default">中</button>
    <button type="button" class="btn btn-default">右</button>
</div>

//将多个按钮组整合起来便于管理
<div class="btn-toolbar">
    <div class="btn-group">
        <button type="button" class="btn btn-default">左</button>
        <button type="button" class="btn btn-default">中</button>
        <button type="button" class="btn btn-default">右</button>
    </div>
    <div class="btn-group">
        <button type="button" class="btn btn-default">1</button>
        <button type="button" class="btn btn-default">2</button>
        <button type="button" class="btn btn-default">3</button>
    </div>
</div>

//设置按钮组大小
<div class="btn-group btn-group-lg">
<div class="btn-group">
<div class="btn-group btn-group-sm">
<div class="btn-group btn-group-xs">

//嵌套一个分组，比如下拉菜单
<div class="btn-group">
    <button type="button" class="btn btn-default">左</button>
    <button type="button" class="btn btn-default">中</button>
    <button type="button" class="btn btn-default">右</button>

    <div class="btn-group">
        <button class="btn btn-default dropdown-toggle" data-toggle="dropdown">
            下拉菜单<span class="caret"></span>
        </button>
        <ul class="dropdown-menu">
            <li><a href="#">首页</a></li>
            <li><a href="#">资讯</a></li>
            <li><a href="#">产品</a></li>
            <li><a href="#">关于</a></li>
        </ul>
    </div>
</div>
注意：这里<div>中并没有实现 class="dropdown"，通过源码分析知道嵌套本身已经 有定位就不需要再设置。而右边的圆角只要多加一个 class="dropdown-toggle"即可。 
设置按钮组垂直排列
<div class="btn-group-vertical">
设置两端对齐按钮组，使用标签
<div class="btn-group-justified">
    <a type="button" class="btn btn-default">左</a>
    <a type="button" class="btn btn-default">中</a>
    <a type="button" class="btn btn-default">右</a>
</div>

第二节 输入框和导航组件
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

第三节 路径分页标签和徽章组件
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
第四节 巨幕页头缩略图和警告框组件
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
第五节 进度条组件
进度条组件为当前工作流程或动作提供时时反馈。
//基本进度条
<div class="progress">
	<div class="progress-bar" style="width: 60%;">60%</div>
</div>

//最低值进度条
<div class="progress">
	<div class="progress-bar" style="min-width:20px">0%</div>
</div>

//结合情景的进度条
<div class="progress">
<div class="progress-bar progress-bar-success" style="min-width:20px;width:60%">60%</div>
</div>

//条纹状，IE10+支持
<div class="progress">
<div class="progress-bar progress-bar-success
progress-bar-striped" style="min-width:20px;width:60%">60%</div>
</div>

//动画效果
<div class="progress">
<div class="progress-bar progress-bar-success progress-bar-striped
active" style="min-width:20px;width:60%">60%</div>
</div>

//堆叠效果
<div class="progress">
<div class="progress-bar progress-bar-success"
style="min-width:20px;width:35%">35%</div>
<div class="progress-bar progress-bar-warning"
style="min-width:20px;width:20%">20%</div>
<div class="progress-bar progress-bar-danger"
style="min-width:20px;width:10%">10%</div>
</div>

第六节 列表组面板和嵌入组件
列表组组件
列表组组件用于显示一组列表的组件。
//基本实例
<ul class="list-group">
    <li class="list-group-item">1.这是起始</li>
    <li class="list-group-item">2.这是第二条数据</li>
    <li class="list-group-item">3.这是第三排信息</li>
    <li class="list-group-item">4.这是末尾</li>
</ul>
//列表项带勋章
<li class="list-group-item">1.这是起始<span class="badge">10</span></li>

//链接和首选
<div class="list-group">
    <a href="#" class="list-group-item active">1.这是起始<span class="badge">10</span></a>
    <a href="#" class="list-group-item">2.这是第二条数据</a>
    <a href="#" class="list-group-item">3.这是第三排信息</a>
    <a href="#" class="list-group-item">4.这是末尾</a>
</div>

//按钮式列表
<div class="list-group">
<button class="list-group-item active">1.这是起始 <span
class="badge">10</span></button>
<button class="list-group-item">2.这是第二条数据</button>
<button class="list-group-item">3.这是第三排信息</button>
<button class="list-group-item">4.这是末尾</button>
</div>
//设置项目被禁用
class="list-group-item disabled"

//情景类
<li class="list-group-item list-group-item-success">3.这是第三排信息</li>

//定制内容
<div class="list-group">
    <a href="#" class="list-group-item active">
        <h4>内容标题</h4>
        <p class="list-group-item-text">这里是相关内容详情！</p>
    </a>
    <a href="#" class="list-group-item">
        <h4>内容标题</h4>
        <p class="list-group-item-text">这里是相关内容详情！</p>
    </a>
    <a href="#" class="list-group-item">
        <h4>内容标题</h4>
        <p class="list-group-item-text">这里是相关内容详情！</p>
    </a>
</div>
面板组件
面板组件就是一个存放内容的容器组件。
//基本实例
<div class="panel panel-default">
	<div class="panel-body">这里是详细内容区！</div>
</div>

//带标题容器的面板
<div class="panel panel-default">
	<div class="panel-heading">面板标题</div>
	<div class="panel-body"></div>
</div>

//也可以设置标题元素
<div class="panel-heading">
	<h3 class="panel-title">面板标题</h3>
</div>

//带注脚的面板
<div class="panel-footer">这里是底部</div>

//情景效果：default、success、info、warning、danger、primary
<div class="panel panel-success">
	//表格类面板
    <div class="panel panel-default">
	<div class="panel-heading">表格标题</div>

    <div class="panel-body">   
        <p>这里是表格标题的详细内容！</p>
	</div>

     <table class="table">
        <tr><th>1</th><th>2</th><th>3</th></tr>
        <tr><td>1</td><td>2</td><td>3</td></tr>
	</table>
</div>

//列表类面板
<div class="panel panel-default">
<div class="panel-heading">表格标题</div>

<div class="panel-body"><p>这里是表格标题的详细内容！</p></div>
	<ul class="list-group">
		<li class="list-group-item">1.这里是首页</li>
		<li class="list-group-item">2.这里是第二个项目</li>
		<li class="list-group-item">3.这里是第三个项目</li>
		<li class="list-group-item">4.这里是第四个项目</li>
	</ul>
</div>

第七节 模态框插件
基本使用
使用模态框的弹窗组件需要三层 div 容器元素，分别为 modal(模态声明层)、dialog(窗口声明层)、content(内容层)。在内容层里面，还有三层，分别为 header(头部)、body(主体)、footer(注脚)。
//基本实例
<!-- 模态声明，show 表示显示 -->
<div class="modal show" tabindex="-1">
    <!-- 窗口声明 -->
    <div class="modal-dialog">
        <!-- 内容声明 -->
        <div class="modal-content">
            <!-- 头部 -->
            <div class="modal-header">
                <button type="button" class="close" data-dismiss="modal"><span>&times;</span></button>
                <h4 class="modal-title">会员登录</h4>
            </div>

            <!-- 主体 -->
            <div class="modal-body">
                <p>暂时无法登录会员</p>
            </div>

            <!-- 注脚 -->
            <div class="modal-footer">
                <button type="button" class="btn btn-default">注册</button>
                <button type="button" class="btn btn-primary">登录</button>
            </div>
        </div>
    </div>
</div>

<!--如果想让模态框自动隐藏，然后通过点击按钮弹窗，那么需要做如下操作。-->
<!--模态框去掉 show，增加一个 id-->

<div class="modal" id="myModal">
    <!--点击触发模态框显示-->
    <button class="btn btn-primary btn-lg" data-toggle="modal" data-target="#myModal">点击弹窗</button>
    弹窗的大小有三种，默认情况下是正常，还有 lg(大)和 sm(小)
    <div class="modal-dialog modal-lg">

        <div class="modal-dialog sm-lg">

        可设置淡入淡出效果
        <div class="modal fade" id="myModal">

        //在主体部分使用栅格系统中的流体
        <!-- 主体 -->
        <div class="modal-body">
            <div class="container-fluid">
                <div class="row">
                    <div class="col-md-4">1</div>
                    <div class="col-md-4">1</div>
                    <div class="col-md-4">1</div>
                </div>
            </div>
        </div>
     </div>
</div>

第八节 下拉菜单和滚动监听插件
下拉菜单
常规使用中，和组件方法一样，代码如下：
<div class="dropdown">
	<button class="btn btn-primary" data-toggle="dropdown">下拉菜单<span class="caret"></span></button>
    <ul class="dropdown-menu">
        <li><a href="#">首页</a></li>
        <li><a href="#">产品</a></li>
        <li><a href="#">资讯</a></li>
        <li><a href="#">关于</a></li>
    </ul>
</div>
声明式用法的关键核心：
•外围容器使用 class="dropdown"包裹；
•内部点击按钮事件绑定 data-toggle="dropdown"；
•菜单元素使用 class="dropdown-menu"。
•如果按钮在容器外部，可以通过 data-target 进行绑定。
滚动监听
滚动监听插件是用来根据滚动条所处在的位置自动更新导航项目，显示导航项目高亮显示。
第九节 标签页和工具提示插件
标签页
标签页也就是通常所说的选项卡功能。
//基本用法
<ul class="nav nav-tabs">
    <li class="active"><a href="#html5" data-toggle="tab">HTML5</a></li>
    <li><a href="#bootstrap" data-toggle="tab">Bootstrap</a></li>
    <li><a href="#jquery" data-toggle="tab">jQuery</a></li>
    <li><a href="#extjs" data-toggle="tab">ExtJS</a></li>
</ul>
<div class="tab-content" style="padding: 10px;">
    <div class="tab-pane active" id="html5">...</div>
    <div class="tab-pane" id="bootstrap">...</div>
    <div class="tab-pane" id="jquery">...</div>
    <div class="tab-pane" id="extjs">...</div>
</div>
使用 JavaScript，直接使用 tab 方法。
$('#nav a').on('click', function (e) {
    e.preventDefault();
    $(this).tab('show');
});
工具提示
工具提示就是通过鼠标移动选定在特定的元素上时，显示相关的提示语。
<a href="#" data-toggle="tooltip" title="超文本标识符">HTML5</a>
JS 部分需要声明
$('#section').tooltip();

第十节 弹出框和警告框插件
弹出框
弹出框即点击一个元素弹出一个包含标题和内容的容器。
<button class="btn btn-lg btn-danger" type="button" data-toggle="popover" title="弹出框"
data-content="这是一个弹出框插件">点击弹出/隐藏弹出框</button>
//JavaScript 初始化
$('button').popover();
警告框
警告框即为点击小时的信息框。
//基本实例
<div class="alert alert-warning">
    <button class="close" type="button" data-dismiss="alert">
    	<span>&times;</span>
    </button>
    <p>警告：您的浏览器不支持！</p>
</div>

//添加淡入淡出效果
<div class="alert alert-warning fade in">
如果用 JavaScript，可以代替 data-dismiss="alert"
JavaScript 方法
$('.close').on('click', function () {
	$('#alert').alert('close');
})

第十一节 按钮和折叠插件
按钮
可以通过按钮插件创建不同状态的按钮。
//单个切换。
<button class="btn btn-primary" data-toggle="button" autocomplete="off">单个切换</button>

//单选按钮
<div class="btn-group" data-toggle="buttons">
	<label for="" class="btn btn-primary active">
		<input type="radio" name="sex" autocomplete="off" checked> 男
	</label>
	<label for="" class="btn btn-primary">
		<input type="radio" name="sex" autocomplete="off"> 女
	</label>
</div>

//复选按钮
<div class="btn-group" data-toggle="buttons">
	<label for="" class="btn btn-primary active">
		<input type="checkbox" name="fa" autocomplete="off" checked>音乐
    </label>

    <label for="" class="btn btn-primary">
    	<input type="checkbox" name="fa" autocomplete="off"> 体育
    </label>

    <label for="" class="btn btn-primary">
   	 <input type="checkbox" name="fa" autocomplete="off"> 美术
    </label>

    <label for="" class="btn btn-primary">
    	<input type="checkbox" name="fa" autocomplete="off"> 电脑
    </label>
</div>

//加载状态
<button id="myButton" type="button" data-loading-text="Loading..." class="btn btn-primary" autocomplete="off">加载状态</button>
$('#myButton').on('click', function () {
    var btn = $(this).button('loading');
        setTimeout(function () {
        btn.button('reset');
    }, 1000);
});

//Button 插件中的 button 方法中有三个参数：toggle、reset、string(比如 loading、complete)。
//可代替 data-toggle="button"
$('button').on('click', function () {
	$(this).button('toggle');
})
折叠
通过点击可以折叠内容。
//基本实例
<button class="btn btn-primary" data-toggle="collapse" data-target="#content" Bootstrap</button>

<div class="collapse" id="content">
    <div class="well">
        Bootstrap 是 Twitter 推出的一个用于前端开发的开源工具包。它由
        Twitter 的设计师 Mark Otto 和 Jacob Thornton 合作开发,是一个 CSS/HTML 框架。目
        前,Bootstrap 最新版本为 3.0 。
    </div>
</div>

第十二节 轮播插件
轮播插件就是将几张同等大小的大图，按照顺序依次播放。
//基本实例。
<div id="myCarousel" class="carousel slide">
    <ol class="carousel-indicators">
        <li data-target="#myCarousel" data-slide-to="0"class="active"></li>
        <li data-target="#myCarousel" data-slide-to="1"></li>
        <li data-target="#myCarousel" data-slide-to="2"></li>
    </ol>

    <div class="carousel-inner">
        <div class="item active">
        	<img src="img/slide1.png" alt="第一张">
        </div>
        <div class="item">
        	<img src="img/slide2.png" alt="第二张">
        </div>

        <div class="item">
        	<img src="img/slide3.png" alt="第三张">
        </div>
    </div>
    <a href="#myCarousel" data-slide="prev" class="carousel-controlleft">&lsaquo;</a>
	<a href="#myCarousel" data-slide="next" class="carousel-controlright">&rsaquo;</a>
</div>
data 属性解释：
•data-slide 接受关键字 prev 或 next，用来改变幻灯片相对于当前位置的位置；
•data-slide-to 来向轮播底部创建一个原始滑动索引，data-slide-to="2"将把滑动块移动到一个特定的索引，索引从 0 开始计数。
•data-ride="carousel"属性用户标记轮播在页面加载时开始动画播放。
轮播插件有三个自定义属性：
属性名称	描述
data-interval	默认值 5000，幻灯片的等待时间(毫秒)。如果为false，轮播将不会自动开始循环。
data-pause	默认鼠标停留在幻灯片区域(hover)即暂停轮播，鼠标离开即启动轮播。
data-wrap	默认值 true，轮播是否持续循环。
如果在 JavaScript 调用就直接使用键值对方法，并去掉 data-；
//设置自定义属性
$('#myCarousel').carousel({
//设置自动播放/2 秒
interval : 2000,
//设置暂停按钮的事件
pause : 'hover',
//只播一次
wrap : false,
});
轮播插件还提供了一些方法，如下：
方法名称	描述
cycle	循环各帧(默认从左到右)
pause	停止轮播
number	轮播到指定的图片上(小标从 0 开始，类似数组)
prev	循环轮播到上一个项目
next	循环轮播到下一个项目
点击按钮执行
$('button').on('click', function () {
//点击后，自动播放
$('#myCarousel').carousel('cycle');
//其他雷同
}

第十三节 附加导航插件
附加导航即粘贴在屏幕某处实现锚点功能。
//基本实例。
<body data-spy="scroll" data-target="#myScrollspy">
    <div class="container">
        <div class="jumbotron" style="height:150px">
        	<h1>Bootstrap Affix</h1>
        </div>
        <div class="row">
            <div class="col-xs-3" id="myScrollspy">
                <ul class="nav nav-pills nav-stacked" data-spy="affix" data-offset-top="150">
                    <li class="active"><a href="#section-1">第一部分</a></li>
                    <li><a href="#section-2">第二部分</a></li>
                    <li><a href="#section-3">第三部分</a></li>
                    <li><a href="#section-4">第四部分</a></li>
                    <li><a href="#section-4">第五部分</a></li>
                </ul>
            </div>
            <div class="col-xs-9">
                <h2 id="section-1">第一部分</h2>
                <p>...</p>
                <h2 id="section-2">第二部分</h2>
                <p>...</p>
                <h2 id="section-3">第三部分</h2>
                <p>...</p>
                <h2 id="section-4">第四部分</h2>
                <p>...</p>
                <h2 id="section-5">第四部分</h2>
                <p>...</p>
            </div>
        </div>
    </div>
</div>
导航的 CSS 部分
ul.nav-pills {width: 200px;}
ul.nav-pills.affix{top: 30px;}
JavaScript 代替 data-spy="affix" data-offset-top="125"
$('#myAffix').affix({
    offset: {
    	top: 150
    }
})
```