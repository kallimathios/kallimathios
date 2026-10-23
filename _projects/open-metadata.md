---
title: "Stanford University Libraries Open Metadata Policy"
summary: >-
  Helping Stanford University Libraries commit to open, reusable metadata: co-writing the Open
  Metadata Policy, reviewing vendor contracts for restrictions on reuse, working with
  Stanford's library units to agree on scope, and publishing SUL's bibliographic metadata under CC0
  in the Stanford Digital Repository.
role: "Policy co-author; contract reviewer; open data release coordinator"
start: "2024"
status: "Ongoing"
collaborators: ["SUL leadership", "SUL DLSS", "SUL Library Systems", "SUL Metadata Services", "Stanford Coordinate libraries"]
standards: [CC0, MARC 21, MARCXML, BIBFRAME]
tools: ["FOLIO", "Stanford Digital Repository", "Consul"]
links:
  - label: "SUL Open Metadata Policy"
    url: "https://library.stanford.edu/stanford-university-libraries-open-metadata-policy"
  - label: "Open MARC metadata (Stanford Digital Repository)"
    url: "https://doi.org/10.25740/sm443kx7967"
  - label: "Open BIBFRAME metadata (Stanford Digital Repository)"
    url: "https://doi.org/10.25740/zn292fv8269"
talk_tag: open-metadata
featured: false
order: 7
---

## The problem

Research, discovery, and scholarly communication depend on metadata, and libraries have long
shared and enriched it cooperatively. Stanford had decided in 2019 to adopt an open metadata
policy but hadn't put it into practice. Doing so meant answering hard questions:

- What can be released, given vendor contracts and privacy concerns?
- What about Stanford's independently managed Coordinate libraries?
- How should records be filtered, packaged, and published on a reliable schedule?

## The policy

The [Stanford University Libraries Open Metadata Policy](https://library.stanford.edu/stanford-university-libraries-open-metadata-policy)
was approved by the University Librarian and published in April 2025. It commits SUL to:

- Releasing library metadata under a Creative Commons Public Domain Dedication (CC0). Patron,
  business, contractual, copyright, privacy, and security-sensitive data are excepted.
- Investing in open infrastructure and in contracts for value-added services, and objecting to
  contracts that restrict metadata reuse
- Making metadata open by default in cooperative projects, a principle carried into
  [Blue Core]({{ '/initiatives/blue-core/' | relative_url }})
- Asking, but not requiring, that users credit SUL as the source, and encouraging them to share
  enrichments under CC0

## My role

I was part of a small core team that ran the project from its December 2024 planning meeting
through policy approval and the first data release.

- **Writing the policy.** I helped draft and refine the statement, moving from longer and shorter
  versions to the final text approved with the University Librarian and General Counsel.
- **Contract review.** I reviewed SUL's metadata vendor contracts to find what each one permits,
  and recommended an action for each vendor, such as which local MARC fields to exclude from
  export. I also collected examples of model and problematic contract language. Model language
  grants a perpetual, transferable license to use, distribute, and make derivative works from
  catalog records. Problematic clauses limit who data can be shared with or where, or extend
  restrictions to anything "copied therefrom."
- **Record analysis.** I worked with Metadata Services and Library Systems to understand why some
  records, mostly electronic resources, were flagged not to export. The reasons included record
  quality, license terms, and records created by others. Together we defined the export criteria.
- **Working with library units.** I met with Stanford's Coordinate libraries, including Law,
  the Graduate School of Business, Hoover, and Lane Medical, to explain the policy, review what
  they already share, and agree on participation and scope.

## Open data releases

With colleagues in DLSS, I publish SUL's open metadata to the Stanford Digital Repository (SDR):

- **MARC, quarterly.** [Stanford University Libraries Open Bibliographic Metadata](https://doi.org/10.25740/sm443kx7967)
  is a full snapshot of SUL bibliographic records in MARC and MARCXML under CC0. The October 2026
  release is version 7 and about 12 GB.
- **BIBFRAME, as available.** [Open BIBFRAME metadata](https://doi.org/10.25740/zn292fv8269)
  is deposited to SDR under CC0 as it becomes available.

## Outcomes

- A published, CC0-based open metadata policy for Stanford University Libraries, aligning SUL with
  its peers and with the Ivy Plus Libraries Confederation's Open Metadata Framework
- Seven releases of the open bibliographic dataset since July 2025, now on a regular quarterly
  schedule, with a persistent DOI and a contact for users
- A documented contract review that guides export filtering and supports negotiation for more open
  terms with vendors
- Agreement with participating Coordinate libraries, and a path for others to join when ready

## What's next

- Extend open releases beyond MARC: SDR descriptive metadata, finding aids, and geospatial
  metadata through EarthWorks and OpenGeoMetadata
- Grow BIBFRAME releases as Blue Core moves toward production
- Keep open metadata a standing priority in vendor contracts and renewals
