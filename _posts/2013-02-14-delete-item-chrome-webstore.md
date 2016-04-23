---
layout:     post
title:      "在 Chrome web store Developer Dashboard 删除无用的 App"
date:       2013-02-14
author:     "Aaron"
header-img: "img/post-bg-js-version.jpg"
tags:
    - Javascript
---

Chrome web store 的 [Developer Dashboard](https://chrome.google.com/webstore/developer/dashboard) 没有提供删除 App 的显式功能。  

但是页面 Javascript 有个 function 提供了删除 App 的功能

```javascript
cxDeleteItem(itemId)
```

如何获得 itemId：
在 Bashboard 点击对应 App 的 Edit 按钮，会跳转至页面，URL 类似 https://chrome.google.com/webstore/developer/edit/dldpoaegoklacfdljbjflkpagodkeibl ，此处的 dldpoaegoklacfdljbjflkpagodkeibl 就是 itemId。

打开 Chrome 菜单 –> Tools –> JavaScript console（快捷键 Ctrl + Shift + J）  
在控制台输入：

```javascript
cxDeleteItem("dldpoaegoklacfdljbjflkpagodkeibl")
```

然后 Enter，会出现是否删除App的确认。Google 为了大家不要误操作也是拼了 @@