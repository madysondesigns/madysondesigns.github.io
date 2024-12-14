# Yet another portfolio site
Finally, a simple and easy-to-grok portfolio site intended to run on GH pages. No deeply nested files, no separate theme to manage, just a sensible IA and clean content.

## Where to put things
- Case study content goes in `/_case-studies` -- `_template.md` includes necessary info
- Images go in `/assets/images`
- Personal info and resume content is in `/_data` in JSON format

## How things work
Most things are auto-generated based on filenames and paths:
- `.md` files in root are top-level pages
- HTML is rendered from files in `/_layouts` based on frontmatter property
- Helpers and partial markup live in `/_includes`
- Case studies are a custom collection with an index page

Run local dev site with `bundle exec jekyll serve --livereload`

# To do
- [x] Migrate from Hugo theme
  - [x] figure out archetypes
  - [x] migrate css
  - [x] migrate page layouts
  - [x] figure out resume json
  - [x] migrate icons
  - [x] set up breadcrumbs
  - [x] set up tags/taxonomies/terms?
  - [x] create case studies index page
  - [x] migrate case study contents
  - [x] migrate javascript
  - [x] fix favicon
- [x] why are styles broken
- [x] figure out noindex on page basis
- [x] figure out how to make a local theme
- [x] figure out how to do excerpts
- [x] better image include
- [x] update/fix left nav
- [x] clean up frontmatter metadata
- [x] update resume content
- [ ] redirect url
- [ ] add more/new case studies
  - [ ] carespace labs
  - [ ] wellsheet
  - [ ] group inboxes shared views?
- [ ] decide what to do with breadcrumbs
- [ ] tag archive pages?
- [ ] polish style/formatting
