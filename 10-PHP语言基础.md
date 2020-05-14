文件命名

•文件后缀名为 php

•文件名中不可包含中文、空格、特殊符号

•建议使用有意义的英文单词命名
```
语言标记
//标准风格
<?php
	.......
?>
```
注意：纯php脚本文件要求：，1. 开始标签要在第一行顶头写，2. 删除结束标签。
```
php标签之外是html语言环境，
在纯php代码环境下，这些html字符
（包括看不见的空格或者回车，制表符号）
也会一同输出，引发意外错误。
因此，在编码规范中规定：
库文件、class类文件等只要是纯php代码的文件，要删除结尾的 ?> 结束标签。
```

```js
<!DOCTYPE html>
<html>
	<body>
		<button>ajax异步请求</button>
	</body>
</html>
<script src="jquery-1.11.3.min.js"></script>
<script>
	$("button").click(function(){
		$.get("doAction.php",function(data){
			alert(data? "ok":"no");
		})
	})
</script>
<?php
	echo false; //输出:""
?>
//结束标签后有空格，输出：" "
//所以要删除php的结束标签
```

注释符与结束符
```
//单行注释
/*多行注释*/

//结束符使用英文分号 “;”
$hello="hello world";
```

常用命令和系统函数

 echo输出 : 只能输出字符串、数字、布尔（true:1 false:空）类型的数据
 
```js
<?php
    $hello="hello world";
	echo "<h1>{$hello}</h1>";
?>

//快速输出----------------------------------------------------
<h1><?= $hello ?></h1> //相当于 <?php echo $hello ?>
```

•var_dump()

此函数显示一个或多个表达式的结构信息，包括表达式的类型与值。数组将递归展开值，通过缩进显示其结构

注意： var_dump中的变量必须是存在的，如果变量存在但值是空，则返回false 没有变量时，则返回NULL 该函数有输出的功能，因此不必加其它的输出函数

•require与include

require

 常用于引入重要文件，若引入失败会直接影响到当前整个脚本，引入失败报 Error错误
 
include

 常用于引入普通文件，若引入失败不会对当前脚本有较大的影响，引入失败报 Warning错误
 
require_once

 避免重复引入，其他规则同require
 
include_once

 避免重复引入，其他规则同include

•header

用于定义 HTTP协议头信息。

变量与常量

变量

•声明变量：$

•命名规则：字母数字下划线、首字母不能为数字、严格区分大小写、且不能使用关键字！推荐驼峰命名法

•变量销毁：unset(变量名)，被销毁的变量在内存中被释放

•引用变量

```js
//变量引用：用不同的名字访问同一个变量内容
$man="zhangsan";
$student=&$man; //用&符号引用
var_dump($man===$student);//true
```

常量

使用define关键字定义常量，常量命名要全部大写，常量的数据类型不能是 资源、对象

```js
//定义常量
define("SCHOOL","清华大学");

//判断常量
var_dump( defined("SCHOOL") );  //true
```

变量与常量的差异

|差异		|变量					|常量					|
|:---|:---|:---|
|定义		|$声明					|define()函数定义		|
|命名		|大小写敏感				|必须大写（行业规范）	|
|赋值		|可以重新赋值			|不能再赋值				|
|数据类型	|8种数据类型			|只能是标量				|
|销毁		|unset() 销毁			|不能销毁				|
|判断方法	|isset() 判断是否定义	|defined() 判断是否定义	|
|作用域		|局部作用域				|全局作用域				|


数据类型

八种数据类型

•四种标量类型

–布尔型（boolean）

–整 型（integer）范围：2^32或2^64（超出自动转换为浮点型）

–浮点型（float）范围：双精度

–字符串（string）

•两种复合类型

–数组型（array）

–对象型（object）

•两种特殊类型

–资源型（resource）

–空 型（null）


不同进制
```
$number1 = 0b10;	//0b开头 二进制 结果:2
$number2 = 0123;	//0开头 八进制 结果:83
$number3 = 0x123;	//0X开头 十六进制 结果:291
```

对象型

具有一定功能和特征的单个事物，对象是属性和方法的集合

资源型

变量可以是文件夹、一个文件、从数据库中得到的结果集等，
操作这个变量，相当于操作这些资源。

NULL型

null也是数据，通常表示一种状态，变量没有任何值，就用null表示。以下情况会得到null：

•直接将一个变量赋值为null

•将一个变量销毁后再次使用该变量

•直接使用一个不存在的变量

数据类型转换

自动类型转换

在特殊运算时，会有自动类型转换的情况

|自动转换为： false			|自动转换为： true	|自动转换为： int	|自动转换为： string|
|:---|:---|:---|:---|
|整型： 0					|非0整数			|true : 1			|true : "1"			|
|浮点： 0.0或0.00			|非0浮点数			|false : 0			|false : " "		|
|字符串： " " 或 "0"		|非空字符串			|null: 0			|null: " "			|
|数组：空数组				|非空数组			|					|					|
|null						|对象				|					|					|
|未知变量（或被销毁变量）	|					|					|					|

强制类型转换

改变原变量类型

 使用 settype() 函数可以将一个指定变量强制转换为另一种指定类型
 
不改变原变量类型

 格式：新变量 = (指定变量类型) 原变量;

```js
//强制类型转换：不改变原变量类型
//定义一个存储变量
$old = 1;
$new;	//用于接收转换之后的变量

//开始转换
$new = (Boolean) $old;	//true
$new = (Integer) $old;	//1
$new = (Float) $old;	//float 1
$new = (String) $old;	//"1"
$new = (Array) $old;	//Array
$new = (Object) $sum;	//Object
```

常用变量检测函数

|函数		|说明																																							|
|:---|:---|
|gettype()	|判断变量类型：<br />返回 boolean、integer、double（ float 返回 “double”）、string、array、object、resource、null、unknown type								|
|isset()	|检测变量是否存在																																				|
|empty()	|判断一个变量是否为空（字符串、数组、0、null）																													|
|其他		|判断变量类型的系列函数<br />isarray()、isbool()、isfloat()、isinteger()、isnull()、isnumeric()、isobject()、isresource()、 isstring() 和 isscalar()是否为标量	|

常用数学运算函数

|函数名	|语法									|说明												|
|:---|:---|:---|
|rand	|rand([int, int])						|返回一个随机整数									|
|mt_rand|mt_rand ([int, int])					|使用Mersenne Twister算法返回随机整数				|
|abs	|abs (mixe)								|返回数字的绝对值									|
|min	|min(array) min(mixed, mixed [, …] )	|返回最小值											|
|max	|max (array) max(mixed, mixed [, …] )	|返回最大值											|
|round	|round (float [, int [, int]])			|四舍五入											|
|floor	|floor (float)							|舍去小数部分取整									|
|ceil	|ceil ( float)							|小数部分非零返回整数部分就加1						|
|pow	|pow(mixed, mixed)						|返回base的exp次方的值								|
|sqrt	|sqrt (float)							|返回平方根											|
|sin	|sin (float)							|返回正弦值											|
|cos	|cos (float)							|返回余弦值											|
|tan	|tan (float)							|返回正切值											|
|deg2rad|deg2rad (float)						|将角度转换为弧度									|
|bindec	|bindec (string)						|二进制转十进制										|
|decbin	|decbin (int)							|十进制转二进制										|
|octdec	|octdec (string)						|八进制转十进制										|
|decoct	|decoct (int)							|十进制转八进制										|
|hexdec	|hexdec (string)						|十六进制转十进制									|
|dechex	|dechex (int)							|十进制转十六进制									|
|exp	|float exp(float arg)					|返回e的arg幂次值，e为自然对数的底数，值为2.718282。|
|pi		|float pi (void)						|返回圆周率的值										|

字符串

三种定义方式

|单引号						|双引号								|定界符					|
|:---|:---|:---|
|不支持解析变量				|支持解析变量，不支持表达式			|同双引号				|
|不能插入单引号				|不能插入双引号						|可以插入双引号和单引号	|
|只能转义 反斜杠 和 单引号	|支持解析转义字符(\n、\t、\s 等）	|同双引号				|

```js
$num=10;

//单引号
$title='hxsd'.$num.'beijing';

//双引号 支持解析变量，不能解析表达式,例如：{$hxsd+1}
$school ="<div id='box'>
	<h1>{$hxsd}</h1>
</div>";

//定界符（可以任意取名）
$str2 = <<<mark
<div id='box'>
	<h1 class="main">{$hxsd}</h1>
</div>
mark;

//注意：---------------------------------------------------------
//定界符中可以使用单、双引号，可以解析变量
//定界符中的字符串，会保留所有格式，包括各种空格（尽量顶格写，避免开始的空格）
//结束标记一定要顶格写
//开始、结束标记（上面代码中的‘mark’）后不能再有空格等字符（包括注释语句也不能有）
//字符串支持折行，注意:折行位置会多一个空格
$txt="abcdef
ghijk";  //显示结果：abcd efghijk
```

常用字符串操作函数

|函数							|功能																|
|:---|:---|
|trim（）						|去除字符串首尾空白等特殊符号或指定字符序列							|
|strtolower()					|转换为小写															|
|strtoupper()					|转换为大写															|
|htmlspecialchars()				|格式化字串中的html标签												|
|strip_tags()					|函数剥去 HTML、XML 以及 PHP 的标签									|
|md5()							|计算字符串的 MD5 散列值											|
|strlen()						|字节长度 utf8编码 西文：1字节 汉字：3字节							|
|mb_strlen()					|字符个数															|
|substr()						|字符串截取函数（中文乱码）											|
|mb_substr()					|字符串截取函数（中文不乱码）										|
|strstr()						|查找字符串的首次出现，开始向后截取全部，并返回						|
|strpos()、stripos()			|查找字符串在另一字符串中第一次、最后一次出现的位置 （不区分大小写）|
|strrpos()、strripos()			|同上 （区分大小写）												|
|								|翻转字符串															|
|								|按字节来比较字符串													|
|str_replace()					|字符串替换函数														|
|str_repeat（）					|重复一个字符串														|
|ltrim() 、 trim() 、 rtrim()	|去除左侧 、 两侧 、 右侧多余字符(默认删除空格)						|
|explode( 符号 , 字符串 )		|字符串 → 数组														|
|implode( 符号 , 数组 )			|数组 → 字符串														|
|md5（）、sha1（）				|字符串加密															|

数组

数组类型

•关联式数组：下标为有意义的字符串

•索引式数组：下标为默认从0开始的数值

定义数组

•直接赋值方式定义
```
$a[] = 10;		
$a[] = 20;		
$a['name'] = '张三';
$a['sex'] = '男';

//结果
/*
 * 0 => int 10
 * 1 => int 20
 * 'name' => string '张三' (length=9)
 * 'sex' => string '男' (length=3)
 */
```
•使用array()函数
```
$b = array(10,20,30);
$b = array('name'=>'张三','sex'=>'男','age'=>28);
```
•快捷赋值
```
$c = [10,20,30];
$c = ['name'=>'张三'，'sex'=>'男','age'=>28];
```

•二维数组与多维数组
```
//二维数组
$group = array(
	'one'=>array('张三','李四','王五'),
  	'two'=>array('赵六','孙七'),
);

//定义一个三维数组
$class = array(
	'class01'=>array(
		'one'=>array('张三','李四','王五'),
  		'two'=>array('赵六','孙七'),
    ),
 	'class02'=>array(
		'one'=>array('张三','李四','王五'),
  		'two'=>array('赵六','孙七'),
    );
);

//获取李四
echo $class['class02']['one'][1];	//李四
```
数组的遍历
```
//for遍历索引数组------------------------------------------------------
$arr=[11,22,33,44，55];
for($i=0; $i<count($arr); $i++){
    var_dump($arr[$i]);
};
//foreach------------------------------------------------------------
$f_arr=["name"=>"zhangsan","age"=>18,"sex"=>"m"];
foreach ($f_arr as $key=>$value) {
    echo $key.":".$value."<br>";
};
//list（只用于索引数组）------------------------------------------------
list($a,$b,$c,$d,$e) = ["张三","李四","王五","小明","小红"];
echo $a,$b,$c,$d,$e;
```

数组的输出
```
$b = 3.1; $c = TRUE; var_dump($b,$c);

/* 输出： float(3.1) bool(true)*/
```
复制数组
```
//复制数组
$arr1=[111,222,333];
$arr2=$arr1; //$arr2是个新数组
var_dump($arr2===$arr1);//false

//用&引用数组
$arr3=&$arr1;
var_dump($arr3===$arr1);//true
```

数组常用函数

|函数							|功能																			|
|:---|:---|
|array_values()					|数组中所有的值放入一个新的索引数组，并返回										|
|array_keys()					|数组中所有的键放入一个新的索引数组，并返回										|
|array_reverse()				|颠倒数组顺序																	|
|in_array(元素，数组)			|检查数组中是否存在某个值														|
|count()						|计算数组中的单元数目 或 对象中的属性个数										|
|array_unshift()				|在数组开头插入一个或多个元素													|
|array_push()					|在数组结尾插入一个或多个元素													|
|array_unique()					|移除数组中重复的值																|
|array_pop()					|删除数组最后一个元素															|
|array_shift()					|删除数组开头的元素																|
|array_splice(数组，索引，数量)	|删除指定元素（<br />删除元素后，会重排数组索引，用unset删除不会重排数组索引）	|
|sort()							|排序 ( 升序 )																	|
|rsort()						|排序（降序）																	|
|array_merge()					|合并一个或多个数组																|

数组转JSON

|函数						|说明																				|
|:---|:---|
|json_encode( 数组 )		|JSON 格式编码 （参数必须是utf-8编码，否则会得到空字符或者null）					|
|json_decode( 字符串，参数 )|对 JSON 格式的字符串进行解码，参数：<br />true : 返回 数组<br />false : 返回 对象	|


运算符

|类型			|运算符					|
|:---|:---|
|算术运算符		|+ - * / %				|
|赋值运算符		|= += -= *= /= %= .=	|
|比较运算符		|> >= < <= != !== == ===|
|逻辑运算符	|&& \|\| not and or			|
|字符串运算符	|.						|
|其他运算符		|三元运算符 ==？ ：		|
|错误抑制符		|@						|
|提升优先级符号	|( )					|


```js
$a=10;
$b=20;
$c="hxsd";

//数字与数字相加：数学运算
echo $a+$b; //30

//数字与字符串相加
echo $a+'2018你好';//2028  数字开头为2018
echo "2018你好"+$a;//2028  同上

echo $a+'你好2018';//10  以字母开头字符串，转换成0
echo "你好2018"+$a;//10  同上

//数字与bool值
echo $a+true;//11  true:1   false：0
```

分支结构
 
单一分支结构
```
//判断你是否长得帅
$face = '帅';

//开始判断
if($face=='帅'){
  echo '你真是帅呆了，酷毙了~~';
}
```
双向分支结构
```
//开始判断
if(true){
  echo "ok";
}else{
  echo "no";
}
```
 
多向分支结构一
```
//学生成绩管理系统
$score = 100;

//判断学生成绩在那个分数段
if($score>=90 && $score<=100){
  echo "优+";
}else if($score>=80 && $score<=89){
  echo "优";
}else if($score>=70 && $score<=79){
  echo "良";
}else if($score>=60 && $score<=69){
  echo "中";
}else($score>=0 && $score<=59){
  echo "差";
}
```
多向分支结构二
```
$action = 'save';

//分支
switch($action){
  case 'save':
    echo "输入数据！";
    break;
  case 'del':
    echo "删除数据！";
    break;
  default:
    echo "请输入正确数据";
}
```

循环结构

while循环
```
While(条件表达式){
	//若条件成立，则执行这里的循环体
	//改变初值的条件;
}
```
do……while循环
```
do{
	//循环体
	//改变初值的条件;
}while(条件表达式);
```
for循环
```
//语法格式
for(初值;范围;递增){
	//循环体
}
```

特殊的流程控制语句
 
|语句		|说明																|
|:---|:---|
|break		|在switch分支当中和循环当中使用，代表结束当前分支或循环				|
|continue	|在循环当中使用，代表跳过当前层循环，若指定数字，则跳过指定层循环	|

函数的分类

系统函数

php提供了丰富的系统函数，可直接使用。这些函数涵盖了软件开发的大部分功能，具体的使用方法，请查看php开发手册。除了各种功能分类清晰的函数，还有一些常用的杂项函数：

|杂项函数	|描述							|
|:---|:---|
|define()	|定义一个常量					|
|defined()	|判断常量是否存在				|
|die()		|输出一条消息，并退出当前脚本	|
|eval()		|把字符串按照 PHP 代码来运行	|
|sleep()	|延迟代码执行若干秒				|

自定义函数

自定义函数命名口诀：字母数字下划线，首字母不能为数字，不会区分大小写，且不能使用关键字，不能重复来定义

函数的参数

形参

•形式上的参数

•在函数定义时声明

实参

•实际上的参数，在函数使用时声明

•实参和形参类型需一致

•实参和形参数量要一一对应（定义的参数必须传值，除非有默认值）

形参的默认值

•若某个形参的值总是固定的某一个值，可以使用默认值指定

•具有默认值的形参，放到参数列表后面

```js
function fun3($a,$b=20){
	return $a+$b;
}
//有默认值的参数可以省略
fun3(10)
```

查看实参函数

|函数				|说明							|
|:---|:---|
|funcgetargs()		|返回一个包含函数参数列表的数组	|
|funcgetarg(索引)	|返回参数数组的某一个			|
|funcnumargs()		|返回实参的个数					|

函数的返回值

•函数当中若遇到return，则会将return后方的内容返回到函数调用处进行保存

•return后面的语句将不再执行

•若函数没有任何返回，则默认返回null类型

变量的作用域

局部变量

在函数内部定义，只作用于函数内部
```
//默认情况下，函数参数通过值传递（因而即使在函数内部改变参数的值，它并不会改变函数外部的值）
$a=1;//外部变量
function test($arg){
	$arg+=100;
}
test($a);//只将外部变量的值传进去
var_dump($a) ;// 1  外部变量$a的值并没有改变
```
全局变量

在函数外部定义，作用于当前整个脚本，在函数内部使用需要使用global关键字声明
```
$a=10;//全局变量
function test(){
	global $a; //用global引入全局变量，在函数内部使用，子函数引入父函数变量，不能使用global
	$a++;
}
test();
var_dump($a); //结果：11
```
注意：global只能用于引入全局变量，子函数引入父函数变量，不能使用global。

引用变量传参

使用global命令，将全局变量引入到函数内部，但这种方式不够灵活，可以使用引用变量的方法：
```
//定义变量时，用&修饰参数
$a=10;
function run(&$arg){
   $arg++;
}
run($a);
var_dump($a) //结果：11
```
静态变量

在函数内部定义，作用于函数内部，使用static关键字声明
```
function test(){
	static $a=1; //静态变量
	$a++;
	echo $a;
}
test(); //2
test(); //3
test(); //4
//echo $a; //报错  静态变量只作用于函数内部，外部无法读取
```

超全局变量

在全部作用域中始终可用的内置变量

|超全局变量	|说明													|
|:---|:---|
|$_GET		|通过 URL 参数传递 ( get请求 ) 给当前脚本的变量的数组	|
|$_POST		|通过 'post' 方式给当前脚本的变量的数组					|
|$_COOKIE	|保存 Cookies信息的数组									|
|$_SESSION	|保存SESSION信息的数组									|
|$_FILES	|通过 HTTP POST 方式上传到当前脚本的项目的数组			|
|$_ENV		|包含服务器端环境变量（版本，目录，用户名等等）的数组	|
|$_SERVER	|服务器和执行环境信息									|
|$_REQUEST	|默认包含了 _POST 和 $_COOKIE 的数组					|
|$GLOBALS	|以上变量的集合											|

获取 application/json的post数据

```
php://input 是一个流，可以读取没有处理过的POST数据（即原始数据）
$postjson = file_get_contents("php://input");
```

其他应用

变量函数
```
//定义测试函数
function test(){
	echo 'web前端';
}

//将函数的名称以字符串形式存储到指定变量
$ceshi = 'test';

//此时该变量可以作为函数来使用，使用规则和函数一致
$ceshi();

//应用于 回调函数--------------------------------------------------------
function play(){
    echo "play";
}
function run($fn){
    $fn();
};
run("play");//将回调函数名作为字符串传入
```

递归
```
//回文数递归(recursion)函数
function recursion($num){
  echo $num;
  //判断
  if($num>1){
    recursion($num-1);
  }
  echo $num;
}
//调用函数
recursion(3);  //结果:3 2 1 1 2 3
```


