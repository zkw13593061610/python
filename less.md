less

人的工作效率高一点

机器的工作效率高一点

机器的性能不断提高

摩尔定律

安迪-比尔定律



响应式  

js 动态的实现

css3升级   @media

@media   js的逻辑   放到  css

栅格化的概念

几种不同的尺寸

html+css

css 可以编程

js用作  doc   html+css   js 动态的操作css

js  -不断的升级和发展

js    ->  前端的内容  doc    html +css

扩展    node.js  ->  服务器的

前端的技术提供无数种可能性

nodejs     vue    angular       编程一样去编写css





非阻塞就是单线程异步机制   

耗费时间  和不确定执行的都是异步   

nodejs    

第一步  下载nodejs 官网

第二部   查看   node -v    npm -v

第三部  打开pycharm -setting   

第四部    file watchers

第五步 点击  +

第六步   点击less

program   node  安装路径

c://user

 a       lessc  命令

### less语法：

```py
函数      
if  else   语法
.shadow(@x:0,@y:0,@s:100px,@c:#000,@type:1) when(@type=1) {
    box-shadow:@x @y @c @c;
}
.shadow(@x:0,@y:0,@s:100px,@c:#000,@type:1) when(@type=2) {
    box-shadow:@x @y @c @c inset;
}
.a(@i:1)  when (@i<=12){
    .col -m-@{i}{
        width:@i/12*100%
    }
    .a(@i:@i+1)
}
.a()
div p {
    width:100px;
    $ a{    //$  指定为上面的两个
        width:100px
    }
}
.contanier{
    ${
        width:@width2;
        height:auto;
    }
    $-fluid{
        width:100%
    }
}
```

下载  wget

解压  tar  

软连接    sudo  In -s 地址       /usr/local/bin/node

sudo npm install   -g  less

右上角的不勾选

左下角的最后一个要勾选

