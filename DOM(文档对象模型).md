#  DOM(文档对象模型)   fullpage   iscroll   swiper

## 获取元素：

> 外部引入js要在js文件中加入window.onload=function(){}

- 获取ID名的元素

  ```js
  let box=document.getElementById("idName(id名)");
  ```

- 获取类名的元素   是集合  有下标  从0开始  获取回来的是一个集合，所以自己要写清楚用哪一个

  ```js
  let obj=document.getElementsByClassName("className");
  ```

- 获取标签名的元素  集合   下标  遍历

  ```js
  let obj=document.getElementsByTagName("tagName");
  ```

- 指定范围获取元素

  ```js
  let obj1=obj.getElementByclassName(obj)
  ```

- 获取选择器选中的第一个元素

  ```js
  let  obj=document.querySelector("选择器");
  ```

- ###### 获取选择器选中的集合   下标  可用forEach

  ```js
  let obj=document.querySelectorAll("选择器");
  ```


## 操作属性：

#### 标准属性：obj.attr

#### 自定义属性：

- 获取：obj.getAttribute(name)
- 设置：obj.setAttribute(name,value)

## 操作样式：

### 获取：

- 行内样式：obj.style.attr     attr 为高度，宽度等具体样式
- css样式:getComputedStyle(obj,null).attr   也可以获取行内样式    简称通用

### 设置：

- 行内样式：!!!!!!!

  ```js
  obj.style.属性名=属性值
  ```

- 批量样式：？

  ```js
  obj.className="box"？
  obj.classList.add("box")  添加类
  obj.classList.remove("box")  删除类
  obj.classList.toggle("box") 切换类
  obj.id="box"
  ```

- 事件：

  事件源.事件=事件处理函数

### 操作内容：    这里的适用范围是标签之间的内容

- InnerText   元素内容
- innerHTML:识别标签对

### 元素的尺寸和位置:

- obj.offsetWidth:获取元素的真实宽度（width+padding+border）

- obj.offsetHeight:获取元素的真实高度(height+padding+border)

- obj.offsetTop:获取元素外边框距离有定位属性的父元素内边框的垂直间距

- obj.offsetLeft:获取元素外边框距离有定位属性的父元素内边框的水平间距

- obj.scrollTop:有滚动条的元素，浏览器滚动式在垂直方向的拉伸距离   有关滚动元素的事件，要写在滚动函数里即window.onscroll=function(){

  }

  ```js
  document.body.scrollTop||document.documentElement.scrollTop
  ```
  document.documentElement  :html      document.body:   body

- obj.scrollLeft:有滚动条的元素，浏览器滚动时在水平方向的拉伸距离

实时获取浏览器宽高

```js
 window.onresize=function(){
            maxWidth=innerWidth;
            maxHeight=innerHeight;
   }
```

动态创建元素

```js
document.creatElement("TagName");
```

添加类名

插入到页面中

```js
父元素.appendchild(子元素)
document.body.appendChild(div);
```

### 懒加载：

- 获取浏览器高度

- 获取楼层高度（楼层距离顶部的距离：`obj.offsetTop`）

- 获取滚动条高度 

  ```js
  document.body.scrollTop||document.documentElement.scrollTop
  ```

- 浏览器高度+滚动条高度>楼层高度时，图片出现（那就应该首先隐藏图片，即将图片的src属性设置为自定义属性，然后再出现时，将图片的标准属性赋值为自定义属性）

#### 楼层移动（根据楼层的高度改变固定定位的楼层）：可以当图片加载时，给楼层设置背景色，楼层点击事件，可以把楼层的高度赋值给滚动条。

### 时间处理函数：

```js
fn();
setInterval(fn,1000);
function  fn(){
	let arr=[];
  	let now=new Date();
    let future=new Date(2018,9,1);
    let times=Math.floor((future.getTime()-now.getTime())/1000);
    let month=Math.floor(times/(30*24*60*60));
    times=times%(30*24*60*60);
    arr.push(month);
    let day=Math.floor(times/(24*60*60));
    times=times%(24*60*60);
    arr.push(day);
    let hour=Math.floor(times/(60*60));
    times=times%(60*60);
    arr.push(hour);
    let minute=Math.floor(times/60);
    times=times%60;
    arr.push(minute);
    let second=Math.floor(times%60);
    if(second<=9){
    second="0"+second;
     }
     arr.push(second);
     let span=document.querySelectorAll("span");
     span.forEach(function(element,index){
         element.innerText=arr[index];
         });
  }
```



## BOM(浏览器对象模型）

> 完成窗口与窗口之间的通信。`window`对象是其核心对象。
>
> - #### history对象
>
> - #### location
>
> - #### dom
>
> - #### screen
>
> - #### framse
>
> - #### navigation

### window对象：默认核心对象，window可以省略不写

#### 属性：

- 浏览器宽高
  - -window.innerWidth  获取浏览器宽度   (IE8以上版本)  （能见屏幕的高度，不是内容设置的高度）
  - -window.innerHeight  获取浏览器高度
  - document.documetElement.clientWidth  获取浏览器宽度  （IE8以下）
  - document.documetElement.clientHeight  获取浏览器高度
- 浏览器左上角句屏幕左上角的偏移量
  - window.screenTop 垂直偏移量
  - window.screenLeft 水平偏移量

#### 方法：

- alert()   弹出框

- prompt()   输入框

- confirm()   确定与取消框

- close()  关闭页面   括号里面写的是自己需要关闭页面的事件源

- open(url(路径))  打开页面  括号里面可以写宽高，即打开页面的宽高  逗号隔开 加个空字符串

  ```js
  window.open("aa.html","","width=,height=")
  ```

- setInterval(fn,1000)    隔一段时间重复不断地执行一个函数  时间毫秒为单位  fn 是一个函数，所以下面要定义一个函数用来调用

- clearInterval(t)   清除时间函数

- setTimeout(fn,1000)   隔一定时间只执行一次函数

- clearTimeout(t)  清除时间函数  

获取表单的值:obj.value

### history对象：？

#### 属性：

- history.length    用来显示历史记录的长度

#### 方法：

- history.forward()  前进
- history.back) 后退
- history.go(0)  刷新  正值前进，负值后退，一般不用

### location对象:

#### 属性：

- location.href  设置或获取页面地址的   设置即为赋值
- location.host 主机名加端口号
- location.hostname 主机名
- location.port  端口号
- location.protocol 协议
- location.pathname 路径
- location.search 问号后的搜索字段

#### 方法：

- location.reload()  重新加载
- location.replace("history.html")  页面替换，不会增加历史记录
- location.assign("history.html")  页面替换，能够增加历史记录                                                                                                                                                                                                                                                                                                                                                                                   

 charAt()     查找对应字符     括号里面写的是下标

  charCodeAt()      查找对应字符编码

 String.fromCharCode(35299)     将对应字符编码找出来  输入字符串编码，找出对应字符串

str.indexOf()  查找对应字符的下标，如果有的话，返回下标，如果没有，返回-1

### window.onload

```py
window.onload 的意思是等页面所有的东西都加载完成，才会执行里面的东西，计算机是很遵循规矩的，写在上面的代码必然是先执行的，如果你把js代码都放在body上面，并且没有加window.onload的话，他会先执行js，但是这里就会出现问题，你如果要获取元素的话，下面你的代码还没有执行，元素还不存在，你获取的东西就是空的，所以就要在页面加载完成后才能执行js代码
```

contains   是否抱哈n