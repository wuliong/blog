---
layout: post
title: "Install Python on CentOS"
date: 2018-06-09 08:11:00 +0800
summary: install python on centos
slug: install-python-on-centos
categories: python
---
_Problem_

You want to install python 3.x without breaking the system's python 2.6 or 2.7

_Solution_

update the system 
```bash
yum -y update
yum groupinstall -y development 
yum install -y zlib-dev openssl-devel sqlite-devel bzip2-devel  
```

download the python release of your choice
```bash
cd /tmp
wget https://www.python.org/ftp/python/x.y.z/Python-x.y.z.tgz  
tar xzf Python-x.y.z.tgz  
cd Python-x.y.z
```

install 
```bash
./configure --enable-optimizations \
            --with-ensurepip=install \
            --enable-shared \
            --prefix=/opt/pythonxyz \
            LDFLAGS="-Wl,--rpath=/opt/pythonxyz/lib"   
make -j 8  
make install
```
