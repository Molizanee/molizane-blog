# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

Package manager is **Bun** (see `bun.lock`). Node `>=22.12.0` is required.

- `bun install` — install dependencies
- `bun dev` — local dev server at `localhost:4321`
- `bun build` — production build to `./dist/`
- `bun preview` — preview the production build
- `bun astro check` — type-check `.astro` files and content collections (no `tsc` script is wired up; this is the canonical typecheck)
- `bun astro add <integration>` — add an Astro integration (updates `astro.config.mjs`)

There is no test runner, linter, or formatter configured in `package.json`.

## Architecture

This is an **Astro 6** static blog built from the official `blog` starter. Output is fully static; there is no SSR adapter.

### Content collections are the source of truth for posts

`src/content.config.ts` defines a single `blog` collection loaded via `glob({ base: './src/content/blog', pattern: '**/*.{md,mdx}' })`. The zod schema requires `title`, `description`, `pubDate` (coerced to `Date`) and allows optional `updatedDate` and `heroImage` (typed via Astro's `image()` helper so hero images get optimized at build time).

When adding/changing post frontmatter fields, update the schema in `src/content.config.ts` — otherwise `getCollection('blog')` consumers (`src/pages/blog/index.astro`, `src/pages/blog/[...slug].astro`, `src/pages/rss.xml.js`) will type-error or silently drop fields.

### Site identity lives in two places

- `src/consts.ts` — `SITE_TITLE`, `SITE_DESCRIPTION` (imported by layouts, RSS, `<BaseHead>`)
- `astro.config.mjs` — the `site` URL used for canonical links, sitemap, and RSS absolute URLs (currently the placeholder `https://example.com`)

Both must be updated when rebranding.

### Fonts are self-hosted via Astro's font API

`astro.config.mjs` registers the Atkinson Hyperlegible font through `fontProviders.local()` against files in `src/assets/fonts/`, exposed as the CSS variable `--font-atkinson`. Use that variable in CSS rather than referencing the font files directly.

### Integrations

`@astrojs/mdx` (so posts can be `.md` or `.mdx`) and `@astrojs/sitemap` (emits `sitemap-index.xml` at build). `sharp` is the image service used by `image()` in the content schema.

### Layout & routing conventions

- `src/pages/` → file-based routes. `src/pages/blog/[...slug].astro` renders individual posts by wrapping MDX/MD content in `src/layouts/BlogPost.astro`.
- `src/pages/rss.xml.js` generates the feed by iterating `getCollection('blog')` — any new post fields that should appear in RSS must be passed through here explicitly.
- `src/components/BaseHead.astro` centralizes `<head>` (canonical URL, OG tags, font preloads). New global `<head>` concerns go here rather than in individual pages.

## Design direction

`design-prd.md` describes the target **"Aura" Minimalist Blog** design system (typography pairing, color tokens like `Soft Pearl #FAFAFA` / `Electric Indigo #4F46E5`, component specs for cards, inline subscribe, split article hero, etc.). The current code is still the unmodified Astro starter — styling work should be implemented against that PRD, not invented ad-hoc.
