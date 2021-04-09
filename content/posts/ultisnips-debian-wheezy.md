---
title: 'Installing Vim UltiSnips on Debian 7 Wheezy'
date: Sat, 15 Apr 2017 11:10:42 +0000
draft: false
tags: ['7', 'debian', 'Guides', 'ultisnips', 'vim', 'wheezy']
---

I had some problems recently installing UltiSnips on my Debian Wheezy. The first problem is that the Vim which comes with Debian does not come precompiled with Python, which UltiSnips needs. The second problem is that the version of the Vim is too old and is unsupported by UltiSnips. First [uncomment](https://www.howtogeek.com/118389/how-to-comment-out-and-uncomment-lines-in-a-configuration-file/) or add the following line to your `/etc/apt/sources.list`. This is because the version of Vim in the default repository is too old. You can read more about backports [here](https://backports.debian.org/).
```
deb http://ftp.debian.org/debian wheezy-backports main
```
Run the following commands:
```
sudo apt-get update # always remember to do this
sudo apt-get remove vim # remove the old Vim which doesn't have python
sudo apt-get remove vim-common # you can try to do this without this line. I personally needed to this.
sudo apt-get -t wheezy-backports install vim-nox # Installing the correct compiled version of Vim which has Python.

```
After this you can install UltiSnips normally by using the official guide: [https://github.com/SirVer/ultisnips](https://github.com/SirVer/ultisnips)
