#                                                                                                                                                                                                                                                                                                                                                                          python   js   动态类型   弱类型的语言    python  动态类型   强类型的语言   弱类型 js中可以隐式转换   强类型  要求严格，Python是一门跨平台、开源、免费的解释型高级动态编程语言 

使用coding:gbk 或者 utf-8 来表明中文注释是以那种方式解读的

type ()   可以用来查询变量所指的对象类型

instance（aaa，int）返回true和false

- type()不会认为子类是一种父类类型。
- isinstance()会认为子类是一种父类类型。

end=""     不换行输出，引号里面加的空格也能显示出来

查看地址 print(id(obj))

注释：

单行#，多行'''    """

### 基本语法：

- print('陕西优逸课')  #输出一个字符串

- print('hello','world')  #接受多个字符串，字符串会进行拼接，每个用空格隔开

- print(123)#打印整数

- 传入表达式print(100+200)

- 混合型print("100+200",100+200)

- 格式化打印print("我今年%d"%（10）)   

  ```py
  print("我今年%d岁,%d斤"%(10,20))   两句之间啥东西都不能加，逗号，空格都不行
  ```

- string.format    用{}  代替以前的%

  ```py
  > a= "我的名字是{0},年龄是{1}"
  >>> b=a.format("赵堃崴",20)
  >>> b
  '我的名字是赵堃崴,年龄是20'
  >>> a= "我的名字是{name},年龄是{age}"
  >>> c=a.format(name="zhaokunwei",age=10)
  >>> c
  '我的名字是zhaokunwei,年龄是10'
  >>> 
  "我是{0},我喜欢数字{1:*^8}".format("赵堃崴",666)
  '我是赵堃崴,我喜欢数字***666***   '    
  冒号后面写的是扩充的内容，*写的是除了内容以外扩充的，8是长度 ^ 表示的是居中，< 左对齐  >  右对齐
  "{0:*>10d}".format(3)
  '*********3'
  ```


### 输入输出:

input     print    如果想要不可见，可用  password=getpass.getpass(),print(password),但必须在终端执行

### 变量：可以储存数据的容器，可以存储引用数据

- 变量不需要声明，我们可以直接给变量赋值，直接使用
- 变量可以存储不同的数据类型
- 可以同时为多个变量赋值
- 变量命名可以有数字字母下划线组成，不能以数字开头，区分大小写，不能用$符号
- 不支持自增自减   但可以用a+=1
- 变量名不可以是关键字和保留字

### 数据类型：

| 对象类 | 例如                           |
| ------ | ------------------------------ |
| 数字   | 123,4.1233，3+4j，十进制       |
| 字符串 | ‘span’ “span”  ‘’‘  span   ’‘’ |
| 列表   | [1,2,3[1,2]]                   |
| 元组   | (1,2,3,4)                      |
| 字典   | {'a':1,'b':2,'c':3}            |
| 集合   | set('abc'),{'a','b','c'}       |
| 布尔值 | true\false                     |

divmod(13,4)   (3,1)  同时得到商和余数

round(value)    返回一个新的数，四舍五入

整数：

- （int）没有小数点得数，整数的大小取决于电脑内存的大小，没有上限。
- 整数缓存问题
  - python仅仅对比较小的整数对象进行缓存（范围为[-5,256]）缓存起来，而并非是所有整数对象，需要注意的是，这仅仅是在命令行中执行，而在pycharm后者保存为文件执行，结果是不一样的，这是因为解释器做了一部分爱优化，范围是[-5,正整数]

浮点数（float）只要有小数点的就是浮点数，无穷小数会做精度处理

复数（complex）虚部以j或J结尾的为复数

浮点数、整数的转换

float（） int（）

将十进制转化为二进制0b、八进制0o、十六进制0x

bin()    cot()   hex()

字符串：

- ord( )   可以把字符串转换为对应的Unicode码   然后计算机再用二进制进行存储
  - ord('A')      65   
- chr()     可以把十进制数字转换成对应的字符
  - chr(66)   'B'
- len()   查询字符长度
- input()    传进来的也是字符串

Python中，**数值类型（int和float）、字符串str、元组tuple都是不可变类型。而列表list、字典dict、集合set是可变类型。** 

定义方式：

- 单引号

- 双引号

- 三引号   可与模板字符串进行比较

  ```py
  print('''   string    ''')
  ```

#### 续行符：

- \     print("aaa\\

  nbbb")    输出的是aaabbb

### 转义字符“\”

- print(r'山西\\n'优逸课\\n")

- print(u‘山西’优逸课“)

  前缀：r代表后面字符串是一个普通字符

  ​	    b代表后面的字符串是byte数据，在python2中print函数操作的字符串全部为byte型数据，在python3中是Unicode数据

  ​	    u  主要是python2为了兼容python3

切片：

```py
str1="山西优逸课"
print（str1[0:5:2]）
输出山优客   最后一位可以是负数，代表的是从反向取   个数为几，隔几个取
 str1="我是赵堃崴"
print(str1[-1:1:-1])   崴堃赵     如果最后一位是负数，第一位也是负数，那么中间的数字写成整数是从左往右点
print(str1[-1:2:-1])   崴堃
print(str1[-1:3:-1])   崴
print(str1[-1::])      崴
```

\t  ,\r,\n

\r 回车

```py
print("123\r11")
如果后面的不够，他会覆盖前面的
```

num1=123

num2=123

print(id(num1))   他俩的地址是一样的

字符串拼接与+拼接的效率

```py
import time   //引入时间包裹
time1=time.time()   //开始的时间
a=""   字符串是不可变量，每一次循环都是创建了一个新的地址，新的对象
for i in range(1000000):
	a+="x" 
time2=time.time()
print(time1)
print(time2)
time3=time.time()
li=[]  选用列表是因为列表的值可以变化
for i in range(1000000):
	li.append("x")   注意这里是往列表里添加，这里i的并不是在列表里循环
a=",".join(li)
time4=time.time()
print(time3)
print(time4)
```

字符串的驻留机制：

​	对于符合标识符规则的字符串（仅包含下划线（_）、字母、和数字）会启用字符串驻留机制驻留

```py
a="avb_11"
b="avb_11"
a is b   true
c="aas#"
d="aas#"
c is d false
```



### 字符串的内建函数：字符串是不可变量

```py
str = 'Runoob'
print (str) # 输出字符串
print (str[0:-1]) # 输出第一个到倒数第二个的所有字符
print (str[0]) # 输出字符串第一个字符
print (str[2:5]) # 输出从第三个开始到第五个的字符
print (str[2:]) # 输出从第三个开始的后的所有字符
print (str * 2) # 输出字符串两次
print (str + "TEST") # 连接字符串
```

- 大小写

  - string.capitalize()  把字符串的第一个字符大写
  - string.replace("q","白")     字符串的替换，不会改变原对象，而是生成新的对象，把原来的地址改变成现在的地址
  - string.lower()  小写
  - string.upper()  大写
  - string.title()     每个首字母都大写
  - string.swapcase()     转换成大写或者小写

- 删除和扩充

  - string.strip(["str"])   在字符串前后删除空格，或者删除str      

    rstrip  lstrip    右左     

    ```py
    str4="1,1,1,a,bc,1,1,1"    括号里的默认为空格   空格不需要[]
    print(str4.strip("1,"))
    结果是 a,bc
    ```

  - string.center(len,"str")    以string为中心两边填充，第一个参数是长度，"str"致使string长度为len  第二个参数是填充的内容

  - string.rjust(len,"str")    在string左边填充

  - string.ljust(len,"str")    在string右边填充

- string.count("str",start,end)   在start和end之间str的次数

- 编码与解码

  - string.encode(encoding="utf-8",errors="ignore")   以指定格式编码

  - string.decode(encoding="utf-8",errors="ignore")   以指定格式解码

    ```py
    str1="一"
    print(str1.encode(encoding="utf-8",errors="ignore"))
    print(str1.decode(encoding="utf-8",errors="ignore"))
    ```

- string.endswith(obj,start,end)    是否已obj结尾

- string.startwith(obj,start,end)    是否已obj开始

- 查找元素

  - string.find("str",start,end)  返回str的位置下标，返回的是第一个，找不到返回-1
  - string.rfind("str",start,end)    从右到左
  - string.index("str",start,end)   返回str的位置下标，找不到报异常
  - string.rindex("str",start,end)
  - string.isalnum()    至少有一个字符，并且所有字符都是字母数字，返回bool值

- string.isalpha()    至少有一个字符，并且所有字符都是字母，返回bool值

- string.isdecimal()    是否字符串都是十进制的数字

- string.isdigit()   是否字符串都是数字

- string.islower()

- string.isuper()

- string.isspace() 至少为一个字符，并且string全为空，返回True，否则返回False

- 拼接与分割

  - ",".join(string)  将列表（里面必须是string类型）对象用string进行分隔组合为字符串         注意@  使用+拼接字符串，会生成新的字符串对象，因此不推荐，而join函数在拼接字符串之前会计算所有字符串的长度，然后逐一拷贝，仅仅新建一次对象

    ```py
    arr=['1','2','3']   arr  里面必须是字符串，否则会报错
    print(",".join(arr))
    结果是1,2,3
    ```

  - string.split("str",num)  将string通过str进行分割，num制定分割次数       引号里面写的是用什么将其分开

    ```py
    str1="1,2,3,4,5,4"
    print(str1.split(",",4))
    结果是  print(str1.split(",",4))
    ```

  - string.splitlines()  将string通过\n进行分割

    ```py
    str1="1,2,\n3,4,5,4"
    print(str1.splitlines())
    ['1,2,','3,4,5,4']
    ```

注意：列表： 可以改变

- 列表可以保存任意类型数据
- 列表可以切片
- 列表是可变的，字符串不可变
- 可以创建空列表。也可以创建只有一个元素的列表
- 可以创建多维列表

列表长度：

len（arr）

列表下标：

arr.index()

列表的遍历

```py
1.mylist=[1,2,3,4,5,6]

  for item in mylist:    注意这里没有括号，他是冒号
	  print(item)
       print(mylist.index(item))一定要缩进   这是python    语法
   结果为1,2,3,4,5,6      item为元素，不是下标
 2.mylist=[1,2,3,4,5,6]
 for i,v  in enumerate(mylist):
 	print(i)   #下标
 	print(v)   #值
 enumerate()   将列表转换为（(0,1),(1,2),(2,3),(3,4),(4,5),(5,6)）
 深拷贝和浅拷贝
 因为浅拷贝只会将对象的各个属性进行依次复制，并不会进行递归复制，而 JavaScript 存储对象都是存地址的，所以浅复制会导致 obj.arr 和 shallowObj.arr 指向同一块内存地址
 import copy     首先得引入
 copy.copy(arr)   #浅拷贝   浅拷贝是运用本身已经存在的方法去进行指针拷贝，而深拷贝需要自己写一个拷贝构造函数，将地址存储下来
 arr1=copy.copy(arr)
	print(arr1)
 copy.deepcopy(arr)   #深拷贝
 数组里面添加元素   arr.append(item)
 传址不叫浅拷贝，传址为赋值，浅拷贝是把内容给了他
 print(str1.splitlines())
arr=[[1,2],[3,4]]     //浅拷贝
arr1=[]
for item in arr:
    arr1.append(item)
arr[0]="a"
print(arr,arr1)
结果为['a',[3,4]]   [[1,2],[3,4]]
python里面有更简单的东西，叫包裹，想要实现这个只需要调用


```

### 列表的切片：

```py
以列表：a = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9] 为说明对象

1.取偶数位置
>>>b = a[::2]
[0, 2, 4, 6, 8]
2.取奇数位置
>>>b = a[1::2]
[1, 3, 5, 7, 9]
3.拷贝整个对象
>>>b = a[:] #★★★★★
>>>print(b) #[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
>>>print(id(a)) #41946376
>>>print(id(b)) #41921864
或
>>>b = a.copy()
>>>print(b) #[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
>>>print(id(a)) #39783752
>>>print(id(b)) #39759176
需要注意的是：[:]和.copy()都属于“浅拷贝”，只拷贝最外层元素，内层嵌套元素则通过引用，而不是独立分配内存。

>>>a = [1,2,['A','B']]
>>>print('a={}'.format(a))
>>>b = a[:]
>>>b[0] = 9 #修改b的最外层元素，将1变成9
>>>b[2][0] = 'D' #修改b的内嵌层元素
>>>print('a={}'.format(a))
>>>print('b={}'.format(b))
>>>print('id(a)={}'.format(id(a)))
>>>print('id(b)={}'.format(id(b)))
a=[1, 2, ['A', 'B']] #原始a
a=[1, 2, ['D', 'B']] #b修改内部元素A为D后，a中的A也变成了D，说明共享内部嵌套元素，但外部元素1没变。
b=[9, 2, ['D', 'B']] #修改后的b
id(a)=38669128
id(b)=38669192

4.修改单个元素
>>>a[3] = ['A','B']
[0, 1, 2, ['A', 'B'], 4, 5, 6, 7, 8, 9]
5.在某个位置插入元素
>>>a[3:3] = ['A','B','C']
[0, 1, 2, 'A', 'B', 'C', 3, 4, 5, 6, 7, 8, 9]
>>>a[0:0] = ['A','B']
['A', 'B', 0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
6.替换一部分元素
>>>a[3:6] = ['A','B']
[0, 1, 2, 'A', 'B', 6, 7, 8, 9]
```



### 列表的内建函数：

- 列表的添加与删除
  - List.append(item)   在列表最后插入元素      
  - List.insert(index,item)       在任意位置(index的前一位)插入元素   如果index 超出，默认插入最后
  - List.extend(list1)   将两个list进行合并   只能合并两个
  - print(arr+[1,2,3]+[2,3,5])   合并多个数组   不改变原数组
  - List.pop()  默认删除最后一个元素    可以指定删除的位置  返回到指定位置    传入的是下标 
  - List.remove(item)  传入的是元素   删除list中的元素，有相同的删除第一个
- 列表元素的查找
  - List.count(item)  查看某元素在list的次数
  - List.index()   查看某元素在list中的第一个下标    如果不存在就报异常    可以指定范围
- List.reverse()  将list反转
- List.sort(reverse=True)     排序  默认升序   ，reverse=true   降序 直接在原列表中改变    a=sorted(a)  生成一个新的列表对象 默认升序排列   迭代器？？？？ c=reversed(a)  返回一个迭代器，再将其转化为列表，但是只能迭代一次，   作用只是将其翻转，并不是排序 
- 列表的清空与拷贝：
  - List.copy()  浅拷贝
  - List.clear()   清空数组
- 列表成员的资格判断：
  - in
  - not in

### 元组：不可改变   

注意：

- 元组和列表有点类似，区别就是元组元素不可改变
- 元组通过圆括号定义
- 可以使用切片
- 元组可以定义只有一个元素的元组，mytuple=(1,),逗号不可少，因为解释器会把(1)解释为一个整数，(1,)会解释为元组 
- 空元祖

操作list\tuple的内建函数

- len(list)    数组的长度

- max()    数组的最大数

- min()   数组的最小数

- tuple()   将列表转化为元组

- enumerate()   返回下标和元素

- 删除元祖   del+元祖名字

  ```py
  tup = ('physics', 'chemistry', 1997, 2000)
   
  print tup
  del tup
  print "After deleting tup : "
  print tup
  ('physics', 'chemistry', 1997, 2000)
  After deleting tup :
  Traceback (most recent call last):
    File "test.py", line 9, in <module>
      print tup
  NameError: name 'tup' is not defined
  ```

    元组生成器

  ```py
  a=(x*2 for x in range(5))   定义一个元祖，返回一个生成器
  a
  <generator object <genexpr> at 0x03D5C4F0>
  tuple(a)     将生成器转换为元组
  (0, 2, 4, 6, 8)
  list(a)    第二次就不能再用了，这是因为指针，每生成一次，指针下移一次
  []
  
  
  s=(x*2 for x in range(5))    括号里面在一个个生成
  >>> s.__next__()   返回指针走到位置的值   生成器才可以用的方法
  0
  >>> s.__next__()
  2
  >>> s.__next__()
  4
  >>> s.__next__()
  6
  ```

  

### 字典:     可以改变   成对存储 键值对 

字典的键是不可变数据，一般用整数，浮点数，元组，字符串，并且键不能重复，否则会覆盖

- json格式创建

  ```oy
  mydict1={"name":"小白"}
  print(mydict1)
  ```

- 通过内建函数

  ```py
  mydict2=dict(name="小红"，age=10)
  mydict3=dict(zip(["name","age"],["小爱","18"]))//这种方式必须是括号套括号  或者是括号套列表
  实际上应该是这样
     k=["name","id"]
     v=["z","1"]
     d=dict(zip(k,v))
  print(mydict2)
  ```

  dict() #创建空字典

  dict(a="a",b="b",c="c")  #传入关键字a，b，c是变量

  dict(zip(['one','two','three'],[1,2,3]))   #映射函数方式来构造字典

  dict([('one',1)('two',2)('three',3)])   #  可迭代对象方式

- 字典内建方法？

  mydict=dict.formkeys([1,2,3,4],'a')   #批量创建键值

  ```py
  mydict4=dict.fromkeys(["name1","name2"],"小白")
  ```


字典访问方式：

- mydict[键]

添加属性和方法：

- mydict[newkey]=value

删除字典和属性方法：

- del mydict[键] 删除指定属性方法
- mydict.clear()  清空字典

字典的内建函数：

- Dict.get("key","info")     返回key对应的value，没有为None，info指定没找到的为什么

  ```py
  mydict={"name":"赵堃崴","age":"22"}
  print(mydict.get("z","dd"))
  结果为dd
  ```

- Dict.keys()   返回字典中所有的key

- Dict.values()  返回字典中所有的value

- Dict.items()  返回字典中所有的  key:value 形式数据

- Dict.setdefault(key,value)   添加数据

- Dict.pop(key)    删除key   返回删除键所对应的值

- Dict.popitem()    删除最后一位的key:value，因为字典是无序列表，不能传参数

- Dict.clear()      清空字 典

#### 序列解包：

```py
>>> a,b,c=1,2,3
>>> a
1
>>> b
2
>>> c
3
>>> a,b,c=(1,2,3)
>>> a
1
>>> a={"name":"z","id":1111,"age":19}
>>> c,b,d=a.keys()
>>> c
'name'
>>> c,b,d=a.values()
>>> c
'z'
>>> 
```



### 集合：

#### 定义：唯一的、不可变得对象的一种无序集合。一个项在集合中只出现一次。有相同的不会报错，但在输出的时候只显示一个

#### 语法：可以使用大括号 { } 或者 set() 函数创建集合，注意：创建一个空集合必须用 set() 而不是 { }，因为 { } 是用来创建一个空字典。 

- y=set（）
- myset ={1,3,2}
- set(1,2,3,4) ×  set（）括号里面的不能是数值型，必须是字符串型
- set("string")

#### 集合的添加：

a.add()    是一个元素

a.update ()   每一个元素是一个集合

a,remove()      

#### 去重

arr1={1,2,3,4,5,6}

arr2={4,5,6,7,8,9}

- 差集（当前的减去比较的，剩下的就是差集）

  ```py
  print(arr1-arr2)
  {1,2,3}
  ```

  

- 并集（不相同和相同的弄在一起）

  ```py
  print(arr1 & arr2)
  {4,5,6}
  ```

  

- 交集（相同的）

  ```py
  print(arr1 | arr2)
  {1,2,3,4,5,6,7,8}
  ```

  

### 运算符：

- 算术运算符

  - 基本算术运算符   +-*/      除法运算中无论有无复杂类型，结果都会精确到浮点数
  - ＋
    - 操作两个数字型数据=> 加法运算
    - 操作一个数字型数据=>正数
    - 操作的str  list  tuple 起到连接作用
  - -
    - 加法运算和负数
  - *
    - 操作两个数字型数据=>乘法运算
    - 操作的str list tuple => 重复

- 逻辑

  - and   与  同真为真，   返回第一个价值

  - or    或   同假为假，返回第一个真值

  - not    非

    ```py
    >>> a=0b11001
    	       
    >>> b=0b01000
    	       
    >>> a
    	       
    25
    >>> b
    	       
    8
    >>> c=a&b   1 0 wei1 11wei1 
    	       
    >>> c
    	       
    8
    c=a^b   异位   相同为0，不同为1
    ```

    

- 关系

  - ==   
  - ！=
  - \>
  - <
  - \>=
  - \<=

  print("str"+123)  ?????

- 位运算符

  - &  按位运算符   原码，反码，补码按   按位与运算符：参与运算的两个值，如果两个相应未都为1，则改为的结果为1，否则为0
  - |  按位运算符：只要对应的二个二进位有一个为1时，结果位就位1
  - ^   按位异或运算符    当两对应的二进位相异时，结果位1
  - ~    按位取反运算符：对数据的每个二进制位取反，即把1变为0，把0变为1.
  - <<   左移运算符：运算符的各二进位全部左移若干位，由<< 右边的数字指定了移动的位数，高位丢弃，低位补0
  - \>>   右移运算符：把>> 左边的运算数的各二进位全部右移若干位，>>右边的数字指定了移动的位数

- 特殊运算符

  - //   地板出
  - %
  - **

- 赋值运算符    这里面没有全等于

  - =
  - +=
  - -=
  - *=
  - /=
  - %
  - ******=      幂赋值运算符    c********=a=c=c********a 
  - //=     取整除赋 值运算符    c//=a  等效于 c=c//a

- 成员运算符      必须是字符串才行

  - in  如果在指定的序列中找到值返回True，否则返回False
  - not in  如果在指定的序列中没有找到值返回True，否则返回False

- 运算符的优先级

  - ** 指数（最高）
  - +-   按位翻转，一元加号和减号
  - */ % //  乘除，取余和取整数
  - +-  加法减法
  - &  位‘AND’
  - ^|   位运算符
  - <=  < > >=  比较运算符
  - ==   !=   等于运算符
  - =  %= /= //= -= +=  *= **=   赋值运算符
  - is   is not   身份运算符
  - in  not in  成员运算符
  - not and or    逻辑运算符

- 身份运算符：

  - is    is 是判断两个标识符是不是引用自一个对象  x is y
  - is not 是判断两个标识符是不是引自不同那个对象  x is not y，类似id(a)!=id(b)  如果引用的不是同一个对象则返回结果True，否则返回False

#### is与==的区别：

- is 是用来比较两个对象的id是否相同  是否指向同一个地址    地址里面包含value，type，id
- ==是用来比较两个对象的value值是否相同   其实就是调用对象的一个方法，一个属性，所以运行效率比较低

```py
obj1={"name":"小白"}
obj2={"name":"小红"}
print(obj1 is obj2)    false
print(obj1 == obj2)    true
```

### python流程控制：

#### 选择结构：if   知道次数，不知道条件

```py
if 1>2:
	print("1>2")
elif 1<2:
	print("2>1")
elif 1==2:
	print("1==2")
	
	
for i in range(1,10):
    for j in range(1,i+1):
        print("%d*%d=%d"%(i,j,i*j),end="")
    print("")
 import random
```

 while    想变成空写pass    知道条件，不知道次数    判断条件为真则执行循环体内的执行语句；  判断条件为真 可以是 任何表达式、任何非零、非空（null）的值； 

```py
import random    引进来一个包裹
num1=random.randint(0,100)   创造一个数
num=int(input())    输入一个数  并且转换为整型，因为输入的都是字符串
num4=0   次数
while True:   满足条件的时候执行循环
    if num1>num:
        print("有点小")
        num4+=1
    elif num1<num:
        print("有点大")
        num4+=1
    elif num1==num:
        print("恭喜你猜对啦")
        num4+=1
        print(num4)
        break
    num=int(input())
```

zip并行迭代

```py
names=("111","222","333")
ages=("11","12")
for name,age in zip(names,ages):
    print("%s,%s"%(name,age))
```



for   / while    如果for或者while 执行，并且没有被中断，后面可以加else语句执行，但是被中断了，就不会执行了

```pt
 for item in students:
        if item[type]==myid:
            print(item)
            break
 else:
     print("查无此人")
```

#### 注意点：

- 尽量减少循环内部不必要的计算

- 嵌套循环中，尽量减少内层循环的计算

- 局部变量查询较快，尽量使用局部变量

  ```py
  import time
  start=time.time()
  for i in range(1000):
      li=[]
      for m in range(10000):
          li.append(i*1000+m*100)
  end=time.time()
  print(end-start)
  start1=time.time()
  for i in range(1000):
      li=[]
      c=i*1000
      for m in range(10000):
          li.append(c+m*100)
  end1=time.time()
  print(end1-start1)
  
  3.8267271518707275
  2.876628875732422
  ```

  

三元表达式：

print（结果1 if  表达式 else  结果2）

range(start,end,step)    #创建序列   start开始下表   end结束  step代表步进值

循环里干预循环的语句：

- continue   终止本次循环
- break   终止整个循环

### 函数

函数也是对象，函数名其实就是一个变量，它里面只不过是引用的一个地址，你把他传递给另一个变量，那个变量拿到那个地址，在使用函数的方法

```py
def aa():
    ''' a'''
    print("a")
c=aa
c()
print(id(aa))
print(id(c))

结果是
a
48862168
48862168
```



- 缺省参数（默认参数）

  调用函数时，缺省参数的值如果没有传入，则被认为是默认值

  ```py
  def person(name,age=19):
  	print("name",name)
  	print("age",age)
  person("赵堃崴",90)
  person("赵堃崴")
  ```

- 可变参数

  定义可变参数和定义list或tuple参数相比，仅仅在参数面前加了一个*号。在函数内部，参数numbers接收到的是有个tuple，因此，函数代码完全不变。但是，调用该函数时，可以传入任意个参数，包括0个参数

  ```py
  def cala(*number):
  	print(type(number))
  	for i in number:
  		print(i)
  cala(1,2,3,4,5)
  ```

- 关键字参数

  ```py
  def person(name,age=18,**attr):
  	print("name:%s"%name)
  	print("age:%s"%age)
  	print(attr)
  person(name="xb",age=18,sex="男",tel=11111111111)
  ```

  参数组合：

  在python中定义函数时，可以用必选参数、默认参数、可变参数、关键字参数，这四种参数都可以一起使用，或者只是用其中某些，但是请注意，参数定义的顺序必须是：

  ​    必选参数->默认参数->可变参数->关键字参数

  ```py
  def person(name,age=18,*cj,**attr):
  	print("name:%s"%name)
  	print("age:%s"%age)
  	print(cj)
  	print(attr)
  person("xb",18,69,30,sex="男",tel="1111111111")
  ```

  必选参数传参时可以这样传：

  ```py
  def add(m,n):
      return m+n
  print(add(n=10,m=19))//参数的位置可以变化，不过需要赋值
  ```

  

#### 高阶函数：

对于高阶函数的形式可以有两种：

- 把一个函数名当做实参传递给另外一个函数（“实参高阶函数”）

  ```py
  def add(a,b):
  	return a+b
  def jian(a,b):
  	return a-b
  def size(a,b,fn):
  	return fn(a,b)
  print(zize(10,20,jian))
  ```

- 返回值中包含函数名("返回值高阶函数")

  ```py
  def fn1():
  	def aa():
  		print("this is aa")
  	return aa   这里的aa只需要是函数名即可
  bb=fn1()
  bb()
  ```

#### 匿名函数：

​	lambda  参数  ： 表达式

​	可以有多个参数

​	表达式不需要返回，自动return

​	num=(lambda a,b:a+b)(10,20)

​	print(num)

 	匿名函数的调用方式

 -	自调用
	-	字面量        fn=lambda a,b:a+b   print(fn(10,20))

#### map:

arr=map(lambda x,y:x+y,range(1,10),range(1,10))

print(list(arr))

#### fliter:

arr=filter(lambda x:x>5,range(1,10))

print(list(arr))

#### reduce:现在很少用，把他装到库里去了，使用的时候需要引进来：import functools

arr=	functools.reduce(lambda x,y:x+y,range(1,11))

print(arr)

它里面的x是前一位表达式的值

### 局部变量与全局变量：

#### 定义：

- 全局变量是整个py文件中声明，全局范围内都可以访问

- 局部变量是在某个函数中声明的，只能在该函数中调用他，如果试图在超出范围的地方调用，程序就爆掉了

  ```py
  aa=123
  def fn():
  	b=46
  	print(a)
  	print(b)
  print(a)
  print(b)
  ```

#### 嵌套作用域的细节

- 在增加（嵌套的函数作用域后，变量的查找法则则变得稍微复杂了一些，对于一个函数：一个引用（x）首先在本地（函数内）作用域查找变量名x；之后会在代码的语法上嵌套了的函数中的本地作用域，从内到外查找，之后查找当前的全局作用域（模块文件），最后在内置作用域内（模块-builtin-））。全局声明将直接从全局（模块文件）作用域进行探索。在默认情况下，一个赋值（x=value）创建或改变了变量名x的当前作用域。如果x在函数内部声明为全局变量，他将会创建或改变变量名x为值会修改最近的嵌套函数的本地作用域中的名称x

#### global语句

- global语句是python中唯一看起来有些像声明语句的语句。但是。他并不是一个类型或大小的声明，他是一个命名空间的声明。他告诉python函数打算生成一个或多个全局变量名。也就是说，存在于整个模块内部作用域（命名空间）的变量名

  ```py
  aa=123
  def fn2():
      global aa  #声明的时候不能修改
      aa=456
  fn2()
  print(aa)
  global bb  可以在创建一个
  ```

- nonlocal局部作用域

  ```py
  num2=123
   def aa():
       num2=455
       def bb():
           nonlocal num2
           num2+=10
       bb()
       print(num2)
   aa()
  ```

  

#### 闭包函数：

- 在一些语言中，在函数中可以（嵌套）定义另一个函数时，如果内部的函数医用了外部的函数的变量，则可能产生了闭包。闭包可以用来在一个函数与一组“私有”限量之间创建关联关系。在给定函数被多次调用的过程中，这些私有变量能够保持其持久性

  ```py
  def aa():
  	num1=123
  	def bb():
  		print(num1)      函数内部的函数想要调用函数外部的变量，并且最外层的函数返回值为内部函数
  	return bb
  bb=aa()
  bb()
  ```

#### 递归函数：

如果一个函数在内部不调用其他的函数，而是自己本身的话，这个函数就是递归函数

```py
def fn(a):
     if a==1:
         return 1
     else:
         return a*fn(a-1)
 print(fn(6))
```



#### 装饰器：

- 定义：装饰器实际上就是为了给某程序增添功能
- 使用场景：比如该程序已经上线或已经被使用，那么就不能大批量的修改源代码，这样是不科学的也是不现实的
- 装饰器满足三个原则：
  - 不能修改被装饰的函数的源代码
  - 不能修改被装饰得函数的调用方式
  - 满足1、2的情况下

```py
import time   引入时间包裹
def texter(fn):
    def newtest():
        start=time.time()
        print("start:",start)
        fn()   //执行test函数 获取当前的时间，执行完之后，获取结束的时间
        end=time.time()
        print("end",end)
        print("总时间是",end-start)
    return newtest
#@texter   这是python中的用法
def test():
    time.sleep(1)
    print("test is running")
test=texter(test)   //这是我们自己定义的方法
test()   //调用他，查找他是什么，他是一个另一个函数的参数，在寻找另一个函数，在执行另一个函数，然后一步一步走。




import time
def texter1(a):
	def texter(fn):
    	def newtest():
        	start=time.time()
        	print("start:",start)
        	fn()
        	end=time.time()
        	print("end",end)
        	print("总时间是",end-start)
    	return newtest
#@texter
def test():
    time.sleep(1)
    print("test is running")
test=texter(test)
test()
```



#### 函数的柯里化：

```py
def add(a):
	def fn(b):
		print(a+b)
	return fn
add(5)(5)


import time
def texter1(a):
    def texter(fn):
        def newtest():
            start=time.time()
            print("start:",start)
            print("参数是：",a)
            fn()
            end=time.time()
            print("end",end)
            print("总时间是",end-start)
        return newtest
    return texter
@texter1(1)
def test():
    time.sleep(1)
    print("test is running")
#test=texter(test)
test()



```

#### 对主函数的理解：

解释器如何判断你执行的文件是哪一个，是因为解释器里面有个\__main__函数，当你执行这个文件的时候，他会传入一个参数，把这个文件当做主函数

```py
假设我们有一个const.py文件，内容如下：

PI = 3.14

def main():
    print("PI:", PI)

main()

# 运行结果：PI: 3.14

现在，我们写一个用于计算圆面积的area.py文件，area.py文件需要用到const.py文件中的PI变量。从const.py中，我们把PI变量导入area.py：

from const import PI

def calc_round_area(radius):
    return PI * (radius ** 2)

def main():
    print("round area: ", calc_round_area(2))

main()

'''
运行结果：
PI: 3.14
round area:  12.56
'''

2.2 修改const.py，添加if __name__ == "__main__"
我们看到const.py中的main函数也被运行了，实际上我们不希望它被运行，因为const.py提供的main函数只是为了测试常量定义。这时if __name__ == '__main__'派上了用场，我们把const.py改一下，添加if __name__ == "__main__"：

PI = 3.14

def main():
    print("PI:", PI)

if __name__ == "__main__":
    main()

运行const.py，输出如下：

PI: 3.14
1
运行area.py，输出如下：

round area:  12.56
1
如上，我们可以看到if __name__ == '__main__'相当于Python模拟的程序入口，Python本身并没有这么规定，这只是一种编码习惯。由于模块之间相互引用，不同模块可能有这样的定义，而程序入口只有一个。到底哪个程序入口被选中，这取决于__name__的值。 
```

help(函数名.\__doc__)    可以打印函数的注释，即文档字符串

```py
def aa():
    ''' a'''
    print("a")
help(aa.__doc__)

结果是
No Python documentation found for 'a'.
Use help() to get the interactive help utility.
Use help(str) for help on the str class.
```



## 模块：py文件

## 包：文件夹   但里面必须有\__init__.py

from bao1 import a as a2      

from bao1.a import aa3,aa2   依次导入

from bao1.a import *   全部导入    执行这句话，可以再模块中定义

相对路径只能在子模块中使用

导入的东西都不需要后缀名

from导入的是文件，而import 导入的是模块，

### 控制模块全部倒出：

```py
from module import *
从moudule模块中全部导出内容
再模块中定义变量 __all__,可以有效的控制被全部导入


def bb():
    print("这是bb")
def bb1():
    print("这是b里面的bb1")
def bb2():
    print("这是b里面的bb2")

__all__=["bb1"]   只能从这里导出函数bb1，其他的都不行，但是你要在外面指定我要导入bb2也可以，这只是在全部导入的情况下

```



### 使用相对路径导入包中子模块：导入的时候要注意你导入的是文件，是方法，还是其他的东西

如果bao1里面的a模块要导入同目录下的模块b。它应该包括import语句如下：

```py
from .b import *     一个点是指当前的，必须有点
from ..b import *    两个点是指上一层
```

!!!!!使用相对路径导入包中子模块注意事项：

- 使用点的这种模式不是从包的目录中导入会引发错误
- 在顶层的脚本的简单模块中，他们将不起作用    即顶层不能使用相对路径
- 包的部分被作为脚本直接执行，那他们将不起作用，即不能作为程序执行

### 将模块分隔成多个文件：

你想将一个模块分割成多个文件。但是你不想将分离的文件统一成一个逻辑快时使已有的代码遭到破坏,例如你想将mymodule.py分为两个文件，每个定义的一个类

本来只有一个模块，但是你想吧它分成两个模块，就需要把模块所在的包里面的\__init__.py文件的内容修改，他需要把两个模块连接起来，同时导入，然后在包外面导入整个包，可以把此时的包当做是一个模块导入。

```py
mymodule.py
class A:
    def spam(self):
        print("A,spam")
class B(A):
    def bar(self):
        print("B.bar")
第一点，将mymodule目录来替换文件mymodule.py  在这个目录下，创建以下文件：
mymodule/
	__init__.py
	a.py
	b.py
第二步：
在a.py文件中插入以下代码：
	class A:
		def spam(self):
			print("A.spam")
在b.py文件中插入以下代码：
	from .a import A
	class B(A):
		def bar(self):
			print("B.bar")	
第三步：
在__int__.py中，将两个文件粘合在一起：// 这里是重点，如何将两个不相关的东西连接到一起，就相当于是把包当做了模块用
	__inti__.py
	from .a import A
	from .b import B
	
import mymodule
a=mymodule.A()
a.spam()
A.spam
b=mymodule.B()
b.bar()
B.bar
```



### 合并包目录

利用命名空间导入目录分散的代码，你可能有大量的代码，由不同的人来维护，每个部分被组织为文件目录，如一个包，然而，你希望能用共同的包前缀将所有组件连接起来，不是将每一个部分作为独立的包来安装。在相同的目录里，任何一个目录都没有\__init__.py文件，两个不同的宝目录被合并到一起，你可以导入两个都能工作

```py
import sys    引入系统模块
sys.path.extend([r"C:\Users\98660\Desktop\demo1\xb",r"C:\Users\98660\Desktop\demo1\xh"])   //这句话的意思是给解释器一个新的路径，让下面的语句from从这里面找，
# print(sys.path)
from span import xbd,xhd
xbd.aa()
xhd.bb()

xb       文件构架
	span
		xbd.py
xh
	span
		xhd.py
```



#### 重新加载

你想重新加载已经加载的模块，因为你对其原码进行了修改。可以使用imp.reload()来重新加载先前加载的模块

```py
import b     //先导入b   你导入的是文件，调用的时候应该是文件的方法
b.bb()      调用bb函数
zheishibb    //然后修改为zheshibbb
import imp    在导入imp
imp.reload(b)   让b重新加载
b.bb()   调用bb
zhehshibbb
```

### 通过字符串名导入模块：

你想导入一个模块，但是模块的名字在字符串理，你想对字符串调用导入命令。使用importlib.import_module()函数来手动导入名字为字符串给出的一个模块或者包的一部分  最顶层要使用绝对路径

```py
import importlib
math=importlib.import_module("b")   括号里面传的是文件名的字符串
math.bb()
```

### 通过字符串名导入模块，只不过是相对导入：你需要给他一个额外的参数

```py
def dd():    /d模块
    print("dd")
import importlib    /c模块    引入字符串模块 返回生成的模块对象，需要存储一个变量  这个变量就是模块
aaa=importlib.import_module(".d",__package__)
import importlib

math=importlib.import_module("bao1.son1.c",__package__)//传入c模块，传入的模块调用模块的方法
math.aaa.dd()    /main模块

```

### 读取位于包中的数据文件：

```py
import pkgutil
data=pkgutil.get_data(__package__,"da.dat")

import pkgutil
date=pkgutil.get_data("bao","b1.py")  第一个参数代表的是包的名称
print(date)
```

### 运行目录或压缩文件：

如果\__main__.py存在，你可以简单在顶级目录运行python解释器：

python myapplication

解释器将执行\__mian__.py文件作为主程序，将你的代码打包成zip文件，这种技术同样也适用

```py
myapplication/
	spam.py
	bar.py
	grok.py
	__main__.py
```



## 包裹：

引进来import

- import time 
  - time.time()   获取当前时间  获取的是秒数，而js中获取回来的是毫秒数不一样
  - time.sleep(1)   休眠时间，里面写的是时间的长短

- import turtle   海归线
  - turtle.goto(x,y)    去（x，y）点

  - turtle.penup()     抬笔

  - turtle.pendowm()     落笔

  - turtle.circle("r")     画圆

    ```py
    import turtle
    t=turtle.Pen()
    mycolor=["red","green","black"]
    for i in range(9):          #0   1    2     3      4   
        t.color(mycolor[i%len(mycolor)])                        #0   10   20    30     40               
        t.circle(i*10+10)       #10  20   30    40     50
        t.penup()
        t.goto(0,-(i+1)*10)
        t.pendown()
    turtle.done()  #执行完命令，窗口仍然在
    ```

    

- import math   数学方法
  - math.sqrt()    求开方

- import os   操作文件、系统    os.path  文件路径
  - os.system  命令控制台
  - os.listdir()   显示目录下的内容
  - os.mkdir()   创建文件夹
  - os.path.isfile()  是否为文件
  - os.path.isdir()   是否为路径

- import io  可变字符串

  ```py
  >>> import io
  >>> s="hello,sxt"
  >>> sio=io.StringIO(s)
  >>> sio
  <_io.StringIO object at 0x0307FF80>
  >>> sio.seek(3)
  3
  >>> sio.getvalue()
  'hello,sxt'
  >>> sio.write("R")
  1
  >>> sio.getvalue
  <built-in method getvalue of _io.StringIO object at 0x0307FF80>
  >>> sio.getvalue()
  'helRo,sxt'
  >>> a="hello，syk"
  >>> sio1=io.StringIO(s)
  >>> sio1
  <_io.StringIO object at 0x035286C0>
  >>> sio1.getvalue()
  'hello,sxt'
  >>> sio1=io.StringIO(a)
  >>> sio1
  <_io.StringIO object at 0x035288F0>
  >>> sio1.getvalue()
  'hello，syk'
  >>> sio1.seek(4)
  4
  >>> sio1.write("Y")
  1
  >>> sio1.getvalue()
  'hellY，syk'
  ```

- import random 

  - random.shuffle()   打乱顺序

## 文件操作：

### 读文件：

f=open("firename",mode,encoding="utf-8",errors="ignore")

firename:操作文件地址     路径要看文件执行的路径   mode：打开文件模式

encoding="utf-8"    文件以什么形式读取     后面的是出错忽略

```py
f=open("note.txt",'r',encoding="gbk",errors="ignore")//创建一个对象，对象是打开的文件
con=f.read()// read方法，读取他里面的内容，并且把他复制到一个新的对象里
print(con)
f.close()//每次弄完一个文件，都要关闭，不关闭是错误的


f=open("note.txt","w")
for i in range(10): 
     f.write("这是第%s行"%i)//   write后面要写添加的东西
f.close()
```

```py
import os,os.path    复制多层
def copyFile(dir):
    if os.path.isfile(dir):
        f=open(dir,"r")
        con=f.readlines()
        f.close()
        f1=open("副本"+dir,"w")
        f1.writelines(con)
        f1.close()
        pass
    else:
        os.mkdir("副本"+dir)
        for item in os.listdir(dir):
            copyFile(dir+"/"+item)
copyFile("date")
```



打开模式：

- r读操作（默认）   rb以二进制的方式读写

  - f.read([num])  num代表读取字符数量，默认为全部   有的编码一个字代表连个字符
  - f.readline([num])     文件读取每一个行，通过\r\nEOF(文件结束标识)   来区别     num代表读取一行几个字符
  - f.readlines()     返回列表形式     ，包含所有的行

- w写操作  ，每次执行从头开始写入，如果么有文件，自动创建新文件、  或者说路径不对直接创建新文件    文件一打开，指针就在文件开始

  - f.write  把str写到文件中，write() 并不会在str后加上一个换行符

    ```py
    f=open("note.txt","w")  // 把一个列表通过write方法传进去，应用到了将列表转化为字符串的方法
    arr=[]
    for i in range(10):
        arr.append("这是第%s行"%i)
    con="".join(arr)
    f.write(con)
    f.close()    
    ```

  - f.writelines(seq)   把seq的内容全部写到文件中（多行一次性写入）。这个函数也只是忠实的写入，不会再每行后面加上任何东西

- a 追加    每次执行从末尾开始写入，路径不对直接创建新文件，文件一打开，指针就在文件末尾

- r+ 读写（不创建新的文件，每次读写文件在文件开头）可读可写   指针默认末尾

  ```py
  f=open("note.txt","r+",encoding="utf-8")
  f.write("abc")    他会把原来的前面三位给替换   原来是1234   现在就是abc4    utf-8里面中文占三个字节  write 默认指针在最前面，其实他是跟着指针走的
  con=f.read()   //只读原来的东西，write不影响，但是覆盖玩的肯定不会读出来的
  print(f.tell())
  f.close()
  print(con)   
  ```

  

- w+ 读写（每次创建新文件，每次读写都会覆盖原来内容）最好不要用   指针默认末尾

- a+ 读写 （创建新文件，每次读写追加）   指针在末尾   即使改变了指针的位置，添加内容他也是在后面添加，但是读文件不影响

指针seek（）： 移动文件读取指针到指定位置

- f.seek(p,0)  移动到文件第p个字节处，绝对位置
- f.seek(p,1)  移动到相对于当前位置之后的p个字节（文件必须以二进制方式打开）
- f.seek(p,2)  移动到相对文章末尾之后的p个字节（文件必须以二进制方式打开）
- tell():  返回文件读取指针的位置

f.close()   把缓冲区的内容写入硬盘，关闭文件

f.flush()  把缓冲区的内容写入硬盘

异常处理：

```py
try:
	f=open("note1.txt","r")
finally:     不管f存在或者不存在，都会执行finally，进行关闭
	if f:
		f.close()
		
		
with open("note1.txt","r") as f:  //用完即关
	f.read()
```

csv存储数据

​	csv格式是电子表格和数据库最常用的导入和导出格式

dialect="excel"=?

```py
import csv   //引入csv
with open("demo.csv","w",newline="") as f:    //newline="" 默认换行，改变使他不换行
    #以列表的方式写
    writer=csv.writer(f) //创建对象  f代表文件对象
    writer.writerow(["name","id","sex","tel"])   //单行输出
    writer.writerows([["赵堃崴","1111","男","111111"],["赵堃崴","1111","男","111111"],["赵堃崴","1111","男","111111"]])  //多行输出，记得要在外面套一个大列表
    #以字典的方式写
    # writer=csv.DictWriter(f,{"name","id","sex","tel"})    //这里是和列表不一样的，他需要输出表头
    # writer.writeheader() // 输出表头，固定方法
    # writer.writerows([{"name":"赵堃崴","id":"1111","sex":"男","tel":"111111"},{"name":"赵堃崴","id":"1111","sex":"男","tel":"111111"},{"name":"赵堃崴","id":"1111","sex":"男","tel":"111111"}])
    #以列表的方式读取
with open("demo.csv","r") as f:
    #以列表的方式读取
    # reader=csv.reader(f) //是一个生成器，不能直接运用
    # mylist=list(reader) //读取的时候，需要转换为列表形式，
    # for i in mylist:    //记得要遍历，
    #     print(i)  
    #以字典的方式读取
    reader=csv.DictReader(f)
    mylist=list(reader)
    for i in mylist:
        print(dict(i))
```



- csv_writer=csv.writer("csvfile",dialect="excel")
- csv_writer.writerow(row)   单行
- csv_csv.DictWriter()   以字典的方式写
- csv.reader(csvfile)    传入文件对象，返回生成器
- csv.DictReader(csvfile)   传入文件对象，返回生成器，每一个都在字典内

pickle模块常用方法

- pickle.dump(obj,file) 序列化对象，并将结果数据流写入到文件对象中去

  ```py
  import pickle
  obj=[{"name":"赵堃崴","sex":"男"}]   创建对象
  with open("note.txt","wb") as f:    //打开文件，以二进制方式输入
      pickle.dump(obj,f)     将对象转换为文件对象
  ```

- pickle.load(file)  序列发生变化，将文件中的数据解析为python对象

  ```py
  with open("note.txt","rb") as f:   读取文件
      obj=pickle.load(f)      将文件对象解析
      print(obj)   
  ```


## 面向对象：

#### 类语法：

- class  类名:

  方法列表

  ```py
  
  class Play:
      name="老j"   #类属性，静态变量，静态属性
      def __init__(self):   #初始化    这里面的self相当于以前学习的this，只在函数里写，外面写的话不用写，像以前的都是this.属性=""     被称为类的构造函数或初始化方法，当创建了这个类的实例时就会调用该方法
          #self 代表类的实例，self 在定义类的方法时是必须有的，虽然在调用时不必传入相应的参数。
          #self  必须写，self之后可以传入参数，self不算第一个参数
          self.name="老k"     #实例属性
      def type(self):
          print("司令")
      def property(self):   #?   self
          print("指挥")
      @staticmethod
      def tell():
          print("这是tell方法")
      @staticmethod   #静态方法  不能调用实例的方法，但同时也不能调用类的属性和方法,也不能调用类的静态方法
      def say():
          print("这是say方法")
          # cls.tell()
      @classmethod
      def say2(cls):
          print("这是say2")
      @classmethod   #类方法也不能调用实例的属性和方法，但还可以调用类属性和方法,也能调用静态方法
      def say1(cls):#cls是啥玩意
          print("这是类方法")
          print(cls.name)   #这是类的一个属性，加cls
          cls.say()  #这是类的一个方法，所以要加cls
  
  p1=Play()   # p1  实例
  p1.say1()
  #p2=Play()          #Play  类
  #print("类属性：",Play.name)
  #print("实例属性：",p1.name)   #如果里面没有实例属性，访问类属性
  # p1.name
  # p2.name
  # Play.name
  ```

#### 类属性：

定义：属性就是属于另一个对象的数据或者函数元素，可以通过我们熟悉的据点属性标识来访问

类的数据属性：类属性，静态属性，静态数据，一次修改所有实例对象全部修改

- 类属性

  ```py
  class Play:
  	name="老j"   //没有this
  ```

- 静态属性

#### 类方法：

```py
class Play:
	@classmethod     cls 代表类，
	def say(cls):   //这里需要传参数，cls   类方法第二阶梯，可以调用类属性和方法，也能调用静态方法，但不能调用实例
		print("123")
```



#### 静态类方法：

级别最低，不能调用实例，类的属性和方法，而且不能传self

```py
class Play:
	@staticmethod
	def say():    //这里不用传参
		print("123")
```

#### 类方法与静态方法：

静态方法与类方法都可以通过类或者实例来调用，其两个的特点都是不能够调用实例属性，类方法与类属性是类固有的方法与属性，不会因为实例不同而改变，写他们的目的是为了减少多实例时所创造出来的内存空间，加快运行速度

#### 特殊实例的方法：

```py
def __new__(cls):
	__new__至少有一个参数cls，代表要实例化的类，此参数在实例化时Python自动提供
	__new__必须要有返回值，返回出实例化的实例，这点在自己实现__new__时要特别注意，可以return父类__new__出来的实例，或者直接是object的__new__出来的实例


def __int__(self):
	作用是初始化实例，有一个参数self，这个就是self实例化出来的实例，__init__在__new__的基础上可以完成一些初始化的动作，__init__不需要返回值

def __str__(self):   #给实例一个描述，在输出实例的时候才会执行
     return "这是一个汽车实例"
def __repr__(self):   #给实例一个描述，在输出实例的时候才会执行
     return "这是一个汽车实例"
def __del__(self):   #当你实例被注销的时候会执行
     print("实例被删除")
```

#### 特殊的类属性：

```py
class Car:
    '''
     Car是一个汽车类
     '''
     def __new__(cls):
         return object.__new__(cls)
     def __init__(self):  #只有在创建了实例对象才能调用此方法
         self.pp="大众"
     def run(self):
         print("运行")

     def __str__(self):   #给实例一个描述，在输出实例的时候才会执行
         return "这是一个汽车实例"
     def __repr__(self):   #给实例一个描述，在输出实例的时候才会执行
         return "这是一个汽车实例"
     def __del__(self):   #当你实例被注销的时候会执行
         print("实例被删除")
 print(Car.__name__)  #类名
 print(Car.__doc__)   #对类的描述  注释
 print(Car.__bases__)  #所有的父类  返回一个元组
 print(Car.__base__)   #父类
 print(Car.__dict__["_init_"])  #返回所有的方法，以字典的形式
 print(Car.__module__)   #返回类所在的模块   __main__
 print(Car.__class__)   #返回类对应的类  <class"type">
```



#### 对象的继承和派生:

- 继承  基类（base class）/超类（super class）/父类（father class） 任何类都直接或间接继承objects类，objects是一切类的基类

  ```pys
  class B:
      name="这是类属性"
      def __init__(self):
          self.name="B"
      def say(self):
          print("这是B类")
      @staticmethod    #静态方法不需要传参数
      def say1():
          print("这是B的静态方法")
      @staticmethod
      def ss():
          print("s")
      @classmethod
      def say2(cls):
          print("这是B的类方法")
  class A(B):
      name="这是A的类属性"
      def __init__(self):
          self.name="A"
  a=A()   //括号有特殊含义，继承性质
  a.say()
  a.say1()
  a.say2()
  a.ss()
  
  就近原则，深度优先
  class D:
      def say(self):
          print("这是D类")
  class E:
      def say1(self):
          print("这是E类")
  class C(E):
      def say(self):
          print("这是C类")
  class B(D):
      def say3(self):
          print("这是B类")
  class A(B,C):
      pass
  a=A()
  a.say()   先从B里面找，找完，再从C里面找
  会输出“这是D类”
  
  ```

  

- 派生：派生类（derived class）/子类(child class)  派生就是子类在继承父类的基础上衍生出新的属性。子类中独有的，父类中没有的，或子类定义与父类重名的东西。子类也叫派生类

  ```py
  class myfloat(float):
      def __new__(cls,val):
          return float.__new__(cls,round(val,3))
      def __init__(self,val):
          self.num=val
      def get(self,type):
          return "%0.2f%s"%(self.num,type)
  num1=myfloat(1.33345)
  print(num1)
  num1.get("￥")
  ```

  


#### 类的内建方法:（魔法方法，双下划线）

- issubclass（sub，parent）  判断是否为parent的子类，返回bool
- isinstance（ins，class）  判断ins是否为class的实例，返回bool
- hasattr（obj，“attr”）判断obj中是否有attr属性  返回bool
- getattr（obj，“attr”）获取obj中attr属性
- setattr（obj，attr.value）设置obj中attr属性
- delattr（obj，attr）删除obj中attr属性
- dir（）列出类或实例的属性和方法，以列表的形式
- vars（object）函数返回对象object的属性和属性值的字典对象
- super（）寻找父类元素super（type，[,object-or-type]）super().xxx  代替 super(Class,self) .xxx ??

#### 实例的魔法方法：

- \__new__ 创建对象
- \__init__ 实例属性
- \__str__实例被输出时执行
- \__rep__实例被输出时执行
- \__del__     当实例被注销时执行
- \__dir__  返回实力属性和方法   列表形式

#### 封装：

> 对内部数据进行保护（隐藏），或者合理的暴露

```py
class Car:
def __init__(self):
	self.__name="q"
def getname(self):
	return self.__name
def setname(self,var):
	self.__name=var
c=Car()
print(c.__name)
print(c.getname())

```

#### 单例模式:

```py
class Dz():
    def __init__(self):
        self.type="大众"
    def start(self):
        print("开始")
    def stop(self):
        print("停止")
class Bm():
    def __init__(self):
        self.type="宝马"
    def start(self):
        print("开始")
    def stop(self):
        print("停止")
class Carfactory:
    def Carmethod(self,type):
        if type=="bm":
            obj=Bm()
        elif type=="dz":
            obj=Dz()
        return obj
c=Carfactory()
a=c.Carmethod("bm")//生成的实例调用类方法，产生一个新的实例
print(a.type)


class Person:
    __instance=None
    def __new__(cls):
        if cls.__instance==None:
            cls.__instance=object.__new__(cls)
        return cls.__instance
    def __init__(self):
        self.name=""
    def aa(self):
        print(self.name)
p=Person()
p3=Person()
p1=Person()
p2 = Person()
p4=Person()
p2.name="ss"   在创建完所有对象之后，改变属性，所有的都会改变，但是在修改完之后，在创建一个，则所有对象的属性全部青空
p1.aa()
p2.aa()
p3.aa()
p4.aa()
print(id(p2))
print(id(p3))
```



### 高级异常：

异常：

- 错误，从软件方面来说，错误是语法或逻辑上的

  - 语法错误是指软件结构上的错误，导致不能被解释器或者编译器无法编译。这些错误必须在程序执行前纠正
  - 逻辑错误可能是由于不完整或者是不合法的输入导致。也可能是逻辑无法生成，计算，或者是输出结果需要的过程无法执行

- 异常：因为程序出现了错误而在正常控制流以外采取的行动异常分为两个阶段

  - 第一阶段：发生异常

  - 第二阶段：异常处理

    当python检测到一个错误时，解释器就无法继续执行了，反而出现了一些错误提示，这就是所谓的异常,例如

    ```py
    print"----text--1--"
    open("123.txt","r")
    print"---text---2"
    //当打开一个不存在的文件，当找不到123.txt文件时，就会抛出一个IOError类型的错误，Nosuch file or directory：123.txt(没有123.txt这样的文件或目录)
    try:
    	num=int(input("请输入数字："))
    	print(num)
    except:
    	print("输入不正确，请输入符合要求的数据")//如果没有捕获异常的话，会直接报错
    ```

  - 异常原理：

    try的工作原理，当开始一个try语句时，python就在当前程序的上下文做标记，这样异常出现时就可以回到这里，try子句先执行，接下来发生什么依赖于发生了什么异常

    - 如果当try语句执行时发生异常，python就会条回到try并执行第一个匹配该异常的excep语句，异常处理完毕，控制流就通过整个try语句
    - 如果try语句发生异常，却没有匹配except语句，异常将递交上层try，或者到程序的最上层，终止程序，并输出出错信息
    - 如果try语句执行时没有发生异常，python将执行else语句后的程序，然后控制流通过整个try

  - 捕获多个异常：

    ```py
    try:
    	print(1/0)
    except ZeroDivisionError as e: //获取异常信息
    	print(e)
    except ValueError: 
    	print('ValueError')
    except (AttributeError,LookupError): 
    	print("出错")
    else:    //当没有捕获到异常时，执行的模块
    	print("没有错误")
    finally:
        print("不管有没有异常，都应该执行的代码")
    ```

  - 异常传递

    ```py
    def C():
    	return 1/0
    def B():
    	C()
    def A():
    	try:
    		B()
    	except 	Exception as e:
    		print(e)
    A()
    
    ```

  - 自定义异常???

    ```py
    class myExcept(Exception):
    	def __init__(self):
    		self.name="这是我定义的异常"
    num=int(input("请输入一个数"))
    if num<0:
    	raise myExcept
    
    
    class myExcept(Exception):
    	def __init__(self):
    		self.name="这是我定义的异常"
    num=int(input("请输入一个数"))
    if num<0:
    	try:
    		raise myExcept
    	except myExcept:
    		print("捕获到myExcept")
    
    
    class myExcept(Exception):
    	def __init__(self,info):
    		self.name="这是我定义的异常"
    		self.info=info   #提示信息
    num=int(input("请输入一个数"))
    if num<0:
    	try:
    		raise myExcept("myExcept错误")
    	except myExcept as e :
    		print(e)
    ```

- 总结

  - except语句不是必须的，finally语句也不是必须的，但是二者必须要有其中一个，否则就没有try的意义
  - Except语句可以有多个，Python会按照except语句的顺序依次匹配你指定的异常，如果异常已经处理，就不会进入后面的except语句
  - except语句可以以元组形式同时指定多个异常
  - except语句后面如果不指定异常类型，则默认捕获所有异常，你可以通过logging或sys模块获取当前异常
  - 如果要捕获异常后重复抛出，请使用raise，后面不要带任何参数或信息
  - 不建议捕获或抛出同一个异常



qqbot     图灵机器人

### 内置函数：

```py
all()  all(x) 是针对x对象的元素而言，如果all(x)参数x对象的所有元素不为0、”、False或者x为空对象，则返回True，否则返回False 
any()  any(x)是判断x对象是否为空对象，如果都为空、0、false，则返回false，如果不都为空、0、false，则返回true
```

### python基础知识点：

python程序的文件扩展名称是py和pyw，后者是带GUI的脚本

py
py就是最基本的源码扩展名。windows下直接双击运行会调用python.exe执行。

pyw
pyw是另一种源码扩展名，跟py唯一的区别是在windows下双击pyw扩展名的源码会调用pythonw.exe执行源码，这种执行方式不会有命令行窗口。主要用于GUI程序发布时不需要看到控制台信息的情况。

pyc
在执行python代码时经常会看到同目录下自动生成同名的pyc文件。这是python源码编译后的字节码，一般会在代码执行时自动生成你代码中引用的py文件的pyc文件。这个文件可以直接执行，用文本编辑器打开也看不到源码。

pyo
pyo是跟pyc类似的优化编码后的文件。

pyd
##### pyd并非从python程序生成，而是其他语言写成的可以被python调用的扩展

### python题库：

print(int('101',2))    把二进制101转换为整型十进制

print(1, 2, 3, sep=':')   结果为 1:2:3

print(int(9**0.5))    9的0.5次方

sort  函数的返回值是啥？  sort直接改的是原列表，sorted生成一个新的数组