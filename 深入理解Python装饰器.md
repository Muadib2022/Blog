---
title: 深入理解Python装饰器
top: false
mathjax: false
summary: 深入理解Python装饰器
date: 2019-02-09 20:07:43
author: Topu
categories: Python
tags: 
- 装饰器
---

# 深入理解Python装饰器

主要内容：

- 函数作用域LEGB
- 闭包理解与使用
- 装饰器

## 函数作用域LEGB

**L：local 函数内部作用域**

**E：enclosing函数内部与内墙函数之间**

**G：global全局作用域**

**B：build-in内置作用域**

## 闭包概念

*Closure：内部函数中对enclosing作用域的变量进行引用*

函数的实质与属性

1. 函数是一个对象
2. 函数执行完成后内部变量回收
3. 函数属性
4. 函数返回值



```python
def func_100(val):
	passline = 60
	if val >= passline:
		print('%d pass'%val)
	else:
		print('failes')

def func_150(val):
	passline = 90
	if val >= passline:
		print('%d pass'%val)
	else:
		print('failed')

def set_passline(passline):
	def cmp(val):
		if val >= passline:
			print('pass')
		else:
			print('failed')
	return cmp
f_100 = set_passline(60)
f_150 = set_passline(90)
func_150(89)
func_100(89)
```

python装饰器

1. 装饰器是用来装饰函数的
2. 返回一个函数对象
3. 被装饰函数标识符只想返回的函数对象
4. 语法糖@deco