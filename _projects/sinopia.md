---
title: "Sinopia Linked Data Editor"
summary: >-
  Guiding the product direction, community, and integrations of Sinopia, the open-source,
  BIBFRAME-optimized linked data cataloging editor used by thousands of catalogers in 48 countries.
role: "Product Owner; Co-Convener, PCC Sinopia Cataloging Affinity Group"
start: "2023"
status: "Ongoing"
collaborators: ["SUL DLSS", "Program for Cooperative Cataloging (PCC)", "LD4 Community", "FOLIO Linked Open Data SIG", "Alma Linked Data Focus Group"]
standards: [BIBFRAME, RDF, SPARQL, PCC templates]
tools: ["Sinopia Editor", "Sinopia ILS Middleware (Apache Airflow)", "Sinopia Graph Explorer", "Questioning Authority", "Elasticsearch", "GitHub"]
repo: "https://github.com/LD4P/sinopia_editor"
links:
  - label: "Sinopia"
    url: "https://sinopia.io"
  - label: "Sinopia ILS Middleware"
    url: "https://github.com/LD4P/ils-middleware"
  - label: "Sinopia Graph Explorer"
    url: "https://ld4p.github.io/graph-explorer/"
talk_tag: sinopia
featured: false
order: 5
---

## The problem

Libraries moving to BIBFRAME need somewhere to actually create linked data, learn how it works,
and connect it back to the systems that run their operations. Sinopia was built during the
Mellon-funded Linked Data for Production (LD4P) grants as "the underdrawing for a new world of
linked data in libraries." It's named for the reddish-brown pigment used to sketch out a fresco.
Keeping it useful means balancing the needs of a large international community with a fast-changing
BIBFRAME and library systems landscape.

## About Sinopia

- Open-source, cloud-based linked data (RDF) editor, optimized for BIBFRAME and free of charge
- Development, stage, and production environments
- **2,752 users from 48 countries and 52 institutional groups** after five years in operation
  (March 2025)
- PCC templates for monographs, serials, music recordings, and notated music. Catalogers can also
  build their own templates and choose their own ontologies.
- Questioning Authority lookups, MARC conversion, multiple RDF serializations, and Elasticsearch
  discovery faceted by BIBFRAME class and user group

## My role

I started at Stanford in 2023 as the Linked Data Community Outreach Librarian, teaching
beginner and template workshops for Sinopia. I'm now Sinopia's Product Owner, setting priorities
and work cycles, and co-convene the PCC Sinopia Cataloging Affinity Group. The group meets
monthly and is a central place for BIBFRAME training and feedback.

## Approach

- **Listen to the community.** I convened a 2025 Sinopia User Forum to look back on six years of
  cataloging in Sinopia. Breakout groups covered how Sinopia shaped catalogers' understanding of
  BIBFRAME, design and UX changes, implementation roadblocks, and programming needs. Findings were
  mapped to existing GitHub issues or turned into new ones to prepare future work cycles.
- **Keep pace with BIBFRAME.** The December 2023 sprint added note-type, serial-publication-type,
  and relationship vocabularies. It moved Questioning Authority from cached to direct API lookups,
  added deriving a Work title from an Instance, fixed title bugs, and adopted
  `bf:PrimaryContribution` and `bf:TransliteratedTitle` while keeping templates backwards-compatible.
- **Connect to library systems.** The Sinopia ILS Middleware uses Apache Airflow to send
  descriptions to Symphony, Alma, and FOLIO, with Sinopia as the source of truth. In 2025 we
  expanded the FOLIO mappings (edition, genre, organization contributors, LC classification,
  primary contribution) and supported FOLIO's UXPROD-5135. That feature adds a source URI to FOLIO
  Inventory, linking a FOLIO record to its description in a shared cataloging environment such as
  Sinopia, Share-VDE, Libris, or Blue Core.
- **Make data discoverable.** The Sinopia Graph Explorer is a browser-based proof of concept for
  loading Sinopia RDF, running SPARQL, and downloading results. The same queries drive the
  middleware mappings.

## Outcomes

- **Alma users:** in a 2025 survey of 15 Alma libraries, all 13 respondents planned to keep
  using Sinopia after the Alma linked data editor launched. A 2026 Sinopia Alma User Forum gathered
  needs on editors, templates, and Blue Core participation to share with Clarivate and LD4 partners.
- **What users said:** catalogers credit Sinopia's forms with clarifying the difference between
  `bf:Work` and `bf:Instance` and easing the move from MARC to BIBFRAME. Their requests included
  batch uploads, clearer documentation, a simpler environment structure, and training for
  complex materials.
- **Blue Core:** a new instance of Sinopia now serves as one of Blue Core's two linked data editors.
