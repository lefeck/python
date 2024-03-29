Python简介
```
　　python是吉多·范罗苏姆发明的一种面向对象的脚本语言，可能有些人不知道面向对象和脚本具体是什么意思，但是对于一个初学者来说，现在并不需要明白。大家都知道，当下全栈工程师的概念很火，而Python是一种全栈的开发语言，所以你如果能学好Python，那么前端，后端，测试，大数据分析，爬虫等这些工作你都能胜任。
为什么选择Python
　　关于语言的选择，有各种各样的讨论，在这里我不多说，就引用Python里面的一个彩蛋来说明为什么要选择Python，在Python解释器里输入import this 就可以看到。
```
```
>>> import this
The Zen of Python, by Tim Peters
 
Beautiful is better than ugly.
Explicit is better than implicit.
Simple is better than complex.
Complex is better than complicated.
Flat is better than nested.
Sparse is better than dense.
Readability counts.
Special cases aren't special enough to break the rules.
Although practicality beats purity.
Errors should never pass silently.
Unless explicitly silenced.
In the face of ambiguity, refuse the temptation to guess.
There should be one-- and preferably only one --obvious way to do it.
Although that way may not be obvious at first unless you're Dutch.
Now is better than never.
Although never is often better than *right* now.
If the implementation is hard to explain, it's a bad idea.
If the implementation is easy to explain, it may be a good idea.
Namespaces are one honking great idea -- let's do more of those!
```
上面的话简单的总结来说就是“优雅”、“明确”、“简单”，或许你还是有些不明白，举个简单的例子，若果同样的功能你用C/C++写可能要写100行代码，而如果用Python写你可能只要20行代码就搞定，同样的如果一个问题有好几种解决方案，但是Python会用一种最简单的方法来实现。所以Python是用最简单最优雅最明确的方法来解决问题。

Python入门　

一、Python 2.x vs 3.x区别
```
1.print在python2.x是语句,在python3.x是print()函数

Old: print "The answer is", 2*2
New: print("The answer is", 2*2)
Old: print x, # Trailing comma suppresses newline
New: print(x, end=" ") # Appends a space instead of a newline
Old: print # Prints a newline
New: print() # You must call the function!
Old: print >>sys.stderr, "fatal error"
New: print("fatal error", file=sys.stderr)
Old: print (x, y) # prints repr((x, y))
New: print((x, y)) # Not the same as print(x, y)!

2.python3.x全部字符集都是unicode,而在python2.x中是ascii编码,需要设置#-*- coding:utf-8 -*-,中文才不会乱码

3.python2.x一些库名在python3.x的更改

python2.x	_winreg	ConfigParser	copy_reg	Queue	SocketServer	markupbase	repr	test.test_support
python3.x	winreg	configparser	copyreg	queue	socketserver	_markupbase	reprlib	test.support

4.python3.x有一些第三方模块支持不了,当然还有其他的模块,后续慢慢添加....

Twisted  urllib2  scrapy MySQLdb

5.python2.x与python3.x库方法的不同,在后续慢慢体现....
```
二、安装Python
```
　　在这里我我推荐安装Python3，因为随着时间的推移Python3，必定是未来的趋势，我们要顺应潮流。在Python的官网可以下载相应的版本，网址是https://www.python.org/downloads/，安装上面的提示安装好即可，就不在多说了，此外后面的操作都是基于Ubuntu 15.10下Python3.5.1操作，默认是Python2.7.10版本
      建议使用pyenv(Python版本控制2.7和3.5之间随意切换)、virtualenv(Python虚拟环境)、pycharm(Python的IDE工具)、pip(Python包管理工具)。
```
windows
```
1、下载安装包
    https://www.python.org/downloads/
2、安装python2.7.11
    默认安装路径：C:\python27
3、配置环境变量
    【右键计算机】--》【属性】--》【高级系统设置】--》【高级】--》【环境变量】--》【在第二个内容框中找到 变量名为Path 的一行，双击】 --> 【Python安装目录追加到变值值中，用 ； 分割】
    如：原来的值;C:\python27，切记前面有分号
4、安装python3.5.1
    默认安装路径: C:\python35
5、将python3.5中的执行程序python.exe重命名成python3
6、配置环境变量
    【右键计算机】--》【属性】--》【高级系统设置】--》【高级】--》【环境变量】--》【在第二个内容框中找到 变量名为Path 的一行，双击】 --> 【Python安装目录追加到变值值中，用 ； 分割】
     如：原来的值;C:\python35，切记前面有分号
7、这样就实现python2.7和python3.5多版本
```
三、编写Hello，World
　　两种方式输出Hello World，第一种我们用解释器交互式环境，打开shell输入python。
```
tomcat@node:~$ python
Python 3.5.1 (default, Jul 27 2016, 18:07:46)
[GCC 5.2.1 20151010] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> print("Hello World!")
Hello World!

第二种将代码保存在 .py文件中，命令行下执行 python1.py 就可以打印出来Hello World。

tomcat@node:~$ vim python1.py
#!/usr/bin/env python
# coding:utf-8
print("Hello World!")
 
tomcat@node:~$ chmod +x python1.py
tomcat@node:~$ python python1.py
Hello World!
在Linux下执行的时候，第一行指出文件由python解释器来执行，第二行是告诉解释器在加载文件时，采用何种编码，不加上这句的话，在python2中显示中文会出现乱码，在python3中则不会，所以你如果用的是windows而且用的是python3，其实可以不用加这两句，不过实际中还是建议加上这两句。到这里我们就用了两种方式输Hello World。
```
四、变量&字符编码
```
变量

常量我们约定俗成都为大写

1、变量声明：

Python将所有数据存为内存对象
Python中，变量事实上是指向内存对象的引用
动态类型：在任何时刻，只要需要，某个对象引用都可以重新引用一个不同的对象（可以是不同的数据类型）内建函数type()用于返回给定数据项的数据类型
"="用于将变量名与内存中的某个对象绑定：如果对象实现存在，就直接进行绑定；否则，则由"="创建引用的对象,变量名也是对象存在内存，比如：name='jerry',name这个指针指向jerry，name='tom'的时候，name是指针指向tom，但是jerry仍在内存中存放着，只是没有被变量名指向，到一定时候会被垃圾收集器回收，和java有点像。其中当test='jerry'时，test和name这两个变量名指向内存的地址是一样的。id(test),id(name)，变量名是内存引用的标识或符号。

2、变量定义的规则：

变量名只能是 字母、数字或下划线的任意组合
变量名的第一个字符不能是数字
以下关键字不能声明为变量名
　　 ['and', 'as', 'assert', 'break', 'class', 'continue', 'def', 'del', 'elif', 'else', 'except', 'exec', 'finally', 'for', 'from', 'global', 'if', 'import', 'in', 'is', 'lambda', 'not', 'or', 'pass', 'print', 'raise','return', 'try', 'while', 'with',             'yield']

# 通过Import keyword查看

import keyword
print(keyword.kwlist)

3、变量最佳命名方式：

使用下划线'_'作为连接,如 name_variables
使用大小写,称为驼峰法,如 NameVariables,nameVariables
　　注意：两种命名方式不要混用,只要你喜欢的一种即可

4、变量命名惯例：

以单一下划线开头的变量名(_x)不会被from module import * 语句导入
以两个下划线开头但结尾没有下划线的变量名(__x)是类的本地变量
前后有双下划线的变量名(__x__)是系统定义的变量名，对python解释器有特殊意义
交互式模式下，变量名"_"用于保存最后表达式的结果

字符编码

1、ASCII

　　ASCII（American Standard Code for Information Interchange，美国标准信息交换代码）是基于拉丁字母的一套电脑编码系统，主要用于显示现代英语和其他西欧语言，其最多只能用 8 位来表示（一个字节），即：2**8 = 256-1，所以，ASCII码最多只能表示 255 个符号，python2.x解释器默认是ASCII编码。

显然ASCII码无法将世界上的各种文字和符号全部表示，所以，就需要新出一种可以代表所有字符和符号的编码，即：Unicode

二进制和数字转换：128 64 32 16 8 4 2 1    比如：2表示二进制 0000 0010

字符和数字转换 ： 查看ASCII码表    比如： A字母 表示数字是65，二进制是0100 0001

2、Unicode

　　Unicode（统一码、万国码、单一码）是一种在计算机上使用的字符编码。Unicode 是为了解决传统的字符编码方案的局限而产生的，它为每种语言中的每个字符设定了统一并且唯一的二进制编码，规定所有的字符和符号最少由 16 位来表示（2个字节），即：2 **16 = 65536，注：此处说的的是最少2个字节，可能更多，比如汉字就需要3个字节，python3.x解释器默认是Unicode编码。

3、UTF-8

     是对Unicode编码的压缩和优化，他不再使用最少使用2个字节，而是将所有的字符和符号进行动态分类：ASCII码中的内容用1个字节保存、欧洲的字符用2个字节保存，汉字用3个字节保存...

所以，python2.x解释器在加载 .py 文件中的代码时，会对内容进行编码（默认ASCII），如果是如下代码的话：

报错：ascii码无法表示中文

tomcat@node:~$ vim a.py
#!/usr/bin/env python
print "你好！世界"<br>
tomcat@node:~$ python a.py
  File "a.py", line 2
SyntaxError: Non-ASCII character '\xe4' in file a.py on line 2, but no encoding declared; see http://python.org/dev/peps/pep-0263/ for details
改正：应该显示的告诉python解释器，用什么编码来执行源代码，即：

tomcat@node:~$ vi a.py
#!/usr/bin/env python
# coding:utf-8
print "你好！世界"
 
tomcat@node:~$ python a.py
你好！世界
注意：python3.x中字符集默认为UTF-8,python2.x还是ASCII所以需要设置#coding:utf-8
```
五、输入、输出、注释
```
Python输入：

1、Python3.x提供了一个input()，可以让用户输入字符串。比如输入用户的名字：

python3中格式化输出默认接收的都视为字符串,如果你获取的是要数字类型则需要另外强制转换为int()转换为数字类型才能获得数字

>>> name = input("please input your name:")
please input your name:tomcatxiao
>>> print("Hello " + name)
Hello tomcatxiao
 
>>> age = input("please enter your age:")
please enter your age:21
>>> type(age)
<class 'str'>
 
>>> age1 = input("please enter your age:")
>>> age1 = int(age1)
>>> type(age1)
<class 'int'>
输入密码时，如果想要不可见，需要利用 getpass 模块中的 getpass 方法，即：

tomcat@node:~$ vi b.py
#!/usr/bin/env python
# -*- coding: utf-8 -*-
   
import getpass
   
# 将用户输入的内容赋值给 pwd变量
pwd = getpass.getpass("请输入密码：")
   
# 打印输入的内容
print(pwd)
 
tomcat@node:~$ python b.py
请输入密码：
123
注意：在pycharm IDE工具中这段代码是行不通的,在Linux命令行或者Windows cmd中是可以的

2、Python2.x提供了一个raw_input()和input(),input()在python2中基本不用忘了吧,当然我这里会演示他们的区别

raw_input()在字符串和数值型都没有问题

>>> name = raw_input("please enter your name:")
please enter your name:tomcatxiao
>>> print name
tomcatxiao
 
>>> age = raw_input("your age is:")
your age is:21
>>> print age
21

input()在输入字符串的时候报错,变量未定义,数值型则没有报错,如果是字符串则需要引号'' or ""，或者事先定义变量赋值

>>> name = input("please input your name:")
please input your name:tomcatxiao
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "<string>", line 1, in <module>
NameError: name 'tomcatxiao' is not defined

>>> age = input("your age is:")
your age is:21

对于上面的代码进行修改下,将字符串事先赋值给一个变量,然后从input中输入则没有报错

>>> myname = "tomcatxiao"
>>> name = input("please input your name:")
please input your name:myname

>>> print name
tomcatxiao
Python输出：
Python中输出是用print,Python2.x中print是语句,Python3.x中则是print()函数　　

1.Python2.x

print "String %format1 %format2 ..." %(variable1,variable2)

2.Python3.x

print("String %format1 %format2 ...." %(variable1,variable2))

3.拼接效率比较低

print  "String"  + variable1
print("String"  + variable1)
input()和格式化输出时要特别要注意input()输入是个数字需要int()转换,格式化输出的时候使用%d才不会报错

tomcat@node:~$ vi c.py
#!/usr/bin/env python
# -*- coding:utf-8 -*-
 
name = input("input your name:")
age = input("input your age:")
job = input("input your job:")
 
msg = '''
Information of %s
-------------
Name: %s
Age : %s
Job : %s
''' %(name,name,age,job)
 
print(msg)
 
 
tomcat@node:~$ python c.py
注意：python3中格式化输出默认接收的都视为字符串,如果是数字则需要另外强制转换为int()转换为数字类型

#!/usr/bin/env python
# -*- coding:utf-8 -*-
 
name = input("input your name:")
age = input("input your age:")
job = input("input your job:")
 
msg = '''
Information of %s
-------------
Name: %s
Age : %d
Job : %s
''' %(name,name,age,job)
 
print(msg)
这里的Age用%d进行格式化如果没有强制转换为数字则会报错,执行上面的代码则会报错,int()转换了则不会报错

input your name:tomcatxiao
input your age:21
input your job:IT
Traceback (most recent call last):
  File "/home/tomcat/PycharmProjects/s13/day01/dsfg.py", line 15, in <module>
    ''' %(name,name,age,job)
TypeError: %d format: a number is required, not str
注释
#号可以从一行的任何地方开始

'''''',"""""",三引号用于多行注释

\,表示续行符 

 注意：如果''''''三引号是在一个def 函数或者class 定义类的下方则是对这个函数或者类的说明,可以通过__doc__动态获得文档子串
```
六、模块初识　
```
Python的强大之处在于他有非常丰富和强大的标准库和第三方库，几乎你想实现的任何功能都有相应的Python库支持，以后的课程中会深入讲解常用到的各种库，现在，我们先来象征性的学2个简单的。
```
sys
```
tomcat@node:~$ vi d.py
#!/usr/bin/env python
# -*- coding: utf-8 -*-
  
import sys
  
print(sys.argv)
  
  
#输出
tomcat@node:~$ python d.py helo world
['test.py', 'helo', 'world']  #把执行脚本时传递的参数获取到了
```
os
```
>>> import os
>>> os.system("df -h") #调用系统命令
注意：os.system()执行系统命令,如果有变量存储该执行的结果,该变量只会存储该命令执行成功或者失败返回值,不会存储命令执行的结果,os.system("df -h")会有返回值

>>> result = os.system("df -h")
df: ‘/mnt/hgfs’: Protocol error
Filesystem      Size  Used Avail Use% Mounted on
udev            3.9G     0  3.9G   0% /dev
tmpfs           797M  9.4M  788M   2% /run
/dev/sda1       189G   10G  170G   6% /
tmpfs           3.9G   16M  3.9G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           3.9G     0  3.9G   0% /sys/fs/cgroup
cgmfs           100K     0  100K   0% /run/cgmanager/fs
tmpfs           797M   76K  797M   1% /run/user/1000
 
>>> print(result)
256
如果需要保存命令执行的结果需哟使用os.popen("系统命令").read(),然后使用变量赋值输出即可

>>> result = os.popen("df -h").read()
 
>>> print(result)
Filesystem      Size  Used Avail Use% Mounted on
udev            3.9G     0  3.9G   0% /dev
tmpfs           797M  9.4M  788M   2% /run
/dev/sda1       189G   10G  170G   6% /
tmpfs           3.9G   16M  3.9G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           3.9G     0  3.9G   0% /sys/fs/cgroup
cgmfs           100K     0  100K   0% /run/cgmanager/fs
tmpfs           797M   76K  797M   1% /run/user/1000

tomcat@node:~$ vi e.py
#!/usr/bin/env python
import os,sys
 
os.system(''.join(sys.argv[1:]))
 
# 执行
tomcat@node:~$ python e.py df
df: ‘/mnt/hgfs’: Protocol error
Filesystem     1K-blocks     Used Available Use% Mounted on
udev             4059116        0   4059116   0% /dev
tmpfs             815812     9596    806216   2% /run
/dev/sda1      198036724 10435852 177518160   6% /
tmpfs            4079040    15996   4063044   1% /dev/shm
tmpfs               5120        4      5116   1% /run/lock
tmpfs            4079040        0   4079040   0% /sys/fs/cgroup
cgmfs                100        0       100   0% /run/cgmanager/fs
tmpfs             815812       76    815736   1% /run/user/1000

```
自己写个补全模块tab.py适合python2.x,python3.5都有自带补全功能
```
#!/usr/bin/env python 
# python startup file 
import sys
import readline
import rlcompleter
import atexit
import os
# tab completion 
readline.parse_and_bind('tab: complete')
# history file 
histfile = os.path.join(os.environ['HOME'], '.pythonhistory')
try:
    readline.read_history_file(histfile)
except IOError:
    pass
atexit.register(readline.write_history_file, histfile)
del os, histfile, readline, rlcompleter

写完后保存,导入就可以使用

tomcat@node:~$ python
Python 2.7.11 (default, Jul 27 2016, 18:09:58) 
[GCC 5.2.1 20151010] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import tab
>>> import os
>>> os.
Display all 238 possibilities? (y or n)
os.EX_CANTCREAT             os.fchdir(
os.EX_CONFIG                os.fchmod(
os.EX_DATAERR               os.fchown(
os.EX_IOERR                 os.fdatasync(
os.EX_NOHOST                os.fdopen(

你会发现，上面自己写的tab.py模块只能在当前目录下导入，如果想在系统的何何一个地方都使用怎么办呢？ 此时你就要把这个tab.py放到python全局环境变量目录里啦，用sys.path可以查看,ubuntu是在/usr/lib/python2.7/dist-packages/,centos是在/usr/lib/python2.7/site-packages/

>>> import sys
>>> sys.path
['', '/usr/lib/python2.7', '/usr/lib/python2.7/plat-x86_64-linux-gnu', '/usr/lib/python2.7/lib-tk', 
'/usr/lib/python2.7/lib-old', '/usr/lib/python2.7/lib-dynload', '/usr/local/lib/python2.7/dist-packages', 
'/usr/lib/python2.7/dist-packages', '/usr/lib/python2.7/dist-packages/PILcompat', '/usr/lib/python2.7/dist-packages/gtk-2.0', 
'/usr/lib/python2.7/dist-packages/ubuntu-kylin-sso-client', '/usr/lib/python2.7/dist-packages/ubuntu-sso-client']
```
七、If语句与流程控制

python的比较操作：
```
所有的Python对象都支持比较操作：

可用于测试值相等、相对大小等
如果是复合对象，python会检查其所有部分，包括自动遍历各级嵌套对象，知道可以得出最终结果
测试操作符：

"==" 操作符测试值的相等性
"is" 表达式测试对象的一致性
"in" 成员关系测试
```
如何实现比较操作：

python中不同类型的比较方法：
```
(1)数字：通过相对大小进行比较
(2)字符串：按照字典次序逐次进行比较
(3)列表和元组：自左至右比较各部分内容
(4)字典：对排序之后的(键、值)列表进行比较
```
python中真和假的含义：
```
(1)非0数字为真，否则为假
(2)非空对象为真，否则为假
(3)None则始终为假
比较和相等测试会递归地应用于数据结构中
返回值为True或False
```
组合条件测试：
```
X and Y: 与运算
X or Y: 或运算
not X : 非运算
```
if测试的语法结构：
```
if boolean_expression1:
    suite1
elif boolean_expression2:
    suite2
else:
    else_suite
    
注意： 
elif语句是可选的
仅用与占位，而后在填充相关语句时，可以使用pass
```
if/else三元表达式：
```
通常在为某变量设定默认值时通常用到如下表达式

A = X if Y else Z
或：

if Y:
    A = X
else
    A = Z
其通用条件表达式语法格式为：
expression1 if boolean_express else expression2
如果boolean_express的值为True，则条件表达式的结果为express1,否则为express2
```
八、循环for,while
```
循环机制及应用场景

while循环：

(1)用于编写通用迭代结构
(2)顶端测试为真即会执行循环体，并会重复多次测试知道为假后执行循环后的其他语句
```
for循环：
```
(1)一个通用的序列迭代器，用于遍历任何有序的序列对象内的元素
(2)可用于字符串、元组、列表和其他的内置可迭代对象，以及通过类所创建的新对象

python也提供了一些能够进行隐性迭代的工具：

(1)in成员关系测试
(2)列表解析
(3)map、reduce和filter函数
 

break: 跳出最内层的循环
continue: 跳出所处的最近层循环的开始处
pass: 占位语句

外层变量，可以被内层代码使用
内层变量，不应被外层代码使用
```
while循环：
```
while True: 死循环

语法格式：

while boolean_express:
    while_suite
else:
    else_suite
注意：

else分支为可选部分
只要boolean_express的结果为True，循环就会执行
boolean_express的结果为False时终止循环，此时如果有else分支，则会执行
```
示例：
```
示例1：
>>> url = 'www.mageedu.com'
>>> while url:
       print(url)
       url = url[1:]

示例2：
>>> x = 0;y = 100
>>> while x < y:
       print(x)
       x += 1

示例3：
>>> url = 'www.mageedu.com'
>>> while url:
       print(url)
       url = url[:-1]
   else:
       print('game over')
```
while大量练习:
```
练习1：逐一显示指定列表中的所有元素
>>> l1 = [1,2,3,4,5,6]
>>> count = 0
>>> while l1:
     print(l1[0])
     l1.pop(0)
     

>>> l1 = [1,2,3,4,5,6]
>>> while l1:
     print(l1[-1])
     l1.pop()
     
   
>>> l1 = [1,2,3,4,5,6]
>>> count = 0
>>> while l1 < len(l1):
     print(l1[count])
     count += 1
 

练习2：求100以内所有偶数之和
练习3：逐一显示指定字典的所有键；并于显示结束后说明总键数；
>>> d1 = {'x':1,'y':23,'z':78}
>>> keylists = d1.keys()
>>> while keylists:
        print(keylists[0])
        keylists.pop[0]
    else:
        print(len(d1))
    
    
练习4：创建一个包含了100以内所有奇数的列表
>>> l1 = []
>>> x = 1
>>> while x < 100:
        l1.append(x)
        x += 2


练习5：逆序逐一显示一个列表的所有元素
练习6：列表l1 = [0,1,2,3,4,5,6],列表l2 = ['Sun','Mon','Tue','Wed','Thu','Fri','Sat'],以第一个列表中的元素为键，以第二个列表中的元素为值生成字典d1


>>> l1 = [0,1,2,3,4,5,6]
>>> l2 = ['Sun','Mon','Tue','Wed','Thu','Fri','Sat']
>>> d1 = {}
>>> count = 0
>>> if len(l1) == len(l2):
    while count < len(l1):
        d1[l1[count]] = l2[count]
        count += 1

>>> print(d1)
```
for循环：
```
语法格式：

for expression1 in iterable:
    for_suite
else:
    else_suite
通常，expression或是一个单独的变量，或是一个变量序列，一般以元组的形式给出
如果以元组或列表用于expression,则其中的每个数据项都会拆分到表达式的项

T = [(1,2),(3,4),(5,6),(7,8)]
for (a,b) in T:
　　print(a,b)
  
编写循环的技巧：

(1)for循环比while循环执行速度快
(2)python提供了两个内置函数，用于在for循环中定制特殊的循环python3.x 只有range,python2.x有(range,xrange)

range: 一次性地返回连续的整数列表
xrange: 一次产生一个数据元素，相较于range更节约空间
zip：返回并行的元素元组的列表，常用于在for循环中遍历数个序列
```
range()函数：非完备遍历
```
用于每隔一定的个数元素挑选一个元素

>>> S = 'How are you these days?'
>>> range(0,len(S),2)
[0, 2, 4, 6, 8, 10, 12, 14, 16, 18, 20, 22]
>>> for i in range(0,len(S),2):
       print(S[i])
修改列表

>>> L = [1,2,3,4,5]
>>> for i in range(len(L)):
       L[i] += 1
>>> L
```
zip()函数：并行遍历
```
取得一个或多个序列为参数，将给定序列中的并排的元素配成元组，返回这些元组的列表
当参数长度不同时，zip会以最短序列的长度为准

1.可在for循环中用于实现并行迭代

>>> L1 = [1,2,3,4,5,6,7]
>>> L2 = ['a','b','c','d','e','f','g']
>>> zip(L1,L2)
2.zip也常用于动态构造字典

>>> keys = [1,2,3,4,5,6,7]
>>> vaules = ['Sun','Mon','Tue','Wed','Thu','Fri','Sat']
>>> D = {}
>>> for (k,v) in zip(keys,values)
       D[k] = v
>>> D
```
for循环练习:
```
练习1：逐一分开显示指定字典d1中的所有元素，类似如下;
    k1  v1
    k2  v2

>>> d1 = {'x':123,'y':321,'z':734}
>>> for (k,v) in d1.items():
    print(k,v)
    
y 321
x 123
z 734

练习2：逐一显示列表中l1=['Sun','Mon','Tue','Wed','Thu','Fri','Sat']中索引为奇数的元素;

>>> l1=['Sun','Mon','Tue','Wed','Thu','Fri','Sat']

>>> for i in range(1,len(l1),2):
    print(l1[i])

练习3：将属于列表l1=['Sun','Mon','Tue','Wed','Thu','Fri','Sat'],但不属于列表l2=['Sun','Mon','Tue','Thu','Sat']的所有元素定义为一个新列表l3;

>>> l1=['Sun','Mon','Tue','Wed','Thu','Fri','Sat'] 
>>> l2=['Sun','Mon','Tue','Thu','Sat']
>>> l3 = []
>>> for i in l1:
>>>     if i not in l2:
>>>         l3.append(i)

练习4：将属于列表namelist=['stu1','stu2','stu3','stu4','stu5','stu6','stu7'],删除列表removelist=['stu3','stu7','stu9'];请将属于removelist列表中的每个元素从namelist中移除(属于removelist,但不属于namelist的忽略即可)

>>> namelist=['stu1','stu2','stu3','stu4','stu5','stu6','stu7']
>>> removelist=['stu3','stu7','stu9']
>>> for i in removelist:
>>>     if i in namelist:
>>>         namelist.remove(i)
>>> print(namelist)
```
场景一、用户登陆验证
```
#!/usr/bin/env python
# -*- coding:utf-8 -*-
import getpass

name = 'tom'
pwd = 123456
count = 0

while True:
    if count < 3:
        print("Please enter your name and password !")
        username = input("username:")
        password = getpass.getpass("password:")

        if username == name and password == pwd:
            print("恭喜你登陆成功！")
            break
        else:
            print("登陆失败！用户名或者密码错误")
    else:
        print("你已经输错3次,正在退出....")
        break

    count += 1
```
场景二、猜年龄游戏
```
#!/usr/bin/env python
# -*- coding:utf-8 -*-

age = 22
count = 0

for i in range(10):
    if count < 3:
        a = int(input("please input num:"))
        if a == age:
            print("恭喜你,答对了")
            break
        elif a > age:
            print("你猜的数字大了")
        else:
            print("你猜的数字小了")
    else:
        b = input("你太笨了,这都猜不对,你继续玩吗？(yes or not):")
        if b == 'yes':
            count = 0
            continue
        else:
            print("Bye!下次再玩")

    count += 1
```
