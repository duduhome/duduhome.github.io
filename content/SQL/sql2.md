---
title: "Linux mySQL"
layout: page
date: 2099-06-02 00:00
---
[TOC]

#终端进入mysql
    mysql -u root -p password

#mysql的操作

* 显示数据库列表

```javascript
    show databases
```

* 打开数据库

```javascript
    user database
```

* 显示数据库中的表

```javascript
    show tables
```

* 查看表结构

```javascript
    desc table_name
```

#本地mysql

##忘记密码

* 关闭mysql

* 进入mysql目录

```javascript
cd /usr/local/mysql/bin
```

* 获取权限

```javascript
sudo su
```

* 开启安全模式

```javascript
./mysqld_safe --skip-grant-tables &
```
