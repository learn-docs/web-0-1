php操作MySQL

MySQL

MySQL是一个关系型数据库数据系统， PHP+MySQL是最流行使用方法，当然，PHP也支持其他的数据库，如Mango，MangoDB，Microsoft SQL Server，Oracle OCI8，Sybase，DB++，PostgreSQL，Access，SQLite等

配置MySQL

在PHP中想要对MySQL数据库进行操作，需要使用mysqli扩展，这时候需要修改PHP的配置文件，打开php.ini，找到“;extension=mysqli”，将前面的分号去掉。修改好以后保存，重启Apache服务。

```
<?php
    $mysqli = new mysqli("localhost", "root", "123456");
    if ($mysqli) {
        echo "env mysql success";
    } else {
        echo "env mysql error";
    }
    $mysqli->close();
?>
```

 访问数据库
 
连接MySQL服务器

建立与MySQL数据库的连接，使用mysqli_connect()函数，它的语法格式如下：
```
mysqli mysqli_connect ([string server[, string username[, string password[, string dbname[, int port[, string socket]]]]]])
```
它的参数含义如下：

•server：可选参数，MySQL服务器地址。

•username：可选参数，MySQL服务器用户名。

•password：可选参数，MySQL服务器用户密码。

•dbname：可选参数，要连接的数据库名字。

•port：可选参数，MySQL服务器的端口号，默认3306。

•socket：可选参数，使用设置的socket或者pipe。

前四个参数比较常用，后两个很少用到。

选择MySQL数据库

PHP提供了mysqliselectdb()函数来选择MySQL数据库，它的语法格式如下：

```
<?php
    $server = "localhost";
    $username = "root";
    $password = "123456";
    $dbname = "php_db";

    // 快速写法
    $mysqli = new mysqli ( $server, $username, $password, $dbname );

    // 兼容写法
    $mysqli = new mysqli ( $server, $username, $password );
    mysqli_select_db ( $mysqli, $dbname );

    // 对象写法
    $mysqli = new mysqli ();
    $mysqli->connect ( $server, $username, $password );
    $mysqli->select_db ( $mysqli, $dbname );
?>
```

断开MySQL服务器

使用mysqli_close()函数来关闭与MySQL服务器的连接。

执行SQL语句

数据库的“增删改查”说到底都是一句SQL语句，PHP提供了mysqli_query()函数来执行SQL语句，它的语法如下：
```
mixed mysqli_query (mysqli link, string query[, int resultmode])
link : 是调用mysqli_connect()函数返回的mysqli对象，
query : 是要执行的SQL语句，
resultmode : 是可选参数，它的默认值是MYSQLISTORERESULT，如果需要查询的数据量很大，需要使用MYSQLIUSERESULT。
```

```
<?php
    $server = "localhost";
    $username = "root";
    $password = "123456";
    $dbname = "account_db";
    $mysqli = new mysqli ( $server, $username, $password, $dbname );

    // 增
    $result = mysqli_query ( $mysqli, "insert into account(username, password, email) values('张三', '123456', 'zhangsan@example.com')" );
    // 删
    $result = mysqli_query ( $mysqli, "delete from account where user='张三'" );
    // 改
    $result = mysqli_query ( $mysqli, "update account set password='abcdefg' where user='张三'" );
    // 查
    $result = mysqli_query ( $mysqli, "select * from account " );
    mysqli_close ( $mysqli );
?>
```

解析结果集

|面向对象						|面向过程			|说明						|
|:---|:---|:---|
|free() close() free_result()	|mysqlifreeresult()	|释放与结果集占用的内存		|
|fetch_row()					|mysqlifetchrow()	|以索引数组方式返回一行数据	|
|fetch_assoc()					|mysqlifetchassoc()	|以关联数组方式返回一行数据	|
|fetch_array()					|mysqlifetcharray()	|以数组的方式返回一行数据	|
|fetch_object()					|mysqlifetchobject()|以对象的方式返回一行数据	|
|data_seek()					|mysqlidataseek()	|移动结果集中的指针到任意行	|
|num_rows						|mysqlinumrows()	|获取结果集中行的数量		|


PDO（PHP Data Object）

PDO是PHP数据对象的英文缩写，英文全称为PHP Data Object，是又MySQL官方封装的、基于面向对象编程思想的、使用C语言开发的数据库抽象层。

配置PDO

Windows下启动PDO需要在“php.ini”文件中进行配置，添加扩展：
```
extension=php_pdo.dll
```
在最新版PHP中，PDO已经默认开启，只需要启动其他数据库扩展即可。配置好这些后重启Apache服务。执行phpinfo()函数，看到PDO配置项，说明开启成功。

访问数据库

与mysqli扩展类似，PDO扩展也是实例一个PDO对象，然后可以调用相关方法和属性来执行数据库的操作。

连接服务器

使用PDO与服务器建立连接，需要先使用构造方法来创建PDO实例，PDO的构造方法如下：
```
_construct(string data_source_name [,string user[,string pwd[,array driver_options]]])
datasourcename : 数据源，该参数包括了数据库名，主机名。MySQL数据库的DSN为：“mysql:host=localhost;dbname=account_db; port=3306”
user：数据库服务器用户名
pwd：为数据库服务器密码
```

数据库连接成功后，将返回一个PDO的实例，连接失败将会抛出一个PDOException异常，通常会使用try/catch语句进行处理。

关闭数据库

要想关闭连接，需要销毁对象以确保所有到它的引用都被删除，可以给变量赋一个NULL。

执行SQL语句

PDO提供了三种执行SQL语句的方法，分别是exec()，query()，预处理语句。

exec(）

exec()方法可以执行一条语句，并返回受影响的行数，它的语法格式如下：
```
int PDO::exec(String sql)
```
exec()方法通常用于insert into，delete，update等语句。
```
<?php
    echo "<pre>";
    $dbms = "mysql";
    $server = "localhost";
    $username = "root";
    $password = "123456";
    $dsn = "$dbms:host=$server";
    try {
        $pdo = new PDO ( $dsn, $username, $password );
        echo "PDO连接MySQL数据库服务器成功";
        print ($pdo->exec ( "create database account_pdo_db" )) ;
        print ($pdo->exec ( "use account_pdo_db" )) ;
        print ($pdo->exec ( "set names utf8" )) ;
        print ($pdo->exec ( "create table account(id int auto_increment primary key, username varchar(50) not null, password varchar(50) not null, email  varchar(50) not null)" )) ;
        print ($pdo->exec ( "insert into account(username, password, email) values ('Jack', '123456', 'jack@example.com')" )) ;
        print ($pdo->exec ( "insert into account(username, password, email) values ('Lucy', '123456', 'lucy@example.com')" )) ;
        $pdo = null;
    } catch ( PDOException $e ) {
        echo "PDO连接MySQL数据库服务器失败";
        die ();
    }
?>
```

query()

query()方法不同于exec()，通常用于select语句中，它的返回值是PDOStatement的实例，是POD里的结果集。它的语法如下：
```
PDOStatement PDO::query(String sql)
<?php
echo "<pre>";
$dbms = "mysql";
$server = "localhost";
$username = "root";
$password = "123456";
$dbname = "account_pdo_db";
$dsn = "$dbms:host=$server;dbname=$dbname";
try {
    $pdo = new PDO ( $dsn, $username, $password );
    echo "<p>PDO连接MySQL数据库服务器成功</p>";
    $result = $pdo->query ( "select * from account" );
    foreach ( $result as $row ) {
        var_dump ( $row );
    }
    $pdo = null;
} catch ( PDOException $e ) {
    echo "PDO连接MySQL数据库服务器失败";
    die ();
}
?>
```

预处理语句

PDO提供对预处理语句的支持。

预处理语句是预先将一个预处理的sql语句发送到数据库服务器，执行其他sql语句只是修改预处理语句里对应的参数。简单的说，就是将sql语句强制一分为二：第一部分为前面相同的命令和结构部分，第二部分为后面可变的数据部分。预处理语句，可以减轻数据库服务器压力。

定义预处理语句

使用prepare()方法执行sql预处理语句，得到一个PDOStatement实例，sql预处理语句通常有如下两种定义方式：

•命名参数：自定义的有意义的字符串作为命名参数，前面加上冒号。
```
insert into table_name(name,password,email) values(:name,:password,:email)
```
•问号数据占位符：使用“？”作为参数。
```
insert into table_name(name,password,email) values(?,?,?)
```
绑定参数

往预处理语句绑定参数有三种方法：

•bindParam()方法一个一个绑定，绑定完成执行execute()方法使之生效。

•bindValue()方法一个一个绑定，绑定完成执行execute()方法使之生效。

•直接使用execute()方法传递一个数组，命名参数使用关联数组，数据占位符使用索引数组。

```
<?php
    echo "<pre>";
    $dbms = "mysql";
    $server = "localhost";
    $username = "root";
    $password = "123456";
    $dbname = "account_pdo_db";
    $dsn = "$dbms:host=$server;dbname=$dbname";
    try {
        $pdo = new PDO ( $dsn, $username, $password );
        echo "PDO连接MySQL数据库服务器成功";

        // 数据占位符
        $pre = $pdo->prepare("insert into account(username, password, email) values (?,?,?)");
        $name = "Peter";
        $pwd = "333333";

        $pre->bindParam ( 1, $name );
        $pre->bindValue ( 2, $pwd );
        $pre->bindValue ( 3, "Peter@example.com" );
        $pre->execute ();

        $name = "张三";
        $pre->execute (array($name,"1245","zhangsan@example.com"));

        // 命名参数
        $pre = $pdo->prepare("insert into account(username, password, email) values (:name,:pwd,:email)" );
        $name = "老王";
        $pwd = "00544abc";
        $email = "laowang@example.com";
        $pre->bindParam ( ":name", $name );
        $pre->bindParam ( ":pwd", $pwd );
        $pre->bindParam ( ":email", $email );
        $pre->execute();
        $name = "柴科夫斯基";
        $pre->execute(array(":name"=>$name,":pwd"=>"love",":email"=>"abc@abc.com"));
        $pdo = null;
    } catch ( PDOException $e ) {
        echo "PDO连接MySQL数据库服务器失败";
        die();
    }
?>
```

解析结果集

PDO提供了三种方法来解析结果集

fetch()方法

从结果集中获取下一行的数据，返回的数组依赖于提取的类型，它的语法格式为：
```
array PDOStatement::fetch([int fetch_style[, int cursor_orientation[, int cursor_offset])
<?php
$dbms = "mysql";
$server = "localhost";
$username = "root";
$password = "123456";
$dbname = "account_pdo_db";
$dsn = "$dbms:host=$server;dbname=$dbname";
try {
    $pdo = new PDO ( $dsn, $username, $password );
    echo "<p>PDO连接MySQL数据库服务器成功</p>";
    $result = $pdo->query("select * from account");
    var_dump($result->fetch());
    var_dump($result->fetch(PDO::FETCH_ASSOC)); //返回索引为集列名的数组
    var_dump($result->fetch(PDO::FETCH_NUM)); //返回索引为数值的数组
    var_dump($result->fetch(PDO::FETCH_OBJ)); //返回属性名对应结果集的列表的匿名对象
    $pdo = null;
} catch ( PDOException $e ) {
    echo "<p>PDO连接MySQL数据库服务器失败</p>";
    die ();
}
?>
```
fetchAll()方法
```
fetchAll()方法可以返回一个包含结果集中所有行的数组，它的语法格式如下：
array PDOStatement::fetchAll([int $fetch_style[, mixed fetch_arg[, array ctor_arg]]])
<?php
$dbms = "mysql";
$server = "localhost";
$username = "root";
$password = "123456";
$dbname = "account_pdo_db";
$dsn = "$dbms:host=$server;dbname=$dbname";
try {
    $pdo = new PDO ( $dsn, $username, $password );
    echo "<p>PDO连接MySQL数据库服务器成功</p>";

    echo "<hr />";
    $result = $pdo->query ( "select * from account" );
    var_dump ( $result->fetchAll (PDO::FETCH_NUM) );

    echo "<hr />";
    $result = $pdo->query ( "select * from account" );
    var_dump ( $result->fetchAll ( PDO::FETCH_ASSOC ) );

    $pdo = null;
} catch ( PDOException $e ) {
    echo "<p>PDO连接MySQL数据库服务器失败</p>";
    die ();
}
?>
```

fetchColumn()方法

fetchColumn()方法用来从结果集中获取下一行中指定列的值。它的基本语法如下：

```
string PDOStatement::fetchColumn([int column_num])
//column_num是列的索引数字（从0开始），默认值为0，表示第一列    
<?php
$dbms = "mysql";
$server = "localhost";
$username = "root";
$password = "123456";
$dbname = "account_pdo_db";
$dsn = "$dbms:host=$server;dbname=$dbname";
try {
    $pdo = new PDO ( $dsn, $username, $password );
    echo "<p>PDO连接MySQL数据库服务器成功</p>";

    echo "<hr />";
    $result = $pdo->query ( "select * from account" );
    var_dump ( $result->fetchColumn());
    echo "<hr />";
    var_dump ( $result->fetchColumn(1));
    echo "<hr />";
    var_dump ( $result->fetchColumn(2));
    echo "<hr />";
    var_dump ( $result->fetchColumn(3));

    $pdo = null;
} catch ( PDOException $e ) {
    echo "<p>PDO连接MySQL数据库服务器失败</p>";
    die ();
}
?>
```

 SQL注入
 
SQL注入就是通过把SQL命令插入到Web表单提交或输入域名或页面请求的查询字符串，最终达到欺骗服务器执行恶意的SQL命令。SQL注入通常由于执行sql语句时，没有对用户通过Web表单提交的参数或者查询的字符串没有进行特殊字符过滤等，导致欺骗服务器执行恶意SQL命令。

为了防止这种情况，写脚本文件的时候，通常会考虑防止SQL注入，最简单的办法就是使用预处理语句，因为预处理语句事先已经编译了语句，传递的参数是不参与解释的。

PHP 的报错级别

|值		|常量				|描述													|
|:---|:---|:---|
|1		|E_ERROR			|致命的运行时错误。 错误无法恢复过来。脚本的执行被暂停	|
|2		|E_WARNING			|非致命的运行时错误。 脚本的执行不会停止				|
|4		|E_PARSE			|编译时分析错误。解析应该只由分析器生成的错误			|
|8		|E_NOTICE			|可能发现了一个错误										|
|16		|ECOREERROR			|在PHP启动时的致命错误									|
|32		|ECOREWARNING		|在PHP启动时的非致命错误								|
|64		|ECOMPILEERROR		|致命的编译时错误										|
|128	|ECOMPILEWARNING	|非致命编译时警告										|
|256	|EUSERERROR			|用户生成的致命错误										|
|512	|EUSERWARNING		|用户生成的非致命警告									|
|1024	|EUSERNOTICE		|用户生成的通知											|
|2048	|E_STRICT			|协同性或兼容性错误										|
|4096	|ERECOVERABLEERROR	|可捕获的致命错误										|
|8191	|E_ALL				|所有的错误和警告										|

$_SERVER参数

|参数							|说明																						|
|:---|:---|
|$SERVER['REMOTEPORT']			|端口																						|
|$SERVER['REMOTEADDR']			|浏览当前页面的用户的 IP 地址																|
|$SERVER['SERVERNAME']			|服务器主机的名称																			|
|$SERVER['SERVERADMIN']			|管理员信息																					|
|$SERVER['SERVERPORT']			|服务器所使用的端口																			|
|$SERVER['SERVERSIGNATURE']		|包含服务器版本和虚拟主机名的字符串															|
|$_SERVER['argv']				|传递给该脚本的参数																			|
|$_SERVER['argc']				|传递给程序的命令行参数的个数																|
|$SERVER['GATEWAYINTERFACE']	|CGI 规范的版本																				|
|$SERVER['SERVERSOFTWARE']		|服务器标识的字串																			|
|$SERVER['SERVERPROTOCOL']		|请求页面时通信协议的名称和版本 例如："HTTP/1.0"。											|
|$SERVER['REQUESTMETHOD']		|访问页面时的请求方法 例如："GET", "POST"													|
|$SERVER['QUERYSTRING']			|查询(query)的字符串																		|
|$SERVER['DOCUMENTROOT']		|当前运行脚本所在的文档根目录																|
|$SERVER['HTTPACCEPT']			|当前请求的 Accept: 头部的内容																|
|$SERVER['HTTPACCEPT_CHARSET']	|当前请求的 Accept-Charset: 头部的内容														|
|$SERVER['HTTPACCEPT_ENCODING']	|当前请求的 Accept-Encoding: 头部的内容														|
|$SERVER['HTTPCONNECTION']		|当前请求的 Connection: 头部的内容。例如：“Keep-Alive”									|
|$SERVER['HTTPHOST']			|当前请求的 Host: 头部的内容																|
|$SERVER['HTTPREFERER']			|链接到当前页面的前一页面的 URL 地址														|
|$SERVER['HTTPUSER_AGENT']		|当前请求的 User_Agent: 头部的内容															|
|$_SERVER['HTTPS']				|如果通过https访问,则被设为一个非空的值(on)，否则返回off									|
|$SERVER['SCRIPTFILENAME']		|当前执行脚本的绝对路径名																	|
|$SERVER['SCRIPTNAME']			|包含当前脚本的路径。这在页面需指向自己时非常有用											|
|$SERVER['PHPSELF']				|正在执行脚本的文件名																		|
|$SERVER['PHPAUTH_USER']		|当 PHP 运行在 Apache 模块方式下，并且正在使用 HTTP 认证功能，这个变量便是用户输入的用户名。|
|$SERVER['PHPAUTH_PW']			|当 PHP 运行在 Apache 模块方式下，并且正在使用 HTTP 认证功能，这个变量便是用户输入的密码	|
|$SERVER['AUTHTYPE']			|当 PHP 运行在 Apache 模块方式下，并且正在使用 HTTP 认证功能，这个变量便是认证的类型		|
|$SERVER['PATHTRANSLATED']		|当前脚本所在文件系统（不是文档根目录）的基本路径											|





