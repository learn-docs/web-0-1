模板引擎

区块占位

首先需要定义一个公共模板，我们这里在layouts目录中生成了index.blade.php模板

```
<!-- 文件保存于 resources/views/layouts/index.blade.php -->

<html>
    <head>
  		<!--这里是一个单行占位-->
        <title>应用程序名称 - @yield('title')</title>
    </head>
    <body>
  		<!--这里是一个区块占位-->
        @section('sidebar')
            这是 master 的侧边栏。
        @show

        <div class="container">
            @yield('content')
        </div>
    </body>
</html>
```

继承布局

公共模板定义好了，那意味着你的框架已经打好了，接下来就是让其他模块来继承公共模块了，然后将需要进行内容替换的位置进行替换即可。

```
<!-- 文件保存于 resources/views/child.blade.php -->
//继承公共模板内容
@extends('layouts/index')

//替换单行占位的内容
@section('title', 'Page Title')

//替换区块占位的sidebar内容
@section('sidebar')
    @parent	//这里的parent代表了，依然要延续使用公共框架的内容

    <p>这将被添加到主侧边栏。</p>
@endsection

//替换单行占位的content内容
@section('content')
    <p>This is my body content.</p>
@endsection
```

控制结构

```
if语句
@if (count($records) === 1)
    我有一条记录！
@elseif (count($records) > 1)
    我有多条记录！
@else
    我没有任何记录！
@endif
switch语句
@switch($i)
    @case(1)
        First case...
        @break

    @case(2)
        Second case...
        @break

    @default
        Default case...
@endswitch
循环结构
@for ($i = 0; $i < 10; $i++)
    目前的值为 {{ $i }}
@endfor

@foreach ($users as $user)
    <p>此用户为 {{ $user->id }}</p>
@endforeach

@while (true)
    <p>死循环了。</p>
@endwhile
特殊的流程控制语句
@foreach ($users as $user)
    @if ($user->type == 1)
        @continue	//跳过当前层遍历
    @endif

    <li>{{ $user->name }}</li>

    @if ($user->number == 5)
        @break	//终止遍历
    @endif
@endforeach
或者，你可以使用另外一种语法结构
@foreach ($users as $user)
    @continue($user->type == 1)	//直接将条件放到括号

    <li>{{ $user->name }}</li>

    @break($user->number == 5)	//同上
@endforeach
```









