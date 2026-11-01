---
tags:
- curatorkit
configs:
- config_name: sft_alpaca
  default: true
  description: curatorkit sft_alpaca export, sha256 1fc8e419da3ce707f3c4a282d27862993e01235186ce759d382dda6f081e49a4
  data_files:
  - split: train
    path: sft_alpaca.jsonl
---

# Dataset Card: curatorkit_run

## Summary

- **Run timestamp**: 2026-11-01T00:41:14.141853Z
- **Wall clock time**: 0.0s
- **Pipeline config hash**: `1a37577fa4fdb7b6`

## Source Documents

  - Unknown

## Pipeline Stages

| Step | Input | Passed | Recovered | Rejected | Forward |
|------|-------|--------|-----------|----------|---------|
| JSONLReader | 12 | 12 | — | 0 | 12 |
| SchemaGate | 12 | 12 | 0 | 0 | 12 |
| ExactDeduplicator | 12 | 12 | — | — | 12 |
| TextCleaner | 12 | 12 | — | — | 12 |
| AlpacaExporter | — | 12 | — | — | 12 |

## Gate Pass Rates and Rejection Breakdown

- **JSONLReader**: 12/0 passed (N/A), 0 rejected
- **SchemaGate**: 12/12 passed (100.0%), 0 rejected


**Rejection reasons:**
  - None

## Deduplication

  - exact_duplicates_removed: 0

## Known Limitations

- No MinHash deduplication applied.
- Table extraction requires `extract_tables: true` on the PDF reader and MinerU with GPU support. Disabled by default.
- Token counting uses a whitespace tokenizer by default. For exact LLM context window
  enforcement, enable `use_tiktoken: true` in the SchemaGate config.
- Both within-run (MinHash/Diversity) and cross-run (EmbeddingDeduplicator) deduplication
  are available. Cross-run dedup persists an embedding index across runs; use
  `embedding_reset_index: true` to start fresh.

## Reproduction

```bash
pip install curatorkit
curatorkit run pipeline.yaml --output-dir ./out/
```

## Tool Versions

- **curatorkit**: 0.1.22
- **python**: 3.13.16

## Configs

Load one with `datasets.load_dataset("<this folder or Hub repo>", "<config>")`.

| Config | Splits (rows) | Columns |
|--------|---------------|---------|
| `sft_alpaca` | train (12) | `instruction`: string<br>`input`: string (empty when there is no input)<br>`output`: string |
