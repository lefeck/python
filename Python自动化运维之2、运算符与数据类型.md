python对象的相关术语：
```
python程序中保存的所有数据都是围绕对象这个概念展开的：

程序中存储的所有数据都是对象
每个对象都有一个身份、一个类型和一个值
　　　　例如，school='MaGe Linux'会以'MaGe Linux'创建一个字符串对象，其身份是指向它在内存中所处位置的指针(其在内存中的地址),而school就是引用这个具体位置的名称

对象的类型也称对象的类别，用于描述对象的内部表示及它支持的方法和操作
创建特定类型的对象时，有时也将该对象称为该类型的实例
实例被创建后，其身份和类型就不可改变
　　　　如果对象的值是可修改的，则称为可变对象
　　　　如果对象的值不可修改，则称为不可变对象

如果某个对象包含对其他对象的引用，则将其称为容器
大多数对象都拥有大量特有的数据属性和方法
　　　　属性：与对象相关的值
　　　　方法：被调用时将在对象上执行某些操作的函数
　　　　使用点(.)运算符可以访问属性和方法
```
对象的身份与类型：
```
python内置函数id()可返回一个对象的身份，即该对象在内存中的位置

is 运算符用于比较两个对象的身份
type() 用于返回一个对象的类型
对象类型本身也是一个对象，称为对象的类
　　　　(1)该对象的定义是唯一的，且对于某类型的所有实例都是相同的
　　　　(2)所有类型对象都有一个指定的名称，可用于执行类型检查,如list、dict

```
示例：
```
>>> num1 = 5
>>> num2 = 5
>>> num1 == num2 #值比较
>>> True

>>> id(num1)     #内存中的地址
9119808
>>> id(num2)
9119808

>>> num1 is num2 #身份比较
True

>>> type(num1) is type(num2) #类型比较
True
```
运算符　
一、算数运算：
![Image text](https://github.com/wangjinh/picture/blob/master/425762-20151025004451692-544714036.png)

二、比较运算：
```
三、赋值运算：
```

四、逻辑运算：


五、成员运算：


六、身份运算：


七、位运算：
1byte = 8bit

2**8     2**7     2**6    2**5    2**4    2**3    2**2    2**1    2**0

256       128        64        32        16        8          4         2         1


以下实例演示了Python所有位运算符的操作：

 View Code
八、运算符优先级：


更多内容：猛击这里

数据类型
核心数据类型：

数字：int, long(python3.5已经没有), float, complex, bool
字符：str, unicode
列表：list
字典：dict
元组：tuple
集合：set(可变集合),frozenset(不可变集合)
文件：file
数字类型：
python的数字字面量：整数，布尔型，浮点数，复数，所有数字类型均为不可变

int（整型）

　　在32位机器上，整数的位数为32位，取值范围为-2**31～2**31-1，即-2147483648～2147483647
　　在64位系统上，整数的位数为64位，取值范围为-2**63～2**63-1，即-9223372036854775808～9223372036854775807
bool(布尔型)

　   真或假
　　1 或 0
float(浮点型)


数字操作：+ , -, *, /, //, **, %, -x, +x


附上源码：

 View Code
序列类型： 　　

　　序列表示索引为非负整数的有序对象集合，包括字符串、列表和元组
　　　　字符串是字符的
　　　　列表和元组是任意python对象的序列
　　字符和元组属于不可变序列，而列表则支持插入、删除和替换元素等
　　所有序列都支持迭代

序列操作总结：(当然元组是不可变对象,对元素的操作是不支持的,当然了有嵌套列表字典是可以操作的)
s + r      连接
s * n     重复s的n次复制
v1,v2...vn = s     变量解包(unpack)
s[i]         索引
s[i:j]                  切片
s[i:j:stride]         扩展切片
x in s,x not in s   成员关系
for x in s:           迭代
all(s)      如果s中的所有项都为True，则返回True
any(s)    如果s中的任意项为True，则返回True
len(s)     长度,元素个数
min(s)    s中的最小项
max(s)   s中的最大项
sum(s [,initial])    具有可选初始值的项的和
del s[i]     删除一个元素
del s[i:j]   删除一个切片
del s[i:j:stride]    删除一个扩展切片
字符类型：不可变对象
字符串字面量：把文本放入单引号、双引号或三引号中，python2.x默认不是国际字符集unicode，需要unicode定义时加上u,python3无需加

>>> str1 = u'hello world'
>>> type(str1)
unicode
文档字串：模块、类或函数的第一条语句是一个字符的话，该字符串就成为文档字符串，可以使用__doc__属性引用

>>> def printName():
       'test function'
       print('hello world')

>>> printName.__doc__
适用于字符串常用方法：

复制代码
str.capitalize()    将字符串的首字母变大写
str.title()         将字符串中的每个单词的首字母大写
str.upper()         将字符串变成大写
str.lower()         将字符串变成小写
str.index()         找出索引对应的字符串
str.find()          同上
str.count()         找出字符串中元素出现的次数
str.format()        也是格式化的一种
str.center()        以什么字符从字符串两边填充
str.join()          以str为分隔符连接字符串
str.split()         以什么为分隔符分隔字符串
str.strip()         将字符串两边中的空格去掉
str.replace()       查找替换
str.isupper()       判断是否为大写
str.islower()       判断是否为小写
str.isalnum()       判断是否是字母数字
str.isalpha()       判断是否是字母下划线
str.isdigit()       判断是否是数字
str.isspace()       判断是否为空
str.startswith()    找出以什么为开头的字符元素
str.endswith()      找出以什么为结尾的字符元素
复制代码
 附上源码：

 View Code
列表类型：可变对象
表达式符号：[]

创建列表：

name_list = ['alex', 'seven', 'eric']
或
name_list ＝ list(['alex', 'seven', 'eric'])
容器类型
　　任意对象的有序集合，通过索引访问其中的元素，可变对象
　　异构混合类型，可以任意嵌套其它类型

支持在原处修改：
　　修改指定的索引元素，修改指定的分片，删除语句，类的内置方法

 

适用于列表常用方法：

复制代码
list.insert() 在列表中指定索引位置前插入元素
list.append() 在列表尾部插入
list.remove() 删除指定的元素
list.pop() 没有指定索引，则弹出最后一个元素，返回的结果是弹出的索引对应的元素
list.copy() 浅复制,只会复制第一层,如果有嵌套序列则不会复制,如果需要复制则要导入copy模块
list.extend() 把另外一个列表合并，并不是追加
list.index() 列表中元素出现的索引位置
list.count() 统计列表中元素的次数
list.reverse() 进行逆序
list.sort() 进行排序,python3无法把数字和字符串一起排序
l1 + l2 :  合并两个列表，返回一个新的列表，不会修改原列表
l1 * N :   把l1重复N次，返回一个新列表
复制代码
 附上源码：

 View Code
 

#通过索引来修改元素

复制代码
>>> print(l2)
[1, 2, 3, 4, 5]

>>> l2[1] = 32

>>> print(l2)
[1, 32, 3, 4, 5]

>>> l2[3] = 'xyz'

>>> print(l2)
[1, 32, 3, 'xyz', 5]

>>> print(l1)
[1, 2, 3]

>>> l1[1:] = ['m','n','r']

>>> print(l1)
[1,'m','n','r']
复制代码
#通过分片进行删除

复制代码
>>> l2[1:3]
[32, 3]

>>> l2[1:3] = []

>>> print(l2)
[1, 'xyz', 5]
复制代码
#通过内置的函数进行删除

>>> del(l2[1:])

>>> print(l2)
[1]
#通过列表类中的方法进行增删改

复制代码
>>> l3 = [1,2,3,4,5,6]

>>> l3.append(77)

>>> print(l3)
[1, 2, 3, 4, 5, 6, 77]

>>> l4 = ['x','y','z']

>>> l3.append(l4)

>>> print(l3)
[1, 2, 3, 4, 5, 6, 77, ['x', 'y', 'z']]
复制代码
#变量解包

复制代码
>>> l1,l2 = [[1,'x','y'],[2,'z','r']]

>>> print(l1)
[1, 'x', 'y']

>>> type(l1)

>>> print(l2)
[2, 'z', 'r']
复制代码
 #找到列表中的元素并修改

复制代码
tomcat@node:~/scripts$ cat b.py 
name = [1,2,3,4,5,1,5,6]
if 1 in name:
    num_of_ele = name.count(1)
    position_of_ele = name.index(1)
    name[position_of_ele] = 888
    print(name)

tomcat@node:~/scripts$ python b.py 
[888, 2, 3, 4, 5, 1, 5, 6]
复制代码
 #找到列表中的元素并批量修改

复制代码
tomcat@node:~/scripts$ cat b.py 
name = [1,2,3,4,5,1,5,6]

for i in range(name.count(1)):
    ele_index = name.index(1)
    name[ele_index] = 8888888
print(name)
tomcat@node:~/scripts$ python b.py 
[8888888, 2, 3, 4, 5, 8888888, 5, 6]
复制代码
元组类型：不可变对象
表达式符号：()

创建元组：

ages = (11, 22, 33, 44, 55)
或
ages = tuple((11, 22, 33, 44, 55))
容器类型

　　任意对象的有序集合，通过索引访问其中的元素，不可变对象
　　异构混合类型，可以任意嵌套其它类型
　　虽然元组本身不可变，但如果元组内嵌套了可变类型的元素，那么此类元素的修改不会返回新元组

　　(): 空元组
　　(1,): 单个元组需要尾部加上逗号，如果元素是数字没有加逗号则不是元组
　　(1,2): 多元素元组
　　1,2,3,4: 在定义变量时没有加上小括号，默认是元组，最好不建议使用
适用于元组常用方法：

tuple.count() 统计元组中元素的个数
tuple.index() 找出元组中元素的索引位置
 

#在没有嵌套的情况，元组是不可变对象，但是在嵌套了列表，列表是可变的

复制代码
>>> t5 = ('x',[1,2,3,4])

>>> print t5
('x', [1, 2, 3, 4])

>>> t5[1].pop()
4

>>> print(t5)
('x', [1, 2, 3])
复制代码
#元组解包

复制代码
>>> t1,t2 = ((1,2,3,4,5,'xy'),('s','y','w'))

>>> print(t1)
(1, 2, 3, 4, 5, 'xy')

>>> type(t1)
tuple

>>> print(t2)
('s', 'y', 'w')
复制代码
字典类型：dict 可变对象
表达式符号：{}

创建字典：

person = {"name": "tomcat", 'age': 18}
或
person = dict({"name": "tomcat", 'age': 18})
　　字典在其他编程语言中又称作关联数组或散列表
　　通过键(key)实现元素存取，无序的，可变类型容器，长度可变，异构，嵌套

　　{}: 空字典
　　{'x':32,'y':[1,2,3,4]}

两种遍历字典方法：

复制代码
第一种：
for k,v in dict.items():
    print(k,v)


第二种：高效
for key in dict:
    print(key,dict[key])
复制代码
适用于字典常用方法：

复制代码
dict.get(key)      取得某个key的value
dict.has_key(key)  判断字典是否有这个key,在python3中已经废除,使用in 判断
dict.keys()        返回所有的key为一个列表
dict.values()      返回所有的value为一个列表
dict.items()       将字典的键值拆成元组，全部元组组成一个列表
dict.pop(key)      弹出某个key-value
dict.popitem()     随机弹出key-value
dict.clear()       清除字典中所有元素
dict.copy()        字典复制，d2 = d1.copy(),是浅复制,如果深复制需要copy模块
dict.fromkeys(S)   生成一个新字典
dict.update(key)   将一个字典合并到当前字典中
dict.iteritems()   生成key-value迭代器，可以用next()取下个key-value
dict.iterkeys()    生成key迭代器
dict.itervalues()  生成values迭代器
复制代码
 附上源码：

 View Code
 

#字典也支持索引的方式获取,只不过key是他的索引了

复制代码
>>> d1 = {'x':32,'y':[1,2,3,4]}

>>> d1['x']
32

>>> d1['y']
[1, 2, 3, 4]

>>> d1['y'][3:]
[4]

>>> len(d1)
2
复制代码
#变量解包1

复制代码
>>> d1.items()
[('y', [1, 2, 3, 4]), ('x', 32)]

>>> t1,t2 = d1.items()

>>> print(t1)
('y', [1, 2, 3, 4])

>>> print(t2)
('x', 32)
复制代码
#变量解包2

复制代码
>>> d3,d4 = {'x':32,'y':80}

>>> print(d3)
y

>>> print(d4)
x
复制代码
#合并字典，但是在有相同的key时会覆盖原有的key的值

复制代码
>>> d1 = {'x':1,'y':2}

>>> d2 = {'m':21,'n':76,'y':44}

>>> d1.update(d2)

>>> print(d1)
{'y': 44, 'x': 1, 'm': 21, 'n': 76}
复制代码
集合类型：set()可变对象,frozenset()不可变对象
表达式符号：{}

创建集合：

s = {"tom","cat","name","error"}
或
s = set({"tom","cat","name","error"})
集合是一组无序排序的可哈希hash的值,不重复
　　支持集合关系测试:
　　支持成员关系测试：in , not in
　　支持迭代

　　不支持：索引、元素获取、切片

　　{"a",123,"b"}或者set()空集合


没有特定语法格式，只能通过工厂函数创建set，像字符串则直接创建即可	
set集合必须中的元素必须是可迭代对象,所有元素不会重复,不像list列表是可以重复


集合运算符：

复制代码
s | t   s和t的并集
s & t   s和t的交集
s - t   求差集
s ^ t   求对称差集
len(s)  集合中项数
max(s)  最大值
min(s)  最小值    
复制代码
适用于可变集合常用方法：

复制代码
s.add(item)     将item添加到s中。如果item已经在s中，则无任何效果
s.remove(item)  从s中删除item。如果item不是s的成员，则引发KeyError异常
s.discard(item) 从s中删除item.如果item不是s的成员，则无任何效果
s.pop()         随机删除一个任意集合元素，并将其从s删除,如果有变量接收则会接收到删除到的那个元素
s.clear()       删除s中的所有元素
s.copy()        浅复制
s.update(t)     将t中的所有元素添加到s中。t可以是另一个集合、一个序列或者支持迭代的任意对象

s.union(t)        求并集。返回所有在s和t中的元素
s.intersection(t) 求交集。返回所有同时在s和t中的都有的元素
s.intersection_update(t)   计算s与t的交集，并将结果放入s
s.difference(t)            求差集。返回所有在set中，但不在t中的元素
s.difference_update(t)     从s中删除同时也在t中的所有元素
s.symmetric_difference(t)  求对称差集。返回所有s中没有t中的元素和t中没有s中的元素组成的集合
s.sysmmetric_difference_update(t) 计算s与t的对称差集，并将结果放入s

s.isdisjoint(t)   如果s和t没有相同项，则返回True
s.issubset(t)     如果s是t的一个子集，则返回True
s.issuperset(t)   如果s是t的一个超集，则返回True
复制代码
 附上源码：

 View Code
 

不可变集合：
help(frozenset)

 

练习：寻找差异

复制代码
# 数据库中原有
old_dict = {
    "#1":{ 'hostname':'c1', 'cpu_count': 2, 'mem_capicity': 80 },
    "#2":{ 'hostname':'c1', 'cpu_count': 2, 'mem_capicity': 80 },
    "#3":{ 'hostname':'c1', 'cpu_count': 2, 'mem_capicity': 80 }
}
# cmdb 新汇报的数据
new_dict = {
    "#1":{ 'hostname':'c1', 'cpu_count': 2, 'mem_capicity': 800 },
    "#3":{ 'hostname':'c1', 'cpu_count': 2, 'mem_capicity': 80 },
    "#4":{ 'hostname':'c2', 'cpu_count': 2, 'mem_capicity': 80 }
}
old_set=set(old_dict)
new_set=set(new_dict)
 
del_set=old_set.difference(new_set)
add_set=new_set.difference(old_set)
flush_set=old_set.intersection(new_set)
 
for i in del_set:
    old_dict.pop(i)
 
for i in add_set:
    old_dict[i]=new_dict[i]
 
for i in flush_set:
    old_dict[i] = new_dict[i]
print(old_dict)
复制代码
 View Code
深拷贝浅拷贝
　　拷贝意味着对数据重新复制一份，对于拷贝有两种深拷贝，浅拷贝两种拷贝，不同的拷贝有不同的效果。拷贝操作对于基本数据结构需要分两类进行考虑，一类是字符串和数字，另一类是列表、字典等。如果要进行拷贝的操作话，要import copy。

1、数字和字符串　　
　　对于数字和字符串而言，深拷贝，浅拷贝没有什么区别，因为对于数字数字和字符串一旦创建便不能被修改，假如对于字符串进行替代操作，只会在内存中重新生产一个字符串，而对于原字符串，并没有改变，基于这点，深拷贝和浅拷贝对于数字和字符串没有什么区别，下面从代码里面说明这一点。

复制代码
import copy
s='abc'
print(s.replace('c','222'))         # 打印出 ab222
print(s)                            # s='abc' s并没有被修改
s1=copy.deepcopy(s)
s2=copy.copy(s)
 
#可以看出下面的值和地址都一样，所以对于字符串和数字，深浅拷贝不一样，数字和字符串一样就不演示了，大家可以去试一下
print(s,id(s2))                     # abc 1995006649768
print(s1,id(s2))                    # abc 1995006649768
print(s2,id(s2))                    # abc 1995006649768
复制代码
2、字典、列表等数据结构　　
对于字典、列表等数据结构，深拷贝和浅拷贝有区别，从字面上来说，可以看出深拷贝可以完全拷贝，浅拷贝则没有完全拷贝，下面先从内存地址分别来说明，假设 n1 = {"k1": "wu", "k2": 123, "k3": ["alex", 456]}。

　　　　　　　　浅拷贝在内存中只额外创建第一层数据　　　　　　　　　　　　　　　　　深拷贝在内存中将所有的数据重新创建一份

　　　　 

下面从代码上来进行说明，copy.copy()与list.copy(),dict.copy()都属于浅复制

复制代码
import copy
n1 = {"k1": "wu", "k2": 123, "k3": ["alex", 456]}
n2=copy.copy(n1)　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　 # 浅拷贝
n3=copy.deepcopy(n1)　　　　　　　　　　　　　　　　　　　　　　　　　　　　# 深拷贝
print(n1,id(n1),id(n1['k1']),id(n1['k3']))
print(n2,id(n2),id(n2['k1']),id(n2['k3']))
print(n3,id(n3),id(n3['k1']),id(n3['k3']))
 
# 从下面打印的值结合上面的图就可以很好的理解，
# {'k3': ['alex', 456], 'k2': 123, 'k1': 'wu'} 2713748822024 2713753080528 2713755115656　　　　　　
# {'k3': ['alex', 456], 'k2': 123, 'k1': 'wu'} 2713755121416 2713753080528 2713755115656
# {'k3': ['alex', 456], 'k2': 123, 'k1': 'wu'} 2713753267656 2713753080528 2713754905800
复制代码
补充
一 、enumrate
　　为一个可迭代的对象添加序号，可迭代的对象你可以理解成能用for循环的就是可迭代的。默认是编号是从0开始，可以设置从1开始

复制代码
li = ["手机", "电脑", '鼠标垫', '游艇']
for k, i in enumerate(li，1):
    print(k,i)
1 手机
2 电脑
3 鼠标垫
4 游艇
复制代码
二、range和xrange
　　在python2中有xrange和range，其中range会一次在内存中开辟出了所需的所有资源，而xrange则是在for循环中循环一次则开辟一次所需的内存，而在Python3中没有xrange，只有range ，但是python3的range代表的就是xrange。range用来指定范围，生成指定的数字。

for i in range(10):     #循环输出所生成的 0-9
    print(i)
 
for i in range(1,10,2): #输出所生成的 1 3 5 7 9
    print(i)
练习：
一、元素分类
　　有如下值集合 [11,22,33,44,55,66,77,88,99]，将所有大于 66 的值保存至字典的第一个key中，将小于 66 的值保存至第二个key的值中。即： {'k1': 大于66的所有值, 'k2': 小于66的所有值}

复制代码
l= [11,22,33,44,55,66,77,88,99]
bignum=[]
smallnum=[]
dir={}
for num in l:
    if num>66:
        bignum.append(num)
    if num<66:
        smallnum.append(num)
    else:
        pass
dir['k1']=bignum
dir['k2']=smallnum
print(dir)
复制代码
二、查找
　　查找元素，移动空格，并查找以 a或A开头 并且以 c 结尾的所有元素。
　　　　li = ["alec", " aric", "Alex", "Tony", "rain"]
　　　　tu = ("alec", " aric", "Alex", "Tony", "rain") 
　　　　dic = {'k1': "alex", 'k2': ' aric',  "k3": "Alex", "k4": "Tony"}
复制代码
li = ["alec", " aric", "Alex", "Tony", "rain"]
tu = ("alec", " aric", "Alex", "Tony", "rain")
dic = {'k1': "alex", 'k2': ' aric',  "k3": "Alex", "k4": "Tony"}
 
for i in li:
    if i.strip().capitalize().startswith('A') and i.strip().endswith('c'):
        print(i)
for i in tu:
    if i.strip().capitalize().startswith('A') and i.strip().endswith('c'):
        print(i)
for i in dic.values():
    if i.strip().capitalize().startswith('A') and i.strip().endswith('c'):
        print (i)
复制代码
三、输出商品列表，用户输入序号，显示用户选中的商品
 　　商品 li = ["手机", "电脑", '鼠标垫', '游艇']
复制代码
#方法一
l1=[1,2,3,4]
l2=["手机", "电脑", '鼠标垫', '游艇']
d=dict(zip(l1,l2))
print(d)
num=input("请输入商品编号：")
print("你选择的商品为 %s" %d[int(num)])
 
#方法二
li = ["手机", "电脑", '鼠标垫', '游艇']
for k, i in enumerate(li):
    print(k,i)
k=input("请输入商品编号：")
print("你选择的商品为 %s" % li[int(k)])
复制代码
 

 购物车游戏
四、购物车
功能要求：

要求用户输入总资产，例如：2000
显示商品列表，让用户根据序号选择商品，加入购物车
购买，如果商品总额大于总资产，提示账户余额不足，否则，购买成功。
1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
20
21
22
23
24
25
26
27
28
29
30
31
32
33
34
35
36
37
38
39
40
41
product = [
    ("iphone",5800),
    ("watch",380),
    ("bike",800),
    ("book",120),
    ("computer",4000)
]
 
shopping_car = []
 
salary = input("input your salary: ")
if salary.isdigit():
    salary = int(salary)
    while True:
        for i in enumerate(product):
            print(i)
 
        user_choice = input(">>>或者q:")
 
        if user_choice.isdigit():
            user_choice = int(user_choice)
            if user_choice >= 0 and user_choice < len(product):
                p_item = product[user_choice]
                if salary >= p_item[1]:
                    shopping_car.append(p_item[0])
                    salary -= p_item[1]
                    print("你购买了\033[32m%s\033[0m,你的余额剩余\033[31m%s\033[0m" % (p_item[0], salary))
                else:
                    print("\033[31m你的余额不足\033[0m")
            else:
                print("你输入的项目[%s]不存在,请重新输入" % user_choice)
        elif user_choice == 'q':
            print("你购买了这些商品:".center(30,"-"))
            for i in shopping_car:
                print("\033[32m%s\033[0m" %i)
            print("\033[31m余额%s\033[0m" %salary)
            exit()
        else:
            print("你输入的[%s]不存在" % user_choice)
else:
    print("你输入的金额不正确！请重新输入金额！")
　　

五、用户交互，显示省市县三级联动的选择
复制代码
dic = {
    "河北": {
        "石家庄": ["鹿泉", "藁城", "元氏"],
        "邯郸": ["永年", "涉县", "磁县"],
    },
    "湖南": {
        "长沙":['a','b','c'],
        "株洲":['d','e','f']
    },
    "湖北": {
        "武汉":['g','h','i'],
        "黄石":['j','k','l']
    }
}
for k in dic.keys():
    print(k)
flag=True
while flag:
    n=input("请输入你所在省：")
    for k in dic.keys():
        if n in dic.keys():
            if k == n:
                for i in dic[n].keys():
                    print(i)
                w = input("请输入你所在的城市：")
                for i in dic[n].keys():
                    if w in dic[n].keys():
                        if i == w:
                            for k in dic[n][w]:
                                print(k)
                            s=input("请输入你所在的县：")
                            for j in dic[n][w]:
                                if s in dic[n][w]:
                                    if j==s:
                                        print("你所在的位置是：%s省%s市%s县" % (n,w,s))
                                        flag = False
                                        break
                                else:
                                    print('不存在，请重新输入')
                                    break
                    else:
                        print('不存在，请重新输入')
                        break
        else:
            print('不存在，请重新输入')
            break
