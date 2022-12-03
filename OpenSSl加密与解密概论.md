---
title: OpenSSl加密与解密概论
img: /source/images/xxx.jpg
top: true
password: 8d969eef6ecad3c29a3a629280e686cf0c3f5d5a86aff3ca12020c923adc6c92
mathjax: True
summary: 这是你自定义的文章摘要内容，如果这个属性有值，文章卡片摘要就显示这段文字，否则程序会自动截取文章的部分内容作为摘要
date: 2019-02-24 11:00:09
author: Topu
categories: 安全
tags: 
- openssl
---

*数据的加密就是将原始有异议的数据转化成无意义的数据。对于对称加密算法，加密和解密采用同一个密钥，大多采用替换、置换和移位等技术对原始数据进行变换。OpenSSl 实现了现代密码学的常见的密码算法，主要有DES、3DES、AES、RC2、RC4等。*

## 函数介绍

在OpenSSl加密和解密开发中：

加密函数：EVP_EncryptInit_ex、EVP_EncryptUpdate、EVP_EncryptFinal_ex

解密函数：EVP_DecryptInit_ex、EVP_DecryptUpdate、EVP_DecryptFinal_ex

所有函数均定义在evp.h中

### 初始化函数 EVP_CHPHER_CTX_init

**函数功能**：初始化一个EVP_CHPHER_CTX的结构体。只有调用该函数初始化后，EVP_CHPHER_CTX结构体才能在其他函数中调用。

**函数定义**：

```c
void EVP_CIPHER_CTX_init(EVP_CIPHER_CTX *a)
```

**参数说明**：a : EVP_CIPHER_CTX结构体，密码算法上下文关系句柄。用于保存密码算法、密码算法引擎、加密或解密的标志位、初始初始化向量、当前初始化向量等信息。

**返回值**：无

### 加密初始化函数 EVP_EncryptInit_ex

**函数功能**：加密初始化、设置密码算法、加密引擎、密钥、初始化向量等参数。

**函数定义**：

**参数说明**：

**返回值**：

### 数据加密Update 函数 EVP_EncryptUpdate

**函数功能**：数据加密

**函数定义**：

**参数说明**：

**返回值**：

### 数据加密结束函数 EVP_EncryptFinal_ex

**函数功能**：数据加密结束，输出最后剩余的密文

**函数定义**：

**参数说明**：

**返回值**：

### 解密初始化函数 EVP_DecryptInit_ex

**函数功能**：解密初始化、设置密码算法、加密引擎、密钥、初始化向量等参数

**函数定义**：

**参数说明**：

**返回值**：

### 函数解密Update 函数 EVP_DecryptUpdate

**函数功能**：数据解密

**函数定义**：

**参数说明**：

**返回值**：

### 函数解密结束函数 EVP_DecryptFinal_ex

**函数功能**：数据解密结束，输出最后剩余的原文

**函数定义**：

**参数说明**：

**返回值**：

