---
title: "cPanel: Listing all non-self-signed certificates"
date: Sat, 10 Feb 2018 13:39:23 +0000
draft: false
tags: ["Bash", "Command-line", "Linux"]
---

I made a bash script listing all non-self-signed certificates (for certain user by username or domain or for all users) in cPanel.

```
Usage: lrcert [OPTION] [INPUT]
Example: lrcert [cPanel username]

Options:
  -d [domain]      Displays all certificates of the owner of the domain.
  -a, --all        Lists all certificates of all cPanel users
  -v, --version    Displays version.
  -h, --help       This help page.
```

GitHub: [https://github.com/nake89/lrcert/](https://github.com/nake89/lrcert/)
