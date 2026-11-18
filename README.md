# aboyfeng.github.io

个人博客 —— [Hugo](https://gohugo.io/) + [PaperMod](https://github.com/adityatelange/hugo-PaperMod)，
由 GitHub Actions 发布到 GitHub Pages。

线上地址：**https://aboyfeng.github.io**

## 本地开发

需要安装 Hugo extended（>= 0.146）和 git。

```bash
git clone --recurse-submodules https://github.com/aboyfeng/aboyfeng.github.io.git
cd aboyfeng.github.io
hugo server -D          # http://localhost:1313
```

如果 clone 时没加 `--recurse-submodules`：

```bash
git submodule update --init --recursive
```

## 写文章

```bash
hugo new content posts/my-new-post.md
```

PaperMod 会读取的 front matter 字段：`title`、`date`、`draft`、`author`、
`summary`、`description`、`tags`、`categories`、`showToc`、`cover`。

## 发布

推送到 `main` 分支即可。`.github/workflows/hugo.yaml` 里的流水线会用固定版本的 Hugo
构建站点，并把 `public/` 部署到 GitHub Pages。

Pages 的发布源设置为 **GitHub Actions**（Settings → Pages → Build and deployment →
Source: GitHub Actions）。

## 目录结构

```
content/
  posts/            # 博客文章
  about.md          # /about/ 关于
  archives.md       # /archives/ 归档（PaperMod 布局）
  search.md         # /search/ 站内搜索（Fuse.js）
  404.md            # 404 页面标题
hugo.yaml           # 站点配置
layouts/            # 少量主题覆盖（中文页脚）
themes/PaperMod     # git submodule
```
