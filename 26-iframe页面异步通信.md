iframe是HTML的一个标签，它的作用就是在页面中再开放出一个窗口，且这个窗口能够重新显示一个页面。

所以iframe称作页面内框架，可以理解为页面中的页面。

 JS操作iframe标签

Js操作iframe标签过程分为2步：

•找到iframe标签

•操作iframe标签

```js
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8">
        <title>Document</title>
    </head>
    <body>
        <h1>发布聊天内容：</h1>
        <iframe id="fr1" style="height:50px;"></iframe><br>
        姓名：<input type="text" id="namer" name="namer"><br>
        内容：<textarea id="content" name="content" style="height:50px;width:300px;"></textarea><br>
        <input type="button" value="发送" onclick="sendMessage();" />
    </body>
    <script type="text/javascript">
        function sendMessage() {
            //获取两个输入框中的值
            var n = document.getElementById('namer').value;
            var c = document.getElementById('content').value;
            //拼接url地址
            var urlStr = "do.php?namer=" + n + "&content=" + c;
            //把urlStr值赋给iframe的src属性
            document.getElementById('fr1').src = urlStr;
        }
    </script>
</html>
```

编写Js中调用的php文件，该php文件主要功能是将输入的内容打印打印出来，代码如下：
```js
<?php
$namer = $_GET['namer'];
$content = $_GET['content'];
var_dump($namer,$content);
```
在点击发送数据的时候并没有刷新整个页面，而是借助于iframe标签实现了页面的异步刷新。当然，我们也可以在点击发送的时候向服务器发送数据，并借助iframe实现页面异步刷新。

jQuery操作iframe标签

同Js一样，jQuery操作iframe标签过程也分为2步：

•找到iframe标签

•操作iframe标签
```
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8">
        <title>Document</title>
        <script src="https://code.jquery.com/jquery-3.4.0.min.js"></script>
    </head>
    <body>
        <h1>发布聊天内容：</h1>
        <iframe id="fr1" style="height:50px;"></iframe><br>
        姓名：<input type="text" id="namer" name="namer"><br>
        内容：<textarea id="content" name="content" style="height:200px;width:500px;"></textarea><br>
        <input type="button" value="发送" onclick="sendMessage();" />
    </body>
    <script type="text/javascript">
        function sendMessage () {
            //获取两个输入框中的值
            var n = $("[name='namer']").val();
            var c = $("[name='content']").val();
            //拼接url地址
            var urlStr = "do.php?namer=" + n + "&content=" + c;
            //把urlStr值赋给iframe的src属性
            $("#fr1").attr('src', urlStr)
        }
    </script>
</html>
```
然后编写Js中调用的php文件，
该php文件主要功能是将输入的内容插入到服务器的数据库中，
并返会插入成功的条目数。
```
<?php
$namer = $_GET['namer'];
$content = $_GET['content'];
$pdo = new PDO('mysql:host=localhost;dbname=php','root','123456');
$sql = "insert into token(namer,content,pubtime) value('".$namer."','".$content."',".time().")";
$re = $pdo->exec($sql);
var_dump($re);
```








