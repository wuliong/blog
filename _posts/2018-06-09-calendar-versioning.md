---
layout: post
title: "Introducing Calendar Versioning"
date: 2018-06-09 18:45:00 +0800
summary: a brief overview of calendar versioning
slug: intro-calendar-versioning
categories: software
---

In short, 
> CalVer is a software versioning convention that is based on your project's release calendar, instead of arbitrary numbers.

In general, a version is composed of two or three numeric segments separated by points. The segments or parts of the version follow this scheme:
```plaintext
Major: 1st number in the version (e.g., 2 & 3 are Python's major versions).
Minor: 2nd number in the version.
Micro: 3rd and usually final number. Sometimes referred as the "patch" segment.
Modifier: Optional text tag, such as "dev", "alpha", "rc1" and so on.
``` 

When speaking of different date format, use the following terminology
```plaintext
YYYY: full year -> 2006, 2016
  YY: short year -> 6, 16, 19
  MM: short month -> 1, 2, ..., 11, 12
  0M: zero-padded month -> 01, 02, ..., 11, 12
  DD: short day -> 1, 2, ..., 30, 31
  0D: zero-padded day -> 01, 02, ..., 30, 31
```

Case studies
```plaintext
Ubuntu: YY.0M.MICRO (4.10, 6.06 LTS, 12.04 LTS, etc.)
Twisted: YY.MM.MICRO (18.4.0) micro being the bugfix release number
youtube_dl: YYYY.0M.0D (2018.06.04, 2018.06.02)
pytz: YYYY.MM (2017.3, 2018.3, 2018.4)
PyCharm: YYYY.MINOR.MICRO (2018.1.4)
fusefs-ntfs: YYYY.MM.DD_MICRO (2011.4.12_1, 2016.2.22_1)
```