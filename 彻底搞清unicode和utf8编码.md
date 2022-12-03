---
title: 彻底搞清unicode和utf8编码
top: false
summary: 从编码发展历程彻底搞清unicode和utf8编码
date: 2019-02-06 12:08:59
author: Topu
categories: Python
tags:
- 编码
---

字符串编码

## 编码发展历程

1. 计算机只能处理数字，文本转换为数字才能处理。计算机中8个bit作一个字节，所以一个字节能表示的最大数字就是255.

2. 计算机是美国人发明的。所以一个字节可以表示他们所有的字符，所以ASCII(一个字节)编码就成为了美国人的标准编码。

3. 但是ASCII处理中文明显是不够的。中文不止255个汉字，所以中国制定了GB2312编码，用两个字节便是一个汉字。GB2312还把ASCII包含进去了。同理，日文韩文也是如此。但是标准越来越多时，当出现多种语言混合显示的情况时就一定会出现乱码。

4. 于是unicode出现了，它将所有语言统一到了一套编码里。

5. 乱码问题虽然解决了，但是如果内容全是英文，unicode编码比ASCII需要多一倍的存储空间，同时如果传输的话，也需要多一倍的传输

6. 所以出现了可变长的编码“utf-8”， 把英文变长一个字节，汉字三个字节。特别生僻的编程4-6个字节，如果传输大量的英文，utf-8的作用就很明显了。

7. ASCII和unicode编码对比

   |              | ASCII编码               | unicode编码                  | 二进制             |
   | ------------ | ----------------------- | ---------------------------- | ------------------ |
   | 字母A        | 65                      |                              | 0100 0001          |
   | 汉字’中‘     | 已经超出ASCII编码的范围 | 20013                        | 01001110 00101101  |
   | A使用unicode |                         | 使用unicode编码只需要前面补0 | 00000000 0100 0001 |

## 编码转换

python3中默认编码为utf-8

```python
>>> x = "我用Python"
>>> x.encode("utf-8")
b'\xe6\x88\x91\xe7\x94\xa8Python'
>>> 
```

```python
>>> import sys
>>> sys.getdefaultencoding()
'utf-8'
>>> 
```

python2中默认编码为ASCII

```python
>>> s = "我用Python"
>>> s.encode("utf8")
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
UnicodeDecodeError: 'ascii' codec can't decode byte 0xe5 in position 0: ordinal not in range(128)
>>> 
```

```python
>>> import sys
>>> sys.getdefaultencoding()
'ascii'
>>> 
```

编码问题是Python2与Python3之间最大的区别，理解好编码问题对真正掌握Python有着至关重要的作用。