# Metadata Librarian Portfolio (Jekyll)

A simple, accessible Jekyll portfolio for a metadata librarian working with RDF and linked data.
It uses Stanford identity colors and the layout from the brand guidelines: a full-width header,
a 1/4 sidebar, 3/4 main content, and a full-width footer. See `SITEMAP.md` for the page plan.

## Publish on GitHub Pages

1. Create a repository named `USERNAME.github.io` (or any name for a project site).
2. Upload these files to the repository root.
3. Go to **Settings → Pages → Build and deployment**, choose **Deploy from a branch**, and select `main` / root.
4. In `_config.yml`, set `url` (and `baseurl: "/repo-name"` if this is a project site).

Optional local preview: `bundle install && bundle exec jekyll serve`, then open http://localhost:4000.

## Where content goes

| What | File |
|---|---|
| Name, tagline, identifiers (ORCID, Wikidata, GitHub), focus areas | `_config.yml` |
| Home headline & intro | `index.md` |
| Bio & statement of librarianship | `about.md` |
| Case studies | `_projects/*.md` (copy an example; set `featured: true` to show on home) |
| Models, vocabularies, shapes, mappings | `_data/models.yml` |
| Code, queries, tools | `_data/tools.yml` |
| Publications / presentations | `_data/publications.yml`, `_data/presentations.yml` |
| Workshops | `_data/workshops.yml` |
| Service | `_data/service.yml` |
| CV | `cv.md` + `assets/cv.pdf` |
| Headshot | `assets/img/headshot.jpg`, then set `author.headshot` |
| Menu order | `_data/navigation.yml` |

## Built-in linked data

Every page embeds a schema.org `Person` description in JSON-LD, built from `_config.yml`, with `sameAs`
links to ORCID, Wikidata, and GitHub. Each project page also embeds a `CreativeWork` linked to you as creator.
Code blocks marked `turtle` or `sparql` get syntax highlighting.

## Branding notes

- Colors are defined as CSS variables at the top of `assets/css/main.css`.
- Fonts: Source Sans 3 and Source Serif 4 (Google Fonts).
- `stanford_global_footer: true` shows the Stanford global footer. Stanford reserves its marks and
  global footer for official university sites, so if this is a personal site, check with University
  Communications or set this to `false`. Your personal footer line still appears either way.
