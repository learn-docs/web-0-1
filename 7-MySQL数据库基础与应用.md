Michael Widenius "Monty"是一位编程天才。

19 岁的时候，他从赫尔辛基理工大学辍学开始全职工作，因为大学已经没有什么东西可以教他了。33 岁时，他发布了 MySQL，成为了全世界最流行的开源数据库。并以10亿美元的价格，将自己创建的公司MySQL AB卖给了SUN，此后，Oracle收购了SUN。

Widenius离开了Sun之后，觉得依靠Sun/Oracle来发展MySQL，实在很不靠谱，于是决定另开分支，这个分支的名字叫做MariaDB。MariaDB名称来自他的女儿Maria的名字。

MariaDB跟MySQL在绝大多数方面是兼容的，对于开发者来说，几乎感觉不到任何不同。目前MariaDB是发展最快的MySQL分支版本，新版本发布速度已经超过了Oracle官方的MySQL版本。

关系型数据库以行和列的形式存储数据，这一系列的行和列被称为表，一组表组成了数据库。
表与表之间的数据记录有关系。

数据保存在表内，行（记录）用于记录数据，列（字段）用于规定数据格式

查看数据库

```
show databases;
```

创建数据库

# 如果没有修改my.ini配置文件的默认字符集，在创建数据库时，指定字符集

```
create database db_name character set 'utf8';
```

# 特殊字符(关键字)用反引号

```
create database `create`;
```

MySQL\data目录下将自动生成一个对应名称的目录，目录内部有一个db.opt文件

显示数据库创建信息

```
show create database db_name;
```

删除数据库

```
drop database db_name;
```

进入（使用）数据库

```
use database;
```

显示当前打开的数据库

```
select database();
```

创建数据表

```
create table 表名(字段 字段类型,....)
```

MySQL\data目录下的数据库目录中将自动生成一个对应名称的.frm文件

删除数据表

```
drop table 表名;
```

查看数据表

```
show tables；
```

# 查看字母是'abc'开头的表

示例

```
show tables like 'abc%';  # %是通配符
```

查看表创建信息

```
show create table 表名;
```

查看数据表结构
```
desc 表名;
```

登录

Mysql是基于C/S架构，必须在客户端通过终端窗口，连接MySQL服务器，进行操作。

```
 mysql -h host -u user -p
 Enter password: ********
```

用户管理

•超级用户 root
•修改账号密码，例：

```
## DOS命令下修改，将root账号密码修改为1234
mysqladmin -u root password 1234   ##语句最后不要加分号，否则密码就是 “1234；”

##mysql命令
set password for 'root'@'localhost'= password('1234');
```

•创建用户

使用create语句进行创建用户，语句格式如下：

```
create user 'username'@'host' identified by 'password';
```

其中：username表示要创建的用户名；
host表示指定该用户在哪个主机上可以登陆，
如果是本地用户可用localhost，
如果想让该用户可以从任意远程主机登陆，可以使用通配符%；
password表示该用户的登陆密码，密码可以为空，
如果为空则该用户可以不需要密码登陆服务器。
例：
```
create user 'zhangsan'@'localhost' identified by '123456';
```

•删除用户

删除用户使用drop语句，语句格式如下：
```
drop user 'username'@'host';
```

修改配置文件my.ini

字符集

MySQL默认字符集是latin( 拉丁 )，改变为utf8才能正确显示中文
```
[mysqld] 下添加
character-set-server=utf8
init-connect='\set NAMES utf8'
```

修改默认引擎

InnoDB优于MYISAM
```
default-storage-engine=MYISAM 修改为 default-storage-engine=InnoDB
```
个性化mysql提示符

MySQL默认提示符是” mysql>“ ，可以个性化定制，例如："mysql(数据库)>"
```
[mysql]下添加
prompt="mysql(\d)>"
```

•information_schema

 提供了访问数据库元数据的方式。什么是元数据呢？元数据是关于数据的数据，如数据库名或表名，列的数据类型，或访问权限等。有些时候用于表述该信息的其他术语包括“数据词典”和“系统目录”。

•performance_schema

 mysql 5.5 版本 新增了一个性能优化的引擎
 
•mysql

这个是MySQL的核心数据库，主要负责存储数据库的用户、权限设置、关键字等MySQL自己需要使用的控制和管理信息。不可以删除，也不要轻易修改这个数据库里面的表信息。

•test

安装时候创建的一个测试用数据库，空数据库，没有任何表，可以删除（新版mysql已取消）。

SQL语言

SQL(Structured Query Language)是用于访问和处理数据库的标准计算机语言。使用 SQL 访问和处理数据系统中的数据，这类数据库包括：Oracle,mysql,Sybase, SQL Server, DB2, Access 等等。

基本规范

•SQL 对大小写不敏感，一般数据库名称、表名称、字段名称全部小写

•MySQL要求在每条 SQL 命令的末端使用分号（MS Access 和 SQL Server 2000，则不必在每条 SQL 语句之后使用分号）。

注释
```js
mysql> select 1+1;     # 这个注释直到该行结束
mysql> select 1+1;     -- 这个注释直到该行结束
mysql> select 1  /* 这是一个在行中间的注释 */ + 1;
mysql> select 1+
/*
这是一个
多行注释的形式
*/
1;
```

字段类型

数据类型是指列、存储过程参数、表达式和局部变量的数据特征，它决定了数据的存储方式，代表了不同的信息类型。不同的数据库，数据类型有所不同，MySQL数据库有以下几种数据类型：

•字符串型
|类型		|字节	|大小						|说明	|
|:---|:---|:---|:---|
|char		|1		|0-255字符 (2^8)			|定长字符串						|
|varchar	|2		|0-65 535字符 (2^16)		|变长字符串						|
|tinytext	|1		|0-255字符 (2^8)			|短文本（与char存储形式不同）	|
|text		|2		|0-65 535字符(2^16)			|文本							|
|mediumtext	|3		|0-16 777 215字符 (2^24)	|中等长度文本					|
|longtext	|4		|0-4 294 967 295字符 (2^32)	|极大文本						|

注意：char和varchar需要指定长度，例如：char（10）

整数型

|类型			|字节	|范围（有符号）											|范围（无符号）					|用途			|
|:---|:---|:---|:---|
|tinyint		|1		|(-128，127)											|(0，255)						|很小整数值		|
|smallint		|2		|(-32 768，32 767)										|(0，65 535)					|小整数值		|
|mediumint		|3		|(-8 388 608，8 388 607)								|(0，16 777 215)				|中整数值		|
|int或integer	|4		|(-2 147 483 648，2 147 483 647)						|(0，4 294 967 295)				|整数值			|
|bigint			|8		|(-9 233 372 036 854 775 808，9 223 372 036 854 775 807)|(0，18 446 744 073 709 551 615)|很大的整数值	|

很多人喜欢在定义数据时，这样写：
```js
create table tbl_name(
age int(10)
);
```

int后面()中的数字，不代表占用空间容量。而代表最小显示位数。这个东西基本没有意义，除非你对字段指定zerofill。mysql会自动分配长度：int(11)、tinyint(4)、smallint(6)、mediumint(9)、bigint(20)。所以，建议在使用时，就用这些默认的显示长度就可以了。不用再去自己填长度（比如：int(10)、tinyint(1)之类的基本没用）。

浮点型

|类型			|字节	|范围							|用途												|
|:---|:---|:---|:---|
|float(M,D)		|4		|23bit（约6~7位 10进制数字）	|单精度浮点数<br />值绝对能保证精度为6~7位有效数字	|
|double(M,D)	|8		|52bit（约15~16位 10进制数字）	|双精度浮点数值<br />精度为15~16位有效数字			|
|decimal(M,D)	|M+2	|依赖于M和D的值					|定点型												|

M（精度），代表总长度（整数位和小数位）限制
D（标度），代表小数位的长度限制。
M必需大于等于D

|数字的修饰符	|功能	|说明							|
|:---|:---|:---|
|unsigned		|无符号	|非负数							|
|zerofill		|前导 0	|整形前加0（自动添加unsigned）	|







