# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is the Lethean documentation website built with MkDocs Material. The site is hosted at https://lt.hn and documentation content lives in the `docs/` folder as Markdown files.

## Commands

### Development Server
```shell
mkdocs serve                              # Basic local server
CI=true INSIDERS=true mkdocs serve        # With paid features enabled
```
Visit: http://127.0.0.1:8000/

### Build & Clean
```shell
mkdocs build    # Build static site to ./site
make clean      # Remove ./site directory
```

### Install Dependencies
```shell
pip install mkdocs-material mkdocs-git-revision-date-localized-plugin mkdocs-git-committers-plugin-2 mkdocs-material[imaging]
```

For image processing features, also install system dependencies:
```shell
sudo apt-get install libcairo2-dev libfreetype6-dev libffi-dev libjpeg-dev libpng-dev libz-dev pngquant
```

## Architecture

- **docs/**: Markdown content files organized by section (getting-started, network, sdk, updates, web3)
- **mkdocs.yml**: Site configuration, navigation, theme settings, and plugins
- **overrides/**: Custom Jinja2 templates extending the base Material theme (announcement bar, custom JS/CSS)
- **docs/assets/**: Images and custom stylesheets

## Deployment

Merging PRs to `main` automatically deploys to the documentation website. Tagged releases (v*) trigger the CI workflow to build and create a downloadable documentation.zip.

## Key Plugins

The site uses several MkDocs plugins configured in mkdocs.yml:
- Blog (for updates section)
- Git revision date and committers
- Tags with listings
- Search with highlighting
- Social cards and image optimization
