---
layout: post
title: "Simple File Manipulation: truncate, wc, sort, uniq & etc."
date: 2018-06-18 10:22:00 +0800
summary: simple file manipulation
slug: simple-file-manipulation
categories: linux
---

Shrink the size of a file 
```bash
# Reduce the size of file to zero. Any file that does not exist is created
truncate --size=0 FILE 
truncate --size=0 -c FILE # Do not create file if it doesn't exist
```

Count the number of characters, whitespace-separated words and newlines in given file
```bash
wc -m FILE # byte counts
wc -w FILE # word counts
wc -l FILE # newline counts
```

Use `cut` to print selected fields of a delimited file.
```bash
cut -d: -f1,5 /etc/passwd # use : as field delimiter, cut out fields 1 and 5
# use STRING as the output delimiter, default is to use the input delimiter
cut -d: -f1,5 /etc/passwd --output-delimiter=STRING 
cal | cut -c3-5 # cut col 3-5, useful for fixed-width file
```

Use `sort` to sort lines of given file or standard input based on character collating sequence.
```bash
sort FILENAME
sort FILE -o NEWFILE # write to NEWFILE instead of standard output
```

`uniq` removes adjacent repeated lines from given file
```bash
uniq FILE # print one instance of each line
uniq -c FILE # prefix lines by the number of occurrences
uniq -d FILE # only print duplicate lines, one for each group
uniq -cd
```




