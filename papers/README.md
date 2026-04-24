# Managing the raw paper PDFs

The attached archive `RecSys_Papers 2.zip` is about **116.7 MB**, which makes it awkward to commit directly into a standard GitHub repository.

This repository therefore keeps the paper collection indirect and reproducible:

- `data/pdf_manifest.csv` maps paper metadata to likely ACM-style PDF filenames.
- `data/bibliography.bib` provides a clean bibliography export.
- `source_materials/History_20_RecSys_Combined.xlsx` preserves the original spreadsheet.

## Recommended options

### Option 1 — Keep the PDF archive outside Git
Store the zip in cloud storage or a release asset and point to it from the README.

### Option 2 — Use Git LFS
If the project needs raw PDFs inside version control, place them under `papers/raw/` and manage them with Git LFS.

### Option 3 — Keep only a curated subset in Git
Commit only the small set of cornerstone papers that are repeatedly cited in the paper, and keep the full archive external.

## Local reconstruction

If you have the original archive, place it next to the repository root and extract it locally. The manifest file can be used to map ACM-style filenames back to titles and DOIs.
