---
title: 'Python之禅及注释的写法'
date: 2018-11-15 10:04:39
summary: Python设计哲学的精髓表现
tags: 
- Pythonic
categories: 
- Python
---

# Python之禅

如果你在使用Python，那么Python之禅的概念你必须要了解一下。Python社区的理念都包含其中，要获悉关于Python之禅的所有内容，只需要在终端启动Python并输入‘import this’。

## 英文原版

```
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

英文虽然部分人看着可能会比较吃力，但是翻译过来的东西有些时候难免会变了味道。但是还是贴份中文版上来，毕竟语言是座大山。

## 中文译版

```

Python之禅 by Tim Peters
 
优美胜于丑陋（Python 以编写优美的代码为目标）
明了胜于晦涩（优美的代码应当是明了的，命名规范，风格相似）
简洁胜于复杂（优美的代码应当是简洁的，不要有复杂的内部实现）
复杂胜于凌乱（如果复杂不可避免，那代码间也不能有难懂的关系，要保持接口简洁）
扁平胜于嵌套（优美的代码应当是扁平的，不能有太多的嵌套）
间隔胜于紧凑（优美的代码有适当的间隔，不要奢望一行代码解决问题）
可读性很重要（优美的代码是可读的）
即便假借特例的实用性之名，也不可违背这些规则（这些规则至高无上）
不要包容所有错误，除非你确定需要这样做（精准地捕获异常，不写 except:pass 风格的代码）
当存在多种可能，不要尝试去猜测
而是尽量找一种，最好是唯一一种明显的解决方案（如果不确定，就用穷举法）
虽然这并不容易，因为你不是 Python 之父（这里的 Dutch 是指 Guido ）
做也许好过不做，但不假思索就动手还不如不做（动手之前要细思量）
如果你无法向人描述你的方案，那肯定不是一个好方案；反之亦然（方案测评标准）
命名空间是一种绝妙的理念，我们应当多加利用（倡导与号召）

```

优秀的程序员总是能够使用更少的代码来做更多的事情，而学好Tim Peters给你的建议是你成为Python高手的第一步

# 如何写注释

## 注释的作用

注释的主要目的是阐述代码功能，要做什么以及如何做。一个专业的程序员总是会有写注释的习惯，注释能将复杂难懂的代码转换成自然语言，可以让你或者合作伙伴快速的阅读程序。这对开源项目以及公司多人协作项目的发展有着重要意义

## 哪里该写注释

思考在你解决问题前是否想了多种解决办法，如果是肯定的那就应该编写注释进行说明

## 如何编写注释

在你要描述的内容前加‘#’。Python会忽略井号（#）之后的内容

```
#输出Hello World
print('Hello World')
```

