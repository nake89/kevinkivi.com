---
title: 'Echoing multiline in linux terminal'
date: Sat, 03 Feb 2018 18:02:29 +0000
draft: false
tags: ['Bash', 'Command-line', 'Linux', 'Terminal']
---

There are at least three fun ways to echo multiline to a file. We are going to look at doing the output twice, the heredoc -method and writing multiline using double quotes. 1. Output twice I think this is the simplest and most intuitive method if you are familiar with linux output redirection.

```
user@server:~/projects/blog\_content$ echo "This file is" >> multiline.txt
user@server:~/projects/blog\_content$ echo "multiline" >> multiline.txt
user@server:~/projects/blog\_content$ cat multiline.txt
This file is
multiline
```

2\. [Heredoc](https://en.wikipedia.org/wiki/Here_document#Unix_shells) -method You can replace EOF with your choice of characters. It denotes the ending of your input.

```
user@server:~/projects/blog\_content$ cat <<EOF >> sorcery.txt
> This is
> SORCERY!
> EOF
user@server:~/projects/blog\_content$ cat sorcery.txt
This is
SORCERY!
```

3\. Write multiline Leaving the double quote open you can press enter and start a new line. This is my favorite method.

```
user@server:~/projects/blog\_content$ echo "what is this
> magic" > magic.txt
user@server:~/projects/blog\_content$ cat magic.txt
what is this
magic
```
