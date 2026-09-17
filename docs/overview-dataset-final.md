# Safe-Guard dataset overview (review-ready)

The project uses the [Safe-Guard Prompt Injection dataset](https://huggingface.co/datasets/xTRam1/safe-guard-prompt-injection), pinned for reproducibility to revision `a3a877d608f37b7d20d9945671902df895ecdb46`. It is hosted as Parquet with `text` and `label` fields: `0` means safe/benign and `1` means prompt injection. The dataset has 8,236 training rows and 2,060 test rows; validation must be derived from training data, with test held out for final evaluation.

The dataset card describes synthetic injection generation with GPT-3.5-turbo from curated seeds and a categorical tree. The described generation categories are not per-row labels. The linked GLAN paper is methodological background, not evidence for this detector's performance.

Results should be described as benchmark results on this source, not as evidence of production safety. General-purpose seed prompts, synthetic attacks, unknown licensing, and the absence of finance-specific traffic limit generalization. Raw files remain excluded from this repository. See [`docs/data-provenance.md`](data-provenance.md) and [`docs/threat-model.md`](threat-model.md).
