---
title: 'How to Search Contents of File in Linux'
date: Sat, 15 Apr 2017 17:48:48 +0000
draft: false
tags: ['Bash', 'bash', 'command-line', 'grep', 'guide', 'Guides', 'linux', 'search contents of file', 'search string in file']
---

This is something you need to do often for one reason or another. Maybe you have a bunch of text files, which have been named horribly and you have no idea which file has the thing you are looking for, but you happen to remember a word in that file. Or maybe you need to find which file contains a certain variable to find the root cause of an error you are experiencing in your script.

What ever the reason may be, this command lets you search a directory recursively (meaning all the directories in it as well) to find your file(s). Below is the command.
```
grep -rnw '/give/your/path/' -e "pattern"
```
The command-line options are as the following: `-r`, Recursive `-n`, Gives you the line number `-w`, Searches the whole word `-e`, Searches the pattern you tell it.

Source: [http://stackoverflow.com/questions/16956810/how-to-find-all-files-containing-specific-text-on-linux](http://stackoverflow.com/questions/16956810/how-to-find-all-files-containing-specific-text-on-linux)
