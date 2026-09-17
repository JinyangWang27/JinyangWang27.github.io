# Repository Guidelines

## Project Structure & Module Organization

This repository is a Jekyll academic homepage. Top-level HTML files such as `index.html` and `publications.html` define pages and select layouts. Shared page shells live in `_layouts/`; reusable Liquid fragments belong in `_includes/` and `_includes/widgets/`. Edit structured site content under `_data/`, especially `profile.yml`, `navigation.yml`, and `display.yml`. Add dated entries to `_news/`, papers to `_publications/<year>/`, and blog articles to `_posts/`. Keep browser code in `assets/js/`, styles in `assets/css/`, and images in `assets/images/`.

## Build, Test, and Development Commands

- `bundle install` installs the Ruby gems declared in `Gemfile`.
- `bundle exec jekyll serve` builds the site and starts a local preview, normally at `http://127.0.0.1:4000`.
- `bundle exec jekyll build` generates the production-ready site in `_site/` and is the primary validation command.

Pushes to `main` run `.github/workflows/jekyll.yml`, which builds and deploys the site through GitHub Pages.

## Coding Style & Naming Conventions

Use two-space indentation for YAML and Liquid markup, and four spaces in existing CSS and JavaScript files. Preserve each file's established formatting when it differs. Use lowercase, descriptive filenames; follow Jekyll's `YYYY-MM-DD-slug.md` convention for posts and the existing year directories for publications. Include valid YAML front matter in collection entries. Keep reusable markup in includes instead of duplicating it across pages. No formatter or linter is configured, so review whitespace and rendered output manually.

## Testing Guidelines

There is no automated test suite or coverage requirement. Before submitting changes, run `bundle exec jekyll build` and fix all warnings or errors. For visual changes, also preview locally and check the affected page at desktop and narrow viewport widths. Confirm navigation highlighting, links, images, and Liquid-generated content.

## Commit & Pull Request Guidelines

Recent commits use short, imperative summaries such as `add news` and `mark blog and showcase pages as unpublished`. Follow that pattern: describe one focused change without a trailing period. Pull requests should explain the purpose, list the pages or data files affected, and note the local build result. Link relevant issues and include before/after screenshots for visible layout or styling changes. Avoid committing generated `_site/`, `.jekyll-cache/`, or Bundler output.
