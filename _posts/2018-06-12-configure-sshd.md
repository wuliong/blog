---
layout: post
title: "Configure OpenSSH Server"
date: 2018-06-12 20:24:00 +0800
summary: configure openssh server
slug: configure-openssh-sever
categories: linux
---

There are many ways to make your linux server as secure as possible. The first step is to change the SSH port to something other than the default value of 22. You need to log into the server first, then add a new port number in the configure file at `/etc/ssh/sshd_config`
```config
Port 22 # keep this line
Port NEW_PORT_NUMBER # add a new port
```

restart the server and check if SSH listen on the `NEW_PORT_NUMBER`
```bash
service sshd restart
netstat -tnlp
```

reopen the configure file and remove the line that says `Port 22`. Scroll down the file, uncomment this line, then restart the server
```config
PasswordAuthentication no
```
Next time you log in, you will not be asked for a password. 