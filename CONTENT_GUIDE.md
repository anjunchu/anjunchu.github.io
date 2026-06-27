# Content Editing Guide

This website is designed so most updates happen in Markdown or YAML files. You should rarely need to edit files in `_layouts`, `_includes`, or `assets/css` unless you want to change the design or page structure.

## Quick Preview

From PowerShell:

```powershell
cd C:\Codex\PersonalWebsite
$env:PATH = "C:\Ruby40-x64\bin;$env:PATH"
jekyll build
jekyll serve
```

Then open:

```text
http://127.0.0.1:4000/
```

If `jekyll build` cannot overwrite a file inside `_site`, delete the `_site` folder manually and build again.

For a no-risk build check that does not touch `_site`, use:

```powershell
$dest = Join-Path $env:TEMP "personalwebsite-check"
jekyll build --destination $dest
```

## Profile And Homepage

Edit `_data/profile.yml` for:

- Name
- Title
- Affiliation
- Location
- Profile image
- Email
- Links
- Research interests
- Short homepage summary

The profile image should live in `assets/images/`. Update `image` and `image_alt` together so the site remains accessible.

Example:

```yaml
image: /assets/images/authorimage.png
image_alt: "Portrait of Anjun Chu"
```

Edit `index.md` for the main editable homepage text below the profile information.

## News

Edit `_data/news.yml`.

Add the newest item at the top:

```yaml
- date: 2026-06-26
  text: "Started a new project on ..."
  url: https://example.com
```

If there is no link, leave `url:` blank.

## Publications

Edit `_data/publications.yml`.

Add new publications near the top, usually newest first. Keep the same field names:

```yaml
- title: "Paper title"
  authors: "**Anjun Chu**, Coauthor One, and Coauthor Two"
  venue: "Journal or arXiv information"
  year: 2026
  status: "Preprint"
  doi: https://doi.org/example
  arxiv: https://arxiv.org/abs/example
  pdf: /assets/pdfs/example.pdf
  supplement:
  selected: true
  groups:
    - selected-paper
    - theory-work
    - quantum-simulation
```

Put PDFs in `assets/pdfs/` and link them with paths beginning `/assets/pdfs/`.

The filter buttons at the top of the Publications page are controlled by `_data/publication_filters.yml`.

Example filter:

```yaml
- label: "Quantum Simulation"
  group: quantum-simulation
```

To make a publication appear when that button is clicked, add the same group id under that paper:

```yaml
groups:
  - quantum-simulation
```

The `Selected Papers` button uses `selected: true`, so you do not need to manually maintain that filter.

To add, remove, rename, or reorder publication filter buttons, edit `_data/publication_filters.yml`. To control which papers appear for a button, edit the `groups` list in `_data/publications.yml`.

## Talks And Posters

Edit `_data/talks.yml`.

Example:

```yaml
- title: "Talk title"
  event: "Conference name"
  type: "Oral Presentation"
  year: 2026
  location: "City, State"
  slides: /assets/pdfs/talk-slides.pdf
  poster:
```

Store slides and posters in `assets/pdfs/`.

Talks appear on the standalone `talks.md` page. They are no longer embedded in the research page.

## Research Page

Edit `research.md` for research descriptions, themes, and longer prose. Use Markdown headings:

```markdown
## Research Theme

Paragraph text here.
```

Research highlight cards are controlled by `_data/research_highlights.yml`.

Example:

```yaml
- title: "Research highlight title"
  kicker: "Short label"
  image: /assets/images/highlight-image.png
  image_background: "#071827"
  image_alt: "Brief description of the highlight image"
  summary: >-
    One paragraph describing the research direction, the physical platform, the
    main idea, and why it matters.
  selected: true
  links:
    - label: Related papers
      url: /publications/
```

Put highlight images in `assets/images/`. Use `selected: true` for highlights that should appear on the homepage. Use `selected: false` for highlights that should only appear on the research page.

Use `image_background` to control the color behind images that do not fill the whole image box. Any CSS color works, such as `"#071827"`, `"#ffffff"`, or `transparent`.

## Hiding Or Showing Notes

Edit `_data/site_settings.yml`.

To hide Notes from the top navigation:

```yaml
show_notes: false
```

To show Notes again:

```yaml
show_notes: true
```

The notes page and posts stay in the project either way; this switch only controls whether the Notes link appears in navigation.

## Notes Or Blog Posts

Edit `notes.md` for the notes landing page.

Add new long-form notes in `_posts/` using this filename format:

```text
YYYY-MM-DD-short-title.md
```

Each post should start with front matter:

```markdown
---
layout: post
title: "Post Title"
math: true
---
```

Use `math: true` only when the post needs MathJax for equations.

## Navigation

Edit `_data/navigation.yml` to add, remove, or reorder top navigation links. Each navigation item can include a `key`, which lets templates apply simple visibility rules.

For a new page, create a Markdown file such as `cv.md`:

```markdown
---
layout: page
title: CV
permalink: /cv/
---

Page content here.
```

Then add it to `_data/navigation.yml`:

```yaml
- text: CV
  key: cv
  url: /cv/
```

## Before Committing

Run:

```powershell
jekyll build
git status
```

Commit only source files, content files, and intentional assets. Do not commit `_site`, `.bundle`, `vendor`, `bin`, `.agents`, `.codex`, `PersonalWebsite-*`, or annotation-review helpers.

## Pushing To GitHub

Before the first push, remove the local backup folder from Git tracking while keeping it on your computer:

```powershell
git rm -r --cached PersonalWebsite-20260626-161136
```

Then check the files that will be committed:

```powershell
git status --short
```

Commit the current website source:

```powershell
git add .
git commit -m "Update academic website"
```

If the branch is still named `master`, rename it to `main`:

```powershell
git branch -M main
```

Create or choose a GitHub repository. For the main GitHub Pages user site, the repository should usually be named:

```text
anjunchu.github.io
```

Connect this local repo to GitHub:

```powershell
git remote add origin https://github.com/anjunchu/anjunchu.github.io.git
```

Push:

```powershell
git push -u origin main
```

On GitHub, enable Pages from the repository settings if needed. For a user site named `anjunchu.github.io`, GitHub Pages normally serves from the default branch automatically.
