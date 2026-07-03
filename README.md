# chiaweilinunil.github.io

Personal academic website of **Chia-Wei Lin** — Assistante diplômée, Université de Lausanne.

Live site: <https://chiaweilinunil.github.io>

Built as a minimal Jekyll site. No remote theme, no plugins beyond what GitHub Pages already runs — pure Markdown/HTML/CSS so it deploys with zero configuration on the GitHub Pages side.

---

## Preview locally

You need Ruby (3.1+) and Bundler. On Windows the easiest path is [RubyInstaller](https://rubyinstaller.org/) with the MSYS2 dev kit.

```bash
bundle install
bundle exec jekyll serve --livereload
```

Then open <http://localhost:4000>.

If you don't want to install Ruby locally, just push to the `main` branch — GitHub Pages will build the site and you can preview at the live URL.

---

## Editing the site

The site is structured so you only ever touch Markdown / YAML files.

### Site identity (name, photo, social links, navigation)

Edit [`_config.yml`](_config.yml). Sections of interest:

- `title`, `tagline`, `description`, `author` — site-wide metadata.
- `me:` — your hero block (position, affiliation, photo path, CV path).
- `socials:` — list of profile links shown under your photo on the home page. Add or remove entries; order is preserved.
- `nav:` — the top navigation. Each item has `title` and `url`.
- `news_limit` — how many news items the home page shows (default 5).

### Adding a news item

Create a new file in `_news/` named `YYYY-MM-DD-slug.md`:

```markdown
---
date: 2026-03-15
---
Short Markdown text. Links work, *italics* and **bold** work, footnotes don't.
```

The home page sorts by `date` descending and shows the most recent `news_limit` items. Older items keep living in the folder for the record.

### Adding a publication

Open [`publications.md`](publications.md). Publications are grouped by year inside `<div class="pub-group">` blocks. Copy an existing `<li class="entry">` block, change the year/title/authors/DOI, and put it under the right year group (or add a new `<div class="pub-group">` for a new year).

If you want your name highlighted, wrap it in `<span class="self">Lin, Chia-Wei</span>`.

### Adding a talk, workshop, course

Same pattern — open [`talks.md`](talks.md) or [`teaching.md`](teaching.md), copy an existing `<li class="entry">` and edit. The two columns are `<span class="when">` (date) and `<span class="what">` (title + venue + meta).

### Updating bio / research interests

[`index.md`](index.md) is the about-page text. [`research.md`](research.md) is the longer research page.

---

## Updating the CV PDF

The `/cv/` page embeds `assets/pdf/cv.pdf`. To rebuild it from the LaTeX sources in `Prompt and materials/CV_Academia_20260127/`:

```bash
cd "Prompt and materials/CV_Academia_20260127"
xelatex Main.tex
biber Main
xelatex Main.tex
xelatex Main.tex
cp Main.pdf "../../chiaweilinunil.github.io/assets/pdf/cv.pdf"
```

`xelatex` is required (the CV uses non-Latin scripts through fontspec / polyglossia). Until `cv.pdf` exists the `/cv/` page will fall back to a "download" link only.

---

## Replacing the profile photo

Put a square image at `assets/img/prof_pic.jpg`. The CSS crops it to a 140 px circle, so a square original works best.

---

## File map

```text
_config.yml            site config (identity, nav, socials)
Gemfile                Ruby dependencies for local preview
index.md               About page (home)
publications.md        Publications page
teaching.md            Teaching page
talks.md               Talks & workshops page
research.md            Research narrative
cv.md                  CV page (embeds assets/pdf/cv.pdf)
_news/                 One Markdown file per news entry
_layouts/              default.html, home.html, page.html
_includes/             head.html, header.html, footer.html, socials.html
assets/css/style.css   All styling
assets/img/            Profile photo and other images
assets/pdf/            CV PDF lives here
```

---

## Things deliberately left out (v1)

Blog, dark mode, language switcher, comments, analytics. The bones are simple — any of these can be added later without rewriting the layout.

## TODOs

- [ ] Compile and place `assets/pdf/cv.pdf` (see above).
- [ ] Replace the bio paragraphs in [`index.md`](index.md) and [`research.md`](research.md) with whatever wording you prefer.
- [ ] Trim the starter `_news/` entries you don't want.
- [ ] Add an ORCID link to `socials:` in `_config.yml` once you have one.
