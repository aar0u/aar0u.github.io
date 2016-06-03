---
layout:     post
title:      "如果单独下载了 node.exe, 手动安装 npm"
subtitle:   "npm w/o installer"
date:       2016-06-03
author:     "Aaron"
tags:
    - 程序
---

下载 [Node.js](https://nodejs.org/en/download/) 的时候，个人偏向喜欢下载独立 Windows Binary (.exe)。

这种情况下如果需要使用 npm，就不是很方便，官方提供的[文档](https://github.com/npm/npm#windows-install-or-upgrade)也是建议重新下载 Intaller。

手动安装方法如下

1. 前往 [https://github.com/npm/npm/releases](https://github.com/npm/npm/releases) 下载最新 npm Release
2. 在 node.exe 同目录下创建目录 node_modules\npm
3. 解压下载的 npm Release 至 node_modules\npm
4. 拷贝 node_modules\npm\bin 下面的 npm 或者 npm.cmd (依照操作系统) 到 node.exe 同目录下

测试如下，应该可以看到正确版本。如果需要全局使用，添加 node.exe 根目录到系统 path 路径。

```
npm -v
```