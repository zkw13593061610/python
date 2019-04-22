## Django  

### 入门：

#### 下载Django

```py
pip install django
```



#### 创建Django应用

```py
django-admin startproject mysite
```

#### Django目录介绍

##### mysite

```py
__init.py    配置文件
settings.py    配置文件
urls.py     路由文件
wsgi.py   服务器文件
```

##### manage.py   django指令

##### python manage.py startapp polls （应用名）

##### mysite    

- mysite   项目包
- polls   应用包
  - migrations   迁移文件包
  - __init__.py
  - admin.py   自定义后台界面
  - apps.py    应用配置，主要设置应用名称
  - models.py   数据模型  (创建表以及表的结构)
  - tests.py    
  - views.py   视图  （逻辑，其实就是控制器）
- manage.py   工具文件

##### 配置项：

- #语言

  ```
  LANGUAGE_CODE = 'zh-hans'
  ```

- 时区

  ```py
  TIME_ZONE = 'Asia/Shanghai'
  ```

- 应用

  ```py
  INSTALLED_APPS = [
      'django.contrib.admin',
      'django.contrib.auth',
      'django.contrib.contenttypes',
      'django.contrib.sessions',
      'django.contrib.messages',
      'django.contrib.staticfiles',
      'polls'
  ]
  ```

- 数据库

  ```py
  DATABASES = {
      'default': {
          'ENGINE': 'django.db.backends.sqlite3',
          'NAME': os.path.join(BASE_DIR, 'db.sqlite3'),
      }
  }
  ```

### 创建第一个视图：

- 在应用视图文件中创建视图函数（views.py）

  ```py
  from django.shortcuts import render
  from django.http import HttpResponse
  # Create your views here.
  def index(request):
      return HttpResponse("123")
  ```

- 在应用中创建路由文件（urls.py）

  ```py
  from django.urls import path
  from . import views
  urlpatterns = [
      path('',views.index),
  ]
  ```

- 在项目文件包中导入应用路由(mysite/polls)

  ```py
  from django.contrib import admin
  from django.urls import path,include
  urlpatterns = [
      path('admin/', admin.site.urls),
      path('polls/', include("polls.urls")),
  ]
  
  ```

### 配置数据库：

```py
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'polls',
        'HOST': 'localhost',
        'PORT': '3306',
        'USER': 'root',
        'PASSWORD': '123456'
    }
}
```

##### pymysql 配置：

mysite/__init.py

```py
import pymysql

pymysql.install_as_MySQLdb()
```

##### 创建数据库：polls/models

```py
from django.db import models
这里面的模型 ，其实都是数据库需要存储的数据
# Create your models here.


class Question(models.Model):
    question_text = models.CharField(max_length=200)
    pub_date = models.DateTimeField()


class Choice(models.Model):
    question = models.ForeignKey(to=Question, on_delete=models.CASCADE)
    choice_text = models.CharField(max_length=200)
    votes = models.IntegerField(default=0)
    
    
代码非常直白。每个模型被表示为 django.db.models.Model 类的子类。每个模型有一些类变量，它们都表示模型里的一个数据库字段。
每个字段都是 Field 类的实例 - 比如，字符字段被表示为 CharField ，日期时间字段被表示为 DateTimeField 。这将告诉 Django 每个字段要处理的数据类型。
每个 Field 类实例变量的名字（例如 question_text 或 pub_date ）也是字段名，所以最好使用对机器友好的格式。你将会在 Python 代码里使用它们，而数据库会将它们作为列名。
定义某些 Field 类实例需要参数。例如 CharField 需要一个 max_length 参数。这个参数的用处不止于用来定义数据库结构，也用于验证数据，我们稍后将会看到这方面的内容。

Field 也能够接收多个可选参数；在上面的例子中：我们将 votes 的 default 也就是默认值，设为0。

注意在最后，我们使用 ForeignKey 定义了一个关系。这将告诉 Django，每个 Choice 对象都关联到一个 Question 对象。Django 支持所有常用的数据库关系：多对一、多对多和一对一。
```

##### 创建迁移文件：就是把模型放到迁移文件里面，这里应该把你写的python语言转换成了mysql语言

```py
 python manage.py makemigrations polls
```

##### 执行迁移文件：就是把数据放到数据库里，

```py
python manage.py migrate
```

### 创建站点：

```py
python manage.py createsuperuser     创建用户
```

```py
首页，列表页，详情页    开通博客，申请通过        管理用户    管理文章   个人信息管理  审批管理   分类管理        前台   主页，详情页  关注   管理分类
```

```py
from django.db import models
class MyBaseModel(models):
	add_   models.DatetimeField(auto_  =True)
	update
	delete    models.InterField
	
	class Meta():
		abstract = True
```

```py
objects.create(name=name,)
```

数据的处理

```py
def index(request):
    # return JsonResponse({'name': 'zkw'})
    banji = Class.objects.all()
    student = Student.objects.all()
    if request.method == 'GET':
        return render(request, 'demo/index.html', {'banji': banji,'student': student})
    else:
        name = request.POST.get('name', None)
        tel = request.POST.get('tel', None)
        c = request.POST.get('c', None)
        c = Class.objects.filter(id=c).first()
        Student.objects.create(name=name, tel=tel, c=c)
        return render(request, 'demo/index.html', {'banji': banji, 'student': student})
        数据的增加，用create，数据的保存与修改，用save
        
 增加   有两种方式
 1. Student.objects.create(name=name, tel=tel, c=c)
 2.obj = Student(name=name,tel=tel,c=c)
 	obj.save()
 	
更新     
	Student.objects.filter(id=id).update(name=name)
删除 
    Student.objects.filter(id=id).delete()
```

更新[`ManyToManyField`](https://docs.djangoproject.com/zh-hans/2.1/ref/models/fields/#django.db.models.ManyToManyField)工作的方式略有不同 - 使用 [`add()`](https://docs.djangoproject.com/zh-hans/2.1/ref/models/relations/#django.db.models.fields.related.RelatedManager.add)字段上的方法向关系添加记录。此示例将`Author`实例 添加`joe`到`entry`对象： 

```py
from blog.models import Author
>>> joe = Author.objects.create(name="Joe")
>>> entry.authors.add(joe)
```

要[`ManyToManyField`](https://docs.djangoproject.com/zh-hans/2.1/ref/models/fields/#django.db.models.ManyToManyField)一次性添加多个记录，请在调用中包含多个参数 [`add()`](https://docs.djangoproject.com/zh-hans/2.1/ref/models/relations/#django.db.models.fields.related.RelatedManager.add)，如下所示： 

```py
>>> john = Author.objects.create(name="John")
>>> paul = Author.objects.create(name="Paul")
>>> george = Author.objects.create(name="George")
>>> ringo = Author.objects.create(name="Ringo")
>>> entry.authors.add(john, paul, george, ringo)
```

检索对象：

```py
从表中检索对象的最简单方法是获取所有这些对象。为此，请使用以下all()方法 Manager：
该all()方法返回 QuerySet数据库中所有对象的一个。
filter(**kwargs)
返回QuerySet包含与给定查找参数匹配的新对象。
exclude(**kwargs)
返回QuerySet包含与给定查找参数不匹配的新对象。
用get()检索单个对象
使用Python的数组切片语法的子集将您限制 QuerySet为一定数量的结果。这相当于SQL LIMIT和OFFSET子句。

例如，这将返回前5个对象（）：LIMIT 5

>>> Entry.objects.all()[:5]
```



distinct   去重

在一个应用中，会有很多的html页面，为了防止另一个应用中也有相同的页面名称，所以要在这个项目中建立一个templates文件夹，里面在建立一个文件夹与项目名称相同

![img](https://img-blog.csdn.net/20171210024421008?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvYmFpZHVfMjQ1NDU5MDE=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center) 

加载静态变量：

```py
{% load static %}
<script  src="{% static '/demo/js/jquery.js' %}">
```

静态文件：

```py
需要创建templates和static，然后里面都需要demo文件夹
```

```py
blank,nulls
```

```py
*    
```

基类，因为常用，创建一个包

```py

```

```py
django.core.exception import Validation     
except VlidationError as e:
	message = e
obj.full_clean
```

验证器：

```py
def nihao(value):
	if value[0:4]!='abc':
	    raise ValidationErroe('信息')
	    
validators = [nihao]


验证参数message,  code 
```

自定义验证器：

```py
from django.core.exceptions import ValidationError   导入报错包裹


def validate_name(value):    定义报错函数
    if value[0:3] != 'abc':
        raise ValidationError('不正确')
class User(models.Model):
    name = models.CharField(max_length=10,validators=[
        validate_name    定义报错字段，调用这个函数，但不需要传参数
    ])
    del_id = models.BooleanField(default=False)
    sex = models.CharField(
        choices=(
            ('0','男'),
            ('1','女')
        ),
        max_length=10,
        default='1'
    )
    email = models.EmailField(default=None)

    c = models.ForeignKey(to=Identify, on_delete=models.CASCADE)

    def __str__(self):
        return self.name
```

内置验证器：

```py
from django.core.validators import RegexValidator   导入内置验证器，里面有很多的验证器
class User(models.Model):
    name = models.CharField(max_length=10,error_messages=(
        {'m1':'必须以abc开头(0)','m2':'必须以abc结尾(1)'}
    ),validators=[
        RegexValidator(regex='abc$', message='必须以abc结尾',code='m2'),
        RegexValidator(regex='^abc', message='必须以abc开头', code='m1'),
        那句话写在前面，就会先执行那句话
    ])
    del_id = models.BooleanField(default=False)
    sex = models.CharField(
        choices=(
            ('0','男'),
            ('1','女')
        ),
        max_length=10,
        default='1'
    )
    email = models.EmailField(default=None)

    c = models.ForeignKey(to=Identify, on_delete=models.CASCADE)

    def __str__(self):
        return self.name

```

### 有关admin的：

#### 创建用户：

```py
python manage.py createsuperuser
```

#### 设置里面的用户：

在models里面需要写入模型

在admin里面写入类，注册一下两个表：

```py
from django.contrib import admin
from .models import User,Identify    从模型中引入两个模型
# Register your models here.


@admin.register(Identify)       注册有两种方式   一种是装饰器
class Idenadmin(admin.ModelAdmin):
    fields = ['name']


class Useradmin(admin.ModelAdmin):
    fields = ['name','del_id','sex','email','c']


admin.site.register(User,Useradmin)  另一种是直接注册，前面是模型，后面是这个用户
```

### Django里面有三种关系

一对一

#### 一对多：

```py
一般需要用外键来实现
如您所料，ForeignKey和ManyToManyField模型字段类型是特殊情况：

ForeignKey由...表示django.forms.ModelChoiceField，ChoiceField其选择是模型QuerySet。
ManyToManyField由...表示 django.forms.ModelMultipleChoiceField， MultipleChoiceField其选择是模型QuerySet。
此外，每个生成的表单字段都具有如下设置的属性：

如果模型字段有blank=True，则在表单字段上required设置 False。否则，required=True。
表单字段label设置为verbose_name模型字段，第一个字符大写。
表单字段help_text设置为help_text模型字段的字段。
如果模型字段已choices设置，则表单字段widget 将设置为Select，其中选项来自模型字段 choices。选项通常包括默认选择的空白选项。如果该字段是必需的，则强制用户进行选择。如果模型字段具有blank=False显式default值（default将最初选择该 值，则不包括空白选项）。

```

```py
h2 | safe    这种类型的就叫过滤器
{% csrf_token %}  jinjia标签（jinjia函数，必须有返回值）      csrf_token  这叫跨域令牌   解决问题：跨域问题    如何解决：    help_text     'required':'必填'
as_p  作为p标签 as_table    as_ul
widget = forms.PasswordInput(attrs={'class':''})
form.cleaned_data   表单的数据     help_text    forms.username.label_tag
```

``` py
class Adduser(forms.ModelForm):
	class Mata:
		model = User
		fields = "__all__"   这里是一个集合  ['username']
		exclude =['password']
        widgets ={
            'username':forms.TxetInut(attrs={'class':''}),
             'password':forms.PasswordInut(attrs={'class':''})
        }
        labels={
            'username':'用户名',
            'password':'密码'
        }
        error_messages={
            'name':{'required':'必填'}
        }
```

```py
obj = forms.save(commit=False)   保存到内存中，不会提交到数据库,返回一个对象
obj.password = '123456'   设置对象的属性
obj.save()   保存对象

save    可以保存一对一，一对多，多对多，
注意点：再多对多中，如果使用了  save(commit=False) ,还需要执行一下forms.save_m2m()
```

```py
博客系统：平台，个人模块，登陆注册
平台：前台，后太
前台：首页，详情页，列表页
后台：审核用户，用户管理，文章审核，个人信息，管理文章（增，删，改），分类管理
个人模块：个人文章的增删改查，个人评论的管理，个人信息管理，个人分类管理，关注管理
```

管理站点：

list-display:

```py
设置list_display为控制在管理员的更改列表页面上显示的字段。如果未设置list_display，管理站点将显示一列，显示__str__()每个对象的表示形式。
注意点：
    如果字段是a ForeignKey，Django将显示 __str__()相关对象。
    ManyToManyField不支持字段，因为这将需要为表中的每一行执行单独的SQL语句。如果您想要这样做，请为您的模型提供自定义方法，并将该方法的名称添加到list_display。（有关自定义方法的更多信息，请参见下文list_display。）

    如果字段是a BooleanField，Django将显示一个漂亮的“开”或“关”图标而不是True或False。

    如果给定的字符串是模型的方法，ModelAdmin或者是可调用的，Django将默认HTML转义输出。要逃避用户输入并允许您自己的非转义标签，请使用 format_html()。
```

AdminSite：更改站点的信息

```py
AdminSite.site_header
放在每个管理页面顶部的文本，作为<h1>（字符串）。默认情况下，这是“Django管理”。

AdminSite.site_title
放在每个管理页面末尾的文本<title>（一个字符串）。默认情况下，这是“Django站点管理员”。

AdminSite.site_url
每个管理页面顶部“查看网站”链接的URL。默认情况下 site_url是/。将其设置None为删除链接。

对于在子路径上运行的站点，该each_context()方法检查当前请求是否已request.META['SCRIPT_NAME']设置，如果site_url未设置为其他值，则使用该值/。

AdminSite.index_title
放在管理员索引页面顶部的文本（字符串）。默认情况下，这是“站点管理”。

AdminSite.index_template
管理站点主索引视图将使用的自定义模板的路径。

AdminSite.app_index_template
管理网站应用程序索引视图将使用的自定义模板的路径。

AdminSite.empty_value_display
用于在管理站点的更改列表中显示空值的字符串。默认为短划线。通过在字段上设置属性，还可以在每个ModelAdmin基础上和在自定义字段内覆盖该值 。请参阅 示例。ModelAdminempty_value_displayModelAdmin.empty_value_display

AdminSite.login_template
管理站点登录视图将使用的自定义模板的路径。

AdminSite.login_form
AuthenticationForm管理站点登录视图将使用该子类。

AdminSite.logout_template
管理站点注销视图将使用的自定义模板的路径。

AdminSite.password_change_template
管理站点密码更改视图将使用的自定义模板的路径。

AdminSite.password_change_done_template
管理站点密码更改完成视图将使用的自定义模板的路径。
```

将字符串写成html语言：

```py
from django.utils.html import format_html

    def listKeyword(self):
        objs = self.keyword_set.all()
        arr = []
        for item in objs:
            arr.append('<e style="margin:3px">'+item.name+'</e>')
        return format_html("".join(arr))
    listKeyword.short_description = '关键字'   这里是关键字
```

导入模板:

```py
{% include 'pingtai_muban/index_list.html'  %}
```

cookie:

```py
res = HttpResponse（'123'）
res.set_cookies('eje','122',)
res.delete_cookie("")



保存在数据库
request.session['ydh'] = '21111'
res = HttpResponse(resquest.session.session_key)
return res
```

### Djaong Cookie、Session使用 :

#### Cookie:

```py
cookies
获取cookies   request.COOKIES['username']
设置cookie      response.set_cookie('key','value',max_length=秒钟,expires=日期)
path="/" 那个页面下可以使用cookie
domain  =""  生效的域名
secure = False https传输
httponly = js中获取不到
```

#### Session:

分为几种：

- 数据库（默认）
- 缓存
- 文件
- 缓存+数据库
- 加密cookie

#### 数据库 Session:

```py
 SESSION_ENGINE = 'django.contrib.sessions.backends.db'   # 引擎（默认）
```

#### 其他公共配置:

```py
SESSION_COOKIE_NAME ＝ "sessionid"                       # Session的cookie保存在浏览器上时的key，即：sessionid＝随机字符串（默认）
    SESSION_COOKIE_PATH ＝ "/"                               # Session的cookie保存的路径（默认）
    SESSION_COOKIE_DOMAIN = None                             # Session的cookie保存的域名（默认）
    SESSION_COOKIE_SECURE = False                            # 是否Https传输cookie（默认）
    SESSION_COOKIE_HTTPONLY = True                           # 是否Session的cookie只支持http传输（默认）
    SESSION_COOKIE_AGE = 1209600                             # Session的cookie失效日期（2周）（默认）
    SESSION_EXPIRE_AT_BROWSER_CLOSE = False                  # 是否关闭浏览器使得Session过期（默认）
    SESSION_SAVE_EVERY_REQUEST = False                       # 是否每次请求都保存Session，默认修改之后才保存（默认）
```

#### session使用:

```py
#使用
        def index(request):
            # 获取、设置、删除Session中数据
            request.session['k1'] = 'ydh' # 设置
            request.session.get('k1',None)
            request.session['k1'] = 123
            request.session.setdefault('k1',123) # 存在则不设置
            del request.session['k1']
     
            # 所有 键、值、键值对
            request.session.keys()
            request.session.values()
            request.session.items()
            request.session.iterkeys()
            request.session.itervalues()
            request.session.iteritems()
     
     
            # 用户session的随机字符串
            request.session.session_key
     
            # 将所有Session失效日期小于当前日期的数据删除
            request.session.clear_expired()
     
            # 检查 用户session的随机字符串 在数据库中是否
            request.session.exists("session_key")
     
            # 删除当前用户的所有Session数据
            request.session.delete("session_key")
     
            request.session.set_expiry(value)
                * 秒数
                * datatime或timedelta
                * 0,用户关闭浏览器session失效。
```

#### 缓存Session:

```py
 配置：
    SESSION_ENGINE = 'django.contrib.sessions.backends.cache'  # 引擎
    SESSION_CACHE_ALIAS = 'default'                            # 使用的缓存别名（默认内存缓存，也可以是memcache），此处别名依赖缓存的设置
 
```

#### 文件:

```py
   SESSION_ENGINE = 'django.contrib.sessions.backends.file'    # 引擎
    SESSION_FILE_PATH = None                                    # 缓存文件路径，如果为None，则使用tempfile模块获取一个临时地址tempfile.gettempdir()
 
```

#### 缓存+数据库session:

```py
SESSION_ENGINE = 'django.contrib.sessions.backends.cached_db'        # 引擎
```

#### 加密cookie Session:

```py
SESSION_ENGINE = 'django.contrib.sessions.backends.signed_cookies'   # 引擎
```

0000  网络号   11111广播号

```py
list_etiable=
```







{csrfmiddlewaretoken: '{{ csrf_token }}' } 



```py
form django.conf.urls.static iport static
form django.conf import settings

部署服务器时，整合静态文件地址，以便服务器统一管理
static_root = '/static/'
静态文件加载地址
static_url = os.path.join
staticfiles_dirs=[
    os.path.join(base_dir,'static')
]
上传到项目中文件地址
media_root= os.path.join(base_url,'media')

加载到
media_url=

static(settings.media_url,document_root=settings.media_root)  在主路由中
```

```py
form Djang0.conf import settings
def upload():
	username = request.sesstion.get('username',None)
	if request.is_ajax():
		img = request.FILES.get('img',None)
		name = os.path.join(settings.MEDIA_URL,'touxiang',img.name)
		if img:
			with open(name,'wb+') as f: 
				for item in img.chunks():
					f.write(item)
		User.objects.filter(username=username).update(img=name)
	return JsonResponse({'src':name,
	
	
用户表
flower = models.Text(max  65535
star = models.Text(max   65535
平台models  
look 浏览
self.models

```

```py
forloop.counter    序号
re_path    ??
 正则
<script type="text/javascript" src="{% static 'ckeditor/ckeditor-init.js' %}"></script>
<script type="text/javascript" src="{% static 'ckeditor/ckeditor/ckeditor.js' %}"></script>

```

### 中间件：

```py
django.utils.deprecations import MiddleMixin

```

主路由

```[y
from django.contrib import admin
from django.urls import path
from myapp import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('<name>/', views.index),

]

```



![1545987166172](C:\Users\98660\AppData\Local\Temp\1545987166172.png)

```py
settings 的配置
MIDDLEWARE = [
    'myMiddleware.myMiddleware.MyMiddle',
    'myMiddleware.myMiddleware.MyMiddle1',
    'django.middleware.security.SecurityMiddleware',
    'django.contrib.sessions.middleware.SessionMiddleware',
    'django.middleware.common.CommonMiddleware',
    'django.middleware.csrf.CsrfViewMiddleware',
    'django.contrib.auth.middleware.AuthenticationMiddleware',
    'django.contrib.messages.middleware.MessageMiddleware',
    'django.middleware.clickjacking.XFrameOptionsMiddleware',
]
```

```py
包中的类：
from django.utils.deprecation import MiddlewareMixin


class MyMiddle(MiddlewareMixin):

    def process_request(self,request):
        print('请求1')

    def process_response(self,request,response):
        print('响应1')
        return response

    def process_view(self,request,callback,callback_args,callback_kwargs):
        print('view1')
        print(callback)
        print(callback_args)
        print(callback_kwargs)

    def process_exception(self,request,exception):
        print('异常1')


class MyMiddle1(MiddlewareMixin):

    def process_request(self, request):
        print('请求2')

    def process_response(self, request, response):
        print('响应2')
        return response

    def process_view(self, request, callback, callback_args, callback_kwargs):
        print('view2')
        print(callback)
        print(callback_args)
        print(callback_kwargs)

    def process_exception(self, request, exception):
        print('异常2')
        return '1231'


```

render     ，以前的版本是  render_to_response('模板',locals())

locals()  可以把函数中所有的变量都传给模板，可能会有点浪费内存

### django  filter查询：

参数可以传   

- __gt  大于
- __gte 大于等于
- __lt  小于
- __lte  小于等于
- __contains  包含  +i忽略大小写
- __startwith   开头是
- __endswith   结尾是
- __in  其中之一    后面是加[]
- __range   范围
- 日期类型的查询  (create_time__year=2018)

### django model_to_dict方法：  将模型转换为字典

```py
推荐一个好用的django方法，用于将model实例转换为dict，命名非常简单粗暴

from django.forms.models import model_to_dict

di = model_to_dict(order, exclude=［'create_time', 'update_time'］)

源码函数声明：def model_to_dict(instance, fields=None, exclude=None):

其中参数instance是对象实例，fields是指定需要哪些字段，exclude是指定排除哪些字段，exclude比fields优先级高。

```

### django  objects.all(),objects.get() 与object.filter() 区别

```py
all  返回的是queryset对象，程序并没有在数据库中执行sql语句查询数据，但支持迭代，使用for循环可以获取数据
get  返回的是model对象，类型为列表，说明使用get方法会直接执行sql语句获取数据
filter 和get 类似，但支持更强大的查询功能
```

