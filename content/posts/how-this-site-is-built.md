---
title: "这个网站是怎么搭的"
date: 2026-11-09T10:30:00+08:00
draft: false
author: "ycf"
summary: "Hugo、PaperMod 加一条 GitHub Actions 流水线——简单介绍一下这个博客背后的技术栈。"
description: "介绍这个博客背后的技术栈：Hugo 静态站点生成器、PaperMod 主题，以及通过 GitHub Actions 自动部署到 GitHub Pages。"
tags: ["hugo", "建站", "github"]
categories: ["博客"]
showToc: true
---

这个网站是用 [Hugo](https://gohugo.io/) 生成的静态站点，样式来自
[PaperMod](https://github.com/adityatelange/hugo-PaperMod) 主题，最后由一条
GitHub Actions 流水线发布到 GitHub Pages。

## 技术栈

| 层次 | 选择 |
| --- | --- |
| 生成器 | Hugo（extended 版） |
| 主题 | PaperMod |
| 托管 | GitHub Pages |
| 构建与部署 | GitHub Actions |
| 内容 | git 里的 Markdown |

## 写一篇文章

```bash
# 新建一篇文章
hugo new content posts/my-new-post.md

# 本地预览，包含草稿并支持热重载
hugo server -D
```

Front matter 就是普通的 TOML/YAML；PaperMod 会读取 `title`、`date`、`tags`、
`categories`、`summary`、`showToc` 这些字段。

## 发布流程

每次推送到 `main` 分支都会触发流水线：

1. 安装固定版本的 Hugo extended。
2. 检出仓库，包含主题子模块。
3. 执行 `hugo --gc --minify` 构建。
4. 把 `public/` 作为 Pages 产物上传并部署。

部署时不在本地构建，所以发一篇文章就是一次 `git push`。

## 为什么这么搭

- **快**——纯静态站点，没有服务器、没有数据库，也没有运行时构建。
- **可迁移**——内容就是 git 仓库里的 Markdown。
- **免费**——GitHub Pages 负责托管，GitHub Actions 负责构建。
- **无聊**——对一个博客来说，这恰恰是优点。
