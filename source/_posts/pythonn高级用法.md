---
title: pythonn高级用法
abbrlink: 29394
date: 2022-03-09 09:17:04
tags: Python
categories: Python学习
---

# python高级用法

### 切片
适用对象: list、tuple、str
1. `list[:]`返回原样list，:前面表示从哪个数组下标开始，:后表示从哪个数组下标的前一个结束。
2. `list[-1:]`从倒数第一个到最后一个。
3. `list[::5]` 间隔每隔5取一次。

### all() 和 any()
1. `all()` 函数表示一个迭代对象里面都是True才返回True,否则返回False。
2. `any()` 函数表示迭代对象里面只要有一个为True都返回True,否则返回False。

### 迭代
适用对象：list、tuple、dict、set、str等可迭代对象，范围比较广。
1. `for x in list/tuple:` 迭代list和tuple对象
2. `for key in dict:` 迭代dict对象
  `for value in dict.values():` 迭代dict的值
  `for k,v in dict.items():` 迭代dict的key和value
3. `for ch in str:` 迭代字符串对象
4. 如何判断一个对象是否是可迭代对象
	通过collections.abc模块中的Iterable类型来判断：
  `isinstance(object,Iterable)`: 判断object是否可迭代
5. 对list的下标进行循环
  `for i,v in enumerate(list):` 迭代下标和下标对应的值
 	```
	list1=[1,2,3]
	list(enumerate(list1)) == [(0,1),(1,2),(2,3)]
	```

### 列表生成式
写列表生成式时，把要生成的元素放在最前面，后面接for循环，最后可用if语句对循环值进行限制。
1. `[x+x for x in range(1,11)]` 
2. `[x+y for x in range(1,11) for y in range(1,5)]` 这里会生成 10 * 4 = 40 个元素，区别于：
```
[x+y for x,y in zip(range(1,11),range(1,11))]  # 这里是将对应数组下标相同的元素相加
list1=[1,2,3]
list2=[4,5,6]
zip(list1,list2)==[(1,4),(2,5),(3,6)]
```
3. `[x for x in range(1,11) if x%2==0]` 对循环值进行限制,这里if后面不能再跟elif和else了。
4. `[key+'='+value for key,value in dict.items()]`
5. [2 for i in range(3)] == [2,2,2]

### 生成器
一边循环一边计算的机制，称为生成器：generator。
```
L = [x * x for x in range(10)]
L
[0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
g = (x * x for x in range(10))
g
<generator object <genexpr> at 0x1022ef630>
```
1. 用next(g)来获得generator的下一个返回值，每次循环计算下一个值。
2. generator也是一个可迭代对象，可以用for循环。
3. 对于复杂函数的生成器
```
def fib(max):
    n, a, b = 0, 0, 1
    while n < max:
        print(b)
        a, b = b, a + b
        n = n + 1
    return 'done'
```
这是一个普通的斐波那契函数。
现在需要将其改为生成器。
```
def fib(max):
    n, a, b = 0, 0, 1
    while n < max:
        yield b
        a, b = b, a + b
        n = n + 1
    return 'done'
>>> f = fib(6)
>>> f
<generator object fib at 0x104feaaa0>
```
这时该函数就变成了一个生成器，用来生成斐波那契额数列。
4. 普通函数和生成器的执行对比
* 普通函数是顺序执行的，遇到return语句返回或者执行完最后一条语句。
* 生成器是调用next()后才执行，执行到yield中断，并返回yield后的内容。下次再调用next()时，就从该yield处执行。
5. 杨辉三角
```
def triangles():
    L=[1]
    while True:
        yield L
        S=L[:]
        S.append(0)
        L=[S[i-1]+S[i] for i in range(len(S))] 
```

### 迭代器
list、tuple、dict、set、str、generator都可以作为迭代器。
```
isinstance([],Iterable)
```
用来判断是否是迭代对象。
***

### 异常、错误与调试
1. try-except-finally模式
```
try:
	语句
except Ex1:
	语句
finally:
	语句
```
finally不管有没有出错都要执行的语句。

2. try-except-else 模式
当try捕获到异常时会跳转到except处，出错位置后的代码将不再执行，当try没有捕获到错误时，就会跳转到else进行处理。
```
try:
	语句
except Ex1:
	语句
else:
	语句
```
3. raise 手动抛出异常
```
raise ValueError("This is a Exception")
```

4. **pycharm调试**
 * step over 跳过子函数运行，（就是整个函数作为一行运行）。
 * step into 遇到子函数，进入子函数。
 * step out 当单步执行在子函数内，用step out 可以执行完剩余的子函数，并跳出来。
 * resume program 跳到下一个断点处。
