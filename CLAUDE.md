# CLAUDE.md

## Overview

This is a **GitHub profile repository**. Because the repo name (`danielpalenicek`)
matches the owner's GitHub username, the contents of `README.md` are rendered on
the owner's GitHub profile page at https://github.com/danielpalenicek.

There is no application code, build system, test suite, or dependency manifest.
The entire repository is a single Markdown file. Do not invent build/test/lint
workflows — none exist.

## Structure

```
.
├── README.md    # Profile bio + Publications list shown on the GitHub profile page
├── CLAUDE.md    # This file (guidance for AI assistants; not shown on the profile)
└── assets/      # Publication thumbnails (SVG source + rasterized PNG)
```

### Publication thumbnails

Each publication in `README.md` is paired with a thumbnail in `assets/`. The
workflow used so far:

- Author the thumbnail as an SVG (`assets/<name>.svg`) — dark gradient
  background, title, authors, and a small illustrative panel.
- Rasterize to PNG for reliable GitHub rendering with cairosvg:
  `python3 -c "import cairosvg; cairosvg.svg2png(url='assets/<name>.svg', write_to='assets/<name>.png', output_width=1200, output_height=675)"`
  (cairosvg / Pillow may need `pip install`).
- Reference the PNG (not the SVG) from the README and link the image to the
  paper's arXiv abstract page.
- Note: arXiv hosts are typically blocked from the sandbox, so paper metadata
  may need to come from web search rather than fetching the page directly;
  verify titles/authors before publishing.

## Working in this repo

- The deliverable is almost always an edit to `README.md`.
- `README.md` uses GitHub Flavored Markdown. GitHub supports a limited subset of
  HTML and a fixed emoji set; verify any fancy formatting renders on github.com
  rather than assuming it works.
- Keep the tone consistent with the existing bio (first-person, friendly).
- `CLAUDE.md` is internal guidance only — it does not appear on the profile, so
  it never needs to be kept "presentable" for visitors.

## Conventions

- Commit messages in history are short and imperative (e.g. "Update README.md").
  Follow that style.
- There is nothing to run or verify locally beyond previewing Markdown rendering.
