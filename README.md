# Win95 Hugo Theme

A Windows 95-aesthetic blog theme for [Hugo](https://gohugo.io). Teal desktop background, gray beveled panels, chunky buttons, green-on-black code blocks — the full geocities-meets-Win95 experience.

Built for blogging and an about page. Nothing else.

## Features

- Raised/sunken beveled panels with classic Win95 gray chrome
- Gradient blue title bars on every section
- Win95-style navigation buttons
- Tag support with pill-style Win95 buttons
- Green-on-black terminal-style code blocks
- Pagination
- RSS feed
- Responsive (looks good on mobile too)
- Zero JavaScript, zero dependencies

## Requirements

- Hugo **v0.80.0** or later (extended edition recommended)

## Installation

### Option 1: Git submodule (recommended)

```bash
cd your-hugo-site
git submodule add https://github.com/AbhinavMir/win95-hugo.git themes/win95-hugo
```

### Option 2: Git clone

```bash
cd your-hugo-site
git clone https://github.com/AbhinavMir/win95-hugo.git themes/win95-hugo
```

### Option 3: Hugo module

Add to your `hugo.toml`:

```toml
[module]
  [[module.imports]]
    path = "github.com/AbhinavMir/win95-hugo"
```

Then run:

```bash
hugo mod init github.com/yourusername/your-site
hugo mod get
```

## Configuration

Set the theme in your `hugo.toml` (or `config.toml`):

```toml
baseURL = "https://yourdomain.com/"
languageCode = "en-us"
title = "My Website"
theme = "win95-hugo"

paginate = 5
summaryLength = 40

[params]
  description = "Welcome to my corner of the internet"
  author = "Your Name"
  startYear = 2024

[menu]
  [[menu.main]]
    name = "Blog"
    url = "/posts/"
    weight = 1
  [[menu.main]]
    name = "About"
    url = "/about/"
    weight = 2

[markup]
  [markup.highlight]
    style = "monokailight"
    noClasses = false
  [markup.goldmark]
    [markup.goldmark.renderer]
      unsafe = true

[outputs]
  home = ["HTML", "RSS"]

[taxonomies]
  tag = "tags"
  category = "categories"
```

### Parameters

| Parameter     | Description                          | Default |
|---------------|--------------------------------------|---------|
| `description` | Site tagline shown on the homepage   | —       |
| `author`      | Your name, shown in the footer       | —       |
| `startYear`   | Start year for the copyright range   | —       |

### Menu

Add items to `[menu.main]` in your config. Each item gets a Win95-style beveled button in the nav bar.

## Content Structure

```
content/
├── about.md          # About page (uses special layout)
└── posts/
    ├── _index.md     # Blog list page title
    ├── my-post.md
    └── another-post.md
```

### Creating the About page

Create `content/about.md` with this frontmatter:

```markdown
---
title: "About"
layout: "about"
type: "page"
---

Your about page content here.
```

### Creating blog posts

```bash
hugo new posts/my-new-post.md
```

Or create `content/posts/my-new-post.md` manually:

```markdown
---
title: "My New Post"
date: 2024-01-15
tags: ["example", "hello"]
draft: false
---

Post content here.
```

### Supported frontmatter

| Field    | Description                        |
|----------|------------------------------------|
| `title`  | Post title                         |
| `date`   | Publish date (`YYYY-MM-DD`)        |
| `tags`   | List of tags                       |
| `draft`  | Set `true` to hide from production |
| `author` | Per-post author override           |

## Running locally

```bash
hugo server -D
```

Open `http://localhost:1313` in your browser.

## Building for production

```bash
hugo
```

Output goes to `public/`. Deploy that folder to any static host.

## Customization

### Overriding styles

Create `static/css/custom.css` in your site and add a `head` block override in `layouts/_default/baseof.html` to include it — or just edit the theme CSS directly if you've cloned it.

### Overriding layouts

Copy any file from the theme's `layouts/` into your site's `layouts/` directory. Your copy takes precedence.

## Example site

A complete working example is included in `exampleSite/`. To run it:

```bash
cd exampleSite
hugo server --themesDir ../..
```

## License

MIT — see [LICENSE](LICENSE).
