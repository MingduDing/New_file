## 小笔记

* python2.x 中**换行**是加逗号。

* python3.x 中**换行**是end=" "。

#### class：

实例属性优先级 > 类属性优先级

```python
class Student(objet):
	count = 0
    def __init__(self, name):
        self.name = name
```

count = 0 是类属性，创建的每一个实例都会自动增加该属性。

* pass：为了保持程序结构的完整性,不做什么事，一般做占位语句
* return：直接返回函数，所有该函数体内的代码（包括循环体）都不会再执行
* continue：跳出本次循环，从下一个迭代继续运行循环，内层循环执行完毕，外层代码继续运行
* break：跳出所在的当前整个循环，到外层代码继续执行
* exit()：退出整个循环

| break（外层）                                                | break（内层）                                                | continue                                                     |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| <img src="https://images2017.cnblogs.com/blog/1233990/201709/1233990-20170906195557538-1808918089.jpg" style="width:100px height:122px" /> | <img src="https://images2017.cnblogs.com/blog/1233990/201709/1233990-20170906195607726-1997870131.jpg" style="width:100px height:122px" /> | <img src="https://images2017.cnblogs.com/blog/1233990/201709/1233990-20170906195622366-1778530157.jpg" style="width:100px height:122px" /> |
## class中self的作用
```python
class Test:
	def prt(self):
    print self
    print self.__class__

t = Test()  # <__main__.Test object at 0x000000000284E080>
t.prt()  # <class '__main__.Test'>
```

`self`代表了类的实例。

在`Python`的解释器内部，当我们调用`t.prt()`时，实际上`Python`解释成`Test.prt(t)`，也就是说把`self`替换成类的实例。

如果没有`self`，运行时提醒错误如下：prt在定义时没有参数，但是我们运行时强行传了一个参数。由于上面解释过了`t.prt()`等同于`Test.prt(t)`，所以程序提醒我们多传了一个参数`t`。

