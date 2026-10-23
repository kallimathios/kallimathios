---
title: "FOLIO MARC Authorities Automation"
summary: >-
  Restarting and automating authority processing for Stanford Libraries after the move to FOLIO,
  covering more than 4 million authority records, and testing FOLIO's authority linking and settings
  to improve them for the wider FOLIO community.
role: "Authorities & Entity Management Librarian (authorities lead)"
start: "2025"
status: "Ongoing"
collaborators: ["SUL Metadata Services", "SUL Library Systems (Libsys)", "Lane Medical Library", "FOLIO Metadata Management SIG"]
standards: [MARC 21 Authority, MARC 21 Bibliographic, LC NAF, LCSH]
tools: ["FOLIO (Quesnelia)", "Apache Airflow", "FOLIO Data Import", "quickMARC", "Authority vendor processing"]
talk_tag: folio
featured: false
order: 6
---

## The problem

Stanford University Libraries went live with FOLIO in 2023. Authority loading and processing
paused during the migration until 2025. Stanford and Lane Medical Library authorities had
previously been processed separately. Restarting meant consolidating them, catching up on almost
two years of new cataloging, and building a sustainable routine. The scale is large: **more than
4 million authority records** and **about 380,000 bibliographic records** to enhance.

## Approach

Metadata Services and Library Systems worked together, starting from a local analysis of FOLIO
functionality, historical practices and migration, and open issues and questions. That led to a
documented plan, timeline, and sequence.

**Catching up:**

- Lane sent its pre-migration Voyager records for vendor enhancement, and Libsys loaded the
  returned file.
- All bibliographic records cataloged since the FOLIO migration (August 28, 2023 to June 11, 2025),
  Lane's included, went to the authority vendor. The returned bibliographic and authority records
  were loaded in batches.

**Weekly automated cycle (Apache Airflow):**

1. **Select:** Fridays at 7 pm PT, find FOLIO instances newly marked *Cataloged* in the past seven
   days and not suppressed from discovery, excluding some records for licensing and other reasons
2. **Send:** Saturdays at 1:30 am PT, send them to the vendor by FTP
3. **Load:** Saturdays at 5 pm PT, load the enhanced bibliographic records and new or updated
   authorities through dedicated FOLIO Data Import profiles

**Monthly updates:** on the second Wednesday of each month, vendor notification files with new,
updated, and deleted authorities load automatically through Data Import with Airflow.

## Testing FOLIO authority linking and settings

Cataloger testing of FOLIO's authority-to-bibliographic linking and admin settings surfaced issues
that we documented and shared with the FOLIO Metadata Management SIG.

**Linking and search:**

- Searches skip `$c` in headings
- Headings with `$t` found no match (fixed in Trillium)
- Exact-phrase matching can link to the wrong vocabulary when the same terms appear in more
  than one vocabulary
- The 240 name-title search queries only the title
- Linking a `$0` can hide an existing `$1`
- The interface doesn't make clear what is being linked, and where

**Authority settings:**

- Prefix values behave as case-sensitive, despite documentation saying they aren't. As a result,
  GSAFD authorities with uppercase prefixes weren't recognized.
- Additional RBMS vocabulary codes, such as `rbbin`, can't be configured locally because Base
  URLs must be unique.
- The required "HRID starts with" field isn't documented.
- Prefixes can't be changed once authorities are assigned, which will matter when moving to
  linked data authorities.

## Outcomes

- Authority processing restarted for all Stanford libraries, with Lane and SUL authorities
  consolidated in one FOLIO environment
- A hands-off weekly and monthly routine instead of manual loads
- Documented feedback to the FOLIO community on authority linking and settings. FOLIO has since
  updated the authority settings interface.

## What's next

- Tune the vendor processing profiles for authority and bibliographic records
- Keep the automated routine running and prioritize the linking issues
- Investigate linked data authorities in 2026, connecting this work with Blue Core and Wikidata
  entity management
