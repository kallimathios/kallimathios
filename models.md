---
title: Data Models & Vocabularies
intro: "Application profiles, vocabularies, shapes, and mappings I have designed or maintain."
---

<div class="item-list">
{% for m in site.data.models %}
  <article class="item">
    <h2 class="item__title">{% if m.url != "" %}<a href="{{ m.url }}">{{ m.title }}</a>{% else %}{{ m.title }}{% endif %}</h2>
    <p class="item__meta">{{ m.type }}{% if m.role %} · {{ m.role }}{% endif %}{% if m.formats %} · {{ m.formats | join: ", " }}{% endif %}{% if m.status %} <span class="status-badge">{{ m.status }}</span>{% endif %}</p>
    <p>{{ m.description }}</p>
    {% if m.draft_note %}<p class="draft-note">{{ m.draft_note }}</p>{% endif %}
    {% include tags.html tags=m.standards %}
  </article>
{% endfor %}
</div>

<h2 id="accessibility">Accessibility metadata in DCMI Metadata Terms</h2>

<p><span class="status-badge">Under review</span></p>

As a member of the DCMI Usage Board, I coordinated public comment on a proposed accessibility
property and then helped the Usage Board Chairs draft its successor. The work supports the draft
DCMI Scholarly Resources Application Profile (DC-SRAP). It sits where linked data practice meets
the needs of people who rely on accessibility metadata to find resources they can use.

### From one note to two properties

1. **A single free-text property (January 2026).** The Usage Board proposed
   `dcterms:accessibilityNote`, "a statement describing features or deficiencies of a resource that
   enhance or impede its usability and accessibility," and opened a
   [30-day public comment period](https://www.dublincore.org/news/2026/01-21_accessibility-note-comment/).
   I served as the contact for comments.
2. **What the community said.** [Responses](https://github.com/dcmi/usage/issues/133) came from
   repository managers, EPUB and accessibility specialists, and linked data practitioners. They
   affirmed the need for accessibility metadata but questioned free text as the vehicle for it.
   Concerns included:
   - Overlap with `dcterms:description`, and a MARC-style "note" pattern unlike other DCMI terms
   - Free text can't support filtering, consistent display, translation, or validation, as the
     EPUB community's shift to machine-readable metadata shows
   - Interoperability with MARC 341/532 and BIBFRAME, informed in part by BIBFRAME
     Interoperability Group comments on MARC Proposal 2026-02 that I contributed to as BIG Chair
3. **A revised proposal (June 2026).** With Tom Baker and Niklas Lindström, I helped draft a
   [two-property approach](https://github.com/dcmi/dc-srap/issues/103) for the Usage Board, and
   proposed alternative wording for how the text presents existing vocabularies such as Schema.org
   and the IFLA Accessibility Metadata Network's principles of consistency, standardization,
   granularity, interoperability, and extensibility.

### The proposed model

<div class="prop-grid">
  <div class="prop">
    <p class="prop__name"><code>dcterms:accessibility</code></p>
    <p><strong>Values:</strong> URIs from controlled vocabularies, preferably SKOS concepts</p>
    <p><strong>Role:</strong> precise, machine-actionable features and hazards for filtering search results and configuring interfaces</p>
  </div>
  <div class="prop">
    <p class="prop__name"><code>dcterms:accessibilitySummary</code></p>
    <p><strong>Values:</strong> free text (a subproperty of <code>dcterms:description</code>)</p>
    <p><strong>Role:</strong> a short, human-readable statement that complements rather than repeats the structured values</p>
  </div>
</div>

```turtle
@prefix dct:  <http://purl.org/dc/terms/> .
@prefix bibo: <http://purl.org/ontology/bibo/> .

# Illustrative only: these properties are proposed, not yet part of DCMI Metadata Terms.
<https://example.org/book/1> a bibo:Book ;
    dct:title "Example title"@en ;
    dct:accessibility <https://id.kb.se/vocab/accessibilityHazard/none> ;   # "no hazards" (LIBRIS URI)
    dct:accessibilitySummary "Tactile versions of the diagrams are available on request."@en .
```

### Open questions

Usage Board discussion continues on questions that matter to anyone modeling accessibility:

- Where controlled terms *without* URIs belong, given that most accessibility vocabularies,
  including Schema.org's, use literal terms
- Whether to express the range as `rdfs:range skos:Concept` or `dcam:rangeIncludes skos:Concept`
- How to keep the summary a complement to structured data rather than a substitute for it

The planned next steps are Usage Board consensus, a second 30-day public comment period, and revisions in light of that feedback.

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
