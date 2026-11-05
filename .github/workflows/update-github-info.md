---
name: update-github-info
description: Keep Mona's GitHub Info content current with official GitHub updates.
on:
  schedule: daily
  workflow_dispatch:
permissions:
  contents: read
  pull-requests: read
engine:
  id: copilot
  copilot-sdk: true
tools:
  edit:
  github:
    toolsets: [repos]
  web-fetch:
network:
  allowed:
    - github.blog
    - github.com
safe-outputs:
  create-pull-request:
    max: 1
---

# Update GitHub Info

Keep Mona's GitHub Info website current using official GitHub sources.

## Instructions

1. Read `notes/mona-notes.md` with the GitHub repository tools and follow its editorial guidance.
2. Read the current `site/content/github-info.md` with the GitHub repository tools before making changes.
3. Use `web-fetch` to fetch `https://github.blog/latest/`.
4. Use `web-fetch` to fetch `https://github.blog/changelog/`.
5. Identify the most useful recent blog and changelog updates for developers. Keep summaries short and practical, and include the source for every update.
6. Edit `site/content/github-info.md` with the selected, source-linked updates. Preserve useful existing context and avoid duplicating entries.
7. Review the diff for accuracy, concise writing, valid Markdown, and links that point to the official GitHub Blog or Changelog.
8. Use the `create-pull-request` safe output to open a pull request for Mona to review. Do not write directly to `main`.

The pull request should explain which updates were added and cite their official source URLs.