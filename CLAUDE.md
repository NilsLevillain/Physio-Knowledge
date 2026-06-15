# Pelvic Floor Physiotherapy Knowledge Base

## Mission

Long-term clinical knowledge graph for pelvic floor and ano-rectal physiotherapy. Markdown files are the source of truth. Goal: durable, interconnected clinical knowledge — not a collection of summaries.

Must stay: human-readable, LLM-readable, Git-friendly, Obsidian-friendly.

## Domain Scope

**Primary:** pelvic floor physiotherapy, ano-rectal disorders, urinary/fecal incontinence, pelvic organ prolapse, chronic pelvic pain, sexual dysfunction, constipation, postpartum rehabilitation, women's health, pediatric perineal care, transgender care.

**Secondary:** anatomy, biomechanics, pain science, behavioral interventions, evidence-based practice.

## Directory Layout

```
raw/articles/      # PDFs, papers, conference proceedings (immutable)
raw/attachments/   # Images and binary files
wiki/              # Knowledge graph
wiki/index.md      # Catalog of all pages
wiki/queries/      # Temporary query outputs
outputs/reports/   # Lint and maintenance reports
log.md             # Append-only operation log
```

## Core Principles

- **Files are memory.** Never rely on conversation history. Persist knowledge into markdown.
- **Update before creating.** Search existing pages first. Prefer updating over creating.
- **One concept = one page.** `stress-urinary-incontinence.md` ✓ — `sui.md`, `stress-incontinence.md` ✗
- **Build relationships.** Pages should link to related anatomy, assessments, treatments, concepts. A page in isolation is incomplete.
- **Clinical utility first.** Practical over verbose. Preserve evidence levels and nuance.

## Note Types & Frontmatter

All notes use:
```yaml
---
date: YYYY-MM-DD
type: concept | anatomy | assessment | treatment | clinical-case | guideline | patient-faq | source-summary
status: active
tags: []
---
```

| Type | Use for | Key sections |
|---|---|---|
| `concept` | Conditions, symptoms, mechanisms | Definition · Epidemiology · Risk Factors · Mechanisms · Symptoms · Assessment · Treatment · Clinical Pearls · Evidence Notes · Related Concepts |
| `anatomy` | Anatomical structures | Structure · Anatomy · Function · Clinical Relevance · Related Conditions |
| `assessment` | Tests, scales, examinations | Purpose · Procedure · Interpretation · Limitations · Related Conditions |
| `treatment` | Interventions, protocols | Indications · Contraindications · Protocol · Evidence · Clinical Pearls |
| `clinical-case` | Real patient scenarios | Patient Profile · Symptoms · Assessment · Differential · Treatment Plan · Follow-Up · Learning Points |
| `guideline` | Official recommendations | Scope · Recommendations · Evidence Levels · Related Concepts |
| `patient-faq` | Common patient questions | Short Answer · Clinical Explanation · Practical Advice · When To Seek Help |
| `source-summary` | Ingested sources | Citation · Summary · Key Findings · Clinical Recommendations · Evidence Level · Related Concepts |

## Naming Conventions

- Lowercase kebab-case filenames only: `levator-ani.md`, `pelvic-floor-muscle-training.md`
- No abbreviations in filenames — abbreviations belong inside content
- Wiki is primarily in **French** (reflecting source material)

## Linking Rules

- Use Obsidian wikilinks only: `[[stress-urinary-incontinence]]` ✓ — plain text ✗
- Every page should link to relevant anatomy, assessments, treatments, guidelines, and concepts

## Source Ingestion Workflow

1. Read source → create/update `source-summary`
2. Extract: concepts, anatomy, assessments, treatments, guidelines
3. Update existing pages before creating new ones
4. Update `wiki/index.md`
5. Append entry to `log.md`

Always distinguish evidence quality: high / moderate / low / expert opinion.

## Query Workflow

1. Read `wiki/index.md`
2. Navigate linked pages
3. Synthesize answer with wikilink citations
4. Save output to `wiki/queries/`
5. Suggest promoting durable findings to permanent pages

## Lint Checks

Report: orphan pages, duplicate concepts, broken links, missing backlinks, missing source references, contradictory recommendations, empty sections.

## Logging

Append-only. Format: `YYYY-MM-DD | operation | title` + one-line description.
Operations: `ingest` · `compile` · `query` · `promote` · `lint` · `remove`

## Git Rules

Do not commit unless explicitly requested. The repository owner controls commits.
