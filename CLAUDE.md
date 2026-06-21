# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is **Daevlog** - a personal technical blog built with AstroPaper theme (Astro static site generator). Deployed at https://daily-kim.github.io

## Tech Stack

- **Framework**: Astro 5.x
- **Styling**: TailwindCSS 4.x
- **Type Checking**: TypeScript
- **Linting**: ESLint with `eslint-plugin-astro`
- **Code Formatting**: Prettier (with Astro & Tailwind plugins)
- **Search**: Pagefind (static search)
- **Icons**: Tabler Icons (SVG)
- **Deployment**: GitHub Pages

## Commands

```bash
# Install dependencies
pnpm install

# Start dev server
pnpm run dev

# Build for production (includes type check, build, and Pagefind generation)
pnpm run build

# Preview production build locally
pnpm run preview

# Type check only
pnpm run sync

# Format code
pnpm run format

# Format check
pnpm run format:check

# Lint
pnpm run lint
```

## Architecture

### Content Structure
- Blog posts stored in `src/data/blog/` as Markdown files
- Content schema defined in `src/content.config.ts` using Astro Content Collections
- Each post has frontmatter: `title`, `description`, `pubDatetime`, `tags`, `featured`, `draft`, `ogImage`

### Key Configuration Files
- `src/config.ts` - Site configuration (title, author, domain, SEO settings)
- `src/constants.ts` - Social links and other constants
- `astro.config.ts` - Astro configuration (integrations, markdown settings, Shiki transformers)
- `src/content.config.ts` - Blog collection schema

### Layouts (`src/layouts/`)
- `Layout.astro` - Base layout with HTML structure
- `Main.astro` - Main page layout wrapper
- `PostDetails.astro` - Blog post detail layout
- `AboutLayout.astro` - About page layout

### Components (`src/components/`)
- `Header.astro`, `Footer.astro` - Site header/footer
- `Card.astro` - Blog post card component
- `Breadcrumb.astro` - Navigation breadcrumbs
- `Pagination.astro` - Post pagination
- `ShareLinks.astro` - Social share buttons
- `Tag.astro` - Tag display component

### Pages (`src/pages/`)
- `index.astro` - Homepage with featured + recent posts
- `posts/` - All posts listing with pagination
- `tags/` - Tags listing page
- `archives/` - Archives by year
- `search.astro` - Search page
- `about.md` - About page (Markdown)
- `og.png.ts` - Dynamic OG image generation
- `rss.xml.ts` - RSS feed generation
- `robots.txt.ts` - Robots.txt generation

### Utilities (`src/utils/`)
- `getSortedPosts.ts` - Sort posts by date
- `getPostsByTag.ts` - Filter posts by tag
- `slugify.ts` - URL slug generation
- `postFilter.ts` - Filter out drafts/scheduled posts

## Adding New Blog Posts

1. Create a new `.md` file in `src/data/blog/`
2. Include required frontmatter:
   ```yaml
   ---
   title: "Post Title"
   description: "Post description for SEO"
   pubDatetime: 2026-04-22T10:00:00Z
   tags: ["tag1", "tag2"]
   featured: false
   draft: false
   ---
   ```
3. Write content in Markdown
4. Run `pnpm run dev` to preview locally

## Customization

- **Color schemes**: TailwindCSS custom properties in `src/styles/global.css`
- **Site metadata**: Edit `src/config.ts`
- **Social links**: Edit `src/constants.ts`
- **OG images**: Set `dynamicOgImage: true` in config for automatic generation
