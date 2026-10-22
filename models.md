---
title: Data Models & Vocabularies
intro: "Application profiles, vocabularies, shapes, and mappings I have designed or maintain."
---

<div class="item-list">
{% for m in site.data.models %}
  <article class="item">
    <h2 class="item__title">{% if m.url != "" %}<a href="{{ m.url }}">{{ m.title }}</a>{% else %}{{ m.title }}{% endif %}</h2>
    <p class="item__meta">{{ m.type }}{% if m.formats %} · {{ m.formats | join: ", " }}{% endif %}</p>
    <p>{{ m.description }}</p>
    {% include tags.html tags=m.standards %}
  </article>
{% endfor %}
</div>

## Modeling sample

Short, annotated excerpts help reviewers see your modeling choices. Replace this one with your own.

```turtle
@prefix bf:   <http://id.loc.gov/ontologies/bibframe/> .
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .
@prefix ex:   <https://example.org/> .

ex:work1 a bf:Work ;
    bf:title [ a bf:Title ; bf:mainTitle "Example title" ] ;
    bf:subject <http://id.loc.gov/authorities/subjects/sh85076502> .

ex:instance1 a bf:Instance ;
    bf:instanceOf ex:work1 .
```
