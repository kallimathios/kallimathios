---
title: Service
intro: "Leadership in metadata standards, linked data communities, conferences, and publishing, building shared infrastructure for library data on the open web."
---

{% for group in site.data.service %}
## {{ group.category }}

<ul class="service-list">
  {% for s in group.items %}
  <li>
    <strong>{{ s.role }}</strong>, {% if s.link %}<a href="{{ s.link | relative_url }}">{{ s.group }}</a>{% else %}{{ s.group }}{% endif %}
    <span class="item__meta">({{ s.dates }})</span>
    {% if s.note %}<br><span class="item__meta">{{ s.note }}</span>{% endif %}
  </li>
  {% endfor %}
</ul>
{% endfor %}

See the [CV]({{ '/cv/' | relative_url }}) for the complete record.
