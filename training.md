---
title: Teaching & Training
intro: "Workshops and training that help colleagues work confidently with linked data."
---

<div class="item-list">
{% for w in site.data.workshops %}
  <article class="item">
    <h2 class="item__title">{{ w.title }}</h2>
    <p class="item__meta">{{ w.audience }} · {{ w.date }}</p>
    <p>{{ w.description }}</p>
    {% if w.materials_url != "" %}<p><a href="{{ w.materials_url }}">Materials</a></p>{% endif %}
  </article>
{% endfor %}
</div>
