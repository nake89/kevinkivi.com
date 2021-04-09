---
title: 'End Bash Script Loop'
date: Wed, 03 May 2017 16:24:51 +0000
draft: false
tags: ['Bash', 'Command-line']
---

Sometimes when bash scripting you might want the ability to cancel your script's loop with CTRL-C. Below is an exampl simple script which loops through a file of domains separated by line break and it digs the A record (IP address) of the domain. Read further to learn how to force quit this script.

```
#!/bin/bash
while read p; do
    dig $p A +short
done <listofdomains.txt
```

If your list of domains is large your and you want to quit this script, you cant. Pressing CTRL-C will not work. You need to add `trap "echo Script ended; exit;" SIGINT SIGTERM` to the beginning of your script. E.g.

```
#!/bin/bash
trap "echo Script ended; exit;" SIGINT SIGTERM
while read p; do
    dig $p A +short
done <listofdomains.txt
```

Pressing CTRL-C will now print "Script ended" to your terminal and exit the script.
