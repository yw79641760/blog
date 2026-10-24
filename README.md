# Neverland 🌱

> _Live fast, Love hard, Die young._

Personal digital garden and blog built with [Quartz v5](https://github.com/jackyzha0/quartz), deployed at **[blog.yanwei.xyz](https://blog.yanwei.xyz)**.

## 📖 Content Categories

| Category | Path | Description |
|----------|------|-------------|
| **Ham Radio** | `content/ham/` | Amateur radio guides, antenna theory, device reviews, QSL cards |
| **AI** | `content/ai/` | AI tooling, troubleshooting, experiments |
| **Books** | `content/book/` | Book notes and reading sheets |
| **Security** | `content/security/` | Kali Linux, security cookbooks |

## 🚀 Quick Start

```bash
# Install dependencies
npm install

# Development server (hot reload)
npm run docs

# Production build
npm run build

# Output directory: public/
```

## 🛠️ Tech Stack

- **Framework**: Quartz v5 (TypeScript, ESM)
- **Styling**: SCSS with CSS variables, Obsidian theme variant
- **Fonts**: Google Fonts (Inter, Playfair Display, JetBrains Mono)
- **Plugins**: 30+ community plugins (syntax highlighting, graph, backlinks, search, comments, etc.)
- **Analytics**: Google Analytics (GA4)
- **Comments**: Giscus (GitHub Discussions)
- **Deployment**: Static output to `public/`, deployable anywhere

## 📁 Project Structure

```
.
├── content/                 # Markdown content (source of truth)
│   ├── ham/                # Amateur radio notes
│   ├── ai/                 # AI experiments
│   ├── book/               # Book notes
│   └── security/           # Security guides
├── quartz/                 # Quartz core (vendored)
│   ├── components/         # React components (TSX)
│   ├── plugins/            # Plugin system
│   ├── styles/             # SCSS partials
│   └── i18n/               # 25+ locales
├── quartz.config.yaml      # Site configuration
├── package.json            # Scripts & dependencies
└── public/                 # Build output (gitignored)
```

## ✨ Key Features

- **SPA mode** with popovers for instant navigation
- **Graph view** (right sidebar) for note connections
- **Full-text search** with keyboard shortcut (`/`)
- **Dark/light mode** with system preference detection
- **Table of contents** (right sidebar on content pages)
- **Backlinks** and **tag pages** for discovery
- **RSS feed** and **sitemap** generation
- **Mermaid diagrams**, **LaTeX** (KaTeX), **Excalidraw** support
- **OG images** and **favicon** generation
- **CNAME** for custom domain

## 🔧 Configuration

Main config: `quartz.config.yaml`

Key sections:
- `configuration` — site metadata, theme, analytics, locale
- `plugins` — enabled/disabled plugins with options and layout positions
- `layout` — component positioning per page type

## 📝 Writing Content

Add `.md` files to `content/` with frontmatter:

```yaml
---
title: My Note
date created: 2024-01-15
date modified: 2024-01-20
tags: [tag1, tag2]
description: Brief summary for SEO/social
---
```

Supports:
- Wiki-links: `[[Other Note]]`
- Tags: `#tag` or frontmatter `tags`
- Mermaid: ````mermaid` ... ````
- LaTeX: `$inline$` or `$$block$$`
- Excalidraw: `.excalidraw.md` files

## 🌐 Deployment

```bash
npm run build    # outputs to public/
# Deploy public/ to any static host (Netlify, Vercel, Cloudflare Pages, GitHub Pages, etc.)
```

Custom domain configured via `CNAME` plugin (points to `blog.yanwei.xyz`).

## 📄 License

MIT — see `package.json` for details. Content in `content/` is personal writing.