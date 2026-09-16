---
name: update-github-info
description: Keep the GitHub Info page current with practical updates from GitHub Blog and Changelog sources.
on:
  schedule: daily
  workflow_dispatch:
permissions:
  contents: read
  pull-requests: read
engine: copilot
tools:
  github:
    toolsets: [repos]
  edit:
  web-fetch:
network:
  allowed:
    - defaults
    - github.blog
    - github.com
    - awesome-copilot.github.com
safe-outputs:
  create-pull-request:
    title-prefix: "[github-info] "
    draft: true
    max: 1
---

# Update GitHub Info

Read `notes/mona-notes.md` before making any changes and follow its guidance:

- Keep summaries short and practical.
- Prefer updates that help developers learn GitHub faster.
- Mention the source for every update, identifying whether it came from the GitHub Blog or GitHub Changelog.
- Publish changes through a pull request for Mona to review.

Use `web-fetch` to read both:

- https://github.blog/latest/
- https://github.blog/changelog/
- https://awesome-copilot.github.com/workflows/

Review the latest relevant items from those pages and update `site/content/github-info.md` with concise, useful information for developers. Add relevant Awesome Copilot workflows to the sources alongside GitHub Blog and Changelog updates. Preserve the existing document structure and style where possible, avoid duplicate items, and include source links for new content.

After editing the file, inspect the diff for accuracy, source attribution, and unintended changes. Use the `create-pull-request` safe output to open one draft pull request for Mona to review. The pull request title and body should briefly summarize the updates and identify the Blog or Changelog sources used. Do not write directly to the default branch.