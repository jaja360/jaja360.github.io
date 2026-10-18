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
│   │   ├── publication/ # Academic publications (also served to fr)
│   │   ├── project/     # Research projects
│   │   └── slides/      # Reveal.js presentations (also served to fr)
│   └── fr/              # French content
│       ├── _index.md    # Homepage
│       ├── courses/     # Course documentation (also served to en)
│       └── project/     # Research projects
├── static/
│   ├── en/uploads/      # English static files (resume.pdf)
│   └── fr/uploads/      # French static files (resume.pdf)
├── assets/
│   ├── css/             # Custom CSS (reveal_custom.css for slides)
│   └── media/           # Site icons and images
├── layouts/_partials/   # Custom Hugo partials (overrides theme)
├── data/                # Data files (page_sharer.yaml, authors/{me.yaml,fr/me.yaml})
├── deploy               # Build script for manual deployment
├── netlify.toml         # Netlify build configuration
├── go.mod               # Hugo modules (Go)
└── package.json         # Node dependencies (Tailwind)
```

## Content Types

### Publications (`content/en/publication/`, shared with `fr`)

Academic papers with BibTeX support:

```yaml
---
title: Paper Title
authors:
  - me                 # Site owner (data/authors/me.yaml)
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

### Projects (`content/en/project/` + `content/fr/project/`)

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

### Author Profile (`data/authors/me.yaml`, `data/fr/authors/me.yaml`)

The `me` author (key `me`, schema `hugoblox/author/v1`) is the site owner. `data/authors/me.yaml` holds the full English profile; `data/fr/authors/me.yaml` overrides only the French fields (role, bio, etc.). Edit for:
- Display name, role, affiliation
- Social profiles / IDs (Google Scholar, ORCID, links)
- Education history
- Languages and skills
- `bio` multiline text

### Slides (`content/en/slides/`, shared with `fr`)

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
      username: me
  - block: collection
    id: publications
    content:
      filters:
        folders:
          - publication
    design:
      view: citation
---
```

## Multilingual Content

- English content: `content/en/`
- French content: `content/fr/`
- Language switcher enabled in header/footer
- Default language is English with subdirectory (`/en/`, `/fr/`)
- Some sections are **shared across languages via module mounts** (`config/_default/module.yaml`), not duplicated on disk:
  - `content/en/publication` → served to `en` + `fr` (`/fr/publication/<slug>/`)
  - `content/en/slides` → served to `en` + `fr` (`/fr/slides/<slug>/`)
  - `content/fr/courses` → served to `fr` + `en` (`/en/courses/<slug>/`)
  - `content/en/project` and `content/fr/project` are NOT shared: keep both language versions in sync manually.

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

1. Create folder: `content/en/publication/author-venue-year/`
2. Add `index.md` with publication front matter
3. Add `cite.bib` with BibTeX entry
4. Add optional files: `featured.png`, `slides.pdf`, `poster.pdf`

No French copy is needed: the `content/en/publication` → `content/publication` module mount already serves these pages to `fr` (identical files, `/fr/publication/<slug>/`).

### Adding a New Project

1. Create folder: `content/en/project/project-slug/`
2. Add `index.md` with project front matter and content
3. Add `featured.png` for thumbnail
4. Add the French version under `content/fr/project/project-slug/` (projects are NOT shared by a mount)

### Updating Author Bio

Edit `data/authors/me.yaml` (English) and `data/fr/authors/me.yaml` (French overrides):
- `role`, `affiliations`, `ids`, `links`, `interests`, `education`, `languages`
- `bio` block for the biography paragraph

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
5. **Bilingual Parity**: Sections shared by mounts (publication, slides, courses) only need one copy; `project` pages need both `content/en/project/` and `content/fr/project/` versions. Missing translations won't generate cross-language links.
6. **Author References**: Use `me` to reference the site owner in publication/project `authors` lists (profile lives in `data/authors/me.yaml`).
7. **Relative Links in Publications**: Links to PDFs/files in publication front matter are relative to the publication folder, not the site root.
8. **Tailwind v4**: Uses `@tailwindcss/cli` v4.1+. Configuration differs from v3.
9. **Hugo ignores symlinks**: `content/fr/slides -> ../en/slides` and `content/en/courses -> ../fr/courses` are NOT followed by Hugo (same for the untracked `content/fr/publication -> ../en/publication`): a symlinked content dir silently produces zero pages. Cross-language sharing is done with `module.mounts` (`sites.matrix.languages`) in `config/_default/module.yaml`; add/edit mounts there, the symlinks are cosmetic only.
10. **Tailwind in security sandbox**: Hugo must be allowed to exec `tailwindcss` (`security.exec.allow` in `config/_default/hugo.yaml`), otherwise CSS builds fail with "access denied ... not whitelisted in policy security.exec.allow".

## External Resources

- [Hugo Blox Documentation](https://docs.hugoblox.com/)
- [Hugo Documentation](https://gohugo.io/documentation/)
- [Reveal.js for Slides](https://revealjs.com/)
- [Pagefind Search](https://pagefind.app/)
