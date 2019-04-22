## jQuery:     jQuery  API 中文文档

本质：JavaScript框架    主要加载的是dom

宗旨：write Less      do More

作用：优化js操作  example  dom操作、页面交互、事件、ajax、动效

特性：隐式循环，链式调用

```js
$(function(){
    $("div")   不用遍历，直接应用，因为函数内部已经自我遍历
    .css("background","red")
    .animate({"margin-left",100},1000)
})
```

```js
<input type="text">
$(function(){
	$("input").focus();
})
$("input").focus();      
想要让输入框自动获取焦点，必须将方法写在函数里面，下在外面的话没有作用，因为页面已经加载完成，此时的对象已经执行完方法。
```



jQuery核心函数：

- 选择器    返回的是jQuery对象    相当于queryselector（“.box”）

- 函数 ，相当于给document   添加  ready 事件

  ```js
  jquery(function(){
      console.log("document")
  })
  jquery("document")[选择器].ready(function(){
      
  })
  jquery().ready
  ```

- 传入dom对象,返回jquery对象

- "<div></div>"     创建一个新的节点    

  ```js
  jquery(function{
         jquery("<div><span>this is span</span></div>")appendTo(jquery(".box")) })
  ```

常用方法：  call   bind    apply   

- .toArray()    将jquery对象转化为原生数组对象

jquery对象常用方法

- .css("样式属性","样式值")

- .css({})

- :header     h标签

  ```js
  $(':header').css({
  		backgroundColor:"red"
  });
  ```

  

筛选的方法：   注意与jquery对象获取的区别

- .eq(index)  返回对应下标的jQuery对象     只能用jquery方法

  ```js
  $("div".eq(1).css({
      ba
  })
  ```

  

- .get(index)   返回对应下标DOM对象   只能用dom方法

  ```js
  $("div".eq(1).style{})
  ```

- .first()

- .last()

- .hasClass("类名")    判断jquery数组中是否有一个类型为***的对象    返回true和false

- .filter([选择器],[元素],[,function])      筛选出符合条件的对象

  ```js
  <p>Hello</p><p>Hello Again</p><p class="selected">And Again</p>
  $('p').filter(".selected,:first")   保留第一个，并且保留带有selected类名的元素
  ```

  

- .is("选择器")   判断是否为某个对象

- .map(fn)   遍历对象生成一个新的数组

- .has("选择器")     返回一个选中的jquery对象   选中对象中是否有这样的子类

- .not("选择器")     从jquery数组中删除选中的元素    返回的是直接把带有这个元素的所有东西都删除

- .slice(start[,end])     截取当前位置的jquery对象

- each(index,item)    遍历jquery数组，index在前，item灾后

- .index()    返回jquery对象在数组中的下标

操作属性的方法：   属性并非样式，样式基本上都是style，而属性都是什么name，id，type等等

- .attr()   获取 传一个参数    设置  传两个参数
- .removeAttr()
- prop()     更底层   所以东西默认为空    
- removeProp()

操作类名的方法：

- addClass()
- removeClass()
- toggleClass()      

操作内容的方法：

- .text()
- .html()
- .val()

jQuery对象元素的位置信息：

- offset（）   返回一个位置信息的对象{top:\**,left:\**}     相对于浏览器的位子
- position()     返回一个位置信息的对象{x:\**,y:\**}   相对于定位的祖先元素的位置
- scrollTop()    上滚动条的高度
- scollLeft()     下滚动条的高度

事件对象：

e.offsetX

e.offsetY

e.pageX

e.pageY

e.target

e.currentTarget==this

e.stopPropagation()

e.preventDefault()

事件：

- one()
- on()
- trigger()    自动触发事件
- triggerHandler   自动触发事件，并且清除浏览器默认行为
- hover(fn,fn)   两个函数，不触发时间流
- window.onresize              

```js
$(function(){
		let arr= $('.box').map(function(){
			return $(this).offset().top    this指每个box  
		})
		let flag=true;
		arr=arr.toArray();   将jquery对象转化为普通数组
		$(window).scroll(function(){//window不需要加引号，而HTML需要加引号
			if(flag==false){
				return;
			}
			let h=$(window).scrollTop();
			let index=arr.findIndex(item=>item>h+50)
			console.log(index,h)
			h>180?$('ul').fadeIn():$('ul').fadeOut();
			if (index>=0){
				$('li')
				.removeClass('active')
				.eq(index)
				.addClass('active')
			}		
		})
		$('li').click(function(){
			let index=$(this).index();
			$('html')
			.stop()	 停止当前动作，直接执行下一个动作		.animate({scrollTop:arr[index]-200},2222,function(){
				flag=true;   //执行完这句话，把开关关闭，上面的滚动条也会触发事件，所以把开关关闭，但是除了点击事件，你还要执行滚动事件，所以执行
			})
			$('li')
				.removeClass('active')
				.eq(index)
				.addClass('active')
			flag=false;
		})
	})
```

删除DOM元素

- empty()   

  ```py
  删除子节点
  ```

- remove()

  ```py
  删除节点
  ```

- detach()

  ```py
  和上面一样
  ```

### window.onload

```py
window.onload 的意思是等页面所有的东西都加载完成，才会执行里面的东西，计算机是很遵循规矩的，写在上面的代码必然是先执行的，如果你把js代码都放在body上面，并且没有加window.onload的话，他会先执行js，但是这里就会出现问题，你如果要获取元素的话，下面你的代码还没有执行，元素还不存在，你获取的东西就是空的，所以就要在页面加载完成后才能执行js代码
```

### 为什么会使用jquery:

```py
用js首先你查询的方式 特别冗长 ，document.querySelectorAll('div')  获取回来的是类似数组 数组 arr=[1,2,3] ，类似数组 ccc=[0:'1',1:'2'] ,但是他可以用素组的方法获取到每一个元素 instanceof Array 判断是否是素组；其次他需要循环，然后才能获取到每一个元素，还有就是操作不流畅，就是说写的东西太多，不够简洁，json 没有面向对象的特质，json js独有的一种存储数据的对象。
```

### js的函数：

```py
1.就是指函数
2.对象，函数也是对象
3.构造函数（类）
c.call('a') 指针指向a
ecmascript      在js nodejs（操作后台）  actionscript（）  都会使用mjs操作的是dom元素，js中创建类 把方法要放到prototype 里面，因为这样运行效率快，至于为什么，老师说比较复杂，没讲   
```

### jquery：

```py
 jQuery
 将原生的单个化操作，批量操作
 将原生的复杂的查询方式（兼容），简单化
 将原生逐步操作的方式，链式的操作
 将原生操作复杂的逻辑，提供简单的接口

 只专注于业务的逻辑，语法的问题
 link    Script   Image  图片精灵就是为了减少浏览器的请求
  document.addEventListener('DOMContentLoaded',function)  页面加载标签就会触发，window.onload的是页面所有的东西都加载完，才会出发，比如说有很多图片，这个需要全部加载完，而前面那个只需要加载标签   
  background:url()   audio video ajax 链接    被动发生请求是啥
```

### this指针问题：

```py
一般函数的this指针都指向window，但如果说你给一个事件赋值了一个函数，那么这个函数里面的this就会指向这个时间对象
如果你想使用this来指向HTML元素响应的事件，你必须确保this关键字被写在onclick属性里。只有在这种情况下它才指向event
element.onclick = doSomething
element.addEventListener('click', doSomething, false)
element.onclick =
function() {this.style.color = '#cc0000';}
<element
onclick="this.sytle.color = '#cc0000';">
element.onclick = doSomething
element.addEventListener('click', doSomething, false)
element.onclick =
function() {this.style.color = '#cc0000';}
<element
onclick="this.sytle.color = '#cc0000';">

下述情况中，this指向window：
Javascript代码
element.onclick = function() {doSomething()}    这里只是引用了一下这个函数，并不是给他复制，model最主要的弊端是attachEvent()创建了一个指向函数的引用，而不是复制它。因此有时不可能知道哪个HTML正在处理该事件。
element.attachEvent('onclick', doSomething)
<element
onclick="doSomething()">
element.onclick = function() {doSomething()}
element.attachEvent('onclick', doSomething)
<element
onclick="doSomething()">
```

## www:

```py
Uncaught ReferenceError: Invalid left-hand side in assignment
相关错误：

Uncaught exception: ReferenceError: Cannot assign to ‘functionCall()’, Uncaught exception: ReferenceError: Cannot assign to ‘this’
尝试给不能赋值的东西赋值，引起这个错误。

这个错误最常见的例子出现在 if 语句使用：

if(doSomething() = 'somevalue')
此例中，程序员意外地使用了单个等号，而不是双等号。“left-hand side in assignment” 提及了等号左手边的部分，因此你可以看到以上例子，左手边包含不能赋值的东西，导致这个错误。

如何修复错误：确保没有给函数结果赋值，或者给 this 关键字赋值。
```

### jquery

```py
1.zifuchuan
	选择器     要将选择器
	标签
2undefined
3.hanshu
4.
```

### 数据缓存：

```py
var name=‘z’
￥（function（）{
    ￥（‘div）。data（name ，z）
    console，log（￥（’div）。data（name））
}）
div
```

插件机制   框架的意义

多苦共存   

队列控制

### ajax

```py
ajax.onreadystatechange=function（）
ajax.readystate
ajax.status
ajax.response
一般只有四个步骤：
	1.创建对象 let ajax=new XMLHTTPRequest()
	2.监听过程 ajax.onload=function(){
        
	}
	3.安排任务 ajax.open('get','/url')   第一个参数是以什么方式获取，第二个参数是去哪里寻找 第一个参数还可以以post方式获取，但这个方式有点不一样，首先指定获取方式为post，但要在send里面进行数据的传递,然后需要再添加一个方法，ajax.setRequestHeader('content-type','application/x-www-form-urlencoded')
	4.发送  ajax.send()    
	open 里面有五个参数，第三个是同步与异步，同步时一起发生，异步是互不影响，默认是异步，true，如果是false ，则为同步，第四五个是用户名和密码，但如果在自己的服务器上面，不需要输入这些东西
1.ajax解决的问题：
	1.页面跳转的问题
	2.用户的交互就是用户的体验度
	3.异步的获取或者传递数据
	4.操作效率
	老师的总结：
		1.页面无刷新操作数据
		2.按需获取的问题   第一次还没加载，但是过去之后加载了
		3.让基于bs架构的软件能成为想基于cs架构的软件操作流畅
2.ajax的使用   立用js异步地能力
3.new XMLHTTPRequest()
4.open（） send（） onload
5.可以处理多种返回类型的返回的数据（text，json，blob，arraybuffer，document）
6.传递数据  get post

地址
方式
返回的类型
传递的数据
最终的处理结果
function（）{
    
}
参数初始化
data.
success(){}
json.dumps(result)   把json对象转化为json字符串


服务器    
	优点：首页加载速度快，业务逻辑清淅，工作量比较少
	缺点：用户体验度不好，服务器压力大，不利于协同工作
ajax
	优点：用户的体验比较流畅，减轻服务器的压力，有利于协同工作
	缺点：首页加载速度慢，业务逻辑不清晰，工作量比较大
mvvm  model ->模型->数据    view->视图->模板->html+css
    数据到视图    视图到数据   双向数据绑定   优点大于缺点
angular   react  vue
vue->node.js  前端的繁荣


```

BS与CS的区别：

```py
C/S架构的优缺点：
*优点：
1.客户端因为是独立设计，所以可以实现个性化
2.因为客户端是需要进行安装的，可以不需要重复安装和加载
3.因为客户端是独立开发的，所以有能力对客户端进行安全设计
4.如果遇到不同的操作系统，需要为不同的操作系统各开发一套客户端
*缺点：
1.因为客户端是不需要重复安装，所以用户可以不更新与升级，增加了维护成本。
2.因为需要开发客户端和服务器两套程序，所以开发成本会增加
B/S架构的优缺点：
*优点：
1.因为B/S架构具备通用性，所以开发成本较低。
2.因为不需要安装客户端，所以客户端不需要进行升级，只需要更新后台代码即可实现所有客户端的更新。
3.因为B/S架构多用WEB网页进行开发，所以增、删功能也非常容易，只需要修改网页即可完成
*缺点：
1.耗流量，每次都要加载全部的内容（不过有缓存可以降低流量损耗）
2.因为没有独立的客户端，所以无法实现个性化（通过账号体系可以实现）
3.因为没有独立设计客户端，所以客户端难以实现安全控制（HTTPS、控件）。
4.难以实现特殊的操作（删本地文件），所以所有的杀毒软件都是C/S架构的。
B/S架构更多的时候是使用了HTTP协议、而C/S架构更多的时候使用的WinSocket协议（TCP、UDP）
```



码云

插件机制？

$().fn.extend({aaa:function(){

}})

单线程异步机制的语言   js 最基本的特性

单线程  程序同一时间只能执行一件事情

异步机制      把需要耗费时间以及不确定时间的代码放到异步执行

极少的资源左更多的事情，单线程模拟多线程

因为异步机制的代码，

电影  屏幕有刷新率  赫兹   60  眼睛看不到

1s  23-24   yinwei人

### 队列：

回调地狱，队列就是为了解决回调地狱   优雅的控制异步代码的执行顺序

原声js没有队列思想，jQuery里面添加了这种思想     现在 的js实现了 promise

三种队列：  animate（不需要指挥）   fx（需要指挥）   自定义队列（每次都指挥）

入队  出对

jQuery  animate已经实现了队列，js没有

$('div').queue(function(){

​	settimeout(function(){

​	console.log(1)

​	$('div').dequeue()

},1000)

})

animate       自己进去队列，自己出列

fx             自己进去队列，自己出列，但是需要通知你出对

自定义队列      自己进去队列，但是出列需要通知，最重要的是，需要通知整个队伍开始表演

stop  和finnish     stop是停止当前的动作，直接做下一个，finish是直接到最后一步，省略过程，stop需要写在动作前面，finish需要写在动作后面