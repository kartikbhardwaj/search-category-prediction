# Search Annotation Auditor

Lightweight workspace for exploring the Shopping Queries ESCI dataset and running LLM-based audits / tag extraction.

Contents
- search_auditor notebook: [search_auditor.ipynb](search_auditor.ipynb)
- data loader: [data_loader.py](data_loader.py)
- requirements: [requirements.txt](requirements.txt)
- raw dataset: [data/shopping_queries_dataset_examples.parquet](data/shopping_queries_dataset_examples.parquet), [data/shopping_queries_dataset_products.parquet](data/shopping_queries_dataset_products.parquet), [data/shopping_queries_dataset_sources.csv](data/shopping_queries_dataset_sources.csv)
- processed output: [processed_data/shopping_queries_dataset_esci_E_with_tags.xlsx](processed_data/shopping_queries_dataset_esci_E_with_tags.xlsx)
- audit/export: [output_data/shopping_queries_dataset_esci_E_audit_samples.xlsx](output_data/shopping_queries_dataset_esci_E_audit_samples.xlsx)
- interim results: [interim_results/shopping_queries_single_llm_dspy_results.xlsx](interim_results/shopping_queries_single_llm_dspy_results.xlsx), [interim_results/shopping_queries_multiple_llm_dspy_results.xlsx](interim_results/shopping_queries_multiple_llm_dspy_results.xlsx), [interim_results/shopping_queries_single_llm_langchain_results.xlsx](interim_results/shopping_queries_single_llm_langchain_results.xlsx)

Quick start

1) Create Python environment and install deps
```bash
# Linux / macOS
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

2) Inspect raw data
- Examples and products are available in [data/shopping_queries_dataset_examples.parquet](data/shopping_queries_dataset_examples.parquet) and [data/shopping_queries_dataset_products.parquet](data/shopping_queries_dataset_products.parquet).
- Sources (query metadata) are in [data/shopping_queries_dataset_sources.csv](data/shopping_queries_dataset_sources.csv).

3) Open and run the exploration notebook
- Open [search_auditor.ipynb](search_auditor.ipynb) in VSCode / JupyterLab and run cells interactively.
- Or run headless:
```bash
jupyter nbconvert --to notebook --execute search_auditor.ipynb --inplace
```
Notes:
- The notebook demonstrates loading the data, generating tags, and running LLM audits (uses local Ollama in the examples).
- The notebook references dspy and Chat/Ollama configurations; adjust model endpoints if you are not running Ollama locally.

4) Where outputs are written
- Processed dataset with tags: [processed_data/shopping_queries_dataset_esci_E_with_tags.xlsx](processed_data/shopping_queries_dataset_esci_E_with_tags.xlsx)
- Audit sample exports: [output_data/shopping_queries_dataset_esci_E_audit_samples.xlsx](output_data/shopping_queries_dataset_esci_E_audit_samples.xlsx)
- Intermediate experiment results: see [interim_results/](interim_results/)

Useful commands and tips
- Run Jupyter: jupyter lab or code --install-extension ms-toolsai.jupyter (VSCode builtin)
- Re-generate processed Excel:
  - Run the preprocessing cells in [search_auditor.ipynb](search_auditor.ipynb)
- If you use local LLM servers (Ollama), start them before running notebook cells that invoke models. Notebook examples use ports like 11434 / 11435 (see notebook cells).

References
- Dataset README: [data/README.md](data/README.md) — dataset description and task definitions.
- Notebook entrypoints: [search_auditor.ipynb](search_auditor.ipynb)