---
title: "MARC2Wiki2BF: Wikidata Reconciliation to BIBFRAME"
summary: >-
  A prototype pipeline that converts MARC21 or spreadsheet records into BIBFRAME Work and
  Instance RDF, reconciling them against Wikidata at the right level of description and
  writing them directly to Blue Core, without asserting an uncertain match as fact.
role: "Creator (AI-assisted development)"
start: "2026"
status: "Prototype"
collaborators: ["Blue Core"]
standards: [BIBFRAME, MARC 21, Wikidata, SPARQL, JSON-LD]
tools: ["Python", "rdflib", "pymarc", "rapidfuzz", "Wikidata Query Service", "Blue Core API", "Keycloak", "Jupyter"]
repo: ""   # add the GitHub URL
talk_tag: marc2wiki2bf
featured: true
order: 4
---

## The problem

Library records and Wikidata describe the same books, films, and journals, but they draw the
line between a *work* and its *editions* differently. Wikidata often blurs Work and Edition,
while BIBFRAME keeps Work and Instance distinct. Naive reconciliation links a library record to
the wrong level, or treats a fuzzy title match as a confirmed identity, and pollutes both graphs.

## Approach

MARC2Wiki2BF puts the main recommendation of my
[Journal of Open Humanities Data article](https://doi.org/10.5334/johd.454) into practice: match at
the most specific level you can, keep Work and Instance distinct, and never assert an uncertain
match as fact. I built it with AI-assisted development, using the article's modeling decisions
and my cataloging expertise to direct and verify the code.

**Pipeline:**

1. **Load** MARC21 binary or a CSV/JSON spreadsheet. The column aliases accept exports such as
   Goodreads without renaming.
2. **Reconcile with Wikidata** using identifiers first (ISBN, ISSN, OCLC, LCCN, DOI, VIAF), then
   cleaned title searches.
3. **Verify people.** `$0`/`$1` authority links on name fields (LC NAF, VIAF, ISNI, Wikidata)
   resolve to a person's QID. A fuzzy title candidate gets a boost only if Wikidata credits that
   person as its author, director, screenwriter, creator, or composer.
4. **Classify the level.** SPARQL checks whether each Wikidata match is a work or an edition, so
   the link lands on the correct `bf:Work` or `bf:Instance` node.
5. **Emit BIBFRAME** as Turtle, JSON-LD, RDF/XML, or N-Triples, or push directly to the Blue Core
   API.

**Match confidence decides what gets asserted:**

| Decision | Trigger | What lands in the RDF |
|---|---|---|
| `auto_accept` | Exact identifier match | `rdfs:seeAlso` to the Wikidata QID, on the correct tier |
| `needs_review` | Fuzzy title/author match only | An `rdfs:comment` naming the candidate, with no link |
| `no_match` | Nothing found | Plain local BIBFRAME |

Every record becomes a complete BIBFRAME Work and Instance regardless of match status, and
uncertain matches go to a `needs_review.csv` for a cataloger. Links use `rdfs:seeAlso` rather
than `owl:sameAs`, because the two graphs draw the Work/Instance boundary differently.

## Data model

- Mapped against the Library of Congress's **marc2bibframe2** XSLT, then checked against the
  **BIBFRAME OWL ontology** and against **production records from id.loc.gov**. These two
  rounds of checks found and fixed 11 errors. For example, OCLC numbers are now typed
  `bf:OclcNumber`, primary contributions are double-typed `bf:Contribution, bf:PrimaryContribution`,
  and vocabulary terms are used as resources rather than `rdfs:seeAlso` wrappers.
- Aligned with **Blue Core's Sinopia resource templates** for monograph Works and Instances,
  including the templates' required defaults, an LCSH-only subject filter, and separate Work and
  Instance titles.
- **Deterministic URIs:** UUID5 minting from the local record ID, so re-running the pipeline on
  corrected data reproduces the same URIs.

## Writing to Blue Core

A companion script, `push_to_bcld.py`, writes records straight to the Blue Core development API:

- Authenticates through Keycloak
- POSTs each Work, then its Instance
- Checks for duplicates before every push, by verified identifier match and fuzzy title match,
  and holds possible duplicates for review
- Writes a manifest of every Work and Instance it creates
- Has a dry-run mode that previews every payload without touching the database

A Jupyter notebook walks through the same stages interactively. Its live push is locked behind
an explicit confirmation flag.

## Outcomes

- Tested on real catalog data:
  - 200 sequential records from a 68,100-record export
  - The 200 records richest in identifiers and authority links from the same export
  - 200 academic journals
  - Audiovisual records, which have no 1XX main entry and need a fallback for the primary
    contributor
- Created serial Works and Instances in the Blue Core development environment through the API,
  with a full manifest.
- Includes the *11th International Astronautical Congress* proceedings record used in my DCMI 2026
  keynote. Correctly, it found no confident Wikidata match for review, rather than forcing a link.

## What's next

The README documents the known gaps:

- Relator URIs for additional contributors
- ISBN qualifiers
- Distribution statements
- SuDocs classification
- Name subjects (600–630)
- Typed variant titles
- Meeting names, which are currently typed as `bf:Person`, should be `bf:Meeting`
