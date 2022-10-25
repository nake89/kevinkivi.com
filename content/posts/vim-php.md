---
title: 'VIM and PHP'
date: 2022-10-25T22:01:00+02:00
draft: false
tags: ['vim', 'php', 'coc']
---

To make VIM work more like VSCode, you really want to install VIM plugin called CoC. It adds LSP features to VIM and makes it easy to port VSCode extensions to Vim, and it has great, mature ecosystem: https://github.com/neoclide/coc.nvim

To get PHP language server features, you want to install a PHP language server extension for CoC: https://github.com/marlonfan/coc-phpls

This extension uses Intelephense in the background and makes it so that you can jump to definitions etc. But some of the features that you are used to have with language servers are missing unless you get premium licence for Intelephense. Like renaming variables.

Thankfully there is a free plugin for vim that allows for variable renaming: https://github.com/adoy/vim-php-refactoring-toolbox

The plugin is purely written in vim script. I've used this for a while and it works fine.

I hope this helps you in your VIM PHP journey. Have a great day!
