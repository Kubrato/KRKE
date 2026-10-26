# One Story, Four Cultures

### A knowledge graph of folktales from Japan, Italy, Germany and Turkey

KRKE group project – Knowledge Representation & Knowledge Extraction (Prof. Aldo Gangemi)

**Team:** Kübra, Johanna, Saya, Andrea

---

## The idea in simple words

The same story often appears in many countries. Cinderella is "Aschenputtel" in Germany (Brothers Grimm) and "La gatta Cenerentola" in Italy (Giambattista Basile, 1634). Folklorists give each kind of story a number in the **ATU index** (Aarne–Thompson–Uther). For example, Cinderella is **ATU 510A**.

Our team is Japanese, Italian, German and Turkish. So we build a knowledge graph that connects folktales from our 4 countries.

The graph has two parts:

1. **Shared tales (the main part).** We pick about 5–10 tale types that exist in several of our countries. Each of us finds the version from their own country. The graph links the versions and shows what is the same and what is different (names, hero, villain, magic objects, ending).
2. **Unique tales (a smaller part).** Each of us adds 2–3 famous tales that exist only in their country (for example Momotarō in Japan, Keloğlan in Turkey).

| Tale type | Germany | Italy | Japan | Turkey |
|---|---|---|---|---|
| Cinderella (ATU 510A) | Aschenputtel (Grimm) | La gatta Cenerentola (Basile) | ? | ? |
| _more types to find_ | | | | |
| Only in one country | | | Momotarō | Keloğlan |

`?` = we still have to search for it.

---

## What we must deliver (from the course)

1. An **ontology** – the schema: classes (Tale, TaleType, Character, Event…) and properties (hasVersion, hasVillain…).
2. A **knowledge graph** – our real data about tales, written as RDF triples.
3. **Knowledge extraction** – get data from real sources (Wikidata, Wikipedia, tale texts) and turn it into RDF.
4. **Links to the web** – connect our tales, authors and characters to Wikidata / DBpedia.
5. **Tests** – our questions written as SPARQL queries that return the right answers.
6. A **presentation** at the end.

The teachers care a lot about the **method** (XD from the slides):
**stories → competency questions → design patterns → ontology → data → SPARQL tests → documentation.**
We should show every step, not only the final graph.

---

## The plan, step by step

### Step 1 – Find the tales (research)

Each person is the expert for one country.

| Country | Who | Where to look |
|---|---|---|
| Germany | ? | Grimm's Kinder- und Hausmärchen (Project Gutenberg), Wikipedia DE |
| Italy | ? | Basile's Pentamerone, Calvino's Fiabe italiane (use summaries), Wikipedia IT |
| Japan | ? | Japanese folktale collections, Wikipedia JA |
| Turkey | ? | Turkish folktales, Nasreddin Hodja, Keloğlan, Wikipedia TR |

Everybody uses Wikidata and the ATU index lists too (Wikidata has a property for the ATU tale type).

**Goal of this step:**
- A list of **5–10 tale types** that exist in at least 2–3 of our countries (ideally all 4).
- **2–3 unique tales** per country.
- For each tale: title (original + English), country, collector/author, year, ATU type, a short English summary, and the Wikidata/Wikipedia link.

Put the list in `docs/tales-list.md`.

**Warning:** if we find very few shared tale types, we talk again before Step 2.

### Step 2 – Write stories (requirements)

A **story** here = a short, concrete sentence about our domain (not a fairy tale!).
Examples:
- _"Aschenputtel, collected by the Brothers Grimm in 1812, is a German version of the Cinderella type (ATU 510A). The heroine is helped by birds and loses a golden shoe."_
- _"In the Italian version by Basile, the heroine is helped by a magic date tree instead of birds."_

We write **3–5 stories** in `docs/stories.md`.

### Step 3 – Competency Questions (CQs)

A **CQ** = a question our knowledge graph must answer. Goal: **10–20 CQs** in `docs/competency-questions.md`.

Examples:
- Which tale types exist in all 4 countries?
- What are the different versions of the Cinderella type, and who collected them?
- Who is the hero / villain / helper in each version of tale type X?
- Which magic objects appear in both Japanese and German tales?
- Which tales exist in only one country?
- Which tales were written down before 1800?
- Which characters are animals?

Negative CQ example (must be impossible): _a tale version that belongs to two different countries of origin._

### Step 4 – Find patterns and existing ontologies (reuse first!)

For each CQ we write: CQ → problem → pattern. Patterns we will probably need:

| Problem | Pattern |
|---|---|
| One tale type has many national versions | **Collection** / **Description & Situation** (the type is a "description", each version "satisfies" it) |
| A character is the hero in one tale and the helper in another | **Role pattern** (Propp's roles: hero, villain, helper, donor, princess, false hero…) |
| "The stepmother gives the heroine a task at the palace" (who + what + whom + where) | **Situation / n-ary event pattern** |
| A tale (the story) vs. a written book / an edition | **Information realization** |
| Places: a village is part of a region, part of a country | **Part-of** |

Look at: http://www.ontologydesignpatterns.org, DOLCE-UltraLite (DUL), schema.org (`CreativeWork`, `Person`, `Place`), FOAF, and Wikidata classes for folktales.

### Step 5 – Design the ontology

- Draw it first (Graffoo in draw.io or yEd), then build it in **Protégé**.
- First draft of classes: `TaleType`, `Tale` (a national version), `Collection` (e.g. Grimm's book), `Collector` (a person), `Character`, `CharacterRole`, `MagicObject`, `PlotEvent`, `Place`, `Country`.
- First draft of properties: `isVersionOf`, `hasATUCode`, `collectedBy`, `publishedIn`, `fromCountry`, `hasCharacter`, `playsRole`, `hasEvent`, `hasAgent`, `hasPatient`, `usesObject`, `takesPlaceIn`.
- Add domain/range, disjoint classes (e.g. a `Character` is not a `Place`).
- Avoid the anti-patterns (a tale version is _not_ a subclass of its type; a collection is _not_ a class).
- Run the **reasoner** (HermiT) → no inconsistencies.
- Save as `ontology/folktales.ttl`.

### Step 6 – Extract the data and convert it to RDF

- **Structured data:** SPARQL queries on Wikidata (tales, ATU types, collectors, dates) → convert with **Python + rdflib**. Scripts go in `scripts/`.
- **Text:** short English summaries of each tale → run them through **FRED** to get characters, events and roles. Then clean the result by hand using our patterns.
- **Entity linking:** DBpedia Spotlight or TagMe on the summaries to find characters and places.
- Raw files go to `data/raw/`, the final graph to `data/kg.ttl`.

This step is the "Knowledge Extraction" half of the course, so we should explain it well in the presentation.

### Step 7 – Link to Wikidata / DBpedia

- Our tales and people: `:Aschenputtel owl:sameAs wd:Q…` (the Wikidata ID).
- Our classes: `owl:equivalentClass` / `rdfs:subClassOf` to DUL, schema.org or DBpedia classes.
- Optional: use SPARQL CONSTRUCT to import extra facts (e.g. birth dates of collectors).

### Step 8 – Load into a triplestore and test

- Load ontology + data into **GraphDB** (or Apache Jena Fuseki).
- Write **every CQ as a SPARQL query** → one `.rq` file per CQ in `queries/`.
- Check the answers. If something is wrong, fix the ontology or the data and test again.
- Check the ontology with **OOPS!** (pitfall scanner).

### Step 9 – Document and publish

- HTML documentation with **LODE**, visual view with **WebVOWL**.
- Update this README: sources, patterns used, how to run the scripts, example queries.

### Step 10 – Presentation

1. The idea: one story, four cultures
2. Stories and competency questions
3. Patterns we reused + ontology diagram
4. Data sources and extraction (Wikidata + FRED)
5. Links to Wikidata / DBpedia
6. Example SPARQL queries + results (e.g. Cinderella across 4 countries)
7. Limits and future work

---

## Who does what

**Everybody:** expert for the tales of their own country (Step 1), plus Steps 2, 3 and 10.

**Technical jobs (suggestion, we can change it):**

| Person | Main job |
|---|---|
| ? | Ontology design in Protégé + diagrams (Steps 4–5) |
| ? | Wikidata queries + conversion scripts (Step 6) |
| ? | Text extraction with FRED + entity linking (Steps 6–7) |
| ? | GraphDB, SPARQL tests, documentation (Steps 8–9) |

We will often work in pairs (XD is like pair programming), so the jobs overlap.

---

## Folder structure

```
KRKE/
├── README.md
├── docs/
│   ├── tales-list.md              # Step 1: the tales we found
│   ├── stories.md                 # Step 2
│   ├── competency-questions.md    # Step 3
│   └── diagrams/
├── ontology/
│   └── folktales.ttl
├── data/
│   ├── raw/                       # downloaded files, summaries
│   └── kg.ttl                     # our knowledge graph
├── scripts/                       # Python / rdflib code
└── queries/                       # one SPARQL file per CQ
```

---

## Tools

| What | Tool |
|---|---|
| Ontology editor + reasoner | Protégé (HermiT / Pellet) |
| Diagrams | Graffoo (draw.io / yEd), WebVOWL |
| Triplestore + SPARQL | GraphDB or Apache Jena Fuseki |
| Data conversion | Python + rdflib, SPARQL CONSTRUCT |
| Text extraction | FRED, DBpedia Spotlight, TagMe |
| Quality check | OOPS!, Protégé reasoner |
| Documentation | LODE, WebVOWL |
| Practise SPARQL | https://query.wikidata.org, https://dbpedia.org/sparql |

---

## Next actions

- [ ] Everyone: read this README
- [ ] Fill in the "Who" column in Step 1 (one country each)
- [ ] Everyone: search tales from your country and add them to `docs/tales-list.md`
- [ ] Meeting: compare lists → choose the 5–10 shared tale types
- [ ] Split the technical jobs
- [ ] Write the first stories and competency questions
