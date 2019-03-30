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

## python中列表、字符串、字典相互转换

1. 列表转字符串

   * 将列表中的内容拼接成一个字符串

     ```python
     list = ['a', 'b', 'c']
     ''.join(list)
     # abc
     ```

   * 将列表中的内容转换成字符串

     ```python
     list = ['a', 1, 'b', 2]
     [str(i) for i in list]
     # ['a', '1', 'b', '2']
     ```
2. 字符串转列表
   * 用`eval`转换
     ```python
     s = "['a', 'b', 'c']"
     eval(s)
     # ['a', 'b', 'c']
     ```
   * 将字符串每个字符转成列表中的值
     ```python
     s = 'abc'
     list(s)
     # ['a', 'b', 'c']
     ```
   * 将字符串分割成列表
     ```python
     s = 'a, b, c'
     s.spilt(',')
     # ['a', 'b', 'c']
     ```
3. 列表转字典
   * 将两个列表转换成字典
     ```python
     list = ['a', 'b', 'c']
     t = [1, 2, 3]
     zip(list, t)
     # <zip object at 0x00000000003013F88>
     dict(zip(list, t))
     # {'a':1, 'b':2, 'c':3}
     ```
   * 将嵌套列表转换为字典
     ```python
     list = [['a', 1], ['b', 2], ['c', 3]]
     dict(1)
     # {'a':1, 'b':2, 'c':3}
     ```
4. 字典转列表
   * 字典中键值转换为列表
     ```python
     d = {'a':1, 'b':2}
     list(d.key())
     # ['a', 'b']
     list(d.values())
     # [1, 2]
     ```
5. 字符串转字典
   * 用`eval`转换
     ```python
     s = "{'a':1, 'b':2}"
     eval(s)
     # {'a':1, 'b':2}
     ```
   * 用`json.loads`转换
     ```python
     s = '{"a":1, "b":2}'
     json.loads(s)
     # {'a':1, 'b':2}
     ```
6. 字典转字符串
   * 用`json.dumps`转换
     ```python
     d = {'a':1, 'b':2}
     json.dumps(d)
     # '{"a":1, "b":2}'
     ```
   * 强转换
     ```python
     d = {'a':1, 'b':2}
     str(d)
     "{'a':1, 'b':2}"
     ```


