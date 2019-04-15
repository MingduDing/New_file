## 时间复杂度

**大O记法**：对于单调的整数函数f，如果存在一个整数函数g和实常数c>0，使得对于充分大的n总有f(n)<=c*g(n)，就说函数g是f的一个渐近函数（忽略常数），记为f(n)=Og(n)。

**时间复杂度**：假设存在函数g，是的算法A处理规模为n的问题示例所用时间位T(n)=Og(n)，则称Og(n)为算法A的渐近时间复杂度，简称时间复杂度，记为T(n)。

* **最优时间复杂度**：算法完成工作最少需要多少基本操作
* **最坏时间复杂度**：算法完成工作最多需要多少基本操作
* **平均时间复杂度**：算法完成工作平均需要多少基本操作

## 时间复杂度计算规则

1. ==基本操作==：即只有常数项，认为其时间复杂度为O(1)
2. ==顺序结构==：时间复杂度按**加法**进行计算
3. ==循环结构==：时间复杂度按**乘法**进行计算
4. ==分支结构==：时间复杂度取**最大值**
5. 判断一个算法的效率时，往往只需要关注操作数量的最高次项，其他次要项和常数项可以忽略
6. 在没有特殊说明时，我们所分析的算法的时间复杂度都是指**最坏时间复杂度**

## 常见时间复杂度

|   执行次数函数举例   |     阶     | 非正式术语 |
| :------------------: | :--------: | :--------: |
|         $12$         |   $O(1)$   |   常数阶   |
|        $2n+3$        |   $O(n)$   |   线性阶   |
|     $3n^2+2n+1$      |  $O(n^2)$  |   平方阶   |
|     $5log_2n+20$     | $O(logn)$  |   对数阶   |
|   $2n+3nlog_2n+19$   | $O(nlogn)$ | $nlogn$阶  |
| $6n^3 + 2n^2 +3n +4$ |  $O(n^3)$  |   立方阶   |
|        $2^n$         |  $O(2^n)$  |   指数阶   |

**注意**：$log_2n$简写成了$logn$。

所消耗时间大小关系：

**$O(1) < O(logn) < O(n) < O(nlogn) < O(n^2) < O(n^3) < O(2^n) < O(n!) < O(n^n)​$**

```python
count = 0
while count < n:
    count = count * 2
```

当$2^x=n​$时，得到$x=logn​$，时间复杂度就是$logn​$。

## 数据结构

**数据**是一个抽象的概念，将其进行分类后得程序设计语言中的基本类型。如：int, float, char等。数据元素之间不是独立的，存在特定的关系，这些关系便是**结构**。

**数据结构**指数据对象中数据元素之间的关系。

根据线性表的实际存储方式，分为两种实现模型：

* 顺序表，将元素顺序地存放在一块连续的存储区里，元素间的顺序关系由他们的存储顺序自然表示。
* 链表，将元素存放在通过链接构造起来的一系列存储块中。

| 操作            | 链表 | 顺序表 |
| --------------- | ---- | ------ |
| 访问元素        | O(n) | O(1)   |
| 在头部插入/删除 | O(1) | O(n)   |
| 在尾部插入/删除 | O(n) | O(1)   |
| 在中间插入/删除 | O(n) | O(n)   |

链表的主要耗时操作是遍历查找，删除和插入操作本身的复杂度是O(1)。

顺序表查找很快，主要耗时是拷贝覆盖。因为顺序表进行插入和删除操作时需要对操作点之后的所有元素进行前后移位操作，只能通过拷贝和覆盖的方式进行。

* **顺序表**：将元素顺序地存放在一块连续的存储区中，元素间的顺序关系由它们的存储顺序自然表示。
* **链表**：将元素存放在通过链接构造起来的一系列存储块中。

二者都是**线性表**。

#### 栈

​	栈是一种容器，可存入数据元素、访问元素、删除元素，只能允许在**top**（栈顶）进行**push**（加入数据）和**pop**（输出数据）。没有位置概念，确定了一种默认的访问顺序，按照后进先出（**LIFO**，Last In First Out）原理运作。

#### 队列

​	队列是一种先进先出（**FIFO**，First In First Out）的线性表。允许插入的一端为队尾，允许删除的一端为队头。

## 排序与搜索

**稳定性：**稳定排序算法会让原本有相等键值的记录维持相对次序。即当有两个相等键值的记录R和S，且原本的列表中R出现在S之前，且排序过的列表中R也将会是在S之前。

#### 冒泡排序

```python
def bubble_sort(alist):
    """冒泡排序"""
    n = len(alist)
    for j in range(n-1,0,-1):
    	count = 0
    	for i in range(j):
        	if alist[i] > alist[i+1]:
    			alist[i], alist[i+1] = alist[i+1], alist[i]
                count += 1
        if count == 0:
            return
```

最优时间复杂度：$O(n)$（表示遍历一遍发现没有任何可以交换的元素）

最坏时间复杂度：$O(n^2)​$

稳定性：**√**

#### 选择排序

```python
def select_sort(alist):
    """选择排序"""
    n = len(alist)
    for j in range(n-1):
    	min_index = j
    	for i in range(j+1, n):
        	if alist[i] < alist[min_index]:
           		min_index = i
    	alist[j], alist[min_index] = alist[min_index], alist[j]
```

最优时间复杂度：$O(n^2)​$

最坏时间复杂度：$O(n^2)​$

稳定性：**X**（考虑升序每次选择最大的情况）

#### 插入排序

```python
def insert_sort(alist):
    """插入排序"""
    for j in range(1, len(alist)):
        for i in range(j, 0, -1):
            if alist[j] < alist[j-1]:
                alist[j], alist[j-1] = alist[j-1], alist[j]
            else:
                break
```

最优时间复杂度：$O(n)$（升序排列，序列已经处于升序状态）

最坏时间复杂度：$O(n^2)​$

稳定性：**√**

#### 快速排序

```python
def quick_sort(alist, first, last):
	"""快速排序"""	
	if first >= last:
		return
	mid_value = alist[first]
	low = first
	high = last
	
	while low < high:
		# high游标左移
		while low < high and alist[high] >= mid_value:
			high -= 1
		alist[low] = alist[high]		
		# low游标右移
		while low < high and alist[low] < mid_value:
			low += 1
		alist[high] = alist[low]
	
	# 循环退出，low==high
	alist[low] = mid_value	
	# 对low左边的列表执行快速排序
	quick_sort(alist, first, low-1)	
	# 对low右边的列表执行快速排序
	quick_sort(alist, low+1, last)

if __name__ == "__main__":
	li = [54, 26, 93, 17, 77, 31, 44, 55, 20]
	print li
	quick_sort(li, 0, len(li)-1)
	print li 
```

最优时间复杂度：$O(nlogn)$

最坏时间复杂度：$O(n^2)$

稳定性：**X**

#### 希尔排序

```python
def shell_sort(alist):
	"""希尔排序"""
	n = len(alist)
	gap = n / 2
	while gap > 0:
		for j in range(gap, n):
			i = j
			while i > 0:
				if alist[i] < alist[i-gap]:
					alist[i], alist[i-gap] = alist[i-gap], alist[i]
					i -= gap
				else:
					break
		gap /= 2
```

最优时间复杂度：$$O(n^{1.3})$$（根据步长序列的不同而不同）

最坏时间复杂度：$O(n^2)​$

稳定性：**X**

#### 归并排序

```python
def merge_sort(alist):
	"""归并排序"""
	n = len(alist)
	if n <= 1:
		return alist
	mid = n / 2
	# left_li 采用归并排序后形成的有序的新的列表
	left_li = merge_sort(alist[:mid])
	# right_li 采用归并排序后形成的有序的新的列表
	right_li = merge_sort(alist[mid:])
	# 将两个有序的子序列合并为一个整体，利用两个指针
	left_pointer, right_pointer = 0, 0
	result = []
	
	while left_pointer < len(left_li) and right_pointer < len(right_li):
		if left_li[left_pointer] <= right_li[right_pointer]:
			result.append(left_li[left_pointer])
			left_pointer += 1
		else:
			result.append(right_li[right_pointer])
			right_pointer += 1
			
	result += left_li[left_pointer:]
	result += right_li[right_pointer:]
	return result

if __name__ == "__main__":
	li = [54, 26, 93, 17, 77, 31, 44, 55, 20]
	print li
	sorted_li = merge_sort(li) 
	print sorted_li
```

最优时间复杂度：$O(nlogn)​$

最坏时间复杂度：$O(nlogn)$

稳定性：**√**

| 排序方法 | 平均情况            | 最优情况     | 最坏情况   | 辅助情况         | 稳定性 |
| -------- | ------------------- | ------------ | ---------- | ---------------- | ------ |
| 冒泡排序 | $O(n^2)$            | $O(n)$       | $O(n^2)$   | $O(1)$           | 稳定   |
| 选择排序 | $O(n^2)$            | $O(n^2)$     | $O(n^2)$   | $O(1)$           | 不稳定 |
| 插入排序 | $O(n^2)$            | $O(n)$       | $O(n^2)$   | $O(1)$           | 稳定   |
| 希尔排序 | $O(nlogn)$~$O(n^2)$ | $O(n^{1.3})$ | $O(n^2)$   | $O(1)$           | 不稳定 |
| 堆排序   | $O(nlogn)$          | $O(nlogn)$   | $O(nlogn)$ | $O(1)$           | 不稳定 |
| 归并排序 | $O(nlogn)$          | $O(nlogn)$   | $O(nlogn)$ | $O(n)$           | 稳定   |
| 快速排序 | $O(nlogn)$          | $O(nlogn)$   | $O(n^2)$   | $O(logn)$~$O(n)​$ | 不稳定 |

 ## 树

* 无序树
* 有序树
  * 二叉树
    * 完全二叉树
    * 平衡二叉树（AVL树）
    * 排序二叉树
  * 霍夫曼树
  * B树