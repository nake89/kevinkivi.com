---
title: 'Linux & OSX: Get file encoding'
date: Fri, 28 Sep 2018 14:37:01 +0000
draft: false
tags: ['Bash', 'Linux', 'OSX']
---

Sometime you need to know what's your file encoding? Is it UTF-8, ISO 8859-1, ASCII or Windows 1252? You can find this out by using the `file` Unix command. Linux: `file -i <filename>` Mac OSX: `file -I <filename>` Example usage:

```
username@server ~$ file -i somefile.php
somefile.php: text/x-php; charset=us-ascii
username@server ~$ file -i myutf8file.txt
myutf8file.txt: text/plain; charset=utf-8
username@server ~$ file -i username.tar.bz2
username.tar.bz2: application/x-bzip2; charset=binary
username@server ~$
```
If you want only the encoding. You can do `file -i filename.txt | sed "s/.*charset=\(.*\)/\1/"` E.g.
```
username@server ~$ file -i myutf8file.txt | sed "s/.\*charset=\\(.\*\\)/\\1/"
utf-8
```
