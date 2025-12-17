# Copilot Instructions for Qiita Blogs

## Project Overview

This repository manages blog posts for Qiita using [@qiita/qiita-cli](https://github.com/increments/qiita-cli). Posts are written in Markdown with specific frontmatter and synchronized to Qiita via CLI commands.

## Directory Structure & Workflows

- **`drafts/`**: Work-in-progress articles not yet published (not synced to Qiita)
  - `ideas.md`: Blog ideas in Vietnamese - content focused on software philosophy, developer roles, AI impact, and project management
  - `qiita-writing-instructions.md`: Qiita Markdown syntax reference and writing best practices
  - Working draft articles (e.g., `developer-role-in-ai-era.md`)
- **`public/`**: Published articles synced to Qiita
  - `.remote/` folder is created by Qiita CLI (gitignored) - never manually edit
- **Note**: No GitHub Actions workflow exists currently - publishing is manual via `npx qiita publish`

**Critical**: Files in `public/` are two-way synced with Qiita. Always run `npx qiita pull` before editing to get latest remote changes and avoid conflicts.

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
# Create new article (generates file in public/ with frontmatter template)
npx qiita new <article-name>

# Preview locally at http://localhost:8888 (configured in qiita.config.json)
npx qiita preview

# Sync from Qiita to local (pulls remote changes) - ALWAYS run before editing public/ files
npx qiita pull

# Publish all public/ articles to Qiita (creates or updates based on id field)
npx qiita publish

# Initial setup (required once, creates .qiita-token file)
npx qiita login

# View all available commands
npx qiita help
```

**Preview configuration**: `qiita.config.json` sets `includePrivate: false`, `host: localhost`, `port: 8888`

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

1. **New article workflow**: Create with `npx qiita new <name>` in `public/` → edit → preview with `npx qiita preview` → publish with `npx qiita publish`
   - Alternatively: Draft in `drafts/` first → move to `public/` when ready → publish
2. **Editing existing**: **CRITICAL** - run `npx qiita pull` first to sync remote changes → edit file → preview → publish → commit to git
3. **Draft workflow**: Work in `drafts/` folder - files here are NOT synced to Qiita, allowing safe iteration before publication
4. **Bilingual workflow**: Vietnamese for ideation (`drafts/ideas.md`), English/Japanese for final articles

## Git Workflow

- Only `node_modules/` and `public/.remote/` are gitignored
- All articles in both `drafts/` and `public/` are committed to version control
- **No automated publishing** - manual `npx qiita publish` required after editing `public/` files
