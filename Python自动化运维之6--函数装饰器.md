装饰器：
```
　　装饰器可以使函数执行前和执行后分别执行其他的附加功能，这种在代码运行期间动态增加功能的方式，称之为“装饰器”(Decorator)，装饰器的功能非常强大。装饰器一般接受一个函数对象作为参数，以对其进行增强

装饰器本身是一个函数，用于装饰其他函数
功能：增强被装饰函数的功能
装饰器是一个闭包函数是嵌套函数，通过外层函数提供嵌套函数的环境
装饰器在权限控制，增加额外功能如日志,发送邮件用的比较多
```
装饰器知识准备一：
```
>>> def f1():
...     print("hello world")
... 
>>> def f2(arg):
...     arg()
... 
>>> f2(f1)
hello world
```
装饰器知识准备二：
```
复制代码
>>> def f1():
...     print("hello world")
... 
>>> def f1():
...     print("hello python")
... 
>>> f1()
hello python
```
从上面两个知识准备应该要知道的几点：
```
1.定义函数,需要函数名+()调用才能执行函数

2.函数名是指向函数体,python执行时会把函数体加载到内存,函数名是对函数体的引用

3.函数是可以通过参数的方式传递

4.Python执行代码是从上往下执行,当相同的函数名指向了不同的函数体,越靠近函数执行的函数体才会真正的执行,说白了：函数名在内存中指向了新的函数体,和变量赋值是一样的。

5.python在函数中碰到return关键字就会终止同一级的代码执行
```
1、原函数不带参数的装饰器
　　假设我定义了一个函数f，想要在不改变原来函数定义的情况下，在函数运行前打印出before，函数运行后打印出after，要实现这样一个功能该怎么实现？看下面如何用一个简单的装饰器来实现：

def outer(func):
    def inner():
        print("before")
        result = func()
        print("after")
        return result
    return inner

# (1) @ + 函数名 直接作用在需要装饰的函数上一行
# (2)自动执行outer函数并且将下面的函数名f1当做参数传递到outer()
# (3)将outer函数的返回值inner,重新赋值给f1
@outer
def f1():
    print("F1")
    return "是你"

ret = f1()
print("返回值是:",ret)

执行后的结果是：
before
F1
after
返回值是: 是你
```
python执行代码从上往下执行过程:
```
(1)碰到def outer(func)就把函数体加载到内存

(2)碰到@outer装饰器就会自动执行outer()函数并把f1这个函数名通过参数传递到outer(f1)

(3)碰到def inner()就把函数体加载内存(注意：1.函数体中f1()这个函数已经执行过了print("F1")这段代码

　　　　　　　　　　　　　　　　　　　　　 2.此时inner()函数体中就有了print("before"),print("F1"),print("after")3句代码

                                                                  3.并将返回值赋值给变量result,然后return result返回)

                                                                                      python碰到return同一级代码不再执行了,此时inner()函数就结束了(因为inner函数没有调用,所以没有执行)

(4)碰到return inner,函数outer()就会把inner的函数名(函数名是指向函数体的)重新赋值给了f1,此时f1->指向inner的函数体,而不是指向原来的函数体(print("F1") return "是你"),f1指向了新的函数体

(5)碰到ret = f1(),f1()被调用了就会执行f1函数就会执行inner的函数体,并用ret接收返回值

(6)就print()打印出返回值

 

2、原函数带参数的装饰器
　　在实际中，我们的装饰器可能应用到不同的函数中去，这些函数的参数都不一样，和函数传参是一样的，下面来看看如何将其应用到装饰器中去。

(1)原函数带单个参数或者几个参数,接受参数的时候定义单个形参即可：

复制代码
def outer(func):
    def inner(args):
        print("before")
        ret = func(args)
        print("after")
        return ret
    return inner

@outer
def f1(args):
    print(args)
    return "是你"

ret = f1("aaaaaaaa")
print("返回值是:",ret)
复制代码
(2)接收参数的时候定义万能参数,不管原参数带多少参数：

复制代码
def outer(func):
    def inner(*args,**kwargs):
        print("before")
        ret = func(*args,**kwargs)
        print("after")
        return ret
    return inner

@outer
def f1(args):
    print(args)
    return "是你"

ret = f1("aaaaaaaa")
print("返回值是:",ret)
复制代码
 

3、使用两个装饰器
　　当一个装饰器不够用的话，我们就可以用两个装饰器，当然理解起来也就更复杂了，当使用两个装饰器的话，首先将函数与内层装饰器结合然后在与外层装饰器相结合，要理解使用@语法的时候到底执行了什么，是理解装饰器的关键。这里还是用最简单的例子来进行说明。　　

复制代码
def outer2(func2):
    def inner2(*args,**kwargs):
        print('开始')
        r=func2(*args,**kwargs)
        print('结束')
        return r
    return inner2
 
def outer1(func1):
    def inner1(*args,**kwargs):
        print('start')
        r=func1(*args,**kwargs)
        print('end')
        return r
    return inner1
 
@outer2                                # 这里相当于执行了 f=outer1(f)  f=outer2(f)，步骤如下
@outer1                                #1、f=outer1(f) f被重新赋值为outer1(1)的返回值inner1，
def f():                               #    此时func1为 f():print('f 函数')
    print('f 函数')                     #2、f=outer2(f) 类似f=outer2(inner1) f被重新赋值为outer2的返回值inner2
                                       #    此时func2 为inner1函数 inner1里面func1函数为原来的 f():print('f 函数')
                                                                          
f()                                    # 相当于执行 outer2(inner1)()

执行结果如下：
开始                                   # 在outer函数里面执行，首先打印 ‘开始 ’
start                                 # 执行func2 即执行inner1函数 打印 ‘start’
f 函数                                 # 在inner1函数里面执行 func1 即f()函数，打印 ‘f 函数’
end                                   # f函数执行完，接着执行inner1函数里面的 print('end')
结束                                   # 最后执行inner2函数里面的 print('结束')
复制代码
python执行代码的时候碰到两个装饰器解释过程：

将@outer1和f()先执行，函数outer1()将返回值inner1重新赋值给f,此时f指向的函数体是inner1的函数体,这里称f为新f

@outer2将新f当作参数传入inner2(),然后将返回值inner2重新赋值给f,此时f指向的函数体是inner2的函数体

 

执行过程和解释过程是相反的：从上到下的,先通过第一层@outer2 -----> @outer1 -------> f(),结合执行结果你就很明白了。

 

4、带参数的装饰器　　
　　前面的装饰器本身没有带参数，如果要写一个带参数的装饰器怎么办，那么我们就需要写一个三层的装饰器，而且前面写的装饰器都不太规范，下面来写一个比较规范带参数的装饰器，下面来看一下代码，大家可以将下面的代码自我运行一下

复制代码
import functools
 
def log(k=''):                                      　　#这里参数定义的是一个默认参数，如果没有传入参数，默认为空，可以换成其他类型的参数
    def decorator(func):
        @functools.wraps(func)                      　　#这一句的功能是使被装饰器装饰的函数的函数名不被改变，
        def wrapper(*args, **kwargs):
            print('start')
            print('{}:{}'.format(k, func.__name__))    #这里使用了装饰器的参数k
            r = func(*args, **kwargs)
            print('end')
            return r
        return wrapper
    return decorator
 
@log()                        # fun1=log()(fun1) 装饰器没有使用参数
def fun1(a):
    print(a + 10)
 
fun1(10)
# print(fun1.__name__)        # 上面装饰器如果没有@functools.wraps(func)一句的话，这里打印出的函数名为wrapper
 
@log('excute')                # fun2=log('excute')(fun2) 装饰器使用给定参数
def fun2(a):
    print(a + 20)
fun2(10)
复制代码
 

一个粗糙的例子：
复制代码
USER_INFO = {}

def check_login(func):
    def inner(*args,**kwargs):
        if USER_INFO.get('is_login',None):
            ret = func()
            return ret
        else:
            print("请登录")
    return inner

def check_admin(func):
    def inner(*args,**kwargs):
        if USER_INFO.get('user_type',None) == 2:
            ret = func()
            return ret
        else:
            print("无权限查看")
    return inner


@check_login
@check_admin
def index():
    """
    管理员用户
    :return:
    """
    print('index')


@check_login
def home():
    """
    普通用户
    :return:
    """
    print('home')

def login():
    user = input("请输入用户名:")
    if user == 'admin':
        USER_INFO['is_login'] = True
        USER_INFO['user_type'] = 2
    else:
        USER_INFO['is_login'] = True
        USER_INFO['user_type'] = 1


def main():
    while True:
        inp = input('1、登录;2、查看信息;3、超级管理员管理\n>>>:')
        if inp == '1':
            login()
        elif inp == '2':
            home()
        elif inp == '3':
            index()


main()
