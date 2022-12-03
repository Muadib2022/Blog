---
title: Python列表简介以及使用
date: 2018-11-15 11:11:37
summary: Python列表简介以及使用
tags: 
- list
categories: 
- Python
---

# **Python基础:Python列表简介以及使用**

## 列表简介

### 基本介绍

- 有一系列按特定顺序排列的元素组成
- 用方括号（[ ]）来表示列表，并用逗号（ , ）来分割其中的元素
- 你可以将任何东西加入列表，其中元素之间可以没有任何关系
- 命名：习惯给列表指定一个复数名称，如posts、lists、names等，而元素则常被指定一个列表名称的单数作为名称，如post、list、name.

### 创建一个列表

```
In [2]: stars = ['Mars','Earth', 'Moon', 'Mercury', 'Jupiter']  
In [3]: print(stars)                                                            
['Mars', 'Earth', 'Moon', 'Mercury', 'Jupiter']
```

### 访问列表元素

```
In [6]: stars = ['Mars','Earth', 'Moon', 'Mercury', 'Jupiter']                  
In [7]: print(stars[0])                                                         
Mars
```

*从中可以看出列表索引是从0开始的。*

### 逆向访问列表元素

```
In [8]: stars = ['Mars','Earth', 'Moon', 'Mercury', 'Jupiter']                  
In [9]: print(stars[-1])                                                        
Jupiter
In [10]: print(stars[-3])                                                       
Moon
```

### 修改列表元素

```
In [11]: stars = ['Mars','Earth', 'Moon', 'Mercury', 'Jupiter']                 
In [12]: stars[0] = 'Sun'                                                       
In [13]: print(stars[0])                                                        
Sun
In [14]: print(stars)                                                           
['Sun', 'Earth', 'Moon', 'Mercury', 'Jupiter']
```

### 在列表末尾添加元素 append（）

```
In [17]: stars = ['Mars','Earth', 'Moon', 'Mercury', 'Jupiter']                 
In [18]: stars.append('Sun')                                                    
In [19]: print(stars)                                                           
['Mars', 'Earth', 'Moon', 'Mercury', 'Jupiter', 'Sun']
```

### 在列表中插入元素 insert（）

```
In [20]: stars = ['Mars','Earth', 'Moon', 'Mercury', 'Jupiter']                 
In [21]: stars.insert(2, 'Sun')                                                 
In [22]: print(stars)                                                           
['Mars', 'Earth', 'Sun', 'Moon', 'Mercury', 'Jupiter']
```

### 从列表中删除指定位置元素 del（）

```
In [23]: stars = ['Mars','Earth', 'Moon', 'Mercury', 'Jupiter']                 
In [24]: del stars[1]                                                           
In [25]: print(stars)                                                           
['Mars', 'Moon', 'Mercury', 'Jupiter']
```

### 从列表中删除指定元素remove（）

```
In [26]: stars = ['Mars','Earth', 'Moon', 'Mercury', 'Jupiter']                 
In [27]: stars.remove('Mars')                                                   
In [28]: print(stars)                                                           
['Earth', 'Moon', 'Mercury', 'Jupiter']
```

*方法remove()只删除第一个指定的值，如果要删除的值在列表中出现多次，需要用循环来判断是否删除了所有这样的值*

### 对列表进行排序

#### *按字母顺序永久性排序sort()*

```
In [29]: stars = ['Mars','Earth', 'Moon', 'Mercury', 'Jupiter']                 
In [30]: stars.sort()                                                           
In [31]: print(stars)                                                           
['Earth', 'Jupiter', 'Mars', 'Mercury', 'Moon']
```

#### *按与字母顺序相反的循序永久性排序sorted()*

```
In [32]: stars = ['Mars','Earth', 'Moon', 'Mercury', 'Jupiter']                 
In [33]: stars.sort(reverse=True)                                               
In [34]: print(stars)                                                           
['Moon', 'Mercury', 'Mars', 'Jupiter', 'Earth']
```

sorted()可进行临时性排序，使用方法与sort()相同，但是排序后的新列表只能使用一次。

#### 按相反顺序永久性排列列表元素

```
In [37]: stars = ['Mars','Earth', 'Moon', 'Mercury', 'Jupiter']                 
In [38]: stars.reverse()                                                        
In [39]: print(stars)                                                           
['Jupiter', 'Mercury', 'Moon', 'Earth', 'Mars']
```

#### *确定列表程长度*

```
In [42]: stars = ['Mars','Earth', 'Moon', 'Mercury', 'Jupiter']                 
In [43]: len(stars)                                                             
Out[43]: 5
```

## 操作列表

### 遍历一个列表

```
In [4]: for star in stars: 
   ...:     print(star) 
   ...:                                                                         
Mars
Earth
Moon
Mercury
Jupiter
```

*使用复数（列表）-单数（元素）名称有助于你分辨哪个是列表，哪个是元素*

*Python的严格缩进机制不要忘记，避免代码因为缩进出错*

### 使用函数range()

```
In [45]: for i in range(1,5): 
    ...:     print(i) 
    ...:                                                                        
1
2
3
4
```

*特点:range(x,y)会生成一个x到y-1的列表*

### 使用range()创建一个列表

```
In [49]: numbers = list(range(1, 5))                                            
In [50]: print(numbers)                                                         
[1, 2, 3, 4]
```

### 对数字列表的简单统计

```
In [52]: numbers = [12, 3, 34, 25, 11, 14]                                      

In [53]: max(numbers)   #求最大值                                                        
Out[53]: 34

In [54]: min(numbers)   #求最小值                                                      
Out[54]: 3

In [55]: sum(numbers)   #求和                                                       
Out[55]: 99
```

### 精简for循环-列表解析

```
In [56]: numbers = [value**2 for value in range(1,10)]                          

In [57]: print(numbers)                                                         
[1, 4, 9, 16, 25, 36, 49, 64, 81]
```

### 列表的切片

*要创建切片，可指定所使用的第一个元素和最后一个元素的索引*

```
In [4]: stars = ['Mars','Earth', 'Moon', 'Mercury', 'Jupiter']                    

In [5]: print(stars[0:3])                                                         
['Mars', 'Earth', 'Moon']
```

提取列表中任意的子集

```
In [6]: stars = ['Mars','Earth', 'Moon', 'Mercury', 'Jupiter']                    

In [7]: print(stars[2:4])                                                         
['Moon', 'Mercury']
```

若没有指定第一个索引，将从头开始

```
In [8]: stars = ['Mars','Earth', 'Moon', 'Mercury', 'Jupiter']                    

In [9]: print(stars[:4])                                                          
['Mars', 'Earth', 'Moon', 'Mercury']
```

若没有指定最后一个元素，将在结尾处结束循环

```
In [10]: stars = ['Mars','Earth', 'Moon', 'Mercury', 'Jupiter']                   

In [11]: print(stars[3:])                                                         
['Mercury', 'Jupiter']
```

输出最后三个元素

```
In [12]: stars = ['Mars','Earth', 'Moon', 'Mercury', 'Jupiter']                   

In [13]: print(stars[-3:])                                                        
['Moon', 'Mercury', 'Jupiter']
```

复制列表（非赋值）

```
In [14]: stars = ['Mars','Earth', 'Moon', 'Mercury', 'Jupiter']                   

In [15]: planets = stars[:]                                                       

In [16]: solars = stars                                                           
#输出添加元素后的stars[]
In [17]: print(stars)                                                             
['Mars', 'Earth', 'Moon', 'Mercury', 'Jupiter']
#给stars[]添加元素
In [18]: stars.append('Sun')   

#输出添加元素后的planets[]
In [19]: print(planets)                                                           
['Mars', 'Earth', 'Moon', 'Mercury', 'Jupiter']

#输出添加元素后的solars[]
In [20]: print(solars)                                                            
['Mars', 'Earth', 'Moon', 'Mercury', 'Jupiter', 'Sun']

#输出添加元素后的stars[]
In [21]: print(stars)                                                             
['Mars', 'Earth', 'Moon', 'Mercury', 'Jupiter', 'Sun']
```

*观察以上代码可以发现，复制列表与将列表赋值给另一个变量是不同的。*

*planets = stars[:]是将starts[ ]内容复制了一份并赋予变量名planets*

*solars = stars 则是简单的让solars这个变量指向了stars[]列表的存储地址*

## 元组

Python将不能修改的值成为*不可变的*，而不变的列表被称为*元组*

元组与列表十分相似，但是使用圆括号而不是方括号标识，因为其内的数据不可以被修改，经常被用于存储程序中不可被修改的值。

### 定义元组

```
In [23]: stars =('Mars','Earth', 'Moon', 'Mercury', 'Jupiter')                    

In [24]: print(stars)                                                             
('Mars', 'Earth', 'Moon', 'Mercury', 'Jupiter')
```

### 尝试修改元组

```
In [26]: stars[0] = 'Sun'                                                         
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
<ipython-input-26-1b8422aaebe9> in <module>
----> 1 stars[0] = 'Sun'

TypeError: 'tuple' object does not support item assignment
```

可见程序报错‘TypeError: 'tuple' object does not support item assignment’

错误类型：tuple对象不支持项目分配

------

*参考书籍：Python编程从入门到实践*
