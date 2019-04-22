## Nginx概述
Nginx是一款轻量级的HTTP服务器，采用事件驱动和异步非阻塞处理方式框架，这让其具有极好的IO性能，市场用于服务端的反向代理和负载均衡
## Nginx优点
- 高并发连接：官方测试Nginx能够支撑5万并发连接，实际生产环境中更可以支撑2~4万并发连接数。
- 内存消耗少：在主流的服务器中Nginx目前是内存消耗最小
- 免费使用可以商业化：开源
- 配置文件简单：网络和程序配置通俗易懂  

## 环境搭建
- 购置服务器
- 阿里云学生优惠服务器(推荐) https://promotion.aliyun.com/ntms/act/campus2018.html?accounttraceid=b580e226-1c85-492e-a500-21116affda2e&userCode=agtj8gav
- 百度云学生优惠服务器 https://cloud.baidu.com/campaign/campus-2018/index.html?unifrom=eventpage

## Ubuntu下载nginx配置（下载最新版nginx）
#### http://nginx.org/en/linux_packages.html#stable （nginx官网）
1. 对于Ubuntu，请将以下内容追加到/etc/apt/source.list文件的末尾
```
deb http://nginx.org/packages/ubuntu/ codename nginx
deb-src http://nginx.org/packages/ubuntu/ codename nginx
```
codename为Ubuntu版本

Version| codename | Supported Platforms
---|---|---
16.04 | xenial|x86_64, i386, ppc64el, aarch64/arm64
17.10 | artful | x86_64, i386
18.04 | bionic | x86_64

2. 更新源
```
apt-get update
```
3. 下载所需密钥，在/etc/apt目录下
```
wget http://nginx.org/keys/nginx_signing.key 
sudo apt-key add nginx_signing.key
```
4. 下载nginx命令
```
sudo apt-get install nginx
# 下载
```

## nginx其他命令
```
sudo apt-get remove nginx nginx-common 
# 卸载删除除了配置文件以外的所有文件。

sudo apt-get purge nginx nginx-common 
# 卸载所有东东，包括删除配置文件。

sudo apt-get autoremove 
# 在上面命令结束后执行，主要是卸载删除Nginx的不再被使用的依赖包。

sudo apt-get remove nginx-full nginx-common 
#卸载删除两个主要的包。

```
```
nginx -V 
# 查看版本 1.14稳定版
nginx 
# 运行
killall nginx
# 终止运行
```
此时浏览器打开 服务器公网ip 可以看到nginx欢迎页面

## uwsgi概述
#### web服务器和web框架
web服务器是用来接收客户端请求，建立连接，转发响应的程序
web框架是处理业务逻辑
举例：
web服务器：nginx
web框架：flask
#### uWSGI和WSGI
WSGI：通信协议
uWSGI：属于WSGI协议的web服务器（nginx、nginx都是web服务器）
#### 为什么需要nginx+uWSGI
利用nginx可以实现反向代理的能力，可以实现分布式服务器功能可以解决网络访问量过大的问题。

#### 安装 pip
一般默认Ubuntu服务器自带python3.5但是却没有自带pip
```
sudo apt-get install python3-pip
```
#### 安装 uwsgi
```
pip3 install uwsgi
```
Django自带wsgi为什么不直接使用，Django自带wsgi只是为了开发使用的是单进程的，不适合上线使用。
#### 在项目根目录（manage.py同目录）下创建 uwsgi.ini 文件
[uwsgi官网](https://uwsgi-docs.readthedocs.io/en/latest/WSGIquickstart.html)
```
[uwsgi]
socket = 127.0.0.1:3031
http= 127.0.0.1:8000
chdir = /home/foobar/myproject/   项目目录
wsgi-file = myproject/wsgi.py   文件目录
processes = 4   进程
threads = 2   线程
stats = 127.0.0.1:9191     查看状态
```
#### 在etc/nginx/conf.d/default.conf 配置nginx
将其中如下代码注释
```
#location / {
#    root   /usr/share/nginx/html;
#    index  index.html index.htm;
#}
```
替换为
```
location / {
     include uwsgi_params;
     uwsgi_pass 127.0.0.1:8080;
}
```
#### 运行Django程序
- 检查项目异常
```
python3 manage.py runserver
```
- 下载项目所依赖包裹
- 安装数据库
```
sudo apt-get install mysql-server
#期间设置数据库密码
```
- setting.py
```
DEBUG = FALSE
ALLOWED_HOSTS = ['*']
```
- url.py
```
+ static(settings.MEDIA_URL, document_root=settings.MEDIA_ROOT)
```
#### 数据库常用命令
```
mysql -u root -p
# 登录数据库
show databases;
# 查看数据库
CREATE DATABASE uaiw1803 DEFAULT CHARACTER SET utf8 COLLATE utf8_general_ci;
# 创建数据库
quit;
# 退出数据库
```
#### 执行迁移
```
python manage.py migrate
```
#### uwsgi运行
```
uwsgi uwsgi.ini
```
到此服务器部署成功，接下来就是设置静态文件了。
#### 设置静态文件
因为此时服务器路由统一由nginx管理，所以我们需要进行配置nginx，etc/nginx/conf.d/default.conf
```
location  /static {
    autoindex on;
    alias  /home/ydh/<项目根目录>/static;
}
```
#### 将项目中的文件同一管理
- 在项目settion.py中设置STATIC_ROOT 静态文件根目录
```
STATIC_ROOT = os.path.join(BASE_DIR,'static')
```
- 在项目根目录创建 static
- 执行命令
```
python3 manage.py collectstatic
# 将静态文件收集到STATIC_ROOT
```
#### 重启nginx
```
killall nginx
nginx
```

```py
[uwsgi]
socket = 127.0.0.1:3031
http= 127.0.0.1:8000
chdir = /home/foobar/myproject/   项目目录
wsgi-file = myproject/wsgi.py   文件目录
processes = 4   进程
threads = 2   线程
stats = 127.0.0.1:9191     查看状态
```



部署服务器事项：

- 上传项目，需要用到软件WinSCP，

- 下载数据库

- 下载pip

- 自带python 不需要下载

- 下载所要用到的依赖包

- 修改配置文件

  - debug 为false
  - ALLOWED_HOSTS = ['*']，这是为了让所有的局域网可以访问

- 创建数据库，迁移数据表

- 把静态文件全部放到根目录下面，创建一个static文件夹

- 运行的时候把局域网改为0.0.0.0：8000

- 在根目录下面写个uwsgi.ini 文件

  ```py
  [uwsgi]
  socket = 127.0.0.1:8000    端口号，本来nginx可以直接用，但是uwsgi把项目和nginx联系起来，相当于是一个接口
  http= 127.0.0.1:8000   设置这个的话，就相当于是一个服务器，不是中间链接的啦   和socket只能有一个
  chdir = /home/foobar/myproject/   项目目录   项目放在那里
  wsgi-file = myproject/wsgi.py   文件目录    uwsgi文件在哪
  processes = 4   进程
  threads = 2   线程
  stats = 127.0.0.1:9191     查看状态   一般可以注释掉
  ```

- 修改nginx的配置

- 运行nginx

- 运行uwsgi

静态文件的设置方法：

```py
一个是  debug  改为ture
另一个是  用pycharm 远程连接  在 tools/Depment/configuration 添加远程链接
```

