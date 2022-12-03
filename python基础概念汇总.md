---
title: Python变量命名规则与简单数据类型
date: 2018-11-07 12:39:01
summary: Python的变量命名规则与简单数据类型
tags:
- Python
categories: 
- Python
---

# Python基础:变量命名规则与简单数据类型

## 变量名的命名规则：

- 变量名只能包含字母、数字、下划线。可以以字母、下划线打头，不能以数字打头。
- 变量名不能包含空格，可以用下划线分割单词。
- 不可以将Python关键字和函数名（即其中特殊用途的单词）当作变量名。
- 变量名应具有简短与可描述性的特质。
- 少用小写字母i和大写字母O，因为它们容易被混淆。

## 字符串：

字符串就是一系列的字符，在Python中用引号括起来的都是字符串，引号可以是单引号，也可以是双引号。

title(): 可以使一段字符串的首字母变为大写。

upper(): 可以使字符串全部字母变成大写。

lower(): 可以使字符串全部字母变成小写。

拼接字符串：

```
<<<name1 = 'zhang'+'san'

<<<'zhangsan'
```

------

```
<<<firstname = 'san'

<<<lastname = 'zhang'

<<<name2 = firstname + lastname

<<name2

sanzhang
```

------

```
<<<name3 = lastname + 'san'

<<<name3

'zhangsan'
```

------

**制表符与换行符：***\t 制表符可缩进三个字符的长度。\n换行符换行到下一行。*

rstrip() 能够暂时性的删除字符串尾部的空格

lstrip() 能够暂时性的删除字符串首部的空格

strip() 能够暂时性的删除字符串首尾两端的空格

## 数字

## 整数

### 加减乘除：

![](https://personal-blog-1253377966.cos.ap-beijing.myqcloud.com/Python%E5%9F%BA%E7%A1%80/%E9%80%89%E5%8C%BA_006.png)

### 乘方：

​            ![](https://personal-blog-1253377966.cos.ap-beijing.myqcloud.com/Python%E5%9F%BA%E7%A1%80/%E9%80%89%E5%8C%BA_007.png)

### 运算次序：

![](https://personal-blog-1253377966.cos.ap-beijing.myqcloud.com/Python%E5%9F%BA%E7%A1%80/%E9%80%89%E5%8C%BA_008.png)

## 浮点数

![](https://personal-blog-1253377966.cos.ap-beijing.myqcloud.com/Python%E5%9F%BA%E7%A1%80/%E9%80%89%E5%8C%BA_009.png)

因为计算机内部表达数字的方式，部分计算结果的小数位具有不确定性。（所有语言都存在这种问题，几乎无影响可忽略）

![](https://personal-blog-1253377966.cos.ap-beijing.myqcloud.com/Python%E5%9F%BA%E7%A1%80/%E9%80%89%E5%8C%BA_010.png)

### str()函数避免类型错误

在Python中，字符串与数字拼接时，你要将数值转换成字符串。否则Python将会不知该如何解读这个值。

例如‘23’看做数值就是23，但是看做字符串就是2和3。

#### 错误示例

![](https://personal-blog-1253377966.cos.ap-beijing.myqcloud.com/Python%E5%9F%BA%E7%A1%80/%E9%80%89%E5%8C%BA_011.png)

#### 正确示例

![](https://personal-blog-1253377966.cos.ap-beijing.myqcloud.com/Python%E5%9F%BA%E7%A1%80/%E9%80%89%E5%8C%BA_012.png)

#### 整数的取整与取余

![](https://personal-blog-1253377966.cos.ap-beijing.myqcloud.com/Python%E5%9F%BA%E7%A1%80/%E9%80%89%E5%8C%BA_013.png)

