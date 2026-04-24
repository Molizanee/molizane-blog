# Molizane Blog

[![Netlify Status](https://api.netlify.com/api/v1/badges/df65430f-6302-4941-965b-64632df3ff93/deploy-status)](https://app.netlify.com/projects/singular-lily-688cb3/deploys)

Personal blog by David Molizane. Essays, notes, and field reports. Built with Astro 6 and deployed to Netlify as a fully static site.

## Project structure

```
src/
  assets/           -- Fonts and images processed at build time
  components/       -- Reusable Astro components (header, footer, cards, etc.)
  content/
    blog/           -- Blog posts as Markdown or MDX files
  layouts/
    BlogPost.astro  -- Layout wrapper for individual posts
  pages/
    index.astro     -- Home page
    about.astro     -- About page
    blog/
      index.astro       -- Blog listing page
      [...slug].astro   -- Dynamic route for individual posts
    rss.xml.js      -- RSS feed generator
  styles/           -- Global stylesheets
  consts.ts         -- Site title and description constants
  content.config.ts -- Content collection schema (Zod validation for frontmatter)
public/             -- Static assets served as-is (favicons, OG images, etc.)
astro.config.mjs    -- Astro configuration, font providers, and integrations
```

## Content collections

Posts live in `src/content/blog/` as `.md` or `.mdx` files. The schema in `src/content.config.ts` validates frontmatter fields:

- `title` (required)
- `description` (required)
- `pubDate` (required, coerced to Date)
- `updatedDate` (optional)
- `heroImage` (optional, processed through Astro image optimization)

Adding or changing frontmatter fields requires updating the schema, otherwise builds will fail or silently drop data.

## Commands

All commands run from the project root. The package manager is Bun.

| Command              | Description                                |
| :------------------- | :----------------------------------------- |
| `bun install`        | Install dependencies                       |
| `bun dev`            | Start local dev server at `localhost:4321`  |
| `bun build`          | Build the production site to `./dist/`      |
| `bun preview`        | Preview the production build locally        |
| `bun astro check`    | Type-check Astro files and content schemas  |

## Integrations

- **@astrojs/mdx** -- MDX support for posts
- **@astrojs/sitemap** -- Generates `sitemap-index.xml` at build
- **sharp** -- Image optimization service for hero images and assets

## Fonts

Atkinson Hyperlegible is self-hosted through Astro's font API and exposed as the CSS variable `--font-atkinson`. Reference the variable in stylesheets rather than the font files directly.

## License

This project is based on the [Astro Blog starter](https://github.com/withastro/astro/tree/main/examples/blog), which draws from [Bear Blog](https://github.com/HermanMartinus/bearblog/).
