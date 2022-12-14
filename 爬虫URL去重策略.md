---
title: 爬虫URL去重策略
top: false
summary: 五种爬虫URL去重策略带你轻松爬取数据
date: 2019-02-06 11:01:09
author: Topu
categories: 爬虫
tags: URL去重
---

# 爬虫去重策略

> 爬虫为何要进行去重：
>
> - 如果不去重容易陷入爬取死循环
> - 浪费资源、重复爬取效率低下

## 以100000000条数据为例子、对比各个去重方式的效率。

### 1.将访问过的URL保存到数据库

特点：应用简单、效率非常低下

使用方法： 

- ​    将URL存储至数据库中
- ​     获取新URL时，查询数据库检查是否与既有URL重复

效率：效率十分低下，并使用很少。不进行计算

### 2.将访问过的URL保存到set中

特点：速度较快、内存占用会越来越大

效率：100000000×2byte×50个字符/1024/1024/1024 = 9G

### 3.URL经过md5等方法哈希后保存到set中

特点：md5能将任意长度字符串压缩成固定长度md5字符串，并且不会重复。

效率：能够成倍的压缩字符串，大约只需要两三G的内存

### 4.用bitmap方法，将访问过的URL通过hash函数映射到某一位

特点：十分节省内存，容易出现映射冲突

使用方法：

一个Byte有八个位，将访问过的URL通过hash函数映射到某一位，但是容易将两个URL映射到同一个位上。

效率：对内存压缩十分显著，100000000/8/1024/1024/1024 = 11.920  大约十二M的内存占用。

### 5.bloomfilter方法对bitmap进行改进，多重hash函数降低冲突

特点：通过多个hash函数减少冲突可能性