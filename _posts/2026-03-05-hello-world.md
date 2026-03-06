---
title: "Hello, World — Getting Started with GitHub Pages"
date: 2026-03-05
tags: [github, devops]
summary: "A quick walkthrough of how this blog was set up using plain HTML and CSS, pushed via GitHub CLI from a dev machine."
---

Every blog needs a first post, so here it is. This site is hosted on **GitHub Pages** — free, fast, and zero infrastructure to manage.

## How it was set up

The repo is named `physercoe/physercoe.github.io`. GitHub automatically serves any repo with that naming pattern at `https://physercoe.github.io`. No build step, no CI pipeline — just push Markdown and it's live (Jekyll does the rest).

## Writing posts

Posts live in the `_posts/` directory as Markdown files named `YYYY-MM-DD-slug.md`. Each file starts with YAML frontmatter:

```yaml
---
title: "Your Post Title"
date: 2026-03-05
tags: [tag1, tag2]
summary: "One-line excerpt shown on the home page."
---
```

Everything after the frontmatter is standard Markdown — written in Obsidian, pushed to GitHub, published automatically.

## Pushing with GitHub CLI

After enabling Pages in the repo settings, deploying is just:

```bash
git add .
git commit -m "new post"
git push origin main
```

GitHub builds the site automatically via Jekyll. No local build needed.

## Next steps

- Add more posts
- Wire up a custom domain (optional)
- Customise the Jekyll theme
