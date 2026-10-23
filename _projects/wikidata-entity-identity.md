---
title: "Wikidata & Entity Identity"
summary: >-
  Bridging library authority work and Wikidata through ontology research, prototypes,
  cataloging workflows, and community training, so identities for people and works stay
  precise and reusable across metadata styles.
role: "Lead author; workshop instructor; keynote co-presenter; Stanford Wikidata Community of Practice"
start: "2020"
status: "Ongoing"
collaborators:
  - "Ege Atacan Doğan"
  - "Jeremy Nelson"
  - "Tom Baker (DCMI)"
  - "Niklas Lindström (National Library of Sweden)"
  - "Wikidata Ontology Course"
standards: [Wikidata, IFLA LRM, BIBFRAME, DCTAP, SPARQL]
tools: ["Wikidata", "QLever", "OpenRefine", "QuickStatements", "Blue Core Graph Toolbox"]
links:
  - label: "Journal of Open Humanities Data article (doi:10.5334/johd.454)"
    url: "https://doi.org/10.5334/johd.454"
talk_tag: wikidata
featured: true
order: 3
---

## The problem

Libraries invest heavily in authority data: complete, correct, consistent descriptions of
people, organizations, and works. Wikidata is the most widely reused open knowledge graph,
feeding search engines, voice assistants, and AI systems. But the two don't line up neatly.
Wikidata's crowd-sourced bibliographic model conflates entities that library models keep
distinct, which limits reuse in both directions.

## Research: refining Wikidata's bibliographic domain

Through the 2025 Wikidata Ontology Course, my co-authors and I compared IFLA LRM,
WikiProject Books, and BIBFRAME 2.0. We identified class and property conflations in
Wikidata's bibliographic domain and proposed refinements:

- Splitting Wikidata's "version, edition or translation" class so that LRM Expression and
  Manifestation are distinct
- Minimum property sets for Work, Expression, Manifestation, and Item entities
- New property proposals (*has version*, *has edition*, *has translation*, issue date)

> Mathios, K., Doğan, E. A., & Nelson, J. (2026). Refining Wikidata's Bibliographic Domain
> to Increase Reuse in GLAMs. *Journal of Open Humanities Data*, 12(1), 3.
> [doi:10.5334/johd.454](https://doi.org/10.5334/johd.454)

## Prototypes

- **MARC2Wiki2BF**: a prototype pathway between MARC, Wikidata, and BIBFRAME
- **Wikidata → BIBFRAME with AI**: an experiment in the Blue Core Graph Toolbox that gives an
  AI agent a Wikidata QID for a bibliographic entity and generates a BIBFRAME Work

## In practice at Stanford

- Stanford University Libraries participates in the **EMCO early adopters** Wikidata community
  of practice, modeling person entities and integrating Wikidata into cataloging workflows
- This builds on the PCC Wikidata Pilot and LD4P projects, and on Stanford's Wikidata
  Community of Practice and Working Group

## Teaching and community

- **Love Data Week 2026 Wikidata Edit-a-thon** (Stanford): introduction to Wikidata, editing
  ethics, and hands-on contribution
- **DCMI 2026 workshop, Seoul**: "Wikidata for Open Innovation in Libraries, Industry, and
  Communities", a two-hour session with presentation and edit-a-thon
- Guest talk for the Wikidata Ontology Course on the bibliographic domain

## Keynote: Identity in context across metadata styles

At **DCMI 2026 in Seoul**, I delivered the keynote with Tom Baker (DCMI) and Niklas Lindström
(National Library of Sweden). It followed one editor attribution from a catalog card through
MARC, BIBFRAME, Libris, Dublin Core, DataCite, and the DCMI Scholarly Resources Application
Profile. The central argument: for interoperability, **precision of identity matters more than
richness of detail**. RDF, application profiles (DCTAP, ShEx, SHACL), and AI can help translate
between "simpler and flatter" and "complex and nested" metadata styles. The Wikidata item used
in the talk's example was edited by Stanford Libraries while preparing it.
