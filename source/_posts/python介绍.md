---
title: python介绍
abbrlink: 2394
date: 2022-03-08 08:25:11
tags: Python
categories: Python学习
---
# Python介绍
### python简介
Python是一个解释型语言
优点：简单、提供很多的基础代码库
缺点：运行速度慢、代码不能加密，源代码暴露

### python解释器
1. Cpython：用的最多
2. Ipython: 交互式解释器
3. PyPy: 执行速度快

### 命令行模式和python交互模式
1. cmd进入的就是命令行模式，输入python可以看到对应的python版本并进入到python交互模式，在交互模式又可以输入exit()退出到命令行模式。
2. 也可以在命令行下 python + 文件名（.py）运行python文件，这里需要时绝对路径。
3. 在python交互模式下可以直接输入100+200回车，会得到300，但是要在文件中运行需要print(100+200)才能看到结果。
4. 在window中py文件不能像exe文件那样直接运行，不过在mac和linux中可以，需要在py文件的第一行加上一个特殊注释**#!/usr/bin/env python3**，然后给该文件赋予执行权限chmod a+x hello.py，最后命令行 ./hello.py 就可以运行。

### 输入输出
1. **输出**
	*  print()，字符串用 ”或 ‘，多个字符串可以用逗号或者+号连接，逗号连接中间会加个空格，+号连接会直接连接起来。
	* 逗号也可以用来连接多个不同类型的输出，例如print("100+200=",100+200)。
	* 按格式输出：print("%s : %s",(str1,str2))
3. **输入**
	* input(),用户可以输入一个字符串，并赋给name，例如，**name=input()**,键盘输入的内容会到name中去。
	* 你也可以加一个输入提示，例如：**name=input("请输入你的姓名：")**
	* input键盘输入的都是字符串类型，例如x1=input("请输入第一个数：") ， x2=input("请输入第二个数：") ，print(x1+x2) 输出结果为23 而不是5 。

【注】input返回结果是str。
	


