# 数据分析包

numpy ——基础库 python数据计算的核心库，提供了高性能的多维数组和处理数组的能力

Pandas——数据分析 基于Numpy创建的python库，为python提供了易于使用的数据结构和数据分析工具

Matplotlib——绘图 对于图像美化方面比较完善，方便的对数据进行可视化分析

Scipy

## Numpy    

- ndarray   多维数组   
- ufunc   

### 方法：

np.zeros,zp.ones(2,3,4)     第一个是几个数组，第二个是几行几列   初始化矩阵

#### np.linspace(1,3,3)  等差矩阵：

 开始指（start），结束值（end），num，默认50，endpoint=false，不包含最后一个

#### np.logspace(start,stop,num,endpoint,base(默认以10为底),dtype=None) 等比数列：

#### np.arange().reshape(2,-1)    从0开始，几个数       几行几列   -1为默认一行或者一列 用np.arange()生成数列,用np.arange().reshape()将数列转成矩阵

#### np.eye(2)  单位矩阵：

#### np.full((2,3),10)   两行三列，个数是记   常数矩阵：

#### a=np.array([2,4])     np.eye(2)*a    构成一个对角矩阵

#### np.empty(2,3)      随机数组    里面传两个参数，是二维，三个是三维  

#### np.random.random()

### 属性：

#### type   类型

#### a.ndim   数组的维度

#### a.shape(1,2)  形状   一行两列   后面可以赋值

#### a.ravel()   拉平，变称一维数组

#### size   元素个数

#### dtype   

#### astype

#### np.linalg.norm  范数？   可以求模长

#### a.itemsize     范数

#### np.linalg.inv()  求逆矩阵

#### np.linalg.det()  行列式的值

#### np.linalg.eig()  特征值

#### sigma=np.eye(2)*sigma

### 运算：

#### 简单运算：

##### 相加和相减或者乘除直接写就行  np.add(a,b) np.substract()  np.multiply() np.divide()

##### 幂运算  np.exp()     相当于np.e**2

##### 开方  np.sqrt()

##### 三角运算   np.sin()

##### np.where()  返回的是索引  ，第一个是行，第二个是列  b[np.where(b>7)]  可以得到元素

##### np.unique()  去重

##### np.dot()   矩阵相乘  或者  a.dot(b)

##### np.linalg.svd()

##### a.T   或者  np.transpose(a)  转置

##### np.linalg.eig

#### 聚合函数

##### np.sum()         对行求和    np.sum(a,axis=1)    axis=0  对列求和   轴

##### mean（）平均值

##### media（）中位数

##### np.cumsum()  累计求和，后面加前面

##### np.diff()   相邻元素相减

##### argmin（）矩阵最小值的位置

##### clip（矩阵，最小值，最大值）   小于最小值的都换成最小值，大于最大值的换成最大值，中间的不变

##### sort()   排序，本行排序   默认升序   axis 指定行排列还是列排列

#### 合并和分割数组：

##### np.concatenate((a,b))    行拼接  ，换轴用axis，默认为列

##### np.hsplit()   分割

##### np.vsplit()   分割

### 取值：

花式索引

a[[0,1,2],[0,2,3]]   前面的是行数，后面的是列数，从0开始

## Pandas   

series   一般都是一列，索引可以自己规定，

pd.set_option

```py
import pandas as pd
s =  pa.Series([1,2,3],index=['a','b','c'])  里面可以放列表（可以用numpy直接传值），标量，字典   index 可以指定索引名称 dtype指定类型   name  可以指定名字
属性
s.count     不包含确实值，就那个Nan，len(s)包含   缺失值可以用np.nan  来表示
s.value_counts   每个值的数量
s.unique
s.dropna()   删除缺失值
s.fillna()   填充缺失值
取值
取值，可以用写的索引，也可以用0，1，2
可以直接赋值
添加，默认在最后 s['d']=1
s.tail(2)
切片
中位数  median
运算
相加,索引对应位置相加，对应位置没有的话，会变成NaN，
s1.add(s2,fill_value=2) ,如果没有的话，用填充值来代替
```

DateFrame   表格型的数据类型，有多个Series组成

```py
pd.DateFrame([1,2,3])  列表数组字典   column 指定列索引  iloc位置   loc标签

```

中心极限定理   似然？     对数似然函数

```py
预测值-真实值   的平方 的和  加起来
缺失值    二分之一【theta0+theta1x1-y1】^   对theta0  和 theta1求偏导   theta0 = theta0-阿尔法乘以梯度
```

```py
读文件loadtxt()
标准化  x-miu/seigema        miu 平均值    seigema 方差
阿尔法 的选择       大，可能跳过最优解，小，可能运行效率慢
过拟合和正则项
弹性网络算法   岭回归 lass回归
```

```py
df=pd.read_csv()
df.head()
pd.get_dummies(df[[‘dist’,'floor']]).head()

X= df2.iloc[:,:-1]
del df1['dist_chaochaoyang']
reg.predict(np.array([]))
reg.score(X,y)

```

最小二乘法

```py
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from sklearn.linear_model import LinearRegression   这里的包是直接解决算法问题的，这个包里面用的是最小二乘法
reg = LinearRegression()
df = pd.read_csv('./house_price.csv')    pandas 读取csv文件，可以读取很多不同类型的文件
print(df)
df1 = pd.get_dummies(df[['dist','floor']])   独热编码 （one-hot） 我理解的就是把文字或者是没有规则的数据整理成有规则的数据，然后再进行处理
del df1['dist_chaoyang']   删除某一行
del df1['floor_high']
print(df1)
del df['dist']
del df['floor']
df2 = pd.concat((df1,df),axis=1) 合并，列方向
print(df2)
Y = df2['price']
del df2['price']
print(df2)
X = df2
reg.fit(X,Y)    将数据丢给这个包裹，进行算法分析，这里面用的是最小二乘法
print(reg.score(X,Y))    将数据进行剖析，以此来看看分析结果是否合理，一般到达60%就可以
```

梯度下降法

```py
import numpy as np
import matplotlib.pyplot as plt

data = np.loadtxt('data.txt')    numpy 读取文件
m,n = np.shape(data)  numpy 创造一个和data一样形状的矩阵
x = np.ones((m,n))   
x[:,0]=1       使x的第一列变为1
x[:,1]=data[:,0]
X = data[:,0]
# print(x) 
y = data[:,1]
theta = np.zeros(n)
times = 0
alpha = 0.001

while times < 1000000:
    # 程序里面dot方法默认会把需要转置后才能相乘的矩阵自动转换
    g = np.dot(x.T, (np.dot(x, theta)-y))   矩阵相乘
    theta_new = theta-g*alpha
    if (abs(theta-theta_new) < 0.00000001).all():
        break
    else:
        theta = theta_new
        times += 1

plt.scatter(X,y)
x1 = [min(X),max(X)]
y1 = [min(y),max(y)]
plt.plot(x1,y1,'r--')
plt.show()
# x[:,:-1]=data[:,:-1]
r = np.dot(np.dot(np.linalg.inv(np.dot(x.T,x)),x.T), y)   最小二乘法公式
print(r)


from sklearn.linear_model import LinearRegression   最小二乘法
reg = LinearRegression()
reg = reg.fit(data[:,0].reshape(-1,1),data[:,-1])
print(reg.coef_)    斜率
print(reg.intercept_) 截距



```

梯度下降法最基本的思想

```py
f1 = open('data.txt','r')
data = []
for item in f1:
    d = list(map(float,item.split('\t')))
    data.append(d)
row = []
column = []
for i in data:
    row.append(i[0])
    column.append(i[1])

M = len(data)
N = len(data[0])


# 预测值
def f(theta, x):
    y = 0
    for i in range(N - 1):
        y += theta[i] * x[i]
    y += theta[N - 1]
    return y
    # y = theta0+theta1*x1+theta1*x2+...+


# 梯度     （预测值-真实值）*当前的x   其实就是求导数
def grad(data, theta, j):
    g = 0
    for i in range(M):
        h = f(theta, data[i])
        if j != N - 1:
            g += (h - data[i][N - 1]) * data[i][j]
        else:
            g += (h - data[i][N - 1])
    return g


# 缺失值
def loss(data, theta):
    l = 0
    for i in range(M):
        h = f(theta, data[i])
        l += (h - data[i][N - 1]) ** 2
    return l / 2


theta = [0 for i in range(N)]
print(theta)
theta_new = [0 for i in range(N)]
g = [0 for i in range(N)]
times = 0
alpha = 0.001   #步长
print(g)
这里面最重要的思想是迭代，现在的点与上一个点之间的方向角度差距越来越小，那就说明已经到达了最低点
while times < 1000000:
    flag = 0
    for j in range(N):
        g = grad(data, theta, j)
        theta_new[j] = theta[j] - alpha * g    公式  theta1 = theta0-阿尔法乘以梯度 
        # print('l,theta,times:\t',loss(data,theta),theta,times)
        if abs(theta_new[j] - theta[j]) < 0.000001:
            flag = 1
            break
        else:
            theta[j] = theta_new[j]
            times += 1
    if flag:
        break

print(times)
print(g)
print(theta)
求出来theta，即知道了斜率和截距，就可以画出这条回归线

```

随机梯度下降，SDG

```
sklearn.linear_model import LinearRegression
使用方法
实例化
sklearn一直秉承着简洁为美得思想设计着估计器，实例化的方式很简单，使用clf = LinearRegression()就可以完成，但是仍然推荐看一下几个可能会用到的参数：

fit_intercept：是否存在截距，默认存在
normalize：标准化开关，默认关闭
还有一些参数感觉不是太有用，就不再说明了，可以去官网文档中查看。

回归
其实在上面的例子中已经使用了fit进行回归计算了，使用的方法也是相当的简单。

fit(X,y,sample_weight=None)：X,y以矩阵的方式传入，而sample_weight则是每条测试数据的权重，同样以array格式传入。
predict(X)：预测方法，将返回预测值y_pred
score(X,y,sample_weight=None)：评分函数，将返回一个小于1的得分，可能会小于0
方程
LinearRegression将方程分为两个部分存放，coef_存放回归系数，intercept_则存放截距，因此要查看方程，就是查看这两个变量的取值。
```
逻辑回归——分类

logistic  函数/sigmoid 函数

```py
import 
```

优缺点

```py
优点：
	1.形式简单，模型的可解释性强
	2.训练速度较快
	3.资源暂用内存小
	4.模型效果不错
	5.输出所属类别概率

缺点：
	1.准确率不是很高
	2.很难处理数据不平衡的问题
	3.本身无法筛选特征   
		有时候GBDT筛选特征，结合逻辑回归
```

## 朴素贝叶斯分类算法：

先验概率，根据主观意识判断

后验概率，经验

平滑技术 拉普拉斯平滑，也叫加1平滑，分子上加1，对应分母，有几类加几

取对数处理，为了防止数值下溢，因为太小，导致计算机没法识别，所以用对数来表示

吃鸡        出现没有    词但    出现几次

NB与LR的异同：

LR：Loss最优化

多一个朴素的假设

scikit-learn.org  几种算法

朴素，贝叶斯，先验概率估计后验概率

### 文本相似度算法：

欧几里得距离   dist(x,y) = (xi-yi)的绝对值 的平方的开放然后加起来

余弦相似度     cos = a的转置乘以b 的积再除以（a的模与b的模的积）

皮尔逊相关系数        多基于用户做推荐

作用域推荐    内容推荐，协同过滤推荐（基于用户，基于物品）

基于物品    sim（i，j）*r（u，j）/sim（j，i）

sim（u，v）*（）

### HOG特征提取：

方向梯度直方图

1.预处理   以灰度形式读取图片，并归一化（划到0-1之间）

2.计算梯度图像

- 计算每个像素点的梯度值（sobel算子）
- 计算水平和垂直方向的梯度赋值和梯度方向
- 方法：
  - 可下面的两个kernel来计算
  - 直接用opencv里面的kernel大小为1的

3.计算8*8网格的梯度    

- 每个cell有9个bin   像素点
- 初始化cell的梯度向量，求出每一个cell的梯度峰值和方向（把单一看成一个整体）

4.16乘以16快归一化（4个9乘以1的直方图组成了一个36*1的向量）  标准化处理

5.计算hog特征向量

- 8列，16行，    移动7乘以15次,每一次是36乘以1的向量，总共是 36乘以105次

6.可视化hog特征

opencv     卷积核？   滤波器？ 傅里叶变化

tan（theta）角度    g = （x的平方+y的平方）开根号   梯度峰值

### 凸优化问题：

求取最小值

两到大于0   凸函数

小于0  凹函数

拉格朗日函数    L（x，阿尔法） = f（x）+阿尔法h（x）

KKT 条件  

- L（x，阿尔法，被他）分别对x求导为0
- 被他g（x）=0
- g（x）<=0
- 被他>0,阿尔法 不等于0
- h(x) = 0

不等式约束优化问题    L(X,阿尔法，被他)= f（x）+阿尔法h（x）+βg（x）    g（x）<=0  h(x)=0

### 支持向量机  简称svm

分类的一种算法，分割的原则是间隔最大化，最终转换为一个凸二次规划问题来求解

线性，对偶

