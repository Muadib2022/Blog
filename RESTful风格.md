---
title: 如何设计出RESTful风格
date: 2019-02-06 12:08:59
author: chen
categories: others
tags:
- restful
---

## 什么是 RESTFUL?

- Representational State Transfer
- HTTP协议（1.0版和1.1版）的主要设计者Roy Thomas Fielding提出
- 资源（Resources）,表现层（Representation）,状态转化（State Transfer）

## RESTFUL解释

- 资源（Resources）：使用URL指向一个实体
- 表现层（Representation）：资源的表现形式，比如图片，HTML文本等
- 状态转化（State Transfer）：GET，POST，PUT，DELETE HTTP动词来操作资源

## 幂等性操作

- GET/PUT/DELETE都是幂等操作，而POST是非幂等操作
- 幂等指的是无论一次还是多次操作具有一样的副作用

## Tornado RESTful API示例

| HTTP方法 | URL                                   | 动作         |
| -------- | ------------------------------------- | ------------ |
| GET      | http://[hostname]/api/users           | 检索用户列表 |
| GET      | http://[hostname]/api/users/[user_id] | 检索单个用户 |
| POST     | http://[hostname]/api/users           | 创建新用户   |
| PUT      | http://[hostname]/api/users/[user_id] | 更新用户信息 |
| DELETE   | http://[hostname]/api/users/[user_id] | 删除用户     |

