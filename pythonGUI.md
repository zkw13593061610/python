## pythonGUI

### 插入文本：

```py
# import tkinter as tk    导入模块

# window=tk.Tk()   #创建窗口

# window.title("我的窗口")   #设置窗口的title

# window.geometry("400x200")  #设置窗口尺寸

# window.resizable(0,0)   #重置尺寸的范围  只要是0，都拖不动，只要不是零，都能放大变小

 

 

# #label  标签

# #str1=tk.StringVar()

# #str1.set("abc")

# img1=tk.PhotoImage(file="cedao1.png",width=200)  插入图片，图片必须是png格式或者gif格式，而且暂时没法设置图片大小，只会改变labe标签的大小                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       

# l1=tk.Label(window,text="hello world",font=("",20,"bold italic"))  #实例化label  第一个参数是主窗口

# #l1["text"]="hello world"   内容

# l1["font"]=("",20,"bold italic")   #字体  元组（字体，大小，倾斜或者加粗）

# l1["bg"]="#ff6700"    #背景色

# l1["foreground"]="#fff"  #前景色

# l1["height"]=2

# l1["width"]=20  #类似行

# l1["anchor"]="c"    #文本位置   n北,s南,e东,w西,c中间

# #l1["value"]="this is value"

# # l1["variable"]=

# l1["image"]=img1

# #Button 按钮

# num=0

# def aa():

#     global num

#     l1["text"]=str(num)

#     num+=1

# b1=tk.Button(window,text="点击",width=20,height=1,bg="#333",fg="#fff",command=aa)

# l1.pack()   #布局   相当于与是添加到页面中

# b1.pack()

 

 

# window.mainloop()   #进行事件循环



```

### 插入文本域，组件，单选按钮：

```py
import tkinter as tk

window=tk.Tk()

window.title("my window")

window.geometry("600x400")

 

#输入组件

e=tk.Entry(window)

e["selectbackground"]="red"   #选中文字的背景色

e["selectforeground"]="blue"   #选中文字的颜色

e["show"]=""    #将输入的显示为""

#文本域组件

t=tk.Text(window)

#button

def fn():

    val=e.get()

    t.insert("end",val)  #末尾插入

b1=tk.Button(window,text="after",command=fn)

def fn1():

    val=e.get() 

    t.insert("insert",val)   #insert   鼠标指定位置插入

b2=tk.Button(window,text="insert",command=fn1)

e.pack()

b1.pack()

b2.pack()

t.pack()

window.mainloop()  #让程序一直在执行



import tkinter as tk

window=tk.Tk()

window.title("my window")

window.geometry("600x400")

 

 

# l1 =tk.Label(window,text="",width=20,height=3,bg="red",fg="#fff",font=("",20))

 
# v1=tk.Variable()

# v1.set("1")#设置默认值  本来都有点，随便设置一个即为空   他与0或者1没有关系

# def aa():

#     con=v1.get()

#     l1["text"]="这是%s"%con

# r1=tk.Radiobutton(window,text="A",variable=v1,value="A",command=aa)  #点击它的时候 改变它的默认值

# r2=tk.Radiobutton(window,text="B",variable=v1,value="B",command=aa)

# r3=tk.Radiobutton(window,text="C",variable=v1,value="C",command=aa)

# r4=tk.Radiobutton(window,text="D",variable=v1,value="D",command=aa)

 

# l1.pack()

# r1.pack()

# r2.pack()

# r3.pack()

# r4.pack()



```



### 登录：

```py
import tkinter as tk
window=tk.Tk()
window.title("登录界面")
window.geometry("600x400")
username,password=False,False
a=username
b=password
def isok():
    if a and b:
        btn1["state"]="normal"

def intrue():
    u=e1.get()
    p=e2.get()
    if u=="1234567890"  and p=="1234567890":
        tk.Label(window,text="登陆成功").place(x=100,y=300)
    else:
        tk.Label(window,text="登陆失败").place(x=100,y=300)
        btn1["state"]="disable"

def fn1():
    if len(e1.get())>=10:
        l1["text"]="成功"
        l1["foreground"]="green"
        global a
        a=True
        isok()
        
        return True
    else:
        return False
def fn2():
    l1["text"]="长度不足十位"
    l1["foreground"]="red"

def fn3():
    if len(e2.get())>=10:
        l2["text"]="成功"
        l2["foreground"]="green"
        global b
        b=True
        isok()
        return True
    else:
        return False
def fn4():
    l2["text"]="长度不足十位"
    l2["foreground"]="red"

tk.Label(window,text="用户名").place(x=40,y=40)
e1=tk.Entry(window,validate="focusout",validatecommand=fn1,invalidcommand=fn2)
e1.place(x=100,y=40)  定位的时候就不用写添加到页面中了

l1=tk.Label(window)
l1.place(x=300,y=40)
tk.Label(window,text="密码").place(x=40,y=100)
e2=tk.Entry(window,validate="focusout",validatecommand=fn3,invalidcommand=fn4)        validatecommand必须返回true或者false
e2.place(x=100,y=100)

l2=tk.Label(window)
l2.place(x=300,y=100)
btn1=tk.Button(window,text="登录",command=intrue)
btn1.place(x=100,y=140)
btn1["state"]="disable"
btn1["activebackground"]="#ff6700"   #活跃的时候的前景色
btn1["activeforeground"]="#ff2222"    #活跃的时候的背景色

btn2=tk.Button(window,text="注册")
btn2.place(x=200,y=140)
btn2["state"]="normal"
btn2["activebackground"]="#ff6700"
btn2["activeforeground"]="#ff2222"

window.mainloop()
```

### 多选按钮：

```py
import tkinter as tk
window=tk.Tk()
window.title("w")
window.geometry("600x400")
window.resizable(0,0)


#checkbutton
v1=tk.Variable()
v2=tk.Variable()
v1.set("3")
v2.set("3")
def fn():
    con1=int(v1.get())
    con2=int(v2.get())
    print(con1,con2)
    if con1==1 and con2==0:
        l1["text"]="我喜欢看电影"
    elif con1==0 and con2==1:
        l1["text"]="我喜欢敲代码"
    elif con1==1 and con2==1:
        l1["text"]="都喜欢"
    else:
        l1.config(text="都不喜欢")

l1=tk.Label(window,width=60,height=3,bg="#333",fg="#fff",font=("",24))
l1.pack()
c1=tk.Checkbutton(window,text="看电影",variable=v1,command=fn)    #variable=v1 到底是啥意思？
c1.pack()
c2=tk.Checkbutton(window,text="敲代码",variable=v2,command=fn)
c2.pack()

window.mainloop()
```

### 列表：

```py
import tkinter as tk
window=tk.Tk()
window.title("w")
window.geometry("600x400")
window.resizable(0,0)

#listbox
l1=tk.Label(window,width=10,height=1,bg="#333",fg="#fff")
l1.pack()

e=tk.Entry(window)
e.pack()
def fn1():
    arr=lx1.curselection()  #返回选中数据的下标，返回一个元组
    con=e.get()   #输入框文本
    if len(con)==0:
        return
    if len(arr)==0:
        lx1.insert("end",con)
    elif len(arr)==1:
        lx1.insert(arr[0]+1,con)   //arr是一个元祖，它的下标是一个数字，insert的第一个参数应该是下标，只写arr是无法相加的
    else:
        num=1
        for i in arr:
            lx1.insert(i+num,con)
            num+=1

b1=tk.Button(window,text="插入",command=fn1)
b1.pack()
lx1=tk.Listbox(window,selectmode="extended")    #selectmode="extended" 指定为多选
lx1.insert(0,"北京")

for item in ["上海","广州","深圳"]:
    lx1.insert("end",item)

lx1.pack()
def fn():
    print(lx1.curselection())

b=tk.Button(window,text="点击")


window.mainloop()
```

### 插入滑块和数字框

```py

import tkinter as tk
window=tk.Tk()
window.geometry("600x300")
window.resizable(0,9)

l1=tk.Label(window)

l1.config({
    "text":"this is label",
    "fg":"red",
    "bg":"#333",
    "font":("",20,"bold italic")
})

def fn1(v):
    l1['text']=h1.get()
    s1.set(h1.get())     获取滑块里面的值，需要在函数里面传参数，参数v就是滑块的值
h1=tk.Scale(window,command=fn1)
h1.config({
    "orient":tk.HORIZONTAL,  #水平方向    默认竖直方向
    "from":0,
    "to":200,
    "length":200,
    "resolution":1,    #步进值
    "digits":5,     #有效数字的位数
    "tickinterval":10,     #间隔的刻度  最小为步进值的一半
    "showvalue":0,#  bool 1 0 显示刻度条上面的的值   默认为1
    "label":"温度"  #给滑块添加标签 滑块的说明
})
def fn2(v):
    l1['text']=v
    h1['value']=v   #数字框里面没有set属性，只能改变他的value值
    h1['value']=""    #数字框里面的value值一旦设定没法改变，只能让他改变后得值进行清空,然后在进行改变
s1=tk.Scale(window,command=fn2)
s1.config({
    'orient':tk.HORIZONTAL,
    'from':0,
    'to':200,
    'resolution':1,
    'tickinterval':30,
    'length':200,

})
s1.pack()

l1.pack()
h1.pack()


#Spinbox   数字框     
shu=tk.Spinbox(window)
shu.pack()
shu["values"]=("北京","上海","广州")    这里有个比较特殊的就是有个属性values，可以直接用
shu.config({
    "from":0,  #从什么开始
    "to":200,  #到什么结束   但是自己可以写，鼠标不能调
    "width":20,
    #"value":50,   #设置固定值
    "command":fn3
})
```

### 画布：

```py
import tkinter as tk
window=tk.Tk()
window.geometry('600x400')
window.resizable(0,0)

画布出了本身的属性外，其往里面添加的东西都是需要重新创建一个，不能直接在里面添加

#canvas  
canvas=tk.Canvas()   画布比较特殊，这里面不需要传window就可以呈现在窗口中
canvas.config({
    'width':500,
    'height':500,
    'bg':'#999',
})
img1=tk.PhotoImage(file='cedao1.png',width=100,height=130)   这里面的高度和宽度搞不清楚是啥玩意
cimg=canvas.create_image(100,0,image=img1)   #前面的是x，y的位置    插入图片
cline=canvas.create_line(0,0,200,100,fill='red')   #定义一条线  初始位置，结束位置
carc=canvas.create_arc(200,200,300,300,extent=20,start=90,fill="blue")  #   画一个扇形  extent 为设置角度     start 开始位置 画角度    fill   为填充   前两个参数是位置，后两个参数是宽高
coval=canvas.create_oval(300,300,350,350,fill="yellow")    #画圆,前面连个参数是位置，后面两个参数是宽和高
ctext=canvas.create_text(50,50,text="Python",font=("",20))  #添加文本
cp=canvas.create_polygon(0,0,0,100,100,100,fill="green")   #多边形   前两个参数是第一个点的起点 以此类推
cr=canvas.create_rectangle(300,200,200,210,fill='pink')   #矩形   前两个参数是第一个点的位置，后两个参数是最后一个点的位置

def fn1():
    canvas.move(cr,-50,-50)  移动位置
b1=tk.Button(text='click',command=fn1)
b1.pack()
canvas.pack()
window.mainloop()
```

### 菜单：

```py
import tkinter as tk
window=tk.Tk()
window.geometry('600x400')
window.resizable(0,0)

yuyan=tk.Variable()
yuyan.set('1')

#菜单栏   Menu
menubar=tk.Menu(window)  #创建菜单栏
menu1=tk.Menu(menubar,tearoff=0)   #创建菜单项     tearoff 设置默认，不让移出

menu1.add_command(label='新建文件')   #添加内容
menu1.add_command(label='新建窗口')   #添加内容

menu1.add_separator()  #设置分割线

menu1.add_command(label='打开文件')
menu1.add_command(label='打开文件夹')
menu1.add_command(label='打开工作区')

menu1_2=tk.Menu(menu1,tearoff=False)
menu1_2.add_command(label='重新打开已关闭的编辑器')
menu1_2.add_command(label='更多')
menu1_2.add_command(label="清除最近的打开记录")

menu1.add_cascade(label='打开最近的文件',menu=menu1_2)

menu1.add_separator()

menu1.add_command(label='将文件添加到工作区')
menu1.add_command(label='将工作区另存为')

menu1.add_separator()

menu1.add_command(label='保存')
menu1.add_command(label='另存为')
menu1.add_command(label='全部保存为')

menu1.add_separator()

menu1.add_checkbutton(label="自动保存")

menu1_1=tk.Menu(menu1,tearoff=False)
menu1_1.add_command(label="设置")
menu1_1.add_command(label="键盘快捷方式")
menu1_1.add_command(label="按键映射扩展")
menu1_1.add_command(label="用户代码片段")
menu1_1.add_command(label="颜色主题")
menu1_1.add_command(label="文件图片主题")

menu1.add_cascade(label='首选项',menu=menu1_1)

menu1.add_separator()

menu1.add_command(label='还原文件')
menu1.add_command(label='关闭编辑器')
menu1.add_command(label='关闭文件夹')
menu1.add_command(label='关闭窗口')

menu1.add_separator()

menu1.add_command(label='退出')

menu2=tk.Menu(menubar,tearoff=0) 
menu3=tk.Menu(menubar,tearoff=0) 
menu4=tk.Menu(menubar,tearoff=0) 
menu5=tk.Menu(menubar,tearoff=0) 
menu6=tk.Menu(menubar,tearoff=0) 
menu7=tk.Menu(menubar,tearoff=0) 
menu8=tk.Menu(menubar,tearoff=0) 



menubar.add_cascade(label='文件(F)',menu=menu1)  #添加菜单项,这里会用到cascade方法
menubar.add_cascade(label='编辑(E)',menu=menu2)
menubar.add_cascade(label='选择(S)',menu=menu3)
menubar.add_cascade(label='查看(V)',menu=menu4)
menubar.add_cascade(label='转到(G)',menu=menu5)
menubar.add_cascade(label='调试(D)',menu=menu6)
menubar.add_cascade(label='任务(T)',menu=menu7)
menubar.add_cascade(label='帮助(H)',menu=menu8)

#语言选项
def fn1():
    print(yuyan.get())
menu1_2=tk.Menu(menu1,tearoff=False)
menu1.add_cascade(label='语言',menu=menu1_2)
menu1_2.add_radiobutton(label='汉语',variable=yuyan,value=0,command=fn1)
menu1_2.add_radiobutton(label='英语',variable=yuyan,value=1,command=fn1)

menu1_2.add_radiobutton(label='俄语',variable=yuyan,value=2,command=fn1)


window.configure(menu=menubar)   把菜单栏添加到窗口中，只有这个会用到configure
window.mainloop()
```

### 右键菜单：

```py
import tkinter as tk
window=tk.Tk()
window.geometry('600x400')
window.resizable(0,0)


menubar=tk.Menu(window,tearoff=False)
for item in ['css','html','javascript','python']:
    menubar.add_command(label=item)
def click(e):
    # menubar.post(0,0)   #绝对定位  在最上面
    menubar.post(e.x_root,e.y_root) 
window.bind('<Button-3>',click)  #给鼠标右键添加一个事件   点击是在窗口中点击

window.mainloop()
```

### 布局：

```py
三种布局方式
1.相对定位  pack  组件的大小会随着窗口的大小而改变，但是x轴最小只能缩到它的宽度，但是y轴可以缩到最小
f1.pack(expand=1)   只写这句话会让他定位在最中间   那是因为expand是设置他的伸展性，相当于是他左右上下全部都扩展了，再加一个只会让他把所有的空间全部平均分配
	fill 填充
	f1.pack(expand=1,fill=tk.BOTH) 只写x是x轴
	如果位置在中间，默认x轴expand为1，y轴为0
	如果位置在两边，正好相反
	
	
	
import tkinter as tk
window=tk.Tk()
window.geometry('600x400')
# window.resizable(0,0)





#布局
#三种布局方式
#pack   相对布局：组件的大小和位置会随着窗口的大小而改变
#place  绝对布局：组件的大小和位置不会随着窗口的大小而改变
#grid   网格布局：通过表格形式进行布局
# f1=tk.Frame(window,width=200,height=200,bg='blue')
# f1.pack(anchor='n')
# f1=tk.Frame(window,width=200,height=200,bg='red')
# f1.pack(anchor='s')
# f1=tk.Frame(window,width=200,height=200,bg='tan')
# f1.pack(anchor='e')
# f1=tk.Frame(window,width=200,height=200,bg='pink')
# f1.pack(anchor='w')


# f1=tk.Frame(window,width=200,height=200,bg='blue')
# f1.pack(side=tk.LEFT)



# f1=tk.Frame(window,width=200,height=200,bg='blue')

# f2=tk.Frame(window,width=200,height=200,bg='pink')

# f3=tk.Frame(window,width=200,height=200,bg='green')


# f2.pack(side=tk.TOP,fill = tk.X)
# f3.pack(side=tk.BOTTOM)
# f1.pack(fill=tk.Y,side=tk.LEFT,anchor="w")      #???





#anthor  锚位置，当剩余空间远远大于所需空间
#side = top left right bottom      tk.TOP tk.BOTTOM tk.LEFT tk.RIGHT 对齐方式
#fill   填充    tk.X  tk.Y  'x' 'y'
#expand  扩充，展开

#padx/pady( 外间距)
#ipadx/ipady(内间距)
# f2=tk.Frame(window,width=200,height=200,bg='red')
# f2.pack(side=tk.TOP,fill=tk.X)      
# f3=tk.Frame(window,width=200,height=200,bg='tan')
# f3.pack(side=tk.RIGHT)
# f4=tk.Frame(window,width=200,height=200,bg='pink')
# f4.pack(side=tk.BOTTOM)

# b1=tk.Button(f2,text='click1')
# b2=tk.Button(f2,text='click2')
# b1.pack(side=tk.RIGHT,fill=tk.X)   #不设置的话，默认expand为0
# b2.pack(side=tk.RIGHT,fill=tk.X,expand=1,padx=10,pady=10,ipadx=20,ipady=20)
# b2.pack_forget()   #让b2隐藏，相当于以前的display:none，但是想出现还得重写一遍上面的代码

# #x/y  相对于父元素的偏移量
# #relx/rely 相对于父元素
# #width/height     指定容器的宽度和高度
# #relx,rely,relwidth,relheight [0-1]   参照于父元素位置，宽度和高度
# f1=tk.Frame(window,width=200,height=200,bg='red')
# # f1.place(x=100,y=100)
# f1.place(x=100,y=100)



# f2=tk.Frame(f1,width=100,height=100,bg='blue')
# # f2.place(x=10,y=10)
# f2.place(relx=0.5,rely=0.5)
#f2.place_forget()


#row/column   行与列
#columnspan   横跨两列   但不会改变框的大小
#rowspan   横跨两行
#sticky   组建在表格内的对齐方式  4个方向

# b1=tk.Button(window,width=6,height=6,text='click1')
# b2=tk.Button(window,width=6,height=6,text='click2')
# b3=tk.Button(window,width=6,height=6,text='click3')
# b4=tk.Button(window,width=6,height=6,text='click4')
# b5=tk.Button(window,width=6,height=6,text='click5')

# b1.grid(row=0,column=0,padx=10,pady=10)
# b2.grid(row=0,column=1)
# b3.grid(row=1,column=0)
# b4.grid(row=1,column=1,columnspan=2)
# b5.grid(row=0,column=3)

# expand  需要看一下，一般默认为零，但在横向的时候，默认为1
f1=tk.Frame(window,width=100,height=100,bg='red')
f2=tk.Frame(window,width=100,height=100,bg='green')

f3=tk.Frame(window,width=100,height=100,bg='blue')

f4=tk.Frame(window,width=100,height=100,bg='black')

f1.pack(side=tk.RIGHT)
f2.pack(side=tk.RIGHT)
f3.pack(side=tk.BOTTOM)
f4.pack(side=tk.LEFT)

# f1.pack(fill=tk.X)
# f1.pack(fill=tk.Y,expand=1)
# f1.pack(side=tk.LEFT,fill=tk.X,expand=1)
# f1.pack(side=tk.LEFT,fill=tk.Y)
# f1.pack(side=tk.LEFT,fill=tk.X,expand=1)



window.mainloop()
	

```

### 计算器：

```py
import tkinter as tk 
class Mywindow(tk.Tk):
    def __init__(self):
        super().__init__()
        self.createmenu()
        self.createscreen()
        self.keys=[
            ['MC','MR','MS','M+','M-'],
            ['→','CE','c','±','√'],
            ['7','8','9','/','%'],
            ['4','5','6','*','1/x'],
            ['1','2','3','-','='],
            ['0','.','+'],

        ]
        self.createbtns()
    def createmenu(self):
        menubar=tk.Menu(self)
        self.configure(menu=menubar)
        menu1=tk.Menu(menubar,tearoff=False)
        menu1.add_command(label='标准型')
        menu1.add_command(label='科学型')
        menu1.add_cascade(label='查看',menu=menu1)
        menu2=tk.Menu(menubar,tearoff=False)
        menu2.add_command(label='复制')
        menu2.add_command(label='粘贴')
        menubar.add_cascade(label='编辑',menu=menu2)
    def createscreen(self):
        self.screen=tk.Label(self,text='screen',bg='#ccc',height=3,anchor='e',fg='#fff',font=('',20))
        self.screen.grid(row=0,column=0,columnspan=5)
    def createbtns(self):
        for arr in self.keys:
            for item in arr:
                if self.keys.index(arr)==4 and arr.index(item)==4:
                    tk.Button(self,text=item,width=10,height=11,font=('',10)).grid(row=self.keys.index(arr)+1,column=arr.index(item),rowspan=70)
                    continue
                if self.keys.index(arr)==5 and arr.index(item)==0:
                    tk.Button(self,text=item,width=22,height=5,font=('',10)).grid(row=self.keys.index(arr)+1,column=arr.index(item),columnspan=2)
                    continue
                if self.keys.index(arr)==5 and arr.index(item)==1:
                    tk.Button(self,text=item,width=10,height=5,font=('',10)).grid(row=self.keys.index(arr)+1,column=arr.index(item)+1)
                    continue
                if self.keys.index(arr)==5 and arr.index(item)==2:
                    tk.Button(self,text=item,width=10,height=5,font=('',10)).grid(row=self.keys.index(arr)+1,column=arr.index(item)+1)
                    continue
                tk.Button(self,text=item,width=10,height=5,font=('',10)).grid(row=self.keys.index(arr)+1,column=arr.index(item),pady=5,padx=5)



if __name__=="__main__":
    window=Mywindow()
    window.mainloop()
```

### 事件：

```py
#事件
import tkinter as tk 
window=tk.Tk()
window.geometry('600x400')

#鼠标事件
#单击事件
# window.bind('<Button-1>',lambda x:print('左击'))  #第一个参数是事件名，第二个是函数
# window.bind('<Button-2>',lambda x:print('中间滚轮'))
# window.bind('<Button-3>',lambda x:print('右击'))
#双击事件
# window.bind('<Double-Button-1>',lambda x:print('左击'))
# window.bind('<Double-Button-2>',lambda x:print('中间点击'))
# window.bind('<Double-Button-3>',lambda x:print('右击'))
# #三击事件
# window.bind('<Triple-Button-1>',lambda x:print('左击三击'))
# window.bind('<Triple-Button-2>',lambda x:print('中间点击'))
# window.bind('<Triple-Button-3>',lambda x:print('右击三击'))


#window.bind('<B1-Motion>',lambda x:print('左键移动'))  左键按下移动



# window.bind('<ButtonRelease-1>',lambda x:print('左键抬起'))


# window.bind('<Enter>',lambda x:print('鼠标移入'))
# window.bind('<Leave>',lambda x:print('鼠标移出'))


#滚轮事件
# window.bind('<Button-4>',lambda x:print('向上滚动'))
# window.bind('<Button-5>',lambda x:print('向下滚动'))


#键盘事件

e=tk.Entry(window)
e.pack()
# e.bind('<Key>',lambda x:print('键盘按下'))
# e.bind('<KeyRelease>',lambda x:print('键盘抬起'))


# e.bind('<Return>',lambda x:print('回车'))
# e.bind('<Up>',lambda x:print('上'))
# e.bind('<Down>',lambda x:print('下'))
# e.bind('<Right>',lambda x:print('左'))
# e.bind('<Left>',lambda x:print('右'))

# e.bind('<Shift_L>',lambda x:print('shift_l'))
# e.bind('<Shift_R>',lambda x:print('shift_r'))
# e.bind('<Control_L>',lambda x:print('control_r'))
# e.bind('<Shift_R>',lambda x:print('shift_r'))
# e.bind('<Alt_L>',lambda x:print('Alt_r'))
# e.bind('<A>',lambda x:print('A'))
# e.bind('<a>',lambda x:print('a'))
# e.bind('<Shift-R>',lambda x:print('Shift+r'))
e.bind('<Shift-R>',lambda e:print(dir(e)))

#事件对象
# keykode  键盘码
# keysym   键盘符
# char     字符
# widget   事件源
# x
# y
# x_root
# y_root
```

### 弹框：

```py
import tkinter as tk 
from tkinter import messagebox
#弹框


window=tk.Tk()
window.geometry('600x400')



def fn():
    # tk.messagebox.showerror(title='error',message='代码出现错误')
    # tk.messagebox.showinfo(title='info',message='你选择的是科学型计算机')
    # tk.messagebox.showwarning(title='warning',message='这是一个警告')
    # b=tk.messagebox.askyesno(title='ask',message='确定关闭吗')
    # print(b)
    # c=tk.messagebox.askokcancel(title='ask',message='确定退出吗')
    # print(c)   返回布尔值
    # d=tk.messagebox.askquestion(title='ask',message='是否关闭')
    # print(d)  #返回yes和no
    # e=tk.messagebox.askretrycancel(title='ask',message='程序未响应，是否退出')
    #print(e)
    f=tk.messagebox.askyesnocancel(title='ask',message='是否退出')
    print(f)   #返回true false none

button=tk.Button(window,text='click',command=fn)

button.pack()

window.mainloop()
```

### 新建文件：

```py
import tkinter as tk 
from tkinter import messagebox

class Application(tk.Tk):
    def __init__(self):
        super().__init__()
    def com1(self):
        tk.messagebox.showinfo(message='新建文件')

class Addmenu:
    def __init__(self,window):
        self.window=window
        self.menubar=tk.Menu(window)
        self.window.configure(menu=self.menubar)
        self.createfile()
    def createfile(self):
        menu1=tk.Menu(self.menubar,tearoff=0)
        menu1.add_command(label='新建文件',command=self.window.com1)
        menu1.add_command(label='保存文件')
        self.menubar.add_cascade(label='文件',menu=menu1)

if __name__=="__main__":
    window=Application()
    Addmenu(window)
    window.mainloop()
```

### 事件:

```py
#事件
import tkinter as tk 
window=tk.Tk()
window.geometry('600x400')
def click1(e):   调用函数的时候必须传参
    print('左击')
window.bind('<Button-2>',click1)
#鼠标事件
#


单击事件
# window.bind('<Button-1>',lambda x:print('左击'))  #第一个参数是事件名，第二个是函数     lambda匿名函数，表达式结果就是返回值，不需要再写返回值
# window.bind('<Button-2>',lambda x:print('中间滚轮'))
# window.bind('<Button-3>',lambda x:print('右击'))
#双击事件
# window.bind('<Double-Button-1>',lambda x:print('左击'))
# window.bind('<Double-Button-2>',lambda x:print('中间点击'))
# window.bind('<Double-Button-3>',lambda x:print('右击'))
# #三击事件
# window.bind('<Triple-Button-1>',lambda x:print('左击三击'))
# window.bind('<Triple-Button-2>',lambda x:print('中间点击'))
# window.bind('<Triple-Button-3>',lambda x:print('右击三击'))


#window.bind('<B1-Motion>',lambda x:print('左键移动'))  左键按下移动



# window.bind('<ButtonRelease-1>',lambda x:print('左键抬起'))


# window.bind('<Enter>',lambda x:print('鼠标移入'))
# window.bind('<Leave>',lambda x:print('鼠标移出'))


#滚轮事件
# window.bind('<Button-4>',lambda x:print('向上滚动'))
# window.bind('<Button-5>',lambda x:print('向下滚动'))


#键盘事件

e=tk.Entry(window)
e.pack()
# e.bind('<Key>',lambda x:print('键盘按下'))
# e.bind('<KeyRelease>',lambda x:print('键盘抬起'))


# e.bind('<Return>',lambda x:print('回车'))
# e.bind('<Up>',lambda x:print('上'))
# e.bind('<Down>',lambda x:print('下'))
# e.bind('<Right>',lambda x:print('左'))
# e.bind('<Left>',lambda x:print('右'))

# e.bind('<Shift_L>',lambda x:print('shift_l'))
# e.bind('<Shift_R>',lambda x:print('shift_r'))
# e.bind('<Control_L>',lambda x:print('control_r'))
# e.bind('<Shift_R>',lambda x:print('shift_r'))
# e.bind('<Alt_L>',lambda x:print('Alt_r'))
# e.bind('<A>',lambda x:print('A'))
# e.bind('<a>',lambda x:print('a'))
# e.bind('<Shift-R>',lambda x:print('Shift+r')) 键盘键合在一起用连字符
e.bind('<Shift-R>',lambda e:print(dir(e)))

#事件对象
# keykode  键盘码
# keysym   键盘符
# char     字符
# widget   事件源
# x
# y
# x_root
# y_root


import tkinter as tk 
window=tk.Tk()
window.geometry('600x400')
window.resizable(0,0)

def fn1(e):
    index=e.widget.curselection()
    # val=e.widget.get(index)
    print(index)

l1=tk.Listbox(window)
l1.pack()
for item in ['上海','北京','深圳','广州']:
    l1.insert('end',item)

l1.bind('<Dounle-Button-1>',fn1)  这里面单机事件传进来的下标有问题，不知道是为什么
window.mainloop()

```

### labelFrame    ：

```py
l1=tk.LabelFrame(window,text='我')
btn1=tk.Radiobutton(l1,text='a')
btn2=tk.Radiobutton(l1,text='s')
btn3=tk.Radiobutton(l1,text='d')
btn1.pack()
btn2.pack()
btn3.pack()

l1.pack()
window.mainloop()
```

