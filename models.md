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

<h2 id="bibframe-work-id">A Wikidata property for Library of Congress BIBFRAME Works</h2>

<p><span class="status-badge">Live</span></p>

In August 2025 I proposed, and the Wikidata community approved,
[Library of Congress BIBFRAME Work ID (P13714)](https://www.wikidata.org/wiki/Property:P13714): an
external identifier that connects a Wikidata item to its BIBFRAME Work in the Library of Congress
BIBFRAME database at id.loc.gov.

**Why it was needed.** Wikidata already had identifiers for LC authorities (P244), BIBFRAME Hubs
(P11859), and LCCNs (P1144). Other national libraries' work-level identifiers, such as BnF (P268)
and GND (P227), were also represented. But there was no equivalent for BIBFRAME Works assigned by
the Library of Congress, which maintains the BIBFRAME ontology and is a major source of
bibliographic data for the global GLAM community. Wikidata's modeling of books varies widely, so a
reliable link to the authoritative source lets data consumers confirm which Wikidata items
correspond to LC BIBFRAME Works. It also opens new editing paths in both directions between
library systems and Wikidata.

**How it's modeled:**

- **Subject item:** BIBFRAME Work ([Q107364994](https://www.wikidata.org/wiki/Q107364994)), for
  items that are instances of work ([Q386724](https://www.wikidata.org/wiki/Q386724)) or its
  subclasses
- **Datatype:** external identifier, formatted as `https://id.loc.gov/resources/works/$1.html`, with
  the format `^[1-9][0-9]*$`. The regular expression was refined with community input during
  the proposal discussion.
- **Constraints:** single value and distinct values, for data integrity, plus constraints on subject
  type, property scope, and allowed entity types
- **Related to:** Library of Congress Authorities ID (P244); "stated in" value: Library of Congress
  Linked Data Service
- **Examples:** *Data Feminism* → [21273441](https://id.loc.gov/resources/works/21273441.html),
  *Tropic of Cancer* → [4633147](https://id.loc.gov/resources/works/4633147.html),
  *Last Stop on Market Street* → [18189849](https://id.loc.gov/resources/works/18189849.html)

**Outcome.** The proposal received unanimous support, including from Wikidata ontology and
library linked data practitioners, and the property was created on August 21, 2025. The LC BIBFRAME
database holds more than 20 million Works, and the property is now in use on more than 160
Wikidata items as of October 2026.
[Read the proposal discussion](https://www.wikidata.org/wiki/Wikidata:Property_proposal/BIBFRAME_Work_ID).

<h2 id="wikidata-bibframe-mapping">Mapping Wikidata to BIBFRAME: a brief Work description</h2>

As part of the [Wikidata Ontology Course](https://www.wikidata.org/wiki/Wikidata:WikiProject_Ontology/Ontology_Course/Books/Mapping#Brief_description_for_a_BIBFRAME_Work)
Books group, I helped develop a mapping from Wikidata properties to BIBFRAME properties for a
**brief description of a BIBFRAME Work**. It treats Wikidata's work class
([Q386724](https://www.wikidata.org/wiki/Q386724)) and its subclasses as equivalent to BIBFRAME
Work ([Q107364994](https://www.wikidata.org/wiki/Q107364994)).

<div class="map-list" role="table" aria-label="Wikidata to BIBFRAME property mapping">
  <div class="map-row map-row--head" role="row"><span role="columnheader">Wikidata property</span><span role="columnheader">Datatype</span><span role="columnheader">BIBFRAME property</span></div>
  <div class="map-row" role="row"><span role="cell"><a href="https://www.wikidata.org/wiki/Property:P1476">title (P1476)</a></span><span role="cell">Monolingual text</span><span role="cell"><code>bf:title</code></span></div>
  <div class="map-row" role="row"><span role="cell"><a href="https://www.wikidata.org/wiki/Property:P1680">subtitle (P1680)</a></span><span role="cell">Monolingual text</span><span role="cell"><code>bf:subtitle</code></span></div>
  <div class="map-row" role="row"><span role="cell"><a href="https://www.wikidata.org/wiki/Property:P50">author (P50)</a>, <a href="https://www.wikidata.org/wiki/Property:P170">creator (P170)</a></span><span role="cell">Item</span><span role="cell"><code>bf:agent</code>, <code>bflc:simpleAgent</code></span></div>
  <div class="map-row" role="row"><span role="cell"><a href="https://www.wikidata.org/wiki/Property:P407">language of work or name (P407)</a></span><span role="cell">Item</span><span role="cell"><code>bf:language</code></span></div>
  <div class="map-row" role="row"><span role="cell"><a href="https://www.wikidata.org/wiki/Property:P577">publication date (P577)</a></span><span role="cell">Point in time</span><span role="cell"><code>bf:date</code></span></div>
  <div class="map-row" role="row"><span role="cell"><a href="https://www.wikidata.org/wiki/Property:P921">main subject (P921)</a></span><span role="cell">Item</span><span role="cell"><code>bf:subject</code></span></div>
  <div class="map-row" role="row"><span role="cell"><a href="https://www.wikidata.org/wiki/Property:P136">genre (P136)</a></span><span role="cell">Item</span><span role="cell"><code>bf:genreForm</code></span></div>
</div>

**Where it's used.** The mapping supports my experiment in the
[Blue Core Graph Toolbox]({{ '/initiatives/marc2wiki2bf/' | relative_url }}) that gives an AI agent
a Wikidata QID and generates a brief BIBFRAME Work, and complements the minimum property sets
proposed in my [Journal of Open Humanities Data article](https://doi.org/10.5334/johd.454). The
mapping builds on Matt Miller's earlier work
[mapping Wikidata to BIBFRAME](https://medium.com/@thisismattmiller/mapping-wikidata-to-bibframe-f674a4eab748)
and on modeling and community guidelines from
[WikiProject Books](https://www.wikidata.org/wiki/Wikidata:WikiProject_Books).

## Modeling sample: MARC to BIBFRAME with MARC2Wiki2BF

This is real output from [MARC2Wiki2BF]({{ '/initiatives/marc2wiki2bf/' | relative_url }}), my MARC →
Wikidata → BIBFRAME pipeline. The pipeline was run on a 2008 e-book edition of Jules Verne's
*Around the World in 80 Days* from its sample MARC records. The excerpt is trimmed for length,
some properties are omitted, and it includes the confirmed Wikidata link for the novel. Its mappings follow LC's marc2bibframe2, were checked against the
BIBFRAME ontology and live id.loc.gov records, and align with Blue Core's Sinopia templates.

```turtle
@prefix bf:   <http://id.loc.gov/ontologies/bibframe/> .
@prefix rdf:  <http://www.w3.org/1999/02/22-rdf-syntax-ns#> .
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .

# Work: the French uniform title (MARC 240), distinct from the Instance's English title (245)
<https://dev.bcld.info/works/f26b37cf-42b9-5061-b589-16240a4a6d5d> a bf:Work ;
    bf:title [ a bf:Title ;
            bf:mainTitle "Tour du monde en quatre-vingts jours." ] ;
    bf:contribution [ a bf:Contribution, bf:PrimaryContribution ;
            bf:agent [ a bf:Person ; rdfs:label "Verne, Jules," ] ;
            bf:role <http://id.loc.gov/vocabulary/relators/aut> ] ;
    bf:content <http://id.loc.gov/vocabulary/contentTypes/txt> ;
    bf:language <http://id.loc.gov/vocabulary/languages/eng> ;
    bf:classification [ a bf:ClassificationLcc ;
            bf:classificationPortion "PQ2469.T7" ;
            bf:itemPortion "E5 2008eb" ] ;
    bf:subject [ a bf:Topic ; rdfs:label "Voyages around the world--Fiction." ] ;
    bf:genreForm [ a bf:GenreForm ; rdfs:label "Adventure fiction." ] ;
    bf:hasInstance <https://dev.bcld.info/instances/b595d16e-4c54-564b-a4dc-833105d6694c> ;
    # Wikidata's item for the novel is a literary work, so the link belongs on the bf:Work
    rdfs:seeAlso <http://www.wikidata.org/entity/Q1219561> .

# Instance: the 2008 e-book edition
<https://dev.bcld.info/instances/b595d16e-4c54-564b-a4dc-833105d6694c> a bf:Instance ;
    bf:instanceOf <https://dev.bcld.info/works/f26b37cf-42b9-5061-b589-16240a4a6d5d> ;
    bf:title [ a bf:Title ; bf:mainTitle "Around the world in 80 days" ],
        [ a bf:VariantTitle ; bf:mainTitle "Around the world in eighty days" ] ;
    bf:responsibilityStatement "Jules Verne." ;
    bf:identifiedBy [ a bf:Isbn ; rdf:value "9781775412403" ] ;
    bf:provisionActivity [ a bf:Publication ;
            bf:agent [ a bf:Agent ; rdfs:label "Floating Press," ] ;
            bf:date "2008" ;
            bf:place <http://id.loc.gov/vocabulary/countries/nz> ] ;
    bf:issuance <http://id.loc.gov/vocabulary/issuance/mono> ;
    bf:media <http://id.loc.gov/vocabulary/mediaTypes/c> ;
    bf:carrier <http://id.loc.gov/vocabulary/carriers/cr> ;
    bf:extent [ a bf:Extent ; rdfs:label "1 online resource" ] .
```

### Modeling choices in this example

- **Work and Instance stay distinct.** The Work takes its title from the 240 uniform title, in French
  here. The Instance keeps the English 245 title, with the 246 variant title typed `bf:VariantTitle`.
- **Primary contribution is double-typed** as `bf:Contribution, bf:PrimaryContribution`, with the role
  as an id.loc.gov relator URI. This matches live LC records.
- **Controlled values are resources, not strings.** Content, media, carrier, issuance, language, and the
  008 country of publication point directly to id.loc.gov vocabulary URIs. The country nests as
  `bf:place` inside the `bf:Publication`.
- **URIs are deterministic.** Work and Instance URIs are minted with UUID5 from the record's local ID,
  so re-running the pipeline on corrected data reproduces the same URIs instead of creating new ones.
- **Wikidata links land at the right level.** Wikidata's item for the novel
  ([Q1219561](http://www.wikidata.org/entity/Q1219561)) is a literary work, so it links to the
  `bf:Work`, not the e-book Instance. The pipeline adds such links only on confident matches, and as
  `rdfs:seeAlso` rather than `owl:sameAs`, because the two graphs draw the Work/Instance boundary
  differently.
