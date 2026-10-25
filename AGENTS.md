# AGENTS.md

This is a personal digital garden/blog built with **Quartz v5**. It is deployed at **blog.yanwei.xyz**.

## Project Identity

- Type: Quartz static site generator (digital garden)
- Language: TypeScript (ESM), Markdown content
- Framework version: Quartz 5.0.0
- Domain: `blog.yanwei.xyz` (CNAME)
- Author: Wei YAN (Hangzhou) — ham radio operator `BR5AI` / `BG5FUE`
- Content license: personal writing

## Key Directories

| Path                 | Purpose                                                  |
| -------------------- | -------------------------------------------------------- |
| `content/`           | Markdown source of truth (ham, ai, book, security)       |
| `quartz/`            | Vendored Quartz core (components, plugins, styles, i18n) |
| `quartz.config.yaml` | Site config — the single source of behavior              |
| `package.json`       | Scripts, deps, engines (Node ≥22, npm ≥10.9.2)           |
| `public/`            | Build output (do not edit)                               |

## Common Commands

```bash
npx quartz build          # production build to public/
npx quartz build --serve  # dev server (hot reload)
npm run docs              # same as above, outputs to docs/
npm run check             # tsc --noEmit && prettier --check
npm run format            # prettier --write
npm run test              # tsx --test (unit tests under quartz/**/*.test.ts)
npm run install-plugins   # install @quartz-community/* plugins into node_modules
```

## Content Rules

- All notes live in `content/` as `.md` with YAML frontmatter (`title`, `date created`, `date modified`, optional `tags`/`description`).
- Ignore patterns: `private`, `templates`, `.obsidian` (from `quartz.config.yaml`).
- Wiki-links `[[Note]]` resolve across the vault.
- Mermaid diagrams and KaTeX math are enabled.
- Images go under `content/` next to the referencing note; relative paths work.
- Ham radio category: `content/ham/` (+ `qsl/` subfolder). Do not reclassify without checking `quartz.config.yaml` tag-page/folder-page settings.

## Configuration Editing

1. Edit `quartz.config.yaml` (schema validated by `./quartz/plugins/quartz-plugins.schema.json`).
2. Plugin order and layout `position`/`priority` matter — check sibling entries before moving a component.
3. Theme overrides use CSS variables; SCSS partials live in `quartz/styles/` (`variables.scss`, `custom.scss`, `callouts.scss`, `syntax.scss`, `base.scss`).
4. React components are TSX under `quartz/components/` — check existing registry pattern (`registry.ts`) before adding new components.

## Verification Standards

- **Never** run checks just to confirm user-reported failures — user observation is ground truth.
- After config/component changes: `npm run check` (type + prettier), then `npm run docs` to smoke-test the dev server.
- Keep diffs minimal: delete dead weight, prefer boring design over abstraction, no unnecessary allocation/copying in compiled code paths.
- Do not add tests for wiring/forwarding/trivial defaults. Add tests only for genuine edge cases or at user request.

## Repo-Specific Constraints

- `engines`: Node ≥22, npm ≥10.9.2 — do not target older runtimes.
- Private package (`private: true`) — do not publish.
- Prettier enforced (`npm run check` includes prettier `--check`).
- `@quartz-community/*` plugins resolved via `quartz/plugins/loader/install-plugins.ts` (runs on `prebuild`).
- `quartz.lock.json` pins plugin versions — update it when adding/removing plugins.

## Gotchas / Pitfalls

- **`backlinks` requires `crawl-links` to be enabled.** The `backlinks` component reads `file.data.links`, which is only populated by the `crawl-links` transformer. If `crawl-links` is `enabled: false` in `quartz.config.yaml`, backlinks will always render nothing (it silently returns `null` due to `hideWhenEmpty: true`). Always enable both together:

  ```yaml
  - source: "@quartz-community/crawl-links"
    enabled: true
    options:
      markdownLinkResolution: shortest
    order: 60
  - source: "@quartz-community/backlinks"
    enabled: true
    layout:
      position: right
      priority: 45
  ```

- Backlinks only appear on pages that have incoming wiki-links (`[[Note]]`). Plain Markdown links `[text](url)` do not count. If no page links to the current note, the backlinks section is hidden.

## What to Avoid

- No new top-level conventions that duplicate Quartz patterns.
- No shims/aliases for removed code; clean cutover only.
- No markdown in `quartz.lock.json` or `package-lock.json` edits by hand.
- No background services, scripts, or animation in SVG outputs.
- No `<foreignObject>` or external `href` in SVGs.
