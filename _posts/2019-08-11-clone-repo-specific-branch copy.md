---
title: Clone Repo Specific Branch
author: danijeljw-rpc
date: 2019-08-11 00:00:00 +1000
categories: [git, cli]
tags: [git, github]
math: true
mermaid: true 
---

Clone just a single branch from git repo:
```sh
git clone -b <branch> <remote_repo>
```

Example:
```sh
git clone -b my-branch git@github.com:user/myproject.git
```

With Git 1.7.10 and later, add `--single-branch` to prevent fetching all branches:
```
git clone -b my-branch --single-branch git@github.com:user/myproject.git
```