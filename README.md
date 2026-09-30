# Prompt as Stratified Interface: Reproducibility Artifact

This is the public, text-free reproducibility artifact accompanying **“Prompt as Stratified Interface: Decomposing Label-Mediated Effects in Chinese-English NLI”** by Hua Zhao, Zhiqing Yang, and Michelle Mingyue Gu.

Repository: <https://github.com/zhao4hua4/stratified-prompt-interface>

This artifact corresponds to the camera-ready manuscript (`stratified_interface_v18_camera_ready.tex`) and is published directly on the repository's `main` branch.

## What is included

- `samples/main_sample_ids.csv`: identifiers and labels for the main balanced XNLI sample.
- `samples/alternative_sample_ids.csv`: identifiers and labels for the disjoint alternative sample used in the appendix representativeness check.
- `results/main_semantic_baseline_per_id.csv`: per-example semantic-label baseline results for all models reported in the paper.
- `results/alternative_sample_semantic_baseline_per_id.csv`: per-example alternative-sample semantic-label baseline results reported in the appendix.
- `results/abc_only_per_id.csv`: per-example ABC-only diagnostic results for Qwen3-8B and Llama-3.1-70B across all six mappings.
- `results/anchored_abc_per_id.csv`: per-example instruction-matched anchored-ABC results reported in the paper.
- `results/semantic_output_anchor_per_id.csv`: per-example semantic-output control results for the selected reported conditions.
- `results/alternate_chinese_labels_per_id.csv`: per-example alternate Chinese-label results reported in the supplementary appendix.
- `results/qwen3_8b_label_language_swap_per_id.csv`: per-example Qwen3-8B label-language swap results reported in the supplementary appendix.
- `results/llama8_abc_boundary_per_id.csv`: per-example Llama-3.1-8B ABC-only boundary-check results reported in the supplementary appendix.
- `config/api_and_model_config.json`: provider endpoint, model name, model specification, decoding, and thinking-control metadata without API keys.
- `config/abc_mappings.json`: all six A/B/C mappings used in the diagnostic regimes.
- `config/prompt_version_ids.json`: prompt version identifiers used by each reported result set.
- `docs/reported_items_data_map.md`: map from manuscript tables/figures/appendix items to artifact files.
- `manifest.json`: row counts, file checksums, and basic result-file diagnostics.

## What is excluded

The artifact intentionally excludes original XNLI text. It does not include premises, hypotheses, prompts, API keys, provider response IDs, timestamps, row UUIDs, request hashes, local absolute paths, source run filenames, token-use logs, raw scripts, or exploratory runs that are not reported in the paper.

Raw model outputs are released only when the output is exactly an allowed label or option symbol (`A`, `B`, `C`, `entailment`, `neutral`, `contradiction`, `蕴含`, `中立`, `矛盾`, `可推出`, `无法确定`, or `冲突`). Non-label invalid outputs are withheld to avoid accidental release of dataset text or provider-specific messages.

## Deduplication policy

Some run logs contain repair rows. For each run file, rows are deduplicated by `example_id`, and the last logged row is retained. This matches the repair-aware result summaries used in the manuscript.

## Reconstructing reported metrics

Accuracy can be computed as the mean of `correct == True` over the relevant rows. Macro-F1 can be computed from `gold_label` and `parsed_label`, treating invalid or error rows as incorrect with no parsed label. ABC and anchored regimes should be grouped by `model_name`, `condition_id`, and `mapping_id`; mapping-averaged statistics average over all six mappings. CN-interface gain is computed as:

- Chinese input: `accuracy(ZH-ZH) - accuracy(ZH-EN)`
- English input: `accuracy(EN-ZH) - accuracy(EN-EN)`

## Dataset reconstruction note

The sample files provide identifiers only, not the original dataset. Users who obtain XNLI through its original distribution channel can use `source_pair_id`, `example_id`, and `input_language` to reproduce sample membership without this artifact redistributing dataset text.
