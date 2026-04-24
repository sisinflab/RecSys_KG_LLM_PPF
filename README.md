# LLM+KG RecSys Companion Repository

Companion repository for the paper **"From Side Information and Knowledge Graphs to Large Language Models: Two Decades of Knowledge Integration in Recommender Systems"**.

This repo organizes the attached project materials into a GitHub-ready structure: the paper PDF, a machine-readable paper corpus, extracted notes, a timeline of the field, and a forward-looking agenda for hybrid LLM+KG recommender systems.

## Why this repo exists

The central argument of the paper is that recommender systems did **not** evolve through simple replacement cycles. Instead, they evolved through a sequence of **representational translations**:

1. **Rules and constraints** made knowledge explicit, inspectable, and controllable.
2. **Side information and feature models** made that knowledge more scalable.
3. **Linked open data and knowledge graphs** reintroduced structure, semantics, and explanation.
4. **LLMs** increased interaction bandwidth, natural-language reasoning, and generative flexibility.

The paper argues that the strongest future systems will be **hybrid**, not purely generative: LLMs should act as a powerful interaction and reasoning layer, while explicit knowledge stores remain essential for grounding, traceability, reproducibility, and responsible deployment.

## Research questions covered by the paper

### RQ1 — Representational translation
How did external knowledge move from constraints and rules to features, graphs, embeddings, and natural language, and what was gained or lost at each step?

### RQ2 — Recurring design patterns
Which design patterns keep returning across eras, even when the model family changes?

### RQ3 — Responsible knowledge integration
What new risks appear when recommendation becomes generative and conversational, and how do they relate to older goals such as traceability, fairness, and user control?

## Corpus snapshot

- **136** paper records
- Coverage from **2007** to **2026**
- **98** records from the main **RecSys** venue
- Era split:
  - **2007–2014:** 7 papers
  - **2015–2022:** 29 papers
  - **2023–2026:** 100 papers

Largest keyword groups in the spreadsheet:

| Group | Papers |
|---|---:|
| RecSys LLM | 46 |
| RecSys Large Language Model | 38 |
| RecSys Knowledge Graph | 19 |
| RecSys Knowledge Based | 13 |
| RecSys side information | 9 |
| RecSys Linked open data | 4 |

## Historical reading path

### 1) Rules, constraints, and side information (2007–2014)
A first phase focused on explicit knowledge engineering, personalized query repair, semantic enrichment, and early side-information pipelines.

Representative works:
- *A multiagent knowledge-based recommender approach with truth maintenance* (2007)
- *Personalized query relaxations and repairs in knowledge-based recommendation* (2009)
- *Knowledge infusion into content-based recommender systems* (2009)
- *Sparse linear methods with side information for top-n recommendations* (2012)
- *Top-N recommendations from implicit feedback leveraging linked open data* (2013)

### 2) Knowledge graphs, embeddings, and explainability (2015–2022)
This phase emphasized KG traversal, semantic reasoning, graph-aware embeddings, and human-facing explanations.

Representative works:
- *Personalized Recommendations using Knowledge Graphs: A Probabilistic Logic Programming Approach* (2016)
- *Meta-Prod2Vec: Product Embeddings Using Side-Information for Recommendation* (2016)
- *ExpLOD: A Framework for Explaining Recommendations based on the Linked Open Data Cloud* (2016)
- *entity2rec* (2017)
- *Recurrent knowledge graph embedding for effective recommendation* (2018)
- *Knowledge-aware Recommendations Based on Neuro-Symbolic Graph Embeddings and First-Order Logical Rules* (2022)

### 3) LLMs, retrieval augmentation, and agentic recommender systems (2023–2026)
The newest phase treats language as a substrate for preference elicitation, explanation, sequential recommendation, retrieval augmentation, and interactive recommendation agents.

Representative works:
- *Large Language Models are Competitive Near Cold-start Recommenders for Language- and Item-based Preferences* (2023)
- *TALLRec* (2023)
- *Retrieval-augmented Recommender System* (2023)
- *KGGLM* (2024)
- *Reproducibility of LLM-based Recommender Systems: the Case Study of P5 Paradigm* (2024)
- *Privacy Risks of LLM-Empowered Recommender Systems* (2025)
- *Consistent Explainers or Unreliable Narrators?* (2025)
- *A Tutorial on Agentic LLM for Recommender Systems* (2025)
- *LRSA: LLM-RecSys alignment for time-specific next POI recommendation* (2026)

## Recurring design patterns distilled from the paper

1. **Fight sparsity with external knowledge**
   - Rules, metadata, graphs, and language all serve as surrogate signal when user-item interaction data is weak.
2. **Keep reasons communicable**
   - Human-readable structure matters for explanations, trust, critique handling, and user control.
3. **Separate heavy offline enrichment from lightweight online serving**
   - This appears across side-information models, KG-enhanced recommenders, distillation pipelines, and LLM teacher-student setups.
4. **Hybridize rather than replace**
   - The strongest systems combine retrieval, ranking, graph structure, metadata, and language rather than treating them as mutually exclusive paradigms.

## Forward-looking thesis for 2026–2030

The attached future-prediction notes extend the paper into a concrete engineering agenda. The main themes are:

- **Hybrid retrieval + ranking + LLM stacks** instead of fully free-form generation.
- **Teacher-student distillation** so LLM reasoning can improve low-latency serving systems.
- **Multimodal grounding** through deeper alignment across text, vision, and audio.
- **Agentic architectures** where specialized recommendation agents coordinate through explicit protocols.
- **Governance, fairness, privacy, and hallucination controls** as measurable system requirements rather than optional add-ons.

See `docs/future_agenda_2026_2030.md` for a compact synthesis.

## Suggested use

### For reading the paper
Start with:
- `paper/LLM_KG_companion_paper.pdf`
- `docs/research_questions.md`
- `docs/timeline.md`
- `docs/recurring_patterns.md`

### For literature review work
Use:
- `data/papers_master.csv`
- `data/llm_kg_focus_subset.csv`
- `data/bibliography.bib`
- `data/pdf_manifest.csv`

### For extending the project
Use:
- `notes/progress_info_retrieval_project_papers_notes.md`
- `notes/recommender_systems_future_prediction.md`
- `scripts/build_exports.py`

## Repository structure

```text
llm-kg-recsys-companion/
├── README.md
├── NOTICE.md
├── data/
├── docs/
├── notes/
├── paper/
├── papers/
├── scripts/
└── source_materials/
```

## Notes on raw PDFs

The attached archive `RecSys_Papers 2.zip` is larger than the standard single-file size GitHub comfortably handles. To keep this repo GitHub-ready, the archive is **not** committed into the repository itself.

Instead, this repo includes:
- a bibliography export,
- a PDF filename manifest,
- the original spreadsheet,
- and guidance in `papers/README.md` for restoring the raw paper archive locally or via Git LFS / external storage.

## Citation

If you use this repository, cite the paper and, when relevant, the curated literature spreadsheet included under `source_materials/`.
