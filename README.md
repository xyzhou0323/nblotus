网站基于hugo框架的lotusdocs主题：https://lotusdocs.dev/docs/

如果要增加新文章，请用markdown排版后存在content/docs对应主题的文件夹下

注意文件头：

---

weight: 1 #排序权重

title: "文章标题"

description: "文章描述"

icon: "Record_Voice_Over" # 参考这里选择，把名称空格换成下划线即可：https://fonts.google.com/icons?icon.style=Outlined

date: "2025-04-22T17:06:44+08:00" #注意日期不要超过此刻，否则会出错

lastmod: "2025-12-21T17:06:44+08:00"

draft: false #草稿状态将不会展示出来

toc: true #开启目录显示

---

文本框格式：

{{% alert icon="🫧" context="info" %}} # Additional alert contexts include success, danger, warning, primary, light and dark

文本内容

{{% /alert %}}

添加图片：
在/content/docs建立一个文件夹，以文章名命名，md放在这个文件夹内，名称为index.md。图片放在文件夹内，自行命名。

{{< figure src="图片名称.png" caption="图片内容：描述图片" >}}
