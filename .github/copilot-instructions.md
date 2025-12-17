# Copilot Instructions for Qiita Blogs

## Project Overview

This repository manages blog posts for Qiita using [@qiita/qiita-cli](https://github.com/increments/qiita-cli). Posts are written in Markdown with specific frontmatter and synchronized to Qiita via CLI commands or GitHub Actions.

## Directory Structure & Workflows

- **`drafts/`**: Work-in-progress articles not yet published (not synced to Qiita)
- **`public/`**: Published articles synced to Qiita
  - `.remote/` folder is created by Qiita CLI (gitignored) - never edit
- **`.github/workflows/publish.yml`**: Auto-publishes on push to main/master using `QIITA_TOKEN` secret

**Critical**: Files in `public/` are two-way synced with Qiita. Always use `npx qiita pull` before editing to get latest remote changes.

## Article Frontmatter (Required)

Every article must have this YAML frontmatter structure:

```markdown
---
title: Article Title Here
tags:
  - Tag1
  - Tag2
private: false
updated_at: ''
id: null
organization_url_name: null
slide: false
ignorePublish: false
---
```

- `id: null` for new articles (Qiita CLI will populate on first publish)
- `ignorePublish: false` - set to `true` to prevent auto-publishing
- `private: true` for private drafts on Qiita

## Essential Commands

```bash
# Create new article (generates file in public/ with frontmatter)
npx qiita new <article-name>

# Preview locally at http://localhost:8888
npx qiita preview

# Sync from Qiita to local (pulls remote changes)
npx qiita pull

# Publish all public/ articles to Qiita
npx qiita publish

# Initial setup (required once, creates .qiita-token)
npx qiita login
```

## Content Guidelines

Refer to `drafts/qiita-writing-instructions.md` for:
- Qiita Markdown syntax (supports PlantUML, Mermaid diagrams)
- Code block formatting with language tags
- Table, emoji, footnote syntax
- Writing best practices (clear titles, structured content, code examples)

## Language & Content Notes

- Blog ideas tracked in `drafts/ideas.md` (Vietnamese language)
- Content topics lean toward software philosophy and project management
- Focus on developer roles, AI impact, project management practices

## Common Patterns

1. **New article workflow**: `npx qiita new` → edit in `drafts/` → move to `public/` when ready → `npx qiita publish`
2. **Editing existing**: `npx qiita pull` first → edit → commit → auto-publishes via GitHub Actions
3. **Preview before publish**: Always run `npx qiita preview` to check rendering locally
4. **Bilingual content**: Support both Vietnamese (ideas/planning) and English/Japanese (articles)

## GitHub Actions Setup

The workflow requires `QIITA_TOKEN` secret in repository settings. Get token from: https://qiita.com/settings/tokens/new

Required permissions: `read_qiita` and `write_qiita`
