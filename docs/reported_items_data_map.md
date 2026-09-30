# Manuscript Table/Figure Data Map

This file maps reported manuscript items to text-free per-example result files in this artifact.

| Manuscript item | Supporting file(s) |
|---|---|
| Main semantic-label gains and Figure 1 | `results/main_semantic_baseline_per_id.csv` |
| Full semantic-label appendix baseline | `results/main_semantic_baseline_per_id.csv` |
| Alternative-sample appendix tables | `samples/alternative_sample_ids.csv`; `results/alternative_sample_semantic_baseline_per_id.csv` |
| ABC-only residuals | `results/abc_only_per_id.csv` |
| Anchored contrasts and diagnostic ladder | `results/anchored_abc_per_id.csv`; `results/abc_only_per_id.csv`; `results/main_semantic_baseline_per_id.csv` |
| Mapping variance and option-bias appendix | `results/abc_only_per_id.csv`; `results/anchored_abc_per_id.csv`; `config/abc_mappings.json` |
| Semantic-output control | `results/semantic_output_anchor_per_id.csv`; `results/anchored_abc_per_id.csv` |
| Per-label F1 appendix | `results/main_semantic_baseline_per_id.csv`; `results/abc_only_per_id.csv`; `results/anchored_abc_per_id.csv`; `results/semantic_output_anchor_per_id.csv` |
| Gain decomposition table and figure | `results/main_semantic_baseline_per_id.csv`; `results/abc_only_per_id.csv`; `results/anchored_abc_per_id.csv` |
| Supplementary alternate Chinese-label tables | `results/alternate_chinese_labels_per_id.csv` |
| Supplementary Qwen3-8B label-language swap tables | `results/qwen3_8b_label_language_swap_per_id.csv` |
| Supplementary Llama-3.1-8B ABC-only boundary tables | `results/llama8_abc_boundary_per_id.csv` |
| A/B/C mappings appendix | `config/abc_mappings.json` |

All files exclude premise and hypothesis text, provider response IDs, timestamps, request hashes, source run filenames, row UUIDs, local paths, and raw prompts.
