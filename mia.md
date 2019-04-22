我是谁，我是做啥的，面试的是啥，我是大二就开始接触这个方面的东西，项目，平台级，企业级，小程序之类的，元类，排序，正反排序，去重，with的用法，引导面试官

自我介绍？

​	我叫赵堃崴，我来面试咋们公司的python工程师一职

能力？

​	我之前做的是python这方面的

工作经验？

​	我在学校的时候一直就是研究的这个方向，之后一直做的这方面的项目

项目？

​	做个几种级别的项目，企业级，平台级，电商app，小程序之类的

去重?

​	自己循环弄成一个新的数组

​	set  先转换为集合，在转换为数组

​	itertools.grouby  先排序，

```py
import itertools
ids = [1,4,3,3,4,2,3,4,5,6,1]
ids.sort()
it = itertools.groupby(ids)
for k, g in it:
    print k
```

正反排序?

​	arr.sort(reverse=True)    倒叙

```py
arr = [3,8,4,1]
arr.sort(reverse=True)
arr1 = sorted(arr,reverse=False)
print(arr1)
print(arr)
arr2 = {1,2}
arr4 = set('2334')
print(type(arr2))
print(type(arr4))
```

set number  (vim 显示行数)     ~ 一般都是临时文件linux中

nginx配置

```py
location   /aa {
    root /home/zkw/one
    index index.html
}
这样就是先访问root，在访问 aa目录下的index.html

deny，allow
静态文件   alias
```

