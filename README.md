# Ashutosh Bajpai's Quarto Blog

This blog is built using [Quarto](https://quarto.org/), a powerful open-source scientific and technical publishing system.

## Deployment Process

This blog is automatically deployed using GitHub Actions whenever changes are pushed to the main branch. Here's how it works:

1. The workflow is defined in [.github/workflows/publish.yml](.github/workflows/publish.yml)
2. When changes are pushed to `main`, GitHub Actions:
   - Checks out the repository
   - Sets up UV (fast Python package installer)
   - Sets up Python using the version specified in `.python-version`
   - Installs Jupyter and other dependencies (required for Quarto pages that contain code)
   - Sets up Quarto
   - Renders the Quarto documents and publishes to the `gh-pages` branch

The rendered site is then served via GitHub Pages from the `gh-pages` branch.

### Manual Deployment

To manually trigger deployment:

1. Go to the "Actions" tab in the repository
2. Select the "Quarto Publish" workflow
3. Click "Run workflow" and select the branch to deploy from

### Local Preview

To preview the blog locally, run:

```bash
quarto preview
```

## Installation

1. Install [Quarto](https://quarto.org/docs/get-started/)
2. Install Python dependencies:
   ```bash
   pip install -r requirements.txt
   # or if using uv:
   uv sync
   ```

## Creating New Posts

Create a new folder in the `posts/` directory with the format `YYYY-MM-DD-title-slug/` and add an `index.qmd` file:

```markdown
---
title: "Your Post Title"
author: "Ashutosh Bajpai"
date: "2025-01-01"
categories: [Category1, Category2]
---

Your content here...
```

## Useful Commands

```bash
# Preview locally
quarto preview

# Build the site
quarto render

# Shrink PNG files
brew install pngquant
for file in *.png; do pngquant --force --output "$file" --quality 60-80 "$file"; done
```
