# How this site works

A Jekyll site. GitHub Pages builds it on push — there is no toolchain to
install, no CI to configure, and no `_site/` committed to the repo.

## Publishing a post

1. Copy `_posts/TEMPLATE.md.example` to `_posts/YYYY-MM-DD-slug.md`.
   **The date prefix in the filename is required** — Jekyll uses it to decide
   the post is a post.
2. Fill in the front matter. `title`, `date`, and `section` are the only
   required fields; `subtitle` and `summary` are shown on the index.
3. Write in Markdown (GitHub-flavoured — tables, fenced code, footnotes).
4. Commit and push. The URL is `/<slug>/`, taken from the filename.

That is the whole workflow. Nothing else needs touching.

## Sections

Posts are grouped on the index by their `section:` field. The groups and their
order live in `_config.yml`:

```yaml
sections:
  - id: essays
    label: Essays
  - id: notes
    label: Notes
```

Add an entry there and posts with that `id` get their own heading. A post with
no `section` defaults to `notes`. A section with no posts is not rendered.

Rough division of labour: **essays** are long, structured, and meant to be
re-read. **notes** are shorter — one finding, one argument, one correction.

## House style

The site's only real editorial rule, and the reason it exists:

> If a claim cannot be checked, it does not go in.

Which in practice means:

- **State the prior.** What did you expect before you looked? Write it down
  before the evidence, so the evidence can contradict it.
- **Keep the "where I was wrong" section.** It is the highest-value part of any
  post and the first thing you will want to cut. Cutting it turns the post into
  content.
- **Link the sources.** Not as credentialling — so a reader can go check and
  find you wrong.
- **Separate inference from data.** Say which is which, explicitly. Most bad
  writing is a datum and a conclusion wearing the same clothes.
- **No motivational register.** No "unlock", "game-changer", "10x". If a
  sentence would survive being deleted, delete it.

## Local preview (optional)

Not required — pushing is faster. But if you want it:

```bash
bundle install
bundle exec jekyll serve   # http://localhost:4000/Grow/
```

If Ruby is a nuisance, skip it. Push to a branch and let GitHub Pages build a
preview instead.

## Layout of the repo

```
_config.yml                site config, section definitions
index.html                 the index page (bio + grouped listing)
feed.xml                   Atom feed, hand-written, no plugin
_layouts/default.html      shell: head, masthead, footer
_layouts/post.html         post header + prose wrapper
_posts/                    the writing lives here
_posts/TEMPLATE.md.example starting point for a new post
assets/css/main.css        all the styling, ~300 lines, no framework
```

## Deployment

This repo is `rishabharora-kk/blog`. It is a **project** repo, not a GitHub user
site -- a user site must be named `<username>.github.io` exactly. So the site
serves under a subpath:

```
https://rishabharora-kk.github.io/blog/
```

and `baseurl` in `_config.yml` must match the repo name exactly. **If you rename
the repo, change `baseurl` in the same commit** or every link and stylesheet
404s, silently:

| Repo name | baseurl | Serves at |
|---|---|---|
| `blog` (current) | `"/blog"` | `https://rishabharora-kk.github.io/blog/` |
| `notes` | `"/notes"` | `https://rishabharora-kk.github.io/notes/` |
| `rishabharora-kk.github.io` | `""` | `https://rishabharora-kk.github.io/` |

Pages setup is one manual step: **Settings -> Pages -> Source: Deploy from a
branch -> `main` / `(root)`.** A workflow cannot enable Pages for you -- creating
a Pages site needs repo-admin rights that `GITHUB_TOKEN` does not have at any
permission level. The setting survives a repo rename; the published URL follows
the new name.

For a custom domain later: add a `CNAME` file, set `url:` to the domain, and set
`baseurl: ""`.

## Where posts come from

Posts are **not written here.** They are produced by the publishing pipeline in
the private workshop repo and emitted into `_posts/` only after passing its
gates and an explicit human approval.

Writing a post directly into this repo bypasses the disclosure scan, both
judges, and the checklist. Don't. The whole point of the split is that nothing
reaches this repo unreviewed.

See the workshop's `publishing/README.md` for the pipeline.
