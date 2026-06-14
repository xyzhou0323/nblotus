# 脑脑客厅 (NeuroBridge) 网站项目指南

## 项目概览

- **框架**: Hugo v0.153+ (extended)
- **主题**: lotusdocs (本地修改版, `themes/lotusdocs/`)
- **语言**: 中文 (`zh-cn`)
- **线上地址**: `https://neurobridge.cn/`

## 目录结构

```
content/docs/
├── brainstorm/     # 头脑风暴 — 评论文章
├── cowriting/      # 脑脑共写 — 多人共同自述
├── external/       # 外部视角 — NT/外部人士的分享
├── interview/      # 脑脑访谈 — 访谈记录
├── neurobridge/    # 脑脑空间 — 关于本站
├── neurodiversity/ # 神经多样性 — 翻译与学术资料
├── resource/       # 资源 — 工具和练习册
└── story/          # 脑脑故事 — 个人自述故事
```

## 内容创建规则

### Front Matter (所有页面通用)

```yaml
---
weight: <整数>              # 同 section 内的排序, 数字越小越靠前
title: "<标题>"
description: "<简短描述>"   # 用于 OG 图片和 meta 标签, 建议 30-120 字
icon: "<Material图标名>"    # Google Material Icons, 用下划线连接
date: "2025-01-01T00:00:00+08:00"
lastmod: "2025-01-01T00:00:00+08:00"
draft: false
toc: true
---
```

### 标题格式规范

| Section | 标题格式 | 示例 |
|---|---|---|
| brainstorm | `Author丨中文标题` | `"Admin丨关于神经多样性运动的四个迷思"` |
| interview | `Guest1 & Guest2丨中文标题` | `"Alexaner & peihan丨在误解中生长：神经多样性与我们所处的世界"` |
| story | `Author丨中文标题` | `"大发丨确诊故事分享：无限包容，继续前进"` |
| neurodiversity | `类型丨作者（年份）：中文标题` | `"翻译丨Walker（2014）：神经多样性：基本术语与定义"` |
| cowriting | `共写 N丨中文标题` | `"共写 5丨我看"脑脑空间"（2025.12）"` |
| external | `Author丨中文标题` | `"阿米丨跨越脑间的桥梁：当NT开始了解ND"` |
| resource | `类型丨中文标题` | `"网站丨NeuroXYZ.cn：神经殊异测试平台"` |

### 正文结构

按 section 分 4 类模板：

#### 模板 1: 评论/故事/外部 (brainstorm, story, external)

```markdown
作者：[AuthorName](profile-link) 

（约XXXX字，阅读约需X分钟，读屏软件约需X分钟）

文章结构：

1. 第一节标题
2. 第二节标题
...

---

正文内容，使用 ## 二级标题分节...

---

本文首发: [脑脑空间NeuroBridge小红书](link)  
首发时间：YYYY-M-D  
首发排版：[排版者名](link)  
本文亦见：[脑脑空间NeuroBridge微信公众号](link)  
公众号排版：[排版者](link)

头脑风暴内容为投稿者分享，不代表脑脑空间及其他个人的观点及立场。

{{< figure src="/images/qrcode.png" caption="上图内容：脑脑空间的小红书、公众号、网站二维码，欢迎关注脑脑空间NeuroBridge" >}}
```

注意事项：
- `story` 和 `external` 节**不加**"头脑风暴内容为投稿者分享..."的免责声明
- 阅读时间估算：中文 ~500字/分钟，读屏 ~300字/分钟
- 部分 story 文章没有文章结构列表，取决于内容

#### 模板 2: 访谈 (interview)

```markdown
系列访谈——"脑洞时间" 第X期  
主人公：Name1 & Name2  

（约XXXX字，阅读约需X分钟，读屏幕软件约需X分钟）

内容结构：

1. 话题一
2. 话题二
...

---

{{% alert icon="🔖" context="warning" %}}
**对谈双方介绍**：
...介绍内容...
{{% /alert %}}

---

## 话题一

> Person

对话内容...

---

本文首发: 脑脑空间NeuroBridge小红书[1](link1)、[2](link2)  
首发时间：YYYY-M-D  
首发排版：[排版者](link)  

{{< figure src="/images/qrcode.png" caption="上图内容：脑脑空间的小红书、公众号、网站二维码，欢迎关注脑脑空间NeuroBridge" >}}
```

#### 模板 3: 翻译/学术 (neurodiversity)

```markdown
原文链接: Author（Year）：[Title](url)  
原标题："Original Title"  
作者：AuthorName，Affiliation  
（本译文已由原作者授权。）  
翻译：Translator1，Translator2

（约XXXX字，阅读约需X分钟，读屏幕软件约需X分钟）

文章结构：

- 前置说明
- 正文
    1. 小节
    ...

---

正文内容...
```

#### 模板 4: 共写 (cowriting)

```markdown
本期参与者（按写作顺序）：  
（1）Name1，（2）Name2，...

（约XXXX字，阅读约需X分钟，读屏幕软件约需X分钟）

内容结构

1. 前言
2. 共写说明
3. 共写正文

---

## 前言

...

## 共写说明

本期主题：【主题】  
副标题

说明文字...

（AuthorName）

---

## 共写正文 

### 01 Name1

内容...

---

本文首发: [脑脑空间NeuroBridge微信公众号](link)  
首发时间：YYYY-M-D  
公众号编辑 & 题图 & 排版：Name  

{{< figure src="/images/qrcode.png" caption="上图内容：..." >}}
```

### 正文格式细节

- **作者署名**: `作者：[Name](link)` 或 `分享者：Name`
- **分隔符**: 使用 `---` 分隔文章的不同区块
- **引用格式**: 使用 `> ` 块引用表示对话中的发言者
- **强调**: 使用 `**粗体**` 强调关键词
- **代码/术语**: 使用反引号包围英文术语，如 `masking`
- **注释**: 使用 `{{% alert %}}` shortcode 添加译注或说明
- **图片**: 使用 `{{< figure src="filename.jpg" width="300" caption="..." >}}`

### 文件命名与目录约定

- **单文件页面** (无附属图片): `content/docs/section/page-name.md`
- **页面包** (有附属图片/资源): 
  ```
  content/docs/section/page-name/
  ├── index.md
  ├── image1.jpg
  └── image2.png
  ```
- 文件名用小写、连字符分隔，与标题关键词对应

### 常用 Shortcodes

| Shortcode | 用途 |
|---|---|
| `{{< figure src="..." caption="..." >}}` | 插入图片 |
| `{{% alert icon="🔖" context="warning" %}}...{{% /alert %}}` | 警告/提示框 |
| `{{% alert icon="🧠" context="info" %}}...{{% /alert %}}` | 信息框 |
| `{{% relref "/docs/section/page" %}}` | 站内链接 |

### 图标命名

使用 Google Material Icons 的蛇形命名 (`snake_case`)，例如:
`Accessibility_New`, `Article_Person`, `Call_Missed_Outgoing`, `Record_Voice_Over`, `Stylus_Fountain_Pen`

可用的图标列表参见 [Material Icons](https://fonts.google.com/icons)。

### OG 图片

- 模板文件: `layouts/partials/docs/head/get-featured-image.html` (项目级覆盖)
- 中文字体: SimHei (`assets/fonts/simhei.ttf`)
- 源模板中的 `themes/lotusdocs/layouts/.../get-featured-image.html` 同步保持
- 换行逻辑: 使用 `findRE` + `delimit` 手动对中文进行字符级切分换行
- 如需调整字号/行距/位置参数，编辑项目级的 `layouts/` 副本

### 构建命令

```bash
hugo              # 常规构建
hugo --gc         # 构建 + 清理过期资源
hugo server -D    # 开发服务器 (含草稿)
```
