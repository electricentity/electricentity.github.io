# electric entity

Personal site hosted on GitHub Pages (electricentity.com), primarily for posts about adventures and photography. Built with Jekyll on the Indigo template.

## Structure
- `_posts/` — blog entries (`YYYY-MM-DD-Title.markdown`). `author:` front matter must match a key under `authors:` in `_config.yml`.
- `_config.yml` — site settings, author info, plugin list, feature toggles (most are commented out/disabled).
- `_layouts/`, `_includes/`, `_sass/` — Indigo template views/styles.
- `assets/images/` — site images, including favicons.
- `about.md`, `projects.html` — unfinished/unused pages, currently excluded from the build via `_config.yml`'s `exclude:` list.

## Working locally
`./bin/serve` runs the site via Docker (no local Ruby needed) at `http://localhost:4000` with livereload. See README.md for the native-Ruby alternative.
`./bin/new-post "Title"` scaffolds a new post file. `./bin/upload-photos <slug> <folder>` uploads a folder of Lightroom-exported JPEGs to Cloudflare R2 (`img.electricentity.com`) and prints ready-to-paste post markdown — requires a one-time local `rclone config` (see README.md).

## CI/deploy
`.github/workflows/deploy.yml` builds and deploys on push to `main` via GitHub Pages' "Actions" source (not the legacy branch-based Pages build).
