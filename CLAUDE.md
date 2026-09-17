# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This is a Jekyll-based personal academic homepage (`JinyangWang27.github.io`), built from the [academic-homepage](https://github.com/luost26/academic-homepage) template. It is deployed to GitHub Pages via a custom Actions workflow (not the default GitHub Pages Jekyll build).

## Commands

```bash
bundle install          # install gems (first time / after Gemfile changes)
bundle exec jekyll serve   # run locally with live reload, e.g. http://127.0.0.1:4000
bundle exec jekyll build   # static build into _site/
```

There is no test suite or linter in this repo.

## Deployment

`.github/workflows/jekyll.yml` builds with `bundle exec jekyll build --baseurl "..."` and deploys to GitHub Pages on every push to `main`. Do not rely on GitHub's built-in Pages Jekyll build — this custom workflow is what actually runs.

## Content model (data-driven pages)

Almost all page content lives in YAML under `_data/`, not in the HTML/layout files:

- `_data/profile.yml` — name, tagline phrases, bio, positions, education, experience, peer reviews, social links (email/github/linkedin/orcid/gscholar). Edit this for personal info changes.
- `_data/navigation.yml` — navbar entries. The `name` field must match a page's `navbar_title` front-matter value or the active-page highlight breaks.
- `_data/display.yml` — homepage section toggles (`show_experience`, `show_news`, `show_selected_publications`, `num_news`) and footer text.
- `_data/authors.yml` — canonical author name → URL/display overrides, referenced from publication entries.

Collections (defined in `_config.yml`) hold individual content items as markdown files with front matter:
- `_publications/` — one file per paper.
- `_news/` — dated news items shown on the homepage.
- `_showcase/` (collection currently commented out in `_config.yml`).

`_posts/` holds blog posts (blog page is currently unpublished — see `_data/navigation.yml`, both Blog and Showcase are commented out).

## Templates

- `_layouts/default.html` — base HTML shell: loads Bootstrap/FontAwesome/Academicons/KaTeX from CDN plus `assets/css/global.css` and `assets/js/*.js`, includes `navbar.html`/`footer.html`, and renders `{{ content }}`.
- `_layouts/blog_post.html`, `_layouts/prompt.html` — other page layouts.
- `_includes/navbar.html`, `_includes/footer.html`, `_includes/widgets/` — reusable partials.

Top-level `.html` files (`index.html`, `publications.html`, `blog.html`, `showcase.html`) are thin pages that set front matter (layout, `navbar_title`, etc.) and pull in data/collections via Liquid.

## Adding content

- New publication: add a markdown file to `_publications/` following the existing front-matter shape of files in that directory.
- New news item: add a markdown file to `_news/`.
- To re-enable Blog/Showcase: uncomment the relevant lines in `_data/navigation.yml` and `_config.yml`'s `collections` list.
