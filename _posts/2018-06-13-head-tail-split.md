---
layout: post
title: "Introducing head, tail & split"
date: 2018-06-13 20:11:00 +0800
summary: introducing linux commands, head, tail and split
slug: intro-head-tail-split
categories: linux
---

There are three linux commands that display or print part(s) of a file: `head` output the first part of file, `tail` output the last part of file, and `split` splits file into pieces.

```bash
head -n K FILENAME # print first K lines
head -n -K FILENAME # print all but the last K lines
tail -n K FILENAME # print last K lines
tail -n +K FILENAME # print all starting with the Kth line
tail -n +2 FILENAME | head -n -1 # print 2nd to (N-1)th line
```

`split` creates output files containing consecutive sections of _input file_, use the optional argument `prefix` to specify the beginning part of output filenames, by default, `prefix` will be `x`.
```bash
split -l K FILENAME [prefix] # put K lines in each output file
split -n K FILENAME [prefix] # generate K files, it may split lines
split -n l/K FILENAME [prefix] # generate K files without splitting lines
split -n l/P/K FILENAME [prefix] # likewise but output pth of K to stdout
```
examples,
```bash
split -l 10 test.txt OUT_
split -n 5 test.txt OUT_ 
split -n l/5 test.txt OUT_
split -n l/3/5 test.txt OUT_ # split into 5 pieces and output 3rd to stdout
```

The _suffix_ of output files will be 'aa', 'ab', 'ac', etc. To use digits in suffixes,
```bash 
split -l K FILENAME [prefix] -d # use 00, 01, 02 ...
split -l K FILENAME [prefix] --numeric-suffixes=F # use digits starting with F
```

for example, the output of `split -n 3 test.txt --numeric-suffixes=13` are
```console
x13  x14  x15
```




