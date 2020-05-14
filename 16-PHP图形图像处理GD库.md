PHP中的绘图工具

作用：绘制饼图、柱形图、折线图、验证码、水印、缩放等

支持：GIF、JPEG、PNG、WBMP等格式

绘画步骤

```js
//示例
//1.创建画布
$img = imagecreatetruecolor(200,200);

//2.准备颜料
$bg = imagecolorallocate($img,200,200,200);
$red = imagecolorallocate($img,255,0,0);
$blue = imagecolorallocate($img,0,0,255);

//3.绘画...
imagefill($img,0,0,$bg);	 //填充背景
imageellipse($img, 200, 200, 100, 100, $red); //画空心圆
imagesetpixel($img, 100, 100，$blue);//绘制像素点

//绘画其他..............

//4.输出图像
header('Content-Type:image/jpeg');	//设置http协议头信息
imagejpeg($img);	//输出图像流

//4.释放资源
imagedestroy($img);
```

常用函数

GD库图片函数的参数很多，具体使用方法参照php手册

|函数										|说明																		|
|:---|:---|
|imagecreate(宽,高)							|创建一个256色画布															|
|imagecreatetruecolor(宽,高)				|创建一个真彩画布															|
|imagecreatefromgif(完整路径文件名)			|将一张gif图像放入画布														|
|imagecreatefrompng(完整路径文件名)			|将一张png图像放入画布														|
|imagecreatefromjpeg(完整路径文件名)		|将一张jpeg图像放入画布														|
|imagecreatefromstring(字符串)				|从字符串中的图像流新建一图像												|
|imagecolorallocate()						|定义颜色																	|
|imagecolorallocatealpha()					|定义带alpha通道（透明）的颜色												|
|imagefill()								|填充背景																	|
|imagesetpixel()							|绘制像素点																	|
|imageline()								|绘制线条																	|
|imagerectangle()、imagefilledrectangle()	|矩形线框、实心矩形框														|
|imagepolygon()、imagefilledpolygon()		|多边形线框、实心多边形														|
|imageellipse()、imagefilledellipse()		|椭圆线框、实心椭圆															|
|imagearc()、imagefilledarc()				|圆弧、实心圆弧（扇形）														|
|imagettftext()								|绘制文本需引入字库(支持中文字库，输出中文)									|
|getimagesize(完整路径文件名)				|获取图像的宽、高、大小、类型等相关信息<br />成功返回：数组 失败返回：false	|
|imagesx(资源)								|取得图像宽度																|
|imagesy(资源)								|取得图像高度																|
|imagecopy()								|用于拷贝图像或图像的一部分 <br />成功返回：true ，失败返回：false			|
|imagecopyresampled()						|用于拷贝部分图像并调整大小（重新采样）										|
|imagegif()									|输出gif格式图像															|
|imagejpeg()								|输出jpeg格式图像															|
|imagepng()									|输出png格式图像															|
|imagedestroy()								|释放资源																	|


```js
imagecopyresample（src_image , dy , sy , dh , sh）
```

绘制基本几何图形

最基本的集合图形主要有点、线、圆、多边形等，有了基本几何图形，就可以演变出更为复杂的图形。GD库也提供了三个绘制基本图形的函数， imageline()函数、imagearc()函数、imagerectangle()函数分别用来绘制线段，弧形（包括圆弧），矩形。

•imageline()函数用来绘制线段
```
 bool imageline(resource image, int x1, int y1, int x2, int y2, int color)
```
 该函数参数表示使用color颜色在图像image上从坐标(x1,y1)到(x2,y2)画一条线段。在画布里，坐标原点为左上角，横坐标水平向右为正，纵坐标垂直向下为正。

•imagearc()函数用于绘制椭圆弧（包括圆弧）
```
 bool imagearc(resource image, int cx, int cy, int w, int h, int s, int e, int color)
```
 该函数参数表示用color颜色在图像image上以(cx,cy)为中心，画一个椭圆弧，w和h分别是这个椭圆的宽和高，s和e都是角度，分别表示圆弧起点角度和圆弧终点角度，0度位置在中心的三点钟位置（x轴正轴方向）。

•imagerectangle()函数用来绘制一个矩形
```
 bool imagerectangel(resource image, int x1, int y1, int x2, int y2, int color)
```
 该函数参数表示用color颜色在图像image上画一个矩形，左上角坐标为(x1,y1)，右下角坐标(x2,y2)。

图像填充

•imagefill()函数用于图像区域填充
```
 bool imagefill(resource image, int x, int y, int color)
```
 该函数表示用color在image图像的坐标(x,y)位置执行区域填充，与(x,y)点颜色相同且相邻的点都会被填充。

•imagefilledarc()函数用于画一椭圆弧并填充
```
 bool imagefilledarc(resource image, int cx, int cy, int w, int h, int s, int e, int color, int style)
```
 它的参数说明同imagearc()函数，与之相比，多了参数style，它用来表示填充的方式，可选择有如下几种：
 
 IMGARCPIE：普通填充，产生圆形边界
 
 IMGARCCHORD：只是用直线连接了起始和结束点与IMGARCPIE互斥
  
  IMGARCNOFILL：指明弧或弦只有轮廓，不填充
 
 IMGARCEDGE：指明用直线将起始和结束点与中心点相连

•imagefilledellipse()函数用于画一个椭圆并填充
```
 bool imagefilledellipse(resource image, int cx, int cy, int width, int height, int color)
```
 该函数表示用color颜色在image图像上画一个填充的椭圆形，这个椭圆形的中心点在(cx,xy)，宽为windth，高为height。

•imagefilledrectangle()函数用于画一个矩形并填充
```
 bool imagefilledrectangle(resource image, int x1, int y1, int x2, int y2, int color)
```
参数意义和imagerectangle()函数一致，与之不同的是imagefilledrectangle()函数会填充颜色。

•imagefilledpolygon()函数用来画一个多边形并填充
```
 bool imagefilledpolygon(resource image, array points, int numpoints, int color该函数表示用color颜色在image图像上画一个填充的多边形，多边形的顶点按照顺序存储在points数组中，numpoints表示多变形的边数，num_points的数值必须大于等于3，且小于等于points数组的值个数的一半。
```
在图像中添加文字

前面在加载图像章节在加载失败则以图像方式输出错误信息的时候已经见过这个函数：imagestring()。imagestring()的主要功能就是在图像中添加函数，它的语法格式如下：
```
bool imagestring(resource image, int font, int x, int y, string string, int color)
```
该函数表示用color颜色在image图像上的(x,y)位置，使用font字体绘制字符串string。绘制字符串的时候，是从(x,y)右下方开始绘制。通常情况下font使用1，2，3，4，5等内置字体。

拷贝图像

•getimagesize()函数用于获取图像的尺寸：
```
 array getimagesize(string filename)
```
•imagecopy()函数用于拷贝图像或图像的一部分
```
 bool imagecopy(resource dstim, resource srcim, int dstx, int dsty, int srcx, int srcy, int srcw, int srch)
```
•imagecopyresized()函数用于拷贝图像或图像的一部分并调整大小，它的语法结构如下：
```
 bool imagecopyresized(resource dstim, resource srcim, int dstx, int dsty, int srcx, int srcy, int dstw, int dsth, int srcw, int srch)
```
•imagecopymerge()用于拷贝并合并成图像的一部分：
```
 bool imagecopymerge(resource dstim, resource srcim, int dstx, int dsty, int srcx, int srcy, int srcw, int srch, int pct)
```

