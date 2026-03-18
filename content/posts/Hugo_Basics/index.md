---
title: "Hugo Basics: A Beginner's Guide to Static Sites"
date: 2026-03-18T12:00:00+05:00
draft: false
tags: ["hugo", "web", "static-sites", "tutorial"]
---

## Introduction

Hugo is one of the fastest static site generators in the world. It takes your content written in Markdown, combines it with a theme, and generates a complete website made of plain HTML files. No databases, no servers — just fast, simple websites.

In this guide, we will cover everything you need to get started with Hugo from scratch.

---

## What is a Static Site?

A static site is a website made of fixed HTML files. Unlike WordPress or other CMS platforms, there is no backend processing on every request. This makes static sites:

- **Fast** — pages load instantly
- **Secure** — no database to hack
- **Simple** — easy to host anywhere
- **Free** — platforms like GitHub Pages host them for free

---

## Installing Hugo

### On Linux (Fedora/RHEL)

```bash
sudo dnf install hugo
```

### On Linux (Ubuntu/Debian)

```bash
sudo apt install hugo
```

### On macOS

```bash
brew install hugo
```

### On Windows

```bash
winget install Hugo.Hugo.Extended
```

### Verify Installation

```bash
hugo version
```

You should see something like:
```
hugo v0.152.2+extended linux/amd64
```

---

## Creating Your First Site

```bash
hugo new site myblog
cd myblog
```

This creates the following folder structure:

```
myblog/
├── archetypes/       # default front matter templates
├── assets/           # CSS, JS, images to be processed
├── config/           # site configuration files
├── content/          # your markdown posts and pages
├── data/             # data files (JSON, YAML, TOML)
├── layouts/          # custom HTML templates
├── public/           # generated site output (auto-created)
├── static/           # files copied as-is to output
└── themes/           # your installed themes
```

---

## Adding a Theme

Hugo sites need a theme to look good. You can find themes at [themes.gohugo.io](https://themes.gohugo.io).

To add a theme using Git:

```bash
git init
git submodule add https://github.com/nunocoracao/blowfish.git themes/blowfish
```

Then set the theme in your `hugo.toml`:

```toml
theme = "blowfish"
```

---

## Site Configuration

Your main config file is `hugo.toml` (or `hugo.yaml`). Here are the most important settings:

```toml
baseURL = "https://yoursite.com/"
title = "My Blog"
defaultContentLanguage = "en"
theme = "blowfish"

enableEmoji = true
enableRobotsTXT = true
buildDrafts = false
buildFuture = false

[pagination]
  pagerSize = 10
```

| Setting | What it does |
|---|---|
| `baseURL` | Your live site URL |
| `title` | Site name shown in browser tab |
| `theme` | Which theme to use |
| `buildDrafts` | Whether to show draft posts |
| `buildFuture` | Whether to show future-dated posts |

---

## Creating Content

### Creating a New Post

```bash
hugo new posts/my-first-post.md
```

This creates `content/posts/my-first-post.md` with default front matter.

### Creating a Page

```bash
hugo new about.md
```

This creates `content/about.md`.

---

## Understanding Front Matter

Front matter is metadata at the top of every markdown file. It tells Hugo how to handle the page.

```yaml
---
title: "My First Post"
date: 2026-03-18T10:00:00+05:00
draft: false
tags: ["hugo", "tutorial"]
categories: ["web"]
description: "A short description of this post"
---
```

### Common Front Matter Fields

| Field | Description |
|---|---|
| `title` | The post title |
| `date` | Publication date |
| `draft` | If `true`, post is hidden from build |
| `tags` | List of tags for the post |
| `categories` | Category grouping |
| `description` | Short summary shown in previews |
| `weight` | Controls ordering in lists |

---

## Writing Content in Markdown

All your content is written in Markdown. Here is a quick reference:

### Headings

```markdown
# Heading 1
## Heading 2
### Heading 3
```

### Bold and Italic

```markdown
**bold text**
*italic text*
***bold and italic***
```

### Lists

```markdown
- Item one
- Item two
- Item three

1. First
2. Second
3. Third
```

### Links

```markdown
[Link Text](https://example.com)
```

### Images

```markdown
![Alt text](image.jpg)
```

### Code

Inline code: `` `code here` ``

Code block:

````markdown
```bash
echo "Hello World"
```
````

### Blockquote

```markdown
> This is a quote
```

---

## Running the Development Server

To preview your site locally:

```bash
hugo server
```

Then open your browser at `http://localhost:1313`

### Useful Server Flags

```bash
hugo server -D           # include draft posts
hugo server --buildFuture  # include future-dated posts
hugo server --bind 0.0.0.0  # accessible on local network
```

The server **hot-reloads** — any change you save is instantly reflected in the browser.

---

## Content Organization

Hugo organizes content by folders inside `content/`. Each folder becomes a **section**.

```
content/
├── _index.md        # homepage content
├── about.md         # standalone page at /about/
└── posts/
    ├── _index.md    # posts list page
    ├── post-one.md  # lives at /posts/post-one/
    └── post-two.md  # lives at /posts/post-two/
```

### The `_index.md` File

`_index.md` is a special file that adds content to **list pages** (like the homepage or a section index). Regular `.md` files are **single pages**.

---

## Taxonomies

Taxonomies are ways to group your content. Hugo supports tags and categories by default.

In your `hugo.toml`:

```toml
[taxonomies]
  tag = "tags"
  category = "categories"
```

In your post front matter:

```yaml
tags: ["hugo", "tutorial"]
categories: ["web development"]
```

Hugo automatically generates pages at `/tags/` and `/categories/` listing all grouped posts.

---

## Building Your Site

When you are ready to publish:

```bash
hugo
```

This generates your complete site into the `public/` folder. You can then upload the contents of `public/` to any web host.

```bash
hugo --minify    # minify HTML, CSS, JS for smaller file sizes
```

---

## Deploying to GitHub Pages

1. Push your Hugo project to a GitHub repository
2. Create a file at `.github/workflows/hugo.yml`
3. GitHub Actions will automatically build and deploy your site

Your `baseURL` in `hugo.toml` must match your GitHub Pages URL:

```toml
baseURL = "https://yourusername.github.io/"
```

---

## Useful Hugo Commands

| Command | What it does |
|---|---|
| `hugo new site mysite` | Create a new site |
| `hugo new posts/title.md` | Create a new post |
| `hugo server` | Start local dev server |
| `hugo server -D` | Server with drafts |
| `hugo` | Build site to `public/` |
| `hugo --minify` | Build with minification |
| `hugo version` | Check Hugo version |

---

## Conclusion

Hugo is a powerful yet beginner-friendly static site generator. Once you understand the basic structure — configuration, content, front matter, and themes — you can build fast, professional websites with very little effort.

The best way to learn is by doing. Start with a simple blog, experiment with front matter, add a few posts, and explore the theme documentation to customize your site further.

