---
layout:     post
title:      "取得 Momentum 的壁纸"
date:       2016-04-22 08:00:00
author:     "Aaron"
tags:
    - Javascript
---

一直用 Chrome 上一个扩展 [Momentum](https://chrome.google.com/webstore/detail/momentum/laookkfknpbbblfpciffpaejjkokdgca)，经常会遇到打开新tab的时候看到背景图片 喜欢得不得了，然后就得 Dev Tool 慢慢去找链接下载下来做桌面壁纸，很是麻烦。做了一个 Bookmarklet 来方便操作。

<a href="javascript: (function() { if (typeof jQuery === 'undefined') { var script = document.createElement('script'); script.src = 'http://ajax.googleapis.com/ajax/libs/jquery/1/jquery.min.js'; script.onload = releasetheKraken; document.body.appendChild(script); } else { releasetheKraken(); } function releasetheKraken() { var url = $('li.fadein').css('background-image').slice(5, -2); var dLink = $('.quicklinks-show').next(':contains(\'Download\')'); if (dLink.length === 0) { console.log('show bg url', url); var a = document.createElement('a'); a.target = '_blank'; a.href = url; txt = document.createTextNode('Download'); a.appendChild(txt); dLink = $(a).insertAfter('.quicklinks-show').css('opacity', 0); } dLink.animate({ opacity: 0, marginLeft: '50px' }, 0); dLink.delay(100).animate({ marginLeft: '0', opacity: 1 }, 1000); } })();">☕ Momentum Wallpaper</a> ← drag this button to your Bookmarks Bar.

点击之后，Momentum Tab 左上角 Links 右边会出现 Download 字样链接新 Tab 到图片的 URL。