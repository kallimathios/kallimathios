---
title: Code, Queries & Tools
intro: "Code I've written, and open-source linked data tools I help shape as a product owner, tester, and chair."
---

<div class="item-list">
{% for t in site.data.tools %}
  <article class="item">
    <h2 class="item__title">{% if t.url and t.url != "" %}<a href="{{ t.url }}">{{ t.title }}</a>{% else %}{{ t.title }}{% endif %}</h2>
    <p class="item__meta">{{ t.language }}{% if t.role %} · {{ t.role }}{% endif %}</p>
    <p>{{ t.description }}</p>
    {% if t.initiative %}<p><a href="{{ '/initiatives/' | append: t.initiative | append: '/' | relative_url }}">Read the initiative</a></p>{% endif %}
  </article>
{% endfor %}
</div>

## Sample: classifying a Wikidata match by level

From MARC2Wiki2BF. Before linking a library record to Wikidata, the pipeline asks whether the
matched item is an *edition* (so the link goes on the `bf:Instance`) or a *work* (so it goes on
the `bf:Work`), following class hierarchies with `wdt:P31/wdt:P279*`.

```sparql
# Is the candidate an edition/version (→ bf:Instance)?
ASK {
  wd:Q12345 wdt:P31/wdt:P279* ?c .
  VALUES ?c { wd:Q3331189 }          # version, edition or translation
}

# Otherwise, is it a work (→ bf:Work)?
ASK {
  wd:Q12345 wdt:P31/wdt:P279* ?c .
  VALUES ?c { wd:Q386724 wd:Q11424 wd:Q24856 }   # work, film, film series
}
```

## Sample: verifying a person before trusting a title match

A fuzzy title match only gets a confidence boost if the author's authority-linked QID
(resolved from MARC `$0`/`$1`) is credited as a creator of the candidate.

```sparql
ASK { wd:Q12345 (wdt:P50|wdt:P57|wdt:P58|wdt:P170|wdt:P86) wd:Q67890 }
# author | director | screenwriter | creator | composer
```
