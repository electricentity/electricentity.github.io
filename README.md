# electricentity.github.io

Personal site for adventures and photography, hosted on GitHub Pages at [electricentity.com](https://www.electricentity.com). Built with [Jekyll](https://jekyllrb.com/) on the [Indigo](https://github.com/sergiokopplin/indigo) template.

## Local development

The easiest way to run the site locally is via Docker — no Ruby install required:

```sh
./bin/serve
```

Then open `http://localhost:4000`. Edits to posts, layouts, or styles auto-reload the browser.

If you'd rather use a native Ruby toolchain (matching `.ruby-version`, used in CI):

```sh
bundle install
bundle exec jekyll serve --config _config.yml,_config-dev.yml
```

## Writing a post

Add a new file to `_posts/` named `YYYY-MM-DD-Title.markdown` with front matter like:

```yaml
---
title: "Post Title"
layout: post
date: YYYY-MM-DD HH:MM
tag:
- photography
category: blog
author: michaelreeve
description: A short summary
---
```

`author` must match a key under `authors:` in `_config.yml`.

## Testing

`bundle exec rake test` builds the site and runs [HTMLProofer](https://github.com/gjtorikian/html-proofer) to catch broken links/images. This also runs in CI on every push.

## Deployment

Pushing to `main` triggers `.github/workflows/deploy.yml`, which builds the site and deploys it via GitHub Pages.
