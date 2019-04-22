onmousedown     =null   

函数function aa (){

}



box.addevent    ('时间'，‘函数)  添加

box。removeev（’时间，函数）删除

submit   提交  没有action  提交到本页面

form -data

value 需要设置

name  不需要

classname split （‘ ’）【0】

天猫未来店

setTimeout() 方法用于在指定的毫秒数后调用函数或计算表达式。 

mousemove    mousedown mouseup click

mousedown   mouseup touchstart  touchend   click

先触摸在点击

移动端事件的库  作业

window['属性']   window.属性

e.srcElement   e.target

$.fn.extend({drag:drag})

$('.forms').drag('.opt')

this.each(index,obj

插件能够让功能进行扩展的一个术语，   让一个对象的功能进行扩展   动态的给某个对象添加属性或者是方法

extands   

class    b

constructor  

class a  extands b {

​	 

}

### 1、移动框架之zeptojs

### Zepto是一个轻量级的针对现代高级浏览器的JavaScript库，它与jquery有着类似的API。如果你会用jquery，那么你也会用zepto。Zepto的一些可选功能是专门针对移动端浏览器的;它的最初目标是在移动端提供一个精简的类似jquery的js库。

a、zepto官网：http://zeptojs.com/

b、zepto中文api：http://www.css88.com/doc/zeptojs_api/

c、zepto包含很多模块，默认下载版本包含的模块有Core，Ajax，Event，Form，IE模块，如果还需要其他的模块，可以自定义构建。

d、zepto自定义构建地址：http://github.e-sites.nl/zeptobulider/

e、touch模块封装了针对移动端常用的事件，可使用此模块进行移动端特定效果开发，这些事件有：

　　e1、tap元素tap的时候触发，此事件类似click，但是比click快

　　e2、longTap当一个元素被按住超过750ms触发

　　e3、swipe ，swipeLeft，swipeRight，swipeUp，swipeDown当元素被划过时触发。（可选择给定的方向）

### 2、移动框架之swiper

swiper.js是一款成熟的稳定的应用于PC端和移动端的滑动效果插件，一般用来触屏焦点图、触屏整屏滚动等效果。swiper分为2x版和3x版，2x版支持低版本浏览器（IE7），3x放弃支持低版本浏览器。适合应用在移动端。

2x版本中文网址：http://2.swiper.com.cn/

3x版本中文网址：http://www.swiper.com.cn/

### Swiper使用方法

1.首先加载插件，需要用到的文件有[swiper.min.js](http://www.swiper.com.cn/download/index.html#file7)和[swiper.min.css](http://www.swiper.com.cn/download/index.html#file5)文件。

![img](https://images2015.cnblogs.com/blog/810514/201707/810514-20170724203303184-468683040.png)

如果你的页面加载了[jQuery.js](http://www.swiper.com.cn/download/index.html#file2)或者[zepto.js](http://www.swiper.com.cn/download/index.html#file3)，你可以选择使用更轻便的[swiper.jquery.min.js](http://www.swiper.com.cn/download/index.html#file4)。

![img](https://images2015.cnblogs.com/blog/810514/201707/810514-20170724203342918-126312265.png)

2.HTML内容。

![img](https://images2015.cnblogs.com/blog/810514/201707/810514-20170724203419793-275089966.png)

3.你可能想要给Swiper定义一个大小，当然不要也行。

![img](https://images2015.cnblogs.com/blog/810514/201707/810514-20170724203636715-1664685572.png)

4.初始化Swiper：最好是挨着</body>标签

![img](https://images2015.cnblogs.com/blog/810514/201707/810514-20170724203916653-852144702.png)

5、如果不能写在HTML内容的后面，则需要在页面加载完成后再初始化。

![img](https://images2015.cnblogs.com/blog/810514/201707/810514-20170724204004137-1745215421.png)

或者这样（Jquery和Zepto）

![img](https://images2015.cnblogs.com/blog/810514/201707/810514-20170724204121199-11323316.png)

### **swiper（使用参数）**

1、initialSlide：初始索引值，从0开始

2、direction：滑动方向 horizontal  vertical

3、speed：滑动速度，单位ms

4、autoplay：设置自动播放及播放时间

5、autoplayDisableOnraction：用户操作swiper后是否还自动播放，默认是true，不再自动播放

6、pagination：分页圆点

7、paginationClickable：分页圆点是否点击

8、prevButton：上一页箭头

9、nextButton：下一页箭头

10、loop：是否首尾衔接

11、onSlideChangeEnd：回调函数，滑动结束时执行

**hammer.js**：多点触控插件。官网：<http://hammerjs.github.io/>

hammer.js在使用时非常简单，代码示例如下：

```
<div id="test" class="test"></div>  



<script type="text/javascript">  



     //创建一个新的hammer对象并且在初始化时指定要处理的dom元素  



     var hammertime = new Hammer(document.getElementById("test"));  



     //为该dom元素指定触屏移动事件  



     hammertime.on("pan", function (ev) {  



          //控制台输出  



          console.log(ev);  



     });  



</script>
```
extend   任意两个对象之间互相拷贝

$.extend(obj1,obj2)

命名空间  

webkittransitionend   监听动画