# AGENTS.md

Guidelines for maintaining this academic research website.

## Project Goal

Build a GitHub Pages-compatible personal academic website for Anjun Chu. The site should feel modern, calm, readable, and research-focused. Content updates should be possible through Markdown or structured data files without editing HTML templates.

## Content and Design Separation

- Put page content in Markdown files or collection/data files.
- Put reusable page structure in layouts and includes.
- Put visual styling in CSS/Sass only.
- Do not hard-code publications, news items, talks, navigation entries, or profile details inside HTML layouts when they can live in Markdown, YAML, or collection files.
- When adding a new page, prefer creating a Markdown file with front matter and an existing layout.
- If a new layout or include is needed, keep it generic enough to reuse.

## Recommended Content Model

- Home page: Markdown front matter for profile metadata and Markdown body for short editable sections.
- News: use a data file such as `_data/news.yml`.
- Publications: use a data file such as `_data/publications.yml` or a collection such as `_publications/`.
- Talks and posters: use `_data/talks.yml` or a collection.
- CV or PDFs: store files under `assets/pdfs/` and link to them from data/Markdown.
- Images: store stable images under `assets/images/`; avoid remote hotlinking for core profile assets.
- Blog or notes: use `_posts/` only if a blog remains part of the site.

## Design Direction

- Prioritize legibility, fast scanning, and a professional academic tone.
- Use a restrained color palette with strong typography and generous spacing.
- Avoid decorative clutter, oversized marketing-style sections, and theme-heavy visual effects.
- Make the first screen immediately identify the researcher, field, affiliation, research areas, and primary links.
- Publication entries should expose title, authors, venue/year, links, and selected/highlighted status when useful.
- Ensure the site works well on mobile and desktop.

## GitHub Pages Compatibility

- Prefer a standard Jekyll setup that GitHub Pages can build without custom deployment unless the project intentionally switches to GitHub Actions.
- Keep dependencies minimal.
- Avoid build steps that require unsupported plugins unless a GitHub Actions workflow is added.
- Preserve MathJax or KaTeX support for research/blog pages that use equations.

## Editing Rules

- Do not overwrite user content without checking the current file first.
- Keep changes focused; do not refactor unrelated pages during small content updates.
- Maintain accessible headings, link text, image alt text, and keyboard-friendly navigation.
- Test locally after template or styling changes when possible.
- Check generated pages for broken internal links after moving content or assets.

## Future Agent Workflow

1. Read this file before making website changes.
2. Inspect the existing content files before editing templates.
3. Decide whether the requested change belongs in content, layout, styling, or configuration.
4. Prefer content-only edits for profile, news, publication, talk, CV, and page additions.
5. Run a local build or dev server after structural changes and report any warnings.

