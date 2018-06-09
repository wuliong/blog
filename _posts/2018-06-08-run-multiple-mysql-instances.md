---
layout: post
title: "Run multiple MySQL instances on one machine"
date: 2018-06-08 19:00:00 +0800
summary: run multiple mysql instances on one machine
slug: run-multiple-mysql-instances
categories: mysql
---

_Problem_

You want to run multiple instances of MySQL on a single machine and give different users access to different mysqld servers.

_Solution_

Create a directory for the new MySQL instance, initialize the datadir with initialize-insecure option so that it won't generate a random password for root, and change the ownership.

```bash
mkdir -p /var/lib/mysql2/data
mysqld --initialize-insecure --user=mysql --datadir=/var/lib/mysql2/data
chown -R mysql:mysql /var/lib/mysql2
```

edit /etc/my.cnf and add the following

```conf
[mysqld_multi]
mysqld     = /usr/bin/mysqld_safe
mysqladmin = /usr/bin/mysqladmin
user       = multi_admin
password   = multi_pwd

[mysqld2]
datadir     = /var/lib/mysql2/data
port        = 1234
server_id   = 2
socket      = /tmp/mysql2.sock
pid-file    = /var/run/mysqld/mysqld2.pid
log-error   = /var/log/mysqld2.log
user        = mysql
```

check if the new instance has been added, start it, and log into this instance without password.
```bash
mysqld_multi report
mysqld_multi start 2
mysql --socket=/tmp/mysql2.sock -u root
```

reset the root password
```sql
mysql> use mysql;
mysql> alter user 'root'@'localhost' identified by 'new_root_pwd';
mysql> quit;
```
grant the permission to shutdown mysql instances
```sql
mysql> use mysql;
mysql> grant shutdown on *.* to 'multi_admin'@'localhost' identified by 'multi_pwd';
mysql> flush privileges;
mysql> quit;
```

shutdown the new instance
```bash
mysqld_multi report
mysqld_multi stop 2
```

if mysqld_multi cannot stop the instance, use mysqladmin instead
```bash
mysqladmin -h127.0.0.1 -P1234 -uroot -p shutdown
mysqladmin -h127.0.0.1 -P1234 -uroot -p ping
```