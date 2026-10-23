# Update: Initiatives + Scholarship & Talks

## 1. Upload these files (replace existing)

Drag the contents of this folder into your repo root on GitHub ("Add file → Upload files").
Folder paths are preserved, so files land in the right place.

| File | What changed |
|---|---|
| `_data/navigation.yml` | "Projects" → "Initiatives"; "Scholarship" → "Scholarship & Talks" |
| `_data/presentations.yml` | 32 talks from your slide decks, tagged by initiative |
| `_data/publications.yml` | JOHD 2026 article + DCMI 2025 paper |
| `_projects/bibframe-interoperability.md` | New initiative page |
| `_projects/wikidata-entity-identity.md` | New initiative page |
| `_includes/talk.html` | New: formats one talk |
| `_layouts/project.html` | "Initiatives" breadcrumb, Links list, auto "Related talks" section |
| `_layouts/home.html` | "Featured initiatives" |
| `projects.html` | Initiatives index page, now at /initiatives/ |
| `scholarship.md` | Featured keynote, publications, talks grouped by year |
| `404.html` | Link updated |
| `_includes/footer.html` | AI acknowledgment added to the site footer |
| `assets/css/main.css` | Styles for talks, the featured keynote, and the footer note |
| `SITEMAP.md` | Updated |

## 2. Edit by hand (these have your own changes, so they aren't included)

**`_config.yml`**: change one line under `collections:`:

```yaml
permalink: /initiatives/:name/
```

**`about.md`**: if it still links to `/projects/`, change it to `/initiatives/`.

**Your Blue Core file in `_projects/`**: add these lines to its front matter so its talks
appear automatically and it sorts first:

```yaml
talk_tag: blue-core
featured: true
order: 1
```

## 3. Delete the template examples (if still in your repo)

- `_projects/marc-to-bibframe.md`
- `_projects/shacl-application-profile.md`
- `_projects/wikidata-reconciliation.md`

## 4. Confirm the "CHECK" items

Open `_data/presentations.yml` and search for `CHECK`. Those items need a date or venue
confirmed. Add `slides_url:` to any talk with slides online (SlideShare, Zenodo, Google Slides)
and a "Slides" link appears automatically.
