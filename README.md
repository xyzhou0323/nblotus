# 脑脑客厅 (NeuroBridge)

基于 [Hugo](https://gohugo.io/) 构建的神经多样性中文内容站点，使用 lotusdocs 主题。

线上地址：**[neurobridge.cn](https://neurobridge.cn/)**

## 环境要求

- **Hugo** v0.153+ (extended 版本)，[安装指南](https://gohugo.io/installation/)
- **Git** — 版本管理
- 文本编辑器（推荐 VS Code）

```bash
# 确认 Hugo 版本
hugo version
# 应输出类似: hugo v0.153.1+extended windows/amd64 ...
```

## 快速开始

```bash
# 克隆仓库
git clone <repo-url> neurobridge
cd neurobridge

# 启动本地开发服务器（含草稿）
hugo server -D

# 浏览器访问 http://localhost:1313
```

开发服务器支持热重载：修改内容或模板后浏览器自动刷新。

## 项目结构

```
nblotus/
├── archetypes/         # Hugo 内容模板 (hugo new content --kind <name>)
├── assets/
│   └── fonts/
│       └── simhei.ttf  # OG 图片中文字体（黑体）
├── content/docs/       # 所有文章内容
│   ├── brainstorm/     # 头脑风暴 — 评论与观点文章
│   ├── cowriting/      # 脑脑共写 — 多人共同自述
│   ├── external/       # 外部视角 — NT/外部人士分享
│   ├── interview/      # 脑脑访谈 — 访谈记录
│   ├── neurobridge/    # 脑脑空间 — 关于本站与里程碑
│   ├── neurodiversity/ # 神经多样性 — 翻译与学术资料
│   ├── resource/       # 资源 — 工具、练习册、测试
│   └── story/          # 脑脑故事 — 个人自述故事
├── layouts/            # 项目级模板覆盖（优先级高于 themes/）
│   └── partials/docs/head/
│       └── get-featured-image.html  # OG 图片生成模板
├── static/             # 静态资源（直接复制到 public/）
│   └── images/
├── themes/lotusdocs/   # 主题（本地修改版）
├── hugo.toml           # Hugo 配置
├── CLAUDE.md           # AI 助手的项目规则（供 Claude Code 使用）
└── public/             # 构建输出（已 gitignore，上传至 OSS 部署）
```

## 创建新文章

### 使用 Hugo archetype（推荐）

```bash
# 头脑风暴评论文章
hugo new content --kind brainstorm content/docs/brainstorm/my-post.md

# 访谈
hugo new content --kind interview content/docs/interview/my-interview.md

# 个人故事
hugo new content --kind story content/docs/story/my-story.md

# 翻译/学术资料
hugo new content --kind neurodiversity content/docs/neurodiversity/my-translation/index.md

# 共写
hugo new content --kind cowriting content/docs/cowriting/my-cowriting/index.md

# 外部视角
hugo new content --kind external content/docs/external/my-post.md
```

创建后：
1. 修改 `weight`（同 section 内排序，数字越小越靠前）
2. 填写 `description`（30-120 字，会显示在 OG 卡片和 SEO 标签中）
3. 选择 `icon`（[Google Material Icons](https://fonts.google.com/icons)，用下划线连接）
4. 把 `draft: true` 改为 `false` 即可发布

### 文件命名约定

- **单文件页面**（无附属图片）：`content/docs/<section>/post-name.md`
- **页面包**（有附属图片/资源）：
  ```
  content/docs/<section>/post-name/
  ├── index.md
  ├── image1.jpg
  └── image2.png
  ```

## Front Matter 参考

```yaml
---
weight: 99                   # 排序（越小越靠前）
title: "Author丨你的标题"     # 格式因 section 而异，见 CLAUDE.md
description: "简短描述"       # SEO & OG 卡片用
icon: "Article_Person"        # Material Icons 名称
date: "2026-01-01T00:00:00+08:00"
lastmod: "2026-01-01T00:00:00+08:00"
draft: false                  # true = 开发可见，false = 发布
toc: true                     # 显示目录
---
```

标题格式详见 [CLAUDE.md](CLAUDE.md)。

## 常用 Shortcodes

| Shortcode | 用途 |
|---|---|
| `{{< figure src="image.jpg" caption="说明" >}}` | 插入图片 |
| `{{% alert icon="🔖" context="warning" %}}文字{{% /alert %}}` | 警告框 |
| `{{% alert icon="🧠" context="info" %}}文字{{% /alert %}}` | 信息框 |
| `{{% relref "/docs/brainstorm/post-name" %}}` | 站内文章链接 |

## OG 图片

每次构建时 Hugo 会自动为每篇文章生成 OpenGraph 社交分享图片（1200×630px）。

- **模板**：[layouts/partials/docs/head/get-featured-image.html](layouts/partials/docs/head/get-featured-image.html)
- **字体**：SimHei 黑体（`assets/fonts/simhei.ttf`）— 支持中文 + 拉丁字符
- **优先级**：页面内嵌图片 > 自动生成
- 如果文章有 `feature*`、`cover*` 或 `thumbnail*` 图片，Hugo 会使用该图片而非自动生成

OG 模板中的中文字符换行通过 Hugo 的 `findRE` + `delimit` 手动实现（因为 `images.Text` 不支持 CJK 自动换行）。如需调整字号/间距/位置，编辑 `layouts/` 下的副本即可。

## 构建与部署

```bash
# 常规构建（输出到 public/）
hugo

# 构建并清理过期资源
hugo --gc

# 开发服务器（含草稿，支持热重载）
hugo server -D
```

**部署流程**：本地 `hugo` 构建 → 将 `public/` 目录上传至阿里云 OSS。

> `public/` 已加入 `.gitignore`，不需要提交到仓库。

## 协作注意事项

- **草稿机制**：新建文章默认 `draft: true`，开发服务器 (`-D`) 可见，正式构建不可见。确认发布前改为 `false`
- **图片资源**：页面专属图片放在页面包内（`index.md` 同级目录）；公共图片放在 `static/images/`
- **模板修改**：覆盖主题模板时，将文件放在项目根目录的 `layouts/` 下（而非直接改 `themes/lotusdocs/`），这样主题升级时不会丢失自定义
- **AI 辅助**：项目包含 `CLAUDE.md`，使用 Claude Code 时它会自动参考项目规范
- **提交前**：确保 `hugo` 构建无报错后再提交

## 链接

- Hugo 文档：[gohugo.io](https://gohugo.io/)
- lotusdocs 主题：[github.com/colinwilson/lotusdocs](https://github.com/colinwilson/lotusdocs)
- Material Icons：[fonts.google.com/icons](https://fonts.google.com/icons)
