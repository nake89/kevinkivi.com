---
title: "Developing for Old Browsers"
date: 2025-07-16T09:44:00+02:00
lastmod: 2025-07-16T14:35:00+02:00
draft: false
tags:
  ["internet explorer", "javascript", "ie6", "software development"]
---

### This post is still a draft. Come back later.

I have a Windows 98 SE virtual machine that I like to tinker with. I have Apache and PHP 5.1.X running on it. I have ansi.sys enabled MS-DOS terminal[^ansisys], so I can have colors and create cool CLI apps[^ansicolors]. I have VIM 7.3 installed in it.[^vimdos] Surprisingly enough vim-plug and vim-airline work.[^vimplug][^vimairline] This means we can have a very modern development expierience on Vim. Vim 7.3 has omni-completion (a type of intellisense) and JS syntax highlighting. For editing text files or keeping notes I also have Notepad++. [^notepadplusplus] I also have webone installed. So I can connect to https sites. webone is a proxy that runs in a docker container that terminates the TLS connection. [^webone]

As a fun exercise for myself I wanted to create a modern web app that would work on an old browser. I first picked IE5. Because it is the first browser to support XmlHttpRequest, which means it could be used to run a "modern" web app. I then upgraded my IE5 to IE5.5. Now I'm thinking of compromising and running IE6. I have created a bundler and a JSX transpiler and a watcher. I have created a react-like web application, that supports routing and state. It supports JSX. Immediately if it detects a file change it compiles and bundles the files. And I just need to hit refresh on the browser and I can view my changes.

Currently I don't know if all of this works on my Windows 98 yet. It should though. I don't like develeping on my Win98 because it doesn't have git. So I can keep my files in sync nice. That is why I'm creating a git "client" for Windows 98. It wont work completely standalone. It actually needs a server. Because it is a thin-client. 
Internet Explorer <=6 had interesting quirks.[^doublemargin]

[^ansisys]: https://en.wikipedia.org/wiki/ANSI.SYS
[^ansicolors]: https://stackoverflow.com/questions/34034730/how-to-enable-color-for-php-cli
[^vimdos]: https://www.vim.org/download.php#pc
[^vimplug]: https://github.com/junegunn/vim-plug
[^vimairline]: https://github.com/vim-airline/vim-airline
[^notepadplusplus]: Version 5.8.2 seems to be the last properly working version for Windows 98. https://www.vogons.org/viewtopic.php?t=49858&start=40
[^webone]: https://github.com/atauenis/webone
[^doublemargin] https://web.archive.org/web/20090501035842/http://www.positioniseverything.net/explorer/doubled-margin.html
