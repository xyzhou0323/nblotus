---
weight: 99
title: "类型丨Author（Year）：{{ replace .File.ContentBaseName "-" " " | title }}"
description: ""
icon: "Script"
date: "{{ .Date }}"
lastmod: "{{ .Date }}"
draft: true
toc: true
---

原文链接: Author（Year）：[Title](url)  
原标题："Original Title"  
作者：AuthorName，Affiliation  
（本译文已由原作者授权。）  
翻译：Translator1，Translator2

（约XXXX字，阅读约需X分钟，读屏软件约需X分钟）

文章结构：

- 前置说明
- ...

---

正文内容...

---

本文首发: 脑脑空间NeuroBridge小红书：[link1](url1)、[link2](url2)  
首发时间：{{ dateFormat "2006-1-2" .Date }}  
首发排版：[排版者](link)  

{{< figure src="/images/qrcode.png" caption="上图内容：脑脑空间的小红书、公众号、网站二维码，欢迎关注脑脑空间NeuroBridge" >}}
