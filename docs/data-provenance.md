# Safe-Guard dataset provenance

This project uses the [Safe-Guard Prompt Injection dataset](https://huggingface.co/datasets/xTRam1/safe-guard-prompt-injection), published on Hugging Face by `xTRam1`.

## Pinned source

The source used for project documentation is the Hugging Face dataset repository at revision [`a3a877d608f37b7d20d9945671902df895ecdb46`](https://huggingface.co/datasets/xTRam1/safe-guard-prompt-injection/tree/a3a877d608f37b7d20d9945671902df895ecdb46) (the dataset repository's `main` revision on 2024-06-27).

The hosted configuration is Parquet and contains:

| Split | Rows | Fields |
| --- | ---: | --- |
| `train` | 8,236 | `text` (string), `label` (int64) |
| `test` | 2,060 | `text` (string), `label` (int64) |

The dataset contract for this project is `label = 0` for safe/benign prompts and `label = 1` for prompt-injection prompts. The provided `test` split remains held out for final evaluation; any validation split must be derived from `train` only.

## Retrieval and reproducibility

Raw dataset files are not committed to this repository. A reproducible Python retrieval example is:

```python
from datasets import load_dataset

DATASET = "xTRam1/safe-guard-prompt-injection"
REVISION = "a3a877d608f37b7d20d9945671902df895ecdb46"

dataset = load_dataset(DATASET, revision=REVISION)
train = dataset["train"]
test = dataset["test"]
```

The equivalent files are the hosted Parquet files under `data/train-*` and `data/test-*`. Retrieval should be followed by checks for the expected columns, null text values, duplicate prompts, and the observed label values before modeling.

## Origin and limitations

According to the [dataset card](https://huggingface.co/datasets/xTRam1/safe-guard-prompt-injection/blob/a3a877d608f37b7d20d9945671902df895ecdb46/README.md), the authors curated seed prompts from several open-source datasets and used GPT-3.5-turbo with a categorical tree of objection categories to generate synthetic injection examples. The card describes categories such as context manipulation, social engineering, instruction override, and fake completion. Those are descriptions of the generation process; they are **not per-example labels in this dataset**.

The card also links [Synthetic Data (Almost) from Scratch: Generalized Instruction Tuning for Language Models](https://arxiv.org/abs/2402.13064) (GLAN) as background for the synthetic-data method. That paper is not a validation study of this project's detector.

Because the data combines synthetic attacks with prompts curated from general-purpose open-source datasets, benchmark results may not generalize to real-world or finance-specific traffic. They must not be presented as evidence that a production filter is safe without additional evaluation, including finance-domain and adversarial testing.

## Access and licensing questions

At the pinned revision, the dataset card describes the data and links its sources but does not provide a clear dataset license in the repository metadata. Before redistributing the Parquet files, publishing derived examples, or using the data in a deployed product, the team should confirm:

1. what license, if any, governs the Safe-Guard dataset;
2. whether the licenses and terms of the cited seed datasets permit this use and redistribution; and
3. whether the synthetic prompts or source examples create attribution, privacy, or other downstream obligations.

Until those questions are answered, use the hosted data for the project's documented experiments, avoid committing raw files, and preserve source attribution.

## References

- [Safe-Guard Prompt Injection dataset card](https://huggingface.co/datasets/xTRam1/safe-guard-prompt-injection)
- [Safe-Guard dataset repository at the pinned revision](https://huggingface.co/datasets/xTRam1/safe-guard-prompt-injection/tree/a3a877d608f37b7d20d9945671902df895ecdb46)
- [GLAN paper, arXiv:2402.13064](https://arxiv.org/abs/2402.13064)
