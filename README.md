# aojie.space

林奥杰的个人研究站点，聚焦**数字艺术金融**与**文化数字资产**。

- **框架**：Astro 5
- **样式**：学术极简风（衬线字体 + 黑白灰 + 中国红）
- **托管**：Cloudflare Pages（计划）
- **域名**：aojie.space（阿里云注册 + Cloudflare 解析）
- **部署**：Git push → Cloudflare Pages 自动构建

## 目录结构

```
.
├── astro.config.mjs       # Astro 配置（含 site、locale、integrations）
├── package.json
├── tsconfig.json
├── .gitignore
├── .node-version          # 锁定 Node.js 20
├── public/                # 静态资源（favicon、robots.txt）
└── src/
    ├── content.config.ts  # Content Collections schema
    ├── styles/global.css  # 全局样式
    ├── layouts/           # 布局组件
    ├── components/        # 可复用 UI 组件
    ├── pages/             # 路由
    └── content/posts/     # Markdown 文章
```

## 本地开发

```bash
# 1. 安装依赖（首次）
npm install

# 2. 启动开发服务器（热更新）
npm run dev

# 浏览器打开 http://localhost:4321
```

## 构建静态站点

```bash
npm run build
# 输出在 dist/ 目录
```

## 添加新文章

1. 在 `src/content/posts/` 下新建 `.md` 文件
2. 文件名用英文或中文，例：`ai-valuation-2026.md` 或 `数字艺术金融-时代之问.md`
3. 必须包含以下 frontmatter：

```yaml
---
title: '文章标题'
description: '一句话简介（用于 SEO 和卡片展示）'
pubDate: 2026-09-12     # 发布日期
category: '研究笔记'    # 可选
tags: ['NFT', 'RWA']    # 可选
draft: false             # true 时不发布
---
```

4. 写 Markdown 正文即可

## 推送到 GitHub

```bash
# 1. 在 GitHub 上创建空仓库：aojie-site
#    （不要勾选 README / .gitignore / License）

# 2. 初始化并推送
git init
git add .
git commit -m "init: aojie.site v0.1"
git branch -M main
git remote add origin https://github.com/<你的用户名>/aojie-site.git
git push -u origin main
```

## 部署到 Cloudflare Pages

1. Cloudflare Dashboard → **Workers & Pages** → **Create** → **Pages** → **Connect to Git**
2. 选 aojie-site 仓库
3. 配置：
   - **Framework preset**：Astro
   - **Build command**：`npm run build`
   - **Build output directory**：`dist`
4. 点 **Save and Deploy**
5. 部署完成后 → **Custom domains** → 添加 `aojie.space`

## 域名解析（阿里云 → Cloudflare）

如果尚未改 NS（阶段 1）：

1. Cloudflare 添加站点后会给两个 NS
2. 阿里云控制台 → 域名 → aojie.space → DNS 修改
3. 把现有 NS 改为 Cloudflare 给的两个
4. 等待 5-60 分钟生效

## License

- **代码**：MIT
- **内容**（文章、图片）：CC BY-NC 4.0（保留署名 + 非商业使用）

© 2026 林奥杰
