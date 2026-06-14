---
weight: 99
title: "Author丨{{ replace .File.ContentBaseName "-" " " | title }}"
description: ""
icon: "Arrows_Output"
date: "{{ .Date }}"
lastmod: "{{ .Date }}"
draft: true
toc: true
---

分享者：AuthorName  

（约XXXX字，阅读约需X分钟，读屏软件约需X分钟）

---

正文内容...

---

本文首发: [脑脑空间NeuroBridge小红书](link)  
首发时间：{{ dateFormat "2006-1-2" .Date }}  
首发排版：[排版者](link)  

{{< figure src="/images/qrcode.png" caption="上图内容：脑脑空间的小红书、公众号、网站二维码，欢迎关注脑脑空间NeuroBridge" >}}
