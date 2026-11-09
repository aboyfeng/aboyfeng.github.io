# aboyfeng.github.io

Personal blog — [Hugo](https://gohugo.io/) + [PaperMod](https://github.com/adityatelange/hugo-PaperMod),
published to GitHub Pages by GitHub Actions.

Live at **https://aboyfeng.github.io**

## Local development

Requires Hugo extended (>= 0.146) and git.

```bash
git clone --recurse-submodules https://github.com/aboyfeng/aboyfeng.github.io.git
cd aboyfeng.github.io
hugo server -D          # http://localhost:1313
```

If you cloned without `--recurse-submodules`:

```bash
git submodule update --init --recursive
```

## Writing

```bash
hugo new content posts/my-new-post.md
```

Front matter fields used by PaperMod: `title`, `date`, `draft`, `author`,
`summary`, `description`, `tags`, `categories`, `showToc`, `cover`.

## Publishing

Push to `main`. The workflow in `.github/workflows/hugo.yaml` builds the site
with the pinned Hugo version and deploys `public/` to GitHub Pages.

Pages is configured to deploy from **GitHub Actions** (Settings → Pages →
Build and deployment → Source: GitHub Actions).

## Layout

```
content/
  posts/            # blog posts
  about.md          # /about/
  archives.md       # /archives/ (PaperMod layout)
  search.md         # /search/   (Fuse.js client-side search)
hugo.yaml           # site config
themes/PaperMod     # git submodule
```
