---
title: 'How to get history to work in vim mode zsh'
date: 2022-08-12T20:52:00+02:00
draft: false
tags: ['shell', 'vim', 'zsh', 'terminal history']
---

When [enabling vim mode in zsh](https://kevinkivi.com/posts/how-to-enable-vim-mode-in-zsh/) it will make pressing `ctrl+r` not show terminal history anymore. It gets rebound to terminal refresh which is not necessary. To renable `ctrl+r` append this to your `.zshrc`:

```
bindkey "^R" history-incremental-search-backward
```

Now close the terminal and reopen it (or just type `. .zshrc`) and you are done.
