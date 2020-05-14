Laravel是一款简洁、优雅的PHP Web开发框架，它可以让你从面条一样杂乱的代码中解脱出来；它可以帮你构建一个完美的网络APP，而且每行代码都可以简洁、富于表达力。

官方手册推荐我们使用Laravel Homstead虚拟机，我们可以着手去配置该虚拟机，若是初学者的话，建议先使用本地环境wamp即可

检查环境

新建phpinfo.php，输入phpinfo()函数，并进行访问查看。

•PHP >= 7.0.0

•PHP OpenSSL 扩展

•PHP PDO 扩展

•PHP Mbstring 扩展

•PHP Tokenizer 扩展

•PHP XML 扩展

安装 Composer
```
//下载地址(点击 Composer-Setup.exe 按钮)
https://getcomposer.org/download/
```

下载 Laravel
```
composer global require "laravel/installer"
```

在使用前，要确保以下几个内容的配置是正确的，配置有问题会影响我们的项目开发。

1. 虚拟域名

框架安装完毕后要给项目定义一个虚拟域名，具体步骤如下：
```
httpd.conf
打开wamp/bin/apache/apache2.4.23/conf/httpd.conf 文件，查找 Include conf/extra/httpd-vhosts.conf，将其前方的#号去掉。
hosts
编辑 C:\Windows\System32\drivers\etc\hosts文件，添加：127.0.0.1  www.test.com
httpd.vhost
编辑 wamp/bin/apache/ apache2.4.23/conf/extra/httpd-vhosts.conf文件，参考如下代码：
// 复制已存在的 VirtualHost 标签包含的所有内容，并修改如下三步(含)
<VirtualHost *:80>
	ServerName www.test.com	//1. 修改这里与hosts文件中的域名一样
	ServerAlias localhost
	DocumentRoot c:/wamp/www/test/public	//2.修改这里为你的Laravel框架入口文件所在路径
	<Directory  "c:/wamp/www/test/public">	//3.这里的修改同上
		Options +Indexes +Includes +FollowSymLinks +MultiViews
		AllowOverride All
		Require local
	</Directory>
</VirtualHost>
```
2. 配置文件

Laravel 的所有配置文件都存储在 config 目录下

3. 目录权限

确保storage 目录和 bootstrap/cache 目录应该允许 Web 服务器写入，否则 Laravel 将无法运行。

4. 应用秘钥

如果应用程序密钥没有被设置，就不能确保你的用户会话和其他加密数据的安全！
```
//在git命令行输入如下命令即可
php artisan key:generate
```
5. .env配置

确保.env配置文件中的数据库配置是正确的(如下)
```
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=myshop
DB_USERNAME=root
DB_PASSWORD=1234
```
6. 维护模式
若你的项目进入了维护状态，你需要执行以下命令来关闭你的应用；维护完毕记得开启！
```
//维护
php artisan down

//启动
php artisan up
```

目录结构

认识目录结构，有助于我们在后续的开发更迅速与便捷
```
test
  |----app/ *			//包含应用程序的核心代码(Controller、Middleware、Model)
  |----bootstrap/		 //包含引导框架并配置自动加载的文件
  |----config/ *		 //包含应用程序所有的配置文件(app.php、database.php)
  |----database/ *		 //包含数据填充和迁移文件
  |----public/ *		 //包含了入口文件index.php、资源文件(Js/Css/Img)
  |----resoure/ *		 //包含了视图和未编译的资源文件(LESS/SASS)
  |----routes/ *		 //包含了应用的所有路由定义(web.php/api.php)
  |----storage/			 //包含编译的 Blade 模板
  |----tests/			 //包含自动化测试文件
  |----vendor/			 //包含了你的 Composer 依赖包
  |----.env*			 //环境配置文件
  |----artisan*			 //Artisan 是 Laravel 中自带的命令行工具的名称
  |----composer.json	  //Composer用于安装依赖包的配置文件
  |----composer.lock	  //优先读取的依赖版本文件，可确保使用者使用相同版本依赖包
  |----package.json		  //依赖包详细描述文件
  |----phpunit.xml		  //一个面向程序员的PHP测试框架
  |----readme.md		  //使用说明书
  |----server.php		  //模拟了web server的rewrite功能，主要用于测试
  |----webpack.mix.js	   //资源文件打包配置文件
```

路由

当我们请求index.php这个加载框架的起点，它就为我们加载Composer生成定义的自动加载器，紧接着就找到bootstrap/app.php脚本中检索 Laravel 应用程序的实例。

当程序完成上述几步以后，就会通过HTTP请求去访问app/Http/Kernel.php 中的 HTTP 内核，从而使得内核把我们带到了Routes/web.php 路由文件中。

执行完了上述的一系列过滤、加载、启动之后，Laravel开始给我们分发路由了，路由的核心就是要让我们定位到某个闭包程序或某个控制器上去。

基本应用

简单路由

路由文件在 Routes/web.php
```
//这是一个测试路由，当我们访问 www.test.com/test 时，会访问到此路由，并在页面输出 Hello World
Route::get('/test', function () {
    return 'Hello World';
});
```
请求方式

路由指定了请求方式，必须由该方式进行访问，否则页面会提示未找到
```
Route::get($uri, $callback);		//GET方式请求(常用)
Route::post($uri, $callback);		//POST方式请求(常用)
Route::put($uri, $callback);		//伪造PUT方法请求
Route::patch($uri, $callback);		//伪造PATCH方法请求
Route::delete($uri, $callback);		//伪造DELETE方法请求
```
路由参数

说到请求，当然少不了参数，Laravel的路由位置也可以传递参数

单个参数

路由中的参数，可以在闭包程序中直接使用，也可以在控制器中直接获取
```
//当我们请求 www.test.com/user/10 时，会将10的参数传递到当前路由
Route::get('user/{id}', function ($id) {
    return '当前用户的id是：'.$id;
});
```
多个参数

参数与参数之间的符号分割没有明确的限定，通常为/或-
```
//当我们请求 www.test.com/user/5-info-1 时，可以访问到如下路由的内容
Route::get('user/{id}-{service}-{page}', function ($id, $service, $page) {
    //输出参数信息
  	return '您正在查看用户id为：'.$id.'的'.$service.'服务的第'.$page.'页的内容！';
});
```
可选参数

某些情况下，有的参数是可有可无的，我们可以使用?问好来标注改参数是可有可无的。
```
//当我们请求 www.test.com/user/zhangsan 或 www.test.com/user时
Route::get('user/{name?}', function ($name = null) {
    if($name != null){
  		return "这是zhangsan的信息";
	}else{
  		return "这里是用户的列表信息";
	}
});
```
正则约束

约束一个

若不给用户所传递的参数限定格式，
将导致一些不必要的麻烦，因此，我们可以使用正则对其进行约束。
```
//在路由后方追加where方法，第一个参数是要进行约束的参数名称，第二个参数则是正则模式的规则
Route::get('user/{id}', function ($id) {
    return '当前用户的id是：'.$id;
})->where('id','\d+');
约束多个
Route::get('user/{id}-{service}-{page}', function ($id, $service, $page) {
    //输出参数信息
  	return '您正在查看用户id为：'.$id.'的'.$service.'服务的第'.$page.'页的内容！';
})->where(['id'=>'\d+', 'service'=>'\w+', 'page'=>'\d+']);
命名路由
某些路由的可能会非常非常长，例如users/list/info/{id}-{service}-{page}...，若想要在跳转到或获取该路由时，可能不太方便，因此，Laravel给我们准备了命名路由。
//直接在路由后方追加name方法，并定义当前路由的别名
Route::get('user/info', function () {
    //
})->name('uinfo');
生成链接
这样一来，若我们想要进行跳转，我们可以这样写
// 生成 URL...
$url = route('uinfo');	//www.test.com/user/info

// 生成重定向...
return redirect()->route('uinfo');
```

路由组

我们的项目程序都是分为前台后台模块的，有些项目甚至分了其他诸多模块，
因此，若一直按之前的路由书写方式写下去，将导致路由文件中的路由毫无章法，
因此，Laravel为我们准备了路由组
```
//前台路由组（没有任何条件限定）
Route::group([这里存放中间件、路由前缀等信息，默认为空(老版本)],function(){
  //加载首页的路由
  Route::get('/',function(){
  	return "这里是前台首页！";
  });
});
```
中间件

如果你想要让用户在进入当前路由组之前，给其添加一些要求，
我们可以使用路由组中间件进行限定
```
//添加了一个login的中间件限定，用户必须登录后才能访问前台首页（知乎）
Route::middleware('login')->group(function(){
  //加载首页的路由
  Route::get('/',function(){
  	return "这里是前台首页！";
  });
});
```

如果有多个中间件限定，我们也可以以数组方式进行使用
```
Route::middleware(['login','auth','status'])->group(function(){...});
```

命名空间

这里的命名空间主要是针对控制器的，因为项目划分前后台的原因，
我们需要将前台的控制器放置到前台目录，后台控制器放置到后台目录，
因此，这个时候就涉及到了前后台命名空间的问题。
```
//若你的控制器来自于后台，则可以直接使用如下方式指定
Route::namespace('Admin')->group(function () {
    // 在 "App\Http\Controllers\Admin" 命名空间下的控制器
});
```
路由前缀

当我们通过路由访问某个应用时，因为前后台的原因，
路由肯定也应当有一些响应的区别，因此，
我们可以使用路由前缀来规定访问前台和访问后台的路由。
```
//当我们请求 www.test.com/admin/users 时会访问到如下的方法
Route::prefix('admin')->group(function () {
    Route::get('users', function () {
        // 匹配包含 "/admin/users" 的 URL
    });
});
```
同时使用

若你想要再同一个路由组中同时使用中间件、路由前缀、
命名空间等信息，你可以这样写
```
Route::middleware('login')->prefix('home')->namespace('home')->group(function(){
  //加载首页的控制器
  Route::get('/','IndexController@index');
});
```

