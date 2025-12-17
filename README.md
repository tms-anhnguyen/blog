# Qiita Blogs

This repository contains my blog posts for Qiita, managed using the Qiita CLI.

## 📝 About

This project uses [@qiita/qiita-cli](https://github.com/increments/qiita-cli) to manage and publish blog posts to Qiita. All blog posts are written in Markdown and stored in the `public/` directory.

## 🚀 Getting Started

### Prerequisites

- Node.js installed on your machine
- A Qiita account
- Qiita personal access token

### Installation

```bash
npm install
```

### Authentication

Set up your Qiita personal access token:

```bash
npx qiita login
```

You'll be prompted to enter your personal access token, which you can generate from your [Qiita account settings](https://qiita.com/settings/tokens/new).

## 📖 Writing Blog Posts

### Create a New Post

```bash
npx qiita new <post-name>
```

This will create a new Markdown file in the `public/` directory with the necessary frontmatter.

### Frontmatter Structure

Each blog post should have the following frontmatter:

```markdown
---
title: Your Post Title
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

### Writing Guidelines

For detailed writing instructions and best practices, see [public/qiita-writing-instructions.md](public/qiita-writing-instructions.md).

**Key Tips:**
- Use clear and concise titles
- Structure content with proper headings
- Include code examples with syntax highlighting
- Add visuals where appropriate
- Proofread before publishing

## 🔧 Qiita CLI Commands

### Preview Posts Locally

Start a local preview server to view your posts before publishing:

```bash
npx qiita preview
```

Then open `http://localhost:8888` in your browser.

### Publish Posts

Publish all posts in the `public/` directory:

```bash
npx qiita publish
```

This will create or update posts on Qiita based on the frontmatter configuration.

### Pull Posts from Qiita

Download your existing posts from Qiita:

```bash
npx qiita pull
```

### List Commands

View all available commands:

```bash
npx qiita help
```

## 📁 Project Structure

```
qiita_blogs/
├── public/              # Blog posts (Markdown files)
│   ├── developer-role-in-ai-era.md
│   ├── qiita-writing-instructions.md
│   ├── ideas.md         # Blog post ideas
│   └── rules.md         # Communication rules
├── package.json         # Project dependencies
├── qiita.config.json    # Qiita CLI configuration
└── README.md            # This file
```

## ⚙️ Configuration

The `qiita.config.json` file contains settings for the Qiita CLI:

```json
{
  "includePrivate": false,
  "host": "localhost",
  "port": 8888
}
```

- `includePrivate`: Include private posts when pulling from Qiita
- `host`: Preview server host
- `port`: Preview server port

## 📚 Resources

- [Qiita CLI Documentation](https://github.com/increments/qiita-cli)
- [Qiita Markdown Guide](https://qiita.com/Qiita/items/c686397e4a0f4f11683d)
- [Writing Instructions](public/qiita-writing-instructions.md)

## 💡 Blog Post Ideas

See [public/ideas.md](public/ideas.md) for upcoming blog post topics and ideas.

## 📝 License

Personal blog repository - all rights reserved.
