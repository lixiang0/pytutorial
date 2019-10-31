## python口袋书

---


#### python map()方法

- 语法：
  map(fun,iter)
  
- 参数：
  - 方法：作用于iter中的元素
  - iter对象，逐个应用于fun方法
  
- 作用：
  讲iter中的元素依次传递给fun方法，最后返回每个元素的结果组成的list。

- 实例：
```
map(lambda x : x*x , [1,2,3,4,5])
#[1,4,9,16,25]
```

---

#### python 中的self

首先要注意的是```self```并不是python中的关键字，而仅仅是为了方便阅读。比如：
```
self=1
print(self)
#1
```
这是因为python中对于方法的调用是通过传递方法所属的实例进行调用的，这就是为什么类方法的第一个参数总是```self```了。

这里给出一个不使用self的示例：
```
class one_class:
  def show(other_self):
    print('we use other_self replace of self')
ne_class().show()
#we use other_self replace of self
```

---


#### python ```__import__()```

```__import__()```用于在运行时引入需要的模块，一般很少使用，效果等同于```import XXX```。

- 语法：
```__import__(name,globals,locals,formlist,level)```

- 参数：
  - name:模块的名字
  - globals和locals：解释器名字
  - formlist：需引入的对象或者子模块
  - level：相对（0）或者绝对（1）//这里指包的路径的相对或绝对

- 示例：
```
np=__import__('numpy',globals(),locals(),[],0)
a=np.array([1,2,3,4,5,6])
print(type(a))
#<class 'numpy.ndarray'>
```

---


#### python hex() oct() bin()

- 语法：
hex(x) oct(x) bin(x) 
- 参数:
  - x:int型整数
- 返回：
  - TypeError：x不是int型
  - str:转换成的16、8、2进制字符串
- 实例：
```
print('___',float.hex(16.))
print('___',hex(16))
print('___',oct(110))
print('___',type(bin(110)))

#___ 0x1.0000000000000p+4
#___ 0x10
#___ 0o156
#___ <class 'str'>
```

---


#### python dir()
python内置方法，以列表方式返回对象的属性和方法
- 语法：
dir([object]) 
- 参数:
  - object:对象名字
- 返回：
  - 返回的是的属性或者基类属性
  - 如果object为空，返回当前命名空间内的属性。
- 示例：
```
dir()
#
['In','Out','_','_1','__','___','__builtin__','__builtins__','__doc__', '__loader__', '__name__', '__package__', '__spec__', '_dh', '_i', '_i1', '_i2', '_ih', '_ii', '_iii', '_oh', 'exit','get_ipython', 'quit','test']
```

---

#### 一行代码从字符串中读取数字

```
test_string = "2019 年 9 月 6 号 下午 3点 。"
#方法1
[int(i) for i in test_string.split() if i.isdigit()]
#方法2
import re
list(map(int,re.findall('\d+',test_string)))
#[2019, 9, 6, 3]
#[2019, 9, 6, 3]
```

---


#### 一行代码从字符串中抽取数字，并找出最大值

```
test_string = "2019 年 9 月 6 号 下午 3点 。"
max([int(i) for i in test_string.split() if i.isdigit()])
#2019
```

---


#### 从字符串去除标点符号

```
import re
import string
test_string = "Geeksforgeeks,    is best @# Computer Science Portal.!!!"
res = re.sub('['+string.punctuation+']', '', test_string).split()
 #
['Geeksforgeeks', 'is', 'best', 'Computer', 'Science', 'Portal']
```

---

#### a+b与a+=b中a不经常等于b
```
a=[1,2,3,4]
b=a
#操作一：a+=[5,6,7,8]
##这里a,b=[1,2,3,4,5,6,7,8]
##操作二：a=a+[5,6,7,8]
#这里a=[1,2,3,4,5,6,7,8] b=[1,2,3,4]
```
解析：+=操作是直接在a上面进行操作，而a=a+[5,6,7,8]是新建了另一个a对象，而b依然指的是之前的[1,2,3,4]对象

---

#### dir()操作

该操作返回的是模块所有的方法和属性，示例：
```
d={}

print(dir(d))

#['__class__', '__contains__', '__delattr__', '__delitem__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', '__getitem__', '__gt__', '__hash__', '__init__', '__iter__', '__le__', '__len__', '__lt__', '__ne__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__setattr__', '__setitem__', '__sizeof__', '__str__', '__subclasshook__', 'clear', 'copy', 'fromkeys', 'get', 'items', 'keys', 'pop', 'popitem', 'setdefault', 'update', 'values']
```
