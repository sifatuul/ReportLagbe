# Report Lagbe

A GitHub Pages home for lab-report helper tools.

## Structure

- `index.html` — dynamic home/discovery page
- `tools/` — individual report generators and utilities
- Add future `.html` tools anywhere under `tools/`; the home page discovers them automatically.

## Automatic discovery

The home page uses the GitHub API to:
1. read the repository tree,
2. find HTML tool pages,
3. classify them from their filenames,
4. fetch each page's latest commit date,
5. show newest/updated tools first.

Change `owner`, `repo`, or `branch` in `index.html` if needed.

## Current tool

`tools/mme302-exp08-09-graph-maker.html` — the existing MME 302 graph maker, converted from the original root index page.


## Performance architecture

The home page does **not** call the GitHub API. It reads `tools.json`, so normal visitors do not consume GitHub API rate limits.

A GitHub Actions workflow regenerates `tools.json` whenever a tool HTML file changes. The browser therefore makes one tiny static-file request instead of one repository request plus one commit-history request per tool.
