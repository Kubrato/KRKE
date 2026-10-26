# KRKE – Group Project

Knowledge Representation & Knowledge Extraction (Prof. Aldo Gangemi)

**Team:** Kübra, Johanna, Saya, Andrea

**Topic:** _not chosen yet – see [Step 1](#step-1--choose-the-topic-together)_

---

## What do we have to do? (short version)

The exam is this group project. We must:

1. **Choose a topic** (we pick it ourselves).
2. **Build an ontology** – the "schema": classes (Person, Song, Event…) and properties (performedBy, hasDate…).
3. **Build a knowledge graph (KG)** – the real data, written as RDF triples that follow our ontology.
4. **Use knowledge extraction** – get the data out of real sources (CSV, websites, text) and turn it into RDF.
5. **Link our data to the web** – connect our entities to DBpedia / Wikidata (`owl:sameAs`).
6. **Test it** – write our questions as SPARQL queries and show they return the right answers.
7. **Present the project** at the end.

The teachers care a lot about the **method** (the XD method from the slides):
**stories → competency questions → design patterns → ontology → data → SPARQL tests → documentation.**
So we should show every step, not only the final graph.

---

## The plan, step by step

### Step 1 – Choose the topic together

A good topic for this course has:

- **Data we can actually get** (a CSV, a Wikipedia table, an open dataset, or text).
- **Events with many parts**: who + what + when + where (this lets us use the n-ary / Situation pattern, which the professor loves).
- **People with roles** (singer, director, player…) and **groups** (bands, teams, juries).
- **Entities that exist in DBpedia / Wikidata**, so we can link to them.
- **Not too big.** A few hundred to a few thousand entities is enough.

Some ideas (we can also propose our own):

| Idea | Why it fits | Possible data sources |
|---|---|---|
| **Eurovision Song Contest** | Song + artist + country + year + points + jury/televote → perfect n-ary situations | Kaggle / GitHub Eurovision datasets, Wikidata, Wikipedia tables |
| **Film festivals (Venice, Cannes, Berlin)** | Film + director + award + edition + jury → roles and events | Wikidata, Wikipedia lists, IMDB |
| **Music bands and members over time** | Same as the course homework: person + role + band + album + time | Wikidata, DBpedia, MusicBrainz |
| **Nobel Prizes** | Person + prize + year + affiliation + motivation (free text → FRED) | Nobel Prize open API, Wikidata |
| **Cultural heritage in a city (e.g. Bologna)** | Can reuse and link to ArCo, the course's main example | ArCo SPARQL endpoint, city open data portals |

**How we decide:** each person looks at 1–2 ideas for ~30 min, checks if the data really exists and is easy to download, then we vote.

### Step 2 – Write stories (requirements)

A **story** is a short, concrete sentence about the domain.
Example: _"Måneskin represented Italy at Eurovision 2021 with the song 'Zitti e buoni' and won with 524 points."_

- Each person writes 2–3 stories → we keep the best **3–5**.
- Put them in `docs/stories.md`.

### Step 3 – Turn stories into Competency Questions (CQs)

A **CQ** is a question our KG must be able to answer.

- "Which countries won Eurovision more than once?"
- "Who performed for Italy in 2021, and which song?"
- "Which artists performed in more than one edition?"

Goal: **10–20 CQs**, in `docs/competency-questions.md`.
Optional: a few **negative CQs** (things that must be impossible, e.g. "a song with two different winning ranks in the same year").

### Step 4 – Look for existing ontologies and patterns (reuse first!)

Before inventing anything, check:

- **Ontology Design Patterns:** http://www.ontologydesignpatterns.org (Situation, Role, Collection, Part-of, Time-indexed…)
- **Existing vocabularies:** schema.org, FOAF, DOLCE-UltraLite (DUL), ArCo, CIDOC-CRM, Music Ontology.

For each CQ, write which pattern solves it (a small table: CQ → problem → pattern), like the Ferguson example in the slides.

### Step 5 – Design the ontology

- Draw it first (Graffoo in draw.io or yEd), then build it in **Protégé**.
- Classes, object properties, datatype properties, domain/range, `subClassOf`, disjoint classes.
- Use the **Situation / n-ary pattern** for events with many parts.
- Avoid the anti-patterns (a city is _part of_ a country, not a _subclass_; a band is a _collection_, not a class…).
- Run the **reasoner** (HermiT) → no inconsistencies.
- Save as `ontology/ontology.ttl`.

### Step 6 – Extract the data and convert it to RDF

- Download the raw data into `data/raw/`.
- Convert it to RDF with **Python + rdflib** (or csv2rdf / SPARQL CONSTRUCT). Script goes in `scripts/`.
- If we have free text (biographies, descriptions), try **FRED** or entity linking (DBpedia Spotlight / TagMe) on some sentences – this shows the "extraction" part of the course.
- Output: `data/kg.ttl`.

### Step 7 – Link to DBpedia / Wikidata

- Our entities: `:Maneskin owl:sameAs dbr:Måneskin` (or the Wikidata ID).
- Our classes: `owl:equivalentClass` / `rdfs:subClassOf` to DBpedia, schema.org or DUL classes.
- Optional: use SPARQL CONSTRUCT on DBpedia/Wikidata to import extra facts.

### Step 8 – Load into a triplestore and test

- Load ontology + data into **GraphDB** (or Apache Jena Fuseki).
- Write **every CQ as a SPARQL query** → save in `queries/` (one `.rq` file per CQ).
- Check: does each query return the right answer? If not, fix the ontology or the data and repeat.
- Check the ontology with **OOPS!** (pitfall scanner).

### Step 9 – Document and publish

- Generate HTML docs with **LODE** (or WebVOWL for a visual view).
- Update this README: topic, sources, patterns used, how to run the scripts, example queries.
- Everything stays in this GitHub repo.

### Step 10 – Prepare the presentation

Suggested order of the slides:

1. Problem / domain and goal
2. Stories and competency questions
3. Patterns we reused + ontology diagram
4. Data sources and extraction pipeline
5. Linking to DBpedia / Wikidata
6. Example SPARQL queries + results
7. Limits and future work

---

## Who does what (suggestion – we can change it)

Everybody joins Steps 1–3 and 10. After that:

| Person | Main job |
|---|---|
| ? | Ontology design in Protégé + diagrams (Steps 4–5) |
| ? | Data collection + conversion scripts (Step 6) |
| ? | Entity linking + text extraction with FRED (Step 7) |
| ? | GraphDB, SPARQL tests, documentation (Steps 8–9) |

We will often work in pairs (XD is like pair programming), so the jobs overlap.

---

## Planned folder structure

```
KRKE/
├── README.md
├── docs/
│   ├── stories.md
│   ├── competency-questions.md
│   └── diagrams/
├── ontology/
│   └── ontology.ttl
├── data/
│   ├── raw/          # original downloaded files
│   └── kg.ttl        # our knowledge graph
├── scripts/          # Python / rdflib conversion code
└── queries/          # one SPARQL file per competency question
```

---

## Tools

| What | Tool |
|---|---|
| Ontology editor + reasoner | Protégé (HermiT / Pellet) |
| Diagrams | Graffoo (draw.io / yEd), WebVOWL |
| Triplestore + SPARQL | GraphDB or Apache Jena Fuseki |
| Data conversion | Python + rdflib, csv2rdf, SPARQL CONSTRUCT |
| Text extraction | FRED, DBpedia Spotlight, TagMe |
| Quality check | OOPS!, Protégé reasoner |
| Documentation | LODE, WebVOWL |
| Practise SPARQL | https://dbpedia.org/sparql, https://query.wikidata.org, https://dati.beniculturali.it/sparql |

---

## Next actions

- [ ] Everyone: read this README
- [ ] Everyone: check 1–2 topic ideas (is the data really available?)
- [ ] Meeting: choose the topic and split the roles
- [ ] Write the first stories and competency questions
