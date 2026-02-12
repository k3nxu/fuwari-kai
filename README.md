# Fuwari (Theme Repository)

[![Deploy with GitHub Actions](https://github.com/saicaca/fuwari/actions/workflows/deploy.yml/badge.svg)](https://github.com/saicaca/fuwari/actions/workflows/deploy.yml)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

> **Note**: This is the **Theme Repository** containing the source code and logic. For writing content and configuring your site, please use the **Content Repository**.

## 🚀 Architecture

Fuwari adopts a **Separation of Concerns** architecture:

-   **Theme Repo (This)**: Contains Astro components, layouts, styles, and logic.
-   **Content Repo ([Astro_Fuwari_Content](https://github.com/k3nxu/Astro_Fuwari_Content))**: Contains your Markdown posts, images, and site configuration.

During deployment, the Content Repo overlays its files onto the Theme Repo, ensuring a clean separation between "System" and "User Data".

## 🛠 Usage

**Do not fork this repository to start your blog.**

1.  Fork or Use the [Content Repository Template](https://github.com/k3nxu/Astro_Fuwari_Content).
2.  Write your posts in `src/content/posts/`.
3.  Configure your site in `src/config.ts` (in the Content Repo).
4.  Push to `main` branch to trigger the automatic build and deployment.

## ⚙️ Configuration

The site configuration is managed in `src/config.ts`. We use a unified `Config` object structure.

### Structure

```typescript
// src/config.ts (in Content Repo)

const Config = {
  site: {
    title: "My Blog",
    lang: "en",
    banner: { enable: true, src: "..." },
    favicon: [ ... ]
  },
  profile: {
    name: "User",
    bio: "Bio...",
    links: [ ... ]
  },
  mappings: {
    tags: { 'demo': '演示' },
    categories: { 'examples': '示例' }
  }
}
```

### Key Options

-   **site.banner**: Enable/Disable the homepage banner.
-   **site.favicon**: Array of favicons (supports light/dark mode switching).
-   **mappings**: Map English slugs (URL) to Display Names (UI).
    -   `tags`: `/tags/demo/` -> Display as "演示"
    -   `categories`: `/categories/examples/` -> Display as "示例"

## 📂 Directory Structure

```
.
├── src/
│   ├── components/     # Astro components
│   ├── layouts/        # Page layouts
│   ├── pages/          # Routing logic (SSG)
│   ├── utils/          # Helper functions
│   ├── config.ts       # Config definition (Default values)
│   └── content/        # (Empty in Theme) Content placeholder
├── public/             # Static assets
└── astro.config.mjs    # Astro configuration
```

## 📝 License

This project is licensed under the MIT License.
