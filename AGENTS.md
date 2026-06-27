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
- Keep review-only helpers out of the public build. Annotation tools are useful during design review, but should not be included from `_layouts/default.html` or committed for production.

## Recommended Content Model

- Home page: Markdown front matter for profile metadata and Markdown body for short editable sections.
- News: use a data file such as `_data/news.yml`.
- Publications: use a data file such as `_data/publications.yml` or a collection such as `_publications/`.
- Publication filter buttons live in `_data/publication_filters.yml`; group membership lives in each publication's `groups` list.
- Talks and posters: use `_data/talks.yml` or a collection.
- CV or PDFs: store files under `assets/pdfs/` and link to them from data/Markdown.
- Images: store stable images under `assets/images/`; avoid remote hotlinking for core profile assets.
- Blog or notes: use `_posts/` only if a blog remains part of the site.
- Research highlights: use `_data/research_highlights.yml`; homepage visibility is controlled by each entry's `selected` field.
- Simple visibility switches belong in `_data/site_settings.yml`; currently `show_notes` controls whether Notes appears in navigation.

## Design Direction

- Prioritize legibility, fast scanning, and a professional academic tone.
- Use a restrained color palette with strong typography and generous spacing.
- Avoid decorative clutter, oversized marketing-style sections, and theme-heavy visual effects.
- Make the first screen immediately identify the researcher, field, affiliation, research areas, and primary links.
- Publication entries should expose title, authors, venue/year, links, and selected/highlighted status when useful.
- Publication cards should not show topic chips by default. Use top-of-page filter buttons from `_data/publication_filters.yml` and each paper's `groups` list instead.
- Ensure the site works well on mobile and desktop.

## GitHub Pages Compatibility

- Prefer a standard Jekyll setup that GitHub Pages can build without custom deployment unless the project intentionally switches to GitHub Actions.
- Keep dependencies minimal.
- Avoid build steps that require unsupported plugins unless a GitHub Actions workflow is added.
- Preserve MathJax or KaTeX support for research/blog pages that use equations.

## Local Windows Workflow

- This project has been tested on Windows with Ruby installed at `C:\Ruby40-x64`.
- If `ruby`, `bundle`, or `jekyll` are not visible in the shell, prepend Ruby to `PATH` for that session:

  ```powershell
  $env:PATH = "C:\Ruby40-x64\bin;$env:PATH"
  ```

- The command that successfully built the site in this workspace was:

  ```powershell
  C:\Ruby40-x64\bin\jekyll.bat build
  ```

- `bundle exec jekyll build` may fail on this Windows install with `command not found: jekyll` even when the Jekyll gem is installed. In that case, use `jekyll build` or the full `C:\Ruby40-x64\bin\jekyll.bat build` command.
- If building into `_site` fails with a Windows permission error on an existing generated file, the source may still be fine. Either delete `_site` manually and rebuild, or test with a fresh destination:

  ```powershell
  C:\Ruby40-x64\bin\jekyll.bat build --destination "$env:TEMP\personalwebsite-check"
  ```

- For local viewing outside Codex, run:

  ```powershell
  C:\Ruby40-x64\bin\jekyll.bat serve
  ```

- In the Codex sandbox, background Jekyll serving may fail because detached processes and `_site` rewrites can be restricted. A working fallback is to build the site, then serve the already-built `_site` folder with a small static server.

## Clean GitHub Publish Rules

- Do not commit generated or local-runtime folders: `_site`, `.bundle`, `vendor`, `bin`, `.agents`, `.codex`.
- Do not commit the timestamped backup folder `PersonalWebsite-20260626-161136`; it is local recovery material, not site source.
- Do not commit review-only annotation helpers unless the user explicitly asks for public annotation support.
- Keep `AGENTS.md`, `CONTENT_GUIDE.md`, and `README.md` excluded from Jekyll output through `_config.yml`; they can remain repository documentation.
- Before pushing, run a clean build to a fresh destination when `_site` has Windows permission locks:

  ```powershell
  $dest = Join-Path $env:TEMP "personalwebsite-check"
  C:\Ruby40-x64\bin\jekyll.bat build --destination $dest
  ```

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
6. Do not delete the backup folder `PersonalWebsite-20260626-161136` unless the user explicitly asks. It is excluded from Jekyll builds and should be untracked before GitHub push.
7. Keep generated/local tooling folders out of the published site: `_site`, `.bundle`, `vendor`, `bin`, `.agents`, and `.codex` should not be committed or published.
