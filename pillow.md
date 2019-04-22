## pillow

Django的一种模块

cv2

Qt  c语言写界面   

安装：

```py
pip install pillow
```

数据结构：

```py
  顺序表，链表，二叉树
```

```py
Image.new('RGB',(100,100),color=(0,255,255))
兰与率为青       红与率为黄
imageDraw
```

```py
ImageFont? dizhi导入
class code:
	def __init__(self):
		self.codecon='a'
		self.codelen=4
		self.width
		self.height
		self.im=None
		self.lineNum=0
	def randBGcolor(self):
		return (random.randint(0,120),random.randint(0,120),random.randint(0,120))
	def randFGcolor(self):
		return (random.randint(0,120),random.randint(0,120),random.randint(0,120))
	def create(self):
		
	def lines(self):
		lineNum= self.lineNum or random.randint(5,10)
		draw=ImageDraw.Draw(self.im)
		for item in range(lineNum):
			place=(random.randint(0,self.width),random.randint(0,self.height),random.randint(0,self.width),random.randint(0,self.height))
			draw.lin(place,fill=self.randFGcolor(),width=random.randint(1,3))
	def points(self):
	def texts(self):
		
		
		
import  io 
bt=io.BytesIO
self..im.save(bt,'png')
return bt.getvalue()
self.str+=letter.lower()
	
codeobj=code()

```

