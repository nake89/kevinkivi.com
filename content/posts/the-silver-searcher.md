---
title: "Say goodbye to grep"
date: 2021-07-25T10:11:00+02:00
draft: false
tags: ["linux", "cli", "terminal", "grep", "ag", "ack"]
---

`ack` is a famous code search tool to replace `grep` (in a lot of use cases): https://beyondgrep.com/why-ack/ Now there is something even better. There is `ag` aka The Silver Searcher: [ggreer/the_silver_searcher](https://github.com/ggreer/the_silver_searcher)
It is like ack, but faster.

### Why not just grep?

- [Hella fast.](https://github.com/ggreer/the_silver_searcher#whats-so-great-about-ag) [Like really](https://geoff.greer.fm/ag/speed/) [really fast.](https://github.com/ggreer/the_silver_searcher#how-is-it-so-fast) It is beautifully optimized C.
- It ignores files from `.gitignore`

Instead of doing this with grep:

```
grep -R --exclude-dir=node_modules 'foobar' /path/to/your/code
```

You can just do (if you have node_modules in your .gitignore):

```
ag foobar /path/to/your/code
```

You can also ignore folders with this option:

```
ag --ignore file_or_folder_name_to_ignore /path/to/your/code
```
