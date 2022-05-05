# Mybatis学习

## 面试常问

```mysql
ENGINE=INNODB DEFAULT
```

## SQL代码

```mysql
CREATE DATABASE mybatis;

USE mybatis;

CREATE TABLE `User`(
	`id` INT(20) NOT NULL primary key,
	`name` varchar(30) default null,
	`pwd` varchar(30) default null
)ENGINE=INNODB DEFAULT CHARSET=utf8;
```

