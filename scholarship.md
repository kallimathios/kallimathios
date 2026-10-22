---
title: Scholarship
intro: "Publications, presentations, and posters. Open-access versions are linked where available."
---

## Publications

<ul class="citation-list">
{% for p in site.data.publications %}
  <li>
    <span class="item__meta">{{ p.type }}</span><br>
    {{ p.citation }}
    {% if p.doi != "" %}<a href="https://doi.org/{{ p.doi }}">doi:{{ p.doi }}</a>{% endif %}
    {% if p.open_access_url != "" %} · <a href="{{ p.open_access_url }}">Open-access version</a>{% endif %}
  </li>
{% endfor %}
</ul>

## Presentations & posters

<ul class="citation-list">
{% for p in site.data.presentations %}
  <li>
    <span class="item__meta">{{ p.type }} · {{ p.date }}</span><br>
    <strong>{{ p.title }}</strong>. {{ p.event }}.
    {% if p.slides_url != "" %}<a href="{{ p.slides_url }}">Slides</a>{% endif %}
    {% if p.video_url != "" %} · <a href="{{ p.video_url }}">Recording</a>{% endif %}
  </li>
{% endfor %}
</ul>

For the full list, see my [ORCID record](https://orcid.org/{{ site.author.orcid }}).
