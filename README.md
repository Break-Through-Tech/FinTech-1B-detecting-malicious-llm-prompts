# Detecting Malicious LLM Prompts

This Break Through Tech AI Studio project explores a recall-first classifier for detecting prompt-injection text. The project is a benchmark and learning artifact; it is not a production security certification or a financial decision system.

## Project scope

The detector receives prompt-like text at an LLM application boundary and classifies it as safe/benign or prompt injection. Protected assets include confidential data, credentials and system instructions, workflow integrity, and model/tool availability and cost. A classifier alone cannot enforce authorization or safely execute downstream actions.

See the [threat model](docs/threat-model.md) and [analyst taxonomy](docs/analyst-taxonomy.md). The taxonomy is human-derived review vocabulary, not additional Safe-Guard source labels.

## Dataset

The project uses the [Safe-Guard Prompt Injection dataset](https://huggingface.co/datasets/xTRam1/safe-guard-prompt-injection), hosted as Parquet. It has `text` and `label` fields, with `0` meaning safe/benign and `1` meaning prompt injection. The hosted `train` split has 8,236 rows and `test` has 2,060 rows. Validation must be derived from `train`; the provided test split stays held out for final evaluation.

Raw files are not committed. Follow the [data acquisition instructions](data/README.md) and read the [full provenance note](docs/data-provenance.md), including unresolved licensing questions and synthetic-data limitations.

## Setup and data access

Create an isolated Python environment and install the packages in [`requirements.txt`](requirements.txt):

```bash
python -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt
```

Retrieve the pinned hosted dataset using the example in [`data/README.md`](data/README.md). Before modeling, verify the expected schema, nulls, duplicates, labels, and split sizes. Do not place downloaded raw files under version control.

## Methods and evaluation

The [shared experiment protocol](docs/experiment-protocol.md) defines deterministic stratified validation from `train`, training-only feature fitting, artifact naming, and comparable runs. The planned baseline uses TF-IDF features with linear classifiers; neural comparisons follow the [neural-model plan](docs/neural-model-plan.md).

Evaluation should report injection recall and false negatives first, alongside precision, F1, PR-AUC, and a confusion matrix. Thresholds and hyperparameters must be selected using validation data only. See the [baseline methods draft](docs/baseline-methods.md) and [baseline review checklist](docs/baseline-review-checklist.md).

## Results and limitations

No model results or generated evaluation artifacts are committed yet. Future claims must link the exact run, source revision, configuration, and generated report. The source combines synthetic attacks with prompts curated from general-purpose datasets; its binary labels do not identify attack techniques. Performance may not generalize to finance-specific traffic, adaptive attacks, indirect injection, multilingual or obfuscated prompts, multi-turn workflows, or tool abuse.

The detector must not be used alone to authorize, block, or reverse a high-impact financial action. Production use would require additional controls such as instruction isolation, least-privilege tools, action validation, logging, and human review.

## Project documentation

- [Dataset provenance and retrieval](docs/data-provenance.md)
- [Threat model](docs/threat-model.md)
- [Shared experiment protocol](docs/experiment-protocol.md)
- [Neural training provenance template](docs/neural-training-provenance.md)
- [Methods and preliminary-results narrative](docs/methods-and-preliminary-results.md)
- [Final delivery checklist](docs/final-delivery-checklist.md)
- [Presentation artifact package](docs/presentation-artifacts.md)

## Team

| Name | GitHub handle | Contribution |
| --- | --- | --- |
| Ahmed Lawal | [@AhmedLawal08](https://github.com/AhmedLawal08) | Data preprocessing, model evaluation, performance analysis, and results interpretation |
| Avi Paudel | [@Avi161](https://github.com/Avi161) | EDA, model selection, model training, and model evaluation |
| Han Wang | [@doublehan2023](https://github.com/doublehan2023) | Data exploration |
| Jacqueline Henriksen | [@jjjhenriksen](https://github.com/jjjhenriksen) | Data collection, exploratory analysis, and dataset documentation |
| Moukthika Nellutla | [@Mnellutla1120](https://github.com/Mnellutla1120) | Model selection, hyperparameter tuning, model training, and optimization |
| Zeynep Bezeklioglu | [@zeynepbezeklioglu](https://github.com/zeynepbezeklioglu) | Data preprocessing, model training and evaluation, and data validation |
| Zakariye Mohamed | [@zakiscoding](https://github.com/zakiscoding) | Model and data processing |

## References

- [Safe-Guard Prompt Injection dataset](https://huggingface.co/datasets/xTRam1/safe-guard-prompt-injection)
- [Synthetic Data (Almost) from Scratch: Generalized Instruction Tuning for Language Models](https://arxiv.org/abs/2402.13064)

## License

The repository does not currently declare a project license. Confirm the dataset and cited seed-source terms with the project advisor before redistributing raw or derived data.
