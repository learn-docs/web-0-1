PHP与Web页面交互是实现PHP网站与用户交互的重要手段。

在PHP中提供了两种与Web页面交互的方法，一种是通过Web表单提交数据，另一种是直接通过URL参数传递数据。

Web表单提交数据有两种方式：GET方法和POST方法。

POST方法不依赖于URL，不会将传递的参数值显示在地址栏中，而是将参数值放置在是HTTP包的包体中，这样可以传输更多的内容，传输方法也更加安全，所以POST方法通常用于上传信息。

GET方法完全依赖于URL，参数值会附在URL之后，以?分割URL和传输数据，多个参数用&连接，这样传输安全性很低，而且受到URL长度的限制，传输内容很小，所以GET方法通常用于获取信息。

Web表单用get方法提交数据，最终效果如同直接通过URL参数传递数据。

PHP针对这两种请求方法，提供了两个全局变量_GET[ ]，分别用来获取POST请求和GET请求的参数值。

$_GET[ ]

建立一个get请求的表单页面名叫form_get.html：
```
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8">
        <title>GET方式的表单</title>
    </head>
    <body>
        <form action="form_get.php" method="get">
            账户：<input name="username" type="text" /><br />
            密码：<input name="password" type="password" /><br />
            邮箱：<input name="email" type="email" /><br />
            <input type="submit" />
        </form>
    </body>
</html>
<?php
    echo "<pre>";
    var_dump ( $_GET );
    $username = $_GET ["username"];
    $password = $_GET ["password"];
    $email = $_GET ["email"];
    echo "<br />接收到的账户：" . $username;
    echo "<br />接收到的密码：" . $password;
    echo "<br />接收到的邮箱：" . $email;
?>
```

$_POST[ ]

同formget.html，我们建立一个名叫formpost.html，内容仅仅把<form>元素的action和method修改一下：
```
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8">
        <title>POST方式的表单</title>
    </head>
    <body>
        <form action="form_post.php" method="post">
            账户：<input name="username" type="text" /><br />
            密码：<input name="password" type="password" /><br />
            邮箱：<input name="email" type="email" /><br />
            <input type="submit" />
        </form>
    </body>
</html>
```
运行界面除了地址栏和标题栏，其他内容完全和formget.html一致。

这时候点击跳转到同目录下的formpost.php文件，文件内容为：
```
<?php
echo "<pre>";
var_dump ( $_POST );
$username = $_POST ["username"];
$password = $_POST ["password"];
$email = $_POST ["email"];
echo "<br />接收到的账户：" . $username;
echo "<br />接收到的密码：" . $password;
echo "<br />接收到的邮箱：" . $email;
?>
```


会话控制是一种跟踪用户的通信方式

例如：当一个用户在请求一个页面后，再次请求这个页面，
网站是无法知道这个用户刚才是否曾经来访问过。

由此我们就会觉得奇怪，平时我们在电商网站购物时，
只要我们在这个站点内，不论我们怎么跳转页面，
网站总会记得我是谁，这是怎么做到的呢？

这就是运用了HTTP会话控制。

在网站中跟踪一个变量，通过对变量的跟踪，使多个请求事物之间建立联系，根据授权和用户身份显示不同的内容、不同页面。

cookie

cookie是在服务器端创建，并写回到客户端浏览器

浏览器接到指令则在本地临时文件夹中创建了一个cookie文件，
其中保存了你的cookie内容

客户端浏览器每次访问网站时，
都会检测是否有该网站的cookie信息，如果有的话，也会同时发送过去。

注意：

cookie内容的存储是键/值对的方式，键和值都只能是字符串。

|函数								|功能					|
|:---|:---|
|setcookie( key , value ,有效期 )	|设置会话 cookie 参数	|

```js
//定义cookie
//setcookie(键, 值, 有效期(秒))
setcookie("name","zhangsan",time()+1000); //如果不设置有效期，关闭浏览器就会消失
setcookie("pwd","123",time()+1000);

//删除cookie（设定过期时间，使失效）
setcookie("name","",time()-1);
setcookie('age',null,time()-1);
setcookie('sex',"",time()-1);
```

session与cookie相似，只是原来将信息存在客户端，现在保存到服务端

客户端第一次访问时将信息保存到服务器，
同时分配给用户一个固定长度的字符串（sessionID），
并以cookie方式保存在客户端

在php.ini配置文件中，可以指定这个sessionID的名称：
```
session.name = PHPSESSID
```

```js
//开启session 要保证在它之前，没有向浏览器输出过任何内容,通常放在代码第一行
session_start();

//往session中存储信息
$_SESSION['name'] = '张三';
$_SESSION['sex'] = '男';
$_SESSION['age'] = 18;

//获取session信息
$name=$_SESSION['name'];

//销毁session中的信息
unset($_SESSION);

//销毁session文件
session_destroy();

//销毁客户端cookie信息
setcookie('PHPSESSID','',time()-1);   
```

cookie与session的区别

|区别		|cookie							|session				|
|:---|:---|:---|
|存放位置	|客户端							|服务器端				|
|安全性		|不够安全						|安全					|
|资源占用	|存放在客户端，不占服务器资源	|占服务器资源			|
|生命周期	|固定时长						|每次访问，重新计算时长	|
|文件大小	|4k								|不限制					|

建议将登陆信息等重要信息存放为session，其他信息如果需要保留，可以放在cookie中
