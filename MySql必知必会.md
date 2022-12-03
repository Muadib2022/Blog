---
title: MySQL数据库基本语法
date: 2019-02-13 10:25:16
author: chen
categories: 
- mysql
tags: 
- mysql

---

## 数据库

#### 查看数据库

```mysql
SHOW DATABASES;
```

#### 创建数据库

```mysql
CREATE DATABASE "DATABASE_NAME";
```

#### 删除数据库

```mysql
drop database DATABASE_NAME;
```

#### 选择数据库

```mysql
USE DATABASE_NAME;
```

## 数据表

#### 查看表

```mysql
SHOW TABLES;
```

#### 创建表

```mysql
CREATE TABLE table_name (column_name column_type);
```

```mysql
CREATE TABLE IF NOT EXISTS `runoob_tbl`(
   `runoob_id` INT UNSIGNED AUTO_INCREMENT,
   `runoob_title` VARCHAR(100) NOT NULL,
   `runoob_author` VARCHAR(40) NOT NULL,
   `submission_date` DATE,
   PRIMARY KEY ( `runoob_id` )
)ENGINE=InnoDB DEFAULT CHARSET=utf8;
```

实例解析：

- 如果你不想字段为 **NULL** 可以设置字段的属性为 **NOT NULL**， 在操作数据库时如果输入该字段的数据为**NULL** ，就会报错。
- AUTO_INCREMENT定义列为自增的属性，一般用于主键，数值会自动加1。
- PRIMARY KEY关键字用于定义列为主键。 您可以使用多列来定义主键，列间以逗号分隔。
- ENGINE 设置存储引擎，CHARSET 设置编码。

#### 删除表

```mysql
drop table table_name;
```

#### 插入数据

```mysql
INSERT INTO table_name ( field1, field2,...fieldN )
                       VALUES
                       ( value1, value2,...valueN );
```

```mysql
mysql> INSERT INTO table_name 
    -> (table_title, table_author, submission_date)
    -> VALUES
    -> ("龙族", "江南", NOW());
```

#### 查询数据

```mysql
SELECT column_name,column_name
FROM table_name
[WHERE Clause]
[LIMIT N][ OFFSET M];
```

#### 查看整张表

```mysql
SELECT * FROM table_name
```

## 查表WHERE子句

```mysql
SELECT field1, field2,...fieldN FROM table_name1, table_name2...
[WHERE condition1 [AND [OR]] condition2.....
```

- 查询语句中你可以使用一个或者多个表，表之间使用逗号**,** 分割，并使用WHERE语句来设定查询条件。
- 你可以在 WHERE 子句中指定任何条件。
- 你可以使用 AND 或者 OR 指定一个或多个条件。
- WHERE 子句也可以运用于 SQL 的 DELETE 或者 UPDATE 命令。
- WHERE 子句类似于程序语言中的 if 条件，根据 MySQL 表中的字段值来读取指定的数据。

#### 读取指定某项值的数据

```mysql
SELECT * from table_name WHERE table_author='suchen';
```

MySQL 的 WHERE 子句的字符串比较是不区分大小写的。 你可以使用 BINARY 关键字来设定 WHERE 子句的字符串比较是区分大小写的。

```mysql
SELECT * from table_name WHERE BINARY table_author='suchen';
```

## UPDATE更新

```mysql
UPDATE table_name SET field1=new-value1, field2=new-value2
[WHERE Clause]
```

- 你可以同时更新一个或多个字段。
- 你可以在 WHERE 子句中指定任何条件。
- 你可以在一个单独表中同时更新数据。

```mysql
UPDATE table_name SET table_title='龙族' WHERE runoob_id=3;
```

## DELETE删除

```mysql
DELETE FROM table_name [WHERE Clause]
```

- 如果没有指定 WHERE 子句，MySQL 表中的所有记录将被删除。
- 你可以在 WHERE 子句中指定任何条件
- 您可以在单个表中一次性删除记录。

按条件删除数据

```mysql
 DELETE FROM table_name WHERE table_id=3;
```

## LIKE 子句

SQL LIKE 子句中使用百分号 **%**字符来表示任意字符，类似于UNIX或正则表达式中的星号 *****。

如果没有使用百分号 **%**, LIKE 子句与等号 **=** 的效果是一样的。

```mysql
SELECT field1, field2,...fieldN 
FROM table_name
WHERE field1 LIKE condition1 [AND [OR]] filed2 = 'somevalue'
```

- 你可以在 WHERE 子句中指定任何条件。
- 你可以在 WHERE 子句中使用LIKE子句。
- 你可以使用LIKE子句代替等号 **=**。
- LIKE 通常与 **%** 一同使用，类似于一个元字符的搜索。
- 你可以使用 AND 或者 OR 指定一个或多个条件。
- 你可以在 DELETE 或 UPDATE 命令中使用 WHERE...LIKE 子句来指定条件。

```mysql
SELECT * from table_name  WHERE table_author LIKE '%chen';
```

## MySQL UNION 操作符

## MySQL排序

使用SELECT 查询　ORDER BY　排序

升序排序

```mysql
mysql> SELECT * from runoob_tbl ORDER BY submission_date ASC;
```

降序排序

```mysql
mysql> SELECT * from runoob_tbl ORDER BY submission_date DESC;
```

GROUP BY 语句根据一个或多个列对结果集进行分组。

在分组的列上我们可以使用 COUNT, SUM, AVG,等函数。

### GROUP BY 语法

```mysql
SELECT column_name, function(column_name)
FROM table_name
WHERE column_name operator value
GROUP BY column_name;
```

```mysql
mysql> select * from employee_tbl;
+----+--------+---------------------+--------+
| id | name   | date                | singin |
+----+--------+---------------------+--------+
|  1 | 小明   | 2016-04-22 15:25:33 |      1 |
|  2 | 小王   | 2016-04-20 15:25:47 |      3 |
|  3 | 小丽   | 2016-04-19 15:26:02 |      2 |
|  4 | 小王   | 2016-04-07 15:26:14 |      4 |
|  5 | 小明   | 2016-04-11 15:26:40 |      4 |
|  6 | 小明   | 2016-04-04 15:26:54 |      2 |
+----+--------+---------------------+--------+
6 rows in set (0.00 sec)

mysql> select name, COUNT(*) from employee_tbl GROUP BY name;
+--------+----------+
| name   | COUNT(*) |
+--------+----------+
| 小明   |        3 |
| 小王   |        2 |
| 小丽   |        1 |
+--------+----------+
3 rows in set (0.00 sec)
```

## MySQL正则表达式

```
MySQL 同样也支持其他正则表达式的匹配， 
```

```mysql
mysql> select * from runoob_tbl;
+-----------+--------------+---------------+-----------------+
| runoob_id | runoob_title | runoob_author | submission_date |
+-----------+--------------+---------------+-----------------+
|         1 | 学习python   | 菜鸟教程      | 2019-07-06      |
|         2 | rich         | suchen        | 2019-07-06      |
|         3 | 龙族         | 江南          | 2019-07-06      |
+-----------+--------------+---------------+-----------------+
3 rows in set (0.00 sec)

mysql> select runoob_title from runoob_tbl where name regexp 'python$';
ERROR 1054 (42S22): Unknown column 'name' in 'where clause'
mysql> select runoob_title from runoob_tbl where runoob_title regexp 'python$';
+--------------+
| runoob_title |
+--------------+
| 学习python   |
+--------------+
1 row in set (0.10 sec)
```

