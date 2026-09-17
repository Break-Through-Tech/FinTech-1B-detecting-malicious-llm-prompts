# Detecting Malicious LLM Prompts

This Break Through Tech AI Studio project explores a recall-first classifier for detecting prompt-injection text. The project is a benchmark and learning artifact; it is not a production security certification or a financial decision system.

---

### 👥 **Team Members**

| Name | GitHub Handle | Contribution |
| --- | --- | --- |
| Ahmed Lawal | @AhmedLawal08 | Data preprocessing, model evaluation, performance analysis, and results interpretation |
| Avi Paudel | @Avi161 | EDA, model selection, model training, and model evaluation |
| Han Wang | @doublehan2023 | Data exploration |
| Jacqueline Henriksen | @jjjhenriksen | Data collection, exploratory data analysis (EDA), and dataset documentation |
| Moukthika Nellutla | @Mnellutla1120 | Model selection, hyperparameter tuning, model training, and optimization |
| Zeynep Bezeklioglu | @zeynepbezeklioglu | Data preprocessing, model training and evaluation, and data validation |
| Zakariye Mohamed | @zakiscoding | Model and data processing |

---

## 🎯 **Project Highlights**

- Develop a machine-learning classifier that prioritizes recall for prompt-injection detection.
- Establish a reproducible dataset, validation, and evaluation protocol for comparable experiments.
- Document the threat-model boundary, source provenance, limitations, and responsible-use requirements.
- Keep model results and generated evaluation artifacts pending until an exact, reproducible run is committed.

---

## 👩🏽‍💻 **Setup and Installation**

Clone the repository, create an isolated Python environment, and install the pinned dependencies:

```bash
git clone https://github.com/Break-Through-Tech/FinTech-1B-detecting-malicious-llm-prompts.git
cd FinTech-1B-detecting-malicious-llm-prompts
python -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt
```

Retrieve the pinned hosted dataset using [`data/README.md`](data/README.md). Before modeling, verify the expected schema, nulls, duplicates, labels, and split sizes. Raw downloaded files must not be placed under version control.

---

## 🏗️ **Project Overview**

The detector receives prompt-like text at an LLM application boundary and classifies it as safe/benign or prompt injection. Protected assets include confidential data, credentials and system instructions, workflow integrity, and model/tool availability and cost.

A classifier alone cannot enforce authorization or safely execute downstream actions. See the [threat model](docs/threat-model.md) and [analyst taxonomy](docs/analyst-taxonomy.md); the taxonomy is human-derived review vocabulary, not additional Safe-Guard source labels.

---

## 📊 **Data Exploration**

The project uses the [Safe-Guard Prompt Injection dataset](https://huggingface.co/datasets/xTRam1/safe-guard-prompt-injection), hosted as Parquet. It has `text` and `label` fields, with `0` meaning safe/benign and `1` meaning prompt injection. The hosted `train` split has 8,236 rows and `test` has 2,060 rows. Validation must be derived from `train`; the provided test split stays held out for final evaluation.

Read the [dataset provenance and retrieval note](docs/data-provenance.md), including unresolved licensing questions and synthetic-data limitations. The source combines synthetic attacks with prompts curated from general-purpose datasets; its binary labels do not identify attack techniques.

---

## 🧠 **Model Development**

The [shared experiment protocol](docs/experiment-protocol.md) defines deterministic stratified validation from `train`, training-only feature fitting, artifact naming, and comparable runs. The planned baseline uses TF-IDF features with linear classifiers; neural comparisons follow the [neural-model plan](docs/neural-model-plan.md).

The [baseline methods draft](docs/baseline-methods.md), [baseline review checklist](docs/baseline-review-checklist.md), and [neural training provenance template](docs/neural-training-provenance.md) define the documentation and review requirements for model work.

The [methods and preliminary-results narrative](docs/methods-and-preliminary-results.md) records the current analysis boundary and the evidence required before reporting results.

---

## 📈 **Results & Key Findings**

No model results or generated evaluation artifacts are committed yet. Future claims must link the exact run, source revision, configuration, and generated report.

Evaluation should report injection recall and false negatives first, alongside precision, F1, PR-AUC, and a confusion matrix. Thresholds and hyperparameters must be selected using validation data only.

---

## 🚀 **Next Steps**

- Run and document the shared baseline protocol, including exact data and configuration provenance.
- Evaluate generalization limits for finance-specific traffic, adaptive attacks, indirect injection, multilingual or obfuscated prompts, multi-turn workflows, and tool abuse.
- Complete the [final delivery checklist](docs/final-delivery-checklist.md) and [presentation artifact package](docs/presentation-artifacts.md).
- Treat the detector as one signal among layered controls: instruction isolation, least-privilege tools, action validation, logging, and human review.

The detector must not be used alone to authorize, block, or reverse a high-impact financial action.

---

## 📝 **License**

The repository does not currently declare a project license. Confirm the dataset and cited seed-source terms with the project advisor before redistributing raw or derived data.

---

## 📄 **References**

- [Safe-Guard Prompt Injection dataset](https://huggingface.co/datasets/xTRam1/safe-guard-prompt-injection)
- [Synthetic Data (Almost) from Scratch: Generalized Instruction Tuning for Language Models](https://arxiv.org/abs/2402.13064)

---

## 🙏 **Acknowledgements**

This project is part of the Break Through Tech AI Studio program. Project-specific advisor, host-company, and additional acknowledgement details should be added when confirmed by the team.
