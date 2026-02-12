# Fuwari (主题仓库)

[![Deploy with GitHub Actions](https://github.com/saicaca/fuwari/actions/workflows/deploy.yml/badge.svg)](https://github.com/saicaca/fuwari/actions/workflows/deploy.yml)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

> **注意**：这是包含源代码和逻辑的 **主题仓库 (Theme Repository)**。如需撰写文章和配置站点，请使用 **内容仓库 (Content Repository)**。

## 🚀 架构说明

Fuwari 采用了 **代码与内容分离 (Separation of Concerns)** 的架构：

-   **Theme Repo (本仓库)**: 包含 Astro 组件、布局、样式和逻辑代码。
-   **Content Repo ([Astro_Fuwari_Content](https://github.com/k3nxu/Astro_Fuwari_Content))**: 包含你的 Markdown 文章、图片资源以及站点配置文件。

在部署过程中，Content Repo 的文件会覆盖到 Theme Repo 上，从而确保“系统逻辑”与“用户数据”的清晰分离。

## 🛠 使用方法

**请不要直接 Fork 本仓库来开始你的博客。**

1.  Fork 或使用 [内容仓库模板 (Content Repository Template)](https://github.com/k3nxu/Astro_Fuwari_Content)。
2.  在 `src/content/posts/` 目录下撰写文章。
3.  在 `src/config.ts` (内容仓库中)配置你的站点。
4.  推送到 `main` 分支，GitHub Actions 会自动触发构建和部署。

## ⚙️ 配置说明

站点配置位于 `src/config.ts`。我们采用了统一的 `Config` 对象结构。

### 配置结构

```typescript
// src/config.ts (位于内容仓库)

const Config = {
  site: {
    title: "我的博客",
    lang: "zh_CN",
    banner: { enable: true, src: "..." },
    favicon: [ ... ]
  },
  profile: {
    name: "用户名",
    bio: "个人简介...",
    links: [ ... ]
  },
  mappings: {
    tags: { 'demo': '演示' },        // URL用英文，显示用中文
    categories: { 'examples': '示例' }
  }
}
```

### 关键选项

-   **site.banner**: 启用或禁用首页 Banner。
-   **site.favicon**: Favicon 数组 (支持深色/浅色模式切换)。
-   **mappings**: 将英文 Slug (URL) 映射为显示名称 (UI)。
    -   `tags`: 访问 `/tags/demo/` -> 页面显示 "演示"
    -   `categories`: 访问 `/categories/examples/` -> 页面显示 "示例"

## 📂 目录结构

```
.
├── src/
│   ├── components/     # Astro 组件
│   ├── layouts/        # 页面布局
│   ├── pages/          # 路由逻辑 (SSG)
│   ├── utils/          # 工具函数
│   ├── config.ts       # 配置定义 (默认值)
│   └── content/        # (主题仓库为空) 内容占位符
├── public/             # 静态资源
└── astro.config.mjs    # Astro 配置
```

## 📝 许可协议

本项目采用 MIT 许可证。
