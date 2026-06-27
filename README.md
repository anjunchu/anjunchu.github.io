# Anjun Chu Academic Website

This is a GitHub Pages-compatible Jekyll website for academic research, publications, talks, notes, and profile information.

Most updates should be made in Markdown or YAML files:

- `_data/profile.yml` for profile, affiliation, research interests, and links
- `_data/news.yml` for homepage news
- `_data/publications.yml` for publications
- `_data/publication_filters.yml` for publication filter buttons
- `_data/research_highlights.yml` for research highlight cards
- `_data/site_settings.yml` for simple visibility switches, such as showing or hiding Notes
- `_data/talks.yml` for presentations and posters
- `index.md`, `research.md`, and `notes.md` for editable page copy
- `_posts/` for longer notes or blog posts

See `CONTENT_GUIDE.md` for a practical guide to editing the site content.

Run locally on this Windows machine with:

```powershell
cd C:\Codex\PersonalWebsite
$env:PATH = "C:\Ruby40-x64\bin;$env:PATH"
jekyll build
jekyll serve
```

If the plain `jekyll` command is not found, use `C:\Ruby40-x64\bin\jekyll.bat` instead.
