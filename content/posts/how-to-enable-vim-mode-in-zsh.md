---
title: 'How to enable vim mode in zsh'
date: 2022-08-12T20:24:00+02:00
draft: false
tags: ['shell', 'vim', 'zsh']
---

Vim mode let's you use vim keys. You start in insert mode and esc let's you go into normal mode. To enable vim mode append the following snippet to you .zshrc in your home directory.

```
# Enable vim mode.
bindkey -v
```

Now close the terminal and reopen it (or just type `. .zshrc`) and you are done.
