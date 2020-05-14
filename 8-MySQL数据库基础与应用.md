MYSQL函数

运算函数

•abs(x) : 返回x的绝对值

•floor(x) : 返回小于x的最大整数值

•round(x,y) : 返回参数x的四舍五入的有y位小数的值

•mod(x,y) : 返回x/y的模（余数）

•greatest(x1,x2,...,xn) : 返回集合中最大的值

•least(x1,x2,...,xn) : 返回集合中最小的值

字符串函数

•trim(str) :去除字符串首尾两端的空格

•upper(str) : 字符串转大写

•concat(s1,s2...,sn) : 将s1,s2...,sn连接成字符串

```js
# concat
insert into tbl_name values( concat('abc','def') );
```

日期函数

•year(date) : 返回日期date的年份(1000~9999)

•month(date) : 返回date的月份值(1~12)

•day(date)：返回date的日(1~31)

•curdate() : 返回当前的日期

•week(date) : 返回日期date为一年中第几周(0~53)

•now() : 返回当前的日期和时间

•curtime() : 返回当前的时间

•hour(time) : 返回time的小时值(0~23)

•minute(time) : 返回time的分钟值(0~59)

聚合函数

•count(col) : 统计记录的条数

•sum(col) : 求和

•avg(col) : 求平均值

•max(col): 求最大值

•min(col) : 求最小值

```js
# count 统计总记录数
select count(*) from tbl_name;

# sum 年龄总和
select sum(age) from tbl_name; 

# avg 平均年龄
select avg(age) from tbl_name; 

# 最大年龄
select min(birthday) from tbl_name;   # 日期最小的
```

FOUND_ROWS()
```
# FOUND_ROWS函数配合SQL_CALC_FOUND_ROWS 用于获取总记录数（忽略limit）

select SQL_CALC_FOUND_ROWS * from qa_list limit 3;
select FOUND_ROWS();
```

第一个sql里面的SQL_CALC_FOUND_ROWS不可省略，它表示需要取得结果数，也是后面使用FOUND_ROWS()函数的铺垫。

FOUND_ROWS()返回的结果是临时的。如果程序往后会用到这个数字，必须提前它保存在一个变量中待用。

FOUND_ROWS()与count()的区别：

当SQL限制条件太多时， count()的执行效率不是很高，最好使用FOUND_ROWS()

当SQL查询语句没有where等条件限制时，使用count()函数的执行效率较高。

数据库备份

使用Navicat可视化工具导入 导出数据，备份 恢复数据

备份数据

```js
mysqldump -u [用户名] -p [密码] [数据库名] > [path]/[名称].sql
```

恢复数据

```js
恢复数据
mysql>source c:\system.sql
```
