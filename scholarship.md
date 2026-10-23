---
title: Scholarship & Talks
intro: "Publications, keynotes, conference presentations, and workshops on linked data, BIBFRAME, Wikidata, and metadata interoperability."
---

{% assign featured = site.data.presentations | where: "featured", true %}
{% for t in featured %}
<section class="feature-talk bg-plum" aria-label="Featured talk">
  <p class="feature-talk__label">{{ t.type }} · {{ t.event }} · {{ t.when }}</p>
  <h2 class="feature-talk__title">{{ t.title }}</h2>
  {% if t.copresenters %}<p class="feature-talk__with">with {{ t.copresenters | join: " and " }}</p>{% endif %}
  {% if t.description %}<p>{{ t.description }}</p>{% endif %}
  {% if t.slides_url and t.slides_url != "" %}<p><a class="button button--light" href="{{ t.slides_url }}">View slides</a></p>{% endif %}
</section>
{% endfor %}

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

## Talks & workshops

{% assign talks = site.data.presentations | where_exp: "t", "t.featured != true" %}
<p class="item__meta">{{ site.data.presentations.size }} presentations, including keynotes, conference talks, workshops, and community updates.</p>
{% assign by_year = talks | group_by: "year" %}
{% for y in by_year %}
<h3 class="year-heading">{{ y.name }}</h3>
<ul class="talk-list">
  {% for t in y.items %}{% include talk.html talk=t %}{% endfor %}
</ul>
{% endfor %}

For a complete record, see my [ORCID profile](https://orcid.org/{{ site.author.orcid }}).
