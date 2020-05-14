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

日期型

|类型		|字节	|范围																														|格式				|用途						|
|:---|:---|:---|:---|:---|
|date		|3		|1000-01-01---9999-12-31																									|YYYY-MM-DD			|日期值						|
|time		|3		|-838:59:59---838:59:59																										|HH:MM:SS			|时间值或持续时间			|
|year		|1		|1901---2155																												|YYYY				|年份值						|
|datetime	|8		|1000-01-01 00:00:00---9999-12-31 23:59:59																					|YYYY-MM-DD HH:MM:SS|混合日期和时间值			|
|timestamp	|4		|1970-01-01 00:00:00/2038结束时间是第 2147483647 秒，北京时间 2038-1-19 11:14:07，格林尼治时间 2038年1月19日 凌晨 03:14:07	|YYYYMMDD HHMMSS	|时间戳，混合日期和时间值	|

列举与枚举

|名称	|字节			|说明											|
|:---|:---|:---|
|set	|1、2、3、4或8	|列举：可以取SET列表中的一个或多个元素（多选）	|
|enum	|1或2			|枚举：可以取ENUM列表中的一个元素（单选）		|

```js
create table students(
  id tinyint, # 微小整型
  name varchar(10), #变长字符 
  sex enum('m','w'), #单选
  birthday date, # 日期型
  tel char(11), # 定长字符
  city char(1), # 城市
  hobby set('1','2','3','4'), #多选
  introduce	text # 个人介绍
 );
```

字段属性

|属性				|功能		|说明								|
|:---|:---|:---|
|not null			|非空		|必须有值，不允许为null								|
|default			|默认值		|当插入记录时没有赋值，自动赋予默认值（允许为null）	|
|primary key		|主键		|惟一标识一行数据的字段（主键自动为not null）		|
|auto_increment		|自动增量	|不能单独使用，必须与primary key 一起定义			|
|unique(unique key)	|唯一		|记录不能重复（一张表可以有多个unique，允许为null）	|


增删改查（简称：CURD）

增
```
# 方法1：指定字段
insert into students(name,age) values('张三','20');

# 方法2： 省略字段名，字段位要一一对应，不能跳过（auto_increment字段，可以使用null或 default）
insert into students values(null,'张三','20');

# 方法3：批量增加数据
insert into students(name,age) values('张三','20')，('李四','21')，('王五','22') ……
```
删
```
# 用delete删除记录，一定要加where条件，否则表数据全部删除！！
delete from 表名 where xx=xxx;

# 用truncate删除记录，不能加where条件，直接删除全部记录，id索引重新从1开始
truncate table 表名; 
```
改
```
#单条修改
update 表名 set xx=xx,xxx=xx where xxx=xxx and xxx=xxx;
#多条修改
update students
    set name = case id # id字段
        when 1 then 'zhangsan'
        when 2 then 'lisi'
        when 3 then 'wangwu'
        when 4 then 'zhaoliu'
    end,
    city = case id
        when 1 then '2'
        when 2 then '4'
        when 3 then '1'
        when 4 then '2'
    end
where id in (1,2,3,4);
```

SELECT 语句用于从表中选取数据。结果被存储在一个结果表中（称为结果集）

```js
# 当前使用的数据库
select database();

# 查看当前MySQL版本
select version();

# 查看当前用户 
select user();

# 查看运算结果
select 1+2;
```

from子句
```
# 字段用','隔开，至少有一个字段，最终结果集按照这个这个顺序显示
select 字段1,字段2... from 表名;

# *代表所有字段
select * from 表名;
```
•distinct(去重)
```
# 去重后的结果，distinct必须紧接着select后面
select distinct 字段 from 表名;

# 统计不重复的个数
select count(distinct 字段) from 表名;
```
where子句

•where子句适用于对记录的 删、改、查 操作

•对记录进行过滤，如果没有指定where子句，则显示所有记录

•在where表达式中，可以使用函数或运算符，运算符包括：

|类型		|运算符			|
|:---|:---|
|算术		|+ - * / %		|
|比较		|> < >= <= != =	|
|逻辑	|or |			| and && not !	|
|提升优先级	|( )			|

```
# 搜索id<20的所以数据
select * from students where id<20;

# 搜索id编号为偶数的数据
select * from students where id%2=0;
```
•where条件关键字
 in：查询一个集合的数据

```
# 搜索id在（1,3,7）之中的数据
select * from students where id=1 || id=3 || id=7;
select * from students where id in(1,3,7);

# 一次删除多条记录
delete from students where id=3 || id=15 || id=23;
delete from students where id in(3,15,23);
```

between...and... ：查询一个区间的数据
```
# 搜索id在20-40之间的数据
select * from students where id>20 && id<40;
select * from students where id between 20 and 40;

# 删除id在20-40之间的数据
delete from students where id between 20 and 40;
```
not：排除
```
# 搜索id除了20-40之间的数据
select * from students where id not between 30 and 40;
```

like子句
```
用于模糊查询 %：任意字符长度 _ ：一个字符长度
# 搜索name名字以5结尾的数据
select * from students where name like '张%';

# 搜索name名字包含字母s的数据
select * from students where name like '%二%';

# 搜索id以5结尾的两位数 数据
select * from students where id like '_5';
```
limit子句
```
控制查询记录条数，数据表中的记录，索引从0开始
select * from students limit 2 # 返回两条记录
select * from students limit 3,4 # 从索引为3的记录开始，返回4条记录

# php中的分页功能，偏移值的计算：（当前页-1） * 每页记录数
select name from student limit 4 offset 3
# 还可以使用offset（偏移）：从索引为3的记录开始，返回4条
```

group by(结果分组) 

根据给定数据列的每个成员对查询结果进行分组统计，最终得到一个分组汇总表
利用group by分组信息进行统计，常见的是配合max等聚合函数筛选数据后分析。

select指定的字段要么作为分组的依据（Group By语句的后面），要么就要被包含在聚合函数中。
```
#  简单分组
select sex from students group by sex;
+-----+
| sex |
+-----+
| m   |
| w   |
+-----+

# 聚合函数分组
select count(*),city from students group by city;
+----------+----------+
| count(*) | livecity |
+----------+----------+
|        7 |        1 |
|        8 |        2 |
|        1 |        3 |
|        3 |        4 |
|        2 |        5 |
+----------+----------+
```

order by(结果排序)

按照给定的字段进行排序，asc：升序(默认) desc：降序
如果同时选择多个字段，先按第一个字段排序，如果第一个字段值相等，再尝试第二个字段，以此类推
```
# 默认升序
select * from students order by birthday;

# 降序
select * from students order by birthday desc;
```
查询语句的书写顺序
```
select →字段→ from→表名→where→group by→order by→limit 
```
别名

```		
# 上图的语句中的where 语句还可以修改
select a.name,c.name,b.score from students as a,score as b,course as c where b.user_id=6 and b.course_id=4 and a.id=b.user_id and c.id=b.course_id;
```
			
表连接

有时为了得到完整的结果，我们需要从两个或更多的表中获取结果。我们就需要执行 join

# 内连接

•JOIN: 如果表中有至少一个匹配，则返回行
```
select a.*,b.name from students as a [inner] join city as b on a.livecity=b.id;
```
•LEFT JOIN: 即使右表中没有匹配，也从左表返回所有的行
```
select a.*,b.name from students as a left join city as b on a.livecity=b.id;
```
•RIGHT JOIN: 即使左表中没有匹配，也从右表返回所有的行
```
select a.*,b.name from students as a right join city as b on a.livecity=b.id;
```
•FULL JOIN: 只要其中一个表中存在匹配，就返回行（mysql 不支持）
```
# 带有连接的分组
select city.name, count(*) from students,city where students.livecity=city.id group by students.livecity；
+--------+----------+
| name   | count(*) |
+--------+----------+
| 北京   |        7 |
| 上海   |        8 |
| 杭州   |        1 |
| 深圳   |        3 |
+--------+----------+
```

子查询（subquery）是指出现在其他SQL语句内的select子句（嵌套在查询内部，且必须始终出现在圆括号内）
```
# 查找城市名称是北京的
# 普通方式查询
select * from students where livecity=1;

# 子查询方式
select * from students where livecity=(select id from city where name='北京');
```

•子查询可以包含多个关键字或条件，如：distinct、group by、order by、limit、函数等

•子查询的外层可以是：select，insert，update

视图是从一个或几个基本表（或视图）中导出的虚拟的表。在系统的数据字典中仅存放了视图的定义，不存放视图对应的数据。视图是原始数据库数据的一种变换，是查看表中数据的另外一种方式。可以将视图看成是一个移动的窗口，通过它可以看到感兴趣的数据。 视图是从一个或多个实际表中获得的，这些表的数据存放在数据库中。那些用于产生视图的表叫做该视图的基表。一个视图也可以从另一个视图中产生。
数据库中视图是一个重要的概念，其优势在于：

•安全：有的数据是需要保密的，如果直接把表给出来进行操作会造成泄密，那么可以通过创建视图把相应视图的权限给出来即可保证数据的安全。

•高效：复杂的连接查询，每次执行时效率比较低，建立视图，每次从视图中获取，将会提高效率。

•定制数据：将常用的字段放置在视图中。

创建视图
```
CREATE VIEW view_name AS SELECT column_name(s) FROM table_name WHERE condition;
```

其中，viewname为欲创建的视图名，columnname(s)为查询的列名，table_name为查询的表名，condition为查询条件。

修改视图

```
# ALTER语句：
ALTER VIEW view_name AS SELECT column_name(s) FROM table_name WHERE condition;
# CREATE OR REPLACE语句：
ALTER VIEW view_name AS SELECT column_name(s) FROM table_name WHERE condition;
```

删除视图
```
DROP view_name;
```
查询视图
```
SHOW TABLES;
SHOW TABLE STATUS;
```
这两个命令不仅可以显示表名及表信息，而且会显示出所有视图名称及视图信息。除此之外，使用SHOW CREATE VIEW命令可以查看某个视图的定义，格式如下：
```
SHOW CREATE VIEW view_name;
```
关系数据库表是用于存储和组织信息的数据结构,数据结构的不同，直接影响操作数据的效率和功能，对于MySQL来说，它提供了很多种类型的存储引擎，可以根据对数据处理的需求，选择不同的存储引擎，从而最大限度的利用MySQL强大的功能。

MyISAM引擎

MyISAM表是独立于操作系统的，这说明可以轻松地将其从Windows服务器移植到Linux服务器，建立一个MyISAM引擎的tb_Demo表，就会生成以下三个文件：
tbdemo.frm 存储表定义 tbdemo.MYD 存储数据 tb_demo.MYI 存储索引。

MyISAM无法处理事务，特别适合以下几种情况下使用：

选择密集型的表。MyISAM存储引擎在筛选大量数据时非常迅速，这是它最突出的优点。

2.插入密集型的表。MyISAM的并发插入特性允许同时选择和插入数据。例如：MyISAM存储引擎很适合管理邮件或Web服务器日志数据。

InnoDB引擎

InnoDB是一个健壮的事务型存储引擎，InnoDB还引入了外键约束，在以下场合下，使用InnoDB是最理想的选择：

1.更新密集的表。InnoDB存储引擎特别适合处理多重并发的更新请求。

2.事务。InnoDB存储引擎是支持事务的标准MySQL存储引擎。

3.外键约束。MySQL支持外键的存储引擎只有InnoDB。

4.自动灾难恢复。与其它存储引擎不同，InnoDB表能够自动从灾难中恢复。

事务处理

以银行转账业务为例，张三→李四转账100元，这是一个完整事务，需要两步操作：

1.张三数据表减去100元

2.李四数据表增加100元

如果在1步完成后，操作出现错误（断电、操作异常等），使2步没有完成，此时，张三减去了100元，而张三却没有收到100元

为了避免这种情况的发生，就将整个操作定义为一个事务，任何操作步骤出现错误，都会回滚到上一次断点位置，避免出现其他错误。

```js
# 开始
begin;
update tbl_a set money=money-100 where name='zhangsan';
update tbl_b set money=money+100 where name='lisi';

# 提交
commit;

# 回滚
rollback;
```

索引是帮助MySQL高效获取数据的数据结构

数据库在保存数据之外，还维护着满足特定查找算法的数据结构，这些数据结构以某种方式引用（指向）数据，这样就可以在这些数据结构上实现高级查找算法。这种数据结构，就是索引。索引可以大大提高MySQL的检索速度。

在MySQL中，对于一个Primary Key的列，MySQL已经自动对其建立了Unique和 Index。

```js
# 创建索引
create table 表名(  
id int not null,   
username varchar(16) not null,  
index(username(length))   ### 用username字段作为索引
);

# 显示索引
show index from 表名;  

# 删除索引
alter table 表名 drop index name;
```

约束保证数据的完整性和一致性，根据约束的字段数目的多少，约束又分为表级约束和列级约束

•列级约束：针对某一字段来使用

表级约束：针对两个或两个以上的字段使用

约束类型包括：

•not null(非空约束)

•primary key (主键约束)

•unique key (唯一约束)

•default (默认约束)

•foreign key(外键约束)

唯一(unique)约束

unique 约束唯一标识数据库表中的每条记录。

unique和primary key约束均为列提供了唯一性的保证。

primary key 被自动定义为unique 约束。

注意: 每个表可以有多个unique约束，但是每个表只能有一个primary key 约束。

```js
# 第一种方式
create table persons(
id_p int not null,
address varchar(255),
city varchar(255),
phone varchar(11) unique # 定义字段的同时，定义约束
);

# 第二种方式
create table persons(
id_p int not null,
address varchar(255),
city varchar(255),
phone varchar(11),
unique phone(phone) # 单独一行命令，定义约束
    
# 第三种方式
alter table persons add unique city(city); #修改表
```

默认(default)约束

用于约束对应列中的值的默认值（除非默认为空值，否则不可插入空值）

```js
create table persons(
id tinyint primary key auto_increment,
name varchar(30),
sex enum('m','w') default 'm', # 定义sex默认值为:'m'
)
```

主键(primary key)约束 

每张数据表只能存在一个主键，主键保证记录的唯一性，主键自动为not null（同时作为表的索引）。
```js
# 为没有主键的表添加主键
alter table 表名 add primary key (字段名)
```

外键(foreign key)约束

外键约束是为了保持数据一致性，完整性，实现一对一或一对多关系

•子表（具有外键列的表）和 父表（子表所参照的表），存储引擎只能为innoDB。

•外键列和参照列必须具有相似的数据类型。

– 如果是数字类型，数字的长度、是否有符号位 必须相同

– 字符类型的长度则可以不同

•外键列和参照列必须创建索引（如果外键列不存在索引的话，MySQL将自动创建索引）。

```js
# 先建父表 子表才能建外键  父表和子表必须都是innodb引擎

# city父表
create table city(
id tinyint primary key,
name varchar(10) not null
)engine=INNODB;

# students 子表
create table students(
id tinyint primary key auto_increment, #id
# 定义字段时同时定义
city tinyint,  # 外键字段类型要与主表相同
foreign key(city) references city(id),	 # city 字段作为外键 ，引用city表中的id 
)engine=INNODB;
-----------------------------------------------------------------------------
# 主表的数据可以修改，但不能删除
# 删除city中的记录     
delete from city where id=1;

# 创建外键以后，再删除city记录，就会报错：
ERROR 1451 (23000): Cannot delete or update a parent row: a foreign key constraint fails (`hxsd`.`students`, CONSTRAINT `students_ibfk_1` FOREIGN KEY (`city`) REFERENCES `city` (`id`))
```

删除约束

•删除primary key

alter table 表名 drop primary key;

•删除index

alter table 表名 drop index index_name;

•删除外键约束

alter table 表名 drop foreign key FK_ID;

索引与约束的关系

索引是面向数据库本身的，用于查询优化等操作。约束则更多的是业务上的关系。

通常，创建唯一约束就自动获取唯一索引，是因为数据库认为对数据库进行唯一检查时，如果该字段上有索引会很快，所以创建唯一约束就默认创建唯一索引。同样，常见的主键即是唯一性的约束，也是个索引。但对于not null 这样的约束，数据库是不会创建索引的。

分区

如果一张表的数据量太大，不仅查找数据的效率低下，而且难以找到一块集中的存储来存放。为了解决这个问题，数据库推出了分区的功能。

MySQL表分区主要有以下四种类型：

RANGE分区

 RANGE即范围分区，根据区间来判断位于哪个分区。这些区间要连续且不能相互重叠，使用VALUES LESS THAN操作符来进行定义。
 
 ```js
 create table test(
 id int DEFAULT null,
 name char(30),
 datedata date
 )
 PARTITION BY RANGE (year(datedata)) (
 PARTITION part1 VALUES LESS THAN (1990) ,
 PARTITION part2 VALUES LESS THAN (1995) ,  
 PARTITION part3 VALUES LESS THAN (2000) ,
 PARTITION part4 VALUES LESS THAN MAXVALUE );
 ```
 
 LIST分区
 
  LIST分区类似于按RANGE分区，区别在于LIST分区是基于列值匹配一个离散值集合中的某个值来进行选择。
  
  ```js
  create table test1(
  id int not null,
  name char(30),
  career VARCHAR(30)
  )
  PARTITION BY LIST (id) (
  PARTITION part0 VALUES IN (1,5) ,
  PARTITION part1 VALUES IN (11,15) ,
  PARTITION part2 VALUES IN (6,10) ,
  PARTITION part3 VALUES IN (16,20) 
  );
  ```
  
•HASH分区
  
 HASH分区基于用户定义的表达式返回值来选择分区，该表达式对要插入到表的行中列值进行Hash计算。
 
 ```js
 CREATE TABLE employees (
  id INT NOT NULL, 
 firstname VARCHAR(30), 
 lastname VARCHAR(30), 
 hired DATE NOT NULL DEFAULT '1970-01-01', 
 separated DATE NOT NULL DEFAULT '9999-12-31', 
 job_code INT, 
 store_id INT
 ) 
 PARTITION BY HASH(store_id) PARTITIONS 4;
 ```
 
 •KEY分区
 
 KEY分区类似HASH，但是HASH允许用户使用自定义表达式，而KEY分区不允许，它需要使用MySQL服务器提供的HASH函数，同时HASH分区只支持整数分区，而KEY分区支持除BLOB和TEXT类型外其他列。
 
 ```js
 CREATE TABLE tk ( 
 col1 INT NOT NULL, 
 col2 CHAR(5), 
 col3 DATE,
 PRIMARY KEY(col1)
 ) 
 PARTITION BY KEY (col1) PARTITIONS 3;
 ```
 
 存储过程、触发器
 
 存储过程
 
 存储过程（Stored Procedure）是一种在数据库中存储复杂程序，以便外部程序调用的一种数据库对象。
 
 存储过程是为了完成特定功能的SQL语句集，经编译创建并保存在数据库中，用户可通过指定存储过程的名字并给定参数(需要时)来调用执行。
 
存储过程思想上很简单，就是数据库 SQL 语言层面的代码封装与重用。

•优点

–存储过程可封装，并隐藏复杂的商业逻辑。

–存储过程可以回传值，并可以接受参数。

–存储过程无法使用 SELECT 指令来运行，因为它是子程序，与查看表，数据表或用户定义函数不同。

–存储过程可以用在数据检验，强制实行商业逻辑等。

•缺点

存储过程，往往定制化于特定的数据库上，因为支持的编程语言不同。当切换到其他厂商的数据库系统时，需要重写原有的存储过程。

存储过程的性能调校与撰写，受限于各种数据库系统。

存储过程的创建和调用

存储过程就是具有名字的一段代码，用来完成一个特定的功能

创建的存储过程保存在数据库的数据字典中

```js
create procedure 存储过程名称(in|out|inout 参数名称 参数类型,......)
begin
过程体;
end
```

实例

```js
create procedure getStudentCount()
begin
	select count(*) as num from student where classid=8;
end
```

查询、修改与删除

•查询

查看所有存储过程状态：
```
SHOW PROCEDURE STATUS;
```
查看对应数据库下所有存储过程状态：
```
SHOW PROCEDURE STATUS WHERE DB='数据库名';
```
查看名称包含Student的存储过程状态：
```
SHOW PROCEDURE STATUS WHERE name LIKE '%Student%';
```
查询存储过程详细代码：
```
SHOW CREATE PROCEDURE 过程名;
```
•修改
```
ALTER PROCEDURE 过程名 ([过程参数[,...]]) 过程体;
```
•删除
```
DROP PROCEDURE 过程名;
```
注意：不能在一个存储过程中删除另一个存储过程，只能调用另一个存储过程。

调用存储过程
MySQL存储过程用call和过程名以及一个括号，括号里面根据需要，加入参数，参数包括输入参数、输出参数、输入输出参数调用，格式如下：

```js
CALL存储过程名 ([过程参数[,...]])
```

触发器

触发器（trigger），也叫触发程序，是与表有关的命名数据库对象，是MySQL中提供给程序员来保证数据完整性的一种方法，它是与表事件INSET、UPDATE、DELETE相关的一种特殊的存储过程，它的执行是由事件来触发，比如当对一个表进行INSET、UPDATE、DELETE事件时就会激活它执行。因此，删除、新增或者修改操作可能都会激活触发器，所以不要编写过于复杂的触发器，也不要增加过多的触发器，这样会对数据的插入、修改或者删除带来比较严重的影响，同时也会带来可移植性差的后果，所以在设计触发器的时候一定要有所考虑。

创建触发器

```js
CREATE TRIGGER trigger_name trigger_time trigger_event ON tb_name FOR EACH ROW trigger_stmt
```

其创建触发器的参数说明如下表：

|参数			|说明																						|
|:---|:---|
|trigger_name	|标识触发器名称，由用户自行指定；															|
|trigger_time：	|标识触发时机，取值为 BEFORE 或 AFTER；														|
|trigger_event：|标识触发事件，取值为 INSERT、UPDATE 或 DELETE；											|
|tb_name：		|标识建立触发器的表名，即在哪张表上建立触发器；												|
|trigger_stmt：	|触发器程序体，可以是一句SQL语句，<br />或者用 BEGIN 和 END 包含的多条语句，与存储过程类似。|
|FOR EACH ROW	|表示任何一条记录上的操作满足触发事件都会触发该触发器。										|

触发事件类型介绍如下表所示

|事件			|描述																	|
|:---|:---|
|INSERT型触发器	|插入某一行时激活触发器，可能通过 INSERT、LOAD DATA、REPLACE 语句触发	|
|UPDATE型触发器	|更改某一行时激活触发器，可能通过 UPDATE 语句触发						|
|DELETE型触发器	|删除某一行时激活触发器，可能通过 DELETE、REPLACE 语句触发				|

我们想要使班级表中的班内学生数随着学生的添加自动更新，则采用触发器来实现最为合适，创建触发器如下：

```js
CREATE trigger tri_stuInsert after insert
on student for each row
BEGIN
	declare c int;
	set c = (select stuCount from class where classID=new.classID);
	update class set stuCount = c + 1 where classID = new.classID;
END
```

从需求我们可以得知，班内学生数的变化是在插入学生记录之后发生的，所以创建的触发器类型为after insert类型。

查看触发器
```
SHOW TRIGGERS;
```
删除触发器
```
DROP TRIGGER [IF EXISTS] trigger_name
```

触发器执行顺序

日常开发中创建的数据库通常都是 InnoDB 数据库，在数据库上建立的表大都是事务性表，也就是事务安全的，这时触发器的执行顺序主要是：

如果 BEFORE 类型的触发器执行失败，SQL 无法正确执行。

如果SQL 执行失败时，AFTER 类型的触发器不会触发。

如果AFTER 类型的触发器执行失败，数据会回滚。

如果是对数据库的非事务表进行操作，当触发器执行顺序中的任何一步执行出错，那么就无法回滚了，数据可能会出错。
