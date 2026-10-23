---
title: "Blue Core: A community-operated, shared BIBFRAME datastore."
summary: "Blue Core aims to create a community-operated BIBFRAME datastore where ownership and creation of the metadata are shared among member institutions, eliminating the need for duplicative institutional copies, and bringing library linked open data to production at scale."
role: "Project Manager and Product Owner"
start: "2023"
status: "In progress"
collaborators: ["SUL DLSS", "Cornell University", "University of California, Davis", "Library of Congress", "University of Pennsylvania"]
standards: [BIBFRAME, MARC 21, SPARQL]
tools: ["GitHub", "MARC2BIBFRAME2 XSLT", "Blue Core Postgres Datastore", "Sinopia Editor", "Marva", "FastAPI", "Keycloak", "Apache Airflow", "Milvus", "PydanticAI"]
repo: "https://github.com/blue-core-lod"
data_url: ""
links:
  - label: "Blue Core website"
    url: "https://bluecore.info/"
talk_tag: blue-core
featured: true
order: 1
---

## The problem

After successful experimentation and development during the Mellon-funded Linked Data for Production (LD4P) grants, Stanford and Blue Core partners needed to shift focus from tooling and technology strategy to implementing BIBFRAME cataloging.

Most shared cataloging today depends on institutions copying and storing their own versions of bibliographic and authority data, or on third parties for access. Blue Core imagines an alternative: a library metadata environment with linked data at its core, cooperatively shaped and owned, so that each institution doesn't have to build linked data tooling locally. Shared bibliographic data (BIBFRAME Works and Instances) is kept separate from local data (holdings and administrative data in library services platforms like FOLIO and Alma). Data is copied only for downstream uses such as local search indexing.

## Approach

Agile development drove the development of the Blue Core ecosystem, along with a thorough assessment of user requirements and existing linked data tooling with an emphasis on open-source technologies.

The project moves through four phases: **Plan • Prototype • MVP • Production**. It draws on a design approach that frames challenges as design opportunities and treats each solution as iterative: analysis, synthesis, evaluation, and repeat. Three opportunities shaped the prototype:

- **BIBFRAME origins:** supporting BIBFRAME from many sources, including MARC conversion and multiple linked data editors, with validation and templates for consistency
- **Metadata workflows:** rethinking the cataloging data flow when Work and Instance cataloging moves outside the local system, with Blue Core BIBFRAME as the source of truth
- **Description sets:** moving beyond the MARC record by working with Concise Bounded Descriptions, sets of linked statements rather than self-contained records

For the MVP, the governance group worked with local teams at each institution to gather use cases, identify common and diverging needs, and scope requirements. Requirements moved from a shared spreadsheet and narrative document to the Blue Core GitHub project board, and development runs in work cycles of about eight weeks.

## Technical architecture

Blue Core is built on well-supported open-source projects also used in FOLIO and Sinopia:

- **Blue Core API:** FastAPI, built on the Sinopia API's OpenAPI specification, with authentication and authorization through Keycloak
- **Data store:** Postgres. The prototype ingested about 430,000 BIBFRAME Works and 520,000 BIBFRAME Instances from the Library of Congress BIBFRAME Database as Concise Bounded Descriptions.
- **Blue Core Workflows:** Apache Airflow for batch processing and integration with Alma and FOLIO, adapted from the Sinopia ILS Middleware
- **Editors:** Blue Core instances of the Sinopia and Marva linked data editors
- **AI-ready design:** Milvus stores vectors of BIBFRAME Work and Instance RDF for AI agents built with PydanticAI. The first agent detects BIBFRAME duplicates and keeps a human in the loop for deduplication decisions.
- **Open access model:** open read access to all RDF resources, with authentication required to add or edit, following Sinopia's model

## Data model

BIBFRAME data shapes are determined by the Program for Cooperative Cataloging (PCC) Metadata Application Profiles Working Group's Sinopia Resource Templates which align with the Library of Congress Marva Profiles.

Blue Core also plans to use BIBFRAME Interoperability Group validation and extension work to normalize incoming BIBFRAME and encourage reuse.

## Outcomes

After successful completion of the Blue Core Prototype in 2025, we are on track to complete the Blue Core MVP by early 2027. The Blue Core ecosystem offers a first for the library industry: two open-source linked data editors are able to create, edit, and display BIBFRAME RDF descriptions within a shared datastore. Blue Core offers single and batch MARC conversion to BIBFRAME, import reports, and duplicate reports. Cataloging policy and BIBFRAME best practices are developed in tandem with partners like the PCC and Share-VDE.

- **Prototype assessment:** after the technical working group finished the prototype, the metadata working group tested Sinopia, Marva, and the Graph Toolbox against cataloger needs (searching, results display, editing, queries, and bulk actions). Top issues for the MVP were URI and label management, search and results display, and tighter integration with editors and library systems.
- **MVP scope:** end-to-end monograph cataloging, with some serials work, covering print and e-books, notated music, games, and non-English-language material. It includes original and copy cataloging, batch workflows, and Alma and FOLIO integration through Apache Airflow.
- **2026 work cycles:**
  - Better LCSH support in Blue Core Sinopia, and Blue Core Marva aligned with LC Marva
  - Public search with content negotiation, and user-facing bulk ingest
  - Deduplication, and ingest of Library of Congress BIBFRAME Hubs, Works, and Instances
  - Production, stage, and development environments provisioned on-premises at Stanford
- **New institution code:** Blue Core has its own institution code, CBC, for BIBFRAME cataloging.
- **Community:** collaborating with the BIBFRAME Interoperability Group, PCC, LD4 Community, Share-VDE, DCMI, the FOLIO LOD SIG, and the Alma Linked Data Focus Group, following the Library of Congress's lead and inspired by the National Library of Sweden's Libris.
- **What's next:** Blue Core libraries plan to use the system in production in mid-2027, with all data available to everyone under a CC0 public domain dedication.

## What I learned

The road to production linked open data in libraries is a marathon, not a sprint.
