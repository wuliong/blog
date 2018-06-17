---
layout: post
title: "Print System Information: uname, hostname, uptime & etc."
date: 2018-06-17 13:02:00 +0800
summary: print system information
slug: print-system-information
categories: linux
---

To print machine architecture information
```bash
arch # machine hardware name
uname -m # machine hardware name
uname -p # processor type, Example: x86_64, i386
uname -i # hardware platform
```
about the operating system
```bash
nproc # number of processing units available
uname -o # name of the operating system, Example: GNU/Linux, Darwin
uname -n # network node hostname, Example: localhost
uname -r # kernel release, Example: 3.10.0-693.2.2.el7.x86_64
uname -s # kernel name, Example: Linux, Darwin
hostname # print the name of the current host system
hostname STRING # sets the current hostname to the specified string
hostid # numeric identifier of the current host in hexadecimal
```
since when and for how long has the sytem been up 
```bash
uptime -p # show the system's uptime in pretty format
uptime -s # show system up since, in yyyy-mm-dd HH:MM:SS format
uptime # current time, how long the system has been running, how many users 
       # are currently logged in, and the system load averages for the past 
       # 1, 5, and 15 minutes
```

to know how much disk space is available and how it has been used

```bash
df # disked space used on all currently mounted file systems
df -h # print sizes in human readable format
df --total # print a grand total at the end
```