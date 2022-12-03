---
title: MySQL数据库基本语法
top: true
summary: 认识MySQL基本语法，防止从删库到跑路
date: 2019-02-13 10:25:16
author: Topu
categories: 
- 数据库
tags: 
- MySQL语法
---

# MySQL数据库基本语法

1. 创建数据库

```mysql
CREATE　DATABASES `student`;
```

2. 查看已有数据库

```mysql
SHOW DATABASES;				#查看已有数据库
SHOW TABLES;				#查看数据库内的数据表
```

3. 使用数据库

```mysql
USE `student`;
```

4. 创建新表

```mysql
CREATE TABLE `student`(
    `id` INT NOT NULL AUTO_INCREMENT PRIMARY KEY,,    #数据类型 int; 不为空 NOT NULL; 
    #PRIMARY KEY 设置为主键
    `name` VARCHAR(200) NOT NULL         #数据类型 varchar; 不为空
    `nickname` VARCHAR(20) NULL,
    `sex` CHAR(1) NULL,	
    `int_time` DATETIME NULL
);
```

5. 将数据插入新表

```MYSQL
INSERT INTO `student` VALUE(
	1, 'topu', 'dreamer', '男', now()
);			#插入单行数据
```

```mysql
INSERT INTO `student` ('name', 'nickname', 'sex', 'in_time') VALUE(
	'Neox', 'internet', '男', now()
);			#插入单行数据，ID自增长。需要一一对应，在默认可以为空时可以为空。
```

```mysql
INSERT INTO `student` VALUE(
	1, 'topu', 'dreamer', '男', now()，
	2, 'Neox', 'internet', '男', now()
);			#插入多行语句
```

6. 查询数据

```mysql
SELECT * from `student`;			#查询‘student’表内所有数据
```

```mysql
SELECT `name`, `nickname` from `student`;			#查询指定的数据
```

```mysql
SELECT `name`, `nickname` from `student` WHERE `sex`='男';		  #查询男生的指定数据
```

```mysql
SELECT `name`, `nickname` from `student` WHERE `sex`='男' ORDER BY `id` DESC;
#以id为准倒序排列，ASC是默认排序，DESC是倒序排列
```

```MYSQL
SELECT `name`, `nickname` from `student` WHERE `sex`='男' ORDER BY `id` DESC LIMIT 0, 2;
#翻页查询
```

7. 修改数据

```mysql
UPDATE `student` SET `name`='辰宇' WHERE `name`='Neox';	
UPDATE `student` SET `name`='梦宇' WHERE `id`='2';
#将name Neox 更改为 辰宇。 SET后是更改后内容， WHERE后边定位要更改的位置
```

```mysql
UPDATE `student` SET `sex`='男' WHERE `id`> 3;
#修改id>3之后的所有性别为男
```

8. 删除数据

```mysql
DELETE FROM `student` WHERE `sex`='男';			#删除所有性别为男的数据
```

```mysql
DELETE FROM `student`;			#若忘记加上限制条件，本语句将删除student表中的所有数据
```

注：在编写数据库语言时，对于敏感操作一定要注意。像7和8的数据操作如果不加限制条件或者加错了限制条件，会造成不可挽回的损失。所以一定要小心认真，防止职业生涯变成数据库之从删库到跑路的一个剪影。