## vue

### 下载nodejs：

```py
linux 系统  在官网复制链接
wget+链接 ，下载好将他解包
tar -Jxvf +文件名
进入bin里面的找到npm，node，将他们进行软连接
sudo ln -s ~/nodejs/bin/npm  /usr/local/bin/npm 
sudo ln -s ~/nodejs/bin/node  /usr/local/bin/node 
windows里面，直接在官网里面下载 安装好就行
```



### mvvm

```py
mvc 的   model  view  controller
mvvm   moedl view  view model
v-model  只能用在表单上
mvvm    页面不跳转，热加载

MVVM是Model-View-ViewModel的简写。它本质上就是MVC 的改进版。MVVM 就是将其中的View 的状态和行为抽象化，让我们将视图 UI 和业务逻辑分开 ，采用双向数据绑定，view与viewmodel绑定，model与viewmodel绑定


"MVVM是Model-View-ViewModel的缩写。MVVM是一种设计思想。Model 层代表数据模型，也可以在Model中定义数据修改和操作的业务逻辑；View 代表UI 组件，它负责将数据模型转化成UI 展现出来，ViewModel 是一个同步View 和 Model的对象。\n\n在MVVM架构下，View 和 Model 之间并没有直接的联系，而是通过ViewModel进行交互，Model 和 ViewModel 之间的交互是双向的， 因此View 数据的变化会同步到Model中，而Model 数据的变化也会立即反应到View 上。\n\nViewModel 通过双向数据绑定把 View 层和 Model 层连接了起来，而View 和 Model 之间的同步工作完全是自动的，无需人为干涉，因此开发者只需关注业务逻辑，不需要手动操作DOM, 不需要关注数据状态的同步问题，复杂的数据状态维护完全由 MVVM 来统一管理。"  

```

### MVC：

```py
软件可以分为三个部分，视图（用户界面），控制器（业务逻辑），模型（数据保存），view传送指令到控制器，控制器完成业务逻辑后，要求model改变状态，在讲数据返回到view中
```



### 指令

### 路由

控制器，mvv是mvc的一种扩展   mvvm只能用在前端，mvc  前后端分离  控制 controller

定义组建，定义路由，绑定到对象身上

#### 嵌套路由：

```py
你当前的这个页面就是通过路由呈现出来的，但是你需要在这个页面又有不同的效果，所以想到了嵌套路由，
{
        path:'/',
          component:upload,
          children:[{
            path :'rrr',
              component:list
            }

          ],
      },
      当前在根目录邮箱嵌套路由，有个children属性专门写这个的，如果push为空，那么页面一进来就是这个状态，如果不为空，为具体的东西，则地址栏上会进行跳转
```



### 状态

努力使有目标的自觉奋斗  而忙碌则是毫无目的的被人拖着走

1.启动vue	

​	new Vue（）

2.参数选项

​	el：锁定vue作用的范围

​	data：{}   指定数据

​	methods：{}  操作逻辑

​	computed：{}  动态的数据

​	watch：{}   手动去监控某一个数据的变化

​	mounted:{}    周期性的东西

3.指令

​	模板引擎  {{}}

​	v-text：预期想要呈现的样子，比如说把前面两个的计算结果显示出来

```py
<td colspan="2" v-text="rows"></td>
computed:{
            rows(){
                let num=0
                this.datas.forEach(function(item,index){
                    num+=item.mount
                })
                return num
            },}
```



​	v-html:  和上面的一样

​	v-model:    表单上面的指定  双向数据绑定

​	v-for:循环

​	v-if:判断

​	v-else:

​	v-show：

​	v-bind    或者是 ：

​	v-on:  或者是@   添加事件函数

​	：style={background:(item.isdown?'red':'none')}

4.组件

组件化开发

函数：

Vue.component("car",代码,data(new Vue里面的代码))

Vue.component("car",{"template":`代码`},data{

return{

Vue 里面的代码} })



完整的结构 完整的逻辑  完整的数据

Vue.component（'myul'{

​	template:`

​		

`	,data(){

​	return {

​	datas:[

​		{"1111"},

​		{"2222"},

​		{"3333"}

]

}

}

}）



parsefloat

自调用    调用  添加事件

localstorage    5mab

cookie   登陆    

local.aa=bb

local.setItem（‘aa’，“bb”）

local.removeItem（‘aa’）

loacl.clear（）

localstorage    存储的是字符串

JSON.stringify（datas）

json.parse  

### 双向数据绑定：

```py
<div>zhangsan</div>
<script>
        var temp;
        var obj={}
        Object.defineProperty(obj,'name',{
        	value:100,       指定值
        	writable:true,        可更改   set函数与这个属性是不能共存的，两者都是为了设置对象的属性，同时存在会冲突
            configurable:true,		可删除
            enumerable:true,			可循环
            set:function(val){
                console.log('我在设置值')
                if (temp!=val){
                    document.querySelector('div').innerHTML=val;
                }
                temp=val
            },
            get:function(){
                console.log('我在获取值')
                return temp
            },
        })
        obj.name="zhangsan"    这句话是给对象设置属性，当你执行这句话的时候，会调用set方法，下面同理，真正获取值的时候，是跟设置值的时候是没关系的，get函数最终的返回结果才能决定最后的值
        console.log(obj.name)
        obj.name="lisi"
        console.log(obj.name)
  </script>
```

```py
var 声明一个新的变量    
变量=xx  顶i一个全局变量    不管在函数外面还是里面  函数运行外
为什么局部变量在外面访问不到
	1.语言的使用层面：防止全局变量的污染
	2.节省内存的空间
		局部变量运行完就销毁
```

闭包：能够在函数的外部访问到 函数内部的变量

在一个函数里面引用了外层函数的变量，并且当我们调用里层函数的时候，闭包形成

svg  矢量图    canvas   位图   babel

### 安装vue开发版，比较牛逼的

2.0

npm install -g  vue-cli

vue -V

vue init webpack  aaa       创建项目

y y y n   n  n   yes   cd aaaa    npm run dev  

src   

npm uninstall -g vue-cli

3.0

npm install -g @vue/cli

linux系统下需要把他进行软连接

vue create  filename

手动  第二个    （更改设置，自己配置）

babel  vuex   router  空格选中   选中这三个

是否让浏览器实现不用#就可以实现获取数据，但不跳转的效果，用到什么history，选择否，是否保存你的设置，选择是packgejson    这个相当于是nodejs的包，在python中，文件里面有__init__.py就可以认为是一个包，两者类似。

y     n   npm run serve

页面不跳转，获取内容，能有历史纪录

uri  定位资源的方式，url是通过http规定的地址的方式，他是uri的一种

协议   http https   svn   统称tcp/ip协议

协议://（用户名：密码@）主机的名字：端口/路径/文件名？查询字符串#锚链接

什么是锚链接？

```py
在本地进行跳转
 <a href="#ccc">1111</a>
    <div>01</div>
    <div>02</div>
    <div>03</div>
    <div>04</div>
    <div>05</div>
    <div>06</div>
    <div>07</div>
    <div>08</div>
    <div>09</div>
    <div>10</div>
    <div>11</div>
    <div>12</div>
    <div id='ccc'>13</div>
    <div>14</div>
    <div>15</div>
    <div>16</div>
    <div>17</div>
    <div>18</div>
    <div>19</div>
    <div>20</div>
在一个页面中，位置不同进行跳转
```



易用性  可用性  愉悦性

@代表src的绝对路径

vue。use（router）扩展

mounted？？跨域

：to   =“’/edit？id=‘+item.id”

跨域访问，ajax可以获取信息是因为在同一域下面

什么是跨域：

```py
浏览器从一个域名的网页去请求另一个域名的资源时，域名、端口、协议任一不同，都是跨域 
域名： 
　主域名不同 http://www.baidu.com/index.html –>http://www.sina.com/test.js 
　子域名不同 http://www.666.baidu.com/index.html –>http://www.555.baidu.com/test.js 
　域名和域名ip http://www.baidu.com/index.html –>http://180.149.132.47/test.js 
端口： 
　http://www.baidu.com:8080/index.html–> http://www.baidu.com:8081/test.js 
协议： 
　http://www.baidu.com:8080/index.html–> https://www.baidu.com:8080/test.js 
备注： 
　1、端口和协议的不同，只能通过后台来解决 
　2、localhost和127.0.0.1虽然都指向本机，但也属于跨域
--------------------- 
作者：飞扬_柳絮 
来源：CSDN 
原文：https://blog.csdn.net/tjcjava/article/details/76468225 
版权声明：本文为博主原创文章，转载请附上博文链接！
```



ajax解决跨域问题

1.jsonp    快捷一点，但有诸多限制   就代表script标签对   局限性，自己有权限操作的两个域名   或者对方配合的服务器   原理：script  标签对跨越的能力   应用：jQuery

```py
jsonp
这是html的页面
<script>
	function aa(con){
        document.querySelector('div').innerHTML=con
	}
</script>	
<script src="http:127.0.0.1:9000/callback=aaa"></script>  html界面利用script的跨域性，访问第二个服务器，然后把数据传过去，服务器再去接受，最后返回东西
第一个服务器 ，返回html界面  
@route('/')
def home():
	return render_temlpate(1.html)
第二个服务器
@app.route('/')
def home():
	fn=request.args.get('callback')
	return fn+"('ccc')"
```

```py
$.ajax({
    url:'url',   传进来地址
    datetype:'jsonp',   指定类型
    callback:'callback',  这个函数就是就jQuery里面定义的
    success(e){
        console.log(e)
    }
})
jquery  里面也有这种用法，他认为ajax和jsonp是一样的体验，所以把他归到ajax里面
```



2.代理   优点： 没有任何限制， 确定：运行效率慢，卡法起来比较慢，原理：python具有客户端的能力  应用：爬虫，动态跨域获取信息

```py
Python中的包裹，专门用来处理有关http的信息
from urllib import request
res=request.urlopen('http://www.se')     request对象，urlopen用来读取和打开网页
console.log(res.read()decode('utf8'))  要将结果转化，首先得读取，然后返回二进制，再将其转码，转码格式为utf8
```

script 标签对接受的东西，不管其后缀名是什么，都会当作js去执行

ajax 异步的能力，ajax限制。不能跨域

jsonview

为什么要讲ajax跨域的问题，因为这是常规操作，虽然你现在用的是vue，它里面提供了跨域的功能，但是没有这个运行环境，你还需要使用jsonp和代理的方法。

/ajax/del/+id        /ajax/del/<id>

db.close() 

this.$route.query.id    全局的路由

this.$routes当掐的路由

path   /edit/:id

生命周期   beforecreate    mounted  created

flask两种传参方式  

''/ajax/add?''+id   接受的数据需要用request

"/ajax/add/"    接收数据用 "/ajax/add/<id>"

? 时 query    《》  parmse

ajax上传文件？

link  script    ajax  img  a  form   浏览器格式？

request headers   请求头 response    响应头

响应的时候填写cookie，请求的时候没有，但再次请求的时候，相应的没有，请求的会带着cookie

Mozilla  火狐浏览器

```p
res=make_response(res)
res.headers["set-cookie"]="aa=bb"
return res_cookie("aa","bb")

def a()

request.cookies.get('aa')


生命周期     浏览器开关
```

哈希算法    不可逆的加密方式   123456->&&&&&&&&   只能从左到右

python   hashlib     md5  32位

```py
import hashlib
md5=hashlib.md5()
md5.update(b"zhangsan")
print(md5.digest())
print(md5.hexdigest())
encodeupass）
几的加name
```

validata 

insert into stu  （uanme，upass）values（%s，%s），（uname，upass）

session   依赖于cookie  

用来管理组件之间的信息传递

state   数据  状态

mutation  放方法的

scoped     指定类名

/query    ？parmes

vue整个数据和视图绑定的受

### vue自定义指令

```py
三种方式
1.创建一个js文件，并且在mian.js中引入，然后用Vue.use() ，添加功能
	focus.js文件
	var obj={}
	obj.install=function(Vue){
        Vue.directive('focus',{
            inserted:function(el){
                el.focus()
            }
        })
	}
	main.js 文件
	import obj from"./assets/focus.js"
	Vue.use(obj)
	然后可以在任意一个组件中使用
2.直接在mian.js中写入
Vue.directive('focus',{
    inserted:function(el){
        el.focus()
    }
})  可以在任意组件中使用
3.直接在组建里面写，这是局部定义指令
	directives:{
        focus:{
            inserted:function(el){
                el.focus()
            }
        }
	}
```

blueprint

```py
from flask import Blueprint
head=Blueprint('head',__name__)
@head.route('/addhead')
在url副本中引入，声明

from url.head   import head 
app.register_blueprint(head,url_prefix="/ajax/head/")  在主py文件中注册

```

### router-link跳转：

```py
<router-link :to="'/createhead/id='+currentdata.id">创建表节构</router-link>
router.js  中要写  components '/createhead/:id'   
跳转的组件中获取用   this.$route.params.id
<router-link :to="'/createhead?id='+currentdata.id">创建表节构</router-link>
router.js  中要写  components '/createhead'   
跳转的组件中获取用   this.$route.query.id
获取的时候  $route
跳转的时候   $router.push('url')
```

axure    uml  

用例图   实体关系图  类图  这三个属于uml

组织结构图    uml   流程图

需求  调研     竞品分析  需求{功能，流程}   实体图

easyui  bui

request.args.getlist()   获取表单里面的列表值

```py
@app.before_request
def before_request():
	if request.path!='/checklogin':
        if  not session.get("login") or request.path!='/login':
            	return redirect ('/')
        else:
            return redirect('/login')
@app.route('/login')
def login():
	return render_template('login.html')
```

```py
json.load(file)
嵌套路由
children:[
    path:'',    设置成空的，就可以一起显示，如果设置为其他的，需要在地址栏手动输入
    
]{
    path:''
}
arr=[cname,step,part]    json.strigfy()
```

