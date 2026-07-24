# Imaging AI Lab website (Jekyll)

This site uses Jekyll includes so the header, navigation, and footer live in
one place (`_includes/`) instead of being duplicated in every page.

## Structure

```
_config.yml          site settings
_includes/header.html   shared <head>, header banner, and nav bar
_includes/footer.html   shared contact footer + closing scripts
_layouts/default.html   wraps every page with header + content + footer
index.html            Home / About  (nav: about)
research.html          (nav: research)
projects.html          (nav: projects)
teaching.html          (nav: teaching)
education.html         (nav: education)
publications.html      (nav: publications)
positions.html          (nav: positions)
images/                add your existing images/ folder here
styles.css              add your existing stylesheet here
CV-Craig-Jones-2025-05.pdf   add your CV file here
```

## How it works

Each page file (e.g. `research.html`) starts with YAML front matter:

```yaml
---
layout: default
title: "Research"
nav: research
---
```

`layout: default` tells Jekyll to wrap the page's content with
`_layouts/default.html`, which pulls in `_includes/header.html` and
`_includes/footer.html`. `nav: research` tells the header include which nav
link to mark `active`. `title` fills in `<title>{{ page.title }} - Imaging AI Lab</title>`.

To add a new page, copy an existing one, change `title`/`nav` in the front
matter, add a corresponding `<li>` in `_includes/header.html`, and write your
content below the `---`.

## Before deploying

1. Copy your existing `images/` folder and `styles.css` into this directory.
2. Copy `CV-Craig-Jones-2025-05.pdf` into this directory (or update the path
   in `index.html` if it lives elsewhere).
3. In `_config.yml`:
   - If this repo will be served as `https://<username>.github.io` (a **user/org
     Pages site**, repo named `<username>.github.io`), leave `baseurl: ""`.
   - If this repo will be served as `https://<username>.github.io/<repo-name>`
     (a **project Pages site**), set `baseurl: "/<repo-name>"`.
4. Push to GitHub and enable Pages (Settings → Pages → Deploy from a branch).
   GitHub Pages runs Jekyll automatically — no build step required on your end.

## Testing locally (optional)

If you have Ruby installed:

```bash
gem install bundler jekyll
bundle init
bundle add jekyll
bundle exec jekyll serve
```

Then visit `http://localhost:4000`.
