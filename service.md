---
title: Service
intro: "Standards, community, professional, and campus service."
---

{% for group in site.data.service %}
## {{ group.category }}

<ul class="service-list">
  {% for s in group.items %}
  <li><strong>{{ s.role }}</strong>, {{ s.group }} <span class="item__meta">({{ s.dates }})</span></li>
  {% endfor %}
</ul>
{% endfor %}
