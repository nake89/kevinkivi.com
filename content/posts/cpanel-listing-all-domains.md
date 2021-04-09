---
title: "cPanel: Listing all domains"
date: Sun, 11 Feb 2018 19:46:38 +0000
draft: false
tags: ["Bash", "Command-line", "Linux"]
---

I made a bash script listing all main domains and addon domains (for certain user by username or domain or for all users) in cPanel.

```
Usage: lsdom [OPTION] [INPUT]
Example: lsdom [cPanel username]
Lists domains for certain user by username or domain or for all users

Options:
  -d [domain]      Displays all domains of the user of the input domain.
  -a, --all        Lists all domains.
  -v, --version    Displays version.
  -h, --help       This help page.
```

GitHub: [https://github.com/nake89/lsdom](https://github.com/nake89/lsdom)
