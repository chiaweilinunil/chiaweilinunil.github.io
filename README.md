# chiaweilinunil.github.io

Personal academic website of **Chia-Wei Lin** — Assistante diplômée, Université de Lausanne.

Live at <https://chiaweilinunil.github.io>. Built with plain Jekyll and served by GitHub Pages; every push to `main` redeploys.

## Local preview

Requires Ruby (3.1+) and Bundler.

```bash
bundle install
bundle exec jekyll serve --livereload
```

Then open <http://localhost:4000>. (Changes to `_config.yml` need a server restart.)

## Structure

- `_config.yml` — site config: identity, navigation, social links, `news_limit`.
- `index.md`, `publications.md`, `teaching.md`, `talks.md`, `cv.md` — the pages.
- `_news/` — one Markdown file per news item (`YYYY-MM-DD-slug.md`).
- `_layouts/`, `_includes/` — templates.
- `assets/` — CSS, images, and the CV PDF.

## CV PDF

`cv.md` embeds `assets/pdf/cv.pdf`. Rebuild it from the LaTeX sources with `xelatex`
(needed for the non-Latin scripts), then copy the output to `assets/pdf/cv.pdf`.
