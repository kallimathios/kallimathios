---
title: Code, Queries & Tools
intro: "Scripts, queries, and workflows I've written to create, transform, and check linked data."
---

<div class="item-list">
{% for t in site.data.tools %}
  <article class="item">
    <h2 class="item__title">{% if t.url != "" %}<a href="{{ t.url }}">{{ t.title }}</a>{% else %}{{ t.title }}{% endif %}</h2>
    <p class="item__meta">{{ t.language }}</p>
    <p>{{ t.description }}</p>
  </article>
{% endfor %}
</div>

## Sample query

```sparql
# Find works that have no subject headings
PREFIX bf: <http://id.loc.gov/ontologies/bibframe/>
SELECT ?work ?title WHERE {
  ?work a bf:Work ;
        bf:title/bf:mainTitle ?title .
  FILTER NOT EXISTS { ?work bf:subject ?s }
}
LIMIT 100
```
