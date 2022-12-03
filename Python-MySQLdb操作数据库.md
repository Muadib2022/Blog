---
title: Python-MySQLdb操作数据库
img: 
top: true
mathjax: true
summary: Python操作数据库来实现简单的增删改查
date: 2019-02-15 23:32:29
author: Topu
categories: 
- 数据库
tags:
- MySQLdb
---

## Python-MySQLdb操作数据库

使用Python不管是做任何事都无法逃过数据库，今天我们就来学习一下如何使用Python操作数据库来实现简单的增删改查的功能

直接上代码，代码中有详细的注释。

在程序设计中应该尽量将复杂操作封装至对象中。

1. 连接数据库

   ```python
   def get_conn(self):
           # 获取连接
           try:
               self.conn = MySQLdb.connect(
                   host="localhost",
                   port=3306,
                   user="root",
                   passwd="*",
                   db="news",
                   charset="utf8"
               )
           except MySQLdb.Error as e:
               print('Error: %s' % e)
   ```

2. 查询数据库

   ```python
    def get_one(self):
           # 获取数据
           # 准备SQL
           sql = 'SELECT * FROM `news` WHERE `types` = %s ORDER BY `created_at` DESC;'
           # 找到cursor
           cursor = self.conn.cursor()
           # 执行SQL
           cursor.execute(sql, ('互联网',))
           # 拿到结果
           rest = dict(zip([k[0] for k in cursor.description], cursor.fetchone()))
           print(rest)
           # 关闭cursor链接
           cursor.close()
           # 关闭数据库连接
           self.close_conn()
           return rest
   ```

3. 添加更改数据到数据库

   ```python
   def add_one(self):
           try:
               sql = ("INSERT INTO `news` (`title`, `content`, `types`, `image`, `author`) VALUES "
                      "(%s, %s, %s, %s, %s);"
                      )
               # 获取链接和cursor
               cursor = self.conn.cursor()
               # 执行sql
               # 提交数据到数据库
               cursor.execute(sql, ('互联网寒冬已经到临', 23, '互联网', '/image.jpg', '梦溪'))
               # 提交事务
               self.conn.commit()
               # 关闭cursor和链接
               cursor.close()
           except:
               print('Error')
               self.close_conn()
   ```

5. 全部代码（可直接运行）

   ```python
   
   import MySQLdb
   
   class MysqlSearch(object):
       def __init__(self):
           self.get_conn()
   """连接MySQL数据库"""
       def get_conn(self):
           # 获取连接
           try:
               self.conn = MySQLdb.connect(
                   host="localhost",
                   port=3306,
                   user="root",
                   passwd="*",
                   db="news",
                   charset="utf8"
               )
           except MySQLdb.Error as e:
               print('Error: %s' % e)
               
   #关闭数据库连接
       def close_conn(self):
           try:
               if self.conn:
                   self.conn.close()
           except MySQLdb.Error as e:
               print('Error: %s' % e)
               
   #查询指定数据
       def get_one(self):
           # 获取数据
           # 准备SQL
           sql = 'SELECT * FROM `news` WHERE `types` = %s ORDER BY `created_at` DESC;'
           # 找到cursor
           cursor = self.conn.cursor()
           # 执行SQL
           cursor.execute(sql, ('互联网',))
           # 拿到结果
           rest = dict(zip([k[0] for k in cursor.description], cursor.fetchone()))
           print(rest)
           # 关闭cursor链接
           cursor.close()
           # 关闭数据库连接
           self.close_conn()
           return rest
       
   #添加更改指定信息
       def add_one(self):
           try:
               sql = ("INSERT INTO `news` (`title`, `content`, `types`, `image`, `author`) VALUES "
                      "(%s, %s, %s, %s, %s);"
                      )
               # 获取链接和cursor
               cursor = self.conn.cursor()
               # 执行sql
               # 提交数据到数据库
               cursor.execute(sql, ('互联网寒冬已经到临', 23, '互联网', '/image.jpg', '梦溪'))
               # 提交事务
               self.conn.commit()
               # 关闭cursor和链接
               cursor.close()
           except:
               print('Error')
               self.close_conn()
               
   def main():
       obj = MysqlSearch()
       obj.get_one
       obj.add_one()
       obj.get_one
       
   if __name__ == '__main__':
       main()
   ```

   

