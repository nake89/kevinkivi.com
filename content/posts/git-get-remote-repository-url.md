---
title: 'GIT: Get remote repository URL'
date: Thu, 27 Sep 2018 19:37:13 +0000
draft: false
tags: ['Git']
---

So you need the remote repository URL. Maybe because you are trying to `git add remote`. You can type the below text to get the full info (needs to be done inside the folder you are working in):

```
git remote show origin
```

OR

```
git config --get remote.origin.url
```

After you know this, if you want you can create a new remote branch

```
git add remote <name you want for your new branch> <URL you just got>
git add remote newbranch git@hostedgit.yourdomain.com:name/project.git
```
