## flask

/show/{{item.id}}   传递数据

/show/<id>  接收数据

### 让浏览器解析html     需要使用接受符号  {%data ['id']| safe%}   而且必须写上管道 保证安全 safe   

fetchall 与feachone 的区别     

最重要的区别是前者是数组，后者是对象，直接是json格式

前者可能包含很多的id  ，他可以输出同一个表中的素有id，后者只有一个id，他可以输出同一个id里面的所有东西  

jquery 获取的是表单里面的值   serialize  得到的是字符串   serializeArray  得到的是数组，并且里面的是json对象格式

JSON.stringify(value[, replacer [, space]]) 

**该函数的作用是：系列化对象** 
**系列化对象说白了就是把对象的类型转换为字符串类型**

value 
 将要序列化成 一个JSON 字符串的值。

 

数组

函数

 

1. 如果为**数组**：则只有包含在这个数组中的属性名才会被序列化到最终的 JSON 字符串中，replacer作key值（这个在讲实例的时候就知道这个key是干嘛的了，先记住就好）
2. 如果为**函数**：则把系列化后的每一个对象（记住是每一个）传进方法里面进行处理

 

缩进

 

1. 如果省略的话，那么显示出来的值就没有分隔符。直接输出来 
2. 如果是一个数字的话，那么它就定义缩进几个字符，范围是：0到10（数字小于1，则默认为0，大于10，则默认为10）
3. 如果是一些转义字符，比如“\t”，表示回车，那么它每行一个回车。 
4. 如果仅仅是字符串，就在每行输出值的时候把这些字符串附加上去就OK。当然，最大长度也是10个字符

 json.load  读取文件   json.loads  读取字符串

### flask session:

```py
这是一种安全传递信息的方式
首先实在flask环境下
需要引入flask_session import Session
app.serect_key="123456"

#secret_key
如果设置了密钥，则加密组件可以使用此密钥来签署cookie和其他内容。如果要使用安全cookie，请将此值设置为复杂的随机值。
也可以使用SECRET_KEY配置密钥从配置中配置此属性 。默认为None。可以认为是一种解密方式

app.config['SESSION_FILE_DIR']="/home/zkw/PycharmProjects/Vue"
指定文件存储的位置
app.config['SESSION_TYPE']='filesystem'
指定数据存储的类型
Session(app)
运行session    
session['aa']='bb'   设置session
session.get('aa')='bb'  获取session
```

### redirect 里面写的是路径，服务器下的路径，跳转的意思

云之讯    短信码验证   高并发     

发展环境下的服务器

生产环境下的服务器    apache   iis uwsgi  

外键？  数据库   索引  引擎  

phpadmin     

navicat    

element.io

--open  serve

vue添加插件是用Vue.use()

```py
var obj={}
obj.install=function(Vue,parmes){
    Vue.pro.abc=function(){
        alert(parmes,s)
    }
}
Vue.use(obj,{aa:"bb"})
```

vh 屏幕赞比  分成一百分，1vh就是占1%

contextmenu.prevent.stop      阻止浏览器默认行为，阻止冒泡

$.event  获取鼠标位置

$refs   ?

@app.errorhandler(404)

def error(error)

​	return redirect()

​	return 'error'

​	return render_template('index.html')

### 错误：

```py
Failed to load resource: the server responded with a status of 404 (Not Found) favicon.ico文件找不到


[Thu May 11 16:40:06 2017] [error] [client ::1] File does not exist: D:/wamp/www/favicon.ico, referer: http://localhost/js/test.html

仔细对照路径查看确实没有favicon.ico文件，后来查了相关的资料才知道，这是浏览器自动加载的，浏览器一般自动在网站根目录寻找，就是你页面卡片那个图标。

favicon.ico意指你的网站图标。 当有人（使用IE浏览器）将你的网站收藏为“my favorite”时，就会去参照网站根目录下的“favicon.ico”文件，这个图标也就是“my favorite”里显示的图标。 
比如你将“http://www.debian.org/”列为“my favorite”的时候，你的“my favorite”清单会显示“http://www.debian.org/favicon.ico”这个图标。 
当你的根目录下没有“favicon.ico”这个文件时，“my favorite”里将显示IE浏览器的图标，与此同时“favicon.ico”不存在的信息（404 not found）会写到你的apache2错误日志中去，这样你可以从这个日志中看出，什么时候，什么人（其IP网址）将你的网站设定为“my favorite”。

解决的方法：

1、做个favicon.ico文件放在根目录下，在head标签引入favicon.ico文件即可

<link href="favicon.ico" rel="shortcut icon">
2、在Stack Overflow搜索到的，直接在head标签插入以下代码也OK

 <link rel="shortcut icon" href="#" />
```

### flask接收参数的两种方式：

```py
'?id={{item.id}}'   后面需要接受，用 get方式
"/{{item.id}}"   后面需要写 <rid> 函数传参数(rid)  然后直接用就可以
```

overflow :auto

换行读取excel表

http下载

如何上传

lxrd 读取excel表

xlwd   写表

### render_template传递数据：

```py
return render_template('index.html', datas={'menu': menus, 'rname': session.get('rname')})
可以是字典
return render_template('/user/select.html', datas=result)
也可以是变量

在前端里面要用{{}}  语法接受
```

### python中hashlib算法：

```py
md5 = hashlib.md5()
md5.update(pw.encode('utf8'))
pw = md5.hexdigest()
在你注册的时候，你需要将其转换为不认识的编码，进而在保存在数据库中，而在登陆，你就需要讲前端获取回来的数据进行编码，与数据库中的密码相比较
```

### 登陆注册：

```py
@app.before_request    这里面的意思是在客户端向服务器发起请求时，过程中就要进行判断，如果说你服务器已经把页面给你返回，而且你还带着cookie，在网址中
def before_request():
    if request.path != '/checklogin':
        if request.path != '/logina/login' and not session.get('login'):
            return redirect('/logina/login')
```

```py
f=oepn('/download/1.txt','w')
con=f.read()
f.close()
res=make_response(con)'
res.headers['content-disposition']='attachment;filename=2.txt'


res=make_response(send_from_directory('download','1.txt',as_attachment=True))'
res.headers['content-disposition']='attachment;filename=2.txt'

指定method为post    request。files【‘file’】
entycpe=file+++
file.save('a.xlsx')  上传到当前路径
secury.filename(file.filename)
book=xlrd.open_w(a.xla)
sheet=book.sheet_by_index(0)      sheet=book.sheet_by_name(0) 可以通过name获取
sheet.row_values(0)
sheet.nrows   获取他的行数

批量插入数据   
cursor.executemany()
arr=[]
for item in range(1,sheet.nrows):
	con=sheet.row_values(item)
	cid=db.insert_id()
	step=con(1).split('\n')
	for index in range(len(step)):
		arr.append((step[index],part[index],cid))
	cursor.executemany('insert into category_info (step,part,cid) valuse(%s,%s,%s)',(arr))
	db.commit()
```

action    dreamviwer   自动生成代码



xlrd   文件   表   行  单元格      

PIL pillow  处理图形图像信息    python第三方包    base64格式  图片

opengl    计算机最底层的处理工具      

css3   html5    canvas       webgl 三维

pathWrite {

}

```py
fetch('/ajax/url',{
    credentials:"include"   默认不带cookie，要设置为带
})
res=make_response(redirect('/'))
res.headers['Acess-controll-Allow-Credential']='true'
return res
action='/ajax/cursor/update'
multiply    
```

上传文件必须要用post方式接受

location.pathname   路径

category=$('select [name=category]'.val())

url=path+'?'+parms

location.href=url

刚开始 category=''

timecon='and data _format(logs.time)'+'''+time      if time lese  ''     

limit  5,5  分页

request.url    获取地址兰信息

```py
def pages(total,pageNum):
	if request.url.find('?')<0:
		url=request.url+'?page='
	else:
		if request.url.find('page')<0:
			url=request.url+'&page='
		else: 
			url=request.url[0:request.url.rfind('=')+1]
			
	pagenums=math.ceil(total/pageNum)
	currentpage=int(requset.args.get('page') or 0)
	pagestr=''
	pagestr+='共%s页'%(pagenums)
	pagestr+='<a href="%s">首页</a>'%(url+'0')
	start=currentpage-2 if currentpage-2>0 else 0
	end=start+4 if start+4<pagenums else pagenum-1
	foritem in range(start,end+1):
		if currentpage==item:
			pagestr+='<a href="%s" style="color:">[%s]'
	last=current-1 if currentpage-1>0 else 0
	pagestr+='<a href="%s">上一页</a>'%(url+str(last))
	
	next=current+1 if currentpage+1<pagenum else pagenum-1
	pagestr+='<a href="%s">上一页</a>'%(url+str(last))
	
	pagestr+='<a href="%s">首页</a>'%(url+str(pagenums-1))
	limit='limit '+str()
```

富文本编辑   验证码    ckeditor   

cdn   内容分发网络   缓存   路有缓存   dns 缓存    其他dns   美国   地址   返回

webpack    ？   jade   node。js 的模板引擎    package.json    

创建于个项目

```py
package.json:
里面的配置项
npm install
会放到根目录下的node——moduels
npm install --save\

webpack.congig。js  创建  复制
创建src    拷贝包裹
创建app。js

在   webpack.congig。js  里面设置入口  出口    entry   output
path=require('path')
entry:'./app.js'
output  :
	path: path.resolve(__dirname, 'dist'),
    filename: 'my-first-webpack.bundle.js'
 scripts:  build  webpack --mode development
 
 npm run build   
 
 
 npm init 创建一个包说明文件   package.json
 把编辑器功能的组件 放到 package。json作为以来安装
 安装 webpack 以及webpack的依赖项
 配置webpack的选项
 写自己的配置文件
 写自己的入口文件
 运行webpack命令
 修改配置
 按照webpack制定的output 路径和文件名，输入相应的编译好的文件
 按照规范引入js
 动态的添加或删除相应的功能
 删除：把相应的组件和依赖删掉
 添加：到  features  找到相应的路径 按照步骤更改
```

postcss    解构   

path。join     ‘/a/  ‘/b’     python  node都有



express        

下载  npm install    救远     找 ，就近    flask是什么

npm官网

图片要存储在服务器上，再将地址存储进数据库

res

str(random.randint(1,2000))+"." + res.filename.rsplit('.'[1])

uploaded       url     save("."+path)