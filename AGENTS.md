# AGENTS.md

Agent-focused documentation for working in this codebase.

## Project Overview

Academic CV website for Jaël Champagne Gareau, built with **Hugo** and **Hugo Blox** (formerly Wowchemy). Bilingual site (English/French) deployed to both Netlify and GitHub Pages.

- **Live site**: https://www.jaelgareau.com/
- **Hugo Blox version**: 0.11.0
- **Hugo version**: 0.152.2
- **Package manager**: pnpm (10.14.0)

## Commands

### Development

```bash
# Start local dev server with live reload
pnpm dev
# or: hugo server --disableFastRender

# Build for production (outputs to public/)
pnpm build
# or: hugo --minify

# Full production build with search indexing
./deploy
# Runs: hugo --gc --minify && pnpm dlx pagefind --site "public"
```

### Dependencies

```bash
# Install Node dependencies (Tailwind CSS)
pnpm install

# Update Hugo modules
hugo mod get -u
hugo mod tidy
```

### Hugo Modules

Hugo modules are managed via `go.mod`. Key modules:
- `github.com/HugoBlox/kit/modules/blox` - Core Hugo Blox components
- `github.com/HugoBlox/kit/modules/slides` - Reveal.js slides support
- `github.com/HugoBlox/kit/modules/integrations/netlify` - Netlify integration

## Project Structure

```
├── config/_default/     # Hugo configuration (YAML)
│   ├── hugo.yaml        # Core Hugo settings
│   ├── params.yaml      # Hugo Blox parameters (theme, SEO, analytics)
│   ├── languages.yaml   # i18n config (en, fr)
│   ├── menus.en.yaml    # English navigation
│   ├── menus.fr.yaml    # French navigation
│   └── module.yaml      # Hugo module imports and mounts
├── content/
│   ├── en/              # English content
│   │   ├── _index.md    # Homepage (landing page with blocks)
│   │   ├── authors/     # Author profiles (admin/ is the site owner)
│   │   ├── publications/# Academic publications
│   │   ├── projects/    # Research projects
│   │   ├── slides/      # Reveal.js presentations
│   │   └── courses/     # Course documentation
│   └── fr/              # French content (mirrors en/ structure)
├── static/
│   ├── en/uploads/      # English static files (resume.pdf)
│   └── fr/uploads/      # French static files (resume.pdf)
├── assets/
│   ├── css/             # Custom CSS (reveal_custom.css for slides)
│   └── media/           # Site icons and images
├── layouts/_partials/   # Custom Hugo partials (overrides theme)
├── data/                # Data files (page_sharer.yaml for social sharing)
├── deploy               # Build script for manual deployment
├── netlify.toml         # Netlify build configuration
├── go.mod               # Hugo modules (Go)
└── package.json         # Node dependencies (Tailwind)
```

## Content Types

### Publications (`content/{lang}/publications/`)

Academic papers with BibTeX support:

```yaml
---
title: Paper Title
authors:
  - admin              # References content/authors/admin
  - Co-author Name
publication_types:
  - paper-conference   # or: article-journal, thesis, etc.
publication: 'Conference/Journal Name'
publication_short: 'CONF 2024'
date: '2024-01-01'
tags: [Tag1, Tag2]
projects: [project-folder-name]  # Links to projects

hugoblox:
  ids:
    doi: '10.xxxx/xxxxx'

links:
  - type: code
    url: 'code.zip'     # Relative to publication folder
  - type: slides
    url: 'slides.pdf'
---

Abstract text here.
```

Include supporting files in the publication folder: `cite.bib`, `featured.png`, PDFs.

### Projects (`content/{lang}/projects/`)

```yaml
---
title: Project Name
summary: Brief description
tags: [Tag1, Tag2]
date: "2024-01-01"

image:
  caption: Image description
  focal_point: Smart

links:
  - type: code
    url: 'https://github.com/...'
---

Markdown content describing the project.
```

### Author Profile (`content/{lang}/authors/admin/`)

The `admin` author is the site owner. Edit `_index.md` for:
- Display name, role, organization
- Social profiles (GitHub, LinkedIn, Google Scholar, ORCID)
- Education history
- Languages and skills
- Bio text (below the front matter)

### Slides (`content/{lang}/slides/`)

Reveal.js presentations using Hugo shortcodes:

```yaml
---
title: Presentation Title
slides:
  theme: black
  highlight_style: dracula
  reveal_options:
    slide_number: c/t
    mouse_wheel: true
---

## Slide 1

Content

---

## Slide 2

{{< slide background-image="./figs/image.png" >}}
```

Use `---` to separate slides. Place supporting images in a `figs/` subfolder.

### Homepage (`content/{lang}/_index.md`)

Landing page built with Hugo Blox blocks:

```yaml
---
type: landing
sections:
  - block: resume-biography-3
    content:
      username: admin
  - block: collection
    id: publications
    content:
      filters:
        folders:
          - publications
    design:
      view: citation
---
```

## Multilingual Content

- English content: `content/en/`
- French content: `content/fr/`
- Both languages share the same structure
- Language switcher enabled in header/footer
- Default language is English with subdirectory (`/en/`, `/fr/`)

When adding content, create matching files in both language directories.

## Configuration

### Main Settings (`config/_default/params.yaml`)

Key Hugo Blox settings under `hugoblox:`:
- `identity`: Site name, description, social accounts
- `theme`: Color mode (system/light/dark), typography
- `header/footer`: Navigation style, search, language switcher
- `comments`: Giscus configuration
- `analytics`: Google Analytics, Clarity

### Navigation (`config/_default/menus.{lang}.yaml`)

```yaml
main:
  - name: Bio
    url: /
    weight: 10
  - name: Papers
    url: /#publications
    weight: 20
```

## Deployment

### Netlify (Primary)

Configured in `netlify.toml`:
- Builds with Hugo 0.152.2, Node 22
- Runs `pnpm install` + `hugo --gc --minify` + `pagefind` indexing
- Uses `netlify-plugin-hugo-cache-resources` for caching

### GitHub Pages

Configured in `.github/workflows/deploy.yml`:
- Triggers on push to `main`
- Same build process as Netlify
- Deploys to GitHub Pages

### Manual Build

```bash
./deploy
```

Builds site and generates Pagefind search index. Rsync command (commented) available for custom server deployment.

## Styling

- **CSS Framework**: Tailwind CSS v4
- **Custom CSS**: `assets/css/reveal_custom.css` for slide styling
- **Theme**: Configured in `params.yaml` under `hugoblox.theme`

## Common Tasks

### Adding a New Publication

1. Create folder: `content/en/publications/author-venue-year/`
2. Add `index.md` with publication front matter
3. Add `cite.bib` with BibTeX entry
4. Add optional files: `featured.png`, `slides.pdf`, `poster.pdf`
5. Create French version in `content/fr/publications/` if needed

### Adding a New Project

1. Create folder: `content/en/projects/project-slug/`
2. Add `index.md` with project front matter and content
3. Add `featured.png` for thumbnail
4. Create French version

### Updating Author Bio

Edit `content/en/authors/admin/_index.md`:
- Front matter: education, organizations, social links
- Body: Bio paragraph

### Adding a Presentation

1. Create folder: `content/en/slides/presentation-name/`
2. Add `index.md` with Reveal.js configuration
3. Add images in `figs/` subfolder
4. Use `---` to separate slides

## Gotchas

1. **Hugo Modules**: Run `hugo mod get -u` to update modules when Hugo Blox releases updates
2. **Pagefind Search**: Search index must be rebuilt after content changes. The `./deploy` script handles this automatically.
3. **Git Info**: `enableGitInfo: true` in hugo.yaml means Hugo uses git commit dates. Ensure proper git history.
4. **Image Processing**: Hugo caches processed images in `resources/`. This folder is git-ignored but cached in CI.
5. **Bilingual Parity**: Keep `content/en/` and `content/fr/` in sync. Missing translations won't generate cross-language links.
6. **Author References**: Use `admin` to reference the site owner in publication/project `authors` lists.
7. **Relative Links in Publications**: Links to PDFs/files in publication front matter are relative to the publication folder, not the site root.
8. **Tailwind v4**: Uses `@tailwindcss/cli` v4.1+. Configuration differs from v3.

## External Resources

- [Hugo Blox Documentation](https://docs.hugoblox.com/)
- [Hugo Documentation](https://gohugo.io/documentation/)
- [Reveal.js for Slides](https://revealjs.com/)
- [Pagefind Search](https://pagefind.app/)
