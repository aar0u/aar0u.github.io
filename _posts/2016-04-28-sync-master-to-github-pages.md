---
layout:     post
title:      "Github 简单同步 master 到 Github Pages 分支"
subtitle:   "我真的很懒"
date:       2016-04-28
author:     "Aaron"
tags:
    - 程序
---

Github Page for User Site 只要使用 master 分支就好，但是 for Project Site 需要 push 代码到 gh-pages 分支

```
For Project pages, the gh-pages branch is used to publish your site.
```

用 Git GUI 比如 [SourceTree](https://www.sourcetreeapp.com/), [Github Desktop](https://desktop.github.com/) 来切换分支到 gh-pages，commit，push，再切换回来 master branch，操作起来太繁琐。

Git 命令行会提高很多效率 

```bash
git checkout master
git status
git commit -am "Committing changes to master"
git push origin master
git checkout gh-pages
git rebase master # or merge, whatever your preference
git push origin gh-pages
git checkout master
```