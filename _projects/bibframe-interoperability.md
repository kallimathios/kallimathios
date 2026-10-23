---
title: "BIBFRAME Interoperability & SHACL Validation"
summary: >-
  Leading an international effort to define shared BIBFRAME shapes and validate data
  with tabular application profiles converted to SHACL, so BIBFRAME created anywhere
  can be reused consistently across institutions, tools, and data pools.
role: "Chair, BIBFRAME Interoperability Group (2025–2026)"
start: ""
status: "Ongoing"
collaborators:
  - "Library of Congress"
  - "OCLC"
  - "PCC"
  - "National Library of Sweden"
  - "National Library of Finland"
  - "Share-VDE"
  - "Index Data"
  - "Cornell"
  - "Penn"
  - "UC Davis"
  - "University of Alberta"
  - "Sinopia"
standards: [BIBFRAME, BFLC, DCTAP, SHACL]
tools: ["BIG DCTAP-to-SHACL validation tool", "Google Sheets (DCTAP)", "GitHub"]
repo: "https://github.com/bf-interop"
links:
  - label: "BIBFRAME Interoperability Validation Tool"
    url: "https://bf-interop.github.io/bf-demo-validation-tool"
  - label: "BIG wiki page"
    url: "https://wiki.lyrasis.org/pages/viewpage.action?pageId=249135298"
talk_tag: bibframe-interop
featured: true
order: 2
---

## The problem

BIBFRAME is now used in production by the Library of Congress and a growing number of
libraries, vendors, and data pools; however, BIBFRAME created in different editors, converted
by different versions of MARC-to-BIBFRAME tooling, or extended with local vocabularies
doesn't always look the same. Valid RDF isn't the same as interoperable data. Without
shared expectations for a "base" description, reuse across systems is unpredictable.

## The group

The BIBFRAME Interoperability Group (BIG) was established by the PCC Policy Committee to
address BIBFRAME interoperability internationally. It develops best practices and the tooling
needed for production-level reuse. It does not develop the BIBFRAME ontology itself. Two
subgroups do most of the technical work:

- **BIBFRAME Interlingua**: defines the properties, subgraph shapes, and violation levels for a
  base BIBFRAME description
- **DCTAP/SHACL**: maintains the tabular application profiles (DCTAP) and their conversion to
  SHACL shapes

## My role

I serve as Chair of BIG for 2025–2026 (Incoming Chair, 2024-2025; Past Chair, 2026-2027) and served as lead metadata tester for the group's validation tool.
As chair, I led the 2025 work plan across five areas: communications, governance, validation,
profiles, and use cases. I also represent the group at international conferences, develop documentation, and help maintain our GitHub repository.

## Approach

1. **Profiles in spreadsheets.** Core elements for monographs and serials are maintained as DCTAP
   in Google Sheets, so catalogers can read and edit validation rules without writing code.
2. **DCTAP → SHACL.** Profiles are converted to SHACL shapes that drive the BIBFRAME
   Interoperability Validation Tool. Users validate RDF by URL or file upload and see violations
   and warnings.
3. **Multi-institution testing.** In early 2025, seven member institutions tested the tool with
   their own data: Work and Instance descriptions (including administrative metadata) for print
   and electronic monographs and serials. The test included both MARC-converted and natively
   created BIBFRAME.

## Outcomes

- Most member data met validation requirements for monograph and serial shapes, with few violations.
- Created documentation for the validation tool to support testers.
- Surfaced issues that now shape BIG's work plan:
  - Places where cataloging practice and validation rules are misaligned
  - SHACL rules that needed adjusting to align with BFLC extension documentation
  - Different error patterns for MARC-converted and natively created BIBFRAME
  - The administrative metadata shape needing reconsideration
- Informed early implementations that build on BIG outputs, including the Sinopia validation
  prototype and OCLC validation work.

## What's next

- Turning real-world use cases into published BIBFRAME best practices, aligned with LC documentation
- Analyzing disparate BIBFRAME metadata application profiles to develop a common data shape for full descriptions
- Supporting MARC-to-BIBFRAME conversion and "Modern MARC" during the transition
- Identifying core elements for non-textual formats, and extending shapes to bf:Hub and svde:Opus
- Integrating DCTAP/SHACL validation into editors and vendor tools, so validation is part of
  everyday cataloging workflows rather than a separate step
