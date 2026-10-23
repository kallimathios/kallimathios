---
title: Teaching & Training
intro: "Workshops, staff training, and community working hours that help colleagues work confidently with linked data, from first triples to production cataloging."
---

{% for group in site.data.workshops %}
## {{ group.category }}

<div class="item-list">
  {% for w in group.items %}
  <article class="item">
    <h3 class="item__title">{{ w.title }}</h3>
    <p class="item__meta">{{ w.audience }} · {{ w.date }}</p>
    <p>{{ w.description }}</p>
    {% assign has_materials = false %}{% if w.materials_url and w.materials_url != "" %}{% assign has_materials = true %}{% endif %}
    {% if has_materials or w.link %}
    <p class="item__links">
      {% if has_materials %}<a href="{{ w.materials_url }}">Materials</a>{% endif %}
      {% if has_materials and w.link %} · {% endif %}
      {% if w.link %}<a href="{{ w.link | relative_url }}">Related initiative</a>{% endif %}
    </p>
    {% endif %}
  </article>
  {% endfor %}
</div>
{% endfor %}
