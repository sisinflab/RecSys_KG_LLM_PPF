# LLM+KG RecSys Companion Repository

Companion repository for the paper **"From Side Information and Knowledge Graphs to Large Language Models: Two Decades of Knowledge Integration in Recommender Systems"**.

- **Paper:** <https://dl.acm.org/doi/10.1145/3773078.3831782> (DOI: `10.1145/3773078.3831782`)
- **Authors:** Claudio Pomo, Diego Baquero Sanz, Liam Claude Morris, Ludovico Boratto, Fedelucio Narducci, Tommaso Di Noia
- **Affiliations:** Politecnico di Bari and University of Cagliari

This repository accompanies the article with the data behind it: the machine-readable corpus of surveyed papers, derived statistics, a bibliography, a timeline of the field, and a forward-looking agenda for hybrid LLM+KG recommender systems. It is meant to help you **reproduce the corpus statistics, find and cite the surveyed works, and reuse the material** for your own literature reviews.

## Table of contents

- [Repository structure](#repository-structure)
- [Quick start](#quick-start)
- [Data dictionary](#data-dictionary)
- [Why this repo exists](#why-this-repo-exists)
- [Research questions](#research-questions-covered-by-the-paper)
- [Corpus snapshot](#corpus-snapshot)
- [Historical reading path](#historical-reading-path)
- [Recurring design patterns](#recurring-design-patterns-distilled-from-the-paper)
- [Forward-looking thesis](#forward-looking-thesis-for-20262030)
- [Reproducibility notes](#reproducibility-notes)
- [Citation](#citation)
- [Contributing and feedback](#contributing-and-feedback)

## Repository structure

```
.
├── README.md
├── data/
│   ├── papers_master.csv          # all 136 surveyed papers (one row per paper)
│   ├── llm_kg_focus_subset.csv    # subset used for the LLM+KG focus
│   ├── bibliography.bib           # BibTeX entries for the surveyed papers
│   ├── keyword_group_counts.csv   # papers per search keyword group
│   ├── yearly_counts.csv          # papers per publication year
│   └── pdf_manifest.csv           # expected ACM-style PDF filename per paper (PDFs are not included)
├── docs/
│   ├── README.md                  # index of the docs
│   ├── research_questions.md      # RQ1-RQ3 of the paper
│   ├── timeline.md                # timeline of representative papers
│   ├── recurring_patterns.md      # cross-era design patterns
│   ├── future_agenda_2026_2030.md # engineering agenda for 2026-2030
│   └── corpus_summary.md          # corpus statistics
└── scripts/
    └── build_exports.py           # reference for generating the CSV/BibTeX exports (currently non-runnable: BibTeX writer has malformed string literals)
```

## Quick start

Clone the repository and explore the corpus with any CSV tool. For example, with Python and pandas:

```python
import pandas as pd

papers = pd.read_csv("data/papers_master.csv")

# Papers per year
print(papers["year"].value_counts().sort_index())

# LLM-related papers
llm = papers[papers["found_by_keywords"].str.contains("LLM|Large Language Model", na=False)]
print(llm[["year", "title", "doi"]].head())
```

To use the bibliography in LaTeX, add `data/bibliography.bib` to your project and cite entries by their key (e.g. `\cite{DBLP:conf/recsys/Lorenzi07}`).

## Data dictionary

`data/papers_master.csv` and `data/llm_kg_focus_subset.csv` share these columns:

| Column | Description |
|---|---|
| `year` | Publication year |
| `title` | Paper title |
| `venue` | Publication venue (e.g. `RecSys`) |
| `doi` | DOI of the paper |
| `pdf_file_hint` | Expected PDF filename derived from the ACM DOI (`10.1145/<suffix>` becomes `<suffix>.pdf`) |
| `authors` | Author list as exported from the source database (formats vary across rows) |
| `found_by_keywords` | Search keyword group(s) through which the paper was found |
| `dblp_url` | DBLP record URL |
| `scholar_citations`, `scopus_citations`, `semantic_citations` | Citation counts from Google Scholar, Scopus and Semantic Scholar at collection time (may be empty) |
| `source_id` | DBLP record key; the BibTeX key in `bibliography.bib` is this value prefixed with `DBLP:` |

Other files: `keyword_group_counts.csv` (`keyword_group`, `paper_count`), `yearly_counts.csv` (`year`, `paper_count`), `pdf_manifest.csv` (`year`, `title`, `doi`, `pdf_file_hint`, `notes`).

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

The future-prediction notes in this repository extend the paper into a concrete engineering agenda. The main themes are:

- **Hybrid retrieval + ranking + LLM stacks** instead of fully free-form generation.
- **Teacher-student distillation** so LLM reasoning can improve low-latency serving systems.
- **Multimodal grounding** through deeper alignment across text, vision, and audio.
- **Agentic architectures** where specialized recommendation agents coordinate through explicit protocols.
- **Governance, fairness, privacy, and hallucination controls** as measurable system requirements rather than optional add-ons.

See `docs/future_agenda_2026_2030.md` for a compact synthesis.

## Reproducibility notes

- The files in `data/` are the released snapshot of the corpus. Citation counts reflect the time of collection and will differ from current values.
- The full-text PDFs of the surveyed papers are **not** redistributed here; use `pdf_manifest.csv` and the DOIs to retrieve them from their publishers.
- `scripts/build_exports.py` documents how the CSV and BibTeX exports were generated from the source spreadsheet (`source_materials/History_20_RecSys_Combined.xlsx`, not included in this repository). It is currently non-runnable because its BibTeX writer contains malformed string literals. It requires `python-docx` and `openpyxl`.

## Citation

If you use this repository or the accompanying paper, please cite:

```bibtex
@inproceedings{pomo2026sideinfo_kg_llm,
  author    = {Pomo, Claudio and Baquero Sanz, Diego and Morris, Liam Claude and Boratto, Ludovico and Narducci, Fedelucio and Di Noia, Tommaso},
  title     = {From Side Information and Knowledge Graphs to Large Language Models: Two Decades of Knowledge Integration in Recommender Systems},
  year      = {2026},
  publisher = {ACM},
  doi       = {10.1145/3773078.3831782},
  url       = {https://dl.acm.org/doi/10.1145/3773078.3831782}
}
```

## Contributing and feedback

Found a missing paper, a wrong DOI, or a metadata error? Please open an issue or pull request describing the correction.
