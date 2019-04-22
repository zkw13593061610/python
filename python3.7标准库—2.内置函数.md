# 2.内置函数

Python解释器内置了许多函数和类型，这些函数和类型总是可用的。它们按字母顺序排列在这里。

|                                  | Built-in Functions               |                               |                                    |                                   |
| -------------------------------- | -------------------------------- | ----------------------------- | ---------------------------------- | --------------------------------- |
| [`abs()`](#abs)                  | [`delattr()`](#delattr)          | [`hash()`](#hash)             | [`memoryview()`](#func-memoryview) | [`set()`](#func-set)              |
| [`all()`](#all)                  | [`dict()`](#func-dict)           | [`help()`](#help)             | [`min()`](#min)                    | [`setattr()`](#setattr)           |
| [`any()`](#any)                  | [`dir()`](#dir)                  | [`hex()`](#hex)               | [`next()`](#next)                  | [`slice()`](#slice)               |
| [`ascii()`](#ascii)              | [`divmod()`](#divmod)            | [`id()`](#id)                 | [`object()`](#object)              | [`sorted()`](#sorted)             |
| [`bin()`](#bin)                  | [`enumerate()`](#enumerate)      | [`input()`](#input)           | [`oct()`](#oct)                    | [`staticmethod()`](#staticmethod) |
| [`bool()`](#bool)                | [`eval()`](#eval)                | [`int()`](#int)               | [`open()`](#open)                  | [`str()`](#func-str)              |
| [`breakpoint()`](#breakpoint)    | [`exec()`](#exec)                | [`isinstance()`](#isinstance) | [`ord()`](#ord)                    | [`sum()`](#sum)                   |
| [`bytearray()`](#func-bytearray) | [`filter()`](#filter)            | [`issubclass()`](#issubclass) | [`pow()`](#pow)                    | [`super()`](#super)               |
| [`bytes()`](#func-bytes)         | [`float()`](#float)              | [`iter()`](#iter)             | [`print()`](#print)                | [`tuple()`](#func-tuple)          |
| [`callable()`](#callable)        | [`format()`](#format)            | [`len()`](#len)               | [`property()`](#property)          | [`type()`](#type)                 |
| [`chr()`](#chr)                  | [`frozenset()`](#func-frozenset) | [`list()`](#func-list)        | [`range()`](#func-range)           | [`vars()`](#vars)                 |
| [`classmethod()`](#classmethod)  | [`getattr()`](#getattr)          | [`locals()`](#locals)         | [`repr()`](#repr)                  | [`zip()`](#zip)                   |
| [`compile()`](#compile)          | [`globals()`](#globals)          | [`map()`](#map)               | [`reversed()`](#reversed)          | [`__import__()`](#__import__)     |
| [`complex()`](#complex)          | [`hasattr()`](#hasattr)          | [`max()`](#max)               | [`round()`](#round)                |                                   |

==**abs**(*x*)==

​    返回数字的绝对值。参数可以是整数，也可以是浮点数。如果参数是复数，则返回其大小。

==**all**(*iterable*)==

​    如果*iterable*的所有元素都是`True`(或者如果可迭代对象是空的)，则返回True。相当于：

```python
def all(iterable):
    for element in iterable:
        if not element:
            return False
    return True
```

==**any**(*iterable*)==

​	如果可迭代的任何元素为true，则返回`True`。如果可迭代为空，则返回`False`。相当于：

```python
def any(iterable):
    for element in iterable:
        if element:
            return True
    return False
```

==**ascii**(*object*)==

​    作为`repr()`，返回包含对象可打印表示的字符串，但使用`\x`、`\u`或`\U`转义来转义`repr()`返回的字符串中的非ASCII字符。这将生成一个类似于Python 2中`repr()`返回的字符串。

==**bin**(*x*)==

​    将整数转换为以“0b”为前缀的二进制字符串。结果是一个有效的Python表达式。如果*x*不是Python `int`对象，则必须定义返回整数的`__index__()`方法。一些例子：

```python
>>> bin(3)
'0b11'
>>> bin(-10)
'-0b1010'
```

​    如果前缀“0b”是否需要，则可以使用以下任何一种方式。

```python
>>> format(14, '#b'), format(14, 'b')
('0b1110', '1110')
>>> f'{14:#b}', f'{14:b}'
('0b1110', '1110')
```

​    有关更多信息，请参见`format()`。

==*class* **bool**([*x*])==

​    返回一个布尔值，即`True`值或`False`值。*x*使用标准的`truth testing procedure`进行转换。如果*x*为false或省略，则返回False；否则返回True。`bool`类是`int`的子类(请参见数字类型-int、float、complex)。它不能再被子类化了。它的唯一实例是`False`和`True`(参见布尔值)。

==**breakpoint**(*\*args*, *\*\*kws*)==

​    此函数会将您放到调用站点的调试器中。具体来说，它调用`sys.interpointhook()`，直接传递`args`和`kws`。默认情况下，`sys.interpointhook()`调用`pdb.set_trace()`，不需要任何参数。在本例中，它纯粹是一个方便的函数，因此您不必显式导入`pdb`或键入足够多的代码才能进入调试器。但是，`sys.interpointhook()`可以设置为其他函数，而且`breakpoint()`将自动调用它，从而允许您进入所选择的调试器。

`版本3.7新增。`

==*class* **bytearray**([*source*[,*encoding*[,*errors*]]])==

​    返回一个新的二进制数组。`bytearray`类是0<=x<256范围内的可变整数序列。它有大多数常见的可变序列方法(在`可变序列类型`中描述)，以及`bytes`类型所具有的大多数方法，参见`Bytes和ByteArray操作`。

​    可选*source*参数可用于以几种不同的方式初始化数组：

* 如果是字符串，则还必须提供编码参数(以及可选的错误)参数；`bytearray()`然后使用`str.encode()`将字符串转换为字节。
* 如果它是一个整数，数组将具有这个大小，并将被初始化为空字节。
* 如果它是一个符合缓冲区接口的对象，则对象的只读缓冲区将用于初始化字节数组。
* 如果它是可迭代的，则必须是`0 <= x < 256`范围内的整数可迭代，这些整数用作数组的初始内容。

​    如果没有参数，则创建大小为0的数组。

还请参见二进制序列类型-字节、字节数组、内存视图和ByteArray对象。

==*class* **bytes**([*source*[,*encoding*[,*errors*]]])==

​    返回一个新的“bytes”对象，它是`0 <= x < 256`范围内不可变的整数序列。`bytes`是字节数组的不可变版本—它具有相同的非变异方法和相同的索引和切片行为。

​    因此，构造函数参数被解释为`bytearray()`。

​    Bytes对象也可以使用文字创建，请参见`字符串和字节文本`。

​    还请参见二进制序列类型-`字节`、`字节数组`、`内存视图`、`Bytes对象`以及`Bytes和Bytearray操作`。

==**callable**(*object*)==

​    如果对象参数显示为可调用，则返回`True`，否则返回`False`。如果返回True，仍然有可能调用失败，但如果调用为False，则调用对象将永远不会成功。注意，类是可调用的(调用类返回一个新实例)；如果类具有`__call__()`方法，则实例是可调用的。

   *版本3.2新增*：这个函数首先在Python3.0中被删除，然后在Python3.2中被带回来。 

==**chr**(*i*)==

​    返回表示Unicode代码点为整数*i*的字符串。例如，`chr(97)`返回字符串`'a'`，而chr(8364)返回字符串`'€'`。这是`ord()`的反义词。

​    参数的有效范围为0到1,114,111(基数16为0x10FFFF)。如果我超出了这个范围，`ValueError`就会被触发。

==@**classmethod**==

​    将方法转换为类方法。

​    类方法作为隐式第一个参数接收类，就像实例方法接收实例一样。要声明类方法，请使用以下术语：

```python
class C:
    @classmethod
    def f(cls, arg1, arg2, ...): ...
```

​    `@classmethod`表单是一个函数修饰器-有关详细信息，请参阅函数定义中对函数定义的描述。

​    它可以在类(如`C.F()`上调用，也可以在实例(例如`C().f()`上调用。除了它的类之外，实例将被忽略。如果为派生类调用类方法，派生类对象将作为隐含的第一个参数传递。

​    类方法与C++或Java静态方法不同。如果需要，请参阅本节中的`staticmethod()`。

​    有关类方法的详细信息，请参阅`标准类型层次结构`中的标准类型层次结构的文档。

==**compile**(*source*, *filename*, *mode*, *flags=0*, *dont_inherit=False*, *optimize=-1*)==

​    将*source*编译为代码或AST对象。

​    代码对象可以由`exec()`或`eval()`执行。*source*可以是普通字符串、字节字符串或AST对象。有关如何使用AST对象的信息，请参阅`ast`模块文档。

​    *filename*参数应该给出读取代码的文件；如果不是从文件中读取的，则传递一些可识别的值(`'<string>'`是常用的)。

​    *mode*参数指定必须编译哪种代码；如果`source`由一系列语句组成，则*mode*可以是`'exec'`；如果它由单个表达式组成，则为`'eval'`；如果它由单个交互式语句组成，则为`'single'`(在后一种情况下，将打印计算结果为`None`的表达式语句)。

​    可选参数*flags*和*dont_inherit*是用来控制编译源码时的标志，(可以查看PEP236文档来了解这些参数)，以及相关编译的说明。如果两者使用缺省参数（也即两者都是零值），在调用本函数编译时，主要使用代码中指明的编译特征来对待；如果flags参数设置有值，而dont_inherit没有设置（即是零值），那么编译代码时，不仅源码的编译特征起作用，而且flags指明的特征也起作用，相当两者的并集；如果参数dont_inherit设置有值（即是非零值），编译语句时只有参数flags指明的编译特征值起作用，即是不使用源码里指明的特征。

​    future语句是由位指定的，这些位可以一起按位来指定多个语句。指定给定功能所需的位字段可以在`__future__`模块中的`_Feature`实例上找到`compiler_flag`属性。

​    参数*optimize*指定编译器的优化级别；默认值-1选择解释器的优化级别(由-O选项提供)。显式级别为0(无优化；`__debug__`为真)、1(移除断言、`__debug__`为false)或2(docstring也被删除)。

​    如果编译的源代码无效，则此函数将触发`SyntaxError`，如果source包含空字节，则触发`ValueError`。

​    如果要将Python代码解析为AST表示，请参见`ast.parse()`。

> **注：在“`single`”或“`eval`”模式下使用多行代码编译字符串时，输入必须以至少一个换行符结束。这是为了便于在`code`模块中检测不完整和完整的语句**

> **⚠️警告：由于Python的AST编译器中的堆栈深度限制，编译到AST对象时可能会使用足够大/复杂的字符串使Python解释器崩溃。**

​    在3.2版本中更新：允许使用Windows和Mac换行符。此外，在‘exec’模式下输入不再需要以换行符结尾。添加了*optimize*参数。

​    在3.5版本中更新：以前，当*source*中遇到空字节时，就会触发`TypeError`。

==class **complex([*real*[, *imag*]])**==

​    返回一个值为*real* + *image*\*1j的复数，或者将一个字符串或数字转换为复数。如果第一个参数是字符串，它将被解释为一个复数，函数必须在没有第二个参数的情况下调用。第二个参数永远不可能是字符串。每个参数都可以是任何数字类型(包括复杂类型)。如果省略了*imag*，则默认为零，构造函数充当像`int`和`float`这样的数字转换。如果省略了这两个参数，则返回`0j`。

> **⚠️注意：当从字符串转换时，字符串不能包含中央+或-运算符周围的空格。例如，`complex(“1+2j”)`可以，但是`complex(“1  +  2j”)`会产生ValueError。**

​    复数类型在`数字类型`中描述—— `int`、`float`、`complex`

*版本3.6变更*:允许按代码文字中的下划线分组数字。

==**delattr**(*object*, *name*)==

这和`setattr()`关系密切。参数是一个对象和一个字符串。字符串必须是对象的一个属性的名称。如果对象允许，该函数将删除指定的属性。例如，`delattr(x， 'foobar')`等价于`del x.foobar`。

==*class* **dict**(***kwarg*)==

==*class* **dict**(*mapping*, ***kwarg*)==

==*class* **dict**(*iterable*, ***kwarg*)==

​    创建一个新字典。`dict`对象是`dictionary`类。有关该类的文档，请参阅`dict`和`Mapping Types - dict`。

对于其他容器，请参见内置的`list`、`set`和`tuple`类，以及`collections`模块。

==**dir**([*object*])==

​    如果没有参数，则返回当前局部作用域中的名称列表。使用参数，尝试返回该对象的有效属性列表。

​    如果对象有一个名为`__dir__()`的方法，将调用该方法，并且必须返回属性列表。这允许实现自定义`__getattr__()`或`__getattribute__()`函数的对象自定义`dir()`报告其属性的方式。

​    如果对象不提供`__dir__()`，则函数将尽力从对象的`__dict__`属性(如果定义)和它的类对象中收集信息。结果列表不一定是完整的，而且当对象具有自定义`__getattr__()`时可能是不准确的。

​    默认的`dir()`机制对不同类型的对象的行为不同，因为它试图生成最相关的信息，而不是完整的信息:

* 如果对象是模块对象，则列表包含模块属性的名称。
* 如果对象是类型或类对象，则列表包含其属性的名称，并递归地包含其基的属性。
* 否则，该列表将包含对象的属性名、其类的属性名以及其类的基类的属性的递归名称。

​    结果列表是按字母顺序排序的。例如:

```python
>>> import struct
>>> dir()   # show the names in the module namespace  
['__builtins__', '__name__', 'struct']
>>> dir(struct)   # show the names in the struct module 
['Struct', '__all__', '__builtins__', '__cached__', '__doc__', '__file__',
 '__initializing__', '__loader__', '__name__', '__package__',
 '_clearcache', 'calcsize', 'error', 'pack', 'pack_into',
 'unpack', 'unpack_from']
>>> class Shape:
...     def __dir__(self):
...         return ['area', 'perimeter', 'location']
>>> s = Shape()
>>> dir(s)
['area', 'location', 'perimeter']
```

> **⚠️注意：因为`dir()`主要是为了方便在交互式提示符下使用而提供的，所以它试图提供一组有趣的名称，而不是严格地或一致地定义一组名称，而且它的详细行为可能在不同版本之间发生变化。例如，当参数是类对象时，元类属性不在结果列表中。**

==**divmod**(*a*, *b*)==

​    以两个(非复数)数字作为参数，在使用整数除法时，返回一对由它们的商和余数组成的数字。对于混合操作数类型，适用二进制算术运算符的规则。对于整数，结果与`(a // b, a % b)`相同，对于浮点数，结果是`(q, a % b)`，其中*q*通常是`math.floor(a / b)`，但可能比这低1层。在任何情况下，`q * b + a % b`非常接近a，如果`a % b`不为0，它与b有相同的符号，`0 <= abs(a % b) < abs(b)`。

==**enumerate**(*iterable*, *start=0*)==

​    返回一个枚举对象，*iterable*必须是一个序列,`iterator`必须是序列、迭代器或其他支持迭代的对象。`enumerate()`返回的迭代器的`__next__()`方法返回一个元组，其中包含一个计数(从*start*默认值为0)和在*iterable*上迭代获得的值。

```python
>>> seasons = ['Spring', 'Summer', 'Fall', 'Winter']
>>> list(enumerate(seasons))
[(0, 'Spring'), (1, 'Summer'), (2, 'Fall'), (3, 'Winter')]
>>> list(enumerate(seasons, start=1))
[(1, 'Spring'), (2, 'Summer'), (3, 'Fall'), (4, 'Winter')]
```

​    等价于

```python
def enumerate(sequence, start=0):
    n = start
    for elem in sequence:
        yield n, elem
        n += 1
```

==**eval**(*exception, globals=None, locals=None*)==

​    参数是字符串、可选*globals*和*locals*。如果提供*globals*，该参数必须是字典。如果提供*locals*，该参数是任何映射对象。

​    使用*globals*和*locals*字典作为全局和本地名称空间，将`exception`参数解析并作为Python表达式(技术上称为条件列表)计算。如果globals字典存在且缺少“\__builtins__”，则在解析*exception*之前将当前的全局名称空间字典复制到*globals*中。这意味着*exception*通常可以完全访问标准`builtins`模块，并传播受限制的环境。如果省略了*locals*字典，则默认为`globals`字典。如果省略这两个字典，表达式将在调用`eval()`的环境中执行。返回值是求值表达式的结果。语法错误被报告为异常。例子:

```python
>>> x = 1
>>> eval('x+1')
2
```

​    这个函数还可以用来执行任意的代码对象(例如由`compile()`创建的代码对象)。在这种情况下，传递代码对象而不是字符串。如果以`'exec'`作为*mode*参数编译了代码对象，`eval()`的返回值将为`None`。

​    提示:`exec()`函数支持语句的动态执行。`globals()`和`local()`函数分别返回当前的全局字典和本地字典，传递给`eval()`或`exec()`使用可能很有用。

​    可以使用只包含文字的表达式安全地计算字符串的函数，请参见`ast.literal_eval()`。

==**exec**(*object*[, *globals*[, *locals*]])==

​    该函数支持Python代码的动态执行。*object*必须是字符串或代码对象。如果是字符串，则将字符串解析为一组Python语句，然后执行这些语句(除非出现语法错误)[1]。如果它是一个代码对象，它将被简单地执行。在所有情况下，执行的代码都应该作为文件输入有效(请参阅参考手册中的“文件输入”一节)。请注意，`return`和`yield`语句不能在函数定义之外使用，甚至不能在传递给`exec()`函数的代码上下文中使用。返回值为`None`。

​    在所有情况下，如果省略了可选部分，代码将在当前作用域内执行。如果只提供*globals*变量，那么它必须是一个字典，它将用于全局变量和局部变量。如果给定*globals*变量和*locals*变量，则分别将它们用于全局变量和局部变量。如果提供，locals变量可以是任何映射对象。请记住，在模块级别上，全局变量和局部变量是相同的字典。如果`exec`得到两个单独的对象，作为`globals`对象和`locals`对象，那么代码将被执行，就像它被嵌入到类定义中一样。

​    如果*globals*字典不包含键`__builtins__`的值，则在该键下插入对内置模块`builtins`字典的引用。通过这种方式，您可以在将自己的*globals*字典传递给`exec()`之前，将\__builtins__字典插入*globals*变量中，从而控制执行代码可以使用哪些内建函数。

> ⚠️**注意：内置函数`globals()`和`local()`分别返回当前的全局字典和本地字典，传递它们作为`exec()`的第二个和第三个参数可能很有用。**

> ⚠️**注意：默认*locals*变量的作用如下面的函数`locals()`所述:不应该尝试修改默认*locals*字典。如果需要在函数exec()返回后查看代码对*locals*的影响，请传递显式*locals*字典。**

==**filter**(*function*, *iterable*)==

​    从那些*function*返回*true*的*iterable*元素构造迭代器。*iterable*可以是序列、支持迭代的容器或迭代器。如果*function*为`None`，则假定恒等函数，即所有*iterable*为`False`的元素都被删除。

​    注意：如果*function*不是`None`，那么`filter(function, iterable)`等价于生成器表达式`(item for item in iterable if function(item))`，如果*function*是`None`等价于`(item for item in iterable if item)`。

​    有关返回iterable元素的互补函数(即`function`返回False的元素)，请参见`itertools.filterfalse()`。

==class **float**([*x*])==

​    返回由数字或字符串*x*构造的浮点数。

​    如果参数是一个字符串，它应该包含一个十进制数，前面可以加上一个符号，也可以嵌入空格。可选的符号可以是“+”或“-”;“+”符号对生成的值没有影响。参数也可以是表示NaN(not-a-number)或正无穷大或负无穷大的字符串。更准确地说，在去掉前导和尾随空格字符后，输入必须符合以下语法:

```python
sign           ::=  "+" | "-"
infinity       ::=  "Infinity" | "inf"
nan            ::=  "nan"
numeric_value  ::=  floatnumber | infinity | nan
numeric_string ::=  [sign] numeric_value
```

​    这里，`floatnumber`是Python浮点文字的一种形式，用浮点文字描述。大小写不重要，因此，例如“inf”,“Inf”,“INFINITY”和“iNfINity”都是正无穷可以接受的拼写。

​    另一方面，如果参数是整数或浮点数，则返回具有相同值的浮点数(在Python的浮点精度范围内)。如果参数超出Python浮点数的范围，将引发`OverflowError`。

​    对于一般Python对象`x`, `float(x)`委托给`x.__float__()`。

​    如果没有给出参数，则返回`0.0`。

​    例子：

```python
>>> float('+1.23')
1.23
>>> float('   -12345\n')
-12345.0
>>> float('1e-003')
0.001
>>> float('+1E6')
1000000.0
>>> float('-Infinity')
-inf
```

​    浮动类型在`Numeric Types—int、float、complex`中描述。

​    版本3.6中的更改:允许按代码文字中的下划线分组数字。

==**format**(*value*[, *format_spec*])==

​    将*value*转换为由*format_spec*控制的“格式化”表示。*format_spec*的解释取决于*value*参数的类型，但是大多数内置类型都使用标准格式语法:Format Specification Mini-Language。

​    默认的*format_spec*是一个空字符串，通常与调用`str(value)`的效果相同。

​    对`format(value, format_spec)`的调用被转换为`type(value).__format__(value, format_spec)`，它在搜索*value*的`__format__()`方法时绕过实例字典。如果方法搜索到达`object`且`format_spec`不是空的，或者`format_spec`和返回值都不是字符串，则会引发`TypeError`异常。

​    在3.4版本中更改:如果format_spec不是空字符串，`object().__format__(format_spec)`会引发`TypeError`。

==class **frozenset**([*iterable*])==

​    返回一个新的`frozenset`对象，可以从可选参数*iterable*获取元素。`frozenset`是一个内置类。有关该类的文档，请参见`frozenset`和`Set Type——set, frozenset`。

​    对于其他容器，请参阅内置的`set`，`list`，`tuple`和`dict`类以及`collections`模块。

==**getattr**(*object*, *name*[, *default*])==

​    返回对象的名称属性的值。名称必须是字符串。如果字符串是对象的一个属性的名称，那么结果就是该属性的值。例如，`getattr(x， 'foobar')`等价于`x.foobar`。如果指定的属性不存在，则提供*default*，否则会引发`AttributeError`。

==**globals**()==

​    返回表示当前全局符号表的字典。这始终是当前模块的字典(在函数或方法中，这是定义它的模块，而不是调用它的模块)。

==**hasattr**(*object*, *name*)==

​    参数是一个对象和一个字符串。如果字符串是对象属性之一的名称，则结果为`True`;如果不是，则为`False`。(这是通过调用`getattr(object, name)`并查看它是否引发`AttributeError`来实现的。)

==**hash**(*object*)==

​    返回对象的哈希值(如果它有)。哈希值是整数。它们用于在字典查找期间快速比较字典键。比较相等的数值具有相同的散列值(即使它们是不同类型的，例如1和1.0)。

> ⚠️**注意：对于使用自定义`__hash__()`方法的对象，请注意`hash()`根据主机的位宽截断返回值。有关详细信息，请参见`__hash__()`。**

==**help**([*object*])==

​    调用内置的帮助系统。(此功能用于交互式使用。)如果没有给出参数，交互式帮助系统将在解释器控制台启动。如果参数是字符串，那么该字符串将作为模块名、函数名、类名、方法名、关键字名或文档主题名查找，帮助页面将打印在控制台上。如果参数是任何其他类型的对象，将生成该对象上的帮助页。 

​    这个函数由`site`模块添加到内置的名称空间。

​    版本3.4中的更改:对`pydoc`和`inspect`的更改意味着报告的可调用签名现在更加全面和一致。

==**hex**(*x*)==

​    将整数转换为以“0x”为前缀的小写十六进制字符串。如果*x*不是Python `int`对象，它必须定义一个`__index__()`方法，该方法返回一个整数。一些例子:

```python
>>> hex(255)
'0xff'
>>> hex(-42)
'-0x2a'
```

​    如果您想将一个整数转换为大写或小写的十六进制字符串并加上前缀，您可以使用以下两种方法之一:

```python
>>> '%#x' % 255, '%x' % 255, '%X' % 255
('0xff', 'ff', 'FF')
>>> format(255, '#x'), format(255, 'x'), format(255, 'X')
('0xff', 'ff', 'FF')
>>> f'{255:#x}', f'{255:x}', f'{255:X}'
('0xff', 'ff', 'FF')
```

​    有关更多信息，请参见`format()`。

​    还请参见`int()`，以16为基数将十六进制字符串转换为整数。

​    注意:要获得浮点数的十六进制字符串表示，请使用`float.hex()`方法。

==**id**(*object*)==

​    返回对象的“标识”。这是一个整数，保证该对象在其生命周期内是惟一和常量。具有非重叠生存期的两个对象可能具有相同的`id()`值。

​    **CPython实现细节**：这是内存中对象的地址。

==**input**([*prompt*])==

​    如果*prompt*参数存在，则将其写入标准输出，而不带结尾换行符。然后，该函数从输入读取一行，将其转换为字符串(去掉后面的换行符)，并返回该字符串。读取`EOF`时，会引发`EOFError`。例子:

```python
>>> s = input('--> ')  
--> Monty Python's Flying Circus
>>> s  
"Monty Python's Flying Circus"
```

​    如果加载了`readline`模块，则input()将使用它提供详细的行编辑和历史特性。

==class **int**(*x=0*)==

==class **int**(*x*, *base=10*)==

​    返回由数字或字符串x构造的整数对象，如果没有参数，则返回0。如果*x*定义了`__int__()`,int(x)返回`x.__int__()`。如果*x*定义了`__trunc__()`，它返回`x.__trunc__()`。对于浮点数，它截断为0。

​    如果*x*不是一个数字，或者给定了*base*，那么*x*必须是一个字符串、`bytes`或`bytearray`实例，它以*base*表示`整数文本`。可选地，文字前面可以加上+或-(中间没有空格)，并被空格包围。base-n文字由数字0到n-1组成，a到z(或A到Z)的值为10到35。默认*base*是10。允许的值是0和2-36。Base-2、-8和-16文字可以选择以0b/ 0B、0o/ 0O或0x/ 0X作为前缀，就像在代码中使用整数文字一样。Base 0的意思是准确地解释为一个代码字面，因此实际的基数是2,8,10或16，因此int('010'， 0)是不合法的，而int('010')是合法的，以及int('010'， 8)。

​    整数类型在数字类型——int、float、complex中描述。

​    3.4 版本更新：如果*base*不是int的实例，并且*base*对象有一个`base.__index__`方法，该方法被调用以获取*base*的整数。以前的版本使用`base.__int__`而不是`base.__index__`。

​    3.6 版本更新：允许按代码文字中的下划线分组数字。

==**isinstance**(*object*, *classinfo*)==

​    如果*object*参数是*classinfo*参数的实例，或者是它的子类(直接、间接或虚拟)的实例，则返回true。如果对象不是给定类型的对象，函数总是返回false。如果*classinfo*是type对象的元组(或者递归地，其他类型的元组)，如果对象是任何类型的实例，则返回true。如果*classinfo*不是一个类或者类的元组和类似的元组，那么就会引发`TypeError`异常。

==**issubclass**(*class*, *classinfo*)==

​    如果*class*是*classinfo*的子类(直接、间接或虚拟)，则返回true。类被认为是它自己的子类。*classinfo*可能是类对象的一个元组，在这种情况下，*classinfo*中的每个条目都将被检查。在任何其他情况下，都会引发`TypeError`异常。

==**iter**(*object*[, *sentinel*])==

​    返回`迭代器`对象。根据第二个参数的存在，第一个参数的解释非常不同。如果没有第二个参数，object必须是支持迭代协议(`__iter__()`方法)的集合对象，或者必须支持序列协议(`__getitem__()`方法，该方法的整型参数从`0`开始)，如果不支持这两个协议，则会引发`TypeError`。如果给出第二个参数*sentinel*，则*object*必须是可调用对象。在这种情况下创建的迭代器将调用`object`，对其`__next__()`方法的每次调用都不带参数;如果返回的值等于*sentinel*，则将引发*StopIteration*，否则将返回该值。

​    还请参见`迭代器类型`。

​    iter()的第二种形式的一个有用的应用是读取文件的行，直到达到某一行。下面的例子读取一个文件，直到readline()方法返回一个空字符串:

```python
with open('mydata.txt') as fp:
    for line in iter(fp.readline, ''):
        process_line(line)
```

==**len**(*s*)==

​    返回对象的长度(项数)。参数可以是序列(如字符串、字节、元组、列表或范围)，也可以是集合(如字典、集合或冻结集合)。

==class **list**([*iterable*])==

​    `list`并不是一个函数，它实际上是一个可变的序列类型，如列表和序列类型——list、tuple、range中所述。

==**locals**()==

​    更新并返回表示当前本地符号表的字典。在函数块中调用它时，`locals()`会返回局部变量，但在类块中不会。

> ⚠️**注意：本词典的内容不能修改;更改可能不会影响解释器使用的本地变量和自由变量的值。**

==**map**(*function*, *iterable*, …)==

​    返回一个迭代器，该迭代器将*function*应用于可迭代的每一项，生成结果。如果传递了额外的*iterable*参数，则*function*必须接受那么多参数，并并行地应用于所有可迭代项。对于多个迭代器，当最短的迭代器耗尽时迭代器停止。对于已经将函数输入安排为参数元组的情况，请参见`itertools.starmap()`。

==**max**(*iterable*[, *key*[, *default*])==

==**max**(*arg1*, *arg2*, **args*[, *key*])==

​    返回*iterable*中的最大项，或两个或多个参数中的最大项。

​    如果提供了一个位置参数，它应该是`iterable`。返回`iterable`中最大的项。如果提供了两个或更多的位置参数，则返回最大的位置参数。

​    有两个可选的关键字参数。*key*参数指定一个单参数排序函数，就像`list.sort()`所使用的那样。如果提供的可迭代对象为空(空可迭代对象)，则*default*参数指定要返回的对象。如果迭代器为空且未提供`default`，则会引发`ValueError`。

​    如果多个项目是最大的，函数返回遇到的第一个项目。这与其他保持排序稳定性的工具(如`sorted(iterable, key=keyfunc, reverse=True)[0]`和`heapq.nlargest(1, iterable, key=keyfunc)`一致。

==**memoryview**(*obj*)==

​    返回从给定参数创建的“内存视图”对象。有关更多信息，请参见`内存视图`。

==**min**(*iterable*, *[, *key*, [, *default*]])==

==**min**(*arg1*, *arg2*, **args*[, *key*])==

​    返回*iterable*中的最小项，或两个或多个参数中的最小项。

​    如果提供了一个位置参数，它应该是`iterable`。返回迭代器中最小的项。如果提供了两个或多个位置参数，则返回最小的位置参数。

​    有两个可选的关键字参数。*key*参数指定一个单参数排序函数，就像`list.sort()`所使用的那样。如果提供的可迭代对象为空，则*default*参数指定要返回的对象。如果迭代器为空且未提供*default*，则会引发`ValueError`。

​    如果多个条目最少，函数将返回遇到的第一个条目。这与其他保持排序稳定性的工具(如`sorted(iterable, key=keyfunc)[0]`和`heapq.nsmallest(1, iterable, key=keyfunc)`)。

​    3.4版本新增:*default*为关键字参数。

==**next**(*iterator*[, *default*])==

​    通过调用迭代器的`__next__()`方法从迭代器检索下一个项目。如果给定*default*，则迭代器耗尽时返回默认值，否则将引发`StopIteration`。

==class **object**==

​    返回一个新的无特征的对象。`object`是所有类的基。它的方法对于Python类的所有实例都是通用的。这个函数不接受任何参数。

> ⚠️**注意：`object`没有`__dict__`，因此不能将任意属性分配给`object`类的实例。**

==**oct**(*x*)==

​    将整数转换为以“0o”为前缀的八进制字符串。结果是一个有效的Python表达式。如果*x*不是Python `int`对象，它必须定义一个`__index__()`方法，该方法返回一个整数。例如:

```python
>>> oct(8)
'0o10'
>>> oct(-56)
'-0o70'
```

​    如果您希望将整数转换为八进制字符串(前缀为“0o”或不带前缀)，可以使用以下任何一种方法：

```python
>>> '%#o' % 10, '%o' % 10
('0o12', '12')
>>> format(10, '#o'), format(10, 'o')
('0o12', '12')
>>> f'{10:#o}', f'{10:o}'
('0o12', '12')
```

​    有关更多信息，请参见`format()`。

==**open**(*file*, *mode='r'*, *buffering=-1*, *encoding=None*, *errors=None*, *newline=None*, *closefd=True*, *opener=None*)==

​    打开文件并返回相应的`文件对象`。如果文件无法打开，则会引发一个`OSError`。

​    *file*是一个类路径的对象，它给出要打开的文件的路径名(绝对或相对于当前工作目录)或要包装的文件的整数文件描述符。(如果给定文件描述符，则在关闭返回的I/O对象时关闭它，除非将*closefd*设置为`False`。)

​    *mode*是一个可选字符串，它指定打开文件的模式。它的默认值是`'r'`，这意味着在文本模式下可以打开阅读。其他常见的值有:`'w'`表示写入(如果文件已经存在就截断它)，`'x'`表示单独创建，`'a'`表示追加(在某些Unix系统中，这意味着所有写入都将追加到文件的末尾，而不管当前的查找位置如何)。在文本模式中，如果没有指定*encoding*，则使用的编码依赖于平台调用:`locale.getpreferredencoding(False)`来获取当前的地区编码。(对于读取和写入原始字节，使用二进制模式，不指定*encoding*。)可用的模式有:

| Character | Meaning                                    |
| --------- | ------------------------------------------ |
| `'r'`     | 打开阅读(默认)                             |
| `'w'`     | 打开以进行写入，首先截断文件               |
| `'x'`     | 打开单独创建，如果文件已经存在则失败       |
| `'a'`     | 打开以供写入，如果文件存在则追加到文件末尾 |
| `'b'`     | 二进制模式                                 |
| `'t'`     | 文本模式(默认)                             |
| `'+'`     | 打开用于更新(读取和写入)的磁盘文件         |
| `'U'`     | `universal newlines`模式(弃用)             |

​    默认模式是“r”(打开阅读文本，它是`'rt'`的同义词)。对于二进制读写访问，模式`'w+b'`打开并将文件截断为0字节。`'r+b'`打开文件没有截断。

​    正如概述中提到的，Python区分二进制和文本I/O。以二进制模式打开的文件(包括*mode*参数中的`'b'`)将内容作为`bytes`对象返回，无需任何解码。在文本模式下(默认情况下，或者在模式参数中包含`'t'`时)，文件的内容以`str`返回，字节首先使用依赖于平台的编码进行解码，如果给定*encoding*，则使用指定的编码。

> ⚠️**注意：Python不依赖于底层操作系统对文本文件的注释;所有的处理都是由Python本身完成的，因此是独立于平台的。**

​    `buffering`是一个可选整数，用于设置缓冲策略。传递0以关闭缓冲(仅在二进制模式下允许)，传递1以选择行缓冲(仅在文本模式下可用)，传递一个大于1的整数，以字节表示固定大小块缓冲区的大小。当没有给出`buffering`参数时，默认的缓冲策略工作方式如下:

* 二进制文件以固定大小的块缓冲;缓冲区的大小是使用启发式来确定底层设备的“块大小”并返回到`io.DEFAULT_BUFFER_SIZE`。在许多系统上，缓冲区通常为4096或8192字节长。
* “交互式”文本文件(`isatty()`返回`True`的文件)使用行缓冲。其他文本文件使用上述二进制文件策略。

​    *encoding*是用于解码或编码文件的编码的名称。这应该只在文本模式下使用。默认编码依赖于平台(`locale.getpreferredencoding()`返回的值)，但是Python支持的任何`text encoding`都可以使用。有关支持的编码列表，请参见`codecs`模块。

​    `errors`是一个可选字符串，它指定如何处理编码和解码错误——不能在二进制模式中使用。虽然在`codec .register_error()`中注册的任何错误处理名称都是有效的，但是仍然可以使用各种标准错误处理程序(在错误处理程序下列出)。标准名称包括:

* `'strict' `如果存在编码错误，则引发`ValueError`异常。默认值`None`具有相同的效果。
* `'ignore`忽略错误。注意，忽略编码错误会导致数据丢失。
* `'replace'`在数据格式不正确的地方插入替换标记(例如`'?'`)。
* `'surrogateescape'`将任何不正确的字节表示为Unicode私有使用区域中的代码点，范围从U+DC80到U+DCFF。当写入数据时使用`surrogateescape`错误处理程序时，这些私有代码点将被转换回相同的字节。这对于处理未知编码的文件非常有用。
* `'xmlcharrefreplace'`只在写入文件时受支持。编码不支持的字符被替换为适当的XML字符引用&#nnn;。
* `'backslashreplace'`用Python的反斜杠转义序列替换格式错误的数据。
* `'namereplace'`(也只在写入时支持)将不支持的字符替换为`\N{…}`转义序列。

​    *newline*控制如何通用换行模式(它只适用于文本模式)。它可以是`None`，`''`，`'\n'`，` '\r'`，` '\r\n'`。它的工作原理如下:

* 当从流读取输入时，如果*newline*为`None`，则启用通用换行模式。输入中的行可以以`'\n'`、`'\r'`或`'\r\n'`结尾，这些行在返回给调用方之前被转换为`'\n'`。如果是`''`，则启用通用换行模式，但行尾将未翻译地返回给调用方。如果它有任何其他合法值，输入行仅由给定的字符串终止，并且行结束未翻译地返回给调用方。
* 当向流写入输出时，如果换行符为`None`，则写入的任何`'\n'`字符都被转换为系统默认的行分隔符`os.linesep`。如果*newline*是`''`或`'\n'`，则不进行翻译。如果*newline*是其他合法值之一，那么写入的任何`'\n'`字符都将被转换为给定的字符串。

​    如果*closefd*为`False`，并且提供的是文件描述符而不是文件名，那么在关闭文件时，底层文件描述符将保持打开状态。如果文件名给定的*closefd*必须为`True`(默认)，否则将引发错误。

​    自定义文件打开器可以通过传递可调用的*opener*来使用。然后，通过调用opener并传递(*file*、*flags*)来获得文件对象的底层文件描述符。必须返回打开的文件描述符(传递os.open 作为 opener的功能类似于传递None)。

​    新创建的文件是不可继承的。

​    下面的例子使用`os.open()`函数的`dir_fd`参数来打开相对于给定目录的文件:

```python
>>> import os
>>> dir_fd = os.open('somedir', os.O_RDONLY)
>>> def opener(path, flags):
...     return os.open(path, flags, dir_fd=dir_fd)
...
>>> with open('spamspam.txt', 'w', opener=opener) as f:
...     print('This will be written to somedir/spamspam.txt', file=f)
...
>>> os.close(dir_fd)  # don't leak a file descriptor
```

​    `open()`函数返回的文件对象的类型取决于模式。当`open()`用于以文本模式(`'w'`、`'r'`、`'wt'`、`'rt'`等)打开文件时，它返回`io.TextIOBase`的子类(特别是`io.TextIOWrapper`)。当以二进制模式打开带有缓冲的文件时，返回的类是`io.BufferedIOBase`的子类。具体的类是不同的:在读取二进制模式下，它返回一个`io.BufferedReader`;在写二进制和追加二进制模式中，它返回`io.BufferedWriter`。在读/写模式下，它返回一个`io.BufferedRandom`。当缓冲被禁用时，原始流，io.RawIOBase的子类——`io.FileIO`返回。

​    也请参阅文件处理模块，例如，`fileinput`、`io`(声明`open()`处)、`os`、`os.path`、`tempfile`和`shutil`。

​    版本3.3更新：

* 添加了*opener*参数。
* 添加了`'x'`模式。
* 曾经引发`IOError`，现在它是`OSError`的别名。
* 如果以仅创建模式(`'x'`)打开的文件已经存在，则会引发`FileExistsError`。

​    版本3.4更新：

* 文件现在是不可继承的。

​    从3.4版本开始不支持，将在4.0版本中删除:`'U'`模式。

​    版本3.5更新：

* 如果系统调用被中断，并且信号处理程序没有引发异常，则该函数重试系统调用，而不是引发`InterruptedError`异常(参见`PEP 475`了解其基本原理)。
* 添加了`'namereplace'`错误处理程序。

​    版本3.6更新：

* 支持添加接受实现`os.PathLike`的对象。
* 在Windows上，打开控制台缓冲区可能返回io.RawIOBase的子类，而不是io.FileIO。

==**ord**(*c*)==

​    给定一个表示一个Unicode字符的字符串，返回一个表示该字符的Unicode编码点的整数。例如`ord('a')`返回整数`97`和`ord('€')`(欧元符号)返回`8364`。这是`chr()`的逆。

==**pow**(*x*, *y*[, *z*])==

​    返回*x*的*y*次方;如果存在*z*，则返回*x*的*y*次方，模z(计算效率高于`pow(x, y) % z`)。双参数形式`pow(x, y)`等价于使用幂运算符:`x**y`。

​    参数必须具有数字类型。对于混合操作数类型，适用二进制算术运算符的强制规则。对于`int`操作数，结果与操作数的类型相同(强制之后)，除非第二个参数为负值;在这种情况下，所有参数都转换为`float`，并交付一个`float`结果。例如，`10**2`返回`100`，但是`10**-2`返回`0.01`。如果第二个参数为负，则必须省略第三个参数。如果*z*存在，*x*和*y*必须是整数类型，*y*必须是非负的。

==**print**(**objects*, *sep=' '*, *end='\n'*, *file=sys.stdout*, *flush=False*)==

​    将*objects*打印到文本流*file*中，由`sep`分隔，然后是*end*。*sep*、*end*、*file*和*flush*(如果存在)必须作为关键字参数给出。

​    所有非关键字参数都被转换为字符串，就像`str()`所做的那样，并写入流中，由*sep*分隔，然后是*end*。*sep*和*end*都必须是字符串;它们也可以是`None`，这意味着使用默认值。如果没有*objects*，`print()`将只写*end*。

​    *file*参数必须是具有`write(string)`方法的对象;如果它不存在或没有，将使用sys.stdout。由于打印的参数被转换为文本字符串，所以`print()`不能与二进制模式的文件对象一起使用。对于这些，使用`file.write(…)`代替。

​    是否缓冲输出通常由*file*决定，但是如果*flush*关键字参数为`True`，则强制刷新流。

​    版本3.3更新：添加flush关键字参数。

==class **property**(*fget=None*, *fset=None*, *fdel=None*, *doc=None*)==

​    返回一个所有权属性。

​    *fget*是一个获取属性值的函数。*fset*是一个设置属性值的函数。*fdel*是一个用于删除属性值的函数。*doc*为属性创建一个docstring。

​    一个典型的用法是定义托管属性*x*:

```python
class C:
    def __init__(self):
        self._x = None

    def getx(self):
        return self._x

    def setx(self, value):
        self._x = value

    def delx(self):
        del self._x

    x = property(getx, setx, delx, "I'm the 'x' property.")
```

​    如果*c*是*C*的一个实例，`c.x`将调用getter `c.x = value`将调用setter，`del c.x `将调用delx。

​    如果给定，*doc*将是property属性的docstring。否则，property将复制*fget*的docstring(如果它存在的话)。这使得使用property()作为decorator来创建只读属性成为可能:

```python
class Parrot:
    def __init__(self):
        self._voltage = 100000

    @property
    def voltage(self):
        """Get the current voltage."""
        return self._voltage
```

​    `@property`装饰器将`voltage()`方法转换为同名只读属性的“getter”方法，并将voltage的文档字符串设置为“Get the current voltage”。

​    property对象具有`getter`、`setter`和`deleter`方法，这些方法可用作修饰符，它们创建property的副本，并将相应的访问器函数设置为修饰后的函数。最好用一个例子来解释:

```python
class C:
    def __init__(self):
        self._x = None

    @property
    def x(self):
        """I'm the 'x' property."""
        return self._x

    @x.setter
    def x(self, value):
        self._x = value

    @x.deleter
    def x(self):
        del self._x
```

​    这段代码与第一个示例完全相同。确保附加函数的名称与原始属性相同(在本例中为`x`)。

​    返回的property对象还具有与构造函数参数相对应的属性`fget`、`fset`和`fdel`。

​    3.5版本更新:property对象的文档字符串现在是可写的。

==**range**(*stop*)==

==**range**(*start*, *stop*[, *step*])==

​    `range`不是一个函数，它实际上是一个不可变的序列类型，就像在`Ranges`和序列类型——list、tuple、range中记录的那样。

==**repr**(*object*)==

​    返回包含对象的可打印表示形式的字符串。对于许多类型,这个函数试图返回一个字符串,将产生一个具有相同值 的对象传递给`eval()`,否则表示形式是用尖括号括起来的字符串,它包含的类型对象的名称加上额外的信息通常包括对象的名称和地址。类可以通过定义`__repr__()`方法来控制这个函数返回给它的实例的内容。

==**reserved**(*seq*)==

​    返回一个反向迭代器。*seq*必须是具有`__reversed__()`方法或支持序列协议(`__len__()`方法和`__getitem__()`方法的对象，该方法的整数参数从0开始)。 

==**round**(*number*[, *ndigits*])==

​    返回小数点后四舍五入为*ndigits*位的*number*。如果省略了*ndigits*或为`None`，则返回其输入的最近整数。

​    对于支持`round()`的内置类型，值四舍五入到最接近10的幂减*ndigits*位数的倍数;如果两个倍数相等，则四舍五入是针对偶数进行的(例如，round(0.5)和round(-0.5)都是0，round(1.5)是2)。如果省略n位数或没有，则返回值为整数。否则，返回值的类型与number相同。

​    对于一般的Python对象`number`，将`round`委托给`number.__round__`。

> ⚠️**注意：对于浮点数，round()的行为可能令人惊讶:例如，round(2.675, 2)给出2.67，而不是预期的2.68。这不是一个bug:这是因为大多数十进制分数不能准确地表示为浮点数。有关更多信息，请参见浮点算法:问题和限制。**

==class **set**([*iterable*])==

   返回一个新的`set`对象，可以选择从`iterable`获取元素。`set`是一个内置类。有关该类的文档，请参见`set`和`Set Type——set、frozenset`。

对于其他容器，请参见内置的`frozenset`、`list`、`tuple`和`dict`类，以及`collections`模块。

==**setattr**(*object*, *name*, *value*)== 

​    这是`getattr()`的对应项。参数是一个对象、一个字符串和一个任意值。字符串可以命名现有属性或新属性。如果对象允许，函数将值赋给属性。例如`setattr(x， 'foobar'， 123)`等于`x.foobar = 123`。

==class **slice**(*stop*)==

==class **slice**(*start*, *stop*[, *step*])==

​    返回一个`slice`对象，该对象表示由`range(start, stop, step)`指定的索引集。*start*和*step*参数默认为`None`。slice对象具有只读数据属性**start**、**stop**和**step**，这些属性只返回参数值(或它们的默认值)。它们没有其他显式功能;但是它们被Numerical Python和其他第三方扩展所使用。使用扩展索引语法时也会生成slice对象。例如:`a[start:stop:step]`或`a[start:stop, i]`。有关返回迭代器的替代版本，请参见`itertools.islice()`。

==**sorted**(*iterable*, *\**, *key=None*, *reverse=False*)==

​    从iterable中的项返回一个新的排序列表。

​    有两个必须指定为关键字参数的可选参数。

​    *key*指定一个参数的函数，该函数用于从每个列表元素中提取比较键:`key=str.lower`。默认值为`None`(直接比较元素)。

​    `reverse`是一个布尔值。如果设置为`True`，那么列表元素的排序就好像每次比较都是颠倒的一样。

​    使用`functools.cmp_to_key()`将旧式*cmp*函数转换为*key*函数。

​    内置的`sorted()`函数保证是稳定的。排序是稳定的，如果它保证不改变比较相等的元素的相对顺序——这有助于在多个通道中排序(例如，按部门排序，然后按工资等级排序)。

​    有关排序示例和简要排序教程，请参见`Sorting HOW TO`。

==@**staticmethod**==

​    将方法转换为静态方法。

​    静态方法不接收隐式的第一个参数。要声明静态方法，请使用以下习惯用法:

```python
class C:
    @staticmethod
    def f(arg1, arg2, ...): ...
```

​    `@staticmethod`表单是一个函数`装饰器`——有关详细信息，请参阅函数定义中的函数定义描述。

​    它既可以在类(如`C.f()`)上调用，也可以在实例(如`C().f()`上调用。除了类之外，实例将被忽略。

​    Python中的静态方法类似于Java或C++中的静态方法。还请参阅`classmethod()`，了解用于创建备用类构造函数的变量。

​    与所有装饰器一样，也可以将`staticmethod`作为常规函数调用，并对其结果进行处理。在需要从类体引用函数并希望避免自动转换到实例方法的情况下，需要使用这种方法。对于这些情况，使用这个习语:

```python
class C:
    builtin_open = staticmethod(open)
```

​    有关静态方法的更多信息，请参阅关于标准类型层次结构中的`标准类型层次结构`的文档。

==class **str**(*object=''*)==

==class **str**(*object=b''*, *encoding='utf-8'*, *errors=‘strict’*)==

​    返回*object*的`str`版本。有关详细信息，请参见`str()`。

​    `str`是内置的字符串`类`。有关字符串的一般信息，请参见`文本序列类型- str`。

==**sum**(*iterable*[, *start*])==

​    sum从start开始从左到右进行迭代，并返回总数。*start*默认值为0。`iterable`的项通常是数字，并且*start*值不允许是字符串。

​    对于某些使用案例，`sum()`有很好的替代方案。连接字符串序列的首选快速方法是调用`''.join(sequence)`。要添加具有扩展精度的浮点值，请参见`math.fsum()`。要连接一系列可迭代对象，可以考虑使用`itertools.chain()`。

==**super**([*type*[, *object-or-type*]])==

​    返回一个代理对象，该对象将方法调用委托给*type*的父类或兄弟类。这对于访问在类中被重写的继承方法非常有用。搜索顺序与`getattr()`使用的相同，只是*type*本身被跳过了。

​    *type*的`__mro__`属性列出`getattr()`和`super()`使用的方法解析搜索顺序。属性是动态的，可以在继承层次结构更新时更改。

​    如果省略第二个参数，返回的super对象将被解除绑定。如果第二个参数是一个对象，`isinstance(obj, type)`必须为真。如果第二个参数是类型，`issubclass(type2, type)`必须为真(这对于类方法很有用)。

​    *super*有两个典型的用例。在单继承的类层次结构中，可以使用*super*引用父类，而无需显式地命名它们，从而使代码更易于维护。这种用法与在其他编程语言中使用*super*非常相似。

​    第二个使用案例是支持动态执行环境中的协作多继承。这个用例是Python特有的，在静态编译语言或只支持单一继承的语言中找不到。这使得实现多个基类实现相同方法的“菱形图”成为可能。良好的设计要求该方法在每种情况下都具有相同的调用签名(因为调用的顺序是在运行时确定的，因为该顺序可以适应类层次结构中的更改，而且该顺序可以包含在运行时之前未知的同级类)。

​    对于这两个用例，一个典型的超类调用是这样的:

```python
class C(B):
    def method(self, arg):
        super().method(arg)    # This does the same thing as:
                               # super(C, self).method(arg)
```

​    注意，`super()`是作为显式点属性查找(如`super().__getitem__(name)`)绑定过程的一部分实现的。它通过实现自己的`__getattribute__()`方法来按照支持协作多继承的可预测顺序搜索类。因此，对于使用语句或操作符(如`super()[name]`)进行隐式查找，`super()`是未定义的。

​    还要注意，除了0参数形式之外，`super()`并不仅限于在方法内部使用。两个参数表单准确地指定了参数，并提供了适当的引用。0参数表单只在类定义中工作，因为编译器填入必要的细节以正确检索定义的类，以及访问普通方法的当前实例。

​    有关如何使用`super()`设计协作类的实际建议，请参阅`使用super()指南`。

==**tuple**([*iterable*])==

​    tuple并不是一个函数，它实际上是一个不可变的`序列`类型，正如在Tuples和序列类型——list、tuple、range中记录的那样。

==class **type**(*object*)==

==class **type**(*name*, *bases*, *dict*)==

​    使用一个参数，返回*object*的类。返回值是一个类对象，通常与`object.__class__`返回的对象相同。

​    建议使用`isinstance()`内置函数来测试对象的类型，因为它考虑了子类。

​    使用三个参数，返回一个新的类对象。这本质上是`class`语句的动态形式。*name*字符串是类名，并成为*__name__*属性;*bases*元组对基类进行了标记，并成为`__bases__`属性;*dict*字典是包含类体定义的名称空间，它被复制到标准字典中，成为*__dict__*属性。例如，下面两条语句创建了相同的`type`对象:

```python
>>> class X:
...     a = 1
...
>>> X = type('X', (object,), dict(a=1))
```

​    还请参见`Type Objects`。

​    3.6版本更新:`type`的子类不重写`type.__new__`可能不再使用单参数表单来获取对象的类型。

==**vars**([*object*])==

​    为模块、类、实例或任何具有`__dict__`属性的其他对象返回`__dict__`属性。

​    模块和实例等对象具有可更新的`__dict__`属性;然而，其他对象可能对其`__dict__`属性(例如，类使用`types.MappingProxyType`以防止直接更新字典)。

​    毫无疑问，`vars()`的行为类似于`locals()`。注意，局部变量字典只对读取有用，因为对局部变量字典的更新将被忽略。

==**zip**(**iterables*)==

​    创建一个从*iterables*每个元素聚合后的迭代器。

​    返回元组的迭代器，其中第i个元组包含来自每个参数序列或迭代器的第i个元素。当用尽最短的输入迭代器时，迭代器停止。使用一个可迭代参数，它返回一个一元组的迭代器。没有参数，它返回一个空迭代器。等价于:

```python
def zip(*iterables):
    # zip('ABCD', 'xy') --> Ax By
    sentinel = object()
    iterators = [iter(it) for it in iterables]
    while iterators:
        result = []
        for it in iterators:
            elem = next(it, sentinel)
            if elem is sentinel:
                return
            result.append(elem)
        yield tuple(result)
```

​    保证了迭代的从左到右求值顺序。这使得使用`zip(*[iter(s)]*n)`将数据序列聚类为n个长度组成为可能。这将重复相同的迭代器n次，以便每个输出元组拥有对迭代器的n次调用的结果。这可以将输入分割为n个长度的块。

​    如果您不关心从较长的`iterables`中拖出的不匹配的值，`zip()`应该只用于长度不相等的输入。如果这些值很重要，则使用`itertools.zip_longest()`。

​    `zip()`与`*`操作符一起可用于解压列表:

```python
>>> x = [1, 2, 3]
>>> y = [4, 5, 6]
>>> zipped = zip(x, y)
>>> list(zipped)
[(1, 4), (2, 5), (3, 6)]
>>> x2, y2 = zip(*zip(x, y))
>>> x == list(x2) and y == list(y2)
True
```

==**\__import__**(*name*, *globals=None*, *locals=None*, *fromlist=()*, *level=0*)==

> ⚠️**注意：这是一个高级函数，与`importlib .import_module()`不同，在日常Python编程中不需要它。**

​    该函数由`import`语句调用。它可以被取代(通过导入内置模块和分配`builtins.__import__`)为了改变`import`语句的语义,但**强烈**不提倡这样做，因为它通常是更简单的使用`import`挂钩(见`PEP 302`)达到相同的目标，不会导致问题的代码假定默认实现使用的`import`。为了支持`importlib .import_module()`，也不鼓励直接使用`__import__()`。

​    该函数导入模块*name*，可能使用给定的*globals*和*locals*来确定如何在包上下文中解释该名称。*fromlist*给出了应该从按*name*指定的模块导入的对象或子模块的名称。标准实现完全不使用它的*locals*，只使用它的*globals*参数来确定`import`语句的包上下文。

​    *level*指定是使用绝对导入还是相对导入。`0`(默认值)表示只执行绝对导入。*level*的正值表示相对于调用`__import__()`的模块目录要搜索的父目录的数量(详细信息请参见`PEP 328`)。

​    当*name*变量是表单package.module时，通常返回顶级包(直到第一个点的名称)，而不是按*name*命名的模块。但是，当给出一个非空的*fromlist*参数时，将返回按*name*命名的模块。

​    例如，语句`import spam`产生的字节码类似于以下代码:

```python
spam = __import__('spam', globals(), locals(), [], 0)
```

​    在这个调用中语句import spam.ham的结果是：

```python
spam = __import__('spam.ham', globals(), locals(), [], 0)
```

​    请注意`__import__()`如何在这里返回顶级模块，因为这是通过`import`语句绑定到名称的对象。

​    另一方面，语句`from spam.ham import eggs, sausage as saus`会导致：

```python
_temp = __import__('spam.ham', globals(), locals(), ['eggs', 'sausage'], 0)
eggs = _temp.eggs
saus = _temp.sausage
```

​    这里的`spam.ham`模块从`__import__()`返回。从该对象检索要导入的名称并将其分配给各自的名称。

​    如果您只想按名称导入模块(可能在包中)，请使用`importlib .import_module()`。

​    版本3.3更新:不再支持*level*的负值(也将默认值更改为0)。

补充说明：

[1] 注意，解析器只接受unix风格的行尾约定。如果您正在从文件中读取代码，请确保使用换行转换模式来转换Windows或mac风格的换行。