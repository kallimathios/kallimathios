---
title: CV
intro: "Authorities & Entity Management Librarian at Stanford University Libraries, working on linked open data, BIBFRAME, and entity management."
---
{% assign cv = site.data.cv %}
{% assign cv_pdf = site.static_files | where: "path", "/assets/cv.pdf" | first %}
<div class="cv-actions">
  {% if cv_pdf %}<a class="button" href="{{ '/assets/cv.pdf' | relative_url }}">Download CV (PDF)</a>{% endif %}
  <span class="item__meta">Updated {{ cv.updated }}</span>
</div>

<nav class="cv-toc" aria-label="CV sections">
  <ul>
    <li><a href="#experience">Experience</a></li>
    <li><a href="#education">Education</a></li>
    <li><a href="#publications">Publications</a></li>
    <li><a href="#presentations">Presentations</a></li>
    <li><a href="#service">Service</a></li>
    <li><a href="#grants">Grants</a></li>
    <li><a href="#volunteer">Volunteer</a></li>
    <li><a href="#courses">Courses</a></li>
  </ul>
</nav>

<section class="cv-section" aria-labelledby="experience">
  <h2 id="experience">Professional experience</h2>
  {% for job in cv.experience %}
  <article class="cv-entry">
    <div class="cv-entry__when">{{ job.dates }}<br><span>{{ job.location }}</span></div>
    <div class="cv-entry__body">
      <h3 class="cv-entry__title">{{ job.title }}</h3>
      <p class="cv-entry__org">{{ job.org }}</p>
      <p>{{ job.description }}</p>
    </div>
  </article>
  {% endfor %}
</section>

<section class="cv-section" aria-labelledby="education">
  <h2 id="education">Education</h2>
  {% for e in cv.education %}
  <article class="cv-entry">
    <div class="cv-entry__when">{{ e.date }}<br><span>{{ e.location }}</span></div>
    <div class="cv-entry__body">
      <h3 class="cv-entry__title">{{ e.degree }}</h3>
      <p class="cv-entry__org">{{ e.school }}</p>
    </div>
  </article>
  {% endfor %}
</section>

<section class="cv-section" aria-labelledby="publications">
  <h2 id="publications">Publications</h2>
  <ol class="cv-citations" reversed>
    {% for p in cv.publications %}
    <li>{{ p.citation }}{% if p.doi %} <a href="https://doi.org/{{ p.doi }}">https://doi.org/{{ p.doi }}</a>{% endif %}</li>
    {% endfor %}
  </ol>
</section>

<section class="cv-section" aria-labelledby="presentations">
  <h2 id="presentations">Presentations</h2>
  <ol class="cv-citations" reversed>
    {% for p in cv.presentations %}<li{% if p.keynote %} class="cv-keynote"{% endif %}>{{ p.citation }}</li>{% endfor %}
  </ol>
  <p>See <a href="{{ '/scholarship/' | relative_url }}">Scholarship &amp; Talks</a> for workshops, community updates, and slides.</p>
</section>

<section class="cv-section" aria-labelledby="service">
  <h2 id="service">Professional service</h2>
  <h3 class="cv-subhead">Current</h3>
  <ul class="cv-list">{% for s in cv.service.current %}<li>{{ s }}</li>{% endfor %}</ul>
  <h3 class="cv-subhead">Previous</h3>
  <ul class="cv-list">{% for s in cv.service.past %}<li>{{ s }}</li>{% endfor %}</ul>
</section>

<section class="cv-section" aria-labelledby="grants">
  <h2 id="grants">Grants</h2>
  <ul class="cv-list">{% for g in cv.grants %}<li>{{ g }}</li>{% endfor %}</ul>
</section>

<section class="cv-section" aria-labelledby="volunteer">
  <h2 id="volunteer">Volunteer &amp; internship experience</h2>
  {% for v in cv.volunteer %}
  <article class="cv-entry cv-entry--compact">
    <div class="cv-entry__when">{{ v.dates }}<br><span>{{ v.location }}</span></div>
    <div class="cv-entry__body">
      <h3 class="cv-entry__title">{{ v.role }}</h3>
      <p class="cv-entry__org">{{ v.org }}</p>
    </div>
  </article>
  {% endfor %}
</section>

<section class="cv-section" aria-labelledby="courses">
  <h2 id="courses">Certifications &amp; courses</h2>
  <ul class="cv-courses">
    {% for c in cv.courses %}
    <li><span class="cv-courses__name">{{ c.course }}</span><span class="cv-courses__meta">{{ c.provider }} · {{ c.date }}</span></li>
    {% endfor %}
  </ul>
</section>
