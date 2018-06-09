---
layout: post
title: "One Liners"
date: 2018-06-09 08:53:00 +0800
summary: one-liner program
slug: one-liners-program
categories: programming
---
Many tasks can be easily accomplished by one line of program.

Convert HEX code to Base64
```bash
echo '4B5CC4' | xxd -r -p | base64
```

Get list of actors of a movie using Douban.com and browser console.
```console
jQuery.map(jQuery("a[rel='v:starring']"),function(x){return x.text;}).join(',')
```

Convert image to Base64 code
```bash
base64 input.png > output.txt
```

Get ip address of the server you just logged in 
```bash
/sbin/ifconfig|grep inet|head -1|sed 's/\:/ /'|awk '{print $3}'
```

Convert milliseconds to nice datetime string using browser console
```javascript
(function(x){var date = new Date(x); return date.toString();})(1506300029207)
```

Print a single string multiple times at the command line
```bash
printf "%0.stest\n" {1..10}
printf '%0.stest\n' 1 2 3 4 5
printf '%0.stest\n' $(seq 1 5)
```

To download multiple files, put urls in a single file named `download.txt`, then type following at the command line
```bash
wget -i download.txt 
```

Change timezone in Linux
```bash 
cp -f /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
```
