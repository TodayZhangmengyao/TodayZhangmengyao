# 个人主页 & 阅读清单

一个简洁学术风的静态网站，纯 HTML/CSS/JS，零依赖。

## 文件结构

```
site/
├── index.html                   ← 首页（自我介绍 + 工作论文）
├── analytical/index.html        ← 分析模型阅读清单
├── field-experiments/index.html ← 田野实验阅读清单
├── notes/
│   ├── index.html               ← 笔记列表页
│   └── example-post.html        ← 一篇示例笔记
└── assets/
    ├── style.css                ← 所有样式（共享）
    └── portrait.jpg             ← 你的头像（自己放进来）
```

## 本地预览

直接双击 `index.html` 在浏览器里打开就行，或者在 `site/` 目录里跑：

```bash
python3 -m http.server 8000
# 然后浏览器打开 http://localhost:8000
```

## 怎么改内容

### 1. 改自我介绍

打开 `index.html`，所有需要替换的地方都是 `___` 或 `Your Name`、`example.edu` 这种占位符，搜索替换即可。

### 2. 加头像

把你的头像图片重命名成 `portrait.jpg` 放进 `assets/`，然后把 `index.html` 里的：

```html
<div class="portrait">PORTRAIT</div>
```

替换成：

```html
<img class="portrait" src="assets/portrait.jpg" alt="Portrait" />
```

### 3. 加一篇阅读清单条目

在 `analytical/index.html` 或 `field-experiments/index.html` 里照着这个格式复制粘贴：

```html
<div class="entry">
  <span class="authors">作者A, 作者B.</span>
  <span class="title">论文标题.</span>
  <span class="venue">期刊名, 卷(期):页码, 年份.</span>
  <span class="tag">foundational</span>     <!-- 可选标签 -->
  <div class="links-row">
    <a href="https://doi.org/...">DOI</a>
    <a href="...">PDF</a>
  </div>
  <p class="note">一句话评论：为什么这篇值得读。</p>
</div>
```

### 4. 加一篇笔记

- 在 `notes/` 目录里照着 `example-post.html` 复制一份，比如叫 `2026-06-some-topic.html`
- 在 `notes/index.html` 里加一项 `<li>` 指向这个新文件

## 发布到 GitHub Pages

1. 把整个 `site/` 目录里的内容推到一个 GitHub 仓库（比如叫 `your-username.github.io` —— 这样就是你的主域名）
2. Settings → Pages → Source 选 `main` 分支根目录
3. 几分钟后 `https://your-username.github.io/` 就能访问

如果仓库名不是 `your-username.github.io`，访问地址是 `https://your-username.github.io/仓库名/`。

## 调色

所有颜色都在 `assets/style.css` 顶部的 `:root` 里，集中改一处全站生效：

- `--accent` 主强调色（默认深红 `#8b2a2a`）——改成藏青 `#1e3a5f`、墨绿 `#2d5a3d` 都好看
- `--bg` 背景色
- `--serif` 正文字体——目前是 Crimson Pro，想换 EB Garamond / Source Serif 改这里就行
