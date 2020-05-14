网络上的两个程序通过一个双向的通信连接实现数据的交换，这个连接的一端称为一个socket。socket（套接字）既不是程序，也不是协议，其只是操作系统提供的通信层的一组抽象API。

通信需要服务端和客户端组成：

服务端：

1.使用php初始化socket然后绑定一个端口，对端口进行监听。

2.调用accept阻塞，等待客户端连接。

客户端：

3.初始化一个socket，

4.连接服务器，如果连接成功，客户端与服务器端建立连接。

5.发送数据请求，服务器端接收请求并处理请求，把回应数据发送给客户端

6.读取数据

7.关闭连接，一次交互结束。

客户端------
服务端是可以彼此交互的应用程序。
客户端和服务端之间的交互需要连接。

Socket编程负责的就是为应用程序之间建立可进行交互的连接。

Socket通信是双向的、长连接，它提供了网络通信的一些接口，
我们基于这些接口可以控制数据的发送。

在一般情况下，服务器多用PHP来开发Socket通信，
客户端多用Javascript或者JQuery来开发Socket通信。


|服务器端函数					|说明															|
|:---|:---|
|socket_create(stream,$protocol)|创建Socket，参数：<br />stream：socket流<br />$protocol：协议	|
|socket_bind()					|绑定IP和端口													|
|socket_listen()				|监听端口														|
|socket_accept()				|接受一个socket连接，与客户端建立连接							|
|socket_read()					|读取客户端发送过来的数据										|
|socket_write()					|将数据写到 socket 缓存向客户端发送								|
|socket_close()					|关闭Socket连接													|
|客户端函数						|说明															|
|Websocket(wsurl)				|向服务器发送连接												|
|send(string)					|向服务器发送数据												|
|onmessage事件					|监听服务器发送过来的数据										|
|onclose事件					|监听服务器开关状态												|

Socket通信的工作原理

根据连接启动的方式以及本地套接字要连接的目标，
套接字之间的连接过程可以分为三个步骤：

•服务器监听：
是服务器端套接字并不定位具体的客户端套接字，
而是处于等待连接的状态，实时监控网络状态。

•客户端请求：
是指由客户端的套接字提出连接请求，
要连接的目标是服务器端的套接字。
为此，客户端的套接字必须首先描述它要连接的服务器的套接字，
指出服务器端套接字的地址和端口号，然后就向服务器端套接字提出连接请求。

•连接确认：
是指当服务器端套接字监听到或者说接收到客户端套接字的连接请求，
它就响应客户端套接字的请求，建立一个新的线程，
把服务器端套接字的描述发给客户端，
一旦客户端确认了此描述，连接就建立好了。
而服务器端套接字继续处于监听状态，继续接收其他客户端套接字的连接请求。

```js
服务器端
$ip = '127.0.0.1';
$port = 8001;//端口

//创建socket
$sock = socket_create(AF_INET,SOCK_STREAM,SOL_TCP）；
//参数：
//AF_INET： IPv4 网络协议。TCP 和 UDP 都可使用此协议。一般都用这个
//SOCK_STREAM:是基于TCP的，数据传输比较有保障   
//SOL_TCP:TCP 协议               

//绑定ip和端口                      
$ret = socket_bind($sock,$ip,$port)；

//监听                      
$ret = socket_listen($sock,4)； //最大监听套接字个数

$count = 0;
do {
    if (($msgsock = socket_accept($sock)) < 0) {
        echo "失败: ".socket_strerror($msgsock) ;
        break;
    } else {
        //发到客户端
        $msg ="测试成功！";
        socket_write($msgsock, $msg, strlen($msg));
        echo "测试成功了啊";

        $buf = socket_read($msgsock,8192);
        echo "收到的信息:{$buf}";

        if(++$count >= 5){
            break;
        }
    }
    socket_close($msgsock);
} while (true);

socket_close($sock);
客户端
$(function() {
	//连接Socket的URL地址
	var wsurl = "ws://127.0.0.1:8001/socket_server.php";
	var websocket; //用于存放客户端创建的Socket对象
	if (window.WebSocket) {
		websocket = new WebSocket(wsurl);
		websocket.onopen = function(event) {//onopen事件，连接成功
			$(body).append("<p>conneted success!</p>");
		}
		websocket.onmessage = function(event) {//onmessage事件，接收消息，显示在页面上
            var msg = JSON.parse(event.data);
            console.log(msg);
        }
	}
})
```


Socket通信实现聊天室

PHP实现Socket服务端

```js
Js实现Socket客户端
var ws = new WebSocket("ws://localhost:8080/msg");ws.onopen = function(evt)
{	console.log("Connection open ...");	ws.send("Hello WebSockets!");};ws.onmessage = function(evt)
{	console.log("Received Message: " + evt.data);	ws.close();};ws.onclose = function(evt)
{
console.log("Connection closed.");
};
```





