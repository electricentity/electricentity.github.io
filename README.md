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

`./bin/new-post "Post Title"` scaffolds `_posts/YYYY-MM-DD-Post-Title.markdown` with the front matter below pre-filled. `author` must match a key under `authors:` in `_config.yml`.

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

## Adding photos

Export your picks from Lightroom to a local folder as JPEGs, then run:

```sh
./bin/upload-photos <post-slug> <path-to-exported-jpegs>
```

This uploads the folder to Cloudflare R2 (`img.electricentity.com`) and prints a ready-to-paste markdown block for the post body — no resizing or recompression, whatever you export is what gets served. Requires `rclone` (`brew install rclone`) configured once with an `r2` remote pointing at the R2 bucket's API credentials (Cloudflare dashboard → R2 → Manage API tokens).

## Testing

`bundle exec rake test` builds the site and runs [HTMLProofer](https://github.com/gjtorikian/html-proofer) to catch broken links/images. This also runs in CI on every push.

## Deployment

Pushing to `main` triggers `.github/workflows/deploy.yml`, which builds the site and deploys it via GitHub Pages.
