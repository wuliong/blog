---
layout: post
title: "Reset MySQL password"
date: 2018-06-07 21:28:00 +0800
summary: reset password of root account in mysql
slug: reset-mysql-password
categories: mysql
---

*Problem*

MySQL on the server was installed long time ago and you forgot the password of root account.

*Solution*

stop mysql server, then restart it with the skip-grant-tables option

```bash
/etc/init.d/mysqld stop
/usr/bin/mysqld_safe --skip-grant-tables &
/usr/bin/mysql -u root
```

reset the password
```sql
mysql> use mysql;
mysql> update user set authentication_string=PASSWORD("123") where User='root';
mysql> flush privileges;
mysql> quit;
```

start mysql again
```bash
/etc/init.d/mysqld start
/usr/bin/mysql -u root -p
```
